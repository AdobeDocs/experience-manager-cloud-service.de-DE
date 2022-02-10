---
title: Konfigurieren von Produktions-Pipelines
description: Erfahren Sie, wie Sie Produktions-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.
index: true
source-git-commit: 536740f8bb5e54a3a831a22f4e6d237863aea324
workflow-type: tm+mt
source-wordcount: '1367'
ht-degree: 8%

---


# Konfigurieren einer Produktions-Pipeline {#configure-production-pipeline}

Erfahren Sie, wie Sie Produktions-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.

Ein Benutzer muss über die **[Bereitstellungsmanager](/help/onboarding/learn-concepts/cloud-manager-introduction.md#role-based-permissions)** Rolle zum Konfigurieren von Produktions-Pipelines.

>[!NOTE]
>
>Eine Produktions-Pipeline kann erst eingerichtet werden, wenn die Programmerstellung abgeschlossen ist, ein Git-Repository über mindestens eine Verzweigung verfügt und ein Satz aus Produktions- und Staging-Umgebung erstellt wird.

Bevor Sie Code bereitstellen, müssen Sie Ihre Pipelineeinstellungen über [!UICONTROL Cloud Manager] konfigurieren.

>[!NOTE]
>
>Sie können [Pipeline-Einstellungen bearbeiten](managing-pipelines.md) nach der Ersteinrichtung.

## Hinzufügen einer neuen Produktions-Pipeline {#adding-production-pipeline}

Nachdem Sie Ihr Programm eingerichtet haben und mindestens eine Umgebung mit der [!UICONTROL Cloud Manager] -Benutzeroberfläche können Sie eine Produktions-Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

>[!TIP]
>
>Bevor Sie eine Front-End-Pipeline konfigurieren, lesen Sie den Abschnitt [Journey zur AEM SchnellSite-Erstellung](/help/journey-sites/quick-site/overview.md) für eine durchgängige Anleitung über das benutzerfreundliche AEM Tool zur schnellen Site-Erstellung. Mit dieser Journey können Sie die Front-End-Entwicklung Ihrer AEM-Site optimieren, sodass Sie Ihre Site ohne AEM Backend-Wissen schnell anpassen können.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zum **Pipelines** der Karte **Programmübersicht** Seite und klicken Sie auf **Hinzufügen** auswählen **Produktions-Pipeline hinzufügen**.

   ![Die Karte &quot;Pipelines&quot;im Programm-Manager - Überblick](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. Die **Produktions-Pipeline hinzufügen** angezeigt. Bereitstellung einer **Pipeline-Name** , um Ihre Pipeline zusammen mit den folgenden Optionen zu identifizieren. Klicken Sie auf **Weiter**.

   **Deployment Trigger** - Sie haben beim Definieren der Bereitstellungs-Trigger zum Starten der Pipeline die folgenden Optionen.

   * **Manuell** - Verwenden Sie diese Option, um die Pipeline manuell zu starten.
   * **Bei Git-Änderungen** - Diese Optionen starten die CI/CD-Pipeline, sobald der konfigurierten Git-Verzweigung Commits hinzugefügt werden. Mit dieser Option können Sie die Pipeline nach Bedarf weiterhin manuell starten.

   **Verhalten bei wichtigen Metrikfehlern** - Während der Einrichtung oder Bearbeitung der Pipeline wird die **Bereitstellungsmanager** hat die Möglichkeit, das Verhalten der Pipeline zu definieren, wenn ein wichtiger Fehler in einem der Quality Gates auftritt. Die verfügbaren Optionen sind:

   * **Jedes Mal fragen** - Dies ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Sofort scheitern** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren** - Wenn diese Option aktiviert ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Anwender simuliert, der manuell jeden Fehler genehmigt.

   ![Konfiguration der Produktions-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Im **Quellcode** -Registerkarte müssen Sie definieren, wo die Pipeline ihren Code abrufen soll und welcher Code sie ist.

   * **[Code für das Frontend](#front-end-code)**
   * **[Full-Stack-Code](#full-stack-code)**
   * **[Web-Stufen-Konfiguration](#web-tier-config)**

Die Schritte zum Erstellen Ihrer Produktions-Pipeline variieren je nach der Option für **Quellcode** ausgewählt haben. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

### Code für das Frontend {#front-end-code}

Eine Frontend-Code-Pipeline stellt Frontend-Code-Builds bereit, die eine oder mehrere clientseitige Benutzeroberflächenanwendungen enthalten. Siehe Dokument . [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) für weitere Informationen zu diesem Pipelinetyp.

Führen Sie die folgenden Schritte aus, um die Konfiguration der Frontend-Code-Produktions-Pipeline abzuschließen.

1. Im **Quellcode** definieren, müssen Sie die folgenden Optionen definieren.

   * **Repository** - Diese Option definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.
   >[!TIP]
   > 
   >Siehe Dokument . [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
   * **Code-Speicherort** - Diese Option definiert den Pfad im Zweig des ausgewählten Repositorys, aus dem die Pipeline den Code abrufen soll.
   * **Anhalten vor der Bereitstellung in der Produktion** - Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.

   ![Frontend-Code](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-frontend.png)

1. Klicken **Speichern** , um die Pipeline zu speichern.

Die Pipeline wird gespeichert und Sie können jetzt [Pipelines verwalten](managing-pipelines.md) auf **Pipelines** auf der Karte **Programmübersicht** Seite.

### Full-Stack-Code {#full-stack-code}

Eine vollständige Codepipeline stellt gleichzeitig Back-End- und Front-End-Code-Builds bereit, die eine oder mehrere AEM Serveranwendungen zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten. Siehe Dokument . [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#full-stack-pipeline) für weitere Informationen zu diesem Pipelinetyp.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung bereits eine vollständige Codepipeline vorhanden ist, wird diese Auswahl deaktiviert.

Führen Sie die folgenden Schritte aus, um die Konfiguration der Code-Produktions-Pipeline für den vollständigen Stapel abzuschließen.

1. Im **Quellcode** definieren, müssen Sie die folgenden Optionen definieren.

   * **Repository** - Diese Option definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.
   >[!TIP]
   > 
   >Siehe Dokument . [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
   * **Code-Speicherort** - Diese Option definiert den Pfad im Zweig des ausgewählten Repositorys, aus dem die Pipeline den Code abrufen soll.
   * **Anhalten vor der Bereitstellung in der Produktion** - Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.
   * **Geplant**: Mit dieser Option kann der Benutzer die geplante Bereitstellung in der Produktionsumgebung aktivieren.

   ![Vollständiger Stack-Code](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-fullstack.png)

1. Klicken **Weiter** , um **Erlebnisprüfung** -Registerkarte, auf der Sie die Pfade definieren können, die immer in die Erlebnisprüfung einbezogen werden sollen.

   ![Erlebnisprüfung hinzufügen](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit.png)

1. Geben Sie einen Pfad an, der in die Erlebnisprüfung aufgenommen werden soll.

   * Seitenpfade müssen mit `/`.
   * Wenn Sie beispielsweise `https://wknd.site/us/en/about-us.html` Geben Sie im Experience Audit den Pfad ein. `/us/en/about-us.html`.

   ![Definieren eines Pfads für die Erlebnisprüfung](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit3.png)

1. Klicken **Seite hinzufügen** und der Pfad wird automatisch mit der Adresse Ihrer Umgebung ausgefüllt und der Pfadtabelle hinzugefügt.

   ![Pfad zur Tabelle speichern](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-audit4.png)

1. Fügen Sie bei Bedarf weitere Pfade hinzu, indem Sie die vorherigen beiden Schritte wiederholen.

   * Sie können maximal 25 Pfade hinzufügen.
   * Wenn Sie keine Pfade definieren, wird die Startseite der Site standardmäßig in die Erlebnisprüfung einbezogen.

1. Klicken Sie auf **Speichern** , um die Pipeline zu speichern.

Für Experience Audit konfigurierte Pfade werden an den Dienst gesendet und gemäß den Leistungs-, Zugänglichkeits-, SEO- (Suchmaschinenoptimierung), Best Practices- und PWA-Tests (Progressive Web App) bewertet, wenn die Pipeline ausgeführt wird. Weitere Informationen finden Sie unter [Verstehen der Ergebnisse von Experience Audit](/help/implementing/cloud-manager/experience-audit-testing.md).

Die Pipeline wird gespeichert und Sie können jetzt [Pipelines verwalten](managing-pipelines.md) auf **Pipelines** auf der Karte **Programmübersicht** Seite.

### Web-Stufen-Konfiguration {#web-tier-config}

Eine Web-Ebene-Konfigurationspipeline stellt HTTPD-/Dispatcher-Konfigurationen bereit. Siehe Dokument . [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipeline) für weitere Informationen zu diesem Pipelinetyp.

Führen Sie die folgenden Schritte aus, um die Konfiguration der Code-Produktions-Pipeline für den vollständigen Stapel abzuschließen.

1. Im **Quellcode** definieren, müssen Sie die folgenden Optionen definieren.

   * **Repository** - Diese Option definiert, aus welchem Git-Repo die Pipeline den Code abrufen soll.
   >[!TIP]
   > 
   >Siehe Dokument . [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md) , um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Diese Option definiert, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
   * **Code-Speicherort** - Diese Option definiert den Pfad im Zweig des ausgewählten Repositorys, aus dem die Pipeline den Code abrufen soll.
      * Bei Web-Tier-Konfigurationspipelines ist dies normalerweise der Pfad, der Folgendes enthält `conf.d`, `conf.dispatcher.d`und `opt-in` Verzeichnissen.
      * Wenn die Projektstruktur beispielsweise aus dem [AEM Projektarchetyp,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de) der Pfad `/dispatcher/src`.
   * **Anhalten vor der Bereitstellung in der Produktion** - Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.
   * **Geplant**: Mit dieser Option kann der Benutzer die geplante Bereitstellung in der Produktionsumgebung aktivieren.

   ![Webebenencode](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-webtier.png)

1. Klicken **Speichern** , um die Pipeline zu speichern.

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
