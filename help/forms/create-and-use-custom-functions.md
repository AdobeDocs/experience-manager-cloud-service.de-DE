---
title: Erstellen und Hinzufügen benutzerdefinierter Funktionen in einem adaptiven Formular
description: AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer eigene Funktionen im Regeleditor erstellen und verwenden können.
keywords: Fügen Sie eine benutzerdefinierte Funktion hinzu, verwenden Sie eine benutzerdefinierte Funktion, erstellen Sie eine benutzerdefinierte Funktion, verwenden Sie eine benutzerdefinierte Funktion im Regeleditor.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
source-git-commit: 494e90bd5822495f0619e8ebf55f373a26a3ffe6
workflow-type: tm+mt
source-wordcount: '3521'
ht-degree: 4%

---


<span class="preview"> Dieser Artikel enthält `Override form submission success and error handlers` als Vorab-Release-Funktion. Die Vorabversion-Funktion ist nur über unsere [Pre-Release-Kanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features).

# Benutzerdefinierte Funktionen in Adaptive Forms (Kernkomponenten)

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions) |
| AEM as a Cloud Service | Dieser Artikel |

## Einführung

AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer JavaScript-Funktionen zur Implementierung komplexer Geschäftsregeln definieren können. Diese benutzerdefinierten Funktionen erweitern die Funktionen von Formularen, indem sie die Manipulation und Verarbeitung der eingegebenen Daten zur Erfüllung bestimmter Anforderungen erleichtern. Sie ermöglichen auch eine dynamische Änderung des Formularverhaltens basierend auf vordefinierten Kriterien.

