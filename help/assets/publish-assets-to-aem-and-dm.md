---
title: Quick Publish in AEM und Dynamic Media
description: Quick Publish ist eine Funktion in der neuen Benutzeroberfläche oder der Asset-Ansicht. Diese Funktion bietet Benutzern Flexibilität bei der schnellen Veröffentlichung in AEM und Dynamic Media gleichzeitig oder einzeln . Das bedeutet, dass Benutzer nach Auswahl von Assets und Ordnern die Veröffentlichung in Dynamic Media oder die Veröffentlichung in AEM auswählen können. Die Funktion "Quick Publish"bietet die neue Benutzeroberfläche zum Veröffentlichen von Assets und Ordnern in Dynamic Media und AEM.
source-git-commit: a1069ec278143665c1e17ea1a482589763dd153f
workflow-type: tm+mt
source-wordcount: '1219'
ht-degree: 0%

---


# Veröffentlichen von Assets in AEM und Dynamic Media{#Publish-Assets-to-AEM-and-Dynamic-Media}

Mit Experience Manager Assets können Sie Assets mithilfe der Asset-Ansicht schnell in Experience Manager und Dynamic Media veröffentlichen. Dadurch wird sichergestellt, dass Sie Ihre Assets verwalten und sie dann mit [Asset-Ansicht ohne Wechsel zur Admin-Ansicht](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/overview#persona-based-experiences).

Die Experience Manager Assets-Ansicht bietet die Flexibilität, Assets gleichzeitig in AEM oder Dynamic Media oder beidem zu veröffentlichen. Sie können Assets beim Hochladen, Durchsuchen und Suchen nach Assets veröffentlichen. Alle diese Optionen zum Veröffentlichen von Assets werden in diesem Artikel ausführlich erläutert.

## Vorbereitung {#before-you-begin}

Konfigurieren Sie diese Einstellungen, um die Veröffentlichungsoptionen für AEM und Dynamic Media anzuzeigen:

* Um die Veröffentlichungsoptionen für Dynamic Media anzuzeigen, konfigurieren Sie die folgenden Einstellungen mithilfe der Admin-Ansicht:

   * [Erstellen einer Dynamic Media-Cloud-Konfiguration](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/assets/dynamicmedia/config-dm#configuring-dynamic-media-cloud-services).
   * Legen Sie den Veröffentlichungsmodus für Dynamic Media auf Ordnerebene fest. Sie können diese Einstellungen auch beim Erstellen der Dynamic Media-Cloud-Konfiguration konfigurieren. Informationen zum Überschreiben dieser Einstellungen auf Ordnerebene finden Sie unter [Konfigurieren Sie Selektive Veröffentlichung auf Ordnerebene in Dynamic Media](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/selective-publishing).

* Um die Veröffentlichungsoptionen für AEM anzuzeigen, müssen Sie den AEM Veröffentlichungsendpunkt für Ihre Umgebung konfigurieren.

## Veröffentlichen von Assets während des Uploads {#piblish-assets-during-upload}

Sie können Assets beim Hochladen von Assets in einen Ordner in AEM und Dynamic Media veröffentlichen. Die angezeigten Veröffentlichungsoptionen hängen vom Dynamic Media-Veröffentlichungsmodus ab, der für den Ordner festgelegt ist, in den die Assets hochgeladen werden. Der Dynamic Media-Veröffentlichungsmodus kann auf Folgendes festgelegt werden:

* **Bei Aktivierung:** Wenn Assets in diesen Ordner hochgeladen werden, müssen Sie das Asset zuerst explizit veröffentlichen, bevor eine URL/ein Link zur Einbettung bereitgestellt wird.

* **Sofort:** Wenn Assets in diesen Ordner hochgeladen werden, erfasst das System die Assets in Experience Manager und stellt die URL/Einbettung sofort bereit.
* **Selektive Veröffentlichung:** Assets werden entweder nach Ihrer Wahl in Experience Manager oder Dynamic Media veröffentlicht, um sie öffentlich zugänglich zu machen.

### Veröffentlichungsmodus von Dynamic Media auf Bei Aktivierung eingestellt {#dynamic-media-publish-mode-set-to-upon-activation}

So veröffentlichen Sie Assets während des Uploads in einen Ordner, für den der Dynamic Media-Veröffentlichungsmodus auf **Bei Aktivierung**:

1. Klicks **Hinzufügen von Assets** > **Durchsuchen** > **Dateien durchsuchen** , um zum entsprechenden Ordner zum Hochladen von Assets zu navigieren. Die **Veröffentlichungsoptionen** angezeigt. **DM-Veröffentlichungsmodus** as **Bei Aktivierung**.
   ![Bild bei Aktivierung hochladen](/help/assets/assets/upload-upon-activation.png)
2. Auswählen **Veröffentlichen in AEM und Dynamic Media** und klicken **Hochladen**. Die Assets werden gleichzeitig in AEM und Dynamic Media veröffentlicht. Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Status &quot;Veröffentlichen&quot;überprüfen](#check-publish-status).

### Dynamic Media-Veröffentlichungsmodus auf Sofort eingestellt {#dynamic-media-publish-mode-set-to-immediate}

So veröffentlichen Sie Assets während des Uploads in einen Ordner, für den der Dynamic Media-Veröffentlichungsmodus auf **Sofort**:

1. Klicks **Hinzufügen von Assets** > **Durchsuchen** > **Dateien durchsuchen** , um zum entsprechenden Ordner zum Hochladen von Assets zu navigieren. Im Abschnitt &quot;Veröffentlichungsoptionen&quot;wird die **DM-Veröffentlichungsmodus** as **Sofort**.
   ![Bild für Datei-Upload - sofortiger Modus](/help/assets/assets/upload-immediate-mode.png)
Der Veröffentlichungsmodus von Dynamic Media ist wie folgt: **Sofort**, werden die hochgeladenen Assets automatisch in Dynamic Media veröffentlicht, wenn Sie auf **Hochladen**.

2. Wählen Sie Veröffentlichen in **AEM veröffentlichen** die hochgeladenen Assets in AEM und klicken Sie auf Hochladen.

   Wenn Sie **Veröffentlichen in AEM**, werden die Assets in AEM und Dynamic Media veröffentlicht, andernfalls werden die Assets in Dynamic Media veröffentlicht.

   Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Status &quot;Veröffentlichen&quot;überprüfen](#check-publish-status).

### Dynamic Media-Veröffentlichungsmodus auf Selektive Veröffentlichung eingestellt {#dynamic-media-publish-mode-set-to-selective-publish}

So veröffentlichen Sie Assets während des Uploads in einen Ordner, für den der Dynamic Media-Veröffentlichungsmodus auf **Selektive Veröffentlichung**:

1. Klicks **Hinzufügen von Assets** > **Durchsuchen** > **Dateien durchsuchen** , um zum entsprechenden Ordner zum Hochladen von Assets zu navigieren. Im Abschnitt Veröffentlichungsoptionen wird die **DM-Veröffentlichungsmodus** as **Selektive Veröffentlichung**.
   ![Bildselektiven Veröffentlichungsmodus hochladen](/help/assets/assets/upload-image-selective-publish-mode.png)

2. Auswählen **Veröffentlichen in AEM**, **In Dynamic Media veröffentlichen** oder entsprechend Ihren Anforderungen und klicken Sie auf **Hochladen**.

   Die Assets werden basierend auf Ihrer Auswahl in AEM und Dynamic Media veröffentlicht.

   Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Status &quot;Veröffentlichen&quot;überprüfen](#check-publish-status).

## Veröffentlichen von Assets mithilfe der Asset-Durchsuchen-Seite {#publish-assets-using-asset-browse-page}

So veröffentlichen Sie Assets über die Asset-Durchsuchen-Seite:

1. Klicks **Assets** im **Asset-Verwaltung** im linken Bereich verfügbar.
2. Wählen Sie die zu veröffentlichenden Assets oder Ordner aus und klicken Sie auf **Veröffentlichen**.
3. Auswählen **AEM** und klicken **Veröffentlichen** , um Assets in AEM und Dynamic Media zu veröffentlichen.
   ![Asset-Suche](/help/assets/assets/assets-browse-1.png)
Sie können einen Ordner nicht veröffentlichen, für den der Dynamic Media-Veröffentlichungsmodus auf **Selektive Veröffentlichung.** Alle anderen ausgewählten Ordner oder Assets werden nach Auswahl von AEM in AEM und Dynamic Media veröffentlicht.
   ![Asset-Suche](/help/assets/assets/assets-browse-2.png)

## Veröffentlichen von Assets mithilfe der Suchergebnisseite {#publish-assets-using-search-results-page}

So veröffentlichen Sie Assets über die Seite mit den Asset-Suchergebnissen:

1. Geben Sie die Kriterien in der Suchleiste an und klicken Sie auf das Symbol Suchen , um die Ergebnisse anzuzeigen.
2. Wählen Sie die Assets aus, die Sie veröffentlichen möchten, und klicken Sie auf **Veröffentlichen Sie.**
3. Wählen Sie AEM, Dynamic Media oder beide gemäß Ihren Anforderungen aus und klicken Sie auf **Veröffentlichen Sie.**
   ![Suchbild](/help/assets/assets/search-image1.png)
Die Option zum Veröffentlichen in Dynamic Media auf der Suchergebnisseite hängt vom Dynamic Media-Veröffentlichungsmodus ab, der für den Ordner festgelegt ist, in dem das Asset im Repository verfügbar ist.

   >[!NOTE]
   >
   >Wenn Sie einen Ordner auswählen und auf **Veröffentlichen** Auf der Suchergebnisseite zeigt Experience Manager Assets eine Option zum Veröffentlichen von Assets in AEM und nicht in Dynamic Media an, unabhängig von den Einstellungen für den Dynamic Media-Veröffentlichungsmodus für den Ordner.

## Status &quot;Veröffentlichen&quot;überprüfen {#check-publish-status}

So prüfen Sie den Veröffentlichungsstatus für ein Asset oder einen Ordner:

1. Klicks **Assets** im **Asset-Verwaltung** im linken Bereich verfügbar.
2. Wechseln Sie mit dem Ansichtsschalter zur Listenansicht. Sie können Asset-Eigenschaften wie AEM, Veröffentlichen in Dynamic Media, Titel, Größe, Dimensionen usw. anzeigen.\
   Wenn ein Asset oder Ordner nicht veröffentlicht wird, wird der Status für **AEM Publish** und **Dynamic Media Publish** Spalten werden als **Nicht zutreffend.**
   ![Prüfung des Veröffentlichungsstatus1](/help/assets/assets/check-publish-status1.png)
Wenn Sie die Spalten AEM Publish und Dynamic Media Publish nicht in der Listenansicht anzeigen können:
   1. Klicks ![settings](/help/assets/assets/settings-icon.svg) und wählen **AEM Publish** und **Dynamic Media Publish** Spalten aus **Konfigurierbare Spalten** angezeigt.
   2. Klicks **Bestätigen Sie.** Experience Manager Assets fügt die ausgewählten Spalten zur Listenansicht hinzu.

      ![Veröffentlichungsstatus überprüfen2](/help/assets/assets/check-publish-status2.png)

Sie können auch den Veröffentlichungsstatus eines Assets überprüfen, indem Sie ein Asset auswählen und auf **Details.** Die Details sind im Abschnitt **Veröffentlichen** im rechten Bereich verfügbar. Die **Veröffentlichen** gibt das Datum an, an dem die Assets in Dynamic Media und AEM veröffentlicht werden. Wenn Sie den Zeitpunkt der Veröffentlichung der Assets anzeigen müssen, können Sie zur Listenansicht navigieren und diese Details anzeigen.

![Veröffentlichungsstatus 3 überprüfen](/help/assets/assets/check-publish-status3.png)

## Einschränkungen {#limitations}

Die folgenden Funktionen sind beim Veröffentlichen von Assets in AEM und Dynamic Media derzeit nicht verfügbar:

* Veröffentlichen Sie Assets auf der Seite &quot;Asset-Details&quot;in AEM und Dynamic Media.
* Visualisieren Sie die Endpunkte, an denen die Assets veröffentlicht werden, mithilfe des Assistenten für schnelle Veröffentlichung .
* Fügen Sie weitere Assets im Assistenten &quot;Quick Publish&quot;hinzu oder löschen Sie sie.
* Eine Seite zum Anzeigen veröffentlichter Assets.
* Möglichkeit zum Kopieren oder Einfügen der Dynamic Media-URL auf einer Asset-Ebene (wenn die Assets in Dynamic Media veröffentlicht werden).
* Möglichkeit, beim Veröffentlichen in AEM Verweise (Assets, Tags usw.) zu veröffentlichen
* Möglichkeit, den Synchronisierungsstatus von Dynamic Media auf Ordnerebene zu überschreiben.
* Möglichkeit, den Dynamic Media-Veröffentlichungsmodus auf Ordnerebene zu überschreiben.