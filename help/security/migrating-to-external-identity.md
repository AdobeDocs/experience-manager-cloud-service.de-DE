---
title: Migration zur externen Identität und zur dynamischen Gruppenmitgliedschaft
description: Technisches Handbuch zum Migrieren lokaler Benutzer und Gruppen zu einem externen Identitätsmodell mit dynamischer Gruppenmitgliedschaft in AEM as a Cloud Service
solution: Experience Manager Sites
feature: Security
role: Developer, Admin
source-git-commit: 1f8bd9eea249e0b2242f3fbe1490b3d51052f546
workflow-type: tm+mt
source-wordcount: '2232'
ht-degree: 1%

---

# Migration zur externen Identität und zur dynamischen Gruppenmitgliedschaft {#migrating-to-external-identity}

## Übersicht {#overview}

Wenn [Datensynchronisierung](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md#data-synchronization) in AEM as a Cloud Service aktiviert ist, kann der SAML-Authentifizierungs-Handler so konfiguriert werden, dass er automatisch zu externen Identitäten mit dynamischer Gruppenmitgliedschaft migriert wird, wenn die Benutzer- und Gruppenerstellung verwaltet wird. Wenn Ihr Projekt benutzerdefinierten Code zum Erstellen von Benutzenden oder Gruppen verwendet, müssen Sie ihn aktualisieren, um externe Benutzende und Gruppen zu erstellen, im Gegensatz zu lokalen Benutzenden und Gruppen.

### Warum externe Benutzer und Gruppen erforderlich sind {#why-external-required}

Die Migration von lokalen Benutzern und Gruppen zu externen Identitäten mit dynamischer Gruppenmitgliedschaft ist aus mehreren kritischen Gründen wichtig:

**Leistungsoptimierung:**

* **Reduzierte Repository-Schreibvorgänge**: Herkömmliche lokale Gruppenmitgliedschaften erfordern das Schreiben von Mitgliedschaftsbeziehungen zum Repository in einer einzelnen mehrwertigen Eigenschaft des Gruppenknotens. Bei dynamischer Gruppenmitgliedschaft verfügen Benutzende über eine einzige `rep:externalPrincipalNames`-Eigenschaft, die alle Gruppenprinzipale enthält, sodass der Gruppenknoten nicht synchronisiert werden muss
* **Schnellere Synchronisierung**: Bei der Synchronisierung von Benutzern über Knoten der Veröffentlichungsebene hinweg benötigen externe Benutzer mit dynamischer Gruppenmitgliedschaft im Vergleich zu lokalen Benutzern mit herkömmlicher Gruppenmitgliedschaft erheblich weniger Datenübertragungen und Schreibvorgänge
* **Skalierbarkeit**: Systeme mit einer großen Anzahl von Benutzern und Gruppen profitieren erheblich von einem geringeren Repository-Overhead. Die dynamische Gruppenmitgliedschaft kann auch bei sehr großen Gruppen effizient skaliert werden.

Dieses Dokument enthält technische Anleitungen für:

* Grundlagen zum externen Identitätsmodell
* Ändern von benutzerdefiniertem Code zum Erstellen externer Benutzer und Gruppen
* Migrieren vorhandener lokaler Benutzer und Gruppen zum externen Identitätsmodell

## Externe Identität verstehen {#understanding-external-identity}

### Externe Benutzer {#external-users}

Externe Benutzer werden durch die `rep:externalId`-Eigenschaft identifiziert, die den Benutzer mit einem externen Identitätsanbieter verknüpft. Das Format lautet:

```
userId;idpName
```

Beispiel: `john.doe;saml-idp`.

>[!NOTE]
>
> `idpName` bezieht sich auf den Namen des Oak Identity Providers (IDP), wie in der Authentifizierungs-Handler-Konfiguration definiert. Bei SAML-Integrationen ist dies der Wert, der für das `idpIdentifier`-Attribut im SAML-Authentifizierungs-Handler festgelegt wird.

**Schlüsseleigenschaften:**

* `rep:externalId`: Erforderliche Eigenschaft, die einen Benutzer als extern kennzeichnet (z. B. `john.doe;saml-idp`)
* `rep:externalPrincipalNames`: Mehrwertige Eigenschaft mit externen Gruppenprinzipalen für dynamische Mitgliedschaft
* `rep:lastSynced`: Zeitstempel der letzten Synchronisierung
* `rep:lastDynamicSync`: Zeitstempel der letzten Synchronisierung der dynamischen Gruppenmitgliedschaft

### Externe Gruppen {#external-groups}

Externe Gruppen werden ebenfalls durch die `rep:externalId`-Eigenschaft identifiziert und verwenden ein Prinzipalnamenformat:

```
groupId;idpName
```

Zum Beispiel: `content-authors;saml-idp`

### Dynamische Gruppenzugehörigkeit {#dynamic-group-membership}

Anstelle der im Repository gespeicherten direkten Benutzer-zu-Gruppe-Beziehungen verwendet die dynamische Gruppenmitgliedschaft die `rep:externalPrincipalNames`-Eigenschaft auf dem Benutzerknoten. Wenn ein(e) Benutzende(r) einen externen Prinzipalnamen hat, der mit der ID einer externen Gruppe übereinstimmt, wird er/sie automatisch Mitglied dieser Gruppe. Weitere Informationen finden Sie in der [Apache Oak-Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authentication/external/dynamic.html).

**Vorteile:**

* Reduzierte Repository-Schreibvorgänge (es werden keine Gruppenmitgliedschaftsknoten geändert, wenn Benutzer Gruppen hinzugefügt/daraus entfernt werden)
* Schnellere Synchronisierung zwischen Knoten der Veröffentlichungsebene
* Verwaltung der skalierbaren Gruppenmitgliedschaft
* Kompatibel mit den Anforderungen für die Datensynchronisation

## Dienstbenutzerkonfiguration {#service-user-configuration}

Alle Vorgänge, die externe Benutzer und Gruppen erstellen oder ändern, sollten mit einem **Service-Benutzer** durchgeführt werden, der ordnungsgemäß so konfiguriert ist, dass er den Standardschutz für die `rep:externalId`- und `rep:externalPrincipalNames` umgeht.

### Warum ist ein Service-Benutzer erforderlich? {#why-is-a-service-user-required}

Standardmäßig verhindert Oak Security, dass reguläre Sitzungen geschützte Eigenschaften ändern, wie etwa:

* `rep:externalId` - Markiert Benutzer/Gruppen als extern
* `rep:externalPrincipalNames` - Speichert dynamische Gruppenmitgliedschaftsprinzipale

Nur ein ordnungsgemäß konfigurierter Dienstbenutzer kann diese Eigenschaften ändern.

### Konfiguration und Zuordnung von Service-Benutzern {#service-user-configuration-mapping}

Die Einrichtung eines Dienstbenutzers zur Verwaltung externer Identitäten erfordert drei koordinierte Konfigurationen:

1. Dienstbenutzer über `repoinit` erstellen
2. `ExternalPrincipal` konfigurieren
3. Ordnen Sie den Dienstbenutzer Ihrem Anwendungspaket zu.

Unten finden Sie eine ausführliche Beschreibung dieser Schritte.

#### Schritt 1: Service-Benutzer über Repoinit erstellen {#create-the-serviice-user-via-repoinit}

In diesem Schritt wird die Erstellung des Dienstbenutzers mit den erforderlichen Berechtigungen mithilfe eines `repoinit` beschrieben.

**Konfigurationsdatei:** `org.apache.sling.jcr.repoinit.RepositoryInitializer~group-provisioner.cfg.json`

**Beispielhafte Lage:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "scripts": [
    "create service user group-provisioner with path system/yourproject",
    "set ACL for group-provisioner\n  allow jcr:read,jcr:readAccessControl,jcr:modifyAccessControl,rep:userManagement,rep:write on /home/users\n  allow jcr:read,jcr:readAccessControl,jcr:modifyAccessControl,rep:userManagement,rep:write on /home/groups\nend"
  ]
}
```

**Berechtigungen - Übersicht**

* `jcr:read`: Benutzer und Gruppen lesen
* `jcr:readAccessControl`: ACLs lesen
* `jcr:modifyAccessControl`: Ändern von ACLs (erforderlich für das Festlegen von Eigenschaften)
* `rep:userManagement`: Erstellen und Verwalten von Benutzern/Gruppen
* `rep:write`: Schreiben von Eigenschaften einschließlich `rep:externalId` und `rep:externalPrincipalNames`

>[!NOTE]
>
>Der Service-Benutzer wird unter `/home/users/system/yourproject` erstellt, um ihn mit anderen Systembenutzern zu organisieren.

#### Schritt 2: Externen Prinzipalschutz konfigurieren {#configure-externalprincipal-protection}

Im Folgenden finden Sie eine Beispielkonfiguration, mit der der Service-Benutzer auf die Zulassungsliste gesetzt wird, damit er den Schutz umgehen kann, der auf externe Identitätseigenschaften angewendet wird.

**Konfigurationsdateiname:** `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration.cfg.json`

**Beispielspeicherort:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "protectExternalIdentities": "Warn",
  "systemPrincipalNames": [
    "group-provisioner",
    "saml-migration-service"
  ]
}
```

