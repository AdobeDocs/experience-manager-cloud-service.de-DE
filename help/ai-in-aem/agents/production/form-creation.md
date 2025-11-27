---
title: Qualifikation zur Formularerstellung
description: Erfahren Sie mehr über die Fähigkeit des Experience Production Agents zur Formularerstellung und darüber, wie Sie mit natürlicher Sprache Formulare von Grund auf neu erstellen können.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
source-git-commit: 01fce6fcdf1c8ada0422a84fccb9a89f395e2a0e
workflow-type: tm+mt
source-wordcount: '539'
ht-degree: 0%

---


# Qualifikation zur Formularerstellung {#form-creation-skill}

Die Fähigkeit zur Formularerstellung ist eine Funktion des Experience Production Agent, die dazu dient, Formulare mithilfe von Eingabeaufforderungen in natürlicher Sprache zu entwickeln. Diese Fähigkeit generiert automatisch die entsprechende Formularstruktur und die entsprechenden Feldtypen. Die Qualifikation wird durch den KI-Assistenten angezeigt.

Zu den wichtigsten Vorteilen der Fähigkeit zur Formularerstellung gehören:

* **Beschleunigte Formularentwicklung**: Erstellen Sie Formulare schnell mit
Einfache, natürliche Sprachbefehle machen das Erlernen herkömmlicher Produktoberflächen überflüssig.
* **Konsistente und markeninterne Erlebnisse**: Erstellen Sie Formulare, die dem Branding, den Vorlagen und Stilrichtlinien Ihres Unternehmens entsprechen, indem Sie genehmigte Vorlagen und Stile verwenden.
* **Geringere technische Hürde**: Ermöglicht es Geschäftsbenutzern, Formulare einfach zu erstellen, ohne fortgeschrittene technische oder fundierte Produktkenntnisse zu benötigen.

## Funktionen {#capabilitiess}

* **Erstellen eines neuen Formulars mit einer Textaufforderung**: Sie können ein Formular erstellen, indem Sie Ihre Anforderungen in einfacher Sprache übermitteln. Der Agent generiert automatisch die entsprechende Formularstruktur, Feldtypen und Markenerlebnisse basierend auf Ihrer Beschreibung in natürlicher Sprache und der angegebenen Vorlage. Diese Funktion beschleunigt die Formularerstellung und stellt gleichzeitig sicher, dass die Marken- und Compliance-Standards eingehalten werden.

* **Importieren eines PDF-Dokuments und Konvertieren in ein Formular**: Sie können vorhandene PDF-Dokumente importieren und in Formulare umwandeln. Der Agent analysiert hochgeladene Inhalte, um Feldtypen zu erkennen, Layouts beizubehalten und Formulare mit responsiver Design- und Validierungslogik zu verbessern und gleichzeitig sicherzustellen, dass die Marken- und Compliance-Standards eingehalten werden.

  Wenn Sie eine der oben genannten Funktionen verwenden, werden Sie aufgefordert, den zu erstellenden Formulartyp auszuwählen, entweder eine auf Kernkomponenten basierende Vorlage für adaptive Formulare oder eine auf Edge Delivery Services basierende Vorlage für adaptive Formulare anzugeben und Ihren bevorzugten Pfad zum Speichern des Formulars anzugeben. Wenn Sie ein Formular erstellen, das auf Edge Delivery Services basiert, können Sie auch die GitHub-URL Ihres Repositorys angeben.


### Eingabeaufforderungen im Beispiel {#sample-prompts}

* *Erstellen Sie ein Formular für die Feedback-Sammlung mit den Feldern Name, E-Mail und Nachricht*
* *Erstellen Sie ein Formular für Kunden-Feedback mit Produktbewertung (1-5 Sterne), Kommentarfeld und optionaler E-Mail-Adresse*
* *Erstellen Sie ein Kontaktformular mit den Feldern „Name“, „E-Mail“, „Betreff“ und „Nachricht“*
* *Erstellen Sie ein Registrierungsformular mit persönlichen Informationen, Kontovoreinstellungen und Bedingungen zur Annahme*
* *Erstellen Sie ein Kreditkartenantragsformular, indem Sie die PDF-Datei importieren, die unter &quot;https://[aem-author-url]/path/to/pdf/file“ verfügbar ist*
* *Erstellen Sie ein Feedback-Formular mit dem Textbaustein unter &quot;<https://github.com/wkndforms/wesecure>&quot;*

