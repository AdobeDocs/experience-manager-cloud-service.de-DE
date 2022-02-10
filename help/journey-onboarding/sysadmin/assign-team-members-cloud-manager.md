---
title: Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder den Cloud Manager-Produktprofilen zuordnen können.
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 22a08a0cb80052485309ce3d33537e9fe303c6f5
workflow-type: tm+mt
source-wordcount: '1154'
ht-degree: 25%

---

# Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen {#assign-team-members}

Im vorherigen Schritt in dieser Journey [Erste Schritte mit dem Onboarding-Prozess](/help/journey-onboarding/sysadmin/get-started-onboarding-journey.md), haben Sie jetzt gelernt, sich bei der Admin Console anzumelden und Ihre Berechtigungen als Systemadministrator angezeigt. Sie können jetzt Team-Mitglieder Cloud Manager-Produktprofilen zuweisen.

## Ziel {#objective}

In diesem Dokument wird zusammengefasst, wie Sie von der Adobe Admin Console aus Cloud Manager-Produktprofilen Team-Mitglieder zuweisen. Nach der Zuweisung können diese Mitglieder dann eine Zugriff-Cloud-Ressource erstellen, wie im nächsten Schritt dieser Journey beschrieben.

Nach dem Lesen dieses Abschnitts sollten Sie zu Folgendem in der Lage sein:

* Verstehen, warum und wie Sie Team-Mitglieder hinzufügen müssen.
* Erfahren Sie mehr über drei wichtige Cloud Manager-Produktprofile: **Business Owner**, **Bereitstellungsmanager** und **Entwickler**.
* Weisen Sie Team-Mitglieder Cloud Manager-Produktprofilen zu.

>[!TIP]
>
>Für das Onboarding empfehlen wir, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Onboarding-Prozess fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie weitere Benutzer hinzufügen.

## Voraussetzungen {#prerequisites}

Die folgenden Voraussetzungen müssen erfüllt sein, bevor Sie mit diesem Abschnitt beginnen. Sie müssen:

* Seien Sie Systemadministrator und verstehen Sie die Cloud Manager-Produktprofile.
   * Kehren Sie zu [Übersicht über Onboarding-Journey](onboarding-journey-overview.md) wenn Sie mit diesen Konzepten nicht vertraut sind.
* Mit den Grundlagen zur Adobe Admin Console vertraut sein.
   * Kehren Sie zu [Übersicht über Onboarding-Journey](onboarding-journey-overview.md) wenn Sie mit diesen Konzepten nicht vertraut sind.
* Sie erhalten Details zu Ihren Teammitgliedern, die as a Cloud Service auf AEM zugreifen müssen, darunter
   * Namen
   * E-Mail-Adressen
   * Rollen und Zuständigkeiten

## Überprüfen von Cloud Manager-Produktprofilen {#review-product-profiles}

In Adobe Admin Console wird die Liste der Cloud Manager-Profile angezeigt.

