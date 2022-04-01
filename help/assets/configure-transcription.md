---
title: Transaktionsdienst konfigurieren
seo-title: Configure transcription service
description: Adobe Experience Manager Assets ist mit [!DNL Azure Media Services] , wodurch automatisch ein Texttranskript der gesprochenen Sprache in einer unterstützten Audio- oder Videodatei im WebVTT-Format (VTT) generiert wird.
seo-description: When an audio or video asset is processed in Experience Manager Assets, the AI-based transcription service automatically generates the text transcript rendition of the audio or video asset and stores it at the same location within your Assets repository where the original asset resides. The Experience Manager Assets transcription service allows marketers to effectively manage their audio and video content with added discoverability of the text content as well as increase the ROI of these assets by supporting accessibility and localization.
products: SG_EXPERIENCEMANAGER/ASSETS and Experience Manager as a Cloud Service
sub-product: assets
content-type: reference
contentOwner: Vishabh Gupta
topic-tags: Configuration
feature: Asset Management, Configuration
role: Admin
source-git-commit: feef8159a01393baebe11c014ae6093b79df72d1
workflow-type: tm+mt
source-wordcount: '1666'
ht-degree: 3%

---


# Konfigurieren der Übertragung in [!DNL Experience Manager Assets] {#configure-transcription-service}

Transkription ist der Prozess der Übersetzung des Audioinhalts aus einer Audio- oder Videodatei in Text (Sprache in Text) mithilfe der Spracherkennungstechnologie.
[!DNL Adobe Experience Manager Assets] konfiguriert wurde mit [!DNL Azure Media Services] , wodurch automatisch ein Texttranskript der gesprochenen Sprache in einer unterstützten Audio- oder Videodatei im WebVTT-Format (.vtt) generiert wird. Wenn ein Audio- oder Video-Asset in [!DNL Experience Manager Assets], generiert der Transkriptionsdienst automatisch die Texttranskriptdarstellung des Audio- oder Video-Assets und speichert sie an demselben Speicherort in Ihrem Assets-Repository, in dem sich das Original-Asset befindet. Die [!DNL Experience Manager Assets] Mit dem Transkriptionsdienst können Marketingexperten ihren Audio- und Videoinhalt effektiv verwalten, indem sie die zusätzliche Auffindbarkeit des Textinhalts sicherstellen und den ROI dieser Assets erhöhen, indem sie Barrierefreiheit und Lokalisierung unterstützen.

Transkripte sind Textversionen gesprochener Inhalte; Ein Beispiel ist ein Film, den Sie auf jeder OTT-Plattform ansehen, der häufig Untertitel oder Untertitel enthält, um die Barrierefreiheit zu verbessern oder den Inhalt in anderen Sprachen zu verwenden. Oder eine Audio- oder Videodatei, die für Marketing-, Lern- oder Unterhaltungszwecke verwendet wird. Diese Erlebnisse beginnen mit einer Transkription, die dann entsprechend formatiert oder übersetzt wird. Das Transskribieren von Audio oder Video ist bei manueller Ausführung zeitintensiv und fehleranfällig. Angesichts des immer größeren Bedarfs an Audio-Video-Inhalten ist es auch eine Herausforderung, den manuellen Prozess zu skalieren. [!DNL Experience Manager Assets] verwendet die AI-basierte Transkription von Azure, die eine groß angelegte Verarbeitung der Audio- und Video-Assets ermöglicht und die Text-Transkripte (.vtt-Dateien) zusammen mit den Zeitstempeldetails generiert. Neben Assets wird die Transkriptionsfunktion auch in Dynamic Media unterstützt.

