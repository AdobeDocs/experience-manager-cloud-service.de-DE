---
title: Taggen Sie Bilder mit künstlich intelligenten Diensten.
description: Taggen Sie Bilder mit künstlich intelligenten Diensten, die kontextbezogene und beschreibende Geschäftstags mit Adobe Sensei-Diensten anwenden.
contentOwner: AG
translation-type: tm+mt
source-git-commit: bf7bb91dd488f39181a08adc592971d6314817de
workflow-type: tm+mt
source-wordcount: '2398'
ht-degree: 35%

---


# Taggen Sie Ihre Bilder mit intelligenten Diensten. {#smart-tag-assets}

Organisationen, die mit digitalen Assets arbeiten, verwenden zunehmend ein taxonomiegesteuertes Vokabular in Asset-Metadaten. Es enthält im Wesentlichen eine Liste von Suchbegriffen, die Mitarbeiter, Partner und Kunden häufig verwenden, um auf ihre digitalen Assets zu verweisen und nach ihnen zu suchen. Durch das Taggen von Assets mit einem taxonomisch gesteuerten Vokabular wird sichergestellt, dass die Assets durch tag-basierte Suchen leicht identifiziert und abgerufen werden können.

Verglichen mit den natürlichen Sprachvokabularen hilft das Tagging auf der Grundlage der Geschäftstaxonomie, die Assets an das Geschäft einer Firma anzupassen und sicherzustellen, dass die relevantesten Assets in Suchvorgängen angezeigt werden. Beispielsweise kann ein Automobilhersteller Autobilder mit Modellnamen markieren, sodass nur relevante Kampagnen angezeigt werden, wenn nach einer Promotion gesucht wird.

