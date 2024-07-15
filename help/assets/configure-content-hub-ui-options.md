---
title: Konfigurieren der Benutzeroberfläche von Content Hub
description: Konfigurieren der Benutzeroberfläche von Content Hub
source-git-commit: 7224cca950e61bea298f246245bdb221fd8fa22e
workflow-type: tm+mt
source-wordcount: '1119'
ht-degree: 7%

---

# Konfigurieren der Benutzeroberfläche von Content Hub {#configure-content-hub-user-interface}

<!-- ![Download assets](assets/download-asset.jpg) -->
![Konfigurieren von Assets in Content Hub](assets/configure-assets.png)

Mit Experience Manager Assets können Administratoren die in der Benutzeroberfläche von Content Hub verfügbaren Optionen konfigurieren. Je nach den Konfigurationsoptionen, die von den Administratoren ausgewählt wurden, können Benutzer von Content Hub Felder in Content Hub anzeigen. Zu den Konfigurationsoptionen gehören:

* Für Benutzer bei der Suche nach Assets verfügbare Filter.

* Asset-Details oder Eigenschaften, die für jedes Asset verfügbar sind.

* Beim Hinzufügen von Assets zu Content Hub verfügbare Metadatenfelder.

* Asset-Metadatenfelder, die für die Suche in Content Hub verfügbar sind.

* Branding von Inhalten, die Sie für Ihre Organisation anzeigen müssen.

* Alle benutzerspezifischen Links, die Sie zusätzlich zu Assets, Sammlungen und Einblicken in Content Hub hinzufügen müssen.

## Voraussetzungen {#prerequisites-configuration-ui}

