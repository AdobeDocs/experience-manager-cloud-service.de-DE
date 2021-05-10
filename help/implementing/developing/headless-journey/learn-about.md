---
title: Weitere Informationen zur CMS-Headless-Entwicklung
description: In diesem Teil der AEM Headless Developer Journey erfahren Sie mehr über die kostenlose Technologie und warum Sie sie verwenden würden.
hide: true
hidefromtoc: true
index: false
exl-id: d96f02b3-d650-4b9e-addf-409d31c80372
translation-type: tm+mt
source-git-commit: 7df3620e6f58336de2ac29dd496a888b17606d7f
workflow-type: tm+mt
source-wordcount: '1651'
ht-degree: 0%

---

# Weitere Informationen zu CMS Headless Development {#learn-about}

>[!CAUTION]
>
>ARBEITEN IN FORTSCHRITTEN - Die Schaffung dieses Dokuments ist im Gange und sollte nicht als vollständig oder endgültig betrachtet werden und auch nicht für Produktionszwecke verwendet werden.

In diesem Teil der [AEM Headless Developer-Journey lernen Sie von der ](overview.md)-Technologie ohne Kopf und warum Sie sie verwenden würden.

## Vorgabe {#objective}

Dieses Dokument hilft Ihnen, den Versand von kostenlosen Inhalten zu verstehen und zu verstehen, warum er verwendet werden sollte. Nach dem Lesen sollten Sie:

* Grundlegende Konzepte und Terminologie von Versand ohne Inhalt verstehen
* Verstehen Sie, warum und wann Kopflosigkeit erforderlich ist
* Auf hoher Ebene wissen, wie Headless-Konzepte verwendet werden und wie sie miteinander verknüpft werden

## Vollstapelinhalt-Versand {#full-stack}

Seit der Einführung benutzerfreundlicher, großmaßstäblicher Content-Management-Systeme (CMSes) haben Unternehmen diese als zentralen Standort für die Verwaltung von Messaging, Markendarstellung und Kommunikationswesen genutzt. Die Verwendung des CMS als zentrales Instrument zur Verwaltung von Erlebnissen hat die Effizienz verbessert, da Aufgaben in unterschiedlichen Systemen nicht mehr Duplikat werden müssen.

![Das klassische Vollstapel-CMS](assets/full-stack.png)

In einem Vollstapel-CMS befinden sich alle Funktionen zum Bearbeiten Ihrer Inhalte im CMS. Die Funktionen des Systems bestehen aus verschiedenen Komponenten des CMS-Stapels. Die Komplettlösung bietet viele Vorteile.

* Sie haben ein System zu warten.
* Inhalte werden zentral verwaltet.
* Alle Dienste des Systems sind integriert.
* Content Authoring ist nahtlos.

Wenn Sie also einen neuen Kanal hinzufügen oder neue Erlebnistypen unterstützen möchten, können Sie eine (oder mehrere) neue Komponente in Ihren Stapel einfügen und nur eine Stelle für die Änderungen bereitstellen.

![Hinzufügen eines neuen Kanals zum Stapel](assets/adding-channel.png)

Die Komplexität der Abhängigkeiten innerhalb des Stapels wird schnell sichtbar, da Sie sehen, dass andere Elemente im Stapel möglicherweise angepasst werden müssen, um die Änderungen zu berücksichtigen.

## Beschränkungen des Vollstapel-Versands {#limits}

Der Vollstapelansatz erzeugt automatisch ein Silo, bei dem alle Erlebnisse in einem System landen. Änderungen oder Ergänzungen an einer Komponente des Silo erfordern Änderungen an anderen Komponenten, die Änderungen zeitintensiv und kostenintensiv machen können.

Dies gilt insbesondere für das Präsentationssystem, das in traditionellen Setups oft eng an das CMS gebunden ist. Jeder neue Kanal bedeutet im Allgemeinen eine Aktualisierung des Präsentationssystems, die alle anderen Kanal betreffen kann.

![Komplexität wächst, wenn Kanal zu einem Stapel hinzugefügt werden](assets/presentation-complexity.png)

Die Einschränkungen dieses natürlichen Silos können sichtbar werden, wenn Sie sich mehr Mühe geben, Änderungen über alle Komponenten Ihres Stapels hinweg zu koordinieren.

Die Benutzer erwarten Interaktionen, ganz gleich, welche Plattform oder welcher Touchpoint sie erwarten, und benötigen mehr Flexibilität bei der Bereitstellung Ihrer Erlebnisse.  Dieser Mehrkanalansatz ist der Standard digitaler Erlebnisse, und ein Vollstapelansatz kann sich unter bestimmten Umständen als unflexibel erweisen.

## Der Head in Headless {#the-head}

Der Kopf eines Systems ist in der Regel der Ausgabe-Renderer dieses Systems, normalerweise in Form einer GUI oder anderen grafischen Ausgabe.

