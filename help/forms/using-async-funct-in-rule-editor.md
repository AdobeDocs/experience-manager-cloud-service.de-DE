---
title: Wie werden asynchrone Funktionsaufrufe im Visual Rule Editor verwendet?
description: Asynchrone Funktionsaufrufe im Visual Rule Editor
feature: Adaptive Forms, Core Components
role: User, Developer
level: Beginner, Intermediate
source-git-commit: f6e1de0c2cc2c056b3bfcea6ce5d7aaed041f6f8
workflow-type: tm+mt
source-wordcount: '1437'
ht-degree: 2%

---


# Verwenden asynchroner Funktionen in einem adaptiven Formular basierend auf Kernkomponenten

Der [Regeleditor in Adaptive Forms](/help/forms/rule-editor-core-components.md) unterstützt asynchrone Funktionen, mit denen Sie Vorgänge integrieren und verwalten können, die auf externe Prozesse oder Datenabrufe warten müssen, ohne die Interaktion des Benutzers mit dem Formular zu unterbrechen.

## Welche Faktoren bestimmen die Verwendung asynchroner oder synchroner Funktionen?

Die effektive Verwaltung der Benutzerinteraktion ist für ein reibungsloses Erlebnis von entscheidender Bedeutung. Zwei gängige Vorgehensweisen zur Handhabung von Vorgängen sind synchrone und asynchrone Funktionen.

**Synchrone Funktionen** führen Aufgaben nacheinander aus, wodurch die Anwendung auf den Abschluss jedes Vorgangs wartet, bevor sie fortfährt. Dies kann zu Verzögerungen und einem weniger ansprechenden Benutzererlebnis führen, insbesondere wenn Aufgaben das Warten auf externe Ressourcen wie Datei-Uploads oder Datenabruf erfordern.

Angenommen, ein Benutzer lädt ein Bild hoch, das gesamte Formular wird angehalten und wartet auf den Abschluss des Uploads. Durch diese Pause kann der Benutzer nicht mit anderen Feldern interagieren, was zu Frustration und Verzögerungen führt. Während sie auf die Verarbeitung des Bildes warten, können alle eingegebenen Informationen verloren gehen, wenn sie wegnavigieren oder die Geduld verlieren, was das Erlebnis schwerfällig und ineffizient macht.

**Asynchrone Funktionen** ermöglichen dagegen die gleichzeitige Ausführung von Aufgaben. Das bedeutet, dass Benutzer weiterhin mit der Anwendung interagieren können, während Hintergrundprozesse ausgeführt werden. Asynchrone Vorgänge erhöhen die Reaktionsgeschwindigkeit, sodass Benutzer sofort Feedback erhalten und Interaktionen ohne Unterbrechungen aufrechterhalten können.

Umgekehrt können Benutzer mit einem asynchronen Ansatz Bilder im Hintergrund hochladen, während sie den Rest des Formulars nahtlos ausfüllen. Die Benutzeroberfläche bleibt responsiv und ermöglicht Echtzeitaktualisierungen und sofortiges Feedback im Zuge des Uploads. Sie verbessert die Benutzerinteraktion und sorgt für ein reibungsloses Erlebnis ohne Unterbrechungen.

![Asynchrone und synchrone Funktionen](/help/forms/assets/sync-async.png){align=center}

## Implementieren asynchroner Funktionen für adaptive Forms

Sie können die asynchronen Funktionen für Adaptive Forms mithilfe der folgenden Regeltypen im Regeleditor implementieren:

