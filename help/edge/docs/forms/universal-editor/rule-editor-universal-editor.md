---
title: Regeleditor für Dynamic Forms im universellen Editor
description: Erstellen dynamischer, intelligenter Formulare mit dem Regeleditor im universellen Editor Hinzufügen von bedingter Logik, Berechnungen und interaktiven Verhaltensweisen ohne Programmierung.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: 44a8d5d5fdd2919d6d170638c7b5819c898dcefe
workflow-type: tm+mt
source-wordcount: '2598'
ht-degree: 1%

---


# Regeleditor für Dynamic Forms im universellen Editor

Mit dem Regeleditor können Autoren statische Formulare in responsive, intelligente Erlebnisse umwandeln - ohne Code zu schreiben. Sie können Felder bedingt anzeigen, Berechnungen durchführen, Daten validieren, Benutzer durch Flüsse führen und Geschäftslogik integrieren, die sich je nach Benutzertyp anpasst.

## Lerninhalt

Am Ende dieses Handbuchs haben Sie folgende Möglichkeiten:

- So funktionieren Regeln und wann verschiedene Regeltypen verwendet werden sollten
- Aktivieren des Regeleditors im universellen Editor und Zugreifen auf ihn
- Erstellen einer bedingten Logik zum dynamischen Anzeigen oder Ausblenden von Feldern
- Implementieren automatisierter Berechnungen und Datenvalidierung
- Erstellen benutzerdefinierter Funktionen für komplexe Geschäftsregeln
- Anwendung von Best Practices für Leistung, Wartungsfreundlichkeit und Benutzerfreundlichkeit

## Wozu dient der Regeleditor?

- **Bedingte Logik**: Zeigen Sie relevante Felder nur an, wenn sie benötigt werden, um Lärm und kognitive Belastung zu reduzieren.
- **Dynamische Berechnungen**: Werte (Summen, Sätze, Steuern) werden je nach Benutzertyp automatisch berechnet.
- **Datenvalidierung**: Frühzeitige Fehlervermeidung durch Echtzeit-Prüfungen und Löschen von Nachrichten.
- **Geführte Erlebnisse**: Führen Sie Benutzer durch logische Schritte (Assistenten, Verzweigungen).
- **Erstellen ohne Code**: Konfigurieren Sie leistungsstarkes Verhalten über eine visuelle Oberfläche.

Häufige Szenarien sind Steuerrechner, Schätzer für Darlehen und Prämien, Fördermittelflüsse, mehrstufige Anträge und Umfragen mit bedingten Fragen.

## Funktionsweise von Regeln

Eine Regel definiert, was passieren soll, wenn eine Bedingung erfüllt ist. Grundsätzlich besteht eine Regel aus zwei Teilen:

- **Bedingung**: Eine Anweisung, die als „true“ oder „false“ ausgewertet wird.
   - Beispiele: „Einkommen > 50.000“, „Abdeckung = &#39;Ja&#39;&quot;, „Feld ist leer“
- **Action**: Was passiert, wenn die Bedingung wahr ist (und optional, wenn sie falsch ist).
   - Beispiele: Ein-/Ausblenden eines Felds, Festlegen/Löschen eines Werts, Validieren der Eingabe, Aktivieren/Deaktivieren einer Schaltfläche

+++ Regellogikmuster

- **Bedingung → Aktion (Wenn/Dann)**

  ```text
  WHEN Gross Salary > 50000
  THEN Show "Additional Deduction"
  ```

  Am besten geeignet für bedingte Sichtbarkeit und progressive Offenlegung.

- **Aktion ← Bedingung (wenn/nur wenn festgelegt)**

  ```text
  SET Taxable Income = Gross Salary - Deductions
  IF Deductions are applicable
  ```

  Optimiert für Berechnungen und Datenumwandlungen.

- **Wenn → dann → Sonst (alternative Aktion)**

  ```text
  IF Income > 50000
  THEN Show "High Income" fields
  ELSE Show "Standard Income" fields
  ```

  Optimiert für Verzweigungslogik und sich gegenseitig ausschließende Flüsse.

+++

+++ Beispiel aus der Praxis

