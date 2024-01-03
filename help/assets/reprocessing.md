---
title: Erneute Verarbeitung digitaler Assets
description: Erfahren Sie mehr über verschiedene Methoden zur Neuverarbeitung digitaler Assets
contentOwner: KK
source-git-commit: cb8eb56d07163f46aec252c70a3ec3b0273d97cf
workflow-type: tm+mt
source-wordcount: '685'
ht-degree: 43%

---

# Erneute Verarbeitung digitaler Assets {#reprocessing-digital-assets}

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein vorhandenes Metadatenprofil verfügt, das Sie nachträglich geändert haben. Wenn die neu bearbeitete Vorgabe erneut auf die vorhandenen Assets im Ordner angewendet werden soll, müssen Sie den Ordner erneut verarbeiten. Sie können beliebig viele Assets erneut verarbeiten.

Verarbeiten Sie Assets in einem Ordner neu, wenn eines der folgenden beiden Szenarien eintritt:

* Sie möchten eine Stapelsatzvorgabe für einen vorhandenen Asset-Ordner ausführen, in den bereits Assets hochgeladen wurden.
* Sie bearbeiten später eine vorhandene Stapelsatzvorgabe, die zuvor auf einen Asset-Ordner angewendet wurde.

## Erneutes Verarbeiten von Assets {#reprocessing-steps}

So verarbeiten Sie Assets in einem Ordner erneut:

1. In [!DNL Experience Manager]Wählen Sie auf der Seite &quot;Assets&quot;die neu hinzugefügten Assets oder die Assets aus, die Sie erneut verarbeiten möchten.
Wenn Sie einen Ordner auswählen:

   * Der Workflow berücksichtigt rekursiv alle Dateien in dem ausgewählten Ordner.
   * Wenn sich im ausgewählten Hauptordner ein oder mehrere Unterordner mit Assets befinden, verarbeitet der Workflow jedes Asset in der Ordnerhierarchie neu.
   * Es empfiehlt sich, diesen Workflow nicht in einer Ordnerhierarchie mit mehr als 1.000 Assets auszuführen.

1. Auswählen **[!UICONTROL Assets erneut verarbeiten]**. Wählen Sie zwischen den beiden Optionen:

   ![Optionen zur Neuverarbeitung von Assets](assets/reprocessing-assets-options.png)

   * **[!UICONTROL Vollständiger Prozess]:** Wählen Sie diese Option, wenn Sie den gesamten Prozess ausführen möchten, einschließlich Standardprofil, benutzerdefiniertes Profil, dynamischer Verarbeitung (sofern konfiguriert) und Nachbearbeitungs-Workflows.
   * **[!UICONTROL Erweitert]:** Wählen Sie diese Option, um die erweiterte Neuverarbeitung auszuwählen.

     ![Erweiterte Optionen für die Neuverarbeitung von Assets](assets/reprocessing-assets-options-advanced.png)

     Wählen Sie unter den folgenden erweiterten Optionen aus:

      * **[!UICONTROL Standard-Ausgabeformate für die Vorschau]:** Wählen Sie diese Option, wenn Sie die standardmäßig in der Vorschau angezeigten Ausgabedarstellungen erneut verarbeiten möchten.

      * **[!UICONTROL Metadaten]:** Wählen Sie diese Option, wenn Sie Metadateninformationen und Smart-Tags für die ausgewählten Assets extrahieren möchten.

      * **[!UICONTROL Verarbeitungsprofile]:** Wählen Sie diese Option, wenn Sie ein ausgewähltes Profil erneut verarbeiten möchten. Sie können **[!UICONTROL Vollständiger Prozess]** -Option, um die Standardverarbeitung und das benutzerdefinierte Profil einzuschließen, die auf der Ordnerebene zugewiesen sind.
        <!--When assets are uploaded to a folder, [!DNL Experience Manager] checks the containing folder's properties for a processing profile. If none is applied, a parent folder in the hierarchy is checked for a processing profile to apply.-->

      * **[!UICONTROL Nachbearbeitungs-Workflow]:** Wählen Sie diese Option, bei der eine zusätzliche Verarbeitung von Assets erforderlich ist, die mit den Verarbeitungsprofilen nicht erreicht werden kann. Der Konfiguration können weitere Nachbearbeitungs-Workflows hinzugefügt werden. Mit der Nachbearbeitung können Sie zusätzlich zur konfigurierbaren Verarbeitung mithilfe von Asset-Microservices eine vollständig angepasste Verarbeitung hinzufügen.

