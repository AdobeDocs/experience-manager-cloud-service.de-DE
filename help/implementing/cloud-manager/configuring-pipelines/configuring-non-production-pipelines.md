---
title: Konfigurieren von produktionsfremden Pipelines
description: Erfahren Sie, wie Sie produktionsfremde Pipelines konfigurieren, um die Qualität Ihres Codes zu testen, bevor Sie ihn in Produktionsumgebungen bereitstellen.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '1356'
ht-degree: 57%

---


# Konfigurieren von produktionsfremden Pipelines {#configuring-non-production-pipelines}

Erfahren Sie, wie Sie produktionsfremde Pipelines konfigurieren, um die Qualität Ihres Codes zu testen, bevor Sie ihn in Produktionsumgebungen bereitstellen.

## Produktionsfremde Pipelines {#non-production-pipelines}

Zusätzlich zu [Produktions-Pipelines](#configuring-production-pipelines.md), die in Staging- und Produktionsumgebungen bereitstellen, können Sie auch produktionsfremde Pipelines zur Validierung Ihres Codes einrichten.

Es gibt zwei Arten von produktionsfremden Pipelines:

* **Code-Qualitäts-Pipelines**: Diese Pipelines führen Code-Qualitätsprüfungen für den Code in einer Git-Verzweigung durch und sie führen die Build- und Code-Qualitätsschritte aus.
* **Bereitstellungs-Pipelines**: Diese Pipelines führen nicht nur wie die Code-Qualitäts-Pipelines die Build- und Code-Qualitätsschritte aus, sondern stellen den Code auch in einer produktionsfremden Umgebung bereit.

>[!NOTE]
>
>Nach der Ersteinrichtung können Sie [Pipeline-Einstellungen bearbeiten](managing-pipelines.md).

## Hinzufügen einer neuen produktionsfremden Pipeline {#adding-non-production-pipeline}

Sobald Sie mit der Benutzeroberfläche von Cloud Manager Ihr Programm eingerichtet und mindestens eine Umgebung haben, können Sie eine produktionsfremde Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Rufen Sie die Karte **Pipelines** über den Startbildschirm von Cloud Manager auf. Klicken **+Hinzufügen** und wählen Sie **Hinzufügen einer produktionsfremden Pipeline**.

   ![Produktionsfremde Pipeline hinzufügen](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Wählen Sie im Dialogfeld **Hinzufügen einer produktionsfremden Pipeline** auf der Registerkarte **Konfiguration** den Typ der produktionsfremden Pipeline aus, die Sie hinzufügen möchten.

   * **Code-Qualitäts-Pipeline** – Erstellen Sie eine Pipeline, die Ihren Code erstellt, Komponententests durchführt und die Code-Qualität auswertet, aber NICHT implementiert.
   * **Implementierungs-Pipeline** – Erstellen Sie eine Pipeline, die Ihren Code erstellt, Komponententests durchführt, die Code-Qualität auswertet und in einer Umgebung implementiert.

   ![Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Geben Sie einen **Namen für die produktionsfremde Pipeline** an, um Ihre Pipeline zu identifizieren, sowie die folgenden zusätzlichen Informationen.

   * **Bereitstellungsauslöser**: Beim Definieren der Bereitstellungsauslöser für den Start der Pipeline haben Sie die folgenden Optionen.

      * **Manuell**: Verwenden Sie diese Option, um die Pipeline manuell zu starten.
      * **Bei Git-Änderungen** - Diese Option startet die CI/CD-Pipeline, sobald der konfigurierten Git-Verzweigung Commits hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

1. Wenn Sie eine **Bereitstellungs-Pipeline**, müssen Sie auch die **Verhalten bei wichtigen Metrikfehlern**.

   * **Jedes Mal fragen** - Dieses Verhalten ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofort scheitern** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Im Grunde emuliert er einen Benutzer, der jeden Fehler manuell ablehnt.
   * **Sofort fortfahren** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler automatisch ausgeführt. Im Grunde emuliert er einen Benutzer, der manuell jeden Fehler genehmigt.

1. Klicken Sie auf **Weiter**.

1. Auf der Registerkarte **Quell-Code** im Dialogfeld **Produktionsfremde Pipeline hinzufügen** müssen Sie auswählen, welche Art von Code die Pipeline verarbeiten soll.

   * **[Front-End-Code](#front-end-code)**
   * **[Full-Stack-Code](#full-stack-code)**
   * **[Web-Stufen-Konfiguration](#web-tier-config)**

Die Schritte zum Abschluss der Erstellung Ihrer produktionsfremden Pipeline variieren je nach der von Ihnen gewählten Option für den **Quell-Code**. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu gelangen, damit Sie die Konfiguration der Pipeline abschließen können.

### Front-End-Code {#front-end-code}

Eine Frontend-Code-Pipeline stellt Frontend-Code-Builds bereit, die eine oder mehrere Client-seitige Benutzeroberflächenanwendungen enthalten. Weitere Informationen zu dieser Art von Pipelines finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end).

Führen Sie die folgenden Schritte aus, um die Konfiguration der produktionsfremden Frontend-Code-Pipeline abzuschließen.

1. In der Registerkarte **Quell-Code** müssen Sie die folgenden Optionen definieren.

   * **Berechtigte Bereitstellungsumgebungen**: Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, in welche Umgebungen sie bereitstellen soll.
   * **Repository** - Diese Option definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Siehe [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) damit Sie lernen können, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Zweignamens und die Funktion zur automatischen Vervollständigung dieses Felds ein. Es werden die entsprechenden Verzweigungen gesucht, die Sie auswählen können.
   * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.

   ![Frontend-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-front-end.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und auf der Karte **Pipelines** auf der Seite **Programmübersicht** können Sie jetzt [Pipelines verwalten](managing-pipelines.md).

### Full-Stack-Code {#full-stack-code}

Eine Pipeline mit Full-Stack-Code stellt gleichzeitig Backend- und Frontend-Code-Builds bereit, die ein oder mehrere AEM-Server-Programme zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten. Weitere Informationen zu dieser Art von Pipelines finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline).

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung eine vollständige Codepipeline vorhanden ist, ist diese Auswahl deaktiviert.

Führen Sie die folgenden Schritte aus, um die Konfiguration der produktionsfremden Full-Stack-Code-Pipeline abzuschließen.

1. In der Registerkarte **Quell-Code** müssen Sie die folgenden Optionen definieren.

   * **Berechtigte Bereitstellungsumgebungen**: Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, in welche Umgebungen sie bereitstellen soll.
   * **Repository** - Diese Option definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Siehe [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) damit Sie lernen können, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Zweignamens und die Funktion zur automatischen Vervollständigung dieses Felds ein. Es hilft Ihnen, die passenden Verzweigungen zu finden, die Sie auswählen können.
   * **Konfiguration der Web-Ebene ignorieren** - Wenn diese Option aktiviert ist, stellt die Pipeline Ihre Webebenenkonfiguration nicht bereit.

   * **Pipeline** – Wenn es sich bei Ihrer Pipeline um eine Implementierungs-Pipeline handelt, können Sie eine Testphase ausführen. Überprüfen Sie die Optionen, die Sie in dieser Phase aktivieren möchten. Wenn keine der Optionen ausgewählt ist, wird die Testphase während der Pipeline-Ausführung nicht angezeigt.

      * **Funktionstests für das Produkt** – Führen Sie [Produktfunktionstests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) mit der Entwicklungsumgebung durch.
      * **Benutzerdefinierte Funktionstests** – Führen Sie [benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) gegen die Entwicklungsumgebung durch.
      * **Benutzerdefinierte UI-Tests** – Führen Sie [benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/ui-testing.md) für benutzerdefinierte Anwendungen aus.

   ![Full-Stack-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und auf der Karte **Pipelines** auf der Seite **Programmübersicht** können Sie jetzt [Pipelines verwalten](managing-pipelines.md).

### Web-Stufen-Konfiguration {#web-tier-config}

Eine Web-Tier-Konfigurationspipeline stellt HTTPD-/Dispatcher-Konfigurationen bereit. Siehe [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) für weitere Informationen zu diesem Pipelinetyp.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung eine Code-Pipeline auf Webebene vorhanden ist, ist diese Auswahl deaktiviert.

Führen Sie die folgenden Schritte aus, um die Konfiguration der produktionsfremden Web-Stufen-Konfigurations-Pipeline abzuschließen.

1. In der Registerkarte **Quell-Code** müssen Sie die folgenden Optionen definieren.

   * **Berechtigte Bereitstellungsumgebungen**: Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, in welche Umgebungen sie bereitstellen soll.
   * **Repository** - Diese Option definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Siehe [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) damit Sie lernen können, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
   * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.
      * Bei Web-Tier-Konfigurationspipelines enthält dieser Pfad normalerweise `conf.d`, `conf.dispatcher.d`und `opt-in` Verzeichnissen.
      * Wenn die Projektstruktur beispielsweise aus dem [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) generiert wurde, wäre der Pfad `/dispatcher/src`.

   ![Web-Stufen-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-web-tier.png)

1. Klicken Sie auf **Speichern**.

>[!NOTE]
>
>Wenn Sie über eine vorhandene Full-Stack-Pipeline verfügen, die in einer Umgebung bereitgestellt wird, wird beim Erstellen einer Web-Stufen-Konfigurations-Pipeline für dieselbe Umgebung die vorhandene Web-Stufen-Konfiguration in der Full-Stack-Pipeline ignoriert.

Die Pipeline wird gespeichert und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

## Entwickeln von Sites mit der Frontend-Pipeline {#developing-with-front-end-pipeline}

Mit Frontend-Pipelines erhalten Frontend-Entwicklern mehr Unabhängigkeit und der Entwicklungsprozess kann beschleunigt werden.

Siehe Dokument . [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md) , um zu erfahren, wie dieser Prozess funktioniert, und einige Überlegungen anzustellen, um das Potenzial dieses Prozesses voll auszuschöpfen.

## Überspringen von Dispatcher-Paketen {#skip-dispatcher-packages}

Wenn Sie möchten, dass Dispatcher-Pakete als Teil Ihrer Pipeline erstellt werden, sie aber nicht als Buildspeicher veröffentlicht werden sollen, können Sie die Veröffentlichung deaktivieren, was die Laufzeit der Pipeline verkürzen kann.

Die folgende Konfiguration zum Deaktivieren der Veröffentlichung von Dispatcher-Paketen muss über Ihr Projekt hinzugefügt werden `pom.xml` -Datei. Sie basiert auf einer Umgebungsvariablen, die als Markierung dient, die Sie im Cloud Manager-Build-Container festlegen können, um zu definieren, wann Dispatcher-Pakete ignoriert werden sollen.

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
