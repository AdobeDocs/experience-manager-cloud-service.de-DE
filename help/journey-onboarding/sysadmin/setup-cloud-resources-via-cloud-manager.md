---
title: Einrichten von Cloud-Ressourcen über Cloud Manager
description: Auf dieser Seite erfahren Sie, wie Sie über Cloud Manager Cloud-Ressourcen einrichten
role: Admin, User, Developer
exl-id: de3a33b7-b459-4e47-b232-a0f88e2ce22e
source-git-commit: 7fe39bbc8d5e965af7f339b2a524420c76360552
workflow-type: tm+mt
source-wordcount: '1246'
ht-degree: 92%

---

# Einrichten von Cloud-Ressourcen über Cloud Manager {#setup-cloud-resources}

Der Systemadministrator, der der Rolle „Geschäftsverantwortlicher“ zugewiesen ist, sollte auf Cloud Manager zugreifen und sich dort anmelden. Danach muss sich ein Team-Mitglied, das dem Produktprofil „Geschäftsverantwortlicher“ zugewiesen ist, bei Cloud Manager anmelden und Ihr Cloud-Programm und Ihre Umgebungen erstellen, damit Ihr Experten-Team beginnen kann.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Ihre Cloud-Ressourcen erstellt werden und wer sie verwenden kann.

Nach Lesen dieses Abschnitts sollten Sie Folgendes verstehen:

* Ein Systemadministrator, der der Rolle „Geschäftsverantwortlicher“ zugewiesen ist, muss als erster auf Cloud Manager zugreifen und sich dort anmelden.
* Wie Ihr Cloud-Programm und Umgebungen erstellt werden.

## Einführung {#introduction}

Das Hinzufügen Ihrer Cloud-Ressourcen erfolgt über Cloud Manager durch Ihr Team-Mitglied, das dem Cloud Manager-Produktprofil „Geschäftsverantwortlicher“ zugewiesen ist. Diese Person ist in der Regel eine Person, die die Geschäftsanforderungen versteht und die Ersteinrichtung von Cloud Manager abschließt.

