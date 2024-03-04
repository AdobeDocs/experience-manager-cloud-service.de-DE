---
title: Erstellen und Hinzufügen benutzerdefinierter Funktionen in einem adaptiven Formular
description: AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer eigene Funktionen im Regeleditor erstellen und verwenden können.
keywords: Fügen Sie eine benutzerdefinierte Funktion hinzu, verwenden Sie eine benutzerdefinierte Funktion, erstellen Sie eine benutzerdefinierte Funktion, verwenden Sie eine benutzerdefinierte Funktion im Regeleditor.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
source-git-commit: 46fbed98a806f62dd1882eb0085d4338c5cd51a7
workflow-type: tm+mt
source-wordcount: '1108'
ht-degree: 26%

---


# Benutzerdefinierte Funktionen in Adaptive Forms (Kernkomponenten)

## Einführung

AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer JavaScript-Funktionen zur Implementierung komplexer Geschäftsregeln definieren können. Diese benutzerdefinierten Funktionen erweitern die Funktionen von Formularen, indem sie die Manipulation und Verarbeitung der eingegebenen Daten zur Erfüllung bestimmter Anforderungen erleichtern. Sie ermöglichen auch eine dynamische Änderung des Formularverhaltens basierend auf vordefinierten Kriterien.
In Adaptive Forms können Sie benutzerdefinierte Funktionen innerhalb der [Regeleditor eines adaptiven Formulars](/help/forms/rule-editor-core-components.md) , um spezifische Validierungsregeln für Formularfelder zu erstellen.

Im Folgenden wird die Verwendung einer benutzerdefinierten Funktion beschrieben, in der Benutzer die E-Mail-Adresse eingeben und sichergestellt werden soll, dass die eingegebene E-Mail-Adresse ein bestimmtes Format aufweist (sie enthält ein &quot;@&quot;-Symbol und einen Domänennamen). Erstellen Sie eine benutzerdefinierte Funktion als &quot;ValidateEmail&quot;, die die E-Mail-Adresse als Eingabe verwendet und &quot;true&quot; zurückgibt, wenn sie gültig ist, andernfalls &quot;false&quot;.

```javascript
function ValidateEmail(inputText)
{
    var email = /^\w+([\.-]?\w+)*@\w+([\.-]?\w+)*(\.\w{2,3})+$/;
    if(inputText.value.match(email))
        {
            alert("Valid email address!");
            return true;
        }
    else
    {
        alert("Invalid email address!");
        return false;
    }
}
```

Im obigen Beispiel wird, wenn der Benutzer versucht, das Formular zu senden, die benutzerdefinierte Funktion &quot;ValidateEmail&quot;aufgerufen, um zu überprüfen, ob die eingegebene E-Mail-Adresse gültig ist.

### Verwendung benutzerdefinierter Funktionen {#uses-of-custom-function}

Die Verwendung benutzerdefinierter Funktionen in Adaptive Forms bietet folgende Vorteile:

* **Datenverarbeitung**: Benutzerdefinierte Funktionen bearbeiten und verarbeiten Daten, die in die Formularfelder eingegeben werden.
* **Datenvalidierung**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, benutzerdefinierte Prüfungen von Formulareingaben durchzuführen und bestimmte Fehlermeldungen bereitzustellen.
* **Dynamisches Verhalten**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, das dynamische Verhalten Ihrer Formulare anhand bestimmter Bedingungen zu steuern. Beispielsweise können Sie Felder ein-/ausblenden, Feldwerte ändern oder die Formularlogik dynamisch anpassen.
* **Integration**: Sie können benutzerdefinierte Funktionen zur Integration mit externen APIs oder Diensten verwenden. Dies hilft beim Abrufen von Daten aus externen Quellen, beim Senden von Daten an externe REST-Endpunkte oder beim Ausführen benutzerdefinierter Aktionen basierend auf externen Ereignissen.

## Unterstützte JS-Anmerkungen

Stellen Sie sicher, dass die benutzerdefinierte Funktion, die Sie schreiben, von der `jsdoc` darüber.

Unterstützte `jsdoc`-Tags:

* **Private** (Privat)
Syntax: `@private`  
Eine Private-Funktion ist nicht als benutzerdefinierte Funktion enthalten.

* **Name**
Syntax: `@name funcName <Function Name>`
Alternativ dazu ist es möglich`,``@function funcName <Function Name>` **oder** `@func` `funcName <Function Name>` zu verwenden.
  `funcName` ist der Name der Funktion (Leerzeichen sind nicht zulässig).
  `<Function Name>` ist der Anzeigename der Funktion.

