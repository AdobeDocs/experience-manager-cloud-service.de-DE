---
title: Funktionstests
description: Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den Bereitstellungsprozess von AEM as a Cloud Service integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 05531a5c1eca996bd3652d6ce6233b7a960d0bc9
workflow-type: ht
source-wordcount: '1322'
ht-degree: 100%

---


# Einführung {#functional-testing-introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Funktionstests"
>abstract="Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den Bereitstellungsprozess von AEM as a Cloud Service integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen."

Lernen Sie die im [AEM as a Cloud Service-Bereitstellungsprozess](/help/implementing/cloud-manager/deploy-code.md) verfügbaren Qualitäts-Gates und die verschiedenen Arten integrierter Funktionstests kennen. Erfahren Sie, wie Sie im Rahmen einer umfassenden Teststrategie ihren Einsatz optimieren können.

## Über Funktionstests

Das folgende Diagramm bietet einen allgemeinen Überblick über die verfügbaren Pipelines im Kontext einer Gesamtteststrategie und des [AEM as a Cloud Service-Bereitstellungsprozesses](/help/implementing/cloud-manager/deploy-code.md).

![Qualitäts-Gates für die AEM Cloud Service-Bereitstellung](assets/functional-testing/quality-gates-compact.svg)

## Zweck der Funktionstests

Die Pipelines zur AEM Cloud Service-Implementierung haben den Zweck, eine robuste und sichere Bereitstellung in verschiedenen Phasen des Entwicklungs- und AEM-Produktveröffentlichungslebenszyklus zu erleichtern. Diese Pipelines enthalten mehrere Qualitäts-Gates auf unterschiedlichen Ebenen, um die Integrität und Sicherheit von Bereitstellungen sowohl für Ihre AEM-Anwendungsänderungen als auch für AEM-Produktaktualisierungen zu gewährleisten.

Adobe bietet mehrere integrierte Qualitäts-Gates, während andere Ihren Eingriff für die Implementierung und Konfiguration erfordern. Diese Qualitäts-Gates sind vielseitig, werden in verschiedenen Phasen des Lebenszyklus angewendet und direkt in Ihre Entwicklungseinrichtung sowie CI/CD-Prozesse integriert.

Die integrierten Qualitäts-Gates validieren in erster Linie die Funktionalität des AEM-Produkts im Kontext Ihrer AEM-Anwendung. Die von Ihnen eingerichteten benutzerdefinierten QualitätsGates hingegen dienen dazu, zu überprüfen, ob die kritischen Funktionen und Benutzerinteraktionen Ihrer Anwendung wie gewünscht funktionieren. Gemeinsam arbeiten diese beiden Sets von Qualitäts-Gates zusammen, um eine robuste und sichere automatisierte Bereitstellung sowohl für Ihre Änderungen am Code als auch für AEM-Produktaktualisierungen sicherzustellen.

Es ist wichtig zu beachten, dass diese Qualitäts-Gates nicht als umfassendes Test-Framework für Ihre gesamte Teststrategie gedacht sind. Das AEM-Produkt wird umfassend getestet, bevor es in den AEM Cloud Service-Bereitstellungsprozess eintritt. Ebenso sollte Ihre Anwendung bereits von hoher Qualität sein, bevor sie die Bereitstellungsphase erreicht. Dieser Ansatz stellt sicher, dass sich die Qualitäts-Gates auf ihr vorrangiges Ziel konzentrieren, den sicheren Implementierungsprozess zu gewährleisten, anstatt ein vollständiges Testverfahren zu ersetzen.

## Qualitäts-Gates beim Testen

Das folgende Diagramm bietet einen detaillierten Überblick über die verfügbaren Qualitäts-Gates und deren Verwendung in der Gesamtteststrategie sowie den [AEM as a Cloud Service-Bereitstellungsprozess](/help/implementing/cloud-manager/deploy-code.md).

![Qualitäts-Gates für die AEM Cloud Service-Bereitstellung](assets/functional-testing/quality-gates-overview.svg)

### Zusammenfassung zu kundenseitig bereitgestellten Qualitäts-Gates

