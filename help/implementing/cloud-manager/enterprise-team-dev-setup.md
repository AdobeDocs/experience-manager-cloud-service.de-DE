---
title: Einrichten der Enterprise-Team-Entwicklung – Cloud Services
description: Auf dieser Seite erfahren Sie mehr über die Einrichtung der Enterprise-Team-Entwicklung
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
source-git-commit: 33e1c7eb5ea224b46ba441ca7447f90f04476c76
workflow-type: ht
source-wordcount: '1525'
ht-degree: 100%

---

# Einrichten der Enterprise-Team-Entwicklung für AEM as a Cloud Service {#enterprise-setup}

## Einführung {#introduction}

AEM as a Cloud Service, ein Cloud-natives Angebot, das AEM as a Service bereitstellt, profitiert von über 10 Jahren Erfahrung in der Bereitstellung von Unternehmens-Software für Unternehmens-Teams mit ihren spezifischen Anforderungen. Während AEM in die Cloud-native Welt katapultiert wurde, mit neuen Werten wie „always on“, „always current“, „always secure“ und „always at scale“, behält es das Haupt-Wertversprechen bei, das AEM als anpassbare Plattform für unsere Kunden bietet und die Integration von Teams im Unternehmensmaßstab in ihre Entwicklungs- und Leistungserstellungsprozesse ermöglicht.

Um unsere Kunden beim Einrichten der Enterprise-Entwicklung zu unterstützen, ist AEM as a Cloud Service vollständig in Cloud Manager und seine speziell entwickelten bestimmenden CI/CD-Pipelines integriert, die mit Best Practices und Erfahrungen aus mehrjähriger Erfahrung mit Entwicklung und Bereitstellung im Unternehmensmaßstab ausgestattet sind. Dies gewährleistet gründliche Tests und höchste Code-Qualität, um außergewöhnliche Erlebnisse zu erzielen.

## Unterstützung von Cloud Manager bei der Einrichtung der Enterprise-Team-Entwicklung {#cloud-manager}

Um für die Kunden eine schnelle Einarbeitung zu gewährleisten, stellt Cloud Manager alles bereit, was erforderlich ist, um sofort mit der Entwicklung von Erlebnissen zu beginnen, einschließlich eines Git-Repositorys zum Speichern von Anpassungen, die dann von Cloud Manager erstellt, überprüft und bereitgestellt werden.
Mit Cloud Manager können Entwicklungs-Teams auf die häufige Durchführung von Änderungen hinarbeiten, ohne auf Adobe-Mitarbeiter angewiesen zu sein.

In Cloud Manager sind drei Umgebungstypen verfügbar:

* Entwicklung
* Staging
* Produktion

Der Code kann über eine Nicht-Produktions-Pipeline in Entwicklungsumgebungen bereitgestellt werden. Bei Staging- und Produktionsumgebungen, die immer zusammengehören und als Best Practice so eine Validierung vor der Produktionsbereitstellung sicherstellen, verwendet eine Produktions-Pipeline Quality Gates, um den Code des Programms und die Konfigurationsänderungen zu validieren.

Die Produktions-Pipeline stellt den Code und die Konfiguration zuerst in der Staging-Umgebung bereit, testet das Programm und stellt es schließlich für die Produktion bereit.
Ein Cloud Service-SDK, das immer mit den neuesten Cloud Service-Verbesserungen aktualisiert wird, ermöglicht die lokale Entwicklung, die direkt die lokale Hardware des Entwicklers verwendet. Dies ermöglicht eine schnelle Entwicklung mit sehr geringen Durchlaufzeiten. So können Entwickler in ihrer vertrauten lokalen Umgebung bleiben und aus einer Vielzahl von Entwicklungs-Tools wählen und in Entwicklungsumgebungen oder Produktionsumgebungen pushen, wenn sie es für richtig halten.

Cloud Manager unterstützt flexible Multi-Team-Setups, die an die Anforderungen eines Unternehmens angepasst werden können. Dies gilt sowohl für Cloud Service als auch für AMS. Um stabile Implementierungen mit mehreren Teams zu gewährleisten und zu vermeiden, dass ein Team die Produktion für alle Teams beeinträchtigt, validiert und testet die bestimmende Pipeline von Cloud Manager immer den Code aller Teams gemeinsam.


## Beispiel aus der Praxis {#real-world-example}

Jedes Unternehmen hat unterschiedliche Anforderungen, dazu gehören verschiedene Teams, Prozesse und Entwicklungs-Workflows. Das unten beschriebene Setup wird von Adobe für verschiedene Projekte verwendet, die Erlebnisse zusätzlich zu AEM as a Cloud Service bereitstellen.

