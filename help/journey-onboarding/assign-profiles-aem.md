---
title: Zuweisen von AEM-Produktprofilen
description: Nachdem Sie Ihre Cloud-Ressourcen konfiguriert haben, müssen Sie Ihrem Team mithilfe von AEM-Produktprofilen Zugriff auf AEM gewähren.
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: 050e5966728e157bf2ae51f99a31f68a1d347e4b
workflow-type: ht
source-wordcount: '769'
ht-degree: 100%

---

# Zuweisen von AEM-Produktprofilen {#assign-profiles-aem}

In diesem Teil der [Onboarding-Journey](overview.md) erfahren Sie, wie Sie Ihrem Team mithilfe von AEM-Produktprofilen Zugriff auf AEM gewähren.

## Ziel {#objective}

Nachdem Sie das vorherige Dokument [Umgebungen erstellen](create-environments.md) in dieser Onboarding-Journey gelesen haben und Ihre Cloud-Ressourcen konfiguriert haben, müssen Sie Ihrem Team mithilfe von AEM-Produktprofilen Zugriff auf AEM gewähren. Als Systemadmin weisen Sie dazu AEM-Produktprofile zu.

Nach dem Lesen dieses Dokuments wissen Sie Folgendes:

* Was sind AEM-Produktprofile?
* Wie man Team-Mitglieder zu AEM-Benutzer-Produktprofilen hinzufügt.
* Wie man Team-Mitglieder zu AEM-Administrator-Produktprofilen hinzufügt.

## AEM-Produktprofile {#aem-product-profiles}

Um AEM verwenden zu können, müssen Ihre Team-Mitglieder mindestens einem AEM-Produktprofil zugewiesen sein. Berechtigungen für den Zugriff auf Cloud Manager reichen nicht aus. Benutzende müssen zu einem von zwei Produktprofilen gehören:

* `AEM Users` - Zu dieser Gruppe gehören normale Benutzende, die alltägliche Aufgaben zum Erstellen von Inhalten ausführen.
* `AEM Administrators` - Diese Gruppe umfasst Benutzende, die für erweiterte Funktionen oder AEM verantwortlich sind.

Alle Benutzenden, die einem AEM-Produktprofil zugewiesen ist, erhalten ebenfalls schreibgeschützten Zugriff auf Cloud Manager. Der Schreibzugriff auf Cloud Manager kann über andere Produktprofile gewährt werden.

>[!CAUTION]
>
>Die Produktprofile „AEM-Administrierende“ oder „AEM-Benutzende“ dürfen nicht bearbeitet oder gelöscht werden. Die Bearbeitung dieser Profilnamen kann einen Fehler bei der Anmeldung bei der AEM Cloud-Instanz erzeugen.

## Voraussetzungen {#prerequisites}

Wenn Sie diesen Abschnitt lesen, sollten Sie über die folgenden Informationen zu Ihrem Team verfügen, das AEM verwendet.

* Namen
* E-Mail-Adressen
* Rollen und Zuständigkeiten

>[!TIP]
>
>Für das Onboarding empfehlen wir, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Rest des Onboarding fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie später die Anzahl von Benutzern ausweiten.

## AEM-Produktprofile anzeigen {#view-profiles}

Führen Sie diese Schritte aus, um die AEM-Produktprofile aus Admin Console anzuzeigen.

1. Melden Sie sich bei Admin Console unter [`https://adminconsole.adobe.com` an.](https://adminconsole.adobe.com)

1. Wählen Sie auf der Seite **Übersicht** die Option **Adobe Experience Manager as a Cloud Service** auf der Karte **Produkte und Services** aus.

   ![Karte „Produkte und Services“](/help/journey-onboarding/assets/assign-team1.png)

1. Navigieren Sie zur Instanz und wählen Sie sie aus.

   ![Instanz auswählen](/help/journey-onboarding/assets/cloud-profiles-1.png)

1. Sie sehen die Liste der AEM as a Cloud Service-Produktprofile, die Benutzenden basierend auf ihrer Rolle zugewiesen werden müssen.

   ![Produktprofile](/help/journey-onboarding/assets/cloud-profiles-2.png)

## Team-Mitglieder zu Produktprofilen hinzufügen {#add-team-members}

Wenn Sie sich mit den verfügbaren Profilen vertraut gemacht haben, können Sie sie Ihren Team-Mitgliedern nach Bedarf zuweisen.

Für diese Aufgaben müssen Sie Systemadmin für das Produktprofil **Geschäftsinhaber** in Cloud Manager sein.

1. Gehen Sie in Cloud Manager zu Ihrem Programm und wählen Sie im Kontext der relevanten Umgebung den Button **Zugriff verwalten** aus.

   ![Zugriff verwalten](/help/journey-onboarding/assets/add-team1.png)

1. Über eine neue Registerkarte gelangen Sie zu Admin Console, von wo aus Sie Zugriff auf die Autoreninstanz der Umgebung haben. Wählen Sie **AEM-Admins** oder **AEM-Benutzer** basierend auf den Berechtigungen aus, die diese Person erhalten muss.

   ![Zugriff zuweisen](/help/journey-onboarding/assets/add-team2.png)

1. Wählen Sie `AEM Administrator` oder `AEM User` aus und klicken Sie auf **Benutzer hinzufügen**, wie unten dargestellt. Übermitteln Sie die erforderlichen Details, um das Hinzufügen des Team-Mitglieds abzuschließen.

   ![Team-Mitglied hinzufügen](/help/journey-onboarding/assets/add-team3.png)

1. Sie sollten diese Schritte für alle Umgebungen wiederholen, einschließlich Entwicklung, Staging und Produktion, wenn Sie über diese Informationen zu den Team-Mitgliedern verfügen, die Zugriff benötigen.

Die Benutzenden, die Sie hinzugefügt haben, haben jetzt Zugriff auf die AEM as a Cloud Service-Autoren-Services.

## Tour beendet? {#the-end}

Herzlichen Glückwunsch! Die Benutzenden, die Sie AEM as a Cloud Service-Produktprofilen zugewiesen haben, sind jetzt bereit, auf die AEM-Authoring-Umgebung zuzugreifen und mit der Erstellung von Inhalten mit AEM as a Cloud Service zu beginnen. Ebenso können Entwickler jetzt auf Cloud Manager zugreifen, um Git zum Speichern von benutzerdefiniertem Programm-Code und dessen Bereitstellung zu verwenden. Insofern ist Ihre Onboarding-Journey abgeschlossen und Ihre Benutzenden können jetzt AEMaaCS verwenden.

Wenn Sie jedoch besser verstehen möchten, wie Autoren und Entwickler das System verwenden, können Sie mit zwei optionalen Teilen dieser Onboarding-Journey fortfahren:

* [Aufgaben für Entwickler und Bereitstellungs-Manager](developers.md) - Hier erfahren Sie, wie Entwickler Git verwenden, um ihren benutzerdefinierten Code zu speichern und ihn mithilfe von Cloud Manager-Pipelines bereitzustellen.
* [AEM-Benutzeraufgaben](aem-users.md) - Hier erfahren Sie, wie Sie in die AEM-Umgebung gelangen, in der Sie Inhalte erstellen können.

## Zusätzliche Ressourcen {#additional-resources}

* [Verwalten von Produkten und Benutzerzugriff in der Admin Console](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console) - Erfahren Sie, wie Sie mit Admin Console den Zugriff der Benutzenden verwalten.
* [Zugriff auf AEM konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=de) - In dieser kurzen Anleitung erfahren Sie mehr über die Konfiguration von Adobe IMS-Benutzern, Benutzergruppen und Produktprofilen in Admin Console.

