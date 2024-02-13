---
title: Erstellen und Hinzufügen benutzerdefinierter Funktionen in einem adaptiven Formular
description: AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer eigene Funktionen im Regeleditor erstellen und verwenden können.
keywords: Fügen Sie eine benutzerdefinierte Funktion hinzu, verwenden Sie eine benutzerdefinierte Funktion, erstellen Sie eine benutzerdefinierte Funktion, verwenden Sie eine benutzerdefinierte Funktion im Regeleditor.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
source-git-commit: 94a290964a92f8c6ed353d9c77f3dd3b8a5598a4
workflow-type: tm+mt
source-wordcount: '778'
ht-degree: 17%

---


# Benutzerdefinierte Funktionen in Adaptive Forms (Kernkomponenten)

## Einführung

AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer JavaScript-Funktionen zur Implementierung komplexer Geschäftsregeln definieren können. Diese benutzerdefinierten Funktionen erweitern die Funktionen von Formularen, indem sie die Manipulation und Verarbeitung der eingegebenen Daten zur Erfüllung bestimmter Anforderungen erleichtern. Sie ermöglichen auch eine dynamische Änderung des Formularverhaltens basierend auf vordefinierten Kriterien.
In Adaptive Forms können Sie benutzerdefinierte Funktionen innerhalb der [Regeleditor eines adaptiven Formulars](/help/forms/rule-editor.md#custom-functions) , um spezifische Validierungsregeln für Formularfelder zu erstellen.

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

Die Verwendung benutzerdefinierter Funktionen in Adaptive Forms bietet unter anderem folgende Vorteile:

* **Datenverarbeitung**: Benutzerdefinierte Funktionen bearbeiten und verarbeiten die in die Formularfelder eingegebenen Daten.
* **Datenvalidierung**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, benutzerdefinierte Prüfungen von Formulareingaben durchzuführen und bestimmte Fehlermeldungen bereitzustellen.
* **Dynamisches Verhalten**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, das dynamische Verhalten Ihrer Formulare anhand bestimmter Bedingungen zu steuern. Beispielsweise können Sie Felder ein-/ausblenden, Feldwerte ändern oder die Formularlogik dynamisch anpassen.
* **Integration**: Sie können benutzerdefinierte Funktionen zur Integration mit externen APIs oder Diensten verwenden. Dies hilft beim Abrufen von Daten aus externen Quellen, beim Senden von Daten an externe REST-Endpunkte oder beim Ausführen benutzerdefinierter Aktionen basierend auf externen Ereignissen.

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

* **Pfeilfunktion mit obligatorischem jsdoc-Kommentar**

Beispiele für die Erstellung von Pfeilfunktionen:

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

<!-- 
    * @param {string=} b another parameter description
      /** */
    testFunction1=(a) => (return a)
    /** */
    testFunction2 = a => a + 100;-->

* **Funktionsausdruck mit obligatorischem jsdoc-Kommentar**

Erstellen Sie benutzerdefinierte Funktionen in den folgenden Formaten, um sie im Regeleditor eines adaptiven Formulars aufzulisten. Zum Beispiel:

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
> Sie können die `error.log` -Datei, falls Fehler wie benutzerdefinierte Funktionen im Regeleditor nicht aufgeführt werden.

<!--The `error.log` file also displays the methods and parameters that are not supported for custom functions. -->


## Benutzerdefinierte Funktion erstellen {#create-custom-function}

Erstellen Sie eine Client-Bibliothek, um benutzerdefinierte Funktionen im Regeleditor aufzurufen. Weitere Informationen finden Sie unter [Verwenden Client-seitiger Bibliotheken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/full-stack/clientlibs.html?lang=de#developing).

Schritte zum Erstellen benutzerdefinierter Funktionen:
1. [Erstellen einer Client-Bibliothek](#create-client-library)
1. [Clientbibliothek in einem adaptiven Formular hinzufügen](#use-custom-function)

### Erstellen einer Client-Bibliothek {#create-client-library}

Sie können benutzerdefinierte Funktionen hinzufügen, indem Sie die Client-Bibliothek hinzufügen. Um eine Client-Bibliothek zu erstellen, führen Sie die folgenden Schritte aus:

1. [Klonen Sie Ihr AEM Forms as a Cloud Service-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).
1. Erstellen Sie einen Ordner unter dem Ordner `[AEM Forms as a Cloud Service repository folder]/apps/`. Erstellen Sie beispielsweise einen Ordner mit dem Namen `experience-league`
1. Navigieren Sie zu `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` und erstellen Sie einen `ClientLibraryFolder` als `es6clientlibs`.
1. Hinzufügen einer Eigenschaft `categories`mit einem Zeichenfolgenwert als `es6customfunctions` der `es6clientlibs` Ordner.

   >[!NOTE]
   >
   >`es6customfunctions` ist eine Beispielkategorie. Sie können einen beliebigen Namen für die Kategorie auswählen.

1. Erstellen Sie einen Ordner mit dem Namen `js`.
1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/es6clientlibs/js`.
1. Fügen Sie eine JavaScript-Datei hinzu, beispielsweise `function.js`. Die Datei enthält den Code für die benutzerdefinierte Funktion.

   >[!NOTE]
   >
   >* Wenn die JavaScript-Datei mit dem Code für benutzerdefinierte Funktionen einen Fehler enthält, werden die benutzerdefinierten Funktionen nicht im Regeleditor eines adaptiven Formulars aufgeführt. Sie können auch die `error.log` -Datei für den Fehler.

   <!-- 
    >* AEM Adaptive Form supports the caching of custom functions. If the JavaScript is modified, the caching becomes invalidated, and it is parsed. You can see a message as `Fetched following custom functions list from cache` in the `error.log` file.  -->

1. Speichern Sie die Datei `function.js`.
1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/es6clientlibs/js`.
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

Sobald die Pipeline erfolgreich ausgeführt wurde, wird die in der Client-Bibliothek hinzugefügte benutzerdefinierte Funktion in Ihrer [Regeleditor für adaptive Formulare](/help/forms/rule-editor.md).

### Clientbibliothek in einem adaptiven Formular hinzufügen{#use-custom-function}

Nachdem Sie Ihre Client-Bibliothek hinzugefügt haben, verwenden Sie sie in Ihrem adaptiven Formular. Damit können Sie Ihre [benutzerdefinierte Funktion als Regel im Formular](/help/forms/rule-editor.md#custom-functions). So fügen Sie die Client-Bibliothek in Ihrem adaptiven Formular hinzu:

1. Öffnen Sie das Formular im Bearbeitungsmodus.
Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und wählen Sie **[!UICONTROL Öffnen]**.
1. Wählen Sie im Bearbeitungsmodus eine Komponente aus und wählen Sie dann ![Feldebene](assets/select_parent_icon.svg) > **[!UICONTROL Container für adaptive Formulare]** und wählen Sie ![cmppr](assets/configure-icon.svg).
1. Fügen Sie in der Seitenleiste unter „Name der Client-Bibliothek“ Ihre Client-Bibliothek hinzu. (In diesem Beispiel wäre das `es6customfunctions`.)

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/assets/clientlib-custom-function.png)

Erstellen Sie eine Regel, um die benutzerdefinierte Funktion im Regeleditor zu verwenden.

<!--

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