Die Adobe Creative Cloud-Programme wie Adobe Photoshop oder Adobe Illustrator enthalten beispielsweise Inhaltsressourcen wie Tutorials, Beispiele und Handbücher, die Endbenutzern zur Verfügung stehen. Diese Inhalte werden von den Client-Anwendungen unter Verwendung von AEM as a Cloud Service auf *Headless*-Weise genutzt, indem API-Aufrufe an die AEM Cloud-Publishing-Ebene gesendet werden, um die strukturierten Inhalte als JSON-Streams abzurufen, und indem das [Content Delivery Network (CDN) in AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/content-delivery/cdn.html?lang=de#content-delivery) genutzt wird, um strukturierte und unstrukturierte Inhalte mit optimaler Leistung bereitzustellen.

Die an diesem Projekt beteiligten Teams halten sich an den nachfolgend beschriebenen Prozess.

>[!NOTE]
>Weitere Informationen zum Setup finden Sie unter [Arbeiten mit mehreren Quell-Git-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html?lang=de#managing-code).

Jedes Team verwendet seinen eigenen Entwicklungs-Workflow und verfügt über ein eigenes Git-Repository. Ein zusätzliches gemeinsames Git-Repository wird in der Einarbeitungsphase von Projekten verwendet. Dieses Git-Repository enthält die Stammstruktur des Git-Repositorys von Cloud Manager, einschließlich der freigegebenen Dispatcher-Konfiguration. In der Einarbeitungsphase eines neuen Projekts ist ein Eintrag in der React- oder Maven-Projektdatei im Stammverzeichnis des gemeinsamen Git-Repositorys erforderlich. Für die Dispatcher-Konfiguration wird innerhalb des Dispatcher-Projekts eine neue Konfigurationsdatei erstellt. Diese Datei wird dann von der Hauptdispatcher-Konfiguration eingeschlossen. Jedes Team ist für seine eigene Dispatcher-Konfigurationsdatei verantwortlich. Änderungen am gemeinsamen Git-Repository sind selten und in der Regel nur erforderlich, wenn sich ein neues Projekt in der Einarbeitungsphase befindet. Die Hauptarbeit wird von jedem Projekt-Team in seinem eigenen Git-Repository ausgeführt.

![](assets/team-setup1.png)

Das Git-Repository für jedes Team wurde mithilfe des AEM-Maven-Archetyps eingerichtet und befolgt daher die Best Practices zum Einrichten von AEM Projekten. Die einzige Ausnahme ist die Handhabung der Dispatcher-Konfiguration, die wie oben beschrieben im gemeinsamen Git-Repository erfolgt.
Jedes Team verwendet einen vereinfachten Git-Workflow mit zwei + N Verzweigungen, der dem Git-Flussmodell folgt:

* Eine stabile Versionsverzweigung enthält den Produktions-Code

* Eine Entwicklungsverzweigung enthält die neueste Entwicklung

* Für jede Funktion wird eine neue Verzweigung erstellt


Die Entwicklung erfolgt in einer Funktionsverzweigung. Wenn die Funktion ausgereift ist, wird sie in der Entwicklungsverzweigung zusammengeführt. Abgeschlossene und validierte Funktionen werden aus der Entwicklungsverzweigung ausgewählt und in der stabilen Verzweigung zusammengeführt. Alle Änderungen werden über Pull Requests (PR) vorgenommen. Jede PR wird automatisch durch Quality Gates validiert. Bei der Qualitätsprüfung des Codes kommt Sonar zum Einsatz und es wird eine Reihe von Testfolgen ausgeführt, um sicherzustellen, dass der neue Code keine Regression einführt.

Das Setup im Git-Repository von Cloud Manager umfasst zwei Verzweigungen:

* Eine *Verzweigung für stabile Versionen*, die den Produktions-Code aller Teams enthält
* Eine *Entwicklungsverzweigung*, die den Entwicklungs-Code aller Teams enthält

Jeder Push an das Git-Repository eines Teams in der Entwicklungs- oder der stabilen Verzweigung löst eine [GitHub-Aktion](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html?lang=de#managing-code) aus. Alle Projekte folgen demselben Setup für die stabile Verzweigung. Ein Push in die stabile Verzweigung eines Projekts wird automatisch in die stabile Verzweigung im Git-Repository von Cloud Manager gepusht. Die Produktions-Pipeline in Cloud Manager ist so konfiguriert, dass sie durch einen Push an die stabile Verzweigung ausgelöst wird. Die Produktions-Pipeline wird daher von jedem Push-Vorgang eines Teams in eine stabile Verzweigung ausgeführt und die Produktionsimplementierung wird aktualisiert, wenn alle Quality-Gate-Prüfungen bestanden werden.

![](assets/team-setup2.png)

Push-Vorgänge zur Entwicklungsverzweigung werden anders gehandhabt. Während ein Push an eine Entwicklungsverzweigung im Git-Repository eines Teams ebenfalls eine GitHub-Aktion auslöst und der Code automatisch in die Entwicklungsverzweigung im Git-Repository von Cloud Manager gepusht wird, wird die Nicht-Produktions-Pipeline nicht automatisch durch den Code-Push ausgelöst. Sie wird durch einen Aufruf der API von Cloud Manager ausgelöst.
Das Ausführen der Produktions-Pipeline umfasst das Überprüfen des Codes aller Teams durch die bereitgestellten Quality Gates. Sobald der Code für die Staging-Umgebung bereitgestellt wurde, werden die Tests und Prüfungen ausgeführt, um sicherzustellen, dass alles erwartungsgemäß funktioniert. Sobald alle Quality-Gate-Prüfungen bestanden sind, werden die Änderungen ohne Unterbrechung oder Ausfallzeiten in die Produktion überführt.
Für die lokale Entwicklung wird das [SDK für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=de#developing) verwendet. Das SDK ermöglicht die Einrichtung einer lokalen Autoren- und Veröffentlichungsumgebung sowie eines Dispatchers. Dies ermöglicht die Offline-Entwicklung und schnelle Durchlaufzeiten. Manchmal wird nur die Autorenumgebung für die Entwicklung verwendet, aber das schnelle Einrichten des Dispatchers und der Veröffentlichungsumgebung ermöglicht es, alles lokal zu testen, bevor es in das Git-Repository gepusht wird. Mitglieder jedes Teams checken normalerweise den Code aus dem gemeinsamen Git-Repository sowie ihren eigenen Projekt-Code aus. Andere Projekte müssen nicht ausgecheckt werden, da die Projekte voneinander unabhängig sind.

![](assets/team-setup3.png)

Dieses reale Setup kann als Entwurf verwendet und dann an die Bedürfnisse eines Unternehmens angepasst werden. Das flexible Verzweigungs- und Zusammenführungskonzept von Git ermöglicht Variationen der oben genannten Workflows, die auf die Anforderungen jedes Teams abgestimmt sind. AEM as a Cloud Service unterstützt alle diese Varianten, ohne den Kernwert der bestimmenden Cloud Manager-Pipeline zu opfern.

### Überlegungen zu einem Multi-Team-Setup {#considerations}

>[!NOTE]
>Für jedes Multi-Team-Setup ist es entscheidend, ein Governance-Modell und einen Satz von Standards zu definieren, die alle Teams befolgen müssen. Der oben beschriebene Entwurf für ein Multi-Team-Setup ermöglicht die Skalierung über eine größere Anzahl von Teams hinweg und Sie können diesen Entwurf als Ausgangspunkt verwenden.

Mit dem Git-Repository von Cloud Manager und der Produktions-Pipeline wird der vollständige Produktions-Code immer durch alle Quality Gates geleitet und als eine Implementierungseinheit behandelt. Auf diese Weise wird das Produktionssystem *always on*, d. h. ohne Unterbrechung oder Ausfallzeit gehalten.
Ohne ein solches System dagegen besteht die Gefahr, dass eine Änderung eines einzelnen Teams zu Problemen mit der Produktionsstabilität führen kann, da jedes Team separat bereitstellen kann. Darüber hinaus sind eine Koordinierung und geplante Ausfallzeiten erforderlich, um Aktualisierungen einzuführen. Mit zunehmender Anzahl von Teams wird der Koordinierungsaufwand immer komplexer und schnell unkontrollierbar.

Wenn ein Problem in den Quality Gates erkannt wird, ist die Produktion nicht betroffen und das Problem kann erkannt und behoben werden, ohne dass Adobe-Mitarbeiter eingreifen müssen. Ohne Cloud Service und ohne immer die gesamte Implementierung zu testen, können partielle Implementierungen zu Ausfällen führen, die eine Rollback-Anfrage oder sogar eine vollständige Wiederherstellung aus einer Sicherung erfordern. Das teilweise Testen kann auch zu anderen Problemen führen, die dann im Nachhinein behoben werden müssen, was wiederum die Koordination und Unterstützung durch Adobe-Mitarbeiter erfordert.
