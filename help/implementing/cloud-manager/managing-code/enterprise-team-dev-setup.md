---
title: Einrichten eines Entwicklungs-Teams für Unternehmen
description: Erfahren Sie, wie Sie Ihr Entwicklungs-Team für Unternehmen einrichten und skalieren, und sehen Sie, wie AEM as a Cloud Service Ihren Entwicklungsprozess unterstützen kann.
exl-id: 85f8779b-12cb-441b-a34d-04641184497a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: cbeb3d8f5fa5cbf1839e1e8c5e651329b06e60a4
workflow-type: tm+mt
source-wordcount: '1401'
ht-degree: 40%

---

# Einrichten des Enterprise-Entwicklungsteams für AEM as a Cloud Service {#enterprise-setup}

Erfahren Sie, wie Sie Ihr Enterprise-Entwicklungsteam einrichten und skalieren und wie AEM (Adobe Experience Manager) as a Cloud Service Ihren Entwicklungsprozess unterstützen kann.

## Einführung {#introduction}

Zur Unterstützung von Kundinnen und Kunden mit unternehmensweiten Entwicklungskonfigurationen ist AEM as a Cloud Service vollständig mit Cloud Manager und dafür vorgesehenen, [opinionierten CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) integriert. Diese Pipelines und Dienste basieren auf Best Practices und gewährleisten sorgfältige [Tests und höchste Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md).

## Cloud Manager-Unterstützung bei der Teamentwicklung in Unternehmen {#cloud-manager}

Um ein schnelles Onboarding zu gewährleisten, bietet Cloud Manager alles, was für die ersten Schritte mit der Entwicklung digitaler Erlebnisse erforderlich ist, einschließlich eines Git-Repositorys zum Speichern von Anpassungen, die dann von Cloud Manager erstellt, überprüft und bereitgestellt werden.

Mit Cloud Manager können Entwicklungs-Teams auf die häufige Durchführung von Änderungen hinarbeiten, ohne auf Personal von Adobe angewiesen zu sein.

In Cloud Manager sind drei Arten von Umgebungen verfügbar.

* Entwicklung
* Staging
* Produktion

Der Code kann über eine produktionsfremde Pipeline in Entwicklungsumgebungen bereitgestellt werden. Bei Staging- und Produktionsumgebungen, die immer zusammengehören und so als Best Practice eine Validierung vor der Produktionsbereitstellung sicherstellen, verwendet eine Produktions-Pipeline [Quality Gates](/help/implementing/cloud-manager/custom-code-quality-rules.md), um den Code des Programms und die Konfigurationsänderungen zu validieren.

Die Produktions-Pipeline stellt den Code und die Konfiguration zuerst in der Staging-Umgebung bereit, testet die Anwendung und stellt sie schließlich für die Produktion bereit.

Ein Cloud Service-SDK, das immer mit den neuesten AEM as a Cloud Service-Verbesserungen aktualisiert wird, ermöglicht die lokale Entwicklung direkt unter Verwendung der lokalen Hardware des Entwicklers. Dieser Ansatz ermöglicht eine schnelle Entwicklung mit sehr niedrigen Bearbeitungszeiten. So können Entwickler in ihrer vertrauten lokalen Umgebung bleiben und aus einer Vielzahl von Entwicklungs-Tools wählen und in Entwicklungsumgebungen oder Produktionsumgebungen pushen, wenn sie es für richtig halten.

Cloud Manager unterstützt flexible Multi-Team-Setups, die an die Anforderungen eines Unternehmens angepasst werden können. Um eine stabile Bereitstellung über mehrere Teams hinweg sicherzustellen, validiert und testet die von Cloud Manager angezeigte Pipeline den Code von allen Teams gemeinsam. Dieser Ansatz verhindert Situationen, in denen sich die Änderungen eines Teams auf die Produktion für alle Teams auswirken.

## Beispiel der realen Welt {#real-world-example}

Jedes Unternehmen hat unterschiedliche Anforderungen, dazu gehören verschiedene Teams, Prozesse und Entwicklungs-Workflows. Das unten beschriebene Setup wird von Adobe für verschiedene Projekte verwendet, die Erlebnisse zusätzlich zu AEM as a Cloud Service bereitstellen.

