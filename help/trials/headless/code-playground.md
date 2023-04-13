---
title: JSON-Inhalt mit JavaScript abrufen
description: Erfahren Sie, wie Sie JSON-Inhalte mit einer CodePen-App und dem AEM Headless-Client für JavaScript aus Ihrer Testumgebung abrufen.
hidefromtoc: true
index: false
source-git-commit: 3aff5ef2fb9ecdd815f0bc1a813d3a3982b4e0ed
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 1%

---


# JSON-Inhalt mit JavaScript abrufen {#fetch-json}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript"
>title="JSON-Inhalt mit JavaScript abrufen"
>abstract="Erfahren Sie, wie Sie JSON-Inhalte mit einer CodePen-App und dem AEM Headless-Client für JavaScript aus Ihrer Testumgebung abrufen."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide"
>title="Starten der Beispielanwendung &quot;CodePen&quot;"
>abstract="Wir haben eine minimale CodePen-App zusammengestellt, um das Abrufen von JSON-Daten aus Ihrer Testumgebung mithilfe von persistenten GraphQL-Abfragen einzuführen.<br><br>Starten Sie das CodePen-Beispiel, indem Sie unten klicken, und befolgen Sie dieses Handbuch, um mehr zu erfahren."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_fetch_json_with_javascript_guide_footer"
>title="In diesem Modul haben Sie erfahren, wie Sie mit dem AEM Headless-Client für JavaScript JSON-Daten aus Ihrer Testumgebung abrufen können, indem Sie persistente GraphQL-Abfragen verwenden.<br><br>Jetzt wissen Sie, wie Sie mit diesem Client Daten aus Ihrer eigenen Webanwendung nutzen können."
>abstract=""

## Einführung {#intro}

