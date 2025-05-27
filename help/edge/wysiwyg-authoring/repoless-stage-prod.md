---
title: Staging- und Produktionsumgebungen ohne Repository
description: Erfahren Sie, wie Sie mithilfe einer einzigen Code-Basis und ohne Repository separate Sites für Ihre Staging- und Produktionsumgebungen einrichten.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 701bd9bc-30e8-4654-8248-a06d441d1504
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '799'
ht-degree: 100%

---

# Staging- und Produktionsumgebungen ohne Repository {#repoless-stage-prod}

Erfahren Sie, wie Sie mithilfe einer einzigen Code-Basis und ohne Repository separate Sites für Ihre Staging- und Produktionsumgebungen einrichten.

## Überblick {#overview}

Unter Umständen möchten Sie eine von Ihrer Staging-Umgebung getrennte Site für Ihre Produktionsumgebung einrichten. Die Einrichtung einer zweiten Site für eine separate Staging- und Produktionskonfiguration ähnelt der für das [Multi-Site-Management](/help/edge/wysiwyg-authoring/repoless-msm.md). Tatsächlich kann sie bei Bedarf mit MSM-Site-Strukturen kombiniert werden.

In diesem Dokument wird ein typisches Beispiel für separate Staging- und Produktionsumgebungen verwendet. Sie können für jede gewünschte Umgebung separate Umgebungen erstellen.

## Voraussetzungen {#requirements}

Zum Konfigurieren von Staging- und Produktionsumgebungen ohne Repository müssen Sie zunächst die folgenden Aufgaben durchführen:

* In diesem Dokument wird vorausgesetzt, dass Sie bereits eine Site für Ihr Projekt auf Grundlage des [Erste-Schritte-Handbuchs für Entwickelnde zum WYSIWYG-Authoring mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) erstellt haben.
* Sie müssen die [Funktion zum Einrichten ohne Repository bereits für Ihr Projekt aktiviert](/help/edge/wysiwyg-authoring/repoless.md) haben.

## Konfiguration {#configuration}

In diesem Dokument wird beschrieben, wie Sie mit derselben Code-Basis eine separate Produktions-Site für Ihr Projekt einrichten. Folgendes wird vorausgesetzt:

* Die Staging-Site ist bereits eingerichtet und Sie möchten nun eine Konfiguration für die Produktions-Site erstellen.
* Die Inhaltsstruktur in der AEM-Autoreninstanz ist ähnlich.
* Für die Staging- und Produktionsumgebung werden dieselben Pfadzuordnungen verwendet.

In diesem Beispiel wird davon ausgegangen, dass bereits eine Produktions-Site für das Projekt namens „wknd“ erstellt wurde, dessen GitHub-Repository ebenfalls „wknd“ heißt.

Es gibt zwei Schritte, die Sie zum Konfigurieren einer separaten Produktions-Site durchführen müssen.

1. [Erstellen Sie neue Edge Delivery Services-Sites für die Produktionsumgebung](#create-edge-site).
1. [Aktualisieren Sie die Cloud-Konfiguration in AEM für die Produktions-Site](#update-cloud-configuration).

### Erstellen neuer Edge Delivery Services-Sites für die Produktionsumgebung {#create-edge-site}

1. Rufen Sie Ihr Authentifizierungs-Token und das technische Konto für Ihr Programm ab.
   * Weitere Informationen zum [Abrufen Ihres Zugriffstokens](/help/edge/wysiwyg-authoring/repoless.md#access-token) und des [technischen Kontos](/help/edge/wysiwyg-authoring/repoless.md#access-control) für Ihr Programm finden Sie im Dokument **Wiederverwenden von Code in verschiedenen Sites**.
1. Erstellen Sie eine neue Site, indem Sie den folgenden Aufruf an den Konfigurations-Service ausführen. Bitte beachten:
   * Der Projektname in der POST-URL muss der Name der neuen Site sein, die Sie erstellen. In diesem Beispiel lautet er `wknd-prod`.
   * Die `code`-Konfiguration sollte mit der für die anfängliche Projekterstellung verwendeten Konfiguration übereinstimmen.
   * Der Pfad `content` > `source` > `url` muss an den Namen der neuen Site angepasst werden, die Sie erstellen. In diesem Beispiel lautet er `wknd-prod`.
   * D. h., der Name der Site in der POST-URL und der Pfad `content` > `source` > `url` müssen identisch sein.
   * Passen Sie den Block `admin` an, um die Benutzenden zu definieren, die vollen administrativen Zugriff auf die Site haben sollen.
      * Es handelt sich um ein Array von E-Mail-Adressen.
      * Der Platzhalter `*` kann verwendet werden.
      * Weitere Informationen finden Sie im Dokument [Konfigurieren der Authentifizierung für Autorinnen und Autoren](https://www.aem.live/docs/authentication-setup-authoring?lang=de#default-roles).

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
                       "<email>@<domain>.<tld>"
                   ],
                   "config_admin": [
                       "<tech-account-id>@techacct.adobe.com"
                   ]
               },
               "requireAuth": "auto"
           }
       }
   }'
   ```

1. Fügen Sie die Pfadzuordnung für Ihre neue Site hinzu, indem Sie den folgenden Aufruf an den Konfigurations-Service durchführen.

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

Überprüfen Sie, ob die öffentliche Konfiguration Ihrer neuen Site funktioniert, indem Sie `https://main--wknd-prod--<your-github-org>.aem.page/config.json` aufrufen und den Inhalt der zurückgegebenen JSON-Datei verifizieren.

