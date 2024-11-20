---
title: Abrechenbare APIs für Transaktionsberichte
description: Liste aller APIs, die als Transaktionen verbucht werden
feature: Adaptive Forms, Foundation Components
exl-id: 6dfcac3e-5654-4b4f-9134-0cd8be24332e
role: Admin, Developer, User
source-git-commit: 2b76f1be2dda99c8638deb9633055e71312fbf1e
workflow-type: ht
source-wordcount: '1438'
ht-degree: 100%

---


# Abrechenbare APIs für Transaktionsberichte {#transaction-reports-billable-apis}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/de/docs/experience-manager-65/content/forms/transaction-reports/transaction-reports-billable-apis) |
| AEM as a Cloud Service | Dieser Artikel |


AEM Forms bietet mehrere APIs zum Senden von Formularen, zum Verarbeiten von Dokumenten und zum Rendern von Dokumenten. Einige APIs werden als Transaktionen verbucht, andere können kostenlos verwendet werden. Dieses Dokument enthält eine Liste aller APIs, die in einem Transaktionsbericht als Transaktionen verbucht werden. Im Folgenden finden Sie einige gängige Szenarien, in denen eine kostenpflichtige API verwendet wird:

* Senden eines adaptiven Formulars
* Konvertieren eines Dokuments aus einem Format in ein anderes
* Reduzieren eines dynamischen PDF-Dokuments
* Generieren eines Datensatzdokuments (mit dem Forms-Dienst oder dem Ausgabe-Service)
* Zusammenführen eines interaktiven PDF-Dokuments mit einem anderen PDF-Dokument
* Verwenden des Schritts zum Zuweisen einer Aufgabe und der Kommunikations-API-Schritte von AEM-Workflows

Kostenpflichtige APIs berücksichtigen nicht die Anzahl der Seiten, die Länge eines Dokuments oder Formulars oder das endgültige Format des wiedergegebenen Dokuments. Ein Transaktionsbericht unterteilt die Transaktionen in zwei Kategorien: übermittelte Formulare und gerenderte Dokumente.

* **Übermittelte Formulare**: Wenn Daten von einem mit AEM Forms erstellten Formular beliebigen Typs gesendet werden und die Daten an ein Datenspeicher-Repository oder an eine Datenbank gesendet werden, gilt dies als Formularübermittlung. Beispielsweise wird das Senden eines adaptiven Formulars oder eines Formularsatzes als Formularübermittlung betrachtet. Wenn ein Formularsatz 5 Formulare umfasst und dieser Formularsatz übermittelt wird, zählt der Dienst für Transaktionsberichte dies als 5 Übermittlungen.

