---
title: Hinzufügen benutzerdefinierter Fehler-Handler in Adaptive Forms für AEM Adaptive Forms
seo-title: Error Handlers in Adaptive Forms for AEM Adaptive Forms
description: AEM Forms bietet vordefinierte Erfolgs- und Fehler-Handler für ein Formular mit dem REST-Endpunkt, der zum Aufrufen eines externen Dienstes konfiguriert wurde. Sie können einen Standard-Fehler-Handler sowie einen benutzerdefinierten Fehler-Handler in einem AEM adaptiven Formular hinzufügen.
seo-description: Error handler function and Rule Editor in Adaptive Forms helps you to effectively manage and customize error handling. You can add a default error handler as well as custom error handler in an AEM Adaptive Form.
keywords: Fügen Sie einen benutzerdefinierten Fehler-Handler hinzu, fügen Sie einen Standard-Fehler-Handler hinzu, fügen Sie einen Fehler-Handler zum Formular hinzu, verwenden Sie den invoke-Dienst des Regeleditors, um einen benutzerdefinierten Fehler-Handler hinzuzufügen, konfigurieren Sie den Regeleditor, um einen benutzerdefinierten Fehler-Handler hinzuzufügen, fügen Sie mithilfe des Regeleditors einen benutzerdefinierten Fehler-Handler hinzu.
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms
source-git-commit: 66c7b30b8b66bc86d7b83e57e02ed61d426553a2
workflow-type: tm+mt
source-wordcount: '1979'
ht-degree: 6%

---

# Fehler-Handler in Adaptive Forms {#error-handlers-in-adaptive-form}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html) |
| AEM as a Cloud Service | Dieser Artikel |

AEM Forms bietet vordefinierte Erfolgs- und Fehler-Handler für die Formularübermittlung. Es bietet außerdem Funktionen zum Anpassen von Fehler-Handler-Funktionen. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehlercodes aufrufen oder den Kunden darüber informieren, dass der Dienst ausgefallen ist. Handler sind clientseitige Funktionen, die basierend auf der Serverantwort ausgeführt werden. Wenn ein externer Dienst mithilfe von APIs aufgerufen wird, werden die Daten zur Validierung an den Server übertragen, der eine Antwort mit Informationen zum Erfolgs- oder Fehlerereignis für die Übermittlung an den Client zurückgibt. Die Informationen werden als Parameter an den relevanten Handler übergeben, um die Funktion auszuführen. Ein Fehler-Handler hilft bei der Verwaltung und Anzeige von Fehlern oder aufgetretenen Validierungsproblemen.

![Workflow für Fehler-Handler, um zu verstehen, wie Sie benutzerdefinierten Fehler-Handler in Formularen hinzufügen](/help/forms/assets/error-handler-workflow.png)

Das adaptive Formular validiert die Eingaben, die Sie in Feldern bereitstellen, basierend auf voreingestellten Validierungskriterien und prüft, ob verschiedene Fehler vom REST-Endpunkt zurückgegeben werden, der zum Aufrufen eines externen Dienstes konfiguriert ist. Sie können die Validierungskriterien auf Grundlage der Datenquelle festlegen, die Sie mit dem adaptiven Formular verwenden. Wenn Sie beispielsweise RESTful-Web-Services als Datenquelle verwenden, können Sie die Validierungskriterien in einer Swagger-Definitionsdatei definieren.

Wenn die Eingabewerte die Validierungskriterien erfüllen und die Werte an die Datenquelle gesendet werden, zeigt das adaptive Formular eine Fehlermeldung mit einem Fehler-Handler an. Ähnlich wie dieser Ansatz integriert sich Adaptive Forms in benutzerdefinierte Fehler-Handler, um Datenvalidierungen durchzuführen. Wenn die Eingabewerte die Validierungskriterien nicht erfüllen, werden die Fehlermeldungen auf Feldebene im adaptiven Formular angezeigt. Dies tritt auf, wenn die vom Server zurückgegebene Validierungsfehlermeldung im standardmäßigen Nachrichtenformat vorliegt.