### Aktualisieren von Cloud-Konfigurationen in AEM für die Produktions-Site {#update-cloud-configuration}

Ihre AEM-Produktionsumgebung muss so konfiguriert sein, dass sie die neuen Edge Delivery-Sites verwendet, die Sie im vorherigen Abschnitt für eine dedizierte Produktions-Site erstellt haben. In diesem Beispiel muss der Inhalt unter `/content/wknd` in Ihrer Produktionsumgebung wissen, dass die von Ihnen erstellte `wknd-prod`-Site verwendet werden soll.

1. Melden Sie sich bei der AEM-Produktionsinstanz an und navigieren Sie zu **Tools** -> **Cloud Services** -> **Edge Delivery Services-Konfiguration**.
1. Wählen Sie die Konfiguration aus, die automatisch für Ihr Projekt erstellt wurde.
1. Tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften**.
1. Das Fenster **Edge Delivery Services-Konfiguration** wird angezeigt:
   * Geben Sie Ihre GitHub-Organisation im Feld **Organisation** an.
   * Ändern Sie den Site-Namen in den Namen der Site, die Sie im vorherigen Abschnitt erstellt haben. In diesem Beispiel wäre dies `wknd-prod`.
   * Ändern Sie den Projekttyp in **aem.live mit Konfigurations-Setup ohne Repo**.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

## Überprüfen Ihres Setups {#verify}

Nachdem Sie nun alle erforderlichen Konfigurationsänderungen vorgenommen haben, überprüfen Sie, ob alles erwartungsgemäß funktioniert.

1. Melden Sie sich bei Ihrer AEM-Produktions-Autoreninstanz an.
1. Navigieren Sie über **Navigation** -> **Sites** zur **Sites-Konsole**.
1. Wählen Sie in Ihrer Site eine Seite aus.
1. Tippen oder klicken Sie in der Symbolleiste auf **Bearbeiten**.
1. Stellen Sie sicher, dass die Seite im universellen Editor ordnungsgemäß gerendert wird und denselben Code wie der Site-Stamm verwendet.
1. Nehmen Sie eine Änderung an der Seite vor und veröffentlichen Sie sie erneut.
1. Besuchen Sie Ihre neue Edge Delivery Services-Site für diese Seite unter `https://main--wknd-prod--<your-github-org>.aem.page`.

Wenn die von Ihnen vorgenommenen Änderungen angezeigt werden, funktioniert das Setup der separaten Produktions-Site ordnungsgemäß.

## Verwendung {#usage}

Sobald Ihr Projekt mit Staging und Produktionsumgebungen ohne Repository konfiguriert ist, können Sie Code für beides unabhängig verwalten. Das folgende Diagramm zeigt das Verhältnis der Inhalte in Ihren verschiedenen Umgebungen in AEM, Edge Delivery Services-Sites und Ihren GitHub-Repositorys.

![Abbildung von AEM-Umgebungen und Produktions-/Staging-Umgebungen ohne Repository](assets/repoless/aem-edge-github.png)
