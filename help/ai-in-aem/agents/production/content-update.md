---
title: Kenntnisse zum Aktualisieren von Inhalten
description: Erfahren Sie, was die Inhaltsaktualisierungsfähigkeiten des Experience Production Agents sind und was sie für Sie tun können.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 437da39f61d7af2fe01a1617d3299fd60ee38ad5
workflow-type: tm+mt
source-wordcount: '858'
ht-degree: 1%

---


# Kenntnisse zum Aktualisieren von Inhalten {#content-update}

Die Fähigkeit zum Aktualisieren von Inhalten des Experience Production Agents automatisiert die Inhaltserstellung, um alltägliche Aufgaben für Adobe Experience Manager (AEM) as a Cloud Service und Edge Delivery Services zu beschleunigen.

Die Fähigkeit zur Inhaltsaktualisierung aktualisiert vorhandene Inhalte, einschließlich Inhaltsfragmenten, Seiten, Formularen und Assets. Der Agent kann Aktionen wie das Aktualisieren, Entfernen, Ersetzen oder Hinzufügen von Inhaltselementen durchführen, um Erlebnisse genau und aktuell zu halten. Eingaben können Beschreibungen in natürlicher Sprache sein und bei Verwendung mit Jira-PDFs und Screenshots auch Eingaben liefern.

## Überblick {#overview}

Die Fähigkeit zur Inhaltsaktualisierung wandelt die Details, die Sie entweder über natürliche Sprache oder visuelle Inhalte bereitstellen, in Inhaltsaktualisierungen auf Ihrer Seite um. Sie geben die URL einer Seite an, die aktualisiert werden muss, zusammen mit Details dazu, was aktualisiert werden muss, und die Agentenkompetenz erledigt Ihre Aufgabe.

## Funktionen {#capabilities}

Sie können auf die Fähigkeit zur Inhaltsaktualisierung zugreifen unter:

* [KI-Assistent](#ai-assistant)

* [Jira](#jira)

## KI-Assistent {#ai-assistant}

Sie können über den KI-Assistenten auf die Agenten in AEM zugreifen.

Öffnen Sie den KI-Assistenten unter experience.adobe.com und beginnen Sie dann mit der Interaktion, indem Sie Ihre Eingabeaufforderung in natürlicher Sprache mithilfe des Felds `Ask AI Assistant anything` angeben:

![Zugriff auf Discovery Agent](/help/ai-in-aem/agents/production/assets/content-update-ai-assistant-example.png)

### Eingabeaufforderungen {#sample-prompts}

Um Inhaltsaktualisierungen zu initiieren, können Sie eine Vielzahl von Eingabeaufforderungen in natürlicher Sprache eingeben. Außerdem müssen Sie die öffentlich zugängliche URL der Seite angeben, die Sie aktualisieren möchten. Beispiel:

* Ändern Sie die folgende Seite https://www.your-url.com/sale Aktualisieren Sie die Haupthelden-Überschrift auf „Black Friday Mega Sale - Bis zu 70% Rabatt“, ändern Sie den Countdown-Timer, um „Endet in 48 Hours“ anzuzeigen, entfernen Sie „Für Updates anmelden“, ändern Sie alle „Shop Now“-Schaltflächen auf „Grab the Deal“

* https://www.your-url.com/laptops/your-laptop-model Aktualisieren Sie die Bannerkopie auf „Save 300 USD Today Only“, Aktualisieren Sie die Preise von 1.299 USD auf 999 USD, Entfernen Sie das Finanzierungsoptionenbanner

* https://www.your-url.com/your-sneaker Aktualisieren Sie den Lagerstatus von „Geringer Lagerbestand“ auf „Zurück auf Lager - Begrenzte Mengen“, ändern Sie die Größenauswahl, um die verfügbaren Größen in grün hervorzuheben, Entfernen Sie das Abzeichen „In Kürze verfügbar“

* https://www.your-url.com/your-sneaker Aktualisieren Sie die Produktbilder, um neue Farbverläufe zu zeigen

>[!NOTE]
>
>Datei-Uploads können bei der Interaktion mit [Jira](#jira) verwendet werden, werden jedoch nicht mit dem KI-Assistenten unterstützt.

## Jira {#jira}

Wenn Sie die Fähigkeit zur Inhaltsaktualisierung mit Jira verwenden, können Sie ein Ticket mit Anweisungen erstellen, die Ihre Änderungen automatisieren.

### Erstellen eines Tickets {#create-a-ticket}

Erstellen Sie ein Jira-Ticket (beliebiger Typ).

Im Feld „Beschreibung **Ihres Tickets** Sie zwei wichtige Details:

1. Die öffentlich zugängliche URL der Seite, die Sie bearbeiten müssen.

1. Die erforderlichen Änderungen.

   Derzeit unterstützt die Kenntnisse die folgenden Formate, um Ihre Änderungen zu beschreiben:

   * Natürliche Sprache in der Ticketbeschreibung
      * Beispiel: „Ändern der Überschrift von X in Y“
   * PDF mit Anmerkungen
      * Erstellen Sie beispielsweise eine PDF Ihrer Seite und fügen Sie Anmerkungen hinzu, die detailliert beschreiben, was Sie ändern möchten
   * Kommentare in angehängter PDF
      * Erstellen Sie beispielsweise eine PDF Ihrer Seite und fügen Sie Kommentare hinzu, die detailliert beschreiben, was Sie ändern möchten
   * Angehängter Screenshot
      * Beispiel: Erstellen Sie einen Screenshot eines Teils Ihrer Seite und fügen Sie Anmerkungen hinzu, die detailliert beschreiben, was Sie ändern möchten
   * Angehängte Microsoft Word-Datei mit natürlichen Sprachänderungen

### Agent von Ihrem Ticket aus aufrufen {#invoke-the-agent-from-your-ticket}

Um den Agenten zu verwenden, fügen Sie Ihrem Ticket einen Kommentar hinzu. Geben Sie im Kommentar den Agenten mit dem Symbol `@` zusammen mit dem Befehl an, den er ausführen soll. Beispiel:

* `@aemagent@adobe.com process`

Derzeit versteht der Agent die Befehle:

* `process` - Anfrage verarbeiten
* `cancel` - Abbrechen der Verarbeitung einer Anfrage
* `retry` - Anfrage erneut verarbeiten
* `feedback` - Wenden Sie Feedback auf eine frühere Generation an
* `reprocess` - Ursprüngliche Anfrage erneut verarbeiten

### Interaktion des Agenten {#how-the-agent-interacts}

Nachdem Sie einen -Befehl an den Agenten ausgegeben haben, antwortet er mit Kommentaren in der Jira. In den Kommentaren werden der Fortschritt des Agenten und die ergriffenen Maßnahmen beschrieben.

Wenn ein `process` Befehl an den Trigger aktualisiert wird, können die Antworten der folgenden Sequenz folgen:

* Der erste Kommentar bestätigt, dass der Agent gestartet wurde.

* Sobald die Aufgabe abgeschlossen ist. Der Agent antwortet mit einem weiteren Kommentar, der Details zu den durchgeführten Aktionen enthält.
   * Die vom Agenten vorgenommenen Inhaltsaktualisierungen sind zerstörungsfrei. Das bedeutet, dass sie an einer Vorschauinstanz vorgenommen werden.
   * Der Kommentar enthält Links zu den Aktualisierungen, sodass Sie die Jira nach Bedarf überprüfen und veröffentlichen oder sie dem Verantwortlichen zuweisen können.

* Die folgende Abbildung zeigt ein Beispiel-Jira, das den `process`Befehl für die Fähigkeit zur Inhaltsaktualisierung“ Trigger:

  ![Beispiel Jira unter Verwendung der Inhaltsaktualisierungsfähigkeiten des Experience Production Agents](assets/content-update-jira-example.png)

## Aktivierung {#activation}

Um den Experience Production Agent zu aktivieren und Zugriff auf ihn zu erhalten, müssen Sie sich an Adobe wenden. Für die ersten Schritte wenden Sie sich an:

* `experience-production-agent@adobe.com`
* oder wenden Sie sich an Ihr Account-Team

Um den Prozess zu beschleunigen, hilft es, die folgenden Informationen bereitzustellen:

* Für AEM as a Cloud Service
   * Sie müssen Folgendes angeben:
      * Unternehmens-ID
      * `product_id`
      * `profile_id`

   * Diese Werte können mithilfe der folgenden Schritte gefunden werden:
      * Ihr Administrator muss <https://adminconsole.adobe.com/> besuchen
      * **Adobe Experience Manager as a Cloud Service**
      * Auswählen der entsprechenden AEM-Instanz
      * Wählen Sie das Profil aus, das Lese- und Schreibvorgänge für den betreffenden Inhalt zulässt
      * Browser-URL erfassen
      * Extrahieren Sie `product_id` und `profile_id` aus der URL.
Zum Beispiel: <https://adminconsole.adobe.com/products/profiles/users>

* Edge Delivery-Dokumenterstellung
   * Geben Sie Ihrem Adobe-Team die folgenden Informationen:
      * Relevante Domains
      * Relevante GitHub-Informationen:
         * Org
         * Repo
         * Verzweigung

## Einschränkungen {#limitations}

Derzeit gelten folgende Einschränkungen für Content Updater:

* Datei-Uploads können bei der Interaktion mit [Jira](#jira) verwendet werden, werden aber bei der Interaktion mit dem [AI-Assistenten](#ai-assistant) nicht unterstützt.