## Verwendung von Fehler-Handlern {#uses-of-error-handler}

Fehlerhandler werden für verschiedene Zwecke verwendet. Einige der Verwendungen von Fehler-Handler-Funktionen sind unten aufgeführt:
* **Validierung durchführen**: Die Fehlerbehebung beginnt mit der Validierung von Benutzereingaben anhand vordefinierter Regeln oder Kriterien. Wenn Benutzer ein adaptives Formular ausfüllen, validiert der Fehler-Handler die Eingabe, um sicherzustellen, dass sie das erforderliche Format, die Länge oder andere Einschränkungen erfüllt.

* **Echtzeit-Feedback geben**: Wenn ein Fehler erkannt wird, zeigt der Fehler-Handler dem Benutzer sofortiges Feedback an, z. B. Inline-Fehlermeldungen unter den entsprechenden Formularfeldern. Dieses Feedback hilft Benutzern, Fehler zu identifizieren und zu korrigieren, ohne das Formular senden und auf eine Antwort warten zu müssen.


* **Fehlermeldungen anzeigen**: Wenn bei der Übermittlung eines adaptiven Formulars ein Überprüfungsfehler auftritt, zeigt der Fehler-Handler eine entsprechende Fehlermeldung an. Die Fehlermeldungen sollten klar, kurz und deutlich die spezifischen Felder sein, die beachtet werden müssen.

* **markiert das fehlerhafte Feld**: Um die Aufmerksamkeit des Benutzers auf bestimmte falsche Felder zu lenken, hebt der Fehler-Handler die entsprechenden Felder hervor oder unterscheidet sie visuell. Dies geschieht durch Ändern der Hintergrundfarbe, Hinzufügen eines Symbols oder Rahmens oder eines anderen visuellen Hinweises, der Benutzern beim schnellen Auffinden und Beheben der Fehler hilft.


## Fehler-/Fehlerreaktionsformat {#failure-response-format}

Ein adaptives Formular zeigt die Fehler auf Feldebene an, wenn die Fehlermeldungen zur Servervalidierung im folgenden Standardformat vorliegen.
Der folgende Code veranschaulicht die vorhandene Fehlerreaktionsstruktur:

```javascript
   {
    errorCausedBy : "SERVER_SIDE_VALIDATION/SERVICE_INVOCATION_FAILURE"
    errors : [
        {
             somExpression  : <somexpr>
             errorMessage / errorMessages : <validationMsg> / [<validationMsg>, <validationMsg>]
        }
    ]
    originCode : <target error Code>
    originMessage : <unstructured error message returned by service>
}
```


Dabei gilt:

* `errorCausedBy` beschreibt den Grund für das Fehlschlagen.
* `errors` geben den SOM-Ausdruck der Felder an, die die Überprüfungskriterien nicht erfüllt haben, zusammen mit der Validierungsfehlermeldung.
* `originCode` -Feld von AEM hinzugefügt wurde und den vom externen Dienst zurückgegebenen HTTP-Status-Code enthält.
* `originMessage` -Feld von AEM hinzugefügt wurde und die vom externen Dienst zurückgegebenen rohen Fehlerdaten enthält.

Mit den Verbesserungen der Funktionen und nachfolgenden Aktualisierungen der Versionen von AEM Forms hat sich die vorhandene Fehlerreaktionsstruktur auf Grundlage von RFC7807 in ein neues Format geändert, das abwärtskompatibel mit der vorhandenen Fehlerreaktionsstruktur ist:

```javascript
    {
        "type": "SERVER_SIDE_VALIDATION/FORM_SUBMISSION/SERVICE_INVOCATION/FAILURE/VALIDATION_ERROR", (required)
        "title": "Server side validation failed/Third party service invocation failed", (optional)
        "detail": "", (optional)
        "instance": "", (optional)
        "validationErrors" : [ (required)
            {
                "fieldName":"<SOM expression of the field whose data sent is invalid>",
                "dataRef":<JSONPath (or XPath) of the data element which is invalid>
                "details": ["Error Message(s) for the field"] (required)
    
            }
        ],
        "originCode": <Origin http status code>, (optional - in case of SERVER_SIDE_VALIDATION)
        "originMessage" : "<unstructured error message returned by service>" (optional - in case of SERVER_SIDE_VALIDATION)
    }
```


