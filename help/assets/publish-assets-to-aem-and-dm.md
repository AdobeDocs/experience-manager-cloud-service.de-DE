---
title: Quick Publish in AEM und Dynamic Media
description: Mit Quick Publish in der Assets-Ansicht können Sie Assets gleichzeitig oder separat in AEM und Dynamic Media veröffentlichen. Sie können Assets und Ordner auswählen und sich für eine Veröffentlichung in Dynamic Media oder AEM entscheiden.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, Dynamic Media
role: User
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: ht
source-wordcount: '1206'
ht-degree: 100%

---

# Veröffentlichen von Assets in AEM und Dynamic Media{#Publish-Assets-to-AEM-and-Dynamic-Media}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Mit Experience Manager Assets können Sie über die Asset-Ansicht Assets schnell in Experience Manager und Dynamic Media veröffentlichen. Dadurch wird sichergestellt, dass Sie Ihre Assets verwalten und dann mithilfe der [Assets-Ansicht veröffentlichen können, ohne zur Admin-Ansicht zu wechseln](/help/assets/overview.md##persona-based-experiences).

Die Experience Manager Assets-Ansicht bietet die Flexibilität, Assets in AEM oder Dynamic Media oder gleichzeitig in beides zu veröffentlichen. Sie können Assets beim Hochladen, Durchsuchen und Suchen von Assets veröffentlichen. Alle diese Optionen zum Veröffentlichen von Assets werden in diesem Artikel ausführlich erläutert.

## Voraussetzungen {#before-you-begin}

Konfigurieren Sie diese Einstellungen, um die Veröffentlichungsoptionen für AEM und Dynamic Media anzuzeigen:

* Um die Veröffentlichungsoptionen für Dynamic Media anzuzeigen, konfigurieren Sie die folgenden Einstellungen mithilfe der Admin-Ansicht:

   * [Erstellen Sie eine Dynamic Media-Cloud-Konfiguration](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Legen Sie den Dynamic Media-Veröffentlichungsmodus auf Ordnerebene fest. Sie können diese Einstellungen auch beim Erstellen der Dynamic Media-Cloud-Konfiguration einrichten. Informationen zum Überschreiben dieser Einstellungen auf Ordnerebene finden Sie unter [Konfigurieren einer selektiven Veröffentlichung auf der Ordnerebene in Dynamic Media](/help/assets/dynamic-media/selective-publishing.md).

* Um die Veröffentlichungsoptionen für AEM anzuzeigen, müssen Sie den AEM-Veröffentlichungsendpunkt für Ihre Umgebung konfigurieren.

## Veröffentlichen von Assets beim Hochladen {#piblish-assets-during-upload}

Sie können Assets beim Hochladen von Assets in einen Ordner in AEM und Dynamic Media veröffentlichen. Die angezeigten Veröffentlichungsoptionen hängen vom Dynamic Media-Veröffentlichungsmodus ab, der für den Upload-Ordner der Assets festgelegt ist. Der Dynamic Media-Veröffentlichungsmodus kann wie folgt eingestellt werden:

* **Bei Aktivierung**: Wenn Assets in diesen Ordner hochgeladen werden, müssen Sie das Asset zuerst explizit veröffentlichen, bevor eine URL/ein Einbettungs-Link bereitgestellt wird.

* **Unmittelbar**: Wenn Assets in diesen Ordner hochgeladen werden, nimmt das System die Assets in Experience Manager auf und stellt die URL/den Einbettungs-Link sofort bereit.
* **Selektive Veröffentlichung**: Assets werden für die Bereitstellung im öffentlich zugänglichen Bereich je nach Wahl entweder in Experience Manager oder Dynamic Media veröffentlicht.

### Dynamic Media-Veröffentlichungsmodus mit der Einstellung „Bei Aktivierung“ {#dynamic-media-publish-mode-set-to-upon-activation}

So veröffentlichen Sie Assets beim Hochladen in einen Ordner, für den der Dynamic Media-Veröffentlichungsmodus auf **Bei Aktivierung** eingestellt ist:

1. Klicken Sie auf **Assets hinzufügen** > **Durchsuchen** > **Dateien durchsuchen**, um zum entsprechenden Ordner für den Asset-Upload zu navigieren. Im Abschnitt **Veröffentlichungsoptionen** wird für **DM-Veröffentlichungsmodus** die Einstellung **Bei Aktivierung** angezeigt.
   ![Hochladen bei Aktivierung](/help/assets/assets/upload-uactivation.svg)
2. Wählen Sie **In AEM und Dynamic Media veröffentlichen** aus und klicken Sie auf **Hochladen**. Die Assets werden gleichzeitig in AEM und Dynamic Media veröffentlicht. Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Überprüfen des Veröffentlichungsstatus](#check-publish-status).

### Dynamic Media-Veröffentlichungsmodus mit der Einstellung „Unmittelbar“ {#dynamic-media-publish-mode-set-to-immediate}

So veröffentlichen Sie Assets beim Hochladen in einen Ordner, für den der Dynamic Media-Veröffentlichungsmodus auf **Unmittelbar** eingestellt ist:

1. Klicken Sie auf **Assets hinzufügen** > **Durchsuchen** > **Dateien durchsuchen**, um zum entsprechenden Ordner für den Asset-Upload zu navigieren. Im Abschnitt „Veröffentlichungsoptionen“ wird für **DM-Veröffentlichungsmodus** die Einstellung **Unmittelbar** angezeigt.
   ![Datei-Upload – Modus „Unmittelbar“](/help/assets/assets/resized-image-pdf-svg-new.svg)


   Da der Dynamic Media-Veröffentlichungsmodus **Unmittelbar** lautet, werden die hochgeladenen Assets automatisch in Dynamic Media veröffentlicht, wenn Sie auf **Hochladen** klicken.

2. Wählen Sie **In AEM veröffentlichen** aus, um die hochgeladenen Assets in AEM zu veröffentlichen, und klicken Sie auf „Hochladen“.

   Wenn Sie **In AEM veröffentlichen** auswählen, werden die Assets in AEM und Dynamic Media veröffentlicht, andernfalls nur in Dynamic Media.

   Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Überprüfen des Veröffentlichungsstatus](#check-publish-status).

### Dynamic Media-Veröffentlichungsmodus mit der Einstellung „Selektive Veröffentlichung“ {#dynamic-media-publish-mode-set-to-selective-publish}

So veröffentlichen Sie Assets beim Hochladen in einen Ordner, für den der Dynamic Media-Veröffentlichungsmodus auf **Selektive Veröffentlichung** eingestellt ist:

1. Klicken Sie auf **Assets hinzufügen** > **Durchsuchen** > **Dateien durchsuchen**, um zum entsprechenden Ordner für den Asset-Upload zu navigieren. Im Abschnitt „Veröffentlichungsoptionen“ wird für **DM-Veröffentlichungsmodus** die Einstellung **Selektive Veröffentlichung** angezeigt.
   ![Upload – Modus „Selektive Veröffentlichung“](/help/assets/assets/upload-selective.svg)

2. Wählen Sie abhängig von Ihren Anforderungen **In AEM veröffentlichen**, **In Dynamic Media veröffentlichen** oder beide Optionen aus und klicken Sie auf **Hochladen**.

   Die Assets werden basierend auf Ihrer Auswahl in AEM und Dynamic Media veröffentlicht.

   Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Überprüfen des Veröffentlichungsstatus](#check-publish-status).

## Veröffentlichen von Assets über die Seite „Asset-Suche“ {#publish-assets-using-asset-browse-page}

So veröffentlichen Sie Assets über die Seite „Asset-Suche“:

1. Klicken Sie im Abschnitt **Assets-Verwaltung** im linken Bereich auf **Assets**.
2. Wählen Sie die Assets oder Ordner aus, die veröffentlicht werden sollen, und klicken Sie auf **Veröffentlichen**.
3. Wählen Sie **AEM** aus und klicken Sie auf **Veröffentlichen**, um Assets in AEM und Dynamic Media zu veröffentlichen.
   ![Asset-Suche](/help/assets/assets/browse-uactivation-immediate.svg)
Sie können einen Ordner nicht veröffentlichen, für den der Dynamic Media-Veröffentlichungsmodus auf „Selektive Veröffentlichung“ eingestellt ist.**** Alle anderen ausgewählten Ordner oder Assets werden nach Auswahl von AEM in AEM und Dynamic Media veröffentlicht.
   ![Asset-Suche](/help/assets/assets/browse-selective123.svg)

## Veröffentlichen von Assets über die Seite „Suchergebnisse“ {#publish-assets-using-search-results-page}

So veröffentlichen Sie Assets über die Seite mit den Asset-Suchergebnissen:

1. Geben Sie die Kriterien in der Suchleiste an und klicken Sie auf das Suchsymbol, um die Ergebnisse anzuzeigen.
2. Wählen Sie die Assets aus, die veröffentlicht werden sollen, und klicken Sie auf **Veröffentlichen**.
3. Wählen Sie abhängig von Ihren Anforderungen AEM, Dynamic Media oder beides aus und klicken Sie auf **Veröffentlichen**.
   ![Suchen](/help/assets/assets/search-mode.svg)
Die Option zum Veröffentlichen in Dynamic Media auf der Seite „Suchergebnisse“ hängt vom Dynamic Media-Veröffentlichungsmodus ab, der für den Ordner festgelegt ist, in dem das Asset im Repository verfügbar ist.

   >[!NOTE]
   >
   >Wenn Sie einen Ordner auswählen und auf der Seite „Suchergebnisse“ auf **Veröffentlichen** klicken, zeigt Experience Manager Assets unabhängig von den Einstellungen für den Dynamic Media-Veröffentlichungsmodus für den Ordner eine Option zum Veröffentlichen von Assets in AEM und nicht in Dynamic Media an.

## Überprüfen des Veröffentlichungsstatus {#check-publish-status}

So überprüfen Sie den Veröffentlichungsstatus für ein Asset oder einen Ordner:

1. Klicken Sie im Abschnitt **[!UICONTROL Assets-Verwaltung]** im linken Bereich auf **[!UICONTROL Assets]**.
2. Wechseln Sie mit dem Ansichtsschalter zur Listenansicht. Sie können Asset-Eigenschaften wie AEM-Veröffentlichung, Dynamic Media-Veröffentlichung, Titel, Größe, Dimensionen usw. anzeigen.\
   Wenn ein Asset oder Ordner nicht veröffentlicht wurde, wird für die Spalten **AEM-Veröffentlichung** und **Dynamic Media-Veröffentlichung** der Status **K/A** angezeigt.
   ![Überprüfen des Veröffentlichungsstatus 1](/help/assets/assets/check-publish-status1.png)
Gehen Sie wie folgt vor, wenn die Spalten „AEM-Veröffentlichung“ und „Dynamic Media-Veröffentlichung“ nicht in der Listenansicht zu sehen sind:
   1. Klicken Sie auf ![Einstellungen](/help/assets/assets/settings-icon.svg) und wählen Sie im Dialogfeld **Konfigurierbare Spalten** die Option **Dynamic Media-Veröffentlichung** und **AEM-Veröffentlichung** aus.
   2. Klicken Sie auf **Bestätigen.** Experience Manager Assets fügt der Listenansicht die ausgewählten Spalten hinzu.

      ![Überprüfen des Veröffentlichungsstatus 2](/help/assets/assets/check-publish-status2.png)

Sie können den Veröffentlichungsstatus eines Assets auch überprüfen, indem Sie ein Asset auswählen und auf „Details“ klicken.**** Die Details sind im Abschnitt **Veröffentlichen** im rechten Bereich verfügbar. Im Abschnitt **Veröffentlichen** wird das Datum aufgelistet, zu dem die Assets in Dynamic Media und AEM veröffentlicht werden. Wenn Sie den Zeitpunkt der Asset-Veröffentlichung anzeigen möchten, können Sie zur Listenansicht navigieren und diese Details aufrufen.

![Überprüfen des Veröffentlichungsstatus 3](/help/assets/assets/check-publish-status3.png)

## Einschränkungen {#limitations}

Die folgenden Funktionen sind beim Veröffentlichen von Assets in AEM und Dynamic Media derzeit nicht verfügbar:

* Veröffentlichen von Assets in AEM und Dynamic Media über die Seite „Asset-Details“.
* Visualisieren der Endpunkte, bei denen die Assets veröffentlicht werden, mithilfe des Assistenten „Quick Publish“.
* Hinzufügen oder Löschen weiterer Assets im Assistenten „Quick Publish“.
* Seite zum Anzeigen veröffentlichter Assets.
* Möglichkeit zum Kopieren oder Einfügen der Dynamic Media-URL auf Asset-Ebene (bei Veröffentlichung der Assets in Dynamic Media).
* Möglichkeit zum Veröffentlichen von Verweisen (Assets, Tags usw.) beim Veröffentlichen in AEM
* Möglichkeit zum Überschreiben des Synchronisierungsstatus von Dynamic Media auf Ordnerebene.
* Möglichkeit zum Überschreiben des Dynamic Media-Veröffentlichungsmodus auf Ordnerebene
* Noch keine Unterstützung für „Veröffentlichung verwalten“.
