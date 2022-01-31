---
title: AEM Forms as a Cloud Service – Kommunikation
description: Automatisches Zusammenführen von Daten mit XDP- und PDF-Vorlagen oder Generieren von Ausgaben in den Formaten PCL, ZPL und PostScript
exl-id: 9fa9959e-b4f2-43ac-9015-07f57485699f
source-git-commit: ed46b0be25dabcea69be29e54000a4eab55e2836
workflow-type: tm+mt
source-wordcount: '2250'
ht-degree: 99%

---


# Verwenden von AEM Forms as a Cloud Service Communications-APIs {#frequently-asked-questions}

**Die Kommunikationsfunktion befindet sich in der Betaphase.**

Mithilfe von Kommunikations-APIs können Sie XDP-Vorlagen, XDP-basierte PDF-Dokumente und Acrobat Forms (AcroForm) mit XML-Daten kombinieren, um Print-Dokumente in verschiedenen Formaten zu generieren und Programme zu erstellen, die Ihnen Folgendes ermöglichen:

- Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten.

- Generieren von Formularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Printstreams.

- Generieren von druckbaren PDFs aus XFA-Formular-PDFs.

- Generieren von PDF-, PostScript-, PCL- und ZPL-Dokumenten in großen Mengen durch Zusammenführen mehrerer Datensätze mit den Quellvorlagen.

Angenommen, Sie haben eine oder mehrere Vorlagen und für jede Vorlage mehrere Datensätze mit XML-Daten. Sie können Kommunikations-APIs verwenden, um für jeden Eintrag ein Print-Dokument zu generieren. <!-- You can also combine the records into a single document. --> Das Ergebnis ist ein nicht interaktives PDF-Dokument. Bei einem nicht interaktiven PDF-Dokument können Benutzer keine Daten in die Felder eingeben.

