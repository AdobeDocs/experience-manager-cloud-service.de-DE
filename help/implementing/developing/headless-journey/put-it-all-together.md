---
title: Wie Sie alles zusammenstellen - Ihre App und Ihre Inhalte ohne Kopf AEM
description: Erfahren Sie in diesem Teil der AEM Headless Developer-Journey, wie Sie Ihr AEM-Projekt, einschließlich Inhaltsfragmente, Ihre GraphQL-Aufrufe, Ihre REST-API-Aufrufe und Ihre Anwendung, mitnehmen und es für die Live-Schaltung vorbereiten.
hide: true
hidefromtoc: true
index: false
exl-id: 254fb9dd-36c8-43ce-aaea-ceb4d079503d
translation-type: tm+mt
source-git-commit: e8eb9d2c96d24601e50c48f6846a8c8bac8b0252
workflow-type: tm+mt
source-wordcount: '892'
ht-degree: 1%

---

# Wie Sie alles zusammenstellen - Ihre App und Ihr Inhalt in AEM Headless {#put-it-all-together}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der [AEM Headless Developer-Journey lernen Sie, wie Sie Ihr AEM Projekt, einschließlich Inhaltsfragmente, Ihre GraphQL-Aufrufe, Ihre REST-API-Aufrufe und Ihre Anwendung übernehmen und es für Live-Übertragungen vorbereiten.](overview.md)

## Die Meldung bisher {#story-so-far}

Im vorherigen Dokument der AEM-Journey [So aktualisieren Sie Ihre Inhalte über AEM Assets APIs](update-your-content.md), haben Sie gelernt, wie Sie Ihre vorhandenen, kopflosen Inhalte in AEM über API aktualisieren können. Sie sollten jetzt:

* Machen Sie sich mit der AEM Assets HTTP API vertraut.

Dieser Artikel baut auf diesen Grundlagen auf, damit Sie verstehen, wie Sie Ihr eigenes, AEM kopfloses Projekt live vorbereiten können.

## Vorgabe {#objective}

* Verstehen Sie, für welchen lokalen Entwicklungsarbeitsablauf AEM
* Installieren Sie das AEM SDK, um eine lokale Entwicklungslaufzeit zu erhalten, die Sie zum Testen Ihres Inhalts verwenden können.
* Erfahren Sie mehr über die Entwicklungstools, die Sie neben der lokalen Entwicklungslaufzeit benötigen

## Lokaler Entwicklungsarbeitsablauf {#the-local-development-workflow}

Das lokale Entwicklungsprojekt basiert auf Apache Maven und nutzt Git zur Quellcodeverwaltung. Um das Projekt zu aktualisieren, können Entwickler unter anderem ihre bevorzugte integrierte Entwicklungs-Umgebung wie Eclipse, Visual Studio Code oder IntelliJ verwenden.

Zum Testen von Code- oder Inhaltsaktualisierungen, die von Ihrer Anwendung ohne Kopfdaten erfasst werden, müssen Sie die Updates für eine lokale AEM-Laufzeit bereitstellen, die lokale Instanzen des AEM-Autoren- und Veröffentlichungsinstanzen enthält.

Achten Sie darauf, die Unterschiede zwischen den einzelnen Komponenten in der lokalen AEM-Laufzeit zu beachten, da es wichtig ist, Ihre Updates dort zu testen, wo sie am wichtigsten sind - zum Beispiel Inhaltsaktualisierungen beim Autor zu testen oder neuen Code in der Veröffentlichungsinstanz zu testen.

In einem Produktionssystem sitzen ein Dispatcher und ein HTTP-Apache-Server immer vor einer AEM Veröffentlichungsinstanz. Sie bieten Caching- und Sicherheitsdienste für das AEM System, daher ist es von größter Bedeutung, auch Code- und Inhaltsupdates für den Dispatcher zu testen.

Nachdem Sie sichergestellt haben, dass alles getestet wurde und ordnungsgemäß funktioniert, können Sie Codeaktualisierungen an ein zentralisiertes Git-Repository in Cloud Manager übertragen.

