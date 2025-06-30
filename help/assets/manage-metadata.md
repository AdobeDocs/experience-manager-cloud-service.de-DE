---
title: Verwalten von Metadaten für digitale Assets
description: Erfahren Sie, welche Arten von Metadaten es gibt und wie [!DNL Adobe Experience Manager Assets] die Verwaltung von Metadaten für Assets unterstützt, um die Kategorisierung und Organisation von Assets zu erleichtern. [!DNL Experience Manager]  ermöglicht die automatische Organisation und Verarbeitung von Assets basierend auf ihren Metadaten.
contentOwner: AG
mini-toc-levels: 1
feature: Asset Management, Metadata
role: User, Architect, Admin
exl-id: 73a82bc2-1dda-4090-b7ee-29d1a632ba25
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: tm+mt
source-wordcount: '1944'
ht-degree: 100%

---

# Verwalten von Metadaten für digitale Assets {#managing-metadata-for-digital-assets}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/metadata.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

[!DNL Adobe Experience Manager Assets] speichert Metadaten für jedes Asset. Damit können Assets einfacher kategorisiert und organisiert und bestimmte Assets leichter von Benutzern gefunden werden. Metadaten können aus in [!DNL Experience Manager Assets] hochgeladenen Dateien extrahiert werden. Damit lässt sich die Metadatenverwaltung in den kreativen Workflow integrieren. Da Sie Metadaten mit den Assets speichern und verwalten können, können Sie Assets basierend auf ihren Metadaten automatisch organisieren und verarbeiten.

<!-- 
* [Metadata Schemata Reference](meta-ref.md)
-->

## Die Bedeutung von Metadaten {#why-metadata}

Metadaten sind Informationen über Daten. In dieser Hinsicht beziehen sich Daten auf Ihr digitales Asset, z. B. ein Bild. Metadaten sind für ein effizientes Asset-Management von entscheidender Bedeutung.

Metadaten stellen die Sammlung aller für ein Asset verfügbaren Daten dar, die nicht unbedingt im Bild selbst enthalten sind. Beispiele für Metadaten:

* Name des Assets.
* Uhrzeit und Datum der letzten Änderung.
* Größe des Assets bei Speicherung im Repository.
* Name des Ordners, der das Asset enthält.
* Zugehörige Assets oder angewendete Tags.

Dies sind die grundlegenden Metadaten-Eigenschaften, die [!DNL Experience Manager] für Assets verwalten kann, sodass die Benutzer alle Assets anzeigen können. Beispielsweise ist es nützlich, Assets nach dem Datum der letzten Änderung zu sortieren, wenn Sie versuchen, kürzlich hinzugefügte oder geänderte Assets zu finden.

Sie können digitalen Assets auch Daten auf höherer Ebene hinzufügen – darunter:

* Typ des Assets (Bild, Video, Audio-Clip oder Dokument).
* Inhaber des Assets.
* Titel des Assets.
* Beschreibung des Assets.
* Tags, die einem Asset zugewiesen sind.

Mit mehr Metadaten können Sie Assets genauer einteilen. Außerdem erweisen sie sich als nützlich, wenn die Menge digitaler Daten ansteigt. Es ist möglich, einige hundert Dateien nur anhand der Dateinamen zu verwalten. Dieser Ansatz ist jedoch nicht skalierbar. Er bleibt hinter den Erwartungen zurück, wenn die Zahl der beteiligten Personen und die Zahl der verwalteten Assets zunehmen.

Durch das Hinzufügen von Metadaten steigt der Wert eines digitalen Assets, da das Asset folgende Eigenschaften aufweist:

* besser zugänglich – Systeme und Benutzer können es leicht finden.
* einfacher zu verwalten – Sie können Assets mit denselben Eigenschaften einfacher finden und Änderungen auf sie anwenden.
* vollständig – Asset enthält mehr Informationen und Kontext mit mehr Metadaten.

Aus diesen Gründen erhalten Sie mit [!DNL Assets] die richtigen Mittel, um Metadaten für digitale Assets zu erstellen, zu verwalten und auszutauschen.

## Metadatentypen {#types-of-metadata}

Metadaten werden in technische, informative und administrative Metadaten eingeteilt.

### Technische Metadaten

Bei technischen Metadaten liegt der Schwerpunkt auf den technischen Aspekten digitaler Assets. Sie liefern wichtige Informationen zu Folgendem:

* Dateigröße
* Format
* Auflösung
* Abmessungen
* Farbmodus

Dieser Metadatentyp hilft Benutzenden dabei, digitale Assets zu verstehen und effizient einzusetzen.

### Informative Metadaten

Informative Metadaten bieten beschreibende Informationen, um das Verständnis von Inhalten zu verbessern, und helfen bei der Inhaltserkennung und -suche. Sie umfassen Schlüsselwörter, Beschriftungen und Beschreibungen. <br>Beispielsweise können beim Verwalten eines Videos in Experience Manager Assets die folgenden informativen Metadaten einbezogen werden:

* **Schlüsselwörter**: Marketing, Produktstart, Werbung
* **Beschriftung**: Einführung unseres neuesten Produkts mit überzeugenden Funktionen
* **Beschreibung**: Ein detaillierter Überblick über den Videoinhalt.

### Administrative Metadaten

Administrative Metadaten behandeln die verwaltungstechnischen Aspekte digitaler Assets. Sie stellen die Zugriffssteuerung, die Compliance und die Verwaltung des gesamten Lebenszyklus von Assets innerhalb des Digital Asset Management-Systems sicher. Sie umfassen Informationen zu Folgendem:

* Asset-Eigentümerschaft
* Verwendungsrechte
* Berechtigungen
* Weitere administrative Details

Dieser Metadatentyp gewährleistet einen effektiven Ablauf von Asset-Management, Zugriffssteuerung und Compliance.

<!-- Learn more about [metadata best practices](metadata-best-practices.md) to manage your digital assets effectively. -->

<!-- The two basic types of metadata are technical metadata and descriptive metadata.

Technical metadata is useful for software applications that are dealing with digital assets and should not be maintained manually. [!DNL Experience Manager Assets] and other software automatically determine technical metadata and the metadata may change when the asset is modified. The available technical metadata of an asset depends largely on the file type of the asset. Some examples of technical metadata are:

* Size of a file.
* Dimensions (height and width) of an image.
* Bit rate of an audio or video file.
* Resolution (level of detail) of an image.

Descriptive metadata is metadata concerned with the application domain, for example, the business that an asset is coming from. Descriptive metadata cannot be determined automatically. It is created manually or semi-automatically. For example, a GPS-enabled camera can automatically track the latitude and longitude and add geotag the image.

The cost of manually creating descriptive metadata information is high. So, standards are established to ease the exchange of metadata across software systems and organizations. [!DNL Experience Manager Assets] supports all relevant standards for metadata management. -->

## Metadaten und letzte Änderung {#last-modification}

Das Datum der letzten Änderung eines Assets spiegelt das letzte Mal wider, dass die Originaldatei für ein Asset geändert wurde. Folglich ändern sich das Datum der Änderung und der Benutzer, der sie vorgenommen hat, nur dann, wenn:

* Eine neue Version des Assets hochgeladen wird
* Ein Asset erneut verarbeitet wird

Das Datum der Änderung und der Benutzer, der sie vorgenommen hat, ändern sich nicht:

* Wenn ein Asset verschoben oder umbenannt wird
* Wenn ein Asset oder seine Version ausgecheckt oder eingecheckt wird
* Wenn ein Asset veröffentlicht oder seine Veröffentlichung rückgängig gemacht wird
* Bei Metadatenaktualisierungen
* Referenz- oder Sammlungsaktualisierungen

## Codierungsstandards {#encoding-standards}

Es gibt verschiedene Möglichkeiten, Metadaten in Dateien einzubetten. Dazu werden die folgenden Codierungsstandards unterstützt:

* XMP: Damit speichert [!DNL Assets] die extrahierten Metadaten im Repository.
* ID3: für Audio- und Videodateien
* EXIF: für Grafikdateien.
* Andere/Legacy: von [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel] usw.

### XMP {#xmp}

