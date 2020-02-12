---
title: Bereitstellen auf AEM als Cloud-Dienst
description: 'Bereitstellen auf AEM als Cloud-Dienst '
translation-type: tm+mt
source-git-commit: 6bf4d9d106a35ead10be235237986a60f2bf1148

---


# Bereitstellen auf AEM als Cloud-Dienst {#deploying-to-aem-as-a-cloud-service}

## Einführung {#introduction}

Die Grundlagen der Codeentwicklung sind in AEM als Cloud-Dienst im Vergleich zu den AEM On Premise- und Managed Services-Lösungen ähnlich. Entwickler schreiben Code und testen ihn lokal, der dann als Cloud-Dienstumgebungen an AEM gesendet wird. Cloud Manager, ein optionales Werkzeug zur Inhaltsbereitstellung für Managed Services, ist erforderlich. Dies ist jetzt der einzige Mechanismus zur Bereitstellung von Code in AEM als Cloud-Dienstumgebungen.

Die Aktualisierung der AEM-Version ist immer ein separates Bereitstellungsereignis, das nicht das Verschieben von benutzerdefiniertem Code ermöglicht. Andernfalls sollten Versionen von benutzerspezifischem Code mit der AEM-Version getestet werden, die in Produktion ist, da diese Version zusätzlich bereitgestellt wird. Updates der AEM-Version, die danach erfolgen und die im Vergleich zu den heutigen Managed Services häufig auftreten, werden automatisch angewendet. Sie sollen abwärtskompatibel mit dem bereits bereitgestellten Kundencode sein.

In diesem Dokument wird beschrieben, wie Entwickler ihre Vorgehensweisen so anpassen sollten, dass sie sowohl mit AEM als Updates für die Version des Cloud-Dienstes als auch mit Updates für Kunden arbeiten.

>[!NOTE]
>Es wird empfohlen, dass Kunden mit vorhandenen Code-Datenbanken die in der [AEM-Dokumentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html)beschriebene Repository-Restrukturierung durchführen.


## Aktualisierungen der AEM-Version {#version-updates}

Es ist wichtig zu verstehen, dass AEM häufig aktualisiert wird, potenziell so oft wie einmal am Tag, und sich auf Fehlerbehebungen und Leistungsverbesserungen konzentriert. Die Aktualisierung erfolgt transparent und ohne Ausfallzeiten. Das Update soll abwärtskompatibel sein, d. h., Sie müssen keinen benutzerdefinierten Code ändern. Tatsächlich sind AEM-Updates unabhängige Ereignisse von der Bereitstellung von Kundencode. Das AEM-Update wird zusätzlich zu Ihrem letzten erfolgreichen Code-Push bereitgestellt, was bedeutet, dass alle seit dem letzten Push-to-Production-Vorgang vorgenommenen Änderungen nicht bereitgestellt werden.

>[!NOTE]
>
> Wenn benutzerdefinierter Code in die Staging-Phase verschoben und dann von Ihnen abgelehnt wurde, werden diese Änderungen beim nächsten AEM-Update entfernt, um das git-Tag der letzten erfolgreichen Kunden-Version bis zur Produktion widerzuspiegeln.

In regelmäßigen Abständen wird eine Version der Funktionen veröffentlicht, die sich auf Funktionserweiterungen und Erweiterungen konzentriert, die die Benutzererfahrung im Vergleich zu den täglichen Versionen wesentlich beeinflussen. Eine neue Version der Funktionen wird nicht durch die Bereitstellung eines großen Änderungssatzes ausgelöst, sondern durch den Umstieg auf einen Umschalter, der Code aktiviert, der sich im Laufe von Tagen oder Wochen während der täglichen Aktualisierungen angesammelt hat.

Gesundheitskontrollen dienen zur Überwachung des Gesundheitszustands des Antrags. Wenn diese Prüfungen während einer Aktualisierung des AEM-Dienstes als Cloud-Dienst fehlschlagen, wird die Version für diese Umgebung nicht ausgeführt. Adobe untersucht dann, warum das Update dieses unerwartete Verhalten verursachte.