- **Bedingung**: „Bruttogehalt übersteigt 50.000 $&quot;
- **Primäre Aktion**: „Zusätzlichen Abzug“ anzeigen
- **Alternative Aktion**: „Zusätzlicher Abzug“ ausblenden
- **Ergebnis**: Benutzende sehen nur die Felder, die für sie gelten

+++

## Voraussetzungen


+++ Zugriffsanforderungen

**Grundlegende Berechtigungen und Einrichtung**:

- **AEM as a Cloud Service**: Authoring-Zugriff mit Berechtigungen zur Formularbearbeitung
- **Universeller Editor**: In Ihrer Umgebung installiert und konfiguriert
- **Erweiterung des Regeleditors**: Aktiviert über [Extension Manager](/help/implementing/developing/extending/extension-manager.md)
- **Berechtigungen zur Formularbearbeitung**: Möglichkeit zum Erstellen und Ändern von Formularkomponenten im universellen Editor

**Überprüfungsschritte**:

1. Bestätigen Sie, dass Sie über Ihre AEM Sites-Konsole auf den universellen Editor zugreifen können
2. Überprüfen Sie, ob Sie Formularkomponenten erstellen und bearbeiten können
3. Vergewissern Sie sich, dass bei der Auswahl von Formularkomponenten das Symbol ![Regel-Editor](/help/forms/assets/edit-rules-icon.svg) angezeigt wird

+++

+++ Technische Anforderungen

**Erforderliche Kenntnisse und Fähigkeiten**:

- **Professionalität des universellen Editors**: Erfahrung beim Erstellen von Formularen mit Texteingaben, Dropdown-Menüs und grundlegenden Feldeigenschaften
- **Verständnis von Business-**: Möglichkeit, bedingte Anforderungen und Validierungsregeln für Ihren spezifischen Anwendungsfall zu definieren
- **Vertrautheit** Formularkomponenten: Kenntnisse in Feldtypen (Text, Zahl, Dropdown), Eigenschaften (erforderlich, sichtbar, schreibgeschützt) und Formularstruktur

**Optional für erweiterte Verwendung**:

- **JavaScript-Grundlagen**: Nur zum Erstellen benutzerdefinierter Funktionen (Datentypen, Funktionen, Grundsyntax) erforderlich
- **JSON-Verständnis**: Hilfreich für komplexe Datenmanipulationen und API-Integrationen

**Bewertungsfragen**:

- Kann man im universellen Editor ein einfaches Formular mit Texteingaben und einer Senden-Schaltfläche erstellen?
- Verstehen Sie, wann Felder in Ihrem Geschäftskontext erforderlich oder optional sein sollten?
- Können Sie erkennen, welche Formularelemente in Ihrem Anwendungsfall eine bedingte Sichtbarkeit benötigen?

+++

+++ Aktivieren der Erweiterung des Regeleditors

**Wichtig**: Die Erweiterung des Regeleditors ist in Umgebungen des universellen Editors nicht standardmäßig aktiviert.

**Aktivierungsschritte**:

1. Navigieren Sie zur [Extension Manager](/help/implementing/developing/extending/extension-manager.md) in Ihrer AEM-Umgebung
2. Suchen Sie die Erweiterung „Regel-Editor“ in der Liste der verfügbaren Erweiterungen
3. Klicken Sie auf **Aktivieren** und bestätigen Sie die Aktivierung
4. Warten Sie, bis das System aktualisiert wurde (kann 1-2 Minuten dauern)

**Verifizierung**:

- Nach der Aktivierung wird das Symbol „Regeleditor“ angezeigt, wenn Sie eine Formularkomponente auswählen: ![edit-rules](/help/forms/assets/edit-rules-icon.svg)

![Regeleditor für den universellen Editor](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)
Abbildung: Das Symbol „Regeleditor“ wird angezeigt, wenn Sie Formularkomponenten auswählen

So öffnen Sie den Regeleditor:

1. Wählen Sie im universellen Editor eine Formularkomponente aus.
2. Klicken Sie auf das Symbol Regeleditor .
3. Der Regeleditor wird in einem Seitenbereich geöffnet.

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-for-field.png)
Abbildung: Benutzeroberfläche des Regeleditors zum Bearbeiten von Komponentenregeln

