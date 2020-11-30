---
title: Komponentenübersicht
description: Bei Komponenten handelt es sich um modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
translation-type: tm+mt
source-git-commit: 83c27daae4e8ae2ae6a8f115c9da9527971c6ecb
workflow-type: tm+mt
source-wordcount: '391'
ht-degree: 53%

---


# Komponentenübersicht {#components-overview}

Diese Seite enthält eine Übersicht über die Komponenten von Adobe Experience Manager (AEM), z. B. für die [Seitenbearbeitung](/help/sites-cloud/authoring/fundamentals/components.md).

## Was sind Komponenten? {#what-are-components}

Komponenten in AEM sind:

* Modulare Einheiten, die spezielle Funktionen zur Darstellung Ihrer Inhalte auf Ihrer Website implementieren.
* Wiederverwendbar.
* Entwickelt als eigenständige Einheiten in einem Ordner des Repositorys.
* Verfügen nicht über ausgeblendete Konfigurationsdateien.
* Können andere Komponenten enthalten.
* Kann überall in einem beliebigen AEM ausgeführt werden und kann auch auf die Ausführung unter bestimmten Komponenten beschränkt sein.
* Verfügen über eine standardisierte Benutzeroberfläche.
* Sie können das Bearbeitungsverhalten konfigurieren.
* Verwenden Sie Dialogfelder, die mit Unterelementen basierend auf Granite-UI-Komponenten erstellt wurden.
* werden mit [HTL](https://docs.adobe.com/content/help/de-DE/experience-manager-htl/using/overview.html)entwickelt.
* Können für die Erstellung von angepassten Komponenten entwickelt werden, mit denen die Standardfunktionalität erweitert wird.

Da die Komponenten modular sind, haben Sie folgende Möglichkeiten:

* Entwickeln einer neuen Komponente auf Ihrer lokalen Instanz
* Stellen Sie es in Ihrer Test-Umgebung bereit.
* Bereitstellen in Ihrer Live-Authoring-Umgebung, in der Autoren bzw. Administratoren Inhalt hinzufügen und konfigurieren können
* Stellen Sie sie in Ihrer (den) Live-Veröffentlichungs-Umgebung(en) bereit, in der (denen) sie zum Rendern von Inhalten für Besucher auf Ihrer Website verwendet werden.

Für jede AEM-Komponente gilt Folgendes:

* Ist ein Ressourcentyp.
* Ist eine Sammlung mit Skripten, mit denen eine bestimmte Funktion vollständig realisiert wird.
* Kann isoliert funktionieren, d. h. entweder innerhalb eines AEM oder eines Portals.

## AEM-Kernkomponenten {#aem-core-components}

[Die AEM Kernkomponenten](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) sind eine Reihe standardisierter Webkomponenten (WCM), mit denen AEM die Entwicklungszeit verkürzen und die Wartungskosten Ihrer Websites senken können.

Die Kernkomponenten werden als Cloud Service AEM und das [WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) veranschaulicht, wie Komponenten implementiert und verwendet werden. Die Komponenten werden mit dem gesamten Quellcode bereitgestellt und können unverändert oder als Ausgangspunkte für geänderte oder erweiterte Komponenten genutzt werden.

### Anzeigen der verfügbaren Komponenten {#viewing-available-components}

Eine Übersicht über alle verfügbaren Komponenten Ihrer AEM-Instanz erhalten Sie in der [Komponentenkonsole](/help/sites-cloud/authoring/features/components-console.md).

Alternativ hierzu können Sie auch CRXDE Lite verwenden, um eine Liste mit allen Komponenten abzurufen, die im Repository verfügbar sind.

1. In **[!UICONTROL CRXDE Lite]**, select **[!UICONTROL Tools]** from the toolbar, then **[!UICONTROL Query]**, which opens the **[!UICONTROL Query]** tab.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Query]** (Abfrage) für `XPath`Type **[!UICONTROL (Typ) die Option]**.

1. Geben Sie in das Feld **[!UICONTROL Abfrage]** folgende Zeichenfolge ein:

   `//element(*, cq:Component)`

1. Click **[!UICONTROL Execute]** and the components are listed.

