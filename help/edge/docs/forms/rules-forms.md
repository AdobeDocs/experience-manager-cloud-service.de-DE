---
title: Verwenden Sie Regeln, um einem Formular dynamisches Verhalten hinzuzufügen
description: AEM Forms-Edge Delivery Services wurden für optimale Leistung entwickelt und ermöglichen es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen. Verwenden Sie Regeln, um Ihren Formularen dynamisches Verhalten hinzuzufügen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
exl-id: 58042016-e655-446f-a2bf-83f1811525e3
source-git-commit: 61c8d08a21ad81a74e1093838b38f22af94751c3
workflow-type: tm+mt
source-wordcount: '2216'
ht-degree: 0%

---

# Verwenden Sie Regeln, um Ihren Formularen dynamisches Verhalten hinzuzufügen

Eine der leistungsstarken Funktionen beim Erstellen von Formularen mithilfe eines Arbeitsblatts ist die Möglichkeit, integrierte Tabellenfunktionen zu verwenden, um Regeln zu erstellen. So können Sie Formularfelder bedingt anzeigen oder ausblenden, Berechnungen anhand von Benutzereingaben automatisieren und ein dynamischeres Benutzererlebnis schaffen.

Dieser Artikel führt Sie durch die Verwendung verschiedener Eigenschaften von adaptiven Formularblöcken, hauptsächlich [`Visible`](#visible-property), [`Visibility Expression`](#visible-expression-property) und [`Value Expression`](#value-expression-property) -Eigenschaften zusammen mit [Tabellenfunktionen](#spreadsheet-functions-for-rules) , um effektive Regeln für Ihre Formulare zu erstellen. Wir werden auch einige Beispiele untersuchen, um zu veranschaulichen, wie diese Regeln in der Praxis umgesetzt werden können.

## Grundlegendes zu den Konstrukten einer Regel

Regeln sind wie Anweisungen, die uns sagen, was wir in verschiedenen Situationen tun sollen. Eine Regel weist im Allgemeinen die folgenden Konstrukte auf:

* Bedingungen : Diese geben die Umstände an, unter denen die Regel angewendet wird. Stellen Sie sich sie als eine Frage vor, die beantwortet werden muss (ja oder nein).

* Aktionen: Diese definieren, was passiert, wenn die Bedingung erfüllt (true) oder nicht erfüllt (false) ist.


Beispiel: Um ein E-Mail-Feld anzuzeigen, wenn ein Kontrollkästchen aktiviert ist:

* Bedingung: Die &quot;Möchten Sie Zeitschrift und Aktivitäten abonnieren?&quot; aktiviert ist. (Ja oder nein?) Diese Bedingung wird im `Visible` -Eigenschaft des Formulars.
* Aktion (True): Das E-Mail-Feld wird angezeigt. (Was passiert, wenn ja). Die `Visibility Expression`  die für die `visible` -Eigenschaft, um Felder dynamisch anzuzeigen.
* Aktion (False): Das E-Mail-Feld ist ausgeblendet. (Was passiert, wenn nein). Die `Visibility Expression`  die für die `Value` um Felder dynamisch auszublenden.

Eine detaillierte schrittweise Anleitung finden Sie in der [E-Mail-Feld basierend auf einer Bedingung ein-/ausblenden](#example-1-conditional-email-field)


## Verstehen der Eigenschaften für Wert, Sichtbar, Sichtbarkeitsausdruck und Wertausdruck

### Sichtbare Eigenschaft

Stellen Sie sich einen Lichtschalter für Ihr Formularfeld vor. Die `Visible` -Eigenschaft ist wie dieser Schalter, der steuert, ob das Feld beim ersten Laden im Formular anfänglich sichtbar ist.

* True (wie der Lichtschalter &quot;Ein&quot;): Das Feld wird im Formular angezeigt.
* False (z. B. wenn der Lichtschalter &quot;aus&quot;ist): Das Feld wird im Formular ausgeblendet.

Sie können die SpreadSheet-Formel (einschließlich des = -Tags) verwenden, um mithilfe einer tabellenähnlichen Logik eine Formel zu schreiben, mit der die Sichtbarkeit des Felds bestimmt wird. Sie können die Werte aus anderen Feldern in Ihrem Formular in dieser Formel verwenden. Wenn ein Benutzer beispielsweise in einem Feld vom Typ Registrierung &quot;Individuell&quot; auswählt, können Sie das E-Mail-Feld mit einer Formel ausblenden, die diesen Wert überprüft.

### Sichtbare Ausdruckseigenschaft (Feld ein-/ausblenden)

Die `Visible Expression` -Eigenschaft können Sie die Regel verwenden, die zu `Visible` -Eigenschaft, um zu entscheiden, ob das Feld basierend auf Benutzerinteraktionen angezeigt oder ausgeblendet werden soll.

Verwenden Sie die `=FORMULATEXT("Address of the corresponding Visible property)` um die in der `Visible` Eigenschaft als Zeichenfolge für `Visible Expression` Eigenschaftsfeld. Dies ist erforderlich, um Felder in einem veröffentlichten Formular dynamisch ein-/auszublenden.

![Forumaltext](/help/edge/assets/aem-forms-formulatext.png)

### Werteigenschaft (Legen Sie die Anfangsdaten fest)

Stellen Sie sich einen vordefinierten Wert an einem Dimmerschalter vor, um das Licht eines Raumes zu beleuchten. Die `Value` -Eigenschaft ist ähnlich und bestimmt den Anfangsstatus der Daten, die ein Benutzer im Feld sieht.  Legt die aktuellen Daten fest oder ruft sie ab, die im Formularfeld angezeigt werden.

Wenn das Formular zum ersten Mal geladen wird, wird die `Value` -Eigenschaft gibt an, was der Benutzer im Feld sieht, bevor er Änderungen vornimmt. Unlike `Visible` und `Visible Expression` Eigenschaften, die die Sichtbarkeit steuern, wirkt sich die Eigenschaft Wert direkt auf die Daten selbst aus. Benutzer können diesen Wert ändern, indem sie eine Eingabe eingeben, Optionen auswählen (Dropdown-Menüs) oder mit dem Feld interagieren.

Sie können die Excel-Formel (einschließlich des = -Tags) verwenden, um mithilfe einer tabellenähnlichen Logik eine Formel zu schreiben, mit der der im Feld angezeigte Wert bestimmt wird. Sie können die Werte aus anderen Feldern in Ihrem Formular in dieser Formel verwenden. Beispielsweise können Sie einen Rabatt automatisch auf der Basis des in einem anderen Feld eingegebenen Bestellbetrags berechnen.


### Eigenschaft &quot;Value Expression&quot;(Werte berechnen, die in einem Feld angezeigt werden sollen)

Mit dieser Eigenschaft können Sie den in einem Feld angezeigten Wert anhand einer Formel steuern, die dem sichtbaren Ausdruck ähnelt. Stellen Sie sich einen in das Feld integrierten Rechner vor.

Verwenden Sie die `=FORMULATEXT("Address of the corresponding Value property)` um die in der `Value` Eigenschaft als Zeichenfolge für `Value Expression` Eigenschaftsfeld. Dies ist erforderlich, um berechnete Werte in einem veröffentlichten Formular dynamisch zu berechnen und anzuzeigen.

![Forumaltext](/help/edge/assets/aem-forms-formulatext-value.png)

Hier ist eine Analogie zur Festigung dieser Konzepte:

* Sichtbar: Stellen Sie sich eine Form wie ein Haus vor. Die Eigenschaft &quot;Sichtbar&quot;ähnelt dem Lichtschalter für jeden Raum (Feld). Sie entscheiden, ob der Raum anfänglich beleuchtet (sichtbar) oder dunkel (ausgeblendet) ist, wenn jemand das Haus betritt (öffnet das Formular).
* Sichtbarer Ausdruck: Dies ist wie ein Lichtschalter für Bewegungsmelder. Der Raum (Feld) kann anfangs dunkel (ausgeblendet) sein, aber eine Formel (Bewegungsmelder) kann sie aktivieren (Feld anzeigen), wenn jemand vorbeigeht (den Wert in einem anderen Feld ändert).
* Wert: Dies ist wie ein vordefinierter Dmmerschalter für das Licht (Anfangsdaten im Feld). Benutzer können dann die Helligkeit anpassen (den Wert ändern).
* Wertausdruck: Dies ist wie ein fiktiver Taschenrechner, der in das Preisschild eines Produkts im Haus integriert ist (Formular). Das Preis-Tag (Feld) zeigt den endgültigen Preis basierend auf einer Formel (z. B. durch Hinzufügung der Steuer zum Basispreis) an, die andere Informationen wie den Basispreis (Wert aus einem anderen Feld) verwendet.

Durch Kombination dieser Eigenschaften mit [Tabellenfunktionen](#spreadsheet-functions-for-rules)können Sie eine Vielzahl dynamischer Verhaltensweisen in Ihren Formularen erzielen.

## Tabellenfunktionen für Regeln

Der adaptive Forms-Block unterstützt eine Vielzahl von Tabellenfunktionen, die zum Erstellen von Regeln verwendet werden können. Im Folgenden finden Sie Funktionen, die standardmäßig (OOTB) verfügbar sind:

### Logische Funktionen

* [NOT()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018452_715980110): Hiermit wird der logische Status umgekehrt (TRUE wird zu FALSE und umgekehrt).
* [AND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#AND): Gibt nur TRUE zurück, wenn alle angegebenen Bedingungen TRUE sind.
* [OR()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#OR): Gibt TRUE zurück, wenn mindestens eine der angegebenen Bedingungen TRUE ist.

### Bedingte Funktionen

* [IF()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018446_715980110): Wertet eine Bedingung aus und gibt bei TRUE einen bestimmten Wert zurück sowie bei FALSE einen anderen Wert.

### Mathematische Funktionen

* [SUM()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#SUM): Fügt Werte aus einem bestimmten Zellenbereich hinzu.
* [ROUND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#ROUND): Kürzt die Angabe der angegebenen Anzahl von Dezimalstellen.
* [MIN()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#MIN): Gibt den kleinsten Wert aus einem angegebenen Zellenbereich zurück.

## Erstellen einer Regel

Sehen wir uns einige praktische Beispiele an, um zu veranschaulichen, wie Regeln zur Verbesserung Ihrer Formulare verwendet werden können:

## Beispiel 1: Bedingtes E-Mail-Feld

Dieses Beispiel zeigt, wie das Kontrollkästchen als Bedingung dient. Wenn es ausgewählt ist (Bedingung wahr ist), wird das E-Mail-Feld angezeigt (Aktion für &quot;true&quot;). Wenn es nicht ausgewählt ist (Bedingung ist falsch), bleibt das E-Mail-Feld ausgeblendet (Aktion für false).

Erstellen Sie ein Formular mit einem Kontrollkästchen und einem E-Mail-Feld, wie in der folgenden Abbildung dargestellt:

![Bedingtes E-Mail-Formular](/help/edge/assets/aem-forms-conditional-email-form.png)


So verwenden Sie eine Regel, um das E-Mail-Feld bei der Auswahl eines Kontrollkästchens anzuzeigen:

1. Legen Sie die `Value` Eigenschaft des Kontrollkästchenfelds zu `TRUE`.
1. Legen Sie die `Checked` Eigenschaft des Kontrollkästchenfelds zu `FALSE`. Dadurch wird sichergestellt, dass das Kontrollkästchen nicht standardmäßig aktiviert ist.
1. Legen Sie die `Visible` Eigenschaft des E-Mail-Felds zu `=[address of Checked property of the checkbox field] = true()`. Beispiel: `=Q11=TRUE()`. Die Formel wird ausgewertet, wenn das Kontrollkästchen aktiviert ist oder nicht. Wenn das Kontrollkästchen aktiviert ist, wird die Formel als TRUE ausgewertet. Wenn das Kontrollkästchen nicht aktiviert ist, wird die Formel als FALSE ausgewertet.



   Die `TRUE()` -Funktion den logischen Wert zurückgibt, wenn Sie festlegen, dass dieser auf `Checked` -Eigenschaft, wenn die `checked = false` gibt false zurück. Wenn `checked=true`zurückgibt `true`. Dadurch wird sichergestellt, dass das E-Mail-Feld standardmäßig ausgeblendet wird.


1. Legen Sie die `Visible Expression` Eigenschaft des Kontrollkästchenfelds zu `=FORMULATEXT ((address of Visible property of the checkbox field))`. Beispiel: `=FORMULATEXT((G12))`. Die Funktion FORMULATEXT() nimmt eine Formel als Eingabe und gibt die Formel selbst als Textzeichenfolge zurück. Dies hilft bei der Verwendung der Formel im Formular.

   ![Bedingtes E-Mail-Feld](/help/edge/assets/aem-forms-visible-expression-formula-text.png)

1. Vorschau erstellen und Formular publizieren. Wenn Sie nun das Kontrollkästchen aktivieren, wird das E-Mail-Feld eingeblendet, während die Deaktivierung dieses Felds das Feld ausblendet, wodurch ein dynamisches Benutzererlebnis entsteht.

   ![Bedingte E-Mail](/help/edge/assets/aem-forms-coditional-email.gif)


## Beispiel 2: Automatische Berechnung

In diesem Beispiel wird gezeigt, wie ein Formular die geschätzten Reisekosten bei der Auswahl von Reisedaten in einem Formular automatisch berechnet.

Erstellen Sie ein Formular mit einem Datums-, Zimmer- und veranschlagten Reisekosten-Feld, wie unten dargestellt, und einem E-Mail-Feld, wie in der folgenden Abbildung dargestellt:

![Bedingtes E-Mail-Formular](/help/edge/assets/aem-forms-automatic-calculations-form.png)

So verwenden Sie eine automatische Berechnung, um die geschätzten Reisekosten anzuzeigen:

1. Legen Sie die `Value` -Eigenschaft der `amount` -Feld zu `=F6*DAYS(F3,F2)`. Diese Formel berechnet die Anzahl der Tage ab `Start Date`  und `End Date`, multipliziert die Anzahl der Tage mit dem Zimmerbudget und zeigt das Ergebnis in `Estimated Trip Cost` -Feld.

1. Legen Sie die `Value Expression` -Eigenschaft der `Estimated Trip Cost` -Feld zu `=FORMULATEXT ((address of value property of the amount field))`. Beispiel: `=FORMULATEXT(F7)`. Die Funktion FORMULATEXT() nimmt eine Formel als Eingabe und gibt die Formel selbst als Textzeichenfolge zurück. Dies hilft bei der Verwendung der Formel im Formular.

1. Vorschau erstellen und Formular publizieren. Jetzt beim Festlegen einer `Start Date`, `End Date`und Zimmerbudget. Die `Estimated Trip Cost` wird automatisch berechnet.

## Beispiele für Tabellenfunktionen


Im Folgenden finden Sie einige Beispiele für häufig verwendete Tabellenfunktionen:

**Logische Funktionen:**

* **NOT():** Gibt den logischen Status zurück (TRUE wird zu FALSE und umgekehrt).

  Beispiel: Ausblenden des Felds &quot;E-Mail bestätigen&quot;, wenn das E-Mail-Feld leer gelassen wird.

   1. Legen Sie die `Visible` -Eigenschaft des Felds &quot;E-Mail bestätigen&quot;auf `=NOT(if('address of email field'=""))`.

      ![AEM Forms blendet E-Mail-Feld bestätigen aus](/help/edge/assets/aem-forms-not-function-hide-email-field.png)


   1. Setzen Sie den sichtbaren Ausdruck des Felds &quot;E-Mail bestätigen&quot;auf `=FORMULATEXT ((address of visible property of the Confirm Email field))`

      ![AEM Forms-Ausdrucksformel](/help/edge/assets/aem-forms-visible-expression-formula-text.png)


* AND(): Gibt nur TRUE zurück, wenn alle angegebenen Bedingungen TRUE sind.

   * Beispiel: Die Schaltfläche &quot;Senden&quot;wird nur aktiviert, wenn alle erforderlichen Felder ausgefüllt sind.

   1. Legen Sie die `Visible` -Eigenschaft der Schaltfläche &quot;Senden&quot;an:



      ```JavaScript
      =AND(NOT(address of `value` property of the `name` field = ""), NOT(address of `value` property of the `email` field = ""), NOT(address of `value` property of the `phone` field))
      ```

      Zum Beispiel:

      ```JavaScript
      =AND(NOT(F9=""), NOT(F12=""), NOT(F10=""))
      ```

   1. Setzen Sie den sichtbaren Ausdruck des Felds &quot;E-Mail bestätigen&quot;auf

      ```JavaScript
      =FORMULATEXT ((address of visible property of the Confirm Email field))
      ```

      Zum Beispiel:

      ```JavaScript
      =FORMULATEXT(G14)
      ```

      Diese Formel zeigt die &quot;Senden&quot;-Schaltfläche (TRUE) nur an, wenn alle Felder (Name, E-Mail, Telefon) ausgefüllt sind (NOT()) gibt TRUE für jede zurück. Andernfalls wird die Schaltfläche ausgeblendet (AND(multiple FALSES) = FALSE).

* OR(): Gibt TRUE zurück, wenn mindestens eine der angegebenen Bedingungen TRUE ist.

   * Beispiel: Anwenden eines Rabatts, wenn ein Benutzer einen der entsprechenden Rabattgutscheincodes eingibt.

   1. Legen Sie die `Visible` -Eigenschaft des Felds &quot;final amount&quot; zu:


  ```JavaScript
     =IF(OR(F14="BlackFridaySale", F14="NewYearDiscount"), (F6*DAYS(F3,F2)* 0.7) , (F6*DAYS(F3,F2)))
  ```

   1. Setzen Sie den Werteausdruck des Felds &quot;E-Mail bestätigen&quot;auf

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      Zum Beispiel:

      ```JavaScript
      =FORMULATEXT(F7)
      ```

      Mit dieser Formel wird ein Rabatt von 30 % berechnet, wenn der Benutzer einen Couponcode (couponCode = &quot;NewYearDiscount&quot;) ODER (couponCode = &quot;BlackFridaySale&quot;) eingibt. Andernfalls wird der Rabatt auf 0 gesetzt.

**Textfunktionen:**

* IF(): Wertet eine Bedingung aus und gibt einen bestimmten Wert zurück, wenn TRUE lautet, sowie einen anderen Wert, wenn FALSE.

   * Beispiel: Anzeige einer benutzerdefinierten Nachricht basierend auf einer ausgewählten Produktkategorie.

   1. Legen Sie die `Value` -Eigenschaft der `message` -Feld zu `Only upto 7 kg check-in lagguage is allowed!`:

   1. Legen Sie die `Visible` -Eigenschaft der `message` -Feld an:


      ```JavaScript
      =if(address of value property of chosen product category ="Economy", TRUE(), FALSE())
      ```

      Zum Beispiel:

      ```JavaScript
      =if(F5="Economy", TRUE(), FALSE())
      ```

   1. Legen Sie den Wertausdruck der `message` -Feld zu

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      Zum Beispiel:

      ```JavaScript
      =FORMULATEXT(G15)
      ```

      Diese Formel zeigt die Meldung &quot;Nur bis zu 7 kg Check-in Gepäck ist erlaubt!&quot; Wenn die gewählte Klasse &quot;Wirtschaft&quot;ist, bleibt das Meldungsfeld leer.

**Mathematische Funktionen:**

* SUM(): Fügt Werte aus einem bestimmten Zellbereich hinzu.

  Beispiel: Berechnung der Gesamtkosten von Artikeln in einem Warenkorb.

  Im Werteausdruck des Felds &quot;Gesamtkosten&quot;: SUM(Preis * Menge)

  Bei dieser Formel wird davon ausgegangen, dass Sie für jedes Element separate Felder für &quot;Preis&quot;und &quot;Menge&quot;haben. Er multipliziert diese und verwendet SUM(), um die Gesamtkosten für alle Artikel im Warenkorb zu addieren.

* ROUND(): Richtet eine Zahl auf eine angegebene Anzahl von Dezimalstellen.

  Beispiel: Rounding a calculated discount amount to two decimal places.

  Im Werteausdruck des Felds &quot;Discount&quot;(vorausgesetzt, ein Rabatt wird an anderer Stelle berechnet): ROUND(discount, 2)

  Diese Formel rundet den Discount-Wert auf zwei Dezimalstellen.

* MIN(): Gibt den kleinsten Wert aus einem bestimmten Zellenbereich zurück.

  Beispiel: Das erforderliche Mindestalter für ein Anmeldeformular anhand eines ausgewählten Landes ermitteln.

  Im Werteausdruck eines Felds &quot;Minimum age&quot;: MIN(ageLimits)[&quot;US&quot;], ageLimits[&quot;UK&quot;], ageLimits[&quot;Frankreich&quot;])

  Bei dieser Formel wird davon ausgegangen, dass Sie über eine Tabelle mit dem Namen &quot;ageLimits&quot;verfügen, in der die Mindestanforderungen an das Alter für verschiedene Länder gespeichert sind. Es verwendet MIN(), um den kleinsten Wert unter ihnen zu finden.


Darüber hinaus können Sie mit Adaptive Forms Block Ihre Formulare vollständig übernehmen, indem Sie [benutzerdefinierte Funktionen](#creating-custom-functions). Mit benutzerdefinierten Funktionen können Sie Ihre eigenen Regeln und Logiken definieren und so vollständig steuern, wie sich Ihre Formulare verhalten.


## Erstellen und Bereitstellen benutzerdefinierter Funktionen

Der vordefinierte Adaptive Forms-Block (OOTB) bietet Implementierungen für viele [Allgemeine Tabellenfunktionen](#spreadsheet-functions-for-rules). Für eine präzisere Steuerung Ihrer Formulare können Sie jedoch alle OOTB-Funktionen verwenden, die in Microsoft® Excel oder Google Tabellen in Ihren adaptiven Forms-Bausteinen verfügbar sind. Der adaptive Forms-Block enthält nicht die Implementierung für alle OOTB-Funktionen, die in Microsoft® Excel oder Google Tabellen verfügbar sind. Wenn Sie eine dieser Funktionen benötigen, können Sie eine benutzerdefinierte Funktion mit ähnlicher Syntax entwickeln, um die Funktionen von Microsoft® Excel oder Google Tabellen zu erreichen. Sie können beispielsweise die [Funktion &quot;Year()&quot;von Microsoft® Excel](https://support.microsoft.com/en-us/office/calculate-age-113d599f-5fea-448f-a4c3-268927911b37#) um das Alter ab dem Geburtsdatum zu berechnen.


### Benutzerdefinierte Funktion erstellen

Benutzerdefinierte Funktionen befinden sich im `[Adaptive form block]/functions.js` -Datei. Der Erstellungsprozess umfasst im Allgemeinen die folgenden Schritte:

* Funktionsdeklaration: Definieren Sie den Funktionsnamen und die zugehörigen Parameter (die Eingaben, die von ihm akzeptiert werden).
* Logikimplementierung: Schreiben Sie den Code, der die spezifischen Berechnungen oder Manipulationen beschreibt, die von der Funktion ausgeführt werden.
* Funktionsexport: Machen Sie die Funktion in Ihren Regeln zugänglich, indem Sie sie aus der entsprechenden Datei exportieren.

### Beispiel: Year-Funktion

In diesem Beispiel werden zwei benutzerdefinierte Funktionen veranschaulicht, mit denen die Funktion &quot;YEAR()&quot;von Microsoft® Excel zur Berechnung des Alters imitiert wird:


```JavaScript
/**
 * Get the current date and time
 * @name now
 * @returns {Date} The current date and time as a Date object
 */
function now() {
  const today = new Date();
  return today;
}

/**
 * Get the year from a Date object
 * @name year
 * @param {Date} date The date object
 * @throws {TypeError} If the input is not a Date object
 * @returns {number} The year as a number
 */
function year(date) {
  let inputDate = new Date(date)

  if (!(inputDate instanceof Date)) {
    throw new TypeError("Input must be a Date object");
  }

  const year = inputDate.getFullYear();

  return year;
}

// Make the function accessible for use in rules
export { now, year };
```

### Verwenden einer benutzerdefinierten Funktion in Ihrem Formular

So verwenden Sie die benutzerdefinierte Funktion in Ihrem Formular:

1. **Funktion hinzufügen**: Fügen Sie Ihre benutzerdefinierte Funktion in die `[Adaptive form block]/functions.js` -Datei. Denken Sie daran, ihn der Exportanweisung in der Datei hinzuzufügen.
1. **Datei bereitstellen**: Bereitstellen der aktualisierten `functions.js` in Ihr GitHub-Projekt ein und überprüfen Sie, ob der Build erfolgreich war.
1. **Funktionsnutzung**: Greifen Sie mithilfe der Funktion `Value`, `Value Expression`, `Visible`oder `Visible Expression` -Eigenschaften, ähnlich wie bei jeder anderen Tabellenkalkulationsfunktion, die OOTB unterstützt.
1. **Vorschau des Formulars anzeigen**: Verwenden Sie AEM Sidekick, um Ihr Formular mit der neu implementierten Funktion in der Vorschau anzuzeigen.

