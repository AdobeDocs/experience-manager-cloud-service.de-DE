---
title: Konfigurieren von Produktions-Pipelines
description: Erfahren Sie, wie Sie Produktions-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
source-git-commit: 3ba5184275e539027728ed134c47f66fa4746d9a
workflow-type: ht
source-wordcount: '1338'
ht-degree: 100%

---


# Konfigurieren einer Produktions-Pipeline {#configure-production-pipeline}

Erfahren Sie, wie Sie Produktions-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen. Eine Produktions-Pipeline stellt Code zuerst in der Staging-Umgebung bereit. Nach der Genehmigung wird derselbe Code in der Produktionsumgebung bereitgestellt.

Benutzende müssen über die Rolle **[Bereitstellungs-Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** verfügen, um Produktions-Pipelines konfigurieren zu können.

>[!NOTE]
>
>Eine Produktions-Pipeline kann erst eingerichtet werden, wenn die Erstellung eines Programms abgeschlossen wurde, das Git-Repository über mindestens eine Verzweigung verfügt und ein Satz aus Produktions- und Staging-Umgebung erstellt wurde.

Bevor Sie Code bereitstellen, müssen Sie Ihre Pipeline-Einstellungen über den [!UICONTROL Cloud Manager] konfigurieren.

>[!NOTE]
>
>Nach der Ersteinrichtung können Sie [Pipeline-Einstellungen bearbeiten](managing-pipelines.md).

## Hinzufügen einer neuen Produktions-Pipeline {#adding-production-pipeline}

Sobald Sie mit der Benutzeroberfläche von [!UICONTROL Cloud Manager] Ihr Programm eingerichtet und mindestens eine Umgebung haben, können Sie eine Produktions-Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

>[!TIP]
>
>Bevor Sie eine Frontend-Pipeline konfigurieren, lesen Sie den Abschnitt [Tour zur schnellen Erstellung einer AEM-Site](/help/journey-sites/quick-site/overview.md). Dort finden Sie eine durchgängige Anleitung über das benutzerfreundliche AEM-Tool zur schnellen Site-Erstellung. Diese Tour hilft Ihnen, die Frontend-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site schnell ohne AEM-Backend-Kenntnisse anzupassen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus

1. Wählen Sie auf dem Bildschirm **[Meine Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/editing-programs.md#my-programs)** das Programm aus.

1. Gehen Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf **Hinzufügen** und wählen Sie dann **Produktions-Pipeline hinzufügen** aus.

   ![Die Karte „Pipelines“ im Programm-Manager – Überblick](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** erscheint. Geben Sie einen **Pipeline-Name** an, um Ihre Pipeline zu identifizieren, sowie die folgenden Optionen. Klicken Sie auf **Weiter**.

   **Bereitstellungsauslöser**: Beim Definieren der Bereitstellungsauslöser für den Start der Pipeline haben Sie die folgenden Optionen.

   * **Manuell**: Verwenden Sie diese Option, um die Pipeline manuell zu starten.
   * **Bei Git-Änderungen**: Diese Option startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

   **Verhalten bei bedeutenden Metrikfehlern**: Bei der Einrichtung oder Bearbeitung der Pipeline kann der **Bereitstellungs-Manager** festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Folgende Optionen sind verfügbar:

   * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler abgebrochen. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.

   ![Konfiguration der Produktions-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Auf der Registerkarte **Quell-Code** müssen Sie auswählen, welcher Code von der Pipeline verarbeitet werden soll.

   * **[Full-Stack-Code](#full-stack-code)**
   * **[Zielgerichtete Bereitstellung](#targeted-deployment)**

Weitere Informationen zu diesem Pipeline-Typ finden Sie unter [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

Die Schritte zum Abschluss der Erstellung Ihrer Produktions-Pipeline variieren je nach dem von Ihnen gewählten Typ von Quell-Code. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

### Full-Stack-Code {#full-stack-code}

Eine Pipeline mit Full-Stack-Code stellt gleichzeitig Backend- und Frontend-Code-Builds bereit, die ein oder mehrere AEM-Server-Programme zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung bereits eine Pipeline mit Full-Stack-Code vorhanden ist, wird diese Auswahl deaktiviert.

Gehen Sie wie folgt vor, um die Konfiguration der Pipeline mit Full-Stack-Code abzuschließen.

1. In der Registerkarte **Quell-Code** müssen Sie die folgenden Optionen definieren.

   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie im Dokument [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md).

   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welchem Zweig in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens ein und die Funktion zum automatischen Vervollständigen dieses Feldes findet die entsprechenden Verzweigungen, um Ihnen bei der Auswahl zu helfen.
   * **Konfiguration der Web-Stufe ignorieren**: Wenn diese Option aktiviert ist, stellt die Pipeline Ihre Web-Stufenkonfiguration nicht bereit.
   * **Anhalten vor der Bereitstellung in der Produktion**: Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.
   * **Geplant**: Mit dieser Option kann der Benutzer die geplante Bereitstellung in der Produktionsumgebung aktivieren.

   ![Full-Stack-Code](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Tippen oder klicken Sie auf **Weiter**, um zur Registerkarte **Erlebnisprüfung** zu gelangen, auf der Sie die Pfade definieren können, die immer in die Erlebnisprüfung einbezogen werden sollen.

   ![Hinzufügen der Erlebnisprüfung](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Geben Sie Pfade an, die in die Erlebnisprüfung aufgenommen werden sollen.

   * Einzelheiten finden Sie im Dokument [Testen mit der Erlebnisprüfung](/help/implementing/cloud-manager/experience-audit-testing.md#configuration).

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

Für das Experience Audit konfigurierte Pfade werden an den Dienst gesendet und gemäß den Leistungs-, Zugänglichkeits-, SEO- (Suchmaschinenoptimierung), Best Practices- und PWA (Progressive Web-App)-Tests bewertet, wenn die Pipeline ausgeführt wird. Weitere Einzelheiten finden Sie unter [Grundlegendes zu den Ergebnissen von Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md).

Die Pipeline wird gespeichert und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

### Zielgerichtete Bereitstellung {#targeted-deployment}

Bei einer zielgerichteten Bereitstellung wird Code nur für ausgewählte Teile Ihrer AEM-Anwendung bereitgestellt. In einer solchen Bereitstellung können Sie auswählen, einen der folgenden Code-Typen **einzuschließen**:

* **Konfiguration**: Konfigurieren der Einstellungen für Traffic-Filterregeln in Ihrer AEM-Umgebung.
   * Im Dokument [Traffic-Filterregeln einschließlich WAF-Regeln](/help/security/traffic-filter-rules-including-waf.md) erfahren Sie, wie Sie die Konfigurationen in Ihrem Repository verwalten, damit sie ordnungsgemäß bereitgestellt werden.
   * Wenn Sie eine gezielte Bereitstellungs-Pipeline ausführen, werden [WAF-Konfigurationen](/help/security/traffic-filter-rules-including-waf.md) bereitgestellt, sofern sie in der Umgebung, dem Repository und der Verzweigung gespeichert sind, die Sie in der Pipeline definiert haben.
   * Es kann immer nur eine Konfigurations-Pipeline pro Umgebung geben.
* **Frontend-Code** – Konfigurieren Sie JavaScript und CSS für das Frontend Ihrer AEM-Anwendung.
   * Mit Frontend-Pipelines erhalten Frontend-Entwickelnde mehr Unabhängigkeit, und der Entwicklungsprozess kann beschleunigt werden.
   * Weitere Informationen dazu, wie dieser Prozess abläuft und was dabei zu beachten ist, um das volle Potenzial dieses Prozesses auszuschöpfen, finden Sie im Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
* **Web-Stufen-Konfiguration** – Konfigurieren Sie die Dispatcher-Eigenschaften zum Speichern, Verarbeiten und Bereitstellen von Web-Seiten für den Client.
   * Weitere Informationen finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines).
   * Wenn für die ausgewählte Umgebung bereits eine Web-Stufen-Code-Pipeline vorhanden ist, wird diese Auswahl deaktiviert.
   * Wenn Sie über eine vorhandene Full-Stack-Pipeline verfügen, die in einer Umgebung bereitgestellt wird, wird beim Erstellen einer Web-Stufen-Konfigurations-Pipeline für dieselbe Umgebung die vorhandene Web-Stufen-Konfiguration in der Full-Stack-Pipeline ignoriert.

Die Schritte zum Abschluss der Erstellung Ihrer Produktions- und Zielgruppen-Bereitstellungs-Pipeline sind dieselben, wenn Sie einen Bereitstellungstyp auswählen.

1. Wählen Sie den benötigten Bereitstellungstyp aus.

![Zielgerichtete Bereitstellungsoptionen](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-targeted-deployment.png)

1. Definieren Sie die **geeigneten Bereitstellungsumgebungen**.

   * Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, für welche Umgebungen sie etwas bereitstellen soll.

1. Definieren Sie unter **Quell-Code** die folgenden Optionen:

   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md).

   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens und die Funktion zur automatischen Vervollständigung dieses Felds ein. Es werden die entsprechenden auswählbaren Verzweigungen gesucht.
   * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.
   * **Anhalten vor der Bereitstellung in der Produktion**: Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.
   * **Geplant**: Mit dieser Option können Benutzende die geplante Bereitstellung in der Produktionsumgebung aktivieren. Nur für Web-Stufen-spezifische Bereitstellungen verfügbar.

   ![Konfigurations-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

## Überspringen von Dispatcher-Paketen {#skip-dispatcher-packages}

Wenn Sie möchten, dass Dispatcher-Pakete als Teil Ihrer Pipeline erstellt werden, sie aber nicht im Build-Speicher veröffentlicht werden sollen, können Sie die Veröffentlichung deaktivieren, was die Laufzeit der Pipeline verkürzen kann.

Die folgende Konfiguration zum Deaktivieren der Veröffentlichung von Dispatcher-Paketen muss über die Datei `pom.xml` Ihres Projekts hinzugefügt werden. Sie basiert auf einer Umgebungsvariablen, die als Markierung dient, die Sie im Cloud Manager-Build-Container festlegen können, um zu definieren, wann Dispatcher-Pakete ignoriert werden sollen.

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
