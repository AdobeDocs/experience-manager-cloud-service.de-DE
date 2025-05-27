---
title: Wiederverwenden von Code in verschiedenen Sites
description: Erfahren Sie, wie Sie Code in einem Modell ohne Repo über mehrere Sites hinweg freigeben können, wenn Sie über viele ähnliche Sites verfügen, die in Aussehen und Verhalten meist identisch sind, deren Inhalte sich jedoch unterscheiden.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: a6bc0f35-9e76-4b5a-8747-b64e144c08c4
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '1039'
ht-degree: 100%

---

# Wiederverwenden von Code in verschiedenen Sites {#repoless}

Erfahren Sie, wie Sie Code in einem Modell ohne Repo über mehrere Sites hinweg freigeben können, wenn Sie über viele ähnliche Sites verfügen, die in Aussehen und Verhalten meist identisch sind, deren Inhalte sich jedoch unterscheiden.

## Eine Code-Basis für mehrere Sites {#one-codebase}

AEM ist standardmäßig eng an Ihr Code-Repository gebunden, was die meisten Anwendungsfälle erfüllt. Sie können jedoch über mehrere Sites verfügen, die sich größtenteils in ihren Inhalten unterscheiden, aber dieselbe Code-Basis nutzen könnten.

Anstatt mehrere GitHub-Repositorys zu erstellen und jede Site in einem dedizierten GitHub-Repository auszuführen und dabei synchron zu halten, unterstützt AEM die Ausführung mehrerer Sites aus derselben Code-Basis.

