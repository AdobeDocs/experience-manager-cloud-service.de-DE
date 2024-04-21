---
title: Erstellen eines Formulars mit dokumentbasiertem Authoring für AEM Forms Edge Delivery Service
description: Perfekte Formulare im Handumdrehen! ⚡ AEM Forms Edge Delivery + dokumentbasiertes Authoring = atemberaubende Geschwindigkeit und SEO-freundliche Formulare für zufriedenere Benutzende und Suchmaschinen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: 0ad9f349c997c35862e4f571b4741ed4c0c947e2
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 100%

---


# Erstellen eines Formulars mit dokumentbasiertem Authoring für AEM Forms Edge Delivery Service

Im heutigen digitalen Zeitalter ist die Erstellung benutzerfreundlicher Formulare für jedes Unternehmen schlicht unverzichtbar. Mit dem dokumentbasierten Authoring von AEM Forms Edge Delivery können Sie Formulare mit vertrauten Tools wie Word oder Google Docs erstellen. Die Daten dieser Formulare werden dann direkt an eine Microsoft Excel- oder Google Tabellen-Datei übermittelt, sodass Sie ein dynamisches Ökosystem und robuste APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint verwenden können, um die übermittelten Daten einfach zu verarbeiten oder einen bestehenden Business-Workflow zu initiieren.

Diese Anleitung führt Sie durch die folgenden Schritte:

* Vorbereitung des Arbeitsblatts: Erfahren Sie, wie Sie eine Excel- oder Google Tabellen-Datei für die Datenerfassung einrichten und Formularfelder hinzufügen.
* Datenversand an Ihr Blatt: Erfahren Sie, wie Sie Daten mithilfe von POST-Anfragen an Ihr Blatt senden können.
* Veröffentlichung des Formulars: Integrieren Sie Ihr Formular in Ihre AEM Sites-Seite oder veröffentlichen Sie es als eigenständige Seite.

Diese Anleitung ermöglicht es sowohl Neulingen als auch Profis, ansprechende, funktionale Formulare zu erstellen, die bei Benutzenden gut ankommen. Machen wir uns nun gemeinsam auf den Weg, hin zu einer effizienten Formularerstellung.

## Bevor Sie beginnen

`WIP`

## Vorbereiten des Arbeitsblatts für den Datenempfang

1. Erstellen Sie eine Microsoft Excel-Arbeitsmappe oder eine Google-Tabelle an einer beliebigen Stelle im AEM Edge Delivery-Projektverzeichnis auf Microsoft OneDrive oder Google Drive. In diesem Dokument wird eine Google-Tabelle namens `contact-us.xlsx` verwendet. Sie finden sie im Stammverzeichnis eines Adobe Experience Manager(AEM)-Projekts.

1. Stellen Sie sicher, dass die oder der für Ihr Projekt konfigurierte AEM-Benutzerin oder AEM-Benutzer (z. B. helix@adobe.com) über Bearbeitungsberechtigungen für das Blatt verfügt.

1. Öffnen Sie die von Ihnen erstellte Arbeitsmappe und ändern Sie den Namen des Standardblatts in „incoming“.

   >[!NOTE]
   >
   > Wenn das Blatt „incoming“ nicht vorhanden ist, sendet AEM keine Daten an diese Arbeitsmappe.

1. Zeigen Sie eine Vorschau des Blattes im Sidekick an.

   >[!NOTE]
   >
   >Auch wenn Sie das Blatt zuvor in einer Vorschau angezeigt haben, müssen Sie es dort erneut aufrufen, nachdem Sie das Blatt „incoming“ zum ersten Mal erstellt haben.

