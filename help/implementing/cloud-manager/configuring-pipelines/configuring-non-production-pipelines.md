---
title: Konfigurieren von produktionsfremden Pipelines
description: Erfahren Sie, wie Sie produktionsfremde Pipelines so konfigurieren, dass die Qualität des Codes vor seiner Bereitstellung in Produktionsumgebungen getestet wird.
index: true
exl-id: eba608eb-a19e-4bff-82ff-05860ceabe6e
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '1285'
ht-degree: 80%

---


# Konfigurieren von produktionsfremden Pipelines {#configuring-non-production-pipelines}

Erfahren Sie, wie Sie produktionsfremde Pipelines so konfigurieren, dass die Qualität des Codes vor seiner Bereitstellung in Produktionsumgebungen getestet wird.

Ein Benutzer muss über die **[Bereitstellungsmanager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** Rolle zum Konfigurieren von Nicht-Produktions-Pipelines.

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
   * **[Zielgerichtete Implementierung](#targeted-deployment)**

Siehe [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) für weitere Informationen zu den Pipelinetypen.

Die Schritte zum Erstellen Ihrer produktionsfremden Pipeline variieren je nach ausgewähltem Quellcode. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

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
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md).

   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens und die Funktion zur automatischen Vervollständigung dieses Felds ein. Dies hilft Ihnen, die entsprechenden auswählbaren Verzweigungen zu suchen.
   * **Konfiguration der Web-Stufe ignorieren**: Wenn diese Option aktiviert ist, stellt die Pipeline Ihre Web-Stufenkonfiguration nicht bereit.
   * **Pipeline**: Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, können Sie eine Testphase ausführen. Aktivieren Sie die Optionen, die Sie in dieser Phase aktivieren möchten. Wenn keine der Optionen ausgewählt ist, wird die Testphase während der Pipeline-Ausführung nicht angezeigt.

      * **Funktionstests für das Produkt** – Führen Sie [Produktfunktionstests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing) mit der Entwicklungsumgebung durch.
      * **Benutzerdefinierte Funktionstests** – Führen Sie [benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) gegen die Entwicklungsumgebung durch.
      * **Benutzerdefinierte UI-Tests** – Führen Sie [benutzerdefinierte UI-Tests](/help/implementing/cloud-manager/ui-testing.md) für benutzerdefinierte Anwendungen aus.
      * **Erlebnisprüfung** - Ausführen [Erlebnisprüfung](/help/implementing/cloud-manager/experience-audit-testing.md)

   ![Full-Stack-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-full-stack.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und auf der Karte **Pipelines** auf der Seite **Programmübersicht** können Sie jetzt [Pipelines verwalten](managing-pipelines.md).

### Zielgerichtete Implementierung {#targeted-deployment}

Bei einer zielgerichteten Bereitstellung wird Code nur für ausgewählte Teile Ihrer AEM bereitgestellt. In einer solchen Bereitstellung können Sie auswählen, **Einschließen** einen der folgenden Code-Typen:

* **[Konfiguration](#config)** - Konfigurieren Sie Einstellungen für Ihre AEM-Umgebung, Wartungsaufgaben, CDN-Regeln und mehr.
   * Siehe Dokument . [Traffic-Filterregeln, einschließlich WAF-Regeln](/help/security/traffic-filter-rules-including-waf.md) , um zu erfahren, wie Sie Traffic-Filterregeln in Ihrem Repository verwalten, damit sie ordnungsgemäß bereitgestellt werden.
* **[Frontend-Code](#front-end-code)** - Konfigurieren Sie JavaScript und CSS für das Frontend Ihrer AEM.
   * Mit Frontend-Pipelines erhalten Frontend-Entwicklern mehr Unabhängigkeit und der Entwicklungsprozess kann beschleunigt werden.
   * Weitere Informationen dazu, wie dieser Prozess abläuft und was dabei zu beachten ist, um das volle Potenzial dieses Prozesses auszuschöpfen, finden Sie im Dokument [Entwickeln von Sites mit der Frontend-Pipeline](/help/implementing/developing/introduction/developing-with-front-end-pipelines.md).
* **[Web-Ebene-Konfiguration](#web-tier-config)** - Konfigurieren Sie die Dispatcher-Eigenschaften zum Speichern, Verarbeiten und Bereitstellen von Webseiten für den Client.

>[!NOTE]
>
>* Wenn für die ausgewählte Umgebung bereits eine Web-Stufen-Code-Pipeline vorhanden ist, wird diese Auswahl deaktiviert.
>* Wenn Sie über eine vorhandene Full-Stack-Pipeline verfügen, die in einer Umgebung bereitgestellt wird, wird beim Erstellen einer Web-Stufen-Konfigurations-Pipeline für dieselbe Umgebung die vorhandene Web-Stufen-Konfiguration in der Full-Stack-Pipeline ignoriert.
> * Es kann immer nur eine Konfigurationspipeline pro Umgebung geben.

Die Schritte zum Erstellen Ihrer nicht produktionsbezogenen, zielgerichteten Implementierungs-Pipeline sind dieselben, wenn Sie einen Bereitstellungstyp auswählen.

1. Wählen Sie den benötigten Bereitstellungstyp aus.

![Zielgerichtete Bereitstellungsoptionen](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-targeted-deployment.png)

1. Definieren Sie die **Förderfähige Bereitstellungsumgebungen**.

   * Wenn es sich bei Ihrer Pipeline um eine Bereitstellungs-Pipeline handelt, müssen Sie auswählen, in welchen Umgebungen sie bereitgestellt werden soll.

1. under **Quellcode**, definieren Sie die folgenden Optionen:

   * **Repository**: Diese Option legt fest, aus welchem Git-Repository die Pipeline den Code abrufen soll.

   >[!TIP]
   > 
   >Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/cloud-manager-repositories.md).

   * **Git-Verzweigung**: Mit dieser Option wird festgelegt, von welcher Verzweigung in der ausgewählten Pipeline der Code abgerufen werden soll.
      * Geben Sie die ersten Zeichen des Verzweigungsnamens und die Funktion zur automatischen Vervollständigung dieses Felds ein. Es werden die entsprechenden auswählbaren Verzweigungen gesucht.
   * **Speicherort des Codes**: Mit dieser Option wird der Pfad in der Verzweigung des ausgewählten Repositorys festgelegt, aus dem die Pipeline den Code abrufen soll.

   ![Config-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/non-prod-pipeline-config-deployment.png)

1. Klicken Sie auf **Speichern**.

Die Pipeline wird gespeichert und auf der Karte **Pipelines** auf der Seite **Programmübersicht** können Sie jetzt [Pipelines verwalten](managing-pipelines.md).

Beim Ausführen einer zielgerichteten Bereitstellungs-Pipeline Konfigurationen [wie WAF-Konfigurationen](/help/security/traffic-filter-rules-including-waf.md) wird bereitgestellt, sofern sie in der Umgebung, im Repository und in der Verzweigung gespeichert werden, die Sie in der Pipeline definiert haben.

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