>[!NOTE]
>
> * Stellen Sie sicher, dass die Struktur der Fehlerantwort Folgendes enthält: **fieldName** oder **dataRef**.
> * Stellen Sie sicher, dass **ContentType** -Kopfzeile ist **application/problem+json**.

Dabei gilt:
* `type (required)` gibt den Fehlertyp an. Es kann sich um einen der folgenden Werte handeln:
   * `SERVER_SIDE_VALIDATION` weist auf einen Fehler aufgrund der serverseitigen Validierung hin.
   * `FORM_SUBMISSION` weist auf einen Fehler während der Formularübermittlung hin
   * `SERVICE_INVOCATION` weist auf einen Fehler während eines Drittanbieter-Dienstaufrufs hin.
   * `FAILURE` zeigt einen allgemeinen Fehler an.
   * `VALIDATION_ERROR` weist auf einen Fehler aufgrund eines Validierungsfehlers hin.

* `title (optional)` gibt einen Titel oder eine kurze Beschreibung des Fehlschlagens ein.
* `detail (optional)` enthält bei Bedarf weitere Details zum Fehler.
* `instance (optional)` stellt eine Instanz oder einen Bezeichner dar, die bzw. der mit dem Fehler verknüpft ist, und hilft beim Tracking oder Identifizieren des spezifischen Vorkommens des Fehlers.
* `validationErrors (required)` enthält Informationen zu Validierungsfehlern. Er enthält die folgenden Felder:
   * `fieldname` erwähnt den SOM-Ausdruck der Felder, die die Validierungskriterien nicht erfüllt haben.
   * `dataRef` stellt den JSON-Pfad oder XPath der Felder dar, bei denen die Überprüfung fehlgeschlagen ist.
   * `details` enthalten die Validierungsfehlermeldung mit dem fehlerhaften Feld.
* `originCode (optional)` von AEM hinzugefügtes Feld enthält den vom externen Dienst zurückgegebenen HTTP-Status-Code
* `originMessage (optional)` -Feld von AEM hinzugefügt wurde und die vom externen Dienst zurückgegebenen rohen Fehlerdaten enthält.

### Beispiel für ein Antwortformat für Fehler {#sample-error-response-format}

Einige der Optionen zur Anzeige der Fehlerantworten sind:

+++

+++  Basiert auf dem Feldnamen des adaptiven Formulars


* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

      &quot;javascript
      {
      &quot;type&quot;: &quot;VALIDATION_ERROR&quot;,
      &quot;validationErrors&quot;: [
      {
      &quot;fieldName&quot;: &quot;guide[0].guide1[0].guideRootPanel[0].textbox1686647736683[0]&quot;,
      &quot;dataRef&quot;: &quot;&quot;,
      &quot;details&quot;: [
      &quot;Ungültige ID angegeben. Der angegebene Wert ist nicht korrekt!&quot;
      ]
      }
      ]}
      &quot;
  
  Sie können den SOM-Ausdruck eines beliebigen Felds in einem adaptiven Formular anzeigen, indem Sie auf das Feld tippen und die **[!UICONTROL SOM-Ausdruck anzeigen]**.

  ![SOM-Ausdruck eines adaptiven Formularfelds zur Anzeige der Fehlerantwort im benutzerdefinierten Fehler-Handler](/help/forms/assets/custom-error-handler-somexpression.png)

+++


+++ Basierend auf der Datenreferenz für das adaptive Formular

* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
  {
      "type": "VALIDATION_ERROR",
      "validationErrors": [
      {
          "fieldName": "",
          "dataRef": "/Pet/id",
          "details": [
          "Invalid ID supplied. Provided value is not correct!"
          ]
          }
  ]}
  ```

  ![Datenreferenz eines adaptiven Formularfelds zur Anzeige der Fehlerantwort im benutzerdefinierten Fehler-Handler](/help/forms/assets/custom-errorhandler-dataref.png)

Sie können den Wert von dataRef im **[!UICONTROL Eigenschaften]** -Fenster einer Formularkomponente.


+++

## Hinzufügen eines Fehler-Handlers mit dem Regeleditor {#add-error-handler-using-rule-editor}

Verwenden der [Aufrufdienst des Regeleditors](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) -Aktion verwenden, definieren Sie die Validierungskriterien auf Grundlage der Datenquelle, die Sie mit dem adaptiven Formular verwenden. Wenn Sie RESTful-Webdienste als Datenquelle verwenden, können Sie die Validierungskriterien in einer Swagger-Definitionsdatei definieren. Durch die Verwendung der Funktionen für Fehler-Handler und des Regel-Editors in Adaptive Forms können Sie die Fehlerbehandlung effektiv verwalten und anpassen. Sie definieren die Bedingungen mithilfe des Regeleditors und konfigurieren die gewünschten Aktionen, die ausgeführt werden sollen, wenn die Regel ausgelöst wird. Adaptives Formular validiert die Eingaben, die Sie in Felder eingeben, basierend auf vordefinierten Validierungskriterien. Falls die Eingabewerte die Validierungskriterien nicht erfüllen, werden die Fehlermeldungen auf Feldebene in einem adaptiven Formular angezeigt.

>[!NOTE]
>
> * Um Fehler-Handler mit der Aktion &quot;Aufrufdienst&quot;des Regeleditors zu verwenden, konfigurieren Sie Adaptive Forms mit einem Formulardatenmodell.
> * Standardmäßig wird ein standardmäßiger Fehler-Handler bereitgestellt, um Fehlermeldungen in Feldern anzuzeigen, wenn die Fehlerantwort im Standardschema enthalten ist. Der Standard-Fehler-Handler kann auch den benutzerdefinierten Fehler-Handler aufrufen, wenn die Fehlerantwort nicht dem Standardschema entspricht.

<!-- 
Using Rule Editor, you can:
* [Add default error handler function](#add-default-errror-handler)
* [Add custom error handler function](#add-custom-errror-handler)


### Add default error handler function {#add-default-errror-handler}

A default error handler is supported by default to display error messages on fields if the error response is in standard schema or in server-side validation failure. 
To understand how to use a default error handler using the [Rule Editor's Invoke Service](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) action, take an example of a simple Adaptive Form with two fields, **Pet ID** and **Pet Name** and use a default error handler at the **Pet ID** field to check for various errors returned by the REST endpoint configured to invoke an external service, for example, `200 - OK`,`404 - Not Found`, `400 - Bad Request`. To add a default error handler using the Rule Editor's Invoke Service action, execute the following steps:

1. Open an Adaptive Form in authoring mode, select a form component and tap **[!UICONTROL Rule Editor]** to open the rule editor.
1. Tap **[!UICONTROL Create]**.
1. Create a condition in the **When** section of the rule. For example, **When[Name of Pet ID field]** is changed. Select is changed from the **Select State** drop-down list.
1. In the **Then** section, select **[!UICONTROL Invoke Service]** from the **Select Action** drop-down list.
1. Select a **Post service** and its corresponding data bindings from the **Input** section. For example, to validate **Pet ID**, select a **Post service** as **GET /pet/{petId}** and select **Pet ID** in the **Input** section.
1. Select the data bindings from the **Output** section. Select **Pet Name** in the **Output** section.
1. Select **[!UICONTROL Default Error Handler]** from the **Error Handler** section. 
1. Click **[!UICONTROL Done]**.

 ![add a default error handler for a field validation checks in a form](/help/forms/assets/default-error-handler.png)

As a result of this rule, the values you enter for **Pet ID** checks validation for **Pet Name** using external service invoked by REST endpoint. If the validation criteria based on the data source fail, the error messages are displayed at the field level.

 ![display the default error message when you add a default error handler in a form to handle error responses](/help/forms/assets/default-error-message.png)

-->

### Hinzufügen einer benutzerdefinierten Fehler-Handler-Funktion {#add-custom-errror-handler}

Sie können eine benutzerdefinierte Fehler-Handler-Funktion hinzufügen, um einige der folgenden Aktionen auszuführen:
* Verarbeiten Sie Fehlerantworten, die nicht standardmäßige oder standardmäßige Fehlerantworten verwenden. Beachten Sie, dass diese nicht standardmäßigen Fehlerantworten nicht mit dem [Standardschema von Fehlerantworten](#failure-response-format).
* Analytics-Ereignisse an beliebige Analytics-Plattformen senden. Beispiel: Adobe Analytics.
* modales Dialogfeld mit Fehlermeldungen anzeigen.

Zusätzlich zu den genannten Aktionen können die benutzerdefinierten Fehler-Handler verwendet werden, um benutzerdefinierte Funktionen auszuführen, die bestimmten Benutzeranforderungen entsprechen.

Der benutzerdefinierte Fehler-Handler ist eine Funktion (Client-Bibliothek), die auf von einem externen Dienst zurückgegebene Fehler reagiert und Endbenutzern eine benutzerdefinierte Antwort bereitstellt. Jede Client-Bibliothek mit Anmerkungen `@errorHandler` wird als benutzerdefinierte Fehler-Handler-Funktion betrachtet. Diese Anmerkung hilft bei der Identifizierung der Fehler-Handler-Funktion, die in der `.js` -Datei.
Informationen zum Erstellen und Verwenden eines benutzerdefinierten Fehler-Handlers mit dem [Aufrufdienst des Regeleditors](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=en#invoke) -Aktion verwenden. Nehmen wir ein Beispiel für ein adaptives Formular mit zwei Feldern. **Haustier-ID** und **Heimtiername** und verwenden Sie einen benutzerdefinierten Fehler-Handler am **Haustier-ID** -Feld zur Überprüfung auf verschiedene Fehler, die vom REST-Endpunkt zurückgegeben werden, der zum Aufrufen eines externen Dienstes konfiguriert ist, z. B. `200 - OK`,`404 - Not Found`, `400 - Bad Request`.

Um einen benutzerdefinierten Fehler-Handler in einem adaptiven Formular hinzuzufügen und zu verwenden, führen Sie die folgenden Schritte aus:
1. [Benutzerdefinierten Fehler-Handler erstellen](#create-custom-error-message)
1. [Verwenden des Regeleditors zum Konfigurieren des benutzerdefinierten Fehler-Handlers](#use-custom-error-handler)

#### 1. Erstellen Sie einen benutzerdefinierten Fehler-Handler. {#create-custom-error-message}

Um eine benutzerdefinierte Fehlerfunktion zu erstellen, führen Sie die folgenden Schritte aus:
1. [Klonen Sie Ihr as a Cloud Service AEM Forms-Repository.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#accessing-git).
1. Navigieren Sie zu `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/`.
1. Erstellen Sie einen Ordner mit dem Namen `js`.
1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js`.
1. Fügen Sie eine JavaScript-Datei hinzu, z. B. `function.js`. Die Datei enthält den Code für den benutzerdefinierten Fehler-Handler.
Fügen wir den folgenden Code zur JavaScript-Datei hinzu, um die Antwort und die vom REST-Dienstendpunkt empfangenen Kopfzeilen in der Browserkonsole anzuzeigen.

       &quot;javascript
       /**
       * Benutzerdefinierter Fehler-Handler
       * @name customErrorHandler Benutzerdefinierte Fehler-Handler-Funktion
       * @errorHandler
       */
       function customErrorHandler(response, headers)
       {
       console.log(&quot;Custom Error Handler processing start..&quot;);
       console.log(&quot;response:&quot;+JSON.stringify(response));
       console.log(&quot;headers:&quot;+JSON.stringify(headers));
       console.log(&quot;Custom Error Handler processing end...&quot;);
       }
       &quot;
   
   <!--  To call the default error handler after the custom error handler, the following line of the sample code is used:
        `guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers) `-->
