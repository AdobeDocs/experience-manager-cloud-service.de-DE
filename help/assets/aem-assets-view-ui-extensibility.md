---
title: Aktivieren der Erweiterbarkeit der Benutzeroberfläche in [!DNL AEM Assets View]
description: Erfahren Sie mehr über die Fähigkeit „Erweiterbarkeit der Benutzeroberfläche“ der  [!DNL AEM Assets View]. [!DNL AEM Assets View] -Benutzeroberfläche, die das Hinzufügen benutzerdefinierter Benutzeroberflächenkomponenten ermöglicht, um bestimmte Geschäftsanforderungen zu erfüllen.
feature: App Builder
role: User, Developer
exl-id: a11f7043-17cf-4331-b76c-d3db099c2411
source-git-commit: a03e6cf842f95f8799f23ed5c7e3b563b092b4e5
workflow-type: tm+mt
source-wordcount: '641'
ht-degree: 97%

---

# Aktivieren der Erweiterbarkeit der Benutzeroberfläche in [!DNL AEM Assets View] {#AEM-Assets-View-UI-Extensibility}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
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

[!DNL AEM Assets View] unterstützt die Erweiterbarkeit der Benutzeroberfläche, sodass Sie Ihrer [!DNL Assets View]-Benutzeroberfläche benutzerdefinierte Benutzeroberflächenkomponenten für bestimmte Workflows und Geschäftsanforderungen hinzufügen können, die von den vorkonfigurierten Funktionen von [!DNL AEM Assets View] nicht erfüllt werden. Diese Erweiterbarkeitsfunktion der Benutzeroberfläche von [!DNL AEM Assets View] erhöht die Flexibilität und ermöglicht es Organisationen, die Benutzeroberfläche an bestimmte Workflows und Anforderungen anzupassen.\
Sie können Ihre Erweiterungen auf den Ebenen **Asset**, **Ordner** und **Sammlung** hinzufügen. Die hinzugefügte Erweiterung wird in einem eigenen Panel auf der Seite **Asset**, **Sammlung** oder **Ordnerdetails** **** angezeigt.

>[!IMPORTANT]
>
> * [!DNL AEM Assets View] Die Erweiterbarkeit der Benutzeroberfläche ist mit [[!DNL Assets Ultimate]](/help/assets/assets-ultimate-overview.md) verfügbar.
> * Um Zugriff auf die Erweiterbarkeit der Benutzeroberfläche von [!DNL Assets view] zu erhalten, [erstellen und senden Sie einen [!DNL Adobe] Kunden-Support-Fall](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).
> * Sie können Feedback zur Dokumentation geben, indem Sie **[!UICONTROL Detaillierte Feedback-Optionen]** erweitern und auf **[!UICONTROL Problem melden]** klicken.

## <a id="1"></a> Zugriff auf die Assets-Ansicht{#add-UI-Extensibility-in-AEM-Assets-View}

Führen Sie die im folgenden Bild genannten Schritte aus, um auf die [!DNL Assets View] zuzugreifen:
![access-assets-view-ui](/help/assets/assets/access-assets-view.jpg)

## Anzeigen von Benutzeroberflächenerweiterungen in [!DNL Assets View] {#ui-extensibility-panel-assets-view}

Navigieren Sie in [!DNL Assets View] zur Seite **[!UICONTROL Details]** eines Assets, Ordners oder einer Sammlung. Auf der Seite **[!UICONTROL Details]** wird die hinzugefügte Benutzeroberflächenerweiterung in einem eigenen Panel angezeigt.
![Mein Arbeitsbereich](/help/assets/assets/my-workspace-assets-view3.png)

## Voraussetzungen für das Hinzufügen der Erweiterbarkeitskomponente{#assets-view-ui-extensibility}

Sie müssen die folgenden Anforderungen erfüllen, um die Erweiterbarkeitskomponente zu Ihrer [!DNL Assets View UI] hinzuzufügen:

