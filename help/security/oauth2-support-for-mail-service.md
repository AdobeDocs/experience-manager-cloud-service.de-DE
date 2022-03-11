---
title: OAuth2-Unterstützung für den E-Mail-Service
description: OAuth2-Unterstützung für den E-Mail-Service in Adobe Experience Manager as a Cloud Service
exl-id: 93e7db8b-a8bf-4cc7-b7f0-cda481916ae9
source-git-commit: 4a5967f682d122d20528b1d904590fb82f438fa7
workflow-type: tm+mt
source-wordcount: '674'
ht-degree: 100%

---

# OAuth2-Unterstützung für den E-Mail-Service {#oauth2-support-for-the-mail-service}

AEM as a Cloud Service bietet OAuth2-Unterstützung für seinen integrierten E-Mail-Service, um Unternehmen die Einhaltung E-Mail-Sicherheitsanforderungen zu ermöglichen.

Sie können OAuth für mehrere E-Mail-Anbieter konfigurieren. Im Folgenden finden Sie eine schrittweise Anleitung zum Konfigurieren des AEM E-Mail-Service für die Authentifizierung über OAuth2 mit Microsoft Office 365 Outlook. Andere Anbieter können auf ähnliche Weise konfiguriert werden.

Weitere Informationen zum AEM as a Cloud Service E-Mail-Service finden Sie unter [Senden von E-Mails](/help/implementing/developing/introduction/development-guidelines.md#sending-email).

## Microsoft Outlook {#microsoft-outlook}

1. Gehen Sie zu [https://portal.azure.com/](https://portal.azure.com/) und melden Sie sich an.
1. Suchen Sie in der Suchleiste nach **Azure Active Directory** und klicken Sie auf das Ergebnis. Alternativ können Sie direkt zu [https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview](https://portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/Overview) gehen.
1. Klicken Sie auf **Registrierung einer Anwendung** – **Neue Registrierung**

   ![](assets/oauth-outlook1.png)

1. Füllen Sie die Informationen entsprechend Ihren Anforderungen aus und klicken Sie dann auf **Registrieren**
1. Wechseln Sie zur neu erstellten Anwendung und wählen Sie **API-Berechtigungen** aus.
1. Gehen Sie zu **Berechtigung hinzufügen** – **Diagrammberechtigungen** – **Zugewiesene Berechtigungen**.
1. Wählen Sie die folgenden Berechtigungen für Ihre Anwendung aus und klicken Sie dann auf **Berechtigung hinzufügen**:
   * `SMTP.Send`
   * `Mail.Read`
   * `Mail.Send`
   * `openid`
   * `offline_access`
1. Gehen Sie zu **Authentifizierung** – **Plattform hinzufügen** – **Web** und fügen Sie im Abschnitt **URLs umleiten** die folgenden URLs hinzu – eine mit und eine ohne Schrägstrich:
   * `http://localhost/`
   * `http://localhost`
1. Klicken Siei auf **Konfigurieren**, nachdem Sie jede URL hinzugefügt und Ihre Einstellungen Ihren Anforderungen entsprechend konfiguriert haben.
1. Gehen Sie dann zu **Zertifikate und Geheimnisse**, klicken Sie auf **Neues Client-Geheimnis** und führen Sie die Schritte auf dem Bildschirm aus, um ein Geheimnis zu erstellen. Notieren Sie sich dieses Geheimnis für die spätere Verwendung.
1. Klicken Sie auf **Überblick** im linken Bereich und kopieren Sie die Werte für **Anwendungs (Client) ID** und **Directory (Mandant) ID** zur späteren Verwendung.

Zusammenfassend benötigen Sie die folgenden Informationen, um OAuth2 für den E-Mail-Service auf der AEM-Seite zu konfigurieren:

* Die Auth-URL, die mit der Mandanten-ID erstellt wird. Sie hat folgendes Format: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize`
* Die Token-URL, die mit der Mandanten-ID erstellt wird. Sie hat folgendes Format: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Die Aktualisierungs-URL, die mit der Mandanten-ID erstellt wird. Sie hat folgendes Format: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/token`
* Die Client-ID
* Das Client-Geheimnis

### Erzeugen des Aktualisierungstokens {#generating-the-refresh-token}

Als Nächstes müssen Sie das Aktualisierungs-Token generieren, das in einem nachfolgenden Schritt Teil der OSGi-Konfiguration sein wird.

Gehen Sie dazu wie folgt vor:

1. Öffnen Sie die folgende URL im Browser, nachdem Sie `clientID` und `tenantID` durch die für Ihr Konto spezifischen Werte ersetzt haben: `https://login.microsoftonline.com/<tenantID>/oauth2/v2.0/authorize?client_id=<clientId>&response_type=code&redirect_uri=http://localhost&response_mode=query&scope=https%3A%2F%2Foutlook.office365.com%2FSMTP.Send%20EWS.AccessAsUser.All%20https%3A%2F%2Foutlook.office365.com%2FSMTP.Send%20https%3A%2F%2Foutlook.office365.com%2FMail.Read%20https%3A%2F%2Foutlook.office365.com%2FMail.Send%20openid%20offline_access&state=12345`
1. Auf Anfrage Berechtigung erteilen
1. Die URL wird an einen neuen Ort umgeleitet. Sie wird in folgendem Format erstellt: `http://localhost/?code=<code>&state=12345&session_state=4f984c6b-cc1f-47b9-81b2-66522ea83f81#`
1. Kopieren Sie den Wert von `<code>` im obigen Beispiel.
1. Verwenden Sie den folgenden cURL-Befehl, um das refreshToken abzurufen. Sie müssen die tenantID, clientID und clientSecret durch die Werte für Ihr Konto sowie den Wert für `<code>` ersetzen:

   ```
   curl --location --request POST 'https://login.microsoftonline.com/<tenantId>/oauth2/v2.0/token' \
   --header 'Content-Type: application/x-www-form-urlencoded' \
   --header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_5vR5dAQAAALDXP9gOAAAAwIpkkQEAAACT2T_YDgAAAA' \
   --data-urlencode 'client_id=<clientID>' \
   --data-urlencode 'scope=https://outlook.office365.com/SMTP.Send https://outlook.office365.com/Mail.Read https://outlook.office365.com/Mail.Send openid' \
   --data-urlencode 'redirect_uri=http://localhost' \
   --data-urlencode 'grant_type=authorization_code' \
   --data-urlencode 'client_secret=<clientSecret>' \
   --data-urlencode 'code=<code>'
   ```

1. Notieren Sie sich die Werte für refreshToken und accessToken.

### Validieren der Tokens {#validating-the-tokens}

Bevor Sie mit der OAuth-Konfiguration auf der AEM-Seite fortfahren, überprüfen Sie mit dem folgenden Verfahren sowohl accessToken als auch refreshToken:

1. Erzeugen Sie das accessToken mithilfe des im vorherigen Verfahren erstellten refreshToken. Sie können dies mit der folgenden URL erreichen, indem Sie die Werte für `<client_id>`,`<client_secret>` und `<refreshToken>` ersetzen:

   ```
   curl --location --request POST 'https://login.microsoftonline.com/<tenetId>/oauth2/v2.0/token' \
   --header 'Content-Type: application/x-www-form-urlencoded' \
   --header 'Cookie: buid=0.ARgAep0nU49DzUGmoP2wnvyIkcQjsx26HEpOnvHS0akqXQgYAAA.AQABAAEAAAD--DLA3VO7QrddgJg7Wevry9XPJSKbGVlPt5NWYxLtTl3K1W0LwHXelrffApUo_K02kFrkvmGm94rfBT94t25Zq4bCd5IM3yFOjWb3V22yDM7-rl112sLzbBQBRCL3QAAgAA; esctx=AQABAAAAAAD--DLA3VO7QrddgJg7Wevr4a8wBjYcNbBXRievdTOd15caaeAsQdXeBAQA3tjVQaxmrOXFGkKaE7HBzsJrzA-ci4RRpor-opoo5gpGLh3pj_iMZuqegQPEb1V5sUVQV8_DUEbBv5YFV2eczS5EAhLBAwAd1mHx6jYOL8LwZNDFvd2-MhVXwPd6iKPigSuBxMogAA; x-ms-gateway-slice=estsfd; stsservicecookie=estsfd; fpc=Auv6lTuyAP1FuOOCfj9w0U_IezHLAQAAAPeNSdgOAAAA' \
   --data-urlencode 'client_id=<client_id>' \
   --data-urlencode 'scope=https://outlook.office365.com/SMTP.Send https://outlook.office365.com/Mail.Read https://outlook.office365.com/Mail.Send openid' \
   --data-urlencode 'redirect_uri=http://localhost' \
   --data-urlencode 'grant_type=refresh_token' \
   --data-urlencode 'client_secret=<client_secret>' \
   --data-urlencode 'refresh_token=<refreshToken>'
   ```

1. Senden Sie eine E-Mail mit dem accessToken, um zu sehen, ob es ordnungsgemäß funktioniert.

>[!NOTE]
>
> Sie können die Postman-API-Sammlung von [diesem Speicherort](https://docs.microsoft.com/de-de/azure/active-directory/develop/v2-oauth2-auth-code-flow) abrufen.

### Integration mit AEM as a Cloud Service {#integration-with-aem-as-a-cloud-service}

1. Erstellen Sie eine OSGi-Eigenschaftendatei mit dem Namen `com.day.cq.mailer.oauth.impl.OAuthConfigurationProviderImpl.cfg.json` unter `/apps/<my-project>/osgiconfig/config` mit der folgenden Syntax:

   ```
   {
       authUrl: "<Authorization Url>",
       tokenUrl: "<Token Url>",
       clientId: "<clientID>",
       clientSecret: "$[secret:SECRET_SMTP_OAUTH_CLIENT_SECRET]",
       scopes: [
          "scope1",
          "scope2"
       ],
       refreshUrl: "<Refresh token Url>",
       refreshToken: "$[secret:SECRET_SMTP_OAUTH_REFRESH_TOKEN]"
   }
   ```

1. Füllen Sie die Felder `authUrl`, `tokenUrl` und `refreshURL` aus, indem Sie sie wie im vorherigen Abschnitt beschrieben erstellen.
1. Fügen Sie der Konfiguration die folgenden Umfänge hinzu:
   * `openid`
   * `offline_access`
   * `https://outlook.office365.com/Mail.Send`
   * `https://outlook.office365.com/Mail.Read`
   * `https://outlook.office365.com/SMTP.Send`
1. Erstellen Sie eine OSGi-Eigenschaftendatei `called com.day.cq.mailer.impl.DefaultMailService.cfg.json`
under 
`/apps/<my-project>/osgiconfig/config` mit der folgenden Syntax:

   ```
   {
    "smtp.host": "<smtp hostname>"
    "smtp.user": "<user account that logged into get the oauth tokens>",
    "smtp.password": "value not used",
    "smtp.port": 587,
    "from.address": "<from address used for sending>"
    "smtp.ssl": false,
    "smtp.starttls": true,
    "smtp.requiretls": true,
    "debug.email": false,
    "oauth.flow": true
   }
   ```

1. Für Outlook ist der `smtp.host`-Konfigurationswert `smtp.office365.com`.
1. Übergeben Sie zur Laufzeit die Geheimnisse `refreshToken values` und `clientSecret` mithilfe der Cloud Manager-Variablen-API wie [hier](/help/implementing/deploying/configuring-osgi.md#setting-values-via-api) beschrieben. Die Werte für die Variablen `SECRET_SMTP_OAUTH_REFRESH_TOKEN` und `SECRET_SMTP_OAUTH_CLIENT_SECRET` sollten definiert werden.

### Fehlerbehebung {#troubleshooting}

Wenn der E-Mail-Service nicht ordnungsgemäß funktioniert, müssen Sie in den meisten Fällen `refreshToken` wie oben beschrieben neu generieren und den neuen Wert über die Cloud Manager-API übergeben. Es dauert einige Minuten, bis der neue Wert bereitgestellt wird.
