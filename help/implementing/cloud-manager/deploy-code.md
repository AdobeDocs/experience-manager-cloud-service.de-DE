---
title: Bereitstellen des Codes
description: Erfahren Sie, wie Sie Ihren Code mithilfe von Cloud Manager-Pipelines in AEM as a Cloud Service bereitstellen.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: af1e682505d68a65a5e2b500d42f01f030e36ac1
workflow-type: tm+mt
source-wordcount: '806'
ht-degree: 23%

---


# Bereitstellen des Codes {#deploy-your-code}

Erfahren Sie, wie Sie Ihren Code mithilfe von Cloud Manager-Pipelines in AEM as a Cloud Service für die Produktion bereitstellen.

![Produktions-Pipeline-Diagramm](./assets/configure-pipeline/production-pipeline-diagram.png)

Die nahtlose Bereitstellung von Code in der Staging- und dann bis zur Produktion erfolgt über eine Produktions-Pipeline. Die Ausführung der Produktions-Pipeline ist in zwei logische Phasen unterteilt.

1. Bereitstellung in der Staging-Umgebung
   * Der Code wird erstellt und in der Staging-Umgebung bereitgestellt, um automatisierte Funktionstests, Benutzeroberflächen-Tests, Erlebnisprüfungen und Benutzerakzeptanztests (UAT) durchzuführen.
1. Bereitstellung in der Produktionsumgebung
   * Sobald der Build auf der Staging-Umgebung validiert und für die Promotion zur Produktion genehmigt wurde, wird dasselbe Build-Artefakt in der Produktionsumgebung bereitgestellt.

_Nur der Pipelinetyp &quot;Vollständiger Stack-Code&quot;unterstützt das Codescannen, Funktionstests, UI-Tests und Erlebnisprüfungen._

## Bereitstellen Ihres Codes mit Cloud Manager in AEM as a Cloud Service {#deploying-code-with-cloud-manager}

Einmal [die Produktions-Pipeline konfiguriert haben](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) einschließlich Repository, Umgebung und Testumgebung, können Sie Ihren Code bereitstellen.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie Code bereitstellen möchten.

1. Klicken **Bereitstellen** aus dem Aktionsaufruf auf der **Übersicht** -Bildschirm, um den Implementierungsprozess zu starten.

   ![CTA](assets/deploy-code1.png)

1. Der Bildschirm **Pipeline-Ausführung** wird angezeigt. Klicken Sie auf **Build**, um den Prozess zu starten.

   ![Pipeline-Ausführungsbildschirm](assets/deploy-code2.png)

Der Build-Prozess stellt Ihren Code in drei Phasen bereit.

