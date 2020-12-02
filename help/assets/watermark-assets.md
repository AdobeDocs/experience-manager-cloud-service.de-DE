---
title: Assets mit Wasserzeichen versehen
description: Hinzufügen von Wasserzeichen zu digitalen Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: af27295b618fb3909d43ed94a74148f7c4f59c10
workflow-type: tm+mt
source-wordcount: '196'
ht-degree: 87%

---


# Versehen Sie Assets mit Wasserzeichen {#watermark-assets}

In [!DNL Adobe Experience Manager Assets] können Sie Bildern ein digitales Wasserzeichen hinzufügen. [!DNL Assets] unterstützt das Anwenden eines Bilds als Wasserzeichen für andere Bilddateien. Wasserzeichen können Benutzern dabei helfen, die Authentizität und das Urheberrecht von Assets zu überprüfen. Außerdem können Wasserzeichen dazu dienen, den Status eines Dokuments (wie vertraulich, Entwurf, Gültigkeit usw.) anzugeben.

Gehen Sie wie folgt vor, um [!DNL Experience Manager] so zu konfigurieren, dass Assets mit Wasserzeichen versehen werden:

1. Eine PNG-Datei wird als Wasserzeichen angewendet. Laden Sie diese Datei in Ihr DAM-Repository hoch.

1. Greifen Sie auf das [!DNL Cloud Manager]-Git-Repository zu, das Ihrer Umgebung zugeordnet ist. Komprimieren Sie eine Datei mit dem Namen `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.cfg.json` im Repository mit folgendem Inhalt. Anweisungen hierzu finden Sie unter [Wie Sie OSGi-Konfigurationen in [!DNL Experience Manager] als Cloud Service](/help/implementing/deploying/configuring-osgi.md) durchführen.

   ```json
   {
   "watermark": "/content/dam/<path-to-watermark-image.png>",
    "width": 100
   }
   ```

1. [Erstellen Sie ein Verarbeitungsprofil](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile), um Asset-Microservices zur Anwendung des Wasserzeichens zu nutzen.

   ![Asset-Verarbeitungsprofil zum Erstellen eines Wasserzeichens](assets/watermark-processing-profile.png)

1. [Wenden Sie die Verarbeitungsprofile auf einen Ordner](/help/assets/asset-microservices-configure-and-use.md#use-profiles) an, um mit Wasserzeichen versehene Assets zu erstellen.

## Tipps und Einschränkungen {#tips-limitations-bestpractices}

* Sie können eine einzelne Konfiguration verwenden, um alle Ihre Assets mit Wasserzeichen zu versehen. Für Wasserzeichen wird nur ein Bild verwendet; dessen Breite ist fest.
* Sie können das Wasserzeichen ohne Tiling in der Mitte platzieren.
* Textbasierte Wasserzeichen werden nicht unterstützt.

>[!MORELIKETHIS]
>
>* [Asset-Microservices – Überblick](/help/assets/asset-microservices-overview.md).
>* [Verwenden von Asset-Microservices mit Verarbeitungsprofilen](/help/assets/asset-microservices-configure-and-use.md).

