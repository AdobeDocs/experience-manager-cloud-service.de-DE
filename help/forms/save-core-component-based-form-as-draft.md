---
title: Wie speichern Sie das auf Kernkomponenten basierende adaptive Formular als Entwurf und verwenden Sie die Komponente "Drafts and Submissions", um Entwürfe und Übermittlungen aufzulisten?
description: Erfahren Sie, wie Sie Kernkomponenten-basierte adaptive Formulare als Entwurf speichern. Erfahren Sie außerdem, wie Sie mit der Komponente "Drafts and Submissions"Entwürfe und Übermittlungen für angemeldete Benutzer auflisten können.
feature: Adaptive Forms, Core Components
exl-id: c0653bef-afeb-40c1-b131-7d87ca5542bc
role: User, Developer
source-git-commit: 2e4c9a7d30b954045082baf242737ac2f7426c70
workflow-type: tm+mt
source-wordcount: '1387'
ht-degree: 16%

---


# Speichern von Formularen als Entwürfe und Auflisten dieser Formulare auf der Sites-Seite

<span class="preview"> Dieser Artikel enthält Inhalte zur Funktion **Entwürfe**, einer Vorabveröffentlichungsfunktion. Die Vorabveröffentlichungsfunktion ist nur über unseren [Vorabveröffentlichungskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features) zugänglich.</span>

Betrachten Sie einen Benutzer, der mit dem Ausfüllen eines Formulars beginnt, aber anhalten und später zurückkehren muss. AEM bietet die Option &quot;`save-as-draft`&quot;, mit der der Benutzer das Formular als Entwurf speichern kann, der später fertig gestellt werden kann. Um dies zu erleichtern, stellt AEM die Komponente **Entwürfe und Übermittlungen** Formularportal standardmäßig bereit, die Entwürfe und Übermittlungen auf AEM Sites-Seiten anzeigt. Die Komponente listet Formulare auf, die als Entwürfe zum späteren Abschluss gespeichert wurden, sowie die gesendeten Formulare. Nur angemeldete Benutzer können ihre Entwürfe bearbeiten oder die übermittelten Formulare anzeigen. Wenn jedoch ein anonymer Benutzer mithilfe der Komponente **Search &amp; Lister** durch die Liste der Formulare navigiert und ein Formular als Entwurf speichert, wird dieser Entwurf nicht von der Komponente **Entwürfe &amp; Sendungen** aufgeführt. Um Entwürfe und Übermittlungen anzuzeigen, müssen Benutzer zum Zeitpunkt der Formularübermittlung angemeldet sein.

![Symbol für Entwürfe](assets/drafts-component.png)

## Voraussetzungen

* [Aktivieren Sie die adaptiven Forms-Kernkomponenten für Ihre Umgebung.](/help/forms/enable-adaptive-forms-core-components.md)

  Nach der Bereitstellung der neuesten Kernkomponenten in Ihrer Umgebung können Sie auf die Formularportal-Komponenten in Ihrer Authoring-Umgebung zugreifen.

* [Konfigurieren der Forms Portal-Komponente &quot;Azure Storage and Unified Storage Connector for Drafts &amp; Submissions](#configure-azure-storage-and-unified-storage-connector-for-drafts--submissions-forms-portal-component)

### Konfigurieren der Forms Portal-Komponente &quot;Azure Storage and Unified Storage Connector for Drafts &amp; Submissions

Die Komponente **Entwürfe und Übermittlungen** benötigt eine Speichereinrichtung zum Speichern und Auflisten von Entwürfen auf der AEM Sites-Seite. Unified Storage Connector bietet ein Framework zur Verknüpfung von AEM mit externem Speicher. Um das Formular als Entwurf zu speichern, stellen Sie sicher, dass Sie über ein Azure-Speicherkonto und einen Zugriffsschlüssel verfügen, um den Zugriff auf das Speicherkonto [!DNL Azure] zu autorisieren. Sobald Sie über ein Azure Storage-Konto und den Zugriffsschlüssel verfügen, führen Sie die folgenden Schritte aus, um eine Azure Storage-Konfiguration zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure-Speicher]**.

   ![Auswahl der Azure Storage Card](/help/forms/assets/save-form-as-draft-azure-card.png)

