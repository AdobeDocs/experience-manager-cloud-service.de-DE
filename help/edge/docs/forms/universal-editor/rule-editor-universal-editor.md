---
title: Regeleditor für dynamische Formulare im universellen Editor
description: Erstellen Sie mit dem Regeleditor im universellen Editor dynamische, intelligente Formulare. Fügen Sie bedingte Logik, Berechnungen und interaktive Verhaltensweisen ohne Programmierung hinzu.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: 03e46bb43e684a6b7057045cf298f40f9f1fe622
workflow-type: tm+mt
source-wordcount: '2781'
ht-degree: 93%

---


# Regeleditor für dynamische Formulare im universellen Editor

Mit dem Regeleditor können Autorinnen und Autoren statische Formulare in responsive, intelligente Erlebnisse umwandeln – ohne Code verfassen zu müssen. Sie können Felder bedingt anzeigen, Berechnungen durchführen, Daten validieren, Benutzerinnen und Benutzer durch Flüsse leiten und Geschäftslogik integrieren, die sich je nach Benutzertyp anpasst.

## Lerninhalt

Am Ende dieses Handbuchs können Sie:

- Verstehen, wie Regeln funktionieren und wann verschiedene Regeltypen verwendet werden sollten
- Den Regeleditor im universellen Editor aktivieren und aufrufen
- Eine bedingte Logik zum dynamischen Anzeigen oder Ausblenden von Feldern erstellen
- Automatisierte Berechnungen und Datenvalidierung implementieren
- Benutzerdefinierte Funktionen für komplexe Geschäftsregeln erstellen
- Best Practices für Leistung, Wartungsfreundlichkeit und Benutzerfreundlichkeit anwenden

## Wozu dient der Regeleditor?

- **Bedingte Logik**: Zeigen Sie relevante Felder nur an, wenn sie benötigt werden, um Rauschen und kognitive Belastung zu reduzieren.
- **Dynamische Berechnungen**: Werte (Summen, Sätze, Steuern) werden je nach Benutzertyp automatisch berechnet.
- **Datenvalidierung**: Frühzeitige Fehlervermeidung durch Echtzeit-Prüfungen und verständliche Meldungen.
- **Geleitete Erlebnisse**: Benutzerinnen und Benutzer werden durch logische Schritte geführt (Assistenten, Verzweigungen).
- **Erstellung ohne Code**: Konfigurieren Sie effektive Verhaltensweisen über eine visuelle Oberfläche.

Gängige Szenarien sind Steuerrechner, Schätzer für Darlehen und Prämien, Fördermittelflüsse, mehrstufige Anträge und Umfragen mit bedingten Fragen.

## Funktionsweise von Regeln

Eine Regel definiert, was geschehen soll, wenn eine Bedingung erfüllt ist. Grundsätzlich besteht eine Regel aus zwei Teilen:

- **Bedingung**: Eine Anweisung, die als „true“ oder „false“ ausgewertet wird.
   - Beispiele: „Einkommen > 50.000“, „Abdeckung = Ja“, „Feld ist leer“
- **Aktion**: Was geschieht, wenn die Bedingung true ist (und optional, wenn sie false ist).
   - Beispiele: Ein-/Ausblenden eines Felds, Festlegen/Löschen eines Werts, Validieren der Eingabe, Aktivieren/Deaktivieren einer Schaltfläche

+++ Regellogikmuster

- **Bedingung → Aktion (Wenn/Dann)**

  ```text
  WHEN Gross Salary > 50000
  THEN Show "Additional Deduction"
  ```

  Am besten geeignet für bedingte Sichtbarkeit und progressive Offenlegung.

- **Aktion ← Bedingung (Festlegen wenn/Nur wenn)**

  ```text
  SET Taxable Income = Gross Salary - Deductions
  IF Deductions are applicable
  ```

  Am besten geeignet für Berechnungen und Datenumwandlungen.

- **Wenn → dann → Sonst (alternative Aktion)**

  ```text
  IF Income > 50000
  THEN Show "High Income" fields
  ELSE Show "Standard Income" fields
  ```

  Am besten geeignet für Verzweigungslogik und sich gegenseitig ausschließende Flüsse.

+++

+++ Beispiel aus der Praxis

- **Bedingung**: „Bruttogehalt übersteigt 50.000 Euro&quot;
- **Primäre Aktion**: „Zusätzlicher Abzug“ anzeigen
- **Alternative Aktion**: „Zusätzlicher Abzug“ ausblenden
- **Ergebnis**: Benutzende sehen nur die Felder, die für sie gelten

+++

## Voraussetzungen


+++ Zugriffsanforderungen

**Grundlegende Berechtigungen und Einrichtung**:

- **AEM as a Cloud Service**: Authoring-Zugriff mit Berechtigungen zur Formularbearbeitung
- **Universeller Editor**: In Ihrer Umgebung installiert und konfiguriert
- **Regeleditor-Erweiterung**: Aktiviert über [Extension Manager](/help/implementing/developing/extending/extension-manager.md)
- **Berechtigungen zur Formularbearbeitung**: Möglichkeit zum Erstellen und Ändern von Formularkomponenten im universellen Editor

**Überprüfungsschritte**:

1. Überprüfen Sie, ob Sie über Ihre AEM Sites-Konsole auf den universellen Editor zugreifen können.
2. Überprüfen Sie, ob Sie Formularkomponenten erstellen und bearbeiten können
3. Vergewissern Sie sich, dass bei der Auswahl von Formularkomponenten das Regeleditor-Symbol ![edit-rules](/help/forms/assets/edit-rules-icon.svg) angezeigt wird.

+++

+++ Technische Anforderungen

**Erforderliche Kenntnisse und Fähigkeiten**:

- **Erfahrung mit dem universellen Editor**: Erfahrung beim Erstellen von Formularen mit Texteingaben, Dropdown-Menüs und grundlegenden Feldeigenschaften
- **Verständnis von Geschäftslogik**: Fähigkeit, bedingte Anforderungen und Validierungsregeln für Ihren spezifischen Anwendungsfall zu definieren
- **Vertrautheit mit Formularkomponenten**: Kenntnisse zu Feldtypen (Text, Zahl, Dropdown), Eigenschaften (erforderlich, sichtbar, schreibgeschützt) und Formularstruktur

**Optional für erweiterte Nutzung**:

- **JavaScript-Grundlagen**: Nur zum Erstellen benutzerdefinierter Funktionen (Datentypen, Funktionen, Grundsyntax) erforderlich
- **JSON-Verständnis**: Hilfreich bei komplexen Datenmanipulationen und API-Integrationen

**Fragen zur Einschätzung**:

- Können Sie im universellen Editor ein einfaches Formular mit Texteingaben und eine Senden-Schaltfläche erstellen?
- Wissen Sie, wann Felder in Ihrem Geschäftskontext erforderlich oder optional sein sollten?
- Können Sie erkennen, welche Formularelemente in Ihrem Anwendungsfall eine bedingte Sichtbarkeit erfordern?

+++

+++ Aktivieren der Erweiterung „Regeleditor“

**Wichtig**: Die Erweiterung „Regeleditor“ ist in Umgebungen des universellen Editors nicht standardmäßig aktiviert. 

**Aktivierungsschritte**:

1. Navigieren Sie in Ihrer AEM-Umgebung zu [Extension Manager](/help/implementing/developing/extending/extension-manager.md).
2. Suchen Sie in der Liste der verfügbaren Erweiterungen nach der Erweiterung „Regeleditor“.
3. Klicken Sie auf **Aktivieren** und bestätigen Sie die Aktivierung.
4. Warten Sie, bis das System aktualisiert wurde (kann 1-2 Minuten dauern).

 **Überprüfung**:

- Nach der Aktivierung wird das Regeleditor-Symbol angezeigt, wenn Sie eine Formularkomponente auswählen: ![edit-rules](/help/forms/assets/edit-rules-icon.svg)

![Regeleditor im universellen Editor](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)
Abbildung: Das Symbol „Regeleditor“ wird angezeigt, wenn Sie Formularkomponenten auswählen.

So öffnen Sie den Regeleditor:

1. Wählen Sie im universellen Editor eine Formularkomponente aus.
2. Klicken Sie auf das Symbol „Regeleditor“.
3. Der Regeleditor wird in einem Seitenbereich geöffnet. 

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-for-field.png)
Abbildung: Benutzeroberfläche des Regeleditors zum Bearbeiten von Komponentenregeln

>[!NOTE]
>
> In diesem Artikel verweisen „Formularkomponente“ und „Formularobjekt“ auf dieselben Elemente (z. B. Eingaben, Schaltflächen, Bedienfelder).

## Übersicht über die Benutzeroberfläche des Regeleditors

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-interface.png)
Abbildung: Vollständige Benutzeroberfläche des Regeleditors mit nummerierten Komponenten

- **Komponententitel und Regeltyp**: Bestätigt die ausgewählte Komponente und den aktiven Regeltyp.
- **Bedienfeld „Formularobjekte und Funktionen“**
   - Formularobjekte: Hierarchische Ansicht von Feldern und Containern für Verweise in Regeln
   - Funktionen: integrierte Hilfsfunktionen für Mathematik, Zeichenfolge, Datum und Validierung
- **Umschalten von Bedienfeld**: Ein- oder Ausblenden des Bedienfelds für Objekte und Funktionen, um den Arbeitsbereich zu vergrößern
- **Visueller Regelgenerator**: Drag-and-Drop- sowie Dropdown-gesteuerter Regel-Composer
- **Steuerungen**: Fertig (Speichern), Abbrechen (Verwerfen). Testen Sie Regeln immer vor dem Speichern.

