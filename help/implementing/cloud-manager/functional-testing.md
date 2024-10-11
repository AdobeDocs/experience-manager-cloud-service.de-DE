---
title: Funktionstests
description: Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die im AEM as a Cloud Service-Implementierungsprozess integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '1321'
ht-degree: 58%

---


# Einführung {#functional-testing-introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Funktionstests"
>abstract="Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die im AEM as a Cloud Service-Implementierungsprozess integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen."

Erfahren Sie mehr über die im [AEM as a Cloud Service-Implementierungsprozess](/help/implementing/cloud-manager/deploy-code.md) verfügbaren Qualitätstests und die verschiedenen Arten integrierter Funktionstests. Erfahren Sie, wie Sie im Rahmen einer umfassenden Teststrategie ihren Einsatz optimieren können.

## Über Funktionstests

Das folgende Diagramm bietet einen allgemeinen Überblick über die verfügbaren Pipelines im Kontext einer Gesamtteststrategie und des [AEM as a Cloud Service-Bereitstellungsprozesses](/help/implementing/cloud-manager/deploy-code.md).

![Qualitäts-Gates für die AEM Cloud Service-Bereitstellung](assets/functional-testing/quality-gates-compact.svg)

## Zweck der Funktionstests

Die Pipelines zur AEM Cloud Service-Implementierung haben den Zweck, eine robuste und sichere Bereitstellung in verschiedenen Phasen des Entwicklungs- und AEM-Produktveröffentlichungslebenszyklus zu erleichtern. Diese Pipelines enthalten mehrere Qualitäts-Gates auf unterschiedlichen Ebenen, um die Integrität und Sicherheit von Bereitstellungen sowohl für Ihre AEM-Anwendungsänderungen als auch für AEM-Produktaktualisierungen zu gewährleisten.

Adobe bietet mehrere integrierte Qualitäts-Gates, während andere Ihren Eingriff für die Implementierung und Konfiguration erfordern. Diese Qualitätstests sind vielseitig, werden in verschiedenen Lebenszyklusphasen angewendet und direkt in Ihre Entwicklungs- und CI/CD-Prozesse integriert.

Die integrierten Qualitäts-Gates validieren in erster Linie die Funktionalität des AEM-Produkts im Kontext Ihrer AEM-Anwendung. Die von Ihnen eingerichteten benutzerdefinierten QualitätsGates hingegen dienen dazu, zu überprüfen, ob die kritischen Funktionen und Benutzerinteraktionen Ihrer Anwendung wie gewünscht funktionieren. Gemeinsam arbeiten diese beiden Sets von Qualitäts-Gates zusammen, um eine robuste und sichere automatisierte Bereitstellung sowohl für Ihre Änderungen am Code als auch für AEM-Produktaktualisierungen sicherzustellen.

Es ist wichtig zu beachten, dass diese Qualitäts-Gates nicht als umfassendes Test-Framework für Ihre gesamte Teststrategie gedacht sind. Das AEM-Produkt wird umfassend getestet, bevor es in den AEM Cloud Service-Bereitstellungsprozess eintritt. Ebenso sollte Ihre Anwendung bereits von hoher Qualität sein, bevor sie die Bereitstellungsphase erreicht. Dieser Ansatz stellt sicher, dass sich die Qualitäts-Gates auf ihr vorrangiges Ziel konzentrieren, den sicheren Implementierungsprozess zu gewährleisten, anstatt ein vollständiges Testverfahren zu ersetzen.

## Qualitätstests

Das folgende Diagramm bietet einen detaillierten Überblick über die verfügbaren Qualitäts-Gates und deren Verwendung in der Gesamtteststrategie sowie den [AEM as a Cloud Service-Bereitstellungsprozess](/help/implementing/cloud-manager/deploy-code.md).

![Qualitäts-Gates für die AEM Cloud Service-Bereitstellung](assets/functional-testing/quality-gates-overview.svg)

### Zusammenfassende vom Kunden bereitgestellte Quality Gates

