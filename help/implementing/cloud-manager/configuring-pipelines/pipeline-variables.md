---
title: Pipeline-Variablen in Cloud Manager
description: Erfahren Sie, wie Sie Pipeline-Variablen in Cloud Manager verwenden können, um bestimmte Konfigurationsvariablen für Ihren Build zu verwalten.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '637'
ht-degree: 97%

---

# Pipeline-Variablen in Cloud Manager {#configuring-pipeline-variables}

Ihr Build-Prozess basiert möglicherweise auf bestimmten Konfigurationsvariablen, die nicht im Git-Repository gespeichert werden sollen. Oder Sie müssen sie ggf. zwischen Pipeline-Ausführungen in derselben Verzweigung anpassen. Mit Cloud Manager können Sie diese Einstellungen als Pipeline-Variablen verwalten.

## Über Pipeline-Variablen {#pipeline-variables}

Mithilfe von Cloud Manager können Sie Pipeline-Variablen auf verschiedene Arten konfigurieren.

* [Verwenden der Cloud Manager-Benutzeroberfläche](#ui)
* [Verwenden der Cloud Manager-CLI](#cli)
* [Verwenden der Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

Variablen können entweder als reiner Test oder im Ruhezustand verschlüsselt gespeichert werden. In beiden Fällen werden Variablen innerhalb der Build-Umgebung als Umgebungsvariable bereitgestellt, die dann in der Datei `pom.xml` oder anderen Build-Skripten referenziert werden kann.

## Hinzufügen einer Pipeline-Variablen über Cloud Manager {#ui}

Pipeline-Variablen können über die Cloud Manager-Benutzeroberfläche konfiguriert und verwaltet werden. Sie helfen beim Optimieren der Pipeline-Verwaltung, insbesondere wenn unterschiedliche Konfigurationen in verschiedenen Schritten erforderlich sind.

Sie müssen über Berechtigungen zum Bearbeiten der Pipeline verfügen, um Pipeline-Variablen hinzufügen, bearbeiten und löschen zu können.

Wenn eine Pipeline ausgeführt wird, wird die Variablenverwaltung blockiert.

**So fügen Sie eine Pipeline-Variable über Cloud Manager hinzu:**

1. Klicken Sie [beim Verwalten Ihrer Pipelines](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) auf das Symbol ![Auslassungspunkte – Mehrsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) der Pipeline, für die Pipeline-Variablen erstellt werden sollen.

1. Klicken Sie im Dropdown-Menü auf **Variablen anzeigen/bearbeiten**.

   ![Bearbeiten/Anzeigen von Pipeline-Variablen](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Geben Sie im Dialogfeld **Variablenkonfiguration** die Details in die erste Zeile der Tabelle ein.

   | Feld | Beschreibung |
   | --- | --- |
   | Name | Ein eindeutiger Name der Konfigurationsvariablen. Er identifiziert die spezifische Variable, die in der Pipeline verwendet wird, und muss den folgenden Namenskonventionen entsprechen:<ul><li>Variablen dürfen nur alphanumerische Zeichen und einen Unterstrich (`_`) enthalten.</li><li>Die Namen sollten in Großbuchstaben geschrieben sein.</li><li>Pro Pipeline sind maximal 200 Variablen zulässig.</li><li>Jeder Name darf maximal 100 Zeichen lang sein.</li><li>Jede `string`-Variable darf höchstens 2047 Zeichen enthalten.</li><li>Jede Variable des Typs `secretString` darf maximal 500 Zeichen enthalten.</li></ul> |
   | Wert | Der Wert, den die Variable enthält. |
   | Angewendeter Schritt | Erforderlich. Der Schritt in der Pipeline, für den die Variable gilt:<ul><li>**Build**: Die Variable wird während des Build-Prozesses angewendet.</li><li>**Funktionsprüfung**: Die Variable wird während des Schritts „Funktionsprüfung“ verwendet.</li><li>**UI-Tests** – Die Variable wird während der UI-Testphase verwendet.</li><li>**Bereitstellen** - Die Variable wird während des Bereitstellungsschritts verwendet. Verwenden Sie diese Variable beispielsweise für Edge Delivery Services-Pipelines.</li></ul> |
   | Typ | Wählen Sie aus, ob es sich bei der Variablen um reinen Text handelt oder ob sie als geheim verschlüsselt wurde. |

   ![Variable hinzufügen](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png)

1. Klicken Sie auf **Hinzufügen**.

   Fügen Sie nach Bedarf weitere Variablen hinzu.

1. Klicken Sie auf **Speichern**.

## Bearbeiten einer Pipeline-Variablen {#edit-ui}

1. Klicken Sie bei der [Verwaltung Ihrer Pipelines ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) auf ![Auslassungspunkte – Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) neben der Pipeline, für die Sie Pipeline-Variablen bearbeiten möchten.

1. Klicken Sie im Dropdown-Menü auf **Variablen anzeigen/bearbeiten**.

   ![Pipeline-Variablen anzeigen/bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Klicken Sie im Dialogfeld **Variablenkonfiguration** auf ![Auslassungspunkte – Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) der Variable, die Sie ändern möchten.

1. Klicken Sie im Dropdown-Menü auf **Bearbeiten**.

   ![Variable bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png)

1. Aktualisieren Sie den Wert der Variablen nach Bedarf.

   Nur der Wert der Variablen kann geändert werden.

1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf ![Apply - Checkmark icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg), um die Änderung anzuwenden.
   * Klicken Sie auf ![Undo icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Undo_18_N.svg), um die Änderung zurückzusetzen.

1. Klicken Sie auf **Speichern**.


## Löschen einer Pipeline-Variablen {#delete-ui}

1. Klicken Sie bei der [Verwaltung Ihrer Pipelines ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) auf ![Auslassungspunkte – Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) neben der Pipeline, für die Sie Pipeline-Variablen löschen möchten.

1. Klicken Sie im Dropdown-Menü auf **Variablen anzeigen/bearbeiten**.

   ![Pipeline-Variablen anzeigen/bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Klicken Sie im Dialogfeld **Variablenkonfiguration** auf ![Auslassungspunkte – Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) neben der Variable, die Sie entfernen möchten. Klicken Sie anschließend auf **Löschen**.

## Festlegen von Pipeline-Variablen mithilfe der Cloud Manager-Befehlszeilenschnittstelle {#cli}

Dieser Befehl in der Befehlszeilenschnittstelle legt eine Variable fest.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Dieser Befehl listet Variablen auf.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Bei Verwendung in einer Maven-Datei `pom.xml` ist es in der Regel hilfreich, diese Variablen Maven-Eigenschaften mithilfe einer Syntax zuzuordnen, die dem folgenden Beispiel ähnelt:

```xml
        <profile>
            <id>cmBuild</id>
            <activation>
                <property>
                    <name>env.CM_BUILD</name>
                </property>
            </activation>
            <properties>
                <my.custom.property>${env.MY_CUSTOM_VARIABLE}</my.custom.property> 
            </properties>
        </profile>
```
