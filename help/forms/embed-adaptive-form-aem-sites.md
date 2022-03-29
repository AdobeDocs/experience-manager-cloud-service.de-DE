---
title: 'Wie wird ein adaptives Formular in eine AEM Sites-Seite eingebettet? '
description: Sie können adaptive Formulare in AEM Sites-Seiten einbetten. Benutzer können Formulare ausfüllen und senden, ohne die Sites-Seiten zu verlassen.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '949'
ht-degree: 100%

---


# Einbetten eines adaptiven Formulars in eine AEM Sites-Seite {#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-page}

Mit [!DNL AEM Forms] können Formularentwickler adaptive Formulare problemlos in eine AEM Sites-Seite oder in eine Web-Seite einbetten, die außerhalb von AEM gehostet wird. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzer können es ausfüllen und senden, ohne die Seite zu verlassen. Dies hilft Benutzern, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

<!-- For information about embedding an Adaptive Form in an external web page, see [Embed Adaptive Form in external web page](/help/forms/using/embed-adaptive-form-external-web-page.md). -->

In einer AEM Sites-Seite können Sie ein adaptives Formular mithilfe einer der folgenden beiden Möglichkeiten hinzufügen:

* **[[!DNL AEM Forms] Container-Komponente](#af-component)**
   [!DNL AEM Forms] stellt eine Komponente bereit, die Sie den Site-Seiten hinzufügen können. Über die [!DNL AEM Forms]-Container-Komponente können Sie ein adaptives Formular einbetten.

* **[Assets-Browser](/help/forms/using/embed-adaptive-form-aem-sites.md#asset-browser)**
Alle Formulare, die Sie erstellen, sind unter „Assets“ verfügbar. Sie können das Formular als Asset mittels Drag-and-Drop auf Ihrer Seite einfügen.

## Voraussetzungen {#prerequisites}

Wenn Sie ein adaptives Formular in eine AEM Sites-Seite einbetten möchten, die eine bearbeitbare Vorlage verwendet, müssen Sie sicherstellen, dass die AEM Forms-Komponente in der zugehörigen Vorlage als zulässige Komponente konfiguriert ist. Weitere Informationen finden Sie im Abschnitt **Richtlinie und Eigenschaften (Layout-Container)** unter [Erstellen von Seitenvorlagen](/help/sites-authoring/templates.md).

Falls eine Sites-Seite eine statische Vorlage verwendet, müssen Sie sie im Absatzsystem der Seite konfigurieren. Weitere Informationen finden Sie unter [Konfigurieren von Komponenten im Designmodus](/help/sites-authoring/default-components-designmode.md).

## Einbetten eines adaptiven Formulars   {#af-component}

Einbetten eines adaptiven Formulars mithilfe der [!DNL AEM Forms]-Container-Komponente:

1. Öffnen Sie die AEM Sites-Seite, in die Sie ein adaptives Formular einbetten möchten, im Bearbeitungsmodus.
1. Ziehen Sie die [!DNL AEM Forms]-Container-Komponente aus dem Komponenten-Browser auf die Seite.

   Alternativ dazu können Sie nach einem adaptiven Formular im Assets-Browser suchen und es dann per Drag-and-Drop auf die Sites-Seite ziehen. Dadurch wird das Formular in einen [!DNL AEM Forms]-Container eingebettet.

   >[!NOTE]
   >
   >Mehrere [!DNL AEM Forms]-Container-Komponenten auf einer Seite werden nicht unterstützt.

1. Tippen Sie auf die eingebettete [!DNL AEM Forms]-Container-Komponente in der Sites-Seite und tippen Sie dann in der Aktionsleiste auf ![settings_icon](assets/settings_icon.png). Das Dialogfeld **[!UICONTROL AEM Forms-Container bearbeiten]** wird geöffnet.
1. Geben Sie im Dialogfeld „[!DNL AEM Forms]-Container bearbeiten“ Folgendes an.

   * **Asset-Typ:** Wählen Sie den Typ des einzubettenden Assets. Die Option lautet „Adaptives Formular“.
   * **Asset-Pfad**: Klicken Sie auf „Durchsuchen“ und wählen Sie das einzubettende adaptive Formular aus. Es wird automatisch ausgefüllt, wenn Sie es über den Assets-Browser eingefügt haben.
   * (Nur adaptives Formular) **Nach dem Senden**: Wählen Sie die Aktion aus, die bei der Formularübermittlung ausgelöst werden soll. Sie können auswählen, dass eine Dankesnachricht oder eine Dankesseite angezeigt werden soll.

      * **Dankesnachricht**: Verfassen Sie im Rich-Text-Editor eine Nachricht, die beim Absenden des Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesnachricht angezeigt werden soll.
      * **Dankesseite**: Klicken Sie auf „Durchsuchen“ und wählen Sie die Seite aus, die bei Übermittlung eines Formulars angezeigt werden soll. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.
      * **Seite beim Senden aktualisieren**: Aktivieren Sie diese Option, um die Seite mit dem eingebetteten adaptiven Formular zu aktualisieren, sodass die Dankesseite angezeigt wird. Andernfalls ersetzt die Dankesseite das adaptive Formular im [!DNL AEM Forms]-Container, ohne dass die Seite aktualisiert wird. Diese Option steht nur zur Verfügung, wenn Sie ausgewählt haben, dass eine Dankesseite angezeigt werden soll.
   * **Design**: Wählen Sie ein Design aus, das die Formatierung für die Komponenten in Ihrem adaptiven Formular definiert. Zur Formatierung gehören Eigenschaften des Erscheinungsbildes, wie Schriftschnitt, Hintergrundfarbe, Abmessungen und Ausrichtung.
   * **Höhe**: Geben Sie die Höhe des Containers an. Lassen Sie sie leer, um die Größe des Containers automatisch anzupassen.
   * **CSS-Client-Bibliothek**: Geben Sie den Pfad zu einer CSS-Client-Bibliothek an.


1. Speichern Sie die Einstellungen. Das adaptive Formular ist jetzt in der Seite eingebettet.

## Veröffentlichen von eingebetteten adaptiven Formularen {#publishing-embedded-adaptive-form}

Betrachten wir die folgenden Szenarien für das Veröffentlichen eines eingebetteten Assets (eingebettetes Formular) in einer AEM Sites-Seite:

* Wenn Sie die AEM Sites-Seite zum ersten Mal veröffentlichen und sie ein eingebettetes adaptives Formular enthält, veröffentlichen Sie die Sites-Seite und das eingebettete Asset.
* Wenn Sie nur das eingebettete Formular in einer veröffentlichten Sites-Seite geändert haben, veröffentlichen Sie das ursprüngliche Asset, und die Änderungen werden in der veröffentlichten Sites-Seite übernommen. Die veröffentlichte Sites-Seite enthält einen Verweis auf das Asset und erfordert kein erneutes Veröffentlichen der Seite.
* Wenn Sie die Sites-Seite und das eingebettete adaptive Formular geändert haben, veröffentlichen Sie die Sites-Seite und das eingebettete Asset erneut.

## Ändern des eingebetteten adaptiven Formulars {#modifying-embedded-adaptive-form-and-interactive-communication}

Die AEM Sites-Seite behält den Verweis auf das adaptive Formular im [!DNL AEM Forms]-Container bei. Daher werden alle im ursprünglichen adaptiven Formular konfigurierten Konfigurationen und Eigenschaften (wie Design, Formatierungen und Übermittlungsaktion) im eingebetteten adaptiven Formular beibehalten.

Um eine Konfiguration oder Eigenschaft des eingebetteten adaptiven Formulars zu ändern, führen Sie einen der folgenden Schritte aus.

* Öffnen Sie das Originalformular in adaptiven Formularen im entsprechenden Editor und modifizieren Sie sie.
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

