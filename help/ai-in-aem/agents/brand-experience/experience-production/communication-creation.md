---
title: Kommunikationserstellungsauftrag
description: Erfahren Sie mehr über den Kommunikationserstellungsauftrag von Brand Experience Agents und darüber, wie Sie mit natürlicher Sprache interaktive Kommunikation erstellen können.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: 49111cdb-e714-4590-8b81-382377083d6e
source-git-commit: 9be60c79ef001edf7590a8fd3fd64c1a9a1ab9f9
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 0%

---


# Kommunikations-Erstellungskompetenz {#ic-creation-skill}

<!-- UNCOMMENT ACTIVATION SECTION AT THE BOTTOM ONCE THIS IS NO LONGER ALPHA -->

>[!NOTE]
>
> Der Kommunikationserstellungsauftrag befindet sich derzeit in der Alpha-Phase. Wenn Sie teilnehmen möchten, senden Sie bitte eine Anfrage von Ihrer offiziellen E-Mail-Adresse an [aem-forms-ea@adobe.com.](mailto:aem-forms-ea@adobe.com)

[Interaktive Kommunikation](/help/forms/introduction-to-interactive-communication.md) sind personalisierte, datengesteuerte Dokumente, die für die Geschäftskorrespondenz entwickelt wurden, z. B. Kontoauszüge, Richtliniendokumente, Rechnungen, Begrüßungs-Kits und Mitteilungen über finanzielle Leistungen. Im Gegensatz zu Formularen, die Eingaben von Benutzern erfassen, generieren interaktive Kommunikationen Ausgabedokumente mit dynamischen, empfängerspezifischen Inhalten.

Der Kommunikationserstellungsauftrag ist eine Funktion des [Markenerlebnisagenten](/help/ai-in-aem/agents/brand-experience/overview.md) die zur Entwicklung interaktiver Kommunikationen mithilfe natürlicher Sprachaufforderungen entwickelt wurde. Dieser Auftrag generiert automatisch personalisierte, datengesteuerte Korrespondenz für den Druck (im PDF-Format). Der Auftrag wird über den KI-Assistenten angezeigt.

Zu den wichtigsten Vorteilen der Schaffung von Kommunikationsjobs gehören:

* **Beschleunigte Kommunikationsentwicklung**: Erstellen Sie schnell Kommunikation mit einfachen Befehlen in natürlicher Sprache, wodurch die Notwendigkeit entfällt, herkömmliche Produktschnittstellen zu lernen.
* **Konsistente und markeninterne Korrespondenz**: Erstellen Sie mithilfe genehmigter Vorlagen und Stile Kommunikation, die dem Branding, den Vorlagen und Stilrichtlinien Ihres Unternehmens entspricht.
* **Geringere technische Hürde**: Ermöglichen Sie es Geschäftsbenutzern, einfach Kommunikation zu erstellen, ohne fortgeschrittene technische oder fundierte Produkterfahrung zu benötigen.

## Funktionen {#capabilities}

<!-- * **Create personalized communications with plain text prompt**: You can create communication documents for print (in PDF format) by submitting your requirements in plain language. The job automatically generates appropriate document structures, layouts, and data bindings based on your natural language description. -->

* **Erstellen aus Vorlagen**: Sie können genehmigte Organisationsvorlagen verwenden, um Markenkonsistenz und Compliance-Standards sicherzustellen. Der Auftrag nutzt Ihre vorhandenen Vorlagen und Stilrichtlinien, um eine markeninterne Korrespondenz zu erstellen, die den gesetzlichen Anforderungen entspricht.

* **Importieren und Konvertieren vorhandener Bilder und Dokumente in interaktive**: Sie können vorhandene Dokumente importieren und in interaktive Kommunikation umwandeln. Der Auftrag analysiert hochgeladene Inhalte, um Felder zu erkennen, Layouts beizubehalten und datengesteuerte Korrespondenz mit Funktionen für dynamische Inhalte zu erstellen. Zu den unterstützten Formaten gehören PDFs, Bilder (JPG, PNG) und handgezeichnete Vorlagen.