**Konfigurationseigenschaften:**

* `protectExternalIdentities`: Steuert das Schutzniveau für externe Identitätseigenschaften:
   * `"Strict"`: Nur Systemprinzipale in der Zulassungsliste können externe Eigenschaften ändern. Dies ist die für die Produktion empfohlene Ebene.
   * `"Warn"`: Protokolliert Warnungen, lässt jedoch Änderungen zu. Nützlich für Entwicklung/Tests.
   * `"None"`: Kein Schutz. Nicht empfohlen.
* `systemPrincipalNames`: Liste der Service-Benutzernamen, die `rep:externalId` und `rep:externalPrincipalNames` ändern dürfen. Einschließen aller Service-Benutzer, die externe Identitäten verwalten müssen (z. B. `group-provisioner`, `saml-migration-service`).

>[!IMPORTANT]
>
>Die Service-Benutzernamen in `systemPrincipalNames` müssen genau mit den Service-Benutzer-IDs übereinstimmen, die im repoinit-Skript erstellt wurden.

#### Schritt 3: Service-Benutzerzuordnung {#service-user-mapping}

Ordnen Sie den Dienstbenutzer Ihrem Anwendungspaket zu, damit Ihr Code ihn verwenden kann.

**Konfigurationsdatei:** `org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended~group-provisioner.cfg.json`

