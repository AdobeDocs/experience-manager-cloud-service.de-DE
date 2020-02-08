---
title: Digitale Assets in mehreren Sprachen erstellen und verwalten und Übersetzungs-Workflows ausführen
description: Erfahren Sie, wie Sie Workflows für die Übersetzung von Assets, darunter Binärdateien, Metadaten und Tags, in mehrere Sprachen automatisieren.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Multilingual assets {#multilingual-assets}

Bei mehrsprachigen Assets handelt es sich um Assets mit Binärdateien, Metadaten und Tags in verschiedenen Sprachen. Im Allgemeinen liegen Binärdateien, Metadaten und Tags für Assets in einer Sprache vor, die dann in andere Sprachen für die Verwendung in mehrsprachigen Projekten übersetzt werden. Mit Adobe Experience Manager (AEM) Assets können Sie Übersetzungs-Workflows für Assets automatisieren (einschließlich Binärdateien, Metadaten und Tags), um Assets in anderen Sprachen für die Verwendung in mehrsprachigen Projekten zu generieren.

Um Übersetzungs-Workflows zu automatisieren, integrieren Sie Übersetzungsdienstleister mit AEM und erstellen Sie Projekte für die Übersetzung von Assets in mehrere Sprachen. AEM unterstützt Workflows für menschliche und maschinelle Übersetzungen.

Menschliche Übersetzung: Die übersetzten Assets werden zurückgegeben und in AEM importiert. Wenn Ihr Übersetzungsanbieter mit AEM integriert ist, werden die Assets automatisch zwischen AEM und dem Übersetzungsanbieter gesendet.

Maschinelle Übersetzung: Der Dienst für maschinelle Übersetzung übersetzt die Metadaten und Tags für Assets sofort.

<!--
We have multiple articles around translation of assets. For now, dumping all content in this article to remove others and create only 1 master article.

https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/translation-projects.html
https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/preparing-assets-for-translation.html
[Apply translation cloud services to folders](https://docs.adobe.com/content/help/en/experience-manager-65/assets/managing/transition-cloud-services.html)

One of these articles is a copy of [Preparing Content for Translation](https://docs.adobe.com/content/help/en/experience-manager-65/administering/introduction/tc-prep.html

-->

<!-- 
Translating assets includes the following:

1. [Connecting AEM with the translation service provider](/help/sites-administering/tc-tic.md#connecting-to-a-translation-service-provider)
1. [Creating translation integration framework configurations](/help/sites-administering/tc-tic.md)
1. [Preparing assets for translation](prepare-assets-for-translation.md)
1. [Applying translation cloud services to folders](transition-cloud-services.md)
1. [Create translation projects](translation-projects.md)

If your translation service provider does not provide a connector to integrate with AEM, use an [alternative process](/help/sites-administering/tc-manage.md#exporting-a-translation-job).

Also see, [Creating translation projects for content fragments](creating-translation-projects-for-content-fragments.md).

-->

## Vorbereiten von Assets für die Übersetzung {#prepare-assets-for-translation}

Bei mehrsprachigen Assets handelt es sich um Assets mit Binärdateien, Metadaten und Tags in verschiedenen Sprachen. Im Allgemeinen liegen Binärdateien, Metadaten und Tags für Assets in einer Sprache vor, die dann in andere Sprachen für die Verwendung in mehrsprachigen Projekten übersetzt werden.

In Adobe Experience Manager (AEM) Assets sind mehrsprachige Assets in Ordnern enthalten, wobei jeder Ordner die Assets in einer anderen Sprache enthält.

Jeder Sprachordner wird als eine Sprachkopie bezeichnet. Der Stammordner einer Sprachkopie, auch als Sprachstamm bezeichnet, identifiziert die Sprache des Inhalts in der Sprachkopie. For example, `/content/dam/it` is the Italian language root for the Italian language copy. Language copies must use a [correctly-configured language root](#create-a-language-root) so that the correct language is targeted when translations of source assets are performed.

Die Sprachkopie, für die Sie ursprünglich Assets hinzufügen, ist die Sprachmustervorlage. Die Sprachmustervorlage ist die Quelle, die in andere Sprachen übersetzt wird. Eine Beispielordnerhierarchie umfasst mehrere Sprachwurzeln:

```
/content
&nbsp; &nbsp; /- dam
&nbsp; &nbsp; &nbsp; |- en
&nbsp; &nbsp; &nbsp; |- fr
&nbsp; &nbsp; &nbsp; |- de
&nbsp; &nbsp; &nbsp; |- es
&nbsp; &nbsp; &nbsp; |- it
&nbsp; &nbsp; &nbsp; |- ja
&nbsp; &nbsp; &nbsp; |- zh
```

Führen Sie die folgenden Schritte aus, um Ihre Assets für die Übersetzung vorzubereiten:

1. Erstellen Sie den Sprachstamm für Ihren Sprach-Master. Beispielsweise ist der Sprachstamm der englischen Sprachkopie in der Beispielordnerhierarchie */content/dam/en*. Ensure that the language root is correctly configured according to the information in [Create a language root](#create-a-language-root).

1. Fügen Sie Assets zu Ihrer Sprachmustervorlage hinzu.
1. Erstellen Sie den Sprachstamm der jeweiligen Zielsprache, für die Sie eine Sprachkopie benötigen.

### Sprachstamm erstellen {#create-a-language-root}

Um den Sprachstamm zu erstellen, erstellen Sie einen Ordner und verwenden Sie einen ISO-Sprachcode als Wert für die Name-Eigenschaft. Nachdem Sie den Sprachstamm erstellt haben, können Sie eine Sprachkopie auf jeder beliebigen Ebene im Sprachstamm erstellen.

For example, the root page of the Italian language copy of the sample hierarchy has `it` as the Name property. Die Name-Eigenschaft wird als Name des Assetknotens im Repository verwendet und bestimmt daher den Pfad des Assets. (*&lt;server>:&lt;port>/assets.html/content/dam/it/*)

1. Klicken/tippen Sie in der Konsole „Assets“ auf **[!UICONTROL Erstellen]** und wählen Sie **[!UICONTROL Ordner]** aus dem Menü aus.
1. In the Name field type the country code in the format of `<language-code>`.
1. Klicken oder tippen Sie auf **[!UICONTROL Erstellen]**. Der Sprachstamm wird in der Konsole „Assets“ erstellt. 

### Anzeigen von Sprachwurzeln {#view-language-roots}

Die Touch-optimierte Benutzeroberfläche bietet einen Bereich „Verweise“, der eine Liste von Sprachstämmen anzeigt, die in AEM Assets erstellt wurden.

1. In der Konsole „Assets“ wählen Sie die Sprachmustervorlage aus, für die Sie Sprachkopien erstellen möchten.
1. Klicken oder tippen Sie auf das GlobalNav-Symbol und wählen Sie **[!UICONTROL Verweise]** aus, um den Bereich „Verweise“ zu öffnen.
1. Im Bereich „Verweise“ klicken oder tippen Sie auf **[!UICONTROL Sprachkopien]**. Der Bereich „Sprachkopien“ zeigt die Sprachkopien der Assets an.

### Neues Übersetzungsprojekt erstellen {#create-a-new-translation-project}

Wenn Sie diese Option verwenden, werden die zu übersetzenden Assets in den Sprachstamm der Sprache kopiert, in die übersetzt werden soll. Je nach gewählten Optionen wird ein Übersetzungsprojekt für die Assets in der Projektekonsole erstellt. Abhängig von den Einstellungen kann das Übersetzungsprojekt manuell gestartet oder automatisch ausgeführt werden, sobald es erstellt wird.

1. Wählen Sie in der Benutzeroberfläche von Assets den Ordner, für den Sie eine Sprachkopie erstellen möchten.
1. Wechseln Sie zum Bereich **[!UICONTROL Verweise]** und klicken/tippen Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**.
1. Click/tap **[!UICONTROL Create &amp; Translate]** at the bottom.
1. Wählen Sie aus der Liste **[!UICONTROL Zielsprachen]** die Sprache(n), für die Sie eine Ordnerstruktur erstellen möchten.
1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Neues Übersetzungsprojekt erstellen]**.
1. Geben Sie im Feld **[!UICONTROL Projekttitel]** einen Namen für das Projekt ein.
1. Klicken/tippen Sie auf **[!UICONTROL Erstellen]**. Assets aus dem Quellordner werden in die Zielordner für die Gebietsschemata kopiert, die Sie in Schritt 4 gewählt haben.
1. Um zum Ordner zu navigieren, wählen Sie die Sprachkopie und klicken Sie auf **[!UICONTROL In Assets einblenden]**.
1. Navigieren Sie zur Projektekonsole. Der Übersetzungsordner wird in die Projektekonsole kopiert.
1. Öffnen Sie den Ordner, um das Übersetzungsprojekt anzuzeigen.
1. Klicken/tippen Sie auf das Projekt, um die Seite mit den Details zu öffnen.
1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen. <!-- For more details around job statuses, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. Öffnen Sie in der Benutzeroberfläche &quot;Assets&quot;die Seite &quot;Eigenschaften&quot;für jedes der übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

>[!NOTE]
>
>Diese Funktion ist sowohl für Assets als auch für Ordner verfügbar. Wenn ein Asset anstelle eines Ordners ausgewählt wird, wird die gesamte Hierarchie von Ordnern bis zum Sprachstamm kopiert, um eine Sprachkopie für das Asset zu erstellen.

### Add to an existing translation project {#add-to-existing-translation-project}

Wenn Sie diese Option verwenden, wird der Übersetzungs-Workflow für Assets ausgeführt, die Sie zum Quellordner hinzufügen, nachdem bereits ein Übersetzungs-Workflow ausgeführt wurde. Nur die neu hinzugefügten Assets werden in den Zielordner kopiert, der zuvor übersetzte Assets enthält. In diesem Fall wird kein neues Übersetzungsprojekt erstellt.

1. Navigieren Sie in der Benutzeroberfläche „Assets“ zu dem Ordner, der nicht übersetzte Assets enthält.
1. Select an asset you want to translate, and open the **[!UICONTROL Reference pane]**. The **[!UICONTROL Language Copies]** section displays the number of translation copies that are currently available.
1. Click/tap **[!UICONTROL Language Copies]** under **[!UICONTROL Copies]**. Eine Liste der verfügbaren Übersetzungskopien wird angezeigt.
1. Click/tap **[!UICONTROL Create &amp; Translate]** at the bottom.
1. Wählen Sie aus der Liste **[!UICONTROL Zielsprachen]** die Sprache(n), für die Sie eine Ordnerstruktur erstellen möchten.
1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]**, um den Übersetzungs-Workflow für den Ordner auszuführen.
   >[!NOTE]
   >
   >Wenn Sie die Option **[!UICONTROL Zu vorhandenem Übersetzungsprojekt hinzufügen]** wählen, wird Ihr Übersetzungsprojekt zu einem vorhandenen Projekt hinzugefügt, sofern Ihre Projekteinstellungen genau den Einstellungen des bereits vorhandenen Projekts entsprechen. Anderenfalls wird ein neues Projekt erstellt.
1. Wählen Sie aus der Liste **[!UICONTROL Vorhandenes Übersetzungsprojekt]** ein Projekt, dem das zu übersetzende Asset hinzugefügt werden soll.
1. Klicken/tippen Sie auf **[!UICONTROL Erstellen]**. Die zu übersetzenden Assets werden zum Zielordner hinzugefügt. Der aktualisierte Ordner wird unter **[!UICONTROL Sprachkopien]** aufgeführt.
1. Navigieren Sie zur Projektkonsole und öffnen Sie das vorhandene Übersetzungsprojekt, dem Sie Assets hinzugefügt haben.
1. Klicken/tippen Sie auf das Übersetzungsprojekt, um die Seite mit den Projektdetails anzuzeigen.
1. Click/tap the ellipsis at the bottom of the **Translation Job** tile to view the assets in the translation workflow. In der Übersetzungsauftragsliste werden auch Einträge für Asset-Metadaten und -Tags aufgeführt. Diese Einträge geben an, dass die Metadaten und Tags für die Assets ebenfalls übersetzt werden.

   >[!NOTE]
   >
   >* Wenn Sie den Eintrag für Tags oder Metadaten löschen, werden keine Tags oder Metadaten für die Assets übersetzt.
   >* Wenn Sie die maschinelle Übersetzung verwenden, werden Asset-Binärdateien nicht übersetzt.
   >* Wenn das Asset, das Sie zum Übersetzungsauftrag hinzufügen, Teil-Assets enthält, wählen Sie die Teil-Assets und entfernen Sie sie, damit die Übersetzung fehlerfrei fortgesetzt werden kann.


1. To start the translation for the assets, click/tap the arrow on the **[!UICONTROL Translation Job]** tile and select **[!UICONTROL Start]** from the list. Eine Meldung informiert Sie darüber, dass mit der Ausführung des Übersetzungsauftrags begonnen wird.
1. Um den Status des Übersetzungsauftrags anzuzeigen, klicken/tippen Sie unten auf der Kachel **[!UICONTROL Übersetzungsauftrag]** auf das Auslassungszeichen. <!-- For more details, see [Monitoring the Status of a Translation Job](/help/sites-administering/tc-manage.md#monitoring-the-status-of-a-translation-job). -->
1. Nach Abschluss des Übersetzungsvorgangs ändert sich der Status in „Bereit für Überprüfung“. Navigieren Sie zur Benutzeroberfläche „Assets“ und öffnen Sie die Seite mit den Eigenschaften für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

### Sprachkopien aktualisieren {#update-language-copies}

Führen Sie diesen Workflow aus, um weitere Assets zu übersetzen und sie in eine Sprachkopie für ein bestimmtes Gebietsschema einzuschließen. In diesem Fall werden die übersetzten Assets zu dem Zielordner hinzugefügt, der bereits zuvor übersetzte Assets enthält. Abhängig von den gewählten Optionen wird ein Übersetzungsprojekt erstellt oder ein vorhandenes Übersetzungsprojekt für die neuen Assets aktualisiert. Der Workflow zum Aktualisieren der Sprachkopien umfasst die folgenden Optionen:

* Neues Übersetzungsprojekt erstellen
* Zu vorhandenem Übersetzungsprojekt hinzufügen

### Zu vorhandenem Übersetzungsprojekt hinzufügen {#add-to-existing-translation-project-1}

Wenn Sie diese Option verwenden, wird die Gruppe der Assets zu einem vorhandenen Übersetzungsprojekt hinzugefügt, um die Sprachkopien für das von Ihnen gewählte Gebietsschema zu aktualisieren.

1. Wählen Sie in der Benutzeroberfläche „Assets“ den Quellordner, dem Sie einen Asset-Ordner hinzugefügt haben.
1. Open the **[!UICONTROL References pane]**, and click/tap **[!UICONTROL Language Copies]** under **[!UICONTROL Copies]** to display the list of language copies.
1. Select the check box before **[!UICONTROL Language Copies]**, which selects all language copies. Heben Sie die Auswahl anderer Kopien auf. Nur die Sprachkopien, die den gewünschten Gebietsschemas entsprechen, sollten ausgewählt bleiben.
1. Klicken/tippen Sie am unteren Rand auf **[!UICONTROL Sprachkopien aktualisieren]**.
1. From the **[!UICONTROL Project]** list, choose **[!UICONTROL Add to existing translation project]**.
1. Wählen Sie aus der Liste **[!UICONTROL Vorhandenes Übersetzungsprojekt]** ein Projekt, dem das zu übersetzende Asset hinzugefügt werden soll.
1. Klicken/tippen Sie auf **[!UICONTROL Start]**.
1. See steps 9-14 of [Add to existing translation project](#add-to-existing-translation-project) to complete the rest of the procedure.

### Erstellen von temporären Sprachkopien {#creating-temporary-language-copies}

Wenn Sie einen Übersetzungs-Workflow ausführen, um eine Sprachkopie mit bearbeiteten Versionen der ursprünglichen Assets zu aktualisieren, wird die vorhandene Sprachkopie beibehalten, bis Sie die übersetzten Assets genehmigen. AEM Assets speichert die neu übersetzten Assets an einem temporären Speicherort und aktualisiert die vorhandene Sprachkopie, nachdem Sie die Assets genehmigt haben. Wenn Sie die Assets ablehnen, bleibt die Sprachkopie unverändert.

1. Click/tap the source root folder under **[!UICONTROL Language Copies]** for which you already created a language copy, and then click/tap **[!UICONTROL Reveal in Assets]** to open the folder in AEM Assets.
1. Wählen Sie in der Benutzeroberfläche von Assets ein bereits übersetztes Asset und tippen/klicken Sie in der Symbolleiste auf das Symbol **[!UICONTROL Bearbeiten]**, um das Asset im Bearbeitungsmodus zu öffnen.
1. Bearbeiten Sie das Asset und speichern Sie die Änderungen.
1. Perform steps 2-14 of the [Add to existing translation project](#add-to-existing-translation-project) procedure to update the language copy.
1. Click/tap the ellipsis at the bottom of the **[!UICONTROL Translation Job]** tile. Der Liste der Assets auf der Seite **[!UICONTROL Übersetzungsauftrag]** können Sie den temporären Speicherort der übersetzten Version des Assets entnehmen.
1. Aktivieren Sie das Kontrollkästchen neben **[!UICONTROL Titel]**.
1. From the toolbar, click/tap **[!UICONTROL Accept Translation]** and then click/tap **[!UICONTROL Accept]** in the dialog to overwrite the translated asset in the target folder with the translated version of the edited asset.

   >[!NOTE]
   >
   >Damit der Übersetzungs-Workflow die Ziel-Assets aktualisieren kann, akzeptieren Sie sowohl das Asset als auch die Metadaten.

   Click/tap **[!UICONTROL Reject Translation]** to retain the originally translated version of the asset in the target locale root and reject the edited version.

1. Navigieren Sie zur Assets-Konsole und öffnen Sie die Seite mit den Eigenschaften für die einzelnen übersetzten Assets, um die übersetzten Metadaten anzuzeigen.

For tips on translating metadata for assets efficiently, see [5 Steps to efficiently translate metadata](https://blogs.adobe.com/experiencedelivers/experience-management/translate_aemassets_metadata/).

## Erstellen von Übersetzungsprojekten{#creating-translation-projects} 

Lösen Sie zum Erstellen einer Sprachkopie einen der folgenden Sprachkopie-Workflows aus, die in der Benutzeroberfläche von Assets in der Leiste „Verweise“ verfügbar sind:

**Erstellen und übersetzen**

Bei diesem Workflow werden die zu übersetzenden Assets in den Sprachstamm der Sprache kopiert, in die übersetzt werden soll. Darüber hinaus wird je nach gewählten Optionen ein Übersetzungsprojekt für die Assets in der Projektekonsole erstellt. Je nach Einstellungen kann das Übersetzungsprojekt manuell gestartet oder automatisch ausgeführt werden, sobald es erstellt wurde.

**Sprachkopien aktualisieren**

Diesen Workflow führen Sie aus, um eine weitere Gruppe von Assets zu übersetzen und in eine Sprachkopie für ein bestimmtes Gebietsschema aufzunehmen. In diesem Fall werden die übersetzten Assets zu dem Zielordner hinzugefügt, der bereits zuvor übersetzte Assets enthält.

>[!NOTE]
>
>Asset-Binärdateien werden nur dann übersetzt, wenn der Übersetzungsanbieter die Übersetzung von Binärdaten unterstützt.

>[!NOTE]
>
>Wenn Sie einen Übersetzungsarbeitsablauf für komplexe Assets wie PDF-Dateien und Adobe InDesign-Dateien starten, werden deren Teilassets oder Darstellungen (sofern vorhanden) nicht zur Übersetzung gesendet.

### Workflow für das Erstellen und Übersetzen {#create-and-translate-workflow}

Sie verwenden den Arbeitsablauf zum Erstellen und Übersetzen, um zum ersten Mal Sprachkopien für eine bestimmte Sprache zu erstellen. Der Workflow bietet die folgenden Optionen:

* Nur Struktur erstellen
* Neues Übersetzungsprojekt erstellen
* Zu vorhandenem Übersetzungsprojekt hinzufügen

### Nur Struktur erstellen {#create-structure-only}

Use the **Create structure only** option to create a target folder hierarchy within the target language root to match the hierarchy of the source folder within the source language root. In diesem Fall werden die Quell-Assets in den Zielordner kopiert. Allerdings wird kein Übersetzungsprojekt erstellt.

1. Wählen Sie in der Benutzeroberfläche von Assets den Ordner, für den Sie eine Struktur im Zielsprachenstamm erstellen möchten.
1. Wechseln Sie zum Bereich **[!UICONTROL Verweise]** und klicken/tippen Sie unter **[!UICONTROL Kopien]** auf **[!UICONTROL Sprachkopien]**.
1. Click/tap **[!UICONTROL Create &amp; Translate]** at the bottom.
1. Wählen Sie aus der Liste **[!UICONTROL Zielsprachen]** die Sprache, für die Sie eine Ordnerstruktur erstellen möchten.
1. Wählen Sie aus der Liste **[!UICONTROL Projekt]** die Option **[!UICONTROL Nur Struktur erstellen]**.
1. Klicken/tippen Sie auf **[!UICONTROL Erstellen]**. The new structure for the target language is listed under **[!UICONTROL Language Copies]**.
1. Klicken/tippen Sie auf die Struktur aus der Liste und dann auf **[!UICONTROL In Assets einblenden]**, um zur Ordnerstruktur in der Zielsprache zu navigieren.

## Apply translation cloud services to folders {#applying-translation-cloud-services-to-folders}

Mit Adobe Experience Manager (AEM) können Sie von cloudbasierten Übersetzungsdiensten von Ihrem bevorzugten Übersetzungsanbieter Gebrauch machen, um sicherzustellen, dass Ihre Assets basierend auf Ihren Anforderungen übersetzt werden.

Sie können den Übersetzungs-Cloud-Service direkt auf Ihren Asset-Ordner anwenden, sodass die Assets in den Übersetzungs-Workflows verwendet werden können.

### Übersetzungsdienste anwenden {#applying-the-translation-services}

Durch die direkte Anwendung der Übersetzungs-Cloud-Services auf Ihren Assets-Folder entfällt die Notwendigkeit, Übersetzungsdienste zu konfigurieren, wenn Sie Übersetzungs-Workflows erstellen oder aktualisieren.

1. Wählen Sie in der Benutzeroberfläche &quot;Assets&quot;den Ordner aus, auf den Sie Übersetzungsdienste anwenden möchten.
1. Klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Eigenschaften]**, um die Seite **[!UICONTROL Ordnereigenschaften]** anzuzeigen.

   ![chlimage_1-215](assets/chlimage_1-215.png)

1. Navigieren Sie zur Registerkarte **[!UICONTROL Cloud-Services]**.
1. Wählen Sie in der Liste &quot;Cloud-Dienstkonfigurationen&quot;den gewünschten Übersetzungsanbieter aus. Wenn Sie beispielsweise Übersetzungsdienste von Microsoft nutzen möchten, wählen Sie **[!UICONTROL Microsoft Translator]** aus.

   ![chlimage_1-216](assets/chlimage_1-216.png)

1. Wählen Sie den Connector für den Übersetzungsanbieter aus.

   ![chlimage_1-217](assets/chlimage_1-217.png)

1. Klicken/tippen Sie in der Symbolleiste auf **[!UICONTROL Speichern]** und klicken Sie anschließend auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Der Übersetzungsdienst wird auf den Ordner angewendet.

### Benutzerdefinierten Übersetzungs-Connector anwenden {#applying-custom-translation-connector}

Wenn Sie einen benutzerdefinierten Connector für die Übersetzungs-Services anwenden möchten, die in Übersetzungs-Workflows verwendet werden sollen. Um einen benutzerdefinierten Connector anzuwenden, installieren Sie den Connector zunächst über Package Manager. Konfigurieren Sie den Connector anschließend über die Konsole „Cloud-Services“. Wenn Sie den Connector konfiguriert haben, ist er in der Connector-Liste in der Registerkarte „Cloud-Services“ verfügbar. Die Beschreibung hierzu finden Sie unter [Anwenden der Übersetzungsdienste](#applying-the-translation-services). Wenn Sie den benutzerdefinierten Connector anwenden und Übersetzungs-Workflows ausführen, werden die Connector-Details in der Kachel **[!UICONTROL Zusammenfassung der Übersetzung]** des Übersetzungsprojekts unter den Überschriften **[!UICONTROL Anbieter]** und **[!UICONTROL Methode]** angezeigt.

1. Installieren Sie den Connector von Package Manager.
1. Klicken oder tippen Sie auf das AEM-Logo und navigieren Sie zu **[!UICONTROL Tools > Bereitstellung > Cloud-Services]**.
1. Locate the connector you installed under **[!UICONTROL Third Party Services]** in the **[!UICONTROL Cloud Services]** page.

   ![chlimage_1-218](assets/chlimage_1-218.png)

1. Klicken/tippen Sie auf den Link **[!UICONTROL Jetzt konfigurieren]**, um das Dialogfeld **[!UICONTROL Konfiguration erstellen]** zu öffnen.

   ![chlimage_1-219](assets/chlimage_1-219.png)

1. Geben Sie einen Titel und einen Namen für den Connector ein und klicken/tippen Sie dann auf **[!UICONTROL Erstellen]**. The custom connector is available in the list of connectors in the **[!UICONTROL Cloud Services]** tab described in step 5 of [Applying the translation services](#applying-the-translation-services).
1. Führen Sie einen beliebigen Übersetzungs-Workflow aus, der in der Erstellung von Übersetzungsprojekten beschrieben wird, nachdem Sie den benutzerdefinierten Connector angewendet haben. Verify the details of the connector in the **[!UICONTROL Translation Summary]** tile of the translation project in the **[!UICONTROL Projects]** console.

   ![chlimage_1-220](assets/chlimage_1-220.png)
