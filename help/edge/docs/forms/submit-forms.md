---
title: Vorbereiten der Tabelle auf die Datenaufnahme
description: Erstellen Sie leistungsstarke Formulare schneller mit Tabellen und Blockfelder für ein adaptives Formular.
feature: Edge Delivery Services
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
role: Admin, Architect, Developer
source-git-commit: 552779d9d1cee2ae9f233cabc2405eb6416c41bc
workflow-type: tm+mt
source-wordcount: '873'
ht-degree: 81%

---

# Einrichten von Google Tabellen- oder Microsoft Excel-Dateien für die Datenaufnahme


Nachdem Sie [das Formular erstellt und in der Vorschau angezeigt](/help/edge/docs/forms/create-forms.md), können Sie die entsprechende Tabelle aktivieren, um mit dem Empfang von Daten zu beginnen. Sie haben folgende Möglichkeiten:

* [Aktivieren Sie die Tabelle manuell, um Daten zu akzeptieren](#manually-enable-the-spreadsheet-to-accept-data)
* [Verwenden von Admin-APIs, um das Akzeptieren von Daten durch eine Tabelle zu aktivieren](#use-admin-apis-to-enable-a-spreadsheet-to-accept-data)

![Das Ökosystem des dokumentbasierten Authorings](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)


<!--

>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->

## Manuelles Aktivieren der Tabelle für die Datenaufnahme

So ermöglichen Sie die Datenaufnahme in der Tabelle:

1. Öffnen Sie das Arbeitsblatt, in dem sich Ihr Formular befindet, und fügen Sie ein neues Arbeitsblatt an, indem Sie es in `incoming` umbenennen. Zum Beispiel die Arbeitsmappe [Anfrage](/help/edge/assets/enquiry.xlsx) von Microsoft Excel.

   >[!WARNING]
   >
   > Wenn das Blatt `incoming` nicht vorhanden ist, sendet AEM keine Daten an die Tabelle.

1. Fügen Sie aus diesem Blatt eine Tabelle mit dem Namen „intake_form“ ein. Wählen Sie die Anzahl der Spalten aus, die zum Abgleich der Formularfeldnamen erforderlich sind. Navigieren Sie dann in der Symbolleiste zu „Einfügen“ > „Tabelle“ und klicken Sie auf „OK“.

1. Ändern Sie den Namen der Tabelle in „intake_form“. Um in Microsoft Excel den Tabellennamen zu ändern, wählen Sie die Tabelle aus und klicken Sie auf „Tabellendesign“.

1. Fügen Sie als Nächstes die Formularfeldnamen als Tabellenkopfzeilen hinzu. Um sicherzustellen, dass die Felder genau identisch sind, können Sie sie aus dem Blatt „shared-aem“ kopieren und einfügen.  Wählen Sie in Ihrem Blatt „Shared-AEM“ die Formular-IDs aus, die unter der Spalte „Name“ aufgeführt sind, und kopieren Sie sie, mit Ausnahme des Felds „Senden“.

1. Wählen Sie im Blatt „eingehend“ die Option „Sonderzeichen einfügen“ > „Zeilen in Spalten exportieren“, um die Feld-IDs als Spaltenkopfzeilen in dieses neue Blatt zu kopieren. Behalten Sie nur die Felder bei, deren Daten erfasst werden müssen. Andere Felder können ignoriert werden.

   Jeder Wert in der Spalte `Name` des Blattes `shared-aem`, mit Ausnahme der Senden-Schaltfläche, kann als Kopfzeile im Blatt `incoming` dienen. Betrachten Sie beispielsweise das folgende Bild, das Kopfzeilen für ein Formular „Anfrage“ veranschaulicht:

   ![Felder für das Formular „contact-us“](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

1. Verwenden Sie die Erweiterung [AEM Sidekick](https://www.aem.live/developer/tutorial#preview-and-publish-your-content), um eine Vorschau der Formularaktualisierungen anzuzeigen. Ihr Blatt kann jetzt eingehende Formularübermittlungen aufnehmen.

   >[!NOTE]
   >
   >Selbst wenn Sie das Blatt zuvor in der Vorschau angezeigt haben, müssen Sie die Vorschau erneut anzeigen, nachdem Sie das Blatt `incoming` zum ersten Mal erstellt haben.


Nachdem die Feldnamen zu dem Blatt `incoming` hinzugefügt wurden, kann Ihr Formular Übermittlungen annehmen. Sie können das Formular in der Vorschau anzeigen und damit Daten an das Blatt senden, das es verwendet.

Nachdem das Blatt für den Datenempfang eingerichtet wurde, können Sie [Vorschau des Formulars anzeigen](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) <!--or [use POST requests](#use-admin-apis-to-send-data-to-your-sheet)--> um mit dem Senden von Daten an das Blatt zu beginnen.

>[!WARNING]
>
>  Die „Shared-AEM“-Blätter sollten niemals persönlich identifizierbare Informationen oder vertrauliche Daten enthalten, bei denen Sie nicht sicher sind, ob sie öffentlich zugänglich sind.


## Verwenden von Admin-APIs, um das Akzeptieren von Daten durch eine Tabelle zu aktivieren

Sie können auch eine POST-Anfrage an das Formular senden, damit es Daten aufnehmen und Kopfzeilen für das Blatt `incoming` konfigurieren kann. Nach Erhalt der POST-Anfrage analysiert der Dienst den Anforderungstext und generiert autonom die für die Datenaufnahme erforderlichen Kopfzeilen und Blätter.

So verwenden Sie Admin-APIs, um das Akzeptieren von Daten durch eine Tabelle zu aktivieren:


1. Öffnen Sie die von Ihnen erstellte Arbeitsmappe und ändern Sie den Namen des Standardblattes in `incoming`.

   >[!WARNING]
   >
   > Wenn das Blatt `incoming` nicht existiert, sendet AEM keine Daten an diese Arbeitsmappe.

1. Zeigen Sie eine Vorschau des Blattes im Sidekick an.

   >[!NOTE]
   >
   >Selbst wenn Sie das Blatt zuvor in der Vorschau angezeigt haben, müssen Sie die Vorschau erneut anzeigen, nachdem Sie das Blatt `incoming` zum ersten Mal erstellt haben.

1. Senden Sie die POST-Anfrage, um die entsprechenden Kopfzeilen auf dem Blatt `incoming` zu generieren, und fügen Sie das Blatt `shared-default` zu Ihrer Tabelle hinzu, falls es nicht bereits existiert.

   Informationen zum Formatieren der POST-Anfrage zum Einrichten des Blattes finden Sie in der [Dokumentation zur Admin-API](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile). Sie können sich das folgende Beispiel ansehen:

   **Anfrage**

   ```JSON
   POST 'https://admin.aem.page/form/{owner}/{repo}/{branch}/contact-us.json' \
   --header 'Content-Type: application/json' \
   --data '{
       "data": {
           "Email": "john@wknd.com",
           "Name": "John",
           "Subject": "Regarding Product Inquiry",
           "Message": "I have some questions about your products.",
           "Phone": "123-456-7890",
           "Company": "Adobe Inc.",
           "Country": "United States",
           "PreferredContactMethod": "Email",
           "SubscribeToNewsletter": true
       }
   }'
   ```


   **Antwort**

   ```JSON
   HTTP/2 200 
   content-type: application/json
   x-invocation-id: 1b3bd30a-8cfb-4f85-a662-4b1f7cf367c5
   cache-control: no-store, private, must-revalidate
   accept-ranges: bytes
   date: Sat, 10 Feb 2024 09:26:48 GMT
   via: 1.1 varnish
   x-served-by: cache-del21736-DEL
   x-cache: MISS
   x-cache-hits: 0
   x-timer: S1707557205.094883,VS0,VE3799
   strict-transport-security: max-age=31557600
   content-length: 138
   
   {"rowCount":2,"columns":["Email","Name","Subject","Message","Phone","Company","Country",      "PreferredContactMethod","SubscribeToNewsletter"]}%
   ```

   Sie können Tools wie curl oder Postman verwenden, um diese POST-Anfrage auszuführen, wie unten dargestellt:

   ```JSON
   curl -s -i -X POST 'https://admin.aem.page/form/wkndform/wefinance/main/contact-us.json' \
       --header 'Content-Type: application/json' \
       --data '{
           "data": {
               "Email": "john@wknd.com",
               "Name": "John",
               "Subject": "Regarding Product Inquiry",
               "Message": "I have some questions about your products.",
               "Phone": "123-456-7890",
               "Company": "Wknd Inc.",
               "Country": "United States",
               "PreferredContactMethod": "Email",
               "SubscribeToNewsletter": true
       }
   }'
   ```

   Die oben genannte POST-Anfrage enthält Beispieldaten, einschließlich der beiden Formularfelder und ihren entsprechenden Beispielwerten. Diese Daten werden vom Admin-Dienst zum Einrichten des Formulars verwendet.

   Ihr Formular kann jetzt Daten annehmen. Beachten Sie auch die folgenden Änderungen in Ihrer Tabelle:

## Automatische Änderungen am Blatt, sobald es zur Datenaufnahme aktiviert ist.

Nachdem das Blatt auf den Empfang von Daten eingestellt wurde, beachten Sie die folgenden Änderungen an Ihrer Tabelle:

Ein Blatt mit dem Namen „Slack“ wird Ihrer Excel-Arbeitsmappe oder Ihrer Google-Tabelle hinzugefügt. In dieser Tabelle können Sie automatische Benachrichtigungen für einen bestimmten Slack-Kanal konfigurieren, sobald neue Daten in Ihre Tabelle aufgenommen werden. Derzeit unterstützt AEM ausschließlich Benachrichtigungen an die Organisation AEM Engineering Slack und die Organisation Adobe Enterprise Support.

1. Um Slack-Benachrichtigungen einzurichten, geben Sie die „teamId“ des Slack-Arbeitsbereichs und den „Kanalnamen“ bzw. die „ID“ ein. Sie können auch den Slack-Bot (mit dem Debugging-Befehl) nach der „teamId“ und der „Kanal-ID“ fragen. Die Verwendung der „Kanal-ID“ anstelle des „Kanalnamens“ ist vorzuziehen, da sie bei Kanalumbenennungen erhalten bleibt.

   >[!NOTE]
   >
   > Bei älteren Formularen war die Spalte „teamId“ nicht vorhanden. Die „teamId“ wurde in die Kanalspalte eingeschlossen, getrennt durch „#“ oder „/“.

1. Geben Sie einen beliebigen Titel ein und geben Sie unter den Feldern die Namen der Felder ein, die in der Slack-Benachrichtigung angezeigt werden sollen. Jede Überschrift sollte durch ein Komma getrennt werden (z. B. Name, E-Mail).

   >[!WARNING]
   >
   >  Die Blätter namens „shared-default“ dürfen niemals persönlich identifizierbare Informationen oder vertrauliche Daten enthalten, für die Sie keinen öffentlichen Zugriff wünschen.



<!--
## Send data to your sheet {#send-data-to-your-sheet}

After the sheet is set to receive data, you can [preview the form using Adaptive Forms Block](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) or [use Admin APIs](#use-admin-apis-to-send-data-to-your-sheet) to start sending data to the sheet.

### Use Admin APIs to send data to your sheet

You can send POST requests directly to your form using aem.page, aem.live, or your production domain, to send data. 


```JSON

POST https://branch–repo–owner.aem.(page|live)/email-form
POST https://my-domain.com/email-form

```

>[!NOTE] 
>
> The URL should not have the .json extension. You must publish the sheet for POST operations to function on `.live` or on the production domain.

#### Formatting the form data

There are a few different ways that you can format the form data in the POST body. You can use: 

* array of `name:value` pairs: 
    
    ```JSON
    
    {
      "data": [
        { "name": "name", "value": "Clark Kent" },
        { "name": "email", "value": "superman@example.com" },
        { "name": "subject", "value": "Regarding Product Inquiry" },
        { "name": "message", "value": "I have some questions about your products." },
        { "name": "phone", "value": "123-456-7890" },
        { "name": "company", "value": "Example Inc." },
        { "name": "country", "value": "United States" },
        { "name": "preferred_contact_method", "value": "Email" },
        { "name": "newsletter_subscribe", "value": true }
      ]
    }

    ```

    For example

    ```JSON

    curl -s -i -X POST 'https://main--wefinance--wkndform.aem.page/contact-us' \
        --header 'Content-Type: application/json' \
        --data '{
        "data": [
            { "name": "name", "value": "Clark Kent" },
            { "name": "email", "value": "superman@example.com" },
            { "name": "subject", "value": "Regarding Product Inquiry" },
            { "name": "message", "value": "I have some questions about your        products." },
            { "name": "phone", "value": "123-456-7890" },
            { "name": "company", "value": "Example Inc." },
            { "name": "country", "value": "United States" },
            { "name": "preferred_contact_method", "value": "Email" },
            { "name": "newsletter_subscribe", "value": true }
        ]
    }'

    ```



* an object with `key:value` pairs:

    ```JSON

        {
          "data": {
            "name": "Jessica Jones",
            "email": "jj@example.com",
            "subject": "Regarding Product Inquiry",
            "message": "I have some questions about your products.",
            "phone": "123-456-7890",
            "company": "Example Inc.",
            "country": "United States",
            "preferred_contact_method": "Email",
            "newsletter_subscribe": true
          }
        }

    ```

    For example,

    ```JSON

    curl -s -i -X POST 'https://admin.aem.page/form/wkndform/wefinance/main/contact-us.json' \
    --header 'Content-Type: application/json' \
    --data '{
        "data": {
            "Email": "khushwant@wknd.com",
            "Name": "khushwant",
            "Subject": "Regarding Product Inquiry",
            "Message": "I have some questions about your products.",
            "Phone": "123-456-7890",
            "Company": "Adobe Inc.",
            "Country": "United States",
            "PreferredContactMethod": "Email",
            "SubscribeToNewsletter": true
        }
    }'

    ```

* URL encoded (`x-www-form-urlencoded`) body (with `content-type` header set to `application/x-www-form-urlencoded`)

    ```Shell

    'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'

    ```

    For example, if your project's repository is named "wefinance", it's located under the account owner "wkndform", and you're using the "main" branch.,

    ```Shell

    curl -s -i -X POST \
      -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
      https://main--wefinance--wkndform.aem.live/contact-us

    ```
-->

Als Nächstes können Sie [die Dankesnachricht anpassen](/help/edge/docs/forms/thank-you-page-form.md).

## Siehe auch

{{see-more-forms-eds}}
