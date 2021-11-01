---
title: Installieren und Konfigurieren von Playern in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie man Player in Screens as a Cloud Service installiert und konfiguriert.
exl-id: a022738a-c543-4629-a244-f70fa294fe7f
source-git-commit: 3367977496d3edad0f6f1e27e98eac95c791e870
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 100%

---

# Installieren und Konfigurieren von Playern in Screens as a Cloud Service {#installing-players-screens-cloud}

In diesem Abschnitt wird beschrieben, wie man AEM Screens-Player, die für AEM -On-Premise-Intsanzen registriert sind, installiert. Außerdem müssen Sie den vorhandenen Player auf die Werksteinstellungen zurücksetzen und dann den neuen Player bei AEM Screens as a Cloud Service registrieren.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie den Player einrichten, bevor Sie die Player registrieren. Nach dem Lesen sollten Sie Folgendes verstehen:

* won wo aus die Player von installiert werden
* wie man den Player zum Cloud-Modus aktualisert

## Schritte zum Festlegen des Players auf den Cloud-Modus {#cloud-mode-setup}

Nachdem Sie den neuesten Player von [AEM Screens Player-Downloads](https://download.macromedia.com/screens/) heruntergeladen haben, können Sie Ihren Player jetzt zum Cloud-Modus aktualisieren.

Gehen Sie wie folgt vor, um den Player zu aktualisieren:

1. Öffnen Sie den AEM Screens-Player.

   >[!NOTE]
   >Sie können mit speziellen Hardwaregeräten oder mit einer Web-Erweiterung auf Ihrem eigenen Player testen.

1. Klicken Sie auf die Registerkarte **Konfiguration** und klicken Sie unter der Option **Zurücksetzen** auf die Schaltfläche **Auf Werkseinstellungen**.

   ![image](/help/screens-cloud/assets/player/installplayer-2.png)

1. Klicken Sie auf **Bestätigen**, um Ihren Player zurückzusetzen.

1. Wählen Sie erneut auf der Registerkarte **Konfiguration** die Schaltfläche **Wechsel zum Cloud-Modus** unter der Option **Ausführungsmodus ein/aus**.

   ![image](/help/screens-cloud/assets/player/installplayer-1.png)

1. Ein Klick auf **Bestätigen**, das erscheint, wenn Sie in den Cloud-Modus wechseln, hebt die Registrierung des Players auf.

## Einfache Wiedergabe-Überwachung {#playback-monitoring}

Mit jedem `ping` (standardmäßig alle 30 Sekunden) meldet der Player verschiedene Wiedergabemetriken. Basierend auf diesen Metriken können wir verschiedene Randfälle wie steckengebliebenes Erlebnis, leerer Bildschirm und Terminprobleme erkennen. Auf diese Weise können wir Probleme auf dem Gerät verstehen und beheben und somit gemeinsam mit Ihnen durchgeführte Untersuchungen und Abhilfemaßnahmen beschleunigen.

Eine einfache Wiedergabe-Überwachung in einem AEM Screens-Player ermöglicht Folgendes:

* Fernüberwachung, ob ein Player Inhalte ordnungsgemäß wiedergibt.

* Verbessern der Reaktionsfähigkeit auf leere Bildschirme oder fehlerhafte Erlebnisse im Feld.

* Verringerung des Risikos, dem Endbenutzer ein fehlerhaftes Erlebnis anzuzeigen.

### Grundlegendes zu Eigenschaften {#understand-properties}

Die folgenden Eigenschaften sind in jedem `ping` enthalten:

| Eigenschaft | Beschreibung |
|---|---|
| id {Zeichenfolge} | die Player-Kennung |
| activeChannel {Zeichenfolge} | der derzeit wiedergebende Kanalpfad, oder null, wenn nichts geplant ist |
| activeElements {Zeichenfolge} | Kommagetrennte Zeichenfolge, derzeit sichtbare Elemente in allen wiedergegebenen Sequenzkanälen (mehrere bei einem Mehrzonen-Layout) |
| isDefaultContent {Boolesch} | „true“, wenn der Wiedergabekanal als Standard- oder Fallback-Kanal betrachtet wird (d. h. hat Priorität 1 und keinen Zeitplan) |
| hasContentChanged {Boolesch} | „true“, wenn der Inhalt in den letzten 5 Minuten geändert wurde, andernfalls „false“ |
| lastContentChange {Zeichenfolge} | Zeitstempel der letzten Inhaltsänderung |

>[!NOTE]
>Optional kann eine erweiterte Eigenschaft in den Player-Voreinstellungen (Wiedergabeüberwachung aktivieren) aktiviert werden, und zwar:
>|Eigenschaft|Beschreibung|
>|---|---|
>|isContentRendering {Boolesch}|„true“, wenn die GPU bestätigen kann, dass tatsächliche Inhalte wiedergegeben werden (basierend auf der Pixelanalyse)|

### Beschränkungen {#limitations}

Im Folgenden finden Sie einige Beschränkungen bei der einfachen Wiedergabeüberwachung:

* Der Player meldet dem Server seinen eigenen Wiedergabestatus, sodass eine aktive Verbindung erforderlich ist.

* Die `isContentRendering`-Eigenschaft, die die GPU prüft, ist derzeit zu ressourcenintensiv, als dass sie standardmäßig aktiviert werden könnte, und erfordert eine explizite Anmeldung aus den Player-Voreinstellungen heraus. Es wird empfohlen, sie nicht zusammen mit Videos in der Produktion zu verwenden.

* Diese Funktion wird nur für Sequenzkanäle unterstützt und deckt noch nicht den Anwendungsfall für interaktive Kanäle (SPA) ab.

* Die Metriken sind noch nicht vollständig für unsere Kunden verfügbar. Wir arbeiten intensiv daran, in naher Zukunft einen Dashboard-ähnlichen Reporting- und Warnmechanismus zu ermöglichen.

## Wie geht es weiter {#whats-next}

Nun, da Sie den Player im Cloud-Modus installiert und konfiguriert haben, sollten Sie Ihre Screens as a Cloud Service-Tour weiterführen, indem Sie das Dokument [Registrieren von Playern in Screens as a Cloud Service](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) von Screens Services Provider lesen.
