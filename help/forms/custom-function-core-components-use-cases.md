---
title: In diesem Artikel werden verschiedene Anwendungsfälle für eine benutzerdefinierte Funktion in einem adaptiven Formular beschrieben, die auf Kernkomponenten basiert.
description: In diesem Artikel werden verschiedene Anwendungsfälle für eine benutzerdefinierte Funktion in einem adaptiven Formular beschrieben, die auf Kernkomponenten basiert. Benutzerdefinierte Funktionen werden im Regeleditor verwendet, um benutzerdefinierte Regeln für das Formular zu erstellen.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: df92b91e-f3b0-4a08-bd40-e99edc9a50a5
source-git-commit: 5b5b44f8dffc01a75eda464cd7759cf03028c2c6
workflow-type: tm+mt
source-wordcount: '2184'
ht-degree: 34%

---

# Beispiele für die Entwicklung und Verwendung benutzerdefinierter Funktionen

Der Artikel enthält die detaillierten Beispiele für benutzerdefinierte Funktionen für ein adaptives Formular, das auf Kernkomponenten basiert, und bietet wertvolle Einblicke in ihre effektive Implementierung in verschiedenen Szenarien. Benutzerdefinierte Funktionen werden im Regeleditor einer AEM Forms verwendet und ermöglichen es Entwickelnden, die Logik zu definieren und zu steuern, die das Formularverhalten steuert.
In diesem Artikel werden verschiedene Implementierungen benutzerdefinierter Funktionen untersucht und gezeigt, wie sie verwendet werden können, um Formulare an spezifische Anforderungen anzupassen und die allgemeine Funktionalität zu verbessern.

## Füllen der Dropdown-Listenoptionen mit benutzerdefinierten Funktionen

Der Regeleditor in den Kernkomponenten unterstützt die Eigenschaft **Optionen festlegen** nicht, um Dropdown-Listenoptionen zur Laufzeit dynamisch zu füllen. Sie können jedoch Dropdown-Listenoptionen mit benutzerdefinierten Funktionen füllen, mit denen Sie Optionen basierend auf einer bestimmten Logik abrufen können. Benutzerdefinierte Funktionen bieten mehr Flexibilität und Kontrolle darüber, wie und wann die Dropdown-Optionen ausgefüllt werden, und verbessern das Benutzererlebnis.

Um die Dropdown-Listenoptionen mit einer benutzerdefinierten Funktion zu füllen, fügen Sie den folgenden Code hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben:


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

Im obigen Code wird `setEnums` verwendet, um die `enum`-Eigenschaft festzulegen, und `setEnumNames` wird verwendet, um die `enumNames`-Eigenschaft von Dropdown festzulegen.

Erstellen wir eine Regel für die Schaltfläche `Next` , die den Wert der Dropdown-Listenoption festlegt, wenn der Benutzer auf die Schaltfläche `Next` klickt:

![Dropdown-Listenoptionen](/help/forms/assets/drop-down-list-options.png)

Anhand der unten stehenden Abbildung können Sie sehen, wo die Optionen der Dropdown-Liste eingestellt sind, wenn Sie auf die Schaltfläche Anzeigen klicken:

![Dropdown-Optionen im Regeleditor](/help/forms/assets/drop-down-option-rule-editor.png)

## Anzeigen eines Bereichs mithilfe der `SetProperty`

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen mithilfe eines `Contact Us` Formulars Felder und globale Objekte verwenden.

![Kontaktformular ](/help/forms/assets/contact-us-form.png)

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben, um das Formularfeld auf `Required` festzulegen.

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
> * Änderungen am Formular, die mit der Methode `setProperty` des Globals-Objekts vorgenommen werden, sind asynchron und werden bei der Ausführung der benutzerdefinierten Funktion nicht berücksichtigt.

In diesem Beispiel wird das Bedienfeld `personaldetails` durch Klicken auf die Schaltfläche überprüft. Wenn im Bedienfeld keine Fehler erkannt werden, wird ein weiteres Bedienfeld, das Bedienfeld `feedback`, beim Klicken auf die Schaltfläche angezeigt.

Erstellen wir eine Regel für die Schaltfläche `Next`, die das Bedienfeld `personaldetails` validiert und das Bedienfeld `feedback` sichtbar macht, wenn Benutzende auf die Schaltfläche `Next` klicken.

