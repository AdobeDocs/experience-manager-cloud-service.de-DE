---
title: Personalisierung und Content-Targeting
description: Informationen zum Erstellen von personalisierten, zielgerichteten Inhalten mit AEM
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 99%

---


# Personalisierung und Content-Targeting {#personalization-and-content-targeting}

Personalisierung der Web-Inhalte, die Sie Kunden bereitstellen, bedeutet, diese Erlebnisse auf die Kundeninteressen und -bedürfnisse abzustimmen. Sie können dies auf der Grundlage der Informationen tun, die Sie über Ihre Kunden haben. z. B. Einkaufsübersicht, Alter, Geschlecht, geografische Angaben usw.

Mit Adobe Experience Manager as a Cloud Service (AEM) können Sie eine Auswahl von Inhalten erstellen und dann festlegen, welche Zielgruppen (Gruppen von Endbenutzenden) die einzelnen Erlebnisse zu sehen bekommen. Das bedeutet, dass Sie Ihre personalisierten Erlebnisse an bestimmte Zielgruppen richten.

Wenn Ihr Reader online ist, überprüft Ihre Targeting-Engine die über den Endbenutzer verfügbaren Informationen und vergleicht sie mit den Erlebnisdefinitionen. Die Engine *„entscheidet“* dann, welches personalisierte Erlebnis angezeigt werden soll.

AEM bietet ein Framework von Tools für folgende Aktivitäten:

* Erstellen zielgerichteter Inhalte, die für eine Reihe von Zielgruppen geeignet sind, in Abhängigkeit von den verfügbaren Kundeninformationen.
* Definieren der Regeln, die verwendet werden, um die bekannten Benutzerinformationen mit einer Zielgruppendefinition abzugleichen.
* Konfigurieren Ihrer Seiten, um zielgerichtete personalisierter Erlebnisse zu präsentieren, sodass die für den aktuellen Endbenutzer spezifischen Inhalte dargestellt werden.

Die folgende Übersicht zeigt einige der Begriffe, die im Zusammenhang mit der Personalisierung in AEM as a Cloud Service verwendet werden, gefolgt von einer empfohlenen Reihenfolge von Aktionen.

## Erfahrung {#experience}

Ein Erlebnis ist ein Inhalt, den Sie Ihren Endbenutzern anzeigen lassen möchten.

## Personalisiertes Erlebnis {#personalized-experience}

Ein personalisiertes Erlebnis ist ein Erlebnis, das einer eingeschränkten Zielgruppe angezeigt wird. Die Zielgruppe wird von Ihnen definiert und der Inhalt wird nur angezeigt, wenn die über den aktuellen Endbenutzer bekannten Informationen dieser Zielgruppendefinition entsprechen.

Beim Erstellen von Seiten definieren Sie mehrere Erlebnisse, wobei jedes Erlebnis für eine (oder mehrere) Zielgruppe(n) bestimmt ist. Wenn sich keine Zielgruppe zuordnen lässt, wird das Standarderlebnis angezeigt.

### Angebot {#offer}

Ein Angebot ist ein personalisiertes Erlebnis, das oft nur für einen begrenzten Zeitraum zur Verfügung steht.

Beispielsweise kann eine Seite einer Beispiel-Website Angebote als das Teaser-Bild verwenden, das oben auf der Seite eingeblendet wird. Personen über 30 und Personen unter 30 können jeweils andere Angebote als Erlebnis-Teaser angezeigt bekommen.

## Zielgruppe {#audience}

Eine Zielgruppe ist eine Gruppe von Endbenutzern, die Sie mit personalisierten Inhalten ansprechen möchten. Wenn ein Besucher eine Web-Seite öffnet, bestimmt die Seitenlogik anhand bekannter Informationen die Zielgruppe, zu der er gehört. Auf der Grundlage dieser Bewertung zeigt AEM die Inhalte an, die Sie für diese Zielgruppe erstellt haben.

Zielgruppen basieren auf Marketing-Segmenten. Sie werden entweder in AEM oder Adobe Target erstellt. Sie können Adobe Target-Zielgruppen direkt in AEM mithilfe der Zielgruppen-Konsole erstellen.

### Segment {#segment}

In AEM ContextHub wird eine Zielgruppe als Segment definiert, und zwar auf der Grundlage von Regeln (Bedingungen). Diese werden dann aufgelöst, um den erforderlichen Inhalt zu rendern.

## Aktivität {#activity}

Eine Aktivität

