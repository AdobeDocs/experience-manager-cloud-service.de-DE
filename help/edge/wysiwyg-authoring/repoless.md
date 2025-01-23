---
title: Wiederverwenden von Code in verschiedenen Sites
description: Wenn Sie viele ähnliche Websites haben, die meist gleich aussehen und sich verhalten, aber unterschiedliche Inhalte haben, erfahren Sie, wie Sie Code in einem responsiven Modell über mehrere Websites hinweg teilen können.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: a6bc0f35-9e76-4b5a-8747-b64e144c08c4
source-git-commit: e7f7c169e7394536fc2968ecf1418cd095177679
workflow-type: tm+mt
source-wordcount: '971'
ht-degree: 2%

---

# Wiederverwenden von Code in verschiedenen Sites {#repoless}

Wenn Sie viele ähnliche Websites haben, die meist gleich aussehen und sich verhalten, aber unterschiedliche Inhalte haben, erfahren Sie, wie Sie Code in einem responsiven Modell über mehrere Websites hinweg teilen können.

## Eine Codebasis für mehrere Sites {#one-codebase}

Standardmäßig ist AEM eng an Ihr Code-Repository gebunden, das die meisten Anwendungsfälle erfüllt. Sie können jedoch mehrere Sites haben, die sich größtenteils in ihren Inhalten unterscheiden, aber dieselbe Code-Basis nutzen können.

Anstatt mehrere GitHub-Repositorys zu erstellen und jede Site in einem dedizierten GitHub-Repository auszuführen und dabei synchron zu halten, unterstützt AEM das Ausführen mehrerer Sites von derselben Codebasis aus.

