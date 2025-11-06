---
title: So speichern Sie das auf Kernkomponenten basierende adaptive Formular als Entwurf und verwenden die Komponente „Drafts and Submissions“, um Entwürfe und Sendungen aufzulisten?
description: Erfahren Sie, wie Sie auf Kernkomponenten basierende adaptive Formulare als Entwurf speichern. Erfahren Sie außerdem, wie Sie mit der Komponente „Drafts and Submissions“ Entwürfe und Sendungen für angemeldete Benutzer auflisten können.
feature: Adaptive Forms, Core Components
exl-id: c0653bef-afeb-40c1-b131-7d87ca5542bc
role: User, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1387'
ht-degree: 16%

---


# Speichern von Formularen als Entwürfe und Auflisten auf der Sites-Seite

<!--This article provides information about the Auto-save feature, which is currently available as a pre-release feature. The pre-release feature is accessible only through our [pre-release channel](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/release-notes/prerelease#new-features).-->

Erwägen Sie einen Benutzer, der mit dem Ausfüllen eines Formulars beginnt, aber später anhalten und zurückkehren muss. AEM bietet eine `save-as-draft` Option, mit der Benutzende das Formular als Entwurf für den zukünftigen Abschluss speichern können. Um dies zu erleichtern, stellt AEM die Forms **Portalkomponente „Entwürfe und Übermittlungen** bereit, die Entwürfe und Übermittlungen auf AEM Sites-Seiten anzeigt. Die Komponente listet Formulare auf, die als Entwürfe für den späteren Abschluss gespeichert wurden, sowie die gesendeten Formulare. Nur angemeldete Benutzer können ihre Entwürfe bearbeiten oder ihre gesendeten Formulare anzeigen. Wenn ein anonymer Benutzer jedoch mithilfe der Komponente **Suche und Auflister** durch die Liste der Formulare navigiert und ein Formular als Entwurf speichert, wird dieser Entwurf nicht durch die Komponente **Entwürfe und Sendungen** aufgeführt. Um Entwürfe und Übermittlungen anzuzeigen, müssen Benutzer zum Zeitpunkt der Formularübermittlung angemeldet sein.

![Symbol für Entwürfe](assets/drafts-component.png)

## Voraussetzungen

* Installieren Sie die neueste Version, um Kernkomponenten für adaptive Formulare für Ihre AEM Cloud Service-Umgebung zu aktivieren.

  Nach der Bereitstellung der neuesten Kernkomponenten in Ihrer Umgebung können Sie auf die Formularportal-Komponenten in Ihrer Authoring-Umgebung zugreifen.

* [Konfigurieren von Azure Storage und Unified Storage Connector für die Forms Portal-Komponente für Entwürfe und Übermittlungen](#configure-azure-storage-and-unified-storage-connector-for-drafts--submissions-forms-portal-component)

### Konfigurieren von Azure Storage und Unified Storage Connector für die Forms Portal-Komponente für Entwürfe und Übermittlungen

Die **Drafts &amp; Submissions**-Komponente benötigt eine Speichereinrichtung zum Speichern und Auflisten von Entwürfen auf der AEM Sites-Seite. Unified Storage Connector bietet ein Framework zur Verknüpfung von AEM mit externem Speicher. Um das Formular als Entwurf zu speichern, stellen Sie sicher, dass Sie über ein Azure-Speicherkonto und einen Zugriffsschlüssel verfügen, um den Zugriff auf das [!DNL Azure]-Speicherkonto zu autorisieren. Sobald Sie über ein Azure-Speicherkonto und den Zugriffsschlüssel verfügen, führen Sie die folgenden Schritte aus, um eine Azure Storage-Konfiguration zu erstellen:

1. Navigieren Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Azure-Speicher]**.

   ![Azure-Speicherkartenauswahl](/help/forms/assets/save-form-as-draft-azure-card.png)

1. Wählen Sie einen Konfigurationsordner aus, um die Konfiguration zu erstellen, und wählen Sie **[!UICONTROL Erstellen]**.

   ![Azure Storage-Konfigurationsordner auswählen](/help/forms/assets/save-form-as-draft-select-config-folder.png)

1. Geben Sie im Feld **[!UICONTROL Titel]** einen Titel für die Konfiguration an.
1. Geben Sie den Namen des [!DNL Azure] Speicherkontos in den Feldern **[!UICONTROL Azure-Speicherkonto]** und **[!UICONTROL Azure-]**) an.

   ![Azure Storage-Konfiguration](/help/forms/assets/save-form-as-draft-azure-storage.png)

   Geben Sie `Connection String` in das Textfeld `Azure Storage Account` und `Azure Key` in das Textfeld `Azure Access key` ein.

