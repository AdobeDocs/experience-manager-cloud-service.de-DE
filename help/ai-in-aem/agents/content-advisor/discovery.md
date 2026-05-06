---
title: Content Discovery Agent
description: Erfahren Sie, wie Sie mit dem Content Discovery Agent relevante AEM-Inhalte bei Bedarf über natürliche Gesprächsaufforderungen bereitstellen können, um ein optimiertes, klick- und kostenloses Discovery-Erlebnis zu erzielen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: 676300cd-b799-4c53-a58e-043e58a2cbc5
source-git-commit: d4b216294791958c29a4cca736bc041a7bf4ad0c
workflow-type: tm+mt
source-wordcount: '2375'
ht-degree: 1%

---


# Content Discovery Agent {#discovery-agent}

Als Teil des AEM [Content Advisor Agent](/help/ai-in-aem/agents/content-advisor/overview.md) stellt der Content Discovery Agent AEM-Inhalte nach Bedarf über natürliche, konversative Eingabeaufforderungen für ein optimiertes, klick- und kostenloses Discovery-Erlebnis bereit. Es durchsucht intelligent Assets, Inhaltsfragmente, AEM Sites-Seiten und adaptives Forms, um relevante Materialien wie Bilder, Videos, PDF-Dokumente, Artikel und Formularvorlagen bereitzustellen. Mit natürlicher Sprache können Sie auf der AEM Assets-Benutzeroberfläche nach Inhalten suchen, ohne komplexe Abfragen zu erstellen oder Filter anzuwenden. Basierend auf Ihrer Eingabeaufforderung gibt der Agent kuratierte Ergebnisse zusammen mit Asset-Metadaten und Bereitstellungs-URLs zurück, die in andere Programme eingebettet werden können.

Zu den wichtigsten Vorteilen des Content Discovery Agent gehören:

* **Einheitliche Inhaltserkennung**: Greifen Sie auf alle Arten von AEM-Inhalten wie Bilder, Videos, PDF-Dokumente, Artikel, Seiten und Formulare über eine einzige Gesprächsoberfläche zu.

* **Schnellere Kampagnenplanung**: Schnelle Erfassung von Visualisierungen und Formularen für Marketing-Kampagnen auf E-Mails, im Web und in sozialen Kanälen.

* **Verbesserte Produktivität**: Verringern Sie den Zeitaufwand für das Durchsuchen von Repositorys oder das Filtern von Metadaten durch eine automatisierte, absichtsbasierte Suche.

* **Konsistente Inhaltsnutzung**: Stellt die Wiederverwendung genehmigter Assets und Fragmente sicher und wahrt so die Markenkonsistenz über alle Kanäle hinweg.

