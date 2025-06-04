---
title: Übersicht über die Refaktorierungs-Tools
description: Erste Schritte mit den AEM-Refaktorierungs-Tools
source-git-commit: a77dfef8dce9f4ed549135087f7b63f6d46a4ea1
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 1%

---


<!-- Alexandru: temporarily commeting this out, since it breaks validation

>[!CONTEXTUALHELP]
>id="aemcloud_rs_overview"
>title="Overview"
>abstract="Refactoring Tools is a solution developed by Adobe to help refactor existing AEM projects for compatibility with AEM as a Cloud Service. The tools are executed via Cloud Acceleration Manager (CAM) and automate key modernization tasks."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de" text="Guidelines and Best Practices"

-->

# Übersicht über die Refaktorierungs-Tools {#refactoring-tools-overview}

**Refaktorierungs-Tools** optimieren Sie den Prozess der Aktualisierung vorhandener AEM-Projekte, damit sie mit **AEM as a Cloud Service (AEMaaCS) kompatibel sind**. Diese Tools automatisieren gängige Refaktorierungs- und Modernisierungsaufgaben und sind für ein nahtloses Erlebnis in die **Cloud Acceleration Manager (CAM** integriert.

Früher nur als CLI-Dienstprogramme verfügbar, bieten die Refaktorierungs-Tools jetzt eine einheitliche Oberfläche mit Funktionen wie automatisierte Inspektion, Konfigurationserstellung und Auftragsausführung, wodurch der manuelle Overhead reduziert und die Sichtbarkeit verbessert wurde.

## Prüf-Workflow {#inspection-workflow}

Der **Inspektions-Workflow** vereinfacht den Vorbereitungsprozess für die Ausführung von Refaktorierungs-Tools.

### Wichtigste Funktionen:

* **Automatischer Trigger** - Beim Hochladen eines Projekts wird die Überprüfung automatisch gestartet.
* **Konfigurationserstellung** - Die Tools überprüfen den hochgeladenen Quell-Code und generieren die erforderlichen Konfigurationen.
* **Payload-Übermittlung** - Diese Konfigurationen werden zur Ausführung direkt an die ausgewählten Tools übergeben.

## Verfügbare Refaktorierungs-Tools

### Repository Modernizer {#repo-modernizer}

Der **Repository Modernizer** strukturiert das Repository-Layout und den Inhalt Ihres AEM-Projekts neu, um sie an AEMaaCS-Standards und Best Practices anzupassen. Es ersetzt das alte Tool zur Repository-Modernisierung durch eine verbesserte Automatisierung und Genauigkeit.

### Code-Transformer {#code-transformer}

Der **Code Transformer** verwendet intelligente Mustererkennung und KI-gesteuerte Analyse, um Code-Segmente zu erkennen und zu aktualisieren, die mit AEMaaCS nicht kompatibel sind. Dieses Tool vereinfacht den Migrationsaufwand und reduziert manuelle Code-Änderungen.

## Workflow-Phasen umgestalten {#phases-in-refactoring-tools}

Die Refaktorierungs-Tools folgen einem strukturierten zweiphasigen Prozess:

### Phase 1: Source-Code hochladen

* Laden Sie Ihren Quellcode (im ZIP-Format) über die CAM-Schnittstelle hoch.
* Nach dem Hochladen wird **Prüfungs-Workflow** automatisch ausgelöst, um das Projekt zu analysieren und für die Ausführung des Tools vorzubereiten.

>[!NOTE]
>Während des Inspektionsprozesses ist das Hochladen eines anderen Projekts nicht zulässig.

### Phase 2: Trigger eines Refaktorierungsauftrags

Nach erfolgreicher Inspektion können Sie ein oder mehrere Refaktorierungs-Tools ausführen:

* **Run Repository Modernizer**: Führt die Repository-Modernisierung aus.
* **Code-Transformer ausführen** - Führt die Code-Transformation basierend auf der Prüfergebnisausgabe aus.
* **Alle Tools gemeinsam ausführen** - Führt alle verfügbaren Tools in einem Vorgang aus.

>[!NOTE]
>Refaktorierungsaufträge können erst gestartet werden, nachdem der Quell-Code erfolgreich hochgeladen und überprüft wurde.

>[!NOTE]
>Benutzende können mehrere Refaktorierungsaufträge parallel ausführen, aber jeder Trigger wird separat ausgeführt.
