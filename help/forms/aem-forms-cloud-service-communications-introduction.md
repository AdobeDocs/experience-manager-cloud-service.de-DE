---
title: Einführung in die Kommunikationsfunktion von Forms as a Cloud Service
description: Automatisches Zusammenführen von Daten mit XDP- und PDF-Vorlagen oder Generieren von Ausgaben in den Formaten PCL, ZPL und PostScript
exl-id: b6f05b2f-5665-4992-8689-d566351d54f1
source-git-commit: 0673aa4f2f0ad2f0a5205bf929de3f26aea0d879
workflow-type: tm+mt
source-wordcount: '1911'
ht-degree: 98%

---

# as a Cloud Service Kommunikation mit AEM Forms verwenden {#frequently-asked-questions}

**Die Funktion &quot;AEM Forms as a Cloud Service Communications&quot;befindet sich in der Betaphase.**

Die Funktion Communications hilft Ihnen, markenorientierte, personalisierte und standardisierte Dokumente wie Geschäftskorrespondenzen, Kontoauszüge, Mahnschreiben, Leistungsbescheide, monatliche Rechnungen oder Willkommenspakete zu erstellen.


Sie können bei Bedarf ein Dokument generieren oder einen Batch-Vorgang erstellen, um mehrere Dokumente in definierten Intervallen zu generieren. Kommunikations-APIs bieten:

* Optimierte Funktionen zur Erstellung von On-Demand- und Batch-Dokumentationen

* Bereitstellen von HTTP-APIs für eine einfachere Integration in bestehende Systeme

* Sicherer Datenzugriff. Communications-APIs stellen nur eine Verbindung zu kundenspezifischen Daten-Repositorys her und greifen auf die Daten dort zu. Sie erstellen jedoch keine lokalen Kopien der Daten, wodurch Communications äußerst sicher ist.

* separate APIs für Operationen mit geringer Latenz und hohem Durchsatz, wodurch die Dokumentenerstellung zu einer effizienten Aufgabe wird.

![Beispiel eines Kreditkartenauszugs](assets/statement.png)

## Funktionsweise?

