---
title: Bereitstellen des Codes
description: Erfahren Sie, wie Sie Ihren Code mithilfe von Cloud Manager-Pipelines in AEM as a Cloud Service bereitstellen.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '1192'
ht-degree: 91%

---


# Bereitstellen des Codes {#deploy-your-code}

Erfahren Sie, wie Sie Ihren Code mithilfe von Cloud Manager-Pipelines in AEM as a Cloud Service für die Produktion bereitstellen.

![Produktions-Pipeline-Diagramm](./assets/configure-pipeline/production-pipeline-diagram.png)

Die nahtlose Bereitstellung von Code zum Staging und dann bis zur Produktion erfolgt über eine Produktions-Pipeline. Die Ausführung der Produktions-Pipeline ist in zwei logische Phasen unterteilt.

1. Bereitstellung in der Staging-Umgebung
   * Der Code wird erstellt und in der Staging-Umgebung für automatisierte Funktionstests, Benutzeroberflächentests, Erlebnis-Audits und Benutzerakzeptanztests (UAT) bereitgestellt.
1. Bereitstellung in der Produktionsumgebung
   * Sobald der Build im Staging überprüft und für die Produktion freigegeben ist, wird das gleiche Build-Artefakt in der Produktionsumgebung bereitgestellt.

_Nur der Pipelinetyp „Full Stack code“ unterstützt das Codescannen, Funktionstests, Benutzeroberflächentests und Erlebnis-Audits._

## Bereitstellen des Codes mit Cloud Manager in AEM as a Cloud Service {#deploying-code-with-cloud-manager}

Sobald Sie [Ihre Produktions-Pipeline einschließlich Repository, Umgebung und Testumgebung konfiguriert](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) haben, können Sie Ihren Code bereitstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie auf das Programm, für das Sie Code bereitstellen möchten.

1. Klicken Sie auf **Bereitstellen** aus der Aktionsaufforderung auf dem Bildschirm **Übersicht**, um den Implementierungsprozess zu starten.

   ![Aktionsaufforderung](assets/deploy-code1.png)

1. Der Bildschirm **Pipeline-Ausführung** wird angezeigt. Klicken Sie auf **Build**, um den Prozess zu starten.

   ![Pipeline-Ausführungsbildschirm](assets/deploy-code2.png)

Der Build-Prozess stellt Ihren Code in drei Phasen bereit.

