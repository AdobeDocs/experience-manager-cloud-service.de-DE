---
title: Generieren eines Datensatzdokuments für adaptive Formulare?
description: Erfahren Sie, wie Sie eine Vorlage für ein Datensatzdokument für Kernkomponenten adaptiver Formulare generieren.
feature: Adaptive Forms, Core Components
exl-id: 15540644-c0c3-45ce-97d3-3bdaa16fb4b6
role: User, Developer
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '3244'
ht-degree: 98%

---

# Generieren eines Datensatzdokuments für adaptive Formulare (Kernkomponenten)

## Überblick {#overview}

Wenn ein Formular ausgefüllt oder übermittelt wird, können Sie das Formular drucken oder als Dokument speichern. Dies wird als Datensatzdokument (DoR) bezeichnet. Es handelt sich dabei um eine druckoptimierte Kopie des gesendeten Formulars. Auch können Sie im Datensatzdokument mittels Verweis Informationen erfassen, die Kunden zu einem späteren Zeitpunkt eingegeben haben, oder mithilfe des Datensatzdokuments Formulare und zugehörige Inhalte gemeinsam im PDF-Format archivieren.

![Datensatzdokument (Document of Record, DoR)](assets/document-of-record.png)

Um ein Datensatzdokument zu erstellen, wird eine XFA- oder AcroForm-basierte Vorlage mit Daten zusammengeführt, die über ein adaptives Formular erfasst wurden. Sie können ein Datensatzdokument entweder automatisch oder auf Anfrage generieren. Mit der On-Demand-Option können Sie eine benutzerdefinierte XFA- oder AcroForm-basierte Vorlage angeben, um Ihrem Datensatzdokument ein benutzerdefiniertes Erscheinungsbild zu verleihen.

Sie haben folgende Möglichkeiten:

* [Erzeugen eines XFA-basierten Datensatzdokuments](#generate-an-XFA-based-document-of-record)
* [Erzeugen eines AcroForm-basierten Datensatzdokuments (Acrobat Form PDF)](#generate-an-Acroform-based-document-of-record)
* [Automatisches Generieren eines Datensatzdokuments](#auto-generate-a-document-of-record)

## Bevor Sie beginnen {#components-to-automatically-generate-a-document-of-record}

Bevor Sie beginnen, lernen Sie die für ein Datensatzdokument erforderlichen Assets kennen und bereiten Sie sie vor:

**Basisvorlage:** Eine XFA-Vorlage (XDP-Datei), die in Forms Designer oder einem Acrobat-Formular (AcroForm) erstellt wurde. Über die [Basisvorlage](#base-template-of-a-document-of-record) werden Stil- und Branding-Informationen für ein Datensatzdokument festgelegt. Laden Sie vorher Ihre XFA-Vorlage (XDP-Datei) in Ihre AEM Forms-Instanz hoch.

**Adaptives Formular**: Ein adaptives Formular, für das das Datensatzdokument generiert werden soll.

## Erzeugen eines XFA-basierten Datensatzdokuments {#generate-an-XFA-based-document-of-record}

Laden Sie Ihre XFA-Vorlage (XDP-Datei) in Ihre AEM Forms-Instanz hoch. Führen Sie die folgenden Schritte aus, um ein adaptives Formular zu konfigurieren und die XFA-Vorlage (XDP-Datei) als Vorlage für das Datensatzdokument zu verwenden:

1. Klicken Sie in der Experience Manager-Autor-Instanz auf **[!UICONTROL Forms]** > **[!UICONTROL Formulare und Dokumente].**
1. Wählen Sie ein Formular aus oder erstellen Sie ein adaptives Formular und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie im Fenster „Eigenschaften“ **[!UICONTROL Formularmodell]**.
1. Öffnen Sie die Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie im Dropdown-Menü **[!UICONTROL Auswählen aus]** die Option **[!UICONTROL Formulardatenmodell]**, **[!UICONTROL Schema]** oder **[!UICONTROL Keine]** aus. Sie können auch bei der Erstellung eines Formulars ein Formularmodell auswählen.
1. Wählen Sie auf der Registerkarte „Formularmodell“ im Abschnitt „Konfiguration der Datensatzdokument-Vorlagenkonfiguration“ die Option **Formularvorlage als Datensatzdokument-Vorlage zuordnen**. Bei Auswahl dieser Option werden alle auf Ihrem Computer verfügbaren XFA-Vorlagen (XDP-Dateien) angezeigt. Wählen Sie die entsprechende Datei aus. Stellen Sie außerdem sicher, dass dasselbe Schema (Datenschema) für das adaptive Formular und die ausgewählte XFA-Vorlage (XDP-Datei) verwendet wird.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

Ihr adaptives Formular ist jetzt so konfiguriert, dass eine XDP-Datei als Vorlage für den Nachweis verwendet wird. Der nächste Schritt besteht darin, [die Komponenten des adaptiven Formulars an die entsprechenden Vorlagenfelder zu binden](#bind-adaptive-form-components-with-template-fields).

## Erzeugen eines AcroForm-basierten Datensatzdokuments {#generate-an-Acroform-based-document-of-record}

Laden Sie Ihr Adobe Acrobat-PDF (AcroForm) in Ihre AEM Forms-Instanz hoch. Führen Sie die folgenden Schritte aus, um ein adaptives Formular zur Verwendung von Adobe Acrobat-PDF (AcroForm) als Vorlage für das Datensatzdokument zu konfigurieren:

1. Klicken Sie in der Experience Manager-Autor-Instanz auf **[!UICONTROL Forms]** > **[!UICONTROL Formulare und Dokumente].**
1. Wählen Sie ein Formular aus oder wählen Sie **[!UICONTROL Erstellen eines adaptiven Formulars]** und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie im Fenster „Eigenschaften“ **[!UICONTROL Formularmodell]**.
1. Öffnen Sie die Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie im Dropdown-Menü **[!UICONTROL Auswählen aus]** die Option **[!UICONTROL Formulardatenmodell]**, **[!UICONTROL Schema]** oder **[!UICONTROL Keine]** aus. Sie können auch bei der Erstellung eines Formulars ein Formularmodell auswählen.
1. Wählen Sie auf der Registerkarte „Formularmodell“ im Abschnitt „Konfiguration der Datensatzdokument-Vorlagenkonfiguration“ die Option **Formularvorlage als Datensatzdokument-Vorlage zuordnen**. Bei Auswahl dieser Option werden alle auf Ihrem Gerät verfügbaren Acrobat-PDFs (AcroForm) angezeigt. Wählen Sie das AcroForm aus, das Sie verwenden möchten.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

Ihr adaptives Formular ist jetzt so konfiguriert, dass ein AcroForm als Vorlage für den Nachweis verwendet wird. Der nächste Schritt besteht darin, [die Komponenten des adaptiven Formulars an die entsprechenden Vorlagenfelder zu binden](#bind-adaptive-form-components-with-template-fields).

## Automatisches Generieren eines Datensatzdokuments {#auto-generate-a-document-of-record}

Wenn ein adaptives Formular so konfiguriert ist, dass automatisch ein Datensatzdokument generiert wird, wird dieses direkt aktualisiert, sobald das Formular geändert wird. Wenn beispielsweise ein Feld aus einem vorhandenen adaptiven Formular entfernt wird, wird das entsprechende Feld ebenfalls entfernt und ist nicht im Datensatzdokument sichtbar. Die automatische Erzeugung eines Datensatzdokuments bietet jedoch noch zahlreiche weitere Vorteile:

* Bindungen von Daten müssen von Formularentwicklern nicht mehr manuell verwaltet werden. Das automatisch generierte Datensatzdokument übernimmt bereits alle Aktualisierungen im Zusammenhang mit der Datenbindung.
* Felder, die als vom Datensatzdokument ausgeschlossen markiert sind, müssen von Formularentwicklern nicht manuell ausgeblendet werden. Das automatisch generierte Datensatzdokument ist bereits so vorkonfiguriert, dass solche Felder ausgeschlossen werden.
* Mit der Option zur automatischen Generierung des Datensatzdokuments fällt kein Zeitaufwand mehr für die Erstellung einer entsprechenden Formularvorlage an.
* Mit der Option zur automatischen Generierung des Datensatzdokuments lässt sich dessen Stil und Erscheinungsbild anhand verschiedener Basisvorlagen anpassen. So können Sie den Stil und das Erscheinungsbild des Datensatzdokuments danach auswählen, was für Ihr Unternehmen am besten geeignet ist. Wenn Sie keinen Stil angeben, werden standardmäßig die systemeigenen Stile verwendet.
* Durch die automatische Generierung des Datensatzdokuments wird sichergestellt, dass sämtliche Änderungen im Formular direkt im Datensatzdokument übernommen werden.

Führen Sie die folgenden Schritte aus, um ein adaptives Formular so zu konfigurieren, dass automatisch ein Datensatzdokument erzeugt wird:

1. Klicken Sie in der Experience Manager-Autor-Instanz auf **[!UICONTROL Forms]** > **[!UICONTROL Formulare und Dokumente].**
1. Wählen Sie ein Formular aus oder erstellen Sie ein adaptives Formular und klicken Sie auf **[!UICONTROL Eigenschaften]**.
1. Wählen Sie im Fenster „Eigenschaften“ **[!UICONTROL Formularmodell]**.
1. Öffnen Sie die Registerkarte **[!UICONTROL Formularmodell]** und wählen Sie im Dropdown-Menü **[!UICONTROL Auswählen aus]** die Option **[!UICONTROL Formulardatenmodell]**, **[!UICONTROL Schema]** oder **[!UICONTROL Keine]** aus. Sie können auch bei der Erstellung eines Formulars ein Formularmodell auswählen.
1. Wählen Sie auf der Registerkarte „Formularmodell“ im Abschnitt „Konfiguration der Datensatzdokument-Vorlage“die Option **Datensatzdokument erzeugen**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Binden von Komponenten adaptiver Formulare mit Vorlagenfeldern {#bind-adaptive-form-components-with-template-fields}

Binden Sie Felder adaptiver Formulare mit Vorlagenfeldern, um die erfassten Formulardaten im entsprechenden Datensatzdokument-Feld anzuzeigen. Gehen Sie wie folgt vor, um die Komponenten des adaptiven Formulars an die entsprechenden Felder der Datensatzdokument-Vorlage zu binden:

1. Öffnen Sie das adaptive Formular, das für die Verwendung einer benutzerdefinierten Formularvorlage konfiguriert wurde, um es zu bearbeiten.

1. Wählen Sie eine Komponente des adaptiven Formulars aus und klicken Sie auf das Symbol ![Konfigurieren](assets/Smock_Wrench_18_N.svg). Dadurch wird der Eigenschaften-Browser geöffnet.

1. Wählen Sie im Eigenschaften-Browser ein Feld aus.

   * Bei Verwendung der AcroForm-Vorlage wählen Sie die Feldeigenschaft für den **[!UICONTROL Bindungsverweis zum Datensatzdokument]**.
   * Bei Verwendung der XFA-Vorlage verwenden Sie die Eigenschaft für den **[!UICONTROL Bindungsverweis zum Datenmodell]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

<!-- 
In the following video, Adaptive Form components are bound with corresponding Acroform template fields and the Document of Record is sent as an email attachment.
-->

Sie können Aktionen wie „E-Mail senden“, „AEM-Workflow aufrufen“, „Power Automate-Fluss aufrufen“ und andere [Übermittlungsaktionen](configuring-submit-actions.md) verwenden, um ein Datensatzdokument zu erhalten.
![Bildübermittlungsaktionen](/help/forms/assets/submit-actions-img.png)


>[!NOTE]
>
> Sie können den Nachweis für jedes Formulardatenmodell speichern, indem Sie die Eigenschaft **[!UICONTROL Bindungsverweis für Nachweis]** verwenden.

## Inkrementelle Aktualisierungen der Datensatzdokument-Vorlage {#document-of-record-template-incremental-updates}

Adaptive Formulare und entsprechende Vorlagen für Datensatzdokumente können sich im Laufe der Zeit weiterentwickeln. So können Sie etwa Felder zu einem adaptiven Formular oder einer Datensatzdokument-Vorlage hinzufügen, entfernen oder ändern.

Wenn Sie Änderungen an einer Datensatzdokument-Vorlage vornehmen und die geänderte Vorlage in AEM Forms hochladen, erkennt der Editor für adaptive Formulare automatisch die geänderten Bindungen und informiert Sie über die Komponenten des adaptiven Formulars, für die neue Bindungen erforderlich sind. Dies ermöglicht es Ihnen, eine Datensatzdokument-Vorlage sukzessive zu aktualisieren.

Zum Beispiel: Beim Unternehmen *We.Retail* wird eine AcroForm-basierte Datensatzdokumentvorlage namens *we-retail-bill.pdf* verwendet. Die Vorlage sieht wie folgt aus:

![Originalvorlage](assets/we-retail-invoice.png)

Nachdem das Unternehmen die Vorlage einige Zeit verwendet hat, entscheidet es sich, das Feld `invoice-number` in `bill-number` umzubenennen und die E-Mail-Adresse der Käufer zu erfassen. Ein Entwickler aktualisiert den Namen des Felds `invoice-number` und fügt der Vorlage ein Feld zur Eingabe der E-Mail-Adresse hinzu. Außerdem erstellt er eine neue Version der Vorlage namens *we-retail-invoice-v2.pdf*.

![Aktualisierte Vorlage](assets/we-retail-new-invoice.png)

<!--

The developer uploads and applies to the updated template to the adaptive form. The adaptive form automatically detects and displays list of fields where binding has changed.

![Binding Error](assets/we-retail-binding-error.png)

The form developer binds Adaptive Forms fields with corresponding Document of Record template.

-->

>[!VIDEO](assets/we-retail-binding.mp4)

Bei der Übermittlung des adaptiven Formulars wird dann ein aktualisiertes Datensatzdokument erstellt.

![Aktualisiert:](assets/we-retail-new-invoice-sent-to-customer.png)

## Wichtige Aspekte beim Arbeiten mit einem Datensatzdokument {#key-considerations-when-working-with-document-of-record}

Beachten Sie die folgenden Hinweise und Einschränkungen beim Arbeiten mit einem Datensatzdokument für adaptive Formulare.

* Datensatzdokument-Vorlagen unterstützen keinen Rich-Text. Daher wird jeglicher Rich-Text, der im statischen adaptiven Formular oder in den von den Benutzenden ausgefüllten Informationen enthalten ist, im Datensatzdokument als unformatierter Text angezeigt.
* Dokumentfragmente in einem adaptiven Formular werden im Datensatzdokument nicht angezeigt. Adaptive Formularfragmente werden jedoch unterstützt.
* Die Inhaltsbindung wird in Datensatzdokumenten, die für auf XML-Schemata basierende adaptive Formulare generiert werden, nicht unterstützt.
* Lokalisierte Versionen des Datensatzdokuments werden für ein Gebietsschema bedarfsgesteuert erstellt, wenn der Benutzer die Darstellung des Datensatzdokuments anfordert. Die Lokalisierung des Datensatzdokuments erfolgt zusammen mit der Lokalisierung des adaptiven Formulars. <!-- For more information on localization of Document of Record and Adaptive Forms see Using AEM translation workflow to localize Adaptive Forms and Document of Record.-->

<!-- ## Configure an adaptive form to generate  Document of Record {#adaptive-form-types-and-their-documents-of-record}

While creating an adaptive form, in the Form Model tab of Adaptive Form properties, select one the following option: 

* **None**
  Select the option to create an Adaptive Form without a form model. When the option is selected, the Document of Record is automatically generated for your Adaptive Form.

* **[Associate form template as a Document of Record template](creating-adaptive-form.md#create-an-adaptive-form-based-on-an-xfa-form-template)**
  
  Select the option to use an XFA Form as a template for Document of Record. 

* **[Generate Document of Record](creating-adaptive-form.md#create-an-adaptive-form-based-on-xml-or-json-schema)**
  Select the option to use an XFA Form as a template. When the option is selected, the Document of Record is automatically generated for your Adaptive Form. When you use an XML schema as a template for an Adaptive Form, ensure that the adaptive form and associated XFA Form use the same XML schema as your Adaptive Form
  

When you select a form model, configure Document of Record using options available under Document of Record Template Configuration. See [Document of Record Template Configuration](#document-of-record-template-configuration). -->

## Zuordnen von adaptiven Formularelementen {#mapping-of-adaptive-form-elements}

Im Folgenden sind die Komponenten des adaptiven Formulars sowie die ihnen zugehörigen XFA-Komponenten aufgeführt. Ebenfalls ist aus der Tabelle abzulesen, ob Letztere im Datensatzdokument aufgenommen werden.

### Felder {#fields}

<table>
 <tbody>
  <tr>
   <th>Komponente eines adaptiven Formulars</th>
   <th>Zugehörige XFA-Komponente</th>
   <th>Standardmäßig in Datensatzdokument-Vorlage enthalten?</th>
   <th>Anmerkungen</th>
  </tr>
  <tr>
   <td>Schaltfläche</td>
   <td>Schaltfläche</td>
   <td>Falsch</td>
   <td> </td>
  </tr>
  <tr>
   <td>Kontrollkästchen</td>
   <td>Kontrollkästchen</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Datumsauswahl</td>
   <td>Datum-/Uhrzeitfeld</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Dropdown-Liste</td>
   <td>Dropdown-Liste</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Numerisches Feld</td>
   <td>Numerisches Feld</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Optionsschaltfläche</td>
   <td>Optionsschaltfläche</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Textfeld</td>
   <td>Textfeld</td>
   <td>Ja</td>
   <td> </td>
  </tr>
  <tr>
   <td>Schaltfläche „Zurücksetzen“</td>
   <td>Schaltfläche „Zurücksetzen“</td>
   <td>Falsch</td>
   <td> </td>
  </tr>
  <tr>
   <td>Schaltfläche „Senden“</td>
   <td><p>Schaltfläche „E-Mail senden“</p> <p>Schaltfläche „HTTP senden“</p> </td>
   <td>Falsch</td>
   <td> </td>
  </tr>
  <tr>
   <td>Dateianhang</td>
   <td> </td>
   <td>Falsch</td>
   <td>In Datensatzdokument-Vorlage nicht verfügbar. Nur über Anhänge in Datensatzdokument-Vorlage verfügbar.</td>
  </tr>
 </tbody>
</table>

### Container {#containers}

<table>
 <tbody>
  <tr>
   <th>Komponente eines adaptiven Formulars</th>
   <th>Zugehörige XFA-Komponente</th>
   <th>Anmerkungen</th>
  </tr>
  <tr>
   <td>Bereich<br /> </td>
   <td>Teilformular<br /> </td>
   <td>Wiederholbare Bedienfelder werden wiederholbaren Teilformularen zugeordnet.</td>
  </tr>
 </tbody>
</table>

### Statische Komponenten {#static-components}

| Komponente eines adaptiven Formulars | Zugehörige XFA-Komponente | Anmerkungen |
|---|---|---|
| Bild | Bild | Die Komponenten „TextDraw“ und „Image“ (unabhängig davon, ob gebunden oder nicht) werden in dem Datensatzdokument für ein XSD-basiertes adaptives Formular immer angezeigt, es sei denn, sie werden per Einstellungen des Datensatzdokuments ausgeschlossen. |
| Text | Text |

### Tabellen {#tables}

Die Tabellenkomponenten adaptiver Formulare (wie Kopf- und Fußzeile sowie Zeilen) sind den entsprechenden XFA-Komponenten zugeordnet. Sie können Tabellen im Datensatzdokument wiederholbare Bereiche zuordnen.

## Basisvorlage eines Datensatzdokuments {#base-template-of-a-document-of-record}

Die Basisvorlage liefert Informationen zu Stil und Erscheinungsbild des Datensatzdokuments. Das bietet Ihnen die Möglichkeit, das standardmäßige Erscheinungsbild des automatisch generierten Datensatzdokuments anzupassen. So können Sie über eine Basisvorlage beispielsweise festlegen, dass das Datensatzdokument in der Kopfzeile das Logo Ihres Unternehmens und in der Fußzeile Ihre Copyright-Informationen enthält.

Die Musterseite aus der Basisvorlage wird als Musterseite für die Datensatzdokument-Vorlage verwendet. Die Musterseite kann Informationen wie Kopfzeile, Fußzeile und Seitenzahl enthalten, die Sie auf das Datensatzdokument anwenden können. Sie können diese Informationen mithilfe der Basisvorlage auf das Datensatzdokument anwenden, damit das Datensatzdokument automatisch generiert wird. Mithilfe der Basisvorlage können Sie die Standardeigenschaften von Feldern ändern.

Halten Sie sich bei der Entwicklung Ihrer Basisvorlage stets an die [Konventionen für Basisvorlagen](#base-template-conventions).

## Konventionen für Basisvorlagen {#base-template-conventions}

Eine Basisvorlage wird verwendet, um Kopf- und Fußzeile, Stil und Erscheinungsbild eines Datensatzdokuments zu definieren. Die Kopf- und die Fußzeile können Informationen wie Firmenlogo und Copyright-Vermerk enthalten. Die erste Musterseite in der Basisvorlage wird kopiert und dient als Musterseite für das Datensatzdokument. Sie enthält Kopfzeile, Fußzeile, Seitenzahl oder andere Informationen, die auf allen Seiten im Datensatzdokument angezeigt werden sollen. Wenn Sie eine Basisvorlage verwenden, die den Konventionen für Basisvorlagen nicht entspricht, wird die erste Musterseite aus der Basisvorlage trotzdem in der Datensatzdokument-Vorlage verwendet. Es wird dringend empfohlen, dass Sie Ihre Basisvorlage gemäß den Konventionen gestalten und sie für die automatische Generierung von Datensatzdokumenten verwenden.

**Konventionen für Masterseiten**

* Benennen Sie in der Basisvorlage das Stamm-Unterformular mit `AF_METATEMPLATE` und die Musterseite mit `AF_MASTERPAGE`.

* Die Musterseite mit dem Namen `AF_MASTERPAGE`, die sich unterhalb des Stamm-Unterformulars `AF_METATEMPLATE` befindet, hat beim Extrahieren von Kopfzeilen-, Fußzeilen- und Stilinformationen Vorrang.

* Wenn `AF_MASTERPAGE` fehlt, wird die erste Musterseite in der Basisvorlage verwendet.

**Stilkonventionen für Felder**

* Wenn Sie einen Stil auf die Felder im Datensatzdokument anwenden, stellt die Basisvorlage Felder in dem Unterformular `AF_FIELDSSUBFORM` unter dem Stamm-Unterformular `AF_METATEMPLATE` bereit.

* Die Eigenschaften dieser Felder werden auf die Felder in dem Datensatzdokument angewendet. Benennungen für diese Felder sollten der Form `AF_<name of field in all caps>_XFO` folgen. So sollte beispielsweise der Feldname für ein Kontrollkästchen `AF_CHECKBOX_XFO` lauten.

Gehen Sie wie folgt vor, um eine Basisvorlage in Forms Designer zu erstellen:

1. Klicken Sie auf **[!UICONTROL Datei]** > **[!UICONTROL Neu]**.
1. Wählen Sie die Option **[!UICONTROL Auf Basis einer Vorlage]** aus.

1. Wählen Sie die Kategorie **[!UICONTROL Formulare – Aufzuzeichnendes Dokument]**.
1. Wählen Sie **[!UICONTROL DoR-Basisvorlage]** aus.
1. Klicken Sie auf **[!UICONTROL Weiter]** und geben Sie die erforderlichen Informationen ein.

1. (Optional) Ändern Sie den Stil und das Erscheinungsbild von Feldern, die Sie auf die Felder im Datensatzdokument anwenden möchten.
1. Speichern Sie das Formular.
   ![Allgemeine Eigenschaften](/help/forms/assets/form-designer-dor-img.png)

Sie können das gespeicherte Formular nun als Basisvorlage für ein Datensatzdokument verwenden. Ändern oder entfernen Sie keine Skripte, die in der Basisvorlage vorhanden sind.

**Ändern der Basisvorlage**

* Sie sollten auf Felder in der Basisvorlage keinen Stil anwenden. Es wird empfohlen, diese Felder aus der Basisvorlage zu entfernen, damit alle Aktualisierungen der Basisvorlage automatisch übernommen werden.
* Während des Änderns der Basisvorlage dürfen Sie keine Skripte entfernen, hinzufügen oder ändern.

Halten Sie sich bei der Entwicklung einer Basisvorlage genau die oben genannten Konventionen und Anweisungen.

## Anpassen der Branding-Informationen im Datensatzdokument {#customize-the-branding-information-in-document-of-record}

Beim Generieren eines Datensatzdokuments können Sie auf der Registerkarte „Datensatzdokument“ die Branding-Informationen für das Datensatzdokument ändern. Die Registerkarte „Datensatzdokument“ enthält Optionen für Logos, Aussehen, Layout, Kopf- und Fußzeile, zum Anpassen des Haftungsausschlusses sowie eine Optionen zum Entscheiden, ob Sie deaktivierte Kontrollkästchen und Optionsfeldern berücksichtigen möchten.

Achten Sie darauf, dass für Ihren Browser das richtige Gebietsschema festgelegt ist. Dadurch wird sichergestellt, dass die von Ihnen auf der Registerkarte für das Datensatzdokument eingegebenen Branding-Informationen lokalisiert werden. Gehen Sie wie folgt vor, um die Branding-Informationen des Datensatzdokuments anzupassen:

1. Wählen Sie einen Bereich (Stammbereich) im Datensatzdokument aus und wählen Sie dann ![Konfigurieren](assets/configure.png).
1. Wählen Sie ![dortab](assets/dortab.png). Die Registerkarte „Datensatzdokument“ wird angezeigt.
1. Wählen Sie entweder die Standardvorlage oder eine benutzerdefinierte Vorlage für die Darstellung des Datensatzdokuments aus. Wenn Sie die Standardvorlage auswählen, wird eine Miniaturvorschau des Datensatzdokuments unterhalb der Dropdown-Liste „Vorlage“ angezeigt.
1. Abhängig davon, ob Sie eine standardmäßige oder benutzerdefinierte Vorlage auswählen, werden einige oder alle der folgenden Eigenschaften auf der Registerkarte „Datensatzdokument“ angezeigt. Geben Sie die folgenden Eigenschaften an, um das Erscheinungsbild des Datensatzdokuments zu definieren:

   1. **Allgemeine Eigenschaften**:
      * **Vorlage**: Wenn Sie eine benutzerdefinierte Vorlage auswählen möchten, wählen Sie eine XDP-Datei auf Ihrem [!DNL AEM Forms]-Server aus. Wenn Sie eine Vorlage verwenden möchten, die sich noch nicht auf Ihrem [!DNL AEM Forms]-Server befindet, müssen Sie die XDP-Datei zuerst auf Ihren [!DNL AEM Forms]-Server hochladen.
      * **Akzentfarbe**: Die Farbe, in der Kopfzeilentext und Trennlinien im Datensatzdokument-PDF gerendert werden.
      * **Schriftfamilie**: Schriftfamilie des Textes im Datensatzdokument-PDF.

        >[!NOTE]
        >
        > AEM Forms bietet eine Vielzahl integrierter Schriftarten, die nahtlos in PDF-Dateien integriert werden können. Um die Liste der unterstützten Schriftarten anzuzeigen, [klicken Sie hier](/help/forms/supported-out-of-the-box-fonts.md).

      * **Formularobjekte einschließen, die nicht mit dem Datenmodell verbunden sind**: Durch Festlegen dieser Eigenschaft werden ungebundene Felder aus dem schemabasierten adaptiven Formular in das Datensatzdokument einbezogen.

      <!-- **Exclude hidden fields from the Document of Record**: Setting the property identifies the hidden fields for exclusion from Document of Record.-->

      * **Beschreibung der Bedienfelder ausblenden**: Durch Festlegen dieser Eigenschaft ist die Beschreibung des Bedienfeldes bzw. der Tabelle im Datensatzdokument nicht enthalten. Gilt für Bedienfeld und Tabelle.



   1. **Formularfeldeigenschaften**:
      * **Für Kontrollkästchen und Optionsschaltflächenkomponenten nur ausgewählte Werte einblenden**: Durch Festlegen dieser Eigenschaft werden nur die ausgewählten Werte von Kontrollkästchen und Optionsfeldern im [!UICONTROL Datensatzdokument] angezeigt.
      * **Trennzeichen für mehrere Werte**: Sie können ein beliebiges Trennzeichen wie Komma oder Zeilenumbruch auswählen, um mehrere Werte anzuzeigen.
      * **Optionenausrichtung**: Sie können die gewünschte Ausrichtung (horizontal, vertikal, wie das adaptive Formular) auswählen, um die Ausrichtung für Felder wie Kontrollkästchen oder Optionsfelder festzulegen, die im [!UICONTROL Datensatzdokument] angezeigt werden sollen. Standardmäßig ist für die Felder im [!UICONTROL Datensatzdokument] die vertikale Ausrichtung festgelegt. Das Festlegen der Eigenschaften über die [!UICONTROL Formularfeldeigenschaften] des Datensatzdokuments überschreibt die Eigenschaften, die in der [!UICONTROL Elementausrichtung] für die Felder in einem adaptiven Formular festgelegt sind. Wenn Sie die Option [!UICONTROL Wie adaptives Formular] auswählen, wird die in der Autoreninstanz des adaptiven Formulars konfigurierte Ausrichtung für Felder des [!UICONTROL Datensatzdokuments] verwendet.
      * **Anzahl der Optionen für die horizontale Ausrichtung**:You: Sie können die Anzahl der Optionen festlegen, die im Nachweis für die horizontale Ausrichtung angezeigt werden sollen.



   1. **Eigenschaften der primären Seite**:
      * **Logo-Bild**: Sie können wahlweise das Logo-Bild aus dem adaptiven Formular verwenden, eines aus DAM auswählen oder eines von Ihrem Computer hochladen.
      * **Formulartitel**: Titel des Datensatzdokuments.
      * **Kopfzeilentext**: Text, der im Kopfzeilenabschnitt des Datensatzdokuments angezeigt wird.
      * **Haftungsausschluss-Bezeichnung**: Bezeichnung des Haftungsausschlusses.
      * **Haftungsausschluss**: Text, der den Umfang der Rechte und Pflichten für das Datensatzdokument angibt.
      * **Text des Haftungsausschlusses**: Text des Haftungsausschlusses.

      ![Eigenschaften der Musterseite](/help/forms/assets/dorpropertiesimg.png)

   >[!NOTE]
   >
   >Wenn Sie eine Vorlage für ein adaptives Formular mit einer Designer-Version vor 6.3 verwenden, müssen Sie sicherstellen, dass im Stamm-Unterformular der Vorlage für das adaptive Formular Folgendes vorhanden ist, damit Akzentfarbe und Schriftfamilie funktionieren:

   ```xml
   <proto>
   <font typeface="Arial"/>
   <fill>
   <color value="4,166,203"/>
   </fill>
   <edge>
   <color value="4,166,203"/>
   </edge>
   </proto>
   ```

1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Branding-Änderungen zu speichern.

>[!NOTE]
> 
> Um einen benutzerdefinierten Formulartitel in Ihrem Nachweis anzuzeigen, bearbeiten Sie den **benutzerdefinierten Formulartitel** unter **Nachweis-Eigenschaften** > **Eigenschaften der primären Seite**. Dieser benutzerdefinierte Titel:
> 
> * Erscheint in der Kopfzeile der generierten PDF-Datei
> * Wird als Titel in den Dokumenteneigenschaften der PDF-Datei angezeigt
> * Wird beim Öffnen der PDF-Datei als Ansichtstitel angezeigt

## Tabellen- und Spalten-Layouts für Bereiche im Datensatzdokument {#table-and-column-layouts-for-panels-in-document-of-record}

Ihr adaptives Formular ist möglicherweise sehr lang und enthält mehrere Formularfelder. Sie möchten vielleicht nicht, dass ein Datensatzdokument als eine exakte Kopie des adaptiven Formulars gespeichert wird. Jetzt können Sie zum Speichern eines oder mehrerer Bereiche des adaptiven Formulars in der Datensatzdokument-PDF ein Tabellen- oder Spalten-Layout auswählen.

Wählen Sie vor dem Generieren eines Datensatzdokuments in den Einstellungen eines Bereichs als „Layout für das Datensatzdokument“ entweder „Tabelle“ oder „Spalte“ für diesen Bereich aus. Die Felder in dem Bereich werden in dem Datensatzdokument entsprechend angeordnet.

![Felder in einem Bereich, die im Datensatzdokument im Tabellen-Layout dargestellt werden](assets/dortablelayout.png)

Felder in einem Bereich, die im Datensatzdokument im Tabellen-Layout dargestellt werden

![Felder in einem Bereich, die im Datensatzdokument im Spalten-Layout dargestellt werden](assets/dorcolumnlayout.png)

Felder in einem Bereich, die im Datensatzdokument im Spalten-Layout dargestellt werden

## Einstellungen für Datensatzdokumente {#document-of-record-settings}

In den Datensatzdokument-Einstellungen können Sie Optionen auswählen, die in dem Datensatzdokument enthalten sein sollen. Eine Bank akzeptiert zum Beispiel Name, Alter, Sozialversicherungsnummer und Telefonnummer in einem Formular. Das Formular generiert eine Bankkontonummer und Details zur Zweigstelle. Sie können festlegen, dass nur Name, Sozialversicherungsnummer, Bankkonto und Filialendetails im Datensatzdokument angezeigt werden sollen.

Die Einstellung der Komponente „Datensatzdokument“ ist in den Eigenschaften verfügbar. Um auf die Eigenschaften einer Komponente zuzugreifen, wählen Sie die Komponente aus und klicken Sie auf ![cmppr](assets/cmppr.png) in der Überlagerung. Die Eigenschaften werden in der Seitenleiste mit den folgenden Einstellungen angezeigt.

**Einstellungen auf Feldebene**

* **Aus Datensatzdokument ausschließen**: Wenn aktiviert, ist das Feld im Datensatzdokument nicht enthalten. Dies ist eine skriptfähige Eigenschaft namens `excludeFromDoR`. Ihr Verhalten ist von der auf Formularebene befindlichen Eigenschaft **Felder aus DoR ausschließen, wenn sie ausgeblendet sind** abhängig.

* **Bereich als Tabelle anzeigen**: Wenn aktiviert, wird der Bereich im Datensatzdokument als Tabelle angezeigt, wenn der Bereich weniger als 6 Felder enthält. Gilt nur für den Bereich.
* **Titel aus Datensatzdokument ausschließen**: Wenn aktiviert, ist der Titel des Bereichs bzw. der Tabelle im Datensatzdokument nicht enthalten. Gilt nur für Bereiche und Tabellen.
* **Beschreibung aus Datensatzdokument ausschließen**: Wenn aktiviert, ist die Beschreibung des Bereichs bzw. der Tabelle im Datensatzdokument nicht enthalten. Gilt nur für Bereiche und Tabellen.
* **Ausgeblendete Felder vom Datensatzdokument ausschließen**: Wenn Sie diese Eigenschaft auswählen, werden ausgeblendete Felder aus dem Datensatzdokument ausgeschlossen. Sie gilt für alle Formularfelder. Standardmäßig ist die Option **Ausgeblendete Felder vom Datensatzdokument ausschließen** nicht ausgewählt.

**Einstellungen auf Formularebene**

* **Ungebundene Felder in Datensatzdokument einbeziehen**: Wenn aktiviert, werden ungebundene Felder aus einem Schema-basierten adaptiven Formular im Datensatzdokument eingefügt. Diese Option ist standardmäßig aktiviert.

## Siehe auch {#see-also}

{{see-also}}


<!-- 

**Exclude fields from DoR if hidden:** Set the property to exclude the hidden fields from Document of Record at form submission. When you enable [Revalidate on server](/help/forms/configuring-submit-actions.md#server-side-revalidation-in-adaptive-form-server-side-revalidation-in-adaptive-form), the server recomputes the hidden fields before excluding those fields from the Document of Record.

!->>
