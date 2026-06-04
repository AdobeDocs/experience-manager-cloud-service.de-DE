---
title: Übersicht über den Experience Modernization Agent
description: Erfahren Sie, wie der Experience Modernization Agent mithilfe von KI neue Websites in Edge Delivery Services integriert.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: c23a6f55-2ba8-4290-b7e8-06cad5de0fc8
source-git-commit: f2ab0a3d604ed4cd07ec8922ed331dfc37b45e5f
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 0%

---


# Übersicht über den Experience Modernization Agent {#experience-modernization-agent}

Erfahren Sie, wie der Experience Modernization Agent mithilfe von KI Websites in Edge Delivery Services integriert.

## Einführung {#introduction}

[Im Rahmen der Brand Experience Agent ](/help/ai-in-aem/agents/brand-experience/overview.md) der Experience Modernization Agent das Onboarding für Edge Delivery Services durch die Automatisierung von Website-Migrationen und die Einrichtung grundlegender Websites.

Es kombiniert [Site-Creation und Migration](#creation-migration) für anfängliches Onboarding von Websites und [Blockentwicklungsfunktionen](#block-development) um die Site-Erstellung und Migrations-Workflows zu unterstützen. Darüber hinaus bietet sie die [Experience Modernization Console](#console) als Web-basierte KI-unterstützte Entwicklungsumgebung, die Ihnen direkt zur Verfügung steht. Während Benutzer den Agenten direkt über diese Konsole betreiben können, behalten Entwickler die volle Kontrolle darüber, was ausgeliefert wird.

Für komplexe Migrationen oder Migrationen mit hoher Priorität bietet Adobe das [Agent Outcome Engineer (AOE)-Bereitstellungsmodell, ](#aoe-delivery) einen Engineering-geführten Service, der entwickelt wurde, um produktionsbereite Edge Delivery-Sites mithilfe des Experience Modernization Agent bereitzustellen.

## Vorteile {#benefits}

Der Experience Modernization Agent beschleunigt die Wertschöpfungszeit für die [Edge Delivery Services](/help/edge/overview.md)-Einführung und gibt Ihnen die Agilität, das Web-Erlebnis Ihrer Marke anzupassen.

* **Hohe Geschwindigkeit**: Die KI-Automatisierung übernimmt repetitive Migrationsaufgaben (Inhaltsimport, Blockzuordnung, Design-Systemanwendung) und komprimiert die Migrationszeitpläne im Vergleich zu herkömmlichen Ansätzen
* **Effizienzorientiert**: Automatisierung reduziert repetitive Arbeit, sodass sich Teams auf höherwertige Implementierungsarbeiten konzentrieren können
* **Für alle zugänglich**: Anfragen in natürlicher Sprache machen Website-Änderungen für weniger technische Benutzer zugänglich, mit einer Live-Vorschau, um Änderungen sofort zu validieren
* **Enterprise Governance**: Entwickler behalten die volle Autorität über die Live-Schaltung durch in GitHub integrierte Prüfungs-Workflows
* **Flexibilität nach der Migration**: Ermöglicht es Teams, migrierte Sites mithilfe von Edge Delivery Services-Mustern zu erweitern und einzuengen

## Site-Erstellung und -Migration - Kenntnisse {#creation-migration}

Der Experience Modernization Agent bietet Funktionen zum Erstellen neuer Edge Delivery Services-Sites und zum Migrieren vorhandener Websites. Jeder neue Edge Delivery Services-Standort oder jede neue Migration wird empfohlen, diese Kenntnisse zu nutzen.

* Beschleunigt die Erstellung von Websites und die Migration von Monaten auf Wochen oder Tage und reduziert so die Time-to-Value für die Einführung von Edge Delivery Services erheblich
* Unterstützt die Migration von einer Vielzahl von CMS-Plattformen, älteren AEM- oder Design-Systemen (wie Figma) in produktionsfähige Edge Delivery Services-Projekte
* Unterstützt Best Practices für Leistung, Barrierefreiheit und responsives Design in Übereinstimmung mit den Edge Delivery Services-Richtlinien

Zu den detaillierten Kenntnissen gehören Seitenmigration, Massenimport, Designextraktion, Navigationseinrichtung und Web-Scraping.

## Figmabasierte Migrationen und Seitenerstellung {#figma}

Zusätzlich zu Live-Site-Migrationen kann der Experience Modernization Agent Figma als Design-Quelle verwenden. Um diese Funktionen zu verwenden, richten Sie Ihre Figma-Details in [Experience-Modernisierungs-Konsole“ ein](/help/ai-in-aem/agents/brand-experience/modernization/console.md)

### Umgestalten der Migration mithilfe von FIGMA-abgeleiteten Blöcken {#figma-redesign}

Wenn Sie eine vorhandene Website in ein neu gestaltetes Erlebnis migrieren, [ der Agent zunächst die neu gestaltete Blocksammlung aus Figma-Komponenten, ](/help/ai-in-aem/agents/brand-experience/modernization/prompting-guide.md#figma-redesign-migration) und führt dann die Site-Migration für die Live-Quell-Website durch und ordnet Quellinhalte in diese Figma-abgeleiteten Blöcke zu.

* **Figma** ist die Zieldesign- und Blockbibliotheksquelle.
* **Die Live-Website** bleibt die Inhaltsquelle.
* Inhalte werden anhand der Quell-Website validiert; visuelle Ausgaben werden anhand des aus Figma abgeleiteten Designsystems validiert.

### Erstellen einer neuen Seite aus Figma {#figma-new-page}

Wenn eine Seite nicht bereits auf einer Quell-Website vorhanden ist, generiert der Agent [eine neue Edge Delivery Services-Seite direkt aus einem Figma-Frame oder einer Figma-Seite, ](/help/ai-in-aem/agents/brand-experience/modernization/prompting-guide.md#figma-new-page-from-figma) Figma-Abschnitte vorhandenen Blöcken, Standardinhalten oder neuen Varianten zuordnet. Text und Assets stammen aus Figma.

Weitere Informationen zu diesen Workflows, zur Migration einzelner Figma-Blöcke und zu Eingabetipps finden Sie im [Eingabeaufforderung für den Experience Modernization Agent.](/help/ai-in-aem/agents/brand-experience/modernization/prompting-guide.md)

## Blockentwicklungsfunktionen {#block-development}

Der Experience Modernization Agent nutzt allgemeine Edge Delivery Services-Entwicklungsfunktionen, die verschiedene Entwicklungsaufgaben unterstützen und einen kontinuierlichen Nutzen über die anfängliche Site-Erstellung oder -Migration hinaus bieten.

* Folgt der CDD-Methode (Content-Driven Development) für autorenfreundliche Inhaltsmodelle
* Nutzt die [Blocksammlung](https://www.aem.live/developer/block-collection) und [Blockpartei](https://www.aem.live/developer/block-party/) um Referenzimplementierungen und Best Practices zu finden
* Unterstützt Test- und Debugging-Workflows für die Validierung von Änderungen vor der Bereitstellung

Zu den detaillierten Funktionen gehören Blockentwicklung, Inhaltsmodellierung, Erkennung von Referenzblöcken, Tests und Debugging.

## Experience Modernization Console {#console}

Der Experience Modernization Agent bietet eine Web-basierte KI-unterstützte Entwicklungsumgebung für Edge Delivery Services, die als Web-Schnittstelle unter [`aemcoder.adobe.io` bereitgestellt wird.](https://aemcoder.adobe.io)

* Die Konsole erfordert kein lokales Setup, damit die Benutzer sofort Änderungen in natürlicher Sprache eingeben können.
* Führen Sie schnell alltägliche Aufgaben zur Erlebnisentwicklung aus, während Sie sie über die Live-AEM-Vorschau in der Vorschau anzeigen und Inhalte mit AEM synchronisieren.
* Die Konsole unterstützt Enterprise Governance durch standardmäßige GitHub-Überprüfungs-Workflows.

Die Self-Service-Konsole zur Erlebnismodernisierung ist allgemein verfügbar. Interessierte Benutzer können Zugriff erhalten, um ein reibungsloses Onboarding sicherzustellen.

Erste Schritte mit der Experience Modernization Console!

* Wenn Sie Ihre Site durch die Erstellung von Dokumenten modernisieren möchten, [ Sie hier (Erste Schritte)](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md)
* Wenn Sie Ihre Site durch das Authoring mit AEM modernisieren möchten, [ Sie hier (Erste Schritte)](/help/ai-in-aem/agents/brand-experience/modernization/getting-started-aem-authoring.md)

## Projektdokumentations-Kenntnisse {#project-documentation}

Angesichts der zeitintensiven Natur von Projekt-Handovers kann [die Projektdokumentationsfertigkeit](/help/ai-in-aem/agents/brand-experience/modernization/project-documentation.md) nach Abschluss der Autoren- und Entwicklungsarbeiten automatisch eine umfassende Dokumentation erstellen.

## Site Catalog SKILL {#site-catalog}

Die Katalogfertigkeit der Site crawlen eine vorhandene Website, katalogisiert alle Seitenvorlagen und Blockvarianten, erfasst Screenshots jeder Vorlage und jedes Blocks und generiert ein interaktives HTML-Berichtspaket zur Überprüfung. Diese Kenntnisse sind nützlich für:

* **Jeder, der ein Migrationsprojekt startet** um eine vollständige Bestandsaufnahme der Seitenlayouts, Blockvarianten, Gebietsschemata und Seiten pro Vorlage zu erhalten, bevor Code geschrieben wird, damit Teams die Komplexität frühzeitig genau planen und aufdecken können
* **Teams, die Massenimporte durchführen** Um zu ermitteln, welche Seiten dasselbe Layout verwenden, importieren und perfektionieren Sie zuerst die repräsentativen Seiten manuell und importieren dann alle verbleibenden Seiten für diese Vorlage per Massenimport
* **Projektleiter und Stakeholder** um den Umfang der Bemühungen zu verstehen

Bitte lesen Sie das Dokument [Site-Katalog Kenntnisse](/help/ai-in-aem/agents/brand-experience/modernization/site-catalog.md) für weitere Informationen.

## Versand durch Agent Outcome Engineer (AOE) {#aoe-delivery}

Für komplexe Migrationen oder beschleunigte Ergebnisse bietet Adobe die Bereitstellung von AOE (Agentic Outcome Engineer). Dies ist ein optionaler Service, bei dem Adobe-Techniker den Experience Modernization Agent in Ihrem Namen betreiben und dabei KI-Automatisierung mit fachkundiger Anleitung kombinieren, um skalierbare, produktionsbereite Ergebnisse zu erzielen. Weitere Informationen zum AOE-Versand finden Sie im Dokument [AOE-Bereitstellung des Experience Modernization Agent.](/help/ai-in-aem/agents/brand-experience/modernization/aoe-delivery.md)

Wenn Sie am AOE-Modell für Ihre nächste Migration interessiert sind:

* Wenden Sie sich an Ihren Adobe-Support-Mitarbeiter oder Ihr Account-Team, um die Berechnung und Planung einzuleiten.
* Adobe bestätigt die Eignung, schätzt die Interaktion und schlägt einen Interaktionsplan vor.

## Einschränkungen {#limitations}

Die folgenden Anwendungsfälle erfordern zusätzlich zu den Fähigkeiten des Experience Modernization Agents zusätzlichen Implementierungsaufwand.

Die Scraping-Fähigkeit unterstützt nicht die folgenden Quellen.

* Intranet oder geschützte Quellen wie Inhalte hinter Authentifizierung, VPNs oder Firewalls, auf die nicht zugegriffen werden kann
   * Alternativ können Sie [SLICC](https://www.sliccy.com) verwenden, das den Authentifizierungskontext von Ihrem Browser aus nutzen kann, um auf geschützte Quellen zuzugreifen.
* Komplexe dynamische Inhalte, z. B. Inhalte, für die eine anspruchsvolle Benutzerinteraktion im DOM erforderlich ist.
   * Client-seitig gerenderte Inhalte werden unterstützt, wenn der Zugriff auf die Inhalte über eine bestimmte URL möglich ist.
   * Über CSS ausgeblendete, aber im DOM vorhandene Elemente wie Registerkarten, Akkordeons oder Karussells werden ebenfalls unterstützt.

Der Agent unterstützt die folgenden Ziele nicht.

* AEM-Veröffentlichungsumgebungen, in denen Sites die HTL-basierte Bereitstellung verwenden
   * Die Kenntnisse beziehen sich nur auf Edge Delivery Services.
* Headless-Bereitstellungsmuster wie „Nur API“- oder SPA-basierte Bereitstellung (z. B. Next.js)

Die folgenden Anforderungen werden nicht durch dedizierte Automatisierungsfähigkeiten abgedeckt und erfordern manuellen Aufwand.

* Strenge Pixelperfektion
   * Nur die praktische Designtreue wird automatisiert
* Integrationen von Server- oder Client-seitigen Daten/Services von Drittanbietern
* Integrationen der Commerce- oder Suchfunktion
* MarTech-Datenschicht für Targeting/Experimentieren
* Isolieren von Inhalts-/Experience Fragments
* Multisite-Vererbung (MSM)
* Benutzerdefinierte Funktionen (z. B. Taschenrechner, Konfiguratoren)
* Benutzerdefinierte Geschäftslogik

## Nächste Schritte {#next-steps}

Erste Schritte beim Migrieren einer Site mit dem Dokument [Erste Schritte mit dem Experience Modernization Agent.](/help/ai-in-aem/agents/brand-experience/modernization/getting-started.md)
