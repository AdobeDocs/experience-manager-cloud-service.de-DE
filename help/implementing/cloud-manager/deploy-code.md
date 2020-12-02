---
title: Bereitstellen des Codes – Cloud Services
description: Bereitstellen des Codes – Cloud Services
translation-type: tm+mt
source-git-commit: e1bf1a42ff81352c4946a2e5e5c731255234d5f3
workflow-type: tm+mt
source-wordcount: '985'
ht-degree: 85%

---


# Bereitstellen des Codes {#deploy-your-code}

## Bereitstellen von Code mit Cloud Manager {#deploying-code-with-cloud-manager}

Sobald Sie Ihre Produktions-Pipeline (Repository, Umgebung und Testumgebung) konfiguriert haben, können Sie Ihren Code bereitstellen.

1. Klicken Sie in Cloud Manager auf **Bereitstellen**, um den Bereitstellungsprozess zu starten.

   ![](assets/deploy-code1.png)


1. Der Bildschirm **Pipeline-Ausführung** wird angezeigt.

   Klicken Sie auf **Erstellen**, um den Prozess zu starten.

   ![](assets/deploy-code2.png)

1. Der vollständige Build-Prozess stellt Ihren Code bereit.

   Der Build-Prozess umfasst die folgenden Phasen:

   1. Staging-Bereitstellung
   1. Staging-Tests
   1. Produktionsbereitstellung

   >[!NOTE]
   >
   >Außerdem können Sie die Schritte der verschiedenen Bereitstellungsprozesse überprüfen, indem Sie die Protokolle anzeigen oder die Ergebnisse anhand der Testkriterien überprüfen.

   Die **Staging-Bereitstellung** umfasst die folgenden Schritte:

   * Validierung: Dieser Schritt stellt sicher, dass die Pipeline so konfiguriert ist, dass die derzeit verfügbaren Ressourcen verwendet werden. So wird z. B. überprüft, ob die konfigurierte Verzweigung vorhanden ist und die Umgebungen verfügbar sind.
   * Build- und Komponententests: Dieser Schritt führt einen containerisierten Build-Prozess aus. Einzelheiten zur Build-Umgebung finden Sie unter [Build Umgebung Details](/help/onboarding/getting-access-to-aem-in-cloud/build-environment-details.md).
   * Code-Scan: Dieser Schritt bewertet die Qualität Ihres Anwendungs-Codes. Weitere Informationen zum Testprozess finden Sie unter [Code Quality Testing](/help/implementing/cloud-manager/code-quality-testing.md).
   * Bilder erstellen: Dieser Schritt enthält eine Protokolldatei aus dem Prozess, der zum Erstellen von Bildern verwendet wird. Dieser Prozess ist für die Umwandlung der vom Build-Schritt erstellten Inhalts- und Dispatcher-Pakete in Docker-Bilder und die Kubernetes-Konfiguration verantwortlich.
   * Bereitstellen in der Staging-Umgebung

      ![](assets/stage-deployment.png)
   **Staging-Tests** umfassen die folgenden Schritte:

   * Produktfunktionstests: Cloud Manager-Pipeline-Hinrichtungen unterstützen die Ausführung von Tests, die mit der Umgebung der Phase ausgeführt werden.
Weitere Informationen finden Sie unter [Produktfunktionstests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing).

   * Benutzerdefinierte Funktionstests: Dieser Schritt in der Pipeline ist immer vorhanden und kann nicht übersprungen werden. Wenn jedoch keine Test-JAR vom Build erzeugt wird, wird der Test standardmäßig erfolgreich durchgeführt.\
      Weitere Informationen finden Sie unter [Benutzerspezifische Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing).

   * Erlebnis-Prüfung: Dieser Schritt in der Pipeline ist immer vorhanden und kann nicht übersprungen werden. Bei der Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests, die die Prüfungen ausführen, ein Erlebnis-Prüfschritt eingefügt. Die konfigurierten Seiten werden an den Dienst gesendet und ausgewertet. Die Ergebnisse sind informativ und ermöglichen es dem Benutzer, die Bewertungen sowie die Unterschiede zwischen aktuellen und vorherigen Bewertungen anzuzeigen. Diese Erkenntnis ist nützlich, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Implementierung eingeführt wird.
Weitere Informationen finden Sie unter [Die Ergebnisse der Erlebnisprüfung](/help/implementing/cloud-manager/experience-audit-testing.md).

      ![](assets/testing-tab.png)





## Bereitstellungsprozess {#deployment-process}

Im folgenden Abschnitt wird beschrieben, wie AEM- und Dispatcher-Pakete in der Staging- und Produktionsphase bereitgestellt werden.

