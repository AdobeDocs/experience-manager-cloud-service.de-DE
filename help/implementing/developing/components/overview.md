---
title: Komponentenübersicht
description: Bei Komponenten handelt es sich um modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
exl-id: 0fdc99e7-2103-448d-8217-d5d52c94acea
source-git-commit: 856266faf4cb99056b1763383d611e9b2c3c13ea
workflow-type: tm+mt
source-wordcount: '387'
ht-degree: 86%

---

# Komponentenübersicht {#components-overview}

Diese Seite enthält einen Überblick über die Komponenten von Adobe Experience Manager (AEM), z. B. für die [Seitenbearbeitung](/help/sites-cloud/authoring/fundamentals/components.md).

## Was sind Komponenten? {#what-are-components}

Komponenten in AEM:

* Sind modulare Einheiten, mit denen spezifische Funktionalität zum Darstellen von Inhalten auf Ihrer Website realisiert wird.
* Sind wiederverwendbar.
* Werden als eigenständige Einheiten innerhalb eines Ordners des Repositorys entwickelt.
* Es gibt keine ausgeblendeten Konfigurationsdateien.
* Kann andere Komponenten enthalten.
* Können in einem beliebigen AEM-System überall ausgeführt werden und auch auf die Ausführung unter bestimmten Komponenten beschränkt sein.
* Verfügen über eine standardisierte Benutzeroberfläche.
* Verfügen über ein konfigurierbares Bearbeitungsverhalten.
* Verwenden Dialogfelder, die basierend auf Granite-UI-Komponenten mit Unterelementen erstellt werden.
* Werden mit [HTL](https://experienceleague.adobe.com/docs/experience-manager-htl/using/overview.html?lang=de) entwickelt.
* Kann entwickelt werden, um benutzerdefinierte Komponenten zu erstellen, die die Standardfunktion erweitern.

Da Komponenten modular sind, haben Sie folgende Möglichkeiten:

* Entwickeln Sie eine neue Komponente auf Ihrer lokalen Instanz.
* Bereitstellen dieser Komponente in Ihrer Testumgebung
* Bereitstellen in Ihrer Live-Authoring-Umgebung, in der Autoren bzw. Administratoren Inhalt hinzufügen und konfigurieren können
* Bereitstellen in Ihren Live-Veröffentlichungsumgebungen, in denen sie zum Rendern von Inhalten für Besucher Ihrer Website verwenden können

Für jede AEM-Komponente gilt Folgendes:

* Ist ein Ressourcentyp.
* Ist eine Sammlung mit Skripten, mit denen eine bestimmte Funktion vollständig realisiert wird.
* Funktioniert auch isoliert (also in AEM oder einem Portal).

## AEM-Kernkomponenten {#aem-core-components}

[AEM-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind eine Reihe standardisierter Web-Content-Management-Komponenten (WCM) für AEM, um die Entwicklungszeit zu verkürzen und die Wartungskosten Ihrer Websites zu senken.

Die Kernkomponenten werden mit AEM as a Cloud Service bereitgestellt; das [WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) veranschaulicht, wie Komponenten implementiert und verwendet werden. Die Komponenten werden mit dem gesamten Quell-Code bereitgestellt und können unverändert oder als Ausgangspunkte für geänderte oder erweiterte Komponenten genutzt werden.

### Anzeigen der verfügbaren Komponenten {#viewing-available-components}

Einen Überblick über alle verfügbaren Komponenten Ihrer AEM-Instanz erhalten Sie in der [Komponentenkonsole](/help/sites-cloud/authoring/features/components-console.md).

Alternativ können Sie auch CRXDE Lite verwenden, um eine Liste aller im Repository verfügbaren Komponenten zu erhalten.

1. Wählen Sie in **[!UICONTROL CRXDE Lite]** in der Symbolleiste die Option **[!UICONTROL Tools]** und dann **[!UICONTROL Abfrage]**, um die Registerkarte **[!UICONTROL Abfrage]** zu öffnen.

1. Wählen Sie auf der Registerkarte **[!UICONTROL Abfrage]** die Option `XPath` als **[!UICONTROL Typ]**.

1. Geben Sie in das Feld **[!UICONTROL Abfrage]** folgende Zeichenfolge ein:

   `//element(*, cq:Component)`

1. Wenn Sie auf **[!UICONTROL Ausführen]** klicken, werden die Komponenten aufgelistet.
