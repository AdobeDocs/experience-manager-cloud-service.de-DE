---
title: Konsole „Live Copy-Übersicht“
description: Erfahren Sie mehr über die Grundlagen der Live Copy-Übersichtskonsole, um den Status Ihrer Live-Kopien schnell zu verstehen und Inhalte zu synchronisieren.
feature: Multi Site Manager
role: Administrator
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 23%

---


# Konsole „Live Copy-Übersicht“{#live-copy-overview-console}

Die Konsole **Übersicht über die Live-Kopie** ermöglicht Ihnen Folgendes:

* Anzeigen/Verwalten der Vererbung einer Site.
   * Ansicht der Baum- und der zugehörigen Live Copy-Struktur sowie des Vererbungsstatus
   * Ändern des Vererbungsstatus, z. B. Aussetzen und Wiederaufnehmen
   * Eigenschaften &quot;Ansicht-Blueprint&quot;und &quot;Live Copy&quot;
* Durchführen von Rollout-Aktionen.

## Öffnen der Live Copy-Übersicht {#opening-the-live-copy-overview}

Sie können die Live Copy-Übersicht wie folgt öffnen:

* [über das seitliche Bedienfeld „Verweise“ einer Blueprint-Seite (Sites-Konsole);](#opening-live-copy-overview-references-for-a-blueprint-page)
* [über die Eigenschaften der Blueprint-Seite.](#opening-live-copy-overview-properties-of-a-blueprint-page)

### Verweise auf eine Blueprint-Seite {#references-to-a-blueprint-page}

Die **Übersicht über die Live-Kopie** kann über das Seitenbedienfeld **Verweise** der Konsole **Sites** geöffnet werden:

1. Navigieren Sie in der **Sites-Konsole** [zu Ihrer Blueprint-Seite und wählen Sie diese aus.](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
1. Öffnen Sie die Leiste **[References](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** und wählen Sie **Live Copies**.

   ![Live Copy aus Bezugsleiste](../assets/live-copy-references.png)

   >[!TIP]
   >
   >Sie können Verweise auch zuerst öffnen und dann den Blueprint auswählen.

1. Wählen Sie **Übersicht über die Live-Kopie** aus, um die Übersicht über alle Live-Kopien im Zusammenhang mit dem ausgewählten Entwurf anzuzeigen und zu verwenden.
1. Verwenden Sie **Schließen**, um den Vorgang zu beenden, und kehren Sie zur **Sites-Konsole** zurück.

### Eigenschaften einer Blueprint-Seite {#properties-of-a-blueprint-page}

Die **Live Copy-Übersicht** kann beim Anzeigen der Eigenschaften einer Blueprint-Seite geöffnet werden:

1. Öffnen Sie **Eigenschaften** für die entsprechende Blueprint-Seite.
1. Öffnen Sie die Registerkarte **Blueprint**; die Option **Live Copy-Übersicht** wird in der oberen Symbolleiste angezeigt:

   ![Registerkarte &quot;Blueprint-Eigenschaften&quot;](../assets/live-copy-blueprint-tab.png)

1. Wählen Sie **Übersicht über die Live-Kopie** aus, um die Übersicht über alle Live-Kopien im Zusammenhang mit dem aktuellen Entwurf anzuzeigen und zu verwenden.

1. Verwenden Sie **Schließen**, um den Vorgang zu beenden, und kehren Sie zur **Sites-Konsole** zurück.

## Verwenden der Live Copy-Übersicht {#using-the-live-copy-overview}

Das Fenster **Übersicht über die Live-Kopie** bietet eine Übersicht über den Status der Live-Kopien in Bezug auf die ausgewählte Seite.

![Übersicht über Live Copy](../assets/live-copy-overview.png)

Ein Rollout hängt von den Synchronisierungsaktionen ab, die in der jeweiligen Rollout-Konfiguration definiert sind. Einige Aktionen hängen von Änderungen am Inhalt ab. Es gibt jedoch auch viele Aktionen, die nicht von Inhaltsänderungen abhängig sind, sondern von Ereignissen wie der Aktivierung der Seite abhängig sind. Solche Ereignis ändern den Inhalt nicht, ändern jedoch die internen Eigenschaften im Zusammenhang mit dem Inhalt.

Die Statusfelder hängen auch von den Synchronisierungsaktionen ab, die in der jeweiligen Rollout-Konfiguration definiert sind, und geben an, ob diese Aktionen seit der letzten erfolgreichen Einführung entweder im Entwurf oder in der Live Copy durchgeführt wurden. Ein Statusfeld spiegelt nur die Aktionen in der jeweiligen Rollout-Konfiguration wider. Wenn bei einer Live Copy kein erfolgreicher Rollout durchgeführt wurde, wird der Status immer auf dem neuesten Stand angezeigt.

Eine Rollout-Konfiguration wird beispielsweise als `targetActivate` definiert. Eine Einführung hängt daher ausschließlich von den Ereignissen der Aktivierung ab. Das Statusfeld gibt nur an, ob seit der letzten erfolgreichen Einführung Ereignis in der Aktivierung aufgetreten sind.

Die **Übersicht über die Live-Kopie** kann auch zum Durchführen von Aktionen für die Live-Kopie verwendet werden:

1. Öffnen Sie die **Live Copy-Übersicht**.
1. Wählen Sie die gewünschte Blueprint- oder Live Copy-Seite aus und die Symbolleiste wird aktualisiert, um die verfügbaren Aktionen anzuzeigen. Die verfügbaren [Aktionen](overview.md#terms-used) hängen davon ab, ob Sie eine [Blueprint](#actions-for-a-blueprint-page)- oder [Live Copy](#actions-for-a-live-copy-page)-Seite auswählen.

### Aktionen für Blueprint-Seiten {#actions-for-a-blueprint-page}

Bei Auswahl einer Blueprint-Seite sind die folgenden Aktionen verfügbar:

![Live Copy-Übersichtsaktionen für einen Entwurf](../assets/live-copy-overview-actions-blueprint.png)

* **Bearbeiten** : Öffnen Sie die Seite &quot;Entwurf&quot;zur Bearbeitung.
* **[Rollout](overview.md#rollout-and-synchronize)** : Führen Sie einen Rollout durch, um Änderungen von der Quelle an die Live Copy zu übertragen.

### Aktionen für eine Live Copy-Seite {#actions-for-a-live-copy-page}

Wenn Sie eine Live Copy-Seite auswählen, stehen die folgenden Aktionen zur Verfügung:

![Übersichtsaktionen für Live Copy für eine Live Copy](../assets/live-copy-overview-actions.png)

* **Bearbeiten** : Öffnen Sie die Seite &quot;Live Copy&quot;zur Bearbeitung.
* **[Beziehungsstatus](#relationship-status)**  - Informationen zur Ansicht über den Status und die Vererbung.
* **[Synchronisieren](overview.md#rollout-and-synchronize)**  - Synchronisieren Sie eine Live Copy, um Änderungen von der Quelle an die Live Copy zu ziehen.
* **[Zurücksetzen](creating-live-copies.md#resetting-a-live-copy-page)**  - Zurücksetzen einer Live Copy-Seite, um alle Vererbungsabbrüche zu entfernen und die Seite wieder in den gleichen Status wie die Quellseite zurückzusetzen.
* **[Aussetzen](overview.md#suspending-and-cancelling-inheritance-and-synchronization)**  - Deaktiviert vorübergehend die Live-Beziehung zwischen einer Live Copy und ihrer Blueprint-Seite.
* **[Wiederaufnehmen](creating-live-copies.md#resuming-inheritance-for-a-page)**  - Mit der Wiederaufnahme können Sie eine ausgesetzte Beziehung wiederherstellen.
* **[Abtrennen](overview.md#detaching-a-live-copy)** : Entfernt die Live-Beziehung zwischen einer Live Copy und der zugehörigen Blueprint-Seite dauerhaft.

## Beziehungsstatus {#relationship-status}

Die Konsole **Beziehungsstatus** verfügt über zwei Registerkarten mit verschiedenen Funktionen.

* [Beziehungsstatus](#relationship-status-tab)
* [Live Copy ](#live-copy-tab)

### Beziehungsstatus {#relationship-status-tab}

Diese Registerkarte enthält detaillierte Informationen zum Status der Beziehung zwischen dem Entwurf und der Live Copy.

![Registerkarte &quot;Beziehungsstatus&quot;](../assets/live-copy-relationship-status.png)

### Live Copy   {#live-copy-tab}

Auf dieser Registerkarte können Sie die Live Copy-Konfiguration Ansicht und bearbeiten.

![Registerkarte &quot;Live kopieren&quot;](../assets/live-copy-relationship-status-live-copy.png)
