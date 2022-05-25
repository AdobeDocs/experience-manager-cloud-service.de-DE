---
title: Caching in AEM as a Cloud Service
description: 'Zwischenspeicherung in AEM as a Cloud Service '
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
source-git-commit: 2df0c88d82554362879f6302e8f7c784cb96d2b8
workflow-type: tm+mt
source-wordcount: '2184'
ht-degree: 63%

---

# Einführung {#intro}

Traffic wird über das CDN an einen Apache-Webserver geleitet, der die Module einschließlich des Dispatchers unterstützt. Um die Leistung zu steigern, wird der Dispatcher hauptsächlich als Cache verwendet, um die Verarbeitung auf den Veröffentlichungsknoten zu begrenzen.
Auf die Dispatcher-Konfiguration können Regeln angewendet werden, um die Standardeinstellungen für den Cache-Ablauf zu ändern, was zum Caching im CDN führt. Beachten Sie, dass der Dispatcher auch die resultierenden Cache-Ablaufkopfzeilen berücksichtigt, wenn `enableTTL` in der Dispatcher-Konfiguration aktiviert ist. Dies bedeutet, dass bestimmte Inhalte auch außerhalb der erneut veröffentlichten Inhalte aktualisiert werden.

Auf dieser Seite wird auch beschrieben, wie der Dispatcher-Cache ungültig wird und wie das Caching auf Browser-Ebene in Bezug auf Client-seitige Bibliotheken funktioniert.

## Caching {#caching}

### HTML/Text {#html-text}

* Standardmäßig vom Browser fünf Minuten lang zwischengespeichert, basierend auf der `cache-control`-Kopfzeile, die von der Apache-Ebene ausgegeben wird. Das CDN berücksichtigt diesen Wert ebenfalls.
* Die Standardeinstellung für die HTML/Text-Zwischenspeicherung kann deaktiviert werden, indem die Variable `DISABLE_DEFAULT_CACHING` in `global.vars` definiert wird:

```
Define DISABLE_DEFAULT_CACHING
```

Dies kann beispielsweise nützlich sein, wenn die Geschäftslogik eine Feinabstimmung der Alter-Kopfzeile erfordert (mit einem Wert, der auf dem Kalendertag basiert), da die Alter-Kopfzeile standardmäßig auf 0 eingestellt ist. Allerdings sollten Sie **beim Deaktivieren der Standard-Zwischenspeicherung vorsichtig sein**.

