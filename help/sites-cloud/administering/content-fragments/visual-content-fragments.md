---
title: Visual Content Fragments
description: Erfahren Sie, wie Sie visuelle Inhaltsfragmente mithilfe von HTML-Vorlagen visualisieren und veröffentlichen.
feature: Content Fragments
role: User, Developer
source-git-commit: 19931f7cc911376f5096903a2d99d6ff11f928ac
workflow-type: tm+mt
source-wordcount: '1047'
ht-degree: 0%

---

# Visual Content Fragments {#visual-content-fragments}

Inhaltsfragmente enthalten strukturierten Inhalt, der für die JSON-Ausgabe ohne Design oder Layout vorgesehen ist. Durch das Hinzufügen von HTML-Vorlagen können Sie vollständig dekorierte visuelle Erlebnisse mit strukturierten Inhalten im HTML-Format erstellen:

* Die Visualisierung eines Inhaltsfragments hilft bei der Qualitätssicherung von Inhalten, sodass Stakeholder Inhalte vor der Verwendung überprüfen können, ohne den Inhaltsfragment-Editor öffnen zu müssen

* Die Bereitstellung eines visuellen Fragments unterstützt die Omni-Channel-Bereitstellung und ermöglicht die Wiederverwendung modularer Erlebnisse in Kanälen wie Web, E-Mail oder Mobile Apps.

Die gerenderte Ausgabe eines AEM-Inhaltsfragments, das das Layout und Design einer angehängten HTML-Vorlage verwendet, wird als &quot;*Inhaltsfragment“*.

HTML-Vorlagen enthalten Layout- und Design-Informationen, die die Visualisierung von Inhaltsfragmenten ermöglichen. Die Verbindung zwischen einer Vorlage und einem Inhaltsfragment wird mithilfe der Handlebars-Syntax hergestellt, um HTML-Tags den im Inhaltsfragmentmodell definierten Datentypen (Feldern) zuzuordnen. Diese Definition ermöglicht die Anzeige von Inhalten, die in den entsprechenden Feldern des Inhaltsfragment-Editors erstellt wurden, an den entsprechenden Stellen innerhalb der Vorlage.

