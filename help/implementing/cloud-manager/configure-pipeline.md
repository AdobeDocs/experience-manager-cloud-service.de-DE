---
title: Konfigurieren der CI/CD-Pipeline – Cloud Services
description: Konfigurieren der CI/CD-Pipeline – Cloud Services
translation-type: tm+mt
source-git-commit: 9cfdf421db39dd08e8b772241f1f750fb73375b8
workflow-type: tm+mt
source-wordcount: '770'
ht-degree: 72%

---


# Konfigurieren der CI/CD-Pipeline {#configure-ci-cd-pipeline}

In Cloud Manager gibt es zwei Arten von Pipeline:

* **Produktionsrohre**:
Eine Produktions-Pipeline kann nur hinzugefügt werden, wenn eine Produktions- und Stage-Umgebung erstellt wurde. Weitere Informationen finden Sie im Abschnitt [Einrichten der Pipeline](configure-pipeline.md#setting-up-the-pipeline) .

* **Produktionsfremde Pipelines**:

   Auf der Seite &quot; **Übersicht** &quot;der Benutzeroberfläche von Cloud Manager kann eine Pipeline für Nicht-Produktion hinzugefügt werden. Weitere Informationen finden Sie unter [Nicht-Produktion- und Nur-Code-Qualitätsrohre](configure-pipeline.md#non-production-pipelines) .

## Wissenswertes zum Ablauf {#understanding-the-flow}

Sie können Ihre Pipeline über die Kachel **Pipeline-Einstellungen** in der [!UICONTROL Cloud Manager]-Benutzeroberfläche konfigurieren.

Der Bereitstellungsmanager ist für die Einrichtung der Pipeline verantwortlich. Wählen Sie hierfür zunächst eine Verzweigung im **Git-Repository** aus.

Zur Konfiguration der Pipeline muss der Benutzer:

* den Auslöser festlegen, der die Pipeline startet,
* Parameter zur Steuerung der Produktionsimplementierung festlegen,
* Leistungstestparameter konfigurieren.

## Einrichten der Pipeline {#setting-up-the-pipeline}

>[!CAUTION]
>
>Die Pipeline kann erst eingerichtet werden, wenn die Erstellung eines Programms abgeschlossen ist und das Git-Repository mindestens eine Verzweigung hat.

Bevor Sie Code bereitstellen, müssen Sie Ihre Pipelineeinstellungen über [!UICONTROL Cloud Manager] konfigurieren.

>[!NOTE]
>
>Sie können die Pipelineeinstellungen nach der Ersteinrichtung ändern.

## Konfigurieren der Pipeline-Einstellungen in [!UICONTROL Cloud Manager] {#configuring-the-pipeline-settings-from-cloud-manager}

Sobald Sie Ihr Programm eingerichtet haben und über mindestens eine Umgebung mit der [!UICONTROL Cloud Manager]-Benutzeroberfläche verfügen, können Sie Ihre Implementierungs-Pipeline einrichten.

Führen Sie folgende Schritte aus, um das Verhalten und die Voreinstellungen für Ihre Pipeline zu konfigurieren:

1. Klicken Sie auf **Pipeline einrichten**, um Ihre Pipeline einzurichten und zu konfigurieren.

   ![](assets/set-up-pipeline1.png)

1. Der Bildschirm **Pipeline einrichten** wird angezeigt. Wählen Sie die Verzweigung aus und klicken Sie auf **Weiter**.

   ![](assets/setup-pipeline-1.png)

1. Konfigurieren Sie die Implementierungsoptionen.

   ![](assets/setup-pipeline-2.png)

   Sie können den Auslöser definieren, mit dem die Pipeline gestartet wird:

   * **Manuell**: Die Pipeline wird über die Benutzeroberfläche manuell gestartet.
   * **Zu Git-Änderungen**: Startet die CI/CD-Pipeline, wenn zur konfigurierten Git-Verzweigung Commits hinzugefügt werden. Wenn Sie diese Option auswählen, können Sie die Pipeline weiterhin manuell starten.

   Bei der Einrichtung oder Bearbeitung der Pipeline kann der Implementierungsmanager festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates (Test der Code-Qualität, Sicherheitstest und Leistungstest) ein wichtiger Fehler auftritt.

   Das ist für Kunden nützlich, die die Prozesse stärker automatisieren möchten. Die verfügbaren Optionen sind:

   * **Jedes Mal fragen**: Das ist die Standardeinstellung und erfordert manuelles Eingreifen bei einem wichtigen Fehler.
   * **Schlagen sofort fehl**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler abgebrochen. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem wichtigen Fehler automatisch fortgesetzt. Damit wird im Grunde ein Benutzer simuliert, der manuell jeden Fehler genehmigt.


1. Die Einstellungen für die Produktions-Pipeline enthalten eine dritte Registerkarte mit der Bezeichnung **Content Audit**.

   Diese Option enthält eine Tabelle der URL-Pfade, die immer im Content Audit enthalten sein sollten. Der Benutzer kann manuell einen einzuschließenden URL-Pfad eingeben. Es können maximal 25 Zeilen eingefügt werden. Wenn der Benutzer in diesem Abschnitt keine Seiten übermittelt hat, wird die Homepage der Site standardmäßig in die Inhaltsprüfung einbezogen.

   >[!NOTE]
   > Die konfigurierten Seiten werden an den Dienst gesendet und gemäß den Tests für Leistung, Barrierefreiheit, SEO (Suchmaschinenoptimierung), Best Practice und PWA (Progressive Web App) bewertet.

   Weitere Informationen finden Sie unter [Die Ergebnisse](/help/implementing/developing/introduction/understand-test-results.md#content-audit-testing) der Inhaltsprüfung.

   ![](assets/content-audit-1.png)

   Klicken Sie auf **Hinzufügen Überschreiben** der neuen Seite, um einen URL-Pfad anzugeben, der in die Content-Prüfung aufgenommen werden soll. Klicken Sie nach dem Hinzufügen des Pfads auf **Speichern**.

   ![](assets/content-audit-2.png)

1. Klicken Sie im Bildschirm &quot;Pipeline **bearbeiten&quot;auf** Speichern **** . Auf der Seite **Übersicht** wird nun die Karte **Ihr Programm bereitstellen** angezeigt. Klicken Sie auf **Bereitstellen**, um das Programm bereitzustellen.

   ![](assets/configure-pipeline5.png)


## Produktionsfremde Pipelines und Pipelines für Tests der Codequalität {#non-production-pipelines}

Zusätzlich zur Haupt-Pipeline, die für die Staging- und Produktionsumgebung bereitgestellt wird, können Kunden weitere Pipelines einrichten, die als **produktionsfremde Pipelines** bezeichnet werden. Diese Pipelines führen immer die Schritte Build-Erstellung und Tests der Codequalität aus. Sie können optional auch für die Adobe Managed Services-Umgebung bereitgestellt werden.

Auf dem Startbildschirm werden diese Pipelines in einer neuen Karte aufgeführt:

1. Greifen Sie im Cloud Manager-Startbildschirm auf die Kachel **Nicht-Produktions-Pipelines** zu.

   ![](assets/configure-pipeline6.png)

1. Klicken Sie auf **Hinzufügen**, um den Pipeline-Namen, den Pipeline-Typ und die Git-Verzweigung anzugeben.

   Außerdem können Sie in den Pipeline-Optionen Implementierungsauslöser und das Verhalten bei wichtigen Fehlern festlegen.

   ![](assets/non-prod-pipe1.png)

1. Klicken Sie auf **Speichern**, damit die Pipeline (wie unten dargestellt) auf der Karte auf dem Startbildschirm mit drei Aktionen angezeigt wird:

   ![](assets/configure-pipeline8.png)

   * **Bearbeiten**: Ermöglicht die Bearbeitung der Pipeline-Einstellungen.
   * **Build**: Wechselt zur Ausführungsseite, von der die Pipeline ausgeführt werden kann.
   * **Git verwalten**: Ermöglicht es dem Benutzer, die für den Zugriff auf das Cloud Manager-Git-Repository erforderlichen Informationen abzurufen.

## Die nächsten Schritte {#the-next-steps}

Nachdem die Konfiguration der Pipeline abgeschlossen ist, müssen Sie Ihren Code bereitstellen.

Weitere Informationen finden Sie unter [Bereitstellen Ihres Codes](deploy-code.md).
