---
title: AEM Forms as a Cloud Service – Kommunikation
description: Automatisches Zusammenführen von Daten mit XDP- und PDF-Vorlagen oder Generieren von Ausgaben in den Formaten PCL, ZPL und PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: c38a34519822449ff2577a9474b1294d5d45d3ae
workflow-type: tm+mt
source-wordcount: '711'
ht-degree: 54%

---


# Verwenden der as a Cloud Service Kommunikations-APIs von AEM Forms - Syncronous Processing {#frequently-asked-questions}

**Die Kommunikationsfunktion befindet sich in der Betaphase.**

Mithilfe der Kommunikationsfunktion können Sie markenorientierte und personalisierte Kommunikation kreieren, zusammenstellen und bereitstellen, wie z. B. Geschäftskorrespondenz, Dokumente, Mitteilungen, Schadensbearbeitungsschreiben, Leistungsbenachrichtigungen, Monatsabrechnungen und Begrüßungs-Kits. Sie können Kommunikations-APIs verwenden, um eine Vorlage (XFA oder PDF) mit Kundendaten zu kombinieren und Dokumente im PDF-, PS-, PCL-, DPL-, IPL- und ZPL-Format zu generieren.

Angenommen, Sie haben eine oder mehrere Vorlagen und für jede Vorlage mehrere Datensätze mit XML-Daten. Sie können Kommunikations-APIs verwenden, um für jeden Eintrag ein Print-Dokument zu generieren. <!-- You can also combine the records into a single document. --> Das Ergebnis ist ein nicht interaktives PDF-Dokument. Bei einem nicht interaktiven PDF-Dokument können Benutzer keine Daten in die Felder eingeben.


Die Kommunikationsfunktion bietet APIs für die On-Demand- und geplante Dokumenterstellung. Sie können synchrone APIs für die On-Demand-Dokumenterstellung und Batch-APIs (asynchrone APIs) für die geplante Dokumenterstellung verwenden:

* Synchrone APIs eignen sich für die Dokumenterstellung auf Anfrage, mit geringer Latenz und mit einzelnen Datensätzen. Diese APIs eignen sich besser für Anwendungen auf Basis einer Benutzeraktion. Zum Beispiel zum Generieren eines Dokuments, nachdem ein Anwender ein Formular ausgefüllt hat.

* Batch-APIs (asynchrone APIs) eignen sich für Anwendungsfälle für die geplante Erstellung mehrerer Dokumente mit hohem Durchsatz. Diese APIs generieren Dokumente in Stapeln. Beispielsweise werden damit monatliche Telefonrechnungen, Kreditkartenauszüge und Leistungsmitteilungen generiert.

## Verwenden von synchronen Vorgängen {#batch-operations}

Ein synkronischer Vorgang ist ein Vorgang, bei dem Dokumente linear generiert werden. Es unterstützt zwei Authentifizierungstypen:

* **Grundlegende Authentifizierung**: Die einfache Authentifizierung ist ein einfaches Authentifizierungsschema, das in das HTTP-Protokoll integriert ist. Der Client sendet HTTP-Anfragen mit dem Autorisierungs-Header, der das Wort &quot;Einfach&quot;gefolgt von einem Leerzeichen und einer base64-kodierten Zeichenfolge username:password enthält. Um beispielsweise als Administrator/Administrator zu autorisieren, sendet der Client Basic [base64-kodierter String-Benutzername]: [base64-kodiertes Zeichenfolgenkennwort].

* **Token-basierte Authentifizierung:** Token-basierte Authentifizierung verwendet ein Zugriffstoken (Trägerauthentifizierungstoken), um Anfragen an AEM as a Cloud Service zu senden. AEM Forms as a Cloud Service stellt APIs zum sicheren Abrufen des Zugriffstokens bereit. So rufen Sie das Token ab und verwenden es, um eine Anfrage zu authentifizieren:

   1. [Abrufen AEM as a Cloud Service Anmeldeinformationen aus der Developer Console](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. [Installieren AEM as a Cloud Service Anmeldeinformationen für Ihre Umgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (Anwendungsserver, Webserver oder andere Nicht-AEM-Server), die zum Senden von Anfragen an den Cloud-Dienst (Aufrufe) konfiguriert sind.
   1. [Erstellen Sie ein JWT-Token und tauschten Sie es mit Adobe IMS-APIs gegen ein Zugriffstoken aus.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. Führen Sie die AEM-API mit dem Zugriffstoken als Trägerauthentifizierungstoken aus.
   1. [Festlegen der entsprechenden Berechtigungen für technische Kontobenutzer in der AEM-Umgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=en#configure-access-in-aem).

   >[!NOTE]
   >
   >Adobe empfiehlt die Verwendung der Token-basierten Authentifizierung in einer Produktionsumgebung.

### Voraussetzungen {#pre-requisites}

Um synkronische APIs zu verwenden, ist Folgendes erforderlich:

* PDF- oder XDP-Vorlagen
* [Daten, die mit Vorlagen zusammengeführt werden sollen](#form-data)
* Benutzer mit Experience Manager-Administratorberechtigungen
* Hochladen von Vorlagen und anderen Assets in Ihre Experience Manager Forms Cloud Service-Instanz

#### Hochladen von Vorlagen und anderen Assets in Ihre Experience Manager-Instanz

Eine Organisation verfügt in der Regel über mehrere Vorlagen. Zum Beispiel eine Vorlage für Kreditkartenauszüge, Leistungsmitteilungen und Anträge. Laden Sie alle diese XDP- und PDF-Vorlagen in Ihre Experience Manager-Instanz hoch. Hochladen von Vorlagen:

1. Öffnen Sie die Experience Manager-Instanz.
1. Navigieren Sie zu „Forms“ > „Forms und Dokumente“.
1. Klicken Sie auf „Erstellen“ > „Ordner“ und erstellen Sie einen Ordner. Öffnen Sie den Ordner.
1. Klicken Sie auf „Erstellen“ > „Datei-Upload“ und laden Sie die Vorlagen hoch.

### Synkronische API zum Generieren von Dokumenten verwenden

Separate APIs sind verfügbar für:

* Erzeugt aus einer Vorlage ein PDF-Dokument und führt Daten zusammen.
* Generieren Sie ein PostScript (PS)-, Printer Command Language (PCL)-, Zebra Printing Language (ZPL)-Dokument aus einer XDP-Datei oder einem PDF-Dokument.

Die [Dokumentation zur API-Referenz](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/Communications-Services) enthält detaillierte Informationen zu allen Parametern, Authentifizierungsmethoden und verschiedenen Services, die von APIs bereitgestellt werden. Die Dokumentation zur API-Referenz ist auch im Format .yaml verfügbar. Sie können die .yaml-Datei herunterladen für [Synkronische APIs](assets/sync.yaml) und laden Sie es in Postman hoch, um die Funktionalität der APIs zu überprüfen.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Nur Mitglieder der Gruppe „Formularbenutzer“ können auf Kommunikations-APIs zugreifen.