Die [API-Referenzdokumentation](https://documentcloud.adobe.com/link/track?uri=urn:aaid:scds:US:b1223732-ae0f-4921-bdc0-c31e48b56044) liefert detaillierte Informationen zu allen APIs, Parametern, Authentifizierungsmethoden und verschiedenen Services, die von APIs bereitgestellt werden. Die Dokumentation zur API-Referenz ist auch im Format .yaml verfügbar. Sie können die .yaml-Datei für [Batch-APIs](assets/batch-api.yaml) oder die [Nicht-Batch-API.yaml-Datei](assets/non-batch-api.yaml) herunterladen und sie in Postman hochladen, um die Funktionalität der APIs zu überprüfen.

>[!VIDEO](https://video.tv.adobe.com/v/335771)

Hochladen der .yaml-Datei der Kommunikations-APIs in Postman, um die Funktionalität der APIs zu prüfen.

>[!NOTE]
>
>Nur Mitglieder der Gruppe „Formularbenutzer“ können auf Kommunikations-APIs zugreifen.

## Aktivieren der Kommunikation

So aktivieren Sie Communications für Ihre Forms as a Cloud Service-Umgebung:

1. Melden Sie sich bei Cloud Manager an und öffnen Sie eine AEM Forms as a Cloud Service-Instanz.

1. Wählen Sie die Option „Programm bearbeiten“, gehen Sie zur Registerkarte „Lösungen und Add-ons“ und wählen Sie **[!UICONTROL Forms - Communications]**.

   <!-- ![Communications](assets\communications.png)

    If you have already enabled the **[!UICONTROL Forms - Digital Enrollment]** option, then select the **[!UICONTROL Forms - Communications Add-On]** option.  

    <!-- ![Addon](assets\add-on.png) -->

1. Klicken Sie auf **[!UICONTROL Aktualisieren]**.

1. Führen Sie die Build-Pipeline aus.

Nachdem die Build-Pipeline erfolgreich ausgeführt wurde, werden die Communications-APIs für Ihre Umgebung aktiviert.

## Verwenden der Kommunikations-APIs {#workflows}

In der Regel erstellen Sie eine Vorlage mit [Designer](use-forms-designer.md) und verwenden Kommunikations-APIs zu folgenden Zwecken:

- Konvertieren dieser Vorlagen in verschiedene Formate, darunter PDF, PostScript, ZPL und PCL.
- Zusammenführen von XML-Formulardaten mit einem Formular-Design, um ein Dokument zu generieren.
- Generieren eines Dokuments, ohne die XML-Formulardaten im Dokument zusammenzuführen. Der primäre Workflow besteht jedoch darin, Daten in dem Dokument zusammenzuführen.

Anschließend wird das Ausgabedokument in einer Datei gespeichert. Sie können benutzerdefinierte Workflows entwerfen, um die Datei an einen Netzwerkdrucker, einen lokalen Drucker oder zur Archivierung an ein Speichersystem zu senden. Typische vorkonfigurierte und benutzerdefinierte Workflows sehen wie folgt aus:

![Kommunikations-Workflow](assets/communicaions-workflow.png)

### Erstellen von PDF-Dokumenten {#create-pdf-documents}

Sie können die _generatePDFOutput_-API verwenden, um ein PDF-Dokument zu erstellen, das auf einem Formular-Design und XML-Formulardaten basiert. Die Ausgabe ist ein nicht interaktives PDF-Dokument. Das heißt, Benutzer können keine Formulardaten eingeben oder ändern. Ein einfacher Workflow besteht darin, XML-Formulardaten mit einem Formular-Design zusammenzuführen, um ein PDF-Dokument zu erstellen. Die folgende Abbildung zeigt die Zusammenführung von Formular-Designs und XML-Formulardaten zur Erstellung eines PDF-Dokuments.

![Erstellen von PDF-Dokumenten](assets/outPutPDF_popup.png)

### Erstellen des Dokuments im Format PostScript (PS), Printer Command Language (PCL), Zebra Printing Language (ZPL) {#create-PS-PCL-ZPL-documents}

Sie können Kommunikations-APIs verwenden, um PostScript (PS)-, Printer Command Language (PCL)- und Zebra Printing Language (ZPL)-Dokumente zu erstellen, die auf einem XDP-Formular-Design oder PDF-Dokument basieren. Die _generatePrintedOutput_-API führt ein Formular-Design mit Formulardaten zusammen, um ein Dokument zu generieren. Sie können das Dokument in einer Datei speichern und einen benutzerdefinierten Prozess entwickeln, um es an einen Drucker zu senden.

<!-- ### Processing batch data to create multiple documents

Communications APIs can create separate documents for each record within an XML batch data source. The APIs can also create a single document that contains all records (this functionality is the default). Assume that an XML data source contains ten records and you instruct the APIs to create a separate document for each record (for example, PDF documents). As a result, the APIs generate ten PDF documents.

The following illustration also shows Communications APIs processing an XML data file that contains multiple records. However, assume that you instruct the APIs to create a single PDF document that contains all data records. In this situation, the APIs generate one document that contains all of the records.

The following illustration shows Communications APIs processing an XML data file that contains multiple records. Assume that you instruct the Communications APIs to create a separate PDF document for each data record. In this situation, the APIs generates a separate PDF document for each data record.

 -->

### Verarbeitung von Batch-Daten zum Erstellen mehrerer Dokumente {#processing-batch-data-to-create-multiple-documents}

Für jeden Datensatz innerhalb einer XML-Batch-Datenquelle können Sie separate Dokumente erstellen. Sie können Dokumente im Bulk-Modus und im asynchronen Modus erstellen. Sie können verschiedene Parameter für die Konvertierung konfigurieren und dann den Batch-Prozess starten. <!-- You can can also create a single document that contains all records (this functionality is the default).  Assume that an XML data source contains ten records and you have a requirement to create a separate document for each record (for example, PDF documents). You can use the Communication APIs to generate ten PDF documents. -->

<!-- The following illustration shows the Communication APIs processing an XML data file that contains multiple records. However, assume that you instruct the Communication APIs to create a single PDF document that contains all data records. In this situation, the Communication APIs generate one document that contains all of the records.

![Create PDF Documents](assets/ou_OutputBatchSingle_popup.png)

The following illustration shows the Communication APIs processing an XML data file that contains multiple records. Assume that you instruct the Communication APIs to create a separate PDF document for each data record. In this situation, the Communication APIs generates a separate PDF document for each data record.

![Create PDF Documents](assets/ou_OutputBatchMany_popup.png)

For detailed information on using Batch APIs, see Communication APIs: Processing batch data to create multiple documents. -->

### Reduzieren interaktiver PDF-Dokumente {#flatten-interactive-pdf-documents}

Mit den Kommunikations-APIs können Sie interaktive PDF-Dokumente (z. B. Formulare) in nicht interaktive PDF-Dokumente umwandeln. Interaktive PDF-Dokumente ermöglichen dem Benutzer, Daten in die PDF-Dokumentfelder einzugeben bzw. darin zu ändern. Die Umwandlung eines interaktiven PDF-Dokuments in ein nicht interaktives PDF-Dokument bezeichnet man als Reduzieren. Wenn ein PDF-Dokument reduziert wird, kann ein Benutzer die in den Feldern des Dokuments enthaltenen Daten nicht ändern. Dies kann ein Grund dafür sein, PDF-Dokumente zu reduzieren.

Sie können die folgenden Arten von PDF-Dokumenten reduzieren:

- In Designer erstellte interaktive PDF-Dokumente (die XFA-Streams enthalten).

- Acrobat-PDF-Formulare

Wenn Sie versuchen, ein nicht interaktives PDF-Dokument zu reduzieren, tritt ein Ausnahmefehler auf.

### Beibehalten des Formularstatus {#retain-form-state}

Ein interaktives PDF-Dokument enthält verschiedene Elemente, aus denen ein Formular besteht. Diese Elemente können Felder (zum Eingeben oder Anzeigen von Daten), Schaltflächen (um Ereignisse auszulösne) und Skripte (Befehle zum Ausführen einer bestimmten Aktion) umfassen. Durch Klicken auf eine Schaltfläche wird möglicherweise ein Ereignis ausgelöst, das den Status eines Felds ändert. Wenn Sie beispielsweise eine Option für das Geschlecht wählen, kann sich die Farbe eines Felds oder das Erscheinungsbild des Formulars ändern. Dies ist ein Beispiel für ein manuelles Ereignis, das dazu führt, dass sich der Formularstatus ändert.

Wenn ein solches interaktives PDF-Dokument mithilfe der Kommunikations-APIs reduziert wird, wird der Status des Formulars nicht beibehalten. Um sicherzustellen, dass der Status des Formulars auch nach dem Reduzieren des Formulars beibehalten wird, setzen Sie den booleschen Wert _retainFormState_ auf „true“, um den Status des Formulars zu speichern und beizubehalten.

### Überlegungen zu Kommunikations-APIs {#considerations-for-communications-apis}

#### Formulardaten {#form-data}

Kommunikations-APIs akzeptieren sowohl ein Formular-Design, das normalerweise in Designer erstellt wird, als auch XML-Formulardaten als Eingabe. Zum Ausfüllen eines Dokuments mit Daten muss in den XML-Formulardaten für jedes Formularfeld, das ausgefüllt werden soll, ein XML-Element vorhanden sein. Der Name des XML-Elements muss mit dem Feldnamen übereinstimmen. Ein XML-Element wird ignoriert, wenn es keinem Formularfeld entspricht oder wenn der XML-Elementname nicht mit dem Feldnamen übereinstimmt. Es ist nicht erforderlich, die Reihenfolge zu berücksichtigen, in der die XML-Elemente angezeigt werden. Wichtig ist, dass die XML-Elemente mit entsprechenden Werten angegeben werden.

Beachten Sie das folgende Beispielformular für einen Kreditantrag:

![Kreditantragsformular](assets/loanFormData.png)

Um Daten mit diesem Formular-Design zusammenzuführen, erstellen Sie eine XML-Datenquelle, die dem Formular entspricht. Die folgende XML-Datei stellt eine XML-Datenquelle dar, die dem Beispielformular für einen Hypothekenantrag entspricht.

```XML
<?xml version="1.0" encoding="UTF-8" ?>
- <xfa:datasets xmlns:xfa="http://www.xfa.org/schema/xfa-data/1.0/">
- <xfa:data>
- <data>
    - <Layer>
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
    - <Mortgage>
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

#### Unterstützte Dokumenttypen {#supported-document-types}

Für den vollständigen Zugriff auf die Rendering-Funktionen der Kommunikations-APIs wird empfohlen, eine XDP-Datei als Eingabe zu verwenden. In einigen Fällen kann eine PDF-Datei verwendet werden. Die Verwendung einer PDF-Datei als Eingabe hat jedoch die folgenden Einschränkungen:

- Ein PDF-Dokument, das keinen XFA-Stream enthält, kann nicht als PostScript, PCL oder ZPL gerendert werden. Kommunikations-APIs können PDF-Dokumente mit XFA-Streams (d. h. in Designer erstellte Formulare) in Laser- und Label-Formate wiedergeben. Wenn das PDF-Dokument signiert oder zertifiziert ist oder Verwendungsrechte enthält (die mithilfe des AEM Forms Reader Extensions-Service angewendet werden), kann es nicht in diesen Druckformaten gerendert werden.

<!-- * Run-time options such as PDF version and tagged PDF are not supported for Acrobat forms. They are valid for PDF forms that contain XFA streams; however, these forms cannot be signed or certified. 

#### Email support {#email-support}

For email functionality, you can create a process in AEM Workflows that uses the Email Step. A workflow represents a business process that you are automating. -->

#### Druckbereiche {#printable-areas}

Der standardmäßige, nicht druckbare Rand von 0,25 Zoll ist für Etikettendrucker nicht exakt und variiert von Drucker zu Drucker und von Etikettengröße zu Etikettengröße. Es wird empfohlen, den 0,25-Zoll-Rand beizubehalten oder zu reduzieren. Es wird in jedem Fall empfohlen, den nicht druckbaren Rand nicht zu vergrößern. Andernfalls werden Informationen im druckbaren Bereich nicht ordnungsgemäß gedruckt.

Stellen Sie immer sicher, dass Sie die richtige XDC-Datei für den Drucker verwenden. Vermeiden Sie beispielsweise die Auswahl einer XDC-Datei für einen 300-dpi-Drucker und das Senden des Dokuments an einen 200-dpi-Drucker.

#### Skripte {#scripts}

Ein Formular-Design, das mit den Kommunikations-APIs verwendet wird, kann Skripte enthalten, die auf dem Server ausgeführt werden. Stellen Sie sicher, dass ein Formular-Design keine Skripte enthält, die auf dem Client ausgeführt werden. Weitere Informationen zum Erstellen von Formular-Design-Skripten finden Sie in der Hilfe zu Designer.

<!-- #### Working with Fonts
 Document Considerations for Working with Fonts>> -->

#### Schriftzuordnung {#font-mapping}

Wenn eine Schriftart auf einem Client-Computer installiert ist, ist sie in der Dropdown-Liste in Designer verfügbar. Wenn die Schriftart nicht installiert ist, müssen Sie den Schriftnamen manuell angeben. Die Option „Nicht verfügbare Schriften dauerhaft ersetzen“ in Designer kann deaktiviert sein. Andernfalls wird beim Speichern der XDP-Datei in Designer der Name der Ersatzschriftart in die XDP-Datei geschrieben. Dies bedeutet, dass die druckerresidente Schriftart nicht verwendet wird.

Um ein Formular zu entwerfen, das druckerresidente Schriftarten verwendet, wählen Sie in Designer den Namen einer Schriftart, die mit den auf dem Drucker verfügbaren Schriftarten übereinstimmt. Eine Liste der für PCL oder PostScript unterstützten Schriftarten befindet sich in den entsprechenden Geräteprofilen (XDC-Dateien). Alternativ kann eine Schriftzuordnung erstellt werden, um nicht druckerresidente Schriftarten druckerresidenten Schriftarten mit einem anderen Schriftartennamen zuzuordnen. In einem PostScript-Szenario können beispielsweise Verweise auf die Schriftart Arial® der druckerresidenten Helvetica®-Schriftart zugeordnet werden.

Es gibt zwei Arten von OpenType®-Schriftarten. Ein Typ ist eine TrueType OpenType®-Schriftart, die von PCL unterstützt wird. Der andere ist CFF OpenType®. Die PDF- und PostScript-Ausgabe unterstützt eingebettete Type-1-, TrueType- und OpenType®-Schriftarten. Die PCL-Ausgabe unterstützt eingebettete TrueType-Schriftarten.

Type-1- und OpenType®-Schriftarten sind nicht in die PCL-Ausgabe eingebettet. Inhalte, die mit Type-1- und OpenType®-Schriftarten formatiert sind, werden gerastert und als ein Bitmap-Bild generiert, das groß und langsamer zu generieren sein kann.

Heruntergeladene oder eingebettete Schriftarten werden beim Generieren der PostScript-, PCL- oder PDF-Ausgabe automatisch ersetzt. Dies bedeutet, dass nur die Teilmenge der Schriftzeichen, die zum ordnungsgemäßen Rendern des generierten Dokuments erforderlich sind, in die generierte Ausgabe aufgenommen wird.

#### Arbeiten mit Geräteprofildateien (XDC-Datei) {#working-with-xdc-files}

Ein Geräteprofil (XDC-Datei) ist eine Druckerbeschreibungsdatei im XML-Format. Diese Datei ermöglicht es den Kommunikations-APIs, Dokumente als Laser- oder Etikettendruckerformate auszugeben. Kommunikations-APIs verwenden die XDC-Dateien, einschließlich:

- hppcl5c.xdc

- hppcl5e.xdc

- ps_plain_level3.xdc

- ps_plain.xdc

- zpl300.xdc

- zpl600.xdc

- zpl300.xdc

- ipl300.xdc

- ipl400.xdc

- tpcl600.xdc

- dpl300.xdc

- dpl406.xdc

- dpl600.xdc

Es ist nicht erforderlich, diese Dateien zu ändern, um Dokumente zu erstellen. Sie können sie jedoch an Ihre Geschäftsanforderungen anpassen.

Diese Dateien sind Beispiel-XDC-Dateien, die die Funktionsmerkmale bestimmter Drucker, z. B. residente Schriftarten, Papierfächer und Hefter, unterstützen. Diese Beispieldateien sollen Ihnen verständlich machen, wie Sie Ihre eigenen Drucker mithilfe von Geräteprofilen einrichten können. Die Beispiele sind auch ein Ausgangspunkt für ähnliche Drucker in derselben Produktlinie.

#### Arbeiten mit der XCI-Konfigurationsdatei {#working-with-xci-files}

Kommunikations-APIs verwenden eine XCI-Konfigurationsdatei, um Aufgaben auszuführen, z. B. um zu steuern, ob es sich bei der Ausgabe um einen einzelnen Bereich handelt oder ob sie paginiert wird. Obwohl diese Datei Einstellungen enthält, die festgelegt werden können, ist es nicht üblich, diesen Wert zu ändern. <!-- The default.xci file is located in the svcdata\XMLFormService folder. -->

Sie können eine modifizierte XCI-Datei übergeben, während Sie eine Kommunikations-API verwenden. Erstellen Sie dabei eine Kopie der Standarddatei, ändern Sie nur die Werte, die geändert werden müssen, um Ihre Geschäftsanforderungen zu erfüllen, und verwenden Sie die geänderte XCI-Datei.

Kommunikations-APIs beginnen mit der standardmäßigen XCI-Datei (oder der geänderten Datei). Anschließend werden Werte angewendet, die mithilfe der Kommunikations-APIs angegeben werden. Diese Werte überschreiben die XCI-Einstellungen.

Die folgende Tabelle gibt die XCI-Optionen an.

| XCI-Option | Beschreibung |
| ------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
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

<!-- Using API

 There are two main Communications APIs. The _generatePDFOutput_ generates PDFs, while the _generatePrintedOutput_ generates PostScript, ZPL, and PCL formats. These APIs are available as HTTP endpoints on your environment, both on author and publish instances. Since the publish instances are configured to scale faster than the author instances, it is recommended use these APIs via publish instances.

The first parameter of both the operations accept the path and name of the template file (for example ExpenseClaim.xdp). You can specify a fully qualified path, reference path of your AEM Repository, or path of a binary file. The second parameter accepts an XML document that is merged with the template while generating the output document. -->
