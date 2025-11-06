---
title: Hinzufügen einer Produktions-Pipeline
description: Erfahren Sie, wie Sie eine Produktions-Pipeline hinzufügen, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1402'
ht-degree: 87%

---


# Hinzufügen einer Produktions-Pipeline {#configure-production-pipeline}

Erfahren Sie, wie Sie Produktions-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen. Eine Produktions-Pipeline stellt Code zuerst in der Staging-Umgebung bereit. Nach der Genehmigung wird derselbe Code in der Produktionsumgebung bereitgestellt.

Benutzende müssen über die Rolle **[Bereitstellungs-Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** verfügen, um Produktions-Pipelines konfigurieren zu können.

>[!NOTE]
>
>Eine Produktions-Pipeline kann erst eingerichtet werden, wenn Folgendes gegeben ist:
>
>* Das Programm ist erstellt. 
>* Das Git-Repository hat mindestens eine Verzweigung.
>* Die Produktions- und Staging-Umgebungen sind erstellt.

Konfigurieren Sie Ihre Pipeline-Einstellungen über [!UICONTROL Cloud Manager], bevor Sie Code bereitstellen.

>[!NOTE]
>
>Nach der Ersteinrichtung können Sie die [Pipeline-Einstellungen bearbeiten](managing-pipelines.md).

## Hinzufügen einer neuen Produktions-Pipeline {#adding-production-pipeline}

Nachdem Sie Ihr Programm eingerichtet haben und über mindestens eine Umgebung mit der Benutzeroberfläche von [!UICONTROL Cloud Manager] verfügen, können Sie eine Produktions-Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

>[!TIP]
>
>Bevor Sie eine Frontend-Pipeline konfigurieren, lesen Sie die [Tour zur schnellen AEM-Site-Erstellung](/help/journey-sites/quick-site/overview.md). Dort finden Sie eine vollständige Anleitung für das benutzerfreundliche Tool zur schnellen AEM-Site-Erstellung. Diese Tour hilft Ihnen, die Frontend-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site ohne AEM-Backend-Kenntnisse schnell anzupassen.

1. Melden Sie sich unter [experiece.adobe.com](https://experience.adobe.com) bei Cloud Manager an.
1. Klicken Sie **Abschnitt „Schnellzugriff** auf **Experience Manager**.
1. Klicken Sie im linken Panel auf **Cloud Manager**.
1. Wählen Sie die gewünschte Organisation aus.
1. Klicken Sie in **Konsole** Meine Programme“ auf ein Programm.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Gehen Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf **Hinzufügen** und wählen Sie dann **Produktions-Pipeline hinzufügen** aus.

   ![Die Karte „Pipelines“ im Programm-Manager – Überblick](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** erscheint. Geben Sie einen **Pipeline-Name** an, um Ihre Pipeline zu identifizieren, sowie die folgenden Optionen. Klicken Sie auf **Weiter**.

   **Bereitstellungsauslöser**: Beim Definieren der Bereitstellungsauslöser für den Start der Pipeline haben Sie die folgenden Optionen.

   * **Manuell**: Mit dieser Option wird die Pipeline manuell gestartet.
   * **Bei Git-Änderungen**: Mit dieser Option wird die CI/CD-Pipeline gestartet, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

   **Verhalten bei bedeutenden Metrikfehlern**: Bei der Einrichtung oder Bearbeitung der Pipeline kann der **Bereitstellungs-Manager** festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Folgende Optionen sind verfügbar:

   * **Jedes Mal fragen**: Dies ist die Standardeinstellung, die ein manuelles Eingreifen bei jedem bedeutenden Fehler verlangt.
   * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler abgebrochen. Damit wird im Grunde eine Person simuliert, die manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler automatisch fortgesetzt. Damit wird im Grunde eine Person simuliert, die manuell jeden Fehler quittiert.

   ![Konfiguration der Produktions-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Legen Sie auf der Registerkarte **Quell-Code** fest, welche Art von Code von der Pipeline verarbeitet werden soll.

   * **[Konfigurieren einer Full-Stack-Pipeline](#full-stack-code)**
   * **[Konfigurieren einer zielgerichteten Bereitstellungs-Pipeline](#targeted-deployment)**

Weitere Informationen zu diesem Pipeline-Typ finden Sie unter [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

Die Schritte zum Abschluss der Erstellung Ihrer Produktions-Pipeline variieren je nach dem von Ihnen gewählten Typ von Quell-Code. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

### Konfigurieren einer Full-Stack-Code-Pipeline {#full-stack-code}

Eine Pipeline mit Full-Stack-Code stellt gleichzeitig Backend- und Frontend-Code-Builds bereit, die ein oder mehrere AEM-Server-Programme zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung bereits eine Pipeline mit Full-Stack-Code vorhanden ist, wird diese Auswahl deaktiviert.

**So konfigurieren Sie eine Full-Stack-Code-Pipeline:**

1. Definieren Sie auf der Registerkarte **Quell-Code** die folgenden Optionen:

   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

   * **Git-Verzweigung**: Diese Option legt fest, von welcher Verzweigung die ausgewählte Pipeline den Code abrufen soll.
Wenn Sie die ersten Zeichen des Verzweigungsnamens eingeben, findet die Funktion zum automatischen Vervollständigen dieses Feldes die entsprechenden Verzweigungen, um Ihnen bei der Auswahl zu helfen.
   * **Konfiguration der Web-Stufe ignorieren**: Wenn diese Option aktiviert ist, stellt die Pipeline Ihre Web-Stufenkonfiguration nicht bereit.
   * **Vor Bereitstellung in Produktion pausieren**: Setzt die Pipeline vor der Bereitstellung in der Produktion aus.
   * **Geplant**: Ermöglicht Benutzenden die Aktivierung der geplanten Produktionsbereitstellung.

   ![Full-Stack-Code](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Klicken Sie auf **Weiter**, um zur Registerkarte **Erlebnis-Audit** zu gelangen, auf der Sie die Pfade definieren können, die immer in das Erlebnis-Audit einbezogen werden sollen.

   ![Hinzufügen des Erlebnis-Audits](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Geben Sie Pfade an, die in das Erlebnis-Audit aufgenommen werden sollen.

   * Einzelheiten hierzu finden Sie unter [Erlebnis-Audit-Tests](/help/implementing/cloud-manager/reports/report-experience-audit.md#configuration).

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

Bei Ausführung der Pipeline werden für Erlebnis-Audit konfigurierte Pfade basierend auf Leistungs-, Zugänglichkeits-, SEO-, Best Practices- und PWA-Tests gesendet und ausgewertet. Weitere Einzelheiten finden Sie unter [Grundlegendes zu den Ergebnissen eines Erlebnis-Audits](/help/implementing/cloud-manager/reports/report-experience-audit.md).

Die Pipeline wird gespeichert, und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

### Konfigurieren einer zielgerichteten Bereitstellungs-Pipeline {#targeted-deployment}

Bei einer zielgerichteten Bereitstellung wird Code nur für ausgewählte Teile Ihrer AEM-Anwendung bereitgestellt. In einer solchen Bereitstellung können Sie sich dazu entscheiden, einen der folgenden Code-Typen **einzuschließen**:

* **Konfig**: Konfigurieren Sie Einstellungen für verschiedene Funktionen in Ihrer AEM-Umgebung.
   * Unter [Verwenden von Konfigurations](/help/operations/config-pipeline.md)Pipelines“ finden Sie eine Liste der unterstützten Konfigurationen, darunter Protokollweiterleitung, Bereinigungsaufgaben und verschiedene CDN-Konfigurationen. Außerdem erfahren Sie, wie Sie diese in Ihrem Repository verwalten, damit sie ordnungsgemäß bereitgestellt werden.
   * Beim Ausführen einer zielgerichteten Bereitstellungs-Pipeline werden Konfigurationen bereitgestellt, sofern sie in der Umgebung, dem Repository und der Verzweigung gespeichert sind, die in der Pipeline definiert sind.
   * Es kann immer nur eine Konfigurations-Pipeline pro Umgebung geben.
* **Konfigurieren der Edge Delivery Services-Konfigurations**-Pipeline: Edge Delivery-Konfigurations-Pipelines verfügen über keine separaten Entwicklungs-, Staging- und Produktionsumgebungen. In AEM as a Cloud Service durchlaufen die Änderungen Entwicklungs-, Staging- und Produktionsebenen. Eine Edge Delivery-Konfigurations-Pipeline wendet ihre Konfiguration dagegen direkt auf alle in Cloud Manager registrierten Edge Delivery Sites-Domains an. Weitere Informationen finden Sie unter [Hinzufügen einer Edge Delivery-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).
* **Frontend-Code** – Konfigurieren Sie JavaScript und CSS für das Frontend Ihrer AEM-Anwendung.
   * Mit Frontend-Pipelines erhalten Frontend-Entwickelnde mehr Unabhängigkeit, und der Entwicklungsprozess kann beschleunigt werden.
   * Weitere Informationen dazu, wie dieser Prozess abläuft und was dabei zu beachten ist, um das volle Potenzial dieses Prozesses auszuschöpfen, finden Sie im Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
* **Web-Stufen-Konfiguration**: Konfigurieren Sie die Dispatcher-Eigenschaften zum Speichern, Verarbeiten und Bereitstellen von Web-Seiten für den Client.
   * Weitere Informationen finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines).
   * Wenn für die ausgewählte Umgebung bereits eine Code-Pipeline auf Web-Ebene vorhanden ist, wird diese Auswahl deaktiviert.
   * Wenn Sie eine Konfigurations-Pipeline auf Web-Ebene für eine Umgebung mit einer vorhandenen Full-Stack-Pipeline erstellen, wird die Konfiguration auf Web-Ebene in der Full-Stack-Pipeline ignoriert. Diese Änderung betrifft nur die Web-Stufen-Konfiguration in dieser Umgebung.

>[!NOTE]
>
>Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt. Details sowie eine vollständige Liste der Einschränkungen finden Sie unter [Hinzufügen von privaten Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md).

**Konfigurieren einer zielgerichteten Bereitstellungs-Pipeline:**

1. Wählen Sie den benötigten Bereitstellungstyp aus.

![Zielgerichtete Bereitstellungsoptionen](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-targeted-deployment.png)

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
   * **Anhalten vor der Bereitstellung in der Produktion**: Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.
   * **Geplant**: Ermöglicht Benutzenden die Aktivierung der geplanten Produktionsbereitstellung. Nur für Web-Stufen-spezifische Bereitstellungen verfügbar.

   ![Konfigurations-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert, und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

## Überspringen von Dispatcher-Paketen {#skip-dispatcher-packages}

Um Dispatcher-Pakete in Ihrer Pipeline zu erstellen, ohne sie für den Build-Speicher zu veröffentlichen, können Sie die Veröffentlichungsoption deaktivieren. Dies kann dazu beitragen, die Laufzeit der Pipeline zu verkürzen.

Die folgende Konfiguration zum Deaktivieren von Veröffentlichungs-Dispatcher-Paketen muss über die Datei `pom.xml` Ihres Projekts hinzugefügt werden. Eine Umgebungsvariable dient als Flag, das Sie im Cloud Manager-Build-Container festlegen, um festzulegen, wann Dispatcher-Pakete ignoriert werden sollen.

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
