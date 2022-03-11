---
title: Repository Modernizer
description: Repository Modernizer
exl-id: cd9d212e-e720-4209-8b5a-659883cc1d95
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 100%

---

# Repository Modernizer {#repo-modernizer}

Repository Modernizer ist ein Service-Programm, das entwickelt wurde, um bestehende Projektpakete umzustrukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden, um mit der Projektstruktur kompatibel zu sein, die für Adobe Experience Manager as a Cloud Service definiert wurde.

## Einführung {#introduction}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für Ihre AEM-Projekte. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind. Im Allgemeinen erfordert AEM eine Trennung von **Inhalt** und **Code** in separate Unterpakete, um die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt zu berücksichtigen. Weitere Informationen zur neuen AEM-Projektstruktur für Cloud Service finden Sie unter [Struktur von AEM-Projekten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html?lang=de).

Der Repository Modernizer erstellt eine kompatible AEM Cloud Service-Projektstruktur, indem er die folgende Implementierungsstruktur erstellt:

* Das `ui.apps`-Paket wird unter `/apps` bereitgestellt und enthält den gesamten Code.

* Das `ui.content`-Package wird in zur Laufzeit beschreibbare Bereichen bereitgestellt (z. B. `/content`, `/conf`, `/home` oder alles, was nicht `/apps` ist) und enthält alle Inhalte und Konfigurationen.

* Das `all`-Paket ist ein Container-Paket, das die Unterpakete `ui.apps` und `ui.content`enthält.

>[!NOTE]
>Die Projektstruktur basiert auf *Archetyp 24* für Pakete und deren `pom.xml/filter.xml files`. Weitere Informationen finden Sie unter [Archetyp 24](https://github.com/adobe/aem-project-archetype).

## Verwenden des Repository Modernizer {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Über Adobe I/O-CLI: Es empfiehlt sich, Repository Modernizer über `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service-Code-Refaktorierungs-Plug-in für Adobe I/O CLI) zu verwenden.

   Unter **[Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** erfahren Sie, wie Sie das Plug-in installieren und verwenden.

* Als eigenständiges Service-Programm: Der Repository Modernizer kann auch als eigenständiges Service-Programm ausgeführt werden.

   Unter **[Git-Ressource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** erfahren Sie, wie dieses Tool verwendet wird.

   >[!NOTE]
   >
   >Der Repository Modernizer wird mithilfe von NodeJS entwickelt. Es wird empfohlen, NodeJS 10.0 oder höher zu installieren.
