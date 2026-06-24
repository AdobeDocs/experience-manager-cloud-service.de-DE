---
title: Aufspalten in reine Staging- und reine Produktions-Pipelines
description: Erfahren Sie, wie Sie mithilfe von dedizierten Pipelines in Staging- und Produktionsbereitstellungen aufteilen können.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
hidefromtoc: false
index: true
exl-id: 7d76a87c-122c-4c4d-8071-957bef4c9cf1
source-git-commit: 1eb2a3fede53e01f07f511ae24de5ac1f11b8821
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 60%

---

# Aufspalten in reine Staging- und reine Produktions-Pipelines {#stage-prod-only}

<!--
 REMOVED AS PER CQDOC-23086 ON OCTOBER 3, 2025:
badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#staging-production-only-pipelines"
-->

Sie können Staging- und Produktionsbereitstellungen mithilfe von dedizierten Pipelines aufspalten.

## Überblick {#overview}

Staging- und Produktionsumgebungen sind eng miteinander verbunden. Standardmäßig sind die damit verknüpften Bereitstellungen mit einer einzelnen Pipeline verknüpft. Eine Bereitstellungs-Pipeline wird sowohl in der Staging- als auch in der Produktionsumgebung dieses Programms bereitgestellt. Während diese Kupplung normalerweise geeignet ist, gibt es bestimmte Anwendungsfälle, in denen Nachteile auftreten:

* Wenn Sie eine Bereitstellung für das Staging durchführen möchten, lehnen Sie den Schritt **Nach Produktion**&quot; in der Pipeline ab. Die Ausführung wird jedoch als abgebrochen markiert.
* Wenn Sie den neuesten Code in einer Staging-Umgebung für die Produktion bereitstellen möchten, müssen Sie die gesamte Pipeline einschließlich der Staging-Bereitstellung erneut bereitstellen, selbst wenn dort kein Code geändert wurde.
* Während einer Bereitstellung können Umgebungen nicht aktualisiert werden. Wenn Sie mehrere Tage warten, bis Sie in der Staging-Umgebung getestet haben, bevor Sie zur Produktion weiterleiten, bleibt die Produktionsumgebung weiterhin nicht verfügbar und kann nicht aktualisiert werden. Dieses Szenario verhindert unabhängige Aufgaben wie das Aktualisieren von [Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md).

Staging- und Nur-Produktions-Pipelines bieten Lösungen für diese Anwendungsfälle, indem spezielle Bereitstellungsoptionen bereitgestellt werden.

* **Bereitstellungs-Pipelines für reine Staging-Umgebungen** stellen nur in einer Staging-Umgebung bereit und beenden ihre Ausführung, sobald die Bereitstellung und die Tests abgeschlossen sind. Eine reine Staging-Pipeline verhält sich genauso wie die standardmäßig gekoppelte Full-Stack-Produktions-Pipeline, jedoch ohne die Schritte der Produktionsbereitstellung (Genehmigung, Zeitplan, Bereitstellung).
* **Bereitstellungs-Pipelines für reine Produktionsumgebungen:** Wird nur in einer Produktionsumgebung bereitgestellt, indem die letzte erfolgreiche Staging-Ausführung ausgewählt wird. Anschließend stellt sie ihre Artefakte in der Produktion bereit. Reine Produktions-Pipelines verwenden Artefakte zur Staging-Bereitstellung wieder, wobei die Build-Phase weggelassen wird.

Reine Staging- und reine Produktions-Pipelines werden nicht ausgeführt, während eine Full-Stack-Produktions-Pipeline ausgeführt wird und umgekehrt. Wenn sowohl bei der reinen Staging- als auch bei der Full-Stack-Produktions-Pipeline der Trigger **Bei Git-Änderungen** konfiguriert wurde und auf dieselbe Verzweigung und dasselbe Repository verweist, wird nur die reine Staging-Pipeline automatisch gestartet. Reine Produktions-Pipelines führen keinen Trigger zu **`On Git Changes`**, da sie nicht direkt mit einem Repository verknüpft sind.

Reine Produktions-Pipelines werden manuell ausgelöst, da sie nicht direkt mit einem Repository für **Bei Git-Änderungen**-Trigger verknüpft sind.

