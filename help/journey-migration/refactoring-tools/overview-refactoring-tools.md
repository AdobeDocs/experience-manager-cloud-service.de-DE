---
title: Erste Schritte mit Refaktorierungs-Tools
description: Erste Schritte mit den AEM-Refaktorierungs-Tools
exl-id: c0cecf65-f419-484b-9d55-3cbd561e8dcd
source-git-commit: fa65b489d54d5333811145a1875a8f6fc89317bc
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 2%

---


>[!CONTEXTUALHELP]
>id="aemcloud_rs_overview"
>title="Überblick"
>abstract="„Refaktorierungs-Tools“ ist eine von Adobe entwickelte Lösung, mit der Sie bestehende AEM-Projekte im Hinblick auf die Kompatibilität mit AEM as a Cloud Service refaktorieren können. Die Tools werden über Cloud Acceleration Manager (CAM) ausgeführt und automatisieren wichtige Modernisierungsaufgaben."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/guidelines-best-practices-content-transfer-tool.html?lang=de" text="Richtlinien und Best Practices"

# Erste Schritte mit Refaktorierungs-Tools {#getting-started-refactoring-tools}

**Refaktorierungs-Tools** optimieren Sie den Prozess der Aktualisierung vorhandener AEM-Projekte, damit sie mit **AEM as a Cloud Service (AEMaaCS) kompatibel sind**. Diese Tools automatisieren gängige Refaktorierungs- und Modernisierungsaufgaben und sind für ein nahtloses Erlebnis in die **Cloud Acceleration Manager (CAM** integriert.

Früher nur als CLI-Dienstprogramme verfügbar, bieten die Refaktorierungs-Tools jetzt eine einheitliche Oberfläche mit Funktionen wie automatisierte Inspektion, Konfigurationserstellung und Auftragsausführung, wodurch der manuelle Overhead reduziert und die Sichtbarkeit verbessert wurde.

&#x200B;---

## Prüf-Workflow {#inspection-workflow}

Der **Inspektions-Workflow** vereinfacht den Vorbereitungsprozess für die Ausführung von Refaktorierungs-Tools.

### Wichtigste Funktionen:

* **Automatischer Trigger** - Beim Hochladen eines Projekts wird die Überprüfung automatisch gestartet.
* **Konfigurationserstellung** - Die Tools überprüfen den hochgeladenen Quell-Code und generieren die erforderlichen Konfigurationen.
* **Payload-Übermittlung** - Diese Konfigurationen werden zur Ausführung direkt an die ausgewählten Tools übergeben.

&#x200B;---

## Verfügbare Refaktorierungs-Tools

### Repository Modernizer {#repo-modernizer}

Der **Repository Modernizer** strukturiert das Repository-Layout und die Inhalte Ihres AEM-Projekts neu, um sie an AEMaaCS-Standards und Best Practices anzupassen. Es ersetzt das alte Tool zur Repository-Modernisierung durch eine verbesserte Automatisierung und Genauigkeit.

### Code-Transformer {#code-transformer}

Der **Code Transformer** verwendet intelligente Mustererkennung und KI-gesteuerte Analyse, um Code-Segmente zu erkennen und zu aktualisieren, die mit AEMaaCS nicht kompatibel sind. Dieses Tool vereinfacht den Migrationsaufwand und reduziert manuelle Code-Änderungen.

&#x200B;---

## Workflow-Phasen umgestalten {#phases-in-refactoring-tools}

Die Refaktorierungs-Tools folgen einem strukturierten zweiphasigen Prozess:

### Phase 1: Source-Code hochladen

* Laden Sie Ihren Quellcode (im ZIP-Format) über die CAM-Schnittstelle hoch.
* Nach dem Hochladen wird **Prüfungs-Workflow** automatisch ausgelöst, um das Projekt zu analysieren und für die Ausführung des Tools vorzubereiten.

>[!NOTE]
>Während des Inspektionsprozesses ist das Hochladen eines anderen Projekts nicht zulässig.

&#x200B;---

### Phase 2: Trigger eines Refaktorierungsauftrags

Nach erfolgreicher Inspektion können Sie ein oder mehrere Refaktorierungs-Tools ausführen:

* **Run Repository Modernizer**: Führt die Repository-Modernisierung aus.
* **Code-Transformer ausführen** - Führt die Code-Transformation basierend auf der Prüfergebnisausgabe aus.
* **Alle Tools gemeinsam ausführen** - Führt alle verfügbaren Tools in einem Vorgang aus.

>[!NOTE]
>Refaktorierungsaufträge können erst gestartet werden, nachdem der Quell-Code erfolgreich hochgeladen und überprüft wurde.

>[!NOTE]
>Benutzende können mehrere Refaktorierungsaufträge parallel ausführen, aber jeder Trigger wird separat ausgeführt.
