---
title: Hinzufügen benutzerdefinierter Fehler-Handler in adaptive Formulare für adaptive Formulare in AEM
description: AEM Forms bietet vordefinierte Erfolgs- und Fehler-Handler für ein Formular mit Verwendung des REST-Endpunkts, der zum Aufrufen eines externen Dienstes konfiguriert wurde. Sie können einen standardmäßigen und einen benutzerdefinierten Fehler-Handler zu einem adaptiven AEM-Formular hinzufügen.
keywords: Einen benutzerdefinierten Fehler-Handler hinzufügen, einen Standard-Fehler-Handler hinzufügen, einen Fehler-Handler zum Formular hinzufügen, einen benutzerdefinierten Fehler-Handler mit dem vom Regeleditor aufgerufenen Dienst hinzufügen, den Regeleditor für das Hinzufügen eines benutzerdefinierten Fehler-Handlers konfigurieren, einen benutzerdefinierten Fehler-Handler mit dem Regeleditor hinzufügen
contentOwner: Ruchita Srivastav
content-type: reference
feature: Adaptive Forms, Foundation Components
exl-id: 198a26a9-d6bb-457d-aab8-0a5d15177c48
role: User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '2323'
ht-degree: 98%

---

# Hinzufügen von benutzerdefinierten Fehler-Handlern in adaptiven Formularen {#error-handlers-in-adaptive-form}

>[!NOTE]
>
> Adobe empfiehlt die Verwendung der modernen und erweiterbaren Datenerfassung [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de) zum [Erstellen eines neuen adaptiven Forms](/help/forms/creating-adaptive-form-core-components.md) oder [Hinzufügen von adaptivem Forms zu AEM Sites-Seiten](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md). Diese Komponenten stellen einen bedeutenden Fortschritt bei der Erstellung adaptiver Formulare dar und sorgen für beeindruckende Anwendererlebnisse. In diesem Artikel wird der ältere Ansatz zum Erstellen adaptiver Forms mithilfe von Foundation-Komponenten beschrieben.

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

AEM Forms bietet vordefinierte Erfolgs- und Fehler-Handler für Formularübermittlungen. Es bietet außerdem Funktionen zum Anpassen von Fehler-Handler-Funktionen. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehler-Codes aufrufen oder die Kundin bzw. den Kunden darüber informieren, dass der Dienst ausgefallen ist. Handler sind Client-seitige Funktionen, die basierend auf der Server-Antwort ausgeführt werden. Beim Aufruf eines externen Dienstes über APIs werden die Daten zu Validierung an den Server gesendet, der wiederum die Kundin bzw. den Kunden über das Erfolgs- oder Fehlerereignis in Bezug auf die Übermittlung informiert. Die Informationen werden als Parameter an den relevanten Handler übergeben, um die Funktion auszuführen. Ein Fehler-Handler hilft bei der Verwaltung und Anzeige von Fehlern und Validierungsproblemen.

![Workflow für Fehler-Handler, um zu verstehen, wie Sie benutzerdefinierte Fehler-Handler in Formularen hinzufügen](/help/forms/assets/error-handler-workflow.png)

 Das adaptive Formular validiert die Eingaben in die Felder anhand vorgegebener Validierungskriterien und sucht nach verschiedenen Fehlern, die von dem für den Aufruf eines externen Dienstes konfigurierten REST-Endpunkt zurückgegeben werden. Sie können die Validierungskriterien auf Grundlage der Datenquelle festlegen, die Sie mit dem adaptiven Formular verwenden. Wenn Sie beispielsweise RESTful-Web-Services als Datenquelle verwenden, können Sie die Validierungskriterien in einer Swagger-Definitionsdatei definieren.

Wenn die Eingabewerte die Validierungskriterien erfüllen und die Werte an die Datenquelle gesendet werden, zeigt das adaptive Formular mithilfe eines Fehler-Handlers eine Fehlermeldung an. Ähnlich wie bei diesem Ansatz können adaptive Formulare jetzt in benutzerdefinierte Dienste integriert werden, um Datenvalidierungen durchzuführen. Wenn die Eingabewerte die Validierungskriterien nicht erfüllen, werden die Fehlermeldungen auf Feldebene im adaptiven Formular angezeigt. Dies tritt auf, wenn die vom Server zurückgegebene Validierungsfehlermeldung im standardmäßigen Nachrichtenformat vorliegt.