**Standort:** `ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/config.publish/`

```json
{
  "user.mapping": [
    "yourproject.core:group-provisioner=[group-provisioner]"
  ]
}
```

**Zuordnungsformat:**

* `yourproject.core`: Der symbolische Bundle-Name (in `pom.xml` `<Bundle-SymbolicName>`)
* `group-provisioner` (vor `=`): Der Name des Unterdienstes, den Sie im Code verwenden werden
* `[group-provisioner]` (nach `=`): Die tatsächliche Service-Benutzer-ID, die in repoinit erstellt wurde

### Verwenden des Dienstbenutzers in Code {#using-the-service-user-in-code}

Beim Öffnen einer Sitzung für die Durchführung von Migrations- oder Benutzer-/Gruppenerstellungsvorgängen müssen Sie den Dienstbenutzer verwenden:

```java
import org.apache.sling.jcr.api.SlingRepository;

@Reference
private SlingRepository repository;

// Login as the service user
Session serviceSession = repository.loginService("group-provisioner", null);

try {
    UserManager userManager = ((JackrabbitSession) serviceSession).getUserManager();
    // Perform operations...
    serviceSession.save();
} finally {
    if (serviceSession != null && serviceSession.isLive()) {
        serviceSession.logout();
    }
}
```

>[!IMPORTANT]
>
>Ohne ordnungsgemäße Dienstbenutzerkonfiguration schlagen Versuche, `rep:externalId` oder `rep:externalPrincipalNames` festzulegen, mit Berechtigungsfehlern fehl. Stellen Sie sicher, dass Ihr Dienstbenutzer in der `ExternalPrincipal`-Konfiguration ordnungsgemäß konfiguriert ist, bevor Sie die Migration durchführen.

## Vollständiges Konfigurationsbeispiel {#complete-configuration-example}

Nachfolgend finden Sie ein vollständiges praktisches Beispiel, das alle drei Konfigurationen zusammen zeigt:

### Dateistruktur {#file-structure}

```
ui.config/src/main/content/jcr_root/apps/yourproject/osgiconfig/
└── config.publish/
    ├── org.apache.sling.jcr.repoinit.RepositoryInitializer~group-provisioner.cfg.json
    ├── org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration.cfg.json
    └── org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended~group-provisioner.cfg.json
```

### Ändern von benutzerdefiniertem Code {#modifying-custom-code}

#### Externe Benutzer erstellen {#creating-external-users}

**before (lokaler Benutzer):**

```java
UserManager userManager = ((JackrabbitSession) session).getUserManager();
User user = userManager.createUser(userId, password);
```

**nach (externer Benutzer):**

```java
import org.apache.jackrabbit.oak.spi.security.authentication.external.ExternalIdentityRef;

UserManager userManager = ((JackrabbitSession) session).getUserManager();
ValueFactory valueFactory = session.getValueFactory();

// Create user with principal
Principal userPrincipal = new Principal() {
    @Override
    public String getName() {
        return userId;
    }
};

User user = userManager.createUser(userId, null, userPrincipal, null);

// Set rep:externalId
ExternalIdentityRef externalRef = new ExternalIdentityRef(userId, idpName);
String externalId = externalRef.getString(); // Format: userId;idpName
user.setProperty("rep:externalId", valueFactory.createValue(externalId));

// Set sync timestamps to far future (workaround for OAK-12079)
// Set to 10 years in the future to prevent premature cleanup of external group memberships
// See: https://issues.apache.org/jira/browse/OAK-12079
java.util.Calendar future = java.util.Calendar.getInstance();
future.add(java.util.Calendar.YEAR, 10);
user.setProperty("rep:lastSynced", valueFactory.createValue(future));
user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));

session.save();
```

#### Erstellen externer Gruppen {#creating-external-groups}

**before (lokale Gruppe):**

```java
UserManager userManager = ((JackrabbitSession) session).getUserManager();
Group group = userManager.createGroup(groupId);
```

**Nach (externe Gruppe):**

```java
import org.apache.jackrabbit.oak.spi.security.authentication.external.ExternalIdentityRef;

UserManager userManager = ((JackrabbitSession) session).getUserManager();
ValueFactory valueFactory = session.getValueFactory();

// Create group with principal
Principal groupPrincipal = new Principal() {
    @Override
    public String getName() {
        return groupId;
    }
};

Group group = userManager.createGroup(groupPrincipal);

// Set rep:externalId
ExternalIdentityRef externalRef = new ExternalIdentityRef(groupId, idpName);
String externalId = externalRef.getString(); // Format: groupId;idpName
group.setProperty("rep:externalId", valueFactory.createValue(externalId));

session.save();
```

