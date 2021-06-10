---
title: Bereitstellen des Codes – Cloud Services
description: Bereitstellen des Codes – Cloud Services
exl-id: 2c698d38-6ddc-4203-b499-22027fe8e7c4
source-git-commit: 64023bbdccd8d173b15e3984d0af5bb59a2c1447
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 93%

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
   * Codescan: Dieser Schritt bewertet die Qualität Ihres Programm-Codes. Weitere Informationen zum Testprozess finden Sie unter [Tests der Code-Qualität](/help/implementing/cloud-manager/code-quality-testing.md).
   * Bilder erstellen: Dieser Schritt enthält eine Protokolldatei aus dem Prozess, der zum Erstellen von Bildern verwendet wird. Dieser Prozess ist für die Umwandlung der vom Build-Schritt erstellten Inhalts- und Dispatcher-Pakete in Docker-Bilder und die Kubernetes-Konfiguration verantwortlich.
   * Bereitstellen in der Staging-Umgebung

      ![](assets/stage-deployment.png)
   **Staging-Tests** umfassen die folgenden Schritte:

   * **Produktfunktionstests**: Cloud Manager-Pipeline-Ausführungen unterstützen die Ausführung von Tests, die für die Staging-Umgebung ausgeführt werden.
Weitere Informationen finden Sie unter [Produktfunktionstests](/help/implementing/cloud-manager/functional-testing.md#product-functional-testing).

   * **Benutzerdefinierte Funktionstests**: Dieser Schritt in der Pipeline ist immer vorhanden und kann nicht übersprungen werden. Wenn jedoch keine Test-JAR vom Build erzeugt wird, wird der Test standardmäßig erfolgreich durchgeführt.\
      Weitere Informationen finden Sie unter [Benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing).

   * **Benutzerdefinierte Benutzeroberflächentests**: Dieser Schritt ist eine optionale Funktion, mit der unsere Kunden Benutzeroberflächentests für ihre Programme erstellen und automatisch ausführen können. Benutzeroberflächentests sind Selenium-basierte Tests, die in einem Docker-Image verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen (z. B. Java und Maven, Node und WebDriver.io oder alle anderen Frameworks und Technologien, die auf Selenium aufbauen).
Weitere Informationen finden Sie unter [Benutzerdefinierte Benutzeroberflächentests](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/test-results/functional-testing.html?lang=de#custom-ui-testing).


   * **Erlebnisprüfung**: Dieser Schritt in der Pipeline ist immer vorhanden und kann nicht übersprungen werden. Bei Ausführung einer Produktions-Pipeline wird nach benutzerdefinierten Funktionstests, die die Prüfungen ausführen, ein Schritt zur Erlebnisprüfung eingefügt. Die konfigurierten Seiten werden an den Service gesendet und ausgewertet. Die Ergebnisse sind informativ und ermöglichen es dem Benutzer, die Bewertungen sowie die Änderung zwischen den aktuellen und vorherigen Bewertungen zu prüfen. Diese Erkenntnisse sind nützlich, um festzustellen, ob es eine Regression gibt, die mit der aktuellen Implementierung eingeführt wird.
Weitere Informationen finden Sie unter [Verstehen der Ergebnisse von Erlebnisprüfungen](/help/implementing/cloud-manager/experience-audit-testing.md).

      ![](assets/stage-testing.png)





## Implementierungsprozess {#deployment-process}

Alle Cloud Service-Bereitstellungen werden fortlaufend verarbeitet, um Ausfallzeiten zu vermeiden. Weitere Informationen finden Sie unter [Funktionsweise von rollierenden Bereitstellungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/overview.html#how-rolling-deployments-work) .

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
