---
title: Freigeben privater Ordner
description: Erfahren Sie, wie Sie in Adobe Experience Manager (AEM) Assets einen privaten Ordner erstellen, ihn mit anderen Benutzern teilen und ihnen verschiedene Berechtigungen zuweisen können.
contentOwner: AG
translation-type: ht
source-git-commit: 991d4900862c92684ed92c1afc081f3e2d76c7ff

---


# Freigeben privater Ordner {#private-folder-sharing}

Sie können einen privaten Ordner in der Adobe Experience Manager (AEM) Assets-Benutzeroberfläche erstellen, der nur für Sie verfügbar ist. Sie können diesen privaten Ordner auch für andere Benutzer freigeben und diesen Benutzern verschiedene Berechtigungen zuweisen. Je nach der zugewiesenen Berechtigungsstufe können Benutzer verschiedene Aufgaben mit dem Ordner ausführen, wie das Anzeigen oder Bearbeiten von Assets im Ordner.

1. Klicken oder tippen Sie in der Konsole „Assets“ von der Symbolleiste aus auf **[!UICONTROL Erstellen]** und wählen Sie dann **[!UICONTROL Ordner]** aus dem Menü aus.
1. Geben Sie in das Dialogfeld **[!UICONTROL Ordner hinzufügen]** einen Titel und einen Namen (optional) für den Ordner ein und wählen Sie **[!UICONTROL Privat]** aus.
1. Tippen oder klicken Sie auf **[!UICONTROL Erstellen]**. Ein privater Ordner wird auf der Assets-Benutzeroberfläche erstellt.
1. Um den Ordner gemeinsam mit anderen Benutzern verwenden und Berechtigungen zuweisen zu können, wählen Sie den Ordner aus und klicken/tippen Sie in der Symbolleiste auf das Symbol **[!UICONTROL Eigenschaften]**.

   >[!NOTE]
   >
   >Der Ordner wird erst dann für andere Benutzer sichtbar, wenn Sie ihn freigeben.

1. Wählen Sie auf der Seite „Ordnereigenschaften“ einen Benutzer in der Liste **[!UICONTROL Benutzer hinzufügen]** aus, weisen Sie dem Benutzer eine Rolle für den privaten Ordner zu und klicken Sie auf **[!UICONTROL Hinzufügen]**.

   >[!NOTE]
   >
   >Sie können dem Benutzer, für den Sie den Ordner freigeben, verschiedene Rollen zuweisen, wie Bearbeiter, Eigentümer oder Betrachter. Wenn Sie dem Benutzer eine Eigentümerrolle zuweisen, hat der Benutzer Editor-Berechtigungen für den Ordner. Darüber hinaus kann der Benutzer den Ordner für andere freigeben. Wenn Sie die Rolle „Editor“ zuweisen, kann der Benutzer die Assets in Ihrem privaten Ordner bearbeiten. Wenn Sie die Rolle „Betrachter“ zuweisen, kann der Benutzer die Assets im privaten Ordner lediglich anzeigen.

1. Klicken Sie auf **[!UICONTROL Speichern]**. Je nach der zugewiesenen Rolle erhält der Benutzer einen Satz Berechtigungen für den privaten Ordner, wenn er sich bei AEM Assets anmeldet.
1. Klicken Sie auf **[!UICONTROL OK]** zum Schließen der Bestätigungsmeldung.
1. Der Benutzer, für den Sie den Ordner freigeben, erhält eine Freigabebenachrichtigung. Melden Sie sich bei AEM Assets mit den Anmeldedaten des Benutzers an, um die Benachrichtigungen anzuzeigen.
1. Tippen/klicken Sie auf das Symbol „Benachrichtigungen“, um eine Liste der Benachrichtigungen zu öffnen.
1. Klicken oder tippen Sie auf den Eintrag für den privaten Ordner, der vom Administrator freigegeben wurde, um den Ordner zu öffnen.

>[!NOTE]
>
>Um einen privaten Ordner zu erstellen, benötigen Sie die Berechtigungen „Lesen“ und „ACL bearbeiten“ für den übergeordneten Ordner, unter dem Sie einen privaten Ordner erstellen möchten. Wenn Sie kein Administrator sind, werden diese Berechtigungen auf */content/dam* nicht standardmäßig für Sie aktiviert. In diesem Fall müssen Sie zunächst diese Berechtigungen für Ihre Benutzer-ID/Gruppe erhalten, bevor Sie versuchen, private Ordner zu erstellen oder Ordnereinstellungen anzuzeigen.
