---
title: Komponentenübersicht
description: Bei Komponenten handelt es sich um modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
source-git-commit: bbd845079cb688dc3e62e2cf6b1a63c49a92f6b4
workflow-type: tm+mt
source-wordcount: '376'
ht-degree: 56%

---

# Komponentenübersicht {#components-overview}

Diese Seite enthält einen Überblick über die Komponenten von Adobe Experience Manager (AEM), z. B. für die [Seitenbearbeitung](/help/sites-cloud/authoring/page-editor/components.md).

## Was sind Komponenten? {#what-are-components}

* Sind modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
* Wiederverwendbar.
* Werden als eigenständige Einheiten innerhalb eines Ordners des Repositorys entwickelt.
* Es gibt keine ausgeblendeten Konfigurationsdateien.
* Sie können andere Komponenten enthalten.
* Sie können überall in jedem AEM ausgeführt werden und auch auf die Ausführung unter bestimmten Komponenten beschränkt sein.
* Verfügen über eine standardisierte Benutzeroberfläche.
* Verfügen über ein konfigurierbares Bearbeitungsverhalten.
* Verwenden Sie Dialogfelder, die basierend auf Granite-UI-Komponenten mit Unterelementen erstellt werden.
* Sie werden mithilfe von [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html?lang=de).
* Sie können entwickelt werden, um benutzerdefinierte Komponenten zu erstellen, die die Standardfunktionalität erweitern.

Da Komponenten modular sind, haben Sie folgende Möglichkeiten:

* Entwickeln Sie eine neue Komponente auf Ihrer lokalen Instanz.
* Bereitstellen dieser Komponente in Ihrer Testumgebung
* Bereitstellen in Ihrer Live-Authoring-Umgebung, in der Autoren bzw. Administratoren Inhalt hinzufügen und konfigurieren können
* Bereitstellen in Ihren Live-Veröffentlichungsumgebungen, in denen sie zum Rendern von Inhalten für Besucher Ihrer Website verwendet werden.

Für jede AEM-Komponente gilt Folgendes:

* Ist ein Ressourcentyp.
* Ist eine Sammlung mit Skripten, mit denen eine bestimmte Funktion vollständig realisiert wird.
* Funktioniert auch isoliert (also in AEM oder einem Portal).

## AEM-Kernkomponenten {#aem-core-components}

[Die AEM Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind eine Reihe standardisierter Web Content Management (WCM)-Komponenten, mit denen AEM die Entwicklungszeit verkürzen und die Wartungskosten Ihrer Websites reduzieren können.

Die Kernkomponenten werden mit AEM as a Cloud Service bereitgestellt; das [WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) veranschaulicht, wie Komponenten implementiert und verwendet werden. Die Komponenten werden mit dem gesamten Quell-Code bereitgestellt und können unverändert oder als Ausgangspunkte für geänderte oder erweiterte Komponenten genutzt werden.

### Anzeigen der verfügbaren Komponenten {#viewing-available-components}

Eine Übersicht über alle verfügbaren Komponenten in Ihrer AEM-Instanz erhalten Sie über die [Komponentenkonsole](/help/sites-cloud/authoring/components-console.md).

Alternativ können Sie auch CRXDE Lite verwenden, um eine Liste aller im Repository verfügbaren Komponenten zu erhalten.

1. Wählen Sie in **[!UICONTROL CRXDE Lite]** in der Symbolleiste die Option **[!UICONTROL Tools]** und dann **[!UICONTROL Abfrage]**, um die Registerkarte **[!UICONTROL Abfrage]** zu öffnen.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Abfrage]** die Option `XPath` als **[!UICONTROL Typ]**.

1. Im **[!UICONTROL Abfrage]** Geben Sie folgende Zeichenfolge in das Eingabefeld ein:

   `//element(*, cq:Component)`

1. Wenn Sie auf **[!UICONTROL Ausführen]** klicken, werden die Komponenten aufgelistet.