In den folgenden Abschnitten erfahren Sie, wie Sie Ihre [Cloud-Service-Programme](#create-cloud-service-program) und [Umgebungen.](#create-cloud-environments)

### Voraussetzungen {#prerequisites}

* Der Systemadministrator, der der Rolle „Geschäftsverantwortlicher“ zugewiesen ist, sollte auf Cloud Manager zugreifen und sich dort anmelden.

* Erfahren Sie, wie Sie [zu Cloud Manager gelangen und sich dort anmelden.](/help/onboarding/learn-concepts/cloud-manager-introduction.md)

* Machen Sie sich mit [Cloud Manager-Produktprofile.](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md#cloud-manager-product-profiles)

* Verstehen Sie die Konzepte von Cloud Manager-[Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/understand-program-types.md) und [Umgebungen.](/help/implementing/cloud-manager/manage-environments.md)

## Navigieren zu Cloud Manager {#navigate-cloud-manager}

Ein Benutzer mit der Rolle „Geschäftsverantwortlicher“ erhält eine Begrüßungs-E-Mail mit einem Link zu den ersten Schritten. Wenn er sie nicht finden kann, greift er auf [Cloud Manager](https://my.cloudmanager.adobe.com/) direkt durch Anmeldung mit seiner Adobe ID zu.

Führen Sie die nachfolgenden Schritte aus, um zu Cloud Manager zu gelangen:

1. Klicken Sie in Ihrer Willkommens-E-Mail auf **Erste Schritte**, wie in der folgenden Abbildung dargestellt.
   ![](/help/journey-onboarding/assets/get-started-email.png)

1. Gehen Sie zur Seite **Programme und Produkte** von Cloud Manager.

   >[!IMPORTANT]
   >
   >Alternativ können Sie auch direkt von [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) zur Anmeldeseite von Cloud Manager navigieren. Setzen Sie ein Lesezeichen für diese Seite, damit Sie in Zukunft direkt zur Startseite von Cloud Manager gehen können.

1. Sie werden zur Landingpage von Cloud Manager weitergeleitet. Weitere Informationen finden Sie im Abschnitt [Anzeigen der Cloud Manager-Programme](#viewing-programs).

Darüber hinaus können Sie von der Adobe Experience Cloud-Startseite aus zur Seite **Programme und Produkte** von Cloud Manager gehen. Führen Sie dazu folgende Schritte durch:

1. Gehen Sie direkt zu [Adobe Experience Cloud](https://experience.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie auf der Adobe Experience Cloud-Startseite **Experience Manager** aus.

   ![](/help/journey-onboarding/assets/setup-resources2.png)

1. Dadurch gelangen Sie zur AEM-Startseite. Starten Sie von hier aus **Cloud Manager**.

   ![](/help/journey-onboarding/assets/setup-resources3.png)

1. Nach erfolgreicher Anmeldung werden Sie zur Landingpage von Cloud Manager weitergeleitet. Weitere Informationen finden Sie im Abschnitt [Anzeigen der Cloud Manager-Programme](#viewing-programs).

   >[!NOTE]
   >
   >Je nach den in [!UICONTROL Cloud Manager] zugewiesenen Rollen und dem Programmstatus werden bei der Verwendung der [!UICONTROL Cloud Manager]-Benutzeroberfläche unterschiedliche Bildschirme angezeigt.

### Anzeigen von Programmen auf der Landingpage von Cloud Manager {#viewing-programs}

Nach erfolgreicher Anmeldung werden Sie zur Landingpage von Cloud Manager weitergeleitet. Es wird eine der drei Optionen angezeigt, wie nachfolgend beschrieben:

#### Wenn es keine Programme in Cloud Manager gibt {#no-programs}

Wenn in Ihrer Organisation keine Programme vorhanden sind, werden Sie auf der Landingpage aufgefordert, Ihr erstes Programm zu erstellen, wie in der folgenden Abbildung dargestellt.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### Wenn es in Cloud Manager bereits Programme gibt {#programs-exist}

Wenn in Ihrer Organisation bereits Programme vorhanden sind, werden Sie auf der Landingpage aufgefordert, ein weiteres Programm hinzuzufügen, und es werden alle vorhandenen Programme angezeigt, wie in der Abbildung unten dargestellt.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### Wenn es ein Programm gibt und der Anwender Systemadministrator ist {#programs-exist-sysadmin}

Wenn in Ihrer Organisation bereits Programme vorhanden sind und Sie Systemadministrator sind, wird auf der Landingpage die Schaltfläche **Zugriff verwalten** zusammen mit der Option **Programm hinzufügen** angezeigt, wie in der folgenden Abbildung dargestellt.

![](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## Überprüfen der Benutzerrollen {#verify-user-roles}

Nachdem Sie sich erfolgreich bei Cloud Manager angemeldet haben, führen Sie die folgenden Schritte aus, um sicherzustellen, dass Ihnen das Produktprofil „Geschäftsverantwortlicher“ zugewiesen wurde:

1. Wählen Sie oben rechts Ihr Profil aus, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/setup-resources5.png)

1. Wählen Sie **Benutzerrollen** aus und stellen Sie sicher, dass Sie der Rolle „Geschäftsverantwortlicher“ zugewiesen sind.

   ![](/help/journey-onboarding/assets/setup-resources6.png)

1. Dadurch wird Ihre Benutzerrolle als Geschäftsverantwortlicher bestätigt.

   ![](/help/journey-onboarding/assets/setup-resources7.png)

   Gute Arbeit! Sie haben sich erfolgreich als Geschäftsverantwortlicher bei Cloud Manager angemeldet!

## Cloud Service-Programm erstellen {#create-cloud-service-program}

Gehen Sie wie folgt vor, um Ihr Cloud Service-Programm aus Cloud Manager heraus zu erstellen:

1. Gehen Sie zur Landingpage von Cloud Manager, wie unten dargestellt.

   >[!NOTE]
   >
   >Sie müssen ein Team-Mitglied sein, das dem Cloud Manager-Produktprofil „Geschäftsverantwortlicher“ zugewiesen ist, um diesen Schritt erfolgreich abzuschließen.

   Klicken Sie hier auf **Programm hinzufügen**, um den Assistenten „Programm hinzufügen“ zu starten.

   ![](/help/journey-onboarding/assets/setup-resources4.png)

   >[!TIP]
   >
   >Sehen Sie sich das [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html) an, um zu erfahren, wie Sie Ihr AEM as a Cloud-Programm erstellen, und erfahren Sie, was Sie vor der Erstellung Ihres Programms beachten müssen.

   >[!TIP]
   >
   >Eine schrittweise Anleitung zur Verwendung des Assistenten „Programm hinzufügen“ finden Sie [hier](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-program.md).

1. Nach erfolgreicher Erstellung Ihres Cloud-Programms können Sie zu Ihrem Programm gehen, um die Seite **Überblick** Ihres Programms anzuzeigen, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/setup-resources8.png)

   >[!NOTE]
   >
   >Wenn Sie dies noch nicht getan haben, können Sie jetzt die Entwickler-Mitglieder zu Ihrem Cloud Manager-Team hinzufügen. Weitere Informationen finden Sie unter „Benutzer zum Produktprofil „Entwickler“ hinzufügen“. Führen Sie die dort beschriebenen Schritte aus.

1. Mitglieder, die dem Produktprofil „Entwickler“ zugewiesen sind, können sich bei Cloud Manager und [Cloud Manager-Git verwalten](/help/implementing/cloud-manager/managing-code/accessing-repos.md) anmelden.

   Gute Arbeit! Nachdem Ihr Programm erfolgreich erstellt wurde, können Ihre Entwickler auf Ihr Cloud Manager-Git zugreifen!


## Erstellen von Cloud-Umgebungen {#create-cloud-environments}

Nachdem Sie Ihr Cloud-Programm erfolgreich erstellt haben, erstellen Sie Ihre Cloud-Umgebungen.

Gehen Sie wie folgt vor, um Ihre Cloud-Umgebungen aus Cloud Manager heraus zu erstellen:

1. Gehen Sie zur Seite **Überblick** von Cloud Manager und wählen Sie **Hinzufügen** aus der Karte „Umgebung“ aus.

   ![](/help/journey-onboarding/assets/setup-resources9.png)

   >[!IMPORTANT]
   >
   >Ein Cloud Manager-Benutzer mit der Rolle „Geschäftsverantwortlicher“ oder „Implementierungs-Manager“ muss angemeldet sein, um diesen Schritt erfolgreich durchführen zu können.

   Sehen Sie sich außerdem das kurze [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html)-Tutorial an, um mehr über Cloud Manager-Umgebungen und darüber zu erfahren, wie Sie sie Ihrem Programm hinzufügen können.

1. Dadurch wird der Assistent „Umgebung hinzufügen“ gestartet, der Sie beim Hinzufügen Ihrer Umgebung unterstützt. Fügen Sie zuerst Ihre Entwicklungsumgebung hinzu, um sich mit dem Assistenten vertraut zu machen. Weitere Informationen finden Sie unter [Hinzufügen einer Umgebung](/help/implementing/cloud-manager/manage-environments.md#adding-environments).

   >[!NOTE]
   >
   >Wenn Sie dies noch nicht getan haben, können Sie jetzt die Entwickler-Mitglieder zu Ihrem Cloud Manager-Team hinzufügen. Weitere Informationen finden Sie unter „Benutzer zum Produktprofil „Entwickler“ hinzufügen“. Führen Sie die dort beschriebenen Schritte aus.

1. Mitglieder, die dem Entwicklerproduktprofil zugewiesen sind, können sich bei Cloud Manager anmelden und [Verwalten von Cloud Manager Git.](/help/implementing/cloud-manager/managing-code/accessing-repos.md)

   Gute Arbeit! Nun wurde Ihr Programm erfolgreich erstellt und Ihre Entwickler können auf Ihr Cloud Manager-Git zugreifen!

   Herzlichen Glückwunsch! Jetzt wurden Ihre Cloud-Programmumgebungen erstellt und Ihre Entwickler wurden zum Team hinzugefügt!

## Wie geht es weiter? {#whats-next}

Ihren Team-Mitgliedern müssen Berechtigungen für die Instanz erteilt werden, da die Berechtigungen zum Verwalten von Cloud Manager nicht ausreichen. Nun, da Ihre Cloud-Ressourcen erstellt wurden und Ihr Team darauf zugreifen kann, muss der Systemadministrator Ihre Team-Mitglieder über die Adobe Admin Console den AEM as a Cloud Service-Produktprofilen zuweisen.

>[!NOTE]
>
>Um Zugriff auf AEM as a Cloud Service zu erhalten, müssen Benutzer zu einem von zwei Produktprofilen gehören: `AEM Users` oder `AEM Administrators`. Weitere Informationen finden Sie unter [Verwalten von Produkten und Benutzerzugriff in Admin Console](/help/security/ims-support.md#managing-products-and-user-access-in-admin-console).

Sie sollten Ihre Onboarding-Journey fortsetzen, indem Sie das Dokument zum nächsten Mal lesen. [Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service Produktprofilen.](/help/journey-onboarding/sysadmin/assign-team-members-aem-cloud-service.md)


## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Programmtypen und Hinzufügen eines Programms](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html)
* [Umgebungstypen und Hinzufügen einer Umgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html)
* [Verwalten von Cloud Manager-Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md)
* [Zugriff auf AEM as a Cloud Service von Admin Console aus konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html#adobe-ims-users)
