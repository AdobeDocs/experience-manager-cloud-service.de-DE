---
title: Inhaltsmodellierung für AEM als Headless-CMS – eine Einführung
description: Eine Einführung in die Verwendung der Funktionen von Adobe Experience Manager as a Cloud Service als Headless-CMS zum Modellieren von Inhalten für Ihr Projekt.
exl-id: 62061d73-6fdb-440b-a7dd-b0d530d49186
source-git-commit: d280bcfa7e4fe297952309a94bc0229d08fd5f9c
workflow-type: tm+mt
source-wordcount: '722'
ht-degree: 92%

---

# Inhaltsmodellierung für AEM als Headless-CMS – eine Einführung {#architect-headless-introduction}

In diesem Teil der [AEM Headless-Inhaltsarchitekten-Tour](overview.md) lernen Sie die (grundlegenden) Konzepte und die Terminologie kennen, die notwendig sind, um das Modellieren von Inhalten bei der Verwendung von Adobe Experience Manager (AEM) as a Cloud Service als Headless-CMS zu verstehen.

Dieses Dokument hilft Ihnen dabei, die Bereitstellung von Headless-Inhalten zu verstehen, und wie AEM Headless unterstützt und wie Inhalte für Headless modelliert werden. Nach dem Lesen sollten Sie:

* die grundlegenden Konzepte der Headless-Bereitstellung von Inhalten verstehen,
* damit vertraut sein, wie AEM Headless und Inhaltsmodellierung unterstützt.

## Ziel {#objective}

* **Zielgruppe**: Anfänger
* **Ziel**: Einführung der Konzepte und Terminologie für die Headless-Inhaltsmodellierung.

## Full-Stack-Inhaltsbereitstellung {#full-stack}

Seit der Einführung benutzerfreundlicher, umfangreicher Content-Management-Systeme (CMS) haben Unternehmen diese als zentralen Ort für die Verwaltung von Messaging, Branding und Kommunikation genutzt. Die Verwendung des CMS als zentraler Punkt für die Verwaltung von Erlebnissen verbessert die Effizienz, da Aufgaben in unterschiedlichen Systemen nicht mehr dupliziert werden müssen.

![Das klassische Full-Stack-CMS](/help/journey-headless/developer/assets/full-stack.png)

In einem Full-Stack-CMS befindet sich die gesamte Funktionalität zum Bearbeiten Ihrer Inhalte im CMS. Die Funktionen des Systems bilden die verschiedenen Komponenten des CMS-Stacks. Die Full-Stack-Lösung hat viele Vorteile.

* Es gibt ein System, das gepflegt werden muss.
* Inhalte werden zentral verwaltet.
* Alle Services des Systems sind integriert.
* Die Inhaltsbearbeitung ist nahtlos.

Wenn also ein neuer Kanal hinzugefügt werden muss oder Unterstützung für neue Erlebnistypen erforderlich ist, können eine (oder mehrere) neue Komponenten in den Stack eingefügt werden und es gibt nur einen Ort, an dem Änderungen vorgenommen werden können.

![Hinzufügen eines neuen Kanals zum Stack](/help/journey-headless/developer/assets/adding-channel.png)

Die Komplexität der Abhängigkeiten innerhalb des Stacks wird jedoch schnell deutlich, da andere Elemente im Stack möglicherweise angepasst werden müssen, um die Änderungen zu berücksichtigen.

## Das „Head“ in Headless {#the-head}

Der Kopf (engl. „head“) eines Systems ist im Allgemeinen der Ausgabe-Renderer dieses Systems, in der Regel in Form einer GUI oder einer anderen grafischen Ausgabe.

Wenn wir über ein Headless-CMS sprechen, verwaltet das CMS die Inhalte und stellt sie in der Folge für die Verbraucher bereit. Indem ein Headless-CMS jedoch nur die **Inhalte** standardisiert bereitstellt, lässt es das endgültige Ausgabe-Rendering aus, sodass die **Präsentation** des Inhalts dem verbrauchenden Service überlassen bleibt.

![Headless-CMS](/help/journey-headless/developer/assets/headless-cms.png)

Die verbrauchenden Services – seien es AR-Erlebnisse, ein Webshop, mobile Erlebnisse, Progressive Web Apps (PWAs) usw. – nehmen Inhalte aus dem Headless-CMS auf und stellen ihr eigenes Rendering bereit. Sie sorgen für die Bereitstellung eigener Köpfe für Ihre Inhalte.

Das Auslassen des Kopfes vereinfacht das CMS, indem es die Komplexität beseitigt. Dadurch wird auch die Verantwortung für das Rendering der Inhalte auf die Services verlagert, die den Inhalt tatsächlich benötigen und oft besser für dieses Rendering geeignet sind.

## Inhaltsmodellierung {#content-modeling}

Inhaltsmodellierung (auch als Datenmodellierung bezeichnet) ist Ihre Spezialität. Was muss daher bei der Modellierung für Headless berücksichtigt werden?

Damit die Headless-Anwendungen auf Ihre Inhalte zugreifen und etwas damit anfangen können, müssen die Inhalte wirklich über eine vordefinierte Struktur verfügen. Es wäre möglich, Ihre Inhalte frei zu gestalten, aber das würde das Leben für die Anwendungen *sehr* kompliziert machen.

Für AEM führen Sie als Inhaltsarchitekt die Inhaltsmodellierung durch, um eine Reihe von **Inhaltsfragmentmodellen** zu entwerfen. Diese definieren die Struktur, die verwendet wird, wenn Ihre Inhaltsautoren die **Inhaltsfragmente** erstellen, die die Inhalte enthalten.

### Zugreifen auf die Inhalte {#access-content}

Das ist eher ein Entwicklungsdetail – aber es könnte Sie interessieren, nur um die Geschichte zu vervollständigen.

Nachdem Sie die Inhaltsfragmentmodelle erstellt haben und Ihre Autoren sie zum Generieren des Inhalts verwendet haben, müssen die Headless-Anwendungen auf diesen Inhalt zugreifen.

Mit Adobe Experience Manager (AEM) as a Cloud Service können Sie mithilfe der AEM-GraphQL-API selektiv auf Ihre Inhaltsfragmente zugreifen, um nur die benötigten Inhalte zurückzugeben. Mithilfe der API kann ein Entwickler Abfragen formulieren, die bestimmte Inhalte auswählen. Dieser Auswahlprozess basiert auf *Ihren* Inhaltsfragmentmodellen.

Dies bedeutet, dass Sie die Headless-Bereitstellung von strukturierten Inhalten zur Verwendung in Ihren Programmen umsetzen können.

## Wie geht es weiter {#whats-next}

Jetzt, da Sie die Konzepte und Terminologie gelernt haben, lautet der nächste Schritt [Kennenlernen der Grundlagen der Modellierung mit Inhaltsfragmentmodellen](basics.md).

## Zusätzliche Ressourcen {#additional-resources}

* AEM Headless-Entwickler-Tour
   * [Grundlegendes zur CMS-Headless-Entwicklung](/help/journey-headless/developer/learn-about.md)
   * [Hier erfahren Sie, wie Sie Ihre Inhalte modellieren](/help/journey-headless/developer/model-your-content.md)

<!--
* [Introduction to AEM as a Headless CMS](/help/headless/introduction.md)
* [AEM Developer Portal](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
* [Tutorials for Headless in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html)
-->
