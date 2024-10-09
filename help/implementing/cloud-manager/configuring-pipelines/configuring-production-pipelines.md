---
title: Hinzufügen einer Produktions-Pipeline
description: Erfahren Sie, wie Sie eine Produktions-Pipeline hinzufügen, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 9cde6e63ec452161dbeb1e1bfb10c75f89e2692c
workflow-type: tm+mt
source-wordcount: '1314'
ht-degree: 57%

---


# Hinzufügen einer Produktions-Pipeline {#configure-production-pipeline}

Erfahren Sie, wie Sie Produktions-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen. Eine Produktions-Pipeline stellt Code zuerst in der Staging-Umgebung bereit. Bei der Genehmigung wird derselbe Code in der Produktionsumgebung bereitgestellt.

Benutzende müssen über die Rolle **[Bereitstellungs-Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** verfügen, um Produktions-Pipelines konfigurieren zu können.

>[!NOTE]
>
>Eine Produktions-Pipeline kann erst eingerichtet werden, wenn Folgendes passiert ist:
>
>* Das Programm wird erstellt.
>* Das Git-Repository hat mindestens eine Verzweigung.
>* Die Produktions- und Staging-Umgebungen werden erstellt.

Bevor Sie mit der Bereitstellung des Codes beginnen, konfigurieren Sie Ihre Pipeline-Einstellungen über [!UICONTROL Cloud Manager].

>[!NOTE]
>
>Nach der Ersteinrichtung können Sie [Pipeline-Einstellungen bearbeiten](managing-pipelines.md).

## Hinzufügen einer neuen Produktions-Pipeline {#adding-production-pipeline}

Sobald Sie mit der Benutzeroberfläche von [!UICONTROL Cloud Manager] Ihr Programm eingerichtet und mindestens eine Umgebung haben, können Sie eine Produktions-Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

>[!TIP]
>
>Bevor Sie eine Front-End-Pipeline konfigurieren, lesen Sie die [AEM Journey zur schnellen Site-Erstellung](/help/journey-sites/quick-site/overview.md) für eine durchgängige Anleitung durch das benutzerfreundliche AEM Tool zur schnellen Site-Erstellung . Diese Journey kann Ihnen dabei helfen, die Front-End-Entwicklung Ihrer AEM-Site zu optimieren, sodass Sie Ihre Site schnell und ohne AEM Backend-Kenntnisse anpassen können.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Gehen Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf **Hinzufügen** und wählen Sie dann **Produktions-Pipeline hinzufügen** aus.

   ![Die Karte „Pipelines“ im Programm-Manager – Überblick](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** erscheint. Geben Sie einen **Pipeline-Name** an, um Ihre Pipeline zu identifizieren, sowie die folgenden Optionen. Klicken Sie auf **Weiter**.

   **Bereitstellungsauslöser**: Beim Definieren der Bereitstellungsauslöser für den Start der Pipeline haben Sie die folgenden Optionen.

   * **Manuell** - Starten Sie die Pipeline manuell.
   * **Bei Git-Änderungen** - Startet die CI/CD-Pipeline, sobald der konfigurierten Git-Verzweigung Commits hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

   **Verhalten bei bedeutenden Metrikfehlern**: Bei der Einrichtung oder Bearbeitung der Pipeline kann der **Bereitstellungs-Manager** festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Folgende Optionen sind verfügbar:

   * **Jedes Mal fragen** - Standardeinstellung. Es erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler abgebrochen. Dieser Prozess emuliert im Wesentlichen einen Benutzer, der jeden Fehler manuell ablehnt.
   * **Sofort fortfahren** - Wenn ausgewählt, wird die Pipeline automatisch fortgesetzt, sobald ein wichtiger Fehler auftritt. Dieser Prozess emuliert im Wesentlichen einen Benutzer, der manuell jeden Fehler genehmigt.

   ![Konfiguration der Produktions-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Wählen Sie auf der Registerkarte **Source-Code** den Code aus, den die Pipeline verarbeiten soll.

   * **[Konfigurieren einer vollständigen Stack-Code-Pipeline](#full-stack-code)**
   * **[Konfigurieren einer zielgerichteten Bereitstellungs-Pipeline](#targeted-deployment)**

Weitere Informationen zu diesem Pipeline-Typ finden Sie unter [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

Die Schritte zum Abschluss der Erstellung Ihrer Produktions-Pipeline variieren je nach dem von Ihnen gewählten Typ von Quell-Code. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

### Konfigurieren einer vollständigen Stack-Code-Pipeline {#full-stack-code}

Eine Pipeline mit Full-Stack-Code stellt gleichzeitig Backend- und Frontend-Code-Builds bereit, die ein oder mehrere AEM-Server-Programme zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung bereits eine Pipeline mit Full-Stack-Code vorhanden ist, wird diese Auswahl deaktiviert.

**So konfigurieren Sie eine vollständige Stack-Code-Pipeline:**

1. Definieren Sie auf der Registerkarte **Source-Code** die folgenden Optionen.

   * **Repository** - Definiert, aus welchem Git-Repository die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Informationen zum Hinzufügen und Verwalten von Repositorys in Cloud Manager finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md) .

   * **Git-Verzweigung** - Definiert, von welcher Verzweigung die ausgewählte Pipeline den Code abrufen soll.
Geben Sie die ersten Zeichen des Zweignamens ein, und die Funktion zum automatischen Vervollständigen dieses Felds sucht nach den entsprechenden Verzweigungen, die Ihnen bei der Auswahl helfen.
   * **Konfiguration der Web-Stufe ignorieren**: Wenn diese Option aktiviert ist, stellt die Pipeline Ihre Web-Stufenkonfiguration nicht bereit.
   * **Pause vor der Bereitstellung in der Produktion** - Hält die Pipeline vor der Bereitstellung in der Produktion an.
   * **Geplant** - Ermöglicht dem Benutzer die Aktivierung der geplanten Produktionsbereitstellung.

   ![Full-Stack-Code](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Klicken Sie auf **Weiter**, um zur Registerkarte **Experience Audit** zu gelangen, auf der Sie die Pfade definieren können, die immer in das Experience Audit einbezogen werden sollen.

   ![Hinzufügen der Erlebnisprüfung](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Geben Sie Pfade an, die in die Erlebnisprüfung aufgenommen werden sollen.

   * Weitere Informationen finden Sie unter [Erlebnisprüfungstests](/help/implementing/cloud-manager/experience-audit-dashboard.md#configuration) .

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

Wenn die Pipeline ausgeführt wird, werden für Experience Audit konfigurierte Pfade basierend auf Leistungs-, Zugänglichkeits-, SEO-, Best Practices- und PWA-Tests gesendet und ausgewertet. Weitere Informationen finden Sie unter [Verstehen der Ergebnisse von Erlebnisprüfungen](/help/implementing/cloud-manager/experience-audit-dashboard.md).

Die Pipeline wird gespeichert und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

### Zielgerichtete Bereitstellungspipeline konfigurieren {#targeted-deployment}

Bei einer zielgerichteten Bereitstellung wird Code nur für ausgewählte Teile Ihrer AEM-Anwendung bereitgestellt. In einer solchen Bereitstellung können Sie einen der folgenden Code-Typen für **Einschließen** auswählen:

* **Konfiguration** - Konfigurieren Sie Einstellungen für verschiedene Funktionen in Ihrer AEM.
   * Eine Liste der unterstützten Konfigurationen, einschließlich Protokollweiterleitung, bereinigungsbezogener Wartungsaufgaben und verschiedener CDN-Konfigurationen, sowie Informationen zu deren ordnungsgemäßer Bereitstellung im Repository finden Sie unter [Verwenden von Konfigurations-Pipelines](/help/operations/config-pipeline.md).
   * Beim Ausführen einer zielgerichteten Bereitstellungs-Pipeline werden Konfigurationen bereitgestellt, sofern sie in der in der Pipeline definierten Umgebung, im Repository und in der Verzweigung gespeichert wurden.
   * Es kann immer nur eine Konfigurations-Pipeline pro Umgebung geben.
* **Frontend-Code** – Konfigurieren Sie JavaScript und CSS für das Frontend Ihrer AEM-Anwendung.
   * Mit Frontend-Pipelines erhalten Frontend-Entwickelnde mehr Unabhängigkeit, und der Entwicklungsprozess kann beschleunigt werden.
   * Weitere Informationen dazu, wie dieser Prozess abläuft und was dabei zu beachten ist, um das volle Potenzial dieses Prozesses auszuschöpfen, finden Sie im Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
* **Web-Ebene-Konfiguration** - Konfigurieren Sie Dispatcher-Eigenschaften zum Speichern, Verarbeiten und Bereitstellen von Webseiten für den Client.
   * Weitere Informationen finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines).
   * Wenn für die ausgewählte Umgebung bereits eine Web-Stufen-Code-Pipeline vorhanden ist, wird diese Auswahl deaktiviert.
   * Wenn Sie eine Web-Tier-Konfigurationspipeline für eine Umgebung mit einer vorhandenen Vollstapelpipeline erstellen, wird die Webstufenkonfiguration in der Vollstapelpipeline ignoriert. Diese Änderung betrifft nur die Webstufenkonfiguration in dieser Umgebung.

>[!NOTE]
>
>Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt. Weitere Informationen und die vollständige Liste der Einschränkungen finden Sie unter [Hinzufügen privater Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md) .

**So konfigurieren Sie eine zielgerichtete Bereitstellungs-Pipeline:**

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
   * **Geplant** - Ermöglicht dem Benutzer die Aktivierung der geplanten Produktionsbereitstellung. Nur für Web-Stufen-spezifische Bereitstellungen verfügbar.

   ![Konfigurations-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und auf der Karte **Pipelines** auf der Seite **Programmübersicht** können Sie jetzt [Pipelines verwalten](managing-pipelines.md).

## Dispatcher-Pakete überspringen {#skip-dispatcher-packages}

Um Dispatcher-Pakete in Ihrer Pipeline zu erstellen, ohne sie für den Build-Speicher zu veröffentlichen, können Sie die Veröffentlichungsoption deaktivieren. Dies kann dazu beitragen, die Laufzeit der Pipeline zu verkürzen.

Die folgende Konfiguration zum Deaktivieren von Veröffentlichungs-Dispatcher-Paketen muss über die `pom.xml`-Datei Ihres Projekts hinzugefügt werden. Eine Umgebungsvariable dient als Markierung, die Sie im Cloud Manager-Build-Container festlegen, um zu bestimmen, wann Dispatcher-Pakete ignoriert werden.

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