1. Klicken Sie auf **Speichern**.

   >[!NOTE]
   >
   > Sie können das **[!UICONTROL Azure-Speicherkonto]** und den **[!UICONTROL Azure-Zugriffsschlüssel]** über das [Microsoft Azure-Portal](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-keys-manage?tabs=azure-portal) abrufen.

   Nachdem Sie die Azure Storage-Konfiguration erfolgreich erstellt haben, konfigurieren Sie Unified Storage Connector für Forms Portal wie folgt:

1. Gehen Sie zu **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Unified Storage Connector]**.

   ![Unified Connector-Speicher](/help/forms/assets/save-form-as-draft-unified-connector.png)

1. Wählen Sie im Abschnitt **[!UICONTROL Formularportal]** den Eintrag **[!UICONTROL Azure]** aus der Dropdown-Liste **[!UICONTROL Speicher]** aus.
1. Geben Sie den Konfigurationspfad für die Azure-Speicherkonfiguration im Feld **[!UICONTROL Speicherkonfigurationspfad]** an.

   ![Unified Connector-Speichereinstellung](/help/forms/assets/save-form-as-draft-unified-connector-storage.png)

1. Wählen Sie **[!UICONTROL Speichern]** aus.

>[!NOTE]
>
> Wenn Sie eine andere Speicheroption als Azure konfigurieren müssen, schreiben Sie an aem-forms-ea@adobe.com von Ihrer offiziellen E-Mail-Adresse mit Ihren detaillierten Anforderungen.

Nachdem Sie Azure Storage und Unified Storage Connector erfolgreich zum Speichern der Entwürfe und gesendeten Formulare konfiguriert haben, fügen Sie die Komponente **Drafts &amp; Submissions** auf der AEM Sites-Seite hinzu.

## Wie fügt man die Komponente „Drafts &amp; Submissions“ zu einer AEM Sites-Seite hinzu?

Sie können vordefinierte Forms Portal-Komponenten verwenden, um Entwürfe und Sendungen auf der Sites-Seite aufzulisten. Führen Sie die folgenden Schritte aus, um die Portalkomponente **Entwürfe und**) hinzuzufügen:

1. Öffnen Sie die AEM Sites-Seite in einem **Bearbeitungsmodus**.
1. Navigieren Sie zu **[!UICONTROL Seiteninformationen]** > **[!UICONTROL Vorlage bearbeiten]**
   ![Richtlinie zum Bearbeiten von Vorlagen](/help/forms/assets/save-form-as-draft-edit-template.png)

1. Klicken Sie auf **[!UICONTROL Richtlinie]** und aktivieren Sie das Kontrollkästchen **[!UICONTROL Entwürfe und Übermittlungen]** unter dem **[AEM Archetype Project Name] - Forms and Communications Portal**.

   ![Auswählen von Richtlinien](/help/forms/assets/save-form-as-draft-enable-policy.png)

1. Klicken Sie auf **[!UICONTROL Fertig]**.
1. Öffnen Sie die AEM Sites-Seite jetzt erneut im Authoring-Modus.
1. Suchen Sie im Seiteneditor nach dem Abschnitt, in dem Sie die Formularportal-Komponente hinzufügen können.
1. Klicken Sie auf das Symbol **Hinzufügen**. Das Symbol ist ein Pluszeichen (+). Es steht für die Option zum Hinzufügen neuer Komponenten.

   Wenn Sie auf das Symbol **Hinzufügen** klicken, wird das Dialogfeld **Neue Komponente einfügen** angezeigt, in dem verschiedene Komponenten zum Einfügen angezeigt werden.

   >[!NOTE]
   >
   > Alternativ können Sie die Komponente auch per Drag-and-Drop hinzufügen.

