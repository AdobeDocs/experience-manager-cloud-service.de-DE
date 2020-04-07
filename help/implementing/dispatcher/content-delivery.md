---
title: Content Versand
description: 'Content Versand '
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Content Versand in AEM als Cloud-Dienst {#content-delivery}

Die aktuellen Seitendetails veröffentlichen den Content Versand des Dienstes in AEM als Cloud-Dienst. Der Content Versand des Veröffentlichungsdienstes umfasst:

* CDN (normalerweise von Adobe verwaltet)
* AEM-Dispatcher
* AEM-Veröffentlichung

Der Datenfluss sieht folgendermaßen aus:

1. Die URL wird im Browser hinzugefügt
1. Anforderung an CDN, die dieser Domäne im DNS zugeordnet ist
1. Wenn Inhalte auf dem CDN vollständig zwischengespeichert sind, stellt CDN sie für den Browser bereit
1. Wenn der Inhalt nicht vollständig zwischengespeichert ist, ruft das CDN den Dispatcher ab (Reverse-Proxy)
1. Wenn Inhalte auf dem Dispatcher vollständig zwischengespeichert sind, stellt der Dispatcher sie dem CDN zur Verfügung
1. Wenn Inhalte nicht vollständig zwischengespeichert sind, ruft der Dispatcher (Reverse-Proxy) zur AEM-Veröffentlichung auf
1. Der Inhalt wird vom Browser gerendert, der ihn ggf. auch zwischenspeichert, je nach Header

Der Content-Typ HTML/Text läuft nach 300 s (5 Minuten) auf der Dispatcher-Ebene ab. Dies ist ein Schwellenwert, den sowohl der Dispatcher-Cache als auch CDN beachten. Bei der Bereitstellung des Veröffentlichungsdiensts wird der Dispatcher-Cache geleert und anschließend erwärmt, bevor die neuen Veröffentlichungsknoten Traffic akzeptieren.

Die folgenden Abschnitte enthalten genauere Informationen zum Content Versand, einschließlich CDN-Konfiguration und -Zwischenspeicherung.

Informationen zur Replizierung vom Autorendienst zum Veröffentlichungsdienst finden Sie [hier](/help/operations/replication.md).

## CDN {#cdn}

AEM als Cloud-Dienst wird mit einem integrierten CDN ausgeliefert. Hauptzweck ist es, die Latenz zu reduzieren, indem zwischengespeicherte Inhalte von den CDN-Knoten an der Kante in der Nähe des Browsers bereitgestellt werden. Es wird vollständig verwaltet und für eine optimale Leistung von AEM-Anwendungen konfiguriert.

Insgesamt stehen AEM Angebots zwei Optionen zur Verfügung:

1. AEM Managed CDN - AEM&#39;s vordefiniertes CDN. Es handelt sich um eine eng integrierte Option, die keine umfangreichen Kundeninvestitionen zur Unterstützung der CDN-Integration mit AEM erfordert.
1. Kundenverwaltetes CDN verweist auf AEM Managed CDN - der Kunde verweist sein eigenes CDN auf das vordefinierte CDN von AEM. Der Kunde muss weiterhin sein eigenes CDN verwalten, aber die Investitionen in die Integration mit AEM sind gering.

Die erste Option sollte die meisten Leistungs- und Sicherheitsanforderungen des Kunden erfüllen. Darüber hinaus erfordert es minimalen Kundenaufwand.

Die zweite Option ist von Fall zu Fall zulässig. Die Entscheidung beruht auf der Erfüllung bestimmter Voraussetzungen, darunter auch dem Kunden, der über eine veraltete Integration mit seinem CDN-Anbieter verfügt, die schwer aufzugeben ist.

Nachfolgend finden Sie eine Entscheidungsmatrix zum Vergleich der beiden Optionen. Detailliertere Informationen finden Sie in den folgenden Abschnitten.

| Details | AEM Managed CDN | Vom Kunden verwaltetes CDN verweist auf AEM CDN |
|---|---|---|
| **Kundenaufwand** | Keine, sie ist vollständig integriert. Nur CNAME muss auf AEM Managed CDN verweisen. | Mäßige Kundeninvestitionen. Der Kunde muss sein eigenes CDN verwalten. |
| **Voraussetzungen** | Keine | Vorhandenes CDN, das nur schwer zu ersetzen ist. Vor dem Start muss ein erfolgreicher Belastungstest durchgeführt werden. |
| **CDN-Expertise** | Keine | Benötigt mindestens eine Teilzeit-Engineering-Ressource mit detailliertem CDN-Wissen, die das CDN des Kunden konfigurieren kann. |
| **Sicherheit** | Verwaltet von Adobe. | Verwaltet von Adobe (und optional vom Kunden bei seinem eigenen CDN). |
| **Leistung** | Optimiert von Adobe. | Einige AEM-CDN-Funktionen sind nützlich, aber möglicherweise ein kleiner Leistungseinbruch aufgrund des zusätzlichen Hosts. **Hinweis**: Hopfen vom Kunden CDN bis Fastly CDN wahrscheinlich effizient sein). |
| **Caching** | Unterstützt Cache-Kopfzeilen, die auf den Dispatcher angewendet werden. | Unterstützt Cache-Kopfzeilen, die auf den Dispatcher angewendet werden. |
| **Funktionen zur Bild- und Videokomprimierung** | Kann mit Adobe Dynamic Media verwendet werden. | Kann mit Adobe Dynamic Media oder einer kundenverwalteten CDN-Bild-/Videolösung verwendet werden. |