Ein Headless-Server beispielsweise sitzt wahrscheinlich in einem Rack irgendwo in einem Serverraum und hat keinen Monitor angeschlossen. Um darauf zugreifen zu können, müssen Sie sich remote damit verbinden. In diesem Fall ist der Monitor der Kopf, da er für die Wiedergabe der Ausgabe des Servers sorgt. Als Verbraucher des Dienstes stellen Sie Ihren eigenen Kopf (den Monitor) bereit, wenn Sie eine Verbindung mit dem Dienst remote herstellen.

Wenn wir von einem kopflosen CMS sprechen, verwaltet das CMS die Inhalte und liefert sie weiterhin an die Verbraucher. Indem jedoch **content** nur in standardisierter Form bereitgestellt wird, lässt ein kopfloses CMS das endgültige Ausgabe-Rendering aus und überlässt die **Präsentation** des Inhalts dem konsumierenden Dienst.

![Headless-CMS](assets/headless-cms.png)

Die konsumierenden Dienste, ob es sich nun um AR-Erlebnisse, einen Webshop, mobile Erlebnisse, progressive Web-Apps (PWA) usw. handelt, nehmen Inhalte aus dem kopflosen CMS auf und bieten eine eigene Wiedergabe. Sie kümmern sich darum, ihre eigenen Köpfe für Ihre Inhalte bereitzustellen.

Das Auslassen des Kopfes vereinfacht das CMS, indem es Komplexität beseitigt. Auf diese Weise wird auch die Verantwortung für die Wiedergabe der Inhalte auf die Dienste verlagert, die den Inhalt tatsächlich benötigen und für diese Darstellung oft besser geeignet sind.

## Entkoppelung {#decoupling}

Ein Headless-Versand ist möglich, indem Sie eine Reihe robuster und flexibler Anwendungsprogrammierschnittstellen (APIs) verfügbar machen, auf die alle Ihre Erlebnisse zugreifen können. Die API dient als gemeinsame Sprache der Dienste und verbindet diese auf Inhaltsebene durch standardisierten Content-Versand, ermöglicht ihnen jedoch die Flexibilität, eigene Lösungen zu implementieren.

Headless ist ein Beispiel für die Entkopplung Ihres Inhalts von seiner Präsentation. Oder in einem allgemeineren Sinne, entkoppeln Sie das Front-End vom Back-End Ihres Service-Stapels. Bei einem Headless-Setup wird das Präsentationssystem (der Kopf) vom Content-Management (der Schwanz) entkoppelt. Die beiden interagieren nur über API-Aufrufe.

Diese Entkopplung bedeutet, dass jeder konsumierende Dienst (das Front-End) sein Erlebnis auf der Grundlage desselben Inhalts aufbauen kann, der über die APIs bereitgestellt wird, um die Wiederverwendung und Konsistenz von Inhalten zu gewährleisten. Verbrauchsdienste können dann ihre eigenen Präsentationssysteme implementieren, sodass der Content-Management-Stapel (das Back-End) einfach horizontal skaliert werden kann.

## Technologische Grundlagen {#technology}

Mit einem kopflosen Ansatz können Sie einen Technologiestapel erstellen, der sich schnell und einfach an zukünftige Anforderungen an digitale Erlebnisse anpassen kann.

In der Vergangenheit waren die APIs für CMS in der Regel REST-basiert. Repräsentativer Staatstransfer (REST) bietet Ressourcen als Text in statusloser Weise. Dadurch können die Ressourcen mit einem vordefinierten Satz von Vorgängen gelesen und geändert werden. REST ermöglichte eine große Interoperabilität zwischen den Diensten im Internet, indem sichergestellt wurde, dass die Inhalte staatenlos dargestellt werden.

Es sind noch robuste REST-APIs erforderlich. REST-Anfragen können jedoch umfangreich und ausführlich sein. Wenn Sie mehrere Kunden haben, die REST-Aufrufe für all Ihre Kanal tätigen, kann dies zu einer Beeinträchtigung der Ausführlichkeit und Leistung führen.

Versand ohne Kopfdaten verwendet häufig GraphQL-APIs. GraphQL ermöglicht eine ähnliche statuslose Übertragung, ermöglicht jedoch zielgerichtetere Abfragen, reduziert die Gesamtzahl der erforderlichen Abfragen und verbessert die Leistung. Es ist üblich zu sehen, Lösungen verwenden eine Mischung aus REST und GraphQL, im Wesentlichen die Wahl der besten Werkzeug für den jeweiligen Auftrag.

Unabhängig von der gewählten API können Sie durch die Definition eines kopflosen Systems, das auf gängigen APIs basiert, die neuesten Browser- und anderen Webtechnologien wie progressive Web-Apps (PWA) nutzen. APIs erstellen eine Standardschnittstelle, die einfach erweiterbar und anpassbar ist.

Normalerweise werden Inhalte auf der Clientseite wiedergegeben. Das bedeutet normalerweise, dass jemand Ihre Inhalte auf einem Mobilgerät aufruft, dass Ihr CMS-Versand den Inhalt enthält und dass dann das Mobilgerät (der Client) für die Wiedergabe der von Ihnen bereitgestellten Inhalte verantwortlich ist. Wenn das Gerät alt oder auf andere Weise langsam ist, ist das digitale Erlebnis ebenfalls langsam.