1. Melden Sie sich bei Adobe Admin Console an unter [adminconsole.adobe.com](https://adminconsole.adobe.com/) und von **Übersicht** Seite, wählen Sie **Adobe Experience Manager as a Cloud Service** von **Produkte und Dienstleistungen** Karte.

   ![AEM als Produkt](/help/journey-onboarding/assets/assign-team1.png)

1. Gehen Sie in der Liste aller Instanzen zur Instanz **Cloud Manager**.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. Sie sehen die Liste der vorkonfigurierten Cloud Manager-Produktprofile.

   ![Produktprofile](/help/journey-onboarding/assets/assign-team3.png)

## Zuweisen von Benutzern zum Produktprofil „Geschäftsinhaber“ {#assign-users-business-owner}

Sie können jetzt Benutzer hinzufügen und sie dem **Business Owner** Produktprofil.

1. Ermitteln Sie den/die Benutzer, der/die Cloud Manager-Programme verwalten wird/werden, und fügen Sie ihn/sie dem Produktprofil „Geschäftsinhaber“ hinzu.

1. Melden Sie sich bei der Admin Console an unter [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) und auf **Übersicht** Seite, wählen Sie **Adobe Experience Manager as a Cloud Service** Produkt aus **Produkte und Dienstleistungen** Karte.

   ![Produkte und Dienstleistungen](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Im **Benutzer zu Ihrem Team hinzufügen** Geben Sie die E-Mail-Adresse des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für **ID-Typ**.

   ![Benutzerdetails hinzufügen](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter **Produkte oder Benutzergruppen auswählen** Überschrift zur Produktauswahl und Auswahl **Adobe Experience Manager as a Cloud Service** und zuweisen **Business Owner** Produktprofil an den Benutzer.

   * Weisen Sie jeden Benutzer mindestens einem Produktprofil zu, damit der Benutzer auf Cloud Manager zugreifen kann.
   * Denken Sie daran, sich selbst als Systemadministrator dem **Business Owner** Rolle.

   ![Zuweisen von Benutzern](/help/journey-onboarding/assets/assign-team6.png)

1. Klicken **Speichern** und dem hinzugefügten Benutzer wird eine Begrüßungs-E-Mail gesendet. Er kann jetzt auf Cloud Manager zugreifen, indem er auf den Link in der Begrüßungs-E-Mail klickt und sich mithilfe einer Adobe ID anmeldet.

1. Wiederholen Sie diese Schritte für die Benutzer in Ihrem Team.

Ihr neu gegründetes Cloud Manager-Team (einschließlich Ihres dem **Business Owner** Rolle) eingerichtet wurde. In der Rolle von **Business Owner** sind Sie jetzt nur einen Schritt von der Anmeldung bei Cloud Manager und der Erstellung Ihrer Cloud-Ressourcen entfernt.

## Zuweisen von Benutzern zum Produktprofil „Implementierungs-Manager“ {#assign-users-deployment-manager}

1. Ermitteln Sie die Benutzer, die Cloud Manager-Programme verwalten sollen, und fügen Sie sie zum Produktprofil „Implementierungs-Manager“ hinzu.

1. Melden Sie sich bei der Admin Console an unter [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) und auf **Übersicht** Seitenauswahl **Adobe Experience Manager as a Cloud Service** aus **Produkte und Dienstleistungen** Karte.

   ![Produkte und Dienstleistungen](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie die **Benutzer** Registerkarte oben in der Navigation und wählen Sie **Benutzer hinzufügen**.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Im **Benutzer zu Ihrem Team hinzufügen** Geben Sie die E-Mail-Adresse des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für **ID-Typ**.

   ![Kennung eingeben](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter **Produkte oder Benutzergruppen auswählen** Überschrift zur Produktauswahl und Auswahl **Adobe Experience Manager as a Cloud Service** und zuweisen **Bereitstellungsmanager** Produktprofil an den Benutzer.

   ![Profil zuweisen](/help/journey-onboarding/assets/assign-team6.png).

## Zuweisen von Benutzern zum Produktprofil „Entwickler“ {#assign-users-developer}

1. Identifizieren Sie die Benutzer, die Cloud Manager-Programme verwalten.

1. Melden Sie sich bei der Admin Console an unter [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) und auf **Übersicht** Seitenauswahl **Adobe Experience Manager as a Cloud Service** aus **Produkte und Dienstleistungen** Karte.

   ![Produkte und Dienstleistungen](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie die **Benutzer** Registerkarte oben in der Navigation und wählen Sie **Benutzer hinzufügen**.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. In **Benutzer zu Ihrem Team hinzufügen** Geben Sie die E-Mail-Adresse des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für **ID-Typ**.

   ![Benutzer-ID hinzufügen](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter **Produkte oder Benutzergruppen auswählen** Überschrift zur Produktauswahl und Auswahl **Adobe Experience Manager as a Cloud Service** und zuweisen **Entwickler** Produktprofil an den Benutzer.

   ![Profil zuweisen](/help/journey-onboarding/assets/assign-team6.png).

## Wie geht es weiter? {#whats-next}

In diesem Teil des Onboarding-Journey haben Sie alles über die Zuweisung Ihrer Teammitglieder zu Rollen in der Admin Console erfahren. Sie sollten jetzt:

* Verstehen, warum und wie Sie Team-Mitglieder hinzufügen müssen.
* Machen Sie sich mit drei wichtigen Cloud Manager-Produktprofilen vertraut: **Business Owner**, **Bereitstellungsmanager** und **Entwickler**.
* Sie können Team-Mitglieder Cloud Manager-Produktprofilen zuweisen.

Sie sind nun bereit, mit der Onboarding-Tour fortzufahren, indem Sie als Nächstes das Dok [ument Einrichten von Cloud-Ressourcen über Cloud Manager](/help/journey-onboarding/sysadmin/setup-cloud-resources-via-cloud-manager.md) lesen, in dem Sie mehr über Folgendes erfahren:

1. Damit andere Geschäftsinhaber Programme erstellen können, müssen Sie als Systemadministrator, der dem **Business Owner** Rolle, muss zuerst auf Cloud Manager zugreifen und sich dort anmelden.
1. Wie ein Benutzer mit dem **Business Owner** Rolle kann sich anmelden und Ihre Cloud-Ressourcen einrichten, einschließlich Ihres Cloud-Programms und Ihrer Umgebungen.
1. So verwenden Benutzer mit **Entwickler** und **Bereitstellungsmanager** -Rollen können auf Cloud Manager zugreifen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, auf der Onboarding-Journey weiterzumachen, wie zuvor beschrieben. Dies sind einige zusätzliche Ressourcen, wenn Sie einen tiefen Einblick in ein bestimmtes Thema von dieser Journey wünschen.

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=de)
* [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles)
* [Identitätsüberblick für die Admin Console](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