### Composite Node Store {#composite-node-store}

Wie oben erwähnt, werden Updates in den meisten Fällen keine Ausfallzeiten verursachen, auch für den Autor, der ein Cluster aus Knoten ist. Rollierende Aktualisierungen sind möglich, da die Funktion &quot;Composite Node Store&quot;in Oak verwendet wird. Mit dieser Funktion kann AEM mehrere Repositorys gleichzeitig referenzieren. Bei einer rollierenden Bereitstellung enthält die neue grüne AEM-Version ein eigenes Repository `/libs` (das auf TarMK basierende, unveränderliche Repository), das sich von der älteren Blue AEM-Version unterscheidet, obwohl beide auf ein freigegebenes, auf DocumentMK basierendes veränderbares Repository verweisen, das Bereiche wie `/content`, `/conf`und `/etc` andere enthält. Da sowohl die Blue- als auch die Green-Version über eigene Versionen verfügen, können sie beide während der rollierenden Aktualisierung aktiv sein, wobei beide Traffic aufnehmen, bis das Blau vollständig durch das Grün ersetzt wird. `/libs`

## Kundenveröffentlichungen {#customer-releases}

### Kodierung mit der richtigen AEM-Version {#coding-against-the-right-aem-version}

Bei vorherigen AEM-Lösungen änderte sich die aktuelle AEM-Version selten (etwa jährlich mit vierteljährlichen Service Packs), und Kunden aktualisieren die Produktionsinstanzen zu ihrer eigenen Zeit auf den neuesten Schnellstart, wobei auf die API-JAR verwiesen wird. AEM als Cloud-Service-Anwendungen werden jedoch häufiger automatisch auf die neueste Version von AEM aktualisiert. Daher sollte benutzerdefinierter Code für interne Versionen mit diesen neueren AEM-Schnittstellen erstellt werden.

Wie bei vorhandenen Nicht-Cloud-AEM-Versionen wird eine lokale Offline-Entwicklung unterstützt, die auf einem bestimmten Schnellstart basiert. In den meisten Fällen ist dies das bevorzugte Debugging-Tool.

> [!HINWEIS}
>Es gibt geringfügige betriebliche Unterschiede zwischen dem Verhalten der Anwendung auf einem lokalen Computer und der Adobe Cloud. Diese architektonischen Unterschiede müssen bei der lokalen Entwicklung beachtet werden und könnten bei der Bereitstellung der Cloud-Infrastruktur zu einem anderen Verhalten führen. Aufgrund dieser Unterschiede ist es wichtig, die umfassenden Tests in Entwicklungs- und Bereitstellungsumgebungen durchzuführen, bevor neuer benutzerdefinierter Code in der Produktion eingeführt wird.

Um benutzerdefinierten Code für eine interne Version zu entwickeln, sollte die entsprechende Version von [AEM als Cloud-Dienst-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) heruntergeladen und installiert werden. Weitere Informationen zur Verwendung der Funktion als Cloud-Dienst-Dispatcher-Tools finden Sie auf [dieser Seite](/help/implementing/dispatcher/overview.md).

## Bereitstellen von Content Packages über Cloud Manager und Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Bereitstellung über Cloud Manager {#deployments-via-cloud-manager}

