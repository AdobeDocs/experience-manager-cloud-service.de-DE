---
title: Bereitstellen für AEM as a Cloud Service
description: Bereitstellen für AEM as a Cloud Service
feature: Deploying
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '3523'
ht-degree: 80%

---

# Bereitstellen für AEM as a Cloud Service {#deploying-to-aem-as-a-cloud-service}

## Einführung {#introduction}

Die Grundlagen der Code-Entwicklung in AEM as a Cloud Service ähneln denen von AEM On-Premise- und Managed Services-Lösungen. Entwickler schreiben Code und testen ihn lokal, bevor sie ihn an Remote-AEM as a Cloud Service-Umgebungen pushen. Dafür wird Cloud Manager benötigt, das ein optionales Tool zur Inhaltsbereitstellung für Managed Services war. Dies ist nun das einzige Verfahren für die Bereitstellung von Code in AEM as a Cloud Service-Entwicklungs-, Staging- und Produktionsumgebungen. Zur schnellen Funktionsüberprüfung und zum Debugging vor der Bereitstellung der oben genannten Umgebungen kann der Code von einer lokalen Umgebung mit einer [schnellen Entwicklungsumgebung](/help/implementing/developing/introduction/rapid-development-environments.md) synchronisiert werden.

Die Aktualisierung der [AEM-Version](/help/implementing/deploying/aem-version-updates.md) ist stets ein separates Bereitstellungsereignis, das nicht mit dem Pushen von [anwenderspezifischem Code](#customer-releases) verbunden ist. Anders gesagt, sollten Versionen von benutzerspezifischem Code mit der AEM Version getestet werden, die sich in der Produktion befindet, da diese Version oben bereitgestellt wird. AEM Aktualisierungen der Version, die danach stattfinden und häufig auftreten und automatisch angewendet werden. Sie sollen abwärtskompatibel mit dem bereits bereitgestellten anwenderpezifischen Code sein.

In diesem Dokument wird beschrieben, wie Entwickler ihr Vorgehen anpassen sollten, um sowohl mit Aktualisierungen der AEM as a Cloud Service-Version als auch mit benutzerspezifischen Aktualisierungen zu arbeiten.

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).
-->

## Benutzerspezifische Versionen {#customer-releases}

### Kodierung mit der richtigen AEM-Version {#coding-against-the-right-aem-version}

Bei früheren AEM-Lösungen änderte sich die aktuelle AEM-Version selten (etwa 1-mal jährlich mit vierteljährlichen Service Packs); Kunden aktualisierten die Produktionsinstanzen im eigenen Tempo auf den neuesten Schnellstart, indem sie auf das API-JAR verwiesen. AEM as a Cloud Service-Programme jedoch werden häufiger automatisch auf die neueste Version von AEM aktualisiert. Daher sollte anwenderpezifischer Code für interne Freigaben für die neueste AEM-Version erstellt werden.

Wie bei bestehenden Nicht-Cloud-AEM-Versionen wird eine lokale, Offline-Entwicklung unterstützt, die auf einem bestimmten Schnellstart basiert. In den meisten Fällen ist dies das bevorzugte Debugging-Tool.

>[!NOTE]
>Beim Verhalten des Programms gibt es geringfügige Unterschiede zwischen einem lokalen Computer und der Adobe Cloud. Diese architektonischen Unterschiede müssen bei der lokalen Entwicklung berücksichtigt werden und können bei Bereitstellung in der Cloud-Infrastruktur ggf. zu einem anderen Verhalten führen. Darum ist es wichtig, in Entwicklungs- und Staging-Umgebungen umfassende Tests durchzuführen, bevor neuer benutzerspezifischer Code in die Produktionsumgebung eingeführt wird.

Um benutzerdefinierten Code für eine interne Version zu entwickeln, muss die entsprechende Version der [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) heruntergeladen und installiert werden. Weitere Informationen zur Verwendung der AEM as a Cloud Service-Dispatcher-Tools finden Sie auf [dieser Seite](/help/implementing/dispatcher/disp-overview.md).

Das folgende Video bietet einen Überblick über die Bereitstellung von Code für AEM as a Cloud Service:

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html). 
-->

## Bereitstellen von Inhaltspaketen über Cloud Manager und Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Bereitstellungen über Cloud Manager {#deployments-via-cloud-manager}

