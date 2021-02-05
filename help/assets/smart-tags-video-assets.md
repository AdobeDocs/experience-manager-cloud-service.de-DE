---
title: Intelligente Tags für Video-Assets
description: Experience Manager fügt Videos mit [!DNL Adobe Sensei] automatisch kontextbezogene und beschreibende Smart-Tags hinzu.
translation-type: tm+mt
source-git-commit: ceaa9546be160e01b124154cc827e6b967388476
workflow-type: tm+mt
source-wordcount: '1183'
ht-degree: 0%

---


# Smart-Tags für Ihre Video-Assets {#video-smart-tags}

Der wachsende Bedarf an neuen Inhalten erfordert geringere manuelle Anstrengungen, um in kürzester Zeit überzeugende digitale Erlebnisse bereitzustellen. [!DNL Adobe Experience Manager] als  [!DNL Cloud Service] Unterstützung für das automatische Tagging von Video-Assets mit künstlicher Intelligenz. Das manuelle Tagging der Videos kann zeitaufwendig sein. Die Funktion für intelligentes Tagging von Videos verwendet jedoch Modelle mit künstlicher Intelligenz, um Videoinhalte zu analysieren und den Video-Assets Tags hinzuzufügen. [!DNL Adobe Sensei] Dadurch wird die Zeit für DAM-Benutzer verringert, ihren Kunden umfangreiche Erlebnisse bereitzustellen. Der maschinelle Lerndienst der Adobe generiert zwei Tags für ein Video. Ein Satz entspricht jedoch Objekten, Szenen und Attributen in diesem Video; Der andere Satz bezieht sich auf Aktionen wie Trinken, Laufen und Joggen.

