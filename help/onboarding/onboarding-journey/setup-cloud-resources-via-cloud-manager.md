---
title: Einrichten von Cloud-Ressourcen über Cloud Manager
description: Auf dieser Seite erfahren Sie, wie Sie Cloud-Ressourcen über Cloud Manager einrichten
hide: true
hidefromtoc: true
index: false
source-git-commit: 9caf3447fedf13fa81bb616cc54b7cb6a08ff159
workflow-type: tm+mt
source-wordcount: '1023'
ht-degree: 2%

---

# Einrichten von Cloud-Ressourcen über Cloud Manager {#setup-cloud-resources}

Der Systemadministrator, der der Rolle *Business Owner* zugewiesen ist, sollte auf Cloud Manager zugreifen und sich dort anmelden. Danach muss sich ein Team-Mitglied, das dem Produktprofil *Business Owner* zugewiesen ist, bei Cloud Manager anmelden und Ihr Cloud-Programm und Ihre Umgebungen erstellen, damit Ihr Expertenteam beginnen kann.

## Zielsetzung {#objective}

In diesem Dokument erfahren Sie, wie Ihre Cloud-Ressourcen erstellt werden und wer sie verwenden kann.

Nach Lesen dieses Abschnitts sollten Sie Folgendes verstehen:

* Ein Systemadministrator, der der Rolle *Business Owner* zugewiesen ist, muss als erster auf Cloud Manager zugreifen und sich dort anmelden.
* Erstellung des Cloud-Programms und der Umgebungen.

## Einführung {#introduction}

Das Hinzufügen Ihrer Cloud-Ressourcen erfolgt über Cloud Manager durch Ihr Team-Mitglied, das dem Cloud Manager Business Owner-Produktprofil zugewiesen ist. Diese Person ist in der Regel eine Person, die die Geschäftsanforderungen versteht und die Ersteinrichtung von Cloud Manager abschließt.

In den folgenden Abschnitten erfahren Sie, wie Sie Ihre [Cloud Service-Programme](#create-cloud-service-program) und [Umgebungen](#create-cloud-environments) erstellen.

### Voraussetzungen {#prerequisites}

* Der Systemadministrator, der der Rolle *Business Owner* zugewiesen ist, sollte auf Cloud Manager zugreifen und sich dort anmelden.

* Hier erfahren Sie, wie Sie [zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/navigate-to-cloud-manager.html?lang=en) navigieren und sich dort anmelden.

* Machen Sie sich mit [Cloud Manager-Produktprofilen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) vertraut.

* Machen Sie sich mit den Überlegungen zur Programmerstellung vertraut. Sehen Sie sich dieses Video an, um mehr zu erfahren.

* Grundlegendes zu den Konzepten von Cloud Manager [Programmen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html?lang=en) und [Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de)

## Zu Cloud Manager navigieren {#navigate-cloud-manager}

1. Der Benutzer *Business Owner* erhält eine Begrüßungs-E-Mail, von der aus er starten kann. Wenn er sie nicht finden kann, gehen Sie direkt zu [Adobe Experience Cloud](https://experience.adobe.com/#/@ccs/home) und melden Sie sich mit Ihrer Adobe ID an.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources1.png)

1. Wählen Sie auf der Adobe Experience Cloud-Startseite **Experience Manager** aus.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources2.png)

1. Dadurch gelangen Sie zur AEM Homepage. Starten Sie von hier aus **Cloud Manager** .

   ![](/help/onboarding/onboarding-journey/assets/setup-resources3.png)

1. Die Landingpage von Cloud Manager wird angezeigt, wie in der folgenden Abbildung dargestellt.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources4.png)

1. Vergewissern Sie sich, dass Ihnen das Produktprofil &quot;Business Owner&quot;zugewiesen wurde. Wählen Sie dazu Ihr Profil oben rechts aus, wie unten dargestellt.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources5.png)

1. Wählen Sie **Benutzerrollen** aus und stellen Sie sicher, dass Sie dem Business Owner zugewiesen sind.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources6.png)

1. Dadurch wird Ihre Benutzerrolle als Business Owner bestätigt.

   ![](/help/onboarding/onboarding-journey/assets/setup-resources7.png)

   Gute Arbeit! Sie haben sich erfolgreich als Business Owner bei Cloud Manager angemeldet!

## Cloud Service erstellen {#create-cloud-service-program}

Gehen Sie wie folgt vor, um Ihr Cloud Service-Programm aus Cloud Manager zu erstellen:

1. Navigieren Sie zur Landingpage von Cloud Manager , wie unten dargestellt.

   >[!NOTE]
   >Sie müssen ein Team-Mitglied sein, das dem Cloud Manager Business Owner-Produktprofil zugewiesen ist, um diesen Schritt erfolgreich abzuschließen.