1. Durchsuchen Sie die verfügbaren Komponenten im Dialogfeld und wählen Sie die gewünschte Komponente aus der Liste aus. Wählen Sie beispielsweise die Komponente **Entwürfe und Übermittlungen** aus der Liste aus, um die Komponente **Entwürfe und Übermittlungen** Forms Portal hinzuzufügen.

   ![Komponente „Entwurf und Übermittlung hinzufügen](/help/forms/assets/save-form-as-draft-add-dns.png)

Konfigurieren Sie nun die Eigenschaften der Komponente **Drafts and Submissions** entsprechend den Anforderungen.

## Konfigurieren Sie die Eigenschaften der Komponente „Drafts &amp; Submissions“

Sie können die Eigenschaften von **Entwürfe und Übermittlungen** konfigurieren:

1. Wählen Sie die **Drafts &amp; Submissions** aus.
1. Klicken Sie auf ![Symbol „Konfigurieren](assets/configure_icon.png) und das Dialogfeld wird angezeigt.
1. Geben **[!UICONTROL im Dialogfeld]** Entwürfe und Einsendungen“ Folgendes an:

   * **Titel** Um eine Komponente auf einer Sites-Seite zu identifizieren, wird der Titel standardmäßig über der Komponente angezeigt.
   * **Typ auswählen**, um die Formularliste als Entwurf oder übermittelte Formulare anzugeben. Wenn Sie **Forms-Entwurf** auswählen, werden die als Entwürfe gespeicherten Formulare angezeigt. Alternativ können Sie **Gesendete Forms** auswählen, um die Formulare anzuzeigen, die von angemeldeten Benutzern gesendet wurden.
   * **Layout**: Zum Anzeigen von Listenentwürfen oder übermittelten Formularen im Karten- oder Listenformat.

   ![Eigenschaften der Entwurfs- und Sendekomponente](/help/forms/assets/save-form-as-draft-dns-properties.png)

## Konfigurieren von Formularen zum Speichern als Entwürfe

Sie können adaptive Forms auf die beiden folgenden Arten konfigurieren, um sie als Entwürfe für die spätere Verwendung zu speichern:

* [Benutzeraktion](#user-action)
* [Automatisches Speichern](#auto-save)

### Benutzeraktion

>[!NOTE]
>
> Stellen Sie sicher, dass [Kernkomponentenversion auf 3.0.24 oder höher eingestellt ist](https://github.com/adobe/aem-core-forms-components) um Formulare mithilfe der Regel **Formular speichern** als Entwürfe zu speichern.

Um ein Formular als Entwurf zu speichern, erstellen Sie eine Regel **Formular speichern** für eine Formularkomponente, z. B. eine Schaltfläche. Wenn auf die Schaltfläche geklickt wird, wird die Regel Trigger und das Formular wird als Entwurf gespeichert. Führen Sie die folgenden Schritte aus, um eine Regel **Formular speichern** für eine Schaltflächenkomponente zu erstellen:

1. Öffnen Sie ein adaptives Formular im Bearbeitungsmodus.
1. Wählen Sie das Symbol **[!UICONTROL Regeln bearbeiten]**, um den Regeleditor für die Komponente **Schaltfläche** zu öffnen.
1. Wählen Sie **[!UICONTROL Erstellen]** aus, um die Regel für die Schaltfläche zu konfigurieren und zu erstellen.
1. Wählen Sie im Abschnitt **[!UICONTROL Wenn]** die Option **wird**) und im Abschnitt **[!UICONTROL Dann]** die Option **Formular speichern** aus.
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.

   ![Regel für Schaltfläche erstellen](/help/forms/assets/save-form-as-drfat-create-rule.png)

Wenn Sie ein adaptives Formular in der Vorschau anzeigen, ausfüllen und auf die Schaltfläche **Formular speichern** klicken, wird das Formular als Entwurf gespeichert.

### Entwürfe

>[!NOTE]
>
> Stellen Sie sicher, dass [Kernkomponentenversion auf 3.0.52 oder höher eingestellt ist](https://github.com/adobe/aem-core-forms-components) um Formulare mithilfe der Funktion zum automatischen Speichern als Entwürfe zu speichern.

Sie können ein adaptives Formular auch so konfigurieren, dass es automatisch auf der Grundlage eines zeitbasierten Ereignisses gespeichert wird, sodass das Formular nach der angegebenen Dauer gespeichert wird. Wenn Sie [Forms Portal-Komponenten für Ihre Umgebung aktivieren](/help/forms/list-forms-on-sites-page.md#enable-forms-portal-components-for-your-existing-environment) wird die Registerkarte **Automatisches Speichern** in den Eigenschaften des Forms-Containers angezeigt. Sie können die Funktion zum automatischen Speichern für ein adaptives Formular konfigurieren:

1. Öffnen Sie in der Autoreninstanz ein adaptives Formular im Bearbeitungsmodus.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol Guide-Container![Eigenschaften](/help/forms/assets/configure-icon.svg) und öffnen Sie die Registerkarte **[!UICONTROL Entwürfe]**.

   ![Automatisches Speichern](/help/forms/assets/auto-save.png)

1. Aktivieren Sie **[!UICONTROL Kontrollkästchen]** Entwürfe automatisch speichern“, um das automatische Speichern des Formulars als Entwürfe zu aktivieren.
1. Konfigurieren Sie **[!UICONTROL Voreinstellung speichern]** als **Entwürfe in regelmäßigen Abständen speichern**, um das Formular <!--based on the occurrence of an event or--> nach einem bestimmten Zeitintervall automatisch zu speichern.
1. Geben Sie das Zeitintervall in **[!UICONTROL Häufigkeit für Speicherintervall (Sekunden)]** an, um die Dauer festzulegen, mit der das automatische Speichern des Formulars im definierten Intervall Trigger wird.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

## Anzeigen von Entwürfen/gesendeten Formularen auf der Sites-Seite mithilfe der Komponente „Drafts &amp; Submissions“

Um gespeicherte Entwürfe oder übermittelte Formulare anzuzeigen, verwenden Sie die **Entwürfe und Übermittlungen** Forms Portal-Komponente.
Wenn **[!UICONTROL Typ auswählen]** im Dialogfeld **Konfigurieren der Komponente „Entwürfe und Einsendungen** als [Forms&quot; ausgewählt ist](#configure-properties-of-the-drafts--submissions-component) werden die als Entwürfe gespeicherten Formulare auf der Sites-Seite angezeigt. Sie können die Entwürfe öffnen, indem Sie auf die Auslassungspunkte (…) klicken, um das Formular auszufüllen.

![Symbol für Entwürfe](assets/drafts-component.png)

Forms Wenn **[!UICONTROL Typ auswählen]** im Dialogfeld „Konfigurieren **der Komponente „Drafts &amp; Submissions** als „Gesendete“ ausgewählt [, &#x200B;](#configure-properties-of-the-drafts--submissions-component) die gesendeten Formulare angezeigt. Sie können die übermittelten Formulare anzeigen, sie jedoch nicht bearbeiten.

![Symbol für Einsendungen](assets/submission-listing.png)

Sie können Formulare auch verwerfen, indem Sie auf die Auslassungspunkte (…) in der rechten unteren Ecke des Formulars klicken.

>[!NOTE]
>
> Im Forms-Portal unterstützt die Komponente „Drafts &amp; Submissions“ nur Übermittlungen aus Foundation-basierten Formularen.

## Nächste Schritte

Im nächsten Artikel erfahren wir, [&#x200B; Sie mithilfe der Link-Forms-Portal-Komponente Verweise auf Formulare auf der Sites-Seite hinzufügen](/help/forms/add-form-link-to-aem-sites-page.md).

## Verwandte Artikel

{{forms-portal-see-also}}

## Siehe auch {#see-also}

{{see-also}}