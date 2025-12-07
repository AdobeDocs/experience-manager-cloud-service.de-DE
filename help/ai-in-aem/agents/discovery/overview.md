---
title: Übersicht über den Discovery Agent
description: Erfahren Sie, wie Sie mit dem Discovery Agent relevante AEM-Inhalte bei Bedarf über natürliche Gesprächsaufforderungen bereitstellen können, um ein optimiertes, klick- und kostenloses Discovery-Erlebnis zu erzielen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: f83324be68bdab65e5c76ef336eb7e4a2e318dd1
workflow-type: tm+mt
source-wordcount: '1265'
ht-degree: 1%

---


# Discovery Agent {#discovery-agent}

Der Discovery Agent stellt AEM-Inhalte bei Bedarf über natürliche, dialogorientierte Eingabeaufforderungen für ein optimiertes, klick- und starres Erkennungserlebnis bereit. Es durchsucht intelligent Assets, Inhaltsfragmente und adaptives Forms, um relevante Materialien wie Bilder, Videos, PDF-Dokumente, Artikel und Formularvorlagen bereitzustellen. Mit natürlicher Sprache können Sie auf der AEM Assets-Benutzeroberfläche nach Inhalten suchen, ohne komplexe Abfragen zu erstellen oder Filter anzuwenden. Basierend auf Ihrer Eingabeaufforderung gibt der Agent kuratierte Ergebnisse zusammen mit Asset-Metadaten und Bereitstellungs-URLs zurück, die in andere Programme eingebettet werden können.

Zu den wichtigsten Vorteilen von Discovery Agent gehören:

* **Einheitliche Inhaltserkennung**: Greifen Sie auf alle Arten von AEM-Inhalten wie Bilder, Videos, PDF-Dokumente, Artikel und Formulare über eine einzige Gesprächsoberfläche zu.

* **Schnellere Kampagnenplanung**: Schnelle Erfassung von Visualisierungen und Formularen für Marketing-Kampagnen auf E-Mails, im Web und in sozialen Kanälen.

* **Verbesserte Produktivität**: Verringern Sie den Zeitaufwand für das Durchsuchen von Repositorys oder das Filtern von Metadaten durch eine automatisierte, absichtsbasierte Suche.

* **Konsistente Inhaltsnutzung**: Stellt die Wiederverwendung genehmigter Assets und Fragmente sicher und wahrt so die Markenkonsistenz über alle Kanäle hinweg.