>[!NOTE]
>
> In diesem Artikel verweisen „Formularkomponente“ und „Formularobjekt“ auf dieselben Elemente (z. B. Eingaben, Schaltflächen, Bedienfelder).

## Übersicht über die Benutzeroberfläche des Regeleditors

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-interface.png)
Abbildung: Vollständige Benutzeroberfläche des Regeleditors mit nummerierten Komponenten

- **Komponententitel und**: Bestätigt die ausgewählte Komponente und den aktiven Regeltyp.
- **Bedienfeld „Formularobjekte und Funktionen**:
   - Formularobjekte: Hierarchische Ansicht von Feldern und Containern für Verweise in Regeln
   - Funktionen: integrierte Hilfsfunktionen für Mathematik, Zeichenfolge, Datum und Validierung
- **Umschalten des Bedienfelds**: Blenden Sie das Bedienfeld mit den Objekten und Funktionen ein oder aus, um den Arbeitsbereich zu vergrößern
- **Visual Rule Builder**: Drag &amp; Drop, Dropdown-gesteuerter Regel-Composer
- **Controls**: Done (save), Cancel (Discard). Regeln immer vor dem Speichern testen.

+++

+++ Verwalten vorhandener Regeln

Wenn eine Komponente bereits über Regeln verfügt, können Sie:

- **Anzeigen**: Siehe Regelzusammenfassungen und Logik
- **Bearbeiten**: Bedingungen und Aktionen ändern
- **Neu anordnen**: Ändern der Ausführungsreihenfolge (von oben nach unten)
- **Aktivieren/Deaktivieren**: Regeln für Tests umschalten
- **Löschen**: Regeln sicher entfernen

>[!TIP]
>
> Spezifische Regeln sind wichtiger als allgemeine. Die Ausführung erfolgt von oben nach unten.

+++

## Verfügbare Regeltypen

Wählen Sie den Regeltyp aus, der am besten zu Ihrer Absicht passt.

+++ Bedingungslogik

- **Wenn**: Primäre Regel für komplexes bedingtes Verhalten (Bedingung → Aktion ± Sonst)
- **Ausblenden/Anzeigen**: Steuert die Sichtbarkeit basierend auf einer Bedingung (progressive Offenlegung)
- **Aktivieren/Deaktivieren**: Steuert, ob ein Feld interaktiv ist (deaktiviert beispielsweise „Senden“, bis die erforderlichen Felder gültig sind)

+++

+++ Datenmanipulation

- **Wert festlegen von**: Werte automatisch ausfüllen (z. B. Daten, Gesamtwerte, Kopien)
- **Wert löschen von**: Daten bei Änderung der Bedingungen entfernen
- **Format**: Umwandeln der Anzeigeformatierung (Währung, Telefon, Datum) ohne Änderung der gespeicherten Werte

+++

+++ Validierung

- **Validate**: Benutzerdefinierte Validierungslogik, einschließlich feldübergreifender Prüfungen und Geschäftsregeln

+++

+++ Kalkulation

- **Mathematischer Ausdruck**: Werte in Echtzeit berechnen (Summen, Steuern, Verhältnisse)

+++

+++ Benutzeroberfläche

- **Fokus festlegen**: Fokus auf ein bestimmtes Feld verschieben (sparsam verwenden)
- **Eigenschaft festlegen**: Dynamisches Ändern von Komponenteneigenschaften (Platzhalter, Optionen usw.)

+++

+++ Formularsteuerelement

- **Formular senden**: Das Formular programmgesteuert übermitteln (nur nach erfolgreicher Überprüfung)
- **Formular zurücksetzen**: Löschen und auf Anfangsstatus zurücksetzen (vor der Verwendung bestätigen)
- **Formular speichern**: Als Entwurf für später speichern (lange Formulare, mehrere Sitzungen)

+++

+++ Erweitert