>[!NOTE]
>
> Stellen Sie sicher, dass [Kernkomponente](https://github.com/adobe/aem-core-forms-components) auf die neueste Version eingestellt ist, um die neuesten Funktionen zu verwenden.

### Verwendung benutzerdefinierter Funktionen {#uses-of-custom-function}

Die Verwendung benutzerdefinierter Funktionen in Adaptive Forms bietet folgende Vorteile:
* **Datenverarbeitung**: Benutzerdefinierte Funktionen helfen bei der Verarbeitung der in die Formularfelder eingegebenen Daten.
* **Datenvalidierung**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, benutzerdefinierte Prüfungen von Formulareingaben durchzuführen und bestimmte Fehlermeldungen bereitzustellen.
* **Dynamisches Verhalten**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, das dynamische Verhalten Ihrer Formulare anhand bestimmter Bedingungen zu steuern. Beispielsweise können Sie Felder ein-/ausblenden, Feldwerte ändern oder die Formularlogik dynamisch anpassen.
* **Integration**: Sie können benutzerdefinierte Funktionen zur Integration mit externen APIs oder Diensten verwenden. Dies hilft beim Abrufen von Daten aus externen Quellen, beim Senden von Daten an externe REST-Endpunkte oder beim Ausführen benutzerdefinierter Aktionen basierend auf externen Ereignissen.

Benutzerdefinierte Funktionen sind im Wesentlichen Client-Bibliotheken, die in der JavaScript-Datei hinzugefügt werden. Nachdem Sie eine benutzerdefinierte Funktion erstellt haben, steht sie im Regeleditor zur Auswahl durch den Benutzer in einem adaptiven Formular zur Verfügung. Die benutzerdefinierten Funktionen werden durch die JavaScript-Anmerkungen im Regeleditor identifiziert.

### Unterstützte JavaScript-Anmerkungen für benutzerdefinierte Funktionen {#js-annotations}

JavaScript-Anmerkungen werden verwendet, um Metadaten für JavaScript-Code bereitzustellen. Es enthält Kommentare, die mit bestimmten Symbolen beginnen, z. B. /** und @. Die Anmerkungen enthalten wichtige Informationen zu Funktionen, Variablen und anderen Elementen im Code. Das adaptive Formular unterstützt die folgenden JavaScript-Anmerkungen für benutzerdefinierte Funktionen:

#### Name

Der Name wird verwendet, um die benutzerdefinierte Funktion im Regeleditor eines adaptiven Formulars zu identifizieren. Die folgenden Syntaxen werden verwendet, um eine benutzerdefinierte Funktion zu benennen:

* `@name [functionName] <Function Name>`
* `@function [functionName] <Function Name>`
* `@func [functionName] <Function Name>`.
  `functionName` ist der Name der Funktion. Leerzeichen sind nicht zulässig.
  `<Function Name>` ist der Anzeigename der Funktion im Regeleditor eines adaptiven Formulars.
Wenn der Name der Funktion mit dem Namen der Funktion selbst übereinstimmt, können Sie `[functionName]` aus der Syntax.

#### Parameter

Der Parameter ist eine Liste von Argumenten, die von benutzerdefinierten Funktionen verwendet werden. Eine Funktion kann mehrere Parameter unterstützen. Die folgenden Syntaxen werden verwendet, um einen Parameter in einer benutzerdefinierten Funktion zu definieren:

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`.
  `{type}` stellt den Parametertyp dar.  Zulässige Parametertypen sind:

   * string: Stellt einen einzelnen Zeichenfolgenwert dar.
   * number: Stellt einen einzelnen numerischen Wert dar.
   * boolean: Stellt einen einzelnen booleschen Wert dar (true oder false).
   * Zeichenfolge[]: Stellt ein Array von Zeichenfolgenwerten dar.
   * number[]: Stellt ein Array numerischer Werte dar.
   * boolean[]: Stellt ein Array boolescher Werte dar.
   * date: Stellt einen einzelnen Datumswert dar.
   * date[]: Stellt ein Array von Datumswerten dar.
   * array: Stellt ein generisches Array dar, das Werte verschiedener Typen enthält.
   * object: Stellt ein an eine benutzerdefinierte Funktion übergebenes Formularobjekt dar, anstatt dessen Wert direkt weiterzugeben.
   * scope: Stellt das global -Objekt dar, das schreibgeschützte Variablen wie Formularinstanzen, Zielfeldinstanzen und Methoden zum Ausführen von Formularänderungen innerhalb benutzerdefinierter Funktionen enthält. Sie wird als letzter Parameter in JavaScript-Anmerkungen deklariert und ist im Regeleditor eines adaptiven Formulars nicht sichtbar. Der Parameter scope greift auf das Objekt des Formulars oder der Komponente zu, um die für die Formularverarbeitung erforderliche Regel oder das Ereignis Trigger. Weitere Informationen zum Globals-Objekt und dessen Verwendung finden Sie unter [Klicken Sie hier](/help/forms/create-and-use-custom-functions.md#support-field-and-global-objects).

Beim Parametertyp wird nicht zwischen Groß- und Kleinschreibung unterschieden und Leerzeichen sind im Parameternamen nicht zulässig.

`<Parameter Description>` enthält Details zum Zweck des Parameters. Es kann mehrere Wörter enthalten.

**Optionale Parameter**
Standardmäßig sind alle Parameter obligatorisch. Sie können einen Parameter als optional definieren, indem Sie entweder `=` nach dem Parametertyp oder , der den Parameternamen in  `[]`. Parameter, die in JavaScript-Anmerkungen als optional definiert wurden, werden im Regeleditor als optional angezeigt.
Um eine Variable als optionalen Parameter zu definieren, können Sie eine der folgenden Syntaxen verwenden:

* `@param {type=} Input1`

In der obigen Codezeile `Input1` ist ein optionaler Parameter ohne Standardwert. So deklarieren Sie einen optionalen Parameter mit dem Standardwert:
`@param {string=<value>} input1`

`input1` als optionalen Parameter verwenden, wobei der Standardwert auf `value`.

* `@param {type} [Input1]`

In der obigen Codezeile `Input1` ist ein optionaler Parameter ohne Standardwert. So deklarieren Sie einen optionalen Parameter mit dem Standardwert:
`@param {array} [input1=<value>]`
`input1` ist ein optionaler Parameter des Array-Typs, dessen Standardwert auf `value`.
Stellen Sie sicher, dass der Parametertyp in geschweifte Klammern eingeschlossen ist. {} und der Parametername in eckigen Klammern eingeschlossen ist [].

Betrachten Sie das folgende Code-Snippet, bei dem input2 als optionaler Parameter definiert ist:

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

Die folgende Abbildung zeigt mithilfe der `OptionalParameterFunction` benutzerdefinierte Funktion im Regeleditor:

![Optionale oder erforderliche Parameter ](/help/forms/assets/optional-default-params.png)

Sie können die Regel speichern, ohne einen Wert für die erforderlichen Parameter anzugeben. Die Regel wird jedoch nicht ausgeführt und es wird eine Warnmeldung angezeigt, wie folgt:

![unvollständige Regelwarnung](/help/forms/assets/incomplete-rule.png)

Wenn der Benutzer den optionalen Parameter leer lässt, wird der Wert &quot;Undefined&quot;an die benutzerdefinierte Funktion für den optionalen Parameter übergeben.

Weitere Informationen zum Definieren optionaler Parameter in JSDocs finden Sie unter [Klicken Sie hier](https://jsdoc.app/tags-param).

#### Rückgabetyp

Der Rückgabetyp gibt den Typ des Werts an, den die benutzerdefinierte Funktion nach der Ausführung zurückgibt. Die folgenden Syntaxen werden verwendet, um einen Rückgabetyp in einer benutzerdefinierten Funktion zu definieren:

* `@return {type}`
* `@returns {type}`
  `{type}` stellt den Rückgabetyp der Funktion dar. Zulässige Rückgabetypen sind:
   * string: Stellt einen einzelnen Zeichenfolgenwert dar.
   * number: Stellt einen einzelnen numerischen Wert dar.
   * boolean: Stellt einen einzelnen booleschen Wert dar (true oder false).
   * Zeichenfolge[]: Stellt ein Array von Zeichenfolgenwerten dar.
   * number[]: Stellt ein Array numerischer Werte dar.
   * boolean[]: Stellt ein Array boolescher Werte dar.
   * date: Stellt einen einzelnen Datumswert dar.
   * date[]: Stellt ein Array von Datumswerten dar.
   * array: Stellt ein generisches Array dar, das Werte verschiedener Typen enthält.
   * object: Stellt direkt das Formularobjekt anstelle des Werts dar.

  Beim Rückgabetyp wird nicht zwischen Groß- und Kleinschreibung unterschieden.

#### Privat

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
Wenn der Benutzer der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügt, wird sie im Regeleditor anhand ihres Funktionsnamens aufgelistet. Es wird jedoch empfohlen, JavaScript-Anmerkungen einzufügen, um die Lesbarkeit der benutzerdefinierten Funktionen zu verbessern.

### Pfeilfunktion mit obligatorischen JavaScript-Anmerkungen oder Kommentaren

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

Wenn der Benutzer der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügt, wird die benutzerdefinierte Funktion nicht im Regeleditor eines adaptiven Formulars aufgeführt.

### Funktionsausdruck mit obligatorischen JavaScript-Anmerkungen oder Kommentaren

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

Wenn der Benutzer der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügt, wird die benutzerdefinierte Funktion nicht im Regeleditor eines adaptiven Formulars aufgeführt.

## Erstellen einer benutzerdefinierten Funktion {#create-custom-function}

Erstellen Sie eine Client-Bibliothek, um benutzerdefinierte Funktionen im Regeleditor aufzurufen. Weitere Informationen finden Sie unter [Verwenden Client-seitiger Bibliotheken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=de#developing).

Schritte zum Erstellen benutzerdefinierter Funktionen:
1. [Erstellen einer Client-Bibliothek](#create-client-library)
1. [Clientbibliothek zu einem adaptiven Formular hinzufügen](#use-custom-function)

### Erstellen einer Client-Bibliothek {#create-client-library}

Sie können benutzerdefinierte Funktionen hinzufügen, indem Sie eine Client-Bibliothek hinzufügen. Um eine Client-Bibliothek zu erstellen, führen Sie die folgenden Schritte aus:

1. [Klonen Sie Ihr AEM Forms as a Cloud Service-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).
1. Erstellen Sie einen Ordner unter dem Ordner `[AEM Forms as a Cloud Service repository folder]/apps/`. Erstellen Sie beispielsweise einen Ordner mit dem Namen `experience-league`.
1. Navigieren Sie zu `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` und erstellen Sie eine `ClientLibraryFolder`. Erstellen Sie beispielsweise einen Client-Bibliotheksordner als `customclientlibs`.
1. Hinzufügen einer Eigenschaft `categories` mit einem Zeichenfolgentyp -Wert. Weisen Sie beispielsweise den Wert zu `customfunctionscategory` der `categories` -Eigenschaft für `customclientlibs` Ordner.

   >[!NOTE]
   >
   > Sie können einen beliebigen Namen für `client library folder` und `categories` -Eigenschaft.

1. Erstellen Sie einen Ordner mit dem Namen `js`.
1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/customclientlibs/js`.
1. Fügen Sie eine JavaScript-Datei hinzu, z. B. `function.js`. Die Datei enthält den Code für die benutzerdefinierte Funktion.
1. Speichern Sie die Datei `function.js`.
1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/customclientlibs/js`.
1. Hinzufügen einer Textdatei als `js.txt`. Die Datei enthält:

   ```javascript
       #base=js
       functions.js
   ```

1. Speichern Sie die Datei `js.txt`.
1. Fügen Sie die Änderungen mit den folgenden Befehlen hinzu, übertragen Sie sie und pushen Sie sie in das Repository:

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. [Pipeline ausführen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline) , um die benutzerdefinierte Funktion bereitzustellen.

Sobald die Pipeline erfolgreich ausgeführt wurde, wird die in der Client-Bibliothek hinzugefügte benutzerdefinierte Funktion in Ihrer [Regeleditor für adaptive Formulare](/help/forms/rule-editor-core-components.md).

### Clientbibliothek zu einem adaptiven Formular hinzufügen{#use-custom-function}

Nachdem Sie Ihre Client-Bibliothek in Ihrer Forms CS-Umgebung bereitgestellt haben, verwenden Sie die zugehörigen Funktionen in Ihrem adaptiven Formular. Hinzufügen der Client-Bibliothek zum adaptiven Formular

1. Öffnen Sie das Formular im Bearbeitungsmodus. Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und wählen Sie **[!UICONTROL Bearbeiten]**.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Allgemein]** und wählen Sie den Namen der **[!UICONTROL Client-Bibliothekskategorie]** aus der Dropdown-Liste aus (in diesem Fall wählen Sie `customfunctionscategory`).

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > Es können mehrere Kategorien hinzugefügt werden, indem Sie eine kommagetrennte Liste innerhalb der **[!UICONTROL Kategorie der Client-Bibliothek]** -Feld.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Sie können die benutzerdefinierte Funktion im [Regeleditor eines adaptiven Formulars](/help/forms/rule-editor-core-components.md) mithilfe der [JavaScript-Anmerkungen](##js-annotations).

## Verwenden einer benutzerdefinierten Funktion in einem adaptiven Formular

In einem adaptiven Formular können Sie [benutzerdefinierte Funktionen im Regeleditor](/help/forms/rule-editor-core-components.md). Fügen Sie der JavaScript-Datei (`Function.js` ), um das Alter basierend auf dem Geburtsdatum (JJJ-MM-TT) zu berechnen. Erstellen Sie eine benutzerdefinierte Funktion als `calculateAge()` , das das Geburtsdatum als Eingabe annimmt und das Alter zurückgibt:

```javascript
    /**
        * Calculates Age
        * @name calculateAge
        * @param {object} field
        * @return {string} 
    */

    function calculateAge(field) {
    var dob = new Date(field);
    var now = new Date();

    var age = now.getFullYear() - dob.getFullYear();
    var monthDiff = now.getMonth() - dob.getMonth();

    if (monthDiff < 0 || (monthDiff === 0 && now.getDate() < dob.getDate())) {
    age--;
    }

    return age;
    }
```

Wenn der Benutzer im obigen Beispiel das Geburtsdatum im Format (JJJJ-MM-TT) eingibt, wird die benutzerdefinierte Funktion `calculateAge` aufgerufen wird und das Alter zurückgibt.

![Benutzerdefinierte Funktion &quot;Seite berechnen&quot;im Regeleditor](/help/forms/assets/custom-function-calculate-age.png)

Sehen wir uns das Formular in der Vorschau an, um zu sehen, wie die benutzerdefinierten Funktionen über den Regeleditor implementiert werden:

![Benutzerdefinierte Funktion &quot;Seite berechnen&quot;in der Formularvorschau des Regeleditors](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> Sie können auf Folgendes verweisen: [benutzerdefinierte Funktion](/help/forms/assets//customfunctions.zip) Ordner. Laden Sie diesen Ordner herunter und installieren Sie ihn in Ihrer AEM mithilfe der [Package Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager).


### Festlegen von Dropdown-Listenoptionen mit benutzerdefinierten Funktionen

Regel-Editor in Kernkomponenten unterstützt nicht die **Festlegen von Optionen für** -Eigenschaft zum Festlegen der Dropdown-Listenoptionen zur Laufzeit. Sie können die Optionen der Dropdown-Liste jedoch mit benutzerdefinierten Funktionen festlegen.

Sehen Sie sich den folgenden Code an, um zu sehen, wie wir die Dropdown-Listenoptionen mithilfe benutzerdefinierter Funktionen festlegen können:

```javascript
    /**
    * @name setEnums
    * @returns {string[]}
    **/
    function setEnums() {
    return ["0","1","2","3","4","5","6"];   
    }

    /**
    * @name setEnumNames
    * @returns {string[]}
    **/
    function setEnumNames() {
    return ["Sunday","Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"];
    }
```

Im obigen Code: `setEnums` wird verwendet, um `enum` -Eigenschaft und `setEnumNames` wird verwendet, um `enumNames` -Eigenschaft von Dropdown.

Erstellen wir eine Regel für die `Next` -Schaltfläche, die den Wert der Dropdown-Listenoption festlegt, wenn der Benutzer auf die `Next` Schaltfläche:

![Optionen für Dropdown-Listen](/help/forms/assets/drop-down-list-options.png)

In der folgenden Abbildung sehen Sie, wo die Optionen der Dropdown-Liste beim Klicken auf die Schaltfläche Anzeigen eingestellt sind:

![Dropdown-Optionen im Regeleditor](/help/forms/assets/drop-down-option-rule-editor.png)



### Unterstützung für asynchrone Funktionen in benutzerdefinierten Funktionen {#support-of-async-functions}

Asynchrone benutzerdefinierte Funktionen werden nicht in der Liste des Regeleditors angezeigt. Es ist jedoch möglich, asynchrone Funktionen innerhalb benutzerdefinierter Funktionen aufzurufen, die mit synchronen Funktionsausdrücken erstellt wurden.

![Benutzerdefinierte Funktion &quot;Synchronisieren und asynchron&quot;](/help/forms/assets/workflow-for-sync-async-custom-fumction.png)

>[!NOTE]
>
> Der Vorteil des Aufrufs asynchroner Funktionen in benutzerdefinierten Funktionen besteht darin, dass asynchrone Funktionen die gleichzeitige Ausführung mehrerer Aufgaben ermöglichen, wobei das Ergebnis jeder Funktion in den benutzerdefinierten Funktionen verwendet wird.

Im folgenden Code erfahren Sie, wie Sie asynchrone Funktionen mit benutzerdefinierten Funktionen aufrufen können:

```javascript
    
    async function asyncFunction() {
    const response = await fetch('https://petstore.swagger.io/v2/store/inventory');
    const data = await response.json();
    return data;
    }

    /**
    * callAsyncFunction
    * @name callAsyncFunction callAsyncFunction
    */
    function callAsyncFunction() {
    asyncFunction()
        .then(responseData => {
        console.log('Response data:', responseData);
        })
        .catch(error => {
         console.error('Error:', error);
    });
}
```

Im obigen Beispiel ist die asyncFunction-Funktion ein `asynchronous function`. Er führt einen asynchronen Vorgang durch, indem er eine `GET` Anfrage an `https://petstore.swagger.io/v2/store/inventory`. Es wartet auf die Antwort mit `await`, analysiert den Antworttext mit der `response.json()`und gibt dann die Daten zurück. Die `callAsyncFunction` -Funktion ist eine synchrone benutzerdefinierte Funktion, die die `asyncFunction` und zeigt die Antwortdaten in der Konsole an. Obwohl die Variable `callAsyncFunction` -Funktion synchron ist, ruft sie die asynchrone asyncFunction-Funktion auf und verarbeitet ihr Ergebnis mit `then` und `catch` -Anweisungen.

Um seine Funktionsweise zu sehen, fügen wir eine Schaltfläche hinzu und erstellen eine Regel für die Schaltfläche, die die asynchrone Funktion bei einem Klick auf eine Schaltfläche aufruft.

![Erstellen einer Regel für die asynchrone Funktion](/help/forms/assets/rule-for-async-funct.png)

In der Abbildung unten sehen Sie das Konsolenfenster, um zu veranschaulichen, dass der Benutzer beim Klicken auf die `Fetch` Schaltfläche, die benutzerdefinierte Funktion `callAsyncFunction` aufgerufen wird, was wiederum eine asynchrone Funktion aufruft `asyncFunction`. Inspect Sie das Konsolenfenster, um die Antwort auf die Schaltfläche anzuzeigen. Klicken Sie auf:

![Konsolenfenster](/help/forms/assets/async-custom-funct-console.png)

Im Folgenden werden die Funktionen von benutzerdefinierten Funktionen vorgestellt.

## Verschiedene Funktionen für benutzerdefinierte Funktionen

Sie können benutzerdefinierte Funktionen verwenden, um Formularen personalisierte Funktionen hinzuzufügen. Diese Funktionen unterstützen verschiedene Funktionen, wie z. B. das Arbeiten mit bestimmten Feldern, das Verwenden globaler Felder oder das Zwischenspeichern. Diese Flexibilität ermöglicht es Ihnen, Formulare entsprechend den Anforderungen Ihres Unternehmens anzupassen.

### Felder und globale Perimeter in benutzerdefinierten Funktionen {#support-field-and-global-objects}

Feldobjekte beziehen sich auf die einzelnen Komponenten oder Elemente in einem Formular, z. B. Textfelder und Kontrollkästchen. Das Globals -Objekt enthält schreibgeschützte Variablen wie Formularinstanz, Zielfeldinstanz und Methoden zum Durchführen von Formularänderungen in benutzerdefinierten Funktionen.

>[!NOTE]
>
> Die `param {scope} globals` muss der letzte Parameter sein und wird nicht im Regeleditor eines adaptiven Formulars angezeigt.

<!-- Let us look at the following code snippet:

```JavaScript
   
    /**
    * updateDateTime
    * @name updateDateTime
    * @param {object} field
    * @param {scope} globals
    */
    function updateDateTime(field, globals) {
    // Accessing the Date object from the global scope
    var currentDate = new Date();
    // Formatting the date and time
    var formattedDateTime = currentDate.toLocaleString();
    // Updating the field value with the formatted date and time using setProperty.
    globals.functions.setProperty(field, {value: formattedDateTime});
    }
```

In the above code snippet, a custom function named `updateDateTime` takes parameters such as a field object and a global object. The field represents the textbox object where the formatted date and time value is displayed within the form. -->

Erfahren Sie, wie benutzerdefinierte Funktionen mithilfe eines `Contact Us` Formular mit verschiedenen Anwendungsfällen verwenden.

![Kontaktformular](/help/forms/assets/contact-us-form.png)

+++ **Anwendungsfall**: Zeigen Sie ein Bedienfeld mit dem `SetProperty` Regel

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) Abschnitt, um das Formularfeld als `Required`.