* **Gerenderte Dokumente**: Das Generieren eines Dokuments durch Kombinieren einer Vorlage und von Daten, das digitale Signieren oder Zertifizieren eines Dokuments, die Verwendung kostenpflichtiger Document Services-APIs für Dokumenten-Services oder das Konvertieren eines Dokuments von einem Format in ein anderes werden als gerenderte Dokumente verbucht.

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_submission_graph_en"
>title="Verfolgung von Formularübermittlungen"
>abstract="Dieses Diagramm stellt die Anzahl der Übermittlungen adaptiver Formulare während bestimmter Zeiträume dar. Die Zunahme der Übermittlungen könnte darauf hindeuten, dass das Formular beliebter wird oder dass mehr Daten von Benutzerinnen und Benutzern erfasst werden müssen. **Hinweis:** Das Diagramm stellt Daten bereit, die spezifisch für die aktuelle Instanz sind, sodass Sie Trends schnell analysieren und fundierte Entscheidungen treffen können. Für Übermittlungsdaten anderer Instanzen greifen Sie einfach auf das Dashboard der jeweiligen Instanz zu."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_conversions_graph_en"
>title="Nachverfolgung von Dokument-Ausgabedarstellungen"
>abstract="Dieses Diagramm stellt die Anzahl der Dokument-Ausgabedarstellungen während bestimmter Zeiträume dar. **Hinweis:** Das Diagramm stellt Daten bereit, die spezifisch für die aktuelle Instanz sind, sodass Sie Trends schnell analysieren und fundierte Entscheidungen treffen können. Für Übermittlungsdaten anderer Instanzen greifen Sie einfach auf das Dashboard der jeweiligen Instanz zu."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_newForms_graph_en"
>title="Nachverfolgung neuer Formulare"
>abstract="Das Diagramm enthält Informationen zur Anzahl der neu erstellten Formulare in bestimmten Zeiträumen. **Hinweis:** Das Diagramm stellt Daten bereit, die spezifisch für die aktuelle AEM Forms-Autoreninstanz sind. Um Daten anderer Instanzen anzuzeigen, rufen Sie das Dashboard der jeweiligen Instanz auf."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_publishedForms_graph_en"
>title="Nachverfolgung veröffentlichter Formulare"
>abstract="Das Diagramm enthält Informationen zur Anzahl der Formulare, die in bestimmten Zeiträumen erfolgreich veröffentlicht wurden. **Hinweis:** Das Diagramm stellt Daten bereit, die spezifisch für die aktuelle AEM Forms-Veröffentlichungsinstanz sind. Um Konversionsdaten anderer Instanzen anzuzeigen, rufen Sie das Dashboard der jeweiligen Instanz auf."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formCreationAvgDuration_graph_en"
>title="Durchschnittliche Dauer für die Formularerstellung"
>abstract="Das Diagramm zeigt die durchschnittliche Zeit, die zum Erstellen eines Formulars benötigt wurde. Jeder Balken im Diagramm stellt ein bestimmtes Formular dar. Die Höhe des Balkens gibt die durchschnittliche Dauer an, die für die Formularerstellung während dieses Zeitraums verwendet wurde."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formPublishAvgDuration_en"
>title="Durchschnittliche Dauer der Formularerstellung"
>abstract="Das Diagramm zeigt die durchschnittliche Zeit an, die zum Erstellen und Veröffentlichen eines Formulars benötigt wurde, gemessen ab dem ersten Tag, an dem das Formular zur Bearbeitung geöffnet wurde. **Hinweis:** Das Diagramm stellt Daten bereit, die spezifisch für die aktuelle AEM Forms-Autoreninstanz sind. Um Daten anderer Instanzen anzuzeigen, rufen Sie das Dashboard der jeweiligen Instanz auf."


>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_formFragments_graph_en"
>title="Nachverfolgung von Formularfragmenten"
>abstract="Anhand dieses Diagramms können Sie sehen, wie viele Formularfragmente Sie in ihren Formularen verwenden. **Hinweis:** Das Diagramm stellt Daten bereit, die spezifisch für die aktuelle AEM Forms-Veröffentlichungsinstanz sind. Um Konversionsdaten anderer Instanzen anzuzeigen, rufen Sie das Dashboard der jeweiligen Instanz auf."

>[!CONTEXTUALHELP]
>id="aemforms_cs_transaction_reporting_avgFormPerFragments_graph_en"
>title="Nachverfolgung der durchschnittlichen Zeit von Formularfragmenten"
>abstract="Das Diagramm zeigt die durchschnittliche Zeit an, die zum Erstellen eines Formularfragments benötigt wurde, gemessen ab dem ersten Tag, an dem das Formularfragment zur Bearbeitung geöffnet wurde. **Hinweis:** Das Diagramm stellt Daten bereit, die spezifisch für die aktuelle AEM Forms-Veröffentlichungsinstanz sind. Um Konversionsdaten anderer Instanzen anzuzeigen, rufen Sie das Dashboard der jeweiligen Instanz auf."


<!-- 

>[!NOTE]
>
>Transaction Reports UI displays three categories: Forms Submitted, Documents Rendered, and Documents Processed. Both Documents Rendered and Documents Processed are accounted as Documents Rendered.
-->


<!--

## Billable Document Services APIs {#billable-document-services-apis}

