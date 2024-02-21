---
title: Erstellen eines Formulars mit dokumentbasiertem Authoring für den AEM Forms Edge Delivery Service
description: Handwerkliche perfekte Formen, schnell! ⚡ AEM Forms Edge Delivery + doc-basiertes Authoring = Blazing Speed & SEO-freundliche Formulare für glücklichere Benutzer und Suchmaschinen.
feature: Edge Delivery Services
hide: true
hidefromtoc: true
source-git-commit: f2752673dcaa0762bb55719cee23765aa8ecde96
workflow-type: tm+mt
source-wordcount: '889'
ht-degree: 0%

---


# Erstellen eines Formulars mit dokumentbasiertem Authoring für den AEM Forms Edge Delivery Service

Im heutigen digitalen Zeitalter ist die Erstellung benutzerfreundlicher Formulare für jedes Unternehmen von entscheidender Bedeutung. Mit dem dokumentbasierten Authoring von AEM Forms Edge Delivery können Sie Formulare mit vertrauten Tools wie Word- oder Google-Dokumenten erstellen. Diese Formulare senden Daten direkt an eine Microsoft Excel- oder Google Tabellen-Datei, sodass Sie ein dynamisches Ökosystem und robuste APIs von Google Tabellen, Microsoft Excel und Microsoft SharePoint verwenden können, um die übermittelten Daten einfach zu verarbeiten oder einen bestehenden Geschäftsarbeitsablauf zu initiieren.

Dieser Leitfaden führt Sie durch:

* Vorbereitung des Arbeitsblatts: Erfahren Sie, wie Sie eine Excel- oder Google Tabellen-Datei für die Datenerfassung einrichten und Formularfelder hinzufügen.
* Daten an Ihr Blatt senden: Erfahren Sie, wie Sie Daten mithilfe von POST-Anforderungen an Ihr Blatt senden können.
* Formular veröffentlichen: Integrieren Sie Ihr Formular auf Ihrer AEM Sites-Seite oder veröffentlichen Sie es als eigenständige Seite.

Ob Anfänger oder Profi - dieser Leitfaden ermöglicht es Ihnen, schöne, funktionale Formulare zu erstellen, die von Benutzern gern genutzt werden. Entsperren wir eine effiziente Formularerstellung - tauchen Sie jetzt ein!

## Bevor Sie beginnen

`WIP`

## Vorbereitung des Arbeitsblatts auf den Empfang von Daten

1. Erstellen Sie eine Microsoft Excel-Arbeitsmappe oder ein Google-Blatt an einer beliebigen Stelle im Projektverzeichnis für die AEM Edge-Bereitstellung auf Microsoft OneDrive oder Google Drive. Dieses Dokument verwendet ein Google-Blatt mit dem Namen `contact-us.xlsx`, der sich im Stammverzeichnis eines Adobe Experience Manager-Projekts (AEM) befindet.

1. Stellen Sie sicher, dass der für Ihr Projekt konfigurierte AEM-Benutzer (z. B. helix@adobe.com) über Bearbeitungsberechtigungen für das Arbeitsblatt verfügt.

1. Öffnen Sie die von Ihnen erstellte Arbeitsmappe und ändern Sie den Namen des Standardblatts in &quot;Eingehend&quot;.

   >[!NOTE]
   >
   > Wenn das &quot;eingehende&quot; Blatt nicht vorhanden ist, sendet AEM keine Daten an diese Arbeitsmappe.

1. Zeigen Sie eine Vorschau der Tabelle im Sidekick an.

   >[!NOTE]
   >
   >Auch wenn Sie das Blatt zuvor in der Vorschau angezeigt haben, müssen Sie es erneut in der Vorschau anzeigen, nachdem Sie das &quot;eingehende&quot;Blatt zum ersten Mal erstellt haben.