## Verfeinern des Formulars {#refine-with-forms-experience-builder}

Nachdem Sie Ihre anfängliche Formularstruktur mit dem KI-Assistenten erstellt haben, können Sie den Forms Experience Builder verwenden, um:

* **Formulare aktualisieren**: Felder hinzufügen oder ändern, Feldtypen anpassen und den Stil nach Bedarf über den visuellen Editor aktualisieren.

* **Layout aktualisieren**: Neuanordnen von Abschnitten, Gruppen oder Feldern, Anpassen der Abstände und Ändern der visuellen Hierarchie, um die Benutzerfreundlichkeit zu verbessern und sicherzustellen, dass das Formular für Ihre Zielgruppe klar und intuitiv ist.

* **Geschäftslogik hinzufügen**: Erstellen Sie eine bedingte Logik, blenden Sie Regeln ein/aus, geben Sie Feldabhängigkeiten ein und definieren Sie Validierungsregeln.

* **Übermittlung konfigurieren** Konfigurieren Sie, wohin Formulardaten gesendet werden, einschließlich der Einrichtung von E-Mail-Benachrichtigungen, Integrationen mit Workflows oder Verbindungen zu externen Systemen.

Weitere Informationen finden Sie in der Dokumentation zu [Forms Experience Builder](/help/forms/experience-builder/product-overview.md).


## Aktivierung {#activation}

Um den Experience Production Agent für Ihr Unternehmen zu aktivieren, muss die Aktivierung über Adobe initiiert werden. Beginnen Sie den Prozess, indem Sie sich an wenden über:

* E-Mail: `experience-production-agent@adobe.com`
* Oder wenden Sie sich an Ihr persönliches Adobe-Accountteam.

Stellen Sie bei der Kontaktaufnahme sicher, dass Sie Ihre AEM as a Cloud Service-Organisations-ID angeben.


<!-- 
#### Import and convert {#import-and-convert}

Transform existing documents into interactive digital forms. The agent analyzes uploaded content to detect field types, preserve layouts, and enhance forms with responsive design and validation logic. Supported formats include Acroforms, XFA PDFs, flat PDFs, images (JPG, PNG), and hand-drawn form photographs.

>[!VIDEO](https://video.tv.adobe.com/v/3474042)

**Prompt examples:**

* *Convert the attached PDF file to an adaptive form*
* *Transform this scanned form image into an interactive digital form*
* *Import the employee onboarding PDF and create an editable form*
* *Convert this paper form photograph into a digital form with validation*
-->

<!-- 
### Embed an existing form to a sites page {#embed-existing-form}

The form creation skill enables seamless integration of existing forms into any sites page through natural language commands. Rather than manually locating, copying, and embedding form components, users can simply specify which form to add and where to place it. The agent handles the technical implementation, ensuring proper rendering and functionality.

>[!VIDEO](https://video.tv.adobe.com/v/PLACEHOLDER)

**Prompt examples:**

* *Embed the contact form to the homepage*
* *Add the existing customer feedback form to the support page*
* *Insert the newsletter signup form into the footer section*
* *Place the registration form on /content/site/signup*
* *Add form "contact-us-2024" to the current page*
-->

<!-- 
### Build and add a form to an existing sites page {#build-and-add-form}

The form creation skill combines form creation and site integration in a single conversational workflow. Users can describe the form they need and specify where to add it, and the agent creates the form and embeds it into the specified page automatically. This eliminates the traditional multi-step process of creating a form separately and then manually adding it to a page.

>[!VIDEO](https://video.tv.adobe.com/v/PLACEHOLDER)

**Prompt examples:**

* *Create a newsletter signup form with email field and add it to the footer*
* *Build a quick contact form with name, email, and message, then add it to /content/about-us*
* *Add a feedback form with rating stars and comment field to this page*
* *Create a simple survey form with 5 questions and embed it on the customer portal homepage*
* *Build an event registration form with name, email, and date selection, then add it to /content/events/conference-2025*
-->
