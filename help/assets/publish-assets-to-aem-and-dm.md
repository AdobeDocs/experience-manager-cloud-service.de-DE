---
title: Quick Publish in [!DNL AEM and Dynamic Media]
description: Mit Quick Publish in  [!DNL Assets view]  können Sie Assets  [!DNL AEM and Dynamic Media]  oder separat in veröffentlichen. Sie können Assets und Ordner auswählen und auswählen, in  [!DNL Dynamic Media]  oder  [!DNL AEM] veröffentlicht werden soll.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, [!DNL Dynamic Media]
role: User
source-git-commit: 138f7ef2023399ce5da9fe80447ac45fd9542064
workflow-type: tm+mt
source-wordcount: '1099'
ht-degree: 38%

---

# Veröffentlichen von Assets in [!DNL AEM and Dynamic Media]{#Publish-Assets-to-AEM-and-Dynamic-Media}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

[!DNL Experience Manager Assets] können Sie Assets mithilfe der [!DNL Assets view] schnell in [!DNL Experience Manager] und [!DNL Dynamic Media] veröffentlichen. Dadurch wird sichergestellt, dass Sie Ihre Assets verwalten und anschließend mit dem veröffentlichen[[!DNL Assets view]  ohne zur  [!DNL Admin view]](/help/assets/overview.md##persona-based-experiences).

[!DNL Experience Manager Assets view] bietet die Flexibilität, Assets in [!DNL AEM] oder [!DNL Dynamic Media] oder in beiden gleichzeitig zu veröffentlichen. Sie können Assets beim Hochladen, Durchsuchen und Suchen von Assets veröffentlichen. Alle diese Optionen zum Veröffentlichen von Assets werden in diesem Artikel ausführlich erläutert.

## Voraussetzungen {#before-you-begin}

Konfigurieren Sie diese Einstellungen, um die Veröffentlichungsoptionen für [!DNL AEM and Dynamic Media] anzuzeigen:

* Um die Veröffentlichungsoptionen für [!DNL Dynamic Media] anzuzeigen, konfigurieren Sie die folgenden Einstellungen in der Admin-Ansicht:

   * [Erstellen einer  [!DNL Dynamic Media] -Cloud-Konfiguration](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Legen Sie den [!DNL Dynamic Media] Veröffentlichungsmodus auf Ordnerebene fest. Sie können diese Einstellungen auch beim Erstellen der [!DNL Dynamic Media] Cloud-Konfiguration konfigurieren. Informationen zum Überschreiben dieser Einstellungen auf Ordnerebene finden Sie unter [Konfigurieren von selektiver Veröffentlichung auf Ordnerebene in [!DNL Dynamic Media]](/help/assets/dynamic-media/selective-publishing.md).

* Um die Veröffentlichungsoptionen für [!DNL AEM] anzuzeigen, müssen Sie den Endpunkt [!DNL AEM] für Ihre Umgebung konfigurieren.

## Veröffentlichen von Assets beim Hochladen {#piblish-assets-during-upload}

Sie können Assets in [!DNL AEM and Dynamic Media] veröffentlichen, während Sie Assets in einen Ordner hochladen. Die angezeigten Veröffentlichungsoptionen hängen von den [!DNL Dynamic Media] Veröffentlichungsmodus-Einstellungen des Ordners ab, in den die Assets hochgeladen werden. [!DNL Dynamic Media] Veröffentlichungsmodus kann auf Folgendes festgelegt werden:

* **[!UICONTROL Bei Aktivierung]:** Wenn Assets in diesen Ordner hochgeladen werden, müssen Sie das Asset zuerst explizit veröffentlichen, bevor eine URL/ein Link zur Einbettung bereitgestellt wird.

* **[!UICONTROL Sofort]:** Wenn Assets in diesen Ordner hochgeladen werden, nimmt das System die Assets in Experience Manager auf und stellt die URL / den Link zur Einbettung sofort bereit.
* **[!UICONTROL Selektive Veröffentlichung]:** Assets werden nach Wahl [!DNL Experience Manager] oder [!DNL Dynamic Media] veröffentlicht, um sie im öffentlich zugänglichen Bereich bereitzustellen.

### [!UICONTROL Veröffentlichungsmodus für Dynamic Media] auf [!UICONTROL Bei Aktivierung] {#dynamic-media-publish-mode-set-to-upon-activation}

So veröffentlichen Sie Assets beim Hochladen in einen Ordner, dessen [!DNL Dynamic Media Publish Mode] auf „Bei Aktivierung **[!UICONTROL festgelegt]**:

1. Klicken Sie auf **[!UICONTROL Assets hinzufügen]** > **[!UICONTROL Durchsuchen]** > **[!UICONTROL Dateien durchsuchen]**, um zum entsprechenden Ordner für den Asset-Upload zu navigieren. Im Abschnitt **[!UICONTROL Veröffentlichungsoptionen]** wird als **[!UICONTROL DM-Veröffentlichungsmodus]** die Einstellung **[!UICONTROL Bei Aktivierung]** angezeigt.
   ![Hochladen bei Aktivierung](/help/assets/assets/upload-uactivation.svg)
2. Wählen Sie **[!UICONTROL In AEM und Dynamic Media veröffentlichen]** aus und klicken Sie auf **[!UICONTROL Hochladen]**. Die Assets werden gleichzeitig in [!DNL AEM and Dynamic Media] veröffentlicht. Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Überprüfen des Veröffentlichungsstatus](#check-publish-status).

### [!UICONTROL Veröffentlichungsmodus für Dynamic Media] auf &quot;[!UICONTROL &quot; ] {#dynamic-media-publish-mode-set-to-immediate}

So veröffentlichen Sie Assets beim Hochladen in einen Ordner, dessen [!UICONTROL Veröffentlichungsmodus für Dynamic Media] auf &quot;**[!UICONTROL &quot;]**:

1. Klicken Sie auf **[!UICONTROL Assets hinzufügen]** > **[!UICONTROL Durchsuchen]** > **[!UICONTROL Dateien durchsuchen]**, um zum entsprechenden Ordner für den Asset-Upload zu navigieren. Im Abschnitt **[!UICONTROL Veröffentlichungsoptionen]** wird für den **[!UICONTROL DM-Veröffentlichungsmodus]** die Einstellung **[!UICONTROL Unmittelbar]** angezeigt.
   ![Bild zum Datei-Upload - Sofortiger Modus](/help/assets/assets/resized-image-pdf-svg-new.svg)
Da der [!UICONTROL Veröffentlichungsmodus für Dynamic ] auf **[!UICONTROL Sofort]** festgelegt ist, werden die hochgeladenen Assets automatisch in [!DNL Dynamic Media] veröffentlicht, wenn Sie auf **[!UICONTROL Hochladen]**.

2. Wählen Sie **In AEM veröffentlichen** aus, um die hochgeladenen Assets in [!DNL AEM] zu veröffentlichen, und klicken Sie auf **[!UICONTROL Hochladen]**.

   Wenn Sie **In AEM veröffentlichen** auswählen, werden die Assets in [!DNL AEM and Dynamic Media] veröffentlicht. Andernfalls werden die Assets in [!DNL Dynamic Media] veröffentlicht.

   Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Überprüfen des Veröffentlichungsstatus](#check-publish-status).

### [!UICONTROL Veröffentlichungsmodus für Dynamic Media] auf &quot;[!UICONTROL  Veröffentlichung“ ] {#dynamic-media-publish-mode-set-to-selective-publish}

Zum Veröffentlichen von Assets während des Uploads in einen Ordner mit [!UICONTROL Veröffentlichungsmodus für Dynamic Media] auf **[!UICONTROL Selektive Veröffentlichung]**:

1. Klicken Sie auf **[!UICONTROL Assets hinzufügen]** > **[!UICONTROL Durchsuchen]** > **[!UICONTROL Dateien durchsuchen]**, um zum entsprechenden Ordner für den Asset-Upload zu navigieren. Im Abschnitt **[!UICONTROL Veröffentlichungsoptionen]** wird für den **[!UICONTROL DM-Veröffentlichungsmodus]** die Einstellung **[!UICONTROL Selektive Veröffentlichung]** angezeigt.
   ![Upload – Modus „Selektive Veröffentlichung“](/help/assets/assets/upload-selective.svg)

2. Wählen Sie abhängig von Ihren Anforderungen **[!UICONTROL In AEM veröffentlichen]**, **[!UICONTROL In Dynamic Media veröffentlichen]** oder beide Optionen aus und klicken Sie auf **Hochladen**.

   Die Assets werden basierend auf Ihrer Auswahl in [!DNL AEM and Dynamic Media] veröffentlicht.

   Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Überprüfen des Veröffentlichungsstatus](#check-publish-status).

## Veröffentlichen von Assets über die Seite „Asset-Suche“ {#publish-assets-using-asset-browse-page}

So veröffentlichen Sie Assets über die Seite „Asset-Suche“:

1. Klicken Sie im Abschnitt **[!UICONTROL Assets-Verwaltung]** im linken Bereich auf **[!UICONTROL Assets]**.
2. Wählen Sie ein oder mehrere Assets oder Ordner aus, die veröffentlicht werden sollen, und klicken Sie auf **[!UICONTROL Veröffentlichen]**.
3. Wählen Sie **[!UICONTROL AEM]** aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**, um Assets in [!DNL AEM and Dynamic Media] zu veröffentlichen.
   ![Assets durchsuchen](/help/assets/assets/browse-uactivation-immediate.svg)
Sie können keinen Ordner veröffentlichen, dessen [!DNL Dynamic Media] Veröffentlichungsmodus auf „Selektive Veröffentlichung **[!UICONTROL eingestellt]**. Alle anderen ausgewählten Ordner oder Assets werden nach der Auswahl von [!DNL AEM] in [!DNL AEM and Dynamic Media] veröffentlicht.
   ![Asset-Suche](/help/assets/assets/browse-selective123.svg)

## Veröffentlichen von Assets über die Seite „Suchergebnisse“ {#publish-assets-using-search-results-page}

So veröffentlichen Sie Assets über die Seite mit den Asset-Suchergebnissen:

1. Geben Sie die Kriterien in der Suchleiste an und klicken Sie auf das Suchsymbol, um die Ergebnisse anzuzeigen.
2. Wählen Sie die Assets aus, die Sie veröffentlichen möchten, und klicken Sie auf **[!UICONTROL Veröffentlichen].**
3. Wählen Sie [!DNL AEM, Dynamic Media] oder beides gemäß Ihren Anforderungen aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**.
   ![Suchbild](/help/assets/assets/search-mode.svg)
Die Option zum Veröffentlichen in [!DNL Dynamic Media] auf der Suchergebnisseite hängt davon ab, welcher Veröffentlichungsmodus [!DNL Dynamic Media] für den Ordner festgelegt wurde, in dem das Asset im Repository verfügbar ist.
   >[!NOTE]
   >
   >Wenn Sie einen Ordner auswählen und auf der ]**auf**[!UICONTROL  Veröffentlichen“ klicken, zeigt [!DNL Experience Manager Assets] eine Option zum Veröffentlichen von Assets in [!DNL AEM] an, [!DNL Dynamic Media] unabhängig von den [!DNL Dynamic Media] Veröffentlichungsmoduseinstellungen für den Ordner.

## Überprüfen des Veröffentlichungsstatus {#check-publish-status}

So überprüfen Sie den Veröffentlichungsstatus für ein Asset oder einen Ordner:

1. Klicken Sie im Abschnitt **[!UICONTROL Assets-Verwaltung]** im linken Bereich auf **[!UICONTROL Assets]**.
2. Wechseln Sie mit dem Anzeigeumschalter zur Listenansicht. Sie können Asset-Eigenschaften wie [!UICONTROL AEM-Veröffentlichung], [!UICONTROL Dynamic Media-Veröffentlichung], [!UICONTROL Titel], [!UICONTROL Größe], [!UICONTROL Dimensionen] usw. anzeigen.\
   Wenn ein Asset oder ein Ordner nicht veröffentlicht wurde, wird der Status für die Spalten **[!UICONTROL AEM Publish]** und **[!UICONTROL Dynamic Media]** Publish) als **[!UICONTROL K.A]** angezeigt.
   ![Veröffentlichungsstatus überprüfen1](/help/assets/assets/check-publish-status1.png)
Wenn Sie die Spalten Veröffentlichen [!DNL AEM] Veröffentlichen und Veröffentlichen [!DNL Dynamic Media] Listenansicht nicht anzeigen können:
   1. Klicken Sie auf ![Einstellungen](/help/assets/assets/settings-icon.svg) und wählen Sie im Dialogfeld **[!UICONTROL Konfigurierbare Spalten]** die Option **[!UICONTROL Dynamic Media-Veröffentlichung]** und **[!UICONTROL AEM-Veröffentlichung]** aus.
   2. Klicken Sie auf **[!UICONTROL Bestätigen]**. [!DNL Experience Manager Assets] fügt die ausgewählten Spalten zur Listenansicht hinzu.

      ![Überprüfen des Veröffentlichungsstatus 2](/help/assets/assets/check-publish-status2.png)

Sie können den Veröffentlichungsstatus eines Assets auch überprüfen, indem Sie ein Asset auswählen und auf **[!UICONTROL Details]** klicken. Die Details sind im Abschnitt **[!UICONTROL Veröffentlichen]** im rechten Bereich verfügbar. Im Abschnitt **[!UICONTROL Veröffentlichen]** wird das Datum aufgelistet, an dem die Assets in [!DNL Dynamic Media] und [!DNL AEM] veröffentlicht werden. Wenn Sie den Zeitpunkt der Asset-Veröffentlichung anzeigen möchten, können Sie zur Listenansicht navigieren und diese Details aufrufen.

![Überprüfen des Veröffentlichungsstatus 3](/help/assets/assets/check-publish-status3.png)

## Einschränkungen {#limitations}

Die folgenden Funktionen sind derzeit nicht im Umfang enthalten, wenn Assets in [!DNL AEM and Dynamic Media] veröffentlicht werden:

* Veröffentlichen von Assets in [!DNL AEM and Dynamic Media] aus dem [!DNL Asset details page].
* Visualisieren der Endpunkte, bei denen die Assets veröffentlicht werden, mithilfe des Assistenten „Quick Publish“
* Hinzufügen oder Löschen weiterer Assets im Assistenten „Quick Publish“
* Seite zum Anzeigen veröffentlichter Assets.
* Eine Möglichkeit zum Kopieren oder Einfügen [!DNL Dynamic Media] URL auf Asset-Ebene (wenn die Assets in [!DNL Dynamic Media] veröffentlicht wurden).
* Möglichkeit, Verweise (Assets, Tags usw.) beim Veröffentlichen in [!DNL AEM] zu veröffentlichen.
* Möglichkeit, [!DNL Dynamic Media] Synchronisierungsstatus auf Ordnerebene zu überschreiben.
* Möglichkeit zum Überschreiben [!DNL Dynamic Media] Veröffentlichungsmodus auf Ordnerebene
* Noch keine Unterstützung für „Veröffentlichung verwalten“.