1. Bereiten Sie das Blatt vor, indem Sie Kopfzeilen hinzufügen, die mit den eingegebenen Daten übereinstimmen. Im folgenden Beispiel werden Felder für das Formular „contact-us“ angezeigt:

   ![Felder für das Formular „contact-us“](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

   Dies ist manuell oder mithilfe einer POST-Anfrage an die Formularroute im AEM Admin-Dienst möglich. Der Admin-Dienst prüft die Daten im POST-Hauptteil und generiert die entsprechenden Kopfzeilen, Tabellen und Blätter, die für eine effektive Datenaufnahme und optimale Nutzung des Formulardienstes erforderlich sind.

   Informationen dazu, wie Sie die POST-Anfrage zum Einrichten Ihres Blatts formatieren, finden Sie in der [Dokumentation zur Admin-API](https://www.hlx.live/docs/admin.html#tag/form). Sehen Sie sich außerdem das folgende Beispiel an:

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
   
   {"rowCount":2,"columns":["Email","Name","Subject","Message","Phone","Company","Country","PreferredContactMethod","SubscribeToNewsletter"]}%
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

Die oben genannte POST-Anfrage liefert Beispieldaten, einschließlich beider Formularfelder und entsprechender Beispielwerte. Der Admin-Dienst nutzt diese Daten, um das Formular einzurichten.

Der Admin-Dienst empfiehlt, dass Sie das Blatt konfigurieren. Wenn Sie aber die Kopfzeilen lieber manuell erstellen möchten, finden Sie unter [Manuelle Einrichtung von Formularblättern](https://www.hlx.live/docs/manual-forms-sheet-setup) weitere Informationen dazu.

Wenn Sie die POST-Anfrage an den Admin-Dienst senden, werden Sie die folgenden Änderungen in Ihrer Arbeitsmappe feststellen:

* Ihrer Excel-Arbeitsmappe bzw. Google-Tabelle wird ein neues Blatt mit dem Namen „shared-default“ hinzugefügt. Die im Blatt „shared-default“ vorhandenen Daten werden abgerufen, wenn eine GET-Anfrage an das Blatt erfolgt. Dieses Blatt eignet sich perfekt für die Verwendung von Tabellenformeln, mit denen sich die eingehenden Daten zusammenfassen und so auch in anderen Kontexten nutzen lassen.

  Unter keinen Umständen sollte das Blatt „shared-default“ personenbezogene oder vertrauliche Daten enthalten, die nicht der Öffentlichkeit zugänglich gemacht werden sollen.

* Ein Blatt mit dem Namen „Slack“ wird Ihrer Excel-Arbeitsmappe oder Ihrer Google-Tabelle hinzugefügt. In dieser Tabelle können Sie automatische Benachrichtigungen für einen bestimmten Slack-Kanal konfigurieren, sobald neue Daten in Ihre Tabelle aufgenommen werden. Derzeit unterstützt AEM ausschließlich Benachrichtigungen an die Organisation AEM Engineering Slack und die Organisation Adobe Enterprise Support.

   1. Um Slack-Benachrichtigungen einzurichten, geben Sie die „teamId“ des Slack-Arbeitsbereichs und den „Kanalnamen“ bzw. die „ID“ ein. Sie können auch den Slack-Bot (mit dem Debugging-Befehl) nach der „teamId“ und der „Kanal-ID“ fragen. Die Verwendung der „Kanal-ID“ anstelle des „Kanalnamens“ ist vorzuziehen, da sie bei Kanalumbenennungen erhalten bleibt.

      >[!NOTE]
      >
      > Bei älteren Formularen war die Spalte „teamId“ nicht vorhanden. Die „teamId“ wurde in die Kanalspalte eingeschlossen, getrennt durch „#“ oder „/“.

   1. Geben Sie einen beliebigen Titel und unter den Feldern die Namen der Felder ein, die in der Slack-Benachrichtigung angezeigt werden sollen. Jede Überschrift sollte durch ein Komma getrennt werden (z. B. Name, E-Mail).

Das Blatt ist jetzt für den Empfang von Daten eingerichtet und Sie können POST-Anfragen mithilfe von hlx.page, hlx.live oder Ihrer Produktions-Domain direkt an das Blatt senden.


## Senden von Daten an Ihr Blatt {#send-data-to-your-sheet}

Nachdem das Blatt auf den Empfang von Daten eingestellt wurde, können Sie POST-Anfragen mithilfe von hlx.page, hlx.live oder Ihrer Produktions-Domain direkt an das Blatt richten, um Daten zu senden.

```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> Die URL sollte keine .json-Erweiterung enthalten. Sie müssen das Blatt veröffentlichen, damit POST-Vorgänge in „.live“ oder der Produktions-Domain funktionieren.

### Formatieren von Daten für EDS-Formulare

Es gibt verschiedene Möglichkeiten, die Formulardaten im POST-Hauptteil zu formatieren.

* Array von Name-Wert-Paaren:

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
              { "name": "message", "value": "I have some questions about your products." },
              { "name": "phone", "value": "123-456-7890" },
              { "name": "company", "value": "Example Inc." },
              { "name": "country", "value": "United States" },
              { "name": "preferred_contact_method", "value": "Email" },
              { "name": "newsletter_subscribe", "value": true }
              ]
          }'
  
* Objekt mit Schlüssel-Wert-Paaren

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

* `x-www-form-urlencoded` body (`content-type`-Header muss auf `application/x-www-form-urlencoded` festgelegt sein)
&#39;firstname=bruce&amp;lastname=banner&amp;email=bruce%40example.com&#39;



