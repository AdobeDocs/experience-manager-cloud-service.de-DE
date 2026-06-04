---
title: Site Catalog SKILL
description: Erfahren Sie, wie die Site-Katalog-Kenntnisse des Experience Modernisierungs-Agenten eine vorhandene Website automatisch analysieren, um die Migrationsplanung für Edge Delivery Services zu unterstützen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
source-git-commit: 30037f08d5caeab878b6cf89b936308d16ae3e8d
workflow-type: tm+mt
source-wordcount: '776'
ht-degree: 1%

---


# Site Catalog SKILL {#site-catalog-skill}

Erfahren Sie, wie die Site-Katalog-Kenntnisse des Experience Modernisierungs-Agenten eine vorhandene Website automatisch analysieren, um die Migrationsplanung für Edge Delivery Services zu unterstützen.

## Überblick {#overview}

Die Katalogfertigkeit der Website erkennt jede Seite auf der Website, identifiziert die Seitenvorlagen und Blockvarianten, erfasst Screenshots von jeder Seite und generiert ein interaktives HTML-Berichtspaket, das Sie in der Konsolenvorschau durchsuchen oder lokal herunterladen und öffnen können.

Die Kenntnisse unterstützen Sie und Ihre Migration eines vorhandenen Projekts zu Edge Delivery Services auf folgende Weise:

* **Starten eines Migrationsprojekts** - Führen Sie die Kenntnisse aus, bevor irgendwelche Arbeiten beginnen, die Skalierung der Site zu verstehen, einschließlich Seitenzahl, Vorlagen, Blockvarianten und Gebietsschemata. Es stellt den Grundbestand her, von dem jede nachgelagerte Entscheidung abhängt.
* **Aufwandsschätzung und -planung** - Erhalten Sie quantifizierte Metriken zur Unterstützung von Angeboten, Sprint-Planung und Ressourcenplanung.
* **Massenimportvorbereitung** - Verwenden Sie `template-catalog.json`, um zu bestimmen, welche Seiten dasselbe Layout haben, und planen Sie die Massenimporte nach Vorlage.
* **Stakeholder-**: Geben Sie das interaktive Berichtspaket für HTML für Projektmanager, Architekten und geschäftliche Stakeholder frei.

## Aufrufen {#invoking}

[Verwenden ](/help/ai-in-aem/agents/brand-experience/modernization/console.md) in der Experience Modernization Console eine natürliche Sprache, um den Agenten zum Katalogisieren einer Site aufzufordern. Im Folgenden finden Sie Beispielaufforderungen.

* `scope site https://www.example.com`
* `site scope https://www.example.com`
* `analyze https://www.example.com`
* `find templates on https://www.example.com`
* `discover templates on https://www.example.com`
* `catalog site https://www.example.com`
* `how many page types are there on https://www.example.com`
* `what are the layouts on https://www.example.com`
* `analyze site structure of https://www.example.com`

Sie werden feststellen, dass der Workflow der Kenntnisse vier aufeinander folgende Phasen umfasst:

1. Analysieren
1. Vorlagenbildung
1. Abstimmung
1. Blockkatalogisierung

Sie können jede Phase wiederholen, und der Agent löscht die Ausgaben dieser Phase und alle nachgelagerten Ausgaben und nimmt dann von diesem Punkt an wieder auf. Im Folgenden finden Sie einige Beispielaufforderungen für Wiederholungsphasen.

* `Repeat analyzing` / `Redo page analysis` / `Rerun analyze pages`
* `Repeat templating` / `Redo the template discovery step` / `Restart the templating step`
* `Repeat tuning` / `Rerun tune templates` / `Redo template tuning`
* `Repeat block cataloging` / `Restart catalog block variants`

Beim Reproduzieren einer Phase bleiben frühere Phasen erhalten.

## Ausgabe {#output}

Wenn die Kenntnisse ihre Katalogisierung der Website abschließen, erhalten Sie drei verschiedene Arten von Ausgaben.

1. **Eine Abschlusszusammenfassung im Chat** einschließlich Gesamtsummen (Seiten, Vorlagen, Blockvarianten mit EDS-Zuordnung vs. benutzerdefinierter Aufschlüsselung), Gebietsschema-Aufschlüsselung, Abdeckungsprozentsatz und Gesamtberichtsstatus (vollständig/unvollständig/fehlgeschlagen)
1. **Ein interaktives HTML-Berichtspaket** als primäre Leistung, gespeichert in `catalog/template-catalog-report-bundle.zip`
   * Das Paket enthält `template-catalog-report.html` sowie alle referenzierten Screenshots und Assets.
   * Sie können das Bundle herunterladen und lokal anzeigen oder freigeben.
   * `Move template-catalog-report-bundle.zip to the /content folder to render it in the preview tab. Update all references as needed.` Sie können den Agenten auch bitten, den Bericht in der Konsole anzuzeigen.