Das Entpacken von Inhalten von der Präsentation bedeutet, dass es mehr Kontrolle über diese clientseitigen Leistungsaspekte geben kann. Beim serverseitigen Rendering (SSR) wird die Verantwortung für die Wiedergabe des Inhalts vom Browser des Clients auf den Server übertragen. Dadurch können Sie als Anbieter des Inhalts eine garantierte Leistung für Ihre Audience Angebot haben, wenn dies erforderlich ist.

## Organisatorische Herausforderungen {#organization}

Headless eröffnet eine Welt der Flexibilität bei der Bereitstellung digitaler Erlebnisse. Diese Flexibilität kann aber auch eine eigene Herausforderung darstellen.

Viele verschiedene Kanal zu haben kann bedeuten, dass sie jeweils über eigene Präsentationssysteme verfügen. Obwohl sie alle denselben Inhalt über dieselben APIs nutzen, kann das Erlebnis aufgrund der verschiedenen Präsentationen unterschiedlich sein. Die Konsistenz des Kundenerlebnisses muss mit Sorge und Sorge gewährleistet werden.

Durch die Implementierung sorgfältiger Designsysteme, die gemeinsame Nutzung von Musterbibliotheken und die Nutzung wiederverwendbarer Designkomponenten sowie etablierter, offener clientseitiger Frameworks können konsistente Erlebnisse gewährleistet werden. Dies muss jedoch geplant werden.

## Die Zukunft ist ohne Kopf und die Zukunft ist jetzt {#future}

Digitale Erlebnisse werden weiterhin definieren, wie Marken mit Kunden interagieren. Was an einem kostenlosen Design aufregend ist, ist die Flexibilität, die es uns gibt, auf sich verändernde Kundenerwartungen zu reagieren.

Es ist unmöglich, die Zukunft vorherzusagen, aber ohne Kopf gibt man die Agilität, auf alles zu reagieren, was die Zukunft bringt.

## AEM und Headless {#aem-and-headless}

Wenn Sie mit der Developer Journey fortfahren, erfahren Sie, wie AEM kopflosen Versand neben den Vollstapel-Versand-Funktionen unterstützt.

Als Branchenführer im Bereich des digitalen Erfahrungsmanagements erkennt die Adobe, dass die ideale Lösung für echte Herausforderungen, vor denen Erfinder stehen, selten eine binäre Lösung ist. Deshalb unterstützt AEM nicht nur beide Modelle, sondern ermöglicht auch die nahtlose Hybrid-Kombination der beiden Modelle, indem die Vorteile von Headless und Full Stack kombiniert werden, um Ihnen zu helfen, die Verbraucher Ihrer Inhalte am besten zu bedienen, egal wo sie sich befinden.

Diese Journey konzentriert sich auf das reine Headless-Modell von Content Versand. Sobald Sie dieses grundlegende Wissen haben, können Sie jedoch weiter untersuchen, wie Sie die Kraft beider Modelle nutzen können.

## Wie geht es weiter {#what-is-next}

Danke, dass du auf deiner AEM kopflosen Journey angefangen hast! Nachdem Sie dieses Dokument gelesen haben, sollten Sie:

* Grundlegende Konzepte und Terminologie von Versand ohne Inhalt verstehen.
* Verstehen Sie, warum und wann Kopflosigkeit erforderlich ist.
* Wissen Sie auf hoher Ebene, wie kopflose Konzepte verwendet werden und wie sie miteinander verknüpft sind.

Auf diesen Erkenntnissen aufbauen und Ihre AEM Journey ohne Kopf fortsetzen, indem Sie das Dokument [Erste Schritte mit AEM Headless als Cloud Service](getting-started.md) überprüfen, in dem Sie lernen, wie Sie die erforderlichen Tools einrichten und wie Sie damit beginnen können, darüber nachzudenken, wie AEM sich dem Versand von kostenlosen Inhalten und dessen Voraussetzungen nähert.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, mit dem nächsten Teil der Journey für die Entwicklung ohne Kopfdaten fortzufahren, indem Sie das Dokument [Erste Schritte mit AEM Headless als Cloud Service überprüfen. Es folgen jedoch einige zusätzliche optionale Ressourcen, die einen tieferen Einstieg in einige der in diesem Dokument erwähnten Konzepte ermöglichen, die jedoch nicht mit der Journey ohne Kopfdaten fortgeführt werden müssen.](getting-started.md)

* [Eine Einführung in die Architektur von Adobe Experience Manager als Cloud Service](/help/core-concepts/architecture.md)  - Verstehen AEM als Struktur eines Cloud Service
* [AEM Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=de)  ohne Kopf - Nutzen Sie diese praktischen Übungen, um zu untersuchen, wie Sie die verschiedenen Optionen für die Bereitstellung von Inhalten an kopflosen Endpunkten mit AEM nutzen können, und zu entscheiden, was für Sie am besten geeignet ist.
