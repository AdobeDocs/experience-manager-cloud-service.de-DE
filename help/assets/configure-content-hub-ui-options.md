---
title: Benutzeroberfläche von Content Hub konfigurieren
description: Benutzeroberfläche von Content Hub konfigurieren
source-git-commit: 5a968440c8841abe7af2c81c4af12258b7e4547f
workflow-type: tm+mt
source-wordcount: '1096'
ht-degree: 6%

---

# Benutzeroberfläche von Content Hub konfigurieren {#configure-content-hub-user-interface}

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

[Content Hub-Administratoren](/help/assets/deploy-content-hub.md#step-3-onboard-content-hub-administrator) kann die Konfigurationsoptionen für andere Benutzer in Ihrer Organisation festlegen.

## Auf Konfigurationsoptionen in Content Hub zugreifen {#access-configuration-options-content-hub}

So greifen Sie auf Konfigurationsoptionen in Content Hub zu:

1. Klicken Sie auf das Benutzersymbol im rechten Bereich.

1. Im **[!UICONTROL Produkteinstellungen]** Bereich, wählen Sie **[!UICONTROL Konfigurationen]**.

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

1. Im [Konfigurationen](#access-configuration-options-content-hub) Benutzeroberfläche, klicken Sie auf **[!UICONTROL Import]**.

1. Klicks **[!UICONTROL Hinzufügen von Metadaten]**.

1. Geben Sie eine Beschriftung für die Eigenschaft an und ordnen Sie sie mithilfe der **[!UICONTROL Metadaten]** und wählen Sie den Eingabetyp für die neuen Asset-Metadaten aus.

1. Klicken Sie auf **[!UICONTROL Erforderliches Feld]** Umschalten, um das neue Metadatenfeld als obligatorisch festzulegen, das für Benutzer beim Hochladen neuer Assets angegeben wird.

1. Klicks **[!UICONTROL Bestätigen]**. Die neuen Metadaten werden in der Liste der vorhandenen Asset-Eigenschaften angezeigt.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

Auf ähnliche Weise können Sie ![Symbol Bearbeiten](assets/do-not-localize/edit_icon.svg), verfügbar neben jeder verfügbaren Eigenschaft, um die Beschriftungen zu bearbeiten, müssen Sie diese Felder für Benutzer beim Hochladen von Assets mit dem **[!UICONTROL Erforderliches Feld]** ein- oder klicken Sie auf das Symbol Löschen , um eine Metadateneigenschaft zu löschen.

Klicken Sie auf **[!UICONTROL Automatische Genehmigung]** umschalten, wenn alle Assets, die Sie zum Experience Manager Assets-Repository hinzufügen, automatisch genehmigt werden müssen, damit sie sofort in Content Hub verfügbar sind. Andernfalls müssen DAM-Autoren oder -Administratoren die Assets manuell genehmigen, damit sie in Content Hub verfügbar sind. Der Umschalter ist standardmäßig auf den Status Aus eingestellt.

Klicks **[!UICONTROL Speichern]** nach Durchführung aller Änderungen, um die Änderungen anzuwenden.

![Upload-Details der Konfigurationsoberfläche in Content Hub](assets/configuration-ui-upload-details.png)

Auf der Konfigurationsoberfläche aktivierte Metadaten werden auf der Asset-Upload-Seite angezeigt:

![Hochladen von Metadaten in Content Hub](assets/configuration-ui-add-assets.png)

### Filter {#configure-filters-content-hub}

Mit Content Hub können Administratoren Filter konfigurieren, die bei der Suche nach Assets angezeigt werden. Führen Sie die folgenden Schritte aus, um einen neuen Filter hinzuzufügen:

1. Im [Konfigurationen](#access-configuration-options-content-hub) Benutzeroberfläche, klicken Sie auf **[!UICONTROL Filter]**.

1. Klicks **[!UICONTROL Filter hinzufügen]**.

1. Geben Sie eine Bezeichnung für den Filter an und ordnen Sie ihn mithilfe der **[!UICONTROL Metadaten]** und wählen Sie den Eingabetyp für den neuen Filter aus.
1. Klicks **[!UICONTROL Bestätigen]**. Der neue Filter wird in der Liste der vorhandenen Filter angezeigt.

1. Klicks **[!UICONTROL Speichern]** , um die Änderungen so anzuwenden, dass der neue Filter beim Filtern von Assets auf der Suchseite angezeigt wird.

Auf ähnliche Weise können Sie ![Symbol Bearbeiten](assets/do-not-localize/edit_icon.svg), der neben jedem verfügbaren Filter verfügbar ist, um die Beschriftungen zu bearbeiten, oder klicken Sie auf das Löschsymbol, um einen vorhandenen Filter zu löschen. Klicks **[!UICONTROL Speichern]** nach Durchführung aller Änderungen, um die Änderungen anzuwenden.

![Filter der Konfigurationsoberfläche in Content Hub](assets/configuration-ui-filters.png)

Die auf der Konfigurationsoberfläche aktivierten Filter werden auf der Suchseite angezeigt:

![Suchen in Content Hub](assets/filters-for-search.png)


### Asset-Details {#configure-asset-details-content-hub}

Sie können auch die Asset-Eigenschaften konfigurieren, die für jedes Asset angezeigt werden, z. B. Dateiname, Titel, Format, Größe usw. Führen Sie dazu die folgenden Schritte aus:

1. Im [Konfigurationen](#access-configuration-options-content-hub) Benutzeroberfläche, klicken Sie auf **[!UICONTROL Asset-Details]**.

1. Klicks **[!UICONTROL Hinzufügen von Metadaten]**.

1. Geben Sie eine Beschriftung für die Eigenschaft an und ordnen Sie sie mithilfe der **[!UICONTROL Metadaten]** und wählen Sie den Eingabetyp für die neuen Asset-Metadaten aus.
1. Klicks **[!UICONTROL Bestätigen]**. Die neuen Metadaten werden in der Liste der vorhandenen Asset-Eigenschaften angezeigt.

1. Klicks **[!UICONTROL Speichern]** , um die Änderungen so anzuwenden, dass die neue Eigenschaft auf der Seite mit den Asset-Details angezeigt wird.

Auf ähnliche Weise können Sie ![Symbol Bearbeiten](assets/do-not-localize/edit_icon.svg), verfügbar neben jeder verfügbaren Eigenschaft, um die Beschriftungen zu bearbeiten, oder klicken Sie auf das Löschsymbol, um vorhandene Asset-Details zu löschen. Klicks **[!UICONTROL Speichern]** nach Durchführung aller Änderungen, um die Änderungen anzuwenden.

![Asset-Details der Konfigurationsoberfläche in Content Hub](assets/configuration-ui-asset-details.png)

Die auf der Konfigurationsoberfläche aktivierten Eigenschaften werden auf der Seite &quot;Asset-Details&quot;angezeigt:

![Asset-Eigenschaften in Content Hub](assets/config-ui-asset-properties.png)

### Suchen {#configure-metadata-search-content-hub}

Administratoren können die Metadatenfelder definieren, die durchsucht werden, wenn ein Benutzer in Content Hub Suchkriterien angibt. Führen Sie die folgenden Schritte aus:

1. Im [Konfigurationen](#access-configuration-options-content-hub) Benutzeroberfläche, klicken Sie auf **[!UICONTROL Hinzufügen von Metadaten]**.

1. Geben Sie das Metadatenfeld an und klicken Sie auf **[!UICONTROL Bestätigen]**.

1. Klicks **[!UICONTROL Speichern]** , um die Änderungen so anzuwenden, dass die neue Metadateneigenschaft in der Liste der Metadatenfelder angezeigt wird.

Auf ähnliche Weise können Sie ![Symbol Bearbeiten](assets/do-not-localize/edit_icon.svg), verfügbar neben jeder verfügbaren Metadateneigenschaft, um die Eigenschaft zu bearbeiten, oder klicken Sie auf das Löschsymbol, um eine vorhandene Eigenschaft zu löschen. Klicks **[!UICONTROL Speichern]** nach Durchführung aller Änderungen, um die Änderungen anzuwenden.

![Benutzeroberfläche für Konfiguration - Suche in Content Hub](assets/configuration-ui-metadata-search.png)


### Branding {#configure-branding-content-hub}

Administratoren können auch den Titel und den Textkörper im Banner des Content Hub-Portals entsprechend Ihren Branding-Anforderungen personalisieren. Führen Sie dazu die folgenden Schritte aus:

1. Im [Konfigurationen](#access-configuration-options-content-hub) Benutzeroberfläche, klicken Sie auf **[!UICONTROL Branding]**.

1. Text angeben in **[!UICONTROL Titeltext im Banner]** und **[!UICONTROL Textkörper im Banner]** -Felder.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

![Branding der Konfigurationsoberfläche in Content Hub](assets/configuration-ui-branding.png)

Die auf der Konfigurationsoberfläche aktivierten Branding-Aktualisierungen werden im Content Hub-Portal-Banner angezeigt:

![Branding der Konfigurationsoberfläche in Content Hub](assets/configuration-ui-branding-updates.png)

### Benutzerspezifische Links {#configure-custom-links-content-hub}

Zusätzlich zu den Standardregisterkarten können Sie auch benutzerdefinierte Registerkarten hinzufügen **[!UICONTROL Alle Assets]**, **[!UICONTROL Sammlungen]**, und **[!UICONTROL Insights]** Registerkarten im Content Hub-Portal direkt unter dem Banner. Führen Sie dazu die folgenden Schritte aus:

1. Im [Konfigurationen](#access-configuration-options-content-hub) Benutzeroberfläche, klicken Sie auf **[!UICONTROL Benutzerspezifische Links]**.

1. Klicks **[!UICONTROL Link hinzufügen]**.

1. Text angeben in **[!UICONTROL Titel]** und **[!UICONTROL URL]** -Felder. Der Titel, den Sie definieren, wird als Tab angezeigt. Wenn Sie auf den Titel klicken, navigieren Sie zu der URL, die in der Variablen **[!UICONTROL URL]** -Feld.

1. Klicken Sie auf **[!UICONTROL Bestätigen]**.

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Änderungen zu speichern.

Auf ähnliche Weise können Sie ![Symbol Bearbeiten](assets/do-not-localize/edit_icon.svg), verfügbar neben jeder URL, um die Links zu bearbeiten, oder klicken Sie auf das Löschsymbol, um eine vorhandene URL zu löschen. Klicks **[!UICONTROL Speichern]** nach Durchführung aller Änderungen, um die Änderungen anzuwenden.

![Benutzerdefinierte Links in der Konfigurationsoberfläche für Content Hub](assets/configuration-ui-custom-links.png)

Der benutzerspezifische Link wird auf der Content Hub-Startseite neben der Registerkarte Einblicke als neue Registerkarte angezeigt.

![Registerkarten der Konfigurationsoberfläche für benutzerdefinierte Links in Content Hub](assets/configuration-ui-custom-link-tab.png)


