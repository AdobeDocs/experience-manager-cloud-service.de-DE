---
title: Konfigurieren von Produktions-Pipelines
description: Erfahren Sie, wie Sie Produktions-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
source-git-commit: 3348662e3da4dad75b851d7af7251d456321a3ec
workflow-type: ht
source-wordcount: '1520'
ht-degree: 100%

---


# Konfigurieren einer Produktions-Pipeline {#configure-production-pipeline}

Erfahren Sie, wie Sie Produktions-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen. Eine Produktions-Pipeline stellt Code zuerst in der Staging-Umgebung bereit. Nach der Genehmigung wird derselbe Code in der Produktionsumgebung bereitgestellt.

Ein Benutzer muss über die Rolle **[Implementierungs-Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** verfügen, um Produktions-Pipelines konfigurieren zu können.

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

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Programmübersicht** zur Karte **Pipelines** und klicken Sie auf **Hinzufügen** und wählen Sie dann **Produktions-Pipeline hinzufügen** aus.

   ![Die Karte „Pipelines“ im Programm-Manager – Überblick](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** erscheint. Geben Sie einen **Pipeline-Name** an, um Ihre Pipeline zu identifizieren, sowie die folgenden Optionen. Klicken Sie auf **Weiter**.

   **Bereitstellungsauslöser**: Beim Definieren der Bereitstellungsauslöser für den Start der Pipeline haben Sie die folgenden Optionen.

   * **Manuell**: Verwenden Sie diese Option, um die Pipeline manuell zu starten.
   * **Bei Git-Änderungen**: Diese Option startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

   **Verhalten bei bedeutenden Metrikfehlern**: Bei der Einrichtung oder Bearbeitung der Pipeline kann der **Implementierungs-Manager** festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Folgende Optionen sind verfügbar:

   * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem gravierenden Fehler abgebrochen. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.

   ![Konfiguration der Produktions-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. In der Registerkarte **Quell-Code** müssen Sie definieren, wo die Pipeline ihren Code abrufen soll und um welche Art von Code es sich handelt.

   * **[Code für das Frontend](#front-end-code)**
   * **[Full-Stack-Code](#full-stack-code)**
   * **[Web-Stufen-Konfiguration](#web-tier-config)**

Die Schritte zum Abschluss der Erstellung Ihrer Produktions-Pipeline variieren je nach der von Ihnen gewählten Option für den **Quell-Code**. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

### Code für das Frontend {#front-end-code}

Eine Frontend-Code-Pipeline stellt Frontend-Code-Builds bereit, die eine oder mehrere Client-seitige Benutzeroberflächenanwendungen enthalten. Weitere Informationen zu dieser Art von Pipelines finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end).

Führen Sie die folgenden Schritte aus, um die Konfiguration der Frontend-Code-Produktions-Pipeline abzuschließen.

1. In der Registerkarte **Quell-Code** müssen Sie die folgenden Optionen definieren.

   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.
   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie im Dokument [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md).

   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welchem Zweig in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens ein und die Funktion zum automatischen Vervollständigen dieses Feldes findet die entsprechenden Verzweigungen, um Ihnen bei der Auswahl zu helfen.
   * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.
   * **Anhalten vor der Bereitstellung in der Produktion**: Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.

   ![Code für das Frontend](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-frontend.png)

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

Die Pipeline wird gespeichert und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

### Full-Stack-Code {#full-stack-code}

Eine Pipeline mit Full-Stack-Code stellt gleichzeitig Backend- und Frontend-Code-Builds bereit, die ein oder mehrere AEM-Server-Programme zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten. Weitere Informationen zu dieser Art von Pipelines finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline).

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
   * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.
   * **Anhalten vor der Bereitstellung in der Produktion**: Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.
   * **Geplant**: Mit dieser Option kann der Benutzer die geplante Bereitstellung in der Produktionsumgebung aktivieren.

   ![Full-Stack-Code](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Klicken Sie auf **Weiter**, um zur Registerkarte **Experience Audit** zu gelangen, auf der Sie die Pfade definieren können, die immer in das Experience Audit einbezogen werden sollen.

   ![Hinzufügen von Experience Audit](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Geben Sie einen Pfad an, der in das Experience Audit aufgenommen werden soll.

   * Seitenpfade müssen mit einem `/` beginnen.
   * Wenn Sie beispielsweise `https://wknd.site/us/en/about-us.html` in das Experience Audit aufnehmen möchten, geben Sie den Pfad `/us/en/about-us.html` ein.

   ![Definieren eines Pfads für das Experience Audit](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

1. Klicken Sie auf **Seite hinzufügen** und der Pfad wird automatisch mit der Adresse Ihrer Umgebung ausgefüllt und der Pfadtabelle hinzugefügt.

   ![Speichern des Pfads zur Tabelle](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

1. Fügen Sie weitere Pfade hinzu, indem Sie die vorherigen beiden Schritte wiederholen.

   * Sie können maximal 25 Pfade hinzufügen.
   * Wenn Sie keine Pfade definieren, wird die Startseite der Site standardmäßig in das Experience Audit einbezogen.

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

Für das Experience Audit konfigurierte Pfade werden an den Service gesendet und gemäß den Leistungs-, Zugänglichkeits-, SEO- (Suchmaschinenoptimierung), Best Practices- und PWA (Progressive Web App)-Tests bewertet, wenn die Pipeline ausgeführt wird. Weitere Informationen finden Sie unter [Verstehen der Ergebnisse von Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md).

Die Pipeline wird gespeichert und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

### Web-Stufen-Konfiguration {#web-tier-config}

Eine Pipeline für die Web-Stufen-Konfiguration stellt HTTPD-/Dispatcher-Konfigurationen bereit. Weitere Informationen zu dieser Art von Pipelines finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline).

Gehen Sie wie folgt vor, um die Konfiguration der Pipeline mit Full-Stack-Code abzuschließen.

1. In der Registerkarte **Quell-Code** müssen Sie die folgenden Optionen definieren.

   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.
   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie im Dokument [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md).

   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welchem Zweig in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens ein und die Funktion zum automatischen Vervollständigen dieses Feldes findet die entsprechenden Verzweigungen, um Ihnen bei der Auswahl zu helfen.
   * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.
      * Bei Pipelines für die Web-Stufen-Konfiguration ist dies normalerweise der Pfad, der `conf.d`-, `conf.dispatcher.d`- und `opt-in`-Verzeichnisse enthält.
      * Wenn die Projektstruktur beispielsweise aus dem [AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) erzeugt wurde, ist der Pfad `/dispatcher/src`.
   * **Anhalten vor der Bereitstellung in der Produktion**: Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.
   * **Geplant**: Mit dieser Option kann der Benutzer die geplante Bereitstellung in der Produktionsumgebung aktivieren.

   ![Web-Stufen-Code](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-webtier.png)

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

>[!NOTE]
>
>Wenn Sie über eine vorhandene Full-Stack-Pipeline verfügen, die in einer Umgebung bereitgestellt wird, wird beim Erstellen einer Web-Stufen-Konfigurations-Pipeline für dieselbe Umgebung die vorhandene Web-Stufen-Konfiguration in der Full-Stack-Pipeline ignoriert.

Die Pipeline wird gespeichert und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

## Entwickeln von Sites mit der Frontend-Pipeline {#developing-with-front-end-pipeline}

Mit Frontend-Pipelines erhalten Frontend-Entwicklern mehr Unabhängigkeit und der Entwicklungsprozess kann beschleunigt werden.

Wie dieser Prozess abläuft und was dabei zu beachten ist, um das volle Potenzial dieses Prozesses auszuschöpfen, erfahren Sie im Dokument [Entwicklung von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).

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
