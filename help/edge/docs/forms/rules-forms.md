---
title: Verwenden von Regeln zum Hinzufügen von dynamischem Verhalten zu einem Formular
description: Edge Delivery Services für AEM Forms wurde für eine optimale Leistung entwickelt und ermöglicht es Ihnen, sich die Zukunft einer optimierten Datenerfassung und Benutzerinteraktion vorzustellen. Verwenden Sie Regeln, um Ihren Formularen dynamisches Verhalten hinzuzufügen.
feature: Edge Delivery Services
exl-id: 58042016-e655-446f-a2bf-83f1811525e3
role: Admin, Architect, Developer
source-git-commit: 2e2a0bdb7604168f0e3eb1672af4c2bc9b12d652
workflow-type: tm+mt
source-wordcount: '2218'
ht-degree: 100%

---

# Verwenden von Regeln zum Hinzufügen von dynamischem Verhalten zu einem Formular

Eine der leistungsstarken Funktionen bei der Erstellung von Formularen mit einer Kalkulationstabelle ist die Möglichkeit, integrierte Kalkulationstabellenfunktionen zur Erstellung von Regeln zu verwenden. Auf diese Weise können Sie Formularfelder bedingt anzeigen oder ausblenden, Berechnungen auf der Grundlage von Benutzereingaben automatisieren und ein dynamischeres Benutzererlebnis schaffen.