<!-- Alexandru: temporarily commenting this out, until I get some clarification from Brian 

![image](https://git.corp.adobe.com/storage/user/9001/files/e91b880e-226c-4d5a-93e0-ae5c3d6685c8) -->

Kunden können benutzerspezifischen Code in Cloud-Umgebungen über Cloud Manager bereitstellen. Beachten Sie, dass Cloud Manager lokal assemblierte Inhaltspakete nach dem Sling-Funktionsmodell in ein Artefakt umwandelt. So wird ein AEM as a Cloud Service-Programm beschrieben, wenn es in einer Cloud-Umgebung ausgeführt wird. Wenn Sie also die Pakete in [Package Manager](/help/implementing/developing/tools/package-manager.md) für Cloud-Umgebungen betrachten, stellen Sie fest, dass der Name „cp2fm“ enthält und alle Metadaten der umgewandelten Pakete entfernt wurden. Mit ihnen kann nicht interagiert werden; d. h. sie lassen nicht herunterladen, replizieren oder öffnen. Eine ausführliche Dokumentation zum Konvertierer finden Sie [hier](https://github.com/apache/sling-org-apache-sling-feature-cpconverter).

Inhalts-Packages, die für AEM as a Cloud Service-Progrramme geschrieben wurden, müssen eine saubere Trennung zwischen unveränderlichem und veränderlichem Inhalt aufweisen, und Cloud Manager installiert nur den veränderlichen Inhalt und gibt außerdem eine Meldung wie diese aus:

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

Im Rest dieses Abschnitts werden die Komposition und Implikationen unveränderlicher und veränderlicher Pakete beschrieben.

### Unveränderliche Inhaltspakete {#immutabe-content-packages}

Sämtlicher Inhalt und Code, der im unveränderlichen Repository persistent ist, muss in Git eingecheckt und mit Cloud Manager bereitgestellt werden. Anders gesagt: Im Gegensatz zu aktuellen AEM-Lösungen wird Code niemals direkt in einer laufenden AEM-Instanz bereitgestellt. Dadurch wird sichergestellt, dass der Code, der für eine bestimmte Version in beliebigen Cloud-Umgebungen ausgeführt wird, identisch ist. So wird das Risiko unbeabsichtigter Code-Varianten in der Produktion eliminiert. Beispiel: Die OSGi-Konfiguration sollte der Quell-Code-Verwaltung übergeben und nicht zur Laufzeit über den Konfigurations-Manager der AEM-Web-Konsole verwaltet werden.

Da Anwendungsänderungen aufgrund des Bereitstellungsmusters durch einen Schalter aktiviert werden, können sie nicht von Änderungen im veränderlichen Repository abhängig sein, mit Ausnahme von Dienstbenutzern, ihren ACLs, Knotentypen und Änderungen der Indexdefinition.

Kunden mit vorhandener Code-Basis müssen die in der AEM-Dokumentation beschriebene Repository-Umstrukturierung durchführen, um dafür zu sorgen, dass zuvor unter „/etc“ befindliche Inhalte an den richtigen Speicherort verschoben werden.

Für diese Code-Pakete gelten einige zusätzliche Einschränkungen, z. B. werden keine [Install Hooks](https://jackrabbit.apache.org/filevault/installhooks.html) unterstützt.

## OSGi-Konfiguration {#osgi-configuration}

Wie bereits erwähnt, sollte die OSGi-Konfiguration an die Quell-Code-Verwaltung übermittelt werden und nicht über die Web-Konsole. Zu geeigneten Verfahren gehören:

* Vornehmen der erforderlichen Änderungen in der lokalen AEM-Umgebung des Entwicklers mit dem Konfigurations-Manager der AEM-Web-Konsole und anschließendes Exportieren der Ergebnisse in das AEM-Projekt im lokalen Dateisystem;
* manuelles Erstellen der OSGi-Konfiguration im AEM-Projekt im lokalen Dateisystem und anschließendes Verweisen auf die Eigenschaftsnamen durch den Konfigurations-Manager der AEM-Web-Konsole.

Weitere Informationen zur OSGi-Konfiguration finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).

## Veränderlicher Inhalt {#mutable-content}

Manchmal kann es nützlich sein, Inhaltsänderungen in der Quell-Code-Verwaltung vorzubereiten, damit sie von Cloud Manager bereitgestellt werden können, sobald eine Umgebung aktualisiert wird. So kann es beispielsweise sinnvoll sein, bestimmte Stammordnerstrukturen zu testen oder Änderungen in editierbaren Vorlagen anzuordnen, um darin Richtlinien für Komponenten zu aktivieren, die bei der Programmbereitstellung aktualisiert wurden.

Es gibt zwei Strategien zur Beschreibung des Inhalts, der von Cloud Manager im veränderlichen Repository bereitgestellt wird: veränderliche Inhaltspakete und repoinit-Anweisungen.

### Veränderliche Inhaltspakete {#mutable-content-packages}

Inhalte wie Ordnerpfadhierarchien, Service-Benutzer und Zugangssteuerungen (ACLs) werden in der Regel in ein AEM-Projekt übertragen, das auf Maven-Archetypen basiert. Zu den Methoden gehören das Exportieren aus AEM oder das direkte Schreiben als XML. Bei der Erstellung und Bereitstellung packt Cloud Manager das resultierende veränderliche Inhaltspaket. Der veränderbare Inhalt wird in der Bereitstellungsphase in der Pipeline zu drei verschiedenen Zeitpunkten installiert:

Vor dem Start der neuen Version des Programms:

* Indexdefinitionen (hinzufügen, ändern, entfernen)

Beim Start der neuen Version des Programms, aber vor der Umstellung:

* Service-Benutzer (hinzufügen)
* ACLs für Service-Benutzer (hinzufügen)
* Knotentypen (hinzufügen)

Nach der Umstellung auf die neue Programmversion:

* Alle anderen Inhalte, über Jackrabbit Vault definierbar Beispiel:
   * Ordner (hinzufügen, ändern, entfernen)
   * Bearbeitbare Vorlagen (hinzufügen, ändern, entfernen)
   * Kontextsensible Konfiguration (alles unter `/conf`) (hinzufügen, ändern, entfernen)
   * Skripte (Pakete können in verschiedenen Phasen der Paketinstallation Installationshaken auslösen. Informationen zu Installations Hooks finden Sie in der [Jackrabbit Filevault-Dokumentation](https://jackrabbit.apache.org/filevault/installhooks.html). Beachten Sie, dass AEM CS derzeit die Filevault-Version 3.4.0 verwendet, die die Installations-Hooks für Admin-Benutzer, Systembenutzer und Mitglieder der Administratorgruppe einschränkt).

Die Installation veränderlicher Inhalte in Autoren- oder Veröffentlichungsinstanzen lässt sich einschränken, indem Sie Pakete unter `/apps` in einen „install.author“- oder „install.publish“-Ordner einbetten. Eine Umstrukturierung, die dieser Trennung Rechnung trägt, wurde in AEM 6.5 vorgenommen. Einzelheiten zur empfohlenen Projektumstrukturierung finden Sie in der [Dokumentation zu AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html?lang=de)

>[!NOTE]
>Inhaltspakete werden für alle Umgebungstypen (dev, stage, prod) bereitgestellt. Die Bereitstellung kann nicht auf eine bestimmte Umgebung beschränkt werden. Diese Einschränkung dient dazu, einen Testlauf der automatischen Ausführung zu ermöglichen. Umgebungsspezifische Inhalte müssen manuell über [Package Manager](/help/implementing/developing/tools/package-manager.md) installiert werden.

Außerdem gibt es keinen Mechanismus, um die Änderungen an veränderlichen Inhaltspaketen nach deren Anwendung rückgängig zu machen. Wenn Kunden ein Problem entdecken, können sie es in ihrer nächsten Code-Version beheben oder – als letzte Möglichkeit – das ganze System auf einen Zeitpunkt vor der Bereitstellung zurücksetzen.

Alle enthaltenen Pakete von Drittanbietern müssen als kompatibel mit AEM as a Cloud Service validiert werden. Andernfalls führt ihre Einbeziehung zu einem Bereitstellungsfehler.

Wie bereits erwähnt, sollten sich Kunden mit bestehender Code-Basis an die Repository-Umstrukturierung halten, die durch die in der [Dokumentation zu AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html?lang=de) beschriebenen 6.5-Repository-Änderungen erforderlich ist.

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
* Repoinit ist ein relativ sicherer Anweisungssatz, da Sie explizit steuern, welche Aktion vorgenommen werden soll. Zudem werden nur additive Vorgänge unterstützt, mit Ausnahme einiger sicherheitsrelevanter Fälle, in denen Benutzer, Service-Benutzer und Gruppen entfernt werden können. Im Gegensatz dazu ist die Entfernung von etwas im Ansatz für veränderliche Inhaltspakete explizit. Wenn Sie einen Filter definieren, werden alle von einem Filter erfassten Elemente gelöscht. Dennoch ist Vorsicht geboten, da es bei jedem Inhalt Szenarien geben kann, in denen die Existenz neuer Inhalte das Verhalten des Programms verändert.
* Repoinit sorgt für schnelle und atomische Operationen. Veränderliche Inhaltspakete hingegen können stark von der Leistung der Strukturen abhängen, die von einem Filter abgedeckt werden. Auch wenn Sie nur einen Knoten aktualisieren, wird ggf. ein Schnappschuss einer großen Baumstruktur erstellt.
* Es ist möglich, repoinit-Anweisungen in einer lokalen Entwicklungsumgebung zur Laufzeit zu validieren, da sie ausgeführt werden, wenn die OSGi-Konfiguration registriert wird.
* Repoinit-Anweisungen sind atomisch und explizit und werden übersprungen, wenn der Status bereits übereinstimmt.

Wenn Cloud Manager das Programm bereitstellt, werden diese Anweisungen unabhängig von der Installation jeglicher Inhaltspakete ausgeführt.

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

### Package Manager-„one-offs“ für Pakete mit veränderlichen Inhalten {#package-manager-oneoffs-for-mutable-content-packages}

>[!CONTEXTUALHELP]
>id="aemcloud_packagemanager"
>title="Package Manager – Migrieren von Packages mit veränderlichen Inhalten"
>abstract="Erfahren Sie mehr über die Verwendung des Package Manager für Anwendungsfälle, in denen ein Inhaltspaket als &quot;einmalig&quot;installiert werden soll. Dazu gehören der Import bestimmter Inhalte aus der Produktion in die Staging-Umgebung, das Debuggen eines Produktionsproblems, die Übertragung kleiner Inhaltspakete von der On-Premise-Umgebung auf AEM Cloud-Umgebungen und mehr."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de#cloud-migration" text="Content Transfer Tool"

Es gibt Anwendungsfälle, in denen ein Inhaltspaket als „one off“ (einmalig) installiert werden sollte. Beispielsweise können Sie bestimmte Inhalte aus der Produktion in die Staging-Umgebung importieren, um ein Produktionsproblem zu beheben. Für solche Szenarien kann [Package Manager](/help/implementing/developing/tools/package-manager.md) in Umgebungen in AEM as a Cloud Service verwendet werden.

Da Package Manager auf einem Laufzeitkonzept basiert, ist es unmöglich, Inhalte oder Code im unveränderlichen Repository zu installieren. Daher dürfen diese Inhaltspakete nur aus veränderlichen Inhalten bestehen (hauptsächlich `/content` oder `/conf`). Wenn das Inhaltspaket gemischte Inhalte enthält (sowohl veränderliche als auch unveränderliche Inhalte), wird nur der veränderliche Inhalt installiert.

>[!IMPORTANT]
>
>Die Benutzeroberfläche von Package Manager gibt möglicherweise die Fehlermeldung **undefiniert** zurück, wenn die Installation eines Pakets länger als 10 Minuten dauert.
>
>Dies ist nicht auf einen Installationsfehler zurückzuführen, sondern auf eine Zeitüberschreitung, die es bei Cloud Service für alle Anfragen gibt.
>
>Wiederholen Sie die Installation nicht, wenn ein solcher Fehler auftritt. Die Installation wird im Hintergrund korrekt ausgeführt. Würden Sie die Installation neu starten, könnten Konflikte durch mehrere gleichzeitige Importprozesse entstehen.

Sämtliche über Cloud Manager installierten Inhaltspakete (sowohl veränderliche als auch unveränderliche) werden in der Benutzeroberfläche von AEM Package Manager mit einem eingefrorenen Status angezeigt. Solche Pakete können weder neu installiert, neu erstellt noch heruntergeladen werden und werden mit dem Suffix **cp2fm** aufgeführt, was darauf hinweist, dass ihre Installation von Cloud Manager vorgenommen wurde.

### Einschließen von Drittanbieterpaketen {#including-third-party}

Es ist üblich, dass Kunden vorgefertigte Pakete aus Drittanbieterquellen (zum Beispiel von Software-Anbietern wie Übersetzungspartnern von Adobe) einbeziehen. Es wird empfohlen, diese Pakete in einem Remote-Repository zu hosten und in `pom.xml` auf sie zu verweisen. Dies ist für öffentliche Repositorys und auch für private Repositorys mit Kennwortschutz möglich, wie unter [Unterstützung für kennwortgeschütztes Maven-Repository](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories) beschrieben.

Wenn das Speichern des Pakets in einem Remote-Repository nicht möglich ist, können Kunden es in einem lokalen, Dateisystem-basierten Maven-Repository platzieren, das im Rahmen des Projekts an SCM übermittelt und auf das bei Bedarf verwiesen wird. Das Repository wird in diesem Fall wie im nachfolgend dargestellten POM des Projekts deklariert:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Alle enthaltenen Pakete von Drittanbietern müssen den in diesem Artikel beschriebenen Richtlinien zur Kodierung und Verpackung für AEM as a Cloud Service entsprechen. Andernfalls wird ihre Einbeziehung zu einem Bereitstellungsfehler führen.

Das folgende `POM.xml`-Fragment zeigt, wie Drittanbeiter-Pakete über die Maven-Plug-in-Konfiguration **filevault-package-maven-plugin** in das „Container“-Paket des Projekts, in der Regel **&#39;all&#39;** genannt, eingebettet werden können.

```
...
<plugin>
  <groupId>org.apache.jackrabbit</groupId>
  <artifactId>filevault-package-maven-plugin</artifactId>
  <extensions>true</extensions>
  <configuration>
      ...
      <embeddeds>

          ...

          <!-- Include any other extra packages  -->
          <embedded>
              <groupId>com.vendor.x</groupId>
              <artifactId>vendor.plug-in.all</artifactId>
              <type>zip</type>
              <target>/apps/vendor-packages/container/install</target>
          </embedded>
      <embeddeds>
  </configuration>
</plugin>
...
```

## Funktionsweise von rollierenden Bereitstellungen {#how-rolling-deployments-work}

Wie AEM Aktualisierungen werden auch Kundenfreigaben mithilfe einer rollierenden Bereitstellungsstrategie bereitgestellt, um unter den richtigen Umständen Ausfallzeiten im Autoren-Cluster zu vermeiden. Die allgemeine Ereignisabfolge wird unten beschrieben, in der Knoten mit der alten und der neuen Version des Kundencodes dieselbe Version AEM Code ausführen.

* Knoten mit der alten Version sind aktiv und ein Freigabekandidat für die neue Version wird erstellt und verfügbar.
* Wenn neue oder aktualisierte Indexdefinitionen vorhanden sind, werden die entsprechenden Indizes verarbeitet. Beachten Sie, dass Knoten mit der alten Version immer die alten Indizes verwenden, während Knoten mit der neuen Version immer die neuen Indizes verwenden.
* Knoten mit der neuen Version starten, während alte Versionen weiterhin Traffic bereitstellen.
* Knoten mit der alten Version werden ausgeführt und bedienen weiterhin, während Knoten mit der neuen Version über Konsistenzprüfungen auf ihre Bereitschaft überprüft werden.
* Knoten mit der neuen Version, die bereit sind, akzeptieren Traffic und ersetzen die Knoten durch die alte Version, die heruntergefahren wird.
* Im Laufe der Zeit werden die Knoten mit der alten Version durch Knoten mit der neuen Version ersetzt, bis nur Knoten mit neuen Versionen verbleiben, sodass die Bereitstellung abgeschlossen ist.
* Alle neuen oder geänderten veränderlichen Inhalte werden dann bereitgestellt.

## Indizes {#indexes}

Neue oder geänderte Indizes führen zu einem zusätzlichen Indizierungs- oder Neuindizierungsschritt, bevor die neue Version Traffic aufnehmen kann. Details zur Indexverwaltung in AEM as a Cloud Service finden Sie in [diesem Artikel](/help/operations/indexing.md). Sie können den Status des Indizierungsauftrags auf der Build-Seite von Cloud Manager überprüfen und erhalten eine Benachrichtigung, sobald die neue Version bereit zur Aufnahme von Traffic ist.

>[!NOTE]
>
>Die für eine rollierende Implementierung benötigte Zeit hängt von der Größe des Index ab, da die neue Version Traffic erst akzeptieren kann, wenn der neue Index generiert wurde.

Derzeit funktioniert AEM as a Cloud Service nicht mit Indexverwaltungs-Tools wie dem ACS Commons Ensure Oak Index-Tool.

## Replikation {#replication}

Der Veröffentlichungsmechanismus ist rückwärtskompatibel mit den [AEM Replication Java-APIs](https://helpx.adobe.com/de/experience-manager/6-3/sites/developing/using/reference-materials/diff-previous/changes/com.day.cq.replication.Replicator.html).

Um mit Replikation mit dem Cloud-fähigen Schnellstart zu entwickeln und zu testen, müssen die klassischen Replikationsfunktionen mit einem Autoren-/Veröffentlichungssetup verwendet werden. Wenn der Einstiegspunkt der Benutzeroberfläche in AEM Author für die Cloud entfernt wurde, würden Benutzer zur Konfiguration `http://localhost:4502/etc/replication` aufrufen.

## Rückwärtskompatibler Code für rollierende Bereitstellungen {#backwards-compatible-code-for-rolling-deployments}

Wie oben erläutert, beinhaltet die kontinuierliche Bereitstellungsstrategie von AEM as a Cloud Service, dass sich sowohl die alten als auch die neuen Versionen gleichzeitig ausführen lassen. Seien Sie daher vorsichtig bei Code-Änderungen, die nicht rückwärtskompatibel mit der alten, weiter verwendeten AEM-Version sind.

Darüber hinaus sollte die alte Version auf ihre Kompatibilität mit allen neuen Strukturen veränderlicher Inhalte getestet werden, die von der neuen Version im Fall eines Rollbacks angewendet werden, da veränderliche Inhalte nicht entfernt werden.

### Service-Benutzer- und ACL-Änderungen {#service-users-and-acl-changes}

Das Ändern von Service-Benutzern oder ACLs, die für den Zugriff auf Inhalt oder Code erforderlich sind, kann in den älteren AEM-Versionen zu Fehlern führen, sodass mit veralteten Service-Benutzern auf diesen Inhalt oder Code zugegriffen wird. Um dieses Verhalten zu beheben, wird empfohlen, Änderungen über mindestens zwei Versionen zu verteilen, wobei die erste Version als Brücke fungiert, bevor die nächste Version bereinigt wird.

### Indexänderungen {#index-changes}

Wenn Änderungen an Indizes vorgenommen werden, ist es wichtig, dass die neue Version ihre Indizes bis zum Ende verwendet, während die alte Version ihren eigenen geänderten Satz von Indizes verwendet. Der Entwickler sollte die [in diesem Artikel](/help/operations/indexing.md) beschriebenen Methoden zur Indexverwaltung befolgen.

### Konservative Kodierung für Rollbacks {#conservative-coding-for-rollbacks}

Wenn nach der Bereitstellung ein Fehler gemeldet oder erkannt wird, ist möglicherweise ein Rollback zur alten Version erforderlich. Es wird empfohlen sicherzustellen, dass der neue Code mit allen neuen Strukturen kompatibel ist, die von dieser neuen Version erstellt wurden, da die neuen Strukturen (alle veränderlichen Inhalte) nicht zurückgesetzt werden. Wenn der alte Code nicht kompatibel ist, müssen in späteren benutzerspezifischen Versionen Korrekturen vorgenommen werden.

## Schnelle Entwicklungsumgebung (RDE) {#rde}

[Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md) (oder kurz: RDEs) ermöglichen es Entwickelnden, Änderungen schnell bereitzustellen und zu überprüfen und so den Zeitaufwand für das Testen von Funktionen zu minimieren, die nachweislich in einer lokalen Entwicklungsumgebung funktionieren.

Im Gegensatz zu normalen Entwicklungsumgebungen, die Code über die Cloud Manager-Pipeline bereitstellen, verwenden Entwickler Befehlszeilen-Tools, um Code aus einer lokalen Entwicklungsumgebung mit dem RDE zu synchronisieren. Sobald die Änderungen erfolgreich in einer RDE getestet wurden, sollten sie über die Cloud Manager-Pipeline in einer regulären Cloud-Entwicklungsumgebung bereitgestellt werden, wodurch der Code die entsprechenden Qualitätsprüfungen durchläuft.

## Ausführungsmodi {#runmodes}

In bestehenden AEM-Lösungen haben Kundinnen und Kunden die Möglichkeit, Instanzen mit beliebigen Ausführungsmodi auszuführen und OSGi-Konfigurationen anzuwenden oder OSGi-Pakete in diesen spezifischen Instanzen zu installieren. Zu den definierten Ausführungsmodi gehören normalerweise der *Service* (Autor und Veröffentlichen) sowie die Umgebung (RDE, dev, stage, prod).

AEM as a Cloud Service hingegen ist eigenwilliger bezüglich der Frage, welche Ausführungsmodi verfügbar sind und wie ihnen OSGi-Pakete und OSGi-Konfigurationen zugeordnet werden können:

* Die OSGI-Konfigurationslaufmodi müssen auf RDE, dev, stage, prod für die Umgebung oder Autor, Veröffentlichen für den Service verweisen. Es wird eine Kombination aus `<service>.<environment_type>` unterstützt, wobei diese genau in dieser bestimmten Reihenfolge verwendet werden müssen (z. B. `author.dev` oder `publish.prod`). Auf die OSGi-Token sollte direkt im Code verwiesen werden, da die `getRunModes`-Methode zur Laufzeit den `environment_type` nicht mehr enthält. Weitere Informationen finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).
* Die Ausführungsmodi von OSGi-Bundles sind auf den Service (author, publish) beschränkt. OSGi-Pakete für den Pre-Run-Modus sollten im Inhaltspaket unter `install.author` oder `install.publish` installiert werden.

AEM as a Cloud Service lässt die Verwendung von Ausführungsmodi nicht zu, um Inhalte für bestimmte Umgebungen oder Dienste zu installieren. Wenn eine Entwicklungsumgebung mit Daten oder HTML-Dateien bestückt werden muss, die sich nicht in der Staging- oder Produktionsumgebung befinden, kann der Package Manager verwendet werden.

Die folgenden Runmode-Konfigurationen werden unterstützt:

* **config** (*der Standard, gilt für alle AEM-Services*)
* **config.author** (*gilt für alle AEM Author-Services*)
* **config.author.dev** (*gilt für den AEM Dev Author-Service*)
* **config.author.rde** (*Gilt für AEM RDE Autor-Service*)
* **config.author.stage** (*gilt für den AEM Staging Author-Service*)
* **config.author.prod** (*gilt für den AEM Production Author-Service*)
* **config.publish** (*gilt für den AEM Publish-Service*)
* **config.publish.dev** (*gilt für den AEM Dev Publish-Service*)
* **config.publish.rde** (*Gilt für AEM-RDE Publish-Service*)
* **config.publish.stage** (*gilt für den AEM Staging Publish-Service*)
* **config.publish.prod** (*gilt für den AEM Production Publish-Service*)
* **config.dev** (*gilt für AEM-Dev-Services*)
* **config.rde** (*Gilt für RDE-Services*)
* **config.stage** (*gilt für AEM-Staging-Services*)
* **config.prod** (*gilt für AEM-Produktions-Services*)

Es wird jene OSGi-Konfiguration verwendet, die über die meisten passenden Ausführungsmodi verfügt.

Wird die Entwicklung lokal durchgeführt, wird der Ausführungsmodus-Startparameter `-r` verwendet, um die OSGI-Konfiguration des Ausführungsmodus zu definieren.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Konfiguration von Wartungsaufgaben in der Quell-Code-Verwaltung {#maintenance-tasks-configuration-in-source-control}

Die Konfiguration von Wartungsaufgaben muss in der Quell-Code-Verwaltung persistiert werden, da der Bildschirm **Tools > Vorgänge** in Cloud-Umgebungen nicht mehr verfügbar ist. Das hat den Vorteil, dass Veränderungen vorsätzlich persistiert werden, anstatt reaktiv angewandt und ggf. vergessen zu werden. Weitere Informationen finden Sie im [Artikel zur Wartungsaufgabe](/help/operations/maintenance.md).
