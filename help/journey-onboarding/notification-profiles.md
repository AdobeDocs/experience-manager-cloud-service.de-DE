---
title: Benachrichtigungsprofile
description: Erfahren Sie, wie Sie in der Admin Console Benutzerprofile erstellen, um den Empfang wichtiger E-Mail-Benachrichtigungen zu verwalten.
feature: Onboarding
role: Admin, User, Developer
exl-id: 4edecfcd-6301-4a46-98c7-eb5665f48995
source-git-commit: afb20efe8ed078a508f828c5df4e079f99dfab21
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 96%

---


# Benachrichtigungsprofile {#notification-profiles}

Erfahren Sie, wie Sie in der Admin Console Benutzerprofile erstellen, um den Empfang wichtiger E-Mail-Benachrichtigungen zu verwalten.

## Übersicht {#overview}

Von Zeit zu Zeit muss Adobe Benutzer bezüglich ihrer AEM as a Cloud Service-Umgebung kontaktieren. Neben produktinternen Benachrichtigungen verwendet Adobe gelegentlich auch E-Mails für Benachrichtigungen. Es gibt zwei Arten von E-Mail-Benachrichtigungen:

* **Benachrichtigung bei Vorfällen**: Diese Benachrichtigungen werden während eines Vorfalls gesendet oder wenn Adobe ein potenzielles Verfügbarkeitsproblem bei Ihrer AEM as a Cloud Service-Umgebung erkannt hat.
* **Proaktive Benachrichtigung**: Diese Benachrichtigungen werden gesendet, wenn ein Mitglied des Adobe-Support-Teams Anleitungen zu einer potenziellen Optimierung oder Empfehlung bereitstellen möchte, die für Ihre AEM as a Cloud Service-Umgebung von Vorteil sein kann.

>[!NOTE]
>
>Das Zuweisen von Gruppen zu proaktiven Benachrichtigungen wird nicht unterstützt. Stattdessen müssen Sie den Produktprofilen Benutzer direkt zuweisen.

Damit die richtigen Personen diese Benachrichtigungen erhalten, müssen Sie Benutzerprofile konfigurieren und zuweisen, wie in diesem Dokument beschrieben.

## Voraussetzungen {#prerequisites}

Da Benutzergruppen in der Admin Console erstellt und gepflegt werden, müssen vor dem Erstellen von Profilen für Benachrichtigungen folgende Bedingungen erfüllt sein:

* Sie verfügen über Berechtigungen zum Hinzufügen und Bearbeiten von Profilmitgliedschaften.
* Sie verfügen über ein gültiges Adobe Admin Console-Profil.

## Erstellen neuer Cloud Manager-Produktprofile {#create-profiles}

Um den Empfang von Benachrichtigungen ordnungsgemäß einzurichten, müssen Sie zwei Benutzerprofile erstellen. Diese Schritte dürfen nur einmal ausgeführt werden.

1. Melden Sie sich bei Admin Console unter [`https://adminconsole.adobe.com` an.](https://adminconsole.adobe.com)

1. Stellen Sie sicher, dass Sie sich in der richtigen Organisation befinden.

1. Wählen Sie auf der Seite **Übersicht** und auf der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Liste der Produkte und Dienste in der Admin Console](assets/products_services.png)

1. Gehen Sie in der Liste aller Instanzen zur **Cloud Manager**-Instanz.

   ![Liste der Instanzen in der Admin Console](assets/cloud_manager_instance.png)

1. Sie sehen die Liste aller vorkonfigurierten Cloud Manager-Produktprofile.

   ![Produktprofile in der Admin Console](assets/cloud_manager_profiles.png)

1. Klicken Sie auf **Neues Profil** und geben Sie die folgenden Details an:

   * **Name des Produktprofils**: `Incident Notification - Cloud Service`
   * **Anzeigename**: `Incident Notification - Cloud Service`
   * **Beschreibung**: Cloud Manager-Profil für die Benutzer, die Benachrichtigungen während eines Vorfalls oder dann erhalten, wenn Adobe ein potenzielles Verfügbarkeitsproblem in Ihrer AEM as a Cloud Service-Umgebung identifiziert hat

1. Klicken Sie auf **Speichern**.

1. Klicken Sie noch einmal auf **Neues Profil** und geben Sie die folgenden Details an:

   * **Name des Produktprofils**: `Proactive Notification - Cloud Service`
   * **Anzeigename**: `Proactive Notification - Cloud Service`
   * **Beschreibung**: Cloud Manager-Profil für Benutzer, die Benachrichtigungen erhalten, wenn ein Mitglied des Adobe Support-Teams Anleitungen zu einer potenziellen Optimierung oder Empfehlung für Ihre AEM as a Cloud Service-Umgebungskonfiguration bereitstellen möchte

1. Klicken Sie auf **Speichern**.

Ihre beiden neuen Benachrichtigungsprofile werden erstellt.

