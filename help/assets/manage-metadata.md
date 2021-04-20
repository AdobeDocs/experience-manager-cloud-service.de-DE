---
title: Verwalten von Metadaten für digitale Assets
description: Erfahren Sie mehr über die Metadatentypen und wie [!DNL Adobe Experience Manager Assets] helps manage metadata for assets to allow easier categorization and organization of assets. [!DNL Experience Manager] Assets automatisch basierend auf ihren Metadaten organisiert und verarbeitet werden können.
contentOwner: AG
mini-toc-levels: 1
feature: Asset Management,Metadata
role: Business Practitioner,Architect,Administrator
translation-type: tm+mt
source-git-commit: 6fa911f39d707687e453de270bc0f3ece208d380
workflow-type: tm+mt
source-wordcount: '1861'
ht-degree: 97%

---


# Verwalten von Metadaten für digitale Assets {#managing-metadata-for-digital-assets}

[!DNL Adobe Experience Manager Assets] speichert Metadaten für jedes Asset. Damit können Assets einfacher kategorisiert und organisiert und bestimmte Assets leichter von Benutzern gefunden werden. Metadaten können aus in [!DNL Experience Manager Assets] hochgeladenen Dateien extrahiert werden. Damit lässt sich die Metadatenverwaltung in den kreativen Workflow integrieren. Da Sie Metadaten mit den Assets speichern und verwalten können, können Sie Assets basierend auf ihren Metadaten automatisch organisieren und verarbeiten.

>[!MORELIKETHIS]
>
>* [XMP-Metadaten](xmp-metadata.md)
>* [Anleitung zum Bearbeiten oder Hinzufügen von Metadaten](meta-edit.md)


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

Dies sind die grundlegenden Metadaten-Eigenschaften, die [!DNL Experience Manager] für Assets verwalten kann, sodass die Benutzer alle Assets anzeigen können. Beispielsweise ist es nützlich, Assets nach dem Datum der letzten Änderung zu ordnen, wenn Sie versuchen, kürzlich hinzugefügte Assets zu finden.

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

Die beiden grundlegenden Metadatentypen sind technische Metadaten und beschreibende Metadaten.

Technische Metadaten eignen sich für Software-Anwendungen, die mit digitalen Assets arbeiten und nicht manuell gepflegt werden sollen. [!DNL Experience Manager Assets] und andere Software ermitteln technische Metadaten automatisch. Die Metadaten können sich ändern, wenn das Asset geändert wird. Die verfügbaren technischen Metadaten für ein Asset hängen größtenteils vom Dateityp des Assets ab. Beispiele für technische Metadaten:

* Größe einer Datei.
* Abmessungen (Höhe und Breite) eines Bildes.
* Bitrate einer Audio- oder Videodatei.
* Auflösung (Detaillierungsgrad) eines Bildes.

Beschreibende Metadaten sind solche, die sich auf die Anwendungsdomäne beziehen – etwa das Unternehmen, aus dem ein Asset stammt. Beschreibende Metadaten können nicht automatisch bestimmt werden. Sie werden manuell oder halbautomatisch erstellt. Beispielsweise kann eine GPS-fähige Kamera automatisch den Längen- und Breitengrad verfolgen und das Bild mit einem Geotag versehen.

Die Kosten für die manuelle Erstellung beschreibender Metadateninformationen sind hoch. Daher werden Standards festgelegt, um den Austausch von Metadaten zwischen Software-Systemen und Organisationen zu erleichtern. [!DNL Experience Manager Assets] unterstützt alle relevanten Standards für die Metadatenverwaltung.

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

Exchangeable Image File Format (Exif, austauschbares Bilddateiformat) ist das in der digitalen Fotografie am häufigsten verwendete Metadatenformat. Es bietet eine Möglichkeit, ein festes Vokabular von Metadateneigenschaften in viele Dateiformate wie JPEG, TIFF, RIFF und WAV einzubetten. Exif speichert Metadaten als Paare aus Metadatenname und Metadatenwert. Die Name/Wert-Paare für Metadaten werden auch als Tags bezeichnet (nicht zu verwechseln mit dem Tagging in [!DNL Experience Manager]). Moderne Digitalkameras erstellen Exif-Metadaten und moderne Grafik-Software unterstützt sie. Das Exif-Format ist der kleinste gemeinsame Nenner für die Metadatenverwaltung, insbesondere für Bilder.

