---
title: Installieren und Konfigurieren von Playern in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie Sie Player in Screens as a Cloud Service installieren und konfigurieren.
source-git-commit: 1fc06f987bb40d940bbec9c37e6d58c2c1ca9266
workflow-type: tm+mt
source-wordcount: '555'
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

Der Player meldet verschiedene Wiedergabemetriken mit jeweils `ping` , die standardmäßig 30 Sekunden betragen. Basierend auf den Metriken können Sie verschiedene Edge-Fälle erkennen, wie z. B. festes Erlebnis, leerer Bildschirm und Planungsprobleme. Dadurch können Sie Probleme auf dem Gerät verstehen und beheben und so Untersuchungen und Korrekturmaßnahmen beschleunigen.

Die grundlegende Wiedergabe-Überwachung in einem AEM Screens-Player ermöglicht Ihnen Folgendes:

* Remote-Überwachung der ordnungsgemäßen Wiedergabe von Inhalten durch einen Player

* Verbessern der Reaktionsrate auf leere Bildschirme oder fehlerhafte Erlebnisse im Feld

* Geringeres Risiko, dem Endbenutzer ein defektes Erlebnis anzuzeigen

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

* Da der Player seinen eigenen Wiedergabestatus an den Server meldet, benötigt er eine aktive Verbindung.

* Die `isContentRendering`-Eigenschaft, die prüft, ob die GPU derzeit ressourcenintensiv ist, um standardmäßig aktiviert zu werden, und erfordert eine explizite Anmeldung über die Player-Voreinstellungen. Es wird empfohlen, es nicht zusammen mit Videos zu verwenden.

* Wird für Sequenzkanäle unterstützt.

## Wie geht es weiter {#whats-next}

Nachdem Sie den Player im Cloud -Modus installiert und konfiguriert haben, sollten Sie Screens als Cloud Service-Journey weiterführen, indem Sie das Dokument [Registrieren von Playern in Screens als Cloud Service](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) vom Screens-Dienstanbieter lesen.