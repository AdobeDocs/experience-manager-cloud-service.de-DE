---
title: Bereitstellen des Codes – Cloud Services
description: Bereitstellen des Codes – Cloud Services
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: 782035708467693ec7648b1fd701c329a0b5f7c8
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 90%

---

# Bereitstellen des Codes {#deploy-your-code}

## Bereitstellen von Code mit Cloud Manager in AEM als Cloud Service {#deploying-code-with-cloud-manager}

Sobald Sie Ihre Produktions-Pipeline (Repository, Umgebung und Testumgebung) konfiguriert haben, können Sie Ihren Code bereitstellen.

1. Klicken Sie in Cloud Manager auf **Bereitstellen**, um den Implementierungsprozess zu starten.

   ![](assets/deploy-code1.png)


1. Der Bildschirm **Pipeline-Ausführung** wird angezeigt.

   Klicken Sie auf **Erstellen**, um den Prozess zu starten.

   ![](assets/deploy-code2.png)

1. Der vollständige Build-Prozess stellt Ihren Code bereit.

   Der Build-Prozess umfasst die folgenden Phasen:

   1. Staging-Implementierung
   1. Staging-Tests
   1. Produktionsimplementierung

   >[!NOTE]
   >
   >Außerdem können Sie die Schritte der verschiedenen Implementierungsprozesse überprüfen, indem Sie die Protokolle anzeigen oder die Ergebnisse anhand der Testkriterien überprüfen.

   Die **Staging-Implementierung** umfasst die folgenden Schritte:

   * Validierung: Dieser Schritt stellt sicher, dass die Pipeline so konfiguriert ist, dass die derzeit verfügbaren Ressourcen verwendet werden. So wird z. B. überprüft, ob die konfigurierte Verzweigung vorhanden ist und die Umgebungen verfügbar sind.
   * Build- und Komponententests: Dieser Schritt führt einen containerisierten Build-Prozess aus. Siehe [Details zur Build-Umgebung](/help/onboarding/getting-access-to-aem-in-cloud/build-environment-details.md), um weitere Informationen zur Build-Umgebung zu erhalten.
   * Codescan: Dieser Schritt bewertet die Qualität Ihres Anwendungs-Codes. Weitere Informationen zum Testprozess finden Sie unter [Tests der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md).
   * Bilder erstellen: Dieser Schritt enthält eine Protokolldatei aus dem Prozess, der zum Erstellen von Bildern verwendet wird. Dieser Prozess ist für die Umwandlung der vom Build-Schritt erstellten Inhalts- und Dispatcher-Pakete in Docker-Bilder und die Kubernetes-Konfiguration verantwortlich.
   * Bereitstellen in der Staging-Umgebung

      ![](assets/stage-deployment.png)
   **Staging-Tests** umfassen die folgenden Schritte:

   * **Produktfunktionstests**: Cloud Manager-Pipeline-Ausführungen unterstützen die Ausführung von Tests, die für die Staging-Umgebung ausgeführt werden.
Weitere Informationen finden Sie unter [Produktfunktionstests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing).

   * **Benutzerdefinierte Funktionstests**: Dieser Schritt in der Pipeline ist immer vorhanden und kann nicht übersprungen werden. Wenn jedoch keine Test-JAR vom Build erzeugt wird, wird der Test standardmäßig erfolgreich durchgeführt.\
      Weitere Informationen finden Sie unter [Benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing).

   * **Benutzerdefinierte UI-Tests**: Dieser Schritt ist eine optionale Funktion, mit der unsere Kunden Benutzeroberflächentests für ihre Anwendungen erstellen und automatisch ausführen können. Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl in Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen).
