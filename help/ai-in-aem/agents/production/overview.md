---
title: Übersicht über Experience Production Agent
description: Erfahren Sie, wie Sie mit dem Experience Production Agent in AEM die Inhaltserstellung beschleunigen und Änderungen automatisch koordinieren können.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 8cd524891df550913a734a9355c1012dc11adf5b
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 3%

---


# Übersicht über Experience Production Agent {#experience-production-agent}

Der Experience Production Agent automatisiert Aufgaben mit hohem Aufwand und hohem Volumen. Die Stärkung von Teams und die Umwandlung manueller, wochenlanger Prozesse in schnelle, KI-gestützte Workflows, die jedes Erlebnis aktuell und konsistent halten und dem Unternehmen helfen, seine Ziele zu erreichen.

## Aufträge {#jobs}

Der Agent bietet die folgenden Aufträge:

* [Inhaltsaktualisierung](#content-update)
* [Formularerstellung](#form-creation)
* [Erstellung von Kommunikationen](#communications-creation)
* [Site-Migration](#site-migration)

>[!IMPORTANT]
>
>KI-generierte Antworten können ungenau oder irreführend sein. Überprüfen Sie unbedingt die vorgeschlagenen Fehlerbehebungen und Antworten.
>
>Siehe auch [Benutzerhandbücher für die generative KI von Adobe Experience Cloud](https://www.adobe.com/legal/licenses-terms/adobe-dx-gen-ai-user-guidelines.html).

### Inhaltsaktualisierung {#content-update}

Mit [Inhaltsaktualisierung](/help/ai-in-aem/agents/production/content-update.md) werden vorhandene Inhalte in der gesamten CMS, einschließlich Inhaltsfragmenten, Seiten, Formularen und Assets, problemlos aktualisiert. Der Agent kann Aktionen wie das Aktualisieren, Entfernen, Ersetzen oder Hinzufügen von Inhaltselementen durchführen, um Erlebnisse genau und aktuell zu halten. Eingaben können Beschreibungen in natürlicher Sprache sein und bei Verwendung mit Jira-PDFs und Screenshots auch Eingaben liefern.

### Formularerstellung {#form-creation}

Die [Formularerstellung](/help/ai-in-aem/agents/production/form-creation.md) ermöglicht es Benutzern, adaptive Formulare über Eingabeaufforderungen in natürlicher Sprache zu erstellen, ohne von Entwicklungs- oder IT-Teams abhängig zu sein. Diese Funktion beschleunigt die Formularentwicklung, während die Markenkonsistenz gewahrt bleibt und es Geschäftsbenutzern ermöglicht wird, Formulare ohne fundierte technische Produktkenntnisse zu erstellen.

### Kommunikationserstellung {#communications-creation}

Die [Communication Creation](/help/ai-in-aem/agents/production/communications-creation.md)-Fähigkeit ermöglicht es Geschäftsbenutzern, personalisierte, datengesteuerte Korrespondenz im benötigten Umfang zu erstellen. Von Kontoauszügen und Richtliniendokumenten bis hin zu Rechnungen und Willkommenspaketen wandelt der Agent Anforderungen an die natürliche Sprache in professionelle Kommunikation um.

>[!NOTE]
>
> Die Fähigkeit zur Kommunikationserstellung befindet sich derzeit in der Alpha-Phase. Wenn Sie teilnehmen möchten, senden Sie bitte eine Anfrage von Ihrer offiziellen E-Mail-Adresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com).

### Site-Migration {#site-migration}

Die [Site-Migration](/help/ai-in-aem/agents/production/site-migration.md) migriert nahtlos Sites, die nicht von AEM stammen, in AEM-Umgebungen (Experience Delivery Services), um sicherzustellen, dass sie leistungsfähig, konform und agentenbereit sind. Der Agent optimiert die Einrichtung und Umwandlung, wodurch der manuelle Aufwand und die Wertschöpfungszeit reduziert werden.

Der Agent sollte in der Lage sein, mit anderen Agentenfähigkeiten zu arbeiten, Beispiele sind:

## Verwendung mit anderen Wirkstoffen {#use-with-other-agents}

* Abrufen von Quell-Assets vom Experience Advisory Agent

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
