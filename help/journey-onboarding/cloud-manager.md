---
title: Zugreifen auf Cloud Manager
description: Erfahren Sie, wie Sie auf Cloud Manager zugreifen können, damit Sie Ihre Projektressourcen einrichten können.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
feature: Onboarding
source-git-commit: 0db48ef4c15b6ca530b2626f7078c7172c872fff
workflow-type: tm+mt
source-wordcount: '909'
ht-degree: 84%

---

# Zugreifen auf Cloud Manager {#cloud-resources}

In diesem Teil der [Onboarding-Tour](overview.md) erfahren Sie, wie Sie auf Cloud Manager zugreifen können, um Ihre Projektressourcen einzurichten.

## Ziel {#objective}

Im vorherigen Artikel dieser Onboarding-Tour, [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](assign-profiles-cloud-manager.md), haben Sie Ihrem AEMaaCS-Team die jeweiligen Rollen zugewiesen. Erfahren Sie jetzt, wie Sie auf Cloud Manager zugreifen können, damit Sie die Projektressourcen einrichten können, die Ihr Team verwenden wird.

Seit Sie den vorherigen Schritt in dieser Tour abgeschlossen haben, kann Ihr Team auf Cloud Manager zugreifen. Cloud Manager dient zum Erstellen und Verwalten von Projektressourcen, wie z. B. von Programmen und Umgebungen.

Nach dem Lesen dieses Dokuments sollten Sie Folgendes verstehen können:

* Dass die erste Anmeldung und der erste Zugriff auf Cloud Manager in Ihrer Organisation durch eine/n System-Admin mit der Rolle **Geschäftsinhaber** erfolgen muss.
* Wie Sie sich bei Cloud Manager anmelden.

## Cloud Manager {#cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM as a Cloud Service und dient als zentraler Einstiegspunkt für Ihr Team. Cloud Manager unterstützt Kunden und Kundinnen bei ihren Entwicklungsprojekten mit speziell dafür konzipierten CI/CD-Pipelines, die für umfassende Tests und höchste Code-Qualität zur Bereitstellung außergewöhnlicher Erlebnisse ausgelegt sind. Cloud Manager bietet alles, was für den Einstieg erforderlich ist, als Self-Service-Funktionalität, einschließlich der Möglichkeit, Ihre Cloud-Ressourcen und -Umgebungen selbst einzurichten.

Normalerweise ist ein Team-Mitglied mit dem Produktprofil **Geschäftsinhaber** für das Hinzufügen Ihrer Cloud-Ressourcen (wie Programme und Umgebungen) verantwortlich. Diese Person versteht die Geschäftsanforderungen und führt die Ersteinrichtung von Cloud Manager durch.

Im Rahmen dieser Onboarding-Tour haben Sie sich als System-Admin bereits selbst das Produktprofil **Geschäftsinhaber** zugewiesen und werden die Cloud-Ressourcen einrichten. Abhängig von den tatsächlichen Projektanforderungen können die Geschäftsinhaber mit den System-Admins identisch sein.

## Zugriff auf Cloud Manager als System-Admin und Geschäftsinhaber {#access-sysadmin-bo}

Bevor die Team-Mitglieder, denen Sie die Rolle des **Geschäftsinhabers** zugewiesen haben, auf Cloud Manager zugreifen und mit der Erstellung von Cloud-Ressourcen beginnen können, muss der bzw. dem System-Admin die Rolle des **Geschäftsinhabers** zugewiesen werden. Sie müssen sich auch bei Cloud Manager anmelden, wie Sie es im vorherigen Schritt in dieser Onboarding-Tour getan haben.

1. Stellen Sie sicher, dass Ihnen als System-Admin die Rolle als **Geschäftsinhaber** zugewiesen wurde.

   Kehren Sie zum vorherigen Schritt zurück ([Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen](assign-profiles-cloud-manager.md)), um weitere Informationen über die Zuweisung der Rolle **Geschäftsinhaber** zum bzw. zur System-Admin zu erhalten.

