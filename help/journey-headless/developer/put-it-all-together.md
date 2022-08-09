---
title: So fügen Sie alles zusammen – Ihre Mobile App und Ihre Inhalte in AEM Headless
description: In diesem Teil der AEM Headless-Entwickler-Tour erfahren Sie, wie Sie Ihr AEM-Projekt, einschließlich Inhaltsfragmenten, Ihrer GraphQL-Aufrufe, Ihrer REST-API-Aufrufe und Ihres Programms für das Go-Live vorbereiten.
exl-id: bece84ad-4c8c-410c-847e-9ef3f79970cb
source-git-commit: 270eb35023e34eed2cd17674372794c6c2cc7757
workflow-type: tm+mt
source-wordcount: '1116'
ht-degree: 100%

---

# So fügen Sie alles zusammen – Ihre Mobile App und Ihre Inhalte in AEM Headless {#put-it-all-together}

In diesem Teil der [AEM Headless-Entwickler-Tour](overview.md) machen Sie sich mit der Verwendung der AEM-Entwicklungs-Tools und des Headless-SDK vertraut, um Ihre Anwendung zusammenzustellen.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument zur AEM Headless-Entwickler-Tour [Aktualisieren Ihres Inhalts über AEM Assets-APIs](update-your-content.md) haben Sie erfahren, wie Sie Ihren vorhandenen Headless-Content in AEM über die API aktualisieren können. Nun verfügen Sie über folgende Kenntnisse:

* Grundlegendes zur AEM Assets-HTTP-API

## Ziel {#objective}

Dieser Artikel soll Ihnen helfen zu verstehen, wie Sie Ihre AEM-Headless-Anwendung zusammenstellen können, indem Sie:

* mehr über das AEM-SDK und die erforderlichen Entwicklungs-Tools erfahren
* eine lokale Entwicklungslaufzeit einrichten, um Ihre Inhalte vor der Live-Schaltung zu simulieren
* Grundlagen zur AEM-Inhaltsreplikation

## Das AEM-SDK {#the-aem-sdk}

Das AEM-SDK wird zum Erstellen und Bereitstellen von anwenderdefiniertem Code verwendet. Es ist das wichtigste Tool, das Sie vor der Live-Schaltung zum Entwickeln und Testen Ihres Headless-Programms benötigen. Es enthält die folgenden Artefakte:

* Die Quickstart-JAR-Datei: eine ausführbare JAR-Datei, die sowohl zum Einrichten einer Autoren- als auch einer Veröffentlichungsinstanz verwendet werden kann
* Dispatcher-Tools: das Dispatcher-Modul und seine Abhängigkeiten für Windows- und UNIX®-basierte Systeme
* Java™-API-JAR-Datei: die Java™-JAR-/Maven-Abhängigkeit, die alle zulässigen Java™-APIs verfügbar macht, die zur Entwicklung für AEM verwendet werden können
* Javadoc-JAR: die Javadocs für die Java™-API-JAR-Datei

## Das AEM Headless-SDK {#the-aem-headless-sdk}

Anders als das AEM-SDK ist das AEM **Headless-SDK** ist Satz von Bibliotheken, die von Clients verwendet werden können, um schnell und einfach mit AEM Headless-APIs über HTTP zu interagieren.

Weitere Informationen zum AEM Headless-SDK finden Sie in der [Dokumentation hier](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/how-to/aem-headless-sdk.html?lang=de).

## Weitere Entwicklungs-Tools {#additional-development-tools}

Zusätzlich zum AEM-SDK benötigen Sie weitere Tools, die das lokale Entwickeln und Testen von Code und Inhalten erleichtern:

* Java™
* Git
* Apache Maven
* Die Node.js-Bibliothek
* Die IDE Ihrer Wahl

Da AEM ein Java™-Programm ist, müssen Sie Java™ und das Java™-SDK installieren, um die Entwicklung von AEM as a Cloud Service zu unterstützen.

Git wird für die Versionskontrolle verwendet sowie um Änderungen in Cloud Manager einzuchecken und sie dann in einer Produktionsinstanz bereitzustellen.

AEM verwendet Apache Maven zum Erstellen von Projekten, die aus dem AEM-Maven-Projektarchetyp generiert wurden. Alle wichtigen IDEs bieten Integrationsunterstützung für Maven.

Node.js ist eine JavaScript-Laufzeitumgebung, die zum Arbeiten mit den Frontend-Assets des Unterprojekts `ui.frontend` eines AEM-Projekts verwendet wird. Node.js wird mit npm verteilt, dem De-facto-Paket-Manager von Node.js, der zur Verwaltung von JavaScript-Abhängigkeiten verwendet wird.

## Komponenten eines AEM-Systems auf einen Blick {#components-of-an-aem-system-at-a-glance}

Als Nächstes sehen wir uns die Bestandteile einer AEM-Umgebung an.

Eine vollständige AEM-Umgebung besteht aus einer Autoren-, Veröffentlichungs- und Dispatcher-Komponente. Dieselben Komponenten werden in der lokalen Entwicklungslaufzeit verfügbar gemacht, damit Sie Ihre Code- und Inhaltsvorschau vor der Live-Schaltung einfacher anzeigen können.

* **Der Autoren-Service**, mit dem interne Anwender Inhalte erstellen, verwalten und in der Vorschau anzeigen.

