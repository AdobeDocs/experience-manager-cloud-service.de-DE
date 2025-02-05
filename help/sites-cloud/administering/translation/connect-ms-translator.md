---
title: Herstellen einer Verbindung mit Microsoft Translator
description: Erfahren Sie, wie Sie AEM sofort mit Microsoft Translator verbinden können, um Ihren Übersetzungs-Workflow zu automatisieren.
feature: Language Copy
role: Admin
exl-id: ca3c50f9-005e-4871-8606-0cfd3ed21936
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 84%

---

# Herstellen einer Verbindung mit Microsoft Translator {#connecting-to-microsoft-translator}

AEM bietet einen integrierten Connector für [Microsoft Translator](https://www.microsoft.com/de-de/translator/business/) zur Übersetzung von Seiteninhalten oder Assets. Nachdem Sie eine Lizenz von Microsoft für die Verwendung von Microsoft Translator erhalten haben, konfigurieren Sie den Connector entsprechend den Anweisungen auf dieser Seite.

>[!TIP]
>
>Wenn Sie mit der Übersetzung von Inhalten noch nicht vertraut sind, lesen Sie [Sites Translation Journey](/help/journey-sites/translation/overview.md), die Sie durch die Übersetzung Ihrer AEM Sites-Inhalte mithilfe der leistungsstarken Übersetzungs-Tools von AEM führt und ideal für alle ist, die keine AEM- oder Übersetzungserfahrung haben.

| Eigenschaft | Beschreibung |
|---|---|
| Übersetzungsetikett | Der Anzeigename für den Übersetzungs-Service |
| Übersetzungszuteilung | (Optional) Bei nutzergenerierten Inhalten die Zuteilung, die neben übersetzten Texten angezeigt wird, beispielsweise `Translations by Microsoft` |
| Workspace-ID | (Optional) Die ID Ihrer angepassten Microsoft Translator-Engine, die verwendet werden soll |
| Mitgliedschaftsschlüssel | Ihr Mitgliedschaftsschlüssel für Microsoft Translator |

Mit dem folgenden Verfahren wird eine Microsoft Translator-Konfiguration erstellt.

1. Wählen Sie im [Navigationsbereich](/help/sites-cloud/authoring/basic-handling.md#first-steps) die Option **Tools** > **Cloud Service** > **Übersetzungs-Cloud Service**.
1. Navigieren Sie zu dem Ort, an dem Sie die Konfiguration erstellen möchten. Normalerweise ist dies in Ihrem Site-Stammverzeichnis oder es kann eine globale Standardkonfiguration sein.
1. Wählen Sie die Schaltfläche **Erstellen**.
1. Legen Sie Ihre Konfiguration fest.
   1. Wählen Sie **Microsoft Translator** in der Dropdown-Liste aus.
   1. Geben Sie einen Titel für Ihre Konfiguration ein. Durch den Titel wird die Konfiguration in der Cloud Services-Konsole und in Dropdown-Listen mit den Seiteneigenschaften identifiziert.
   1. Geben Sie optional einen Namen für den Repository-Knoten ein, auf dem die Konfiguration gespeichert wird.

   ![Erstellen einer Übersetzungskonfiguration](../assets/create-translation-config.png)

1. Klicken Sie auf **Erstellen**.
1. Geben Sie im Fenster **Konfiguration bearbeiten** die in der vorherigen Tabelle beschriebenen Werte für den Übersetzungs-Service ein.

   ![Bearbeiten einer Übersetzungskonfiguration](../assets/msft-config-ui.png)

1. Wählen Sie **Verbinden** aus, um die Verbindung zu überprüfen.
1. Wählen Sie **Speichern und schließen**.

## Veröffentlichen der Übersetzungs-Service-Konfigurationen {#publishing-the-translator-service-configurations}

Veröffentlichen Sie als letzten Schritt Ihre Microsoft Translator-Konfigurationen, um veröffentlichte übersetzte Inhalte zu unterstützen. Verwenden Sie dazu die Aktion [Veröffentlichen eines Baums](/help/sites-cloud/authoring/sites-console/publishing-pages.md#publishing-and-unpublishing-a-tree).
