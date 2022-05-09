---
title: Bereitstellen des Codes
description: Erfahren Sie, wie Sie Ihren Code mithilfe von Cloud Manager-Pipelines in AEM as a Cloud Service bereitstellen.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: c6e930f62cc5039e11f2067ea31882c72be18774
workflow-type: tm+mt
source-wordcount: '1199'
ht-degree: 16%

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

## Produktionsimplementierung erneut ausführen {#Reexecute-Deployment}

Die erneute Ausführung des Produktionsbereitstellungsschritts wird bei Ausführungen unterstützt, bei denen der Schritt zur Produktionsbereitstellung abgeschlossen ist. Die Art der Fertigstellung ist nicht wichtig - die Bereitstellung kann abgebrochen oder nicht erfolgreich sein. Der primäre Anwendungsfall ist jedoch Fälle, in denen der Produktionsbereitstellungsschritt aus Verlaufsgründen fehlgeschlagen ist. Bei der erneuten Ausführung wird eine neue Ausführung mit derselben Pipeline erstellt. Diese neue Ausführung besteht aus drei Schritten:

1. Der Validierungsschritt - dies ist im Wesentlichen dieselbe Validierung, die während einer normalen Pipeline-Ausführung erfolgt.
1. Der Build-Schritt - Im Kontext einer erneuten Ausführung kopiert der Build-Schritt Artefakte und führt keinen neuen Build-Prozess aus.
1. Der Schritt zur Produktionsbereitstellung - verwendet dieselbe Konfiguration und dieselben Optionen wie der Schritt zur Produktionsbereitstellung bei einer normalen Pipeline-Ausführung.

Der Build-Schritt ist in der Benutzeroberfläche möglicherweise etwas anders beschriftet, um zu erkennen, dass er Artefakte kopiert und nicht neu erstellt.

![Neu bereitstellen](assets/Re-deploy.png)

Beschränkungen:

* Die erneute Ausführung des Produktionsbereitstellungsschritts ist nur bei der letzten Ausführung verfügbar.
* Die Neuausführung ist nicht für Push-Update-Ausführungen verfügbar. Wenn es sich bei der letzten Ausführung um eine Push-Update-Ausführung handelt, ist eine erneute Ausführung nicht möglich.
* Wenn es sich bei der letzten Ausführung um eine Push-Update-Ausführung handelt, ist eine erneute Ausführung nicht möglich.
* Wenn die letzte Ausführung vor dem Produktionsbereitstellungsschritt fehlschlug, ist eine erneute Ausführung nicht möglich.

### API erneut ausführen {#Reexecute-API}

### Ermitteln einer erneuten Ausführung

Um festzustellen, ob es sich bei einer Ausführung um eine erneute Ausführung handelt, kann das Feld Trigger geprüft werden. Ihr Wert lautet *RE_EXECUTE*.

### Auslösen einer neuen Ausführung

Um eine erneute Ausführung Trigger, muss eine PUT-Anfrage an den HAL Link &lt;(<http://ns.adobe.com/adobecloud/rel/pipeline/reExecute>)> im Status der Produktionsbereitstellungs-Schritte. Wenn dieser Link vorhanden ist, kann die Ausführung von diesem Schritt an neu gestartet werden. Wenn dies nicht der Fall ist, kann die Ausführung von diesem Schritt an nicht erneut gestartet werden. In der ersten Version ist dieser Link nur im Schritt zur Produktionsbereitstellung vorhanden, aber zukünftige Versionen unterstützen möglicherweise das Starten der Pipeline von anderen Schritten aus. Beispiel:

```Javascript
 {
  "_links": {
    "http://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "http://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/metrics",
      "templated": false
    },
    "self": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530",
      "templated": false
    }
  },
  "id": "6187842",
  "stepId": "2983530",
  "phaseId": "1575676",
  "action": "deploy",
  "environment": "weretail-global-b75-prod",
  "environmentType": "prod",
  "environmentId": "59254",
  "startedAt": "2022-01-20T14:47:41.247+0000",
  "finishedAt": "2022-01-20T15:06:19.885+0000",
  "updatedAt": "2022-01-20T15:06:20.803+0000",
  "details": {
  },
  "status": "FINISHED"
```


Die Syntax des HAL-Links _href_  Der obige Wert ist nicht zur Verwendung als Bezugspunkt vorgesehen. Der tatsächliche Wert sollte immer aus dem HAL-Link gelesen und nicht generiert werden.

Senden einer *PUT* -Anfrage an diesen Endpunkt führt zu einer *201* Antwort bei Erfolg und der Antworttext ist die Darstellung der neuen Ausführung. Dies ähnelt dem Starten einer regulären Ausführung über die API.