Sie oder Ihr Entwicklungs-Team können [Ihre eigenen HTML-Vorlagen erstellen und anpassen](/help/implementing/developing/extending/content-fragments-visualization-templates.md) und dann [eines oder mehrere von ihnen hochladen und an Inhaltsfragmentmodelle anhängen](#upload-and-assign-your-template) sodass die entsprechenden Fragmente in Erlebnisse gerendert, [in der Vorschau angezeigt](#preview-your-fragment-with-a-template) und nach Bedarf [ bereitgestellt werden können](#deliver-your-visual-content-fragment).

>[!NOTE]
>
>Eine **generische Vorlage** ist standardmäßig immer in AEM verfügbar und mit jedem Modell verknüpft. Diese Vorlage ermöglicht die Anzeige von Schlüssel/Wert-Paaren in strukturierten Inhalten in einem sauberen, tabellenartigen Format, um Anwendungsfälle für Content Quality Assurance (QA) zu unterstützen.

## Erstellen einer Vorlage {#create-a-template}

Mit Handlebars entwickelte HTML-Vorlagen ermöglichen die Vorschau und Bereitstellung visueller Inhaltsfragmente im HTML-Format. Die Handlebars.js-Syntax definiert Platzhalter für Inhalte, die in Inhaltsfragmentfeldern verfasst werden.

Einzelheiten zum Entwickeln eigener Vorlagen finden Sie unter [Visual Content Fragments - Vorlagen](/help/implementing/developing/extending/content-fragments-visualization-templates.md).

## Hochladen und Zuweisen Ihrer Vorlage {#upload-and-assign-your-template}

Eine Vorlage ist mit einem Inhaltsfragmentmodell verknüpft, sodass sie mit allen Inhaltsfragmenten verwendet werden kann, die aus diesem Modell erstellt wurden.

Hochladen der neuen HTML-Vorlage:

1. Öffnen Sie in der Inhaltsfragmentkonsole die Registerkarte für **Inhaltsfragmentmodelle**.
1. Navigieren Sie zum Speicherort Ihres Fragmentmodells.
1. Wählen Sie das Informationssymbol (i) für das gewünschte Modell aus:

   ![Inhaltsfragmentkonsole - Informationssymbol](/help/sites-cloud/administering/content-fragments/assets/cfc-information-icon.png)

   Das rechte Bedienfeld wird angezeigt.
1. Scrollen Sie nach unten, um **HTML** Vorlagen anzuzeigen. Die **Generische Vorlage** wird bereits als Standard aufgeführt:

   ![Vorschau eines Fragments mit einer generischen HTML-Vorlage](/help/sites-cloud/administering/content-fragments/assets/cf-visual-html-template-configure-default.png)

1. Wählen Sie **+** aus, um Ihre Vorlage aus einer HTML-Datei (`.html`) hochzuladen. In einem Dialogfeld können Sie **lokale Dateisystem durchsuchen** Ihre Vorlagendatei auswählen.
1. Nach dem Hochladen werden zwei Ansichten der Vorlage angezeigt, die Sie überprüfen können:

   * Links: Darstellung der Vorlage ohne Inhalt
   * Rechts: der HTML-Code, der hier auch bearbeitet werden kann, bevor er in AEM importiert wird

   ![HTML-Vorlage beim Hochladen überprüfen](/help/sites-cloud/administering/content-fragments/assets/cf-visual-html-template-upload-review.png)

1. Wählen Sie **Weiter**, um fortzufahren.
1. Geben Sie einen **Vorlagennamen** zur Verwendung in AEM ein.
1. Bestätigen Sie mit **Vorlage erstellen**.
1. Die Vorlage wird in AEM erstellt und unter **HTML-Vorlagen** in den Eigenschaften von Inhaltsfragmentmodellen aufgeführt.
Nach dem Laden kann sie für die [Vorschau von Fragmenten) ](#preview-your-fragment-with-a-template) werden. Sie können die Vorlage auch **[Herunterladen](#download-your-template)** oder **[Löschen](#download-your-template)**.

## Vorschau eines Fragments mit einer Vorlage {#preview-your-fragment-with-a-template}

So zeigen Sie eine Vorschau Ihres Inhaltsfragments mithilfe einer Vorlage an:

>[!NOTE]
>
>Da die **generische Vorlage** immer verfügbar ist, können Sie eine Vorschau des Fragments anzeigen, ohne benutzerdefinierte Vorlagen zu laden.

1. Navigieren Sie in der Inhaltsfragmentkonsole zum Speicherort des gewünschten Fragments.

1. Sie haben folgende Möglichkeiten:
   * Wählen Sie Ihr Fragment in der Konsole aus
   * Fragment im Editor öffnen

1. Wählen **Vorschau** in der oberen Symbolleiste von aus:

   * die Inhaltsfragmentkonsole
   * im Editor, in dem Sie dann „Vorlage **auswählen**

In beiden Fällen wird ein neues modales Fenster geöffnet.

1. Wenn keine benutzerdefinierten Vorlagen verfügbar sind, verwendet AEM die **Generische Vorlage** um Ihr Fragment anzuzeigen. Die **generische Vorlage**:

   * Zeigt die Felder des Fragments in Tabellenform, Name und Inhalt an
   * Zeigt den vollständig hydrierten Inhalt referenzierter Fragmente in derselben Ansicht

1. Wenn benutzerdefinierte Vorlagen verfügbar sind, können Sie die gewünschte Vorlage auswählen (einschließlich der &quot;**Vorlage**).

1. Wenn das Inhaltsfragment veröffentlicht ist, können Sie auch seine **Vorschau-URL** und **Veröffentlichungs-URL** anzeigen und kopieren.

Beispielsweise die Vorschau mit der **generischen Vorlage**:

![Vorschau eines Fragments mit einer generischen HTML-Vorlage](/help/sites-cloud/administering/content-fragments/assets/cf-visual-html-template-referenced-fragment.png)

## Bereitstellen des visuellen Inhaltsfragments {#deliver-your-visual-content-fragment}

Das visuelle Inhaltsfragment kann an eine Reihe von Zielen im HTML-Format bereitgestellt werden.

### An den Browser senden {#deliver-to-the-browser}

Kopieren Sie die **Vorschau-URL** oder die **Veröffentlichungs-URL**. Greifen Sie darauf direkt über Ihren Browser zu, um Ihr visuelles Inhaltsfragment zu sehen.

### An Edge Delivery Services senden {#deliver-to-edge-delivery-services}

Sie können Ihr visuelles Fragment auf einer Edge Delivery Service (EDS)-Seite bereitstellen.

1. Navigieren Sie zu Ihrem EDS-Projekt.
1. Fügen Sie einen (Block **[des ](https://www.aem.live/developer/block-collection)** (**[) hinzu oder greifen Sie ](https://sidekick-library--aem-block-collection--adobe.aem.page/tools/sidekick/library.html?plugin=blocks&path=/block-collection/embed&index=0)**.
1. Fügen Sie die **Veröffentlichungs-URL** in den Block ein.
1. Veröffentlichen Sie Ihre EDS-Seite. Die HTML-Darstellung Ihres Fragments wird angezeigt.

>[!NOTE]
>
>Ausführliche Informationen finden Sie unter [Integration mit Edge Delivery Services (Einbettungsblock)](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#integration-with-edge-services-embed-block)

### An AEM senden {#deliver-to-an-AEM-page}

Sie können Ihr visuelles Inhaltsfragment auf einer AEM-Seite mithilfe der Kernkomponente bereitstellen: Inhaltsfragment.

Beim Konfigurieren einer **Inhaltsfragment**-Komponente [ Ihrer Seite](/help/sites-cloud/authoring/fragments/content-fragments.md#adding-a-content-fragment-to-your-page):

1. Geben Sie das erforderliche **Inhaltsfragment** an.
1. Wählen Sie **Inhaltsfragmentvisualisierung** aus.
1. Wählen Sie die gewünschte **Visualisierungsvorlage** aus der Dropdown-Liste aus.

   ![Konfigurieren der Inhaltsfragmentkomponente für ein visuelles Fragment](/help/sites-cloud/administering/content-fragments/assets/cf-visual-template-aem-page.png)

1. Das visuelle Fragment wird auf der Seite angezeigt.

>[!NOTE]
>
>Ausführliche Informationen finden Sie unter [Integration - AEM Sites mit Kernkomponenten](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#integration-aem-sites-with-core-components)

## Vorlage herunterladen {#download-your-template}

So laden Sie Ihre HTML-Vorlage von AEM herunter:

1. Öffnen Sie in der Inhaltsfragmentkonsole die Registerkarte für **Inhaltsfragmentmodelle**.
1. Navigieren Sie zum Speicherort Ihres Fragmentmodells.
1. Wählen Sie das Informationssymbol (i) für das gewünschte Modell aus:

   ![Inhaltsfragmentkonsole - Informationssymbol](/help/sites-cloud/administering/content-fragments/assets/cfc-information-icon.png)

   Das rechte Bedienfeld wird angezeigt.

1. Scrollen Sie nach unten, um **HTML-Vorlagen anzuzeigen**.
1. Wählen Sie die Auslassungszeichen nach der Vorlage aus, die Sie herunterladen möchten.
1. Wählen Sie **Herunterladen** aus.
1. Geben Sie den Dateinamen und den Speicherort an.
1. Bestätigen Sie mit **Speichern**.

## Vorlage löschen {#delete-your-template}

So löschen Sie Ihre neue HTML-Vorlage (aus AEM):

1. Öffnen Sie in der Inhaltsfragmentkonsole die Registerkarte für **Inhaltsfragmentmodelle**.
1. Navigieren Sie zum Speicherort Ihres Fragmentmodells.
1. Wählen Sie das Informationssymbol (i) für das gewünschte Modell aus:

   ![Inhaltsfragmentkonsole - Informationssymbol](/help/sites-cloud/administering/content-fragments/assets/cfc-information-icon.png)

   Das rechte Bedienfeld wird angezeigt.
1. Scrollen Sie nach unten, um **HTML-Vorlagen anzuzeigen**.
1. Wählen Sie die Auslassungszeichen nach der Vorlage aus, die Sie herunterladen möchten.
1. Wählen Sie **Löschen** aus.
1. Bestätigen Sie die Aktion im folgenden Dialogfeld mit **Löschen**.