Video-Tagging ist in [!DNL Adobe Experience Manager] standardmäßig als [!DNL Cloud Service] aktiviert. Sie können jedoch [Smart-Tagging für Videos](#opt-out-video-smart-tagging) in einem Ordner deaktivieren. Videos werden automatisch mit Tags versehen, wenn Sie neue Videos hochladen oder vorhandene erneut verarbeiten. [!DNL Experience Manager] erstellt außerdem die Miniaturansichten und extrahiert Metadaten der Videodateien. Die Smarttags werden in absteigender Reihenfolge ihres [Konfidenzwerts](#confidence-score-video-tag) in Asset [!UICONTROL Eigenschaften] angezeigt.

## Smart-Tagging-Videos beim Hochladen von {#smart-tag-assets-on-ingestion}

Wenn Sie [Video-Assets](add-assets.md#upload-assets) als [!DNL Adobe Experience Manager] [!DNL Cloud Service] hochladen, werden die Videos verarbeitet. Sobald die Verarbeitung abgeschlossen ist, finden Sie weitere Informationen auf der Seite [!UICONTROL Einfach] des Assets [!UICONTROL Eigenschaften]. Intelligente Tags werden dem Video unter [!UICONTROL Smart Tags] automatisch hinzugefügt. Asset Microservices verwendet [!DNL Adobe Sensei], um diese Smarttags zu erstellen.

![Intelligente Tags werden Videos hinzugefügt und auf der Registerkarte &quot;Einfach&quot;der Asset-Eigenschaften angezeigt](assets/smart-tags-added-to-videos.png)

Die angewendeten Smarttags werden in absteigender Reihenfolge nach [Konfidenzwert](#confidence-score-video-tag) sortiert, kombiniert mit Objekt- und Aktionstag, innerhalb von [!UICONTROL Smart Tags].

>[!IMPORTANT]
>
>Sie sollten diese automatisch generierten Tags überprüfen, um sicherzustellen, dass sie mit Ihrer Marke und ihren Werten übereinstimmen.

## Intelligentes Tagging vorhandener Videos in DAM {#smart-tag-existing-videos}

Die bereits vorhandenen Video-Assets in DAM werden nicht automatisch mit intelligenten Tags versehen. Sie müssen die Elemente [!UICONTROL Neu verarbeiten] manuell, um Smarttags für sie zu generieren.

Gehen Sie wie folgt vor, um Video-Assets oder Ordner (einschließlich Unterordner) mit Assets zu versehen, die bereits im Assets-Repository vorhanden sind:

1. Wählen Sie das [!DNL Adobe Experience Manager]-Logo aus und wählen Sie dann Assets auf der Seite [!UICONTROL Navigation] aus.

1. Wählen Sie [!UICONTROL Dateien] aus, um die Assets-Oberfläche anzuzeigen.

1. Navigieren Sie zu dem Ordner, auf den Sie Smarttags anwenden möchten.

1. Wählen Sie den gesamten Ordner oder bestimmte Video-Assets aus.

1. Wählen Sie das Symbol ![Assets neu verarbeiten](assets/do-not-localize/reprocess-assets-icon.png) [!UICONTROL Assets neu verarbeiten] und wählen Sie die Option [!UICONTROL Vollständiger Prozess].

<!-- TBD: Limit size -->

![Assets neu verarbeiten, um dem vorhandenen DAM-Repository Tags hinzuzufügen](assets/reprocess.gif)

Nach Abschluss des Vorgangs navigieren Sie zur Seite [!UICONTROL Eigenschaften] eines Videoassets im Ordner. Die automatisch hinzugefügten Tags werden im Abschnitt [!UICONTROL Smart Tags] auf der Registerkarte [!UICONTROL Einfach] angezeigt. Diese angewendeten Smarttags werden in absteigender Reihenfolge nach [Konfidenzwert](#confidence-score-video-tag) sortiert.

## Suchen nach getaggten Videos {#search-smart-tagged-videos}

Verwenden Sie [Omniture Search](search-assets.md#search-assets-in-aem), um nach Video-Assets zu suchen, die auf den automatisch generierten Smart-Tags basieren:

1. Wählen Sie das Suchsymbol ![Suchsymbol](assets/do-not-localize/search_icon.png) aus, um das Suchfeld anzuzeigen.

1. Geben Sie im Feld &quot;Omniture-Suche&quot;ein Tag an, das Sie einem Video nicht explizit hinzugefügt haben.

1. Suche anhand des Tags.

Die Suchergebnisse zeigen die Video-Assets basierend auf dem von Ihnen angegebenen Tag an.

Bei Ihren Suchergebnissen handelt es sich um eine Kombination aus Video-Assets mit gesuchten Suchbegriffen in den Metadaten und den Video-Assets, die mit den gesuchten Suchbegriffen gekennzeichnet sind. Die Suchergebnisse, die mit allen Suchbegriffen in den Metadatenfeldern übereinstimmen, werden jedoch zuerst angezeigt, gefolgt von den Suchergebnissen, die mit einem der Suchbegriffe in den Smarttags übereinstimmen. Weitere Informationen finden Sie unter [Suchergebnisse mit Smarttags](smart-tags.md#understandsearch) verstehen. [!DNL Experience Manager] 

## Moderieren von Smart-Tags für Videos {#moderate-video-smart-tags}

[!DNL Adobe Experience Manager] ermöglicht Ihnen, die Smarttags wie folgt zu kuratieren:

* Entfernen Sie ungenaue Tags, die Ihren Markenvideos zugewiesen wurden.

* verfeinern Sie tagbasierte Suchen nach Videos, indem Sie sicherstellen, dass Ihr Video in den Suchergebnissen nach den relevantesten Tags angezeigt wird. Dadurch wird die Wahrscheinlichkeit, dass Videos ohne Bezug in Suchergebnissen angezeigt werden, vermieden.

* einem Tag einen höheren Rang zuweisen, um seine Relevanz in Bezug auf ein Video zu erhöhen. Die Förderung eines Tags für ein Video erhöht die Wahrscheinlichkeit, dass das Video in den Suchergebnissen angezeigt wird, wenn eine Suche basierend auf diesem Tag durchgeführt wird.

Weitere Informationen zum Moderieren der Smart-Tags für Assets finden Sie unter [Verwalten von Smart-Tags](smart-tags.md#manage-smart-tags-and-searches).

![Moderieren von Smart-Tags für Videos](assets/manage-video-smart-tags.png)

>[!NOTE]
>
>Alle Tags, die mithilfe der Schritte unter [Smarttags verwalten](smart-tags.md#manage-smart-tags-and-searches) moderiert werden, werden bei der Neuverarbeitung des Assets nicht gespeichert. Der ursprüngliche Tag-Satz wird erneut angezeigt.

## Opt-out der intelligenten Tagging-Funktion für Videos {#opt-out-video-smart-tagging}

Da das automatische Tagging von Videos parallel zu anderen Asset-verarbeitenden Aufgaben wie der Erstellung von Miniaturbildern und der Extraktion von Metadaten ausgeführt wird, kann dies zeitaufwendig sein. Um die Asset-Verarbeitung zu beschleunigen, können Sie beim Hochladen auf Ordnerebene Video-Smart-Tagging Opt-out.

So Opt-out Sie die Erstellung automatisierter Video-Smart-Tags für Assets, die in einen bestimmten Ordner hochgeladen wurden:

1. Öffnen Sie die Registerkarte [!UICONTROL Asset-Verarbeitung] im Ordner [!UICONTROL Eigenschaften].

1. Im Menü [!UICONTROL Smart Tags für Videos] ist die Option [!UICONTROL Inherited] standardmäßig ausgewählt und das Smart-Tag für Videos ist aktiviert.

   Wenn die Option [!UICONTROL Inherited] ausgewählt ist, wird der geerbte Ordnerpfad zusammen mit den Informationen auch angezeigt, ob er auf [!UICONTROL Aktivieren] oder [!UICONTROL Deaktivieren] eingestellt ist.

   ![Deaktivieren der intelligenten Tagging-Funktion für Videos](assets/disable-video-tagging.png)

1. Wählen Sie [!UICONTROL Deaktivieren Sie], um Opt-out intelligentes Tagging von in den Ordner hochgeladenen Videos durchzuführen.

>[!IMPORTANT]
>
>Wenn Sie sich zum Zeitpunkt des Hochladevorgangs dafür entschieden haben, Videos in einem Ordner nicht mit Tags zu versehen, und die Videos nach dem Hochladen mit Tags versehen möchten, dann **[!UICONTROL Aktivieren Sie Smart Tags für Videos]** auf der Registerkarte [!UICONTROL Asset-Verarbeitung] des Ordners [!UICONTROL Eigenschaften] und verwenden Sie die Option [[!UICONTROL Element neu verarbeiten], um intelligente Tags hinzuzufügen Video.](#smart-tag-existing-videos)

## Konfidenzwert {#confidence-score-video-tag}

[!DNL Adobe Experience Manager] wendet einen minimalen Konfidenzschwellenwert für Objekt- und Aktionssmart-Tags an, um zu vermeiden, dass für jedes Video-Asset zu viele Tags vorhanden sind, was die Indizierung verlangsamt. Die Suchergebnisse Ihrer Assets werden auf der Grundlage der Vertrauenswerte sortiert, wodurch die Suchergebnisse im Allgemeinen über das hinausgehen, was eine Überprüfung der zugewiesenen Tags eines Video-Assets nahe legt. Falsche Tags weisen oft niedrige Konfidenzwerte auf, sodass sie selten oben in der Liste für intelligente Tags für Assets angezeigt werden.

Der Standardschwellenwert für Aktions- und Objekt-Tags in [!DNL Adobe Experience Manager] ist 0,7 (sollte zwischen 0 und 1 liegen). Wenn einige Video-Assets nicht mit einem bestimmten Tag versehen sind, deutet dies darauf hin, dass der Algorithmus in den prognostizierten Tags weniger als 70 % sicher ist. Der Standardschwellenwert ist möglicherweise nicht immer optimal für alle Benutzer. Sie können daher den Wert des Konfidenzwerts in der OSGI-Konfiguration ändern.

So fügen Sie die OSGI-Konfiguration des Konfidenzwerts zum Projekt hinzu, das [!DNL Adobe Experience Manager] als [!DNL Cloud Service] bis [!DNL Cloud Manager] bereitgestellt wird:

* Fügen Sie im [!DNL Adobe Experience Manager]-Projekt (`ui.config` seit Archetype 24 oder zuvor `ui.apps`) die `config.author` OSGi-Konfiguration eine Konfigurationsdatei mit dem Namen `com.adobe.cq.assetcompute.impl.senseisdk.SenseiSdkImpl.cfg.json` mit folgendem Inhalt hinzu:

```json
{
  "minVideoActionConfidenceScore":0.5,
  "minVideoObjectConfidenceScore":0.5,
}
```

>[!NOTE]
>
>Manuelle Tags erhalten eine Konfidenz von 100 % (maximale Konfidenz). Wenn es also Video-Assets mit manuellen Tags gibt, die der Abfrage der Suche entsprechen, werden sie angezeigt, bevor Smart-Tags mit der Abfrage der Suche übereinstimmen.

## Beschränkungen {#video-smart-tagging-limitations}

* Sie können den Dienst, der intelligente Tags auf Videos anwendet, nicht mit bestimmten Videos ausbilden. Es funktioniert mit Standardeinstellungen für [!DNL Adobe Sensei].

* Der Tag-Fortschritt wird nicht angezeigt.

* Nur Videos mit einer Dateigröße von weniger als 300 MB werden automatisch mit Tags versehen. Der Dienst [!DNL Adobe Sensei] überspringt Videodateien, die größer sind.

* Nur die Videos in den Dateiformaten und unterstützten Codecs, die unter [Smart Tags](/help/assets/smart-tags.md#smart-tags-supported-file-formats) erwähnt werden, werden mit Tags versehen.

>[!MORELIKETHIS]
>
>* [Verwalten von Smart-Tags und Asset-Suchen](smart-tags.md#manage-smart-tags-and-searches)
>* [Trainieren des Smart-Tag-Service und Tagging von Bildern](smart-tags.md)