* **Der Veröffentlichungs-Service** fungiert als „Live-Umgebung“ und ist in der Regel der Bereich, mit die Endanwender interagieren. Inhalte werden nach der Bearbeitung und Genehmigung im Autoren-Service an den Veröffentlichungs-Service weitergeleitet. Das häufigste Bereitstellungsmuster bei AEM Headless-Programmen besteht darin, die Produktionsversion des Programms mit dem Veröffentlichungs-Service von AEM zu verbinden.

* **Der Dispatcher** ist ein statischer Webserver, der durch das AEM Dispatcher-Modul erweitert wird. Er speichert durch die Veröffentlichungsinstanz generierte Web-Seiten zwischen, um die Leistung zu verbessern.

## Workflow für die lokale Entwicklung {#the-local-development-workflow}

Das Projekt für die lokale Entwicklung basiert auf Apache Maven und verwendet Git für die Quell-Code-Verwaltung. Um das Projekt zu aktualisieren, können Entwickler ihre bevorzugte integrierte Entwicklungsumgebung wie Eclipse, Visual Studio Code oder IntelliJ verwenden.

Um Code- oder Inhaltsaktualisierungen zu testen, die von Ihrem Headless-Programm aufgenommen werden, müssen Sie die Aktualisierungen für die lokale AEM-Laufzeit bereitstellen, die lokale Instanzen der Autoren- und Veröffentlichungs-Services von AEM enthält.

Achten Sie auf die Unterschiede zwischen den einzelnen Komponenten in der lokalen AEM-Laufzeit, da Sie Ihre Updates unbedingt dort testen sollten, wo sie am relevantesten sind. Testen Sie beispielsweise Inhaltsaktualisierungen in der Autoreninstanz, bzw. neuen Code in der Veröffentlichungsinstanz.

In einem Produktionssystem befinden sich Dispatcher und ein Apache-HTTP-Server immer vor der AEM-Veröffentlichungsinstanz. Sie stellen Caching- und Sicherheits-Services für das AEM-System bereit, daher ist es von größter Bedeutung, Code- und Inhaltsaktualisierungen auch in Richtung Dispatcher zu testen.

## Lokale Vorschau Ihres Codes und Ihrer Inhalte mit der lokalen Entwicklungsumgebung {#previewing-your-code-and-content-locally-with-the-local-development-environment}

Um Ihr AEM Headless-Projekt auf den Launch vorzubereiten, müssen Sie sicherstellen, dass alle Bestandteile Ihres Projekts einwandfrei funktionieren.

Dazu müssen Sie alle Komponenten – Code, Inhalte und Konfiguration – zusammenführen und anschließend in einer lokalen Entwicklungsumgebung testen, damit sie bereit für die Live-Schaltung sind.

Die lokale Entwicklungsumgebung umfasst drei Hauptbereiche:

1. Das AEM-Projekt: Es enthält den anwenderdefinierten Code, die Konfiguration und die Inhalte, an dem die AEM-Entwickler arbeiten werden.
1. Die lokale AEM-Laufzeit: Dabei handelt es sich um lokale Versionen der Autoren- und Veröffentlichungs-Services von AEM, die zum Bereitstellen von Code aus dem AEM-Projekt verwendet werden.
1. Die lokale Dispatcher-Laufzeit: Dies ist eine lokale Version des Apache-HTTP-Servers („httpd“), die das Dispatcher-Modul enthält.

Nachdem die lokale Entwicklungsumgebung eingerichtet wurde, können Sie die Bereitstellung von Inhalten für das React-Programm simulieren, indem Sie lokal einen statischen Knoten-Server bereitstellen.

Weitere Informationen zum Einrichten einer lokalen Entwicklungsumgebung und allen Abhängigkeiten, die für die Inhaltsvorschau erforderlich sind, finden Sie in der [Dokumentation zur Produktionsbereitstellung](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/production-deployment.html?lang=de#prerequisites).

## Wie geht es weiter {#whats-next}

Nachdem Sie nun diesen Teil der AEM Headless-Entwickler-Tour abgeschlossen haben, sollten Sie über die folgenden Kenntnisse verfügen:

* Kennenlernen der AEM Entwicklungs-Tools
* Grundlegendes zum Workflow für die lokale Entwicklung

Sie sollten Ihre AEM Headless-Tour fortsetzen, indem Sie sich das Dokument [So gehen Sie mit Ihrer Headless-Anwendung live](/help/journey-headless/developer/go-live.md) ansehen, in dem Sie mit Ihrem AEM Headless-Projekt tatsächlich live gehen.

## Zusätzliche Ressourcen {#additional-resources}

* [Das AEM as a Cloud Service-SDK](/help/implementing/developing/introduction/aem-as-a-cloud-service-sdk.md)
* [Einrichten einer lokalen AEM-Entwicklungsumgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/set-up-a-local-aem-development-environment.html?lang=de)
* [AEM Headless-SDK für Client-seitige Browser (JavaScript)](https://github.com/adobe/aem-headless-client-js)
* [AEM Headless-SDK für Server-seitig/Node.js (JavaScript)](https://github.com/adobe/aem-headless-client-nodejs)
* [AEM Headless-SDK für Java™](https://github.com/adobe/aem-headless-client-java)

