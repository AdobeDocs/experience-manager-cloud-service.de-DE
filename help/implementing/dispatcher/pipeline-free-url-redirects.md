---
title: Pipeline-freie URL-Umleitungen
description: Erfahren Sie, wie Sie 301- oder 302-Umleitungen ohne Zugriff auf Git- oder Cloud Manager-Pipelines deklarieren.
feature: Dispatcher
role: Admin
exl-id: dacb1eda-79e0-4e76-926a-92b33bc784de
source-git-commit: 7a543c8fe63166ef34999f23ce9b05de8e8b0e9f
workflow-type: tm+mt
source-wordcount: '781'
ht-degree: 96%

---

# Pipeline-freie URL-Umleitungen {#pipeline-free-redirects}

Aus verschiedenen Gründen schreiben Organisationen URLs so um, dass eine 301- oder 302-Umleitung erfolgt. Das bedeutet, dass der Browser zu einer anderen Seite umgeleitet wird.

Mögliche Szenarien sind etwa:

* eine entfernte HTML-Seite, sodass Benutzende zu einer Ersatzseite (manchmal zur Startseite) weitergeleitet werden, anstatt den Fehler `404 Page Not Found` zu sehen,
* eine umbenannte HTML-Seite,
* SEO-Optimierung.

AEM as a Cloud Service offers [several approaches](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/administration/url-redirection) to implement server-side redirects, but the strategy described in this article, pipeline-free redirects, is a good choice when:

* Bei den Personen, die für die Umleitungen zuständig sind, handelt es sich um Business-Anwendende, denen die erforderlichen Zugriffsrechte zum Übertragen von Dateiänderungen an die Quell-Code-Verwaltung fehlen oder die nicht die Möglichkeit haben, eine Cloud Manager-Konfigurations-Pipeline auf Web-Ebene auszuführen.
* Der Umfang reicht von wenigen bis hin zu Zehntausenden von Umleitungen.
* Am besten geeignet ist die Option einer Benutzeroberfläche, die entweder als benutzerdefiniertes Projekt oder mit [ACS Commons Redirect Map Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html) oder [ACS Commons Redirect Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-manager/subpages/rewritemap.html) erstellt wird.

Das Kernstück dieser Funktion ist die Möglichkeit für AEM Apache/Dispatcher, eine oder mehrere Rewrite-Zuordnungsdateien (neu) zu laden, die an einem bestimmten Speicherort im Veröffentlichungs-Repository abgelegt wurden (sodass sie vom AEM-Veröffentlichungsdienst heruntergeladen werden können). Hierbei ist darauf hinzuweisen, dass die Art und Weise, wie die Dateien dorthin gelangen, außerhalb des Anwendungsbereichs dieser Funktion liegt. Sie können jedoch eine der folgenden Methoden in Betracht ziehen:

* Aufnehmen der Rewrite-Zuordnung als Asset in der Autorenbenutzeroberfläche mit anschließender Veröffentlichung.
* Installation des [ACS Commons Rewrite Map Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html) ([mindestens Version 6.7.0](https://github.com/Adobe-Consulting-Services/acs-aem-commons/releases)), der eine Benutzeroberfläche zum Verwalten der URL-Zuordnungen enthält und auch die Rewrite-Zuordnungsdatei veröffentlichen kann.
* Installieren von [ACS Commons Rewrite Map Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-manager/subpages/rewritemap.html) ([mindestens Version 6.10.0](https://github.com/Adobe-Consulting-Services/acs-aem-commons/releases)), wobei eine Benutzeroberfläche zum Verwalten der URL-Zuordnungen enthalten ist und außerdem die Rewrite-Zuordnungsdatei veröffentlicht werden kann.
* Volle Flexibilität durch Schreiben einer benutzerdefinierten Anwendung. Beispiel: eine Benutzeroberfläche oder Befehlszeilenschnittstelle zum Verwalten der URL-Zuordnungen oder alternativ ein Formular zum Hochladen einer Rewrite-Zuordnung, die dann AEM-APIs verwendet, um die Rewrite-Zuordnungsdatei zu veröffentlichen.

>[!NOTE]
> Für diese Funktion ist die AEM-Version **18311 oder höher** erforderlich.

>[!NOTE]
> Die Verwendung von Redirect Map Manager durch diese Funktion erfordert ACS Commons Version **6.7.0 oder höher**, während die Verwendung von Redirect Manager Version **6.10.0 oder höher** erfordert.

Eine detaillierte Schritt-für-Schritt-Anleitung zur Implementierung finden Sie im Tutorial [Implementieren von Pipeline-freien URL-Umleitungen](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/administration/implementing-pipeline-free-url-redirects).

## Die Rewrite-Zuordnung {#rewrite-map}

Die Rewrite-Zuordnung wird (im Falle einer Änderung) vom Apache HTTP-Server standardmäßig alle 300 Sekunden neu geladen (der Wert ist konfigurierbar). Das Dateiformat sollte dem in der [Apache-Dokumentation](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html#txt) beschriebenen RewriteMap-Dateiformat mit Nur-Text-Schlüssel-Wert-Zuordnung entsprechen.

Eine Datei mit dem Namen `managed-rewrite-maps.yaml` sollte erstellt werden, um den Speicherort der Rewrite-Zuordnungsdatei anzugeben; sie muss einmal mithilfe der Cloud Manager-Fullstack-Pipeline oder der Web-Ebenen-Pipeline bereitgestellt werden. Die Datei muss im Ordner [src/opt-in](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/dispatcher.cloud/src/opt-in) Ihrer Dispatcher-Konfiguration erstellt werden. Achten Sie darauf, die [Dateistruktur mit flexiblem Modus](/help/implementing/dispatcher/validation-debug.md#flexible-mode-file-structure) zu verwenden.

Sie können sie mit dem folgenden Muster konfigurieren:

```
maps:
- name: my.map
  path: <path-in-publish-repository>/redirectmap.txt
```

Wenn die Rewrite-Zuordnungsdatei beispielsweise dadurch platziert wird, dass Sie sie in AEM als Asset mit dem Namen `mysite-redirectmap.txt` aufnehmen und dann veröffentlichen, können Sie einen Ordner unter `/content/dam` angeben:

```
maps:
- name: my.map
  path: /content/dam/redirectmaps/mysite-redirectmap.txt
```

Anschließend müssen Sie in einer Apache-Konfigurationsdatei wie `rewrites/rewrite.rules` oder `<yourfile>.vhost` die durch die Eigenschaft „name“ referenzierte Zuordnungsdatei konfigurieren (`my.map` im obigen Beispiel). Nach dem Laden wird diese Zuordnungsdatei im lokalen Dispatcher-Speicher unter dem **festen** Speicherort gespeichert`/tmp/rewrites/`.

Die Anweisung `RewriteMap` sollte angeben, dass die Daten im DBM-Dateiformat (Database Manager) unter Verwendung des `sdbm`-Formats (einfacher DBM) gespeichert werden und der vollständige Dateipfad aus dem Präfix des Speicherorts und der Eigenschaft „name“ abgeleitet wird.

Der Rest der Konfiguration hängt vom Format der Datei `redirectmap.txt` ab. Das einfachste Format, zu sehen im folgenden Beispiel, ist eine 1:1-Zuordnung zwischen der ursprünglichen URL und der zugeordneten URL:

```
# RewriteMap from managed rewrite maps
RewriteMap map.foo dbm=sdbm:/tmp/rewrites/my.map
RewriteCond ${map.foo:$1} !=""
RewriteRule ^(.*)$ ${map.foo:$1|/} [L,R=301]
```

## Überlegungen {#considerations}

Beachten Sie dabei Folgendes:

* Standardmäßig startet Apache beim Laden einer Rewrite-Zuordnung, ohne auf das Laden der vollständigen Zuorddnungsdatei(en) zu warten. Daher kann es, bis die vollständigen Zuordnungen geladen sind, vorübergehend zu Inkonsistenzen kommen. Diese Einstellung kann so geändert werden, dass Apache darauf wartet, dass der gesamte Zuordnungsinhalt geladen wird. Es dauert dann jedoch länger, bis Apache gestartet wird. Um dieses Verhalten so zu ändern, dass Apache wartet, fügen Sie `wait:true` zur Datei `managed-rewrite-maps.yaml` hinzu.
* Um das Intervall zwischen den Ladevorgängen zu ändern, fügen Sie `ttl: <integer>` zur Datei `managed-rewrite-maps.yaml` hinzu. Beispiel: `ttl: 120`.
* Apache hat eine Längenbeschränkung von 1024 für RewriteMap-Einzeleinträge.

## Tutorials {#tutorials}

1. [Implementieren von Pipeline-freien URL-Umleitungen](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/administration/implementing-pipeline-free-url-redirects)
1. [URL-Umleitungen](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/administration/url-redirection)
