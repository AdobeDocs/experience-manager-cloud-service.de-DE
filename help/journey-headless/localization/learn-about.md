---
title: Erfahren Sie mehr über Headless Content und wie Sie in AEM lokalisieren können.
description: Erfahren Sie mehr über Headless-Konzepte, AEM und die Theorie AEM Lokalisierung.
source-git-commit: 22ca7c01bfddb407c119de7d9a4d105941772664
workflow-type: tm+mt
source-wordcount: '655'
ht-degree: 40%

---

# Erfahren Sie mehr über Headless Content und wie Sie in AEM lokalisieren können. {#learn-about}

Erfahren Sie mehr über Headless-Konzepte, AEM und die Theorie AEM Lokalisierung.

## Zielsetzung {#objective}

Dieses Dokument hilft Ihnen, die Bereitstellung Headless Content zu verstehen, wie AEM Headless unterstützen und wie solche Inhalte lokalisiert werden können. Nach dem Lesen sollten Sie:

* Machen Sie sich mit den grundlegenden Konzepten der Headless Content-Bereitstellung vertraut.
* Machen Sie sich damit vertraut, wie AEM Headless und Lokalisierung unterstützt.

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

Die Komplexität der Abhängigkeiten innerhalb des Stapels wird schnell sichtbar, da andere Elemente im Stapel angepasst werden müssen, um die Änderungen zu berücksichtigen.

## Das Head in Headless {#the-head}

Der Kopf (engl. Head) eines Systems ist im Allgemeinen der Ausgabe-Renderer dieses Systems, in der Regel in Form einer GUI oder einer anderen grafischen Ausgabe.

Wenn wir über ein Headless-CMS sprechen, verwaltet das CMS die Inhalte und stellt sie dann an die Verbraucher bereit. Indem ein Headless-CMS jedoch nur **Inhalte** standardisiert bereitstellt, lässt es das endgültige Ausgabe-Rendering aus, sodass die **Präsentation** des Inhalts dem verbrauchenden Service überlassen bleibt.

![Headless-CMS](/help/journey-headless/developer/assets/headless-cms.png)

Die verbrauchenden Services, seien es AR-Erlebnisse, ein Webshop, mobile Erlebnisse, progressive Web-Apps (PWA) usw. nehmen Inhalte aus dem Headless-CMS auf und leisten ihr eigenes Rendering. Sie kümmern sich darum, Ihren Inhalt mit ihren eigenen Köpfen bereitzustellen.

Das Auslassen des Kopfes vereinfacht das CMS, indem es die Komplexität beseitigt. Dadurch wird auch die Verantwortung für das Rendering der Inhalte auf die Services verlagert, die die Inhalte tatsächlich benötigen und oft besser für dieses Rendering geeignet sind.

## Lokalisieren von Headless Content in AEM {#localizing-in-aem}

Zusätzlich zu den robusten Tools zum Erstellen, Verwalten und Bereitstellen herkömmlicher Webseiten im Vollstapelmodus bietet AEM auch die Möglichkeit, eigenständige Inhaltsauswahlen zu erstellen und diese Headless-Legs bereitzustellen.

Die Leistungsfähigkeit von AEM ermöglicht es, Inhalte entweder Headless, Full Stack oder in beiden Modellen gleichzeitig bereitzustellen. Für Lokalisierungsexperten können die gleichen Lokalisierungs-Tools auf beide Inhaltstypen angewendet werden, sodass Sie bei der Übersetzung Ihrer Inhalte einen einheitlichen Ansatz verfolgen können.

## Wie geht es weiter {#what-is-next}

Vielen Dank für den Einstieg in Ihre AEM Headless-Lokalisierung-Journey! Nachdem Sie dieses Dokument gelesen haben, sollten Sie:

* Machen Sie sich mit den grundlegenden Konzepten der Headless Content-Bereitstellung vertraut.
* Machen Sie sich damit vertraut, wie AEM Headless und Lokalisierung unterstützt.

Machen Sie sich mit diesem Wissen vertraut und setzen Sie Ihre AEM Headless-Lokalisierungs-Journey fort, indem Sie sich das Dokument [Lesen Sie zunächst AEM Headless-Lokalisierung](getting-started.md) ansehen. Dort erhalten Sie einen Überblick darüber, wie AEM Headless-Content verwaltet und die Lokalisierungs-Tools kennenlernen kann.

## Zusätzliche Ressourcen {#additional-resources}

Es wird zwar empfohlen, zum nächsten Teil der Headless-Lokalisierungs-Journey zu wechseln, indem Sie sich das Dokument [Erste Schritte mit AEM Headless-Lokalisierung ansehen.](getting-started.md) Im Folgenden finden Sie einige zusätzliche optionale Ressourcen, die einige der in diesem Dokument erwähnten Konzepte vertiefen. Sie müssen jedoch nicht mit der Headless-Journey weitermachen.

* [MSM und Übersetzung](/help/sites-cloud/administering/msm-and-translation.md)  - Die Details AEM Multi-Site-Managers und wie er mit seinen Übersetzungs-Tools funktioniert
