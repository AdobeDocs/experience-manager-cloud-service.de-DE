---
title: Erstellen und Hinzufügen benutzerdefinierter Funktionen in einem adaptiven Formular
description: AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer eigene Funktionen im Regeleditor erstellen und verwenden können.
keywords: Fügen Sie eine benutzerdefinierte Funktion hinzu, verwenden Sie eine benutzerdefinierte Funktion, erstellen Sie eine benutzerdefinierte Funktion, verwenden Sie eine benutzerdefinierte Funktion im Regeleditor.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Core Components
exl-id: 24607dd1-2d65-480b-a831-9071e20c473d
role: User, Developer
source-git-commit: 52b87073cad84705b5dc0c6530aff44d1e686609
workflow-type: tm+mt
source-wordcount: '4333'
ht-degree: 4%

---


# Benutzerdefinierte Funktionen in Adaptive Forms (Kernkomponenten)

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-core-components/create-and-use-custom-functions) |
| AEM as a Cloud Service | Dieser Artikel |

## Einführung

AEM Forms unterstützt benutzerdefinierte Funktionen, mit denen Benutzer JavaScript-Funktionen zur Implementierung komplexer Geschäftsregeln definieren können. Diese benutzerdefinierten Funktionen erweitern die Funktionen von Formularen, indem sie die Manipulation und Verarbeitung der eingegebenen Daten zur Erfüllung bestimmter Anforderungen erleichtern. Sie ermöglichen auch eine dynamische Änderung des Formularverhaltens basierend auf vordefinierten Kriterien.

