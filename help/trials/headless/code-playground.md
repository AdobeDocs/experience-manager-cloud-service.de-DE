---
title: Rendern Sie Ihren Inhalt in einer einfachen App
description: Erfahren Sie, wie Sie JSON-Inhalte mit einer CodePen-App und dem AEM Headless-Client für JavaScript aus Ihrer Testumgebung abrufen.
hidefromtoc: true
index: false
exl-id: b7dc70f2-74a2-49f7-ae7e-776eab9845ae
source-git-commit: b9b9cf79173a0ae486bd5d8fcbc1fec48c0b2bc8
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 96%

---


# Rendern Sie Ihren Inhalt in einer einfachen App {#render-content-simple-app}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="Rendern von Inhalten in einer einfachen App"
>abstract="Untersuchen Sie, wie Sie JSON-Inhalte mit einer CodePen-App und dem AEM Headless-Client für JavaScript aus Ihrer Testumgebung abrufen können."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="Starten der CodePen-Beispiel-App"
>abstract="Dieses Handbuch führt Sie durch die Abfrage von JSON-Daten aus Ihrer Testumgebung in eine einfache JavaScript-Web-Anwendung. Es werden die Inhaltsfragmente verwendet, die in den früheren Lernmodulen modelliert und erstellt worden sind. Lesen Sie bei Bedarf zuerst diese Handbücher, bevor Sie mit dem vorliegenden Handbuch beginnen."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="In diesem Modul haben Sie erfahren, wie Sie mit dem AEM Headless-Client für JavaScript JSON-Daten aus Ihrer Testumgebung abrufen können, indem Sie persistierte GraphQL-Abfragen verwenden.<br><br>Jetzt wissen Sie, wie dieser Client verwendet wird, um Daten von innerhalb Ihrer eigenen Web-Anwendung nutzen zu können."
>abstract=""

## CodePen {#codepen}

