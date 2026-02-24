---
title: Vorschau von Inhaltsfragmenten
description: Erfahren Sie, wie Sie Ihre Inhaltsfragmente mit einer Reihe von Methoden in der Vorschau anzeigen können.
feature: Content Fragments
role: User, Developer
solution: Experience Manager Sites
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 40c02806-76a2-43ed-982c-0410c2125a36
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 49%

---

# Vorschau von Inhaltsfragmenten {#previewing-content-fragments}

Inhaltsfragmente können sowohl für die Headless-Bereitstellung als auch für die Seitenbearbeitung verwendet werden. Da es sich bei den Fragmenten ausschließlich um Inhalte ohne Formatierung handelt, kann die Überprüfung schwieriger sein. Es werden also mehrere Methoden für die Vorschau Ihrer Fragmente in einer Vielzahl von Szenarien bereitgestellt.

Es gibt mehrere Methoden für Inhaltsfragmente, auf die über die Konsole und den Editor für Inhaltsfragmente zugegriffen werden kann. Die in diesem Abschnitt beschriebene Konsole und der Editor wurden für die Bereitstellung von Headless-Inhalten entwickelt (obwohl sie für alle Szenarien verwendet werden können).

Sie können eine Vorschau Ihres Fragments anzeigen:

* mithilfe des [Vorschau-URL-Musters](#preview-url-pattern)

* durch Veröffentlichung in und Rückgängigmachen der Veröffentlichung in der [Vorschauinstanz](#preview-instance)

<!--
* with a HTML template, using **[Preview]()** from the Content Fragments console
-->

Sie können Ihr Fragment natürlich auch im [Inhaltsfragment-Editor“ ](/help/sites-cloud/administering/content-fragments/authoring.md).

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

## Muster für URL-Vorschau {#preview-url-pattern}

Der Inhaltsfragmenteditor bietet Autorinnen und Autoren die Möglichkeit, die Vorschau von Bearbeitungen in einer externen Frontend-Anwendung anzuzeigen.

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

## Vorschauinstanz {#preview-instance}

Sie können **Fragment** und **Veröffentlichung rückgängig machen** in Ihrem **[Vorschau-Service](/help/headless/deployment/architecture.md)** (sowie in Ihrer Veröffentlichungsinstanz) veröffentlichen.

Sie können Ihr Fragment entweder im Editor oder in der Konsole veröffentlichen.

Siehe:

* [Veröffentlichen und Anzeigen einer Vorschau eines Fragments](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment) für ausführliche Informationen.

* [Veröffentlichung eines Fragments aufheben](/help/sites-cloud/administering/content-fragments/managing.md#unpublishing-a-fragment) für ausführliche Details.

<!--
## Preview based on a HTML Template {#preview-based-on-a-html-template}

The Content Fragment console provides a **Preview** option for every fragment.

The icon can be selected to open a dialog that represents the fragment based on a HTML template. You can use the default template, or develop and load your own.
-->