>[!NOTE]
>
> Stellen Sie sicher, dass die [Kernkomponente](https://github.com/adobe/aem-core-forms-components) auf die neueste Version eingestellt ist, um die neuesten Funktionen verwenden zu können.

### Verwendung benutzerdefinierter Funktionen {#uses-of-custom-function}

Die Verwendung benutzerdefinierter Funktionen in Adaptive Forms bietet folgende Vorteile:
* **Datenverarbeitung**: Benutzerdefinierte Funktionen helfen bei der Verarbeitung der in die Formularfelder eingegebenen Daten.
* **Validierung der Daten**: Benutzerdefinierte Funktionen ermöglichen es Ihnen, benutzerdefinierte Prüfungen für Formulareingaben durchzuführen und bestimmte Fehlermeldungen anzugeben.
* **Dynamisches Verhalten**: Mit benutzerdefinierten Funktionen können Sie das dynamische Verhalten Ihrer Formulare anhand bestimmter Bedingungen steuern. Beispielsweise können Sie Felder ein-/ausblenden, Feldwerte ändern oder die Formularlogik dynamisch anpassen.
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
Wenn der Name der Funktion mit dem Namen der Funktion selbst übereinstimmt, können Sie in der Syntax den Wert &quot;`[functionName]`&quot; weglassen.

#### Parameter

Der Parameter ist eine Liste von Argumenten, die von benutzerdefinierten Funktionen verwendet werden. Eine Funktion kann mehrere Parameter unterstützen. Die folgenden Syntaxen werden verwendet, um einen Parameter in einer benutzerdefinierten Funktion zu definieren:

* `@param {type} name <Parameter Description>`
* `@argument` `{type} name <Parameter Description>`
* `@arg` `{type}` `name <Parameter Description>`.
  `{type}` steht für den Parametertyp.  Zulässige Parametertypen sind:

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
   * scope: Stellt das global -Objekt dar, das schreibgeschützte Variablen wie Formularinstanzen, Zielfeldinstanzen und Methoden zum Ausführen von Formularänderungen innerhalb benutzerdefinierter Funktionen enthält. Sie wird als letzter Parameter in JavaScript-Anmerkungen deklariert und ist im Regeleditor eines adaptiven Formulars nicht sichtbar. Der Parameter scope greift auf das Objekt des Formulars oder der Komponente zu, um die für die Formularverarbeitung erforderliche Regel oder das Ereignis Trigger. Weitere Informationen zum Globals-Objekt und dessen Verwendung finden Sie unter [Klicken Sie hier](/help/forms/create-and-use-custom-functions.md#support-field-and-global-objects).

Beim Parametertyp wird nicht zwischen Groß- und Kleinschreibung unterschieden und Leerzeichen sind im Parameternamen nicht zulässig.

`<Parameter Description>` enthält Details zum Zweck des Parameters. Es kann mehrere Wörter enthalten.

**Optionale Parameter**
Standardmäßig sind alle Parameter obligatorisch. Sie können einen Parameter als optional definieren, indem Sie entweder `=` nach dem Parametertyp hinzufügen oder den Parameternamen in `[]` einschließen. Parameter, die in JavaScript-Anmerkungen als optional definiert wurden, werden im Regeleditor als optional angezeigt.
Um eine Variable als optionalen Parameter zu definieren, können Sie eine der folgenden Syntaxen verwenden:

* `@param {type=} Input1`

In der obigen Codezeile ist `Input1` ein optionaler Parameter ohne Standardwert. So deklarieren Sie einen optionalen Parameter mit dem Standardwert:
`@param {string=<value>} input1`

`input1` als optionalen Parameter verwenden, wobei der Standardwert auf `value` festgelegt ist.

* `@param {type} [Input1]`

In der obigen Codezeile ist `Input1` ein optionaler Parameter ohne Standardwert. So deklarieren Sie einen optionalen Parameter mit dem Standardwert:
`@param {array} [input1=<value>]`
`input1` ist ein optionaler Parameter des Array-Typs, dessen Standardwert auf `value` festgelegt ist.
Stellen Sie sicher, dass der Parametertyp in geschweifte Klammern {} eingeschlossen ist und der Parametername in eckigen Klammern eingeschlossen ist.

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

Die folgende Abbildung zeigt die Verwendung der benutzerdefinierten Funktion `OptionalParameterFunction` im Regeleditor:

![Optionale oder erforderliche Parameter ](/help/forms/assets/optional-default-params.png)

Sie können die Regel speichern, ohne einen Wert für die erforderlichen Parameter anzugeben. Die Regel wird jedoch nicht ausgeführt und es wird eine Warnmeldung angezeigt, wie folgt:

![Warnung bezüglich unvollständiger Regeln](/help/forms/assets/incomplete-rule.png)

Wenn der Benutzer den optionalen Parameter leer lässt, wird der Wert &quot;Undefined&quot;an die benutzerdefinierte Funktion für den optionalen Parameter übergeben.

Um mehr über das Definieren optionaler Parameter in JSDocs zu erfahren, klicken Sie [hier auf](https://jsdoc.app/tags-param).

#### Rückgabetyp

Der Rückgabetyp gibt den Typ des Werts an, den die benutzerdefinierte Funktion nach der Ausführung zurückgibt. Die folgenden Syntaxen werden verwendet, um einen Rückgabetyp in einer benutzerdefinierten Funktion zu definieren:

* `@return {type}`
* `@returns {type}`
  `{type}` steht für den Rückgabetyp der Funktion. Zulässige Rückgabetypen sind:
   * string: Stellt einen einzelnen Zeichenfolgenwert dar.
   * number: Stellt einen einzelnen numerischen Wert dar.
   * boolean: Stellt einen einzelnen booleschen Wert dar (true oder false).
   * string[]: Stellt ein Array von Zeichenfolgenwerten dar.
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
Wenn der Benutzer der benutzerdefinierten Funktion keine JavaScript-Anmerkungen hinzufügt, wird sie im Regeleditor anhand ihres Funktionsnamens aufgelistet. Es wird jedoch empfohlen, JavaScript-Anmerkungen einzubeziehen, um die Lesbarkeit der benutzerdefinierten Funktionen zu verbessern.

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


### Voraussetzungen für die Erstellung einer benutzerdefinierten Funktion

Bevor Sie mit dem Hinzufügen einer benutzerdefinierten Funktion zu Ihrem adaptiven Forms beginnen, stellen Sie Folgendes sicher:

**Software:**

* **Nur-Text-Editor (IDE)**: Obwohl jeder Nur-Text-Editor funktionieren kann, bietet eine integrierte Entwicklungsumgebung (IDE) wie Microsoft Visual Studio Code erweiterte Funktionen zur einfacheren Bearbeitung.

* **Git:** Dieses Versionskontrollsystem ist für die Verwaltung von Code-Änderungen erforderlich. Wenn Sie es nicht installiert haben, laden Sie es von https://git-scm.com herunter.

### Erstellen einer Client-Bibliothek {#create-client-library}

Sie können benutzerdefinierte Funktionen hinzufügen, indem Sie eine Client-Bibliothek hinzufügen. Um eine Client-Bibliothek zu erstellen, führen Sie die folgenden Schritte aus:

**Repository klonen**

Klonen Sie Ihr [AEM Forms as a Cloud Service-Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git):

1. Öffnen Sie die Befehlszeile oder ein Terminal-Fenster.

1. Navigieren Sie zum gewünschten Speicherort auf Ihrem Computer, auf dem Sie das Repository speichern möchten.

1. Führen Sie den folgenden Befehl aus, um das Repository zu klonen:

   `git clone [Git Repository URL]`

Mit diesem Befehl wird das Repository heruntergeladen und ein lokaler Ordner des geklonten Repositorys auf Ihrem Computer erstellt. In diesem Handbuch wird dieser Ordner als das AEMaaCS-Projektverzeichnis ] bezeichnet.[

**Hinzufügen eines Client-Bibliotheksordners**

Gehen Sie wie folgt vor, um den neuen Client-Bibliotheksordner zum AEMaaCS-Projektverzeichnis ] hinzuzufügen:[

1. Öffnen Sie das Verzeichnis [AEMaaCS-Projekt] in einem Editor.

   ![Ordnerstruktur der benutzerdefinierten Funktion](/help/forms/assets/custom-library-folder-structure.png)

1. Suchen Sie `ui.apps`.
1. Fügen Sie neuen Ordner hinzu. Fügen Sie beispielsweise einen Ordner mit dem Namen `experience-league` hinzu.
1. Navigieren Sie zum Ordner &quot;`/experience-league/`&quot;und fügen Sie den Ordner &quot;`ClientLibraryFolder`&quot;hinzu. Erstellen Sie beispielsweise einen Client-Bibliotheksordner mit dem Namen &quot;`customclientlibs`&quot;.

   `Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/`

**Hinzufügen von Dateien und Ordnern zum Ordner &quot;Client-Bibliothek&quot;**

Fügen Sie dem hinzugefügten Client-Bibliotheksordner Folgendes hinzu:

* .content.xml-Datei
* js.txt-Datei
* js-Ordner

`Location is: [AEMaaCS project directory]/ui.apps/src/main/content/jcr_root/apps/experience-league/customclientlibs/`

1. Fügen Sie in den `.content.xml` die folgenden Codezeilen hinzu:

   ```javascript
   <?xml version="1.0" encoding="UTF-8"?>
   <jcr:root xmlns:cq="http://www.day.com/jcr/cq/1.0" xmlns:jcr="http://www.jcp.org/jcr/1.0"
   jcr:primaryType="cq:ClientLibraryFolder"
   categories="[customfunctionscategory]"/>
   ```

   >[!NOTE]
   >
   > Sie können einen beliebigen Namen für die Eigenschaften `client library folder` und `categories` auswählen.

1. Fügen Sie in den `js.txt` die folgenden Codezeilen hinzu:

   ```javascript
         #base=js
       function.js
   ```
1. Fügen Sie im Ordner `js` die JavaScript-Datei als `function.js` hinzu, die die benutzerdefinierten Funktionen enthält:

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
1. Speichern Sie die Dateien.

![Ordnerstruktur der benutzerdefinierten Funktion](/help/forms/assets/custom-function-added-files.png)

**Fügen Sie den neuen Ordner in filter.xml** ein:

1. Navigieren Sie zur Datei `/ui.apps/src/main/content/META-INF/vault/filter.xml` in Ihrem [AEMaaCS-Projektverzeichnis].

1. Öffnen Sie die Datei und fügen Sie die folgende Zeile am Ende ein:

   `<filter root="/apps/experience-league" />`
1. Speichern Sie die Datei.

![benutzerdefinierter Funktionsfilter xml](/help/forms/assets/custom-function-filterxml.png)

**Stellen Sie den neu erstellten Client-Bibliotheksordner in Ihrer AEM-Umgebung bereit**

Stellen Sie das [AEMaaCS Projektverzeichnis] von AEM as a Cloud Service in Ihrer Cloud Service-Umgebung bereit. So stellen Sie es in Ihrer Cloud Service-Umgebung bereit:

1. Übergeben Sie die Änderungen

   1. Fügen Sie die Änderungen mit den folgenden Befehlen hinzu, übertragen Sie sie und pushen Sie sie in das Repository:

   ```javascript
       git add .
       git commit -a -m "Adding custom functions"
       git push
   ```

1. Stellen Sie den aktualisierten Code bereit:

   1. Trigger einer Bereitstellung Ihres Codes über die vorhandene Vollstapelpipeline. Dadurch wird der aktualisierte Code automatisch erstellt und bereitgestellt.

Wenn Sie noch keine Pipeline eingerichtet haben, lesen Sie das Handbuch zur [Einrichtung einer Pipeline für AEM Forms as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline).

Sobald die Pipeline erfolgreich ausgeführt wurde, ist die benutzerdefinierte Funktion, die in der Client-Bibliothek hinzugefügt wurde, im Regeleditor für adaptive Formulare [verfügbar.](/help/forms/rule-editor-core-components.md)

### Clientbibliothek zu einem adaptiven Formular hinzufügen{#use-custom-function}

Nachdem Sie Ihre Client-Bibliothek in Ihrer Forms CS-Umgebung bereitgestellt haben, verwenden Sie die zugehörigen Funktionen in Ihrem adaptiven Formular. Hinzufügen der Client-Bibliothek zum adaptiven Formular

1. Öffnen Sie das Formular im Bearbeitungsmodus. Um ein Formular im Bearbeitungsmodus zu öffnen, wählen Sie ein Formular aus und klicken Sie auf **[!UICONTROL Bearbeiten]**.
1. Öffnen Sie den Inhalts-Browser und wählen Sie die **[!UICONTROL Guide-Container]**-Komponente Ihres adaptiven Formulars aus.
1. Klicken Sie auf das Symbol für die Guide-Container-Eigenschaften ![Guide-Eigenschaften](/help/forms/assets/configure-icon.svg). Das Dialogfeld „Container für ein adaptives Formular“ wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Einfach]** und wählen Sie den Namen der Kategorie **[!UICONTROL Client-Bibliothek]** aus der Dropdownliste aus (wählen Sie in diesem Fall `customfunctionscategory` aus).

   ![Hinzufügen der benutzerdefinierten Funktion zur Client-Bibliothek](/help/forms/assets/clientlib-custom-function.png)

   >[!NOTE]
   >
   > Es können mehrere Kategorien hinzugefügt werden, indem eine kommagetrennte Liste innerhalb des Felds **[!UICONTROL Kategorie der Client-Bibliothek]** angegeben wird.

1. Klicken Sie auf **[!UICONTROL Fertig]**.

Sie können die benutzerdefinierte Funktion im Regeleditor [eines adaptiven Formulars](/help/forms/rule-editor-core-components.md) mit den Anmerkungen in [JavaScript](##js-annotations) verwenden.

## Verwenden einer benutzerdefinierten Funktion in einem adaptiven Formular

In einem adaptiven Formular können Sie [benutzerdefinierte Funktionen im Regeleditor](/help/forms/rule-editor-core-components.md) verwenden. Fügen Sie der JavaScript-Datei (`Function.js`) den folgenden Code hinzu, um das Alter basierend auf dem Geburtsdatum (JJJ-MM-TT) zu berechnen. Erstellen Sie eine benutzerdefinierte Funktion als `calculateAge()` , die das Geburtsdatum als Eingabe annimmt und das Alter zurückgibt:

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

Wenn der Benutzer im obigen Beispiel das Geburtsdatum im Format JJJ-MM-TT eingibt, wird die benutzerdefinierte Funktion `calculateAge` aufgerufen und das Alter zurückgegeben.

![Benutzerdefinierte Funktion &quot;Seite berechnen&quot;im Regeleditor](/help/forms/assets/custom-function-calculate-age.png)

Sehen wir uns das Formular in der Vorschau an, um zu sehen, wie die benutzerdefinierten Funktionen über den Regeleditor implementiert werden:

![Benutzerdefinierte Funktion &quot;Seite berechnen&quot;in der Formularvorschau des Regeleditors](/help/forms/assets/custom-function-age-calculate-form.png)

>[!NOTE]
>
> Sie können auf den folgenden Ordner [Benutzerdefinierte Funktion](/help/forms/assets//customfunctions.zip) verweisen. Laden Sie diesen Ordner herunter und installieren Sie ihn mithilfe des [Package Manager](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/implementing/developer-tools/package-manager) in Ihrer AEM-Instanz.


### Festlegen von Dropdown-Listenoptionen mit benutzerdefinierten Funktionen

Der Regeleditor in den Kernkomponenten unterstützt die Eigenschaft **Optionen von** nicht zum Festlegen der Dropdown-Listenoptionen zur Laufzeit. Sie können die Optionen der Dropdown-Liste jedoch mit benutzerdefinierten Funktionen festlegen.

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

Im obigen Code wird `setEnums` verwendet, um die Eigenschaft `enum` festzulegen, und `setEnumNames` wird verwendet, um die Eigenschaft `enumNames` der Dropdown-Liste festzulegen.

Erstellen wir eine Regel für die Schaltfläche `Next`, die den Wert der Dropdown-Listenoption festlegt, wenn der Benutzer auf die Schaltfläche `Next` klickt:

![Optionen für Dropdown-Listen](/help/forms/assets/drop-down-list-options.png)

In der folgenden Abbildung sehen Sie, wo die Optionen der Dropdown-Liste beim Klicken auf die Schaltfläche Anzeigen eingestellt sind:

![Dropdown-Optionen im Regeleditor](/help/forms/assets/drop-down-option-rule-editor.png)



### Unterstützung für asynchrone Funktionen in benutzerdefinierten Funktionen {#support-of-async-functions}

Asynchrone benutzerdefinierte Funktionen werden nicht in der Liste des Regeleditors angezeigt. Es ist jedoch möglich, asynchrone Funktionen innerhalb benutzerdefinierter Funktionen aufzurufen, die mit synchronen Funktionsausdrücken erstellt wurden.

![Synchronisieren und asynchrone benutzerdefinierte Funktion](/help/forms/assets/workflow-for-sync-async-custom-fumction.png)

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

Im obigen Beispiel ist die asyncFunction-Funktion ein `asynchronous function`. Es führt einen asynchronen Vorgang durch, indem eine `GET` -Anfrage an `https://petstore.swagger.io/v2/store/inventory` gesendet wird. Er wartet mit `await` auf die Antwort, analysiert den Antworttext mit dem `response.json()` als JSON und gibt dann die Daten zurück. Die Funktion `callAsyncFunction` ist eine synchrone benutzerdefinierte Funktion, die die Funktion `asyncFunction` aufruft und die Antwortdaten in der Konsole anzeigt. Obwohl die Funktion `callAsyncFunction` synchron ist, ruft sie die asynchrone asyncFunction-Funktion auf und verarbeitet ihr Ergebnis mit `then` - und `catch` -Anweisungen.

Um seine Funktionsweise zu sehen, fügen wir eine Schaltfläche hinzu und erstellen eine Regel für die Schaltfläche, die die asynchrone Funktion bei einem Klick auf eine Schaltfläche aufruft.

![Erstellen einer Regel für die asynchrone Funktion](/help/forms/assets/rule-for-async-funct.png)

In der Abbildung unten finden Sie das Konsolenfenster, um zu zeigen, dass beim Klicken auf die Schaltfläche `Fetch` die benutzerdefinierte Funktion `callAsyncFunction` aufgerufen wird, die wiederum eine asynchrone Funktion `asyncFunction` aufruft. Inspect Sie das Konsolenfenster, um die Antwort auf die Schaltfläche anzuzeigen. Klicken Sie auf:

![Konsolenfenster](/help/forms/assets/async-custom-funct-console.png)

Im Folgenden werden die Funktionen von benutzerdefinierten Funktionen vorgestellt.

## Verschiedene Funktionen für benutzerdefinierte Funktionen

Sie können benutzerdefinierte Funktionen verwenden, um Formularen personalisierte Funktionen hinzuzufügen. Diese Funktionen unterstützen verschiedene Funktionen, wie z. B. das Arbeiten mit bestimmten Feldern, das Verwenden globaler Felder oder das Zwischenspeichern. Diese Flexibilität ermöglicht es Ihnen, Formulare entsprechend den Anforderungen Ihres Unternehmens anzupassen.

### Felder und globale Perimeter in benutzerdefinierten Funktionen {#support-field-and-global-objects}

Feldobjekte beziehen sich auf die einzelnen Komponenten oder Elemente in einem Formular, z. B. Textfelder und Kontrollkästchen. Das Globals -Objekt enthält schreibgeschützte Variablen wie Formularinstanz, Zielfeldinstanz und Methoden zum Durchführen von Formularänderungen in benutzerdefinierten Funktionen.

>[!NOTE]
>
> Der `param {scope} globals` muss der letzte Parameter sein und wird nicht im Regeleditor eines adaptiven Formulars angezeigt.

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

Im Folgenden erfahren wir, wie benutzerdefinierte Funktionen mithilfe eines `Contact Us` -Formulars mithilfe verschiedener Anwendungsfälle Felder und globale Objekte verwenden.

![Kontaktformular ](/help/forms/assets/contact-us-form.png)

+++ **Anwendungsfall**: Anzeigen eines Bedienfelds mithilfe der `SetProperty`-Regel

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um das Formularfeld auf `Required` festzulegen.

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
> * Sie können die Feldeigenschaften mit den verfügbaren Eigenschaften in `[form-path]/jcr:content/guideContainer.model.json` konfigurieren.
> * Änderungen am Formular, die mit der Methode `setProperty` des Globals -Objekts vorgenommen werden, sind asynchron und werden bei der Ausführung der benutzerdefinierten Funktion nicht berücksichtigt.

In diesem Beispiel wird das Bedienfeld `personaldetails` durch Klicken auf die Schaltfläche überprüft. Wenn im Bedienfeld keine Fehler erkannt werden, wird ein weiteres Bedienfeld, das Bedienfeld `feedback`, beim Klicken auf die Schaltfläche angezeigt.

Erstellen wir eine Regel für die Schaltfläche `Next` , die das Bedienfeld `personaldetails` validiert und den Bereich `feedback` sichtbar macht, wenn der Benutzer auf die Schaltfläche `Next` klickt.

![Eigenschaft festlegen](/help/forms/assets/custom-function-set-property.png)

In der folgenden Abbildung sehen Sie, wo das Bedienfeld `personaldetails` beim Klicken auf die Schaltfläche `Next` validiert wird. Falls alle Felder innerhalb der `personaldetails` validiert werden, wird das Bedienfeld `feedback` angezeigt.

![Festlegen der Vorschau für die Eigenschaftsform ](/help/forms/assets/set-property-form-preview.png)

Wenn Fehler in den Feldern des Bereichs `personaldetails` vorhanden sind, werden sie beim Klicken auf die Schaltfläche `Next` auf Feldebene angezeigt und das Bedienfeld `feedback` bleibt unsichtbar.

![Festlegen der Vorschau für die Eigenschaftsform ](/help/forms/assets/set-property-panel.png)

+++

+++ **Anwendungsfall**: Validieren Sie das Feld.

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um das Feld zu validieren.

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
> Wenn in der Funktion `validate()` kein Argument übergeben wird, wird das Formular validiert.

In diesem Beispiel wird ein benutzerdefiniertes Überprüfungsmuster auf das Feld `contact` angewendet. Benutzer müssen eine Telefonnummer eingeben, die mit `10` gefolgt von `8` Ziffern beginnt. Wenn der Benutzer eine Telefonnummer eingibt, die nicht mit `10` beginnt oder mehr oder weniger als `8` Ziffern enthält, wird beim Klicken auf die Schaltfläche eine Überprüfungsfehlermeldung angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/custom-function-validation-pattern.png)

Der nächste Schritt besteht darin, eine Regel für die Schaltfläche `Next` zu erstellen, die das Feld `contact` beim Klicken auf die Schaltfläche validiert.

![Überprüfungsmuster](/help/forms/assets/custom-function-validate.png)

Beachten Sie die folgende Abbildung, um zu zeigen, dass eine Fehlermeldung auf Feldebene angezeigt wird, wenn der Benutzer eine Telefonnummer eingibt, die nicht mit `10` beginnt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/custom-function-validate-error-message.png)

Wenn der Benutzer eine gültige Telefonnummer eingibt und alle Felder im Bedienfeld `personaldetails` validiert werden, wird das Bedienfeld `feedback` auf dem Bildschirm angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/validate-form-preview-form.png)

+++

+++ **Nutzungsszenario**: Bedienfeld zurücksetzen

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um den Bereich zurückzusetzen.

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
> Wenn in der Funktion `reset()` kein Argument übergeben wird, wird das Formular validiert.

In diesem Beispiel wird das Bedienfeld `personaldetails` beim Klicken auf die Schaltfläche `Clear` zurückgesetzt. Als Nächstes erstellen Sie eine Regel für die Schaltfläche `Clear` , mit der das Bedienfeld auf die Schaltfläche zurückgesetzt wird.

![Schaltfläche &quot;Löschen&quot;](/help/forms/assets/custom-function-reset-field.png)

In der folgenden Abbildung sehen Sie, dass der Bereich `personaldetails` zurückgesetzt wird, wenn der Benutzer auf die Schaltfläche `clear` klickt:

![Formular zurücksetzen](/help/forms/assets/custom-function-reset-form.png)

+++

+++ **Anwendungsfall**: Um eine benutzerdefinierte Meldung auf Feldebene anzuzeigen und das Feld als ungültig zu kennzeichnen

Mit der Funktion `markFieldAsInvalid()` können Sie ein Feld als ungültig definieren und eine benutzerdefinierte Fehlermeldung auf Feldebene festlegen. Der `fieldIdentifier` -Wert kann `fieldId`, `field qualifiedName` oder `field dataRef` sein. Der Wert des Objekts `option` kann `{useId: true}`, `{useQualifiedName: true}` oder `{useDataRef: true}` sein.
Die Syntax, mit der ein Feld als ungültig markiert und eine benutzerdefinierte Nachricht festgelegt wird, lautet:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um eine benutzerdefinierte Nachricht auf Feldebene zu aktivieren.

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

Der nächste Schritt besteht darin, eine Regel für das Feld `comments` zu erstellen:

![Feld als ungültig markieren](/help/forms/assets/custom-function-invalid-field.png)

Sehen Sie sich die unten stehende Demonstration an, um anzuzeigen, dass die Anzeige einer benutzerdefinierten Nachricht auf Feldebene durch die Eingabe von negativem Feedback im Feld `comments` Trigger wird:

![Feld als ungültiges Vorschauformular markieren](/help/forms/assets/custom-function-invalidfield-form.png)

Wenn der Benutzer mehr als 15 Zeichen in das Textfeld &quot;Kommentare&quot;eingibt, wird das Feld validiert und das Formular wird gesendet:

![Feld als gültiges Vorschauformular markieren](/help/forms/assets/custom-function-validfield-form.png)

+++

+++ **Nutzungsszenario**: Übermittlung geänderter Daten an den Server

Die folgende Codezeile:
`globals.functions.submitForm(globals.functions.exportData(), false);` wird verwendet, um die Formulardaten nach der Bearbeitung zu senden.
* Das erste Argument sind die zu übermittelnden Daten.
* Das zweite Argument stellt dar, ob das Formular vor der Übermittlung validiert werden soll. Er ist `optional` und standardmäßig als `true` festgelegt.
* Das dritte Argument ist der `contentType` der Übermittlung, der ebenfalls optional ist, wobei der Standardwert `multipart/form-data` lautet. Die anderen Werte können `application/json` und `application/x-www-form-urlencoded` sein.

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um die bearbeiteten Daten an den Server zu senden:

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

Wenn der Benutzer in diesem Beispiel das Textfeld `comments` leer lässt, wird der `NA` beim Senden des Formulars an den Server gesendet.

Erstellen Sie nun eine Regel für die `Submit` -Schaltfläche, mit der Daten gesendet werden:

![Daten übermitteln](/help/forms/assets/custom-function-submit-data.png)

In der Abbildung unten finden Sie die `console window` , die zeigt, dass der Wert als `NA` auf dem Server gesendet wird, wenn der Benutzer das Textfeld `comments` leer lässt:

![Senden von Daten im Konsolenfenster](/help/forms/assets/custom-function-submit-data-form.png)

Sie können auch das Konsolenfenster überprüfen, um die an den Server gesendeten Daten anzuzeigen:

![Inspect-Daten im Konsolenfenster](/help/forms/assets/custom-function-submit-data-console-data.png)

+++

+++ **Nutzungsszenario**: Erfolgreiche Formularübermittlung und Fehler-Handler überschreiben

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um die Übermittlung oder Fehlermeldung für Formularübermittlungen anzupassen und die Meldungen für Formularübermittlungen in einem modalen Feld anzuzeigen:

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

In diesem Beispiel werden die Erfolgs- und Fehlermeldungen in einem Modal angezeigt, wenn der Benutzer die benutzerdefinierten Funktionen `customSubmitSuccessHandler` und `customSubmitErrorHandler` verwendet. Die JavaScript-Funktion `showModal(type, message)` wird verwendet, um ein modales Dialogfeld dynamisch zu erstellen und auf einem Bildschirm anzuzeigen.

Erstellen Sie nun eine Regel für die erfolgreiche Formularübermittlung:

![Erfolg der Formularübermittlung](/help/forms/assets/form-submission-success.png)

In der unten stehenden Abbildung sehen Sie, wie die Erfolgsmeldung bei erfolgreicher Übermittlung des Formulars in einem Modal dargestellt wird:

![Erfolgsmeldung zur Formularübermittlung](/help/forms/assets/form-submission-success-message.png)

Erstellen Sie eine Regel für fehlgeschlagene Formularübermittlungen:

![Fehler bei der Formularübermittlung](/help/forms/assets/form-submission-fail.png)

In der folgenden Abbildung sehen Sie, dass die Fehlermeldung in einem Modal angezeigt wird, wenn die Formularübermittlung fehlschlägt:

![Fehlermeldung bei Formularübermittlung](/help/forms/assets/form-submission-fail-message.png)

Um den Erfolg und das Fehlschlagen der Formularübermittlung standardmäßig anzuzeigen, sind die Funktionen `Default submit Form Success Handler` und `Default submit Form Error Handler` standardmäßig verfügbar.

Falls der benutzerdefinierte Übermittlungs-Handler nicht wie erwartet in vorhandenen AEM Projekten oder Formularen ausgeführt werden kann, lesen Sie den Abschnitt [Fehlerbehebung](#troubleshooting) .

+++

+++ **Anwendungsfall**: Führen Sie Aktionen in einer bestimmten Instanz des wiederholbaren Bereichs durch.

Regeln, die mit dem visuellen Regeleditor in einem wiederholbaren Bereich erstellt wurden, gelten für die letzte Instanz des wiederholbaren Bereichs. Um eine Regel für eine bestimmte Instanz des wiederholbaren Bereichs zu schreiben, können wir eine benutzerdefinierte Funktion verwenden.

Erstellen wir ein anderes Formular, um Informationen über Reisende zu sammeln, die zu einem Ziel fahren. Ein Reisende-Bedienfeld wird als wiederholbares Bedienfeld hinzugefügt, in dem der Benutzer mithilfe der Schaltfläche `Add Traveler` Details für fünf Reisende hinzufügen kann.

![Informationen für Reisende](/help/forms/assets/traveler-info-form.png)

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) erläutert, um Aktionen in einer bestimmten Instanz des wiederholbaren Bereichs durchzuführen, die nicht der letzte ist:

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

In diesem Beispiel führt die benutzerdefinierte Funktion `hidePanelInRepeatablePanel` eine Aktion in einer bestimmten Instanz des wiederholbaren Bereichs durch. Im obigen Code stellt `travelerinfo` den wiederholbaren Bereich dar. Der Code `repeatablePanel[1].traveler, {visible: false}` blendet das Bedienfeld in der zweiten Instanz des wiederholbaren Bedienfelds aus.

Fügen Sie eine Schaltfläche mit der Bezeichnung `Hide` hinzu und fügen Sie eine Regel hinzu, um die zweite Instanz eines wiederholbaren Bereichs auszublenden.

![Bereichsregel ausblenden](/help/forms/assets/custom-function-hidepanel-rule.png)

Im folgenden Video erfahren Sie, dass beim Klicken auf `Hide` der Bereich in der zweiten wiederholbaren Instanz ausgeblendet wird:

>[!VIDEO](https://video.tv.adobe.com/v/3429554?quality=12&learn=on)

+++

+++ **Anwendungsfall**: Füllen Sie das Feld beim Laden des Formulars mit einem Wert vorab aus

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) erläutert, um den vorausgefüllten Wert in ein Feld zu laden, wenn das Formular initialisiert wird:

```javascript
/**
 * Tests import data
 * @name testImportData
 * @param {scope} globals
 */
function testImportData(globals)
{
    globals.functions.importData(Object.fromEntries([['amount','10000']]));
} 
```

Im oben genannten Code füllt die Funktion `testImportData` beim Laden des Formulars das Textfeld `Booking Amount` im Voraus aus. Nehmen wir an, das Buchungsformular setzt voraus, dass der Mindestbuchungsbetrag `10,000` ist.

Erstellen wir eine Regel bei der Formularinitialisierung, bei der der Wert im Textfeld `Booking Amount` mit einem angegebenen Wert vorausgefüllt wird, wenn das Formular geladen wird:

![Datenregel importieren](/help/forms/assets/custom-function-import-data.png)

Im folgenden Screenshot wird gezeigt, dass beim Laden des Formulars der Wert im Textfeld `Booking Amount` mit einem angegebenen Wert vorausgefüllt ist:

![Formular für Datenregel importieren](/help/forms/assets/custom-function-prefill-form.png)

+++

+++ **Anwendungsfall**: Fokus auf ein bestimmtes Feld legen

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) erläutert, um den Fokus auf das angegebene Feld zu legen, wenn auf die Schaltfläche `Submit` geklickt wird:

```javascript
/**
 * @name testSetFocus
 * @param {object} emailField
 * @param {scope} globals
 */
    function testSetFocus(field, globals)
    {
        globals.functions.setFocus(field);
    }
```

Fügen Sie der Schaltfläche `Submit` eine Regel hinzu, um den Fokus beim Klicken auf das Textfeld `Email ID` festzulegen:

![Fokusregel festlegen](/help/forms/assets/custom-function-set-focus.png)

Der folgende Screenshot zeigt, dass beim Klicken auf die Schaltfläche `Submit` der Fokus auf das Feld `Email ID` gelegt wird:

![Fokusregel festlegen](/help/forms/assets/custom-function-set-focus-form.png)

>[!NOTE]
>
> Sie können den optionalen Parameter `$focusOption` verwenden, wenn Sie sich auf das nächste oder vorherige Feld relativ zum Feld `email` konzentrieren möchten.

+++

+++ **Use**: Fügen Sie wiederholbare Bereiche mithilfe der Eigenschaft `dispatchEvent` hinzu oder löschen Sie sie

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um beim Klicken auf die Schaltfläche `Add Traveler` mit der Eigenschaft `dispatchEvent` einen Bereich hinzuzufügen:

```javascript
/**
 * Tests add instance with dispatchEvent
 * @name testAddInstance
 * @param {scope} globals
 */
function testAddInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel,'addInstance');
}
```

