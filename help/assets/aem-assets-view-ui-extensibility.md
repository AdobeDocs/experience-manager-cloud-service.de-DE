---
title: Erweiterbarkeit der Benutzeroberfläche der AEM Assets-Ansicht
description: Erfahren Sie mehr über die Erweiterbarkeitsfunktion der Benutzeroberfläche von AEM Assets View. Die AEM Assets View-Benutzeroberfläche ermöglicht das Hinzufügen benutzerdefinierter Benutzeroberflächenkomponenten, um bestimmte Geschäftsanforderungen zu erfüllen.
feature: App Builder
role: User, Developer
exl-id: a11f7043-17cf-4331-b76c-d3db099c2411
source-git-commit: bbb183470e12c0fc81c821fc2e0c1e7d77c33707
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 5%

---

# Erweiterbarkeit der Benutzeroberfläche der AEM Assets-Ansicht{#AEM-Assets-View-UI-Extensibility}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

AEM Assets View verfügt über eine Funktion zur Erweiterbarkeit der Benutzeroberfläche. Diese Funktion ermöglicht es Benutzenden, benutzerdefinierte Benutzeroberflächenkomponenten zur Assets-Ansichts-Benutzeroberfläche hinzuzufügen, um bestimmte Geschäftsanforderungen zu erfüllen, die von den vorkonfigurierten Funktionen der AEM Assets-Ansicht nicht erfüllt werden. Diese Erweiterbarkeitsfunktion erhöht die Flexibilität der AEM Assets-Ansicht, die es Unternehmen ermöglicht, die Benutzeroberfläche an bestimmte Workflows und Anforderungen anzupassen.
Sie können Ihre Erweiterungen zur Asset-, Ordner- und Sammlungsebene hinzufügen. Die hinzugefügte Erweiterung wird in einem speziellen Bedienfeld auf der Seite mit Asset-, Sammlungs- oder Ordnerdetails angezeigt.

>[!IMPORTANT]
>
> * Die Erweiterbarkeit der AEM Assets-Ansicht-Benutzeroberfläche ist mit [Assets Ultimate](/help/assets/assets-ultimate-overview.md) verfügbar.
> * Um Zugriff auf die Erweiterbarkeit der Assets-Ansichtsbenutzeroberfläche zu erhalten[ erstellen und senden Sie einen Adobe-Support-Fall](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).
> * Sie können Feedback zur Dokumentation geben, indem Sie die Optionen für detailliertes Feedback erweitern und auf Problem melden klicken.

## <a id="1"></a> Zugriff auf Assets View

Greifen Sie wie folgt auf die Assets-Ansicht zu:
![access-assets-view-ui](/help/assets/assets/access-assets-view.jpg)

## Wo werden Benutzeroberflächenerweiterungen in der Assets-Ansichts-Benutzeroberfläche angezeigt? {#ui-extensibility-panel-assets-view}

Navigieren Sie in der Assets-Ansicht zur Detailseite eines Assets, Ordners oder einer Sammlung. Diese Detailseite verfügt über ein dediziertes Bedienfeld, das die hinzugefügte UI-Erweiterung anzeigt.
![Mein Arbeitsbereich](/help/assets/assets/my-workspace-assets-view3.png)


## Voraussetzungen für das Hinzufügen der Erweiterbarkeitskomponente

* [Zugriff auf Assets View](#1).
* Zugriff auf den [Adobe App Builder](https://developer.adobe.com/app-builder/docs/overview/).
* Berechtigung für Entwickler der Systemadministratorrolle innerhalb der Organisation. Weitere [ finden Sie ](https://developer.adobe.com/uix/docs/guides/get-access/)hier).
* Das Adobe IO Command Line Tool (AIO CLI) muss auf Ihren lokalen Computern installiert sein. Dieses Tool ist für das Erstellen und Bereitstellen von Erweiterungsprojekten von entscheidender Bedeutung. Weitere [ finden Sie ](https://developer.adobe.com/app-builder/docs/getting_started/#local-environment-set-up)hier).
* Gute Kenntnisse der Technologien von JavaScript, Node.js und React.

## Hinzufügen einer Benutzeroberflächen-Erweiterbarkeitskomponente in der Assets-Ansichts-Benutzeroberfläche{#Adding-UI-Extensibility-Component-on-Assets-View}

1. Siehe [Erste Schritte](https://developer.adobe.com/uix/docs/getting-started/) für wichtige Informationen zu Benutzeroberflächenerweiterungen und dem Adobe-App Builder-Framework. Erfahren Sie, wie die Erweiterbarkeit der Benutzeroberfläche die Integration von benutzerdefinierter Logik und Benutzeroberfläche in Adobe Experience Cloud-Services ermöglicht, und lernen Sie die Architektur und den Workflow zur Implementierung von Benutzeroberflächenerweiterungen kennen.
1. Siehe [Handbücher](https://developer.adobe.com/uix/docs/guides/) für allgemeine Informationen zur Erweiterbarkeit der Benutzeroberfläche, einschließlich der Einrichtung lokaler Umgebungen, der lokalen Vorschau, Veröffentlichung und Verwaltung.
1. Unter [Allgemeine Konzepte beim Erstellen von Erweiterungen](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/) finden Sie die Grundlagen, die zum Entwickeln einer Benutzeroberflächenerweiterung für die AEM Assets-Ansicht erforderlich sind.
1. Hinzufügen benutzerdefinierter Seitenbereiche zur Assets View-Oberfläche. Die Host-Anwendung (Assets-Ansicht) verwaltet diese Bedienfelder, um Benutzeroberflächeninteraktionen wie Umschalten und Deep-Linking zu verarbeiten. Erweiterungen verwenden den `aem/assets/details/1` Erweiterungspunkt, um benutzerdefinierte Bedienfelder zu integrieren, die Eigenschaften wie Bedienfeld-ID, Titel und Inhalts-URL angeben. Entwickler registrieren benutzerdefinierte Bedienfelder mit der `getPanels()`-Methode und erstellen Routen, um benutzerdefinierte Inhalte anzuzeigen. Ausführliche Implementierungen, einschließlich API-Referenzen und Code-Beispielen, finden Sie unter [Detailansicht](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/).
1. Richten Sie Ihre lokale Umgebung ein und erfahren Sie, wie Sie Benutzeroberflächenerweiterungen in der Assets-Ansicht aus erster Hand entwickeln, indem Sie Ihre erste Benutzeroberflächenerweiterung erstellen. Weitere [ finden Sie unter &quot;-für-Schritt-Entwicklung ](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/) AEM Assets View“.
1. Richten Sie Ihre App mithilfe der AIO-CLI ein, um die grundlegende Erweiterungsstruktur und den erforderlichen Code zu generieren. Siehe [Code-Generierung für die AEM Assets-Ansicht](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/) für detaillierte Informationen.
1. Testen Sie Ihre Erweiterungen lokal, um sicherzustellen, dass sie vor der Bereitstellung wie erwartet funktionieren. Führen Sie Ihre Erweiterung in einer vollständig isolierten Umgebung oder mit teilweiser Isolierung aus und verbinden Sie Ihre Erweiterung zum Testen mit der AEM Assets-Produktions-Ansicht. Siehe [Fehlerbehebung - Erweiterbarkeit der AEM Assets-Ansicht](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/) für detaillierte Informationen.