* Kann für alle HTML-/Textinhalte überschrieben werden, indem die `EXPIRATION_TIME`-Variable in `global.vars` mithilfe der Dispatcher Tools des AEM as a Cloud Service-SDK definiert wird.
* kann auf einer feineren Ebene überschrieben werden, einschließlich der unabhängigen Kontrolle von CDN und Browser-Cache mit den folgenden Anweisungen von Apache mod_headers:

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header set Cache-Control "max-age=200"
        Header set Surrogate-Control "max-age=3600"
        Header set Age 0
   </LocationMatch>
   ```

   >[!NOTE]
   >Die Kopfzeile &quot;Surrogate-Control&quot;gilt für das von der Adobe verwaltete CDN. Wenn Sie eine [kundenverwaltetes CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html?lang=en#point-to-point-CDN)festgelegt ist, kann je nach CDN-Provider eine andere Kopfzeile erforderlich sein.

   Gehen Sie beim Festlegen von globalen Cache-Steuerungskopfzeilen oder solchen, die einem weit gefassten Regex entsprechen, umsichtig vor, damit sie nicht auf Inhalte angewendet werden, die andere nicht einsehen sollen. Erwägen Sie, mehrere Anweisungen zu verwenden, um sicherzustellen, dass die Regeln detailliert angewendet werden. AEM as a Cloud Service entfernt die Cache-Kopfzeile, wenn er feststellt, dass sie auf etwas angewendet wurde, von dem er erkennt, dass es vom Dispatcher nicht zwischengespeichert werden kann, wie in der Dispatcher-Dokumentation beschrieben. Um AEM zu zwingen, die Caching-Kopfzeilen immer anzuwenden, können Sie folgendermaßen die Option **Immer** hinzufügen:

   ```
   <LocationMatch "^/content/.*\.(html)$">
        Header unset Cache-Control
        Header unset Expires
        Header always set Cache-Control "max-age=200"
        Header set Age 0
   </LocationMatch>
   ```

   Sie müssen sicherstellen, dass eine Datei unter `src/conf.dispatcher.d/cache` die folgende Regel enthält (die sich in der Standardkonfiguration befindet):

   ```
   /0000
   { /glob "*" /type "allow" }
   ```

* Um zu verhindern, dass bestimmte Inhalte **im CDN** zwischengespeichert werden, setzen Sie die Cache-Control-Kopfzeile auf *Privat*. Das Folgende würde beispielsweise verhindern, dass HTML-Inhalte in einem Verzeichnis mit dem Namen **secure** im CDN zwischengespeichert werden:

   ```
      <LocationMatch "/content/secure/.*\.(html)$">.  // replace with the right regex
      Header unset Cache-Control
      Header unset Expires
      Header always set Cache-Control “private”
     </LocationMatch>
   ```

   >[!NOTE]
   >Andere Methoden, einschließlich des [AEM ACS Commons-Projekts dispatcher-ttl](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), überschreiben Werte nicht erfolgreich.

   >[!NOTE]
   >Bitte beachten Sie, dass der Dispatcher möglicherweise weiterhin Inhalte gemäß seinen eigenen [Zwischenspeicherungsregeln](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17497.html) zwischenspeichert. Damit der Inhalt wirklich privat ist, sollten Sie sicherstellen, dass er nicht vom Dispatcher zwischengespeichert wird.

### Client-seitige Bibliotheken (js, css) {#client-side-libraries}

* Durch Verwendung des Client-seitigen Bibliotheks-Frameworks von AEM wird JavaScript- und CSS-Code so generiert, dass Browser ihn unbegrenzt zwischenspeichern können, da Änderungen als neue Dateien mit einem eindeutigen Pfad angezeigt werden.  Mit anderen Worten: HTML-Code, der auf die Client-Bibliotheken verweist, wird nach Bedarf erstellt, damit Kunden neue Inhalte gleich nach der Veröffentlichung erleben können. Die Cache-Steuerung ist bei älteren Browsern, die den Wert „unveränderlich“ nicht einhalten, auf „unveränderlich“ oder auf 30 Tage eingestellt.
* Weitere Informationen finden Sie im Abschnitt [Client-seitige Bibliotheken und Versionskonsistenz](#content-consistency).

### Bilder und alle Inhalte, die groß genug sind, um in Blob-Speicher gespeichert zu werden {#images}

Das Standardverhalten von Programmen, die nach Mitte Mai 2022 erstellt wurden (insbesondere bei Programm-IDs über 65000), besteht darin, standardmäßig den Cache zu speichern, wobei auch der Authentifizierungskontext der Anfrage berücksichtigt wird. Ältere Programme (Programm-IDs kleiner/gleich 65000) speichern nicht standardmäßig Blob-Inhalte.

In beiden Fällen können die Zwischenspeicherkopfzeilen auf einer feineren Ebene auf der Apache-/Dispatcher-Ebene überschrieben werden, indem der Apache verwendet wird `mod_headers` Direktiven, z. B.:

```
   <LocationMatch "^/content/.*\.(jpeg|jpg)$">
     Header set Cache-Control "max-age=222"
     Header set Age 0
   </LocationMatch>