1. Melden Sie sich bei Cloud Manager unter [experience.adobe.com](https://experience.adobe.com) an.
1. Klicken Sie in der Schnellzugriffs-Gruppierung auf **Experience Manager**.
1. Klicken Sie im linken Bedienfeld auf **Cloud Manager**.

   ![Cloud Manager in der Konsole](/help/journey-onboarding/assets/consol-cloud-manager.png)

Durch die erfolgreiche Anmeldung als System-Admin mit der Rolle **Geschäftsinhaber** können Sie Cloud Manager für die Verwendung durch andere Benutzende mit der Rolle **Geschäftsinhaber** verwenden. Sie erhalten keine Bestätigung oder Nachricht. Die einfache Anmeldung ist ausreichend.

Solange Sie sich nicht als System-Admin mit der Rolle **Geschäftsinhaber** bei Cloud Manager anmelden, können andere Benutzende mit der Rolle **Geschäftsinhaber** keine Programme in Cloud Manager erstellen. Diese Regel gilt auch dann, wenn ihnen die richtigen Rollen zugewiesen sind.

## Navigieren zu Cloud Manager {#navigate-cloud-manager}

Personen mit der Rolle **Geschäftsinhaber** erhalten eine Begrüßungs-E-Mail mit einem Link für die ersten Schritte. Gehen Sie wie folgt vor, um mithilfe dieser Begrüßungs-E-Mail zu Cloud Manager zu navigieren.

1. Klicken Sie in Ihrer Begrüßungs-E-Mail auf **Erste Schritte**, wie in der folgenden Abbildung dargestellt.
   ![E-Mail-Beispiel](/help/journey-onboarding/assets/get-started-email.png)

1. Navigieren Sie zur Cloud Manager-Seite **Programme &amp; Produkte**.

   >[!TIP]
   >
   >Alternativ können Sie auch direkt von `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)` zur Anmeldeseite von Cloud Manager gelangen. Setzen Sie auf dieser Seite für künftige Referenzzwecke ein Lesezeichen.

1. Sie werden zur Landingpage von Cloud Manager weitergeleitet.

<!-- OLD
Alternatively, you can navigate to Cloud Manager's **Programs and Products** page from the Adobe Experience Cloud home page using these steps.

1. Navigate directly to [Adobe Experience Cloud](https://experience.adobe.com) and login using your Adobe ID.

1. From the Adobe Experience Cloud home page, select **Experience Manager** to open the AEM home page.

   ![Experience Cloud homepage](/help/journey-onboarding/assets/setup-resources2.png)

1. On the **Cloud Manager** tile, select **Launch**.

   ![AEM home page](/help/journey-onboarding/assets/setup-resources3.png)

1. After successfully logging on, you are directed to the Cloud Manager landing page. See [Viewing Cloud Manager's Programs](#viewing-programs) for more details.

How you access your programs and products via Cloud Manager is up to you and has no effect on how you use Cloud Manager or how you manage your programs.

>[!NOTE]
>
>Depending on the roles assigned in Cloud Manager and the state of the application, you see different screens while using the Cloud Manager user interface. -->

## Programme anzeigen {#viewing-programs}

Sobald Sie erfolgreich auf den Cloud Manager zugreifen, hängt das, was Sie sehen, vom Status Ihrer Programme ab, wie in den folgenden Abschnitten beschrieben.

### Wenn keine Programme vorhanden sind {#no-programs}

Wenn in Ihrer Organisation keine Programme vorhanden sind, werden Sie von Ihrer Landingpage angewiesen, Ihr erstes Programm zu erstellen.

![Keine Programme](/help/journey-onboarding/assets/cloud-manager-programs-do-not-exist.png)

### Wenn es bereits Programme gibt {#programs-exist}

Wenn in Ihrer Organisation bereits Programme vorhanden sind, zeigt Ihre Landingpage Ihre vorhandenen Programme an und bietet außerdem eine Schaltfläche zum Hinzufügen zusätzlicher Programme.

![Programme sind vorhanden](/help/journey-onboarding/assets/cloud-manager-programs-exist.png)

### Wenn es ein Programm gibt und Sie Systemadministrator sind {#programs-exist-sysadmin}

Wenn in Ihrer Organisation bereits Programme vorhanden sind und Sie System-Admin sind, werden auf Ihrer Landingpage die Schaltfläche **Zugriff verwalten** und die Option **Programm hinzufügen** angezeigt.

![Systemadministratoransicht](/help/journey-onboarding/assets/cloud-manager-programs-as-sysadmin.png)

## Überprüfen der Benutzerrollen {#verify-user-roles}

Nachdem Sie sich erfolgreich bei Cloud Manager angemeldet haben, können Sie überprüfen, ob Ihnen das Produktprofil **Geschäftsinhaber** zugewiesen ist.

1. Klicken Sie oben rechts auf der Seite auf das Symbol **Konto**.

1. Klicken Sie **Benutzerrollen**.

   ![Benutzerrollen](/help/journey-onboarding/assets/cloud-manager-user-roles.png)

1. Bestätigen Sie **Dialogfeld &quot;**&quot;, dass Ihr Benutzer über die Rolle **Geschäftsinhaber** verfügt.

   ![Liste der Benutzerrollen](/help/journey-onboarding/assets/cloud-manager-user-roles-business-owner.png)

Sie haben sich erfolgreich als Geschäftsinhaber bei Cloud Manager angemeldet. Wenn Ihnen die Rolle des **Geschäftsinhabers** nicht zugewiesen wurde, wenden Sie sich an Ihren Systemadministrator.

## Wie geht es weiter {#whats-next}

Jetzt, da Sie als System-Admin auf Cloud Manager zugreifen können, können Sie Ihr erstes Programm erstellen.

Setzen Sie Ihre Onboarding-Tour mit dem Lesen des Dokuments [Erstellen eines Programms](create-program.md) fort, in dem Sie erfahren, wie Sie dies tun können.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt der Onboarding-Tour hinausgehen möchten.

* [Einführung in Cloud Manager](/help/onboarding/cloud-manager-introduction.md) – 
Erfahren Sie mehr über Cloud Manager sowie Cloud Manager-Programme und -Umgebungen.
* [Team- und Produktprofile in AEM as a Cloud Service](/help/onboarding/aem-cs-team-product-profiles.md) – Erfahren Sie, wie Sie mit Team- und Produktprofilen in AEM as a Cloud Service den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren und einschränken können. 
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager UI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/cloud-manager-ui.md) - Watch this video for an overview of Cloud Manager's UI from an AEM champion. -->