- **Service aufrufen**: Externe APIs/Services aufrufen (Laden und Fehler behandeln)
- **Instanz hinzufügen/entfernen**: Wiederholbare Abschnitte verwalten (z. B. Angehörige, Adressen)
- **Navigieren zu**: Weiterleiten zu anderen Formularen/Seiten (Daten vor der Navigation beibehalten)
- **Zwischen Bedienfeldern navigieren**: Schrittnavigation und Überspringen im Assistenten „Steuerelement“
- **Ereignis auslösen**: Benutzerdefinierte Trigger-Ereignisse für Integrationen oder Analysen

+++

## Schritt-für-Schritt-Tutorial: Erstellen eines intelligenten Steuerrechners

+++ Tutorial-Übersicht

Dieses Beispiel zeigt bedingte Sichtbarkeit und automatische Berechnungen.

![Screenshot der Benutzeroberfläche des Regeleditors, der die Erstellung einer bedingten Regel mit Wenn-Dann-Logik für die Sichtbarkeit des Formularfelds zeigt](/help/edge/docs/forms/assets/rule-editor-1.png)
Abbildung: Steuerberechnungsformular mit intelligenten bedingten Feldern

Sie erstellen ein Formular, das:

1. Passt sich an Benutzereingaben an, indem relevante Felder angezeigt werden
2. Berechnet Werte in Echtzeit
3. Validiert Daten, um die Genauigkeit zu verbessern

+++

+++ Formularstruktur

| Feldname | Typ | Zweck | Verhalten |
|-------------------------|---------------|--------------------------------|-----------------------------------------|
| Bruttogehalt | Zahleneingabe | Jahreseinkommen des Nutzers | Bedingte Logik für Trigger |
| Nachabzug | Zahleneingabe | Zusätzliche Abzüge (falls förderfähig) | Nur sichtbar, wenn Gehalt > 50.000 $ |
| steuerpflichtiges Einkommen | Zahleneingabe | Berechneter Wert | Schreibgeschützt, Aktualisierungen bei Änderung |
| Steuerschuld | Zahleneingabe | Berechneter Wert | Schreibgeschützt, pauschal berechnet |

+++

+++ Business-Logik

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

+++ Schritt 1: Erstellen des Foundation-Formulars

**Ziel**: Erstellen des Basisformulars mit allen Feldern und Anfangseinstellungen.

1. **Universellen Editor öffnen**:
   - Navigieren Sie zur AEM Sites-Konsole, wählen Sie Ihre Seite aus und klicken Sie auf **Bearbeiten**
   - Stellen Sie sicher, dass [universeller Editor](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction.html) ordnungsgemäß konfiguriert ist

2. **Fügen Sie Formularkomponenten in dieser Reihenfolge hinzu**:
   - Titel (H2): „Steuerberechnungsformular“
   - Zahleneingabe: „Bruttogehalt“ (erforderlich: ja, Platzhalter: „Jahresgehalt eingeben„)
   - Zahleneingabe: „Zusätzlicher Abzug“ (erforderlich: Nein, Platzhalter: „Zusätzliche Abzüge eingeben„)
   - Zahleneingabe: „Steuerpflichtiges Einkommen“ (schreibgeschützt: ja)
   - Zahleneingabe: „Steuerschuld“ (schreibgeschützt: ja)
   - Senden-Schaltfläche: „Steuer berechnen“

3. **Konfigurieren Sie die anfänglichen Feldeigenschaften**:
   - „Zusätzlicher Abzug“ ausblenden (Einstellung „Sichtbar: Keine“ im Bedienfeld „Eigenschaften„)
   - Legen Sie „Steuerpflichtiges Einkommen“ und „Steuerpflichtig“ auf Schreibgeschützt fest: Ja

![Screenshot eines Steuerberechnungsformulars mit Eingabefeldern für Bruttogehalt, Familienstand und unterhaltsberechtigte Kinder, auf denen die Formularstruktur vor der Anwendung von Regeln veranschaulicht wird](/help/edge/docs/forms/assets/rule-editor2.png)
Abbildung: Anfängliche Formularstruktur mit konfigurierten grundlegenden Komponenten

**Checkpoint**: Sie sollten ein Formular mit allen Pflichtfeldern haben, in denen „Zusätzlicher Abzug“ ausgeblendet ist und berechnete Felder schreibgeschützt sind.

