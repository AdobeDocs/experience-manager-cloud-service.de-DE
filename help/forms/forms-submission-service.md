---
title: Forms Submission Service für Edge Delivery Services
description: Speichern von Formularübermittlungen direkt in Tabellen mithilfe des gehosteten Forms-Übermittlungs-Services von Adobe. Erfahren Sie mehr über Setup, Konfiguration und API-Nutzung für die Integration von Google Sheets, OneDrive und SharePoint.
keywords: Forms Submission Service, Edge Delivery Services Forms, Tabellenintegration, Google Sheets-Formulare, OneDrive-Formulare, SharePoint-Formulare, Formulardatenerfassung
feature: Edge Delivery Services
role: User, Developer, Admin
level: Beginner, Intermediate
hide: true
hidefromtoc: true
exl-id: 12b4edba-b7a1-4432-a299-2f59b703d583
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '1578'
ht-degree: 1%

---

# Forms Submission Service für Edge Delivery Services

Der Forms Submission Service ist eine gehostete Lösung von Adobe, mit der Formularübermittlungsdaten automatisch direkt in Ihren bevorzugten Tabellen gespeichert werden - Google Sheets, Microsoft OneDrive oder SharePoint. Dadurch entfällt die Notwendigkeit komplexer Backend-Infrastrukturen, während gleichzeitig eine Echtzeit-Datenerfassung und -Verwaltung ermöglicht wird.

