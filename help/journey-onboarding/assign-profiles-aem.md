---
title: Zuweisen AEM Produktprofilen
description: Nachdem Sie Ihre Cloud-Ressourcen konfiguriert haben, müssen Sie Ihrem Team mithilfe AEM Produktprofilen Zugriff auf AEM gewähren.
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 22%

---

# Zuweisen AEM Produktprofilen {#assign-profiles-aem}

In diesem Teil des [Onboarding-Journey,](overview.md) Hier erfahren Sie, wie Sie Ihrem Team mithilfe AEM Produktprofilen Zugriff auf AEM gewähren.

## Ziel {#objective}

Nachdem Sie das vorherige Dokument in dieser Onboarding-Journey gelesen haben, [Erstellen von Umgebungen,](create-environments.md) Wenn Sie Ihre Cloud-Ressourcen konfiguriert haben, müssen Sie Ihrem Team mithilfe AEM Produktprofilen Zugriff auf AEM gewähren. Als Systemadministrator weisen Sie dazu AEM Produktprofile zu.

Nach dem Lesen dieses Dokuments sollten Sie Folgendes verstehen:

* Welche AEM Produktprofile sind.
* Wie man Team-Mitglieder zu AEM-Benutzer-Produktprofilen hinzufügt.
* Wie man Team-Mitglieder zu AEM-Administrator-Produktprofilen hinzufügt.

## AEM Produktprofile {#aem-product-profiles}

Um AEM verwenden zu können, müssen Ihre Teammitglieder mindestens einem AEM Produktprofil zugewiesen sein. Berechtigungen für den Zugriff auf Cloud Manager reichen nicht aus. Benutzer müssen zu einem von zwei Produktprofilen gehören:

* `AEM Users` - Zu dieser Gruppe gehören normale Benutzer, die alltägliche Aufgaben zum Erstellen von Inhalten ausführen.
* `AEM Administrators` - Diese Gruppe umfasst Benutzer, die für erweiterte Funktionen oder AEM verantwortlich sind.

Jeder Benutzer, der einem AEM Produktprofil zugewiesen ist, erhält ebenfalls schreibgeschützten Zugriff auf Cloud Manager. Der Schreibzugriff auf Cloud Manager kann über andere Produktprofile gewährt werden.

## Voraussetzungen {#prerequisites}

Bevor Sie diesen Abschnitt lesen, sollten Sie über die folgenden Informationen zu Ihrem Team verfügen, das AEM verwenden wird.

* Namen
* E-Mail-Adressen
* Rollen und Zuständigkeiten

>[!TIP]
>
>Für das Onboarding empfehlen wir, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Rest des Onboarding fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie später die Anzahl von Benutzern ausweiten.

## Anzeigen AEM Produktprofile {#view-profiles}

Führen Sie diese Schritte aus, um die AEM Produktprofile aus der Admin Console anzuzeigen.

1. Bei Admin Console anmelden unter [`https://adminconsole.adobe.com`.](https://adminconsole.adobe.com)

1. Wählen Sie auf der Seite **Überblick** die Option **Adobe Experience Manager as a Cloud Service** aus der Karte **Produkte und Services**.

   ![Karte für Produkte und Dienstleistungen](/help/journey-onboarding/assets/assign-team1.png)

1. Navigieren Sie zur Instanz und wählen Sie sie aus.

   ![Instanz auswählen](/help/journey-onboarding/assets/cloud-profiles-1.png)

1. Daraufhin wird die Liste AEM as a Cloud Service Produktprofile angezeigt, die einem Benutzer basierend auf seinen Benutzerrollen zugewiesen werden können.

   ![Produktprofile](/help/journey-onboarding/assets/cloud-profiles-2.png)

## Hinzufügen von Team-Mitgliedern zu Produktprofilen {#add-team-members}

Nachdem Sie sich mit den verfügbaren Profilen vertraut gemacht haben, können Sie sie Ihren Team-Mitgliedern nach Bedarf zuweisen.

Für diese Aufgaben müssen Sie Systemadministrator bei der **Business Owner** Cloud Manager-Produktprofil.

1. Navigieren Sie in Cloud Manager zu Ihrem Programm und wählen Sie die **Zugriff verwalten** -Schaltfläche aus dem Kontext der interessanten Umgebung.

   ![Zugriff verwalten](/help/journey-onboarding/assets/add-team1.png)

1. Über eine neue Registerkarte gelangen Sie zu der Admin Console, von der aus Sie auf die Autoreninstanz der Umgebung zugreifen können. Auswählen **AEM Administratoren** oder **AEM** basierend auf den Berechtigungen, die diese Person erhalten muss.

   ![Zugriff zuweisen](/help/journey-onboarding/assets/add-team2.png)

1. Wählen Sie `AEM Administrator` oder `AEM User` aus und klicken Sie auf **Benutzer hinzufügen**, wie unten dargestellt. Übermitteln Sie die erforderlichen Details, um das Hinzufügen des Team-Mitglieds abzuschließen.

   ![Team-Mitglied hinzufügen](/help/journey-onboarding/assets/add-team3.png)

1. Wiederholen Sie diese Schritte für alle Umgebungen, einschließlich Entwicklung, Staging und Produktion, wenn Sie über die Informationen der Teammitglieder verfügen, die Zugriff benötigen.

Der Benutzer, den Sie hinzugefügt haben, hat jetzt Zugriff auf die AEM as a Cloud Service-Autoren-Services!

## Tour beendet? {#the-end}

Herzlichen Glückwunsch! Die Benutzer, die Sie AEM as a Cloud Service Produktprofilen zugewiesen haben, sind jetzt bereit, auf die AEM Authoring-Umgebung zuzugreifen und mit der Erstellung von Inhalten mit AEM as a Cloud Service zu beginnen. Ebenso können Entwickler jetzt auf Cloud Manager zugreifen, um Git zum Speichern von benutzerdefiniertem Anwendungs-Code und dessen Bereitstellung zu verwenden. In diesem Sinne ist Ihre Onboarding-Journey abgeschlossen und Ihre Benutzer können jetzt AEMaaCS verwenden.

Wenn Sie jedoch besser verstehen möchten, wie Autoren und Entwickler das System verwenden, können Sie mit zwei optionalen Teilen dieser Onboarding-Journey fortfahren:

* [Aufgaben für Entwickler und Bereitstellungs-Manager](developers.md) - Hier erfahren Sie, wie Entwickler auf Git zugreifen, um ihren benutzerdefinierten Code zu speichern und ihn mithilfe von Cloud Manager-Pipelines bereitzustellen.
* [AEM Benutzeraufgaben](aem-users.md) - Hier erfahren Sie, wie Sie auf die AEM-Umgebung zugreifen können, in der Sie Inhalte erstellen können.

## Zusätzliche Ressourcen {#additional-resources}

* [Verwalten von Produkten und Benutzerzugriff in der Admin Console](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console) - Erfahren Sie, wie Sie mit der Admin Console den Benutzerzugriff verwalten.
* [Zugriff auf AEM konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=de) - Sehen Sie sich diese kurze Anleitung an, um mehr über die Konfiguration von Adobe IMS-Benutzern, Benutzergruppen und Produktprofilen in der Admin Console zu erfahren.

