---
title: KI-Assistenzkraft in Adobe Experience Manager (Limited Beta)
description: Verwenden Sie den KI-Assistenten in Adobe Experience Manager, um Antworten zu finden, Fehler zu beheben und zu erkunden, ob es sich um Sites, Assets, Forms und Cloud Manager handelt.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: false
hidefromtoc: true
source-git-commit: e454581a2e6f2b8184a54d6550daec60e58bbc6c
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 1%

---

# Über den KI-Assistenten in Adobe Experience Manager {#aem-home}

Der KI-Assistent in AEM (Adobe Experience Manager) bietet eine Dialogschnittstelle, die die Suche nach Antworten auf Ihre Adobe Experience Manager-bezogenen Abfragen optimiert. Es hilft Ihnen beim Zugriff auf Produktwissen, bei der Fehlerbehebung und bei der Erforschung von Informationen, die unter Experience League verfügbar sind. Im Rahmen des eingeschränkten Beta-Programms unterstützt der AI-Assistent Adobe Experience Manager as a Cloud Service, einschließlich Sites, Assets, Forms und Cloud Manager.

>[!IMPORTANT]
>Stellen Sie sicher, dass Sie die Benutzervereinbarung geprüft und eingereicht haben, damit Adobe die Funktion des KI-Assistenten für Sie aktivieren kann, damit Sie sie testen und am Beta-Programm teilnehmen können.
>
>Bei Fragen senden Sie eine E-Mail an [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com) aus Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse.

## Datenschutz, Sicherheit und Governance

Der KI-Assistent in AEM wurde mit einem starken Schwerpunkt auf Privatsphäre, Sicherheit und Governance entwickelt.

In diesem Artikel werden die vertrauensorientierten Funktionen beschrieben, die Sie vom KI-Assistenten erwarten können:

* Von der KI-Assistenzkraft werden keine personenbezogenen Daten verwendet, auch nicht zu Schulungszwecken.
* Der KI-Assistent hat keinen Zugriff auf Verbraucherdaten.
* Für die Interaktion mit dem AI-Assistenten ist eine explizite Berechtigung erforderlich.
* Vom Benutzer bereitgestellte Eingabeaufforderungen (Fragen, Abfragen usw.) werden nicht für andere Kunden freigegeben.


## Erfahren Sie mehr über den KI-Assistenten für Produktwissen {#ai-prod-insights}

Das Produktwissen umfasst Konzepte und Themen, die aus der Adobe Experience League-Dokumentation abgeleitet wurden. Diese Fragen können in die folgenden Untergruppen unterteilt werden:

| Produktwissen | Beispiele |
| --- | --- |
| Zielgerichtetes Lernen | <ul><li>Was ist der universelle Editor?</li><li>Wie erstelle ich ein Programm in Cloud Manager?</li></ul> |
| Offene Entdeckung | <ul><li>Wie verwende ich den universellen Editor?</li><li>Gibt es eine Möglichkeit, Inhalte von einer Umgebung in eine andere zu kopieren?</li></ul> |
| Fehlerbehebung | <ul><li>Warum kann ich nicht auf den universellen Editor zugreifen?</li><li>Warum schlägt meine Pipeline fehl?</li></ul> |

Der aktuelle Umfang des AI-Assistenten konzentriert sich auf Fragen zu Produktwissen für Adobe Experience Manager as a Cloud Service. Dieser Umfang umfasst umfassende Unterstützung für wichtige Bereiche wie Sites, Assets, Forms und Cloud Manager.

## Wie können effektive Fragen gestellt werden? {#ai-craft-questions}

Um die genauesten Antworten vom KI-Assistenten zu erhalten, müssen Sie Ihre Fragen klar und kontextbezogen formulieren. Verwenden Sie die folgenden Tipps, um sicherzustellen, dass Ihre Abfragen klar und gut strukturiert sind:

* Geben Sie Ihre Aufgabe oder Frage klar und präzise an.
* Vermeiden Sie mehrdeutige Formulierungen oder zu komplexe Syntax, um das Verständnis zu verbessern.
* Fügen Sie relevanten Kontext zu Ihrer Aufgabe oder Frage hinzu, da dieser Ansatz dem KI-Assistenten dabei hilft, präzisere und relevantere Antworten bereitzustellen.

### Beispiele für nicht unterstützte Fragen {#ai-unsupported-questions}

