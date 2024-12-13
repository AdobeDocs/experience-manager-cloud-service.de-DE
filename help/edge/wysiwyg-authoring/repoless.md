---
title: Wiederverwenden von Code über mehrere Sites hinweg
description: Wenn Sie viele ähnliche Sites haben, die meist gleich aussehen und sich verhalten, aber unterschiedliche Inhalte haben, erfahren Sie, wie Sie Code über mehrere Sites hinweg in einem Replizierungsmodell freigeben können.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: e25e21984ebadde7076d95c6051b8bfca5b2ce03
workflow-type: tm+mt
source-wordcount: '1010'
ht-degree: 0%

---


# Wiederverwenden von Code über mehrere Sites hinweg {#repoless}

Wenn Sie viele ähnliche Sites haben, die meist gleich aussehen und sich verhalten, aber unterschiedliche Inhalte haben, erfahren Sie, wie Sie Code über mehrere Sites hinweg in einem Replizierungsmodell freigeben können.

## Eine Codebase für mehrere Sites {#one-codebase}

Standardmäßig ist AEM eng an Ihr Code-Repository gebunden, das die meisten Anwendungsfälle erfüllt. Sie können jedoch mehrere Sites haben, die sich hauptsächlich in ihrem Inhalt unterscheiden, aber dieselbe Codebasis nutzen können.

Anstatt mehrere GitHub-Repositorys zu erstellen und jede Website über ein dediziertes GitHub-Repository auszuführen, während sie synchron bleiben, AEM die Ausführung mehrerer Sites von derselben Codebasis aus unterstützt.

