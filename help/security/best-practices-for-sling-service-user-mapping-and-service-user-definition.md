---
title: Best Practices für Sling Service-Benutzerzuordnung und Dienstbenutzerdefinition
description: Erfahren Sie mehr über die Best Practices für die Sling-Dienst-Benutzerzuordnung und die Service-Benutzerdefinition
source-git-commit: b6f7b6996b377ecfa372742ce1ad22139547ebdd
workflow-type: tm+mt
source-wordcount: '1884'
ht-degree: 0%

---


# Best Practices für Sling Service-Benutzerzuordnung und Dienstbenutzerdefinition {#best-practices-for-sling-service-user-mapping-and-service-user-definition}

## Dienstbenutzerzuordnung {#service-user-mapping}

Um eine Zuordnung von Ihrem Dienst zu den entsprechenden Systembenutzern hinzuzufügen, müssen Sie eine Werkskonfiguration für die `ServiceUserMapper` -Dienst. Um diese modulare Konfiguration beizubehalten, können solche Konfigurationen mithilfe des Sling-Mechanismus &quot;change&quot;bereitgestellt werden (siehe [SLING-3578](https://issues.apache.org/jira/browse/SLING-3578) für weitere Details). Die empfohlene Methode zur Installation solcher Konfigurationen mit Ihrem Bundle besteht darin, sie zum Schnellstart-Bereitstellungsmodell hinzuzufügen, wie im folgenden Beispiel beschrieben:

```
org.apache.sling.serviceusermapping.impl.ServiceUserMapperImpl.amended-my-mapping
    user.default=""
    user.mapping=[
        "com.adobe.cq.my-bundle:my-subservice\=[content-writer-service]",
        "com.adobe.cq.my-bundle:my-subservice-different-task\="[myfeature-configuration-writer-service,content-reader-service]"
    ]
```

### Zuordnungsformat {#mapping-format}

Seit AEM 6.4 wird das Mapping-Format wie folgt definiert:

>[!NOTE]
>
>Die `userName` ist veraltet und sollte nicht mehr verwendet werden.

```
bundleId [:subserviceName] = userName | [principalNames]   
```

`bundleId` und `subserviceName` den Dienst identifizieren, `userName/principalNames` den Dienstbenutzer identifizieren und `principalNames` ist eine kommagetrennte Liste.

Beachten Sie außerdem Folgendes: `principalNames` ist die Liste der Hauptnamen des Dienstbenutzers, die standardmäßig mit der ID übereinstimmen.


**Best Practice**

* Namen von Unterdiensten für verschiedene Aufgaben - wenn die Dienste Ihres Bundles verschiedene Aufgaben ausführen, wird empfohlen, die Identität der Dienste anzugeben. `subserviceNames` um sie nach Aufgaben zu gruppieren
* Wenn ein bestimmter Dienst verschiedene Vorgänge ausführt (z. B. das Lesen von Asset-Inhalten und Aktualisieren von Informationen unter einer Unterstruktur von `/var`), wird empfohlen, dies widerzuspiegeln, indem verschiedene Service-Prinzipale, die den einzelnen Vorgang widerspiegeln, wie z. B. die `dam-reader-service` mit Funktionen `assetreport-writer-service`
* Jeder Dienst ist idealerweise an einen sehr spezifischen und begrenzten Satz von Vorgängen gebunden.
* Das neue Format mit `[one,or,multiple,principalNames]` ist die empfohlene Methode zum Definieren von Dienstbenutzerzuordnungen ab AEM 6.4.

Nachstehend finden Sie eine Liste von Gründen für die Formatänderung und warum Adobe empfiehlt, das Format anstelle der Versionszuordnung nur für eine einzelne Benutzer-ID zu verwenden:

* Möglichkeit der Wiederverwendung von Servicebenutzern durch Kombination von Kundenbedürfnissen und allgemeinen Aufgaben
* Vermeiden von doppelten Berechtigungen
* Besseres Verständnis der effektiven Berechtigungen (und Aufgaben), die ein bestimmter Dienst tatsächlich ausführt
* Keine explizite Gruppenmitgliedschaft von Dienstbenutzern erforderlich. Dies kann bei Änderung der Gruppenberechtigungen zu problematischen Nebenwirkungen führen
* Leistungsverbesserungen und Skalierbarkeit

## Zuordnungsauflösung und Dienstanmeldung {#mapping-resolution-and-service-login}

### Auflösung der Dienstzuordnung {#service-mapping-resolution}

Die Abfolge von Aufrufen zur Auflösung des unten beschriebenen Service-Mappings:

1. Suche nach aktiven `principalNames` Zuordnung für die angegebene `bundleId` und `subserviceName`
1. `principalNames` -Zuordnung für `bundleId` und null `subserviceName`
1. `userName` -Zuordnung für `bundleId` und `subserviceName`
1. `userName` Zuordnung für `bundleId` und null `subserviceName`
1. Standardzuordnung
1. Standardbenutzer

### SlingRepository - Dienstanmeldung {#slingrepository-servicelogin}

Die Reihenfolge für den Erhalt eines Dienstes `Session/ResourceResolver` funktioniert wie folgt:

1. Abrufen von Hauptnamen von `ServiceUserMapper` => Repository-Anmeldung vor der Authentifizierung, wie unten beschrieben
1. Abrufen der Benutzer-ID von `ServiceUserMapper`
1. Suchen Sie nach veralteter 1ServiceUserConfiguration` für die aktuelle Benutzer-ID.
1. Standardmäßige Sling-Dienst-Anmeldung mit der Benutzer-ID (z. B. eine Sequenz von `createAdministrativeSession` und stellvertretend für die Dienstbenutzer-ID agieren)

Die neue Zuordnung mit den Prinzipalnamen führt zur folgenden vereinfachten Repository-Anmeldung:

* Die Gruppe von Prinzipalnamen wird als die effektiven Prinzipale(s) behandelt, die zum Ausfüllen der `Subject`
* Die Repository-Anmeldung kann somit vorauthentifiziert werden
* Keine Gruppenmitgliedsauflösung

  >[!NOTE]
  >
  >Alle erforderlichen Berechtigungen müssen für die Dienstbenutzer deklariert werden. &#39;everyone&#39; und andere Gruppenberechtigungen werden nicht mehr vererbt.

* Keine zusätzliche Administratoranmeldung für den Dienst-`Session/ResourceResolver` erstellt werden.

### Veraltete ServiceUserConfiguration {#deprecated-serviceUserConfiguration}

Beachten Sie, dass die Angabe eines einzelnen Benutzernamens in der Zuordnung dem vorhandenen entspricht. `ServiceUserConfiguration.simpleSubjectPopulation`. Mit dem neuen Format die Problemumgehung, die von der `ServiceUserConfiguration` kann direkt mit der Dienstbenutzerzuordnung angezeigt werden. Die `ServiceUserConfiguration` wurde daher für AEM nicht mehr unterstützt und alle bestehenden Verwendungen wurden ersetzt.

## Service-Benutzende {#service-users}

### Wiederverwenden vorhandener Dienstbenutzer {#reusing-existing-service-users}

Es wird empfohlen, vorhandene Dienstbenutzer erneut zu verwenden, wenn die folgenden Bedingungen erfüllt sind:

* Ihre Anforderungen stimmen mit dem Zweck des vorhandenen Dienstbenutzers überein
* Ihr Dienst erfordert eine gemeinsame Aufgabe, die von einem vorhandenen gemeinsamen Dienstbenutzer abgedeckt wird. In diesem Fall wird empfohlen, den Dienstbenutzer erneut zu verwenden, anstatt eine Duplizierung vorzunehmen
* Ihr Dienst erfordert eine bestimmte Aufgabe, die von einem vorhandenen Dienstbenutzer abgedeckt wird. Wenn Sie sich diesbezüglich nicht sicher sind, fragen Sie das Feature Team, dem es gehört.

Verwenden Sie keine vorhandenen Dienstbenutzer erneut, wenn:

* Sie müssen ihre Berechtigungen in einer Weise ändern, dass sie nicht funktionieren.
* Wenn Sie nur eine kleine Teilmenge der Berechtigungen benötigen, die sie bereitstellt, und sie einfach wiederverwenden würden, weil Ihre Funktion dadurch nicht funktioniert, weil sie eine echte Übereinstimmung darstellt
* Wenn der Name eine völlig andere Absicht anzeigt, als Sie es benötigen. Wenn Sie ihn aufgrund seiner Funktionsweise auswählen, kann es zu Problemen auf der Straße kommen, da das Feature-Team, das Inhaber eines bestimmten Dienstes ist, die Berechtigungen ändern und Ihre Funktion beschädigen kann.

### Erstellen eines Dienstbenutzers {#creating-a-service-user}

Nachdem Sie überprüft haben, ob kein bestehender Dienstbenutzer in AEM für Ihren Anwendungsfall anwendbar ist und die entsprechenden RTC-Probleme genehmigt wurden, können Sie fortfahren und den neuen Benutzer zum Standardinhalt hinzufügen. Idealerweise ist ein Mitglied des erweiterten Sicherheitsteams an der RTC-Abstimmung beteiligt. Stellen Sie daher sicher, dass Sie auch die entsprechenden Interessengruppen einbeziehen.

**Namenskonvention**

Das AEM-Sicherheitsteam hat die folgende Benennungskonvention definiert, damit Dienstbenutzer neue Dienstbenutzer konsistent benennen und ihre Lesbarkeit und Wartbarkeit verbessern können.

Ein Dienstbenutzername besteht aus 3 Elementen, die durch einen Bindestrich voneinander getrennt sind **&#39;-&#39;**:

1. Die logische Entität/Funktion, auf die die Dienstvorgänge abzielen (Pfade vermeiden, die sich ändern können)
1. Die Aufgabe, die die Dienste ausführen werden
1. Verfolgen **&#39;service&#39;** um aus der ID und dem Prinzipalnamen leicht erkennen zu können, dass der Benutzer ein Dienstbenutzer ist

**Best Practices**

* Vermischen Sie nicht verschiedene Entitäten/Funktionen. Aufspaltung nach einzelnen Dienstbenutzern und Aggregieren dieser in der Zuordnung, wenn Ihr Dienst unterschiedliche Anforderungen hat
* Beschränken Sie sich auf eine klar definierte Aufgabe pro Dienstbenutzer. Aufteilen, wenn Sie zu viele oder nicht verwandte Berechtigungen gewähren
* Zeit verbringen, um die tatsächliche Notwendigkeit Ihres Dienstes zu ermitteln
* Verbringen Sie Zeit mit der Suche nach einem guten, aussagekräftigen und selbsterklärenden Dienstbenutzernamen.
* Fragen Sie nach Feedback und Review: Entwickler, die mit Ihrer Funktion nicht vertraut sind, sollten in der Lage sein, Ihre Absicht zu lesen und zu verstehen. Sie könnten in Zukunft beauftragt werden, sie zu beheben oder zu warten.

Am Ende sollte der Dienstbenutzername Folgendes anzeigen:

* Verwendung und Wiederverwendbarkeit:

   * Sehr allgemein: `content-writer-service`. Sichere Wiederverwendung in der Aggregation, wenn Ihre Dienste auch in der Lage sein müssen, alle Inhalte zu lesen
   * Sehr spezifisch: `asset-linkshare-service`. Es ist nicht so sicher, die Assets wiederzuverwenden, es sei denn, Ihr Dienst nutzt tatsächlich die Freigabe von Assets per Link.

* Wie das Funktionssatz und die Einrichtung der Berechtigungen aussehen können:

   * Die logische Entität muss mit der Berechtigungseinrichtung übereinstimmen:

      * A `content-foo-service` sollten nur mit Vorgängen zu Inhalten verknüpft werden. Wenn Sie ihm Berechtigungen erteilen, mit anderen Entitäten wie Konfiguration oder Benutzern zu arbeiten, wäre dies falsch
      * Ein bestimmter Dienst, z. B. `personalization-foo-service` sollten auch mit bestimmten Berechtigungen versehen werden. Wenn Sie schließlich Berechtigungen für alle Inhalte erteilen, ist dies nicht mehr spezifisch. Spiegeln Sie dies im Namen oder verwenden Sie einen allgemeinen Benutzer in der Aggregation erneut.
      * Ein funktionsspezifischer Dienst wie `msm-xyz-service` sollte nur msm-bezogene Berechtigungen haben. Erweitern Sie die Berechtigungen nicht auf Funktionen, die nicht mit der Konfiguration von Communities oder Screens-Benutzern in Zusammenhang stehen.

   * Die Aufgabe muss mit den Berechtigungen übereinstimmen:

      * A `foo-reader-service` sollten nur reguläre Elemente lesen können. Schreibberechtigungen nie gewähren
      * A `foo-writer-service` kann erwartet werden, dass sie Schreibvorgänge ausführen. Es sollten jedoch keine Berechtigungen zum Lesen/Ändern von Zugriffssteuerungsinhalten gewährt werden
      * A `foo-replicator-service` kann erwartet werden, dass `crx:replicate` gewährt.

**Beispiele**

Beispiele für `configuration-reader-service`:

* Der Name gibt an, dass er sich auf Konfigurationen im Allgemeinen bezieht und nicht auf die Konfiguration einer bestimmten Funktion, z. B. die Konfiguration der DM-Integration. Ein Dienstbenutzer, der speziell für die Lesekonfiguration einer solchen Integration vorgesehen ist, sollte lieber benannt werden `dmconfig-reader-service` oder `s7config-reader-service`

  >[!NOTE]
  >
  >In der Benennung sind keine Pfadinformationen enthalten. Konfigurationen wurden verschoben von `/etc` nach `/conf`.

* Das task-element gibt an, dass Dienste, die an diesen Benutzer gebunden sind, nur Lesevorgänge ausführen.

Beispiele für `userproperties-copy-service`:

* Dienste, die an diesen Dienstbenutzer gebunden sind, werden für Benutzer-/Gruppeneigenschaften wie Profile oder Voreinstellungen ausgeführt
* Es ist speziell darauf ausgerichtet, diese Informationen zu kopieren, im Gegensatz zu einem Namen wie `userproperties-writer-service` , die jede Art von Schreibvorgängen einschließen würde. Daher ist es möglich, dass die Berechtigungseinrichtung für diese Kopieaufgaben nur das Hinzufügen von Elementen an einem Ort und das Entfernen von Elementen an einem anderen Ort ermöglicht.

**Best Practices für die Einrichtung von Berechtigungen**

* Verwenden Sie immer die Einrichtung der Prinzipal-basierten Zugriffssteuerung für Dienstbenutzer. Weitere Informationen finden Sie in den folgenden Beispielen:

   * Markierungsdienstbenutzer und ihre Berechtigungen als unveränderlichen Anwendungsinhalt zulassen
   * Erstellen von Pfaden und Baumstrukturen nicht erforderlich

* Nur Berechtigungen erteilen, niemals ablehnen
* Begrenzen von Berechtigungen

   * Gewähren Sie nur die erforderlichen Mindestberechtigungen.
   * Weitere Informationen finden Sie im [Zuordnen von Berechtigungen zu Elementen](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoitems.html) und [Zuordnen von API-Aufrufen zu Berechtigungen](https://jackrabbit.apache.org/oak/docs/security/privilege/mappingtoprivileges.html) Dokumentation
   * Erteilen Sie keine Berechtigung für `jcr:all`. Das ist höchstwahrscheinlich nicht die Mindestmenge.

* Umfang reduzieren

   * Platzieren von Zugriffskontrollrichtlinien in funktionsspezifischen Unterstrukturen
   * Bei verteilten Artikeln: Verwenden Sie Einschränkungen zur Begrenzung des Umfangs (siehe [die Dokumentation](http://jackrabbit.apache.org/oak/docs/security/authorization/restriction.html) für die Liste der nativen Einschränkungen).

* Konsistenz sicherstellen

   * Berechtigungen mit der Entität und Aufgabe konsistent machen, die Sie im Dienstbenutzernamen verwendet haben
   * Vermeiden Sie das Hinzufügen von Berechtigungen ohne Bezug. Es wäre beispielsweise seltsam, eine `workflow-administration-service` und gewähren ihr Berechtigungen zum Ausführen von Benutzerverwaltungsvorgängen unter `/home/users/screens` oder lesen Sie s7-config.

* Vollständigkeit

   * Vergewissern Sie sich, dass Ihr Dienst über alle Berechtigungen verfügt, die er zur Durchführung der Aufgaben benötigt, die er ausführen möchte. Ihr Dienst muss auch in Kundenumgebungen vorkonfiguriert funktionieren.
   * Erwarten Sie nie, dass Kunden die Berechtigungseinrichtung erweitern (z. B. unten) `/apps`)

* Vermeiden von doppelten Berechtigungen

   * Wiederverwenden von allgemeinen Dienstbenutzern
   * Aggregieren Sie sie mit Ihren funktionsspezifischen Dienstbenutzern, die die zusätzlich benötigten spezifischen Berechtigungen bereitstellen.

* Teilen Sie die Einrichtung der Berechtigungen nicht auf verschiedene Funktionen auf. Die Notwendigkeit zeigt, dass Ihr Dienstbenutzer nicht genau definiert ist oder zu viele verschiedene Aufgaben ausführt
* Platzieren Sie keine Service-Benutzer in Gruppen, da:

   * Es kombiniert Implementierungsdetails von Dienstbenutzern mit &quot;öffentlichen&quot;Gruppen
   * Sie haben keine Kontrolle über Berechtigungsänderungen (Risiko von Regressionen und Berechtigungseskalationen).
   * Anmelde- und Bewertungsleistung
   * Funktioniert nicht mit prinzipal-basiertem ac-Setup

* Der Zugriff auf den Benutzerstartknoten (oder einen darin enthaltenen Unterbaum), der keinen vorhersehbaren Pfad hat, wird in Repo Init mithilfe von home(`userId`). Siehe Sling-Repo-Init . [Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html) für Details.
* RTC: Erstellen Sie ein dediziertes RTC-Problem, wenn Sie die Berechtigungen eines vorhandenen Dienstbenutzers ändern und sicherstellen, dass Sie es vom Sicherheitsteam überprüfen lassen.

**Erstellung mit der Initialisierung des Repositorys**

Immer verwenden `repo-init` , um Dienstbenutzer und ihre Berechtigungen zu definieren und beide im richtigen Abschnitt des Schnellstart-Funktionsmodells zu platzieren:

**Best Practices**

* Immer verwenden `repo-init` zum Erstellen des Dienstbenutzers
* Geben Sie immer einen Zwischenpfad für die Erstellung eines Dienstbenutzers an
* Alle integrierten Dienstbenutzer für AEM müssen sich unter `system/cq:services/internal`
* Hängen Sie zusätzlich an den relativen Zwischenpfad an, um die Benutzer der Dienste nach Funktionen zu gruppieren: `system/cq:services/internal/<your-feature>`
* Kunden-definierte Service-Benutzer müssen sich unten befinden `system/cq:services/<customer-intermediate-rel-path>` und niemals unterhalb der internen Baumstruktur
* Verwendung **mit erzwungenem Pfad** anstelle von **mit Pfad** , wenn bereits ein Benutzer vorhanden war und an den neuen Speicherort verschoben werden muss, der die prinzipiell basierte Autorisierung unterstützt.

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

### Bereinigen von Dienstbenutzern und -berechtigungen {#cleanup-service-users-and-permissions}

Mit dem folgenden Befehl &quot;repo init&quot;können Sie nicht verwendete Dienstbenutzer und deren Berechtigungen bereinigen:

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

### Testen von Dienstbenutzern {#testing-service-users}

Es ist wichtig, serverseitige Tests für Dienstbenutzer und deren Einrichtung zu schreiben. Dies überprüft nicht nur, ob Ihr Setup wirklich funktioniert, sondern hilft Ihnen auch, Regressionen und unbeabsichtigte Fehler zu erkennen, wenn Sie den Inhalt oder die Service-Benutzer der Zugriffskontrolle ändern.

Die `com.adobe.granite.testing.clients` -Bibliothek bietet eine Vielzahl von Hilfsprogrammen, die das Schreiben von SSTs für Service-Benutzer erleichtern.





