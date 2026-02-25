---
title: Auftrag zur Inhaltsaktualisierung
description: Erfahren Sie, was der Inhaltsaktualisierungsauftrag des Brand Experience Agents ist und was er für Sie tun kann.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: e2d1dae8-38de-4357-bb14-ad35acb71aee
source-git-commit: 36f4ba8207da67b8e68c9c9851311defc909b495
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 2%

---


# Auftrag zur Inhaltsaktualisierung {#content-update}

Der Auftrag zum Aktualisieren von Inhalten des [Brand Experience Agent](/help/ai-in-aem/agents/brand-experience/overview.md) automatisiert die Inhaltserstellung, um alltägliche Aufgaben für Adobe Experience Manager (AEM) as a Cloud Service und Edge Delivery Services zu beschleunigen.

## Übersicht {#overview}

Der Auftrag zur Inhaltsaktualisierung aktualisiert vorhandene Inhalte, einschließlich Inhaltsfragmenten, Seiten, Formularen und Assets. Der Auftrag kann Aktionen durchführen, wie z. B. Aktualisieren, Entfernen, Ersetzen oder Hinzufügen von Inhaltselementen, um Erlebnisse genau und aktuell zu halten. Eingaben können Beschreibungen in natürlicher Sprache sein und bei Verwendung mit Jira-PDFs und Screenshots auch Eingaben liefern.

Der Auftrag zur Inhaltsaktualisierung wandelt die von Ihnen bereitgestellten Details entweder durch natürliche Sprache oder visuelle Elemente in Inhaltsaktualisierungen auf Ihrer Seite um. Sie geben die URL einer Seite an, die aktualisiert werden muss, zusammen mit Details dazu, was aktualisiert werden muss, und die Agentenkompetenz erledigt Ihre Aufgabe. Bei Verwendung mit Adobe Experience Manager (AEM) as a Cloud Service erstellt der Auftrag einen neuen [Launch](/help/sites-cloud/authoring/launches/overview.md), damit Sie die Aktualisierungen vor der Anwendung überprüfen können. Bei Verwendung mit der Dokumenterstellung erstellt der Auftrag eine neue [Version](https://experienceleague.adobe.com/en/docs/experience-manager-learn/sites/document-authoring/how-to/document-versions#).

## Funktionen {#capabilities}

Sie können auf die Fähigkeit zur Inhaltsaktualisierung zugreifen unter:

* [Der KI-Assistent](#ai-assistant)
* [Jira](#jira)

## KI-Assistent {#ai-assistant}

Sie können über den KI-Assistenten auf den Auftrag in AEM zugreifen.

Öffnen Sie den KI-Assistenten von [`experience.adobe.com` aus &#x200B;](https://experience.adobe.com) beginnen Sie dann mit der Interaktion, indem Sie Ihre Eingabeaufforderung in natürlicher Sprache mithilfe des Felds `Ask AI Assistant anything` angeben:

![Auftrag zur Inhaltsaktualisierung](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-ai-assistant-example.png)

### Konfigurieren der Veröffentlichungs-URL {#configuring-the-publish-url}

Um eine Publishing-URL (öffentlich zugängliche URL) zu verwenden, muss eine einmalige Konfiguration vorgenommen werden:

* Voraussetzungen:

   * Um die Konfiguration vorzunehmen, muss der Benutzer über Systemadministrator- oder Produktadministratorrechte verfügen.

* Konfiguration:

   1. Rufen Sie die Fähigkeit zur Inhaltsaktualisierung auf, indem Sie eine Inhaltsaktualisierung für die URL anfordern.
   1. Der Assistent führt Sie durch die Konfiguration und stellt Ihnen eine Reihe von Fragen.
   1. Nach Abschluss des Vorgangs ist die Veröffentlichungs-URL konfiguriert und kann verwendet werden.

Zum Beispiel:

![Kenntnisse zum Aktualisieren von Inhalten - Veröffentlichungs-URL konfigurieren](/help/ai-in-aem/agents/brand-experience/experience-production/assets/content-update-publish-url-configuration.png)

### Eingabeaufforderungen {#prompts}

Um Inhaltsaktualisierungen zu initiieren, können Sie eine Vielzahl von Eingabeaufforderungen in natürlicher Sprache eingeben. Sie müssen die URL der öffentlichen Seite (Veröffentlichungs-) oder die URL der Autorenumgebung der Seite angeben, die Sie aktualisieren möchten. Einige, aber nicht alle der unterstützten Verben; ersetzen, aktualisieren, entfernen, ändern, überarbeiten, ändern, anpassen, löschen.

>[!NOTE]
>
>Datei-Uploads können bei der Interaktion mit [Jira](#jira) verwendet werden, werden jedoch nicht mit dem KI-Assistenten unterstützt.

### Eingabeaufforderungen {#sample-prompts}

Zu den Beispielaufforderungen gehören:

* auf `<your-publish-URL>` Update „Dein perfekter Kaffee ist noch vier Fragen entfernt!“ zu „Dein Kaffee, dein Weg!“
* Ersetzen `<your-author-env-URL>` das Bild von „holdingcup.png“ durch „stairhead.png“
* auf `<your-publish-URL>` Schaltfläche „Take our Coffee Quiz“ in eine ansprechendere Version ändern“
* entfernt `<your-author-env-URL>` den Abschnitt „Nicht beanspruchte Belohnungen sind ein verpasstes Geschenk!“

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

Zum Beispiel:

* `@aemagent@adobe.com process this ticket`

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

Sie können AEM-Agenten über den [Playground](https://www.aem.live/developer/aem-playground) erkunden oder sich mit Ihrem CSM oder TAM verbinden, um den Zugriff über die Agent SKU zu besprechen.

## Einschränkungen {#limitations}

Beachten Sie die folgenden Einschränkungen:

* Datei-Uploads können bei der Interaktion mit [Jira](#jira) verwendet werden, werden aber bei der Interaktion mit dem [AI-Assistenten nicht unterstützt](#ai-assistant)
