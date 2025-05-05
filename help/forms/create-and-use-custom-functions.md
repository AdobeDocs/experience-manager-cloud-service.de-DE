---
title: Verwenden benutzerdefinierter Funktionen in einem adaptiven Formular
description: AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzende ihre eigenen Funktionen im Regeleditor erstellen und verwenden können.
keywords: Im Regeleditor können Sie eine benutzerdefinierte Funktion hinzufügen, eine benutzerdefinierte Funktion verwenden, eine benutzerdefinierte Funktion erstellen oder eine benutzerdefinierte Funktion verwenden.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
role: User, Developer
source-git-commit: 747203ccd3c7e428e2afe27c56e47c3ec18699f6
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 54%

---


# Einführung in benutzerdefinierte Funktionen für adaptive Formulare, die auf Kernkomponenten basieren

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions) |
| AEM as a Cloud Service | Dieser Artikel |

AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzende JavaScript-Funktionen definieren können, um komplexe Geschäftsregeln zu implementieren. Diese benutzerdefinierten Funktionen erweitern die Funktionen von Formularen durch die Erleichterung der Bearbeitung und Verarbeitung der eingegebenen Daten, um bestimmte Anforderungen zu erfüllen. Sie ermöglichen eine dynamische Änderung des Formularverhaltens auf der Grundlage vordefinierter Kriterien. Mit benutzerdefinierten Funktionen können Entwicklerinnen und Entwickler auch komplexe Validierungslogiken durchsetzen, dynamische Berechnungen durchführen und die Anzeige oder das Verhalten von Formularelementen basierend auf Benutzerinteraktionen oder vordefinierten Kriterien steuern.

