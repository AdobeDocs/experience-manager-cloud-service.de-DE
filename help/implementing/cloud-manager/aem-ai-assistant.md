---
title: KI-Assistent in Adobe Experience Manager (eingeschränktes Beta)
description: Verwenden Sie den KI-Assistenten in Adobe Experience Manager, um Antworten zu finden, Fehler zu beheben und Sites, Assets, Forms und Cloud Manager zu erkunden.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: false
hidefromtoc: true
exl-id: 6cdf7f65-7112-420a-90c1-564f0ef8ceaf
source-git-commit: d3ade6ee9216b44b55d6808d8acffe83f1e263c9
workflow-type: tm+mt
source-wordcount: '1122'
ht-degree: 1%

---

# Über den KI-Assistenten in Adobe Experience Manager {#aem-home}

Der KI-Assistent in AEM (Adobe Experience Manager) bietet eine Gesprächsoberfläche, die darauf ausgelegt ist, die Suche nach Antworten auf Ihre Adobe Experience Manager-bezogenen Abfragen zu optimieren. Es hilft Ihnen, auf Produktwissen zuzugreifen, Probleme zu beheben und die in Experience League verfügbaren Informationen zu erkunden. Während des eingeschränkten Beta-Programms unterstützt der KI-Assistent Adobe Experience Manager as a Cloud Service, einschließlich Sites, Assets, Forms und Cloud Manager.

>[!IMPORTANT]
>Sie müssen die Benutzervereinbarung gelesen und eingereicht haben, damit Adobe die KI-Assistentenfunktion aktivieren kann, damit Sie sie testen und am Beta-Programm teilnehmen können.
>
>Bei Fragen senden Sie eine E-Mail an [Grp-AEMAIASSISTANT@adobe.com](mailto:Grp-AEMAIASSISTANT@adobe.com) von Ihrer mit Ihrer Adobe ID verknüpften E-Mail-Adresse.

## Datenschutz, Sicherheit und Governance

Der KI-Assistent in AEM ist so konzipiert, dass ein besonderer Schwerpunkt auf Datenschutz, Sicherheit und Governance gelegt wird.

In diesem Artikel werden die vertrauensorientierten Funktionen beschrieben, die Sie vom KI-Assistenten erwarten können:

* KI Assistant verwendet keine personenbezogenen Daten, auch nicht für Trainingszwecke.
* Der KI-Assistent hat keinen Zugriff auf Verbraucherdaten.
* Für die Interaktion mit dem KI-Assistenten ist eine explizite Berechtigung erforderlich.
* Von Benutzenden bereitgestellte Eingabeaufforderungen (Fragen, Abfragen usw.) werden nicht für andere Kundinnen und Kunden freigegeben.


## Lernen Sie den KI-Assistenten für Produktkenntnisse kennen {#ai-prod-insights}

Das Produktwissen umfasst Konzepte und Themen, die aus der Dokumentation zu Adobe Experience League abgeleitet wurden. Diese Fragen lassen sich in die folgenden Untergruppen einteilen:

| Produktkenntnisse | Beispiele |
| --- | --- |
| Punktuelles Lernen | <ul><li>Was ist der universelle Editor?</li><li>Wie erstelle ich ein Programm in Cloud Manager?</li></ul> |
| Erkennung öffnen | <ul><li>Wie verwende ich den universellen Editor?</li><li>Gibt es eine Möglichkeit, Inhalte von einer Umgebung in eine andere zu kopieren?</li></ul> |
| Fehlerbehebung | <ul><li>Warum kann ich nicht auf den universellen Editor zugreifen?</li><li>Warum schlägt meine Pipeline fehl?</li></ul> |

Der aktuelle Umfang des KI-Assistenten konzentriert sich auf Fragen zum Produktwissen von Adobe Experience Manager as a Cloud Service. Dieser Umfang umfasst umfassende Unterstützung für wichtige Bereiche wie Sites, Assets, Forms und Cloud Manager.

## KI-Assistent für AEM Forms (Forms Experience Builder) {#ai-forms-builder}