Dieses vereinfachte Setup, das die Notwendigkeit der Code-Replikation beseitigt, wird auch als [„ohne Repo“](https://www.aem.live/docs/repoless) bezeichnet, da alle Sites außer Ihrer ersten Site kein eigenes GitHub-Repository benötigen.

Wenn für Ihr Projekt die Flexibilität der Code-Wiederverwendung ohne Repo auf allen Sites erforderlich ist, können Sie die Funktion aktivieren.

Unabhängig davon, wie viele Sites Sie letztendlich ohne Repo erstellen möchten, müssen Sie Ihre erste Site erstellen, die als Basis-Site dient. In diesem Dokument wird erläutert, wie Sie Ihre erste Site für die Verwendung ohne Repo erstellen.

## Voraussetzungen {#prerequisites}

Um diese Funktion nutzen zu können, stellen Sie sicher, dass Sie Folgendes durchgeführt haben.

* Ihre Site ist bereits vollständig gemäß dem Dokument [Erste-Schritte-Handbuch für Entwickelnde zum WYSIWYG-Authoring mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) eingerichtet.
* Sie führen mindestens AEM as a Cloud Service 2024.08 aus.

Außerdem müssen Sie Adobe bitten, die folgenden Elemente für Sie zu konfigurieren. Kontaktieren Sie uns über Ihren Slack-Kanal oder erstellen Sie ein Support-Problem, um Adobe aufzufordern, diese Änderungen vorzunehmen:

* Bitten Sie darum, den [aem.live-Konfigurations-Service](https://www.aem.live/docs/config-service-setup#prerequisites) für Ihre Umgebung zu aktivieren und sicherzustellen, dass Sie als Admin konfiguriert sind.
* Bitten Sie Adobe, die Funktion zum Einrichten ohne Repository für Ihr Programm zu aktivieren.
* Bitten Sie Adobe, die Organisation für Sie zu erstellen.

## Aktivieren der Funktion zum Einrichten ohne Repository {#activate}

Es gibt mehrere Schritte zum Aktivieren der Funktion zum Einrichten ohne Repository für Ihr Projekt.

1. [Abrufen des Zugriffstokens](#access-token)
1. [Einrichten eines Konfigurations-Services](#config-service)
1. [Hinzufügen der Site-Konfiguration und des technischen Kontos](#access-control)
1. [Aktualisieren der AEM-Konfiguration](#update-aem)
1. [Authentifizieren der Site](#authenticate-site)

Bei diesen Schritten wird die Site `https://wknd.site` als Beispiel verwendet. Ersetzen Sie sie entsprechend durch Ihre eigene Site.

### Abrufen des Zugriffstokens {#access-token}

Sie benötigen zunächst ein Zugriffstoken, um den Konfigurations-Service zu verwenden und es für den Anwendungsfall ohne Repo zu konfigurieren.

1. Gehen Sie zu `https://admin.hlx.page/login` und verwenden Sie die Adresse `login_adobe`, um sich beim Adobe-Identitätsanbieter anzumelden.
1. Sie werden zu `https://admin.hlx.page/profile` weitergeleitet.
1. Kopieren Sie mithilfe der Entwickler-Tools Ihres Browsers den Wert des `x-auth-token` aus dem JSON-Web-Token-Cookie, das von der Seite `admin.hlx.page` festgelegt wird.

Sobald Sie über Ihr Zugriffstoken verfügen, kann es im Header von cURL-Anfragen im folgenden Format übergeben werden.

```text
--header 'x-auth-token: <your-token>'
```

### Hinzufügen einer Pfadzuordnung für die Site-Konfiguration und Festlegen des technischen Kontos {#access-control}

Sie müssen eine Site-Konfiguration erstellen und sie zu Ihrer Pfadzuordnung hinzufügen.

1. Erstellen Sie eine neue Seite im Stammverzeichnis Ihrer Site und wählen Sie die [**Konfigurationsvorlage** aus](/help/edge/wysiwyg-authoring/tabular-data.md#other).
   * Sie können die Konfiguration nur mit den vordefinierten Spalten `key` und `value` leer lassen. Sie müssen sie nur erstellen.
1. Erstellen Sie in der öffentlichen Konfiguration eine Zuordnung zur Site-Konfiguration mithilfe eines cURL-Befehls, der dem Folgenden ähnelt.

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
1. Bestätigen Sie, dass die öffentliche Konfiguration festgelegt wurde und mit einem cURL-Befehl ähnlich dem Folgenden verfügbar ist.

   ```text
   curl 'https://main--<your-aem-project>--<your-github-org>.aem.live/config.json'
   ```

Sobald die Site-Konfiguration zugeordnet ist, können Sie die Zugriffssteuerung konfigurieren, indem Sie Ihr technisches Konto so definieren, dass es über Berechtigungen zum Veröffentlichen verfügt.

1. Melden Sie sich bei der AEM-Autoreninstanz an und navigieren Sie zu **Tools** -> **Cloud Services** -> **Edge Delivery Services-Konfiguration**. Wählen Sie die automatisch für Ihre Site erstellte Konfiguration aus und tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften**.

1. Wählen Sie im Fenster **Edge Delivery Services-Konfiguration** die Registerkarte **Authentifizierung** aus und kopieren Sie den Wert für **die ID des technischen Kontos**.

   * Er sieht in etwa so aus: `<tech-account-id>@techacct.adobe.com`.
   * Das technische Konto ist für alle Sites einer AEM-Autorenumgebung gleich.

1. Legen Sie das technische Konto für Ihre Konfiguration ohne Repository mit einem cURL-Befehl wie dem folgenden fest. Verwenden Sie dabei die von Ihnen kopierte ID des technischen Kontos.

   * Passen Sie den Block `admin` an, um die Benutzenden zu definieren, die vollen administrativen Zugriff auf die Site haben sollen.
      * Es handelt sich um ein Array von E-Mail-Adressen.
      * Der Platzhalter `*` kann verwendet werden.
      * Weitere Informationen finden Sie im Dokument [Konfigurieren der Authentifizierung für Autorinnen und Autoren](https://www.aem.live/docs/authentication-setup-authoring?lang=de#default-roles).

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

Da Sie nun den Konfigurations-Service verwenden, können Sie `fstab.yaml` und `paths.json` aus Ihrem Git-Repository entfernen.

>[!NOTE]
>
>Durch Nutzung des Konfigurations-Service und Anzeige der Pfadzuordnung über `config.json` wird die Datei `path.json` ignoriert.

Sobald AEM für die Verwendung ohne Repository konfiguriert ist, müssen Sie den Konfigurations-Service verwenden und eine gültige Datei `config.json` mit der Pfadzuordnung angeben.

### Aktualisieren der AEM-Konfiguration {#update-aem}

Nun können Sie die erforderlichen Änderungen an Edge Delivery Services in AEM vornehmen.

1. Melden Sie sich bei der AEM-Autoreninstanz an und navigieren Sie zu **Tools** -> **Cloud Services** -> **Edge Delivery Services-Konfiguration**. Wählen Sie die automatisch für Ihre Site erstellte Konfiguration aus und tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften**.
1. Ändern Sie im Fenster **Edge Delivery Services-Konfiguration** den Projekttyp in **aem.live mit Konfigurations-Setup ohne Repo** und tippen oder klicken Sie auf **Speichern und schließen**.
   ![Edge Delivery Services-Konfiguration](/help/edge/wysiwyg-authoring/assets/repoless/edge-delivery-services-configuration.png)
1. Kehren Sie über den universellen Editor zu Ihrer Site zurück und stellen Sie sicher, dass sie weiterhin ordnungsgemäß gerendert wird.
1. Ändern Sie einige Ihrer Inhalte und veröffentlichen Sie sie erneut.
1. Besuchen Sie Ihre veröffentlichte Site unter `https://main--<your-aem-project>--<your-github-org>.aem.page/` und überprüfen Sie, ob die Änderungen korrekt angezeigt werden.

Ihr Projekt ist nun für die Verwendung ohne Repository eingerichtet.

## Nächste Schritte {#next-steps}

Da Ihre Basis-Site nun für die Nutzung ohne Repository konfiguriert ist, können Sie zusätzliche Sites erstellen, die dieselbe Code-Basis nutzen. Lesen Sie je nach Anwendungsfall die folgende Dokumentation.

* [Multi-Site-Management ohne Repository](/help/edge/wysiwyg-authoring/repoless-msm.md)
* [Staging- und Produktionsumgebungen ohne Repository](/help/edge/wysiwyg-authoring/repoless-stage-prod.md)
* [Site-Authentifizierung für die Inhaltserstellung](/help/edge/wysiwyg-authoring/site-authentication.md)

## Fehlerbehebung {#troubleshooting}

Das häufigste Problem nach der Konfiguration des Anwendungsfalls „ohne Repository“ besteht darin, dass Seiten im universellen Editor nicht mehr gerendert werden oder Sie eine weiße Seite bzw. eine generische AEM as a Cloud Service-Fehlermeldung erhalten. Gehen Sie in solchen Fällen wie folgt vor:

* Zeigen Sie die Quelle der gerenderten Seite an.
   * Wird tatsächlich etwas gerendert (korrektes HTML-Head mit `scripts.js`, `aem.js` und editorbezogenen JSON-Dateien)?
* Prüfen Sie die AEM-Datei `error.log` der Autoreninstanz auf Ausnahmen.
   * Das häufigste Problem ist, dass die Seitenkomponente mit einem 404-Fehler fehlschlägt.
   * `config.json or paths.json` kann nicht geladen werden.
   * `component-definition.json` usw. kann nicht geladen werden.
