---
title: Automatisches Tagging von Assets mit [!DNL Adobe Sensei] Smart-Service
description: Kennzeichnen Sie Assets mit einem Service für künstliche Intelligenz, der kontextbezogene und beschreibende Business-Tags anwendet.
feature: Smart Tags,Tagging
role: Admin,User
source-git-commit: 9af552b17421e320b6139d6bd6ecaa42428de397
workflow-type: tm+mt
source-wordcount: '2406'
ht-degree: 24%

---


# Smart-Tags für AEM Assets {#using-smart-tags}

Unternehmen verfügen über zahlreiche digitale Assets, und diese Zahl wächst weiter rapide. Die Suche nach einem bestimmten Asset inmitten einer so großen Datenmenge stellt eine erhebliche Herausforderung dar. Um diesem Problem zu begegnen, werden `metadata` und `tags` eingesetzt, um die Durchsuchbarkeit digitaler Assets zu verbessern. Unternehmen verwenden taxonomiegesteuerte Vokabeln in Asset-Metadaten. Diese bestehen in der Regel aus Keyword-Listen, die Mitarbeiter, Partner und Kunden häufig verwenden, um auf digitale Assets zu verweisen und sie zu finden.

Smart-Tags sind Schlüsselwörter, die nicht nur im Text vorkommen, sondern das Asset auch am besten beschreiben. Das Tagging von Assets mit taxonomiegesteuertem Vokabular stellt sicher, dass sie einfach identifiziert und über die Suche abgerufen werden können.

Zum Beispiel sind Wörter, die alphabetisch in einem Wörterbuch angeordnet sind, leichter zu finden als zufällig verstreute. Tagging erfüllt einen ähnlichen Zweck. Sie organisiert Assets nach Unternehmenstaxonomien und stellt sicher, dass die relevantesten Assets in den Suchergebnissen angezeigt werden. Beispielsweise kann ein Automobilhersteller Bilder von Autos mit Modellnamen versehen, sodass beim Entwerfen einer Werbekampagne nur relevante Bilder angezeigt werden. Unabhängig davon, ob Sie „Läufer“ oder „Laufschuhe“ mit Tags versehen, müssen sich Benutzer keine Sorgen über Tippfehler, Rechtschreibvarianten oder alternative Suchbegriffe machen - Smart-Tags erkennen sie alle.