Zusätzlich zum allgemeinen KI-Assistenten für Produktkenntnisse bietet AEM einen speziellen **KI-Assistenten für AEM Forms (Forms Experience Builder)**. Dieser erweiterte Assistent kann Sie aktiv bei der Erstellung und Konfiguration von Formularen unterstützen, indem Sie in natürlicher Sprache Aufforderungen erhalten und formularspezifische Fragen beantworten.

### Schlüsselfunktionen

Der KI-Assistent für AEM Forms bietet:

* **Formularerstellung**: Erstellen neuer Formulare von Grund auf mithilfe von Beschreibungen in natürlicher Sprache
* **Design-Import**: Konvertieren vorhandener Designs (PDF, Figma, Bilder) in funktionale AEM-Formulare
* **Formularkonfiguration**: Felder, Bereiche, Validierungsregeln und bedingte Logik hinzufügen
* **Layout-**: Organisieren der Formularstruktur und Optimierung für verschiedene Geräte
* **Integrations-Setup**: Konfigurieren von Formularübermittlungen und Datenverarbeitung
* **Produktkenntnisse**: Antworten auf Fragen zu den Funktionen und Best Practices von AEM Forms

### Wo zugegriffen werden kann

Der KI-Assistent für AEM Forms ist verfügbar unter:

* **Universeller Editor**: Für Edge Delivery Services-Formulare mit visuellen Bearbeitungsfunktionen
* **Adaptiver Forms-Editor**: Für eine detaillierte Formularkonfiguration und erweiterte Funktionen
* **Benutzeroberfläche für die Verwaltung von Forms**: Für allgemeine Aufgaben zur Formularerstellung und -verwaltung

### Erste Schritte

>[!NOTE]
>
> Der KI-Assistent für AEM Forms (Forms Experience Builder) ist im Rahmen des Early-Adopter-Programms verfügbar. Senden Sie eine E-Mail von Ihrer Geschäftsadresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com), um den Zugriff anzufordern.

Weitere Informationen zur Verwendung des KI-Assistenten für AEM Forms, einschließlich detaillierter Beispiele und Best Practices, finden Sie in der Dokumentation zum KI-Assistenten für AEM Forms .

### Beispiel-Anwendungsfälle

* **„Erstellen Sie ein Formular für Kunden-Feedback mit den Feldern Name, E-Mail, Bewertung und Kommentare“**
* **„Konvertieren Sie dieses hochgeladene PDF-Anwendungsformular in ein digitales adaptives Formular“**
* **„Bedingte Logik hinzufügen, um Ehepartner-Informationen nur dann anzuzeigen, wenn der Familienstand „Verheiratet“ ist“**
* **„Konfigurieren Sie dieses Formular, um Daten an unser CRM-System zu senden“**

Dieser spezielle Forms-KI-Assistent stellt die nächste Evolution bei der Formularerstellung dar, indem er die Leistungsfähigkeit von KI mit den robusten Formularfunktionen von AEM kombiniert, um Ihren Arbeitsablauf für die Formularerstellung zu optimieren.

## Wie man effektive Fragen formuliert {#ai-craft-questions}

Um die genauesten Antworten vom KI-Assistenten zu erhalten, müssen Ihre Fragen klar und in einem klaren Kontext formuliert werden. Verwenden Sie die folgenden Tipps, um sicherzustellen, dass Ihre Abfragen klar und gut strukturiert sind:

* Geben Sie Ihre Aufgabe oder Frage klar und prägnant an.
* Vermeiden Sie mehrdeutige Formulierungen oder eine übermäßig komplexe Syntax, um das Verständnis zu verbessern.
* Binden Sie relevanten Kontext zu Ihrer Aufgabe oder Frage ein, da dieser Ansatz dem KI-Assistenten hilft, präzisere und relevantere Antworten zu liefern.

### Beispiele für nicht unterstützte Fragen {#ai-unsupported-questions}

| Flächendiagramm | Beispiele |
| --- | --- |
| Operative Erkenntnisse | <ul><li>Wie viele Entwicklungsumgebungen gibt es in meinem Mandanten?</li><li>Wer hat die letzte Produktions-Pipeline gestartet?</li></ul> |
| Fehlerbehebung | <ul><li>Warum schlägt meine Produktions-Pipeline fehl?</li></ul> |
| Aufgaben und Automatisierung | <ul><li>Konfigurieren Sie eine Code-Qualitäts-Pipeline aus einer Entwicklungsverzweigung für mich.</li></ul> |


