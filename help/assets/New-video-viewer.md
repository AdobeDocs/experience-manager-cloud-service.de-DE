---
title: Neuer Video-Viewer
description: Der neue Video-Viewer in Dynamic Media bietet ein verbessertes Videowiedergabeerlebnis
role: User
exl-id: null
source-git-commit: 8899fff02409d8bfd021e0043c6d1c74eb62ad3f
workflow-type: tm+mt
source-wordcount: '1443'
ht-degree: 2%

---


# Neuer Video-Viewer in Dynamic Media {#new-video-viewer-dynamic-media}

Der neue Video-Viewer für Dynamic Media bietet ein modernisiertes Videowiedergabeerlebnis in Adobe Experience Manager (AEM). Sie bietet ein konsistentes und erweiterbares Anwendererlebnis für Authoring-, Vorschau- und Sites-Umgebungen, während sie weiterhin mit vorhandenen Dynamic Media-Workflows arbeitet.

Bestehende Video-Viewer in Dynamic Media unterstützen die wichtigsten Anforderungen an die Wiedergabe, bieten jedoch eine begrenzte Erweiterbarkeit und Integration auf Ereignisebene für moderne Analyse- und Integrationsszenarien

Der neue Video-Viewer behebt diese Einschränkungen, indem er:

* Bereitstellen eines konsistenteren Wiedergabeerlebnisses
* Explizite Viewer-Auswahl zulassen
* Ausgeben von strukturierten Wiedergabeereignissen für die programmgesteuerte Nutzung
* Unterstützung der Integration mit externen Analysen und externen Systemen

Der Viewer ist als zusätzliche Option verfügbar und erfordert, sofern unterstützt, eine explizite Auswahl. Vorhandene Video-Viewer werden nicht automatisch ersetzt.

Der neue Video Viewer ist für Unternehmen gedacht, die ein verbessertes und erweiterbares Videoerlebnis benötigen, ohne bestehende Implementierungen zu unterbrechen.

> **HINWEIS**
>
> Der neue Video-Viewer ist eine Funktion mit begrenzter Verfügbarkeit. Sie können es aktivieren, indem Sie ein „Support[Ticket“ &#x200B;](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).


## Funktionsweise des neuen Video-Viewers {#how-it-works}

Der neue Video-Viewer funktioniert wie folgt:

1. Ein Video-Asset wird in einen Ordner aufgenommen, der mit Dynamic Media synchronisiert wird.
2. Das Video kann auf der Seite mit Asset-Details mit „Video (**)“ in der Vorschau angezeigt werden**.
3. Der neue Video-Viewer kann bei der Erstellung von Sites **Seiten in der Komponente** Dynamic Media“ ausgewählt werden.
4. Während der Wiedergabe gibt der Viewer strukturierte Ereignisse an das übergeordnete Fenster aus.
5. Zur Steuerung des Wiedergabeverhaltens können optionale Viewer-Modifikatoren verwendet werden.

## Die wichtigsten Unterschiede zum vorhandenen Video-Viewer {#key-differences}

| Bereich | Beschreibung |
|------|-------------|
| Verfügbarkeit des Viewers | Wird als neue Option mit dem Namen **Video (neu) angezeigt** |
| Viewer-Auswahl | Muss explizit ausgewählt sein |
| Erweiterbarkeit | Gibt strukturierte Wiedergabeereignisse aus |
| Integration | Arbeitet weiterhin mit vorhandenen Dynamic Media-Workflows |

## Voraussetzungen {#prerequisites}

Stellen Sie vor der Verwendung des neuen Video-Viewers sicher, dass die folgenden Voraussetzungen erfüllt sind:

| Anforderung | Beschreibung |
|------------|-------------|
| Synchronisierung von Dynamic Media | Der Asset-Ordner muss mit Dynamic Media synchronisiert werden. |
| Videoprofil | Ein Videoprofil muss auf den Ordner angewendet werden. |
| Video-Asset | Ein Video muss in den Ordner aufgenommen werden. |

Der neue Video-Viewer ist ab der **AEM as a Cloud Service-Version 2025.7.0** verfügbar.

Wenden Sie sich an die Adobe-Kundenunterstützung, um den neuen Video-Viewer zu aktivieren oder zu deaktivieren.

## Vorschau des neuen Video-Viewers {#preview}

Führen Sie die folgenden Schritte aus, um den neuen Video-Viewer auf der Seite mit den Asset-Details in der Vorschau anzuzeigen:

1. Navigieren Sie zu **Assets** > **Dateien** und öffnen Sie den Ordner, der das Video-Asset enthält.
2. Klicken Sie auf das Video-Asset, um die Seite mit den Asset-Details zu öffnen.
3. Klicken Sie im linken Bedienfeld auf **Viewer**.
4. Wählen Sie im **Viewer**-Bedienfeld **Video (neu)** aus.
5. Klicken Sie auf **URL**, um den Vorschau-Link zu kopieren.
   ![URL kopieren](assets/Copy-url1.jpg)

## Verwenden des neuen Video-Viewers in Sites {#use-in-sites}

Der neue Video-Viewer ist über die vorhandene Komponente **Dynamic Media** in AEM Sites verfügbar.

### Hinzufügen der Dynamic Media-Komponente

Führen Sie die folgenden Schritte aus, um ein Video mithilfe der Dynamic Media-Komponente hinzuzufügen:

1. Öffnen Sie die Seite im **Sites-Editor**.
2. Ziehen Sie **Komponente** Dynamic Media) an die gewünschte Position auf der Seite.
3. Wählen Sie die **Dynamic Media** auf der Seite aus.
4. Klicken Sie auf die Komponente, um den Asset-Wähler zu öffnen.
5. Wählen Sie ein Video-Asset.

