---
title: Regeleditor für Dynamic Forms im universellen Editor
description: Erstellen dynamischer, intelligenter Formulare mit dem Regeleditor im universellen Editor Hinzufügen von bedingter Logik, Berechnungen und interaktiven Verhaltensweisen ohne Programmierung.
feature: Edge Delivery Services
role: Admin, Architect, Developer
level: Intermediate
exl-id: 846f56e1-3a98-4a69-b4f7-40ec99ceb348
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '3597'
ht-degree: 23%

---


# Regeleditor für Dynamic Forms im universellen Editor

Mit dem Regeleditor im universellen Editor können Sie intelligente, dynamische Formulare erstellen, die in Echtzeit auf Benutzereingaben reagieren. Sie können statische Formulare in interaktive Erlebnisse mit bedingter Feldsichtbarkeit, automatisierten Berechnungen und komplexer Geschäftslogik umwandeln - und das alles, ohne Code zu schreiben.

## Lerninhalte

Am Ende dieses Handbuchs werden Sie:

- So funktionieren Regeln und wann verschiedene Regeltypen verwendet werden sollten
- Aktivieren des Regeleditors im universellen Editor und Zugreifen auf ihn
- Erstellen einer bedingten Logik zum dynamischen Anzeigen oder Ausblenden von Formularfeldern
- Implementieren automatisierter Berechnungen und Datenvalidierung
- Erstellen benutzerdefinierter Funktionen für komplexe Geschäftsregeln
- Anwendung von Best Practices für eine optimale Formularleistung

## Wozu dient der Regeleditor?

**Transformieren von statischem Forms in intelligente Erlebnisse:**

- **Bedingte Logik**: Anzeigen relevanter Felder basierend auf der Benutzerauswahl
- **Dynamische Berechnungen**: Werte automatisch als Benutzertyp berechnen
- **Datenvalidierung**: Bereitstellung von Echtzeit-Feedback und Vermeidung von Fehlern
- **Verbessertes UX**: Reduzieren Sie die Komplexität von Formularen und führen Sie Benutzer durch logische Flüsse
- **Keine Codierung erforderlich**: Visuelle Schnittstelle, auf die Nicht-Entwickler zugreifen können

**Häufige Anwendungsfälle:**

- Steuerberechnungsformulare mit bedingten Abzügen
- Mehrstufige Assistenten mit Verzweigungspfaden
- Versicherungsformulare mit Tarifberechnungen
- Umfrageformulare mit bedingten Fragen
- E-Commerce-Formulare mit dynamischer Preisgestaltung

## Funktionsweise von Regeln

Regeln sind automatisierte Anweisungen, die Ihre Formulare intelligent und responsiv machen. Sie legen fest, was passieren soll, wenn bestimmte Bedingungen erfüllt sind.

### **Regelkomponenten**

**Bedingung**: Ein logischer Test, der als „true“ oder „false“ ausgewertet wird.

- „Ist das Einkommen des Benutzers größer als 50.000 US-Dollar?“
- „Hat der Benutzer „Ja“ für den Versicherungsschutz ausgewählt?“
- „Ist das Formularfeld leer?“

**Action**: Das Ergebnis, das auftritt, wenn die Bedingung erfüllt ist.

- Formularfelder ein- oder ausblenden
- Werte automatisch berechnen
- Validierungsmeldungen anzeigen
- Aktivieren oder Deaktivieren von Komponenten

### **Regellogikmuster**

**1. condition-action (when-then)**

```
WHEN gross salary > 50000
THEN show "Additional Deduction" field
```

*Am besten geeignet für:* Sichtbarkeit bedingter Felder, dynamische Inhalte

**2. action-condition (set-if)**

```
SET taxable income = gross salary - deductions
IF deductions are applicable
```

*Am besten geeignet für:* Berechnungen, Datenumwandlungen

**3. action-condition-alternative (if-then-else)**

```
IF income > 50000
THEN show "High Income" fields
ELSE show "Standard Income" fields
```

*Am besten geeignet für:* Verzweigungslogik, sich gegenseitig ausschließende Optionen

### **Beispiel aus der Praxis**

**Szenario**: Steuerberechnungsformular

- **Bedingung**: „Bruttogehalt übersteigt 50.000 $&quot;
- **Primäre Aktion**: Feld „Zusätzlicher Abzug“ anzeigen
- **Alternative Aktion**: Feld „Zusätzlicher Abzug“ ausblenden
- **Ergebnis**: Benutzer sehen nur relevante Felder basierend auf ihrem Einkommensniveau

## Voraussetzungen

Bevor Sie mit dem Regeleditor arbeiten, sollten Sie Folgendes sicherstellen:

### **Zugriffsanforderungen**

- Authoring-Zugriff auf **AEM as a Cloud Service**
- **Universeller Editor** mit aktivierter Erweiterung für den Regeleditor
- Berechtigungen zum Bearbeiten von Formularen in Ihrer AEM-Umgebung

### **Technische Anforderungen**

- **Grundlegende Kenntnisse im Formularentwurf**: Vertrautheit mit Formularkomponenten und deren Eigenschaften
- **Vertrautheit mit Geschäftslogik**: Fähigkeit zur Definition bedingter Anforderungen
- **Grundlegende JavaScript-Kenntnisse** (nur für benutzerdefinierte Funktionen erforderlich)

### **Erweiterung des Regeleditors aktivieren**

Die Erweiterung „Regeleditor“ ist im universellen Editor nicht standardmäßig aktiviert. Sie können sie über die [Extension Manager aktivieren](/help/implementing/developing/extending/extension-manager.md).