## Verwenden des KI-Assistenten {#ai-use}


### Starten oder Zurücksetzen einer Konversation

Sie können den KI-Assistenten zurücksetzen und eine neue Unterhaltung beginnen, wenn Sie Themen ändern möchten. Diese Funktion ist besonders hilfreich bei der Fehlerbehebung bei Abfragen, die fehlschlagen oder falsche Informationen liefern.

![Schaltfläche „Unterhaltung beginnen“](/help/implementing/cloud-manager/assets/ai-assistant-start-conversation.png)

**So starten oder setzen Sie eine Konversation zurück:**

1. Klicken Sie im KI-Assistenten auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg).
1. Um den KI-Assistenten über ein neues Thema oder eine Themenänderung zu informieren, klicken Sie auf **Neue Konversation beginnen**.

### Entdeckbarkeit verwenden

Der KI-Assistent enthält eine Entdeckungsfunktion, mit der Sie die unterstützten Themen und Kategorien erkunden können.

![IDEA Glühbirnensymbol](/help/implementing/cloud-manager/assets/ai-assistant-idea.png)

**So verwenden Sie Entdeckbarkeit:**

1. Klicken Sie in der oberen rechten Ecke des KI-Assistenten auf ![Lernsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Learn_18_N.svg).
1. Wählen Sie eine Kategorie aus, um eine Liste der zugehörigen Eingabeaufforderungen anzuzeigen.
1. Wählen Sie eine Eingabeaufforderung aus, um die Arten von Fragen, die der KI-Assistent beantworten kann, besser zu verstehen.

### Feedback zum KI-Assistenten geben

Ihre Eingabe trägt dazu bei, den KI-Assistenten für eine bessere Leistung und Genauigkeit zu verbessern.

Geben Sie Ihr Feedback zu Ihren Erfahrungen mit dem KI-Assistenten über die folgenden Optionen:

![Symbole „Daumen hoch“, „Daumen runter“ und „Markierung“](/help/implementing/cloud-manager/assets/ai-assistant-feedback.png)

| Symbol | Beschreibung |
| --- | --- |
| ![Miniaturansicht nach oben](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbUpOutline_18_N.svg) | Klicken Sie hier, um anzugeben, was gut gelaufen ist, und um positives Feedback zu geben. |
| ![Miniaturansicht nach unten](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ThumbDownOutline_18_N.svg) | Klicken Sie hier, um Verbesserungsvorschläge zu unterbreiten. Fügen Sie spezifische Kommentare zu Ihrem Erlebnis hinzu, die täglich überprüft werden. |
| ![Flag-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Flag_18_N.svg) | Klicken Sie hier, um Probleme zu melden oder detailliertes Feedback zu Ihrer Interaktion mit dem KI-Assistenten zu geben. |

## Häufig gestellte Fragen zum KI-Assistenten {#ai-faq}

Im Folgenden finden Sie Antworten auf einige häufig gestellte Fragen zum KI-Assistenten:

* **Werden die Informationen vom KI-Assistenten in Echtzeit bereitgestellt?**\
  Nein. Der KI-Assistent bezieht seinen Inhalt aus der Adobe Experience League-Dokumentation. Es kann einige Zeit dauern, bis Aktualisierungen des Inhalts in den Antworten widergespiegelt werden.
* **Welche Adobe-Programme unterstützt AI Assistant?**\
  Derzeit unterstützt AI Assistant AEM as a Cloud Service, einschließlich Sites, Assets, Forms und Cloud Manager, speziell für Anfragen zum Produktwissen.
* **Welche Funktionen hat der KI-Assistent?**\
  Der KI-Assistent beantwortet Fragen zu Adobe-Produktkenntnissen.
* **Verwendet der KI-Assistent personenbezogene Daten für Trainingsdaten?**\
  Nein. AI Assistant verwendet keine personenbezogenen Daten für Trainingszwecke. Vermeiden Sie es, persönliche Informationen über sich selbst oder andere, einschließlich Namen oder Kontaktdaten, mit dem KI-Assistenten zu teilen.