1. [Staging-Bereitstellung](#stage-deployment)
1. [Staging-Tests](#stage-testing)
1. [Produktionsimplementierung](#production-deployment)

>[!TIP]
>
>Sie können die Schritte aus verschiedenen Bereitstellungsprozessen überprüfen, indem Sie Protokolle anzeigen oder die Ergebnisse auf die Testkriterien überprüfen.

## Phase der Staging-Bereitstellung {#stage-deployment}

Die **Staging-Bereitstellung** Phase. umfasst diese Schritte.

* **Validierung**  - Dieser Schritt stellt sicher, dass die Pipeline für die Verwendung der derzeit verfügbaren Ressourcen konfiguriert ist. Beispielsweise wird getestet, ob die konfigurierte Verzweigung vorhanden ist und ob die Umgebungen verfügbar sind.
* **Build- und Unit-Tests** - Dieser Schritt führt einen containerisierten Build-Prozess aus.
   * Lesen Sie das Dokument [Details der Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) für Details zur Build-Umgebung.
* **Codescans** - Dieser Schritt bewertet die Qualität Ihres Anwendungs-Codes.
   * Lesen Sie das Dokument [Tests der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md) für Details zum Testprozess.
* **Bilder erstellen** - Dieser Prozess ist für die Umwandlung der vom Build-Schritt erstellten Inhalts- und Dispatcher-Pakete in Docker-Bilder und Kubernetes-Konfigurationen verantwortlich.
* **In der Staging-Umgebung bereitstellen** - Das Bild wird in der Staging-Umgebung bereitgestellt, um die [Staging-Testphase.](#stage-testing)

![Staging-Bereitstellung](assets/stage-deployment.png)

## Staging-Testphase {#stage-testing}

Die **Staging-Tests** Diese Phase umfasst diese Schritte.

* **Funktionstests für das Produkt** - Die Cloud Manager-Pipeline führt Tests aus, die für die Staging-Umgebung ausgeführt werden.
   * Weitere Informationen finden Sie im Dokument . [Funktionstests für das Produkt](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) für weitere Details.

* **Benutzerdefinierte Funktionstests** - Dieser Schritt in der Pipeline wird immer ausgeführt und kann nicht übersprungen werden. Wenn vom Build keine Test-JAR erstellt wird, wird der Test standardmäßig erfolgreich durchgeführt.
   * Weitere Informationen finden Sie im Dokument . [Benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) für weitere Details.

* **Testen der benutzerdefinierten Benutzeroberfläche** - Dieser Schritt ist eine optionale Funktion, mit der automatisch für benutzerdefinierte Anwendungen erstellte UI-Tests ausgeführt werden.
   * UI-Tests sind Selenium-basierte Tests, die in einem Docker-Bild verpackt sind, um eine breite Auswahl in Sprache und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder ein anderes auf Selenium aufbauendes Framework und Technologie).
   * Weitere Informationen finden Sie im Dokument . [Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) für weitere Details.

* **Erlebnisprüfung** - Dieser Schritt in der Pipeline wird immer ausgeführt und kann nicht übersprungen werden. Bei Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests, die die Prüfungen ausführen, ein Schritt zur Erlebnisprüfung eingefügt.
   * Die konfigurierten Seiten werden an den Dienst gesendet und ausgewertet.
   * Die Ergebnisse sind informativ und zeigen die Bewertungen und die Änderung zwischen den aktuellen und vorherigen Bewertungen an.
   * Diese Erkenntnis ist nützlich, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Implementierung eingeführt wird.
   * Weitere Informationen finden Sie im Dokument . [Verstehen der Ergebnisse von Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md) für weitere Details.

![Staging-Tests](assets/stage-testing.png)

## Phase der Produktionsbereitstellung {#deployment-production}

Der Bereitstellungsprozess für Produktions-Topologien unterscheidet sich geringfügig, um die Auswirkungen auf Besucher einer AEM Website zu minimieren.

Produktionsimplementierungen folgen im Allgemeinen den oben beschriebenen Schritten, jedoch rollierend.

1. AEM-Pakete werden für den Autor bereitgestellt
1. dispatcher1 wird aus dem Lastenausgleich gelöst
1. AEM-Pakete werden in publish1 und das Dispatcher-Paket in dispatcher1 bereitgestellt und der Dispatcher-Cache geleert
1. dispatcher1 wird in den Lastenausgleich zurückgesetzt
1. Sobald dispatcher1 wieder aktiv ist, wird dispatcher2 aus dem Lastenausgleich entfernt
1. AEM-Pakete werden in publish2 und das Dispatcher-Paket in dispatcher2 bereitgestellt und der Dispatcher-Cache geleert
1. dispatcher2 wird in den Lastenausgleich zurückgesetzt


Dieser Vorgang wird fortgesetzt, bis die Implementierung alle Publisher und Dispatcher in der Topologie erreicht hat.

![Produktionsbereitstellungsphase](assets/production-deployment.png)

## Zeitüberschreitungen {#timeouts}

Die folgenden Schritte führen zu einer Zeitüberschreitung, wenn auf Benutzer-Feedback gewartet wird:

| Schritt | Zeitüberschreitung |
|--- |--- |
| Testen der Code-Qualität | 14 Tage |
| Sicherheitstests | 14 Tage |
| Leistungstests | 14 Tage |
| Genehmigungsantrag | 14 Tage |
| Planen der Bereitstellung für die Produktion | 14 Tage |
| CSE-Unterstützung | 14 Tage |

## Implementierungsprozess {#deployment-process}

Alle Cloud-Dienste werden in einem fortlaufenden Prozess bereitgestellt, um zu gewährleisten, dass keine Ausfallzeiten entstehen. Weitere Informationen finden Sie im Dokument . [Funktionsweise von rollierenden Implementierungen](/help/implementing/deploying/overview.md#how-rolling-deployments-work) , um mehr zu erfahren.