+++

+++ Verwalten vorhandener Regeln

Wenn eine Komponente bereits über Regeln verfügt, können Sie:

- **Anzeigen**: Regelzusammenfassungen und Logik ansehen
- **Bearbeiten**: Bedingungen und Aktionen ändern
- **Neu anordnen**: Ausführungsreihenfolge (von oben nach unten) ändern
- **Aktivieren/Deaktivieren**: Regeln für Tests umschalten
- **Löschen**: Regeln sicher entfernen

>[!TIP]
>
> Setzen Sie spezifische Regeln vor allgemeine Regeln. Die Ausführung erfolgt von oben nach unten.

+++

## Verfügbare Regeltypen

Wählen Sie den Regeltyp aus, der am besten zu Ihren Absichten passt.

+++ Bedingungslogik

- **Wenn**: Primäre Regel für komplexes bedingtes Verhalten (Bedingung → Aktion ± Sonst)
- **Ausblenden/Einblenden**: Steuert die Sichtbarkeit basierend auf einer Bedingung (progressive Offenlegung)
- **Aktivieren/Deaktivieren**: Steuert, ob ein Feld interaktiv ist (deaktiviert beispielsweise „Senden“, bis alle erforderlichen Felder gültig sind)

+++

+++ Datenmanipulation

- **Wert festlegen von**: Werte automatisch ausfüllen (z. B. Daten, Gesamtwerte, Kopien)
- **Wert löschen von**: Daten bei Änderung der Bedingungen entfernen
- **Formatieren**: Umwandeln der Anzeigeformatierung (Währung, Telefon, Datum) ohne Änderung der gespeicherten Werte

+++

+++ Validierung

- **Validieren**: Benutzerdefinierte Validierungslogik, einschließlich feldübergreifender Prüfungen und Geschäftsregeln

+++

+++ Berechnung

- **Mathematischer Ausdruck**: Berechnung von Werten in Echtzeit (Summen, Steuern, Verhältnisse)

+++

+++ Benutzeroberfläche

- **Fokus festlegen**: Fokus auf ein bestimmtes Feld verschieben (sparsam verwenden)
- **Eigenschaft festlegen**: Dynamisches Ändern von Komponenteneigenschaften (Platzhalter, Optionen usw.)

+++

+++ Formularsteuerung

- **Formular senden**: Das Formular programmgesteuert übermitteln (nur nach erfolgreicher Überprüfung)
- **Formular zurücksetzen**: Löschen und auf Anfangsstatus zurücksetzen (vor der Verwendung bestätigen)
- **Formular speichern**: Als Entwurf für später speichern (lange Formulare, mehrere Sitzungen)

+++

+++ Erweitert

- **Service aufrufen**: Externe APIs/Services aufrufen (Laden und Fehler behandeln)
- **Instanz hinzufügen/entfernen**: Wiederholbare Abschnitte verwalten (z. B. unterhaltspflichtige Kinder, Adressen)
- **Navigieren zu**: Zu anderen Formularen/Seiten weiterleiten (Daten vor der Navigation beibehalten)
- **Zwischen Bedienfeldern navigieren**: Schrittnavigation und Überspringen im Assistenten steuern
- **Ereignis auslösen**: Benutzerdefinierte Trigger-Ereignisse für Integrationen oder Analysen

+++

## Schritt-für-Schritt-Tutorial: Erstellen eines intelligenten Steuerrechners

+++ Überblick über das Tutorial

Dieses Beispiel veranschaulicht bedingte Sichtbarkeit und automatische Berechnungen.

![Screenshot der Benutzeroberfläche des Regeleditors, der die Erstellung einer bedingten Regel mit Wenn-Dann-Logik für die Sichtbarkeit von Formularfeldern zeigt](/help/edge/docs/forms/assets/rule-editor-1.png)
Abbildung: Formular zur Steuerberechnung mit intelligenten bedingten Feldern

Sie erstellen ein Formular, das:

1. Sich an Benutzereingaben anpasst, indem relevante Felder angezeigt werden
2. Werte in Echtzeit berechnet
3. Daten validiert, um die Genauigkeit zu verbessern

+++

+++ Formularstruktur

| Feldname | Typ | Zweck | Verhalten |
|-------------------------|---------------|--------------------------------|-----------------------------------------|
| Bruttogehalt | Zahleneingabe | Jahreseinkommen der Benutzerin bzw. des Benutzers | Löst bedingte Logik aus |
| Zusätzlicher Abzug | Zahleneingabe | Zusätzliche Abzüge (falls infrage kommend) | Nur sichtbar, wenn Gehalt > 50.000 Euro |
| Steuerpflichtiges Einkommen | Zahleneingabe | Berechneter Wert | Schreibgeschützt, Aktualisierungen bei Änderung |
| Steuerschuld | Zahleneingabe | Berechneter Wert | Schreibgeschützt, pauschal berechnet |

