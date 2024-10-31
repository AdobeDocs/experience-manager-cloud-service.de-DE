---
title: Konfiguration der GitHub-Prüfung für private Repositorys
description: Erfahren Sie, wie Sie die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren.
exl-id: 3ae3c19e-2621-4073-ae17-32663ccf9e7b
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 0a08d5fc033f4f4f57b824492766e5b42a801b6e
workflow-type: ht
source-wordcount: '295'
ht-degree: 100%

---

# Konfiguration der GitHub-Prüfung für private Repositorys {#github-check-config}

Erfahren Sie, wie Sie die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren.

## Konfiguration von GitHub-Prüfungen {#configuration}

Bei der Verwendung von [privaten Repositorys](private-repositories.md#using) wird automatisch eine [Full-Stack-Code-Qualitäts-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

Sie können diese Prüfungen steuern, indem Sie eine Konfigurationsdatei namens `.cloudmanager/pr_pipelines.yml` in der Standardverzweigung des privaten Repositorys erstellen.

```yaml
github:
  shouldDeletePreviousComment: false
  shouldSkipCheckAnnotations: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR
    importantMetricsFailureBehavior: CONTINUE
```

| Parameter | Mögliche Werte | Standard | Beschreibung |
| --- | --- | --- | --- |
| `shouldDeletePreviousComment` | `true` oder `false` | `false` | Legt fest, ob bei dieser GitHub-Pull-Anfrage nur der letzte Kommentar oder alle Kommentare mit den Ergebnissen der Codescans beibehalten werden sollen. Ist `false` (Standardeinstellung) festgelegt, werden vorherige Kommentare nicht gelöscht. |
| `shouldSkipCheckAnnotations` | `true` oder `false` | `false` | Legt fest, ob zusätzliche Anmerkungen bei der Prüfung der GitHub-Pull-Anfrage vorhanden sein sollen oder nicht. Ist `false` (Standardeinstellung) festgelegt, werden Prüfanmerkungen nicht übersprungen und in das Feedback aufgenommen. |
| `type` | `CI_CD` | Nicht zutreffend | Definiert das Verhalten der CI/CD(Continuous Integration/Continuous Deploymen)-Pipeline-Konfigurationen. |
| `template.programId` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Kann verwendet werden, um die [Pipeline-Variablen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) wiederzuverwenden, die auf einer vorhandenen Pipeline festgelegt sind, die automatisch von jeder Pull-Anfrage erstellt wird. |
| `template.pipelineId` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Kann verwendet werden, um die [Pipeline-Variablen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) wiederzuverwenden, die auf einer vorhandenen Pipeline festgelegt sind, die automatisch von jeder Pull-Anfrage erstellt wird. |
| `namePrefix` | Zeichenfolge | `Full Stack Code Quality Pipeline for PR` | Wird verwendet, um das Präfix für den Namen der automatisch erstellten Pipeline festzulegen. |
| `importantMetricsFailureBehavior` | `CONTINUE` oder `FAIL` oder `PAUSE` | `CONTINUE` | Legt das Verhalten der Pipeline für wichtige Metriken fest<br>`CONTINUE` = Wenn eine wichtige Metrik fehlschlägt, wird die Pipeline automatisch weitergeleitet<br>`FAIL` = Wenn eine wichtige Metrik fehlschlägt, endet die Pipeline mit dem Status FEHLGESCHLAGEN<br>`PAUSE` = Wenn eine wichtige Metrik fehlschlägt, erhält der Code-Scan-Schritt einen Status WARTEN und muss manuell wieder aufgenommen werden |