Diese dedizierten Pipelines bieten mehr Flexibilität, beachten Sie jedoch die folgenden Details zu Vorgängen und Empfehlungen.

>[!NOTE]
>
>Reine Produktions-Pipelines verwenden immer die Artefakte aus der reinen Staging-Pipeline. Dieser Prozess bleibt auch dann bestehen, wenn die standardmäßige gekoppelte Produktions-Pipeline in der Zwischenzeit eine andere Version zum Staging bereitgestellt hat.
>
>* Dieses Szenario führt zu unbeabsichtigten Code-Rollbacks.
>* Adobe empfiehlt, die Verwendung der standardmäßigen gekoppelten Produktions-Pipeline einzustellen, sobald Sie mit der Verwendung der produktionsbezogenen und der Nur-Staging-Pipeline beginnen.
>* Wenn Sie weiterhin die standardmäßigen gekoppelten Pipelines und die reinen Staging-/Produktions-Pipelines ausführen möchten, sollten Sie die Wiederverwendung von Artefakten nicht vergessen, um Code-Rollbacks zu vermeiden.

## Pipeline-Erstellung {#pipeline-creation}

Reine Produktions- und Staging-Pipelines werden ähnlich wie die standardmäßigen gekoppelten [Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) und [produktionsfremden Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) erstellt. Weitere Informationen finden Sie in den zugehörigen Dokumenten.

