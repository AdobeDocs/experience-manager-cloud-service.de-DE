---
title: Personalisierung und Content-Targeting
description: Erfahren Sie, wie Sie personalisierte, zielgerichtete Inhalte mit AEM erstellen können.
exl-id: b9b5dbf6-d491-48a6-99b1-19bc1b651b8c
source-git-commit: d2975ec84745f9520ead89588ab727af8e43b740
workflow-type: tm+mt
source-wordcount: '1041'
ht-degree: 12%

---


# Personalisierung und Content-Targeting {#personalization-and-content-targeting}

Die Personalisierung der Webinhalte, die Sie Kunden bereitstellen, bedeutet, diese Erlebnisse auf ihre Interessen und Bedürfnisse abzustimmen. Sie können dies auf der Grundlage der Informationen tun, die Sie über sie haben. z. B. Einkaufszusammenfassung, Alter, Geschlecht, Geografie usw.

Mit Adobe Experience Manager as a Cloud Service (AEM) können Sie eine Inhaltsauswahl erstellen und dann festlegen, welche Zielgruppen (Gruppen von Endbenutzern) die einzelnen Erlebnisse sehen. Das bedeutet, dass Sie Ihre personalisierten Erlebnisse auf bestimmte Zielgruppen ausrichten.

Wenn Ihr Leser online ist, überprüft Ihre Targeting-Engine die über den Endbenutzer verfügbaren Informationen und vergleicht sie mit den Erlebnisdefinitionen. Der Motor *&quot;entscheidet&quot;* welches personalisierte Erlebnis angezeigt werden soll.

AEM bietet ein Framework von Tools für:

* Verfassen zielgerichteter Inhalte, die für eine Reihe von Zielgruppen geeignet sind, abhängig von den verfügbaren Kundeninformationen.
* Definieren der Regeln, mit denen die bekannten Benutzerinformationen anhand einer Zielgruppendefinition aufgelöst werden.
* Konfigurieren Ihrer Seiten zur Präsentation zielgerichteter personalisierter Erlebnisse; um den spezifischen Inhalt wiederzugeben, der für den aktuellen Endbenutzer gilt.

Die folgende Übersicht zeigt einige der für die Personalisierung verwendeten Begriffe in AEM as a Cloud Service, gefolgt von einer empfohlenen Reihenfolge der Aktionen.

## Erfahrung {#experience}

Ein Erlebnis ist Inhalt, den Sie Ihren Endbenutzern zeigen möchten.

## Personalisiertes Erlebnis {#personalized-experience}

Ein personalisiertes Erlebnis ist ein Erlebnis, das einer eingeschränkten Zielgruppe angezeigt wird. Die Audience wird von Ihnen definiert und der Inhalt wird nur angezeigt, wenn die über den aktuellen Endbenutzer bekannten Informationen dieser Zielgruppendefinition entsprechen.

Beim Erstellen von Seiten definieren Sie mehrere Erlebnisse, wobei jedes Erlebnis zu einer (oder mehreren) Zielgruppe(n) aufgelöst wird. Wenn keine Zielgruppe aufgelöst wurde, wird das Standarderlebnis angezeigt.

### Angebot {#offer}

Ein Angebot ist ein personalisiertes Erlebnis, das häufig für einen begrenzten Zeitraum verfügbar ist.

Beispielsweise kann eine Seite einer Beispiel-Website Angebote als Teaser-Bild verwenden, das oben auf der Seite angezeigt wird. Für Personen über 30 und Personen unter 30 werden verschiedene Angebote als Erlebnis-Teaser angezeigt.

## Zielgruppe {#audience}

Eine Zielgruppe ist eine Gruppe von Endbenutzern, die Sie mit personalisierten Inhalten ansprechen möchten. Wenn ein Besucher eine Webseite öffnet, bestimmt die Seitenlogik anhand bekannter Informationen die Zielgruppe, zu der er gehört. Basierend auf dieser Bewertung zeigt AEM den Inhalt an, den Sie für diese Zielgruppe erstellt haben.

Zielgruppen basieren auf Marketingsegmenten. Sie werden entweder in AEM oder Adobe Target erstellt. Sie können Adobe Target-Zielgruppen direkt in AEM mithilfe der Konsole Zielgruppen erstellen.

### Segment {#segment}

Innerhalb AEM ContextHub wird eine Zielgruppe als Segment definiert, basierend auf Regeln (Bedingungen). Diese werden dann aufgelöst, um den erforderlichen Inhalt zu rendern.

## Aktivität {#activity}

Eine Aktivität:

* definiert die Zuordnung einer bestimmten Zielgruppe (Segment) zu einem bestimmten Erlebnis
* definiert den Zeitraum, für den die Zielgruppenbestimmung angewendet wird
* identifiziert [Targeting-Engine](#targeting-engine) , die Ihre Seiten verwenden

Die Aktivität kann entweder eine Personalisierungsaktivität oder eine A/B-Test -Aktivität sein (im Fall des AEM- und Adobe Target-Personalisierungs-Workflows).

Beispielsweise könnte eine Aktivität Erlebnisse für zwei verschiedene Zielgruppen definieren: Menschen über 30 Jahre und Menschen unter 30 Jahren. Auf einer Seite Ihrer Website können dann für jede Zielgruppe unterschiedliche Produkte angezeigt werden.

Oder wie ein anderes Beispiel: Ihr Produktkatalog kann Teaser enthalten, die die Aufmerksamkeit auf saisonale Produkte lenken. Eine Sommersport -Aktivität kann also die Zielgruppen definieren, die die Teaser in den Sommermonaten ansprechen.

Verwenden Sie die [Aktivitätskonsole](/help/sites-cloud/authoring/personalization/activities.md) , um Aktivitäten für Ihre [Marken](#brand). Sie können während der Erstellung Ihrer [zielgerichtete Inhalte](/help/sites-cloud/authoring/personalization/targeted-content.md) mit [Targeting-Modus](/help/sites-cloud/authoring/personalization/targeted-content.md#adding-and-removing-experiences-using-targeting-mode).

### Brand Portal-Benutzeroberfläche {#brand}

Eine Marke umfasst eine Auswahl von Marketing-Aktivitäten und -Bereichen.

Wenn Sie eine Marke mithilfe der Aktivitätskonsole erstellen, wird sie auch in der Angebotskonsole angezeigt.

### Bereich {#area}

Ein Gebiet ist eine Unterteilung einer Marke.

## Targeting-Modus {#targeting-mode}

Beim Authoring ist dies der Bearbeitungsmodus, mit dem die Komponenten für die Personalisierung aktiviert und konfiguriert werden.

Sie können [Verfassen zielgerichteter Inhalte](/help/sites-cloud/authoring/personalization/targeted-content.md) im Targeting-Modus von AEM. Der Targeting-Modus und die Targeting-Komponente sind wichtige Werkzeuge für die Erstellung von Erlebnisinhalten für Ihre Marketing-Aktivitäten.

## Experience Fragment {#experience-fragments}

Ein gruppierter Satz von Komponenten, aus denen ein Erlebnis besteht.

[Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#personalization-experience-fragment) aus Inhalten und Informationen (Stilen usw.) bestehen, um ein Erlebnis zu erstellen; sie können direkt beim Erstellen von Seiten verwendet werden. Sie können als Teilmenge einer AEM Seite betrachtet werden. Sie ermöglichen es Autoren von Inhalten, Inhalte kanalübergreifend wiederzuverwenden, einschließlich Sites-Seiten und Drittanbietersystemen.

Für ein Personalisierungsbeispiel können die Schaltflächen Titel, Bild, Beschreibung und Aktionsaufruf kombiniert werden, um ein Teaser-Erlebnis zu bilden. Die Verwendung von Experience Fragments ist ein wichtiger Bestandteil der Adobe Target-Personalisierung.

## Targeting-Engine {#targeting-engine}

Die Targeting-Engine ist der Mechanismus, der die Logik für zielgerichtete Inhalte auflöst. [Aktivitäten](/help/sites-cloud/authoring/personalization/activities.md) sind so konfiguriert, dass eine von zwei verfügbaren Targeting-Engines verwendet wird: AEM oder Adobe Target.

Die Targeting-Engine ist die Plattform oder der Mechanismus, die bzw. der bestimmt, welches Personalisierungssystem verwendet werden soll.

Derzeit können AEM Folgendes verwenden:

* [AEM ContextHub](#aem-contexthub) (AEM)
* die [Adobe Target](#adobe-target) Personalisierungsmaschine

>[!CAUTION]
>
>Eine einzelne AEM kann nicht beide Engines gleichzeitig verwenden.
>
>Sie können beide Engines auf separaten Seiten innerhalb derselben Website verwenden.

### AEM-ContextHub {#aem-contexthub}

AEM stellt die integrierte Targeting-Engine ContextHub bereit, die Seitenanfragen verarbeitet und den anzuzeigenden Inhalt bestimmt. Bei der Verwendung der AEM Targeting-Engine sind Sie auf den Einsatz von Segmenten beschränkt, die in AEM erstellt wurden und die Zielgruppen Ihrer Erlebnisse festlegen.

### Adobe Target {#adobe-target}

Mit der Adobe Target-Targeting-Engine werden von Seitenbesuchen gesammelte Informationen in Adobe Target verfolgt.

* Bei der Verwendung dieser Targeting-Engine setzen Sie Segmente ein, die Sie aus Adobe Target importieren und die die Zielgruppen Ihrer Erlebnisse bestimmen.
* Aktivitäten, die mit der Adobe Target-Engine bereitgestellt werden, werden [mit Target synchronisiert](/help/sites-cloud/authoring/personalization/activities.md#synchronizing-activities-with-adobe-target).

Sie können diese Engine verwenden, wenn Sie [integriert mit Adobe Target](/help/sites-cloud/integrating/integration-adobe-target-ims.md).

## Einrichten personalisierter Inhalte {#how-to-setup-personalized-content}

Für die Bereitstellung Ihres personalisierten Inhalts sind verschiedene Schritte und Definitionen erforderlich:

1. Integrieren Sie AEM in Ihre Targeting-Engine.

1. Konfigurieren Sie die Zielgruppen.

   1. Definieren Sie je nach Targeting-Engine die Zielgruppe oder das Segment sowie die Regeln.

1. Erstellen Sie Ihre Marke und Aktivitäten.

1. Erstellen Sie die Auswahl der Erlebnisse, die Sie den verschiedenen Zielgruppen anzeigen möchten.

1. Personalisieren Sie diese Erlebnisse, indem Sie sie auf die spezifischen Zielgruppen (Segmente) ausrichten.