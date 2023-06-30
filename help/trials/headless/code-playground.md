---
title: Rendern Sie Ihren Inhalt in einer einfachen App
description: Erfahren Sie, wie Sie JSON-Inhalte mit einer CodePen-App und dem AEM Headless-Client für JavaScript aus Ihrer Testumgebung abrufen.
hidefromtoc: true
index: false
exl-id: b7dc70f2-74a2-49f7-ae7e-776eab9845ae
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 58%

---


# Rendern Sie Ihren Inhalt in einer einfachen App {#render-content-simple-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="Rendern von Inhalten in einer einfachen App"
>abstract="Erfahren Sie, wie Sie JSON-Inhalte mit einer CodePen-App und dem AEM Headless-Client für JavaScript aus Ihrer Testumgebung abrufen."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="Starten der CodePen-Beispiel-App"
>abstract="Dieses Handbuch führt Sie durch die Abfrage von JSON-Daten aus Ihrer Testumgebung in eine einfache JavaScript-Web-Anwendung. Es werden die Inhaltsfragmente verwendet, die in den früheren Lernmodulen modelliert und erstellt worden sind. Bearbeiten Sie bei Bedarf zuerst diese Handbücher, bevor Sie mit dem vorliegenden Handbuch beginnen."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="In diesem Modul haben Sie erfahren, wie Sie mit dem AEM Headless-Client für JavaScript JSON-Daten aus Ihrer Testumgebung abrufen können, indem Sie persistierte GraphQL-Abfragen verwenden.<br><br>Jetzt wissen Sie, wie dieser Client verwendet wird, um Daten von innerhalb Ihrer eigenen Web-Anwendung nutzen zu können."
>abstract=""

## CodePen {#codepen}

