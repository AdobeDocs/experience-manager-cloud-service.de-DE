---
title: Auftrag zur Inhaltsaktualisierung
description: Erfahren Sie, was der Inhaltsaktualisierungsauftrag des Brand Experience Agents ist und was er für Sie tun kann.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: 71e3770a7a26b8d3144717513f3ec1c997b3b435
workflow-type: tm+mt
source-wordcount: '854'
ht-degree: 2%

---


# Auftrag zur Inhaltsaktualisierung {#content-update}

Der Auftrag zum Aktualisieren von Inhalten des [Brand Experience Agent](/help/ai-in-aem/agents/brand-experience/overview.md) automatisiert die Inhaltserstellung, um alltägliche Aufgaben für Adobe Experience Manager (AEM) as a Cloud Service und Edge Delivery Services zu beschleunigen.

## Übersicht {#overview}

Der Auftrag zur Inhaltsaktualisierung aktualisiert vorhandene Inhalte, einschließlich Inhaltsfragmenten, Seiten, Formularen und Assets. Der Auftrag kann Aktionen durchführen, wie z. B. Aktualisieren, Entfernen, Ersetzen oder Hinzufügen von Inhaltselementen, um Erlebnisse genau und aktuell zu halten. Eingaben können Beschreibungen in natürlicher Sprache sein und bei Verwendung mit Jira-PDFs und Screenshots auch Eingaben liefern.

Der Auftrag zur Inhaltsaktualisierung wandelt die von Ihnen bereitgestellten Details entweder durch natürliche Sprache oder visuelle Elemente in Inhaltsaktualisierungen auf Ihrer Seite um. Sie geben die URL einer Seite an, die aktualisiert werden muss, zusammen mit Details dazu, was aktualisiert werden muss, und die Agentenkompetenz erledigt Ihre Aufgabe.

## Funktionen {#capabilities}

Sie können auf die Fähigkeit zur Inhaltsaktualisierung zugreifen unter:

* [Der KI-Assistent](#ai-assistant)
* [Jira](#jira)

## KI-Assistent {#ai-assistant}

Sie können über den KI-Assistenten auf den Auftrag in AEM zugreifen.

Öffnen Sie den KI-Assistenten von [`experience.adobe.com` aus ](https://experience.adobe.com) beginnen Sie dann mit der Interaktion, indem Sie Ihre Eingabeaufforderung in natürlicher Sprache mithilfe des Felds `Ask AI Assistant anything` angeben:

![Auftrag zur Inhaltsaktualisierung](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-ai-assistant-example.png)

### Eingabeaufforderungen {#sample-prompts}

Um Inhaltsaktualisierungen zu initiieren, können Sie eine Vielzahl von Eingabeaufforderungen in natürlicher Sprache eingeben. Außerdem müssen Sie die öffentlich zugängliche URL der Seite angeben, die Sie aktualisieren möchten. Beispiel:

* Ändern Sie die folgende Seite `https://www.your-url.com/sale` Aktualisieren Sie die Überschrift des Hauptheld auf „Black Friday Mega Sale - Bis zu 70% Rabatt“, ändern Sie den Countdown-Timer, um „Endet in 48 Hours“ anzuzeigen, entfernen Sie „Für Updates anmelden“, ändern Sie alle „Jetzt einkaufen“-Schaltflächen auf „Den Deal packen“

* `https://www.your-url.com/laptops/your-laptop-model` Aktualisieren der Bannerkopie auf „Nur heute 300 USD sparen“, Aktualisieren der Preise von 1.299 USD auf 999 USD, Entfernen der Finanzierungsoption Banner

* `https://www.your-url.com/your-sneaker` den Lagerstatus von „Geringer Lagerbestand“ auf „Zurück auf Lager - Begrenzte Mengen“ zu aktualisieren, ändern Sie die Größenauswahl, um die verfügbaren Größen in grün zu markieren, Entfernen Sie das Abzeichen „In Kürze verfügbar“

* `https://www.your-url.com/your-sneaker` Aktualisieren Sie die Produktbilder, um neue Farbverläufe anzuzeigen

>[!NOTE]
>
>Datei-Uploads können bei der Interaktion mit [Jira](#jira) verwendet werden, werden jedoch nicht mit dem KI-Assistenten unterstützt.

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

Um den Auftrag zu verwenden, fügen Sie Ihrem Ticket einen Kommentar hinzu. Geben Sie im Kommentar den Auftrag mit dem Symbol &quot;`@`&quot; zusammen mit dem Befehl an, der ausgeführt werden soll. Beispiel:

* `@aemagent@adobe.com process`

Derzeit versteht der Auftrag die Befehle:

* `process` - Anfrage verarbeiten
* `cancel` - Abbrechen der Verarbeitung einer Anfrage
* `retry` - Anfrage erneut verarbeiten
* `feedback` - Wenden Sie Feedback auf eine frühere Generation an
* `reprocess` - Ursprüngliche Anfrage erneut verarbeiten

### Interaktion des Auftrags {#how-the-agent-interacts}

Nachdem Sie einen Befehl für den Auftrag ausgegeben haben, antwortet er mit Kommentaren in der Jira. In den Kommentaren werden der Fortschritt des Vorgangs und die ergriffenen Maßnahmen beschrieben.

Wenn ein `process` Befehl an den Trigger aktualisiert wird, können die Antworten der folgenden Sequenz folgen:

* Der erste Kommentar bestätigt, dass der Vorgang gestartet wurde.

* Nach Abschluss der Aufgabe antwortet der Auftrag mit einem weiteren Kommentar, der Details zu den durchgeführten Aktionen enthält.
   * Die vom Auftrag vorgenommenen Inhaltsaktualisierungen sind zerstörungsfrei. Das bedeutet, dass sie an einer Vorschauinstanz vorgenommen werden.
   * Der Kommentar enthält Links zu den Aktualisierungen, sodass Sie die Jira nach Bedarf überprüfen und veröffentlichen oder sie dem Verantwortlichen zuweisen können.

* Die folgende Abbildung zeigt eine Beispiel-Jira, die den `process`Befehl für den Auftrag zur Inhaltsaktualisierung Trigger:

  ![Beispiel Jira unter Verwendung des Auftrags zur Inhaltsaktualisierung des Experience Production Agents](assets/content-update-jira-example.png)

## Aktivierung {#activation}

Um den Kommunikationserstellungsauftrag zu aktivieren und Zugriff darauf zu erhalten, müssen Sie sich an Adobe wenden. Zu Beginn haben Sie folgende Möglichkeiten:

* `experience-production-agent@adobe.com`
* Oder wenden Sie sich an Ihr Account-Team

Um den Prozess zu beschleunigen, hilft es, die folgenden Informationen bereitzustellen:

* Für AEM as a Cloud Service müssen Sie Folgendes angeben:
   * Unternehmens-ID
   * `product_id`
   * `profile_id`

   * Diese Werte finden Sie in den folgenden Schritten:
      1. Ihr Administrator muss [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) besuchen
      1. **Adobe Experience Manager as a Cloud Service**
      1. Auswählen der entsprechenden AEM-Instanz
      1. Wählen Sie das Profil aus, das Lese- und Schreibvorgänge für den betreffenden Inhalt zulässt
      1. Browser-URL erfassen
      1. Extrahieren Sie `product_id` und `profile_id` aus der URL.
Zum Beispiel: `https://adminconsole.adobe.com/products/profiles/users`

* Edge Delivery-Dokumenterstellung
   * Geben Sie Ihrem Adobe-Team die folgenden Informationen:
      * Relevante Domains
      * Relevante GitHub-Informationen:
         * Org
         * Repo
         * Verzweigung

## Einschränkungen {#limitations}

Beachten Sie die folgenden Einschränkungen:

* Datei-Uploads können bei der Interaktion mit [Jira](#jira) verwendet werden, werden aber bei der Interaktion mit dem [AI-Assistenten nicht unterstützt](#ai-assistant)
