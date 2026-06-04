---
title: Multi-Audio und mehrere Untertitel in Dynamic Media mit OpenAPI-Funktionen Videos
description: Erfahren Sie, wie Sie mit OpenAPI-Funktionen in Adobe Experience Manager Assets mehrere Audiospuren und Untertitel für Video-Assets in Dynamic Media hinzufügen und verwalten können.
role: User
badgeSaas: label="AEM Assets" type="Positive"
source-git-commit: 30037f08d5caeab878b6cf89b936308d16ae3e8d
workflow-type: tm+mt
source-wordcount: '524'
ht-degree: 8%

---


# Multi-Audio und mehrere Untertitel in Dynamic Media mit OpenAPI-Funktionen Videos {#multi-audio-captions-dynamic-media-with-openapi-capabilities}

[!DNL Adobe Experience Manager Assets] Dynamic Media mit OpenAPI-Funktionen können Sie mehrere Audiospuren und Untertiteldateien zu Video-Assets hinzufügen. Diese Funktion verbessert die Barrierefreiheit, unterstützt lokalisierte Wiedergabeerlebnisse und verbessert die Videobereitstellung für globale Zielgruppen.

Diese Funktionen werden direkt über die Registerkarte **Untertitel und Audiospuren** auf der Seite Eigenschaften des Video-Assets verwaltet.

>[!NOTE]
>
>Die Unterstützung von Multi-Audio und Multi-Caption in Dynamic Media mit OpenAPI-Funktionen ist eine Funktion mit begrenzter Verfügbarkeit. Sie können es aktivieren, indem Sie ein [Support-Ticket](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html) erstellen.

Alle unterstützten Dynamic Media-Videoformate mit OpenAPI-Funktionen unterstützen mehrere Untertitel und Audiospuren.

## Bevor Sie beginnen {#before-you-begin}

Vergewissern Sie sich über Folgendes:

* Das Video-Asset ist in [!DNL AEM Assets] verfügbar
* Unterstütztes Audioformat: `.mp3`
* Unterstütztes Untertitelformat: `.vtt`

>[!NOTE]
>
>Für Dynamic Media mit OpenAPI-Funktionen ist kein Videoprofil erforderlich. Die **Untertitel und Audiospuren** ist standardmäßig für alle Video-Assets verfügbar.

## Mehrere Audiospuren hinzufügen {#add-audio-tracks}

![Registerkarte „Untertitel und Audiospuren“](/help/assets/assets/caption-audio-tracks1.png)

So fügen Sie einem Video Audiospuren hinzu:

1. Navigieren Sie zum hochgeladenen Video-Asset.
1. Wählen Sie das Asset aus und klicken Sie auf **Eigenschaften**.
1. Öffnen Sie die **Untertitel und Audiospuren**.
1. Klicken Sie **Audiospuren hochladen**.
1. Wählen Sie eine oder mehrere `.mp3` aus.
1. Klicken Sie **Symbol** Zeichnen“ neben dem Dateinamen der Audiospur.

Im Dialogfeld **Audiospur bearbeiten**:

* **Dateiname** - Standarddateiname, der von der hochgeladenen Datei abgeleitet wird.
* **Sprache** - Wählen Sie die Sprache für den Ton aus.
* **Type** - Original-, Standard- oder Audiobeschreibung.
* **Label** - Anzeigename, der in der Audioauswahl des Players angezeigt wird.

![Dialogfeld „Audiospur“](/help/assets/assets/edit-audio1.png)

1. Klicken Sie auf **Speichern**.
1. Wiederholen Sie dies für weitere Audiospuren, falls erforderlich.
1. Klicken Sie auf **Speichern und schließen**.

>[!NOTE]
>
>Jedes Audiospurlabel muss eindeutig sein.

## Mehrere Beschriftungen hinzufügen {#add-captions}

![Registerkarte „Untertitel und Audiospuren“](/help/assets/assets/caption-audio-tracks1.png)

So fügen Sie Beschriftungen hinzu:

1. Öffnen Sie die Seite **Eigenschaften**.
1. Öffnen Sie **Registerkarte Untertitel und** Audiospuren“.
1. Klicken Sie **Beschriftung erstellen** > **Dateien hochladen**.
1. Wählen Sie eine oder mehrere `.vtt` aus.
1. Klicken Sie **Zeichnen**-Symbol neben der Untertiteldatei.

![Dialogfeld „Beschriftung hochladen“](/help/assets/assets/upload-caption.png)

Im Dialogfeld **Beschriftung bearbeiten**:

* **Dateiname** - Name der standardmäßig hochgeladenen Datei.
* **Language** - Untertitelsprache.
* **type** - Untertitel oder Beschriftung.
* **Label** - Anzeigename, der in der Player-Beschriftungsauswahl angezeigt wird.

![Dialogfeld „Beschriftung bearbeiten](/help/assets/assets/edit-captions.png)

1. Klicken Sie auf **Speichern**.
2. Klicken Sie auf **Speichern und schließen**.

>[!NOTE]
>
>Die Bearbeitung von Untertiteltext wird nicht unterstützt. Datei extern aktualisieren und erneut hochladen.

## Validierungsverhalten {#approval-behavior}

Die Validierung hängt vom übergeordneten Video-Asset ab:

* Wenn **Genehmigt** werden neue Dateien nach der Verarbeitung automatisch genehmigt.
* Wenn sie nicht genehmigt sind, folgen sie dem übergeordneten Lebenszyklus.

## Anzeigen des Lebenszyklusstatus einer Datei {#status}

* **Genehmigt** - Bereit zur Wiedergabe
* **Abgelehnt** - Datei abgelehnt

## Standard-Audiospur festlegen {#set-default-audio}

Standardmäßig wird Originalaudio verwendet.

1. Öffnen Sie **Untertitel und Audiospuren**.
1. Audiospur auswählen.
1. Klicken Sie **Als Standard festlegen**.

   ![Als Standardaktion festlegen](/help/assets/assets/set-default.png)

1. Klicken Sie auf **OK**.
1. Klicken Sie auf **Speichern und schließen**.

## Vorschau von Audio und Untertiteln {#preview-audio-captions}

Nach der Verarbeitung:

1. Öffnen Sie die Videovorschau.

   ![Videovorschau-Player](/help/assets/assets/preview-caption-audio.png)

1. Verwenden von Player-Steuerelementen:

   * Audiospuren wechseln
   * Beschriftungen aktivieren

## Untertitel oder Audiodateien herunterladen {#download-tracks}

1. Wählen Sie Untertitel oder Audiodatei aus.
1. Klicken Sie auf **Herunterladen**.

   ![Aktion für Tracking herunterladen](/help/assets/assets/download-caption.png)

1. Klicken Sie auf **Herunterladen**.

Die ausgewählte Datei wird auf Ihr lokales System heruntergeladen.

## Untertitel oder Audiodateien löschen {#delete-tracks}

1. Wählen Sie Untertitel oder Audiodatei aus.
1. Klicken Sie auf **Löschen**.

   ![Track-Aktion löschen](/help/assets/assets/delete-caption.png)

1. Klicken Sie auf **OK**.

Aus dem Video extrahiertes Originalaudio kann nicht gelöscht werden.