1. Speichern Sie die Datei `function.js`.
1. Navigieren Sie zum Ordner `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js`.
1. Fügen Sie eine Textdatei als `js.txt`. Die Datei enthält:

   ```javascript
       #base=js
       functions.js
   ```

1. Speichern Sie die Datei `js.txt`.

   >[!NOTE]
   >
   > Um mehr über das Erstellen benutzerdefinierter Funktionen zu erfahren, klicken Sie auf [benutzerdefinierte Funktionen im Regeleditor](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/add-rules-and-use-expressions-in-an-adaptive-form/rule-editor.html?lang=en#write-rules).

1. Fügen Sie die Änderungen mithilfe der folgenden Befehle in das Repository ein, übertragen Sie sie und übertragen Sie sie:

   ```javascript
       git add .
       git commit -a -m "Adding error handling files"
       git push
   ```

1. [Ausführen der Pipeline.](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline)

Sobald die Pipeline erfolgreich ausgeführt wurde, steht der benutzerdefinierte Fehler-Handler im Regeleditor für adaptive Formulare zur Verfügung. Jetzt erfahren Sie, wie Sie einen benutzerdefinierten Fehler-Handler mit dem Invoke-Dienst des Regeleditors in AEM Forms konfigurieren und verwenden.

#### 2. Verwenden Sie den Regeleditor, um den benutzerdefinierten Fehler-Handler zu konfigurieren. {#use-custom-error-handler}

So verwenden Sie einen benutzerdefinierten Fehler-Handler mit dem **[!UICONTROL Aufrufdienst des Regeleditors]** Aktion:

1. Öffnen Sie ein adaptives Formular im Authoring-Modus, wählen Sie eine Formularkomponente aus und tippen Sie auf **[!UICONTROL Regeleditor]** , um den Regeleditor zu öffnen.
1. Tippen Sie auf **[!UICONTROL Erstellen]**.
1. Definieren Sie eine Bedingung im Abschnitt **Wann** der Regel. Beispiel: Wenn **[Name des Felds &quot;Haustier-ID&quot;]** geändert wird, wählen Sie **geändert** von **Status auswählen** Dropdown-Liste.
1. Im Abschnitt **Dann** wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **Aktion auswählen.**
1. Wählen Sie eine **Post-Service** und die entsprechenden Datenbindungen der **Eingabe** Abschnitt. Beispiel: Zu validieren **Haustier-ID**, wählen Sie eine **Post-Service** as **GET /pet/{petId}** und wählen Sie **Haustier-ID** im **Eingabe** Abschnitt.
1. Wählen Sie die Datenbindungen aus der **Ausgabe** Abschnitt. Wählen Sie beispielsweise **Heimtiername** im **Ausgabe** Abschnitt.
1. Auswählen **[!UICONTROL Benutzerdefinierter Fehler-Handler]** von **[!UICONTROL Fehler-Handler]** Abschnitt.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Fügen Sie einen benutzerdefinierten Fehler-Handler in ein Formular ein, um Fehlerantworten zu verarbeiten](/help/forms/assets/custom-error-handler.png)


