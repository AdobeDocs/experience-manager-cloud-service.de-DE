---
title: Funktionstests
description: Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den Bereitstellungsprozess von AEM as a Cloud Service integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 181a0fd3097e1af2c432afbd8d2a170d792918be
workflow-type: tm+mt
source-wordcount: '1416'
ht-degree: 10%

---


# Einführung {#functional-testing-introduction}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Funktionstests"
>abstract="Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den Bereitstellungsprozess von AEM as a Cloud Service integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen."

Erfahren Sie mehr über die in der [AEM as a Cloud Service Bereitstellungsprozess](/help/implementing/cloud-manager/deploy-code.md), die verschiedenen Arten von Funktionstests, die integriert sind, wie Sie einen Beitrag leisten können und wie Sie diese im Rahmen einer umfassenden Teststrategie optimal nutzen können.

## Übersicht

Das folgende Diagramm bietet einen allgemeinen Überblick über die verfügbaren Pipelines im Kontext einer Gesamtteststrategie und der [AEM as a Cloud Service Bereitstellungsprozess](/help/implementing/cloud-manager/deploy-code.md).

![Qualitätstests für die AEM Cloud Service-Bereitstellung](assets/functional-testing/quality-gates-compact.svg)

## Zweck

Die AEM Cloud Service-Implementierungs-Pipelines sollen eine robuste und sichere Bereitstellung in verschiedenen Phasen des Entwicklungs- und AEM Produktveröffentlichungslebenszyklus ermöglichen. Diese Pipelines enthalten mehrere Quality Gates auf unterschiedlichen Ebenen, um die Integrität und Sicherheit von Bereitstellungen sowohl für Ihre AEM Anwendungsänderungen als auch für AEM Produktaktualisierungen zu gewährleisten.

Adobe bietet mehrere integrierte Quality Gates, während andere Ihre Eingriffe für die Implementierung und Konfiguration erfordern. Diese Qualitätstests sind vielseitig, wobei einige in verschiedenen Phasen des Lebenszyklus anwendbar sind und sogar in Ihre eigenen Entwicklungs-Setup und CI/CD-Prozesse integriert werden können.

Die integrierten Quality Gates validieren in erster Linie die Funktionalität des AEM Produkts im Kontext Ihrer AEM. Die von Ihnen eingerichteten benutzerdefinierten Quality Gates hingegen dienen dazu, zu überprüfen, ob die kritischen Funktionen und Benutzerinteraktionen Ihrer Anwendung wie gewünscht funktionieren. Gemeinsam arbeiten diese beiden Sets von Quality Gates zusammen, um eine robuste und sichere automatisierte Bereitstellung sowohl für Ihre Codeänderungen als auch für AEM Produktaktualisierungen sicherzustellen.

Es ist wichtig zu beachten, dass diese Qualitätstests kein umfassendes Testframework für Ihre gesamte Teststrategie sein sollen. Das AEM Produkt wird umfassend getestet, bevor es in den AEM Cloud Service-Bereitstellungsprozess eintritt. Ebenso sollte Ihre Anwendung bereits von hoher Qualität sein, bevor sie die Bereitstellungsphase erreicht. Dieser Ansatz stellt sicher, dass sich die Qualitätstests auf ihr vorrangiges Ziel konzentrieren, den Implementierungsprozess zu gewährleisten, anstatt ein vollständiges Testschema zu ersetzen.

## Quality Gates

Das folgende Diagramm bietet einen detaillierten Überblick über die verfügbaren Quality Gates und deren Verwendung in der Gesamtteststrategie sowie die [AEM as a Cloud Service Bereitstellungsprozess](/help/implementing/cloud-manager/deploy-code.md).

![Qualitätstests für die AEM Cloud Service-Bereitstellung](assets/functional-testing/quality-gates-overview.svg)

### Zusammenfassende vom Kunden bereitgestellte Quality Gates