```javascript
    
    /**
    * enablePanel
    * @name enablePanel
    * @param {object} field1
    * @param {object} field2
    * @param {scope} globals 
    */

    function enablePanel(field1,field2, globals)
    {
       if(globals.functions.validate(field1).length === 0)
       {
       globals.functions.setProperty(field2, {visible: true});
       }
    }
```

>[!NOTE]
>
> * Sie können die Feldeigenschaften mit den verfügbaren Eigenschaften konfigurieren, die sich unter `[form-path]/jcr:content/guideContainer.model.json`.
> * Änderungen am Formular, die mithilfe des `setProperty` -Methode des Globals-Objekts sind asynchron und werden bei der Ausführung der benutzerdefinierten Funktion nicht berücksichtigt.

In diesem Beispiel wird die `personaldetails` angezeigt, wenn auf die Schaltfläche geklickt wird. Wenn im Bedienfeld keine Fehler erkannt werden, wird in einem anderen Bedienfeld die `feedback` -Bedienfeld angezeigt, wird beim Klicken auf die Schaltfläche sichtbar.

Erstellen wir eine Regel für die `Next` -Schaltfläche, mit der die `personaldetails` und erstellt die `feedback`  Bereich, der angezeigt wird, wenn der Benutzer auf die `Next` Schaltfläche.