Diese vereinfachte Einrichtung, die die Codereplikation entfällt, wird auch als [&quot;Antwort&quot;, ](https://www.aem.live/docs/repoless) bezeichnet, da alle Websites außer Ihrer ersten kein eigenes GitHub-Repository benötigen.

Wenn Ihr Projekt die replizierte Flexibilität der Site-übergreifenden Codewiederverwendung erfordert, können Sie die Funktion aktivieren.

Unabhängig davon, wie viele Sites Sie letztendlich in einer widerstandslosen Weise erstellen möchten, müssen Sie Ihre erste Site erstellen, die als Basis-Site dient. In diesem Dokument wird erläutert, wie Sie Ihre erste Site für die Verwendung ohne Replikate erstellen.

## Voraussetzungen {#prerequisites}

Um diese Funktion nutzen zu können, müssen Sie Folgendes durchführen.

* Ihre Site ist bereits vollständig eingerichtet, indem Sie dem Dokument [Erste Schritte für Entwickler bei der WYSIWYG-Bearbeitung mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) folgen.
* Sie führen mindestens AEM as a Cloud Service 2024.08 aus.

Außerdem müssen Sie die Adobe bitten, zwei Elemente für Sie zu konfigurieren. Wenden Sie sich über Ihren Slack-Kanal an Adobe oder melden Sie ein Support-Problem, um diese Anfragen zu stellen.

* Der [aem.live-Konfigurationsdienst](https://www.aem.live/docs/config-service-setup#prerequisites) ist für Ihre Umgebung aktiv und Sie sind als Administrator konfiguriert.
* Die Replikationsfunktion muss für Ihr Programm durch Adobe aktiviert werden.

## Funktion &quot;Umpolen aktivieren&quot; {#activate}

Es gibt mehrere Schritte, um die Replikationsfunktion für Ihr Projekt zu aktivieren.

1. [Zugriffstoken abrufen](#access-token)
1. [Konfigurationsdienst einrichten](#config-service)
1. [Zugriffssteuerung festlegen](#access-control)
1. [AEM Konfiguration aktualisieren](#update-aem)
1. [Authentifizierungssite](#authenticate-site)

Für diese Schritte wird die Site `https://wknd.site` als Beispiel verwendet. Ersetzen Sie Ihre eigene entsprechend.

### Zugriffstoken abrufen {#access-token}

Sie benötigen zunächst ein Zugriffstoken, um den Konfigurationsdienst zu verwenden und ihn für den Anwendungsfall &quot;Antworten&quot;zu konfigurieren.

1. Gehen Sie zu `https://admin.hlx.page/login` und melden Sie sich mit der Adresse `login_adobe` beim Adobe-Identitäts-Provider an.
1. Sie werden an `https://admin.hlx.page/profile` weitergeleitet.
1. Kopieren Sie mithilfe der Entwicklertools Ihres Browsers den Wert von `x-auth-token` entweder aus dem JSON-Web-Token-Cookie, das von der Seite `admin.hlx.page` gesetzt wird.

Sobald Sie über Ihr Zugriffstoken verfügen, kann es im Header von cURL-Anfragen im folgenden Format übergeben werden.

```text
--header 'x-auth-token: <your-token>'
```

### Konfigurationsdienst konfigurieren {#config-service}

Wie in den [ Voraussetzungen erwähnt, muss der Konfigurationsdienst für Ihre Umgebung aktiviert sein. ](#prerequisites) Mit diesem cURL-Befehl können Sie die Einrichtung Ihres Konfigurationsdienstes überprüfen.

```text
curl  --location 'https://admin.hlx.page/config/<your-github-org>.json' \
--header 'x-auth-token: <your-token>'
```

Wenn der Konfigurationsdienst ordnungsgemäß eingerichtet ist, wird JSON zurückgegeben, das dem folgenden ähnelt.

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

Wenden Sie sich über Ihren Projekt-Slack-Kanal an Adobe oder lösen Sie ein Support-Problem, wenn Ihr Konfigurationsdienst nicht aktiviert ist. Sobald Sie Ihr Token haben und überprüft haben, ob der Konfigurationsdienst aktiviert ist, können Sie die Konfiguration fortsetzen.

1. Überprüfen Sie, ob Ihre Inhaltsquelle ordnungsgemäß eingerichtet ist.

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

### Zugriffssteuerung festlegen {#access-control}

Um die Zugriffskontrolle einzurichten, müssen Sie das technische Konto angeben.

1. Erstellen Sie eine neue Seite im Stammverzeichnis Ihrer Site und wählen Sie die Vorlage [**Konfiguration** .](/help/edge/wysiwyg-authoring/tabular-data.md#other)
   * Sie können die Konfiguration nur mit den vordefinierten Spalten `key` und `value` leer lassen. Sie müssen es nur erstellen.
1. Erstellen Sie mit einem cURL-Befehl ähnlich dem folgenden eine Zuordnung in der öffentlichen Konfiguration zur Site-Konfiguration.

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
1. In Ihrem Browser können Sie jetzt das technische Konto als Antwort auf den folgenden Link abrufen.

   ```text
   https://author-p<programID>-e<envionmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/<your-aem-project>/main/.helix/config.json
   ```

Die Antwort ähnelt der folgenden.

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

Da Sie jetzt den Konfigurationsdienst verwenden, können Sie `fstab.yaml` und `paths.json` aus Ihrem Git-Repository entfernen.

>[!NOTE]
>
>Wenn Sie den Konfigurationsdienst verwenden und die Pfadzuordnung über `config.json` verfügbar machen, wird die Datei `path.json` ignoriert.

Sobald AEM für die Verwendung von Replikaten konfiguriert ist, müssen Sie den Konfigurationsdienst verwenden und eine gültige `config.json` für die Pfadzuordnung angeben.

### Aktualisieren AEM Konfiguration {#update-aem}

Jetzt sind Sie bereit, die notwendigen Änderungen an Ihren Edge Delivery Services in AEM vorzunehmen.

1. Melden Sie sich bei der AEM-Autoreninstanz an, navigieren Sie zu &quot;**Tools** -> **Cloud Service** -> &quot;**Edge Delivery Services-Konfiguration**&quot;, wählen Sie die automatisch für Ihre Site erstellte Konfiguration aus und tippen oder klicken Sie in der Symbolleiste auf &quot;**Eigenschaften**&quot;.
1. Ändern Sie im Fenster **Edge Delivery Services Configuration** den Projekttyp in **aem.live with repoless config setup** und tippen oder klicken Sie auf **Save &amp; Close**.
   ![Edge Delivery Services-Konfiguration](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. Kehren Sie mit dem universellen Editor zu Ihrer Site zurück und stellen Sie sicher, dass sie weiterhin ordnungsgemäß dargestellt wird.
1. Ändern Sie einen Teil Ihres Inhalts und veröffentlichen Sie ihn erneut.
1. Besuchen Sie Ihre veröffentlichte Site unter `https://main--<your-aem-project>--<your-github-org>.aem.page/` und überprüfen Sie, ob die Änderungen richtig übernommen wurden.

Ihr Projekt ist jetzt für die Verwendung ohne Replikate eingerichtet.

## Nächste Schritte {#next-steps}

Nachdem Ihre Basis-Site für die Nutzung ohne Replizierung konfiguriert wurde, können Sie zusätzliche Sites erstellen, die dieselbe Codebasis nutzen. Weitere Informationen finden Sie in der folgenden Dokumentation je nach Anwendungsfall.

* [Umfasst Multi-Site-Management](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [Umpolen von Staging- und Produktionsumgebungen](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)

## Fehlerbehebung {#troubleshooting}

Das häufigste Problem, das nach der Konfiguration des Anwendungsfalls für Antworten auftrat, besteht darin, dass Seiten im universellen Editor nicht mehr gerendert werden oder dass Sie eine weiße Seite oder eine generische AEM as a Cloud Service-Fehlermeldung erhalten. In solchen Fällen gilt Folgendes:

* Anzeigen der Quelle der gerenderten Seite
   * Gibt es tatsächlich etwas gerendertes (korrekter HTML-Kopf mit `scripts.js`, `aem.js` und Editor-bezogenen JSON-Dateien)?
* Prüfen Sie die AEM `error.log` der Autoreninstanz auf Ausnahmen.
   * Das häufigste Problem ist, dass die Seitenkomponente mit 404-Fehlern fehlschlägt.
   * `config.json or paths.json` kann nicht geladen werden
   * `component-definition.json` usw. kann nicht geladen werden
