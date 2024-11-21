---
title: Erweiterbarkeit der Benutzeroberfläche der AEM Assets-Ansicht
description: Erfahren Sie mehr über die Erweiterbarkeit der Benutzeroberfläche in der AEM Assets-Ansicht. Die Benutzeroberfläche der AEM Assets-Ansicht ermöglicht das Hinzufügen benutzerdefinierter Benutzeroberflächen-Komponenten, um bestimmten Geschäftsanforderungen gerecht zu werden.
feature: App Builder
role: User, Developer
exl-id: a11f7043-17cf-4331-b76c-d3db099c2411
source-git-commit: af7e6ab40212dfa3d91cda80a76b1b6b01dd65a3
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 3%

---

# Erweiterbarkeit der Benutzeroberfläche der AEM Assets-Ansicht{#AEM-Assets-View-UI-Extensibility}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Die AEM Assets-Ansicht verfügt über die Erweiterbarkeit der Benutzeroberfläche. Mit dieser Funktion können Benutzer benutzerdefinierte UI-Komponenten zur Assets View-Benutzeroberfläche hinzufügen, um bestimmten Geschäftsanforderungen gerecht zu werden, die die vordefinierten Funktionen der AEM Assets-Ansicht nicht erfüllen. Diese Erweiterungsfunktion verbessert die Flexibilität der AEM Assets-Ansicht, die es Unternehmen ermöglicht, die Benutzeroberfläche an bestimmte Workflows und Anforderungen anzupassen.
Sie können Ihre Erweiterungen der Asset-, Ordner- und Sammlungsebene hinzufügen. Die hinzugefügte Erweiterung wird in einem dedizierten Bedienfeld auf der Seite &quot;Asset&quot;, &quot;Sammlung&quot;oder &quot;Ordnerdetails&quot;angezeigt.

