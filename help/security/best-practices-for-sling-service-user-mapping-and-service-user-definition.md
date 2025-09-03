---
title: Best Practices für Sling Service-Benutzerzuordnung und Dienstbenutzerdefinition
description: Erfahren Sie mehr über die Best Practices für die Sling Service-Benutzerzuordnung und die Dienstbenutzerdefinition
exl-id: 72f0dcbf-b4e6-4a73-8232-3574a212ac19
feature: Security
role: Admin
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: ht
source-wordcount: '1883'
ht-degree: 100%

---

# Best Practices für Sling Service-Benutzerzuordnung und Dienstbenutzerdefinition {#best-practices-for-sling-service-user-mapping-and-service-user-definition}

## Dienstbenutzerzuordnung {#service-user-mapping}

Um eine Zuordnung von Ihrem Dienst zu den entsprechenden Systembenutzenden hinzuzufügen, müssen Sie eine Werkskonfiguration für den Dienst `ServiceUserMapper` erstellen. Um die Modularität zu gewährleisten, können derartige Konfigurationen mithilfe des Sling-Änderungsmechanismus bereitgestellt werden (siehe [SLING-3578](https://issues.apache.org/jira/browse/SLING-3578) für weitere Details). Die empfohlene Methode zur Installation solcher Konfigurationen mit Ihrem Bundle besteht darin, sie zum Schnellstart-Bereitstellungsmodell hinzuzufügen, wie im folgenden Beispiel beschrieben:

```
org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-my-mapping
    user.default=""
    user.mapping=[
        "com.adobe.cq.my-bundle:my-subservice\=[content-writer-service]",
        "com.adobe.cq.my-bundle:my-subservice-different-task\="[myfeature-configuration-writer-service,content-reader-service]"
    ]
```

### Zuordnungsformat {#mapping-format}

Seit AEM 6.4 wird das Zuordnungsformat wie folgt definiert:

>[!NOTE]
>
>Die Variable `userName` ist veraltet und sollte nicht mehr verwendet werden.

```
bundleId [:subserviceName] = userName | [principalNames]   
```

`bundleId` und `subserviceName` identifizieren den Dienst, `userName/principalNames` identifiziert die Person, die den Dienst benutzt, und `principalNames` ist eine durch Kommata getrennte Liste.

Beachten Sie auch, dass `principalNames` die Liste der Dienstbenutzer-Prinzipalnamen ist, die standardmäßig mit der ID identisch sind.


**Best Practice**

* Namen von Unterdiensten für verschiedene Aufgaben – wenn die Dienste Ihres Bundles verschiedene Aufgaben ausführen, wird empfohlen, die `subserviceNames` zu identifizieren, um sie nach Aufgaben zu gruppieren
* Wenn ein bestimmter Dienst verschiedene Operationen durchführt (z. B. das Lesen von Asset-Inhalten und das Aktualisieren von Informationen unterhalb einer Unterstruktur von `/var`), wird empfohlen, dies durch die Aggregation verschiedener Dienstprinzipale widerzuspiegeln, die die einzelnen Operationen widerspiegeln, wie z. B. die Aggregation des allgemeinen `dam-reader-service` mit Ihrem funktionsspezifischen `assetreport-writer-service`
* Jeder Dienst ist idealerweise an einen sehr spezifischen und begrenzten Satz von Vorgängen gebunden
* Das neue Format mit `[one,or,multiple,principalNames]` ist die empfohlene Methode zum Definieren von Dienstbenutzerzuordnungen ab AEM 6.4.

Nachstehend finden Sie eine Liste von Gründen für die Formatänderung und die Begründung, warum Adobe empfiehlt, das Format anstelle der Versionszuordnung nur für eine einzelne Benutzer-ID zu verwenden:

* Möglichkeit der Wiederverwendung von Dienstbenutzenden durch Kombination von besonderen Kundenbedürfnissen und allgemeinen Aufgaben
* Vermeiden von doppelten Berechtigungen
* Besseres Verständnis der effektiven Berechtigungen (und Aufgaben), die ein bestimmter Dienst tatsächlich ausführt
* Keine Notwendigkeit einer expliziten Gruppenmitgliedschaft von Dienstbenutzenden. Dies kann bei Änderung der Gruppenberechtigungen zu problematischen Nebenwirkungen führen
* Leistungsverbesserungen und Skalierbarkeit

## Zuordnungsauflösung und Dienstanmeldung {#mapping-resolution-and-service-login}

### Auflösung der Dienstzuordnung {#service-mapping-resolution}

Die Abfolge der Aufrufe zum Auflösen der Dienstzuordnung wird im Folgenden beschrieben:

1. Durchführen einer Suche nach aktiver `principalNames`-Zuordnung für die angegebene `bundleId` und den `subserviceName`
1. `principalNames`-Zuordnung für die `bundleId` und einen leeren `subserviceName`
1. `userName`-Zuordnung für die `bundleId` und den `subserviceName`
1. `userName`-Zuordnung für die `bundleId` und einen leeren `subserviceName`
1. Standardzuordnung
1. Standardbenutzerin oder -benutzer

### SlingRepository – Dienstanmeldung {#slingrepository-servicelogin}

Die Sequenz für das Erhalten eines `Session/ResourceResolver` für einen Dienst funktioniert wie folgt:

1. Abrufen von Prinzipalnamen von `ServiceUserMapper` => Repository-Anmeldung vor der Authentifizierung, wie unten beschrieben
1. Abrufen der Benutzer-ID von `ServiceUserMapper`
1. Suchen nach einer veralteten `1ServiceUserConfiguration` für die aktuelle Benutzer-ID
1. Standardmäßige Sling Service-Anmeldung mit der Benutzer-ID (z. B. eine Sequenz von `createAdministrativeSession` und stellvertretend für die Dienstbenutzer-ID)

Die neue Zuordnung mit Prinzipalnamen führt zur folgenden vereinfachten Repository-Anmeldung:

* Die Gruppe von Prinzipalnamen wird als die effektiven Prinzipale behandelt, die zum Ausfüllen des `Subject` verwendet werden sollen
* Die Repository-Anmeldung kann somit vorauthentifiziert werden
* Keine Auflösung der Gruppenmitgliedschaft

  >[!NOTE]
  >
  >Alle erforderlichen Berechtigungen müssen für die Dienstbenutzenden deklariert werden. „Alle“ und andere Gruppenberechtigungen werden nicht mehr vererbt.

* Keine zusätzliche Admin-Anmeldung für die Erstellung des Dienst-`Session/ResourceResolver` notwendig.

### Veraltete ServiceUserConfiguration {#deprecated-serviceUserConfiguration}

Beachten Sie, dass die Angabe eines einzelnen Benutzernamens in der Zuordnung dem vorhandenen Format `ServiceUserConfiguration.simpleSubjectPopulation` entspricht. Mit dem neuen Format kann die Problemumgehung, die von der `ServiceUserConfiguration` bereitgestellt wird, direkt mit der Dienstbenutzerzuordnung wiedergegeben werden. `ServiceUserConfiguration` wird daher für AEM nicht mehr unterstützt und alle bestehenden Verwendungen wurden ersetzt.

## Dienstbenutzende {#service-users}

### Wiederverwenden vorhandener Dienstbenutzender {#reusing-existing-service-users}

Es wird empfohlen, vorhandene Dienstbenutzende erneut zu verwenden, wenn die folgenden Bedingungen erfüllt sind:

* Ihre Anforderungen stimmen mit dem Kriterium der vorhandenen Dienstbenutzenden überein.
* Der Dienst erfordert die Ausführung einer allgemeinen Aufgabe, die von vorhandenen allgemeinen Dienstbenutzenden abgedeckt wird. In diesem Fall wird empfohlen, Dienstbenutzende wiederzuverwenden, statt Duplikate zu erstellen.
* Der Dienst erfordert eine bestimmte Aufgabe, die von vorhandenen Dienstbenutzenden abgedeckt wird. Wenn Sie sich diesbezüglich nicht sicher sind, fragen Sie das Funktions-Team, dem sie gehört.

Verwenden Sie vorhandene Dienstbenutzende nicht erneut, wenn:

* Sie die Berechtigungen auf eine davon unabhängige Weise ändern müssten, damit sie funktionieren.
* Sie nur eine kleine Teilmenge der Berechtigungen benötigen, die sie bieten, und Sie sie einfach wiederverwenden würden, weil Ihre Funktion dadurch funktioniert und nicht, weil sie wirklich übereinstimmen.
* der Name einen völlig anderen Zweck beschreibt, als Sie benötigen. Wenn Sie dies aus einem solchen Grund auswählen, kann es später zu Problemen kommen, wenn das Funktions-Team, dem ein bestimmter Dienst gehört, die Berechtigungen ändert und die Funktion somit nicht mehr funktioniert.

### Erstellen von Dienstbenutzenden {#creating-a-service-user}

Nachdem Sie überprüft haben, dass keine Dienstbenutzerin und auch kein Dienstbenutzer in AEM Ihrem Anwendungsfall entspricht und die jeweiligen RTC-Ausgaben genehmigt wurden, können Sie die neue Benutzerin bzw. den neuen Benutzer zum Standardinhalt hinzufügen. Idealerweise ist ein Mitglied des erweiterten Sicherheits-Teams an der RTC-Abstimmung beteiligt. Stellen Sie daher sicher, dass Sie auch die entsprechenden Verantwortlichen einbeziehen.

**Namenskonvention**

Das AEM-Sicherheits-Team hat die folgende Namenskonvention definiert, damit Dienstbenutzende neue Dienstbenutzende konsistent benennen und ihre Lesbarkeit und Wartbarkeit verbessern können.

Ein Dienstbenutzername besteht aus 3 Elementen, die durch einen Bindestrich **&#39;-&#39;** voneinander getrennt sind:

1. Die logische Entität/Funktion, auf die die Dienstvorgänge abzielen (vermeiden Sie Pfade, die sich ändern können)
1. Die Aufgabe, die die Dienste ausführen sollen
1. Und abschließend **&#39;service&#39;**, um aus der ID und dem Prinzipalnamen leicht schlussfolgern zu können, dass die Benutzerin bzw. der Benutzer eine Dienstbenutzerin bzw. ein -benutzer ist

**Best Practices**

* Vermischen Sie keine unterschiedlichen Entitäten/Funktionen. Teilen Sie sie auf einzelne Dienstbenutzende auf und fassen Sie sie in der Zuordnung zusammen, wenn Ihr Dienst unterschiedliche Anforderungen hat
* Beschränken Sie sich auf eine klar definierte Aufgabe pro Dienstbenutzerin bzw. -benutzer. Teilen Sie sie auf unterschiedliche Dienstbenutzende auf, wenn Sie zu viele oder nicht verwandte Berechtigungen gewähren
* Nehmen Sie sich ausreichend Zeit, um die tatsächliche Notwendigkeit Ihres Dienstes zu ermitteln
* Nehmen Sie sich Zeit bei der Suche nach einem guten, aussagekräftigen und selbsterklärenden Namen für die Dienstbenutzerin bzw. den -benutzer.
* Bitten Sie um Feedback und eine Überprüfung: Entwicklerinnen und Entwickler, die mit Ihrer Funktion nicht vertraut sind, sollten in der Lage sein, den Zweck zu erkennen und zu verstehen. Sie könnten in Zukunft beauftragt werden, Probleme zu beheben oder sie zu warten.

Am Ende sollte der Name der Dienstbenutzerin bzw. des -benutzers Folgendes anzeigen:

* Vorgesehene Verwendung und Wiederverwendbarkeit:

   * Sehr allgemein: `content-writer-service`. Sichere Wiederverwendung in der Aggregation, wenn Ihre Dienste auch in der Lage sein müssen, alle Inhalte zu lesen
   * Sehr spezifisch: `asset-linkshare-service`. Es ist nicht so sicher, die Assets wiederzuverwenden, es sei denn, Ihr Dienst nutzt tatsächlich die Freigabe von Assets per Link.

* Wie der Funktionsumfang und die Einrichtung der Berechtigungen aussehen können:

   * Die logische Entität muss mit dem Setup der Berechtigung übereinstimmen:

      * Ein `content-foo-service` sollte nur mit Vorgängen zu Inhalten verknüpft werden. Es wäre falsch, ihr Berechtigungen zu erteilen, mit anderen Entitäten wie Konfiguration oder Benutzenden zu arbeiten
      * Ein bestimmter Dienst, z. B. `personalization-foo-service`, sollte auch mit bestimmten Berechtigungen versehen werden. Wenn Sie letztendlich Berechtigungen für alle Inhalte erteilen, ist dies nicht mehr spezifisch. Stellen Sie sicher, dass dies im Namen widergespiegelt wird, oder verwenden Sie eine allgemeine Benutzerin bzw. einen allgemeinen Benutzer in der Aggregation erneut.
      * Ein funktionsspezifischer Dienst wie `msm-xyz-service` sollte nur msm-bezogene Berechtigungen enthalten. Erweitern Sie die Berechtigungen nicht auf Funktionen, die nicht mit der Konfiguration von Communities oder Screens-Benutzenden in Zusammenhang stehen.

   * Die Aufgabe muss mit den Berechtigungen übereinstimmen:

      * Ein `foo-reader-service` sollte nur in der Lage sein, reguläre Elemente zu lesen. Gewähren Sie niemals Schreibberechtigungen
      * Es kann erwartet werden, dass ein `foo-writer-service` Schreiboperationen durchführt. Ihm sollten jedoch keine Berechtigungen zum Lesen/Ändern von Zugriffssteuerungsinhalten gewährt werden
      * Ein `foo-replicator-service` sollte über Berechtigungen für `crx:replicate` verfügen.

**Beispiele**

Beispiele für `configuration-reader-service`:

* Der Name gibt an, dass er sich auf Konfigurationen im Allgemeinen bezieht und nicht auf die Konfiguration einer bestimmten Funktion, z. B. die Konfiguration der DM-Integration. Dienstbenutzende, die speziell für die Lesekonfiguration einer solchen Integration vorgesehen sind, sollten lieber `dmconfig-reader-service` oder `s7config-reader-service` genannt werden

  >[!NOTE]
  >
  >In der Benennung sind keine Pfadinformationen enthalten. Konfigurationen wurden von `/etc` nach `/conf` verschoben.

* Das Aufgabenelement „task-element“ gibt an, dass Dienste, die mit diesen Benutzenden verknüpft sind, nur Lesevorgänge ausführen können.

Beispiele für `userproperties-copy-service`:

* Dienste, die an Dienstbenutzende gebunden sind, werden für Benutzer-/Gruppeneigenschaften wie Profile oder Voreinstellungen ausgeführt
* Es ist speziell darauf ausgerichtet, diese Informationen zu kopieren, im Gegensatz zu einem Namen wie `userproperties-writer-service`, der jede Art von Schreibvorgängen einschließen würde. Daher ist es möglich, dass die Berechtigungseinrichtung für diese Kopieaufgaben nur das Hinzufügen von Elementen an einem Ort und das Entfernen von Elementen an einem anderen Ort ermöglicht.

**Best Practices für die Einrichtung von Berechtigungen**

* Verwenden Sie immer die prinzipalbasierte Zugriffskontrolleinrichtung für Dienstbenutzende. Weitere Informationen finden Sie in den Beispielen unten:

   * Lassen Sie das Markieren von Dienstbenutzenden und ihren Berechtigungen als unveränderlichen Anwendungsinhalt in der Skyline zu
   * Erstellen von Pfaden und Baumstrukturen nicht erforderlich

* Nur Berechtigungen erteilen, niemals ablehnen
* Begrenzen von Berechtigungen

   * Gewähren Sie nur die erforderlichen Mindestberechtigungen.
   * Weitere Informationen finden Sie in der Dokumentation zum [Zuordnen von Berechtigungen zu Elementen](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoitems.html) und [Zuordnen von API-Aufrufen zu Berechtigungen](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoprivileges.html)
   * Erteilen Sie keine Berechtigung für `jcr:all`. Das ist höchstwahrscheinlich nicht der Mindestsatz.

* Reduzieren des Umfangs

   * Platzieren von Zugriffskontrollrichtlinien in funktionsspezifischen Unterstrukturen
   * Bei verteilten Elementen: Verwenden Sie Einschränkungen zur Begrenzung des Umfangs (siehe [die Dokumentation](https://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html) für die Liste der nativen Einschränkungen).

* Sicherstellen der Konsistenz

   * Sorgen Sie dafür, dass Berechtigungen mit der Entität und Aufgabe konsistent sind, die Sie im Dienstbenutzernamen verwendet haben
   * Vermeiden Sie das Hinzufügen von nicht verwandten Berechtigungen. Es wäre beispielsweise seltsam, einen `workflow-administration-service` zu haben und ihm Berechtigungen zum Ausführen von Benutzerverwaltungsvorgängen unter `/home/users/screens` oder zum Lesen von s7-config zu gewähren.

* Vollständigkeit

   * Vergewissern Sie sich, dass Ihr Dienst über alle Berechtigungen verfügt, die er zur Durchführung der Aufgaben benötigt, die er ausführen soll. Ihr Dienst muss auch in Kundenumgebungen vorkonfiguriert funktionieren.
   * Erwarten Sie nie, dass Kundinnen und Kunden die Berechtigungseinrichtung erweitern (Beispiel `/apps` unten)

* Vermeiden von doppelten Berechtigungen

   * Wiederverwenden von allgemeinen Dienstbenutzenden
   * Aggregieren Sie sie mit Ihren funktionsspezifischen Dienstbenutzenden, die die zusätzlich benötigten spezifischen Berechtigungen bereitstellen.

* Teilen Sie die Berechtigungseinrichtung nicht auf verschiedene Funktionen auf. Dies würde implizieren, dass Ihre Dienstbenutzenden nicht genau definiert sind oder zu viele verschiedene Aufgaben ausführen
* Platzieren Sie Dienstbenutzende nicht in Gruppen, da:

   * dadurch Implementierungsdetails von Dienstbenutzenden mit „öffentlichen“ Gruppen gemischt werden
   * Sie keine Kontrolle über Berechtigungsänderungen haben (Risiko von Regressionen und Berechtigungseskalationen).
   * Anmelde- und Bewertungsleistung
   * Funktioniert nicht mit prinzipalbasiertem ac-Setup

* Der Zugriff auf den Knoten „user-home“ (oder eine darin enthaltene Unterstruktur), der keinen vorhersehbaren Pfad hat, wird in Repo-Init durch die Verwendung von „home“ (`userId`) erreicht. Weitere Informationen finden Sie in der [Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html) zu Sling-Repo-Init.
* RTC: Erstellen Sie ein dediziertes RTC-Problem, wenn Sie die Berechtigungen von vorhandenen Dienstbenutzenden ändern, und stellen Sie sicher, dass Sie es vom Sicherheits-Team überprüfen lassen.

**Erstellung mit der Repository-Initialisierung**

Verwenden Sie immer `repo-init`, um Dienstbenutzende und ihre Berechtigungen zu definieren, und platzieren Sie beides im richtigen Abschnitt des Schnellstart-Funktionsmodells:

**Best Practices**

* Systematisches Verwenden von `repo-init` zum Erstellen der Dienstbenutzenden
* Systematische Angabe eines Zwischenpfads für jede Dienstbenutzererstellung
* Alle integrierten Dienstbenutzenden für AEM müssen sich unterhalb von `system/cq:services/internal` befinden
* Hängen Sie Folgendes zusätzlich an den relativen Zwischenpfad an, um die Dienstbenutzenden nach Funktionen zu gruppieren: `system/cq:services/internal/<your-feature>`
* Kundendefinierte Dienstbenutzende müssen sich unterhalb von `system/cq:services/<customer-intermediate-rel-path>` und niemals unterhalb der internen Struktur befinden
* Verwenden Sie **mit erzwungenem Pfad** anstelle von **mit Pfad**, wenn eine Benutzerin oder ein Benutzer bereits existiert und an den neuen Speicherort verschoben werden muss, der prinzipalbasierte Autorisierung unterstützt.

**Beispiele**

```
create service user my-new-feature-readcomment-service with path system/cq:services/internal/myfeature
set principal ACL for my-new-feature-readcomment-service
    allow rep:readProperties on /content/myFeature restriction(rep:itemNames,commentTitle,commentDate,commentTxt)
end
```

```
create service user my-existing-feature-addcomment-service with forced path system/cq:services/internal/myfeature
set principal ACL for my-existing-feature-addcomment-service
    allow jcr:addChildNodes,rep:addProperties on /content/myfeature restrictions(rep:glob,*/comments/*)
end
```

```
create service user myfeature-ims-service with path system/cq:services/internal/myfeature
set principal ACL for myfeature-ims-service
    allow jcr:read on home(myfeature-ims-service)
end
```

### Bereinigen von Dienstbenutzenden und Berechtigungen {#cleanup-service-users-and-permissions}

Mit dem folgenden Repo-Init-Befehl können Sie nicht verwendete Dienstbenutzende und deren Berechtigungen bereinigen:

```
# Remove the principal-based access control policy for principal my-feature-service
delete principal ACL for my-feature-service

# Remove all resource-based access control entries (ACEs) for principal my-feature-service
delete ACL for my-feature-service

# Disable the service user
disable service user my-feature-service : "My feature is no longer used"

# Remove the service user
delete service my-feature-service 
```

### Testen von Dienstbenutzenden {#testing-service-users}

Es ist wichtig, Server-seitige Tests für Dienstbenutzende und das Setup Ihrer Berechtigungen zu schreiben. Dadurch wird nicht nur überprüft, ob Ihr Setup wirklich funktioniert, sondern Sie können auch Regressionen und unbeabsichtigte Fehler erkennen, wenn Sie Zugriffskontrollinhalte oder Dienstbenutzende ändern.

Die `com.adobe.granite.testing.clients`-Bibliothek bietet eine Vielzahl von Dienstprogrammen, die das Schreiben von SSTs für Dienstbenutzende erleichtern.