+++

+++ Schritt 2: Bedingte Sichtbarkeitsregel hinzufügen

**Ziel**: Das Feld „Zusätzlicher Abzug“ wird nur angezeigt, wenn das Bruttogehalt 50.000 USD überschreitet.

1. **Wählen Sie das Feld Bruttogehalt** und klicken Sie auf das Symbol Regel-Editor ![edit-rules](/help/forms/assets/edit-rules-icon.svg)
2. **Neue Regel erstellen**:
   - Klicken Sie auf **Erstellen**.
   - Regeltyp von „Wert festlegen von“ in &quot;**&quot; ändern**
3. **Konfigurieren Sie die Bedingung**:
   - Wählen Sie **Dropdown-Liste aus** dass größer als ist
   - Geben Sie `50000` in das Zahlenfeld ein
4. **Festlegen der Dann-Aktion**:
   - Wählen Sie **Dropdown „Aktion**&quot; aus
   - Ziehen oder wählen Sie **Feld „Zusätzliche**&quot; aus Formularobjekten
5. **Fügen Sie die Aktion Sonst hinzu**:
   - Klicken Sie auf **Abschnitt „Sonst hinzufügen“**
   - Wählen Sie **Dropdown „Aktion auswählen** aus
   - Wählen Sie **Feld „Zusätzlicher Abzug**
6. **Regel speichern**: Klicken Sie auf **Fertig**

>[!NOTE]
>
> Alternativer Ansatz: Sie können dasselbe Ergebnis erzielen, indem Sie eine Regel zum Ein-/Ausblenden direkt im Feld „Zusätzlicher Abzug“ anstelle einer Wenn-Regel für „Bruttogehalt“ erstellen.

+++

+++ Schritt 3: Berechnungsregeln hinzufügen

**Ziel**: Berechnet automatisch „Steuerpflichtiges Einkommen“ und „Steuerpflichtig“ basierend auf der Benutzereingabe.

**Konfigurieren der Berechnung des steuerpflichtigen Einkommens**:

1. **Wählen Sie das Feld „Steuerpflichtiges Einkommen** und öffnen Sie den Regeleditor
2. **Mathematischer Ausdruck erstellen**:
   - Klicken Sie **Erstellen** → wählen Sie **„Mathematischer Ausdruck“**
   - Ausdruck erstellen: **Bruttogehalt − zusätzlicher Abzug**
   - „Bruttogehalt“ in das erste Feld ziehen
   - **Operator „Minus** auswählen
   - „Zusätzlicher Abzug“ in das zweite Feld ziehen
3. **Speichern**: Klicken Sie auf **Fertig**

**Konfigurieren Sie die Berechnung der Steuerschuld**:

1. **Feld „Steuerpflichtig“ auswählen** und Regel-Editor öffnen
2. **Mathematischer Ausdruck erstellen**:
   - Klicken Sie **Erstellen** → wählen Sie **„Mathematischer Ausdruck“**
   - Ausdruck erstellen: **Steuerpflichtiges Einkommen × 10 ÷ 100**
   - „Steuerpflichtiges Einkommen“ in das erste Feld ziehen
   - Wählen Sie **Operator „Multipliziert mit**
   - `10` als Zahl eingeben
   - Klicken Sie auf **Ausdruck erweitern“**
   - Wählen Sie **Operator „dividiert durch**
   - `100` als Zahl eingeben
3. **Speichern**: Klicken Sie auf **Fertig**

+++

+++ Schritt 4: Testen des Formulars

**Überprüfen Sie Ihre Implementierung, indem Sie den vollständigen Fluss testen**:

1. **Vorschau des Formulars**: Klicken Sie im universellen Editor auf den Vorschaumodus.
2. **Testen der bedingten Logik**:
   - Bruttogehalt eingeben = `30000` → „Zusätzlicher Abzug“ sollte ausgeblendet bleiben
   - Bruttogehalt eingeben = `60000` → „Zusätzlicher Abzug“ angezeigt
