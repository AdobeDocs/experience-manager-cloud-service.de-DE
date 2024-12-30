---
title: Hinzufügen einer produktionsfremden Pipeline
description: Erfahren Sie, wie Sie eine produktionsfremde Pipeline hinzufügen, um die Qualität des Codes vor seiner Bereitstellung in Produktionsumgebungen zu testen.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 40a76e39750d6dbeb03c43c8b68cddaf515a2614
workflow-type: tm+mt
source-wordcount: '1398'
ht-degree: 100%

---


# Hinzufügen einer produktionsfremden Pipeline {#configuring-non-production-pipelines}

Erfahren Sie, wie Sie produktionsfremde Pipelines so konfigurieren, dass die Qualität des Codes vor seiner Bereitstellung in Produktionsumgebungen getestet wird.

Benutzende müssen über die Rolle **[Bereitstellungs-Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** verfügen, um produktionsfremde Pipelines konfigurieren zu können.

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

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Rufen Sie die Karte **Pipelines** über den Startbildschirm von Cloud Manager auf. Klicken Sie auf **+Hinzufügen** und wählen Sie **Produktionsfremde Pipeline hinzufügen** aus.

   ![Produktionsfremde Pipeline hinzufügen](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Wählen Sie im Dialogfeld **Hinzufügen einer produktionsfremden Pipeline** auf der Registerkarte **Konfiguration** den Typ der produktionsfremden Pipeline aus, die Sie hinzufügen möchten.

   * **Code-Qualitäts-Pipeline** – Erstellen Sie eine Pipeline, die Ihren Code erstellt, Komponententests durchführt und die Code-Qualität auswertet, aber NICHT implementiert.
   * **Implementierungs-Pipeline** – Erstellen Sie eine Pipeline, die Ihren Code erstellt, Komponententests durchführt, die Code-Qualität auswertet und in einer Umgebung implementiert.

   ![Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Geben Sie einen **Namen für die produktionsfremde Pipeline** an, um Ihre Pipeline zu identifizieren, sowie die folgenden zusätzlichen Informationen.

   * **Bereitstellungsauslöser**: Beim Definieren der Bereitstellungsauslöser für den Start der Pipeline haben Sie die folgenden Optionen.

      * **Manuell**: Verwenden Sie diese Option, um die Pipeline manuell zu starten.
      * **Bei Git-Änderungen**: Diese Option startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

1. Wenn Sie eine **Bereitstellungs-Pipeline** erstellen möchten, müssen Sie auch das **Verhalten bei bedeutenden Metrikfehlern** definieren.

   * **Jedes Mal fragen**: Dieses Verhalten ist die Standardeinstellung und erfordert ein manuelles Eingreifen bei einem bedeutenden Fehler.
   * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler abgebrochen. Damit werden im Grunde Benutzende simuliert, die manuell jeden Fehler ablehnen.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler automatisch fortgesetzt. Damit werden im Grunde Benutzende simuliert, die manuell jeden Fehler genehmigen.

1. Klicken Sie auf **Weiter**.

1. Auf der Registerkarte **Quell-Code** im Dialogfeld **Produktionsfremde Pipeline hinzufügen** müssen Sie auswählen, welche Art von Code die Pipeline verarbeiten soll.

   * **[Full-Stack-Code](#full-stack-code)**
   * **[Zielgerichtete Bereitstellung](#targeted-deployment)**

Weitere Informationen zu den Pipeline-Typen finden Sie unter [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

Die Schritte zum Abschluss der Erstellung Ihrer produktionsfremden Pipeline variieren entsprechend der von Ihnen gewählten Option für den Quell-Code. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

### Full-Stack-Code {#full-stack-code}

Eine Pipeline mit Full-Stack-Code stellt gleichzeitig Backend- und Frontend-Code-Builds bereit, die ein oder mehrere AEM-Server-Programme zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung bereits eine Pipeline mit Full-Stack-Code vorhanden ist, wird diese Auswahl deaktiviert.

Führen Sie die folgenden Schritte aus, um die Konfiguration der produktionsfremden Full-Stack-Code-Pipeline abzuschließen.

1. In der Registerkarte **Quell-Code** müssen Sie die folgenden Optionen definieren.

   * **Berechtigte Bereitstellungsumgebungen**: Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, in welche Umgebungen sie bereitstellen soll.
   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens und die Funktion zur automatischen Vervollständigung dieses Felds ein. Dies hilft Ihnen, die entsprechenden auswählbaren Verzweigungen zu suchen.
   * **Konfiguration der Web-Stufe ignorieren**: Wenn diese Option aktiviert ist, stellt die Pipeline Ihre Web-Stufenkonfiguration nicht bereit.
   * **Pipeline**: Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, können Sie eine Testphase ausführen. Aktivieren Sie die Optionen, die Sie in dieser Phase aktivieren möchten. Wenn keine der Optionen ausgewählt ist, wird die Testphase während der Pipeline-Ausführung nicht angezeigt.

      * **Funktionstests für das Produkt** – Führen Sie [Produktfunktionstests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) mit der Entwicklungsumgebung durch.
      * **Benutzerdefinierte Funktionstests** – Führen Sie [benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) gegen die Entwicklungsumgebung durch.
      * **Benutzerdefinierte UI-Tests** – Führen Sie [benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/ui-testing.md) für benutzerdefinierte Anwendungen aus.
      * **Erlebnisprüfung** – Ausführen einer [Erlebnisprüfung](/help/implementing/cloud-manager/experience-audit-dashboard.md)

   ![Full-Stack-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

### Zielgerichtete Bereitstellung {#targeted-deployment}

Bei einer zielgerichteten Bereitstellung wird Code nur für ausgewählte Teile Ihrer AEM-Anwendung bereitgestellt. In einer solchen Bereitstellung können Sie auswählen, einen der folgenden Code-Typen **einzuschließen**:

* **Konfiguration** – Konfigurieren Sie Einstellungen für verschiedene Funktionen in Ihrer AEM-Umgebung.
   * Eine Liste der unterstützten Konfigurationen, einschließlich Protokollweiterleitung, bereinigungsbezogener Wartungsaufgaben und verschiedener CDN-Konfigurationen, sowie Informationen zu deren ordnungsgemäßer Bereitstellung im Repository finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md).
   * Wenn Sie eine gezielte Bereitstellungs-Pipeline ausführen, werden Konfigurationen bereitgestellt, sofern sie in der Umgebung, dem Repository und der Verzweigung gespeichert sind, die Sie in der Pipeline definiert haben.
   * Es kann immer nur eine Konfigurations-Pipeline pro Umgebung geben.
* **Frontend-Code** – Konfigurieren Sie JavaScript und CSS für das Frontend Ihrer AEM-Anwendung.
   * Mit Frontend-Pipelines erhalten Frontend-Entwickelnde mehr Unabhängigkeit, und der Entwicklungsprozess kann beschleunigt werden.
   * Weitere Informationen dazu, wie dieser Prozess abläuft und was dabei zu beachten ist, um das volle Potenzial dieses Prozesses auszuschöpfen, finden Sie im Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
* **Web-Stufen-Konfiguration** – Konfigurieren Sie die Dispatcher-Eigenschaften zum Speichern, Verarbeiten und Bereitstellen von Web-Seiten für den Client.
   * Weitere Informationen finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines).
   * Wenn für die ausgewählte Umgebung bereits eine Code-Pipeline auf Web-Ebene vorhanden ist, wird diese Auswahl deaktiviert.
   * Wenn Sie über eine vorhandene Full-Stack-Pipeline verfügen, die in einer Umgebung bereitgestellt wird, wird beim Erstellen einer Web-Stufen-Konfigurations-Pipeline für dieselbe Umgebung die vorhandene Web-Stufen-Konfiguration in der Full-Stack-Pipeline ignoriert.

>[!NOTE]
>
>Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt. Details sowie eine vollständige Liste der Einschränkungen finden Sie unter [Hinzufügen von privaten Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md).

Die Schritte zum Fertigstellen Ihrer produktionsfremden zielgerichteten Bereitstellungs-Pipeline sind dieselben, wenn Sie einen Bereitstellungstyp auswählen.

1. Wählen Sie den benötigten Bereitstellungstyp aus.

![Zielgerichtete Bereitstellungsoptionen](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment.png)

1. Definieren Sie die **geeigneten Bereitstellungsumgebungen**.

   * Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, für welche Umgebungen sie etwas bereitstellen soll.

1. Definieren Sie unter **Quell-Code** die folgenden Optionen:

   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens und die Funktion zur automatischen Vervollständigung dieses Felds ein. Es werden die entsprechenden auswählbaren Verzweigungen gesucht.
   * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.
   * **Pipeline**: Bei produktionsfremden Frontend-Pipelines haben Sie die Möglichkeit, das **[Erlebnis-Audit](/help/implementing/cloud-manager/experience-audit-dashboard.md)** zu aktivieren.

   ![Konfigurations-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config-deployment-experience-audit.png)

1. Wenn Sie das Erlebnis-Audit aktiviert haben, klicken Sie auf **Weiter**, um zur Registerkarte **Erlebnis-Audit** zu gelangen. Dort können Sie die Pfade definieren, die immer in das Erlebnis-Audit einbezogen werden sollen.

   * Wenn Sie **Erlebnis-Audit** aktiviert haben, finden Sie im Dokument [Erlebnis-Audit](/help/implementing/cloud-manager/experience-audit-dashboard.md) Details zur Konfiguration.
   * Wenn nicht, überspringen Sie diesen Schritt.

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

Die Pipeline wird gespeichert, und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

## Überspringen von Dispatcher-Paketen {#skip-dispatcher-packages}

Wenn Sie möchten, dass Dispatcher-Pakete als Teil Ihrer Pipeline erstellt werden, sie aber nicht im Build-Speicher veröffentlicht werden sollen, können Sie die Veröffentlichung deaktivieren, was die Laufzeit der Pipeline verkürzen kann.

Die folgende Konfiguration zum Deaktivieren von Veröffentlichungs-Dispatcher-Paketen muss über die `pom.xml`-Datei Ihres Projekts hinzugefügt werden. Sie basiert auf einer Umgebungsvariablen, die als Markierung dient, welche Sie im Cloud Manager-Build-Container festlegen können, um zu definieren, wann Dispatcher-Pakete ignoriert werden sollen.

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
