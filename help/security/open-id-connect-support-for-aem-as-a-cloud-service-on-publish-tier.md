---
title: Open ID Connect-Unterstützung für AEM as a Cloud Service auf Veröffentlichungsebene
description: Erfahren Sie, wie Sie Open ID Connect (OIDC) für AEM as a Cloud Service auf der Veröffentlichungsebene einrichten
feature: Security
role: Admin
exl-id: d2f30406-546c-4a2f-ba88-8046dee3e09b
source-git-commit: bf35f847f6f00d21915dfedb10cf38ea74344988
workflow-type: tm+mt
source-wordcount: '1469'
ht-degree: 4%

---

# Open ID Connect-Unterstützung für AEM as a Cloud Service auf Veröffentlichungsebene

## Einführung {#introduction}

Wenn Unternehmen ihre digitalen Erlebnisse modernisieren, wird ein sicheres und skalierbares Identitäts-Management zu einer grundlegenden Anforderung. Adobe Experience Manager (AEM) Cloud Service unterstützt jetzt OpenID Connect (OIDC) auf der Veröffentlichungsebene, was eine nahtlose und standardbasierte Integration mit führenden Identitätsanbietern (IdPs) wie Entra ID (Azure AD), Google, Okta, Auth0, Ping Identity, ForgeRock und von OIDC unterstützten IDPs ermöglicht.

OIDC ist eine Identitätsebene auf dem OAuth 2.0-Protokoll, die eine robuste Benutzerauthentifizierung ermöglicht und gleichzeitig Entwicklern die Arbeit erleichtert. Sie wird häufig für B2C- (Business-to-Consumer), Intranet- und Partnerportalszenarien verwendet, in denen eine sichere Benutzeranmeldung und Identitätsverbände erforderlich sind.

Bisher waren AEM-Kunden dafür verantwortlich, ihre eigene benutzerdefinierte Anmeldelogik auf der Veröffentlichungsebene zu implementieren, was die Entwicklungszeit verlängerte und langfristige Wartungs- und Sicherheitsprobleme mit sich brachte. Durch die native Unterstützung von OIDC beseitigt AEM Cloud Service diese Belastung, indem ein sicherer, erweiterbarer und von Adobe unterstützter Authentifizierungsmechanismus für Endbenutzer bereitgestellt wird, die auf Veröffentlichungsumgebungen zugreifen.

Unabhängig davon, ob Sie eine personalisierte Verbraucher-Website oder ein authentifiziertes internes Portal bereitstellen, vereinfacht OIDC auf Publish die Identitätsverknüpfung und reduziert das Risiko durch zentralisierte Identitäts-Governance. Außerdem können Unternehmen moderne Compliance- und Sicherheitsstandards erfüllen, ohne auf Flexibilität zu verzichten.

## Konfigurieren von AEM für OIDC-Authentifizierung {#configure-aem-oidc-authentication}

### Voraussetzungen {#prerequisits}

Wir gehen davon aus, dass die folgenden Informationen verfügbar oder definiert sind:

1. Die Pfade der zu schützenden Inhalte im AEM-Repository
1. Eine Kennung für die zu konfigurierende ID. Dies kann eine beliebige Zeichenfolge sein

Informationen aus der IdP-Konfiguration:

1. Die in der ID konfigurierte Client-ID
1. Das im IDP konfigurierte Client-Geheimnis. Wenn PKCE für den IDP konfiguriert wurde, ist der geheime Clientschlüssel nicht verfügbar. Speichern Sie den Nur-Text-Wert nicht in der Konfigurationsdatei. Verwenden von geheimen CM-Daten und Verweisen darauf
1. Die für den IDP konfigurierten Bereiche. Es muss mindestens der Umfang `openid` angegeben werden
1. Gibt an, ob PKCE für die IdP aktiviert ist
1. Der `callbackUrl` wird mithilfe eines der konfigurierten Pfade definiert, die unter Punkt 1 definiert sind, und es wird das Suffix hinzugefügt: `/j_security_check`
1. Die `baseUrl` für den Zugriff auf die standardmäßige `.well-known`. Wenn die bekannte URL beispielsweise lautet: `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0/.well-known/openid-configuration` lautet die `baseUrl`: `https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891`

### Überblick über die Konfigurationsdateien {#overview-of-the-configuration-files}

Unten finden Sie eine Liste der Dateien, die konfiguriert werden müssen:

1. **OIDC-Verbindung**: Dies wird vom `OidcAuthenticationHandler` zur Authentifizierung der Benutzer verwendet oder von anderen Komponenten, um den [ auf Ressourcen zu autorisieren, die von der ID mithilfe von OAuth geschützt sind](https://github.com/apache/sling-org-apache-sling-auth-oauth-client)
1. **OIDC Authentication Handler**: Dies ist der Authentifizierungs-Handler, der zum Authentifizieren von Benutzern verwendet wird, die auf die konfigurierten Pfade zugreifen
1. **UserInfoProcessor**: Diese Komponente verarbeitet die vom IdP empfangenen Informationen. Sie kann von Kunden erweitert werden, um benutzerdefinierte Logik zu implementieren
1. [**Standard-Synchronisierungshandler**](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html): Diese Komponente erstellt den Benutzer im Repository
1. [**ExternalLoginModule**](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html): Diese Komponente authentifiziert den Benutzer im lokalen Oak-Repository.

Das folgende Diagramm zeigt, wie die genannten Konfigurationselemente verknüpft sind. Da es sich hierbei um `ServiceFactory` Komponenten handelt, kann der `~uniqueid` eine beliebige eindeutige Zeichenfolge sein:

![OIDC-Konfigurationsschema](/help/security/assets/oidc-diagram.png)

### Konfigurieren der OIDC-Verbindung {#configure-the-oidc-connection}

Zunächst müssen wir die OIDC-Verbindung konfigurieren. Es können mehrere OIDC-Verbindungen konfiguriert werden, von denen jede einen anderen Namen haben muss.

1. Erstellen Sie eine neue `.cfg.json`, in der die Konfiguration gespeichert wird. Sie können beispielsweise `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json` verwenden. Das Suffix **azure** muss eine eindeutige Kennung für die Verbindung sein
1. Befolgen Sie das Konfigurationsformat im folgenden Beispiel:

   ```
   {
    "name":"azure",
    "scopes":[
      "openid"
    ],
    "baseUrl":"<https://login.microsoftonline.com/53279d7a-438f-41cd-a6a0-fdb09efc8891/v2.0>",
    "clientId":"5199fc45-8000-473e-ac63-989f1a78759f",
    "clientSecret":"xxxxxx"
   }
   ```

1. Konfigurieren Sie die Eigenschaften wie folgt:
   * Der **„name** kann vom Benutzer definiert werden
   * `baseUrl`, `clientid` und `clientSecret` sind Konfigurationswerte, die vom IdP kommen.
   * Die Bereiche müssen mindestens den Wert `openid` enthalten.

### Konfigurieren des OIDC-Authentifizierungs-Handlers {#configure-oidc-authentication-handler}

Konfigurieren Sie jetzt den OIDC-Authentifizierungs-Handler. Es können mehrere OIDC-Verbindungen konfiguriert werden. Jeder muss einen anderen Namen haben. Wenn sie denselben [externen OAK-Identitätsanbieter](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html) nutzen, können sie Benutzer freigeben.

1. Erstellen Sie die Konfigurationsdatei. Für dieses Beispiel verwenden wir `org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json`. Das `azure` Suffix muss eine eindeutige Kennung sein. Ein Beispiel für die Konfigurationsdatei finden Sie unten:

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
   * `callbackUri`: Fügen Sie zum zu schützenden Pfad das Suffix `/j_security_check` hinzu
   * `defaultConnectionName`: Mit demselben Namen konfigurieren, der für die OIDC-Verbindung im vorherigen Schritt definiert wurde+
   * `pkceEnabled`: `true` Proof Key for Code Exchange (PKCE) im Autorisierungs-Code-Fluss
   * `idp`: Der Name des [externen OAK-Identitätsanbieters](https://jackrabbit.apache.org/oak/docs/security/authentication/identitymanagement.html). Beachten Sie, dass ein anderer OAK-IDP keine Benutzenden oder Gruppen freigeben kann

### Konfigurieren von SlingUserInfoProcessor

1. Erstellen Sie die Konfigurationsdatei. Für dieses Beispiel verwenden wir `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessor~azure.cfg.json`. Das `azure` Suffix muss eine eindeutige Kennung sein. Ein Beispiel für die Konfigurationsdatei finden Sie unten:

   ```
   {
      "groupsInIdToken":true,
      "groupsClaimName": "groups",
      "connection":"azure",
      "storeAccessToken": false,
      "storeRefreshToken": false
   }
   ```

1. Konfigurieren Sie dann die Eigenschaften wie folgt:
   * `groupsInIdToken`: Auf „true“ gesetzt, wenn die Gruppen im ID-Token gesendet werden. Wenn der Wert „false“ oder nicht angegeben ist, werden die Gruppen aus dem UserInfo-Endpunkt gelesen.
   * `groupsClaimName`: Name des Anspruchs, der die in AEM zu synchronisierenden Gruppen enthält.
   * `connection`: Konfigurieren Sie mit demselben Namen, der für die OIDC-Verbindung im vorherigen Schritt definiert wurde
   * `storeAccessToken`: „true“, wenn das Zugriffstoken im Repository gespeichert werden muss. Standardmäßig ist dies „false“. Legen Sie ihn nur dann auf „true“ fest, wenn AEM im Namen des Benutzers auf Ressourcen zugreifen muss, die auf externen Servern gespeichert sind, die von derselben ID geschützt werden.
   * `storeRefreshToken`: „true“, wenn das Aktualisierungs-Token im Repository gespeichert werden muss. Standardmäßig ist dies „false“. Legen Sie ihn nur dann auf „true“ fest, wenn AEM im Namen des Benutzers auf Ressourcen zugreifen muss, die in externen Servern gespeichert sind, die durch dieselbe ID geschützt sind, und das Token von der ID aktualisieren muss.
Beachten Sie, dass Zugriffstoken und Aktualisierungstoken mit dem AEM-Hauptschlüssel verschlüsselt gespeichert werden.


### Konfigurieren des Synchronisierungs-Handlers {#configure-the-synchronization-handler}

Es muss mindestens ein Synchronisierungshandler konfiguriert werden, um die in Oak authentifizierten Benutzer zu synchronisieren. Weitere Informationen finden Sie auf [dieser](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html) Seite.

Erstellen Sie eine Datei mit dem Namen `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json`. Das **azure**-Suffix muss ein eindeutiger Bezeichner sein. Weitere Informationen zum Konfigurieren der Eigenschaften finden Sie in der Dokumentation zur [Oak-Benutzer- und Gruppensynchronisierung](https://jackrabbit.apache.org/oak/docs/security/authentication/external/defaultusersync.html). Nachfolgend finden Sie eine Beispielkonfiguration:

```
{
  "user.expirationTime":"300s",
  "user.membershipExpTime":"300s",
  "user.propertyMapping":[
    "profile/familyName=profile/familyName",
    "profile/givenName=profile/givenName",
    "rep:fullname=cn",
    "profile/email=profile/email",
    "oauth-tokens"
  ],
  "user.pathPrefix":"azure",
  "handler.name":"azure"
}
```

Im Folgenden finden Sie einige der relevantesten Attribute, die in DefaultSyncHandler konfiguriert werden müssen. Beachten Sie, dass die dynamische Gruppenmitgliedschaft immer in Cloud Services aktiviert sein sollte.

| Eigenschaftsname | Anmerkungen | Vorgeschlagener Wert |
|---|---|---|
| `user.expirationTime` | Dauer, bis synchronisierte Benutzerinnen und Benutzer abgelaufen sind. Benutzer werden erst nach Ablauf der Zeit synchronisiert. | 1 h |
| `user.membershipExpTime` | Dauer, bis eine synchronisierte Benutzermitgliedschaft abgelaufen ist. Benutzermitgliedschaften werden erst nach Ablauf der Zeit synchronisiert. | 1 h |
| `user.dynamicMembership` | Es wird empfohlen, eine dynamische Gruppenmitgliedschaft zu aktivieren | Ja |
| `user.enforceDynamicMembership` | Es wird empfohlen, die Durchsetzung der dynamischen Gruppenmitgliedschaft zu aktivieren | Ja |
| `group.dynamicGroups` | Es wird empfohlen, dynamische Gruppen zu aktivieren | Ja |
| user.propertyMapping | Die bereitgestellte Implementierung von `UserInfoProcessor` synchronisiert nur wenige Eigenschaften. Sie kann geändert und angepasst werden. | <code>„profile/givenName=profile/given_name“,</code><br><code>„profile/familyName=profile/family_name“,</code><br><code>„rep:fullname=profile/name“,</code><br><code>„profile/email=profile/email“,</code><br><code>„access_token=access_token“,</code><br><code>„refresh_token=refresh_token“</code> |  |
| `user.membershipNestingDepth` | Gibt die maximale Tiefe der Gruppenverschachtelung zurück, wenn Mitgliedschaftsbeziehungen synchronisiert werden. Der Wert 0 deaktiviert die Suche nach Gruppenmitgliedschaften. Bei einem Wert von 1 werden nur die direkten Gruppen eines Benutzers hinzugefügt. Dieser Wert hat keinerlei Wirkung, wenn beim Synchronisieren der mitgliedsbezogenen Herkunft eines Benutzers nur einzelne Gruppen synchronisiert werden. | 1 |

### Konfigurieren des externen Anmeldemoduls {#configure-the-external-login-module}

Schließlich müssen Sie das externe Anmeldemodul konfigurieren.

1. Erstellen Sie eine Datei mit dem Namen `org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json`. Siehe eine Beispielkonfiguration unten:

   ```
   {
    "sync.handlerName":"azure",
    "idp.name":"azure-idp"
   }
   ```

1. Konfigurieren Sie die Eigenschaften wie folgt:

   * `sync.handlerName`: Name des zuvor definierten Synchronisierungs-Handlers
   * `idp.name`: OAK Identity Provider im OIDC-Authentifizierungs-Handler definiert

### Optional: Implementieren eines benutzerdefinierten UserInfoProcessor {#implement-a-custom-userinfoprocessor}

Der Benutzer wird durch ein ID-Token authentifiziert und zusätzliche Attribute werden in dem für die ID definierten `userInfo`-Endpunkt abgerufen. Wenn zusätzliche, nicht standardmäßige Vorgänge ausgeführt werden müssen, ist eine benutzerdefinierte Implementierung des [UserInfoProcessor](https://github.com/apache/sling-org-apache-sling-auth-oauth-client/blob/master/src/main/java/org/apache/sling/auth/oauth_client/impl/SlingUserInfoProcessorImpl.java) die Standardimplementierung von Sling.

## Beispiel: OIDC-Authentifizierung mit Azure Active Directory konfigurieren

### Konfigurieren einer neuen Anwendung in Azure Active Directory {#configure-a-new-application-in-azure-ad}

1. Erstellen Sie eine neue Anwendung in Azure Active Directory, indem Sie der [Azure Active Directory-Dokumentation](https://learn.microsoft.com/en-us/power-pages/security/authentication/openid-settings#create-an-app-registration-in-azure) folgen.  Unten sehen Sie, wie der Bildschirm mit Details zur Programmübersicht aussehen sollte:

   ![Anwendungsübersicht](/help/security/assets/odic-application-overview.png)

1. Wenn Gruppen oder Anwendungsrollen erforderlich sind, befolgen Sie die [Dokumentation](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-use-app-roles-customers), um sie für die Anwendung zu aktivieren und im ID-Token zu senden. Nachfolgend finden Sie ein Beispiel für konfigurierte Gruppen:

![OIDC Claim Token ID](/help/security/assets/oidc-claim-id-token.png)

1. Führen Sie die zuvor dokumentierten Schritte aus, um die erforderlichen Konfigurationsdateien zu erstellen. Im Folgenden finden Sie ein spezifisches Beispiel für Azure AD, bei dem:
   * Wir definieren den Namen von oidc Connection, Authentication Handler und DefaultSyncHandler wie folgt: `azure`
   * Die Website-URL lautet: `www.mywebsite.com`
   * Wir schützen den Pfad `/content/wknd/us/en/adventures`
   * Mandant ist: `tennat-id`,
   * Client-ID ist: `client-id`,
   * Geheimnis ist: `secret`,
   * Die Gruppen werden im ID-Token in einem Anspruch namens gesendet`groups`

#### org.apache.sling.auth.oauth_client.impl.OidcConnectionImpl~azure.cfg.json

```
{
  "name":"azure",
  "scopes":[
    openid", "User.Read", "profile", "email
  ],
  "baseUrl":"https://login.microsoftonline.com/tenant-id/v2.0",
  "clientId":"client-id",
  "clientSecret":"secret"
}
```

#### org.apache.sling.auth.oauth_client.impl.OidcAuthenticationHandler~azure.cfg.json

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

#### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory~azure.cfg.json

```
{
  "sync.handlerName":"azure",
  "idp.name":"azure"
}
```

#### org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler~azure.cfg.json

```
{
  "user.expirationTime":"1s",
  "user.membershipExpTime":"1s",
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

#### org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl~azure.cfg.json

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

Um eine Gruppe für die Unternehmensanwendung im Microsoft Azure-Portal zu konfigurieren, müssen Sie die Anwendung nach folgenden Elementen durchsuchen: **Unternehmensanwendungen** und die Gruppen hinzufügen: <!-- Alexandru: this bit cound be clearer-->

![OIDC-Gruppe hinzufügen](/help/security/assets/oidc-ad-additional-info.png)

Um den Gruppenanspruch im ID-Token zu aktivieren, fügen Sie den Anspruch im Abschnitt **Token-Konfiguration** des Microsoft Azure-Portals hinzu: <!-- Alexandru: this bit cound be clearer as well-->

![OIDC Claim Token ID](/help/security/assets/oidc-claim-id-token.png)

Die Konfiguration von `SlingUserInfoProcessor` muss wie im folgenden Beispiel geändert werden.

Der Dateiname, der geändert werden muss, ist `org.apache.sling.auth.oauth_client.impl.SlingUserInfoProcessorImpl.cfg.json`. Der Inhalt sollte wie folgt konfiguriert werden:

```
{
  "connection": "azure",
  "groupsInIdToken": "true",
  "storeAccessToken": "false",
  "storeRefreshToken": "false"
}
```
