---
title: Vorbereiten der Tabelle auf die Datenaufnahme
description: Erstellen Sie leistungsstarke Formulare schneller mit Tabellen und Bausteinfeldern für adaptive Formulare!
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: e8fbe3efae7368c940cc2ed99cc9a352bbafbc22
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 1%

---


# Vorbereiten der Tabelle auf die Datenaufnahme

Sobald du [das Formular erstellt und in der Vorschau angezeigt wurde](/help/edge/docs/forms/create-forms.md)ist es an der Zeit, die entsprechende Tabelle so zu aktivieren, dass sie Daten erhält.

<!-- 
>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->

So aktivieren Sie das Arbeitsblatt:

1. Öffnen Sie das Arbeitsblatt, in dem sich Ihr Formular befindet, und fügen Sie ein neues Blatt hinzu, indem Sie es umbenennen. `incoming`.

   >[!WARNING]
   >
   > Wenn die Variable `incoming` -Tabelle nicht vorhanden ist, AEM keine Daten an die Tabelle sendet.

1. Spiegeln Sie die Formularfeldnamen und -werte der `Name` in der`shared-default` -Tabelle zu den Kopfzeilen im `incoming` Blatt.

   Jeder Wert in `Name` Spalte `shared-default` Tabellenblatt, mit Ausnahme der Senden-Schaltfläche, dient als Kopfzeile im `incoming` Blatt. Betrachten Sie beispielsweise die folgende Abbildung, die Kopfzeilen für ein &quot;contact-us&quot;-Formular veranschaulicht:

   ![Felder für ein Kontakt-Formular](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

1. Verwenden Sie den Sidekick, um eine Vorschau des Blatts anzuzeigen.

   >[!NOTE]
   >
   >Selbst wenn Sie die Vorschau des Arbeitsblatts zuvor angesehen haben, müssen Sie die Vorschau erneut anzeigen, nachdem Sie die `incoming` erstmalig.


Nachdem die Feldnamen zum `incoming` -Seite, kann Ihr Formular Übermittlungen annehmen. Sie können das Formular in der Vorschau anzeigen und Daten mit ihm an das Blatt senden.

Beachten Sie auch die folgenden Änderungen in Ihrer Tabelle:

Eine Tabelle mit dem Namen &quot;Slack&quot;wird Ihrer Excel-Arbeitsmappe oder Ihrem Google-Arbeitsblatt hinzugefügt. In diesem Arbeitsblatt können Sie automatische Benachrichtigungen für einen bestimmten Slack-Kanal konfigurieren, wenn neue Daten in Ihre Tabelle aufgenommen werden. Derzeit unterstützt AEM ausschließlich Benachrichtigungen an die Organisation AEM Engineering Slack und die Adobe Enterprise Support-Organisation.

1. Um Slack-Benachrichtigungen einzurichten, geben Sie die &quot;teamId&quot; des Slack-Arbeitsbereichs und den &quot;Kanalnamen&quot; bzw. die &quot;ID&quot; ein. Sie können auch den slack-Bot (mit dem Debugging-Befehl) nach der &quot;teamId&quot;und der &quot;channel ID&quot;fragen. Die Verwendung der &quot;Kanal-ID&quot;anstelle des &quot;Kanalnamens&quot;ist vorzuziehen, da Kanalumbenennungen erhalten bleiben.

   >[!NOTE]
   >
   > Bei älteren Formularen war die Spalte &quot;teamId&quot;nicht vorhanden. Die &quot;teamId&quot;wurde in die Kanalspalte eingeschlossen, getrennt durch &quot;#&quot;oder &quot;/&quot;.

1. Geben Sie einen beliebigen Titel ein und geben Sie unter den Feldern die Namen der Felder ein, die in der Slack-Benachrichtigung angezeigt werden sollen. Jede Überschrift sollte durch ein Komma getrennt werden (z. B. Name, E-Mail).

   >[!WARNING]
   >
   >  Die &quot;freigegebenen Standard&quot;-Tabellen dürfen niemals persönlich identifizierbare Informationen oder vertrauliche Daten enthalten, die Ihnen nicht mit dem öffentlichen Zugriff vertraut sind.


## (Optional) Verwenden Sie Admin-APIs, um die Akzeptanz von Daten in einer Tabelle zu ermöglichen

Sie können auch eine POST-Anfrage an das Formular senden, damit es Daten aufnehmen und Kopfzeilen für die `incoming` Blatt. Nach Erhalt der POST-Anfrage analysiert der Dienst den Anforderungstext und generiert autonom die für die Datenerfassung erforderlichen Kopfzeilen und Arbeitsblätter.

So verwenden Sie Admin-APIs, um eine Tabelle für die Datenaufnahme zu aktivieren:


1. Öffnen Sie die von Ihnen erstellte Arbeitsmappe und ändern Sie den Namen des Standardblatts in `incoming`.

   >[!WARNING]
   >
   > Wenn die Variable `incoming` Das Blatt existiert nicht, AEM sendet keine Daten an diese Arbeitsmappe.

1. Zeigen Sie eine Vorschau der Tabelle im Sidekick an.

   >[!NOTE]
   >
   >Selbst wenn Sie die Vorschau des Arbeitsblatts zuvor angesehen haben, müssen Sie die Vorschau erneut anzeigen, nachdem Sie die `incoming` erstmalig.

1. Senden Sie die POST-Anfrage, um die entsprechenden Header im `incoming` und fügen Sie die `shared-default` Blätter zu Ihrem Spread, wenn es nicht bereits existiert.

   Informationen zum Formatieren der POST-Anforderung zum Einrichten des Arbeitsblatts finden Sie im Abschnitt [Dokumentation zur Admin-API](https://www.aem.live/docs/admin.html#tag/authentication/operation/profile). Sie können sich das folgende Beispiel ansehen:

   **Anfrage**

   ```JSON
   POST 'https://admin.hlx.page/form/{owner}/{repo}/{branch}/contact-us.json' \
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
   curl -s -i -X POST 'https://admin.hlx.page/form/wkndforms/portal/main/contact-us.json' \
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

   Die oben genannte POST-Anfrage enthält Beispieldaten, einschließlich der beiden Formularfelder und der entsprechenden Beispielwerte. Diese Daten werden vom Admin-Dienst zum Einrichten des Formulars verwendet.

   Ihr Formular kann jetzt Daten annehmen. Beachten Sie auch die folgenden Änderungen in Ihrer Tabelle:

Eine Tabelle mit dem Namen &quot;Slack&quot;wird Ihrer Excel-Arbeitsmappe oder Ihrem Google-Arbeitsblatt hinzugefügt. In diesem Arbeitsblatt können Sie automatische Benachrichtigungen für einen bestimmten Slack-Kanal konfigurieren, wenn neue Daten in Ihre Tabelle aufgenommen werden. Derzeit unterstützt AEM ausschließlich Benachrichtigungen an die Organisation AEM Engineering Slack und die Adobe Enterprise Support-Organisation.

1. Um Slack-Benachrichtigungen einzurichten, geben Sie die &quot;teamId&quot; des Slack-Arbeitsbereichs und den &quot;Kanalnamen&quot; bzw. die &quot;ID&quot; ein. Sie können auch den slack-Bot (mit dem Debugging-Befehl) nach der &quot;teamId&quot;und der &quot;channel ID&quot;fragen. Die Verwendung der &quot;Kanal-ID&quot;anstelle des &quot;Kanalnamens&quot;ist vorzuziehen, da Kanalumbenennungen erhalten bleiben.

   >[!NOTE]
   >
   > Bei älteren Formularen war die Spalte &quot;teamId&quot;nicht vorhanden. Die &quot;teamId&quot;wurde in die Kanalspalte eingeschlossen, getrennt durch &quot;#&quot;oder &quot;/&quot;.

1. Geben Sie einen beliebigen Titel ein und geben Sie unter den Feldern die Namen der Felder ein, die in der Slack-Benachrichtigung angezeigt werden sollen. Jede Überschrift sollte durch ein Komma getrennt werden (z. B. Name, E-Mail).


Das Blatt ist jetzt so eingerichtet, dass es Daten erhält. Sie können [Vorschau des Formulars mit dem Block Adaptives Formular](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) oder [POST-Anfragen verwenden](#use-admin-apis-to-send-data-to-your-sheet) , um Daten an die Tabelle zu senden.

>[!WARNING]
>
>  Die &quot;freigegebenen Standard&quot;-Tabellen dürfen niemals persönlich identifizierbare Informationen oder vertrauliche Daten enthalten, die Ihnen nicht mit dem öffentlichen Zugriff vertraut sind.

## Daten an Ihr Blatt senden {#send-data-to-your-sheet}

Nachdem das Blatt auf den Empfang von Daten eingestellt wurde, können Sie [Vorschau des Formulars mit dem Block Adaptives Formular](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) oder [Admin-APIs verwenden](#use-admin-apis-to-send-data-to-your-sheet) , um Daten an die Tabelle zu senden.

### Verwenden von Admin-APIs zum Senden von Daten an Ihr Blatt

Sie können POST-Anfragen direkt an Ihr Formular senden, indem Sie hlx.page, hlx.live oder Ihre Produktionsdomäne verwenden, um Daten zu senden.


```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> Die URL sollte nicht über die Erweiterung .json verfügen. Sie müssen das Arbeitsblatt veröffentlichen, damit POST-Vorgänge in `.live` oder in der Produktionsdomäne.

#### Formulardaten formatieren

Es gibt verschiedene Möglichkeiten, die Formulardaten im Hauptteil der POST zu formatieren. Sie können Folgendes verwenden:

* Array von `name:value` -Paare:

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

  Beispiel

  ```JSON
  curl -s -i -X POST 'https://main--portal--wkndforms.hlx.page/contact-us' \
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



* ein Objekt mit `key:value` -Paare:

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

  Beispiel:

  ```JSON
  curl -s -i -X POST 'https://admin.hlx.page/form/wkndforms/portal/main/contact-us.json' \
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

* URL-kodiert (`x-www-form-urlencoded`) body (mit `content-type` -Kopfzeile auf `application/x-www-form-urlencoded`)

  ```Shell
  'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'
  ```

  Beispiel:

  ```Shell
  curl -s -i -X POST \
    -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
    https://main--portal--wkndforms.hlx.live/contact-us
  ```

Als Nächstes können Sie die Dankesnachricht anpassen, [Konfigurieren einer Dankeseite](/help/edge/docs/forms/thank-you-page-form.md)oder [set redirects](/help/edge/docs/forms/thank-you-page-form.md).

## Mehr anzeigen

* [Erstellen und Anzeigen einer Vorschau eines Formulars](/help/edge/docs/forms/create-forms.md)
* [Formular zum Senden von Daten aktivieren](/help/edge/docs/forms/submit-forms.md)
* [Veröffentlichen eines Formulars auf der Siteseite](/help/edge/docs/forms/publish-eds-forms.md)
* [Hinzufügen von Überprüfungen zu Formularfeldern](/help/edge/docs/forms/validate-forms.md)
* [Designs und Formularstil ändern](/help/edge/docs/forms/style-theme-forms.md)