![Eigenschaft festlegen](/help/forms/assets/custom-function-set-property.png)

In der folgenden Abbildung sehen Sie, wie das Bedienfeld `personaldetails` beim Klicken auf die Schaltfläche `Next` validiert wird. Falls alle Felder innerhalb der `personaldetails` validiert werden, wird das Bedienfeld `feedback` angezeigt.

![Festlegen der Vorschau für das Eigenschaftsformular ](/help/forms/assets/set-property-form-preview.png)

Wenn Fehler in den Feldern des Bedienfelds `personaldetails` vorhanden sind, werden sie beim Klicken auf die Schaltfläche `Next` auf Feldebene angezeigt und das Bedienfeld `feedback` bleibt unsichtbar.

![Festlegen der Vorschau für das Eigenschaftsformular ](/help/forms/assets/set-property-panel.png)

## Überprüfen des Felds

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um das Feld mithilfe eines `Contact Us` Formulars zu validieren.

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben, um das Feld zu validieren.

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

In diesem Beispiel wird ein benutzerdefiniertes Überprüfungsmuster auf das Feld `contact` angewendet. Benutzende müssen eine Telefonnummer eingeben, die mit `10` gefolgt von `8` Ziffern beginnt. Wenn Benutzende eine Telefonnummer eingeben, die nicht mit `10` beginnt oder nicht genau `8` Ziffern enthält, wird beim Klicken auf die Schaltfläche eine Validierungsfehlermeldung angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/custom-function-validation-pattern.png)

Der nächste Schritt besteht darin, eine Regel für die Schaltfläche `Next` zu erstellen, die das Feld `contact` beim Klicken auf die Schaltfläche validiert.

![Überprüfungsmuster](/help/forms/assets/custom-function-validate.png)

Beziehen Sie sich auf die folgende Abbildung, die zeigt, dass eine Fehlermeldung auf Feldebene angezeigt wird, wenn Benutzende eine Telefonnummer eingeben, die nicht mit `10` beginnt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/custom-function-validate-error-message.png)

Wenn Benutzende eine gültige Telefonnummer eingeben und alle Felder im Bedienfeld `personaldetails` validiert worden sind, wird das Bedienfeld `feedback` auf dem Bildschirm angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/validate-form-preview-form.png)

## Zurücksetzen eines Bedienfelds

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um das Feld mithilfe eines `Contact Us` Formulars zurückzusetzen.

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben, um das Bedienfeld zurückzusetzen.

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

In diesem Beispiel wird das Bedienfeld `personaldetails` beim Klicken auf die Schaltfläche `Clear` zurückgesetzt. Als Nächstes erstellen Sie eine Regel für die Schaltfläche `Clear`, die das Bedienfeld bei einem Klick auf die Schaltfläche zurücksetzt.

![Schaltfläche „Löschen“](/help/forms/assets/custom-function-reset-field.png)

In der folgenden Abbildung sehen Sie, dass der Bereich `personaldetails` zurückgesetzt wird, wenn jemand auf die Schaltfläche `clear` klickt:

![Formular zurücksetzen](/help/forms/assets/custom-function-reset-form.png)

## So zeigen Sie eine benutzerdefinierte Meldung auf Feldebene an und markieren das Feld als ungültig

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um eine benutzerdefinierte Nachricht auf Feldebene anzuzeigen und das Feld mithilfe eines `Contact Us` Formulars als ungültig zu markieren.

Mit der Funktion `markFieldAsInvalid()` können Sie ein Feld als ungültig definieren und eine benutzerdefinierte Fehlermeldung auf Feldebene festlegen. Der Wert `fieldIdentifier` kann `fieldId`, `field qualifiedName` oder `field dataRef` lauten. Der Wert des Objekts namens `option` kann `{useId: true}`, `{useQualifiedName: true}` oder `{useDataRef: true}` lauten.
Folgende Syntax wird verwendet, um ein Feld als ungültig zu markieren und eine benutzerdefinierte Nachricht festzulegen:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) erläutert, um eine benutzerdefinierte Nachricht auf Feldebene zu aktivieren.

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

In diesem Beispiel wird eine benutzerdefinierte Meldung auf Feldebene angezeigt, wenn Benutzende weniger als 15 Zeichen in das Textfeld „Kommentare“ eingeben.

