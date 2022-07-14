---
title: Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder Cloud Manager-Produktprofilen zuweisen.
feature: Onboarding
role: Admin, User, Developer
exl-id: 555688e5-f937-462c-9fcc-b90685f1882b
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '1534'
ht-degree: 42%

---


# Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen {#assign-team-members}

In diesem Teil des [Onboarding-Journey,](overview.md) Hier erfahren Sie, wie Sie Team-Mitglieder Cloud Manager-Produktprofilen zuweisen.

## Ziel {#objective}

Im vorherigen Schritt in dieser Journey [Zugriff auf die Admin Console,](admin-console.md) Sie haben jetzt gelernt, sich bei der Admin Console anzumelden und Ihre Berechtigungen als Systemadministrator zu überprüfen. Jetzt können Sie Ihren Teammitgliedern Zugriff auf Cloud Manager gewähren. Dazu weisen Sie Produktprofile zu.

Wenn Sie Benutzern Zugriff auf eine Adobe-Lösung gewähren, möchten Sie ihnen nicht unbedingt uneingeschränkten Zugriff gewähren. Produktprofile ermöglichen es jeder Lösung, über eigene Benutzerberechtigungen zu verfügen. Sie verwenden die Admin Console, um Produktprofile zuzuweisen.

Der erste Schritt besteht darin, Benutzern Zugriff auf Cloud Manager zu gewähren. Cloud Manager unterstützt Sie mit Unternehmensentwicklungs-Setups und den speziell dafür vorgesehenen CI/CD-Pipelines, die für gründliche Tests und höchste Code-Qualität ausgelegt sind und außergewöhnliche Erlebnisse bieten.

Nach Lesen dieses Dokuments sollten Sie Folgendes können:

* Erfahren Sie, welche Produktprofile sind.
* Erfahren Sie, was Cloud Manager ist.
* Machen Sie sich mit den drei wichtigen Cloud Manager-Produktprofilen vertraut: **Business Owner**, **Bereitstellungsmanager** und **Entwickler**.
* Sie müssen in der Lage sein, Teammitglieder den Cloud Manager-Produktprofilen zuzuordnen.

## Voraussetzungen {#prerequisites}

Um Produktprofilen Teammitglieder zuzuweisen, benötigen Sie Details zu Ihren Teammitgliedern, die auf AEM as a Cloud Service zugreifen müssen, darunter:

* Namen
* E-Mail-Adressen
* Rollen und Zuständigkeiten

>[!TIP]
>
>Zum Onboarding empfiehlt Adobe, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren.
>
>Sie können den Onboarding-Prozess fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie weitere Benutzer hinzufügen.

## Produktprofile {#product-profiles}

Wenn Sie Benutzern Zugriff auf eine Adobe-Lösung gewähren, möchten Sie ihnen nicht unbedingt uneingeschränkten Zugriff gewähren. Produktprofile ermöglichen es jeder Lösung, über eigene Benutzerberechtigungen zu verfügen, die mithilfe der Admin Console festgelegt werden.

Später in dieser Journey verwenden Sie beispielsweise die Admin Console, um Benutzern Zugriff auf die AEM zu gewähren, indem Sie Produktprofile für AEM Administratoren und AEM Autoren zuweisen.

Der nächste Schritt besteht jedoch darin, Produktprofile zu gewähren, damit Ihre Teammitglieder zunächst Zugriff auf Cloud Manager haben.

## Cloud Manager {#cloud-manager}

Als Systemadministrator wissen Sie, dass ein erfolgreiches AEM as a Cloud Service Projekt nicht nur von der Erstellung erstaunlicher Inhalte mithilfe von AEM abhängt, sondern auch von der Entwicklung und Implementierung Ihres eigenen benutzerdefinierten Codes und von Anwendungen zur Bereitstellung Ihrer AEM Inhalte.

Cloud Manager ist ein integraler Bestandteil AEM as a Cloud Service Programms und wird verwendet, um Ihre CI/CD-Pipelines für die Codebereitstellung zu verwalten, Ihre Code-Repositorys zu verwalten und Ihre Umgebungen zu verwalten.

