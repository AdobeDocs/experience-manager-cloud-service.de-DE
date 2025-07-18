---
title: KI-Assistent in Adobe Experience Manager (private Betaversion)
description: Verwenden Sie den KI-Assistenten in Adobe Experience Manager, um Antworten zu finden, Fehler zu beheben und Sites, Assets, Dynamic Media, Cloud Manager und Forms zu erkunden.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: false
hidefromtoc: true
exl-id: 6cdf7f65-7112-420a-90c1-564f0ef8ceaf
source-git-commit: 0afd74120380c9ae3d02db9fb684189c2f19648f
workflow-type: tm+mt
source-wordcount: '1394'
ht-degree: 1%

---

# Über AEM AI Assistant in Adobe Experience Manager {#aem-home}

Der KI-Assistent in AEM (Adobe Experience Manager) bietet eine Gesprächsoberfläche, die darauf ausgelegt ist, die Suche nach Antworten auf Ihre Adobe Experience Manager-bezogenen Abfragen zu optimieren. Es hilft Ihnen, auf Produktwissen zuzugreifen, Probleme zu beheben und die in Experience League verfügbaren Informationen zu erkunden. Während des privaten Beta-Programms unterstützt der AEM AI Assistant Adobe Experience Manager as a Cloud Service, einschließlich Sites, Assets, Dynamic Media, Cloud Manager und Forms.

>[!IMPORTANT]
>Sie müssen die Benutzervereinbarung gelesen und eingereicht haben, damit Adobe die Funktion des KI-Assistenten aktivieren kann, damit Sie sie testen und am privaten Beta-Programm teilnehmen können.
>
>Bei Fragen senden Sie eine E-Mail an [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com) von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse.

## Datenschutz, Sicherheit und Governance

Der AEM AI-Assistent wurde mit einem Schwerpunkt auf Datenschutz, Sicherheit und Governance entwickelt.

In diesem Artikel werden die Funktionen beschrieben, die Sie vom AEM AI-Assistenten erwarten können, um Vertrauen zu schaffen:

* AEM AI Assistant verwendet keine personenbezogenen Daten, auch nicht für Schulungszwecke.
* AEM AI Assistant hat keinen Zugriff auf Verbraucherdaten.
* Für die Interaktion mit dem AEM-KI-Assistenten ist eine explizite Berechtigung erforderlich.
* Von Benutzenden bereitgestellte Eingabeaufforderungen (Fragen, Abfragen usw.) werden nicht für andere Kundinnen und Kunden freigegeben.

<!-- See also [Security at Adobe whitepaper](). NEED ACTIVE LINK FROM ADRIAN NICOLAE TANASE. CURRENTLY 404. -->


## Lernen Sie den AEM AI Assistant für Produktkenntnisse kennen. {#ai-prod-insights}

Das Produktwissen umfasst Konzepte und Themen, die aus der Dokumentation zu Adobe Experience League abgeleitet wurden. Diese Fragen lassen sich in die folgenden Untergruppen einteilen:

| Produktkenntnisse | Beispiele |
| --- | --- |
| Punktuelles Lernen | <ul><li>Was ist der universelle Editor?</li><li>Wie erstelle ich ein Programm in Cloud Manager?</li></ul> |
| Erkennung öffnen | <ul><li>Wie verwende ich den universellen Editor?</li><li>Gibt es eine Möglichkeit, Inhalte von einer Umgebung in eine andere zu kopieren?</li></ul> |
| Fehlerbehebung | <ul><li>Warum kann ich nicht auf den universellen Editor zugreifen?</li><li>Warum schlägt meine Pipeline fehl?</li></ul> |

Der aktuelle Umfang des AEM AI Assistant konzentriert sich auf die Beantwortung von Fragen zum Produktwissen von Adobe Experience Manager as a Cloud Service. Dieser Umfang umfasst umfassende Unterstützung für wichtige Bereiche wie Sites, Assets, Forms und Cloud Manager.

## Wie man effektive Fragen formuliert {#ai-craft-questions}

Um vom AEM AI-Assistenten die genauesten Antworten zu erhalten, ist es wichtig, Ihre Fragen klar und kontextbezogen zu formulieren. Verwenden Sie die folgenden Tipps, um sicherzustellen, dass Ihre Abfragen klar und gut strukturiert sind:

* Geben Sie Ihre Aufgabe oder Frage klar und prägnant an.
* Vermeiden Sie mehrdeutige Formulierungen oder eine übermäßig komplexe Syntax, um das Verständnis zu verbessern.
* Binden Sie relevanten Kontext zu Ihrer Aufgabe oder Frage ein, da dieser Ansatz dem AEM AI-Assistenten hilft, präzisere und relevantere Antworten bereitzustellen.
In Ihrer Eingabeaufforderung ist es beispielsweise hilfreich, die AEM-Lösung zu benennen, in der Sie arbeiten - Sites, Assets, Dynamic Media, Cloud Manager und Forms.

