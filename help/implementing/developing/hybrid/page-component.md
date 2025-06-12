---
title: SPA-Seitenkomponente
description: In einer SPA stellt die Seitenkomponente die HTML-Elemente ihrer untergeordneten Komponenten nicht bereit, sondern delegiert sie stattdessen an das SPA-Framework. In diesem Dokument wird erläutert, warum die Seitenkomponente einer SPA dadurch einzigartig wird.
exl-id: 41b56a60-ebb8-499d-a0ab-a2e920f26227
feature: Developing
role: Admin, Architect, Developer
index: false
source-git-commit: 7a9d947761b0473f5ddac3c4d19dfe5bed5b97fe
workflow-type: tm+mt
source-wordcount: '602'
ht-degree: 100%

---


# SPA-Seitenkomponente {#spa-page-component}

Die Seitenkomponente für eine SPA stellt die HTML-Elemente ihrer untergeordneten Komponenten nicht über die JSP- oder HTL-Datei und Ressourcenobjekte bereit. Dieser Vorgang wird an das SPA-Framework delegiert. Die Darstellung der untergeordneten Komponenten wird als JSON-Datenstruktur (d. h. das Modell) abgerufen. Die SPA-Komponenten werden dann gemäß dem angegebenen JSON-Modell zur Seite hinzugefügt. Somit unterscheidet sich die anfängliche Textzusammensetzung der Seitenkomponente von den im Vorab gerenderten HTML-Entsprechungen.

{{ue-over-spa}}

## Seitenmodellverwaltung {#page-model-management}

Die Auflösung und Verwaltung des Seitenmodells wird an ein bereitgestelltes [`PageModelManager`](blueprint.md#pagemodelmanager)-Modul delegiert. Die SPA muss mit dem `PageModelManager`-Modul interagieren, wenn es initialisiert wird, um das anfängliche Seitenmodell abzurufen und sich für Modellaktualisierungen zu registrieren – die meistens auftreten, wenn der Autor die Seite über den Seiteneditor bearbeitet. Der `PageModelManager` ist für das SPA-Projekt als NPM-Paket zugänglich. Als Dolmetscher zwischen AEM und der SPA soll der `PageModelManager` die SPA begleiten.

Damit die Seite erstellt werden kann, muss eine Client-Bibliothek mit dem Namen `cq.authoring.pagemodel.messaging` hinzugefügt werden, um einen Kommunikationskanal zwischen der SPA und dem Seiteneditor bereitzustellen. Wenn die SPA-Seitenkomponente von der page wcm/core-Komponente erbt, gibt es folgende Optionen, um die Kategorie der `cq.authoring.pagemodel.messaging`-Client-Bibliothek verfügbar zu machen:

* Wenn die Vorlage bearbeitbar ist, fügen Sie der Seitenrichtlinie die Kategorie der Client-Bibliothek hinzu.
* Fügen Sie die Client-Bibliothekskomponente mit der `customfooterlibs.html` der Seitenkomponente hinzu.

Vergessen Sie nicht, die Einbeziehung der `cq.authoring.pagemodel.messaging`-Kategorie auf den Kontext des Seiteneditors zu beschränken.

## Kommunikationsdatentyp {#communication-data-type}

Der Kommunikationsdatentyp ist ein mit dem `data-cq-datatype`-Attribut festgelegtes HTML-Element innerhalb der AEM-Seitenkomponente. Wenn der Kommunikationsdatentyp auf JSON festgelegt ist, rufen die GET-Anfragen die Endpunkte des Sling-Modells einer Komponente auf. Nach einer Aktualisierung im Seiteneditor wird die JSON-Repräsentation der aktualisierten Komponente an die PageModel-Bibliothek gesendet. Die PageModel-Bibliothek informiert dann die SPA über Aktualisierungen.

**SPA-Seitenkomponente –`body.html`**

```
<div id="page"></div>
```

Neben dem bewährten Verfahren, die DOM-Generierung nicht zu verzögern, setzt das SPA-Framework voraus, dass die Skripte am Ende des Hauptteils hinzugefügt werden.

**SPA-Seitenkomponente –`customfooterlibs.html`**

```
<sly data-sly-use.clientLib="${'/libs/granite/sightly/templates/clientlib.html'}"></sly>
<sly data-sly-test="${wcmmode.edit || wcmmode.preview}"
     data-sly-call="${clientLib.js @ categories='cq.authoring.pagemodel.messaging'}"></sly>
<sly data-sly-call="${clientLib.js @ categories='we-retail-journal-react'}"></sly>
```

Die Meta-Ressourceneigenschaften, die den SPA-Inhalt beschreiben:

**SPA-Seitenkomponente –`customheaderlibs.html`**

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
>Die Standardmodellauswahl wird bei Anforderung der Sling-Modelldarstellung einer Komponente statisch gesetzt.

## Meta-Eigenschaften {#meta-properties}

* `cq:wcmmode`: WCM-Modus der Editoren (z. B. Seite, Vorlage)
* `cq:pagemodel_root_url`: URL des Stammmodells der App. Entscheidend beim direkten Zugriff auf eine untergeordnete Seite, da das untergeordnete Seitenmodell ein Fragment des App-Stammmodells ist. Der `PageModelManager` setzt das anfängliche Anwendungsmodell dann systematisch als Eingabe für die Anwendung vom Stamm-Einstiegspunkt neu zusammen.
* `cq:pagemodel_router`: Aktivieren oder Deaktivieren des [`ModelRouter`](routing.md) der `PageModelManager`-Bibliothek
* `cq:pagemodel_route_filters`: Kommagetrennte Liste oder reguläre Ausdrücke, um Routen anzugeben, die [`ModelRouter`](routing.md) ignorieren muss.

## Synchronisation von Seiteneditor-Überlagerungen {#page-editor-overlay-synchronization}

Die Synchronisation der Überlagerungen wird durch denselben Änderungsbeobachter gewährleistet, der von der Kategorie `cq.authoring.page` bereitgestellt wird.

## Sling-Modell – JSON-exportierte Strukturkonfiguration {#sling-model-json-exported-structure-configuration}

Wenn Routing-Funktionen aktiviert sind, wird angenommen, dass der JSON-Export der SPA aufgrund des JSON-Exports der AEM-Navigationskomponente die verschiedenen Routen der Anwendung enthält. Die JSON-Ausgabe der AEM-Navigationskomponente kann in der SPA-Stammseiten-Inhaltsrichtlinie mit den folgenden beiden Eigenschaften konfiguriert werden:

* `structureDepth`: Zahl, die die Tiefe der exportierten Baumstruktur angibt
* `structurePatterns`: Regex oder Array aus Regexes, die der zu exportierenden Seite entsprechen
