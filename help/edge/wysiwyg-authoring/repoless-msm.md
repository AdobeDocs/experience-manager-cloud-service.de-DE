---
title: Multi-Site-Management ohne Repo
description: Erfahren Sie mehr über Best Practices zum reaktionsschnellen Einrichten eines Projekts mit lokalisierten Sites, die eine einzige Code-Basis nutzen, die jeweils von Edge Delivery Services bereitgestellt wird.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: f6b861ed-18e4-4c81-92d2-49fadfe4669a
source-git-commit: 5715a07dc3e90e3781afa8d837394533ba419483
workflow-type: tm+mt
source-wordcount: '1261'
ht-degree: 2%

---

# Multi-Site-Management ohne Repo {#repoless-msm}

Erfahren Sie mehr über Best Practices zum reaktionsschnellen Einrichten eines Projekts mit lokalisierten Sites, die eine einzige Code-Basis nutzen, die jeweils von Edge Delivery Services bereitgestellt wird.

## Überblick {#overview}

[Multi Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) und seine Live Copy-Funktionen ermöglichen die Verwendung derselben Site-Inhalte an mehreren Orten und lassen gleichzeitig Varianten zu. Sie können Inhalte einmal erstellen und Live Copies erstellen. MSM behält Live-Beziehungen zwischen Quellinhalten und deren Live Copies bei, sodass beim Ändern des Quellinhalts die Quelle und die Live Copies synchronisiert werden können.

Sie können MSM verwenden, um eine gesamte Inhaltsstruktur für Ihre Marke über Gebietsschemata und Sprachen hinweg zu erstellen und die Inhalte zentral zu erstellen. Ihre lokalisierten Websites können dann von den jeweiligen Edge Delivery Services bereitgestellt werden, wobei eine zentrale Codebasis genutzt wird.

## Voraussetzungen {#requirements}

Um MSM in einem Anwendungsfall ohne Antwort zu konfigurieren, müssen Sie zunächst eine Reihe von Aufgaben abschließen.

* In diesem Dokument wird davon ausgegangen, dass Sie bereits eine Site für Ihr Projekt erstellt haben, die auf dem Handbuch [Erste Schritte für WYSIWYG-Entwickler mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) basiert.
* Sie müssen die [-Funktion bereits für Ihr Projekt aktiviert haben.](/help/edge/wysiwyg-authoring/repoless.md)

## Anwendungsfall {#use-case}

In diesem Dokument wird davon ausgegangen, dass Sie bereits eine grundlegende lokalisierte Site-Struktur für Ihr Projekt erstellt haben. Als Beispiel dient die folgende Struktur für die WKND-Marke mit Präsenz in der Schweiz und Deutschland.

```text
/content/wknd
/content/wknd/language-masters
/content/wknd/language-masters/en
/content/wknd/language-masters/de
/content/wknd/language-masters/fr
/content/wknd/language-masters/it
/content/wknd/ch
/content/wknd/ch/de
/content/wknd/ch/fr
/content/wknd/ch/it
/content/wknd/ch/en
/content/wknd/de
/content/wknd/de/de
/content/wknd/de/en
```

Die Inhalte in `language-masters` sind die Quelle der Live Copies für die lokalisierten Websites: Deutschland (`de`) und Schweiz (`ch`). Ziel dieses Dokuments ist es, Edge Delivery Services-Sites zu erstellen, die für jede lokalisierte Site dieselbe Codebasis verwenden.

## Konfiguration {#configuration}

Es gibt mehrere Schritte zum Konfigurieren des Anwendungsfalls „MSM-Antworten“.