Diese vereinfachte Einrichtung, die die Notwendigkeit der Code-Replikation beseitigt, wird auch als &quot;[ Repoless“ bezeichnet](https://www.aem.live/docs/repoless) da alle außer Ihrer ersten Site kein eigenes GitHub-Repository benötigen.

Wenn für Ihr Projekt die Flexibilität der Code-Wiederverwendung auf allen Sites erforderlich ist, können Sie die Funktion aktivieren.

Unabhängig davon, wie viele Sites Sie letztendlich auf reaktionsfreie Weise erstellen möchten, müssen Sie Ihre erste Site erstellen, die als Basis-Site dient. In diesem Dokument wird erläutert, wie Sie Ihre erste Site für die Verwendung durch Antwortgeräteverantwortliche erstellen.

## Voraussetzungen {#prerequisites}

Um diese Funktion nutzen zu können, stellen Sie sicher, dass Sie Folgendes getan haben.

* Ihre Site ist bereits vollständig eingerichtet. Folgen Sie dazu dem Dokument [Erste Schritte für WYSIWYG-Entwickler mit Edge Delivery Services.](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md)
* Sie führen mindestens AEM as a Cloud Service 2024.08 aus.

Sie müssen Adobe auch bitten, die folgenden Elemente für Sie zu konfigurieren. Kontaktieren Sie uns über Ihren Slack-Kanal oder werfen Sie ein Support-Problem auf, um Adobe anzufordern, diese Änderungen vorzunehmen:

* Bitten Sie darum, den [aem.live-Konfigurationsdienst](https://www.aem.live/docs/config-service-setup#prerequisites) für Ihre Umgebung zu aktivieren und sicherzustellen, dass Sie als Administrator konfiguriert sind.
* Bitten Sie, die Repoless-Funktion für Ihr Programm per Adobe zu aktivieren.
* Bitten Sie Adobe, die Organisation für Sie zu erstellen.

## Antwortfunktion aktivieren {#activate}

Es gibt mehrere Schritte, um die Repoless-Funktion für Ihr Projekt zu aktivieren.

1. [Zugriffstoken abrufen](#access-token)
1. [Einrichten des Konfigurationsdienstes](#config-service)
1. [Hinzufügen der Site-Konfiguration und des technischen Kontos](#access-control)
1. [AEM-Konfiguration aktualisieren](#update-aem)
1. [Authentifizieren einer Site](#authenticate-site)

Bei diesen Schritten wird beispielhaft der Site-`https://wknd.site` verwendet. Ersetzen Sie Ihre eigenen entsprechend.

### Zugriffstoken abrufen {#access-token}

Sie benötigen zunächst ein Zugriffstoken, um den Konfigurations-Service zu verwenden und ihn für den Anwendungsfall „Antwortlos“ zu konfigurieren.

1. Navigieren Sie zu `https://admin.hlx.page/login` und verwenden Sie die `login_adobe`, um sich beim Adobe-Identitätsanbieter anzumelden.
1. Sie werden an `https://admin.hlx.page/profile` weitergeleitet.
1. Kopieren Sie mithilfe der Entwickler-Tools Ihres Browsers den Wert der `x-auth-token` entweder aus dem JSON-Web-Token-Cookie, das auf der `admin.hlx.page` gesetzt wird.

Sobald Sie über Ihr Zugriffs-Token verfügen, kann es im Header von cURL-Anfragen im folgenden Format übergeben werden.

```text
--header 'x-auth-token: <your-token>'
```

### Pfadzuordnung für Site-Konfiguration hinzufügen und technisches Konto festlegen {#access-control}

Sie müssen eine Site-Konfiguration erstellen und sie zu Ihrer Pfadzuordnung hinzufügen.

1. Erstellen Sie eine neue Seite im Stammverzeichnis Ihrer Site und wählen Sie die Vorlage [**Konfiguration** aus](/help/edge/wysiwyg-authoring/tabular-data.md#other)
   * Sie können die Konfiguration nur mit den vordefinierten Spalten `key` und `value` leer lassen. Sie müssen sie nur erstellen.
1. Erstellen Sie in der öffentlichen Konfiguration eine Zuordnung zur Site-Konfiguration mithilfe eines cURL-Befehls ähnlich dem folgenden.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/<your-site-content>/:/",
               "/content/<your-site-content>/configuration:/.helix/config.json"
      ],
           "includes": [
               "/content/<your-site-content>/"
           ]
       }
   }'
   ```
1. Überprüfen Sie, ob die öffentliche Konfiguration festgelegt wurde und mit einem cURL-Befehl ähnlich dem folgenden verfügbar ist.

   ```text
   curl 'https://main--<your-aem-project>--<your-github-org>.aem.live/config.json'
   ```

Sobald die Site-Konfiguration zugeordnet ist, können Sie die Zugriffskontrolle konfigurieren, indem Sie Ihr technisches Konto so definieren, dass es über Berechtigungen zum Veröffentlichen verfügt.

1. Rufen Sie in Ihrem Browser das technische Konto in der Antwort des folgenden Links ab.

   ```text
   https://author-p<programID>-e<envionmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/<your-aem-project>/main/.helix/config.json
   ```

1. Die Antwort ähnelt der folgenden.

   ```json
   {
     "total": 1,
     "offset": 0,
     "limit": 1,
     "data": [
       {
         "key": "admin.role.publish",
         "value": "<tech-account-id>@techacct.adobe.com"
       }
     ],
     ":type": "sheet"
   }
   ```

1. Legen Sie das technische Konto in Ihrer Konfiguration mit einem cURL-Befehl ähnlich dem folgenden fest.

   * Passen Sie den `admin` an, um die Benutzer zu definieren, die vollen administrativen Zugriff auf die Website haben sollen.
      * Es handelt sich um ein Array von E-Mail-Adressen.
      * Der Platzhalter `*` verwendet werden.
      * Weitere Informationen finden Sie [ Dokument „Konfigurieren der ](https://www.aem.live/docs/authentication-setup-authoring#default-roles) für Autoren“.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/access.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "admin": {
           "role": {
               "admin": [
                   "<email>@<domain>.<tld>"
               ],
               "config_admin": [
                   "<tech-account-id>@techacct.adobe.com"
               ]
           },
           "requireAuth": "auto"
       }
   }'
   ```

Da Sie jetzt den Konfigurations-Service verwenden, können Sie `fstab.yaml` und `paths.json` aus Ihrem Git-Repository entfernen.

>[!NOTE]
>
>Wenn Sie den Konfigurations-Service verwenden und die Pfadzuordnung über `config.json` verfügbar machen, wird die `path.json`-Datei ignoriert.

Sobald AEM für die Verwendung als Antwort konfiguriert ist, müssen Sie den Konfigurations-Service verwenden und eine gültige `config.json` mit der Pfadzuordnung angeben.

### AEM-Konfiguration aktualisieren {#update-aem}

Jetzt können Sie die erforderlichen Änderungen an Ihren Edge Delivery Services in AEM vornehmen.

1. Melden Sie sich bei der AEM-Autoreninstanz an, wechseln Sie zu **Tools** -> **Cloud Service** -> **Edge Delivery Services-Konfiguration** und wählen Sie die automatisch für Ihre Site erstellte Konfiguration aus und tippen oder klicken Sie auf **Eigenschaften** in der Symbolleiste.
1. Ändern Sie im Fenster **Edge Delivery Services** Konfiguration den Projekttyp in &quot;**.live mit Repoless-Konfiguration** und tippen oder klicken Sie auf **Speichern und schließen**.
   Konfiguration von ![Edge Delivery Services](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. Kehren Sie mit dem universellen Editor zu Ihrer Site zurück und stellen Sie sicher, dass sie weiterhin ordnungsgemäß gerendert wird.
1. Ändern Sie einige Ihrer Inhalte und veröffentlichen Sie sie erneut.
1. Besuchen Sie Ihre veröffentlichte Site unter `https://main--<your-aem-project>--<your-github-org>.aem.page/` und überprüfen Sie, ob die Änderungen korrekt widergespiegelt werden.

Ihr Projekt ist jetzt für die Verwendung ohne Gegenmaßnahmen eingerichtet.

## Nächste Schritte {#next-steps}

Da Ihre Basis-Site nun für die Nutzung ohne Antwort konfiguriert ist, können Sie zusätzliche Sites erstellen, die dieselbe Code-Basis nutzen. Lesen Sie je nach Anwendungsfall die folgende Dokumentation.

* [Multi-Site-Management ohne Repo](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [Staging- und Produktionsumgebungen ohne Repo](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)

## Fehlerbehebung {#troubleshooting}

Das häufigste Problem nach der Konfiguration des Anwendungsfalls „Antworten“ ist, dass Seiten im universellen Editor nicht mehr gerendert werden oder Sie eine weiße Seite oder eine generische AEM as a Cloud Service-Fehlermeldung erhalten. In solchen Fällen:

* Anzeigen der Quelle der gerenderten Seite.
   * Gibt es tatsächlich etwas gerendert (korrekter HTML-Kopf mit `scripts.js`-, `aem.js`- und editorbezogenen JSON-Dateien)?
* Prüfen Sie die AEM-`error.log` der Autoreninstanz auf Ausnahmen.
   * Das häufigste Problem ist, dass die Seitenkomponente mit 404-Fehlern fehlschlägt.
   * `config.json or paths.json` kann nicht geladen werden
   * `component-definition.json` usw. kann nicht geladen werden
