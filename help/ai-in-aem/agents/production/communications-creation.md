---
title: Kommunikations-Erstellungskompetenz
description: Erfahren Sie mehr über die Kommunikationsfähigkeiten des Experience Production Agents und wie Sie natürliche Sprache verwenden können, um interaktive Kommunikation zu erstellen.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: aa8369979c99535f0fd77e6a51af10cc17afd971
workflow-type: tm+mt
source-wordcount: '769'
ht-degree: 0%

---


# Kommunikations-Erstellungskompetenz {#ic-creation-skill}

>[!NOTE]
>
> Die Fähigkeit zur Kommunikationserstellung befindet sich derzeit in der Alpha-Phase. Wenn Sie teilnehmen möchten, senden Sie bitte eine Anfrage von Ihrer offiziellen E-Mail-Adresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com).

Interaktive Kommunikation sind personalisierte, datengesteuerte Dokumente, die für die Geschäftskorrespondenz entwickelt wurden, z. B. Kontoauszüge, Richtliniendokumente, Rechnungen, Begrüßungs-Kits und Leistungsbescheide. Im Gegensatz zu Formularen, die Eingaben von Benutzern erfassen, generieren interaktive Kommunikationen Ausgabedokumente mit dynamischen, empfängerspezifischen Inhalten.

Die Fähigkeit zur Kommunikationserstellung ist eine Funktion des Experience Production Agents, die dazu konzipiert ist, interaktive Kommunikation mithilfe natürlicher Sprachaufforderungen zu entwickeln. Diese Fähigkeit generiert automatisch personalisierte, datengesteuerte Korrespondenz für den Druck (im PDF-Format). Die Qualifikation wird durch den KI-Assistenten angezeigt.

Zu den wichtigsten Vorteilen der Kommunikationsfähigkeit gehören:

* **Beschleunigte Kommunikationsentwicklung**: Erstellen Sie schnell Kommunikation mit einfachen Befehlen in natürlicher Sprache, wodurch die Notwendigkeit entfällt, herkömmliche Produktschnittstellen zu lernen.
* **Konsistente und markeninterne Korrespondenz**: Erstellen Sie mithilfe genehmigter Vorlagen und Stile Kommunikation, die dem Branding, den Vorlagen und Stilrichtlinien Ihres Unternehmens entspricht.
* **Geringere technische Hürde**: Ermöglicht es Geschäftsbenutzern, einfach Kommunikation zu erstellen, ohne fortgeschrittenes technisches oder fundiertes Produktwissen zu benötigen.

## Funktionen {#capabilities}

<!-- * **Create personalized communications with plain text prompt**: You can create communication documents for print (in PDF format) by submitting your requirements in plain language. The agent automatically generates appropriate document structures, layouts, and data bindings based on your natural language description. -->

* **Erstellen aus Vorlagen**: Sie können genehmigte Organisationsvorlagen verwenden, um Markenkonsistenz und Compliance-Standards sicherzustellen. Der Agent nutzt Ihre vorhandenen Vorlagen und Stilrichtlinien, um eine markeninterne Korrespondenz zu erstellen, die die gesetzlichen Anforderungen erfüllt.

* **Importieren und Konvertieren vorhandener Bilder und Dokumente in interaktive**: Sie können vorhandene Dokumente importieren und in interaktive Kommunikation umwandeln. Der Agent analysiert hochgeladene Inhalte, um Felder zu erkennen, Layouts beizubehalten und datengesteuerte Korrespondenz mit dynamischen Inhaltsfunktionen zu erstellen. Zu den unterstützten Formaten gehören PDFs, Bilder (JPG, PNG) und handgezeichnete Vorlagen.


## Eingabeaufforderungen im Beispiel {#sample-prompts}

