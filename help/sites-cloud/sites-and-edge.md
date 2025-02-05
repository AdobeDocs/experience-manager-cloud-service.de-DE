---
title: AEM Sites und Edge Delivery Services
description: Erfahren Sie, wie Edge Delivery Services die Authoring- und Publishing-Möglichkeiten für AEM Sites erweitern, um die Inhaltserstellung zu beschleunigen und Sites mit optimaler Leistung bereitzustellen.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: 7747d6f7-18e4-4713-baea-bcfa94f54934
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '618'
ht-degree: 97%

---

# AEM Sites und Edge Delivery Services {#sites-and-edge}

Erfahren Sie, wie Edge Delivery Services die Authoring- und Publishing-Möglichkeiten für AEM Sites erweitern, um die Inhaltserstellung zu beschleunigen und Sites mit optimaler Leistung bereitzustellen.

## Überblick {#overview}

Zusätzlich zu all den [Funktionen und Leistungsmerkmalen, die AEM Sites as a Cloud Service](/help/sites-cloud/sites-cloud-changes.md) als Teil der Cloud-nativen AEM as a Cloud Service-Plattform bietet, erhalten Sie mit Edge Delivery Services weitere Authoring- und Publishing-Möglichkeiten, um die Erstellung von Inhalten zu beschleunigen und Sites mit optimaler Leistung bereitzustellen.

## Was sind Edge Delivery Services? {#what-is-edge}

Edge Delivery Services liefern außergewöhnliche, wirkungsvolle Erlebnisse, die Interaktionen und Konversionen fördern und schnell erstellt und entwickelt werden können. Edge Delivery Services ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autorinnen und Autoren schnell aktualisieren und veröffentlichen können und neue Sites schnell live geschaltet werden können. Weitere Informationen zu Edge Delivery Services finden Sie im Dokument [Übersicht über Edge Delivery Services ](/help/edge/overview.md).

Wenn Sie Edge Delivery Services zusammen mit AEM Sites as a Cloud Service einsetzen, können Ihre Projekte von Folgendem profitieren:

* [einem neuen Entwicklererlebnis](#developer-experience)
* [einer neuen Veröffentlichungsebene](#publish-tier)
* [zusätzlichen Authoring-Optionen](#authoring-options)

## Ein neues Entwicklererlebnis {#developer-experience}

Eine Kernphilosophie von Edge Delivery Services heißt *Geschwindigkeit*. Dies beginnt mit dem Entwicklererlebnis. Ihre Entwicklerinnen und Entwickler:

* sind mit den Git-Grundlagen vertraut und
* kennen die HTML-, CSS- und JavaScript-Grundlagen?

Dann können sie es in weniger als 30 Minuten schaffen, ein eigenes Projekt und eigene Komponenten für Edge Delivery Services aufzusetzen. Klonen Sie zunächst unser Vorlagenprojekt auf GitHub und übertragen Sie dann einfach Ihre Änderungen. Ihre Anpassungen sind sofort online!

Weitere Informationen zur Entwicklung für Edge Delivery Services finden Sie im Dokument [Erste Schritte – Entwickler-Tutorial](https://www.aem.live/developer/tutorial).

## Eine neue Veröffentlichungsebene {#publish-tier}

Nicht nur verkürzt sich die Entwicklungszeit erheblich, Edge Delivery Services sorgen dafür, dass Websites im Handumdrehen verfügbar sind.

## Zusätzliche Authoring-Optionen {#authoring-options}

Edge Delivery Services beschleunigen darüber hinaus die Inhaltserstellung, denn sie stellen neue Authoring-Optionen zur Verfügung.

### Der universelle Editor {#universal-editor}

Der universelle Editor bietet ein nahtloses Authoring-Erlebnis nach dem WYSIWYG(What You See Is What You Get)-Prinzip, mit dem Sie beliebige Inhalte erstellen können.

Weitere Informationen zur Inhaltserstellung mit dem universellen Editor finden Sie im Dokument [WYSIWYG-Inhaltserstellung für Edge Delivery Services](/help/edge/wysiwyg-authoring/authoring.md).

### Dokumentenbasiertes Authoring {#document-authoring}

Dokumentbasiertes Authoring ermöglicht es, dass wirklich alle ohne jedwede Schulung Inhalte erstellen können. Wie? Durch Nutzung der allseits vertrauten Tools Word und Google Docs. Dank dieser einfachen Tools können Sie mit Edge Delivery Services eine Änderung sofort in ein Word-Dokument übertragen und damit den Inhalt auf Ihrer Live-Site aktualisieren.

Weitere Informationen zur Verwendung von dokumentbasiertem Authoring finden Sie im Dokument [Verfassen und Veröffentlichen von Inhalten](https://www.aem.live/docs/authoring).

## Ist Edge das Richtige für Sie? {#decision}

Adobe hat festgestellt, dass seine Kundschaft und ihre Stakeholder von Edge Delivery Services über Projekte aller Größenordnungen hinweg massiv profitieren. Aus diesem Grund empfiehlt Adobe Edge Delivery Services als Ausgangspunkt für jedes neue Projekt.

Es ist auch möglich, eine Teilmenge von Sites oder Seiten in Edge Delivery bereitzustellen, während der Rest im aktuellen Stapel verbleibt. Dies wird immer dann empfohlen, wenn die Leistung, der organische Traffic, Kundeninteraktionen, die Entwicklungsgeschwindigkeit oder die Content Velocity verbessert werden müssen.

Wenden Sie sich an Ihren Adobe-Support, wenn Sie sich nicht sicher sind, ob Edge Delivery für Sie geeignet ist.

### Und was ist mit Edge Delivery und Headless? (#headless)

Edge Delivery ist ein leistungsorientierter Head, der vom Backend entkoppelt ist. Wenn Sie über einen benutzerdefinierten Head verfügen, z. B. eine React-SPA, wird von Adobe das AEM Headless-Integrationsmuster empfohlen. Weitere Informationen finden Sie in der [AEM Headless-Dokumentation](/help/headless/introduction.md).

Im Allgemeinen empfiehlt Adobe jedoch, Edge Delivery als Standard-Head zu verwenden, um von der damit einhergehenden Geschwindigkeit und Leistung zu profitieren und den Headless-Teil Ihres Projekts (in der Regel die Geschäftsanwendung) über einen Headless-Ansatz (z. B. React oder SPA) zu integrieren.