Bevor Ihr Team weitere Aktionen durchführen kann, müssen diese mit Cloud Manager integriert werden, indem die erforderlichen Produktprofile zugewiesen werden. Die nächsten Schritte zeigen Ihnen, wo Sie das Cloud Manager-Produktprofil mithilfe der Admin Console finden und wie Sie es Ihren Teammitgliedern zuweisen.

## Überprüfen von Cloud Manager-Produktprofilen {#review-product-profiles}

Mithilfe der Admin Console können Sie die Liste der Cloud Manager-Profile anzeigen.

1. Melden Sie sich bei der Adobe Admin Console unter [adminconsole.adobe.com](https://adminconsole.adobe.com/) an und wählen Sie auf der Seite **Übersicht** von der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![AEM als Produkt](/help/journey-onboarding/assets/assign-team1.png)

1. Gehen Sie in der Liste aller Instanzen zur Instanz **Cloud Manager**.

   ![Cloud Manager](/help/journey-onboarding/assets/assign-team2.png)

1. Sie sehen die Liste der vorkonfigurierten Cloud Manager-Produktprofile.

   ![Produktprofile](/help/journey-onboarding/assets/assign-team3.png)

Die wichtigsten Profile, die im Rahmen des anfänglichen Onboarding-Prozesses zugewiesen werden, sind:

* **Business Owner** - Diese Benutzer verwalten verschiedene Programme.
* **Bereitstellungsmanager** - Diese Benutzer stellen Code aus Ihren Repositorys für die Ausführung AEM Umgebungen bereit.
* **Entwickler** - Diese Benutzer entwickeln Ihre benutzerdefinierten AEM-Programme und übertragen Code in Ihre Repositorys.

Überprüfen Sie Ihre Liste der Teammitglieder, um festzustellen, wer welches Profil benötigt, und wissen Sie, was diese Rollen sind und was sie tun. Beachten Sie, dass Benutzer in Ihrem Team mehrere Rollen haben können und häufig haben und daher auch mehrere Profile benötigen.

## Zuweisen des Produktprofils für Business Owner {#assign-business-owner}

Sie können jetzt Benutzer hinzufügen und sie dem Cloud Manager-Produktprofil **Geschäftsinhaber** zuweisen.

1. Identifizieren Sie die Benutzer, die Cloud Manager-Programme verwalten müssen. Diese werden **Betriebsinhaber**.

1. Melden Sie sich bei der Adobe Admin Console unter `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` an und wählen Sie auf der Seite **Übersicht** von der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Produkte und Services](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für den **ID-Typ** aus.

   ![Hinzufügen von Benutzerdetails](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte oder Benutzergruppen auswählen**, um mit der Produktauswahl zu beginnen, und wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Geschäftsinhaber** zu.

   * Weisen Sie jeden Benutzer mindestens einem Produktprofil zu, damit der Benutzer auf Cloud Manager zugreifen kann.
   * Denken Sie daran, sich selbst als Systemadministrator dem **Business Owner** Rolle.

   ![Zuweisen von Benutzern](/help/journey-onboarding/assets/assign-team6.png)

1. Klicken Sie auf **Speichern** und dem hinzugefügten Benutzer wird eine Begrüßungs-E-Mail gesendet. Er kann jetzt auf Cloud Manager zugreifen, indem er auf den Link in der Begrüßungs-E-Mail klickt und sich mithilfe einer Adobe ID anmeldet.

1. Wiederholen Sie diese Schritte für die Benutzer in Ihrem Team.

Ihre **Business Owner** wurden zugewiesen und können jetzt auf Cloud Manager zugreifen. Vergessen Sie nicht, sich auch als Systemadministrator dem **Business Owner** Profil.

## Zuweisen des Deployment Manager-Produktprofils {#assign-deployment-manager}

1. Identifizieren Sie die Benutzer, die Code bereitstellen müssen.

1. Melden Sie sich bei der Adobe Admin Console unter `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` an und wählen Sie auf der Seite **Übersicht** von der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Produkte und Services](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für den **ID-Typ** aus.

   ![Eingeben der Kennung](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte oder Benutzergruppen auswählen**, um mit der Produktauswahl zu beginnen, und wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Implementierungs-Manager** zu.

   ![Zuweisen eines Profils](/help/journey-onboarding/assets/assign-team6.png)

Ihre **Bereitstellungsmanager** wurden zugewiesen und können jetzt auf Cloud Manager zugreifen. Abhängig von Ihrer künftigen Verantwortung müssen Sie sich möglicherweise auch als Systemadministrator dem **Bereitstellungsmanager** Profil.

## Zuweisen des Entwicklerproduktprofils {#assign-developer}

1. Identifizieren Sie die Benutzer, die AEM Anwendungen entwickeln und Code verwalten müssen.

1. Melden Sie sich bei der Adobe Admin Console unter `[adminconsole.adobe.com](https://adminconsole.adobe.com/enterprise/overview)` an und wählen Sie auf der Seite **Übersicht** von der Karte **Produkte und Services** die Option **Adobe Experience Manager as a Cloud Service** aus.

   ![Produkte und Services](/help/journey-onboarding/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![Benutzer hinzufügen](/help/journey-onboarding/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zum Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten.

   * Wenn die Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde, wählen Sie **Adobe ID** für den **ID-Typ** aus.

   ![Hinzufügen der Benutzer-ID](/help/journey-onboarding/assets/assign-team5.png)

1. Klicken Sie auf das Pluszeichen unter der Überschrift **Produkte oder Benutzergruppen auswählen**, um mit der Produktauswahl zu beginnen, und wählen Sie **Adobe Experience Manager as a Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Entwickler** zu.

   ![Zuweisen eines Profils](/help/journey-onboarding/assets/assign-team6.png).

Ihre **Entwickler** wurden zugewiesen und können jetzt auf Cloud Manager zugreifen. Abhängig von Ihrer künftigen Verantwortung müssen Sie sich möglicherweise auch als Systemadministrator dem **Entwickler** Profil.

## Wie geht es weiter? {#whats-next}

Herzlichen Glückwunsch! Ihr neu gegründetes Cloud Manager-Team (einschließlich Ihres dem **Business Owner** Profil) eingerichtet wurde. In der Rolle des **Geschäftsinhabers** sind Sie jetzt nur noch einen Schritt davon entfernt, sich bei Cloud Manager anzumelden und die Erstellung Ihrer Cloud-Ressourcen zu ermöglichen.

In diesem Teil der Onboarding-Journey haben Sie erfahren, wie Sie Ihre Teammitglieder Profilen in der Admin Console zuweisen. Sie sollten jetzt folgende Punkte erfüllen:

* Erfahren Sie, welche Produktprofile sind.
* Erfahren Sie, was Cloud Manager ist.
* Machen Sie sich mit den drei wichtigen Cloud Manager-Produktprofilen vertraut: **Business Owner**, **Bereitstellungsmanager** und **Entwickler**.
* Sie müssen in der Lage sein, Teammitglieder den Cloud Manager-Produktprofilen zuzuordnen.

Sie können jetzt mit dem Onboarding-Journey fortfahren, indem Sie das Dokument erneut überprüfen. [Zugriff auf Cloud Manager,](cloud-manager.md) Hier erfahren Sie, wie Sie auf Cloud Manager zugreifen und Ihre Projektressourcen erstellen.

## Zusätzliche Ressourcen {#additional-resources}

Es wird empfohlen, mit der Onboarding-Tour weiterzumachen, wie zuvor beschrieben. Dies sind einige zusätzliche Ressourcen, wenn Sie einen tieferen Einblick in ein bestimmtes Thema dieser Tour wünschen.

* [Einführung in Cloud Manager](/help/onboarding/cloud-manager-introduction.md) - Erfahren Sie mehr über Cloud Manager-, Cloud Manager-Programme und -Umgebungen.
* [Cloud Manager-Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md) - Erfahren Sie mehr über AEM as a Cloud Service Team und Produktprofile.
* [Identitätstypen in Adobe Admin Console](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/identity.ug.html) - Das Identitätsverwaltungssystem von Adobe hilft Administratoren beim Erstellen und Verwalten des Benutzerzugriffs auf Anwendungen und Dienste. Adobe bietet diese Identitätstypen oder -konten an, um Benutzer zu authentifizieren und zu autorisieren.

