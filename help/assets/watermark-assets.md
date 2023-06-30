---
title: Assets mit Wasserzeichen versehen
description: Hinzufügen von Wasserzeichen zu digitalen Assets.
contentOwner: AG
feature: Asset Management,Publishing
role: User,Admin
exl-id: 210f8925-bd15-4b4a-8714-5a1486eeb49e
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '295'
ht-degree: 85%

---

# Versehen von Assets mit Wasserzeichen {#watermark-assets}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/watermarking.html) |
| AEM as a Cloud Service | Dieser Artikel |

In [!DNL Adobe Experience Manager Assets] können Sie Bildern ein digitales Wasserzeichen hinzufügen. [!DNL Assets] unterstützt das Anwenden eines Bilds als Wasserzeichen für andere Bilddateien. Wasserzeichen können Benutzern dabei helfen, die Authentizität und das Urheberrecht von Assets zu überprüfen. Außerdem können Wasserzeichen dazu dienen, den Status eines Dokuments (wie vertraulich, Entwurf, Gültigkeit usw.) anzugeben.

So konfigurieren Sie [!DNL Experience Manager] für Wasserzeichen-Assets:

1. Eine PNG-Datei wird als Wasserzeichen angewendet. Laden Sie diese Datei in Ihr DAM-Repository hoch.

1. Gehen Sie zu **[!UICONTROL Tools > Assets > Assets-Konfigurationen]**.

1. Klicken Sie auf **[!UICONTROL System-Wasserzeichenprofil]**.

1. Auf der [!UICONTROL Seite „System-Wasserzeichenprofil“] geben Sie den Bildpfad an, der in Schritt 1 in Ihr DAM-Repository hochgeladen wurde.

1. Geben Sie im Feld **[!UICONTROL Skalieren]** die Wasserzeichenskala von 0,0 bis 1,0 relativ zur Breite der Ausgabedarstellung an.

1. Klicken Sie auf **[!UICONTROL Speichern]**.

   ![Asset-Duplikations-Detektor](assets/system-watermarking-profile.png)

   >[!NOTE]
   >
   >Wenn Sie das System Watermarking Profile mithilfe von `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` Konfigurationsdatei (OSGi-Konfiguration) verwenden, können Sie sie weiterhin verwenden. Adobe empfiehlt jedoch die Verwendung der neuen Methode.


1. [Verarbeitungsprofil erstellen](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) , um Asset-Microservices zum Anwenden des Wasserzeichens zu verwenden.

   ![Asset-Verarbeitungsprofil zum Erstellen eines Wasserzeichens](assets/watermark-processing-profile.png)

   Stellen Sie sicher, dass Sie den Umschalter **[!UICONTROL Wasserzeichen]** beim Erstellen des Verarbeitungsprofils aktivieren.

1. [Wenden Sie die Verarbeitungsprofile auf einen Ordner an](/help/assets/asset-microservices-configure-and-use.md#use-profiles), um mit Wasserzeichen versehene Assets zu erstellen.

## Tipps und Einschränkungen {#tips-limitations-bestpractices}

* Sie können eine einzelne Konfiguration verwenden, um alle Ihre Assets mit Wasserzeichen zu versehen. Für Wasserzeichen wird nur ein Bild verwendet; dessen Breite ist fest.
* Sie können das Wasserzeichen ohne Tiling in der Mitte platzieren.
* Textbasierte Wasserzeichen werden nicht unterstützt.

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)

>[!MORELIKETHIS]
>
>* [Asset-Microservices – Überblick](/help/assets/asset-microservices-overview.md).
>* [Verwenden von Asset-Microservices mit Verarbeitungsprofilen](/help/assets/asset-microservices-configure-and-use.md).