### Beispiele für nicht unterstützte Fragen {#ai-unsupported-questions}

| Flächendiagramm | Beispiele |
| --- | --- |
| Operative Erkenntnisse | <ul><li>Wie viele Entwicklungsumgebungen gibt es in meinem Mandanten?</li><li>Wer hat die letzte Produktions-Pipeline gestartet?</li></ul> |
| Fehlerbehebung | <ul><li>Warum schlägt meine Produktions-Pipeline fehl?</li></ul> |
| Aufgaben und Automatisierung | <ul><li>Konfigurieren Sie eine Code-Qualitäts-Pipeline aus einer Entwicklungsverzweigung für mich.</li></ul> |


## Verwenden des AEM AI-Assistenten {#ai-use}

### Aktivieren des Zugriffs auf den AEM AI-Assistenten über Admin Console

Um den AEM-KI-Assistenten verwenden zu können, muss sich Ihr Unternehmen auf Admin Console-Ebene anmelden. Ein Produktadministrator erstellt (oder wählt) eine Benutzergruppe und gewährt ihr die neue Berechtigung „KI-Assistent“. Jeder, der dieser Gruppe hinzugefügt wird, erhält sofort Zugriff auf den Assistenten in AEM. Wenn das Ziel die unternehmensweite Verfügbarkeit ist, weist der Administrator einfach alle Benutzer dieser Gruppe zu.

![AEM-KI-Assistent in der Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console.png)

Aus Mitarbeitersicht ist der Prozess einfach: Bestimmen Sie den Produktadministrator für Adobe Experience Manager in Ihrem Unternehmen und fordern Sie die Hinzufügung zur KI-aktivierten Benutzergruppe an. Sobald Sie in dieser Gruppe angezeigt werden, wird das Assistentensymbol automatisch angezeigt, wenn Sie sich das nächste Mal anmelden.

Administratoren sollten die normale Cloud Manager-Governance im Auge behalten. Sie müssen über Produktadministratorrechte in der Admin Console verfügen, um Profile zu erstellen, Benutzergruppen zu verwalten oder Berechtigungen zu bearbeiten. Wenn Benutzende auch die integrierte Funktion „Support-Ticket erstellen **des Assistenten benötigen** fügen Sie die standardmäßige Rolle **Support-Admin** (standardmäßige Admin Console-Rolle) denselben Personen oder derselben Gruppe hinzu.

![Erstellung von Tickets für den technischen Support im AEM AI Assistant der Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-admin-console-support-ticket.png)

Eine Anleitung zum Einrichten von Benutzenden und Gruppen in AEM as a Cloud Service finden Sie unter [Zugriff auf AEM as a Cloud Service konfigurieren](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/accessing/overview).

Siehe auch [Benutzerdefinierte Berechtigungen](/help/implementing/cloud-manager/custom-permissions.md).


### Starten oder Zurücksetzen einer Konversation

Sie können den AEM-KI-Assistenten zurücksetzen und eine neue Unterhaltung beginnen, wenn Sie Themen ändern möchten. Diese Funktion ist besonders hilfreich bei der Fehlerbehebung bei Abfragen, die fehlschlagen oder falsche Informationen liefern.

