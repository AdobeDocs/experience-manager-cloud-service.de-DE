---
title: Auftrag zur Inhaltsaktualisierung
description: Erfahren Sie, was der Inhaltsaktualisierungsauftrag von Brand Experience Agent ist und was er für Sie tun kann.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: dcf2b9f2966144fac969563a395a72fa81ce2751
workflow-type: tm+mt
source-wordcount: '1109'
ht-degree: 1%

---


# Auftrag zur Inhaltsaktualisierung {#content-update}

Der Auftrag zum Aktualisieren von Inhalten des [Experience Production Agent](/help/ai-in-aem/agents/brand-experience/experience-production/overview.md) automatisiert die Inhaltserstellung, um alltägliche Aufgaben für Adobe Experience Manager (AEM) as a Cloud Service und Edge Delivery Services zu beschleunigen.

## Überblick {#overview}

Der Auftrag zur Inhaltsaktualisierung aktualisiert vorhandene Inhalte, einschließlich Inhaltsfragmenten, Seiten, Formularen und Assets. Der Auftrag kann Aktionen durchführen, wie z. B. Aktualisieren, Entfernen, Ersetzen oder Hinzufügen von Inhaltselementen, um Erlebnisse genau und aktuell zu halten. Eingaben können Beschreibungen in natürlicher Sprache sein und bei Verwendung mit Jira-PDFs und Screenshots auch Eingaben liefern.