3. **Testberechnungen**:
   - Bei Bruttogehalt = `60000`, zusätzlichen Abzug = `5000` eingeben
   - Überprüfen des steuerpflichtigen Einkommens = `55000` (60000 - 5000)
   - Steuerschuld prüfen = `5500` (55000 × 10%)

![Vorschau eines Formulars](/help/edge/docs/forms/assets/rule-editor-form.png)
Abbildung: Vervollständigter Steuerrechner mit bedingten Feldern und automatischen Berechnungen

**Erfolgskriterien**: Das Formular sollte Felder dynamisch ein-/ausblenden und Werte in Echtzeit berechnen, wenn Benutzertypen dies eingeben.


+++

## Erweitert: Benutzerdefinierte Funktionen

Für komplexe Geschäftslogik, die über die integrierten Funktionen hinausgeht, können Sie benutzerdefinierte JavaScript-Funktionen erstellen, die sich nahtlos in den Regel-Editor integrieren lassen.

+++ Verwendung benutzerdefinierter Funktionen

**Ideale Szenarien für benutzerdefinierte**:

- **Komplexe Berechnungen**: Mehrstufige Berechnungen, die in der Regel für mathematische Ausdrücke nicht einfach ausgedrückt werden können
- **Geschäftsspezifische Validierungen**: Benutzerdefinierte Validierungslogik, die spezifisch für Ihre Organisation oder Branche ist
- **Datenumwandlungen**: Formatkonvertierungen, Zeichenfolgenmanipulationen oder Datenanalyse
- **Externe Integrationen**: Aufrufe an interne APIs oder Services von Drittanbietern (mit Einschränkungen)

**Vorteile benutzerdefinierter Funktionen**:

- **Wiederverwendbarkeit**: Einmal schreiben, über mehrere Formulare und Regeln hinweg verwenden
- **Wartbarkeit**: Zentralisierte Logik, die einfacher zu aktualisieren und zu debuggen ist
- **Performance**: Optimierte JavaScript-Ausführung im Vergleich zu komplexen Regelketten
- **Flexibilität**: Handhabung von Randfällen und komplexen Szenarien, die nicht von Standardregeln abgedeckt werden

+++

+++ Erstellen und Implementieren benutzerdefinierter Funktionen

**Dateispeicherort**: Alle benutzerdefinierten Funktionen müssen in `/blocks/form/functions.js` in Ihrem Edge Delivery Services-Projekt definiert werden.

**Entwicklungs-**:

1. **Funktionsentwurf**
   - Verwenden Sie beschreibende, aktionsorientierte Funktionsnamen
   - Definieren Sie klare Parametertypen und Rückgabewerte
   - Grenzfälle und ungültige Eingaben elegant verarbeiten

2. **Implementierung**
   - Schreiben Sie saubere, gut kommentierte JavaScript
   - Eingabevalidierung und Fehlerbehandlung einschließen
   - Funktionen vor der Integration unabhängig testen

3. **Dokumentation**
   - Hinzufügen umfassender JSDoc-Kommentare
   - Nutzungsbeispiele und Parameterbeschreibungen einschließen
   - Dokumentieren von Einschränkungen oder Abhängigkeiten

4. **Bereitstellung**
   - Funktionen mit benannten Exporten exportieren
   - Bereitstellen in Ihrem Projekt-Repository
   - Überprüfen des Build-Abschlusses vor dem Testen

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

+++ Verwenden benutzerdefinierter Funktionen im Regeleditor

**Integrationsschritte**:

1. **Funktion zum Projekt hinzufügen**
   - Erstellen oder Bearbeiten von `/blocks/form/functions.js` im Projekt
   - Funktion in Exportanweisung aufnehmen

2. **Bereitstellen und Erstellen**
   - Übertragen von Änderungen an das Repository
   - Sicherstellen, dass der Build-Prozess erfolgreich abgeschlossen wurde
   - Zeit für CDN-Cache-Aktualisierungen zulassen

3. **Zugriff im Regeleditor**
   - Öffnen des Regeleditors für jede Formularkomponente
   - Wählen Sie **Funktionsausgabe“** in der Dropdown-Liste **Aktion auswählen**
   - Wählen Sie Ihre benutzerdefinierte Funktion aus der Liste der verfügbaren Funktionen aus
   - Konfigurieren von Funktionsparametern mithilfe von Formularfeldern oder statischen Werten