#### Zuweisen einer dynamischen Gruppenmitgliedschaft {#assigning-dynamic-membership}

**Vor (Direkte Mitgliedschaft):**

```java
Group group = (Group) userManager.getAuthorizable(groupId);
User user = (User) userManager.getAuthorizable(userId);
group.addMember(user);
```

**Nach (dynamische Mitgliedschaft):**

```java
User user = (User) userManager.getAuthorizable(userId);
ValueFactory valueFactory = session.getValueFactory();

// Get existing external principal names
Value[] existingValues = user.getProperty("rep:externalPrincipalNames");
List<String> principalNames = new ArrayList<>();

if (existingValues != null) {
    for (Value value : existingValues) {
        principalNames.add(value.getString());
    }
}

// Add new principal name (format: groupId;idpName)
String dynamicGroupPrincipal = groupId + ";" + idpName;
if (!principalNames.contains(dynamicGroupPrincipal)) {
    principalNames.add(dynamicGroupPrincipal);
    
    // Create new Value array
    Value[] newValues = new Value[principalNames.size()];
    for (int i = 0; i < principalNames.size(); i++) {
        newValues[i] = valueFactory.createValue(principalNames.get(i));
    }
    
    // Set the property
    user.setProperty("rep:externalPrincipalNames", newValues);
    
    // Update sync timestamps to far future (workaround for OAK-12079)
    // Set to 10 years in the future to prevent premature cleanup of external group memberships
    // See: https://issues.apache.org/jira/browse/OAK-12079
    java.util.Calendar future = java.util.Calendar.getInstance();
    future.add(java.util.Calendar.YEAR, 10);
    user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
    user.setProperty("rep:lastSynced", valueFactory.createValue(future));
}

session.save();
```

## Migrationsprozess {#migration-process}

Die Migration vorhandener lokaler Benutzer und Gruppen zur externen Identität ist nicht erforderlich, wenn der benutzerdefinierte Code vor der Aktivierung der Datensynchronisierungs-Services aktualisiert wurde.

Wenn lokale Benutzer und Gruppen bereits im Repository gespeichert wurden und die Umgebung aktiv verwendet wird, empfehlen wir eine mehrstufige Migration wie die folgende, um Unterbrechungen oder Inkonsistenzen zu vermeiden.

