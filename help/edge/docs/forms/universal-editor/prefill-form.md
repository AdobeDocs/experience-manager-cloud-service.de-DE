---
title: Vorbefüllen von Feldern in adaptiven Formularen
description: 'Verwenden Sie bestehende Daten, um die Felder eines adaptiven Formulars vorzubefüllen. Benutzende können Formulare mit grundlegenden Daten vorbefüllen, indem sie sich mit ihren Social Media-Profilen anmelden. '
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
time: 45-60 minutes
keywords: Vorbefüllen eines adaptiven Formulars, Edge Delivery Services für adaptive Formulare, automatisches Ausfüllen eines adaptiven Formulars
exl-id: 7b6224e2-a19c-4146-8545-0ce9d1da9b29
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: ht
source-wordcount: '1787'
ht-degree: 100%

---

# Konfigurieren des Vorbefüllungsdienstes in adaptiven Forms mit Edge Delivery Services

Beim Vorbefüllen eines Formulars werden Formularfelder automatisch mit relevanten Daten aus externen Quellen ausgefüllt, sobald eine Benutzerin bzw. ein Benutzer das Formular öffnet. Durch die Nutzung von Daten aus Benutzerprofilen, Datenbanken, gespeicherten Entwürfen oder anderen Backend-Systemen wird das Ausfüllen des Formulars erleichtert, indem manuelle Eingaben reduziert, Fehler minimiert und das Ausfüllen beschleunigt werden. Das erhöht nicht nur die Benutzerzufriedenheit, sondern auch die Wahrscheinlichkeit erfolgreicher Formularübermittlungen.

## Vorteile des Vorbefüllens von Formularen

| Vorteil | Beschreibung |
|---------|-------------|
| **Schnellere Fertigstellung** | Reduziert manuelle Dateneingaben und hilft Benutzenden, Formulare schnell auszufüllen |
| **Verbessertes Anwendererlebnis** | Formulare fühlen sich personalisierter und bequemer an, insbesondere für wiederkehrende Benutzende |
| **Höhere Konversionsraten** | Reduziert durch eine Minimierung des Benutzeraufwands die Zahl der Formularabbrüche |
| **Weniger Eingabefehler** | Daten aus vertrauenswürdigen Quellen verringern Tippfehler und falsche Einträge |
| **Bessere Datenqualität** | Stellt strukturierte, genaue und konsistente Daten für Backend-Systeme sicher |

## Funktionsweise der Vorbefüllung

Das folgende Diagramm veranschaulicht die automatische Vorbefüllung, die beim Öffnen eines adaptiven Formulars durch eine Benutzerin bzw. einen Benutzer vorgenommen wird:

![Prozessablauf zum Vorbefüllen von Formularen](/help/edge/docs/forms/universal-editor/assets/prefill-process-flow.svg)

Der Vorbefüllungsprozess umfasst vier wichtige Schritte:

1. **Benutzerin bzw. Benutzer öffnet Formular**: Benutzerin bzw. Benutzer greift über eine URL oder Navigation auf ein adaptives Formular zu
1. **Identifizieren von Datenquelle**: Der Vorbefüllungsdienst ermittelt die konfigurierte Datenquelle (Formulardatenmodell oder Entwurfsdienst)
1. **Abrufen von Daten**: Das System ruft basierend auf Kontext, Parametern oder Benutzeridentifizierung relevante Benutzerdaten ab
1. **Zuordnen und Anzeigen**: Daten werden Formularfeldern mithilfe von `bindRef`-Eigenschaften zugeordnet und das ausgefüllte Formular wird der Benutzerin bzw. dem Benutzer angezeigt

Dieses automatisierte Verfahren sorgt dafür, dass die Benutzenden ein Formular mit ihren relevanten Daten vorausgefüllt sehen, was das Benutzererlebnis und die Formularausfüllraten erheblich verbessert.

## Datenstruktur zum Vorbefüllen

Adaptive Formulare unterstützen zwei Arten von Feldern:

- **Gebundene Felder**: Felder, die mit einer Datenquelle mit einer nicht leeren `bindRef`-Eigenschaft verbunden sind
- **Ungebundene Felder**: Eigenständige Felder mit leeren `bindRef`-Werten

Die Datenstruktur zum Vorbefüllen umfasst:

- **afBoundData**: Enthält Daten für gebundene Felder und Bereiche
- **afUnBoundData**: Enthält Daten für ungebundene Felder

Das Datenformat muss mit Ihrem Formularmodell übereinstimmen:

- **XFA-Formulare**: XML-konform mit dem XFA-Vorlagenschema
- **XML-Schemaformulare**: XML, die mit der Schemastruktur übereinstimmt
- **JSON-Schemaformulare**: JSON-konform mit dem Schema
- **Formulardatenmodell (FDM)-Formulare**: JSON, das mit der FDM-Struktur übereinstimmt
- **Schemalose Formulare**: Alle Felder sind ungebunden und nutzen ungebundene XML

## Voraussetzungen

Bevor Sie Vorbefüllungsdienste konfigurieren, müssen Sie folgende Voraussetzungen erfüllen:

### Erforderliches Setup

- [Für Edge Delivery Services konfiguriertes GitHub-Repository](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)
- [Dem Projekt hinzugefügter Block für adaptive Formulare](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)
- [Datenquelle konfiguriert](/help/forms/configure-data-sources.md)
- [Formulardatenmodell (FDM) erstellt](/help/forms/create-form-data-models.md)

### Zugriffsanforderungen

- Zugriff auf AEM Forms as a Cloud Service
- Berechtigungen zum Erstellen und Bearbeiten von Formularen
- Zugriff auf den universellen Editor mit aktivierten erforderlichen Erweiterungen

>[!TIP]
>
> Sie können Formulare auch bearbeiten, um das Formulardatenmodell (FDM) in den universellen Editor zu integrieren und Daten aus verschiedenen Backend-Quellen abzurufen. Weitere Informationen finden Sie im Artikel [Integrieren von Formularen mit dem Formulardatenmodell im universellen Editor](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md).

## Optionen für den Vorbefüllungsdienst

Der universelle Editor bietet zwei Optionen für den Vorbefüllungsdienst:

| Diensttyp | Zweck | Datenquelle | Am besten geeignet für |
|--------------|---------|-------------|----------|
| **Vorbefüllung mit Formularportal-Entwürfen** | Setzt teilweise ausgefüllte Formulare fort | Gespeicherte Entwürfe im Formularportal | Fortsetzung unvollständiger Anträge |
| **Vorbefüllung mit Formulardatenmodell** | Befüllen von Feldern aus externen Systemen | Backend-Datenbanken über FDM | Automatisches Ausfüllen von Anwenderprofildaten |

### Detailvergleich

| Funktion | Vorbefüllungsdienst mit Entwürfen | Vorbefüllungsdienst mit FDM |
|---------|----------------------|---------------------|
| **Authentifizierung** | Erfordert Benutzeranmeldung für Entwurfszugriff | Konfigurierbar je nach Datenquelle |
| **Setup-Komplexität** | Minimale Konfiguration | FDM-Setup und -Zuordnung erforderlich |
| **Datentyp** | Statisch gespeicherte Daten | Dynamische Echtzeitdaten |
| **Anwendungsfall** | Fortsetzen von gespeicherten Anträgen | Vorbefüllen aus Benutzerprofilen oder Datenbanken |


## Konfigurieren eines Vorbefüllungsdienstes für ein Formular

+++Phase 1: Einrichten des Formulardatenmodells

### Schritt 1: Erstellen Sie ein Formulardatenmodell

1. Melden Sie sich bei Ihrer AEM Forms as a Cloud Service-Instanz an.
1. Navigieren Sie zu: **Adobe Experience Manager** > **Formulare** > **Formulare und Dokumente**
1. Wählen Sie **Erstellen** > **Formulardatenmodell** aus.
1. Wählen Sie Ihre **Datenquellenkonfiguration** und dann die konfigurierte **Datenquelle**.

   ![Erstellen eines Formulardatenmodells](/help/edge/docs/forms/universal-editor/assets/create-fdm.png)

   >[!TIP]
   >
   >Genaue Anweisungen zum Erstellen von Formulardatenmodellen finden Sie unter [Erstellen eines Formulardatenmodells](/help/forms/create-form-data-models.md).

