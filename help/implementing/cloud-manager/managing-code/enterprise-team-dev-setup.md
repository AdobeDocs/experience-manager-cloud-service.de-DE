---
title: Einrichten des Teams für Unternehmensentwicklung
description: Erfahren Sie, wie Sie Ihr Entwicklungsteam für Unternehmen einrichten und skalieren und sehen, wie AEM as a Cloud Service Ihren Entwicklungsprozess unterstützen kann.
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
source-git-commit: a31c3693c9b2af9bd7f9d7f1f6fb0a61a4411df0
workflow-type: tm+mt
source-wordcount: '1444'
ht-degree: 55%

---

# Enterprise Development Team Setup for AEM as a Cloud Service {#enterprise-setup}

Erfahren Sie, wie Sie Ihr Entwicklungsteam für Unternehmen einrichten und skalieren und sehen, wie AEM as a Cloud Service Ihren Entwicklungsprozess unterstützen kann.

## Einführung {#introduction}

Um Kunden mit Enterprise-Entwicklungs-Setups zu unterstützen, ist AEM as a Cloud Service vollständig in Cloud Manager und dessen speziell konzipierte, [opinimierte CI/CD-Pipelines.](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) Diese Pipelines und Dienste basieren auf Best Practices und gewährleisten eine sorgfältige [Tests und höchste Code-Qualität.](/help/implementing/cloud-manager/code-quality-testing.md)

## Unterstützung von Cloud Manager bei der Einrichtung der Enterprise-Team-Entwicklung {#cloud-manager}

Um ein schnelles Onboarding zu gewährleisten, bietet Cloud Manager alles, was für die ersten Schritte mit der Entwicklung digitaler Erlebnisse erforderlich ist, einschließlich eines Git-Repositorys zum Speichern von Anpassungen, die dann von Cloud Manager erstellt, überprüft und bereitgestellt werden.

Mit Cloud Manager können Entwicklungs-Teams auf die häufige Durchführung von Änderungen hinarbeiten, ohne auf Adobe-Mitarbeiter angewiesen zu sein.

In Cloud Manager sind drei Arten von Umgebungen verfügbar.

* Entwicklung
* Staging
* Produktion

Der Code kann über eine produktionsfremde Pipeline in Entwicklungsumgebungen bereitgestellt werden. Für Staging- und Produktionsumgebungen, die immer zusammenpassen und so eine Validierung vor der Produktionsbereitstellung sicherstellen, verwendet eine Produktions-Pipeline als Best Practice [Quality Gates](/help/implementing/cloud-manager/custom-code-quality-rules.md) , um den Anwendungs-Code und die Konfigurationsänderungen zu überprüfen.

Die Produktions-Pipeline stellt den Code und die Konfiguration zuerst in der Staging-Umgebung bereit, testet die Anwendung und stellt schließlich für die Produktion bereit.

Ein Cloud Service-SDK, das immer mit den neuesten AEM as a Cloud Service Verbesserungen aktualisiert wird, ermöglicht die lokale Entwicklung, wobei die lokale Hardware des Entwicklers direkt verwendet wird. Dies ermöglicht eine schnelle Entwicklung mit sehr geringen Durchlaufzeiten. So können Entwickler in ihrer vertrauten lokalen Umgebung bleiben und aus einer Vielzahl von Entwicklungs-Tools wählen und in Entwicklungsumgebungen oder Produktionsumgebungen pushen, wenn sie es für richtig halten.

Cloud Manager unterstützt flexible Multi-Team-Setups, die an die Anforderungen eines Unternehmens angepasst werden können. Um stabile Bereitstellungen mit mehreren Teams sicherzustellen und gleichzeitig Situationen zu vermeiden, in denen sich ein Team auf die Produktion aller Teams auswirkt, validiert und testet die von Cloud Manager initiierte Pipeline den Code immer gemeinsam von allen Teams.

## Beispiel aus der Praxis {#real-world-example}

Jedes Unternehmen hat unterschiedliche Anforderungen, dazu gehören verschiedene Teams, Prozesse und Entwicklungs-Workflows. Das unten beschriebene Setup wird von Adobe für verschiedene Projekte verwendet, die Erlebnisse zusätzlich zu AEM as a Cloud Service bereitstellen.

