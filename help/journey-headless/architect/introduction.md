---
title: Journey AEM Headless Content Architect
description: Eine Einführung in die leistungsstarken und flexiblen, Headless-Funktionen von Adobe Experience Manager as a Cloud Service und die Modellierung von Inhalten für Ihr Projekt.
index: true
hide: false
hidefromtoc: false
source-git-commit: 6605349c698325d432479fac0253a6fd53d7f175
workflow-type: tm+mt
source-wordcount: '714'
ht-degree: 37%

---


# Inhaltsmodellierung für Headless mit AEM - Einführung {#architect-headless-introduction}

In diesem Teil des Journey [AEM Headless Content Architect](overview.md) erfahren Sie mehr über die (grundlegenden) Konzepte und Terminologie, die zum Verständnis der Inhaltsmodellierung für die Headless-Content-Bereitstellung mit Adobe Experience Manager (AEM) als Cloud Service erforderlich sind.

Dieses Dokument hilft Ihnen dabei, die Bereitstellung Headless Content zu verstehen, wie AEM Headless unterstützen und wie Inhalte für Headless modelliert werden. Nach dem Lesen sollten Sie:

* Machen Sie sich mit den grundlegenden Konzepten der Headless Content-Bereitstellung vertraut.
* Machen Sie sich damit vertraut, wie AEM Headless- und Content-Modellierung unterstützt.

## Ziele {#objective}

* **Zielgruppe**: Anfänger
* **Zielsetzung**: Einführung der Konzepte und Terminologie für die Headless Content-Modellierung.

## Full-Stack-Inhaltsbereitstellung {#full-stack}

Seit der Einführung benutzerfreundlicher, umfangreicher Content-Management-Systeme (CMS) haben Unternehmen diese als zentralen Ort für die Verwaltung von Messaging, Branding und Kommunikation genutzt. Die Verwendung des CMS als zentraler Punkt für die Verwaltung von Erlebnissen verbessert die Effizienz, da Aufgaben in unterschiedlichen Systemen nicht mehr dupliziert werden müssen.

![Das klassische Full-Stack-CMS](/help/journey-headless/developer/assets/full-stack.png)

In einem Full-Stack-CMS befindet sich die gesamte Funktionalität zum Bearbeiten von Inhalten im CMS. Die Funktionen des Systems bilden die verschiedenen Komponenten des CMS-Stacks. Die Full-Stack-Lösung hat viele Vorteile.

* Es gibt ein System, das gepflegt werden muss.
* Inhalte werden zentral verwaltet.
* Alle Services des Systems sind integriert.
* Die Inhaltsbearbeitung ist nahtlos.

Wenn also ein neuer Kanal hinzugefügt werden muss oder Unterstützung für neue Erlebnistypen erforderlich ist, können eine (oder mehrere) neue Komponenten in den Stapel eingefügt werden und es gibt nur einen Ort, an dem Änderungen vorgenommen werden können.

![Hinzufügen eines neuen Kanals zum Stack](/help/journey-headless/developer/assets/adding-channel.png)

Die Komplexität der Abhängigkeiten innerhalb des Stapels wird jedoch schnell sichtbar, da andere Elemente im Stapel angepasst werden müssen, um die Änderungen zu berücksichtigen.

## Das Head in Headless {#the-head}

Der Kopf (engl. „head“) eines Systems ist im Allgemeinen der Ausgabe-Renderer dieses Systems, in der Regel in Form einer GUI oder einer anderen grafischen Ausgabe.

Wenn wir über ein Headless-CMS sprechen, verwaltet das CMS die Inhalte und stellt sie in der Folge für die Verbraucher bereit. Indem ein Headless-CMS jedoch nur die **Inhalte** standardisiert bereitstellt, lässt es das endgültige Ausgabe-Rendering aus, sodass die **Präsentation** des Inhalts dem verbrauchenden Service überlassen bleibt.

![Headless-CMS](/help/journey-headless/developer/assets/headless-cms.png)

Die verbrauchenden Services – seien es AR-Erlebnisse, ein Webshop, mobile Erlebnisse, Progressive Web Apps (PWAs) usw. – nehmen Inhalte aus dem Headless-CMS auf und stellen ihr eigenes Rendering bereit. Sie sorgen für die Bereitstellung eigener Köpfe für Ihre Inhalte.

Das Auslassen des Kopfes vereinfacht das CMS, indem es die Komplexität beseitigt. Dadurch wird auch die Verantwortung für das Rendering der Inhalte auf die Services verlagert, die den Inhalt tatsächlich benötigen und oft besser für dieses Rendering geeignet sind.

## Inhaltsmodellierung {#content-modeling}

Inhaltsmodellierung (auch als Datenmodellierung bezeichnet) ist Ihre Spezialität. Was muss daher bei der Modellierung für Headless berücksichtigt werden?

Damit die Headless-Anwendungen auf Ihre Inhalte zugreifen und etwas damit anfangen können, muss der Inhalt wirklich über eine vordefinierte Struktur verfügen. Es wäre möglich, Ihren Inhalt als frei zu gestalten, aber es würde das Leben *sehr* für die Anwendungen kompliziert machen.

Für AEM führen Sie als Inhaltsarchitektin die Inhaltsmodellierung durch, um einen Bereich von **Inhaltsfragmentmodellen** zu entwerfen. Diese definieren die Struktur, die verwendet wird, wenn Ihre Inhaltsautoren die **Inhaltsfragmente** erstellen, die den Inhalt enthalten.

### Zugreifen auf den Inhalt {#access-content}

Das ist eher ein Entwicklungsdetails - aber es könnte Sie interessieren, nur um die Geschichte zu vervollständigen.

Nachdem Sie die Inhaltsfragmentmodelle erstellt haben und Ihre Autoren sie zur Erstellung des Inhalts verwendet haben, müssen die Headless-Anwendungen auf diesen Inhalt zugreifen.

Adobe Experience Manager (AEM) als Cloud Service kann mithilfe der AEM GraphQL-API selektiv auf Ihre Inhaltsfragmente zugreifen, um nur die benötigten Inhalte zurückzugeben. Mithilfe der API kann ein Entwickler Abfragen formulieren, die bestimmte Inhalte auswählen. Dieser Auswahlprozess basiert auf *Ihren* Inhaltsfragmentmodellen.

Das bedeutet, dass Ihr Projekt die Headless-Bereitstellung strukturierter Inhalte für Ihre Anwendungen realisieren kann.

## Wie geht es weiter {#whats-next}

Nachdem Sie die Konzepte und Terminologie gelernt haben, ist der nächste Schritt [Lernen Sie die Grundlagen der Modellierung mit Inhaltsfragmentmodellen](basics.md) kennen.

## Zusätzliche Ressourcen {#additional-resources}

* AEM Headless-Entwickler-Tour
   * [Weitere Infos zur CMS-Headless-Entwicklung](/help/journey-headless/developer/learn-about.md)
   * [Erfahren Sie, wie Sie Ihren Inhalt modellieren](/help/journey-headless/developer/model-your-content.md)
