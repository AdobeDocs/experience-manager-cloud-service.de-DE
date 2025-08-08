---
title: Vorausfüllen von Feldern in adaptiven Formularen?
description: Verwenden Sie vorhandene Daten zum Vorbefüllen von Feldern eines adaptiven Formulars. Benutzer können Formulare mit Standardinformationen vorbefüllen, indem sie sich mit ihrem Social Media-Profil anmelden.
feature: Adaptive Forms, Edge Delivery Services
role: User, Developer
level: Beginner, Intermediate
time: 45-60 minutes
keywords: Vorbefüllen des adaptiven Formulars, Edge-Bereitstellungsdienste für adaptive Formulare, Automatisches Ausfüllen des adaptiven Formulars
source-git-commit: 6c93af923e600dbb20add6c5f1053c832d5a5ca0
workflow-type: tm+mt
source-wordcount: '1829'
ht-degree: 4%

---


# Konfigurieren des Vorbefüllungs-Service in adaptiven Forms mit Edge Delivery Services

Beim Vorausfüllen eines Formulars werden Formularfelder automatisch mit relevanten Daten aus externen Quellen ausgefüllt, sobald ein Benutzer das Formular öffnet. Durch die Nutzung von Informationen aus Benutzerprofilen, Datenbanken, gespeicherten Entwürfen oder anderen Backend-Systemen wird das Ausfüllen des Formulars optimiert, indem die manuelle Eingabe reduziert, Fehler minimiert und das Ausfüllen beschleunigt wird. Dies erhöht nicht nur die Benutzerzufriedenheit, sondern auch die Wahrscheinlichkeit erfolgreicher Formularübermittlungen.

## Vorteile des Vorausfüllens von Formularen

| Vorteil | Beschreibung |
|---------|-------------|
| **Schnellere Fertigstellung** | Reduziert die manuelle Dateneingabe und hilft Benutzern, Formulare schnell auszufüllen |
| **Verbessertes Anwendererlebnis** | Forms ist personalisierter und bequemer, insbesondere für wiederkehrende Benutzende |
| **Höhere Konversionsraten** | Reduziert den erforderlichen Benutzeraufwand durch weniger Formularabbrüche |
| **Weniger Eingabefehler** | Daten aus vertrauenswürdigen Quellen verringern Tippfehler und falsche Einträge |
| **Bessere Datenqualität** | Stellt strukturierte, genaue und konsistente Daten für Backend-Systeme sicher |

## Funktionsweise des Vorbefüllens

Das folgende Diagramm veranschaulicht den automatischen Vorbefüllungsprozess, der beim Öffnen eines adaptiven Formulars durch einen Benutzer auftritt:

![Prozessablauf zum Vorbefüllen von Formularen](/help/edge/docs/forms/universal-editor/assets/prefill-process-flow.svg)

Der Vorbefüllungsprozess umfasst vier wichtige Schritte:

1. **Benutzer öffnet Formular**: Benutzer greift über eine URL oder Navigation auf ein adaptives Formular zu
2. **Identifizieren von Daten - Source**: Der Vorbefüllungs-Service bestimmt die konfigurierte Datenquelle (Formulardatenmodell oder Entwurfs-Service)
3. **Daten abrufen**: Das System ruft relevante Benutzerdaten basierend auf Kontext, Parametern oder Benutzeridentifizierung ab
4. **Zuordnen und Anzeigen**: Daten werden Formularfeldern mithilfe `bindRef` Eigenschaften zugeordnet und das ausgefüllte Formular wird den Benutzenden angezeigt

Dieser automatisierte Prozess stellt sicher, dass Benutzende ein Formular mit den relevanten Informationen vorausgefüllt sehen, was das Benutzererlebnis und die Formularausfüllungsraten erheblich verbessert.

## Datenstruktur zum Vorbefüllen

Adaptive Forms unterstützen zwei Feldtypen:

- **Gebundene Felder**: Felder, die mit einer Datenquelle mit einer nicht leeren `bindRef` verbunden sind
- **Ungebundene Felder**: Eigenständige Felder mit leeren `bindRef`