+++

+++ Geschäftslogik

- **Regel 1: Bedingte Anzeige**

  ```text
  WHEN Gross Salary > 50,000
  THEN Show "Additional Deduction"
  ELSE Hide "Additional Deduction"
  ```

- **Regel 2: Berechnung des steuerpflichtigen Einkommens**

  ```text
  SET Taxable Income = Gross Salary - Additional Deduction
  (Only when Additional Deduction applies)
  ```

- **Regel 3: Berechnung der Steuerschuld**

  ```text
  SET Tax Payable = Taxable Income × 10%
  (Simplified flat rate)
  ```

+++

+++ Schritt 1: Grundlegendes Formular erstellen

**Ziel**: Erstellen Sie das Basisformular mit allen Feldern und Anfangseinstellungen.

1. **Öffnen Sie den universellen Editor**:
   - Navigieren Sie zur AEM Sites-Konsole, wählen Sie Ihre Seite und klicken Sie auf **Bearbeiten**.
   - Stellen Sie sicher, dass der [universelle Editor](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) ordnungsgemäß konfiguriert ist.

2. **Fügen Sie Formularkomponenten in dieser Reihenfolge hinzu**:
   - Titel (H2): „Steuerberechnungsformular“
   - Zahleneingabe: „Bruttogehalt“ (erforderlich: ja, Platzhalter: „Jahresgehalt eingeben“)
   - Zahleneingabe: „Zusätzlicher Abzug“ (erforderlich: nein, Platzhalter: „Zusätzliche Abzüge eingeben“)
   - Zahleneingabe: „Steuerpflichtiges Einkommen“ (schreibgeschützt: ja)
   - Zahleneingabe: „Steuerschuld“ (schreibgeschützt: ja)
   - Senden-Schaltfläche: „Steuer berechnen“

3. **Konfigurieren Sie die anfänglichen Feldeigenschaften**:
   - „Zusätzlicher Abzug“ ausblenden (Einstellung „Sichtbar: nein“ im Bedienfeld „Eigenschaften“)
   - „Steuerpflichtiges Einkommen“ und „Steuerschuld“ auf Schreibgeschützt: ja festlegen

![Screenshot eines Steuerberechnungsformulars mit Eingabefeldern für Bruttogehalt, Familienstand und unterhaltsberechtigte Kinder, auf denen die Formularstruktur vor der Anwendung von Regeln veranschaulicht wird](/help/edge/docs/forms/assets/rule-editor2.png)
Abbildung: Anfängliche Formularstruktur mit konfigurierten Basiskomponenten

**Checkpoint**: Sie sollten ein Formular mit allen Pflichtfeldern haben, in dem „Zusätzlicher Abzug“ ausgeblendet ist und berechnete Felder schreibgeschützt sind.

+++

+++ Schritt 2: Regel für bedingte Sichtbarkeit hinzufügen

**Ziel**: Das Feld „Zusätzlicher Abzug“ wird nur angezeigt, wenn das Bruttogehalt 50.000 Euro überschreitet.

1. **Wählen Sie das Feld Bruttogehalt** und klicken Sie auf das Regeleditor-Symbol ![edit-rules](/help/forms/assets/edit-rules-icon.svg).
2. **Erstellen Sie eine neue Regel**:
   - Klicken Sie auf **Erstellen**.
   - Ändern Sie den Regeltyp von „Wert festlegen von“ in **&quot;Wenn&quot;**.
3. **Konfigurieren Sie die Bedingung**:
   - Wählen Sie in der Dropdown-Liste die Option **&quot;ist größer als&quot;**.
   - Geben Sie `50000` in das Zahlenfeld ein.
4. **Legen Sie die Dann-Aktion fest**:
   - Wählen Sie aus der Dropdown-Liste „Aktion auswählen“ die Option **&quot;Anzeigen&quot;** aus.
   - Ziehen oder wählen Sie das Feld **&quot;Zusätzlicher Abzug&quot;**&quot; aus den Formularobjekten aus.
5. **Fügen Sie die Andernfalls-Aktion hinzu**:
   - Klicken Sie auf **&quot;Andernfalls-Abschnitt hinzufügen&quot;**.
   - Wählen Sie in der Dropdown-Liste „Aktion auswählen“ die Option **&quot;Ausblenden&quot;** aus.
   - Wählen Sie das Feld **&quot;Zusätzlicher Abzug&quot;** aus.
6. **Regel speichern**: Klicken Sie auf **Fertig**.

>[!NOTE]
>
> Alternative Methode: Sie können dasselbe Ergebnis erzielen, indem Sie eine Regel zum Ein-/Ausblenden direkt im Feld „Zusätzlicher Abzug“ anstelle einer Wenn-Regel für „Bruttogehalt“ erstellen.

+++