Eine wichtige Einschränkung von Exif besteht darin, dass das Format von einigen gängigen Bilddateiformaten wie BMP, GIF oder PNG nicht unterstützt wird.

Von Exif definierte Metadatenfelder sind in der Regel technischer Natur und für die beschreibende Metadatenverwaltung nur begrenzt geeignet. Aus diesem Grund bietet [!DNL Experience Manager Assets] die Zuordnung von Exif-Eigenschaften zu [gängigen Metadaten-Schemata](metadata-schemas.md) und zu XMP.

#### Andere Metadaten {#other-metadata}

Andere Metadaten können aus Dateien von [!DNL Microsoft Word], [!DNL PowerPoint], [!DNL Excel] usw. eingebettet werden.

## Verwalten von Metadaten für digitale Assets {#manage-assets-metadata}

Mit Enterprise Manager Assets können Sie die Metadaten mehrerer Assets gleichzeitig bearbeiten, sodass Sie allgemeine Metadatenänderungen an Assets zusammen vornehmen können. Auf der Seite [!UICONTROL Eigenschaften] können Sie Metadateneigenschaften in einen allgemeinen Wert ändern bzw. Tags hinzufügen oder ändern. Verwenden Sie zum Anpassen der Seite mit den Metadateneigenschaften, einschließlich Hinzufügen, Ändern und Löschen von Metadateneigenschaften, den Schemaeditor.