### Generate PDF Service {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Creates PDF from HTML pages.</p> </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimizes PDF to reduce file size by stripping unnecessary metadata without affecting the quality.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
 </tbody>
</table>

-->


<!--
### Distiller Service {#distiller-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF</a><br /> </td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/DistillerService.html#createPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">createPDF2</a></td>
   <td>Creates Adobe PDF from supported file types.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

## Kostenpflichtige Document Services-APIs {#billable-document-services-apis}

### Generate PDF-Service {#generate-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#section/Before-you-start" target="_blank">createPDF</a></td>
   <td>Generiert ein PDF-Dokument aus einer Vorlage und führt Daten damit zusammen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/Communications-Services/paths/~1adobe~1forms~1doc~1v1~1generatePrintedOutput/post" target="_blank">exportPDF</a></td>
   <td>Konvertiert XDP-Dateien oder PDF-Dokumente in unterstützte Dateitypen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <!--<tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF2</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#exportPDF2-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">exportPDF3</a></td>
   <td>Converts Adobe PDF to supported file types. </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-3/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlFileToPdf-com.adobe.aemfd.docmanager.Document-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-">htmlFileToPdf</a></td>
   <td><p>Creates PDF from HTML pages.</p> </td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#htmlToPdf2-java.lang.String-java.lang.String-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.aemfd.docmanager.Document-" target="_blank">htmlToPdf2</a></td>
   <td>Creates PDF from URLs pointing to an HTML page.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/pdfg/service/api/GeneratePDFService.html#optimizePDF-com.adobe.aemfd.docmanager.Document-java.lang.String-com.adobe.aemfd.docmanager.Document-" target="_blank">optimizePDF</a></td>
   <td>Optimizes PDF to reduce file size by stripping unnecessary metadata without affecting the quality.</td>
   <td>Documents Processed<br /> </td>
   <td> </td>
  </tr>-->
 </tbody>
</table>

### Ausgabe-Service {#output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PDFOutput" target="_blank">generatePDFOutput</a></td>
   <td>Führt Daten und Vorlagen zusammen, um ein PDF-Dokument zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PDFOutputOptions" target="_blank">generatePDFOutput (PDFOutputOptions)</a></td>
   <td>Führt Daten und Vorlagen zusammen, um ein PDF-Dokument zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig" target="_blank">generatePDFOutputBatch</a></td>
   <td>Führt Daten und Vorlagen zusammen, um einen Satz von PDF-Dokumenten zu erstellen.</td>
   <td>Verarbeitete Dokumente</td>
   <td> <!-- The generatePDFOutputBatch API combines a form template with a record and generates a PDF. When you process a batch of records, the transaction reporting service counts each record as a separate PDF rendition. <br> You can use the <a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> flag to combine multiple renditions to single PDF file. Irrespective of the status of flag, the service counts each record as a separate PDF rendition. --> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutput" target="_blank">generatePrintedOutput</a></td>
   <td>Konvertiert XDP- und PDF-Dokumente in die Dateiformate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-sync/#tag/PrintedOutputOptions" target="_blank">generatePrintedOutput (PrintedOutputOptions)</a></td>
   <td>Konvertiert XDP- und PDF-Dokumente in die Dateiformate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/output-batch/#tag/Batch-Configuration/operation/CreateBatchConfig" target="_blank">generatePrintedOutputBatch</a></td>
   <td>Konvertiert einen Satz von XDP- und PDF-Dokumenten in die Formate PostScript (PS), Printer Command Language (PCL) und ZPL. </td>
   <td>Verarbeitete Dokumente</td>
   <td> <!-- The generatePDFOutputBatch API combines a form template with a record and generates a PDF. When you process a batch of records, the transaction reporting service counts each record as a separate PDF rendition. <br> You can use the <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/javadocs/com/adobe/fd/output/api/BatchOptions.html#getGenerateManyFiles--">getGenerateManyFiles</a> flag to combine multiple renditions to single PDF file. Irrespective of the status of flag, the service counts each record as a separate PDF rendition. --> </td>
  </tr>
 </tbody>
