---
title: Hinzufügen einer Produktions-Pipeline
description: Erfahren Sie, wie Sie eine Produktions-Pipeline hinzufügen, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.
index: true
exl-id: 67edca16-159e-469f-815e-d55cf9063aa4
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: dea8a3df29876df1c97454a97602045eb50121ad
workflow-type: tm+mt
source-wordcount: '1857'
ht-degree: 54%

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

{{sign-in-to-cloud-manager}}

1. Klicken Sie in **Konsole** Meine Programme“ auf ein Programm.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Gehen Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf **Hinzufügen** und wählen Sie dann **Produktions-Pipeline hinzufügen** aus.

   ![Die Karte „Pipelines“ im Programm-Manager – Überblick](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** erscheint. Geben Sie zur Identifizierung Ihrer Pipeline **Name der Pipeline** zusammen mit den folgenden Optionen an. Klicken Sie auf **Weiter**.

   **Bereitstellungsauslöser**: Beim Definieren der Bereitstellungsauslöser für den Start der Pipeline haben Sie die folgenden Optionen.

   * **Manuell**: Mit dieser Option wird die Pipeline manuell gestartet.
   * **Bei Git-Änderungen**: Mit dieser Option wird die CI/CD-Pipeline gestartet, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

   **Verhalten bei bedeutenden Metrikfehlern**: Bei der Einrichtung oder Bearbeitung der Pipeline kann der **Bereitstellungs-Manager** festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Folgende Optionen sind verfügbar:

   * **Jedes Mal fragen**: Dies ist die Standardeinstellung, Bei einem wichtigen Fehler ist ein manuelles Eingreifen erforderlich.
   * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler abgebrochen. Dieser Prozess emuliert einen Benutzer, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler automatisch fortgesetzt. Dieser Prozess emuliert einen Benutzer, der manuell jeden Fehler genehmigt.

   ![Konfiguration der Produktions-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Wählen Sie auf der Registerkarte **Source** Code den Code-Typ aus, den die Pipeline verarbeitet.

   * **[Ich verwende den Full-Stack-Code](#full-stack-code)**
   * **[Konfigurieren einer zielgerichteten Bereitstellungs-Pipeline](#targeted-deployment)**

Weitere Informationen zu diesem Pipeline-Typ finden Sie unter [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

Die Schritte zum Abschluss der Erstellung Ihrer Produktions-Pipeline variieren je nach dem von Ihnen gewählten Typ von Quell-Code. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

### Ich verwende den Full-Stack-Code {#full-stack-code}

Eine Pipeline mit Full-Stack-Code stellt gleichzeitig Backend- und Frontend-Code-Builds bereit, die ein oder mehrere AEM-Server-Programme zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung bereits eine Pipeline mit Full-Stack-Code vorhanden ist, wird diese Auswahl deaktiviert.

**So konfigurieren Sie eine Full-Stack-Code-Pipeline:**

1. Definieren Sie auf der Registerkarte **Quell-Code** die folgenden Optionen:

   * **Repository** - Definiert das Git-Repository, aus dem die Pipeline den Code abruft.

   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

   * **Git-Verzweigung**: Wählen Sie in der Dropdown-Liste die Verzweigung im ausgewählten Repository aus, aus dem die Pipeline erstellt. Der Standardwert lautet `main`. Die Pipeline verwendet die ausgewählte Verzweigung als Quelle für die Erstellung und Bereitstellung. Klicken Sie bei Bedarf auf **Aktualisieren**, um die Liste der verfügbaren Verzweigungen für das ausgewählte Repository zu aktualisieren. Verwenden Sie diese Option, wenn eine kürzlich erstellte Verzweigung nicht in der Liste angezeigt wird.
   * **Strategie erstellen**
      * **Vollständiger Build**: Erstellt jedes Mal alle Module im Repository.
      * **Smarter Build** - Erstellt nur Module, die seit dem letzten Commit geändert wurden.<br>Weitere Informationen über [Verwendung von Smart Build in einer produktionsfremden Pipeline](#about-smart-build-non-production-pipeline).
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

### Ich verwende eine zielgerichtete Bereitstellung. {#targeted-deployment}

Bei einer zielgerichteten Bereitstellung wird Code nur für ausgewählte Teile Ihrer AEM-Anwendung bereitgestellt. In einer solchen Bereitstellung können Sie sich dazu entscheiden, einen der folgenden Code-Typen **einzuschließen**:

* **Konfig**: Konfigurieren Sie Einstellungen für verschiedene Funktionen in Ihrer AEM-Umgebung.
   * Unter [Verwenden von Konfigurations](/help/operations/config-pipeline.md)Pipelines“ finden Sie eine Liste der unterstützten Konfigurationen, darunter Protokollweiterleitung, Bereinigungsaufgaben und verschiedene CDN-Konfigurationen. Außerdem erfahren Sie, wie Sie diese in Ihrem Repository verwalten, damit sie ordnungsgemäß bereitgestellt werden.
   * Beim Ausführen einer zielgerichteten Bereitstellungs-Pipeline werden Konfigurationen bereitgestellt, sofern sie in der Umgebung, dem Repository und der Verzweigung gespeichert sind, die in der Pipeline definiert sind.
   * Es kann immer nur eine Konfigurations-Pipeline pro Umgebung geben.
* **Konfigurieren der Edge Delivery Services-Konfigurations**-Pipeline: Edge Delivery-Konfigurations-Pipelines verfügen über keine separaten Entwicklungs-, Staging- und Produktionsumgebungen. In AEM as a Cloud Service durchlaufen die Änderungen Entwicklungs-, Staging- und Produktionsebenen. Eine Edge Delivery-Konfigurations-Pipeline wendet ihre Konfiguration dagegen direkt auf alle in Cloud Manager registrierten Edge Delivery Sites-Domains an. Weitere Informationen finden Sie unter [Hinzufügen einer Edge Delivery-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).
* **Frontend-Code** – Konfigurieren Sie JavaScript und CSS für das Frontend Ihrer AEM-Anwendung.
   * Mit Frontend-Pipelines erhalten Frontend-Entwickelnde mehr Unabhängigkeit, und der Entwicklungsprozess kann beschleunigt werden.
   * Weitere Informationen dazu, wie dieser Prozess abläuft und was dabei zu beachten ist, um das volle Potenzial dieses Prozesses auszuschöpfen, finden Sie im Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
* **Web-Stufen-**: Konfigurieren von Dispatcher-Eigenschaften zum Speichern, Verarbeiten und Bereitstellen von Web-Seiten für den Client.
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

   * Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, wählen Sie die Umgebungen aus, in denen sie bereitgestellt wird.

1. Definieren Sie unter **Quell-Code** die folgenden Optionen:

   * **Repository** - Mit dieser Option wird das Git-Repository definiert, aus dem die Pipeline den Code abruft.

   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

   * **Git-Verzweigung** - Mit dieser Option wird die Verzweigung in der ausgewählten Pipeline definiert, aus der der Code abgerufen wird.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens und die Funktion zur automatischen Vervollständigung dieses Felds ein. Es werden die entsprechenden auswählbaren Verzweigungen gesucht.
   * **Code-Speicherort** - Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys definiert, aus dem die Pipeline den Code abruft.
   * **Anhalten vor der Bereitstellung in der Produktion**: Diese Option setzt die Pipeline vor der Bereitstellung in der Produktion aus.
   * **Geplant**: Ermöglicht Benutzenden die Aktivierung der geplanten Produktionsbereitstellung. Nur für Web-Stufen-spezifische Bereitstellungen verfügbar.

   ![Konfigurations-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/prod-pipeline-config-deployment.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).

## Über die Verwendung von Smart Build in einer Produktions-Pipeline{#about-smart-build-production-pipeline}

**Smart Build** in Cloud Manager ist eine optimierte Build-Strategie für Produktions-Pipelines. Smartes Erstellen reduziert Build-Zeiten, indem Module zwischengespeichert und nur die Module neu erstellt werden, die seit der letzten erfolgreichen Ausführung geändert wurden. Unveränderte Module werden aus dem Cache wiederverwendet, während nur geänderte Module und ihre Abhängigkeiten neu erstellt werden, was die Effizienz für Workflows für die iterative Entwicklung verbessert.

>[!IMPORTANT]
>
>Die erste Ausführung nach der Aktivierung von Smart Build verhält sich wie ein vollständiger Build, da der Cache leer ist.

Smartes Erstellen wird empfohlen, wenn Folgendes zutrifft:

* Sie entwickeln aktiv und nehmen häufige inkrementelle Änderungen vor.
* Ihr Projekt enthält mehrere Maven-Module.
* Vollständige Builds beanspruchen viel Zeit.

Smartes Erstellen ist nicht immer ideal, wenn Folgendes zutrifft:

* Ihr Build beruht in hohem Maße auf Plug-ins, die Vorgänge außerhalb des Abhängigkeitsdiagramms von Maven durchführen.
* Sie benötigen bei jeder Ausführung eine vollständige Neuaufbauvalidierung.

### Grundlegendes zur Build-Leistung{#smart-build-performance}

Der Leistungsgewinn durch die Verwendung von Smart Build hängt von mehreren Faktoren ab, darunter den folgenden:

* Die Anzahl der Module im Projekt.
* Häufigkeit und Umfang von Code-Änderungen.
* Die Verteilung von Abhängigkeiten über Module hinweg.

Die größte Verbesserung erleben Projekte mit vielen unabhängigen Modulen.

### Opt-out aus dem Cache pro Modul{#smart-build-cache-optout}

Smart Build bietet eine differenzierte Steuerung, mit der Sie das Caching für bestimmte Module deaktivieren können. Diese Funktion ist nützlich, wenn bestimmte Module:

* Verwenden Sie Plug-ins wie `exec-maven-plugin` oder `maven-antrun-plugin`.
* Führen Sie Dateivorgänge aus, die nicht von Maven-Abhängigkeiten verfolgt werden.
* Zwischengespeicherte Inhalte führen zu inkonsistenten Ergebnissen.

### Deaktivieren der Zwischenspeicherung für ein Modul{#smart-build-disable-caching}

Sie können die folgende Eigenschaft zum `pom.xml` des betroffenen Moduls hinzufügen:

```xml
<properties>
  <maven.build.cache.enabled>false</maven.build.cache.enabled>
</properties>
```

Diese Syntax zwingt das Modul bei jeder Pipeline-Ausführung neu zu erstellen, während andere Module weiterhin vom Caching profitieren.

### Einschränkungen und Überlegungen bei der Verwendung von Smart Build{#smart-build-limitations}

Beachten Sie bei der Verwendung von Smart Build Folgendes:

* Smarter Build beruht auf Maven-Abhängigkeitsanalyse.
* Bei Änderungen außerhalb des Abhängigkeitsdiagramms werden Trigger-Neuaufbauten nicht unterstützt.
* Einige Plug-ins sind nicht vollständig mit der Zwischenspeicherung kompatibel.
* Sie können jederzeit wieder zu **Vollständiger Build** wechseln, indem Sie die Produktions-Pipeline bearbeiten.

Wenn Sie auf unerwartetes Build-Verhalten stoßen, sollten Sie das Caching für bestimmte Module deaktivieren oder Ihre Build-Strategie vorübergehend auf **Vollständiger Build** umstellen.

### Fehlerbehebung bei Problemen mit Smart Build{#smart-build-troubleshoot}

| Problem | Lösungsvorschläge |
| --- | --- |
| Buildergebnisse sind inkonsistent | ・ Deaktivierung der Zwischenspeicherung für betroffene Module.<br>・ Überprüfen des Plug-in-Verhaltens (insbesondere `exec`/`antrun`-Plug-ins). |
| Keine Leistungsverbesserung | ・ Stellen Sie sicher, dass mehrere Durchgänge stattgefunden haben (Aufwärmen des Cache).<br>・ Prüfen Sie, ob die meisten Module häufig wechseln. |
| Unerwartete Artefakte oder fehlende Änderungen | ・ Überprüfen, ob Änderungen außerhalb des Maven-Abhängigkeits-Trackings liegen<br>・ Verwenden Sie **Vollständiger Build** zur Überprüfung. |

Informationen zum Aktivieren von Smart Build [&#x200B; Sie unter „Hinzufügen einer Produktions-Pipeline](#adding-production-pipeline).

## Überspringen von Dispatcher-Paketen {#skip-dispatcher-packages}

Um Dispatcher-Pakete in Ihrer Pipeline zu erstellen, ohne sie für den Build-Speicher zu veröffentlichen, können Sie die Veröffentlichungsoption deaktivieren. Dadurch wird die Laufzeit der Pipeline verkürzt.

Die folgende Konfiguration zum Deaktivieren von Veröffentlichungs-Dispatcher-Paketen muss über die Datei `pom.xml` Ihres Projekts hinzugefügt werden. Eine Umgebungsvariable dient als Flag, das Sie im Cloud Manager-Build-Container festlegen, um festzulegen, wann Dispatcher-Pakete ignoriert werden sollen.

```xml
<profile>
  <id>only-include-dispatcher-when-it-isnt-ignored</id>
  <activation>
    <property>
      <name>env.IGNORE_DISPATCHER_PACKAGES</name>
      <value>[!NOTE]rue</value>
    </property>
  </activation>
  <modules>
    <module>dispatcher</module>
  </modules>
</profile>
```