![Eigenschaft festlegen](/help/forms/assets/custom-function-set-property.png)

In der folgenden Abbildung erfahren Sie, wo die Variable `personaldetails` beim Klicken auf `Next` Schaltfläche. Für alle Felder im `personaldetails` validiert werden, wird die `feedback` -Bedienfeld wird angezeigt.

![Festlegen der Eigenschaftenformularvorschau](/help/forms/assets/set-property-form-preview.png)

Wenn Fehler in den Feldern der Variablen `personaldetails` angezeigt werden, werden sie beim Klicken auf die `Next` und der `feedback` bleibt unsichtbar.

![Festlegen der Eigenschaftenformularvorschau](/help/forms/assets/set-property-panel.png)

+++

+++ **Anwendungsfall**: Validieren Sie das Feld.

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) , um das Feld zu validieren.

```javascript
    /**
    * validateField
    * @name validateField
    * @param {object} field
    * @param {scope} globals
    */
    function validateField(field,globals)
    {
    
        globals.functions.validate(field);
    
    }   
```

>[!NOTE]
>
> Wenn kein -Argument übergeben wird, wird die `validate()` -Funktion, validiert sie das Formular.

In diesem Beispiel wird ein benutzerdefiniertes Überprüfungsmuster auf die `contact` -Feld. Benutzer müssen eine Telefonnummer eingeben, die mit `10` gefolgt von `8` Ziffern. Wenn der Benutzer eine Telefonnummer eingibt, die nicht mit `10` oder enthält mehr oder weniger als `8` Ziffern angeben, wird beim Klicken auf die Schaltfläche eine Validierungsfehlermeldung angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/custom-function-validation-pattern.png)