4. **Gründlich testen**
   - Vorschau des Formulars zur Überprüfung des Funktionsverhaltens
   - Testen mit verschiedenen Eingabekombinationen, einschließlich Edge-Fällen
   - Überprüfen der Auswirkungen auf die Leistung beim Laden und Interagieren von Formularen

![Benutzerdefinierte Funktion im Regeleditor](/help/edge/docs/forms/assets/custom-function-rule-editor.png)
Abbildung: Auswählen und Konfigurieren von benutzerdefinierten Funktionen in der Benutzeroberfläche des Regeleditors

**Best Practices für die Verwendung von Funktionen**:

- **Fehlerbehandlung**: Fallback-Verhalten bei Funktionsfehlern immer einschließen
- **Performance**: Profilfunktionen mit realistischen Datenmengen
- **Sicherheit**: Überprüfen Sie alle Eingaben, um Sicherheitslücken zu vermeiden
- **Testen**: Erstellen Sie Testfälle für normale und Randfälle

+++

## Best Practices für die Regelentwicklung


+++ Leistungsoptimierung

- Minimieren der Regelkomplexität; Aufspaltung großer Logik in kleine, fokussierte Regeln
- Regeln nach Häufigkeit sortieren (am häufigsten zuerst)
- Regelsätze pro Komponente verwaltbar halten
- Wiederverwendbare benutzerdefinierte Funktionen sollten dem Duplizieren von Logik vorgezogen werden

+++

+++ Anwendererlebnis

- Klare Validierung und Inline-Feedback
- Vermeiden Sie störende visuelle Änderungen. Verwenden Sie sorgfältig ein-/ausblenden.
- Testen geräteübergreifend und in Layouts

+++

+++ Entwicklungshygiene

- Testen mit Randfällen und bekannten Werten
- Browser-übergreifend überprüfen
- Dokumentieren der Absicht hinter komplexen Regeln, nicht nur der Mechanik
- Verwalten eines Regelinventars für große Formulare
- Verwenden konsistenter Namen für Komponenten und Regeln
- Version von benutzerdefinierten Funktionen und Tests in Nicht-Produktionsumgebungen

+++

## Fehlerbehebung bei Indizierungsproblemen


+++ Regeln werden nicht ausgelöst

- Überprüfen von Komponentennamen und -verweisen
- Ausführungsreihenfolge überprüfen (von oben nach unten)
- Bedingungen mit bekannten Werten validieren
- Überprüfen der Browser-Konsole auf Sperrfehler

+++

+++ Falsches Verhalten

- Überprüfen von Benutzern und Gruppierungen (AND/OR)
- Testen von Ausdrucksfragmenten einzeln
- Datentypen bestätigen (Zahlen vs. Zeichenfolgen)

+++

+++ Leistungsprobleme

- Vereinfachen tief verschachtelter Bedingungen
- Benutzerdefinierte Profilfunktionen
- Externe Aufrufe innerhalb von Regeln minimieren
- Verwenden spezifischer Selektoren und Verweise

+++

+++ Probleme mit benutzerdefinierten Funktionen

- Dateipfad bestätigen: `/blocks/form/functions.js`
- Stellen Sie sicher, dass benannte Exporte korrekt sind
- Bestätigen Sie, dass der Build Ihre Änderungen enthält
- Browser-Cache nach der Bereitstellung löschen
- Parametertypen und Fehlerbehandlung validieren

+++

+++ Integration des universellen Editors

- Bestätigen der Aktivierung der Erweiterung des Regeleditors
- Unterstützte Komponente auswählen
- Einen unterstützten Browser verwenden (Chrome, Firefox, Safari)
- Überprüfen Sie, ob die erforderlichen Berechtigungen vorliegen.

## Wichtige Einschränkungen

