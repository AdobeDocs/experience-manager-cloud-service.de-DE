---
title: Anmerkungen zur GitHub-Prüfung
description: Erfahren Sie, wie GitHub Pull-Anfragen an Ihre privaten Repositorys mit Anmerkungen prüft, um Ihnen hilfreiches Feedback zu geben.
exl-id: 15178de8-8a8a-4300-8510-88875ad0fc8c
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: 'null'
workflow-type: tm+mt
source-wordcount: '240'
ht-degree: 52%

---


# Anmerkungen zur GitHub-Prüfung {#github-annotations}

Erfahren Sie, wie GitHub Pull-Anfragen an Ihre privaten Repositorys mit Anmerkungen prüft, um Ihnen hilfreiches Feedback zu geben.

## Überblick {#overview}

Wenn Sie [private Repositorys](private-repositories.md) für Ihr Cloud Manager-Programm verwenden, werden Prüfungen in GitHub automatisch bei jeder Pull-Anfrage ausgeführt. Diese PRs enthalten nützliche Informationen, die Ihnen helfen, Probleme mit Ihrem Code so schnell wie möglich zu verstehen.

![Beispiel für Anmerkungen zur GitHub-Prüfung](assets/github-check-annotations.png)

Von [SonarQube](/help/implementing/cloud-manager/custom-code-quality-rules.md) erkannte Probleme mit der [Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md) werden eindeutig aufgeführt.

![Beispiel für eine Anmerkung zu Code-Problemen](assets/github-check-annotations-example.png)

Die genaue Codezeile mit dem Problem wird angegeben und Sie können sie auswählen, um den entsprechenden Code anzuzeigen. Diese Anmerkungen decken Code-Probleme ab, nicht nur die in der Pull-Anfrage.

![Beispiel für eine Anmerkung zu Code-Problemen](assets/github-check-annotations-example-code.png)

Alle kommentierten Zeilen werden auf der Registerkarte **Geänderte Dateien** für die GitHub-Pull-Anfrage zusammengetragen. Anmerkungen für unveränderte Pull-Request-Dateien werden in ihrem eigenen Abschnitt angezeigt.

![Beispiel für Anmerkungen auf der Registerkarte „Geänderte Dateien“](assets/github-check-annotations-files-changed.png)

## Code-Qualitäts-Pipelines {#code-quality-pipelines}

Die [Code](/help/implementing/cloud-manager/code-quality-testing.md)Qualitätsergebnisse sind auch in der Pipeline sichtbar, die von Cloud Manager automatisch am unteren Rand der Registerkarte **Prüfungen** Trigger wird. Auf sie kann auch über die **Details** der Pull-Anforderungsprüfung zugegriffen werden.

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality.png)

![Beispiel für Anmerkungen](assets/github-check-annotations-code-quality-2.png)

Sie können die Probleme auch in Form einer CSV-Datei visualisieren. Sie können diese CSV-Datei abrufen[&#x200B; indem Sie die Details der Pipeline-Ausführung in Cloud Manager &#x200B;](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md#view-details).
