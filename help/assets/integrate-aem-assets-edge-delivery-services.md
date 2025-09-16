---
title: Integrieren von [!DNL AEM Assets] während der Erstellung von Inhalten für [!DNL Edge Delivery Services]
description: Erfahren Sie mehr zur Integration von [!DNL AEM Assets] mit [!DNL Edge Delivery Services]. This integration enables you to integrate [!DNL AEM Assets] mit [!DNL Microsoft Word] und [!DNL Google Docs], integrate [!DNL AEM Assets] mit [!DNL Universal Editor], integrate [!DNL Dynamic Media] mit [!DNL Edge Delivery Services], integrate [!DNL Dynamic Media with OpenAPI capabilities] mit [!DNL Universal Editor] und [!DNL Dynamic Media with OpenAPI capabilities] mit [!DNL Microsoft Word] und [!DNL Google Docs] integrieren.
tags: AEM Assets, Edge Delivery Services, Dynamic Media, Dynamic Media with OpenAPI capabilities, Universal Editor, Edge Delivery Services with Universal Editor
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: 79213bcfe5c5ccf7c60a31e6cb757f60a0ba87a7
workflow-type: ht
source-wordcount: '628'
ht-degree: 100%

---


# Integrieren von [!DNL AEM Assets] während der Erstellung von Inhalten für [!DNL Edge Delivery Services] {#integrate-aem-assets-with-edge-delivery-services}

![Integrieren von AEM-Assets mit dem universellen Editor](/help/assets/assets/EDS2.png)

[[!DNL Edge Delivery Services]](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/overview) ist ein modularer Satz von Diensten, der eine hohe Flexibilität bei der Erstellung von Inhalten auf Ihrer Website ermöglicht. Sie können sowohl das [AEM-Content-Management](/help/sites-cloud/authoring/author-publish.md) und [WYSIWYG-Authoring mit dem [!DNL Universal Editor] als auch das dokumentenbasierte Authoring verwenden](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring).

Sie können Inhalte in folgenden Bereichen bearbeiten:

* [[!DNL Microsoft Word] oder [!DNL Google Docs]](#integrate-dynamic-media-with-edge-delivery-services)
* [[!DNL Universal Editor]](#integrate-aem-assets-with-universal-editor-UE)

Nachdem Sie den Inhalt bearbeitet haben, können Sie ihn in Edge Delivery Services veröffentlichen.

## Integrieren von [!DNL AEM Assets] mit dokumentenbasierten Authoring-Flüssen für [!DNL Edge Delivery Services] {#integrate-dynamic-media-with-edge-delivery-services}

Wenn [!DNL AEM Assets] mit Ihren dokumentbasierten Authoring-Tools wie [!DNL Microsoft Word] oder [!DNL Google Docs] integriert wird, steht eine Asset-Auswahl in Ihrem Authoring-Tool zur Verfügung. Verwenden Sie diese Asset-Auswahl, um auf [!DNL AEM Assets] zuzugreifen und genehmigte Assets in Ihren Inhalt einzufügen.
Wenn Sie bereits über eine [!DNL Edge Delivery Services]-Website verfügen, finden Sie in der [[!DNL AEM Assets] Plug-in](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md)-Dokumentation Informationen zur Integration von [!DNL AEM Assets] in Ihr vorhandenes [!DNL AEM]-Projekt.
Befolgen Sie die folgenden Abschnitte [Voraussetzungen](#integrate-aem-assets-with-microsoft-word-and-google-docs) und [Integrieren von [!DNL AEM Assets] mit der dokumentbasierten](#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs), wenn Sie keine [!DNL Edge Delivery Services]-Website haben, um Ihre inklusiven Inhalte von [!DNL AEM Assets] zu veröffentlichen, die in dokumentbasierten Authoring-Tools erstellt wurden.

### Voraussetzungen{#integrate-aem-assets-with-microsoft-word-and-google-docs}

Bevor Sie beginnen, stellen Sie sicher, dass Ihre dokumentbasierte Authoring-Umgebung bereit ist:

* Integrieren von [!DNL AEM] mit einem dokumentbasierten Authoring-Tool zum Einrichten der Authoring-Umgebung. Unter [Erste Schritte – Entwickler-Tutorial](https://www.aem.live/developer/tutorial) erfahren Sie, wie Sie die Authoring-Umgebung einrichten.

### Integrieren von [!DNL AEM Assets] in die dokumentbasierte Authoring-Umgebung{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

Konfigurieren Sie das [!DNL AEM Assets]-Sidekick-Plug-in für die Verwendung von Assets beim Erstellen von Inhalten in [!DNL Microsoft Word] oder [!DNL Google Docs].

* Unter [[!DNL Adobe Experience Manager Assets Sidekick Plugin]](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors) erfahren Sie, wie Sie AEM Assets in Microsoft Word oder Google Docs abrufen und verwenden können.
* Siehe [Konfigurieren des [!DNL Adobe Experience Manager Assets Sidekick Plugin]](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin)s für Details zur Konfiguration.
  ![Verwenden von Dynamic Media mit OpenAPI-Funktionen in Microsoft Word- und Google-Dokumenten](/help/assets/assets/my-assets-sidebar.png)

## Bereitstellen von Assets mithilfe von [!DNL Dynamic Media with OpenAPI capabilities] {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

Sie können auch Assets verwenden, die mithilfe von [!DNL Dynamic Media with OpenAPI capabilities] bereitgestellt werden. Das Tagging bietet viele Vorteile, z. B.:

* Zugriff auf ausschließlich für die Marke genehmigte Assets (Bilder, Videos, PDFs und andere Asset-Typen) von [!DNL AEM Assets Cloud Services] aus.
* Governance (Verweise vs. Kopien des Assets), die bei der automatischen Weiterleitung von Asset-Zyklusereignissen wie Ablauf, Löschung und Aktualisierungen hilft.
* Dynamische Bildausgabedarstellungen und intelligenter Zuschnitt.
* Optimierung und Bereitstellung von Rich-Media, z. B. standardmäßig adaptives Video-Streaming und Bereitstellung von Original-Assets für PDFs.
<!--

* Asset-level impressions report ([limited availability](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

-->

Weitere Informationen zu den Funktionen finden Sie in der Dokumentation zu [[!DNL Dynamic Media with OpenAPI capabilities]](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview).

### Voraussetzungen {#dynamic-media-with-universal-editor-and-edge-delivery-services}

Um einen Asset-Verweis zu verwenden, müssen Sie über Folgendes verfügen:

* Berechtigung für eine Assets Cloud Service-Umgebung, in der [!DNL Dynamic Media with Open API capabilities] aktiviert ist.
* Eine [!DNL Dynamic Media]-Lizenz.
* Das [!DNL AEM Assets sidekick plugin] mit aktiviertem Kopierverweis für Bild-Assets. Weitere Informationen zum dokumentbasierten Authoring finden Sie in [dieser Dokumentation](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode). Informationen zum auf dem universellen Editor basierten Authoring finden Sie in [dieser Dokumentation](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview).
* Assets, die genehmigt wurden. Genehmigte Assets haben den `dam:status=Approved` über das Assets Cloud Services-Backend oder UI-Aktionen erhalten.

### Verwenden von Assets, die mithilfe von [!DNL Dynamic Media with OpenAPI capabilities] bereitgestellt wurden{#Using-Dynamic-Media-with-edge-delivery-services}

Wählen Sie die folgenden Links aus, um zu erfahren, wie Sie mit [!DNL Dynamic Media with OpenAPI capabilities] Bilder, Videos und andere Asset-Typen in Ihren Inhalten bereitstellen können:

* [Hinzufügen von Bildern zu Inhalten](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content)
* [Hinzufügen von Videos zu Inhalten](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [Hinzufügen von Nicht-Bild- und Nicht-Video-Assets wie PDF-, ZIP-Dateien und mehr zu Inhalten](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

In diesem Video erfahren Sie, wie Sie Assets in Ihren Inhalten mit Dynamic Media mit OpenAPI-Funktionen bereitstellen.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## [!DNL Edge Delivery Services]-Beispiel-Website{#dynamic-media-with-google-docs-and-ms-word}

Siehe [WKND Travel](https://aem-dynamicmedia-demo--dm--hlxsites.aem.live/travel-hospitality/wknd-trvl-home), eine Site, die mithilfe der dokumentbasierten Authoring-Funktionen von [!DNL Edge Delivery Services] erstellt wurde. Der Inhalt der Site wird in [Google Docs](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT) verfasst und [!DNL Dynamic Media with OpenAPI capabilities] wird verwendet, um Assets im Inhalt bereitzustellen. Nach dem Authoring wird der Inhalt direkt aus dem Dokument veröffentlicht. In diesem [Git-Repository](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks) erfahren Sie mehr über alle wichtigen Dateien, Ordner, Konfigurationen, den Stil und die Funktions-Codes der Website, die zum Einrichten des dokumentbasierten Authorings für diese [!DNL Edge Delivery Services (EDS)]-Site verwendet werden.

## Integrieren von [!DNL AEM Assets] mit auf dem [!DNL Universal Editor] basierenden Authoring-Flüssen für [!DNL Edge Delivery Services] {#integrate-aem-assets-with-universal-editor-UE}

Einrichten des [!DNL Universal Editor] für die Integration mit [!DNL AEM Assets]. Durch diese Integration können Sie [!DNL Dynamic Media with OpenAPI capabilities] verwenden, um Assets bereitzustellen.

* Unter [Konfiguration in  [!DNL Edge Delivery] -Site](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site) erfahren Sie, wie Sie im [!DNL Universal Editor] eine benutzerdefinierte Asset-Auswahlfunktion hinzufügen. Mit der benutzerdefinierten Asset-Auswahl können Sie Assets direkt in Ihren [!DNL Universal Editor] einfügen.
* Unter [Erweiterungen – Überblick](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) erfahren Sie, wie Sie beim Authoring im [!DNL Universal Editor] auf [!DNL AEM Assets] zugreifen und die Assets einfügen können.