>[!NOTE]
>
>Es ist wichtig, dass der Name des Cloud Manager-**Produktprofils** genau mit dem angegebenen Namen übereinstimmt. Kopieren Sie den angegebenen Profilnamen und fügen Sie ihn ein, um Fehler zu vermeiden. Abweichungen oder Tippfehler führen dazu, dass Benachrichtigungen nicht wie gewünscht gesendet werden.
>
>Wenn Fehler auftreten oder die Profile nicht definiert wurden, benachrichtigt Adobe standardmäßig vorhandene Benutzer, die den Profilen **Cloud Manager-Entwickler** oder **Bereitstellungs-Manager** zugewiesen wurden.

## Zuweisen von Benutzenden zu den Benachrichtigungsprofilen {#add-users}

Nachdem die Profile erstellt wurden, müssen Sie die entsprechenden Benutzenden zuweisen. Dies ist beim Erstellen neuer oder durch Aktualisierung vorhandener Benutzerinnen und Benutzer möglich.

### Hinzufügen von neuen Benutzenden zu Profilen {#new-user}

Führen Sie diese Schritte aus, um Benutzer hinzuzufügen, für die noch keine Federated IDs eingerichtet wurden.

1. Identifizieren Sie die Benutzer, die Benachrichtigungen zu Vorfällen oder proaktive Benachrichtigungen erhalten sollen.

1. Melden Sie sich unter [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) bei der Admin Console an, wenn Sie noch nicht angemeldet sind.

1. Stellen Sie sicher, dass Sie die entsprechende Organisation ausgewählt haben.

1. Wählen Sie auf der Seite **Übersicht** die Option **Adobe Experience Manager as a Cloud Service** auf der Karte **Produkte und Services** aus.

   ![Benutzer](assets/product_services.png)

1. Wenn die Federated ID für Ihre Team-Mitglieder noch nicht eingerichtet wurde, klicken Sie in der oberen Navigationsleiste auf die Registerkarte **Benutzer** und wählen dann **Benutzer hinzufügen** aus. Andernfalls gehen Sie zum Abschnitt [Hinzufügen von vorhandenen Benutzenden zu Profilen](#existing-users).

   ![Benutzer](assets/cloud_manager_add_user.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten, und wählen Sie `Adobe ID` als **ID-Typ** aus.

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte auswählen**, um mit der Produktauswahl zu beginnen.

1. Wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie der bzw. dem Benutzenden eines oder beide der neuen Profile zu.

   * **Benachrichtigung bei Vorfällen − Cloud Service**
   * **Proaktive Benachrichtigung − Cloud Service**

1. Klicken Sie auf **Speichern**, und dem hinzugefügten Benutzer wird eine Begrüßungs-E-Mail gesendet.

Der eingeladene Benutzer erhält jetzt die Benachrichtigungen. Wiederholen Sie diese Schritte für die Benutzer in Ihrem Team, die Benachrichtigungen erhalten sollen.

### Hinzufügen von vorhandenen Benutzenden zu Profilen {#existing-user}

Führen Sie diese Schritte aus, um Benutzer hinzuzufügen, für die bereits Federated IDs vorhanden sind.

1. Identifizieren Sie die Benutzer, die Benachrichtigungen zu Vorfällen oder proaktive Benachrichtigungen erhalten sollen.

1. Melden Sie sich unter [`https://adminconsole.adobe.com`](https://adminconsole.adobe.com) bei der Admin Console an, wenn Sie noch nicht angemeldet sind.

1. Stellen Sie sicher, dass Sie die entsprechende Organisation ausgewählt haben.

1. Wählen Sie auf der Seite **Übersicht** die Option **Adobe Experience Manager as a Cloud Service** auf der Karte **Produkte und Services** aus.

1. Wählen Sie in der oberen Navigationsleiste die Registerkarte **Benutzer** aus.

1. Wenn die Federated ID bereits für das Team-Mitglied vorhanden ist, das Sie zu einem Benachrichtigungsprofil hinzufügen möchten, suchen Sie diese Person in der Liste und klicken Sie auf sie. Andernfalls fahren Sie mit dem Abschnitt [Hinzufügen von neuen Benutzenden zu Profilen](#add-user) fort.

1. Klicken Sie im Abschnitt **Produkte** auf die Schaltfläche mit den Auslassungspunkten und wählen Sie **Bearbeiten** aus.

1. Klicken Sie im Fenster **Produkte bearbeiten** auf die Schaltfläche mit dem Stift unter der Überschrift **Produkte auswählen**, um die Produktauswahl zu starten.

1. Wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie der bzw. dem Benutzenden eines oder beide der neuen Profile zu.

   * **Benachrichtigung bei Vorfällen − Cloud Service**
   * **Proaktive Benachrichtigung − Cloud Service**

1. Klicken Sie auf **Speichern**, und dem hinzugefügten Benutzer wird eine Begrüßungs-E-Mail gesendet.

Der eingeladene Benutzer erhält jetzt die Benachrichtigungen. Wiederholen Sie diese Schritte für die Benutzer in Ihrem Team, die Benachrichtigungen erhalten sollen.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt der Onboarding-Tour hinausgehen möchten.

* [Aktionszentrum](/help/operations/actions-center.md) - Nutzen Sie das Aktionszentrum, um bequem Maßnahmen zu Vorfällen und anderen wichtigen Informationen zu ergreifen.
