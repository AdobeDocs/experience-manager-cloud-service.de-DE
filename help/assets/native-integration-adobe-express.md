---
title: Verwenden von Content Advisor für den Zugriff auf AEM Assets in Adobe Express
description: Verwenden Sie Content Advisor, um AEM Assets direkt in der nativen Adobe Express-Integration zu erkennen und darauf zuzugreifen.
exl-id: d43e4451-da2a-444d-9aa4-4282130ee44f
feature: Collaboration
role: User
source-git-commit: 6d80567106fe7c32d8073ca093f895ff28500413
workflow-type: tm+mt
source-wordcount: '2581'
ht-degree: 17%

---

# Verwenden von Content Advisor für den Zugriff auf AEM Assets in Adobe Express {#native-integration-adobe-express-using-content-advisor}

Adobe Experience Manager (AEM) Assets ist nativ in Adobe Express integriert, sodass Sie Assets aus AEM Assets direkt über die Express-Benutzeroberfläche mithilfe von Content Advisor identifizieren, darauf zugreifen und verwenden können.

Content Advisor verändert die Art und Weise, wie Sie Assets in Adobe Express erkennen und verwenden, indem die intelligente, kontextbezogene Asset-Erkennung direkt in Ihren Kreativ-Workflow integriert wird. Anstatt nach Assets zu suchen, indem Sie Keywords eingeben, zeigt Content Advisor relevante, genehmigte Assets basierend auf Ihrem Arbeitsflächen-Inhalt, Ihrer Kampagnenbeschreibung und dem Zweck an, sodass Sie das richtige Asset schneller finden können.

Mit intelligenten Vorschlägen, Zugriff auf Dynamic Media-Ausgabedarstellungen und vollständiger Sichtbarkeit der Asset-Metadaten ermöglicht Ihnen Content Advisor, Assets aus AEM Assets effizient zu finden, zu bewerten und zu verwenden, ohne Adobe Express verlassen zu müssen. Dies ermöglicht eine schnellere Inhaltserstellung, eine verbesserte Wiederverwendung von Assets und die konsistente Verwendung genehmigter, markenkonformer Assets.

![Content Advisor-Bannerbild](assets/content-advisor-banner-image.png)

Sie können Assets auch in der Express-Arbeitsfläche platzieren und neue oder bearbeitete Inhalte wieder in AEM Assets speichern, um eine zentralisierte Asset-Verwaltung und -Governance sicherzustellen. Die native Integration mit Adobe Express bietet die folgenden zentralen Vorteile:

* Beschleunigte Inhaltserstellung mit kontextabhängiger Asset-Erkennung und Empfehlungen.

* Verbesserte Wiederverwendung von Inhalten durch Bearbeiten vorhandener Assets und Speichern neuer Assets in AEM Assets.

* Schnellerer Zugriff auf genehmigte, kanaloptimierte Dynamic Media-Ausgabedarstellungen.

* Weniger Zeit- und Arbeitsaufwand für die Erstellung neuer Assets oder neuer Versionen bei gleichzeitiger Wahrung der Markenkonsistenz.

## Voraussetzungen {#prerequisites}

Es sind Berechtigungen für den Zugriff auf Adobe Express und mindestens eine Umgebung in AEM Assets erforderlich. Die Umgebung kann jedes der Assets as a Cloud Service-Repositorys sein.

## Verwenden von AEM Assets im Adobe Express-Editor {#use-aem-assets-in-express}

Führen Sie die folgenden Schritte aus, um mit der Verwendung von AEM Assets im Adobe Express-Editor zu beginnen:

1. Öffnen Sie die Adobe Express-Web-Anwendung.

2. Öffnen Sie eine neue leere Arbeitsfläche, indem Sie eine neue Vorlage oder ein Projekt laden oder ein Asset erstellen.