1. Wählen Sie einen Konfigurationsordner aus, um die Konfiguration zu erstellen, und wählen Sie **[!UICONTROL Erstellen]** aus.

   ![Wählen Sie den Azure Storage Configuration Folder](/help/forms/assets/save-form-as-draft-select-config-folder.png) aus.

1. Geben Sie im Feld **[!UICONTROL Titel]** einen Titel für die Konfiguration an.
1. Geben Sie den Namen des Speicherkontos [!DNL Azure] in den Feldern **[!UICONTROL Azure Storage Account]** und **[!UICONTROL Azure Access Key]** an.

   ![Azure Storage-Konfiguration](/help/forms/assets/save-form-as-draft-azure-storage.png)

   Geben Sie `Connection String` in das Textfeld `Azure Storage Account` und `Azure Key` in das Textfeld `Azure Access key` ein.

1. Klicken Sie auf **Speichern**.

   >[!NOTE]
   >
   > Sie können das **[!UICONTROL Azure Storage Account]** und den **[!UICONTROL Azure Access Key]** aus dem [Microsoft Azure Portal](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal) abrufen.

   Nachdem Sie die Azure Storage-Konfiguration erfolgreich erstellt haben, konfigurieren Sie den Unified Storage Connector für Forms Portal wie folgt:

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]**.

   ![Einheitlicher Connector-Speicher](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. Wählen Sie im Abschnitt **[!UICONTROL Formularportal]** den Eintrag **[!UICONTROL Azure]** aus der Dropdown-Liste **[!UICONTROL Speicher]** aus.
1. Geben Sie den Konfigurationspfad für die Azure-Speicherkonfiguration im Feld **[!UICONTROL Speicherkonfigurationspfad]** an.

   ![Einstellung für den einheitlichen Connector-Speicher](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus.

>[!NOTE]
>
> Wenn Sie eine andere Speicheroption als Azure konfigurieren müssen, schreiben Sie von Ihrer offiziellen E-Mail-Adresse an aem-forms-ea@adobe.com mit Ihren detaillierten Anforderungen.

Nachdem Sie Azure Storage und Unified Storage Connector zum Speichern der Entwürfe und gesendeten Formulare erfolgreich konfiguriert haben, fügen Sie die Komponente **Entwürfe und Übermittlungen** auf der AEM Sites-Seite hinzu.

## Wie wird die Komponente &quot;Drafts &amp; Submissions&quot;zu einer AEM Sites-Seite hinzugefügt?

Sie können vordefinierte Forms Portal-Komponenten verwenden, um Entwürfe und Übermittlungen auf der Sites-Seite aufzulisten. Führen Sie die folgenden Schritte aus, um die Portalkomponente **Entwürfe und Übermittlungen** hinzuzufügen:

1. Öffnen Sie die AEM Sites-Seite in einem **Bearbeitungsmodus**.
1. Navigieren Sie zu **[!UICONTROL Seiteninformationen]** > **[!UICONTROL Vorlage bearbeiten]**
   ![Richtlinie zum Bearbeiten von Vorlagen](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Klicken Sie auf das Kontrollkästchen **[!UICONTROL Richtlinie]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Entwürfe &amp; Sendungen]** unter dem AEM **[Projektnamen des Archetyps] - Forms und Kommunikationsportal**.

   ![Auswählen von Richtlinien](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.
1. Öffnen Sie jetzt die AEM Sites-Seite im Authoring-Modus erneut.
1. Suchen Sie im Seiteneditor nach dem Abschnitt, in dem Sie die Formularportal-Komponente hinzufügen können.
1. Klicken Sie auf das Symbol **Hinzufügen**. Das Symbol ist ein Pluszeichen (+). Es steht für die Option zum Hinzufügen neuer Komponenten.

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt, in dem verschiedene Komponenten zum Einfügen angezeigt werden.

   >[!NOTE]
   >
   > Alternativ können Sie die Komponente auch per Drag-and-Drop hinzufügen.

1. Durchsuchen Sie die verfügbaren Komponenten im Dialogfeld und wählen Sie die gewünschte Komponente aus der Liste aus. Wählen Sie beispielsweise die Komponente **Entwürfe &amp; Übermittlungen** aus der Liste aus, um die Komponente **Entwürfe &amp; Übermittlungen** Forms Portal hinzuzufügen.

   ![Komponente &quot;Entwurf und Übermittlung hinzufügen&quot;](/help/forms/assets/save-form-as-draft-add-dns.png)

Konfigurieren Sie nun die Eigenschaften der Komponente **Entwürfe und Übermittlungen** entsprechend den Anforderungen.

## Eigenschaften der Komponente &quot;Drafts and Submissions&quot;konfigurieren

Sie können die Eigenschaften von **Entwürfen und Übermittlungen** konfigurieren:
1. Wählen Sie die Komponente **Entwürfe &amp; Sendungen** aus.
1. Klicken Sie auf das Symbol ![Konfigurieren](assets/configure_icon.png) und das Dialogfeld wird angezeigt.
1. Geben Sie im Dialogfeld **[!UICONTROL Entwürfe und Übermittlungen]** Folgendes an:
   * **Titel** Um eine Komponente auf einer Sites-Seite zu identifizieren, wird standardmäßig der Titel über der Komponente angezeigt.
   * **Typ auswählen**: Damit wird die Formularliste als Entwurf oder übermittelte Formulare angegeben. Wenn Sie &quot;**Entwurf Forms**&quot;auswählen, werden die als Entwürfe gespeicherten Formulare angezeigt. Wenn Sie alternativ &quot;**Gesendet Forms**&quot;auswählen, werden die Formulare angezeigt, die von angemeldeten Benutzern gesendet wurden.
   * **Layout**: Zum Anzeigen von Listenentwurfsformularen oder gesendeten Formularen im Karten- oder Listenformat.

   ![Eigenschaften der Entwurfs- und Übermittlungskomponente](/help/forms/assets/save-form-as-draft-dns-properties.png)

## Konfigurieren von Formularen zum Speichern als Entwürfe

Sie können Adaptive Forms auf zwei Arten konfigurieren, um sie als Entwürfe zur späteren Verwendung zu speichern:
* [Benutzeraktion](#user-action)
* [Automatisches Speichern](#auto-save)

### Benutzeraktion

>[!NOTE]
>
> Stellen Sie sicher, dass die [Kernkomponentenversion auf 3.0.24 oder höher](https://github.com/adobe/aem-core-forms-components) festgelegt ist, um Formulare mithilfe der Regel **Formular speichern** als Entwürfe zu speichern.

Um ein Formular als Entwurf zu speichern, erstellen Sie eine Regel **Formular speichern** für eine Formularkomponente, z. B. eine Schaltfläche. Wenn auf die Schaltfläche geklickt wird, wird der Trigger der Regel und das Formular als Entwurf gespeichert. Führen Sie die folgenden Schritte aus, um eine **Formular speichern** -Regel für eine Schaltflächenkomponente zu erstellen:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.
1. Wählen Sie das Symbol **[!UICONTROL Regeln bearbeiten]** aus, um den Regeleditor für die Komponente **Schaltfläche** zu öffnen.
1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Regel für die Schaltfläche zu konfigurieren und zu erstellen.
1. Wählen Sie im Abschnitt **[!UICONTROL Wenn]** die Option **ist geklickt** und wählen Sie im Abschnitt **[!UICONTROL Dann]** die Option **Formular speichern** aus.
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.

   ![Regel für Schaltfläche erstellen](/help/forms/assets/save-form-as-drfat-create-rule.png)

Wenn Sie ein adaptives Formular in der Vorschau anzeigen, ausfüllen und auf die Schaltfläche **Formular speichern** klicken, wird das Formular als Entwurf gespeichert.

### Entwürfe

>[!NOTE]
>
> Stellen Sie sicher, dass die [Kernkomponentenversion auf 3.0.52 oder höher](https://github.com/adobe/aem-core-forms-components) festgelegt ist, um Formulare mit der Funktion &quot;Automatisches Speichern&quot;als Entwürfe zu speichern.

Sie können auch ein adaptives Formular so konfigurieren, dass es basierend auf einem zeitbasierten Ereignis automatisch gespeichert wird. So können Sie sicherstellen, dass das Formular nach der festgelegten Dauer gespeichert wird. Wenn Sie [Forms Portal-Komponenten für Ihre Umgebung aktivieren](/help/forms/list-forms-on-sites-page.md#enable-forms-portal-components-for-your-existing-environment), wird die Registerkarte **Automatisches Speichern** in den Eigenschaften des Forms-Containers angezeigt. Sie können die Funktion zum automatischen Speichern für ein adaptives Formular konfigurieren:

1. Öffnen Sie in der Autoreninstanz ein adaptives Formular im Bearbeitungsmodus.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol &quot;Guide Container properties ![Guide properties](/help/forms/assets/configure-icon.svg)&quot;und öffnen Sie die Registerkarte **[!UICONTROL Entwürfe]**.

   ![Automatisches Speichern](/help/forms/assets/auto-save.png)

1. Aktivieren Sie das Kontrollkästchen **[!UICONTROL Entwürfe automatisch speichern]** , um das automatische Speichern des Formulars als Entwürfe zu aktivieren.
1. Konfigurieren Sie **[!UICONTROL Voreinstellung speichern]** als **Entwürfe in regelmäßigen Abständen speichern**, um das Formular nach einem bestimmten Zeitintervall automatisch zu speichern <!--based on the occurrence of an event or-->.
1. Geben Sie das Zeitintervall in der Intervallfrequenz **[!UICONTROL Speichern (Sekunden)]** an, um die Dauer festzulegen, für die das automatische Speichern des Formulars in dem definierten Intervall Trigger wird.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Entwürfe/gesendete Formulare mithilfe der Komponente &quot;Drafts &amp; Submissions&quot;auf der Seite &quot;Sites&quot;anzeigen

Um gespeicherte Entwürfe oder gesendete Formulare anzuzeigen, verwenden Sie die Forms Portal-Komponente **Entwürfe und Übermittlungen** .
Wenn **[!UICONTROL Typ auswählen]** als **Entwurf-Forms** im Dialogfeld [Konfigurieren der Komponente &quot;Drafts &amp; Submissions&quot;ausgewählt ist, werden die als Entwürfe gespeicherten Formulare auf der Seite &quot;Sites&quot;angezeigt. ](#configure-properties-of-the-drafts--submissions-component) Sie können die Entwürfe öffnen, indem Sie auf die Auslassungspunkte (...) klicken, um das Formular auszufüllen.

![Symbol für Entwürfe](assets/drafts-component.png)

Wenn **[!UICONTROL Typ auswählen]** als **Gesendete Forms** im Dialogfeld [ &quot;Konfigurieren&quot;der Komponente &quot;Drafts &amp; Submissions&quot;ausgewählt ist, werden die gesendeten Formulare angezeigt. ](#configure-properties-of-the-drafts--submissions-component) Sie können die gesendeten Formulare anzeigen, sie jedoch nicht bearbeiten.

![Symbol für Einsendungen](assets/submission-listing.png)

Sie können die Formulare auch verwerfen, indem Sie auf die Auslassungspunkte (...) klicken, die in der rechten unteren Ecke des Formulars angezeigt werden.

## Nächste Schritte

Im nächsten Artikel erfahren Sie [wie Sie Verweise auf Formulare auf der Sites-Seite mithilfe der Komponente &quot;Link Forms Portal&quot;hinzufügen](/help/forms/add-form-link-to-aem-sites-page.md).

## Verwandte Artikel

{{forms-portal-see-also}}

## Siehe auch {#see-also}

{{see-also}}