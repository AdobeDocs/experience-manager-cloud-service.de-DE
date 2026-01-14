---
title: Wie kann Forms as a Cloud Service verwendet werden, um Daten mit XDP- und PDF-Vorlagen zusammenzuführen oder Ausgaben in den Formaten PCL, ZPL und PostScript zu generieren?
description: Automatisches Zusammenführen von Daten mit XDP- und PDF-Vorlagen oder Generieren von Ausgaben in den Formaten PCL, ZPL und PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
feature: Adaptive Forms,APIs & Integrations
role: Admin, Developer, User
source-git-commit: 43b648eb3984867fda35ee04de10b78dd836b481
workflow-type: tm+mt
source-wordcount: '725'
ht-degree: 91%

---


# Verwenden der synchronen Verarbeitung {#sync-processing-introduction}

Forms as a Cloud Service – Mit den Kommunikations-APIs können Sie markenorientierte und personalisierte Texte erstellen, zusammenstellen und bereitstellen, wie z. B.  Geschäftskorrespondenz, Dokumente, Kontoauszüge, Briefe zur Bearbeitung von Ansprüchen, Leistungsbescheide, monatliche Rechnungen oder Begrüßungspakete. Sie können Communications APIs verwenden, um eine Vorlage (XFA oder PDF) mit Kundendaten zu kombinieren und damit Dokumente im PDF-, PS-, PCL-, DPL-, IPL- und ZPL-Format zu generieren.

Angenommen, Sie haben eine oder mehrere Vorlagen und für jede Vorlage mehrere Einträge mit XML-Daten. Sie können Kommunikations-APIs verwenden, um für jeden Eintrag ein Print-Dokument zu generieren. <!-- You can also combine the records into a single document. --> Das Ergebnis ist ein nicht interaktives PDF-Dokument. Bei einem nicht interaktiven PDF-Dokument können Benutzer keine Daten in die Felder eingeben.

Forms as a Cloud Service Communications bietet On-Demand- und Batch-APIs (asynchrone APIs) für die geplante Dokumenterstellung:

* Synchrone APIs eignen sich für die Dokumenterstellung auf Anfrage, mit geringer Latenz und mit einzelnen Einträgen. Diese APIs eignen sich besser für Anwendungen auf Basis einer Benutzeraktion. Zum Beispiel zum Generieren eines Dokuments, nachdem ein Anwender ein Formular ausgefüllt hat.

* Batch-APIs (asynchrone APIs) eignen sich für Anwendungsfälle für die geplante Erstellung mehrerer Dokumente mit hohem Durchsatz. Diese APIs generieren Dokumente in Stapeln. Beispielsweise werden damit monatliche Telefonrechnungen, Kreditkartenauszüge und Leistungsmitteilungen generiert.

## Verwenden von synchronen Vorgängen {#batch-operations}

Ein synchroner Vorgang ist ein Prozess, bei dem Dokumente linear generiert werden. Diese APIs werden als Einzelmandant-APIs und Multi-Mandant-APIs klassifiziert:

### Einzelmandant-APIs

* APIs zur Dokumenterstellung
* APIs zur Dokumentbearbeitung

<!-- 
### Multi-tenant APIs

* Document utility APIs -->


### Authentifizierung einer Einzelmandant-API

Einzelmandant-API-Vorgänge unterstützen zwei Authentifizierungstypen:

* **Einfache Authentifizierung**: Die einfache Authentifizierung ist ein einfaches Authentifizierungsschema, das in das HTTP-Protokoll integriert ist. Der Client sendet HTTP-Anfragen mit dem Autorisierungs-Header, der das Wort „Basic“ enthält, gefolgt von einem Leerzeichen und einem base64-kodierten Zeichenfolge-Benutzernamen:password. Um beispielsweise als admin / admin zu autorisieren, sendet der Client Basic [base64-kodierte Zeichenfolge Benutzername]: [base64-kodierte Zeichenfolge Kennwort].

