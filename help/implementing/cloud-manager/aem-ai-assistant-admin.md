---
title: Konfigurieren des KI-Assistenten in Adobe Experience Manager
description: Erfahren Sie, wie Sie den KI-Assistenten mithilfe der Admin Console in Adobe Experience Manager einrichten und konfigurieren.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
hide: true
hidefromtoc: true
exl-id: a7f3dc14-29f7-473a-9870-d52393e6fa6e
source-git-commit: e853e7b46c762ab724d5eecb344897a83e4fb724
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 3%

---

# Konfigurieren des KI-Assistenten in Adobe Experience Manager {#aem-ai-asst-admin-setup}

Ein Administrator muss den Zugriff, die Berechtigungen und die Einstellungen konfigurieren, bevor Benutzer in ihrem Unternehmen die Funktionen im KI-Assistenten von AEM (Adobe Experience Manager) verwenden können.

Der Konfigurationsprozess des AEM AI-Assistenten besteht aus den folgenden Schritten:

1. [Erstellen eines neuen Produktprofils in der Adobe Admin Console](#create-profile).
1. [Aktivieren Sie die Berechtigung KI-Assistent für Produktkenntnisse](#enable-permission).
1. [Erstellen Sie eine neue Benutzergruppe (oder verwenden Sie eine vorhandene Benutzergruppe)](#create-user-group).
1. [Benutzer zur Benutzergruppe hinzufügen](#add-users).
1. [Weisen Sie das Produktprofil der Benutzergruppe zu](#assign-product-profile).

**Voraussetzungen**

Bevor Sie beginnen, stellen Sie sicher, dass Sie die folgenden Voraussetzungen erfüllt haben:

* Sie müssen mindestens über Produktadministrator-Rechte in der Adobe Admin Console verfügen.
* Sie verfügen über Kenntnisse der Benutzerverwaltungsstruktur Ihres Unternehmens.

**Überlegungen zur Konfiguration**

* Verarbeitungszeit: Es kann bis zu 2 Minuten dauern, bis in Cloud Manager erstellte Ressourcen zur Berechtigungskonfiguration in Admin Console angezeigt werden.
* Mehrere Profile: Benutzer können Teil mehrerer Profile sein und Berechtigungen werden aus allen zugewiesenen Profilen kombiniert.
* Organisationsbereich: Einige Berechtigungen können auf Organisationsebene für alle Programme gelten.
* Vordefinierte Profile: Löschen Sie keine vordefinierten Berechtigungsprofile aus der Admin Console.


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
1. Weisen Sie nun das Produktprofil der Benutzergruppe&rbrack;(#assign-product-profile) zu.

>[!TAB Mehrere Benutzer auf einmal hinzufügen]

Sie können die Funktion für den Massen-Upload in der Admin Console verwenden.

1. Bereiten Sie eine CSV-Datei mit Benutzerinformationen vor.
1. Verwenden Sie die **`Add users by CSV`** Option für eine effiziente Massenhinzufügung.
1. Weisen Sie nun das Produktprofil der Benutzergruppe&rbrack;(#assign-product-profile) zu.

>[!ENDTABS]


## &#x200B;5. Zuweisen des Produktprofils zur Benutzergruppe{#assign-product-profile}

Dieser Schritt folgt dem standardmäßigen Adobe Admin Console-Workflow für die Zuweisung von Produktprofilen zu Benutzergruppen.

Referenzartikel: [Verwalten von Produktprofilen für Enterprise-Benutzer](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html)

1. Klicken Sie noch in der Benutzergruppe &quot;AEM AI Assistant“ von [4 - Benutzer zur Benutzergruppe hinzufügen](#add-users) auf die Registerkarte **Zugewiesene Produktprofile**.
1. Klicken Sie **Profil zuweisen**.

   ![Benutzergruppenseite des AEM-KI-Assistenten mit ausgewählter Registerkarte „Zugewiesene Produktprofile“](/help/implementing/cloud-manager/assets/ai-assistant-assign-profile.png)

1. Suchen Sie auf der **Produkte und Profile zuweisen** im Dialogfeld **Produktprofile auswählen** nach Ihrem **KI-Assistent**-Produktprofil und wählen Sie es aus.

   ![Die Seite „Produkte und Profile zuweisen“, die das Dialogfeld „Produktprofile auswählen“ anzeigt und das Produktprofil „KI-Assistent“ ausgewählt ist](/help/implementing/cloud-manager/assets/ai-assistant-select-product-profile.png)

1. Klicken Sie unten rechts im Dialogfeld auf **Übernehmen**.
1. Klicken Sie unten rechts auf der Seite **Produkte und Profile zuweisen** auf **Speichern**.

   ![Das angezeigte Produktprofil „KI-Assistent“ ist der Benutzergruppe &quot;AEM-KI-Assistent“ zugewiesen](/help/implementing/cloud-manager/assets/ai-assistant-profile-assigned-to-user-group.png)


## Konfiguration überprüfen

* Vergewissern Sie sich, dass in Ihrem Produktprofil die richtige Anzahl zugewiesener Benutzergruppen angezeigt wird.
* Vergewissern Sie sich, dass in der Benutzergruppe die richtige Anzahl von Benutzern angezeigt wird.
* Vergewissern Sie sich, dass die Berechtigung KI-Assistent für Produktkenntnisse aktiviert und ordnungsgemäß konfiguriert ist.


## Testen der Konfiguration

Bitten Sie einen Benutzer aus der zugewiesenen Gruppe, Folgendes zu tun:

1. Melden Sie sich bei AEM an.
2. Stellen Sie sicher, dass die Funktionen des KI-Assistenten verfügbar sind.
3. Testen der Funktionalität des KI-Assistenten, um eine ordnungsgemäße Aktivierung sicherzustellen.

## Siehe auch

* [Adobe Experience Platform-Zugriffskontrolle](https://experienceleague.adobe.com/de/docs/experience-platform/access-control/ui/overview)
* [Benutzerdefinierte Cloud Manager-Berechtigungen](/help/implementing/cloud-manager/custom-permissions.md)


