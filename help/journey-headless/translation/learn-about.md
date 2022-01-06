---
title: Learn about headless content and how to translate it in AEM
description: Learn headless concepts, how they map to AEM, and the theory of AEM translation.
exl-id: 72bb6646-e573-4576-8d17-49787d8c8c7f
source-git-commit: 3f6c96da3fd563b4c8db91ab1bc08ea17914a8c1
workflow-type: tm+mt
source-wordcount: '727'
ht-degree: 32%

---

# Learn about headless content and how to translate it in AEM {#learn-about}

Learn headless concepts, how they map to AEM, and the theory of AEM translation.

## Ziel {#objective}

This document helps you understand headless content delivery, how AEM supports headless, and how such content can be translated. Nach dem Lesen sollten Sie:

* Understand the basic concepts of headless content delivery.
* Be familiar with how AEM supports headless and translation.

## Full-Stack-Inhaltsbereitstellung {#full-stack}

Seit der Einführung benutzerfreundlicher, umfangreicher Content-Management-Systeme (CMS) haben Unternehmen diese als zentralen Ort für die Verwaltung von Messaging, Branding und Kommunikation genutzt. Die Verwendung des CMS als zentraler Punkt für die Verwaltung von Erlebnissen verbessert die Effizienz, da Aufgaben in unterschiedlichen Systemen nicht mehr dupliziert werden müssen.

![Das klassische Full-Stack-CMS](/help/journey-headless/developer/assets/full-stack.png)

In a full-stack CMS, all of the functionality for manipulating content is in the CMS. Die Funktionen des Systems bilden die verschiedenen Komponenten des CMS-Stacks. Die Full-Stack-Lösung hat viele Vorteile.

* There is one system to maintain.
* Inhalte werden zentral verwaltet.
* Alle Services des Systems sind integriert.
* Die Inhaltsbearbeitung ist nahtlos.

So if new channel must be added or support for new types of experiences is required, one (or more) new components can be inserted into the stack and there is only one place to make changes.

![Hinzufügen eines neuen Kanals zum Stack](/help/journey-headless/developer/assets/adding-channel.png)

However the complexity of the dependencies within the stack quickly becomes apparent as other items in the stack need to be adjusted to accommodate the changes.

## Das „Head“ in Headless {#the-head}

Der Kopf (engl. „head“) eines Systems ist im Allgemeinen der Ausgabe-Renderer dieses Systems, in der Regel in Form einer GUI oder einer anderen grafischen Ausgabe.

Wenn wir über ein Headless-CMS sprechen, verwaltet das CMS die Inhalte und stellt sie in der Folge für die Verbraucher bereit. Indem ein Headless-CMS jedoch nur die **Inhalte** standardisiert bereitstellt, lässt es das endgültige Ausgabe-Rendering aus, sodass die **Präsentation** des Inhalts dem verbrauchenden Service überlassen bleibt.

![Headless-CMS](/help/journey-headless/developer/assets/headless-cms.png)

The consuming services, be they AR experiences, a web shop, mobile experiences, progressive web apps (PWAs), etc., take in content from the headless CMS and provide their own rendering. Sie sorgen für die Bereitstellung eigener Köpfe für Ihre Inhalte.

Das Auslassen des Kopfes vereinfacht das CMS, indem es die Komplexität beseitigt. Dadurch wird auch die Verantwortung für das Rendering der Inhalte auf die Services verlagert, die den Inhalt tatsächlich benötigen und oft besser für dieses Rendering geeignet sind.

## Translating Headless Content in AEM {#translating-in-aem}

In addition to offering robust tools to create, manage, and deliver traditional webpages in the full-stack fashion, AEM also offers the ability to author self-contained selections of content and serve them headlessly.

The power of AEM allows it to deliver content either headlessly, full-stack, or in both models at the same time. For the translation specialist, the same set of translation tools can be applied to both types of content, giving you a unified approach for translating your content.

Further in the journey you will learn the details about how AEM translates content, but at a high level, the concept is simple:

1. Define a connection to a translation service by configuring the translation integration framework.
1. Define which content should be translated using translation rules.
1. Create a translation project to harvest the content, send it to the translation service, and receive the results.
1. Review and publish the translated content.

## Wie geht es weiter {#what-is-next}

Thanks for getting started on your AEM headless translation journey! Nachdem Sie dieses Dokument gelesen haben, sollten Sie:

* Understand the basic concepts of headless content delivery.
* Be familiar with how AEM supports headless and translation.

[](getting-started.md)

## Zusätzliche Ressourcen {#additional-resources}

[](getting-started.md)

* [](/help/sites-cloud/administering/msm-and-translation.md)
