---
title: Einrichten von Cloud-Ressourcen über Cloud Manager
description: Erfahren Sie, wie Sie mit Cloud Manager Ihre eigenen Cloud-Ressourcen einrichten und verwalten können.
role: Admin, User, Developer
exl-id: de3a33b7-b459-4e47-b232-a0f88e2ce22e
source-git-commit: 0db24518610fccf0d2ea5e0620a0c6a5f8009ea8
workflow-type: tm+mt
source-wordcount: '1369'
ht-degree: 100%

---

# Einrichten von Cloud-Ressourcen über Cloud Manager {#setup-cloud-resources}

Erfahren Sie, wie Sie mit Cloud Manager Ihre eigenen Cloud-Ressourcen einrichten und verwalten können.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Ihre Cloud-Ressourcen erstellt werden und wer sie erstellen kann. Nach Lesen dieses Abschnitts sollten Sie Folgendes verstehen:

* Ein Systemadministrator, dem die Rolle **Geschäftsinhabers** zugewiesen wurde, muss der erste in Ihrem Unternehmen sein, die sich anmeldet und auf Cloud Manager zugreift.
* Wie Ihr Cloud-Programm und Umgebungen erstellt werden.

## Einführung {#introduction}

Das Hinzufügen Ihrer Cloud-Ressourcen erfolgt über Cloud Manager durch Ihr Team-Mitglied, das dem Cloud Manager-Produktprofil **Geschäftsinhaber** zugewiesen ist. Diese Person ist in der Regel eine Person, die die Geschäftsanforderungen versteht und die Ersteinrichtung von Cloud Manager abschließt.