Siehe [Asset-Microservices und Verarbeitungsprofile verwenden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=de) , um mehr über Verarbeitungsprofile und Nachbearbeitungs-Workflow zu erfahren.

![Erweiterte Optionen für die Neuverarbeitung von Assets2](assets/reprocessing-assets-options-advanced-2.png)

Klicken Sie nach Auswahl der entsprechenden Optionen auf **[!UICONTROL Neuverarbeitung]**. Die Erfolgsmeldung wird angezeigt.

## Szenarien für die Neuverarbeitung digitaler Assets {#scenarios-reprocessing}

[!DNL Experience Manager] ermöglicht die erneute Verarbeitung digitaler Assets für die folgenden Komponenten.

### Smart-Tags {#reprocessing-smart-tags}

Organisationen, die mit digitalen Assets arbeiten, verwenden zunehmend taxonomiegesteuertes Vokabular in Asset-Metadaten. Im Wesentlichen handelt es sich um eine Liste von Schlüsselwörtern, die Angestellte, Partner bzw. Partnerinnen und Kunden bzw. Kundinnen üblicherweise verwenden, um sich auf digitale Assets einer bestimmten Klasse zu beziehen und danach zu suchen. Das Tagging von Assets mit taxonomiegesteuertem Vokabular stellt sicher, dass die Assets leicht identifiziert und abgerufen werden können.

Verglichen mit dem Vokabular natürlicher Sprachen hilft das Tagging digitaler Assets anhand einer Geschäftstaxonomie dabei, sie am Geschäft eines Unternehmens auszurichten, und stellt dabei sicher, dass nur die relevantesten Assets bei der Suche angezeigt werden.

Mehr dazu [Smart-Tags für Videoassets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/smart-tags-video-assets.html?lang=en).

Mehr dazu [Erneutes Verarbeiten von Farb-Tags für vorhandene Bilder in DAM](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/color-tag-images.html?lang=en#color-tags-existing-images).

### Smartes Zuschneiden {#reprocessing-smart-crop}

Mehr dazu [Smartes Zuschneiden von Dynamic Media](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=en) , mit dem Sie bestimmte Zuschnitte (**[!UICONTROL Smartes Zuschneiden]** und Pixelzuschnitt) sowie die Scharfzeichnungskonfiguration für die hochgeladenen Assets.

### Metadaten {#reprocessing-metadata}

[!DNL Adobe Experience Manager Assets] speichert Metadaten für jedes Asset. Damit können Assets einfacher kategorisiert und organisiert und bestimmte Assets leichter von Benutzern gefunden werden. Mit der Möglichkeit, Metadaten aus in Experience Manager Assets hochgeladenen Dateien zu extrahieren, lässt sich die Metadatenverwaltung in den kreativen Workflow integrieren. Da Sie Metadaten mit den Assets speichern und verwalten können, können Sie Assets basierend auf ihren Metadaten automatisch organisieren und verarbeiten.

Mehr dazu [Erneutes Verarbeiten von Metadatenprofilen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/metadata-profiles.html?lang=de).

### Dynamic Media-Assets in einem Ordner erneut verarbeiten {#reprocessing-dynamic-media}

Sie können Assets in einem Ordner erneut verarbeiten, der bereits über ein Dynamic Media-Bildprofil oder ein Dynamic Media-Videoprofil verfügt, das Sie nachträglich geändert haben. Weitere Informationen finden Sie unter [Dynamic Media-Assets in einem Ordner erneut verarbeiten.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/about-image-video-profiles.html?lang=en)

>[!NOTE]
>
>Sie müssen [!DNL Dynamic Media] in der Umgebung, um das Dialogfeld &quot;Dynamic Media&quot;zu aktivieren.
>

### Workflows

Mehr dazu [Verarbeitungsprofile und Nachbearbeitungs-Workflows](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/asset-microservices-configure-and-use.html?lang=de).

