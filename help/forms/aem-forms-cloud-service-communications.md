---
title: AEM Forms as a Cloud Service – Kommunikation
description: Automatisches Zusammenführen von Daten mit XDP- und PDF-Vorlagen oder Generieren von Ausgaben in den Formaten PCL, ZPL und PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: 20e54ff697c0dc7ab9faa504d9f9e0e6ee585464
workflow-type: tm+mt
source-wordcount: '1203'
ht-degree: 50%

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

### Multi-Mandant-APIs

* APIs für Dokumentdienstprogramme

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

### Mehrere Mandanten-API authentifizieren

#### Authentifizierungskopfzeilen

Jeder eingehende HTTP-API-Aufruf an die Cloud Manager-API muss die folgenden drei Kopfzeilen enthalten:

* `x-api-key`
* `x-gw-ims-org-id`
* `Authorization`

Die Werte, die im `x-api-key` und `x-gw-ims-org-id` Die Kopfzeilen werden im Bildschirm mit den Details zu Anmeldedaten im [Adobe Developer-Konsole](https://developer.adobe.com/console). Der Wert der `x-api-key` -Kopfzeile ist die Client-ID und der Wert für `x-gw-ims-org-id` -Kopfzeile ist die Organisations-ID.

#### Konfigurieren der Adobe Developer-Konsole zum Generieren eines Zugriffstokens

Um Authentifizierungs-APIs einzurichten, erstellen Sie ein Projekt in der Adobe Developer Console und fügen Sie dem Projekt in der Adobe Developer Console Kommunikations-APIs hinzu. Die Integration erzeugt API-Schlüssel, Client Secret, Payload (JWT):

1. Wenden Sie sich an Ihren Adobe Developer Console-Administrator. Bitten Sie den Administrator, ihn als Entwickler hinzuzufügen.
1. Melden Sie sich bei `https://developer.adobe.com/console/` an. Verwenden Sie Ihr Entwicklerkonto, das Ihr Administrator bereitgestellt hat, um sich bei der Adobe Developer Console anzumelden.
1. Wählen Sie Ihr Unternehmen oben rechts aus. Wenn Sie Ihre Organisation nicht kennen, wenden Sie sich an Ihren Administrator.
1. Tippen Sie auf **[!UICONTROL Neues Projekt erstellen]**. Ein Bildschirm zum Starten Ihres neuen Projekts wird angezeigt. Tippen Sie auf **[!UICONTROL API hinzufügen]**. Ein Bildschirm mit einer Liste aller für Ihr Konto aktivierten APIs wird angezeigt.
1. Auswählen **[!UICONTROL AEM Forms - Kommunikation]** und tippen **[!UICONTROL Nächste]**. Ein Bildschirm zum Konfigurieren der API wird angezeigt.
1. Auswählen **[!UICONTROL OPTION 1 Generieren eines Schlüsselpaars]** und tippen **[!UICONTROL Generieren von keypair]**. Sie erstellt die Konfigurationsdatei und lädt sie herunter. Die heruntergeladene Konfigurationsdatei enthält alle App-Einstellungen sowie die einzige Kopie Ihres privaten Schlüssels. Adobe speichert Ihren privaten Schlüssel nicht, sondern speichern Sie die heruntergeladene Datei sicher. Tippen Sie auf **[!UICONTROL Weiter]**.
1. Auswählen **[!UICONTROL Integrationen - Cloud Service]** und tippen **[!UICONTROL Konfigurierte API speichern]**. Tippen **[!UICONTROL Dienstkonto (JWT)]** um den API-Schlüssel, das Client Secret und andere Informationen anzuzeigen, die für den Zugriff auf die APIs erforderlich sind. Sie legen fest, dass das Token für den Zugriff auf die APIs verwendet werden soll.

#### Programmgesteuertes Generieren und Verwenden eines Zugriffstokens

Um programmgesteuert ein Zugriffstoken zu generieren, generieren Sie ein JSON Web Token (JWT) und tauschen Sie es mit dem Adobe Identity Management Service (IMS) gegen ein Zugriffstoken aus.

Verwenden Sie die folgenden Schlüssel, die als &quot;Schadensmeldungen&quot;bezeichnet werden, um ein JWT-JSON-Objekt zu erstellen:

* `exp`- die angeforderte Gültigkeit des Zugriffstokens, ausgedrückt als Anzahl von Sekunden seit dem 1. Januar 1970 GMT. Für die meisten Anwendungsfälle ist dies ein relativ kleiner Wert. Beispielsweise sollte dieser Wert für fünf Minuten in 5 Minuten 1670923791 betragen.
* `iss` - die Organisations-ID aus dem Adobe Developer Console-Projekt im Format org_ident@AdobeOrg.
* `sub` - die Technische Konto-ID aus der Adobe Developer Console-Integration im folgenden Format: id@techacct.adobe.com
* `aud` - die Client-ID aus der Adobe Developer Console-Integration, der der `https://ims-na1.adobelogin.com/c/`.
* `https://ims-na1-stg1.adobelogin.com/s/ent_aemforms_docprocessing` - auf den Literalwert gesetzt `true`

Dieses JSON-Objekt muss dann mit dem privaten Schlüssel für das Projekt base64-kodiert und signiert werden. Schließlich wird der kodierte Wert im Hauptteil einer POST-Anfrage an `https://ims-na1.adobelogin.com/ims/exchange/jwt` zusammen mit der Client-ID und dem Client-Geheimnis für das Projekt.

##### Beispiel

```JSON
    ========================= REQUEST ==========================
    POST https://ims-na1.adobelogin.com/ims/exchange/jwt
    -------------------------- body ----------------------------
    client_id={myClientId}&client_secret={myClientSecret}&jwt_token={myJSONWebToken}
    ------------------------- headers --------------------------
    Content-Type: application/x-www-form-urlencoded
    Cache-Control: no-cache
```

#### Sprachunterstützung für JWT

Zwar ist es möglich, den gesamten JWT-Generierungs- und Austauschprozess in benutzerdefiniertem Code durchzuführen, doch ist es üblicher, dazu eine Bibliothek auf höherer Ebene zu verwenden. Eine Reihe dieser Bibliotheken sind auf der Seite [Adobe I/O JWT-Dokumentation](https://developer.adobe.com/developer-console/docs/guides/authentication/JWT/).

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