## Verwendung von Fehler-Handlern {#uses-of-error-handler}

Fehler-Handler werden für verschiedene Zwecke verwendet. Nachfolgend finden Sie einige Beispiele für die Verwendung der Fehler-Handler-Funktionen:
* **Durchführen einer Validierung**: Die Fehlerbehandlung beginnt mit der Validierung von Benutzereingaben anhand vordefinierter Regeln oder Kriterien. Wenn Benutzende ein adaptives Formular ausfüllen, validiert der Fehler-Handler die Eingabe, um sicherzustellen, dass sie das erforderliche Format, die Länge oder andere Vorgaben erfüllt.

* **Echtzeit-Feedback geben**: Wenn ein Fehler erkannt wird, zeigt der Fehler-Handler den Benutzenden sofortiges Feedback an, z. B. Inline-Fehlermeldungen unter den entsprechenden Formularfeldern. Anhand dieses Feedbacks hilft können die Benutzenden Fehler identifizieren und korrigieren, ohne das Formular senden und auf eine Antwort warten zu müssen.


* **Anzeigen von Fehlermeldungen**: Wenn bei der Übermittlung eines adaptiven Formulars ein Validierungsfehler auftritt, zeigt der Fehler-Handler eine entsprechende Fehlermeldung an. Die Fehlermeldungen sollten klar und deutlich sein und auf die spezifischen Felder hinweisen, die beachtet werden müssen.

* **Hervorheben des fehlerhaften Felds**: Um die Aufmerksamkeit der Benutzenden auf bestimmte falsche Felder zu lenken, hebt der Fehler-Handler die entsprechenden Felder hervor oder unterscheidet sie visuell. Dies geschieht durch Ändern der Hintergrundfarbe, Hinzufügen eines Symbols oder Rahmens oder eines anderen visuellen Hinweises, der den Benutzenden hilft, den Fehler schnell zu finden und zu beheben.


## Fehlerantwortformat {#failure-response-format}

Ein adaptives Formular zeigt die Fehler auf Feldebene an, wenn die Fehlermeldungen der Server-Validierung im folgenden Standardformat vorliegen.
Folgender Code veranschaulicht die vorhandene Fehlerreaktionsstruktur:

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
* `originCode` Feld, das von AEM hinzugefügt wurde und den vom externen Dienst zurückgegebenen HTTP-Status-Code enthält.
* `originMessage` Feld, das von AEM hinzugefügt wurde und die vom externen Dienst zurückgegebenen Rohfehlerdaten enthält.

Mit den Verbesserungen bei den Funktionen und den nachfolgenden Updates in den Versionen von AEM Forms wurde die bestehende Fehlerantwortstruktur in ein neues Format auf der Grundlage von RFC7807 geändert, das mit der bestehenden Fehlerreaktionsstruktur abwärtskompatibel ist:

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
> * Stellen Sie sicher, dass die Struktur der Fehlerantwort entweder **fieldName** oder **dataRef** enthält.
> * Stellen Sie sicher, dass die **ContentType**-Kopfzeile **application/problem+json** lautet.

Dabei gilt:
* `type (required)` gibt den Fehlertyp an. Es kann einer der folgenden Werte sein:
   * `SERVER_SIDE_VALIDATION` weist auf einen Fehler aufgrund der Server-seitigen Validierung hin.
   * `FORM_SUBMISSION` weist auf einen Fehler während der Formularübermittlung hin.
   * `SERVICE_INVOCATION` weist auf einen Fehler während des Aufrufs eines Drittanbieter-Dienstes hin.
   * `FAILURE` weist auf einen allgemeinen Fehler hin.
   * `VALIDATION_ERROR` weist auf einen Fehler aufgrund eines Validierungsfehlers hin.

