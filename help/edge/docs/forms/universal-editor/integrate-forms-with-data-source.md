---
title: Wie lässt sich das Formulardatenmodell (FDM) für ein Formular im universellen Editor integrieren?
description: Erfahren Sie, wie Sie Formulare für Edge-Bereitstellungs-Services auf der Grundlage eines Formulardatenmodells (FDM) erstellen. Erstellen und bearbeiten Sie Beispieldaten für Datenmodellobjekte im FDM.
feature: Edge Delivery Services, Form Data Model
role: Admin, User
exl-id: 9ce51223-57d0-47d8-8868-84b37d4e8e3e
source-git-commit: cfff846e594b39aa38ffbd3ef80cce1a72749245
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 32%

---


# Integrieren von Forms mit dem Formulardatenmodell (FDM)

Verbinden Sie Ihre Formulare mit Backend-Datenquellen mithilfe von FDM, um Datenbindungs-, Validierungs- und Übermittlungs-Workflows zu ermöglichen.

## Voraussetzungen

Führen Sie diese Schritte aus, bevor Sie FDM in Ihre Formulare integrieren:

1. **[Konfigurieren von Data Source](/help/forms/configure-data-sources.md)**: Einrichten von Backend-Verbindungen
2. **[Formulardatenmodell erstellen](/help/forms/create-form-data-models.md)**: Definieren der Datenstruktur und der Services
3. **[Datenmodellobjekte konfigurieren](/help/forms/work-with-form-data-model.md)**: Datenbeziehungen zuordnen

## Überlegungen

Wenn das Symbol **Datenquellen** in der Benutzeroberfläche des universellen Editors oder die Eigenschaft **Bindungsverweis** im Panel „Eigenschaften“ auf der rechten Seite nicht angezeigt wird, aktivieren Sie die Erweiterung **Datenquelle** im **Extension Manager**.

