---
title: Herunterladen von Assets aus Content Hub
description: Erfahren Sie, wie Sie Assets aus dem Content Hub-Portal herunterladen
role: User
exl-id: 96d4ffba-4e3e-4496-9da2-6eb36be8331f
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 94%

---

# Herunterladen von Assets aus Content Hub {#download-assets}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

<!-- ![Download assets](assets/download-asset.jpg) -->
![Herunterladen von Assets](assets/download-asset-genstudio.jpeg)

>[!AVAILABILITY]
>
>Das Content Hub-Handbuch ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Content Hub Guide PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/content-hub.pdf"}

Mit Content Hub können Sie Assets herunterladen und freigeben. Bei diesen Assets kann es sich um Bilder, Videos oder andere digitale Inhalte handeln. Content Hub verbessert die Barrierefreiheit und Anpassungsfähigkeit und ermöglicht so eine effektive Asset-Verteilung.

Sie können ein einzelnes Asset oder mehrere Assets mit Content Hub herunterladen. Es werden die Originalversionen des Assets heruntergeladen.

## Herunterladen eines einzelnen lizenzierten Assets {#single-download-asset}

Wählen Sie ein Asset aus und klicken Sie in der oberen Leiste auf ![Herunterladen](/help/assets/assets/download-icon.svg). Im Dialogfeld „Asset herunterladen“ wird die Asset-Lizenz angezeigt. Akzeptieren Sie die Lizenzbedingungen und klicken Sie auf **Herunterladen**.
Alternativ können Sie auf der Asset-Karte auf ![Herunterladen](/help/assets/assets/download-icon.svg) klicken, um das Asset herunterzuladen.

### Herunterladen eines einzelnen lizenzierten Assets über das Dialogfeld „Asset“ {#single-download-from-asset-dialog-box}

1. Klicken Sie auf die Asset-Miniatur. Das Dialogfeld „Asset“ wird angezeigt.
1. Klicken Sie in der Symbolleiste ganz rechts auf ![Herunterladen](/help/assets/assets/download-icon.svg). Im Download-Bereich werden die Asset-Ausgabedarstellungen sowie das Kontrollkästchen zur Annahme der Lizenzbedingungen angezeigt.
   ![Dialogfeld zum Herunterladen eines einzelnen Assets](/help/assets/assets/asset-dialog-box-for-single-download.png)
   * Klicken Sie auf den Link für die Nutzungsbedingungen, um die Lizenzbedingungen im linken Bereich anzuzeigen.

     >[!NOTE]
     >
     Das Kontrollkästchen für die Nutzungsbedingungen wird nur für lizenzierte Assets angezeigt. Darüber hinaus zeigt das Dialogfeld „Asset“ eine Vorschau der Lizenzbedingungen nur für die Assets mit genehmigten Lizenzen an. [Genehmigen Sie die Asset-Lizenz](/help/assets/approve-assets-content-hub.md) vor dem Herunterladen, um die Vorschau der Lizenzbedingungen im Dialogfeld „Asset“ zu aktivieren.

   * Klicken Sie auf das Feld für die **Original-Ausgabedarstellung**, um zur ursprünglichen Asset-Ausgabedarstellung im linken Bereich zurückzukehren.
1. Akzeptieren Sie die Lizenzbedingungen (für lizenzierte Assets) und klicken Sie auf **Herunterladen**, um das Asset herunterzuladen.

## Herunterladen mehrerer lizenzierter Assets{#multi-download}

1. Wählen Sie die Assets aus und klicken Sie in der oberen Leiste auf ![Herunterladen](/help/assets/assets/download-icon.svg). Das angezeigte Dialogfeld hängt davon ab, ob die Download-Liste abgelaufene Assets oder nur nicht abgelaufene Assets enthält. <br/>
   **Dialogfeld „Abgelaufene Assets herunterladen“:** Dieses Dialogfeld zeigt eine Vorschau der abgelaufenen Assets mit ihrem Ablaufdatum im linken Bereich an. Die Anzahl der abgelaufenen Assets von der insgesamt ausgewählten Anzahl wird im rechten Bereich angezeigt. Klicken Sie auf **Mit allen Assets fortfahren**, um abgelaufene Assets mit anderen Assets herunterzuladen (sofern vorhanden). Das Dialogfeld „Assets herunterladen“ wird angezeigt. Weitergehende Informationen finden Sie unter [Herunterladen von Assets](#Download-asset-dialog-box).

   >[!NOTE]
   >
   [Aktivieren Sie die Download-Option für abgelaufene Assets](/help/assets/configure-content-hub-ui-options.md#expired-assets-content-hub), um sie herunterzuladen. Nur abgelaufene Assets, für die der Download aktiviert wurde, können heruntergeladen werden.

   <a id="Download-asset-dialog-box"></a> **Dialogfeld „Assets herunterladen“:** Dieses Dialogfeld zeigt die Liste der Lizenzen, die mit den ausgewählten Assets verknüpft sind, im linken Bereich an. Wählen Sie eine Lizenz aus, um im mittleren Bereich eine Vorschau der Nutzungsbedingungen (im PDF-Format) und im rechten Bereich eine Vorschau der zugehörigen Assets samt Anzahl anzuzeigen. Die überprüften Lizenzen sind hellblau hervorgehoben.

   >[!NOTE]
   >
   Im Dialogfeld **Asset herunterladen** werden die Lizenzbedingungen nur für die genehmigten Lizenzen in einer Vorschau angezeigt. [Genehmigen Sie die Asset-Lizenzen](/help/assets/approve-assets-content-hub.md), bevor Sie sie herunterladen, um ihre Lizenzbedingungen im Dialogfeld **Asset herunterladen** in einer Vorschau anzuzeigen.

1. Klicken Sie auf ![Enfernen-Symbol](/help/assets/assets/remove-icon.svg), um eine Lizenz aus dem Download-Dialogfeld zu entfernen.

1. Akzeptieren Sie die Nutzungsbedingungen und klicken Sie dann auf **Herunterladen**, um die Assets herunterzuladen, die mit den verfügbaren Lizenzen im linken Bereich verknüpft sind.
   ![Herunterladen mehrerer Lizenzen](/help/assets/assets/download-multiple-license.png)

### Herunterladen nicht lizenzierter Assets {#download-non-licensed-assets}

Um nicht lizenzierte Assets herunterzuladen, wählen Sie die Assets aus und klicken Sie in der oberen Leiste auf ![Herunterladen](/help/assets/assets/download-icon.svg).







