---
title: Repository Modernizer
description: Erfahren Sie, wie Sie bestehende Projektpakete umstrukturieren und mit der für Adobe Experience Manager as a Cloud Service definierten Projektstruktur kompatibel machen.
exl-id: cd9d212e-e720-4209-8b5a-659883cc1d95
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '322'
ht-degree: 83%

---

# Repository-Modernizer {#repo-modernizer}

Repository Modernizer ist ein Service-Programm, das entwickelt wurde, um bestehende Projektpakete umzustrukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden, um mit der Projektstruktur kompatibel zu sein, die für Adobe Experience Manager as a Cloud Service definiert wurde.

## Einführung {#introduction}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für Ihre AEM-Projekte. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind. Im Allgemeinen erfordert AEM eine Trennung von **Inhalt** und **Code** in diskrete Unterpakete, um die Trennung zwischen veränderlichen und unveränderlichen Inhalten zu berücksichtigen. Weitere Informationen über die neue AEM-Projektstruktur für den Cloud Service finden Sie unter [AEM-Projektstruktur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de).

Der Repository Modernizer erstellt eine kompatible AEM Cloud Service-Projektstruktur, indem er die folgende Bereitstellungsstruktur erstellt:

* Das `ui.apps`-Paket wird unter `/apps` bereitgestellt und enthält den gesamten Code.

* Das `ui.content`-Paket wird in zur Laufzeit beschreibbaren Bereichen bereitgestellt (z. B. `/content`, `/conf`, `/home`, oder alles, was nicht `/apps` ist) und enthält alle Inhalte und Konfigurationen.

* Das Paket `all` ist ein Container-Paket, das die Unterpakete `ui.apps` und `ui.content` enthält.

>[!NOTE]
>Die Projektstruktur basiert auf *Archetyp 24* für Pakete und deren `pom.xml/filter.xml files`. Weitere Informationen finden Sie unter [Archetype 24](https://github.com/adobe/aem-project-archetype).

## Verwenden von Repository Modernizer {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Über Adobe I/O CLI : Adobe empfiehlt die Verwendung des Repository Modernizer via `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service Code-Refaktorierungs-Plug-in für die Adobe I/O-CLI).

  Unter **[Git Resource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** erfahren Sie, wie Sie das Plug-in installieren und verwenden können.

* Als eigenständiges Service-Programm: Der Repository Modernizer kann auch als eigenständiges Service-Programm ausgeführt werden.

  Unter **[Git Ressource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** erfahren Sie, wie Sie dieses Tool verwenden.

  >[!NOTE]
  >
  >Der Repository Modernizer wird mithilfe von NodeJS entwickelt. Es wird empfohlen, NodeJS 10.0 oder höher zu installieren.
