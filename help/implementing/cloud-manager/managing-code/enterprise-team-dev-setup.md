---
title: Einrichten eines Entwicklungs-Teams für Unternehmen
description: Erfahren Sie, wie Sie Ihr Entwicklungs-Team für Unternehmen einrichten und skalieren, und sehen Sie, wie AEM as a Cloud Service Ihren Entwicklungsprozess unterstützen kann.
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1401'
ht-degree: 100%

---

# Einrichten eines Entwicklungs-Teams für Unternehmen für AEM as a Cloud Service {#enterprise-setup}

Erfahren Sie, wie Sie ein Entwicklungs-Team für Ihr Unternehmen einrichten und skalieren, und sehen Sie, wie AEM (Adobe Experience Manager) as a Cloud Service Ihren Entwicklungsprozess unterstützen kann.

## Einführung {#introduction}

Zur Unterstützung von Kundinnen und Kunden mit unternehmensweiten Entwicklungskonfigurationen ist AEM as a Cloud Service vollständig mit Cloud Manager und dafür vorgesehenen, [opinionierten CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) integriert. Diese Pipelines und Dienste basieren auf Best Practices und gewährleisten sorgfältige [Tests und höchste Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md).

## Unterstützung von Cloud Manager bei der Einrichtung von Entwicklungs-Teams für Unternehmen {#cloud-manager}

Um ein schnelles Onboarding zu gewährleisten, bietet Cloud Manager alles, was erforderlich ist, um sofort mit der Entwicklung von digitalen Erlebnissen zu beginnen, einschließlich eines Git-Repositorys zum Speichern von Anpassungen, die dann von Cloud Manager erstellt, überprüft und bereitgestellt werden.

Mit Cloud Manager können Entwicklungs-Teams auf die häufige Durchführung von Änderungen hinarbeiten, ohne auf Personal von Adobe angewiesen zu sein.

In Cloud Manager sind drei Arten von Umgebungen verfügbar.

* Entwicklung
* Staging
* Produktion

Der Code kann über eine produktionsfremde Pipeline in Entwicklungsumgebungen bereitgestellt werden. Bei Staging- und Produktionsumgebungen, die immer zusammengehören und so als Best Practice eine Validierung vor der Produktionsbereitstellung sicherstellen, verwendet eine Produktions-Pipeline [Quality Gates](/help/implementing/cloud-manager/custom-code-quality-rules.md), um den Code des Programms und die Konfigurationsänderungen zu validieren.

Die Produktions-Pipeline stellt den Code und die Konfiguration zuerst in der Staging-Umgebung bereit, testet die Anwendung und stellt sie schließlich für die Produktion bereit.

Ein Cloud Service-SDK, das immer mit den neuesten Verbesserungen von AEM as a Cloud Service aktualisiert wird, ermöglicht die lokale Entwicklung, die direkt die lokale Hardware der Entwickelnden verwendet. Dieser Ansatz ermöglicht eine schnelle Entwicklung mit sehr geringen Durchlaufzeiten. So können Entwickelnde in ihrer vertrauten lokalen Umgebung bleiben, aus einer Vielzahl von Entwicklungswerkzeugen wählen und sie nach Bedarf in Entwicklungs- oder Produktionsumgebungen übertragen.

Cloud Manager unterstützt flexible Multi-Team-Setups, die an die Anforderungen eines Unternehmens angepasst werden können. Um eine stabile Bereitstellung über mehrere Teams hinweg sicherzustellen, validiert und testet die bestimmende Pipeline von Cloud Manager den Code von allen Teams gemeinsam. Dieser Ansatz verhindert Situationen, in denen sich die Änderungen eines Teams auf die Produktion für alle Teams auswirken.

## Beispiel aus der Praxis {#real-world-example}

Jedes Unternehmen hat unterschiedliche Anforderungen, dazu gehören verschiedene Teams, Prozesse und Entwicklungs-Workflows. Das unten beschriebene Setup wird von Adobe für verschiedene Projekte verwendet, die Erlebnisse zusätzlich zu AEM as a Cloud Service bereitstellen.