Cloud Manager lädt alle beim Build-Prozess generierten target/*.zip-Dateien in einen Speicherort hoch. Diese Artefakte werden in der Pipeline-Bereitstellungsphase von diesem Speicherort abgerufen.

Wenn Cloud Manager in produktionsfremden Topologien bereitgestellt wird, besteht das Ziel darin, die Bereitstellung so schnell wie möglich abzuschließen. Daher werden die Artefakte wie folgt auf allen Knoten gleichzeitig bereitgestellt:

1. Cloud Manager bestimmt für jedes Artefakt, ob es sich um ein AEM- oder Dispatcher-Paket handelt.
1. Cloud Manager entfernt alle Dispatcher aus dem Lastenausgleich, um die Umgebung während der Bereitstellung zu isolieren.

   Sofern nicht anders konfiguriert, können Sie die Load-Balancer-Änderungen in Entwicklungs- und Staging-Umgebungen überspringen, d. h. das Trennen und Anfügen in beiden Nicht-Produktions-Pipelines bei Entwicklungsumgebungen und in der Produktions-Pipeline bei Staging-Umgebungen.

   >[!NOTE]
   >
   >Diese Funktion wird voraussichtlich hauptsächlich von 1-1-1-Kunden verwendet.

1. Jedes AEM-Artefakt wird über Package Manager-APIs in jeder AEM-Instanz bereitgestellt, wobei Paketabhängigkeiten die Bereitstellungsreihenfolge bestimmen.

   Weitere Informationen dazu, wie Sie mit Paketen neue Funktionen installieren, Inhalte zwischen Instanzen übertragen und Repository-Inhalte sichern können, finden Sie unter „Arbeiten mit Paketen“.

   >[!NOTE]
   >
   >Alle AEM-Artefakte werden für Autor und Publisher bereitgestellt. Die Ausführungsmodi sollten genutzt werden, wenn knotenspezifische Konfigurationen erforderlich sind. Weitere Informationen dazu, wie Sie mit den Ausführungsmodi Ihre AEM Instanz für einen bestimmten Zweck einstellen können, finden Sie unter Ausführungsmodi.

1. Das Dispatcher-Artefakt wird wie folgt für jeden Dispatcher bereitgestellt:

   1. Aktuelle Konfigurationen werden gesichert und in einen temporären Speicherort kopiert.
   1. Alle Konfigurationen (mit Ausnahme der unveränderlichen Dateien) werden gelöscht. Weitere Informationen finden Sie unter „Verwalten von Dispatcher-Konfigurationen“. Mit diesem Schritt werden die Verzeichnisse gelöscht, damit keine verwaisten Dateien übrig bleiben.
   1. Das Artefakt wird in das `httpd`-Verzeichnis extrahiert. Unveränderliche Dateien werden nicht überschrieben. Alle Änderungen an unveränderlichen Dateien in Ihrem Git-Repository werden bei der Bereitstellung ignoriert. Diese Dateien bilden den Kern des AMS Dispatcher-Frameworks und können nicht geändert werden.
   1. Apache führt einen Konfigurationstest durch. Wenn keine Fehler gefunden werden, wird der Dienst neu geladen. Falls ein Fehler auftritt, werden die Konfigurationen aus der Sicherung wiederhergestellt, der Dienst wird neu geladen und der Fehler wird an Cloud Manager gemeldet.
   1. Jeder in der Pipelinekonfiguration angegebene Pfad wird ungültig oder aus dem Dispatcher-Cache entfernt.

   >[!NOTE]
   >
   >Cloud Manager geht davon aus, dass das Dispatcher-Artefakt alle Dateien enthält. Alle Dispatcher-Konfigurationsdateien müssen im Git-Repository vorhanden sein. Fehlende Dateien oder Ordner führen zu Bereitstellungsfehlern.

1. Nach der erfolgreichen Bereitstellung aller AEM- und Dispatcher-Pakete auf allen Knoten werden die Dispatcher wieder zum Lastenausgleich hinzugefügt und die Bereitstellung wird abgeschlossen.

   >[!NOTE]
   >
   >Sie können Änderungen am Load-Balancer in Entwicklungs- und Staging-Implementierungen überspringen, d. h. das Trennen und Anfügen in beiden produktionsfremden Pipelines bei Entwicklungsumgebungen und in der Produktions-Pipeline bei Staging-Umgebungen.

### Bereitstellung in der Produktionsphase {#deployment-production-phase}

Der Prozess zur Bereitstellung auf Produktionstopologien unterscheidet sich geringfügig, um die Auswirkungen auf AEM Sites-Besucher zu minimieren.

Produktionsbereitstellungen nutzen im Allgemeinen die oben beschriebenen Schritte, aber auf rollierende Weise:

1. AEM-Pakete werden für den Autor bereitgestellt
1. dispatcher1 wird aus dem Lastenausgleich gelöst
1. AEM-Pakete werden in publish1 und das Dispatcher-Paket in dispatcher1 bereitgestellt und der Dispatcher-Cache geleert
1. dispatcher1 wird in den Lastenausgleich zurückgesetzt
1. Sobald dispatcher1 wieder aktiv ist, wird dispatcher2 aus dem Lastenausgleich entfernt
1. AEM-Pakete werden in publish2 und das Dispatcher-Paket in dispatcher2 bereitgestellt und der Dispatcher-Cache geleert
1. dispatcher2 wird in den Lastenausgleich zurückgesetzt
Dieser Vorgang wird fortgesetzt, bis die Bereitstellung alle Publisher und Dispatcher in der Topologie erreicht hat.