Die Datenstruktur zum Vorbefüllen umfasst:

- **afBoundData**: Enthält Daten für gebundene Felder und Bereiche
- **afUnBoundData**: Enthält Daten für ungebundene Felder

Das Datenformat muss mit Ihrem Formularmodell übereinstimmen:

- **XFA-Formulare**: XML kompatibel mit dem XFA-Vorlagenschema
- **XML-Schemaformulare**: XML, die mit der Schemastruktur übereinstimmt
- **JSON-Schemaformulare**: JSON ist mit dem Schema konform
- **Formulardatenmodell (FDM)-Formulare**: JSON, das mit der FDM-Struktur übereinstimmt
- **Schemalose Formulare**: Alle Felder sind ungebunden und verwenden ungebundene XML


## Voraussetzungen

Bevor Sie Vorbefüllungs-Services konfigurieren, stellen Sie Folgendes sicher:

### Erforderliche Einrichtung

- [Für Edge Delivery Services konfiguriertes GitHub-Repository](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#create-a-new-aem-project-pre-configured-with-adaptive-forms-block)
- [Dem Projekt hinzugefügter adaptiver Forms-Block](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md#add-adaptive-forms-block-to-your-existing-aem-project)
- [Datenquelle konfiguriert](/help/forms/configure-data-sources.md)
- [Formulardatenmodell (FDM) erstellt](/help/forms/create-form-data-models.md)

### Zugriffsanforderungen

- Zugriff auf AEM Forms as a Cloud Service
- Berechtigungen zum Erstellen und Bearbeiten von Formularen
- Universeller Editor-Zugriff mit aktivierten erforderlichen Erweiterungen

>[!TIP]
>
> Sie können Formulare auch bearbeiten, um das Formulardatenmodell (FDM) in den universellen Editor zu integrieren und Daten aus verschiedenen Backend-Quellen abzurufen. Weitere Informationen finden Sie im Artikel [Integrieren von Formularen mit dem Formulardatenmodell im universellen Editor](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md) .

## Vorbefüllungs-Service-Optionen

Der universelle Editor bietet zwei Optionen für den Vorbefüllungs-Service:

| Dienst-Typ | Zweck | Datenquelle | Am besten geeignet für |
|--------------|---------|-------------|----------|
| **Formularportal-Vorbefüllungsentwurf** | Setzt teilweise ausgefüllte Formulare fort | Gespeicherte Entwürfe in Forms Portal | Fortsetzung unvollständiger Anträge |
| **Vorbefüllen des Formulardatenmodells** | Füllen von Feldern aus externen Systemen | Backend-Datenbanken über FDM | Automatisches Ausfüllen von Benutzerprofildaten |

### Detailvergleich

| Funktion | Vorbefüllungs-Service für Entwürfe | FDM-Vorbefüllungsdienst |
|---------|----------------------|---------------------|
| **Authentifizierung** | Erfordert Benutzeranmeldung für Entwurfszugriff | Konfigurierbar basierend auf Datenquelle |
| **Setup-Komplexität** | Minimale Konfiguration | FDM-Einrichtung und -Zuordnung erforderlich |
| **Datentyp** | Statisch gespeicherte Daten | Dynamische Daten in Echtzeit |
| **Anwendungsfall** | Gespeicherte Anwendungen fortsetzen | Vorbefüllen aus Benutzerprofilen oder Datenbanken |


## Konfigurieren des Vorbefüllungsdiensts für ein Formular


+++Phase 1: Einrichten des Formulardatenmodells

### Schritt 1: Erstellen Sie ein Formulardatenmodell

1. Anmelden bei der AEM Forms as a Cloud Service-Instanz
2. Navigieren Sie zu **Adobe Experience Manager** > **Forms** > **Datenintegrationen**
3. Wählen Sie **Erstellen** > **Formulardatenmodell**
4. Wählen Sie Ihre **Data Source Configuration** und wählen Sie die konfigurierte **Data Source**

   ![Formulardatenmodell erstellt](/help/edge/docs/forms/universal-editor/assets/create-fdm.png)

   >[!TIP]
   >
   > Detaillierte Anweisungen zum Erstellen von Formulardatenmodellen finden Sie unter [Erstellen eines Formulardatenmodells](/help/forms/create-form-data-models.md).

### Schritt 2: Konfigurieren von FDM-Services

1. Wechseln Sie zu **Adobe Experience Manager** > **Forms** > **Datenintegrationen**
2. Öffnen Sie das Formulardatenmodell im Bearbeitungsmodus
3. Wählen Sie ein Datenmodellobjekt aus und klicken Sie auf **Eigenschaften bearbeiten**
4. Konfigurieren von **Lese** und **Schreib**-Services für die ausgewählten Datenmodellobjekte

   ![Konfigurieren des Lese- und Schreibdiensts](/help/edge/docs/forms/universal-editor/assets/configure-reda-write-service.png)

5. Konfigurieren Sie Service-Argumente:
   - Klicken Sie auf das Bearbeitungssymbol für das Argument des Lesediensts
   - Binden Sie das Argument an **Benutzerprofilattribut**, **Anforderungsattribut** oder **Literalwert**
   - Geben Sie den Bindungswert an (z. B. `petid` für ein Heimtierregistrierungsformular)

   ![Konfigurieren des Haustier-ID-Arguments](/help/edge/docs/forms/universal-editor/assets/pet-id-arguments.png)

6. Klicken Sie **Fertig**, um das Argument zu speichern, und **Speichern**, um das FDM zu speichern

   >[!NOTE]
   >
   > Erfahren Sie mehr über das Konfigurieren von FDM[Services in (Arbeiten mit einem Formulardatenmodell (FDM)](/help/forms/work-with-form-data-model.md).

+++

+++Phase 2: Erstellen und Konfigurieren des adaptiven Formulars

### Schritt 3: Adaptives Formular erstellen

1. Navigieren Sie zu **Adobe Experience Manager** > **Forms** > **Forms und Dokumente**
1. Wählen Sie **Erstellen** > **Adaptive Forms**
1. Wählen Sie auf der Registerkarte **Source** eine Edge Delivery Services-Vorlage aus:

   ![Vorlage von Edge Delivery Services](/help/edge/assets/create-eds-forms.png)

1. Klicken Sie **Erstellen**, um den Assistenten **Formular erstellen** zu öffnen
1. Angeben der Formulardetails:

   - **Name**: Geben Sie einen beschreibenden Namen für Ihr Formular ein
   - **Title**: Geben Sie einen benutzerfreundlichen Titel an
   - **GitHub-**: Geben Sie Ihre Repository-URL ein (z. B. `https://github.com/wkndforms/edsforms`)

1. Klicken Sie auf **Erstellen**.

   ![Erstellen eines schemabasierten Formulars](/help/edge/docs/forms/universal-editor/assets/create-schema-based-form1.png)

Das Formular wird im universellen Editor zum Erstellen geöffnet.

### Schritt 4: Konfigurieren von Formulardaten in Source

1. Wählen Sie Ihr Formular aus und klicken Sie auf **Eigenschaften**

   ![Formulareigenschaften auswählen](/help/edge/docs/forms/universal-editor/assets/select-form-properties1.png)

2. Öffnen Sie die **Formularmodell** Registerkarte
3. Wählen Sie aus **Dropdown** Liste „Auswählen aus“ die Option **Formulardatenmodell (FDM)**
4. Wählen Sie das erstellte Formulardatenmodell (z. B. PetFDM) aus der Dropdown-Liste aus

   ![Registerkarte „Formularmodell auswählen“](/help/edge/docs/forms/universal-editor/assets/select-form-model1.png)

5. Klicken Sie auf **Speichern und schließen**.
6. Öffnen Sie das Formular zur Bearbeitung im universellen Editor

Die Formularelemente aus Ihrem FDM werden auf der Registerkarte **Datenquelle** des **Inhaltsbrowsers** angezeigt.

### Schritt 5: Hinzufügen der Datenbindung zu Formularfeldern

1. Wählen Sie Datenelemente auf der Registerkarte **Datenquelle** aus
2. Klicken Sie auf **Hinzufügen** oder ziehen Sie Elemente per Drag-and-Drop, um Ihr Formular zu erstellen

   ![Screenshot des universellen Editors mit schemabasierten Formularen](/help/edge/docs/forms/universal-editor/assets/ue-form.png)

3. Hinzufügen von Datenbindung zu Formularfeldern:

   - Formularfeld auswählen
   - Suchen Sie **Bedienfeld** Eigenschaften“ nach der Eigenschaft **Bindungsverweis**.
   - Wählen Sie die entsprechende Datenbindungsreferenz aus

     ![Datenbindung](/help/edge/docs/forms/universal-editor/assets/schema-based-form-data-binding1.png)

+++

+++Phase 3: Konfigurieren des Vorbefüllungs-Service

### Schritt 6: Erforderliche Erweiterungen aktivieren

Stellen Sie sicher, dass diese Erweiterungen im universellen Editor aktiviert sind:

1. **Erweiterung der AEM-Formulareigenschaften**

   - **Extension Manager** im universellen Editor öffnen
   - Aktivieren der Erweiterung **AEM Form Properties**

   ![Symbol für Formulareigenschaften](/help/edge/docs/forms/universal-editor/assets/form-edit-properties.png)

1. **Data Source-Erweiterung**

   - Aktivieren Sie **Erweiterung** Datenquelle“, wenn Sie das Symbol **Datenquellen** nicht sehen

   ![Screenshot des universellen Editors Extension Manager](/help/edge/docs/forms/universal-editor/assets/extension-manager.png)

   >[!TIP]
   >
   > Detaillierte Anweisungen zum Verwalten von Erweiterungen finden Sie unter [Extension Manager Feature Highlights](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions).

### Schritt 7: Konfigurieren des Vorbefüllungs-Service

1. Öffnen Sie Ihr adaptives Formular im universellen Editor
2. Klicken Sie auf das Erweiterungssymbol **AEM-**:

   ![Symbol „Formulareigenschaften auswählen“](/help/edge/docs/forms/universal-editor/assets/select-fdm-properties-icon.png)

3. Klicken Sie auf **Registerkarte** Vorbefüllen“
4. Wählen Sie **Vorbefüllungs-Service für Formulardatenmodell**

   ![Vorbefüllungs-Service auswählen](/help/edge/docs/forms/universal-editor/assets/select-fdm-prefill.png)

5. Klicken Sie auf **Speichern und schließen**.

+++

+++Phase 4: Testen der Vorbefüllungskonfiguration

### Schritt 8: Vorschau und Test

1. Wechseln Sie zu **Forms** > **Forms und Dokumente**
2. Auswählen des adaptiven Formulars
3. Wählen Sie **Vorschau als HTML**
4. Testen des Vorbefüllens durch Anhängen von Parametern an die URL:

   https://your-preview-url.com?&lt;bindreferencefield>=&lt;value>

   **Beispiel:**

   https://your-preview-url.com?petid=12345

   ![Formular vorbefüllen](/help/edge/docs/forms/universal-editor/assets/prefill-form.png)

Das Formular sollte basierend auf dem angegebenen Parameter automatisch mit Daten ausgefüllt werden.

+++

## Beispiele

### Beispiele für Datenstrukturen zum Vorbefüllen

**JSON-Beispiel für ein FDM-basiertes Formular:**

    &quot;
    
    &lbrace;
    „afBoundData“: &lbrace;
    „user“: &lbrace;
    „firstName“: „John“,
    „lastName“: „Doe“,
    „email“: &quot;john.doe@example.com&quot;,
    „phone“: &quot;+1-555-0123“
    &rbrace;
    &rbrace;,
    „afUnBoundData“: &lbrace;
    „additionalInfo“: „Benutzereinstellungen geladen“
    &rbrace;
    &rbrace;
    
    &quot;

**XML-Beispiel für XFA-basierte Formulare:**

    &quot;
    
    &lt;?xml version=„1.0“ encoding=„UTF-8“?>
    &lt;afData>
    &lt;afBoundData>
    &lt;user>
    &lt;firstName>John&lt;/firstName>
    &lt;lastName>Doe&lt;/lastName>
    &lt;email>john.doe@example.com&lt;/email>
    &lt;/user>
    &lt;/afBoundData>
    &lt;/afData>
    
    &quot;

### Beispiel für Vorbefüllungs-URLs

Die folgenden URLs dienen nur zu Veranschaulichungszwecken und funktionieren nicht im Istzustand. Ersetzen Sie den Host und die Parameter durch diejenigen, die für Ihre eigene Umgebung beim Testen der Vorbefüllungsfunktion relevant sind.

**Einfache Vorbefüllungsprüfung:**

`https://preview.example.com/form.html?userId=12345`

**Test mit mehreren Parametern:**

`https://preview.example.com/form.html?userId=12345&category=premium`


## Fehlerbehebung

+++Häufige Probleme und Lösungen

| Problem | Mögliche Ursache | Lösung |
|-------|----------------|----------|
| **Formularfelder werden nicht vorausgefüllt** | Falsche `bindRef` | Überprüfen, `bindRef` genau mit FDM-Feldnamen übereinstimmt |
| **Datenformatfehler** | Nicht übereinstimmende Datenstruktur | Sicherstellen, dass die Vorbefüllungsdaten mit dem Formularmodellschema übereinstimmen |
| **Dienst nicht gefunden** | FDM-Konfigurationsprobleme | Überprüfen, ob FDM-Services ordnungsgemäß konfiguriert und gespeichert sind |
| **Authentifizierungsfehler** | Datenquellenkonnektivität | Überprüfen der Anmeldeinformationen und Konnektivität der Datenquelle |
| **Partielles Laden von Daten** | Fehlende Feldzuordnungen | Sicherstellen, dass alle erforderlichen Felder über korrekte Datenbindungen verfügen |

+++

+++Debugging-Schritte

1. **Überprüfen der FDM-Konfiguration:**

   - Prüfen, ob die Dienste korrekt konfiguriert sind
   - FDM-Services unabhängig testen
   - Überprüfen der Datenquellenkonnektivität

2. **Formularkonfiguration überprüfen:**

   - Bestätigen der Verknüpfung des Formulars mit dem richtigen FDM
   - Überprüfen der `bindRef`
   - Testformular ohne Vorbefüllen

3. **Datenfluss testen:**

   - Verwenden von Browser-Entwickler-Tools zur Überprüfung von Netzwerkanfragen
   - Überprüfen der Konsole auf JavaScript-Fehler
   - Validieren des Antwortdatenformats

4. **Häufige Fehlermeldungen:**

   - „Vorbefüllungs-Service nicht gefunden“: Überprüfen der Service-Konfiguration
   - „Datenbindung fehlgeschlagen“: Überprüfen der `bindRef`
   - „Ungültiges Datenformat“: Stellen Sie sicher, dass die Daten mit dem Schema übereinstimmen

+++

## Best Practices

+++Best Practices für die Konfiguration

- **Beschreibende Benennung verwenden**: FDMs und Services klar benennen
- **Datenschemata validieren**: Stellen Sie sicher, dass die Datenstruktur den Formularanforderungen entspricht
- **Inkrementelles Testen**: Konfigurieren und Testen jeweils eines Felds
- **Dokumentzuordnungen**: verfolgen Sie Zuordnungen von Feldern zu Daten

+++

+++Leistungsoptimierung

- **Datenvolumen minimieren**: Nur erforderliche Felder vorbefüllen
- **Caching verwenden**: Konfigurieren Sie das geeignete Caching für häufig aufgerufene Daten
- **Abfragen optimieren**: Sicherstellen, dass Datenbankabfragen effizient sind
- **Überwachen der Leistung**: Verfolgen Sie die Ladezeiten von Formularen mit aktiviertem Vorbefüllen

+++

+++Sicherheitsüberlegungen

- **Eingabeparameter überprüfen**: URL-Parameter immer überprüfen
- **Daten bereinigen**: Daten bereinigen, bevor Formulare vorausgefüllt werden
- **Implementieren von Zugriffssteuerungen**: Stellen Sie sicher, dass Benutzer nur auf ihre eigenen Daten zugreifen können
- **HTTPS verwenden**: Sichere Verbindungen für die Datenübertragung immer verwenden

+++

+++Richtlinien für das Benutzererlebnis

- **Feedback geben**: Ladeanzeigen beim Datenabruf
- **Fehler elegant behandeln**: Hilfreiche Fehlermeldungen anzeigen
- **Überschreibungen zulassen**: Benutzer können vorbefüllte Daten ändern
- **Konsistenz gewährleisten**: Verwenden Sie ein konsistentes Vorbefüllungsverhalten in allen Formularen

+++

## Häufig gestellte Fragen

+++Wie kann ich testen, ob das Vorbefüllen ordnungsgemäß funktioniert?

Zeigen Sie eine Vorschau Ihres Formulars an und fügen Sie Vorbefüllungsparameter in folgendem Format an die URL an: `?<bindreferencefield>=<value>`. Stellen Sie sicher, dass das Feld über eine gültige `bindRef` verfügt, die Ihrer Datenstruktur entspricht. Verwenden Sie Browser Developer Tools, um Netzwerkanfragen zu untersuchen und um sicherzustellen, dass Daten korrekt abgerufen werden.

+++

+++Welche Datenformate werden zum Vorbefüllen von adaptivem Forms unterstützt?

Adaptive Forms unterstützen je nach Formularmodell mehrere Formate:

- **XFA-Formulare**: XML, die dem XFA-Schema entsprechen
- **JSON-Schemaformulare**: JSON-Daten sind mit dem Schema konform
- **FDM-Formulare**: JSON, das der Datenmodellstruktur zugeordnet ist
- **XML-Schemaformulare**: XML, die mit der Schemastruktur übereinstimmt

+++

+++Kann ich sowohl gebundene als auch ungebundene Felder vorbefüllen?

Ja, Sie können beide Arten von Feldern vorbefüllen. Gebundene Felder verwenden den Abschnitt `afBoundData` und müssen mit Ihrem Formularmodellschema übereinstimmen. Ungebundene Felder verwenden den `afUnBoundData` und können zusätzliche Daten enthalten.

+++

+++Was sollte ich tun, wenn nur einige Felder vorausgefüllt sind?

Überprüfen Sie, ob alle Felder richtige `bindRef` haben, die genau mit Ihrem FDM übereinstimmen. Stellen Sie sicher, dass die Datenquelle alle erforderlichen Felder enthält und dass die Datenstruktur mit Ihrem Formularmodellschema übereinstimmt.

+++

+++Wie handhabe ich die Authentifizierung für Vorbefüllungs-Services?

Die Authentifizierung hängt von Ihrer Datenquellenkonfiguration ab. Konfigurieren Sie für FDM-basiertes Vorbefüllen die Authentifizierung in Ihren Datenquelleneinstellungen. Für das Vorbefüllen von Entwürfen müssen Benutzende in der Regel angemeldet sein, um auf ihre gespeicherten Entwürfe zugreifen zu können.

+++

+++Kann ich mehrere Vorbefüllungs-Services in einem Formular verwenden?

Pro Formular kann ein primärer Vorbefüllungs-Service konfiguriert werden. Sie können jedoch verschiedene Datenquellen innerhalb eines Formulardatenmodells kombinieren, um ähnliche Funktionen zu erzielen.

+++

## Verwandte Themen

- [Integrieren von Formularen mit dem Formulardatenmodell im universellen Editor](/help/edge/docs/forms/universal-editor/integrate-forms-with-data-source.md)
- [Erstellen von Formulardatenmodellen](/help/forms/create-form-data-models.md)
- [Arbeiten mit einem Formulardatenmodell (FDM)](/help/forms/work-with-form-data-model.md)
- [Konfigurieren von Datenquellen](/help/forms/configure-data-sources.md)
- [Erste Schritte mit Edge Delivery Services für AEM Forms](/help/edge/docs/forms/universal-editor/getting-started-universal-editor.md)