Fügen Sie der Schaltfläche `Add Traveler` eine Regel hinzu, um das wiederholbare Bedienfeld hinzuzufügen, wenn darauf geklickt wird:

![Bereichsregel hinzufügen](/help/forms/assets/custom-function-add-panel.png)

Beachten Sie das folgende GIF-Dokument, das zeigt, dass beim Klicken auf die Schaltfläche `Add Traveler` das Bedienfeld mithilfe der Eigenschaft `dispatchEvent` hinzugefügt wird:

![Bedienfeld hinzufügen](/help/forms/assets/custom-function-add-panel.gif)

Fügen Sie auf ähnliche Weise die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) beschrieben, um einen Bereich zu löschen, wenn auf die Schaltfläche `Delete Traveler` mit der Eigenschaft `dispatchEvent` geklickt wird:

```javascript
/**
 
 * @name testRemoveInstance
 * @param {scope} globals
 */
function testRemoveInstance(globals)
{
    var repeatablePanel = globals.form.traveler;
    globals.functions.dispatchEvent(repeatablePanel, 'removeInstance');
} 
```

Fügen Sie der Schaltfläche `Delete Traveler` eine Regel hinzu, um den wiederholbaren Bereich beim Klicken zu löschen:

![Bereichsregel löschen](/help/forms/assets/custom-function-delete-panel.png)