### AEM Managed CDN {#aem-managed-cdn}

Die Vorbereitung auf Content Versand mithilfe des standardmäßigen CDN von Adobe ist ganz einfach, wie nachfolgend beschrieben:

1. Sie stellen Adobe das signierte SSL-Zertifikat und den geheimen Schlüssel zur Verfügung, indem Sie einen Link zu einem sicheren Formular mit diesen Informationen freigeben. Bitte stimmen Sie sich mit dem Kundensupport auf dieser Aufgabe ab.
   **Hinweis:** AEM als Cloud-Dienst unterstützt keine DV-Zertifikate (Domain Validated).
1. Sie sollten den Kundensupport informieren:
   * welche benutzerdefinierte Domäne einer bestimmten Umgebung zugeordnet werden soll, wie durch die Programm-ID und die Umgebung-ID definiert.
   * wenn eine IP-Whitelist erforderlich ist, um den Traffic auf eine bestimmte Umgebung zu beschränken.
1. Der Kundensupport koordiniert dann mit Ihnen die zeitliche Abfolge für einen CNAME-DNS-Datensatz und weist deren FQDN auf `adobe-aem.map.fastly.net`.
1. Sie werden benachrichtigt, wenn die SSL-Zertifikate ablaufen, damit Sie die neuen SSL-Zertifikate erneut senden können.

**Einschränkung des Traffics**

Standardmäßig kann bei einem Adobe Managed CDN-Setup der gesamte öffentliche Traffic zum Veröffentlichungsdienst wechseln, sowohl für Produktions- als auch für Nicht-Produktions- (Entwicklungs- und Bereitstellungsdienste) Umgebung. Wenn Sie den Traffic für eine bestimmte Umgebung auf den Veröffentlichungsdienst beschränken möchten (z. B. die Beschränkung der Staging-Aktivität auf eine Reihe von IP-Adressen), sollten Sie sich an den Kundendienst wenden, um diese Einschränkungen zu konfigurieren.

### Customer CDN verweist auf AEM Managed CDN {#point-to-point-CDN}

Wird unterstützt, wenn Sie Ihr vorhandenes CDN verwenden möchten, die Anforderungen eines vom Kunden verwalteten CDN jedoch nicht erfüllen können. In diesem Fall verwalten Sie Ihr eigenes CDN, verweisen aber auf das von Adobe verwaltete CDN.

Bitte beachten Sie, dass:

1. Sie benötigen ein vorhandenes CDN.
1. Du musst es verwalten.
1. Sie müssen in der Lage sein, das CDN für die Verwendung mit AEM als Cloud-Dienst zu konfigurieren - siehe die Konfigurationsanweisungen unten.
1. Sie benötigen technische CDN-Experten, die im Falle von Problemen im Zusammenhang mit dem Projekt auf Anfrage zur Verfügung stehen.
1. Sie müssen vor dem Produktivbetrieb einen Lasttest durchführen und erfolgreich bestehen.

Konfigurationsanweisungen:

