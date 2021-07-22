---
title: 'Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen '
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder Cloud Manager-Produktprofilen zuweisen.
hide: true
hidefromtoc: true
index: false
source-git-commit: 3dbcc5dd09479a84ed13aad0ee3d8c229520e10f
workflow-type: tm+mt
source-wordcount: '1382'
ht-degree: 2%

---


# Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen {#assign-team-members}

Nachdem Sie gelernt haben, wie Sie sich bei [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en) anmelden und Ihre Berechtigungen als [Systemadministrator](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/system-administrator.html?lang=en) angezeigt haben, können Sie jetzt Cloud Manager-Produktprofilen Teammitglieder zuweisen.

## Zielsetzung {#objective}

In diesem Dokument wird zusammengefasst, wie Teammitglieder Cloud Manager-Produktprofilen aus der Admin Console zugewiesen werden.

Nach dem Lesen dieses Abschnitts sollten Sie in der Lage sein:

* Erfahren Sie, warum und wie Sie Team-Mitglieder hinzufügen müssen.
* Erfahren Sie mehr über drei verschiedene Cloud Manager-Produktprofile, z. B. Business Owner, Deployment Manager und Developer.
* Weisen Sie Cloud Manager-Produktprofilen wie Business Owner, Deployment Manager und Developer Team-Mitglieder zu.

## Voraussetzungen {#prerequisites}

Vor dem Start dieses Abschnitts sollten die folgenden Voraussetzungen berücksichtigt werden. Sie müssen ein :

* Einen Systemadministrator und verstehen [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).
* Versteht die Grundlagen zu [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en).
* Muss über Details zu Ihren Teammitgliedern verfügen. Ein Systemadministrator muss über die Namen und E-Mail-Adressen sowie die Rollen und Zuständigkeiten der Teammitglieder verfügen, die Zugriff auf AEM als Cloud Service benötigen.

   >[!NOTE]
   >Für das Onboarding empfehlen wir, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Rest des Onboarding fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie später eine größere Anzahl von Benutzern auswählen.

## Überprüfen von Cloud Manager-Produktprofilen {#review-product-profiles}

Von Admin Console aus können Sie die Liste der Cloud Manager-Profile sehen.

>[!NOTE]
>Bevor Sie die Cloud Manager-Produktprofile aus Admin Console überprüfen, sollten Sie die verfügbaren [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) überprüfen.

Gehen Sie wie folgt vor, um eine Liste der Cloud Manager-Profile anzuzeigen:

1. Melden Sie sich bei [Adobe Admin Console](https://adminconsole.adobe.com/) an. Wählen Sie auf der Seite **Übersicht** die Option **Adobe Experience Manager als Cloud Service** aus der Karte **Produkte und Dienste**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

   >[!NOTE]
   >Informationen zur Verwendung von Admin Console finden Sie unter Anmeldung bei Admin Console .


1. Navigieren Sie in der Tabelle mit der Liste aller Instanzen zur Instanz **Cloud Manager** .

   ![](/help/onboarding/onboarding-journey/assets/assign-team2.png)

1. Sie sehen die Liste der vorkonfigurierten [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles).

   ![](/help/onboarding/onboarding-journey/assets/assign-team3.png)


## Zuweisen von Benutzern zum Produktprofil &quot;Business Owner&quot; {#assign-users-business-owner}

Sie können jetzt Benutzer hinzufügen und sie dem Cloud Manager Business Owner-Produktprofil zuweisen.

>[!NOTE]
>Um dies erfolgreich zu erreichen, müssen Sie in der Adobe Admin Console einen Anwender zum Produkt (hier AEM als Cloud Service) und zum Produktprofil [Cloud Manager Business Owner](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) hinzufügen.

Die folgenden Schritte führen Sie durch diesen Schritt:

1. Identifizieren Sie die Benutzer, die Cloud Manager-Programme verwalten, und fügen Sie sie zum Produktprofil Business Owner hinzu. Der Systemadministrator muss die erste Person sein, die auf Cloud Manager zugreift und sich dort anmeldet. Sie müssen sich selbst (Systemadministrator) zuerst zum Produktprofil Business Owner hinzufügen.

1. Wählen Sie auf der Seite [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **Übersicht** die Option **Adobe Experience Manager als Cloud Service** aus der Karte **Produkte und Dienste** aus, wie unten dargestellt.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zu Ihrem Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten. Wählen Sie für den ID-Typ Adobe ID aus, wenn das Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. Wählen Sie in der Produktauswahl **Adobe Experience Manager als Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Business Owner** wie unten dargestellt zu.

   >[!NOTE]
   >Unter [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) finden Sie Informationen dazu, wie Sie sicherstellen, dass den richtigen Benutzern in der Admin Console die richtigen Rollen zugewiesen werden.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

   >[!NOTE]
   >Weisen Sie den Benutzer mindestens einem Produktprofil zu, damit der Benutzer auf Cloud Manager zugreifen kann. Denken Sie daran, sich selbst (Systemadministrator) dem Business Owner zuzuweisen.

1. Klicken Sie auf **Speichern**.  Der hinzugefügte Benutzer erhält eine Begrüßungs-E-Mail. Der eingeladene Benutzer kann auf Cloud Manager zugreifen, indem er auf den Link in der Begrüßungs-E-Mail klickt und sich mithilfe seiner Adobe ID anmeldet.

Herzlichen Glückwunsch! Jetzt wurde Ihr neu zusammengestelltes Cloud Manager-Team eingerichtet, das auch die Rolle &quot;Business Owner&quot;beinhaltet. Mitglieder erhalten eine Begrüßungs-E-Mail, in der sie zur Anmeldung und zum Zugriff auf Cloud Manager eingeladen werden. Als Business Owner müssen Sie sich jetzt nur noch einen Schritt von der Anmeldung bei Cloud Manager und der Erstellung Ihrer Cloud-Ressourcen entfernt haben.

## Zuweisen von Benutzern zum Deployment Manager-Produktprofil {#assign-users-deployment-manager}

1. Identifizieren Sie die Benutzer, die Cloud Manager-Programme verwalten sollen, und fügen Sie sie zum Deployment Manager-Produktprofil hinzu. Der Systemadministrator muss die erste Person sein, die auf Cloud Manager zugreift und sich dort anmeldet. Sie müssen sich selbst (Systemadministrator) zuerst zum Produktprofil Business Owner hinzufügen.

1. Wählen Sie auf der Seite [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **Übersicht** die Option **Adobe Experience Manager als Cloud Service** aus der Karte **Produkte und Dienste** aus, wie unten dargestellt.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zu Ihrem Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten. Wählen Sie für den ID-Typ Adobe ID aus, wenn das Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. Wählen Sie in der Produktauswahl **Adobe Experience Manager als Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Deployment Manager** wie unten gezeigt zu.

   >[!NOTE]
   >Unter [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) finden Sie Informationen dazu, wie Sie sicherstellen, dass den richtigen Benutzern in der Admin Console die richtigen Rollen zugewiesen werden.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png).

   >[!IMPORTANT]
   >Benutzer können zum Deployment Manager-Produktprofil hinzugefügt werden, nachdem Cloud Manager-Ressourcen erstellt wurden.

## Zuweisen von Benutzern zum Developer Product Profile {#assign-users-developer}

1. Identifizieren Sie die Benutzer, die Cloud Manager-Programme verwalten, und fügen Sie sie zum Entwicklerproduktprofil hinzu. Der Systemadministrator muss die erste Person sein, die auf Cloud Manager zugreift und sich dort anmeldet. Sie müssen sich selbst (Systemadministrator) zuerst zum Produktprofil Business Owner hinzufügen.

1. Wählen Sie auf der Seite [Admin Console](https://adminconsole.adobe.com/enterprise/overview) **Übersicht** die Option **Adobe Experience Manager als Cloud Service** aus der Karte **Produkte und Dienste** aus, wie unten dargestellt.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Wählen Sie in der oberen Navigation die Registerkarte **Benutzer** und dann **Benutzer hinzufügen** aus.

   ![](/help/onboarding/onboarding-journey/assets/assign-team4.png)

1. Geben Sie im Dialogfeld **Benutzer zu Ihrem Team hinzufügen** die E-Mail-ID des Benutzers ein, den Sie hinzufügen möchten. Wählen Sie für den ID-Typ Adobe ID aus, wenn das Federated ID für Ihre Teammitglieder noch nicht eingerichtet wurde.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png)

1. Wählen Sie in der Produktauswahl **Adobe Experience Manager als Cloud Service** aus und weisen Sie dem Benutzer das Produktprofil **Entwickler** wie unten gezeigt zu.

   >[!NOTE]
   >Unter [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) finden Sie Informationen dazu, wie Sie sicherstellen, dass den richtigen Benutzern in der Admin Console die richtigen Rollen zugewiesen werden.

   ![](/help/onboarding/onboarding-journey/assets/assign-team5.png).


   >[!IMPORTANT]
   >Benutzer können zum Entwicklerproduktprofil hinzugefügt werden, nachdem Cloud Manager-Ressourcen erstellt wurden.

## Nächste Schritte {#whats-next}

Als Systemadministrator, der die Rolle *Business Owner* zugewiesen ist, müssen Sie auf Cloud Manager zugreifen und sich dort anmelden.
>[!NOTE]
>Informationen zum Anmelden und Aufrufen von Cloud Manager finden Sie unter [Navigieren zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/navigate-to-cloud-manager.html?lang=en) .

Ein Cloud Manager-Benutzer mit der Rolle &quot;Business Owner&quot;kann sich anmelden und Ihre Cloud-Ressourcen einschließlich Ihrer Programme und Umgebungen einrichten. Dadurch wird sichergestellt, dass Ihr Expertenteam so bald wie möglich mit dem AEM als Cloud Service beginnen kann.
Nachdem Ihr Business Owner Ihre Cloud-Ressourcen eingerichtet hat, können Entwickler und Bereitstellungsmanager, die den Cloud Manager-Produktprofilen erfolgreich hinzugefügt wurden, auf Cloud Manager zugreifen und sich damit vertraut machen, wie sie ihren Lernpfad fortsetzen können.

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html?lang=en)
* [Cloud Manager-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles)
* [Admin Console Identity - Übersicht](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/identity.ug.html)
