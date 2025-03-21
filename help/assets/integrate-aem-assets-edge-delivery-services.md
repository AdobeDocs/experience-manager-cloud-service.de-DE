---
title: Integrieren  [!DNL AEM Assets]  Erstellen von Inhalten für [!DNL Edge Delivery Services]
description: Erfahren Sie, wie Sie  [!DNL AEM Assets] mit [!DNL Edge Delivery Services]. This integration enables you to integrate [!DNL AEM Assets] mit [!DNL Microsoft Word] und [!DNL Google Docs], integrate [!DNL AEM Assets] mit [!DNL Universal Editor], integrate [!DNL Dynamic Media with OpenAPI capabilities]  [!DNL Universal Editor]  und  [!DNL Dynamic Media with OpenAPI capabilities] mit [!DNL Microsoft Word] und [!DNL Google Docs] integrieren.
exl-id: e58db2ce-a55a-49b3-ae8e-709b5ea8d095
source-git-commit: 2de6352363959f4258c0786910eaef7babe68f15
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 3%

---

# Integrieren von [!DNL AEM Assets] beim Erstellen von Inhalten für [!DNL Edge Delivery Services] {#integrate-aem-assets-while-authoring-for-edge-delivery-services}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
         <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

![AEM-Assets mit UE](/help/assets/assets/EDS2.png)

[[!DNL Edge Delivery Services]](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/overview) ist ein zusammenstellbarer Satz von Services, der Ihnen ein hohes Maß an Flexibilität bei der Erstellung und Bereitstellung von Inhalten auf Ihrer Website ermöglicht. Sie können sowohl das [AEM-Content](/help/sites-cloud/authoring/author-publish.md)Management als auch das [WYSIWYG-Authoring mit  [!DNL Universal Editor]  sowie das dokumentbasierte Authoring verwenden](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/edge-delivery/wysiwyg-authoring/authoring).

Sie können Inhalte in folgenden Bereichen bearbeiten:

* [[!DNL Microsoft Word] oder [!DNL Google Docs]](#integrate-aem-assets-with-document-based-authoring-tools)
* [[!DNL Universal Editor]](#integrate-aem-assets-with-UE-universal-editor)

Nachdem Sie den Inhalt bearbeitet haben, können Sie ihn in Edge Delivery Services veröffentlichen.

## Integrieren von [!DNL AEM Assets] mit dokumentenbasierten Authoring-Flüssen für [!DNL Edge Delivery Services] {#integrate-aem-assets-with-document-based-authoring-tools}

Wenn [!DNL AEM Assets] mit Ihren dokumentbasierten Authoring-Tools wie [!DNL Microsoft Word] oder [!DNL Google Docs] integriert wird, steht eine Asset-Auswahl in Ihrem Authoring-Tool zur Verfügung. Verwenden Sie diesen Asset-Wähler, um auf [!DNL AEM Assets] zuzugreifen und genehmigte Assets in Ihren Inhalt einzufügen.
Wenn Sie bereits über eine [!DNL Edge Delivery Services]-Website verfügen, finden Sie in der [[!DNL AEM Assets] Plug-in](https://github.com/adobe-rnd/aem-assets-plugin/blob/main/README.md)-Dokumentation Informationen zur Integration von [!DNL AEM Assets] in Ihr vorhandenes [!DNL AEM].
Befolgen Sie die folgenden Abschnitte [Voraussetzungen](#integrate-aem-assets-with-microsoft-word-and-google-docs) und [Integrieren [!DNL AEM Assets] mit der dokumentbasierten ](#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs)), wenn Sie keine [!DNL Edge Delivery Services] Website haben, um Ihre [!DNL AEM Assets] inklusiven Inhalte zu veröffentlichen, die in dokumentbasierten Authoring-Tools erstellt wurden.

### Voraussetzungen{#integrate-aem-assets-with-microsoft-word-and-google-docs}

Bevor Sie beginnen, stellen Sie sicher, dass Ihre dokumentbasierte Authoring-Umgebung bereit ist:

* Integrieren von [!DNL AEM] mit einem dokumentbasierten Authoring-Tool zum Einrichten der Authoring-Umgebung. Unter [Erste Schritte - Entwickler-Tutorial](https://www.aem.live/developer/tutorial) erfahren Sie, wie Sie die Authoring-Umgebung einrichten.

### Integrieren von [!DNL AEM Assets] in die dokumentbasierte Authoring-Umgebung{#integrate-aem-assets-with-microsoft-word-or-google-docs-to-use-aem-assets-with-microsoft-word-or-google-docs}

Konfigurieren Sie das [!DNL AEM Assets] Sidekick-Plug-in für die Verwendung von Assets beim Verfassen von Inhalten in [!DNL Microsoft Word] oder [!DNL Google Docs].

* Unter [[!DNL Adobe Experience Manager Assets Sidekick Plugin]](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-experience-manager-assets-for-website-authors) erfahren Sie, wie Sie in Microsoft Word oder Google Docs auf AEM Assets zugreifen und diese verwenden können.
* Siehe [Konfigurieren [!DNL Adobe Experience Manager Assets Sidekick Plugin]](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin) für Konfigurationsdetails.
  ![Verwenden von Dynamic Media mit OpenAPI-Funktionen in Microsoft Word- und Google-Dokumenten](/help/assets/assets/my-assets-sidebar.png)

## Bereitstellen von Assets mithilfe von [!DNL Dynamic Media with OpenAPI capabilities] {#integrate-Dynamic-Media-with-OpenAPI-capabilities-with-Microsoft-Word-Google-Docs-and-universal-editor}

Sie können auch Assets verwenden, die mithilfe von [!DNL Dynamic Media with OpenAPI capabilities] bereitgestellt werden. Es bietet viele Vorteile, wie zum Beispiel:

* Nur Zugriff auf markenbestätigte Assets (Bilder, Videos, PDFs und andere Asset-Typen) von [!DNL AEM Assets Cloud Services] aus.
* Governance (Verweise vs. Kopien des Assets), die bei der automatischen Weiterleitung von Asset-Lebenszyklus-Ereignissen wie Ablauf, Löschung und Aktualisierungen hilft.
* Dynamische Bildausgabedarstellungen und smartes Zuschneiden.
* Optimierung und Bereitstellung von Rich-Media, z. B. standardmäßig adaptives Video-Streaming und Bereitstellung von Original-Assets für PDFs.
* Impressionsbericht auf Asset-Ebene ([begrenzte Verfügbarkeit](/help/assets/manage-reports-assets-view.md#dynamic-media-delivery-reports)).

Weitere Informationen zu den Funktionen finden Sie in [[!DNL Dynamic Media with OpenAPI capabilities]](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dynamic-media-open-apis/dynamic-media-open-apis-overview) Dokumentation.

### Voraussetzungen {#prerequisites-for-dm-with-openapi-capabilities-to-use-aem-assets}

Um einen Asset-Verweis zu verwenden, müssen Sie über Folgendes verfügen:

* Berechtigung für eine Assets Cloud Service-Umgebung, in der [!DNL Dynamic Media with Open API capabilities] aktiviert ist.
* Eine [!DNL Dynamic Media].
* Die [!DNL AEM Assets sidekick plugin] mit aktiviertem Kopierverweis für Bild-Assets. Weitere Informationen finden Sie unter [diese Dokumentation](https://www.aem.live/developer/configuring-aem-assets-sidekick-plugin#copymode) für die dokumentbasierte Bearbeitung und unter [diese Dokumentation](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) für die universelle Editor-basierte Bearbeitung.
* Assets, die genehmigt wurden. Genehmigte Assets wurden über das Assets Cloud Services-Backend oder Benutzeroberflächenaktionen `dam:status=Approved`.

### Verwenden von Assets, die mithilfe von [!DNL Dynamic Media with OpenAPI capabilities] bereitgestellt wurden{#how-to-use-Dynamic-Media-with-OpenAPI-assets}

Wählen Sie die folgenden Links aus, um zu erfahren, wie Sie mit [!DNL Dynamic Media with OpenAPI capabilities] Bilder, Videos und andere Asset-Typen in Ihren Inhalten bereitstellen können:

* [Hinzufügen von Bildern zu Inhalten](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-image-references-when-authoring-content)
* [Hinzufügen von Videos zu Inhalten](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-video-references-when-authoring-content)
* [Fügen Sie Nicht-Bild- und Video-Assets wie PDF, ZIP-Dateien und mehr zu Ihrem Inhalt hinzu](https://www.aem.live/docs/aem-assets-sidekick-plugin#using-asset-references-for-pdf-zip-etc-when-authoring-content)

In diesem Video erfahren Sie, wie Sie Assets in Ihren Inhalten mit Dynamic Media mit OpenAPI-Funktionen bereitstellen.

>[!VIDEO](https://video.tv.adobe.com/v/3441155)

## Beispiel [!DNL Edge Delivery Services] Website{#example-of-an-Edge-Delivery-Services-site}

Siehe [WKND Travel](http://bit.ly/3DExLnf), eine Site, die mithilfe der dokumentbasierten Authoring-Funktionen von [!DNL Edge Delivery Services] erstellt wurde. Der Inhalt der Site wird in [Google Docs](https://drive.google.com/drive/folders/1HCCHRWp4HJIXW_cUv5cRDQ5DzzqiZsXT) verfasst und [!DNL Dynamic Media with OpenAPI capabilities] verwendet, um Assets im Inhalt bereitzustellen. Nach dem Authoring wird der Inhalt direkt aus dem Dokument veröffentlicht. In diesem [Git-Repository](https://github.com/hlxsites/franklin-assets-selector/tree/aem-dynamicmedia-demo/blocks) erfahren Sie mehr über alle wichtigen Dateien, Ordner, Konfigurationen, den Stil und die Funktions-Codes der Website, die zum Erstellen der dokumentbasierten Authoring-Einrichtung für diese [!DNL Edge Delivery Services (EDS)]-Site verwendet werden.

## Integrieren von [!DNL AEM Assets] mit [!DNL Universal Editor]-basierten Authoring-Flüssen für [!DNL Edge Delivery Services] {#integrate-aem-assets-with-UE-universal-editor}

Einrichten der [!DNL Universal Editor] für die Integration mit [!DNL AEM Assets]. Durch diese Integration können Sie [!DNL Dynamic Media with OpenAPI capabilities] verwenden, um Assets bereitzustellen.

* Unter [Konfiguration in [!DNL Edge Delivery] Site](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#configuration-in-edge-delivery-site) erfahren Sie, wie Sie eine benutzerdefinierte Asset-Auswahlfunktion in [!DNL Universal Editor] hinzufügen. Mit der benutzerdefinierten Asset-Auswahl können Sie Assets direkt in Ihre [!DNL Universal Editor] einfügen.
* Unter [Übersicht über Erweiterungen](https://developer.adobe.com/uix/docs/extension-manager/extension-developed-by-adobe/configurable-asset-picker/#extension-overview) erfahren Sie, wie Sie beim Authoring in [!DNL Universal Editor] auf [!DNL AEM Assets] zugreifen und die Assets einfügen können.
