---
title: Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder den Cloud Manager-Produktprofilen zuordnen können.
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 22a08a0cb80052485309ce3d33537e9fe303c6f5
workflow-type: ht
source-wordcount: '1154'
ht-degree: 100%

---

# Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen {#assign-team-members}

Im vorherigen Schritt in dieser Tour, [Erste Schritte mit dem Onboarding-Prozess](/help/journey-onboarding/sysadmin/get-started-onboarding-journey.md), haben Sie gelernt, sich bei der Admin Console anzumelden und haben Ihre Berechtigungen als Systemadministrator eingesehen. Sie können jetzt Team-Mitglieder zu Cloud Manager-Produktprofilen zuweisen.

## Ziel {#objective}

In diesem Dokument wird zusammengefasst, wie Sie von der Adobe Admin Console aus Cloud Manager-Produktprofilen Team-Mitglieder zuweisen. Nach der Zuweisung können diese Mitglieder dann Cloud-Ressourcen erstellen und darauf zugreifen, wie im nächsten Schritt dieser Tour beschrieben.

Nach dem Lesen dieses Abschnitts sollten Sie zu Folgendem in der Lage sein:

* Verstehen, warum und wie Sie Team-Mitglieder hinzufügen müssen.
* Lernen Sie drei verschiedene Cloud Manager-Produktprofile wie **Geschäftsinhaber**, **Implementierungs-Manager** und **Entwickler** kennen.
* Weisen Sie Team-Mitglieder zu Cloud Manager-Produktprofilen zu.

>[!TIP]
>
>Für das Onboarding empfiehlt Adobe, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Onboarding-Prozess fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie weitere Benutzer hinzufügen.

## Voraussetzungen {#prerequisites}

Vor dem Start dieses Abschnitts sollten die folgenden Voraussetzungen berücksichtigt werden. Sie müssen:

* Systemadministrator sein und Cloud Manager-Produktprofile verstehen.
   * Kehren Sie zu [Onboarding-Tour – Überblick](onboarding-journey-overview.md) zurück, wenn Sie mit diesen Konzepten nicht vertraut sind.
* Mit den Grundlagen zur Adobe Admin Console vertraut sein.
   * Kehren Sie zu [Onboarding-Tour – Überblick](onboarding-journey-overview.md) zurück, wenn Sie mit diesen Konzepten nicht vertraut sind.
* Halten Sie Details zu Ihren Team-Mitgliedern bereit, die auf AEM as a Cloud Service zugreifen müssen, darunter
   * Namen
   * E-Mail-Adressen
   * Rollen und Zuständigkeiten

## Überprüfen von Cloud Manager-Produktprofilen {#review-product-profiles}

In der Adobe Admin Console wird die Liste der Cloud Manager-Profile angezeigt.