Der nächste Schritt besteht darin, eine Regel für das Feld `comments` zu erstellen:

![Feld als ungültig markieren](/help/forms/assets/custom-function-invalid-field.png)

Sehen Sie sich das Beispiel unten an, in dem dargestellt wird, wie die Eingabe von negativem Feedback in das Feld `comments` die Anzeige einer benutzerdefinierten Nachricht auf Feldebene auslöst:

![Feld als ungültige Formularvorschau markieren](/help/forms/assets/custom-function-invalidfield-form.png)

Wenn der/die Benutzende mehr als 15 Zeichen in das Textfeld „Kommentare“ eingibt, wird das Feld validiert und das Formular übermittelt:

![Feld als gültige Formularvorschau markieren](/help/forms/assets/custom-function-validfield-form.png)

## Senden geänderter Daten an den Server

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen mithilfe eines `Contact Us` Formulars Felder und globale Objekte verwenden, um bearbeitete Daten auf dem Server zu übermitteln.

Diese Codezeile
`globals.functions.submitForm(globals.functions.exportData(), false);` wird verwendet, um die Formulardaten nach der Bearbeitung zu senden.
* Das erste Argument sind die zu übermittelnden Daten.
* Das zweite Argument gibt an, ob das Formular vor der Übermittlung validiert werden soll. Es ist `optional` und standardmäßig auf `true` festgelegt.
* Das dritte Argument ist der `contentType` der Übermittlung, der ebenfalls optional ist und den Standardwert `multipart/form-data` hat. Die anderen Werte können `application/json` und `application/x-www-form-urlencoded` sein.

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben, um die bearbeiteten Daten an den Server zu senden:

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

Wenn jemand in diesem Beispiel das Textfeld `comments` leer lässt, wird beim Senden des Formulars an den Server `NA` gesendet.

Erstellen Sie jetzt eine Regel für die `Submit`-Schaltfläche, die Daten sendet:

![Daten senden](/help/forms/assets/custom-function-submit-data.png)

In der Abbildung unten finden Sie das `console window`, das zeigt, dass der Wert als `NA` an den Server gesendet wird, wenn jemand das Textfeld `comments` leer lässt:

![Daten im Konsolenfenster senden](/help/forms/assets/custom-function-submit-data-form.png)

Sie können auch das Konsolenfenster überprüfen, um die an den Server gesendeten Daten anzuzeigen:

![Daten im Konsolenfenster überprüfen](/help/forms/assets/custom-function-submit-data-console-data.png)

## Überschreiben der erfolgreichen Formularübermittlung und der Fehler-Handler

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen mithilfe eines `Contact Us` Formulars Feld- und globale Objekte verwenden, um Übermittlungs-Handler zu überschreiben.

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-features](/help/forms/custom-function-core-component-create-function.md) erläutert, um die Übermittlungs- oder Fehlermeldung für Formularübermittlungen anzupassen und die Formularübermittlungsmeldungen in einem modalen Feld anzuzeigen:

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

Wenn in diesem Beispiel der Benutzer die `customSubmitSuccessHandler` und `customSubmitErrorHandler` benutzerdefinierten Funktionen verwendet, werden die Erfolgs- und Fehlermeldungen in einem modalen Fenster angezeigt. Die JavaScript-`showModal(type, message)` wird verwendet, um ein modales Dialogfeld dynamisch zu erstellen und auf einem Bildschirm anzuzeigen.

Erstellen Sie jetzt eine Regel für die erfolgreiche Formularübermittlung:

![Formularübermittlung erfolgreich](/help/forms/assets/form-submission-success.png)

Anhand der folgenden Abbildung können Sie zeigen, dass bei erfolgreicher Übermittlung des Formulars die Erfolgsmeldung in einem modalen Fenster angezeigt wird:

![Erfolgsmeldung zur Formularübermittlung](/help/forms/assets/form-submission-success-message.png)

Erstellen wir analog dazu eine Regel für fehlgeschlagene Formularübermittlungen:

![Formularübermittlung schlägt fehl](/help/forms/assets/form-submission-fail.png)

Anhand der folgenden Abbildung können Sie zeigen, dass bei fehlgeschlagener Formularübermittlung die Fehlermeldung in einem modalen Fenster angezeigt wird:

