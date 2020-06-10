---
title: Zwischenspeicherung in AEM als Cloud-Dienst
description: 'Zwischenspeicherung in AEM als Cloud-Dienst '
translation-type: tm+mt
source-git-commit: 9d99a7513a3a912b37ceff327e58a962cc17c627
workflow-type: tm+mt
source-wordcount: '1358'
ht-degree: 85%

---


# Einführung {#intro}

Traffic wird durch das CDN auf eine Apache-Webserverebene übertragen, die Module einschließlich des Dispatchers unterstützt. Um die Leistung zu erhöhen, wird der Dispatcher hauptsächlich als Cache verwendet, um die Verarbeitung auf den Veröffentlichungsknoten zu beschränken.
Regeln können auf die Dispatcher-Konfiguration angewendet werden, um alle standardmäßigen Cache-Ablaufeinstellungen zu ändern, was zu einer Zwischenspeicherung am CDN führt. Note that dispatcher also respects the resulting cache expiration headers if `enableTTL` is enabled in the dispatcher configuration, implying that it will refresh specific content even outside of content being republished.

Diese Seite beschreibt auch, wie Dispatcher-Cache ungültig ist und wie die Zwischenspeicherung auf Browserebene im Hinblick auf clientseitige Bibliotheken funktioniert.

## Caching {#caching}

### HTML/Text {#html-text}

* Standardmäßig vom Browser fünf Minuten lang zwischengespeichert, basierend auf der Cache-Steuerungskopfzeile, die von der Apache-Ebene ausgegeben wird. Das CDN berücksichtigt diesen Wert ebenfalls.
* Kann für alle HTML-/Textinhalte überschrieben werden, indem die `EXPIRATION_TIME`-Variable in `global.vars` mithilfe der Dispatcher Tools des AEM as a Cloud Service-SDK definiert wird.
* Kann auf einer feineren Ebene durch die folgenden Anweisungen von apache mod_headers überschrieben werden:

```
<LocationMatch "\.(html)$">
        Header set Cache-Control "max-age=200"
</LocationMatch>
```

Sie müssen sicherstellen, dass eine Datei unter `src/conf.dispatcher.d/cache` die folgende Regel enthält (die sich in der Standardkonfiguration befindet):

```
/0000
{ /glob "*" /type "allow" }
```

* Um zu verhindern, dass bestimmte Inhalte zwischengespeichert werden, setzen Sie den Cache-Control-Header auf &quot;privat&quot;. Beispielsweise würde Folgendes verhindern, dass HTML-Inhalte in einem Ordner mit dem Namen &quot;myfolder&quot;zwischengespeichert werden:

```
<LocationMatch "\/myfolder\/.*\.(html)$">.  // replace with the right regex
    Header set Cache-Control “private”
</LocationMatch>
```

* Beachten Sie, dass andere Methoden, einschließlich des [AEM ACS Commons-Projekts dispatcher-ttl](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), Werte nicht erfolgreich überschreiben.

### Client-seitige Bibliotheken (js, css) {#client-side-libraries}

