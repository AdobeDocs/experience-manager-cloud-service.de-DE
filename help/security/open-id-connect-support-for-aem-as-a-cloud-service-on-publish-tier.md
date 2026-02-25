---
title: Open ID Connect-Unterstützung für AEM as a Cloud Service auf Veröffentlichungsebene
description: Erfahren Sie, wie Sie Open ID Connect (OIDC) für AEM as a Cloud Service auf der Veröffentlichungsebene einrichten
feature: Security
role: Admin
exl-id: d2f30406-546c-4a2f-ba88-8046dee3e09b
source-git-commit: c9b0f68751bbec69ff0d2a09aa3b7df31d35de3a
workflow-type: tm+mt
source-wordcount: '2153'
ht-degree: 66%

---

# Open ID Connect-Unterstützung für AEM as a Cloud Service auf Veröffentlichungsebene {#open-id-connect-support-for-aem-as-a-cloud-service-on-publish-tier}

## Einführung {#introduction}

Wenn Unternehmen ihre digitalen Erlebnisse modernisieren, wird sicheres und skalierbares Identitäts-Management zu einer grundlegenden Anforderung. Adobe Experience Manager (AEM) Cloud Service unterstützt jetzt OpenID Connect (OIDC) auf der Veröffentlichungsebene, was eine nahtlose und standardbasierte Integration mit führenden Identitätsanbietern (IDPs) wie Entra ID (Azure AD), Google, Okta, Auth0, Ping Identity, ForgeRock und von OIDC unterstützten IDPs ermöglicht.

OIDC ist eine Identitätsebene auf dem OAuth 2.0-Protokoll, die eine zuverlässige Benutzerauthentifizierung ermöglicht und gleichzeitig Entwicklungsfachleuten die Arbeit erleichtert. Sie wird häufig für B2C- (Business-to-Consumer), Intranet- und Partnerportalszenarien verwendet, in denen ein sicherer Verbund von Benutzeranmeldung und Identität erforderlich ist.

Bisher waren AEM-Kundinnen und -Kunden dafür verantwortlich, ihre eigene benutzerdefinierte Anmeldelogik auf der Veröffentlichungsebene zu implementieren. Dies hat die Entwicklungszeit verlängert und langfristige Wartungs- und Sicherheitsprobleme mit sich gebracht. Durch die native Unterstützung von OIDC beseitigt AEM Cloud Service diese Belastung, indem ein sicherer, erweiterbarer und von Adobe unterstützter Authentifizierungsmechanismus für Benutzende bereitgestellt wird, die auf Veröffentlichungsumgebungen zugreifen.

Unabhängig davon, ob Sie eine personalisierte Verbraucher-Website oder ein authentifiziertes internes Portal bereitstellen, vereinfacht OIDC auf der Veröffentlichungsebene die Identitätsverknüpfung und reduziert das Risiko durch zentralisierte Identitäts-Governance. Außerdem können Unternehmen moderne Compliance- und Sicherheitsstandards erfüllen, ohne auf Flexibilität zu verzichten.

## Konfigurieren von AEM für die OIDC-Authentifizierung {#configure-aem-oidc-authentication}

### Voraussetzungen {#prerequisits}

Wir gehen davon aus, dass die folgenden Informationen verfügbar oder definiert sind:

1. Die Pfade der zu schützenden Inhalte im AEM-Repository
1. Eine Kennung für den zu konfigurierenden IDP. Dies kann eine beliebige Zeichenfolge sein

Informationen aus der IDP-Konfiguration:

1. Die im IDP konfigurierte Client-ID
1. Das im IDP konfigurierte Client-Geheimnis. Wenn PKCE für den IDP konfiguriert wurde, ist das Client-Geheimnis nicht verfügbar. Speichern Sie den Nur-Text-Wert nicht in der Konfigurationsdatei. Verwenden Sie ein CM-Geheimnis und verweisen Sie darauf.
1. Die für den IDP konfigurierten Bereiche. Es muss mindestens der Bereich `openid` angegeben werden
1. Ob PKCE für den IDP aktiviert ist
1. Die `callbackUrl` wird mithilfe eines der konfigurierten Pfade definiert, die unter Punkt 1 definiert sind, und es wird das folgende Suffix hinzugefügt: `/j_security_check`
1. Die `baseUrl` für den Zugriff auf die standardmäßige `.well-known`-Datei. Wenn die bekannte URL beispielsweise `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0/.well-known/openid-configuration` ist, lautet die `baseUrl` so: `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891`

