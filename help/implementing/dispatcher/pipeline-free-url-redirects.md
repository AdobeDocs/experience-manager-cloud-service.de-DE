---
title: Pipeline-freie URL-Umleitungen
description: Erfahren Sie, wie Sie 301- oder 302-Umleitungen ohne Zugriff auf Git- oder Cloud Manager-Pipelines deklarieren.
feature: Dispatcher
role: Admin
source-git-commit: 36b7d72f24bd60ad94762c9c9937105bea6e31b6
workflow-type: tm+mt
source-wordcount: '644'
ht-degree: 0%

---

# Pipeline-freie URL-Umleitungen {#pipeline-free-redirects}

Aus verschiedenen Gründen schreiben Unternehmen URLs so um, dass eine 301- (oder 302-) Umleitung erfolgt. Das bedeutet, dass der Browser zu einer anderen Seite umgeleitet wird.

Zu den Szenarien gehören:

* Eine entfernte HTML-Seite, sodass der Benutzer zu einer Ersatzseite (manchmal zur Startseite) gelangt, anstatt einen `404 Page Not Found` -Fehler zu sehen.
* Eine umbenannte HTML-Seite.
* SEO-Optimierung.

AEM as a Cloud Service bietet [mehrere Ansätze](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/administration/url-redirection) zur Implementierung clientseitiger Weiterleitungen. Die in diesem Artikel beschriebene Strategie, Pipeline-freie Weiterleitungen, ist jedoch eine gute Wahl, wenn:

* Die Personen, die die Umleitungen verwalten, sind Geschäftsbenutzer, die nicht den erforderlichen Zugriff haben, um Dateiänderungen an die Quellcodeverwaltung zu übertragen, oder die Möglichkeit, eine Cloud Manager-Web-Tier-Konfigurationspipeline auszuführen.
* Die Anzahl der Umleitungen reicht von wenigen bis zehntausend.
* Sie möchten die Option einer Benutzeroberfläche wählen, die entweder als benutzerdefiniertes Projekt oder mit dem [ACS Commons Rewrite Map Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html) erstellt wurde.

Das Kernstück dieser Funktion ist die Möglichkeit für AEM Apache/Dispatcher, eine oder mehrere Rewrite-Map-Dateien zu laden (oder neu zu laden), die sich an einem bestimmten Speicherort im Veröffentlichungs-Repository befinden. Es ist wichtig zu erwähnen, dass die Art und Weise, wie die Dateien dorthin gelangen, außerhalb des Anwendungsbereichs dieser Funktion liegt. Sie können jedoch eine der folgenden Methoden in Betracht ziehen:

* Erfassen der Rewrite-Zuordnung als Asset in der Authoring-Benutzeroberfläche und Veröffentlichen.
* Installieren Sie den [ACS Commons Rewrite Map Manager](https://adobe-consulting-services.github.io/acs-aem-commons/features/redirect-map-manager/index.html), der eine Benutzeroberfläche zum Verwalten der URL-Zuordnungen enthält und auch die Rewrite-Zuordnungsdatei veröffentlichen kann.
* Volle Flexibilität durch Schreiben eines benutzerdefinierten Programms. Beispielsweise eine Benutzeroberfläche oder Befehlszeilenschnittstelle zum Verwalten der URL-Zuordnungen oder alternativ ein Formular zum Hochladen einer Umschreibungszuordnung, die dann AEM APIs verwendet, um die Umschreibungszuordnungsdatei zu veröffentlichen.

>[!NOTE]
> Diese Funktion erfordert AEM Version **18311 oder höher**.

## Die Rewrite-Zuordnung {#rewrite-map}

Die Rewrite-Zuordnung wird vom Apache HTTP-Server standardmäßig alle 300 Sekunden neu geladen (wenn dieser Wert geändert wird). Das Dateiformat sollte dem in der [Apache-Dokumentation](https://httpd.apache.org/docs/2.4/rewrite/rewritemap.html#txt) beschriebenen Nur-Text-Schlüsselwert-map-Dateiformat RewriteMap entsprechen.

Eine Datei mit dem Namen `managed-rewrite-maps.yaml` sollte erstellt werden, um den Speicherort der Rewrite-Map-Datei anzugeben, und sie muss einmal mithilfe der vollständigen Cloud Manager-Stack-Pipeline oder der Web-Tier-Pipeline bereitgestellt werden. Die Datei muss im Ordner [src/opt-in](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/dispatcher.cloud/src/opt-in) Ihrer Dispatcher-Konfiguration erstellt werden. Stellen Sie sicher, dass Sie die [Dateistruktur mit flexiblem Modus](/help/implementing/dispatcher/validation-debug.md#flexible-mode-file-structure) verwenden.

Sie können sie mit dem folgenden Muster konfigurieren:

```
maps:
- name: my.map
  path: <path-in-publish-repository>/redirectmap.txt
```

Wenn beispielsweise die Methode zum Platzieren der Rewrite-Map-Datei darin besteht, sie in AEM als Asset mit dem Namen `mysite-redirectmap.txt` zu erfassen und sie dann zu veröffentlichen, können Sie einen Ordner unter `/content/dam` angeben:

```
maps:
- name: my.map
  path: /content/dam/redirectmaps/mysite-redirectmap.txt
```

Anschließend müssen Sie in einer Apache-Konfigurationsdatei wie `rewrites/rewrite.rules` oder `<yourfile>.vhost` die Zuordnungsdatei konfigurieren, auf die durch die name -Eigenschaft verwiesen wird (`my.map` im obigen Beispiel).

Die Anweisung `RewriteMap` sollte angeben, dass die Daten im DBM-Dateiformat (Database Manager) unter Verwendung des Formats `sdbm` (einfaches DBM) gespeichert werden.

Der Rest der Konfiguration hängt vom Format des `redirectmap.txt` ab. Das einfachste Format, das im folgenden Beispiel gezeigt wird, ist eine 1:1-Zuordnung zwischen der ursprünglichen URL und der zugeordneten URL:

```
# RewriteMap from managed rewrite maps
RewriteMap map.foo dbm=sdbm:/tmp/rewrites/my.map
RewriteCond ${map.foo:$1} !=""
RewriteRule ^(.*)$ ${map.foo:$1|/} [L,R=301]
```


## Überlegungen {#considerations}

Beachten Sie Folgendes:

* Standardmäßig startet Apache beim Laden einer Rewrite-Map, ohne darauf zu warten, dass die vollständigen Map-Dateien geladen werden. Daher kann es temporäre Inkonsistenzen geben, bis die vollständigen Map(s) geladen werden. Diese Einstellung kann so geändert werden, dass Apache darauf wartet, dass der gesamte Zuordnungsinhalt geladen wird, aber der Start von Apache länger dauert. Um dieses Verhalten so zu ändern, dass Apache wartet, fügen Sie `wait:true` zur Datei `managed-rewrite-maps.yaml` hinzu.
* Um die Häufigkeit zwischen den Ladevorgängen zu ändern, fügen Sie `ttl: <integer>` zur Datei `managed-rewrite-maps.yaml` hinzu. Beispiel: `ttl: 120`.
* Apache hat eine Längenbeschränkung von 1024 für RewriteMap-Einzeleinträge.