Die Adobe Creative Cloud-Programme wie Adobe Photoshop oder Adobe Illustrator enthalten beispielsweise Inhaltsressourcen wie Tutorials, Beispiele und Handbücher, die Endbenutzern zur Verfügung stehen. Clientanwendungen nutzen Inhalte aus AEM as a Cloud Service Headless. Sie führen API-Aufrufe an die AEM Cloud-Veröffentlichungsstufe, um strukturierte Inhalte als JSON-Streams abzurufen. Darüber hinaus wird das [CDN (Content Delivery Network) in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md#content-delivery) verwendet, um strukturierte und unstrukturierte Inhalte mit optimaler Leistung bereitzustellen.

Die Teams, die zu diesem Projekt beitragen, folgen dem folgenden Prozess.

Jedes Team verwendet seinen eigenen Entwicklungs-Workflow und verfügt über ein eigenes Git-Repository. Für das Onboarding von Projekten wird ein zusätzliches freigegebenes Git-Repository verwendet. Dieses Git-Repository enthält die Stammstruktur des Git-Repositorys von Cloud Manager, einschließlich der freigegebenen Dispatcher-Konfiguration.

Für das Onboarding eines neuen Projekts ist es erforderlich, die Datei des Reaktor Maven-Projekts im Stammverzeichnis des freigegebenen Git-Repositorys aufzulisten. Für die Dispatcher-Konfiguration wird innerhalb des Dispatcher-Projekts eine neue Konfigurationsdatei erstellt. Die Dispatcher-Hauptkonfiguration enthält dann diese Datei. Jedes Team ist für seine eigene Dispatcher-Konfigurationsdatei verantwortlich. Änderungen am freigegebenen Git-Repository sind selten und in der Regel nur erforderlich, wenn ein neues Projekt integriert wird. Die Hauptarbeit wird von jedem Projektteam in seinem eigenen Git-Repository ausgeführt.

![Workflow-Diagramm](/help/implementing/cloud-manager/assets/team-setup1.png)

Das Git-Repository für jede wird mit dem Projektarchetyp [AEM ](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/overview) eingerichtet und folgt daher den Best Practices für die Einrichtung AEM Projekte. Die einzige Ausnahme ist die Dispatcher-Konfiguration, die wie oben beschrieben im freigegebenen Git-Repository ausgeführt wird.

Jedes Team verwendet einen vereinfachten Git-Workflow mit zwei + N Verzweigungen, die dem Git-Flussmodell folgen:

* Eine stabile Versionsverzweigung enthält den Produktions-Code.

* Eine Entwicklungsverzweigung enthält die neueste Entwicklung.

* Für jede Funktion wird eine neue Verzweigung erstellt.

Die Entwicklung erfolgt in einer Funktionsverzweigung. Wenn die Funktion ausgereift ist, wird sie in der Entwicklungsverzweigung zusammengeführt. Abgeschlossene und validierte Funktionen werden aus der Entwicklungsverzweigung ausgewählt und in der stabilen Verzweigung zusammengeführt.

Alle Änderungen erfolgen über PRs (Pull Requests). Quality Gates validieren automatisch jede PR. Bei der Qualitätsprüfung des Codes kommt Sonar zum Einsatz und es wird eine Reihe von Testfolgen ausgeführt, um sicherzustellen, dass der neue Code keine Regression einführt.

Das Setup im Git-Repository von Cloud Manager umfasst zwei Verzweigungen.

* Eine Verzweigung für stabile Versionen, die den Produktions-Code aller Teams enthält.
* Eine Entwicklungsverzweigung, die den Entwicklungs-Code aller Teams enthält.

Bei jedem Push an das Git-Repository eines Teams in der Entwicklungs- oder der stabilen Verzweigung wird eine [GitHub-Trigger](/help/implementing/cloud-manager/managing-code/working-with-multiple-source-git-repositories.md#managing-code) angezeigt.

Alle Projekte folgen demselben Setup für die stabile Verzweigung. Ein Push in die stabile Verzweigung eines Projekts wird automatisch in die stabile Verzweigung im Git-Repository von Cloud Manager gepusht. Ein Push an den stabilen Zweig Trigger die Produktions-Pipeline in Cloud Manager. Jedes Pushen eines beliebigen Teams in einen stabilen Zweig Trigger die Produktions-Pipeline. Die Produktionsbereitstellung wird aktualisiert, wenn alle Quality Gates (Gate-Tests) bestehen.

![Push-Diagramm](/help/implementing/cloud-manager/assets/team-setup2.png)

Push-Vorgänge zur Entwicklungsverzweigung werden anders gehandhabt. Eine Push-Benachrichtigung an eine Entwicklerverzweigung im Git-Repository eines Teams Trigger auch eine GitHub-Aktion. Durch diese Aktion wird der Code automatisch in die Entwicklungsverzweigung im Git-Repository von Cloud Manager übertragen. Diese Code-Push-Benachrichtigung Trigger jedoch nicht automatisch die produktionsfremde Pipeline. Ein Aufruf an die Cloud Manager-API-Trigger.

Das Ausführen der Produktions-Pipeline umfasst das Überprüfen des Codes aller Teams durch die bereitgestellten Quality Gates. Nachdem der Code für die Staging-Umgebung bereitgestellt wurde, werden die Tests und Prüfungen ausgeführt, damit alles erwartungsgemäß funktioniert. Wenn alle Akzeptanztests durchgeführt werden, werden die Änderungen ohne Unterbrechung oder Ausfallzeiten in die Produktion eingeführt.

Für die lokale Entwicklung wird das [SDK für AEM as a Cloud Service](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md#developing) verwendet. Das SDK ermöglicht die Einrichtung eines lokalen Autors, einer lokalen Veröffentlichung und Dispatcher. Dieser Workflow ermöglicht die Offline-Entwicklung und die schnelle Abwicklung. Manchmal wird nur die Autorenumgebung für die Entwicklung verwendet. Durch die schnelle Einrichtung von Dispatcher- und Veröffentlichungsumgebungen können Sie jedoch alles lokal testen, bevor Sie in das Git-Repository übertragen.

Mitglieder jedes Teams checken den Code normalerweise aus dem freigegebenen Git für ihren eigenen Projektcode aus. Andere Projekte müssen nicht ausgecheckt werden, da die Projekte unabhängig sind.

![Lokaler Checkout und SDK](/help/implementing/cloud-manager/assets/team-setup3.png)

Dieses reale Setup kann als Entwurf verwendet und dann an die Bedürfnisse eines Unternehmens angepasst werden. Das flexible Verzweigungs- und Zusammenführungskonzept von Git ermöglicht Varianten der oben genannten Workflows, die auf die Anforderungen jedes Teams abgestimmt sind. AEM as a Cloud Service unterstützt alle diese Varianten, ohne den Kernwert der bestimmenden Cloud Manager-Pipeline zu opfern.

>[!TIP]
>
>Weitere Informationen zu diesem Setup finden Sie unter [Arbeiten mit mehreren Source-Git-Repositorys](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/managing-code/multiple-git-repos#managing-code) .

### Überlegungen zum Einrichten mehrerer Teams {#considerations}

Mit dem Git-Repository von Cloud Manager und der Produktions-Pipeline durchläuft der vollständige Produktionscode immer alle Quality Gates und behandelt ihn als eine Implementierungseinheit. Auf diese Weise ist das Produktionssystem stets ohne Unterbrechung oder Ausfallzeiten verfügbar.

Ohne ein solches System besteht dagegen die Gefahr, dass ein Update eines einzelnen Teams zu Problemen mit der Produktionsstabilität führen kann, da jedes Team es separat bereitstellen kann. Darüber hinaus sind eine Koordinierung und geplante Ausfallzeiten erforderlich, um Aktualisierungen einzuführen. Mit zunehmender Anzahl von Teams wird der Koordinierungsaufwand immer komplexer und schnell unkontrollierbar.

Wenn ein Problem in den Quality Gates erkannt wird, ist die Produktion nicht betroffen und das Problem kann erkannt und behoben werden, ohne dass Personal von Adobe eingreifen muss. Ohne Cloud Service und ohne immer die gesamte Bereitstellung zu testen, können partielle Bereitstellungen zu Ausfällen führen, die eine Anfrage zum Zurücksetzen oder sogar eine vollständige Wiederherstellung aus einem Backup erfordern. Teiltests können auch zu zusätzlichen Problemen führen, die später gelöst werden müssen, was wiederum eine Koordinierung und Unterstützung durch Adobe-Mitarbeiter erfordert.

>[!TIP]
>
>Für jedes Multi-Team-Setup ist es von entscheidender Bedeutung, ein Governance-Modell und eine Reihe von Standards zu definieren, denen alle Teams folgen müssen. Der vorherige Blueprint für ein Multi-Team-Setup ermöglicht die Skalierung auf eine größere Anzahl von Teams, die Sie als Ausgangspunkt verwenden können.