Beachten Sie das folgende GIF-Dokument, das zeigt, dass beim Klicken auf die Schaltfläche `Delete Traveler` das Reisende-Bedienfeld mithilfe der Eigenschaft `dispatchEvent` gelöscht wird:

![Bedienfeld löschen](/help/forms/assets/custom-function-delete-panel.gif)

+++

## Caching-Unterstützung für benutzerdefinierte Funktionen

Adaptive Forms implementiert Caching für benutzerdefinierte Funktionen, um die Reaktionszeit beim Abrufen der benutzerdefinierten Funktionsliste im Regeleditor zu verkürzen. Eine Meldung mit dem Wert `Fetched following custom functions list from cache` wird in der Datei `error.log` angezeigt.

![benutzerdefinierte Funktion mit Cache-Unterstützung](/help/forms/assets/custom-function-cache-error.png)

Wenn die benutzerdefinierten Funktionen geändert werden, wird die Zwischenspeicherung invalidiert und analysiert.

## Fehlerbehebung {#troubleshooting}

* Wenn der benutzerdefinierte Übermittlungshandler nicht wie erwartet in bestehenden AEM Projekten oder Formularen ausgeführt werden kann, führen Sie die folgenden Schritte aus:
   * Stellen Sie sicher, dass die Version der [Kernkomponenten auf Version 3.0.18 und höher](https://github.com/adobe/aem-core-forms-components) aktualisiert ist. Für bestehende AEM Projekte und Formulare sind jedoch weitere Schritte erforderlich:

   * Für das AEM Projekt sollte der Benutzer alle Instanzen von `submitForm('custom:submitSuccess', 'custom:submitError')` durch `submitForm()` ersetzen und das Projekt über die Cloud Manager-Pipeline bereitstellen.

   * Wenn die benutzerdefinierten Übermittlungs-Handler für vorhandene Formulare nicht ordnungsgemäß funktionieren, muss der Benutzer die Regel `submitForm` mithilfe des Regeleditors auf der Schaltfläche **Senden** öffnen und speichern. Diese Aktion ersetzt die vorhandene Regel von `submitForm('custom:submitSuccess', 'custom:submitError')` durch `submitForm()` im Formular.


* Wenn die JavaScript-Datei mit dem Code für benutzerdefinierte Funktionen einen Fehler enthält, werden die benutzerdefinierten Funktionen nicht im Regeleditor eines adaptiven Formulars aufgeführt. Um die Liste der benutzerdefinierten Funktionen zu überprüfen, können Sie zur Datei `error.log` für den Fehler navigieren. Im Fall eines Fehlers wird die Liste der benutzerdefinierten Funktionen leer angezeigt:

  ![Fehlerprotokolldatei](/help/forms/assets/custom-function-list-error-file.png)

  Wenn kein Fehler auftritt, wird die benutzerdefinierte Funktion abgerufen und in der Datei &quot;`error.log`&quot;angezeigt. In der Datei `error.log` wird eine Meldung mit dem Wert `Fetched following custom functions list` angezeigt:

  ![Fehlerprotokolldatei mit ordnungsgemäßer benutzerdefinierter Funktion](/help/forms/assets/custom-function-list-fetched-in-error.png)

## Überlegungen

* Die `parameter type` und `return type` unterstützen `None` nicht.

* Folgende Funktionen werden in der benutzerdefinierten Funktionsliste nicht unterstützt:
   * Generator-Funktionen
   * Async/Await-Funktionen
   * Methodendefinitionen
   * Klassenmethoden
   * Standardparameter
   * REST-Parameter

## Siehe auch {#see-also}

{{see-also}}


