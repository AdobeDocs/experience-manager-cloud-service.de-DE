---
title: Vorbereiten der Tabelle auf die Datenaufnahme
description: Erstellen Sie leistungsstarke Formulare schneller mit Tabellen und adaptiven Forms-Blockfeldern.
feature: Edge Delivery Services
exl-id: 0643aee5-3a7f-449f-b086-ed637ae53b5a
source-git-commit: 5eee563a9a425ef187afed69a8159d8b1298dad7
workflow-type: tm+mt
source-wordcount: '1001'
ht-degree: 63%

---

# Richten Sie Ihre Google Tabellen- oder Microsoft Excel-Dateien ein, um Daten zu akzeptieren


Sobald du [das Formular erstellt und in der Vorschau angezeigt wurde](/help/edge/docs/forms/create-forms.md)ist es an der Zeit, die entsprechende Tabelle so zu aktivieren, dass sie Daten erhält. Sie können das Tabellenblatt manuell aktivieren, um Daten zu akzeptieren, oder Admin-APIs verwenden, um die Akzeptanz von Daten in einer Tabelle zu ermöglichen.

![Dokumentenbasiertes Authoring-Ökosystem](/help/edge/assets/document-based-authoring-workflow-enable-sheet-to-accept-data.png)

<!-- 
>[!VIDEO](https://video.tv.adobe.com/v/3427489?quality=12&learn=on)

-->


## Manuelles Aktivieren des Arbeitsblatts für die Datenaufnahme

So aktivieren Sie die Akzeptanz von Daten im Arbeitsblatt

1. Öffnen Sie die Tabelle, die Ihr Formular hat, und fügen Sie ein neues Blatt hinzu, das Sie in `incoming` umbenennen.

   >[!WARNING]
   >
   > Wenn das Blatt `incoming` nicht vorhanden ist, sendet AEM keine Daten an die Tabelle.

1. Fügen Sie in dieses Blatt eine Tabelle mit dem Namen &quot;take_form&quot;ein. Wählen Sie die Anzahl der Spalten aus, die zum Abgleich der Formularfeldnamen erforderlich sind. Navigieren Sie dann in der Symbolleiste zu Einfügen > Tabelle und klicken Sie auf OK.

1. Ändern Sie den Namen der Tabelle in &quot;take_form&quot;. Um in Microsoft Excel den Tabellennamen zu ändern, wählen Sie die Tabelle aus und klicken Sie auf &quot;Tabellendesign&quot;.

1. Fügen Sie als Nächstes die Formularfeldnamen als Tabellenüberschriften hinzu. Um sicherzustellen, dass die Felder genau gleich sind, können Sie sie aus dem &quot;shared-default&quot;-Blatt kopieren und einfügen.  Wählen Sie in Ihrem &quot;shared-default&quot;-Blatt die Formular-IDs aus, die unter der Spalte &quot;Name&quot; aufgeführt sind, mit Ausnahme des Senden-Felds.

1. Wählen Sie im &quot;eingehenden&quot;Blatt die Option &quot;Sonderzeichen einfügen&quot;> &quot;Zeilen in Spalten exportieren&quot;, um die Feld-IDs als Spaltenüberschriften in dieses neue Blatt zu kopieren. Behalten Sie nur die Felder bei, deren Daten erfasst werden müssen, die ignoriert werden können.

   Jeder Wert in `Name` Spalte `shared-default` Eine Tabelle, die die Senden-Schaltfläche ausschließt, kann als Kopfzeile im `incoming` Blatt. Betrachten Sie beispielsweise das folgende Bild, das Kopfzeilen für ein Kontaktformular veranschaulicht:

   ![Felder für ein Kontaktformular](/help/edge/assets/contact-us-form-excel-sheet-fields.png)



1. Verwenden Sie die AEM Sidekick-Erweiterung, um eine Vorschau der Formularaktualisierungen anzuzeigen. Ihr Blatt kann jetzt eingehende Formularübermittlungen akzeptieren.

   >[!NOTE]
   >
   >Selbst wenn Sie das Blatt zuvor in der Vorschau angezeigt haben, müssen Sie die Vorschau erneut anzeigen, nachdem Sie das Blatt `incoming` zum ersten Mal erstellt haben.


Nachdem die Feldnamen zu dem Blatt `incoming` hinzugefügt wurden, kann Ihr Formular Übermittlungen annehmen. Sie können das Formular in der Vorschau anzeigen und damit Daten an das Blatt senden, das es verwendet.

Nachdem das Blatt für den Empfang von Daten eingerichtet wurde, können Sie [Vorschau des Formulars mit Adaptiver Forms-Block](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) oder [POST-Anfragen verwenden](#use-admin-apis-to-send-data-to-your-sheet) , um Daten an die Tabelle zu senden.

>[!WARNING]
>
>  Die Blätter namens „shared-default“ dürfen niemals persönlich identifizierbare Informationen oder vertrauliche Daten enthalten, für die Sie keinen öffentlichen Zugriff wünschen.

### Verwenden Sie Admin-APIs, um die Akzeptanz von Daten in einer Tabelle zu ermöglichen

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

   Die oben genannte POST-Anfrage enthält Beispieldaten, einschließlich der beiden Formularfelder und ihren entsprechenden Beispielwerten. Diese Daten werden vom Admin-Dienst zum Einrichten des Formulars verwendet.

   Ihr Formular kann jetzt Daten annehmen. Beachten Sie auch die folgenden Änderungen in Ihrer Tabelle:

## Automatische Änderungen am Blatt, sobald die Datenakzeptierung aktiviert wurde.

Nachdem das Arbeitsblatt auf den Empfang von Daten eingestellt wurde, beachten Sie die folgenden Änderungen in Ihrem Arbeitsblatt:

Ein Blatt mit dem Namen „Slack“ wird Ihrer Excel-Arbeitsmappe oder Ihrer Google-Tabelle hinzugefügt. In dieser Tabelle können Sie automatische Benachrichtigungen für einen bestimmten Slack-Kanal konfigurieren, sobald neue Daten in Ihre Tabelle aufgenommen werden. Derzeit unterstützt AEM ausschließlich Benachrichtigungen an die Organisation AEM Engineering Slack und die Organisation Adobe Enterprise Support.

1. Um Slack-Benachrichtigungen einzurichten, geben Sie die „teamId“ des Slack-Arbeitsbereichs und den „Kanalnamen“ bzw. die „ID“ ein. Sie können auch den Slack-Bot (mit dem Debugging-Befehl) nach der „teamId“ und der „Kanal-ID“ fragen. Die Verwendung der „Kanal-ID“ anstelle des „Kanalnamens“ ist vorzuziehen, da sie bei Kanalumbenennungen erhalten bleibt.

   >[!NOTE]
   >
   > Bei älteren Formularen war die Spalte „teamId“ nicht vorhanden. Die „teamId“ wurde in die Kanalspalte eingeschlossen, getrennt durch „#“ oder „/“.

1. Geben Sie einen beliebigen Titel ein und geben Sie unter den Feldern die Namen der Felder ein, die in der Slack-Benachrichtigung angezeigt werden sollen. Jede Überschrift sollte durch ein Komma getrennt werden (z. B. Name, E-Mail).

   >[!WARNING]
   >
   >  Die Blätter namens „shared-default“ dürfen niemals persönlich identifizierbare Informationen oder vertrauliche Daten enthalten, für die Sie keinen öffentlichen Zugriff wünschen.


## Senden von Daten an Ihr Blatt {#send-data-to-your-sheet}

Nachdem das Blatt auf den Empfang von Daten eingestellt wurde, können Sie [Vorschau des Formulars mit Adaptiver Forms-Block](/help/edge/docs/forms/create-forms.md#preview-the-form-using-your-edge-delivery-service-eds-page) oder [Admin-APIs verwenden](#use-admin-apis-to-send-data-to-your-sheet) , um Daten an die Tabelle zu senden.

### Verwenden von Admin-APIs zum Senden von Daten an Ihr Blatt

Sie können POST-Anfragen direkt an Ihr Formular richten, indem Sie hlx.page, hlx.live oder Ihre Produktions-Domain verwenden, um Daten zu senden.


```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> Die URL sollte keine .json-Erweiterung enthalten. Sie müssen das Blatt veröffentlichen, damit POST-Vorgänge in `.live` oder in der Produktions-Domain funktionieren.

#### Formatieren der Formulardaten

Es gibt verschiedene Möglichkeiten, die Formulardaten im POST-Text zu formatieren. Sie können Folgendes verwenden:

* Array von `name:value`-Paaren:

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

  Zum Beispiel

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



* ein Objekt mit `key:value`-Paaren:

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

* URL-kodierter (`x-www-form-urlencoded`) Text (wobei die Kopfzeile `content-type` auf `application/x-www-form-urlencoded` gesetzt ist)

  ```Shell
  'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&Message=I   +have+some+questions+about+your+products.&Phone=123-456-7890&Company=Adobe+Inc.&   Country=United+States&PreferredContactMethod=Email&SubscribeToNewsletter=true'
  ```

  Beispiel:

  ```Shell
  curl -s -i -X POST \
    -d 'Email=kent%40wknd.com&Name=clark&Subject=Regarding+Product+Inquiry&   Message=I+have+some+questions+about+your+products.&Phone=123-456-7890& Company=Adobe+Inc.&Country=United+States&PreferredContactMethod=Email&   SubscribeToNewsletter=true' \
    https://main--portal--wkndforms.hlx.live/contact-us
  ```

Als Nächstes können Sie [Dankesnachricht anpassen](/help/edge/docs/forms/thank-you-page-form.md).

## Siehe auch

{{see-more-forms-eds}}