1. [Staging-Bereitstellung](#stage-deployment)
1. [Staging-Tests](#stage-testing)
1. [Produktionsbereitstellung](#production-deployment)

>[!TIP]
>
>Außerdem können Sie die Schritte der verschiedenen Bereitstellungsprozesse überprüfen, indem Sie die Protokolle anzeigen oder die Ergebnisse anhand der Testkriterien überprüfen.

## Phase der Staging-Bereitstellung {#stage-deployment}

Die Phase der **Staging-Bereitstellung** umfasst diese Schritte.

* **Validierung**: Dieser Schritt stellt sicher, dass die Pipeline für die Verwendung der derzeit verfügbaren Ressourcen konfiguriert ist. Beispielsweise wird getestet, ob die konfigurierte Verzweigung vorhanden ist und ob die Umgebungen verfügbar sind.
* **Build- und Komponententests**: Dieser Schritt führt einen containerisierten Build-Prozess aus.
   * Siehe [Details zur Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md), um weitere Informationen zur Build-Umgebung zu erhalten.
* **Codescan**: Dieser Schritt bewertet die Qualität Ihres Programm-Codes.
   * Weitere Informationen zum Testprozess finden Sie unter [Tests der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md).
* **Build-Images**: Dieser Prozess ist für die Umwandlung der vom Build-Schritt erstellten Inhalts- und Dispatcher-Pakete in Docker-Images und die Kubernetes-Konfiguration verantwortlich.
* **In der Staging-Umgebung bereitstellen**: Das Image wird in der Staging-Umgebung bereitgestellt, um die [Staging-Testphase](#stage-testing) vorzubereiten.

![Staging-Bereitstellung](assets/stage-deployment.png)

## Staging-Testphase {#stage-testing}

Die **Staging-Test**-Phase umfasst diese Schritte.

* **Produktfunktionstests**: Die Cloud Manager-Pipeline führt Tests aus, die für die Staging-Umgebung ausgeführt werden.
   * Weitere Informationen finden Sie unter [Produktfunktionstests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing).

* **Benutzerdefinierte Funktionstests**: Dieser Schritt in der Pipeline ist immer vorhanden und kann nicht übersprungen werden. Wenn jedoch keine Test-JAR vom Build erzeugt wird, wird der Test standardmäßig erfolgreich durchgeführt.
   * Weitere Informationen finden Sie unter [Benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing).

* **Testen von benutzerdefinierten Benutzeroberflächen**: Dieser Schritt ist eine optionale Funktion, mit der automatisch für benutzerdefinierte Programme erstellte Benutzeroberflächentests ausgeführt werden.
   * Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen).
   * Weitere Informationen finden Sie unter [Benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing).

* **Erlebnis-Audit**: Dieser Schritt in der Pipeline ist immer vorhanden und kann nicht übersprungen werden. Bei Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests, die die Prüfungen ausführen, ein Schritt zur Erlebnisprüfung eingefügt.
   * Die konfigurierten Seiten werden an den Service übermittelt und ausgewertet.
   * Die Ergebnisse sind informativer Natur und zeigen die Bewertungen sowie die Änderung zwischen den aktuellen und vorherigen Bewertungen.
   * Diese Erkenntnis ist wertvoll, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Bereitstellung eingeführt wird.
   * Weitere Einzelheiten finden Sie unter [Grundlegendes zu den Ergebnissen von Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md).

![Staging-Tests](assets/stage-testing.png)

## Phase der Produktionsbereitstellung {#deployment-production}

Der Prozess für die Bereitstellung in Produktionstopologien unterscheidet sich geringfügig, um die Auswirkungen auf die Besuchenden einer AEM-Site zu minimieren.

Produktionsbereitstellungen nutzen im Allgemeinen die oben beschriebenen Schritte, aber auf rollierende Weise.

1. AEM-Pakete werden für den Autor bereitgestellt
1. dispatcher1 wird aus dem Lastenausgleich gelöst
1. AEM-Pakete werden in publish1 und das Dispatcher-Paket in dispatcher1 bereitgestellt und der Dispatcher-Cache geleert
1. dispatcher1 wird in den Lastenausgleich zurückgesetzt
1. Sobald dispatcher1 wieder aktiv ist, wird dispatcher2 aus dem Lastenausgleich entfernt
1. AEM-Pakete werden in publish2 und das Dispatcher-Paket in dispatcher2 bereitgestellt und der Dispatcher-Cache geleert
1. dispatcher2 wird in den Lastenausgleich zurückgesetzt


Dieser Vorgang wird fortgesetzt, bis die Bereitstellung alle Publisher und Dispatcher in der Topologie erreicht hat.

![Phase der Produktionsbereitstellung](assets/production-deployment.png)

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

## Bereitstellungsprozess {#deployment-process}

Alle Cloud-Dienste werden in einem fortlaufenden Prozess bereitgestellt, um zu gewährleisten, dass keine Ausfallzeiten entstehen. Weitere Informationen finden Sie unter [Funktionsweise von rollierenden Bereitstellungen](/help/implementing/deploying/overview.md#how-rolling-deployments-work).

>[!NOTE]
>
>Der Dispatcher-Cache wird bei jeder Bereitstellung gelöscht. Er wird anschließend aufgewärmt, damit die neuen Veröffentlichungsknoten Traffic akzeptieren.

## Erneutes Ausführen einer Produktionsbereitstellung {#reexecute-deployment}

In seltenen Fällen kann es vorkommen, dass Schritte der Produktionsbereitstellung aus vorübergehenden Gründen fehlschlagen. In solchen Fällen wird die Neuausführung des Produktionsbereitstellungsschritts unterstützt, solange der Produktionsbereitstellungsschritt abgeschlossen ist, unabhängig vom Fertigstellungstyp (z. B. abgebrochen oder nicht erfolgreich). Bei der erneuten Ausführung wird eine neue Ausführung mit derselben Pipeline erstellt, die aus drei Schritten besteht.

1. Der Validierungsschritt – Dies ist im Wesentlichen dieselbe Validierung wie bei einer normalen Pipeline-Ausführung.
1. Der Build-Schritt – Im Rahmen einer erneuten Ausführung kopiert der Build-Schritt Artefakte und führt keinen wirklich neuen Build-Prozess aus.
1. Der Produktionsbereitstellungsschritt – Dieser Schritt verwendet dieselbe Konfiguration und dieselben Optionen wie der Produktionsbereitstellungsschritt bei einer normalen Pipeline-Ausführung.

In solchen Fällen, in denen eine erneute Ausführung möglich ist, bietet die Statusseite der Produktions-Pipeline neben der üblichen Option **Build-Protokoll herunterladen** auch die Option **Erneut ausführen**.

![Die Option „Erneut ausführen“ im Pipeline-Übersichtsfenster](assets/re-execute.png)

>[!NOTE]
>
>Bei einer erneuten Ausführung wird der Build-Schritt in der Benutzeroberfläche mit dem Hinweis versehen, dass er Artefakte kopiert und nicht neu erstellt.

### Einschränkungen {#limitations}

* Die erneute Ausführung des Produktionsbereitstellungsschritts ist nur für die letzte Ausführung verfügbar.
* Eine erneute Ausführung ist für Push-Update-Ausführungen nicht verfügbar.
   * Wenn die letzte Ausführung eine Push-Update-Ausführung war, ist eine erneute Ausführung nicht möglich.
* Wenn die letzte Ausführung zu irgendeinem Zeitpunkt vor dem Schritt der Produktionsbereitstellung fehlgeschlagen ist, ist eine erneute Ausführung nicht möglich.

### Erneutes Ausführen der API {#reexecute-API}

Zusätzlich zur Verfügbarkeit in der Benutzeroberfläche können Sie [die Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) verwenden, um erneute Ausführungen auszulösen und Ausführungen zu identifizieren, die als erneute Ausführungen ausgelöst wurden.

#### Auslösen einer erneuten Ausführung {#reexecute-deployment-api}

Um eine Neuausführung Trigger, stellen Sie eine PUT-Anfrage an den HAL-Link `https://ns.adobe.com/adobecloud/rel/pipeline/reExecute` im Status der Produktionsbereitstellungs-Schritte.

* Wenn diese Verknüpfung vorhanden ist, kann die Ausführung von diesem Schritt aus neu gestartet werden.
* Wenn dies nicht der Fall ist, kann die Ausführung von diesem Schritt an nicht erneut gestartet werden.

Dieser Link ist nur für den Schritt zur Produktionsbereitstellung verfügbar.

```JavaScript
 {
  "_links": {
    "https://ns.adobe.com/adobecloud/rel/pipeline/logs": {
      "href": "/api/program/4/pipeline/1/execution/953671/phase/1575676/step/2983530/logs",
      "templated": false
    },
    "https://ns.adobe.com/adobecloud/rel/pipeline/reExecute": {
      "href": "/api/program/4/pipeline/1/execution?stepId=2983530",
      "templated": false
    },
    "https://ns.adobe.com/adobecloud/rel/pipeline/metrics": {
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

Die Syntax des href-Werts des HAL-Links ist nur ein Beispiel. Der tatsächliche Wert sollte immer aus dem HAL-Link gelesen und nicht generiert werden.

Das Senden einer PUT-Anfrage an diesen Endpunkt führt zu einer 201-Antwort bei Erfolg, wobei der Antworttext die Darstellung der neuen Ausführung ist. Dies ähnelt dem Starten einer regulären Ausführung über die API.

#### Identifizieren einer erneut ausgeführten Ausführung {#identify-reexecution}

Erneute Ausführungen können durch den Wert `RE_EXECUTE` im Feld `trigger` identifiziert werden.
