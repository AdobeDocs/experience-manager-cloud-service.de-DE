---
title: Wie lässt sich das Formulardatenmodell (FDM) für ein Formular im universellen Editor integrieren?
description: Erfahren Sie, wie Sie Formulare für Edge Delivery Services basierend auf einem Formulardatenmodell (FDM) erstellen können. Erstellen und bearbeiten Sie Beispieldaten für Datenmodellobjekte im FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: ht
source-wordcount: '716'
ht-degree: 100%

---


# Integrieren von Formularen mit einem Formulardatenmodell (FDM)

Verbinden Sie Ihre Formulare mithilfe eines FDM mit Backend-Datenquellen, um Datenbindungs-, Validierungs- und Übermittlungs-Workflows zu ermöglichen.

## Voraussetzungen

Führen Sie die folgenden Schritte aus, bevor Sie ein FDM in Ihre Formulare integrieren:

1. **[Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md)**: Richten Sie Backend-Verbindungen ein.
2. **[Erstellen des Formulardatenmodells](/help/forms/create-form-data-models.md)**: Definieren Sie Datenstruktur und Dienste.
3. **[Konfigurieren von Datenmodellobjekten](/help/forms/work-with-form-data-model.md)**: Ordnen Sie Datenbeziehungen zu.

## Überlegungen

Wenn das Symbol **Datenquellen** in der Benutzeroberfläche des universellen Editors oder die Eigenschaft **Bindungsverweis** im Panel „Eigenschaften“ auf der rechten Seite nicht angezeigt wird, aktivieren Sie die Erweiterung **Datenquelle** im **Extension Manager**.

