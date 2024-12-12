---
title: Pipeline-freie URL-Umleitungen
description: Erfahren Sie, wie Sie 301- oder 302-Umleitungen ohne Zugriff auf Git- oder Cloud Manager-Pipelines deklarieren.
feature: Dispatcher
role: Admin
exl-id: dacb1eda-79e0-4e76-926a-92b33bc784de
source-git-commit: 41d610728fe92b07db722694432653cf7f03ce9c
workflow-type: tm+mt
source-wordcount: '699'
ht-degree: 78%

---

# Pipeline-freie URL-Umleitungen {#pipeline-free-redirects}

Aus verschiedenen Gründen schreiben Organisationen URLs so um, dass eine 301- oder 302-Umleitung erfolgt. Das bedeutet, dass der Browser zu einer anderen Seite umgeleitet wird.

Mögliche Szenarien sind etwa:

* eine entfernte HTML-Seite, sodass Benutzende zu einer Ersatzseite (manchmal zur Startseite) weitergeleitet werden, anstatt den Fehler `404 Page Not Found` zu sehen,
* eine umbenannte HTML-Seite,
* SEO-Optimierung.

AEM as a Cloud Service bietet [mehrere Ansätze](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/administration/url-redirection) zur Implementierung Client-seitiger Umleitungen. Die in diesem Artikel beschriebene Strategie Pipeline-freier Umleitungen ist allerdings in folgenden Fällen eine gute Wahl:

* Bei den Personen, die für die Umleitungen zuständig sind, handelt es sich um Business-Anwendende, denen die erforderlichen Zugriffsrechte zum Übertragen von Dateiänderungen an die Quell-Code-Verwaltung fehlen oder die nicht die Möglichkeit haben, eine Cloud Manager-Konfigurations-Pipeline auf Web-Ebene auszuführen.
* Der Umfang reicht von wenigen bis hin zu Zehntausenden von Umleitungen.
* Sie möchten die Option einer Benutzeroberfläche wählen, die entweder als benutzerdefiniertes Projekt oder mithilfe des [ACS Commons Redirect Map Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html) erstellt wurde.

Das Kernstück dieser Funktion ist die Möglichkeit für AEM Apache/Dispatcher, eine oder mehrere Rewrite-Zuordnungsdateien (neu) zu laden, die an einem bestimmten Speicherort im Veröffentlichungs-Repository abgelegt wurden. Hierbei ist darauf hinzuweisen, dass die Art und Weise, wie die Dateien dorthin gelangen, außerhalb des Anwendungsbereichs dieser Funktion liegt. Sie können jedoch eine der folgenden Methoden in Betracht ziehen:

* Aufnehmen der Rewrite-Zuordnung als Asset in der Autorenbenutzeroberfläche mit anschließender Veröffentlichung.
* Installieren des [ACS Commons Redirect Map Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html) ([mindestens 6.7.0 Version oder höher](https://github.com/Adobe-Consulting-Services/acs-aem-commons/releases)), der eine Benutzeroberfläche zum Verwalten der URL-Zuordnungen enthält und auch die Rewrite-Map-Datei veröffentlichen kann.
* Volle Flexibilität durch Schreiben einer benutzerdefinierten Anwendung. Beispiel: eine Benutzeroberfläche oder Befehlszeilenschnittstelle zum Verwalten der URL-Zuordnungen oder alternativ ein Formular zum Hochladen einer Rewrite-Zuordnung, die dann AEM-APIs verwendet, um die Rewrite-Zuordnungsdatei zu veröffentlichen.

>[!NOTE]
> Für diese Funktion ist die AEM-Version **18311 oder höher** erforderlich.

>[!NOTE]
> Für die Verwendung des Redirect Map Managers ist die ACS Commons-Version **6.7.0 oder höher** erforderlich.

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

Anschließend müssen Sie in einer Apache-Konfigurationsdatei wie `rewrites/rewrite.rules` oder `<yourfile>.vhost` die Zuordnungsdatei konfigurieren, auf die durch die name -Eigenschaft verwiesen wird (`my.map` im obigen Beispiel). Nach dem Laden wird diese Zuordnungsdatei im lokalen Dispatcher-Speicher unter dem Speicherort **fixed** location `/tmp/rewrites/` gespeichert.

Die Anweisung `RewriteMap` sollte angeben, dass die Daten im DBM-Dateiformat (Database Manager) unter Verwendung des Formats `sdbm` (einfaches DBM) gespeichert werden und der vollständige Dateipfad vom Speicherort-Speicherort-Präfix und der name-Eigenschaft abgeleitet wird.

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
