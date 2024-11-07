---
title: In diesem Artikel werden verschiedene Anwendungsfälle für eine benutzerdefinierte Funktion in einem adaptiven Formular basierend auf Kernkomponenten beschrieben.
description: In diesem Artikel werden verschiedene Anwendungsfälle für eine benutzerdefinierte Funktion in einem adaptiven Formular basierend auf Kernkomponenten beschrieben. Benutzerdefinierte Funktionen werden im Regeleditor verwendet, um benutzerdefinierte Regeln für das Formular zu erstellen.
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: df92b91e-f3b0-4a08-bd40-e99edc9a50a5
source-git-commit: 88b9686a1ceec6729d9657d4bb6f458d9c411065
workflow-type: tm+mt
source-wordcount: '2134'
ht-degree: 0%

---

# Beispiele für die Entwicklung und Verwendung benutzerdefinierter Funktionen

Der Artikel enthält detaillierte Beispiele für benutzerdefinierte Funktionen für ein adaptives Formular, die auf Kernkomponenten basieren, und bietet wertvolle Einblicke in deren effektive Implementierung in verschiedenen Szenarien. Benutzerdefinierte Funktionen werden im Regeleditor eines AEM Forms verwendet, sodass Entwickler die Logik definieren und steuern können, die das Formularverhalten steuert.
In diesem Artikel werden verschiedene Implementierungen benutzerdefinierter Funktionen untersucht und gezeigt, wie sie verwendet werden können, um Formulare an bestimmte Anforderungen anzupassen und die Funktionalität insgesamt zu verbessern.

## Füllen der Dropdown-Listenoptionen mit benutzerdefinierten Funktionen

Der Regeleditor in Kernkomponenten unterstützt die Eigenschaft **Optionen festlegen** nicht zum dynamischen Füllen von Dropdown-Listenoptionen zur Laufzeit. Sie können jedoch Dropdown-Listenoptionen mit benutzerdefinierten Funktionen ausfüllen, mit denen Sie Optionen basierend auf einer bestimmten Logik abrufen können. Benutzerdefinierte Funktionen bieten mehr Flexibilität und Kontrolle darüber, wie und wann die Dropdown-Optionen aufgefüllt werden, wodurch das Benutzererlebnis verbessert wird.

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

Im obigen Code wird `setEnums` verwendet, um die Eigenschaft `enum` festzulegen, und `setEnumNames` wird verwendet, um die Eigenschaft `enumNames` der Dropdown-Liste festzulegen.

Erstellen wir eine Regel für die Schaltfläche `Next`, die den Wert der Dropdown-Listenoption festlegt, wenn der Benutzer auf die Schaltfläche `Next` klickt:

![Optionen für Dropdown-Listen](/help/forms/assets/drop-down-list-options.png)

In der folgenden Abbildung sehen Sie, wo die Optionen der Dropdown-Liste beim Klicken auf die Schaltfläche Anzeigen eingestellt sind:

![Dropdown-Optionen im Regeleditor](/help/forms/assets/drop-down-option-rule-editor.png)

## Anzeigen eines Bedienfelds mit der Regel `SetProperty`

Im Folgenden erfahren wir, wie benutzerdefinierte Funktionen mithilfe eines `Contact Us` -Formulars Feld- und globale Objekte verwenden.

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
> * Änderungen am Formular, die mit der Methode `setProperty` des Globals -Objekts vorgenommen werden, sind asynchron und werden bei der Ausführung der benutzerdefinierten Funktion nicht berücksichtigt.

In diesem Beispiel wird das Bedienfeld `personaldetails` durch Klicken auf die Schaltfläche überprüft. Wenn im Bedienfeld keine Fehler erkannt werden, wird ein weiteres Bedienfeld, das Bedienfeld `feedback`, beim Klicken auf die Schaltfläche angezeigt.

Erstellen wir eine Regel für die Schaltfläche `Next` , die das Bedienfeld `personaldetails` validiert und den Bereich `feedback` sichtbar macht, wenn der Benutzer auf die Schaltfläche `Next` klickt.

![Eigenschaft festlegen](/help/forms/assets/custom-function-set-property.png)

In der folgenden Abbildung sehen Sie, wo das Bedienfeld `personaldetails` beim Klicken auf die Schaltfläche `Next` validiert wird. Falls alle Felder innerhalb der `personaldetails` validiert werden, wird das Bedienfeld `feedback` angezeigt.

![Festlegen der Vorschau für die Eigenschaftsform ](/help/forms/assets/set-property-form-preview.png)

Wenn Fehler in den Feldern des Bereichs `personaldetails` vorhanden sind, werden sie beim Klicken auf die Schaltfläche `Next` auf Feldebene angezeigt und das Bedienfeld `feedback` bleibt unsichtbar.

![Festlegen der Vorschau für die Eigenschaftsform ](/help/forms/assets/set-property-panel.png)