1. Legen Sie die `X-Forwarded-Host` Kopfzeile mit dem Domänennamen fest.
1. Legen Sie Host-Header mit der Herkunft-Domäne fest, der Adobe CDN-Adresse. Der Wert sollte von Adobe stammen.
1. Schicken Sie die SNI-Kopfzeile an die Herkunft. Wie der Host-Header muss der sni-Header die Herkunft-Domäne sein.
1. Legen Sie die `X-Edge-Key`Variable fest, die erforderlich ist, um den Traffic korrekt an die AEM-Server zu leiten. Der Wert sollte von Adobe stammen.

Bevor Sie Live-Traffic akzeptieren, sollten Sie beim Adobe-Kundensupport überprüfen, ob das End-to-End-Traffic-Routing ordnungsgemäß funktioniert.

## Caching {#caching}

Die Zwischenspeicherung am CDN kann mithilfe von Dispatcher-Regeln konfiguriert werden. Beachten Sie, dass der Dispatcher auch die resultierenden Cache-Ablaufkopfzeilen berücksichtigt, wenn sie in der Dispatcher-Konfiguration aktiviert `enableTTL` sind. Dies bedeutet, dass bestimmte Inhalte auch dann aktualisiert werden, wenn Inhalte erneut veröffentlicht werden.

### HTML/Text {#html-text}

* standardmäßig vom Browser fünf Minuten lang zwischengespeichert, basierend auf dem Cache-Control-Header, der von der Apache-Ebene gesendet wird. Das CDN berücksichtigt diesen Wert ebenfalls.
* kann für alle HTML-/Textinhalte überschrieben werden, indem die `EXPIRATION_TIME` Variable in der Verwendung von AEM als Cloud-Dienst-SDK-Dispatcher-Tools definiert `global.vars` wird.
* kann auf einer feineren Ebene durch die folgenden apache mod_headers-Direktiven überschrieben werden:

```
<LocationMatch "\.(html)$">
        Header set Cache-Control "max-age=200"
</LocationMatch>
```

Sie müssen sicherstellen, dass eine Datei unter `src/conf.dispatcher.d/cache` der folgenden Regel (die sich in der Standardkonfiguration befindet) vorliegt:

```
/0000
{ /glob "*" /type "allow" }
```

* Beachten Sie, dass andere Methoden, einschließlich des Projekts [](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/)dispatcher-ttl AEM ACS Commons, Werte nicht erfolgreich außer Kraft setzen.

### Clientseitige Bibliotheken (js, css) {#client-side-libraries}