>[!VIDEO](https://video.tv.adobe.com/v/3479983)

>[!IMPORTANT]
>
>KI-generierte Antworten können ungenau oder irreführend sein. Überprüfen Sie unbedingt die vorgeschlagenen Fehlerbehebungen und Antworten.
>
>Siehe auch [Benutzerhandbücher für die generative KI von Adobe Experience Cloud.](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html)

## Kompetenzen {#skills-discovery-agent}

Der Content Discovery Agent bietet die folgenden Fähigkeiten:

* **Inhaltssuche für natürliche Sprachen**

  Der Content Discovery Agent ermöglicht es Benutzenden, relevante Assets, Inhaltsfragmente, adaptive Formulare und AEM Sites-Seiten innerhalb von Adobe Experience Manager (AEM) mithilfe einfacher natürlicher Sprachaufforderungen zu finden, ohne dass komplexe Suchabfragen erforderlich sind.

* **Metadatenbasierte Asset-Erkennung**

  Der Content Discovery Agent sucht anhand von Metadaten, die für Assets in AEM verfügbar sind, anhand von Eingabeaufforderungen in natürlicher Sprache. Benutzer können Assets mithilfe von Metadaten wie Tags, Autoren- oder Herausgeber-E-Mail-IDs, Veröffentlichungs- oder Änderungsdaten, MIME-Typ, Asset-Typ, Status, benutzerdefinierten Metadateneigenschaften, die in Metadatenformularen in der Assets- oder Admin-Ansicht definiert sind, usw. ermitteln. Siehe [Häufige Anwendungsfälle und Beispielaufforderungen](#use-cases-prompts) für eine vollständige Liste.

  Sie können auch mehrere Metadatenfilter in einer einzigen Eingabeaufforderung kombinieren, um die Suchergebnisse zu verfeinern.

* **Ordnerbasierte Inhaltserkennung:**\
  Der Content Discovery Agent kann Assets identifizieren, indem er Eingabeaufforderungen in natürlicher Sprache interpretiert, die auf Ordnernamen in AEM verweisen. Benutzer können den Ordner einfach in ihrer Eingabeaufforderung erwähnen, ohne manuell durch das Repository zu navigieren, was die Anzahl der Klicks, die zum Auffinden des richtigen Inhalts erforderlich sind, erheblich reduziert.

## Personen {#personas-content-discovery}

### Kampagnen-Manager {#campaign-managers}

Der Content Discovery Agent ermöglicht es Kampagnen-Managern, vertrauenswürdige, leistungsstarke Inhalte schnell zu identifizieren und wiederzuverwenden, um Ideen zu generieren.

### Channel-Marketing-Experten {#channel-marketers}

Mit dem Content Discovery Agent können Marketing-Experten für Kanäle relevante Assets effizient finden, um zusammenhängende, kanalübergreifende Erlebnisse zu erstellen.

### DAM-Bibliothekare {#dam-librarians}

DAM-Bibliothekarinnen und -Bibliothekare können Assets kennzeichnen, denen die von der Organisation festgelegten Metadatenstandards fehlen, und so eine konsistente Governance unterstützen sowie sicherstellen, dass Assets vollständig und kanalübergreifend einsatzbereit bleiben.

### Agenturen und Partner {#agencies-partners}

Agenturen und Partner können problemlos markengenehmigte Assets innerhalb von Content Hub finden und sie wiederverwenden, um die kreative Arbeit zu beschleunigen und gleichzeitig an den Markenstandards auszurichten.

## Zugriff {#access}

Sie können in AEM über den KI-Assistenten auf den Content Discovery-Agenten zugreifen. Melden Sie sich bei [`experience.adobe.com`](https://experience.adobe.com) an und Sie können mit dem KI-Assistenten interagieren, indem Sie die Eingabeaufforderung in natürlicher Sprache über das Suchfeld angeben:

![Zugriff auf den Content Discovery Agent](/help/ai-in-aem/agents/content-advisor/assets/access-discovery-agent.png)

Informationen zum MCP-Endpunkt für den Zugriff auf den Content Discovery Agent erhalten Sie beim Adobe-Support.

## Häufige Anwendungsfälle und Beispiel-Eingabeaufforderungen {#use-cases-prompts}

### Assets {#discovery-agent-use-cases-assets}

**Metadatenbasierte Asset-Erkennung**

Der Content Discovery Agent sucht anhand von Metadaten, die für Assets in AEM verfügbar sind, anhand von Eingabeaufforderungen in natürlicher Sprache. Benutzer können Assets mithilfe der folgenden Metadateneigenschaften ermitteln: Tags, Erstellt nach E-Mail-ID, Geändert nach E-Mail-ID, Veröffentlicht nach E-Mail-ID, Erstellungsdatum, Änderungsdatum, Veröffentlichungsdatum, MIME-Typ, Asset-Typ, Status, Dateiformat, Dateigröße, Bildbreite, Bildhöhe und mehrere Metadatenfilter innerhalb einer einzigen Eingabeaufforderung.

Der Content Discovery Agent durchsucht auch die benutzerdefinierten Eigenschaften, die in Metadatenschemata für die Admin-Ansicht und in Metadatenformularen für die Assets-Ansicht verfügbar sind. Sie können Ihre Eingabeaufforderungen entsprechend den Suchwerten ändern, die in diesen benutzerdefinierten Asset-Eigenschaften verfügbar sind.

>[!NOTE]
>
>Um die Erkennungsleistung zu verbessern, indizieren Sie relevante benutzerdefinierte Metadateneigenschaften. Indizierte Eigenschaften ermöglichen es dem Agenten, übereinstimmende Inhalte schneller abzurufen, wenn Benutzer diese Eigenschaften in ihre Eingabeaufforderungen einschließen.


Eingabeaufforderungen im Beispiel:

* **Suche basierend auf Tags**: Zeigt Bilder mit Tags `office` Ordner `WKND` an.
* **Suche basierend auf Dateiformat, Asset-Typ, Asset-Status und „Veröffentlicht per E-Mail-ID**: Zeigt Bilder im `.PNG`-Format an, die `approved` und `published by <user email ID>` sind.
* **Suche basierend auf Dateiformat, Asset-Typ, Asset-Status und Erstellt per E-Mail-ID**: Zeigt Videos im `.mp4` Format an, die genehmigt und `created by <user email ID>` wurden.
* **Suche basierend auf Dateiformat, Asset-Typ, Asset-Status und Erstellungsdatum**: Zeigt Bilder im `.PNG` an, die nach dem 1. Januar 2025 und `published by <user email ID>` erstellt wurden
* **Suche basierend auf MIME-Typ, Erstellungsdatum und Veröffentlicht durch E-Mail-ID**: `image/jpeg` anzeigen, die nach `January 1, 2025` und `published by <user email ID>` erstellt wurden.

* **Nach Assets mit fehlenden Metadaten suchen**: „Assets anzeigen, die in den letzten 90 Tagen erstellt wurden, mit `<Name of metadata property including custom properties>` ist leer“.

* **Suche nach Assets mithilfe von Dateigröße, Bildbreite und Bildhöhe**: Zeigt Bilder an, die größer als 5 MB sind, eine Breite von mehr als 2.000 Pixel und eine Höhe von mehr als 1.200 Pixel haben.

**Unterstützung natürlicher Sprachen für benutzerdefinierte Metadaten**

Der Content Discovery Agent unterstützt das Abfragen benutzerdefinierter Metadateneigenschaften, die in Metadatenschemata definiert sind. Sie können Metadatenwerte direkt in Ihren Eingabeaufforderungen referenzieren, ohne sie mithilfe eines strikten Schlüssel-Wert-Formats angeben zu müssen. Der Agent interpretiert Absicht und gleicht relevante Metadatenfelder automatisch ab.

Eingabeaufforderungen im Beispiel:

* **Suche nach Assets, die einen Eigenschaftswert aufweisen, ist nicht festgelegt**: Suchen Sie nach Assets, deren Kampagnenname nicht festgelegt ist (die Eigenschaft muss für geeignete Ergebnisse indiziert werden).

* **Suche nach Assets mit festgelegtem Eigenschaftswert**: Suchen Sie nach Assets, deren Kampagnenname festgelegt ist (die Eigenschaft muss für geeignete Ergebnisse indiziert werden).

* **Suchen nach Assets, für die ein Eigenschaftswert auf X gesetzt ist**: Suchen Sie nach Assets, deren Kampagnenname „Kaffeetag“ lautet.

* **Suchen nach Assets, für die ein Eigenschaftswert auf einen Wertesatz X, Y** gesetzt ist: Suchen Sie nach Assets, deren Kampagnenname „Coffee-day“ lautet, sowie Assets, deren Kampagnenname „Tea-Day“ ist.

* **Wert eines bestimmten Eigenschaftsfelds anzeigen**: „Abrufen von Kaffee-Assets“ zeigt mir auch den Kampagnennamen dieser Assets an.

* **Nach Assets suchen, die einer datumsbasierten Eigenschaftsbedingung entsprechen**: Abrufen von Assets, deren Lizenz nicht abgelaufen ist.












**Ordnerbasierte Inhaltserkennung:**\
Der Content Discovery Agent kann Assets identifizieren, indem er Eingabeaufforderungen in natürlicher Sprache interpretiert, die auf Ordnernamen in AEM verweisen. Benutzer können den Ordner einfach in ihrer Eingabeaufforderung erwähnen, ohne manuell durch das Repository zu navigieren, was die Anzahl der Klicks, die zum Auffinden des richtigen Inhalts erforderlich sind, erheblich reduziert.

Eingabeaufforderungen im Beispiel:

* Gibt es SVGs im Ordner `WKND`?
* Anzeigen von Assets, die nach dem `Nov 1 2025` in Ordner `WKND` geändert wurden.
* Auflisten `lifestyle` Bilder im Ordner `WKND`.

**Zusätzliche Fragen zur Aktivierung der ordnerbasierten Inhaltssuche**

Wenn ein Ordnername in einer Eingabeaufforderung enthalten ist (ohne den vollständigen Asset-Pfad), prüft der Content Discovery-Agent zunächst im Stammpfad `/content/dam/<folder-name>`, ob ein übereinstimmender Ordner vorhanden ist.

Wenn auf der Stammebene kein übereinstimmender Ordner gefunden wird, schlägt der Agent alternative Ordnerpfade vor, bei denen der angegebene Ordnername im Repository vorhanden ist. Dies hilft Benutzenden, den richtigen Speicherort schnell zu identifizieren, ohne die Ordnerstruktur manuell zu durchsuchen.

Beispielsweise wurde der Pfad `/content/dam/<folder-name>` nicht gefunden. Meintest du eine davon?

* Option 1

* Option 2

**Formatbasierte Asset-Erkennung**

Der Content Discovery Agent kann Assets identifizieren, die bestimmte Qualitätsanforderungen erfüllen, z. B. das Dateiformat, sodass Benutzende Produktvisualisierungen, die für eine hochwertige Bereitstellung und Wiederverwendung über verschiedene Kanäle hinweg bereit sind, schnell finden können.

Eingabeaufforderung für Beispiel:

Suchen Sie Produktverpackung PNG-Bilder.

**Orientierungsbasierte Inhaltssuche**

Der Content Discovery Agent kann Assets filtern, indem er visuelle Attribute erkennt, z. B. das Vorhandensein von Personen und die Ausrichtung eines Bildes. Dadurch können Benutzende Inhalte schnell auf die relevantesten Visualisierungen beschränken, ohne mehrere Filter in AEM manuell anwenden zu müssen.

Eingabeaufforderung für Beispiel:

Assets mit Person in Querformat anzeigen.

**Suchergebnisse erweitern**

Der Content Discovery Agent gibt für eine Eingabeaufforderung die 20 relevantesten Ergebnisse pro Inhaltstyp zurück. Wenn zusätzliche übereinstimmende Ergebnisse verfügbar sind, können Benutzer den nächsten Satz anfordern, indem sie eine Folgenachricht eingeben, z. B. `show me more`. Der Agent ruft dann den nächsten Ergebnissatz aus der ursprünglichen Suche ab, sodass Benutzende nach und nach größere Ergebnissätze durchsuchen können, ohne die Eingabeaufforderung zu verfeinern.

**Suchen ähnlicher Assets**

Mit dem Content Discovery Agent können Benutzer Assets finden, die einem bestimmten in den Suchergebnissen zurückgegebenen Ergebnis ähneln. Nachdem der Agent die wichtigsten Ergebnisse für eine Eingabeaufforderung angezeigt hat, können Sie ähnliche Assets anfordern, indem Sie auf die Position eines Elements in der Ergebnisliste verweisen. Beispielsweise wird der Agent durch eine Eingabeaufforderung wie `find assets similar to the 3rd result` angewiesen, andere relevante Assets im Zusammenhang mit diesem Element zu identifizieren und zurückzugeben. Dies hilft Benutzenden, verwandte Inhalte schnell zu finden, ohne eine neue Suchaufforderung zu erstellen.

**Sortieren von Suchergebnissen**

Mit dem Content Discovery Agent können Benutzer Suchergebnisse direkt innerhalb ihrer Eingabeaufforderungen in natürlicher Sprache sortieren. Benutzer können Sortierkriterien wie Änderungsdatum, Erstellungsdatum oder Asset-Name angeben und auf- oder absteigende Reihenfolge wählen.

Eingabeaufforderungen im Beispiel:

* Ermitteln Sie Berg-Bilder, sortiert nach Änderungsdatum in absteigender Reihenfolge (zeigt zuerst die zuletzt geänderten Assets an).

* Bergbilder sortiert nach Namen in aufsteigender Reihenfolge anzeigen (zeigt die Bildnamen beginnend mit dem Buchstaben A, gefolgt von B usw.).

**Kontextabhängige Umgebungserkennung**

In der Admin-Ansicht erkennt der Content Discovery Agent automatisch die Authoring-Umgebung und verwendet sie, um Eingabeaufforderungen aufzulösen, ohne die Autoren-URL explizit angeben zu müssen.

### AEM Sites-Seiten {#content-discovery-agent-aem-sites-pages}

Der Content Discovery Agent hilft Benutzenden, relevante AEM Sites-Seiten schnell zu finden, indem er die Eingabeaufforderungen in natürlicher Sprache interpretiert, die auf Seitenthemen, Kampagnen oder andere kontextuelle Schlüsselwörter verweisen. Der Agent führt eine Volltextsuche anhand der Keywords in der Eingabeaufforderung durch, um übereinstimmende Seiten im AEM-Repository zu identifizieren, sodass Sie die Sites-Struktur nicht manuell durchsuchen müssen.

Eingabeaufforderungen für Beispiel:

* Suchen Sie alle AEM Sites-Seiten für die Sommerkampagne.

* Suchen nach AEM Sites-Seiten mit einem Kaffee-Design.

### Inhaltsfragmente {#discovery-agent-use-cases-content-fragments}

Der Content Discovery Agent hilft Benutzenden, schnell die richtigen Inhaltsfragmente zu finden, indem er natürliche Sprachverweise auf Kampagnennamen, Produktmarken, den Veröffentlichungsstatus und die aktuelle Erstellungsaktivität interpretiert. Damit können Teams kampagnenbereite Fragmente aufdecken und markenspezifische Inhalte anzeigen, ohne manuell durch Ordner zu navigieren oder mehrere Filter in AEM anzuwenden.

Eingabeaufforderungen im Beispiel:

* Inhaltsfragmente zum Erstellen einer WKND-Angebotskampagne anzeigen.

* Inhaltsfragment für americano-Getränk anzeigen.

* Alle veröffentlichten Inhaltsfragmente für WKND-Getränke anzeigen.

* Auflisten aller in den letzten 2 Wochen erstellten Inhaltsfragmente.

### Forms {#discovery-agent-use-cases-forms}

Der Content Discovery Agent hilft Ihnen, adaptive Formulare mithilfe von Eingabeaufforderungen in natürlicher Sprache schnell zu finden. Sie durchsucht den Formularinhalt und die Metadaten, um Übereinstimmungen auf der Grundlage von Schlüsselwörtern in Ihren Eingabeaufforderungen zu finden. Das bedeutet, dass Sie relevante Formulare erfolgreich finden können, auch wenn Ihre Suchbegriffe nicht im Titel oder in der Beschreibung des Formulars enthalten sind.

Eingabeaufforderungen im Beispiel:

* Alle Kreditantragsformulare anzeigen.
* Formulare suchen, um einen Agenten zu beantragen.
* Kontaktformulare suchen.
* Ich suche Onboarding-Formulare für Mitarbeiter.
* Kreditkartenantragsformulare anzeigen.

Hinweis: Die Formularerkennung unterstützt derzeit nur Edge Delivery Services-Formulare, und die Tag-basierte Suche ist derzeit nicht für Formulare verfügbar.

## Suchergebnisse {#discovery-agent-search-results}

### Assets {#discovery-agent-search-results-assets}

Der Content Discovery Agent gibt die wichtigsten Ergebnisse für jede Abfrage aus, sortiert nach Relevanz, um sicherzustellen, dass die exakten Übereinstimmungen zuerst angezeigt werden. Der Agent kombiniert metadatengesteuerte Abfragen mit der semantischen Suche, um einen fokussierten Satz wahrscheinlicher Übereinstimmungen zusammenzustellen, und verwendet dann einen LLM, um sie nach der Benutzerabsicht zu ordnen. Dieser gemischte Ansatz liefert genaue, kontextbezogene Ergebnisse, ohne dass dies vollständig von einer direkten Keyword-Übereinstimmung abhängt.

Jedes Ergebnis wird als Asset-Karte angezeigt, die den Asset-Namen, die Vorschau und wichtige Metadaten wie Beschreibung und Format enthält. Sie können auf das Informationssymbol auf einer Karte klicken, um zusätzliche Asset-Eigenschaften anzuzeigen.

Verwenden Sie die Option **Tabelle anzeigen**, um Ergebnisse in einem tabellarischen Format anzuzeigen. Klicken Sie **Alle Ergebnisse anzeigen**, um den vollständigen Satz von 20 abgerufenen Assets im rechten Bereich anzuzeigen.

Jedes Ergebnis enthält auch wichtige Asset-Metadaten wie den Asset-Pfad, die Größe, das Erstellungsdatum und das Erstellungsdatum sowie das Änderungsdatum zusammen mit dem Benutzer, der das Asset geändert hat, das Format und die Beschreibung. Wenn sich ein Asset im Status Genehmigt befindet, umfassen die Ergebnisse auch [Dynamic Media mit OpenAPI-URL](/help/assets/dynamic-media-open-apis-overview.md). Sie können auf den Asset-Pfad klicken, um nahtlos zum Asset-Speicherort in AEM zu navigieren.

![Suchen nach Assets mit dem Content Discovery Agent](/help/ai-in-aem/agents/content-advisor/assets/search-results-content-discovery-agent.png)

Sie können diese Asset-Details verwenden, um schnell zu beurteilen, ob ein Asset die Anforderungen erfüllt, ohne zu jedem Asset navigieren zu müssen, um diese Details anzuzeigen.

>[!NOTE]
>
>Das [Dynamic Media-URL](/help/assets/dynamic-media/dynamic-media.md)-Feld wird nur dann in den Suchergebnissen angezeigt, wenn das Asset veröffentlicht wurde und Sie über eine gültige Dynamic Media-Lizenz verfügen. Ebenso wird [&#x200B; Feld „Dynamic Media mit OpenAPI-](/help/assets/dynamic-media-open-apis-overview.md)&quot; nur angezeigt, wenn Sie über eine gültige Dynamic Media-Lizenz verfügen und Dynamic Media mit OpenAPI für Ihre AEM as a Cloud Service-Instanz aktiviert ist.

### Inhaltsfragmente {#discovery-agent-search-results-content-fragments}

Der Content Discovery Agent bietet Volltextsuchfunktionen für Inhaltsfragmente, wodurch die besten Ergebnisse zurückgegeben werden, die mit der angegebenen Eingabeaufforderung am besten übereinstimmen. Jedes Ergebnis enthält den Namen des Inhaltsfragments zusammen mit wichtigen Metadatenfeldern wie dem Pfad des Inhaltsfragments, dem Ersteller, dem Erstellungsdatum, Varianten, dem letzten Modifikator und dem Datum der letzten Änderung.

![Durchsuchen von Inhaltsfragmenten mit dem Content Discovery Agent](/help/ai-in-aem/agents/content-advisor/assets/search-content-fragments-discovery-agent.png)

Sie können auf den Pfad des Inhaltsfragments klicken, um in AEM nahtlos zum Speicherort des Inhaltsfragments zu navigieren.

## Best Practices bei der Eingabeaufforderung {#prompting-best-practices-discovery-agent}

Geben Sie in Ihren Eingabeaufforderungen in natürlicher Sprache präzise Details an, damit der Agent genaue und relevante Ergebnisse zurückgeben kann. Je klarer Sie beschreiben, wonach Sie suchen, desto besser kann der Agent die Ausgabe verfeinern und eingrenzen. Sie haben beispielsweise folgende Möglichkeiten:

* Definieren Sie Asset-Metadaten wie Tags, Ordnernamen, Erstellungsdaten, Veröffentlichungsstatus und Autorennamen in Ihren Eingabeaufforderungen zum Filtern von Assets.

* Verwenden Sie Ihre organisationsspezifischen Metadaten, z. B. Kategorien (Laufschuhe, Elektronik), Jahreszeiten (Herbst, Frühling), Ereignisse (Black Friday, Produkteinführung) und Kanäle (Web, E-Mail, Druck), um Inhalte weiter zu filtern.

## Einschränkungen {#limitations-discovery-agent}

* Der Content Discovery Agent unterstützt nur dimensionsbasierte Eingabeaufforderungen für die Formattypen „Bild“ und &quot;SVG&quot;. Zum Beispiel: `Find images wider than 1080px`.

* Content Hub-Administratoren können über das Content Hub-Portal auf den Content Discovery Agent zugreifen. Die Ergebnisse werden jedoch nur von der AEM-Autoreninstanz abgerufen. Benutzende mit Content Hub Limited können derzeit nicht von den Vorteilen des Content Discovery Agent profitieren (in Kürze verfügbar).

* Die Funktion „Ähnliche suchen“ funktioniert nur für Bilder mit [Smart-Tags-Verbesserungen](/help/assets/ai-generated-metadata-assets-view.md).