### Schritt 2: Konfigurieren Sie FDM-Dienste

1. Wechseln Sie zu **Adobe Experience Manager** > **Formulare** > **Datenintegrationen**.
1. Öffnen Sie Ihr Formulardatenmodell im Bearbeitungsmodus.
1. Wählen Sie ein Datenmodellobjekt aus und klicken Sie auf **Eigenschaften bearbeiten**.
1. Konfigurieren Sie **Lese**- und **Schreib**-Dienste für die ausgewählten Datenmodellobjekte. 

   ![Konfigurieren des Lese- und Schreibdiensts](/help/edge/docs/forms/universal-editor/assets/configure-reda-write-service.png)

1. Konfigurieren Sie die Dienstargumente:

   - Klicken Sie auf das Bearbeitungssymbol für das Argument des Lesediensts.
   - Binden Sie das Argument an ein **Benutzerprofilattribut**, **Anfrageattribut** oder einen **Literalwert**.
   - Geben Sie den Bindungswert an (z. B. `petid` für ein Registrierungsformular für Haustiere).

   ![Konfigurieren des Haustier-ID-Arguments](/help/edge/docs/forms/universal-editor/assets/pet-id-arguments.png)

1. Klicken Sie auf **Fertig**, um das Argument zu speichern, und auf **Speichern**, um das FDM zu speichern.

   >[!NOTE]
   >
   > Erfahren Sie mehr über das Konfigurieren von FDM-Diensten in [Arbeiten mit einem Formulardatenmodell (FDM)](/help/forms/work-with-form-data-model.md).

+++

+++Phase 2: Erstellen und Konfigurieren des adaptiven Formulars

### Schritt 3: Erstellen Sie ein adaptives Formular

