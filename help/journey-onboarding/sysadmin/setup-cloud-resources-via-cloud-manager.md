---
title: Einrichten von Cloud-Ressourcen über Cloud Manager
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre eigenen Cloud-Ressourcen einrichten und verwalten können.
role: Admin, User, Developer
exl-id: de3a33b7-b459-4e47-b232-a0f88e2ce22e
source-git-commit: 0db24518610fccf0d2ea5e0620a0c6a5f8009ea8
workflow-type: tm+mt
source-wordcount: '1369'
ht-degree: 23%

---

# Einrichten von Cloud-Ressourcen über Cloud Manager {#setup-cloud-resources}

Erfahren Sie, wie Sie mit Cloud Manager Ihre eigenen Cloud-Ressourcen einrichten und verwalten können.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Ihre Cloud-Ressourcen erstellt werden und wer sie erstellen kann. Nach Lesen dieses Abschnitts sollten Sie Folgendes verstehen:

* Ein Systemadministrator, der dem **Business Owner** Die Rolle muss die erste Rolle in Ihrem Unternehmen sein, die sich anmeldet und auf Cloud Manager zugreift.
* Wie Ihr Cloud-Programm und Umgebungen erstellt werden.

## Einführung {#introduction}

Das Hinzufügen Ihrer Cloud-Ressourcen erfolgt über Cloud Manager durch Ihr Team-Mitglied, das dem **Business Owner** Produktprofil. Diese Person ist in der Regel eine Person, die die Geschäftsanforderungen versteht und die Ersteinrichtung von Cloud Manager abschließt.