**Nach dem Aktivieren der Erweiterung:**
Das ![edit-rules](/help/forms/assets/edit-rules-icon.svg) wird in der oberen rechten Ecke angezeigt, wenn Sie Formularkomponenten auswählen.

![Regeleditor für den universellen Editor](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)
*Abbildung: Das Symbol „Regeleditor“ wird angezeigt, wenn Sie Formularkomponenten auswählen*

**So greifen Sie auf den Regeleditor zu:**

1. Wählen Sie im universellen Editor eine beliebige Formularkomponente aus.
2. Klicken Sie auf das ![edit-rules](/help/forms/assets/edit-rules-icon.svg)-Symbol, das angezeigt wird.
3. Die Benutzeroberfläche des Regeleditors wird in einem neuen Bedienfeld geöffnet.

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-for-field.png)
*Abbildung: Benutzeroberfläche des Regeleditors zum Bearbeiten von Komponentenregeln*

>[!NOTE]
>
> In diesem Artikel beziehen sich „Formularkomponente“ und „Formularobjekt“ auf die gleichen Elemente (Eingabefelder, Schaltflächen, Bedienfelder usw.).

## Übersicht über die Benutzeroberfläche des Regeleditors

Der Regeleditor bietet eine benutzerfreundliche visuelle Oberfläche zum Erstellen und Verwalten von Regeln:

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-interface.png)
*Abbildung: Vollständige Benutzeroberfläche des Regeleditors mit nummerierten Komponenten*

### **Schnittstellenkomponenten**

**1. Komponententitel und Regeltyp**

- **Zweck**: Zeigt den Namen der ausgewählten Komponente und den aktuellen Regeltyp an.
- **Beispiel**: „Bruttogehalt eingeben“ (Texteingabe) mit ausgewählter „Wenn“-Regel.
- **Tipp**: Bestätigen Sie immer, dass Sie die richtige Komponente bearbeiten.

**2. Bedienfeld „Formularobjekte und Funktionen“**

- **Registerkarte „Formularobjekte**: Bietet eine hierarchische Ansicht aller Formularkomponenten.
   - Verwenden Sie für : Verweisen auf andere Felder in Ihren Regeln.
   - Navigation: Erweitern oder reduzieren, um bestimmte Komponenten zu finden.
- **Registerkarte &quot;**&quot;: Enthält integrierte mathematische und logische Funktionen.
   - Verwendung für: Ausführen komplexer Berechnungen und Datenmanipulationen.
   - Kategorien: Mathematische, String-, Datums- und Validierungsfunktionen.

**3. Umschalter für Bedienfeld**

- **Zweck**: Blendet das Bedienfeld Objekte und Funktionen ein oder aus.
- **Tipp**: Schalten Sie das Bedienfeld aus, um den Arbeitsbereich für die Regelbearbeitung zu vergrößern.
- **Tastaturbefehl** Nützlich bei der Arbeit mit komplexen Regeln.

**4. Visual Rule Builder**

- **Zweck**: Der Hauptbereich zum Erstellen der Regellogik.
- **Funktionen**: Drag-and-Drop-Oberfläche und Dropdown-Selektoren.
- **Workflow**: Regeltyp auswählen → Bedingungen definieren → Aktionen festlegen.

**5. Steuertasten**

- **Fertig**: Speichert die Regel und schließt den Editor.
- **Abbrechen**: Verwirft Änderungen und schließt den Editor, ohne zu speichern.
- **Tipp**: Testen Sie Ihre Regeln immer, bevor Sie auf „Fertig“ klicken.

### **Regelverwaltung**

Wenn Sie den Regeleditor für eine Komponente öffnen, die bereits Regeln enthält:

![Anzeigen der verfügbaren Regeln eines Formularobjekts](/help/edge/docs/forms/assets/rule-editor15.png)
*Abbildung: Verwalten vorhandener Regeln für eine Formularkomponente*

**Verfügbare Aktionen:**

- **Anzeigen**: Überprüfen von Regelzusammenfassungen und Logik.
- **Bearbeiten**: Ändern vorhandener Regelbedingungen oder Aktionen.
- **Neu anordnen**: Ändert die Ausführungsreihenfolge der Regeln (Regeln werden von oben nach unten ausgeführt).
- **Aktivieren/Deaktivieren**: Regeln zu Testzwecken vorübergehend aktivieren oder deaktivieren.
- **Löschen**: Regeln dauerhaft entfernen.

>[!TIP]
>
> **Die Reihenfolge der Regelausführung ist wichtig**: Regeln werden von oben nach unten ausgeführt. Geben Sie spezifischere Bedingungen vor allgemeinen.

## Verfügbare Regeltypen

Der Regeleditor bietet einen umfassenden Satz von Regeltypen, die nach Funktionen geordnet sind. Wählen Sie den entsprechenden Typ basierend auf Ihrem spezifischen Anwendungsfall aus:

### **Bedingte Logikregeln**

**Wenn**

- **Zweck**: Fungiert als primäre bedingte Regel für die Implementierung komplexer Logik.
- **Anwendungsfall**: Zum Beispiel „Wenn der Benutzer „Verheiratet“ auswählt, Felder für die Informationen zum Ehepartner anzeigen“.
- **Logikmuster**: Bedingung → Aktion (mit einer optionalen alternativen Aktion)

**Ausblenden/Anzeigen**

- **Zweck**: Steuert die Sichtbarkeit von Feldern basierend auf angegebenen Bedingungen.
- **Anwendungsfall:** Abschnitte ausblenden oder progressive Offenlegung aktivieren.
- **Best Practice**: Verwenden Sie , um ein sauberes, fokussiertes Benutzererlebnis zu erstellen.