* **Parameter**
Syntax: `@param {type} name <Parameter Description>`
Alternativ dazu ist es möglich, `@argument` `{type} name <Parameter Description>` **oder** `@arg` `{type}` `name <Parameter Description>` zu verwenden.
Zeigt die von der Funktion verwendeten Parameter an. In einer Funktion können mehrere Parameter-Tags vorhanden sein (je ein Tag für jeden Parameter in der Reihenfolge ihres Auftretens).
  `{type}` gibt den Parametertyp an. Zulässige Parametertypen sind:

   1. String (Zeichenfolge)
   2. Number (Zahl)
   3. Boolean (Boolesch)
   4. Scope (Umfang)
   5. Zeichenfolge[]
   6. number[]
   7. boolean[]
   8. Datum
   9. date[]
   10. Array
   11. Objekt

  `scope` bezieht sich auf ein spezielles globales Objekt, das von der Forms-Laufzeit bereitgestellt wird. Es muss der letzte Parameter sein und ist für den Benutzer im Regeleditor nicht sichtbar. Sie können den Bereich verwenden, um auf lesbare Formular- und Feld-Proxy-Objekte zuzugreifen, um Eigenschaften zu lesen, Ereignisse, die die Regel ausgelöst haben, und eine Reihe von Funktionen zur Bearbeitung des Formulars.

  `object` type wird verwendet, um ein lesbares Feldobjekt im Parameter an eine benutzerdefinierte Funktion zu übergeben, anstatt den Wert weiterzugeben.

  Alle Parametertypen fallen in eine der oben genannten Kategorien. „None“ (Keiner) wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei den Typen wird nicht zwischen Groß- und Kleinschreibung unterschieden. Leerzeichen sind im Parameternamen nicht zulässig.  Parameterbeschreibung kann mehrere Wörter enthalten.

* **Optionaler Parameter**
Syntax: `@param {type=} name <Parameter Description>`
Alternativ können Sie Folgendes verwenden: `@param {type} [name] <Parameter Description>`
Standardmäßig sind alle Parameter obligatorisch. Sie können einen Parameter optional markieren, indem Sie `=` in den Parametertyp ein oder den Parameternamen in eckige Klammern setzen.
Deklarieren Sie beispielsweise `Input1` als optionaler Parameter:
   * `@param {type=} Input1`
   * `@param {type} [Input1]`

* **Return Type** (Rückgabetyp)
Syntax: `@return {type}`
Alternativ ist es möglich, `@returns {type}` zu verwenden.
Fügt Informationen über die Funktion hinzu (z. B. ihren Zweck).
Die Zeichenfolge „{type}“ gibt den Rückgabetyp der Funktion an. Zulässige Rückgabetypen sind:

   1. String (Zeichenfolge)
   2. Number (Zahl)
   3. Boolean (Boolesch)
   4. Zeichenfolge[]
   5. number[]
   6. boolean[]
   7. Datum
   8. date[]
   9. Array
   10. Objekt

Alle anderen Rückgabetypen fallen in eine der oben genannten Kategorien. Keine Angabe wird nicht unterstützt. Achten Sie darauf, einen der oben genannten Typen zu wählen. Bei Rückgabetypen wird nicht zwischen Groß- und Kleinschreibung unterschieden.

## Überlegungen beim Erstellen benutzerdefinierter Funktionen {#considerations}

Um die benutzerdefinierten Funktionen im Regeleditor aufzulisten, können Sie sie in einem der folgenden Formate deklarieren:

* **Funktionsanweisung mit oder ohne jsdoc-Kommentare**

Sie können eine benutzerdefinierte Funktion mit oder ohne jsdoc-Kommentare erstellen.

```javascript
    function functionName(parameters) 
        {
            // code to be executed
        }
```
<!--

* **Arrow function with mandatory jsdoc comment**

Some of the examples to create Arrow functions are:
```javascript
    /**
    * test function
    * @name testFunction test function
    * @param {string} a some parameter description
    * @param {string} b another parameter description
    * @return {string}
    */
    testFunction = (a, b) => {
    return a + b;
    };
```

    * @param {string=} b another parameter description
      /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;-->

* **Funktionsausdruck mit obligatorischem jsdoc-Kommentar**

Um benutzerdefinierte Funktionen im Regeleditor eines adaptiven Formulars aufzulisten, erstellen Sie benutzerdefinierte Funktionen im folgenden Format:

```javascript
    /**
    * test function
    * @name testFunction test function
    * @param {string} input1 parameter description
    * @param {string} input2 another parameter description
    * @return {string}
    */
    testFunction = function(input1,input2)
        {
            // code to be executed
        }
```

<!--
* @param {string=} input2 another parameter description
The functions that are not supported in the custom function list are:
* Generator functions
* Async/Await functions 
* Method definitions
* Class methods
* Default parameters
* Rest parameters -->

>[!NOTE]
>
> Sie können die `error.log` -Datei für Fehler, z. B. für benutzerdefinierte Funktionen, die nicht im Regeleditor aufgelistet werden.

<!--The `error.log` file also displays the methods and parameters that are not supported for custom functions. -->


## Benutzerdefinierte Funktion erstellen {#create-custom-function}