>[!NOTE]
>
>**Early Access-Programm** Diese Funktion ist derzeit über Early Access verfügbar. Um den Zugriff anzufordern, senden Sie eine E-Mail an [&#128279;](mailto:aem-forms-ea@adobe.com)aem-forms-ea@adobe.com) mit den Namen Ihrer GitHub-Organisation und des Repositorys von Ihrer offiziellen Adresse.
>
>**Beispiel:** Für Repository-`https://github.com/adobe/abc` senden: Organisation = `adobe`, Repository = `abc`

## Überblick

![Forms-Sendedienst](/help/forms/assets/form-submission-service.png)
*Abbildung: Workflow für den Forms-Übermittlungs-Service - von der Formularübermittlung bis zum Tabellenspeicher*

### Wer sollte diesen Service nutzen?

**Perfekt für:**

- **Inhaltsersteller** Erstellen einfacher Datenerfassungsformulare
- **Kleine Unternehmen** die schnelle Workflows für die Erstellung von Formularen benötigen
- **Marketing-Teams** Sammeln von Lead-Informationen
- **Eventorganisatoren** Registrierung verwalten

**Alternativen in Betracht ziehen für:**

- Komplexe Workflows, die benutzerdefinierte Logik erfordern
- Unternehmensintegrationen mit Datenbanken
- Forms benötigt erweiterte Validierung oder Verarbeitung

### Häufige Anwendungsfälle

| Anwendungsfall | Beispiel | Tabellennutzung |
|----------|---------|-------------------|
| **Forms kontaktieren** | Website-Anfragen → Google Sheets | Einfache Nachverfolgung und CRM-Import |
| **Ereignisregistrierung** | Konferenzanmeldungen → Excel Online | Echtzeit-Teilnehmerverfolgung |
| **Lead-Generierung** | Newsletter-Anmeldungen → SharePoint | Marketing-Kampagnenanalyse |
| **Feedback-Sammlung** | Umfrageantworten → Google Sheets | Schnelle Datenvisualisierung |

## Wichtigste Vorteile

Der Forms Submission Service bietet mehrere Vorteile für eine optimierte Datenerfassung:

### **Vereinfachte Einrichtung**

- **Keine Backend-** erforderlich - Adobe hostet den Übermittlungsendpunkt
- **Direkte Integration** mit gängigen Tabellenkalkulationsplattformen
- **Automatische Datenzuordnung** von Formularfeldern zu Tabellenspalten

### **Echtzeit-Daten-Management**

- **Sofortige Datenerfassung** - Einreichungen werden sofort in Ihrer Tabelle angezeigt
- **Strukturierter Speicher** - Organisierte Spalten für eine einfache Analyse
- **Live-Zusammenarbeit** - Mehrere Team-Mitglieder können auf Daten zugreifen und diese analysieren

### **Integrierte Sicherheit und Zugriffskontrolle**

- **Nutzt bestehende Berechtigungen** - Verwenden Sie die Freigabesteuerelemente Ihrer Tabellenkalkulationsplattform.
- **Adobe-Managed Security** - sicherer Übermittlungsendpunkt mit Schutz auf Unternehmensniveau
- **Dateneigentum** - Ihre Daten verbleiben in der ausgewählten Tabellenkalkulationsplattform

## Voraussetzungen

Bevor Sie den Forms-Übermittlungsdienst einrichten, stellen Sie sicher, dass die folgenden Punkte erfüllt sind:

### **Technische Anforderungen**

- **GitHub-Repository** Richten Sie für Ihr Edge Delivery Services-Projekt ein, wobei der neueste adaptive Forms-Block installiert ist
- auf die Zulassungsliste setzen **Zugriffsgenehmigung** - Repository zur hinzugefügt

### **Tabellenkalkulationsplattform einrichten**


Wählen Sie eine der unterstützten Plattformen:

- **Google Sheets** - Google-Konto mit Berechtigungen zur Erstellung von Tabellen
- **Microsoft OneDrive** - Microsoft 365-Konto mit Excel Online-Zugriff
- **SharePoint** - Zugriff auf SharePoint mit Listen-/Bibliotheksberechtigungen

### **Berechtigungen und Zugriff**

- **Berechtigungen bearbeiten** für das Zielarbeitsblatt
- **Freigabefunktionen** um Zugriff auf `forms@adobe.com` zu gewähren
- **Link-Generierung** Berechtigungen für die ausgewählte Plattform

>[!TIP]
>
>**Neu bei Edge Delivery Services?** Sie mit dem [Erste Schritte-Tutorial](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial), um Ihre Projektstiftung einzurichten.

## Konfigurationsmethoden

Der Forms Submission Service bietet zwei Konfigurationsansätze. Wählen Sie die Methode aus, die am besten zu Ihrem Workflow passt:

### Wählen Sie Ihre Konfigurationsmethode

| Methode | Am besten geeignet für | Erforderliche Zeit | Fachebene |
|--------|----------|---------------|-----------------|
| **[Manuelles Setup](#manual-configuration)** | Inhaltsersteller, einmaliges Setup | 10-15 Minuten | Anfänger |
| **[API-Konfiguration](#api-configuration)** | Entwickler, automatisierte Workflows | 5-10 Minuten | Fortgeschrittene Einsteiger |

### Projekt-Setup

Bevor Sie eine dieser Methoden konfigurieren, stellen Sie sicher, dass Ihre AEM Project Foundation bereit ist:

1. **Erstellen oder aktualisieren Sie Ihr AEM-Projekt** mit dem neuesten adaptiven Forms-Block ([Erste Schritte-Tutorial](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/tutorial))

2. **Aktualisieren von`fstab.yaml`** im Projektstamm:

   ```yaml
   # Replace with the path to your shared folder
   mountpoints:
     /: https://drive.google.com/drive/folders/your-shared-folder-id
   ```


3. **Freigeben des Projektordners** für `forms@adobe.com` (Bearbeitungsberechtigungen erforderlich)

## Manuelle Konfiguration

![Workflow für den Formularübermittlungs-Service](/help/forms/assets/forms-submission-service-workflow.png)
*Abbildung: Abschließen des Workflows für die manuelle Einrichtung des Forms Submission Service*

Folgen Sie diesen Schritt-für-Schritt-Anweisungen, um Ihr Formular mit der Übermittlung von Kalkulationstabellen einzurichten:

### Schritt 1: Erstellen Sie Ihre Formulardefinition

Erstellen Sie Ihre Formularstruktur mit Google Sheets oder Microsoft Excel.

**Schritte zur Formularerstellung:**

1. **Öffnen der Tabellenkalkulationsplattform** (Google Sheets oder Microsoft Excel)
2. **Neue Tabelle erstellen** für Ihr Formularprojekt
3. **Benennen Sie Ihr Blatt** (muss entweder `helix-default` oder `shared-aem` sein)
4. **Definieren Sie Ihre Formularstruktur** mithilfe des [Handbuchs zur Formularerstellung](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms)

![Formulardefinition](/help/forms/assets/form-submission-definition.png)
*Beispiel: Formulardefinition mit Feldtypen, Beschriftungen und Validierungsregeln*

>[!IMPORTANT]
>
>**Benennungsanforderungen für Tabellen**
>
>Das Formulardefinitionsblatt muss wie folgt benannt werden:
>
>- `helix-default` (empfohlen für einzelne Formulare)
>- `shared-aem` (für Projekte mit mehreren Formularen)
>
>Andere Tabellennamen werden vom System nicht erkannt.

**Validierungs-Checkpoint:**

- Formularstruktur ist vollständig mit allen erforderlichen Feldern
- Blatt wurde korrekt benannt (`helix-default` oder `shared-aem`)
- Feldtypen und Validierungsregeln sind ordnungsgemäß konfiguriert

### Schritt 2: Erstellen des Datenerfassungsblatts

Richten Sie ein spezielles Blatt ein, um Formulardaten zur Übermittlung zu empfangen.

**Datenblatt-Setup:**

1. **Ein neues Blatt hinzufügen** zu Ihrem vorhandenen Arbeitsblatt hinzufügen
2. **Benennen Sie die Tabelle genau`incoming`** (Groß-/Kleinschreibung beachten)
3. **Einrichten von Spaltenüberschriften** die Ihren Formularfeldern entsprechen
4. **Speichern Sie die Tabelle** um sicherzustellen, dass die Änderungen erhalten bleiben

![Eingehendes Blatt](/help/forms/assets/form-submission-incoming-sheet.png)
*Beispiel: Eingehendes Blatt mit Spaltenüberschriften, die mit Formularfeldern übereinstimmen*

>[!WARNING]
>
>**Kritische Anforderung**
>
>Das Blatt muss genau `incoming` benannt sein (Kleinbuchstaben). Ohne dieses Blatt:
>
>- Formularübermittlungen werden abgelehnt
>- Es werden keine Daten gespeichert
>- Benutzern werden Übermittlungsfehler angezeigt

**Validierungs-Checkpoint:**

- `incoming` Tabelle ist in der Tabelle vorhanden
- Spaltenüberschriften entsprechen den Formularfeldnamen
- Blatt ist ordnungsgemäß gespeichert und zugänglich

>[!TIP]
>
>**Profi-Tipp** Kopieren Sie die genauen Feldnamen aus Ihrer Formulardefinition, um einen perfekten Abgleich zwischen Formularfeldern und Tabellenspalten sicherzustellen.

### Schritt 3: Freigeben eines Arbeitsblatts für Adobe Service

Gewähren Sie dem Adobe Forms Submission Service Zugriff auf Ihre Tabelle.

**Freigabeprozess:**

1. **Klicken Sie auf die** Freigeben oben rechts im Arbeitsblatt
2. **Fügen Sie das Adobe-Dienstkonto hinzu:**
   - E-Mail: `forms@adobe.com`
   - Berechtigungsstufe: **Editor** (erforderlich für das Schreiben von Daten)
3. **Senden der Freigabeeinladung**
4. **Tabellenlink kopieren** für den nächsten Schritt

![Freigeben eingehender Arbeitsblätter](/help/forms/assets/form-submission-share-incoming.png)
*Schritt-für-Schritt-Freigabeprozess für das Gewähren des Zugriffs auf Adobe-Services*

**Plattformspezifische Anweisungen:**

**Google-Arbeitsblätter:**

- `forms@adobe.com` als Editor hinzufügen
- Stellen Sie sicher, dass „Jeder mit dem Link kann anzeigen“ aktiviert ist
- Kopieren des freigabefähigen Links

**Microsoft Excel (OneDrive/SharePoint):**

- `forms@adobe.com` mit Bearbeitungsberechtigungen hinzufügen
- Setzen Sie die Linkfreigabe auf „Jeder mit dem Link kann bearbeiten“.
- Kopieren der Freigabe-URL

![Link des eingehenden Blatts kopieren](/help/forms/assets/form-submission-copy-link.png)
*Beispiel: Kopieren des Freigabe-Links für die Formularkonfiguration*

**Validierungs-Checkpoint:**

- `forms@adobe.com` hat Editor-Zugriff auf Ihre Tabelle
- Tabellenlink wird kopiert und kann verwendet werden
- Freigabeberechtigungen erlauben externen Zugriff

### Schritt 4: Formular mit Arbeitsblatt verbinden

Verknüpfen Sie Ihre Formulardefinition mit dem Übermittlungs-Arbeitsblatt.

**Form-Spreadsheet-Verbindung:**

1. **Öffnen Sie eine Formulardefinitionstabelle** (die mit `helix-default` oder `shared-aem` Blatt)
2. **Suchen Sie die Zeile „Feld senden** in Ihrer Formulardefinition
3. **Fügen Sie den kopierten Tabellenlink** das Feld Senden in die Spalte **Aktion** ein
4. **Speichern Sie die** in Ihrer Formulardefinition

![Verknüpfen einer Tabelle](/help/forms/assets/form-submission-sheet-linking.png)
*Beispiel: Verbinden der Übermittlungsaktion mit Ihrer Datenerfassungs-Tabelle*

**Formular veröffentlichen:**

1. **Öffnen von AEM Sidekick** in Ihrem Browser
2. **Vorschau des Formulars**, um die Konfiguration zu testen
3. **Formular veröffentlichen** um es live zu schalten

**Endgültige Validierung:**

- Tabellenlink wird korrekt zur Übermittlungsfeldaktion hinzugefügt
- Formulardefinition wird gespeichert und veröffentlicht
- Formularvorschau zeigt alle Felder korrekt an
- Senden-Schaltfläche ist ordnungsgemäß konfiguriert

>[!SUCCESS]
>
>**Setup abgeschlossen!** Ihr Formular ist jetzt mit dem Forms-Übermittlungsdienst verbunden. Testen Sie sie, indem Sie Beispieldaten einreichen und Ihr `incoming` überprüfen.

**Referenzmaterialien:**

- [Beispiel-Tabelle ausfüllen](/help/forms/assets/spreadsheet.xlsx) mit korrekter Konfiguration
- [Dokumentation zu AEM Sidekick](https://www.aem.live/docs/sidekick) für Anleitungen zur Veröffentlichung

## API-Konfiguration

Die API-Methode ermöglicht es Entwicklerinnen und Entwicklern, Daten programmgesteuert an den Forms Submission Service zu übermitteln, der sich ideal für automatisierte Workflows und benutzerdefinierte Integrationen eignet.

### Verwendung der API

**Perfekt für:**

- Automatisierte Datenerfassungssysteme
- Implementierungen benutzerdefinierter Formulare
- Integration in bestehende Anwendungen
- Workflows für die Massenübermittlung von Daten

### API-Voraussetzungen

Bevor Sie die API verwenden, stellen Sie Folgendes sicher:

- **Tabelleneinrichtung** abgeschlossen (einschließlich `incoming`)
- **Zugriff auf Adobe** Service`forms@adobe.com` gewährt
- **Formular-ID** aus dem veröffentlichten Formular
- **Repository-Informationen** (Organisations- und Standortname)

>[!IMPORTANT]
>
>**Erforderliche Einrichtungsschritte**
>
>Für die API ist dieselbe Tabelleneinrichtung wie für die manuelle Konfiguration erforderlich:
>
>- `incoming` muss vorhanden sein
>- `forms@adobe.com` muss Editor-Zugriff haben
>- Blatt muss über AEM Sidekick veröffentlicht werden

### API-Endpunkt und Authentifizierung

**Basis-URL:** `https://forms.adobe.com/adobe/forms/af/submit/{id}`

**Erforderliche Kopfzeilen:**

- `Content-Type: application/json`
- `x-adobe-routing: tier=live,bucket=main--[repository]--[organization]`

**API-Dokumentation:** [vollständige API-Referenz](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/)

### Verwenden von Postman

Postman bietet eine benutzerfreundliche Oberfläche zum Testen von API-Übermittlungen.

**Setup-Anweisungen:**

1. **Erstellen einer neuen POST-Anfrage** in Postman
2. **Konfigurieren des Endpunkts:** `https://forms.adobe.com/adobe/forms/af/submit/{id}`
3. **Platzhalter ersetzen:**
   - `{id}` → tatsächlichen Formular-ID
   - `[repository]` → Ihres GitHub-Repository-Namens
   - `[organization]` → GitHub-Organisation/-Benutzername

**Anfragekonfiguration:**

```json
POST https://forms.adobe.com/adobe/forms/af/submit/your-form-id

Headers:
Content-Type: application/json
x-adobe-routing: tier=live,bucket=main--your-repo--your-org

Body (JSON):
{
    "data": {
        "startDate": "2025-01-10",
        "endDate": "2025-01-25",
        "destination": "Australia",
        "class": "First Class",
        "budget": "2000",
        "amount": "1000000",
        "name": "Mary",
        "age": "35",
        "subscribe": null,
        "email": "mary@gmail.com"
    }
}
```

**Erwartete Antwort:**

- **Status-Code:** `201 Created`
- **Daten werden** sofort in Ihrem `incoming` Arbeitsblatt angezeigt

![Postman-Bildschirm](/help/forms/assets/postman-api.png)
*Beispiel: Erfolgreiche API-Übermittlung mit der Postman-Schnittstelle*

### Verwenden der Befehlszeile (cURL)

Für Entwickler, die Terminal/Eingabeaufforderung bevorzugen, verwenden Sie curl , um Daten programmgesteuert zu übermitteln.

**Befehlszeilen-Setup:**

Ersetzen Sie die folgenden Platzhalter in den folgenden Befehlen:

- `{id}` → tatsächlichen Formular-ID
- `[repository]` → Ihres GitHub-Repository-Namens
- `[organization]` → GitHub-Organisation/-Benutzername

>[!BEGINTABS]

>[!TAB macOS/Linux]

```bash
curl -X POST "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" \
  --header "Content-Type: application/json" \
  --header "x-adobe-routing: tier=live,bucket=main--your-repo--your-org" \
  --data '{
    "data": {
      "startDate": "2025-01-10",
      "endDate": "2025-01-25",
      "destination": "Australia",
      "class": "First Class",
      "budget": "2000",
      "amount": "1000000",
      "name": "Joe",
      "age": "35",
      "subscribe": null,
      "email": "joe@example.com"
    }
  }'
```

>[!TAB Windows-Eingabeaufforderung]

```cmd
curl -X POST "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" ^
  --header "Content-Type: application/json" ^
  --header "x-adobe-routing: tier=live,bucket=main--your-repo--your-org" ^
  --data "{\"data\": {\"startDate\": \"2025-01-10\", \"endDate\": \"2025-01-25\", \"destination\": \"Australia\", \"class\": \"First Class\", \"budget\": \"2000\", \"amount\": \"1000000\", \"name\": \"Joe\", \"age\": \"35\", \"subscribe\": null, \"email\": \"joe@example.com\"}}"
```

>[!TAB Windows PowerShell]

```powershell
$body = @{
  data = @{
    startDate = "2025-01-10"
    endDate = "2025-01-25"
    destination = "Australia"
    class = "First Class"
    budget = "2000"
    amount = "1000000"
    name = "Joe"
    age = "35"
    subscribe = $null
    email = "joe@example.com"
  }
} | ConvertTo-Json -Depth 3

Invoke-RestMethod -Uri "https://forms.adobe.com/adobe/forms/af/submit/your-form-id" `
  -Method POST `
  -Headers @{"Content-Type"="application/json"; "x-adobe-routing"="tier=live,bucket=main--your-repo--your-org"} `
  -Body $body
```

>[!ENDTABS]

### API-Antwort und -Verifizierung

**Erfolgreiche Antwort:**

```http
HTTP/1.1 201 Created
Connection: keep-alive
Content-Length: 0
X-Request-Id: 02a53839-2340-56a5-b238-67c23ec28f9f
X-Message-Id: 42ecb4dd-b63a-4674-8f1a-05a4a5b0372c
Date: Fri, 10 Jan 2025 13:06:10 GMT
Access-Control-Allow-Origin: *
```

**Datenüberprüfung:**

Überprüfen Sie nach erfolgreicher Übermittlung, ob die Daten in Ihrer Tabelle angezeigt werden:

![Aktualisiertes Blatt](/help/forms/assets/updated-sheet.png)
*Beispiel: Daten wurden erfolgreich über die API in das eingehende Blatt geschrieben*

**Validierung der Antwort:**

- **HTTP-Status:** `201 Created` zeigt an, dass die Übermittlung erfolgreich war
- **X-Request-Id:** Eindeutige Kennung für das Tracking der Übermittlung
- **Daten werden** Sekunden in Ihrem `incoming` angezeigt
- **Alle Formularfelder** werden ordnungsgemäß Tabellenspalten zugeordnet

## Fehlerbehebung

### Häufige Probleme und Lösungen

**Problem: 403 Forbidden Error**

```
Causes: Missing or incorrect access permissions
Solutions:
- Verify forms@adobe.com has Editor access to your spreadsheet
- Check that your repository is added to the allowlist
- Confirm the x-adobe-routing header format
```

**Problem: Fehler „404 Nicht gefunden“**

```
Causes: Incorrect Form ID or endpoint URL
Solutions:  
- Verify your Form ID is correct
- Check the API endpoint URL format
- Ensure your form is published and live
```


**Problem: Daten werden nicht in der Tabelle angezeigt**

```
Causes: Missing 'incoming' sheet or permission issues
Solutions:
- Confirm 'incoming' sheet exists (case-sensitive)
- Verify column headers match form field names exactly
- Check forms@adobe.com has edit permissions
- Ensure spreadsheet is shared properly
```


**Problem: Fehler wegen ungültigem JSON-Format**

```
Causes: Malformed request body
Solutions:
- Validate JSON syntax using online JSON validators
- Ensure proper escaping of special characters
- Check quote marks and brackets are balanced
```


### Hilfe

**Support-Kanäle:**

- **Early Access Issues:** E-Mail [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com)
- **API-Dokumentation** [Entwicklerreferenz](https://adobedocs.github.io/experience-manager-forms-cloud-service-developer-reference/references/aem-forms-submission-service/)
- **Community-Support:** [Adobe Experience League-Community](https://experienceleaguecommunities.adobe.com/)

## Nächste Schritte

Nachdem Sie nun den Forms-Übermittlungsdienst konfiguriert haben, lesen Sie die folgenden Themen:

### **Forms verbessern**

- **[Erweiterte Forms erstellen](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/getting-started-edge-delivery-services-forms/create-forms)** - Hinzufügen von Validierung, bedingter Logik und benutzerdefiniertem Stil
- **[Handbuch zu Formularkomponenten](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/edge-delivery/build-forms/forms-components)** - Verfügbare Formularfeldtypen erkunden

### **Alternative Übermittlungsmethoden**

- **[AEM-Veröffentlichungseinreichungen](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)** - Für komplexe Workflows und Unternehmensintegrationen
- **[Benutzerdefinierte Übermittlungsaktionen](/help/forms/configure-submit-actions-core-components.md)** - Erweiterte Übermittlungsverarbeitung

### **Daten-Management**

- **[Formularanalyse](/help/forms/view-understand-aem-forms-analytics-reports.md)** - Verfolgen der Formularleistung und -nutzung
- **[Datenintegration](/help/forms/configure-data-sources.md)** - Verbinden von Formularen mit Datenbanken und CRM-Systemen

## Zusammenfassung

Der Forms Submission Service bietet eine leistungsstarke, nicht auf Code basierende Lösung zur direkten Erfassung von Formulardaten in Tabellen. Zu den wichtigsten Vorteilen gehören:

- **Schnelleinrichtung** - Keine Backend-Infrastruktur erforderlich
- **Echtzeitdaten** - Sofortige Erfassung der Übermittlung
- **Flexible Plattformen** - Google Sheets, OneDrive oder SharePoint
- **API-Zugriff** - Funktionen zur programmgesteuerten Übermittlung
- **Unternehmenssicherheit** - Von Adobe verwaltete Endpunkte mit Zugriffssteuerungen

**Bereit für den Einstieg?*** Befolgen Sie das Handbuch [Manuelle Konfiguration](#manual-configuration) für eine visuelle Einrichtung oder springen Sie zur [API-Konfiguration](#api-configuration) für die programmgesteuerte Integration.