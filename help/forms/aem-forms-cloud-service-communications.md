---
title: AEM Forms as a Cloud Service – Kommunikation
description: Automatisches Zusammenführen von Daten mit XDP- und PDF-Vorlagen oder Generieren von Ausgaben in den Formaten PCL, ZPL und PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: 33e59ce272223e081710294a2e2508edb92eba52
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 79%

---


# Verwenden der synchronen Verarbeitung {#sync-processing-introduction}

Forms as a Cloud Service - Kommunikations-APIs ermöglichen Ihnen das Erstellen, Zusammenstellen und Bereitstellen markenorientierter und personalisierter Kommunikationen wie Geschäftskorrespondenzen, Dokumente, Kontoauszüge, Antragsverarbeitungsbriefe, Benefizmitteilungen, Antragsbearbeitungsbriefe, Monatsrechnungen und Willkommenskits. Sie können Kommunikations-APIs verwenden, um eine Vorlage (XFA oder PDF) mit Kundendaten zu kombinieren und Dokumente im PDF-, PS-, PCL-, DPL-, IPL- und ZPL-Format zu generieren.

Angenommen, Sie haben eine oder mehrere Vorlagen und für jede Vorlage mehrere Datensätze mit XML-Daten. Sie können Kommunikations-APIs verwenden, um für jeden Eintrag ein Print-Dokument zu generieren. <!-- You can also combine the records into a single document. --> Das Ergebnis ist ein nicht interaktives PDF-Dokument. Bei einem nicht interaktiven PDF-Dokument können Benutzer keine Daten in die Felder eingeben.

Forms as a Cloud Service - Communications bietet On-Demand- und Batch-APIs (asynchrone APIs) für die geplante Dokumenterstellung:

* Synchrone APIs eignen sich für die Dokumenterstellung auf Anfrage, mit geringer Latenz und mit einzelnen Datensätzen. Diese APIs eignen sich besser für Anwendungen auf Basis einer Benutzeraktion. Zum Beispiel zum Generieren eines Dokuments, nachdem ein Anwender ein Formular ausgefüllt hat.

* Batch-APIs (asynchrone APIs) eignen sich für Anwendungsfälle für die geplante Erstellung mehrerer Dokumente mit hohem Durchsatz. Diese APIs generieren Dokumente in Stapeln. Beispielsweise werden damit monatliche Telefonrechnungen, Kreditkartenauszüge und Leistungsmitteilungen generiert.

## Verwenden von synchronen Vorgängen {#batch-operations}

Ein synchroner Vorgang ist ein Prozess, bei dem Dokumente linear generiert werden. Diese APIs werden als Single-Mandant-APIs und Multi-Mandant-APIs klassifiziert:

### Single-Mandant-APIs

* APIs zur Dokumenterstellung
* APIs zur Dokumentbearbeitung

<!-- 
### Multi-tenant APIs

* Document utility APIs -->


### Authentifizierung einer Single-Mandant-API

API-Vorgänge mit einem Mandanten unterstützen zwei Arten von Authentifizierung:

* **Einfache Authentifizierung**: Die einfache Authentifizierung ist ein einfaches Authentifizierungsschema, das in das HTTP-Protokoll integriert ist. Der Client sendet HTTP-Anfragen mit dem Autorisierungs-Header, der das Wort „Basic“, gefolgt von einem Leerzeichen und einer base64-kodierten Zeichenfolge „username:password“ enthält. Um beispielsweise als admin / admin zu autorisieren, sendet der Client Basic [base64-kodierte Zeichenfolge Benutzername]: [base64-kodierte Zeichenfolge Kennwort].

