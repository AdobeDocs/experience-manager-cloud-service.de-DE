---
title: Zuweisen von AEM-Produktprofilen
description: Nachdem Sie Ihre Cloud-Ressourcen konfiguriert haben, gewähren Sie Ihrem Team mithilfe AEM Produktprofilen Zugriff auf AEM selbst.
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: a3e79441d46fa961fcd05ea54e84957754890d69
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 79%

---

# Zuweisen von AEM-Produktprofilen {#assign-profiles-aem}

>[!CONTEXTUALHELP]
>id="assets_user_entitlements"
>title="Zuweisen von AEM-Produktprofilen"
>abstract="Sie sind nicht berechtigt, Experience Manager Assets zu verwenden. Kontaktieren Sie diesbezüglich Ihre Admins."

In diesem Teil des [Onboarding-Journey,](overview.md) Hier erfahren Sie, wie Sie Ihrem Team mithilfe AEM Produktprofilen Zugriff auf AEM gewähren.

## Ziel {#objective}

Nachdem Sie das vorherige Dokument in dieser Onboarding-Journey gelesen haben, [Erstellen von Umgebungen,](create-environments.md) und lassen Sie Ihre Cloud-Ressourcen konfiguriert sein, gewähren Sie Ihrem Team Zugriff auf AEM selbst mithilfe AEM Produktprofilen. Als Systemadmin weisen Sie dazu AEM-Produktprofile zu.

Nach dem Lesen dieses Dokuments wissen Sie Folgendes:

* Was sind AEM-Produktprofile?
* Wie man Team-Mitglieder zu AEM-Benutzer-Produktprofilen hinzufügt.
* Wie man Team-Mitglieder zu AEM-Administrator-Produktprofilen hinzufügt.

## AEM-Produktprofile {#aem-product-profiles}

Um AEM verwenden zu können, müssen Ihre Team-Mitglieder mindestens einem AEM-Produktprofil zugewiesen sein. Berechtigungen für den Zugriff auf Cloud Manager reichen nicht aus. Benutzende müssen zu einem von zwei Produktprofilen gehören:

* `AEM Users` - Zu dieser Gruppe gehören normale Benutzende, die alltägliche Aufgaben zum Erstellen von Inhalten ausführen.
* `AEM Administrators` - Diese Gruppe umfasst Benutzende, die für erweiterte Funktionen oder AEM verantwortlich sind.

