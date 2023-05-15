---
title: Erste Schritte mit dem universellen Editor in AEM
description: Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM App beginnen, diese zu verwenden.
exl-id: 9091a29e-2deb-4de7-97ea-53ad29c7c44d
source-git-commit: de33ea3efed87170b081ea467f12a997e0d41a83
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---

# Erste Schritte mit dem universellen Editor in AEM {#getting-started}

Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM App beginnen, diese zu verwenden.

>[!TIP]
>
>Wenn Sie lieber direkt in ein Beispiel eintauchen möchten, können Sie die [Universal Editor-Beispielanwendung auf GitHub.](https://github.com/adobe/universal-editor-sample-editable-app)

## Onboarding-Schritte {#onboarding}

Obwohl der universelle Editor Inhalte aus jeder Quelle bearbeiten kann, verwendet dieses Dokument eine AEM App als Beispiel.

Es gibt eine Reihe von Schritten, um Ihre AEM App zu integrieren und sie für die Verwendung des universellen Editors zu instrumentieren.

1. [Fordern Sie Zugriff auf den universellen Editor an.](#request-access)
1. [Schließen Sie die Hauptbibliothek des universellen Editors ein.](#core-library)
1. [Fügen Sie die erforderliche OSGi-Konfiguration hinzu.](#osgi-configurations)
1. [Instrumentieren Sie die Seite.](#instrument-page)

Dieses Dokument führt Sie durch diese Schritte.

## Zugriff auf den universellen Editor anfordern {#request-access}

Zunächst müssen Sie den Zugriff auf den universellen Editor anfordern. Bitte gehen Sie zu [https://experience.adobe.com/#/aem/editor,](https://experience.adobe.com/#/aem/editor) anmelden und überprüfen, ob Sie Zugriff auf den universellen Editor haben.

Wenn Sie keinen Zugriff haben, können Sie ihn über ein Formular anfordern, das auf derselben Seite verlinkt ist.

![Zugriff auf den universellen Editor anfordern](assets/request-access.png)

Klicken **Zugriff anfordern** und füllen Sie das Formular wie beschrieben aus, um Zugriff anzufordern. Ein Mitarbeiter der Adobe wird Ihre Anfrage überprüfen und sich an Sie wenden, um Ihren Anwendungsfall zu besprechen.

## Universelle Editor-Core-Bibliothek einschließen {#core-library}

Bevor Ihre App für die Verwendung mit dem universellen Editor instrumentiert werden kann, muss sie die folgende Abhängigkeit enthalten.

```javascript
@adobe/universal-editor-cors
```

Um die Instrumentierung zu aktivieren, muss der folgende Import zu Ihrer `index.js`.

```javascript
import "@adobe/universal-editor-cors";
```

### Alternative für Nicht-React-Apps {#alternative}

Wenn Sie keine React-App implementieren und/oder serverseitiges Rendering erfordern, besteht eine alternative Methode darin, Folgendes in den Hauptteil des Dokuments einzuschließen.

```html
<script src="https://cdn.jsdelivr.net/gh/adobe/universal-editor-cors/dist/universal-editor-embedded.js" async></script>
```

## Hinzufügen der erforderlichen OSGi-Konfigurationen {#osgi-configurations}

Um AEM Inhalt mit Ihrer App mithilfe des universellen Editors bearbeiten zu können, müssen die Einstellungen für CORS und Cookie in AEM vorgenommen werden.

Folgendes [OSGi-Konfigurationen müssen in der AEM Authoring-Instanz festgelegt werden.](/help/implementing/deploying/configuring-osgi.md)

* `SameSite Cookies = None` in `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler`
* Entfernen Sie X-FRAME-OPTIONS: SAMEORIGIN-Kopfzeile in `org.apache.sling.engine.impl.SlingMainServlet`

### com.day.crx.security.token.impl.impl.TokenAuthenticationHandler {#samesite-cookies}

Das Anmeldetoken-Cookie muss als Drittanbieterdomäne an AEM gesendet werden. Daher muss das Cookie der gleichen Site explizit auf `None`.

Diese Eigenschaft muss im `com.day.crx.security.token.impl.impl.TokenAuthenticationHandler` OSGi-Konfiguration.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0" jcr:primaryType="sling:OsgiConfig"
          token.samesite.cookie.attr="None" />
```

### org.apache.sling.engine.impl.SlingMainServlet {#sameorigin}

X-Frame-Options: SAMEORIGIN verhindert das Rendern AEM Seiten in einem iframe. Wenn Sie die Kopfzeile entfernen, können die Seiten geladen werden.

Diese Eigenschaft muss im `org.apache.sling.engine.impl.SlingMainServlet` OSGi-Konfiguration.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<jcr:root xmlns:sling="http://sling.apache.org/jcr/sling/1.0"
          xmlns:jcr="http://www.jcp.org/jcr/1.0"
          jcr:primaryType="sling:OsgiConfig"
          sling.additional.response.headers="[X-Content-Type-Options=nosniff]"/>
```

## Instrumentieren der Seite {#instrument-page}

Der Universal Editor-Dienst erfordert eine [Uniform Resource Name (URN)](https://en.wikipedia.org/wiki/Uniform_Resource_Name) , um das richtige Backend-System für den Inhalt der in Bearbeitung befindlichen App zu identifizieren und zu verwenden. Daher ist ein URN-Schema erforderlich, um Inhalte wieder Inhaltsressourcen zuzuordnen.

Die der Seite hinzugefügten Instrumentenattribute bestehen hauptsächlich aus [HTML Microdata,](https://developer.mozilla.org/en-US/docs/Web/HTML/Microdata) ein Industriestandard, der auch verwendet werden kann, um HTML semantischer zu machen, HTML-Dokumente zu indexieren, usw.

### Erstellen von Verbindungen {#connections}

In der App verwendete Verbindungen werden als `<meta>` Tags in der Seite `<head>`.

```html
<meta name="urn:adobe:aem:editor:<referenceName>" content="<protocol>:<url>">
```

* `<referenceName>` - Dies ist ein Kurzname, der im Dokument zur Identifizierung der Verbindung wiederverwendet wird. z. B. `aemconnection`
* `<protocol>` - Dies gibt an, welches Persistenzplugin des Universal Editor Persistence Service verwendet werden soll. z. B. `aem`
* `<url>` - Dies ist die URL zum System, in dem die Änderungen beibehalten werden sollen. z. B. `http://localhost:4502`

Die Kennung `adobe:aem:editor` stellt die Verbindung für den Adobe Universal Editor dar.

`itemid`verwendet die `urn` -Präfix, um die Kennung zu verkürzen.

```html
itemid="urn:<referenceName>:<resource>"
```

* `<referenceName>` - Dies ist die benannte Referenz, die in der `<meta>` -Tag. z. B. `aemconnection`
* `<resource>` - Dies ist ein Zeiger auf die Ressource im Zielsystem. Beispiel: AEM Inhaltspfad, z. B. `/content/page/jcr:content`

>[!TIP]
>
>Siehe Dokument . [Attribute und Typen](attributes-types.md) für weitere Details zu den Datenattributen und -typen, die der universelle Editor erfordert.

### Beispielverbindung {#example}

```html
<html>
<head>
    <meta name="urn:adobe:aem:editor:aemconnection" content="aem:https://localhost:4502">
    <meta name="urn:adobe:aem:editor:fcsconnection" content="fcs:https://example.franklin.adobe.com/345fcdd">
</head>
<body>
        <aside>
          <ul itemscope itemid="urn:aemconnection:/content/example/list" itemtype="container">
            <li itemscope itemid="urn:aemconnection/content/example/listitem" itemtype="component">
              <p itemprop="name" itemtype="text">Jane Doe</p>
              <p itemprop="title" itemtype="text">Journalist</p>
              <img itemprop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" itemtype="image" alt="avatar"/>
            </li>
 
...
 
            <li itemscope itemid="urn:fcsconnection:/documents/mytext" itemtype="component">
              <p itemprop="name" itemtype="text">John Smith</p>
              <p itemid="urn:aemconnection/content/example/another-source" itemprop="title" itemtype="text">Photographer</p>
              <img itemprop="avatar" src="https://www.adobe.com/content/dam/cc/icons/Adobe_Corporate_Horizontal_Red_HEX.svg" itemtype="image" alt="avatar"/>
            </li>
          </ul>
        </aside>
</body>
</html>
```

## Sie können den universellen Editor verwenden {#youre-ready}

Ihre App ist jetzt für die Verwendung des Universal Editors instrumentiert!

Weitere Informationen finden Sie im Dokument . [Inhaltserstellung mit dem universellen Editor](authoring.md) um zu erfahren, wie einfach und intuitiv es für Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) - Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Inhaltserstellung mit dem universellen Editor](authoring.md) - Erfahren Sie, wie einfach und intuitiv es für Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) - Erfahren Sie, wie der universelle Visual Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Architektur des universellen Editors](architecture.md) - Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](attributes-types.md) - Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Universelle Editor-Authentifizierung](authentication.md) - Erfahren Sie, wie der universelle Editor authentifiziert wird.
