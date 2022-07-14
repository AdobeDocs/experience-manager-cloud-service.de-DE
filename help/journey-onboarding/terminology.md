---
title: AEM as a Cloud Service Terminologie
description: Bevor Sie sich bei AEMaaCS anmelden, sollten Sie einige Begriffe des Systems und seiner grundlegenden Struktur kennen.
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 18%

---


# AEM as a Cloud Service Terminologie {#terminology}

In diesem Teil des [Onboarding-Journey,](overview.md) Lernen Sie die Terminologie AEM as a Cloud Service und seiner Grundstruktur kennen.

## Ziel {#objective}

Jetzt, da Sie wissen, was zum Onboarding-Prozess geführt hat, lesen Sie das Dokument [Vorbereitung des Onboarding,](preparation.md) Es ist hilfreich, einige Begriffe des Systems und seine grundlegende Struktur zu verstehen, bevor Sie sich anmelden.

AEM as a Cloud Service ist ein leistungsstarkes und flexibles Tool, mit dem Sie jedes Tool verwenden können, das Sie mit der Organisation und der Terminologie und Sprache, mit der Sie es beschreiben, vertraut sein sollten. In diesem Dokument werden einige Schlüsselbegriffe zusammengefasst, die Sie verstehen müssen, bevor Sie mit der Verwendung des Systems beginnen.

Nach dem Lesen dieses Dokuments verstehen Sie Folgendes:

* Die verschiedenen Ebenen, aus denen AEMaaCS besteht.
* Die Grundlagen der einzelnen Ebenen.

## AEMaaCS-Struktur {#structure}

Für diese Onboarding-Journey ist kein vollständiges Verständnis der Struktur AEM as a Cloud Service erforderlich. Die Vertrautheit mit den folgenden Konzepten wird es jedoch erleichtern, später im Journey zu folgen.

![Cloud Manager-Struktur](/help/journey-sites/quick-site/assets/cloud-manager-structure.png)

* **MANDANT**: Jeder Kunde hat einen Mandanten. Ein Mandant wird auch als IMS-Organisation bezeichnet (weitere Informationen zu IMS finden Sie weiter unten in dieser Journey).
* **PROGRAMME**: Jeder Mandant verfügt über ein oder mehrere Programme, die häufig die lizenzierten Lösungen des Kunden widerspiegeln.
* **UMGEBUNGEN**: Jedes Programm verfügt über mehrere Umgebungen, z. B. die Produktion für Live-Inhalte, eine für Staging und eine für Entwicklungszwecke.
* **REPOSITORY** - Die Umgebungen verfügen über ein oder mehrere Git-Repositorys, in denen Anwendung und Frontend-Code gepflegt werden.
* **TOOLS UND WORKFLOWS**: Pipelines verwalten die Bereitstellung von Code aus den Repositorys in die Umgebungen.

Oft ist ein Beispiel hilfreich, um diese Hierarchie zu kontextualisieren.

* WKND Travel and Adventure Enterprises könnte ein **Mandant** sein, der sich auf Medien zum Thema Reisen konzentriert.
* Der Mieter von WKND Travel and Adventure Enterprises könnte über zwei **Programme**:
   * One Sites-Programm für die WKND Magazine-Division
   * Ein Assets-Programm für den WKND-Medienbereich
* Die WKND Magazine- und WKND-Medienprogramme würden beide über Entwicklung, Staging und Produktion verfügen **Umgebungen**.
* **Repositorys** werden verwendet, um den benutzerdefinierten Code und die Anwendungen für WKND Magazine und WKND Media zu verwalten.
* Verschiedene **Tools und Workflows** In allen Repositorys können Sie Code mithilfe von CI/CD-Pipelines bereitstellen, Protokolle aufrufen, auf AEM zugreifen usw.

## Wie geht es weiter? {#what-is-next}

Nachdem Sie nun diesen Teil der AEM Onboarding-Journey abgeschlossen haben, sollten Sie Folgendes verstehen:

* Die verschiedenen Ebenen, aus denen AEMaaCS besteht.
* Die Grundlagen der einzelnen Ebenen.

Auf diesem Wissen aufbauen und Ihre AEM Onboarding-Journey fortsetzen, bevor Sie das Dokument zum nächsten Mal lesen [Zugriff auf die Admin Console](admin-console.md), wo Sie erfahren, wie Sie auf die Konsole zugreifen und Ihren Status als Systemadministrator überprüfen.
