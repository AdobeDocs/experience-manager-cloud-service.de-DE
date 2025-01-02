---
title: Integrieren von AEM Assets beim Erstellen von Inhalten für Edge Delivery Services
description: Erfahren Sie, wie Sie AEM Assets mit Edge Delivery Services integrieren. Durch diese Integration können Sie AEM Assets mit Microsoft Word und Google Docs integrieren, AEM Assets mit dem universellen Editor integrieren, Dynamic Media mit OpenAPI-Funktionen mit dem universellen Editor integrieren und Dynamic Media mit OpenAPI-Funktionen mit Microsoft Word und Google Docs integrieren.
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: 3a758af4d17d761b8e3e4a77ea3cda6a4b6d0bb7
workflow-type: tm+mt
source-wordcount: '697'
ht-degree: 3%

---

# Integrieren von AEM Assets beim Erstellen von Inhalten für Edge Delivery Services {#integrate-aem-assets-while-authoring-for-edge-delivery-services}

![EDS2](/help/assets/assets/EDS2.png)

Edge Delivery Services ist ein zusammenstellbarer Satz von Services, der Ihnen ein hohes Maß an Flexibilität bei der Erstellung und Bereitstellung von Inhalten auf Ihrer Website ermöglicht. Sie können sowohl das [AEM](/help/sites-cloud/authoring/author-publish.md)Content-Management als auch das [WYSIWYG-Authoring mit dem universellen Editor sowie das dokumentbasierte Authoring ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring).

Sie können Inhalte in folgenden Bereichen bearbeiten:

* [Dokumente zu Microsoft Word oder Google](#integrate-aem-assets-with-document-based-authoring-tools)

* [universellen Editor](#integrate-aem-assets-with-universal-editor)

Nachdem Sie den Inhalt bearbeitet haben, können Sie ihn in Edge Delivery Services veröffentlichen.

## Integrieren von AEM Assets mit dokumentbasierten Authoring-Flüssen für Edge Delivery Services {#integrate-aem-assets-with-document-based-authoring-tools}

Die Integration von AEM Assets mit den dokumentbasierten Authoring-Tools wie Microsoft Word oder Google Docs bietet einen Asset-Selektor direkt in Ihrem Editor. Verwenden Sie diesen Asset-Wähler, um auf die AEM Assets zuzugreifen, und fügen Sie genehmigte Assets in Ihr Dokument ein.

### Voraussetzungen{#integrate-aem-assets-with-microsoft-word-and-google-docs}

Bevor Sie beginnen, stellen Sie sicher, dass Ihre dokumentbasierte Authoring-Umgebung bereit ist:

* Integrieren Sie AEM in ein dokumentbasiertes Authoring-Tool, um die Authoring-Umgebung einzurichten. Siehe [Erste Schritte - Entwickler-Tutorial](https://www.aem.live/developer/tutorial) zum Einrichten der Authoring-Umgebung.

### Integrieren von AEM Assets in die dokumentbasierte Authoring-Umgebung{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

Konfigurieren Sie das AEM Assets Sidekick-Plug-in für die Verwendung von Assets beim Erstellen von Inhalten in Microsoft Word- oder Google-Dokumenten.

* Unter [Adobe Experience Manager Assets Sidekick-Plug](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors) erfahren Sie, wie Sie in Microsoft Word- oder Google-Dokumenten auf AEM Assets zugreifen und diese verwenden können.
* Siehe [Konfigurieren des Adobe Experience Manager Assets Sidekick-Plug](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin) für Konfigurationsdetails.
  ![my-assets-sidebar](/help/assets/assets/my-assets-sidebar.png)

## Bereitstellen von Assets mit Dynamic Media mit OpenAPI-Funktionen {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

Sie können auch Assets verwenden, die mithilfe von DM mit OpenAPI-Funktionen bereitgestellt werden. Es bietet viele Vorteile, wie zum Beispiel:

* Nur Zugriff auf markenbestätigte Assets (Bilder, Videos, PDF und andere Asset-Typen) von AEM Assets Cloud Service aus.
* Governance (Verweise vs. Kopien des Assets), die bei der automatischen Weiterleitung von Asset-Lebenszyklus-Ereignissen wie Ablauf, Löschung und Aktualisierungen hilft.
* Dynamische Bildausgabedarstellungen und smartes Zuschneiden.
* Optimierung und Bereitstellung von Rich-Media, z. B. vorkonfiguriertes adaptives Video-Streaming und Bereitstellung von Original-Assets für PDF.
* Impressionsbericht auf Asset-Ebene ([begrenzte Verfügbarkeit](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

Weitere Informationen zu den Funktionen finden Sie in der Dokumentation zu [Dynamic Media mit OpenAPI](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview)Funktionen.

### Voraussetzungen {#prerequisites-for-dm-with-openapi-capabilities-to-use-aem-assets}

Um einen Asset-Verweis zu verwenden, müssen Sie über Folgendes verfügen:

* Berechtigung für eine Assets-Cloud Service-Umgebung, in der Dynamic Media mit Open API-Funktionen aktiviert ist.
* Eine Dynamic Media-Lizenz.
* Das AEM Assets Sidekick-Plug-in mit aktiviertem Kopierverweis für Bild-Assets. Weitere Informationen finden Sie unter [this](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode) für die dokumentbasierte Bearbeitung und unter [this](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) für die universelle Editor-basierte Bearbeitung.
* Assets, die genehmigt wurden. Genehmigte Assets wurden über das Assets Cloud Service-Backend oder Benutzeroberflächenaktionen `dam:status=Approved`.

### Verwenden von mit Dynamic Media bereitgestellten Assets mit OpenAPI-Funktionen{#how-to-use-Dynamic-Media-with-OpenAPI-assets}

Informationen zur Verwendung von Assets, die mit Dynamic Media mit OpenAPI-Funktionen beim Erstellen von Inhalten bereitgestellt werden, finden Sie unter:

* [Verwenden von Bildverweisen](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content)
* [Verwenden von Videoverweisen](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [Verwenden von Asset-Referenzen für Nicht-Bild- und Video-Assets wie PDF, ZIP-Dateien und mehr](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

In diesem Video erfahren Sie, wie Sie Assets mit Dynamic Media mit OpenAPI-Funktionen bereitstellen.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## Beispiel für Edge Delivery Services-Site{#example-of-an-Edge-Delivery-Services-site}

Siehe [WKND-](https://aem-dynamicmedia-demo--dm--hlxsites.aem.live/travel-hospitality/wknd-trvl-home). Diese Site basiert auf den dokumentbasierten Authoring-Funktionen von Edge Delivery Services. Der Inhalt der Site wird in [Google Docs](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT) erstellt, wobei Dynamic Media mit OpenAPI-Funktionen für die Asset-Bereitstellung verwendet wird. Nach der Erstellung wird der Inhalt direkt aus dem Dokument veröffentlicht. Für dieses dokumentbasierte Authoring-Setup werden alle wichtigen Dateien, Ordner, Konfigurationen, den Stil und die Funktions-Codes der Website in diesem [Git-Repository](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks) gespeichert.

## Integrieren von AEM Assets mit auf dem universellen Editor basierenden Authoring-Flüssen für Edge Delivery Services {#integrate-aem-assets-with-universal-editor}

Einrichten des universellen Editors für die Integration mit AEM Assets. Durch diese Integration können Sie Dynamic Media mit OpenAPI-Funktionen verwenden, um Assets bereitzustellen.

* Siehe [Konfiguration in Edge Delivery Site](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site), um eine benutzerdefinierte Asset-Auswahlfunktion im universellen Editor hinzuzufügen. Mit der benutzerdefinierten Asset-Auswahl können Sie Assets direkt in Ihre Inhalte im universellen Editor einfügen.
* Unter [Übersicht über Erweiterungen](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) erfahren Sie, wie Sie auf AEM Assets zugreifen und die Assets beim Authoring im universellen Editor einfügen können.