>[!NOTE]
>
> Stellen Sie sicher[ dass die ](https://github.com/adobe/aem-core-forms-components)Kernkomponente“ auf die neueste Version eingestellt ist, um die neuesten Funktionen zu verwenden.

## Vorteile benutzerdefinierter Funktionen {#uses-of-custom-function}

Die Verwendung benutzerdefinierter Funktionen in adaptiven Formularen bietet folgende Vorteile:
* **Datenverarbeitung**: Benutzerdefinierte Funktionen helfen bei der Verarbeitung der in die Formularfelder eingegebenen Daten.
* **Datenvalidierung**: Benutzerdefinierte Funktionen ermöglichen Ihnen benutzerdefinierte Überprüfungen von Formulareingaben und das Anzeigen bestimmter Fehlermeldungen.
* **Dynamisches Verhalten**: Mit benutzerdefinierten Funktionen können Sie das dynamische Verhalten Ihrer Formulare anhand bestimmter Bedingungen steuern. Beispielsweise können Sie Felder ein-/ausblenden, Feldwerte ändern oder die Formularlogik dynamisch anpassen.
* **Integration**: Sie können benutzerdefinierte Funktionen zur Integration mit externen APIs oder Diensten verwenden. Dies ist hilfreich beim Abrufen von Daten aus externen Quellen, beim Senden von Daten an externe REST-Endpunkte oder beim Ausführen benutzerdefinierter Aktionen entsprechend externer Ereignisse.

Benutzerdefinierte Funktionen sind im Wesentlichen Client-Bibliotheken, die in der JavaScript-Datei hinzugefügt werden. Nachdem Sie eine benutzerdefinierte Funktion erstellt haben, steht sie im Regeleditor zur Auswahl durch den Benutzer in einem adaptiven Formular zur Verfügung. Die benutzerdefinierten Funktionen sind im Regeleditor anhand der JavaScript-Anmerkungen zu erkennen.

## Unterstützte JavaScript-Anmerkungen für benutzerdefinierte Funktionen {#js-annotations}

JavaScript-Anmerkungen werden verwendet, um Metadaten für JavaScript-Code bereitzustellen. Sie enthält Kommentare, die mit bestimmten Symbolen beginnen, z. B. /** und @. Die Anmerkungen enthalten wichtige Informationen zu Funktionen, Variablen und anderen Elementen im Code. Adaptive Formulare unterstützen die folgenden JavaScript-Anmerkungen für benutzerdefinierte Funktionen:

### Name

Der Name wird verwendet, um die benutzerdefinierte Funktion im Regeleditor eines adaptiven Formulars zu identifizieren. Die folgenden Syntaxen werden zum Benennen einer benutzerdefinierten Funktion verwendet:

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`.
  `functionName` ist der Name der Funktion. Leerzeichen sind nicht zulässig.
  `<Function Name>` ist der Anzeigename der Funktion im Regeleditor eines adaptiven Formulars.
Wenn der Anzeigename der Funktion mit dem Namen der Funktion selbst übereinstimmt, können Sie in der Syntax `[functionName]` weglassen.

### Parameter

Der Parameter ist eine Liste der von benutzerdefinierten Funktionen verwendeten Argumente. Eine Funktion kann mehrere Parameter unterstützen. Die folgenden Syntaxen werden verwendet, um einen Parameter in einer benutzerdefinierten Funktion zu definieren:

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`.
  `{type}` stellt den Parametertyp dar.  Zulässige Parametertypen sind:

   * string: Stellt einen einzelnen Zeichenfolgenwert dar.
   * number: Stellt einen einzelnen numerischen Wert dar.
   * boolean: Stellt einen einzelnen booleschen Wert dar (true oder false).
   * string[]: Stellt ein Array von Zeichenfolgenwerten dar.
   * number[]: Stellt ein Array numerischer Werte dar.
   * boolean[]: Stellt ein Array boolescher Werte dar.
   * date: Stellt einen einzelnen Datumswert dar.
   * date[]: Stellt ein Array von Datumswerten dar.
   * array: Stellt ein generisches Array dar, das Werte verschiedener Typen enthält.
   * object: Stellt ein an eine benutzerdefinierte Funktion übergebenes Formularobjekt dar, anstatt dessen Wert direkt weiterzugeben.
   * scope: Stellt das Globals-Objekt dar, das schreibgeschützte Variablen wie Formularinstanzen, Zielfeldinstanzen und Methoden zum Ausführen von Formularänderungen in benutzerdefinierten Funktionen enthält. Er wird als letzter Parameter in JavaScript-Anmerkungen deklariert und ist im Regeleditor eines adaptiven Formulars nicht sichtbar. Der Parameter „scope“ greift auf das Objekt des Formulars oder der Komponente zu, um die für die Formularverarbeitung erforderliche Regel oder das Ereignis auszulösen. Weitere Informationen zum Globals-Objekt und dessen Verwendung finden Sie [hier](/help/forms/custom-function-core-component-scope-function.md).

Beim Parametertyp wird nicht zwischen Groß- und Kleinschreibung unterschieden und im Parameternamen sind keine Leerzeichen zulässig.

`<Parameter Description>` enthält Details zum Zweck des Parameters. Dies kann aus mehreren Wörtern bestehen.

#### Optionale Parameter

Standardmäßig sind alle Parameter obligatorisch. Sie können einen Parameter als optional definieren, indem Sie entweder `=` nach dem Parametertyp hinzufügen oder den Parameternamen in `[]` einschließen. Parameter, die in JavaScript-Anmerkungen als optional definiert sind, werden im Regeleditor als optional angezeigt.
Um eine Variable als optionalen Parameter zu definieren, können Sie eine der folgenden Syntaxen verwenden:

* `@param {type=} Input1`

In der obigen Codezeile ist `Input1` ein optionaler Parameter ohne Standardwert. So deklarieren Sie optionale Parameter mit dem Standardwert:
`@param {string=<value>} input1`

`input1` als optionaler Parameter, wobei der Standardwert auf `value` festgelegt ist.

* `@param {type} [Input1]`

In der obigen Codezeile ist `Input1` ein optionaler Parameter ohne Standardwert. So deklarieren Sie optionale Parameter mit dem Standardwert:
`@param {array} [input1=<value>]`
`input1` ist ein optionaler Parameter des Array-Typs, dessen Standardwert auf `value` festgelegt ist.
Stellen Sie sicher, dass der Parametertyp in geschweiften Klammern {} und der Parametername in eckigen Klammern eingeschlossen ist.

Betrachten Sie das folgende Codefragment, bei dem input2 als optionaler Parameter definiert ist:

```javascript
        /**
         * optional parameter function
         * @name OptionalParameterFunction
         * @param {string} input1 
         * @param {string=} input2 
         * @return {string}
        */
        function OptionalParameterFunction(input1, input2) {
        let result = "Result: ";
        result += input1;
        if (input2 !== null) {
            result += " " + input2;
        }
        return result;
        }
```

Die folgende Abbildung zeigt die Verwendung der benutzerdefinierten Funktion `OptionalParameterFunction` im Regeleditor:

![Optionale oder erforderliche Parameter ](/help/forms/assets/optional-default-params.png)

Sie können die Regel speichern, ohne einen Wert für die erforderlichen Parameter anzugeben, aber die Regel wird nicht ausgeführt und zeigt eine Warnmeldung als:

![Unvollständige Regelwarnung](/help/forms/assets/incomplete-rule.png)

Wenn der/die Benutzende den optionalen Parameter leer lässt, wird der Wert „Undefiniert“ an die benutzerdefinierte Funktion für den optionalen Parameter übergeben.

Weitere Informationen zum Definieren optionaler Parameter in JSDocs finden Sie [hier](https://jsdoc.app/tags-param).

### Rückgabetyp

Der Rückgabetyp gibt den Typ des Werts an, den die benutzerdefinierte Funktion nach der Ausführung zurückgibt. Die folgenden Syntaxen werden verwendet, um einen Rückgabetyp in einer benutzerdefinierten Funktion zu definieren:

* `@return {type}`
* `@returns {type}`
  `{type}` gibt den Rückgabetyp der Funktion an. Zulässige Rückgabetypen sind:
   * string: Stellt einen einzelnen Zeichenfolgenwert dar.
   * number: Stellt einen einzelnen numerischen Wert dar.
   * boolean: Stellt einen einzelnen booleschen Wert dar (true oder false).
   * string[]: Stellt ein Array von Zeichenfolgenwerten dar.
   * number[]: Stellt ein Array numerischer Werte dar.
   * boolean[]: Stellt ein Array boolescher Werte dar.
   * date: Stellt einen einzelnen Datumswert dar.
   * date[]: Stellt ein Array von Datumswerten dar.
   * array: Stellt ein generisches Array dar, das Werte verschiedener Typen enthält.
   * object: Stellt das Formularobjekt anstatt direkt den Wert dar.

  Beim Rückgabetyp wird nicht zwischen Groß- und Kleinschreibung unterschieden.

### Privat

Die als privat deklarierte benutzerdefinierte Funktion wird nicht in der Liste der benutzerdefinierten Funktionen im Regeleditor eines adaptiven Formulars angezeigt. Standardmäßig sind benutzerdefinierte Funktionen öffentlich. Die Syntax zum Deklarieren der benutzerdefinierten Funktion als privat lautet `@private`.


## Richtlinien beim Erstellen benutzerdefinierter Funktionen

Um die benutzerdefinierten Funktionen im Regeleditor aufzulisten, können Sie eines der folgenden Formate verwenden:

### Funktionsanweisung mit oder ohne jsdoc-Kommentare

Sie können eine benutzerdefinierte Funktion mit oder ohne jsdoc-Kommentare erstellen.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```

Wenn Benutzende zu einer benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügen, wird sie im Regeleditor anhand ihres Funktionsnamens aufgelistet. Es wird jedoch empfohlen, JavaScript-Anmerkungen einzubeziehen, um die Lesbarkeit der benutzerdefinierten Funktionen zu verbessern.

### Pfeilfunktion mit obligatorischen JavaScript-Anmerkungen oder -Kommentaren

Sie können eine benutzerdefinierte Funktion mit einer Pfeilfunktionssyntax erstellen:

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} a parameter description
    * @param {string=} b parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
    /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;
    
```

Wenn Benutzende der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügen, wird die benutzerdefinierte Funktion nicht im Regeleditor eines adaptiven Formulars aufgeführt.

### Funktionsausdruck mit obligatorischen JavaScript-Anmerkungen oder -Kommentaren

Um benutzerdefinierte Funktionen im Regeleditor eines adaptiven Formulars aufzulisten, erstellen Sie benutzerdefinierte Funktionen im folgenden Format:

```javascript
    /**
    * test function
    * @name testFunction 
    * @param {string} input1 parameter description
    * @param {string=} input2 parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

Wenn Benutzende der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügen, wird die benutzerdefinierte Funktion nicht im Regeleditor eines adaptiven Formulars aufgeführt.

## Nächster Schritt

Informationen zum Erstellen und Verwenden einer benutzerdefinierten Funktion in Ihrem adaptiven Formular finden Sie im Artikel [Erstellen einer benutzerdefinierten Funktion für ein adaptives Formular basierend auf Kernkomponenten](/help/forms/custom-function-core-component-create-function.md) .

## Siehe auch

{{see-also-rule-editor}}