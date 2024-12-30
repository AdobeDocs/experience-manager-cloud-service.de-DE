---
title: Verwenden asynchroner Funktionsaufrufe im Visual Rule Editor
description: Asynchrone Funktionsaufrufe im Visual Rule Editor
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
exl-id: a240ba26-a6d8-4643-8acb-1d8812dac61f
source-git-commit: 4eb0feecbc5d0f090789bd3023e366ef4eb620db
workflow-type: tm+mt
source-wordcount: '1437'
ht-degree: 8%

---

# Verwenden asynchroner Funktionen in einem adaptiven Formular, basierend auf Kernkomponenten

Der [Regeleditor in Adaptive Forms](/help/forms/rule-editor-core-components.md) unterstützt asynchrone Funktionen, sodass Sie Vorgänge integrieren und verwalten können, für die das Warten auf externe Prozesse oder den Datenabruf erforderlich ist, ohne die Interaktion des Benutzers mit dem Formular zu unterbrechen.

## Welche Faktoren bestimmen die Verwendung asynchroner oder synchroner Funktionen?

Die effektive Verwaltung der Benutzerinteraktion ist für ein reibungsloses Erlebnis von entscheidender Bedeutung. Zwei gängige Ansätze für die Verarbeitung von Vorgängen sind synchrone und asynchrone Funktionen.

**Synchrone Funktionen** führen Aufgaben nacheinander aus, sodass die Anwendung auf den Abschluss jedes Vorgangs wartet, bevor der Vorgang fortgesetzt wird. Dies kann zu Verzögerungen und einem weniger ansprechenden Benutzererlebnis führen, insbesondere wenn Aufgaben das Warten auf externe Ressourcen erfordern, wie z. B. Datei-Uploads oder das Abrufen von Daten.

Angenommen, ein Benutzer lädt ein Bild hoch und das gesamte Formular wird angehalten, bis der Upload abgeschlossen ist. Durch diese Pause kann der Benutzer nicht mit anderen Feldern interagieren, was zu Frustration und Verzögerungen führt. Während sie warten, bis das Bild verarbeitet wird, können alle eingegebenen Informationen verloren gehen, wenn sie die Geduld verlieren oder wegnavigieren, was das Erlebnis umständlich und ineffizient macht.

**Asynchrone Funktionen** ermöglichen dagegen die gleichzeitige Ausführung von Aufgaben. Dies bedeutet, dass Benutzende während der Ausführung von Hintergrundprozessen weiterhin mit dem Programm interagieren können. Asynchrone Vorgänge verbessern die Reaktionsfähigkeit und ermöglichen es Benutzenden, sofortiges Feedback zu erhalten und die Interaktion ohne Unterbrechungen aufrechtzuerhalten.

Umgekehrt können Benutzer bei einem asynchronen Ansatz Bilder im Hintergrund hochladen und gleichzeitig den Rest des Formulars nahtlos ausfüllen. Die Benutzeroberfläche bleibt responsiv und ermöglicht Echtzeit-Aktualisierungen und sofortiges Feedback im Verlauf des Uploads. Es verbessert die Benutzerinteraktion und sorgt für ein reibungsloses Erlebnis ohne Unterbrechungen.

![Asynchrone und synchrone Funktionen](/help/forms/assets/sync-async.png){align=center}

## Implementieren asynchroner Funktionen für adaptive Forms

Sie können die asynchronen Funktionen für adaptive Forms mithilfe der folgenden Regeltypen im Regeleditor implementieren:

* [Aufruf der asynchronen Funktion](#using-asynchronous-function-calls-in-the-visual-rule-editor)
* [Funktionsausgabe](#how-to-use-function-output-rule-type)

## Wie wird der Regeltyp „Aufruf der asynchronen Funktion“ verwendet?

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, auf die über unseren [Vorabveröffentlichungskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features) zugegriffen werden kann. </span>

Sie können die [benutzerdefinierten Funktionen](/help/forms/custom-function-core-component-create-function.md) für asynchrone Vorgänge schreiben und die asynchronen Funktionen mithilfe des Regeltyps **[!UICONTROL Asynchroner Funktionsaufruf]** im Regeleditor konfigurieren.

### Erkunden des Regeltyps für asynchrone Funktionsaufrufe durch einen Anwendungsfall

Stellen Sie sich ein Registrierungsformular auf einer Website vor, auf der Benutzer ein Einmalkennwort (OTP) eingeben. Das Bedienfeld zum Hinzufügen von Benutzerdetails wird erst nach der Eingabe des richtigen OTP angezeigt. Wenn der OTP falsch ist, bleibt das Bedienfeld ausgeblendet und eine Fehlermeldung wird auf dem Bildschirm angezeigt.

![Login-form](/help/forms/assets/rule-editor-login-form.png) {width-50%}

Wenn der Benutzer in einem Registrierungsformular auf die Schaltfläche **Bestätigen** klickt, wird die `matchOTP()` asynchron aufgerufen, um das eingegebene OTP zu überprüfen. Die `matchOTP()` Funktion wird als [benutzerdefinierte Funktion“ ](/help/forms/custom-function-core-component-create-function.md). Mithilfe des Regeltyps **[!UICONTROL Async Function Call]** im Regeleditor können Sie die `matchOTP()` Funktion im Regeleditor eines adaptiven Formulars konfigurieren. Sie können die Callbacks für Erfolg und Fehler auch im Regeleditor implementieren.

Die folgende Abbildung zeigt die Schritte zum Verwenden des **[!UICONTROL Async Function Call]**-Regeltyps zum Aufrufen asynchroner Funktionen für adaptive Forms:

![Workflow zum Hinzufügen asynchroner Funktionen](/help/forms/assets/workflow-to-add-async-func.png){width=50%, align=center}

### 1. Schreiben Sie eine benutzerdefinierte Funktion für den asynchronen Vorgang in die JS-Datei

>[!NOTE]
>
> * Der Regeleditor eines Formulars zeigt nur Funktionen mit dem Rückgabetyp `Promise` an, wenn Sie den Regeltyp **Asynchroner Funktionsaufruf** auswählen.
> * Informationen zum Erstellen einer benutzerdefinierten Funktion finden Sie im Artikel mit dem Titel [Erstellen einer benutzerdefinierten Funktion für ein adaptives Formular basierend auf Kernkomponenten](/help/forms/custom-function-core-component-create-function.md).

Die `matchOTP()` Funktion wird als benutzerdefinierte Funktion implementiert. Der folgende Code wird in der JS-Datei der benutzerdefinierten Funktion hinzugefügt:

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

Der Code definiert eine `matchOTP()`, die eine Zusage zur asynchronen Validierung eines einmaligen Kennworts (OTP) generiert. Zur Simulation des OTP-Matching-Prozesses wird ein `asyncOperationForOTPMatch()` verwendet. Die Funktion prüft, ob der angegebene OTP gleich `111` ist. Wenn der eingegebene OTP korrekt ist, ruft er den Callback mit null für den Fehler und einem -Objekt auf, das angibt, dass der OTP gültig ist `({'valid':'true'})`. Wenn der OTP nicht gültig ist, ruft er den Callback mit einem Fehlerobjekt `({'valid':'false'})` und null für das Ergebnis auf.

### 2. Konfigurieren der asynchronen Funktion im Regeleditor

Führen Sie die folgenden Schritte aus, um die asynchrone Funktion im Regeleditor zu konfigurieren:

1. [Erstellen Sie eine Regel für die Verwendung einer asynchronen Funktion mithilfe des Regeltyps für den Aufruf der asynchronen Funktion .](#21-create-a-rule-to-use-asynchronous-function-using-the-async-function-call-rule-type)
1. [Implementieren der Callbacks für die asynchrone Funktion](#22-implement-the-callbacks-for-asynchronous-function)

#### 2.1 Erstellen Sie eine Regel für die Verwendung einer asynchronen Funktion mithilfe des Regeltyps für den Aufruf der asynchronen Funktion

Um eine Regel für die Verwendung eines asynchronen Vorgangs mit dem Regeltyp **[!UICONTROL Async Function Call]** zu erstellen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie ein adaptives Formular im Authoring-Modus, wählen Sie eine Formularkomponente und dann **[!UICONTROL Regeleditor]** aus, um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.
1. Erstellen Sie eine Bedingung im **Wenn**-Abschnitt der Regel für einen Klick auf eine Schaltfläche. Beispielsweise wird **Wenn[Bestätigen]** angeklickt.
1. Wählen Sie im **Dann**-Abschnitt **[!UICONTROL Asynchroner Funktionsaufruf]** aus der Dropdown-Liste **Aktion auswählen** aus.
Wenn Sie **[!UICONTROL asynchroner Funktionsaufruf]** auswählen, werden die Funktionen mit dem `Promise` Rückgabetyp angezeigt.
1. Wählen Sie die asynchrone Funktion in der Liste aus. Wählen Sie beispielsweise die Funktion `matchOTP()` und ihre Callbacks als `Add success callback` aus und `add failure callback` angezeigt.
1. Wählen Sie nun die **[!UICONTROL Input]**-Bindungen aus. Wählen Sie beispielsweise **[!UICONTROL Eingabe]** als `Form Object` aus und vergleichen Sie sie mit dem `OTP`.

Im folgenden Screenshot wird die Regel angezeigt:

![Regeltyp](/help/forms/assets/asyn-function-rule-type.png)

Jetzt können Sie mit der Implementierung der Callbacks fortfahren: `Success` und `Failure` für die `matchOTP`.

#### 2.2 Implementieren der Callbacks für die asynchrone Funktion

Implementieren Sie die Rückrufmethoden für Erfolg und Fehler für die asynchrone Funktion mit dem visuellen Regeleditor.

**Erstellen Sie eine Regel für `Add Success callback` Methode**

Erstellen wir eine Regel, um den `userdetails` anzuzeigen, wenn der OTP mit dem `111` übereinstimmt.

1. Klicken Sie **[!UICONTROL Erfolgs-Callback hinzufügen]**.
1. Klicken Sie **[!UICONTROL Anweisung hinzufügen]**, um die Regel zu erstellen.
1. Erstellen Sie eine Bedingung im Abschnitt **Wenn** der Regel.
1. Wählen Sie die **[!UICONTROL Funktionsausgabe]** > **[!UICONTROL Ereignis-Payload abrufen]**.

   >[!NOTE]
   >
   > Die Funktion **[!UICONTROL Ereignis-Payload abrufen]** ruft Daten ab, die mit einem bestimmten Ereignis verknüpft sind, um Benutzerinteraktionen dynamisch zu verwalten.

1. Wählen Sie die entsprechenden Bindungen im Abschnitt **Eingabe** aus. Wählen Sie beispielsweise **[!UICONTROL Zeichenfolge]** und geben Sie `valid` ein. Vergleichen Sie die eingegebene Zeichenfolge mit `true`.
1. Wählen Sie im **Dann**-Abschnitt **[!UICONTROL Anzeigen]** aus der Dropdown-Liste **Aktion auswählen** aus. Zeigen Sie beispielsweise das Bedienfeld `userdetails` an.
1. Klicken Sie **[!UICONTROL Anweisung hinzufügen]**.
1. Wählen **[!UICONTROL Ausblenden]** aus der **Aktion auswählen** Dropdown-Liste aus. Blenden Sie beispielsweise das `error message` Textfeld aus.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Erfolgsaufruf](/help/forms/assets/rule-editor-success-callback.png){width=50%, height=50%}

Im folgenden Screenshot sehen Sie, wie der Benutzer `111` in das OTP-Fenster eintritt. Das Bedienfeld &quot;`User Details`&quot; wird angezeigt, wenn auf die Schaltfläche &quot;`Confirm`&quot; geklickt wird.

![Erfolg](/help/forms/assets/success.gif)

**Erstellen Sie eine Regel für `Add Failure callback` Methode**

Erstellen wir eine Regel, um eine Fehlermeldung anzuzeigen, wenn der OTP nicht mit dem Wert `111` übereinstimmt.

1. Klicken Sie **[!UICONTROL Fehler-Callback hinzufügen]**.

1. Klicken Sie **[!UICONTROL Anweisung hinzufügen]**, um die Regel zu erstellen.
1. Erstellen Sie eine Bedingung im Abschnitt **Wenn** der Regel.
1. Wählen Sie die **[!UICONTROL Funktionsausgabe]** > **[!UICONTROL Ereignis-Payload abrufen]**.
1. Wählen Sie die entsprechenden Bindungen im Abschnitt **Eingabe** aus. Wählen Sie beispielsweise **[!UICONTROL Zeichenfolge]** und geben Sie `valid` ein. Vergleichen Sie die eingegebene Zeichenfolge mit `false`.
1. Wählen Sie im **Dann**-Abschnitt **[!UICONTROL Anzeigen]** aus der Dropdown-Liste **Aktion auswählen** aus. Zeigen Sie beispielsweise das `error message` Textfeld an.
1. Klicken Sie **[!UICONTROL Anweisung hinzufügen]**.
1. Wählen **[!UICONTROL Ausblenden]** aus der **Aktion auswählen** Dropdown-Liste aus. Blenden Sie beispielsweise das Bedienfeld `userdetails` aus.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Rückrufmethode für Fehler](/help/forms/assets/rule-editor-failure-callback.png){width=50%, height=50%}

Die Fehlermeldung wird angezeigt, wenn auf die Schaltfläche `Confirm` geklickt wird. Sie sehen im folgenden Screenshot, wo der Benutzer `123` in das OTP-Programm eintritt.

![Fehler](/help/forms/assets/failure.gif)

Im folgenden Screenshot wird die vollständige Regel für die Verwendung von **[!UICONTROL asynchroner Funktionsaufruf]** zum Implementieren einer asynchronen Funktion angezeigt:

![Regel für asynchronen Funktionsaufruf](/help/forms/assets/rule-editor-async-callbacks.png)

Sie können die Callbacks auch bearbeiten, indem Sie auf **[!UICONTROL Erfolgs-Callback bearbeiten]** und **[!UICONTROL Fehler-Callback bearbeiten]** klicken.

## Wie wird der Regeltyp Funktionsausgabe verwendet?

Sie können die asynchronen Funktionen auch indirekt über die synchronen Funktionen aufrufen. Die synchronen Funktionen werden mit dem Regeltyp **[!UICONTROL Funktionsausgabe]** im Regeleditor eines adaptiven Formulars ausgeführt.

Sehen Sie sich den unten stehenden Code an, um zu sehen, wie Sie asynchrone Funktionen mithilfe des Regeltyps **[!UICONTROL Funktionsausgabe]** aufrufen:

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

Fügen wir eine Schaltfläche hinzu und erstellen Sie eine Regel für die Schaltfläche, die beim Klicken auf eine Schaltfläche die asynchrone Funktion aufruft, damit sie funktioniert.

![Regel für asynchrone Funktion wird erstellt](/help/forms/assets/rule-for-async-funct.png){width=50%}

Im folgenden Screenshot des Konsolenfensters wird gezeigt, dass beim Klicken auf die Schaltfläche `Fetch` die benutzerdefinierte `callAsyncFunction` aufgerufen wird, die wiederum eine asynchrone `asyncFunction` aufruft. Inspect zeigt das Konsolenfenster an, in dem die Reaktion auf das Klicken auf die Schaltfläche angezeigt wird:

![Konsolenfenster](/help/forms/assets/async-custom-funct-console.png)

## Siehe auch

{{see-also-rule-editor}}