* `title (optional)` enthält einen Titel oder eine kurze Beschreibung des Fehlers.
* `detail (optional)` enthält bei Bedarf weitere Details zum Fehler.
* `instance (optional)` stellt eine Instanz oder eine Kennung dar, die mit dem Fehler verknüpft ist, und hilft beim Tracking oder Identifizieren des spezifischen Auftretens des Fehlers.
* `validationErrors (required)` enthält Informationen zu Validierungsfehlern. Dazu gehören folgende Felder:
   * `fieldname` erwähnt den SOM-Ausdruck der Felder, die die Validierungskriterien nicht erfüllt haben.
   * `dataRef` stellt den JSON-Pfad oder XPath der Felder dar, bei denen die Validierung fehlgeschlagen ist.
   * `details` enthält die Validierungsfehlermeldung mit dem fehlerhaften Feld.
* `originCode (optional)` Feld, das von AEM hinzugefügt wurde und den vom externen Dienst zurückgegebenen HTTP-Status-Code enthält.
* `originMessage (optional)` Feld, das von AEM hinzugefügt wurde und die vom externen Dienst zurückgegebenen Rohfehlerdaten enthält.

### Beispiel für das Format einer Fehlerantwort {#sample-error-response-format}

Einige der Optionen zur Anzeige der Fehlerantworten sind:

+++  Basierend auf der fieldName-Eigenschaft des adaptiven Formulars


* **`Header:`** `content-type:application/problem+json`
* **`Response:`**

  ```javascript
          {
              "type": "VALIDATION_ERROR",
              "validationErrors": [
              {
              "fieldName": "guide[0].guide1[0].guideRootPanel[0].textbox1686647736683[0]",
              "dataRef": "",
              "details": [
              "Invalid ID supplied. Provided value is not correct!"
          ]
          }
          ]}
  ```

  Sie können den SOM-Ausdruck eines beliebigen Felds in einem adaptiven Formular anzeigen, indem Sie auf das Feld tippen und **[!UICONTROL SOM-Ausdruck anzeigen]** auswählen.

  ![SOM-Ausdruck eines adaptiven Formularfelds zur Anzeige der Fehlerantwort im benutzerdefinierten Fehler-Handler](/help/forms/assets/custom-error-handler-somexpression.png)

+++


+++ Basierend auf der dataRef-Eigenschaft des adaptiven Formulars

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

Sie können den Wert von dataRef im Fenster **[!UICONTROL Eigenschaften]** einer Formularkomponente anzeigen.

+++


## Hinzufügen eines Fehler-Handlers mithilfe des Regeleditors {#add-error-handler-using-rule-editor}

