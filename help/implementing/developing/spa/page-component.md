---
title: SPA-Seitenkomponente
description: In einer SPA stellt die Seitenkomponente die HTML-Elemente ihrer untergeordneten Komponenten nicht bereit, sondern delegiert sie stattdessen an das SPA-Framework. In diesem Dokument wird erläutert, wie die Seitenkomponente einer SPA dadurch eindeutig wird.
translation-type: tm+mt
source-git-commit: c075bcc415b68ba0deaeca61d6d179bd7263ca5f
workflow-type: tm+mt
source-wordcount: '598'
ht-degree: 11%

---


# SPA-Seitenkomponente {#spa-page-component}

Die Seitenkomponente für eine SPA stellt die HTML-Elemente ihrer untergeordneten Komponenten nicht über eine JSP- oder HTL-Datei und Ressourcenobjekte bereit. Dieser Vorgang wird an das SPA-Framework delegiert. Die Darstellung untergeordneter Komponenten wird als JSON-Datenstruktur (d. h. als Modell) abgerufen. Die SPA-Komponenten werden dann gemäß dem bereitgestellten JSON-Modell zur Seite hinzugefügt. Somit unterscheidet sich die anfängliche Textzusammensetzung der Seitenkomponente von den vorgerenderten HTML-Entsprechungen.

## Seitenmodellverwaltung {#page-model-management}

The resolution and the management of the page model is delegated to a provided [`PageModelManager`](blueprint.md#pagemodelmanager) module. Die SPA muss mit dem `PageModelManager` Modul interagieren, wenn sie initialisiert wird, um das anfängliche Seitenmodell abzurufen und sich für Modellaktualisierungen zu registrieren - meistens, wenn der Autor die Seite über den Seiten-Editor bearbeitet. Das `PageModelManager` ist mit dem SPA-Projekt als npm-Paket verfügbar. Als Dolmetscher zwischen AEM und der SPA `PageModelManager` soll die SPA begleitet werden.

Damit die Seite erstellt werden kann, `cq.authoring.pagemodel.messaging` muss eine Client-Bibliothek mit dem Namen hinzugefügt werden, um einen Kanal für die Kommunikation zwischen der SPA und dem Seiteneditor bereitzustellen. Wenn die SPA-Seitenkomponente von der page wcm/core-Komponente erbt wird, gibt es die folgenden Optionen, um die `cq.authoring.pagemodel.messaging` Client-Bibliothekskomponente verfügbar zu machen:

* Wenn die Vorlage bearbeitbar ist, fügen Sie der Seitenrichtlinie die Kategorie der Client-Bibliothek hinzu.
* hinzufügen die Client-Bibliothekskomponente mit der Kategorie `customfooterlibs.html` der Seitenkomponente.

Vergessen Sie nicht, die Einbeziehung der `cq.authoring.pagemodel.messaging` Kategorie auf den Kontext des Seiteneditors zu beschränken.

## Kommunikationsdatentyp {#communication-data-type}

Der Kommunikationsdatentyp wird mithilfe des `data-cq-datatype` Attributs ein HTML-Element innerhalb der Komponente &quot;AEM Seite&quot;festgelegt. Wenn der Kommunikationsdatentyp auf JSON eingestellt ist, treffen die GET-Anforderungen auf die Sling Model-Endpunkte einer Komponente. Nach einer Aktualisierung im Seiten-Editor wird die JSON-Repräsentation der aktualisierten Komponente an die PageModel-Bibliothek gesendet. Die Seitenmodellbibliothek warnt dann die SPA vor Aktualisierungen.

**SPA-Seitenkomponente:`body.html`**

```
<div id="page"></div>
```

Das SPA-Framework ist nicht nur eine gute Vorgehensweise, die DOM-Generierung nicht zu verzögern, sondern erfordert auch, dass die Skripte am Ende des Körpers hinzugefügt werden.

**SPA-Seitenkomponente:`customfooterlibs.html`**

```
<sly data-sly-use.clientLib="${'/libs/granite/sightly/templates/clientlib.html'}"></sly>
<sly data-sly-test="${wcmmode.edit || wcmmode.preview}"
     data-sly-call="${clientLib.js @ categories='cq.authoring.pagemodel.messaging'}"></sly>
<sly data-sly-call="${clientLib.js @ categories='we-retail-journal-react'}"></sly>
```

Die Metadatenressourceneigenschaften, die den SPA-Inhalt beschreiben:

**SPA-Seitenkomponente:`customheaderlibs.html`**

```
<meta property="cq:datatype" data-sly-test="${wcmmode.edit || wcmmode.preview}" content="JSON"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.edit}" content="edit"/>
<meta property="cq:wcmmode" data-sly-test="${wcmmode.preview}" content="preview"/>
<meta property="cq:pagemodel_root_url" data-sly-use.page="com.adobe.cq.sample.spa.journal.models.AppPage" content="${page.rootUrl}"/>
<sly data-sly-use.clientlib="/libs/granite/sightly/templates/clientlib.html">
    <sly data-sly-call="${clientlib.css @ categories='we-retail-journal-react'}"/>
</sly>
```

>[!NOTE]
>
>Die Standardmodellauswahl wird bei Anforderung der Sling-Modelldarstellung einer Komponente statisch eingestellt.

## Meta-Eigenschaften {#meta-properties}

* `cq:wcmmode`: WCM-Modus der Editoren (z. B. Seite, Vorlage)
* `cq:pagemodel_root_url`: URL des Stammmodells der App. Entscheidend beim direkten Zugriff auf eine untergeordnete Seite, da das untergeordnete Seitenmodell ein Fragment des App-Stammmodells ist. Das `PageModelManager` anfängliche Anwendungsmodell wird dann systematisch als Eingabe für die Anwendung vom Stamm-Einstiegspunkt empfohlen.
* `cq:pagemodel_router`: Aktivieren oder Deaktivieren [`ModelRouter`](routing.md) der `PageModelManager` Bibliothek
* `cq:pagemodel_route_filters`: Kommagetrennte Liste oder reguläre Ausdruck, um Routen bereitzustellen, die ignoriert werden [`ModelRouter`](routing.md) müssen.

## Synchronisierung von Seiteneditor-Überlagerungen {#page-editor-overlay-synchronization}

Die Synchronisierung der Überlagerungen wird durch denselben Mutation-Beobachter gewährleistet, der von der `cq.authoring.page` Kategorie bereitgestellt wird.

## Sling Model JSON Export Structure Configuration {#sling-model-json-exported-structure-configuration}

Wenn die Routing-Funktionen aktiviert sind, wird davon ausgegangen, dass der JSON-Export der SPA die verschiedenen Anwendungsrouten enthält, dank des JSON-Exports der AEM Navigationskomponente. Die JSON-Ausgabe der AEM-Navigationskomponente kann in der SPA-Stammseiten-Inhaltsrichtlinie mit den folgenden beiden Eigenschaften konfiguriert werden:

* `structureDepth`: Zahl, die die Tiefe der exportierten Baumstruktur angibt
* `structurePatterns`: Regex des Arrays von Regexen, die der zu exportierenden Seite entsprechen