Weitere Informationen finden Sie unter [Benutzerdefinierte UI-Tests](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/functional-testing.html?lang=en#custom-ui-testing) .


   * **Experience Audit**: Dieser Schritt in der Pipeline ist immer vorhanden und kann nicht übersprungen werden. Bei Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests, die die Prüfungen ausführen, ein Schritt zur Erlebnisprüfung eingefügt. Die konfigurierten Seiten werden an den Service gesendet und ausgewertet. Die Ergebnisse sind informativ und ermöglichen es dem Benutzer, die Bewertungen sowie die Änderung zwischen den aktuellen und vorherigen Bewertungen zu prüfen. Diese Erkenntnisse sind nützlich, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Implementierung eingeführt wird.
Weitere Informationen finden Sie unter [Verstehen der Ergebnisse von Erlebnisprüfungen](/help/implementing/cloud-manager/experience-audit-testing.md).

      ![](assets/stage-testing.png)





## Implementierungsprozess {#deployment-process}

Im folgenden Abschnitt wird beschrieben, wie AEM- und Dispatcher-Pakete in der Staging- und Produktionsphase bereitgestellt werden.

Cloud Manager lädt alle beim Build-Prozess generierten target/*.zip-Dateien in einen Speicherort hoch. Diese Artefakte werden in der Pipeline-Bereitstellungsphase von diesem Speicherort abgerufen.

Wenn Cloud Manager in produktionsfremden Topologien bereitgestellt wird, besteht das Ziel darin, die Implementierung so schnell wie möglich abzuschließen. Daher werden die Artefakte wie folgt auf allen Knoten gleichzeitig bereitgestellt:

1. Cloud Manager bestimmt für jedes Artefakt, ob es sich um ein AEM- oder Dispatcher-Paket handelt.
1. Cloud Manager entfernt alle Dispatcher aus dem Lastenausgleich, um die Umgebung während der Implementierung zu isolieren.

   Sofern nicht anders konfiguriert, können Sie die Load-Balancer-Änderungen in Entwicklungs- und Staging-Umgebungen überspringen, d. h. das Trennen und Anfügen in beiden Nicht-Produktions-Pipelines bei Entwicklungsumgebungen und in der Produktions-Pipeline bei Staging-Umgebungen.

   >[!NOTE]
   >
   >Diese Funktion wird voraussichtlich hauptsächlich von 1-1-1-Kunden verwendet.

1. Jedes AEM-Artefakt wird über Package Manager-APIs in jeder AEM-Instanz bereitgestellt, wobei Paketabhängigkeiten die Implementierungsreihenfolge bestimmen.

   Weitere Informationen dazu, wie Sie mit Paketen neue Funktionen installieren, Inhalte zwischen Instanzen übertragen und Repository-Inhalte sichern können, finden Sie unter „Arbeiten mit Paketen“.

   >[!NOTE]
   >
   >Alle AEM-Artefakte werden für Autor und Publisher bereitgestellt. Wenn knotenspezifische Konfigurationen erforderlich sind, sollten Ausführungsmodi genutzt werden. Weitere Informationen dazu, wie Sie mit Ausführungsmodi die AEM-Instanz für einen bestimmten Zweck anpassen können, finden Sie unter „Ausführungsmodi“.

1. Das Dispatcher-Artefakt wird wie folgt für jeden Dispatcher bereitgestellt:

   1. Aktuelle Konfigurationen werden gesichert und in einen temporären Speicherort kopiert.
   1. Alle Konfigurationen (mit Ausnahme der unveränderlichen Dateien) werden gelöscht. Weitere Informationen finden Sie unter „Verwalten von Dispatcher-Konfigurationen“. Mit diesem Schritt werden die Verzeichnisse gelöscht, damit keine verwaisten Dateien übrig bleiben.
   1. Das Artefakt wird in das `httpd`-Verzeichnis extrahiert. Unveränderliche Dateien werden nicht überschrieben. Alle Änderungen an unveränderlichen Dateien in Ihrem Git-Repository werden bei der Implementierung ignoriert. Diese Dateien bilden den Kern des AMS Dispatcher-Frameworks und können nicht geändert werden.
   1. Apache führt einen Konfigurationstest durch. Wenn keine Fehler gefunden werden, wird der Service neu geladen. Falls ein Fehler auftritt, werden die Konfigurationen aus der Sicherung wiederhergestellt, der Service wird neu geladen und der Fehler wird an Cloud Manager gemeldet.
   1. Jeder in der Pipelinekonfiguration angegebene Pfad wird ungültig oder aus dem Dispatcher-Cache entfernt.

   >[!NOTE]
   >
   >Cloud Manager geht davon aus, dass das Dispatcher-Artefakt alle Dateien enthält. Alle Dispatcher-Konfigurationsdateien müssen im Git-Repository vorhanden sein. Fehlende Dateien oder Ordner führen zu Implementierungsfehlern.

1. Nach der erfolgreichen Implementierung aller AEM- und Dispatcher-Pakete auf allen Knoten werden die Dispatcher wieder zum Lastenausgleich hinzugefügt und die Implementierung wird abgeschlossen.

   >[!NOTE]
   >
   >Sie können Änderungen am Load-Balancer in Entwicklungs- und Staging-Implementierungen überspringen, d. h. das Trennen und Anfügen in beiden produktionsfremden Pipelines bei Entwicklungsumgebungen und in der Produktions-Pipeline bei Staging-Umgebungen.

### Implementierung in der Produktionsphase {#deployment-production-phase}

Der Prozess zur Bereitstellung auf Produktionstopologien unterscheidet sich geringfügig, um die Auswirkungen auf AEM Sites-Besucher zu minimieren.

Produktionsimplementierungen nutzen im Allgemeinen die oben beschriebenen Schritte, aber auf rollierende Weise:

1. AEM-Pakete werden für den Autor bereitgestellt
1. dispatcher1 wird aus dem Lastenausgleich gelöst
1. AEM-Pakete werden in publish1 und das Dispatcher-Paket in dispatcher1 bereitgestellt und der Dispatcher-Cache geleert
1. dispatcher1 wird in den Lastenausgleich zurückgesetzt
1. Sobald dispatcher1 wieder aktiv ist, wird dispatcher2 aus dem Lastenausgleich entfernt
1. AEM-Pakete werden in publish2 und das Dispatcher-Paket in dispatcher2 bereitgestellt und der Dispatcher-Cache geleert
1. dispatcher2 wird in den Lastenausgleich zurückgesetzt
Dieser Vorgang wird fortgesetzt, bis die Implementierung alle Publisher und Dispatcher in der Topologie erreicht hat.
