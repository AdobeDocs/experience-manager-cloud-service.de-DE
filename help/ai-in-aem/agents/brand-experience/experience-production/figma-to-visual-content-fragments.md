---
title: Auftrag „Figma zu visuellen Inhaltsfragmenten“
description: Erfahren Sie, was der Auftrag „Figma zu visuellen Inhaltsfragmenten“ von Brand Experience Agent ist und was er für Sie tun kann.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
source-git-commit: 5413e173ac159015f224845e238779c5dc997ee5
workflow-type: tm+mt
source-wordcount: '443'
ht-degree: 0%

---


# Auftrag „Figma zu visuellen Inhaltsfragmenten“ {#figma-to-visual-content-fragments-job}

Der Auftrag Figma zu visuellen Inhaltsfragmenten des [Erlebnisproduktionsagenten](/help/ai-in-aem/agents/brand-experience/experience-production/overview.md) automatisiert den Prozess der Neuerstellung von Figma-Designs in Adobe Experience Manager (AEM) as a Cloud Service.

<!-- CQDOC-23232 - remove when GA -->

>[!NOTE]
>
>Der Auftrag Figma zu visuellen Inhaltsfragmenten ist derzeit eingeschränkt verfügbar.
>
>Wenn Sie teilnehmen möchten, senden Sie bitte eine Anfrage von Ihrer offiziellen E-Mail-Adresse an [experience-production-agent@adobe.com](mailto:experience-production-agent@adobe.com).

## Überblick {#overview}

Visuelle Inhaltsfragmente in AEM ermöglichen die Vorschau und Bereitstellung von Inhaltsfragmenten mithilfe eines visuellen Layouts, das auf einer [HTML-Vorlage basiert](/help/implementing/developing/extending/content-fragments-visualization-templates.md).

Während das Definieren von Stil- und Layout-Informationen in handcodierten HTML-Vorlagen durchaus möglich ist, ist dies ein hochtechnischer Prozess, der normalerweise von Web-Entwicklerinnen und -Entwicklern ausgeführt wird.

Um diesen Prozess für [visuelle Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md) zu optimieren und da visuelle Designs für modulare Erlebnisse häufig in Figma erstellt werden, ist es auch möglich, Designs direkt aus Figma in AEM zu importieren.

## Voraussetzungen {#prerequisites}

Bevor Sie beginnen:

* Der Import aus Figma erfordert eine Authentifizierung. Der Figma-Benutzer muss ein Zugriffstoken in Figma erstellen und im AEM-Service speichern.

  Dies wird erreicht durch:

   * Generieren eines persönlichen Tokens in Figma
   * Anmelden bei Adobe Experience Cloud unter `https://experience.adobe.com`
   * Beibehalten des Tokens bei `https://experience.adobe.com/#/aem/figmatocontentfragment`

## So laden Sie ein Design hoch {#to-upload-a-design}

Der Ablauf sieht wie folgt aus:

1. Der Designer (Figma-Benutzer) erstellt das Design in Figma.
1. Der Figma-Benutzer erstellt eine Freigabe-Relation zum Design-Objekt in Figma.
1. Der Figma-Benutzer sendet den Freigabe-Link an den AEM-Benutzer.
1. Beginnend mit einer ersten [Eingabeaufforderung](#sample-prompts) kann der AEM-Benutzer dann den KI-Assistenten verwenden, um mit dem Auftrag Figma to Visual Content Fragments zu interagieren und das genehmigte Design in AEM automatisch neu zu erstellen. AEM erstellt automatisch die erforderlichen Inhaltsfragmentmodelle, Inhaltsfragmente und HTML-Vorlagen.
   * Bei Bedarf fordert der Agent weitere Informationen an, beispielsweise die zu verwendende AEM-Umgebung.
   * Der Agentenerstellungsprozess umfasst auch Funktionen, mit denen vorhandene Inhaltsmodelle oder Fragmente wiederverwendet werden können, sofern sie bereits verfügbar sind.
1. Der Agent generiert ein Inhaltsfragment und ein Inhaltsfragmentmodell für den Inhalt sowie eine HTML-Vorlage für das Layout und Design.
   * Der Agent stellt einen direkten Link zum Fragment bereit, über den Sie auf das Modell und die Vorlage zugreifen können.

## Eingabeaufforderungen {#sample-prompts}

Zu den Beispielaufforderungen gehören:

* Import aus Figma:
   * Import aus Figma {*Figma_share_URL*} nach AEM
* So wählen Sie das AEM-Programm aus den Agentenvorschlägen aus:
   * Import aus Figma {*Figma_share_URL*} nach {*AEMaaCS_program/environment_link*}

## Zusätzliche Ressourcen {#additional-resources}

Die folgenden Ressourcen können bei der weiteren Untersuchung visueller Inhaltsfragmente nützlich sein:

* [Visual Content Fragments](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md)
* [Visuelle Inhaltsfragmente - Vorlagen](/help/implementing/developing/extending/content-fragments-visualization-templates.md)
* [Visuelle Inhaltsfragmente - Versand über die Veröffentlichungs-URL](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md)
