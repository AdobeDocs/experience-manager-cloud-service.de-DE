---
title: Bereitstellen für AEM as a Cloud Service
description: Erfahren Sie mehr über die Grundlagen und Best Practices für die Bereitstellung für AEM as a Cloud Service
feature: Deploying
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
role: Admin
source-git-commit: edfefb163e2d48dc9f9ad90fa68809484ce6abb0
workflow-type: tm+mt
source-wordcount: '3440'
ht-degree: 99%

---

# Bereitstellen für AEM as a Cloud Service {#deploying-to-aem-as-a-cloud-service}

## Einführung {#introduction}

Die Grundlagen der Code-Entwicklung in AEM as a Cloud Service ähneln denen von AEM On-Premise- und Managed Services-Lösungen. Entwicklerinnen und Entwickler schreiben Code und testen ihn lokal, bevor sie ihn an Remote-Umgebungen auf AEM as a Cloud Service pushen. Dafür wird Cloud Manager benötigt, das ein optionales Tool zur Inhaltsbereitstellung für Managed Services war. Dieses Bereitstellungs-Tool ist nun das einzige Verfahren für die Bereitstellung von Code in Entwicklungs-, Staging- und Produktionsumgebungen von AEM as a Cloud Service. Zur schnellen Funktionsüberprüfung und zum Debugging vor der Bereitstellung der oben genannten Umgebungen kann der Code von einer lokalen Umgebung mit einer [schnellen Entwicklungsumgebung](/help/implementing/developing/introduction/rapid-development-environments.md) synchronisiert werden.

Die Aktualisierung der [AEM-Version](/help/implementing/deploying/aem-version-updates.md) ist stets ein separates Bereitstellungsereignis, das nicht mit dem Pushen von [anwenderspezifischem Code](#customer-releases) verbunden ist. Anders gesagt: Bei Freigabe von anwenderspezifischem Code sollte mit jener AEM-Version getestet werden, die sich der Produktion befindet, da der Code auf dieser Version bereitgestellt wird. Aktualisierungen der AEM-Version, die danach erfolgen (die häufig erfolgen und automatisch angewendet werden), sollen mit dem bereits bereitgestellten Kunden-Code abwärtskompatibel sein.

In diesem Dokument wird beschrieben, wie Entwicklerinnen und Entwickler ihr Vorgehen anpassen sollten, um sowohl mit Aktualisierungen der AEM as a Cloud Service-Version als auch mit benutzerspezifischen Aktualisierungen zu arbeiten.

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).
-->

## Benutzerspezifische Versionen {#customer-releases}

### Kodierung mit der richtigen AEM-Version {#coding-against-the-right-aem-version}

Bei früheren AEM-Lösungen änderte sich die aktuelle AEM-Version selten (etwa 1-mal jährlich mit vierteljährlichen Service Packs); Kunden aktualisierten die Produktionsinstanzen im eigenen Tempo auf den neuesten Schnellstart, indem sie auf das API-JAR verwiesen. Anwendungen auf AEM as a Cloud Service jedoch werden häufiger automatisch auf die neueste Version von AEM aktualisiert. Daher sollte anwenderspezifischer Code für interne Freigaben für die neueste AEM-Version erstellt werden.

Wie bei vorhandenen Nicht-Cloud-AEM-Versionen wird eine lokale Offline-Entwicklung unterstützt, die auf einem bestimmten Schnellstart basiert. In den meisten Fällen ist dies das bevorzugte Debugging-Tool.

>[!NOTE]
>Beim Verhalten des Programms gibt es geringfügige Unterschiede zwischen einem lokalen Computer und der Adobe Cloud. Diese architektonischen Unterschiede müssen bei der lokalen Entwicklung berücksichtigt werden und können bei Bereitstellung in der Cloud-Infrastruktur ggf. zu einem anderen Verhalten führen. Darum ist es wichtig, in Entwicklungs- und Staging-Umgebungen umfassende Tests durchzuführen, bevor neuer benutzerspezifischer Code in die Produktionsumgebung eingeführt wird.