|                               | Komponententests | Benutzerdefinierte<br/> Funktionstests | Benutzerdefinierte<br/> Benutzeroberflächentests | Kundenvalidierungen<br/> | Manuelle<br/> Tests |
|:------------------------------|:---------------------:|:-----------------------------------:|:-----------------------------------:|:-------------------------:|:-------------------:|
| **Produktions-Pipeline** | Ja<br/>Blockieren<br/> | Ja<br/>Blockieren<br/>60 min Zeitüberschreitung | Ja<br/>Blockieren<br/>30 min Zeitüberschreitung | Nein | Nein |
| **Produktionsfremde Pipeline** | Ja<br/>Blockieren<br/> | Opt-in<br/>Blockieren<br/>60 min Zeitüberschreitung | Opt-in<br/>Blockieren<br/>30 min Zeitüberschreitung | Nein | Nein |
| **Interne Adobe-Validierung** | Ja<br/>Blockieren<br/> | Ja<br/>Blockieren<br/>60 min Zeitüberschreitung | Ja<br/>Blockieren<br/>30 min Zeitüberschreitung | Nein | Nein |
| **Kunden-CI/CD** | Ja | Ja | Ja | Ja | Ja |
| **Lokaler Entwickler für Kunden** | Ja | Ja | Ja | Ja | Ja |

### Komponententest

Es wird empfohlen, die Komponententests für Ihre AEM-Anwendung bereitzustellen. Sie bilden die Grundlage jeder Teststrategie. Sie sollten schnell und oft ausgeführt werden und frühzeitig und schnell Feedback geben. Sie sind eng in die Entwickler-Workflows, Ihre eigenen CI/CD- und die AEM Cloud Service-Bereitstellungs-Pipelines integriert.