In den folgenden Abschnitten erfahren Sie, wie Sie Ihre [Cloud Service-Programme](#create-cloud-service-program) und -[Umgebungen](#create-cloud-environments) erstellen.

### Voraussetzungen {#prerequisites}

* Der Systemadministrator, der dem **Business Owner** -Rolle muss sich vor allen anderen Benutzern mit der Funktion **Business Owner** Rollenversuche, auf Cloud Manager zuzugreifen, um die in diesem Dokument beschriebenen Schritte durchzuführen und durchzuführen.

   * Kehren Sie zu [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) für weitere Informationen.

* Sie müssen verstehen, wie [Navigieren Sie zu Cloud Manager und melden Sie sich an.](/help/onboarding/learn-concepts/cloud-manager-introduction.md)

* Du solltest dich mit [Cloud Manager-Produktprofile.](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md#cloud-manager-product-profiles)

* Sie sollten die Konzepte von Cloud Manager verstehen [Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) und [Umgebungen.](/help/implementing/cloud-manager/manage-environments.md)

## Zugriff auf Cloud Manager als Systemadministrator und Business Owner {#access-sysadmin-bo}

Vor den Teammitgliedern, die Sie der **Business Owner** Rolle kann auf den Cloud Manager zugreifen und mit der Erstellung von Cloud-Ressourcen beginnen. Dem Systemadministrator muss die **Business Owner** Rolle und melden Sie sich bei Cloud Manager an.

1. Stellen Sie als Systemadministrator sicher, dass Sie über die **Business Owner** zugewiesene Rolle.

   * Kehren Sie zum vorherigen Schritt in dieser Journey zurück, [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen,](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) Weitere Informationen zur Zuweisung der **Business Owner** Rolle für den Systemadministrator angeben, falls Sie dies noch nicht getan haben.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und der normalen Landingpage angezeigt werden.

Durch erfolgreiche Anmeldung als Systemadministrator mit der **Business Owner** Rolle, initialisieren Sie Cloud Manager zur Verwendung durch die anderen Benutzer mit der **Business Owner** Rolle. Sie erhalten keine Bestätigung dieser oder einer Nachricht. Die Anmeldung genügt einfach.

Bis Sie sich bei Cloud Manager als Systemadministrator bei der **Business Owner** Rolle, anderen Benutzern mit dem **Business Owner** -Rolle kann keine Programme in Cloud Manager erstellen, selbst wenn ihnen die richtigen Rollen zugewiesen sind.

## Navigieren zu Cloud Manager {#navigate-cloud-manager}

Der Benutzer mit der **Business Owner** -Rolle erhält eine Begrüßungs-E-Mail mit einem Link zu den ersten Schritten. Gehen Sie wie folgt vor, um mithilfe dieser Begrüßungs-E-Mail zu Cloud Manager zu navigieren.

1. Klicken Sie in Ihrer Willkommens-E-Mail auf **Erste Schritte**, wie in der folgenden Abbildung dargestellt.
   ![E-Mail-Beispiel](/help/journey-onboarding/assets/get-started-email.png)

1. Gehen Sie zur Seite **Programme und Produkte** von Cloud Manager.

   >[!TIP]
   >
   >Sie können auch direkt zur Anmeldeseite von Cloud Manager navigieren von [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/). Bitte Lesezeichen für diese Seite für künftige Referenzzwecke setzen.

1. Sie werden zur Landingpage von Cloud Manager weitergeleitet. Weitere Informationen finden Sie im Abschnitt [Anzeigen der Cloud Manager-Programme](#viewing-programs).

Sie können auch zur Cloud Manager- **Programme und Produkte** von der Adobe Experience Cloud-Startseite aus, indem Sie die folgenden Schritte ausführen

1. Gehen Sie direkt zu [Adobe Experience Cloud](https://experience.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie auf der Adobe Experience Cloud-Startseite **Experience Manager** aus.

   ![Experience Cloud-Homepage](/help/journey-onboarding/assets/setup-resources2.png)

1. Dadurch gelangen Sie zur AEM-Startseite. Klicken Sie hier auf **Launch** auf **Cloud Manager** Kachel.

   ![AEM Homepage](/help/journey-onboarding/assets/setup-resources3.png)

1. Nach erfolgreicher Anmeldung werden Sie zur Landingpage von Cloud Manager weitergeleitet. Weitere Informationen finden Sie im Abschnitt [Anzeigen der Cloud Manager-Programme](#viewing-programs).

Der Zugriff auf Ihre Programme und Produkte über Cloud Manager liegt bei Ihnen und hat keine Auswirkungen auf die Verwendung von Cloud Manager oder die Verwaltung Ihrer Programme.

>[!NOTE]
>
>Je nach den in [!UICONTROL Cloud Manager] zugewiesenen Rollen und dem Programmstatus werden bei der Verwendung der [!UICONTROL Cloud Manager]-Benutzeroberfläche unterschiedliche Bildschirme angezeigt.

### Anzeigen von Programmen {#viewing-programs}

Sobald Sie erfolgreich auf Cloud Manager zugreifen, hängt der Status Ihrer Programme ab, wie in den folgenden Abschnitten beschrieben.

#### Wenn keine Programme vorhanden sind {#no-programs}

Wenn in Ihrer Organisation keine Programme vorhanden sind, werden Sie von Ihrer Landingpage angewiesen, Ihr erstes Programm zu erstellen.

![Keine Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### Wenn bereits Programme vorhanden sind {#programs-exist}

Wenn in Ihrer Organisation bereits Programme vorhanden sind, zeigt Ihre Landingpage Ihre vorhandenen Programme an und bietet außerdem eine Schaltfläche zum Hinzufügen zusätzlicher Programme.

![Programme existieren](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### Wenn ein Programm vorhanden ist und Sie ein Systemadministrator sind {#programs-exist-sysadmin}

Wenn in Ihrer Organisation bereits Programme vorhanden sind und Sie Systemadministrator sind, wird Ihre Landingpage angezeigt **Zugriff verwalten** -Schaltfläche zusammen mit **Programm hinzufügen** -Option.

![Systemadministratoransicht](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## Überprüfen der Benutzerrollen {#verify-user-roles}

Nachdem Sie sich erfolgreich bei Cloud Manager angemeldet haben, können Sie überprüfen, ob Ihnen die **Business Owner** Produktprofil.

1. Wählen Sie Ihr Profil oben rechts im Fenster aus.

   ![Benutzerprofil](/help/journey-onboarding/assets/setup-resources5.png)

1. Auswählen **Benutzerrollen** , um die Ihrem Benutzer zugewiesenen Rollen anzuzeigen.

   ![Benutzerrollen](/help/journey-onboarding/assets/setup-resources6.png)

1. Vergewissern Sie sich, dass Ihr Benutzer über die **Business Owner** Rolle.

   ![Liste der Benutzerrollen](/help/journey-onboarding/assets/setup-resources7.png)

Sie haben sich erfolgreich als Geschäftsverantwortlicher bei Cloud Manager angemeldet! Wenn Ihnen die Variable **Business Owner** -Rolle, wenden Sie sich an Ihren Systemadministrator.

## Cloud Service-Programm erstellen {#create-cloud-service-program}

Nachdem Sie den entsprechenden Zugriff sichergestellt haben, können Sie Ihr erstes Programm erstellen.

1. Navigieren Sie zur Landingpage von Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und melden Sie sich an.

1. Klicken Sie auf der Landingpage von Cloud Manager auf **Programm hinzufügen** , um den Assistenten Programm hinzufügen zu starten.

   ![Einstiegsseite](/help/journey-onboarding/assets/setup-resources4.png)

   >[!TIP]
   >
   >Eine schrittweise Anleitung zur Verwendung des Assistenten &quot;Programm hinzufügen&quot;finden Sie im Dokument [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) oder sehen Sie sich dies an [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de) , um zu erfahren, wie Sie Ihr AEM as a Cloud-Programm erstellen und wichtige Überlegungen vor der Erstellung Ihres Programms kennenlernen.


1. Nach erfolgreicher Erstellung Ihres Cloud-Programms können Sie von der Cloud Manager-Landingpage aus zu Ihrem Programm navigieren, um die **Übersicht** Seite Ihres Programms.

   ![Programmübersicht](/help/journey-onboarding/assets/setup-resources8.png)

1. Mitglieder, die dem Produktprofil &quot;Entwickler&quot;zugewiesen sind, können sich bei Cloud Manager anmelden und Cloud Manager-Git-Repositorys verwalten.

   * Wenn Sie dies noch nicht getan haben, ist jetzt eine gute Zeit, Mitglieder dem **Entwickler** Rolle in Ihrem Cloud Manager-Team. Kehren Sie zu [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) für weitere Informationen.

Jetzt wurde Ihr Programm erfolgreich erstellt und Ihr Cloud Manager-Git-Repository steht Ihren Entwicklern für den Zugriff zur Verfügung!

## Erstellen von Cloud-Umgebungen {#create-cloud-environments}

Nachdem Sie Ihr Cloud-Programm erfolgreich erstellt haben, erstellen Sie Ihre Cloud-Umgebungen.

1. Navigieren Sie zur Landingpage von Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) und wählen Sie **Hinzufügen** von der Umgebungskarte aus.

   ![Schaltfläche &quot;Umgebung hinzufügen&quot;](/help/journey-onboarding/assets/setup-resources9.png)

1. Der Assistent zum Hinzufügen einer Umgebung wird gestartet und führt Sie durch das Hinzufügen Ihrer Umgebung. Fügen Sie zuerst Ihre Entwicklungsumgebung hinzu, um sich mit dem Assistenten vertraut zu machen.

   >[!TIP]
   >
   >Siehe Dokument . [Hinzufügen einer Umgebung](/help/implementing/cloud-manager/manage-environments.md#adding-environments) mehr dazu oder sehen Sie sich an [dieses Schnellvideo-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de) , um mehr über Cloud Manager-Umgebungen zu erfahren und zu erfahren, wie Sie sie Ihrem Programm hinzufügen können.

1. Mitglieder, die **Entwickler** Produktprofil kann sich bei Cloud Manager anmelden und Cloud Manager-Git-Repositorys verwalten.

Jetzt wurde Ihr Programm erfolgreich erstellt und Ihr Cloud Manager-Git steht Ihren Entwicklern zur Verfügung!

## Wie geht es weiter? {#whats-next}

Nachdem Ihre Cloud-Ressourcen erstellt wurden und für Ihr Team zugänglich sind, muss der Systemadministrator Ihre Team-Mitglieder AEM as a Cloud Service Produktprofilen aus Adobe Admin Console zuweisen, um auf diese Ressourcen zugreifen zu können.

Sie sollten Ihre Onboarding-Journey fortsetzen, indem Sie das Dokument zum nächsten Mal lesen. [Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service Produktprofilen](/help/journey-onboarding/sysadmin/assign-team-members-aem-cloud-service.md) Hier erfahren Sie, wie Sie Ihren Teammitgliedern die Rechte gewähren, die sie für den Zugriff auf Ihre neuen Umgebungen benötigen.

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Programmtypen und Hinzufügen eines Programms](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html)
* [Umgebungstypen und Hinzufügen einer Umgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html)
* [Verwalten von Cloud Manager-Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md)
* [Konfigurieren des Zugriffs auf AEM as a Cloud Service von der Admin Console aus](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=de#adobe-ims-users)