In den folgenden Abschnitten erfahren Sie, wie Sie Ihre [Cloud Service-Programme](#create-cloud-service-program) und -[Umgebungen](#create-cloud-environments) erstellen.

### Voraussetzungen {#prerequisites}

* Der Systemadministrator, der der Rolle **Geschäftsinhaber** zugewiesen wurde, muss sich bei Cloud Manager anmelden, bevor andere Benutzer mit der Rolle **Geschäftsinhaber** versuchen, auf Cloud Manager zuzugreifen, um in diesem Dokument beschriebene Schritte durchzuführen.

   * Kehren Sie zum Dokument [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) zurück, um mehr zu erfahren.

* Sie müssen verstehen, wie Sie [zu Cloud Manager gelangen und sich dort anmelden.](/help/onboarding/learn-concepts/cloud-manager-introduction.md)

* Sie sollten mit [Cloud Manager-Produktprofilen](/help/onboarding/learn-concepts/aem-cs-team-product-profiles.md#cloud-manager-product-profiles) vertraut sein.

* Sie sollten die Konzepte von Cloud Manager-[Programmen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/program-types.md) und -[Umgebungen](/help/implementing/cloud-manager/manage-environments.md) verstehen.

## Zugriff auf Cloud Manager als Systemadministrator und Geschäftsinhaber {#access-sysadmin-bo}

Bevor die Team-Mitglieder, denen Sie die Rolle des **Geschäftsinhabers** zugewiesen haben, auf Cloud Manager zugreifen und mit der Erstellung von Cloud-Ressourcen beginnen können, muss dem Systemadministrator die Rolle des **Geschäftsinhabers** zugewiesen werden und er muss sich bei Cloud Manager anmelden.

1. Stellen Sie als Systemadministrator sicher, dass Ihnen die Rolle **Geschäftsinhaber** zugewiesen wurde.

   * Kehren Sie zum vorherigen Schritt dieser Tour zurück, [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md), um weitere Informationen über die Zuweisung der Rolle des **Geschäftsinhabers** an den Systemadministrator zu erhalten, falls Sie dies noch nicht getan haben.

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und lassen Sie sich die normale Landingpage anzeigen.

Durch die erfolgreiche Anmeldung als Systemadministrator mit der Rolle des **Geschäftsinhabers** initialisieren Sie Cloud Manager für die Verwendung durch andere Benutzer mit der Rolle des **Geschäftsinhabers**. Sie erhalten keine Bestätigung mit dieser oder irgendeiner Nachricht. Die Anmeldung genügt einfach.

Solange Sie sich nicht als Systemadministrator mit der Rolle **Geschäftsinhaber** bei Cloud Manager anmelden, können andere Benutzer mit der Rolle **Geschäftsinhaber** keine Programme in Cloud Manager erstellen, selbst wenn ihnen die richtigen Rollen zugewiesen sind.

## Navigieren zu Cloud Manager {#navigate-cloud-manager}

Der Benutzer mit der Rolle **Geschäftsinhaber** erhält eine Begrüßungs-E-Mail mit einem Link zu den ersten Schritten. Gehen Sie wie folgt vor, um mithilfe dieser Begrüßungs-E-Mail zu Cloud Manager zu gelangen.

1. Klicken Sie in Ihrer Begrüßungs-E-Mail auf **Erste Schritte**, wie in der folgenden Abbildung dargestellt.
   ![E-Mail-Beispiel](/help/journey-onboarding/assets/get-started-email.png)

1. Gehen Sie zur Seite **Programme und Produkte** von Cloud Manager.

   >[!TIP]
   >
   >Alternativ können Sie auch direkt von [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) zur Anmeldeseite von Cloud Manager gelangen. Bitte setzen Sie für diese Seite für künftige Referenzzwecke ein Lesezeichen.

1. Sie werden zur Landingpage von Cloud Manager weitergeleitet. Weitere Informationen finden Sie im Abschnitt [Anzeigen der Cloud Manager-Programme](#viewing-programs).

Darüber hinaus können Sie von der Adobe Experience Cloud-Startseite aus auch zur Seite **Programme und Produkte** von Cloud Manager gehen.

1. Gehen Sie direkt zu [Adobe Experience Cloud](https://experience.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie auf der Adobe Experience Cloud-Startseite **Experience Manager** aus.

   ![Experience Cloud-Startseite](/help/journey-onboarding/assets/setup-resources2.png)

1. Dadurch gelangen Sie zur AEM-Startseite. Klicken Sie hier auf der Kachel **Cloud Manager** auf **Starten**.

   ![AEM-Startseite](/help/journey-onboarding/assets/setup-resources3.png)

1. Nach erfolgreicher Anmeldung werden Sie zur Landingpage von Cloud Manager weitergeleitet. Weitere Informationen finden Sie im Abschnitt [Anzeigen der Cloud Manager-Programme](#viewing-programs).

Der Zugriff auf Ihre Programme und Produkte über Cloud Manager liegt bei Ihnen und hat keine Auswirkungen auf die Verwendung von Cloud Manager oder die Verwaltung Ihrer Programme.

>[!NOTE]
>
>Je nach den in [!UICONTROL Cloud Manager] zugewiesenen Rollen und dem Programmstatus werden bei der Verwendung der [!UICONTROL Cloud Manager]-Benutzeroberfläche unterschiedliche Bildschirme angezeigt.

### Anzeigen von Programmen {#viewing-programs}

Sobald Sie erfolgreich auf den Cloud Manager zugreifen, hängt das, was Sie sehen, vom Status Ihrer Programme ab, wie in den folgenden Abschnitten beschrieben.

#### Wenn es keine Programme gibt {#no-programs}

Wenn in Ihrer Organisation keine Programme vorhanden sind, werden Sie von Ihrer Landingpage angewiesen, Ihr erstes Programm zu erstellen.

![Keine Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

#### Wenn es bereits Programme gibt {#programs-exist}

Wenn in Ihrer Organisation bereits Programme vorhanden sind, zeigt Ihre Landingpage Ihre vorhandenen Programme an und bietet außerdem eine Schaltfläche zum Hinzufügen zusätzlicher Programme.

![Programme sind vorhanden](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

#### Wenn ein Programm vorhanden ist und Sie ein Systemadministrator sind {#programs-exist-sysadmin}

Wenn in Ihrer Organisation bereits Programme vorhanden sind und Sie Systemadministrator sind, wird auf der Landingpage die Schaltfläche **Zugriff verwalten** zusammen mit der Option **Programm hinzufügen** angezeigt.

![Systemadministratoransicht](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)


## Überprüfen der Benutzerrollen {#verify-user-roles}

Nachdem Sie sich erfolgreich bei Cloud Manager angemeldet haben, können Sie verifizieren, dass Ihnen das Produktprofil **Geschäftsinhaber** zugewiesen wurde.

1. Wählen Sie Ihr Profil oben rechts im Fenster aus.

   ![Benutzerprofil](/help/journey-onboarding/assets/setup-resources5.png)

1. Wählen Sie **Benutzerrollen** aus, um die Ihrem Benutzer zugewiesenen Rollen anzuzeigen.

   ![Benutzerrollen](/help/journey-onboarding/assets/setup-resources6.png)

1. Vergewissern Sie sich, dass Ihr Benutzer über die Rolle **Geschäftsinhaber** verfügt.

   ![Liste der Benutzerrollen](/help/journey-onboarding/assets/setup-resources7.png)

Sie haben sich erfolgreich als Geschäftsinhaber bei Cloud Manager angemeldet! Wenn Ihnen die Rolle des **Geschäftsinhabers** nicht zugewiesen wurde, wenden Sie sich an Ihren Systemadministrator.

## Erstellen eines Cloud-Service-Programms {#create-cloud-service-program}

Nachdem Sie sich vergewissert haben, dass Sie den richtigen Zugriff haben, können Sie Ihr erstes Programm erstellen.

1. Gehen Sie unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) zur Landingpage von Cloud Manager und melden Sie sich an.

1. Klicken Sie auf der Landingpage von Cloud Manager auf **Programm hinzufügen**, um den Assistenten „Programm hinzufügen“ zu starten.

   ![Landingpage](/help/journey-onboarding/assets/setup-resources4.png)

   >[!TIP]
   >
   >Eine schrittweise Anleitung zur Verwendung des Assistenten „Programm hinzufügen“ finden Sie im Dokument [Erstellen von Produktionsprogrammen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md) oder sehen Sie sich dieses [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=de) an, um zu erfahren, wie Sie Ihr AEM as a Cloud-Programm erstellen und wichtige Überlegungen vor der Erstellung Ihres Programms kennenlernen.


1. Nach erfolgreicher Erstellung Ihres Cloud-Programms können Sie von der Cloud Manager-Landingpage aus zu Ihrem Programm gehen, um die Seite **Übersicht** Ihres Programms zu sehen.

   ![Programmübersicht](/help/journey-onboarding/assets/setup-resources8.png)

1. Mitglieder, die dem Produktprofil „Entwickler“ zugewiesen sind, können sich bei Cloud Manager anmelden und Cloud Manager-Git-Repositorys verwalten.

   * Wenn Sie dies noch nicht getan haben, ist jetzt eine gute Zeit, Mitglieder in Ihrem Cloud Manager-Team der Rolle **Entwickler** zuzuweisen. Kehren Sie zum Dokument [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](/help/journey-onboarding/sysadmin/assign-team-members-cloud-manager.md) zurück, um mehr zu erfahren.

Nun wurde Ihr Programm erfolgreich erstellt und Ihre Entwickler können auf Ihr Cloud Manager-Git-Repository zugreifen!

## Erstellen von Cloud-Umgebungen {#create-cloud-environments}

Nachdem Sie Ihr Cloud-Programm erfolgreich erstellt haben, erstellen Sie Ihre Cloud-Umgebungen.

1. Gehen Sie unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) zur Landingpage des Cloud Managers und wählen Sie auf der Umgebungskarte **Hinzufügen** aus.

   ![Schaltfläche „Umgebung hinzufügen“](/help/journey-onboarding/assets/setup-resources9.png)

1. Der Assistent zum Hinzufügen einer Umgebung wird gestartet und führt Sie durch das Hinzufügen Ihrer Umgebung. Fügen Sie zuerst Ihre Entwicklungsumgebung hinzu, um sich mit dem Assistenten vertraut zu machen.

   >[!TIP]
   >
   >Lesen Sie das Dokument [Hinzufügen einer Umgebung](/help/implementing/cloud-manager/manage-environments.md#adding-environments), um mehr zu erfahren, oder sehen Sie sich [dieses kurze Video-Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=de) an, um mehr über Cloud Manager-Umgebungen zu erfahren und darüber, wie Sie sie zu Ihrem Programm hinzufügen können.

1. Mitglieder, die dem Produktprofil **Entwickler** zugewiesen sind, können sich bei Cloud Manager anmelden und Cloud Manager-Git-Repositorys verwalten.

Nun wurde Ihr Programm erfolgreich erstellt und Ihre Entwickler können auf Ihr Cloud Manager-Git-Repository zugreifen!

## Wie geht es weiter? {#whats-next}

Nun, da Ihre Cloud-Ressourcen erstellt wurden und Ihr Team darauf zugreifen kann, muss der Systemadministrator Ihre Team-Mitglieder über die Adobe Admin Console den AEM as a Cloud Service-Produktprofilen zuweisen, damit sie auf Ressourcen zugreifen können.

Sie sollten Ihre Onboarding-Tour fortsetzen, indem Sie als Nächstes das Dokument [Zuweisen von Team-Mitgliedern zu AEM as a Cloud Service-Produktprofilen](/help/journey-onboarding/sysadmin/assign-team-members-aem-cloud-service.md) lesen, in dem Sie erfahren, wie Sie Ihren Team-Mitgliedern die Rechte erteilen, die sie für den Zugriff auf Ihre neuen Umgebungen benötigen.

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Programmtypen und Hinzufügen eines Programms](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html)
* [Umgebungstypen und Hinzufügen einer Umgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html)
* [Verwalten von Cloud Manager-Git](/help/implementing/cloud-manager/managing-code/accessing-repos.md)
* [Konfigurieren des Zugriffs auf AEM as a Cloud Service von der Admin Console aus](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=de#adobe-ims-users)
