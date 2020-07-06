---
title: Tagging von Bildern mithilfe von KI-Diensten.
description: Tagging von Bildern mithilfe von KI-Diensten, die kontextbezogene und beschreibende Unternehmens-Tags mithilfe von Adobe Sensei-Diensten anwenden.
contentOwner: AG
translation-type: ht
source-git-commit: cc24b16cf17f146e773e7974c649adae1bd10ddf
workflow-type: ht
source-wordcount: '2401'
ht-degree: 100%

---


# Trainieren des Smart-Tag-Service und Tagging von Bildern {#train-service-tag-assets}

Organisationen, die mit digitalen Assets arbeiten, verwenden zunehmend taxonomiegesteuertes Vokabular in Asset-Metadaten. Im Grunde umfasst dieses eine Liste von Keywords, die Mitarbeiter, Partner und Kunden häufig verwenden, um sich auf digitale Assets zu beziehen und nach diesen zu suchen. Das Tagging mit einem taxonomiegesteuerten Vokabular stellt sicher, dass die Assets im Rahmen von Tag-basierten Suchen einfach identifiziert und abgerufen werden können.

Verglichen mit dem Vokabular natürlicher Sprachen hilft das Tagging anhand einer Unternehmenstaxonomie dabei, die Assets am Geschäft eines Unternehmens auszurichten, und stellt dabei sicher, dass nur die relevantesten Assets bei der Suche angezeigt werden. So könnte beispielsweise ein Automobilhersteller für das Erstellen einer Werbekampagne Bilder von Autos mit Tags versehen, die die Modellnamen darstellen, sodass bei einer Suche nur relevante Bilder angezeigt werden.

