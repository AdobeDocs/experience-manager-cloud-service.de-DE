---
title: Pipeline-Variablen konfigurieren
description: Erfahren Sie, wie Sie Pipeline-Variablen in Cloud Manager verwenden können, um bestimmte Konfigurationsvariablen für Ihren Build zu verwalten.
exl-id: cfcef2e2-0590-457d-a0f9-6092a6d9e0e8
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 61%

---

# Pipeline-Variablen konfigurieren {#configuring-pipeline-variables}

Der Build-Prozess kann von bestimmten Konfigurationsvariablen abhängen, die nicht im Git-Repository platziert werden können oder zwischen Pipeline-Ausführungen mit derselben Verzweigung variieren müssen.  Mit Cloud Manager können Sie diese Daten als Pipeline-Variablen verwalten.

## Pipeline-Variablen {#pipeline-variables}

Mithilfe von Cloud Manager können Sie Pipeline-Variablen auf verschiedene Arten konfigurieren.

* [Über die Benutzeroberfläche von Cloud Manager](#ui)
* [Verwenden der Cloud Manager-CLI](#cli)
* [Verwenden der Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/reference/api/#tag/Variables/operation/getPipelineVariables)

Variablen können entweder als reiner Test oder mit Data-at-Rest-Verschlüsselung gespeichert werden. In beiden Fällen werden Variablen innerhalb der Build-Umgebung als Umgebungsvariable bereitgestellt, die in der `pom.xml`-Datei oder anderen Build-Skripten referenziert werden kann.

### Benennungskonventionen für Pipeline-Variablen {#naming-conventions}

Variablennamen müssen die folgenden Konventionen einhalten:

* Variablen dürfen nur alphanumerische Zeichen und den Unterstrich (`_`) enthalten.
* Die Namen sollten in Großbuchstaben geschrieben sein.
* Pro Pipeline sind maximal 200 Variablen zulässig.
* Jeder Name darf maximal 100 Zeichen lang sein.
* Jede `string`-Variable darf höchstens 2047 Zeichen enthalten.
* Jede Variable des Typs `secretString` darf maximal 500 Zeichen enthalten.

## Über die Benutzeroberfläche von Cloud Manager {#ui}

Pipeline-Variablen können über die Cloud Manager-Benutzeroberfläche konfiguriert und verwaltet werden. Sie müssen über die Berechtigungen zum Bearbeiten der Pipeline verfügen, um Pipeline-Variablen hinzuzufügen, zu bearbeiten und zu löschen.

Wenn eine Pipeline ausgeführt wird, wird die Variablenverwaltung blockiert.

### Pipeline-Variablen hinzufügen {#add-ui}

1. Klicken Sie beim Verwalten Ihrer Pipelines ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) auf die Suchschaltfläche der Pipeline, für die Sie Pipeline-Variablen erstellen möchten, und wählen Sie **Variablen anzeigen/bearbeiten** aus dem Kontextmenü aus.[

   ![Pipeline-Variablen anzeigen/bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Das Fenster **Variablenkonfiguration** wird geöffnet. Geben Sie die Variablendetails in die erste Zeile der Tabelle ein und klicken Sie auf **Hinzufügen**.

   * **Konfigurationsname** ist eine eindeutige Kennung für Ihre Variable, die die [Namenskonventionen für Pipeline-Variablen befolgen muss](#naming-conventions).
   * **Wert** ist der Wert, den die Variable enthält.
   * **Angewandter Schritt** ist der Schritt in der Pipeline, für den die Variable gilt. Dieser Schritt ist erforderlich.
      * **Build**
      * **Funktionsprüfung**
      * **UI-Tests**
   * **Typ** definiert, ob es sich bei der Variablen um reinen Text handelt oder ob sie als geheim verschlüsselt wurde.

   ![Variable hinzufügen](/help/implementing/cloud-manager/assets/pipeline-variables-add-variable.png)

1. Wird der Tabelle hinzugefügt. Fügen Sie weitere Variablen nach Bedarf hinzu und tippen oder klicken Sie dann auf **Speichern**, um die Variablen zu speichern, die Sie der Pipeline hinzugefügt haben.

### Bearbeiten von Pipeline-Variablen {#edit-ui}

1. Klicken Sie beim Verwalten Ihrer Pipelines ](/help/implementing/cloud-manager/configuring-pipelines/managing-pipelines.md) auf die Suchschaltfläche der Pipeline, für die Sie Pipeline-Variablen erstellen möchten, und wählen Sie **Variablen anzeigen/bearbeiten** aus dem Kontextmenü aus.[

   ![Pipeline-Variablen anzeigen/bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-view-edit.png)

1. Das Fenster **Variablenkonfiguration** wird geöffnet. Klicken Sie auf die Suchschaltfläche der zu bearbeitenden Variable und wählen Sie **Bearbeiten** aus.

   ![Variable bearbeiten](/help/implementing/cloud-manager/assets/pipeline-variables-edit.png)

1. Aktualisieren Sie den Wert der Variablen nach Bedarf und klicken Sie auf **Anwenden** (das Häkchen am Ende der Zeile), um die Änderung anzuwenden, oder auf **Verwerfen** (den Rückwärtspfeil), um die Änderung wiederherzustellen.

   * Nur der Wert der Variablen kann bearbeitet werden.

   ![Bearbeiten einer Variable](/help/implementing/cloud-manager/assets/pipeline-variables-edit-save.png)

1. Klicken Sie auf **Speichern**.

Wenn Sie eine Variable löschen möchten, wählen Sie im Fenster **Variablenkonfiguration** im Suchmenü der Pipeline-Variablen die Option **Löschen** anstelle von **Bearbeiten** aus.

## Cloud Manager-CLI verwenden {#cli}

Dieser CLI-Befehl legt eine Variable fest.

```shell
$ aio cloudmanager:set-pipeline-variables PIPELINEID --variable MY_CUSTOM_VARIABLE test
```

Dieser Befehl listet Variablen auf.

```shell
$ aio cloudmanager:list-pipeline-variables PIPELINEID
```

Bei Verwendung in einer Maven-Datei `pom.xml` ist es in der Regel hilfreich, diese Variablen Maven-Eigenschaften mithilfe einer ähnlichen Syntax wie dieser zuzuordnen.

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
