---
title: Aufspaltung von Pipelines nur für Staging und Produktion
description: Erfahren Sie, wie Sie Staging- und Produktionsbereitstellungen mithilfe von dedizierten Pipelines aufteilen können.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md
hide: false
hidefromtoc: false
index: true
exl-id: 7d76a87c-122c-4c4d-8071-957bef4c9cf1
source-git-commit: f61183c43d9380900b92fe040098e2eb3155979c
workflow-type: tm+mt
source-wordcount: '1052'
ht-degree: 48%

---

# Aufspaltung von Pipelines nur für Staging und Produktion {#stage-prod-only}

Sie können Staging- und Produktionsbereitstellungen mithilfe dedizierter Pipelines aufteilen.

## Übersicht {#overview}

Staging- und Produktionsumgebungen sind eng miteinander verbunden. Standardmäßig sind die damit verknüpften Bereitstellungen mit einer einzelnen Pipeline verknüpft. Hierbei handelt es sich um eine Bereitstellungs-Pipeline, die sowohl für die Staging- als auch für die Produktionsumgebung in diesem Programm bereitgestellt wird. Diese Kopplung ist zwar in der Regel geeignet, es gibt jedoch einige Anwendungsfälle, in denen Nachteile entstehen:

* Wenn Sie die Bereitstellung nur für die Staging-Umgebung durchführen möchten, lehnen Sie den Schritt **Zur Produktion weiterleiten** in der Pipeline ab. Die Ausführung wird jedoch als abgebrochen markiert.
* Wenn Sie den neuesten Code in einer Staging-Umgebung für die Produktion bereitstellen möchten, müssen Sie die gesamte Pipeline einschließlich der Staging-Bereitstellung erneut bereitstellen, selbst wenn dort kein Code geändert wurde.
* Während einer Bereitstellung können Umgebungen nicht aktualisiert werden. Wenn Sie mehrere Tage in der Staging-Umgebung pausieren und testen möchten, bevor Sie sie zur Produktion weiterleiten, bleibt die Produktionsumgebung gesperrt und kann nicht aktualisiert werden. Dieses Szenario macht nicht abhängige Aufgaben wie die Aktualisierung von [Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md) unmöglich.

Reine Staging- und Produktions-Pipelines bieten Lösungen für diese Anwendungsfälle, indem sie dedizierte Bereitstellungsoptionen bieten.

* **Bereitstellungs-Pipelines für reine Staging-Umgebungen** stellen nur in einer Staging-Umgebung bereit und beenden ihre Ausführung, sobald die Bereitstellung und die Tests abgeschlossen sind. Eine reine Staging-Pipeline verhält sich genauso wie die standardmäßig gekoppelte Full-Stack-Produktions-Pipeline, jedoch ohne die Schritte der Produktionsbereitstellung (Genehmigung, Zeitplan, Bereitstellung).
* **Nur-Produktions-Bereitstellungs-Pipelines:** Wird nur für die Produktion bereitgestellt, indem die neueste erfolgreiche Staging-Ausführung ausgewählt wird. Anschließend stellen sie ihre Artefakte für die Produktion bereit. Reine Produktions-Pipelines verwenden die Artefakte aus den Staging-Bereitstellungen erneut und überspringen die Erstellungsphase.

Reine Staging- und reine Produktions-Pipelines werden nicht ausgeführt, während eine Full-Stack-Produktions-Pipeline ausgeführt wird und umgekehrt. Wenn sowohl bei der reinen Staging- als auch bei der Full-Stack-Produktions-Pipeline der Trigger **Bei Git-Änderungen** konfiguriert wurde und auf dieselbe Verzweigung und dasselbe Repository verweist, wird nur die reine Staging-Pipeline automatisch gestartet. Reine Produktions-Pipelines werden nicht mit **`On Git Changes`** gestartet, da sie nicht direkt mit einem Repository verknüpft sind.

Reine Produktions-Pipelines werden nicht manuell ausgelöst, da sie nicht direkt mit einem Repository für **Bei Git-Änderungen** verknüpft sind.

Diese dedizierten Pipelines bieten mehr Flexibilität. Beachten Sie jedoch die folgenden Details zum Betrieb und Empfehlungen.

