---
title: Funktionstests
description: Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den Bereitstellungsprozess von AEM as a Cloud Service integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen.
exl-id: 7eb50225-e638-4c05-a755-4647a00d8357
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 100%

---


# Funktionstests {#functional-testing}

>[!CONTEXTUALHELP]
>id="aemcloud_nonbpa_functionaltesting"
>title="Funktionstests"
>abstract="Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den Bereitstellungsprozess von AEM as a Cloud Service integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen."

Erfahren Sie mehr über die drei verschiedenen Arten von Funktionstests, die in den [Bereitstellungsprozess von AEM as a Cloud Service](/help/implementing/cloud-manager/deploy-code.md) integriert sind, um die Qualität und Zuverlässigkeit Ihres Codes sicherzustellen.

## Anwendungsbereich

Die funktionalen Testschritte in der Cloud Manager-Pipeline sollen sicherstellen, dass die wesentlichen Funktionen Ihrer Applikation erwartungsgemäß funktionieren.

Diese Testphase ist die letzte Stufe automatisierter Tests vor der Bereitstellung Ihres Codes in der Produktion.

Funktionstests sollten andere Teststrategien wie Komponententests, Integrationstests oder Funktionstests, 
die außerhalb der Pipeline-Ausführung in Cloud Manager durchgeführt werden, nicht ersetzen, sondern ergänzen und erweitern.

## Übersicht {#overview}

Es gibt drei verschiedene Arten von Funktionstests in AEM as a Cloud Service.

* [Funktionstests für das Produkt](#product-functional-testing)
* [Benutzerdefinierte Funktionstests](#custom-functional-testing)
* [Benutzerdefinierte Benutzeroberflächentests](#custom-ui-testing)

Für alle Funktionstests können die detaillierten Ergebnisse der Tests als `.zip`-Datei heruntergeladen werden, indem Sie im Build-Übersichtsbildschirm als Teil des [Bereitstellungsprozesses](/help/implementing/cloud-manager/deploy-code.md) die Schaltfläche **Build-Protokoll herunterladen** verwenden.

Diese Protokolle enthalten nicht die Protokolle des eigentlichen AEM-Laufzeitprozesses. Weitere Details zum Zugriff auf diese Protokolle finden Sie unter [Zugreifen auf und Verwalten von Protokollen](/help/implementing/cloud-manager/manage-logs.md).

Sowohl die Produktfunktionstests als auch die benutzerdefinierten Funktionstests basieren auf den [AEM Testing Clients.](https://github.com/adobe/aem-testing-clients)

### Funktionstests für das Produkt {#product-functional-testing}

Produktfunktionstests sind eine Reihe stabiler HTTP-Integrationstests (ITs) mit Kernfunktionen in AEM wie Authoring- und Replikationsaufgaben. Diese Tests werden von Adobe verwaltet und sollen verhindern, dass Änderungen am benutzerdefinierten Anwendungs-Code bereitgestellt werden, wenn sie die Kernfunktionen beeinträchtigen.

* [Produktions-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) Produktfunktionstests werden automatisch ausgeführt, wenn Sie neuen Code in Cloud Manager implementieren, und können nicht übersprungen werden.
* [Produktionsfremde Pipelines](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md): Für Produktfunktionstests kann optional das Ausführen gewählt werden, wenn Sie Ihre produktionsfremde Pipeline ausführen.

Produktfunktionstests werden als Open-Source-Projekt verwaltet. Details finden Sie unter [Produktfunktionstests](https://github.com/adobe/aem-test-samples/tree/aem-cloud/smoke) in GitHub.

### Benutzerdefinierte Funktionstests {#custom-functional-testing}

Während die Produktfunktionstests von Adobe definiert werden, können Sie Ihre eigenen Qualitätstests für Ihr eigenes Programm schreiben. Dieser wird als benutzerdefinierter Funktionstest im Rahmen der [Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md) oder optional der [produktionsfremden Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md) ausgeführt, um die Qualität Ihrer Anwendung sicherzustellen.

Benutzerdefinierte Funktionstests werden sowohl für benutzerdefinierte Code-Bereitstellungen als auch für Push-Upgrades durchgeführt. Daher ist es besonders wichtig, gute Funktionstests zu schreiben, die verhindern, dass AEM-Code-Änderungen Ihren Anwendungs-Code beschädigen. Der Schritt für benutzerdefinierte Funktionstests ist immer vorhanden und kann nicht übersprungen werden.

Weitere Informationen finden Sie unter [Java-Funktionstests](/help/implementing/cloud-manager/java-functional-testing.md).


### Benutzerdefinierte Benutzeroberflächentests {#custom-ui-testing}

Die Testfunktion für die benutzerdefinierte Benutzeroberfläche ist eine optionale Funktion, mit der man Benutzeroberflächentests für Anwendungen erstellen und automatisch ausführen kann. Benutzeroberflächentests sind Selenium-basierte Tests, die in einer Docker-Grafik verpackt werden, um eine breite Auswahl an Sprachen und Frameworks zu ermöglichen, z. B. Java und Maven, Node und WebDriver.io oder andere Frameworks und Technologien, die auf Selenium aufbauen.

Weitere Informationen finden Sie unter [Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/ui-testing.md#custom-ui-testing).