>[!IMPORTANT]
>
>Alle Migrationsschritte müssen mit einem ordnungsgemäß konfigurierten Service-Benutzer (z. B. `group-provisioner`) ausgeführt werden, dem Berechtigungen zum Umgehen des Schutzes für `rep:externalId`- und `rep:externalPrincipalNames` gewährt wurden. Weitere Informationen finden [ unter ](#service-user-configuration)Service-Benutzerkonfiguration“.

### Schritt 1: Externe Gruppenstruktur erstellen {#step-1-create-external-group-structure}

Für jede lokale Gruppe, die migriert werden muss:

1. Erstellen Sie eine entsprechende externe Gruppe mit dem Prinzipalnamen: `<localGroupId>;<idpName>`. Verwenden Sie eine Namenskonvention, die die Verknüpfung externer Gruppen mit lokalen Gruppen unterstützt.
1. Legen Sie die `rep:externalId`-Eigenschaft der externen Gruppe mit folgenden Werten fest: `<localGroupId>;<idpName>`
1. Fügen Sie die externe Gruppe als Mitglied der ursprünglichen lokalen Gruppe hinzu.

**Validierung**

* Sie können die Ergebnisse überprüfen, indem Sie überprüfen, ob jede lokale Gruppe über eine entsprechende externe Gruppe verfügt. Darüber hinaus ist jede externe Gruppe Mitglied der entsprechenden lokalen Gruppe.

**Beispiel für einen Servlet-Endpunkt:**

```java
@SlingServletPaths("/bin/migration/step1")
public class MigrationStep1Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {
        String groupPath = request.getParameter("groupPath");
        String idpName = request.getParameter("idpName");

        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        // Get local group
        Authorizable localGroupAuth = userManager.getAuthorizableByPath(groupPath);
        Group localGroup = (Group) localGroupAuth;
        String localGroupId = localGroup.getID();
        
        // Create external group
        String externalGroupPrincipalName = localGroupId + ";" + idpName;
        // The function createExternalGroup performs the following steps:
        // 1. Creates a new external group with the given principal name (format: "<localGroupId>;<idpName>").
        // 2. Sets the 'rep:externalId' property on the group to mark it as an external group (value: "<localGroupId>;<idpName>").
        // 3. Sets the 'rep:principalName' property for the group if required.
        // 4. Assigns any other required group metadata, such as a title or description, if needed.
        // 5. Persists the new group node in the repository at the appropriate path under /home/groups.
        // 6. Returns the created Group object so it can be used for further operations, such as membership assignment.
        Group externalGroup = createExternalGroup(externalGroupPrincipalName, localGroupId, idpName);
        
        // Add external group to local group
        localGroup.addMember(externalGroup);
        
        session.save();
    }
}
```

**Nutzung:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step1?groupPath=/home/groups/c/content-authors&idpName=saml-idp"
```

### Schritt 2: Benutzer konvertieren und dynamische Mitgliedschaft zuweisen {#step-2-convert-users-and-assign-dynamic-membership}

Für jeden Benutzer, der Mitglied einer lokalen Gruppe ist:

1. Stellen Sie sicher, dass Folgendes `rep:externalId` ist (konvertieren Sie sie ggf. in einen externen Benutzer).
1. Fügen Sie für jede Gruppenmitgliedschaft den entsprechenden externen Gruppenprinzipal zu `rep:externalPrincipalNames` hinzu
1. Synchronisierungszeitstempel aktualisieren.

>[!IMPORTANT]
>
>Systemgruppen wie „alle“ werden bei diesem Prozess übersprungen.

**Beispiel für einen Servlet-Endpunkt:**

```java
@SlingServletPaths("/bin/migration/step2")
public class MigrationStep2Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {
        String userId = request.getParameter("userId");
        String idpName = request.getParameter("idpName");
        
        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        // Login as the service user
        Session serviceSession = repository.loginService("group-provisioner", null);

        try {
            UserManager userManager = ((JackrabbitSession) serviceSession).getUserManager();
            User user = (User) userManager.getAuthorizable(userId);
            
            // Ensure user has rep:externalId
            Value[] externalIdValues = user.getProperty("rep:externalId");
            if (externalIdValues == null || externalIdValues.length == 0) {
                ExternalIdentityRef externalRef = new ExternalIdentityRef(userId, idpName);
                user.setProperty("rep:externalId", 
                            valueFactory.createValue(externalRef.getString()));
            }
            
            // Get all group memberships
            Iterator<Group> groupIterator = user.declaredMemberOf();
            List<String> principalNames = new ArrayList<>();
            
            while (groupIterator.hasNext()) {
                Group group = groupIterator.next();
                String groupId = group.getID();
                
                // Skip system groups
                if ("everyone".equals(groupId)) {
                    continue;
                }
                
                // Add dynamic group principal
                String dynamicGroupPrincipal = groupId + ";" + idpName;
                principalNames.add(dynamicGroupPrincipal);
            }
            
            // Set rep:externalPrincipalNames
            if (!principalNames.isEmpty()) {
                Value[] newValues = new Value[principalNames.size()];
                for (int i = 0; i < principalNames.size(); i++) {
                    newValues[i] = valueFactory.createValue(principalNames.get(i));
                }
                user.setProperty("rep:externalPrincipalNames", newValues);
            }
            
            // Update timestamps to far future (workaround for OAK-12079)
            // Set to 10 years in the future to prevent premature cleanup of external group memberships
            // See: https://issues.apache.org/jira/browse/OAK-12079
            java.util.Calendar future = java.util.Calendar.getInstance();
            future.add(java.util.Calendar.YEAR, 10);
            user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
            user.setProperty("rep:lastSynced", valueFactory.createValue(future));
        
        // Perform operations...
        serviceSession.save();
    } finally {
        if (serviceSession != null && serviceSession.isLive()) {
            serviceSession.logout();
        }
}    }
}
```

**Nutzung:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step2?userId=john.doe&idpName=saml-idp"
```

**Validierung**

Sie können dies überprüfen, indem Sie überprüfen, ob jeder Benutzer über die `rep:externalId` und `rep:externalPrincipalName` Attribute mit dem `principalName` jeder externen Gruppe verfügt. Die Benutzer sind Mitglieder der lokalen Gruppen *und* der externen Gruppen.

### Schritt 3: Entfernen Sie direkte Benutzermitgliedschaften {#step-3-remove-direct-user-memberships}

Nachdem Benutzer die dynamische Gruppenmitgliedschaft konfiguriert haben:

1. Entfernen direkter Benutzermitgliedschaften aus lokalen Gruppen
1. Beibehalten von Gruppenmitgliedschaften (einschließlich der externen Gruppenmitgliedschaft)

**Beispiel für einen Servlet-Endpunkt:**

```java
@SlingServletPaths("/bin/migration/step3")
public class MigrationStep3Servlet extends SlingAllMethodsServlet {
    
    @Override
    protected void doPost(SlingHttpServletRequest request, 
                          SlingHttpServletResponse response) {

        // Check if the caller is authorized to run the servlet
        isAuthorizedCaller(request, response);

        String groupPath = request.getParameter("groupPath");
        
        Authorizable localGroupAuth = userManager.getAuthorizableByPath(groupPath);
        Group localGroup = (Group) localGroupAuth;
        
        // Process each member
        Iterator<Authorizable> members = localGroup.getDeclaredMembers();
        
        while (members.hasNext()) {
            Authorizable member = members.next();
            
            // Remove only user members, keep group members
            if (!member.isGroup()) {
                localGroup.removeMember(member);
            }
        }
        
        session.save();
    }
}
```

