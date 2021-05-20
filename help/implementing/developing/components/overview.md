---
title: Komponentenübersicht
description: Bei Komponenten handelt es sich um modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 100%

---

# Komponentenübersicht {#components-overview}

Diese Seite enthält einen Überblick über die Komponenten von Adobe Experience Manager (AEM), z. B. für die [Seitenbearbeitung](/help/sites-cloud/authoring/fundamentals/components.md).

## Was sind Komponenten? {#what-are-components}

Komponenten in AEM:

* Sind modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
* Sind wiederverwendbar.
* Werden als eigenständige Einheiten innerhalb eines Ordners des Repositorys entwickelt.
* Verfügen nicht über ausgeblendete Konfigurationsdateien.
* Können andere Komponenten enthalten.
* Können in einem beliebigen AEM-System überall ausgeführt werden und auch auf die Ausführung unter bestimmten Komponenten beschränkt sein.
* Verfügen über eine standardisierte Benutzeroberfläche.
* Verfügen über ein konfigurierbares Bearbeitungsverhalten.
* Verwenden Dialogfelder, die basierend auf Granite-UI-Komponenten mit Unterelementen erstellt werden.
* Werden mit [HTL](https://docs.adobe.com/content/help/de/experience-manager-htl/using/overview.html) entwickelt.
* Können für die Erstellung von angepassten Komponenten entwickelt werden, mit denen die Standardfunktionalität erweitert wird.

Da die Komponenten modular sind, haben Sie folgende Möglichkeiten:

* Entwickeln einer neuen Komponente auf Ihrer lokalen Instanz
* Bereitstellen dieser Komponente in Ihrer Testumgebung
* Bereitstellen in Ihrer Live-Authoring-Umgebung, in der Autoren bzw. Administratoren Inhalt hinzufügen und konfigurieren können
* Bereitstellen in Ihren Live-Veröffentlichungsumgebungen, in denen sie zum Rendern von Inhalten für Besucher Ihrer Website verwenden können

Für jede AEM-Komponente gilt Folgendes:

* Ist ein Ressourcentyp.
* Ist eine Sammlung mit Skripten, mit denen eine bestimmte Funktion vollständig realisiert wird.
* Funktioniert auch isoliert (also in AEM oder einem Portal).

## AEM-Kernkomponenten {#aem-core-components}

[AEM-Kernkomponenten](https://docs.adobe.com/content/help/de/experience-manager-core-components/using/introduction.html) sind eine Reihe standardisierter Web-Content-Management-Komponenten (WCM) für AEM, um die Entwicklungszeit zu verkürzen und die Wartungskosten Ihrer Websites zu senken.

Die Kernkomponenten werden mit AEM as a Cloud Service bereitgestellt; das [WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) veranschaulicht, wie Komponenten implementiert und verwendet werden. Die Komponenten werden mit dem gesamten Quell-Code bereitgestellt und können unverändert oder als Ausgangspunkte für geänderte oder erweiterte Komponenten genutzt werden.

### Anzeigen der verfügbaren Komponenten {#viewing-available-components}

Einen Überblick über alle verfügbaren Komponenten Ihrer AEM-Instanz erhalten Sie in der [Komponentenkonsole](/help/sites-cloud/authoring/features/components-console.md).

Alternativ hierzu können Sie auch CRXDE Lite verwenden, um eine Liste mit allen Komponenten abzurufen, die im Repository verfügbar sind.

1. Wählen Sie in **[!UICONTROL CRXDE Lite]** in der Symbolleiste die Option **[!UICONTROL Tools]** und dann **[!UICONTROL Abfrage]**, um die Registerkarte **[!UICONTROL Abfrage]** zu öffnen.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Abfrage]** die Option `XPath` als **[!UICONTROL Typ]**.

1. Geben Sie in das Feld **[!UICONTROL Abfrage]** folgende Zeichenfolge ein:

   `//element(*, cq:Component)`

1. Wenn Sie auf **[!UICONTROL Ausführen]** klicken, werden die Komponenten aufgelistet.
