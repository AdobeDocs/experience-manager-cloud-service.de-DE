---
title: Konfigurieren von Nicht-Produktions-Pipelines
description: Erfahren Sie, wie Sie produktionsfremde Pipelines konfigurieren, um die Qualität Ihres Codes zu testen, bevor Sie ihn in Produktionsumgebungen bereitstellen.
index: true
source-git-commit: 536740f8bb5e54a3a831a22f4e6d237863aea324
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 8%

---


# Konfigurieren von Nicht-Produktions-Pipelines {#configuring-non-production-pipelines}

Erfahren Sie, wie Sie produktionsfremde Pipelines konfigurieren, um die Qualität Ihres Codes zu testen, bevor Sie ihn in Produktionsumgebungen bereitstellen.

## Produktionsfremde Pipelines {#non-production-pipelines}

Zusätzlich zu [Produktions-Pipelines](#configuring-production-pipelines.md) , die in Staging- und Produktionsumgebungen bereitgestellt wird, können Sie auch produktionsfremde Pipelines zur Validierung Ihres Codes einrichten.

Es gibt zwei Arten von produktionsfremden Pipelines:

* **Code-Qualitäts-Pipelines** - Diese führen Code-Qualitätsprüfungen für den Code in einer Git-Verzweigung durch und führen die Build- und Codequalitätsschritte aus.
* **Implementierungs-Pipelines** - Neben der Ausführung der Build- und Codequalitätsschritte wie der Code-Qualitäts-Pipelines stellen diese Pipelines den Code in einer Nicht-Produktionsumgebung bereit.

>[!NOTE]
>
>Sie können [Pipeline-Einstellungen bearbeiten](managing-pipelines.md) nach der Ersteinrichtung.

## Hinzufügen einer neuen produktionsfremden Pipeline {#adding-non-production-pipeline}

Nachdem Sie Ihr Programm eingerichtet haben und über mindestens eine Umgebung mit der Cloud Manager-Benutzeroberfläche verfügen, können Sie eine produktionsfremde Pipeline hinzufügen, indem Sie diese Schritte ausführen.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte **Pipelines** über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **+Hinzufügen** und wählen Sie **Hinzufügen einer produktionsfremden Pipeline** aus.

   ![Nicht-Produktions-Pipeline hinzufügen](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Im **Konfiguration** des **Hinzufügen einer produktionsfremden Pipeline** auswählen Sie den Typ der produktionsfremden Pipeline, die Sie hinzufügen möchten, entweder **Code-Qualitäts-Pipeline** oder **Bereitstellungs-Pipeline**.

   ![Dialogfeld &quot;Nicht-Produktions-Pipeline hinzufügen&quot;](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Bereitstellung einer **Name der produktionsfremden Pipeline** , um Ihre Pipeline zusammen mit den folgenden zusätzlichen Informationen zu identifizieren.

   * **Deployment Trigger** - Sie haben beim Definieren der Bereitstellungs-Trigger zum Starten der Pipeline die folgenden Optionen.

      * **Manuell** - Verwenden Sie diese Option, um die Pipeline manuell zu starten.
      * **Bei Git-Änderungen** - Diese Optionen starten die CI/CD-Pipeline, sobald der konfigurierten Git-Verzweigung Commits hinzugefügt werden. Mit dieser Option können Sie die Pipeline nach Bedarf weiterhin manuell starten.
   * **Verhalten bei wichtigen Metrikfehlern** - Während der Einrichtung oder Bearbeitung der Pipeline wird die **Bereitstellungsmanager** hat die Möglichkeit, das Verhalten der Pipeline zu definieren, wenn ein wichtiger Fehler in einem der Quality Gates auftritt. Sie haben folgende Optionen.

      * **Jedes Mal fragen** - Dies ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
      * **Sofort scheitern** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
      * **Sofort fortfahren** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.


1. Klicken Sie auf **Weiter**.

1. Im **Quellcode** des **Hinzufügen einer produktionsfremden Pipeline** auswählen, müssen Sie festlegen, welcher Code von der Pipeline verarbeitet werden soll.

   * **[Code für das Frontend](#front-end-code)**
   * **[Full-Stack-Code](#full-stack-code)**
   * **[Web-Stufen-Konfiguration](#web-tier-config)**

Die Schritte zum Erstellen Ihrer produktionsfremden Pipeline variieren je nach der Option für **Quellcode** ausgewählt haben. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

### Code für das Frontend {#front-end-code}

Eine Frontend-Code-Pipeline stellt Frontend-Code-Builds bereit, die eine oder mehrere clientseitige Benutzeroberflächenanwendungen enthalten. Siehe Dokument . [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) für weitere Informationen zu diesem Pipelinetyp.

Führen Sie die folgenden Schritte aus, um die Konfiguration der Front-End-Code-Nicht-Produktions-Pipeline abzuschließen.

1. Im **Quellcode** definieren, müssen Sie die folgenden Optionen definieren.

   * **Förderfähige Bereitstellungsumgebungen** - Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, in welchen Umgebungen sie bereitgestellt werden soll.
   * **Repository** - Diese Option definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Siehe Dokument . [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
   * **Code-Speicherort** - Diese Option definiert den Pfad im Zweig des ausgewählten Repositorys, aus dem die Pipeline den Code abrufen soll.

   ![Front-End-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-front-end.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und Sie können jetzt [Pipelines verwalten](managing-pipelines.md) auf **Pipelines** auf der Karte **Programmübersicht** Seite.

### Full-Stack-Code {#full-stack-code}

Eine vollständige Codepipeline stellt gleichzeitig Back-End- und Front-End-Code-Builds bereit, die eine oder mehrere AEM Serveranwendungen zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten. Siehe Dokument . [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline) für weitere Informationen zu diesem Pipelinetyp.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung bereits eine vollständige Codepipeline vorhanden ist, wird diese Auswahl deaktiviert.

Führen Sie die folgenden Schritte aus, um die Konfiguration der Nicht-Produktions-Pipeline für den Vollstapelcode abzuschließen.

1. Im **Quellcode** definieren, müssen Sie die folgenden Optionen definieren.

   * **Förderfähige Bereitstellungsumgebungen** - Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, in welchen Umgebungen sie bereitgestellt werden soll.
   * **Repository** - Diese Optionen definieren, aus welchem Git-Repo die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Siehe Dokument . [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
   * **Konfiguration der Web-Stufe ignorieren** -

   ![Vollstack-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und Sie können jetzt [Pipelines verwalten](managing-pipelines.md) auf **Pipelines** auf der Karte **Programmübersicht** Seite.

### Web-Stufen-Konfiguration {#web-tier-config}

Eine Web-Ebene-Konfigurationspipeline stellt HTTPD-/Dispatcher-Konfigurationen bereit. Siehe Dokument . [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) für weitere Informationen zu diesem Pipelinetyp.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung bereits eine Code-Pipeline der Webstufe vorhanden ist, wird diese Auswahl deaktiviert.

Führen Sie die folgenden Schritte aus, um die Konfiguration der Nicht-Produktions-Pipeline für den Vollstapelcode abzuschließen.

1. Im **Quellcode** definieren, müssen Sie die folgenden Optionen definieren.

   * **Förderfähige Bereitstellungsumgebungen** - Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, in welchen Umgebungen sie bereitgestellt werden soll.
   * **Repository** - Diese Option definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Siehe Dokument . [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
   * **Code-Speicherort** - Diese Option definiert den Pfad im Zweig des ausgewählten Repositorys, aus dem die Pipeline den Code abrufen soll.
      * Bei Web-Tier-Konfigurationspipelines ist dies normalerweise der Pfad, der Folgendes enthält `conf.d`, `conf.dispatcher.d`und `opt-in` Verzeichnissen.
      * Wenn die Projektstruktur beispielsweise aus dem [AEM Projektarchetyp,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) der Pfad `/dispatcher/src`.

   ![Web-Tier-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-web-tier.png)

1. Klicken Sie auf **Speichern**.

>[!NOTE]
>
>Wenn Sie über eine vorhandene Vollstapel-Pipeline verfügen, die in einer Umgebung bereitgestellt wird, wird beim Erstellen einer Web-Tier-Konfigurationspipeline für dieselbe Umgebung die vorhandene Web-Tier-Konfiguration in der Vollstapel-Pipeline ignoriert.

Die Pipeline wird gespeichert und Sie können jetzt [Pipelines verwalten](managing-pipelines.md) auf **Pipelines** auf der Karte **Programmübersicht** Seite.

## Dispatcher-Pakete überspringen {#skip-dispatcher-packages}

Wenn Sie möchten, dass Dispatcher-Pakete als Teil Ihrer Pipeline erstellt werden, sie aber nicht als Buildspeicher veröffentlicht werden sollen, können Sie die Veröffentlichung deaktivieren, was die Laufzeit der Pipeline verkürzen kann.

Die folgende Konfiguration zum Deaktivieren von Publishing-Dispatcher-Paketen muss über Ihr Projekt hinzugefügt werden `pom.xml` -Datei. Sie basiert auf einer Umgebungsvariablen, die als Markierung dient, die Sie im Cloud Manager-Build-Container festlegen können, um zu definieren, wann Dispatcher-Pakete ignoriert werden sollen.

```xml
<profile>
  <id>only-include-dispatcher-when-it-isnt-ignored</id>
  <activation>
    <property>
      <name>env.IGNORE_DISPATCHER_PACKAGES</name>
      <value>!true</value>
    </property>
  </activation>
  <modules>
    <module>dispatcher</module>
  </modules>
</profile>
```
