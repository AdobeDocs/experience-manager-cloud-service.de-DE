---
title: Bereitstellen Ihres Codes
description: Erfahren Sie, wie Sie Ihren Code mithilfe von Cloud Manager-Pipelines in AEM as a Cloud Service bereitstellen.
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 41%

---


# Code bereitstellen {#deploy-your-code}

Erfahren Sie, wie Sie Ihren Code mithilfe von Cloud Manager-Pipelines in AEM as a Cloud Service für die Produktion bereitstellen.

![Produktions-Pipeline-Diagramm](./assets/configure-pipeline/production-pipeline-diagram.png)

Die nahtlose Bereitstellung von Code in der Staging- und dann in der Produktion erfolgt über eine Produktions-Pipeline. Die Ausführung der Produktions-Pipeline gliedert sich in die beiden folgenden logischen Phasen:

1. **Implementierung in die Staging-Umgebung** - Der Code wird erstellt und in der Staging-Umgebung bereitgestellt, um automatisierte Funktionstests, UI-Tests, Erlebnisprüfungen und Benutzerakzeptanztests (UAT) durchzuführen.
1. **Implementierung in die Produktionsumgebung** - Sobald der Build auf der Bühne validiert und für die Promotion zur Produktion genehmigt wurde, wird dasselbe Build-Artefakt in der Produktionsumgebung bereitgestellt.

_Nur der Pipelinetyp „Full Stack code“ unterstützt das Codescannen, Funktionstests, Benutzeroberflächentests und Erlebnis-Audits._

## Bereitstellungsprozess {#deployment-process}