Aus dieser Regel ergeben sich die Werte, für die Sie **Haustier-ID** überprüft die Validierung für **Heimtiername** Verwendung des externen Dienstes, der vom REST-Endpunkt aufgerufen wurde. Wenn die auf der Datenquelle basierenden Validierungskriterien fehlschlagen, werden die Fehlermeldungen auf Feldebene angezeigt.


![Fügen Sie einen benutzerdefinierten Fehler-Handler in ein Formular ein, um Fehlerantworten zu verarbeiten](/help/forms/assets/custom-error-handler-message.png)

Öffnen Sie die Browser-Konsole und überprüfen Sie die Antwort und die Kopfzeile, die vom REST-Dienstendpunkt empfangen wurden, auf die Überprüfungsfehlermeldung.


Die benutzerdefinierte Fehler-Handler-Funktion ist für die Ausführung zusätzlicher Aktionen verantwortlich, z. B. für die Anzeige eines modalen Dialogfelds oder das Senden eines Analytics-Ereignisses basierend auf der Fehlerantwort. Eine benutzerdefinierte Fehler-Handler-Funktion bietet die Flexibilität, die Fehlerbehandlung an die spezifischen Benutzeranforderungen anzupassen.

<!-- 

## Configure Adaptive Form submission to add custom handlers {#configure-adaptive-form-submission}

