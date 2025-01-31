---
title: Wie kann der Regeleditor verwendet werden, um Regeln auf Formularfelder anzuwenden und so dynamisches Verhalten und komplexe Logik für Formulare zu ermöglichen, die mit WYSIWYG Authoring erstellt wurden?
description: Der Regeleditor im universellen Editor ermöglicht es Ihnen, ohne Programmierung oder Skripterstellung dynamisches Verhalten und komplexe Logik in Formulare zu integrieren.
feature: Edge Delivery Services
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: c27b8e413c060de601a72a669d86c4add2a4167d
workflow-type: tm+mt
source-wordcount: '2111'
ht-degree: 11%

---


# Einführung in den Regeleditor im universellen Editor

Sie können das dynamische Formularverhalten mit dem Regeleditor hinzufügen, mit dem Sie Regeln erstellen können. Diese Regeln ermöglichen die Sichtbarkeit bedingter Felder, automatisieren Berechnungen auf der Grundlage von Benutzereingaben und verbessern das allgemeine Benutzererlebnis. Durch die Optimierung des Formularausfüllvorgangs trägt der Regeleditor zur Genauigkeit und Effizienz bei.

Der Regeleditor bietet eine intuitive visuelle Benutzeroberfläche zum Erstellen und Verwalten von Regeln. Sein benutzerfreundlicher Ansatz macht es für alle Benutzer zugänglich, auch für diejenigen ohne umfangreiches technisches Know-how, sodass sie Logik mühelos in ihren Formularen implementieren können.

## Grundlegendes zu Regeln

Regeln sind Anweisungen, die Benutzende anleiten, welche Aktionen unter bestimmten Bedingungen ausgeführt werden sollen.

* **Bedingung**: Eine Bedingung ist eine Prüfung oder Regel, die auswertet, ob etwas wahr oder falsch ist. Es beantwortet die Frage: „Erfüllt dies die Anforderung?“

* **Aktion**: Eine Aktion geschieht, wenn die Bedingung erfüllt ist. Es handelt sich um die Aufgabe oder das Verhalten, die bzw. das durch die Auswertung der Bedingung ausgelöst wird.

Eine Regel folgt normalerweise einem der folgenden Konstrukte:

* **Bedingung-Aktion**: Prüfen Sie zuerst eine Bedingung und führen Sie dann eine Aktion durch. Im Regeleditor wird das `condition-action` Konstrukt durch den `When` Regeltyp erzwungen.
* **Aktion-Bedingung**: Führen Sie zuerst eine Aktion durch und überprüfen Sie dann eine Bedingung. Die `Set Value Of` und `Validate` Regeltypen im Regeleditor erzwingen das `action-condition`.
* **Aktion-Bedingung-alternative Aktion**: Führen Sie eine Aktion aus, überprüfen Sie eine Bedingung und führen Sie dann entweder die Hauptaktion oder eine alternative Aktion basierend auf der Bedingung aus. Die alternative Aktion für `Show` ist beispielsweise standardmäßig `Hide` und für `Enable` ist sie `Disable`.

Beispielsweise könnte eine Bedingung überprüfen, ob ein Benutzer einen bestimmten Wert in ein Feld eingegeben hat, und die Aktion könnte darin bestehen, ein Feld ein- oder auszublenden.
* **Bedingung**: Überprüfen Sie, ob das Einkommen mehr als 50.000 US-Dollar beträgt.
* **Aktion**: Wenn die Bedingung erfüllt ist, das Feld &quot;`Additional Deduction`&quot; anzeigen; andernfalls die alternative Aktion ausführen: `Additional Deduction` Feld ausblenden.