![Ziehen Sie die Dynamic Media-Komponente](assets/drag-component.jpeg)

### Viewer konfigurieren

Führen Sie die folgenden Schritte aus, um die Viewer-Vorgabe zu konfigurieren:

1. Wählen Sie die **Dynamic Media** auf der Seite aus.
2. Klicken Sie **der Komponenten**&#x200B;Symbolleiste auf „Konfigurieren“.
   ![Dynamic Media-Einstellungen öffnen](assets/configure-asset.png)

3. Wählen Sie **Dialogfeld „Einstellungen für Dynamic**&quot; **Video (neu)** aus der Dropdown-Liste **Viewer**&#x200B;Vorgabe .
   ![Viewer-Vorgabe „Video auswählen (neu)“](assets/viewer-preset.jpeg)

4. Geben Sie alle erforderlichen Modifikatoren in das Feld **Viewer** ein (z. B. `autoplay=true&muted=true`).
   ![Viewer-Modifikatoren](assets/additional-modifiers.jpeg)

5. Speichern Sie die Änderungen.

Das Video wird mit dem neuen Video-Viewer auf der Seite geladen.

> **Hinweis:** Der neue Video-Viewer ersetzt vorhandene Videos nicht automatisch. Benutzende müssen bei Verwendung **Dynamic Media-Komponente manuell** Video (neu **in der Viewer-Vorgabe** auswählen oder die direkten URLs aktualisieren, damit sie bei Bedarf auf den neuen Video-Viewer verweisen.

### Migrieren von Videos mithilfe direkter URLs

Wenn der Zugriff auf Ihre Videos über direkte URLs anstelle der Dynamic Media-Komponente erfolgt, können Sie durch Aktualisieren der URL zum neuen Video-Viewer wechseln. Zum Beispiel: `https://s7d1.scene7.com/dmviewers/html5/VideoViewer.html?asset=<video-asset>`

## Viewer-Modifikatoren {#viewer-modifiers}

Mit Viewer-Modifikatoren können Sie das Laden von Assets, das Wiedergabeverhalten, die Auswahl von Streaming-Formaten und die Viewer-Darstellung steuern.

| Modifikator | Beschreibung |
|--------|-------------|
| `asset` | Gibt die Asset-ID des Videos oder adaptiven Videosets an. |
| `posterimage` | Legt das Bild fest, das angezeigt wird, bevor die Wiedergabe beginnt. |
| `serverurl` | Gibt den Stammverzeichnis der Bildbereitstellung an. |
| `contenturl` | Gibt den Pfad des Inhaltsstamms an. |
| `videoserverurl` | Gibt den Stammverzeichnis des Videoservers an. |
| `sources.dash` | Gibt die DASH-Manifest-URL für die Wiedergabe an. |
| `sources.hls` | Gibt die HLS-Manifest-URL für die Wiedergabe an. |
| `autoplay=true` | Startet die Wiedergabe automatisch beim Laden des Videos. |
| `controls=true/false` | Blendet die Steuerelemente für die Videowiedergabe ein oder aus. |
| `loop=true` | Startet die Wiedergabe automatisch nach Videoende. |
| `muted=true` | Startet die Wiedergabe im stummgeschalteten Zustand |
| `playbackrates` | Legt die verfügbaren Optionen für die Wiedergabegeschwindigkeit fest. |
| `playback` | Gibt das Streaming-Format an (automatisch, HLS, Bindestrich oder progressiv). |
| `progressivebitrate` | Legt die Bitrate für die progressive Wiedergabe fest. |
| `initialbitrate` | Gibt die anfängliche Bitrate für adaptives Streaming an. |
| `isletterboxed=true/false` | Steuert, ob das Video im Briefkasten abgelegt oder gestreckt ist. |
| `customcss` | Gibt eine benutzerdefinierte CSS-Datei für den Viewer-Stil an. |
| `transition` | Gibt das Ein- oder Ausblenden des Übergangsverhaltens für Viewer-Steuerelemente an. |

Modifikatoren werden als Abfrageparameter im Feld **Viewer-Modifikatoren** angegeben.

## Unterstützte Ereignisse {#supported-events}

Der neue Video-Viewer gibt während der Wiedergabe die folgenden Ereignisse aus:

| Ereignistyp | Beschreibung |
|-----------|-------------|
| abspielen | Video startet die Wiedergabe |
| Pause | Video wurde angehalten |
| suchen | Der Benutzer sucht im Video |
| laden | Video wird geladen |
| Schließen | Player is closed |
| Metadaten | Metadaten wie Dauer |
| Meilenstein | Wiedergabe-Meilenstein erreicht |
| current_time | Position der periodischen Wiedergabe |
| Vollbild | Zum Vollbildmodus wechseln |
| un_fullscreen | Vollbildmodus beenden |

## Umgang mit Ereignissen im übergeordneten Fenster {#handling-events}

Der neue Video-Viewer sendet während Videointeraktionen wiedergabebezogene Nachrichten an die übergeordnete Seite.

Um diese Ereignisse zu verarbeiten, muss die übergeordnete Anwendung auf Browser-Nachrichtenereignisse warten und den Nachrichtenursprung validieren, bevor die Daten verarbeitet werden.

Die Ereignis-Payload enthält Informationen wie den Ereignistyp, den Wiedergabestatus, die aktuelle Wiedergabedauer und zusätzliche Metadaten. Diese Ereignisse können zur Unterstützung von Analytics-Tracking, benutzerdefinierten Interaktionen oder der Integration mit externen Systemen verwendet werden

Adobe empfiehlt, den Nachrichtenursprung zu validieren, um sicherzustellen, dass Ereignisse nur von vertrauenswürdigen Dynamic Media-Domains verarbeitet werden.

## Bericht zu Videointeraktionen für den neuen Video-Viewer {#video-engagement-report}

Der Bericht zu Videointeraktionen enthält Analysemetriken für Videos, die mit dem neuen Video-Viewer in Dynamic Media wiedergegeben werden. Der Bericht liefert aggregierte Leistungsdaten für den angegebenen Monat und unterstützt die monatliche Berichterstellung.

Berichte werden auf Anfrage generiert. Um einen Bericht anzufordern, erstellen Sie ein [Support-Ticket](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) und geben Sie die folgenden Details an:

* Berichtsmonat - Geben Sie den Monat an, für den der Bericht erforderlich ist (z. B. Januar 2026).
* Versand-E-Mail-Adresse : E-Mail-Adresse der Gruppe (empfohlen) oder Person, die den Bericht sendet

Der Bericht enthält Metriken zur Interaktion pro Video, einschließlich Ansichten, Impressionen, Beobachtungszeit, Abschlussrate und Interaktionswert.

### Berichtsformat

* Berichte werden im CSV-Format bereitgestellt.
* Jede Zeile stellt ein einzelnes Video dar.
* Metriken werden für den ausgewählten Berichtszeitraum aggregiert.
* Gelöschte Assets werden aus dem Bericht ausgeschlossen.
* Unterstützt das Filtern nach `tenant_name`.

### Berichtsfelder

Der Videointeraktionsbericht enthält die folgenden Felder:

| Feld | Beschreibung | Berechnung |
|-------|------------|-------------|
| `video_id` | Eindeutige Videokennung. | nicht vorhanden |
| `video_name` | Name des Video-Assets. | nicht vorhanden |
| `video_created_date` | Erstellungsdatum des Videos. | nicht vorhanden |
| `duration_in_seconds` | Dauer des Videos in Sekunden. | nicht vorhanden |
| `video_views` | Gesamtzahl der Videowiedergabeereignisse im ausgewählten Berichtszeitraum. | nicht vorhanden |
| `video_impressions` | Gesamtzahl der Ladevorgänge des Videos. | nicht vorhanden |
| `video_watched_seconds` | Gesamtzahl der Sekunden, die über alle Wiedergabeereignisse hinweg beobachtet wurden. | Summe der Sekunden, die über alle Wiedergabeereignisse hinweg beobachtet wurden |
| `play_rate` | Prozentsatz der Videowiedergaben im Verhältnis zur Videolast. | (`video_views` ÷ `video_impressions`) × 100 |
| `avg_time_watched_in_seconds` | Durchschnittlich Sekunden pro Ansicht angesehen. | `video_watched_seconds` ÷ `video_views` |
| `avg_completion_rate` | Prozentsatz der Ansichten, die den vollständigen Videoabschluss erreicht haben. | (Vollständige Ansichten ÷ `video_views`) × 100 |
| `engagement_score` | Durchschnittlicher Prozentsatz der Uhr für alle Wiedergabeereignisse. | (Gesamter Prozentsatz der angezeigten Video-Zeitleiste für alle Sitzungen ÷ `video_views`) |
| `tenant_name` | Kennung des Unternehmens oder Mandanten, das mit den Daten verknüpft ist. | nicht vorhanden |

## Häufig gestellte Fragen {#faq-video-engagement}

+++Wenn für ein Video die automatische Wiedergabe festgelegt ist, wird es automatisch als Ansicht gezählt, oder erst, nachdem der Benutzer es für eine Mindestdauer angesehen hat?

Die automatische Wiedergabe wird als Videoansicht gezählt. Die automatisch initiierte Wiedergabe wird als Ansicht aufgezeichnet.

+++

+++Wenn ein(e) Benutzende(r) nur einen Teil eines Videos ansieht (z. B. die ersten 2 Sekunden und die letzten 2 Sekunden eines 10-Sekunden-Videos), wird es dann als abgeschlossene Ansicht gezählt?

Eine Ansicht wird als abgeschlossen gezählt, wenn die Wiedergabe das Ende der Video-Zeitleiste erreicht, auch wenn Teile des Videos übersprungen wurden.

+++

+++Wenn ein(e) Benutzende(r) das Video rückwärts scrollt und Teile des Videos erneut ansieht, erhöht dies dann die Anzahl der Video-Aufrufe, den Engagement-Score oder beides?

Beim erneuten Ansehen von Teilen des Videos wird die Anzahl der Videoansichten nicht erhöht. Zusätzliche Wiedergabe trägt zum Engagement_Score bei.

+++

+++Wenn derselbe Benutzer dasselbe Video mehrmals ansieht, ohne die Seite neu zu laden, wie werden dann video_views und interaction_score berechnet?

Durch wiederholte Wiedergabe ohne Neuladen der Seite wird die Anzahl der Videoansichten nicht erhöht. Zusätzliche Wiedergabe trägt zum Engagement_Score bei.

+++

+++Wirkt sich das Anhalten und Fortsetzen eines Videos auf die Interaktionsverfolgung oder die Berechnung der Abschlussrate aus?

Das Anhalten und Fortsetzen der Wiedergabe hat keine Auswirkungen auf das Interaktions-Tracking oder die Berechnung der Abschlussrate.

+++
