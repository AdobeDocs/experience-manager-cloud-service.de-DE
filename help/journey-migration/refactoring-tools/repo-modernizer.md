---
title: Repository Modernizer
description: Erfahren Sie, wie Sie bestehende Projektpakete umstrukturieren und mit der für Adobe Experience Manager as a Cloud Service definierten Projektstruktur kompatibel machen.
exl-id: cd9d212e-e720-4209-8b5a-659883cc1d95
source-git-commit: 8c73805b6ed1b7a03c65b4d21a4252c1412a5742
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 57%

---

# Repository Modernizer {#repo-modernizer}

Repository Modernizer ist ein Service-Programm, das entwickelt wurde, um bestehende Projektpakete umzustrukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden, um mit der Projektstruktur kompatibel zu sein, die für Adobe Experience Manager as a Cloud Service definiert wurde.

## Einführung {#introduction}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für Ihre AEM-Projekte. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind. Auf hoher Ebene erfordert AEM eine Trennung der **content** und **code** in separate Unterpakete, um die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt zu berücksichtigen. Siehe [AEM Projektstruktur](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de) Weitere Informationen zur neuen AEM Projektstruktur für Cloud Service.

Der Repository Modernizer erstellt eine kompatible AEM Cloud Service-Projektstruktur, indem er die folgende Bereitstellungsstruktur erstellt:

* Das `ui.apps`-Paket wird unter `/apps` bereitgestellt und enthält den gesamten Code.

* Das `ui.content`-Paket wird in zur Laufzeit beschreibbaren Bereichen bereitgestellt (z. B. `/content`, `/conf`, `/home`, oder alles, was nicht `/apps` ist) und enthält alle Inhalte und Konfigurationen.

* `all` -Paket ist ein Container-Paket, das die Unterpakete enthält `ui.apps` und `ui.content`.

>[!NOTE]
>Die Projektstruktur basiert auf *Archetyp 24* für Pakete und deren `pom.xml/filter.xml files`. Siehe [Archetyp 24](https://github.com/adobe/aem-project-archetype) für weitere Details.

## Verwenden des Repository Modernizer {#using-repo-modernizer}

>[!VIDEO](https://video.tv.adobe.com/v/333057/?quality=12&learn=on)

* Über die Adobe I/O-CLI : Es wird empfohlen, den Repository Modernizer über `aio-cli-plugin-aem-cloud-service-migration` (AEM as a Cloud Service Code-Refaktorierungs-Plug-in für die Adobe I/O-CLI).

  Siehe **[Git-Ressource: aio-cli-plugin-aem-cloud-service-migration](https://github.com/adobe/aio-cli-plugin-aem-cloud-service-migration#introduction)** damit Sie lernen können, wie Sie das Plug-in installieren und verwenden.

* Als eigenständiges Service-Programm: Der Repository Modernizer kann auch als eigenständiges Service-Programm ausgeführt werden.

  Siehe **[Git-Ressource: Repository Modernizer](https://github.com/adobe/aem-cloud-service-source-migration/tree/master/packages/repository-modernizer)** damit Sie lernen können, wie Sie dieses Tool verwenden.

  >[!NOTE]
  >
  >Der Repository Modernizer wird mithilfe von NodeJS entwickelt. Es wird empfohlen, NodeJS 10.0 oder höher zu installieren.