* Durch Verwendung des clientseitigen Bibliotheksrahmens von AEM wird JavaScript- und CSS-Code so generiert, dass Browser ihn unbegrenzt zwischenspeichern können, da Änderungen als neue Dateien mit einem eindeutigen Pfad angezeigt werden.  Mit anderen Worten, HTML, die auf die Client-Bibliotheken verweisen, werden nach Bedarf erstellt, damit Kunden neue Inhalte während der Veröffentlichung erleben können. Die Cachesteuerung ist bei älteren Browsern, die den Wert &quot;unveränderlich&quot;nicht einhalten, auf &quot;unveränderlich&quot;oder auf 30 Tage eingestellt.
* Weitere Informationen finden Sie im Abschnitt [Clientseitige Bibliotheken und Versionskonsistenz](#content-consistency) .

### Bilder und alle Inhalte, die groß genug sind und in der Blob-Datenspeicherung gespeichert sind {#images}

* standardmäßig nicht zwischengespeichert
* kann mithilfe der folgenden Apache- `mod_headers` Richtlinien auf feinere abgestufte Ebene eingestellt werden:

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

Stellen Sie sicher, dass Assets, die nicht im Cache gespeichert, sondern privat gespeichert werden sollen, nicht zu den Filtern der LocationMatch-Direktive gehören.

* Beachten Sie, dass andere Methoden, einschließlich des Projekts [](https://adobe-consulting-services.github.io/acs-aem-commons/features/dispatcher-ttl/)dispatcher-ttl AEM ACS Commons, Werte nicht erfolgreich außer Kraft setzen.

### Andere Inhaltdateitypen im Knotenspeicher {#other-content}

* keine standardmäßige Zwischenspeicherung
* default kann nicht mit der für HTML/Textdateitypen verwendeten `EXPIRATION_TIME` Variablen eingestellt werden
* Cache-Ablauf kann mit derselben LocationMatch-Strategie festgelegt werden, die im Abschnitt html/text beschrieben wird, indem der entsprechende regex angegeben wird

## Dispatcher {#disp}

Traffic wird über einen Apache-Webserver ausgeführt, der Module einschließlich des Dispatchers unterstützt. Der Dispatcher wird primär als Cache verwendet, um die Verarbeitung auf den Veröffentlichungsknoten zu beschränken, um die Leistung zu erhöhen.

Wie im Abschnitt zum Zwischenspeichern des CDN beschrieben, können Regeln auf die Dispatcher-Konfiguration angewendet werden, um alle standardmäßigen Ablaufeinstellungen für den Cache zu ändern.

Der Rest dieses Abschnitts beschreibt Überlegungen zur Ungültigmachung des Dispatcher-Cache. Für die meisten Kunden sollte es nicht erforderlich sein, den Dispatcher-Cache zu ungültigen, sondern sich stattdessen darauf zu verlassen, dass der Dispatcher seinen Cache aktualisiert, wenn Inhalte erneut veröffentlicht werden, und das CDN die Cache-Ablaufkopfzeilen respektiert.

### Dispatcher-Cache-Ungültigkeit während der Aktivierung/Deaktivierung {#cache-activation-deactivation}

Wie bei früheren Versionen von AEM wird der Inhalt durch Veröffentlichen oder Rückgängigmachen der Veröffentlichung aus dem Dispatcher-Cache gelöscht. Wenn ein Zwischenspeicherungsproblem vermutet wird, sollten Kunden die betreffenden Seiten erneut veröffentlichen.

Wenn die Veröffentlichungsinstanz eine neue Version einer Seite oder eines Assets vom Autor erhält, verwendet sie den Flush-Agent, um entsprechende Pfade in ihrem Dispatcher zu ungültigen. Der aktualisierte Pfad wird zusammen mit den übergeordneten Elementen bis zu einer Ebene aus dem Dispatcher-Cache entfernt (Sie können dies mit dem [statfileslevel](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#invalidating-files-by-folder-level)konfigurieren).

### Ungültigmachen des expliziten Dispatcher-Cache {#explicit-invalidation}

Im Allgemeinen ist es nicht notwendig, Inhalte im Dispatcher manuell zu ungültigen, aber es ist möglich, wenn nötig, wie unten beschrieben.

Vor AEM als Cloud-Dienst gab es zwei Möglichkeiten, den Dispatcher-Cache zu ungültigen.

1. Rufen Sie den Replizierungsagenten auf und geben Sie den Veröffentlichungs-Dispatcher-Flush-Agent an
2. Direkter Aufruf der `invalidate.cache` API (z. B. `POST /dispatcher/invalidate.cache`)

Der `invalidate.cache` API-Ansatz des Dispatchers wird nicht mehr unterstützt, da er nur einen bestimmten Dispatcher-Knoten anspricht. AEM als Cloud-Dienst funktioniert auf Dienstebene, nicht auf der Ebene einzelner Knoten. Daher sind die Ungültigmachungsanweisungen auf der Seite &quot; [Ungültige zwischengespeicherte Seiten von AEM](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/page-invalidate.html) &quot;nicht mehr für AEM als Cloud-Dienst gültig.
Stattdessen sollte der Replizierungsspülmittel verwendet werden. Dies kann mithilfe der Replikations-API erfolgen. Die Replikations-API-Dokumentation ist [hier](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/replication/Replicator.html) verfügbar. Ein Beispiel für das Bereinigen des Cache finden Sie auf der [API-Beispielseite](https://helpx.adobe.com/experience-manager/using/aem64_replication_api.html) speziell im `CustomStep` Beispiel, in dem eine Replizierungsaktion des Typs ACTIVATE an alle verfügbaren Agenten ausgegeben wird. Der Endpunkt des Flush-Agenten ist nicht konfigurierbar, sondern vorkonfiguriert, um auf den Dispatcher zu verweisen. Er ist mit dem Veröffentlichungsdienst, der den Flush-Agent ausführt, übereinstimmen. Der Flush-Agent kann in der Regel von OSGi-Ereignissen oder Workflows ausgelöst werden.

Das unten dargestellte Diagramm veranschaulicht dies.

![](assets/cdnd.png "CDNCDN")

Wenn Bedenken bestehen, dass der Dispatcher-Cache nicht geleert wird, wenden Sie sich an den [Kundensupport](https://helpx.adobe.com/support.ec.html) , der den Dispatcher-Cache ggf. bereinigen kann.

Das von Adobe verwaltete CDN berücksichtigt TTLs und muss daher nicht gerötet werden. Bei Verdacht auf ein Problem [wenden Sie sich an den Support](https://helpx.adobe.com/support.ec.html) des Kunden, der nach Bedarf einen von Adobe verwalteten CDN-Cache leeren kann.

## Clientseitige Bibliotheken und Versionskonsistenz {#content-consistency}

Die Seiten bestehen aus HTML, Javascript, CSS und Bildern. Kunden werden empfohlen, das clientlibs-Framework (clientlibs) zu nutzen, um JavaScript- und CSS-Ressourcen in HTML-Seiten zu importieren, wobei Abhängigkeiten zwischen JS-Bibliotheken berücksichtigt werden.

Das clientlibs-Framework bietet eine automatische Versionsverwaltung, d. h. Entwickler können Änderungen an JS-Bibliotheken in der Quellcodeverwaltung einchecken und die neueste Version wird zur Verfügung gestellt, wenn ein Kunde seine Veröffentlichung vorantreibt. Andernfalls müssten Entwickler HTML mit Verweisen auf die neue Version der Bibliothek manuell ändern. Dies ist besonders aufwändig, wenn viele HTML-Vorlagen dieselbe Bibliothek gemeinsam nutzen.

Wenn die neuen Bibliotheksversionen in die Produktion freigegeben werden, werden die referenzierenden HTML-Seiten mit neuen Links zu diesen aktualisierten Bibliotheksversionen aktualisiert. Sobald der Browser-Cache für eine bestimmte HTML-Seite abgelaufen ist, besteht kein Problem, dass die alten Bibliotheken aus dem Browser-Cache geladen werden, da die aktualisierte Seite (von AEM) nun garantiert auf die neuen Versionen der Bibliotheken verweist. Mit anderen Worten, eine aktualisierte HTML-Seite enthält alle aktuellen Bibliotheksversionen.

Der Mechanismus hierfür ist ein serialisierter Hash, der an den Link der Client-Bibliothek angehängt wird und eine eindeutige, versionierte URL gewährleistet, damit der Browser die CSS/JS zwischenspeichert. Der serialisierte Hash wird nur aktualisiert, wenn sich der Inhalt der Client-Bibliothek ändert. Das bedeutet, dass bei nicht zusammenhängenden Aktualisierungen (d. h. bei keiner Änderung der zugrunde liegenden CSS/js der Client-Bibliothek) auch bei einer neuen Bereitstellung der Verweis gleich bleibt, wodurch eine weniger Unterbrechung des Browser-Cache sichergestellt wird.

### Aktivieren von Longcache-Versionen clientseitiger Bibliotheken - AEM als Cloud-Dienst-SDK-Schnellstart {#enabling-longcache}

Die standardmäßigen clientlib-Includes auf einer HTML-Seite sehen wie im folgenden Beispiel aus:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.css" type="text/css">
```

Wenn strikte clientlib-Versionierung aktiviert ist, wird der Client-Bibliothek ein langfristiger Hashschlüssel als Selektor hinzugefügt. Daher sieht der clientlib-Verweis wie folgt aus:

```
<link rel="stylesheet" href="/etc.clientlibs/wkndapp/clientlibs/clientlib-base.lc-7c8c5d228445ff48ab49a8e3c865c562-lc.css" type="text/css">
```

Strenge clientlib-Versionen sind in allen AEM als Cloud-Dienst-Umgebung standardmäßig aktiviert.

So aktivieren Sie eine strikte clientlib-Version im lokalen SDK QuickStart:

1. Navigate to the OSGi Configuration manager `<host>/system/console/configMgr`
1. Suchen Sie die OSGi-Konfiguration für Adobe Granite HTML Library Manager:
   * Aktivieren Sie das Kontrollkästchen, um die strikte Versionierung zu aktivieren.
   * Geben Sie in das Feld Long term client side cache key den Wert / ein.*;Hash
1. Speichern Sie die Änderungen. Beachten Sie, dass diese Konfiguration nicht in der Quellcodeverwaltung gespeichert werden muss, da AEM als Cloud-Dienst diese Konfiguration automatisch in dev-, stage- und production-Umgebung aktiviert.
1. Bei jeder Änderung des Inhalts der Client-Bibliothek wird ein neuer Hashschlüssel generiert und der HTML-Verweis wird aktualisiert.
