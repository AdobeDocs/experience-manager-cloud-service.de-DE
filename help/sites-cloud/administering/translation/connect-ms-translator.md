---
title: Herstellen einer Verbindung mit Microsoft Translator
description: Erfahren Sie, wie Sie AEM sofort mit Microsoft Translator verbinden können, um Ihren Übersetzungs-Workflow zu automatisieren.
feature: Sprachkopie
role: Administrator
exl-id: ca3c50f9-005e-4871-8606-0cfd3ed21936
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 100%

---

# Herstellen einer Verbindung mit Microsoft Translator {#connecting-to-microsoft-translator}

Erstellen Sie eine Konfiguration für den [Microsoft Translator](https://hub.microsofttranslator.com)-Cloud-Service, um Ihr Microsoft Translation-Konto zum Übersetzen von AEM-Seiteninhalten, -Community-Inhalten oder -Assets zu nutzen.

>[!NOTE]
>
>Für AEM wird ein Microsoft Translation-Testkonto verwendet, mit dem pro Monat kostenlos maximal 2.000.000 Zeichen übersetzt werden können. Informationen zum Erhalt eines Kontoabonnements, das für Produktionssysteme geeignet ist, finden Sie unter [Durchführen eines Upgrades für die Konfiguration „Microsoft Translator-Testlizenz“](#upgrading-the-microsoft-translator-trial-license-configuration).

| Eigenschaft | Beschreibung |
|---|---|
| Übersetzungsetikett | Der Anzeigename für den Übersetzungs-Service |
| Übersetzungszuteilung | (Optional) Für nutzergenerierte Inhalte wird die Zuteilung neben übersetzten Texten angezeigt, beispielsweise `Translations by Microsoft`. |
| Workspace-ID | (Optional) Die ID Ihrer angepassten Microsoft Translator-Engine, die verwendet werden soll |
| Mitgliedschaftsschlüssel | Ihr Mitgliedschaftsschlüssel für Microsoft Translator |

Nachdem Sie die Konfiguration erstellt haben, müssen Sie sie [aktivieren](#activating-the-translator-service-configurations).

Mit dem folgenden Verfahren wird eine Microsoft Translator-Konfiguration erstellt.

1. Klicken oder tippen Sie im [Navigationsbereich](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) auf **Tools** -> **Cloud Services** -> **Übersetzungs-Cloud Services**.
1. Navigieren Sie zu dem Ort, an dem Sie die Konfiguration erstellen möchten. Normalerweise ist dies in Ihrem Site-Stammverzeichnis oder es kann eine globale Standardkonfiguration sein.
1. Tippen oder klicken Sie auf die Schaltfläche **Erstellen**.
1. Legen Sie Ihre Konfiguration fest.
   1. Wählen Sie **Microsoft Translator** in der Dropdown-Liste aus.
   1. Geben Sie einen Titel für Ihre Konfiguration ein. Mit dem Titel wird die Konfiguration auf der Cloud Services-Konsole und in Dropdown-Listen mit den Seiteneigenschaften identifiziert.
   1. Geben Sie optional einen Namen für den Repository-Knoten ein, auf dem die Konfiguration gespeichert wird.

   ![Erstellen einer Übersetzungskonfiguration](../assets/create-translation-config.png)

1. Klicken Sie auf **Erstellen**.
1. Geben Sie im Fenster **Konfiguration bearbeiten** die in der vorherigen Tabelle beschriebenen Werte für den Übersetzungs-Service ein.

   ![Bearbeiten einer Übersetzungskonfiguration](../assets/edit-translation-config.png)

1. Tippen oder klicken Sie auf **Verbinden**, um die Verbindung zu überprüfen.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

## Durchführen eines Upgrades für die Konfiguration „Microsoft Translator-Testlizenz“ {#upgrading-the-microsoft-translator-trial-license-configuration}

Die Seiten der Microsoft Translation-Konfiguration enthalten einen direkten Link zur Microsoft-Website, über den Sie ein für Produktionssysteme geeignetes Kontoabonnement erhalten können.

1. Klicken oder tippen Sie im [Navigationsbereich](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) auf **Tools** -> **Cloud Services** -> **Übersetzungs-Cloud Services**.
1. Tippen oder klicken Sie auf Ihre bestehende Microsoft Translator-Konfiguration.
1. Tippen oder klicken Sie auf **Bearbeiten**.
1. Tippen oder klicken Sie im Fenster **Konfiguration bearbeiten** auf **Abonnement aktualisieren**. Eine Microsoft-Webseite mit weiteren Details zum Service wird geöffnet.

## Anpassen der Microsoft Translator-Engine {#customizing-your-microsoft-translator-engine}

Die Seiten der Microsoft Translation-Konfiguration enthalten einen direkten Link zur Microsoft-Website, auf der die Microsoft Translator-Engine angepasst werden kann.

1. Klicken oder tippen Sie im [Navigationsbereich](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps) auf **Tools** -> **Cloud Services** -> **Übersetzungs-Cloud Services**.
1. Tippen oder klicken Sie auf Ihre bestehende Microsoft Translator-Konfiguration.
1. Tippen oder klicken Sie auf **Bearbeiten**.
1. Tippen oder klicken Sie im Fenster **Konfiguration bearbeiten** auf **Übersetzer anpassen**. Verwenden Sie die Microsoft-Webseite, die geöffnet wird, um Ihren Service anzupassen.

## Aktivieren der Übersetzungs-Service-Konfigurationen  {#activating-the-translator-service-configurations}

Sie müssen Ihre Cloud Service-Konfigurationen aktivieren, um übersetzte Inhalte zu unterstützen, die auf der Veröffentlichungsinstanz repliziert werden. Verwenden Sie die Methode [Veröffentlichen eines Baums](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-and-unpublishing-a-tree), um die Repository-Knoten zu aktivieren, die die Microsoft Translator-Konfigurationen speichern. Die Knoten befinden sich unter den folgenden übergeordneten Knoten:

* `/libs/settings/cloudconfigs/translation/msft-translation`
