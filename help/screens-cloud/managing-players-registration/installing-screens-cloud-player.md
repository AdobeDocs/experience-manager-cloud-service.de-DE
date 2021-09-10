---
title: Installieren und Konfigurieren von Playern in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Player in Screens as a Cloud Service installieren und konfigurieren.
exl-id: a022738a-c543-4629-a244-f70fa294fe7f
source-git-commit: 3367977496d3edad0f6f1e27e98eac95c791e870
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 1%

---

# Installieren und Konfigurieren von Playern in Screens as a Cloud Service {#installing-players-screens-cloud}

In diesem Abschnitt wird beschrieben, wie Sie AEM Screens-Player installieren, die für On-Premise-AEM registriert sind. Außerdem müssen Sie den vorhandenen Player werkseitig zurücksetzen und dann den neuen Player bei AEM Screens als Cloud Service registrieren.

## Ziele {#objective}

In diesem Dokument erfahren Sie, wie Sie den Player einrichten, bevor Sie die Player registrieren. Nach dem Lesen sollten Sie Folgendes verstehen können:

* wo die Player von installiert werden
* Aktualisieren des Players in den Cloud-Modus

## Schritte zum Festlegen des Players auf den Cloud-Modus {#cloud-mode-setup}

Nachdem Sie den neuesten Player von [AEM Screens Player-Downloads](https://download.macromedia.com/screens/) heruntergeladen haben, können Sie Ihren Player jetzt auf den Cloud-Modus aktualisieren.

Gehen Sie wie folgt vor, um den Player zu aktualisieren:

1. Öffnen Sie den AEM Screens-Player.

   >[!NOTE]
   >Sie können mit dedizierten Hardwaregeräten oder mit einer Web-Erweiterung auf Ihrem eigenen Player testen.

1. Klicken Sie auf die Registerkarte **Configuration** und klicken Sie unter der Option **Reset** auf die Schaltfläche **To Factory** .

   ![Bild](/help/screens-cloud/assets/player/installplayer-2.png)

1. Klicken Sie auf **Bestätigen** , um Ihren Player zurückzusetzen.

1. Wählen Sie erneut auf der Registerkarte **Konfiguration** die Schaltfläche **Wechsel zum Cloud-Modus** unter der Option **Runmode** ein/aus.

   ![Bild](/help/screens-cloud/assets/player/installplayer-1.png)

1. Klicken Sie auf **Bestätigen Sie**, dass die Registrierung des Players aufgehoben wird, wenn Sie zum Cloud-Modus wechseln.

## Grundlegende Wiedergabe-Überwachung {#playback-monitoring}

Der Player meldet verschiedene Wiedergabemetriken mit jeweils `ping` , die standardmäßig 30 Sekunden betragen. Basierend auf diesen Metriken können wir verschiedene Edge-Fälle wie festes Erlebnis, leerer Bildschirm und Planungsprobleme erkennen. Dadurch können wir Probleme auf dem Gerät verstehen und beheben und so mit Ihnen eine Untersuchung und Korrekturmaßnahmen beschleunigen.

Die grundlegende Wiedergabe-Überwachung in einem AEM Screens-Player ermöglicht Folgendes:

* Remote-Überwachung, ob ein Player Inhalte ordnungsgemäß wiedergibt.

* Verbessern Sie die Reaktionsfähigkeit auf leere Bildschirme oder fehlerhafte Erlebnisse im Feld.

* Verringert das Risiko, dem Endbenutzer ein fehlerhaftes Erlebnis anzuzeigen.

### Eigenschaften {#understand-properties}

Die folgenden Eigenschaften sind in jedem `ping` enthalten:

| Eigenschaft | Beschreibung |
|---|---|
| id {string} | Player-ID |
| activeChannel {string} | derzeit den Kanalpfad wiedergeben, oder null, wenn nichts geplant ist |
| activeElements {string} | Kommagetrennte Zeichenfolge, derzeit sichtbare Elemente in allen wiedergegebenen Sequenzkanälen (mehrere bei einem Mehrzonen-Layout) |
| isDefaultContent {boolean} | &quot;true&quot;, wenn der Wiedergabekanal als Standard- oder Fallback-Kanal betrachtet wird (d. h. hat Priorität 1 und keinen Zeitplan) |
| hasContentChanged {boolean} | true , wenn der Inhalt in den letzten 5 Minuten geändert wurde, andernfalls false |
| lastContentChange {string} | Zeitstempel der letzten Inhaltsänderung |

>[!NOTE]
>Optional kann eine erweiterte Eigenschaft in den Player-Voreinstellungen (Enable Play-back Monitoring) aktiviert werden, und zwar:
>|Eigenschaft|Beschreibung|
>|—|—|
>|isContentRendering {boolean}|true , wenn die GPU bestätigen kann, dass tatsächliche Inhalte wiedergegeben werden (basierend auf der Pixelanalyse)|

### Beschränkungen {#limitations}

Im Folgenden finden Sie einige Einschränkungen bei der grundlegenden Wiedergabe-Überwachung:

* Der Player meldet dem Server seinen eigenen Wiedergabestatus, sodass eine aktive Verbindung erforderlich ist.

* Die `isContentRendering`-Eigenschaft, die die GPU prüft, ist derzeit zu ressourcenintensiv, um standardmäßig aktiviert zu werden, und erfordert eine explizite Anmeldung von den Player-Voreinstellungen. Es wird empfohlen, es nicht zusammen mit Videos in der Produktion zu verwenden.

* Diese Funktion wird nur für Sequenzkanäle unterstützt und deckt noch nicht den Anwendungsfall für interaktive Kanäle (SPA) ab.

* Die Metriken sind noch nicht vollständig für unsere Kunden verfügbar. Wir arbeiten intensiv daran, in naher Zukunft einen dashboard-ähnlichen Berichterstellungs- und Warnmechanismus zu aktivieren.

## Wie geht es weiter {#whats-next}

Nachdem Sie den Player im Cloud -Modus installiert und konfiguriert haben, sollten Sie Screens als Cloud Service-Journey weiterführen, indem Sie das Dokument [Registrieren von Playern in Screens als Cloud Service](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) vom Screens-Dienstanbieter lesen.