1. Bereiten Sie das Blatt vor, indem Sie Kopfzeilen hinzufügen, die mit den eingegebenen Daten übereinstimmen. Im folgenden Beispiel werden Felder für ein Formular &quot;contact-us&quot;angezeigt:

   ![Felder für ein Kontakt-Formular](/help/edge/assets/contact-us-form-excel-sheet-fields.png)

   Sie können dies manuell oder mithilfe einer POST-Anfrage an die Formularroute im AEM Admin-Dienst tun. Der Administratordienst prüft die Daten im Hauptteil der POST und generiert die entsprechenden Kopfzeilen, Tabellen und Arbeitsblätter, die erforderlich sind, um Daten effektiv zu erfassen und den Formulardienst optimal zu nutzen.

   Informationen zum Formatieren der POST-Anforderung zum Einrichten des Arbeitsblatts finden Sie im Abschnitt [Dokumentation zur Admin-API](https://www.hlx.live/docs/admin.html#tag/form). Sehen Sie sich außerdem das unten bereitgestellte Beispiel an:

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

Die oben genannte POST-Anfrage enthält Beispieldaten, einschließlich der beiden Formularfelder und der entsprechenden Beispielwerte. Diese Daten werden vom Admin-Dienst zur Einrichtung des Formulars verwendet.

Der Admin-Dienst empfiehlt die Konfiguration des Arbeitsblatts. Wenn Sie die Kopfzeilen jedoch manuell erstellen möchten, lesen Sie das Dokument mit dem Titel [Manuelle Einrichtung eines Forms-Arbeitsblatts](https://www.hlx.live/docs/manual-forms-sheet-setup).

Wenn Sie die POST-Anforderung an den Admin-Dienst senden, beachten Sie die folgenden Änderungen in Ihrer Arbeitsmappe:

* Eine neue Tabelle mit dem Namen &quot;shared-default&quot;wird zu Ihrer Excel-Arbeitsmappe oder Google-Tabelle hinzugefügt. Die im Arbeitsblatt &quot;shared-default&quot;vorhandenen Daten werden abgerufen, wenn eine GET zum Arbeitsblatt angefordert wird. Diese Zusammenstellung dient als optimale Position für die Verwendung von Tabellenformeln zur Zusammenfassung der eingehenden Daten, wodurch sie für den Verbrauch in anderen Kontexten förderlich ist.

  Unter keinen Umständen sollte das &quot;shared-default&quot;-Blatt personenbezogene Daten oder vertrauliche Daten enthalten, die Ihnen nicht damit vertraut sind, öffentlich zugänglich zu sein.

* Eine Tabelle mit dem Namen &quot;slack&quot;wird zu Ihrer Excel-Arbeitsmappe oder Ihrem Google-Arbeitsblatt hinzugefügt. In diesem Arbeitsblatt können Sie automatische Benachrichtigungen für einen bestimmten Slack-Kanal konfigurieren, wenn neue Daten in Ihre Tabelle aufgenommen werden. Derzeit unterstützt AEM ausschließlich Benachrichtigungen an die Organisation AEM Engineering Slack und die Adobe Enterprise Support-Organisation.

   1. Um Slack-Benachrichtigungen einzurichten, geben Sie die &quot;teamId&quot; des Slack-Arbeitsbereichs und den &quot;Kanalnamen&quot; bzw. die &quot;ID&quot; ein. Sie können auch den slack-Bot (mit dem Debugging-Befehl) nach der &quot;teamId&quot;und der &quot;channel ID&quot;fragen. Die Verwendung der &quot;Kanal-ID&quot;anstelle des &quot;Kanalnamens&quot;ist vorzuziehen, da Kanalumbenennungen erhalten bleiben.

      >[!NOTE]
      >
      > Bei älteren Formularen war die Spalte &quot;teamId&quot;nicht vorhanden. Die &quot;teamId&quot;wurde in die Kanalspalte eingeschlossen, getrennt durch &quot;#&quot;oder &quot;/&quot;.

   1. Geben Sie einen beliebigen Titel ein und geben Sie unter den Feldern die Namen der Felder ein, die in der Slack-Benachrichtigung angezeigt werden sollen. Jede Überschrift sollte durch ein Komma getrennt werden (z. B. Name, E-Mail).

Das Blatt ist jetzt für den Empfang von Daten eingerichtet und Sie können POST-Anfragen direkt über hlx.page, hlx.live oder Ihre Produktionsdomäne an es senden.


## Daten an Ihr Blatt senden {#send-data-to-your-sheet}

Nachdem das Blatt auf den Empfang von Daten eingestellt wurde, können Sie mithilfe von hlx.page, hlx.live oder Ihrer Produktionsdomäne Anfragen zur POST direkt an es senden, um Daten zu senden.

```JSON
POST https://branch–repo–owner.hlx.(page|live)/email-form
POST https://my-domain.com/email-form
```

>[!NOTE]
>
> Die URL sollte nicht über die Erweiterung .json verfügen. Sie müssen das Arbeitsblatt veröffentlichen, damit POST-Vorgänge auf .live oder in der Produktionsdomäne funktionieren.

### Formulardaten für EDS Forms

Es gibt verschiedene Möglichkeiten, die Formulardaten im Hauptteil der POST zu formatieren.

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

  Beispiel

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

* `x-www-form-urlencoded` body (`content-type` -Kopfzeile muss auf `application/x-www-form-urlencoded`) &#39;firstname=bruce&amp;lastname=banner&amp;email=bruce%40example.com&#39;