>[!NOTE]
>
>Die Massenbearbeitung kann auf Assets angewendet werden, die in einem Ordner oder einer Sammlung enthalten sind. Für Assets, die in verschiedenen Ordnern enthalten sind oder gemeinsamen Kriterien entsprechen, können die [Metadaten nach einer Suche stapelweise aktualisiert werden](/help/assets/search-assets.md#metadata-updates).

1. Navigieren Sie zum Speicherort der Assets, die Sie bearbeiten möchten.
1. Wählen Sie die Assets aus, für die Sie gemeinsame Eigenschaften bearbeiten möchten.
1. Tippen oder klicken Sie in der Symbolleiste auf **[!UICONTROL Eigenschaften]**, um für die ausgewählten Assets die Seite [!UICONTROL Eigenschaften] zu öffnen.

   >[!NOTE]
   >
   >Wenn Sie mehrere Assets auswählen, wird die niedrigste gemeinsame übergeordnete Form für die Assets ausgewählt. Das heißt, die Seite [!UICONTROL Eigenschaften] zeigt nur Metadatenfelder an, die auf den Seiten [!UICONTROL Eigenschaften] aller individuellen Assets vorhanden sind.

1. Ändern Sie die Metadateneigenschaften für ausgewählte Assets auf den verschiedenen Registerkarten.
1. Um den Metadaten-Editor für ein bestimmtes Asset Ansicht, brechen Sie die Auswahl der verbleibenden Assets in der Liste ab. Die Metadateneditorfelder werden mit den Metadaten für das jeweilige Asset gefüllt.

   >[!NOTE]
   >
   >* Auf der Seite [!UICONTROL Eigenschaften] können Sie Assets aus der Asset-Liste entfernen, indem Sie die Auswahl abbrechen. In der Asset-Liste sind alle Assets standardmäßig ausgewählt. Die Metadaten für Assets, die Sie aus der Liste entfernen, werden nicht aktualisiert.
   >* Aktivieren Sie über der Asset-Liste das Kontrollkästchen neben **[!UICONTROL Titel]**, um zwischen der Auswahl von Assets und dem Deaktivieren der Liste umzuschalten.


1. Wenn Sie ein anderes Metadatenschema für die Assets wählen möchten, tippen oder klicken Sie in der Symbolleiste auf **[!UICONTROL Einstellungen]** und wählen Sie das gewünschte Schema aus. Speichern Sie die Änderungen.
1. Um die neuen Metadaten mit den vorhandenen Metadatenfeldern, die mehrere Werte enthalten, anzuhängen, wählen Sie den **[!UICONTROL Anlagenmodus]**. Wenn Sie diese Option nicht auswählen, ersetzen die neuen Metadaten die vorhandenen Metadaten in den entsprechenden Feldern. Tippen oder klicken Sie auf **[!UICONTROL Absenden]**.

   >[!CAUTION]
   >
   >Bei Feldern, die nur einen einzigen Wert enthalten, werden die neuen Metadaten nicht an den vorhandenen Wert im Feld angehängt, selbst wenn Sie **[!UICONTROL Anlagenmodus]** auswählen.

## Benutzerdefinierte Metadaten mithilfe eines Verarbeitungsprofils {#metadata-compute-service}

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

## Metadatenschemata {#metadata-schemata}

Metadatenschemata sind vordefinierte Sets aus Metadaten-Eigenschaftsdefinitionen, die in verschiedenen Programmen eingesetzt werden können. Eigenschaften sind stets mit einem Asset verknüpft. Das heißt, die Eigenschaften beziehen sich auf die Ressource.

Sie können auch Ihre eigenen Metadatenschemata entwerfen, falls die vorhandenen Ihren Anforderungen nicht entsprechen. Duplizieren Sie keine vorhandenen Informationen. Innerhalb eines Unternehmens kann die Freigabe von Metadaten durch eine Trennung der Schemata erleichtert werden. [!DNL Experience Manager] stellt eine standardmäßige Liste der beliebtesten Metadatenschemata bereit. Die Liste hilft Ihnen, Ihre Metadatenstrategie zu starten und schnell die benötigten Metadateneigenschaften auszuwählen.

Die unterstützten Metadatenschemata sind unten aufgeführt.

### Standardmetadaten {#standard-metadata}

* DC – [!DNL Dublin Core] ist ein wichtiger und häufig verwendeter Metadatensatz.
* DICOM – Digital Imaging and Communications in Medicine.
* `Iptc4xmpCore` und `iptc4xmpExt` – Internationaler Standard für Pressekommunikation, enthält viele themenspezifische Metadaten.
* RDF – Resource Description Framework: Für generische semantische Web-Metadaten.
* XMP – [!DNL Extensible Metadata Platform].
* `xmpBJ` – Einfaches Job-Ticketing.

### Anwendungsspezifische Metadaten {#application-specific-metadata}

Die anwendungsspezifischen Metadaten umfassen technische und beschreibende Metadaten. Diese Metadaten können unter Umständen nicht von anderen Anwendungen verwendet werden. Beispielsweise kann eine andere Anwendung zum Rendern von Bildern möglicherweise nicht auf [!DNL Adobe Photoshop]-Metadaten zugreifen. Sie können einen Workflow-Schritt erstellen, der eine anwendungsspezifische Eigenschaft in eine Standardeigenschaft ändert.

* ACDSee – Vom [!DNL ACDSee]-Programm verwaltete Metadaten. Siehe [www.acdsee.com/](https://www.acdsee.com/).
* Album – [!DNL Adobe Photoshop Album].
* CQ – Von [!DNL Experience Manager Assets] verwendet.
* DAM – Von [!DNL Experience Manager Assets] verwendet.
* DEX – [Optima SC Description Explorer](http://www.optimasc.com/products/dex/index.html) ist eine Sammlung von Tools zur Metadaten- und Dateiverwaltung für Windows-Betriebssysteme.
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
* PRISM – [Publishing Requirements for Industry Standard Metadata](https://www.idealliance.org/prism-metadata).
* PRL – PRISM Rights Language.
* PUR – PRISM Usage Rights.
* `xmpPlus` – Integration von PLUS in XMP.

### Fotografiespezifische Metadaten {#photography-specific-metadata}

* Exif – Technische Informationen von der Kamera, einschließlich GPS-Position.
* CRS – [!DNL Camera Raw]-Schema.
* `iptc4xmpCore` und `iptc4xmpExt`.
* TIFF – Bildmetadaten (nicht nur für TIFF-Bilder).

### Druckspezifische Metadaten {#print-specific-metadata}

* PDF und PDF/X – Adobe PDF und Drittanbieteranwendungen.
* PRISM – [Publishing Requirements for Industry Standard Metadata](https://www.idealliance.org/prism-metadata).
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