+++ Schritt 3: Berechnungsregeln hinzufügen

**Ziel**: Berechnet basierend auf der Benutzereingabe automatisch „Steuerpflichtiges Einkommen“ und „Steuerschuld“.

**So konfigurieren Sie die Berechnung des steuerpflichtigen Einkommens**:

1. **Wählen Sie das Feld „Steuerpflichtiges Einkommen“** und öffnen Sie den Regeleditor.
2. **Mathematischen Ausdruck erstellen**:
   - Klicken Sie auf **Erstellen** → wählen Sie **&quot;Mathematischer Ausdruck&quot;**.
   - Ausdruck erstellen: **Bruttogehalt − zusätzlicher Abzug**
   - Ziehen Sie „Bruttogehalt“ in das erste Feld.
   - Wählen Sie den Operator **&quot;Minus&quot;** aus.
   - Ziehen Sie „Zusätzlicher Abzug“ in das zweite Feld.
3. **Speichern**: Klicken Sie auf **Fertig**.

**Konfigurieren Sie die Berechnung der Steuerschuld**:

1. **Wählen Sie das Feld „Steuerschuld“ aus** und öffnen Sie den Regeleditor.
2. **Mathematischen Ausdruck erstellen**:
   - Klicken Sie auf **Erstellen** → wählen Sie **&quot;Mathematischer Ausdruck&quot;**.
   - Ausdruck erstellen: **Steuerpflichtiges Einkommen × 10 ÷ 100**
   - Ziehen Sie „Steuerpflichtiges Einkommen“ in das erste Feld.
   - Wählen Sie den Operator **&quot;Multipliziert mit&quot;** aus.
   - Geben Sie `10` als Zahl ein.
   - Klicken Sie auf **“Ausdruck erweitern“**.
   - Wählen Sie den Operator **&quot;dividiert durch&quot;** aus.
   - Geben Sie `100` als Zahl ein.
3. **Speichern**: Klicken Sie auf **Fertig**.

+++

+++ Schritt 4: Formular testen

**Überprüfen Sie Ihre Implementierung, indem Sie den vollständigen Fluss testen**:

1. **Vorschau des Formulars**: Klicken Sie im universellen Editor auf den Vorschaumodus.
2. **Testen Sie die bedingte Logik**:
   - Geben Sie ein Bruttogehalt ein = `30000` → „Zusätzlicher Abzug“ sollte ausgeblendet bleiben
   - Geben Sie ein Bruttogehalt ein = `60000` → „Zusätzlicher Abzug“ sollte eingeblendet werden
3. **Testberechnungen**:
   - Bei Bruttogehalt = `60000`, zusätzlicher Abzug = `5000` eingeben
   - Steuerpflichtiges Einkommen prüfen = `55000` (60000 - 5000)
   - Steuerschuld prüfen = `5500` (55000 × 10%)

![Vorschau eines Formulars](/help/edge/docs/forms/assets/rule-editor-form.png)
Abbildung: Fertiger Steuerrechner mit bedingten Feldern und automatischen Berechnungen

**Erfolgskriterien**: Das Formular sollte Felder dynamisch ein-/ausblenden und Werte in Echtzeit berechnen, während Benutzerinnen und Benutzer Eingaben tätigen.


+++

## Erweitert: benutzerdefinierte Funktionen

Für komplexe Geschäftslogik, die über die integrierten Funktionen hinausgeht, können Sie benutzerdefinierte JavaScript-Funktionen erstellen, die sich nahtlos in den Regeleditor integrieren lassen.

+++ Verwendung benutzerdefinierter Funktionen

**Ideale Szenarien für benutzerdefinierte Funktionen**:

- **Komplexe Berechnungen**: Mehrstufige Berechnungen, die in der Regel „Mathematischer Ausdruck“ nicht einfach ausgedrückt werden können
- **Geschäftsspezifische Validierungen**: Benutzerdefinierte Validierungslogik, die für Ihr Unternehmen oder Ihre Branche spezifisch ist
- **Datenumwandlungen**: Formatkonvertierungen, Bearbeitungen von Zeichenfolgen oder Datenanalysen
- **Externe Integrationen**: Aufrufe an interne APIs oder Services von Drittanbietern (mit Einschränkungen)

**Vorteile benutzerdefinierter Funktionen**:

- **Wiederverwendbarkeit**: Einmal schreiben, über verschiedene Formulare und Regeln hinweg verwenden
- **Wartbarkeit**: Zentralisierte Logik, die einfacher zu aktualisieren und zu debuggen ist
- **Performance**: Optimierte JavaScript-Ausführung im Vergleich zu komplexen Regelketten
- **Flexibilität**: Handhabung von Grenzfällen und komplexen Szenarien, die nicht von Standardregeln abgedeckt werden

+++

+++ Erstellen und Implementieren benutzerdefinierter Funktionen

