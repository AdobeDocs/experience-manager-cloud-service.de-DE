---
title: Unterstützung der Picture-Klausel für HTML5-Formulare
description: HTML5-Formulare unterstützen die XFA-Picture-Klausel für Anzeigewerte und formatierte Werte für Datumsangaben, Text und numerische Symbole.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 5e344be7-46cd-4e1f-ae3a-1f89c645cffe
feature: HTML5 Forms,Mobile Forms
exl-id: 7f9c77c6-447a-407f-ae58-6735176dc99c
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 22aeedaaf4171ad295199a989e659b6bf5ce9834
workflow-type: tm+mt
source-wordcount: '670'
ht-degree: 95%

---

# Unterstützung der Picture-Klausel für HTML5-Formulare {#picture-clause-support-for-html-forms}

<span class="preview"> Die HTML5 Forms-Funktion wird als Teil des Early Access-Programms angeboten. Um den Zugriff anzufordern, senden Sie eine E-Mail von Ihrer offiziellen (geschäftlichen) E-Mail-ID an aem-forms-ea@adobe.com.
</span>

HTML5-Formulare unterstützen die XFA-Picture-Klausel für Anzeigewerte und formatierte Werte für Datumsangaben, Text und numerische Symbole. Folgende Picture-Klauselausdrücke werden unterstützt:

* category(locale){picture-clause} | category(locale){picture-clause} | category(locale){picture-clause}
* category.subcategory{}

>[!NOTE]
>
>Mobile Forms unterstützt derzeit keine Edit Picture-Klausel. Außerdem werden die Klauselsymbole DateTime und Time Picture nicht unterstützt.

## Unterstützte Datumsfeldsymbole {#supported-date-field-symbols}

Unterstützter Ausdruck für Date Picture-Klausel:

* date.long{}
* date.short{}
* date.medium{}
* date.full{}
* date.short{}
* Datum{date Picture Clause symbols}

>[!NOTE]
>
>Das Standardmuster der Picture-Klausel ist das Muster {MMM D, YYYY}. Wird kein Muster angewendet, wird das Standardmuster verwendet.

<table>
 <tbody>
  <tr>
   <th><strong>Symbol</strong></th>
   <th>Interpretation</th>
  </tr>
  <tr>
   <td>D</td>
   <td>1- oder 2-stelliger (1–31) Tag des Monats</td>
  </tr>
  <tr>
   <td>DD</td>
   <td>Mit 0 aufgefüllter zweistelliger (01–31) Tag des Monats.<br /> </td>
  </tr>
  <tr>
   <td>M</td>
   <td>1- oder 2-stelliger (1–12) Monat des Jahres.<br /> </td>
  </tr>
  <tr>
   <td>MM</td>
   <td>Mit 0 aufgefüllter zweistelliger (01–12) Monat des Jahres.<br /> </td>
  </tr>
  <tr>
   <td>MMM</td>
   <td>Abgekürzter Monatsname des aktuellen Gebietsschemas<br /> </td>
  </tr>
  <tr>
   <td>MMMM</td>
   <td>Vollständiger Monatsname des aktuellen Gebietsschemas<br /> </td>
  </tr>
  <tr>
   <td>EEE</td>
   <td>Abgekürzter Wochentag des aktuellen Gebietsschemas<br /> </td>
  </tr>
  <tr>
   <td>EEEE</td>
   <td>Vollständiger Wochentag des aktuellen Gebietsschemas<br /> </td>
  </tr>
  <tr>
   <td>YY</td>
   <td>2-stellige Jahreszahl, wobei 00 = 2000, 29 = 2029, 30 = 1930 und 99 = 1999<br /> </td>
  </tr>
  <tr>
   <td>YYYY</td>
   <td>4-stellige Jahreszahl<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
> Das Datumsfeld in HTML5-Formularen unterstützt das Muster `MM-YYYY` im Bearbeitungsformat nicht wie erwartet. Das Muster wird jedoch im Anzeigeformat unterstützt.

## Numeric Picture-Klausel {#numeric-picture-clause}

HTML5-Formulare unterstützen Numeric Picture-Symbole. Es gibt jedoch einen Unterschied bei der Unterstützung zwischen PDF-Formularen und HTML-Formularen.

In **PDF-Formularen** wird eine Zahl unabhängig von der Anzahl der Symbole in der Picture-Klausel formatiert.

In **HTML-Formularen** wird eine Zahl nur formatiert, wenn die Zahl weniger Ziffern enthält als die Anzahl der Symbole in der Picture-Klausel.

