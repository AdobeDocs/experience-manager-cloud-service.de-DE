---
title: Auftrag zur Inhaltserstellung
description: Erfahren Sie, was der Inhaltserstellungsauftrag von Brand Experience Agent ist und was er für Sie tun kann.
feature: Edge Delivery Services, Agentic AI
role: User, Admin, Developer
source-git-commit: 3a0e9b322aec8b06285a94b9e288580faaf87921
workflow-type: tm+mt
source-wordcount: '787'
ht-degree: 1%

---


# Auftrag zur Inhaltserstellung {#content-create}

Der Auftrag zur Inhaltserstellung ist Teil des [Experience Production Agent](/help/ai-in-aem/agents/brand-experience/experience-production/overview.md) der neue markeninterne Seiten erstellt, wobei eine natürliche Sprache, ein Marketing-Überblick und eine AEM-Vorlage verwendet werden. Dadurch wird die Seitenproduktion für Adobe Experience Manager (AEM) as a Cloud Service und Edge Delivery Services beschleunigt.

<!-- see Limitations too and update when appropriate -->

>[!NOTE]
>
>Der Auftrag zur Inhaltserstellung ist derzeit eingeschränkt verfügbar. Wenn Sie teilnehmen möchten, senden Sie bitte eine Anfrage von Ihrer offiziellen E-Mail-Adresse an [experience-production-agent@adobe.com](mailto:experience-production-agent@adobe.com).

## Übersicht {#overview}

Der Auftrag „Inhaltserstellung“ generiert neue markeninterne Seiten, die eine natürliche Sprache zusammen mit einer Marketing-Zusammenfassung und einer AEM-Vorlage verwenden.

Sie können wie folgt auf den Auftrag zur Inhaltserstellung zugreifen:

* [Der KI-Assistent](#access-ai-assistant)

>[!VIDEO](https://video.tv.adobe.com/v/3488436?learn=on)

So verwenden Sie den Auftrag „Inhalt erstellen“:

* Sie [&#x200B; Folgendes &#x200B;](#provide-the-prompt-and-brief):

   * Eine Eingabeaufforderung in natürlicher Sprache, die beschreibt, was erstellt werden soll und wo die Seite leben soll.

   * Eine kurze Beschreibung:

      * Der Auftrag zur Inhaltserstellung verwendet eine Marketing-Zusammenfassung oder ein Dokument, das beschreibt, was der Agent generieren soll. Der Auftrag akzeptiert eine Vielzahl von Formaten für den Auftrag. In effektiven Briefs werden häufig Ziele, Zielgruppe, Themen, Anzahl der Zielworte und Schlüsselwörter angegeben.

* Anschließend [&#x200B; Sie &#x200B;](#submit) Eingabeaufforderung und die Kurzbeschreibung
* Als Nächstes geben Sie eine [AEM-Vorlage](#select-a-template) an, die das erforderliche Layout definiert
* Der Auftrag stellt einen [Plan zur Überprüfung bereit](#review-the-plan)
* Sie können dann [mit der Generierung fortfahren](#proceed-with-generation) und [bei Bedarf die Bearbeitung weiter verfeinern](#further-refinement-in-authoring)

Der Agent richtet die Generierung an der Vorlage aus und kann Abschnitte hinzufügen oder entfernen, um sie der Zusammenfassung anzupassen, z. B. wenn Sie eine höhere oder niedrigere Wortzahl benötigen.

>[!NOTE]
>
>Auf dieser Seite wird ein Beispiel verwendet, um basierend auf einer angehängten Zusammenfassung unter `https://frescopa.coffee/sustainability/coffee-bean-types` eine neue Seite zu erstellen

## Zugriff - KI-Assistent {#access-ai-assistant}

Sie können über den KI-Assistenten auf den Auftrag in AEM zugreifen.

Öffnen Sie den [KI](/help/implementing/cloud-manager/ai-assistant-in-aem.md)Assistenten) in der Symbolleiste oben rechts in [`experience.adobe.com`](https://experience.adobe.com).

## Eingabeaufforderung und kurze Beschreibung bereitstellen {#provide-the-prompt-and-brief}

Im KI-Assistenten müssen Sie:

1. Beschreiben Sie in natürlicher Sprache, was Sie tun möchten, und identifizieren Sie mithilfe eines Pfads oder einer URL innerhalb Ihrer Website, wo sich die Seite befinden wird. Erstellen Sie beispielsweise eine neue Seite basierend auf Ihrer Zusammenfassung:

   * `create a new page based on the attached at https://frescopa.coffee/sustainability/coffee-bean-types`

     ![Inhaltserstellungsauftrag - Eingabeaufforderung hinzufügen](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-create-page.png)

1. Laden Sie die für Ihre Anfrage relevante Zusammenfassung hoch. So laden Sie die Zusammenfassung:

   1. Wählen Sie **+** unten links im KI-Assistenten und anschließend **Dateien anhängen**:

      ![Inhaltserstellungsauftrag - Zusammenfassung laden](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-load-brief.png)

   1. Fügen Sie Ihre Kurzdatei hinzu. Die geladene Zusammenfassung wird oben rechts im Eingabeaufforderungsdialogfeld angezeigt:

      ![Inhaltserstellungsauftrag - Zusammenfassung geladen](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-loaded-brief.png)

1. Wenn Sie bereit sind, senden Sie die Eingabeaufforderung und die Zusammenfassung mithilfe des blauen Senden-Symbols (blaue Pfeilspitze).

## Wählen Sie eine Vorlage aus {#select-a-template}

Der Agent fordert Sie dann auf, eine Vorlage anzugeben. Die Vorlage stellt dem Agenten die Seitenstruktur und das Layout bereit. Die Generierung entspricht diesem Layout. Der Agent kann je nach Bedarf Abschnitte hinzufügen und entfernen, die auf der Zusammenfassung basieren, z. B. um eine andere Wortzahl zu erreichen.

![Inhaltserstellungsauftrag - Vorlage angeben](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-select-template.png)

## Plan überprüfen {#review-the-plan}

Als Nächstes präsentiert der Agent einen Plan für die Änderungen, die er vornehmen wird, basierend auf Ihren Eingaben und seiner Analyse der Zusammenfassung. Sie können den Plan anpassen oder mit dem Plan fortfahren und mit der Erstellung beginnen.

>[!NOTE]
>
> Wenn Sie den [Governance-Agent](/help/ai-in-aem/agents/governance/overview.md) verwenden, kann die Generierung Ihren Markenrichtlinien entsprechen.

![Inhaltserstellungsauftrag - Plan prüfen](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-review-plan.png)

## Mit Generierung fortfahren {#proceed-with-generation}

Nach Abschluss der Generierung stellt der Agent zwei Links bereit:

* Ein **Vorschau**-Link
* Ein **Bearbeiten**-Link
   * Verwenden Sie den Link „Bearbeiten[&#x200B; um die Seite in einer AEM-Authoring-Oberfläche zur &#x200B;](#further-refinement-in-authoring) zu öffnen.

![Auftrag für Inhaltserstellung - mit der Generierung fortfahren](/help/ai-in-aem/agents/brand-experience/experience-production/assets/create-content-example-proceed-generation.png)

## Weitere Verfeinerung beim Authoring {#further-refinement-in-authoring}

Nachdem Sie die Seite in AEM bearbeitet haben, wird sie in Ihrer Authoring-Umgebung geöffnet (z. B. im [universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) oder [Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md)).

Im [universellen Editor](#universal-editor-edit-text-with-the-assistant) ist der KI-Assistent *kontextbezogen*: Sie können Elemente auf der Arbeitsfläche auswählen und mit dem Assistenten daran arbeiten.

### Universeller Editor - Bearbeiten von Text mit dem Assistenten {#universal-editor-edit-text-with-the-assistant}

So verfeinern Sie die Kopie aus dem Assistenten beim Authoring:

1. Wählen Sie das Element im [universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) aus.
1. Öffnen Sie den KI-Assistenten oben rechts, geben Sie Ihre Eingabeaufforderung ein und senden Sie sie.

Beispiel-Eingabeaufforderungen:

* `Update to Explore the World of Coffee`
* `Update to be more engaging for the 30-40 year old age demographic and avid coffee drinker`

Wählen Sie **Änderungen anwenden** (oder eine entsprechende Option) aus, damit Aktualisierungen auf der Seite angezeigt werden.

## Aktivierung {#activation}

Sie können AEM-Agenten über den [Playground](https://www.aem.live/developer/aem-playground) erkunden oder sich mit Ihrem CSM oder TAM verbinden, um den Zugriff über die Agent SKU zu besprechen.

## Einschränkungen {#limitations}

Beachten Sie die folgenden Einschränkungen:

* Die Funktion ist nur eingeschränkt verfügbar und erfordert manuelles Onboarding für die Teilnahme. Wenn Sie teilnehmen möchten, senden Sie bitte eine Anfrage von Ihrer offiziellen E-Mail-Adresse an [experience-production-agent@adobe.com](mailto:experience-production-agent@adobe.com).

## Zusätzliche Ressourcen {#additional-resources}

Die folgenden Ressourcen können bei der weiteren Untersuchung des Experience Production Agent nützlich sein:

* Sie können auch die [Experience Production Agent Workbook](https://www.adobe.com/go/aem-epa-workbook_de) für angeleitete, praktische Anweisungen verwenden.
