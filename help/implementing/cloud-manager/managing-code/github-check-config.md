---
title: Konfiguration der GitHub-Prüfung für private Repositorys
description: Erfahren Sie, wie Sie die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren.
exl-id: 3ae3c19e-2621-4073-ae17-32663ccf9e7b
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 6eabf593a7566129d32d9a5888cc480117bef51f
workflow-type: tm+mt
source-wordcount: '243'
ht-degree: 63%

---

# Konfiguration der GitHub-Prüfung für private Repositorys {#github-check-config}

Erfahren Sie, wie Sie die automatisch erstellten Pipelines so steuern, dass sie jede Pull-Anfrage an ein privates Repository validieren.

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
| `template.programID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Sie können es verwenden, um die [Pipeline-Variablen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) wiederzuverwenden, die auf einer vorhandenen Pipeline festgelegt sind, die automatisch von jeder Pull-Anforderung erstellt wird. |
| `template.pipelineID` | Ganzzahl | Es werden keine Pipeline-Variablen wiederverwendet | Sie können es verwenden, um die [Pipeline-Variablen](/help/implementing/cloud-manager/configuring-pipelines/pipeline-variables.md) wiederzuverwenden, die auf einer vorhandenen Pipeline festgelegt sind, die automatisch von jeder Pull-Anforderung erstellt wird. |
| `namePrefix` | Zeichenfolge | `Full Stack Code Quality Pipeline for PR` | Wird verwendet, um den Namen der automatisch erstellten Pipeline festzulegen |
| `importantMetricsFailureBehavior` | `CONTINUE` oder `FAIL` oder `PAUSE` | `CONTINUE` | Legt das wichtige Metrikverhalten der Pipeline fest<br>`CONTINUE` = Wenn eine wichtige Metrik fehlschlägt, wechselt die Pipeline automatisch vorwärts.<br>`FAIL` = Die Pipeline wird mit dem Status FEHLGESCHLAGEN beendet, wenn eine wichtige Metrik fehlschlägt.<br>`PAUSE` = Der Codescan-Schritt erhält einen WARING-Status, wenn eine wichtige Metrik fehlschlägt, und muss manuell fortgesetzt werden |
