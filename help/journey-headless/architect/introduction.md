---
title: AEM Headless Content Architect Journey
description: An introduction to the powerful, and flexible, headless features of Adobe Experience Manager as a Cloud Service, and how to model content for your project.
exl-id: 62061d73-6fdb-440b-a7dd-b0d530d49186
source-git-commit: 3f6c96da3fd563b4c8db91ab1bc08ea17914a8c1
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 37%

---

# Content Modeling for Headless with AEM - An Introduction {#architect-headless-introduction}

[](overview.md)

This document helps you understand headless content delivery, how AEM supports headless, and how content is modeled for headless. Nach dem Lesen sollten Sie:

* Understand the basic concepts of headless content delivery.
* Be familiar with how AEM supports headless and content modeling.

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* ****

## Full-Stack-Inhaltsbereitstellung {#full-stack}

Seit der Einführung benutzerfreundlicher, umfangreicher Content-Management-Systeme (CMS) haben Unternehmen diese als zentralen Ort für die Verwaltung von Messaging, Branding und Kommunikation genutzt. Die Verwendung des CMS als zentraler Punkt für die Verwaltung von Erlebnissen verbessert die Effizienz, da Aufgaben in unterschiedlichen Systemen nicht mehr dupliziert werden müssen.

![Das klassische Full-Stack-CMS](/help/journey-headless/developer/assets/full-stack.png)

In a full-stack CMS, all of the functionality for manipulating content is in the CMS. Die Funktionen des Systems bilden die verschiedenen Komponenten des CMS-Stacks. Die Full-Stack-Lösung hat viele Vorteile.

* There is one system to maintain.
* Inhalte werden zentral verwaltet.
* Alle Services des Systems sind integriert.
* Die Inhaltsbearbeitung ist nahtlos.

So if new channel needs to be added or support for new types of experiences is required, one (or more) new components can be inserted into the stack and there is only one place to make changes.

![Hinzufügen eines neuen Kanals zum Stack](/help/journey-headless/developer/assets/adding-channel.png)

However the complexity of the dependencies within the stack quickly become apparent as other items in the stack need to be adjusted to accommodate the changes.

## Das „Head“ in Headless {#the-head}

Der Kopf (engl. „head“) eines Systems ist im Allgemeinen der Ausgabe-Renderer dieses Systems, in der Regel in Form einer GUI oder einer anderen grafischen Ausgabe.

Wenn wir über ein Headless-CMS sprechen, verwaltet das CMS die Inhalte und stellt sie in der Folge für die Verbraucher bereit. Indem ein Headless-CMS jedoch nur die **Inhalte** standardisiert bereitstellt, lässt es das endgültige Ausgabe-Rendering aus, sodass die **Präsentation** des Inhalts dem verbrauchenden Service überlassen bleibt.

![Headless-CMS](/help/journey-headless/developer/assets/headless-cms.png)

Die verbrauchenden Services – seien es AR-Erlebnisse, ein Webshop, mobile Erlebnisse, Progressive Web Apps (PWAs) usw. – nehmen Inhalte aus dem Headless-CMS auf und stellen ihr eigenes Rendering bereit. Sie sorgen für die Bereitstellung eigener Köpfe für Ihre Inhalte.

Das Auslassen des Kopfes vereinfacht das CMS, indem es die Komplexität beseitigt. Dadurch wird auch die Verantwortung für das Rendering der Inhalte auf die Services verlagert, die den Inhalt tatsächlich benötigen und oft besser für dieses Rendering geeignet sind.

## Inhaltsmodellierung {#content-modeling}

Content Modeling (also known as data modeling) is your specialty, so what needs to be considered when modeling for headless?

For the headless applications to be able to access your content, and do something with it, the content really needs to have a predefined structure. **

**** ****

### Accessing the Content {#access-content}

This is more of a development detail - but it might interest you, just to complete the story.

Once you&#39;ve created the Content Fragment Models, and your authors have used them to generate the content, the headless applications will need to access this content.

Adobe Experience Manager (AEM) as a Cloud Service, can selectively access your Content Fragments using the AEM GraphQL API, to return only the content that is needed. **

This means your project can realize headless delivery of structured content for use in your applications.

## Wie geht es weiter {#whats-next}

[](basics.md)

## Zusätzliche Ressourcen {#additional-resources}

* AEM Headless-Entwickler-Tour
   * [Weitere Infos zur CMS-Headless-Entwicklung](/help/journey-headless/developer/learn-about.md)
   * [Learn how to Model Your Content](/help/journey-headless/developer/model-your-content.md)