## Validieren des Felds

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um das Feld mithilfe eines `Contact Us` -Formulars zu validieren.

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

In diesem Beispiel wird ein benutzerdefiniertes Überprüfungsmuster auf das Feld `contact` angewendet. Benutzer müssen eine Telefonnummer eingeben, die mit `10` gefolgt von `8` Ziffern beginnt. Wenn der Benutzer eine Telefonnummer eingibt, die nicht mit `10` beginnt oder mehr oder weniger als `8` Ziffern enthält, wird beim Klicken auf die Schaltfläche eine Überprüfungsfehlermeldung angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/custom-function-validation-pattern.png)

Der nächste Schritt besteht darin, eine Regel für die Schaltfläche `Next` zu erstellen, die das Feld `contact` beim Klicken auf die Schaltfläche validiert.

![Überprüfungsmuster](/help/forms/assets/custom-function-validate.png)

Beachten Sie die folgende Abbildung, um zu zeigen, dass eine Fehlermeldung auf Feldebene angezeigt wird, wenn der Benutzer eine Telefonnummer eingibt, die nicht mit `10` beginnt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/custom-function-validate-error-message.png)

Wenn der Benutzer eine gültige Telefonnummer eingibt und alle Felder im Bedienfeld `personaldetails` validiert werden, wird das Bedienfeld `feedback` auf dem Bildschirm angezeigt:

![Überprüfungsmuster für E-Mail-Adressen](/help/forms/assets/validate-form-preview-form.png)

## Zurücksetzen eines Bedienfelds

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um das Feld mithilfe eines `Contact Us` -Formulars zurückzusetzen.

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben, um den Bereich zurückzusetzen.

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

## So zeigen Sie eine benutzerdefinierte Nachricht auf Feldebene an und kennzeichnen das Feld als ungültig

Im Folgenden erfahren wir, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um eine benutzerdefinierte Meldung auf Feldebene anzuzeigen und das Feld mithilfe eines `Contact Us` -Formulars als ungültig zu kennzeichnen.

Mit der Funktion `markFieldAsInvalid()` können Sie ein Feld als ungültig definieren und eine benutzerdefinierte Fehlermeldung auf Feldebene festlegen. Der `fieldIdentifier` -Wert kann `fieldId`, `field qualifiedName` oder `field dataRef` sein. Der Wert des Objekts `option` kann `{useId: true}`, `{useQualifiedName: true}` oder `{useDataRef: true}` sein.
Die Syntax, mit der ein Feld als ungültig markiert und eine benutzerdefinierte Nachricht festgelegt wird, lautet:

* `globals.functions.markFieldAsInvalid(field.$id,"[custom message]",{useId: true});`
* `globals.functions.markFieldAsInvalid(field.$qualifiedName, "[custom message]", {useQualifiedName: true});`
* `globals.functions.markFieldAsInvalid(field.$dataRef, "[custom message]", {useDataRef: true});`

Fügen Sie den folgenden Code in der benutzerdefinierten Funktion hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben, um eine benutzerdefinierte Nachricht auf Feldebene zu aktivieren.

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

## Senden veränderter Daten an den Server

Im Folgenden erfahren wir, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um mithilfe eines `Contact Us` -Formulars auf dem Server bewegte Daten zu senden.

Die folgende Codezeile:
`globals.functions.submitForm(globals.functions.exportData(), false);` wird verwendet, um die Formulardaten nach der Bearbeitung zu senden.
* Das erste Argument sind die zu übermittelnden Daten.
* Das zweite Argument stellt dar, ob das Formular vor der Übermittlung validiert werden soll. Er ist `optional` und standardmäßig als `true` festgelegt.
* Das dritte Argument ist der `contentType` der Übermittlung, der ebenfalls optional ist, wobei der Standardwert `multipart/form-data` lautet. Die anderen Werte können `application/json` und `application/x-www-form-urlencoded` sein.

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

Wenn der Benutzer in diesem Beispiel das Textfeld `comments` leer lässt, wird der `NA` beim Senden des Formulars an den Server gesendet.

Erstellen Sie nun eine Regel für die `Submit` -Schaltfläche, mit der Daten gesendet werden:

![Daten übermitteln](/help/forms/assets/custom-function-submit-data.png)

In der Abbildung unten finden Sie die `console window` , die zeigt, dass der Wert als `NA` auf dem Server gesendet wird, wenn der Benutzer das Textfeld `comments` leer lässt:

![Senden von Daten im Konsolenfenster](/help/forms/assets/custom-function-submit-data-form.png)

Sie können auch das Konsolenfenster überprüfen, um die an den Server gesendeten Daten anzuzeigen:

![Inspect-Daten im Konsolenfenster](/help/forms/assets/custom-function-submit-data-console-data.png)

## Überschreiben des Erfolgs der Formularübermittlung und der Fehler-Handler