```

Wenn Sie die Zwischenspeicherkopfzeilen auf der Dispatcher-Ebene ändern, achten Sie darauf, den Cache nicht zu weit zu zwischenspeichern (siehe die Diskussion im Abschnitt HTML/Text ) [above](#html-text)). Stellen Sie außerdem sicher, dass Assets, die privat gehalten und nicht zwischengespeichert werden sollen, nicht zum `LocationMatch` Richtlinienfilter.

#### Neues standardmäßiges Caching-Verhalten {#new-caching-behavior}

Die AEM-Ebene legt die Cache-Kopfzeilen abhängig davon fest, ob der Cache-Header bereits festgelegt wurde, und den Wert des Anfragetyps. Beachten Sie, dass öffentliche Inhalte zwischengespeichert werden und authentifizierter Traffic auf &quot;Privat&quot;eingestellt ist, wenn kein Cache-Steuerelement-Header festgelegt wurde. Wenn ein Cache-Steuerelement-Header festgelegt wurde, bleiben die Cache-Header unberührt.

| Cache Control Header vorhanden? | Abfragetyp | AEM legt Cache-Header auf |
|------------------------------|---------------|------------------------------------------------|
| Nein | öffentlich | Cache-Control: public, max-age=600, unveränderlich |
| Nein | authentifiziert | Cache-Control: privat, max-age=600, unveränderlich |
| Ja | beliebig | unverändert |

Obwohl dies nicht empfohlen wird, ist es möglich, das neue Standardverhalten so zu ändern, dass es dem älteren Verhalten folgt (Programm-IDs kleiner/gleich 65000), indem die Umgebungsvariable Cloud Manager festgelegt wird. `AEM_BLOB_ENABLE_CACHING_HEADERS` auf &quot;false&quot;gesetzt.

#### Älteres standardmäßiges Caching-Verhalten {#old-caching-behavior}

Die AEM-Ebene speichert Blob-Inhalte nicht standardmäßig zwischen.

>[!NOTE]
>Es wird empfohlen, das ältere Standardverhalten so zu ändern, dass es mit dem neuen Verhalten übereinstimmt (für Programm-IDs, die höher als 65000 sind), indem die Cloud Manager-Umgebungsvariable AEM_BLOB_ENABLE_CACHING_HEADERS auf &quot;true&quot;gesetzt wird. Wenn das Programm bereits live ist, stellen Sie sicher, dass sich der Inhalt nach den Änderungen wie erwartet verhält.

>[!NOTE]
>Die anderen Methoden, einschließlich der [dispatcher-ttl AEM ACS Commons-Projekt](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), werden die Werte nicht erfolgreich überschrieben.

### Andere Inhaltsdateitypen im Knotenspeicher {#other-content}

* Kein standardmäßiges Caching
* Die Standardeinstellung kann nicht mit der für HTML-/Textdateitypen verwendeten `EXPIRATION_TIME`-Variablen gesetzt werden
* Der Cache-Ablauf kann mit derselben LocationMatch-Strategie festgelegt werden, die im Abschnitt „HTML/Text“ beschrieben wird, indem der entsprechende Regex angegeben wird

### Weitere Optimierungen {#further-optimizations}

* Vermeiden Sie die Verwendung von `User-Agent` als Teil der `Vary` -Kopfzeile. Ältere Versionen des standardmäßigen Dispatcher-Setups (vor Archetyp-Version 28) enthielten dies und empfehlen, dies mithilfe der folgenden Schritte zu entfernen.
   * Suchen Sie die vhost-Dateien in `<Project Root>/dispatcher/src/conf.d/available_vhosts/*.vhost`
   * Entfernen oder kommentieren Sie die Zeile aus: `Header append Vary User-Agent env=!dont-vary` aus allen Vhost-Dateien, mit Ausnahme von default.vhost, der schreibgeschützt ist
* Verwenden Sie die `Surrogate-Control` -Kopfzeile zur Steuerung der CDN-Zwischenspeicherung unabhängig von der Browser-Zwischenspeicherung
* Anwenden [`stale-while-revalidate`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-while-revalidate) und [`stale-if-error`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-if-error) Direktiven, um eine Hintergrundaktualisierung zu ermöglichen und Cache-Fehler zu vermeiden, sodass Ihr Inhalt für Benutzer schnell und frisch bleibt.
   * Es gibt viele Möglichkeiten, diese Richtlinien anzuwenden, es wird jedoch eine 30-minütige `stale-while-revalidate` für alle Cache-Steuerelement-Header ist ein guter Ausgangspunkt.
* Es folgen einige Beispiele für verschiedene Inhaltstypen, die beim Einrichten Ihrer eigenen Caching-Regeln als Anleitung verwendet werden können. Beachten und testen Sie sorgfältig Ihre spezifischen Einrichtungs- und Anforderungen:

   * Speichern Sie veränderliche Client-Bibliotheksressourcen für 12 Stunden im Cache und aktualisieren Sie den Hintergrund nach 12 Stunden.

      ```
      <LocationMatch "^/etc\.clientlibs/.*\.(?i:json|png|gif|webp|jpe?g|svg)$">
         Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200,public" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Speichern Sie unveränderliche Client-Bibliotheksressourcen langfristig (30 Tage) mit einer Hintergrundaktualisierung, um MISS zu vermeiden.

      ```
      <LocationMatch "^/etc\.clientlibs/.*\.(?i:js|css|ttf|woff2)$">
         Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Cache-HTML-Seiten für 5 Minuten mit einer Hintergrundaktualisierung von 1 Stunde im Browser und 12 Stunden im CDN. Cache-Control-Header werden immer hinzugefügt. Daher ist es wichtig sicherzustellen, dass übereinstimmende HTML-Seiten unter /content/* öffentlich sein sollen. Wenn nicht, sollten Sie einen spezifischeren Regex verwenden.

      ```
      <LocationMatch "^/content/.*\.html$">
         Header unset Cache-Control
         Header always set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
         Header always set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Cache Content Services/Sling Model Exporter JSON-Antworten für 5 Minuten mit Hintergrundaktualisierung 1 Stunde im Browser und 12 Stunden im CDN.

      ```
      <LocationMatch "^/content/.*\.model\.json$">
         Header set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
         Header set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Speichern Sie unveränderliche URLs aus der Kernbildkomponente langfristig (30 Tage) mit einer Hintergrundaktualisierung, um MISS zu vermeiden.

      ```
      <LocationMatch "^/content/.*\.coreimg.*\.(?i:jpe?g|png|gif|svg)$">
         Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

   * Speichern veränderlicher Ressourcen aus dem DAM wie Bilder und Videos für 24 Stunden und Hintergrundaktualisierungen nach 12 Stunden, um MISS zu vermeiden

      ```
      <LocationMatch "^/content/dam/.*\.(?i:jpe?g|gif|js|mov|mp4|png|svg|txt|zip|ico|webp|pdf)$">
         Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
         Header set Age 0
      </LocationMatch>
      ```

### HEAD-Anfrageverhalten {#request-behavior}

Wenn eine HEAD-Anfrage im Adobe-CDN für eine Ressource empfangen wird, die **not** zwischengespeichert wird, wird die Anforderung umgewandelt und vom Dispatcher und/oder AEM Instanz als GET-Anfrage empfangen. Wenn die Antwort zwischenspeicherbar ist, werden nachfolgende HEAD-Anfragen vom CDN bereitgestellt. Wenn die Antwort nicht zwischenspeicherbar ist, werden nachfolgende HEAD-Anfragen für einen Zeitraum, der von der `Cache-Control` TTL.

## Dispatcher-Cache-Invalidierung {#disp}

Im Allgemeinen ist es nicht erforderlich, den Dispatcher-Cache zu invalidieren. Stattdessen sollten Sie sich darauf verlassen, dass der Dispatcher seinen Cache aktualisiert, wenn Inhalte erneut veröffentlicht werden, und dass das CDN die Cache-Ablaufkopfzeilen berücksichtigt.

### Dispatcher-Cache-Invalidierung bei der Aktivierung/Deaktivierung {#cache-activation-deactivation}

Wie in früheren Versionen von AEM wird beim Veröffentlichen oder Aufheben der Veröffentlichung von Seiten der Inhalt aus dem Dispatcher-Cache gelöscht. Wenn ein Caching-Problem vermutet wird, sollten Kunden die betreffenden Seiten erneut veröffentlichen und sicherstellen, dass ein virtueller Host verfügbar ist, der mit dem ServerAlias-Localhost übereinstimmt, der für die Invalidierung des Dispatcher-Caches erforderlich ist.


Wenn die Veröffentlichungsinstanz vom Autor eine neue Version einer Seite oder eines Assets erhält, verwendet sie den Flush-Agenten, um die entsprechenden Pfade auf ihrem Dispatcher zu invalidieren. Der aktualisierte Pfad wird zusammen mit den übergeordneten Elementen bis zu einer Ebene, die Sie mit [statfileslevel](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#invalidating-files-by-folder-level) konfigurieren können, aus dem Dispatcher-Cache entfernt.

### Explizite Dispatcher-Cache-Invalidierung {#explicit-invalidation}

Im Allgemeinen ist es nicht erforderlich, Inhalte im Dispatcher manuell zu invalidieren, aber es ist bei Bedarf möglich.

>[!NOTE]
>Vor AEM as a Cloud Service gab es zwei Möglichkeiten, den Dispatcher-Cache zu invalidieren.
>
>1. Aufrufen des Replikations-Agenten und Angeben des Publish-Dispatcher-Flush-Agenten
>2. Direkter Aufruf der `invalidate.cache`-API (z. B. `POST /dispatcher/invalidate.cache`)

>
>Der `invalidate.cache`-API-Ansatz des Dispatchers wird nicht mehr unterstützt, da er sich nur an einen bestimmten Dispatcher-Knoten richtet. AEM as a Cloud Service wird auf Service-Ebene und nicht auf der Ebene einzelner Knoten ausgeführt. Daher sind die Anweisungen zur Invalidierung auf der Seite [Invalidierung zwischengespeicherter Seiten aus AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=de) für AEM as a Cloud Service nicht mehr gültig.

Stattdessen sollte der Replikations-Flush-Agent verwendet werden. Dies kann über die [Replikations-API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html) durchgeführt werden. Der Endpunkt des Flush-Agenten ist nicht konfigurierbar. Er ist aber so vorkonfiguriert, dass er auf den Dispatcher verweist, der mit dem Veröffentlichungs-Service, der den Flush-Agent ausführt, abgestimmt ist. Der Flush-Agent kann normalerweise durch OSGi-Ereignisse oder Workflows ausgelöst werden.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 
-->

Das folgende Diagramm veranschaulicht dies.

![CDN](assets/cdnd.png "CDN")

Wenn Bedenken bestehen, dass der Dispatcher-Cache nicht geleert wird, wenden Sie sich an den [Support](https://helpx.adobe.com/de/support.ec.html), der den Dispatcher-Cache ggf. leeren kann.

Das von Adobe verwaltete CDN berücksichtigt TTLs und muss daher nicht geleert werden. Bei Verdacht auf ein Problem [wenden Sie sich an den Support](https://helpx.adobe.com/support.ec.html), der bei Bedarf einen von Adobe verwalteten CDN-Cache leeren kann.

## Client-seitige Bibliotheken und Versionskonsistenz {#content-consistency}

Seiten bestehen aus HTML, JavaScript, CSS und Bildern. Wir empfehlen Kunden, das [Client-seitige Bibliotheken-Framework (clientlibs)](/help/implementing/developing/introduction/clientlibs.md) zu nutzen, um JavaScript- und CSS-Ressourcen in HTML-Seiten zu importieren und dabei Abhängigkeiten zwischen JS-Bibliotheken zu berücksichtigen.

Das clientlibs-Framework bietet eine automatische Versionsverwaltung, d. h. Entwickler können Änderungen an JS-Bibliotheken in der Quell-Code-Verwaltung einchecken und die neueste Version wird zur Verfügung gestellt, wenn ein Kunde seine Version veröffentlicht. Andernfalls müssten Entwickler HTML mit Verweisen auf die neue Version der Bibliothek manuell ändern. Dies ist sehr aufwendig, wenn viele HTML-Vorlagen dieselbe Bibliothek nutzen.

Wenn die neuen Bibliotheksversionen für die Produktion freigegeben werden, werden die verweisenden HTML-Seiten mit neuen Links zu diesen aktualisierten Bibliotheksversionen aktualisiert. Sobald der Browsercache für eine bestimmte HTML-Seite abgelaufen ist, besteht keine Gefahr, dass die alten Bibliotheken aus dem Browsercache geladen werden, da die aktualisierte Seite (aus AEM) nun garantiert auf die neuen Versionen der Bibliotheken verweist. Anders ausgedrückt: Eine aktualisierte HTML-Seite enthält alle aktuellen Bibliotheksversionen.

Der Mechanismus hierfür ist ein serialisierter Hash, der an den Link der Client-Bibliothek angehängt wird und eine eindeutige, versionierte URL für den Browser zum Zwischenspeichern von CSS/JS gewährleistet. Der serialisierte Hash wird nur aktualisiert, wenn sich der Inhalt der Client-Bibliothek ändert. Das bedeutet, dass bei nicht zusammenhängenden Aktualisierungen (d. h. bei keiner Änderung der zugrunde liegenden CSS/js der Client-Bibliothek) auch bei einer neuen Implementierung der Verweis derselbe bleibt, wodurch weniger Störungen im Browser-Cache auftreten.

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
