---
title: Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder den Cloud Manager-Produktprofilen zuordnen können.
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: ht
source-wordcount: '1520'
ht-degree: 100%

---


# Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen {#assign-team-members}

In diesem Teil der [Onboarding-Tour](overview.md) erfahren Sie, wie Sie Team-Mitgliedern Cloud Manager-Produktprofilen zuweisen.

## Ziel {#objective}

Im vorherigen Schritt dieser Tour, [Zugang zur Admin Console](admin-console.md), haben Sie erfahren, wie Sie sich bei der Admin Console anmelden und Ihre Berechtigungen als Systemadmin prüfen können. Jetzt lernen Sie, wie Sie Ihren Team-Mitgliedern Zugriff auf Cloud Manager gewähren. Dazu weisen Sie Produktprofile zu.

Wenn Sie Benutzenden Zugriff auf eine bestimmte Adobe-Lösung gewähren, möchten Sie ihnen nicht unbedingt uneingeschränkten Zugriff gewähren. Mit Produktprofilen kann jeder Lösung ein eigener Satz von Benutzerberechtigungen zugewiesen werden. Sie verwenden die Admin Console, um Produktprofile zuzuweisen.

Der erste Schritt besteht darin, Benutzenden Zugriff auf Cloud Manager zu gewähren. Cloud Manager unterstützt Sie bei Ihren internen Entwicklungsprojekten und durch die speziell dafür vorgesehenen CI/CD-Pipelines, mit denen Sie gründliche Tests durchführen und höchste Code-Qualität und außergewöhnliche Erlebnisse bereitstellen können.

Nach dem Lesen dieses Dokuments sollten Sie Folgendes können:

* Überblick darüber, was Produktprofile sind.
* Überblick darüber, was Cloud Manager ist.
* Überblick über die drei zentralen Cloud Manager-Produktprofile: **Geschäftsinhaber**, **Bereitstellungs-Manager** und **Entwickler**.
* Sie können Team-Mitglieder den Cloud Manager-Produktprofilen zuordnen.

## Voraussetzungen {#prerequisites}

Um Produktprofilen Team-Mitglieder zuweisen zu können, benötigen Sie Details zu Ihren Team-Mitgliedern, die auf AEM as a Cloud Service zugreifen müssen, darunter:

* Namen
* E-Mail-Adressen
* Rollen und Zuständigkeiten

>[!TIP]
>
>Für das Onboarding empfiehlt Adobe, zunächst Benutzende hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren.
>
>Sie können den Onboarding-Prozess fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie weitere Benutzer hinzufügen.

## Produktprofile {#product-profiles}

Wenn Sie Benutzenden Zugriff auf eine bestimmte Adobe-Lösung gewähren, möchten Sie ihnen nicht unbedingt uneingeschränkten Zugriff gewähren. Durch Produktprofile können für jede Lösung eigene Benutzerberechtigungen vergeben werden, die mithilfe der Admin Console festgelegt werden.

Später in dieser Tour werden Sie beispielsweise die Admin Console verwenden, um Benutzenden Zugriff auf AEM zu gewähren, indem Sie AEM-Administratoren und AEM-Autoren Produktprofile zuweisen.

Als Nächstes werden Sie aber Produktprofile zuweisen, damit Ihre Team-Mitglieder Zugriff auf Cloud Manager haben.

## Cloud Manager {#cloud-manager}

Als Systemadministrator bzw. -administratorin wissen Sie, dass ein erfolgreiches AEM as a Cloud Service-Projekt nicht nur von der Erstellung ansprechender Inhalte mithilfe von AEM abhängt, sondern auch von der Entwicklung und Implementierung Ihres eigenen benutzerdefinierten Codes und von Anwendungen zur Bereitstellung Ihrer AEM-Inhalte.

Cloud Manager ist ein integraler Bestandteil von AEM as a Cloud Service und wird verwendet, um Ihre CI/CD-Pipelines für die Code-Bereitstellung, Ihre Code-Repositorys und Ihre Umgebungen zu verwalten.