Der Auftrag zur Inhaltsaktualisierung wandelt die von Ihnen bereitgestellten Details entweder durch natürliche Sprache oder visuelle Elemente in Inhaltsaktualisierungen auf Ihrer Seite um. Sie geben die URL einer Seite an, die aktualisiert werden muss, zusammen mit Details dazu, was aktualisiert werden muss, und der Agentenauftrag führt Ihre Aufgabe aus. Bei Verwendung mit AEM as a Cloud Service erstellt der Auftrag einen neuen [Launch](/help/sites-cloud/authoring/launches/overview.md), damit Sie die Aktualisierungen vor der Anwendung überprüfen können. Bei Verwendung mit der Dokumenterstellung erstellt der Auftrag eine neue [Version](https://experienceleague.adobe.com/de/docs/experience-manager-learn/sites/document-authoring/how-to/document-versions#).

>[!VIDEO](https://video.tv.adobe.com/v/3486418?learn=on)

## Funktionen {#capabilities}

Sie können wie folgt auf den Auftrag zur Inhaltsaktualisierung zugreifen:

* [Der KI-Assistent](#ai-assistant)
* [Jira](#jira)

## KI-Assistent {#ai-assistant}

Sie können über den KI-Assistenten auf den Auftrag in AEM zugreifen.

Öffnen Sie den [KI](/help/implementing/cloud-manager/ai-assistant-in-aem.md#ai-use)Assistenten) in der Symbolleiste oben rechts, um eine Konversation zu starten.

![Symbol „KI-Assistent“ in der Symbolleiste](/help/ai-in-aem/agents/brand-experience/experience-production/assets/ai-assistant-icon.png)

### Konfigurieren der Veröffentlichungs-URL {#configuring-the-publish-url}

Um den Agenten anzuweisen, wo Aktualisierungen angewendet werden sollen, müssen Sie einen Seitenlink angeben. Sie können entweder eine Autoren-URL oder eine Veröffentlichungs-URL angeben.

Um eine Publishing-URL (öffentlich zugängliche URL) zu verwenden, muss eine einmalige Konfiguration vorgenommen werden:

* Voraussetzungen:

   * Um die Konfiguration vorzunehmen, muss der Benutzer über Systemadministrator- oder Produktadministratorrechte verfügen.

* Konfiguration:

   1. Rufen Sie den Auftrag zur Inhaltsaktualisierung auf, indem Sie eine Inhaltsaktualisierung für die URL anfordern.
   1. Der Assistent führt Sie durch die Konfiguration und stellt Ihnen eine Reihe von Fragen.
   1. Nach Abschluss des Vorgangs ist die Veröffentlichungs-URL konfiguriert und kann verwendet werden.

Beispiel:

![Auftrag zur Inhaltsaktualisierung - Veröffentlichungs-URL konfigurieren](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-publish-url-configuration.png)

### Eingabeaufforderungen {#prompts}

Um Inhaltsaktualisierungen zu initiieren, können Sie eine Vielzahl von Eingabeaufforderungen in natürlicher Sprache eingeben. Sie müssen die URL der öffentlichen Seite (Veröffentlichungs-) oder die URL der Autorenumgebung der Seite angeben, die Sie aktualisieren möchten. Einige, aber nicht alle der unterstützten Verben; ersetzen, aktualisieren, entfernen, ändern, überarbeiten, ändern, anpassen, löschen.

### Eingabeaufforderungen {#sample-prompts}

Zu den Beispielaufforderungen gehören:

* auf `<your-publish-URL>` Update „Dein perfekter Kaffee ist noch vier Fragen entfernt!“ zu „Dein Kaffee, dein Weg!“
* Ersetzen `<your-author-env-URL>` das Bild von „holdingcup.png“ durch „stairhead.png“
* auf `<your-publish-URL>` Schaltfläche „Take our Coffee Quiz“ in eine ansprechendere Version ändern“
* entfernt `<your-author-env-URL>` den Abschnitt „Nicht beanspruchte Belohnungen sind ein verpasstes Geschenk!“
* Bei `<your-author-env-URL>` Aktualisierung basierend auf dem angehängten

### Datei-Upload im KI-Assistenten {#file-upload-in-ai-assistant}

Neben der direkten Eingabe von Eingabeaufforderungen in natürlicher Sprache können Sie auch ein Dokument hochladen, um Änderungen anzufordern.

Verwenden Sie das Symbol `+` unten links im Eingabeaufforderungsmenü, um eine Datei hochzuladen, in der Ihre Anforderungen angegeben sind. Zu den unterstützten Dateiformaten gehören PDF, JPG, PNG, DOCX und andere.

![Auftrag zur Inhaltsaktualisierung - Datei-Upload](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-file-upload.png)

Beispiel: eine PDF mit Anmerkungen, die die angeforderten Änderungen angibt:

![Auftrag zur Inhaltsaktualisierung - PDF mit Anmerkungen](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-annotated-pdf.png)

>[!VIDEO](https://video.tv.adobe.com/v/3491297?learn=on)

### Orchestrierung mit dem Brand Governance-Agenten  {#orchestration-with-the-brand-governance-agent}

Wenn das Unternehmen seine Markenrichtlinie importiert hat, verwendet der Auftrag zur Inhaltsaktualisierung diese Richtlinie während der Aktualisierung der agenten Inhalte (siehe [Übersicht](#overview) Video).

Für eine *präskriptive* Eingabeaufforderung wie:

* `on <your-publish-URL> update “Your perfect coffee is four questions away!” to “Your coffee, your way!”`

Der Vorgang Inhaltsaktualisierung koordiniert sich mit dem [Brand Governance Agent](/help/ai-in-aem/agents/brand-experience/overview.md) und benachrichtigt den Benutzer, wenn die bereitgestellte Kopie markenintern ist oder nicht.

![Auftrag zur Inhaltsaktualisierung - Orchestrierung mit dem Brand Governance Agent](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-brand-experience.png)

Für abstraktere Eingabeaufforderungen wie:

* `on <your-publish-env-URL> change “Take our Coffee Quiz” button to a more engaging version`

Bei der Generierung verwendet der Agent die Markenrichtlinien, um sicherzustellen, dass die Ausgabe markenintern erfolgt.

## Jira {#jira}

Durch die Verwendung des Auftrags zur Inhaltsaktualisierung mit Jira können Sie ein Ticket mit Anweisungen erstellen, die Ihre Änderungen automatisieren.

### Erstellen eines Tickets {#create-a-ticket}

Erstellen Sie ein Jira-Ticket (beliebiger Typ). Im Feld „Beschreibung **Ihres Tickets** Sie zwei wichtige Details:

1. Die öffentlich zugängliche URL der Seite, die Sie bearbeiten müssen.

1. Die erforderlichen Änderungen.

   Der Auftrag unterstützt die folgenden Formate, um Ihre Änderungen zu beschreiben:

   * Natürliche Sprache in der Ticketbeschreibung
      * Beispiel: „Ändern der Überschrift von X in Y“
   * PDF mit Anmerkungen
      * Erstellen Sie beispielsweise eine PDF Ihrer Seite und fügen Sie Anmerkungen hinzu, die detailliert beschreiben, was Sie ändern möchten
   * Kommentare in angehängter PDF
      * Erstellen Sie beispielsweise eine PDF Ihrer Seite und fügen Sie Kommentare hinzu, die detailliert beschreiben, was Sie ändern möchten
   * Angehängter Screenshot
      * Beispiel: Erstellen Sie einen Screenshot eines Teils Ihrer Seite und fügen Sie Anmerkungen hinzu, die detailliert beschreiben, was Sie ändern möchten
   * Angehängte Microsoft Word-Datei mit natürlichen Sprachänderungen

### Aufrufen des Vorgangs über Ihr Ticket {#invoke-the-job-from-your-ticket}

Um den Auftrag zu verwenden, fügen Sie Ihrem Ticket einen Kommentar hinzu. Geben Sie im Kommentar den Auftrag mit dem Symbol &quot;`@`&quot; zusammen mit den Anweisungen an.

Beispiel:

* `@aemagent@adobe.com process this ticket`

### Interaktion des Auftrags {#how-the-agent-interacts}

Nachdem Sie einen Befehl für den Auftrag ausgegeben haben, antwortet er mit Kommentaren in der Jira. In den Kommentaren werden der Fortschritt des Vorgangs und die ergriffenen Maßnahmen beschrieben.

Wenn ein `process` Befehl an den Trigger aktualisiert wird, können die Antworten der folgenden Sequenz folgen:

* Der erste Kommentar bestätigt, dass der Vorgang gestartet wurde.

* Nach Abschluss der Aufgabe antwortet der Auftrag mit einem weiteren Kommentar, der Details zu den durchgeführten Aktionen enthält.
   * Die vom Auftrag vorgenommenen Inhaltsaktualisierungen sind zerstörungsfrei. Das bedeutet, dass sie an einer Vorschauinstanz vorgenommen werden.
   * Der Kommentar enthält Links zu den Aktualisierungen, sodass Sie die Jira nach Bedarf überprüfen und veröffentlichen oder sie dem Verantwortlichen zuweisen können.

* Die folgende Abbildung zeigt eine Beispiel-Jira, die den `process`Befehl für den Auftrag zur Inhaltsaktualisierung Trigger:

  ![Beispiel Jira unter Verwendung des Auftrags zur Inhaltsaktualisierung von Brand Experience Agent](assets/content-update-jira-example.png)

## Weitere Verfeinerung beim Authoring {#further-refinement-in-authoring}

Nachdem Sie die Seite in AEM bearbeitet haben, wird sie in Ihrer Authoring-Umgebung geöffnet (z. B. im [universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) oder [Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md)).

Im [universellen Editor](#universal-editor-edit-text-with-the-assistant) ist der KI-Assistent *kontextbezogen*: Sie können Elemente auf der Arbeitsfläche auswählen und mit dem Assistenten daran arbeiten.

### Universeller Editor - Bearbeiten von Text mit dem Assistenten {#universal-editor-edit-text-with-the-assistant}

So verfeinern Sie die Kopie aus dem Assistenten beim Authoring:

1. Wählen Sie das Element im [universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) aus.
1. Öffnen Sie den KI-Assistenten oben rechts, geben Sie Ihre Eingabeaufforderung ein und senden Sie sie.

Beispiel-Eingabeaufforderungen:

* `Update to Explore the World of Coffee`
* `Update to be more engaging for the 30-40 year old age demographic and avid coffee drinker`

Wählen Sie **Änderungen anwenden** (oder eine entsprechende Option) aus, damit Aktualisierungen auf der Seite angezeigt werden.

## Aktivierung {#activation}

Sie können AEM-Agenten über den [Playground](https://www.aem.live/developer/aem-playground) erkunden oder sich mit Ihrem CSM oder TAM verbinden, um den Zugriff über die Agent SKU zu besprechen.

## Zusätzliche Ressourcen {#additional-resources}

Die folgenden Ressourcen können bei der weiteren Untersuchung des Experience Production Agent nützlich sein:

* Sie können auch die [Experience Production Agent Workbook](https://www.adobe.com/go/aem-epa-workbook_de) für angeleitete, praktische Anweisungen verwenden.
