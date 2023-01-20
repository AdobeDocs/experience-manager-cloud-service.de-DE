---
title: Einbetten eines adaptiven Formulars in eine AEM Sites-Seite
seo-title: Hwo to add an Adaptive Form to an AEM Sites page?
description: Sie können die Container-Komponente von AEM Forms verwenden, um adaptive Formulare zu AEM Sites-Seiten hinzuzufügen oder einzubetten, damit ein Formular ausgefüllt und gesendet werden kann, ohne dass die AEM Sites-Seiten verlassen werden müssen.
feature: Adaptive Forms
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: 51d7198ccf24ca0b46c4e4a34cb1d1ee8ed7e2c0
workflow-type: ht
source-wordcount: '1178'
ht-degree: 100%

---

# Einbetten eines adaptiven Formulars in eine AEM Sites-Seite {#embed-an-adaptive-form-to-aem-sites-page}

## Übersicht {#overview}

Mit AEM Forms können Formularentwickler nahtlos adaptive Formulare in eine AEM Sites-eite oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Dies hilft Benutzern, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

In einer AEM Sites-Seite können Sie ein adaptives Formular mithilfe einer der folgenden Möglichkeiten hinzufügen:

* **AEM Forms-Container-Komponente**
AEM Forms stellt eine Komponente bereit, die Sie Ihren Sites-Seiten hinzufügen können. Über die AEM Forms-Container-Komponente können Sie ein adaptives Formular einbetten.

* **Assets-Browser**
Alle Formulare, die Sie erstellen, sind unter „Assets“ verfügbar. Sie können das Formular als Asset mittels Drag-and-Drop auf Ihrer Seite einfügen.

## Voraussetzungen {#prerequisites}

Wenn Sie ein adaptives Formular in eine AEM Sites-Seite einbetten möchten, die eine bearbeitbare Vorlage verwendet, müssen Sie sicherstellen, dass die AEM Form-Komponente in der zugehörigen Vorlage als zulässige Komponente konfiguriert ist.

Falls die **Container-Komponente von AEM Forms** im **Komponenten-Browser-Fenster** der AEM Sites-Seite nicht sichtbar ist, führen Sie die folgenden Schritte wie im Video beschrieben aus.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

Falls eine Sites-Site eine statische Vorlage verwendet, müssen Sie sie im Absatzsystem der Site-Seite konfigurieren.

## Einbetten eines adaptiven Formulars  {#af-component}

Einbetten eines adaptiven Formulars mithilfe der AEM Forms-Container-Komponente:

1. Öffnen Sie die AEM Sites-Seite, in die Sie ein adaptives Formular einbetten möchten, im Bearbeitungsmodus.
1. Ziehen Sie die AEM Forms-Container-Komponente aus dem Komponenten-Browser auf die Seite. Alternativ dazu können Sie nach einem adaptiven Formular im Assets-Browser suchen und es dann per Drag-and-Drop auf die Sites-Seite ziehen. Dadurch wird das Formular in einen AEM Forms-Container eingebettet. Sie können ein neues adaptives Formular erstellen und hinzufügen oder ein vorhandenes adaptives Formular einbetten.

   >[!NOTE]
   >
   >Mehrere AEM Forms-Container-Komponenten auf einer Seite werden nicht unterstützt.

1. Um ein neues Formular zu erstellen und einzubetten, tippen Sie in der Komponentensymbolleiste auf das Symbol **Formular erstellen**. Ein Fenster zum Erstellen des neuen Formulars wird geöffnet.

1. Tippen Sie auf die eingebettete AEM Forms-Container-Komponente in der Sites-Seite und tippen Sie dann auf ![settings_icon](assets/settings_icon.png) in der Aktionsleiste. Das Dialogfeld **[!UICONTROL AEM Forms-Container bearbeiten]** wird geöffnet.
1. Geben Sie im Dialogfeld „AEM Forms-Container bearbeiten“ Folgendes an.

   **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets.
   * **Asset-Pfad**: Klicken Sie auf „Durchsuchen“ und wählen Sie das einzubettende adaptive Formular aus. Es wird automatisch ausgefüllt, wenn Sie es über den Assets-Browser eingefügt haben.
   * **Nach dem Senden**: Wählen Sie die Aktion aus, die bei der Formularübermittlung ausgelöst werden soll. Sie können auswählen, dass eine Dankesnachricht oder eine Dankeseite angezeigt werden soll.
      * Anzeigen

      * **Dankesnachricht**: Verfassen Sie im Rich-Text-Editor eine Nachricht, die beim Absenden des Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.
      * **Dankesseite**: Klicken Sie auf „Durchsuchen“ und wählen Sie die Seite aus, die bei Übermittlung eines Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.
         * **Umleiten zur Dankeseite**: Aktivieren Sie die Option, um die Seite mit dem eingebetteten adaptiven Formular durch die Dankeseite zu ersetzen. Andernfalls ersetzt die Dankeseite das adaptive Formular im AEM Forms-Container, ohne dass die Seite aktualisiert wird. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankeseite angezeigt werden soll.
   * **Seitensprache verwenden**: Verwenden Sie das Gebietsschema der AEM Sites-Seite anstelle des Gebietsschemas des adaptiven Formulars.
   * **Fokus auf Formular festlegen**: Wählen Sie diese Option aus, um den Fokus auf das erste Feld des adaptiven Formulars zu legen.
   * **Design**: Wählen Sie ein Design aus, das die Formatierung für die Komponenten in Ihrem adaptiven Formular definiert. Zur Formatierung gehören Eigenschaften des Erscheinungsbildes, wie Schriftstil, Hintergrundfarbe, Abmessungen und Ausrichtung.
   * **Formular deckt die gesamte Breite des Rahmens ab**: Wenn diese Option aktiviert ist, wird iframe nicht zum Rendern des Formulars verwendet.
   * **Höhe**: Geben Sie die Höhe des Containers an. Lassen Sie sie leer, um die Größe des Containers automatisch anzupassen.
   * **CSS-Client-Bibliothek**: Geben Sie den Pfad zu einer CSS-Client-Bibliothek an.

