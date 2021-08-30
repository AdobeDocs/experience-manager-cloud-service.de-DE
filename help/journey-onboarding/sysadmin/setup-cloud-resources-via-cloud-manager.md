---
title: Einrichten von Cloud-Ressourcen über Cloud Manager
description: Auf dieser Seite erfahren Sie, wie Sie Cloud-Ressourcen über Cloud Manager einrichten
hide: true
index: false
role: Admin, User, Developer
source-git-commit: e58ee2d3669cfce25b354bd78047119c4132c64e
workflow-type: tm+mt
source-wordcount: '1428'
ht-degree: 15%

---

# Einrichten von Cloud-Ressourcen über Cloud Manager {#setup-cloud-resources}

Der Systemadministrator, der der Rolle &quot;Business Owner&quot;zugewiesen ist, sollte auf Cloud Manager zugreifen und sich dort anmelden. Danach muss sich ein dem Produktprofil Business Owner zugewiesenes Team-Mitglied bei Cloud Manager anmelden und Ihr Cloud-Programm und Ihre Umgebungen erstellen, damit Ihr Expertenteam beginnen kann.

## Ziele {#objective}

In diesem Dokument erfahren Sie, wie Ihre Cloud-Ressourcen erstellt werden und wer sie verwenden kann.

Nach Lesen dieses Abschnitts sollten Sie Folgendes verstehen:

* Ein Systemadministrator, der der Rolle &quot;Business Owner&quot;zugewiesen ist, muss als erster auf Cloud Manager zugreifen und sich dort anmelden.
* Erstellung des Cloud-Programms und der Umgebungen.

## Einführung {#introduction}

Das Hinzufügen Ihrer Cloud-Ressourcen erfolgt über Cloud Manager durch Ihr Team-Mitglied, das dem Cloud Manager Business Owner-Produktprofil zugewiesen ist. Diese Person ist in der Regel eine Person, die die Geschäftsanforderungen versteht und die Ersteinrichtung von Cloud Manager abschließt.

