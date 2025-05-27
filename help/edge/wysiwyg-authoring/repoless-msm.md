---
title: Multi-Site-Management ohne Repository
description: Erfahren Sie mehr über Best-Practice-Empfehlungen zum Einrichten eines Projekts ohne Repository bei lokalisierten Sites mit einer einzigen, jeweils von Edge Delivery Services bereitgestellten Code-Basis.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: f6b861ed-18e4-4c81-92d2-49fadfe4669a
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '1260'
ht-degree: 100%

---

# Multi-Site-Management ohne Repository {#repoless-msm}

Erfahren Sie mehr über Best-Practice-Empfehlungen zum Einrichten eines Projekts ohne Repository bei lokalisierten Sites mit einer einzigen, jeweils von Edge Delivery Services bereitgestellten Code-Basis.

## Überblick {#overview}

[Multi-Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) und seine Live Copy-Funktionen ermöglichen Ihnen die Verwendung desselben Site-Inhalts sowie dessen Variationen an mehreren Orten. Sie können Inhalte einmal entwickeln und Live Copies davon erstellen. MSM behält Live-Beziehungen zwischen Quellinhalten und deren Live Copies bei, sodass beim Ändern des Quellinhalts die Quelle und die Live Copies synchronisiert werden können.

Sie können MSM verwenden, um eine gesamte Inhaltsstruktur für Ihre Marke über Gebietsschemata und Sprachen hinweg aufzubauen und die Inhalte zentral zu erstellen. Ihre lokalisierten Sites können dann jeweils über Edge Delivery Services bereitgestellt werden, bei Nutzung einer zentralen Code-Basis.

## Voraussetzungen {#requirements}

Um MSM in einem Anwendungsfall ohne Repository zu konfigurieren, müssen Sie zunächst die folgenden Aufgaben durchführen:

* In diesem Dokument wird vorausgesetzt, dass Sie bereits eine Site für Ihr Projekt auf Grundlage des [Erste-Schritte-Handbuchs für Entwickelnde zum WYSIWYG-Authoring mit Edge Delivery Services](/help/edge/wysiwyg-authoring/edge-dev-getting-started.md) erstellt haben.
* Sie müssen die [Funktion zum Einrichten ohne Repository bereits für Ihr Projekt aktiviert](/help/edge/wysiwyg-authoring/repoless.md) haben.

## Anwendungsfall {#use-case}

In diesem Dokument wird vorausgesetzt, dass Sie bereits eine grundlegende lokalisierte Site-Struktur für Ihr Projekt erstellt haben. Als Beispiel dient die folgende Struktur für die Marke WKND mit Präsenz in der Schweiz und in Deutschland.

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

Bei den Inhalten unter `language-masters` handelt es sich um die Quelle der Live Copies für die lokalisierten Sites: Deutschland (`de`) und Schweiz (`ch`). Ziel dieses Dokuments ist es, Edge Delivery Services-Sites zu erstellen, die allesamt dieselbe Code-Basis für jede lokalisierte Site nutzen.

## Konfiguration {#configuration}

Es gibt mehrere Schritte zum Konfigurieren des Anwendungsfalls „MSM ohne Repository“:

1. [Aktualisieren Sie die AEM-Site-Konfigurationen](#update-aem-configurations).
1. [Erstellen Sie neue Edge Delivery Services-Sites für die lokalisierten Seiten](#create-edge-sites).
1. [Aktualisieren Sie die Cloud-Konfiguration in AEM für die lokalisierten Sites](#update-cloud-configurations).

### Aktualisieren von AEM-Site-Konfigurationen {#update-aem-configurations}

Stellen Sie sich [Konfigurationen](/help/implementing/developing/introduction/configurations.md) als Arbeitsbereiche vor, mit denen sich Gruppen von Einstellungen sowie deren zugehörige Inhalte für organisatorische Zwecke zusammenfassen lassen. Bei der Erstellung einer Site in AEM wird automatisch auch eine entsprechende Konfiguration erstellt.

Im Allgemeinen sollten Sie bestimmte Inhalte zwischen Sites freigeben, z. B.:

* Vorlagen, die aus Inhalten im Blueprint erstellt wurden
* Inhaltsfragmentmodelle, persistiert, Abfragen usw.

Sie können zusätzliche Konfigurationen erstellen, um solche Freigaben zu erleichtern. Für den WKND-Anwendungsfall sind Konfigurationen für die folgenden Pfade erforderlich.

```text
/content/wknd
/content/wknd/ch
/content/wknd/de
```

Das heißt, Sie verfügen über eine Konfiguration für den Stamm des Inhalts der Marke WKND (`/content/wknd`), der von den Blueprints verwendet wird, und über eine Konfiguration, die von jeder lokalisierten Site (Schweiz und Deutschland) genutzt wird.

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
1. Navigieren Sie über **Tools** -> **Allgemein** -> **Konfigurationsbrowser** zum **Konfigurationsbrowser**.
1. Wählen Sie die Konfiguration aus, die automatisch für Ihr Projekt erstellt wurde (in diesem Fall „wknd“), und tippen oder klicken Sie dann in der Symbolleiste auf **Erstellen**.
1. Geben Sie im Dialogfeld **Konfiguration erstellen** einen beschreibenden **Namen** für Ihre lokalisierte Site ein (z. B. `Switzerland`) und verwenden Sie unter **Titel** denselben Titel der lokalisierten Site (in diesem Fall `ch`).
1. Wählen Sie die Funktion **Cloud-Konfiguration** und alle zusätzlichen Funktionen aus, die Sie ggf. für Ihr Projekt benötigen, z. B. **Bearbeitbare Vorlagen**.
1. Tippen oder klicken Sie auf **Erstellen**.

Erstellen Sie Konfigurationen für jede lokalisierte Site, die Sie benötigen. Im Fall von „wknd“ müssten Sie neben der Konfiguration `ch` eine Konfiguration für `de` erstellen.

Nachdem die Konfigurationen erstellt wurden, müssen Sie sicherstellen, dass sie von den lokalisierten Sites verwendet werden.

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
1. Navigieren Sie über **Navigation** -> **Sites** zur **Sites-Konsole**.
1. Wählen Sie die lokalisierte Site aus, z. B. `Switzerland`.
1. Tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften**.
1. Wählen Sie im Fenster „Seiteneigenschaften“ die Registerkarte **Erweitert** aus und heben Sie dann unter der Überschrift **Konfiguration** die Auswahl der Option **Vererbt von /content/wknd** auf. `wknd` steht dabei für den Site-Stamm.
1. Verwenden Sie im Feld **Cloud-Konfiguration** den Pfad-Browser, um die Konfiguration auszuwählen, die Sie für Ihre lokalisierte Site erstellt haben, z. B. `Switzerland` unter `/conf/wknd/ch`.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

Weisen Sie den zusätzlichen lokalisierten Sites die entsprechenden Konfigurationen zu. Im Fall von WKND müssten Sie neben der Konfiguration `/conf/wknd/de` auch eine Konfiguration für die Deutschland-Site erstellen.

### Erstellen neuer Edge Delivery Services-Sites für die lokalisierten Seiten {#create-edge-sites}

Um mehrere Sites mit Edge Delivery Services für eine regionenübergreifende, mehrsprachige Site-Einrichtung zu verbinden, müssen Sie für jede Ihrer AEM MSM-Sites eine neue aem.live-Site einrichten. Es gibt eine 1:1-Beziehung zwischen den AEM MSM-Sites und den aem.live-Sites mit einem gemeinsamen Git-Repository und einer Code-Basis.

In diesem Beispiel erstellen wir die Site `wknd-ch` für die schweizerische WKND-Präsenz, deren lokalisierte Inhalte sich unter dem AEM-Pfad `/content/wknd/ch` befinden.

1. Rufen Sie Ihr Authentifizierungs-Token und das technische Konto für Ihr Programm ab.
   * Weitere Informationen zum [Abrufen Ihres Zugriffs-Tokens](/help/edge/wysiwyg-authoring/repoless.md#access-token) und des [technischen Kontos](/help/edge/wysiwyg-authoring/repoless.md#access-control) für Ihr Programm finden Sie im Dokument **Wiederverwenden von Code in verschiedenen Sites**.
1. Erstellen Sie eine neue Site, indem Sie den folgenden Aufruf an den Konfigurations-Service ausführen. Bitte beachten:
   * Der Projektname in der POST-URL muss der Name der neuen Site sein, die Sie erstellen. In diesem Beispiel lautet er `wknd-ch`.
   * Die Konfiguration `code` sollte mit der für die anfängliche Projekterstellung verwendeten Konfiguration übereinstimmen.
   * Der Pfad `content` > `source` > `url` muss an den Namen der neuen Site angepasst werden, die Sie erstellen. In diesem Beispiel lautet er `wknd-ch`.
   * D. h., der Name der Site in der POST-URL und der Pfad `content` > `source` > `url` müssen identisch sein.
   * Passen Sie den Block `admin` an, um die Benutzenden zu definieren, die vollen administrativen Zugriff auf die Site haben sollen.
      * Es handelt sich um ein Array von E-Mail-Adressen.
      * Der Platzhalter `*` kann verwendet werden.
      * Weitere Informationen finden Sie im Dokument [Konfigurieren der Authentifizierung für Autorinnen und Autoren](https://www.aem.live/docs/authentication-setup-authoring?lang=de#default-roles).

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

1. Überprüfen Sie, ob die öffentliche Konfiguration Ihrer neuen Site funktioniert, indem Sie `https://main--wknd-ch--<your-github-org>.aem.page/config.json` aufrufen und den Inhalt der zurückgegebenen JSON-Datei verifizieren.

Wiederholen Sie die Schritte, um weitere lokalisierte Sites zu erstellen. Im Fall von WKND müssten Sie auch eine `wknd-de`-Site für die deutsche Präsenz erstellen.

### Aktualisieren der Cloud-Konfigurationen in AEM für die lokalisierten Seiten {#update-cloud-configurations}

Ihre Seiten in AEM müssen so konfiguriert sein, dass die neuen Edge Delivery-Sites verwendet werden, die Sie im vorherigen Abschnitt für Ihre lokalisierte Präsenz erstellt haben. In diesem Beispiel muss der Inhalt unter `/content/wknd/ch` wissen, dass die von Ihnen erstellte `wknd-ch`-Site verwendet werden soll. Entsprechend müssen Inhalte unter `/content/wknd/de` die `wknd-de`-Site verwenden.

1. Melden Sie sich bei der AEM-Autoreninstanz an und navigieren Sie zu **Tools** -> **Cloud Services** -> **Edge Delivery Services-Konfiguration**.
1. Wählen Sie die Konfiguration aus, die automatisch für Ihr Projekt erstellt wurde, und wählen Sie anschließend den Ordner aus, der für die lokalisierte Seite erstellt wurde. In diesem Fall wäre das die Schweiz (`ch`).
1. Tippen oder klicken Sie in der Symbolleiste auf **Erstellen** > **Konfiguration**.
1. Im Fenster **Edge Delivery Services-Konfiguration**:
   * Geben Sie Ihre GitHub-Organisation im Feld **Organisation** an.
   * Ändern Sie den Site-Namen in den Namen der Site, die Sie im vorherigen Abschnitt erstellt haben. In diesem Beispiel wäre dies `wknd-ch`.
   * Ändern Sie den Projekttyp in **aem.live mit Konfigurations-Setup ohne Repo**.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

## Überprüfen Ihres Setups {#verify}

Nachdem Sie nun alle erforderlichen Konfigurationsänderungen vorgenommen haben, überprüfen Sie, ob alles erwartungsgemäß funktioniert.

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an.
1. Navigieren Sie über **Navigation** -> **Sites** zur **Sites-Konsole**.
1. Wählen Sie die lokalisierte Site aus, z. B. `Switzerland`.
1. Tippen oder klicken Sie in der Symbolleiste auf **Bearbeiten**.
1. Stellen Sie sicher, dass die Seite im universellen Editor ordnungsgemäß gerendert wird und denselben Code wie der Site-Stamm verwendet.
1. Nehmen Sie eine Änderung an der Seite vor und veröffentlichen Sie sie erneut.
1. Besuchen Sie Ihre neue Edge Delivery Services-Site für diese lokalisierte Seite unter `https://main--wknd-ch--<your-github-org>.aem.page`.

Wenn die von Ihnen vorgenommenen Änderungen angezeigt werden, funktioniert das MSM-Setup ordnungsgemäß.