>[!IMPORTANT]
>
> * Die Erweiterbarkeit der Benutzeroberfläche der AEM Assets-Ansicht ist mit [Assets Ultimate](/help/assets/assets-ultimate-overview.md) verfügbar.
> * Die Erweiterbarkeit der Assets-Ansicht-Benutzeroberfläche steht Ihnen als Beta-Version zur Verfügung. Um frühzeitigen Zugriff auf die Erweiterbarkeit der Benutzeroberfläche der Assets-Ansicht zu erhalten, erstellen und senden Sie eine Adobe-Support-Anfrage](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).[
> * Sie können Feedback zur Dokumentation bereitstellen, indem Sie die Optionen für detailliertes Feedback erweitern und auf Problem melden klicken.

## <a id="1"></a> Zugriff auf die Assets-Ansicht

Greifen Sie wie folgt auf die Assets-Ansicht zu:
![access-assets-view-ui](/help/assets/assets/access-assets-view.jpg)

## Wo werden Benutzeroberflächenerweiterungen auf der Benutzeroberfläche der Assets-Ansicht angezeigt? {#ui-extensibility-panel-assets-view}

Navigieren Sie in der Assets-Ansicht zur Detailseite eines Assets, Ordners oder einer Sammlung. Diese Detailseite verfügt über ein dediziertes Bedienfeld, in dem die hinzugefügte UI-Erweiterung angezeigt wird.
![mein Arbeitsbereich](/help/assets/assets/my-workspace-assets-view3.png)


## Voraussetzungen für das Hinzufügen der Erweiterungskomponente

* [Zugriff auf die Assets-Ansicht](#1).
* Zugriff auf den [Adobe-App-Builder](https://developer.adobe.com/app-builder/docs/overview/), der standardmäßig in [Assets Ultimate](/help/assets/assets-ultimate-overview.md) enthalten ist.
* Berechtigung zur Entwicklung der Systemadministratorrolle innerhalb der Organisation. Weitere Informationen finden Sie unter [this](https://developer.adobe.com/uix/docs/guides/get-access/) .
* Adobe IO Befehlszeilen-Tool (AIO CLI) muss auf Ihren lokalen Computern installiert sein. Dieses Tool ist für das Erstellen und Bereitstellen von Erweiterungsprojekten von wesentlicher Bedeutung. Weitere Informationen finden Sie unter [this](https://developer.adobe.com/app-builder/docs/getting_started/#local-environment-set-up) .
* Gutes Verständnis der JavaScript-, Node.js- und React-Technologien.

## Hinzufügen der Erweiterungskomponente der Benutzeroberfläche in der Benutzeroberfläche der Assets-Ansicht{#Adding-UI-Extensibility-Component-on-Assets-View}

1. Wichtige Informationen zu Benutzeroberflächen-Erweiterungen und dem Adobe App Builder-Framework finden Sie unter [Erste Schritte](https://developer.adobe.com/uix/docs/getting-started/) . Erfahren Sie, wie die Erweiterbarkeit der Benutzeroberfläche die Integration von benutzerdefinierter Logik und Benutzeroberfläche in Adobe Experience Cloud-Services ermöglicht, und lernen Sie die Architektur und den Arbeitsablauf für die Implementierung von UI-Erweiterungen kennen.
1. Allgemeine Informationen zur Erweiterbarkeit der Benutzeroberfläche, einschließlich der Einrichtung der lokalen Umgebung, der lokalen Vorschau, der Veröffentlichung und der Verwaltung, finden Sie unter [Handbücher](https://developer.adobe.com/uix/docs/guides/) .
1. Siehe [Allgemeine Konzepte in Erstellen von Erweiterungen](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/commons/) , um die Grundlagen zu verstehen, die zum Entwickeln einer UI-Erweiterung für die AEM Assets-Ansicht erforderlich sind.
1. Fügen Sie benutzerdefinierte Seitenbedienfelder zur Benutzeroberfläche der Assets-Ansicht hinzu. Die Host-Anwendung (Assets-Ansicht) verwaltet diese Bedienfelder, um Benutzeroberflächeninteraktionen wie Umschalten und Deep-Linking zu handhaben. Erweiterungen verwenden den Erweiterungspunkt &quot;`aem/assets/details/1`&quot;, um benutzerdefinierte Bedienfelder zu integrieren, die Eigenschaften wie Bedienfeld-ID, Titel und Inhalts-URL angeben. Entwickler registrieren benutzerdefinierte Bedienfelder mit der Methode `getPanels()` und erstellen Routen, um benutzerdefinierte Inhalte anzuzeigen. Eine detaillierte Implementierung, einschließlich API-Referenzen und Codebeispielen, finden Sie unter [Detailansicht](https://developer.adobe.com/uix/docs/services/aem-assets-view/api/details-view/).
1. Richten Sie Ihre lokale Umgebung ein und erleben Sie die Entwicklung von Benutzeroberflächenerweiterungen in der Assets-Ansicht aus, indem Sie Ihre erste UI-Erweiterung erstellen. Weitere Informationen finden Sie unter [Schrittweise Entwicklung der AEM Assets-Ansichtserweiterung](https://developer.adobe.com/uix/docs/services/aem-assets-view/extension-development/) .
1. Richten Sie Ihre App mithilfe der AIO-CLI ein, um die grundlegende Erweiterungsstruktur und den erforderlichen Code zu generieren. Detaillierte Informationen finden Sie unter [Codegenerierung für die AEM Assets-Ansicht](https://developer.adobe.com/uix/docs/services/aem-assets-view/code-generation/) .
1. Testen Sie Ihre Erweiterungen lokal, um sicherzustellen, dass sie vor der Bereitstellung wie erwartet funktionieren. Führen Sie Ihre Erweiterung in einer vollständig isolierten Umgebung oder mit partieller Isolierung aus und verbinden Sie Ihre Erweiterung zum Testen mit der Produktions-AEM Assets-Ansicht. Detaillierte Informationen finden Sie unter [Fehlerbehebung - AEM Assets View Extensibility](https://developer.adobe.com/uix/docs/services/aem-assets-view/debug/) .