![Meldung „Formularübermittlung fehlgeschlagen“](/help/forms/assets/form-submission-fail-message.png)

Um die erfolgreiche und fehlgeschlagene Übermittlung eines Formulars standardmäßig anzuzeigen, sind die Funktionen `Default submit Form Success Handler` und `Default submit Form Error Handler` standardmäßig verfügbar.

Falls der benutzerdefinierte Übermittlungs-Handler in bestehenden AEM-Projekten oder Formularen nicht wie erwartet funktioniert, lesen Sie den Abschnitt [Fehlerbehebung](#troubleshooting).

## Ausführen von Aktionen in einer bestimmten Instanz des wiederholbaren Bereichs

Regeln, die mit dem visuellen Regeleditor in einem wiederholbaren Bereich erstellt wurden, gelten für die letzte Instanz des wiederholbaren Bereichs. Zum Schreiben einer Regel für eine bestimmte Instanz des wiederholbaren Bereichs können wir eine benutzerdefinierte Funktion verwenden.

Erstellen wir ein anderes Formular, `Booking Form` Informationen über Reisende zu sammeln, die zu einem Ziel unterwegs sind. Ein Reisenden-Bedienfeld wird als wiederholbares Bedienfeld hinzugefügt, in dem der Benutzer mithilfe der Schaltfläche `Add Traveler` Details für 5 Reisende hinzufügen kann.

![Informationen für Reisende](/help/forms/assets/traveler-info-form.png)

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) erläutert, um Aktionen in einer bestimmten Instanz des wiederholbaren Bereichs durchzuführen, die nicht der letzten ist:

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

In diesem Beispiel führt die benutzerdefinierte Funktion `hidePanelInRepeatablePanel` eine Aktion in einer bestimmten Instanz des wiederholbaren Bereichs durch. Im obigen Code stellt `travelerinfo` den wiederholbaren Bereich dar. Der `repeatablePanel[1].traveler, {visible: false}`-Code blendet den Bereich in der zweiten Instanz des wiederholbaren Bereichs aus.

Fügen wir eine Schaltfläche mit der Bezeichnung `Hide` hinzu und fügen wir eine Regel hinzu, um die zweite Instanz eines wiederholbaren Bereichs auszublenden.

![Bereichsregel ausblenden](/help/forms/assets/custom-function-hidepanel-rule.png)

Anhand des folgenden Videos wird gezeigt, dass beim Klicken auf die `Hide` der Bereich in der zweiten wiederholbaren Instanz ausgeblendet wird:

>[!VIDEO](https://video.tv.adobe.com/v/3429554?quality=12&learn=on)

## Füllen Sie das Feld beim Laden des Formulars mit einem Wert vorab aus

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um Felder mithilfe eines `Booking Form` vorzubefüllen.

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) erläutert, um den vorausgefüllten Wert in ein Feld zu laden, wenn das Formular initialisiert wird:

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

Im oben genannten Code füllt die Funktion `testImportData` das Textfeld `Booking Amount` vorab aus, wenn das Formular geladen wird. Nehmen wir einmal an, dass das Buchungsformular die `10,000` des Mindestbuchungsbetrags erfordert.

Erstellen wir bei der Initialisierung des Formulars eine Regel, bei der der Wert im `Booking Amount` Textfeld beim Laden des Formulars mit einem angegebenen Wert vorausgefüllt wird:

![Datenregel importieren](/help/forms/assets/custom-function-import-data.png)

Der folgende Screenshot zeigt, dass beim Laden des Formulars der Wert im `Booking Amount` Textfeld mit einem angegebenen Wert vorausgefüllt ist:

![Datenregel-Formular importieren](/help/forms/assets/custom-function-prefill-form.png)

## Fokus auf das spezifische Feld legen

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um mithilfe eines `Booking Form` den Fokus auf ein bestimmtes Feld zu legen.

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) erläutert, um den Fokus auf das angegebene Feld zu legen, wenn auf die `Submit`-Schaltfläche geklickt wird:

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

Fügen wir der Schaltfläche `Submit` eine Regel hinzu, um den Fokus auf das Textfeld `Email ID` zu legen, wenn darauf geklickt wird:

![Fokusregel festlegen](/help/forms/assets/custom-function-set-focus.png)