**Aktivieren/Deaktivieren**

- **Zweck**: Steuert, ob ein Feld basierend auf Bedingungen interagiert werden kann.
- **Anwendungsfall**: Deaktivieren Sie die Schaltfläche Senden , bis alle erforderlichen Felder ausgefüllt sind.
- **Best Practice**: Bieten Sie Benutzern klares visuelles Feedback.

### **Regeln zur Datenbearbeitung**

**Wert festlegen**

- **Zweck**: füllt automatisch Feldwerte aus.
- **Anwendungsfall**: Legen Sie das heutige Datum fest, berechnen Sie Gesamtwerte oder kopieren Sie Werte zwischen Feldern.
- **Best Practice**: Verwenden Sie , um den Benutzeraufwand zu reduzieren und die Genauigkeit sicherzustellen.

**Wert löschen von**

- **Zweck**: Entfernt Daten aus Feldern, wenn sich die Bedingungen ändern.
- **Anwendungsfall**: Löschen abhängiger Felder, wenn sich die Auswahl eines übergeordneten Elements ändert.
- **Best Practice**: Wahrung der Datenintegrität und Verhinderung verwaister Werte.

**Format**

- **Zweck**: Transformiert die Anzeige von Werten.
- **Anwendungsfall**: Formatieren Sie Währung, Telefonnummern oder Daten.
- **Best Practice**: Verbessern der Lesbarkeit ohne Änderung der zugrunde liegenden Daten.

### **Validierungsregeln**

**Validieren**

- **Zweck**: Implementiert eine benutzerdefinierte Validierungslogik.
- **Anwendungsfall**: Durchsetzen komplexer Geschäftsregeln oder feldübergreifender Validierung.
- **Best Practice**: Bereitstellung klarer und umsetzbarer Fehlermeldungen.

### **Berechnungsregeln**

**Mathematischer Ausdruck**

- **Zweck**: Führt automatisierte Berechnungen durch.
- **Anwendungsfall**: Steuerberechnungen, Summen oder Prozentsätze.
- **Best Practice**: Berechnungen in Echtzeit bei Benutzereingabe aktualisieren.

### **Regeln der Benutzeroberfläche**

**Fokus festlegen**

- **Zweck**: lenkt die Aufmerksamkeit der Benutzenden auf bestimmte Felder.
- **Anwendungsfall:** Sie sich auf Fehlerfelder aus oder führen Sie die Benutzer durch die Schritte des Assistenten.
- **Best Practice**: Verwenden Sie sparsam, um eine Unterbrechung des Benutzerflusses zu vermeiden.

**Eigenschaft festlegen**

- **Zweck**: Dynamisches Ändern von Komponenteneigenschaften.
- **Anwendungsfall**: Ändern des Platzhaltertextes oder Ändern von Optionen in einem Dropdown-Menü.
- **Best Practice**: Verbessern des Benutzererlebnisses durch kontextuelle Änderungen.

### **Formularsteuerungsregeln**

**Formular senden**

- **Zweck**: Trigger übermitteln Formulare programmgesteuert.
- **Anwendungsfall**: Automatische Übermittlung nach Erfüllung bestimmter Bedingungen.
- **Best Practice**: Überprüfen Sie das Formular immer vor der Übermittlung.

**Formular zurücksetzen**

- **Zweck**: Löscht alle Formulardaten und setzt das Formular in den Ausgangszustand zurück.
- **Anwendungsfall**: Funktion „Neu starten“.
- **Best Practice**: Bestätigen Sie die Aktion mit dem Benutzer, bevor Sie sie zurücksetzen.

**Formular speichern**

- **Zweck**: Speichert das Formular als Entwurf für das spätere Ausfüllen.
- **Anwendungsfall**: Nützlich für lange Formulare oder Workflows mit mehreren Sitzungen.
- **Best Practice**: Geben Sie ein klares Feedback zum Speicherstatus.

### **Erweiterte Regeln**

**Dienst aufrufen**

- **Zweck**: Ruft externe APIs oder Services auf.
- **Anwendungsfall**: Adresssuche, Echtzeitvalidierung oder Datenanreicherung.
- **Best Practice**: Ladezustände und Fehlerszenarien angemessen handhaben.