</table>

### DocAssurance-Dienst {#DocAssurance-Service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/docassurance/#tag/DocAssurance" target="_blank">secureDocument</a><br /> </td>
   <td>Mit dieser API können Sie Ihr Dokument sichern. Sie können die API verwenden, um ein PDF-Dokument zu signieren, zu zertifizieren, zu lesen, zu erweitern oder zu verschlüsseln.</td>
   <td>Verarbeitete Dokumente</td>
   <td>Es werden nur die Vorgänge zum Signieren und Zertifizieren des secureDocument in Rechnung gestellt.</td>
  </tr>
 </tbody>
</table>

### Document of Record(DOR)-Dienst {#document-of-record-dor-forms-service-and-output-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://opensource.adobe.com/aem-forms-af-runtime/api/#tag/Generate-DoR/operation/generateDoR" target="_blank">render</a></td>
   <td>Ruft die angegebene Render-Methode auf, um mithilfe der bereitgestellten Parameter ein Datensatzdokument zu generieren.</td>
   <td>Mit dem Forms-Dienst verarbeitete Dokumente</td>
   <td> </td>
  </tr>
  <!--<tr>
   <td><a href="" target="_blank">render</a></td>
   <td>Invokes the specified render method to generate a document of record using provided parameters.</td>
   <td>Documents Processed using Output Service</td>
   <td> </td>
  </tr>-->
 </tbody>
</table>

<!--

### Forms Service {#forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#renderPDFForm-java.lang.String-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.PDFFormRenderOptions-" target="_blank">renderPDFForm</a></td>
   <td>Renders PDF Form from XDP templates. The XP templates are created in Forms Designer.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/forms/api/FormsService.html#exportData-com.adobe.aemfd.docmanager.Document-com.adobe.fd.forms.api.DataFormat-" target="_blank">exportData</a></td>
   <td>Extracts data from a PDF Form or XDP templates</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

<!--
### Convert PDF Service {#convert-pdf-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toImage</a></td>
   <td>Converts a PDF document to a list of image documents. Supported image formats are JPEG, JPEG2K, PNG, and TIFF.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/cpdf/api/ConvertPdfService.html#toImage-com.adobe.aemfd.docmanager.Document-com.adobe.fd.cpdf.api.ToImageOptionsSpec-" target="_blank">toPS</a></td>
   <td>Converts a Flat PDF file to PostScript format using the options specified in the option spec.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

<!--
### Barcoded Forms Service {#barcoded-forms-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/bcf/api/BarcodedFormsService.html#decode-com.adobe.aemfd.docmanager.Document-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-java.lang.Boolean-com.adobe.fd.bcf.api.CharSet-" target="_blank">decode</a></td>
   <td>Decodes all the barcodes in a Document object and returns an org.w3c.dom.Document object that contains data that was retrieved from the barcode.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

### Assembler-Service {#assembler-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/DDX-execution/operation/InvokeDDX">invoke</a></td>
   <td>Führt das DDX-Dokument für die angegebenen Eingabedokumente aus und gibt ein Objekt zurück, das die Zieldokumente enthält</td>
   <td>Verarbeitete Dokumente</td>
   <td>Folgende Vorgänge werden nicht als Transaktionen verbucht:
    <ul>
     <li>Erstellen von Paketen oder Portfolios</li>
     <li>Zusammenfügen mehrerer XDPs </li>
    </ul> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/DDX-execution/operation/InvokeDDX" target="_blank">invoke</a></td>
   <td>Führt das DDX-Dokument für die angegebenen Eingabedokumente aus und gibt ein Objekt zurück, das die Zieldokumente enthält</td>
   <td>Verarbeitete Dokumente</td>
   <td>Der Assembler-Service unterstützt alle Eingabedateiformate, die von PDF Generator, Forms und Ausgabe-Services unterstützt werden, als Ausgabedateiformate. </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager-forms-cloud-service-developer-reference/references/assembler-sync/#tag/Document-conversion/operation/ConvertToPDFA">toPDFA</a></td>
   <td>Konvertieren Sie ein bestimmtes Dokument mithilfe der angegebenen Optionen in PDF/A.</td>
   <td>Verarbeitete Dokumente</td>
   <td> </td>
  </tr>
 </tbody>
