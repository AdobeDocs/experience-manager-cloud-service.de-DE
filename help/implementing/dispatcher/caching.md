---
title: Caching in AEM as a Cloud Service
description: Erfahren Sie mehr über die Grundlagen der Zwischenspeicherung in AEM as a Cloud Service
feature: Dispatcher
exl-id: 4206abd1-d669-4f7d-8ff4-8980d12be9d6
source-git-commit: a6714e79396f006f2948c34514e5454fef84b5d8
workflow-type: tm+mt
source-wordcount: '2803'
ht-degree: 49%

---

# Einführung {#intro}

Traffic wird über das CDN an eine Apache-Webserver-Ebene geleitet, welche die Module einschließlich des Dispatchers unterstützt. Zur Leistungssteigerung wird der Dispatcher hauptsächlich als Cache verwendet, um die Verarbeitung auf den Veröffentlichungsknoten zu begrenzen.
Auf die Dispatcher-Konfiguration können Regeln angewendet werden, um die Standardeinstellungen für den Cache-Ablauf zu ändern, was zum Caching im CDN führt. Der Dispatcher berücksichtigt auch die resultierenden Cache-Ablaufkopfzeilen, wenn `enableTTL` in der Dispatcher-Konfiguration aktiviert ist, was bedeutet, dass bestimmte Inhalte auch außerhalb der erneut veröffentlichten Inhalte aktualisiert werden.

Auf dieser Seite wird auch beschrieben, wie der Dispatcher-Cache invalidiert wird und wie die Zwischenspeicherung auf Browserebene in Bezug auf Client-seitige Bibliotheken funktioniert.

## Caching {#caching}

### HTML/Text {#html-text}

* standardmäßig wird vom Browser fünf Minuten lang zwischengespeichert, basierend auf der `cache-control`-Kopfzeile, die von der Apache-Ebene ausgegeben wird. Das CDN berücksichtigt diesen Wert ebenfalls.
* Die Standardeinstellung für die HTML/Text-Zwischenspeicherung kann deaktiviert werden, indem die Variable `DISABLE_DEFAULT_CACHING` in `global.vars` definiert wird:

```
Define DISABLE_DEFAULT_CACHING
```

Diese Methode ist beispielsweise nützlich, wenn Ihre Geschäftslogik eine Feinabstimmung der Kopfzeile der Seite erfordert (mit einem Wert, der auf dem Kalendertag basiert), da die Kopfzeile der Seite standardmäßig auf 0 gesetzt ist. Dies bedeutet: **Gehen Sie beim Deaktivieren der standardmäßigen Zwischenspeicherung vorsichtig vor.**

