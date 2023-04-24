---
title: Einbetten eines adaptiven Formulars in eine AEM Sites-Seite
seo-title: Hwo to add an Adaptive Form to an AEM Sites page?
description: Sie können die Komponente Adaptive Forms - Embed verwenden, um Adaptive Forms zu einer AEM Sites-Seite hinzuzufügen oder einzubetten, um ein Formular auszufüllen und zu senden, ohne die AEM Sites-Seiten zu verlassen.
feature: Adaptive Forms
exl-id: 359b05e8-d8c1-4a77-9e70-6f6b6e668560
source-git-commit: 2a487654c3af2d2ec3aa43481caed5e1d4fc77a2
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 63%

---

# Einbetten eines adaptiven Formulars in eine AEM Sites-Seite {#embed-an-adaptive-form-to-aem-sites-page}

## Übersicht {#overview}

Mit AEM Forms können Formularentwickler Adaptive Forms nahtlos in eine AEM Sites-Seite oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Dies hilft Benutzern, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.



<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

In einer AEM Sites-Seite können Sie ein adaptives Formular mithilfe einer der folgenden Möglichkeiten hinzufügen:

* **Adaptives Forms - Einbettungskomponente**
Adaptive Forms - Einbettungskomponente ermöglicht es AEM Sites-Autoren, ein vorhandenes adaptives Formular in eine AEM Sites-Seite einzuschließen, wodurch die Wiederverwendbarkeit adaptiver Formulare verbessert wird. Vorhandene adaptive Forms können eigenständig verwendet oder in die Site-Seite eingebettet werden. Diese Integration bietet eine praktische Möglichkeit für Kunden, die bereits erstellte adaptive Forms wiederzuverwenden.

* **Assets-Browser**
Alle Formulare, die Sie erstellen, sind unter „Assets“ verfügbar. Sie können das Formular als Asset mittels Drag-and-Drop auf Ihrer Seite einfügen.

## Voraussetzungen {#prerequisites}

Wenn Sie ein adaptives Formular in eine AEM Sites-Seite einbetten möchten, die eine bearbeitbare Vorlage verwendet, müssen Sie sicherstellen, dass die AEM Form-Komponente in der zugehörigen Vorlage als zulässige Komponente konfiguriert ist.

In diesem Fall **Adaptives Forms - Einbettungskomponente** ist nicht im **Komponenten-Browser-Bedienfeld** Führen Sie die folgenden Schritte auf AEM Siteseite aus, wie im Video dargestellt.