</table>

Die Verwendung der invoke-API wird als Transaktion gezählt, wenn Sie einen oder mehrere der folgenden Vorgänge ausführen:

1. Konvertierung von Nicht-PDF-Formaten in PDF-Formate. <!--For instance, the conversion from XDP format to PDF format, catering to both interactive and non-interactive forms of communication, and the conversion from Word to PDF.-->
1. Konvertierung vom PDF-Format in das PDF/A-Format.
1. Konvertierung vom PDF-Format in Nicht-PDF-Formate. Beispiele sind die Umwandlung von PDF in das Bildformat oder die Konvertierung von PDF in das Textformat.


>[!NOTE]
>
>* Die invoke-API des Assembler-Services kann abhängig von der Eingabe intern eine kostenpflichtige API eines anderen Services aufrufen. Daher kann die invoke-API als keine, eine einzige oder auch mehrere Transaktionen verbucht werden. Die Anzahl der gezählten Transaktionen hängt von der Eingabe und den aufgerufenen internen APIs ab.
>* Ein einzelnes PDF-Dokument, das mit dem Assembler-Service erstellt wurde, kann als keine, eine einzige oder auch mehrere Transaktionen erfasst werden. Die Anzahl der gezählten Transaktionen hängt vom bereitgestellten Code ab.
>

<!--
### PDF Utility Service  {#pdf-utility-service}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/pdfutility/services/PDFUtilityService.html#convertPDFtoXDP-com.adobe.aemfd.docmanager.Document-" target="_blank">convertPDFtoXDP</a></td>
   <td>Converts a PDF document into an XDP file. In order for a PDF document to be successfully converted to an XDP file, the PDF document must contain an XFA stream in the AcroForm dictionary.</td>
   <td>Documents Processed</td>
   <td> </td>
  </tr>
 </tbody>
</table>
-->

## Kostenpflichtige Datenerfassungs-APIs {#billable-data-capture-apis}

Alle Übermittlungsereignisse von adaptiven Formularen werden als Transaktionen verbucht. Standardmäßig wird die Übermittlung eines PDF-Formulars nicht als Transaktion verbucht. Verwenden Sie die bereitgestellte [Transaktions-Recorder-API](record-transaction-custom-implementation.md), um eine Übermittlung von PDF-Formularen als Transaktion zu erfassen.

### Adaptive Formulare {#adaptive-forms}

<table>
 <tbody>
  <tr>
   <td><p>Nutzungsszenario</p> </td>
   <td>Beschreibung</td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Senden eines adaptiven Formulars</td>
   <td>Übermittelt ein adaptives Formular entsprechend der konfigurierten Übermittlungsaktion. </td>
   <td>Übermittelte Formulare</td>
   <td>
    <ul>
     <li>Erfolgreiche Übermittlungen zählen als eine oder zwei Transaktionen. Die Anzahl der gezählten Transaktionen hängt vom Typ der für die Übermittlung verwendeten Übermittlungsaktion ab. Das Senden einer PDF-Datei über eine E-Mail-Übermittlungsaktion wird zum Beispiel als zwei Transaktionen gezählt. Eine Transaktion für die Formularübermittlung und eine andere für die PDF, die mit dem DoR-Service (Datensatzdokument) generiert wurde. </li>
     <li>Bei Verwendung des adaptiven Formulars innerhalb eines adaptiven Formulars (Formularsatz von adaptiven Formularen) wird nur eine einzige Transaktion verbucht. Sie können eine beliebige Anzahl adaptiver Formulare innerhalb eines adaptiven Formulars verwenden.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