* [Asynchrone Funktionsaufrufe](#using-asynchronous-function-calls-in-the-visual-rule-editor)
* [Funktionsausgabe](#how-to-use-function-output-rule-type)

## Wie wird der Regeltyp Async-Funktionsaufruf verwendet?

<span class="preview"> Dies ist eine Vorabveröffentlichungsfunktion, auf die über unseren [Vorabveröffentlichungskanal](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/release-notes/prerelease.html?lang=de#new-features) zugegriffen werden kann. </span>

Sie können die [benutzerdefinierten Funktionen](/help/forms/custom-function-core-component-create-function.md) für asynchrone Vorgänge schreiben und die asynchronen Funktionen mithilfe des Regeltyps **[!UICONTROL Async Function Call]** im Regeleditor konfigurieren.

### Den Regeltyp für asynchrone Funktionsaufrufe anhand eines Anwendungsfalls untersuchen

Betrachten Sie ein Registrierungsformular auf einer Website, auf der Benutzer ein einmaliges Kennwort (OTP) eingeben. Das Bedienfeld zum Hinzufügen von Benutzerdetails wird erst nach Eingabe des richtigen OTP angezeigt. Wenn das OTP nicht korrekt ist, bleibt das Bedienfeld ausgeblendet und eine Fehlermeldung wird auf dem Bildschirm angezeigt.

![Login-form](/help/forms/assets/rule-editor-login-form.png) {width-50%}

Wenn der Benutzer in einem Registrierungsformular auf die Schaltfläche **Bestätigen** klickt, wird die Funktion `matchOTP()` asynchron aufgerufen, um den eingegebenen OTP zu überprüfen. Die Funktion `matchOTP()` wird als [benutzerdefinierte Funktion](/help/forms/custom-function-core-component-create-function.md) implementiert. Mithilfe des Regeltyps **[!UICONTROL Async Function Call]** im Regeleditor können Sie die Funktion `matchOTP()` im Regeleditor eines adaptiven Formulars konfigurieren. Sie können die Rückrufe für Erfolg und Fehler auch im Regeleditor implementieren.

Die folgende Abbildung zeigt die Schritte zum Verwenden des Regeltyps **[!UICONTROL Async Function Call]** zum Aufrufen asynchroner Funktionen für Adaptive Forms:

![Workflow zum Hinzufügen asynchroner Funktionen](/help/forms/assets/workflow-to-add-async-func.png){width=50%, align=center}

### 1. Schreiben Sie eine benutzerdefinierte Funktion für den asynchronen Vorgang in die JS-Datei

>[!NOTE]
>
> * Der Regeleditor eines Formulars zeigt nur Funktionen mit dem Rückgabetyp `Promise` an, wenn Sie den Regeltyp **Async Function Call** auswählen.
> * Informationen zum Erstellen einer benutzerdefinierten Funktion finden Sie im Artikel [Erstellen einer benutzerdefinierten Funktion für ein adaptives Formular basierend auf Kernkomponenten](/help/forms/custom-function-core-component-create-function.md).

Die Funktion `matchOTP()` wird als benutzerdefinierte Funktion implementiert. Der folgende Code wird in der JS-Datei der benutzerdefinierten Funktion hinzugefügt:

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

Der Code definiert eine Funktion &quot;`matchOTP()`&quot;, die ein Promise generiert, um ein einmaliges Kennwort (OTP) asynchron zu validieren. Es verwendet eine Funktion `asyncOperationForOTPMatch()` , um den OTP-Abgleichprozess zu simulieren. Die Funktion prüft, ob das bereitgestellte OTP gleich `111` ist. Wenn das eingegebene OTP korrekt ist, ruft es den Rückruf mit null für den Fehler auf und ein Objekt, das angibt, dass das OTP gültig ist `({'valid':'true'})`. Wenn das OTP nicht gültig ist, wird der Rückruf mit einem Fehlerobjekt `({'valid':'false'})` und null für das Ergebnis aufgerufen.

### 2. Konfigurieren Sie die asynchrone Funktion im Regeleditor

Führen Sie die folgenden Schritte aus, um die asynchrone Funktion im Regeleditor zu konfigurieren:

1. [Erstellen Sie eine Regel zur Verwendung der asynchronen Funktion mit dem Regeltyp Async-Funktionsaufruf](#21-create-a-rule-to-use-asynchronous-function-using-the-async-function-call-rule-type)
1. [Implementieren der Rückrufe für die asynchrone Funktion](#22-implement-the-callbacks-for-asynchronous-function)

#### 2.1 Erstellen Sie eine Regel zur Verwendung der asynchronen Funktion mithilfe des Regeltyps Async-Funktionsaufruf

Um eine Regel für die Verwendung eines asynchronen Vorgangs zu erstellen, führen Sie die folgenden Schritte mit dem Regeltyp **[!UICONTROL Async Function Call]** aus:

1. Öffnen Sie ein adaptives Formular im Authoring-Modus, wählen Sie eine Formularkomponente und dann **[!UICONTROL Regeleditor]** aus, um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.
1. Erstellen Sie eine Bedingung im Abschnitt **When** der Regel für einen Klick auf die Schaltfläche. Beispiel: **Wenn auf [Bestätigen]** geklickt wird.
1. Wählen Sie im Abschnitt **Dann** die Option **[!UICONTROL Async Function call]** aus der Dropdownliste **Aktion auswählen** aus.
Wenn Sie **[!UICONTROL Async Function call]** auswählen und die Funktionen mit dem Rückgabetyp `Promise` angezeigt werden.
1. Wählen Sie die asynchrone Funktion aus der Liste aus. Wählen Sie beispielsweise die Funktion `matchOTP()` aus und ihre Rückrufe werden als `Add success callback` und `add failure callback` angezeigt.
1. Wählen Sie nun die Bindungen **[!UICONTROL Eingabe]** aus. Wählen Sie beispielsweise **[!UICONTROL Eingabe]** als `Form Object` aus und vergleichen Sie sie mit dem Feld `OTP` .

Im folgenden Screenshot wird die Regel angezeigt:

![Regeltyp](/help/forms/assets/asyn-function-rule-type.png)

Jetzt können Sie mit der Implementierung der Rückrufe fortfahren: `Success` und `Failure` für die Funktion `matchOTP` .

#### 2.2 Implementieren der Rückrufe für die asynchrone Funktion

Implementieren Sie die Callback-Methoden für Erfolg und Fehler für die asynchrone Funktion mit dem visuellen Regeleditor.

**Erstellen einer Regel für die `Add Success callback` -Methode**

Erstellen wir eine Regel zum Anzeigen des Bereichs `userdetails` , wenn das OTP mit dem Wert `111` übereinstimmt.

1. Klicken Sie auf **[!UICONTROL Erfolgsrückruf hinzufügen]**.
1. Klicken Sie auf **[!UICONTROL Anweisung hinzufügen]** , um die Regel zu erstellen.
1. Erstellen Sie eine Bedingung im Abschnitt **When** der Regel.
1. Wählen Sie die **[!UICONTROL Funktionsausgabe]** > **[!UICONTROL Ereignisnutzlast abrufen]** aus.

   >[!NOTE]
   >
   > Die Funktion **[!UICONTROL Ereignis-Payload abrufen]** ruft Daten ab, die mit einem bestimmten Ereignis verknüpft sind, um Benutzerinteraktionen dynamisch zu verwalten.

1. Wählen Sie die entsprechenden Bindungen im Abschnitt **Eingabe** aus. Wählen Sie beispielsweise **[!UICONTROL String]** und geben Sie `valid` ein. Vergleichen Sie die eingegebene Zeichenfolge mit `true`.
1. Wählen Sie im Abschnitt **Dann** die Option **[!UICONTROL Anzeigen]** aus der Dropdownliste **Aktion auswählen** aus. Zeigen Sie beispielsweise das Bedienfeld &quot;`userdetails`&quot;an.
1. Klicken Sie auf **[!UICONTROL Anweisung hinzufügen]**.
1. Wählen Sie **[!UICONTROL Ausblenden]** aus der Dropdownliste **Aktion auswählen** aus. Blenden Sie beispielsweise das Textfeld `error message` aus.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Erfolgsaufruf](/help/forms/assets/rule-editor-success-callback.png){width=50%, height=50%}

Siehe Screenshot unten, in dem der Benutzer das OTP als `111` eingibt und das Bedienfeld `User Details` angezeigt wird, wenn auf die Schaltfläche `Confirm` geklickt wird.

![Erfolg](/help/forms/assets/success.gif)

**Erstellen einer Regel für die `Add Failure callback` -Methode**

Erstellen wir eine Regel, um eine Fehlermeldung anzuzeigen, wenn das OTP nicht mit dem Wert `111` übereinstimmt.

1. Klicken Sie auf **[!UICONTROL Rückruf für Fehler hinzufügen]**.

1. Klicken Sie auf **[!UICONTROL Anweisung hinzufügen]** , um die Regel zu erstellen.
1. Erstellen Sie eine Bedingung im Abschnitt **When** der Regel.
1. Wählen Sie die **[!UICONTROL Funktionsausgabe]** > **[!UICONTROL Ereignisnutzlast abrufen]** aus.
1. Wählen Sie die entsprechenden Bindungen im Abschnitt **Eingabe** aus. Wählen Sie beispielsweise **[!UICONTROL String]** und geben Sie `valid` ein. Vergleichen Sie die eingegebene Zeichenfolge mit `false`.
1. Wählen Sie im Abschnitt **Dann** die Option **[!UICONTROL Anzeigen]** aus der Dropdownliste **Aktion auswählen** aus. Zeigen Sie beispielsweise das Textfeld `error message` an.
1. Klicken Sie auf **[!UICONTROL Anweisung hinzufügen]**.
1. Wählen Sie **[!UICONTROL Ausblenden]** aus der Dropdownliste **Aktion auswählen** aus. Blenden Sie beispielsweise das Bedienfeld &quot;`userdetails`&quot;aus.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Rückruffunktion bei Fehler](/help/forms/assets/rule-editor-failure-callback.png){width=50%, height=50%}

Siehe Screenshot unten, in dem der Benutzer das OTP als `123` eingibt und die Fehlermeldung angezeigt wird, wenn auf die Schaltfläche `Confirm` geklickt wird.

![Fehler](/help/forms/assets/failure.gif)

Der folgende Screenshot zeigt die vollständige Regel für die Verwendung von **[!UICONTROL Async Function Call]** zur Implementierung einer asynchronen Funktion:

![Regel für asynchronen Funktionsaufruf](/help/forms/assets/rule-editor-async-callbacks.png)

Sie können die Rückrufe auch bearbeiten, indem Sie auf **[!UICONTROL Erfolgs-Rückruf bearbeiten]** und auf **[!UICONTROL Fehler-Rückruf bearbeiten]** klicken.

## Wie wird der Regeltyp &quot;Funktionsausgabe&quot;verwendet?

Sie können die asynchronen Funktionen auch indirekt mithilfe der synchronen Funktionen aufrufen. Die synchronen Funktionen werden mit dem Regeltyp **[!UICONTROL Funktionsausgabe]** im Regeleditor eines adaptiven Formulars ausgeführt.

Im folgenden Code erfahren Sie, wie Sie asynchrone Funktionen mithilfe des Regeltyps **[!UICONTROL Funktionsausgabe]** aufrufen:

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

![ Regel für asynchrone Funktion erstellen](/help/forms/assets/rule-for-async-funct.png){width=50%}

Im folgenden Screenshot des Konsolenfensters erfahren Sie, dass beim Klicken auf die Schaltfläche `Fetch` die benutzerdefinierte Funktion `callAsyncFunction` aufgerufen wird, die wiederum eine asynchrone Funktion `asyncFunction` aufruft. Inspect Sie das Konsolenfenster, um die Antwort auf die Schaltfläche anzuzeigen. Klicken Sie auf:

![Konsolenfenster](/help/forms/assets/async-custom-funct-console.png)

## Siehe auch

{{see-also-rule-editor}}