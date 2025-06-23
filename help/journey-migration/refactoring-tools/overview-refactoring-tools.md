---
title: Übersicht über die Refaktorierungs-Tools
description: Erfahren Sie mehr über die ersten Schritte mit dem AEM-Refaktorierungs-Tool
exl-id: b8137e01-87e8-4298-b0cc-b376330cb730
source-git-commit: 879f4f3476ee369554188d6e3b7973d32454ed4b
workflow-type: ht
source-wordcount: '338'
ht-degree: 100%

---

<!-- Alexandru: temporarily commeting this out, since it breaks validation

>[!CONTEXTUALHELP]
>id="aemcloud_rs_overview"
>title="Overview"
>abstract="Refactoring Tools is a solution developed by Adobe to help refactor existing AEM projects for compatibility with AEM as a Cloud Service. The tools are executed via Cloud Acceleration Manager (CAM) and automate key modernization tasks."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de" text="Guidelines and Best Practices"

-->

# Übersicht über die Refaktorierungs-Tools {#refactoring-tools-overview}

**Refaktorierungs-Tools** optimieren den Prozess der Aktualisierung vorhandener AEM-Projekte, damit sie mit **AEM as a Cloud Service (AEMaaCS)** kompatibel sind. Diese Tools automatisieren gängige Refaktorierungs- und Modernisierungsaufgaben und sind für ein nahtloses Erlebnis in den **Cloud Acceleration Manager (CAM)** integriert.

Während sie früher nur als CLI-Dienstprogramme verfügbar waren, bieten die Refaktorierungs-Tools jetzt eine einheitliche Oberfläche mit Funktionen wie automatisierte Inspektion, Konfigurationserstellung und Auftragsausführung, wodurch der manuelle Overhead reduziert und die Sichtbarkeit verbessert wurde.

## Inspektions-Workflow {#inspection-workflow}

Der **Inspektions-Workflow** vereinfacht den Vorbereitungsprozess für die Ausführung von Refaktorierungs-Tools.

### Wichtigste Funktionen:

* **Automatisches Auslösen** – Beim Hochladen eines Projekts wird die Überprüfung automatisch gestartet.
* **Konfigurationserstellung** – Die Tools überprüfen den hochgeladenen Quell-Code und generieren die erforderlichen Konfigurationen.
* **Payload-Übermittlung** – Diese Konfigurationen werden direkt an die ausgewählten Tools zur Ausführung übergeben.

## Verfügbare Refaktorierungs-Tools

### Repository Modernizer {#repo-modernizer}

Der **Repository Modernizer** strukturiert das Repository-Layout und den Inhalt Ihres AEM-Projekts neu, um es an AEMaaCS-Standards und Best Practices anzupassen. Es ersetzt das alte Tool zur Repository-Modernisierung durch eine verbesserte Automatisierung und Genauigkeit.

### Code Transformer {#code-transformer}

Der **Code Transformer** verwendet intelligente Mustererkennung und KI-gesteuerte Analyse, um Code-Segmente zu erkennen und zu aktualisieren, die mit AEMaaCS nicht kompatibel sind. Dieses Tool vereinfacht den Migrationsaufwand und reduziert manuelle Code-Änderungen.

## Phasen des Refaktorierungs-Workflows {#phases-in-refactoring-tools}

Die Refaktorierungs-Tools folgen einem strukturierten, zweiphasigen Prozess:

### Phase 1: Hochladen Ihres Quell-Codes

* Laden Sie Ihren Quell-Code (im ZIP-Format) über die CAM-Schnittstelle hoch.
* Nach dem Hochladen wird automatisch der **Inspektions-Workflow** ausgelöst, um das Projekt zu analysieren und für die Ausführung des Tools vorzubereiten.

>[!NOTE]
>Während des Inspektionsprozesses ist das Hochladen eines anderen Projekts nicht zulässig.

### Phase 2: Auslösen eines Refaktorierungsauftrags

Nach erfolgreicher Inspektion können Sie ein oder mehrere Refaktorierungs-Tools ausführen:

* **Repository Modernizer ausführen** – Führt die Repository-Modernisierung aus.
* **Code-Transformer ausführen** – Führt die Code-Transformation basierend auf der Ausgabe der Inspektion aus.
* **Alle Tools gemeinsam ausführen** – Führt alle verfügbaren Tools in einem Vorgang aus.

>[!NOTE]
>Refaktorierungsaufträge können erst gestartet werden, nachdem der Quell-Code erfolgreich hochgeladen und überprüft wurde.

>[!NOTE]
>Benutzende können mehrere Refaktorierungsaufträge parallel ausführen, aber jeder Auftrag wird separat ausgeführt.