>[!NOTE]
>
>Jede Person, die einem AEM as a Cloud Service-Produktprofil zugewiesen ist, hat über die Rolle **Cloud Manager-Benutzer** schreibgeschützten Zugriff auf Cloud Manager.
>
>Benutzerinnen und Benutzer, die nur die Rolle **Cloud Manager-Benutzer** haben, können sich bei Cloud Manager anmelden und zu den AEM-Authoring-Umgebungen navigieren (falls vorhanden), indem sie die Menüoptionen unter „Anwendungen“ verwenden. Die Rolle **Cloud Manager-Benutzer** reicht nicht aus, um auf Programmdetails zuzugreifen. Wenn ein solcher Zugriff erforderlich ist, müssen Benutzende von ihrem Systemadministrator zusätzliche Rollen erhalten.
>Im [Abschnitt „Zusätzliche Ressourcen“ weiter unten](#additional-resources) finden Sie weitere Informationen zu Cloud Manager-Benutzerrollen.

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
>Für das Onboarding empfiehlt Adobe, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Rest des Onboarding fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie später die Anzahl von Benutzern ausweiten.

## AEM-Produktprofile anzeigen {#view-profiles}

Führen Sie diese Schritte aus, um die AEM-Produktprofile aus Admin Console anzuzeigen.

1. Melden Sie sich bei Admin Console unter [`https://adminconsole.adobe.com` an.](https://adminconsole.adobe.com)

1. Wählen Sie auf der Seite **Übersicht** die Option **Adobe Experience Manager as a Cloud Service** auf der Karte **Produkte und Services** aus.

   ![Karte „Produkte und Services“](/help/journey-onboarding/assets/assign-team1.png)

1. Navigieren Sie zur Instanz und wählen Sie sie aus.

   ![Instanz auswählen](/help/journey-onboarding/assets/cloud-profiles-1.png)

1. Sie können die Liste AEM as a Cloud Service Produktprofile anzeigen, die einem Benutzer basierend auf seinen Benutzerrollen zugewiesen werden können.

   ![Produktprofile](/help/journey-onboarding/assets/cloud-profiles-2.png)

## Team-Mitglieder zu Produktprofilen hinzufügen {#add-team-members}

Wenn Sie sich mit den verfügbaren Profilen vertraut gemacht haben, können Sie sie Ihren Team-Mitgliedern nach Bedarf zuweisen.

Für diese Aufgaben müssen Sie Systemadmin für das Produktprofil **Geschäftsinhaber** in Cloud Manager sein.

1. Gehen Sie in Cloud Manager zu Ihrem Programm und wählen Sie im Kontext der relevanten Umgebung den Button **Zugriff verwalten** aus.

   ![Zugriff verwalten](/help/journey-onboarding/assets/add-team1.png)

1. Über eine neue Registerkarte gelangen Sie zu Admin Console, von wo aus Sie Zugriff auf die Autoreninstanz der Umgebung haben. Wählen Sie **AEM-Admins** oder **AEM-Benutzer** basierend auf den Berechtigungen aus, die diese Person erhalten muss.

   ![Zugriff zuweisen](/help/journey-onboarding/assets/add-team2.png)

1. Auswählen `AEM Administrator` oder `AEM User` und klicken **Benutzer hinzufügen** wie unten gezeigt, und senden Sie die erforderlichen Details, um das Hinzufügen des Teammitglieds abzuschließen.

   ![Team-Mitglied hinzufügen](/help/journey-onboarding/assets/add-team3.png)

1. Sie sollten diese Schritte für alle Umgebungen wiederholen, einschließlich Entwicklung, Staging und Produktion, wenn Sie über diese Informationen zu den Team-Mitgliedern verfügen, die Zugriff benötigen.

Die Benutzenden, die Sie hinzugefügt haben, haben jetzt Zugriff auf die AEM as a Cloud Service-Autoren-Services.

## Tour beendet? {#the-end}

Herzlichen Glückwunsch! Die Benutzenden, die Sie AEM as a Cloud Service-Produktprofilen zugewiesen haben, sind jetzt bereit, auf die AEM-Authoring-Umgebung zuzugreifen und mit der Erstellung von Inhalten mit AEM as a Cloud Service zu beginnen. Ebenso können Entwickler jetzt auf Cloud Manager zugreifen, um Git zum Speichern von benutzerdefiniertem Programm-Code und dessen Bereitstellung zu verwenden. Insofern ist Ihre Onboarding-Journey abgeschlossen und Ihre Benutzenden können jetzt AEMaaCS verwenden.

Wenn Sie jedoch besser verstehen möchten, wie Autoren und Entwickler das System verwenden, können Sie mit zwei optionalen Teilen dieser Onboarding-Journey fortfahren:

* [Aufgaben für Entwickler und Bereitstellungs-Manager](developers.md) - Hier erfahren Sie, wie Entwickler auf Git zugreifen, um ihren benutzerdefinierten Code zu speichern und ihn mithilfe von Cloud Manager-Pipelines bereitzustellen.
* [AEM Benutzeraufgaben](aem-users.md) - Hier erfahren Sie, wie Sie auf die AEM-Umgebung zugreifen können, in der Sie mit der Erstellung von Inhalten beginnen können.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt der Onboarding-Tour hinausgehen möchten.

* [Team- und Produktprofile in AEM as a Cloud Service](/help/onboarding/aem-cs-team-product-profiles.md) – Erfahren Sie, wie Sie mit Team- und Produktprofilen in AEM as a Cloud Service den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren bzw. einschränken können.
* [Verwalten von Produkten und Benutzerzugriffen in der Admin Console](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console): Erfahren Sie, wie Sie die Admin Console zur Verwaltung des Benutzerzugriffs verwenden können.
* [Zugriff auf AEM konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=de): In dieser kurzen Anleitung erfahren Sie mehr über die Konfiguration von Adobe IMS-Benutzern, Benutzergruppen und Produktprofilen in Admin Console.