* [Sie haben Zugriff auf  [!DNL Assets View]](#1).
* Sie haben Zugriff auf [[!DNL Adobe app builder]](https://developer.adobe.com/app-builder/docs/overview/).
* Sie verfügen über die Berechtigung für Entwickelnde der Rolle „Systemadmin“ innerhalb der Organisation. Weitere Informationen finden Sie in [dieser Dokumentation](https://developer.adobe.com/uix/docs/guides/get-access/).
* [!DNL Adobe IO command line tool (AIO CLI)] ist auf Ihren lokalen Computern installiert. Dieses Tool ist für das Erstellen und Bereitstellen von Erweiterungsprojekten von entscheidender Bedeutung. Weitere Informationen [ Sie unter „Erstellen der ersten App Builder](https://developer.adobe.com/app-builder/docs/get_started/app_builder_get_started/first-app#local-environment-set-up)Anwendung (Authentifizierung für den Zugriff erforderlich)“.
* Grundlegendes Verständnis der Technologien [!DNL JavaScript], [!DNL Node.js] und [!DNL React].

## Hinzufügen der UI-Erweiterbarkeitskomponente zu [!DNL Assets View] {#ui-extensibility-in-assets-view}

1. Wichtige Informationen zu Benutzeroberflächenerweiterungen und dem [!DNL Adobe App Builder]-Framework finden Sie unter [Erste Schritte](https://developer.adobe.com/uix/docs/getting-started/). Erfahren Sie, wie die Erweiterbarkeit der Benutzeroberfläche die Integration einer benutzerdefinierten Logik und Benutzeroberfläche in [!DNL Adobe Experience Cloud services] ermöglicht, und lernen Sie die Architektur und den Workflow zur Implementierung von Benutzeroberflächenerweiterungen kennen.
1. Allgemeine Informationen zur Erweiterbarkeit der Benutzeroberfläche, einschließlich des Setups lokaler Umgebungen, der lokalen Vorschau, Veröffentlichung und Verwaltung, finden Sie in den [Handbüchern](https://developer.adobe.com/uix/docs/guides/).
1. Unter [Allgemeine Konzepte beim Erstellen von Erweiterungen](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/) erfahren Sie mehr über die Grundlagen, die zum Entwickeln einer Benutzeroberflächenerweiterung für die [!DNL AEM Assets View] erforderlich sind.
1. Fügen Sie benutzerdefinierte Seiten-Panels zur Oberfläche der [!DNL Assets View] hinzu. Die Host-Anwendung ([!DNL Assets View]) verwaltet diese Panels, um Benutzeroberflächeninteraktionen wie Umschalten und Deep-Linking zu verarbeiten. Erweiterungen verwenden den Erweiterungspunkt `aem/assets/details/1`, um benutzerdefinierte Panels zu integrieren, die Eigenschaften wie Panel-ID, Titel und Inhalts-URL festlegen. Entwickelnde registrieren benutzerdefinierte Panels mit der `getPanels()`-Methode und erstellen Routen, um benutzerdefinierte Inhalte anzuzeigen. Ausführliche Implementierungen, einschließlich API-Referenzen und Code-Beispielen, finden Sie unter [Detailansicht](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/).
1. Richten Sie Ihre lokale Umgebung ein und erstellen Sie Ihre erste Benutzeroberflächenerweiterung, um den Prozess der Entwicklung von Benutzeroberflächenerweiterungen in der [!DNL Assets View] aus erster Hand zu erleben. Weitere Informationen finden Sie unter [Schrittweise Entwicklung der Erweiterung für die AEM Assets-Ansicht](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/).
1. Richten Sie Ihre Anwendung mithilfe der AIO-CLI ein, um die grundlegende Erweiterungsstruktur und den erforderlichen Code zu generieren. Weitere Informationen finden Sie unter [Code-Generierung für die [!DNL AEM Assets View]](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/).
1. Testen Sie Ihre Erweiterungen lokal, um sicherzustellen, dass sie vor der Bereitstellung wie erwartet funktionieren. Führen Sie Ihre Erweiterung in einer vollständig isolierten Umgebung oder mit teilweiser Isolierung aus und verbinden Sie Ihre Erweiterung zum Testen mit der in der Produktion eingesetzten [!DNL AEM Assets View]. Weitere Informationen finden Sie unter [Fehlerbehebung – Erweiterbarkeit der [!DNL AEM Assets View] ](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/).

## Anpassen der Schnellaktionen und Aktionsleiste in der Assets-Ansicht {#customize-quick-actions-and-actions-bar}

Sie können anpassen, welche Aktionen angezeigt werden, wenn Sie ein oder mehrere Assets (Aktionsleiste) in der Assets-Ansicht auswählen. Mit der Assets-Ansicht können Sie auch anpassen, welche Aktionen angezeigt werden, wenn Sie auf „Weitere Optionen“ (…) auf der Asset-Karte klicken. Weitere Informationen finden Sie unter [Ansicht für das Durchsuchen](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/browse-view/).

## Öffnen benutzerdefinierter Dialogfelder in der Assets-Ansicht {#open-custom-dialogs-assets-view}

Die Assets-Ansicht bietet außerdem die Möglichkeit, benutzerdefinierte Dialogfelder mit einem Text Ihrer Wahl zu öffnen. Sie können dem Text auch Links hinzufügen. Weitere Informationen finden Sie unter [Modales API](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/#modal-api).