**Dateispeicherort**: Alle benutzerdefinierten Funktionen müssen in `/blocks/form/functions.js` in Ihrem Edge Delivery Services-Projekt definiert werden.

**Entwicklungs-Workflow**:

1. **Funktionsentwurf**
   - Verwenden Sie beschreibende, aktionsorientierte Funktionsnamen
   - Definieren Sie klare Parametertypen und Rückgabewerte
   - Handhaben Sie Grenzfälle und ungültige Eingaben auf elegante Weise

2. **Implementierung**
   - Schreiben Sie sauberes, gut kommentiertes JavaScript
   - Schließen Sie Eingabevalidierung und Fehlerbehandlung ein
   - Testen Sie Funktionen unabhängig vor der Integration

3. **Dokumentation**
   - Fügen Sie umfassende JSDoc-Kommentare hinzu
   - Schließen Sie Nutzungsbeispiele und Parameterbeschreibungen ein
   - Dokumentieren Sie Einschränkungen oder Abhängigkeiten

4. **Bereitstellung**
   - Exportieren Sie Funktionen mit benannten Exporten
   - Stellen Sie in Ihrem Projekt-Repository bereit
   - Überprüfen Sie den Build-Abschluss vor dem Testen

**Beispielimplementierung**:

```javascript
/**
 * Concatenates first and last name with proper formatting
 * @name getFullName
 * @description Combines first and last name, handles edge cases like missing values
 * @param {string} firstName - The person's first name
 * @param {string} lastName - The person's last name  
 * @returns {string} Formatted full name or empty string if both inputs are invalid
 */
function getFullName(firstName, lastName) {
  // Handle null, undefined, or empty string inputs
  const first = (firstName || '').toString().trim();
  const last = (lastName || '').toString().trim();
  
  return `${first} ${last}`.trim();
}

/**
 * Calculates the number of days between two dates
 * @name days
 * @description Computes absolute difference in days, handles various date input formats
 * @param {Date|string} endDate - End date (Date object or ISO string)
 * @param {Date|string} startDate - Start date (Date object or ISO string)
 * @returns {number} Number of days between dates, 0 if inputs are invalid
 */
function days(endDate, startDate) {
  // Convert string inputs to Date objects
  const start = typeof startDate === 'string' ? new Date(startDate) : startDate;
  const end = typeof endDate === 'string' ? new Date(endDate) : endDate;

  // Validate date objects
  if (Number.isNaN(start.getTime()) || Number.isNaN(end.getTime())) {
    return 0;
  }

  // Calculate absolute difference in milliseconds, then convert to days
  const diffInMs = Math.abs(end.getTime() - start.getTime());
  return Math.floor(diffInMs / (1000 * 60 * 60 * 24));
}

// Export functions for use in Rule Editor
export { getFullName, days };
```

![Hinzufügen benutzerdefinierter Funktionen](/help/edge/docs/forms/assets/create-custom-function.png)
Abbildung: Hinzufügen benutzerdefinierter Funktionen zur Datei „features.js“

+++

+++ Verwendung benutzerdefinierter Funktionen im Regeleditor

**Integrationsschritte**:

1. **Funktion zu Projekt hinzufügen**
   - `/blocks/form/functions.js` im Projekt erstellen oder bearbeiten
   - Funktion in Exportanweisung aufnehmen

2. **Bereitstellen und aufbauen**
   - Änderungen an das Repository übertragen
   - Sicherstellen, dass der Build-Prozess erfolgreich abgeschlossen wurde
   - Zeit für CDN-Cache-Aktualisierungen lassen

3. **Aufrufen im Regeleditor**
   - Öffnen des Regeleditors für jede Formularkomponente
   - Wählen Sie **“Funktionsausgabe“** in der Dropdown-Liste **Aktion auswählen**.
   - Wählen Sie Ihre benutzerdefinierte Funktion aus der Liste der verfügbaren Funktionen aus.
   - Konfigurieren Sie Funktionsparameter mithilfe von Formularfeldern oder statischen Werten.

4. **Führen Sie gründliche Tests durch.**
   - Sehen Sie sich zur Überprüfung des Funktionsverhaltens eine Vorschau des Formulars an.
   - Testen Sie mit verschiedenen Eingabekombinationen, einschließlich Grenzfällen.
   - Überprüfen Sie die Auswirkungen auf die Leistung beim Laden von und Interagieren mit Formularen.

![Benutzerdefinierte Funktion im Regeleditor](/help/edge/docs/forms/assets/custom-function-rule-editor.png)
Abbildung: Auswählen und Konfigurieren von benutzerdefinierten Funktionen in der Benutzeroberfläche des Regeleditors


**Best Practices für den Einsatz von Funktionen**:

- **Fehlerbehandlung**: Fallback-Verhalten bei Funktionsfehlern immer einschließen
- **Performance**: Profilfunktionen mit realistischen Datenmengen
- **Sicherheit**: Alle Eingaben überprüfen, um Sicherheitslücken zu verhindern
- **Testen**: Testfälle für normale Fälle und Grenzfälle erstellen

