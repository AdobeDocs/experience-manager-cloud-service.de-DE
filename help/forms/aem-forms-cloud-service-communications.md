---
title: AEM Forms as a Cloud Service – Kommunikation
description: Automatisches Zusammenführen von Daten mit XDP- und PDF-Vorlagen oder Generieren von Ausgaben in den Formaten PCL, ZPL und PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: fdbb927dbd7f6d640100d444431f931d95414ebc
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 39%

---


# Synchrone Verarbeitung verwenden {#sync-processing-introduction}

Mithilfe der Kommunikationsfunktionen können Sie markengenehmigte, personalisierte und standardisierte Dokumente erstellen, z. B. Geschäftskorrespondenzen, Anweisungen, Anforderungsverarbeitungsbriefe, Leistungsbenachrichtigungen, monatliche Rechnungen oder Willkommenskits.

Die Funktion stellt APIs zum Generieren und Bearbeiten der Dokumente bereit. Sie können ein Dokument bei Bedarf generieren oder bearbeiten oder einen Batch-Auftrag erstellen, um in definierten Intervallen mehrere Dokumente zu generieren.

Die Kommunikationsfunktion bietet APIs für die On-Demand- und geplante Dokumenterstellung. Sie können synchrone APIs für die On-Demand-Dokumenterstellung und Batch-APIs (asynchrone APIs) für die geplante Dokumenterstellung verwenden:

* Synchrone APIs eignen sich für die Dokumenterstellung auf Anfrage, mit geringer Latenz und mit einzelnen Datensätzen. Diese APIs eignen sich besser für Anwendungen auf Basis einer Benutzeraktion. Zum Beispiel zum Generieren eines Dokuments, nachdem ein Anwender ein Formular ausgefüllt hat.

* Batch-APIs (asynchrone APIs) eignen sich für Anwendungsfälle für die geplante Erstellung mehrerer Dokumente mit hohem Durchsatz. Diese APIs generieren Dokumente in Stapeln. Beispielsweise werden damit monatliche Telefonrechnungen, Kreditkartenauszüge und Leistungsmitteilungen generiert.

## Verwenden von synchronen Vorgängen {#batch-operations}

Ein synchroner Vorgang ist ein Vorgang, bei dem Dokumente linear erzeugt oder bearbeitet werden. Es unterstützt zwei Authentifizierungstypen:

* **Grundlegende Authentifizierung**: Die einfache Authentifizierung ist ein einfaches Authentifizierungsschema, das in das HTTP-Protokoll integriert ist. Der Client sendet HTTP-Anfragen mit dem Autorisierungs-Header, der das Wort &quot;Einfach&quot;gefolgt von einem Leerzeichen und einer base64-kodierten Zeichenfolge username:password enthält. Um beispielsweise als Administrator/Administrator zu autorisieren, sendet der Client Basic [base64-kodierter String-Benutzername]: [base64-kodiertes Zeichenfolgenkennwort].

* **Token-basierte Authentifizierung:** Token-basierte Authentifizierung verwendet ein Zugriffstoken (Trägerauthentifizierungstoken), um Anforderungen an Experience Manager as a Cloud Service zu machen. AEM Forms as a Cloud Service stellt APIs zum sicheren Abrufen des Zugriffstokens bereit. So rufen Sie das Token ab und verwenden es, um eine Anfrage zu authentifizieren:

   1. [as a Cloud Service Anmeldeinformationen von Experience Manager aus der Developer Console abrufen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. [as a Cloud Service Anmeldeinformationen von Experience Manager auf Ihrer Umgebung installieren](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html). (Anwendungsserver, Webserver oder andere Nicht-AEM-Server), die zum Senden von Anfragen an den Cloud-Dienst (Aufrufe) konfiguriert sind.
   1. [Erstellen Sie ein JWT-Token und tauschten Sie es mit Adobe IMS-APIs gegen ein Zugriffstoken aus.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html).
   1. Führen Sie die Experience Manager-API mit dem Zugriffstoken als Trägerauthentifizierungstoken aus.
   1. [Legen Sie die entsprechenden Berechtigungen für den Benutzer des technischen Kontos in der Experience Manager-Umgebung fest.](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/authentication/service-credentials.html?lang=en#configure-access-in-aem).

   >[!NOTE]
   >
   >Adobe empfiehlt die Verwendung der Token-basierten Authentifizierung in einer Produktionsumgebung.

### (Nur Document Generation APIs) Voraussetzungen {#pre-requisites}

Um synchrone APIs für die Dokumenterstellung zu verwenden, ist Folgendes erforderlich:

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

### Verwenden der synchronen API zum Generieren von Dokumenten

Separate APIs sind verfügbar für:

* Erzeugt aus einer Vorlage ein PDF-Dokument und führt Daten zusammen.
* Generieren Sie ein PostScript (PS)-, Printer Command Language (PCL)-, Zebra Printing Language (ZPL)-Dokument aus einer XDP-Datei oder einem PDF-Dokument.

Die [Dokumentation zur API-Referenz](https://www.adobe.io/experience-manager-forms-cloud-service-developer-reference/api/sync/#tag/Communications-Services) enthält detaillierte Informationen zu allen Parametern, Authentifizierungsmethoden und verschiedenen Services, die von APIs bereitgestellt werden. Die Dokumentation zur API-Referenz ist auch im Format .yaml verfügbar. Sie können die .yaml-Datei herunterladen für [synchrone APIs](assets/sync.yaml) und laden Sie es in Postman hoch, um die Funktionalität der APIs zu überprüfen.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

>[!NOTE]
>
>Nur Mitglieder der Gruppe „Formularbenutzer“ können auf Kommunikations-APIs zugreifen.