Communications verwendet [PDF- und XFA-Vorlagen](#supported-document-types) mit [XML-Daten](#form-data), um ein einzelnes Dokument bei Bedarf oder mehrere Dokumente mithilfe eines Batch-Vorgangs in definierten Intervallen zu generieren.

Eine Communications-API hilft, eine Vorlage (XFA oder PDF) mit Kundendaten ([XML-Daten](#form-data)) zu kombinieren, um Dokumente in PDF- und Druckformaten wie PS, PCL, DPL, IPL und ZPL zu generieren.

Normalerweise erstellen Sie eine Vorlage mit Designer und verwenden Communications-APIs, um Daten mit der Vorlage zusammenzuführen. Ihr Programm kann das Ausgabedokument zur Archivierung an einen Netzwerkdrucker, einen lokalen Drucker oder an ein Speichersystem senden. Typische vorkonfigurierte und benutzerdefinierte Workflows sehen wie folgt aus:

![Kommunikations-Workflow](assets/communicaions-workflow.png)

Je nach Anwendungsfall können Sie diese Dokumente auch über Ihre Website oder einen Speicher-Server zum Download bereitstellen.

## Kommunikations-APIs

Kommunicationen bieten HTTP-APIs für die On-Demand- und Batch-Dokumentgenerierung:

* **Synchrone APIs** eignen sich für die Dokumenterstellung auf Anfrage, mit geringer Latenz und mit einzelnen Datensätzen. Diese APIs eignen sich besser für Anwendungen auf Basis einer Benutzeraktion. Zum Beispiel das Generieren eines Dokuments, nachdem ein Benutzer ein Formular ausgefüllt hat.

* **Batch-APIs (asynchrone APIs)** eignen sich für Anwendungsfälle für die geplante Erstellung mehrerer Dokumente mit hohem Durchsatz. Diese APIs generieren Dokumente in Stapeln. Beispielsweise werden damit monatliche Telefonrechnungen, Kreditkartenauszüge und Leistungsmitteilungen generiert.

## Einstieg 

Communications ist als eigenständiges und als Add-on-Modul für Forms as a Cloud Service-Benutzer verfügbar. Sie können sich an das Adobe-Vertriebs-Team oder Ihren Adobe-Support-Mitarbeiter wenden, um Zugriff anzufordern.

Adobe ermöglicht den Zugriff für Ihre Organisation und stellt der in Ihrer Organisation als Administrator genannten Person die erforderlichen Berechtigungen zur Verfügung. Der Administrator kann den AEM Forms-Entwicklern (Benutzern) Ihrer Organisation Zugriff auf die APIs gewähren.

<!--

Communication help you combine a template and XML data to generate print documents in various formats. The service allows you to generate documents in synchronous and batch modes. The APIs enables you to create applications that let you:

  * Generate documents by populating template files (PDF and XDP) with XML data.
  * Generate output forms in various formats, including non-interactive PDF print streams.

Consider a scenario where you have one or more templates and multiple records of XML data for each template. You can use Communications APIs to generate a print document for each record.  You can also combine the records into a single document.  The result is a non-interactive PDF document. A non-interactive PDF document does not let users enter data into its fields.

 There are two main Communications APIs. The _generatePDFOutput_ generates PDFs, while the _generatePrintedOutput_ generates PostScript, ZPL, and PCL formats. These APIs are available as REST endpoints on your environment, both on author and publish instances. Since the publish instances are configured to scale faster than the author instances, it is recommended use these APIs via publish instances.

The first parameter of both the operations accept the path and name of the template file (for example ExpenseClaim.xdp). You can specify a fully qualified path, reference path of your AEM Repository, or path of a binary file. The second parameter accepts an XML document that is merged with the template while generating the output document.  

The [API reference documentation](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:b1223732-ae0f-4921-bdc0-c31e48b56044) provides detailed information about all the parameters, authentication methods, and various services provided by APIs. The API reference documentation is also available in the .yaml format. You can download the .yaml for [Batch APIs](assets/batch-api.yaml) or [non-Batch API.yaml](assets/non-batch-api.yaml) file and upload it to postman to check functionality of APIs.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

Uploading Communication APIs .yaml file to postman to check functionality of APIs.

## Using the Communications APIs {#workflows}

Typically, you create a template using [Designer](use-forms-designer.md) and use communications APIs ( generatePDFOutput and generatePrintedOutput) to:

* Convert these templates to various formats, including PDF, PostScript, ZPL, and PCL.
* Merge XML form data with a form design to generate a document.
* Generate a document without merging XML form data into the document. However, the primary workflow is merging data into the document.

Then, the output document is stored to a file. You can design custom workflows to send the file to a network printer, a local printer, or to a storage system for archival. A typical out of the box and custom workflows look like the following:

![Communications Workflow](assets/communicaions-workflow.png)

### Create PDF documents {#create-pdf-documents}

You can use the _generatePDFOutput_ API to create PDF document that is based on a form design and XML form data. The output is a non-interactive PDF document. That is, users cannot enter or modify form data. A basic workflow is to merge XML form data with a form design to create a PDF document. The following illustration shows the merging of a form design and XML form data to produce a PDF document.

![Create PDF Documents](assets/outPutPDF_popup.png)

### Create PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL) document {#create-PS-PCL-ZPL-documents}

You can use Communications APIs to create PostScript (PS), Printer Command Language (PCL), and Zebra Printing Language (ZPL) document that are based on a XDP form design or PDF document. The _generatePrintedOutput_ API merges a form design with form data to generate a document. You can save the document to a file and develop a custom process to send it to a printer.

 ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that contains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.



### Processing batch data to create multiple documents {#processing-batch-data-to-create-multiple-documents}

You create separate documents for each record within an XML batch data source. You can can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents.

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents.

### Flatten interactive PDF documents {#flatten-interactive-pdf-documents}

You can use the Communications APIs to transform an interactive PDF document (for example, a form) to a non-interactive PDF document. An interactive PDF document lets users enter or modify data located in the PDF document fields. The process of transforming an interactive PDF document to a non-interactive PDF document is called flattening. When a PDF document is flattened, a user cannot modify the data located in the document’s fields. One reason to flatten a PDF document is to ensure that data cannot be modified.

You can flatten the following types of PDF documents:

* Interactive PDF documents created in Designer (that contain XFA streams).

* Acrobat PDF forms

If you attempt to flatten a non-interactive PDF document, an exception occurs.

### Retain Form State {#retain-form-state}

An interactive PDF document contains various elements that constitute a form. These elements may include fields (to accept or display data), buttons (to trigger events), and scripts (commands to perform a specific action). Clicking a button may trigger an event that changes the state of a field. For example, choosing a gender option may change the color of a field or the appearance of the form. This is an example of a manual event causing the form state to change.

When such an interactive PDF document is flattened using the Communications APIs, the state of the form is not retained. To ensure that the state of the form is retained even after the form is flattened, set the Boolean value _retainFormState_ to True to save and retain the state of the form.  -->

## Zu beachten {#considerations-for-communications-apis}

Bevor Sie mit der Generierung von Dokumenten mit Communications-APIs beginnen, gehen Sie die folgenden Überlegungen durch:

### Formulardaten {#form-data}

Communications-APIs akzeptieren einen Formularentwurf, der normalerweise in Designer und XML-Formulardaten als Eingabe erstellt wird. Zum Ausfüllen eines Dokuments mit Daten muss in den XML-Formulardaten für jedes Formularfeld, das ausgefüllt werden soll, ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Es ist nicht erforderlich, die Reihenfolge zu berücksichtigen, in der die XML-Elemente angezeigt werden. Wichtig ist, dass die XML-Elemente mit entsprechenden Werten angegeben werden.

Beachten Sie das folgende Beispielformular für einen Kreditantrag:

![Kreditantragsformular](assets/loanFormData.png)

Um Daten mit diesem Formular-Design zusammenzuführen, erstellen Sie eine XML-Datenquelle, die dem Formular entspricht. Die folgende XML-Datei stellt eine XML-Datenquelle dar, die dem Beispielformular für einen Hypothekenantrag entspricht.

```XML
<?xml version="1.0" encoding="UTF-8" ?>
* <xfa:datasets xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/">
* <xfa:data>
* <data>
    * <Layer>
        <closeDate>1/26/2007</closeDate>
        <lastName>Johnson</lastName>
        <firstName>Jerry</firstName>
        <mailingAddress>JJohnson@NoMailServer.com</mailingAddress>
        <city>New York</city>
        <zipCode>00501</zipCode>
        <state>NY</state>
        <dateBirth>26/08/1973</dateBirth>
        <middleInitials>D</middleInitials>
        <socialSecurityNumber>(555) 555-5555</socialSecurityNumber>
        <phoneNumber>5555550000</phoneNumber>
    </Layer>
    * <Mortgage>
        <mortgageAmount>295000.00</mortgageAmount>
        <monthlyMortgagePayment>1724.54</monthlyMortgagePayment>
        <purchasePrice>300000</purchasePrice>
        <downPayment>5000</downPayment>
        <term>25</term>
        <interestRate>5.00</interestRate>
    </Mortgage>
</data>
</xfa:data>
</xfa:datasets>
```

### Unterstützte Dokumenttypen {#supported-document-types}

Für den vollständigen Zugriff auf die Rendering-Funktionen der Kommunikations-APIs wird empfohlen, eine XDP-Datei als Eingabe zu verwenden. Manchmal kann eine PDF-Datei verwendet werden. Die Verwendung einer PDF-Datei als Eingabe hat jedoch die folgenden Einschränkungen:

Ein PDF-Dokument, das keinen XFA-Stream enthält, kann nicht als PostScript, PCL oder ZPL gerendert werden. Kommunikations-APIs können PDF-Dokumente mit XFA-Streams (d. h. in Designer erstellte Formulare) in Laser- und Label-Formate wiedergeben. Wenn das PDF-Dokument signiert oder zertifiziert ist oder Verwendungsrechte enthält (die mithilfe des AEM Forms Reader Extensions-Service angewendet werden), kann es nicht in diesen Druckformaten gerendert werden.

&lt;!-* * Laufzeitoptionen wie PDF-Version und mit Tags versehene PDF werden für Acrobat-Formulare nicht unterstützt. Sie gelten für PDF-Formulare, die XFA-Streams enthalten. Diese Formulare können jedoch nicht signiert oder zertifiziert werden.

### E-Mail-Support {#email-support}

Für die E-Mail-Funktionalität können Sie in Experience Manager Workflows einen Prozess erstellen, der den E-Mail-Schritt verwendet. Ein Workflow stellt einen Geschäftsprozess dar, den Sie automatisieren. -->

### Druckbereiche {#printable-areas}

Der standardmäßige, nicht druckbare Rand von 0,25 Zoll ist für Etikettendrucker nicht exakt und variiert von Drucker zu Drucker und von Etikettengröße zu Etikettengröße. Es wird empfohlen, den 0,25-Zoll-Rand beizubehalten oder zu reduzieren. Es wird in jedem Fall empfohlen, den nicht druckbaren Rand nicht zu vergrößern. Andernfalls werden Informationen im druckbaren Bereich nicht ordnungsgemäß gedruckt.

Stellen Sie immer sicher, dass Sie die richtige XDC-Datei für den Drucker verwenden. Vermeiden Sie beispielsweise die Auswahl einer XDC-Datei für einen 300-dpi-Drucker und das Senden des Dokuments an einen 200-dpi-Drucker.

### Skripte {#scripts}

Ein Formular-Design, das mit den Kommunikations-APIs verwendet wird, kann Skripte enthalten, die auf dem Server ausgeführt werden. Stellen Sie sicher, dass ein Formular-Design keine Skripte enthält, die auf dem Client ausgeführt werden. Weitere Informationen zum Erstellen von Formular-Design-Skripten finden Sie in der Hilfe zu Designer.

&lt;!-* #### Arbeiten mit Schriftarten
Dokument-Überlegungen zum Arbeiten mit Schriftarten>> -->

### Schriftzuordnung {#font-mapping}

Um ein Formular zu entwerfen, das druckerresidente Schriftarten verwendet, wählen Sie in Designer den Namen einer Schriftart, die mit den auf dem Drucker verfügbaren Schriftarten übereinstimmt. Eine Liste der für PCL oder PostScript unterstützten Schriftarten befindet sich in den entsprechenden Geräteprofilen (XDC-Dateien). Alternativ kann eine Schriftzuordnung erstellt werden, um nicht druckerresidente Schriftarten druckerresidenten Schriftarten mit einem anderen Schriftartennamen zuzuordnen. In einem PostScript-Szenario können beispielsweise Verweise auf die Schriftart Arial® der druckerresidenten Helvetica®-Schriftart zugeordnet werden.

Wenn eine Schriftart auf einem Client-Computer installiert ist, ist sie in der Dropdown-Liste in Designer verfügbar. Wenn die Schriftart nicht installiert ist, müssen Sie den Schriftnamen manuell angeben. Die Option „Nicht verfügbare Schriften dauerhaft ersetzen“ in Designer kann deaktiviert sein. Andernfalls wird beim Speichern der XDP-Datei in Designer der Name der Ersatzschriftart in die XDP-Datei geschrieben. Dies bedeutet, dass die druckerresidente Schriftart nicht verwendet wird.

Es gibt zwei Arten von OpenType®-Schriftarten. Ein Typ ist eine TrueType OpenType®-Schriftart, die von PCL unterstützt wird. Der andere ist CFF OpenType®. Die PDF- und PostScript-Ausgabe unterstützt eingebettete Type-1-, TrueType- und OpenType®-Schriftarten. Die PCL-Ausgabe unterstützt eingebettete TrueType-Schriftarten.

Type-1- und OpenType®-Schriftarten sind nicht in die PCL-Ausgabe eingebettet. Inhalte, die mit Type-1- und OpenType®-Schriftarten formatiert sind, werden gerastert und als ein Bitmap-Bild generiert, das groß und langsamer zu generieren sein kann.

Heruntergeladene oder eingebettete Schriftarten werden beim Generieren der PostScript-, PCL- oder PDF-Ausgabe automatisch ersetzt. Dies bedeutet, dass nur die Teilmenge der Schriftzeichen, die zum ordnungsgemäßen Rendern des generierten Dokuments erforderlich sind, in der generierten Ausgabe enthalten ist.

### Arbeiten mit Geräteprofildateien (XDC-Datei) {#working-with-xdc-files}

Ein Geräteprofil (XDC-Datei) ist eine Druckerbeschreibungsdatei im XML-Format. Diese Datei ermöglicht es den Kommunikations-APIs, Dokumente als Laser- oder Etikettendruckerformate auszugeben. Kommunikations-APIs verwenden die XDC-Dateien, einschließlich der folgenden:

* hppcl5c.xdc

* hppcl5e.xdc

* ps_plain_level3.xdc

* ps_plain.xdc

* zpl300.xdc

* zpl600.xdc

* zpl300.xdc

* ipl300.xdc

* ipl400.xdc

* tpcl600.xdc

* dpl300.xdc

* dpl406.xdc

* dpl600.xdc

Sie können die bereitgestellten XDC-Dateien verwenden, um Druckdokumente zu erstellen oder diese nach Ihren Anforderungen zu ändern.
&lt;!-* Es ist nicht erforderlich, diese Dateien zu ändern, um Dokumente zu erstellen. Sie können sie jedoch an Ihre Geschäftsanforderungen anpassen. —>

Diese Dateien sind Beispiel-XDC-Dateien, die die Funktionsmerkmale bestimmter Drucker, z. B. residente Schriftarten, Papierfächer und Hefter, unterstützen. Dieser Beispieldateien sollen Ihnen verständlich machen, wie Sie Ihre eigenen Drucker mithilfe von Geräteprofilen einrichten können. Die Beispiele sind auch ein Ausgangspunkt für ähnliche Drucker in derselben Produktlinie.

### Arbeiten mit der XCI-Konfigurationsdatei {#working-with-xci-files}

Kommunikations-APIs verwenden eine XCI-Konfigurationsdatei, um Aufgaben auszuführen, z. B. um zu steuern, ob es sich bei der Ausgabe um einen einzelnen Bereich handelt oder ob sie paginiert wird. Obwohl diese Datei Einstellungen enthält, die festgelegt werden können, ist es nicht üblich, diesen Wert zu ändern. &lt;!-* Die Datei default.xci befindet sich im Ordner svcdata\XMLFormService. —>

Sie können eine modifizierte XCI-Datei übergeben, während Sie eine Kommunikations-API verwenden. Erstellen Sie dabei eine Kopie der Standarddatei, ändern Sie nur die Werte, die geändert werden müssen, um Ihre Geschäftsanforderungen zu erfüllen, und verwenden Sie die geänderte XCI-Datei.

Kommunikations-APIs beginnen mit der standardmäßigen XCI-Datei (oder der geänderten Datei). Anschließend werden Werte angewendet, die mithilfe der Kommunikations-APIs angegeben werden. Diese Werte überschreiben die XCI-Einstellungen.

Die folgende Tabelle gibt die XCI-Optionen an.

| XCI-Option | Beschreibung |
| ------------------------------------| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| config/present/pdf/creator | Identifiziert den Ersteller des Dokuments mithilfe des Eintrags „Ersteller“ im Wörterbuch zu Dokumentinformationen. Weitere Informationen zu diesem Wörterbuch finden Sie im Handbuch „PDF-Referenzen“. |
| config/present/pdf/producer | Identifiziert den Produzenten des Dokuments mithilfe des Eintrags „Produzent“ im Wörterbuch zu Dokumentinformationen. Weitere Informationen zu diesem Wörterbuch finden Sie im Handbuch „PDF-Referenzen“. |
| config/present/layout | Steuert, ob es sich bei der Ausgabe um einen einzelnen Bereich handelt oder ob sie paginiert wird. |
| config/present/pdf/compression/level | Gibt den Komprimierungsgrad an, der beim Generieren eines PDF-Dokuments verwendet werden soll. |
| config/present/pdf/scriptModel | Steuert, ob XFA-spezifische Informationen im PDF-Ausgabedokument enthalten sind. |
| config/present/common/data/adjustData | Steuert, ob die XFA-Anwendung die Daten nach dem Zusammenführen anpasst. |
| config/present/pdf/renderPolicy | Steuert, ob die Erstellung des Seiteninhalts auf dem Server erfolgt oder zum Client ausgelagert wird. |
| config/present/common/locale | Gibt das im Ausgabedokument verwendete Standardgebietsschema an. |
| config/present/destination | Gibt das Ausgabeformat an, wenn es in einem vorhandenen Element enthalten ist. Gibt die Aktion an, die beim Öffnen des Dokuments in einem interaktiven Client ausgeführt werden soll, wenn sie in einem openAction-Element enthalten ist. |
| config/present/output/type | Gibt entweder die Art der Komprimierung an, die auf eine Datei angewendet werden soll, oder den Typ der zu erzeugenden Ausgabe. |
| config/present/common/temp/uri | Gibt den Formular-URI an. |
| config/present/common/template/base | Liefert einen Basisspeicherort für URIs im Formular-Design. Wenn dieses Element fehlt oder leer ist, wird der Speicherort des Formular-Designs als Basis verwendet. |
| config/present/common/log/to | Steuert den Speicherort, an den Protokolldaten oder Ausgabedaten geschrieben werden. |
| config/present/output/to | Steuert den Speicherort, an den Protokolldaten oder Ausgabedaten geschrieben werden. |
| config/present/script/currentPage | Gibt die Anfangsseite an, auf der das Dokument geöffnet wird. |
| config/present/script/exclude | Informiert AEM Forms-Server-/Kommunikations-APIs, welche Ereignisse ignoriert werden sollen. |
| config/present/pdf/linearized | Steuert, ob das ausgegebene PDF-Dokument linearisiert ist. |
| config/present/script/runScripts | Steuert, welcher Satz von Skripten von AEM Forms ausgeführt wird. |
| config/present/pdf/tagged | Steuert die Einbeziehung von Tags in das PDF-Ausgabedokument. Tags sind im Kontext von PDF zusätzliche Informationen, die in einem Dokument enthalten sind, um die logische Struktur des Dokuments anzuzeigen. Tags unterstützen Barrierefreiheitshilfen und die Neuformatierung. Beispielsweise kann eine Seitenzahl als Artefakt getaggt werden, sodass eine Bildschirmlesehilfe sie nicht in der Mitte des Textes anzeigt. Obwohl Tags ein Dokument nützlicher machen, erhöhen sie auch die Größe des Dokuments und die Verarbeitungszeit bei der Erstellung. |
| config/present/pdf/version | Gibt die Version des zu erzeugenden PDF-Dokuments an. |