![Screenshot der Extension Manager-Benutzeroberfläche des universellen Editors mit den verfügbaren Erweiterungen, einschließlich der Datenquellenerweiterung, die für die Formularintegration aktiviert werden kann](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

Informationen zum Aktivieren und Deaktivieren von Erweiterungen im universellen Editor finden Sie im Artikel [Extension Manager – Highlights der Funktionen](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

## Wählen Sie Ihren Formulartyp

Der universelle Editor unterstützt zwei Ansätze zur Formularerstellung:

| Aspekt | Schemabasiertes Formular | Nicht schemabasiertes Formular |
|--------|-------------------|----------------------|
| **Setup-Komplexität** | Einfach (automatische Bindung) | Manuell (feldweise Bindung) |
| **Anwendungsfall** | Neue Formulare mit definierter Datenstruktur | Bestehende Formulare oder flexible Anforderungen |
| **Datenquelle** | Erforderlich bei der Erstellung | Kann später hinzugefügt werden |
| **Bindung** | Automatische Feldbindung | Manuelle Bindung pro Feld |

![Formulartypen im universellen Editor](/help/edge/docs/forms/universal-editor/assets/form-types.png){width="50%" align="center" height="50%"}

## Schemabasiertes Formular

Schemabasierte Formulare konfigurieren automatisch Datenquellen und binden Formularfelder an Daten. Dieser Ansatz eignet sich ideal für neue Formulare mit klar definierten Datenstrukturen.

### Schemabasiertes Formular erstellen

1. **Zugriff auf die Forms-Konsole**
   - Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an
   - Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms und Dokumente]**

2. **Formularerstellung starten**
   - Wählen Sie **[!UICONTROL Erstellen]** > **[!UICONTROL Adaptive Forms]**
   - Edge Delivery Services-Vorlage auswählen
   - Klicken Sie auf **[!UICONTROL Erstellen]** wenn aktiviert

   ![Vorlage von Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

3. **Konfigurieren des Datenmodells**
   - Wechseln Sie zur Registerkarte **Daten**
   - Wählen Sie **Formulardatenmodell (FDM)** für mehrere Datenquellen oder **JSON-Schema** für ein einzelnes Backend-System aus
   - Wählen Sie das erstellte FDM aus (z. B. „Haustier-Formulardatenmodell„)

   ![Auswählen des Formulardatenmodells](/help/edge/docs/forms/universal-editor/assets/select-petstore-form-data-model.png)

4. **Abschließen der Formulareinrichtung**
   - Geben Sie **Name** und **Titel** ein
   - Geben Sie **GitHub-URL** an (z. B. `https://github.com/wkndforms/edsforms`)
   - Klicken Sie auf **[!UICONTROL Erstellen]**.

   ![Erstellen eines schemabasierten Formulars](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form.png)

### Schemabasiertes Formular überprüfen

Das Formular wird im universellen Editor mit vorkonfigurierter Datenbindung geöffnet:

![Screenshot des universellen Editors, der ein schemabasiertes Formular mit vorausgefüllten Formularfeldern und den Inhalts-Browser mit verfügbaren Datenquellenelementen zeigt](/help/edge/docs/forms/universal-editor/assets/schema-based-form-in-ue.png)

![Automatische Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## Nicht schemabasiertes Formular

Nicht-Schemaformulare erfordern eine manuelle Datenquellenkonfiguration und Feldbindung. Dieser Ansatz bietet Flexibilität für bestehende Formulare oder komplexe Anforderungen.

### Erstellen eines nicht schemabasierten Formulars

1. **Zugriff auf Formulareigenschaften**
   - Melden Sie sich bei Ihrer [!DNL Experience Manager Forms]-Autoreninstanz an
   - Navigieren Sie zu **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms und Dokumente]**
   - Wählen Sie Ihr Formular aus und klicken Sie auf **[!UICONTROL Eigenschaften]**

   ![Öffnen der Formulareigenschaften](/help/edge/docs/forms/universal-editor/assets/non-schema-based-edit-properties.png)

2. **Formularmodell konfigurieren**
   - Öffnen Sie die **Formularmodell** Registerkarte
   - Wählen Sie **Formulardatenmodell (FDM)** aus der Dropdown-Liste **Auswählen aus** aus
   - FDM aus der Liste auswählen

   ![Registerkarte „Formularmodell auswählen“](/help/edge/docs/forms/universal-editor/assets/select-form-model.png)

   ![Auswählen des FDM](/help/edge/docs/forms/universal-editor/assets/select-fdm.png)

3. **Konfiguration bestätigen**
   - Klicken **im** auf OK
   - Klicken Sie auf **[!UICONTROL Speichern und schließen]**.

   ![Assistent für das Formularmodell](/help/edge/docs/forms/universal-editor/assets/form-model-wizard.png)

### Hinzufügen von Datenelementen

1. **Formular zur Bearbeitung öffnen**
   - Das Formular wird im universellen Editor geöffnet

   ![Erstellen nicht schemabasierter Formulare](/help/edge/docs/forms/universal-editor/assets/non-schema-form-authoring.png)

2. **Zugriff auf Source-Datenelemente**
   - Navigieren Sie zur **[!UICONTROL Datenquelle]** im **[!UICONTROL Inhaltsbrowser]**
   - Anzeigen verfügbarer Datenelemente aus Ihrem FDM

   ![Formulardatenquelle](/help/edge/docs/forms/universal-editor/assets/non-schema-data-source.png)

3. **Elemente zum Formular hinzufügen**
   - Wählen Sie Datenelemente aus und klicken Sie auf **[!UICONTROL Hinzufügen]**
   - Oder ziehen Sie Elemente per Drag-and-Drop, um das Formular zu erstellen

   ![Hinzufügen von Datenelementen](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-element.png)

   ![Screenshot des universellen Editors mit einem Nicht-Schemaformular, das durch Ziehen und Ablegen von Datenelementen von der Registerkarte „Data Source“ in die Formularstruktur erstellt wird](/help/edge/docs/forms/universal-editor/assets/non-schema-form.png)

### Manuelle Datenbindung hinzufügen

Fügen Sie für vorhandene Formularfelder die Datenbindung über die Eigenschaft **Bindungsverweis** hinzu:

1. **Feldeigenschaften öffnen**
   - Formularfeld für die Bindung auswählen
   - Öffnen des Eigenschaftenbedienfelds

2. **Bindungsverweis konfigurieren**
   - Wechseln Sie zur Eigenschaft **Bindungsverweis**
   - Klicken Sie auf das **Durchsuchen**-Symbol

   ![Manuelles Hinzufügen der Datenbindung für ein Formularfeld](/help/edge/docs/forms/universal-editor/assets/non-schema-add-data-binding.png)

3. **Datenelement auswählen**
   - Wählen Sie im Datenquellenbaum des Assistenten **Bindungsverweis auswählen**.
   - Wählen Sie das gewünschte Datenelement aus und klicken Sie auf **Auswählen**

   ![Auswählen des Datenbindungsverweises](/help/edge/docs/forms/universal-editor/assets/select-bind-reference.png)

   ![Auswählen des Datenelements](/help/edge/docs/forms/universal-editor/assets/select-data-element.png)

4. **Bindung überprüfen**
   - Das Formularfeld wird jetzt an das Datenelement gebunden
   - Die Bindung wird in der Eigenschaft **Bindungsverweis** angezeigt

   ![Automatische Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding.png)

## Integration überprüfen

Nach Abschluss der Integration:

1. **Datenbindung testen**: Überprüfen Sie, ob Formularfelder korrekte Daten anzeigen
2. **Übermittlungen validieren**: Sicherstellen, dass Daten in konfigurierten Quellen gespeichert werden
3. **Fehlerbehandlung überprüfen**: Testen mit ungültigen Datenszenarien

## Nächste Schritte

Konfigurieren Sie [Übermittlungsaktionen](/help/edge/docs/forms/universal-editor/submit-action.md), um Ihren Formular-Workflow abzuschließen.