>[!IMPORTANT]
>
>KI-generierte Antworten können ungenau oder irreführend sein. Überprüfen Sie unbedingt die vorgeschlagenen Fehlerbehebungen und Antworten.
>
>Siehe auch [Benutzerhandbücher für die generative KI von Adobe Experience Cloud](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

## Kompetenzen {#skills-discovery-agent}

Der Discovery Agent bietet die folgenden Fähigkeiten:

* **Inhaltssuche für natürliche Sprachen**\
  Der Discovery Agent ermöglicht es Benutzenden, relevante Assets, Inhaltsfragmente und adaptive Formulare in Adobe Experience Manager (AEM) mithilfe einfacher natürlicher Sprachaufforderungen zu finden - keine komplexen Suchabfragen erforderlich.

* **Tag-basierte Asset-Erkennung**

  Der Discovery Agent verwendet natürliche Eingabeaufforderungen, um Assets zu finden, die bestimmten Tags im AEM-Repository zugeordnet sind, sodass Benutzende schnell auf Inhalte zugreifen können, die gemäß der Taxonomie des Unternehmens organisiert oder nicht organisiert sind.

* **Ordnerbasierte Inhaltserkennung:**\
  Der Discovery Agent kann Assets identifizieren, indem er Eingabeaufforderungen in natürlicher Sprache interpretiert, die auf Ordnernamen in AEM verweisen. Benutzer können den Ordner einfach in ihrer Eingabeaufforderung erwähnen, ohne manuell durch das Repository zu navigieren, was die Anzahl der Klicks, die zum Auffinden des richtigen Inhalts erforderlich sind, erheblich reduziert.

## Personen {#personas-discovery-agent}

### Kampagnen-Manager {#campaign-managers}

Der Discovery Agent ermöglicht es Campaign-Managern, vertrauenswürdige, leistungsstarke Inhalte schnell zu identifizieren und wiederzuverwenden.

### Channel-Marketing-Experten {#channel-marketers}

Der Discovery Agent ermöglicht es Channel-Marketern, relevante Assets effizient zu finden, um zusammenhängende Multi-Channel-Erlebnisse zu erstellen.

### DAM-Bibliothekare {#dam-librarians}

Die DAM-Bibliothekare können Assets kennzeichnen, denen die von der Organisation festgelegten Metadatenstandards fehlen, und so eine konsistente Governance unterstützen sowie sicherstellen, dass Assets vollständig und kanalübergreifend einsatzbereit bleiben.

### Agenturen und Partner {#agencies-partners}

Agenturen und Partner können problemlos markenbestätigte Assets innerhalb von Content Hub finden und sie wiederverwenden, um die kreative Arbeit zu beschleunigen und gleichzeitig an den Markenstandards auszurichten.

## Wie greife ich auf den Discovery Agent zu? {#access-discovery-agent}

Sie können über den KI-Assistenten auf die Agenten in AEM zugreifen. Melden Sie sich bei experience.adobe.com an und Sie können mit dem KI-Assistenten interagieren, indem Sie Ihre Eingabeaufforderung in natürlicher Sprache mithilfe des Suchfelds angeben:

![Zugriff auf Discovery Agent](/help/ai-in-aem/agents/discovery/assets/access-discovery-agent.png)

Wenden Sie sich an den Adobe-Support, um Informationen zum MCP-Endpunkt für den Zugriff auf den Discovery Agent zu erhalten.

## Häufige Anwendungsfälle und Beispielaufforderungen {#use-cases-prompts}

### Assets {#discovery-agent-use-cases-assets}

**Tag-basierte Asset-Erkennung**

Der Discovery Agent verwendet natürliche Sprachaufforderungen, um Assets zu finden, die bestimmten Tags im AEM-Repository zugeordnet sind, sodass Benutzende schnell auf Inhalte zugreifen können, die gemäß der Taxonomie ihres Unternehmens organisiert sind.

Eingabeaufforderung für Beispiel:

Bilder mit Tags `office` Ordner `WKND` anzeigen.

**Ordnerbasierte Inhaltserkennung:**\
Der Discovery Agent kann Assets identifizieren, indem er Eingabeaufforderungen in natürlicher Sprache interpretiert, die auf Ordnernamen in AEM verweisen. Benutzer können den Ordner einfach in ihrer Eingabeaufforderung erwähnen, ohne manuell durch das Repository zu navigieren, was die Anzahl der Klicks, die zum Auffinden des richtigen Inhalts erforderlich sind, erheblich reduziert.

Eingabeaufforderungen im Beispiel:

* Gibt es SVGs im Ordner `WKND`?
* Anzeigen von Assets, die nach dem `Nov 1 2025` in Ordner `WKND` geändert wurden.
* Auflisten `lifestyle` Bilder im Ordner `WKND`.

**Formatbasierte Asset-Erkennung**

Der Discovery Agent kann Assets identifizieren, die bestimmten Qualitätsanforderungen entsprechen, z. B. dem Dateiformat, sodass Benutzer Produktvisualisierungen, die für eine hochwertige Bereitstellung und Wiederverwendung über verschiedene Kanäle hinweg bereit sind, schnell finden können.

Eingabeaufforderung für Beispiel:

Suchen Sie Produktverpackung PNG-Bilder.

**Orientierungsbasierte Inhaltssuche**

Der Discovery Agent kann Assets filtern, indem er visuelle Attribute erkennt, z. B. das Vorhandensein von Personen und die Ausrichtung eines Bildes. Dadurch können Benutzende Inhalte schnell auf die relevantesten Visualisierungen beschränken, ohne mehrere Filter in AEM manuell anwenden zu müssen.

Eingabeaufforderung für Beispiel:

Assets mit Person in Querformat anzeigen.

### Inhaltsfragmente {#discovery-agent-use-cases-content-fragments}

Der Discovery Agent hilft Benutzern, schnell die richtigen Inhaltsfragmente zu finden, indem natürliche Sprachverweise auf Kampagnennamen, Produktmarken, Veröffentlichungsstatus und die aktuelle Erstellungsaktivität interpretiert werden. Damit können Teams kampagnenbereite Fragmente aufdecken und markenspezifische Inhalte anzeigen, ohne manuell durch Ordner zu navigieren oder mehrere Filter in AEM anzuwenden.

Eingabeaufforderungen im Beispiel:

* Inhaltsfragmente zum Erstellen einer WKND-Angebotskampagne anzeigen.

* Inhaltsfragment für americano-Getränk anzeigen.

* Alle veröffentlichten Inhaltsfragmente für WKND-Getränke anzeigen.

* Auflisten aller in den letzten 2 Wochen erstellten Inhaltsfragmente.

### Forms {#discovery-agent-use-cases-forms}

Der Discovery Agent hilft Ihnen, adaptive Formulare mithilfe natürlicher Eingabeaufforderungen schnell zu finden. Sie durchsucht den Formularinhalt und die Metadaten, um Übereinstimmungen auf der Grundlage von Schlüsselwörtern in Ihren Eingabeaufforderungen zu finden. Das bedeutet, dass Sie relevante Formulare erfolgreich finden können, auch wenn Ihre Suchbegriffe nicht im Titel oder in der Beschreibung des Formulars enthalten sind.

Eingabeaufforderungen im Beispiel:

* Alle Kreditantragsformulare anzeigen.
* Formulare suchen, um sich für eine Stelle zu bewerben.
* Kontaktformulare suchen.
* Ich suche Onboarding-Formulare für Mitarbeiter.
* Kreditkartenantragsformulare anzeigen.

Hinweis: Die Formularerkennung unterstützt derzeit nur Edge Delivery Services-Formulare, und die Tag-basierte Suche ist derzeit nicht für Formulare verfügbar.

## Suchergebnisse {#discovery-agent-search-results}

### Assets {#discovery-agent-search-results-assets}

Der Discovery Agent gibt die wichtigsten Ergebnisse für jede Abfrage aus, sortiert nach Relevanz, um sicherzustellen, dass die exakten Übereinstimmungen zuerst angezeigt werden. Der Agent kombiniert metadatengesteuerte Abfragen mit der semantischen Suche, um einen fokussierten Satz wahrscheinlicher Übereinstimmungen zusammenzustellen, und verwendet dann einen LLM, um sie nach der Benutzerabsicht zu ordnen. Dieser gemischte Ansatz liefert genaue, kontextbezogene Ergebnisse, ohne dass dies vollständig von einer direkten Keyword-Übereinstimmung abhängt.

Jedes Ergebnis enthält den Asset-Namen zusammen mit wichtigen Asset-Metadaten wie den Asset-Pfad, den Ersteller, das Erstellungsdatum, den Titel, die Beschreibung, das Format, den letzten Modifikator, das Datum der letzten Änderung, die Dateigröße, die [Dynamic Media-URL](/help/assets/dynamic-media/dynamic-media.md) und die zugehörigen Tags. Wenn sich ein Asset im Status Genehmigt befindet, umfassen die Ergebnisse auch [Dynamic Media mit OpenAPI-URL](/help/assets/dynamic-media-open-apis-overview.md).

Sie können auf den Asset-Pfad klicken, um nahtlos zum Asset-Speicherort in AEM zu navigieren.

![Suche nach Assets mit dem Discovery Agent](/help/ai-in-aem/agents/discovery/assets/search-results-discovery-agent.png)

Sie können diese Asset-Details verwenden, um schnell zu beurteilen, ob ein Asset die Anforderungen erfüllt, ohne zu jedem Asset navigieren zu müssen, um diese Details anzuzeigen.

>[!NOTE]
>
>Das [Dynamic Media-URL](/help/assets/dynamic-media/dynamic-media.md)-Feld wird nur dann in den Suchergebnissen angezeigt, wenn das Asset veröffentlicht wurde und Sie über eine gültige Dynamic Media-Lizenz verfügen. Ebenso wird [ Feld „Dynamic Media mit OpenAPI-](/help/assets/dynamic-media-open-apis-overview.md)&quot; nur angezeigt, wenn Sie über eine gültige Dynamic Media-Lizenz verfügen und Dynamic Media mit OpenAPI für Ihre AEM as a Cloud Service-Instanz aktiviert ist.

### Inhaltsfragmente {#discovery-agent-search-results-content-fragments}

Der Discovery Agent bietet Volltextsuchfunktionen für Inhaltsfragmente, wobei die besten Ergebnisse zurückgegeben werden, die mit der angegebenen Eingabeaufforderung am besten übereinstimmen. Jedes Ergebnis enthält den Namen des Inhaltsfragments zusammen mit wichtigen Metadatenfeldern wie dem Pfad des Inhaltsfragments, dem Ersteller, dem Erstellungsdatum, Varianten, dem letzten Modifikator und dem Datum der letzten Änderung.

![Inhaltsfragmente mit dem Discovery-Agenten durchsuchen](/help/ai-in-aem/agents/discovery/assets/search-content-fragments-discovery-agent.png)

Sie können auf den Pfad des Inhaltsfragments klicken, um in AEM nahtlos zum Speicherort des Inhaltsfragments zu navigieren.

## Best Practices bei der Eingabeaufforderung {#prompting-best-practices-discovery-agent}

Geben Sie in Ihren Eingabeaufforderungen in natürlicher Sprache präzise Details an, damit der Agent genaue und relevante Ergebnisse zurückgeben kann. Je klarer Sie beschreiben, wonach Sie suchen, desto besser kann der Agent die Ausgabe verfeinern und eingrenzen. Sie haben beispielsweise folgende Möglichkeiten:

* Definieren Sie Asset-Metadaten wie Tags, Ordnernamen, Erstellungsdaten, Veröffentlichungsstatus und Autorennamen in Ihren Eingabeaufforderungen zum Filtern von Assets.

* Verwenden Sie Ihre organisationsspezifischen Metadaten, z. B. Kategorien (Laufschuhe, Elektronik), Jahreszeiten (Herbst, Frühling), Ereignisse (Black Friday, Produkteinführung) und Kanäle (Web, E-Mail, Druck), um Inhalte weiter zu filtern.