**Nutzung:**

```bash
curl -X POST "http://localhost:4503/bin/migration/step3?groupPath=/home/groups/c/content-authors"
```

**Validierung**

* Sie können dies überprüfen, indem Sie überprüfen, ob jede lokale Gruppe nur die entsprechende externe Gruppe oder andere Gruppen als Mitglied hat.


## Migrations-Workflow {#migration-workflow}

### Checkliste vor der Migration {#pre-migration-checklist}

* **Dienstbenutzer konfigurieren**: Erstellen und konfigurieren Sie den Dienstbenutzer (z. B. `group-provisioner`) mit den entsprechenden Berechtigungen
* **Externe Prinzipalkonfiguration überprüfen**: Stellen Sie sicher, dass der Dienstbenutzer so konfiguriert ist, dass der Schutz auf `rep:externalId` und `rep:externalPrincipalNames` umgangen wird
* **Berechtigungen für Service-Benutzer testen**: Überprüfen, ob der Service-Benutzer externe Identitätseigenschaften in der Entwicklung festlegen kann
* Identifizieren des gesamten benutzerdefinierten Codes, der Benutzer oder Gruppen erstellt
* Überprüfen und aktualisieren Sie benutzerdefinierten Code zur Verwendung des externen Identitätsmodells
* Testen von aktualisiertem Code in der Entwicklungsumgebung
* Inventarisieren aller zu migrierenden lokalen Benutzer und Gruppen
* Testen des Migrationsprozesses in niedrigeren Umgebungen

### Ausführungsschritte {#execution-steps}

1. **Aktualisierten Code bereitstellen**: Benutzerdefinierte Code-Änderungen bereitstellen, um externe Benutzer/Gruppen zu erstellen

1. **Externe Gruppen erstellen** (für jede lokale Gruppe):

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step1?groupPath=/home/groups/g/my-group&idpName=saml-idp"
   ```

1. **Benutzer migrieren** (für jeden Benutzer):

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step2?userId=username&idpName=saml-idp"
   ```

1. **Bereinigung** (für jede migrierte Gruppe):

   ```bash
   curl -X POST "http://localhost:4503/bin/migration/step3?groupPath=/home/groups/g/my-group"
   ```

1. **Überprüfen**: Überprüfen Sie die Mitgliedschaft in Benutzergruppen und die Zugriffsberechtigungen für Tests

1. **Datensynchronisierung aktivieren**: Wenden Sie sich an den Support, um die Funktion zu aktivieren

### Validierung nach der Migration {#post-migration-validation}

Überprüfen Sie die Migration:

1. **Benutzereigenschaften überprüfen**:

   Überprüfen Sie auf Benutzerknoten, ob Folgendes vorhanden ist:

   * `rep:externalId`: Das Format muss `userId;idpName` sein
   * `rep:externalPrincipalNames`: Array von Gruppenprinzipalen im Format `groupId;idpName`
   * `rep:lastSynced`: Zeitstempel auf weit in der Zukunft (ca. 10 Jahre ab dem Migrationsdatum)
   * `rep:lastDynamicSync`: Zeitstempel auf weit in der Zukunft (ca. 10 Jahre ab dem Migrationsdatum)

   **Hinweis**: Als Problemumgehung für OAK-12079 werden die Zeitstempel absichtlich auf ein weit künftiges Datum festgelegt. Dies ist das erwartete Verhalten.

1. **Gruppeneigenschaften überprüfen**:

   Überprüfen Sie auf lokalen Gruppenknoten, ob Folgendes vorhanden ist:

   * Externes Gruppenmitglied mit dem Format `groupId;idpName`
   * Keine direkten Benutzermitglieder (erst nach Schritt 3)

1. **Benutzeranmeldung testen**: Überprüfen Sie, ob Benutzer sich anmelden können und über die richtigen Berechtigungen verfügen

1. **Zugriffssteuerung testen** Überprüfen, ob Benutzer auf durch CUGs/ACLs geschützte Inhalte zugreifen können

## Fehlerbehebung {#troubleshooting}

### Gängige Probleme {#common-issues}

**Problem: Berechtigungsfehler beim Festlegen von `rep:externalId` oder`rep:externalPrincipalNames`**

**Fehlermeldungen:**

* `javax.jcr.AccessDeniedException: Access denied`
* `OakAccess0000: Access denied`
* `Cannot set property 'rep:externalId'`

**Lösung**: Die Sitzung muss mit einem ordnungsgemäß konfigurierten Service-Benutzer geöffnet werden, dem Berechtigungen zum Umgehen des Schutzes für externe Identitätseigenschaften gewährt wurden.

**Schritte zur Auflösung:**

