---
title: Quick Publish in  [!DNL AEM and Dynamic Media]
description: Mit Quick Publish in  [!DNL Assets view]  können Sie Assets gleichzeitig oder separat in  [!DNL AEM and Dynamic Media]  veröffentlichen. Sie können Assets und Ordner auswählen und sich für eine Veröffentlichung in  [!DNL Dynamic Media]  oder  [!DNL AEM] entscheiden.
exl-id: 147c1c35-0d81-4458-b4ed-7541d2b0dd54
feature: Publishing, [!DNL Dynamic Media]
role: User
source-git-commit: 138f7ef2023399ce5da9fe80447ac45fd9542064
workflow-type: ht
source-wordcount: '1099'
ht-degree: 100%

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

Mit [!DNL Experience Manager Assets] können Sie Assets mithilfe der [!DNL Assets view] schnell in [!DNL Experience Manager] und [!DNL Dynamic Media] veröffentlichen. Dadurch wird sichergestellt, dass Sie Ihre Assets verwalten und dann mithilfe der Assets-Ansicht veröffentlichen können, [[!DNL Assets view] ohne zur Admin-Ansicht zu wechseln [!DNL Admin view]](/help/assets/overview.md##persona-based-experiences).

[!DNL Experience Manager Assets view] bietet die Flexibilität, Assets in [!DNL AEM] oder [!DNL Dynamic Media] oder in beiden gleichzeitig zu veröffentlichen. Sie können Assets beim Hochladen, Durchsuchen und Suchen von Assets veröffentlichen. Alle diese Optionen zum Veröffentlichen von Assets werden in diesem Artikel ausführlich erläutert.

## Bevor Sie beginnen {#before-you-begin}

Konfigurieren Sie diese Einstellungen, um die Veröffentlichungsoptionen für [!DNL AEM and Dynamic Media] anzuzeigen:

* Um die Veröffentlichungsoptionen für [!DNL Dynamic Media] anzuzeigen, konfigurieren Sie die folgenden Einstellungen mithilfe der Admin-Ansicht:

   * [Erstellen Sie eine  [!DNL Dynamic Media] Cloud-Konfiguration](/help/assets/dynamic-media/config-dm.md#configuring-dynamic-media-cloud-services).
   * Legen Sie auf der Ordnerebene den [!DNL Dynamic Media]-Veröffentlichungsmodus fest. Sie können diese Einstellungen auch beim Erstellen der [!DNL Dynamic Media]-Cloud-Konfiguration einrichten. Informationen zum Überschreiben dieser Einstellungen auf Ordnerebene finden Sie unter [Konfigurieren einer selektiven Veröffentlichung auf der Ordnerebene in Dynamic Media [!DNL Dynamic Media]](/help/assets/dynamic-media/selective-publishing.md).

* Um die Veröffentlichungsoptionen für [!DNL AEM] anzuzeigen, müssen Sie den [!DNL AEM]-Veröffentlichungsendpunkt für Ihre Umgebung konfigurieren.

## Veröffentlichen von Assets beim Hochladen {#piblish-assets-during-upload}

Sie können Assets beim Hochladen von Assets in einen Ordner in [!DNL AEM and Dynamic Media] veröffentlichen. Die angezeigten Veröffentlichungsoptionen hängen von den Einstellungen für den [!DNL Dynamic Media]-Veröffentlichungsmodus ab, die für den Upload-Ordner der Assets festgelegt sind. Der [!DNL Dynamic Media]-Veröffentlichungsmodus kann wie folgt eingestellt werden:

* **[!UICONTROL Bei Aktivierung:]:** Wenn Assets in diesen Ordner hochgeladen werden, müssen Sie das Asset zuerst explizit veröffentlichen, bevor eine URL bzw. ein Einbettungs-Link bereitgestellt wird.

* **[!UICONTROL Unmittelbar]:** Wenn Assets in diesen Ordner hochgeladen werden, nimmt das System die Assets in Experience Manager auf und stellt die URL bzw. den Einbettungs-Link sofort bereit.
* **[!UICONTROL Selektive Veröffentlichung]:** Assets werden für die Bereitstellung im öffentlich zugänglichen Bereich je nach Wahl entweder in [!DNL Experience Manager] oder [!DNL Dynamic Media] veröffentlicht.

### [!UICONTROL Dynamic Media-Veröffentlichungsmodus] mit der Einstellung [!UICONTROL Bei Aktivierung] {#dynamic-media-publish-mode-set-to-upon-activation}

So veröffentlichen Sie Assets beim Hochladen in einen Ordner, für den der [!DNL Dynamic Media Publish Mode] auf **[!UICONTROL Bei Aktivierung]** eingestellt ist:

1. Klicken Sie auf **[!UICONTROL Assets hinzufügen]** > **[!UICONTROL Durchsuchen]** > **[!UICONTROL Dateien durchsuchen]**, um zum entsprechenden Ordner für den Asset-Upload zu navigieren. Im Abschnitt **[!UICONTROL Veröffentlichungsoptionen]** wird als **[!UICONTROL DM-Veröffentlichungsmodus]** die Einstellung **[!UICONTROL Bei Aktivierung]** angezeigt.
   ![Hochladen bei Aktivierung](/help/assets/assets/upload-uactivation.svg)
2. Wählen Sie **[!UICONTROL In AEM und Dynamic Media veröffentlichen]** aus und klicken Sie auf **[!UICONTROL Hochladen]**. Die Assets werden gleichzeitig in [!DNL AEM and Dynamic Media] veröffentlicht. Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Überprüfen des Veröffentlichungsstatus](#check-publish-status).

### [!UICONTROL Dynamic Media-Veröffentlichungsmodus] mit der Einstellung [!UICONTROL Unmittelbar] {#dynamic-media-publish-mode-set-to-immediate}

So veröffentlichen Sie Assets beim Hochladen in einen Ordner, für den der [!UICONTROL Dynamic Media-Veröffentlichungsmodus] auf **[!UICONTROL Unmittelbar]** eingestellt ist:

1. Klicken Sie auf **[!UICONTROL Assets hinzufügen]** > **[!UICONTROL Durchsuchen]** > **[!UICONTROL Dateien durchsuchen]**, um zum entsprechenden Ordner für den Asset-Upload zu navigieren. Im Abschnitt **[!UICONTROL Veröffentlichungsoptionen]** wird für den **[!UICONTROL DM-Veröffentlichungsmodus]** die Einstellung **[!UICONTROL Unmittelbar]** angezeigt.
   ![Bild zum Datei-Upload – Modus „Unmittelbar“](/help/assets/assets/resized-image-pdf-svg-new.svg)
Da der [!UICONTROL Veröffentlichungsmodus für Dynamic Media] auf **[!UICONTROL Unmittelbar]** festgelegt ist, werden die hochgeladenen Assets automatisch in [!DNL Dynamic Media] veröffentlicht, wenn Sie auf **[!UICONTROL Hochladen]** klicken.

2. Wählen Sie **In AEM veröffentlichen** aus, um die hochgeladenen Assets in [!DNL AEM] zu veröffentlichen, und klicken Sie auf **[!UICONTROL Hochladen]**.

   Wenn Sie **In AEM veröffentlichen** auswählen, werden die Assets in [!DNL AEM and Dynamic Media] veröffentlicht, andernfalls werden sie in [!DNL Dynamic Media] veröffentlicht.

   Informationen zum aktualisierten Veröffentlichungsstatus für diese Assets finden Sie unter [Überprüfen des Veröffentlichungsstatus](#check-publish-status).

### [!UICONTROL Dynamic Media-Veröffentlichungsmodus] mit der Einstellung [!UICONTROL Selektive Veröffentlichung] {#dynamic-media-publish-mode-set-to-selective-publish}

So veröffentlichen Sie Assets beim Hochladen in einen Ordner, für den der [!UICONTROL Dynamic Media-Veröffentlichungsmodus] auf **[!UICONTROL Selektive Veröffentlichung]** eingestellt ist:

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
   ![Asset-Suche](/help/assets/assets/browse-uactivation-immediate.svg)
Sie können einen Ordner nicht veröffentlichen, für den der [!DNL Dynamic Media]-Veröffentlichungsmodus auf **[!UICONTROL Selektive Veröffentlichung]** eingestellt ist. Alle anderen ausgewählten Ordner oder Assets werden nach der Auswahl von [!DNL AEM] in [!DNL AEM and Dynamic Media] veröffentlicht.
   ![Asset-Suche](/help/assets/assets/browse-selective123.svg)

## Veröffentlichen von Assets über die Seite „Suchergebnisse“ {#publish-assets-using-search-results-page}

So veröffentlichen Sie Assets über die Seite mit den Asset-Suchergebnissen:

1. Geben Sie die Kriterien in der Suchleiste an und klicken Sie auf das Suchsymbol, um die Ergebnisse anzuzeigen.
2. Wählen Sie die Assets aus, die veröffentlicht werden sollen, und klicken Sie auf **[!UICONTROL Veröffentlichen].**
3. Wählen Sie abhängig von Ihren Anforderungen [!DNL AEM, Dynamic Media] oder beides aus und klicken Sie auf **[!UICONTROL Veröffentlichen]**.
   ![Bild suchen](/help/assets/assets/search-mode.svg)
Die Option zum Veröffentlichen in Dynamic Media auf der Seite [!DNL Dynamic Media] hängt vom [!DNL Dynamic Media]-Veröffentlichungsmodus ab, der für den Ordner festgelegt ist, in dem das Asset im Repository verfügbar ist.
   >[!NOTE]
   >
   >Wenn Sie einen Ordner auswählen und auf der Seite „Suchergebnisse“ auf **[!UICONTROL Veröffentlichen]** klicken, zeigt [!DNL Experience Manager Assets] unabhängig von den Einstellungen für den [!DNL Dynamic Media]-Veröffentlichungsmodus für den Ordner eine Option zum Veröffentlichen von Assets in [!DNL AEM] und nicht in [!DNL Dynamic Media] an.

## Überprüfen des Veröffentlichungsstatus {#check-publish-status}

So überprüfen Sie den Veröffentlichungsstatus für ein Asset oder einen Ordner:

1. Klicken Sie im Abschnitt **[!UICONTROL Assets-Verwaltung]** im linken Bereich auf **[!UICONTROL Assets]**.
2. Wechseln Sie mit dem Anzeigeumschalter zur Listenansicht. Sie können Asset-Eigenschaften wie [!UICONTROL AEM-Veröffentlichung], [!UICONTROL Dynamic Media-Veröffentlichung], [!UICONTROL Titel], [!UICONTROL Größe], [!UICONTROL Dimensionen] usw. anzeigen.\
   Wenn ein Asset oder Ordner nicht veröffentlicht wurde, wird für die Spalten **[!UICONTROL AEM-Veröffentlichung]** und **[!UICONTROL Dynamic Media-Veröffentlichung]** der Status **[!UICONTROL N/A]** angezeigt.
   ![Überprüfen des Veröffentlichungsstatus 1](/help/assets/assets/check-publish-status1.png)
Gehen Sie wie folgt vor, wenn die Spalten „[!DNL AEM]-Veröffentlichung“ und „[!DNL Dynamic Media]-Veröffentlichung“ nicht in der Listenansicht zu sehen sind:
   1. Klicken Sie auf ![Einstellungen](/help/assets/assets/settings-icon.svg) und wählen Sie im Dialogfeld **[!UICONTROL Konfigurierbare Spalten]** die Option **[!UICONTROL Dynamic Media-Veröffentlichung]** und **[!UICONTROL AEM-Veröffentlichung]** aus.
   2. Klicken Sie auf **[!UICONTROL Bestätigen]**. [!DNL Experience Manager Assets] fügt der Listenansicht die ausgewählten Spalten hinzu.

      ![Überprüfen des Veröffentlichungsstatus 2](/help/assets/assets/check-publish-status2.png)

Sie können den Veröffentlichungsstatus eines Assets auch überprüfen, indem Sie ein Asset auswählen und auf **[!UICONTROL Details]** klicken. Die Details sind im Abschnitt **[!UICONTROL Veröffentlichen]** im rechten Bereich verfügbar. Im Abschnitt **[!UICONTROL Veröffentlichen]** wird das Datum aufgelistet, zu dem die Assets in [!DNL Dynamic Media] und [!DNL AEM] veröffentlicht werden. Wenn Sie den Zeitpunkt der Asset-Veröffentlichung anzeigen möchten, können Sie zur Listenansicht navigieren und diese Details aufrufen.

![Überprüfen des Veröffentlichungsstatus 3](/help/assets/assets/check-publish-status3.png)

## Einschränkungen {#limitations}

Die folgenden Funktionen sind beim Veröffentlichen von Assets in [!DNL AEM and Dynamic Media] derzeit nicht verfügbar:

* Veröffentlichen von Assets in [!DNL AEM and Dynamic Media] aus der [!DNL Asset details page].
* Visualisieren der Endpunkte, bei denen die Assets veröffentlicht werden, mithilfe des Assistenten „Quick Publish“
* Hinzufügen oder Löschen weiterer Assets im Assistenten „Quick Publish“
* Seite zum Anzeigen veröffentlichter Assets.
* Möglichkeit zum Kopieren oder Einfügen der [!DNL Dynamic Media]-URL auf Asset-Ebene (bei Veröffentlichung der Assets in [!DNL Dynamic Media]).
* Möglichkeit zum Veröffentlichen von Verweisen (Assets, Tags usw.) beim Veröffentlichen in [!DNL AEM].
* Möglichkeit zum Überschreiben des Synchronisierungsstatus von [!DNL Dynamic Media] auf Ordnerebene.
* Möglichkeit zum Überschreiben des [!DNL Dynamic Media]-Veröffentlichungsmodus auf Ordnerebene.
* Noch keine Unterstützung für „Veröffentlichung verwalten“.
