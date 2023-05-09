---
title: Was ist ein Headless-CMS?
description: Erfahren Sie mehr über Headless-CMS. Wie funktionieren sie? Welche Alternativen und Unterschiede gibt es? Warum würden Sie ein Headless-CMS verwenden wollen?
exl-id: 53f24f69-ad49-4b8e-9a91-36cd64c1f2b9
source-git-commit: 3306bde7b94b9f863b57d36542e8822df38c79ba
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 100%

---

# Was ist ein Headless-CMS? {#what-is-a-headless-cms}

Headless-Content-Management ist eine zentrale Entwicklung für das heutige Webdesign, das Frontend-/Client-seitige Programme vom Backend-Content-Management-System entkoppelt. Ein Headless-CMS ist daher für die (Backend-)Content-Management-Services verantwortlich, zusammen mit den Mechanismen, die den (Frontend)-Programmen den Zugriff auf diesen Inhalt ermöglichen.

Aber was bedeutet der Begriff wirklich? Hier bieten wir Ihnen eine (sehr kurze) Einführung in die wichtigsten Konzepte.

## Was ist ein Content Management System (CMS)? {#content-management-system}

Beginnen wir mit den Grundlagen – was ist ein Content Management System?

Ein Content Management System (CMS) dient der Speicherung, Verwaltung und Bereitstellung der Inhalte für Ihre Online-Erlebnisse.

## „Traditionelles“ CMS {#traditional-cms}

Traditionell enthält ein CMS sowohl die Backend-Funktionalität für die Speicherung und Bereitstellung von Inhalten als auch die Frontend-Technologie, die zum Rendern des Markups für ein Erlebnis verwendet wird, das Ihr Browser anzeigt (die Präsentationsschicht).

Sehr leistungsstark, sodass Sie die Inhalte und Formatierungen vollständig kontrollieren können, aber einiges an Flexibilität vermissen, die in der sich schnell verändernden Umgebung von heute erforderlich ist, z. B. bei der Verbindung mit externen Programmen.

## Headless-CMS {#headless-cms}

Bei einem Headless-Content-Management-System sind Backend und Frontend jetzt entkoppelt.

Der Headless-Teil ist das Inhalts-Backend, da ein Headless Content Management System (CMS) ein reines Backend-Content-Management-System ist, das explizit als Inhalts-Repository konzipiert und entwickelt wurde, welches Inhalte über eine API für die Anzeige auf beliebigen Geräten zugänglich macht.

Das Frontend, das unabhängig entwickelt und gepflegt wird, ruft mithilfe einer Content Delivery-API Inhalte aus dem Headless-Backend ab, normalerweise im JSON-Format. Dies kann beispielsweise als React- oder Angular-Programm (Einzelseitenprogramm (SPA, Single Page Application)) erfolgen.

Ein Headless-CMS-Backend erfordert normalerweise, dass der Inhalt basierend auf einem Modell oder Schema strukturiert ist. Dies erleichtert es Client-Programmen, die richtigen Inhalte für das Rendern eines Erlebnisses anzufordern. Einige CMS können sowohl strukturierte als auch unstrukturierte Inhalte im JSON-Format bereitstellen.

Ein wesentliches Merkmal dieser Topologie ist, dass der von dem Headless-CMS im JSON-Format bereitgestellte Inhalt ausschließlich Inhalt ohne Design- oder Layout-Informationen ist. In einer Headless-CMS-Implementierung werden alle Formatierungen und Layouts von dem entkoppelten Frontend-Programm verwaltet.

Ein wesentlicher Vorteil einer Headless-CMS-Topologie besteht in der Möglichkeit, Inhalte über mehrere Kanäle hinweg wiederzuverwenden, wobei verschiedene Client-seitige Frontend-Implementierungen genutzt werden können. Dadurch kann der Frontend-Entwicklungsprozess effizienter gestaltet werden. Aber es bedeutet auch, dass der Frontend-Erlebnisentwicklungsprozess sehr Code- und IT-orientiert werden kann, wobei die IT im Wesentlichen das Erlebnis besitzt.

## Content-Delivery-APIs {#content-delivery-apis}

Ein Headless-CMS kann eine oder mehrere Möglichkeiten bereitstellen, Inhalte für Client-seitige Programme verfügbar zu machen. In den meisten Fällen HTTP-REST-APIs, GraphQL-APIs oder beides.

Auch wenn eine REST-API häufig eine einfachere Möglichkeit zum Anfordern von Inhalten zu sein scheint (z. B. durch Bereitstellung von JSON für alle Inhalte, die einem Kriterium entsprechen), stellen sie normalerweise zu viele Inhalte für ein Client-Programm bereit. Dies kann dazu führen, dass der Client die Inhalte analysieren und filtern muss, die tatsächlich für das Rendern benötigt werden.

GraphQL dagegen ist ein fokussierterer Mechanismus, der es Client-Programmen ermöglicht, nach genau dem Inhalt zu suchen, der zum Rendern eines Erlebnisses benötigt wird.

## Full-Stack-CMS {#fullstack-cms}

Ein Full-Stack-CMS stellt normalerweise die traditionelle Topologie für Content-Management und Bereitstellung dar, indem es die Content-Backend- und Frontend-Technologie für das Rendern von Erlebnissen einbezieht. Die Bereitstellung von Inhalten im Full-Stack-CMS erfolgt normalerweise über interne Content-Delivery-APIs. Die Frontend-Funktionalität ist in der Regel spezifisch für das Full-Stack-CMS. Diese Kopplung der Frontend-Technologie mit dem Inhalts-Backend ermöglicht das Erlebnis-Authoring mit WYSIWYG (What-you-see-is-what-you-get) als entscheidenden Vorteil.

## Hybrid-CMS {#hybrid-cms}

Eine moderne Weiterentwicklung des Full-Stack-CMS kann ein hybrides CMS sein. Dadurch soll das Beste aus beiden Welten kombiniert werden:

* effiziente Frontend-Entwicklung über verschiedene Kanäle mit modernen Frontend-Tools;
* unter Beibehaltung der WYSIWYG-Erlebniserstellung, um Benutzer mit wenigen Kenntnissen zu unterstützen und um vermeiden, dass die IT zu einem Engpass für unternehmensübergreifendes Inhalts- und Erlebnis-Management wird.

Dies wird erreicht, indem moderne Frontend-Frameworks wie React eingeführt werden, aber ein wesentliches Minimum an Kopplung mit dem Content-Backend beibehalten wird.

## Entkoppeltes CMS {#decoupled-cms}

Während der Begriff „entkoppeltes CMS” manchmal unabhängig verwendet wird, beschreibt er im Wesentlichen ein Headless-CMS-Backend, indem er sein Schlüsselmerkmal betont: vom Client-seitigen Frontend-Programm entkoppelt zu werden.

## Headful-CMS {#headful-cms}

Dies ist ein weiterer Begriff für ein herkömmliches CMS.

## Weiterführende Literatur {#further-reading}

Weitere Informationen zur Verwendung von AEM in einer Headless-CMS-Topologie finden Sie hier:

* [Einführung in Adobe Experience Manager als Headless-CMS](/help/headless/introduction.md)