Alle Cloud-Dienste werden in einem fortlaufenden Prozess bereitgestellt, um zu gewährleisten, dass keine Ausfallzeiten entstehen. Weitere Informationen finden Sie unter [Funktionsweise von rollierenden Bereitstellungen](/help/implementing/deploying/overview.md#how-rolling-deployments-work).

>[!NOTE]
>
>Der Dispatcher-Cache wird bei jeder Bereitstellung gelöscht. Er wird anschließend &quot;aufgewärmt&quot;, bevor die neuen Veröffentlichungsknoten Traffic akzeptieren.

## Bereitstellen Ihres Codes mit Cloud Manager in AEM as a Cloud Service {#deploying-code-with-cloud-manager}

Sobald Sie [Ihre Produktions-Pipeline einschließlich Repository, Umgebung und Testumgebung konfiguriert](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) haben, können Sie Ihren Code bereitstellen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Klicken Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** auf das Programm, für das Sie Code bereitstellen möchten.

1. Klicken Sie auf der Seite **Überblick** im Bereich &quot;Aktionsaufruf&quot;auf **Bereitstellen**.

   ![Aktionsaufforderung](assets/deploy-code1.png)

1. Klicken Sie auf der Seite **Für Produktion bereitstellen** auf **Erstellen**.

   ![Pipeline-Ausführungsbildschirm](assets/deploy-code2.png)

Der Build-Prozess stellt Ihren Code in den folgenden drei geordneten Phasen bereit:

1. [Staging-Bereitstellungsphase](#stage-deployment)
1. [Staging-Testphase](#stage-testing)
1. [Produktionsbereitstellungsphase](#production-deployment)

>[!TIP]
>
>Sie können die Schritte verschiedener Bereitstellungsprozesse überprüfen, indem Sie die Protokolle lesen oder die Ergebnisse anhand der Testkriterien durchgehen.

### Staging-Bereitstellungsphase {#stage-deployment}

Die Phase der **Staging-Bereitstellung** umfasst die folgenden Schritte:

| Schritt zur Staging-Bereitstellung | Beschreibung |
| --- | --- |
| Validierung | Stellt sicher, dass die Pipeline für die Verwendung der derzeit verfügbaren Ressourcen konfiguriert ist. Beispielsweise wird getestet, ob die konfigurierte Verzweigung vorhanden ist und ob die Umgebungen verfügbar sind. |
| Test- und Unit-Tests | Führt einen containerisierten Build-Prozess aus.<br>Weitere Informationen zur Build-Umgebung finden Sie unter [Details zur Build-Umgebung](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md) . |
| Codescans | Wertet die Qualität Ihres Anwendungscodes aus.<br>Weitere Informationen zum Testprozess finden Sie unter [Tests der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md) . |
| Build-Images | Dieser Prozess konvertiert Inhalte und Dispatcher-Pakete aus dem Schritt &quot;Erstellen&quot;in Docker-Bilder. Es generiert außerdem Kubernetes-Konfigurationen basierend auf diesen Paketen. |
| Bereitstellung für Staging | Das Bild wird in der Staging-Umgebung bereitgestellt, um die [Staging-Testphase](#stage-testing) vorzubereiten. |

![Staging-Bereitstellung](assets/stage-deployment.png)

### Staging-Testphase {#stage-testing}

Die Phase des **Staging-Tests** umfasst die folgenden Schritte:

| Schritt zu Staging-Tests | Beschreibung |
| --- | --- |
| Funktionstests für das Produkt | Die Cloud Manager-Pipeline führt Tests aus, die für die Staging-Umgebung ausgeführt werden.<br>Siehe auch [Funktionstests für das Produkt](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing). |
| Benutzerdefinierte Funktionstests | Dieser Schritt in der Pipeline wird immer ausgeführt und kann nicht übersprungen werden. Wenn der Build keine Test-JAR erzeugt, wird der Test automatisch bestanden.<br>Siehe auch [Benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing). |
| Benutzerdefinierte Benutzeroberflächentests | Eine optionale Funktion, mit der automatisch für benutzerdefinierte Anwendungen erstellte UI-Tests ausgeführt werden.<br>UI-Tests sind Selenium-basiert und in einem Docker-Bild verpackt, um Flexibilität in Sprache und Frameworks zu bieten. Mit diesem Ansatz können Sie Java und Maven, Node und WebDriver.io oder ein beliebiges Selenium-basiertes Framework oder jede Selenium-Technologie verwenden.<br>Siehe auch [Benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing). |
| Experience Audit | Dieser Schritt in der Pipeline wird immer ausgeführt und kann nicht übersprungen werden. Während eine Produktions-Pipeline ausgeführt wird, wird nach benutzerdefinierten Funktionstests, die die Prüfungen ausführen, ein Schritt zur Erlebnisprüfung eingefügt.<ul><li>Die konfigurierten Seiten werden an den Service übermittelt und ausgewertet.</li><li>Die Ergebnisse sind informativer Natur und zeigen die Bewertungen sowie die Änderung zwischen den aktuellen und vorherigen Bewertungen.</li><li>Diese Erkenntnis ist wertvoll, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Bereitstellung eingeführt wird.</li></ul>Siehe [Verstehen der Ergebnisse von Erlebnisprüfungen](/help/implementing/cloud-manager/experience-audit-dashboard.md).</li></ul> |

![Staging-Tests](assets/stage-testing.png)

### Produktionsbereitstellungsphase {#production-deployment}

Der Bereitstellungsprozess für Produktions-Topologien unterscheidet sich geringfügig, um die Auswirkungen auf Besucher einer AEM Website zu minimieren.

Produktionsimplementierungen folgen im Allgemeinen den oben beschriebenen Schritten, aber auf rollierende Weise. Dazu gehören die folgenden Schritte:

1. AEM-Pakete werden für den Autor bereitgestellt
1. Trennen Sie `dispatcher1` vom Lastenausgleich.
1. Stellen Sie AEM Pakete in `publish1` bereit und das Dispatcher-Paket in `dispatcher1`, und leeren Sie den Dispatcher-Cache.
1. Setzen Sie `dispatcher1` zurück in den Lastenausgleich.
1. Wenn `dispatcher1` wieder in Betrieb ist, trennen Sie `dispatcher2` vom Lastenausgleich.
1. Stellen Sie AEM Pakete in `publish2` bereit und das Dispatcher-Paket in `dispatcher2`, und leeren Sie den Dispatcher-Cache.
1. Setzen Sie `dispatcher2` zurück in den Lastenausgleich.

Dieser Prozess wird fortgesetzt, bis die Bereitstellung alle Publisher und Dispatcher in der Topologie erreicht hat.

![Phase der Produktionsbereitstellung](assets/production-deployment.png)

## Zeitüberschreitungen während einer Bereitstellung {#timeouts}

Die folgenden Schritte zeigen ein Timeout, wenn sie während einer Bereitstellung auf Benutzerfeedback warten lassen:

| Schritt | Zeitüberschreitung |
|--- |--- |
| Testen der Code-Qualität | 14 Tage |
| Sicherheitstests | 14 Tage |
| Leistungstests | 14 Tage |
| Genehmigungsantrag | 14 Tage |
| Planen der Bereitstellung für die Produktion | 14 Tage |
| CSE-Unterstützung | 14 Tage |

## Produktions-Bereitstellung erneut ausführen {#reexecute-deployment}

In seltenen Fällen kann es vorkommen, dass Schritte der Produktionsbereitstellung aus vorübergehenden Gründen fehlschlagen. In solchen Fällen wird die erneute Ausführung des Produktionsbereitstellungsschritts unterstützt, solange der Produktionsbereitstellungsschritt abgeschlossen ist, unabhängig vom Fertigstellungstyp (z. B. abgebrochen oder nicht erfolgreich). Bei der erneuten Ausführung wird eine neue Ausführung mit derselben Pipeline erstellt, die aus den folgenden drei Schritten besteht:

1. **Validierung** - Die gleiche Validierung, die während einer normalen Pipeline-Ausführung erfolgt.
1. **Build** - Im Kontext einer erneuten Ausführung kopiert der Build-Schritt Artefakte und führt keinen neuen Build-Prozess aus.
1. **Produktionsbereitstellung** - Verwendet dieselbe Konfiguration und dieselben Optionen wie der Produktionsbereitstellungsschritt in einer normalen Pipeline-Ausführung.

In solchen Fällen, in denen eine erneute Ausführung möglich ist, bietet die Statusseite der Produktions-Pipeline neben der üblichen Option **Build-Protokoll herunterladen** auch die Option **Erneut ausführen**.

![Die Option „Erneut ausführen“ im Pipeline-Übersichtsfenster](assets/re-execute.png)

>[!NOTE]
>
>Bei einer erneuten Ausführung wird der Build-Schritt in der Benutzeroberfläche mit dem Hinweis versehen, dass er Artefakte kopiert und nicht neu erstellt.

### Einschränkungen {#limitations}

* Das erneute Ausführen des Produktionsbereitstellungsschritts ist nur für die letzte Ausführung verfügbar.
* Die Neuausführung ist nicht für Push-Update-Ausführungen verfügbar. Wenn die letzte Ausführung eine Push-Update-Ausführung war, ist eine erneute Ausführung nicht möglich.
* Wenn die letzte Ausführung vor dem Produktionsbereitstellungsschritt fehlschlug, ist eine erneute Ausführung nicht möglich.

### Erneutes Ausführen der API {#reexecute-API}

Zusätzlich zur Verfügbarkeit in der Benutzeroberfläche können Sie [die Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Pipeline-Execution) verwenden, um erneute Ausführungen auszulösen und Ausführungen zu identifizieren, die als erneute Ausführungen ausgelöst wurden.

#### Auslösen einer erneuten Ausführung {#reexecute-deployment-api}

Um eine erneute Ausführung auszulösen, muss eine PUT-Anfrage an den HAL-Link `https://ns.adobe.com/adobecloud/rel/pipeline/reExecute` im Status des Produktionsbereitstellungsschritts erfolgen.

* Wenn diese Verknüpfung vorhanden ist, kann die Ausführung von diesem Schritt aus neu gestartet werden.
* Wenn dies nicht der Fall ist, kann die Ausführung von diesem Schritt an nicht erneut gestartet werden.

Diese Verknüpfung ist immer nur für den Schritt der Produktionsbereitstellung verfügbar.

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

Die Übermittlung einer PUT-Anfrage an diesen Endpunkt führt bei Erfolg zu einer 201-Antwort und der Antworttext stellt die Darstellung der neuen Ausführung dar. Dieser Workflow ähnelt dem Starten einer regulären Ausführung über die API.

#### Ermitteln einer erneuten Ausführung {#identify-reexecution}

Das System erkennt Wiederausführungen, indem es das Feld `trigger` auf den Wert `RE_EXECUTE` setzt.
