---
title: Pipeline-Variablen konfigurieren
description: Erfahren Sie, wie Sie Pipeline-Variablen in Cloud Manager verwenden können, um bestimmte Konfigurationsvariablen für Ihren Build zu verwalten.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f7a8e823f058115f11241f0864517432a7dea5ab
workflow-type: tm+mt
source-wordcount: '611'
ht-degree: 28%

---

# Pipeline-Variablen konfigurieren {#configuring-pipeline-variables}

Ihr Build-Prozess basiert möglicherweise auf bestimmten Konfigurationsvariablen, die nicht im Git-Repository gespeichert werden sollen. Sie müssen sie auch zwischen Pipeline-Ausführungen auf demselben Zweig anpassen. Mit Cloud Manager können Sie diese Einstellungen als Pipeline-Variablen verwalten.

## Pipeline-Variablen {#pipeline-variables}

Mithilfe von Cloud Manager können Sie Pipeline-Variablen auf verschiedene Arten konfigurieren.

* [Verwenden der Cloud Manager-Benutzeroberfläche](#ui)
* [Verwenden der Cloud Manager-CLI](#cli)
* [Verwenden der Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

Variablen können entweder als reiner Test oder mit Data-at-Rest-Verschlüsselung gespeichert werden. In beiden Fällen werden Variablen innerhalb der Build-Umgebung als Umgebungsvariable bereitgestellt, die dann in der Datei `pom.xml` oder anderen Build-Skripten referenziert werden kann.

## Hinzufügen von Pipeline-Variablen über Cloud Manager {#ui}

Pipeline-Variablen können über die Cloud Manager-Benutzeroberfläche konfiguriert und verwaltet werden. Sie helfen bei der Optimierung der Pipeline-Verwaltung, insbesondere wenn unterschiedliche Konfigurationen in verschiedenen Schritten erforderlich sind.

Sie müssen über die Berechtigungen zum Bearbeiten der Pipeline verfügen, um Pipeline-Variablen hinzuzufügen, zu bearbeiten und zu löschen.

Wenn eine Pipeline ausgeführt wird, wird die Variablenverwaltung blockiert.

### Pipeline-Variable hinzufügen {#add-ui}

1. Klicken Sie beim Verwalten Ihrer Pipelines [ auf das Symbol &quot;![Ellipse - Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) der Pipeline, für die Sie Pipeline-Variablen erstellen möchten.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)

1. Klicken Sie im Dropdownmenü auf **Variablen anzeigen/bearbeiten**.

   ![Pipeline-Variablen anzeigen/bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Geben Sie im Dialogfeld **Variablenkonfiguration** die Details in die erste Zeile der Tabelle ein.

   | Feld | Beschreibung |
   | --- | --- |
   | Name | Ein eindeutiger Name der Konfigurationsvariablen. Er identifiziert die spezifische Variable, die in der Pipeline verwendet wird. Sie muss den folgenden Benennungskonventionen entsprechen:<ul><li>Variablen dürfen nur alphanumerische Zeichen und den Unterstrich (`_`) enthalten.</li><li>Die Namen sollten in Großbuchstaben geschrieben sein.</li><li>Pro Pipeline sind maximal 200 Variablen zulässig.</li><li>Jeder Name darf maximal 100 Zeichen lang sein.</li><li>Jede `string`-Variable darf höchstens 2047 Zeichen enthalten.</li><li>Jede Variable des Typs `secretString` darf maximal 500 Zeichen enthalten.</li></ul> |
   | Wert | Der Wert, den die Variable enthält. |
   | ANGEWENDETER SCHRITT | Erforderlich. Der Schritt in der Pipeline, für den die Variable gilt:<ul><li>**Build** - Die Variable wird während des Build-Prozesses angewendet.</li><li>**Funktionstests** - Die Variable wird während des Funktionstestschritts verwendet.</li><li>**UI-Tests** - Die Variable wird während der UI-Testphase verwendet.</li></ul> |
   | Typ | Wählen Sie aus, ob es sich bei der Variablen um Text handelt oder als geheim verschlüsselt wurde. |

   ![Variable hinzufügen](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png)

1. Klicken Sie auf **Hinzufügen**.

   Fügen Sie nach Bedarf weitere Variablen hinzu.

1. Klicken Sie auf **Speichern**.

### Pipeline-Variable bearbeiten {#edit-ui}

1. Klicken Sie beim Verwalten Ihrer Pipelines [ auf das Symbol &quot;![Ellipse - Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) der Pipeline, für die Sie Pipeline-Variablen bearbeiten möchten.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)

1. Klicken Sie im Dropdown-Menü auf **Variablen anzeigen/bearbeiten**.

   ![Pipeline-Variablen anzeigen/bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Klicken Sie im Dialogfeld **Variablenkonfiguration** auf das Symbol ![Ellipse - Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) der Variablen, die Sie ändern möchten.

1. Klicken Sie im Dropdown-Menü auf **Bearbeiten**.

   ![Variable bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png)

1. Aktualisieren Sie den Wert der Variablen nach Bedarf.

   Nur der Wert der Variablen kann geändert werden.

1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf ![Anwenden - Häkchensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Checkmark_18_N.svg) , um die Änderung anzuwenden.
   * Klicken Sie auf das Symbol ![Rückgängig](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Undo_18_N.svg) , um die Änderung rückgängig zu machen.

1. Klicken Sie auf **Speichern**.

### Pipeline-Variable löschen {#delete-ui}

1. Klicken Sie beim Verwalten Ihrer Pipelines [ auf das Symbol &quot;![Ellipse - Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) der Pipeline, für die Sie Pipeline-Variablen löschen möchten.](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md)

1. Klicken Sie im Dropdown-Menü auf **Variablen anzeigen/bearbeiten**.

   ![Pipeline-Variablen anzeigen/bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Klicken Sie im Dialogfeld **Variablenkonfiguration** auf das Symbol ![Ellipse - Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) der Variablen, die Sie entfernen möchten.

1. Klicken Sie im Dropdown-Menü auf **Löschen**.


## Festlegen von Pipeline-Variablen mithilfe der Cloud Manager-CLI {#cli}

Dieser Befehl in der CLI (Befehlszeilenschnittstelle) legt eine Variable fest.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Dieser Befehl listet Variablen auf.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Bei Verwendung in einer Maven `pom.xml` -Datei ist es häufig nützlich, diese Variablen mit Maven-Eigenschaften zu verknüpfen, indem eine Syntax ähnlich der folgenden verwendet wird:

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