Detaillierte Schritt-für-Schritt-Anweisungen finden Sie unter [Hinzufügen einer bedingten Regel](#2-add-a-conditional-rule).

## Wie wird die Erweiterung des Regeleditors aktiviert?

Im universellen Editor ist der Regeleditor nicht standardmäßig aktiviert. Um die Erweiterung des Regeleditors für Ihre Umgebung zu aktivieren, senden Sie mit Ihrer Anfrage eine E-Mail von Ihrer offiziellen Adresse ](mailto:aem-forms-ea@adobe.com) [aem-forms-ea@adobe.com.

Nachdem die Erweiterung des Regeleditors für Ihre Umgebung aktiviert wurde![ wird das Symbol „edit](/help/forms/assets/edit-rules-icon.svg)rules“ in der oberen rechten Ecke des Editors angezeigt.

![Regeleditor für den universellen Editor](/help/edge/docs/forms/assets/universal-editor-rule-editor.png)

Wählen Sie das Formularobjekt aus, für das Sie eine Regel erstellen möchten, und klicken Sie auf das Symbol ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Die Benutzeroberfläche des Regeleditors wird angezeigt.

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-for-field.png)

Jetzt können Sie mit dem Schreiben von Regeln oder Geschäftslogik für das ausgewählte Formularfeld beginnen, indem Sie die [verfügbaren Regeltypen im Regeleditor“ ](#available-rule-types-in-rule-editor).

## Grundlegendes zur Benutzeroberfläche des Regeleditors

Der visuelle Editor des Regeleditors wird geöffnet, wenn Sie auf das Symbol ![edit-rules](/help/forms/assets/edit-rules-icon.svg) klicken:

![Benutzeroberfläche des Regeleditors](/help/edge/docs/forms/assets/rule-editor-interface.png)

<table border="1">
  <thead>
    <tr>
      <th>Komponente des Regeleditors</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>1. Ansicht „Komponente und Regel“</td>
      <td>Zeigt den Titel des Formularobjekts, über das Sie den Regeleditor gestartet haben, und den aktuell ausgewählten Regeltyp an.</td>
    </tr>
    <tr>
      <td>2. Formularobjekte und Funktionen</td>
      <td>Die Registerkarte <b>Forms</b>Objekte“ zeigt eine hierarchische Ansicht aller im Formular enthaltenen Objekte an. Die <b>Funktionen</b> enthält eine Reihe integrierter Funktionen.</td>
    </tr>
    <tr>
      <td>3. Umschalten zwischen Formularobjekten und Funktionen</td>
      <td>Durch Tippen auf die Schaltfläche schalten Sie zwischen den Bereichen für Formularobjekte und Funktionen um.</td>
    </tr>
    <tr>
      <td>4. Visual Rule Editor</td>
      <td>Der visuelle Regeleditor ist der Bereich im Visual Editor-Modus der Benutzeroberfläche des Regeleditors, in dem Sie Regeln schreiben.</td>
    </tr>
    <tr>
      <td>5. Schaltflächen „Fertig“ und „Abbrechen“</td>
      <td>Die Schaltfläche <b>Fertig</b> wird verwendet, um eine Regel zu speichern. Die <b>Abbrechen</b>-Schaltfläche verwirft alle Änderungen, die Sie an einer Regel vorgenommen haben, und schließt den Regeleditor.</td>
    </tr>
  </tbody>
</table>

Wenn Sie das Objekt auswählen, werden alle vorhandenen Regeln für ein Formularobjekt aufgelistet. Sie können den Titel und eine Vorschau der Regelzusammenfassung im visuellen Regeleditor anzeigen. Außerdem können Sie die Reihenfolge der Regeln ändern, Regeln bearbeiten, Regeln aktivieren/deaktivieren oder Regeln löschen.

![Anzeigen der verfügbaren Regeln eines Formularobjekts](/help/edge/docs/forms/assets/rule-editor15.png)

## Verfügbare Regeltypen

Der Regeleditor bietet eine Reihe vordefinierter Regeltypen, mit denen Sie Regeln schreiben können, wie in der folgenden Tabelle dargestellt:

<table border="1">
  <thead>
    <tr>
      <th>Regeltyp</th>
      <th>Beschreibung</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Wert festlegen</td>
      <td>Legt den Wert eines Formularobjekts in Abhängigkeit davon fest, ob die angegebene Bedingung erfüllt ist.</td>
    </tr>
    <tr>
      <td>Wert löschen von</td>
      <td>Löscht den Wert des angegebenen Objekts.</td>
    </tr>
    <tr>
      <td>Ausblenden/Anzeigen</td>
      <td>Blendet ein Formularobjekt je nachdem aus oder ein, ob eine Bedingung erfüllt ist oder nicht.</td>
    </tr>
    <tr>
      <td>Aktivieren/Deaktivieren</td>
      <td>Aktiviert oder deaktiviert ein Formularobjekt in Abhängigkeit davon, ob eine Bedingung erfüllt ist oder nicht.</td>
    </tr>
    <tr>
      <td>Validieren</td>
      <td>Validiert das Formular oder ein angegebenes Objekt.</td>
    </tr>
    <tr>
      <td>Wenn</td>
      <td>Folgt dem <i>condition-action-alternative</i> Aktionsregelkonstrukt oder <i>condition-action</i> Regelkonstrukt. Sie gibt eine auszuwertende Bedingung und anschließend eine Aktion zum Trigger an, wenn die Bedingung erfüllt ist.</td>
    </tr>
    <tr>
      <td>Format</td>
      <td>Formatiert ein Formularobjekt anhand einer Funktion oder eines regulären Ausdrucks.</td>
    </tr>
    <tr>
      <td>Dienst aufrufen</td>
      <td>Ruft einen Service auf, der in einem Formulardatenmodell (FDM) konfiguriert ist.</td>
    </tr>
    <tr>
      <td>Eigenschaft festlegen</td>
      <td>Legt den Wert einer Eigenschaft des angegebenen Objekts basierend auf einer Bedingung fest.</td>
    </tr>
    <tr>
      <td>Fokus festlegen</td>
      <td>Setzt den Fokus auf das angegebene Objekt.</td>
    </tr>
    <tr>
      <td>Formular speichern</td>
      <td>Speichert das Formular.</td>
    </tr>
    <tr>
      <td>Formular senden/zurücksetzen</td>
      <td>Sendet das Formular oder setzt es zurück.</td>
    </tr>
    <tr>
      <td>Instanz hinzufügen/entfernen</td>
      <td>Fügt eine Instanz des angegebenen wiederholbaren Bereichs oder der Tabellenzeile hinzu oder entfernt sie.</td>
    </tr>
    <tr>
      <td>Navigieren zu</td>
      <td>Navigiert zu anderen adaptiven Forms, anderen Assets (wie Bildern oder Dokumentfragmenten) oder zu einer externen URL.</td>
    </tr>
    <tr>
      <td>Dispatch-Ereignis</td>
      <td>Trigger-spezifische Aktionen basierend auf vordefinierten Bedingungen oder Ereignissen.</td>
    </tr>
    <tr>
      <td>Navigieren zwischen den Bereichen</td>
      <td>Ermöglicht das Verschieben des Fokus zwischen verschiedenen Bereichen in einem Formular.</td>
    </tr>
  </tbody>
</table>


Sehen wir uns nun an, wie [ im Regeleditor Regeln schreiben ](#write-rules).

## Regeln schreiben

Um zu verstehen, wie Regeln im visuellen Regeleditor geschrieben werden, sehen wir uns ein einfaches Beispiel für ein Steuerberechnungsformular an:

![Beispiel für einen Regeleditor](/help/edge/docs/forms/assets/rule-editor-1.png)

In der oben beschriebenen Form gibt der Benutzer das Bruttogehalt ein. Basierend auf dieser Eingabe wird ein bedingtes Feld angezeigt und die zu zahlende Steuer berechnet.

**Formularfelder:**
* Bruttogehalt (Benutzereingabe)
* Zusätzlicher Abzug (bedingtes Feld)
* Steuerpflichtiges Einkommen (berechnetes Feld)
* Steuerschuld (berechnetes Feld)

**Bedingte Regel:**
* Bedingung: Bruttogehalt > 50.000
* Aktion: Feld für zusätzlichen Abzug anzeigen

**Berechnungsregeln:**

* Steuerpflichtiges Einkommen = Bruttogehalt - zusätzlicher Abzug (falls zutreffend)
* Steuerpflichtig = Steuerpflichtiges Einkommen * Steuersatz (nehmen Sie zur Einfachheit einen festen Satz von 10 % an)

Gehen Sie wie folgt vor, um Regeln zu erstellen:

### 1. Formular erstellen

So erstellen Sie ein Formular im universellen Editor:

1. Öffnen Sie ein Formular im universellen Editor zur Bearbeitung.
1. Fügen Sie die folgenden Formularkomponenten hinzu:
   * Steuerberechnungsformular (Titel)
   * Bruttogehalt (Texteingabe)
   * Zusätzlicher Abzug (Texteingabe)
   * Steuerpflichtiges Einkommen (Texteingabe)
   * Steuerschuld (Texteingabe)
   * Senden (Schaltfläche „Senden„)
1. Blenden Sie das `Additional Deduction` Formularfeld aus, indem Sie dessen `Properties` öffnen.

   ![Beispiel für einen Regeleditor](/help/edge/docs/forms/assets/rule-editor2.png)

### 2. Hinzufügen einer bedingten Regel für ein Formularfeld

Nachdem Sie das Formular erstellt haben, schreiben Sie die erste Regel, um das Feld `Additional Deduction` nur dann anzuzeigen, wenn das Bruttogehalt 50.000 USD überschreitet. Hinzufügen einer bedingten Regel:

1. Öffnen Sie ein Formular im universellen Editor zur Bearbeitung.
1. Wählen Sie die **[!UICONTROL Bruttolöhne]** in der Inhaltsstruktur aus und klicken Sie auf ![edit-rules](/help/forms/assets/edit-rules-icon.svg).
   ![Beispiel für den Regeleditor1](/help/edge/docs/forms/assets/rule-editor3.png)
Die Benutzeroberfläche des visuellen Regeleditors wird angezeigt.
1. Klicken Sie **[!UICONTROL Erstellen]**, um den Regeleditor zu starten.
   ![Beispiel für Regeleditor2](/help/edge/docs/forms/assets/rule-editor4.png)
Standardmäßig ist der `Set Value Of` Regeltyp ausgewählt. Sie können zwar das ausgewählte Objekt nicht ändern, aber Sie können über die Dropdown-Liste „Regel“ einen anderen Regeltyp auswählen.\
   ![Regel-Editor Beispiel3](/help/edge/docs/forms/assets/rule-editor5.png)
1. Öffnen Sie die Dropdown-Liste Regeltyp und wählen Sie **[!UICONTROL Wenn]** Regeltyp aus.
   ![Beispiel für Regeleditor4](/help/edge/docs/forms/assets/rule-editor6.png)
1. Wählen Sie **[!UICONTROL Dropdown]** Status auswählen aus und wählen Sie **[!UICONTROL ist größer als]** aus. Das **[!UICONTROL Eine Zahl eingeben]** wird angezeigt.
   ![Beispiel für Regeleditor5](/help/edge/docs/forms/assets/rule-editor7.png)
1. Geben Sie in der Regel `50000` in **[!UICONTROL Feld]**Zahl eingeben“ ein.
   ![Beispiel für den Regeleditor6](/help/edge/docs/forms/assets/rule-editor8.png)
Sie haben die Bedingung als `When Gross Salary is greater than 50000` definiert. Definieren Sie als Nächstes die Aktion, die ausgeführt werden soll, wenn diese Bedingung `True` ist.
1. Wählen Sie in der `Then`-Anweisung **[!UICONTROL Anzeigen]** aus der Dropdown **[!UICONTROL Auswahl der Aktion]** aus.
   ![Beispiel für Regeleditor7](/help/edge/docs/forms/assets/rule-editor9.png)
1. Ziehen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** aus der Registerkarte „Formularobjekte“ in das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**. Alternativ können Sie das Feld **[!UICONTROL Legen Sie das Objekt ab oder wählen Sie hier aus]** und wählen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** aus dem Popup-Menü aus, in dem alle Formularobjekte im Formular aufgeführt sind.
   ![Beispiel für den Regeleditor8](/help/edge/docs/forms/assets/rule-editor10.png)
1. Klicken Sie **[!UICONTROL Abschnitt „Sonst hinzufügen]**, um eine weitere Bedingung für das Feld **[!UICONTROL Bruttogehalt]** hinzuzufügen, falls Sie ein Gehalt unter `50000` eingeben.
   ![Beispiel für Regeleditor9](/help/edge/docs/forms/assets/rule-editor11.png)
1. Wählen **[!UICONTROL Ausblenden]** aus der **[!UICONTROL Aktion auswählen]** in der `Else` aus.
   ![Beispiel für den Regeleditor10](/help/edge/docs/forms/assets/rule-editor12.png)
1. Ziehen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** aus der Registerkarte „Formularobjekte“ in das Feld **[!UICONTROL Objekt hier einfügen oder auswählen]**. Alternativ können Sie das Feld **[!UICONTROL Legen Sie das Objekt ab oder wählen Sie hier aus]** und wählen Sie das Feld **[!UICONTROL Zusätzlicher Abzug]** aus dem Popup-Menü aus, in dem alle Formularobjekte im Formular aufgeführt sind.
   ![Beispiel für den Regeleditor11](/help/edge/docs/forms/assets/rule-editor13.png)
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.
Die Regel wird im Regeleditor wie folgt angezeigt.
   ![Beispiel für den Regeleditor12](/help/edge/docs/forms/assets/rule-editor14.png)

>[!NOTE]
>
> Alternativ können Sie für das Feld Zusätzlicher Abzug anstelle einer Wenn-Regel für das Feld Bruttogehalt eine Regel vom Typ Anzeigen erstellen, um dasselbe Verhalten zu implementieren.

### 3. Hinzufügen von Berechnungsregeln für die Formularfelder

Als Nächstes schreiben Sie eine Regel, um die `Taxable Income` zu berechnen. Dies ist der Unterschied zwischen `Gross Salary` und `Additional Deduction` (falls zutreffend). Um eine Berechnungsregel für das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** hinzuzufügen, führen Sie die folgenden Schritte aus:

1. Wählen Sie im Autorenmodus das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** und klicken Sie auf ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Wählen Sie anschließend **[!UICONTROL Erstellen]**, um den Regeleditor zu starten.
   ![Beispiel für den Regeleditor13](/help/edge/docs/forms/assets/rule-editor16.png)
1. Wählen Sie **[!UICONTROL Option auswählen]** und dann **[!UICONTROL Mathematischer Ausdruck]** aus. Ein Feld, in dem Sie mathematische Ausdrücke schreiben können, wird geöffnet.
   ![Beispiel für den Regeleditor14](/help/edge/docs/forms/assets/rule-editor17.png)

1. Im Feld Mathematischer Ausdruck:

   * Wählen Sie das Feld **[!UICONTROL Bruttogehalt“ auf der Registerkarte &quot;Forms-Objekt]** im ersten Feld **[!UICONTROL Legen Sie das Objekt ab oder wählen Sie hier aus]** oder ziehen Sie es dorthin.

   * Wählen Sie **[!UICONTROL Minus]** aus dem Feld **[!UICONTROL Operator auswählen]** aus.

   * Wählen Sie das Feld **[!UICONTROL Zusätzliche Abzüge“ auf der Registerkarte &quot;Forms-Objekt]** im anderen Feld **[!UICONTROL Objekt hier einfügen oder]**.
     ![Beispiel für den Regeleditor15](/help/edge/docs/forms/assets/rule-editor18.png)

1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.

   Fügen Sie nun eine Regel für das Feld `Tax Payable ` hinzu, das durch Multiplikation des steuerpflichtigen Einkommens mit dem Steuersatz bestimmt wird. Zur Einfachheit nehmen wir einen festen Steuersatz von `10%` an.

1. Wählen Sie im Bearbeitungsmodus das Feld **[!UICONTROL Steuerpflichtig]** und klicken Sie auf das Symbol ![edit-rules](/help/forms/assets/edit-rules-icon.svg). Wählen Sie anschließend **[!UICONTROL Erstellen]**, um den Regeleditor zu starten.
   ![Beispiel für den Regeleditor16](/help/edge/docs/forms/assets/rule-editor19.png)
1. Wählen Sie **[!UICONTROL Option auswählen]** und dann **[!UICONTROL Mathematischer Ausdruck]** aus. Ein Feld, in dem Sie mathematische Ausdrücke schreiben können, wird geöffnet.
   ![Beispiel für den Regeleditor17](/help/edge/docs/forms/assets/rule-editor20.png)
1. Im Feld Mathematischer Ausdruck:

   * Wählen Sie auf der Registerkarte &quot;Forms-Objekt“ das Feld **[!UICONTROL Steuerpflichtiges Einkommen]** im ersten Feld **[!UICONTROL Legen Sie das Objekt ab oder wählen Sie hier aus]** oder ziehen Sie es dorthin.

   * Wählen Sie **[!UICONTROL Multipliziert mit]** aus dem Feld **[!UICONTROL Operator auswählen]** aus.

   * Wählen Sie **Zahl** aus dem Feld **[!UICONTROL Option auswählen]** und geben Sie den Wert wie `10` in das Feld **[!UICONTROL Zahl eingeben]** ein.
     ![Beispiel für den Regeleditor18](/help/edge/docs/forms/assets/rule-editor21.png)
1. Wählen Sie als Nächstes etwas im hervorgehobenen Bereich um das Ausdrucksfeld und wählen Sie dann **[!UICONTROL Ausdruck erweitern]** aus.
   ![Beispiel für den Regeleditor19](/help/edge/docs/forms/assets/rule-editor22.png)
1. Wählen Sie im Feld für den erweiterten Ausdruck im Feld **[!UICONTROL Operator auswählen]** die Option **[!UICONTROL geteilt durch]** und im Feld **[!UICONTROL Option auswählen]** die Option **[!UICONTROL Zahl]** aus. Geben Sie dann `100` in das Zahlenfeld ein.
   ![Beispiel für den Regeleditor20](/help/edge/docs/forms/assets/rule-editor23.png)
1. Wählen Sie **[!UICONTROL Fertig]** aus, um die Regel zu speichern.

### 4. Vorschau eines Formulars

Wenn Sie jetzt das Formular in der Vorschau anzeigen und das **Bruttogehalt** als `60,000` eingeben, wird das Feld **Zusätzlicher**&quot; angezeigt und die **Steuerpflichtiges Einkommen** und **Steuerpflichtiger** werden entsprechend berechnet.

![Vorschau eines Formulars](/help/edge/docs/forms/assets/rule-editor-form.png)

Zusätzlich zu den vordefinierten Funktionen wie „Summe“ und „Durchschnitt“, die unter „Funktionsausgabe“ aufgeführt sind, können Sie auch [benutzerdefinierte Funktionen schreiben](#create-a-custom-function) um komplexe Geschäftslogiken zu implementieren.

## Benutzerdefinierte Funktion im Regeleditor

Edge Delivery Services Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzende JavaScript-Funktionen für die Implementierung komplexer Geschäftsregeln definieren können. Die benutzerdefinierten Funktionen erweitern die Funktionen von Formularen durch die Erleichterung der Bearbeitung und Verarbeitung der eingegebenen Daten, um bestimmte Anforderungen zu erfüllen.

### Erstellen einer benutzerdefinierten Funktion

Um eine benutzerdefinierte Funktion zu erstellen, bearbeiten Sie die `../[blocks]/form/functions.js`. Der Erstellungsprozess umfasst im Allgemeinen die folgenden Schritte:

* **Funktionsdeklaration**: Definieren Sie den Funktionsnamen und die Parameter (die Eingaben, die er akzeptiert).
* **Logische Implementierung** Schreiben Sie den Code, der die spezifischen Berechnungen oder Manipulationen umreißt, die von der Funktion durchgeführt werden.
* **Funktionsexport**: Machen Sie die Funktion in Ihren Regeln zugänglich, indem Sie sie aus der entsprechenden Datei exportieren.


In diesem Beispiel werden zwei benutzerdefinierte Funktionen veranschaulicht, nämlich `getFullName` und `days`:

```JavaScript
/**
 * Get Full Name
 * @name getFullName Concats first name and last name
 * @param {string} firstname in Stringformat
 * @param {string} lastname in Stringformat
 * @return {string}
 */
function getFullName(firstname, lastname) {
  return `${firstname} ${lastname}`.trim();
}

/**
 * Calculate the number of days between two dates.
 * @param {*} endDate
 * @param {*} startDate
 * @name days Calculates the numebr of days between two dates
 * @returns {number} returns the number of days between two dates
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
![Hinzufügen benutzerdefinierter Funktionen](/help/edge/docs/forms/assets/create-custom-function.png)

### Verwenden einer benutzerdefinierten Funktion im Regeleditor

So verwenden Sie die benutzerdefinierte Funktion im Regeleditor:

1. **Funktion hinzufügen**: Fügen Sie Ihre benutzerdefinierte Funktion in die Datei `../[blocks]/form/functions.js` ein. Denken Sie daran, ihn zur `export`-Anweisung in der Datei hinzuzufügen.
1. **Bereitstellen der Datei**: Stellen Sie die aktualisierte Datei `functions.js` in Ihrem GitHub-Projekt bereit und überprüfen Sie, ob der Build erfolgreich war.
1. **Funktionsnutzung**: Greifen Sie auf die Funktion im Regeleditor Ihres Formulars zu, indem Sie die Option `Function Output` im Feld **[!UICONTROL Aktion auswählen]** auswählen.

   ![Benutzerdefinierte Funktion im Regeleditor](/help/edge/docs/forms/assets/custom-function-rule-editor.png)

1. **Vorschau des Formulars**: Vorschau des Formulars mit der neu implementierten Funktion.

## Ähnliche Artikel

{{see-also-rule-editor}}

## Siehe auch

* [Erste Schritte mit Edge Delivery Services für AEM Forms](/help/edge/docs/forms/tutorial.md)
* [Erstellen eines Formulars mit Google Tabellen oder Microsoft Excel](/help/edge/docs/forms/create-forms.md)
* [Einrichten von Google Tabellen- oder Microsoft Excel-Dateien, um Daten zu akzeptieren](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen des Formulars und Starten der Datenerfassung](/help/edge/docs/forms/publish-forms.md)
* [Anpassen des Erscheinungsbilds von Formularen](/help/edge/docs/forms/style-theme-forms.md)
* [Hinzufügen wiederholbarer Abschnitte zu einem Formular](/help/edge/docs/forms/repeatable-forms.md)
* [Anzeigen einer benutzerdefinierten Dankesnachricht nach der Formularübermittlung](/help/edge/docs/forms/thank-you-page-form.md)
* [Komponenten von adaptiven Formularblöcken und ihre Eigenschaften](/help/edge/docs/forms/form-components.md)
* [Real Use Monitoring](https://www.aem.live/developer/rum#authentication)