In the background, the Smart Tags uses an artificial intelligence framework of [Adobe Sensei](https://www.adobe.com/de/sensei/experience-cloud-artificial-intelligence.html) to train its image recognition algorithm on your tag structure and business taxonomy. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden.

<!-- TBD: Create a similar flowchart for how training works in CS.
![flowchart](assets/flowchart.gif) 
-->

Führen Sie die folgenden Aufgaben aus, um intelligentes Tagging zu verwenden:

* [Integration von Experience Manager mit Adobe I/O](#integrate-aem-with-aio).
* [Verstehen Sie Tag-Modelle und Richtlinien](#understand-tag-models-guidelines).
* [Zug das Modell](#train-model).
* [Taggen Sie Ihre digitalen Assets](#tag-assets).
* [Verwalten Sie die Tags und Suchen](#manage-smart-tags-and-searches).

Intelligente Tags gelten nur für [!DNL Adobe Experience Manager Assets] Kunden. The Smart Tags is available for purchase as an add-on to [!DNL Experience Manager].

<!-- TBD: Is there a link to buy SCS or initiate a sales call. How are AIO services sold? -->

## Integration [!DNL Experience Manager] mit Adobe I/O {#integrate-aem-with-aio}

You can integrate [!DNL Adobe Experience Manager] with the Smart Tags using Adobe I/O. Use this configuration to access the Smart Tags service from within [!DNL Experience Manager].

Aufgaben zum Konfigurieren der intelligenten Tags finden Sie unter Experience Manager für intelligentes Tagging von Assets [](smart-tags-configuration.md) konfigurieren. At the back end, the [!DNL Experience Manager] server authenticates your service credentials with the Adobe I/O gateway before forwarding your request to the Smart Tags service.

## Verstehen Sie Tag-Modelle und -Richtlinien. {#understand-tag-models-guidelines}

Ein Tag-Modell ist eine Gruppe verwandter Tags, die von einem visuellen Aspekt des Bildes stammen. Eine Schuhsammlung kann beispielsweise unterschiedliche Tags haben, aber alle Tags beziehen sich auf Schuhe und können zum gleichen Tag-Modell gehören. Tags können sich nur auf die deutlich unterschiedlichen visuellen Aspekte von Bildern beziehen. Um die Darstellung des Inhalts eines Schulungsmodells in zu verstehen, [!DNL Experience Manager]stellen Sie sich ein Schulungsmodell als Entität auf oberster Ebene vor, die aus einer Gruppe manuell hinzugefügter Tags und Beispielbildern für jedes Tag besteht. Jedes Tag kann ausschließlich auf ein Bild angewendet werden.

Tags, die realistischerweise nicht verarbeitet werden können, beziehen sich auf:

* Nicht visuelle, abstrakte Aspekte wie das Jahr oder die Saison der Veröffentlichung eines Produkts, Stimmung oder Emotion, die durch ein Bild ausgelöst wird.
* Bildende visuelle Unterschiede in Produkten wie Hemden mit und ohne Halterungen oder kleine Produktlogos, die in Produkten eingebettet sind.

Bevor Sie ein Tag-Modell erstellen und den Dienst schulen, müssen Sie einen Satz eindeutiger Tags identifizieren, die die Objekte in den Bildern im Kontext Ihres Unternehmens am besten beschreiben. Ensure that the assets in your curated set conform to [the training guidelines](#training-guidelines).

### Ausbildungsleitlinien {#training-guidelines}

Die Bilder in Ihrem Schulungsset sollten den folgenden Richtlinien entsprechen:

**Menge und Größe:** Mindestens 10 Bilder und höchstens 50 Bilder pro Tag.

**Kohärenz**: Bilder für ein Tag sollten visuell ähnlich sein. Es empfiehlt sich, die Tags zu denselben visuellen Aspekten (z. B. zum gleichen Objekttyp in einem Bild) zu einem einzelnen Tag-Modell zusammenzufügen. So ist es beispielsweise nicht empfehlenswert, all diese Bilder mit dem Tag `my-party` zu versehen (zu Trainingszwecken), da sie einander visuell nicht ähnlich sind.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/coherence.png)

**Abdeckung:** Bei den Trainings-Bildern muss eine ausreichende Vielfalt vorhanden sein. Der Grundgedanke ist, einige Beispiele bereitzustellen, die jedoch verhältnismäßig vielfältig sind, sodass AEM lernt, sich auf die richtigen Dinge zu konzentrieren. Wenn Sie dasselbe Tag auf visuell unähnliche Bilder anwenden, schließen Sie mindestens fünf Beispiele für jeden Typ ein. Beispiel: Schließen Sie für das Tag *model-down-pose* mehr Trainingsbilder ein, die dem hervorgehobenen Bild unten ähnlich sind, sodass der Dienst ähnliche Bilder beim Hinzufügen von Tags genauer identifizieren kann.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/coverage_1.png)

**Ablenkung/Verdeckung**: Der Dienst kann besser mit Bildern trainieren, die weniger Ablenkungen enthalten (hervorgehobenen Hintergründe oder Elemente ohne Bezug wie Objekte/Personen neben dem Hauptsubjekt). Beispiel: Für das Tag *casual-shoe* ist das zweite Bild kein guter Kandidat für das Training.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/distraction.png)

**Vollständigkeit:** Wenn ein Bild für mehr als ein Tag qualifiziert ist, fügen Sie alle entsprechenden Tags hinzu, bevor Sie das Bild für eine Schulung hinzufügen. Fügen Sie beispielsweise für Tags wie *Regenmantel* und *Modell-Seitenansicht* beide Tags für das entsprechende Asset hinzu, bevor Sie es für die Schulung hinzufügen.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/completeness.png)

**Anzahl der Tags**: Adobe empfiehlt, dass Sie ein Modell mit mindestens zwei verschiedenen Tags und mindestens 10 verschiedenen Bildern für jedes Tag ausbilden. Fügen Sie in einem einzelnen Tag-Modell nicht mehr als 50 Tags hinzu.

**Anzahl der Beispiele**: Fügen Sie für jedes Tag mindestens 10 Beispiele hinzu. Adobe empfiehlt jedoch etwa 30 Beispiele. Es werden maximal 50 Beispiele pro Tag unterstützt.

**Vermeidung falscher Positivwerte und Konflikte**: Adobe empfiehlt die Erstellung eines einzelnen Tag-Modells für einen einzelnen visuellen Aspekt. Strukturieren Sie die Tag-Modelle so, dass sich überschneidende Tags zwischen den Modellen vermieden werden. Verwenden Sie beispielsweise keine gemeinsamen Tags wie `sneakers` in zwei verschiedenen Tag-Modellnamen `shoes` und `footwear`. Der Schulungsprozess überschreibt ein ausgebildetes Tag-Modell mit dem anderen für einen allgemeinen Suchbegriff.

**Beispiele**: Weitere Beispiele:

* Erstellen Sie ein Tag-Modell, das
   * nur die Tags, die sich auf Automodelle beziehen.
   * nur die Tags, die sich auf die Farben von Hemden beziehen.
   * nur die Tags, die sich auf Jackets für Frauen und Männer beziehen.
* Erstellen Sie nicht,
   * ein Tag-Modell, das in den Jahren 2019 und 2020 veröffentlichte Automodelle enthält.
   * mehrere Tag-Modelle, die die gleichen Automodelle enthalten.

**Für die Schulung** verwendete Bilder: Sie können dieselben Bilder verwenden, um verschiedene Tag-Modelle zu schulen. Sie können jedoch kein Bild mit mehr als einem Tag in einem Tag-Modell verknüpfen. Daher ist es möglich, das gleiche Bild mit verschiedenen Tags zu versehen, die zu verschiedenen Tag-Modellen gehören.

Sie können die Schulung nicht rückgängig machen. Die obigen Richtlinien sollten Ihnen helfen, gute Bilder zu trainieren.

## Erstellen Sie das Modell für Ihre benutzerdefinierten Tags. {#train-model}

Gehen Sie wie folgt vor, um ein Modell für Ihre unternehmensspezifischen Tags zu erstellen und auszubilden:

1. Erstellen Sie die erforderlichen Tags und die entsprechende Tag-Struktur. Laden Sie die entsprechenden Bilder in das DAM-Repository hoch.
1. Rufen Sie in der [!DNL Experience Manager] Benutzeroberfläche **[!UICONTROL Assets]** > **[!UICONTROL Schulungsmodell]** auf.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Geben Sie einen **[!UICONTROL Titel]**, eine **[!UICONTROL Beschreibung]** ein.
1. Suchen Sie die Tags der vorhandenen Tags, für die Sie das Modell trainieren möchten, und wählen Sie sie aus `cq:tags` diesen aus. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Klicken Sie im Dialogfeld &quot;Assets **[!UICONTROL auswählen]** &quot;auf **[!UICONTROL Hinzufügen Assets]** für jedes Tag. Suchen Sie im DAM-Repository oder durchsuchen Sie das Repository, um mindestens 10 und höchstens 50 Bilder auszuwählen. Wählen Sie Assets und nicht den Ordner aus. Klicken Sie nach Auswahl der Bilder auf **[!UICONTROL Auswählen]**.
1. Um die Miniaturansichten der ausgewählten Bilder Vorschau, klicken Sie auf das Akkordeon vor dem Tag. Sie können Ihre Auswahl ändern, indem Sie auf **[!UICONTROL Hinzufügen Assets]** klicken. Wenn Sie mit der Auswahl zufrieden sind, klicken Sie auf **[!UICONTROL Senden]**. Die Benutzeroberfläche zeigt eine Benachrichtigung am unteren Rand der Seite an, dass die Schulung initiiert wird.
1. Überprüfen Sie den Status der Schulung in der Spalte **[!UICONTROL Status]** für jedes Tag-Modell. Mögliche Status sind [!UICONTROL Ausstehend], [!UICONTROL Fortgebildet]und [!UICONTROL Fehlgeschlagen].

![Arbeitsablauf zur Schulung des Tagging-Modells für intelligente Tags](assets/smart-tag-model-training-flow.png)

*Abbildung: Schritte des Schulungsarbeitsablaufs zur Schulung des Tagging-Modells.*

### Ausbildungsstatus und Bericht der Ansicht {#training-status}

Um zu überprüfen, ob der Smart-Tags-Dienst für Ihre Tags im Schulungssatz von Assets geschult ist, überprüfen Sie den Bericht zum Schulungsarbeitsablauf in der Konsole &quot;Berichte&quot;.

1. Gehen Sie in der [!DNL Experience Manager] Benutzeroberfläche zu **[!UICONTROL Werkzeuge > Assets > Berichte]**.
1. In the **[!UICONTROL Asset Reports]** page, click **[!UICONTROL Create]**.
1. Select the **[!UICONTROL Smart Tags Training]** report, and then click **[!UICONTROL Next]** from the toolbar.
1. Geben Sie einen Titel und eine Beschreibung für den Bericht an. Lassen Sie unter **[!UICONTROL Berichtplanen]** die Option **[!UICONTROL Jetzt]** aktiviert. Wenn Sie den Bericht für einen späteren Zeitpunkt planen möchten, wählen Sie **[!UICONTROL Später]** und geben Sie ein Datum und eine Uhrzeit an. Then, click **[!UICONTROL Create]** from the toolbar.
1. Wählen Sie auf der Seite **[!UICONTROL Asset-Berichte]** den erstellten Bericht aus. To view the report, click **[!UICONTROL View]** from the toolbar.
1. Prüfen Sie die Details des Berichts. Der Bericht zeigt den Trainingsstatus der von Ihnen trainierten Tags an. The green color in the **[!UICONTROL Training Status]** column indicates that the Smart Tags service is trained for the tag. Gelb bedeutet, dass der Service für ein bestimmtes Tag nicht vollständig trainiert ist. Fügen Sie in diesem Fall weitere Bilder mit dem jeweiligen Tag hinzu und führen Sie den Trainings-Workflow aus, um den Service vollständig für das Tag zu trainieren. Wenn Ihre Tags in diesem Bericht nicht angezeigt werden, führen Sie den Schulungsarbeitsablauf für diese Tags erneut aus.Tags
1. To download the report, select it from the list, and click **[!UICONTROL Download]** from the toolbar. Der Bericht wird als Microsoft Excel-Tabelle heruntergeladen.

## Taggen von Assets {#tag-assets}

Nachdem Sie den Smart-Tags-Dienst trainiert haben, können Sie den Tag-Arbeitsablauf auslösen, um automatisch geeignete Tags auf einen anderen Satz ähnlicher Assets anzuwenden. Sie können den Tag-Arbeitsablauf regelmäßig oder bei Bedarf anwenden. Der Tag-Arbeitsablauf gilt sowohl für Assets als auch für Ordner.

### Tag assets from the workflow console {#tagging-assets-from-the-workflow-console}

1. Gehen Sie in der Experience Manager-Oberfläche zu **[!UICONTROL Werkzeuge > Workflow > Modelle]**.
1. From the **[!UICONTROL Workflow Models]** page, select the **[!UICONTROL DAM Smart Tags Assets]** workflow and then click **[!UICONTROL Start Workflow]** from the toolbar.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. In the **[!UICONTROL Run Workflow]** dialog, browse to the payload folder containing assets on which you want to apply your tags automatically.
1. Geben Sie einen Titel für den Workflow und optional einen Kommentar an. Klicken Sie auf **[!UICONTROL Ausführen]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Navigieren Sie zum Asset-Ordner und überprüfen Sie die Tags, um zu überprüfen, ob Ihre Assets ordnungsgemäß getaggt wurden. For details, see [manage smart tags](#manage-smart-tags-and-searches).

### Tag assets from the timeline {#tagging-assets-from-the-timeline}

1. Wählen Sie über die Assets-Benutzeroberfläche den Ordner mit Assets bzw. bestimmte Assets aus, auf die Sie Smart-Tags anwenden möchten.
1. Öffnen Sie in der oberen linken Ecke die **[!UICONTROL Zeitleiste]**.
1. Öffnen Sie Aktionen unten in der linken Seitenleiste und klicken Sie auf **[!UICONTROL Beginn-Workflow]**.

   ![Beginn_workflow](assets/start_workflow.png)

1. Wählen Sie den Workflow **[!UICONTROL DAM Smart-Tag-Assets]** aus und geben Sie einen Titel für den Workflow an.
1. Klicken Sie auf **[!UICONTROL Starten]**. Der Workflow wendet Ihre Tags auf Assets an. Navigieren Sie zum Asset-Ordner und überprüfen Sie die Tags, um zu überprüfen, ob Ihre Assets ordnungsgemäß getaggt wurden. For details, see [manage smart tags](#manage-smart-tags-and-searches).

>[!NOTE]
>
>In den nachfolgenden Tagging-Zyklen werden nur die geänderten Assets erneut mit neu geschulten Tags versehen. Selbst nicht veränderte Assets werden mit Tags versehen, wenn die Lücke zwischen der letzten und der aktuellen Tagging-Phase für den Tag-Arbeitsablauf 24 Stunden überschreitet. Beim regelmäßigen Tagging Workflows werden unveränderte Assets mit Tags versehen, wenn die Zeitspanne 6 Monate überschreitet.

### Hochgeladene Assets taggen {#tag-uploaded-assets}

Experience Manager kann die Assets, die Benutzer in DAM hochladen, automatisch mit Tags versehen. Zu diesem Zweck konfigurieren Administratoren einen Workflow, um Smart-Tag-Assets einen verfügbaren Schritt hinzuzufügen. Erfahren Sie, [wie Sie intelligentes Tagging für hochgeladene Assets](/help/assets/smart-tags-configuration.md#enable-smart-tagging-for-uploaded-assets)aktivieren.

## Manage smart tags and image searches {#manage-smart-tags-and-searches}

Sie können Smart-Tags kuratieren, um ungenaue Tags zu entfernen, die möglicherweise Ihren Markenbildern zugewiesen wurden, sodass nur die relevantesten Tags angezeigt werden.

Mithilfe der Moderation von Smart-Tags können Sie Tag-basierte Suchen nach Bildern verfeinern, indem Sie sicherstellen, dass Ihr Bild nur in den Suchergebnissen für die relevantesten Tags angezeigt wird. Im Grunde wird so ausgeschlossen, dass in den Suchergebnissen Bilder ohne Bezug angezeigt werden.

Darüber hinaus können Sie Tags einen höheren Rang zuweisen, um ihre Relevanz in Bezug auf ein Bild zu erhöhen. Je höher der Rang eines Tags für ein Bild, desto wahrscheinlicher ist bei einer Tag-basierten Suche die Aufnahme des Bildes in die Suchergebnisse.

1. Suchen Sie im OmniSearch-Feld nach Assets, die auf einem Tag basieren.
1. Prüfen Sie die Suchergebnisse auf Bilder, die Ihnen für Ihren Suchvorgang nicht relevant erscheinen.
1. Select the image, and then click the **[!UICONTROL Manage Tags]** icon from the toolbar.
1. Prüfen Sie die Tags auf der Seite **[!UICONTROL Tags verwalten]**. Wenn das Bild nicht anhand eines bestimmten Tags durchsucht werden soll, wählen Sie das Tag aus und klicken Sie dann in der Symbolleiste auf das Symbol zum Löschen. Alternatively, click `X` symbol that appears beside the label.
1. Um einem Tag einen höheren Rang zuzuweisen, wählen Sie das Tag aus und klicken Sie in der Symbolleiste auf das Symbol &quot;bewerben&quot;. Das höhergestufte Tag wird in den Abschnitt **[!UICONTROL Tags]** verschoben.
1. Click **[!UICONTROL Save]**, and then click **[!UICONTROL OK]** to close the Success dialog.
1. Navigieren Sie zur Seite „Eigenschaften“ des betreffenden Bildes. Beachten Sie, dass das beworbene Tag eine hohe Relevanz erhält und es aus diesem Grund höher in den Suchergebnissen angezeigt wird.

### AEM-Suchergebnisse mit Smart-Tags   {#understandsearch}

Die AEM-Suche kombiniert die Suchbegriffe standardmäßig mit einer `AND`-Klausel. Dieses Standardverhalten ändert sich durch die Verwendung von Smart-Tags nicht. Durch die Verwendung von Smart-Tags wird eine zusätzliche `OR`-Klausel hinzugefügt. Damit wird jeder Suchbegriff aus den angewandten Smart-Tags gefunden. Suchen Sie beispielsweise nach `woman running`. Assets, die in den Metadaten nur das Schlüsselwort `woman`oder `running` aufweisen, werden standardmäßig nicht in den Suchergebnissen angezeigt. Ein Asset, das über Smart-Tags mit `woman` oder `running` getaggt wurde, wird bei dieser Suchanfrage jedoch angezeigt. Die Suchergebnisse sind also eine Kombination aus

* Assets mit den Keywords `woman` und `running` in den Metadaten.

* Assets, die über Smart-Tags mit einem der Schlüsselwörter getaggt wurden.

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. Treffer von `woman running` in den verschiedenen Metadatenfeldern.
1. Treffer von `woman running` in den Smart-Tags,
1. Treffer von `woman` oder `running` in Smart-Tags.

### Einschränkungen bei Tags {#limitations}

Optimierte Smart-Tags basieren auf Lernmodellen von Markenbildern und den zugehörigen Tags. Diese Modelle können Tags nicht immer perfekt identifizieren. Die aktuelle Version der intelligenten Tags unterliegt folgenden Einschränkungen:

* Subtile Unterschiede in Bildern können nicht erkannt werden. Zum Beispiel schlanke im Vergleich zu normal montierten Hemden.
* Tags können nicht anhand von winzigen Mustern/Teilen eines Bildes identifiziert werden. Beispiel: Logos auf T-Shirts.
* Tagging wird in den Sprachen unterstützt, in denen AEM unterstützt wird. For a list of languages, see [Smart Tags release notes](https://docs.adobe.com/content/help/en/experience-manager-64/release-notes/smart-content-service-release-notes.html).

Verwenden Sie zum Suchen nach Assets mit Smart-Tags (regulär oder erweitert) die Assets-Omniture-Suche (Volltextsuche). Es gibt kein separates Suchprädikat für Smart-Tags.

>[!NOTE]
>
>Die Fähigkeit der Smart-Tags, Ihre Tags zu trainieren und sie auf andere Bilder anzuwenden, hängt von der Qualität der Bilder ab, die Sie für die Schulung verwenden.
>Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe die Verwendung visuell ähnlicher Bilder, um den Dienst für die einzelnen Tags zu trainieren.

>[!MORELIKETHIS]
>
>* [Experience Manager für intelligentes Tagging konfigurieren](smart-tags-configuration.md)
>* [Erkennen, wie intelligente Tags die Verwaltung von Assets unterstützen](https://medium.com/adobetech/efficient-asset-management-with-enhanced-smart-tags-887bd47dbb3f)