In diesem Artikel erfahren Sie, wie Sie verschiedene Eigenschaften des adaptiven Formularblocks, vor allem [`Visible`](#visible-property), [`Visibility Expression`](#visible-expression-property) und [`Value Expression`](#value-expression-property), zusammen mit den [Kalkulationstabellen-Funktionen](#spreadsheet-functions-for-rules) verwenden können, um effektive Regeln für Ihre Formulare zu erstellen. Wir werden auch einige Beispiele untersuchen, um zu veranschaulichen, wie diese Regeln in der Praxis umgesetzt werden können.

## Grundlegendes der Konstruktionen einer Regel

Regeln sind wie Anweisungen, die uns sagen, was wir in verschiedenen Situationen tun sollen. Eine Regel weist im Allgemeinen die folgenden Konstrukte auf:

- Bedingungen: Diese geben die Umstände an, unter denen die Regel angewendet wird. Betrachten Sie sie als eine Frage, die beantwortet werden muss (ja oder nein).

- Aktionen: Diese definieren, was passiert, wenn die Bedingung erfüllt (true) oder nicht erfüllt (false) ist.


Zum Beispiel, um ein E-Mail-Feld anzuzeigen, wenn ein Kontrollkästchen markiert ist:

- Bedingung: Das Kontrollkästchen „Möchten Sie das Magazin und die Aktivitäten abonnieren?“ ist aktiviert. (Ja oder nein?) Diese Bedingung wird in der Eigenschaft `Visible` des Formulars festgelegt.
- Aktion (True): Das E-Mail-Feld wird angezeigt. (Was passiert, wenn „Ja“ ausgewählt wurde). Die `Visibility Expression` verwenden die für die Eigenschaft `visible` definierte Bedingung, um Felder dynamisch anzuzeigen.
- Aktion (False): Das E-Mail-Feld ist ausgeblendet. (Was passiert, wenn „Nein“ ausgewählt wurde). Die `Visibility Expression` verwendet die für die `Value` definierte Bedingung, um Felder dynamisch auszublenden.

Eine detaillierte Schritt-für-Schritt-Anleitung finden Sie unter [Ein-/Ausblenden eines E-Mail-Feldes basierend auf einer Bedingung](#example-1-conditional-email-field)


## Grundlegendes zu den Eigenschaften für Wert, Sichtbarkeit, Sichtbarkeitsausdruck und Wertausdruck

### Sichtbare Eigenschaft

Stellen Sie sich einen Lichtschalter für Ihr Formularfeld vor. Die Eigenschaft `Visible` ist wie ein Schalter, der steuert, ob das Feld beim ersten Laden des Formulars sichtbar ist.

- True (wie wenn der Lichtschalter „an“ ist): Das Feld wird im Formular angezeigt.
- False (wie wenn der Lichtschalter „aus“ ist): Das Feld wird im Formular ausgeblendet.

Sie können die SpreadSheet-Formel (einschließlich des Tags „=“) verwenden, um mithilfe einer tabellenähnlichen Logik eine Formel zu schreiben, mit der die Sichtbarkeit des Felds bestimmt wird. Sie können die Werte aus anderen Feldern in Ihrem Formular in dieser Formel verwenden. Wenn Benutzende beispielsweise „Kontakt“ in einem Feld für den Registrierungstyp auswählt, können Sie das E-Mail-Feld mithilfe einer Formel ausblenden, die diesen Wert überprüft.

### Sichtbare Ausdruckseigenschaft (Feld ein-/ausblenden)

Mit der Eigenschaft `Visible Expression` können Sie die zur Eigenschaft `Visible` hinzugefügte Regel verwenden, um zu entscheiden, ob das Feld auf der Grundlage von Benutzerinteraktionen ein- oder ausgeblendet werden soll.

Verwenden Sie die `=FORMULATEXT("Address of the corresponding Visible property)`, um die in der Eigenschaft `Visible` erwähnte Formel als Zeichenfolge in das Eigenschaftsfeld `Visible Expression` zu übertragen. Dies ist erforderlich, um Felder in einem veröffentlichten Formular dynamisch ein-/auszublenden.

![Formulatext](/help/edge/assets/aem-forms-formulatext.png)

### Werteigenschaft (Festlegen der Anfangsdaten)

Stellen Sie sich einen vordefinierten Wert an einem Dimmschalter vor, um das Licht eines Raumes zu beleuchten. Die Eigenschaft `Value` ist ähnlich und bestimmt den Anfangszustand der Daten, die Benutzende im Feld sehen.  Legt die aktuellen Daten fest, die im Formularfeld angezeigt werden, oder ruft sie ab.

Wenn das Formular zum ersten Mal geladen wird, bestimmt die Eigenschaft `Value`, was die Benutzenden in dem Feld sehen, bevor sie Änderungen vornehmen. Anders als die Eigenschaften `Visible` und `Visible Expression`, die die Sichtbarkeit steuern, wirkt sich die Eigenschaft „Wert“ direkt auf die Daten selbst aus. Benutzende können diesen Wert ändern, indem sie eine Eingabe eingeben, „Optionen“ auswählen (in den Dropdown-Menüs) oder mit dem Feld interagieren.

Sie können die Excel-Formel (einschließlich des Tags „=“) verwenden, um mithilfe einer tabellenähnlichen Logik eine Formel zu schreiben, mit der der im Feld angezeigte Wert bestimmt wird. Sie können die Werte aus anderen Feldern in Ihrem Formular in dieser Formel verwenden. Beispielsweise können Sie einen Rabatt automatisch auf der Basis des in einem anderen Feld eingegebenen Bestellbetrags berechnen.


### Eigenschaft „Wertausdruck“ (das Berechnen der Werte, die in einem Feld angezeigt werden sollen)

Mit dieser Eigenschaft können Sie den in einem Feld angezeigten Wert anhand einer Formel steuern, die dem Sichtbarkeitsausdruck ähnelt. Stellen Sie sich einen in das Feld integrierten Taschenrechner vor.

Verwenden Sie `=FORMULATEXT("Address of the corresponding Value property)`, um die in der Eigenschaft `Value` genannte Formel als Zeichenfolge in das Eigenschaftsfeld `Value Expression` zu übertragen. Dies ist erforderlich, um berechnete Werte in einem veröffentlichten Formular dynamisch zu berechnen und anzuzeigen.

![Formulatext](/help/edge/assets/aem-forms-formulatext-value.png)

Hier ist eine Analogie zur Festigung dieser Konzepte:

- Sichtbar: Stellen Sie sich ein Formular wie ein Haus vor. Die Eigenschaft „Sichtbar“ entspricht dem Lichtschalter für jeden Raum (Feld). Sie entscheiden, ob der Raum anfänglich beleuchtet (sichtbar) oder dunkel (ausgeblendet) ist, wenn jemand das Haus betritt (das Formular öffnet).
- Sichtbarer Ausdruck: Dies ist wie ein Lichtschalter mit Bewegungsmelder. Der Raum (Feld) kann anfangs dunkel (ausgeblendet) sein, aber eine Formel (Bewegungsmelder) kann sie aktivieren (Feld anzeigen), wenn jemand vorbeigeht (den Wert in einem anderen Feld ändert).
- Wert: Dies ist wie ein vordefinierter Dimmschalter für das Licht (Anfangsdaten im Feld). Benutzende können dann die Helligkeit anpassen (den Wert ändern).
- Wertausdruck: Dies ist wie ein fiktiver Taschenrechner, der in das Preisschild eines Produkts im Haus integriert ist (Formular). Das Preis-Tag (Feld) zeigt den endgültigen Preis auf der Grundlage einer Formel an (z. B. durch Hinzufügen einer Steuer zum Basispreis), die andere Informationen wie den Basispreis (Wert aus einem anderen Feld) verwendet.

Durch die Kombination dieser Eigenschaften mit [Tabellenfunktionen](#spreadsheet-functions-for-rules) können Sie eine breite Palette dynamischer Verhaltensweisen in Ihren Formularen erzielen.

## Tabellenfunktionen für Regeln

Der adaptive Formularbaustein unterstützt eine Vielzahl von Tabellenfunktionen, die zum Erstellen von Regeln verwendet werden können. Im Folgenden finden Sie Funktionen, die standardmäßig verfügbar sind:

### Logikfunktionen

- [NOT()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018452_715980110): Hiermit wird der logische Status umgekehrt (TRUE wird zu FALSE und umgekehrt).
- [AND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#AND): Gibt nur TRUE zurück, wenn alle angegebenen Bedingungen TRUE sind.
- [OR()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#OR): Gibt TRUE zurück, wenn mindestens eine der angegebenen Bedingungen TRUE ist.

### Bedingte Funktionen

- [IF()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#__RefHeading__1018446_715980110): Wertet eine Bedingung aus und gibt einen bestimmten Wert zurück, wenn TRUE, oder einen anderen, wenn FALSE.

### Mathematische Funktionen

- [SUM()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#SUM): Addiert Werte aus einem bestimmten Zellenbereich auf.
- [ROUND()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#ROUND): Rundet eine Zahl auf die angegebene Anzahl von Dezimalstellen.
- [MIN()](https://docs.oasis-open.org/office/v1.2/os/OpenDocument-v1.2-os-part2.html#MIN): Gibt den kleinsten der Werte aus einem angegebenen Zellenbereich zurück.

## Erstellen einer Regel

Sehen wir uns einige praktische Beispiele an, um zu veranschaulichen, wie Regeln zur Verbesserung Ihrer Formulare verwendet werden können:

## Beispiel 1: Bedingtes E-Mail-Feld

Dieses Beispiel zeigt, wie das Kontrollkästchen als Bedingung dient. Wenn es ausgewählt ist (Bedingung TRUE ist), wird das E-Mail-Feld angezeigt (Aktion für TRUE). Wenn es nicht ausgewählt ist (Bedingung ist FALSE), bleibt das E-Mail-Feld ausgeblendet (Aktion für FALSE).

Erstellen Sie ein Formular mit einem Kontrollkästchen und einem E-Mail-Feld, wie in der folgenden Abbildung dargestellt:

![Bedingtes E-Mail-Formular](/help/edge/assets/aem-forms-conditional-email-form.png)


So verwenden Sie eine Regel, um bei der Auswahl eines Kontrollkästchens das E-Mail-Feld anzuzeigen:

1. Legen Sie die Eigenschaft `Value` des Kontrollkästchenfelds auf `TRUE` fest.
1. Legen Sie die Eigenschaft `Checked` des Kontrollkästchenfelds auf `FALSE` fest. Dadurch wird sichergestellt, dass das Kontrollkästchen nicht standardmäßig aktiviert ist.
1. Legen Sie die Eigenschaft `Visible` des E-Mail-Felds auf `=[address of Checked property of the checkbox field] = true()` fest. Beispiel: `=Q11=TRUE()`. Die Formel wertet aus, ob das Kontrollkästchen aktiviert ist oder nicht. Wenn das Kontrollkästchen aktiviert ist, wird die Formel als TRUE ausgewertet. Wenn das Kontrollkästchen nicht aktiviert ist, wird die Formel als FALSE ausgewertet.



   Die Funktion `TRUE()` gibt den logischen Wert zurück, wenn Sie sie so einstellen, dass sie auf die Eigenschaft `Checked` zeigt. Im Falle `checked = false` gibt sie FALSE zurück. Im Falle `checked=true` wird `true` zurückgegeben. Dadurch wird sichergestellt, dass das E-Mail-Feld standardmäßig ausgeblendet wird.


1. Legen Sie die Eigenschaft `Visible Expression` des Kontrollkästchenfelds auf `=FORMULATEXT ((address of Visible property of the checkbox field))` fest. Beispiel: `=FORMULATEXT((G12))`. Die Funktion FORMULATEXT() nimmt eine Formel als Eingabe und gibt die Formel selbst als Textzeichenfolge zurück. Dies hilft bei der Verwendung der Formel im Formular.

   ![Bedingtes E-Mail-Feld](/help/edge/assets/aem-forms-visible-expression-formula-text.png)

1. Zeigen Sie eine Vorschau an und veröffentlichen Sie Ihr Formular. Wenn Sie nun das Kontrollkästchen aktivieren, wird das E-Mail-Feld eingeblendet, während bei Deaktivierung dieses Kontrollkästchens das Feld ausgeblendet wird, wodurch ein dynamisches Anwendererlebnis entsteht.

   ![Bedingte E-Mail](/help/edge/assets/aem-forms-coditional-email.gif)


## Beispiel 2: Automatische Berechnung

In diesem Beispiel wird gezeigt, wie ein Formular die geschätzten Reisekosten bei der Auswahl von Reisedaten in einem Formular automatisch berechnet.

Erstellen Sie ein Formular mit einem Datumsfeld, einem Zimmer-Budget, den Feldern für die geschätzten Reisekosten (siehe unten) und einem E-Mail-Feld (siehe Abbildung unten):

![Bedingtes E-Mail-Formular](/help/edge/assets/aem-forms-automatic-calculations-form.png)

So verwenden Sie eine automatische Berechnung, um die geschätzten Reisekosten anzuzeigen:

1. Legen Sie die Eigenschaft `Value` des Feldes `amount` auf `=F6*DAYS(F3,F2)` fest. Diese Formel berechnet die Anzahl der Tage zwischen `Start Date` und `End Date`, multipliziert die Anzahl der Tage mit dem Zimmer-Budget und zeigt das Ergebnis im Feld `Estimated Trip Cost` an.

1. Setzen Sie die Eigenschaft `Value Expression` des Feldes `Estimated Trip Cost` auf `=FORMULATEXT ((address of value property of the amount field))`. Beispiel: `=FORMULATEXT(F7)`. Die Funktion FORMULATEXT() nimmt eine Formel als Eingabe und gibt die Formel selbst als Textzeichenfolge zurück. Dies hilft bei der Verwendung der Formel im Formular.

1. Zeigen Sie eine Vorschau an und veröffentlichen Sie Ihr Formular. Wenn Sie nun ein `Start Date`, `End Date` und ein Raum-Budget angeben. `Estimated Trip Cost` wird automatisch berechnet.

## Beispiele für Tabellenfunktionen


Im Folgenden finden Sie einige Beispiele für häufig verwendete Tabellenfunktionen:

**Logikfunktionen:**

- **NOT():** Kehrt den logischen Zustand um (TRUE wird FALSE und umgekehrt).

  Beispiel: Ausblenden eines Feldes „E-Mail bestätigen“, wenn das E-Mail-Feld leer gelassen wird.

   1. Legen Sie die Eigenschaft `Visible` des Feldes „E-Mail bestätigen“ auf `=NOT(if('address of email field'=""))` fest.

      ![AEM Forms blendet das Feld „E-Mail bestätigen“ aus](/help/edge/assets/aem-forms-not-function-hide-email-field.png)


   1. Legen Sie den sichtbaren Ausdruck des Feldes „E-Mail bestätigen“ auf `=FORMULATEXT ((address of visible property of the Confirm Email field))` fest.

      ![AEM Forms – sichtbare Ausdrucksformel](/help/edge/assets/aem-forms-visible-expression-formula-text.png)


- AND(): Gibt nur TRUE zurück, wenn alle angegebenen Bedingungen TRUE sind.

   - Beispiel: Die Schaltfläche „Senden“ wird nur dann aktiviert, wenn alle erforderlichen Felder ausgefüllt sind.

   1. Legen Sie die Eigenschaft `Visible` der Schaltfläche „Senden“ fest:



      ```JavaScript
      =AND(NOT(address of `value` property of the `name` field = ""), NOT(address of `value` property of the `email` field = ""), NOT(address of `value` property of the `phone` field))
      ```

      Zum Beispiel:

      ```JavaScript
      =AND(NOT(F9=""), NOT(F12=""), NOT(F10=""))
      ```

   1. Setzen Sie den sichtbaren Ausdruck des Feldes „E-Mail bestätigen“ auf:

      ```JavaScript
      =FORMULATEXT ((address of visible property of the Confirm Email field))
      ```

      Zum Beispiel:

      ```JavaScript
      =FORMULATEXT(G14)
      ```

      Diese Formel zeigt die Schaltfläche „Senden“ (TRUE) nur dann an, wenn alle Felder (Name, E-Mail, Telefon) ausgefüllt sind (NOT(()) liefert jeweils TRUE), andernfalls wird die Schaltfläche ausgeblendet (AND(mehrere FALSES) = FALSE).

- OR(): Gibt TRUE zurück, wenn mindestens eine der angegebenen Bedingungen TRUE ist.

   - Beispiel: Anwenden eines Rabatts, wenn eine Benutzerin bzw. ein Benutzer einen der entsprechenden Rabattgutschein-Codes eingibt.

   1. Setzen Sie die Eigenschaft `Visible` des Feldes „Endbetrag“ auf:


  ```JavaScript
     =IF(OR(F14="BlackFridaySale", F14="NewYearDiscount"), (F6*DAYS(F3,F2)* 0.7) , (F6*DAYS(F3,F2)))
  ```

   1. Setzen Sie den Werteausdruck des Felds „E-Mail bestätigen“ auf:

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      Zum Beispiel:

      ```JavaScript
      =FORMULATEXT(F7)
      ```

      Mit dieser Formel wird ein Rabatt von 30 % berechnet, wenn die Benutzerin bzw. der Benutzer einen Coupon-Code (couponCode = &quot;NewYearDiscount&quot;) ODER (couponCode = &quot;BlackFridaySale&quot;) eingibt. Andernfalls wird der Rabatt auf 0 gesetzt.

**Textfunktionen:**

- IF(): Wertet eine Bedingung aus und gibt einen bestimmten Wert zurück, wenn TRUE, oder einen anderen Wert, wenn FALSE.

   - Beispiel: Anzeige einer benutzerdefinierten Meldung auf der Grundlage einer ausgewählten Produktkategorie.

   1. Legen Sie die Eigenschaft `Value` des Feldes `message` auf `Only upto 7 kg check-in lagguage is allowed!` fest:

   1. Legen Sie die Eigenschaft `Visible` des Feldes `message` auf fest:


      ```JavaScript
      =if(address of value property of chosen product category ="Economy", TRUE(), FALSE())
      ```

      Zum Beispiel:

      ```JavaScript
      =if(F5="Economy", TRUE(), FALSE())
      ```

   1. Setzen Sie den Wertausdruck des Feldes `message` auf:

      ```JavaScript
      =FORMULATEXT ((address of value property of the final amount field))
      ```

      Zum Beispiel:

      ```JavaScript
      =FORMULATEXT(G15)
      ```

      Diese Formel zeigt die Meldung „Nur bis zu 7 kg Check-in-Gepäck ist erlaubt!“ an, wenn die gewählte Klasse „Economy“ ist, andernfalls bleibt das Meldungsfeld leer.

**Mathematische Funktionen:**

- SUM(): Fügt Werte aus einem bestimmten Zellbereich hinzu.

  Beispiel: Berechnung der Gesamtkosten von Artikeln in einem Warenkorb.

  Im Werteausdruck des Felds „Gesamtkosten“: 
SUM(price * quantity)

  Bei dieser Formel wird davon ausgegangen, dass Sie für jedes Element separate Felder für „price“ (Preis) und „quantity“ (Menge) haben. Sie multipliziert diese und verwendet SUM(), um die Gesamtkosten für alle Artikel im Warenkorb zu addieren.

- ROUND(): Rundet eine Zahl auf eine angegebene Anzahl von Dezimalstellen.

  Beispiel: Runden eines berechneten Rabattbetrags auf zwei Dezimalstellen.

  Im Wertausdruck des Feldes „discount“ (Rabattbetrag) (vorausgesetzt, ein Rabatt wird an anderer Stelle berechnet):
ROUND(discount, 2)

  Diese Formel rundet den Rabattwert auf zwei Dezimalstellen.

- MIN(): Gibt den kleinsten der Werte aus einem bestimmten Zellenbereich zurück.

  Beispiel: Ermittlung des erforderlichen Mindestalters für ein Anmeldeformular auf der Grundlage eines ausgewählten Landes.

  Im Wertausdruck eines Feldes „Mindestalter“:
MIN(ageLimits[&quot;US&quot;], ageLimits[&quot;UK&quot;], ageLimits[&quot;France&quot;])

  Bei dieser Formel wird davon ausgegangen, dass Sie über eine Tabelle mit dem Namen „ageLimits“ (Altersbeschränkungen) verfügen, in der die Mindestanforderungen an das Alter für verschiedene Länder gespeichert sind. Sie verwendet MIN(), um den kleinsten Wert unter ihnen zu finden.


Darüber hinaus können Sie mit adaptiven Formularbausteinen die volle Kontrolle über Ihre Formulare übernehmen, indem Sie [benutzerdefinierte Funktionen](#creating-custom-functions) erstellen. Mit benutzerdefinierten Funktionen können Sie Ihre eigenen Regeln und Logiken definieren und so vollständig steuern, wie sich Ihre Formulare verhalten.


## Erstellen und Bereitstellen benutzerdefinierter Funktionen

Der vorkonfigurierte adaptive Formularbaustein bietet Implementierungen für viele [übliche Tabellenkalkulationsfunktionen](#spreadsheet-functions-for-rules). Für eine präzisere Steuerung Ihrer Formulare können Sie jedoch alle vorkonfigurierten Funktionen verwenden, die in Microsoft® Excel oder Google Sheets in Ihren adaptiven Formularbausteinen verfügbar sind. Der adaptive Formularbaustein enthält nicht die Implementierung für alle vorkonfigurierten Funktionen, die in Microsoft® Excel oder Google Sheets zur Verfügung stehen. Wenn Sie eine dieser Funktionen benötigen, können Sie eine benutzerdefinierte Funktion mit einer ähnlichen Syntax entwickeln, um die von Microsoft® Excel oder Google Sheets bereitgestellte Funktionalität zu erreichen. Sie können zum Beispiel die [Microsoft® Excel-Funktion „Year()“](https://support.microsoft.com/de-de/office/calculate-age-113d599f-5fea-448f-a4c3-268927911b37#) implementieren, um das Alter anhand des Geburtsdatums zu berechnen.


### Erstellen einer benutzerdefinierten Funktion

Benutzerdefinierte Funktionen befinden sich in der Datei `[Adaptive form block]/functions.js`. Der Erstellungsprozess umfasst im Allgemeinen die folgenden Schritte:

- Funktionsdeklaration: Definieren der Funktionsnamen und die zugehörigen Parameter (die Eingaben, die akzeptiert werden).
- Logikimplementierung: Schreiben des Codes, der die spezifischen Berechnungen oder Manipulationen beschreibt, die von der Funktion ausgeführt werden.
- Funktionsexport: Ermöglichen, dass die Funktion innerhalb Ihrer Regeln zugänglich ist, indem Sie sie aus der entsprechenden Datei exportieren.

### Beispiel: Year-Funktion

In diesem Beispiel werden zwei benutzerdefinierte Funktionen veranschaulicht, mit denen die Funktion „YEAR()“ von Microsoft® Excel zur Berechnung des Alters imitiert wird:


```JavaScript
/**
 - Get the current date and time
 - @name now
 - @returns {Date} The current date and time as a Date object
 */
function now() {
  const today = new Date();
  return today;
}

/**
 - Get the year from a Date object
 - @name year
 - @param {Date} date The date object
 - @throws {TypeError} If the input is not a Date object
 - @returns {number} The year as a number
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

1. **Hinzufügen der Funktion**: Fügen Sie Ihre benutzerdefinierte Funktion in die Datei `[Adaptive form block]/functions.js` ein. Denken Sie daran, sie der Exportanweisung in der Datei hinzuzufügen.
1. **Bereitstellen der Datei**: Stellen Sie die aktualisierte Datei `functions.js` in Ihrem GitHub-Projekt bereit und überprüfen Sie, ob der Build erfolgreich war.
1. **Funktionsverwendung**: Greifen Sie auf die Funktion innerhalb der Tabellenkalkulation Ihres Formulars zu, indem Sie die Eigenschaften `Value`, `Value Expression`, `Visible` oder `Visible Expression` verwenden, ähnlich wie bei jeder anderen Tabellenkalkulationsfunktion, deren Unterstützung schon vorkonfiguriert ist.
1. **Vorschau des Formulars**: Verwenden Sie AEM Sidekick, um eine Vorschau Ihres Formulars mit der neu implementierten Funktion anzuzeigen.