>[!IMPORTANT]
>
> Benutzerdefinierte Funktionsbeschränkungen:
>
> - Statische/dynamische Importe werden nicht unterstützt
> - Alle Logiken müssen sich in `/blocks/form/functions.js` befinden
> - Funktionen müssen synchron sein (keine asynchronen/wartenden oder Promises)
> - Der Zugriff auf die Browser-API ist eingeschränkt

>[!WARNING]
>
> Überlegungen zur Produktion:
>
> - In der Staging-Phase gründlich testen
> - Überwachen der Leistung nach der Bereitstellung
> - Einen Rollback-Plan für Regelprobleme haben
> - Betrachten Sie langsame Netzwerke und Geräte mit niedriger Spezifikation

## Zusammenfassung

Der Regeleditor im universellen Editor wandelt statische Formulare in intelligente, responsive Erlebnisse um, die sich in Echtzeit an Benutzereingaben anpassen. Durch die Nutzung von bedingter Logik, automatisierten Berechnungen und benutzerdefinierten Geschäftsregeln können Sie anspruchsvolle Formular-Workflows erstellen, ohne Anwendungs-Code zu schreiben.

**Wichtige Funktionen, die Sie gelernt haben**:

- **Bedingte Logik**: Felder basierend auf Benutzereingaben anzeigen und ausblenden, um fokussierte, relevante Erlebnisse zu erstellen
- **Dynamische Berechnungen**: Berechnen Sie automatisch Werte (Steuern, Gesamtsummen, Sätze), wenn Benutzer mit dem Formular interagieren
- **Datenvalidierung**: Implementieren Sie die Echtzeit-Validierung mit klaren, umsetzbaren Feedback-Nachrichten
- **Benutzerdefinierte Funktionen**: Erweitern der Funktionen mit JavaScript für komplexe Geschäftslogik und Integrationen
- **Leistungsoptimierung**: Wenden Sie Best Practices für eine verwaltbare, effiziente Regelentwicklung an

**Wert bereitgestellt**:

- **Verbessertes Benutzererlebnis**: Verringern Sie kognitive Belastung durch progressive Offenlegung und intelligente Formularflüsse
- **Weniger Fehler**: Verhindern Sie ungültige Übermittlungen durch Echtzeit-Validierung und geführte Eingabe
- **Verbesserte Effizienz**: Automatisieren von Berechnungen und Dateneingabe zur Minimierung des Benutzeraufwands
- **Wartbare Lösungen**: Erstellen Sie wiederverwendbare, gut dokumentierte Regeln, die in Ihrem gesamten Unternehmen skaliert werden können

**Geschäftsauswirkungen**:

Forms wird zu leistungsstarken Tools für die Datenerfassung, Lead-Qualifizierung und Benutzerinteraktion. Der Regeleditor ermöglicht es technisch nicht versierten Autorinnen und Autoren, eine anspruchsvolle Geschäftslogik zu implementieren, wodurch die Entwicklungskosten gesenkt und gleichzeitig die Formularausfüllungsraten und die Datenqualität verbessert werden.

+++

+++ Nächste Schritte

**Empfohlener Lernpfad**:

1. **Mit den Grundlagen beginnen**: Erstellen einfacher Einblenden-/Ausblenden-Regeln, um die grundlegenden Konzepte zu verstehen
2. **Üben mit Tutorials**: Verwenden Sie das Beispiel des Steuerrechners als Grundlage für Ihre eigenen Formulare
3. **Schrittweise Erweiterung**: Mathematische Ausdrücke und Validierungsregeln hinzufügen, wenn Ihre Konfidenz wächst
4. **Benutzerdefinierte Funktionen implementieren**: JavaScript-Funktionen für spezielle Geschäftsanforderungen entwickeln
5. **Optimieren und skalieren**: Anwendung von Best Practices bei der Leistung und Pflege der Regeldokumentation

**Zusätzliche**:

- [Dokumentation zum universellen Editor](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/universal-editor/introduction.html) für mehr Kontext
- [Extension Manager-Handbuch](/help/implementing/developing/extending/extension-manager.md) zur Aktivierung zusätzlicher Funktionen
- [Edge Delivery Services Forms](/help/edge/docs/forms/overview.md) für eine umfassende Anleitung zur Formularentwicklung

+++
