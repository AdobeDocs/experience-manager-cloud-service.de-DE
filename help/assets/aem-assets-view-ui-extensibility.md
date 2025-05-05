---
title: Aktivieren der Erweiterbarkeit der Benutzeroberfläche in [!DNL AEM Assets View]
description: Erfahren Sie mehr über die Erweiterbarkeit der Benutzeroberfläche von  [!DNL AEM Assets View]. [!DNL AEM Assets View] -UI, die das Hinzufügen benutzerdefinierter Benutzeroberflächenkomponenten ermöglicht, um bestimmte Geschäftsanforderungen zu erfüllen.
feature: App Builder
role: User, Developer
exl-id: a11f7043-17cf-4331-b76c-d3db099c2411
source-git-commit: 969860593670ce490cc688a92c349addb952b3b4
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 4%

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

[!DNL AEM Assets View] unterstützt die Erweiterbarkeit der Benutzeroberfläche, sodass Sie Ihrer [!DNL Assets View]-Benutzeroberfläche benutzerdefinierte UI-Komponenten für bestimmte Workflows und Geschäftsanforderungen hinzufügen können, die von den vorkonfigurierten Funktionen von [!DNL AEM Assets View] nicht erfüllt werden. Diese Erweiterbarkeitsfunktion der Benutzeroberfläche von [!DNL AEM Assets View] erhöht die Flexibilität und ermöglicht es Unternehmen, die Benutzeroberfläche an bestimmte Workflows und Anforderungen anzupassen.\
Sie können Ihre Erweiterungen auf den Ebenen **Asset**, **Ordner** und **Sammlung** hinzufügen. Die hinzugefügte Erweiterung wird in einem eigenen Bedienfeld auf der Seite **Asset**, **Collection** oder **Folder** **[!UICONTROL Details]** angezeigt.

>[!IMPORTANT]
>
> * [!DNL AEM Assets View] Erweiterbarkeit der Benutzeroberfläche ist mit [[!DNL Assets Ultimate]](/help/assets/assets-ultimate-overview.md) verfügbar.
> * Um Zugriff auf die Erweiterbarkeit [!DNL Assets view] Benutzeroberfläche zu erhalten[ erstellen und senden Sie einen  [!DNL Adobe] -Support-Fall](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).
> * Sie können Feedback zur Dokumentation geben, indem Sie **[!UICONTROL Optionen für detailliertes Feedback]** erweitern und auf **[!UICONTROL Problem melden]** klicken.

## <a id="1"></a> Zugriff auf die Assets-Ansicht{#add-UI-Extensibility-in-AEM-Assets-View}

Führen Sie die in der folgenden Abbildung genannten Schritte aus, um auf die [!DNL Assets View] zuzugreifen:
![access-assets-view-ui](/help/assets/assets/access-assets-view.jpg)

## Anzeigen von Benutzeroberflächenerweiterungen in [!DNL Assets View] {#ui-extensibility-panel-assets-view}

Navigieren Sie in [!DNL Assets View] zur **[!UICONTROL Details]** eines Assets, Ordners oder einer Sammlung. Auf **[!UICONTROL Seite]**&#x200B;Details“ wird die hinzugefügte Benutzeroberflächenerweiterung in einem speziellen Bedienfeld angezeigt.
![Mein Arbeitsbereich](/help/assets/assets/my-workspace-assets-view3.png)

## Voraussetzungen für das Hinzufügen der Erweiterbarkeitskomponente{#assets-view-ui-extensibility}

Sie müssen die folgenden Anforderungen erfüllen, um die Erweiterbarkeitskomponente zu Ihrer [!DNL Assets View UI] hinzuzufügen:

