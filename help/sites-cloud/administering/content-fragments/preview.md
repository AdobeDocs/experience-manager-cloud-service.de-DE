---
title: Vorschau von Inhaltsfragmenten
description: Erfahren Sie, wie Sie Ihre Inhaltsfragmente mit einer Reihe von Methoden in der Vorschau anzeigen können.
feature: Content Fragments
role: User, Developer
solution: Experience Manager Sites
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 40c02806-76a2-43ed-982c-0410c2125a36
source-git-commit: 5413e173ac159015f224845e238779c5dc997ee5
workflow-type: tm+mt
source-wordcount: '561'
ht-degree: 37%

---

# Vorschau von Inhaltsfragmenten {#previewing-content-fragments}

Inhaltsfragmente können sowohl für die Headless-Bereitstellung als auch für die Seitenbearbeitung verwendet werden. Da es sich bei den Fragmenten ausschließlich um Inhalte ohne Formatierung handelt, kann die Überprüfung schwieriger sein. Es werden also mehrere Methoden für die Vorschau Ihrer Fragmente in einer Vielzahl von Szenarien bereitgestellt.

Es gibt mehrere Methoden für Inhaltsfragmente, auf die über die Konsole und den Editor für Inhaltsfragmente zugegriffen werden kann. Die in diesem Abschnitt beschriebene Konsole und der Editor wurden für die Bereitstellung von Headless-Inhalten entwickelt (obwohl sie für alle Szenarien verwendet werden können).

Sie können eine Vorschau Ihres Fragments anzeigen:

* durch Veröffentlichung in und Rückgängigmachen der Veröffentlichung in der [Vorschauinstanz](#preview-instance)

* in einer [externen Anwendung](#preview-url-pattern) unter Verwendung des [Vorschau-URL-Musters](#preview-url-pattern)

* mit einer [Visualisierungsvorlage (HTML)](#preview-with-visualization-html-templates)

Sie können Ihr Fragment natürlich auch im [Inhaltsfragment-Editor“ &#x200B;](/help/sites-cloud/administering/content-fragments/authoring.md).

>[!IMPORTANT]
>
>Auf Inhaltsfragmente können Sie über zwei Konsolen zugreifen: **Inhaltsfragmente** und **Assets**.
>
>Es gibt auch zwei Editoren für die Erstellung von Inhaltsfragmenten. Auch wenn die grundlegende Funktionalität gleich ist, gibt es einige Unterschiede. Auf beide Editoren kann von beiden Konsolen aus zugegriffen werden.
>
>Dieser Abschnitt befasst sich mit der **Inhaltsfragmentekonsole** und dem *neuen* Inhaltsfragmenteditor. Diese wurden für die Bereitstellung von Headless-Inhalten entwickelt (obwohl sie für alle Szenarien verwendet werden können)
>
>Weitere Informationen finden Sie unter:
>
>* Verwendung der **Assets**-Konsole für die [Verwaltung von Inhaltsfragmenten](/help/assets/content-fragments/content-fragments-managing.md),
>* Verwendung des [*originalen* Inhaltsfragmenteditors](/help/assets/content-fragments/content-fragments-variations.md),
>* Verwendung von [Inhaltsfragmenten für die Seitenerstellung](/help/sites-cloud/authoring/fragments/content-fragments.md).

## Vorschauinstanz {#preview-instance}

Sie können **Fragment** und **Veröffentlichung rückgängig machen** in Ihrem **[Vorschau-Service](/help/headless/deployment/architecture.md)** (sowie in Ihrer Veröffentlichungsinstanz) veröffentlichen.

Sie können das Fragment entweder über den Editor oder die Konsole veröffentlichen.

Siehe:

* [Veröffentlichen und Anzeigen einer Vorschau eines Fragments](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment) für ausführliche Informationen.

* [Veröffentlichung eines Fragments aufheben](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment) für ausführliche Details.

## Vorschau in einer externen Anwendung {#preview-in-an-external-application}

Der Inhaltsfragmenteditor bietet Autorinnen und Autoren die Möglichkeit, die Vorschau von Bearbeitungen in einer externen Frontend-Anwendung anzuzeigen.

### Muster für URL-Vorschau {#preview-url-pattern}

Für die Verwendung dieser Funktion müssen Sie zunächst wie folgt vorgehen:

* Arbeiten Sie mit Ihrem IT-Team zusammen, um die externe Frontend-Anwendung einzurichten, die das Inhaltsfragment rendert, indem sie die JSON-Ausgabe nutzt.

* Wenn die externe Frontend-Anwendung eingerichtet ist, muss das **Standard-URL-Vorschaumuster** als [-Eigenschaft des entsprechenden Inhaltsfragmentmodells](/help/sites-cloud/administering/content-fragments/managing-content-fragment-models.md#model-properties) definiert werden.

Die Vorschau-URL sollte diesem Muster folgen:

    `https://<preview_url>?param=${expression}`

Verfügbare Ausdrücke sind:

* `${contentFragment.path}`
* `${contentFragment.model.path}`
* `${contentFragment.model.name}`
* `${contentFragment.variation}`
* `${contentFragment.id}`

Wenn die URL definiert wurde **[ist die Schaltfläche](/help/sites-cloud/administering/content-fragments/authoring.md#preview-content-fragment)** Vorschau“ in der oberen Symbolleiste des Editors aktiv. Sie können diese Schaltfläche auswählen, um die externe Anwendung (auf einer separaten Registerkarte) zum Rendern des Inhaltsfragments zu starten.

### Vorschau in der externen Anwendung {#preview-in-the-external-application}

Sie können eine Vorschau eines Inhaltsfragments in einer externen Anwendung anzeigen:

>[!NOTE]
>
>Für [&#x200B; Option muss &#x200B;](#preview-url-pattern) „Vorschau des URL-Musters“ konfiguriert werden.

1. Navigieren Sie in der Inhaltsfragmentkonsole zum Speicherort des gewünschten Fragments.
1. Fragment im Editor öffnen
1. Wählen **Vorschau** in der oberen Symbolleiste aus.
1. Wählen Sie **Anwendung** aus, um Ihr Fragment in der externen Anwendung zu öffnen, z. B. im [universellen Editor](/help/implementing/universal-editor/introduction.md).

## Vorschau mit Visualisierungsvorlagen (HTML) {#preview-with-visualization-html-templates}

<!-- CQDOC-23232 - remove when GA -->

>[!NOTE]
>
>Visuelle Inhaltsfragmente sind derzeit nur eingeschränkt verfügbar.
>
>Wenn Sie teilnehmen möchten, senden Sie bitte eine Anfrage von Ihrer offiziellen E-Mail-Adresse an [experience-production-agent@adobe.com](mailto:experience-production-agent@adobe.com).

Mit AEM können Sie eine Vorschau Ihres Inhaltsfragments mithilfe eines visuellen Layouts anzeigen, das auf einer HTML-Vorlage basiert.

Siehe [Visuelle Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md) für Details zum [Vorschau Ihres Fragments mit Vorlagen](/help/sites-cloud/administering/content-fragments/visual-content-fragments.md#preview-your-template-with-a-template).

>[!NOTE]
>
>Unter [Visual Content Fragments - Vorlagen](/help/implementing/developing/extending/content-fragments-visualization-templates.md) finden Sie Einzelheiten zum Erstellen, Anpassen und Hochladen eigener HTML-Vorlagen.