1. Wählen Sie hier Programm hinzufügen aus, um den Assistenten Programm hinzufügen zu starten. Sehen Sie sich das Video an, um zu erfahren, wie Sie Ihr AEMaaCS-Programm erstellen, und wichtige Überlegungen vor der Erstellung Ihres Programms an.

1. Eine schrittweise Anleitung zur Verwendung des Assistenten Programm hinzufügen finden Sie hier.

   >[!CAUTION]
   >Beachten Sie, dass der Programmname nach der Erstellung nicht mehr geändert werden kann. Wir empfehlen Ihnen, sich bezüglich des Namens, den Sie Ihrem Programm geben möchten, sicher zu sein.

   Falls Sie den Programmnamen ändern müssen, müssen Sie sich an den Support der Adobe wenden oder sich alternativ an Ihren Kundenbetreuer der Adobe wenden. Sie werden dazu beitragen, das Programm effektiv zu löschen. Sie müssen von Anfang an mit einem potenziellen Verlust an Arbeit beginnen, den Ihr Team geleistet hat.

1. Nach erfolgreicher Erstellung Ihres Cloud-Programms können Sie zu Ihrem Programm navigieren, um die Übersichtsseite Ihres Programms wie unten dargestellt anzuzeigen:

1. Wenn Sie dies noch nicht getan haben, ist es jetzt an der Zeit, Ihre Entwickler-Mitglieder Ihrem Cloud Manager-Team hinzuzufügen, navigieren Sie zu Benutzer zum Entwicklerproduktprofil hinzufügen und führen Sie die beschriebenen Schritte aus.

1. Mitglieder, die dem Produktprofil &quot;Entwickler&quot;zugewiesen sind, können sich bei Cloud Manager anmelden und Cloud Manager Git verwalten.


   Gute Arbeit! Nachdem Ihr Programm erfolgreich erstellt wurde, können Ihre Entwickler auf Ihr Cloud Manager-Git zugreifen!


## Erstellen von Cloud-Umgebungen {#create-cloud-environments}

Gehen Sie wie folgt vor, um Ihre Cloud-Umgebungen aus Cloud Manager zu erstellen:

1. Nachdem Sie Ihr Cloud-Programm erfolgreich erstellt haben, erstellen Sie Ihre Cloud-Umgebungen, indem Sie zur Cloud Manager-Übersichtsseite navigieren und auf der Umgebungskarte Hinzufügen auswählen.

   >[!IMPORTANT]
   >Ein Cloud Manager-Benutzer mit der Rolle Business Owner oder Deployment Manager muss angemeldet sein, um diesen Schritt erfolgreich durchführen zu können.

   Sehen Sie sich außerdem das Schnellvideo-Tutorial an, um mehr über Cloud Manager-Umgebungen und darüber zu erfahren, wie Sie sie Ihrem Programm hinzufügen können.

1. Dadurch wird der Assistent zum Hinzufügen der Umgebung gestartet, der Sie beim Hinzufügen Ihrer Umgebung unterstützt. Fügen Sie zuerst Ihre Entwicklungsumgebung hinzu, um sich kennenzulernen.

1. Wenn Sie dies noch nicht getan haben, können Sie jetzt Ihre Entwickler-Mitglieder zu Ihrem Cloud Manager-Team hinzufügen, zu Benutzer zum Entwicklerproduktprofil hinzufügen navigieren und die beschriebenen Schritte ausführen. Auf diese Weise können Ihre Entwickler mit dem Navigieren zu Cloud Manager und Verwalten von Cloud Manager Git beginnen.


   Herzlichen Glückwunsch! Jetzt wurden Ihre Cloud-Programmumgebungen erstellt und Ihre Entwickler wurden zum Team hinzugefügt!

## Nächste Schritte {#whats-next}

Ihren Teammitgliedern müssen Berechtigungen für die Instanz erteilt werden, da die Berechtigungen zum Verwalten von Cloud Manager nicht ausreichen. Nachdem Ihre Cloud-Ressourcen erstellt wurden und für Ihr Team verfügbar sind, muss der Systemadministrator Ihre Team-Mitglieder AEM als Cloud Service-Produktprofile aus Admin Console zuweisen.

Sie sollten Ihre Onboarding-Journey fortsetzen, indem Sie sich das Dokument Zuweisen von Team-Mitgliedern zu AEM als Cloud Service Produktprofile ansehen.

>[!NOTE]
>Um Zugriff auf AEM als Cloud Service zu erhalten, müssen Benutzer einem von zwei Produktprofilen &quot;AEM Benutzer&quot;oder &quot;AEM Administratoren&quot;angehören. Weitere Informationen

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Programmtypen und Hinzufügen eines Programms](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en)
* [Umgebungstypen und Hinzufügen einer Umgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en)
* [Verwalten von Cloud Manager Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en)
* [Zugriff auf AEM als Cloud Service von Admin Console konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=en#adobe-ims-users)
