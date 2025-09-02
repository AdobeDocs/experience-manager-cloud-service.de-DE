---
title: Forms Experience Builder
description: Schnelleres Erstellen leistungsstarker Formulare mithilfe von Formularfragmenten
feature: Edge Delivery Services
hide: true
index: false
hidefromtoc: true
role: Admin, Architect, Developer
source-git-commit: fe34b44d02c308e7d18a08dd05f21abc67bd0cb2
workflow-type: tm+mt
source-wordcount: '946'
ht-degree: 4%

---


# Einführung in Forms Experience Builder

>[!IMPORTANT]
>
> **Dokumentation kann sich ändern**: Diese Dokumentation wird derzeit mit dem Produkt getestet und unterliegt möglichen Aktualisierungen und Überarbeitungen. Funktionen, Befehle und Beispiele können sich ändern, wenn Forms Experience Builder während des Early-Adopter-Programms weiterentwickelt wird.

AEM Forms Experience Builder nutzt die Leistungsfähigkeit von Generative AI, um die Erstellung und Aktualisierung digitaler Formularerlebnisse zu demokratisieren und zu beschleunigen. Durch die Ermöglichung von Intent-basierten Workflows, die durch natürliche Sprachinteraktionen gesteuert werden, ermöglicht es Benutzenden, Formulare nahtlos schnell und einfach zu entwerfen, zu ändern und zu optimieren.

Forms Experience Builder basiert auf modernen Web-Technologien und basiert auf fortschrittlichen KI-Services. Dadurch können sowohl technische als auch nicht-technische Anwender über konversationelle Benutzeroberflächen anspruchsvolle, professionelle Formulare erstellen. Dieser revolutionäre Ansatz reduziert die Wertschöpfungszeit von Tagen auf Stunden, beseitigt technische Hindernisse durch die Einfachheit der Benutzeroberfläche und skaliert die Modernisierungsbemühungen im gesamten Formular-Ökosystem.



## Kernfunktionen

Forms Experience Builder bietet zwei primäre Workflows zum Erstellen leistungsstarker digitaler Formulare:

### &#x200B;1. KI-gestützte Formularerstellung

**Erzeugung natürlicher Formulare**

Erstellen Sie vollständige Formulare von Grund auf mit einfachen englischen Beschreibungen. Beschreiben Sie einfach Ihre Anforderungen, z. B. „Erstellen eines Kunden-Feedback-Formulars mit Bewertungs- und Kommentarfeldern“, und der Forms Experience Builder generiert die entsprechende Formularstruktur. Mit dem Experience Builder von visuellen Editoren können Sie weitere Felder, Validierungsregeln und Übermittlungslogik hinzufügen.

**Dynamische Feldverwaltung**

Hinzufügen, Ändern oder Entfernen von Formularfeldern über Dialogbefehle. Die KI versteht den Kontext und kann basierend auf Ihren Anforderungen intelligent Feldtypen, Validierungsregeln und Verbesserungen der Benutzeroberfläche vorschlagen.

**Layout-Optimierung**

Formularlayouts und -konfigurationen mit natürlicher Sprache aktualisieren. Anforderungsänderungen wie „Formularlayout in Assistentenlayout ändern“ und Forms Experience Builder wendet geeignete Stil- und Layout-Anpassungen an.

**Umfassende Konfiguration der Übermittlungsaktion**

Konfigurieren Sie die Formularübermittlung für die Integration mit Ihren vorhandenen Geschäftssystemen:

- **E-Mail-Integration**: Einrichten automatisierter E-Mail-Benachrichtigungen und -Bestätigungen
- **REST-API-Endpunkte**: Verbinden mit benutzerdefinierten Programmen und Services
- **Cloud-**: Integration mit Azure Blob Storage, SharePoint und OneDrive
- **Workflow-**: Verbindung zu Power Automate und Workfront Fusion herstellen
- **Marketing-Plattformen**: Direkte Integration mit Marketo für Lead-Management
- **AEM-Workflows**: Vorhandene AEM-Workflow-Funktionen nutzen