## Eingabeaufforderungen im Beispiel {#sample-prompts}

* *Erstellen Sie eine Kommunikation für einen Darlehensauszug mithilfe der Vorlage unter https://[aem-author-url]/path/to/pdf/file*
* *Erstellen Sie eine Kommunikation von PDF unter https://[aem-author-url]/path/to/pdf/file*
* *Erstellen Sie eine Kommunikation aus der Bilddatei unter https://[aem-author-url]/path/to/image/file*
* https:// Erstellen Sie einen Brief mit einer PDF-Datei unter [-aem-author-url]/path/to/pdf/file

## Verfeinern der Kommunikation {#refine-with-ic-editor}

Nachdem Sie Ihre anfängliche Kommunikationsstruktur mit dem KI-Assistenten erstellt haben, können Sie den Editor für interaktive Kommunikation verwenden, um Ihr Dokument zu verfeinern und zu verbessern. Im Editor für interaktive Kommunikation können Sie Eingabeaufforderungen in natürlicher Sprache bereitstellen, um:

* **Felder und Inhalte hinzufügen**: Fügen Sie Ihren Kommunikationsdokumenten mithilfe natürlicher Eingabeaufforderungen neue Felder, Textblöcke, Bilder, Diagramme, Tabellen und andere Komponenten hinzu. Der Auftrag interpretiert Ihre Anweisungen und fügt die entsprechenden Elemente mit der richtigen Struktur und Formatierung ein.

* **Felder und Inhalte bearbeiten**: Ändern Sie vorhandene Felder und Inhalte in Ihren Kommunikationsdokumenten mithilfe von Dialogbefehlen. Feldeigenschaften aktualisieren, Textinhalt ändern, Datenbindungen anpassen und Komponentenkonfigurationen verfeinern.

* **Felder und Inhalte entfernen**: Löschen unerwünschter Felder, Komponenten oder Abschnitte aus Ihren Kommunikationsdokumenten mithilfe von Anweisungen in natürlicher Sprache. Der Auftrag entfernt die angegebenen Elemente unter Beibehaltung der Dokumentstruktur und der Layout-Integrität.

* **Stilfelder und Inhalte**: Wenden Sie Formatierung und Stile auf Felder und Inhalte über natürliche Sprachaufforderungen an. Passen Sie Schriftarten, Farben, Ausrichtung, Abstand und andere visuelle Eigenschaften an Ihre Markenrichtlinien und Design-Anforderungen an.

### Eingabeaufforderungen zur Verfeinerung der Kommunikation {#sample-prompts-refining}

* *Generieren eines Zahlungsbriefs für Kfz-Versicherungsansprüche*
* *Machen Sie den Text des Haftungsausschlusses kursiv*
* *Ändern Sie die Schriftgröße des Haftungsausschlusses in 12*
* *Aktualisieren Sie die Schriftfarbe des Textes des Haftungsausschlusses auf Rot*
* *Aktualisieren Sie die Hintergrundfarbe der Textfelder für Kopf- und Fußzeile auf Hellgrau*
* *Fügen Sie ein neues Haftungsausschluss-Bedienfeld mit Signatur- und Bestätigungsfeldern hinzu*
* *Entfernen Sie das Bestätigungstext-Feld*
* *Fügen Sie eine Tabelle mit Zahlungsdetails mit drei Spalten hinzu*
* *Aktualisieren Sie die Ausrichtung des Felds „Richtliniennummer“ auf die Mitte*
* *Ändern Sie den Zeilenabstand im Abschnitt Nutzungsbedingungen auf 1.5*

Weitere Informationen zu den Funktionen des Editors für interaktive Kommunikation finden Sie unter [Dokumentation zu interaktiven Kommunikationen.](/help/forms/introduction-to-interactive-communication.md)

<!-- UNCOMMENT ONCE NO LONGER ALPHA -->

<!--
## Activation {#activation}

You can explore AEM Agents through the [Playground](https://www.aem.live/developer/aem-playground), or connect with your CSM or TAM to discuss access via the Agentic SKU.
-->