In den folgenden Abschnitten erfahren Sie, wie Sie Ihre [Cloud Service-Programme](#create-cloud-service-program) und [Umgebungen](#create-cloud-environments) erstellen.

### Voraussetzungen {#prerequisites}

* Der Systemadministrator, der der Rolle &quot;Business Owner&quot;zugewiesen ist, sollte auf Cloud Manager zugreifen und sich dort anmelden.

* Hier erfahren Sie, wie Sie [zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/what-is-required/navigate-to-cloud-manager.html?lang=en) navigieren und sich dort anmelden.

* Machen Sie sich mit [Cloud Manager-Produktprofilen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/aem-cs-team-product-profiles.html?lang=en#cloud-manager-product-profiles) vertraut.

* Grundlegendes zu den Konzepten von Cloud Manager [Programmen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/understand-program-types.html?lang=en) und [Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de)

## Zu Cloud Manager navigieren {#navigate-cloud-manager}

Der Business Owner-Benutzer erhält eine Begrüßungs-E-Mail mit einem Link zu den ersten Schritten. Wenn er sie nicht finden kann, greifen Sie direkt auf [Cloud Manager](https://my.cloudmanager.adobe.com/) zu, indem Sie sich mit Ihrer Adobe ID anmelden.

Gehen Sie wie folgt vor, um zu Cloud Manager zu navigieren:

1. Klicken Sie in Ihrer Willkommens-E-Mail auf **Erste Schritte**, wie in der folgenden Abbildung dargestellt.
   ![](/help/journey-onboarding/assets/get-started-email.png)

1. Navigieren Sie zur Seite **Programme und Produkte** von Cloud Manager.

   >[!IMPORTANT]
   >Alternativ können Sie auch direkt von [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) zur Anmeldeseite von Cloud Manager navigieren. Bitte Lesezeichen für diese Seite einfügen, um Sie bei der Navigation zur Landingpage von Cloud Manager zu unterstützen.

1. Sie werden zur Landingpage von Cloud Manager weitergeleitet. Weitere Informationen finden Sie im Abschnitt [Anzeigen der Cloud Manager-Programme](#viewing-programs) .

Darüber hinaus können Sie von der Adobe Experience Cloud-Startseite aus zur Seite **Programme und Produkte** von Cloud Manager navigieren. Führen Sie dazu folgende Schritte durch:

1. Navigieren Sie direkt zu [Adobe Experience Cloud](https://experience.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie auf der Adobe Experience Cloud-Startseite **Experience Manager** aus.

   ![](/help/journey-onboarding/assets/setup-resources2.png)

1. Dadurch gelangen Sie zur AEM Homepage. Starten Sie von hier aus **Cloud Manager** .

   ![](/help/journey-onboarding/assets/setup-resources3.png)

1. Nach erfolgreicher Anmeldung werden Sie zur Landingpage von Cloud Manager weitergeleitet. Weitere Informationen finden Sie im Abschnitt [Anzeigen der Cloud Manager-Programme](#viewing-programs) .

   >[!NOTE]
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

Nachdem Sie sich erfolgreich bei Cloud Manager angemeldet haben, führen Sie die folgenden Schritte aus, um sicherzustellen, dass Ihnen das Produktprofil &quot;Business Owner&quot;zugewiesen wurde:

1. Wählen Sie Ihr Profil oben rechts aus, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/setup-resources5.png)

1. Wählen Sie **Benutzerrollen** aus und stellen Sie sicher, dass Sie dem Business Owner zugewiesen sind.

   ![](/help/journey-onboarding/assets/setup-resources6.png)

1. Dadurch wird Ihre Benutzerrolle als Business Owner bestätigt.

   ![](/help/journey-onboarding/assets/setup-resources7.png)

   Gute Arbeit! Sie haben sich erfolgreich als Business Owner bei Cloud Manager angemeldet!

## Cloud Service erstellen {#create-cloud-service-program}

Gehen Sie wie folgt vor, um Ihr Cloud Service-Programm aus Cloud Manager zu erstellen:

1. Navigieren Sie zur Landingpage von Cloud Manager , wie unten dargestellt.

   >[!NOTE]
   >Sie müssen ein Team-Mitglied sein, das dem Cloud Manager Business Owner-Produktprofil zugewiesen ist, um diesen Schritt erfolgreich abzuschließen.

   Klicken Sie hier auf **Programm hinzufügen** , um den Assistenten Programm hinzufügen zu starten.

   ![](/help/journey-onboarding/assets/setup-resources4.png)

   >[!NOTE]
   >Sehen Sie sich das [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en) an, um zu erfahren, wie Sie Ihr AEM as a Cloud-Programm erstellen. Außerdem erhalten Sie Informationen über wichtige Aspekte, bevor Sie Ihr Programm erstellen.

   >[!IMPORTANT]
   >Eine schrittweise Anleitung zur Verwendung des Assistenten Programm hinzufügen finden Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/production-programs/creating-production-program.html?lang=en).
   >
   >* Beachten Sie, dass der Programmname nach der Erstellung nicht mehr geändert werden kann. Wir empfehlen Ihnen, sich bezüglich des Namens, den Sie Ihrem Programm geben möchten, sicher zu sein.
   >* Falls Sie den Programmnamen ändern müssen, müssen Sie sich an den Support der Adobe wenden oder sich alternativ an Ihren Kundenbetreuer der Adobe wenden. Sie werden dazu beitragen, das Programm effektiv zu löschen. Sie müssen von Anfang an mit einem potenziellen Verlust an Arbeit beginnen, den Ihr Team geleistet hat.


1. Nach erfolgreicher Erstellung Ihres Cloud-Programms können Sie zu Ihrem Programm navigieren, um die Seite **Übersicht** Ihres Programms anzuzeigen, wie unten dargestellt.

   ![](/help/journey-onboarding/assets/setup-resources8.png)

   >[!NOTE]
   >Wenn Sie dies noch nicht getan haben, können Sie jetzt Ihre Entwickler-Mitglieder Ihrem Cloud Manager-Team hinzufügen. Weitere Informationen finden Sie unter Benutzer zum Produktprofil &quot;Entwickler&quot;hinzufügen und führen Sie die beschriebenen Schritte aus.

1. Mitglieder, die dem Entwicklerproduktprofil zugewiesen sind, können sich bei Cloud Manager und [Cloud Manager-Git verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en) anmelden.

   Gute Arbeit! Nachdem Ihr Programm erfolgreich erstellt wurde, können Ihre Entwickler auf Ihr Cloud Manager-Git zugreifen!


## Erstellen von Cloud-Umgebungen {#create-cloud-environments}

Nachdem Sie Ihr Cloud-Programm erfolgreich erstellt haben, erstellen Sie Ihre Cloud-Umgebungen.

Gehen Sie wie folgt vor, um Ihre Cloud-Umgebungen aus Cloud Manager zu erstellen:

1. Navigieren Sie zur Seite **Übersicht** von Cloud Manager und wählen Sie **Hinzufügen** aus der Umgebungskarte aus.

   ![](/help/journey-onboarding/assets/setup-resources9.png)

   >[!IMPORTANT]
   >Ein Cloud Manager-Benutzer mit der Rolle Business Owner oder Deployment Manager muss angemeldet sein, um diesen Schritt erfolgreich durchführen zu können.

   Sehen Sie sich außerdem das kurze [Video](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en)-Tutorial an, um mehr über Cloud Manager-Umgebungen und darüber zu erfahren, wie Sie sie Ihrem Programm hinzufügen können.

1. Dadurch wird der Assistent zum Hinzufügen der Umgebung gestartet, der Sie durch das Hinzufügen Ihrer Umgebung führt. Fügen Sie zuerst Ihre Entwicklungsumgebung hinzu, um sich mit dem Assistenten vertraut zu machen. Weitere Informationen finden Sie unter [Hinzufügen einer Umgebung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/manage-environments.html?lang=de#adding-environments) .

   >[!NOTE]
   >Wenn Sie dies noch nicht getan haben, können Sie jetzt Ihre Entwickler-Mitglieder Ihrem Cloud Manager-Team hinzufügen. Weitere Informationen finden Sie unter Benutzer zum Produktprofil &quot;Entwickler&quot;hinzufügen und führen Sie die beschriebenen Schritte aus.

1. Mitglieder, die dem Entwicklerproduktprofil zugewiesen sind, können sich bei Cloud Manager und [Cloud Manager-Git verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en) anmelden.

   Gute Arbeit! Jetzt wurde Ihr Programm erfolgreich erstellt und Ihr Cloud Manager-Git steht Ihren Entwicklern zur Verfügung!

   Herzlichen Glückwunsch! Jetzt wurden Ihre Cloud-Programmumgebungen erstellt und Ihre Entwickler wurden zum Team hinzugefügt!

## Nächste Schritte {#whats-next}

Ihren Teammitgliedern müssen Berechtigungen für die Instanz erteilt werden, da die Berechtigungen zum Verwalten von Cloud Manager nicht ausreichen. Nachdem Ihre Cloud-Ressourcen erstellt wurden und für Ihr Team verfügbar sind, muss der Systemadministrator Ihre Team-Mitglieder AEM als Cloud Service-Produktprofile aus Adobe Admin Console zuweisen.

>[!NOTE]
>Um Zugriff auf AEM als Cloud Service zu erhalten, müssen Benutzer zu einem von zwei Produktprofilen gehören: `AEM Users` oder `AEM Administrators`. Weitere Informationen finden Sie unter [Verwalten von Produkten und Benutzerzugriff in Admin Console](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/security/ims-support.html?lang=en#managing-products-and-user-access-in-admin-console) .

Sie sollten Ihre Onboarding-Journey fortsetzen, indem Sie das Dokument [Zuweisen von Teammitgliedern zu AEM als Cloud Service Produktprofile](/help/journey-onboarding/sysadmin/assign-team-members-aem-cloud-service.md) erneut überprüfen.


## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Programmtypen und Hinzufügen eines Programms](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/programs.html?lang=en)
* [Umgebungstypen und Hinzufügen einer Umgebung](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/cloud-manager/environments.html?lang=en)
* [Verwalten von Cloud Manager Git](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/managing-code/accessing-git.html?lang=en)
* [Zugriff auf AEM als Cloud Service von Admin Console konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/accessing/overview.html?lang=en#adobe-ims-users)