### Überblick über die Konfigurationsdateien {#overview-of-the-configuration-files}

Unten finden Sie eine Liste der Dateien, die konfiguriert werden müssen:

1. **OIDC-Verbindung**: Diese wird von `OidcAuthenticationHandler` zur Authentifizierung der Benutzenden verwendet. Andere Komponenten nutzen sie, um den [Zugriff auf Ressourcen zu autorisieren, die vom IDP mithilfe von OAuth geschützt werden](https://github.com/apache/sling-org-apache-sling-auth-oauth-client)
1. **OIDC-Authentifizierung-Handler**: Dies ist der Authentifizierungs-Handler, der zum Authentifizieren von Benutzenden verwendet wird, die auf die konfigurierten Pfade zugreifen
1. **UserInfoProcessor**: Diese Komponente verarbeitet die vom IDP empfangenen Informationen. Sie kann von Kunden erweitert werden, um benutzerdefinierte Logik zu implementieren
1. [**Standardmäßiger Synchronisierungs-Handler**](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html): Diese Komponente erstellt Benutzende im Repository
1. [**ExternalLoginModule**](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html): Diese Komponente authentifiziert Benutzende im lokalen Oak-Repository.

Das folgende Diagramm zeigt, wie die genannten Konfigurationselemente verknüpft sind. Da es sich hierbei um `ServiceFactory`-Komponenten handelt, kann `~uniqueid` eine beliebige eindeutige Zeichenfolge sein:

![OIDC-Konfigurationsdiagramm](/help/security/assets/oidc-diagram.png)

### Konfigurieren der OIDC-Verbindung {#configure-the-oidc-connection}

Zunächst müssen wir die OIDC-Verbindung konfigurieren. Es können mehrere OIDC-Verbindungen konfiguriert werden, von denen jede einen anderen Namen haben muss.

1. Erstellen Sie eine neue `.cfg.json`-Datei, in der die Konfiguration gespeichert wird. Sie können beispielsweise `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json` verwenden. Das Suffix **azure** muss eine eindeutige Kennung für die Verbindung sein
1. Befolgen Sie das Konfigurationsformat aus dem folgenden Beispiel:

   ```
   {
    "name":"azure",
    "scopes":[
      "openid"
    ],
    "baseUrl":"<https://login.microsoftonline.com/tenant-id/v2.0>",
    "clientId":"client-id-from-idp",
    "clientSecret":"xxxxxx"
   }
   ```

In einigen Umgebungen macht der Identitätsanbieter (IdP) möglicherweise keinen gültigen `.well-known`-Endpunkt verfügbar.
In diesem Fall können die erforderlichen Endpunkte manuell definiert werden, indem die folgenden Eigenschaften in der Konfigurationsdatei angegeben werden.
In diesem Konfigurationsmodus darf die `baseUrl`-Eigenschaft nicht festgelegt werden.

```
"authorizationEndpoint": "https://idp-url/oauth2/v1/authorize",
"tokenEndpoint": "https://idp-url/oauth2/v1/token",
"jwkSetURL":"https://idp-url/oauth2/v1/keys",
"issuer": "https://idp-url"
```

1. Konfigurieren Sie die Eigenschaften wie folgt:
   * Der **name** kann vom Benutzenden definiert werden
   * `baseUrl`, `clientid` und `clientSecret` sind Konfigurationswerte, die vom IDP stammen.
   * Die Bereiche müssen mindestens den Wert `openid` enthalten.

### Konfigurieren des OIDC-Authentifizierungs-Handlers {#configure-oidc-authentication-handler}

Konfigurieren Sie jetzt den OIDC-Authentifizierungs-Handler. Es können mehrere OIDC-Verbindungen konfiguriert werden. Jede muss einen anderen Namen haben. Wenn sie denselben [externen OAK-Identitätsanbieter](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html) nutzen, können sie Benutzende freigeben.

1. Erstellen Sie die Konfigurationsdatei. Für dieses Beispiel verwenden wir `org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json`. Das Suffix `azure` muss eine eindeutige Kennung sein. Ein Beispiel für die Konfigurationsdatei finden Sie unten:

   ```
   {
     "path":"/content/tests/us/en/test-7",
     "callbackUri":"http://localhost:14503/content/tests/us/en/test-7/j_security_check",
     "pkceEnabled":false,
     "defaultConnectionName":"azure"
     "idp": "azure-idp"
   }
   ```

1. Konfigurieren Sie dann die Eigenschaften wie folgt:
   * `path`: Der zu schützende Pfad
   * `callbackUri`: Der zu schützende Pfad, wobei das Suffix `/j_security_check` hinzugefügt wird. Derselbe CallbackUri muss auch in der Remote-ID als Umleitungs-URL konfiguriert werden.
   * `defaultConnectionName`: Konfigurieren Sie dies mit dem Namen, der für die OIDC-Verbindung im vorherigen Schritt definiert wurde+
   * `pkceEnabled`: `true` PKCE (Proof Key for Code Exchange) im Autorisierungs-Code-Fluss
   * `idp`: Der Name des [externen OAK-Identitätsanbieters](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html). Beachten Sie, dass ein anderer OAK-IDP keine Benutzenden oder Gruppen freigeben kann

### Konfigurieren von SlingUserInfoProcessor {#configure-slinguserinfoprocessor}

1. Erstellen Sie die Konfigurationsdatei. Für dieses Beispiel verwenden wir `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json`. Das Suffix `azure` muss eine eindeutige Kennung sein. Ein Beispiel für die Konfigurationsdatei finden Sie unten:

   ```
   {
      "groupsInIdToken":true,
      "groupsClaimName": "groups",
      "connection":"azure",
      "storeAccessToken": false,
      "storeRefreshToken": false,
      "idpNameInPrincipals": true
   }
   ```

1. Konfigurieren Sie dann die Eigenschaften wie folgt:
   * `groupsInIdToken`: Auf „true“ festgelegt, wenn die Gruppen im ID-Token gesendet werden. Wenn der Wert „false“ oder nicht angegeben ist, werden die Gruppen aus dem UserInfo-Endpunkt gelesen.
   * `groupsClaimName`: Name der Anforderung, die die in AEM zu synchronisierenden Gruppen enthält.
   * `connection`: Konfigurieren Sie dies mit dem Namen, der für die OIDC-Verbindung im vorherigen Schritt definiert wurde
   * `storeAccessToken`: „true“, wenn das Zugriffstoken im Repository gespeichert werden muss. Standardmäßig ist dies „false“. Legen Sie es nur dann auf „true“ fest, wenn AEM im Namen der Benutzenden auf Ressourcen zugreifen muss, die auf externen Servern gespeichert sind, die vom selben IDP geschützt werden.
   * `storeRefreshToken`: „true“, wenn das Aktualisierungstoken im Repository gespeichert werden muss. Standardmäßig ist dies „false“. Legen Sie ihn nur dann auf „true“ fest, wenn AEM im Namen des Benutzers auf Ressourcen zugreifen muss, die in externen Servern gespeichert sind, die durch dieselbe ID geschützt sind, und das Token von der ID aktualisieren muss.
   * `idpNameInPrincipals`: Bei Festlegung auf „true“ wird der Name der IDp als Suffix an die Benutzer- und Gruppenprinzipale angefügt, getrennt durch &quot;;“. Wenn beispielsweise der IdP-Name `azure-idp` und der Benutzername `john.doe` ist, wird der in Oak gespeicherte Prinzipal `john.doe;azure-idp`. Dies ist nützlich, wenn in Oak mehrere IDs konfiguriert sind, um Konflikte zwischen Benutzern oder Gruppen mit demselben Namen, die von verschiedenen IDs stammen, zu vermeiden. Diese Einstellung kann auch festgelegt werden, um Konflikte mit Benutzern oder Gruppen zu vermeiden, die von anderen Authentifizierungs-Handlern wie SAML erstellt wurden.
Beachten Sie, dass Zugriffstoken und Aktualisierungstoken mit dem AEM-Hauptschlüssel verschlüsselt gespeichert werden.


### Konfigurieren des Synchronisierungs-Handlers {#configure-the-synchronization-handler}

Es muss mindestens ein Synchronisierungs-Handler konfiguriert werden, um die in Oak authentifizierten Benutzenden zu synchronisieren. Weitere Details finden Sie auf [dieser](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html) Seite.

Erstellen Sie eine Datei mit dem Namen `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json`. Das Suffix **azure** muss eine eindeutige Kennung sein. Weitere Informationen zum Konfigurieren der Eigenschaften finden Sie in der [Dokumentation zur Benutzer- und Gruppensynchronisierung in Oak](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html). Nachfolgend sehen Sie eine Beispielkonfiguration:

```
{
  "user.expirationTime":"1h",
  "user.membershipExpTime":"1h",
  "group.expirationTime": "1d"
  "user.propertyMapping":[
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "access_token=access_token",
    "refresh_token=refresh_token"
  ],
  "user.pathPrefix":"azure",
  "handler.name":"azure"
}
```

Während der Entwicklung können die Ablaufzeiten auf einen niedrigeren Wert reduziert werden (z. B.: 1s), um das Testen der Benutzer- und Gruppensynchronisierung in Oak zu beschleunigen.
Im Folgenden finden Sie einige der relevantesten Attribute, die in DefaultSyncHandler konfiguriert werden müssen. Beachten Sie, dass die dynamische Gruppenmitgliedschaft immer in Cloud Services aktiviert sein sollte.

| Eigenschaftsname | Anmerkungen | Vorgeschlagener Wert |
|---|---|---|
| `user.expirationTime` | Dauer, bis synchronisierte Benutzende abgelaufen sind. Benutzende werden erst nach der Ablaufzeit synchronisiert. | 1 h |
| `user.membershipExpTime` | Dauer, bis eine synchronisierte Benutzemitgleidschaft abgelaufen ist. Benutzermitgliedschaften werden erst nach der Ablaufzeit synchronisiert. | 1 h |
| `user.dynamicMembership` | Es wird empfohlen, die dynamische Gruppenmitgliedschaft zu aktivieren | true |
| `user.enforceDynamicMembership` | Es wird empfohlen, die Durchsetzung der dynamischen Gruppenmitgliedschaft zu aktivieren | true |
| `group.dynamicGroups` | Es wird empfohlen, dynamische Gruppen zu aktivieren | true |
| user.propertyMapping | Die bereitgestellte Implementierung von `UserInfoProcessor` synchronisiert nur wenige Eigenschaften. Sie kann geändert und angepasst werden. | <code>&quot;profile/givenName=profile/given_name&quot;,</code><br><code>&quot;profile/familyName=profile/family_name&quot;,</code><br><code>&quot;rep:fullname=profile/name&quot;,</code><br><code>&quot;profile/email=profile/email&quot;,</code><br><code>&quot;access_token=access_token&quot;,</code><br><code>&quot;refresh_token=refresh_token&quot;</code> |
| `user.membershipNestingDepth` | Gibt die maximale Tiefe der Gruppenverschachtelung zurück, wenn Mitgliedschaftsbeziehungen synchronisiert werden. Der Wert 0 deaktiviert die Suche nach Gruppenzugehörigkeiten. Bei einem Wert von 1 werden nur die direkten Gruppen eines Benutzers hinzugefügt. Dieser Wert hat keinerlei Wirkung, wenn beim Synchronisieren der mitgliedsbezogenen Herkunft eines Benutzers nur einzelne Gruppen synchronisiert werden. | 1 |

### Konfigurieren des externen Anmeldemoduls {#configure-the-external-login-module}

Schließlich müssen Sie das externe Anmeldemodul konfigurieren.

1. Erstellen Sie eine Datei mit dem Namen `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json`. Unten sehen Sie eine Beispielkonfiguration:

   ```
   {
    "sync.handlerName":"azure",
    "idp.name":"azure-idp"
   }
   ```

1. Konfigurieren Sie die Eigenschaften wie folgt:

   * `sync.handlerName`: Name des zuvor definierten Synchronisierungs-Handlers
   * `idp.name`: Im OIDC-Authentifizierungs-Handler definierter OAK-Identitätsanbieter

### Optional: Implementieren eines benutzerdefinierten UserInfoProcessor {#implement-a-custom-userinfoprocessor}

Benutzende werden durch ein ID-Token authentifiziert und zusätzliche Attribute werden in dem für den IDP definierten `userInfo`-Endpunkt abgerufen. Wenn zusätzliche, nicht standardmäßige Vorgänge ausgeführt werden müssen, ist eine benutzerdefinierte Implementierung von [UserInfoProcessor](https://github.com/apache/sling-org-apache-sling-auth-oauth-client/blob/master/src/main/java/org/apache/sling/auth/oauth_client/impl/SlingUserInfoProcessorImpl.java) die Standardimplementierung von Sling.

### Konfigurieren von ACL für externe Gruppen {#configure-acl-for-external-groups}

Wenn Benutzer über OIDC authentifiziert werden, werden ihre Gruppenmitgliedschaften normalerweise mit dem externen Identitätsanbieter synchronisiert.
Diese externen Gruppen werden dynamisch im AEM-Repository erstellt, aber nicht automatisch mit Zugriffssteuerungseinträgen verknüpft.
Um sicherzustellen, dass Benutzende über die entsprechenden Berechtigungen verfügen, müssen für diese Gruppen explizit Zugriffssteuerungslisten (ACLs) definiert werden.

Es stehen zwei Hauptansätze zur Verfügung.

### Option 1 — Lokale Gruppen

Die externe Gruppe kann als Mitglied einer lokalen Gruppe hinzugefügt werden, die bereits über die erforderlichen ACLs verfügt.

* Die externe Gruppe muss im Repository vorhanden sein. Dies tritt automatisch auf, wenn sich ein Benutzer, der zu dieser Gruppe gehört, zum ersten Mal anmeldet.
* Diese Option wird im Allgemeinen bevorzugt, wenn geschlossene Benutzergruppen (CUGs) verwendet werden, da die lokale Gruppe sowohl in der Autoren- als auch in der Veröffentlichungsumgebung vorhanden ist.

### Option 2 - Direkte ACLs für externe Gruppen über RepoInit

ACLs können mithilfe von RepoInit-Skripten direkt auf externe Gruppen angewendet werden.

* Dieser Ansatz ist effizienter und wird bevorzugt, wenn keine CUGs verwendet werden.
* Das folgende Beispiel zeigt eine RepoInit-Konfiguration, die einer externen Gruppe Leseberechtigungen zuweist. Die Option ermöglicht `ignoreMissingPrincipal` die Erstellung der ACL, auch wenn die Gruppe noch nicht im Repository vorhanden ist:

  ```
  {
    "scripts":[
      "set ACL for \"my-group;my-idp\"  (ACLOptions=ignoreMissingPrincipal)\r\n  allow jcr:read on /content/wknd/us/en/magazine\r\nend"
    ]
  }    
  ```

>[!NOTE]
>Die Benutzeroberfläche für AEM-Berechtigungen kann verwendet werden, um die den Gruppenprinzipalen zugewiesenen ACLs zu überprüfen

## Beispiel: Konfigurieren der OIDC-Authentifizierung mit Azure Active Directory

### Konfigurieren einer neuen Anwendung in Azure Active Directory {#configure-a-new-application-in-azure-ad}

1. Erstellen Sie eine neue Anwendung in Azure Active Directory, indem Sie der [Azure Active Directory-Dokumentation](https://learn.microsoft.com/de-de/power-pages/security/authentication/openid-settings#create-an-app-registration-in-azure) folgen.  Unten sehen Sie, wie der Bildschirm mit Details zur Anwendungsübersicht aussehen sollte:

   ![Anwendungsübersicht](/help/security/assets/odic-application-overview.png)

1. Wenn Gruppen oder Anwendungsrollen erforderlich sind, befolgen Sie die [Dokumentation](https://learn.microsoft.com/de-de/entra/external-id/customers/how-to-use-app-roles-customers), um sie für die Anwendung zu aktivieren und im ID-Token zu senden. Nachfolgend sehen Sie ein Beispiel für konfigurierte Gruppen:

![OIDC-Anforderungstoken-ID](/help/security/assets/oidc-claim-id-token.png)

1. Führen Sie die zuvor dokumentierten Schritte aus, um die erforderlichen Konfigurationsdateien zu erstellen. Im Folgenden sehen Sie ein spezifisches Beispiel für Azure AD, bei dem Folgendes gilt:
   * Wir definieren den Namen der OIDC-Verbindung, den Authentifizierungs-Handler und DefaultSyncHandler wie folgt: `azure`
   * Die Website-URL ist: `www.mywebsite.com`
   * Wir schützen den Pfad `/content/wknd/us/en/adventures`, auf den nur authentifizierte Benutzer der Gruppe `adventures` zugreifen können
   * Der Mandant ist: `tennat-id`
   * Die Client-ID ist: `client-id`
   * Das Geheimnis ist: `secret`
   * Die Gruppen werden im ID-Token in einer Anforderung mit folgendem Namen gesendet: `groups`

### org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json

```
{
  "name":"azure",
  "scopes":[
    openid", "User.Read", "profile", "email"
  ],
  "baseUrl":"https://login.microsoftonline.com/tenant-id/v2.0",
  "clientId":"client-id",
  "clientSecret":"secret"
}
```

### org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json

```
{
  "callbackUri":"https://www.mywebsite.com/content/wknd/us/en/adventures/j_security_check",
  "path":[
    "/content/wknd/us/en/adventures"
  ],
  "idp":"azure",
  "defaultConnectionName":"azure"
}
```

### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json

```
{
  "sync.handlerName":"azure",
  "idp.name":"azure"
}
```

### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json

```
{
  "user.expirationTime":"1h",
  "user.membershipExpTime":"1h",
  "group.expirationTime": "1d"
  "user.propertyMapping":[
    "profile/givenName=profile/given_name",
    "profile/familyName=profile/family_name",
    "rep:fullname=profile/name",
    "profile/email=profile/email",
    "access_token=access_token",
    "refresh_token=refresh_token"
  ],
  "user.pathPrefix":"azure",
  "group.pathPrefix": "oidc",
  "user.membershipNestingDepth": "1",
  "handler.name":"azure"
}
```

### org.apache.sling.jcr.repoinit.RepositoryInitializer~azure.cfg.json

```
{
  "scripts":[
    "set ACL for \"adventures;azure\"  (ACLOptions=ignoreMissingPrincipal)\r\n  allow jcr:read on /content/wknd/us/en/adventures\r\nend"
  ]
}
```

### org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json

```
{
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false",
  "connection": "azure",
  "groupsClaimName": "groups"
}
```

### Zusätzliche Informationen zu Azure AD-Gruppen {#additional-information-about-azure-ad-groups}

Um eine Gruppe für die Enterprise-Anwendung im Microsoft Azure-Portal zu konfigurieren, müssen Sie die Anwendung nach **Enterprise-Anwendungen** durchsuchen und die Gruppen hinzufügen: <!-- Alexandru: this bit cound be clearer-->

![OIDC-Gruppe hinzufügen](/help/security/assets/oidc-ad-additional-info.png)

Um die Gruppenanforderung im ID-Token zu aktivieren, fügen Sie die Anforderung im Abschnitt **Tokenkonfiguration** des Microsoft Azure-Portals hinzu: <!-- Alexandru: this bit cound be clearer as well-->

![OIDC-Anforderungstoken ID](/help/security/assets/oidc-claim-id-token.png)

Die Konfiguration von `SlingUserInfoProcessor` muss wie im folgenden Beispiel geändert werden.

Der Dateiname, der geändert werden muss, ist `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl.cfg.json`. Der Inhalt muss wie folgt konfiguriert werden:

```
{
  "connection": "azure",
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false"
}
```

## Benutzerdefinierte Weiterleitung nach der Authentifizierung {#custom-redirect-after-authentication}

Standardmäßig werden Benutzer nach erfolgreicher OIDC-Authentifizierung zurück zur ursprünglich angeforderten URL geleitet. Sie können dieses Verhalten jedoch mithilfe des `redirect` Abfrageparameters anpassen.

### Verwenden des Weiterleitungsparameters

Beim Initiieren der Authentifizierung können Sie eine benutzerdefinierte Umleitungs-URL angeben, indem Sie den `redirect`-Parameter zu Ihrer Authentifizierungsanfrage hinzufügen:

```
/content/wknd/us/en/adventures?redirect=/content/wknd/us/en/welcome
```

In diesem Beispiel wird der Benutzer nach erfolgreicher Authentifizierung an `/content/wknd/us/en/welcome` anstelle der ursprünglich angeforderten Seite weitergeleitet.

### Sicherheitsbeschränkungen

Aus Sicherheitsgründen hat der `redirect`-Parameter die folgenden Einschränkungen:

* **Muss ein relativer Pfad sein**: Die Umleitungs-URL muss mit `/` beginnen (z. B. `/content/mysite/dashboard`)
* **Keine Site-übergreifenden Weiterleitungen**: Absolute URLs (z. B. `https://external-site.com`) sind nicht zulässig
* **Keine protokollrelativen URLs**: URLs, die mit `//` beginnen, werden zurückgewiesen, um protokollrelative Weiterleitungen zu verhindern

Wenn eine ungültige Umleitungs-URL angegeben wird, schlägt die Authentifizierung mit einem Fehler fehl.

### Beispiel-Anwendungsfälle

1. **Begrüßungsseite nach der Anmeldung**: Leitet Benutzer nach der ersten Anmeldung zu einer personalisierten Begrüßungsseite um.

   ```
   /content/mysite/secure-area?redirect=/content/mysite/welcome
   ```

2. **Dashboard-Umleitung**: Leitet Benutzer nach der Authentifizierung zu einem bestimmten Dashboard weiter

   ```
   /content/mysite/login?redirect=/content/mysite/user/dashboard
   ```

3. **Deep-Linking**: Zulassen, dass sich Benutzer authentifizieren und dann auf eine bestimmte Ressource zugreifen

   ```
   /content/mysite/protected?redirect=/content/mysite/protected/specific-document
   ```

## Migration vom SAML-Authentifizierungs-Handler zum OIDC-Authentifizierungs-Handler

Wenn AEM bereits mit einem SAML-Authentifizierungs-Handler konfiguriert ist und Benutzende mit aktivierter [Datensynchronisierung](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/personalization/user-and-group-sync-for-publish-tier#data-synchronization) im Repository vorhanden sind, können Konflikte zwischen den ursprünglichen SAML-Benutzenden und den neuen OIDC-Benutzenden auftreten.

1. Konfigurieren Sie [OidcAuthenticationHandler](#configure-oidc-authentication-handler) und aktivieren Sie `idpNameInPrincipals` in der Konfiguration [SlingUserInfoProcessor](#configure-slinguserinfoprocessor).
1. Einrichten [ACL für externe Gruppen](#configure-acl-for-external-groups).
1. Nach der Anmeldung von Benutzern können die alten Benutzer, die vom SAML-Authentifizierungs-Handler erstellt wurden, gelöscht werden.

>[!NOTE]
>Sobald der SAML-Authentifizierungs-Handler deaktiviert und der OIDC-Authentifizierungs-Handler aktiviert ist und [Datensynchronisierung](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/sites/authoring/personalization/user-and-group-sync-for-publish-tier#data-synchronization) nicht aktiviert ist, werden bestehende Sitzungen ungültig. Die Benutzer müssen sich erneut authentifizieren, was zur Erstellung neuer OIDC-Benutzerknoten im Repository führt.