1. **Strukturierte JSON** Artefakte in `catalog/` für nachgelagerte Fähigkeiten und programmatische Verwendung, einschließlich `summary.json`, `template-catalog.json`, `block-catalog.json`, `urls-all.json`, `urls-grouped.json`, `urls-checklist.json`, `.pages/`, `.blocks/`

### Katalogordnerinhalte {#contents}

Strukturierte JSON-Artefakte werden von der Qualifikation in `catalog/` gespeichert.

| File | Beschreibung |
|---|---|
| `template-catalog-report-bundle.zip` | Interaktives Berichtspaket für HTML (primäres Ergebnis) |
| `summary.json` | Datenaggregationsmetriken und [Berichtsstatus](#status) |
| `template-catalog.json` | Alle eindeutigen Vorlagen mit den jeweiligen URLs (für Massenimporte verwendet) |
| `block-catalog.json` | Alle Blockvarianten mit Metadaten und Screenshot-Referenzen |
| `urls-all.json` | Jede erkannte URL |
| `urls-grouped.json` | Nach Muster und Gebietsschema gruppierte URLs |
| `urls-sample.json` | Repräsentative URLs für die Analyse |
| `urls-checklist.json` | Status der Pro-URL-Analyse |
| `catalog.log` | Ausführungsprotokoll |
| `.pages/<page-slug>/page-catalog.json` | Analyseausgabe auf Seitenebene |
| `.pages/<page-slug>/full-page.jpg` | Vollständiger Screenshot |
| `.pages/<page-slug>/blocks/<block-name>.jpg` | Screenshots pro Block |
| `.pages/_global/header.json + header.jpg` | Analyse der globalen Kopfzeile und Screenshot |
| `.pages/_global/footer.json + footer.jpg` | Analyse und Screenshot der globalen Fußzeile |
| `.blocks/<variantId>/metadata.json` | Variantenmetadaten blockieren |
| `.blocks/<variantId>/screenshots/<name>.jpg` | Variante-Screenshots blockieren |

### Berichtsstatus {#status}

Das `status` Feld in [`summary.json`](#contents) kann wie folgt aussehen:

| Status | Bedeutung |
|---|---|
| `complete` | Alle Seiten wurden erfolgreich analysiert (oder es gab eine Fehlerrate von 10 % oder weniger). |
| `incomplete` | Über 10 % der Seiten sind fehlgeschlagen oder die Blockerkennung stürzte auf über 50 % der Seiten ab. Die Ergebnisse sind weiterhin verwendbar, aber nur teilweise. |
| `failed` | Keine Seiten erfolgreich analysiert. |

## Sampling für große Sites {#sampling}

Standardmäßig beschränkt die Kenntnis die Deep Page Analysis auf 1000 URLs. Bei Sites mit bis zu 1.000 URLs wird jede Seite analysiert.

Bei Sites mit mehr als 1000 URLs pausiert der Agent und fragt, wie er fortfahren soll:

* Sampling-Obergrenze erhöhen (bis zu 4.000 URLs)
* Nur eine bestimmte Gruppe analysieren (z. B. nur `/products/*` oder `/blog/*`)
* Alle URLs analysieren und die gesamte Site ohne Sampling ausführen

Die URL-Erkennung deckt immer die gesamte Site ab, unabhängig vom Limit für Beispiele. Nur die Phase der Tiefen-Analyse pro Seite ist begrenzt.

Um jede Seite zu überschreiben und zu analysieren, teilen Sie dem Agenten Folgendes mit:

* `analyze all URLs`
* `analyze everything`
* `analyze every page`
* `run the full site`

## Massenimport-Workflow {#bulk-import}

Die Katalogfertigkeit der Site ist Teil des empfohlenen Ansatzes für die Migration einer vollständigen Site.

1. Führen Sie die Site-Katalog-Kenntnisse aus, um den vollständigen Vorlagenkatalog und den Blockkatalog zu erhalten.
1. Öffnen Sie [Bundle HTML-Bericht](#output), um die vom Agenten identifizierten Vorlagen visuell zu überprüfen.
1. Importieren Sie für jede Vorlage manuell die repräsentativen Seiten (aufgeführt in [`template-catalog.json`](#output)) und verfeinern Sie den Import, bis die Ausgabe korrekt ist.
1. Importieren Sie die verbleibenden Seiten für diese Vorlage mithilfe der URL-Liste aus `template-catalog.json` per Massenimport.
1. Wiederholen Sie den Vorgang für jede Vorlage, bis die vollständige Site migriert ist.

## Einschränkungen {#limitations}

Für die Katalogfertigkeit der Site gelten die folgenden Einschränkungen.

* **Nur öffentliche Websites** - Das Ziel muss öffentlich zugänglich sein (keine Authentifizierung, VPN oder Firewall).
* **Dynamische Inhalte werden nicht unterstützt** - Inhalte, für die eine Benutzerinteraktion im DOM erforderlich ist, werden möglicherweise nicht erfasst.
* **Standard-URL-Limit von 1.000** - Die Deep-Analysis-Phase ist standardmäßig auf 1.000 URLs beschränkt, [die überschrieben werden können](#sampling) auf bis zu 4.000 URLs.