1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

AEM Sites ermöglicht Ihnen auch, ein adaptives Formular direkt mithilfe der Container-Komponente für AEM Forms zu erstellen. Führen Sie die Schritte aus, um ein adaptives Formular mit einer **Container-Komponente für AEM Forms** auf der AEM Sites-Seite zu verwenden:
1. Öffnen Sie die AEM Sites-Seite, in die Sie ein adaptives Formular einbetten möchten, im Bearbeitungsmodus.
1. Ziehen Sie die AEM Forms-Container-Komponente aus dem Komponenten-Browser auf die Seite.
1. Klicken Sie auf das **Plus**-Symbol, und Sie werden zum Assistenten für die Formularerstellung weitergeleitet.

   ![Container-Komponente für AEM-Formular](/help/forms/assets/aemformcontainer.png)

1. Wenn ein adaptives Formular erstellt wird, werden Sie zur AEM Sites-Seite weitergeleitet und das erstellte Formular wird auf der AEM Sites-Seite gerendert.

## Veröffentlichen von eingebetteten adaptiven Formularen {#publishing-embedded-adaptive-form}

Betrachten wir die folgenden Szenarien für das Veröffentlichen eines eingebetteten Formulars in einer AEM Sites-Seite:

* Wenn Sie die AEM Sites-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular enthält, veröffentlichen Sie die Sites-Seite und das eingebettete Asset.
* Wenn Sie nur das eingebettete Formular in einer veröffentlichten Sites-Seite geändert haben, veröffentlichen Sie das ursprüngliche Asset, und die Änderungen werden in der veröffentlichten Sites-Seite übernommen. Die veröffentlichte Sites-Seite enthält einen Verweis auf das Asset und erfordert kein erneutes Veröffentlichen der Seite.
* Wenn Sie die Sites-Seite und das eingebettete adaptive Formular geändert haben, veröffentlichen Sie die Sites-Seite und das eingebettete Asset erneut.

## Ändern des eingebetteten adaptiven Formulars  {#modifying-embedded-adaptive-form}

Die AEM Sites-Seite behält den Verweis auf das adaptive Formular im AEM Forms-Container bei. Daher werden alle im ursprünglichen adaptiven Formular konfigurierten Konfigurationen und Eigenschaften (wie Design, Formatierungen und Übermittlungsaktion) im eingebetteten adaptiven Formular beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in adaptiven Formularen im entsprechenden Editor und modifizieren Sie es.
* Tippen Sie von der Sites-Seite aus im Bearbeitungsmodus auf das adaptive Formular und tippen Sie dann auf **[!UICONTROL In neuem Fenster bearbeiten]**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet, sodass Sie es bearbeiten können.

>[!NOTE]
>
>Die im ursprünglichen adaptiven Formular vorgenommenen Änderungen werden automatisch im eingebetteten Formular übernommen. Allerdings müssen Sie das adaptive Formular oder die Sites-Seite erneut veröffentlichen, damit die Änderungen in der veröffentlichten Seite angezeigt werden.

## Aspekte und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM Sites-Seiten einbetten:

* Die Kopf- und Fußzeile im Originalformular werden im eingebetteten Formular nicht übernommen.
* Benutzerentwürfe und Übermittlungen von eingebetteten Formularen werden unterstützt und sind auf der entsprechenden Registerkarte im Forms Portal sichtbar.
* Die im Originalformular konfigurierte Aktion wird im eingebetteten Formular beibehalten.
* Die im Originalformular konfigurierten Erlebnis-Targeting und A/B-Tests funktionieren im eingebetteten Formular nicht. Sie können jedoch Erlebnis-Targeting auf der Siteseite verwenden, um verschiedene Formular je nach Benutzerprofil darzustellen.
* Wenn Sie für das Originalformular Adobe Analytics konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.