|                               | Komponententests | Benutzerdefinierte<br/> Funktionstests | Benutzerdefinierte<br/> Benutzeroberflächentests | Kundenvalidierungen<br/> | Manuelle<br/> Tests |
|:------------------------------|:---------------------:|:-----------------------------------:|:-----------------------------------:|:-------------------------:|:-------------------:|
| **Produktions-Pipeline** | Ja<br/>Blockieren<br/> | Ja<br/>Blockieren<br/>60 min Zeitüberschreitung | Ja<br/>Blockieren<br/>30 min Zeitüberschreitung | Nein | Nein |
| **Produktionsfremde Pipeline** | Ja<br/>Blockieren<br/> | Opt-in<br/>Blockieren<br/>60 min Zeitüberschreitung | Opt-in<br/>Blockieren<br/>30 min Zeitüberschreitung | Nein | Nein |
| **Interne Adobe-Validierung** | Ja<br/>Blockieren<br/> | Ja<br/>Blockieren<br/>60 min Zeitüberschreitung | Ja<br/>Blockieren<br/>30 min Zeitüberschreitung | Nein | Nein |
| **Kunden-CI/CD** | Ja | Ja | Ja | Ja | Ja |
| **Lokaler Entwickler für Kunden** | Ja | Ja | Ja | Ja | Ja |

### Unit-Test

Es wird empfohlen, die Komponententests für Ihre AEM-Anwendung bereitzustellen. Sie bilden die Grundlage jeder Teststrategie. Sie sollten schnell und oft ausgeführt werden und frühzeitig und schnell Feedback geben. Sie sind eng in die Entwickler-Workflows, Ihre eigenen CI/CD- und die AEM Cloud Service-Bereitstellungs-Pipelines integriert.