1. [Aktualisieren Sie AEM-Site-Konfigurationen.](#update-aem-configurations)
1. [Erstellen Sie neue Edge Delivery Services-Sites für Ihre lokalisierten Seiten.](#create-edge-sites)
1. [Aktualisieren Sie die Cloud-Konfiguration in AEM für Ihre lokalisierten Sites.](#update-cloud-configurations)

### AEM-Site-Konfigurationen aktualisieren {#update-aem-configurations}

[Konfigurationen](/help/implementing/developing/introduction/configurations.md) können als Arbeitsbereiche betrachtet werden, die verwendet werden können, um Gruppen von Einstellungen und deren zugehörigen Inhalt für organisatorische Zwecke zu erfassen. Wenn Sie eine Site in AEM erstellen, wird automatisch eine -Konfiguration dafür erstellt.

Im Allgemeinen möchten Sie bestimmte Inhalte zwischen Sites freigeben, z. B.:

* Vorlagen, die aus Inhalten in der Blueprint erstellt wurden
* Inhaltsfragmentmodelle, persistente Abfragen usw.

Sie können zusätzliche Konfigurationen erstellen, um diese Freigabe zu erleichtern. Für den WKND-Anwendungsfall benötigen wir Konfigurationen für die folgenden Pfade.

```text
/content/wknd
/content/wknd/ch
/content/wknd/de
```

Das heißt, Sie verfügen über eine Konfiguration für den Stamm des Inhalts (`/content/wknd`) der WKND-Marke, der von den Blueprints verwendet wird, und eine Konfiguration, die von jeder lokalisierten Site (Schweiz und Deutschland) verwendet wird.

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
1. Navigieren Sie zum **Konfigurations** Browser unter **Tools** > **Allgemein** > **Konfigurations-Browser**.
1. Wählen Sie die Konfiguration aus, die automatisch für Ihr Projekt erstellt wurde (in diesem Fall WKND), und tippen oder klicken Sie dann auf **Erstellen** in der Symbolleiste.
1. Geben **im Dialogfeld „Konfiguration erstellen** einen beschreibenden **Name** für Ihre lokalisierte Site ein (z. B. `Switzerland`) und verwenden Sie für **Titel** denselben Titel der lokalisierten Größe (in diesem Fall `ch`).
1. Wählen Sie die **Cloud-Konfiguration**-Funktion und alle zusätzlichen Funktionen aus, die Sie für Ihr Projekt benötigen, z. B. **bearbeitbare Vorlagen**.
1. Tippen oder klicken Sie auf **Erstellen**.

Erstellen Sie Konfigurationen für jede lokalisierte Site, die Sie benötigen. Im Fall von wknd müssten Sie eine Konfiguration für `de` sowie die `ch`-Konfiguration erstellen.

Nachdem die Konfigurationen erstellt wurden, müssen Sie sicherstellen, dass sie von den lokalisierten Sites verwendet werden.

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
1. Navigieren Sie zur **Sites**-Konsole, indem Sie zu **Navigation** -> **Sites** wechseln.
1. Wählen Sie die lokalisierte Site aus, z. B. `Switzerland`.
1. Tippen oder klicken Sie **der Symbolleiste** Eigenschaften“.
1. Wählen Sie im Fenster „Seiteneigenschaften“ die Registerkarte **Erweitert** und heben Sie unter der Überschrift **Konfiguration** die Auswahl der Option **Übernommen von /content/wknd** auf, wobei `wknd` der Site-Stamm ist.
1. Verwenden **im Feld** Cloud-Konfiguration“ den Pfad-Browser, um die Konfiguration auszuwählen, die Sie für Ihre lokalisierte Site erstellt haben, z. B. `Switzerland` unter `/conf/wknd/ch`.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

Weisen Sie den zusätzlichen lokalisierten Sites die entsprechenden Konfigurationen zu. Im Fall von wknd müssen Sie die `/conf/wknd/de`-Konfiguration auch der Website Deutschland zuweisen.

### Erstellen Sie neue Edge Delivery Services-Sites für Ihre lokalisierten Seiten {#create-edge-sites}

Um mehrere Websites mit Edge Delivery Services für eine Einrichtung einer Website mit mehreren Regionen und Sprachen zu verbinden, müssen Sie für jede Ihrer AEM MSM-Websites eine neue Website aem.live einrichten. Es besteht eine 1:1-Beziehung zwischen AEM MSM-Sites und aem.live-Sites mit einem gemeinsamen Git-Repository und einer Code-Basis.

In diesem Beispiel erstellen wir die `wknd-ch` für die schweizerische Präsenz von wknd, dessen lokalisierter Inhalt sich unter dem AEM-Pfad `/content/wknd/ch` befindet.

1. Rufen Sie Ihr Authentifizierungs-Token und das technische Konto für Ihr Programm ab.
   * Lesen Sie das Dokument **Wiederverwenden von Code über Sites hinweg**, um Details zum [Abrufen Ihres Zugriffs-Tokens](/help/edge/wysiwyg-authoring/repoless.md#access-token) und zum [technischen Konto](/help/edge/wysiwyg-authoring/repoless.md#access-control) für Ihr Programm zu erhalten.
1. Erstellen Sie eine neue Site, indem Sie den folgenden Aufruf an den Konfigurations-Service ausführen. Bitte beachten Sie:
   * Der Projektname in der POST-URL muss der neue Site-Name sein, den Sie erstellen. In diesem Beispiel ist es `wknd-ch`.
   * Die `code` sollte mit der für die anfängliche Projekterstellung verwendeten Konfiguration übereinstimmen.
   * Der `content` > `source` > `url` muss an den Namen der neuen Site angepasst werden, die Sie erstellen. In diesem Beispiel ist es `wknd-ch`.
   * Das heißt, der Site-Name in der POST-URL und der `content` > `source` > `url` müssen identisch sein.
   * Passen Sie den `admin` an, um die Benutzer zu definieren, die vollen administrativen Zugriff auf die Website haben sollen.
      * Es handelt sich um ein Array von E-Mail-Adressen.
      * Der Platzhalter `*` verwendet werden.
      * Weitere Informationen finden Sie [ Dokument „Konfigurieren der ](https://www.aem.live/docs/authentication-setup-authoring#default-roles) für Autoren“.

   ```text
   curl --request POST \
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-ch.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
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
               "url": "https://author-p<programID>-e<environmentID>.adobeaemcloud.com/bin/franklin.delivery/<your-github-org>/wknd-ch/main",
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
     --url https://admin.hlx.page/config/<your-github-org>/sites/wknd-ch/public.json \
     --header 'Content-Type: application/json' \
     --header 'x-auth-token: <your-token>' \
     --data '{
       "paths": {
           "mappings": [
               "/content/wknd/ch/:/"
           ],
           "includes": [
               "/content/wknd/ch/"
           ]
       }
   }'
   ```

1. Überprüfen Sie, ob die öffentliche Konfiguration Ihrer neuen Site funktioniert, indem Sie `https://main--wknd-ch--<your-github-org>.aem.page/config.json` aufrufen und den Inhalt der zurückgegebenen JSON-Datei überprüfen.

Wiederholen Sie die Schritte, um weitere lokalisierte Sites zu erstellen. Im Falle von wknd müssten Sie auch eine `wknd-de` für die deutsche Präsenz erstellen.

### Aktualisieren Sie Cloud-Konfigurationen in AEM für Ihre lokalisierten Seiten {#update-cloud-configurations}

Ihre Seiten in AEM müssen so konfiguriert sein, dass die neuen Edge Delivery Sites verwendet werden, die Sie im vorherigen Abschnitt für Ihre lokalisierte Präsenz erstellt haben. In diesem Beispiel muss Inhalt unter `/content/wknd/ch` wissen, wie die von Ihnen erstellte `wknd-ch`-Site verwendet werden soll. Entsprechend müssen Inhalte unter `/content/wknd/de` die `wknd-de`-Site verwenden.

1. Melden Sie sich bei der AEM-Autoreninstanz an und gehen Sie zu **Tools** -> **Cloud Service** -> **Edge Delivery Services-Konfiguration**.
1. Wählen Sie die automatisch für Ihr Projekt erstellte Konfiguration und dann den Ordner aus, der für die lokalisierte Seite erstellt wurde. In diesem Fall wäre das die Schweiz (`ch`).
1. Tippen oder klicken Sie auf **Erstellen** > **Konfiguration** in der Symbolleiste.
1. Im Fenster **Edge Delivery Services** Konfiguration:
   * Geben Sie Ihre GitHub-Organisation im Feld **Organisation** an.
   * Ändern Sie den Site-Namen in den Namen der Site, die Sie im vorherigen Abschnitt erstellt haben. In diesem Fall wäre das `wknd-ch`.
   * Ändern Sie den Projekttyp in **aem.live mit repoless config setup**.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

## Überprüfen des Setups {#verify}

Nachdem Sie nun alle erforderlichen Konfigurationsänderungen vorgenommen haben, überprüfen Sie, ob alles erwartungsgemäß funktioniert.

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
1. Navigieren Sie zur **Sites**-Konsole, indem Sie zu **Navigation** -> **Sites** wechseln.
1. Wählen Sie die lokalisierte Site aus, z. B. `Switzerland`.
1. Tippen oder klicken Sie auf **Bearbeiten** in der Symbolleiste.
1. Stellen Sie sicher, dass die Seite im universellen Editor ordnungsgemäß gerendert wird und denselben Code wie den Stammordner Ihrer Site verwendet.
1. Nehmen Sie eine Änderung an der Seite vor und veröffentlichen Sie sie erneut.
1. Besuchen Sie Ihre neue Edge Delivery Services-Site für diese lokalisierte Seite unter `https://main--wknd-ch--<your-github-org>.aem.page`.

Wenn die von Ihnen vorgenommenen Änderungen angezeigt werden, funktioniert das MSM-Setup ordnungsgemäß.
