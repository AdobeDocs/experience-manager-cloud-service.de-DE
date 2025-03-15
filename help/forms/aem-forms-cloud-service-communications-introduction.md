---
title: AEM Forms as a Cloud Service – Kommunikations-APIs
description: Erstellen, Bearbeiten und Schützen von Dokumenten mit AEM Forms Communication APIs in der Cloud
Keywords: document generation, PDF manipulation, document security, batch processing, document conversion, PDF/A compliance
feature: Adaptive Forms, APIs & Integrations, Document Services
role: Admin, Developer, User
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: a9eed5b6219163e721d81c9d77a31604666a2ac5
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 8%

---


# AEM Forms as a Cloud Service – Kommunikations-APIs {#communications-apis-overview}

> **Versionsverfügbarkeit**
>
> * **AEM 6.5**: [Überblick über AEM Document Services](https://experienceleague.adobe.com/docs/experience-manager-65/forms/use-document-services/overview-aem-document-services.html?lang=de)
> * **AEM as a Cloud Service**: Dieser Artikel

## Einführung

Mithilfe von Kommunikations-APIs in AEM Forms as a Cloud Service können Sie markengeprüfte, personalisierte und standardisierte Dokumente für Ihre Geschäftsanforderungen erstellen. Diese leistungsstarken APIs ermöglichen es Ihnen, Dokumente programmgesteuert zu generieren, zu bearbeiten und zu sichern, ob bei Bedarf oder in Batch-Prozessen mit hohem Volumen.


### Die wichtigsten Vorteile

* **Optimierte Dokumenterstellung** - Erstellen personalisierter Dokumente durch Zusammenführen von Vorlagen mit Kundendaten
* **Leistungsstarke Dokumentbearbeitung** - PDF-Dokumente programmgesteuert kombinieren, neu anordnen und validieren
* **Flexible Bereitstellungsoptionen** - Verwenden Sie On-Demand-APIs für Anforderungen mit geringer Latenz oder Batch-APIs für Vorgänge mit hohem Durchsatz.
* **Verbesserte Sicherheit** - Anwenden digitaler Signaturen, Zertifizierung und Verschlüsselung zum Schutz sensibler Dokumente
* **Cloud-native Architektur** - Nutzung skalierbarer, sicherer Cloud-Infrastrukturen ohne Wartungsaufwand

## Schlüsselfunktionen

Kommunikations-APIs bieten einen umfassenden Satz an Dokumentverarbeitungsfunktionen, die in die folgenden Funktionsbereiche unterteilt sind:


| Erstellen von Dokumenten | Bearbeitung von Dokumenten | Dokumentenextraktion | Dokumentenkonvertierung | Document Assurance |
|---------------------|----------------------|---------------------|---------------------|-------------------|
| Erzeugen Sie personalisierte Dokumente durch Zusammenführen von Vorlagen mit Daten in verschiedenen Formaten, einschließlich PDF und Druckformaten. | PDF-Dokumente programmgesteuert kombinieren, neu anordnen und validieren, um neue Dokumentpakete zu erstellen. | Extrahieren Sie Eigenschaften, Metadaten und Inhalte aus PDF-Dokumenten für die weitere Verarbeitung. | Konvertieren von Dokumenten zwischen Formaten, einschließlich PDF/A-Compliance-Validierung für Archivierungsanforderungen. | Anwenden digitaler Signaturen, Zertifizierung und Verschlüsselung zum Sichern und Schützen von Dokumenten. |

## Erstellen von Dokumenten

APIs zur Generierung von Kommunikationsdokumenten kombinieren Vorlagen (XFA oder PDF) mit Kundendaten (XML), um personalisierte Dokumente in PDF und verschiedenen Druckformaten (PS, PCL, DPL, IPL, ZPL) zu erstellen.

### Funktionsweise der Dokumenterstellung

Der typische Workflow umfasst Folgendes:

1. Erstellen einer Vorlage mit [Designer](use-forms-designer.md)
2. Vorbereiten von XML-Daten zum Ausfüllen der Vorlage
3. Verwenden von Kommunikations-APIs zum Zusammenführen der Vorlage mit Daten
4. Generieren von Ausgabedokumenten in Ihrem gewünschten Format

![Workflow zum Erzeugen von Kommunikationsdokumenten](assets/communicaions-workflow.png)

### Erstellen von PDF-Dokumenten

Mit den APIs zur Dokumenterstellung können Sie nicht interaktive PDF-Dokumente erstellen, indem Sie XML-Daten mit Formularvorlagen zusammenführen:

![Erstellen von PDF-Dokumenten](assets/outPutPDF_popup.png)

Sie können die generierten PDF-Dateien über Downloads an Benutzer senden, in einem Repository speichern oder optional in Azure Blob Storage hochladen.

<span class="preview">Das Hochladen generierter PDFs in Azure Blob Storage ist über das [Early-Adopter-Programm](/help/forms/early-access-ea-features.md) verfügbar. aem-forms-ea@adobe.com von Ihrer offiziellen E-Mail kontaktieren, um teilzunehmen.</span>

### Druckformatdokumente erstellen

Generieren von Dokumenten in Druckformaten, einschließlich:
* PostScript (PS)
* Printer Command Language (PCL)
* Zebra Printing Language (ZPL)

Diese Formate eignen sich ideal für den Druck großer Druckvolumen und für spezielle Druckanforderungen.

### Stapelverarbeitung für mehrere Dokumente

Effiziente Verarbeitung großer Dokumentmengen mithilfe von Batch-APIs:

![Batch-Verarbeitungs-Workflow](assets/ou_OutputBatchMany_popup.png)

Die Batch-Verarbeitung ermöglicht Ihnen Folgendes:

* Für jeden Datensatz in einer XML-Datenquelle separate Dokumente generieren
* Dokumente asynchron verarbeiten, um die Leistung zu verbessern
* Konfigurieren verschiedener Konvertierungsparameter für den Batch-Prozess

## Bearbeitung von Dokumenten

Mit APIs zur Dokumentbearbeitung können Sie PDF-Dokumente programmgesteuert kombinieren, neu anordnen und transformieren.

### Dokument-Zusammenstellung

Kombinieren mehrerer PDF- oder XDP-Dokumente in einem einzigen zusammenhängenden Dokument:

![Assemblieren eines einzelnen PDF-Dokuments aus mehreren PDF-Dokumenten](assets/as_document_assembly.png)

Zu den Funktionen für die Dokumentzusammenstellung gehören:
* Erstellen einfacher PDF-Dokumente aus mehreren Quellen
* Erstellen von PDF-Portfolios
* Zusammenstellen verschlüsselter Dokumente
* Bates-Nummerierung für juristische Dokumente hinzufügen
* Reduzieren und Zusammenstellen interaktiver Formulare

### Dokumentzerlegung

Unterteilen Sie große PDF-Dokumente in kleinere, besser verwaltbare Komponenten:

![Aufteilen eines Quelldokuments in mehrere Dokumente basierend auf Lesezeichen](assets/as_intro_pdfsfrombookmarks.png)

Die Dokumentzerlegung ermöglicht Ihnen Folgendes:
* Extrahieren von bestimmten Seiten aus Quelldokumenten
* Dokumente anhand von Lesezeichen aufteilen
* Erstellen logischer Dokumentensätze aus größeren Kompilierungen

>[!NOTE]
>
> AEM Forms enthält viele integrierte Schriftarten, die sich nahtlos in PDF-Dateien integrieren lassen. Eine vollständige Liste der unterstützten Schriftarten finden [hier ](/help/forms/supported-out-of-the-box-fonts.md).

## Dokumentenextraktion

<span class="preview">Die Dokumentenextraktion ist über das [Early-Adopter-Programm](/help/forms/early-access-ea-features.md) verfügbar. aem-forms-ea@adobe.com von Ihrer offiziellen E-Mail kontaktieren, um teilzunehmen.</span>

Mit APIs zur Dokumentextraktion können Sie Informationen aus PDF-Dokumenten abrufen, darunter:

* Dokumenteigenschaften (ein ausfüllbares Formular, Anhänge usw.)
* Verwendungsrechte und Berechtigungen
* Metadateninformationen mithilfe der Adobe Extensible Metadata Platform (XMP)

Diese Funktion ist besonders nützlich für Dokumentenmanagement-Systeme, Archivierungslösungen und die Workflow-Automatisierung.

## Dokumentenkonvertierung

### PDF/A-Konvertierung und -Validierung

Konvertieren von standardmäßigen PDF-Dokumenten in das PDF/A-Format für langfristige Archivierungszwecke:

* Unterstützung für PDF/A-1a-, 1b-, 2a-, 2b-, 3a- und 3b-Compliance-Standards
* Validierung der PDF/A-Konformität
* Erhaltung der Dokumentintegrität mit eingebetteten Schriftarten und unkomprimiertem Inhalt

### Konvertierung von PDF in XDP

<span class="preview">Die Konvertierung von PDF in XDP ist über das [Early-Adopter-Programm“ ](/help/forms/early-access-ea-features.md). aem-forms-ea@adobe.com von Ihrer offiziellen E-Mail kontaktieren, um teilzunehmen.</span>

Konvertieren von PDF-Dokumenten mit XFA-Streams in das XDP-Format zur Bearbeitung und Wiederverwendung von Vorlagen.

## Document Assurance {#doc-assurance}

Document Assurance enthält Signature- und Encryption-APIs, mit denen Ihre Dokumente während ihres gesamten Lebenszyklus geschützt werden.

### Signature-APIs

Schützen von PDF-Dokumenten mit digitalen Signaturen und Zertifizierung:

* Hinzufügen sichtbarer oder unsichtbarer Signaturfelder
* Signaturfelder digital signieren
* Zertifizieren von Dokumenten für Integrität
* Entfernen von Signaturen aus Dokumenten
* Löschen von Signaturfeldern aus Dokumenten

<span class="preview">Das Entfernen von Signaturen und das Löschen von Signaturfeldern sind über das [Early-Adopter-Programm“ ](/help/forms/early-access-ea-features.md). aem-forms-ea@adobe.com von Ihrer offiziellen E-Mail kontaktieren, um teilzunehmen.</span>

### Verschlüsselungs-APIs

Dokumentinhalt mit Verschlüsselung sichern:

* Verschlüsseln von PDF-Dokumenten mit Passwörtern
* Kennwortbasierte Verschlüsselung entfernen
* Bestimmen der auf Dokumente angewendeten Sicherheitstypen
* Abrufen von Sicherheitsinformationen aus geschützten Dokumenten

### Dokumenten-Dienstprogramme {#doc-utility}

Document Utilities bietet zusätzliche Funktionen zum Arbeiten mit PDF-Dokumenten:

#### Verwendungsrechte-APIs (Reader-Erweiterung)

<span class="preview">Verwendungsrechte (Reader-Erweiterung) sind über das [Early-Adopter-Programm](/help/forms/early-access-ea-features.md) verfügbar. aem-forms-ea@adobe.com von Ihrer offiziellen E-Mail kontaktieren, um teilzunehmen.</span>

Erweitern Sie die Funktionalität von Adobe Reader, indem Sie Verwendungsrechte zu PDF-Dokumenten hinzufügen und Funktionen wie die folgenden aktivieren:

* Ausfüllen und Speichern von Formularen
* Hinzufügen von Kommentaren und Anmerkungen
* Digitale Signatur
* Dateianhänge
* Importieren/Exportieren von Formulardaten
* Zugriff auf Web-Services und Datenbanken

Zu den verfügbaren Verwendungsrechten gehören:

* **Formularinteraktion**: Ausfüllen von Formularen, Importieren/Exportieren von Formulardaten, Dynamische Formularfelder/-seiten
* **Anmerkungen**: Kommentare (online und offline), Digitale Signaturen
* **Dokumentenverarbeitung**: Eingebettete Dateien, eigenständiges Senden, Barcode-Dekodierung
* **Online Services**: Online-Forms, Zugriff auf Web-Services

## Typen von Kommunikations-APIs {#types}

Communications bietet zwei Arten von APIs für verschiedene Anwendungsfälle:

### Synchrone APIs

**Am besten geeignet für**: Erstellung einzelner Dokumente bei Bedarf, mit geringer Latenz
**Anwendungsfälle**: Benutzergesteuerte Dokumenterstellung, interaktive Anwendungen
**Dokumentation**: [synchrone API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)

### Batch-APIs (asynchron)

**Am besten geeignet für**: Geplante Erstellung mehrerer Dokumente mit hohem Durchsatz
**Anwendungsfälle**: Monatsabschlüsse, Rechnungen, Benachrichtigungen, terminierte Berichte
**Dokumentation**: [Batch-API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/)

## Erste Schritte mit Kommunikations-APIs

### Onboarding-Prozess

Communications ist als eigenständiges Modul oder Add-on für Benutzende von Forms as a Cloud Service verfügbar:

1. Wenden Sie sich an den Adobe-Vertrieb oder Ihren Adobe-Support-Mitarbeiter, um den Zugriff anzufordern
2. Adobe aktiviert den Zugriff für Ihr Unternehmen und gewährt Administratorrechte
3. Ihr Administrator kann dann Entwicklern in Ihrer Organisation Zugriff gewähren

### Aktivieren der Kommunikation in Ihrer Umgebung

Führen Sie die folgenden Schritte aus, um Communications für Ihre Forms as a Cloud Service-Umgebung zu aktivieren:

1. Melden Sie sich bei Cloud Manager an und öffnen Sie Ihre AEM Forms as a Cloud Service-Instanz
2. Wählen Sie die Option Programm bearbeiten aus und navigieren Sie zur Registerkarte Lösungen und Add-ons .
3. Wählen Sie die Option **[!UICONTROL Forms - Kommunikation]** aus

   ![Kommunikationen](assets/communications.png)

   Wenn Sie **[!UICONTROL Forms - Digitale Registrierung]** bereits aktiviert haben, wählen Sie stattdessen die Option **[!UICONTROL Forms - Kommunikations]** Add-on.

   ![Add-on](assets/add-on.png)

4. Klicken Sie auf **[!UICONTROL Aktualisieren]**
5. Ausführen der Build-Pipeline - Kommunikations-APIs werden nach erfolgreichem Abschluss aktiviert

>[!NOTE]
>
> Um APIs zur Dokumentbearbeitung zu aktivieren, fügen Sie Ihrer [Dispatcher-Konfiguration die folgende Regel hinzu](setup-local-development-environment.md#forms-specific-rules-to-dispatcher):
>
> `# Allow Forms Doc Generation requests`
> `/0062 { /type "allow" /method "POST" /url "/adobe/forms/assembler/*" }`

## API-Referenzdokumentation {#api-reference}

Kommunikations-APIs sind in mehrere funktionale Kategorien unterteilt, von denen jede eine detaillierte Referenzdokumentation aufweist. Diese API-Referenzen bieten umfassende Informationen zu Endpunkten, Parametern, Anfrage-/Antwortformaten und Authentifizierungsanforderungen.

### APIs zur Dokumenterstellung

| API | Beschreibung | Referenz-Link |
|-----|-------------|----------------|
| Dokumenterstellung - synchron | Bei Bedarf Dokumente mit geringer Latenz für interaktive Szenarien generieren | [API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-sync/) |
| Dokumenterstellung - Batch | Asynchrone Verarbeitung großer Dokumentmengen für geplante Vorgänge | [API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/output-batch/) |

### APIs zur Dokumentbearbeitung

| API | Beschreibung | Referenz-Link |
|-----|-------------|----------------|
| Dokumentenbearbeitung - synchron | Kombinieren, Aufteilen und Transformieren von PDF-Dokumenten mithilfe von DDX-Anweisungen | [API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/assembler-sync/) |

### Document Assurance-APIs

| API | Beschreibung | Referenz-Link |
|-----|-------------|----------------|
| DocAssurance - synchron | Anwenden von digitalen Signaturen, Zertifizierung, Verschlüsselung und Readererweiterungen | [API-Referenz](https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/api/docassurance/) |

### Allgemeine API-Parameter

Jede API-Kategorie verfügt über bestimmte Parameter, aber zu den gebräuchlichen Parametern gehören:

#### Parameter für die Dokumenterstellung

| Parameter | Typ | Erforderlich | Beschreibung |
|-----------|------|----------|-------------|
| `template` | Zeichenfolge | Ja | Pfad zur XDP- oder PDF-Vorlagendatei |
| `data` | Zeichenfolge | Nein | Zusammenzuführende XML-Daten |
| `outputOptions` | Objekt | Nein | Konfigurationsoptionen für das Ausgabedokument |

#### Parameter für die Dokumentbearbeitung

| Parameter | Typ | Erforderlich | Beschreibung |
|-----------|------|----------|-------------|
| `ddx` | Zeichenfolge | Ja | DDX-Anweisungen für die Zusammenstellung oder Demontage von Dokumenten |
| `inputDocuments` | Objekt | Ja | Karte der zu verarbeitenden Eingabedokumente |
| `outputOptions` | Objekt | Nein | Konfigurationsoptionen für das Ausgabedokument |

#### Document Assurance-Parameter

| Parameter | Typ | Erforderlich | Beschreibung |
|-----------|------|----------|-------------|
| `inputPDF` | Zeichenfolge | Ja | Zu sicherndes oder zu signierendes PDF-Eingabedokument |
| `certificateAlias` | Zeichenfolge | Bedingt | Alias des Zertifikats für Signaturvorgänge |
| `credentialPassword` | Zeichenfolge | Bedingt | Kennwort für die zum Signieren verwendete Berechtigung |

Ausführliche Informationen zu Parametern, Authentifizierungsanforderungen und Beispielanforderungen/-antworten finden Sie in der spezifischen API-Referenzdokumentation, die in den obigen Tabellen verlinkt ist.

## Zusätzliche Ressourcen {#see-also}

* [Kommunikationsverarbeitung – Synchrone APIs](/help/forms/aem-forms-cloud-service-communications.md)
* [Kommunikationsverarbeitung – Batch-APIs](/help/forms/aem-forms-cloud-service-communications-batch-processing.md)
* [Architektur von AEM Forms as a Cloud Service](/help/forms/aem-forms-cloud-service-architecture.md)
* [API-Referenzdokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)
* [Early-Adopter-Programmfunktionen](/help/forms/early-access-ea-features.md)
