---
title: Terminologie von AEM as a Cloud Service
description: Bevor Sie sich bei AEMaaCS anmelden, sollten Sie einige Begriffe des Systems und seine grundlegende Struktur kennen.
exl-id: d02776a7-836a-4894-a5d5-ae88cc7e4e76
feature: Onboarding
role: Admin, User, Developer
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '463'
ht-degree: 87%

---

# Terminologie von AEM as a Cloud Service {#terminology}

In diesem Teil der [Onboarding-Journey](overview.md) lernen Sie die Terminologie von AEM as a Cloud Service und seine Grundstruktur kennen.

## Ziel {#objective}

Nachdem Sie nun durch das Lesen des Dokuments [Onboarding-Vorbereitung](preparation.md) wissen, wie Sie sich auf den Onboarding-Prozess vorbereiten können, sollten Sie sich vor der Anmeldung mit einigen Begriffen des Systems und seiner Grundstruktur vertraut machen.

AEM as a Cloud Service ist ein leistungsstarkes, flexibles Tool. Und wie bei jedem Tool, das Sie verwenden, sollten Sie auch hier den Aufbau und die zur Beschreibung genutzte Terminologie kennen. In diesem Dokument werden die wichtigste Begriffe erläutert, die Sie verstehen sollten, bevor Sie mit der Verwendung des Systems beginnen.

Nach dem Lesen dieses Dokuments wissen Sie Folgendes

* Die verschiedenen Ebenen, aus denen AEMaaCS besteht.
* Die Grundlagen der einzelnen Ebenen.

## Die AEMaaCS-Struktur {#structure}

Für diese Onboarding-Tour ist kein vollständiges Verständnis der Struktur von AEM as a Cloud Service erforderlich. Wenn Sie jedoch die folgenden Konzepte kennen, wird es Ihnen leichter fallen, dem weiteren Verlauf der Tour zu folgen.

![Cloud Manager-Struktur](/help/journey-sites/quick-site/assets/cloud-manager-structure.png)

* **MANDANT**: Jeder Kunde hat einen Mandanten. Ein Mandant wird auch als IMS-Organisation bezeichnet (weitere Informationen zu IMS erhalten Sie etwas später in dieser Tour).
* **PROGRAMME**: Jeder Mandant verfügt über ein oder mehrere Programme, die häufig die lizenzierten Lösungen des Kunden widerspiegeln.
* **UMGEBUNGEN**: Jedes Programm verfügt über mehrere Umgebungen, z. B. die Produktion für Live-Inhalte, eine für Staging und eine für Entwicklungszwecke.
* **REPOSITORY**: Umgebungen verfügen über ein oder mehrere Git-Repositorys, in denen Anwendungs- und Frontend-Code gespeichert wird.
* **TOOLS UND WORKFLOWS**: Pipelines verwalten die Bereitstellung von Code aus den Repositorys in den Umgebungen.

Oft ist ein Beispiel hilfreich, um diese Hierarchie zu kontextualisieren.

* WKND Travel and Adventure Enterprises könnte ein **Mandant** sein, der sich auf Medien zum Thema Reisen konzentriert.
* Der Mandant von WKND Travel and Adventure Enterprises hat möglicherweise zwei **Programme**:
   * Ein Sites-Programm für den WKND-Magazinbereich
   * Ein Assets-Programm für den WKND-Medienbereich
* Die Programme WKND-Magazin und WKND-Medien verfügen beide über Entwicklungs-, Staging- und Produktions-**Umgebungen**.
* **Repositorys** dienen der Speicherung des benutzerdefinierten Codes und der Programme für WKND-Magazin und WKND-Medien.
* Verschiedene **Tools und Workflows** arbeiten über die Repositorys hinweg, um Code über CI/CD-Pipelines bereitzustellen, auf Protokolle zuzugreifen, auf AEM zuzugreifen und so weiter.

## Wie geht es weiter {#what-is-next}

Nachdem Sie nun diesen Teil der AEM-Onboarding-Tour abgeschlossen haben, wissen Sie über Folgendes Bescheid:

* Die verschiedenen Ebenen, aus denen AEMaaCS besteht.
* Die Grundlagen der einzelnen Ebenen.

Bauen Sie auf diesem Wissen auf und setzen Sie Ihre AEM-Onboarding-Tour fort, indem Sie als Nächstes das Dokument [Zugriff auf die Admin Console](admin-console.md) lesen. Dort erfahren Sie, wie Sie auf die Konsole zugreifen und Ihren Status als System-Admin überprüfen können.
