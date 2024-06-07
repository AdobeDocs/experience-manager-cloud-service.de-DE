---
title: Einrichten eines Entwicklungs-Teams für Unternehmen
description: Erfahren Sie, wie Sie Ihr Entwicklungs-Team für Unternehmen einrichten und skalieren, und sehen Sie, wie AEM as a Cloud Service Ihren Entwicklungsprozess unterstützen kann.
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 646ca4f4a441bf1565558002dcd6f96d3e228563
workflow-type: ht
source-wordcount: '1423'
ht-degree: 100%

---

# Einrichten eines Entwicklungs-Teams für Unternehmen für AEM as a Cloud Service {#enterprise-setup}

Erfahren Sie, wie Sie Ihr Entwicklungs-Team für Unternehmen einrichten und skalieren, und sehen Sie, wie AEM as a Cloud Service Ihren Entwicklungsprozess unterstützen kann.

## Einführung {#introduction}

Zur Unterstützung von Kundinnen und Kunden mit unternehmensweiten Entwicklungskonfigurationen ist AEM as a Cloud Service vollständig mit Cloud Manager und dafür vorgesehenen, [opinionierten CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) integriert. Diese Pipelines und Dienste basieren auf Best Practices und gewährleisten sorgfältige [Tests und höchste Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md).

## Unterstützung von Cloud Manager bei der Einrichtung der Unternehmens-Team-Entwicklung {#cloud-manager}

Um ein schnelles Onboarding zu gewährleisten, stellt Cloud Manager alles bereit, was erforderlich ist, um sofort mit der Entwicklung von digitalen Erlebnissen zu beginnen, einschließlich eines Git-Repositorys zum Speichern von Anpassungen, die dann von Cloud Manager erstellt, überprüft und bereitgestellt werden.

Mit Cloud Manager können Entwicklungs-Teams auf die häufige Durchführung von Änderungen hinarbeiten, ohne auf Personal von Adobe angewiesen zu sein.

In Cloud Manager sind drei Arten von Umgebungen verfügbar.

* Entwicklung
* Staging
* Produktion

Der Code kann über eine produktionsfremde Pipeline in Entwicklungsumgebungen bereitgestellt werden. Bei Staging- und Produktionsumgebungen, die immer zusammengehören und so als Best Practice eine Validierung vor der Produktionsbereitstellung sicherstellen, verwendet eine Produktions-Pipeline [Quality Gates](/help/implementing/cloud-manager/custom-code-quality-rules.md), um den Code des Programms und die Konfigurationsänderungen zu validieren.

Die Produktions-Pipeline stellt den Code und die Konfiguration zuerst in der Staging-Umgebung bereit, testet die Anwendung und stellt sie schließlich für die Produktion bereit.

Ein Cloud Service-SDK, das immer mit den neuesten AEM as a Cloud Service-Verbesserungen aktualisiert wird, ermöglicht die lokale Entwicklung, die direkt die lokale Hardware der Entwicklerin bzw. des Entwicklers verwendet. Dies ermöglicht eine schnelle Entwicklung mit sehr geringen Durchlaufzeiten. So können Entwickler in ihrer vertrauten lokalen Umgebung bleiben und aus einer Vielzahl von Entwicklungs-Tools wählen und in Entwicklungsumgebungen oder Produktionsumgebungen pushen, wenn sie es für richtig halten.

Cloud Manager unterstützt flexible Multi-Team-Setups, die an die Anforderungen eines Unternehmens angepasst werden können. Um stabile Bereitstellungen mit mehreren Teams zu gewährleisten und gleichzeitig Situationen zu vermeiden, in denen ein Team die Produktion für alle Teams beeinträchtigt, validiert und testet die bestimmende Pipeline von Cloud Manager immer den Code aller Teams gemeinsam.

## Beispiel aus der Praxis {#real-world-example}

Jedes Unternehmen hat unterschiedliche Anforderungen, dazu gehören verschiedene Teams, Prozesse und Entwicklungs-Workflows. Das unten beschriebene Setup wird von Adobe für verschiedene Projekte verwendet, die Erlebnisse zusätzlich zu AEM as a Cloud Service bereitstellen.