### &#x200B;2. Intelligenter Import und Konversion

**Unterstützte Importformate**

Transformieren vorhandener Formulare und Dokumente in interaktive digitale Erlebnisse. Forms Experience Builder unterstützt:

- **Acroforms**: Interaktive PDF forms mit vorhandenen Feldstrukturen
- **XFA-PDFs**: Komplexe XML-basierte Formulararchitekturen
- **Einfache PDF**: In interaktive Formulare konvertierte statische Dokumente
- **Bilder und Screenshots**: JPG, PNG-Formate (bitte mit dem Team nach Größenbeschränkungen suchen)
- **Handgezeichnetes Forms**: Skizzen und Papierformularbilder


**Intelligenter Konvertierungsprozess**

Der hochgeladene Inhalt wird analysiert nach:

- Erkennen von Feldtypen und Beziehungen
- Layout so weit wie möglich beibehalten
- Modernes responsives Design
- Erweiterte Validierung und bedingte Logik hinzufügen
- Optimierung für Barrierefreiheit und mobile Erlebnisse

## Funktionsweise

Forms Experience Builder folgt einem einfachen, dialogorientierten Ansatz:

    ┌─────────────────┐    ┌─────────────────┐    ┌─────────────────┐
    │ 1. beschreiben    │───▶│ 2. KI erstellt │───▶│ 3. Verfeinern und    Formular │
    │      │    │   │    │ Konfigurieren      │
    │   │    │                 │    │                 │
    └─────────────────┘    └─────────────────┘    └─────────────────┘
    │                       │                       │
    │                       │                       │
    ▼                       ▼                       ▼
    ┌───────────────────────────────────────────────────────────────────────────┐
    │ „Erstellen eines Kreditantragsformulars“ → Formular mit relevanten                  │
    │ „E-Mail-Feld hinzufügen“           Felder und Grundeinstellungen →                          │
    │ „Wert des E-Mail-Felds auf @firstname@gmail.com setzen“ → Validierungsregeln   │
    └───────────────────────────────────────────────────────────────────────────┘

## Beispielszenarien:

:::: landing-cards-container
:::
![icon](https://cdn.experienceleague.adobe.com/icons/file-pdf.svg)

**PDF forms in Digital Forms umwandeln**

Konvertieren von Acroforms, XFA-PDFs oder einfachen PDF-Dokumenten in responsive, interaktive digitale Formulare mit erweiterten Funktionen.
:::

:::
![icon](https://cdn.experienceleague.adobe.com/icons/data-transfer-up.svg)

**Ältere XFA-Forms modernisieren**

Transformieren Sie komplexe XFA-Anwendungen in moderne, barrierefreie digitale Erlebnisse mit verbesserten Benutzer-Workflows.
:::

:::
![icon](https://cdn.experienceleague.adobe.com/icons/image.svg)

**Konvertieren von Screenshots in Digital Forms**

Verwandeln Sie Bilder, Screenshots oder handgezeichnete Formulare in voll funktionsfähige digitale Erlebnisse.
:::
::::

<!-- #### Import and Enhance Web Forms

Import existing HTML forms and enhance them with advanced features while preserving existing functionality.

**Key benefits:**

- Advanced validation and business logic
- Conditional field behaviors
- Multi-channel submission options
- Enhanced user experience design -->

## Forms Experience Builder im Vergleich zur herkömmlichen Entwicklung

| Aspekt | Erstellung herkömmlicher Formulare | Forms Experience Builder |
|--------|---------------------------|----------------------|
| **Zeit zum Erstellen** | 2-3 Tage | 2-3 Stunden |
| **Technisches Wissen** | Erforderlich | Nicht erforderlich |
| **Validierungsregeln** | Manuelle Kodierung | Natürliche Sprache |
| **Barrierefreiheit** | Manuelle Implementierung | Integrierte Compliance |


## Vorteile für Organisationen

:::: landing-cards-container
:::
![icon](https://cdn.experienceleague.adobe.com/icons/users.svg)

**Demokratisierte Formularerstellung**

Nicht-technische Anwender in die Lage versetzen, anspruchsvolle Formulare zu erstellen, ohne Wissen durch Gespräche in natürlicher Sprache zu programmieren.
:::

:::
![icon](https://cdn.experienceleague.adobe.com/icons/bolt.svg)

**Verkürzte Time-to-Value (TTV)**

Drastische Beschleunigung der Formularentwicklung von Tagen auf Stunden, sodass digitale Initiativen schneller auf den Markt kommen können.
:::

:::
![icon](https://cdn.experienceleague.adobe.com/icons/lightbulb.svg)

**Einfachheit der Benutzeroberfläche**

Eliminieren Sie die Lernkurve mit einer intuitiven Gesprächsoberfläche, reduzieren Sie die Schulungszeit und steigern Sie die Akzeptanz.
:::

:::
![icon](https://cdn.experienceleague.adobe.com/icons/layers.svg)

**Skalierung der Modernisierungsmaßnahmen**

Modernisieren Sie ältere Formularportfolios effizient, behalten Sie die Geschäftslogik bei und verbessern Sie das Benutzererlebnis in Ihrem gesamten Formularökosystem.
:::
::::

## Onboarding

Forms Experience Builder ist derzeit als Teil des Early Access (EA)-Programms verfügbar. Um teilzunehmen und Zugang zu erhalten, benötigen Sie die folgenden Informationen:

### Erforderliche Informationen

- **IMS-Organisations-ID**: Ihre Adobe-Organisationskennung
- **Programm-ID**: Ihre spezifische Programmkennung in Adobe Experience Cloud
- **Projektdetails**: Zeitlicher Ablauf, Umfang und vorgesehene Anwendungsfälle
- **Offizielle E-Mail**: Dem Adobe-Konto Ihres Unternehmens zugeordnet


### Abrufen der IMS-Organisations-ID und Programm-ID

Detaillierte Anweisungen zum Suchen Ihrer IMS-Organisations-ID und Programm-ID finden Sie unter:

- [Einrichtungshandbuch für Adobe Experience Cloud-Organisationen](/help/onboarding/cloud-manager-introduction.md)
- [Programm- und Umweltmanagement](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md)

### Zugriff anfordern

1. Erfassen Sie Ihre IMS-Organisations-ID und Programm-ID mithilfe der oben genannten Handbücher
2. Senden einer E-Mail an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) mit Zugriffsanfrage
3. In Ihre Anfrage einschließen:
   - Organisationsname und IMS-Organisations-ID
   - Programm-ID
   - Projektzeitplan und -umfang
   - Vorgesehene Anwendungsfälle und Geschäftsziele

>[!IMPORTANT]
>
> **Programm für eingeschränkte Verfügbarkeit**: Der Zugriff auf Forms Experience Builder muss von den internen Stakeholdern genehmigt werden. Adobe prüft Ihre Anfrage auf der Grundlage der Programmkapazität und der Ausrichtung an den Kriterien für den frühzeitigen Zugriff. Die Genehmigung ist nicht garantiert und hängt von der aktuellen Programmverfügbarkeit ab.

Weitere Informationen zum Early-Access-Programm und seinen Funktionen finden Sie in der [AEM Forms Early Access-Dokumentation](/help/forms/early-access-ea-features.md).


## Erste Schritte

Informationen zu den ersten Schritten mit Forms Experience Builder finden Sie in der [Dokumentation zu Forms Experience Builder](forms-ai-assistant-getting-started.md). Sie können auf Forms Experience Builder je nach bevorzugtem Workflow über den AEM Forms-Editor oder den universellen Editor zugreifen.

Für Unternehmen, die ihre Formularerstellungsprozesse umgestalten möchten, bietet Forms Experience Builder eine leistungsstarke, intuitive Lösung, die die Flexibilität der konversativen KI mit der Robustheit der Formularverwaltung auf Unternehmensebene kombiniert.
