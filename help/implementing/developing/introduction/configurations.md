---
title: Konfigurationen und der Konfigurations-Browser
description: Machen Sie sich mit Adobe Experience Manager-Konfigurationen (AEM) und der Verwaltung von Workspace-Einstellungen in AEM vertraut.
exl-id: 0ade04df-03a9-4976-a4b7-c01b4748474d
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1487'
ht-degree: 55%

---

# Konfigurationen und der Konfigurations-Browser {#configuration-browser}

Adobe Experience Manager-Konfigurationen (AEM) dienen zur Verwaltung von Einstellungen in AEM und dienen als Arbeitsbereiche.

## Was ist eine Konfiguration? {#what-is-a-configuration}

Eine Konfiguration kann aus zwei verschiedenen Blickwinkeln betrachtet werden.

* [Ein Administrator](#configurations-administrator) verwendet Konfigurationen als Arbeitsbereiche in AEM, um Gruppen von Einstellungen zu definieren und zu verwalten.
* [Ein Entwickler](#configurations-developer) verwendet den zugrunde liegenden Konfigurationsmechanismus, der Konfigurationen implementiert, um Einstellungen in AEM beizubehalten und einzusehen.

Zusammenfassend: Aus Sicht eines Administrators sind Konfigurationen das Erstellen von Arbeitsbereichen zum Verwalten von Einstellungen in AEM, während der Entwickler verstehen sollte, wie AEM diese Konfigurationen im Repository verwendet und verwaltet.

Unabhängig von Ihrem Blickwinkel dienen Konfigurationen in AEM zwei Hauptzwecken:

* Konfigurationen ermöglichen bestimmte Funktionen für bestimmte Benutzergruppen.
* Konfigurationen definieren Zugriffsrechte für diese Funktionen.

## Konfigurationen als Administrator {#configurations-administrator}

AEM-Admins und Autorinnen bzw. Autoren können Konfigurationen als Arbeitsbereiche betrachten. Diese Arbeitsbereiche können verwendet werden, um Gruppen von Einstellungen und zugehörigen Inhalten für organisatorische Zwecke zu sammeln, indem Zugriffsberechtigungen für diese Funktionen implementiert werden.

Konfigurationen können für viele verschiedene Funktionen in AEM erstellt werden.

* [Context-Hub-Segmente](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)
* [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)
* [Bearbeitbare Vorlagen](/help/sites-cloud/authoring/features/templates.md)
* verschiedene Cloud-Konfigurationen

### Beispiel {#administrator-example}

Admins können beispielsweise zwei Konfigurationen für bearbeitbare Vorlagen erstellen.

* WKND-General
* WKND-Magazin

Der Administrator kann dann allgemeine Seitenvorlagen mit der Konfiguration „WKND-General“ und magazinspezifische Vorlagen unter „WKND-Magazin“ erstellen.

Der Administrator kann dann „WKND-General“ mit allen Inhalten der WKND-Site verknüpfen. Die Konfiguration „WKND-Magazin“ würde jedoch nur mit der Magazin-Site verknüpft.

Dies geschieht folgendermaßen:

* Wenn ein Inhaltsautor eine Seite für die Zeitschrift erstellt, kann der Autor aus allgemeinen Vorlagen (WKND-General) oder Zeitschriftenvorlagen (WKND-Magazine) wählen.
* Wenn ein Inhaltsautor eine Seite für einen anderen Teil der Site erstellt, der nicht das Magazin ist, kann der Autor nur aus den allgemeinen Vorlagen (WKND-General) wählen.

Ähnliche Setups sind nicht nur für bearbeitbare Vorlagen möglich, sondern auch für Cloud-Konfigurationen, ContextHub-Segmente und Inhaltsfragmentmodelle.

### Verwenden des Konfigurations-Browsers {#using-configuration-browser}

Mit dem Konfigurations-Browser kann ein Administrator auf einfache Weise Zugriffsrechte für Konfigurationen in AEM erstellen, verwalten und konfigurieren.

>[!NOTE]
>
>Es ist nur möglich, Konfigurationen mithilfe des Konfigurations-Browsers zu erstellen, wenn Ihr Benutzer `admin` Rechte. Solche `admin` -Berechtigungen sind auch erforderlich, um der Konfiguration Zugriffsrechte zuzuweisen oder eine Konfiguration anderweitig zu ändern.

#### Erstellen einer Konfiguration {#creating-a-configuration}

Es ist einfach, eine Konfiguration in AEM mithilfe des Konfigurationsbrowsers zu erstellen.

1. Melden Sie sich bei AEM as a Cloud Service an und wählen Sie im Hauptmenü die Option **Instrumente** > **Allgemein** > **Konfigurationsbrowser**.
1. Wählen Sie **Erstellen** aus.
1. Geben Sie einen **Titel** und einen **Namen** für Ihre Konfiguration an.

   ![Erstellen einer Konfiguration](assets/configuration-create.png)

   * Der **Titel** sollte beschreibend sein.
   * Der **Name** wird zum Knotennamen im Repository.
      * Er wird automatisch auf der Grundlage des Titels generiert und gemäß den [AEM-Benennungskonventionen](naming-conventions.md) angepasst.
      * Er kann bei Bedarf angepasst werden.
1. Überprüfen Sie den Konfigurationstyp, den Sie zulassen möchten.
   * [Context-Hub-Segmente](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md)
   * [Inhaltsfragmentmodelle](/help/sites-cloud/administering/content-fragments/content-fragment-models.md)
   * [Bearbeitbare Vorlagen](/help/sites-cloud/authoring/features/templates.md)
   * verschiedene Cloud-Konfigurationen
1. Wählen Sie **Erstellen** aus.

>[!TIP]
>
>Konfigurationen können verschachtelt sein.

#### Bearbeiten von Konfigurationen und deren Zugriffsrechten {#access-rights}

Wenn Sie Konfigurationen als Workspace betrachten, können Zugriffsrechte für diese Konfigurationen festgelegt werden, um zu erzwingen, wer auf diesen Workspace zugreifen darf und wer nicht.

1. Melden Sie sich bei AEM as a Cloud Service an und wählen Sie im Hauptmenü die Option **Instrumente** > **Allgemein** > **Konfigurationsbrowser**.
1. Wählen Sie die Konfiguration aus, die Sie bearbeiten möchten, und klicken Sie auf **Eigenschaften** in der Symbolleiste.
1. Wählen Sie zusätzliche Funktionen aus, die Sie der Konfiguration hinzufügen möchten.

   >[!NOTE]
   >
   >Es ist nicht möglich, die Auswahl einer Funktion aufzuheben, nachdem die Konfiguration erstellt wurde.

1. Verwenden Sie die Schaltfläche **Gültige Berechtigungen**, um eine Matrix der Rollen und der ihnen derzeit gewährten Berechtigungen für Konfigurationen anzuzeigen.
   ![Fenster „Gültige Berechtigungen“](assets/configuration-effective-permissions.png)
1. Um neue Berechtigungen zuzuweisen, geben Sie den Benutzer- oder Gruppennamen in das Feld **Benutzer oder Gruppe wählen** im Abschnitt **Neue Berechtigung hinzufügen** ein.
   * Das Feld **Benutzer oder Gruppe wählen** bietet eine automatische Vervollständigung basierend auf vorhandenen Benutzern und Rollen.
1. Wählen Sie den entsprechenden Benutzer oder die entsprechende Rolle aus den Ergebnissen der automatischen Vervollständigung aus.
   * Sie können mehrere Benutzer oder Rollen auswählen.
1. Aktivieren Sie die Zugriffsoptionen, die einem oder mehreren ausgewählten Benutzern oder Rollen zugewiesen werden sollen, und klicken Sie auf **Hinzufügen**.
   ![Zugriffsrechte zu einer Konfiguration hinzufügen](assets/configuration-edit.png)
1. Wiederholen Sie die Schritte, damit Sie Benutzer oder Rollen auswählen und bei Bedarf zusätzliche Zugriffsberechtigungen zuweisen können.
1. Auswählen **Speichern und schließen** wenn fertig.

## Konfigurationen als Entwickler {#configurations-developer}

Als Entwickler ist es wichtig zu wissen, wie AEM as a Cloud Service mit Konfigurationen funktioniert und wie eine Konfigurationsauflösung verarbeitet wird.

### Trennung von Konfiguration und Inhalt {#separation-of-config-and-content}

Obwohl der [Administrator und die Benutzer Konfigurationen möglicherweise als Arbeitsplätze](#configurations-administrator) zum Verwalten unterschiedlicher Einstellungen und Inhalte betrachten, ist es wichtig zu verstehen, dass Konfigurationen und Inhalte von AEM separat im Repository gespeichert und verwaltet werden.

* `/content` nimmt alle Inhalte auf.
* `/conf` nimmt alle Konfigurationen auf.

Der Inhalt verweist auf die zugehörige Konfiguration über eine `cq:conf` -Eigenschaft. AEM führt eine Suche basierend auf dem Inhalt und dem Kontext durch `cq:conf` -Eigenschaft, um die entsprechende Konfiguration zu finden.

### Beispiel {#developer-example}

Nehmen wir für dieses Beispiel an, Sie haben Programm-Code, der an DAM-Einstellungen interessiert ist.

```java
Conf conf = resource.adaptTo(Conf.class);
ValueMap imageServerSettings = conf.getItem("dam/imageserver");
String bgkcolor = imageServerSettings.get("bgkcolor", "FFFFFF");
```

Der Ausgangspunkt der gesamten Konfigurationssuche ist eine Inhaltsressource unter `/content`. Dabei kann es sich um eine Seite, eine Komponente innerhalb einer Seite, ein Asset oder einen DAM-Ordner handeln. Dies ist der eigentliche Inhalt, für den Sie die richtige Konfiguration suchen, die in diesem Zusammenhang gilt.

Jetzt mit dem `Conf` -Objekt, können Sie das spezifische Konfigurationselement abrufen, an dem Sie interessiert sind. In diesem Fall ist es `dam/imageserver`, eine Sammlung von Einstellungen, die sich auf die `imageserver`. Der Aufruf `getItem` gibt ein `ValueMap` zurück. Sie lesen dann `bgkcolor` Zeichenfolgeneigenschaft und geben Sie den Standardwert &quot;FFFF&quot;an, falls die Eigenschaft (oder das gesamte Konfigurationselement) nicht vorhanden ist.

Sehen wir uns nun den entsprechenden JCR-Inhalt an:

```text
/content/dam/wknd
    + jcr:content
      - cq:conf = "/conf/wknd"
    + image.png [dam:Asset]

/conf/wknd
    + settings
      + dam
        + imageserver [cq:Page]
          + jcr:content
            - bgkcolor = "FF0000"
```

In diesem Beispiel können Sie von einem WKND-spezifischen DAM-Ordner hier und einer entsprechenden Konfiguration ausgehen. Beginnt bei diesem Ordner `/content/dam/wknd`, können Sie sehen, dass es eine Zeichenfolgeneigenschaft mit dem Namen `cq:conf` , der auf die Konfiguration verweist, die für die Unterstruktur gilt. Die Eigenschaft wird auf die `jcr:content` eines Asset-Ordners oder einer Seite. Diese `conf`-Links sind explizit, sodass es einfach ist, ihnen zu folgen, indem Sie sich den Inhalt in CRXDE ansehen.

Springen hinein `/conf`, folgen Sie der Referenz und sehen Sie, dass es eine `/conf/wknd` Knoten. Dies ist eine Konfiguration. Die Suche ist für den Anwendungscode transparent. Der Beispiel-Code hat nie eine dedizierte Referenz darauf, sie ist hinter dem `Conf`-Objekt versteckt. Welche Konfiguration angewendet wird, wird über den JCR-Inhalt gesteuert.

Sie sehen, dass die Konfiguration einen fest benannten `settings` -Knoten, der die tatsächlichen Elemente enthält, einschließlich der `dam/imageserver` benötigen Sie in diesem Fall. Ein solches Element kann als &quot;Einstellungsdokument&quot;betrachtet werden und wird durch ein `cq:Page` einschließlich `jcr:content` den tatsächlichen Inhalt enthalten.

Schließlich sehen Sie die -Eigenschaft `bgkcolor` , die dieser Beispielcode benötigt. Die `ValueMap` zurück von `getItem` basiert auf dem `jcr:content` Knoten.

### Konfigurationsauflösung {#configuration-resolution}

Das grundlegende Beispiel oben zeigte eine einzelne Konfiguration. Es gibt jedoch viele Fälle, in denen Sie unterschiedliche Konfigurationen haben möchten, z. B. eine standardmäßige globale Konfiguration, eine andere für jede Marke und möglicherweise eine spezifische für Ihre Unterprojekte.

Um dies bei der Konfigurationssuche zu unterstützen, verfügt AEM über einen Vererbungs- und Ausweichmechanismus in der folgenden Reihenfolge der Voreinstellung:

1. `/conf/<siteconfig>/<parentconfig>/<myconfig>`
   * Spezifische Konfiguration, auf die von `cq:conf` irgendwo in `/content` verwiesen wird
   * Die Hierarchie ist willkürlich und kann genau wie Ihre Site-Struktur entworfen werden, es ist nicht Aufgabe des Programm-Codes, dies zu wissen
   * Zur Laufzeit durch Benutzer mit Konfigurationsrechten änderbar
1. `/conf/<siteconfig>/<parentconfig>`
   * Übergeordnete Elemente für Ausweichkonfigurationen
   * Zur Laufzeit durch Benutzer mit Konfigurationsrechten änderbar
1. `/conf/<siteconfig>`
   * Übergeordnete Elemente für Ausweichkonfigurationen
   * Zur Laufzeit durch Benutzer mit Konfigurationsrechten änderbar
1. `/conf/global`
   * Globale Systemeinstellungen
   * Globale Standardeinstellungen für Ihre Installation
   * Durch eine `admin`-Rolle festgelegt
   * Zur Laufzeit durch Benutzer mit Konfigurationsrechten änderbar
1. `/apps`
   * Programmstandardwerte
   * Mit der Programmbereitstellung festgelegt
   * Zur Laufzeit schreibgeschützt
1. `/libs`
   * AEM-Produktstandardwerte
   * Nur von Adobe änderbar, Projektzugriff nicht erlaubt
   * Mit der Programmbereitstellung festgelegt
   * Zur Laufzeit schreibgeschützt

### Verwenden von Konfigurationen {#using-configurations}

Die Konfigurationen in AEM basieren auf kontextabhängigen Sling-Konfigurationen. Die Sling-Bundles bieten eine Dienst-API, mit der kontextabhängige Konfigurationen abgerufen werden können. Kontextabhängige Konfigurationen sind Konfigurationen, die sich auf eine Inhaltsressource oder eine Ressourcenstruktur beziehen, wie sie war [im vorherigen Beispiel beschrieben](#developer-example).

Weitere Informationen zu kontextsensitiven Konfigurationen, Beispielen und deren Verwendung finden Sie unter [Sling-Dokumentation.](https://sling.apache.org/documentation/bundles/context-aware-configuration/context-aware-configuration.html).

### ConfMgr-Web-Konsole {#confmgr-web-console}

Zu Debuggings- und Testzwecken gibt es eine **ConfMgr**-Web-Konsole unter `https://<host>:<port>/system/console/conf`, die Konfigurationen für einen bestimmten Pfad/ein bestimmtes Element anzeigen kann.

![ConfMgr](assets/configuration-confmgr.png)

Geben Sie einfach Folgendes an:

* **Inhalts-Pfad**
* **Element**
* **Benutzer**

Klicks **Auflösen** damit Sie sehen können, welche Konfigurationen aufgelöst wurden, und Codebeispiele erhalten, die zur Lösung dieser Konfigurationen beitragen.

### Web-Konsole für kontextabhängige Konfigurationen {#context-aware-web-console}

Zu Debuggings- und Testzwecken gibt es eine Web-Konsole für **kontextabhängige Konfigurationen** unter `https://<host>:<port>/system/console/slingcaconfig`, mit der Sie kontextabhängige Konfigurationen im Repository abfragen und ihre Eigenschaften anzeigen können.

![Web-Konsole für kontextabhängige Konfigurationen](assets/configuration-context-aware-console.png)

Geben Sie einfach Folgendes an:

* **Inhalts-Pfad**
* **Konfigurationsname**

Klicks **Auflösen** sodass Sie die zugehörigen Kontextpfade und Eigenschaften für die ausgewählte Konfiguration abrufen können.
