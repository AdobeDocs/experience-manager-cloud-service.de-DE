---
title: Verwenden asynchroner Funktionsaufrufe im visuellen Regeleditor
description: Asynchrone Funktionsaufrufe im visuellen Regeleditor
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: a240ba26-a6d8-4643-8acb-1d8812dac61f
source-git-commit: 2cae8bb1050bc4538f4645d9f064b227fb947d75
workflow-type: ht
source-wordcount: '1409'
ht-degree: 100%

---

# Verwenden asynchroner Funktionen in einem auf Kernkomponenten basierenden adaptiven Formular

Der [Regeleditor in adaptiven Formularen](/help/forms/rule-editor-core-components.md) unterstützt asynchrone Funktionen, sodass Sie Vorgänge integrieren und verwalten können, bei denen auf externe Prozesse oder Datenabrufe gewartet werden muss, ohne dabei die Interaktion der Benutzenden mit dem Formular zu unterbrechen.

## Welche Faktoren bestimmen die Verwendung asynchroner oder synchroner Funktionen?

Das effektive Verwalten von Benutzerinteraktionen ist für ein reibungsloses Erlebnis von entscheidender Bedeutung. Zwei gängige Ansätze zur Verarbeitung von Vorgängen sind synchrone und asynchrone Funktionen.

**Synchrone Funktionen** führen Aufgaben nacheinander aus, sodass die Anwendung auf den Abschluss jedes einzelnen Vorgangs wartet, bevor fortgefahren wird. Dies kann zu Verzögerungen und einem weniger ansprechenden Anwendererlebnis führen. Dies gilt insbesondere dann, wenn bei Aufgaben auf externe Ressourcen gewartet werden muss, z. B. bei Datei-Uploads oder Datenabrufen.

Angenommen, eine Person lädt ein Bild hoch und das gesamte Formular wird angehalten, bis der Upload abgeschlossen ist. Durch diese Pause kann die Person nicht mit anderen Feldern interagieren, was Frustration und Verzögerungen bedeutet. Während sie wartet, bis das Bild verarbeitet wird, können alle eingegebenen Informationen verloren gehen, wenn sie die Geduld verliert oder das Formular verlässt. So wird das Ganze zu einem umständlichen und ineffizienten Erlebnis.

**Asynchrone Funktionen** ermöglichen dagegen eine gleichzeitige Ausführung von Aufgaben. Dies bedeutet, dass Benutzende während der Ausführung von Hintergrundprozessen weiterhin mit der Anwendung interagieren können. Asynchrone Vorgänge verbessern die Reaktionsfähigkeit und ermöglichen es Benutzenden, sofortiges Feedback zu erhalten und die Interaktion ohne Unterbrechungen aufrechtzuerhalten.

Umgekehrt können Benutzende bei einem asynchronen Ansatz Bilder im Hintergrund hochladen und gleichzeitig den Rest des Formulars nahtlos ausfüllen. Die Benutzeroberfläche bleibt responsiv und lässt Echtzeitaktualisierungen und sofortiges Feedback während des Uploads zu. Die Benutzerinteraktion wird verbessert und ein reibungsloses Erlebnis ohne Unterbrechungen sichergestellt.

![Asynchrone und synchrone Funktionen](/help/forms/assets/sync-async.png){align=center}

## Implementieren asynchroner Funktionen für adaptive Formulare

Sie können die asynchronen Funktionen für adaptive Formulare mithilfe der folgenden Regeltypen im Regeleditor implementieren:

* [Asynchrone Funktionsaufrufe](#using-asynchronous-function-calls-in-the-visual-rule-editor)
* [Funktionsausgabe](#how-to-use-function-output-rule-type)

## Wie wird der Regeltyp für asynchrone Funktionsaufrufe verwendet?

Sie können die [benutzerdefinierten Funktionen](/help/forms/custom-function-core-component-create-function.md) für asynchrone Vorgänge schreiben und die asynchronen Funktionen mithilfe des Regeltyps für **[!UICONTROL asynchrone Funktionsaufrufe]** im Regeleditor konfigurieren.

### Erkunden des Regeltyps für asynchrone Funktionsaufrufe durch einen Anwendungsfall

Stellen Sie sich ein Registrierungsformular auf einer Website vor, auf der Benutzende ein Einmalpasswort (One-Time Password, OTP) eingeben. Das Panel zum Hinzufügen von Benutzerdetails wird erst nach der Eingabe des richtigen OTP angezeigt. Wenn das OTP falsch ist, bleibt das Panel ausgeblendet und es wird eine Fehlermeldung auf dem Bildschirm angezeigt.

![Anmeldeformular](/help/forms/assets/rule-editor-login-form.png) {width-50%}

Wenn die Benutzenden in einem Registrierungsformular auf die Schaltfläche **Bestätigen** klicken, wird die `matchOTP()`-Funktion asynchron aufgerufen, um das eingegebene OTP zu überprüfen. Die `matchOTP()`-Funktion wird als [benutzerdefinierte Funktion](/help/forms/custom-function-core-component-create-function.md) implementiert. Mithilfe des Regeltyps für **[!UICONTROL asynchrone Funktionsaufrufe]** im Regeleditor können Sie die `matchOTP()`-Funktion im Regeleditor eines adaptiven Formulars konfigurieren. Sie können die Rückrufe bei Erfolg und Fehler ebenfalls im Regeleditor implementieren.

Die folgende Abbildung zeigt die Schritte zum Verwenden des Regeltyps für **[!UICONTROL asynchrone Funktionsaufrufe]** in adaptiven Formularen:

![Workflow zum Hinzufügen asynchroner Funktionen](/help/forms/assets/workflow-to-add-async-func.png){width=50%, align=center}

### 1. Schreiben einer benutzerdefinierten Funktion für den asynchronen Vorgang in die JS-Datei

>[!NOTE]
>
> * Der Regeleditor eines Formulars zeigt nur Funktionen mit dem Rückgabetyp `Promise` an, wenn Sie den Regeltyp für **asynchrone Funktionsaufrufe** auswählen.
> * Informationen zum Erstellen einer benutzerdefinierten Funktion finden Sie im Artikel mit dem Titel [Erstellen einer benutzerdefinierten Funktion für ein auf Kernkomponenten basierendes adaptives Formular](/help/forms/custom-function-core-component-create-function.md).

Die `matchOTP()`-Funktion wird als benutzerdefinierte Funktion implementiert. Der folgende Code wird in der JS-Datei der benutzerdefinierten Funktion hinzugefügt:

```JavaScript
/**
 * generates the otp for success use case
 * @param {string} otp
 * @return {PROMISE}
 */
function matchOTP(otp) {
     return new Promise((resolve, reject) => {
        // Perform some asynchronous operation here
         asyncOperationForOTPMatch(otp, (error, result) => {
            if (error) {
                // On failure, call reject(error)
                reject(error);
            } else {
                // On success, call resolve(result)
                resolve(result);
            }
        });
    });
}

/**
 * generates the otp
 */
function asyncOperationForOTPMatch(otp, callback) {
    setTimeout(() => {
        if(otp === '111') {
            callback( null, {'valid':'true'});    
        } else {
            callback( {'valid':'false'}, null);
        }
    }, 1000);
}
```

Der Code definiert eine `matchOTP()`-Funktion, die eine Zusage zur asynchronen Validierung eines OTP generiert. Zur Simulation des Abgleichvorgangs für das OTP wird eine `asyncOperationForOTPMatch()`-Funktion verwendet. Die Funktion prüft, ob das angegebene OTP gleich `111` ist. Wenn das eingegebene OTP korrekt ist, erfolgt ein Rückruf mit null für den Fehler und einem Objekt `({'valid':'true'})`, das angibt, dass das OTP gültig ist. Wenn das OTP ungültig ist, erfolgt ein Rückruf mit einem Fehlerobjekt `({'valid':'false'})` und null für das Ergebnis.

### 2. Konfigurieren der asynchronen Funktion im Regeleditor

Führen Sie die folgenden Schritte aus, um die asynchrone Funktion im Regeleditor zu konfigurieren:

1. [Erstellen Sie eine Regel zur Verwendung einer asynchronen Funktion mithilfe des Regeltyps für asynchrone Funktionsaufrufe.](#21-create-a-rule-to-use-asynchronous-function-using-the-async-function-call-rule-type)
1. [Implementieren Sie die Rückrufe für die asynchrone Funktion.](#22-implement-the-callbacks-for-asynchronous-function)

#### 2.1 Erstellen einer Regel zur Verwendung einer asynchronen Funktion mithilfe des Regeltyps für asynchrone Funktionsaufrufe

Führen Sie die folgenden Schritte aus, um eine Regel zur Verwendung eines asynchronen Vorgangs mit dem Regeltyp für **[!UICONTROL asynchrone Funktionsaufrufe]** zu erstellen:

1. Öffnen Sie ein adaptives Formular im Authoring-Modus, wählen Sie eine Formularkomponente und dann **[!UICONTROL Regeleditor]** aus, um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.
1. Erstellen Sie eine Bedingung im Abschnitt **Wenn** der Regel für einen Klick auf eine Schaltfläche, z. B. **Wenn[Bestätigen]** ausgewählt wird.
1. Wählen Sie im Abschnitt **Dann** aus der Dropdown-Liste **Aktion auswählen** die Option für **[!UICONTROL asynchrone Funktionsaufrufe]** aus.
Wenn Sie die Option für **[!UICONTROL asynchrone Funktionsaufrufe]** auswählen, werden die Funktionen mit dem Rückgabetyp `Promise` angezeigt.
1. Wählen Sie die asynchrone Funktion aus der Liste aus. Wählen Sie beispielsweise die `matchOTP()`-Funktion und für ihre Rückrufe `Add success callback` aus und `add failure callback` wird angezeigt.
1. Wählen Sie nun die Bindungen vom Typ **[!UICONTROL Eingabe]** aus. Wählen Sie beispielsweise **[!UICONTROL Eingabe]** als `Form Object` aus und vergleichen Sie dies mit dem Feld `OTP`.

Im folgenden Screenshot wird die Regel angezeigt:

![Regeltyp](/help/forms/assets/asyn-function-rule-type.png)

Nun können Sie mit der Implementierung der Rückrufe fortfahren: `Success` und `Failure` für die `matchOTP`-Funktion.

#### 2.2 Implementieren der Rückrufe für die asynchrone Funktion

Implementieren Sie die Rückrufmethoden bei Erfolg und Fehler für die asynchrone Funktion mit dem visuellen Regeleditor.

**Erstellen einer Regel für die Methode `Add Success callback`**

Erstellen wir nun eine Regel, um das Panel `userdetails` anzuzeigen, wenn das OTP mit dem Wert `111` übereinstimmt.

1. Klicken Sie auf **[!UICONTROL Rückruf bei Erfolg hinzufügen]**.
1. Klicken Sie auf **[!UICONTROL Aussage hinzufügen]**, um die Regel zu erstellen.
1. Erstellen Sie eine Bedingung im Abschnitt **Wenn** der Regel. 
1. Wählen Sie **[!UICONTROL Funktionsausgabe]** > **[!UICONTROL Ereignis-Payload abrufen]** aus.

   >[!NOTE]
   >
   > Mit der Funktion **[!UICONTROL Ereignis-Payload abrufen]** werden Daten abgerufen, die mit einem bestimmten Ereignis verknüpft sind, um Benutzerinteraktionen dynamisch zu verwalten.

1. Wählen Sie die Datenbindungen aus dem Abschnitt **Eingabe** aus. Wählen Sie beispielsweise **[!UICONTROL Zeichenfolge]** aus und geben Sie `valid` ein. Vergleichen Sie die eingegebene Zeichenfolge mit `true`.
1. Wählen Sie im Abschnitt **Dann** aus der Dropdown-Liste **Aktion auswählen** die Option **[!UICONTROL Anzeigen]** aus. Zeigen Sie beispielsweise das Panel `userdetails` an.
1. Klicken Sie auf **[!UICONTROL Aussage hinzufügen]**. 
1. Wählen Sie aus der Dropdown-Liste **Aktion auswählen** die Option **[!UICONTROL Ausblenden]** aus. Blenden Sie beispielsweise das Textfeld `error message` aus.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Aufruf bei Erfolg](/help/forms/assets/rule-editor-success-callback.png){width=50%, height=50%}

Im folgenden Screenshot ist zu sehen, wie eine Person `111` als OTP eingibt. Das Panel `User Details` wird angezeigt, wenn auf die Schaltfläche `Confirm` geklickt wird.

![Erfolg](/help/forms/assets/success.gif)

**Erstellen einer Regel für die Methode `Add Failure callback`**

Erstellen wir nun eine Regel, um eine Fehlermeldung anzuzeigen, wenn das OTP nicht mit dem Wert `111` übereinstimmt.

1. Klicken Sie auf **[!UICONTROL Rückruf bei Fehler hinzufügen]**.

1. Klicken Sie auf **[!UICONTROL Aussage hinzufügen]**, um die Regel zu erstellen.
1. Erstellen Sie eine Bedingung im Abschnitt **Wenn** der Regel. 
1. Wählen Sie **[!UICONTROL Funktionsausgabe]** > **[!UICONTROL Ereignis-Payload abrufen]** aus.
1. Wählen Sie die Datenbindungen aus dem Abschnitt **Eingabe** aus. Wählen Sie beispielsweise **[!UICONTROL Zeichenfolge]** aus und geben Sie `valid` ein. Vergleichen Sie die eingegebene Zeichenfolge mit `false`.
1. Wählen Sie im Abschnitt **Dann** aus der Dropdown-Liste **Aktion auswählen** die Option **[!UICONTROL Anzeigen]** aus. Blenden Sie beispielsweise das Textfeld `error message` aus.
1. Klicken Sie auf **[!UICONTROL Aussage hinzufügen]**. 
1. Wählen Sie aus der Dropdown-Liste **Aktion auswählen** die Option **[!UICONTROL Ausblenden]** aus. Blenden Sie beispielsweise das Panel `userdetails` aus.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Rückrufmethode für Fehler](/help/forms/assets/rule-editor-failure-callback.png){width=50%, height=50%}

Im folgenden Screenshot ist zu sehen, wie eine Person `123` als OTP eingibt. Die Fehlermeldung wird angezeigt, wenn auf die Schaltfläche `Confirm` geklickt wird.

![Fehler](/help/forms/assets/failure.gif)

Der folgende Screenshot zeigt die vollständige Regel für die Verwendung eines **[!UICONTROL asynchronen Funktionsaufrufs]** zum Implementieren einer asynchronen Funktion:

![Regel für asynchronen Funktionsaufruf](/help/forms/assets/rule-editor-async-callbacks.png)

Sie können die Rückrufe auch bearbeiten, indem Sie auf **[!UICONTROL Rückruf bei Erfolg bearbeiten]** und **[!UICONTROL Rückruf bei Fehler bearbeiten]** klicken.

## Wie wird der Regeltyp für die Funktionsausgabe verwendet?

Sie können die asynchronen Funktionen auch indirekt über die synchronen Funktionen aufrufen. Die synchronen Funktionen werden mit dem Regeltyp für die **[!UICONTROL Funktionsausgabe]** im Regeleditor eines adaptiven Formulars ausgeführt.

Sehen Sie sich den folgenden Code an, um zu erfahren, wie Sie asynchrone Funktionen mit dem Regeltyp für die **[!UICONTROL Funktionsausgabe]** aufrufen können:

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

Im obigen Beispiel ist die Funktion „asyncFunction“ eine `asynchronous function`. Sie führt einen asynchronen Vorgang durch, indem eine `GET`-Anfrage an `https://petstore.swagger.io/v2/store/inventory` gesendet wird. Sie wartet mit `await` auf die Antwort, analysiert den Antworttext mithilfe der `response.json()` als JSON und gibt dann die Daten zurück. Die Funktion `callAsyncFunction` ist eine synchrone benutzerdefinierte Funktion, die die Funktion `asyncFunction` aufruft und die Antwortdaten in der Konsole anzeigt. Obwohl die Funktion `callAsyncFunction` synchron ist, ruft sie die asynchrone Funktion „asyncFunction“ auf und verarbeitet ihr Ergebnis mit den Anweisungen `then` und `catch`.

Um ihre Funktionsweise zu sehen, fügen wir eine Schaltfläche hinzu und erstellen eine Regel für die Schaltfläche, die die asynchrone Funktion bei einem Klick auf eine Schaltfläche aufruft.

![Erstellen einer Regel für eine asynchrone Funktion](/help/forms/assets/rule-for-async-funct.png){width=50%}

Im Screenshot des Konsolenfensters ist zu sehen, dass beim Klicken auf die Schaltfläche `Fetch` die benutzerdefinierte Funktion `callAsyncFunction` aufgerufen wird, die wiederum die asynchrone Funktion `asyncFunction` aufruft. Inspizieren Sie das Konsolenfenster, um die Antwort anzusehen, wenn Sie auf die Schaltfläche klicken:

![Konsolenfenster](/help/forms/assets/async-custom-funct-console.png)

## Siehe auch

{{see-also-rule-editor}}
