---
title: Zugehörige Assets
description: Erfahren Sie, wie Sie Assets mit bestimmten gemeinsamen Attributen verknüpfen. Mit der Funktion können Sie außerdem Quellbeziehungen/abgeleitete Beziehungen zwischen Assets erstellen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Related assets {#related-assets}

Mit Adobe Experience Manager (AEM) Assets können Sie Assets manuell entsprechend den Anforderungen Ihres Unternehmens zuordnen. Verwenden Sie hierfür die Funktion „Zugehörige Assets“. Beispielsweise können Sie einem Asset oder einem Bild/Video eine Lizenzdatei zu einem ähnlichen Thema zuordnen. Sie können Assets zuordnen, die bestimmte gängige Attribute teilen. Mit der Funktion können Sie außerdem Quellbeziehungen/abgeleitete Beziehungen zwischen Assets erstellen. Beispielsweise können Sie PDF-Dateien, die aus einer INDD-Datei generiert wurden, der INDD-Quelldatei zuordnen.

Auf diese Weise haben Sie die Flexibilität, Dateien mit niedriger Auflösung (z. B. PDF/JPG) mit Mitarbeitern/Agenturen zu teilen und die Datei mit hoher Auflösung (z. B. INDD) nur auf Anfrage zur Verfügung zu stellen.

## Relate assets {#relating-assets}

1. Öffnen Sie in der Benutzeroberfläche von Assets die Eigenschaftenseite für ein Asset, das Sie zuordnen möchten. Wählen Sie alternativ das gewünschte Asset in der Liste aus. Sie können das Asset auch aus einer Sammlung auswählen.
1. Um dem ausgewählten Asset ein anderes Asset zuzuordnen, klicken/tippen Sie in der Symbolleiste auf das Symbol für **[!UICONTROL Zuordnen]**.
1. Führen Sie einen der folgenden Schritte aus:

   * Um die Quelldatei des Elements zuzuordnen, wählen Sie **[!UICONTROL Quelle]** aus der Liste aus.
   * To relate a derived file, select **[!UICONTROL Derived]** from the list.
   * Um eine Zweiwege-Beziehung zwischen den Assets zu erstellen, wählen Sie **[!UICONTROL Andere]** aus der Liste aus.

1. Navigieren Sie im Bildschirm **[!UICONTROL Assets auswählen]** zum Speicherort des Elements, das Sie zuordnen möchten, und wählen Sie es aus.

1. Klicken/tippen Sie auf das Symbol **[!UICONTROL Bestätigen]**.
1. Click/tap **[!UICONTROL OK]** to close the dialog. Je nach Auswahl der Beziehung in Schritt 3 wird das zugeordnete Asset unter einer entsprechenden Kategorie im Abschnitt **[!UICONTROL Zugehörig]** aufgeführt. Beispiel: Wenn das zugeordnete Asset die Quelldatei des aktuellen Elements ist, wird es unter **[!UICONTROL Quelle]** aufgeführt.
1. Um die Zuordnung eines Elements aufzuheben, klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Bezug aufheben]**.
1. Wählen Sie die Assets aus, deren Bezug zum Dialogfeld **[!UICONTROL Beziehungen entfernen]** Sie aufheben möchten, und klicken/tippen Sie auf **[!UICONTROL Bezug aufheben]**.
1. Klicken/tippen Sie auf **[!UICONTROL OK]**, um das Dialogfeld zu schließen. Die Assets, für die Sie Verbindungen entfernt haben, werden aus der Liste der zugeordneten Assets im Abschnitt **[!UICONTROL Zugehörig]** gelöscht.

## Übersetzen verwandter Assets {#translating-related-assets}

Für die Übersetzungs-Workflows ist die Erstellung von Quellbeziehungen/abgeleiteten Beziehungen zwischen Assets mit der Funktion „Zugehörige Assets“ nützlich. Wenn Sie für ein abgeleitetes Asset einen Übersetzungs-Workflow ausführen, ruft AEM Assets automatisch beliebige Assets ab, die von der Quelldatei referenziert werden, und nimmt sie in die Übersetzung auf. Auf diese Weise wird das vom Quell-Asset referenzierte Asset zusammen mit dem Quell-Asset und den abgeleiteten Assets übersetzt. Beispiel: In einem Szenario enthält die Kopie in englischer Sprache ein abgeleitetes Asset und die entsprechende Quelldatei wie gezeigt.

Wenn die Quelldatei mit einem anderen Asset verknüpft ist, ruft AEM Assets das referenzierte Asset ab und nimmt es zur Übersetzung auf.

1. Übersetzen Sie die Assets im Quellordner für eine Zielsprache, indem Sie die Schritte unter [Neues Übersetzungsprojekt erstellen](/help/assets/translate-assets.md#create-a-new-translation-project) befolgen. Übersetzen Sie in diesem Fall zum Beispiel Ihre Assets ins Französische.
1. Öffnen Sie auf der Seite „Projekte“ den Übersetzungsordner.
1. Klicken/tippen Sie auf die Projektkachel, um die Seite mit den Details zu öffnen.
1. Klicken/tippen Sie auf die Auslassungszeichen unter der Karte „Übersetzungsauftrag“, um den Übersetzungsstatus anzuzeigen.
1. Wählen Sie das Asset aus und tippen/klicken Sie in der Symbolleiste auf **[!UICONTROL In Assets einblenden]**, um den Übersetzungsstatus für das Asset anzuzeigen.
1. Um sicherzustellen, dass die der Quelle zugeordneten Assets übersetzt wurden, klicken/tippen Sie auf das Quellelement.
1. Select the asset that is related to the source, and then click/tap **[!UICONTROL Reveal in Assets]**. Das übersetzte zugehörige Asset wird angezeigt.