1. Klicken Sie im Fenster **Pipelines** auf **Pipeline hinzufügen**.

   * Wählen Sie **Produktionsfremde Pipeline hinzufügen** aus, [um eine reine Staging-Pipeline zu erstellen](#stage-only).
   * Wählen Sie **Produktions-Pipeline hinzufügen**, um [eine reine Produktions-Pipeline zu erstellen](#prod-only).

![Erstellen einer reinen Produktions-/Staging-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-stage-pipeline.png)

>[!NOTE]
>
>Bestimmte Optionen sind ausgegraut, wenn die entsprechenden Pipelines bereits vorhanden sind.
>
>* **Reine Produktions-Pipeline hinzufügen** ist nicht verfügbar, wenn noch keine reine Staging-Pipeline existiert.
>* **Produktions-Pipeline hinzufügen** ist nicht verfügbar, wenn bereits eine standardmäßige gekoppelte Pipeline vorhanden ist.
>* Pro Programm ist nur eine produktbezogene und eine studienbezogene Pipeline zulässig.

### Erstellen einer reinen Staging-Pipeline {#stage-only}

1. Wählen **Dialogfeld Produktionsfremde Pipeline hinzufügen** auf der Registerkarte **Konfiguration** das Feld **Bereitstellungs-Pipeline** für Ihre Pipeline aus.
1. Geben Sie im Feld Name der produktionsfremden Pipeline einen Freitext-Namen ein.
1. Wählen Sie die gewünschten Bereitstellungsoptionen aus und klicken Sie dann auf **Weiter**.

   ![Registerkarte „Konfiguration“ im Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-1.png)

1. Wählen Sie auf der Registerkarte **Quell-Code** **Full-Stack-Code** aus. Mit dieser Option wird die gesamte AEM-Anwendung (Backend, Dispatcher-/Web-Stufen-Konfiguration und alle Frontend-Module im Repository) erstellt und bereitgestellt.

1. Wählen Sie in der Dropdown-Liste **Zulässige Implementierungsumgebungen** die **Staging**-Umgebung als Bereitstellungsumgebung für Ihre Pipeline aus. Wenn Sie die Phase auswählen, wird eine Pipeline für die Staging-Umgebung erstellt (die Produktionsweiterleitung erfolgt über eine separate Pipeline).

1. Wählen Sie **Repository** und **Git-Verzweigung** in den entsprechenden Dropdown-Listen aus und klicken Sie dann auf **Weiter**.

   ![Registerkarte „Quell-Code“ im Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-2.png)

1. Auf der Registerkarte **Experience Audit** ist die angegebene Site-URL die veröffentlichte URL, die von Cloud Manager auf Seitenqualität geprüft wird.

1. Geben Sie im Feld **Seitenpfad** an, welche Seiten Sie überprüfen möchten, und klicken Sie dann auf **![Symbol „Hinzufügen“](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) Seite hinzufügen**.

   Experience Audit analysiert jeden Pfad, den Sie hinzufügen, auf Leistung, Barrierefreiheit, Progressive Web Apps, Best Practices, SEO und andere Qualitätsprüfungen. Sie können mehrere Pfade hinzufügen und entfernen, indem Sie auf ![Symbol „Cross Size 400“](https://spectrum.adobe.com/static/icons/ui_18/CrossSize400.svg) klicken.

   ![Registerkarte „Erlebnisprüfung“ im Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-3.png)

1. Klicken Sie auf **Speichern**.


### Erstellen einer reinen Produktions-Pipeline {#prod-only}

1. Geben **im Dialogfeld Nur Produktions-Pipeline hinzufügen** im Textfeld **Pipeline-Name** den Freitext-Namen der Pipeline ein.
1. Geben Sie im Feld **Name der Pipeline** den gewünschten Namen ein.
1. Wählen Sie unter **Optionen für die Produktionsimplementierung** die Option **Vor Implementierung in Produktion pausieren** aus.

   Mit dieser Option wird direkt vor dem Produktionsschritt ein manueller Validierungsschritt eingefügt. Die Pipeline wird angehalten und wartet, bis eine genehmigende Person (z. B. ein Bereitstellungs-Manager oder ein Geschäftsinhaber) die Produktionsbereitstellung genehmigt oder abbricht.

   Dient zur Änderungskontrolle oder für Prüfungen in letzter Minute.

1. Klicken Sie **Speichern**, um die reine Produktions-Pipeline mit diesen Optionen zu erstellen.

   ![Erstellen einer reinen Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/assets/add-production-only-pipeline.png)

## Ausführen reiner Staging- und reiner Produktions-Pipelines {#running}

Sie können die neuen Pipelines [wie jede andere Pipeline starten](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines). Sie können eine reine Produktions-Pipeline auch direkt von den Ausführungsdetails einer reinen Staging-Pipeline aus auslösen.

<!--
 * Stage-only and prod-only pipelines offer a new [emergency mode](#emergency-mode) to skip testing.
Prod-only pipeline run can be triggered directly from the execution details of a [stage-only pipeline](#stage-only-run).


### Emergency Mode {#emergency-mode}

When starting production-only and staging-online pipelines, you are prompted to confirm the start and how it starts.

* **Normal Mode** is a standard run and includes stage testing steps.
* **Emergency Mode** skips stage testing steps.

![Emergency Mode](/help/assets/configure-pipelines/emergency-mode.png)
-->

### Ausführen reiner Staging-Pipelines {#stage-only-run}

Nach Abschluss der Testschritte wird die Schaltfläche **Build weiterleiten** in den Ausführungsdetails angezeigt. Klicken Sie darauf, um eine reine Produktions-Pipeline auszulösen, die die Staging-Artefakte dieser Ausführung für die Produktion bereitstellt. Die Schaltfläche wird nur bei der letzten erfolgreichen Ausführung einer reinen Staging-Pipeline angezeigt.

![Ausführen einer reinen Staging-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/assets/stage-only-pipelines-run.png)

Wenn Sie auf **Build bewerben** klicken, wird ein Dialogfeld geöffnet, in dem Sie die Ausführung der zugehörigen produktionsbezogenen Pipeline bestätigen können. Um ihn zu starten, klicken Sie auf **Ausführen**.

![Dialogfeld „Build weiterleiten“ – „Pipeline ausführen“](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-run.png)

Wenn keine vorhanden ist, werden Sie in einem Einrichtungsdialogfeld aufgefordert, eine zu erstellen.

![Dialogfeld „Build weiterleiten“ – „Keine gültige Pipeline“](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-no-valid-pipeline.png)


### Ausführen reiner Produktions-Pipelines {#prod-only-run}

Bei einer **reinen Produktions**-Pipeline zeigt Cloud Manager die Quellartefakte an, die für die Produktion bereitgestellt werden. Überprüfen Sie den Schritt **Artefaktvorbereitung** für die Quellausführung und öffnen Sie ihn dann, um Details und Protokolle anzuzeigen.


![Artefaktdetails](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-only-pipelines-run.png)