![Screenshot der Extension Manager-Benutzeroberfläche des universellen Editors mit den verfügbaren Erweiterungen, einschließlich der Datenquellenerweiterung, die für die Formularintegration aktiviert werden kann](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

Informationen zum Aktivieren und Deaktivieren von Erweiterungen im universellen Editor finden Sie im Artikel [Extension Manager – Highlights der Funktionen](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

## Auswählen Ihres Formulartyps

Der universelle Editor unterstützt zwei Ansätze zur Formularerstellung:

| Aspekt | Schemabasiertes Formular | Nicht schemabasiertes Formular |
|--------|-------------------|----------------------|
| **Komplexität beim Setup** | Einfach (automatische Bindung) | Manuell (feldweise Bindung) |
| **Anwendungsfall** | Neue Formulare mit definierter Datenstruktur | Vorhandene Formulare oder flexible Anforderungen |
| **Datenquelle** | Erforderlich bei der Erstellung | Kann später hinzugefügt werden |
| **Bindung** | Automatische Feldbindung | Manuelle Bindung pro Feld |

![Formulartypen im universellen Editor](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

## Schemabasiertes Formular

Schemabasierte Formulare konfigurieren Datenquellen automatisch und binden Formularfelder an Daten. Dieser Ansatz eignet sich ideal für neue Formulare mit klar definierten Datenstrukturen.

### Erstellen eines schemabasierten Formulars

1. **Aufrufen der Forms-Konsole**
   - Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an. 
   - Gehen Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Formulare und Dokumente]**.

2. **Starten der Formularerstellung**
   - Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptives Formular]**. 
   - Wählen Sie eine Edge Delivery Services-Vorlage.
   - Klicken Sie auf **[!UICONTROL Erstellen]** (so aktiviert).

   ![Vorlage von Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

3. **Konfigurieren eines Datenmodells**
   - Wechseln Sie zur Registerkarte **Daten**.
   - Wählen Sie **Formulardatenmodell (FDM)** für mehrere Datenquellen oder **JSON-Schema** für ein einzelnes Backend-System.
   - Wählen Sie das erstellte FDM aus (z. B. „Formulardatenmodell für Haustiere“).

   ![Auswählen des Formulardatenmodells](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)

4. **Abschließen der Formulareinrichtung**
   - Geben Sie **Name** und **Titel** ein.
   - Geben Sie die **GitHub-URL** an (z. B. `https://github.com/wkndforms/edsforms`).
   - Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Erstellen eines schemabasierten Formulars](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

### Überprüfen Sie das schemabasierte Formular.

Das Formular wird im universellen Editor mit vorkonfigurierter Datenbindung geöffnet:

![Screenshot des universellen Editors, der ein schemabasiertes Formular mit vorausgefüllten Formularfeldern und den Inhalts-Browser mit verfügbaren Datenquellenelementen zeigt](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

![Automatische Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## Nicht schemabasiertes Formular

Nicht schemabasierte Formulare erfordern eine manuelle Datenquellenkonfiguration und Feldbindung. Dieser Ansatz bietet Flexibilität bei bestehenden Formularen oder komplexen Anforderungen.

### Erstellen Sie ein nicht schemabasiertes Formular.

1. **Aufrufen der Formulareigenschaften**
   - Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an. 
   - Gehen Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Formulare und Dokumente]**.
   - Wählen Sie ein Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften]**.

   ![Öffnen der Formulareigenschaften](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

2. **Konfigurieren eines Formularmodells**
   - Öffnen Sie die Registerkarte **Formularmodell**.
   - Wählen Sie **Formulardatenmodell (FDM)** aus der Dropdown-Liste **Auswählen** aus.
   - Wählen Sie Ihr FDM aus der Liste aus.

   ![Registerkarte „Formularmodell auswählen“](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

   ![Auswählen des FDM](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

3. **Bestätigen der Konfiguration**
   - Klicken Sie im Warndialogfeld auf **OK**.
   - Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   ![Assistent für das Formularmodell](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

### Hinzufügen von Datenelementen

1. **Öffnen von Formular zur Bearbeitung**
   - Das Formular wird im universellen Editor geöffnet. 

   ![Erstellen nicht schemabasierter Formulare](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

2. **Zugreifen auf Datenquellenelemente**
   - Navigieren Sie zur Registerkarte **[!UICONTROL Datenquelle]** im **[!UICONTROL Inhalts-Browser]**.
   - Zeigen Sie verfügbare Datenelemente aus Ihrem FDM an.

   ![Formulardatenquelle](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

3. **Hinzufügen von Elementen zum Formular**
   - Wählen Sie Datenelemente aus und klicken Sie auf **[!UICONTROL Hinzufügen]**.
   - Oder ziehen Sie Elemente per Drag-and-Drop, um Ihr Formular einzurichten.

   ![Hinzufügen von Datenelementen](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   ![Screenshot des universellen Editors mit einem Nicht-Schemaformular, das durch Ziehen und Ablegen von Datenelementen von der Registerkarte „Data Source“ in die Formularstruktur erstellt wird](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

### Hinzufügen einer manuellen Datenbindung

Fügen Sie für vorhandene Formularfelder über die Eigenschaft **Bindungsverweis** eine Datenbindung hinzu:

1. **Öffnen der Feldeigenschaften**
   - Wählen Sie das Formularfeld für die Bindung aus.
   - Öffnen Sie das Bedienfeld „Eigenschaften“.

2. **Konfigurieren des Bindungsverweises**
   - Wechseln Sie zur Eigenschaft **Bindungsverweis**.
   - Klicken Sie auf das Symbol für **Durchsuchen**.

   ![Manuelles Hinzufügen der Datenbindung für ein Formularfeld](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

3. **Auswählen des Datenelements**
   - Wählen Sie aus der Datenquellenstruktur im Assistenten **Bindungsverweis auswählen** aus.
   - Wählen Sie das gewünschte Datenelement aus und klicken Sie auf **Auswählen**.

   ![Auswählen des Datenbindungsverweises](/help/edge/docs/forms/universal-editor/assets/select-bind-reference.png)

   ![Auswählen des Datenelements](/help/edge/docs/forms/universal-editor/assets/select-data-element.png)

4. **Überprüfen der Bindung**
   - Das Formularfeld ist jetzt an das Datenelement gebunden.
   - Die Bindung wird in der Eigenschaft **Bindungsverweis** angezeigt.

   ![Automatische Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## Überprüfen Sie die Integration.

Nach Abschluss der Integration:

1. **Datenbindung testen**: Überprüfen Sie, ob Formularfelder korrekte Daten anzeigen.
2. **Übermittlungen validieren**: Vergewissern Sie sich, dass Daten in konfigurierten Quellen gespeichert werden
3. **Fehlerbehandlung überprüfen**: Testen Sie mit ungültigen Datenszenarien.

## Nächste Schritte

Konfigurieren Sie [Übermittlungsaktionen](/help/edge/docs/forms/universal-editor/submit-action.md), um Ihren Formular-Workflow abzuschließen.