**Beispiel**: Man nehme eine Picture-Klausel: num{zzz,zzz,zz9}.

Die Zahl **10000** ist formatiert als **10.000** sowohl in HTML- als auch in PDF-Formularen.

Die Zahl 1000000 ist in PDF-Formularen als 1.000.000 formatiert. In HTML-Formularen bleibt die Zahl jedoch unformatiert als 1000000.

Unterstützte Ausdrücke für die numerische Picture-Klausel in **HTML-Formularen** sind:

* num.integer{}
* num.decimal{}
* num.currency{}
* num.percent{}
* Anzahl{Numeric Picture Clause Symbols}

<table>
 <tbody>
  <tr>
   <th><strong>Symbol</strong></th>
   <th><strong>Interpretation</strong></th>
   <th>Eingabe-Analyse</th>
  </tr>
  <tr>
   <td>9</td>
   <td><strong>Ausgabeformatierung</strong>: eine einzelne Ziffer. Oder die Ziffer Null, wenn die Eingabedaten leer sind oder sich an der entsprechenden Position ein Leerzeichen befindet.<br /> </td>
   <td>Einzelne Ziffer</td>
  </tr>
  <tr>
   <td>Z</td>
   <td><strong>Ausgabeformatierung</strong>: eine einzelne Ziffer. Oder ein Leerzeichen, wenn die Eingabedaten leer sind oder sich an der entsprechenden Position die Ziffer Null befindet.<br /> </td>
   <td>Einzelne Ziffer oder Leerzeichen</td>
  </tr>
  <tr>
   <td>z</td>
   <td><strong>Ausgabeformatierung</strong>: eine einzelne Ziffer. Oder nichts, wenn die Eingabedaten leer sind oder sich an der entsprechenden Position die Ziffer Null befindet.<br /> </td>
   <td>Einzelne Ziffer oder nichts</td>
  </tr>
  <tr>
   <td>E</td>
   <td><strong>Ausgabeformatierung</strong>: der Exponententeil einer Gleitkommazahl, bestehend aus dem Exponentialsymbol (E). Gefolgt von einem optionalen Plus- oder Minuszeichen. Gefolgt vom Exponentenwert.<br /> </td>
   <td>Derselbe Wert wie für die Ausgabeformatierung</td>
  </tr>
  <tr>
   <td>CR oder cr<br /> </td>
   <td>Kreditsymbol (CR), wenn die Zahl negativ ist. Andernfalls nichts.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>S oder s<br /> </td>
   <td>Ausgabeformatierung: ein Minuszeichen, wenn die Zahl negativ ist. Andernfalls Leerzeichen.<br /> </td>
   <td>Minuszeichen, wenn die Zahl negativ ist; Pluszeichen, wenn die Zahl positiv ist</td>
  </tr>
  <tr>
   <td>V</td>
   <td>Dezimalwurzel des maßgeblichen Gebietsschemas. Einbeziehen der Dezimalwurzel in die Eingabeanalyse.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>v</td>
   <td>Dezimalwurzel des maßgeblichen Gebietsschemas. Einbeziehen der Dezimalwurzel in die Eingabeanalyse und Ausgabeformatierung.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>.</td>
   <td>Dezimalwurzel des maßgeblichen Gebietsschemas.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>, (U+FF0C)</td>
   <td>Gruppierungstrennzeichen des maßgeblichen Gebietsschemas</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>$ (U+FF04)</td>
   <td>Währungssymbol des maßgeblichen Gebietsschemas.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>% (U+FF05)</td>
   <td>Prozentsymbol des maßgeblichen Gebietsschemas.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>( (U+FF08)</td>
   <td>Linke Klammer, wenn die Zahl negativ ist. Andernfalls Leerzeichen.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>) (U+FF09)</td>
   <td>Rechte Klammer, wenn die Zahl negativ ist. Andernfalls Leerzeichen.</td>
   <td><br type="_moz" /> </td>
  </tr>
  <tr>
   <td>t</td>
   <td>Tabulatorzeichen.</td>
   <td><br type="_moz" /> </td>
  </tr>
 </tbody>
</table>

## Text-Picture-Klausel {#text-picture-clause}

HTML5-Formulare unterstützen die folgenden Text-Picture-Klauselausdrücke:

* Text{text Picture clause symbols}

| **Symbol** | **Interpretation** |
|---|---|
| A | Einzelner Buchstabe. |
| X | Einzelnes Zeichen. |
| O | Einzelnes alphanumerisches Zeichen. |
| 0 (Null) | Einzelnes alphanumerisches Zeichen. |
| 9 | Einzelne Ziffer. |
