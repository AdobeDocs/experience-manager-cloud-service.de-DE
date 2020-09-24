---
title: Repository-Moderator
description: Repository-Moderator
translation-type: tm+mt
source-git-commit: fd70f5b6a17666d411a64a8fb3961555a42a5430
workflow-type: tm+mt
source-wordcount: '266'
ht-degree: 3%

---


# Repository-Moderator {#repo-modernizer}

Repository Modernizer ist ein Dienstprogramm, das entwickelt wurde, um bestehende Projektpakete umzustrukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden, um mit der Projektstruktur kompatibel zu sein, die für Adobe Experience Manager als Cloud Service definiert wurde.

## Einführung {#introduction}

Adobe Experience Manager als Cloud Service bringt viele neue Features und Möglichkeiten in Ihre AEM Projekte ein. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager Maven-Projekte mit AEM Cloud Service kompatibel sind. Auf hoher Ebene erfordert AEM eine Trennung von **Inhalt** und **Code** in separate Unterpakete, um die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt zu respektieren. Weitere Informationen zur neuen AEM Projektstruktur für Cloud Service finden Sie in der [AEM Projektstruktur](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html) .

Der Repository Moderator erstellt eine kompatible AEM Cloud Service-Projektstruktur, indem er die folgende Bereitstellungsstruktur erstellt:

* `ui.apps` -Paket bereitstellt `/apps` und den gesamten Code enthält

* `ui.content` -Pakete in Laufzeitbereiche (z. B. `/content`, `/conf`, `/home`oder etwas nicht `/apps`) und enthält alle Inhalte und Konfigurationen.

* `all` -Paket ist ein Container-Paket, das die Unterpakete `ui.apps` und `ui.content`enthält.

## Verwenden des Repository-Moderators {#using-repo-modernizer}

* Über Adobe I/O CLI: Es wird empfohlen, den Repository Modernizer über `aio-cli-plugin-aem-cloud-service-migration` (AEM als Cloud Service-Code-Refactoring-Plugin für die Adobe-I/O-CLI) zu verwenden.

   Siehe **[Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** erfahren Sie, wie Sie das Plugin installieren und verwenden.

* Als eigenständiges Dienstprogramm: Der Repository Modernizer kann auch als eigenständiges Dienstprogramm ausgeführt werden.

   Siehe **[Git-Ressource: Repository-Moderator](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** , um zu erfahren, wie dieses Tool verwendet wird.
