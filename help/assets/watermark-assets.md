---
title: Wasserzeichen für Assets
description: Hinzufügen von Wasserzeichen zu digitalen Assets.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f1fcddf196a1a2bfa2629dbd6a8fe0ac057a3d07
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 2%

---


# Wasserzeichen für Assets {#watermark-assets}

[!DNL Adobe Experience Manager Assets] können Sie Bildern ein digitales Wasserzeichen hinzufügen. [!DNL Assets] unterstützt das Anwenden eines Bildes als Wasserzeichen auf andere Bilddateien. Wasserzeichen können Benutzern dabei helfen, die Authentizität und das Urheberrecht der Assets zu überprüfen. Außerdem kann ein Wasserzeichen verwendet werden, um den Status eines Dokuments wie vertraulich, Entwurf, Gültigkeit usw. anzugeben.

Gehen Sie wie folgt vor, um Experience Manager zu Wasserzeichenelementen zu konfigurieren:

1. Eine PNG-Datei wird als Wasserzeichen angewendet. Laden Sie diese Datei in Ihr DAM-Repository hoch.

1. Greifen Sie auf das mit Ihrer Umgebung verknüpfte Cloud Manager Git-Repository zu. Komprimieren Sie eine Datei mit dem Namen `com.adobe.cq.assetcompute.impl.profile.WatermarkingProfileServiceImpl.json` in ihrem Cloud Manager Git-Repository mit folgendem Inhalt. Weitere Informationen finden Sie unter [OSGi-Konfiguration in Experience Manager als Cloud Service](/help/implementing/deploying/configuring-osgi.md).

   ```json
   {
   "watermark": "/content/dam/<path-to-watermark-image.png>",
    "width": 100
   }
   ```

1. [Erstellen Sie ein Profil](/help/assets/asset-microservices-configure-and-use.md#create-custom-profile) zur Verarbeitung, um Asset-Mikrodienste zur Anwendung des Wasserzeichens zu nutzen.

   ![Profil zur Asset-Verarbeitung zum Erstellen eines Wasserzeichens](assets/watermark-processing-profile.png)

1. [Wenden Sie die verarbeitenden Profil auf einen Ordner](/help/assets/asset-microservices-configure-and-use.md#use-profiles) an, um mit Wasserzeichen versehene Assets zu erstellen.

## Tipps und Einschränkungen {#tips-limitations-bestpractices}

* Sie können eine einzelne Konfiguration verwenden, um alle Assets mit einem Wasserzeichen zu versehen. Für Wasserzeichen wird nur ein Bild verwendet und seine Breite ist fixiert.
* Sie können das Wasserzeichen in der Mitte platzieren, ohne dass es gekachelt wird.
* Textbasierte Wasserzeichen werden nicht unterstützt.

>[!MORELIKETHIS]
>
>* [Asset Microservices - Übersicht](/help/assets/asset-microservices-overview.md).
>* [Verwenden Sie Asset-Mikrodienste mit verarbeitenden Profilen](/help/assets/asset-microservices-configure-and-use.md).