Der folgende Screenshot zeigt, dass beim Klicken auf die Schaltfläche `Submit` der Fokus auf das Feld `Email ID` gelegt wird:

![Fokusregel festlegen](/help/forms/assets/custom-function-set-focus-form.png)

>[!NOTE]
>
> Sie können den optionalen `$focusOption`-Parameter verwenden, wenn Sie sich relativ zum `email` auf das nächste oder vorherige Feld konzentrieren möchten.

## Hinzufügen oder Löschen eines wiederholbaren Bereichs mithilfe der `dispatchEvent`

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen mithilfe von Feld- und globalen Objekten wiederholbare Bereiche mithilfe der `dispatchEvent`-Eigenschaft mithilfe eines `Booking Form` hinzufügen oder löschen.

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben, um einen Bereich hinzuzufügen, wenn mithilfe der `dispatchEvent`-Eigenschaft auf die Schaltfläche `Add Traveler` geklickt wird:

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

Fügen wir der Schaltfläche `Add Traveler` eine Regel hinzu, um den wiederholbaren Bereich hinzuzufügen, wenn auf ihn geklickt wird:

![Bereichsregel hinzufügen](/help/forms/assets/custom-function-add-panel.png)

Die folgende GIF-Datei veranschaulicht, dass beim Klicken auf die Schaltfläche `Add Traveler` der Bereich mithilfe der `dispatchEvent` hinzugefügt wird:

![Bedienfeld hinzufügen](/help/forms/assets/custom-function-add-panel.gif)

Fügen Sie auf ähnliche Weise die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](#create-custom-function) erläutert, um einen Bereich zu löschen, wenn mithilfe der `dispatchEvent`-Eigenschaft auf die Schaltfläche `Delete Traveler` geklickt wird:

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

Fügen wir der Schaltfläche `Delete Traveler` eine Regel hinzu, um den wiederholbaren Bereich beim Klicken zu löschen:

![Bereichsregel löschen](/help/forms/assets/custom-function-delete-panel.png)

Die nachstehende GIF-Datei zeigt, dass beim Klicken auf die Schaltfläche `Delete Traveler` das Reisenden-Bedienfeld mithilfe der Eigenschaft `dispatchEvent` gelöscht wird:

![Bedienfeld löschen](/help/forms/assets/custom-function-delete-panel.gif)

## Bekanntes Problem

* Benutzerdefinierte Funktionen unterstützen keine Literale für reguläre Ausdrücke in JavaScript. Die Verwendung von Regex-Literalen in einer benutzerdefinierten Funktion führt zu Fehlern während der Ausführung. Zum Beispiel:
  `const pattern = /^abc$/;`

  Um die Kompatibilität zu gewährleisten, verwenden Sie den RegExp-Konstruktor in den benutzerdefinierten Funktionen.

  `const pattern = new RegExp("^abc$");`
Refaktorieren Sie reguläre Ausdrücke so, dass der RegExp-Konstruktor verwendet wird, um eine konsistente und zuverlässige Ausführung zu gewährleisten.

## Fehlerbehebung

* Wenn der benutzerdefinierte Übermittlungs-Handler in bestehenden AEM-Projekten oder -Formularen nicht wie erwartet funktioniert, führen Sie die folgenden Schritte aus:
   * Stellen Sie sicher[ dass die Kernkomponentenversion auf Version 3.0.18 und höher aktualisiert ](https://github.com/adobe/aem-core-forms-components). Für bestehende AEM-Projekte und -Formulare müssen jedoch zusätzliche Schritte ausgeführt werden:

   * Für das AEM-Projekt sollte der Benutzer alle Instanzen von `submitForm('custom:submitSuccess', 'custom:submitError')` durch `submitForm()` ersetzen und das Projekt über die Cloud Manager-Pipeline bereitstellen.

   * Wenn die benutzerdefinierten Übermittlungs-Handler für vorhandene Formulare nicht richtig funktionieren, müssen Benutzende die Regel `submitForm` mithilfe des Regeleditors anhand der Schaltfläche **Senden** öffnen und speichern. Diese Aktion ersetzt im Formular die vorhandene Regel `submitForm('custom:submitSuccess', 'custom:submitError')` durch `submitForm()`.

## Siehe auch

{{see-also-rule-editor}}