[Content Hub-Administratoren](/help/assets/deploy-content-hub.md#step-3-onboard-content-hub-administrator) können die Konfigurationsoptionen für andere Benutzer in Ihrer Organisation festlegen.

## Auf Konfigurationsoptionen in Content Hub zugreifen {#access-configuration-options-content-hub}

So greifen Sie auf Konfigurationsoptionen in Content Hub zu:

1. Klicken Sie auf das Benutzersymbol im rechten Bereich.

1. Wählen Sie im Abschnitt **[!UICONTROL Produkteinstellungen]** die Option **[!UICONTROL Konfigurationen]** aus.

   ![Auf Konfigurationsoptionen in Content Hub zugreifen](assets/access-content-hub-configuration-ui.png)

## Konfigurationsoptionen in Content Hub verwalten {#manage-configuration-options}

Verwalten Sie die folgenden Konfigurationsoptionen für Ihre Benutzer:

* [Importieren](#configure-import-options-content-hub)

* [Filter](#configure-filters-content-hub)

* [Asset-Details](#configure-asset-details-content-hub)

* [Suchen](#configure-metadata-search-content-hub)

* [Branding](#configure-branding-content-hub)

* [Benutzerspezifische Links](#configure-custom-links-content-hub)

### Importieren {#configure-import-options-content-hub}

Sie können die Metadatenfelder konfigurieren, die den Benutzern beim Hochladen oder Importieren von Assets in das Content Hub-Portal angezeigt werden, z. B. Kampagnenname, Keywords, Kanäle, Zeitrahmen, Region usw. Führen Sie dazu die folgenden Schritte aus:

1. Klicken Sie in der Benutzeroberfläche von [Konfigurationen](#access-configuration-options-content-hub) auf **[!UICONTROL Importieren]**.

1. Klicken Sie auf **[!UICONTROL Metadaten hinzufügen]**.

1. Geben Sie eine Beschriftung für die Eigenschaft an, ordnen Sie sie mithilfe des Felds **[!UICONTROL Metadaten]** einer Eigenschaft zu und wählen Sie den Eingabetyp für die neuen Asset-Metadaten aus.

1. Klicken Sie auf den Umschalter **[!UICONTROL Erforderliches Feld]** , um das neue Metadatenfeld als obligatorisch festzulegen, das beim Hochladen neuer Assets für Benutzer angegeben werden soll.

1. Klicken Sie auf **[!UICONTROL Bestätigen]**. Die neuen Metadaten werden in der Liste der vorhandenen Asset-Eigenschaften angezeigt.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

Auf ähnliche Weise können Sie auf das Symbol ![Bearbeiten](assets/do-not-localize/edit_icon.svg) klicken, das neben jeder verfügbaren Eigenschaft verfügbar ist, um die Beschriftungen zu bearbeiten, diese Felder für Benutzer beim Hochladen von Assets mit dem Umschalter **[!UICONTROL Erforderliches Feld]** als obligatorisch oder für Benutzer als nicht obligatorisch zu kennzeichnen oder auf das Symbol Löschen , um eine Metadateneigenschaft zu löschen.

Klicken Sie auf den Umschalter **[!UICONTROL Automatische Genehmigung]** , wenn alle Assets, die Sie zum Experience Manager Assets-Repository hinzufügen, automatisch genehmigt werden müssen, damit sie in Content Hub sofort verfügbar sind. Andernfalls müssen DAM-Autoren oder -Administratoren die Assets manuell genehmigen, damit sie in Content Hub verfügbar sind. Der Umschalter ist standardmäßig auf den Status Aus eingestellt.

Klicken Sie auf **[!UICONTROL Speichern]** , nachdem Sie alle Änderungen vorgenommen haben, um die Änderungen anzuwenden.

![Upload-Details der Konfigurationsoberfläche auf Content Hub](assets/configuration-ui-upload-details.png)

Auf der Konfigurationsoberfläche aktivierte Metadaten werden auf der Asset-Upload-Seite angezeigt:

![Hochladen von Metadaten auf Content Hub](assets/configuration-ui-add-assets.png)

### Filter {#configure-filters-content-hub}

Mit Content Hub können Administratoren Filter konfigurieren, die bei der Suche nach Assets angezeigt werden. Führen Sie die folgenden Schritte aus, um einen neuen Filter hinzuzufügen:

1. Klicken Sie in der Benutzeroberfläche von [Konfigurationen](#access-configuration-options-content-hub) auf **[!UICONTROL Filter]**.

1. Klicken Sie auf **[!UICONTROL Filter hinzufügen]**.

1. Geben Sie einen Titel für den Filter an, ordnen Sie ihn mithilfe des Felds **[!UICONTROL Metadaten]** einer Eigenschaft zu und wählen Sie den Eingabetyp für den neuen Filter aus.
1. Klicken Sie auf **[!UICONTROL Bestätigen]**. Der neue Filter wird in der Liste der vorhandenen Filter angezeigt.

1. Klicken Sie auf **[!UICONTROL Speichern]** , um die Änderungen anzuwenden, sodass der neue Filter beim Filtern von Assets auf der Suchseite angezeigt wird.

   >[!NOTE]
   >
   >Der neue Filter wird nur dann auf der Suchseite angezeigt, wenn im Repository mindestens ein Asset vorhanden ist, das den Filterkriterien entspricht.

Auf ähnliche Weise können Sie auf das neben jedem verfügbaren Filter verfügbare Symbol ![Bearbeiten](assets/do-not-localize/edit_icon.svg) klicken, um die Beschriftungen zu bearbeiten, oder auf das Löschsymbol klicken, um einen vorhandenen Filter zu löschen. Klicken Sie auf **[!UICONTROL Speichern]** , nachdem Sie alle Änderungen vorgenommen haben, um die Änderungen anzuwenden.

![Filter der Konfigurationsoberfläche für Content Hub](assets/configuration-ui-filters.png)

Die auf der Konfigurationsoberfläche aktivierten Filter werden auf der Suchseite angezeigt:

![Suchen in Content Hub](assets/filters-for-search.png)


### Asset-Details {#configure-asset-details-content-hub}

Sie können auch die Asset-Eigenschaften konfigurieren, die für jedes Asset angezeigt werden, z. B. Dateiname, Titel, Format, Größe usw. Führen Sie dazu die folgenden Schritte aus:

1. Klicken Sie in der Benutzeroberfläche von [Konfigurationen](#access-configuration-options-content-hub) auf **[!UICONTROL Asset-Details]**.

1. Klicken Sie auf **[!UICONTROL Metadaten hinzufügen]**.

1. Geben Sie eine Beschriftung für die Eigenschaft an, ordnen Sie sie mithilfe des Felds **[!UICONTROL Metadaten]** einer Eigenschaft zu und wählen Sie den Eingabetyp für die neuen Asset-Metadaten aus.
1. Klicken Sie auf **[!UICONTROL Bestätigen]**. Die neuen Metadaten werden in der Liste der vorhandenen Asset-Eigenschaften angezeigt.

1. Klicken Sie auf **[!UICONTROL Speichern]** , um die Änderungen anzuwenden, sodass die neue Eigenschaft auf der Asset-Detailseite angezeigt wird.

Auf ähnliche Weise können Sie auf das Symbol ![Bearbeiten](assets/do-not-localize/edit_icon.svg) klicken, das neben jeder verfügbaren Eigenschaft verfügbar ist, um die Beschriftungen zu bearbeiten, oder auf das Löschsymbol klicken, um vorhandene Asset-Details zu löschen. Klicken Sie auf **[!UICONTROL Speichern]** , nachdem Sie alle Änderungen vorgenommen haben, um die Änderungen anzuwenden.

![Asset-Details der Konfigurationsoberfläche in Content Hub](assets/configuration-ui-asset-details.png)

Die auf der Konfigurationsoberfläche aktivierten Eigenschaften werden auf der Seite &quot;Asset-Details&quot;angezeigt:

![Asset-Eigenschaften in Content Hub](assets/config-ui-asset-properties.png)

### Suchen {#configure-metadata-search-content-hub}

Administratoren können die Metadatenfelder definieren, die durchsucht werden, wenn ein Benutzer in Content Hub Suchkriterien angibt. Führen Sie die folgenden Schritte aus:

1. Klicken Sie in der Benutzeroberfläche von [Konfigurationen](#access-configuration-options-content-hub) auf **[!UICONTROL Metadaten hinzufügen]**.

1. Geben Sie das Metadatenfeld an und klicken Sie auf **[!UICONTROL Bestätigen]**.

1. Klicken Sie auf **[!UICONTROL Speichern]** , um die Änderungen anzuwenden und die neue Metadateneigenschaft in der Liste der Metadatenfelder anzuzeigen.

Auf ähnliche Weise können Sie auf das Symbol ![Bearbeiten](assets/do-not-localize/edit_icon.svg) klicken, das neben jeder verfügbaren Metadateneigenschaft verfügbar ist, um die Eigenschaft zu bearbeiten, oder auf das Löschsymbol klicken, um eine vorhandene Eigenschaft zu löschen. Klicken Sie auf **[!UICONTROL Speichern]** , nachdem Sie alle Änderungen vorgenommen haben, um die Änderungen anzuwenden.

![Konfigurations-UI-Suche in Content Hub](assets/configuration-ui-metadata-search.png)


### Branding {#configure-branding-content-hub}

Administratoren können auch den Titel und den Textkörper im Banner des Content Hub-Portals entsprechend Ihren Branding-Anforderungen personalisieren. Führen Sie dazu die folgenden Schritte aus:

1. Klicken Sie in der Benutzeroberfläche von [Konfigurationen](#access-configuration-options-content-hub) auf **[!UICONTROL Branding]**.

1. Geben Sie Text in den Feldern **[!UICONTROL Titeltext im Banner]** und **[!UICONTROL Textkörper im Banner]** an.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

![Branding der Konfigurationsoberfläche auf Content Hub](assets/configuration-ui-branding.png)

Die auf der Konfigurationsoberfläche aktivierten Branding-Aktualisierungen werden im Content Hub-Portal-Banner angezeigt:

![Branding der Konfigurationsoberfläche auf Content Hub](assets/configuration-ui-branding-updates.png)

### Benutzerspezifische Links {#configure-custom-links-content-hub}

Zusätzlich zu den Standardregisterkarten **[!UICONTROL Alle Assets]**, **[!UICONTROL Sammlungen]** und **[!UICONTROL Insights]** im Content Hub-Portal direkt unterhalb des Banners können Sie auch benutzerdefinierte Registerkarten hinzufügen. Führen Sie dazu die folgenden Schritte aus:

1. Klicken Sie in der Benutzeroberfläche von [Konfigurationen](#access-configuration-options-content-hub) auf **[!UICONTROL Benutzerspezifische Links]**.

1. Klicken Sie auf **[!UICONTROL Link hinzufügen]**.

1. Geben Sie Text in den Feldern **[!UICONTROL Beschriftung]** und **[!UICONTROL URL]** an. Die von Ihnen definierte Beschriftung wird als Registerkarte angezeigt. Wenn Sie auf die Beschriftung klicken, navigieren Sie zu der im Feld **[!UICONTROL URL]** definierten URL.

1. Klicken Sie auf **[!UICONTROL Bestätigen]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

Auf ähnliche Weise können Sie auf das neben jeder URL verfügbare Symbol ![Bearbeiten](assets/do-not-localize/edit_icon.svg) klicken, um die Links zu bearbeiten, oder auf das Löschsymbol klicken, um eine vorhandene URL zu löschen. Klicken Sie auf **[!UICONTROL Speichern]** , nachdem Sie alle Änderungen vorgenommen haben, um die Änderungen anzuwenden.

![Benutzerdefinierte Links der Konfigurationsoberfläche für Content Hub](assets/configuration-ui-custom-links.png)

Der benutzerspezifische Link wird auf der Content Hub-Startseite neben der Registerkarte Einblicke als neue Registerkarte angezeigt.

![Registerkarte &quot;Benutzerspezifische Links&quot;der Konfigurationsoberfläche in Content Hub](assets/configuration-ui-custom-link-tab.png)