* *Erstellen Sie eine Kommunikation für einen Darlehensauszug mithilfe der Vorlage unter https://[aem-author-url]/path/to/pdf/file*
* *Erstellen Sie eine Kommunikation von PDF unter https://[aem-author-url]/path/to/pdf/file*
* *Erstellen Sie eine Kommunikation aus der Bilddatei unter https://[aem-author-url]/path/to/image/file*
* https:// Erstellen Sie einen Brief mit einer PDF-Datei unter [-aem-author-url]/path/to/pdf/file


## Verfeinern der Kommunikation {#refine-with-ic-editor}


Nachdem Sie Ihre anfängliche Kommunikationsstruktur mit dem KI-Assistenten erstellt haben, können Sie den Editor für interaktive Kommunikation verwenden, um Ihr Dokument zu verfeinern und zu verbessern. Im Editor für interaktive Kommunikation können Sie Eingabeaufforderungen in natürlicher Sprache bereitstellen, um:

* **Felder und Inhalte hinzufügen**: Fügen Sie Ihren Kommunikationsdokumenten mithilfe natürlicher Eingabeaufforderungen neue Felder, Textblöcke, Bilder, Diagramme, Tabellen und andere Komponenten hinzu. Der Agent interpretiert Ihre Anweisungen und fügt die entsprechenden Elemente mit der richtigen Struktur und Formatierung ein.

* **Felder und Inhalte bearbeiten**: Ändern Sie vorhandene Felder und Inhalte in Ihren Kommunikationsdokumenten mithilfe von Dialogbefehlen. Feldeigenschaften aktualisieren, Textinhalt ändern, Datenbindungen anpassen und Komponentenkonfigurationen verfeinern.

* **Felder und Inhalte entfernen**: Löschen unerwünschter Felder, Komponenten oder Abschnitte aus Ihren Kommunikationsdokumenten mithilfe von Anweisungen in natürlicher Sprache. Der Agent entfernt die angegebenen Elemente unter Beibehaltung der Dokumentstruktur und der Layout-Integrität.

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

Weitere Informationen zu den Funktionen des Editors für interaktive Kommunikation finden Sie unter [Dokumentation zu interaktiven Kommunikationen](/help/forms/introduction-to-interactive-communication.md).

## Aktivierung {#activation}

Um den Experience Production Agent für Ihr Unternehmen zu aktivieren, muss die Aktivierung über Adobe initiiert werden. Beginnen Sie den Prozess, indem Sie sich an wenden über:

* E-Mail: `experience-production-agent@adobe.com`
* Oder wenden Sie sich an Ihr persönliches Adobe-Accountteam.

Für ein effizientes Onboarding-Erlebnis sollten Sie die folgenden Details vorbereiten und bereitstellen:

Für **AEM as a Cloud Service** geben Sie die folgenden Kennungen frei:

* Unternehmens-ID
* `product_id`
* `profile_id`

Ihr AEM-Administrator kann diese finden, indem er:

1. Navigieren zu <https://adminconsole.adobe.com/>
1. **Adobe Experience Manager as a Cloud Service wird ausgewählt**
1. Auswählen der entsprechenden AEM-Instanz in Ihrer Umgebung
1. Auswählen eines Profils mit Lese-/Schreibberechtigungen für relevante Inhalte
1. Vollständige Browser-URL von dieser Seite kopieren
1. Extrahieren der `product_id`- und `profile_id` aus der URL\
   (z. B. enthält eine URL wie `https://adminconsole.adobe.com/products/profiles/users` diese Parameter).

Für das **Erstellen von Edge Delivery**-Dokumenten stellen Sie Ihrem Adobe-Team Folgendes zur Verfügung:

* Domains für Ihre Edge Delivery Services-Umgebung
* Entsprechende GitHub-Details:
   * Organisation (Org)
   * Repository (Repository)
   * Verzweigung

Die Bereitstellung vollständiger und genauer Informationen beschleunigt den Aktivierungsprozess und stellt die zeitnahe Bereitstellung des Experience Production Agents sicher.