* Durch Verwendung des Client-seitigen Bibliotheks-Frameworks von AEM wird JavaScript- und CSS-Code so generiert, dass Browser ihn unbegrenzt zwischenspeichern können, da Änderungen als neue Dateien mit einem eindeutigen Pfad angezeigt werden. Mit anderen Worten: HTML-Code, der auf die Client-Bibliotheken verweist, wird nach Bedarf erstellt, damit Kunden neue Inhalte gleich nach der Veröffentlichung erleben können. Die Cache-Steuerung ist bei älteren Browsern, die den Wert „unveränderlich“ nicht einhalten, auf „unveränderlich“ oder auf 30 Tage eingestellt.
* Weitere Informationen finden Sie im Abschnitt [Client-seitige Bibliotheken und Versionskonsistenz](#content-consistency).

### Bilder und alle Inhalte, die groß genug sind, um im Blob-Speicher gespeichert zu werden {#images}

* Standardmäßig nicht zwischengespeichert
* Können durch die folgenden Apache-Anweisungen `mod_headers` auf eine feinere Ebene gesetzt werden:

```
<LocationMatch "^.*.jpeg$">
    Header set Cache-Control "max-age=222"
</LocationMatch>
```

Es muss sichergestellt werden, dass eine Datei unter src/conf.dispatcher.d/cache die folgende Regel enthält (die sich in der Standardkonfiguration befindet):

```
/0000
{ /glob "*" /type "allow" }
```

Stellen Sie sicher, dass Assets, die privat gehalten und nicht zwischengespeichert werden sollen, nicht Teil der Filter der LocationMatch-Anweisung sind.

* Beachten Sie, dass andere Methoden, einschließlich des [AEM ACS Commons-Projekts dispatcher-ttl](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), Werte nicht erfolgreich überschreiben.

### Andere Inhaltsdateitypen im Knotenspeicher {#other-content}

* Kein standardmäßiges Caching
* Die Standardeinstellung kann nicht mit der für HTML-/Textdateitypen verwendeten `EXPIRATION_TIME`-Variablen gesetzt werden
* Der Cache-Ablauf kann mit derselben LocationMatch-Strategie festgelegt werden, die im Abschnitt „HTML/Text“ beschrieben wird, indem der entsprechende Regex angegeben wird

## Dispatcher-Cache-Ungültigkeit {#disp}

Im Allgemeinen sollte es nicht notwendig sein, den Dispatcher-Cache ungültig zu machen. Stattdessen sollten Sie sich darauf verlassen, dass der Dispatcher seinen Cache aktualisiert, wenn Inhalte erneut veröffentlicht werden, und dass das CDN Cache-Ablaufkopfzeilen berücksichtigt.

### Dispatcher-Cache-Invalidierung bei der Aktivierung/Deaktivierung {#cache-activation-deactivation}

Wie in früheren Versionen von AEM wird beim Veröffentlichen oder Aufheben der Veröffentlichung von Seiten der Inhalt aus dem Dispatcher-Cache gelöscht. Wenn ein Caching-Problem vermutet wird, sollten Kunden die betreffenden Seiten erneut veröffentlichen.

Wenn die Veröffentlichungsinstanz vom Autor eine neue Version einer Seite oder eines Assets erhält, verwendet sie den Flush-Agenten, um die entsprechenden Pfade auf ihrem Dispatcher zu invalidieren. Der aktualisierte Pfad wird zusammen mit den übergeordneten Elementen bis zu einer Ebene, die Sie mit [statfileslevel](https://docs.adobe.com/content/help/de-DE/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level) konfigurieren können, aus dem Dispatcher-Cache entfernt.

### Explizite Dispatcher-Cache-Invalidierung {#explicit-invalidation}

Im Allgemeinen ist es nicht erforderlich, Inhalte im Dispatcher manuell zu invalidieren, aber es ist bei Bedarf möglich, wie unten beschrieben.

Vor AEM as a Cloud Service gab es zwei Möglichkeiten, den Dispatcher-Cache zu invalidieren.

1. Aufrufen des Replikations-Agenten und Angeben des Publish-Dispatcher-Flush-Agenten
2. Direkter Aufruf der `invalidate.cache`-API (z. B. `POST /dispatcher/invalidate.cache`)

Der `invalidate.cache`-Ansatz des Dispatchers wird nicht mehr unterstützt, da er sich nur an einen bestimmten Dispatcher-Knoten richtet. AEM as a Cloud Service wird auf Dienstebene und nicht auf der Ebene einzelner Knoten ausgeführt. Daher sind die Anweisungen zur Invalidierung auf der Seite [Invalidierung zwischengespeicherter Seiten aus AEM](https://docs.adobe.com/content/help/de-DE/experience-manager-dispatcher/using/configuring/page-invalidate.html) für AEM as a Cloud Service nicht mehr gültig.
Stattdessen sollte der Replikations-Flush-Agent verwendet werden. Dies kann über die Replikations-API durchgeführt werden. Die Replikations-API-Dokumentation ist [hier](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/Replicator.html) verfügbar. Ein Beispiel für das Bereinigen des Cache finden Sie auf der [API-Beispielseite](https://helpx.adobe.com/de/experience-manager/using/aem64_replication_api.html) und insbesondere im `CustomStep`-Beispiel, bei dem eine Replikationsaktion des Typs ACTIVATE an alle verfügbaren Agenten ausgegeben wird. Der Endpunkt des Flush-Agenten ist nicht konfigurierbar. Er ist aber so vorkonfiguriert, dass er auf den Dispatcher verweist, der mit dem Publish-Dienst, der den Flush-Agent ausführt, abgestimmt ist. Der Flush-Agent kann normalerweise durch OSGi-Ereignisse oder Workflows ausgelöst werden.

Das folgende Diagramm veranschaulicht dies.

![CDN](assets/cdnd.png "CDN")

Wenn Bedenken bestehen, dass der Dispatcher-Cache nicht geleert wird, wenden Sie sich an den [Support](https://helpx.adobe.com/de/support.ec.html), der den Dispatcher-Cache ggf. leeren kann.

Das von Adobe verwaltete CDN berücksichtigt TTLs und muss daher nicht geleert werden. Bei Verdacht auf ein Problem [wenden Sie sich an den Support](https://helpx.adobe.com/de/support.ec.html), der bei Bedarf einen von Adobe verwalteten CDN-Cache leeren kann.

## Client-seitige Bibliotheken und Versionskonsistenz {#content-consistency}

Seiten bestehen aus HTML, JavaScript, CSS und Bildern. Wir empfehlen Kunden, das Client-seitige Bibliotheken-Framework zu nutzen, um JavaScript- und CSS-Ressourcen in HTML-Seiten zu importieren und dabei Abhängigkeiten zwischen JS-Bibliotheken zu berücksichtigen.

Das clientlibs-Framework bietet eine automatische Versionsverwaltung, d. h. Entwickler können Änderungen an JS-Bibliotheken in der Quell-Code-Verwaltung einchecken und die neueste Version wird zur Verfügung gestellt, wenn ein Kunde seine Version veröffentlicht. Andernfalls müssten Entwickler HTML mit Verweisen auf die neue Version der Bibliothek manuell ändern. Dies ist sehr aufwendig, wenn viele HTML-Vorlagen dieselbe Bibliothek nutzen.

Wenn die neuen Bibliotheksversionen für die Produktion freigegeben werden, werden die verweisenden HTML-Seiten mit neuen Links zu diesen aktualisierten Bibliotheksversionen aktualisiert. Sobald der Browsercache für eine bestimmte HTML-Seite abgelaufen ist, besteht keine Gefahr, dass die alten Bibliotheken aus dem Browsercache geladen werden, da die aktualisierte Seite (aus AEM) nun garantiert auf die neuen Versionen der Bibliotheken verweist. Anders ausgedrückt: Eine aktualisierte HTML-Seite enthält alle aktuellen Bibliotheksversionen.

Der Mechanismus hierfür ist ein serialisierter Hash, der an den Link der Client-Bibliothek angehängt wird und eine eindeutige, versionierte URL für den Browser zum Zwischenspeichern von CSS/JS gewährleistet. Der serialisierte Hash wird nur aktualisiert, wenn sich der Inhalt der Client-Bibliothek ändert. Das bedeutet, dass bei nicht zusammenhängenden Aktualisierungen (d. h. bei keiner Änderung der zugrunde liegenden CSS/js der Client-Bibliothek) auch bei einer neuen Bereitstellung der Verweis derselbe bleibt, wodurch weniger Störungen im Browser-Cache auftreten.

### Aktivieren von Longcache-Versionen Client-seitiger Bibliotheken – AEM as a Cloud Service-SDK-Schnellstart {#enabling-longcache}

Die standardmäßigen clientlib-Includes auf einer HTML-Seite sehen wie im folgenden Beispiel aus:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

Wenn die strikte clientlib-Versionierung aktiviert ist, wird der Client-Bibliothek ein langfristiger Hash-Schlüssel als Selektor hinzugefügt. Daher sieht der clientlib-Verweis wie folgt aus:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Die strikte Clientlib-Versionierung ist standardmäßig in allen AEM as a Cloud Service-Umgebungen aktiviert.

Führen Sie die folgenden Aktionen aus, um die strikte Clientlib-Versionierung im lokalen SDK-Schnellstart zu aktivieren:

1. Navigieren Sie zum OSGi Configuration Manager `<host>/system/console/configMgr`
1. Suchen Sie die OSGi-Konfiguration für Adobe Granite HTML Library Manager:
   * Aktivieren Sie das Kontrollkästchen, um die strikte Versionierung zu aktivieren.
   * Geben Sie in das Feld für den langfristigen Client-seitigen Cache-Schlüssel den Wert /.*;hash ein.
1. Speichern Sie die Änderungen. Beachten Sie, dass es nicht notwendig ist, diese Konfiguration in der Quell-Code-Verwaltung zu speichern, da AEM as a Cloud Service diese Konfiguration in Entwicklungs-, Staging- und Produktionsumgebungen automatisch aktiviert.
1. Bei jeder Änderung des Inhalts der Client-Bibliothek wird ein neuer Hash-Schlüssel generiert und der HTML-Verweis wird aktualisiert.