Im Hintergrund verwenden Smart-Tags ein KI-Framework von [Adobe Sensei](https://www.adobe.com/de/sensei/experience-cloud-artificial-intelligence.html), um den Bilderkennungsalgorithmus auf Ihre Tag-Struktur und Ihre Unternehmenstaxonomie zu trainieren. Diese Content-Intelligenz wird dann verwendet, um relevante Tags auf einen anderen Satz von Assets anzuwenden.

<!-- TBD: Create a similar flowchart for how training works in CS.
![flowchart](assets/flowchart.gif) 
-->

Führen Sie die folgenden Aufgaben aus, um Smart-Tagging zu verwenden:

* [Integrieren von Experience Manager mit der Adobe Developer Console](#integrate-aem-with-aio).
* [Grundlegendes zu Tag-Modellen und Richtlinien](#understand-tag-models-guidelines).
* [Trainieren der Modelle](#train-model)
* [Tagging digitaler Assets](#tag-assets)
* [Verwalten von Tags und Suchvorgängen](#manage-smart-tags-and-searches)

Smart-Tags sind nur für [!DNL Adobe Experience Manager Assets]-Kunden relevant. Die Smart-Tag-Funktion kann als Add-on zu [!DNL Experience Manager] erworben werden.

<!-- TBD: Is there a link to buy SCS or initiate a sales call. How are AIO services sold? -->

## Integrieren von [!DNL Experience Manager] mit der Adobe Developer Console {#integrate-aem-with-aio}

Sie können [!DNL Adobe Experience Manager] mithilfe der Adobe Developer Console mit Smart Tags integrieren. Verwenden Sie diese Konfiguration, um über [!DNL Experience Manager] auf den Smart-Tags-Service zuzugreifen. 

Informationen zu den Aufgaben zum Konfigurieren von Smart-Tags finden Sie unter [Konfigurieren von Experience Manager für das Smart-Tagging von Assets](smart-tags-configuration.md). Im Backend authentifiziert der [!DNL Experience Manager]-Server Ihre Service-Anmeldedaten mit dem Gateway der Adobe Developer Console, bevor Ihre Anfrage an den Smart-Tags-Service weitergeleitet wird.

## Grundlegendes zu Tag-Modellen und Richtlinien {#understand-tag-models-guidelines}

Ein Tag-Modell ist eine Gruppe verwandter Tags, die sich auf einen visuellen Aspekt des Bildes beziehen. Beispielsweise kann eine Schuhkollektion unterschiedliche Tags haben, aber alle Tags beziehen sich auf Schuhe und können zum selben Tag-Modell gehören. Tags können sich nur auf deutlich unterschiedliche visuelle Aspekte von Bildern beziehen. Um die inhaltliche Darstellung eines Trainings-Modells in [!DNL Experience Manager] zu verstehen, stellen Sie sich ein Trainings-Modell als eine Entität der obersten Ebene vor, die aus einer Gruppe manuell hinzugefügter Tags und Beispielbildern für jedes Tag besteht. Jedes Tag kann ausschließlich auf ein Bild angewendet werden.

Tags, die realistisch nicht gehandhabt werden können, beziehen sich auf:

* Nicht visuelle, abstrakte Aspekte wie das Jahr oder die Jahreszeit der Veröffentlichung eines Produkts, die Stimmung oder die Emotionen, die durch ein Bild hervorgerufen werden.
* Feine visuelle Unterschiede bei Produkten wie Hemden mit und ohne Kragen oder kleinen Produktlogos, die in Produkte eingebettet sind.

Bevor Sie ein Tag-Modell erstellen und den Service trainieren, identifizieren Sie einen Satz eindeutiger Tags, die die Objekte in den Bildern im Kontext Ihres Unternehmens am besten beschreiben. Stellen Sie sicher, dass die Assets in Ihrem Satz den [Trainings-Richtlinien](#training-guidelines) entsprechen.

### Trainings-Richtlinien {#training-guidelines}

Die Bilder im Trainings-Satz sollten folgende Richtlinien einhalten:

**Menge und Größe:** Mindestens 10 Bilder und maximal 50 Bilder pro Tag.

**Kohärenz**: Bilder für ein Tag sollten visuell ähnlich sein. Es ist am besten, die Tags zu denselben visuellen Aspekten (z. B. demselben Objekttyp in einem Bild) zu einem einzigen Tag-Modell zusammenzufassen. So ist es beispielsweise nicht empfehlenswert, all diese Bilder mit dem Tag `my-party` zu versehen (zu Trainings-Zwecken), da sie einander visuell nicht ähnlich sind.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/coherence.png)

**Abdeckung:** Bei den Trainings-Bildern muss eine ausreichende Vielfalt vorhanden sein. Der Grundgedanke ist, einige Beispiele bereitzustellen, die jedoch verhältnismäßig vielfältig sind, sodass AEM lernt, sich auf die richtigen Dinge zu konzentrieren. Wenn Sie dasselbe Tag auf visuell unähnliche Bilder anwenden, schließen Sie mindestens fünf Beispiele für jeden Typ ein. Beispiel: Schließen Sie für das Tag *model-down-pose* mehr Trainings-Bilder ein, die dem hervorgehobenen Bild unten ähnlich sind, sodass der Dienst ähnliche Bilder beim Hinzufügen von Tags genauer identifizieren kann.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/coverage_1.png)

**Ablenkung/Verdeckung**: Der Service kann besser mit Bildern trainieren, die weniger Ablenkungen enthalten (hervorgehobenen Hintergründe oder Elemente ohne Bezug wie Objekte/Personen neben dem Hauptsubjekt). Beispiel: Für das Tag *casual-shoe* ist das zweite Bild kein guter Kandidat für das Training.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/distraction.png)

**Vollständigkeit:** Wenn ein Bild für mehr als ein Tag qualifiziert ist, fügen Sie alle entsprechenden Tags hinzu, bevor Sie das Bild für eine Schulung hinzufügen. Fügen Sie beispielsweise für Tags wie *Regenmantel* und *Modell-Seitenansicht* beide Tags für das entsprechende Asset hinzu, bevor Sie es für die Schulung hinzufügen.

![Veranschaulichende Bilder als Beispiele für die Richtlinien für das Training](assets/do-not-localize/completeness.png)

**Anzahl der Tags**: Adobe empfiehlt, dass Sie ein Modell mit mindestens zwei verschiedenen Tags und mindestens 10 verschiedenen Bildern für jedes Tag trainieren. Fügen Sie in einem einzelnen Tag-Modell nicht mehr als 50 Tags hinzu.

**Anzahl der Beispiele**: Fügen Sie für jedes Tag mindestens 10 Beispiele hinzu. Adobe empfiehlt jedoch etwa 30 Beispiele. Es werden maximal 50 Beispiele pro Tag unterstützt.

**Vermeidung falscher positiver Werte und von Konflikte**: Adobe empfiehlt die Erstellung eines einzelnen Tag-Modells für einen einzelnen visuellen Aspekt. Strukturieren Sie die Tag-Modelle so, dass überlappende Tags zwischen den Modellen vermieden werden. Verwenden Sie beispielsweise keine gemeinsamen Tags wie `sneakers` in zwei verschiedenen Tag-Modellen, die `shoes` und `footwear` heißen. Der Trainings-Prozess überschreibt ein trainiertes Tag-Modell mit dem anderen für ein gemeinsames Keyword.

**Beispiele**: Weitere Beispiele zur Orientierung:

* Erstellen Sie ein Tag-Modell, das Folgendes umfasst:
   * nur die Tags, die sich auf Automodelle beziehen.
   * nur die Tags, die sich auf die Farben von Hemden beziehen.
   * nur die Tags, die sich auf Jacken für Frauen und Männer beziehen.
* Erstellen Sie nicht Folgendes:
   * ein Tag-Modell, das in den Jahren 2019 und 2020 auf den Markt gekommene Automodelle enthält.
   * mehrere Tag-Modelle, die dieselben Automodelle enthalten.

**Zum Trainieren verwendete Bilder**: Sie können dieselben Bilder zum Trainieren verschiedener Tag-Modelle verwenden. Sie können jedoch kein Bild mit mehr als einem Tag in einem Tag-Modell verknüpfen. Daher ist es möglich, dasselbe Bild mit verschiedenen Tags zu versehen, die zu verschiedenen Tag-Modellen gehören.

Sie können das Training nicht rückgängig machen. Die obigen Richtlinien sollen Ihnen bei der Auswahl guter Bilder für das Training helfen.

## Trainieren des Modelle für Ihre benutzerdefinierten Tags {#train-model}

Gehen Sie folgendermaßen vor, um ein Modell für Ihre geschäftsspezifischen Tags zu erstellen und zu trainieren:

1. Erstellen Sie die erforderlichen Tags und die entsprechende Tag-Struktur. Laden Sie die entsprechenden Bilder in das DAM-Repository hoch.
1. Rufen Sie in der [!DNL Experience Manager]-Benutzeroberfläche **[!UICONTROL Assets]** > **[!UICONTROL Smart-Tag-Training]** auf.
1. Klicken Sie auf **[!UICONTROL Erstellen]**. Geben Sie einen **[!UICONTROL Titel]** und eine **[!UICONTROL Beschreibung]** ein.
1. Durchsuchen und wählen Sie die Tags aus den vorhandenen Tags in `cq:tags` aus, für die Sie das Modell trainieren möchten. Klicken Sie auf **[!UICONTROL Weiter]**.
1. Klicken Sie im Dialogfeld **[!UICONTROL Assets auswählen]** für jedes Tag auf **[!UICONTROL Assets hinzufügen]**. Suchen Sie im DAM-Repository oder durchsuchen Sie das Repository, um mindestens 10 und höchstens 50 Bilder auszuwählen. Wählen Sie Assets und nicht den Ordner aus. Klicken Sie nach Auswahl der Bilder auf **[!UICONTROL Auswählen]**.
1. Um eine Vorschau der Miniaturansichten der ausgewählten Bilder anzuzeigen, klicken Sie auf das Akkordeon vor einem Tag. Sie können Ihre Auswahl ändern, indem Sie auf **[!UICONTROL Assets hinzufügen]** klicken. Wenn Sie mit der Auswahl zufrieden sind, klicken Sie auf **[!UICONTROL Senden]**. Die Benutzeroberfläche zeigt unten auf der Seite eine Benachrichtigung an, die angibt, dass das Training gestartet wurde.
1. Überprüfen Sie den Status des Trainings in der Spalte **[!UICONTROL Status]** für jedes Tag-Modell. Mögliche Status sind [!UICONTROL Ausstehend], [!UICONTROL Trainiert] und [!UICONTROL Fehlgeschlagen].

![Workflow zum Trainieren von Tagging-Modellen für das Smart-Tagging](assets/smart-tag-model-training-flow.png)

*Abbildung: Schritte des Trainings-Workflows zum Trainieren des Tagging-Modells.*

### Anzeigen von Trainings-Status und -Bericht {#training-status}

Um sicherzustellen, dass der Smart-Tags-Service mit Ihren Tags im Asset-Trainings-Satz trainiert wurde, überprüfen Sie den Bericht zum Trainings-Workflow über die Berichte-Konsole.

1. Gehen Sie in der [!DNL Experience Manager]-Benutzeroberfläche zu **[!UICONTROL Tools > Assets > Berichte]**.
1. Klicken Sie auf der Seite **[!UICONTROL Asset-Berichte]** auf **[!UICONTROL Erstellen]**.
1. Wählen Sie den Bericht **[!UICONTROL Smart-Tags-Training]** aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Weiter]**.
1. Geben Sie einen Titel und eine Beschreibung für den Bericht an. Lassen Sie unter **[!UICONTROL Berichtplanen]** die Option **[!UICONTROL Jetzt]** aktiviert. Wenn Sie den Bericht für einen späteren Zeitpunkt planen möchten, wählen Sie **[!UICONTROL Später]** und geben Sie ein Datum und eine Uhrzeit an. Klicken Sie dann in der Symbolleiste auf **[!UICONTROL Erstellen]**.
1. Wählen Sie auf der Seite **[!UICONTROL Asset-Berichte]** den erstellten Bericht aus. Um den Bericht anzuzeigen, klicken Sie in der Symbolleiste auf **[!UICONTROL Ansicht]**.
1. Prüfen Sie die Details des Berichts. Der Bericht zeigt den Trainings-Status der von Ihnen trainierten Tags an. Grün gibt in der Spalte **[!UICONTROL Trainings-Status]** an, dass der Smart-Tages-Service für das Tag trainiert wurde. Gelb bedeutet, dass der Service für ein bestimmtes Tag nicht vollständig trainiert ist. Fügen Sie in diesem Fall weitere Bilder mit dem jeweiligen Tag hinzu und führen Sie den Trainings-Workflow aus, um den Service vollständig für das Tag zu trainieren. Wenn Ihre Tags nicht im Bericht angezeigt werden, führen Sie den Trainings-Workflow für diese Tags erneut aus.
1. Um den Bericht herunterzuladen, wählen Sie ihn aus der Liste aus und klicken Sie in der Symbolleiste auf **[!UICONTROL Herunterladen]**. Der Bericht wird als Microsoft Excel-Tabellenkalkulation heruntergeladen.

## Tagging von Assets {#tag-assets}

Wenn Sie den Smart-Tags-Service trainiert haben, können Sie den Tagging-Workflow starten, um automatisch passende Tags auf einen anderen Satz ähnlicher Assets anzuwenden. Sie können den Tagging-Workflow periodisch oder nur bei Bedarf ausführen. Der Tagging-Workflow wird sowohl für Assets als auch für Ordner ausgeführt.

### Tagging von Assets über die Workflow-Konsole {#tagging-assets-from-the-workflow-console}

1. Gehen Sie in der Experience Manager-Benutzeroberfläche zu **[!UICONTROL Tools > Workflow > Modelle]**.
1. Wählen Sie auf der Seite **[!UICONTROL Workflow-Modelle]** den Workflow **[!UICONTROL DAM Smart Tags Assets]** aus und klicken Sie dann in der Symbolleiste auf **[!UICONTROL Workflow starten]**.

   ![dam_smart_tag_workflow](assets/dam_smart_tag_workflow.png)

1. Suchen Sie im Dialogfeld **[!UICONTROL Workflow ausführen]** den Payload-Ordner mit den Assets, auf die Sie automatisch Tags anwenden möchten.
1. Geben Sie einen Titel für den Workflow und optional einen Kommentar an. Klicken Sie auf **[!UICONTROL Ausführen]**.

   ![tagging_dialog](assets/tagging_dialog.png)

   Navigieren Sie zum Asset-Ordner und prüfen Sie die Tags, um sicherzustellen, dass Ihre Assets ordnungsgemäß mit Tags versehen sind. Weitere Informationen finden Sie unter [Verwalten von Smart-Tags](#manage-smart-tags-and-searches).

### Tagging von Assets über die Timeline {#tagging-assets-from-the-timeline}

1. Wählen Sie über die Assets-Benutzeroberfläche den Ordner mit Assets bzw. bestimmte Assets aus, auf die Sie Smart-Tags anwenden möchten.
1. Öffnen Sie die **[!UICONTROL Timeline]** oben links.
1. Öffnen Sie die Aktionen unten in der linken Seitenleiste und klicken Sie auf **[!UICONTROL Workflow starten]**.

   ![start_workflow](assets/start_workflow.png)

1. Wählen Sie den Workflow **[!UICONTROL DAM Smart-Tag-Assets]** aus und geben Sie einen Titel für den Workflow an.
1. Klicken Sie auf **[!UICONTROL Starten]**. Der Workflow wendet Ihre Tags auf Assets an. Navigieren Sie zum Asset-Ordner und prüfen Sie die Tags, um sicherzustellen, dass Ihre Assets ordnungsgemäß mit Tags versehen sind. Weitere Informationen finden Sie unter [Verwalten von Smart-Tags](#manage-smart-tags-and-searches).

>[!NOTE]
>
>In den nachfolgenden Tagging-Zyklen werden nur die geänderten Assets erneut mit neu trainierten Tags markiert. Selbst unveränderte Assets werden jedoch markiert, wenn das Intervall zwischen dem letzten und dem aktuellen Tagging-Zyklus des Tagging-Workflows 24 Stunden überschreitet. Bei periodischen Tagging-Workflows werden unveränderte Assets mit Tags versehen, wenn das Intervall 6 Monate überschreitet.

### Tagging hochgeladener Assets {#tag-uploaded-assets}

Experience Manager kann die Assets, die Benutzer in DAM hochladen, automatisch mit Tags versehen. Zu diesem Zweck konfigurieren Administratoren einen Workflow, um einen Schritt hinzuzufügen, um die Assets mit Smart-Tags zu versehen. Erfahren Sie, [wie Sie Smart-Tagging für hochgeladene Assets aktivieren](/help/assets/smart-tags-configuration.md#enable-smart-tagging-for-uploaded-assets).

## Verwalten von Smart-Tags und Bildsuchvorgängen {#manage-smart-tags-and-searches}

Sie können Smart-Tags kuratieren, um ungenaue Tags zu entfernen, die möglicherweise Ihren Markenbildern zugewiesen wurden, sodass nur die relevantesten Tags angezeigt werden.

Mithilfe der Moderation von Smart-Tags können Sie Tag-basierte Suchen nach Bildern verfeinern, indem Sie sicherstellen, dass Ihr Bild nur in den Suchergebnissen für die relevantesten Tags angezeigt wird. Im Grunde wird so ausgeschlossen, dass in den Suchergebnissen Bilder ohne Bezug angezeigt werden.

Darüber hinaus können Sie Tags einen höheren Rang zuweisen, um ihre Relevanz in Bezug auf ein Bild zu erhöhen. Je höher der Rang eines Tags für ein Bild, desto wahrscheinlicher ist bei einer Tag-basierten Suche die Aufnahme des Bildes in die Suchergebnisse.

1. Suchen Sie im OmniSearch-Feld nach Assets, die auf einem Tag basieren.
1. Prüfen Sie die Suchergebnisse auf Bilder, die Ihnen für Ihren Suchvorgang nicht relevant erscheinen.
1. Wählen Sie ein solches Bild aus und klicken Sie dann in der Symbolleiste auf das Symbol **[!UICONTROL Tags verwalten]**.
1. Prüfen Sie die Tags auf der Seite **[!UICONTROL Tags verwalten]**. Wenn Sie ein spezifisches Tag für ein Bild ausschließen möchten, wählen Sie das Tag aus und klicken Sie in der Symbolleiste auf das Löschsymbol. Klicken Sie alternativ auf das `X`-Symbol, das neben der Beschriftung angezeigt wird.
1. Um dem Tag einen höheren Rang zuzuweisen, wählen Sie es aus und klicken Sie in der Symbolleiste auf das Symbol „Heraufstufen“. Das höhergestufte Tag wird in den Abschnitt **[!UICONTROL Tags]** verschoben.
1. Klicken Sie auf **[!UICONTROL Speichern]** und dann Sie auf **[!UICONTROL OK]**, um das Dialogfeld „Erfolg“ zu schließen.
1. Navigieren Sie zur Seite „Eigenschaften“ des betreffenden Bildes. Beachten Sie, dass das beworbene Tag eine hohe Relevanz erhält und es aus diesem Grund höher in den Suchergebnissen angezeigt wird.

### AEM-Suchergebnisse mit Smart-Tags     {#understandsearch}

Die AEM-Suche kombiniert die Suchbegriffe standardmäßig mit einer `AND`-Klausel. Dieses Standardverhalten ändert sich durch die Verwendung von Smart-Tags nicht. Durch die Verwendung von Smart-Tags wird eine zusätzliche `OR`-Klausel hinzugefügt. Damit wird jeder Suchbegriff aus den angewandten Smart-Tags gefunden. Suchen Sie beispielsweise nach `woman running`. Assets, die in den Metadaten nur das Schlüsselwort `woman`oder `running` aufweisen, werden standardmäßig nicht in den Suchergebnissen angezeigt. Ein Asset, das über Smart-Tags mit `woman` oder `running` getaggt wurde, wird bei dieser Suchanfrage jedoch angezeigt. Die Suchergebnisse sind also eine Kombination aus

* Assets mit den Keywords `woman` und `running` in den Metadaten.

* Assets, die über Smart-Tags mit einem der Schlüsselwörter getaggt wurden.

Die Suchergebnisse, die in Metadatenfeldern alle Suchbegriffe aufweisen, werden zuerst angezeigt. Danach folgen die Suchergebnisse, die einem oder mehr Suchbegriffen in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. Treffer von `woman running` in den verschiedenen Metadatenfeldern.
1. Treffer von `woman running` in den Smart-Tags,
1. Treffer von `woman` oder `running` in Smart-Tags.

### Einschränkungen beim Tagging {#limitations}

Optimierte Smart-Tags basieren auf Lernmodellen von Markenbildern und den zugehörigen Tags. Diese Modelle können Tags nicht immer perfekt identifizieren. Bei der aktuellen Version der Smart-Tags gibt es folgende Einschränkungen:

* Subtile Unterschiede in Bildern können nicht erkannt werden. Beispiel: T-Shirts mit schmalem oder normalem Schnitt.
* Tags können nicht anhand von winzigen Mustern/Teilen eines Bildes identifiziert werden. Beispiel: Logos auf T-Shirts.
* Tagging wird in den Sprachen unterstützt, in denen AEM unterstützt wird. Eine Liste der Sprachen finden Sie in den [Versionshinweisen für Smart-Tags](https://docs.adobe.com/content/help/de-DE/experience-manager-64/release-notes/smart-content-service-release-notes.html).

Verwenden Sie Asset-OmniSearch (Volltextsuche), um nach Assets mit Smart-Tags (normal oder erweitert) zu suchen. Es gibt kein separates Suchprädikat für Smart-Tags.

>[!NOTE]
>
>Die Fähigkeit der Smart-Tags, aus Ihren Tags zu lernen und diese Tags auf andere Bilder anzuwenden, hängt von der Qualität der für das Training verwendeten Bilder ab.
>Um die bestmöglichen Ergebnisse zu erzielen, empfiehlt Adobe die Verwendung visuell ähnlicher Bilder, um den Service für die einzelnen Tags zu trainieren.

>[!MORELIKETHIS]
>
>* [Konfigurieren von Experience Manager für Smart-Tagging ](smart-tags-configuration.md)
>* [Grundlegendes, wie Smart-Tags die Verwaltung von Assets unterstützen](https://medium.com/adobetech/efficient-asset-management-with-enhanced-smart-tags-887bd47dbb3f)

