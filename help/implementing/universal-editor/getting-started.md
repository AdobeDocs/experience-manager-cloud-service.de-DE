---
title: Erste Schritte mit dem universellen Editor in AEM
description: Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
source-git-commit: 0bb649b91c42f43b852d7fdd54b367c0c5df2c99
workflow-type: tm+mt
source-wordcount: '921'
ht-degree: 100%

---


# Erste Schritte mit dem universellen Editor in AEM {#getting-started}

Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.

>[!TIP]
>
>Wenn Sie lieber direkt in ein Beispiel eintauchen möchten, können Sie die [Beispielanwendung des universellen Editors auf GitHub ansehen.](https://github.com/adobe/universal-editor-sample-editable-app)

## Onboarding-Schritte {#onboarding}

Obwohl der universelle Editor Inhalte aus jeder Quelle bearbeiten kann, verwendet dieses Dokument eine AEM-App als Beispiel.

Es gibt verschiedene Schritte für das Onboarding Ihrer AEM-App und ihre Instrumentierung für die Verwendung des universellen Editors.

1. [Fordern Sie Zugriff auf den universellen Editor an.](#request-access)
1. [Schließen Sie die Hauptbibliothek des universellen Editors ein.](#core-library)
1. [Fügen Sie die erforderliche OSGi-Konfiguration hinzu.](#osgi-configurations)
1. [Instrumentieren Sie die Seite.](#instrument-page)

Dieses Dokument führt Sie durch diese Schritte.

## Anfordern des Zugriffs auf den universellen Editor {#request-access}

Zunächst müssen Sie den Zugriff auf den universellen Editor anfordern. Öffnen Sie die Seite [https://experience.adobe.com/#/aem/editor](https://experience.adobe.com/#/aem/editor), melden Sie sich an und validieren Sie, ob Sie Zugriff auf den universellen Editor haben.

Wenn Sie keinen Zugriff haben, können Sie ihn über ein Formular anfordern, das auf derselben Seite verlinkt ist.

![Anfordern des Zugriffs auf den universellen Editor](assets/request-access.png)

Klicken Sie auf **Zugriff anfordern** und füllen Sie das Formular wie angewiesen aus, um Zugriff anzufordern. Eine Adobe-Kontaktperson wird Ihre Anfrage überprüfen und sich an Sie wenden, um Ihren Anwendungsfall zu besprechen.

## Einschließen der Hauptbibliothek des universellen Editors {#core-library}

Bevor Ihre App für die Verwendung mit dem universellen Editor instrumentiert werden kann, muss sie die folgende Abhängigkeit enthalten.

```javascript
@adobe/universal-editor-cors
```

Um die Instrumentierung zu aktivieren, muss der folgende Import zu Ihrer `index.js` hinzugefügt werden.

```javascript
import "@adobe/universal-editor-cors";
```

### Alternative für Nicht-React-Apps {#alternative}

Wenn Sie keine React-App implementieren und/oder Server-seitiges Rendering erforderlich ist, besteht eine alternative Methode darin, Folgendes in den Hauptteil des Dokuments einzuschließen.

```html
<script src="https://universal-editor-service.experiencecloud.live/corslib/LATEST" async></script>
```

Es wird immer die neueste Version empfohlen, im Bedarfsfall kann aber auch auf frühere Versionen des Service verwiesen werden.

* `https://universal-editor-service.experiencecloud.live/corslib/LATEST` - die neueste EU CORS-Bibliothek
* `https://universal-editor-service.experiencecloud.live/corslib/2/LATEST` – die neueste UE CORS-Bibliothek unter Version 2.x
* `https://universal-editor-service.experiencecloud.live/corslib/2.1/LATEST` – die neueste UE CORS-Bibliothek unter Version 2.1.x
* `https://universal-editor-service.experiencecloud.live/corslib/2.1.1`- die UE CORS-Bibliothek in der Version 2.1.1

## Hinzufügen der erforderlichen OSGi-Konfigurationen {#osgi-configurations}

Um AEM-Inhalte mit Ihrer App mithilfe des Universal Editors bearbeiten zu können, müssen die CORS- und Cookie-Einstellungen in AEM vorgenommen werden.

Die folgenden [OSGi-Konfigurationen müssen in der AEM-Autoreninstanz festgelegt werden.](/help/implementing/deploying/configuring-osgi.md)

* `SameSite Cookies = None` in `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler`
* Entfernen Sie die Kopfzeile X-FRAME-OPTIONS: SAMEORIGIN in `org.apache.sling.engine.impl.SlingMainServlet`

### com.day.crx.security.token.impl.impl.TokenAuthenticationHandler {#samesite-cookies}

Das Anmelde-Token-Cookie muss als Drittanbieter-Domain an AEM gesendet werden. Daher muss das same-site-Cookie explizit auf `None` gesetzt werden.

Diese Eigenschaft muss in der OSGi-Konfiguration `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler` eingestellt werden.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
          token.samesite.cookie.attr="None" />
```

### org.apache.sling.engine.impl.SlingMainServlet {#sameorigin}

X-Frame-Optionen: SAMEORIGIN verhindert das Rendern von AEM-Seiten in einem iFrame. Wenn Sie die Kopfzeile entfernen, können die Seiten geladen werden.

Diese Eigenschaft muss in der OSGi-Konfiguration `org.apache.sling.engine.impl.SlingMainServlet` eingestellt werden.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="sling:OsgiConfig"
          sling.additional.response.headers="[X-Content-Type-Options=nosniff]"/>
```

## Instrumentieren der Seite {#instrument-page}

Der Service des universellen Editors erfordert einen [Uniform Resource Name (URN)](https://de.wikipedia.org/wiki/Uniform_Resource_Name), um das richtige Backend-System für den Inhalt in der bearbeiteten App zu identifizieren und zu verwenden. Daher ist ein URN-Schema erforderlich, um Inhalte wieder Inhaltsressourcen zuzuordnen.

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
            <li data-aue-resource="urn:aemconnection/content/example/listitem" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">Jane Doe</p>
              <p data-aue-prop="title" data-aue-type="text">Journalist</p>
              <img data-aue-prop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" data-aue-type="image" alt="avatar"/>
            </li>

...

            <li data-aue-resource="urn:fcsconnection:/documents/mytext" data-aue-type="component">
              <p data-aue-prop="name" data-aue-type="text">John Smith</p>
              <p data-aue-resource="urn:aemconnection/content/example/another-source" data-aue-prop="title" data-aue-type="text">Photographer</p>
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
