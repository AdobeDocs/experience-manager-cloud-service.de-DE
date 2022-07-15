---
title: Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service-Produktprofilen
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder AEM as a Cloud Service-Produktprofilen zuweisen.
feature: Onboarding
role: Admin, User, Developer
exl-id: c00f5d28-85af-4bd3-a50c-913d1342241c
source-git-commit: 96a0dacf69f6f9c5744f224d1a48b2afa11fb09e
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 100%

---

# Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service-Produktprofilen {#assign-team-members-cloud-service}

## Ziel {#objective}

Dieses Dokument hilft Ihnen dabei, die Schritte zu verstehen, die Ihr Systemadministrator unternehmen muss, um Ihre Team-Mitglieder AEM as a Cloud Service-Produktprofilen zuzuweisen, und warum es entscheidend dafür ist, dass Ihre AEM-Autoren ihren Weg mit AEM beginnen können.

Nach Lesen dieses Abschnitts sollten Sie Folgendes verstehen:

* Warum und wie Ihre Team-Mitglieder AEM as a Cloud Service-Produktprofilen zugewiesen werden.
* Wie man Team-Mitglieder zu AEM-Benutzer-Produktprofilen hinzufügt.
* Wie man Team-Mitglieder zu AEM-Administrator-Produktprofilen hinzufügt.


## Einführung {#introduction}

Um Zugriff auf AEM as a Cloud Service zu erhalten, müssen Benutzer einem von zwei Produktprofilen angehören: `AEM Users` oder `AEM Administrators`. Ihren Team-Mitgliedern müssen Berechtigungen für die AEM-Instanz gewährt werden, da die Berechtigungen zum Verwalten von Cloud Manager nicht ausreichen.

>[!NOTE]
>Jeder Benutzer, der vom Systemadministrator zum AEM-Benutzer-Produktprofil zugewiesen wurde, hat (schreibgeschützten) Zugriff auf Cloud Manager.

## Voraussetzungen {#prerequisites}

Bevor Sie mit dem Lesen dieses Abschnitts beginnen, sollten Sie die folgenden Voraussetzungen beachten:

* Grundlegendes Verständnis von [AEM as a Cloud Service-Produktprofilen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=de#aem-product-profiles)
* Vertrautheit mit [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=de)
* Ihren Team-Mitgliedern wurden entsprechende Cloud Manager-Produktprofile zugewiesen und Cloud-Ressourcen wurden eingerichtet.
* Details zu Ihrem Team-Mitglied: Der Systemadministrator muss über die Namen und E-Mail-Adressen sowie die Rollen und Zuständigkeiten der Team-Mitglieder verfügen, die Zugriff auf AEM as a Cloud Service benötigen.

   >[!NOTE]
   >Für das Onboarding empfehlen wir, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Rest des Onboarding fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie später die Anzahl von Benutzern ausweiten.


   >[!IMPORTANT]
   >Bevor Sie mit der Überprüfung der Schritte für die Zuweisung von Team-Mitgliedern zu AEM as a Cloud Service-Produktprofilen beginnen, stellen Sie sicher, dass Sie die folgenden beiden Schritte ausführen:
   >
   >1. Melden Sie sich bei der [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en) an. Weitere Informationen finden Sie unter „Anmelden bei Admin Console“.
   >
   >1. Lesen Sie [AEM as a Cloud Service-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).


Gehen Sie wie folgt vor, um von Adobe Admin Console aus die Liste der Cloud Manager-Profile anzuzeigen:

1. Melden Sie sich bei der [Adobe Admin Console](https://adminconsole.adobe.com/) an. Wählen Sie auf der Seite **Überblick** die Option **Adobe Experience Manager as a Cloud Service** aus der Karte **Produkte und Services**.

   ![](/help/journey-onboarding/assets/assign-team1.png)

1. Gehen Sie zur Instanz (Autoreninstanz der Entwicklungsumgebung) und wählen Sie sie aus, wie im folgenden Bild dargestellt.

   ![](/help/journey-onboarding/assets/cloud-profiles-1.png)


1. Sie sehen die Liste der AEM as a Cloud Service-Produktprofile, die einem Benutzer basierend auf seiner Rolle zugewiesen werden müssen.

   >[!NOTE]
   >Weitere Informationen dazu finden Sie unter [AEM as a Cloud Service-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

   ![](/help/journey-onboarding/assets/cloud-profiles-2.png)


## Hinzufügen von Team-Mitgliedern zum AEM-Benutzer- oder AEM-Administrator-Produktprofil {#add-team-members}

Um Zugriff auf die AEM as a Cloud Service-Instanz zu erhalten, müssen Benutzer einem von zwei Produktprofilen, `AEM Users` oder `AEM Administrators`, angehören.

>[!NOTE]
>Sie müssen über Berechtigungen für die Instanz verfügen. Berechtigungen zur Verwaltung von Cloud Manager reichen nicht aus. Weitere Informationen

Die folgenden Schritte müssen von einem Systemadministrator ausgeführt werden, der auch der Rolle „Geschäftsverantwortlicher“ angehört.

1. Gehen Sie in Cloud Manager zu Ihrem Programm und wählen Sie die Schaltfläche **Zugriff verwalten** aus dem Kontext der gewünschten Umgebung aus, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/add-team1.png)

1. Über eine neue Registerkarte gelangen Sie zu Adobe Admin Console, von wo aus Sie Zugriff auf die Autoreninstanz der Umgebung haben. Wählen Sie **AEM-Administratoren** oder **AEM-Benutzer** aus, basierend auf den Berechtigungen, die diese Person erhalten muss. Erfahren Sie mehr über [AEM as a Cloud Service-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

   ![](/help/journey-onboarding/assets/add-team2.png)

1. Wählen Sie `AEM Administrator` oder `AEM User` aus und klicken Sie auf **Benutzer hinzufügen**, wie unten dargestellt. Übermitteln Sie die erforderlichen Details, um das Hinzufügen des Team-Mitglieds abzuschließen.

   ![](/help/journey-onboarding/assets/add-team3.png)

   Der Benutzer, den Sie hinzugefügt haben, hat jetzt Zugriff auf die AEM as a Cloud Service-Autoren-Services!

   >[!NOTE]
   >Sie sollten diese Schritte für alle Umgebungen wiederholen, einschließlich Entwicklung, Staging und Produktion, wenn Sie über Informationen zu den Team-Mitgliedern verfügen, die Zugriff benötigen.


## Wie geht es weiter? {#whats-next}

Die Benutzer, die Sie AEM as a Cloud Service-Produktprofilen zugewiesen haben, können jetzt lernen, wie Sie auf die Autoreninstanz zugreifen und können sich mit Authoring-Seiten in AEM as a Cloud Service vertraut machen. Sie sollten diesen Weg weiter gehen, indem Sie sich das Dokument „Lernpfad für [AEM-Anwender](/help/journey-onboarding/sysadmin/learning-path-aem-users.md)“ oder „Lernpfad für [Entwickler und Implementierungs-Manager](/help/journey-onboarding/sysadmin/learning-path-developers-deploymentmanagers.md)“ ansehen.

## Zusätzliche Ressourcen {#additional-resources}

* [Verwalten von Produkten und Benutzerzugriff in der Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=de#managing-products-and-user-access-in-admin-console)
* [Konfigurieren des Zugriffs auf AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=de)
* [Schnellstartanleitung zum Verfassen von Seiten (Authoring)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=de)
