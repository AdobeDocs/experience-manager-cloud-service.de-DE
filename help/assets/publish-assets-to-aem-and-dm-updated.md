---
title: Schnelles Publish-AEM und Dynamic Media
description: Mit der Schnellansicht Publish in der Assets-Ansicht können Sie Assets gleichzeitig oder separat in AEM und Dynamic Media veröffentlichen. Sie können Assets und Ordner auswählen und die Veröffentlichung in Dynamic Media oder AEM auswählen.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
source-git-commit: cb8a5e5e8ecec2884c061d60f2519ba3e0208f81
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 0%

---

# Veröffentlichen von Assets in AEM und Dynamic Media{#Publish-Assets-to-AEM-and-Dynamic-Media}

Mit Experience Manager Assets können Sie Assets mithilfe der Assets-Ansicht schnell in Experience Manager und Dynamic Media veröffentlichen. Dadurch wird sichergestellt, dass Sie Ihre Assets verwalten und sie dann mithilfe der [Assets-Ansicht veröffentlichen, ohne zur Admin-Ansicht](/help/assets/overview.md##persona-based-experiences) zu wechseln.

Die Experience Manager Assets-Ansicht bietet die Flexibilität, Assets gleichzeitig in AEM oder Dynamic Media oder beidem zu veröffentlichen. Sie können Assets beim Hochladen, Durchsuchen und Suchen nach Assets veröffentlichen. Alle diese Optionen zum Veröffentlichen von Assets werden in diesem Artikel ausführlich erläutert.

## Vorbereitung {#before-you-begin}

Konfigurieren Sie diese Einstellungen, um die Veröffentlichungsoptionen für AEM und Dynamic Media anzuzeigen:

* Um die Veröffentlichungsoptionen für Dynamic Media anzuzeigen, konfigurieren Sie die folgenden Einstellungen mithilfe der Admin-Ansicht:

   * [Erstellen Sie eine Dynamic Media-Cloud-Konfiguration](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Legen Sie den Dynamic Media Publish-Modus auf Ordnerebene fest. Sie können diese Einstellungen auch beim Erstellen der Dynamic Media-Cloud-Konfiguration konfigurieren. Informationen zum Überschreiben dieser Einstellungen auf Ordnerebene finden Sie unter [Konfigurieren der Auswahl von Publish auf Ordnerebene in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

* Um die Veröffentlichungsoptionen für AEM anzuzeigen, müssen Sie den AEM Veröffentlichungsendpunkt für Ihre Umgebung konfigurieren.

## Publish Assets beim Hochladen {#piblish-assets-during-upload}

Sie können Assets beim Hochladen von Assets in einen Ordner in AEM und Dynamic Media veröffentlichen. Die angezeigten Veröffentlichungsoptionen hängen vom Dynamic Media-Veröffentlichungsmodus ab, der für den Ordner festgelegt ist, in den die Assets hochgeladen werden. Der Dynamic Media-Veröffentlichungsmodus kann auf Folgendes festgelegt werden:

* **Nach Aktivierung:** Wenn Assets in diesen Ordner hochgeladen werden, müssen Sie das Asset zuerst explizit veröffentlichen, bevor eine URL/ein Link zur Einbettung bereitgestellt wird.

* **Sofort:** Wenn Assets in diesen Ordner hochgeladen werden, nimmt das System die Assets in den Experience Manager auf und stellt die URL/den Link zur Einbettung sofort bereit.
* **Selektiver Publish:** Assets wird entweder auf Ihrem Experience Manager oder in Dynamic Media veröffentlicht, um ihn öffentlich zugänglich zu machen.

### Dynamic Media Publish-Modus auf Bei Aktivierung eingestellt {#dynamic-media-publish-mode-set-to-upon-activation}

So veröffentlichen Sie Assets während des Uploads in einen Ordner, für den der Dynamic Media Publish-Modus auf **Bei Aktivierung** festgelegt ist:

1. Klicken Sie auf **Assets hinzufügen** > **Durchsuchen** > **Dateien durchsuchen** , um zum entsprechenden Ordner zu navigieren, um Assets hochzuladen. Im Abschnitt **Publish-Optionen** wird der **DM Publish-Modus** als **Bei Aktivierung** angezeigt.
   ![Bild bei Aktivierung hochladen](/help/assets/assets/upload-uactivation.svg)
2. Wählen Sie **Publish zu AEM und Dynamic Media** und klicken Sie auf **Upload**. Die Assets werden gleichzeitig in AEM und Dynamic Media veröffentlicht. Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Publish-Status überprüfen](#check-publish-status).

### Dynamic Media Publish-Modus auf Sofort eingestellt {#dynamic-media-publish-mode-set-to-immediate}

So veröffentlichen Sie Assets während des Uploads in einen Ordner, für den der Dynamic Media Publish-Modus auf **Sofort** festgelegt ist:

1. Klicken Sie auf **Assets hinzufügen** > **Durchsuchen** > **Dateien durchsuchen** , um zum entsprechenden Ordner zu navigieren, um Assets hochzuladen. Im Abschnitt &quot;Publish-Optionen&quot;wird der **DM Publish-Modus** als **Sofort** angezeigt.
   ![Bild für den Datei-Upload - sofortiger Modus](/help/assets/assets/resized-image-pdf-svg-new.svg)


   Da der Dynamic Media Publish-Modus **Sofort** ist, werden die hochgeladenen Assets automatisch in Dynamic Media veröffentlicht, wenn Sie auf **Hochladen** klicken.

2. Wählen Sie Publish auf **AEM aus, um die hochgeladenen Assets in AEM zu veröffentlichen, und klicken Sie auf &quot;Hochladen&quot;.**

   Wenn Sie **Publish zu AEM** auswählen, werden die Assets in AEM und Dynamic Media veröffentlicht, andernfalls werden die Assets in Dynamic Media veröffentlicht.

   Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Publish-Status überprüfen](#check-publish-status).

### Dynamic Media Publish-Modus auf Selektive Publish eingestellt {#dynamic-media-publish-mode-set-to-selective-publish}

So veröffentlichen Sie Assets während des Uploads in einen Ordner, für den der Dynamic Media Publish-Modus auf **Selektive Publish** festgelegt ist:

1. Klicken Sie auf **Assets hinzufügen** > **Durchsuchen** > **Dateien durchsuchen** , um zum entsprechenden Ordner zu navigieren, um Assets hochzuladen. Im Abschnitt &quot;Publish-Optionen&quot;wird der **DM Publish-Modus** als **Selektiver Publish** angezeigt.
   ![ Bildselektiven Veröffentlichungsmodus hochladen](/help/assets/assets/upload-selective.svg)

2. Wählen Sie **Publish zu AEM**, **Publish zu Dynamic Media** oder beide Ihrer Anforderungen aus und klicken Sie auf **Upload**.

   Die Assets werden basierend auf Ihrer Auswahl in AEM und Dynamic Media veröffentlicht.

   Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Publish-Status überprüfen](#check-publish-status).

## Publish-Assets mithilfe der Asset-Durchsuchen-Seite {#publish-assets-using-asset-browse-page}

So veröffentlichen Sie Assets über die Asset-Durchsuchen-Seite:

1. Klicken Sie im Bereich **Assets-Verwaltung** im linken Bereich auf **Assets** .
2. Wählen Sie die Assets oder Ordner aus, die Sie veröffentlichen möchten, und klicken Sie auf **Publish**.
3. Wählen Sie **AEM** und klicken Sie auf **Publish** , um Assets in AEM und Dynamic Media zu veröffentlichen.
   ![Assets durchsuchen](/help/assets/assets/browse-uactivation-immediate.svg)
Sie können einen Ordner nicht veröffentlichen, für den der Dynamic Media Publish-Modus auf &quot;Selektive Veröffentlichung&quot;festgelegt ist.**** Alle anderen ausgewählten Ordner oder Assets werden nach Auswahl von AEM in AEM und Dynamic Media veröffentlicht.
   ![Assets durchsuchen](/help/assets/assets/browse-selective123.svg)

## Publish-Assets mithilfe der Suchergebnisseite {#publish-assets-using-search-results-page}

So veröffentlichen Sie Assets über die Seite mit den Asset-Suchergebnissen:

1. Geben Sie die Kriterien in der Suchleiste an und klicken Sie auf das Symbol Suchen , um die Ergebnisse anzuzeigen.
2. Wählen Sie die Assets aus, die Sie veröffentlichen möchten, und klicken Sie auf **Publish**.
3. Wählen Sie AEM, Dynamic Media oder beide gemäß Ihren Anforderungen aus und klicken Sie auf **Publish**.
   ![Suchbild](/help/assets/assets/search-mode.svg)
Die Option zum Veröffentlichen in Dynamic Media auf der Suchergebnisseite hängt vom Dynamic Media Publish-Modus ab, der auf den Ordner festgelegt ist, in dem das Asset im Repository verfügbar ist.

   >[!NOTE]
   >
   >Wenn Sie einen Ordner auswählen und auf der Suchergebnisseite auf &quot;**Publish**&quot;klicken, zeigt Experience Manager Assets unabhängig von den Einstellungen für den Dynamic Media Publish-Modus für den Ordner eine Option zum Veröffentlichen von Assets in AEM und nicht in Dynamic Media an.

## Überprüfen des Publish-Status {#check-publish-status}

So prüfen Sie den Veröffentlichungsstatus für ein Asset oder einen Ordner:

1. Klicken Sie im Bereich **[!UICONTROL Assets-Verwaltung]** im linken Bereich auf **[!UICONTROL Assets]** .
2. Wechseln Sie mit dem Ansichtsschalter zur Listenansicht. Sie können Asset-Eigenschaften wie AEM Publish, Dynamic Media Publish, Titel, Größe, Dimensionen usw. anzeigen.\
   Wenn ein Asset oder Ordner nicht veröffentlicht wurde, wird der Status für die Spalten **AEM Publish** und **Dynamic Media Publish** als **K/A** angezeigt.
   ![Überprüfen Sie den Veröffentlichungsstatus1](/help/assets/assets/check-publish-status1.png)
Wenn Sie die Spalten AEM Publish und Dynamic Media Publish nicht in der Listenansicht anzeigen können:
   1. Klicken Sie auf ![settings](/help/assets/assets/settings-icon.svg) und wählen Sie die Spalten **AEM Publish** und **Dynamic Media Publish** aus dem Dialogfeld **Konfigurierbare Spalten** aus.
   2. Klicken Sie auf **Bestätigen.** Experience Manager Assets fügt die ausgewählten Spalten zur Listenansicht hinzu.

      ![Überprüfen Sie den Veröffentlichungsstatus2](/help/assets/assets/check-publish-status2.png)

Sie können auch den Veröffentlichungsstatus eines Assets überprüfen, indem Sie ein Asset auswählen und auf **Details klicken.** Die Details sind im Abschnitt **Publish** verfügbar, der im rechten Bereich verfügbar ist. Im Abschnitt **Publish** wird das Datum aufgelistet, an dem die Assets in Dynamic Media und AEM veröffentlicht werden. Wenn Sie den Zeitpunkt der Veröffentlichung der Assets anzeigen müssen, können Sie zur Listenansicht navigieren und diese Details anzeigen.

![Überprüfen Sie den Veröffentlichungsstatus 3](/help/assets/assets/check-publish-status3.png)

## Einschränkungen {#limitations}

Die folgenden Funktionen sind beim Veröffentlichen von Assets in AEM und Dynamic Media derzeit nicht verfügbar:

* Publish-Assets in AEM und Dynamic Media von der Asset-Detailseite aus.
* Visualisieren Sie mithilfe des Quick Publish-Assistenten die Endpunkte, an denen die Assets veröffentlicht werden.
* Fügen Sie weitere Assets im Assistenten für schnelle Publish hinzu oder löschen Sie sie.
* Eine Seite zum Anzeigen veröffentlichter Assets.
* Möglichkeit zum Kopieren oder Einfügen der Dynamic Media-URL auf einer Asset-Ebene (wenn die Assets in Dynamic Media veröffentlicht werden).
* Möglichkeit, beim Veröffentlichen in AEM Verweise (Assets, Tags usw.) zu veröffentlichen
* Möglichkeit, den Synchronisierungsstatus von Dynamic Media auf Ordnerebene zu überschreiben.
* Möglichkeit, den Dynamic Media Publish-Modus auf Ordnerebene zu überschreiben
* Veröffentlichung verwalten wird noch nicht unterstützt.
