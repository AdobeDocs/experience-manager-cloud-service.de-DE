---
title: Private Ordner zum Freigeben von Assets
description: Erfahren Sie, wie Sie einen privaten Ordner im [!DNL Adobe Experience Manager Assets] und teilen sie mit anderen Benutzern und weisen ihnen verschiedene Berechtigungen zu.
contentOwner: Vishabh Gupta
role: User
feature: Collaboration
source-git-commit: 103bf8a477fb851e093bfde8e2c0535f49a01566
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 8%

---

# Privater Ordner in [!DNL Adobe Experience Manager Assets] {#private-folder}

Sie können einen privaten Ordner im [!DNL Adobe Experience Manager Assets] -Benutzeroberfläche, die ausschließlich für Sie verfügbar ist. Sie können diesen privaten Ordner für andere Benutzer freigeben und ihnen verschiedene Berechtigungen zuweisen. Je nach der zugewiesenen Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner ausführen, wie das Anzeigen oder Bearbeiten von Assets im Ordner.

>[!NOTE]
>
>Der private Ordner hat mindestens ein Mitglied mit der Eigentümerrolle.
>
>Um einen privaten Ordner zu erstellen, benötigen Sie `Read` und `Modify` -Berechtigungen für den übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen. Wenn Sie kein Administrator sind, sind diese Berechtigungen standardmäßig nicht für `/content/dam`. Rufen Sie in diesem Fall zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe ab, bevor Sie versuchen, private Ordner zu erstellen.

## Erstellen und Freigeben von privaten Ordnern  {#create-share-private-folder}

So erstellen und teilen Sie einen privaten Ordner:

1. Im [!DNL Assets] in der Konsole auf **[!UICONTROL Erstellen]** in der Symbolleiste und wählen Sie **[!UICONTROL Ordner]** aus dem Menü.

   ![Erstellen von Asset-Ordnern](assets/create-folder.png)

1. Im **[!UICONTROL Ordner erstellen]** Dialogfeld, geben Sie eine `Title` und `Name` (optional) für den Ordner.

   Wählen Sie die **[!UICONTROL Privat]** aktivieren und auf **[!UICONTROL Erstellen]**.

   ![chlimage_1-413](assets/create-private-folder.png)

   Ein privater Ordner wird erstellt. Sie können jetzt [Assets hinzufügen](add-assets.md#upload-assets) in den Ordner und geben Sie den Ordner für andere Benutzer oder Gruppen frei. Der Ordner ist für andere Benutzer erst sichtbar, wenn Sie ihn freigeben und ihnen Berechtigungen zuweisen.

1. Um den Ordner freizugeben, wählen Sie den Ordner aus und klicken Sie auf **[!UICONTROL Eigenschaften]** aus der Symbolleiste.

1. Im **[!UICONTROL Ordnereigenschaften]** ein Benutzer oder eine Gruppe aus der **[!UICONTROL Benutzer hinzufügen]** Liste, Rolle zuweisen (`Viewer`, `Editor`oder `Owner`) in Ihrem privaten Ordner speichern, und klicken Sie auf **[!UICONTROL Hinzufügen]**.

   ![assign-user-group](assets/assign-permissions-private-folder.png)

   Sie können verschiedene Rollen zuweisen, z. B. `Editor`, `Owner`oder `Viewer` auf den Benutzer, für den Sie den Ordner freigeben. Wenn Sie eine `Owner` Rolle für den Benutzer hat, hat der Benutzer `Editor` Berechtigungen für den Ordner. Darüber hinaus kann der Benutzer den Ordner für andere freigeben. Wenn Sie eine `Editor` -Rolle kann der Benutzer die Assets in Ihrem privaten Ordner bearbeiten. Wenn Sie eine Viewer-Rolle zuweisen, kann der Benutzer die Assets nur in Ihrem privaten Ordner anzeigen.

   >[!NOTE]
   >
   >Mindestens ein Mitglied des privaten Ordners verfügt über `Owner` Rolle. Daher kann der Administrator nicht alle Eigentümermitglieder aus einem privaten Ordner entfernen. Um jedoch die vorhandenen Eigentümer (und den Administrator selbst) aus dem privaten Ordner zu entfernen, muss der Administrator einen anderen Benutzer als Eigentümer hinzufügen.

1. Klicken Sie auf **[!UICONTROL Speichern und schließen]**. Je nach der zugewiesenen Rolle erhält der Benutzer eine Reihe von Berechtigungen für Ihren privaten Ordner, wenn sich der Benutzer bei anmeldet. [!DNL Assets].
1. Klicken Sie auf **[!UICONTROL OK]** zum Schließen der Bestätigungsmeldung.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält in seiner Benutzeroberfläche eine Freigabebenachrichtigung.

1. Klicken [!UICONTROL Benachrichtigungen] , um eine Benachrichtigungsliste zu öffnen.

   ![Benachrichtigung](assets/notification-icon.png)

1. Klicken Sie auf den Eintrag für den privaten Ordner, der vom Administrator freigegeben wurde, um den Ordner zu öffnen.

## Löschen privater Ordner {#delete-private-folder}

Sie können einen Ordner löschen, indem Sie ihn auswählen und [!UICONTROL Löschen] oder über die Rücktaste auf der Tastatur.

![Löschoption im oberen Menü](assets/delete-option.png)

>[!CAUTION]
>
>Wenn Sie einen privaten Ordner aus CRXDE Lite löschen, bleiben redundante Benutzergruppen im Repository.

>[!NOTE]
>
>Wenn Sie einen Ordner mit der oben genannten Methode aus der Benutzeroberfläche löschen, werden auch die zugehörigen Benutzergruppen gelöscht.
>
>Die vorhandenen redundanten, nicht verwendeten und automatisch generierten Benutzergruppen können jedoch mithilfe von aus dem Repository entfernt werden `clean` -Methode in JMX in der Autoreninstanz (`http://[server]:[port]/system/console/jmx/com.day.cq.dam.core.impl.team%3Atype%3DClean+redundant+groups+for+Assets`).