* Kann für alle HTML-/Textinhalte überschrieben werden, indem die Variable `EXPIRATION_TIME` in `global.vars` mithilfe der Dispatcher-Tools des AEM as a Cloud Service-SDK definiert wird.
* kann mit den folgenden `mod_headers`-Anweisungen von Apache auf einer detaillierteren Ebene überschrieben werden, einschließlich der unabhängigen Steuerung von CDN- und Browser-Cache:

  ```
  <LocationMatch "^/content/.*\.(html)$">
       Header set Cache-Control "max-age=200"
       Header set Surrogate-Control "max-age=3600"
       Header set Age 0
  </LocationMatch>
  ```

  >[!NOTE]
  >Die Surrogate-Control-Kopfzeile gilt für das von Adobe verwaltete CDN. Wenn Sie eine [kundenverwaltetes CDN](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn.html?lang=de#point-to-point-CDN)festgelegt ist, kann je nach CDN-Provider eine andere Kopfzeile erforderlich sein.

  Gehen Sie beim Festlegen von globalen Cache-Steuerelement-Headern oder ähnlichen Cache-Headern, die mit einem breiten Regex übereinstimmen, vorsichtig vor, damit sie nicht auf Inhalte angewendet werden, die privat bleiben müssen. Erwägen Sie, mehrere Anweisungen zu verwenden, um sicherzustellen, dass die Regeln detailliert angewendet werden. Daher entfernt AEM as a Cloud Service den Cache-Header, wenn festgestellt wird, dass er auf das angewendet wurde, was vom Dispatcher als nicht erreichbar erkannt wird, wie in der Dispatcher-Dokumentation beschrieben. Um AEM zu erzwingen, die Zwischenspeicherkopfzeilen immer anzuwenden, können Sie die **`always`** -Option wie folgt:

  ```
  <LocationMatch "^/content/.*\.(html)$">
       Header unset Cache-Control
       Header unset Expires
       Header always set Cache-Control "max-age=200"
       Header set Age 0
  </LocationMatch>
  ```

  Stellen Sie sicher, dass eine Datei unter `src/conf.dispatcher.d/cache` verfügt über die folgende Regel (die sich in der Standardkonfiguration befindet):

  ```
  /0000
  { /glob "*" /type "allow" }
  ```

* Um zu verhindern, dass bestimmte Inhalte **im CDN** zwischengespeichert werden, setzen Sie die Cache-Control-Kopfzeile auf *Privat*. Das Folgende würde beispielsweise verhindern, dass HTML-Inhalte in einem Verzeichnis mit dem Namen **secure** im CDN zwischengespeichert werden:

  ```
     <LocationMatch "/content/secure/.*\.(html)$">.  // replace with the right regex
     Header unset Cache-Control
     Header unset Expires
     Header always set Cache-Control "private"
    </LocationMatch>
  ```

* Während HTML-Inhalte, die auf &quot;privat&quot;festgelegt sind, nicht im CDN zwischengespeichert werden, können sie beim Dispatcher zwischengespeichert werden, wenn [Zwischenspeicherung unter Berücksichtigung von Berechtigungen](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=de) konfiguriert ist, sodass nur autorisierte Benutzer den Inhalt erhalten können.

  >[!NOTE]
  >Die anderen Methoden, einschließlich der [Dispatcher-ttl AEM ACS Commons-Projekt](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), überschreibt Werte nicht erfolgreich.

  >[!NOTE]
  >Der Dispatcher speichert möglicherweise Inhalte weiterhin nach eigenem [Zwischenspeicherungsregeln](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17497.html?lang=de). Um den Inhalt wirklich privat zu gestalten, stellen Sie sicher, dass er nicht vom Dispatcher zwischengespeichert wird.

### Client-seitige Bibliotheken (js, css) {#client-side-libraries}

* Bei Verwendung des client-seitigen Bibliotheks-Frameworks von AEM wird JavaScript- und CSS-Code so generiert, dass Browser ihn unbegrenzt zwischenspeichern können, da alle Änderungen als neue Dateien mit einem eindeutigen Pfad manifestiert werden. Mit anderen Worten: HTML, die auf die Client-Bibliotheken verweist, wird nach Bedarf erstellt, damit Kunden neue Inhalte bei der Veröffentlichung erleben können. Die Cache-Steuerung ist bei älteren Browsern, die den Wert &quot;unveränderlich&quot;nicht berücksichtigen, auf &quot;unveränderlich&quot;oder auf 30 Tage eingestellt.
* Weitere Informationen finden Sie im Abschnitt [Client-seitige Bibliotheken und Versionskonsistenz](#content-consistency).

### Bilder und alle Inhalte, die groß genug sind, um im Blob-Speicher gespeichert zu werden {#images}

Das Standardverhalten von Programmen, die nach Mitte Mai 2022 erstellt wurden (insbesondere bei Programm-IDs über 65000), besteht darin, standardmäßig zwischenzuspeichern. Dabei wird auch der Authentifizierungskontext der Anfrage berücksichtigt. Ältere Programme (Programm-IDs kleiner/gleich 65000) speichern Blob-Inhalte nicht standardmäßig.

In beiden Fällen können die Caching-Kopfzeilen auf einer detaillierteren Ebene auf Apache-/Dispatcher-Ebene überschrieben werden, indem die `mod_headers`-Anweisungen von Apache verwendet werden, Beispiel: 

```
   <LocationMatch "^/content/.*\.(jpeg|jpg)$">
     Header set Cache-Control "max-age=222"
     Header set Age 0
   </LocationMatch>
```

Achten Sie beim Ändern der Zwischenspeicherkopfzeilen auf der Dispatcher-Ebene darauf, nicht zu weit zwischengespeichert zu werden. Siehe die Diskussion im Abschnitt HTML/Text . [above](#html-text). Stellen Sie außerdem sicher, dass Assets, die privat bleiben sollen (und nicht zwischengespeichert werden sollen), nicht Teil der Filter der `LocationMatch`-Anweisung sind.

#### Neues Caching-Standardverhalten {#new-caching-behavior}

Die AEM-Ebene legt die Cache-Header abhängig davon fest, ob der Cache-Header bereits festgelegt wurde, und den Wert des Anfragetyps. Wenn kein Cache-Steuerelement-Header festgelegt ist, wird der öffentliche Inhalt zwischengespeichert und der authentifizierte Traffic wird auf &quot;Privat&quot;eingestellt. Wenn ein Cache-Steuerelement-Header festgelegt ist, bleiben die Cache-Header unberührt.

| Cache-Control-Kopfzeile vorhanden? | Abfragetyp | AEM legt Cache-Kopfzeile wie folgt fest |
|------------------------------|---------------|------------------------------------------------|
| Nein | Öffentlich | Cache-Control: public, max-age=600, immutable |
| Nein | Authentifiziert | Cache-Control: private, max-age=600, immutable |
| Ja | Beliebig | Unverändert |

Obwohl es nicht empfohlen wird, ist es möglich, das neue Standardverhalten so zu ändern, dass es dem älteren Verhalten folgt (Programm-IDs kleiner/gleich 65000), indem die Cloud Manager-Umgebungsvariable `AEM_BLOB_ENABLE_CACHING_HEADERS` auf „false“ festgelegt wird.

#### Älteres Caching-Standardverhalten {#old-caching-behavior}

Die AEM-Ebene speichert Blob-Inhalte nicht standardmäßig zwischen.

>[!NOTE]
>Ändern Sie das ältere Standardverhalten so, dass es dem neuen Verhalten entspricht (Programm-IDs, die höher als 65000 sind), indem Sie die Cloud Manager-Umgebungsvariable AEM_BLOB_ENABLE_CACHING_HEADERS auf &quot;true&quot;setzen. Wenn das Programm bereits live ist, stellen Sie sicher, dass sich der Inhalt nach den Änderungen wie erwartet verhält.

Bilder im Blob-Speicher, die als privat gekennzeichnet sind, können jetzt im Dispatcher mit [Zwischenspeicherung unter Berücksichtigung von Berechtigungen](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=de). Das Bild wird immer von der AEM-Quelle angefordert und bereitgestellt, sofern der Benutzer/die Benutzerin über die entsprechenden Berechtigungen verfügt.

>[!NOTE]
>Die anderen Methoden, einschließlich der [dispatcher-ttl AEM ACS Commons-Projekt](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/), überschreiben Sie die Werte nicht erfolgreich.

### Andere Inhaltsdateitypen im Knotenspeicher {#other-content}

* Kein standardmäßiges Caching
* Die Standardeinstellung kann nicht mit der für HTML-/Textdateitypen verwendeten `EXPIRATION_TIME`-Variablen gesetzt werden
* Der Cache-Ablauf kann mit derselben LocationMatch-Strategie festgelegt werden, die im Abschnitt „HTML/Text“ beschrieben wird, indem der entsprechende Regex angegeben wird

### Weitere Optimierungen {#further-optimizations}

* Vermeiden Sie die Verwendung von `User-Agent` als Teil der `Vary`-Kopfzeile. Ältere Versionen der standardmäßigen Dispatcher-Einrichtung (vor Archetyp-Version 28) enthielten sie und Adobe empfiehlt, sie mithilfe der folgenden Schritte zu entfernen.
   * Suchen Sie die vhost-Dateien in `<Project Root>/dispatcher/src/conf.d/available_vhosts/*.vhost`.
   * Entfernen oder kommentieren Sie die Zeile aus: `Header append Vary User-Agent env=!dont-vary` aus allen Vhost-Dateien, mit Ausnahme von default.vhost, der schreibgeschützt ist
* Verwenden Sie die `Surrogate-Control`-Kopfzeile, um das CDN-Caching unabhängig vom Browser-Caching zu steuern.
* Sie könnten die Anweisungen [`stale-while-revalidate`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-while-revalidate) und [`stale-if-error`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#stale-if-error) anwenden, um eine Hintergrundaktualisierung zu ermöglichen und Cache-Fehler zu vermeiden, sodass Ihr Inhalt für Benutzerinnen und Benutzer schnell und aktuell verfügbar bleibt.
   * Es gibt viele Möglichkeiten, diese Richtlinien anzuwenden, es wird jedoch eine 30-minütige `stale-while-revalidate` für alle Cache-Steuerelement-Header ist ein guter Ausgangspunkt.
* Im Folgenden finden Sie einige Beispiele für verschiedene Inhaltstypen, die Sie beim Einrichten Ihrer eigenen Caching-Regeln als Anleitung verwenden können. Prüfen und testen Sie sorgfältig Ihre spezifischen Einstellungen und Anforderungen:

   * Reduzierbare Client-Bibliotheksressourcen werden 12 Stunden lang zwischengespeichert und der Hintergrund nach 12 Stunden aktualisiert.

     ```
     <LocationMatch "^/etc\.clientlibs/.*\.(?i:json|png|gif|webp|jpe?g|svg)$">
        Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200,public" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * Speichern Sie unveränderliche Client-Bibliotheksressourcen langfristig (30 Tage) mit einer Hintergrundaktualisierung, um Fehler zu vermeiden.

     ```
     <LocationMatch "^/etc\.clientlibs/.*\.(?i:js|css|ttf|woff2)$">
        Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * HTML-Seiten für fünf Minuten zwischenspeichern, wobei der Hintergrund eine Stunde im Browser und 12 Stunden im CDN aktualisiert wird. Cache-Control-Header werden immer hinzugefügt. Daher ist es wichtig sicherzustellen, dass übereinstimmende HTML-Seiten unter /content/* öffentlich sein sollen. Wenn nicht, sollten Sie einen spezifischeren regulären Ausdruck verwenden.

     ```
     <LocationMatch "^/content/.*\.html$">
        Header unset Cache-Control
        Header always set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
        Header always set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * Cache-Content-Services/Sling Model Exporter JSON-Antworten für fünf Minuten mit einer Hintergrundaktualisierung eine Stunde im Browser und 12 Stunden im CDN.

     ```
     <LocationMatch "^/content/.*\.model\.json$">
        Header set Cache-Control "max-age=300,stale-while-revalidate=3600" "expr=%{REQUEST_STATUS} < 400"
        Header set Surrogate-Control "stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * Speichern Sie unveränderliche URLs aus der Kernbildkomponente langfristig (30 Tage) mit einer Hintergrundaktualisierung, um Fehler zu vermeiden.

     ```
     <LocationMatch "^/content/.*\.coreimg.*\.(?i:jpe?g|png|gif|svg)$">
        Header set Cache-Control "max-age=2592000,stale-while-revalidate=43200,stale-if-error=43200,public,immutable" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

   * Speichern Sie veränderliche Ressourcen aus dem DAM wie Bilder und Videos 24 Stunden lang im Cache und aktualisieren Sie den Hintergrund nach 12 Stunden, um MISS zu vermeiden.

     ```
     <LocationMatch "^/content/dam/.*\.(?i:jpe?g|gif|js|mov|mp4|png|svg|txt|zip|ico|webp|pdf)$">
        Header set Cache-Control "max-age=43200,stale-while-revalidate=43200,stale-if-error=43200" "expr=%{REQUEST_STATUS} < 400"
        Header set Age 0
     </LocationMatch>
     ```

### HEAD-Anfrageverhalten {#request-behavior}

Wenn eine HEAD-Anfrage im Adobe-CDN für eine Ressource empfangen wird, die **nicht** zwischengespeichert wird, wird die Anfrage umgewandelt und vom Dispatcher und/oder der AEM-Instanz als GET-Anfrage empfangen. Wenn die Antwort zwischenspeicherbar ist, werden nachfolgende HEAD-Anfragen vom CDN bereitgestellt. Wenn die Antwort nicht zwischenspeicherbar ist, werden nachfolgende HEAD-Anfragen für einen von der `Cache-Control` TTL.

### Parameter von Marketing-Kampagnen {#marketing-parameters}

Website-URLs enthalten häufig Marketing-Kampagnenparameter, mit denen der Erfolg einer Kampagne verfolgt werden kann.

In Umgebungen, die im Oktober 2023 oder höher erstellt wurden, entfernt das CDN gängige Marketing-bezogene Abfrageparameter, insbesondere diejenigen, die dem folgenden Regex-Muster entsprechen, um Cache-Anforderungen zu verbessern:

```
^(utm_.*|gclid|gdftrk|_ga|mc_.*|trk_.*|dm_i|_ke|sc_.*|fbclid)$
```

Bitte senden Sie ein Support-Ticket, wenn Sie möchten, dass dieses Verhalten deaktiviert wird.

Für Umgebungen, die vor Oktober 2023 erstellt wurden, wird empfohlen, die `ignoreUrlParams` Eigenschaft als [hier dokumentiert](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#ignoring-url-parameters).


## Dispatcher-Cache-Invalidierung {#disp}

Im Allgemeinen ist es nicht erforderlich, den Dispatcher-Cache ungültig zu machen. Stattdessen sollten Sie sich darauf verlassen, dass der Dispatcher seinen Cache aktualisiert, wenn Inhalte erneut veröffentlicht werden, und dass das CDN die Cache-Ablaufkopfzeilen berücksichtigt.

### Dispatcher-Cache-Invalidierung bei der Aktivierung/Deaktivierung {#cache-activation-deactivation}

Wie bei früheren Versionen von AEM wird beim Veröffentlichen oder Aufheben der Veröffentlichung von Seiten der Inhalt aus dem Dispatcher-Cache gelöscht. Wenn ein Caching-Problem vermutet wird, sollten Sie die betreffenden Seiten erneut veröffentlichen und sicherstellen, dass ein virtueller Host verfügbar ist, der dem `ServerAlias`-Localhost entspricht, der für die Dispatcher-Cache-Invalidierung erforderlich ist.

>[!NOTE]
>Stellen Sie für eine ordnungsgemäße Dispatcher-Invalidierung sicher, dass Anforderungen von &quot;127.0.0.1&quot;, &quot;localhost&quot;, &quot;.local&quot;, &quot;.adobeaemcloud.com&quot;und &quot;.adobeaemcloud.net&quot;von einer vhost-Konfiguration abgeglichen und verarbeitet werden, damit die Anfrage bereitgestellt werden kann. Sie können diese Aufgabe ausführen, indem Sie in einer Catch-All-Vhost-Konfiguration global mit &quot;*&quot;übereinstimmen, entsprechend dem Muster in der Referenz [AEM Archetyp](https://github.com/adobe/aem-project-archetype/blob/develop/src/main/archetype/dispatcher.cloud/src/conf.d/available_vhosts/default.vhost). Sie können auch sicherstellen, dass die zuvor erwähnte Liste von einem der Hosts erfasst wird.

Wenn die Veröffentlichungsinstanz eine neue Version einer Seite oder eines Assets vom Autor erhält, verwendet sie den Flush-Agenten, um die entsprechenden Pfade auf ihrem Dispatcher zu invalidieren. Der aktualisierte Pfad wird zusammen mit den übergeordneten Elementen bis zu einer Ebene aus dem Dispatcher-Cache entfernt (Sie können diese Ebene mit der [statfileslevel](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#invalidating-files-by-folder-level)).

## Explizite Invalidierung des Dispatcher-Caches {#explicit-invalidation}

Adobe empfiehlt, zur Steuerung des Lebenszyklus der Inhaltsbereitstellung auf Standard-Cache-Header zurückzugreifen. Bei Bedarf können Inhalte jedoch direkt im Dispatcher invalidiert werden.

Die folgende Liste enthält Szenarien, in denen es sinnvoll sein kann, den Cache explizit zu invalidieren (während Sie optional auf den Abschluss der Invalidierung warten):

* Nach der Veröffentlichung von Inhalten wie Experience Fragments oder Inhaltsfragmenten wird der veröffentlichte und zwischengespeicherte Inhalt, der auf diese Elemente verweist, invalidiert.
* Benachrichtigung eines externen Systems, wenn referenzierte Seiten erfolgreich invalidiert wurden.

Es gibt zwei Möglichkeiten, den Cache explizit zu invalidieren:

* Der bevorzugte Ansatz ist die Verwendung von Sling Content Distribution (SCD) aus der Autoreninstanz.
* Der andere Ansatz besteht darin, die Replikations-API zu verwenden, um den Replikationsagenten für das Leeren des Dispatchers im Veröffentlichungsmodus aufzurufen.

Die Ansätze unterscheiden sich hinsichtlich der Verfügbarkeit der Stufe, der Möglichkeit, Ereignisse zu deduplizieren, und der Garantie für die Ereignisverarbeitung. In der folgenden Tabelle sind diese Optionen zusammengefasst:

<table style="table-layout:auto">
 <tbody>
  <tr>
    <th>Nicht zutreffend</th>
    <th>Verfügbarkeit der Stufe</th>
    <th>Deduplizierung </th>
    <th>Garantie </th>
    <th>Aktion </th>
    <th>Auswirkungen </th>
    <th>Beschreibung </th>
  </tr>  
  <tr>
    <td>Sling Content Distribution (SCD)-API</td>
    <td>Autor</td>
    <td>Möglich durch Verwendung der Discovery-API oder Aktivierung des <a href="https://github.com/apache/sling-org-apache-sling-distribution-journal/blob/e18f2bd36e8b43814520e87bd4999d3ca77ce8ca/src/main/java/org/apache/sling/distribution/journal/impl/publisher/DistributedEventNotifierManager.java#L146-L149">Deduplizierungsmodus</a>.</td>
    <td>Mindestens einmal.</td>
    <td>
     <ol>
       <li>HINZUFÜGEN</li>
       <li>LÖSCHEN</li>
       <li>INVALIDIEREN</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hierarchische/statische Ebene</li>
       <li>Hierarchische/statische Ebene</li>
       <li>Ebene nur für Ressourcen</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Veröffentlicht Inhalte und macht den Cache ungültig.</li>
       <li>Entfernt Inhalte und macht den Cache ungültig.</li>
       <li>Invalidiert den Inhalt, ohne ihn zu veröffentlichen.</li>
     </ol>
     </td>
  </tr>
  <tr>
    <td>Replikations-API</td>
    <td>Veröffentlichen </td>
    <td>Nicht möglich, Ereignis wird bei jeder Veröffentlichungsinstanz ausgelöst.</td>
    <td>Beste Möglichkeit.</td>
    <td>
     <ol>
       <li>AKTIVIEREN</li>
       <li>DEAKTIVIEREN</li>
       <li>LÖSCHEN</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Hierarchische/statische Ebene</li>
       <li>Hierarchische/statische Ebene</li>
       <li>Hierarchische/statische Ebene</li>
     </ol>
     </td>
    <td>
     <ol>
       <li>Veröffentlicht Inhalte und macht den Cache ungültig.</li>
       <li>Aus der Autoren-/Veröffentlichungsebene – Entfernt Inhalte und macht den Cache ungültig.</li>
       <li><p><strong>Aus der Autorenebene</strong> – Entfernt Inhalte und macht den Cache ungültig (wenn er von der AEM-Autorenebene im Veröffentlichungsagenten ausgelöst wird).</p>
           <p><strong>Auf der Veröffentlichungsebene</strong> – Invalidiert nur den Cache (wenn er von der AEM-Veröffentlichungsebene im Flush- oder Resource-only-Flush-Agenten ausgelöst wird).</p>
       </li>
     </ol>
     </td>
  </tr>
  </tbody>
</table>

Die beiden Aktionen, die sich direkt auf die Cache-Invalidierung beziehen, sind die Invalidierung der Sling Content Distribution (SCD)-API und die Deaktivierung der Replikations-API.

Aus der Tabelle können Sie außerdem Folgendes feststellen:

* Die SCD-API ist erforderlich, wenn jedes Ereignis garantiert werden muss, z. B. die Synchronisierung mit einem externen System, das genaue Kenntnisse erfordert. Wenn zum Zeitpunkt des Invalidierungs-Aufrufs ein Upskalierungs-Ereignis auf der Veröffentlichungsstufe vorhanden ist, wird ein zusätzliches Ereignis ausgelöst, wenn jede neue Veröffentlichung die Invalidierung verarbeitet.

* Die Verwendung der Replikations-API ist kein gängiges Anwendungsbeispiel, kann jedoch verwendet werden, wenn der Trigger zur Invalidierung des Caches von der Veröffentlichungsstufe und nicht von der Autorenstufe stammt. Diese Methode kann nützlich sein, wenn die Dispatcher-TTL konfiguriert ist.

Wenn Sie abschließend den Dispatcher-Cache invalidieren möchten, wird empfohlen, die SCD-API-Invalidierungsaktion aus der Autoreninstanz zu verwenden. Sie können auch auf das Ereignis überwachen, damit Sie dann weitere nachgelagerte Aktionen Trigger haben.

### Sling Content Distribution (SCD) {#sling-distribution}

>[!NOTE]
>Wenn Sie die unten beschriebenen Anweisungen verwenden, testen Sie den benutzerdefinierten Code in einer AEM Cloud Service-Entwicklungsumgebung und nicht lokal.

Bei Verwendung der SCD-Aktion aus der Autoreninstanz sieht die Implementierung wie folgt aus:

1. Schreiben Sie in der Autoreninstanz benutzerdefinierten Code, um die Sling-Inhaltsverteilungs-[API](https://sling.apache.org/documentation/bundles/content-distribution.html) aufzurufen, wodurch die Invalidierungs-Aktion mit einer Liste von Pfaden übergeben wird:

```
@Reference
private Distributor distributor;

ResourceResolver resolver = ...; // the resource resolver used for authorizing the request
String agentName = "publish";    // the name of the agent used to distribute the request

String pathToInvalidate = "/content/to/invalidate";
DistributionRequest distributionRequest = new SimpleDistributionRequest(DistributionRequestType.INVALIDATE, false, pathToInvalidate);
distributor.distribute(agentName, resolver, distributionRequest);
```

* (Optional) Suchen Sie nach einem Ereignis, das die Ressource widerspiegelt, die für alle Dispatcher-Instanzen invalidiert wird:


```
package org.apache.sling.distribution.journal.shared;

import org.apache.sling.discovery.DiscoveryService;
import org.apache.sling.distribution.journal.impl.event.DistributionEvent;
import org.osgi.service.component.annotations.Component;
import org.osgi.service.component.annotations.Reference;
import org.osgi.service.event.Event;
import org.osgi.service.event.EventHandler;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import static org.apache.sling.distribution.DistributionRequestType.INVALIDATE;
import static org.apache.sling.distribution.event.DistributionEventProperties.DISTRIBUTION_PATHS;
import static org.apache.sling.distribution.event.DistributionEventProperties.DISTRIBUTION_TYPE;
import static org.apache.sling.distribution.event.DistributionEventTopics.AGENT_PACKAGE_DISTRIBUTED;
import static org.osgi.service.event.EventConstants.EVENT_TOPIC;

@Component(immediate = true, service = EventHandler.class, property = {
        EVENT_TOPIC + "=" + AGENT_PACKAGE_DISTRIBUTED
})
public class InvalidatedHandler implements EventHandler {
    private static final Logger LOG = LoggerFactory.getLogger(InvalidatedHandler.class);

    @Reference
    private DiscoveryService discoveryService;

    @Override
    public void handleEvent(Event event) {

        String distributionType = (String) event.getProperty(DISTRIBUTION_TYPE);

        if (INVALIDATE.name().equals(distributionType)) {
            boolean isLeader = discoveryService.getTopology().getLocalInstance().isLeader();
            // process the OSGi event on the leader author instance
            if (isLeader) {
                String[] paths = (String[]) event.getProperty(DISTRIBUTION_PATHS);
                String packageId = (String) event.getProperty(DistributionEvent.PACKAGE_ID);
                invalidated(paths, packageId);
            }
        }
    }

    private void invalidated(String[] paths, String packageId) {
        // custom logic
        LOG.info("Successfully applied package with id {}, paths {}", packageId, paths);
    }
}
```

<!-- Optionally, instead of using the isLeader approach, one could add an OSGi configuration for the PID org.apache.sling.distribution.journal.impl.publisher.DistributedEventNotifierManager and property deduplicateEvent=true. But we'll stick with just one strategy and not mention it (double-check this).**review this**-->

* (Optional) Führen Sie die Geschäftslogik in der genannten `invalidated(String[] paths, String packageId)`-Methode aus.

>[!NOTE]
>
>Das Adobe-CDN wird nicht geleert, wenn der Dispatcher invalidiert wird. Das von Adobe verwaltete CDN berücksichtigt TTLs und muss daher nicht geleert werden.

### Replikations-API {#replication-api}

Im Folgenden finden Sie das Implementierungsmuster bei Verwendung der Replikations-API-Deaktivierungsaktion:

1. Rufen Sie auf der Veröffentlichungsebene die Replikations-API auf, um den Replikationsagenten für das Leeren des Publish-Dispatchers zu triggern.

Der Endpunkt des Flush-Agenten ist nicht konfigurierbar. Er ist aber so vorkonfiguriert, dass er auf den Dispatcher verweist, der mit dem Veröffentlichungs-Service, der den Flush-Agenten ausführt, abgestimmt ist.

Der Flush-Agent kann normalerweise durch OSGi-Ereignisse oder Workflows ausgelöst werden.

```
String[] paths = …
ReplicationOptions options = new ReplicationOptions();
options.setSynchronous(true);
options.setFilter( new AgentFilter {
  public boolean isIncluded (Agent agent) {
   return agent.getId().equals("flush");
  }
});

Replicator.replicate (session,ReplicationActionType.DELETE,paths, options);
```

<!-- In general, it will not be necessary to manually invalidate content in the dispatcher, but it is possible if needed.

>[!NOTE]
>Prior to AEM as a Cloud Service, there were two ways of invalidating the dispatcher cache.
>
>1. Invoke the replication agent, specifying the publish dispatcher flush agent
>2. Directly calling the `invalidate.cache` API (for example, `POST /dispatcher/invalidate.cache`)
>
>The dispatcher's `invalidate.cache` API approach will no longer be supported since it addresses only a specific dispatcher node. AEM as a Cloud Service operates at the service level, not the individual node level and so the invalidation instructions in the [Invalidating Cached Pages From AEM](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html) page are not longer valid for AEM as a Cloud Service.

The replication flush agent should be used. This can be done using the [Replication API](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/replication/Replicator.html). The flush agent endpoint is not configurable but pre-configured to point to the dispatcher, matched with the publish service running the flush agent. The flush agent can typically be triggered by OSGi events or workflows.

<!-- Need to find a new link and/or example -->
<!-- 
and for an example of flushing the cache, see the [API example page](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) (specifically the `CustomStep` example issuing a replication action of type ACTIVATE to all available agents). 

The diagram presented below illustrates this.

![CDN](assets/cdnd.png "CDN")

If there is a concern that the dispatcher cache is not clearing, contact [customer support](https://helpx.adobe.com/support.ec.html) who can flush the dispatcher cache if necessary.

The Adobe-managed CDN respects TTLs and thus there is no need fo it to be flushed. If an issue is suspected, [contact customer support](https://helpx.adobe.com/support.ec.html) support who can flush an Adobe-managed CDN cache as necessary. -->

## Client-seitige Bibliotheken und Versionskonsistenz {#content-consistency}

Seiten bestehen aus HTML, JavaScript, CSS und Bildern. Kunden wird empfohlen, die [Client-seitiges Bibliotheks-Framework (clientlibs)](/help/implementing/developing/introduction/clientlibs.md) um JavaScript- und CSS-Ressourcen in HTML-Seiten zu importieren und dabei Abhängigkeiten zwischen JS-Bibliotheken zu berücksichtigen.

Das clientlibs-Framework bietet eine automatische Versionsverwaltung. Das bedeutet, dass Entwickler Änderungen an JS-Bibliotheken in der Quell-Code-Verwaltung einchecken können und die neueste Version verfügbar gemacht wird, wenn ein Kunde seine Version veröffentlicht. Ohne diesen Workflow müssen Entwickler das HTML mit Verweisen auf die neue Bibliotheksversion manuell ändern. Dies ist besonders aufwändig, wenn dieselbe Bibliothek viele HTML-Vorlagen nutzt.

Wenn die neuen Bibliotheksversionen für die Produktion freigegeben werden, werden die verweisenden HTML-Seiten mit neuen Links zu diesen aktualisierten Bibliotheksversionen aktualisiert. Nachdem der Browsercache für eine bestimmte HTML-Seite abläuft, besteht kein Problem, dass die alten Bibliotheken aus dem Browsercache geladen werden. Der Grund dafür ist, dass die aktualisierte Seite (von AEM) jetzt garantiert auf die neuen Versionen der Bibliotheken verweist. Das heißt, eine aktualisierte HTML-Seite enthält alle aktuellen Bibliotheksversionen.

Der Mechanismus hinter dieser Fähigkeit ist ein serialisierter Hash, der an den Client-Bibliotheks-Link angehängt wird. Dadurch wird eine eindeutige, versionierte URL sichergestellt, damit der Browser die CSS/JS zwischenspeichert. Der serialisierte Hash wird nur aktualisiert, wenn sich der Inhalt der Client-Bibliothek ändert. Das bedeutet, dass bei nicht zusammenhängenden Aktualisierungen (d. h. bei keiner Änderung der zugrunde liegenden CSS/js der Client-Bibliothek) auch bei einer neuen Bereitstellung der Verweis derselbe bleibt. Dadurch wird wiederum eine geringere Unterbrechung des Browser-Cache sichergestellt.

### Aktivieren von Longcache-Versionen Client-seitiger Bibliotheken - AEM as a Cloud Service SDK-Schnellstart {#enabling-longcache}

Die standardmäßigen clientlib-Includes auf einer HTML-Seite sehen wie im folgenden Beispiel aus:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

Wenn die strikte clientlib-Versionierung aktiviert ist, wird der Client-Bibliothek ein langfristiger Hash-Schlüssel als Selektor hinzugefügt. Daher sieht der clientlib-Verweis wie folgt aus:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Die strikte Clientlib-Versionierung ist in AEM as a Cloud Service Umgebung standardmäßig aktiviert.

Gehen Sie wie folgt vor, um die strikte clientlib-Versionierung im lokalen SDK-Schnellstart zu aktivieren:

1. Navigieren Sie zum OSGi Configuration Manager `<host>/system/console/configMgr`
1. Suchen Sie die OSGi-Konfiguration für Adobe Granite HTML Library Manager:
   * Aktivieren Sie das Kontrollkästchen, damit &quot;Strenge Versionierung&quot;aktiviert wird.
   * Im Feld mit der Bezeichnung **Langfristiger clientseitiger Cache-Schlüssel**, geben Sie den Wert von / ein.*;hash ein.
1. Speichern Sie die Änderungen. Diese Konfiguration muss nicht in der Quell-Code-Verwaltung gespeichert werden, da AEM as a Cloud Service diese Konfiguration automatisch in Entwicklungs-, Staging- und Produktionsumgebungen aktiviert.
1. Jedes Mal, wenn der Inhalt der Client-Bibliothek geändert wird, wird ein neuer Hash-Schlüssel generiert und die HTML-Referenz aktualisiert.
