---
title: 'Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service-Produktprofilen '
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder AEM as a Cloud Service-Produktprofilen zuweisen.
hide: true
index: false
source-git-commit: 4a6408c498b093fc8b3baf4bdf1798b4281c90c2
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 2%

---


# Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service-Produktprofilen {#assign-team-members-cloud-service}

## Ziele {#objective}

Dieses Dokument hilft Ihnen dabei, die Schritte zu verstehen, die Ihr Systemadministrator unternehmen muss, um Ihre Teammitglieder Produktprofilen als Cloud Service AEM zu lassen, und warum es wichtig ist, Ihren AEM-Autoren zu ermöglichen, mit AEM auf ihre Journey zuzugreifen.

Nach Lesen dieses Abschnitts sollten Sie Folgendes verstehen:

* Warum und wie Ihre Teammitglieder AEM als Cloud Service-Produktprofile zugewiesen werden.
* Hinzufügen von Teammitgliedern zu AEM Benutzerproduktprofil.
* Hinzufügen von Teammitgliedern zum Produktprofil AEM Administratoren .


## Einführung {#introduction}

Um Zugriff auf AEM als Cloud Service zu erhalten, müssen Benutzer einem von zwei Produktprofilen angehören:  `AEM Users` oder `AEM Administrators`. Ihren Teammitgliedern müssen Berechtigungen für die AEM-Instanz gewährt werden, da die Berechtigungen zum Verwalten von Cloud Manager nicht ausreichen.

>[!NOTE]
>Jeder Benutzer, der AEM Benutzerproduktprofil vom Systemadministrator zugewiesen wurde, hat (schreibgeschützten) Zugriff auf Cloud Manager.

## Voraussetzungen {#prerequisites}

Bevor Sie mit dem Lesen dieses Abschnitts beginnen, sollten Sie die folgenden Voraussetzungen beachten:

* Verstehen Sie [AEM als Cloud Service Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles)
* Machen Sie sich mit [Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en) vertraut.
* Ihren Team-Mitgliedern wurden entsprechend Cloud Manager-Produktprofile zugewiesen und Cloud-Ressourcen wurden eingerichtet.
* Details zu Ihrem Teammitglied: Der Systemadministrator muss über die Namen und E-Mail-Adressen sowie die Rollen und Zuständigkeiten der Teammitglieder verfügen, die Zugriff auf AEM als Cloud Service benötigen.

   >[!NOTE]
   >Für das Onboarding empfehlen wir, zunächst Benutzer hinzuzufügen, die an den unmittelbaren Aufgaben teilnehmen, z. B. Administratoren, Entwickler und Inhaltsautoren. Sie können den Rest des Onboarding fortsetzen, ohne alle Benutzer hinzuzufügen. Nachdem Sie das Onboarding abgeschlossen haben, können Sie später eine größere Anzahl von Benutzern auswählen.


   >[!IMPORTANT]
   >Bevor Sie mit der Überprüfung der Schritte für die Zuweisung von Teammitgliedern zu AEM as a Cloud Service-Produktprofilen beginnen, stellen Sie sicher, dass Sie die folgenden beiden Schritte ausführen:
   >
   >1. Melden Sie sich bei [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en) an. Weitere Informationen finden Sie unter Anmelden bei Admin Console .
      >
      >
   1. Überprüfen Sie [AEM als Cloud Service Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).


Gehen Sie wie folgt vor, um die Liste der Cloud Manager-Profile aus Adobe Admin Console anzuzeigen:

1. Melden Sie sich bei [Adobe Admin Console](https://adminconsole.adobe.com/) an. Wählen Sie auf der Seite **Übersicht** die Option **Adobe Experience Manager als Cloud Service** aus der Karte **Produkte und Dienste**.

   ![](/help/onboarding/onboarding-journey/assets/assign-team1.png)

1. Navigieren Sie zur Instanz (Autoreninstanz der Entwicklungsumgebung) und wählen Sie sie aus, wie im folgenden Bild dargestellt.

   ![](/help/onboarding/onboarding-journey/assets/cloud-profiles-1.png)


1. Sie sehen die Liste der AEM als Cloud Service-Produktprofile, die einem Benutzer basierend auf seiner Rolle zugewiesen werden müssen.

   >[!NOTE]
   >Weitere Informationen dazu finden Sie unter [AEM als Cloud Service Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

   ![](/help/onboarding/onboarding-journey/assets/cloud-profiles-2.png)


## Hinzufügen von Teammitgliedern zu AEM Benutzer- oder AEM Administrator-Produktprofil {#add-team-members}

Um Zugriff auf AEM als Cloud Service-Instanz zu erhalten, müssen Benutzer einem von zwei Produktprofilen `AEM Users` oder `AEM Administrators` angehören.

>[!NOTE]
>Sie müssen über Berechtigungen für die Instanz verfügen. Berechtigungen zur Verwaltung von Cloud Manager reichen nicht aus. Weitere Informationen

Die folgenden Schritte müssen von einem Systemadministrator ausgeführt werden, der auch der Rolle &quot;Business Owner&quot;angehört.

1. Navigieren Sie in Cloud Manager zu Ihrem Programm und wählen Sie die Schaltfläche **Zugriff verwalten** aus dem Kontext der gewünschten Umgebung aus, wie unten dargestellt.

   ![](/help/onboarding/onboarding-journey/assets/add-team1.png)

1. Über eine neue Registerkarte gelangen Sie zu Adobe Admin Console, von wo aus Sie Zugriff auf die Autoreninstanz der Umgebung haben. Wählen Sie **AEM Administratoren** oder **AEM Benutzer** basierend auf den Berechtigungen, die diese Person erhalten muss. Erfahren Sie mehr über [AEM als Cloud Service-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

   ![](/help/onboarding/onboarding-journey/assets/add-team2.png)

1. Wählen Sie `AEM Administrator` oder `AEM User` aus und klicken Sie auf **Benutzer hinzufügen** wie unten dargestellt. Senden Sie die erforderlichen Details, um das Hinzufügen des Teammitglieds abzuschließen.

   ![](/help/onboarding/onboarding-journey/assets/add-team3.png)

   Der Benutzer, den Sie hinzugefügt haben, hat jetzt Zugriff auf die AEM als Cloud Service-Autorendienste!

   >[!NOTE]
   >Sie sollten diese Schritte für alle Umgebungen wiederholen, einschließlich Entwicklung, Staging und Produktion, wenn Sie über die Informationen der Teammitglieder verfügen, die Zugriff benötigen.


## Nächste Schritte {#whats-next}

Die Benutzer, die Sie AEM als Cloud Service-Produktprofilen zugewiesen haben, können jetzt lernen, wie Sie auf die -Autoreninstanz zugreifen und sich mit Authoring-Seiten in AEM as a Cloud Service vertraut machen. Sie sollten dem Pfad folgen, indem Sie sich das Dokument Lernpfad für [AEM Benutzer](/help/onboarding/onboarding-journey/learning-path-aem-users.md) oder für [Entwickler und Bereitstellungsmanager](/help/onboarding/onboarding-journey/learning-path-developers-deploymentmanagers.md) ansehen.

## Zusätzliche Ressourcen {#additional-resources}

* [Verwalten von Produkten und Benutzerzugriff in der Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#managing-products-and-user-access-in-admin-console)
* [Zugriff auf AEM konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en)
* [Schnellstartanleitung zum Verfassen von Seiten (Authoring)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=en)