| Flächendiagramm | Beispiele |
| --- | --- |
| Operative Einblicke | <ul><li>Wie viele Entwicklungsumgebungen gibt es in meinem Mandanten?</li><li>Wer hat die letzte Produktions-Pipeline gestartet?</li></ul> |
| Fehlerbehebung | <ul><li>Warum schlägt meine Produktions-Pipeline fehl?</li></ul> |
| Aufgaben und Automatisierung | <ul><li>Konfigurieren Sie eine Code-Qualitäts-Pipeline von einer Entwicklungsverzweigung für mich.</li></ul> |


## Verwenden des KI-Assistenten {#ai-use}


### Konversation starten oder zurücksetzen

Sie können den KI-Assistenten zurücksetzen und eine neue Konversation starten, wenn Sie Themen ändern möchten. Diese Funktion ist besonders hilfreich bei der Fehlerbehebung bei Abfragen, die fehlschlagen oder falsche Informationen bereitstellen.

![Schaltfläche &quot;Konversation starten&quot;](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**So starten oder setzen Sie eine Konversation zurück:**

1. Klicken Sie im KI-Assistenten auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Um den KI-Assistenten über ein neues Thema oder eine Themenänderung zu informieren, klicken Sie auf **Neue Unterhaltung starten**.

### Erkennung verwenden

Der AI-Assistent verfügt über eine Funktion zur Erkennung von Themen und Kategorien, mit der Sie die unterstützten Themen und Kategorien erkunden können.

![Symbol &quot;Glühbirne&quot;für Ideen ](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**So verwenden Sie die Auffindbarkeit:**

1. Klicken Sie in der rechten oberen Ecke des AI-Assistenten auf das Symbol ![Lernen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).
1. Wählen Sie eine Kategorie aus, um eine Liste der zugehörigen Eingabeaufforderungen anzuzeigen.
1. Wählen Sie eine Eingabeaufforderung aus, um besser zu verstehen, welche Arten von Fragen der KI-Assistent beantworten kann.

### Feedback zum KI-Assistenten geben

Ihre Eingaben tragen zur Verbesserung der Leistung und Genauigkeit des KI-Assistenten bei.

Geben Sie mit den folgenden Optionen Ihr Feedback zu Ihrer Erfahrung an den KI-Assistenten weiter:

![ Dreht nach oben, bewegt sich nach unten und markiert die Flag-Symbole](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| Symbol | Beschreibung |
| --- | --- |
| ![ Dreht das Symbol &quot;Outdoor&quot;nach oben](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Klicken Sie auf , um anzugeben, was gut gelaufen ist, und um positives Feedback zu teilen. |
| ![ Dreht das Symbol für den Ausschnitt nach unten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Klicken Sie auf , um Verbesserungsvorschläge zu unterbreiten. Fügen Sie spezifische Kommentare zu Ihrem Erlebnis hinzu, die täglich geprüft werden. |
| ![Flag-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Klicken Sie auf diese Schaltfläche, um Bedenken zu melden oder detailliertes Feedback zu Ihrer Interaktion mit dem KI-Assistenten zu geben. |

## Häufig gestellte Fragen zu AI Assistant {#ai-faq}

Im Folgenden finden Sie Antworten auf häufige Fragen zum KI-Assistenten:

* **Werden die vom KI-Assistenten bereitgestellten Informationen in Echtzeit bereitgestellt?**\
  Nein. Der AI-Assistent kann seinen Inhalt aus der Adobe Experience League-Dokumentation beziehen. Aktualisierungen des Inhalts können einige Zeit in Anspruch nehmen, um seine Antworten widerzuspiegeln.
* **Welche Adobe-Anwendungen unterstützt der AI-Assistent?**\
  Derzeit unterstützt der AI-Assistent AEM as a Cloud Service, einschließlich Sites, Assets, Forms und Cloud Manager, insbesondere bei Produktinformationen.
* **Welche Funktionen hat der KI-Assistent?**\
  AI Assistant wurde entwickelt, um Fragen im Zusammenhang mit Adobe-Produktwissen zu beantworten.
* **Verwendet der KI-Assistent personenbezogene Daten für Schulungsdaten?**\
  Nein. Die KI-Assistenzkraft verwendet personenbezogene Daten nicht für Schulungszwecke. Vermeiden Sie die Weitergabe personenbezogener Daten über Sie oder andere Personen, einschließlich Name oder Kontaktdaten, an den KI-Assistenten.