Nachdem die Updates in Cloud Manager hochgeladen wurden, können sie mithilfe der CI/CD-Pipeline von Cloud Manager AEM als Cloud Service bereitgestellt werden.


## Das AEM SDK {#the-aem-sdk}

Das AEM SDK wird zum Erstellen und Bereitstellen von benutzerspezifischem Code verwendet. Es enthält die folgenden Artefakte:

* Die Schnellstart-JAR-Datei - eine ausführbare JAR-Datei, mit der sowohl eine Autoren- als auch eine Veröffentlichungsinstanz eingerichtet werden kann
* Dispatcher-Tools - das Dispatcher-Modul und seine Abhängigkeiten für Windows- und UNIX-basierte Systeme
* Java-API-JAR - Die Java-Jar-/Maven-Abhängigkeit, die alle zulässigen Java-APIs verfügbar macht, die für die Entwicklung gegen AEM verwendet werden können
* Javadoc jar - die JavaScript-Dateien für die Java API-JAR

## Umgebung für lokale Entwicklung {#local-development-environment}

Um Ihr AEM freizügiges Projekt auf den Start vorzubereiten, müssen Sie sicherstellen, dass alle Bestandteile Ihres Projekts gut funktionieren.

Dazu müssen Sie alles zusammenstellen - Code, Inhalt und Konfiguration und es in einer lokalen Entwicklungs-Umgebung testen, um live bereitzugehen.

Die örtliche Umgebung umfasst drei Schwerpunkte:

1. Das AEM Projekt - enthält den gesamten benutzerspezifischen Code, die Konfiguration und den Inhalt, an dem die AEM Entwickler arbeiten werden
1. Die lokale AEM Runtime - lokale Versionen der AEM Autoren- und Veröffentlichungsdienste, die zum Bereitstellen des Codes aus dem AEM Projekt verwendet werden
1. Die lokale Dispatcher-Laufzeit - eine lokale Version des Apache htttpd-Webservers, der das Dispatcher-Modul enthält

## Entwicklungstools {#development-tools}

Zusätzlich zum AEM SDK benötigen Sie zusätzliche Werkzeuge, mit denen Sie Code und Inhalte lokal entwickeln und testen können:

* Java
* Git
* Apache Maven
* Die Node.js-Bibliothek
* Die IDE Ihrer Wahl

Da AEM eine Java-Anwendung ist, müssen Sie Java und das Java-SDK installieren, um die Entwicklung von AEM als Cloud Service zu unterstützen.

Git ist das Tool, mit dem Sie Quellcodeverwaltung verwalten sowie die Änderungen in Cloud Manager einchecken und diese dann in einer Produktionsinstanz bereitstellen können.

AEM nutzt Apache Maven zum Erstellen von Projekten, die aus dem AEM Maven Project Archetyp generiert wurden. Alle wichtigen IDEs bieten Integrationsunterstützung für Maven.

Node.js ist eine JavaScript-Laufzeitumgebung, die zum Arbeiten mit den Front-End-Elementen des ui.frontend-Unterprojekts eines AEM Projekts verwendet wird. Node.js wird mit npm verteilt, ist der De-facto-Paketmanager von Node.js, der zum Verwalten von JavaScript-Abhängigkeiten verwendet wird.

## Wie geht es weiter {#what-is-next}

Sie sollten Ihre AEM kopflosen Journey fortsetzen, indem Sie das Dokument [Wie Sie mit Ihrer Headless-Anwendung leben](go-live.md) überprüfen, wo Sie Ihr AEM Headless-Projekt tatsächlich live mitnehmen!

## Zusätzliche Ressourcen {#additional-resources}

* [Setup](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=en#local-dispatcher-runtime)  der lokalen Entwicklungs-Umgebung - erfahren Sie, wie Sie die Werkzeuge installieren, die erforderlich sind, um Beginn zu entwickeln, die für AEM entwickelt werden
* [AEM als Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)  - Sehen Sie sich das AEM SDK genauer an