>[!VIDEO](https://video.tv.adobe.com/v/3410544)

Falls eine Sites-Site eine statische Vorlage verwendet, müssen Sie sie im Absatzsystem der Site-Seite konfigurieren.

## Einbetten eines adaptiven Formulars  {#af-component}

So betten Sie ein adaptives Formular mit dem **[!UICONTROL Adaptives Forms - Einbetten]** component:

1. Öffnen Sie die AEM Sites-Seite, in die Sie ein adaptives Formular einbetten möchten, im Bearbeitungsmodus.
1. Ziehen Sie im Komponenten-Browser-Bedienfeld die [!UICONTROL Adaptives Forms - Einbetten] -Komponente auf der Seite. Alternativ dazu können Sie nach einem adaptiven Formular im Assets-Browser suchen und es dann per Drag-and-Drop auf die Sites-Seite ziehen. Sie können ein neues adaptives Formular hinzufügen oder ein vorhandenes adaptives Formular einbetten.

   >[!NOTE]
   >
   >Mehrere adaptive Forms - Einbettungskomponenten auf einer Seite werden nicht unterstützt.

1. Um ein neues Formular zu erstellen und einzubetten, tippen Sie in der Komponentensymbolleiste auf das Symbol **Formular erstellen**. Ein Fenster zum Erstellen des Formulars wird geöffnet.

1. Tippen Sie auf die eingebettete Komponente Adaptive Forms - Embed auf der Siteseite und dann auf ![settings_icon](assets/settings_icon.png) in der Aktionsleiste. Die **[!UICONTROL Adaptive Forms bearbeiten - Einbetten]** wird geöffnet.
1. Geben Sie im Dialogfeld Adaptive Forms bearbeiten - Einbetten Folgendes an.

   **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets.
   * **Asset-Pfad**: Klicken Sie auf „Durchsuchen“ und wählen Sie das einzubettende adaptive Formular aus. Es wird automatisch ausgefüllt, wenn Sie es über den Assets-Browser eingefügt haben.
   * **Nach dem Senden**: Wählen Sie die Aktion aus, die bei der Formularübermittlung ausgelöst werden soll. Sie können auswählen, dass eine Dankesnachricht oder eine Dankeseite angezeigt werden soll.
      * Anzeigen

      * **Dankesnachricht**: Verfassen Sie im Rich-Text-Editor eine Nachricht, die beim Absenden des Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.
      * **Dankesseite**: Klicken Sie auf „Durchsuchen“ und wählen Sie die Seite aus, die bei Übermittlung eines Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.
         * **Umleiten zur Dankeseite**: Aktivieren Sie die Option, um die Seite mit dem eingebetteten adaptiven Formular durch die Dankeseite zu ersetzen. Andernfalls ersetzt die Dankeseite das adaptive Formular im [!UICONTROL Adaptives Forms - Einbetten] -Komponente, ohne die zugrunde liegenden Sites auf der Seite zu aktualisieren. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankeseite angezeigt werden soll.
   * **Seitensprache verwenden**: Verwenden Sie das Gebietsschema der AEM Sites-Seite anstelle des Gebietsschemas des adaptiven Formulars.
   * **Fokus auf Formular festlegen**: Wählen Sie diese Option aus, um den Fokus auf das erste Feld des adaptiven Formulars zu legen.
   * **Design**: Wählen Sie ein Design aus, das die Formatierung für die Komponenten in Ihrem adaptiven Formular definiert. Zur Formatierung gehören Eigenschaften des Erscheinungsbildes, wie Schriftstil, Hintergrundfarbe, Abmessungen und Ausrichtung.
   * **Das Formular deckt die gesamte Breite des Rahmens ab**: Wenn diese Option aktiviert ist, wird iframe nicht zum Rendern des Formulars verwendet.
   * **Höhe**: Geben Sie die Höhe des Containers an. Lassen Sie es leer, um die Größe des Containers automatisch zu ändern.
   * **CSS-Client-Bibliothek**: Geben Sie den Pfad zu einer CSS-Client-Bibliothek an.

1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

Auf AEM Site können Sie auch direkt mit der Komponente Adaptive Forms - Embed ein adaptives Formular erstellen. Führen Sie die Schritte aus, um ein adaptives Formular mit dem **Adaptives Forms - Einbettungskomponente** auf AEM Siteseite:
1. Öffnen Sie die AEM Sites-Seite, in die Sie ein adaptives Formular einbetten möchten, im Bearbeitungsmodus.
1. Ziehen Sie die Komponente Adaptive Forms - Einbetten aus dem Komponenten-Browser auf die Seite.
1. Klicken Sie auf **Plus** und Sie werden zum Assistenten zur Formularerstellung weitergeleitet.

   ![Adaptives Forms - Einbettungskomponente](/help/forms/assets/aemformcontainer.png)

1. Sie können jetzt ein adaptives Formular mit der Funktion [!UICONTROL AEM Forms-Container-Komponente].

## Veröffentlichen von eingebetteten adaptiven Formularen {#publishing-embedded-adaptive-form}

Betrachten wir die folgenden Szenarien für das Veröffentlichen eines eingebetteten Formulars in einer AEM Sites-Seite:

* Wenn Sie die AEM Sites-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular enthält, veröffentlichen Sie die Sites-Seite und das eingebettete Asset.
* Wenn Sie nur das eingebettete Formular in einer veröffentlichten Sites-Seite geändert haben, veröffentlichen Sie das ursprüngliche Asset, und die Änderungen werden in der veröffentlichten Sites-Seite übernommen. Die veröffentlichte Sites-Seite enthält einen Verweis auf das Asset und erfordert kein erneutes Veröffentlichen der Seite.
* Wenn Sie die Sites-Seite und das eingebettete adaptive Formular geändert haben, veröffentlichen Sie die Sites-Seite und das eingebettete Asset erneut.

## Ändern des eingebetteten adaptiven Formulars  {#modifying-embedded-adaptive-form}

AEM Siteseite behält einen Verweis auf das adaptive Formular im adaptiven Forms - Einbetten bei. Daher werden alle im ursprünglichen adaptiven Formular konfigurierten Konfigurationen und Eigenschaften (wie Design, Formatierungen und Übermittlungsaktion) im eingebetteten adaptiven Formular beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in adaptiven Formularen im entsprechenden Editor und modifizieren Sie es.
* Tippen Sie von der Sites-Seite aus im Bearbeitungsmodus auf das adaptive Formular und tippen Sie dann auf **[!UICONTROL In neuem Fenster bearbeiten]**. Das ursprüngliche Formular wird im Bearbeitungsmodus geöffnet, sodass Sie es bearbeiten können.

>[!NOTE]
>
>Die im ursprünglichen adaptiven Formular vorgenommenen Änderungen werden automatisch im eingebetteten Formular übernommen. Allerdings müssen Sie das adaptive Formular oder die Sites-Seite erneut veröffentlichen, damit die Änderungen in der veröffentlichten Seite angezeigt werden.

## Aspekte und Best Practices {#considerations-and-best-practices}

Beachten Sie die folgenden Punkte, wenn Sie adaptive Formulare in AEM Sites-Seiten einbetten:

* Die Kopf- und Fußzeile im Originalformular sind nicht im eingebetteten Formular enthalten.
* Benutzerentwürfe und -übermittlungen von eingebetteten Formularen werden unterstützt und sind auf den Registerkarten &quot;Entwürfe&quot;und &quot;Gesendete Forms&quot;im Forms-Portal sichtbar.
* Die im Originalformular konfigurierte Sendeaktion wird im eingebetteten Formular beibehalten.
* Wenn Sie für das Originalformular Adobe Analytics konfiguriert haben, werden die Analysedaten des eingebetteten Formulars in Adobe Analytics erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.
