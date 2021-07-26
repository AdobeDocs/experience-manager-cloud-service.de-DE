---
title: 'Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service-Produktprofilen '
description: Auf dieser Seite erfahren Sie, wie Sie Team-Mitglieder AEM as a Cloud Service-Produktprofilen zuweisen.
hide: true
hidefromtoc: true
index: false
source-git-commit: c2301227eb65bedb77acd9754e2bc4b62527863d
workflow-type: tm+mt
source-wordcount: '779'
ht-degree: 1%

---


# Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service-Produktprofilen {#assign-team-members-cloud-service}

## Zielsetzung {#objective}

Dieses Dokument hilft Ihnen dabei, die Schritte zu verstehen, die Ihr Systemadministrator unternehmen muss, um Ihre Teammitglieder Produktprofilen als Cloud Service AEM zu lassen, und warum es wichtig ist, Ihren AEM-Autoren zu ermöglichen, mit AEM auf ihre Journey zuzugreifen.

Nach Lesen dieses Abschnitts sollten Sie Folgendes verstehen:

* Warum und wie Ihre Teammitglieder AEM als Cloud Service-Produktprofile zugewiesen werden.
* Hinzufügen von Teammitgliedern zu AEM Benutzerproduktprofil.
* Hinzufügen von Teammitgliedern zum Produktprofil AEM Administratoren .


## Einführung {#introduction}

Um Zugriff auf AEM als Cloud Service zu erhalten, müssen Benutzer zu einem von zwei Produktprofilen gehören, z. B. `AEM Users` oder `AEM Administrators`. Ihren Teammitgliedern müssen Berechtigungen für die AEM-Instanz gewährt werden, da die Berechtigungen zum Verwalten von Cloud Manager nicht ausreichen. Weitere Informationen

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


1. Melden Sie sich bei [Adobe Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/admin-console.html?lang=en) an. Weitere Informationen finden Sie unter Anmelden bei Admin Console .

1. Überprüfen Sie [AEM als Cloud Service Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

Gehen Sie wie folgt vor, um die Liste der Cloud Manager-Profile aus Adobe Admin Console anzuzeigen:

1. Nachdem Sie sich bei Adobe Admin Console angemeldet haben, wählen Sie Adobe Experience Manager as a Cloud Service auf der Karte Produkte und Dienste aus:

1. Navigieren Sie zur Instanz (Autoreninstanz der Entwicklungsumgebung) und wählen Sie sie aus, wie im folgenden Bild dargestellt.

   Jetzt können Sie die Liste der AEM als Cloud Service-Produktprofile sehen, die einem Benutzer basierend auf seiner Rolle zugewiesen werden müssen. Weitere Informationen dazu finden Sie unter AEM as a Cloud Service - Produktprofile .


## Hinzufügen von Teammitgliedern zu AEM Benutzer- oder AEM Administrator-Produktprofil {#add-team-members}

Um Zugriff auf AEM als Cloud Service-Instanz zu erhalten, müssen Benutzer einem von zwei Produktprofilen `AEM Users` oder `AEM Administrators` angehören.

>[!NOTE]
>Sie müssen über Berechtigungen für die Instanz verfügen. Berechtigungen zur Verwaltung von Cloud Manager reichen nicht aus. Weitere Informationen

Die folgenden Schritte müssen von einem Systemadministrator ausgeführt werden, der auch in der Rolle &quot;Business Owner&quot;tätig ist.

1. Navigieren Sie in Cloud Manager zu Cloud Manager und wählen Sie im Kontext der interessanten Umgebung die Schaltfläche Zugriff verwalten aus, wie unten dargestellt:

1. Nachdem Sie auf Zugriff verwalten geklickt haben, navigiert eine neue REGISTERKARTE zu der Admin Console, von der aus Sie Zugriff auf die Autoreninstanz der Umgebung haben. Wählen Sie *AEM Administratoren* oder *AEM Benutzer* basierend auf den Berechtigungen, die diese Person erhalten muss. Erfahren Sie mehr über [AEM als Cloud Service-Produktprofile](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#aem-product-profiles).

1. Wählen Sie Benutzer hinzufügen wie unten gezeigt aus und reichen Sie die erforderlichen Details ein, um das Hinzufügen des Teammitglieds abzuschließen:


1. Sie sollten diese Schritte für alle Umgebungen wiederholen, einschließlich Entwicklung, Staging und Produktion, wenn Sie über die Informationen der Teammitglieder verfügen, die Zugriff benötigen.

   Der Benutzer, den Sie hinzugefügt haben, hat jetzt Zugriff auf die AEM als Cloud Service-Autorendienste!


## Nächste Schritte {#whats-next}

Die Benutzer, die Sie AEM als Cloud Service-Produktprofilen zugewiesen haben, können jetzt lernen, wie Sie auf die -Autoreninstanz zugreifen und sich mit Authoring-Seiten in AEM as a Cloud Service vertraut machen. Sie sollten dem Pfad folgen, indem Sie sich das Dokument Lernpfad für AEM Benutzer ansehen.

## Zusätzliche Ressourcen {#additional-resources}

* [Zugriff auf AEM konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/walk-through.html?lang=en)
* [Schnellstartanleitung zum Verfassen von Seiten (Authoring)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/authoring/getting-started/quick-start.html?lang=en)
