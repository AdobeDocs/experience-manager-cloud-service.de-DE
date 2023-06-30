---
title: Einbetten eines adaptiven Formulars in eine AEM Sites-Seite
seo-title: Hwo to add an Adaptive Form to an AEM Sites page?
description: Sie können die „Adaptive Formulare – Einbettungskomponente“ verwenden, um adaptive Formulare zu AEM Sites-Seiten hinzuzufügen oder einzubetten, damit ein Formular ausgefüllt und gesendet werden kann, ohne dass die AEM Sites-Seiten verlassen werden müssen.
feature: Adaptive Forms
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: 2a487654c3af2d2ec3aa43481caed5e1d4fc77a2
workflow-type: ht
source-wordcount: '1154'
ht-degree: 100%

---

# Einbetten eines adaptiven Formulars in eine AEM Sites-Seite {#embed-an-adaptive-form-to-aem-sites-page}

## Übersicht {#overview}

Mit AEM Forms können Formularentwickelnde adaptive Formulare problemlos in eine AEM Sites-Seite oder in eine Web-Seite einbetten, die außerhalb von AEM gehostet wird. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Dies hilft Benutzern, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.



<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

In einer AEM Sites-Seite können Sie ein adaptives Formular mithilfe einer der folgenden Möglichkeiten hinzufügen:

* **Adaptive Formulare – Einbettungskomponente**
Die Einbettungskomponente für adaptive Formulare ermöglicht es AEM Sites-Autoren, ein vorhandenes adaptives Formular in eine AEM Sites-Seite einzuschließen, wodurch die Wiederverwendbarkeit adaptiver Formulare verbessert wird. Vorhandene adaptive Formulare können eigenständig verwendet oder in die Site-Seite eingebettet werden. Diese Integration bietet eine praktische Möglichkeit für Kunden oder Kundinnen, die bereits erstellte adaptiven Formulare wiederzuverwenden.

* **Assets-Browser**
Alle Formulare, die Sie erstellen, sind unter „Assets“ verfügbar. Sie können das Formular als Asset mittels Drag-and-Drop auf Ihrer Seite einfügen.

## Voraussetzungen {#prerequisites}

Wenn Sie ein adaptives Formular in eine AEM Sites-Seite einbetten möchten, die eine bearbeitbare Vorlage verwendet, müssen Sie sicherstellen, dass die AEM Form-Komponente in der zugehörigen Vorlage als zulässige Komponente konfiguriert ist.

Falls **Adaptive Formulare – Einbettungskomponente** im **Komponenten-Browser** der AEM Sites-Seite nicht sichtbar ist, führen Sie die folgenden Schritte wie im Video beschrieben aus.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

Falls eine Sites-Site eine statische Vorlage verwendet, müssen Sie sie im Absatzsystem der Site-Seite konfigurieren.

## Einbetten eines adaptiven Formulars  {#af-component}

So betten Sie ein adaptives Formular mit der **[!UICONTROL Adaptive Formulare – Einbettungskomponente]** ein:

1. Öffnen Sie die AEM Sites-Seite, in die Sie ein adaptives Formular einbetten möchten, im Bearbeitungsmodus.
1. Ziehen Sie die [!UICONTROL Adaptive Formulare – Einbettungskomponente] per Drag-and-Drop aus dem Komponenten-Browser auf die Seite. Alternativ dazu können Sie nach einem adaptiven Formular im Assets-Browser suchen und es dann per Drag-and-Drop auf die Sites-Seite ziehen. Sie können ein neues adaptives Formular hinzufügen oder ein bestehendes adaptives Formular einbetten.

   >[!NOTE]
   >
   >Mehrere „Adaptive Formulare – Einbettungskomponenten“ auf einer Seite werden nicht unterstützt.

1. Um ein neues Formular zu erstellen und einzubetten, tippen Sie in der Komponentensymbolleiste auf das Symbol **Formular erstellen**. Es öffnet sich ein Fenster zum Erstellen des Formulars.