3. Klicken Sie im linken Navigationsbereich auf **[!UICONTROL Assets]**. Adobe Express zeigt [Content Advisor](#intelligent-asset-discovery-content-advisor) an, in dem die Repositorys, auf die Sie zugreifen dürfen, zusammen mit der Liste der auf der Stammebene verfügbaren Assets und Ordner aufgeführt sind.

4. Suchen Sie mit [Content Advisor) nach Assets im Repository &#x200B;](#intelligent-asset-discovery-content-advisor) ziehen Sie sie per Drag-and-Drop auf die Arbeitsfläche. Klicken Sie alternativ auf die Assets, um sie auf der Arbeitsfläche zu platzieren. Sie können ![&#x200B; Assets auch &#x200B;](assets/do-not-localize/filter.svg) verschiedenen Kriterien filtern (filtern), z. B. Genehmigungsstatus, Dateityp, MIME-Typ und Dimensionen.

   >[!NOTE]
   >
   >Das Filtern nach Dimension gilt nicht für Videos.

   ![Einschließen von Assets aus dem Assets-Add-on](assets/native-express-content-advisor-home.png)

## Intelligente Asset-Erkennung mit Content Advisor {#intelligent-asset-discovery-content-advisor}

Der Content Advisor hilft Ihnen, relevante Assets mithilfe intelligenter, kontextbezogener Empfehlungen zu finden, die auf Ihrem Canvas-Inhalt oder Ihrer Kampagnenbeschreibung basieren. Darüber hinaus können Sie kanalfertige Dynamic Media-Ausgabedarstellungen auswählen, die für Ihren Anwendungsfall optimiert sind.


Content Advisor zeigt die Liste der Dateien, Ordner und Sammlungen in Listen- und Rasteransichten an. Damit können Sie Assets im PNG-, JPEG-, PSD-, MP4-, SVG- und PDF-Format zur Express-Arbeitsfläche hinzufügen. Sie können auch eine Vorschau der scrollbaren PDF-Dateien oder anderer Formattypen anzeigen, indem Sie auf das Symbol ![Info](assets/info-icon.svg) klicken, das auf der Asset-Karte verfügbar ist.

Klicken Sie auf das Symbol ![Info](assets/info-icon.svg), um auch die Asset-Metadaten auf der Registerkarte **[!UICONTROL Allgemein]** oder die Dynamic Media-Ausgabedarstellungen auf der Registerkarte [Dynamic Media](#dynamic-media-renditions-content-advisor) anzuzeigen. Ziehen Sie den vorgeschlagenen Inhalt per Drag-and-Drop auf die Arbeitsfläche. Klicken Sie alternativ auf das Asset, um es automatisch auf der Arbeitsfläche zu platzieren.

![Asset-Metadaten in Adobe Express](assets/express-native-integration-metadata.png)


>[!IMPORTANT]
> 
>Stellen Sie sicher, dass Sie ein **author**-Repository aus der Dropdown-Liste **Repository** auswählen. Ein **delivery**-Repository zeigt keine Content Advisor-Funktionen an.
>
> Darüber hinaus sind im **delivery**-Repository keine Assets in Ordnern und Sammlungen organisiert. Alle Assets werden auf der Stammebene in einer flachen Struktur angezeigt.

Content Advisor bietet die folgenden zentralen Funktionen:

* [KI-Suchen für die intelligentere Asset-Erkennung](#content-advisor-ai-search)

* [Intelligente Vorschläge basierend auf Kontext und Absicht](#smart-suggestions-content-advisor)

* [Informationen zu Campaign, um relevante Assets zu finden](#campaign-briefs-content-advisor)

* [Für Dynamic Media verfügbare Asset-Ausgabedarstellungen](#dynamic-media-renditions-content-advisor)

* [Zugriff auf Asset-Metadaten in Übereinstimmung mit der Assets-Ansicht](#asset-metadata-content-advisor)

* [Zugriff auf Filter, die der Assets-Ansicht entsprechen](#filters-content-advisor)

* [Zugreifen auf und Wiederverwenden von zuletzt verwendeten und gespeicherten Suchvorgängen](#saved-searches-content-advisor)

* [Suchen nach Assets in und innerhalb von Sammlungen](#search-collections-content-advisor)

### KI-Suchen für die intelligentere Asset-Erkennung {#content-advisor-ai-search}

Content Advisor verwendet eine erweiterte Suchfunktion, die die Bedeutung und den Zweck hinter der Abfrage eines Benutzers versteht, anstatt sich auf exakte Keyword-Übereinstimmungen zu verlassen. Es nutzt künstliche Intelligenz (KI) und maschinelles Lernen, um genauere und kontextbezogene Ergebnisse zu liefern.

Im Gegensatz zur herkömmlichen schlüsselwortbasierten Suche, die nach exakten Begriffen sucht, interpretiert die KI-Suche die Beziehungen zwischen Wörtern, Konzepten und der Absicht der Benutzenden. Dadurch wird sichergestellt, dass Benutzende das Gesuchte finden – selbst wenn die Abfrage anders formuliert ist, Tippfehler enthält oder in einer anderen Sprache verfasst ist.

![KI-Suchen für Assets in Adobe Express](assets/express-native-integration-ai-search.png)

Zu den wichtigsten Vorteilen zählen:

* Mehrsprachige Unterstützung: Suchen Sie über mehrere Sprachen hinweg, ohne dass genaue Übersetzungen erforderlich sind. Benutzende können relevante Inhalte unabhängig von ihrer Abfragesprache finden.

* Verarbeitet Rechtschreibfehler: Interpretiert Tippfehler und Rechtschreibfehler, sodass auch bei unvollständiger Eingabe korrekte Ergebnisse erzielt werden.

* Versteht Synonyme: Liefert Ergebnisse für verwandte Begriffe und Ausdrücke, sodass Benutzende nicht das richtige Keyword erraten müssen.

* Kontextabhängige Suche: Erkennt den Zweck einer Abfrage, nicht nur die genauen Wörter.

>[!IMPORTANT]
> 
>* Die mindestens erforderliche AEM-Versionsversion für den Zugriff auf KI-Suchen in Content Advisor ist `21994`.


### Intelligente Vorschläge basierend auf Kontext und Absicht {#smart-suggestions-content-advisor}

Der Inhaltsratgeber zeigt intelligente Vorschläge basierend auf dem Kontext und der Absicht des Inhalts auf der Express-Arbeitsfläche an. So können Sie schnell Assets erkennen und verwenden, die Ihren Inhaltsanforderungen entsprechen, ohne die zeitaufwendige manuelle Suche durchführen zu müssen.

![Empfohlene Inhalte von Content Advisor in Adobe Express](assets/express-native-integration-suggested-content.png)

>[!IMPORTANT]
> 
>* Der Inhaltsratgeber zeigt intelligente Vorschläge basierend auf dem Kontext und der Absicht des Inhalts an, der in den Textebenen oder dem Titel auf der Express-Arbeitsfläche verfügbar ist. Es werden keine Ergebnisse basierend auf den auf der Arbeitsfläche verfügbaren Bildern angezeigt.
>* Sie müssen einen GenAI-Treiber signieren, um in Content Advisor auf diese Funktion zugreifen zu können. Um GenAI Rider zu unterzeichnen, kontaktieren Sie Ihren Adobe-Support-Mitarbeiter.
>* Die mindestens erforderliche AEM-Release-Version für den Zugriff auf diese Funktion ist `21994`.
>* Intelligente Vorschläge werden beim Aktualisieren der Arbeitsfläche nicht automatisch aktualisiert. Klicken Sie im Bedienfeld **Vorgeschlagener Inhalt** auf das Aktualisierungssymbol, um die aktualisierte Liste der Vorschläge anzuzeigen,

### Informationen zu Campaign, um relevante Assets zu finden {#campaign-briefs-content-advisor}

Mit Content Advisor können Sie ein Kampagnenübersichtsdokument hochladen, um relevante Assets zu ermitteln, ohne Suchbegriffe manuell eingeben zu müssen. Der Content Advisor analysiert die Informationen in der Kampagnenbeschreibung, um die Kampagnenzielsetzung zu verstehen, und empfiehlt relevante Assets, die in AEM Assets verfügbar sind.

![Einschließen von Assets aus dem Assets-Add-on](assets/upload-brief-native-express.png)

>[!IMPORTANT]
>
>* Content Advisor analysiert die Informationen, die als Text in der Kampagnenbeschreibung verfügbar sind, um relevante Assets zu empfehlen. Die Informationen, die als Bilder in der Kampagnenbeschreibung verfügbar sind, werden nicht analysiert.
>* Zu den unterstützten Dateitypen, die Sie als Kampagnenübersicht hochladen können, gehören PDF-, DOCX- und TXT-Dokumente.
>* Sie müssen einen GenAI-Treiber signieren, um in Content Advisor auf diese Funktion zugreifen zu können. Um GenAI Rider zu unterzeichnen, kontaktieren Sie Ihren Adobe-Support-Mitarbeiter.
>* Die mindestens erforderliche AEM-Release-Version für den Zugriff auf diese Funktion ist `21994`.

### Für Dynamic Media verfügbare Asset-Ausgabedarstellungen {#dynamic-media-renditions-content-advisor}

Dynamic Media-Ausgabedarstellungen bieten einsatzbereite, kanaloptimierte Versionen von Assets, einschließlich [Bildvorgaben](/help/assets/dynamic-media/managing-image-presets.md), [Smartes Zuschneiden](/help/assets/dynamic-media/image-profiles.md), Formattypen und Farbprofilen. Mit diesen Ausgabedarstellungen können Sie sicherstellen, dass das ausgewählte Asset den Kanal- und Design-Anforderungen entspricht, ohne dass eine manuelle Bearbeitung oder Duplizierung des Assets erforderlich ist.

Sie können Dynamic Media-Modifikatoren auch anwenden, um Anpassungen in Echtzeit anzuzeigen, bevor Sie die Ausgabedarstellung auf der Express-Arbeitsfläche platzieren. So können Sie die am besten geeignete Ausgabedarstellung schneller auswählen und gleichzeitig die Konsistenz und Qualität des Assets beibehalten.

Klicken Sie auf das Symbol ![Info](assets/info-icon.svg) auf der Asset-Karte und wählen Sie die Registerkarte **[!UICONTROL Dynamic Media]** aus, um die verfügbaren Ausgabedarstellungen für ein Asset anzuzeigen. Sie können die Ausgabedarstellungen [Dynamic Media Scene7) oder &#x200B;](/help/assets/dynamic-media/dynamic-media.md)Dynamic Media mit [OpenAPI) &#x200B;](/help/assets/dynamic-media-open-apis-overview.md). Wenn Sie **[!UICONTROL OpenAPI]** für ein Asset auswählen, werden die verfügbaren Ausgabedarstellungen nur angezeigt, wenn das Asset genehmigt wurde und für Dynamic Media mit OpenAPI verfügbar ist.

Sie müssen über eine gültige AEM Dynamic Media-Lizenz verfügen, um die Registerkarte „Dynamic Media“ anzeigen zu können.

![Anzeigen von Dynamic Media-Ausgabedarstellungen](assets/native-express-dynamic-media.png)

Klicken Sie auf das ![Vorschausymbol](assets/do-not-localize/preview-icon.svg), um eine Vorschau der Ausgabedarstellung anzuzeigen, oder klicken Sie auf den Namen der Ausgabedarstellung, um sie automatisch auf der Arbeitsfläche zu platzieren. Sie können auch eine Vorschau der Ausgabedarstellung anzeigen und sie dann per Drag-and-Drop verschieben, um das Bild auf der Arbeitsfläche zu platzieren.

![Vorschau von Dynamic Media-Ausgabedarstellungen](assets/native-express-dynamic-media-preview.png)

Klicken Sie auf **[!UICONTROL Modifikatoren hinzufügen]**, geben Sie einen Modifikator im Textfeld an und drücken Sie die Eingabetaste , um die Umwandlung in Echtzeit auf die Ausgabedarstellungen anzuwenden. Ebenso können Sie einer Ausgabedarstellung mehrere Modifikatoren hinzufügen und eine Vorschau dieser Umwandlungen anzeigen. Ziehen Sie das Asset aus der Vorschau auf die Arbeitsfläche. Die Ausgabedarstellung nach Anwendung dieser Modifikatoren wird nicht gespeichert. Eine Liste der unterstützten Modifikatoren für [Dynamic Media Scene7](https://experienceleague.adobe.com/de/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/c-command-reference) und [Dynamic Media mit OpenAPI](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat) finden Sie.

>[!IMPORTANT]
> 
>Mit Dynamic Media können Sie die Größenbeschränkung von 80 MB für Upload-Dateien in Adobe Express (Web) überwinden, indem Sie optimierte Ausgabedarstellungen großer Assets bereitstellen. Dynamic Media-Ausgabedarstellungen reduzieren die Dateigröße erheblich und behalten gleichzeitig die visuelle Qualität bei. Beispielsweise kann ein TIFF-Asset mit 300 MB ohne Qualitätseinbußen als Ausgabedarstellung mit 2,5 MB bereitgestellt werden, was eine effiziente Verwendung hochauflösender Assets in Adobe Express ermöglicht.

### Zugriff auf Asset-Metadaten in Übereinstimmung mit der Assets-Ansicht {#asset-metadata-content-advisor}

Der Content Advisor bietet Zugriff auf Asset-Eigenschaften, die in AEM Assets definiert sind, einschließlich der in der Assets-Ansicht verfügbaren Metadaten. Content Advisor verwendet dieselbe Metadatenkonfiguration wie in der Assets-Ansicht und repliziert so die Liste der Metadaten-Registerkarten und Inhalte auf der Detailseite für Assets-Asset anzeigen . Auf diese Weise können Sie wichtige Asset-Details wie Titel, Beschreibung, Format, Größe und andere Metadaten überprüfen, bevor Sie ein Asset auswählen. Durch den Zugriff auf Asset-Eigenschaften können Sie sicherstellen, dass Sie das richtige und genehmigte Asset für Ihren Inhalt auswählen.

![Assets-Metadaten in Content Advisor anzeigen](assets/native-express-asset-metadata.png)

Klicken Sie auf das Symbol ![Info](assets/info-icon.svg) auf der Asset-Karte und wählen Sie die Registerkarte **[!UICONTROL Standard]** aus, um die Asset-Metadaten anzuzeigen. Sie können auch andere Asset-Metadaten-Registerkarten wie Produkt, Kampagne und Tags anzeigen, die mit den Asset-Metadaten in der Assets-Ansicht konsistent sind.

Content Advisor zeigt Eigenschaften (Metadaten) für Dateien in einer schreibgeschützten Ansicht an. Die Eigenschaften werden für Sammlungen und Ordner nicht angezeigt.

### Zugriff auf Filter, die der Assets-Ansicht entsprechen {#filters-content-advisor}

Content Advisor bietet dieselben Filterfunktionen in Express, die auch in der Assets-Ansicht verfügbar sind, sodass Sie Assets mithilfe vordefinierter Filter einschränken können. Die gleichen Filterfunktionen, die in der Assets-Ansicht verfügbar sind, gelten auch für die Filter, die speziell für Inhaltstypen wie Dateien, Ordner und Sammlungen gelten. Dadurch wird ein konsistentes Asset-Erkennungserlebnis sichergestellt und die effiziente Suche nach relevanten Assets in Adobe Express unterstützt.

Wenn Sie in der Assets-Ansicht keine Filter über das Filterschema eingerichtet haben, zeigt Content Advisor vordefinierte Filter an, darunter Dateityp, Dateiformat, Asset-Status, Dateigröße, Bildbreite, Bildhöhe, Änderungsdatum und Erstellungsdatum.

### Zugreifen auf und Wiederverwenden von zuletzt verwendeten und gespeicherten Suchvorgängen {#saved-searches-content-advisor}

Gespeicherte Suchvorgänge, die in der Assets-Ansicht erstellt wurden, sind ebenfalls verfügbar, sodass Sie vordefinierte Suchkriterien wiederverwenden können. Gespeicherte Suchen funktionieren browserübergreifend konsistent zwischen Assets-Ansicht und Inhaltsratgeber. Dies hilft Ihnen bei der effizienten Suche nach Assets mithilfe von konsistenten Suchmustern in AEM Assets und Adobe Express.

So speichern Sie Ihre häufig verwendete Suche mit Content Advisor:

1. Geben Sie einen Suchbegriff an (optional), klicken Sie auf das Symbol Filter und wählen Sie die Optionen entsprechend Ihren Anforderungen aus, um eine Suchabfrage zu erstellen.

1. Klicken Sie **[!UICONTROL Anwenden]** um die Ergebnisse anzuzeigen.

1. Klicken Sie auf das Symbol Filter > **Gespeicherte Suchen verwalten** > **Neue gespeicherte Suche erstellen**.

1. Geben Sie den Namen der Suche an und klicken Sie auf ![Infosymbol](assets/do-not-localize/checkmark-icon.svg), um sie zu speichern. Die Suche wird in der Liste der Elemente angezeigt.

   ![Gespeicherte Suchen - Inhaltsratgeber](assets/native-express-saved-searches.png)

Um eines der gespeicherten Suchelemente anzuwenden, klicken Sie auf das Symbol Filter , wählen Sie das Suchelement aus der Dropdown-Liste **[!UICONTROL Gespeicherte Suchen]** und klicken Sie auf **[!UICONTROL Anwenden]**.

Der Content Advisor speichert Ihre letzten Suchvorgänge und ermöglicht Ihnen auch, häufig verwendete Suchvorgänge für den späteren Schnellzugriff zu speichern. Die Liste der letzten Suchvorgänge ist zwischen der Assets-Ansicht und dem Inhaltsratgeber nicht konsistent. Derselbe Benutzer kann in der Ansicht &quot;Assets&quot; und im Inhaltsratgeber über verschiedene kürzlich durchgeführte Suchvorgänge verfügen. Wenn Sie den Inkognito-Modus verwenden, um auf den Inhaltsratgeber zuzugreifen, ist die Liste der letzten Suchvorgänge nicht verfügbar. Außerdem werden aktuelle Suchvorgänge nicht in verschiedenen Browsern für denselben Benutzer freigegeben und sind AEM-umgebungsspezifisch.



Die in der Assets-Ansicht verfügbare Standardfunktion für die Suche nach gespeicherten Daten ist noch nicht in Content Advisor verfügbar.

### Suchen nach Assets in und innerhalb von Sammlungen {#search-collections-content-advisor}

Mit Content Advisor können Sie über alle Sammlungen hinweg nach Assets oder Sammlungen suchen oder Ihre Suche auf eine bestimmte Sammlung beschränken. Auf diese Weise können Sie Assets aus kuratierten Sammlungen schnell finden und verwenden und gleichzeitig den beabsichtigten Organisationskontext beibehalten.

## Ersetzen des Bildes mithilfe des AEM-Uploads {#replace-image-using-aem-upload}

Darüber hinaus können Sie die hinzugefügten Bilder mithilfe von **[!UICONTROL AEM Upload]** ersetzen. Führen Sie dazu die folgenden Schritte aus:

1. Durchsuchen oder suchen von Assets und Ziehen und Ablegen auf der Arbeitsfläche.

1. Wählen Sie das Bild aus, das Sie ersetzen möchten. Klicken Sie **[!UICONTROL Ersetzen]** und wählen Sie **[!UICONTROL AEM Assets]** unter verschiedenen anderen Optionen aus.

   ![AEM ersetzen](assets/aem-replace.png)

1. [Content Advisor](#intelligent-asset-discovery-content-advisor) wird im linken Navigationsbereich geöffnet. Adobe Express zeigt die Liste der Repositorys an, auf die Sie zugreifen dürfen, sowie die Liste der Assets und Ordner, die auf der Stammebene verfügbar sind. Wählen Sie dort ein Asset aus, um eine Vorschau der Ersetzung auf der Arbeitsfläche anzuzeigen, und klicken Sie dann zur Bestätigung **[!UICONTROL Ersetzen]**.

   >[!NOTE]
   >
   > SVG-Dateitypen werden nicht unterstützt.

## Speichern von Adobe Express-Projekten in AEM Assets {#save-express-projects-in-assets}

Nachdem Sie entsprechende Änderungen in die Express-Arbeitsfläche eingefügt haben, können Sie sie in AEM Assets speichern.

1. Klicken Sie auf **[!UICONTROL Freigeben]**, um das Dialogfeld **[!UICONTROL Freigeben]** zu öffnen.

   ![Speichern von Assets in AEM](assets/adobe-express-share.png)

2. **AEM Assets**. Adobe Express zeigt das Dialogfeld „Hochladen“ an.

3. Wählen Sie entweder **Aktuelle Seite** oder **Alle Seiten** aus. Geben Sie einen Namen und ein Format für die Assets an, die exportiert werden sollen. Sie können die Inhalte der Arbeitsfläche in die folgenden Formate exportieren: PNG, JPEG, PDF, MP4, MP4+PNG oder MP4+JPEG. Das Format passt sich basierend auf den Assets automatisch an die Seite(n) der Arbeitsfläche an.
Durch Auswahl von **Aktuelle Seite** wird das Asset auf Ihrer aktuellen Seite in Ihrem Zielordner gespeichert. Wenn Sie **Alle Seiten** auswählen und das Exportformat nicht „PDF“ lautet, werden alle Seiten der Arbeitsfläche als separate Dateien in einem neuen Ordner in Ihrem Zielordner gespeichert. Wenn das Exportformat „PDF“ lautet, werden alle Seiten der Arbeitsfläche als eine einzige PDF-Datei im Zielordner gespeichert.

4. Klicken Sie auf das Ordnersymbol unter „**Zielordner**“, um einen Speicherort auszuwählen und die Assets zu speichern.

   ![Speichern von Assets in AEM](/help/assets/assets/page-selection-and-destination-folder.png)

5. Optional: Sie können mit dem Feld **Projekt- oder Kampagnenname** Kampagnen-Metadaten für Ihren Upload hinzufügen. Sie können einen vorhandenen Namen verwenden oder einen neuen erstellen. Sie können mehrere Projekt- oder Kampagnennamen für Ihren Upload definieren. Geben Sie zum Registrieren des Namens einfach den Namen ein und drücken Sie die Eingabetaste.
Adobe empfiehlt als Best Practice, in den restlichen Feldern Werte anzugeben sowie ein verbessertes Sucherlebnis für Ihre hochgeladenen Assets zu schaffen.

6. Definieren Sie auf ähnliche Weise Werte für die Felder **[!UICONTROL Keywords]** und **[!UICONTROL Kanäle]**.

7. Klicken Sie auf **[!UICONTROL Hochladen]**, um die Assets in AEM Assets hochzuladen.

   >[!NOTE]
   >
   > Wenn Sie Asset(s) im Content Hub-Versand-Repository speichern, ist der Projekt- oder Kampagnenname ein Pflichtfeld. Sie müssen in diesem Fall auch keinen Zielordner auswählen, da er automatisch aus Metadaten abgeleitet wird.

## Unterstützte Dateiformate {#supported-file-formats-import-assets}

Adobe Express unterstützt nativ die Formate unter [Überprüfen der Mindestanforderungen an das Bild](https://helpx.adobe.com/express/web/image-creation-and-editing/change-file-formats/image-requirements.html). AEM Assets unterstützt jedoch die folgenden Formattypen:

| Unterstütztes Format | Max. Abmessungen/Auflösung | Maximale Dateigröße |
|------------------|---------------------------------------------|---------------|
| JPEG | 65 MP (z. B. 8K × 8K oder 16K × 4K) | 80 MB Desktop, 40 MB Mobile |
| PNG | 65 MP (z. B. 8K × 8K oder 16K × 4K) | 80 MB Desktop, 40 MB Mobile |
| SVG | — | 250 KB |
| MP4 | 3840 × 3840 Pixel | 200 MB |
| PSD | 65 MP (z. B. 8K × 8K oder 16K × 4K) | 80 MB Desktop, 40 MB Mobile |
| PDF | — | — |


## Einschränkungen {#limitations}

1. Für den Import und Export wird MP4 als Videodateityp unterstützt.

2. Beim **MP4-Videoimport** werden Videos mit transparentem Hintergrund (Alphakanal) nicht unterstützt.
   <!--
   1. The maximum file size supported is 200 MB. If this limit exceeds, an alert message displays.
   2. The maximum supported resolution is 3840 X 3840 pixels.
   3. Videos with transparent backgrounds (alpha channel) are not supported.
   -->

3. Beim **MP4-Videoexport** wird eine Dateigröße von maximal 200 MB unterstützt. Bei Überschreiten dieses Grenzwerts wird ein Warnhinweis angezeigt, das Video auf 200 MB oder weniger zu reduzieren oder es nach dem Herunterladen manuell in den Zielordner in AEM Assets hochzuladen.

<!--
## Content Advisor Properties {#content-advisor-props}

You can configure following properties for the content advisor:

* `featureSet` : This property enables the Content Advisor MFE.

    ```
    featureSet: [
        ...defaultFeatures, /* to include all default features */
        'advisor', /* enables Content Advisor features */
        'content-fragments', /* enables Content Fragments */
    ],
    ```

* `rail:true/false` : If marked true, Content Advisor is rendered in a left rail view. If it is marked false, the Content Advisor is rendered in modal view.

## Browse assets using Content Advisor {#browse-assets-content-advisor}

<!--In the Modal View of Content Advisor, you can access both [Assets](#using-assets-tab) and [Content Fragments](#using-content-fragments) within a unified interface.

### Assets tab{#assets-tab}

The **[!UICONTROL Assets]** tab allows you to browse or filter available assets, preview them before selection, and choose appropriate **[!UICONTROL Dynamic Media]** [renditions](renditions.md) or [smart crops](/help/assets/dynamic-media/image-profiles.md#creating-image-profiles) as needed. Assets, folders, and collections are presented together in a single, streamlined experience. The interface also provides contextual recommendations based on the integrated application context, helping you quickly identify relevant content.

Within assets tab, you can access content by browsing [Files and folders](#content-advisor-files-and-folders) or viewing [Collections](#content-advisor-collections).

### Files and Folders tab{#content-advisor-files-and-folders}

Browsing content using Files and Folders allows you navigate your assets in a familiar hierarchical structure, making it easy to locate assets within the repository. To browse assets within files and folders, navigate to the **[!UICONTROL Assets]** tab and select **[!UICONTROL Files & Folders]**. A hierarchical structure is then displayed, allowing you to easily locate and select the desired assets.

![Browse assets using files and folder](assets/browse-assets-content-advisor.png)

### Collections tab{#content-advisor-collections}

Browsing content using Collections allows you to access curated groups of assets within Collections. To browse assets within Collections, navigate to the **[!UICONTROL Assets]** tab and select **[!UICONTROL Collections]**. The interface then displays curated groups of assets, enabling you to browse the content you need.

![Browse assets using Collections](assets/browse-assets-collections.png)

<!--
### Content Fragments tab{#content-fragments}

The [Content Fragments](/help/assets/content-fragments/content-fragments.md) tab displays structured assets, allowing you to browse, search, and filter fragments efficiently within the same interface. To browse assets using Content Fragments, navigate to the **[!UICONTROL Content Fragments]** tab to access and explore the fragments available in the repository.

![Browse assets using Content Fragments](assets/browse-assets-content-fragment.png)
-->