Der nächste Schritt besteht darin, eine Regel für die `Next` -Schaltfläche, die die `contact` auf der Schaltfläche klicken.

![Überprüfungsmuster](/help/forms/assets/custom-function-validate.png)

Beachten Sie die folgende Abbildung, um zu zeigen, dass wenn der Benutzer eine Telefonnummer eingibt, die nicht mit `10`wird auf Feldebene eine Fehlermeldung angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/custom-function-validate-error-message.png)

Wenn der Benutzer eine gültige Telefonnummer und alle Felder in der `personaldetails` validiert werden, wird die `feedback` wird auf dem Bildschirm angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/validate-form-preview-form.png)

+++

+++ **Anwendungsfall**: Zurücksetzen eines Bedienfelds

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) -Abschnitt, um das Bedienfeld zurückzusetzen.

```javascript
    /**
    * resetField
    * @name  resetField
    * @param {string} input1
    * @param {object} field
    * @param {scope} globals 
    */
    function  resetField(field,globals)
    {
    
        globals.functions.reset(field);
    
    }
```

>[!NOTE]
>
> Wenn kein -Argument übergeben wird, wird die `reset()` -Funktion, validiert sie das Formular.

In diesem Beispiel wird die `personaldetails` beim Klicken auf `Clear` Schaltfläche. Der nächste Schritt besteht darin, eine Regel für die `Clear` -Schaltfläche, mit der das Bedienfeld auf die Schaltfläche zurückgesetzt wird.