Sie werden mit JUnit implementiert und mit Maven ausgeführt. Unter [Kernmodul des AEM-Projektarchetyps](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/using#unit-tests) finden Sie ein Beispiel für einen Komponententest für AEM und die ersten Schritte damit.

### Code-Qualität

Dieser Qualitätstest ist standardmäßig konfiguriert und führt eine statische Code-Analyse für Ihren AEM-Anwendungs-Code durch.

Unter [Testen der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md) und [Qualitätsregeln für benutzerspezifischen Code](/help/implementing/cloud-manager/custom-code-quality-rules.md) finden Sie weitere Informationen.

### Produkttests

Produktfunktionstests sind stabile HTTP-Integrationstests (ITs) für Kernfunktionen in AEM wie Authoring- und Replikationsaufgaben. Adobe stellt sie standardmäßig bereit und verwaltet sie. Sie sollen verhindern, dass Änderungen an benutzerdefiniertem Anwendungs-Code bereitgestellt werden, wenn dadurch die Kernfunktionalität im AEM-Produkt beeinträchtigt wird.

Sie verwenden JUnit für die Implementierung, werden mithilfe von Maven ausgeführt und stützen sich auf die offiziellen [AEM-Test-Clients](https://github.com/adobe/aem-testing-clients). Die Produkttestsuite wird als 
[Open-Source-Projekt](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) verwaltet, folgt Best Practices und kann als guter Ausgangspunkt für die Implementierung Ihrer Tests betrachtet werden.

### Benutzerdefinierte Funktionstests

Ähnlich wie die Produkttests sind Kundenfunktionstests HTTP-Integrationstests (ITs) und werden ebenso mit JUnit implementiert, mithilfe von Maven ausgeführt und auf den offiziellen [AEM-Test-Clients](https://github.com/adobe/aem-testing-clients) erstellt.

>[!NOTE]
>
>Benutzerdefinierte Funktionstests werden in den Produktions-Pipelines und produktionsfremden (Opt-in-)Pipelines ausgeführt, die von den Bereitstellungen der AEM-Anwendungsänderungen und Push-Updates für AEM-Produkte verwendet werden. Sie spielen eine entscheidende Rolle bei der Sicherstellung der ordnungsgemäßen Funktionsfähigkeit Ihrer Anwendung und bei der Verbesserung der Versionssicherheit. Die Kundenfunktionstests werden auch für jede Kundin und jeden Kunden in internen Validierungs-Pipelines vor der Veröffentlichung ausgeführt. Dies trägt zu frühzeitigem Feedback bei.

Um effiziente Pipeline-Ausführungen zu gewährleisten, empfiehlt Adobe, sich auf wichtige Funktionen und die Interaktionsflüsse der primären Benutzenden zu konzentrieren und eine funktionale Testlaufzeit von höchstens 15 Minuten anzustreben. Vollständige Funktionstestsuiten, die diese Dauer überschreiten, sollten im Rahmen der allgemeinen Kundenvalidierungs-Pipelines während des Entwicklungsprozesses ausgeführt werden.

Beispiele finden Sie unter [Open-Source-Produkttests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) oder [it.tests-Modul des AEM-Projektarchetyps](https://github.com/adobe/aem-project-archetype/tree/develop/src/main/archetype/it.tests).

Weitere Informationen finden Sie unter [Java-Funktionstests](/help/implementing/cloud-manager/java-functional-testing.md).

### Benutzerdefinierte Benutzeroberflächentests

Um die Risikokontrolle für Ihre kundenspezifische Entwicklung zu maximieren, empfiehlt Ihnen Adobe dringend, kritische Benutzeroberflächentests in AEM as a Cloud Service zu erfassen. Beschränken Sie deren Anzahl und konzentrieren Sie sich stattdessen darauf, ihre Wirkung auf das Kundenerlebnis zu maximieren.

Die Tests sind in einem Docker-Image verpackt, das so flexibel wie möglich ist (mit Unterstützung für Cypress, Playwright, Selenium, Java und JavaScript). Sie folgen denselben Merkmalen und Zwecken wie die benutzerdefinierten Funktionstests.

>[!NOTE]
>
>Benutzerdefinierte Benutzeroberflächentests werden in den Produktions-Pipelines und produktionsfremden (Opt-in-)Pipelines ausgeführt, die von den Bereitstellungen der AEM-Anwendungsänderungen und Push-Updates für AEM-Produkte verwendet werden. Sie sind unerlässlich, um die ordnungsgemäße Funktionsfähigkeit Ihrer Anwendung sicherzustellen und die Versionssicherheit zu erhöhen. Die benutzerdefinierten Benutzeroberflächentests werden auch für jeden Kunden und jede Kundin in internen Validierungs-Pipelines vor der Veröffentlichung ausgeführt. Dies trägt zu frühzeitigem Feedback bei.
>
>Nicht-Selenium-Container sollten Tests mithilfe eines HTTP-Proxys ausführen, der auf den Umgebungsvariablen im [UI-Tests-Abschnitt](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing) beruht.

Damit Pipeline-Ausführungen effizient bleiben, empfiehlt Adobe, dass Sie sich auf Schlüsselfunktionen und die wichtigsten Benutzerinteraktionsabläufe konzentrieren. Umfassende Test-Suites der Benutzeroberfläche, die dieses Quality Gate übertreffen, sollten als Teil der allgemeinen Kundenvalidierungs-Pipelines ausgeführt werden. Integrieren Sie sie in den Entwicklungsprozess der Kundin bzw. des Kunden.

Beispiele finden Sie unter [Open-Source-Beispieltests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/) oder [ui.tests-Modul des AEM-Projektarchetyps](/help/implementing/cloud-manager/ui-testing.md).

Weitere Informationen finden Sie unter [Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

### Erlebnisprüfung

Der Experience Audit-Qualitätstest führt [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/)-Audits auf der Webseite des Kunden durch.

Dieser Qualitätstest wird von AEM vordefiniert bereitgestellt, blockiert jedoch nicht die Bereitstellungs-Pipelines. Standardmäßig wird ein Audit für die Stammseite (`/`) der Veröffentlichungsinstanz durchgeführt. Sie können einen Beitrag leisten, indem Sie bis zu 25 benutzerdefinierte Pfade konfigurieren, die für Audits berücksichtigt werden.

Weitere Details finden Sie unter [Testen mit Experience Audit](/help/implementing/cloud-manager/experience-audit-dashboard.md).

### Kundenvalidierungen

Der Qualitätstest für Kundenvalidierungen ist ein Platzhalter für die kundeneigene Teststrategie und den Testaufwand auf Kundenseite. Er wird ausgeführt, bevor die kundenseitigen Anwendungsänderungen die AEM-Cloud-Bereitstellungs-Pipelines erreichen.

Hier können Sie die Tools und Frameworks auswählen, die Sie bevorzugen. Im Gegensatz zu Kundenfunktionstests und benutzerdefinierten Benutzeroberflächentests gibt es keine mit AEM as a Cloud Service zusammenhängenden Beschränkungen. Daher empfiehlt Adobe, hier langwierige Funktions- und Benutzeroberflächentests durchzuführen.

Sie können zwar ein beliebiges Tool und Framework wählen, Adobe empfiehlt jedoch, HTTP-basierte Integrationstests und Benutzeroberflächentests mit den Tools und Frameworks abzustimmen, die für die Qualitäts-Gates benutzerdefinierter Funktions- und Benutzeroberflächentests verwendet werden. Darüber hinaus empfiehlt Adobe, [schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md) (Rapid Development Environments, RDE) in Ihre lokale Teststrategie zu integrieren, um AEM Cloud-Umgebungen möglichst genau widerzuspiegeln.

### Manuelle Tests

Das Qualitäts-Gate für manuelle Tests ist ein Platzhalter für Kunden, die manuelle Tests durchführen. Da AEM-Cloud-Pipelines manuelle Tests nicht unterstützen, ist eine Aufnahme in Ihre lokale Teststrategie erforderlich.

Für manuelle Tests kann die Integration in eine zusätzliche AEM Cloud Service-Entwicklungsumgebung nützlich sein.