If the server validation error message does not display in the standard format, you can enable asynchronous submission and add a custom error handler on Adaptive Form submission to convert the message into a standard format.

### Configure asynchronous Adaptive Form submission {#configure-asynchronous-adaptive-form-submission}

Before adding custom handler, you must configure the adaptive form for asynchronous submission. Execute the following steps:

1. In adaptive form authoring mode, select the Form Container object and tap ![adaptive form properties](assets/configure_icon.png) to open its properties.
1. In the **[!UICONTROL Submission]** properties section, enable **[!UICONTROL Use asynchronous submission]**.
1. Select **[!UICONTROL Revalidate on server]** to validate the input field values on server before submission.
1. Select the Submit Action:

    * Select **[!UICONTROL Submit using Form Data Model]** and select the appropriate data model, if you are using RESTful web service based [form data model](work-with-form-data-model.md) as the data source.
    * Select **[!UICONTROL Submit to REST Service endpoint]** and specify the **[!UICONTROL Redirect URL/Path]**, if you are using RESTful web services as the data source.

    ![adaptive form submission properties](assets/af_submission_properties.png)

1. Tap ![Save](assets/save_icon.png) to save the properties.

### Add custom error handler on Adaptive Form submission {#add-custom-error-handler-af-submission}

AEM Forms provides out-of-the-box success and error handlers for form submissions. Handlers are client-side functions that execute based on the server response. When an Adaptive Form is submitted, the data is transmitted to the server for validation, which returns a response to the client with information about the success or error event for the submission. The information is passed as parameters to the relevant handler to execute the function.

Execute the following steps to add custom error handler on Adaptive Form submission:

1. Open an Adaptive Form in authoring mode, select any form object, and tap  to open the rule editor.
1. Select **[!UICONTROL Form]** in the Form Objects tree and tap **[!UICONTROL Create]**.
1. Select **[!UICONTROL Error in Submission]** from the Event drop-down list.
1. Write a rule to convert custom error structure to the standard error structure and tap **[!UICONTROL Done]** to save the rule.

The following is a sample code to convert a custom error structure to the standard error structure:

```javascript
var data = $event.data;
var som_map = {
    "id": "guide[0].guide1[0].guideRootPanel[0].Pet[0].id_1[0]",
    "name": "guide[0].guide1[0].guideRootPanel[0].Pet[0].name_2[0]",
    "status": "guide[0].guide1[0].guideRootPanel[0].Pet[0].status[0]"
};

var errorJson = {};
errorJson.errors = [];

if (data) {
    if (data.originMessage) {
        var errorData;
        try {
            errorData = JSON.parse(data.originMessage);
        } catch (err) {
            // not in json format
        }

        if (errorData) {
            Object.keys(errorData).forEach(function(key) {
                var som_key = som_map[key];
                if (som_key) {
                    var error = {};
                    error.somExpression = som_key;
                    error.errorMessage = errorData[key];
                    errorJson.errors.push(error);
                }
            });
        }
        window.guideBridge.handleServerValidationError(errorJson);
    } else {
        window.guideBridge.handleServerValidationError(data);
    }
}
```

The `var som_map` lists the SOM expression of the Adaptive Form fields that you want to transform into the standard format. You can view the SOM expression of any field in an adaptive form by tapping the field and selecting **[!UICONTROL View SOM Expression]**.

Using this custom error handler, the adaptive form converts the fields listed in `var som_map` to standard error message format. As a result, the validation error messages display at field-level in the adaptive form.

 -->