**Instanz hinzufügen/**

- **Zweck**: Verwaltet dynamisch wiederholbare Abschnitte.
- **Anwendungsfall**: Hinzufügen von Familienmitgliedern oder mehreren Adressen.
- **Best Practice**: Bereitstellung klarer Steuerelemente zum Hinzufügen oder Entfernen von Instanzen.

**Navigieren Sie zu**

- **Zweck**: Leitet Benutzer zu anderen Formularen oder Seiten weiter.
- **Anwendungsfall**: Workflows mit mehreren Formularen oder bedingtes Routing.
- **Best Practice**: Formulardaten vor der Navigation beibehalten.

**Navigieren zwischen Bereichen**

- **Zweck**: Steuert die Navigation in Formularen im Assistentenstil.
- **Anwendungsfall**: Mehrstufige Formulare oder bedingter Schritt-Überspringen.
- **Best Practice**: Anzeige klarer Fortschrittsanzeigen.

**Dispatch-Ereignis**

- **Zweck**: Benutzerdefinierte Trigger-Ereignisse für erweiterte Integrationen.
- **Anwendungsfall**: Analytics-Tracking oder Integrationen von Drittanbietern.
- **Best Practice**: Wird nur für nicht blockierende Aktionen verwendet.


## Schritt-für-Schritt-Tutorial: Erstellen eines intelligenten Steuerrechners

Dieser Abschnitt enthält ein praktisches Beispiel zur Veranschaulichung der Funktionen des Regeleditors. Das Beispiel führt Sie durch den Aufbau eines Steuerberechnungsformulars, das eine bedingte Logik und automatisierte Berechnungen verwendet.

![Screenshot der Benutzeroberfläche des Regeleditors, der die Erstellung einer bedingten Regel mit Wenn-Dann-Logik für die Sichtbarkeit des Formularfelds zeigt](/help/edge/docs/forms/assets/rule-editor-1.png)
*Abbildung: Steuerberechnungsformular mit intelligenten bedingten Feldern*

### **Tutorial-Übersicht**

In diesem Tutorial erstellen Sie ein Formular, das:

1. **Adaption to user input**: Zeigt relevante Felder basierend auf dem Einkommensniveau an.
2. **Berechnet automatisch**: Berechnet die Steuerschuld in Echtzeit.
3. **Validiert Daten**: Stellt genaue Berechnungen und Dateneingabe sicher.

### **Formularstruktur**

| Feldname | Typ | Zweck | Verhalten |
|------------|------|---------|----------|
| **Bruttogehalt** | Zahleneingabe | Benutzer gibt Jahreseinkommen ein | Bedingte Logik für Trigger |
| **zusätzlicher Abzug** | Zahleneingabe | Zusätzliche Abzüge (falls zutreffend) | Wird angezeigt, wenn Gehalt > 50.000 $ |
| **Steuerpflichtiges Einkommen** | Zahleneingabe | Automatisch berechnet | Aktualisierungen bei Eingabeänderungen |
| **Steuerpflichtig** | Zahleneingabe | Endgültiger Steuerbetrag | Berechnet mit 10 % Rate |

### **Business-Logik zu implementieren**

**Regel 1: Anzeige bedingter Felder**

```
WHEN Gross Salary > 50,000
THEN Show "Additional Deduction" field
ELSE Hide "Additional Deduction" field
```

**Regel 2: Berechnung des steuerpflichtigen Einkommens**

```
SET Taxable Income = Gross Salary - Additional Deduction
(When Additional Deduction is applicable)
```

**Regel 3: Steuerberechnung**

```
SET Tax Payable = Taxable Income × 10%
(Simplified flat rate for demonstration)
```

### **Implementierungsschritte**

Führen Sie die folgenden Schritte aus, um Ihr intelligentes Steuerformular zu erstellen:



+++ 1: Erstellen des Foundation-Formulars

**Ziel**: Erstellen der grundlegenden Formularstruktur mit allen erforderlichen Komponenten

So erstellen Sie ein Steuerberechnungsformular im universellen Editor:

1. **Öffnen des universellen Editors**
   - Navigieren Sie zu Ihrer AEM Sites-Konsole
   - Wählen Sie die Seite aus, auf der Sie das Formular hinzufügen möchten
   - Klicken Sie **Bearbeiten**, um den universellen Editor zu öffnen

2. **Hinzufügen von Formularkomponenten**

   Fügen Sie diese Komponenten in der richtigen Reihenfolge hinzu:

   | Komponente | Typ | Label | Einstellungen |
   |-----------|------|-------|----------|
   | Titel | Titel | „Steuerberechnungsformular“ | Überschriftenebene H2 |
   | Zahleneingabe | Zahleneingabe | „Bruttogehalt“ | Erforderlich: Ja, Platzhalter: „Jahresgehalt eingeben“ |
   | Zahleneingabe | Zahleneingabe | „Zusätzlicher Abzug“ | Erforderlich: Nein, Platzhalter: „Zusätzliche Abzüge eingeben“ |
   | Zahleneingabe | Zahleneingabe | „Steuerpflichtiges Einkommen“ | Erforderlich: Nein, Schreibgeschützt: Ja |
   | Zahleneingabe | Zahleneingabe | „Steuerschuld“ | Erforderlich: Nein, Schreibgeschützt: Ja |
   | Schaltfläche „Senden“ | Absenden | „Steuer berechnen“ | Typ: Senden |

3. **Ersteinstellungen konfigurieren**

   - **Feld für zusätzlichen Abzug ausblenden**:
      - Wählen Sie die Komponente „Zusätzlicher Abzug“
      - Legen Sie im Bedienfeld Eigenschaften **Sichtbar** auf **Nein** fest
      - Dieses Feld wird abhängig von den Regeln angezeigt

   - **Berechnete Felder als schreibgeschützt festlegen**:
      - Felder „Steuerpflichtiges Einkommen“ und „Steuerpflichtig“ auswählen
      - Legen Sie **Schreibgeschützt** in den Eigenschaften **Ja** fest

     ![Screenshot eines Steuerberechnungsformulars mit Eingabefeldern für Bruttogehalt, Familienstand und unterhaltsberechtigte Kinder, auf denen die Formularstruktur vor der Anwendung von Regeln veranschaulicht wird](/help/edge/docs/forms/assets/rule-editor2.png)
     *Abbildung: Ursprüngliche Formularstruktur mit konfigurierten grundlegenden Komponenten*

**Checkpoint**: Sie sollten jetzt ein Formular mit allen Pflichtfeldern haben, in dem „Zusätzlicher Abzug“ ausgeblendet ist und berechnete Felder schreibgeschützt sind.

+++

+++ &#x200B;2. Eine bedingte Regel für ein Formularfeld hinzufügen

Nachdem Sie das Formular erstellt haben, schreiben Sie die erste Regel, damit das Feld `Additional Deduction` nur angezeigt wird, wenn das Bruttogehalt 50.000 US-Dollar überschreitet. So fügen Sie eine bedingte Regel hinzu:

1. Öffnen Sie ein Formular im universellen Editor zur Bearbeitung und wählen Sie in der Inhaltsstruktur das Feld **[!UICONTROL Bruttogehalt]** und dann ![Regeln bearbeiten](/help/forms/assets/edit-rules-icon.svg) aus. Alternativ können Sie das Feld **[!UICONTROL Bruttogehalt]** direkt im Bereich **[!UICONTROL Formularobjekt]** auswählen.
   ![Beispiel1 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor3.png)
Die Benutzeroberfläche des visuellen Regeleditors wird angezeigt.
1. Klicken Sie auf **[!UICONTROL Erstellen]**, um Regeln zu erstellen.
   ![Beispiel2 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor4.png)
Standardmäßig ist der Regeltyp `Set Value Of` ausgewählt. Sie können zwar das ausgewählte Objekt nicht bearbeiten oder ändern, es ist jedoch möglich, über die Dropdown-Liste für Regeln einen anderen Regeltyp auszuwählen.\
   ![Beispiel3 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor5.png)
1. Öffnen Sie die Dropdown-Liste „Regeltyp“ und wählen Sie den Regeltyp **[!UICONTROL Wenn]** aus.
   ![Beispiel4 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor6.png)
1. Wählen Sie die Dropdown-Liste **[!UICONTROL Status auswählen]** und wählen Sie dann **[!UICONTROL Ist größer als]**. Das Feld **[!UICONTROL Zahl eingeben]** wird angezeigt.
   ![Beispiel5 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor7.png)
1. Geben Sie im Feld **[!UICONTROL Zahl eingeben]** in der Regel `50000` ein.
   ![Beispiel6 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor8.png)
Sie haben die Bedingung als `When Gross Salary is greater than 50000` definiert. Definieren Sie anschließend die Aktion, die ausgeführt werden soll, wenn diese Bedingung `True` ist.
1. Wählen Sie in der Anweisung `Then` aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]** die Option **[!UICONTROL Anzeigen]** aus.
   ![Beispiel7 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor9.png)
1. Ziehen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** aus der Registerkarte „Formularobjekte“ in das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**. Stattdessen können Sie auch das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]** auswählen und das Feld **[!UICONTROL Zusätzlicher Abzug]** aus dem Popup-Menü wählen, in dem sämtliche Formularobjekte im Formular aufgeführt sind.
   ![Beispiel8 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor10.png)
1. Klicken Sie auf **[!UICONTROL Abschnitt „Andernfalls“ hinzufügen]**, um eine weitere Bedingung für das Feld **[!UICONTROL Bruttogehalt]** hinzuzufügen, falls ein Gehalt von weniger als `50000` eingegeben wird.
   ![Beispiel9 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor11.png)
1. Wählen Sie in der Anweisung `Else` aus der Dropdown-Liste **[!UICONTROL Aktion auswählen]** die Option **[!UICONTROL Ausblenden]** aus.
   ![Beispiel10 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor12.png)
1. Ziehen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** aus der Registerkarte „Formularobjekte“ in das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**. Stattdessen können Sie auch das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]** auswählen und das Feld **[!UICONTROL Zusätzlicher Abzug]** aus dem Popup-Menü wählen, in dem sämtliche Formularobjekte im Formular aufgeführt sind.
   ![Beispiel11 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor13.png)
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.
Die Regel wird im Regeleditor wie folgt angezeigt.
   ![Beispiel12 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor14.png)

>[!NOTE]
>
> Alternativ können Sie dieses Verhalten auch implementieren, indem Sie eine Anzeige-Regel für das Feld „Zusätzlicher Abzug“ anstelle einer Wenn-Regel für das Feld „Bruttogehalt“ erstellen.

+++

+++ &#x200B;3. Hinzufügen von Berechnungsregeln für die Formularfelder

Als Nächstes schreiben Sie eine Regel, um das `Taxable Income` zu berechnen. Dies ist die Differenz zwischen `Gross Salary` und `Additional Deduction` (falls vorhanden). Um eine Berechnungsregel für das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** hinzuzufügen, führen Sie die folgenden Schritte aus:

1. Wählen Sie im Autorenmodus das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** und dann das Symbol ![Regeln bearbeiten](/help/forms/assets/edit-rules-icon.svg) aus. Alternativ können Sie das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** direkt im Bereich **[!UICONTROL Formularobjekt]** auswählen.
1. Wählen Sie dann **[!UICONTROL Erstellen]** aus, um die Regel zu erstellen.
   ![Beispiel13 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor16.png)
1. Wählen Sie **[!UICONTROL Option auswählen]** und dann **[!UICONTROL Mathematischer Ausdruck]** aus. Ein Feld, in das Sie mathematische Ausdrücke schreiben können, wird geöffnet.
   ![Beispiel14 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor17.png)

1. Gehen Sie im Feld „Mathematischer Ausdruck“ wie folgt vor:

   - Wählen Sie das Feld **[!UICONTROL Bruttogehalt]** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das erste Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**.

   - Wählen Sie **[!UICONTROL Minus]** aus dem Feld **[!UICONTROL Operator wählen]**.

   - Wählen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das andere Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**.
     ![Beispiel15 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor18.png)

1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.

   Fügen Sie nun eine Regel für das Feld `Tax Payable ` hinzu, das durch die Multiplikation des steuerpflichtigen Einkommens mit dem Steuersatz bestimmt wird. Zur Einfachheit nehmen wir einen festen Steuersatz von `10%` an.

1. Wählen Sie im Autorenmodus das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** und dann das Symbol ![Regeln bearbeiten](/help/forms/assets/edit-rules-icon.svg) aus. Wählen Sie anschließend **[!UICONTROL Erstellen]** aus, um Regeln zu erstellen.
   ![Beispiel16 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor19.png)
1. Wählen Sie **[!UICONTROL Option auswählen]** und dann **[!UICONTROL Mathematischer Ausdruck]** aus. Ein Feld, in das Sie mathematische Ausdrücke schreiben können, wird geöffnet.
   ![Beispiel17 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor20.png)
1. Gehen Sie im Feld „Mathematischer Ausdruck“ wie folgt vor:

   - Wählen Sie das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** auf der Registerkarte „Formularobjekt“ aus oder ziehen Sie es in das erste Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**.

   - Wählen Sie **[!UICONTROL Multipliziert mit]** aus dem Feld **[!UICONTROL Operator wählen]**.

   - Wählen Sie **Zahl** aus dem Feld **[!UICONTROL Option auswählen]** und geben Sie den Wert als `10` in das Feld **[!UICONTROL Zahl eingeben]** ein.
     ![Beispiel18 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor21.png)
1. Klicken Sie als Nächstes in den hervorgehobenen Bereich um das Ausdrucksfeld und wählen Sie dann **[!UICONTROL Ausdruck erweitern]** aus.
   ![Beispiel19 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor22.png)
1. Wählen Sie im Feld für den erweiterten Ausdruck im Feld **[!UICONTROL Operator auswählen]** die Option **[!UICONTROL geteilt durch]** und im Feld **[!UICONTROL Option auswählen]** die Option **[!UICONTROL Zahl]** aus. Geben Sie `100` in das Zahlenfeld ein.
   ![Beispiel20 für den Regeleditor](/help/edge/docs/forms/assets/rule-editor23.png)
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.

+++

+++ &#x200B;4. Anzeigen der Vorschau eines Formulars

Wenn Sie jetzt das Formular in der Vorschau anzeigen und das **Bruttogehalt** als `60,000` eingeben, wird das Feld **Zusätzlicher Abzug** angezeigt und **Steuerpflichtiges Einkommen** und **Zu zahlende Steuer** werden entsprechend berechnet.

![Auswählen eines Formulars](/help/edge/docs/forms/assets/rule-editor-form.png)

+++

Zusätzlich zu den integrierten Funktionen wie Summe und Durchschnitt können Sie benutzerdefinierte Funktionen erstellen, um komplexe Geschäftslogiken zu implementieren, die auf Ihre spezifischen Anforderungen zugeschnitten sind.

## Erweitert: Benutzerdefinierte Funktionen

**Verwendung benutzerdefinierter Funktionen:**

- Für komplexe Berechnungen, die über die Möglichkeiten integrierter Funktionen hinausgehen
- So implementieren Sie geschäftsspezifische Validierungsregeln
- Für Datenumwandlungen und Formatierungen
- Integration mit externen Systemen oder APIs

**Vorteile:**

- **Wiederverwendbarkeit**: Einmaliges Schreiben der Funktion und ihre Verwendung in mehreren Formularen und Regeln
- **Wartbarkeit**: Zentralisierte Logik, die einfach zu aktualisieren ist
- **Performance**: Optimierte Ausführung von JavaScript
- **Flexibilität**: Fähigkeit zur Verarbeitung komplexer Szenarien, die nicht von Standardregeln abgedeckt werden

### **Erstellen benutzerdefinierter Funktionen**

**Dateispeicherort**: `/blocks/form/functions.js` in Ihrem AEM-Projekt

**Entwicklungs-Workflow:**

1. **Funktionsdeklaration**
   - Klare und beschreibende Funktionsnamen und Parameter definieren
   - Namen verwenden, die den Zweck der Funktion angeben
   - Dokumentparameter und Rückgabetypen

2. **logische Implementierung**
   - Schreiben von JavaScript-Code
   - Handhabung von Edge-Fällen und Fehlerszenarien
   - Befolgen der Best Practices für die Kodierung

3. **Funktionsexport**
   - Exportfunktionen, um sie im Regeleditor verfügbar zu machen
   - Verwenden benannter Exporte für eine bessere Organisation
   - Testfunktionen vor der Bereitstellung

4. **Dokumentation**
   - Hinzufügen von JSDoc-Kommentaren zur Funktionsdokumentation
   - Anwendungsbeispiele einschließen
   - Angeben von Parametertypen und Rückgabewerten

Das folgende Beispiel zeigt zwei benutzerdefinierte Funktionen: `getFullName` und `days`.

```JavaScript
/**
 - Get Full Name
 - @name getFullName Concats first name and last name
 - @param {string} firstname in Stringformat
 - @param {string} lastname in Stringformat
 - @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

/**
 - Calculate the number of days between two dates.
 - @param {*} endDate
 - @param {*} startDate
 - @name days Calculates the numebr of days between two dates
 - @returns {number} returns the number of days between two dates
 */