* [Zugriff auf [!DNL Assets View]](#1).
* Zugriff auf die [[!DNL Adobe app builder]](https://developer.adobe.com/app-builder/docs/overview/).
* Berechtigung für Entwickler der Systemadministratorrolle innerhalb der Organisation. Weitere Informationen finden [ in ](https://developer.adobe.com/uix/docs/guides/get-access/) Dokumentation .
* [!DNL Adobe IO command line tool (AIO CLI)] ist auf Ihren lokalen Rechnern installiert. Dieses Tool ist für das Erstellen und Bereitstellen von Erweiterungsprojekten von entscheidender Bedeutung. Weitere Informationen finden [ in ](https://developer.adobe.com/app-builder/docs/getting_started/#local-environment-set-up) Dokumentation .
* Ein gutes Verständnis von [!DNL JavaScript]-, [!DNL Node.js]- und [!DNL React].

## Hinzufügen der UI-Erweiterbarkeitskomponente zu [!DNL Assets View] {#ui-extensibility-in-assets-view}

1. Siehe [Erste Schritte](https://developer.adobe.com/uix/docs/getting-started/) für wichtige Informationen zu Benutzeroberflächenerweiterungen und dem [!DNL Adobe App Builder]-Framework. Erfahren Sie, wie die Erweiterbarkeit der Benutzeroberfläche die Integration von benutzerdefinierter Logik und Benutzeroberfläche in [!DNL Adobe Experience Cloud services] ermöglicht, und lernen Sie die Architektur und den Workflow zur Implementierung von Benutzeroberflächenerweiterungen kennen.
1. Siehe [Handbücher](https://developer.adobe.com/uix/docs/guides/) für allgemeine Informationen zur Erweiterbarkeit der Benutzeroberfläche, einschließlich der Einrichtung lokaler Umgebungen, der lokalen Vorschau, Veröffentlichung und Verwaltung.
1. Unter [Allgemeine Konzepte beim Erstellen von Erweiterungen](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/) erfahren Sie mehr über die Grundlagen, die zum Entwickeln einer Benutzeroberflächenerweiterung für die [!DNL AEM Assets View] erforderlich sind.
1. Hinzufügen benutzerdefinierter Seitenbereiche zur [!DNL Assets View]. Die Host-Anwendung ([!DNL Assets View]) verwaltet diese Bedienfelder, um Benutzeroberflächeninteraktionen wie Umschalten und Deep-Linking zu verarbeiten. Erweiterungen verwenden den `aem/assets/details/1` Erweiterungspunkt, um benutzerdefinierte Bedienfelder zu integrieren, die Eigenschaften wie Bedienfeld-ID, Titel und Inhalts-URL angeben. Entwickler registrieren benutzerdefinierte Bedienfelder mit der `getPanels()`-Methode und erstellen Routen, um benutzerdefinierte Inhalte anzuzeigen. Ausführliche Implementierungen, einschließlich API-Referenzen und Code-Beispielen, finden Sie unter [Detailansicht](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/).
1. Richten Sie Ihre lokale Umgebung ein und erstellen Sie Ihre erste Benutzeroberflächenerweiterung, um den Prozess der Entwicklung von Benutzeroberflächenerweiterungen in [!DNL Assets View] aus erster Hand zu erleben. Weitere [ finden Sie unter &quot;-für-Schritt-Entwicklung ](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/) AEM Assets View“.
1. Richten Sie Ihre Anwendung mithilfe der AIO-CLI ein, um die grundlegende Erweiterungsstruktur und den erforderlichen Code zu generieren. Siehe [Code-Generierung für [!DNL AEM Assets View]](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/) für detaillierte Informationen.
1. Testen Sie Ihre Erweiterungen lokal, um sicherzustellen, dass sie vor der Bereitstellung wie erwartet funktionieren. Führen Sie Ihre Erweiterung in einer vollständig isolierten Umgebung oder mit teilweiser Isolierung aus und verbinden Sie Ihre Erweiterung zum Testen mit dem [!DNL AEM Assets View]. Siehe [Fehlerbehebung  [!DNL AEM Assets View] Erweiterbarkeit](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/) für detaillierte Informationen.