|                               | Komponententests | Benutzerdefiniert<br/> Funktionstests | Benutzerdefiniert<br/> UI-Tests | Kunde<br/> Überprüfungen | Manuell<br/> Test |
|:------------------------------|:---------------------:|:-----------------------------------:|:-----------------------------------:|:-------------------------:|:-------------------:|
| **Produktions-Pipeline** | Ja<br/>Blockieren<br/> | Ja<br/>Blockieren<br/>60 m Zeitüberschreitung | Ja<br/>Blockieren<br/>60 m Zeitüberschreitung | Nein | Nein |
| **Produktionsfremde Pipeline** | Ja<br/>Blockieren<br/> | Opt-in<br/>Blockieren<br/>60 m Zeitüberschreitung | Opt-in<br/>Blockieren<br/>60 m Zeitüberschreitung | Nein | Nein |
| **Adobe Interne Validierung** | Ja<br/>Blockieren<br/> | Ja<br/>Blockieren<br/>60 m Zeitüberschreitung | Ja<br/>Blockieren<br/>60 m Zeitüberschreitung | Nein | Nein |
| **Kunden-CI/CD** | Ja | Ja | Ja | Ja | Ja |
| **Lokaler Entwickler für Kunden** | Ja | Ja | Ja | Ja | Ja |

### Unit-Test

Es wird empfohlen, die Komponententests für Ihre AEM-Anwendung bereitzustellen, die die Grundlage jeder Teststrategie bilden. Sie sollen schnell und oft laufen und frühzeitig und schnell Feedback geben. Sie sind eng in die Entwickler-Workflows, Ihre eigene CI/CD und die AEM Cloud Service-Bereitstellungs-Pipelines integriert.

