---
title: Bereitstellen für AEM as a Cloud Service
description: 'Bereitstellen für AEM as a Cloud Service '
feature: Bereitstellen
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
translation-type: tm+mt
source-git-commit: 9ff68805d4deabaf637cee9ab81ba9b366a8e762
workflow-type: tm+mt
source-wordcount: '3266'
ht-degree: 96%

---

# Bereitstellen in AEM as a Cloud Service {#deploying-to-aem-as-a-cloud-service}

## Einführung {#introduction}

Die Grundlagen der Code-Entwicklung in AEM as a Cloud Service ähneln denen von AEM On-Premise- und Managed Services-Lösungen. Entwickler schreiben Code und testen ihn lokal, bevor sie ihn an Remote-AEM as a Cloud Service-Umgebungen pushen. Dafür wird Cloud Manager benötigt, das ein optionales Tool zur Inhaltsbereitstellung für Managed Services war. Dies ist nun das einzige Verfahren zur Implementierung von Code in AEM as a Cloud Service-Umgebungen.

Die Aktualisierung der [AEM-Version](/help/implementing/deploying/aem-version-updates.md) ist stets ein separates Implementierungsereignis, das nicht mit dem Pushen von [anwenderspezifischem Code](#customer-releases) verbunden ist. Anders gesagt: Bei Freigabe von anwenderspezifischem Code sollte mit jener AEM-Version getestet werden, die sich in der Produktion befindet, da der Code auf dieser Version bereitgestellt wird. Aktualisierungen der AEM-Version, die danach stattfinden und häufiger vorkommen, werden automatisch angewendet. Sie sollen abwärtskompatibel mit dem bereits bereitgestellten anwenderpezifischen Code sein.

In diesem Dokument wird beschrieben, wie Entwickler ihr Vorgehen anpassen sollten, um sowohl mit Aktualisierungen der AEM as a Cloud Service-Version als auch mit benutzerspezifischen Aktualisierungen zu arbeiten.

>[!NOTE]
>Kunden mit vorhandener Code-Basis wird empfohlen, die in der [AEM-Dokumentation](https://docs.adobe.com/help/de-DE/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html) beschriebene Repository-Umstrukturierung ausführen.

## Benutzerspezifische Versionen {#customer-releases}

### Kodierung mit der richtigen AEM-Version {#coding-against-the-right-aem-version}

Bei früheren AEM-Lösungen änderte sich die aktuelle AEM-Version selten (etwa 1-mal jährlich mit vierteljährlichen Service Packs); Kunden aktualisierten die Produktionsinstanzen im eigenen Tempo auf den neuesten Schnellstart, indem sie auf das API-JAR verwiesen. AEM as a Cloud Service-Programme jedoch werden häufiger automatisch auf die neueste Version von AEM aktualisiert. Daher sollte anwenderpezifischer Code für interne Freigaben für die neueste AEM-Version erstellt werden.

Wie bei vorhandenen Nicht-Cloud-AEM-Versionen wird eine lokale Offline-Entwicklung unterstützt, die auf einem bestimmten Schnellstart basiert. In den meisten Fällen ist dies das bevorzugte Debugging-Tool.

>[!NOTE]
>Beim Verhalten der Anwendung gibt es geringfügige Unterschiede zwischen einem lokalen Computer und der Adobe Cloud. Diese architektonischen Unterschiede müssen bei der lokalen Entwicklung berücksichtigt werden und können bei Implementierung in der Cloud-Infrastruktur ggf. zu einem anderen Verhalten führen. Darum ist es wichtig, in Entwicklungs- und Staging-Umgebungen umfassende Tests durchzuführen, bevor neuer benutzerspezifischer Code in die Produktionsumgebung eingeführt wird.

Um benutzerdefinierten Code für eine interne Version zu entwickeln, sollte die entsprechende Version des [AEM as a Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) heruntergeladen und installiert werden. Weitere Informationen zur Verwendung der AEM as a Cloud Service-Dispatcher-Tools finden Sie auf [dieser Seite](/help/implementing/dispatcher/disp-overview.md).

Das folgende Video bietet einen Überblick über die Implementierung von Code für AEM as a Cloud Service:

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

>[!NOTE]
>Kunden mit vorhandener Code-Basis wird empfohlen, die in der [AEM-Dokumentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html) beschriebene Repository-Umstrukturierung ausführen.

## Bereitstellen von Inhaltspaketen über Cloud Manager und Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Implementierungen über Cloud Manager {#deployments-via-cloud-manager}

Kunden können benutzerspezifischen Code in Cloud-Umgebungen über Cloud Manager bereitstellen. Beachten Sie, dass Cloud Manager lokal assemblierte Inhaltspakete nach dem Sling-Funktionsmodell in ein Artefakt umwandelt. So wird eine AEM as a Cloud Service-Anwendung beschrieben, wenn sie in einer Cloud-Umgebung ausgeführt wird. Wenn Sie also die Pakete im Package Manager für Cloud-Umgebungen betrachten, enthält der Name „cp2fm“ und wurden alle Metadaten der transformierten Pakete entfernt. Mit ihnen kann nicht interagiert werden; d. h. sie lassen nicht herunterladen, replizieren oder öffnen. Eine ausführliche Dokumentation zum Konvertierer finden Sie [hier](https://github.com/apache/sling-org-apache-sling-feature-cpconverter).

Inhaltspakete, die für AEM als Cloud Service-Anwendungen geschrieben wurden, müssen eine saubere Trennung zwischen unveränderbarem und veränderbarem Inhalt aufweisen. Cloud Manager installiert dann nur den veränderbaren Inhalt und gibt eine Meldung wie die folgende aus:

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

Im Rest dieses Abschnitts werden die Komposition und Implikationen unveränderlicher und veränderlicher Pakete beschrieben.

### Unveränderliche Inhaltspakete {#immutabe-content-packages}

Sämtlicher Inhalt und Code, der im unveränderlichen Repository persistent ist, muss in Git eingecheckt und mit Cloud Manager bereitgestellt werden. Anders gesagt: Im Gegensatz zu aktuellen AEM-Lösungen wird Code niemals direkt in einer laufenden AEM-Instanz bereitgestellt. Dadurch wird sichergestellt, dass der Code, der für eine bestimmte Version in beliebigen Cloud-Umgebungen ausgeführt wird, identisch ist. So wird das Risiko unbeabsichtigter Code-Varianten in der Produktion eliminiert. Beispiel: Die OSGi-Konfiguration sollte der Quell-Code-Verwaltung übergeben und nicht zur Laufzeit über den Konfigurations-Manager der AEM-Web-Konsole verwaltet werden.

Da Anwendungsänderungen aufgrund des Blue-Green-Implementierungsmusters durch einen Schalter aktiviert werden, dürfen sie nicht von Änderungen im veränderlichen Repository abhängig sein, mit Ausnahme von Service-Benutzern, ihren ACLs, Knotentypen und Änderungen der Indexdefinition.

Kunden mit vorhandener Code-Basis müssen die in der AEM-Dokumentation beschriebene Repository-Umstrukturierung durchführen, um dafür zu sorgen, dass zuvor unter „/etc“ befindliche Inhalte an den richtigen Speicherort verschoben werden.

Für diese Codepakete gelten einige zusätzliche Einschränkungen, z. B. werden [Installationshoke](http://jackrabbit.apache.org/filevault/installhooks.html) nicht unterstützt.

## OSGi-Konfiguration {#osgi-configuration}

Wie bereits erwähnt, sollte die OSGi-Konfiguration an die Quell-Code-Verwaltung übermittelt werden und nicht über die Web-Konsole. Zu geeigneten Verfahren gehören:

* Vornehmen der erforderlichen Änderungen in der lokalen AEM-Umgebung des Entwicklers mit dem Konfigurations-Manager der AEM-Web-Konsole und anschließendes Exportieren der Ergebnisse in das AEM-Projekt im lokalen Dateisystem;
* manuelles Erstellen der OSGi-Konfiguration im AEM-Projekt im lokalen Dateisystem und anschließendes Verweisen auf die Eigenschaftsnamen durch den Konfigurations-Manager der AEM-Web-Konsole.

Weitere Informationen zur OSGi-Konfiguration finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).

## Veränderlicher Inhalt {#mutable-content}

Manchmal kann es nützlich sein, Inhaltsänderungen in der Quell-Code-Verwaltung vorzubereiten, damit sie von Cloud Manager bereitgestellt werden können, sobald eine Umgebung aktualisiert wird. So kann es beispielsweise sinnvoll sein, bestimmte Stammordnerstrukturen zu testen oder Änderungen in editierbaren Vorlagen anzuordnen, um darin Richtlinien für Komponenten zu aktivieren, die bei der Anwendungsimplementierung aktualisiert wurden.

Es gibt zwei Strategien zur Beschreibung von Inhalten, die von Cloud Manager im veränderlichen Repository bereitgestellt werden: veränderliche Inhaltspakete und repoinit-Anweisungen.

### Veränderliche Inhaltspakete {#mutable-content-packages}

Inhalte wie Ordnerpfadhierarchien, Service-Benutzer und Zugangssteuerungen (ACLs) werden in der Regel in ein AEM-Projekt übertragen, das auf Maven-Archetypen basiert. Zu den Methoden gehören das Exportieren aus AEM oder das direkte Schreiben als XML. Bei der Erstellung und Implementierung packt Cloud Manager das resultierende veränderliche Inhaltspaket. Der veränderbare Inhalt wird in der Implementierungsphase in der Pipeline zu drei verschiedenen Zeitpunkten installiert:

Vor dem Start der neuen Version der Anwendung:

* Indexdefinitionen (hinzufügen, ändern, entfernen)

Beim Start der neuen Version der Anwendung, aber vor der Umstellung:

* Service-Benutzer (hinzufügen)
* ACLs für Service-Benutzer (hinzufügen)
* Knotentypen (hinzufügen)

Nach der Umstellung auf die neue Anwendungsversion:

* Alle anderen Inhalte, über Jackrabbit Vault definierbar Beispiel:
   * Ordner (hinzufügen, ändern, entfernen)
   * Bearbeitbare Vorlagen (hinzufügen, ändern, entfernen)
   * Kontextsensible Konfiguration (alles unter `/conf`) (hinzufügen, ändern, entfernen)
   * Skripte (Pakete können in verschiedenen Phasen der Paketinstallation Installationshaken auslösen). Informationen zu Installationshaken, die Benutzern die Ausführung erlauben, finden Sie in der [Jackrabbit filevault-Dokumentation](http://jackrabbit.incubator.apache.org/filevault/installhooks.html).

Die Installation veränderlicher Inhalte in Autoren- oder Veröffentlichungsinstanzen lässt sich einschränken, indem Sie Pakete unter `/apps` in einen „install.author“- oder „install.publish“-Ordner einbetten. Die Umstrukturierung zur Berücksichtigung dieser Trennung erfolgte in AEM 6.5 und Einzelheiten zur empfohlenen Projektumstrukturierung finden Sie in der [AEM 6.5 Dokumentation.](https://docs.adobe.com/content/help/de-DE/experience-manager-65/deploying/restructuring/repository-restructuring.html)

>[!NOTE]
>Inhaltspakete werden für alle Umgebungstypen (dev, stage, prod) bereitgestellt. Die Implementierung kann nicht auf eine bestimmte Umgebung beschränkt werden. Diese Einschränkung dient dazu, einen Testlauf der automatischen Ausführung zu ermöglichen. Umgebungsspezifische Inhalte müssen manuell über Package Manager installiert werden.

Außerdem gibt es kein Verfahren, um Änderungen durch veränderliche Inhaltspakete nach deren Anwendung zurückzunehmen. Wenn Kunden ein Problem entdecken, können sie es in ihrer nächsten Code-Version beheben oder – als letzte Möglichkeit – das ganze System auf einen Zeitpunkt vor der Implementierung zurücksetzen.

Alle enthaltenen Pakete von Drittanbietern müssen als kompatibel mit AEM as a Cloud Service validiert werden. Andernfalls führt ihre Einbeziehung zu einem Implementierungsfehler.

Wie oben erwähnt, sollten Kunden mit vorhandenen Code-Basen der Repository-Restrukturierung entsprechen, die durch die 6.5-Repository-Änderungen erforderlich ist, die in der [AEM 6.5-Dokumentation beschrieben werden.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html?lang=de)

## Repoinit {#repoinit}

In folgenden Fällen ist es vorzuziehen, in den OSGi-Werkseinstellungen manuell explizite `repoinit`-Anweisungen für die Inhaltserstellung zu kodieren:

* Service-Benutzer erstellen/löschen/deaktivieren
* Gruppen erstellen/löschen
* Benutzer erstellen/löschen
* ACLs hinzufügen

   >[!NOTE]
   >
   >Eine Definition von ACLs erfordert, dass die Knotenstrukturen bereits vorhanden sind. Daher können vorherige Anweisungen zur Pfaderstellung erforderlich sein.

* Pfad hinzufügen (z. B. für Stammordnerstrukturen)
* CNDs hinzufügen (Definitionen für Knotentypen)

Aufgrund der folgenden Vorteile ist bei diesen Anwendungsfällen für die Inhaltsänderung bevorzugt „repoinit“ zu verwenden:

* Repoinit erstellt Ressourcen beim Start, sodass Logik die Existenz dieser Ressourcen als selbstverständlich betrachten kann. Beim Ansatz mit veränderlichen Inhaltspaketen werden Ressourcen nach dem Start erstellt, sodass Anwendungs-Code, der auf sie angewiesen ist, fehlschlagen kann.
* Repoinit ist ein relativ sicherer Anweisungssatz, da Sie explizit steuern, welche Aktion vorgenommen werden soll. Zudem werden nur additive Vorgänge unterstützt, mit Ausnahme einiger sicherheitsrelevanter Fälle, in denen Benutzer, Service-Benutzer und Gruppen entfernt werden können. Dagegen ist eine Entfernung beim Ansatz mit variablen Inhaltspaketen explizit. Wenn Sie einen Filter definieren, werden alle von einem Filter derzeit erfassten Elemente gelöscht. Dennoch ist Vorsicht geboten, da es bei jedem Inhalt Szenarien geben kann, in denen die Existenz neuer Inhalte das Verhalten der Anwendung verändert.
* Repoinit sorgt für schnelle und atomische Operationen. Veränderliche Inhaltspakete hingegen können stark von der Leistung der Strukturen abhängen, die von einem Filter abgedeckt werden. Auch wenn Sie nur einen Knoten aktualisieren, wird ggf. ein Schnappschuss einer großen Baumstruktur erstellt.
* Repoinit-Anweisungen können in einer lokalen Entwicklungsumgebung zur Laufzeit überprüft werden, da sie bei der Registrierung der OSGi-Konfiguration ausgeführt werden.
* Repoinit-Anweisungen sind atomisch und explizit und werden übersprungen, wenn der Status bereits übereinstimmt.

Wenn Cloud Manager die Anwendung bereitstellt, werden diese Anweisungen unabhängig von der Installation jeglicher Inhaltspakete ausgeführt.

Gehen Sie wie folgt vor, um weitere repoinit-Anweisungen zu erstellen:

1. Fügen Sie die OSGi-Konfiguration für werksmäßige PID `org.apache.sling.jcr.repoinit.RepositoryInitializer` in einem Konfigurationsordner des Projekts hinzu. Verwenden Sie einen beschreibenden Namen für die Konfiguration wie **org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure**.
1. Fügen Sie der Skripteigenschaft von „config“ repoinit-Anweisungen hinzu. Syntax und Optionen werden in der [Sling-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html) beschrieben. Beachten Sie, dass vor untergeordneten Ordnern explizit ein übergeordneter Ordner erstellt werden muss. Beispielsweise ist eine explizite Erstellung von `/content` vor `/content/myfolder` und vor `/content/myfolder/mysubfolder` erforderlich. Bei ACLs, die für untergeordnete Strukturen festgelegt werden, wird empfohlen, diese auf einer höheren Ebene festzulegen und eine `rep:glob`-Einschränkung zu nutzen.  Beispiel `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. Validieren Sie zur Laufzeit in der lokalen Entwicklungsumgebung.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Bei ACLs, die für Knoten unter `/apps` oder `/libs` definiert sind, beginnt die repoinit-Ausführung in einem leeren Repository. Die Pakete werden nach dem „repoinit“ installiert. Das bedeutet, dass Anweisungen sich auf nichts verlassen können, was in den Paketen definiert ist, sondern Vorbedingungen wie die übergeordneten Strukturen darunter definieren müssen.

>[!TIP]
>
>Bei ACLs ist die Erstellung von tiefen Strukturen ggf. aufwendig. Daher ist es vernünftiger, eine ACL auf einer höheren Ebene zu definieren und durch eine rep:glob-Beschränkung zu beschränken, wo sie handeln soll.

Weitere Informationen zu „repoinit“ finden Sie in der [Sling-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html).

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Package Manager-„one offs“ für Pakete mit veränderlichen Inhalten {#package-manager-oneoffs-for-mutable-content-packages}

Es gibt Anwendungsfälle, in denen ein Inhaltspaket als „one off“ (einmalig) installiert werden sollte. Möglicherweise importieren Sie bestimmte Inhalte aus der Produktions- in die Staging-Umgebung, um ein Problem in der Produktion zu debuggen. Für solche Szenarien kann Package Manager in AEM as a Cloud Service-Umgebungen verwendet werden.

Da Package Manager auf einem Laufzeitkonzept basiert, ist es unmöglich, Inhalte oder Code im unveränderlichen Repository zu installieren. Daher dürfen diese Inhaltspakete nur aus veränderlichen Inhalten bestehen (hauptsächlich `/content` oder `/conf`). Wenn das Inhaltspaket gemischte Inhalte enthält (sowohl veränderliche als auch unveränderliche Inhalte), wird nur der veränderliche Inhalt installiert.

Sämtliche über Cloud Manager installierten Inhaltspakete (sowohl veränderliche als auch unveränderliche) werden in der Benutzeroberfläche von AEM Package Manager mit einem eingefrorenen Status angezeigt. Solche Pakete können weder neu installiert, neu erstellt noch heruntergeladen werden und werden mit dem Suffix **cp2fm** aufgeführt, was darauf hinweist, dass ihre Installation von Cloud Manager vorgenommen wurde.

### Einschließen von Drittanbieterpaketen {#including-third-party}

Es ist üblich, dass Kunden vorgefertigte Pakete aus Drittanbieterquellen (zum Beispiel von Software-Anbietern wie Übersetzungspartnern von Adobe) einbeziehen. Es wird empfohlen, diese Pakete in einem Remote-Repository zu hosten und in `pom.xml` auf sie zu verweisen. Dies ist für öffentliche Repositorys und auch für private Repositorys mit Kennwortschutz möglich, wie unter [Unterstützung für kennwortgeschütztes Maven-Repository](/help/onboarding/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories) beschrieben.

Wenn das Speichern des Pakets in einem Remote-Repository nicht möglich ist, können Kunden es in einem lokalen, Dateisystem-basierten Maven-Repository platzieren, das im Rahmen des Projekts an SCM übermittelt und auf das bei Bedarf verwiesen wird. Das Repository würde in den nachfolgend dargestellten Projekt-POMs deklariert:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Alle enthaltenen Pakete von Drittanbietern müssen den in diesem Artikel beschriebenen Richtlinien zur Kodierung und Verpackung für AEM as a Cloud Service entsprechen. Andernfalls wird ihre Einbeziehung zu einem Implementierungsfehler führen.

Das folgende Maven-POM-XML-Fragment zeigt, wie Pakete von Drittanbietern über das „Container“-Paket des Projekts, in der Regel **&#39;all&#39;** genannt, über die Maven-Plug-in-Konfiguration **filevault-package-maven-plugin** eingebettet werden können.

```
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <subPackages>
           
          <!-- Include the application's ui.apps and ui.content packages -->
          ...
 
          <!-- Include any other extra packages such as AEM WCM Core Components -->
          <!-- Set the version for all dependencies, including 3rd party packages, in the project's Reactor POM -->
          <subPackage>
              <groupId>com.adobe.cq</groupId>
              <artifactId>core.wcm.components.all</artifactId>
              <filter>true</filter>
          </subPackage>
 
 
          <subPackage>
              <groupId>com.3rdparty.groupId</groupId>
              <artifactId>core.3rdparty.artifactId</artifactId>
              <filter>true</filter>
          </subPackage>
      <subPackages>
  </configuration>
</plugin>
...
```

## Funktionsweise von rollierenden Implementierungen {#how-rolling-deployments-work}

Genauso wie AEM-Aktualisierungen werden benutzerspezifische Versionen mithilfe einer rollierenden Implementierungsstrategie bereitgestellt, um unter den richtigen Bedingungen Ausfallzeiten im Autoren-Cluster zu verhindern. Die allgemeine Reihenfolge der Ereignisse ist wie unten beschrieben, wobei **Blue** die alte Version des benutzerspezifischen Codes und **Green** die neue Version darstellt. Sowohl „Blue“ als auch „Green“ verwenden dieselbe Version von AEM-Code.

* Die blaue Version ist aktiv; für die grüne Version wird ein Freigabekandidat erstellt und verfügbar gemacht.
* Wenn neue oder aktualisierte Indexdefinitionen vorhanden sind, werden die entsprechenden Indizes verarbeitet. Beachten Sie, dass bei der blauen Implementierung immer die alten Indizes verwendet werden, während bei der grünen Implementierung stets die neuen Indizes verwendet werden.
* „Green“ startet, während „Blue“ weiter bereitstellt.
* „Blue“ wird ausgeführt und stellt bereit, während „Green“ mit Konsistenzprüfungen auf ihre Bereitschaft überprüft wird.
* Grüne Knoten, die bereit zur Aufnahme von Traffic sind und blaue Knoten ersetzen, die heruntergefahren werden.
* Nach und nach werden blaue Knoten durch grüne ersetzt, bis nur noch grüne Knoten übrig bleiben, wodurch die Implementierung abgeschlossen ist.
* Alle neuen oder geänderten veränderlichen Inhalte werden bereitgestellt.

## Indizes {#indexes}

Neue oder geänderte Indizes führen zu einem zusätzlichen Indizierungs- oder Neuindizierungsschritt, bevor die neue (grüne) Version Traffic annehmen kann. Details zur Indexverwaltung in AEM as a Cloud Service finden Sie in [diesem Artikel](/help/operations/indexing.md). Sie können den Status des Indizierungsauftrags auf der Build-Seite von Cloud Manager überprüfen und erhalten eine Benachrichtigung, sobald die neue Version bereit zur Aufnahme von Traffic ist.

>[!NOTE]
>
>Die Dauer einer rollierenden Implementierung hängt von der Größe des Indexes ab, da die grüne Version Traffic erst annehmen kann, nachdem der neue Index generiert wurde.

Derzeit funktioniert AEM as a Cloud Service nicht mit Indexverwaltungs-Tools wie dem ACS Commons Ensure Oak Index-Tool.

## Replikation {#replication}

Der Veröffentlichungsmechanismus ist rückwärtskompatibel mit den [AEM Replication Java-APIs](https://helpx.adobe.com/de/experience-manager/6-3/sites/developing/using/reference-materials/diff-previous/changes/com.day.cq.replication.Replicator.html).

Um mit Replikation und dem Cloud-fähigen AEM-Schnellstart entwickeln und testen zu können, müssen die klassischen Replikationsfunktionen in einem Author/Publish-Setup verwendet werden. Wenn der Einstiegspunkt der Benutzeroberfläche in AEM Author für die Cloud entfernt wurde, würden Benutzer zur Konfiguration `http://localhost:4502/etc/replication` aufrufen.

## Rückwärtskompatibler Code für rollierende Implementierungen {#backwards-compatible-code-for-rolling-deployments}

Wie oben erläutert, beinhaltet die kontinuierliche Implementierungsstrategie von AEM as a Cloud Service, dass sich sowohl die alten als auch die neuen Versionen gleichzeitig ausführen lassen. Seien Sie daher vorsichtig bei Code-Änderungen, die nicht rückwärtskompatibel mit der alten, weiter verwendeten AEM-Version sind.

Darüber hinaus sollte die alte Version auf ihre Kompatibilität mit allen neuen Strukturen veränderlicher Inhalte getestet werden, die von der neuen Version im Fall eines Rollbacks angewendet werden, da veränderliche Inhalte nicht entfernt werden.

### Service-Benutzer- und ACL-Änderungen {#service-users-and-acl-changes}

Das Ändern von Service-Benutzern oder ACLs, die für den Zugriff auf Inhalt oder Code erforderlich sind, kann in den älteren AEM-Versionen zu Fehlern führen, sodass mit veralteten Service-Benutzern auf diesen Inhalt oder Code zugegriffen wird. Darum wird empfohlen, Änderungen auf mindestens zwei Versionen zu verteilen, wobei die erste Version als Brücke fungiert, bevor die folgende Version bereinigt wird.

### Indexänderungen {#index-changes}

Wenn Änderungen an Indizes vorgenommen werden, muss die blaue Version ihre Indizes bis zum Ende weiter verwenden, während die grüne Version ihre eigenen geänderten Indizes nutzt. Der Entwickler sollte die [in diesem Artikel](/help/operations/indexing.md) beschriebenen Methoden zur Indexverwaltung befolgen.

### Konservative Kodierung für Rollbacks {#conservative-coding-for-rollbacks}

Wenn nach der Implementierung ein Fehler gemeldet oder erkannt wird, ist möglicherweise ein Rollback zur blauen Version erforderlich. Es ist ratsam, dass der Blue-Code mit allen neuen Strukturen, die von der Green-Version erstellt werden, kompatibel ist, da die neuen Strukturen (beliebige veränderliche Inhalte) nicht zurückgesetzt werden. Wenn der alte Code nicht kompatibel ist, müssen in späteren benutzerspezifischen Versionen Korrekturen vorgenommen werden.

## Ausführungsmodi {#runmodes}

In bestehenden AEM-Lösungen haben Kunden die Möglichkeit, Instanzen mit beliebigen Ausführungsmodi auszuführen und OSGi-Konfigurationen anzuwenden oder OSGi-Pakete in diesen spezifischen Instanzen zu installieren. Zu den definierten Ausführungsmodi gehören normalerweise der *Service* (author und publish) sowie die Umgebung (dev, stage, prod).

AEM as a Cloud Service hingegen ist eigenwilliger bezüglich der Frage, welche Ausführungsmodi verfügbar sind und wie ihnen OSGi-Pakete und OSGi-Konfigurationen zugeordnet werden können:

* Die Ausführungsmodi der OSGi-Konfiguration müssen für die Umgebung auf dev, stage, prod bzw. für den Service auf author, publish verweisen. Es wird eine Kombination aus `<service>.<environment_type>` unterstützt, wobei diese genau in dieser bestimmten Reihenfolge verwendet werden müssen (z. B. `author.dev` oder `publish.prod`). Auf die OSGi-Token sollte direkt im Code verwiesen werden, da die `getRunModes`-Methode zur Laufzeit den `environment_type` nicht mehr enthält. Weitere Informationen finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).
* Die Ausführungsmodi von OSGi-Bundles sind auf den Service (author, publish) beschränkt. OSGi-Pakete für den Pre-Run-Modus sollten im Inhaltspaket unter `install/author` oder `install/publish` installiert werden.

Wie bei vorhandenen AEM-Lösungen gibt es keine Möglichkeit, Ausführungsmodi zu verwenden, um Inhalte nur für bestimmte Umgebungen oder Services zu installieren. Wenn eine Entwicklungsumgebung mit Daten oder HTML getestet werden soll, die sich nicht in der Staging- oder Produktionsumgebung befinden, kann Package Manager verwendet werden.

Die folgenden Runmode-Konfigurationen werden unterstützt:

* **config** (*der Standard, gilt für alle AEM-Services*)
* **config.author** (*gilt für alle AEM Author-Services*)
* **config.author.dev** (*gilt für den AEM Dev Author-Service*)
* **config.author.stage** (*gilt für den AEM Staging Author-Service*)
* **config.author.prod** (*gilt für den AEM Production Author-Service*)
* **config.publish** (*gilt für den AEM Publish-Service*)
* **config.publish.dev** (*gilt für den AEM Dev Publish-Service*)
* **config.publish.stage** (*gilt für den AEM Staging Publish-Service*)
* **config.publish.prod** (*gilt für den AEM Production Publish-Service*)
* **config.dev** (*gilt für AEM Dev-Service)
* **config.stage** (*gilt für AEM Staging-Service)
* **config.prod** (*gilt für AEM Production-Service)

Es wird jene OSGi-Konfiguration verwendet, die über die meisten passenden Ausführungsmodi verfügt.

Bei der lokalen Entwicklung kann ein Runmode-Startparameter übergeben werden, um anzugeben, welche Runmode-OSGi-Konfiguration verwendet werden soll.

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Konfiguration von Wartungsaufgaben in der Quell-Code-Verwaltung {#maintenance-tasks-configuration-in-source-control}

Die Konfiguration von Wartungsaufgaben muss in der Quell-Code-Verwaltung persistiert werden, da der Bildschirm **Tools > Vorgänge** in Cloud-Umgebungen nicht mehr verfügbar ist. Das hat den Vorteil, dass Veränderungen vorsätzlich persistiert werden, anstatt reaktiv angewandt und ggf. vergessen zu werden. Weitere Informationen finden Sie im [Artikel zur Wartungsaufgabe](/help/operations/maintenance.md).