1. Tippen Sie auf die „Adaptive Formulare – Einbettungskomponente“ in der Sites-Seite und tippen Sie dann auf ![settings_icon](assets/settings_icon.png) in der Aktionsleiste. Das Dialogfeld **[!UICONTROL Bearbeiten der „Adaptive Formulare – Einbettungskomponente“]** wird geöffnet.
1. Geben Sie im Dialogfeld „Bearbeiten der ‚Adaptive Formulare – Einbettungskomponente&#39;“ Folgendes an.

   **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets.
   * **Asset-Pfad**: Klicken Sie auf „Durchsuchen“ und wählen Sie das einzubettende adaptive Formular aus. Es wird automatisch ausgefüllt, wenn Sie es über den Assets-Browser eingefügt haben.
   * **Nach dem Senden**: Wählen Sie die Aktion aus, die bei der Formularübermittlung ausgelöst werden soll. Sie können auswählen, dass eine Dankesnachricht oder eine Dankeseite angezeigt werden soll.
      * Anzeigen

      * **Dankesnachricht**: Verfassen Sie im Rich-Text-Editor eine Nachricht, die beim Absenden des Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.
      * **Dankesseite**: Klicken Sie auf „Durchsuchen“ und wählen Sie die Seite aus, die bei Übermittlung eines Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.
         * **Umleiten zur Dankeseite**: Aktivieren Sie die Option, um die Seite mit dem eingebetteten adaptiven Formular durch die Dankeseite zu ersetzen. Andernfalls ersetzt die Dankesseite das adaptive Formular in der [!UICONTROL Adaptive Formulare – Einbettungskomponente], ohne die darunter liegenden Seiten zu aktualisieren. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankeseite angezeigt werden soll.
   * **Seitensprache verwenden**: Verwenden Sie das Gebietsschema der AEM Sites-Seite anstelle des Gebietsschemas des adaptiven Formulars.
   * **Fokus auf Formular festlegen**: Wählen Sie diese Option aus, um den Fokus auf das erste Feld des adaptiven Formulars zu legen.
   * **Design**: Wählen Sie ein Design aus, das die Formatierung für die Komponenten in Ihrem adaptiven Formular definiert. Zur Formatierung gehören Eigenschaften des Erscheinungsbildes, wie Schriftstil, Hintergrundfarbe, Abmessungen und Ausrichtung.
   * **Formular deckt die gesamte Breite des Rahmens ab**: Wenn diese Option aktiviert ist, wird iframe nicht zum Rendern des Formulars verwendet.
   * **Höhe**: Geben Sie die Höhe des Containers an. Lassen Sie es leer, um die Größe des Containers automatisch zu anzupassen.
   * **CSS-Client-Bibliothek**: Geben Sie den Pfad zu einer CSS-Client-Bibliothek an.

1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

AEM Sites ermöglicht Ihnen auch, ein adaptives Formular direkt mithilfe der „Adaptive Formulare – Einbettungskomponente“ zu erstellen. Führen Sie die Schritte aus, um ein adaptives Formular mit der **Adaptive Formulare – Einbettungskomponente** auf der AEM Sites-Seite zu verwenden:
1. Öffnen Sie die AEM Sites-Seite, in die Sie ein adaptives Formular einbetten möchten, im Bearbeitungsmodus.
1. Ziehen Sie die „Adaptive Formulare – Einbettungskomponente“ per Drag-and-Drop aus dem Komponenten-Browser auf die Seite.
1. Klicken Sie auf das **Plus**-Symbol, und Sie werden zum Assistenten für die Formularerstellung weitergeleitet.

   ![Adaptive Formulare – Einbettungskomponente](/help/forms/assets/aemformcontainer.png)

1. Sie können jetzt ein adaptives Formular auf AEM-Webseiten einbetten, indem Sie die [!UICONTROL AEM Forms Container-Komponente] verwenden.

## Veröffentlichen von eingebetteten adaptiven Formularen {#publishing-embedded-adaptive-form}

Betrachten wir die folgenden Szenarien für das Veröffentlichen eines eingebetteten Formulars in einer AEM Sites-Seite:

* Wenn Sie die AEM Sites-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular enthält, veröffentlichen Sie die Sites-Seite und das eingebettete Asset.
* Wenn Sie nur das eingebettete Formular in einer veröffentlichten Sites-Seite geändert haben, veröffentlichen Sie das ursprüngliche Asset, und die Änderungen werden in der veröffentlichten Sites-Seite übernommen. Die veröffentlichte Sites-Seite enthält einen Verweis auf das Asset und erfordert kein erneutes Veröffentlichen der Seite.
* Wenn Sie die Sites-Seite und das eingebettete adaptive Formular geändert haben, veröffentlichen Sie die Sites-Seite und das eingebettete Asset erneut.

## Ändern des eingebetteten adaptiven Formulars  {#modifying-embedded-adaptive-form}

Die AEM Sites-Seite enthält einen Verweis auf das adaptive Formular im Abschnitt „Adaptive Formulare – Einbettungskomponente“. Daher werden alle im ursprünglichen adaptiven Formular konfigurierten Konfigurationen und Eigenschaften (wie Design, Formatierungen und Übermittlungsaktion) im eingebetteten adaptiven Formular beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in adaptiven Formularen im entsprechenden Editor und modifizieren Sie es.
* Tippen Sie von der Sites-Seite aus im Bearbeitungsmodus auf das adaptive Formular und tippen Sie dann auf **[!UICONTROL In neuem Fenster bearbeiten]**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet, sodass Sie es bearbeiten können.

>[!NOTE]
>
>Die im ursprünglichen adaptiven Formular vorgenommenen Änderungen werden automatisch im eingebetteten Formular übernommen. Allerdings müssen Sie das adaptive Formular oder die Sites-Seite erneut veröffentlichen, damit die Änderungen in der veröffentlichten Seite angezeigt werden.

## Aspekte und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM Sites-Seiten einbetten:

* Die Kopf- und Fußzeile im Originalformular sind nicht im eingebetteten Formular enthalten.
* Benutzerentwürfe und -übermittlungen von eingebetteten Formularen werden unterstützt und sind auf den Registerkarten „Entwürfe“und „Gesendete Formulare“ im Formularportal sichtbar.
* Die im Originalformular konfigurierte Übermittlungsaktion wird im eingebetteten Formular beibehalten.
* Wenn Sie für das Originalformular Adobe Analytics konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.