Im Hintergrund verwendet die Funktion das KI-Framework von [Adobe Sensei](https://business.adobe.com/products/sensei/adobe-sensei.html), das automatisch Smart-Tags auf hochgeladene Assets anwendet - standardmäßig - und Text, der an die Unternehmenstaxonomie angepasst ist.

## Voraussetzungen und Konfiguration {#smart-tags-prereqs-config}

Smart-Tags werden automatisch für [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] bereitgestellt, sodass keine Konfiguration erforderlich ist.

## Smart-Tags-Workflow {#smart-tags-workflow}

[!DNL Adobe Sensei] Smart-Tagging nutzt Modelle mit künstlicher Intelligenz, um Inhalte zu analysieren und den Assets Tags hinzuzufügen. Dadurch wird die Zeit für DAM-Benutzer verkürzt, ihren Kunden umfangreiche Erlebnisse bereitzustellen. Die Smart-Tags werden in den Asset[Eigenschaften in absteigender Reihenfolge ihres ](#confidence-score) angezeigt.

* **Bildbasierte Assets**
Bei Bildern basieren die Smart-Tags auf visuellen Aspekten. Bilder in vielen Formaten werden mit Smart Content Services getaggt. Smart-Tags werden auf die [unterstützten Dateitypen“ angewendet](#supported-file-formats) die Ausgabedarstellungen im JPG- und PNG-Format generieren.

  <!-- ![Image Smart Tag](assets/image-smart-tag.png)-->

* **Videobasierte Assets**
Bei videobasierten Assets ist das Tagging in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] standardmäßig aktiviert. Ebenso werden Bild- und textbasierte Tags für Videos automatisch mit Tags versehen, wenn Sie neue Videos hochladen oder vorhandene erneut verarbeiten. [!DNL Adobe Sensei] generiert zwei Sätze von Tags für ein Video: Ein Satz entspricht Objekten, Szenen und Attributen in diesem Video, während sich der andere Satz auf Aktionen wie Trinken, Laufen und Joggen bezieht. Aktivieren Sie auch [Opt-out-Video-Smart-Tagging](#opt-out-video-smart-tagging).

* **Textbasierte Assets**
Bei unterstützten Assets extrahiert [!DNL Experience Manager] bereits den Text, der dann indiziert wird und zur Suche nach den Assets verwendet wird. Smart-Tags, die auf Keywords im Text basieren, bieten jedoch eine dedizierte, strukturierte und höher priorisierte Suchfacette. Letzteres trägt dazu bei, die Asset-Erkennung im Vergleich zu einem Suchindex zu verbessern.
Bei textbasierten Assets hängt die Wirksamkeit von Smart-Tags nicht von der Textmenge im Asset ab, sondern von den relevanten Keywords oder Entitäten, die im Text des Assets vorhanden sind.

  ![Smart-Tag-types](assets/smart-tags-types.png)

Smart-Tags werden in AEM Assets mithilfe des folgenden Workflows implementiert:

1. Erstellen oder Hochladen eines Assets in AEM. Vorkonfigurierte Tags werden für Bild-, Video- und textbasierte Assets generiert.

1. Wenn Sie feststellen, dass bestimmte Tags nicht generiert werden, können Sie Ihre Tags vom Typ Bild entsprechend trainieren. Siehe [Smart-Tags-](#smart-tags-training.md).

## Unterstützte Dateiformate für Smart-Tags {#supported-file-formats}

| Bilder (MIME-Typen) | Textbasierte Assets (Dateiformate) | Video-Assets (Dateiformate und Codecs) |
|----|-----|------|
| image/jpeg | CSV | MP4 (H264/AVC) |
| image/tiff | DOC | MKV (H264/AVC) |
| image/png | DOCX | MOV (H264/AVC, Motion JPEG) |
| image/bmp | HTML | AVI (indeo4) |
| image/gif | PDF | FLV (H264/AVC, vp6f) |
| image/pjpeg | PPT | WMV (WMV2) |
| image/x-portable-anymap | PPTX |  |
| image/x-portable-bitmap | RTF |  |
| image/x-portable-graymap | SRT |  |
| image/x-portable-pixmap | TXT |  |
| image/x-rgb | VTT |  |
| image/x-xbitmap | |  |
| image/x-xpixmap | |  |
| image/x-icon |  |  |
| image/photoshop |  |  |
| image/x-photoshop |  |  |
| image/psd |  |  |
| image/vnd.adobe.photoshop |  |  |

## Vorbereiten eines Assets für vorkonfiguriertes Smart-Tagging

Wenn Sie [Assets hochladen](add-assets.md#upload-assets), um als [!DNL Cloud Service] zu [!DNL Adobe Experience Manager], werden die hochgeladenen Assets verarbeitet. Sobald die Verarbeitung abgeschlossen ist, finden Sie weitere Informationen auf der Registerkarte [!UICONTROL Allgemein] auf der Seite [!UICONTROL Asset-Eigenschaften]. Smart-Tags werden den Assets automatisch unter [!UICONTROL Smart-Tags“ ]. Asset-Microservices verwenden [!DNL Adobe Sensei], um diese Smart-Tags zu erstellen.

![Smart-Tags werden Videos hinzugefügt und auf der Registerkarte „Allgemein“ der Asset-Eigenschaften angezeigt.](assets/smart-tags-added-to-videos.png)

<!--
The applied smart tags are sorted in descending order of [confidence score](#confidence-score), combined for object and action tags, within [!UICONTROL Smart Tags].
-->

>[!IMPORTANT]
>
>Sie sollten diese automatisch generierten Tags überprüfen, um sicherzustellen, dass sie Ihrer Marke und ihren Werten entsprechen.

## Assets ohne Tags in DAM {#smart-tag-existing-assets}

Die vorhandenen oder älteren Assets in DAM werden nicht automatisch mit Smart-Tags versehen. Sie müssen Assets [erneut ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/about-image-video-profiles.html?lang=en#adjusting-load), um Smart-Tags für sie zu generieren. Navigieren Sie nach Abschluss des Vorgangs zur [!UICONTROL Eigenschaften] eines beliebigen Assets im Ordner. Die automatisch hinzugefügten Tags werden auf der Registerkarte [!UICONTROL Allgemein] im Abschnitt [!UICONTROL Smart-Tags] angezeigt. Diese angewendeten Smart-Tags werden in absteigender Reihenfolge des [Konfidenzwerts) ](#confidence-score).

<!--
To smart tag assets, or folders (including subfolders) of assets that exist in assets repository, follow these steps:

1. Select the [!DNL Adobe Experience Manager] logo and then select assets from the [!UICONTROL Navigation] page.

1. Select [!UICONTROL Files] to display the Assets interface.

1. Navigate to the folder to which you want to apply Smart Tags.

1. Select the assets and click ![Reprocess assets icon](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL Reprocess Assets] icon and select the [!UICONTROL Full Process] option.

![Reprocess assets to add tags to videos existing DAM repository](assets/reprocess.gif)-->

## Konfidenzwert {#confidence-score}

Die Ergebnisse Ihrer Asset-Suche werden auf der Grundlage der Konfidenzwerte sortiert, was die Suchergebnisse im Allgemeinen über das hinausgeht, was eine Überprüfung der zugewiesenen Tags eines Assets nahe legt. Fehlerhafte Tags weisen oft geringe Konfidenzwerte auf. Entsprechend erscheinen sie selten oben in der Liste der Smart-Tags für Assets.
<!--
[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] applies a minimum confidence threshold for object and action-smart tags to avoid having too many tags for each asset, which slows down indexing. 

The default threshold for action and object tags in [!DNL Adobe Experience Manager] for an image is 0.5 and for video it is 0.7 (should be value from 0 through 1). If some assets are not tagged by a specific tag, then it indicates that the algorithm is less than 70% confident in the predicted tags. The default threshold might not always be optimal for all the users. You can, therefore, change the confidence score value in OSGI configuration.

To add the confidence score OSGI configuration to the project deployed to [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] through [!DNL Cloud Manager]:

In the [!DNL Adobe Experience Manager] project (`ui.config` since Archetype 24, or previously `ui.apps`) the `config.author` OSGi configuration, include a config file named `com.adobe.cq.assetcompute.impl.senseisdk.SenseiSdkImpl.cfg.json` with the following contents:

```json
{
  "minVideoActionConfidenceScore":0.5,
  "minVideoObjectConfidenceScore":0.5,
}
```
-->

>[!NOTE]
>
>Manuellen Tags muss ein Vertrauen von 100 % (max. Vertrauen) zugewiesen werden. Wenn also Assets mit manuellen Tags vorhanden sind, die mit der Suchabfrage übereinstimmen, werden sie vor den Smart-Tags angezeigt, die mit der Suchabfrage übereinstimmen.

## Moderate Smart-Tags {#moderate-smart-tags}

Mit [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] können Sie die Smart-Tags kuratieren, um:

* Entfernen Sie ungenaue Tags, die Ihren Marken-Assets zugewiesen sind.

* Verfeinern Sie die Tag-basierte Suche nach Assets, indem Sie sicherstellen, dass Ihr Asset in den Suchergebnissen nach den relevantesten Tags angezeigt wird. Dadurch wird die Wahrscheinlichkeit eliminiert, dass nicht verwandte Assets in Suchergebnissen angezeigt werden.

* Weisen Sie einem Tag einen höheren Rang zu, um seine Relevanz in Bezug auf ein Asset zu erhöhen. Das Hochstufen eines Tags für ein Asset erhöht die Wahrscheinlichkeit, dass das bestimmte Asset in den Suchergebnissen erscheint, wenn eine auf diesem Tag basierende Suche durchgeführt wird.

Weitere Informationen zum Moderieren der Smart-Tags für Assets finden Sie unter [ von Smart-Tags](smart-tags.md#manage-smart-tags-and-searches).

![Smart-Tags für moderate Videos](assets/manage-video-smart-tags.png)

>[!NOTE]
>
>Alle Tags, die mit den Schritten in [Verwalten von Smart-Tags](smart-tags.md#manage-smart-tags-and-searches) moderiert werden, werden bei der erneuten Verarbeitung des Assets nicht gespeichert. Die ursprünglichen Sätze von Tags werden erneut angezeigt.

## Verwalten von Smart-Tags und Asset-Suchen {#manage-smart-tags-and-searches}

Sie können Smart-Tags kuratieren, um ungenaue Tags zu entfernen, die Ihren Marken-Assets zugewiesen wurden, sodass nur die relevantesten Tags angezeigt werden.

Durch die Moderation von Smart-Tags können Sie auch die Tag-basierte Suche nach Assets verfeinern, indem Sie sicherstellen, dass Ihre Assets in den Suchergebnissen für die relevantesten Tags angezeigt werden. Im Grunde wird so ausgeschlossen, dass in den Suchergebnissen Assets ohne Bezug angezeigt werden.

Sie können einem Tag auch einen höheren Rang zuweisen, um die Relevanz des Tags für das Asset zu erhöhen. Je höher der Rang eines Tags für ein Asset desto wahrscheinlicher ist bei einer Tag-basierten Suche die Aufnahme des Assets in die Suchergebnisse.

So moderieren Sie die Smart-Tags Ihrer digitalen Assets:

1. Suchen Sie im Suchfeld nach digitalen Assets, die auf einem Tag basieren.

1. Prüfen Sie die Suchergebnisse, um die digitalen Assets zu identifizieren, die für Ihre Suche nicht relevant sind.

1. Wählen Sie ein Asset aus, und wählen Sie dann in der Symbolleiste ![Symbol „Tags verwalten“](assets/do-not-localize/manage-tags-icon.png) aus.

1. Prüfen Sie die Tags auf der Seite **[!UICONTROL Tags verwalten]**. Wenn Sie ein spezifisches Tag für ein Asset ausschließen möchten, wählen Sie das Tag und anschießend in der Symbolleiste ![Löschsymbol](assets/do-not-localize/delete-icon.svg) aus. Klicken Sie alternativ auf ![Symbol „Schließen](assets/do-not-localize/close_icon.svg) neben der Beschriftung.

1. Um einem Tag einen höheren Rang zuzuweisen, wählen Sie das Tag und anschließend in der Symbolleiste ![Symbol „Höherstufen“](assets/do-not-localize/promote-icon.svg) aus. Das höhergestufte Tag wird in den Abschnitt **[!UICONTROL Tags]** verschoben.

1. Wählen Sie **[!UICONTROL Speichern]** und dann **[!UICONTROL OK]** au, um das Dialogfeld [!UICONTROL Erfolg] zu schließen.

1. Gehen Sie zur Seite „[!UICONTROL Eigenschaften]“ des betreffenden Assets. Beachten Sie, dass das hochgestufte Tag eine hohe Relevanz hat und daher in den Suchergebnissen höher angezeigt wird.

### Grundlegendes [!DNL Experience Manager] Suchergebnisse mit Smart-Tags {#understand-search}

Standardmäßig kombiniert [!DNL Experience Manager] die Suchbegriffe mit einer `AND`- oder `OR`-Klausel, um einen der Suchbegriffe in den angewendeten Smart-Tags zu finden. Dieses Standardverhalten ändert sich durch die Verwendung von Smart-Tags nicht. Suchen Sie beispielsweise nach `woman running`. Assets, die in den Metadaten nur das Keyword `woman`oder `running` aufweisen, werden standardmäßig nicht in den Suchergebnissen angezeigt. Ein Asset, das über Smart-Tags mit `woman` oder `running` getaggt wurde, wird jedoch in einer solchen Suchanfrage angezeigt. Die Suchergebnisse sind also eine Kombination aus

* Assets mit den Keywords `woman` und `running` in den Metadaten.

* Assets, die über Smart-Tags mit einem der Keywords getaggt wurden.

Die Suchergebnisse, die allen Suchbegriffen in Metadatenfeldern entsprechen, werden zuerst angezeigt, gefolgt von den Suchergebnissen, die einem der Suchbegriffe in den Smart-Tags entsprechen. Im obigen Beispiel werden die Suchergebnisse ungefähr in dieser Reihenfolge angezeigt:

1. Treffer von `woman running` in den verschiedenen Metadatenfeldern.
1. Treffer von `woman running` in Smart-Tags.
1. Treffer von `woman` oder `running` in Smart-Tags.

## Deaktivieren von Smart-Tagging {#opt-out-smart-tagging}

Da das automatische Tagging von Assets parallel zu anderen Asset-Verarbeitungsaufgaben wie der Erstellung von Miniaturen und der Extraktion von Metadaten ausgeführt wird, kann es sich zeitaufwendig gestalten. Um die Asset-Verarbeitung zu beschleunigen, können Sie das Smart-Tagging beim Hochladen auf Ordnerebene deaktivieren. So deaktivieren Sie die automatisierte Smart-Tags-Generierung für Assets, die in einen bestimmten Ordner hochgeladen wurden:

1. Wechseln Sie zur Registerkarte [!UICONTROL Asset-Verarbeitung] im Ordner [!UICONTROL Eigenschaften].
1. Im [!UICONTROL  „Smart-Tags für ]&quot; ist beispielsweise standardmäßig die Option [!UICONTROL Vererbt] ausgewählt und das Smart-Tag „Video“ aktiviert.

   Wenn die Option [!UICONTROL Übernommen] ausgewählt ist, wird auch der Pfad des übernommenen Ordners angezeigt, zusammen mit der Information, ob die Option auf oder [!UICONTROL Aktiviert] oder [!UICONTROL Deaktiviert] festgelegt ist.

   ![Smart-Tagging deaktivieren](assets/disable-tagging.png)

1. Wählen Sie [!UICONTROL Deaktivieren] aus, um das in den Ordner hochgeladene Smart-Tagging abzuwählen.

1. Ebenso können Sie Smart-Tags für [!UICONTROL Smart-Tags für Text], [!UICONTROL Smart-Tags für Bild] und [!UICONTROL Farb-Tags für Bilder] deaktivieren.

>[!IMPORTANT]
>
>Wenn Sie das Tagging für einen Ordner zum Zeitpunkt des Uploads abgelehnt haben und das Smart-Tagging nach dem Upload durchführen möchten, wählen Sie **[!UICONTROL Smart-Tags aktivieren]** auf der Registerkarte [!UICONTROL Asset-Verarbeitung] des Ordners [!UICONTROL Eigenschaften] und verwenden Sie die Option [[!UICONTROL Asset erneut verarbeiten] ](#smart-tag-existing-assets), um den Assets Smart-Tags hinzuzufügen.

<!--
## Benefits of Smart Tags to your assets {#benefits-of-smart-tags}

Following are the benefits of using Smart Tags in your AEM Assets:
*  Makes an asset searchable.
*  Smart Tags are generated automatically to your assets, thus, it minimizes your effort to perform tagging manually.
*  It allows the usage of the same vocabulary, tag structure, and taxonomy so that you need not to worry about tagging if by chance you miss tagging at first.
*  Whether you are tagging "runners" or "running" shoes, you do not need to worry about typos, wrong spellings, or alternative search terms as Smart Tags know it already!
*  Helps your assets to become organized and categorized.
-->

## Verbessern der Inhaltssuche mit KI-generierten Smart-Tags {#ai-smart-tags}

Anstatt sich auf die manuelle Eingabe zu verlassen, weist KI digitalen Assets automatisch beschreibende Tags zu. Diese KI-generierten Tags verbessern die Metadatenqualität und erleichtern die Suche, Kategorisierung und Empfehlung von Assets. Dieser Ansatz verbessert nicht nur die Effizienz durch die Eliminierung manueller Tags, sondern stellt auch Konsistenz und Skalierbarkeit über große Mengen digitaler Inhalte hinweg sicher. Wenn das Asset beispielsweise ein Bild ist, kann KI Objekte, Szenen, Emotionen oder sogar Markenlogos darin identifizieren und relevante Tags wie „Sonnenuntergang“, „Strand“, „Urlaub“ oder „Lächeln“ generieren. KI-generierte Inhalte können die Suche nach Assets verbessern, indem sie sowohl semantische als auch lexikalische Suchtechniken nutzen. Weitere Informationen finden [Assets durchsuchen](search-assets.md). <!--If the asset is a document, AI reads and interprets the text to assign meaningful keywords that summarize its content—such as "climate change," "policy," or "renewable energy.-->

![Optimierte Smart-Tags](assets/enhanced-smart-tags1.png)

### Verwenden von KI-generierten Smart-Tags {#using-ai-generated-smart-tags}

<!--[!NOTE]
>
>The enhanced smart tags capability is available only for the newly uploaded assets.
-->

Um die erweiterte Smart-Tags-Funktion zu verwenden, führen Sie die folgenden Schritte aus:

1. Wechseln Sie in der [!DNL Experience Manager] zum gewünschten Ordner und klicken Sie auf **[!UICONTROL Assets hinzufügen]**. <!--Alternatively, to update enhanced smart tags in an existing content, click **[!UICONTROL reprocess]**.--> Die kompatiblen Bilddateiformate sind `png`, `jpg`, `jpeg`, `psd`, `tiff`, `gif`, `webp`, `crw`, `cr2`, `3fr`, `nef`, `arw` und `bmp`.

1. Warten Sie, bis das neu hochgeladene Asset verarbeitet wurde. Navigieren Sie anschließend zu den Asset-Eigenschaften.

1. Wechseln Sie **[!UICONTROL Registerkarte]** KI-generiert“. Wenn [!DNL Experience Manager] Version inkompatibel ist oder nicht aktualisiert wird, ist diese Registerkarte nicht sichtbar. Die mindestens erforderliche AEM-Release-Version ist `20626`. Die folgenden Felder sind vorhanden:

   * **[!UICONTROL Erstellter Titel]:** Der Titel bietet eine klare und knappe Überschrift, die die Kernidee eines hochgeladenen Assets erfasst und es auf einen Blick leicht verständlich macht. Wenn Sie beim Hinzufügen eines Assets einen Titel angeben (in `dc:title`), wird dieser in der Ansicht zum Durchsuchen von Assets angezeigt. Wenn Sie das Feld leer lassen, wird automatisch ein von KI generierter Titel zugewiesen.
   * **[!UICONTROL Erzeugte Beschreibung]:** Die Beschreibung bietet eine kurze, aber informative Zusammenfassung dessen, worum es bei dem Asset geht, und hilft Benutzern und Suchmodulen, seine Relevanz schnell zu verstehen.
   * **[!UICONTROL Erzeugte Keywords]:** Die Keywords sind zielgerichtete Begriffe, die die Hauptthemen eines Assets darstellen und beim Tagging und Filtern von Inhalten helfen.

1. [Optional] Sie können zusätzliche Tags hinzufügen oder eigene erstellen, wenn Sie der Meinung sind, dass relevante Tags fehlen. Schreiben Sie dazu Ihre Tags in das Feld **[!UICONTROL Erzeugte Keywords]** und klicken Sie auf **[!UICONTROL Speichern]**.

## Einschränkungen und Best Practices im Zusammenhang mit Smart-Tags {#limitations-best-practices-smart-tags}

Diese Modelle können Tags nicht immer perfekt identifizieren. Bei der aktuellen Version der Smart-Tags gibt es folgende Einschränkungen:

* Subtile Unterschiede in Bildern können nicht erkannt werden. Beispiel: Hemden mit schlanker oder normaler Passform.
* Tags können nicht anhand von winzigen Mustern oder Teilen eines Bildes identifiziert werden. Beispiel: Logos auf Hemden.
* Die Tags, die nicht verarbeitet werden, beziehen sich auf:

   * Nicht visuelle, abstrakte Aspekte, Beispielsweise das Jahr oder die Jahreszeit der Veröffentlichung eines Produkts, die Stimmung oder die Emotionen, die durch ein Bild hervorgerufen werden, und eine subjektive Konnotation eines Videos.
   * Feine visuelle Unterschiede bei Produkten wie Hemden mit und ohne Kragen oder kleinen Produkt-Logos, die in Produkte eingebettet sind.

* Nur Videos mit einer Dateigröße von weniger als 300 MB werden automatisch mit Tags versehen. Der [!DNL Adobe Sensei]-Service überspringt Videodateien, die größer sind.
* Verwenden Sie die [!DNL Assets]-Suche (Volltextsuche), um nach Dateien mit Smart-Tags (normal oder erweitert) zu suchen. Es gibt kein separates Suchprädikat für Smart-Tags.
* Im Vergleich zu allgemeinen Tags sind die Assets, die mit einer Unternehmenstaxonomie getaggt werden, durch Tag-basierte Suchen einfacher zu identifizieren und abzurufen.

## Häufig gestellte Fragen{#faq-smart-tags}

+++**Wie verbessern Smart-Tags das Sucherlebnis eines Assets?**

[!DNL Adobe] Sensei taggt die Assets automatisch, sobald Sie sie hochladen. Der automatisierte Prozess läuft am Backend so schnell, dass nach einigen Sekunden nach Abschluss des Uploads Tags in Ihren Assets hinzugefügt werden.

+++

+++**Was passiert, wenn die Smart-Tags-Liste ungenau ist oder unerwünschte Tags anzeigt?**

Ein ungenaues oder unerwünschtes Tag kann aus der Liste entfernt werden. Als Autohändler möchten Sie beispielsweise das Tag „Beschädigt“ aus der Liste entfernen.

+++

+++**Wie können Assets mit denselben Tags priorisiert werden?**

Ja, Sie können Assets mit denselben Tags priorisieren. Sie können ein Tag in die Smart-Tags-Liste eines Assets hochstufen, um eine Priorisierung durchzuführen. Indem Sie ein Tag hochstufen, können Sie die Bilder in den Suchergebnissen für dieses bestimmte Tag priorisieren.

+++

+++**Ist die Anwendung von Smart-Tags auf einen bestimmten Ordner beschränkt?**

Smart-Tags sind konfigurierbar und können auf jeden Ordner in DAM angewendet werden.

+++

+++**Woher weiß ich, dass Tagging Schulung erfordert?**

Siehe [Bestimmen der Anforderungen an das Smart-Tags-Training](#smart-tags-training.md#smart-tag-training-requirement).

+++

+++**Welche Dateiformate werden für das Tagging von Assets unterstützt?**

Siehe [Unterstützte Dateiformate](#supported-file-formats).

+++

+++**In welcher Sprache werden Smart-Tags generiert?**

Smart-Tags werden nur in englischer Sprache generiert. Sie können in andere Sprachen übersetzt werden, indem das gesamte Asset einschließlich der Metadaten übersetzt wird.

+++

+++**Ich möchte das Smart-Tagging nicht mehr verwenden.**

Sie können [Smart-Tagging deaktivieren](#opt-out-smart-tagging) wenn Sie dies beenden möchten.

+++