* definiert die Zuordnung einer bestimmten Zielgruppe (Segment) zu einem bestimmten Erlebnis,
* definiert den Zeitraum, für den die Zielgruppenbestimmung gilt,
* identifiziert die [Targeting-Engine](#targeting-engine), die Ihre Seiten verwenden.

Die Aktivität kann entweder eine Personalisierungsaktivität oder eine A/B-Test-Aktivität sein (im Fall des AEM- und Adobe Target-Personalisierungs-Workflows).

Beispielsweise könnte eine Aktivität Erlebnisse für zwei verschiedene Zielgruppen definieren: Personen im Alter über 30 und Personen im Alter unter 30. Auf einer Seite Ihrer Website könnten dann für jede Zielgruppe jeweils andere Produkte angezeigt werden.

Oder, als ein anderes Beispiel, Ihr Produktkatalog kann Teaser enthalten, die die Aufmerksamkeit auf saisonale Produkte lenken. So könnte eine Sommersportaktivität die Zielgruppen definieren, an die sich die Teaser während der Sommermonate richten.

Mit der [Aktivitätskonsole](/help/sites-cloud/authoring/personalization/activities.md) können Sie die Aktivitäten für Ihre [Marken](#brand) erstellen und verwalten. Auch können Sie Aktivitäten erstellen, während Sie Ihre [zielgerichteten Inhalte](/help/sites-cloud/authoring/personalization/targeted-content.md) mit dem [Targeting-Modus](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode) erstellen.

### Marke {#brand}

Zu einer Marke gehört eine Auswahl von Marketing-Aktivitäten und -Bereichen.

Wenn Sie mithilfe der Aktivitätskonsole eine Marke erstellen, erscheint diese auch in der Angebotskonsole.

### Bereich {#area}

Ein Bereich ist eine Unterabteilung einer Marke.

## Targeting-Modus {#targeting-mode}

Beim Authoring ist dies der Bearbeitungsmodus, in dem Sie die Komponenten für die Personalisierung aktivieren und konfigurieren.

[Erstellen zielgerichteter Inhalte](/help/sites-cloud/authoring/personalization/targeted-content.md) ist im Targeting-Modus von AEM möglich. Der Targeting-Modus und die Targeting-Komponente sind wichtige Werkzeuge für die Erstellung von Erlebnisinhalten für Ihre Marketing-Aktivitäten.

## Experience Fragment {#experience-fragments}

Ein gruppierter Satz von Komponenten, aus denen ein Erlebnis besteht.

[Experience Fragments](/help/sites-cloud/authoring/fragments/content-fragments.md#personalization-experience-fragment) bestehen aus Inhalten und Informationen (Stilen usw.) zum Erstellen eines Erlebnisses. Sie können beim Erstellen von Seiten direkt verwendet werden. Sie können als Teilmenge einer AEM-Seite betrachtet werden. Sie ermöglichen Inhaltsautorinnen und Inhaltsautoren die Wiederverwendung von Inhalten über verschiedene Kanäle hinweg, einschließlich der Seiten von Sites und Drittanbietersystemen.

Um ein Personalisierungsbeispiel zu geben, können die Schaltflächen „Titel“, „Bild“, „Beschreibung“ und „Aktionsaufruf“ kombiniert werden, um ein Teaser-Erlebnis zu bilden. Die Verwendung von Experience Fragments ist ein wichtiger Bestandteil der Adobe Target-Personalisierung.

## Targeting-Engine {#targeting-engine}

Die Targeting-Engine ist der Mechanismus, der die Logik für zielgerichtete Inhalte auflöst. [Aktivitäten](/help/sites-cloud/authoring/personalization/activities.md) sind so konfiguriert, dass eine von zwei verfügbaren Targeting-Engines verwendet wird: AEM oder Adobe Target.

Die Targeting-Engine ist die Plattform oder der Mechanismus, die bzw. der bestimmt, welches Personalisierungssystem verwendet werden soll.

Derzeit kann AEM Folgendes verwenden:

* [AEM ContextHub](#aem-contexthub) (Standard-AEM)
* die [Adobe Target](#adobe-target)-Personalisierungs-Engine

>[!CAUTION]
>
>Auf einer einzelnen AEM-Seite können nicht beide Engines gleichzeitig verwendet werden.
>
>Sie können die beiden Engines auf separaten Seiten innerhalb derselben Website verwenden.

### AEM ContextHub {#aem-contexthub}

AEM verfügt über die integrierte Targeting-Engine [ContextHub](/help/implementing/developing/personalization/contexthub.md), mit der Seitenanfragen verarbeitet und anzuzeigende Inhalte bestimmt werden. Bei der Verwendung der AEM Targeting-Engine sind Sie auf den Einsatz von Segmenten beschränkt, die in AEM erstellt wurden, um die Zielgruppen Ihrer Erlebnisse festzulegen.

### Adobe Target {#adobe-target}

Mit der Targeting-Engine von [Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md) werden von Seitenbesuchen gesammelte Informationen in Adobe Target verfolgt.

* Bei der Verwendung dieser Targeting-Engine setzen Sie Segmente ein, die Sie aus Adobe Target importieren, um die Zielgruppen Ihrer Erlebnisse zu bestimmen.
* Aktivitäten, die die Adobe Target-Engine verwenden, werden [mit Target synchronisiert](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target).

Sie können diese Engine verwenden, wenn Sie über eine [Integration mit Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md) verfügen.

## Einrichten personalisierter Inhalte {#how-to-setup-personalized-content}

Für die Bereitstellung Ihrer personalisierten Inhalte sind verschiedene Schritte und Definitionen erforderlich:

1. Richten Sie Ihre Targeting-Engine wie folgt ein:

   1. Konfigurieren von [ContextHub](/help/implementing/developing/personalization/configuring-contexthub.md)
   1. Integration in [Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)

1. Konfigurieren Sie die Zielgruppen.

   1. Definieren Sie je nach Targeting-Engine die [Zielgruppe](https://experienceleague.adobe.com/docs/target/using/audiences/target.html?lang=de) oder das [ContextHub-Segment](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md) zusammen mit den Regeln.

1. Erstellen Sie Ihre [Marke und Aktivitäten](/help/sites-cloud/authoring/personalization/activities.md).

1. Erstellen Sie die Auswahl der Erlebnisse, die für die verschiedenen Zielgruppen angezeigt werden sollen.

1. Personalisieren Sie diese Erlebnisse, indem Sie sie auf die jeweiligen Zielgruppen (Segmente) [ausrichten](/help/sites-cloud/authoring/personalization/targeted-content.md).