Sie werden mit JUnit implementiert und mit Maven ausgeführt. Weitere Informationen finden Sie unter
[Kernmodul des AEM Projektarchetyps](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/core.html#unit-tests)
für einen Beispiel-Komponententest für AEM und Erste Schritte.

### Code-Qualität

Dieses Qualitäts-Gate ist standardmäßig konfiguriert und führt eine statische Codeanalyse für Ihren AEM-Anwendungscode durch.

Siehe [Tests der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md) und
[Benutzerspezifische Code-Qualitätsregeln](/help/implementing/cloud-manager/custom-code-quality-rules.md) für weitere Informationen.

### Produkttests

Produktfunktionstests sind eine Reihe stabiler HTTP-Integrationstests (ITs) mit Kernfunktionen in AEM wie Authoring- und Replikationsaufgaben. Adobe stellt sie bereit und verwaltet sie standardmäßig. Sie sollen verhindern, dass Änderungen an benutzerdefiniertem Anwendungscode bereitgestellt werden, wenn dies die Kernfunktionalität im AEM beeinträchtigt.

Sie werden mithilfe von Junit implementiert, mithilfe von Maven ausgeführt und nutzen den offiziellen [AEM Testclients](https://github.com/adobe/aem-testing-clients).
Die Produkttestsuite wird als [Open-Source-Projekt](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke)folgt Best Practices und kann als guter Ausgangspunkt für die Implementierung Ihrer Tests betrachtet werden.

### Benutzerdefinierte Funktionstests

Wie die Produkttests sind Kundenfunktionstests HTTP-Integrationstests (ITs) und werden auch mit Junit implementiert, mit Maven ausgeführt und auf der offiziellen [AEM Testclients](https://github.com/adobe/aem-testing-clients).

>[!NOTE]
>
>Benutzerdefinierte Funktionstests werden in den Produktions- und Nicht-Produktions-Pipelines ausgeführt, die von den Implementierungen Ihrer AEM App-Änderungen und AEM Produkt-Push-Updates verwendet werden. Dies ist daher ein wichtiger Beitrag zur Gewährleistung eines ordnungsgemäßen Funktionierens Ihrer Anwendung und zur Erhöhung der Versionssicherheit.
>Die Kundenfunktionstests werden auch in internen Validierungs-Pipelines vor der Veröffentlichung für jeden Kunden ausgeführt, was zu frühzeitigem Feedback beiträgt.

Um Pipeline-Ausführungen effizient zu gestalten, empfehlen wir, sich auf wichtige Funktionen und die wichtigsten Benutzerinteraktionsflüsse zu konzentrieren.
Es wird empfohlen, für Funktionstests eine Ausführungszeit von höchstens 15 Minuten festzulegen. Es wird empfohlen, vollständige funktionale Test-Suites, die nicht in dieses Qualitätstest-Gate passen, im Rahmen der allgemeinen Kunden-Validierungs-Pipelines während des Entwicklungsablaufs des Kunden auszuführen.

Weitere Informationen finden Sie unter [Open-Source-Produkttests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) oder
[it.tests-Modul des AEM Projektarchetyps](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/ittests.html)
für Beispiele.

Weitere Informationen finden Sie unter [Java-Funktionstests](/help/implementing/cloud-manager/java-functional-testing.md).

### Benutzerdefinierte UI-Tests

Um die Risikokontrolle für Ihre kundenspezifische Entwicklung zu maximieren, empfiehlt Ihnen Adobe dringend, kritische UI-Tests in AEMCS zu erfassen. Sie sollen relativ begrenzt bleiben, jedoch mit den größten Auswirkungen auf Ihr Kundenerlebnis.

Die Tests sind in einem Docker-Image verpackt, das so flüchtig wie möglich ist (mit Unterstützung für Cypress, Selenium, Java, JavaScript usw.). Sie folgen denselben Merkmalen und Zwecken wie die benutzerdefinierten Funktionstests.

>[!NOTE]
>
>Benutzerdefinierte UI-Tests werden in den Produktions- und Nicht-Produktions-Pipelines ausgeführt, die von den Implementierungen Ihrer AEM App-Änderungen und AEM Produkt-Push-Aktualisierungen verwendet werden. Dies ist daher ein wichtiger Beitrag zur Gewährleistung eines ordnungsgemäßen Funktionierens Ihrer Anwendung und zur Erhöhung der Versionssicherheit.
>Die Tests der Kundenbenutzeroberfläche werden auch in internen Validierungs-Pipelines vor der Veröffentlichung für jeden Kunden ausgeführt, was zu frühzeitigem Feedback beiträgt.

Um Pipeline-Ausführungen effizient zu gestalten, empfehlen wir, sich auf wichtige Funktionen und die wichtigsten Benutzerinteraktionsflüsse zu konzentrieren.
Es wird empfohlen, vollständige UI-Test-Suites, die nicht in dieses Qualitäts-Gate passen, während des Entwicklungsablaufs des Kunden als Teil der allgemeinen Kunden-Validierungs-Pipelines auszuführen.

Weitere Informationen finden Sie unter [Open-Source-Beispieltests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/) oder
[ui.tests-Modul des AEM Projektarchetyps](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/uitests.html)
für Beispiele.

Weitere Informationen finden Sie unter [Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

### Erlebnisprüfung

Das Qualitäts-Gate der Erlebnisprüfung funktioniert [Google Lighthouse](https://developer.chrome.com/docs/lighthouse/overview/)
Audits auf der Webseite des Kunden.

Dieses Qualitäts-Gate wird von AEM vordefinierten bereitgestellt, blockiert jedoch nicht die Implementierungs-Pipelines. Standardmäßig wird eine Prüfung für die Stammseite (`/`) der Veröffentlichungsinstanz ausgeführt wird. Sie können einen Beitrag leisten, indem Sie bis zu 25 benutzerdefinierte Pfade konfigurieren, die für Prüfungen berücksichtigt werden.

Siehe [Testen mit Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md)
für weitere Informationen.

### Kundenvalidierungen

Das Qualitäts-Gate für Kundenvalidierungen ist ein Platzhalter für die eigene Teststrategie und den eigenen Aufwand des Kunden, der ausgeführt wird, bevor die Anwendungsänderungen des Kunden die AEM Cloud-Implementierungs-Pipelines erreichen.

Hier können Sie natürlich die Werkzeuge und Frameworks auswählen, die Sie bevorzugen. Im Gegensatz zu Kundenfunktionstests und benutzerspezifischen UI-Tests gibt es keine AEM as a Cloud Service damit zusammenhängenden Beschränkungen. Daher empfehlen wir, hier langwierige Funktions- und UI-Tests durchzuführen.

Es steht Ihnen zwar frei, ein beliebiges Tool und Framework auszuwählen, wir empfehlen jedoch, HTTP-basierte Integrationstests und UI-Tests mit den Tools und Frameworks abzustimmen, die in den benutzerdefinierten Funktionstests und den benutzerdefinierten Test-Qualitätstests für die Benutzeroberfläche verfügbar sind.
Wir empfehlen die Integration von
[Rapid Development Environments (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)
in Ihrer lokalen Teststrategie verwenden, um so nahe wie möglich an AEM Cloud-Umgebungen zu testen.

### Manuelle Prüfung

Das manuelle Test-Qualitäts-Gate ist ein Platzhalter für Kunden, die manuelle Tests durchführen. AEM Cloud-Pipelines unterstützen keine manuellen Tests. Daher muss dies im Rahmen Ihrer eigenen lokalen Teststrategie erfolgen.

Für manuelle Tests kann die Integration in eine zusätzliche AEM Cloud Service-Entwicklungsumgebung nützlich sein.
