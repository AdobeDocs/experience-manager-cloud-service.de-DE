---
title: Herstellen einer Verbindung mit Microsoft Translator
description: Erfahren Sie, wie Sie AEM sofort mit Microsoft Translator verbinden können, um Ihren Übersetzungs-Workflow zu automatisieren.
feature: Sprachkopie
role: Administrator
exl-id: ca3c50f9-005e-4871-8606-0cfd3ed21936
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 41%

---

# Herstellen einer Verbindung mit Microsoft Translator {#connecting-to-microsoft-translator}

Erstellen Sie eine Konfiguration für den Cloud-Dienst [Microsoft Translator](https://hub.microsofttranslator.com), um Ihr Microsoft Translation-Konto für die Übersetzung AEM Seiteninhalts oder Assets zu verwenden.

>[!NOTE]
>
>AEM bietet ein Microsoft Translation-Testkonto, das maximal 2.000.000 kostenlose übersetzte Zeichen pro Monat ermöglicht. Informationen zum Abrufen eines Kontoabonnements, das für Produktionssysteme geeignet ist, finden Sie unter [Aktualisieren der Microsoft Translator-Testlizenzkonfiguration](#upgrading-the-microsoft-translator-trial-license-configuration).

| Eigenschaft | Beschreibung |
|---|---|
| Übersetzungsetikett | Der Anzeigename für den Übersetzungsdienst |
| Übersetzungszuteilung | (Optional) Bei benutzergenerierten Inhalten die Attribution, die neben übersetztem Text erscheint, z. B. `Translations by Microsoft` |
| Workspace-ID | (Optional) Die ID Ihrer angepassten Microsoft Translator-Engine, die verwendet werden soll |
| Mitgliedschaftsschlüssel | Ihr Mitgliedschaftsschlüssel für Microsoft Translator |

Nachdem Sie die Konfiguration erstellt haben, müssen Sie [sie aktivieren](#activating-the-translator-service-configurations).

Im folgenden Verfahren wird eine Microsoft Translator-Konfiguration erstellt.

1. Klicken oder tippen Sie im Navigationsfenster [a1/> auf **Tools** -> **Cloud Services** -> **Übersetzungs-Cloud Services**.](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps)
1. Navigieren Sie zu der Stelle, an der Sie die Konfiguration erstellen möchten. Normalerweise befindet sich dies im Stammverzeichnis Ihrer Site oder es kann sich um eine globale Standardkonfiguration handeln.
1. Tippen oder klicken Sie auf die Schaltfläche **Erstellen** .
1. Definieren Sie Ihre Konfiguration.
   1. Wählen Sie **Microsoft Translator** in der Dropdown-Liste aus.
   1. Geben Sie einen Titel für Ihre Konfiguration ein. Mit dem Titel wird die Konfiguration auf der Cloud-Services-Konsole und in Dropdown-Listen mit den Seiteneigenschaften identifiziert.
   1. Geben Sie optional einen Namen für den Repository-Knoten ein, auf dem die Konfiguration gespeichert wird.

   ![Erstellen einer Übersetzungskonfiguration](../assets/create-translation-config.png)

1. Klicken Sie auf **Erstellen**.
1. Geben Sie im Fenster **Konfiguration bearbeiten** die Werte für den Übersetzungsdienst an, die in der vorherigen Tabelle beschrieben sind.

   ![Übersetzungskonfiguration bearbeiten](../assets/edit-translation-config.png)

1. Tippen oder klicken Sie auf **Verbinden** , um die Verbindung zu überprüfen.
1. Tippen oder klicken Sie auf **Speichern und schließen**.

## Durchführen eines Upgrades für die Konfiguration „Microsoft Translator-Testlizenz“{#upgrading-the-microsoft-translator-trial-license-configuration}

Die Seiten der Microsoft Translation-Konfiguration enthalten einen direkten Link zur Microsoft-Website, über den Sie ein für Produktionssysteme geeignetes Kontoabonnement erhalten können.

1. Tippen oder klicken Sie im Navigationsfenster [a1/> auf **Tools** -> **Cloud Services** -> **Übersetzungs-Cloud Services**.](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps)
1. Tippen oder klicken Sie auf Ihre vorhandene Microsoft Translator-Konfiguration.
1. Tippen oder klicken Sie auf **Bearbeiten**.
1. Tippen oder klicken Sie im Fenster **Konfiguration bearbeiten** auf **Upgrade-Abonnement**. Eine Microsoft-Webseite mit weiteren Details zum Dienst wird geöffnet.

## Anpassen der Microsoft Translator-Engine {#customizing-your-microsoft-translator-engine}

Die Seiten der Microsoft Translation-Konfiguration enthalten einen direkten Link zur Microsoft-Website, auf der die Microsoft Translator-Engine angepasst werden kann.

1. Tippen oder klicken Sie im Navigationsfenster [a1/> auf **Tools** -> **Cloud Services** -> **Übersetzungs-Cloud Services**.](/help/sites-cloud/authoring/getting-started/basic-handling.md#first-steps)
1. Tippen oder klicken Sie auf Ihre vorhandene Microsoft Translator-Konfiguration.
1. Tippen oder klicken Sie auf **Bearbeiten**.
1. Tippen oder klicken Sie im Fenster **Konfiguration bearbeiten** auf **Übersetzer anpassen**. Verwenden Sie die Microsoft-Webseite, die geöffnet wird, um Ihren Dienst anzupassen.

## Aktivieren der Übersetzungsdienstkonfigurationen {#activating-the-translator-service-configurations}

Sie müssen Ihre Cloud Service-Konfigurationen aktivieren, um übersetzte Inhalte zu unterstützen, die auf der Veröffentlichungsinstanz repliziert werden. Verwenden Sie die Methode [Veröffentlichen eines Baums](/help/sites-cloud/authoring/fundamentals/publishing-pages.md#publishing-and-unpublishing-a-tree), um die Repository-Knoten zu aktivieren, die die Microsoft Translator-Konfigurationen speichern. Die Knoten befinden sich unter den folgenden übergeordneten Knoten:

* `/libs/settings/cloudconfigs/translation/msft-translation`
