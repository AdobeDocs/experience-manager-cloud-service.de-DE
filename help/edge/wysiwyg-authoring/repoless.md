---
title: Wiederverwenden von Code in verschiedenen Sites
description: Wenn Sie viele ähnliche Websites haben, die meist gleich aussehen und sich verhalten, aber unterschiedliche Inhalte haben, erfahren Sie, wie Sie Code in einem responsiven Modell über mehrere Websites hinweg teilen können.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: a6bc0f35-9e76-4b5a-8747-b64e144c08c4
source-git-commit: 7b37f3d387f0200531fe12cde649b978f98d5d49
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 0%

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

Sie müssen Adobe auch bitten, zwei Elemente für Sie zu konfigurieren. Wenden Sie sich über Ihren Slack-Kanal an Adobe oder werfen Sie ein Support-Problem auf, um diese Anfragen zu stellen.

* Der [aem.live-Konfigurations](https://www.aem.live/docs/config-service-setup#prerequisites)Service ist für Ihre Umgebung aktiv und Sie sind als Administrator konfiguriert.
* Die Repoless-Funktion muss für Ihr Programm per Adobe aktiviert werden.

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

### Konfigurieren des Konfigurations-Services {#config-service}

Wie unter [Voraussetzungen“ erwähnt](#prerequisites) muss der Konfigurations-Service für Ihre Umgebung aktiviert sein. Sie können die Einrichtung Ihres Konfigurations-Services mit diesem cURL-Befehl überprüfen.

```text
curl  --location 'https://admin.hlx.page/config/<your-github-org>.json' \
--header 'x-auth-token: <your-token>'
```

Wenn der Konfigurations-Service ordnungsgemäß eingerichtet ist, wird eine JSON-Datei ähnlich der folgenden zurückgegeben.

```json
{
  "title": "<your-github-org>",
  "description": "Your GitHub Org",
  "lastModified": "2024-11-14T12:14:04.230Z",
  "created": "2024-11-14T12:13:37.032Z",
  "version": 1,
  "users": [
    {
      "email": "justthisguyyouknow@adobe.com",
      "roles": [
        "admin"
      ],
      "id": "<your-id>"
    }
  ]
}
```

Wenden Sie sich über Ihren Projekt-Slack-Kanal an Adobe oder werfen Sie ein Support-Problem auf, wenn Ihr Konfigurations-Service nicht aktiviert ist. Nachdem Sie Ihr Token konfiguriert und überprüft haben, dass der Konfigurations-Service aktiviert ist, können Sie mit der Konfiguration fortfahren.

1. Vergewissern Sie sich, dass Ihre Inhaltsquelle ordnungsgemäß eingerichtet ist.

   ```text
   curl --request GET \
   --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>.json \
   --header 'x-auth-token: <your-token>'
   ```

1. Fügen Sie der öffentlichen Konfiguration eine Pfadzuordnung hinzu.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/<your-site-content>/:/"
      ],
           "includes": [
               "/content/<your-site-content>/"
           ]
       }
   }'
   ```

Nachdem die öffentliche Konfiguration erstellt wurde, können Sie über eine URL wie `https://main--<your-aem-project>--<your-github-org>.aem.page/config.json` darauf zugreifen, um sie zu überprüfen.

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

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/<your-aem-project>/access.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "admin": {
           "role": {
               "admin": [
                   "*@adobe.com"
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

* [Reaktionsloses Multi-Site-Management](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [Reagiert auf Staging- und Produktionsumgebungen](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)

## Fehlerbehebung {#troubleshooting}

Das häufigste Problem nach der Konfiguration des Anwendungsfalls „Antworten“ ist, dass Seiten im universellen Editor nicht mehr gerendert werden oder Sie eine weiße Seite oder eine generische AEM as a Cloud Service-Fehlermeldung erhalten. In solchen Fällen:

* Anzeigen der Quelle der gerenderten Seite.
   * Gibt es tatsächlich etwas gerendert (korrekter HTML-Kopf mit `scripts.js`-, `aem.js`- und editorbezogenen JSON-Dateien)?
* Prüfen Sie die AEM-`error.log` der Autoreninstanz auf Ausnahmen.
   * Das häufigste Problem ist, dass die Seitenkomponente mit 404-Fehlern fehlschlägt.
   * `config.json or paths.json` kann nicht geladen werden
   * `component-definition.json` usw. kann nicht geladen werden