Die Adobe Creative Cloud-Programme wie Adobe Photoshop oder Adobe Illustrator enthalten beispielsweise Inhaltsressourcen wie Tutorials, Beispiele und Handbücher, die Endbenutzern zur Verfügung stehen. Diese Inhalte werden von den Client-Anwendungen unter Verwendung von AEM as a Cloud Service auf Headless-Weise genutzt, indem API-Aufrufe an die Publishing-Ebene von AEM Cloud gesendet werden, um die strukturierten Inhalte als JSON-Streams abzurufen, und indem das [Content Delivery Network (CDN) in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#content-delivery) genutzt wird, um sowohl strukturierte als auch unstrukturierte Inhalte mit optimaler Leistung bereitzustellen.

Die Teams, die zu diesem Projekt beitragen, folgen dem folgenden Prozess.

Jedes Team verwendet seinen eigenen Entwicklungs-Workflow und verfügt über ein separates Git-Repository. Ein zusätzliches, gemeinsames Git-Repository wird beim Onboarding von Projekten verwendet. Dieses Git-Repository enthält die Stammstruktur des Git-Repositorys von Cloud Manager, einschließlich der freigegebenen Dispatcher-Konfiguration.

In der Einarbeitungsphase eines neuen Projekts ist ein Eintrag in der React- oder Maven-Projektdatei im Stammverzeichnis des gemeinsamen Git-Repositorys erforderlich. Für die Dispatcher-Konfiguration wird innerhalb des Dispatcher-Projekts eine neue Konfigurationsdatei erstellt. Diese Datei wird dann von der Hauptdispatcher-Konfiguration eingeschlossen. Jedes Team ist für seine eigene Dispatcher-Konfigurationsdatei verantwortlich. Änderungen am gemeinsamen Git-Repository sind selten und in der Regel nur erforderlich, wenn sich ein neues Projekt in der Einarbeitungsphase befindet. Die Hauptarbeit wird von jedem Projekt-Team in seinem eigenen Git-Repository ausgeführt.

![Workflow-Diagramm](/help/implementing/cloud-manager/assets/team-setup1.png)

Das Git-Repository für jedes Projekt wird mit dem [AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) eingerichtet und folgt somit den Best Practice für die Einrichtung von AEM-Projekten. Die einzige Ausnahme ist die Dispatcher-Konfiguration, die wie oben beschrieben im gemeinsamen Git-Repository erfolgt.

Jedes Team verwendet einen vereinfachten Git-Workflow mit zwei + N-Verzweigungen, der dem Git-Flussmodell folgt:

* Eine stabile Versionsverzweigung enthält den Produktions-Code.

* Eine Entwicklungsverzweigung enthält die neueste Entwicklung.

* Für jede Funktion wird eine neue Verzweigung erstellt.

Die Entwicklung erfolgt in einer Funktionsverzweigung. Wenn die Funktion ausgereift ist, wird sie in der Entwicklungsverzweigung zusammengeführt. Abgeschlossene und validierte Funktionen werden aus der Entwicklungsverzweigung ausgewählt und in der stabilen Verzweigung zusammengeführt.

Alle Änderungen werden über Pull Requests (PR) vorgenommen. Jede PR wird automatisch durch Quality Gates validiert. Bei der Qualitätsprüfung des Codes kommt Sonar zum Einsatz und es wird eine Reihe von Testfolgen ausgeführt, um sicherzustellen, dass der neue Code keine Regression einführt.

Das Setup im Git-Repository von Cloud Manager umfasst zwei Verzweigungen:

* Eine Verzweigung für stabile Versionen, die den Produktions-Code aller Teams enthält.
* Eine Entwicklungsverzweigung, die den Entwicklungs-Code aller Teams enthält.

Jeder Push an das Git-Repository eines Teams in der Entwicklungs- oder der stabilen Verzweigung löst eine [GitHub-Aktion](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md#managing-code) aus.

Alle Projekte folgen demselben Setup für die stabile Verzweigung. Ein Push in die stabile Verzweigung eines Projekts wird automatisch in die stabile Verzweigung im Git-Repository von Cloud Manager gepusht. Die Produktions-Pipeline in Cloud Manager ist so konfiguriert, dass sie durch einen Push an die stabile Verzweigung ausgelöst wird. Die Produktions-Pipeline wird daher von jedem Push-Vorgang eines Teams in eine stabile Verzweigung ausgeführt und die Produktionsbereitstellung wird aktualisiert, wenn alle Quality-Gate-Prüfungen bestanden werden.

![Push-Diagramm](/help/implementing/cloud-manager/assets/team-setup2.png)

Push-Vorgänge zur Entwicklungsverzweigung werden anders gehandhabt. Während ein Push an eine Entwicklungsverzweigung im Git-Repository eines Teams ebenfalls eine GitHub-Aktion auslöst und der Code automatisch in die Entwicklungsverzweigung im Git-Repository von Cloud Manager gepusht wird, wird die produktionsfremde Pipeline nicht automatisch durch den Code-Push ausgelöst. Sie wird durch einen Aufruf der API von Cloud Manager ausgelöst.

Das Ausführen der Produktions-Pipeline umfasst das Überprüfen des Codes aller Teams durch die bereitgestellten Quality Gates. Sobald der Code für die Staging-Umgebung bereitgestellt wurde, werden die Tests und Prüfungen ausgeführt, um sicherzustellen, dass alles erwartungsgemäß funktioniert. Sobald alle Quality-Gate-Prüfungen bestanden sind, werden die Änderungen ohne Unterbrechung oder Ausfallzeiten in die Produktion überführt.

Für die lokale Entwicklung wird das [SDK für AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md#developing) verwendet. Das SDK ermöglicht die Einrichtung einer lokalen Authoring- und Publishing-Umgebung sowie eines Dispatchers. Dies ermöglicht die Offline-Entwicklung und schnelle Durchlaufzeiten. Manchmal wird nur die Authoring-Umgebung für die Entwicklung verwendet, aber das schnelle Einrichten des Dispatchers und der Publishing-Umgebung ermöglicht es, alles lokal zu testen, bevor es in das Git-Repository gepusht wird.

Mitglieder jedes Teams checken normalerweise den Code aus dem gemeinsamen Git-Repository für ihren eigenen Projekt-Code aus. Andere Projekte müssen nicht ausgecheckt werden, da die Projekte voneinander unabhängig sind.

![Lokaler Checkout und SDK](/help/implementing/cloud-manager/assets/team-setup3.png)

Dieses reale Setup kann als Entwurf verwendet und dann an die Bedürfnisse eines Unternehmens angepasst werden. Das flexible Verzweigungs- und Zusammenführungskonzept von Git ermöglicht Variationen der oben genannten Workflows, die auf die Anforderungen jedes Teams abgestimmt sind. AEM as a Cloud Service unterstützt alle diese Varianten, ohne den Kernwert der bestimmenden Cloud Manager-Pipeline zu opfern.

>[!TIP]
>
>Weitere Informationen zur Einrichtung finden Sie unter [Arbeiten mit mehreren Quell-Git-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html?lang=de#managing-code).

### Überlegungen zur Einrichtung mehrerer Teams {#considerations}

Mit dem Git-Repository von Cloud Manager und der Produktions-Pipeline wird der vollständige Produktions-Code immer durch alle Quality Gates geleitet und als eine Bereitstellungseinheit behandelt. Auf diese Weise ist das Produktionssystem stets ohne Unterbrechung oder Ausfallzeiten verfügbar.

Ohne ein solches System dagegen besteht die Gefahr, dass eine Änderung eines einzelnen Teams zu Problemen mit der Produktionsstabilität führen kann, da jedes Team separat bereitstellen kann. Darüber hinaus sind eine Koordinierung und geplante Ausfallzeiten erforderlich, um Aktualisierungen einzuführen. Mit zunehmender Anzahl von Teams wird der Koordinierungsaufwand immer komplexer und schnell unkontrollierbar.

Wenn ein Problem in den Quality Gates erkannt wird, ist die Produktion nicht betroffen und das Problem kann erkannt und behoben werden, ohne dass Personal von Adobe eingreifen muss. Ohne Cloud Service und ohne immer die gesamte Bereitstellung zu testen, können partielle Bereitstellungen zu Ausfällen führen, die eine Anfrage zum Zurücksetzen oder sogar eine vollständige Wiederherstellung aus einem Backup erfordern. Das teilweise Testen kann auch zu anderen Problemen führen, die dann im Nachhinein behoben werden müssen, was wiederum die Koordination und Unterstützung durch Personal von Adobe erfordert.

>[!TIP]
>
>Für jedes Multi-Team-Setup ist es entscheidend, ein Governance-Modell und einen Satz von Standards zu definieren, die alle Teams befolgen müssen. Der vorherige Blueprint für ein Multi-Team-Setup ermöglicht die Skalierung auf eine größere Anzahl von Teams, die Sie als Ausgangspunkt verwenden können.
