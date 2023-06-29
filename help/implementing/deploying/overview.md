---
title: Bereitstellen für AEM as a Cloud Service
description: Bereitstellen für AEM as a Cloud Service
feature: Deploying
exl-id: 7fafd417-a53f-4909-8fa4-07bdb421484e
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '3462'
ht-degree: 40%

---

# Bereitstellen für AEM as a Cloud Service {#deploying-to-aem-as-a-cloud-service}

## Einführung {#introduction}

Die Grundlagen der Code-Entwicklung in AEM as a Cloud Service ähneln denen von AEM On-Premise- und Managed Services-Lösungen. Entwickler schreiben Code und testen ihn lokal, der dann auf AEM as a Cloud Service Remote-Umgebungen gesendet wird. Dafür wird Cloud Manager benötigt, das ein optionales Tool zur Inhaltsbereitstellung für Managed Services war. Dieses Bereitstellungswerkzeug ist jetzt der einzige Mechanismus zur Bereitstellung von Code in AEM as a Cloud Service Entwicklungs-, Staging- und Produktionsumgebungen. Für die schnelle Überprüfung und das Debugging von Funktionen vor der Bereitstellung der zuvor erwähnten Umgebungen kann Code aus einer lokalen Umgebung in eine [Schnelle Entwicklungsumgebung](/help/implementing/developing/introduction/rapid-development-environments.md).

Die Aktualisierung der [AEM-Version](/help/implementing/deploying/aem-version-updates.md) ist stets ein separates Bereitstellungsereignis, das nicht mit dem Pushen von [anwenderspezifischem Code](#customer-releases) verbunden ist. Anders gesagt, sollten Versionen von benutzerspezifischem Code mit der AEM Version getestet werden, die sich in der Produktion befindet, da diese Version oben bereitgestellt wird. AEM Aktualisierungen der Version, die danach stattfinden und häufig auftreten und automatisch angewendet werden. Sie sollen abwärtskompatibel mit dem bereits bereitgestellten anwenderpezifischen Code sein.

Im Rest dieses Dokuments wird beschrieben, wie Entwickler ihre Vorgehensweisen anpassen sollten, damit sie sowohl mit AEM Versionsaktualisierungen von as a Cloud Service als auch mit Kundenaktualisierungen arbeiten.

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html).
-->

## Benutzerspezifische Versionen {#customer-releases}

### Kodierung mit der richtigen AEM-Version {#coding-against-the-right-aem-version}

Bei früheren AEM-Lösungen änderte sich die aktuelle AEM-Version selten (etwa 1-mal jährlich mit vierteljährlichen Service Packs); Kunden aktualisierten die Produktionsinstanzen im eigenen Tempo auf den neuesten Schnellstart, indem sie auf das API-JAR verwiesen. Anwendungen auf AEM as a Cloud Service werden jedoch häufiger automatisch auf die neueste Version von AEM aktualisiert. Daher sollte benutzerspezifischer Code für interne Versionen mit der neuesten AEM Version erstellt werden.

Wie bei bestehenden Nicht-Cloud-AEM-Versionen wird eine lokale, Offline-Entwicklung unterstützt, die auf einem bestimmten Schnellstart basiert. Es wird erwartet, dass sie für das Debugging in der Regel das bevorzugte Tool ist.

>[!NOTE]
>Beim Verhalten des Programms gibt es geringfügige Unterschiede zwischen einem lokalen Computer und der Adobe Cloud. Diese architektonischen Unterschiede müssen bei der lokalen Entwicklung berücksichtigt werden und können bei Bereitstellung in der Cloud-Infrastruktur ggf. zu einem anderen Verhalten führen. Aufgrund dieser Unterschiede ist es wichtig, umfassende Tests für Entwicklungs- und Staging-Umgebungen durchzuführen, bevor neuer benutzerdefinierter Code in der Produktion eingeführt wird.