Bevor Ihre Team-Mitglieder weitere Aktionen durchführen kann, müssen sie mit Cloud Manager integriert werden, indem ihnen die erforderlichen Produktprofile zugewiesen werden. Die nächsten Schritte zeigen Ihnen, wo Sie das Cloud Manager-Produktprofil mithilfe der Admin Console finden und wie Sie es Ihren Team-Mitgliedern zuweisen können.

## Überprüfen von Cloud Manager-Produktprofilen {#review-product-profiles}

In der Admin Console können Sie die Liste der Cloud Manager-Profile einsehen.

1. Melden Sie sich bei der Adobe Admin Console unter [adminconsole.adobe.com](https://adminconsole.adobe.com/) an und wählen Sie auf der Seite **Übersicht** von der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![AEM als Produkt](/help/journey-onboarding/assets/assign-team1.png)

1. Gehen Sie in der Liste aller Instanzen zur Instanz **Cloud Manager**.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. Es wird Ihnen eine Liste der vorkonfigurierten Cloud Manager-Produktprofile angezeigt.

   ![Produktprofile](/help/journey-onboarding/assets/assign-team3.png)

Dies sind die wichtigsten Profile, die im Rahmen des ursprünglichen Onboarding-Prozesses zugewiesen werden:

* **Geschäftsinhaber** - Diese Benutzenden verwalten verschiedene Programme.
* **Bereitstellungs-Manager** - Diese Benutzenden stellen Code aus Ihren Repositorys für aktive AEM-Umgebungen bereit.
* **Entwickler** - Diese Benutzenden entwickeln Ihre benutzerdefinierten AEM-Anwendungen und übertragen Code in Ihre Repositorys.

Mit der Kenntnis dieser Rollen und ihrer Funktionen können Sie jetzt Ihre Liste der Team-Mitglieder prüfen und feststellen, wer welches Profil benötigt. Beachten Sie, dass Benutzende in Ihrem Team mehrere Rollen haben können und häufig auch haben und daher mehrere Profile benötigen.

## Zuweisen des Produktprofils für Geschäftsinhaber {#assign-business-owner}

Sie können jetzt Benutzende hinzufügen und dem Produktprofil **Geschäftsinhaber** zuweisen.

1. Ermitteln Sie die Benutzenden, die Cloud Manager-Programme verwalten müssen. Dies sind Ihre **Geschäftsinhaberinnen und -inhaber**.

1. Melden Sie sich bei der Admin Console unter `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` an und wählen Sie auf der Seite **Übersicht** in der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Produkte und Services](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für den **ID-Typ** aus.

   ![Hinzufügen von Benutzerdetails](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte oder Benutzergruppen auswählen**, um mit der Produktauswahl zu beginnen, und wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Geschäftsinhaber** zu.

   * Weisen Sie jeden Benutzer mindestens einem Produktprofil zu, damit der Benutzer auf Cloud Manager zugreifen kann.
   * Denken Sie daran, sich selbst als Systemadministrator bzw. -administratorin die Rolle **Geschäftsinhaber** zuzuweisen.

   ![Zuweisen von Benutzern](/help/journey-onboarding/assets/assign-team6.png)

1. Klicken Sie auf **Speichern** und dem hinzugefügten Benutzer wird eine Begrüßungs-E-Mail gesendet. Er kann jetzt auf Cloud Manager zugreifen, indem er auf den Link in der Begrüßungs-E-Mail klickt und sich mithilfe einer Adobe ID anmeldet.

1. Wiederholen Sie diese Schritte für die Benutzer in Ihrem Team.

Ihre **Geschäftsinhaber** wurden zugewiesen und können jetzt auf Cloud Manager zugreifen. Vergessen Sie nicht, sich als Systemadministrator bzw. -administratorin auch selbst das Profil **Geschäftsinhaber** zuzuweisen.

## Zuweisen des Produktprofils für Bereitstellungs-Manager {#assign-deployment-manager}

1. Identifizieren Sie die Benutzenden, die Code bereitstellen.

1. Melden Sie sich bei der Admin Console unter `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` an und wählen Sie auf der Seite **Übersicht** in der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Produkte und Services](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für den **ID-Typ** aus.

   ![Eingeben der Kennung](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte oder Benutzergruppen auswählen**, um mit der Produktauswahl zu beginnen, und wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Bereitstellungs-Manager** zu.

   ![Zuweisen eines Profils](/help/journey-onboarding/assets/assign-team6.png)

Ihre **Bereitstellungs-Manager** wurden zugewiesen und können jetzt auf Cloud Manager zugreifen. Abhängig von Ihren künftigen Aufgaben müssen Sie sich möglicherweise auch als Systemadministrator dem **Bereitstellungs-Manager**-Profil zuweisen.

## Zuweisen des Produktprofils für Entwickler {#assign-developer}

1. Prüfen Sie, welche Benutzer AEM-Programme entwickeln und Code verwalten müssen.

1. Melden Sie sich bei Adobe Admin Console unter `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` an und wählen Sie auf der Seite **Übersicht** auf der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Produkte und Services](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für den **ID-Typ** aus.

   ![Hinzufügen der Benutzer-ID](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte oder Benutzergruppen auswählen**, um mit der Produktauswahl zu beginnen, und wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Entwickler** zu.

   ![Zuweisen eines Profils](/help/journey-onboarding/assets/assign-team6.png).

Ihre **Entwickler** wurden zugewiesen und können jetzt auf Cloud Manager zugreifen. Je nach Ihren künftigen Aufgaben müssen Sie sich möglicherweise auch als Systemadmin dem **Entwickler**-Profil zuweisen.

## So geht es weiter {#whats-next}

Herzlichen Glückwunsch! Jetzt ist Ihr neu zusammengestelltes Cloud Manager-Team eingerichtet, das auch das Profil **Geschäftsinhaber** für Sie selbst beinhaltet. In der Rolle des **Geschäftsinhabers** sind Sie jetzt nur noch einen Schritt davon entfernt, sich bei Cloud Manager anzumelden und die Erstellung Ihrer Cloud-Ressourcen zu ermöglichen.

In diesem Teil der Onboarding-Tour haben Sie alles über das Zuweisen Ihrer Team-Mitglieder zu Profilen in Admin Console erfahren. Sie sollten jetzt folgende Punkte erfüllen:

* Überblick darüber, was Produktprofile sind.
* Überblick darüber, was Cloud Manager ist.
* Überblick über die drei zentralen Cloud Manager-Produktprofile: **Geschäftsinhaber**, **Bereitstellungs-Manager** und **Entwickler**.
* Sie können Team-Mitglieder den Cloud Manager-Produktprofilen zuordnen.

Sie sind nun bereit, Ihre Onboarding-Tour fortzusetzen, indem Sie als Nächstes das Dokument [Zugriff auf Cloud Manager](cloud-manager.md) durchsehen. Hier wird beschrieben, wie Sie auf Cloud Manager zugreifen und Ihre Projektressourcen erstellen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, die Onboarding-Tour wie zuvor beschrieben fortzusetzen. Dies sind einige zusätzliche Ressourcen, wenn Sie einen tieferen Einblick in ein bestimmtes Thema dieser Tour wünschen.

* [Einführung in Cloud Manager](/help/onboarding/cloud-manager-introduction.md) - Erfahren Sie mehr über Cloud Manager und Cloud Manager-Programme und -Umgebungen.
* [Cloud Manager-Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md) - Erfahren Sie mehr über ein AEM as a Cloud Service-Team und Produktprofile.
* [Identitätstypen in Adobe Admin Console](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/identity.ug.html) – Das Identitätsverwaltungssystem von Adobe hilft Admins beim Erstellen und Verwalten des Benutzerzugriffs auf Programme und Services. Adobe bietet diese Identitätstypen oder -konten an, um Benutzende zu authentifizieren und zu autorisieren.