Die Transkriptionsfunktion ist ohne Kosten in [!DNL Experience Manager Assets]. Die Administratoren benötigen jedoch die Azure-Anmeldeinformationen des Benutzers, um den Transkriptionsdienst in [!DNL Experience Manager Assets]. Sie können auch [Testberechtigungen abrufen](https://azure.microsoft.com/en-us/pricing/details/media-services/) direkt von Microsoft® aus, um die Audio- oder Videotranskriptionsfunktion in Assets zu erleben.

## Voraussetzungen für die Übertragung {#prerequisites}

1. Eine betriebsbereite [!DNL Experience Manager Assets as a Cloud Service] -Instanz.
1. Die folgenden Azure-Anmeldeinformationen sind für die Konfiguration in [!DNL Experience Manager Assets]:

   * Client-ID (API-Schlüssel)
   * Client-Geheimschlüssel
   * Mandanten-Endpunkt (Domäne)
   * Medienkonto
   * Ressourcengruppe
   * Abonnement-ID

   Siehe [Azure-Dokumentation](https://docs.microsoft.com/en-us/azure/media-services/latest/access-api-howto?tabs=portal) , um Anmeldeinformationen für den Zugriff auf die Azure Media Services-API zu erhalten.

1. Stellen Sie sicher, dass das Azure-Konto über eine ausreichende Gewichtung für die Verarbeitung neuer Anforderungen verfügt.

## Konfigurieren der Übertragung in [!DNL Experience Manager Assets] {#configure-transcription}

Die folgenden Konfigurationen sind erforderlich, um die Transkriptionsfunktion in [!DNL Experience Manager Assets]:

1. [Azure Media Services konfigurieren](#configure-azure-media-service)
1. [Konfigurieren des Verarbeitungsprofils für die Audio-/Videotranskription](#configure-processing-profile-for-transcription)


### Azure Media Services konfigurieren {#configure-azure-media-services}

[!DNL Experience Manager Assets] verwendet die [!DNL Azure Media Services] , wodurch automatisch Texttranskripte der gesprochenen Sprache in einer [unterstützte Audio- oder Videodatei](#supported-file-formats-for-transcription) im WebVTT-Format (.vtt). Administratoren können [!DNL Azure Media Services] in [!DNL Experience Manager Assets] mit den Azure-Anmeldeinformationen. Die [Voraussetzungen für die Transkription](#transcription-prerequisites) Liste [!DNL Azure] Anmeldedaten, die für die Konfiguration erforderlich sind. Wenn Sie [!DNL Azure] Konto und Anmeldedaten, siehe [Azure Media Services - Dokumentation](https://azure.microsoft.com/en-us/pricing/details/media-services/) , um Testberechtigungen zu erhalten.

![configure-transcription-service](assets/configure-transcription-service.png)

Navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure Media Services-Konfiguration]**. Wählen Sie in der linken Leiste einen Ordner (Speicherort) aus und klicken Sie auf die Schaltfläche [!UICONTROL Erstellen] Schaltfläche zum Konfigurieren der Verbindung mit [!DNL Azure] -Konto. Dieser Ordner ist der Speicherort, an dem Ihre [!DNL Azure] Die Cloud-Konfiguration wird in Experience Manager Assets gespeichert. Geben Sie die [!DNL Azure] Anmeldedaten und klicken Sie auf **[!UICONTROL Speichern und schließen]**.

### Konfigurieren des Verarbeitungsprofils für die Übertragung {#configure-processing-profile}

Einmal [!DNL Azure Media Services] in Experience Manager Assets konfiguriert ist, besteht der nächste Schritt darin, ein Asset-Verarbeitungsprofil zum Generieren einer KI-basierten Transkription der Audio- und Video-Assets zu erstellen. Das KI-basierte Verarbeitungsprofil generiert Transkripte der [unterstütztes Audio- oder Video-Asset](#supported-file-formats-for-transcription) als Ausgabedarstellung in Experience Manager Assets verwenden und das Transkript (.vtt-Datei) in demselben Ordner speichern, in dem sich das Original-Asset befindet. Somit ist es für die Benutzer einfacher, das Asset und seine Transkriptausgabe zu suchen und zu finden.

Navigieren Sie zu **[!UICONTROL Instrumente]** > **[!UICONTROL Assets]** > **[!UICONTROL Verarbeitungsprofile]** und klicken Sie auf **[!UICONTROL Erstellen]** -Schaltfläche, um ein KI-basiertes Verarbeitungsprofil zur Generierung der Transkription Ihrer Audio- und Videodateien zu erstellen. Standardmäßig spiegelt die Seite mit dem Verarbeitungsprofil nur drei Registerkarten wider (Bild, Video und Benutzerdefiniert). Jedoch kann eine **[!UICONTROL Content-KI]** ist sichtbar, wenn Sie [!DNL Azure Media Services] in [!DNL Experience Manager Assets] -Instanz. Überprüfen Sie Ihre [!DNL Azure] Anmeldedaten, wenn die **[!UICONTROL Content-KI]** beim Erstellen eines Verarbeitungsprofils.

Im **[!UICONTROL Content-KI]** klicken Sie auf die **[!UICONTROL Neu hinzufügen]** Schaltfläche zum Konfigurieren der Transkription. Hier können Sie die Dateiformate (MIME-Typen) zum Generieren von Transkripten ein- und ausschließen, indem Sie Dateitypen aus der Dropdown-Liste auswählen. In der folgenden Abbildung werden alle unterstützten Audio- und Videodateien eingeschlossen und die Textdateien ausgeschlossen.

Aktivieren Sie die **[!UICONTROL VTT-Transkript im selben Verzeichnis erstellen]** Umschalten, um die Transkript-Ausgabedarstellung (.vtt-Datei) in demselben Ordner zu erstellen und zu speichern, in dem sich das Original-Asset befindet. Die anderen Ausgabedarstellungen werden auch vom standardmäßigen DAM-Asset-Verarbeitungs-Workflow generiert, unabhängig von dieser Einstellung.

![configure-transcription-service](assets/configure-transcription-profile.png)

Die folgende Abbildung zeigt ein benutzerdefiniertes Videoprofil, das in Experience Manager Assets erstellt wird.

![configure-transcription-service](assets/video-processing-profile.png)

Das Videoprofil enthält außerdem die folgenden benutzerdefinierten Konfigurationen. Siehe [Verarbeitungsprofildokumentation](/help/assets/asset-microservices-configure-and-use.md) für Details zum Erstellen eines benutzerdefinierten Verarbeitungsprofils.

![configure-transcription-service](assets/video-processing-profile2.png)

Konfigurieren wir nun die Transkription in diesem Videoprofil. Navigieren Sie zum **[!UICONTROL Content-KI]** und klicken Sie auf **[!UICONTROL Neu hinzufügen]** Schaltfläche. Schließen Sie alle Audio- und Videodateien ein und schließen Sie die Bild- und Anwendungsdateien aus. Aktivieren Sie die **[!UICONTROL VTT-Transkript im selben Verzeichnis erstellen]** die Konfiguration ein- und speichern.

![configure-transcription-service](assets/video-processing-profile1.png)

Nachdem das Verarbeitungsprofil für die Übertragung von Audio- und Videodateien konfiguriert wurde, können Sie dieses Verarbeitungsprofil mit einer der folgenden Methoden auf Ordner anwenden:

* Wählen Sie die Definition eines Verarbeitungsprofils in **[!UICONTROL Instrumente]** > **[!UICONTROL Assets]** > **[!UICONTROL Verarbeitungsprofile]** und verwenden **[!UICONTROL Profil auf Ordner anwenden]** Aktion. Mit dem Inhaltsbrowser können Sie zu einem bestimmten Ordner navigieren, Ordner auswählen und die Anwendung des Profils bestätigen.
* Wählen Sie einen Ordner in der Assets-Benutzeroberfläche aus und klicken Sie auf **[!UICONTROL Eigenschaften]** Aktion zum Öffnen der Ordnereigenschaften. Klicken Sie auf **[!UICONTROL Asset-Verarbeitung]** und wählen Sie das entsprechende Verarbeitungsprofil für den Ordner aus dem **[!UICONTROL Verarbeitungsprofil]** Liste. Klicken Sie auf **[!UICONTROL Speichern und schließen]**, um die Änderungen zu speichern.

   ![configure-transcription-service](assets/video-processing-profile3.png)

* Benutzer können Ordner oder bestimmte Assets in der Assets-Benutzeroberfläche auswählen, um ein Verarbeitungsprofil anzuwenden, und dann **[!UICONTROL Assets erneut verarbeiten]** aus den oben verfügbaren Optionen.

>[!TIP]
>Auf einen Ordner kann nur ein Verarbeitungsprofil angewendet werden.
>
>Nachdem ein Verarbeitungsprofil auf einen Ordner angewendet wurde, werden alle neuen Assets, die in diesen Ordner oder dessen Unterordnern hochgeladen (oder aktualisiert) wurden, mit dem konfigurierten zusätzlichen Verarbeitungsprofil verarbeitet. Diese Verarbeitung erfolgt zusätzlich zum Standardprofil.

>[!NOTE]
>
>Ein Verarbeitungsprofil, das auf einen Ordner angewendet wird, funktioniert für die gesamte Struktur. Es kann jedoch mit einem anderen Profil überschrieben werden, das auf einen Unterordner angewendet wird.
>
>Wenn Assets in einen Ordner hochgeladen werden, kommuniziert der Experience Manager mit den Eigenschaften des übergeordneten Ordners, um das Verarbeitungsprofil zu identifizieren. Wenn nichts angewendet wird, wird in einem übergeordneten Ordner in der Hierarchie geprüft, ob ein Verarbeitungsprofil angewendet werden soll.


## Transkription Ihrer Audio- oder Video-Assets generieren {#generate-transcription}

Bei der Verarbeitung eines Video-Assets wird die [KI-basiertes Verarbeitungsprofil](#configure-processing-profile-for-transcription) generiert automatisch das Transkript (.vtt-Datei) als Ausgabedarstellung zusammen mit dem Original-Asset im selben Ordner.

![configure-transcription-service](assets/transcript1.png)

Sie können das Transkript-Ausgabeformat auch anzeigen, indem Sie auf die Ausgabeformate des Original-Video-Assets zugreifen. So greifen Sie auf die **[!UICONTROL Ausgabeformate]** -Bedienfeld, wählen Sie das Original-Video-Asset aus und öffnen Sie die linke Leiste. Sie können sehen, dass die Transkriptausgabe (.vtt-Datei) unter der **[!UICONTROL TRANSCRIPTVTT]** Kopf.

![configure-transcription-service](assets/transcript.png)

Sie können das Transkript (.vtt-Textdatei) direkt aus dem Ordner als separate Asset-Ausgabedarstellung oder aus dem Ordner **[!UICONTROL Ausgabeformate]** des ursprünglichen Assets durch Herunterladen aller Ausgabeformate des Assets.

Derzeit unterstützt Experience Manager keine native Volltextvorschau oder Bearbeitung von VTT-Dateien. Sie können jedoch die Transkriptausgabe herunterladen und einen beliebigen Texteditor verwenden, um das Transkript zu bearbeiten oder zu überprüfen. Das Transkript spiegelt die gesprochene Sprache als Text zum angegebenen Zeitstempel im Video mit dem Konfidenzwert (Genauigkeit) der Transkription wider.

![configure-transcription-service](assets/transcript-text.png)

## Verwendung von Transkripten in Dynamic Media {#using-transcription-in-dynamic-media}

Wenn Sie [konfigurierte Dynamic Media](/help/assets/dynamic-media/config-dm.md) in Ihrer Experience Manager Assets-Instanz können Sie das Asset (Audio- oder Videodatei) und das zugehörige Transkript (.vtt-Datei) in Dynamic Media veröffentlichen. Dadurch werden das ursprüngliche Asset (Audio- oder Videodatei) und die transkribierte Ausgabedarstellung (VTT-Datei) im selben Ordner in Dynamic Media veröffentlicht. Der Dynamic Media-Administrator kann [CC-Erlebnis mit geschlossener Beschriftung aktivieren](/help/assets/dynamic-media/video.md#adding-captions-to-video) für die Audio- oder Videodatei mit der Transkriptausgabe (.vtt-Datei).

Siehe auch:

* [Video-Tutorial zum Hinzufügen von verdeckten Untertiteln zu Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/dynamic-media-overview-feature-video-use.html#add-cc-closed-captioning-to-dynamic-media-video)
* [Veröffentlichen von Dynamic Media-Videos in YouTube](/help/assets/dynamic-media/video.md#publishing-videos-to-youtube)

In der folgenden Abbildung spiegelt die URL den Beschriftungsteil wider, der auf das Transkript verweist (.vtt-Datei). Das Video spiegelt die gesprochene Sprache (Transkripttext) als **[!UICONTROL Geschlossene Beschriftung]** zum angegebenen Zeitstempel im Video. Der Benutzer kann die Beschriftung mithilfe der **[!UICONTROL CC]** Schaltfläche.

![configure-transcription-service](assets/transcript-example.png)

## Unterstützte Dateiformate für die Transkription {#supported-file-format}

Die folgenden Audio- und Videodateiformate werden für die Transkription unterstützt:

| Unterstützte Audio-/Videoformate | Erweiterungen |
|----|----|
| FLV (mit H.264- und AAC-Codecs) | (.flv) |
| MXF | (.mxf) |
| MPEG2-PS, MPEG2-TS, 3GP | (.ts, .ps, .3gp, .3gpp, .mpg) |
| Windows Media Video (WMV)/ASF | (.wmv, .asf) |
| AVI (unkomprimiert, 8 Bit/10 Bit) | (.avi) |
| MP4 | (.mp4, .m4a, .m4v) |
| Microsoft® Digital Video Recording (DVR-MS) | (.dvr-ms) |
| Matroska/WebM | (.mkv) |
| WAVE/WAV | (.wav) |
| QuickTime | (.mov) |


>[!NOTE]
>
>Die Assets (Audio- oder Videodateien) vom Anwendungstyp werden für die Transkription nicht unterstützt.

## Bekannte Einschränkungen {#known-limitations}

* Die Transkriptionsfunktion wird für Videos mit einer Dauer von bis zu 10 Minuten unterstützt.
* Der Videotitel muss weniger als 80 Zeichen lang sein.
* Die unterstützte Dateigröße beträgt bis zu 15 GB.
* Die maximal unterstützte Verarbeitungsdauer beträgt 60 Minuten.
* Kostenpflichtig [!DNL Azure] -Konto können Sie bis zu 50 Filme pro Minute hochladen. In einem Testkonto können Sie jedoch bis zu fünf Filme pro Minute hochladen.

## Tipps zur Fehlerbehebung {#troubleshooting}

Melden Sie sich bei Ihrer [!DNL Azure Media Services] -Konto mit denselben Anmeldedaten (die Sie für die Konfiguration verwendet haben), um den Anfragestatus zu überprüfen. Kontakt [!DNL Azure] unterstützen, wenn Ihre Anfrage nicht erfolgreich verarbeitet wurde.