![Schaltfläche „Unterhaltung beginnen“](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**So starten oder setzen Sie eine Konversation zurück:**

1. Klicken Sie im KI-Assistenten von AEM auf ![Symbol Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Um den AEM AI-Assistenten über ein neues Thema oder eine Themenänderung zu informieren, klicken Sie auf **Neue Konversation starten**.

### Entdeckbarkeit verwenden

Der AEM-KI-Assistent enthält eine Entdeckungsfunktion, mit der Sie die unterstützten Themen und Kategorien erkunden können.

![IDEA Glühbirnensymbol](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**So verwenden Sie Entdeckbarkeit:**

1. Klicken Sie oben rechts im AEM-KI-Assistenten auf ![Lernsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).
1. Wählen Sie eine Kategorie aus, um eine Liste der zugehörigen Eingabeaufforderungen anzuzeigen.
1. Wählen Sie eine Eingabeaufforderung aus, um die Arten von Fragen besser zu verstehen, die der AEM-KI-Assistent beantworten kann.

### Feedback zum AEM AI-Assistenten geben

Ihre Eingabe trägt dazu bei, den AEM AI-Assistenten zu verbessern, um eine bessere Leistung und Genauigkeit zu erzielen.

Geben Sie mit dem AEM AI Assistant Feedback zu Ihren Erfahrungen. Verwenden Sie dazu die folgenden Optionen:

![Symbole „Daumen hoch“, „Daumen runter“ und „Markierung“](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| Symbol | Beschreibung |
| --- | --- |
| ![Miniaturansicht nach oben](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Klicken Sie hier, um anzugeben, was gut gelaufen ist, und um positives Feedback zu geben. |
| ![Miniaturansicht nach unten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Klicken Sie hier, um Verbesserungsvorschläge zu unterbreiten. Fügen Sie spezifische Kommentare zu Ihrem Erlebnis hinzu, die täglich überprüft werden. |
| ![Flag-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Klicken Sie hier, um Probleme zu melden oder detailliertes Feedback zu Ihrer Interaktion mit dem AEM AI-Assistenten zu geben. |

## Häufig gestellte Fragen zum AEM AI Assistant {#ai-faq}

Im Folgenden finden Sie Antworten auf einige häufig gestellte Fragen zum KI-Assistenten:

* **Werden die Informationen vom AEM AI Assistant in Echtzeit bereitgestellt?**\
  Nein. Der KI-Assistent bezieht seinen Inhalt aus der Adobe Experience League-Dokumentation. Es kann einige Zeit dauern, bis Aktualisierungen des Inhalts in den Antworten widergespiegelt werden.
* **Welche Adobe-Programme unterstützt AEM AI Assistant?**\
  Derzeit unterstützt der KI-Assistent Anfragen zu Produktkenntnissen in AEM as a Cloud Service, einschließlich Sites, Assets, Dynamic Media, Cloud Manager und Forms.
* **Welche Funktionen bietet der AEM AI Assistant?**\
  Der AEM AI-Assistent wurde entwickelt, um Fragen zu Adobe-Produktkenntnissen zu beantworten.
* **Verwendet AEM AI Assistant personenbezogene Daten für Schulungsdaten?**\
  Nein. AEM AI Assistant verwendet keine personenbezogenen Daten für Trainingszwecke. Vermeiden Sie es, persönliche Informationen über sich selbst oder andere, einschließlich Namen oder Kontaktdaten, mit dem AEM AI-Assistenten zu teilen.


## AEM Forms AI-Assistent (Forms Experience Builder) {#ai-forms-builder}

Zusätzlich zum allgemeinen AEM AI-Assistenten für Produktkenntnisse bietet AEM einen speziellen **[AEM Forms AI-Assistenten (Forms Experience Builder)](/help/edge/docs/forms/forms-ai-assistant.md)**. Dieser erweiterte Assistent kann Sie aktiv bei der Erstellung und Konfiguration von Formularen unterstützen, indem Sie in natürlicher Sprache Aufforderungen erhalten und formularspezifische Fragen beantworten.

### Schlüsselfunktionen

Der AEM Forms AI-Assistent bietet:

* **Formularerstellung**: Erstellen Sie neue Formulare von Grund auf mithilfe von Beschreibungen in natürlicher Sprache.
* **Design-Import**: Konvertieren Sie vorhandene Designs (PDF, Figma, Bilder) in funktionale AEM Forms.
* **Formularkonfiguration**: Felder, Bereiche, Validierungsregeln und bedingte Logik hinzufügen.
* **Layout-**: Organisieren der Formularstruktur und Optimierung für verschiedene Geräte.
* **Integrations-Setup**: Konfigurieren von Formularübermittlungen und Datenverarbeitung.
* **Produktkenntnisse**: Antworten auf Fragen zu den Funktionen und Best Practices von AEM Forms.

### Zugriffsbereich

Der AEM Forms AI-Assistent ist in den folgenden Dateien verfügbar:

* **Universeller Editor**: Für Edge Delivery Services-Formulare mit visuellen Bearbeitungsfunktionen.
* **Adaptiver Forms-Editor**: Für eine detaillierte Formularkonfiguration und erweiterte Funktionen.
* **Benutzeroberfläche für die Verwaltung von Forms**: Für allgemeine Aufgaben zur Formularerstellung und -verwaltung.

### Erste Schritte

>[!NOTE]
>
> Der AEM Forms AI-Assistent (Forms Experience Builder) ist im Rahmen des privaten Beta-Programms verfügbar. Senden Sie eine E-Mail von Ihrer Geschäftsadresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com), um den Zugriff anzufordern.

Weitere Informationen zur Verwendung des AEM Forms-KI-Assistenten finden Sie in der Dokumentation zum [AEM Forms-KI](/help/edge/docs/forms/forms-ai-assistant.md)Assistenten.

### Beispiel-Anwendungsfälle

* **„Erstellen Sie ein Formular für Kunden-Feedback mit den Feldern Name, E-Mail, Bewertung und Kommentare“**
* **„Konvertieren Sie dieses hochgeladene PDF-Anwendungsformular in ein digitales adaptives Formular“**
* **„Bedingte Logik hinzufügen, um Ehepartner-Informationen nur dann anzuzeigen, wenn der Familienstand „Verheiratet“ ist“**
* **„Konfigurieren Sie dieses Formular, um Daten an das Customer Relationship Management-System zu senden“**

Dieser spezielle AEM Forms-KI-Assistent stellt die nächste Evolution bei der Formularerstellung dar, indem er die Leistungsfähigkeit von KI mit den robusten Formularfunktionen von AEM kombiniert, um Ihren Arbeitsablauf für die Formularerstellung zu optimieren.