* **Token-basierte Authentifizierung:** Die Token-basierte Authentifizierung verwendet ein Zugriffstoken (Bearer-Authentifizierungstoken), um Anfragen an Experience Manager as a Cloud Service zu senden. AEM Forms as a Cloud Service stellt APIs zum sicheren Abrufen des Zugriffstokens bereit. So rufen Sie das Token ab und verwenden es, um eine Anfrage zu authentifizieren:

   1. [Rufen Sie die Anmeldedaten für Experience Manager as a Cloud Service über die Entwicklerkonsole ab](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de).
   1. [Installieren Sie die Anmeldedaten für Experience Manager as a Cloud Service in Ihrer Umgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de). (Programm-Server, Webserver oder andere Nicht-AEM-Server), die zum Senden von Anfragen an den Cloud-Service (Aufrufe) konfiguriert sind.
   1. [Erstellen Sie ein JWT-Token und tauschten Sie es mithilfe von Adobe IMS-APIs gegen ein Zugriffstoken aus](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de).
   1. Führen Sie die Experience Manager-API mit dem Zugriffstoken als Bearer-Authentifizierungstoken aus.
   1. [Legen Sie die entsprechenden Berechtigungen für den Benutzer des technischen Kontos in der Experience Manager-Umgebung fest](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de#zugriff-in-aem-konfigurieren).

  >[!NOTE]
  >
  >Adobe empfiehlt die Verwendung der Token-basierten Authentifizierung in einer Produktionsumgebung.

  >[!IMPORTANT]
  >
  > Weitere Informationen finden Sie unter [OAuth-Server-zu-Server](/help/forms/oauth-api-authetication.md)Authentifizierung und [JWT-Server-zu-Server-Authentifizierung](/help/forms/jwt-api-authentication.md).
<!-- 

### Authenticate a multi-tenant API

#### Authentication Headers

Every inbound HTTP API call to the multi-tenant API must contain these three headers:


* `x-api-key`
* `x-gw-ims-org-id`
* `Authorization`

The values which should be sent in the `x-api-key` and `x-gw-ims-org-id` headers are provided in the Credentials details screen in the [Adobe Developer Console](https://developer.adobe.com/console). The value of the `x-api-key` header is the Client ID and the value for the `x-gw-ims-org-id` header is the Organization ID.

#### Configure Adobe Developer console to generate an access token

To set up authentication APIs, create a project in Adobe Developer Console and add Communication APIs to the project on Adobe Developer Console. The integration generates API Key, Client Secret, Payload (JWT):

1. Contact you Adobe Developer Console administrator. Ask the administrator to add as a developer.
1. Log in to `https://developer.adobe.com/console/`. Use your developer account that your administrator has provisioned to log in to Adobe Developer Console.
1. Select your organization from the top-right corner. If you do not know your organization, contact your administrator.
1. Select **[!UICONTROL Create new project]**. A screen to get started with your new project appears. Select **[!UICONTROL Add API]**. A screen with list of all the APIs enabled for your account appears.
1. Select **[!UICONTROL AEM Forms - Communications]** and select **[!UICONTROL Next]**. A screen to configure the API appears.
1. Select **[!UICONTROL OPTION 1 Generate a key pair]** and select **[!UICONTROL Generate keypair]**. It creates and downloads the configuration file. The downloaded configuration file contains all your app settings, along with the only copy of your private key. Adobe does not record your private key, make sure to securely store the downloaded file. Select **[!UICONTROL Next]**.
1. Select **[!UICONTROL Integrations - Cloud Service]** and select **[!UICONTROL Save configured API]**. Select **[!UICONTROL Service Account (JWT)]** to view the API Key, Client Secret, and other information required to access the APIs. You set to use the token to access the APIs.

#### Programmatically generate and use an access token

To programmatically generate an access token, generate a JSON Web Token (JWT) and exchange it with the Adobe Identity Management Service (IMS) for an access token.

Use the following keys, referred to as claims, to construct JWT JSON object:


* `exp`- the requested expiration of the access token, expressed as several seconds since January 1, 1970 GMT. For most use cases, this is a relatively small value. For example, 5 minutes, for five minutes from now, this value should be 1670923791.
* `iss` - the Organization ID from the Adobe Developer Console project, in the format org_ident@AdobeOrg.
* `sub` - the Technical Account ID from the Adobe Developer Console integration, in the format: id@techacct.adobe.com.
* `aud` - the Client ID from the Adobe Developer Console integration prepended with `https://ims-na1.adobelogin.com/c/`.
* `https://ims-na1-stg1.adobelogin.com/s/ent_aemforms_docprocessing` - set to the literal value `true`

This JSON object must be then base64 encoded and signed using the private key for the project. Finally, the encoded value is sent in the body of a POST request to `https://ims-na1.adobelogin.com/ims/exchange/jwt` along with the Client ID and Client Secret for the project.

##### Example

```JSON

    ========================= REQUEST ==========================
    POST https://ims-na1.adobelogin.com/ims/exchange/jwt
    -------------------------- body ----------------------------
    client_id={myClientId}&client_secret={myClientSecret}&jwt_token={myJSONWebToken}
    ------------------------- headers --------------------------
    Content-Type: application/x-www-form-urlencoded
    Cache-Control: no-cache

```

#### Language Support for JWT

While it is possible to do the entire JWT generation and exchange process in custom code, it is more common to use a higher-level library to do so. A number of such libraries are listed on the [Adobe I/O JWT Documentation](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/).

-->

### (Nur für APIs zur Dokumenterzeugung) Konfigurieren von Assets und Berechtigungen

Um synchrone APIs zu verwenden, ist Folgendes erforderlich:

* Benutzende mit Experience Manager-Administratorberechtigungen
* Hochladen von Vorlagen und anderen Assets in Ihre Experience Manager Forms Cloud Service-Instanz

### (Nur für APIs zur Dokumenterzeugung) Hochladen von Vorlagen und anderen Assets in Ihre Experience Manager-Instanz

Eine Organisation verfügt in der Regel über mehrere Vorlagen. Zum Beispiel eine Vorlage für Kreditkartenauszüge, Leistungsmitteilungen und Anträge. Laden Sie alle diese XDP- und PDF-Vorlagen in Ihre Experience Manager-Instanz hoch. Hochladen von Vorlagen:

1. Öffnen Sie die Experience Manager-Instanz.
1. Navigieren Sie zu „Forms“ > „Forms und Dokumente“.
1. Klicken Sie auf „Erstellen“ > „Ordner“ und erstellen Sie einen Ordner. Öffnen Sie den Ordner.
1. Klicken Sie auf „Erstellen“ > „Datei-Upload“ und laden Sie die Vorlagen hoch.

### Aufrufen einer API

Die [Dokumentation zur API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) enthält detaillierte Informationen zu allen Parametern, Authentifizierungsmethoden und verschiedenen Services, die von APIs bereitgestellt werden. Die API-Referenzdokumentation enthält auch eine API-Definitionsdatei im .yaml-Format. Sie können die .yaml-Datei herunterladen und in [Postman](https://www.postman.com/) hochladen, um die Funktionalität der APIs zu überprüfen.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
> Die detaillierten Schritte zum Aufrufen von AEM Forms-Kommunikations-APIs finden Sie im Artikel [Aufrufen von AEM Forms-Kommunikations-APIs mithilfe der OAuth-Server-zu-Server-Authentifizierung](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md) .

>[!MORELIKETHIS]
>
>* [Einführung in die Kommunikationsfunktion von AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-communications-introduction.md)
>* [AEM Forms as a Cloud Service-Architektur für adaptive Formulare und Kommunikations-APIs](/help/forms/aem-forms-cloud-service-architecture.md)
>* [Kommunikationsverarbeitung – synchrone APIs](/help/forms/aem-forms-cloud-service-communications.md)
>* [Kommunikationsverarbeitung – Batch-APIs](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
>* [Forms-Kommunikations-API - Tutorial](/help/forms/aem-forms-cloud-service-communications-on-demand-processing.md)