![Schaltfläche Löschen](/help/forms/assets/custom-function-reset-field.png)

Die folgende Abbildung zeigt, dass der Benutzer durch Klicken auf die `clear` -Schaltfläche, `personaldetails` Bedienfeld zurückgesetzt:

![Formular zurücksetzen](/help/forms/assets/custom-function-reset-form.png)

+++

+++ **Anwendungsfall**: So zeigen Sie eine benutzerdefinierte Nachricht auf Feldebene an und kennzeichnen das Feld als ungültig

Sie können die `markFieldAsInvalid()` -Funktion, um ein Feld als ungültig zu definieren und eine benutzerdefinierte Fehlermeldung auf Feldebene festzulegen. Die `fieldIdentifier` Wert kann `fieldId`oder `field qualifiedName`oder `field dataRef`. Der Wert des Objekts mit dem Namen `option` kann `{useId: true}`, `{useQualifiedName: true}`oder `{useDataRef: true}`.
Die Syntax, mit der ein Feld als ungültig markiert und eine benutzerdefinierte Nachricht festgelegt wird, lautet:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) , um eine benutzerdefinierte Nachricht auf Feldebene zu aktivieren.

```javascript
    /**
    * customMessage
    * @name customMessage
    * @param {object} field
    * @param {scope} globals 
    */
    function customMessage(field, globals) {
    const minLength = 15;
    const comments = field.$value.trim();
    if (comments.length < minLength) {
        globals.functions.markFieldAsInvalid(field.$id, "Comments must be at least 15 characters long.", { useId: true });
    }
}
```

In diesem Beispiel wird eine benutzerdefinierte Meldung auf Feldebene angezeigt, wenn der Benutzer weniger als 15 Zeichen in das Textfeld &quot;Kommentare&quot;eingibt.

Der nächste Schritt besteht darin, eine Regel für die `comments` -Feld:

![Feld als ungültig markieren](/help/forms/assets/custom-function-invalid-field.png)

Sehen Sie sich die unten stehende Demonstration an, um anzuzeigen, dass negative Rückmeldungen im `comments` -Feld wird die Anzeige einer benutzerdefinierten Nachricht auf Feldebene Trigger:

![Feld als ungültiges Vorschauformular markieren](/help/forms/assets/custom-function-invalidfield-form.png)

Wenn der Benutzer mehr als 15 Zeichen in das Textfeld &quot;Kommentare&quot;eingibt, wird das Feld validiert und das Formular wird gesendet:

![Feld als gültiges Vorschauformular markieren](/help/forms/assets/custom-function-validfield-form.png)

+++

+++ **Anwendungsfall**: Sendet geänderte Daten an den Server

Die folgende Codezeile:
`globals.functions.submitForm(globals.functions.exportData(), false);` wird verwendet, um die Formulardaten nach der Bearbeitung zu senden.
* Das erste Argument sind die zu übermittelnden Daten.
* Das zweite Argument stellt dar, ob das Formular vor der Übermittlung validiert werden soll. Es ist `optional` und legen Sie `true` Standardmäßig.
* Das dritte Argument ist die `contentType` der Übermittlung, die ebenfalls optional ist, wobei der Standardwert als `multipart/form-data`. Die anderen Werte können `application/json` und `application/x-www-form-urlencoded`.

Fügen Sie den folgenden Code in die benutzerdefinierte Funktion ein, wie im Abschnitt [create-custom-function](#create-custom-function) , um die bearbeiteten Daten auf dem Server zu senden:

```javascript
    /**
    * submitData
    * @name submitData
    * @param {object} field
    * @param {scope} globals 
    */
    function submitData(globals)
    {
    
    var data = globals.functions.exportData();
    if(!data.comments) {
    data.comments = 'NA';
    }
    console.log('After update:{}',data);
    globals.functions.submitForm(data, false);
    }
```

Wenn der Benutzer in diesem Beispiel die `comments` Textfeld leer, das `NA` wird beim Senden des Formulars an den Server gesendet.

Erstellen Sie nun eine Regel für die `Submit` -Schaltfläche, über die Daten gesendet werden:

![Daten senden](/help/forms/assets/custom-function-submit-data.png)

Siehe Abbildung der `console window` unten, um zu zeigen, dass wenn der Benutzer die `comments` Textfeld leer, dann der Wert als `NA` wird auf dem Server gesendet:

![Daten im Konsolenfenster senden](/help/forms/assets/custom-function-submit-data-form.png)

Sie können auch das Konsolenfenster überprüfen, um die an den Server gesendeten Daten anzuzeigen:

![Inspect-Daten im Konsolenfenster](/help/forms/assets/custom-function-submit-data-console-data.png)

+++

+++ **Anwendungsfall**: Überschreiben des Erfolgs der Formularübermittlung und der Fehler-Handler

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) , um die Übermittlung oder Fehlermeldung für Formularübermittlungen anzupassen und die Formularübermittlungsmeldungen in einem modalen Feld anzuzeigen:

```javascript
/**
 * Handles the success response after a form submission.
 *
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitSuccessHandler(globals) {
    var event = globals.event;
    var submitSuccessResponse = event.payload.body;
    var form = globals.form;

    if (submitSuccessResponse) {
        if (submitSuccessResponse.redirectUrl) {
            window.location.href = encodeURI(submitSuccessResponse.redirectUrl);
        } else if (submitSuccessResponse.thankYouMessage) {
            showModal("success", submitSuccessResponse.thankYouMessage);
        }
    }
}

/**
 * Handles the error response after a form submission.
 *
 * @param {string} customSubmitErrorMessage - The custom error message.
 * @param {scope} globals - This object contains a read-only form instance, target field instance, triggered event, and methods for performing form modifications within custom functions.
 * @returns {void}
 */
function customSubmitErrorHandler(customSubmitErrorMessage, globals) {
    showModal("error", customSubmitErrorMessage);
}
function showModal(type, message) {
    // Remove any existing modals
    var existingModal = document.getElementById("modal");
    if (existingModal) {
        existingModal.remove();
    }

    // Create the modal dialog
    var modal = document.createElement("div");
    modal.setAttribute("id", "modal");
    modal.setAttribute("class", "modal");

    // Create the modal content
    var modalContent = document.createElement("div");
    modalContent.setAttribute("class", "modal-content");

    // Create the modal header
    var modalHeader = document.createElement("div");
    modalHeader.setAttribute("class", "modal-header");
    modalHeader.innerHTML = "<h2>" + (type === "success" ? "Thank You" : "Error") + "</h2>";

    // Create the modal body
    var modalBody = document.createElement("div");
    modalBody.setAttribute("class", "modal-body");
    modalBody.innerHTML = "<p class='" + type + "-message'>" + message + "</p>";

    // Create the modal footer
    var modalFooter = document.createElement("div");
    modalFooter.setAttribute("class", "modal-footer");

    // Create the close button
    var closeButton = document.createElement("button");
    closeButton.setAttribute("class", "close-button");
    closeButton.innerHTML = "Close";
    closeButton.onclick = function() {
        modal.remove();
    };

    // Append the elements to the modal content
    modalFooter.appendChild(closeButton);
    modalContent.appendChild(modalHeader);
    modalContent.appendChild(modalBody);
    modalContent.appendChild(modalFooter);

    // Append the modal content to the modal
    modal.appendChild(modalContent);

    // Append the modal to the document body
    document.body.appendChild(modal);
}
```

In diesem Beispiel verwendet der Benutzer die Variable `customSubmitSuccessHandler` und `customSubmitErrorHandler` benutzerdefinierte Funktionen, werden die Erfolgs- und Fehlermeldungen in einem Modal angezeigt. Die JavaScript-Funktion `showModal(type, message)` wird verwendet, um dynamisch ein modales Dialogfeld auf einem Bildschirm zu erstellen und anzuzeigen.

Erstellen Sie nun eine Regel für die erfolgreiche Formularübermittlung:

![Formularübermittlung erfolgreich](/help/forms/assets/form-submission-success.png)

In der unten stehenden Abbildung sehen Sie, wie die Erfolgsmeldung bei erfolgreicher Übermittlung des Formulars in einem Modal dargestellt wird:

![Erfolgsmeldung zur Formularübermittlung](/help/forms/assets/form-submission-success-message.png)

Erstellen Sie eine Regel für fehlgeschlagene Formularübermittlungen:

![Formularübermittlung schlägt fehl](/help/forms/assets/form-submission-fail.png)

In der folgenden Abbildung sehen Sie, dass die Fehlermeldung in einem Modal angezeigt wird, wenn die Formularübermittlung fehlschlägt:

![Fehlermeldung bei Formularübermittlung](/help/forms/assets/form-submission-fail-message.png)

Um den Erfolg und das Fehlschlagen der Formularübermittlung standardmäßig anzuzeigen, muss die `Default submit Form Success Handler` und `Default submit Form Error Handler` -Funktionen sind standardmäßig verfügbar.