Die Adobe Creative Cloud-Programme wie Adobe Photoshop oder Adobe Illustrator enthalten beispielsweise Inhaltsressourcen wie Tutorials, Beispiele und Handbücher, die Endbenutzern zur Verfügung stehen. Diese Inhalte werden von den Client-Anwendungen unter Verwendung von AEM as a Cloud Service auf Headless-Weise genutzt, indem API-Aufrufe an die AEM Cloud-Publishing-Ebene gesendet werden, um die strukturierten Inhalte als JSON-Streams abzurufen, und indem das [Content Delivery Network (CDN) in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#content-delivery) genutzt wird, um strukturierte und unstrukturierte Inhalte mit optimaler Leistung bereitzustellen.

Die Teams, die zu diesem Projekt beitragen, folgen dem folgenden Prozess.

Jedes Team verwendet seinen eigenen Entwicklungs-Workflow und verfügt über ein eigenes Git-Repository. Für das Onboarding von Projekten wird ein zusätzliches freigegebenes Git-Repository verwendet. Dieses Git-Repository enthält die Stammstruktur des Git-Repositorys von Cloud Manager, einschließlich der freigegebenen Dispatcher-Konfiguration.

In der Einarbeitungsphase eines neuen Projekts ist ein Eintrag in der React- oder Maven-Projektdatei im Stammverzeichnis des gemeinsamen Git-Repositorys erforderlich. Für die Dispatcher-Konfiguration wird innerhalb des Dispatcher-Projekts eine neue Konfigurationsdatei erstellt. Diese Datei wird dann von der Hauptdispatcher-Konfiguration eingeschlossen. Jedes Team ist für seine eigene Dispatcher-Konfigurationsdatei verantwortlich. Änderungen am gemeinsamen Git-Repository sind selten und in der Regel nur erforderlich, wenn sich ein neues Projekt in der Einarbeitungsphase befindet. Die Hauptarbeit wird von jedem Projekt-Team in seinem eigenen Git-Repository ausgeführt.

![Workflow-Diagramm](/help/implementing/cloud-manager/assets/team-setup1.png)

Das Git-Repository für jede Datei wird mithilfe der [AEM Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) und folgt somit den Best Practices für die Einrichtung AEM Projekte. Die einzige Ausnahme ist die Dispatcher-Konfiguration, die wie oben beschrieben im freigegebenen Git-Repository durchgeführt wird.

Jedes Team verwendet einen vereinfachten Git-Workflow mit zwei + N-Verzweigungen, der dem Git-Flussmodell folgt:

* Eine stabile Versionsverzweigung enthält den Produktions-Code.

* Eine Entwicklungsverzweigung enthält die neueste Entwicklung.

* Für jede Funktion wird eine neue Verzweigung erstellt.

Die Entwicklung erfolgt in einer Funktionsverzweigung. Wenn die Funktion ausgereift ist, wird sie in der Entwicklungsverzweigung zusammengeführt. Abgeschlossene und validierte Funktionen werden aus der Entwicklungsverzweigung ausgewählt und in der stabilen Verzweigung zusammengeführt.

Alle Änderungen werden durch Pull-Anforderungen (PAs) vorgenommen. Jede PR wird automatisch durch Quality Gates validiert. Bei der Qualitätsprüfung des Codes kommt Sonar zum Einsatz und es wird eine Reihe von Testfolgen ausgeführt, um sicherzustellen, dass der neue Code keine Regression einführt.

Das Setup im Git-Repository von Cloud Manager umfasst zwei Verzweigungen.

* Eine stabile Versionsverzweigung enthält den Produktionscode aller Teams.
* Eine Entwicklungsverzweigung enthält den Entwicklungscode aller Teams.

Jeder Push an das Git-Repository eines Teams in den Triggern &quot;Entwicklung&quot;oder &quot;Stable&quot; [GitHub-Aktion.](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md#managing-code)

Alle Projekte folgen demselben Setup für die stabile Verzweigung. Ein Push in die stabile Verzweigung eines Projekts wird automatisch in die stabile Verzweigung im Git-Repository von Cloud Manager gepusht. Die Produktions-Pipeline in Cloud Manager ist so konfiguriert, dass sie durch einen Push an die stabile Verzweigung ausgelöst wird. Die Produktions-Pipeline wird daher von jedem Push-Vorgang eines Teams in eine stabile Verzweigung ausgeführt und die Produktionsimplementierung wird aktualisiert, wenn alle Quality-Gate-Prüfungen bestanden werden.

![Push-Diagramm](/help/implementing/cloud-manager/assets/team-setup2.png)

Push-Vorgänge zur Entwicklungsverzweigung werden anders gehandhabt. Während ein Push an eine Entwicklerverzweigung im Git-Repository eines Teams ebenfalls eine GitHub-Aktion auslöst und der Code automatisch in die Entwicklungsverzweigung im Git-Repository von Cloud Manager gesendet wird, wird die Nicht-Produktions-Pipeline nicht automatisch durch den Code-Push ausgelöst. Sie wird durch einen Aufruf der Cloud Manager -API ausgelöst.

Das Ausführen der Produktions-Pipeline umfasst das Überprüfen des Codes aller Teams durch die bereitgestellten Quality Gates. Sobald der Code für die Staging-Umgebung bereitgestellt wurde, werden die Tests und Prüfungen ausgeführt, um sicherzustellen, dass alles erwartungsgemäß funktioniert. Sobald alle Quality-Gate-Prüfungen bestanden sind, werden die Änderungen ohne Unterbrechung oder Ausfallzeiten in die Produktion überführt.

Für die lokale Entwicklung wird das [SDK für AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md#developing) verwendet. Das SDK ermöglicht die Einrichtung eines lokalen Autoren-, Veröffentlichungs- und Dispatchers. Dies ermöglicht die Offline-Entwicklung und schnelle Durchlaufzeiten. Manchmal wird nur die Autorenumgebung für die Entwicklung verwendet. Das schnelle Einrichten von Dispatcher- und Veröffentlichungsumgebungen ermöglicht jedoch das lokale Testen, bevor alles in das Git-Repository gepusht wird.

Mitglieder jedes Teams checken normalerweise den Code aus dem gemeinsamen Git-Repository sowie ihren eigenen Projekt-Code aus. Andere Projekte müssen nicht ausgecheckt werden, da die Projekte voneinander unabhängig sind.

![Lokaler Checkout und SDK](/help/implementing/cloud-manager/assets/team-setup3.png)

Dieses reale Setup kann als Entwurf verwendet und dann an die Bedürfnisse eines Unternehmens angepasst werden. Das flexible Verzweigungs- und Zusammenführungskonzept von Git ermöglicht Variationen der oben genannten Workflows, die auf die Anforderungen jedes Teams abgestimmt sind. AEM as a Cloud Service unterstützt alle diese Varianten, ohne den Kernwert der bestimmenden Cloud Manager-Pipeline zu opfern.

>[!TIP]
>
>Weitere Informationen finden Sie im Dokument . [Arbeiten mit mehreren Quell-Git-Repositorys](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/managing-code/working-with-multiple-source-git-repos.html?lang=de#managing-code) , um mehr über dieses Setup zu erfahren.

### Überlegungen zur Einrichtung mehrerer Teams {#considerations}

Mit dem Git-Repository von Cloud Manager und der Produktions-Pipeline wird der vollständige Produktionscode immer durch alle Quality Gates ausgeführt und als eine Implementierungseinheit behandelt. So ist das Produktionssystem immer ohne Unterbrechung oder Ausfallzeiten betriebsbereit.

Ohne ein solches System dagegen besteht die Gefahr, dass eine Änderung eines einzelnen Teams zu Problemen mit der Produktionsstabilität führen kann, da jedes Team separat bereitstellen kann. Darüber hinaus sind eine Koordinierung und geplante Ausfallzeiten erforderlich, um Aktualisierungen einzuführen. Mit zunehmender Anzahl von Teams wird der Koordinierungsaufwand immer komplexer und schnell unkontrollierbar.

Wenn ein Problem in den Quality Gates erkannt wird, ist die Produktion nicht betroffen und das Problem kann erkannt und behoben werden, ohne dass Adobe-Mitarbeiter eingreifen müssen. Ohne Cloud Service und ohne immer die gesamte Implementierung zu testen, können partielle Implementierungen zu Ausfällen führen, die eine Rollback-Anfrage oder sogar eine vollständige Wiederherstellung aus einer Sicherung erfordern. Das teilweise Testen kann auch zu anderen Problemen führen, die dann im Nachhinein behoben werden müssen, was wiederum die Koordination und Unterstützung durch Adobe-Mitarbeiter erfordert.

>[!TIP]
>
>Für jedes Multi-Team-Setup ist es von entscheidender Bedeutung, ein Governance-Modell und eine Reihe von Standards zu definieren, denen alle Teams folgen müssen. Der vorherige Entwurf für ein Multi-Team-Setup ermöglicht die Skalierung über eine größere Anzahl von Teams, die Sie als Ausgangspunkt verwenden können.
