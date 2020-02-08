---
title: Freigeben privater Ordner
description: Erfahren Sie, wie Sie in Adobe Experience Manager (AEM) Assets einen privaten Ordner erstellen, ihn mit anderen Benutzern teilen und ihnen verschiedene Berechtigungen zuweisen können.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Freigeben privater Ordner {#private-folder-sharing}

Sie können einen privaten Ordner in der Adobe Experience Manager (AEM) Assets-Benutzeroberfläche erstellen, der nur für Sie verfügbar ist. Sie können diesen privaten Ordner auch für andere Benutzer freigeben und diesen Benutzern verschiedene Berechtigungen zuweisen. Je nach der zugewiesenen Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner ausführen, wie das Anzeigen oder Bearbeiten von Assets im Ordner.

1. In the Assets console, tap/click **[!UICONTROL Create]** from the toolbar and then choose **[!UICONTROL Folder]** from the menu.
1. Geben Sie in das Dialogfeld **[!UICONTROL Ordner hinzufügen]** einen Titel und einen Namen (optional) für den Ordner ein und wählen Sie **[!UICONTROL Privat]** aus.
1. Tippen/klicken Sie auf **[!UICONTROL Erstellen]**. Ein privater Ordner wird auf der Assets-Benutzeroberfläche erstellt.
1. Um den Ordner gemeinsam mit anderen Benutzern verwenden und Berechtigungen zuweisen zu können, wählen Sie den Ordner aus und klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Eigenschaften]**.

   >[!NOTE]
   >
   >Der Ordner ist erst dann für andere Benutzer sichtbar, wenn Sie ihn freigegeben haben.

1. In the Folder Properties page, select a user from the **[!UICONTROL Add User]** list, assign a role to the user on your private folder, and click **[!UICONTROL Add]**.

   >[!NOTE]
   >
   >Sie können dem Benutzer, für den Sie den Ordner freigeben, verschiedene Rollen zuweisen, wie Bearbeiter, Eigentümer oder Betrachter. Wenn Sie dem Benutzer eine Eigentümerrolle zuweisen, hat der Benutzer Editor-Berechtigungen für den Ordner. Darüber hinaus kann der Benutzer den Ordner für andere freigeben. Wenn Sie die Rolle „Editor“ zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner bearbeiten. Wenn Sie die Rolle „Betrachter“ zuweisen, kann der Benutzer die Assets im privaten Ordner lediglich anzeigen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Je nach der zugewiesenen Rolle erhält der Benutzer einen Satz Berechtigungen für den privaten Ordner, wenn er sich bei AEM Assets anmeldet.
1. Klicken Sie auf **[!UICONTROL OK]** zum Schließen der Bestätigungsmeldung.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält eine Freigabebenachrichtigung. Melden Sie sich bei AEM Assets mit den Anmeldedaten des Benutzers an, um die Benachrichtigungen anzuzeigen.
1. Tippen/klicken Sie auf das Symbol „Benachrichtigungen“, um eine Liste der Benachrichtigungen zu öffnen.
1. Klicken/tippen Sie auf den Eintrag für den privaten Ordner, der vom Administrator freigegeben wurde, um den Ordner zu öffnen.

>[!NOTE]
>
>Um einen privaten Ordner zu erstellen, benötigen Sie die Berechtigungen „Lesen“ und „ACL bearbeiten“ für den übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen möchten. Wenn Sie kein Administrator sind, werden diese Berechtigungen auf */content/dam* nicht standardmäßig für Sie aktiviert. In diesem Fall müssen Sie zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe erhalten, bevor Sie versuchen, private Ordner zu erstellen oder Ordnereinstellungen anzuzeigen.