1. Gehen Sie zu **Adobe Experience Manager** > **Forms** > **Formulare und Dokumente**.
1. Wählen Sie **Erstellen** > **Adaptive Formulare**. 
1. Wählen Sie auf der Registerkarte **Quelle** eine Edge Delivery Services-basierte Vorlage aus:

   ![Vorlage von Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

1. Klicken Sie auf **Erstellen**, um den Assistenten für **Formular erstellen** zu öffnen.
1. Geben Sie die Formulardetails an:

   - **Name**: Geben Sie einen beschreibenden Namen für Ihr Formular ein.
   - **Titel**: Geben Sie einen anwenderfreundlichen Titel an.
   - **GitHub-URL**: Geben Sie die URL Ihres Repositorys ein (z. B. `https://github.com/wkndforms/edsforms`).

1. Klicken Sie auf **Erstellen**.

   ![Erstellen eines schemabasierten Formulars](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form1.png)

Das Formular wird im universellen Editor zum Erstellen geöffnet.

### Schritt 4: Konfigurieren Sie die Formulardatenquelle

1. Wählen Sie ein Formular aus und klicken Sie auf **Eigenschaften**.

   ![Wählen Sie Formulareigenschaften](/help/edge/docs/forms/universal-editor/assets/select-form-properties1.png)

2. Öffnen Sie die Registerkarte **Formularmodell**.
3. Wählen Sie in der Dropdown-Liste **Auswählen** den Eintrag **Formulardatenmodell (FDM)**.
4. Wählen Sie in der Dropdown-Liste das erstellte Formulardatenmodell (z. B. PetFDM) aus.

   ![Registerkarte „Formularmodell auswählen“](/help/edge/docs/forms/universal-editor/assets/select-form-model1.png)

5. Klicken Sie auf **Speichern und schließen**.
6. Öffnen Sie das Formular zur Bearbeitung im universellen Editor.

Die Formularelemente aus Ihrem FDM werden auf der Registerkarte **Datenquelle** des **Inhalts-Browsers** angezeigt.

### Schritt 5: Fügen Sie Datenbindungen zu Formularfeldern hinzu

1. Wählen Sie Datenelemente auf der Registerkarte **Datenquelle** aus.
2. Klicken Sie auf **Hinzufügen** oder ziehen Sie Elemente per Drag-and-Drop, um Ihr Formular zu erstellen.

   ![Screenshot des universellen Editors mit schemabasiertem Formular](/help/edge/docs/forms/universal-editor/assets/ue-form.png)

3. Fügen Sie Datenbindungen zu Formularfeldern hinzu:

   - Wählen Sie ein Formularfeld aus.
   - Suchen Sie im Bedienfeld **Eigenschaften** nach der Eigenschaft **Bindungsverweis**.
   - Wählen Sie den entsprechenden Datenbindungsverweis aus.

     ![Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding1.png)

+++

+++Phase 3: Konfigurieren des Vorbefüllungsdienstes

### Schritt 6: Aktivieren Sie erforderliche Erweiterungen

Stellen Sie sicher, dass folgende Erweiterungen im universellen Editor aktiviert sind:

1. **Erweiterung für AEM-Formulareigenschaften**

   - Öffnen Sie **Extension Manager** im universellen Editor.
   - Aktivieren Sie die Erweiterung **AEM-Formulareigenschaften**.

   ![Symbol „Formulareigenschaften“](/help/edge/docs/forms/universal-editor/assets/form-edit-properties.png)

1. **Erweiterung „Datenquellen“**

   - Aktivieren Sie die Erweiterung **Datenquellen**, wenn Sie das Symbol **Datenquellen** nicht sehen können.

   ![Screenshot von Extension Manager des universellen Editors](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

   >[!TIP]
   >
   > Genaue Anweisungen zum Verwalten von Erweiterungen finden Sie unter [Extension Manager – Highlights der Funktionen](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

### Schritt 7: Konfigurieren Sie den Vorbefüllungsdienst

1. Öffnen Sie Ihr adaptives Formular im universellen Editor.
2. Klicken Sie auf das Erweiterungssymbol **AEM-Formulareigenschaften**.

   ![Symbol „Formulareigenschaften auswählen“](/help/edge/docs/forms/universal-editor/assets/select-fdm-properties-icon.png)

3. Klicken Sie auf die Registerkarte **Vorbefüllung**.
4. Wählen Sie **Vorbefüllungsdienst für Formulardatenmodell**.

   ![Vorbefüllungsdienst auswählen](/help/edge/docs/forms/universal-editor/assets/select-fdm-prefill.png)

5. Klicken Sie auf **Speichern und schließen**.

+++

+++Phase 4: Testen der Vorbefüllungskonfiguration

### Schritt 8: Führen Sie eine Vorschau und Tests durch

1. Gehen Sie zu **Formulare** > **Formulare und Dokumente**.
2. Wählen Sie Ihr adaptives Formular aus.
3. Wählen Sie **Vorschau als HTML**.
4. Testen Sie das Vorbefüllen durch Anhängen von Parametern an die URL:

   https://your-preview-url.com?`<bindreferencefield>`=`<value>`

   **Beispiel:**

   https://your-preview-url.com?petid=12345

   ![Vorfüllen eines Formulars](/help/edge/docs/forms/universal-editor/assets/prefill-form.png)

Das Formular sollte anhand des angegebenen Parameters automatisch mit Daten ausgefüllt werden.

+++

## Beispiele

### Beispieldatenstrukturen zum Vorbefüllen

**JSON-Beispiel für ein FDM-basiertes Formular:**

```
  {
    "afBoundData": {
      "user": {
        "firstName": "John",
        "lastName": "Doe",
        "email": "john.doe@example.com",
        "phone": "+1-555-0123"
      }
    },
    "afUnBoundData": {
      "additionalInfo": "User preferences loaded"
    }
  }
```

**XML-Beispiel für ein XFA-basiertes Formular:**

```
  <?xml version="1.0" encoding="UTF-8"?>
  <afData>
    <afBoundData>
      <user>
        <firstName>John</firstName>
        <lastName>Doe</lastName>
        <email>john.doe@example.com</email>
      </user>
    </afBoundData>
  </afData>
```

### Beispiel-URLs zum Vorbefüllen

Die folgenden URLs dienen nur zu Veranschaulichungszwecken und funktionieren nicht im Istzustand. Ersetzen Sie den Host und die Parameter durch diejenigen, die für Ihre Umgebung beim Testen der Vorbefüllungsfunktion relevant sind.

**Einfacher Vorbefüllungstest:**

`https://preview.example.com/form.html?userId=12345`

**Test mit mehreren Parametern:**

`https://preview.example.com/form.html?userId=12345&category=premium`


## Fehlerbehebung

+++Häufige Probleme und Lösungen

| Problem | Mögliche Ursache | Lösung |
|-------|----------------|----------|
| **Formularfelder werden nicht vorbefüllt** | Ungültige `bindRef`-Werte | Überprüfen Sie, ob `bindRef` genau mit FDM-Feldnamen übereinstimmt |
| **Datenformatfehler** | Nicht übereinstimmende Datenstruktur | Stellen Sie sicher, dass die Vorbefüllungsdaten mit dem Formularmodellschema übereinstimmen |
| **Dienst nicht gefunden** | Probleme mit der FDM-Konfiguration | Überprüfen Sie, ob FDM-Dienste ordnungsgemäß konfiguriert und gespeichert sind |
| **Authentifizierungsfehler** | Verbindung zur Datenquelle | Überprüfen Sie die Anmeldedaten und Verbindung der Datenquelle |
| **Partielles Laden von Daten** | Fehlende Feldzuordnungen | Stellen Sie sicher, dass alle erforderlichen Felder über korrekte Datenbindungen verfügen |

+++

+++Debugging-Schritte

1. **Überprüfen der FDM-Konfiguration:**

   - Prüfen Sie, ob die Dienste korrekt konfiguriert sind
   - Testen Sie FDM-Services unabhängig voneinander
   - Überprüfen Sie die Verbindung der Datenquelle

2. **Überprüfen der Formularkonfiguration:**

   - Prüfen Sie, ob das Formular mit dem richtigen FDM verknüpft ist
   - Überprüfen Sie die `bindRef`-Werte von Feldern
   - Testformular ohne vorheriges Vorbefüllen

3. **Testen von Datenfluss:**

   - Verwenden Sie die Entwickler-Tools des Browsers, um Netzwerkanfragen zu überprüfen
   - Überprüfen Sie die Konsole auf JavaScript-Fehler
   - Validieren Sie das Antwortdatenformat

4. **Häufige Fehlermeldungen:**

   - „Vorbefüllungsdienst nicht gefunden“: Überprüfen Sie die Dienstkonfiguration
   - „Datenbindung fehlgeschlagen“: Überprüfen Sie die Richtigkeit von `bindRef`
   - „Ungültiges Datenformat“: Stellen Sie sicher, dass die Daten mit dem Schema übereinstimmen

+++

## Best Practices

+++Best Practices für die Konfiguration

- **Beschreibende Benennung verwenden**: Benennen Sie FDMs und Dienste klar
- **Datenschemata validieren**: Stellen Sie sicher, dass die Datenstruktur den Formularanforderungen entspricht
- **Inkrementell testen**: Konfigurieren und testen Sie jeweils ein Feld
- **Dokumentzuordnungen**: Überwachen Sie Zuordnungen von Feldern zu Daten

+++

+++Leistungsoptimierung

- **Datenvolumen minimieren**: Lassen Sie nur erforderliche Felder vorbefüllen
- **Zwischenspeichern verwenden**: Konfigurieren Sie ein geeignetes Zwischenspeichern für häufig aufgerufene Daten
- **Abfragen optimieren**: Stellen Sie sicher, dass Datenbankabfragen effizient sind
- **Leistung überwachen**: Verfolgen Sie die Ladezeiten von Formularen mit aktivierter Vorbefüllung

+++

+++Sicherheitsüberlegungen

- **Eingabeparameter überprüfen**: Sie sollten URL-Parameter stets überprüfen
- **Daten bereinigen**: Bereinigen Sie Daten, bevor Formulare vorbefüllt werden
- **Zugriffssteuerungen implementieren**: Sorgen Sie dafür, dass Benutzende nur auf ihre eigenen Daten zugreifen können
- **HTTPS verwenden**: Sie sollten stets sichere Verbindungen für die Datenübertragung nutzen

+++

+++Richtlinien für das Anwendererlebnis

- **Feedback geben**: Zeigen Sie bei Datenabrufen den Ladestatus an
- **Mit Fehlern elegant umgehen**: Zeigen Sie hilfreiche Fehlermeldungen an
- **Überschreibungen zulassen**: Benutzende können vorbefüllte Daten ändern
- **Konsistenz gewährleisten**: Nutzen Sie in allen Formularen ein konsistentes Vorbefüllungsverhalten

+++

## Häufig gestellte Fragen

+++Wie kann ich testen, ob das Vorbefüllen ordnungsgemäß funktioniert?

Zeigen Sie eine Vorschau Ihres Formulars an und fügen Sie Vorbefüllungsparameter in folgendem Format an die URL an: `?<bindreferencefield>=<value>`. Stellen Sie sicher, dass das Feld über eine gültige `bindRef` verfügt, die zu Ihrer Datenstruktur passt. Verwenden Sie die Entwickler-Tools des Browsers, um Netzwerkanfragen zu untersuchen und zu prüfen, ob Daten korrekt abgerufen werden.

+++

+++Welche Datenformate werden beim Vorbefüllen von adaptiven Formularen unterstützt?

Adaptive Formulare unterstützen je nach Formularmodell verschiedene Formate:

- **XFA-Formulare**: XML, die mit dem XFA-Schema übereinstimmt
- **JSON-Schemaformulare**: JSON-Daten, die mit dem Schema konform sind
- **FDM-Formulare**: JSON, das der Datenmodellstruktur zugeordnet ist
- **XML-Schemaformulare**: XML, die mit der Schemastruktur übereinstimmt

+++

+++Kann ich sowohl gebundene als auch ungebundene Felder vorbefüllen?

Ja, Sie können beide Arten von Feldern vorbefüllen. Gebundene Felder verwenden den Abschnitt `afBoundData` und müssen mit Ihrem Formularmodellschema übereinstimmen. Ungebundene Felder verwenden den Abschnitt `afUnBoundData` und können zusätzliche Daten enthalten.

+++

+++Was soll ich tun, wenn nur einige Felder vorbefüllt werden?

Überprüfen Sie, ob alle Felder richtige `bindRef`-Werte haben, die genau mit Ihrem FDM übereinstimmen. Sorgen Sie dafür, dass Ihre Datenquelle alle erforderlichen Felder enthält und die Datenstruktur mit Ihrem Formularmodellschema übereinstimmt.

+++

+++Kann ich verschiedene Vorbefüllungsdienste in einem Formular verwenden?

Pro Formular kann ein primärer Vorbefüllungsdienst konfiguriert werden. Sie können innerhalb eines Formulardatenmodells jedoch verschiedene Datenquellen kombinieren, um ähnliche Funktionen zu erzielen.

+++

+++Wie handhabe ich die Authentifizierung für Vorbefüllungsdienste?

Die Authentifizierung hängt von Ihrer Datenquellenkonfiguration ab. Konfigurieren Sie für FDM-basiertes Vorbefüllen die Authentifizierung in Ihren Datenquelleneinstellungen. Für das Vorbefüllen von Entwürfen müssen Benutzende in der Regel angemeldet sein, um auf ihre gespeicherten Entwürfe zugreifen zu können.

+++



## Verwandte Themen

- [Integrieren von Formularen mit dem Formulardatenmodell im universellen Editor](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)
- [Erstellen von Formulardatenmodellen](/help/forms/create-form-data-models.md)
- [Arbeiten mit einem Formulardatenmodell (FDM)](/help/forms/work-with-form-data-model.md)
- [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md)
- [Erste Schritte mit Edge Delivery Services für AEM Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