Sie werden mit JUnit implementiert und mit Maven ausgeführt. Im [Kernmodul des AEM Projektarchetyps](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/developing/archetype/using#unit-tests) finden Sie einen BeispielKomponententest für AEM und erste Schritte.

### Code-Qualität

Dieser Qualitätstest ist standardmäßig konfiguriert und führt eine statische Code-Analyse für Ihren AEM-Anwendungs-Code durch.

Unter [Testen der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md) und [Qualitätsregeln für benutzerspezifischen Code](/help/implementing/cloud-manager/custom-code-quality-rules.md) finden Sie weitere Informationen.

### Produkttests

Produktfunktionstests sind stabile HTTP-Integrationstests (ITs) für die Kernfunktionalität der AEM, einschließlich Authoring- und Replikationsaufgaben. Adobe stellt sie standardmäßig bereit und verwaltet sie. Sie sollen verhindern, dass Änderungen an benutzerdefiniertem Anwendungs-Code bereitgestellt werden, wenn dadurch die Kernfunktionalität im AEM-Produkt beeinträchtigt wird.

Sie verwenden JUnit für die Implementierung, führen mit Maven aus und sind auf die offiziellen [AEM Testing Clients](https://github.com/adobe/aem-testing-clients) angewiesen. Die Produkttestsuite wird als 
[Open-Source-Projekt](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) verwaltet, folgt Best Practices und kann als guter Ausgangspunkt für die Implementierung Ihrer Tests betrachtet werden.

### Benutzerdefinierte Funktionstests

Ähnlich wie bei den Produkttests sind Kundenfunktionstests HTTP-Integrationstests (ITs), die mit JUnit implementiert wurden, mit Maven ausgeführt werden und auf den offiziellen [AEM Testing Clients](https://github.com/adobe/aem-testing-clients) aufbauen.

>[!NOTE]
>
>Benutzerdefinierte Funktionstests werden sowohl in Produktions- als auch Nicht-Produktions-Pipelines (Opt-in) ausgeführt, die für AEM Implementierungen von Anwendungsänderungen und AEM Produkt-Push-Aktualisierungen verwendet werden. Sie spielen eine entscheidende Rolle bei der ordnungsgemäßen Funktionsfähigkeit Ihrer Anwendung und bei der Verbesserung der Sicherheit der Freisetzung. Die Kundenfunktionstests werden auch in internen Validierungs-Pipelines vor der Veröffentlichung für jede Kundin und jeden Kunden ausgeführt. Dies trägt zu frühzeitigem Feedback bei.

Um effiziente Pipelineabläufe zu gewährleisten, empfiehlt Adobe, sich auf wichtige Funktionen und die Interaktionsflüsse der primären Benutzer zu konzentrieren und eine funktionale Testlaufzeit von höchstens 15 Minuten zu erreichen. Vollständige Funktionstest-Suites, die diese Zeit überschreiten, sollten während des Entwicklungsprozesses als Teil der allgemeinen Kunden-Validierungs-Pipelines ausgeführt werden.

Beispiele finden Sie unter [Open-Source-Produkttests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) oder [it.tests-Modul des AEM-Projektarchetyps](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests).

Weitere Informationen finden Sie unter [Java-Funktionstests](/help/implementing/cloud-manager/java-functional-testing.md).

### Benutzerdefinierte UI-Tests

Um die Risikokontrolle für Ihre kundenspezifische Entwicklung zu maximieren, empfiehlt Ihnen Adobe, kritische Benutzeroberflächentests in AEM as a Cloud Service zu erfassen. Beschränken Sie Ihre Aktivitäten, konzentrieren Sie sich aber darauf, ihre Wirkung auf das Kundenerlebnis zu maximieren.

Die Tests sind in einem Docker-Image verpackt, das so flüchtig wie möglich ist (mit Unterstützung für Cypress, Selenium, Java und JavaScript). Sie folgen denselben Merkmalen und Zwecken wie die benutzerdefinierten Funktionstests.

>[!NOTE]
>
>Benutzerdefinierte UI-Tests werden sowohl in Produktions- als auch Nicht-Produktions-Pipelines (Opt-in) ausgeführt, die für AEM Bereitstellung von Anwendungsänderungen und AEM Produkt-Push-Aktualisierungen verwendet werden. Sie sind unverzichtbar, um das ordnungsgemäße Funktionieren Ihrer Anwendung sicherzustellen und die Sicherheit der Freisetzung zu erhöhen. Die benutzerdefinierten Benutzeroberflächentests werden auch in internen Validierungs-Pipelines vor der Veröffentlichung für jeden Kunden und jede Kundin ausgeführt. Dies trägt zu frühzeitigem Feedback bei.
>
>Nicht-Selenium-Container sollten Tests mithilfe eines HTTP-Proxys ausführen, der auf den Umgebungsvariablen im [UI-Tests-Abschnitt](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) beruht.

Um Pipeline-Ausführungen effizient zu gestalten, empfiehlt Adobe, sich auf wichtige Funktionen und die wichtigsten Benutzerinteraktionsflüsse zu konzentrieren. Vollständige Test-Suites der Benutzeroberfläche, die dieses Quality Gate überschreiten, sollten als Teil der allgemeinen Test-Pipelines zur Kundenvalidierung ausgeführt werden. Integrieren Sie sie in den Entwicklungsprozess des Kunden.

Beispiele finden Sie unter [Open-Source-Beispieltests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/) oder [ui.tests-Modul des AEM-Projektarchetyps](/help/implementing/cloud-manager/ui-testing.md).

Weitere Informationen finden Sie unter [Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

### Erlebnisprüfung

Der Experience Audit-Qualitätstest führt [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/)-Audits auf der Webseite des Kunden durch.

Dieser Qualitätstest wird von AEM vordefiniert bereitgestellt, blockiert jedoch nicht die Bereitstellungs-Pipelines. Standardmäßig wird ein Audit für die Stammseite (`/`) der Veröffentlichungsinstanz durchgeführt. Sie können einen Beitrag leisten, indem Sie bis zu 25 benutzerdefinierte Pfade konfigurieren, die für Audits berücksichtigt werden.

Weitere Details finden Sie unter [Testen mit Experience Audit](/help/implementing/cloud-manager/experience-audit-dashboard.md).

### Kundenvalidierungen

Der Qualitätstest für Kundenvalidierungen ist ein Platzhalter für die eigene Teststrategie und den eigenen Aufwand auf Kundenseite. Er wird ausgeführt, bevor die kundenseitigen Anwendungsänderungen die AEM-Cloud-Bereitstellungs-Pipelines erreichen.

Hier können Sie die Tools und Frameworks auswählen, die Sie bevorzugen. Im Gegensatz zu Kundenfunktionstests und benutzerdefinierten UI-Tests gibt es keine AEM as a Cloud Service-bezogenen Beschränkungen. Daher empfiehlt Adobe, dass Sie hier langwierige Funktionstests und Benutzeroberflächentests durchführen.

Obwohl Sie ein beliebiges Tool und Framework auswählen können, empfiehlt Adobe, HTTP-basierte Integrations- und UI-Tests mit den Tools und Frameworks abzugleichen, die in den benutzerdefinierten Test-Qualitätstests für Funktionen und Benutzeroberflächen verwendet werden. Darüber hinaus empfiehlt Adobe, [Rapid Development Environments (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md) in Ihre lokale Teststrategie zu integrieren, um AEM Cloud-Umgebungen eng zu spiegeln.

### Manuelle Tests

Das Qualitäts-Gate für manuelle Tests ist ein Platzhalter für Kunden, die manuelle Tests durchführen. Da AEM Cloud-Pipelines manuelle Tests nicht unterstützen, muss sie in Ihre lokale Teststrategie aufgenommen werden.

Für manuelle Tests kann die Integration in eine zusätzliche AEM Cloud Service-Entwicklungsumgebung nützlich sein.
