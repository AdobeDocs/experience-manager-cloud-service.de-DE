---
title: Formularerstellungsauftrag
description: Erfahren Sie mehr über den Auftrag zum Erstellen von Formularen durch den Brand Experience Agent und wie Sie Formulare von Grund auf in natürlicher Sprache erstellen können.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Architect, Developer
exl-id: 24ad5f36-405b-4ea2-9819-de6aea856a7a
source-git-commit: 71e3770a7a26b8d3144717513f3ec1c997b3b435
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---


# Formularerstellungsauftrag {#form-creation-job}

Der Vorgang der Formularerstellung ist eine Funktion des [Brand Experience Agent](/help/ai-in-aem/agents/brand-experience/overview.md) die entwickelt wurde, um Formulare mithilfe von Eingabeaufforderungen in natürlicher Sprache zu entwickeln. Dieser Auftrag generiert automatisch die entsprechende Formularstruktur und die entsprechenden Feldtypen. Der Auftrag wird über den KI-Assistenten angezeigt.

Zu den wichtigsten Vorteilen der Formularerstellung gehören:

* **Beschleunigte Formularentwicklung**: Erstellen Sie Formulare schnell mit einfachen Befehlen in natürlicher Sprache, wodurch das Erlernen herkömmlicher Produktschnittstellen überflüssig wird.
* **Konsistente und markeninterne Erlebnisse**: Erstellen Sie Formulare, die dem Branding, den Vorlagen und Stilrichtlinien Ihres Unternehmens entsprechen, indem Sie genehmigte Vorlagen und Stile verwenden.
* **Geringere technische Hürde**: Ermöglichen Sie es Geschäftsbenutzern, Formulare einfach zu erstellen, ohne fortgeschrittene technische oder fundierte Produktkenntnisse zu benötigen.

## Funktionen {#capabilities}

* **Erstellen eines neuen Formulars mit einer Textaufforderung**: Sie können ein Formular erstellen, indem Sie Ihre Anforderungen in einfacher Sprache übermitteln. Die Qualifikation generiert automatisch die entsprechende Formularstruktur, Feldtypen und markeninterne Erlebnisse basierend auf Ihrer Beschreibung in natürlicher Sprache und der angegebenen Vorlage. Diese Funktion beschleunigt die Formularerstellung und stellt gleichzeitig sicher, dass die Marken- und Compliance-Standards eingehalten werden.

* **Importieren eines PDF-Dokuments und Konvertieren in ein Formular**: Sie können vorhandene PDF-Dokumente importieren und in Formulare umwandeln. Die Fähigkeit analysiert hochgeladene Inhalte, um Feldtypen zu erkennen, Layouts beizubehalten und Formulare mit responsiver Design- und Validierungslogik zu verbessern, während sichergestellt wird, dass Marken- und Compliance-Standards eingehalten werden.

Wenn Sie eine dieser Funktionen verwenden, werden Sie aufgefordert, den Typ des zu erstellenden Formulars auszuwählen. Geben Sie entweder eine auf Kernkomponenten basierende Vorlage für adaptive Formulare oder eine auf Edge Delivery Services basierende Vorlage für adaptive Formulare an und geben Sie Ihren bevorzugten Pfad zum Speichern des Formulars an. Wenn Sie ein Formular erstellen, das auf Edge Delivery Services basiert, können Sie auch die GitHub-URL Ihres Repositorys angeben.


### Eingabeaufforderungen {#sample-prompts}

* *Erstellen Sie ein Formular für die Feedback-Sammlung mit den Feldern Name, E-Mail und Nachricht*
* *Erstellen Sie ein Formular für Kunden-Feedback mit Produktbewertung (1-5 Sterne), Kommentarfeld und optionaler E-Mail-Adresse*
* *Erstellen Sie ein Kontaktformular mit den Feldern „Name“, „E-Mail“, „Betreff“ und „Nachricht“*
* *Erstellen Sie ein Registrierungsformular mit persönlichen Informationen, Kontovoreinstellungen und Bedingungen zur Annahme*
* *Erstellen Sie ein Kreditkartenantragsformular, indem Sie die PDF-Datei importieren, die unter`https://[aem-author-url]/path/to/pdf/file`* verfügbar ist.
* *Erstellen Sie ein Feedback-Formular mit dem Textbaustein unter`https://github.com/wkndforms/wesecure`*

## Verfeinern des Formulars {#refine-with-forms-experience-builder}

Nachdem Sie Ihre anfängliche Formularstruktur mit dem KI-Assistenten erstellt haben, können Sie den Forms Experience Builder verwenden, um:

* **Formulare aktualisieren**: Felder hinzufügen oder ändern, Feldtypen anpassen und den Stil nach Bedarf über den visuellen Editor aktualisieren.

* **Layout aktualisieren**: Neuanordnen von Abschnitten, Gruppen oder Feldern, Anpassen der Abstände und Ändern der visuellen Hierarchie, um die Benutzerfreundlichkeit zu verbessern und sicherzustellen, dass das Formular für Ihre Zielgruppe klar und intuitiv ist.

* **Geschäftslogik hinzufügen**: Erstellen Sie eine bedingte Logik, blenden Sie Regeln ein/aus, geben Sie Feldabhängigkeiten ein und definieren Sie Validierungsregeln.

* **Übermittlung konfigurieren** Konfigurieren Sie, wohin Formulardaten gesendet werden, einschließlich der Einrichtung von E-Mail-Benachrichtigungen, Integrationen mit Workflows oder Verbindungen zu externen Systemen.

Weitere Informationen finden Sie in der Dokumentation zu [Forms Experience Builder.](/help/forms/experience-builder/product-overview.md)


## Aktivierung {#activation}

Um den Formularerstellungsauftrag für Ihr Unternehmen zu aktivieren, muss die Aktivierung über Adobe initiiert werden. Beginnen Sie den Prozess, indem Sie sich an wenden über:

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