+++


### Statische Importe für benutzerdefinierte Funktionen

Der Regeleditor des universellen Editors unterstützt statische Importe, sodass Sie wiederverwendbare Logik über mehrere Dateien und Formulare hinweg organisieren können. Anstatt alle benutzerdefinierten Funktionen in einer Datei (/blocks/form/functions.js) zu speichern, können Sie Funktionen aus anderen Modulen importieren.
Beispiel: Funktionen aus einer externen Datei importieren
Beachten Sie die folgende Ordnerstruktur:

```
      form
      ┣ commonLib
      ┃ ┗ functions.js
      ┣ rules
      ┃ ┗ _form.json
      ┣ form.js
      ┗ functions.js
```

Sie können Funktionen aus `commonLib/functions.js` wie unten dargestellt in Ihre `functions.js` importieren:

```
`import {days} from './commonLib/functions';
/**
 * Get Full Name
 * @name getFullName Concats first name and last name
 * @param {string} firstname in String format
 * @param {string} lastname in String format
 * @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

// Export multiple functions for use in Rule Editor
export { getFullName, days};
```

### Organisieren von benutzerdefinierten Funktionen in verschiedenen Forms

Sie können verschiedene Funktionssätze in separaten Dateien oder Ordnern erstellen und diese nach Bedarf exportieren:

- Wenn Sie möchten, dass bestimmte Funktionen nur in bestimmten Formularen verfügbar sind, können Sie den Pfad zur Funktionsdatei in der Formularkonfiguration angeben.

- Wenn das Textfeld für den Pfad leer gelassen wird, lädt der Regeleditor standardmäßig Funktionen aus `/blocks/form/functions.js`

![Benutzerdefinierte Funktion in UE](/help/forms/assets/custom-function-in-ue.png){width=50%}

Im obigen Screenshot wird der Pfad der benutzerdefinierten Funktion im Textfeld Benutzerdefinierter Funktionspfad hinzugefügt. Die benutzerdefinierten Funktionen für dieses Formular werden aus der angegebenen Datei geladen (`cc_function.js`).

Dies ermöglicht Flexibilität, da Funktionen über mehrere Formulare hinweg gemeinsam genutzt oder je Formular isoliert werden können.

## Best Practices für die Regelentwicklung


+++ Leistungsoptimierung

- Regelkomplexität minimieren; umfangreiche Logik in kleine, fokussierte Regeln aufspalten
- Regeln nach Häufigkeit sortieren (am häufigsten zuerst)
- Regelsätze pro Komponente verwaltbar halten
- Wiederverwendbare benutzerdefinierte Funktionen sollten dem Duplizieren von Logik vorgezogen werden

+++

+++ Anwendererlebnis

- Sorgen Sie für klare Validierung und Inline-Feedback
- Vermeiden Sie störende visuelle Änderungen; verwenden Sie Ein-/Ausblenden sorgfältig
- Testen Sie über verschiedene Geräte und Layouts hinweg

+++

+++ Entwicklungshygiene

- Testen Sie mit Grenzfällen und bekannten Werten
- Überprüfen Sie Browser-übergreifend
- Dokumentieren Sie die Absichten hinter komplexen Regeln, nicht nur die Mechanik
- Verwalten Sie ein Regelinventar für große Formulare
- Verwenden Sie konsistente Namen für Komponenten und Regeln
- Versionieren Sie benutzerdefinierte Funktionen und Tests in Nicht-Produktionsumgebungen

+++

## Fehlerbehebung bei häufigen Problemen


+++ Regeln werden nicht ausgelöst

- Überprüfen Sie Komponentennamen und -verweise
- Überprüfen Sie die Ausführungsreihenfolge (von oben nach unten)
- Validieren Sie die Bedingungen mit bekannten Werten
- Überprüfen Sie die Browser-Konsole auf Sperrfehler

+++

+++ Falsches Verhalten

- Überprüfen Sie Operatoren und Gruppierungen (AND/OR)
- Testen Sie Ausdrucksfragmente einzeln
- Überprüfen Sie Datentypen (Zahlen vs. Zeichenfolgen)

+++

+++ Leistungsprobleme

- Vereinfachen Sie tief verschachtelter Bedingungen
- Profilieren Sie benutzerdefinierte Funktionen
- Minimieren Sie externe Aufrufe innerhalb von Regeln
- Verwenden Sie spezifische Selektoren und Verweise

+++

+++ Probleme mit benutzerdefinierten Funktionen

- Überprüfen Sie den Dateipfad: `/blocks/form/functions.js`
- Stellen Sie sicher, dass benannte Exporte korrekt sind
- Prüfen Sie, ob der Build Ihre Änderungen enthält
- Löschen Sie den Browser-Cache nach der Bereitstellung
- Validieren Sie Parametertypen und Fehlerbehandlung

+++

+++ Integration des universellen Editors

- Überprüfen Sie, ob die Erweiterung „Regeleditor“ aktiviert ist
- Wählen Sie eine unterstützte Komponente aus
- Verwenden Sie einen unterstützten Browser (Chrome, Firefox, Safari)
- Überprüfen Sie, ob die erforderlichen Berechtigungen vorliegen

## Wichtige Einschränkungen

>[!IMPORTANT]
>
> Einschränkungen bei benutzerdefinierten Funktionen:
>
> - Statische/dynamische Importe werden nicht unterstützt
> - Alle Logiken müssen sich in `/blocks/form/functions.js` befinden
> - Funktionen müssen synchron sein (keine asynchronen/wartenden Funktionen oder Promises)
> - Der Zugriff auf die Browser-API ist eingeschränkt

>[!WARNING]
>
> Überlegungen zur Produktion:
>
> - Testen Sie in der Staging-Phase gründlich
> - Überwachen Sie die Leistung nach der Bereitstellung
> - Entwickeln Sie einen Rollback-Plan für Regelprobleme
> - Sehen Sie sich langsame Netzwerke und Geräte mit niedriger Spezifikation an

## Zusammenfassung

Der Regeleditor im universellen Editor wandelt statische Formulare in intelligente, responsive Erlebnisse um, die sich in Echtzeit an Benutzereingaben anpassen. Durch den Einsatz von bedingter Logik, automatisierten Berechnungen und benutzerdefinierten Geschäftsregeln können Sie ausgeklügelte Formular-Workflows einrichten, ohne Anwendungs-Code schreiben zu müssen.

**Wichtige Merkmale, die Sie gelernt haben**:

- **Bedingte Logik**: Felder werden je nach Benutzereingaben ein- oder ausgeblendet, sodass fokussierte, relevante Erlebnisse entstehen
- **Dynamische Berechnungen**: Werte (Steuern, Gesamtsummen, Sätze) werden automatisch berechnet, wenn Benutzende mit dem Formular interagieren
- **Datenvalidierung**: Es wird eine Echtzeit-Validierung mit klaren, umsetzbaren Feedback-Meldungen implementiert
- **Benutzerdefinierte Funktionen**: Erweitern von Funktionen mit JavaScript für komplexe Geschäftslogik und Integrationen
- **Leistungsoptimierung**: Anwenden von Best Practices für eine verwaltbare, effiziente Regelentwicklung

**Wert bereitgestellt**:

- **Verbessertes Anwendererlebnis**: Verringerung kognitiver Belastung durch progressive Offenlegung und intelligente Formularflüsse
- **Weniger Fehler**: Verhindern ungültiger Übermittlungen durch Echtzeit-Validierung und geführte Eingaben
- **Verbesserte Effizienz**: Automatisierung von Berechnungen und Dateneingaben zur Minimierung des Benutzeraufwands
- **Wartbare Lösungen**: Erstellung von wiederverwendbaren, gut dokumentierten Regeln, die in Ihrem gesamten Unternehmen skaliert werden können

**Geschäftliche Auswirkungen**:

Formulare werden zu effektiven Tools für die Datenerfassung, Lead-Qualifizierung und Benutzerinteraktion. Der Regeleditor ermöglicht es technisch nicht versierten Autorinnen und Autoren, eine ausgeklügelte Geschäftslogik zu implementieren. Dadurch werden die Entwicklungskosten gesenkt und gleichzeitig die Formularausfüllungsraten und die Datenqualität verbessert.

+++

## Nächste Schritte

**Empfohlener Lernpfad**:

1. **Mit den Grundlagen beginnen**: Erstellen Sie einfache Regeln für Einblenden/Ausblenden, um die grundlegenden Konzepte zu verstehen.
2. **Mit Tutorials üben**: Verwenden Sie das Beispiel des Steuerrechners als Grundlage für Ihre eigenen Formulare.
3. **Schrittweise erweitern**: Fügen Sie mathematische Ausdrücke und Validierungsregeln hin, sobald Sie sich sicherer fühlen.
4. **Benutzerdefinierte Funktionen implementieren**: Entwickeln Sie JavaScript-Funktionen für spezielle Geschäftsanforderungen.
5. **Optimieren und skalieren**: Wenden Sie Best Practices für Leistung an und pflegen Sie eine Regeldokumentation.

**Zusätzliche Ressourcen**:

- [Dokumentation zum universellen Editor](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction) für zusätzlichen Kontext
- [Extension Manager-Handbuch](/help/implementing/developing/extending/extension-manager.md) zur Aktivierung zusätzlicher Funktionen
- [Edge Delivery Services-Formulare](/help/edge/docs/forms/overview.md) für eine umfassende Anleitung zur Formularentwicklung