Um benutzerdefinierten Code für eine interne Version zu entwickeln, muss die entsprechende Version der [AEM as a Cloud Service SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md) heruntergeladen und installiert werden. Weitere Informationen zur Verwendung der AEM as a Cloud Service-Dispatcher-Tools finden Sie auf [dieser Seite](/help/implementing/dispatcher/disp-overview.md).

Das folgende Video bietet einen allgemeinen Überblick darüber, wie Sie Code für AEM as a Cloud Service bereitstellen:

>[!VIDEO](https://video.tv.adobe.com/v/30191?quality=9)

<!--
>[!NOTE]
>It is recommended for customers with existing code bases, to go through the repository restructuring exercise described in the [AEM documentation](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/authoring/restructure.html). 
-->

## Bereitstellen von Inhaltspaketen über Cloud Manager und Package Manager {#deploying-content-packages-via-cloud-manager-and-package-manager}

### Implementierungen über Cloud Manager {#deployments-via-cloud-manager}

<!-- Alexandru: temporarily commenting this out, until I get some clarification from Brian 

![image](https://git.corp.adobe.com/storage/user/9001/files/e91b880e-226c-4d5a-93e0-ae5c3d6685c8) -->

Kunden können benutzerspezifischen Code in Cloud-Umgebungen über Cloud Manager bereitstellen. Cloud Manager wandelt lokal assemblierte Inhaltspakete in ein Artefakt um, das dem Sling-Funktionsmodell entspricht. So wird eine Anwendung auf AEM as a Cloud Service Seite beschrieben, wenn sie in einer Cloud-Umgebung ausgeführt wird. Daher sollten Sie die Pakete in [Package Manager](/help/implementing/developing/tools/package-manager.md) In Cloud-Umgebungen enthält der Name &quot;cp2fm&quot;und die transformierten Pakete haben alle Metadaten entfernt. Mit ihnen kann nicht interagiert werden; d. h. sie lassen nicht herunterladen, replizieren oder öffnen. Eine ausführliche Dokumentation zum Konvertierer finden Sie [hier](https://github.com/apache/sling-org-apache-sling-feature-cpconverter).

Inhaltspakete, die für Anwendungen in AEM as a Cloud Service Anwendungen geschrieben wurden, müssen eine saubere Trennung zwischen unveränderlichem und veränderlichem Inhalt aufweisen. Cloud Manager installiert nur den veränderlichen Inhalt und gibt außerdem eine Meldung wie die folgende aus:

`Generated content-package <PACKAGE_ID> located in file <PATH> is of MIXED type`

Der Rest dieses Abschnitts beschreibt die Zusammensetzung und Implikationen unveränderlicher und veränderlicher Pakete.

### Unveränderliche Inhaltspakete {#immutabe-content-packages}

Sämtlicher Inhalt und Code, der im unveränderlichen Repository persistent ist, muss in Git eingecheckt und mit Cloud Manager bereitgestellt werden. Anders gesagt: Im Gegensatz zu aktuellen AEM-Lösungen wird Code niemals direkt in einer laufenden AEM-Instanz bereitgestellt. Dieser Workflow stellt sicher, dass der Code, der für eine bestimmte Version in einer Cloud-Umgebung ausgeführt wird, identisch ist, was das Risiko unbeabsichtigter Codevarianten in der Produktion eliminiert. Beispielsweise sollte die OSGi-Konfiguration über den Konfigurations-Manager der AEM Web-Konsole an die Quell-Code-Verwaltung übergeben und nicht zur Laufzeit verwaltet werden.

Da Anwendungsänderungen aufgrund des Bereitstellungsmusters durch einen Schalter aktiviert werden, können sie nicht von Änderungen im veränderlichen Repository abhängig sein, außer für Dienstbenutzer, ihre ACLs, Knotentypen und Änderungen der Indexdefinition.

Kunden mit vorhandener Code-Basis müssen die in der AEM-Dokumentation beschriebene Repository-Umstrukturierung durchführen, um dafür zu sorgen, dass zuvor unter „/etc“ befindliche Inhalte an den richtigen Speicherort verschoben werden.

Für diese Code-Pakete gelten einige zusätzliche Einschränkungen, z. B. werden keine [Install Hooks](https://jackrabbit.apache.org/filevault/installhooks.html) unterstützt.

## OSGi-Konfiguration {#osgi-configuration}

Wie bereits erwähnt, sollte die OSGi-Konfiguration an die Quell-Code-Verwaltung übermittelt werden und nicht über die Web-Konsole. Zu geeigneten Verfahren gehören:

* Vornehmen der erforderlichen Änderungen in der lokalen AEM-Umgebung des Entwicklers mit dem Konfigurations-Manager der AEM-Web-Konsole und anschließendes Exportieren der Ergebnisse in das AEM-Projekt im lokalen Dateisystem;
* manuelles Erstellen der OSGi-Konfiguration im AEM-Projekt im lokalen Dateisystem und anschließendes Verweisen auf die Eigenschaftsnamen durch den Konfigurations-Manager der AEM-Web-Konsole.

Weitere Informationen zur OSGi-Konfiguration finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).

## Veränderlicher Inhalt {#mutable-content}

Manchmal kann es nützlich sein, Inhaltsänderungen in der Quell-Code-Verwaltung vorzubereiten, damit sie von Cloud Manager bereitgestellt werden können, sobald eine Umgebung aktualisiert wurde. Es kann beispielsweise sinnvoll sein, bestimmte Stammordnerstrukturen zu testen. Oder ordnen Sie Änderungen in bearbeitbaren Vorlagen an, um Richtlinienkomponenten zu aktivieren, die von der Anwendungsimplementierung aktualisiert wurden.

Es gibt zwei Strategien zur Beschreibung des Inhalts, der von Cloud Manager im veränderlichen Repository bereitgestellt wird: veränderliche Inhaltspakete und `repoinit` -Anweisungen.

### Veränderliche Inhaltspakete {#mutable-content-packages}

Inhalte wie Ordnerpfadhierarchien, Service-Benutzer und Zugangssteuerungen (ACLs) werden in der Regel in ein AEM-Projekt übertragen, das auf Maven-Archetypen basiert. Zu den Methoden gehören das Exportieren aus AEM oder das direkte Schreiben als XML. Bei der Erstellung und Bereitstellung packt Cloud Manager das resultierende veränderliche Inhaltspaket. Der veränderliche Inhalt wird während der Bereitstellungsphase in der Pipeline dreimal installiert:

Vor dem Start der neuen Version des Programms:

* Indexdefinitionen (hinzufügen, ändern, entfernen)

Beim Start der neuen Version des Programms, aber vor der Umstellung:

* Service-Benutzer (hinzufügen)
* ACLs für Service-Benutzer (hinzufügen)
* Knotentypen (hinzufügen)

Nach der Umstellung auf die neue Programmversion:

* Alle anderen Inhalte, die über Jackrabbit Vault definiert werden können. Beispiel:
   * Ordner (hinzufügen, ändern, entfernen)
   * Bearbeitbare Vorlagen (hinzufügen, ändern, entfernen)
   * Kontextsensible Konfiguration (alles unter `/conf`) (hinzufügen, ändern, entfernen)
   * Skripte (Pakete können in verschiedenen Phasen der Paketinstallation Installationshaken auslösen. Siehe [Jackrabbit filevault-Dokumentation](https://jackrabbit.apache.org/filevault/installhooks.html) über Installationshaken. AEM CS verwendet derzeit die Filevault-Version 3.4.0, die Installations-Hooks für Admin-Benutzer, Systembenutzer und Mitglieder der Administratorgruppe einschränkt).

Die Installation veränderlicher Inhalte in Autoren- oder Veröffentlichungsinstanzen lässt sich einschränken, indem Sie Pakete unter `/apps` in einen „install.author“- oder „install.publish“-Ordner einbetten. Eine Umstrukturierung, die dieser Trennung Rechnung trägt, wurde in AEM 6.5 vorgenommen. Einzelheiten zur empfohlenen Projektumstrukturierung finden Sie in der [Dokumentation zu AEM 6.5.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html?lang=de)

>[!NOTE]
>Inhaltspakete werden für alle Umgebungstypen (dev, stage, prod) bereitgestellt. Die Bereitstellung kann nicht auf eine bestimmte Umgebung beschränkt werden. Diese Einschränkung dient dazu, einen Testlauf der automatischen Ausführung zu ermöglichen. Umgebungsspezifische Inhalte müssen manuell installiert werden. [Package Manager](/help/implementing/developing/tools/package-manager.md).

Außerdem gibt es keinen Mechanismus, um die Änderungen an veränderlichen Inhaltspaketen nach deren Anwendung rückgängig zu machen. Wenn Kunden ein Problem entdecken, können sie es in ihrer nächsten Code-Version beheben oder – als letzte Möglichkeit – das ganze System auf einen Zeitpunkt vor der Bereitstellung zurücksetzen.

Alle enthaltenen Pakete von Drittanbietern müssen als AEM as a Cloud Service kompatibel validiert werden. Andernfalls führt ihre Einbeziehung zu einem Implementierungsfehler.

Wie oben erwähnt, sollten Kunden mit vorhandener Code-Basis die Repository-Umstrukturierung durchführen, die für die 6.5 Repository-Änderungen erforderlich ist, die im Abschnitt [AEM 6.5 Dokumentation.](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/restructuring/repository-restructuring.html?lang=de)

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

* `Repoinit` erstellt Ressourcen beim Start, sodass Logik die Existenz dieser Ressourcen als selbstverständlich betrachten kann. Beim Ansatz mit veränderlichen Inhaltspaketen werden Ressourcen nach dem Start erstellt, sodass Anwendungs-Code, der auf sie angewiesen ist, fehlschlagen kann.
* `Repoinit` ist ein relativ sicherer Anweisungssatz, da Sie explizit steuern, welche Aktion vorgenommen werden soll. Außerdem werden nur additive Vorgänge unterstützt, mit Ausnahme einiger sicherheitsrelevanter Fälle, in denen Benutzer, Dienstbenutzer und Gruppen entfernt werden können. Im Gegensatz dazu ist die Entfernung von etwas im Ansatz für veränderliche Inhaltspakete explizit. Wenn Sie einen Filter definieren, werden alle von einem Filter erfassten Elemente gelöscht. Dennoch ist Vorsicht geboten, da es bei jedem Inhalt Szenarien geben kann, in denen die Existenz neuer Inhalte das Verhalten des Programms verändert.
* `Repoinit` sorgt für schnelle und atomische Operationen. Veränderliche Inhaltspakete hingegen können stark von der Leistung der Strukturen abhängen, die von einem Filter abgedeckt werden. Auch wenn Sie nur einen Knoten aktualisieren, wird ggf. ein Schnappschuss einer großen Baumstruktur erstellt.
* Es ist möglich, `repoinit` -Anweisungen zur Laufzeit in einer lokalen Entwicklungsumgebung ausführen, da sie bei der Registrierung der OSGi-Konfiguration ausgeführt werden.
* `Repoinit` -Anweisungen sind atomisch und explizit und werden übersprungen, wenn der Status bereits übereinstimmt.

Wenn Cloud Manager das Programm bereitstellt, werden diese Anweisungen unabhängig von der Installation jeglicher Inhaltspakete ausgeführt.

Erstellen `repoinit` Anweisungen, folgen Sie dem folgenden Verfahren:

1. Fügen Sie die OSGi-Konfiguration für werksmäßige PID `org.apache.sling.jcr.repoinit.RepositoryInitializer` in einem Konfigurationsordner des Projekts hinzu. Verwenden Sie einen beschreibenden Namen für die Konfiguration wie **org.apache.sling.jcr.repoinit.RepositoryInitializer~initstructure**.
1. Hinzufügen `repoinit` -Anweisungen zur Skripteigenschaft der config. Syntax und Optionen werden in der [Sling-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html) beschrieben. Vor den untergeordneten Ordnern sollte explizit ein übergeordneter Ordner erstellt werden. Beispielsweise ist eine explizite Erstellung von `/content` vor `/content/myfolder` und vor `/content/myfolder/mysubfolder` erforderlich. Für ACLs, die auf untergeordnete Strukturen festgelegt werden, wird empfohlen, sie auf einer höheren Ebene festzulegen und mit einer `rep:glob` Beschränkung. Beispiel: `(allow jcr:read on /apps restriction(rep:glob,/msm/wcm/rolloutconfigs))`.
1. Validieren Sie zur Laufzeit in der lokalen Entwicklungsumgebung.

<!-- last statement in step 2 to be clarified with Brian -->

>[!WARNING]
>
>Für ACLs, die für Knoten unter definiert sind `/apps` oder `/libs` die `repoinit`, beginnt die Ausführung in einem leeren Repository. Die Pakete werden nach installiert `repoinit` -Anweisungen können sich auf nichts verlassen, was in den Paketen definiert ist, sondern müssen die Bedingungen wie die übergeordneten Strukturen darunter definieren.

>[!TIP]
>
>Bei ACLs kann die Erstellung tiefer Strukturen umständlich sein. Daher ist es vernünftiger, eine ACL auf einer höheren Ebene zu definieren und zu beschränken, wo sie handeln soll, indem sie `rep:glob` Beschränkung.

Weitere Informationen `repoinit` finden Sie im Abschnitt [Sling-Dokumentation](https://sling.apache.org/documentation/bundles/repository-initialization.html)

<!-- ### Packaging of Immutable and Mutable Packages {#packaging-of-immutable-and-mutable-packages}

above appears to be internal, to confirm with Brian -->

### Package Manager-„one-offs“ für Pakete mit veränderlichen Inhalten {#package-manager-oneoffs-for-mutable-content-packages}

>[!CONTEXTUALHELP]
>id="aemcloud_packagemanager"
>title="Package Manager – Migrieren von Packages mit veränderlichen Inhalten"
>abstract="Erkunden Sie die Verwendung von Package Manager für Anwendungsfälle, in denen ein Inhaltspaket als &quot;einmalig&quot;installiert werden soll. Die Installation umfasst den Import spezifischer Inhalte aus der Produktion in die Staging-Umgebung, um ein Produktionsproblem zu beheben, die Übertragung kleiner Inhaltspakete von der On-Premise-Umgebung auf AEM Cloud-Umgebungen und mehr."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=en" text="Content Transfer Tool"

Es gibt Anwendungsfälle, in denen ein Inhaltspaket als „one off“ (einmalig) installiert werden sollte. Wenn Sie beispielsweise bestimmte Inhalte aus der Produktion in die Staging-Umgebung importieren, um ein Produktionsproblem zu beheben. Für diese Szenarien gilt Folgendes: [Package Manager](/help/implementing/developing/tools/package-manager.md) kann in Umgebungen auf AEM as a Cloud Service verwendet werden.

Da Package Manager auf einem Laufzeitkonzept basiert, ist es unmöglich, Inhalte oder Code im unveränderlichen Repository zu installieren. Daher dürfen diese Inhaltspakete nur aus veränderlichen Inhalten bestehen (hauptsächlich `/content` oder `/conf`). Wenn das Inhaltspaket gemischte Inhalte enthält (sowohl veränderliche als auch unveränderliche Inhalte), wird nur der veränderliche Inhalt installiert.

>[!IMPORTANT]
>
>Die Benutzeroberfläche von Package Manager gibt möglicherweise eine **undefined** Fehlermeldung, wenn die Installation eines Pakets länger als zehn Minuten dauert.
>
>Diese Zeit ist nicht auf einen Installationsfehler zurückzuführen, sondern auf eine Zeitüberschreitung, die der Cloud Service für alle Anforderungen hat.
>
>Wiederholen Sie die Installation nicht, wenn ein solcher Fehler auftritt. Die Installation wird im Hintergrund korrekt ausgeführt. Wenn Sie die Installation neu starten, können einige Konflikte durch mehrere gleichzeitige Importprozesse verursacht werden.

Alle Inhaltspakete, die über Cloud Manager installiert werden (sowohl veränderliche als auch unveränderliche), werden in AEM Benutzeroberfläche von Package Manager mit einem eingefrorenen Status angezeigt. Diese Pakete können nicht neu installiert, neu erstellt oder sogar heruntergeladen werden und werden mit einer **&quot;cp2fm&quot;** -Suffix, das angibt, dass ihre Installation von Cloud Manager verwaltet wurde.

### Einschließen von Drittanbieterpaketen {#including-third-party}

Es ist üblich, dass Kunden vorgefertigte Pakete aus Drittanbieterquellen wie Software-Anbietern wie Übersetzungspartnern von Adobe einbeziehen. Es wird empfohlen, diese Pakete in einem Remote-Repository zu hosten und in `pom.xml` auf sie zu verweisen. Diese Methode ist für öffentliche Repositorys und auch für private Repositorys mit Kennwortschutz möglich, wie unter [Kennwortgeschützte Maven-Repositorys](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/setting-up-project.md#password-protected-maven-repositories).

Wenn das Speichern des Pakets in einem Remote-Repository nicht möglich ist, können Kunden es in einem lokalen, dateisystembasierten Maven-Repository platzieren, das im Rahmen des Projekts an SCM übermittelt wird. Sie wird durch das, was immer davon abhängig ist, referenziert. Das Repository wird wie unten dargestellt im Projekt-POM deklariert:


```
<repository>
    <id>project.local</id>
    <name>project</name>
    <url>file:${maven.multiModuleProjectDirectory}/repository</url>
</repository>
```

<!-- formatting appears broken in the code sample above, check how it appears on AEM -->

Alle enthaltenen Pakete von Drittanbietern müssen den in diesem Artikel beschriebenen as a Cloud Service Richtlinien für Kodierung und Verpackung entsprechen, da andernfalls deren Einbeziehung zu einem Implementierungsfehler führt.

Der folgende Maven `POM.xml` Ein Ausschnitt zeigt, wie Pakete von Drittanbietern in das &quot;Container&quot;-Paket des Projekts eingebettet werden können, normalerweise mit dem Namen **&#39;all&#39;** durch die **filevault-package-maven-plugin** Maven-Plug-in-Konfiguration.

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
* Wenn neue oder aktualisierte Indexdefinitionen vorhanden sind, werden die entsprechenden Indizes verarbeitet. Knoten mit der alten Version verwenden immer die alten Indizes, während Knoten mit der neuen Version immer die neuen Indizes verwenden.
* Knoten mit der neuen Version starten, während alte Versionen weiterhin Traffic bereitstellen.
* Knoten mit der alten Version werden ausgeführt und bedienen weiterhin, während Knoten mit der neuen Version mithilfe von Konsistenzprüfungen auf ihre Bereitschaft überprüft werden.
* Knoten mit der neuen Version, die bereit sind, Traffic akzeptieren und die Knoten durch die alte Version ersetzen, die heruntergefahren wird.
* Im Laufe der Zeit werden die Knoten mit der alten Version durch Knoten mit der neuen Version ersetzt, bis nur Knoten mit neuen Versionen verbleiben, sodass die Bereitstellung abgeschlossen ist.
* Alle neuen oder geänderten veränderlichen Inhalte werden dann bereitgestellt.

## Indizes {#indexes}

Neue oder geänderte Indizes führen zu einem zusätzlichen Indizierungs- oder Neuindizierungsschritt, bevor die neue Version Traffic aufnehmen kann. Details zur Indexverwaltung in AEM as a Cloud Service finden Sie in [diesem Artikel](/help/operations/indexing.md). Sie können den Indizierungsstatus von Build-Seiten in Cloud Manager überprüfen und eine Benachrichtigung erhalten, wenn die neue Version für Traffic bereit ist.

>[!NOTE]
>
>Die für eine rollierende Bereitstellung benötigte Zeit hängt von der Größe des Index ab. Der Grund dafür ist, dass die neue Version Traffic erst akzeptieren kann, wenn der neue Index generiert wurde.

Derzeit funktioniert AEM as a Cloud Service nicht mit Indexverwaltungs-Tools wie dem ACS Commons Ensure Oak Index-Tool.

## Replikation {#replication}

Der Veröffentlichungsmechanismus ist rückwärtskompatibel mit dem [AEM Replikation von Java™-APIs](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=de).

Um mit Replikation mit Cloud-fähigen AEM Schnellstart zu entwickeln und zu testen, müssen die klassischen Replikationsfunktionen bei einem Autoren-/Veröffentlichungssetup verwendet werden. Wenn der Einstiegspunkt der Benutzeroberfläche in der AEM-Autoreninstanz für die Cloud entfernt wird, wechseln Benutzer zu `http://localhost:4502/etc/replication` für die Konfiguration.

## Rückwärtskompatibler Code für rollierende Bereitstellungen {#backwards-compatible-code-for-rolling-deployments}

Wie oben erläutert, beinhaltet die kontinuierliche Bereitstellungsstrategie von AEM as a Cloud Service, dass sich sowohl die alten als auch die neuen Versionen gleichzeitig ausführen lassen. Seien Sie daher vorsichtig bei Code-Änderungen, die nicht rückwärtskompatibel mit der alten, weiter verwendeten AEM-Version sind.

Darüber hinaus sollte die alte Version auf Kompatibilität mit allen neuen Strukturen veränderlicher Inhalte getestet werden, die von der neuen Version angewendet werden, wenn ein Rollback erfolgt, da veränderliche Inhalte nicht entfernt werden.

### Service-Benutzer- und ACL-Änderungen {#service-users-and-acl-changes}

Das Ändern von Dienstbenutzern oder ACLs, die auf Inhalte oder Code zugreifen, kann in älteren AEM zu Fehlern führen, was dazu führt, dass mit veralteten Dienstbenutzern auf diesen Inhalt oder Code zugegriffen wird. Um dieses Verhalten zu beheben, wird empfohlen, Änderungen über mindestens zwei Versionen zu verteilen, wobei die erste Version als Link fungiert, bevor die nächste Version bereinigt wird.

### Indexänderungen {#index-changes}

Wenn Änderungen an Indizes vorgenommen werden, ist es wichtig, dass die neue Version ihre Indizes bis zum Ende verwendet, während die alte Version ihren eigenen geänderten Satz von Indizes verwendet. Der Entwickler sollte die [in diesem Artikel](/help/operations/indexing.md) beschriebenen Methoden zur Indexverwaltung befolgen.

### Konservative Kodierung für Rollbacks {#conservative-coding-for-rollbacks}

Wenn nach der Bereitstellung ein Fehler gemeldet oder erkannt wird, ist möglicherweise ein Rollback zur alten Version erforderlich. Stellen Sie sicher, dass der neue Code mit allen neuen Strukturen kompatibel ist, die von dieser neuen Version erstellt wurden, da die neuen Strukturen (alle veränderlichen Inhalte) nicht zurückgesetzt werden. Wenn der alte Code nicht kompatibel ist, müssen in nachfolgenden Kundenversionen Korrekturen vorgenommen werden.

## Schnelle Entwicklungsumgebung (RDE) {#rde}

[Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md) (oder kurz RDEs) ermöglichen es Entwicklern, Änderungen schnell bereitzustellen und zu überprüfen, wodurch der Zeitaufwand für das Testen von Funktionen minimiert wird, die bereits für eine lokale Entwicklungsumgebung bewährt sind.

Im Gegensatz zu normalen Entwicklungsumgebungen, die Code über die Cloud Manager-Pipeline bereitstellen, verwenden Entwickler Befehlszeilen-Tools, um Code aus einer lokalen Entwicklungsumgebung mit dem RDE zu synchronisieren. Nachdem die Änderungen erfolgreich in einer RDE getestet wurden, stellen Sie sie über die Cloud Manager-Pipeline in einer regulären Cloud-Entwicklungsumgebung bereit, wodurch der Code über die entsprechenden Quality Gates übermittelt wird.

## Ausführungsmodi {#runmodes}

In bestehenden AEM-Lösungen haben Kundinnen und Kunden die Möglichkeit, Instanzen mit beliebigen Ausführungsmodi auszuführen und OSGi-Konfigurationen anzuwenden oder OSGi-Pakete in diesen spezifischen Instanzen zu installieren. Zu den definierten Ausführungsmodi gehören normalerweise der *Service* (Autor und Veröffentlichen) sowie die Umgebung (RDE, dev, stage, prod).

AEM as a Cloud Service hingegen ist eigenwilliger bezüglich der Frage, welche Ausführungsmodi verfügbar sind und wie ihnen OSGi-Pakete und OSGi-Konfigurationen zugeordnet werden können:

* Die Ausführungsmodi der OSGi-Konfiguration müssen auf RDE, Entwicklung, Staging, Produktion für die Umgebung oder auf die Autoreninstanz, die Veröffentlichungsinstanz für den Dienst verweisen. Eine Kombination aus `<service>.<environment_type>` wird unterstützt, während diese Umgebungen in dieser bestimmten Reihenfolge verwendet werden müssen (z. B. `author.dev` oder `publish.prod`). Die OSGi-Token sollten direkt aus dem Code referenziert werden, anstatt die `getRunModes` -Methode, die die `environment_type` zur Laufzeit. Weitere Informationen finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md).
* Die Ausführungsmodi von OSGi-Bundles sind auf den Service (author, publish) beschränkt. OSGi-Pakete für den Pre-Run-Modus sollten im Inhaltspaket unter `install.author` oder `install.publish` installiert werden.

AEM as a Cloud Service lässt die Verwendung von Ausführungsmodi nicht zu, um Inhalte für bestimmte Umgebungen oder Dienste zu installieren. Wenn eine Entwicklungsumgebung mit Daten oder HTML gesendet werden muss, die sich nicht in der Staging- oder Produktionsumgebung befinden, kann Package Manager verwendet werden.

Folgende Ausführungsmoduskonfigurationen werden unterstützt:

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

Es wird die OSGi-Konfiguration verwendet, die über die am besten passenden Ausführungsmodi verfügt.

Bei der lokalen Entwicklung eines Startparameters für den Ausführungsmodus `-r`, wird verwendet, um die OSGi-Konfiguration für den Ausführungsmodus anzugeben.

```shell
$ java -jar aem-sdk-quickstart-xxxx.x.xxx.xxxx-xxxx.jar -r publish,dev
```

<!-- ### Performance Monitoring {#performance-monitoring}

Developers want to ensure that their custom code is performing well. For Cloud environments, performance reports can be viewed on Cloud Manager. -->

## Konfiguration von Wartungsaufgaben in der Quell-Code-Verwaltung {#maintenance-tasks-configuration-in-source-control}

Wartungsaufgaben müssen in der Quell-Code-Verwaltung beibehalten werden, da die **Tools > Vorgänge** -Bildschirm ist in Cloud-Umgebungen nicht verfügbar. Dadurch wird sichergestellt, dass Änderungen vorsätzlich persistiert werden, anstatt reaktiv angewendet und vergessen zu werden. Siehe [Artikel zu Wartungsaufgaben](/help/operations/maintenance.md) für weitere Informationen.