Erstellen Sie eine Client-Bibliothek, um benutzerdefinierte Funktionen im Regeleditor aufzurufen. Weitere Informationen finden Sie unter [Verwenden Client-seitiger Bibliotheken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=de#developing).

Schritte zum Erstellen benutzerdefinierter Funktionen:
1. [Erstellen einer Client-Bibliothek](#create-client-library)
1. [Clientbibliothek in einem adaptiven Formular hinzufügen](#use-custom-function)

### Erstellen einer Client-Bibliothek {#create-client-library}

Sie können benutzerdefinierte Funktionen hinzufügen, indem Sie die Client-Bibliothek hinzufügen. Um eine Client-Bibliothek zu erstellen, führen Sie die folgenden Schritte aus:

1. [Klonen Sie Ihr AEM Forms as a Cloud Service-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).
1. Erstellen Sie einen Ordner unter dem Ordner `[AEM Forms as a Cloud Service repository folder]/apps/`. Erstellen Sie beispielsweise einen Ordner mit dem Namen `experience-league`.
1. Navigieren Sie zu `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` und erstellen Sie eine `ClientLibraryFolder`. Erstellen Sie beispielsweise einen Client-Bibliotheksordner als `customclientlibs`.
1. Hinzufügen einer Eigenschaft `categories` mit einem Zeichenfolgentyp -Wert. Weisen Sie beispielsweise den Wert zu `customfunctionscategory` der `categories` -Eigenschaft für `customclientlibs` Ordner.

   >[!NOTE]
   >
   > Sie können einen beliebigen Namen für `client library folder` und `categories` -Eigenschaft.

1. Erstellen Sie einen Ordner mit dem Namen `js`.
1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/customclientlibs/js`.
1. Fügen Sie eine JavaScript-Datei hinzu, beispielsweise `function.js`. Die Datei enthält den Code für die benutzerdefinierte Funktion.

   >[!NOTE]
   >
   > Wenn die JavaScript-Datei mit dem Code für benutzerdefinierte Funktionen einen Fehler enthält, werden die benutzerdefinierten Funktionen nicht im Regeleditor eines adaptiven Formulars aufgeführt. Sie können auch die `error.log` -Datei für den Fehler.

   <!-- 
    >* AEM Adaptive Form supports the caching of custom functions. If the JavaScript is modified, the caching becomes invalidated, and it is parsed. You can see a message as `Fetched following custom functions list from cache` in the `error.log` file.  -->

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

1. [Ausführen der Pipeline.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline)

Sobald die Pipeline erfolgreich ausgeführt wurde, wird die in der Client-Bibliothek hinzugefügte benutzerdefinierte Funktion in Ihrer [Regeleditor für adaptive Formulare](/help/forms/rule-editor-core-components.md).

### Clientbibliothek in einem adaptiven Formular hinzufügen{#use-custom-function}

Nachdem Sie Ihre Client-Bibliothek in Ihrer Forms CS-Umgebung bereitgestellt haben, verwenden Sie die zugehörigen Funktionen in Ihrem adaptiven Formular. Hinzufügen der Client-Bibliothek zum adaptiven Formular

1. Öffnen Sie das Formular im Bearbeitungsmodus. Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und wählen Sie **[!UICONTROL Bearbeiten]**.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Allgemein]** und wählen Sie den Namen der **[!UICONTROL Client-Bibliothekskategorie]** aus der Dropdown-Liste aus (in diesem Fall wählen Sie `customfunctionscategory`).

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/assets/clientlib-custom-function.png)

1. Klicks **[!UICONTROL Fertig]** .

Jetzt können Sie eine Regel erstellen, um benutzerdefinierte Funktionen im Regeleditor zu verwenden.

<!--

Create a rule to use custom function in the rule editor. 

### Support for the optional parameters in custom functions{#support-for-optional-parameter}

AEM supports including optional parameters in JSDocs. These parameters are displayed as optional in the rule editor. There are two ways to add optional parameters in JSDocs:
*  `@param {string=abc} b -- some description for b which is optional`

    In the above line of code, `b` is an optional parameter with the default value set to `abc`. 
    Alternatively, you can define `b` as an optional parameter without assigning any default value as `@param {string=} b -- some description for b which is optional`

* `@param {array} [z=[def,xyz]] - - some description for z which is optional`

    In the above line of code, `z` is an optional parameter of array type with the default value set to `[def , xyz]`. 
    Alternatively, you can define `z` as an optional parameter without assigning any default value as `@param {array} [z=] - - some description for z which is optional`

>[!NOTE]
>
> Ensure that the parameter name is enclosed in square brackets [] and the parameter type is enclosed in curly brackets {}. 

To learn more about how to define optional parameters in JSDocs, [click here](https://jsdoc.app/tags-param).

In the rule editor of an Adaptive Form, the parameters are displayed as `required`. By default the parameters are `required`, if not defined as optional in JSDocs.

  ![Optional or required parameters](/help/forms/assets/optional-default-params.png) 

  You can save the rule without specifying a value for required parameters, but the rule is not executed and displays a warning message as:

  ![incomplete rule warning message](/help/forms/assets/incomplete-rule.png) 
  
  The rule is executed even if you do not specify a value for optional parameters. Undefined values are passed for optional parameters on executing the rule.

  ### Support for field and globals objects in custom functions {#support-field-and-global-objects}

  needs to be discussed

  -->

## Siehe auch {#see-also}

{{see-also}}





