---
title: Erste Schritte mit dem universellen Editor in AEM
description: Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8e1610e2835a9e85de2d2bffa6a883777c92fe96
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 100%

---


# Erste Schritte mit dem universellen Editor in AEM {#getting-started}

Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.

>[!TIP]
>
>Wenn Sie lieber direkt in ein Beispiel eintauchen möchten, können Sie die [Beispielanwendung des universellen Editors auf GitHub](https://github.com/adobe/universal-editor-sample-editable-app) ansehen.

Obwohl der universelle Editor Inhalte aus jeder Quelle bearbeiten kann, verwendet dieses Dokument eine AEM-App als Beispiel. Dieses Dokument führt Sie durch diese Schritte.

## Instrumentieren der Seite {#instrument-page}

Der universelle Editor erfordert eine JavaScript-Bibliothek, um die Seite im Editor zu rendern und zu bearbeiten.

Der Service des universellen Editors erfordert einen [Uniform Resource Name (URN)](https://de.wikipedia.org/wiki/Uniform_Resource_Name), um das richtige Backend-System für den Inhalt in der in Bearbeitung befindlichen App zu identifizieren und zu verwenden. Daher ist ein URN-Schema erforderlich, um Inhalte wieder Inhaltsressourcen zuzuordnen.

### Einschließen der CORS-Bibliothek des universellen Editors {#cors-library}

Damit der universelle Editor eine Verbindung zu Ihrer App herstellen kann, muss Ihre App die CORS-Bibliothek des universellen Editors enthalten. Fügen Sie das folgende Skript zu Ihrer App hinzu.

```html
 <script src="https://universal-editor-service.adobe.io/cors.js" async></script>
```

### Erstellen von Verbindungen {#connections}

Verbindungen, die in der App verwendet werden, werden als `<meta>`-Tags im `<head>` der Seite gespeichert.

```html
<meta name="urn:adobe:aue:<category>:<referenceName>" content="<protocol>:<url>">
```

* `<category>` – Dies ist eine Klassifizierung der Verbindung mit zwei Optionen.
   * `system` – Für Verbindungsendpunkte
   * `config` – Zum [Definieren optionaler Konfigurationseinstellungen](#configuration-settings).
* `<referenceName>` – Dies ist ein Kurzname, der im Dokument zur Identifizierung der Verbindung wiederverwendet wird. Z. B. `aemconnection`
* `<protocol>` – Dies gibt an, welches Persistenz-Plug-in des universellen Editors Persistence Service verwendet werden soll. Z. B. `aem`
* `<url>` – Dies ist die URL zum System, in dem die Änderungen persistiert werden sollen. Z. B. `http://localhost:4502`

Die Kennung `urn:adobe:aue:system` stellt die Verbindung des universellen Editors von Adobe dar.

`data-aue-resource`s verwenden das Präfix `urn`, um die Kennung zu verkürzen.

```html
data-aue-resource="urn:<referenceName>:<resource>"
```

* `<referenceName>` – Dies ist die im `<meta>`-Tag erwähnte Referenz. Z. B. `aemconnection`
* `<resource>` – Dies ist ein Zeiger auf die Ressource im Zielsystem. Z. B. ein AEM Inhaltspfad, wie `/content/page/jcr:content`

>[!TIP]
>
>Siehe das Dokument [Attribute und Typen](attributes-types.md) für weitere Details zu den Datenattributen und -typen, die der universelle Editor erfordert.

### Beispielverbindung {#example}

```html
<html>
<head>
    <meta name="urn:adobe:aue:system:aemconnection" content="aem:https://localhost:4502">
    <meta name="urn:adobe:aue:system:fcsconnection" content="fcs:https://example.franklin.adobe.com/345fcdd">
</head>
<body>
        <aside>
          <ul data-aue-resource="urn:aemconnection:/content/example/list" data-aue-type="container">
            <li data-aue-resource="urn:aemconnection:/content/example/listitem" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">Jane Doe</p>
              <p data-aue-prop="title" data-aue-type="text">Journalist</p>
              <img data-aue-prop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" data-aue-type="image" alt="avatar"/>
            </li>

...

            <li data-aue-resource="urn:fcsconnection:/documents/mytext" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">John Smith</p>
              <p data-aue-resource="urn:aemconnection:/content/example/another-source" data-aue-prop="title" data-aue-type="text">Photographer</p>
              <img data-aue-prop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" data-aue-type="image" alt="avatar"/>
            </li>
          </ul>
        </aside>
</body>
</html>
```

### Konfigurationseinstellungen {#configuration-settings}

Sie können das Präfix `config` in Ihrem Verbindungs-URN verwenden, um bei Bedarf Service- und Erweiterungsendpunkte festzulegen.

Wenn Sie nicht den von Adobe gehosteten Service „Universeller Editor“, sondern Ihre eigene gehostete Version verwenden möchten, können Sie dies in einem Meta-Tag festlegen. Um den vom universellen Editor bereitgestellten Standard-Service-Endpunkt zu überschreiben, legen Sie Ihren eigenen Service-Endpunkt fest:

* Metaname: `urn:adobe:aue:config:service`
* Metainhalt: `content="https://adobe.com"` (Beispiel)

```html
<meta name="urn:adobe:aue:config:service" content="<url>">
```

Wenn Sie nur bestimmte Erweiterungen für eine Seite aktivieren möchten, können Sie dies in einem Meta-Tag festlegen. Um Erweiterungen abzurufen, legen Sie die Erweiterungsendpunkte fest:

* Metaname: `urn:adobe:aue:config:extensions`
* Metainhalt: `content="https://adobe.com,https://anotherone.com,https://onemore.com"` (Beispiel)

```html
<meta name="urn:adobe:aue:config:extensions" content="<url>,<url>,<url>">
```

## Definieren, für welche Inhaltspfade oder `sling:resourceType`s der universelle Editor geöffnet werden soll. (Optional) {#content-paths}

Wenn Inhaltsautorinnen und -autoren bei einem vorhandenen AEM-Projekt, bei dem [der Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md) verwendet wird, Seiten bearbeiten, werden die Seiten automatisch mit dem Seiteneditor geöffnet. Sie können festlegen, welchen Editor AEM basierend auf den Inhaltspfaden oder dem `sling:resourceType` öffnen soll. Dadurch profitieren Ihre Autorinnen und Autoren von einem nahtlosen Erlebnis, unabhängig davon, welcher Editor für die ausgewählten Inhalte erforderlich ist.

1. Öffnen Sie den Configuration Manager. 

   `http://<host>:<port>/system/console/configMgr`

1. Suchen Sie **Universal Editor URL Service** in der Liste und klicken Sie auf **Edit the configuration values** (Konfigurationswerte bearbeiten).

1. Definieren Sie, für welche Inhaltspfade oder `sling:resourceType`s der universelle Editor geöffnet werden soll.

   * Geben Sie im Feld **Universal Editor Opening Mapping** (Universeller Editor – Zuordnung zum Öffnen) die Pfade an, für die der universelle Editor geöffnet wird.
   * Geben Sie im Feld **Sling:resourceTypes which shall be opened by Universal Editor** (sling:resourceTypes, die vom universellen Editor geöffnet werden sollen) eine Liste der Ressourcen an, die direkt vom universellen Editor geöffnet werden.

1. Klicken Sie auf **Speichern**.

1. Überprüfen Sie Ihre [Externalizer-Konfiguration](/help/implementing/developing/tools/externalizer.md) und stellen Sie sicher, dass Sie zumindest die lokale Umgebung sowie die Autoren- und Veröffentlichungsumgebung wie im folgenden Beispiel festgelegt haben.

   ```text
   "local $[env:AEM_EXTERNALIZER_LOCAL;default=http://localhost:4502]",
   "author $[env:AEM_EXTERNALIZER_AUTHOR;default=http://localhost:4502]",
   "publish $[env:AEM_EXTERNALIZER_PUBLISH;default=http://localhost:4503]"
   ```

Sobald diese Konfigurationsschritte abgeschlossen sind, öffnet AEM den universellen Editor für Seiten in der folgenden Reihenfolge.

1. AEM prüft die Zuordnungen unter `Universal Editor Opening Mapping`. Wenn sich der Inhalt unter einem der dort definierten Pfade befindet, wird der universelle Editor dafür geöffnet.
1. Bei Inhalten, die nicht unter den in `Universal Editor Opening Mapping` definierten Pfaden liegen, überprüft AEM, ob der `resourceType` des Inhalts mit den in **Sling:resourceTypes definierten übereinstimmt, die vom universellen Editor** geöffnet werden sollen. Wenn der Inhalt mit einem dieser Typen übereinstimmt, wird der universelle Editor dafür unter `${author}${path}.html` geöffnet.
1. Andernfalls öffnet AEM den Seiteneditor.

Die folgenden Variablen stehen zur Definition Ihrer Zuordnungen im Feld **Universal Editor Opening Mapping** (Universeller Editor – Zuordnung zum Öffnen) zur Verfügung.

* `path`: Inhaltspfad der zu öffnenden Ressource
* `localhost`: Externalizer-Eintrag für `localhost` ohne Schema, z. B. `localhost:4502`
* `author`: Externalizer-Eintrag für die Autorin bzw. den Autor ohne Schema, z. B. `localhost:4502`
* `publish`: Externalizer-Eintrag für die Veröffentlichung ohne Schema, z. B. `localhost:4503`
* `preview`: Externalizer-Eintrag für die Vorschau ohne Schema, z. B. `localhost:4504`
* `env`: `prod`, `stage`, `dev` basierend auf den definierten Sling-Ausführungsmodi
* `token`: Für `QueryTokenAuthenticationHandler` erforderliches Abfrage-Token

### Beispielzuordnungen {#example-mappings}

* Öffnen Sie alle Seiten unter `/content/foo` in der AEM-Autoreninstanz:

   * `/content/foo:${author}${path}.html?login-token=${token}`
   * Dadurch wird `https://localhost:4502/content/foo/x.html?login-token=<token>` geöffnet.

* Öffnen Sie alle Seiten unter `/content/bar` auf einem NextJS-Remote-Server und geben Sie alle Variablen als Informationen an:

   * `/content/bar:nextjs.server${path}?env=${env}&author=https://${author}&publish=https://${publish}&login-token=${token}`
   * Dadurch wird `https://nextjs.server/content/bar/x?env=prod&author=https://localhost:4502&publish=https://localhost:4503&login-token=<token>` geöffnet.

## Sie können den universellen Editor nun verwenden {#youre-ready}

Ihre App ist jetzt für die Verwendung des universellen Editors instrumentiert!

Unter [Inhaltserstellung mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.

{{ue-headless-auth}}

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Inhaltserstellung mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](/help/implementing/universal-editor/publishing.md) – Erfahren Sie, wie der universelle Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Architektur des universellen Editors](architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.