Sie beginnen mit der CodePen-App, die als minimales Beispiel für das Abrufen von JSON-Daten mithilfe der [AEM Headless-Client für JavaScript](https://github.com/adobe/aem-headless-client-js). Die Beispielanwendung ist so konzipiert, dass alle zurückgegebenen JSON-Inhalte gerendert werden, unabhängig von der Struktur des zugrunde liegenden Inhaltsfragmentmodells. Die CodePen-App versucht, mit allen aufgetretenen Fehlern ausführlich zu sein, sodass die folgende Fehlermeldung im unteren Bereich der App ausgegeben wird:

```
{
  "status": "Failed to fetch persisted query: your-project/USE-YOUR-QUERY-HERE from publishHost: https://publish-p00000-e12345.adobeaemcloud.com",
  "message": "[AEMHeadless:REQUEST_ERROR] General Request error: Failed to fetch."
}
```

Dieser Fehler wird erwartet, da die App noch nicht für die Verwendung der beibehaltenen Abfrage konfiguriert ist, die Sie in einem vorherigen Modul gespeichert und veröffentlicht haben. In den folgenden Schritten konfigurieren Sie die App, um Daten aus Ihrer spezifischen Abfrage abzurufen.

## Codebeispiel {#code-walkthrough}

Der JS-Bereich (Javascript) auf CodePen enthält die Gehirne der Beispielanwendung. Ab Zeile 2 importieren wir den AEM Headless Client für JavaScript aus dem Skypack CDN. Skypack wird verwendet, um die Entwicklung ohne einen Build-Schritt zu erleichtern, aber Sie können auch den AEM Headless Client mit NPM oder Yarn in Ihren eigenen Projekten verwenden. Sehen Sie sich die Gebrauchsanweisungen im Abschnitt [README](https://github.com/adobe/aem-headless-client-js#aem-headless-client-for-javascript) für weitere Details.

```
import AdobeAemHeadlessClientJs from 'https://cdn.skypack.dev/@adobe/aem-headless-client-js@v3.2.0';
```

In Zeile 6 lesen wir Ihre Details zum Veröffentlichungs-Host aus dem `publishHost` Abfrageparameter. Dies ist der Host, von dem der AEM Headless-Client Daten abruft. Dies würde normalerweise in Ihrer App codiert, aber wir verwenden einen Abfrageparameter, um die Arbeit der CodePen-App mit verschiedenen Umgebungen zu erleichtern.

Wir konfigurieren den AEM Headless Client in Zeile 12, um eine Proxy-Adobe IO Runtime-Funktion zu verwenden, um CORS-Probleme zu vermeiden. Dies ist nicht für Ihre eigenen Projekte erforderlich, aber für die CodePen-App erforderlich, damit sie mit Ihrer Testumgebung funktioniert. Die Proxy-Funktion ist so konfiguriert, dass die Variable `publishHost` -Wert, der im Abfrageparameter angegeben wurde.

```
const aemHeadlessClient = new AdobeAemHeadlessClientJs({
  // Use a proxy to avoid CORS issues
  serviceURL: 'https://102588-505tanocelot.adobeioruntime.net/api/v1/web/aem/proxy',
  headers: {
    'aem-url': publishHost
  }
});
```

Schließlich die Funktion `fetchJsonFromGraphQL()` wird verwendet, um die Abrufanforderung mit dem AEM Headless Client auszuführen. Er wird jedes Mal aufgerufen, wenn der Code geändert wird, oder kann durch Drücken des Links &quot;Neu abrufen&quot;ausgelöst werden. Die tatsächlichen `aemHeadlessClient.runPersistedQuery(..)` -Aufruf erfolgt in Zeile 34. Ein wenig später werden wir die Art und Weise ändern, wie diese JSON-Daten gerendert werden, aber für den Moment drucken wir sie einfach in die `#output` div mit dem `resultToPreTag(queryResult)` -Funktion.

## Abrufen von Daten aus Ihrer gespeicherten Abfrage {#use-persisted-query}

In Zeile 25 geben wir an, aus welcher von GraphQL gespeicherten Abfrage die App Daten abrufen soll. Der persistente Abfragename ist eine Kombination aus dem Namen des Projekts (d. h. `your-project`), gefolgt von einem Schrägstrich und dem Namen der Abfrage.

Aktualisieren Sie die `persistedQueryName` zur Verwendung der gespeicherten Abfrage, die Sie im vorherigen Modul erstellt haben. Wenn Sie dem Benennungsvorschlag genau gefolgt sind, hätten Sie eine persistente Abfrage mit dem Namen `adventures` im `your-project` und legen Sie die `persistedQueryName` zu `your-project/adventures`:

```
//
// TODO: Use your persisted query here
//
persistedQueryName = 'your-project/adventures';
```

Sobald diese Änderung vorgenommen wurde, sollte das Programm automatisch aktualisiert und die rohe JSON-Antwort von Ihrer gespeicherten Abfrage an die `#output` div. Wenn eine Fehlermeldung angezeigt wird, überprüfen Sie die Konsole auf weitere Details.

Enthält dieses JSON die genauen Eigenschaften, die Ihre App benötigt? Wenn nicht, gehen Sie zurück zu Ihrer AEM-Autorenumgebung, zu Tools, zum GraphQL-Abfrage-Editor (oder navigieren Sie zum `/aem/graphiql.html` Pfad) und nehmen Sie Änderungen an Ihrer gespeicherten Abfrage vor. Vergessen Sie nicht, die Abfrage zu speichern und zu veröffentlichen, sobald Sie damit fertig sind.

## JSON-Rendering ändern {#change-rendering}

Derzeit wird die JSON unverändert in einer `pre` -Tag, was nicht sehr kreativ ist. Wir können unseren CodePen für die Verwendung der `resultToDom()` -Funktion verwenden, um zu veranschaulichen, wie die JSON-Antwort wiederholt werden kann, um ein interessanteres Ergebnis zu erzielen.

Um diese Änderung vorzunehmen, kommentieren Sie Zeile 37 aus und entfernen Sie den Kommentar aus Zeile 40:

```
// Output the results to a pre tag
//resultToPreTag(queryResult);

// Alternatively, build a colorful div structure with the JSON results and render images inline
resultToDom(queryResult);
```

Diese Funktion rendert auch alle Bilder, die in der JSON-Antwort enthalten sind, als `img` -Tag. Wenn die von Ihnen erstellten Inhaltsfragmente &quot;Abenteuer&quot;keine Bilder enthalten, können Sie versuchen, zu den `aem-demo-assets/adventures-all` persistente Abfrage durch Änderung von Zeile 25:

```
persistedQueryName = 'aem-demo-assets/adventures-all';
```

Diese Abfrage liefert eine JSON-Antwort, die Bilder und die `resultToDom()` -Funktion werden sie inline gerendert.

![Ergebnis der Abenteuer-all-Abfrage und der resultToDom-Rendering-Funktion](assets/do-not-localize/adventures-all-query-result.png)