function days(endDate, startDate) {
  const start = typeof startDate === 'string' ? new Date(startDate) : startDate;
  const end = typeof endDate === 'string' ? new Date(endDate) : endDate;

  // return zero if dates are valid
  if (Number.isNaN(start.getTime()) || Number.isNaN(end.getTime())) {
    return 0;
  }

  const diffInMs = Math.abs(end.getTime() - start.getTime());
  return Math.floor(diffInMs / (1000 * 60 * 60 * 24));
}

// eslint-disable-next-line import/prefer-default-export
export { getFullName, days };
```

![Hinzufügen einer benutzerdefinierten Funktion](/help/edge/docs/forms/assets/create-custom-function.png)

### Verwenden einer benutzerdefinierten Funktion im Regeleditor

So verwenden Sie eine benutzerdefinierte Funktion im Regeleditor:

1. **Funktion hinzufügen**: Fügen Sie die benutzerdefinierte Funktion zur `../[blocks]/form/functions.js` hinzu. Stellen Sie sicher, dass Sie sie in die `export`-Anweisung in der Datei aufnehmen.
2. **Datei bereitstellen**: Stellen Sie die aktualisierte `functions.js`-Datei in Ihrem GitHub-Projekt bereit und bestätigen Sie, dass der Build erfolgreich abgeschlossen wurde.
3. **Funktionsnutzung**: Greifen Sie im Regeleditor Ihres Formulars auf die Funktion zu, indem Sie die Option `Function Output` im Feld **[!UICONTROL Aktion auswählen]** auswählen.

   ![Benutzerdefinierte Funktion im Regeleditor](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

4. **Vorschau des Formulars**: Zeigen Sie eine Vorschau Ihres Formulars an, um zu überprüfen, ob die neu implementierte Funktion erwartungsgemäß funktioniert.

## Best Practices für die Regelentwicklung

### **Leistungsoptimierung**

**Minimieren der Regelkomplexität**

- Halten Sie einzelne Regeln einfach und fokussiert.
- Teilen Sie komplexe Logik in mehrere kleinere Regeln auf.
- Vermeiden Sie nach Möglichkeit tief verschachtelte Bedingungen.

**Regelausführung optimieren**

- Platzieren Sie die am häufigsten ausgelösten Regeln zuerst.
- Verwenden Sie spezifische Bedingungen, um unnötige Auswertungen zu vermeiden.
- Beachten Sie die Auswirkungen von Regeln auf die Ladezeit des Formulars.

**Ressourcenverwaltung**

- Begrenzen der Anzahl von Regeln pro Formularkomponente
- Verwenden Sie benutzerdefinierte Funktionen für wiederholte Logik, anstatt Regeln zu duplizieren.
- Testen Sie die Leistung mit realistischen Datenmengen.

### **Richtlinien für das Benutzererlebnis**

**Klare Rückmeldungen geben**

- Verwenden Sie Validierungsmeldungen, die Benutzer zur korrekten Eingabe führen.
- Ladeindikatoren für Regeln anzeigen, die externe Dienste beinhalten.
- Schrittweise Offenlegung implementieren, um die kognitive Belastung zu reduzieren.

**Beibehalten der Formularreaktionsfähigkeit**

- Vermeiden Sie Regeln, die abrupte visuelle Änderungen verursachen.
- Implementieren Sie reibungslose Übergänge für Einblenden/Ausblenden-Vorgänge.
- Testen Sie Regeln über verschiedene Geräte und Bildschirmgrößen hinweg.

**Fehlerbehandlung**

- Fallback-Verhalten bereitstellen, wenn Regeln fehlschlagen.
- Anzeigen benutzerfreundlicher Fehlermeldungen.
- Protokollieren Sie Fehler für das Debugging, während Sie ein positives Benutzererlebnis aufrechterhalten.

### **Best Practices für die Entwicklung**

**Teststrategie**

- Testen Sie Regeln mit Kantenfällen und Begrenzungswerten.
- Überprüfen des Regelverhaltens über verschiedene Browser hinweg.
- Testen Sie die Formularfunktionalität mit und ohne aktiviertem JavaScript.

**Dokumentation**

- Dokumentieren Sie die Geschäftslogik hinter komplexen Regeln.
- Regelinventar für große Formulare verwalten
- Verwenden Sie konsistente Benennungskonventionen für Komponenten und Regeln.

**Versionskontrolle**

- Nachverfolgen von Änderungen an benutzerdefinierten Funktionen in der Versionskontrolle.
- Testen Sie Regeln in einer Entwicklungsumgebung vor der Produktion.
- Beibehaltung von Sicherungskopien der Arbeitsregelkonfigurationen.

## Beheben häufiger Probleme

### **Probleme bei der Regelausführung**

**Regeln werden nicht ausgelöst**

- **Komponentennamen überprüfen**: Stellen Sie sicher, dass referenzierte Komponenten vorhanden sind und korrekte Namen haben.
- **Regelreihenfolge überprüfen** Regeln werden von oben nach unten ausgeführt. Bei Bedarf müssen sie neu angeordnet werden.
- **Bedingungen validieren**: Testbedingungen mit bekannten Werten zur Überprüfung der Logik.
- **Browser-**: Suchen Sie nach JavaScript-Fehlern, die die Ausführung blockieren könnten.

**Falsches Regelverhalten**

- **Logikoperatoren überprüfen**: Bestätigen Sie, dass UND/ODER-Bedingungen korrekt strukturiert sind.
- **Mit Beispieldaten testen**: Verwenden Sie bekannte Werte, um Probleme zu isolieren.
- **Datentypen überprüfen**: Stellen Sie sicher, dass für numerische Vergleiche Zahlen und keine Zeichenfolgen verwendet werden.
- **Ausdrücke überprüfen**: Testen Sie mathematische Ausdrücke separat.

### **Leistungsprobleme**

**Langsame Formularantwort**

- **Verringern der Regelkomplexität**: Vereinfachen Sie komplexe bedingte Logik.
- **Benutzerdefinierte Funktionen optimieren**: Profilerstellung und Optimierung von JavaScript-Code.
- **Externe Aufrufe begrenzen**: Minimieren Sie Service-Aufrufe in Regeln.
- **Effiziente Selektoren verwenden**: Stellen Sie sicher, dass Formularobjektverweise spezifisch sind.

**Speicherauslastung**

- **Ereignis-Listener bereinigen**: Nicht verwendete Regelbindungen entfernen.
- **Benutzerdefinierte Funktionen optimieren**: Vermeiden Sie Speicherlecks im JavaScript-Code.
- **Regelbereich einschränken**: Verwenden Sie zielgerichtete Regeln anstelle von globalen Bedingungen.

### **Probleme mit benutzerdefinierten Funktionen**

**Funktionen nicht verfügbar**

- **Dateipfad überprüfen**: Überprüfen Sie, ob `functions.js` sich am richtigen Speicherort befindet: `/blocks/form/functions.js`.
- **Exporte überprüfen**: Stellen Sie sicher, dass Funktionen ordnungsgemäß exportiert werden.
- **Build-Prozess**: Bestätigen Sie, dass der Projekt-Build die aktualisierte Funktionsdatei enthält.
- **Cache-Leerung**: Löschen des Browser-Cache nach der Bereitstellung neuer Funktionen.

**Funktionsfehler**

- **Parametervalidierung**: Überprüfen Sie, ob die Funktionsparameter den erwarteten Typen entsprechen.
- **Fehlerbehandlung**: Hinzufügen von try-catch-Blöcken, um Ausnahmen ordnungsgemäß zu behandeln.
- **Konsolenprotokollierung**: Verwenden Sie console.log für die Ausführung der Debugging-Funktion.
- **JSDoc-Validierung**: Stellen Sie sicher, dass die Funktionsdokumentation mit der Implementierung übereinstimmt.

### **Integration des universellen Editors**

**Regel-Editor wird nicht angezeigt**

- **Erweiterung aktiviert**: Überprüfen Sie, ob die Erweiterung des Regel-Editors aktiviert ist.
- **Komponentenauswahl**: Stellen Sie sicher, dass Sie eine unterstützte Formularkomponente ausgewählt haben.
- **Browserkompatibilität**: Testen Sie in unterstützten Browsern (Chrome, Firefox, Safari).
- **Zugriffsberechtigungen**: Bestätigen Sie, dass der Benutzer über die erforderlichen AEM-Berechtigungen verfügt.

**Probleme mit der Benutzeroberfläche**

- **Bedienfeld-Sichtbarkeit**: Verwenden Sie die Umschalter-Schaltfläche, um das Bedienfeld „Formularobjekte“ ein- oder auszublenden.
- **Speichern von Regeln**: Stellen Sie sicher, dass Regeln gespeichert werden, bevor Sie den Editor schließen.
- **Browser-Zoom**: Setzen Sie den Browser-Zoom auf 100 % zurück, um eine optimale Anzeige auf der Benutzeroberfläche zu gewährleisten.

## Wichtige Einschränkungen

>[!IMPORTANT]
>
> **Benutzerdefinierte Funktionsbeschränkungen**:
>
> - Statische und dynamische Importe werden in benutzerdefinierten Funktionsskripten nicht unterstützt.
> - Der gesamte Code muss direkt in der `/blocks/form/functions.js`-Datei enthalten sein.
> - Funktionen müssen synchron sein (keine asynchronen/wartenden oder Promises).
> - Der Zugriff auf Browser-APIs ist aus Sicherheitsgründen eingeschränkt.

>[!WARNING]
>
> **Überlegungen zur Produktion**:
>
> - Testen Sie alle Regeln gründlich in einer Staging-Umgebung.
> - Überwachen der Formularleistung nach der Bereitstellung komplexer Regeln.
> - Einen Rollback-Plan für regelbezogene Probleme haben.
> - Beachten Sie die Auswirkungen auf Benutzer mit langsamen Netzwerkverbindungen.

## Zusammenfassung

Mit dem Regeleditor im universellen Editor können Sie intelligente, dynamische Formulare erstellen, die außergewöhnliche Benutzererlebnisse bieten. Durch die Implementierung von bedingter Logik, automatisierten Berechnungen und benutzerdefinierten Geschäftsregeln haben Sie folgende Möglichkeiten:

**Statische Forms transformieren**:

- Hinzufügen bedingter Feldsichtbarkeit für sauberere, fokussiertere Schnittstellen.
- Implementieren Sie Echtzeitberechnungen und Datenvalidierung.
- Erstellen Sie eine ausgereifte Geschäftslogik ohne Programmierung.

**Verbessern des Benutzererlebnisses**:

- Führen Sie Benutzer durch logische Formularflüsse.
- Reduzieren Sie Fehler durch intelligente Validierung.
- Geben Sie sofortiges Feedback und Hilfe.

**Steigerung der Effizienz**:

- Automatisieren Sie wiederholte Berechnungen und Dateneingabe.
- Optimieren Sie komplexe Workflows mit intelligentem Routing.
- Reduzieren Sie den Support-Aufwand durch Self-Service-Funktionen.

### **Nächste Schritte**

Sie kennen nun die Grundlagen des Regeleditors:

1. **Einfach beginnen** Beginnen Sie mit den grundlegenden Einblenden-/Ausblenden-Regeln, bevor Sie mit komplexen Berechnungen fortfahren.
1. **Üben mit Beispielen**: Verwenden Sie das Tutorial zum Steuerrechner als Grundlage.
1. **Erweiterte Funktionen erkunden**: Experimentieren Sie mit benutzerdefinierten Funktionen für spezielle Anforderungen.
1. **Gründlich testen**: Regeln immer über verschiedene Szenarien und Geräte hinweg validieren.
1. **Leistung überwachen**: Stellen Sie sicher, dass Regeln das Benutzererlebnis verbessern, anstatt es zu behindern.
