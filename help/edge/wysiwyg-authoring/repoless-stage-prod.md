---
title: Umpolen von Staging- und Produktionsumgebungen
description: Erfahren Sie, wie Sie separate Sites für Ihre Staging- und Produktionsumgebungen einrichten, indem Sie eine einzelne Codebasis replizierungslos nutzen.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 709d0661286d023c5cec51be2c51a1123ef7deb6
workflow-type: tm+mt
source-wordcount: '654'
ht-degree: 1%

---


# Umpolen von Staging- und Produktionsumgebungen {#repoless-stage-prod}

Erfahren Sie, wie Sie separate Sites für Ihre Staging- und Produktionsumgebungen einrichten, indem Sie eine einzelne Codebasis replizierungslos nutzen.

## Überblick {#overview}

Möglicherweise möchten Sie eine Site für Ihre Produktionsumgebung separat von Ihrer Staging-Umgebung einrichten. Das Einrichten einer zweiten Site für ein separates Staging- und Produktions-Setup ähnelt dem [Setup, das für die Verwaltung mehrerer Sites erforderlich ist.](/help/edge/wysiwyg-authoring/repoless-msm.md) Tatsächlich kann sie bei Bedarf mit MSM-Site-Strukturen kombiniert werden.

In diesem Dokument wird das typische Beispiel für separate Staging- und Produktionsumgebungen verwendet. Sie können separate Umgebungen für beliebige Umgebungen erstellen.

## Konfiguration {#configuration}

In diesem Dokument wird beschrieben, wie Sie eine separate Produktions-Site für Ihr Projekt mit derselben Codebasis einrichten. Die folgenden Annahmen werden getroffen.

* Die Staging-Site ist bereits eingerichtet und Sie möchten jetzt eine Konfiguration für die Produktions-Site erstellen.
* Die Inhaltsstruktur in AEM Authoring ist ähnlich.
* Für Staging und Produktion werden dieselben Pfadzuordnungen verwendet.

In diesem Beispiel gehen wir davon aus, dass bereits eine Produktionssite für das Projekt &quot;wknd&quot;erstellt wurde, dessen GitHub-Repo auch &quot;wknd&quot;genannt wird.

Es gibt zwei Schritte zum Konfigurieren einer separaten Produktions-Site.

1. [Erstellen Sie neue Edge Delivery Services-Sites für Ihre Produktionsumgebung.](#create-edge-site)
1. [Aktualisieren Sie die Cloud-Konfiguration in AEM für Ihre Produktions-Site.](#update-cloud-configuration)

### Erstellen neuer Edge Delivery Services-Sites für Ihre Produktionsumgebung {#create-edge-site}

1. Rufen Sie Ihr Authentifizierungstoken und das technische Konto für Ihr Programm ab.
   * Weitere Informationen zum Abrufen des Zugriffs-Tokens](/help/edge/wysiwyg-authoring/repoless.md#access-token) und des [technischen Kontos](/help/edge/wysiwyg-authoring/repoless.md#access-control) für Ihr Programm finden Sie im Dokument **Wiederverwenden von Code über Sites hinweg** .[
1. Erstellen Sie eine neue Site, indem Sie den Konfigurationsdienst wie folgt aufrufen. Beachten Sie Folgendes:
   * Der Projektname in der POST-URL muss der neue Site-Name sein, den Sie erstellen. In diesem Beispiel ist es `wknd-prod`.
   * Die `code` -Konfiguration sollte mit der beim ersten Erstellen des Projekts verwendeten übereinstimmen.
   * Der `content` > `source` > `url` muss an den Namen der neuen Site angepasst werden, die Sie erstellen. In diesem Beispiel ist es `wknd-prod`.
   * Das heißt, der Site-Name in der POST-URL und der `content` > `source` > `url` müssen identisch sein.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-prod.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "code": {
           "owner": "<your-github-org>",
           "repo": "wknd",
           "source": {
               "type": "github",
               "url": "https://github.com/<your-github-org>/wknd"
           }
       },
       "content": {
           "source": {
               "url": "https://author-p<programID>-e<environmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/wknd-prod/main",
               "type": "markup",
               "suffix": ".html"
           }
       },
       "access": {
           "admin": {
               "role": {
                   "admin": [
                       "*@adobe.com"
                   ],
                   "publish": [
                       "<tech-account-id>@techacct.adobe.com"
                   ]
               },
               "requireAuth": "auto"
           }
       }
   }'
   ```

1. Fügen Sie die Pfadzuordnung für Ihre neue Site hinzu, indem Sie den folgenden Aufruf an den Konfigurationsdienst durchführen.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-prod/public.json \
     --header 'x-auth-token: <your-token>' \
     --header 'Content-Type: application/json' \
     --data '{
       "paths": {
           "mappings": [
               "/content/wknd/:/"
           ],
           "includes": [
               "/content/wknd/"
           ]
       }
   }'
   ```

Stellen Sie sicher, dass die öffentliche Konfiguration Ihrer neuen Site funktioniert, indem Sie `https://main--wknd-prod--<your-github-org>.aem.page/config.json` aufrufen und den Inhalt der zurückgegebenen JSON überprüfen.

### Aktualisierung der Cloud-Konfigurationen in AEM für Ihre Produktions-Site {#update-cloud-configuration}

Ihre AEM muss so konfiguriert sein, dass die neuen Edge Delivery-Sites, die Sie im vorherigen Abschnitt für eine dedizierte Produktions-Site erstellt haben, verwendet werden. In diesem Beispiel muss der Inhalt unter `/content/wknd` in Ihrer Produktionsumgebung wissen, um die von Ihnen erstellte `wknd-prod`-Site zu verwenden.

1. Melden Sie sich bei der AEM-Produktionsinstanz an und gehen Sie zu **Tools** -> **Cloud Service** -> **Edge Delivery Services-Konfiguration**.
1. Wählen Sie die Konfiguration aus, die automatisch für Ihr Projekt erstellt wurde.
1. Tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften** .
1. Im Fenster **Edge Delivery Services Configuration** :
   * Geben Sie Ihre GitHub-Organisation im Feld **Organisation** an.
   * Ändern Sie den Site-Namen in den Namen der Site, die Sie im vorherigen Abschnitt erstellt haben. In diesem Fall wäre das `wknd-prod`.
   * Ändern Sie den Projekttyp in &quot;**aem.live&quot;mit der Konfiguration der Replikationskonfiguration**&quot;.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

## Überprüfen der Einrichtung {#verify}

Nachdem Sie alle erforderlichen Konfigurationsänderungen vorgenommen haben, überprüfen Sie, ob alles erwartungsgemäß funktioniert.

1. Melden Sie sich bei Ihrer AEM-Produktionsinstanz an.
1. Navigieren Sie zur Konsole **Sites**, indem Sie zu **Navigation** -> **Sites** navigieren.
1. Wählen Sie eine Seite in Ihrer Site aus.
1. Tippen oder klicken Sie in der Symbolleiste auf **Bearbeiten** .
1. Stellen Sie sicher, dass die Seite im universellen Editor ordnungsgemäß gerendert wird und denselben Code wie Ihr Site-Stamm verwendet.
1. Ändern Sie die Seite und veröffentlichen Sie sie erneut.
1. Besuchen Sie Ihre neue Edge Delivery Services-Site für diese Seite um `https://main--wknd-prod--<your-github-org>.aem.page`.

Wenn Sie die von Ihnen vorgenommenen Änderungen sehen, funktioniert die separate Einrichtung der Produktions-Site ordnungsgemäß.