>[!NOTE]
>
>Reine Produktions-Pipelines verwenden immer die Artefakte aus der reinen Staging-Pipeline. Dieser Prozess wird auch dann eingehalten, wenn die standardmäßige gekoppelte Produktions-Pipeline in der Zwischenzeit etwas Anderes für die Staging-Umgebung bereitgestellt hat.
>
>* Ein solches Szenario könnte zu unerwünschten Code-Rollbacks führen.
>* Adobe empfiehlt, die standardmäßig gekoppelte Produktions-Pipeline nicht mehr zu verwenden, wenn Sie mit der Verwendung der reinen Produktions- und Staging-Pipelines beginnen.
>* Wenn Sie weiterhin die standardmäßigen gekoppelten Pipelines und die reinen Staging-/Produktions-Pipelines ausführen möchten, sollten Sie die Wiederverwendung von Artefakten nicht vergessen, um Code-Rollbacks zu vermeiden.

## Pipeline-Erstellung {#pipeline-creation}

Die Erstellung von reinen Produktions- und Staging-Pipelines erfolgt auf ähnliche Weise wie bei den standardmäßig gekoppelten [Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) und [produktionsfremden Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md). Weitere Informationen finden Sie in den zugehörigen Dokumenten.

1. Klicken Sie im Fenster **Pipelines** auf **Pipeline hinzufügen**.

   * Wählen Sie **Produktionsfremde Pipeline hinzufügen** aus, um [eine reine Staging-Pipeline zu &#x200B;](#stage-only).
   * Wählen Sie **Nur Produktions-Pipeline hinzufügen** aus, um [eine produktionsgeschützte Pipeline zu erstellen](#prod-only).

![Erstellen einer reinen Produktions-/Staging-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-stage-pipeline.png)

>[!NOTE]
>
>Bestimmte Optionen können ausgegraut sein, wenn die entsprechenden Pipelines bereits vorhanden sind.
>
>* **Reine Produktions-Pipeline hinzufügen** ist nicht verfügbar, wenn noch keine reine Staging-Pipeline existiert.
>* **Produktions-Pipeline hinzufügen** ist nicht verfügbar, wenn bereits eine standardmäßige gekoppelte Pipeline vorhanden ist.
>* Pro Programm ist nur je eine reine Produktions-Pipeline und eine reine Staging-Pipeline zulässig.

### Erstellen einer Pipeline, die nur für Staging vorgesehen ist {#stage-only}

1. Wählen **Dialogfeld Produktionsfremde Pipeline hinzufügen** auf der Registerkarte **Konfiguration** das Feld **Bereitstellungs-Pipeline** für Ihre Pipeline aus.
1. Geben Sie im Feld Name der produktionsfremden Pipeline einen Freitext-Namen ein.
1. Wählen Sie die gewünschten Bereitstellungsoptionen aus und klicken Sie dann auf **Weiter**.

   ![Registerkarte „Konfiguration“ im Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-1.png)

1. Wählen Sie auf der Registerkarte **Source** Code **die Option „Full Stack Code**. Mit dieser Option wird die gesamte AEM-Anwendung (Backend, Dispatcher-/Web-Stufen-Konfiguration und alle Frontend-Module im Repository) erstellt und bereitgestellt.

1. Wählen Sie in **Dropdown** Liste „Mögliche Bereitstellungsumgebungen“ die **Staging** Umgebung als Bereitstellungsumgebung für Ihre Pipeline aus. Wenn Sie die Phase auswählen, wird eine Pipeline für die Staging-Umgebung erstellt (die Produktionsweiterleitung erfolgt über eine separate Pipeline).

1. Wählen Sie **Repository** und **Git-Verzweigung** in den entsprechenden Dropdown-Listen aus und klicken Sie dann auf **Weiter**.

   ![Registerkarte &quot;Source-Code“ im Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-2.png)

1. Auf der Registerkarte **Experience Audit** ist die angegebene Site-URL die veröffentlichte URL, die von Cloud Manager auf Seitenqualität geprüft wird.

1. Geben Sie im Feld **Seitenpfad** an, welche Seiten Sie überprüfen möchten, und klicken Sie dann auf **![Symbol hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) Seite hinzufügen**.

   Experience Audit analysiert jeden Pfad, den Sie hinzufügen, auf Leistung, Barrierefreiheit, Progressive Web Apps, Best Practices, SEO und andere Qualitätsprüfungen. Sie können mehrere Pfade hinzufügen und entfernen, indem Sie auf das Symbol ![Cross Size 400“ &#x200B;](https://spectrum.adobe.com/static/icons/ui_18/CrossSize400.svg).

   ![Registerkarte „Erlebnisprüfung“ im Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/add-non-prod-pipeline-3.png)

1. Klicken Sie auf **Speichern**.


### Erstellen einer schreibgeschützten Pipeline {#prod-only}

1. Geben Sie im Dialogfeld **Nur Produktions-Pipeline hinzufügen** im Textfeld **Pipeline-Name** den Freitext-Namen der Pipeline ein.
1. Geben Sie **Feld „Name** Pipeline“ den gewünschten Namen ein.
1. Wählen **unter „Produktionsbereitstellungsoptionen** die Option **Anhalten vor der Bereitstellung in der Produktion** aus.

   Mit dieser Option wird direkt vor dem Produktionsschritt ein manuelles Validierungs-Gate eingefügt. Die Pipeline wird angehalten und wartet, bis eine genehmigende Person (z. B. ein Bereitstellungs-Manager oder ein Geschäftsinhaber) die Produktionsbereitstellung genehmigt oder abbricht.

   Dient zur Änderungskontrolle oder für Prüfungen in letzter Minute.

1. Klicken Sie **Speichern**, um die produktionsgeschützte Pipeline mit diesen Optionen zu erstellen.

   ![Erstellen einer reinen Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/assets/add-production-only-pipeline.png)

## Ausführen von Pipelines nur für Staging und Nur-Produktion {#running}

Sie können die neuen Pipelines starten [wie jede andere Pipeline](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#running-pipelines). Sie können eine reine Produktions-Pipeline auch direkt aus den Ausführungsdetails einer Nur-Staging-Pipeline in Trigger bringen.

<!-- * Stage-only and prod-only pipelines offer a new [emergency mode](#emergency-mode) to skip testing.
Prod-only pipeline run can be triggered directly from the execution details of a [stage-only pipeline](#stage-only-run).


### Emergency Mode {#emergency-mode}

When starting production-only and staging-online pipelines, you are prompted to confirm the start and how it starts.

* **Normal Mode** is a standard run and includes stage testing steps.
* **Emergency Mode** skips stage testing steps.

![Emergency Mode](/help/assets/configure-pipelines/emergency-mode.png) -->

### Ausführen von Pipelines nur für Staging {#stage-only-run}

In den Ausführungsdetails wird nach **Testschritten eine Schaltfläche** Build bewerben“ angezeigt. Klicken Sie darauf, um eine reine Produktions-Pipeline Trigger, die die Staging-Artefakte dieses Durchgangs für die Produktion bereitstellt. Die Schaltfläche wird nur bei der letzten erfolgreichen Nur-Staging-Ausführung angezeigt.

![Ausführen einer reinen Staging-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/assets/stage-only-pipelines-run.png)

Wenn Sie auf **Build bewerben** klicken, wird ein Dialogfeld geöffnet, in dem Sie die Ausführung der zugehörigen produktionsbezogenen Pipeline bestätigen können. Klicken Sie auf **Ausführen**, um sie zu starten.

![Dialogfeld „Erstellen - Pipeline ausführen“ &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-run.png)

Wenn keine vorhanden ist, werden Sie in einem Dialogfeld zur Einrichtung aufgefordert, eine zu erstellen.

![Build bewerben - Kein gültiges Pipeline-Dialogfeld](/help/implementing/cloud-manager/configuring-pipelines/assets/promote-build-no-valid-pipeline.png)


### Ausführen von schreibgeschützten Pipelines {#prod-only-run}

Bei einer **-**-Pipeline zeigt Cloud Manager die Quellartefakte an, die für die Produktion bereitgestellt werden. Überprüfen Sie **Schritt „Artefaktvorbereitung** für die Quellausführung und öffnen Sie ihn dann, um Details und Protokolle anzuzeigen.


![Artefaktdetails](/help/implementing/cloud-manager/configuring-pipelines/assets/prod-only-pipelines-run.png)