CodePen ist ein Online-Code-Editor und Spielplatz für die Front-End-Webentwicklung. Dadurch können Sie HTML-, CSS- und JavaScript-Code in Ihrem Browser schreiben und die Ergebnisse Ihrer Arbeit fast sofort sehen. Sie können Ihre Arbeit auch speichern und mit anderen teilen. Adobe hat eine App in CodePen erstellt, mit der Sie JSON-Daten aus Ihrer Testumgebung mit dem [AEM Headless-Client für JavaScript](https://github.com/adobe/aem-headless-client-js) abrufen können. Sie können diese App unverändert verwenden oder sie in Ihr eigenes CodePen-Konto einbinden, um sie weiter anzupassen.

Wenn Sie in der Testversion auf die Schaltfläche **CodePen-Beispielanwendung starten** klicken, gelangen Sie zur App in CodePen. Die App dient als minimales Beispiel für das Abrufen von JSON-Daten mit JavaScript. Die Beispielanwendung ist so konzipiert, dass alle zurückgegebenen JSON-Inhalte gerendert werden, unabhängig von der Struktur des zugrunde liegenden Inhaltsfragmentmodells. Standardmäßig ruft die App Daten aus einer persistierten `aem-demo-assets`-Abfrage ab, die in Ihrer Testumgebung enthalten ist. Es sollte eine JSON-Antwort ähnlich der folgenden angezeigt werden:

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

Wenn stattdessen ein Fehler angezeigt wird, überprüfen Sie die Browser-Konsole auf weitere Details oder wenden Sie sich an [per E-Mail](mailto:aem-headless-trials-support@adobe.com?subject=AEM%20Trials%20support%20request).

Nachdem Sie nun ein wenig über CodePen wissen, konfigurieren Sie als Nächstes die App, um Daten aus der persistierten Abfrage abzurufen, die Sie in einem vorherigen Modul erstellt haben.

## JavaScript-Code-Anleitung {#code-walkthrough}

Der Bereich **JS** auf der rechten Seite in CodePen enthält das JavaScript der Beispiel-App. Ab Zeile 2 importieren Sie den AEM Headless-Client für JavaScript aus dem Skypack CDN. Skypack wird verwendet, um die Entwicklung ohne einen Build-Schritt zu erleichtern, aber Sie können auch den AEM Headless Client mit NPM oder Yarn in Ihren eigenen Projekten verwenden. In der [README](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) finden Sie weitere Details zur Verwendung.

```javascript
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

In Zeile 6 wurden Ihre Details zum Veröffentlichungs-Host aus dem Abfrageparameter `publishHost` gelesen. Dieser Parameter ist der Host, von dem der AEM Headless-Client Daten abruft. Diese Funktionalität würde normalerweise in Ihrer App codiert, aber wir verwenden einen Abfrageparameter, um die Arbeit der CodePen-App mit verschiedenen Umgebungen zu erleichtern.

Sie konfigurieren nun den AEM Headless-Client in Zeile 12:

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
>Die **serviceURL** ist so eingestellt, dass eine Adobe I/O Runtime-Proxy-Funktion verwendet wird, um CORS-Probleme zu vermeiden. Dieser Proxy ist für Ihre eigenen Projekte nicht erforderlich, aber er ist notwendig, damit die CodePen-App mit Ihrer Testumgebung funktioniert. Die Proxy-Funktion ist so konfiguriert, dass sie den Wert **publishHost** verwendet, der im Abfrageparameter angegeben wurde.

Schließlich wird die Funktion `fetchJsonFromGraphQL()` verwendet, um die Abrufanfrage mit dem AEM Headless-Client durchzuführen. Sie wird jedes Mal aufgerufen, wenn der Code geändert wird, oder kann durch Anklicken des Links **Erneut abrufen** ausgelöst werden. Der eigentliche `aemHeadlessClient.runPersistedQuery(..)`-Aufruf erfolgt in Zeile 34. Ein wenig später werden Sie die Art und Weise ändern, wie diese JSON-Daten gerendert werden, aber für den Moment drucken Sie sie einfach mit der Funktion `resultToPreTag(queryResult)` in den Div `#output`.

## Abrufen von Daten aus Ihrer persistierten Abfrage {#use-persisted-query}

In Zeile 25 geben Sie an, aus welcher persistierten GraphQL-Abfrage die App Daten abrufen soll. Der Name der persistierten Abfrage ist eine Kombination aus dem Namen des Endpunkts (d. h. `your-project` oder `aem-demo-assets`), gefolgt von einem Schrägstrich und dem Namen der Abfrage. Wenn Sie die früheren Modulanweisungen genau befolgt haben, befindet sich die von Ihnen erstellte persistierte Abfrage im Endpunkt `your-project`.

1. Aktualisieren Sie die Variable `persistedQueryName` zur Verwendung der persistierten Abfrage, die Sie im vorherigen Modul erstellt haben. Wenn Sie dem Benennungsvorschlag gefolgt wären, hätten Sie eine persistierte Abfrage mit dem Namen `adventure-list` im Endpunkt `your-project` erstellt und die Variable `persistedQueryName` auf `your-project/adventure-list` gesetzt:

   ```javascript
   //
   // TODO: Use your persisted query here
   //
   persistedQueryName = 'your-project/adventure-list';
   ```

1. Sobald diese Änderung vorgenommen wurde, sollte die App automatisch aktualisiert werden und die rohe JSON-Antwort aus Ihrer persistierten Abfrage in den `#output`-Div drucken. Wenn eine Fehlermeldung angezeigt wird, überprüfen Sie die Konsole auf weitere Details. Reichweite [per E-Mail](mailto:aem-headless-trials-support@adobe.com?subject=AEM%20Trials%20support%20request) wenn Sie noch Probleme mit diesem Schritt haben.

1. Enthält dieses JSON die genauen Eigenschaften, die Ihre App benötigt? Falls nicht, gehen Sie zurück zum Lernhandbuch [Extrahieren von Inhalten mit der GraphQL-API](https://experience.adobe.com/experiencemanager/learn/extract_content_using_graphql), um Änderungen vorzunehmen. Vergessen Sie nicht, Ihre Abfrage zu speichern und zu veröffentlichen, sobald Sie damit fertig sind.

## Änderung von JSON-Rendering {#change-rendering}

Das JSON wird als solches in ein `pre`-Tag gerendert, was nicht sehr kreativ ist. Sie können CodePen so umstellen, dass stattdessen die Funktion `resultToDom()` verwendet wird, um zu veranschaulichen, wie die JSON-Antwort iteriert werden kann, um ein interessanteres Ergebnis zu erzielen.

1. Um diese Änderung vorzunehmen, kommentieren Sie Zeile 37 aus und entfernen Sie den Kommentar aus Zeile 40:

   ```javascript
   // Output the results to a pre tag
   //resultToPreTag(queryResult);
   
   // Alternatively, build a colorful div structure with the JSON results and render images inline
   resultToDom(queryResult);
   ```

1. Diese Funktion rendert auch alle Bilder, die in der JSON-Antwort als `img`-Tag enthalten sind. Wenn die von Ihnen erstellten **Abenteuer**-Inhaltsfragmente keine Bilder enthalten, können Sie versuchen, die persistierte Abfrage `aem-demo-assets/adventures-all` zu verwenden, indem Sie die Zeile 25 ändern:

   ```javascript
   persistedQueryName = 'aem-demo-assets/adventures-all';
   ```

Diese Abfrage liefert eine JSON-Antwort, die Bilder enthält, und die Funktion `resultToDom()` rendert sie inline.

![Ergebnis der Abfrage „adventures-all“ und der Rendering-Funktion „resultToDom“](assets/do-not-localize/adventures-all-query-result.png)

Nachdem Sie die Arbeit zum Erstellen der Modelle und Abfragen abgeschlossen haben, kann Ihr Content-Team die Aufgabe problemlos übernehmen. Im nächsten Modul zeigen Sie den Ablauf für Inhaltsautorinnen und -autoren an.