CodePen ist ein Online-Code-Editor und Spielplatz für die Front-End-Webentwicklung. Damit können Sie HTML-, CSS- und JavaScript-Code in Ihren Browser schreiben und die Ergebnisse Ihrer Arbeit fast sofort sehen. Sie können Ihre Arbeit auch speichern und für andere freigeben. Adobe hat eine App in CodePen erstellt, mit der Sie JSON-Daten aus Ihrer Testumgebung mithilfe der [AEM Headless-Client für JavaScript](https://github.com/adobe/aem-headless-client-js). Sie können diese App unverändert verwenden oder sie in Ihr eigenes CodePen-Konto einbinden, um sie weiter anzupassen.

Klicken Sie auf **Starten der Beispielanwendung &quot;CodePen&quot;** -Schaltfläche in der Testversion führt Sie zur App in CodePen. Die App dient als minimales Beispiel für das Abrufen von JSON-Daten mit JavaScript. Die Beispielanwendung ist so konzipiert, dass alle zurückgegebenen JSON-Inhalte gerendert werden, unabhängig von der Struktur des zugrunde liegenden Inhaltsfragmentmodells. Standardmäßig ruft das Programm Daten von einem `aem-demo-assets` persistente Abfrage, die in Ihrer Testumgebung enthalten ist. Es sollte eine JSON-Antwort ähnlich der folgenden angezeigt werden:

```json
{
  "data": {
    "adventureList": {
      "items": [
        {
          "_path": "/content/dam/aem-demo-assets/en/adventures/bali-surf-camp/bali-surf-camp",
          "title": "Bali Surf Camp",
          "price": "$5000 USD",
          ...
```

Wenn stattdessen ein Fehler angezeigt wird, überprüfen Sie die Browser-Konsole auf weitere Details oder kontaktieren Sie uns [auf Slack](https://adobe-dx-support.slack.com).

Nachdem Sie nun ein wenig über CodePen wissen, konfigurieren Sie als Nächstes die App, um Daten aus der persistierten Abfrage abzurufen, die Sie in einem vorherigen Modul erstellt haben.

## JavaScript-Code-Anleitung {#code-walkthrough}

Die **JS** rechts neben CodePen das JavaScript der Beispielanwendung enthält. Ab Zeile 2 importieren Sie den AEM Headless Client für JavaScript aus dem Skypack CDN. Skypack wird verwendet, um die Entwicklung ohne einen Build-Schritt zu erleichtern, aber Sie können auch den AEM Headless Client mit NPM oder Yarn in Ihren eigenen Projekten verwenden. In der [README](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) finden Sie weitere Details zur Verwendung.

```javascript
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

In Zeile 6 wurden Ihre Details zum Veröffentlichungs-Host aus dem `publishHost` Abfrageparameter. Dieser Parameter ist der Host, von dem der AEM Headless-Client Daten abruft. Diese Funktion wird normalerweise in Ihrer App codiert, Sie verwenden jedoch einen Abfrageparameter, um die Arbeit der CodePen-App mit verschiedenen Umgebungen zu erleichtern.

Sie konfigurieren den AEM Headless-Client in Zeile 12:

```javascript
const aemHeadlessClient = new AdobeAemHeadlessClientJs({
  // Use a proxy to avoid CORS issues
  serviceURL: 'https://102588-505tanocelot.adobeioruntime.net/api/v1/web/aem/proxy',
  headers: {
    'aem-url': publishHost
  }
});
```

>[!NOTE]
>
>Die **serviceURL** ist so eingestellt, dass eine Proxy-Adobe I/O Runtime-Funktion verwendet wird, um CORS-Probleme zu vermeiden. Dieser Proxy ist nicht für Ihre eigenen Projekte erforderlich, ist aber erforderlich, damit die CodePen-App mit Ihrer Testumgebung funktioniert. Die Proxy-Funktion ist so konfiguriert, dass sie den Wert **publishHost** verwendet, der im Abfrageparameter angegeben wurde.

Schließlich wird die Funktion `fetchJsonFromGraphQL()` verwendet, um die Abrufanfrage mit dem AEM Headless-Client durchzuführen. Sie wird jedes Mal aufgerufen, wenn der Code geändert wird, oder kann durch Anklicken des Links **Erneut abrufen** ausgelöst werden. Der eigentliche `aemHeadlessClient.runPersistedQuery(..)`-Aufruf erfolgt in Zeile 34. Ein wenig später ändern Sie die Art und Weise, wie diese JSON-Daten gerendert werden, drucken sie aber zunächst in die `#output` div mit dem `resultToPreTag(queryResult)` -Funktion.

## Abrufen von Daten aus Ihrer persistierten Abfrage {#use-persisted-query}

In Zeile 25 geben Sie an, aus welcher von GraphQL gespeicherten Abfrage die App Daten abrufen soll. Der persistente Abfragename ist eine Kombination aus dem Namen des Endpunkts (d. h. `your-project` oder `aem-demo-assets`), gefolgt von einem Schrägstrich und dem Namen der Abfrage. Wenn Sie die vorherigen Modulanweisungen genau befolgt haben, befindet sich die von Ihnen erstellte persistente Abfrage im `your-project` -Endpunkt.

1. Aktualisieren Sie die `persistedQueryName` verwendet, sodass die von Ihnen im vorherigen Modul erstellte persistente Abfrage verwendet wird. Wenn Sie dem Benennungsvorschlag gefolgt wären, hätten Sie eine persistierte Abfrage mit dem Namen `adventure-list` im Endpunkt `your-project` erstellt und die Variable `persistedQueryName` auf `your-project/adventure-list` gesetzt:

   ```javascript
   //
   // TODO: Use your persisted query here
   //
   persistedQueryName = 'your-project/adventure-list';
   ```

1. Sobald diese Änderung vorgenommen wurde, sollte die App automatisch aktualisiert werden und die rohe JSON-Antwort aus Ihrer persistierten Abfrage in den `#output`-Div drucken. Wenn eine Fehlermeldung angezeigt wird, überprüfen Sie die Konsole auf weitere Details. Kontaktieren Sie uns [auf Slack](https://adobe-dx-support.slack.com), wenn Sie noch Probleme mit diesem Schritt haben.

1. Enthält dieses JSON die genauen Eigenschaften, die Ihre App benötigt? Falls nicht, gehen Sie zurück zum Lernhandbuch [Extrahieren von Inhalten mit der GraphQL-API](https://experience.adobe.com/experiencemanager/learn/extract_content_using_graphql), um Änderungen vorzunehmen. Vergessen Sie nicht, Ihre Abfrage zu speichern und zu veröffentlichen, sobald Sie damit fertig sind.

## Änderung von JSON-Rendering {#change-rendering}

Die JSON wird unverändert in einer `pre` -Tag, was nicht zu kreativ ist. Sie können CodePen zur Verwendung der `resultToDom()` -Funktion verwenden, um zu veranschaulichen, wie die JSON-Antwort wiederholt werden kann, um ein interessanteres Ergebnis zu erzielen.

1. Um diese Änderung vorzunehmen, kommentieren Sie Zeile 37 aus und entfernen Sie den Kommentar aus Zeile 40:

   ```javascript
   // Output the results to a pre tag
   //resultToPreTag(queryResult);
   
   // Alternatively, build a colorful div structure with the JSON results and render images inline
   resultToDom(queryResult);
   ```

1. Diese Funktion rendert alle Bilder, die in der JSON-Antwort enthalten sind, als `img` -Tag. Wenn die von Ihnen erstellten **Abenteuer**-Inhaltsfragmente keine Bilder enthalten, können Sie versuchen, die persistierte Abfrage `aem-demo-assets/adventures-all` zu verwenden, indem Sie die Zeile 25 ändern:

   ```javascript
   persistedQueryName = 'aem-demo-assets/adventures-all';
   ```

Diese Abfrage liefert eine JSON-Antwort mit Bildern und der `resultToDom()` rendert sie inline.

![Ergebnis der Abfrage „adventures-all“ und der Rendering-Funktion „resultToDom“](assets/do-not-localize/adventures-all-query-result.png)

Nachdem Sie die Arbeit zum Erstellen der Modelle und Abfragen abgeschlossen haben, kann Ihr Content-Team die Aufgabe problemlos übernehmen. Im nächsten Modul zeigen Sie den Ablauf des Inhaltsautors an.
