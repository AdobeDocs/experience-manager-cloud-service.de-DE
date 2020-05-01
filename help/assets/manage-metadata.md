---
title: Verwalten Sie Metadaten Ihrer digitalen Assets in [!DNL Adobe Experience Manager].
description: Erfahren Sie mehr über die Metadatentypen und wie [!DNL Adobe Experience Manager Assets] beim Verwalten von Metadaten für Assets hilft, um die Kategorisierung und Organisation von Assets zu erleichtern. [!DNL Experience Manager] ermöglicht die automatische Organisation und Verarbeitung von Assets anhand ihrer Metadaten.
contentOwner: AG
mini-toc-levels: 1
translation-type: tm+mt
source-git-commit: 0686acbc61b3902c6c926eaa6424828db0a6421a

---


# Verwalten von Metadaten für digitale Assets {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] speichert Metadaten für jedes Asset. Dies erleichtert die Kategorisierung und Organisation von Assets und hilft Menschen, die nach einem bestimmten Asset suchen. With the ability to extract metadata from files uploaded to [!DNL Experience Manager Assets], metadata management integrates with the creative workflow. With the ability to keep and manage metadata with your assets, [!DNL Experience Manager Assets] makes it possible to automatically organize and process assets based on their metadata.

>[!MORELIKETHIS]
>
>* [XMP-Metadaten](xmp-metadata.md)
>* [Anleitung zum Bearbeiten oder Hinzufügen von Metadaten](meta-edit.md)


<!-- 
* [Metadata Schemata Reference](meta-ref.md)
-->

## Wozu dienen Metadaten? {#why-metadata}

Metadaten sind Informationen über Daten. In dieser Hinsicht beziehen sich Daten auf Ihr digitales Asset, z. B. ein Bild. Metadaten sind für eine effiziente Asset-Verwaltung von entscheidender Bedeutung.

Metadaten sind alle für ein Asset verfügbaren Daten, die jedoch nicht unbedingt in diesem Bild enthalten sind. Beispiele für Metadaten:

* Name des Assets.
* Zeitpunkt und Datum der letzten Änderung.
* Größe des Assets, wie es im Repository gespeichert wurde.
* Name des Ordners, in dem er enthalten ist.
* Zugehörige Assets oder angewendete Tags.

These are the basic metadata properties that [!DNL Experience Manager] can manage for assets, which allows users to see all assets, for example, ordered by their last modification date - useful when trying to discover what assets have recently been added to the repository.

Sie können digitalen Assets auch Daten auf höherer Ebene hinzufügen – darunter:

* Asset-Typ (ist es ein Bild, ein Video, ein Audioclip oder ein Dokument?)
* Eigentümer des Assets.
* Titel des Assets.
* Beschreibung des Assets.
* Tags, die einem Asset zugewiesen sind.

Mit mehr Metadaten können Sie Assets genauer einteilen. Außerdem erweisen sie sich als nützlich, wenn die Menge digitaler Daten ansteigt. Es ist möglich, einige hundert Dateien zu verwalten, die nur auf den Dateinamen basieren. Dieser Ansatz ist jedoch nicht skalierbar und fällt schnell unter, wenn die Zahl der beteiligten Personen und die Zahl der verwalteten Assets steigt.

Durch Hinzufügen von Metadaten wächst der Wert eines digitalen Assets, da das Asset

* Mehr Zugänglichkeit - Systeme und Benutzer können es leicht finden.
* Einfachere Verwaltung - Sie können Assets mit demselben Satz Eigenschaften einfacher finden und Änderungen darauf anwenden.
* Vollständiger: Je mehr Metadaten Sie zu einem Asset hinzugefügt haben, desto mehr Informationen und Kontext werden mit dem Asset geliefert.

For these reasons, [!DNL Assets] provides you with the right means of creating, managing, and exchanging metadata for your digital assets.

## Metadatentypen {#types-of-metadata}

Die beiden grundlegenden Metadatentypen sind technische Metadaten und beschreibende Metadaten.

Technische Metadaten eignen sich für Software-Anwendungen, die mit digitalen Assets arbeiten und nicht manuell gepflegt werden sollen. [!DNL Experience Manager Assets] und andere Software bestimmen automatisch technische Metadaten und die Metadaten können sich ändern, wenn das Asset geändert wird. Welche technischen Metadaten für ein Asset verfügbar sind, hängt größtenteils vom Dateityp des Assets ab. Beispiele für technische Metadaten:

* Größe einer Datei.
* Abmessungen (Höhe und Breite) eines Bildes.
* Bitrate einer Audio- oder Videodatei.
* Auflösung (Detailstufe) eines Bildes.

Beschreibende Metadaten sind solche, die sich auf die Anwendungsdomäne beziehen – etwa das Unternehmen, aus dem ein Asset stammt. Beschreibende Metadaten können nicht automatisch bestimmt werden. Es wird manuell oder halbautomatisch erstellt. Beispielsweise kann eine GPS-fähige Kamera automatisch den Breiten- und Längengrad verfolgen und Geotag für das Bild hinzufügen.

Da der manuelle Aufwand für die Erstellung beschreibender Metadaten sehr kostspielig ist, wurden Standards aufgestellt, um den Austausch von Metadaten über Softwaresysteme und Organisationen hinweg zu erleichtern.

[!DNL Experience Manager Assets] unterstützt alle relevanten Standards für das Metadatenmanagement.

Aufgrund der Wichtigkeit von Metadaten und des hohen manuellen Arbeitsaufwands für ihre Erstellung wurden Standards aufgestellt, die den Austausch erleichtern.

## Kodierungsstandards {#encoding-standards}

Es gibt verschiedene Möglichkeiten, Metadaten in Dateien einzubetten. Dazu werden die folgenden Kodierungsstandards unterstützt:

* XMP: used by [!DNL Assets] to store the extracted metadata within the repository.
* ID3: für Audio- und Videodateien
* Exif: für Bilddateien.
* Other/Legacy: from [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel], and so on.

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP) ist ein offener Standard, der [!DNL Experience Manager Assets] für alle Metadatenverwaltung verwendet wird. Die standardmäßige Angebot-Metadaten-Kodierung, die in alle Dateiformate eingebettet werden kann. Adobe und andere Firmen unterstützen den XMP-Standard, da er ein Rich-Content-Modell bietet. Benutzer des XMP-Standards und von [!DNL Experience Manager Assets] haben eine leistungsstarke Plattform, auf der sie aufbauen können. Weitere Informationen finden Sie unter [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

In diesen ID3-Tags gespeicherte Daten werden angezeigt, wenn Sie eine digitale Audiodatei auf dem Computer oder einem tragbaren MP3-Player abspielen.

ID3-Tags wurden für das MP3-Dateiformat entwickelt. Weitere Informationen zu Formaten:

* ID3-Tags funktionieren in MP3- und mp3PRO-Dateien.
* WAV weist keine Tags auf.
* WMA verfügt über proprietäre Tags, die keine Open-Source-Implementierung zulassen.
* Ogg Vorbis nutzt Xiph-Kommentare, die in den Ogg-Container eingebettet sind.
* AAC verwendet ein proprietäres Tagging-Format.

### Exif {#exif}

Das austauschbare Bilddateiformat (Exif) ist das beliebteste Metadatenformat für die Digitalfotografie. Es bietet eine Möglichkeit zum Einbetten eines festen Wortschatzes mit Metadateneigenschaften in viele Dateiformate wie JPEG, TIFF, RIFF und WAV. Exif stores metadata as pairs of a metadata name and a metadata value. These metadata name-value-pairs are also called tags, not to be confused with the tagging in [!DNL Experience Manager]. Da Exif automatisch von modernen Digitalkameras erstellt und durch moderne Grafiksoftware unterstützt wird, kann es als kleinster gemeinsamer Nenner für das Metadaten-Management angesehen werden.

Eine wichtige Einschränkung von Exif besteht darin, dass einige gängige Bilddateiformate wie BMP, GIF oder PNG diese nicht unterstützen.

Metadatenfelder, die normalerweise von Exif definiert werden, sind technischer Natur und werden nur in begrenztem Umfang für die Verwaltung beschreibender Metadaten verwendet. Aus diesem Grund werden [!DNL Experience Manager Assets] Angebote von Exif-Eigenschaften in [gängige Metadaten-Schemata](metadata-schemas.md) und in XMP zugeordnet.

#### Other metadata {#other-metadata}

Andere Metadaten können aus Dateien von Microsoft Word, PowerPoint, Excel usw. eingebettet werden.

## Verwalten von Metadaten für digitale Assets {#manage-assets-metadata}

Mit Enterprise Manager Assets können Sie die Metadaten mehrerer Assets gleichzeitig bearbeiten, sodass Sie allgemeine Metadatenänderungen an Assets zusammen vornehmen können. Auf der Seite [!UICONTROL Eigenschaften] können Sie Metadateneigenschaften in einen allgemeinen Wert ändern bzw. Tags hinzufügen oder ändern. Verwenden Sie zum Anpassen der Seite mit den Metadateneigenschaften, einschließlich Hinzufügen, Ändern und Löschen von Metadateneigenschaften, den Schemaeditor.

>[!NOTE]
>
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einem Ordner oder einer Sammlung enthalten sind. Für Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, können die [Metadaten nach einer Suche stapelweise aktualisiert werden](/help/assets/search-assets.md#metadataupdates).

1. Navigieren Sie zum Speicherort der Assets, die Sie bearbeiten möchten.
1. Wählen Sie die Assets aus, für die Sie gemeinsame Eigenschaften bearbeiten möchten.
1. Tippen oder klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**, um für die ausgewählten Assets die Seite [!UICONTROL Eigenschaften] zu öffnen.

   >[!NOTE]
   >
   >Wenn Sie mehrere Assets auswählen, wird die niedrigste gemeinsame übergeordnete Form für die Assets ausgewählt. Das heißt, die Seite [!UICONTROL Eigenschaften] zeigt nur Metadatenfelder an, die auf den Seiten [!UICONTROL Eigenschaften] aller individuellen Assets vorhanden sind.

1. Ändern Sie die Metadateneigenschaften für ausgewählte Assets auf den verschiedenen Registerkarten.
1. Heben Sie die Auswahl der anderen Assets in der Liste auf, um den Metadateneditor für ein bestimmtes Asset anzuzeigen. Die Metadateneditorfelder werden mit den Metadaten für das jeweilige Asset gefüllt.

   >[!NOTE]
   >
   >* Auf der Seite [!UICONTROL Eigenschaften] können Sie Assets aus der Asset-Liste entfernen, indem Sie die Auswahl aufheben. In der Asset-Liste sind alle Assets standardmäßig ausgewählt. Die Metadaten für Assets, die Sie aus der Liste entfernen, werden nicht aktualisiert.
   >* Aktivieren Sie über der Asset-Liste das Kontrollkästchen neben **[!UICONTROL Titel]**, um zwischen der Auswahl von Assets und dem Deaktivieren der Liste umzuschalten.


1. Wenn Sie ein anderes Metadatenschema für die Assets wählen möchten, tippen oder klicken Sie in der Symbolleiste auf **[!UICONTROL Einstellungen]** und wählen Sie das gewünschte Schema aus. Speichern Sie die Änderungen.
1. Um die neuen Metadaten mit den vorhandenen Metadatenfeldern, die mehrere Werte enthalten, anzuhängen, wählen Sie den **[!UICONTROL Anlagenmodus]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Tippen oder klicken Sie auf **[!UICONTROL Absenden]**.

   >[!CAUTION]
   >
   >Bei Feldern, die nur einen einzigen Wert enthalten, werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Anlagenmodus]** auswählen.

## Konfigurieren des Grenzwerts für die Metadaten-Massenaktualisierung {#configlimit}

Um DoS-ähnliche Situationen zu vermeiden, beschränkt AEM die Anzahl der Parameter, die in einer Sling-Anfrage unterstützt werden. Wenn Sie die Metadaten vieler Assets auf einmal aktualisieren, erreichen Sie möglicherweise den Grenzwert, sodass die Metadaten für weitere Assets nicht aktualisiert werden können. AEM generiert die folgende Warnung in den Protokollen:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Um den Grenzwert zu ändern, greifen Sie auf die Web-Konsole zu (**[!UICONTROL Tools]** > **[!UICONTROL Vorgänge]** > **[!UICONTROL Web-Konsole]**) und ändern Sie den Wert für **[!UICONTROL Maximale POST-Parameter]** unter **[!UICONTROL Apache Sling Request Parameter Handling]** der OSGi-Konfiguration.

## Metadata schemata {#metadata-schemata}

Metadaten-Schema sind vordefinierte Sätze von Metadateneigenschaftsdefinitionen, die in verschiedenen Anwendungen verwendet werden können. Eigenschaften sind immer mit einem Asset verknüpft, d. h. die Eigenschaften beziehen sich auf die Ressource.

Sie können auch eigene Metadaten-Schemata entwerfen, wenn keine vorhanden ist, die Ihren Anforderungen entsprechen. Vorhandene Informationen nicht Duplikat. Das Trennen von Schemata innerhalb eines Unternehmens erleichtert die Freigabe von Metadaten. [!DNL Experience Manager] stellt eine standardmäßige Liste der beliebtesten Metadaten-Schemata bereit. Die Liste hilft Ihnen, Ihre Metadatenstrategie zu starten und schnell die benötigten Metadateneigenschaften auszuwählen.

Die unterstützten Metadaten-Schemata sind unten aufgeführt.

### Standard metadata {#standard-metadata}

* dc - [!DNL Dublin Core] is the most important and widely used set of metadata.
* DICOM – Digital Imaging and Communications in Medicine.
* Iptc4xmpCore &amp; iptc4xmpExt - International Press Communications Standard enthält viele themenspezifische Metadaten.
* rdf – Resource Description Framework: Für generische semantische Webmetadaten.
* XMP - [!DNL Extensible Metadata Platform].
* xmpBJ – Einfaches Auftrags-Ticketing.

### Application-specific metadata {#application-specific-metadata}

Die anwendungsspezifischen Metadaten enthalten technische und beschreibende Metadaten. Diese Metadaten können unter Umständen nicht von anderen Anwendungen verwendet werden. For example, if you have an asset with [!DNL Adobe Photoshop] metadata and another image-rendering application tries to access the metadata, it may not be able to access the metadata. Wenn Sie feststellen, dass Ihre Assets viele anwendungsspezifische Metadaten enthalten, können Sie einen Workflow-Schritt erstellen, der eine anwendungsspezifische Eigenschaft in eine Standardeigenschaft ändert.

* ACDSee - Metadata managed by the [!DNL ACDSee] program. Siehe [www.acdsee.com/](https://www.acdsee.com/).
* Album - [!DNL Adobe Photoshop Album].
* cq - Used by [!DNL Experience Manager Assets].
* dam - Used by [!DNL Experience Manager Assets].
* dex: Optima SC Description Explorer.
* crs: Adobe Photoshop Camera Raw.
* lr - [!DNL Adobe Lightroom].
* mediapro: IView MediaPro.
* MicrosoftPhoto und MP: Microsoft Photo.
* pdf und pdfx.
* photoshop &amp; psAux - [!DNL Adobe Photoshop].

### Digital Rights Management metadata {#digital-rights-management-metadata}

* CC - [!DNL Creative Commons].
* [!DNL XMPRights].
* plus - [Picture Licensing Universal System](https://www.useplus.com).
* Prism - https://www.idealliance.org/prism-metadata für Veröffentlichungsanforderungen für Standard-Metadaten der Branche.
* PRL - PRISM Rights Language.
* PUR - PRISM-Nutzungsrechte.
* xmpPlus - Integration von PLUS mit XMP.

### Photography-specific metadata {#photography-specific-metadata}

* Exif - Technische Informationen von der Kamera, einschließlich GPS-Position.
* CRS - [!DNL Camera Raw] Schema.
* Iptc4xmpCore und iptc4xmpExt.
* TIFF: Bildmetadaten (nicht nur für TIFF-Bilder).

### Print-specific metadata {#print-specific-metadata}

* pdf und pdfx: Adobe PDF und Drittanbieteranwendungen.
* prism: [www.prismstandard.org](https://www.prismstandard.org) Publishing Requirements for Industry Standard Metadata.
* XMP.
* xmpPG - XMP-Metadaten für Seiten-Text.

### Multimedia-spezifische Metadaten {#multimedia-specific-metadata}

* xmpDM - [!DNL Dynamic Media].
* xmpMM: Medien-Management.

## Metadatengesteuerte Workflows {#metadata-driven-workflows}

Das Erstellen von durch Metadaten angetriebenen Workflows hilft Ihnen, einige Prozesse zu automatisieren, was die Effizienz verbessert. In einem metadatengesteuerten Workflow liest das Workflow-Managementsystem den Workflow und führt anschließend einige vordefinierte Aktionen aus. Im Folgenden finden Sie einige Beispiele für den Einsatz metadatengesteuerter Workflows:

* Der Workflow kann prüfen, ob ein Bild einen Titel hat oder nicht. Ist dies nicht der Fall, benachrichtigt das System, einen Titel hinzuzufügen.
* Der Arbeitsablauf kann prüfen, ob ein Copyright-Hinweis für ein Asset die Verteilung zulässt. Dementsprechend sendet das System das Asset an den einen oder anderen Server.
* Ein Workflow kann nach Assets ohne vordefinierte, obligatorische Metadaten oder Assets mit *ungültigen* Metadaten suchen.