Kunden stellen benutzerdefinierten Code über Cloud Manager in Cloud-Umgebungen bereit. Beachten Sie, dass Cloud Manager lokal assemblierte Inhaltspakete in ein Artefakt gemäß dem Sling-Funktionsmodell umwandelt. So wird eine AEM als Cloud-Serviceanwendung beschrieben, wenn sie in einer Cloud-Umgebung ausgeführt wird. Wenn Sie sich also die Pakete im Package Manager in Cloud-Umgebungen ansehen, enthält der Name &quot;cp2fm&quot;und die transformierten Pakete enthalten alle Metadaten entfernt. Sie können nicht interagiert werden, d. h. sie können nicht heruntergeladen, repliziert oder geöffnet werden. Ausführliche Dokumentation zum Konverter finden Sie hier [](https://github.com/apache/sling-org-apache-sling-feature-cpconverter).

Inhaltspakete, die für AEM als Cloud-Service-Anwendungen geschrieben wurden, müssen eine saubere Trennung zwischen unveränderbarem und unveränderlichem Inhalt aufweisen. Cloud Manager erzwingt dies, indem der Build fehlschlägt und eine Meldung wie die folgende ausgegeben wird:

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

Der Rest dieses Abschnitts beschreibt die Zusammensetzung und Implikationen unveränderlicher und veränderbarer Pakete.

### Unveränderliche Inhaltspakete {#immutabe-content-packages}

Sämtlicher Inhalt und Code, der im unveränderlichen Repository beibehalten wird, muss in Git überprüft und über Cloud Manager bereitgestellt werden. Anders ausgedrückt wird Code im Gegensatz zu aktuellen AEM-Lösungen nie direkt auf einer laufenden AEM-Instanz bereitgestellt. Dadurch wird sichergestellt, dass der Code, der für eine bestimmte Version in einer Cloud-Umgebung ausgeführt wird, identisch ist. Dadurch wird das Risiko unbeabsichtigter Codeänderungen bei der Produktion vermieden. Beispiel: Die OSGI-Konfiguration sollte der Quellcodeverwaltung übergeben und nicht zur Laufzeit über den Configuration Manager der AEM-Webkonsole verwaltet werden.

Da Anwendungsänderungen aufgrund des Blue-Green-Bereitstellungsmusters durch einen Switch aktiviert werden, können sie nicht von Änderungen im veränderbaren Repository abhängig sein, mit Ausnahme von Dienstbenutzern, ihren ACLs, Nodetyps und Änderungen der Indexdefinition.

Für Kunden mit vorhandenen Code-Datenbanken ist es wichtig, die in der AEM-Dokumentation beschriebene Repository-Restrukturierung durchzuführen, um sicherzustellen, dass zuvor unter &quot;/etc&quot;befindliche Inhalte an den richtigen Speicherort verschoben werden.

## OSGI-Konfiguration {#osgi-configuration}

Wie bereits erwähnt, sollte die OSGI-Konfiguration der Quellcodeverwaltung anstatt über die Web-Konsole zugewiesen werden. Dazu gehören:

* Vornehmen der erforderlichen Änderungen in der lokalen AEM-Umgebung des Entwicklers mit dem Konfigurationsmanager der AEM-Webkonsole und anschließendem Exportieren der Ergebnisse in das AEM-Projekt im lokalen Dateisystem
* Manuelles Erstellen der OSGI-Konfiguration im AEM-Projekt auf dem lokalen Dateisystem, wobei auf den Konfigurationsmanager der AEM-Konsole für die Eigenschaftsnamen verwiesen wird.

## Veränderlicher Inhalt {#mutable-content}

In einigen Fällen kann es nützlich sein, Inhaltsänderungen in der Quellcodeverwaltung vorzubereiten, damit sie von Cloud Manager bereitgestellt werden können, sobald eine Umgebung aktualisiert wurde. Es ist beispielsweise sinnvoll, bestimmte Stammordnerstrukturen zu kopieren oder Änderungen in editierbaren Vorlagen anzuordnen, um Richtlinien in Komponenten zu aktivieren, die von der Anwendungsbereitstellung aktualisiert wurden.

Es gibt zwei Strategien, um die Inhalte zu beschreiben, die von Cloud Manager für das veränderliche Repository bereitgestellt werden, d. h. veränderliche Inhaltspakete und Aussagen zum erneuten Verweisen.

### Flexible Inhaltspakete {#mutable-content-packages}

Inhalte wie Ordnerpfadhierarchien, Dienstbenutzer und Zugriffssteuerelemente (ACLs) werden in der Regel in ein AEM-Projekt übertragen, das auf Archetypen basiert. Zu den Techniken gehören der Export aus AEM oder das direkte Schreiben als XML. Während der Erstellung und Bereitstellung packt Cloud Manager das resultierende Paket mit veränderlichen Inhalten. Der veränderbare Inhalt wird während der Bereitstellungsphase in der Pipeline zu drei verschiedenen Zeitpunkten installiert:

Vor dem Start der neuen Version der Anwendung:

* Indexdefinitionen (hinzufügen, ändern, entfernen)

Während des Starts der neuen Version der Anwendung, aber vor dem Umstieg:

* Dienstbenutzer (Hinzufügen)
* ACLs für Dienstbenutzer (Hinzufügen)
* Knotentypen (hinzufügen)

Nach der Umstellung auf eine neue Anwendungsversion:

* Alle anderen Inhalte über Jackrabbit Vault zu definieren. Beispiel:
   * Ordner (hinzufügen, ändern, entfernen)
   * Bearbeitbare Vorlagen (Hinzufügen, Ändern, Entfernen)
   * Context Aware-Konfiguration (alles unter `/conf`) (Hinzufügen, Ändern, Entfernen)
   * Skripten (Pakete können Installationshaken in verschiedenen Phasen des Installationsprozesses der Paketinstallation auslösen)

Es ist möglich, die Installation variabler Inhalte auf Autoren oder Veröffentlichungen zu beschränken, indem Sie Pakete in einen Ordner install.author oder install.publish unter einbetten `/apps`. Details zur empfohlenen Projektumstrukturierung finden Sie in der [AEM-Dokumentation](https://docs.adobe.com/content/help/en/experience-manager-65/deploying/restructuring/repository-restructuring.html) .

>[!NOTE] Inhaltspakete werden für alle Umgebungstypen (dev, stage, prod) bereitgestellt. Die Bereitstellung kann nicht auf eine bestimmte Umgebung beschränkt werden. Diese Einschränkung ist vorhanden, um die Option eines Testlaufs der automatisierten Ausführung sicherzustellen. Für eine Umgebung spezifische Inhalte müssen manuell über Package Manager installiert werden.

Außerdem gibt es keinen Mechanismus, um die Änderungen des veränderlichen Inhaltspakets nach deren Anwendung zurückzusetzen. Wenn Kunden ein Problem erkennen, können sie es in ihrer nächsten Codeversion oder als letztes Mittel beheben und das gesamte System auf einen Zeitpunkt vor der Bereitstellung wiederherstellen.

Alle enthaltenen Pakete von Drittanbietern müssen als AEM-kompatibel mit einem Cloud-Dienst validiert werden. Andernfalls führt die Einbeziehung zu einem Bereitstellungsfehler.

Wie oben erwähnt, sollten Kunden mit vorhandenen Code-Datenbanken der in der [AEM-Dokumentation](https://helpx.adobe.com/experience-manager/6-5/sites/deploying/using/repository-restructuring.html)beschriebenen Repository-Restrukturierung entsprechen.

## Repointing {#repoinit}

Für die folgenden Fälle ist es vorzuziehen, explizite Inhaltserstellungsanweisungen in OSGI- `repoinit` Fabrikkonfigurationen manuell zu kodieren:

* Dienstbenutzer erstellen/löschen/deaktivieren
* Gruppen erstellen/löschen
* Benutzer erstellen/löschen
* ACLs hinzufügen
   > [!NOTE] Die Definition von ACLs erfordert, dass die Knotenstrukturen bereits vorhanden sind. Daher können Anweisungen zur vorherigen Erstellung von Pfaden erforderlich sein.
* Pfad hinzufügen (z. B. für Stammordnerstrukturen)
* Hinzufügen von CNDs (Begriffsdefinitionen)

Sie sollten aufgrund der folgenden Vorteile erneut auf diese Anwendungsfälle zur Änderung der unterstützten Inhalte verweisen:

* Repoinit erstellt Ressourcen beim Start, sodass Logik die Existenz dieser Ressourcen als selbstverständlich betrachten kann. Bei der Methode des Pakets für veränderliche Inhalte werden Ressourcen nach dem Start erstellt, sodass Anwendungscode, der auf diesen basiert, möglicherweise fehlschlägt.
* Repoinit ist eine relativ sichere Anweisung, da Sie explizit steuern, welche Aktion ausgeführt werden soll. Außerdem werden nur zusätzliche Vorgänge unterstützt, mit Ausnahme einiger sicherheitsrelevanter Fälle, in denen Benutzer, Dienstbenutzer und Gruppen entfernt werden können. Dagegen ist die Entfernung von etwas im variablen Inhaltspaket-Ansatz explizit.  Wenn Sie einen Filter definieren, werden alle von einem Filter erfassten Elemente gelöscht. Vorsicht ist geboten, da es bei jedem Inhalt Szenarien gibt, in denen das Vorhandensein neuer Inhalte das Verhalten der Anwendung verändern kann.
* Repoinit führt schnelle und atomare Operationen durch. Veränderliche Inhaltspakete dagegen können in hohem Maße von der Leistung abhängig sein, die von den Strukturen, die von einem Filter abgedeckt werden. Selbst wenn Sie einen einzelnen Knoten aktualisieren, kann ein Snapshot eines großen Baums erstellt werden.
* Es ist möglich, die Anweisung zum erneuten Verweisen zur Laufzeit in einer lokalen dev-Umgebung zu überprüfen, da sie ausgeführt wird, wenn die OSGi-Konfiguration registriert wird.
* Repoinit-Anweisungen sind atomisch und explizit und werden übersprungen, wenn der Status bereits übereinstimmt.

Wenn Cloud Manager die Anwendung bereitstellt, werden diese Anweisungen unabhängig von der Installation von Inhaltspaketen ausgeführt.

Gehen Sie wie folgt vor, um weitere Aussagen zu erstellen:

1. OSGi-Konfiguration für PID `org.apache.sling.jcr.repoinit.RepositoryInitializer` in einem Konfigurationsordner des Projekts hinzufügen
1. Fügen Sie der Skripteigenschaft der config die Anweisung repoinit hinzu. Syntax und Optionen sind in der [Sling-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html)dokumentiert. Beachten Sie, dass vor den untergeordneten Ordnern explizit ein übergeordneter Ordner erstellt werden muss. Beispielsweise eine explizite Erstellung von `/content` zuvor `/content/myfolder`, vorher `/content/myfolder/mysubfolder`. Für ACLs, die auf niedrigen Strukturen festgelegt werden, wird empfohlen, diese auf einer höheren Ebene festzulegen und mit einer `rep:glob` Einschränkung zu arbeiten.  Beispiel `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. Validieren Sie zur Laufzeit in der lokalen Entwicklungsumgebung.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Für ACLs, die für Knoten unter `/apps` oder `/libs` die Ausführung des Repunkts definiert sind, beginnt die Ausführung in einem leeren Repository. Die Pakete werden nach dem Repoinit installiert, sodass Anweisungen sich nicht auf etwas verlassen können, das in den Paketen definiert ist, sondern müssen die Bedingungen wie die übergeordneten Strukturen darunter definieren.

>[!TIP]
>
>Für ACLs ist die Erstellung von tiefen Strukturen möglicherweise schwerfällig, daher ist es vernünftiger, ein ACL auf einer höheren Ebene zu definieren und zu beschränken, wo es über eine rep:glob-Beschränkung handeln soll.

Weitere Informationen zu Repoinit finden Sie in der [Sling-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Package Manager &quot;one offs&quot;für Pakete mit variablem Inhalt {#package-manager-oneoffs-for-mutable-content-packages}

Es gibt Anwendungsfälle, in denen ein Inhaltspaket als &quot;Einmal&quot;installiert werden sollte. Importieren Sie beispielsweise bestimmten Inhalt von Produktion auf Staging, um ein Produktionsproblem zu debuggen. Für diese Szenarien kann Package Manager in AEM als Cloud-Dienstumgebungen verwendet werden.

Da Package Manager ein Laufzeitkonzept ist, ist es nicht möglich, Inhalte oder Code in das unveränderliche Repository zu installieren. Daher sollten diese Inhaltspakete nur aus veränderlichem Inhalt bestehen (hauptsächlich `/content` oder `/conf`). Wenn das Inhaltspaket gemischten Inhalt enthält (sowohl veränderlicher als auch unveränderlicher Inhalt), wird nur der veränderliche Inhalt installiert.

Sämtliche über Cloud Manager installierten Inhaltspakete (sowohl veränderlich als auch unveränderlich) werden in der Benutzeroberfläche von AEM Package Manager als eingefroren angezeigt. Diese Pakete können nicht neu installiert, neu erstellt oder sogar heruntergeladen werden und werden mit dem Suffix **&quot;cp2fm&quot;** aufgelistet, was anzeigt, dass ihre Installation von Cloud Manager verwaltet wurde.

### Einschließlich Drittanbieter-Pakete {#including-third-party}

Es ist üblich, dass Kunden vorgefertigte Pakete aus Drittanbieterquellen wie Software-Anbietern wie den Übersetzungspartnern von Adobe einbeziehen. Es wird empfohlen, diese Pakete in einem Remote-Repository zu hosten und sie im `pom.xml`. Dies ist nur für öffentliche Repositorys möglich.

Wenn das Speichern des Pakets in einem Remote-Repository nicht möglich ist, können Kunden in einem lokalen, dateisystembasierten Maven-Repository platzieren, das zu SCM als Teil des Projekts verpflichtet ist und unabhängig davon referenziert wird. Das Projektarchiv wird in den nachfolgend dargestellten Projektplänen deklariert:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Alle enthaltenen Pakete von Drittanbietern müssen den in diesem Artikel beschriebenen Richtlinien für die Codierung und Verpackung von AEM als Cloud-Dienst entsprechen. Andernfalls führt die Einbeziehung zu einem Bereitstellungsfehler.

Das folgende Maven POM XML-Fragment zeigt, wie Pakete von Drittanbietern über die **Plugin-Konfiguration filevault-package-maven-plugin in** Maven in das &quot;Container&quot;-Paket des Projekts eingebettet werden können, üblicherweise mit dem Namen **&#39;all&#39;**.

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

## Funktionsweise von Rollierenden Bereitstellungen {#how-rolling-deployments-work}

Wie AEM-Updates werden auch Kundenversionen mithilfe einer kontinuierlichen Implementierungsstrategie bereitgestellt, um unter den richtigen Umständen Ausfallzeiten im Autorencluster zu vermeiden. Die allgemeine Reihenfolge der Ereignisse ist wie unten beschrieben, wobei **Blue** die alte Version des Kundencodes und **Green** die neue Version ist. Sowohl Blau als auch Grün verwenden dieselbe Version von AEM-Code.

* Blaue Version ist aktiv und ein Release-Kandidat für Grün wurde erstellt und verfügbar
* Wenn neue oder aktualisierte Indexdefinitionen vorhanden sind, werden die entsprechenden Indizes verarbeitet. Beachten Sie, dass bei der blauen Bereitstellung immer die alten Indizes verwendet werden, während beim grünen Index immer die neuen Indizes verwendet werden.
* Grün beginnt, während Blau noch serviert
* Blau läuft und serviert, während Green durch Gesundheitskontrollen auf die Bereitschaft überprüft wird
* Grüne Knoten, die bereit sind, Traffic zu akzeptieren und blaue Knoten zu ersetzen, die heruntergefahren werden
* Im Laufe der Zeit werden blaue Nodes durch grüne ersetzt, bis nur noch Grün übrig bleibt, wodurch die Bereitstellung abgeschlossen wird
* Alle neuen oder geänderten veränderlichen Inhalte werden bereitgestellt

## Indexes {#indexes}

Neue oder geänderte Indizes führen zu einem zusätzlichen Indizierungs- oder Neuindizierungsschritt, bevor die neue (grüne) Version Traffic aufnehmen kann. Details zum Indexmanagement in Skyline finden Sie in [diesem Artikel](/help/operations/indexing.md). Sie können den Status des Indexauftrags auf der Buildseite von Cloud Manager überprüfen und erhalten eine Benachrichtigung, sobald die neue Version Traffic aufnehmen kann.

>[!NOTE]
>
>Die für eine kontinuierliche Bereitstellung benötigte Zeit hängt von der Größe des Indexes ab, da die grüne Version Traffic erst akzeptieren kann, wenn der neue Index generiert wurde.

Derzeit funktioniert Skyline nicht mit Indexverwaltungstools wie ACS Commons Sicherstellen des Oak Index-Tools.

## Replikation {#replication}

Der Veröffentlichungsmechanismus ist rückwärtskompatibel mit den [AEM Replication Java-APIs](https://helpx.adobe.com/experience-manager/6-3/sites/developing/using/reference-materials/diff-previous/changes/com.day.cq.replication.Replicator.html).

Um mit der Cloud bereitstehenden AEM QuickStart-Lösung Replizierung zu entwickeln und zu testen, müssen die klassischen Replizierungsfunktionen mit einem Autor-/Veröffentlichungssetup verwendet werden. Wenn der Einstiegspunkt der Benutzeroberfläche in AEM Author für die Cloud entfernt wurde, gehen die Benutzer zur Konfiguration `http://localhost:4502/etc/replication` .

## Abwärtskompatibler Code für Rollierende Bereitstellungen {#backwards-compatible-code-for-rolling-deployments}

Wie oben erläutert, bedeutet die kontinuierliche Bereitstellungsstrategie von AEM als Cloud-Dienst, dass sowohl die alte als auch die neue Version gleichzeitig ausgeführt werden können. Seien Sie daher vorsichtig bei Codeänderungen, die nicht rückwärtskompatibel mit der alten AEM-Version sind, die weiterhin verwendet wird.

Darüber hinaus sollte die alte Version auf Kompatibilität mit allen neuen Strukturen für veränderliche Inhalte getestet werden, die von der neuen Version im Falle einer Zurücknahme angewendet werden, da veränderliche Inhalte nicht entfernt werden.

### Dienstbenutzer und ACL-Änderungen {#service-users-and-acl-changes}

Das Ändern von Dienstbenutzern oder ACLs, die für den Zugriff auf Inhalte oder Code erforderlich sind, kann in älteren AEM-Versionen zu Fehlern führen, was den Zugriff auf diesen Inhalt oder Code mit veralteten Dienstbenutzern ermöglicht. Um dieses Verhalten zu beheben, wird empfohlen, Änderungen in mindestens 2 Versionen durchzuführen, wobei die erste Version als Brücke fungiert, bevor sie in der folgenden Version bereinigt wird.

### Indexänderungen {#index-changes}

Wenn Änderungen an Indizes vorgenommen werden, ist es wichtig, dass die Blue-Version ihre Indizes bis zum Ende verwendet, während die Green-Version ihre eigenen geänderten Indizes verwendet. Der Entwickler sollte die [in diesem Artikel](/help/operations/indexing.md)beschriebenen Indexmanagementtechniken befolgen.

### Konservative Kodierung für Rückflüsse {#conservative-coding-for-rollbacks}

Wenn nach der Bereitstellung ein Fehler gemeldet oder erkannt wird, ist möglicherweise ein Rollback zur Blue-Version erforderlich. Es wäre ratsam sicherzustellen, dass der Blue-Code mit allen neuen Strukturen kompatibel ist, die von der grünen Version erstellt wurden, da die neuen Strukturen (alle veränderlichen Inhalte) nicht zurückgenommen werden. Wenn der alte Code nicht kompatibel ist, müssen Korrekturen in späteren Kundenveröffentlichungen vorgenommen werden.

## Runmodes {#runmodes}

In bestehenden AEM-Lösungen haben Kunden die Möglichkeit, Instanzen mit beliebigen Ausführungsmodi auszuführen und OSGI-Konfigurationen anzuwenden oder OSGI-Pakete auf diese spezifischen Instanzen zu installieren. Zu den definierten Ausführungsmodi gehören normalerweise der *Dienst* (Autor und Veröffentlichung) und die Umgebung (dev, stage, prod).

AEM als Cloud-Dienst hingegen ist genauer darüber informiert, welche Ausführungsmodi verfügbar sind und wie ihnen OSGI-Pakete und OSGI-Konfigurationen zugeordnet werden können:

* Die OSGI-Konfigurationslaufmodi müssen auf dev, stage, prod für die Umgebung oder den Autor verweisen und für den Dienst veröffentlichen. Es `<service>.<environment_type>` wird eine Kombination von unterstützt, die jedoch in dieser bestimmten Reihenfolge verwendet werden müssen (z. B. author.dev oder publish.prod). Die OSGI-Token sollten direkt aus dem Code referenziert werden, anstatt die `getRunModes` Methode zu verwenden, die zur Laufzeit nicht mehr die `environment_type` enthält.
* Die Ausführungsmodi von OSGI-Bundles sind auf den Dienst (Autor, Veröffentlichung) beschränkt. OSGI-Pakete pro Ausführung sollten im Inhaltspaket unter entweder `install/author` oder `install/publish`installiert werden.

Wie bei den vorhandenen AEM-Lösungen gibt es keine Möglichkeit, Ausführungsmodi zu verwenden, um nur Inhalte für bestimmte Umgebungen oder Dienste zu installieren. Wenn Sie eine Entwicklungsumgebung mit Daten oder HTML starten möchten, die sich nicht auf der Bühne oder in der Produktion befinden, könnte Package Manager verwendet werden.

Die folgenden Runmode-Konfigurationen werden unterstützt:

* **config** (*Die Standardeinstellung gilt für alle AEM-Dienste*)
* **config.author** (*Gilt für alle AEM Author-Dienste*)
* **config.author.dev** (*Gilt für den AEM Dev Author-Dienst*)
* **config.author.stage** (*Gilt für den AEM Staging Author-Dienst*)
* **config.author.prod** (*Gilt für den AEM Production Author-Dienst*)
* **config.publish** (*Gilt für den AEM Publish-Dienst*)
* **config.publish.dev** (*Gilt für den AEM Dev Publish-Dienst*)
* **config.publish.stage** (*Gilt für den AEM Staging Publish-Dienst*)
* **config.publish.prod** (*Gilt für den AEM Production Publish-Dienst*)
* **config.dev** (*Gilt für AEM Dev-Dienste)
* **config.stage** (*Gilt für AEM Staging-Dienste)
* **config.prod** (*Gilt für AEM Production-Dienste)

Es wird die OSGI-Konfiguration verwendet, die über die am besten passenden Ausführungsmodi verfügt.

Bei der lokalen Entwicklung kann ein Startparameter des Ausführungsmodus übergeben werden, um anzugeben, welche OSGI-Konfiguration im Ausführungsmodus verwendet wird.

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Konfiguration von Wartungsaufgaben in der Quellcodeverwaltung {#maintenance-tasks-configuration-in-source-control}

Die Konfiguration von Wartungsaufgaben muss in der Quellcodeverwaltung beibehalten werden, da der Bildschirm &quot; **Werkzeuge&quot;> &quot;Vorgänge** &quot;in Cloud-Umgebungen nicht mehr verfügbar ist. Dies hat den Vorteil, dass Veränderungen vorsätzlich beibehalten werden, anstatt reaktiv angewandt und vielleicht vergessen. Weitere Informationen finden Sie im Artikel[ zur ](/help/operations/maintenance.md)Wartungsaufgabe.