[!DNL Extensible Metadata Platform] (XMP) ist ein offener Standard, der von [!DNL Experience Manager Assets] für die gesamte Metadatenverwaltung verwendet wird. Der Standard bietet eine universelle Metadatencodierung, die in alle Dateiformate eingebettet werden kann. Adobe und andere Firmen unterstützen den XMP-Standard, da er ein umfangreiches Inhaltsmodell bietet. Benutzer des XMP-Standards und von [!DNL Experience Manager Assets] können auf einer leistungsstarken Plattform aufbauen. Weitere Informationen finden Sie unter [XMP](https://www.adobe.com/products/xmp.html).

### ID3 {#id}

In diesen ID3-Tags gespeicherte Daten werden angezeigt, wenn Sie eine digitale Audiodatei auf dem Computer oder einem tragbaren MP3-Player abspielen.

ID3-Tags wurden für das MP3-Dateiformat entwickelt. Weitere Informationen zu Formaten:

* ID3-Tags funktionieren in MP3- und mp3PRO-Dateien.
* WAV weist keine Tags auf.
* WMA verfügt über proprietäre Tags, die keine Open-Source-Implementierung zulassen.
* Ogg Vorbis nutzt Xiph-Kommentare, die in den Ogg-Container eingebettet sind.
* AAC verwendet ein proprietäres Tagging-Format.

### Exif {#exif}

Exchangeable Image File Format (Exif, austauschbares Bilddateiformat) ist das in der digitalen Fotografie am häufigsten verwendete Metadatenformat. Es bietet eine Möglichkeit, ein festes Vokabular von Metadateneigenschaften in viele Dateiformate wie JPEG, TIFF, RIFF und WAV einzubetten. Exif speichert Metadaten als Paare aus Metadatenname und Metadatenwert. Diese Name-Wert-Paare für Metadaten werden auch als „Tags“ bezeichnet, nicht zu verwechseln mit dem Tagging in [!DNL Experience Manager]. Moderne Digitalkameras erstellen Exif-Metadaten und moderne Grafik-Software unterstützt sie. Das Exif-Format ist der kleinste gemeinsame Nenner für die Metadatenverwaltung, insbesondere für Bilder.

Eine wichtige Einschränkung von Exif besteht darin, dass das Format von einigen gängigen Bilddateiformaten wie BMP, GIF oder PNG nicht unterstützt wird.

Von Exif definierte Metadatenfelder sind in der Regel technischer Natur und für die beschreibende Metadatenverwaltung nur begrenzt geeignet. Aus diesem Grund bietet [!DNL Experience Manager Assets] die Zuordnung von Exif-Eigenschaften zu [gängigen Metadaten-Schemas](metadata-schemas.md) und zu XMP.

#### Andere Metadaten {#other-metadata}

Andere Metadaten können aus Dateien von [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel] usw. eingebettet werden.

## Verwalten von Metadaten für digitale Assets {#manage-assets-metadata}

Mit Enterprise Manager Assets können Sie die Metadaten mehrerer Assets gleichzeitig bearbeiten, sodass Sie allgemeine Metadatenänderungen an Assets zusammen vornehmen können. Auf der Seite [!UICONTROL Eigenschaften] können Sie Metadateneigenschaften in einen allgemeinen Wert ändern bzw. Tags hinzufügen oder ändern. Verwenden Sie zum Anpassen der Seite mit den Metadateneigenschaften, einschließlich Hinzufügen, Ändern und Löschen von Metadateneigenschaften, den Schemaeditor.

>[!NOTE]
>
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einem Ordner oder einer Sammlung enthalten sind. Für Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, können die [Metadaten nach einer Suche stapelweise aktualisiert werden](/help/assets/search-assets.md#metadata-updates).

1. Navigieren Sie zum Speicherort der Assets, die Sie bearbeiten möchten.
1. Wählen Sie die Assets aus, für die Sie gemeinsame Eigenschaften bearbeiten möchten.
1. Wählen Sie auf der Symbolleiste **[!UICONTROL Eigenschaften]** aus, um für die ausgewählten Assets die Seite [!UICONTROL Eigenschaften] zu öffnen.

   >[!NOTE]
   >
   >Wenn Sie mehrere Assets auswählen, wird die niedrigste gemeinsame übergeordnete Form für die Assets ausgewählt. Das heißt, die Seite [!UICONTROL Eigenschaften] zeigt nur Metadatenfelder an, die auf den Seiten [!UICONTROL Eigenschaften] aller individuellen Assets vorhanden sind.

1. Ändern Sie die Metadateneigenschaften für ausgewählte Assets auf den verschiedenen Registerkarten.
1. Heben Sie die Auswahl der anderen Assets in der Liste auf, um den Metadaten-Editor für ein bestimmtes Asset anzuzeigen. Die Metadateneditorfelder werden mit den Metadaten für das jeweilige Asset gefüllt.

   >[!NOTE]
   >
   >* Auf der Seite [!UICONTROL Eigenschaften] können Sie Assets aus der Asset-Liste entfernen, indem Sie die Auswahl aufheben. In der Asset-Liste sind alle Assets standardmäßig ausgewählt. Die Metadaten für Assets, die Sie aus der Liste entfernen, werden nicht aktualisiert.
   >* Aktivieren Sie über der Asset-Liste das Kontrollkästchen neben **[!UICONTROL Titel]**, um zwischen der Auswahl von Assets und dem Deaktivieren der Liste umzuschalten.

1. Wenn Sie ein anderes Metadatenschema für die Assets wählen möchten, wählen Sie in der Symbolleiste **[!UICONTROL Einstellungen]** und anschließend das gewünschte Schema aus. Speichern Sie die Änderungen.
1. Um die neuen Metadaten mit den vorhandenen Metadatenfeldern, die mehrere Werte enthalten, anzuhängen, wählen Sie den **[!UICONTROL Anlagenmodus]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Wählen Sie **[!UICONTROL Absenden]**.

   >[!CAUTION]
   >
   >Bei Feldern, die nur einen einzigen Wert enthalten, werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Anlagenmodus]** auswählen.

## Benutzerdefinierte Metadaten unter Verwendung eines Verarbeitungsprofils {#metadata-compute-service}

Assets as a [!DNL Cloud Service] kann mithilfe von Cloud-nativen Services benutzerdefinierte Metadaten für ein Asset generieren. Konfigurieren Sie ein Verarbeitungsprofil, um benutzerdefinierte Metadaten zu generieren. Erfahren Sie, [wie Sie Verarbeitungsprofile verwenden](/help/assets/asset-microservices-configure-and-use.md#use-profiles).

![Metadaten-Ausgabedarstellung im Verarbeitungsprofil](assets/processing-profile-metadata.png)

>[!TIP]
>
>Auf einen Ordner kann nur ein Verarbeitungsprofil angewendet werden. Fügen Sie einem einzelnen Verarbeitungsprofil weitere Optionen hinzu, um mehrere Verarbeitungsschritte auf Assets in einem Ordner anzuwenden. Ein einzelnes Profil kann beispielsweise Ausgabedarstellungen generieren, Assets umkodieren, benutzerdefinierte Metadaten generieren usw. Sie können für jede Aufgabe MIME-Filter anwenden, sodass die entsprechende Aufgabe für das erforderliche Dateiformat ausgelöst wird.

<!-- TBD: Commenting as Web Console is not available. Document the appropriate OSGi config method if available in CS.

## Configure limit for bulk metadata update {#configlimit}

To prevent DOS-like situation, [!DNL Experience Manager] limits the number of parameters supported in a Sling request. When updating metadata of many assets in one go, you may reach the limit and the metadata does not get updated for more assets. [!DNL Experience Manager] generates the following warning in the logs:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

To change the limit, access Web Console ( **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**) and change the value of **[!UICONTROL Maximum POST Parameters]** in **[!UICONTROL Apache Sling Request Parameter Handling]** OSGi configuration.
-->

## Metadatenschemas {#metadata-schemata}

Metadatenschemas sind vordefinierte Sets aus Metadaten-Eigenschaftsdefinitionen, die in verschiedenen Programmen eingesetzt werden können. Eigenschaften sind stets mit einem Asset verknüpft. Das heißt, die Eigenschaften beziehen sich auf die Ressource.

Sie können auch Ihre eigenen Metadatenschemata entwerfen, falls die vorhandenen Ihren Anforderungen nicht entsprechen. Duplizieren Sie keine vorhandenen Informationen. Innerhalb eines Unternehmens kann die Freigabe von Metadaten durch eine Trennung der Schemata erleichtert werden. [!DNL Experience Manager] stellt eine standardmäßige Liste der beliebtesten Metadatenschemata bereit. Die Liste hilft Ihnen, Ihre Metadatenstrategie zu starten und schnell die benötigten Metadateneigenschaften auszuwählen.

Die unterstützten Metadatenschemata sind unten aufgeführt.

### Standardmetadaten {#standard-metadata}

* DC – [!DNL Dublin Core] ist ein wichtiger und häufig verwendeter Metadatensatz.
* DICOM – Digital Imaging and Communications in Medicine.
* `Iptc4xmpCore` und `iptc4xmpExt` – Internationaler Standard für Pressekommunikation, enthält viele themenspezifische Metadaten.
* RDF – Resource Description Framework: Für generische semantische Web-Metadaten.
* XMP – [!DNL Extensible Metadata Platform].
* `xmpBJ` – Einfaches Job-Ticketing.

### Programmspezifische Metadaten {#application-specific-metadata}

Die programmspezifischen Metadaten umfassen technische und beschreibende Metadaten. Diese Metadaten können unter Umständen nicht von anderen Programmen verwendet werden. Beispielsweise kann ein anderes Programm zum Rendern von Bildern möglicherweise nicht auf [!DNL Adobe Photoshop]-Metadaten zugreifen. Sie können einen Workflow-Schritt erstellen, der eine programmspezifische Eigenschaft in eine Standardeigenschaft ändert.

* ACDSee – Vom [!DNL ACDSee]-Programm verwaltete Metadaten. Siehe [www.acdsee.com/](https://www.acdsee.com/).
* Album – [!DNL Adobe Photoshop Album].
* CQ – Von [!DNL Experience Manager Assets] verwendet.
* DAM – Von [!DNL Experience Manager Assets] verwendet.
* DEX – [Optima SC Description Explorer](https://www.optimasc.com/products/dex/index.html) ist eine Sammlung von Tools zur Metadaten- und Dateiverwaltung für Windows-Betriebssysteme.
* CRS – [Adobe Photoshop Camera Raw](https://helpx.adobe.com/de/camera-raw/using/introduction-camera-raw.html).
* LR – [!DNL Adobe Lightroom].
* MediaPro – [iView MediaPro](https://de.wikipedia.org/wiki/Phase_One_Media_Pro).
* MicrosoftPhoto und MP – Microsoft Photo.
* PDF und PDF/X.
* Photoshop und psAux – [!DNL Adobe Photoshop].

### Digital Rights Management-Metadaten {#digital-rights-management-metadata}

* CC – [!DNL Creative Commons].
* [!DNL XMPRights].
* PLUS – [Picture Licensing Universal System](https://www.useplus.com).
<!--THIS LINK IS 404 WITH NO SUITABLE REPLACEMENT * PRISM - [Publishing Requirements for Industry Standard Metadata](https://www.idealliance.org/prism-metadata). -->
* PRL – PRISM Rights Language.
* PUR – PRISM Usage Rights.
* `xmpPlus` – Integration von PLUS in XMP.

### Fotografiespezifische Metadaten {#photography-specific-metadata}

* Exif – Technische Informationen von der Kamera, einschließlich GPS-Position.
* CRS – [!DNL Camera Raw]-Schema.
* `iptc4xmpCore` und `iptc4xmpExt`.
* TIFF – Bildmetadaten (nicht nur für TIFF-Bilder).

### Druckspezifische Metadaten {#print-specific-metadata}

* PDF und PDF/X – Adobe PDF und Drittanbieterprogramme.
<!--THIS LINK IS 404 WITH NO SUITABLE REPLACEMENT * PRISM - [Publishing Requirements for Industry Standard Metadata](https://www.idealliance.org/prism-metadata). -->
* XMP – [!DNL Extensible Metadata Platform].
* `xmpPG` – XMP-Metadaten für Seitentext.

### Multimedia-spezifische Metadaten {#multimedia-specific-metadata}

* `xmpDM` – [!DNL Dynamic Media].
* `xmpMM` – Medienverwaltung.

## Metadatengesteuerte Workflows {#metadata-driven-workflows}

Mit der Erstellung von metadatengesteuerten Workflows können Sie einige Prozesse automatisieren und so die Effizienz steigern. In einem metadatengesteuerten Workflow liest das Workflow-Management-System den Workflow und führt anschließend einige vordefinierte Aktionen aus. Im Folgenden finden Sie einige Beispiele für den Einsatz metadatengesteuerter Workflows:

* Der Workflow kann prüfen, ob ein Bild einen Titel aufweist. Falls nicht, fordert das System auf, einen Titel hinzuzufügen.
* Der Workflow kann prüfen, ob ein Copyright-Hinweis für ein Asset dessen Verteilung zulässt. Das System sendet das Asset also an den einen oder den anderen Server.
* Ein Workflow kann auf Assets ohne vordefinierte, obligatorische Metadaten oder Assets mit *ungültigen* Metadaten prüfen.

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [XMP-Metadaten](xmp-metadata.md)
>* [Anleitung zum Bearbeiten oder Hinzufügen von Metadaten](meta-edit.md)
