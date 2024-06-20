---
title: Konfiguration der GitHub-Prüfung für private Repositorys
description: Steuern der automatisch erstellten Pipelines, um jede Pull-Anfrage an ein privates Repository zu validieren.
exl-id: 3ae3c19e-2621-4073-ae17-32663ccf9e7b
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 100%

---

# Konfiguration der GitHub-Prüfung für private Repositorys {#github-check-config}

Steuern der automatisch erstellten Pipelines, um jede Pull-Anfrage an ein privates Repository zu validieren.

## Konfiguration von GitHub-Prüfungen {#configuration}

Bei der Verwendung von [privaten Repositorys](private-repositories.md#using) wird automatisch eine [Full-Stack-Code-Qualitäts-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) erstellt. Diese Pipeline wird bei jeder Aktualisierung einer Pull-Anfrage gestartet.

Sie können diese Prüfungen steuern, indem Sie eine Datei namens `.cloudmanager/pr_pipelines.yml` in der Standardverzweigung des privaten Repositorys erstellen.

```yaml
github:
  shouldDeletePreviousComment: false
pipelines:
  - type: CI_CD
    template:
      programId: 1234
      pipelineId: 456
    namePrefix: Full Stack Code Quality Pipeline for PR 
    importantMetricsFailureBehavior: CONTINUE
```

| Parameter | Mögliche Werte | Standard | Beschreibung |
|---|---|---|---|
| `shouldDeletePreviousComment` | `true` oder `false` | `false` | Ob bei dieser GitHub-Pull-Anfrage nur der letzte Kommentar oder alle Kommentare mit den Ergebnissen der Code-Scans beibehalten werden sollen |
| `type` | `CI_CD` | Nicht zutreffend | Definiert das Verhalten einer CI/CD-Pipeline |
| `template.programID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Kann verwendet werden, um die [Pipeline-Variablen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) wiederzuverwenden, die auf einer der vorhandenen Pipelines festgelegt sind, die automatisch von jeder Pull-Anfrage erstellt werden. |
| `template.pipelineID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Kann verwendet werden, um die [Pipeline-Variablen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) wiederzuverwenden, die auf einer der vorhandenen Pipelines festgelegt sind, die automatisch von jeder Pull-Anfrage erstellt werden. |
| `namePrefix` | Zeichenfolge | `Full Stack Code Quality Pipeline for PR` | Wird verwendet, um den Namen der automatisch erstellten Pipeline festzulegen |
| `importantMetricsFailureBehavior` | `CONTINUE` oder `FAIL` oder `PAUSE` | `CONTINUE` | Legt das Verhalten der Pipeline für wichtige Metriken fest<br>`CONTINUE` = Wenn eine wichtige Metrik fehlschlägt, wird die Pipeline automatisch weitergeleitet<br>`FAIL` = Wenn eine wichtige Metrik fehlschlägt, endet die Pipeline mit dem Status FEHLGESCHLAGEN<br>`PAUSE` = Wenn eine wichtige Metrik fehlschlägt, erhält der Code-Scan-Schritt den Status WARTEN und muss manuell wieder aufgenommen werden |