Mithilfe der Aktion [Aufrufdienst des Regeleditors](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=de#invoke) definieren Sie die Validierungskriterien basierend auf der Datenquelle, die Sie mit dem adaptiven Formular verwenden. Wenn Sie beispielsweise RESTful-Web-Services als Datenquelle verwenden, können Sie die Validierungskriterien in einer Swagger-Definitionsdatei definieren. Durch die Verwendung der Funktionen des Fehler-Handlers und des Regeleditors in adaptiven Formularen können Sie die Fehlerbehandlung effektiv verwalten und anpassen. Sie definieren die Bedingungen mithilfe des Regeleditors und konfigurieren die gewünschten Aktionen, die bei Auslösen der Regel ausgeführt werden sollen. Adaptive Formulare validieren die Eingaben, die Sie in Felder eingeben, auf der Grundlage von voreingestellten Validierungskriterien. Falls die Eingabewerte die Validierungskriterien nicht erfüllen, werden die Fehlermeldungen auf Feldebene in einem adaptiven Formular angezeigt.

>[!NOTE]
>
> * Um Fehler-Handler mit der Regeleditor-Aktion „Dienst aufrufen“ zu verwenden, konfigurieren Sie adaptive Formulare mit einem Formulardatenmodell (FDM).
> * Ein Standard-Fehler-Handler wird standardmäßig bereitgestellt, um Fehlermeldungen auf Feldern anzuzeigen, wenn die Fehlerantwort im Standardschema enthalten ist. Sie können den Standard-Fehler-Handler auch über die benutzerdefinierte Fehler-Handler-Funktion aufrufen.

Mit dem Regeleditor können Sie:
* [Standard-Fehler-Handler-Funktion hinzufügen](#add-default-errror-handler)
* [Hinzufügen einer benutzerdefinierten Fehler-Handler-Funktion](#add-custom-error-handler-function)


### Standard-Fehler-Handler-Funktion hinzufügen {#add-default-errror-handler}

Ein Standard-Fehler-Handler wird unterstützt, um Fehlermeldungen in Feldern anzuzeigen, wenn die Fehlerantwort im Standardschema oder bei Server-seitigem Validierungsfehler liegt
Um zu verstehen, wie man einen Standard-Fehler-Handler mit der Aktion [Aufrufdienst des Regeleditors](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=de#invoke) verwendet, nehmen wir ein Beispiel für ein einfaches adaptives Formular mit zwei Feldern, **Haustier-ID** und **Haustiername**. Verwenden Sie einen Standard-Fehler-Handler für das Feld **Haustier-ID** zur Überprüfung auf verschiedene Fehler, die vom REST-Endpunkt zurückgegeben werden, der zum Aufrufen eines externen Dienstes konfiguriert ist, z. B. `200 - OK`, `404 - Not Found`, `400 - Bad Request`. Führen Sie die folgenden Schritte aus, um mithilfe der Aktion „Aufrufdienst des Regeleditors“ einen Standard-Fehler-Handler hinzuzufügen:

1. Öffnen Sie ein adaptives Formular im Authoring-Modus, wählen Sie eine Formularkomponente und dann **[!UICONTROL Regeleditor]** aus, um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.
1. Erstellen Sie eine Bedingung im Abschnitt **Wenn** der Regel. Zum Beispiel: **Wenn [der Name des Feldes Haustier-ID]** geändert wird. Die Auswahl wird aus der Dropdown-Liste **Status auswählen** geändert.
1. Im Abschnitt **Dann** wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **Aktion auswählen.**
1. Wählen Sie einen **Post-Service** und die zugehörigen Datenbindungen aus dem Abschnitt **Eingabe**. Um zum Beispiel **Haustier-ID** zu validieren, wählen Sie einen **Post-Service** als **GET /pet/{petId}** und dann **Haustier-ID** im Abschnitt **Eingabe**.
1. Wählen Sie die Datenbindungen aus dem Abschnitt **Ausgabe**. Wählen Sie **Haustiername** im Abschnitt **Ausgabe**.
1. Wählen Sie **[!UICONTROL Standard-Fehler-Handler]** im Abschnitt **Fehler-Handler**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Hinzufügen eines Standard-Fehler-Handlers für Feldvalidierungsprüfungen in einem Formular](/help/forms/assets/default-error-handler.png)

Aufgrund dieser Regel werden die Werte, die Sie für **Haustier-ID** eingeben, bei der Validierung von **Haustiername** über einen externen Dienst überprüft, der über einen REST-Endpunkt aufgerufen wird. Wenn die auf der Datenquelle basierenden Validierungskriterien nicht erfüllt werden, werden die Fehlermeldungen auf Feldebene angezeigt.

![Anzeigen der Standardfehlermeldung beim Hinzufügen eines Standard-Fehler-Handlers in einem Formular zur Verarbeitung von Fehlerantworten](/help/forms/assets/default-error-message.png)

### Hinzufügen einer benutzerdefinierten Fehler-Handler-Funktion

Sie können eine benutzerdefinierte Fehler-Handler-Funktion hinzufügen, um einige der folgenden Aktionen auszuführen:

* Behandlung von Fehlerantworten, die nicht standardmäßige oder Standardfehlerantworten verwenden. Es ist wichtig zu beachten, dass diese nicht-standardmäßigen Fehlerantworten nicht dem [Standardschema von Fehlerantworten](#failure-response-format) entsprechen.
* Senden von Analyseereignissen an beliebige Analyse-Plattformen. Beispiel: Adobe Analytics.
* Anzeigen eines modalen Dialogfelds mit Fehlermeldungen.

Zusätzlich zu den genannten Aktionen können die benutzerdefinierten Fehler-Handler verwendet werden, um benutzerdefinierte Funktionen auszuführen, die bestimmten Benutzeranforderungen entsprechen.

Der benutzerdefinierte Fehler-Handler ist eine Funktion (Client-Bibliothek), die auf die von einem externen Dienst zurückgegebenen Fehler reagiert und Endbenutzenden eine benutzerdefinierte Antwort bereitstellt. Jede Client-Bibliothek mit Anmerkungen `@errorHandler` wird als benutzerdefinierte Fehler-Handler-Funktion betrachtet. Diese Anmerkung hilft, die in der `.js`-Datei angegebene Fehler-Handler-Funktion zu identifizieren.
Um zu verstehen, wie man einen benutzerdefinierten Fehler-Handler mit der Aktion [Aufrufdienst des Regeleditors](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/rule-editor.html?lang=de#invoke) erstellt und verwendet, nehmen wir ein Beispiel für ein adaptives Formular mit zwei Feldern, **Haustier-ID** und **Haustiername** und verwenden einen benutzerdefinierten Fehler-Handler für das Feld **Haustier-ID**, um verschiedene Fehler zu überprüfen, die vom REST-Endpunkt zurückgegeben werden, der zum Aufrufen eines externen Dienstes konfiguriert ist, z. B. `200 - OK`, `404 - Not Found`, `400 - Bad Request`.

So können Sie einen benutzerdefinierten Fehler-Handler zu einem adaptiven Formular hinzufügen und verwenden:
1. [Hinzufügen einer benutzerdefinierten Funktion für den Fehler-Handler](#1-add-the-custom-function-for-the-error-handler)
2. [Verwenden des Regeleditors zum Konfigurieren des benutzerdefinierten Fehler-Handlers](#use-custom-error-handler)

#### 1. Hinzufügen der benutzerdefinierten Funktion für den Fehler-Handler

Um zu erfahren, wie Sie benutzerdefinierte Funktionen hinzufügen, klicken Sie auf [Erstellen von benutzerdefinierten Funktionen in einem adaptiven Formular, das auf Kernkomponenten basiert](/help/forms/custom-function-core-component-create-function.md#create-a-custom-function).

<!-- To create a custom error function, perform the following steps:

1. [Clone your AEM Forms as a Cloud Service Repository](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=en#accessing-git). 
2. Create a folder under the `[AEM Forms as a Cloud Service repository folder]/apps/` folder. For example, create a folder named as `experience-league`
3. Navigate to `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/experience-league/` and create a `ClientLibraryFolder` as `clientlibs`.
4. Create a folder named `js`.
5. Navigate to the `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` folder. -->

1. Fügen Sie den folgenden Code für den benutzerdefinierten Fehler-Handler in der JavaScript-Datei hinzu, z. B. `function.js`. Die Datei enthält den Code für den benutzerdefinierten Fehler-Handler.
Fügen Sie folgenden Code zur JavaScript-Datei hinzu, um die Antwort und die vom REST-Dienstendpunkt empfangenen Kopfzeilen in der Browser-Konsole anzuzeigen.

   ```javascript
       /**
       * Custom Error handler
       * @name customErrorHandler Custom Error Handler Function
       * @errorHandler
       */
       function customErrorHandler(response, headers)
       {
           console.log("Custom Error Handler processing start...");
           console.log("response:"+JSON.stringify(response));
           console.log("headers:"+JSON.stringify(headers));
           guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers);
           console.log("Custom Error Handler processing end...");
       }
   ```

   >[!NOTE]
   >
   > * Zum Aufrufen des standardmäßigen Fehler-Handlers über Ihren benutzerdefinierten Fehler-Handler wird folgende Zeile des Beispiel-Codes verwendet: `guidelib.dataIntegrationUtils.defaultErrorHandler(response, headers) `
   > * Fügen Sie in der Datei `.content.xml` die Eigenschaften `allowProxy` und `categories` hinzu, um die Client-Bibliothek des benutzerdefinierten Fehler-Handlers in einem adaptiven Formular zu verwenden.
   >
   >   * `allowProxy = [Boolean]true`
   >   * `categories= customfunctionsdemo`
   >       Beispiel: In diesem Fall wird [custom-errorhandler-name] als `customfunctionsdemo` bereitgestellt.


1. Fügen Sie die Änderungen hinzu, übertragen Sie sie und pushen Sie sie in das Repository.

<!--

<!--
1. Save the `function.js` file.
1. Navigate to the `[AEM Forms as a Cloud Service repository folder]/apps/[AEM Project Folder]/clientlibs/js` folder.
2. Add a text file as `js.txt`. The file contains:

    ```javascript
        #base=js
        functions.js
    ```

3. Save the `js.txt` file.    
The created folder structure looks like:

    ![Created Client Library Folder Structure](/help/forms/assets/customclientlibrary_folderstructure.png) 
    using the below commands:
         
    ```javascript

        git add .
        git commit -a -m "Adding error handling files"
        git push
    ```
-->

1. [Ausführen der Pipeline](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/onboarding/journey/developers.html?lang=de#setup-pipeline) 

Sobald die Pipeline erfolgreich ausgeführt wurde, steht der benutzerdefinierte Fehler-Handler im Regeleditor für adaptive Formulare zur Verfügung. Im Folgenden erfahren Sie, wie Sie einen benutzerdefinierten Fehler-Handler mit dem Aufrufdienst des Regeleditors in AEM Forms konfigurieren und verwenden.

#### 2. Verwenden des Regeleditors zum Konfigurieren des benutzerdefinierten Fehler-Handlers {#use-custom-error-handler}

Bevor Sie den benutzerdefinierten Fehler-Handler in einem adaptiven Formular implementieren, stellen Sie sicher, dass der Name der Client-Bibliothek in der **[!UICONTROL Client-Bibliothekskategorie]** dem Namen entspricht, der in der Kategorieoption der Datei `.content.xml` angegeben ist.

![Hinzufügen des Namens der Client-Bibliothek in der Konfiguration des Containers für adaptive Formulare](/help/forms/assets/client-library-category-name.png)

In diesem Fall wird der Name der Client-Bibliothek als `customfunctionsdemo` in der Datei `.content.xml` angegeben.

So verwenden Sie einen benutzerdefinierten Fehler-Handler mit der Aktion **[!UICONTROL Aufrufdienst des Regel-Editors]**:

1. Öffnen Sie ein adaptives Formular im Authoring-Modus, wählen Sie eine Formularkomponente und dann **[!UICONTROL Regeleditor]** aus, um den Regeleditor zu öffnen.
1. Wählen Sie **[!UICONTROL Erstellen]** aus.
1. Erstellen Sie eine Bedingung im Abschnitt **Wenn** der Regel. Wenn beispielsweise der **[Name des Felds „Haustier-ID“]** geändert wird, wählen Sie in der Dropdown-Liste **Status auswählen** die Option **wird geändert** aus.
1. Im Abschnitt **Dann** wählen Sie **[!UICONTROL Dienst aufrufen]** aus der Dropdown-Liste **Aktion auswählen.**
1. Wählen Sie einen **Post-Service** und die zugehörigen Datenbindungen aus dem Abschnitt **Eingabe**. Um zum Beispiel **Haustier-ID** zu validieren, wählen Sie einen **Post-Service** als **GET /pet/{petId}** und dann **Haustier-ID** im Abschnitt **Eingabe**.
1. Wählen Sie die Datenbindungen aus dem Abschnitt **Ausgabe**. Wählen Sie beispielsweise **Haustiername** im Abschnitt **Ausgabe**.
1. Wählen Sie **[!UICONTROL Benutzerdefinierter Fehler-Handler]** im Abschnitt **[!UICONTROL Fehler-Handler]**.
1. Klicken Sie auf **[!UICONTROL Fertig]**.

![Hinzufügen eines benutzerdefinierten Fehler-Handlers in einem Formular, um Fehlerantworten zu verarbeiten](/help/forms/assets/custom-error-handler.png)

Aufgrund dieser Regel werden die Werte, die Sie für **Haustier-ID** eingeben, bei der Validierung von **Haustiername** über einen externen Dienst überprüft, der über einen REST-Endpunkt aufgerufen wird. Wenn die auf der Datenquelle basierenden Validierungskriterien nicht erfüllt werden, werden die Fehlermeldungen auf Feldebene angezeigt.

![Hinzufügen eines benutzerdefinierten Fehler-Handlers in einem Formular, um Fehlerantworten zu verarbeiten](/help/forms/assets/custom-error-handler-message.png)

Öffnen Sie die Browser-Konsole und überprüfen Sie die Antwort und die Kopfzeile, die vom REST-Dienstendpunkt empfangen wurden, auf die Validierungsfehlermeldung.


Die benutzerdefinierte Fehler-Handler-Funktion ist für die Ausführung zusätzlicher Aktionen verantwortlich, z. B. für die Anzeige eines modalen Dialogfelds oder das Senden eines Analytics-Ereignisses basierend auf der Fehlerantwort. Eine benutzerdefinierte Fehler-Handler-Funktion bietet die Flexibilität, die Fehlerbehandlung an die spezifischen Benutzeranforderungen anzupassen.

<!-- 

## Configure Adaptive Form submission to add custom handlers {#configure-adaptive-form-submission}

If the server validation error message does not display in the standard format, you can enable asynchronous submission and add a custom error handler on Adaptive Form submission to convert the message into a standard format.

### Configure asynchronous Adaptive Form submission {#configure-asynchronous-adaptive-form-submission}

Before adding custom handler, you must configure the adaptive form for asynchronous submission. Execute the following steps:

1. In adaptive form authoring mode, select the Form Container object and select ![adaptive form properties](assets/configure_icon.png) to open its properties.
1. In the **[!UICONTROL Submission]** properties section, enable **[!UICONTROL Use asynchronous submission]**.
1. Select **[!UICONTROL Revalidate on server]** to validate the input field values on server before submission.
1. Select the Submit Action:

    * Select **[!UICONTROL Submit using Form Data Model (FDM)]** and select the appropriate data model, if you are using RESTful web service based [form data model (FDM)](work-with-form-data-model.md) as the data source.
    * Select **[!UICONTROL Submit to REST Service endpoint]** and specify the **[!UICONTROL Redirect URL/Path]**, if you are using RESTful web services as the data source.

    ![adaptive form submission properties](assets/af_submission_properties.png)

1. Select ![Save](assets/save_icon.png) to save the properties.

### Add custom error handler on Adaptive Form submission {#add-custom-error-handler-af-submission}

AEM Forms provides out-of-the-box success and error handlers for form submissions. Handlers are client-side functions that execute based on the server response. When an Adaptive Form is submitted, the data is transmitted to the server for validation, which returns a response to the client with information about the success or error event for the submission. The information is passed as parameters to the relevant handler to execute the function.

Execute the following steps to add custom error handler on Adaptive Form submission:

1. Open an Adaptive Form in authoring mode, select any form object, and select  to open the rule editor.
1. Select **[!UICONTROL Form]** in the Form Objects tree and select **[!UICONTROL Create]**.
1. Select **[!UICONTROL Error in Submission]** from the Event drop-down list.
1. Write a rule to convert custom error structure to the standard error structure and select **[!UICONTROL Done]** to save the rule.

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
            Object.keys (errorData).forEach(function(key) {
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


## Siehe auch {#see-also}

{{see-also}}
* [Erstellen und Verwenden benutzerdefinierter Fehler-Handler in adaptiven Formularen (Kernkomponenten)](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)

<!--

>[!MORELIKETHIS]
>
>* [Create style or themes for your forms](/help/forms/using-themes-in-core-components.md)
>* [Create or add an Adaptive Form to AEM Sites page](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md)

-->
