---
title: Konsole „Live Copy-Übersicht“
description: Erfahren Sie mehr über die Grundlagen der Konsole "Live Copy-Übersicht", um den Status Ihrer Live Copies schnell zu verstehen und Inhalte zu synchronisieren.
feature: Multi-Site-Manager
role: Administrator
exl-id: 3ef7fbce-10a1-4b21-8486-d3c3706e537c
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '738'
ht-degree: 23%

---

# Konsole „Live Copy-Übersicht“{#live-copy-overview-console}

Die Konsole **Live Copy-Übersicht** ermöglicht Ihnen Folgendes:

* Anzeigen/Verwalten der Vererbung einer Site.
   * Zeigen Sie die Blueprint-Struktur und die entsprechende Live Copy-Struktur mit ihrem Vererbungsstatus an
   * Ändern des Vererbungsstatus, z. B. Aussetzen und Fortsetzen
   * Anzeigen von Blueprint- und Live Copy-Eigenschaften
* Durchführen von Rollout-Aktionen.

## Öffnen der Live Copy-Übersicht {#opening-the-live-copy-overview}

Sie können die Live Copy-Übersicht wie folgt öffnen:

* [über das seitliche Bedienfeld „Verweise“ einer Blueprint-Seite (Sites-Konsole);](#opening-live-copy-overview-references-for-a-blueprint-page)
* [über die Eigenschaften der Blueprint-Seite.](#opening-live-copy-overview-properties-of-a-blueprint-page)

### Verweise auf eine Blueprint-Seite {#references-to-a-blueprint-page}

Die **Live Copy-Übersicht** kann über das seitliche Bedienfeld **Verweise** der Konsole **Sites** geöffnet werden:

1. Navigieren Sie in der **Sites-Konsole** [zu Ihrer Blueprint-Seite und wählen Sie diese aus.](/help/sites-cloud/authoring/getting-started/basic-handling.md#viewing-and-selecting-resources)
1. Öffnen Sie die Leiste **[Verweise](/help/sites-cloud/authoring/getting-started/basic-handling.md#references)** und wählen Sie **Live Copies** aus.

   ![Live Copy aus der Verweisleiste](../assets/live-copy-references.png)

   >[!TIP]
   >
   >Sie können auch Verweise zuerst öffnen und dann den Blueprint auswählen.

1. Wählen Sie **Live Copy-Übersicht** aus, um die Übersicht aller Live Copies im Zusammenhang mit dem ausgewählten Blueprint anzuzeigen und zu verwenden.
1. Verwenden Sie **Schließen**, um den Vorgang zu beenden, und kehren Sie zur **Sites-Konsole** zurück.

### Eigenschaften einer Blueprint-Seite {#properties-of-a-blueprint-page}

Die **Live Copy-Übersicht** kann beim Anzeigen der Eigenschaften einer Blueprint-Seite geöffnet werden:

1. Öffnen Sie **Eigenschaften** für die entsprechende Blueprint-Seite.
1. Öffnen Sie die Registerkarte **Blueprint**; die Option **Live Copy-Übersicht** wird in der oberen Symbolleiste angezeigt:

   ![Registerkarte &quot;Blueprint-Eigenschaften&quot;](../assets/live-copy-blueprint-tab.png)

1. Wählen Sie **Live Copy-Übersicht** aus, um die Übersicht aller Live Copies im Zusammenhang mit dem aktuellen Blueprint anzuzeigen und zu verwenden.

1. Verwenden Sie **Schließen**, um den Vorgang zu beenden, und kehren Sie zur **Sites-Konsole** zurück.

## Verwenden der Live Copy-Übersicht {#using-the-live-copy-overview}

Das Fenster **Live Copy-Übersicht** bietet eine Übersicht über den Status der Live Copies, die mit der ausgewählten Seite in Verbindung stehen.

![Fenster &quot;Live Copy-Übersicht&quot;](../assets/live-copy-overview.png)

Ein Rollout hängt von den Synchronisierungsaktionen ab, die in der jeweiligen Rollout-Konfiguration definiert sind. Einige Aktionen hängen von Änderungen am Inhalt ab. Es gibt jedoch auch viele Aktionen, die nicht von Änderungen am Inhalt abhängig sind, aber von Ereignissen wie der Seitenaktivierung abhängig sind. Solche Ereignisse ändern den Inhalt nicht, ändern jedoch die internen Eigenschaften im Zusammenhang mit dem Inhalt.

Die Statusfelder hängen auch von den Synchronisierungsaktionen ab, die in der jeweiligen Rollout-Konfiguration definiert sind, und geben an, ob es seit dem letzten erfolgreichen Rollout Aktionen dieser Art für den Blueprint oder die Live Copy gab. Ein Statusfeld spiegelt nur die Aktionen in der jeweiligen Rollout-Konfiguration wider. Wenn für eine Live Copy kein erfolgreicher Rollout durchgeführt wurde, wird der Status immer aktuell angezeigt.

Beispielsweise wird eine Rollout-Konfiguration als `targetActivate` definiert. Daher hängt ein Rollout ausschließlich von Aktivierungsereignissen ab. Das Statusfeld gibt nur an, ob seit dem letzten erfolgreichen Rollout Aktivierungsereignisse aufgetreten sind.

Die **Live Copy-Übersicht** kann auch verwendet werden, um Aktionen für die Live Copy durchzuführen:

1. Öffnen Sie die **Live Copy-Übersicht**.
1. Wählen Sie die gewünschte Blueprint- oder Live Copy-Seite aus. Die Symbolleiste wird aktualisiert, um die verfügbaren Aktionen anzuzeigen. Die verfügbaren [Aktionen](overview.md#terms-used) hängen davon ab, ob Sie eine [Blueprint](#actions-for-a-blueprint-page)- oder [Live Copy](#actions-for-a-live-copy-page)-Seite auswählen.

### Aktionen für Blueprint-Seiten {#actions-for-a-blueprint-page}

Bei Auswahl einer Blueprint-Seite sind die folgenden Aktionen verfügbar:

![Übersichtsaktionen für Live Copy für einen Blueprint](../assets/live-copy-overview-actions-blueprint.png)

* **Bearbeiten**  - Öffnen Sie die Blueprint-Seite zur Bearbeitung.
* **[Rollout](overview.md#rollout-and-synchronize)**  - Führen Sie einen Rollout durch, um Änderungen von der Quelle an die Live Copy zu übertragen.

### Aktionen für eine Live Copy-Seite {#actions-for-a-live-copy-page}

Wenn Sie eine Live Copy-Seite auswählen, sind die folgenden Aktionen verfügbar:

![Übersichtsaktionen für Live Copy für Live Copy](../assets/live-copy-overview-actions.png)

* **Bearbeiten**  - Öffnen Sie die Live Copy-Seite zur Bearbeitung.
* **[Beziehungsstatus](#relationship-status)**  - Zeigt Informationen zum Status und zur Vererbung an.
* **[Synchronisieren](overview.md#rollout-and-synchronize)**  - Synchronisieren Sie eine Live Copy, um Änderungen von der Quelle an die Live Copy zu ziehen.
* **[Zurücksetzen](creating-live-copies.md#resetting-a-live-copy-page)**  - Setzen Sie eine Live Copy-Seite zurück, um alle Vererbungsabbrüche zu entfernen und die Seite wieder in denselben Status wie die Quellseite zu versetzen.
* **[Aussetzen](overview.md#suspending-and-cancelling-inheritance-and-synchronization)**  - Deaktiviert vorübergehend die Live-Beziehung zwischen einer Live Copy und ihrer Blueprint-Seite.
* **[Wiederaufnehmen](creating-live-copies.md#resuming-inheritance-for-a-page)**  - Mit der Wiederaufnahme können Sie eine ausgesetzte Beziehung reaktivieren.
* **[Trennen](overview.md#detaching-a-live-copy)**  - Entfernt dauerhaft die Live-Beziehung zwischen einer Live Copy und ihrer Blueprint-Seite.

## Beziehungsstatus {#relationship-status}

Die Konsole **Beziehungsstatus** verfügt über zwei Registerkarten mit verschiedenen Funktionen.

* [Beziehungsstatus](#relationship-status-tab)
* [Live Copy ](#live-copy-tab)

### Beziehungsstatus {#relationship-status-tab}

Dieser Tab enthält detaillierte Informationen zum Status der Beziehung zwischen dem Blueprint und der Live Copy.

![Registerkarte &quot;Beziehungsstatus&quot;](../assets/live-copy-relationship-status.png)

### Live Copy   {#live-copy-tab}

Auf dieser Registerkarte können Sie die Live Copy-Konfiguration anzeigen und bearbeiten.

![Registerkarte &quot;Live Copy&quot;](../assets/live-copy-relationship-status-live-copy.png)
