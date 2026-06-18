---
title: Hinzufügen einer produktionsfremden Pipeline
description: Erfahren Sie, wie Sie eine produktionsfremde Pipeline hinzufügen, um die Qualität des Codes vor seiner Bereitstellung in Produktionsumgebungen zu testen.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
source-git-commit: a0d2982cff40cd8a9826eb22304f16b14a44d631
workflow-type: tm+mt
source-wordcount: '1759'
ht-degree: 34%

---


# Hinzufügen einer produktionsfremden Pipeline {#configuring-non-production-pipelines}

Nachdem Sie ein Programm eingerichtet und mindestens eine Umgebung in der Cloud Manager-Benutzeroberfläche erstellt haben, können Sie produktionsfremde Pipelines hinzufügen. Mit diesen Pipelines können Sie die Code-Qualität testen, bevor Sie sie in Produktionsumgebungen bereitstellen.

Benutzende müssen über die Rolle **[Bereitstellungs-Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** verfügen, um produktionsfremde Pipelines konfigurieren zu können.

>[!NOTE]
>
>Nach der Ersteinrichtung können Sie die [Pipeline-Einstellungen bearbeiten](managing-pipelines.md).

## Hinzufügen einer neuen produktionsfremden Pipeline

Nachdem Sie in der Benutzeroberfläche von Cloud Manager ein Programm eingerichtet und mindestens eine Umgebung erstellt haben, können Sie produktionsfremde Pipelines hinzufügen. Verwenden Sie diese Pipelines, um die Code-Qualität zu testen, bevor Sie sie in Produktionsumgebungen bereitstellen.

**So fügen Sie eine neue produktionsfremde Pipeline hinzu:**

1. Melden Sie sich bei Cloud Manager unter [experience.adobe.com](https://experience.adobe.com) an.
1. Klicken Sie **Abschnitt „Schnellzugriff** auf **Experience Manager**.
1. Klicken Sie im linken Panel auf **Cloud Manager**.
1. Wählen Sie die gewünschte Organisation aus.
1. Klicken Sie in **Konsole** Meine Programme“ auf ein Programm.
1. Klicken Sie im linken Seitenbereich auf **Pipelines**.
1. Klicken Sie auf **Seite** Pipelines“ oben rechts auf **Pipeline hinzufügen** > **Produktionsfremde Pipeline hinzufügen**.

   ![Produktionsfremde Pipeline hinzufügen](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. Wählen Sie **der Registerkarte** im Dialogfeld **Produktionsfremde Pipeline hinzufügen** eine der folgenden produktionsfremden Pipelines aus, die Sie erstellen möchten:

   * **Code-Qualitäts-Pipeline**: Erstellt eine Pipeline, die den Code in einer GIT-Verzweigung erstellt, Komponententests durchführt und die Code-Qualität auswertet, ohne in einer Umgebung bereitgestellt zu werden.
   * **Bereitstellungs-Pipeline**: Erstellt eine Pipeline, die den Code erstellt, Komponententests durchführt, die Code-Qualität auswertet und in einer Nicht-Produktionsumgebung implementiert.

   ![Dialogfeld „Produktionsfremde Pipeline hinzufügen“](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Geben Sie **Abschnitt** Pipeline-Konfiguration“ in das Feld **Name der produktionsfremden Pipeline** eine Beschreibung für Ihre produktionsfremde Pipeline ein.
1. Wählen **im Abschnitt** Bereitstellungsoptionen einen der folgenden Bereitstellungs-Trigger aus, die Sie verwenden möchten:

   * **Manuell**: Die Option ermöglicht es Ihnen, die Pipeline manuell zu starten.
   * **Bei Git-Änderungen**: Diese Option startet die Pipeline, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Damit können Sie die Pipeline bei Bedarf immer noch manuell starten.

1. Wählen Sie das **Verhalten bei bedeutenden Metrikfehlern** aus, das Sie verwenden möchten.

   * **Jedes Mal fragen**: Dieses Verhalten ist die Standardeinstellung und erfordert ein manuelles Eingreifen bei einem bedeutenden Fehler.
   * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler abgebrochen. Im Wesentlichen wird damit ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler automatisch fortgesetzt. Im Wesentlichen wird damit eine Benutzerin oder ein Benutzer simuliert, die bzw. der manuell jeden Fehler genehmigt.

1. Klicken Sie auf **Weiter**.

1. Die restlichen Schritte, die Sie zum Abschließen der Konfiguration Ihrer produktionsfremden Pipeline verwenden, hängen vom Typ des Quell-Codes ab, den Sie verwenden möchten.
Wählen Sie auf der Registerkarte **Source** des Dialogfelds **Produktionsfremde Pipeline hinzufügen** aus, welche Art von Code die produktionsfremde Pipeline verarbeiten soll.

   * **[Ich verwende den Full-Stack-Code](#full-stack-code)**
   * **[Ich verwende eine zielgerichtete Bereitstellung](#targeted-deployment)**

   Weitere Informationen zu den Pipeline-Typen finden Sie unter [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).


### Ich verwende den Full-Stack-Code

Eine Pipeline mit Full-Stack-Code stellt gleichzeitig Backend- und Frontend-Code-Builds bereit, die ein oder mehrere AEM-Server-Programme zusammen mit der HTTPD-/Dispatcher-Konfiguration enthalten.

>[!NOTE]
>
>Wenn für die ausgewählte Umgebung bereits eine Pipeline mit Full-Stack-Code vorhanden ist, wird diese Auswahl deaktiviert.

Gehen Sie wie folgt vor, um die Konfiguration der produktionsfremden Full-Stack-Code-Pipeline abzuschließen:

1. Definieren Sie im Abschnitt **Source** Code die folgenden Optionen.

   * **Mögliche Bereitstellungsumgebungen** - Nur verfügbar, wenn Sie eine produktionsfremde Pipeline bearbeiten. Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, für welche Umgebungen sie etwas bereitstellen soll.
   * **Repository**: Wählen Sie in der Dropdown-Liste das Git-Repository aus, das die Pipeline als Quelle verwendet. Cloud Manager erstellt Code aus dem Repository, das Sie hier auswählen.

     >[!TIP]
     > 
     >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

   * **Git-Verzweigung**: Wählen Sie in der Dropdown-Liste die Verzweigung im ausgewählten Repository aus, aus der die Pipeline erstellen soll. Der Standardwert lautet `main`. Die Pipeline verwendet die ausgewählte Verzweigung als Quelle für die Erstellung und Bereitstellung. Klicken Sie bei Bedarf auf **Aktualisieren**, um die Liste der verfügbaren Verzweigungen für das ausgewählte Repository zu aktualisieren. Verwenden Sie diese Option, wenn eine kürzlich erstellte Verzweigung nicht in der Liste angezeigt wird.
   * **Strategie erstellen**
      * **Vollständiger Build**: Erstellt jedes Mal alle Module im Repository.
      * BETA **Smart Build** - Erstellt nur Module, die seit dem letzten Commit geändert wurden.<br>Weitere Informationen über [Verwendung von Smart Build in einer produktionsfremden Pipeline](#about-smart-build-non-production-pipeline).

        >[!IMPORTANT]
        >
        >Smarter Build ist nur für Code-Qualitäts-Pipelines und Bereitstellungs-Pipelines für Entwicklungs-Full-Stack-Code verfügbar.

   * **Konfiguration der Webstufe ignorieren** Kontrollkästchen - Wenn diese Option aktiviert ist, stellt die Pipeline Ihre Webstufenkonfiguration nicht bereit.

1. Im Abschnitt **Pipeline** können Sie, wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, eine Testphase ausführen. Aktivieren Sie die Optionen, die Sie in dieser Phase aktivieren möchten. Wenn keine der Optionen ausgewählt ist, wird die Testphase während der Pipeline-Ausführung nicht angezeigt.

   * **Produktfunktionstests** - Führen Sie [Produktfunktionstests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) mit der Entwicklungsumgebung durch.
   * **Benutzerdefinierte Funktionstests** - Führen Sie [benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) mit der Entwicklungsumgebung durch.
   * **Benutzerdefinierte Benutzeroberflächentests** - Führen Sie [benutzerdefinierte Benutzeroberflächentests](/help/implementing/cloud-manager/ui-testing.md) für benutzerdefinierte Programme aus.
   * **Experience Audit** - Ausführen [Experience Audit](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   ![Full-Stack-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und Sie können jetzt [Pipelines verwalten]&#x200B;(managing-pipe)
lines.md) auf der Karte **Pipelines** auf der Seite **Programmübersicht**.

### Ich verwende eine zielgerichtete Bereitstellung. {#targeted-deployment}

Bei einer zielgerichteten Bereitstellung wird Code nur für ausgewählte Teile Ihrer AEM-Anwendung bereitgestellt. In einer solchen Bereitstellung können Sie auswählen, einen der folgenden Code-Typen **einzuschließen**:

![Zielgerichtete Bereitstellungsoptionen](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment1.png)

<!--
* **Config** - Configure settings for various features in your AEM environment.
  * See [Using Config Pipelines](/help/operations/config-pipeline.md) for a list of supported configurations, which include log forwarding, purge-related maintenance tasks, and various CDN configurations, and to manage them in your repository so they are deployed properly.
  * When running a targeted deployment pipeline, configurations are deployed, provided they are saved to the environment, repository, and branch you defined in the pipeline.
  * At any time, there can only be one config pipeline per environment.
* **Configure Edge Delivery Services config pipeline** - Edge Delivery Configuration Pipelines do not have separate development, staging, and production environments. In AEM as a Cloud Service, changes move through development, stage, and production tiers. In contrast, an Edge Delivery Configuration Pipeline applies its configuration directly to all Edge Delivery Sites domains registered in Cloud Manager. To learn more, see [Add an Edge Delivery Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-edge-delivery-pipeline.md).
-->


* **Frontend-Code** – Konfigurieren Sie JavaScript und CSS für das Frontend Ihrer AEM-Anwendung.
   * Mit Frontend-Pipelines erhalten Frontend-Entwickelnde mehr Unabhängigkeit, und der Entwicklungsprozess kann beschleunigt werden.
   * Weitere Informationen dazu, wie dieser Prozess abläuft und was dabei zu beachten ist, um das volle Potenzial dieses Prozesses auszuschöpfen, finden Sie im Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
* **Web-Stufen-Konfiguration**: Konfigurieren Sie die Dispatcher-Eigenschaften zum Speichern, Verarbeiten und Bereitstellen von Web-Seiten für den Client.
   * Weitere Informationen finden Sie im Dokument [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines).
   * Wenn für die ausgewählte Umgebung bereits eine Code-Pipeline auf Web-Ebene vorhanden ist, wird diese Auswahl deaktiviert.
   * Wenn eine Full-Stack-Pipeline bereits in einer Umgebung bereitgestellt wird, können Sie dennoch eine Web-Stufen-Konfigurations-Pipeline für dieselbe Umgebung erstellen. Dabei ignoriert Cloud Manager die Web-Stufen-Konfiguration in der Full-Stack-Pipeline.

     >[!NOTE]
     >
     >Pipelines auf Web-Ebene und Konfigurations-Pipelines werden bei privaten Repositorys nicht unterstützt. Details sowie eine vollständige Liste der Einschränkungen finden Sie unter [Hinzufügen von privaten Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/private-repositories.md).

<!--
The steps to complete the creation of your non-production, targeted deployment pipeline are the same once you choose a deployment type.

1. Choose which deployment type you require.

![Targeted deployment options](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment.png)

1. Define the **Eligible Deployment Environments**.

   * If your pipeline is a deployment pipeline, you must select to which environments it should deploy.
-->

1. Definieren Sie im Abschnitt **Source** Code die folgenden Optionen:

   * **Repository**: Diese Option definiert, aus welchem GIT-Repository die produktionsfremde Pipeline den Code abrufen soll.

     >[!TIP]
     > 
     >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll. Geben Sie die ersten Zeichen des Verzweigungsnamens und die Funktion zur automatischen Vervollständigung dieses Felds ein. Es werden die entsprechenden auswählbaren Verzweigungen gesucht.
   * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.

<!--
   * **Pipeline** - For front-end non-production pipelines, you have the option to enable **[Experience Audit](/help/implementing/cloud-manager/reports/report-experience-audit.md)**.
   
   ![Config pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config-deployment-experience-audit.png)
-->

1. Wenn Sie das Erlebnis-Audit aktiviert haben, klicken Sie auf **Weiter**, um zur Registerkarte **Erlebnis-Audit** zu gelangen. Dort können Sie die Pfade definieren, die immer in das Erlebnis-Audit einbezogen werden sollen.

   * Wenn Sie **Erlebnis-Audit** aktiviert haben, finden Sie im Dokument [Erlebnis-Audit](/help/implementing/cloud-manager/reports/report-experience-audit.md) Details zur Konfiguration.
   * Wenn nicht, überspringen Sie diesen Schritt.

1. Klicken Sie auf **Speichern**, um die Pipeline zu speichern.

Die Pipeline wird gespeichert, und auf der Seite **Programmübersicht** können Sie nun über die Karte **Pipelines** [Ihre Pipelines verwalten](managing-pipelines.md).


## Über die Verwendung von Smart Build in einer produktionsfremden Pipeline{#about-smart-build-non-production-pipeline}

**Smart Build** in Cloud Manager ist eine optimierte Build-Strategie für produktionsfremde Pipelines. Smartes Erstellen reduziert Build-Zeiten, indem Module zwischengespeichert und nur die Module neu erstellt werden, die seit der letzten erfolgreichen Ausführung geändert wurden. Unveränderte Module werden aus dem Cache wiederverwendet, während nur geänderte Module und ihre Abhängigkeiten neu erstellt werden, was die Effizienz für Workflows für die iterative Entwicklung verbessert.

Smart Build ist derzeit nur für Folgendes verfügbar:

* Code-Qualitäts-Pipelines
* Entwickeln Sie Full-Stack-Bereitstellungs-Pipelines.

>[!NOTE]
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

Im Allgemeinen können Projekte mit vielen unabhängigen Modulen die größte Verbesserung verzeichnen.

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
* Bei Änderungen außerhalb des Abhängigkeitsdiagramms werden Trigger-Neuaufbauten möglicherweise nicht unterstützt.
* Einige Plug-ins sind möglicherweise nicht vollständig mit der Zwischenspeicherung kompatibel.
* Sie können jederzeit wieder zu **Vollständiger Build** wechseln, indem Sie die produktionsfremde Pipeline bearbeiten.

Wenn Sie auf unerwartetes Build-Verhalten stoßen, sollten Sie das Caching für bestimmte Module deaktivieren oder Ihre Build-Strategie vorübergehend auf **Vollständiger Build** umstellen.

### Fehlerbehebung bei Problemen mit Smart Build{#smart-build-troubleshoot}

| Problem | Lösungsvorschläge |
| --- | --- |
| Buildergebnisse sind inkonsistent | ・ Deaktivierung der Zwischenspeicherung für betroffene Module.<br>・ Überprüfen des Plug-in-Verhaltens (insbesondere `exec`/`antrun`-Plug-ins). |
| Keine Leistungsverbesserung | ・ Stellen Sie sicher, dass mehrere Durchgänge stattgefunden haben (Aufwärmen des Cache).<br>・ Prüfen Sie, ob die meisten Module häufig wechseln. |
| Unerwartete Artefakte oder fehlende Änderungen | ・ Überprüfen, ob Änderungen außerhalb des Maven-Abhängigkeits-Trackings liegen<br>・ Verwenden Sie **Vollständiger Build** zur Überprüfung. |

Siehe [Hinzufügen einer produktionsfremden Pipeline](#adding-non-production-pipeline) um die intelligente Erstellung zu aktivieren.











<!--
## Add a non-production pipeline

Once you have set up your program and have at least one environment using the Cloud Manager UI, you are ready to add a non-production pipeline by following these steps.

1. Sign into Cloud Manager at [experience.adobe.com](https://experience.adobe.com).
1. In the **Quick access** section, click **Experience Manager**.
1. In the left side panel, click **Cloud Manager**.
1. Select an organization that you want.
1. On the **My Programs** console, click a program. 

1. Access the **Pipelines** card from the Cloud Manager home screen. Click **+Add** and select **Add Non-Production Pipeline**. 

   ![Add non-production pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/nonprod-pipeline-add1.png)

1. On the **Configuration** tab of the **Add Non-Production Pipeline** dialog, select the type of non-production pipeline you with to add.

   * **Code Quality Pipeline** - Create a pipeline that builds your code, runs unit tests, and evaluates code quality but does NOT deploy.
   * **Deployment Pipeline** - Create a pipeline that builds your code, runs unit tests, evaluates code quality, and deploys to an environment.

   ![Add Non-Production pipeline dialog](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config.png)

1. Provide a **Non-Production Pipeline Name** to identify your pipeline along with the following additional information.

   * **Deployment Trigger** - You have the following options when defining the deployment triggers to start the pipeline.
   
     * **Manual** - Use this option to start the pipeline manually.
     * **On Git Changes** - This option starts the CI/CD pipeline whenever commits are added to the configured Git branch. With this option, you can still start the pipeline manually as required.

1. If you choose to create a **Deployment Pipeline**, you must also define the **Important Metric Failures Behavior**.

   * **Ask every time** - This behavior is the default setting and requires manual intervention on any important failure.
   * **Fail Immediately** - If selected, the pipeline is canceled whenever an important failure occurs. It is essentially emulating a user manually rejecting each failure.
   * **Continue Immediately** - If selected, the pipeline procedes automatically whenever an important failure occurs. It is essentially emulating a user manually approving each failure.

1. Click **Continue**.

1. On the **Source Code** tab of the **Add Non-Production Pipeline** dialog, you must select which type of code the pipeline should process.

   * **[Full Stack Code](#full-stack-code)**
   * **[Targeted deployment](#targeted-deployment)**

See [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) for more information about the types of pipelines.

The steps to complete the creation of your non-production pipeline vary depending on the type of source code you selected. Follow the links above to jump to the next section of this document so you can complete the configuration of your pipeline.

### Full Stack Code

A full-stack code pipeline simultaneously deploys back-end and front-end code builds containing one or more AEM server applications along with HTTPD/Dispatcher configuration.

>[!NOTE]
>
>If a full-stack code pipeline exists for the selected environment, this selection is disabled.

To finish the configuration of the full-stack code non-production pipeline, follow these steps.

1. On the **Source Code** tab, you must define the following options.

   * **Eligible Deployment Environments** - If your pipeline is a deployment pipeline, you must select to which environments it should deploy.
   * **Repository** - This option defines from which git repo that the pipeline should retrieve the code.

   >[!TIP]
   > 
   >See [Adding and Managing Repositories](/help/implementing/cloud-manager/managing-code/managing-repositories.md) so you can learn how to add and manage repositories in Cloud Manager.

   * **Git Branch** - This option defines from which branch in the selected pipeline should retrieve the code.
     * Enter the first few characters of the branch name and the auto-complete feature of this field. It helps you find the matching branches that you can select.
   * **Ignore Web Tier Configuration** - When checked, the pipeline does not deploy your web tier configuration.
   * **Pipeline** - If your pipeline is a deployment pipeline, you can choose to run a testing phase. Check the options that you want to enable in this phase. If none of the options are selected, the testing phase is not displayed during the pipeline's run.

     * **Product Functional Testing** - Execute [product functional tests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) against the development environment.
     * **Custom Functional Testing** - Execute [custom functional tests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) against the development environment.
     * **Custom UI Testing** - Execute [custom UI tests](/help/implementing/cloud-manager/ui-testing.md) for custom applications.
     * **Experience Audit** - Execute [Experience Audit](/help/implementing/cloud-manager/reports/report-experience-audit.md)

   ![Full-stack pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Click **Save**.

The pipeline is saved and you can now [manage your pipelines](managing-pipelines.md) on the **Pipelines** card on the **Program Overview** page.

-->



## Dispatcher-Pakete ausschließen {#exclude-dispatcher-packages}

Wenn Sie möchten, dass Dispatcher-Pakete in Ihrer Pipeline erstellt, aber nicht in den Build-Speicher hochgeladen werden, deaktivieren Sie die Veröffentlichung. Dadurch kann die Laufzeit der Pipeline verkürzt werden.

Fügen Sie Ihrer Projekt-`pom.xml`-Datei die folgende Konfiguration hinzu, um die Veröffentlichung von Dispatcher-Paketen zu deaktivieren. Legen Sie eine Umgebungsvariable im Cloud Manager-Build-Container fest, um zu kennzeichnen, wann Dispatcher-Pakete ignoriert werden sollen. Die Pipeline liest dieses Flag und ignoriert sie entsprechend.

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