* **Token-basierte Authentifizierung:** Die Token-basierte Authentifizierung verwendet ein Zugriffstoken (Bearer-Authentifizierungstoken), um Anfragen an Experience Manager as a Cloud Service zu senden. AEM Forms as a Cloud Service stellt APIs zum sicheren Abrufen des Zugriffstokens bereit. So rufen Sie das Token ab und verwenden es, um eine Anfrage zu authentifizieren:

   1. [as a Cloud Service Berechtigung für Experience Manager aus der Developer Console abrufen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de).
   1. [as a Cloud Service Experience Manager-Anmeldedaten für Ihre Umgebung installieren](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de). (Programm-Server, Webserver oder andere Nicht-AEM-Server), die zum Senden von Anfragen an den Cloud-Service (Aufrufe) konfiguriert sind.
   1. [Erstellen Sie ein JWT-Token und tauschten Sie es mithilfe von Adobe IMS-APIs gegen ein Zugriffstoken aus](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de).
   1. Führen Sie die Experience Manager-API mit dem Zugriffstoken als Bearer-Authentifizierungstoken aus.
   1. [Legen Sie die entsprechenden Berechtigungen für den Benutzer des technischen Kontos in der Experience Manager-Umgebung fest](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=de#zugriff-in-aem-konfigurieren).

   >[!NOTE]
   >
   >Adobe empfiehlt die Verwendung der Token-basierten Authentifizierung in einer Produktionsumgebung.

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
1. Tap **[!UICONTROL Create new project]**. A screen to get started with your new project appears. Tap **[!UICONTROL Add API]**. A screen with list of all the APIs enabled for your account appears.
1. Select **[!UICONTROL AEM Forms - Communications]** and tap **[!UICONTROL Next]**. A screen to configure the API appears.
1. Select **[!UICONTROL OPTION 1 Generate a key pair]** and tap **[!UICONTROL Generate keypair]**. It creates and downloads the configuration file. The downloaded configuration file contains all your app settings, along with the only copy of your private key. Adobe does not record your private key, make sure to securely store the downloaded file. Tap **[!UICONTROL Next]**.
1. Select **[!UICONTROL Integrations - Cloud Service]** and tap **[!UICONTROL Save configured API]**. Tap **[!UICONTROL Service Account (JWT)]** to view the API Key, Client Secret, and other information required to access the APIs. You set to use the token to access the APIs.

#### Programmatically generate and use an access token

To programmatically generate an access token, generate a JSON Web Token (JWT) and exchange it with the Adobe Identity Management Service (IMS) for an access token.

Use the following keys, referred to as claims, to construct JWT JSON object:


* `exp`- the requested expiration of the access token, expressed as a number of seconds since January 1, 1970 GMT. For most use cases, this is a relatively small value. For example, 5 minutes, for five minutes from now, this value should be 1670923791.
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

* Benutzer mit Experience Manager-Administratorberechtigungen
* Hochladen von Vorlagen und anderen Assets in Ihre Experience Manager Forms Cloud Service-Instanz

### (Nur für APIs zur Dokumenterzeugung) Hochladen von Vorlagen und anderen Assets in Ihre Experience Manager-Instanz

Eine Organisation verfügt in der Regel über mehrere Vorlagen. Zum Beispiel eine Vorlage für Kreditkartenauszüge, Leistungsmitteilungen und Anträge. Laden Sie alle diese XDP- und PDF-Vorlagen in Ihre Experience Manager-Instanz hoch. Hochladen von Vorlagen:

1. Öffnen Sie die Experience Manager-Instanz.
1. Navigieren Sie zu „Forms“ > „Forms und Dokumente“.
1. Klicken Sie auf „Erstellen“ > „Ordner“ und erstellen Sie einen Ordner. Öffnen Sie den Ordner.
1. Klicken Sie auf „Erstellen“ > „Datei-Upload“ und laden Sie die Vorlagen hoch.

### Aufrufen einer API

Die [Dokumentation zur API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/) enthält detaillierte Informationen zu allen Parametern, Authentifizierungsmethoden und verschiedenen Services, die von APIs bereitgestellt werden. Die API-Referenzdokumentation enthält auch eine API-Definitionsdatei im .yaml-Format. Sie können die .yaml-Datei herunterladen und in [Postman](https://www.postman.com/) , um die Funktionalität der APIs zu überprüfen.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Nur Mitglieder der Gruppe „Formularbenutzer“ können auf Kommunikations-APIs zugreifen.
