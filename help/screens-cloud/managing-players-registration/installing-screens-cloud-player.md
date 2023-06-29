---
title: Installieren und Konfigurieren von Playern in Screens as a Cloud Service
description: Auf dieser Seite wird beschrieben, wie man Player in Screens as a Cloud Service installiert und konfiguriert.
exl-id: a022738a-c543-4629-a244-f70fa294fe7f
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '582'
ht-degree: 52%

---

# Installieren und Konfigurieren von Playern in Screens as a Cloud Service {#installing-players-screens-cloud}

In diesem Abschnitt wird beschrieben, wie man AEM Screens-Player, die für AEM -On-Premise-Intsanzen registriert sind, installiert. Außerdem müssen Sie den vorhandenen Player werkseitig zurücksetzen und dann den neuen Player für AEM Screens as a Cloud Service registrieren.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie den Player einrichten, bevor Sie die Player registrieren. Nach dem Lesen sollten Sie Folgendes verstehen können:

* won wo aus die Player von installiert werden
* wie man den Player zum Cloud-Modus aktualisert

## Schritte zum Festlegen des Players auf den Cloud-Modus {#cloud-mode-setup}

Nachdem Sie den neuesten Player von heruntergeladen haben [AEM Screens Player-Downloads](https://download.macromedia.com/screens/), können Sie Ihren Player jetzt auf den Cloud-Modus aktualisieren.

Gehen Sie wie folgt vor, um den Player zu aktualisieren:

1. Öffnen Sie den AEM Screens-Player.

   >[!NOTE]
   >Sie können mit speziellen Hardwaregeräten oder mit einer Web-Erweiterung auf Ihrem eigenen Player testen.

1. Klicken Sie auf **Konfiguration** Registerkarte und klicken Sie auf **Nach Factory** Schaltfläche unter **Zurücksetzen** -Option.

   ![Bild](/help/screens-cloud/assets/player/installplayer-2.png)

1. Klicken **Bestätigen** , um den Player zurückzusetzen.

1. Erneut aus dem **Konfiguration** Registerkarte und klicken Sie auf **Wechsel zum Cloud-Modus** Schaltfläche unter **Runmode umschalten** -Option.

   ![Bild](/help/screens-cloud/assets/player/installplayer-1.png)

1. Klicken **Bestätigen** wird beim Wechseln in den Cloud-Modus aufgefordert, die Registrierung des Players aufzuheben.

## Einfache Wiedergabe-Überwachung {#playback-monitoring}

Mit jedem `ping` (standardmäßig alle 30 Sekunden) meldet der Player verschiedene Wiedergabemetriken. Basierend auf diesen Metriken kann Adobe verschiedene Edge-Fälle erkennen, z. B. hängende Erlebnisse, leere Bildschirme und Planungsprobleme. Diese Erkennung ermöglicht es uns, Probleme auf dem Gerät zu verstehen und zu beheben, und beschleunigt daher die Durchführung von Untersuchungen und Korrekturmaßnahmen mit Ihnen.

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
| activeElements {Zeichenfolge} | Kommagetrennte Zeichenfolge, derzeit sichtbare Elemente in allen wiedergegebenen Sequenzkanälen (mehrere, wenn ein Mehrzonen-Layout vorhanden war) |
| isDefaultContent {Boolesch} | „true“, wenn der Wiedergabekanal als Standard- oder Fallback-Kanal betrachtet wird (d. h. hat Priorität 1 und keinen Zeitplan) |
| hasContentChanged {Boolesch} | „true“, wenn der Inhalt in den letzten 5 Minuten geändert wurde, andernfalls „false“ |
| lastContentChange {Zeichenfolge} | Zeitstempel der letzten Inhaltsänderung |

>[!NOTE]
>Optional können Sie in den Player-Voreinstellungen (Wiedergabe-Überwachung aktivieren) eine erweiterte Eigenschaft aktivieren:
>|Eigenschaft|Beschreibung|
>|---|---|
>|isContentRendering {Boolesch}|„true“, wenn die GPU bestätigen kann, dass tatsächliche Inhalte wiedergegeben werden (basierend auf der Pixelanalyse)|

### Beschränkungen {#limitations}

Im Folgenden finden Sie einige Beschränkungen bei der einfachen Wiedergabeüberwachung:

* Der Player meldet dem Server seinen eigenen Wiedergabestatus, sodass eine aktive Verbindung erforderlich ist.

* Die `isContentRendering` -Eigenschaft, die prüft, ob die GPU übermäßig ressourcenintensiv ist, um standardmäßig aktiviert zu werden, und eine explizite Anmeldung über die Player-Voreinstellungen erfordert. Es wird empfohlen, es nicht mit Videos in der Produktion zu verwenden.

* Diese Funktion wird nur für Sequenzkanäle unterstützt und deckt noch nicht den Anwendungsfall für interaktive Kanäle (SPA) ab.

* Die Metriken sind noch nicht vollständig für Kunden verfügbar. Adobe arbeitet in Kürze an der Aktivierung eines Dashboard-ähnlichen Berichts- und Warnmechanismus.

## Wie geht es weiter {#whats-next}

Nachdem Sie den Player im Cloud -Modus installiert und konfiguriert haben, fahren Sie mit dem as a Cloud Service Journey zu Screens fort. Siehe [Registrieren von Playern in Screens as a Cloud Service](/help/screens-cloud/managing-players-registration/registering-players-screens-cloud.md) von Screens Services Provider.