Im Folgenden erfahren Sie, wie benutzerdefinierte Funktionen mithilfe eines `Contact Us` -Formulars Feld- und globale Objekte verwenden, um Übermittlungs-Handler zu überschreiben.

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben, um die Übermittlung oder Fehlermeldung für Formularübermittlungen anzupassen und die Meldungen zur Formularübermittlung in einem modalen Feld anzuzeigen:

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

## Ausführen von Aktionen in einer bestimmten Instanz des wiederholbaren Bedienfelds

Regeln, die mit dem visuellen Regeleditor in einem wiederholbaren Bereich erstellt wurden, gelten für die letzte Instanz des wiederholbaren Bereichs. Um eine Regel für eine bestimmte Instanz des wiederholbaren Bereichs zu schreiben, können wir eine benutzerdefinierte Funktion verwenden.

Erstellen Sie ein anderes Formular als &quot;`Booking Form`&quot;, um Informationen über Reisende zu sammeln, die zu einem Ziel gehen. Ein Reisende-Bedienfeld wird als wiederholbares Bedienfeld hinzugefügt, in dem der Benutzer mithilfe der Schaltfläche `Add Traveler` Details für fünf Reisende hinzufügen kann.

![Informationen für Reisende](/help/forms/assets/traveler-info-form.png)

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) erläutert, um Aktionen in einer bestimmten Instanz des wiederholbaren Bereichs durchzuführen, die nicht der letzte ist:

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

## Füllen Sie das Feld beim Laden des Formulars mit einem Wert aus

Im Folgenden erfahren wir, wie benutzerdefinierte Funktionen mithilfe eines `Booking Form` Felder und globale Objekte zum Vorbefüllen von Feldern verwenden.

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

Im oben genannten Code füllt die Funktion `testImportData` beim Laden des Formulars das Textfeld `Booking Amount` im Voraus aus. Nehmen wir an, das Buchungsformular setzt voraus, dass der Mindestbuchungsbetrag `10,000` ist.

Erstellen wir eine Regel bei der Formularinitialisierung, bei der der Wert im Textfeld `Booking Amount` mit einem angegebenen Wert vorausgefüllt wird, wenn das Formular geladen wird:

![Datenregel importieren](/help/forms/assets/custom-function-import-data.png)

Im folgenden Screenshot wird gezeigt, dass beim Laden des Formulars der Wert im Textfeld `Booking Amount` mit einem angegebenen Wert vorausgefüllt ist:

![Formular für Datenregel importieren](/help/forms/assets/custom-function-prefill-form.png)

## Fokus auf bestimmtes Feld festlegen

Im Folgenden erfahren wir, wie benutzerdefinierte Funktionen mithilfe von Feld- und globalen Objekten mithilfe eines `Booking Form` den Fokus auf ein bestimmtes Feld legen.

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) erläutert, um den Fokus auf das angegebene Feld zu legen, wenn auf die Schaltfläche `Submit` geklickt wird:

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

## Hinzufügen oder Löschen wiederholbarer Bereiche mithilfe der Eigenschaft `dispatchEvent`

Im Folgenden erfahren wir, wie benutzerdefinierte Funktionen Felder und globale Objekte verwenden, um wiederholbare Bereiche mithilfe der Eigenschaft `dispatchEvent` mithilfe eines `Booking Form` hinzuzufügen oder zu löschen.

Fügen Sie die folgende Codezeile hinzu, wie im Abschnitt [create-custom-function](/help/forms/custom-function-core-component-create-function.md) beschrieben, um beim Klicken auf die Schaltfläche `Add Traveler` mit der Eigenschaft `dispatchEvent` einen Bereich hinzuzufügen:

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


## Fehlerbehebung

* Wenn der benutzerdefinierte Übermittlungshandler nicht wie erwartet in bestehenden AEM Projekten oder Formularen ausgeführt werden kann, führen Sie die folgenden Schritte aus:
   * Stellen Sie sicher, dass die Version der [Kernkomponenten auf Version 3.0.18 und höher](https://github.com/adobe/aem-core-forms-components) aktualisiert ist. Für bestehende AEM Projekte und Formulare sind jedoch weitere Schritte erforderlich:

   * Für das AEM Projekt sollte der Benutzer alle Instanzen von `submitForm('custom:submitSuccess', 'custom:submitError')` durch `submitForm()` ersetzen und das Projekt über die Cloud Manager-Pipeline bereitstellen.

   * Wenn die benutzerdefinierten Übermittlungs-Handler für vorhandene Formulare nicht ordnungsgemäß funktionieren, muss der Benutzer die Regel `submitForm` mithilfe des Regeleditors auf der Schaltfläche **Senden** öffnen und speichern. Diese Aktion ersetzt die vorhandene Regel von `submitForm('custom:submitSuccess', 'custom:submitError')` durch `submitForm()` im Formular.

## Siehe auch

{{see-also-rule-editor}}
