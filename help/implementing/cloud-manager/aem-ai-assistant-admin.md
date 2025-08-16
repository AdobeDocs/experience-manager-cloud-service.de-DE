---
title: Konfigurieren des KI-Assistenten in Adobe Experience Manager
description: Erfahren Sie, wie Sie den KI-Assistenten mithilfe der Admin Console in Adobe Experience Manager einrichten und konfigurieren.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
source-git-commit: a216777f6d5bb3dd1afe5d7cdb88ec41435c0500
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 4%

---

# Konfigurieren des KI-Assistenten in Adobe Experience Manager {#aem-ai-asst-admin-setup}

Ein Administrator muss den Zugriff, die Berechtigungen und die Einstellungen konfigurieren, bevor Benutzer in ihrem Unternehmen die Funktionen im KI-Assistenten von AEM (Adobe Experience Manager) verwenden können. In diesem Artikel wird beschrieben, wie Sie den KI-Assistenten für Ihre Organisation aktivieren, die erforderlichen Anmeldeinformationen einrichten und Konfigurationsänderungen speichern.

**Überblick über den Konfigurationsprozess des AEM AI-Assistenten**

Der Konfigurationsprozess besteht aus den folgenden Schritten:

1. [Erstellen eines neuen Produktprofils in der Adobe Admin Console](#create-profile).
1. [Aktivieren Sie die Berechtigung KI-Assistent für Produktkenntnisse](#enable-permission).
1. [Erstellen Sie eine neue Benutzergruppe (oder verwenden Sie eine vorhandene Benutzergruppe)](#create-user-group).
1. [Benutzer zur Benutzergruppe hinzufügen](#add-users).
1. [Weisen Sie das Produktprofil der Benutzergruppe zu](#assign-product-profile).

**Voraussetzungen**

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllt haben:

* Sie müssen mindestens über Produktadministrator-Rechte in der Adobe Admin Console verfügen.
* Sie verfügen über Kenntnisse der Benutzerverwaltungsstruktur Ihres Unternehmens.

## &#x200B;1. Erstellen eines neuen Produktprofils in der Adobe Admin Console{#create-profile}

1. Befolgen Sie die detaillierten Anweisungen unter [Erstellen eines neuen Produktprofils in der Adobe Admin Console](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/ui/create-profile) in der Dokumentation zu Experience Platform.

1. Beim Erstellen des neuen Produktprofils können Sie die folgenden vorgeschlagenen Werte für den KI-Assistenten verwenden.

   | Textfeld | Vorgeschlagener Wert |
   | --- | --- |
   | Produktprofilname | `AEM AI Assistant` (oder Ihr bevorzugter beschreibender Name) |
   | Anzeigename (optional) | `AI Assistant` |
   | Beschreibung (optional) | `Product profile for managing AEM AI Assistant access` |
   | Benachrichtigung | Konfigurieren auf Grundlage der Voreinstellungen Ihrer Organisation |




## &#x200B;2. Aktivieren der Berechtigung „KI-Assistent - Produktkenntnisse“{#enable-permission}

Der Prozess zum Zuweisen benutzerdefinierter Berechtigungen zu Produktprofilen folgt dem standardmäßigen Workflow für benutzerdefinierte Berechtigungen in Adobe Cloud Manager.

Referenzartikel: [Zuweisen benutzerdefinierter Berechtigungen zum neuen Produktprofil](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions)

1. Klicken Sie in der Admin Console auf den Namen Ihres neu erstellten Produktprofils (`AEM AI Assistant`)

   ![Screenshot](/help/implementing/cloud-manager/assets/ai-assistant-console.png)

1. Um die Liste der bearbeitbaren Berechtigungen anzuzeigen, klicken Sie auf die Registerkarte **Berechtigungen** .

1. Suchen Sie in der Tabellenliste die Berechtigung `AI Assistant Product Knowledge` .

   ![Registerkarte „Berechtigungen für KI-Assistenten“ in Admin Console](/help/implementing/cloud-manager/assets/ai-assistant-permission.png)

1. Klicken Sie rechts neben dem Berechtigungsnamen auf ![Bleistiftsymbol oder Bearbeitungssymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).

1. Aktivieren Sie auf **Seite Berechtigungen für KI-** bearbeiten den Umschalter **KI-Assistent - Produktkenntnisse**.

   ![Seite „Berechtigungen bearbeiten“ für die Umschaltoption „KI-Assistent - Produktwissen“](/help/implementing/cloud-manager/assets/ai-assistant-prod-knowledge.png)

1. Klicken Sie unten rechts auf der Seite auf **Speichern**.

   Für Ihr Produktprofil ist jetzt die Berechtigung KI-Assistent für Produktwissen aktiviert.


## &#x200B;3. Erstellen Sie eine neue Benutzergruppe (oder verwenden Sie eine vorhandene Benutzergruppe).{#create-user-group}

1. Führen Sie einen der folgenden Schritte aus:

>[!BEGINTABS]

>[!TAB Erstellen Sie eine neue Benutzergruppe]

1. Klicken Sie in der Admin Console auf **Benutzer** > **Benutzergruppen**.

   ![Benutzergruppen](/help/implementing/cloud-manager/assets/ai-assistant-user-groups.png)

1. Klicken Sie auf **Seite** Benutzergruppen **auf „Neue Benutzergruppe**.

   ![Schaltfläche „Neue Benutzergruppe“ auf der Seite „Benutzergruppen“](/help/implementing/cloud-manager/assets/ai-assistant-new-user-group.png)

1. Geben **auf der Seite „Neue Benutzergruppe erstellen** die folgenden Informationen ein:

   | Option | Vorgeschlagener Wert |
   | --- | --- |
   | Name der Benutzergruppe | `AEM AI Assistant` (oder der bevorzugte Name) |
   | Beschreibung (optional) | `User group for managing AEM AI Assistant access` |

   ![Erstellen Sie eine neue Benutzergruppenseite](/help/implementing/cloud-manager/assets/ai-assistant-create-new-user-group.png)

1. Klicken Sie unten rechts auf der Seite auf **Speichern**.

>[!TAB Vorhandene Benutzergruppe verwenden]

Sie können eine bestehende AEM-Benutzergruppe verwenden, wenn sie die Zugriffsanforderungen für den KI-Assistenten erfüllt, anstatt eine neue Gruppe zu erstellen.

>[!ENDTABS]

## &#x200B;4. Benutzer zur Benutzergruppe hinzufügen{#add-users}

1. Führen Sie einen der folgenden Schritte aus:

>[!BEGINTABS]

>[!TAB Hinzufügen einzelner Benutzer]

1. Klicken Sie auf **Seite** Benutzergruppen“ in der Tabelle **Gruppenname** auf den Namen der neu erstellten Benutzergruppe oder auf einen vorhandenen Benutzergruppennamen.

   ![Benutzergruppenseite mit dem Namen der Benutzergruppe des AEM AI-Assistenten in der Tabelle](/help/implementing/cloud-manager/assets/ai-assistant-user-group-name-in-table.png)

1. Klicken Sie auf **Seite &quot;**&quot; für den **AEM AI Assistant** auf die Registerkarte **Benutzer** und dann auf **Benutzer hinzufügen**.

   ![Die Seite Benutzergruppen des AEM-KI-Assistenten, auf der die Registerkarte Benutzer und die Schaltfläche Benutzer hinzufügen angezeigt werden](/help/implementing/cloud-manager/assets/ai-assistant-add-users.png)

1. Suchen Sie auf der Seite **`Add users to this user group`** nach Benutzern und wählen Sie sie aus, die Zugriff auf den AEM AI-Assistenten benötigen.

   ![Benutzer zu dieser Benutzergruppenseite hinzufügen](/help/implementing/cloud-manager/assets/ai-assistant-add-users-to-this-group.png)

1. Klicken Sie unten rechts auf der Seite auf **Speichern**.

>[!TAB Mehrere Benutzer auf einmal hinzufügen]

Sie können die Funktion für den Massen-Upload in der Admin Console verwenden.

1. Bereiten Sie eine CSV-Datei mit Benutzerinformationen vor.

1. Verwenden Sie die **`Add users by CSV`** Option für eine effiziente Massenhinzufügung.

>[!ENDTABS]




## &#x200B;5. Zuweisen des Produktprofils zur Benutzergruppe{#assign-product-profile}