1. Melden Sie sich bei der Adobe Admin Console unter [adminconsole.adobe.com](https://adminconsole.adobe.com/) an und wählen Sie auf der Seite **Übersicht** von der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![AEM als Produkt](/help/journey-onboarding/assets/assign-team1.png)

1. Gehen Sie in der Liste aller Instanzen zur Instanz **Cloud Manager**.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. Sie sehen die Liste der vorkonfigurierten Cloud Manager-Produktprofile.

   ![Produktprofile](/help/journey-onboarding/assets/assign-team3.png)

## Zuweisen von Benutzern zum Produktprofil „Geschäftsinhaber“ {#assign-users-business-owner}

Sie können jetzt Benutzer hinzufügen und sie dem Cloud Manager-Produktprofil **Geschäftsinhaber** zuweisen.

1. Ermitteln Sie den/die Benutzer, der/die Cloud Manager-Programme verwalten wird/werden, und fügen Sie ihn/sie dem Produktprofil „Geschäftsinhaber“ hinzu.

1. Melden Sie sich bei der Adobe Admin Console unter [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) an und wählen Sie auf der Seite **Übersicht** von der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Produkte und Services](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für den **ID-Typ** aus.

   ![Hinzufügen von Benutzerdetails](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte oder Benutzergruppen auswählen**, um mit der Produktauswahl zu beginnen, und wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Geschäftsinhaber** zu.

   * Weisen Sie jeden Benutzer mindestens einem Produktprofil zu, damit der Benutzer auf Cloud Manager zugreifen kann.
   * Denken Sie daran, sich selbst als Systemadministrator der Rolle **Geschäftsinhaber** zuzuweisen.

   ![Zuweisen von Benutzern](/help/journey-onboarding/assets/assign-team6.png)

1. Klicken Sie auf **Speichern** und dem hinzugefügten Benutzer wird eine Begrüßungs-E-Mail gesendet. Er kann jetzt auf Cloud Manager zugreifen, indem er auf den Link in der Begrüßungs-E-Mail klickt und sich mithilfe einer Adobe ID anmeldet.

1. Wiederholen Sie diese Schritte für die Benutzer in Ihrem Team.

Jetzt wurde Ihr neu zusammengestelltes Cloud Manager-Team eingerichtet, das auch die Rolle **Geschäftsinhaber** für Sie selbst beinhaltet. In der Rolle des **Geschäftsinhabers** sind Sie jetzt nur noch einen Schritt davon entfernt, sich bei Cloud Manager anzumelden und die Erstellung Ihrer Cloud-Ressourcen zu ermöglichen.

## Zuweisen von Benutzern zum Produktprofil „Implementierungs-Manager“ {#assign-users-deployment-manager}

1. Ermitteln Sie die Benutzer, die Cloud Manager-Programme verwalten sollen, und fügen Sie sie zum Produktprofil „Implementierungs-Manager“ hinzu.

1. Melden Sie sich bei der Adobe Admin Console unter [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) an und wählen Sie auf der Seite **Übersicht** von der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Produkte und Services](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für den **ID-Typ** aus.

   ![Eingeben der Kennung](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte oder Benutzergruppen auswählen**, um mit der Produktauswahl zu beginnen, und wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Implementierungs-Manager** zu.

   ![Zuweisen eines Profils](/help/journey-onboarding/assets/assign-team6.png).

## Zuweisen von Benutzern zum Produktprofil „Entwickler“ {#assign-users-developer}

1. Ermitteln Sie den/die Benutzer, der/die Cloud Manager-Programme verwalten sollen.

1. Melden Sie sich bei der Adobe Admin Console unter [adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview) an und wählen Sie auf der Seite **Übersicht** von der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Produkte und Services](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für den **ID-Typ** aus.

   ![Hinzufügen der Benutzer-ID](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte oder Benutzergruppen auswählen**, um mit der Produktauswahl zu beginnen, und wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Entwickler** zu.

   ![Zuweisen eines Profils](/help/journey-onboarding/assets/assign-team6.png).

## Wie geht es weiter? {#whats-next}

In diesem Teil der Onboarding-Tour haben Sie alles über das Zuweisen Ihrer Teammitglieder zu Rollen in der Admin Console erfahren. Sie sollten jetzt folgende Punkte erfüllen:

* Verstehen, warum und wie Sie Team-Mitglieder hinzufügen müssen.
* Machen Sie sich mit drei wichtigen Cloud Manager-Produktprofilen vertraut: **Geschäftsinhaber**, **Implementierungs-Manager** und **Entwickler**.
* Sie müssen in der Lage sein, Teammitglieder den Cloud Manager-Produktprofilen zuzuordnen.

Sie sind nun bereit, mit der Onboarding-Tour fortzufahren, indem Sie als Nächstes das Dokument [Einrichten von Cloud-Ressourcen über Cloud Manager](/help/journey-onboarding/sysadmin/setup-cloud-resources-via-cloud-manager.md) lesen, in dem Sie mehr über Folgendes erfahren:

1. Damit andere Geschäftsverantwortliche Programme erstellen können, müssen Sie als Systemadministrator, der der Rolle **Geschäftsinhaber** zugewiesen ist, zuerst auf Cloud Manager zugreifen und sich dort anmelden.
1. Wie sich ein Cloud Manager-Benutzer mit der Rolle **Geschäftsinhaber** anmelden und Ihre Cloud-Ressourcen einschließlich Ihres Cloud-Programms und Ihrer Umgebungen einrichten kann.
1. Wie Benutzer mit den Rollen **Entwickler** und **Implementierungs-Manager** auf Cloud Manager zugreifen können.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, mit der Onboarding-Tour weiterzumachen, wie zuvor beschrieben. Dies sind einige zusätzliche Ressourcen, wenn Sie einen tieferen Einblick in ein bestimmtes Thema dieser Tour wünschen.

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=de)
* [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#cloud-manager-product-profiles)
* [Identitätsüberblick für die Admin Console](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
