---
title: Erste Schritte mit dem universellen Editor in AEM
description: Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 8357caf2b0d396f6a1bd7b6160d6b48d8d6c026c
workflow-type: tm+mt
source-wordcount: '627'
ht-degree: 87%

---


# Erste Schritte mit dem universellen Editor in AEM {#getting-started}

Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.

>[!TIP]
>
>Wenn Sie lieber direkt in ein Beispiel eintauchen möchten, können Sie die [Beispielanwendung des universellen Editors auf GitHub ansehen.](https://github.com/adobe/universal-editor-sample-editable-app)

Obwohl der universelle Editor Inhalte aus jeder Quelle bearbeiten kann, verwendet dieses Dokument eine AEM-App als Beispiel. Dieses Dokument führt Sie durch diese Schritte.

## Instrumentieren der Seite {#instrument-page}

Der universelle Editor erfordert eine JavaScript-Bibliothek, um die Seite im Editor zu rendern und zu bearbeiten.

Darüber hinaus erfordert der Service des universellen Editors einen [Uniform Resource Name (URN)](https://de.wikipedia.org/wiki/Uniform_Resource_Name), um das richtige Backend-System für den Inhalt in der bearbeiteten App zu identifizieren und zu verwenden. Daher ist ein URN-Schema erforderlich, um Inhalte wieder Inhaltsressourcen zuzuordnen.

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
* `<protocol>` – Dies gibt an, welches Persistenz-Plug-in des Universal Editor Persistence Service verwendet werden soll. Z. B. `aem`
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
<meta name="urn:adobe:aue:system:<referenceName>" content="<protocol>:<url>">

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

## Sie können den universellen Editor nun verwenden {#youre-ready}

Ihre App ist jetzt für die Verwendung des universellen Editors instrumentiert!

Unter [Inhaltserstellung mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Inhaltserstellung mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/publishing.md) – Erfahren Sie, wie der universelle Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Architektur des universellen Editors](architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.