Um benutzerdefinierten Code für eine interne Version zu entwickeln, sollte die entsprechende Version des [AEM as a Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) heruntergeladen und installiert werden. Weitere Informationen zur Verwendung der AEM as a Cloud Service-Dispatcher-Tools finden Sie unter [Dispatcher in der Cloud](/help/implementing/dispatcher/disp-overview.md).

Das folgende Video bietet einen Überblick über die Bereitstellung von Code für AEM as a Cloud Service:

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html). 
-->

## Implementieren eines Inhaltspakets über Cloud Manager und Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Implementierungen über Cloud Manager {#deployments-via-cloud-manager}

<!-- Alexandru: temporarily commenting this out, until I get some clarification from Brian 

![image](https://git.corp.adobe.com/storage/user/9001/files/e91b880e-226c-4d5a-93e0-ae5c3d6685c8) -->

Kundinnen und Kunden können benutzerspezifischen Code in Cloud-Umgebungen über Cloud Manager bereitstellen. Cloud Manager wandelt lokal assemblierte Inhaltspakete nach dem Sling-Funktionsmodell in ein Artefakt um. So wird eine Anwendung auf AEM as a Cloud Service beschrieben, wenn sie in einer Cloud-Umgebung ausgeführt wird. Wenn Sie die Pakete in [Package Manager](/help/implementing/developing/tools/package-manager.md) für Cloud-Umgebungen betrachten, können Sie deswegen feststellen, dass der Name „cp2fm“ enthält und alle Metadaten der umgewandelten Pakete entfernt wurden. Mit ihnen kann nicht interagiert werden; d. h. sie lassen nicht herunterladen, replizieren oder öffnen. Eine ausführliche Dokumentation zum Konvertierer finden Sie unter [sling-org-apache-sling-feature-cpconverter auf GitHub](https://github.com/apache/sling-org-apache-sling-feature-cpconverter).

Inhaltspakete, die für Anwendungen auf AEM as a Cloud Service geschrieben wurden, müssen eine saubere Trennung zwischen unveränderlichen und veränderlichen Inhalten aufweisen. Cloud Manager installiert nur die veränderlichen Inhalte und gibt außerdem eine Meldung wie die folgende aus:

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

Im Rest dieses Abschnitts werden die Komposition und die Implikationen unveränderlicher bzw. veränderlicher Pakete beschrieben.

### Unveränderliche Inhaltspakete {#immutabe-content-packages}

Sämtlicher Inhalt und Code, der im unveränderlichen Repository persistent ist, muss in Git eingecheckt und mit Cloud Manager bereitgestellt werden. Anders gesagt: Im Gegensatz zu aktuellen AEM-Lösungen wird Code niemals direkt in einer laufenden AEM-Instanz bereitgestellt. Durch diesen Workflow wird sichergestellt, dass der Code, der für eine bestimmte Version in beliebigen Cloud-Umgebungen ausgeführt wird, identisch ist. So wird das Risiko unbeabsichtigter Code-Varianten in der Produktion eliminiert. Beispiel: Die OSGi-Konfiguration sollte der Quell-Code-Verwaltung übergeben und nicht zur Laufzeit über den Konfigurations-Manager der AEM-Web-Konsole verwaltet werden.

Da Anwendungsänderungen aufgrund des Bereitstellungsmusters durch einen Umschalter aktiviert werden, dürfen sie nicht von Änderungen im veränderlichen Repository abhängig sein, mit Ausnahme von Dienstbenutzerinnen und -benutzern, ihren ACLs, Knotentypen und Änderungen der Indexdefinition.

Kundinnen und Kunden mit vorhandener Code-Basis müssen die in der AEM-Dokumentation beschriebene Repository-Umstrukturierung durchführen, um dafür zu sorgen, dass die zuvor unter „/etc“ befindlichen Inhalte an den richtigen Speicherort verschoben werden.

Für diese Code-Pakete gelten einige zusätzliche Einschränkungen, z. B. werden keine [Installations-Hooks](https://jackrabbit.apache.org/filevault/installhooks.html) unterstützt.

## OSGi-Konfiguration {#osgi-configuration}

Wie bereits erwähnt, sollte die OSGi-Konfiguration an die Quell-Code-Verwaltung übermittelt werden und nicht über die Web-Konsole. Zu geeigneten Verfahren gehören:

* Vornehmen der erforderlichen Änderungen in der lokalen AEM-Umgebung des Entwicklers mit dem Konfigurations-Manager der AEM-Web-Konsole und anschließendes Exportieren der Ergebnisse in das AEM-Projekt im lokalen Dateisystem;
* manuelles Erstellen der OSGi-Konfiguration im AEM-Projekt im lokalen Dateisystem und anschließendes Verweisen auf die Eigenschaftsnamen durch den Konfigurations-Manager der AEM-Web-Konsole.

Weitere Informationen zur OSGi-Konfiguration finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).

## Veränderlicher Inhalt {#mutable-content}

Manchmal kann es nützlich sein, Inhaltsänderungen in der Quell-Code-Verwaltung vorzubereiten, damit sie von Cloud Manager bereitgestellt werden können, sobald eine Umgebung aktualisiert wird. Es kann beispielsweise sinnvoll sein, bestimmte Stammordnerstrukturen zu initialisieren. Sie können auch Änderungen in bearbeitbaren Vorlagen anordnen, um Richtlinienkomponenten zu aktivieren, die durch die Anwendungsbereitstellung aktualisiert wurden.

Es gibt zwei Strategien zur Beschreibung der Inhalte, die von Cloud Manager im veränderlichen Repository bereitgestellt werden: veränderliche Inhaltspakete und `repoinit`-Anweisungen.

### Veränderliche Inhaltspakete {#mutable-content-packages}

Inhalte wie Ordnerpfadhierarchien, Service-Benutzer und Zugangssteuerungen (ACLs) werden in der Regel in ein AEM-Projekt übertragen, das auf Maven-Archetypen basiert. Zu den Methoden gehören das Exportieren aus AEM oder das direkte Schreiben als XML. Bei der Erstellung und Bereitstellung packt Cloud Manager das resultierende veränderliche Inhaltspaket. Die veränderbaren Inhalte werden in der Bereitstellungsphase in der Pipeline zu drei verschiedenen Zeitpunkten installiert:

Vor dem Start der neuen Version des Programms:

* Indexdefinitionen (hinzufügen, ändern, entfernen)

Beim Start der neuen Version des Programms, aber vor der Umstellung:

* Service-Benutzer (hinzufügen)
* ACLs für Service-Benutzer (hinzufügen)
* Knotentypen (hinzufügen)

Nach der Umstellung auf die neue Programmversion:

* Alle anderen Inhalte, die über Jackrabbit-Vault definiert werden können. Zum Beispiel:
   * Ordner (hinzufügen, ändern, entfernen)
   * Bearbeitbare Vorlagen (hinzufügen, ändern, entfernen)
   * Kontextsensible Konfiguration (alles unter `/conf`) (hinzufügen, ändern, entfernen)
   * Skripte (Pakete können in verschiedenen Phasen der Paketinstallation Installations-Hooks auslösen). Informationen zu Installations-Hooks finden Sie in der [Jackrabbit Filevault-Dokumentation](https://jackrabbit.apache.org/filevault/installhooks.html). AEM CS verwendet derzeit die Filevault-Version 3.4.0, die die Installations-Hooks für Admin-Benutzende, Systembenutzende und Mitglieder der Administratorgruppe einschränkt.)

Die Installation veränderlicher Inhalte in Autoren- oder Veröffentlichungsinstanzen lässt sich einschränken, indem Sie Pakete unter `/apps` in einen „install.author“- oder „install.publish“-Ordner einbetten. Eine Umstrukturierung, die dieser Trennung Rechnung trägt, wurde in AEM 6.5 vorgenommen. Einzelheiten zur empfohlenen Projektumstrukturierung finden Sie in der [Dokumentation zu AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html?lang=de).

>[!NOTE]
>Inhaltspakete werden für alle Umgebungstypen (dev, stage, prod) bereitgestellt. Die Bereitstellung kann nicht auf eine bestimmte Umgebung beschränkt werden. Diese Einschränkung dient dazu, einen Testlauf der automatischen Ausführung zu ermöglichen. Umgebungsspezifische Inhalte müssen manuell über [Package Manager](/help/implementing/developing/tools/package-manager.md) installiert werden.

Außerdem gibt es kein Verfahren, um Änderungen durch veränderliche Inhaltspakete nach deren Anwendung zurückzunehmen. Wenn Kundinnen oder Kunden ein Problem entdecken, können sie es in ihrer nächsten Code-Version beheben oder – als letzte Möglichkeit – das ganze System auf einen Zeitpunkt vor der Bereitstellung zurücksetzen.

Für alle enthaltenen Pakete von Drittanbietern muss die Kompatibilität mit AEM as a Cloud Service validiert werden, andernfalls führt ihre Einbeziehung zu einem Bereitstellungsfehler.

Wie bereits erwähnt, sollten sich Kundinnen bzw. Kunden mit bestehender Code-Basis an die Umstrukturierung des Repositorys halten, die durch die in der [Dokumentation zu AEM 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html?lang=de) beschriebenen Änderungen des 6.5-Repositorys erforderlich ist.

## Repoinit {#repoinit}

In folgenden Fällen ist es vorzuziehen, in den OSGi-Werkseinstellungen manuell explizite `repoinit`-Anweisungen für die Inhaltserstellung zu kodieren:

* Service-Benutzer erstellen/löschen/deaktivieren
* Gruppen erstellen/löschen
* Benutzer erstellen/löschen
* ACLs hinzufügen

  >[!NOTE]
  >
  >Eine Definition von ACLs erfordert, dass die Knotenstrukturen bereits vorhanden sind. Daher können vorherige Anweisungen zur Pfaderstellung erforderlich sein.

* Pfad hinzufügen (z. B. für Stammordnerstrukturen)
* CNDs hinzufügen (Definitionen für Knotentypen)

Aufgrund der folgenden Vorteile ist bei diesen Anwendungsfällen für die Inhaltsänderung bevorzugt „repoinit“ zu verwenden:

* `Repoinit` erstellt Ressourcen beim Start, sodass Logik die Existenz dieser Ressourcen als selbstverständlich betrachten kann. Beim Ansatz mit veränderlichen Inhaltspaketen werden Ressourcen nach dem Start erstellt, sodass Anwendungs-Code, der auf sie angewiesen ist, fehlschlagen kann.
* `Repoinit` ist ein relativ sicherer Anweisungssatz, da Sie explizit steuern, welche Aktion vorgenommen werden soll. Zudem werden nur additive Vorgänge unterstützt, mit Ausnahme einiger sicherheitsrelevanter Fälle, in denen Benutzende, Dienst-Benutzende und Gruppen entfernt werden können. Dagegen ist eine Entfernung beim Ansatz mit variablen Inhaltspaketen explizit. Wenn Sie einen Filter definieren, werden alle von einem Filter derzeit erfassten Elemente gelöscht. Dennoch ist Vorsicht geboten, da es bei jedem Inhalt Szenarien geben kann, in denen die Existenz neuer Inhalte das Verhalten des Programms verändert.
* `Repoinit` sorgt für schnelle und atomische Operationen. Veränderliche Inhaltspakete hingegen können stark von der Leistung der Strukturen abhängen, die von einem Filter abgedeckt werden. Auch wenn Sie nur einen Knoten aktualisieren, wird ggf. ein Schnappschuss einer großen Baumstruktur erstellt.
* `repoinit`-Anweisungen können in einer lokalen Entwicklungsumgebung zur Laufzeit überprüft werden, da sie bei der Registrierung der OSGi-Konfiguration ausgeführt werden.
* `Repoinit`-Anweisungen sind atomisch und explizit und werden übersprungen, wenn der Status bereits übereinstimmt.

Wenn Cloud Manager das Programm bereitstellt, werden diese Anweisungen unabhängig von der Installation jeglicher Inhaltspakete ausgeführt.

Gehen Sie wie folgt vor, um weitere `repoinit`-Anweisungen zu erstellen:

1. Fügen Sie die OSGi-Konfiguration für werksmäßige PID `org.apache.sling.jcr.repoinit.RepositoryInitializer` in einem Konfigurationsordner des Projekts hinzu. Verwenden Sie einen beschreibenden Namen für die Konfiguration wie **org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure**.
1. Fügen Sie `repoinit`-Anweisungen in die Skript-Eigenschaft der Konfiguration ein. Syntax und Optionen werden in der [Sling-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html) beschrieben. Es sollte vor den untergeordneten Ordnern ausdrücklich ein übergeordneter Ordner erstellt werden. Beispielsweise ist eine explizite Erstellung von `/content` vor `/content/myfolder` und von letzterem vor `/content/myfolder/mysubfolder` erforderlich. Bei ACLs, die für untergeordnete Strukturen festgelegt werden, wird empfohlen, diese auf einer höheren Ebene festzulegen und eine Einschränkung `rep:glob` zu verwenden. Beispiel: `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. Validieren Sie zur Laufzeit in der lokalen Entwicklungsumgebung.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Bei ACLs, die für Knoten unterhalb von `/apps` oder `/libs` bzw. `repoinit` definiert sind, beginnt die Ausführung in einem leeren Repository. Die Pakete werden nach `repoinit` installiert. Das bedeutet, dass Anweisungen sich auf nichts verlassen können, was in den Paketen definiert ist, sondern Vorbedingungen wie die übergeordneten Strukturen darunter definieren müssen.

>[!TIP]
>
>Bei ACLs kann die Erstellung tiefer Strukturen umständlich sein. Daher ist es sinnvoller, eine ACL auf einer höheren Ebene zu definieren und dann durch eine Einschränkung `rep:glob` zu begrenzen, wo sie wirken soll.

Weitere Einzelheiten über `repoinit` finden Sie in der [Sling-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Package Manager-„one-offs“ für Pakete mit veränderlichen Inhalten {#package-manager-oneoffs-for-mutable-content-packages}

>[!CONTEXTUALHELP]
>id="aemcloud_packagemanager"
>title="Package Manager – Migrieren von Packages mit veränderlichen Inhalten"
>abstract="Erkunden Sie die Verwendung von Package Manager für Anwendungsfälle, in denen ein Inhaltspaket als „einmalig“ installiert werden soll. Die Installation umfasst den Import spezifischer Inhalte aus der Produktionsumgebung in die Staging-Umgebung, um ein Produktionsproblem zu debuggen, die Übertragung eines kleinen Inhaltspakets aus einer On-Premise-Umgebung in eine AEM Cloud-Umgebung und mehr."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de" text="Content Transfer Tool"

Es gibt Anwendungsfälle, in denen ein Inhaltspaket als „one off“ (einmalig) installiert werden sollte. Zum Beispiel beim Importieren bestimmter Inhalte aus der Produktions- in die Staging-Umgebung, um ein Problem in der Produktion zu debuggen. Für solche Szenarien kann [Package Manager](/help/implementing/developing/tools/package-manager.md) in Umgebungen mit AEM as a Cloud Service verwendet werden.

Da Package Manager auf einem Laufzeitkonzept basiert, ist es unmöglich, Inhalte oder Code im unveränderlichen Repository zu installieren. Daher dürfen diese Inhaltspakete nur aus veränderlichen Inhalten bestehen (hauptsächlich `/content` oder `/conf`). Wenn das Inhaltspaket gemischte Inhalte enthält, d. h. sowohl veränderliche als auch unveränderliche, werden nur die veränderlichen Inhalte installiert.

>[!IMPORTANT]
>
>Die Benutzeroberfläche von Package Manager gibt möglicherweise die Fehlermeldung **undefiniert** zurück, wenn die Installation eines Pakets länger als zehn Minuten dauert.
>
>Diese Zeit ist nicht auf einen Installationsfehler zurückzuführen, sondern auf eine Zeitüberschreitung, die es bei Cloud Service für alle Anfragen gibt.
>
>Wiederholen Sie die Installation nicht, wenn ein solcher Fehler auftritt. Die Installation wird im Hintergrund korrekt ausgeführt. Würden Sie die Installation neu starten, könnten Konflikte durch mehrere gleichzeitige Importprozesse entstehen.

Sämtliche über Cloud Manager installierten Inhaltspakete (sowohl veränderliche als auch unveränderliche) werden in der Benutzeroberfläche von AEM Package Manager mit einem eingefrorenen Status angezeigt. Diese Pakete können nicht neu installiert, neu erstellt oder auch nur heruntergeladen werden. Sie werden mit dem Suffix **cp2fm** aufgeführt, was darauf hinweist, dass ihre Installation von Cloud Manager verwaltet wurde.

### Einschließen von Drittanbieterpaketen {#including-third-party}

Es kommt häufig vor, dass Kundinnen und Kunden vorgefertigte Pakete aus Drittanbieterquellen (zum Beispiel von Software-Anbietern wie Übersetzungspartnern von Adobe) einbeziehen. Es wird empfohlen, diese Pakete in einem Remote-Repository zu hosten und in `pom.xml` auf sie zu verweisen. Diese Methode ist für öffentliche Repositorys und auch für private Repositorys mit Kennwortschutz möglich, wie unter [Unterstützung für kennwortgeschützte Maven-Repositorys](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories) beschrieben.

Wenn das Speichern des Pakets in einem Remote-Repository nicht möglich ist, können Kundinnen und Kunden es in einem lokalen, Dateisystem-basierten Maven-Repository platzieren, das im Rahmen des Projekts an SCM übermittelt wird. Es wird durch alles, was davon abhängig ist, referenziert. Das Repository wird in diesem Fall wie im nachfolgend dargestellten POM des Projekts deklariert:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Alle enthaltenen Drittanbieter-Pakete müssen den in diesem Artikel beschriebenen Richtlinien zur Codierung und Verpackung für AEM as a Cloud Service entsprechen. Andernfalls entsteht ein Implementierungsfehler.

Das folgende Maven-Fragment `POM.xml` zeigt, wie Drittanbeiter-Pakete über die Maven-Plug-in-Konfiguration **filevault-package-maven-plugin** in das „Container“-Paket des Projekts, in der Regel **„all“** genannt, eingebettet werden können.

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

Genauso wie AEM-Aktualisierungen werden benutzerspezifische Versionen mithilfe einer rollierenden Implementierungsstrategie bereitgestellt, um unter den richtigen Bedingungen Ausfallzeiten im Author-Cluster zu verhindern. Die allgemeine Ereignisabfolge, in der Knoten mit der alten und der neuen Version des Kunden-Codes dieselbe Version des AEM-Codes ausführen, wird unten beschrieben.

* Knoten mit der alten Version sind aktiv, und ein Freigabekandidat für die neue Version wird erstellt und verfügbar gemacht.
* Wenn neue oder aktualisierte Indexdefinitionen vorhanden sind, werden die entsprechenden Indizes verarbeitet. Knoten mit der alten Version verwenden immer die alten Indizes, während Knoten mit der neuen Version immer die neuen Indizes verwenden.
* Die Knoten mit der neuen Version werden in Betrieb genommen, während die alten Versionen weiterhin den Traffic versorgen.
* Knoten mit der alten Version werden ausgeführt und arbeiten weiterhin, während Knoten mit der neuen Version mithilfe von Konsistenzprüfungen auf ihre Bereitschaft überprüft werden.
* Knoten mit der neuen Version, die bereit sind, nehmen den Traffic an und ersetzen die Knoten mit der alten Version, die heruntergefahren werden.
* Im Laufe der Zeit werden die Knoten mit der alten Version durch Knoten mit der neuen Version ersetzt, bis nur noch Knoten mit neuen Versionen verbleiben, sodass die Bereitstellung abgeschlossen ist.
* Alle neuen oder geänderten veränderlichen Inhalte werden dann bereitgestellt.

## Indizes {#indexes}

Neue oder geänderte Indizes verursachen einen zusätzlichen Indizierungs- oder Neuindizierungsschritt, bevor die neue Version den Traffic aufnehmen kann. Details zur Indexverwaltung in AEM as a Cloud Service finden Sie in unter [Inhaltssuche und -indizierung](/help/operations/indexing.md).  Sie können den Indizierungsstatus von Build-Seiten in Cloud Manager überprüfen und eine Benachrichtigung erhalten, wenn die neue Version für Traffic bereit ist.

>[!NOTE]
>
>Die für eine rollierende Bereitstellung benötigte Zeit hängt von der Größe des Index ab. Der Grund dafür ist, dass die neue Version Traffic erst akzeptieren kann, wenn der neue Index generiert wurde.

Derzeit funktioniert AEM as a Cloud Service nicht mit Indexverwaltungs-Tools wie dem ACS Commons Ensure Oak Index-Tool.

## Replikation {#replication}

Der Veröffentlichungsmechanismus ist rückwärtskompatibel mit den [AEM Replication Java™-APIs](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de).

Um mit Replikation und dem Cloud-fähigen AEM-Schnellstart entwickeln und testen zu können, müssen die klassischen Replikationsfunktionen in einem Author/Publish-Setup verwendet werden. Wenn der Einstiegspunkt der Benutzeroberfläche auf AEM Author für die Cloud entfernt wird, gehen die Benutzenden für die Konfiguration zu `http://localhost:4502/etc/replication`.

## Rückwärtskompatibler Code für rollierende Bereitstellungen {#backwards-compatible-code-for-rolling-deployments}

Wie oben erläutert, beinhaltet die kontinuierliche Bereitstellungsstrategie von AEM as a Cloud Service, dass sich sowohl die alten als auch die neuen Versionen gleichzeitig ausführen lassen. Seien Sie daher vorsichtig bei Code-Änderungen, die nicht rückwärtskompatibel mit der alten, weiter verwendeten AEM-Version sind.

Darüber hinaus sollte die alte Version auf Kompatibilität mit allen neuen Strukturen für veränderliche Inhalte getestet werden, die von der neuen Version angewendet werden, wenn ein Rollback stattfindet, da veränderliche Inhalte nicht entfernt werden.

### Änderungen von Dienstbenutzenden und ACLs {#service-users-and-acl-changes}

Das Ändern von Dienstbenutzenden oder ACLs, die auf Inhalte oder Code zugreifen, kann zu Fehlern in den älteren AEM-Versionen führen, die den Zugriff auf diese Inhalte oder den Code mit veralteten Dienstbenutzenden zur Folge haben. Um diesem Verhalten entgegenzuwirken, wird empfohlen, die Änderungen auf mindestens zwei Versionen zu verteilen, wobei die erste Version als Bindeglied fungiert, bevor in der folgenden Version bereinigt wird.

### Indexänderungen {#index-changes}

Bei Änderungen an Indizes ist es wichtig, dass die alte Version ihre Indizes bis zum Ende weiter verwendet, während die neue Version ihre eigenen geänderten Indizes nutzt. Die Entwicklerinnen und Entwickler sollten die Indexverwaltungsmethoden befolgen, die unter [Inhaltssuche und -indizierung](/help/operations/indexing.md) beschrieben sind.

### Konservative Codierung für Rollbacks {#conservative-coding-for-rollbacks}

Wenn nach der Bereitstellung ein Fehler gemeldet oder erkannt wird, ist möglicherweise ein Rollback zur alten Version erforderlich. Stellen Sie sicher, dass der neue Code mit allen neuen Strukturen kompatibel ist, die von dieser neuen Version erstellt wurden, da die neuen Strukturen (alle veränderlichen Inhalte) nicht zurückgesetzt werden. Wenn der alte Code nicht kompatibel ist, müssen die Korrekturen in späteren Kundenversionen vorgenommen werden.

## Schnelle Entwicklungsumgebung (RDE) {#rde}

[Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md) (oder kurz: RDEs) ermöglichen es Entwicklerinnen und Entwicklern, Änderungen schnell bereitzustellen und zu überprüfen und so den Zeitaufwand für das Testen von Funktionen zu minimieren, die bereits nachweislich in einer lokalen Entwicklungsumgebung funktionieren.

Im Gegensatz zu normalen Entwicklungsumgebungen, die Code über die Cloud Manager-Pipeline bereitstellen, verwenden Entwicklerinnen und Entwickler Befehlszeilen-Tools, um Code aus einer lokalen Entwicklungsumgebung mit der RDE zu synchronisieren. Nachdem die Änderungen erfolgreich in einer RDE getestet wurden, stellen Sie sie über die Cloud Manager-Pipeline in einer regulären Cloud-Entwicklungsumgebung bereit, wodurch der Code die entsprechenden Qualitätsprüfungen durchläuft.

## Ausführungsmodi {#runmodes}

In bestehenden AEM-Lösungen haben Kundinnen und Kunden die Möglichkeit, Instanzen mit beliebigen Ausführungsmodi auszuführen und OSGi-Konfigurationen anzuwenden oder OSGi-Pakete in diesen spezifischen Instanzen zu installieren. Zu den definierten Ausführungsmodi gehören normalerweise der *Service* (Autor und Veröffentlichen) sowie die Umgebung (RDE, dev, stage, prod).

AEM as a Cloud Service hingegen ist eigenwilliger bezüglich der Frage, welche Ausführungsmodi verfügbar sind und wie ihnen OSGi-Pakete und OSGi-Konfigurationen zugeordnet werden können:

* Die OSGI-Konfigurationslaufmodi müssen auf die RDE-, Entwicklungs-, Staging-, Produktions-Umgebung oder auf Author und Publish für den Service verweisen. Es wird eine Kombination aus `<service>.<environment_type>` unterstützt, wobei diese Umgebungen genau in dieser bestimmten Reihenfolge verwendet werden müssen (z. B. `author.dev` oder `publish.prod`). Die OSGI-Token sollten direkt aus dem Code referenziert werden, anstatt die `getRunModes`-Methode zu verwenden, die den `environment_type` zur Laufzeit nicht mehr enthält. Weitere Informationen finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).
* Die Ausführungsmodi von OSGi-Bundles sind auf den Service (author, publish) beschränkt. OSGi-Pakete für den Pre-Run-Modus sollten im Inhaltspaket unter `install.author` oder `install.publish` installiert werden.

AEM as a Cloud Service lässt die Verwendung von Ausführungsmodi nicht zu, um Inhalte für bestimmte Umgebungen oder Dienste zu installieren. Wenn eine Entwicklungsumgebung mit Daten oder HTML-Dateien bestückt werden muss, die sich nicht in der Staging- oder Produktionsumgebung befinden, kann Package Manager verwendet werden.

Folgende Konfigurationen für den Ausführungsmodus werden unterstützt:

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

Bei der lokalen Entwicklung wird ein Ausführungsmodus-Startparameter `-r` verwendet, um die OSGi-Konfiguration für den Ausführungsmodus anzugeben.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Konfiguration von Wartungsaufgaben in der Quell-Code-Verwaltung {#maintenance-tasks-configuration-in-source-control}

Die Konfiguration von Wartungsaufgaben muss in der Quell-Code-Verwaltung persistiert werden, da der Bildschirm **Tools > Vorgänge** in Cloud-Umgebungen nicht mehr verfügbar ist. Dadurch wird sichergestellt, dass Änderungen vorsätzlich persistiert werden, anstatt reaktiv angewendet und dann vergessen zu werden. Weitere Informationen finden Sie unter [Wartungsaufgaben in AEM as a Cloud Service](/help/operations/maintenance.md).