1. **Dienstbenutzer überprüfen**: Stellen Sie sicher, dass der Dienstbenutzer (z. B. `group-provisioner`) über „repoinit“ erstellt wird
1. **Dienstbenutzerzuordnung überprüfen**: Überprüfen, ob das Servlet oder der Dienst `repository.loginService("group-provisioner", null)` verwendet
1. **Konfiguration von ExternalPrincipal überprüfen**: Sicherstellen, dass `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.principal.ExternalPrincipalConfiguration` ordnungsgemäß konfiguriert ist
1. **Berechtigungen für Dienstbenutzer überprüfen**: Der Dienstbenutzer benötigt `rep:write` und `rep:userManagement` Berechtigungen für `/home/users` und `/home/groups`

Siehe [Service-Benutzerkonfiguration](#service-user-configuration) für vollständige Einrichtungsanweisungen.

**Problem:`OakConstraint0072: Property 'rep:externalPrincipalNames' requires 'rep:externalId' to be present`**

**Lösung**: Benutzer müssen `rep:externalId` festgelegt haben, bevor sie `rep:externalPrincipalNames` festlegen. Stellen Sie sicher, dass in Schritt 2 Benutzer zuerst zu externen Benutzern konvertiert werden.

**Problem: Benutzende verlieren nach der Migration Gruppenmitgliedschaften**

**Lösung**: Überprüfen Sie Folgendes:

* Die externe Gruppe wurde mit dem richtigen Prinzipalnamenformat (`groupId;idpName`) erstellt
* Externe Gruppe wurde als Mitglied der lokalen Gruppe hinzugefügt (Schritt 1)
* Benutzer hat korrekte externe Prinzipalnamen in `rep:externalPrincipalNames` (Schritt 2)
* Die Bereinigung in Schritt 3 wurde erst nach Abschluss der Schritte 1 und 2 durchgeführt

**Problem: Externe Gruppenmitgliedschaften werden nach der Benutzeranmeldung unerwartet entfernt (OAK-12079)**

**Problem**: Aufgrund des Oak-Fehlers [OAK-12079](https://issues.apache.org/jira/browse/OAK-12079) kann der Oak-Synchronisierungsmechanismus externe Gruppenmitgliedschaften basierend auf den `rep:lastSynced` und `rep:lastDynamicSync` Zeitstempeln vorzeitig bereinigen.

**Lösung**: Setzen Sie `rep:lastSynced` und `rep:lastDynamicSync` Zeitstempel auf ein weit künftiges Datum (in 10 Jahren) anstelle der aktuellen Zeit. Dadurch wird verhindert, dass der Synchronisierungsbereinigungsprozess die externen Gruppenmitgliedschaften entfernt.

**Implementierung:**

```java
// Workaround for OAK-12079
// Set to 10 years in the future to prevent premature cleanup
// See: https://issues.apache.org/jira/browse/OAK-12079
java.util.Calendar future = java.util.Calendar.getInstance();
future.add(java.util.Calendar.YEAR, 10);
user.setProperty("rep:lastSynced", valueFactory.createValue(future));
user.setProperty("rep:lastDynamicSync", valueFactory.createValue(future));
```

**Warum dies funktioniert**: Durch Festlegen der Zeitstempel auf ein Datum in ferner Zukunft behandelt die Oak-Synchronisierungslogik diese Benutzenden als „kürzlich synchronisiert“ und löst keinen Trigger beim Bereinigungsprozess aus, der die externen Prinzipalnamen und Gruppenmitgliedschaften entfernen würde.

**Hinweis**: Dies ist eine temporäre Problemumgehung, bis die OAK-12079 in einer zukünftigen Oak-Version behoben ist. Alle Code-Beispiele in diesem Dokument enthalten diese Problemumgehung bereits.

**Problem: Systemgruppe „Jeder“ verursacht Fehler**

**Lösung**: Überspringen Sie bei der Benutzermigration immer die Systemgruppe „Jeder“ (Schritt 2). Diese Gruppe wird automatisch von AEM verwaltet.

### Rollback {#rollback-procedure}

Wenn bei der Migration Probleme auftreten:

1. Migrationsprozess stoppen
1. Wiederherstellung aus einem Backup, wenn kritische Daten betroffen waren
1. Setzt die Änderungen im Code zurück, um externe Benutzer und Gruppen mit dynamischer Gruppenmitgliedschaft zu erstellen
1. Überprüfen und beheben Sie Probleme, bevor Sie die Migration erneut versuchen.

## Best Practices {#best-practices}

* **Gründlich testen**: Migration immer in Entwicklungs- und Staging-Umgebungen vor der Produktion testen
* **Batch-Verarbeitung**: Verarbeiten Sie bei großen Benutzerbasen Migrationen in Batches, um Zeitüberschreitungsprobleme zu vermeiden
* **Leistung überwachen**: Überwachen der Repository-Leistung während der Migration
* **Audit-Protokoll**: Protokollieren Sie alle Migrationsvorgänge zur Fehlerbehebung.
* **Service-Benutzerberechtigungen**: Stellen Sie sicher, dass Migrations-Servlets geeignete Service-Benutzer mit den erforderlichen Berechtigungen verwenden. Der Dienstbenutzer muss in der Konfiguration ExternalPrincipal konfiguriert werden, um den Schutz für `rep:externalId`- und `rep:externalPrincipalNames`-Eigenschaften zu umgehen
* **Idempotente Vorgänge**: Entwerfen Sie Migrations-Code, damit er sicher erneut ausgeführt werden kann
* **Bei jedem Schritt überprüfen** Überprüfen Sie die Ergebnisse nach jedem Migrationsschritt, bevor Sie fortfahren

## Sichern von Migrations-Servlets {#securing-migration-servlets}

Die Migrations-Servlets verfügen über erweiterte Berechtigungen zum Erstellen und Ändern von Benutzern und Gruppen. Es ist wichtig, den Zugriff auf diese Endpunkte einzuschränken, um nicht autorisierten Zugriff zu verhindern.

### Empfohlener Ansatz: Authentifizierung des technischen IMS-Kontos {#recommended-approach-ims-technical-account}

Es wird empfohlen, diese Servlets mithilfe der Adobe IMS-Integration zu sichern, sodass nur ein autorisiertes technisches Konto darauf zugreifen kann.

#### Schritt 1: Erstellen eines technischen Kontos in AEM Developer Console {#create-a-technical-account-in-aem-developer-console}

1. Navigieren Sie zu [Experience Manager](https://experience.adobe.com/) und dann zu **Cloud Manager**
1. Wählen Sie Ihr Programm aus und klicken Sie dann auf die Umgebung, in der Sie das technische Konto erstellen möchten
1. Klicken Sie im **mit den Auslassungspunkten der Umgebung auf** Developer Console
1. Navigieren Sie in AEM Developer Console zur Registerkarte **Integrationen** .
1. Klicken Sie **Neues technisches Konto erstellen**
1. Geben Sie einen Namen für die Integration an (z. B. „Migration Service-Konto„).
1. Klicken Sie auf **Erstellen**.
1. Beachten Sie die folgenden Werte aus der erstellten Integration:
   * **Client-ID**
   * **Client-Geheimnis**
   * **ID des technischen Kontos** (dies ist die Benutzer-ID, die auf Ihre Servlets zugreift - Format: `XXXXXXXXXXXXXXXXXXXXXXXX@techacct.adobe.com`)

Detaillierte Anweisungen finden Sie unter [Generieren von Zugriffstoken für Server-seitige APIs - Dokumentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md).

Beispielcode zur Überprüfung, ob der Aufrufer berechtigt ist:

```
    private boolean isAuthorizedCaller(SlingHttpServletRequest request, 
                                       SlingHttpServletResponse response) {

        Session session = request.getResourceResolver().adaptTo(Session.class);
        String callerId = session != null ? session.getUserID() : null;
               
        if (!ALLOWED_TECHNICAL_ACCOUNT.equals(callerId)) {
            LOG.warn("Unauthorized access attempt by user: '{}' (expected: '{}')", callerId,   ALLOWED_TECHNICAL_ACCOUNT);
            response.setStatus(SlingHttpServletResponse.SC_FORBIDDEN);
            return false;
        }
        
        return true;
    }
```

### Detaillierte Verteidigung: IP-basierte Einschränkungen {#defense-in-depth-ip-based-restrictions}

Als zusätzliche Sicherheitsebene können Sie CDN-Regeln konfigurieren, um den Zugriff auf Migrationsendpunkte anhand der IP-Adresse einzuschränken. Dies ist nützlich, wenn Migrationen von einer bekannten Infrastruktur ausgeführt werden.

>[!NOTE]
>
>IP-Einschränkungen allein reichen nicht aus. Immer mit Authentifizierungsprüfungen kombinieren, wie oben beschrieben.

### Sicherheitscheckliste {#security-checklist}

Vor der Bereitstellung von Migrations-Servlets in der Produktion:

* Erstellen der IMS-Integration in AEM Developer Console
* Konfigurieren von Servlets zur Validierung der ID des technischen Kontos
* Testen des Authentifizierungsflusses in Entwicklungs-/Staging-Umgebungen
* Erwägen zusätzlicher IP-basierter Einschränkungen auf CDN-Ebene
* Planen Sie die Deaktivierung oder Entfernung von Migrationsservlets nach Abschluss der Migration
* Prüfen und Protokollieren des gesamten Zugriffs auf Migrationsendpunkte

>[!IMPORTANT]
>
>Nach Abschluss der Migration sollten Sie die Migrations-Servlets deaktivieren oder aus Ihrer -Bereitstellung entfernen, um potenzielle Sicherheitsrisiken zu vermeiden.

## Zusätzliche Ressourcen {#additional-resources}

* [Benutzer- und Gruppensynchronisierung für Veröffentlichungsebene](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md)
* [SAML 2.0-Authentifizierungs-Handler](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/authentication/saml-2-0.html?lang=de)
* [Externer Identitätsanbieter](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html)
* [Dynamische Gruppenmitgliedschaft](https://jackrabbit.apache.org/oak/docs/security/authentication/external/dynamic.html)