Die Adobe Creative Cloud-Programme wie Adobe Photoshop oder Adobe Illustrator enthalten beispielsweise Inhaltsressourcen wie Tutorials, Beispiele und Handbücher, die Endbenutzern zur Verfügung stehen. Client-Anwendungen verwenden Inhalte aus AEM as a Cloud Service auf eine Headless-Weise. Sie führen API-Aufrufe an die AEM Cloud-Veröffentlichungsebene aus, um strukturierte Inhalte als JSON-Streams abzurufen. Darüber hinaus wird das [Content Delivery Network (CDN) in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#content-delivery) verwendet, um sowohl strukturierte als auch unstrukturierte Inhalte mit optimaler Leistung bereitzustellen.

Die Teams, die zu diesem Projekt beitragen, halten sich an den folgenden Prozess.

Jedes Team verwendet seinen eigenen Entwicklungs-Workflow und verfügt über ein separates Git-Repository. Ein zusätzliches, gemeinsames Git-Repository wird beim Onboarding von Projekten verwendet. Dieses Git-Repository enthält die Stammstruktur des Git-Repositorys von Cloud Manager, einschließlich der gemeinsam verwendeten Dispatcher-Konfiguration.

In der Onboarding-Phase eines neuen Projekts ist ein Eintrag in der Reactor-Maven-Projektdatei im Stammverzeichnis des gemeinsamen Git-Repositorys erforderlich. Für die Dispatcher-Konfiguration wird innerhalb des Dispatcher-Projekts eine neue Konfigurationsdatei erstellt. Die Hauptkonfiguration des Dispatchers enthält dann diese Datei. Jedes Team ist für seine eigene Dispatcher-Konfigurationsdatei verantwortlich. Änderungen am gemeinsamen Git-Repository sind selten und in der Regel nur erforderlich, wenn sich ein neues Projekt in der Onboarding-Phase befindet. Die Hauptarbeit wird von jedem Projekt-Team in seinem eigenen Git-Repository ausgeführt.

![Diagramm des Workflows](/help/implementing/cloud-manager/assets/team-setup1.png)

Zum Einrichten des Git-Repositorys wird der [AEM-Projektarchetyp](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/overview) verwendet, wodurch die Best Practices für die Einrichtung von AEM-Projekten eingehalten werden. Die einzige Ausnahme ist die Dispatcher-Konfiguration, die wie oben beschrieben im gemeinsamen Git-Repository erfolgt.

Jedes Team verwendet einen vereinfachten Git-Workflow mit zwei + N-Verzweigungen, der dem Git-Flussmodell folgt:

* Eine stabile Versionsverzweigung enthält den Produktions-Code.

* Eine Entwicklungsverzweigung enthält die neueste Entwicklung.

* Für jede Funktion wird eine neue Verzweigung erstellt.

Die Entwicklung erfolgt in einer Funktionsverzweigung. Wenn die Funktion ausgereift ist, wird sie in der Entwicklungsverzweigung zusammengeführt. Fertiggestellte und validierte Funktionen werden aus der Entwicklungsverzweigung ausgewählt und in der stabilen Verzweigung zusammengeführt.

Alle Änderungen werden über Pull-Anfragen (Pull Requests, PR) vorgenommen. Qualitäts-Gates validieren automatisch jede PR. Bei der Qualitätsprüfung des Codes kommt Sonar zum Einsatz, und es wird eine Reihe von Testfolgen ausgeführt, um sicherzustellen, dass der neue Code keine Regression einführt.

Das Setup im Git-Repository von Cloud Manager umfasst zwei Verzweigungen:

* Eine Verzweigung für stabile Versionen, die den Produktions-Code aller Teams enthält.
* Eine Entwicklungsverzweigung, die den Entwicklungs-Code aller Teams enthält.

Jeder Push an das Git-Repository eines Teams in der Entwicklungs- oder der stabilen Verzweigung löst eine [GitHub-Aktion](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md#managing-code) aus.

Alle Projekte folgen demselben Setup für die stabile Verzweigung. Ein Push in die stabile Verzweigung eines Projekts wird automatisch in die stabile Verzweigung im Git-Repository von Cloud Manager gepusht. Ein Push in die stabile Verzweigung löst die Produktions-Pipeline in Cloud Manager aus. Jeder Push eines beliebigen Teams in eine stabile Verzweigung löst die Produktions-Pipeline aus. Die Produktionsbereitstellung wird aktualisiert, wenn alle Qualitäts-Gates bestanden sind.

![Push-Diagramm](/help/implementing/cloud-manager/assets/team-setup2.png)

Push-Vorgänge zur Entwicklungsverzweigung werden anders gehandhabt. Eine Push-Benachrichtigung an eine Entwicklerverzweigung im Git-Repository eines Teams löst ebenfalls eine GitHub-Aktion aus. Durch diese Aktion wird der Code automatisch in die Entwicklungsverzweigung im Git-Repository von Cloud Manager gepusht. Dieser Code-Push löst jedoch nicht automatisch die produktionsfremde Pipeline aus. Sie wird durch einen Aufruf der API von Cloud Manager ausgelöst.

Das Ausführen der Produktions-Pipeline umfasst das Überprüfen des Codes aller Teams durch die bereitgestellten Quality Gates. Sobald der Code für die Staging-Umgebung bereitgestellt wurde, werden die Tests und Prüfungen ausgeführt, um sicherzustellen, dass alles erwartungsgemäß funktioniert. Wenn alle Qualitäts-Gate-Prüfungen bestanden sind, werden die Änderungen ohne Unterbrechung oder Ausfallzeiten in die Produktion überführt.

Für die lokale Entwicklung wird das [SDK für AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md#developing) verwendet. Das SDK ermöglicht die Einrichtung einer lokalen Authoring- und Publishing-Umgebung sowie eines Dispatchers. Dieser Workflow ermöglicht die Offline-Entwicklung und schnelle Durchlaufzeiten. Manchmal wird nur die Autorenumgebung für die Entwicklung verwendet, aber das schnelle Einrichten des Dispatchers und der Veröffentlichungsumgebung ermöglicht es, alles lokal zu testen, bevor es in das Git-Repository gepusht wird.

Mitglieder jedes Teams checken normalerweise den Code aus dem gemeinsamen Git-Repository für ihren eigenen Projekt-Code aus. Andere Projekte brauchen nicht ausgecheckt zu werden, weil die Projekte voneinander unabhängig sind.

![Lokaler Checkout und SDK](/help/implementing/cloud-manager/assets/team-setup3.png)

Dieses reale Setup kann als Entwurf verwendet und dann an die Bedürfnisse eines Unternehmens angepasst werden. Das flexible Verzweigungs- und Zusammenführungskonzept von Git ermöglicht Variationen der oben genannten Workflows, die auf die Anforderungen jedes Teams abgestimmt werden können. AEM as a Cloud Service unterstützt alle diese Varianten, ohne den Kernwert der bestimmenden Cloud Manager-Pipeline zu opfern.

>[!TIP]
>
>Für weitere Informationen zur Einrichtung lesen Sie [Arbeiten mit Git-Repositorys aus mehreren Quellen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/managing-code/multiple-git-repos#managing-code).

### Überlegungen zur Einrichtung mit mehreren Teams {#considerations}

Mit dem Git-Repository von Cloud Manager und der Produktions-Pipeline passiert der vollständige Produktions-Code immer alle Qualitäts-Gates und wird als eine einzige Bereitstellungseinheit behandelt. Auf diese Weise ist das Produktionssystem stets ohne Unterbrechung oder Ausfallzeiten verfügbar.

Ohne ein solches System besteht dagegen die Gefahr, dass eine Änderung eines einzelnen Teams zu Problemen mit der Produktionsstabilität führen kann, da jedes Team separat bereitstellen kann. Darüber hinaus sind für das Einspielen von Updates eine Koordinierung und geplante Ausfallzeiten erforderlich. Mit zunehmender Anzahl von Teams wird der Koordinierungsaufwand immer komplexer und schnell unkontrollierbar.

Wenn ein Problem in den Quality Gates erkannt wird, ist die Produktion nicht betroffen und das Problem kann erkannt und behoben werden, ohne dass Personal von Adobe eingreifen muss. Ohne Cloud Service und ohne immer die gesamte Bereitstellung zu testen, können partielle Bereitstellungen zu Ausfällen führen, die eine Anfrage zum Zurücksetzen oder sogar eine vollständige Wiederherstellung aus einem Backup erfordern. Wenn nur teilweise getestet wird, können zusätzliche Probleme auftreten, die später behoben werden müssen, was wiederum die Koordinierung und Unterstützung durch Personal von Adobe erfordert.

>[!TIP]
>
>Für jede Einrichtung mit mehreren Teams ist es entscheidend, ein Governance-Modell und einen Satz von Standards zu definieren, die alle Teams befolgen müssen. Der vorherige Blueprint für eine Einrichtung mit mehreren Teams, den Sie als Ausgangspunkt verwenden können, ermöglicht die Skalierung auf eine größere Anzahl von Teams.