Falls der benutzerdefinierte Übermittlungs-Handler nicht wie erwartet in vorhandenen AEM Projekten oder Formularen ausgeführt werden kann, lesen Sie den Abschnitt [Fehlerbehebung](#troubleshooting) Abschnitt.

<!--

+++

+++ **Use Case**:  Perform actions in a specific instance of the repeatable panel 

Rules created using the visual rule editor on a repeatable panel apply to the last instance of the repeatable panel. To write a rule for a specific instance of the repeatable panel, we can use a custom function.

Let's create a form to collect information about travelers heading to a destination. A traveler panel is added as a repeatable panel, where the user can add details for 5 travelers using the Add button.

Add the following line of code as explained in the [create-custom-function](#create-custom-function) section, to perform actions in a specific instance of the repeatable panel, other than the last one:

```javascript

/**
* @name hidePanelInRepeatablePanel
* @param {scope} globals
*/
function hidePanelInRepeatablePanel(globals)
{    
    var repeatablePanel = globals.form.travelerinfo;
    // hides a panel inside second instance of repeatable panel
    globals.functions.setProperty(repeatablePanel[1].traveler, {visible : false});
}  

```
 
In this example, the `hidePanelInRepeatablePanel` custom function performs action in a specific instance of the repeatable panel. In the above code, `travelerinfo` represents the repeatable panel. The `repeatablePanel[1].traveler, {visible: false}` code hides the panel in the second instance of the repeatable panel. 
Let us add a button labeled `Hide` to add a rule to hide a specific panel.

![Hide Panel rule](/help/forms/assets/custom-function-hidepanel-rule.png)

Refer to the video below to demonstrate that when the `Hide` is clicked, the panel in the second repeatable instance hides:


+++

+++ **Usecase**: Pre-fill the field with a value when the form loads

Add the following line of code, as explained in the [create-custom-function](#create-custom-function) section, to load the pre-filled value in a field when the form is initialized:

```javascript
/**
 * @name importData
 * @param {scope} globals
 */
function importData(globals)
{
    globals.functions.importData(Object.fromEntries([['amount',200000]]));
} 
```

In the aforementioned code, the `importData` function updates the value in the `amount` textbox field when the form loads.

Let us create a rule for the `Submit` button, where the value in the `amount` textbox field changes to specified value when the form loads:

![Import Data Rule](/help/forms/assets/custom-function-import-data.png)

Refer to the screenshot below, which demonstrates that when the form loads, the value in the amount textbox is pre-filled with a specified value:

![Import Data Rule](/help/forms/assets/cg)

+++

+++ **Usecase**: Set focus on the specific field

Add the following line of code, as explained in the [create-custom-function](#create-custom-function) section, to set focus on the specified field when the `Submit` button is clicked.:

```javascript
/**
 * @name setFocus
 * @param {object} field
 * @param {scope} globals
 */
function setFocus(field, globals)
{
    globals.functions.setFocus(field);
}
```

Let us add a rule to the `Submit` button to set focus on the `email` field when it is clicked:

![Set Focus Rule](/help/forms/assets/custom-function-set-focus.png)

Refer to the screenshot below, which demonstrates that when the `Submit` button is clicked, the focus is set on the `email` field:

![Set Focus Rule](/help/forms/assets/custom-function-set-focus-form.png)

>[!NOTE]
>
> You can use the optional `$focusOption` parameter, if you want to focus on the next or previous field relative to the `email` field.

+++

+++ **Usecase**: Add or delete repeatable panel using the `dispatchEvent` property

Add the following line of code, as explained in the [create-custom-function](#create-custom-function) section, to add a panel when the `Add Traveler` button is clicked using the `dispatchEvent` property:

```javascript
/**
 
 * @name addInstance
 * @param {scope} globals
 */
function addInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel, 'addInstance');
} 

```

Let us add a rule to the `Add Traveler` button to add the repeatable panel when it is clicked:

![Add Panel Rule](/help/forms/assets/custom-function-add-panel.png)

Refer to the screenshot below, which demonstrates that when the `Add Traveler` button is clicked, the traveler panel is added using the `dispatchEvent` property:

![Add Panel](/help/forms/assets/customg)

Similarly, add a button labeled `Delete Traveler` to delete a panel. Add the following line of code, as explained in the [create-custom-function](#create-custom-function) section, to delete a panel when the `Delete Traveler` button is clicked using the `dispatchEvent` property:

```javascript

/**
 
 * @name removeInstance
 * @param {scope} globals
 */
function removeInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel, 'removeInstance');
} 

```
Let us add a rule to the `Delete Traveler` button to delete the repeatable panel when it is clicked:

![Delete Panel Rule](/help/forms/assets/custom-function-delete-panel.png)

Refer to the screenshot below, which demonstrates that when the `Delete Traveler` button is clicked, the traveler panel is deleted using the `dispatchEvent` property:

![Delete Panel](/help/forms/assets/customg)
-->

## Caching-Unterstützung für benutzerdefinierte Funktionen

Adaptive Forms implementiert Caching für benutzerdefinierte Funktionen, um die Reaktionszeit beim Abrufen der benutzerdefinierten Funktionsliste im Regeleditor zu verkürzen. Eine Nachricht als `Fetched following custom functions list from cache` im `error.log` -Datei.

![benutzerdefinierte Funktion mit Cache-Unterstützung](/help/forms/assets/custom-function-cache-error.png)

Wenn die benutzerdefinierten Funktionen geändert werden, wird die Zwischenspeicherung invalidiert und analysiert.

## Fehlerbehebung {#troubleshooting}

* Wenn der benutzerdefinierte Übermittlungshandler nicht wie erwartet in bestehenden AEM Projekten oder Formularen ausgeführt werden kann, führen Sie die folgenden Schritte aus:
   * Stellen Sie sicher, dass [Version der Kernkomponenten wird auf Version 3.0.18 und höher aktualisiert.](https://github.com/adobe/aem-core-forms-components). Für bestehende AEM Projekte und Formulare sind jedoch weitere Schritte erforderlich:

   * Für das AEM Projekt sollte der Benutzer alle Instanzen von `submitForm('custom:submitSuccess', 'custom:submitError')` mit `submitForm()` und stellen das Projekt über die Cloud Manager-Pipeline bereit.

   * Wenn die benutzerdefinierten Übermittlungs-Handler für vorhandene Formulare nicht ordnungsgemäß funktionieren, muss der Benutzer die `submitForm` -Regel auf **Einsenden** -Schaltfläche mit dem Regeleditor. Diese Aktion ersetzt die vorhandene Regel aus `submitForm('custom:submitSuccess', 'custom:submitError')` mit `submitForm()` im Formular.


* Wenn die JavaScript-Datei mit dem Code für benutzerdefinierte Funktionen einen Fehler enthält, werden die benutzerdefinierten Funktionen nicht im Regeleditor eines adaptiven Formulars aufgeführt. Um die Liste der benutzerdefinierten Funktionen zu überprüfen, können Sie zum `error.log` -Datei für den Fehler. Im Fall eines Fehlers wird die Liste der benutzerdefinierten Funktionen leer angezeigt:

  ![Fehlerprotokolldatei](/help/forms/assets/custom-function-list-error-file.png)

  Wenn kein Fehler auftritt, wird die benutzerdefinierte Funktion abgerufen und im `error.log` -Datei. Eine Nachricht als `Fetched following custom functions list` im `error.log` Datei:

  ![Fehlerprotokolldatei mit entsprechender benutzerdefinierter Funktion](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Überlegungen

* Die `parameter type` und `return type` nicht unterstützen `None`.

* Folgende Funktionen werden in der benutzerdefinierten Funktionsliste nicht unterstützt:
   * Generator-Funktionen
   * Async/Await-Funktionen
   * Methodendefinitionen
   * Klassenmethoden
   * Standardparameter
   * REST-Parameter

## Siehe auch {#see-also}

{{see-also}}


