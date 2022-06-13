---
title: Was ist ein Headless-CMS?
description: Erfahren Sie mehr über Headless-CMS. Wie funktionieren sie? Welche Alternativen und Unterschiede gibt es? Warum sollten Sie ein Headless-CMS verwenden wollen?
source-git-commit: 35064ef7d9a4a3f2368667be02b11840b29d56f0
workflow-type: tm+mt
source-wordcount: '754'
ht-degree: 6%

---


# Was ist ein Headless-CMS? {#what-is-a-headless-cms}

Headless Content Management ist eine zentrale Entwicklung für das heutige Web-Design, das Frontend-Client-seitige Anwendungen vom Backend, Content Management System entkoppelt. Ein Headless-CMS ist daher für die (Backend-)Content-Management-Services verantwortlich, zusammen mit den Mechanismen, die den (Frontend-)Anwendungen den Zugriff auf diesen Inhalt ermöglichen.

Aber was bedeutet der Begriff wirklich? Hier bieten wir Ihnen eine (sehr schnelle) Einführung in die Schlüsselkonzepte.

## Was ist ein Content Management System (CMS)? {#content-management-system}

Beginnen wir mit den Grundlagen - was ist ein Content Management System?

Ein Content Management System (CMS) speichert, verwaltet und stellt die Inhalte bereit, die zur Bereitstellung Ihrer Online-Erlebnisse verwendet werden.

## Traditionelles CMS {#traditional-cms}

Traditionell enthält ein CMS sowohl die Backend-Funktionalität für die Speicherung und Bereitstellung von Inhalten als auch die Frontend-Technologie, die zum Rendern des Markups für ein Erlebnis verwendet wird, das Ihr Browser anzeigen wird (die Präsentationsschicht).

Sehr leistungsstark, sodass Sie die Inhalte und Formatierungen vollständig kontrollieren können, aber einige der Flexibilität vermissen, die in der sich schnell bewegenden Umgebung von heute erforderlich ist. z. B. bei der Verbindung mit externen Apps.

## Headless-CMS {#headless-cms}

Mit einem Headless-Content-Management-System sind Backend und Frontend jetzt entkoppelt.

Der Headless-Teil ist das Inhalts-Backend.

* „*Ein Headless-Content-Management-System oder Headless-CMS ist ein Backend-Content-Management-System (CMS), das von Grund auf als Content-Repository erstellt wurde und Inhalte über eine API für die Anzeige auf jedem Gerät zugänglich macht.*“

   Weitere Informationen finden Sie in [Wikipedia](https://en.wikipedia.org/wiki/Headless_content_management_system).

Das Frontend, das unabhängig voneinander entwickelt und gepflegt wird, ruft mithilfe einer Content Delivery-API Inhalte aus dem Headless-Backend ab, normalerweise im JSON-Format. Dies kann beispielsweise als React- oder Angular-Anwendung (Einzelseitenanwendung (SPA)) erfolgen.

Ein Headless-CMS-Backend erfordert normalerweise, dass der Inhalt basierend auf einem Modell oder Schema strukturiert ist. Dies erleichtert Clientanwendungen, die die richtigen Inhalte für das Rendern eines Erlebnisses anfordern. Einige CMS können sowohl strukturierte als auch unstrukturierte Inhalte im JSON-Format verfügbar machen.

Ein wesentliches Merkmal dieser Topologie ist, dass der von dem Headless-CMS im JSON-Format bereitgestellte Inhalt reine Inhalte ohne Design- oder Layoutinformationen ist. In einer Headless-CMS-Implementierung werden alle Formatierungen und Layouts von der entkoppelten Frontend-Anwendung verwaltet.

Ein wesentlicher Vorteil einer Headless-CMS-Topologie besteht in der Möglichkeit, Inhalte über mehrere Kanäle hinweg wiederzuverwenden, was verschiedene clientseitige Frontend-Implementierungen verwenden kann. Dadurch kann der Frontend-Entwicklungsprozess effizienter gestaltet werden. Aber es bedeutet auch, dass der Frontend-Erlebnisentwicklungsprozess sehr Code- und IT-orientiert werden kann, wobei die IT im Wesentlichen das Erlebnis besitzt.

## Content Delivery APIs {#content-delivery-apis}

Ein Headless-CMS kann eine oder mehrere Möglichkeiten bereitstellen, Inhalte für Client-seitige Anwendungen verfügbar zu machen. In den meisten Fällen HTTP-REST-APIs, GraphQL-APIs oder beides.

Auch wenn eine REST-API häufig eine einfachere Möglichkeit zum Anfordern von Inhalten ist (z. B. durch Bereitstellung von JSON für alle Inhalte, die einem Kriterium entsprechen), stellen sie normalerweise zu viele Inhalte für eine Client-Anwendung bereit. Dies kann dazu führen, dass der Client die Inhalte analysieren und herausfiltern muss, die tatsächlich für das Rendering benötigt werden.

GraphQL dagegen ist ein fokussierterer Mechanismus, der es Clientanwendungen ermöglicht, genau nach dem Inhalt zu suchen, der zum Rendern eines Erlebnisses benötigt wird.

## Full-Stack CMS {#fullstack-cms}

Ein Full-Stack-CMS stellt in der Regel die traditionelle Topologie für Content Management und Bereitstellung dar, indem es die Content-Backend- und Frontend-Technologie für das Rendering von Erlebnissen einbezieht. Die Bereitstellung von Inhalten in Full-Stack-CMS erfolgt normalerweise über interne Content-Bereitstellungs-APIs. Die Frontend-Funktionalität ist in der Regel spezifisch für das Vollstapel-CMS. Diese Kopplung der Frontend-Technologie mit dem Inhalts-Backend ermöglicht das Erlebnis-Authoring mit WYSIWYG (What-you-see-is-what-you-get) als entscheidenden Vorteil.

## Hybrid-CMS {#hybrid-cms}

Eine moderne Weiterentwicklung des Full-Stack CMS kann ein hybrides CMS sein. Dadurch soll das Beste aus beiden Welten kombiniert werden:

* effiziente Frontend-Entwicklung über verschiedene Kanäle mit modernen Frontend-Tools;
* unter Beibehaltung der WYSIWYG-Erlebniserstellung, um nicht-technische Benutzer zu unterstützen und zu vermeiden, dass die IT zu einem Engpass für unternehmensübergreifendes Inhalts- und Erlebnismanagement wird.

Dies wird erreicht, indem moderne Frontend-Frameworks wie React eingeführt werden, aber ein wesentliches Minimum an Kopplung mit dem Content-Backend beibehalten wird.

## Entkoppeltes CMS {#decoupled-cms}

Während der Begriff entkoppeltes CMS manchmal unabhängig verwendet wird, beschreibt es im Wesentlichen ein Headless-CMS-Backend, indem es sein Schlüsselmerkmal betont, von der clientseitigen Frontend-Anwendung entkoppelt zu werden.

## Headful CMS {#headful-cms}

Dies ist ein weiterer Begriff für ein herkömmliches CMS.

## Weiterführende Literatur {#further-reading}

Weitere Informationen zur Verwendung von AEM in einer Headless-CMS-Topologie finden Sie hier:

* [Einführung in Adobe Experience Manager as a Headless CMS](/help/headless/introduction.md)