<!--

### HTML5 Forms {#html-forms}

<table>
 <tbody>
  <tr>
   <td><p>Use Case</p> </td>
   <td>Description </td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting an HTML5 Form</td>
   <td>Submits an HTML5 Form to submit URL configured in the form.</td>
   <td>Forms Submitted</td>
   <td> </td>
  </tr>
 </tbody>
</table>

### Form set {#form-set}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Submitting a form set</td>
   <td>Submits form set to the submit URL configured in the form set.</td>
   <td>Forms Submitted</td>
   <td>
    <ul>
     <li>Using the adaptive form within an adaptive form (Adaptive form formset) accounts only single transaction. You can have any number of adaptive forms within an adaptive form.</li>
     <li>Every form in an HTML5 Forms form set accounts as a separate transaction. </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

-->

## Abrechenbare formularzentrierte AEM-Workflows {#billable--form-centric-aem-workflows}

Die Schritte der Zuweisung von Aufgaben und der Dokumenten-Services von formularzentrierten AEM-Workflows werden als Transaktionen verbucht. Wenn durch einen Workflow-Schritt eine Transaktion verbucht wird, aber der Workflow nicht abgeschlossen werden kann, wird die Transaktionsanzahl trotzdem nicht zurückgesetzt.

<!--
Assign task and document services steps of Form-centric AEM Workflows on OSGi and all the renditions of interactive communication and are accounted as transactions. Previewing an interactive communication on the author instance and previewing on the publish instance using Agent UI are not accounted as transactions. If a workflow step accounts a transaction and the workflow fails to complete, the transaction count is not reversed.
-->


<!--

### Interactive Communication - Web Channel {#interactive-communication-web-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td>Rendering a web channel</td>
   <td>Opens the web version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

### Interactive Communication - Print Channel {#interactive-communication-print-channel}

<table>
 <tbody>
  <tr>
   <td><p>API</p> </td>
   <td>Description</td>
   <td>Transaction report category</td>
   <td>Additional Information</td>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/ccm/channels/print/api/model/PrintChannel.html" target="_blank">render</a> (convert to PDF)</td>
   <td>Generates the PDF version of an interactive communication.</td>
   <td>Documents Rendered</td>
   <td>
    <div>
    </div> </td>
  </tr>
 </tbody>
</table>

-->

### Formularzentrierte AEM-Workflows {#form-centric-aem-workflows}

<table>
 <tbody>
  <tr>
   <td><p>Anwendungsfall</p> </td>
   <td>Kategorie des Transaktionsberichts</td>
   <td>Zusätzliche Informationen</td>
  </tr>
  <tr>
   <td>Übermitteln eines Schritts „Aufgabe zuweisen“</td>
   <td>Übermittelte Formulare</td>
   <td>
    <div>
    </div> </td>
  </tr>
  <tr>
   <td>Übermitteln eines Startpunkts für ein Workflow-Programm </td>
   <td>Übermittelte Formulare</td>
   <td> </td>
  </tr>
 </tbody>
</table>

## Aufzeichnen von kostenpflichtigen APIs als Transaktionen für benutzerspezifischen Code {#recording-billable-apis-as-transactions-for-custom-code}

Aktionen wie das Übermitteln eines PDF-Formulars, die Verwendung der Agent-Benutzeroberfläche zur Vorschau einer interaktiven Kommunikation, die Verwendung nicht standardmäßiger Formularübermittlung und benutzerdefinierte Implementierungen werden nicht als Transaktionen berücksichtigt. AEM Forms bietet eine API zum Aufzeichnen solcher Aktionen als Transaktionen. Sie können die API aus Ihren benutzerdefinierten Implementierungen aufrufen, um [eine Transaktion aufzuzeichnen](/help/forms/record-transaction-custom-implementation.md).

## Ähnliche Artikel {#related-articles}

* [Aufzeichnen einer Transaktion für benutzerdefinierte Implementierungen](/help/forms/record-transaction-custom-implementation.md)
