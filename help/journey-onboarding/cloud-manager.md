---
title: Zugreifen auf Cloud Manager
description: Erfahren Sie, wie Sie auf Cloud Manager zugreifen können, damit Sie Ihre Projektressourcen einrichten können.
role: Admin, User, Developer
exl-id: c9476ac9-8318-493e-a48d-94ff5a6433a7
source-git-commit: 5c9dbaa25f0142afdae8b09dc18d1e1aaaf4c1fb
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 52%

---

# Zugreifen auf Cloud Manager {#cloud-resources}

In diesem Teil des [Onboarding-Journey,](overview.md) Hier erfahren Sie, wie Sie auf Cloud Manager zugreifen können, um Ihre Projektressourcen einzurichten.

## Ziel {#objective}

Im vorherigen Artikel dieser Onboarding-Tour, [Zuweisung von Team-Mitgliedern zu Cloud Manager-Produktprofilen](assign-profiles-cloud-manager.md), haben Sie Ihrem AEMaaCS-Team die jeweiligen Rollen zugewiesen. Erfahren Sie jetzt, wie Sie auf Cloud Manager zugreifen können, damit Sie Ihre Projektressourcen einrichten können, die Ihr Team verwendet.

Seit Sie den vorherigen Schritt in dieser Tour abgeschlossen haben, kann Ihr Team auf Cloud Manager zugreifen. Cloud Manager wird zum Erstellen und Verwalten von Projektressourcen, wie z. B, Programmen und Umgebungen, verwendet.

Nach dem Lesen dieses Dokuments sollten Sie Folgendes verstehen:

* Dieser Systemadministrator hat der **Business Owner** -Rolle muss die erste Rolle in Ihrem Unternehmen sein, die sich anmeldet und auf Cloud Manager zugreift.
* Wie Sie sich bei Cloud Manager anmelden.

## Cloud Manager {#cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM as a Cloud Service und dient als zentraler Einstiegspunkt für Ihr Team. Cloud Manager unterstützt Kunden und Kundinnen bei ihren Entwicklungsprojekten mit speziell dafür konzipierten CI/CD-Pipelines, die für umfassende Tests und höchste Code-Qualität zur Bereitstellung außergewöhnlicher Erlebnisse ausgelegt sind. Cloud Manager bietet alles, was für den Einstieg erforderlich ist, als Self-Service-Funktionalität, einschließlich der Möglichkeit, Ihre Cloud-Ressourcen und -Umgebungen selbst zu erstellen.

Normalerweise ist ein Team-Mitglied mit dem Produktprofil **Geschäftsinhaber** für das Hinzufügen Ihrer Cloud-Ressourcen, wie Programme und Umgebungen, verantwortlich. Diese Person versteht die Geschäftsanforderungen und führt die Ersteinrichtung von Cloud Manager durch.

Im Rahmen dieser Onboarding-Journey haben Sie sich als Systemadministrator bereits dem **Business Owner** Produktprofil erstellen und die Cloud-Ressourcen einrichten. Je nach den tatsächlichen Projektanforderungen können die Geschäftsinhaber mit dem Systemadministrator identisch sein oder nicht.

## Zugriff auf Cloud Manager als System-Admin und Geschäftsinhaber {#access-sysadmin-bo}

Vor den Teammitgliedern, die Sie der **Business Owner** Rolle kann auf Cloud Manager zugreifen und mit der Erstellung von Cloud-Ressourcen beginnen. Dem Systemadministrator muss die **Business Owner** Rolle. Sie müssen sich auch bei Cloud Manager anmelden, wie Sie es im vorherigen Schritt in dieser Onboarding-Journey getan haben.

1. Stellen Sie sicher, dass Ihnen als System-Admin die Rolle als **Geschäftsinhaber** zugewiesen wurde.

   * Kehren Sie zum vorherigen Schritt in dieser Journey zurück, [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen,](assign-profiles-cloud-manager.md) Weitere Informationen zur Zuweisung der **Business Owner** Rolle für den Systemadministrator.

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an. Daraufhin wird die Landingpage angezeigt.

Durch die erfolgreiche Anmeldung als System-Admin mit der Rolle **Geschäftsinhaber** initialisieren Sie Cloud Manager für die Verwendung durch andere, die ebenfalls die Rolle **Geschäftsinhaber** haben. Sie erhalten keine Bestätigung oder Nachricht. Die einfache Anmeldung ist ausreichend.

Bis Sie sich bei Cloud Manager als Systemadministrator bei der **Business Owner** Rolle, anderen Benutzern mit dem **Business Owner** Rolle kann keine Programme in Cloud Manager erstellen. Diese Regel gilt auch dann, wenn ihnen die richtigen Rollen zugewiesen sind.

## Navigieren zu Cloud Manager {#navigate-cloud-manager}

Benutzer mit **Business Owner** -Rolle eine Begrüßungs-E-Mail mit einem Link zum Einstieg erhalten. Gehen Sie wie folgt vor, um mithilfe dieser Begrüßungs-E-Mail zu Cloud Manager zu gelangen.

1. Klicken Sie in Ihrer Begrüßungs-E-Mail auf **Erste Schritte**, wie in der folgenden Abbildung dargestellt.
   ![E-Mail-Beispiel](/help/journey-onboarding/assets/get-started-email.png)

1. Navigieren Sie zum Cloud Manager- **Programme und Produkte** Seite.

   >[!TIP]
   >
   >Alternativ können Sie auch direkt von `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)` zur Anmeldeseite von Cloud Manager gelangen. Markieren Sie diese Seite als Referenz für die Zukunft.

1. Sie werden zur Landingpage von Cloud Manager weitergeleitet.

Alternativ können Sie auch von der Adobe Experience Cloud-Startseite zur Seite **Programme und Produkte** in Cloud Manager navigieren, indem Sie die folgenden Schritte ausführen.

1. Gehen Sie direkt zu [Adobe Experience Cloud](https://experience.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie auf der Adobe Experience Cloud-Startseite die Option **Experience Manager** , um die AEM Homepage zu öffnen.

   ![Experience Cloud-Startseite](/help/journey-onboarding/assets/setup-resources2.png)

1. Im **Cloud Manager** Kachel, auswählen **Launch**.

   ![AEM-Startseite](/help/journey-onboarding/assets/setup-resources3.png)

1. Nach erfolgreicher Anmeldung gelangen Sie zur Landingpage von Cloud Manager. Siehe [Anzeigen der Cloud Manager-Programme](#viewing-programs) für weitere Details.

Der Zugriff auf Ihre Programme und Produkte über Cloud Manager liegt bei Ihnen und hat keine Auswirkungen auf die Verwendung von Cloud Manager oder die Verwaltung Ihrer Programme.

>[!NOTE]
>
>Je nach den in Cloud Manager zugewiesenen Rollen und dem Status der Anwendung werden bei der Verwendung der Cloud Manager-Benutzeroberfläche unterschiedliche Bildschirme angezeigt.

## Anzeigen von Programmen {#viewing-programs}

Nach dem erfolgreichen Zugriff auf Cloud Manager hängt der Status Ihrer Programme ab, wie in den folgenden Abschnitten beschrieben.

### Wenn es keine Programme gibt {#no-programs}

Wenn in Ihrer Organisation keine Programme vorhanden sind, werden Sie von Ihrer Landingpage angewiesen, Ihr erstes Programm zu erstellen.

![Keine Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

### Wenn es bereits Programme gibt {#programs-exist}

Wenn in Ihrer Organisation Programme vorhanden sind, zeigt Ihre Landingpage Ihre vorhandenen Programme an und bietet außerdem eine Schaltfläche zum Hinzufügen zusätzlicher Programme.

![Programme sind vorhanden](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

### Wenn ein Programm vorhanden ist und Sie ein Systemadministrator sind {#programs-exist-sysadmin}

Wenn in Ihrer Organisation Programme vorhanden sind und Sie Systemadministrator sind, wird Ihre Landingpage angezeigt **Zugriff verwalten** -Schaltfläche zusammen mit **Programm hinzufügen** -Option.

![Systemadministratoransicht](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

## Überprüfen der Benutzerrollen {#verify-user-roles}

Nachdem Sie sich erfolgreich bei Cloud Manager angemeldet haben, können Sie verifizieren, dass Ihnen das Produktprofil **Geschäftsinhaber** zugewiesen wurde.

1. Wählen Sie Ihr Profil oben rechts im Fenster aus.

   ![Benutzerprofil](/help/journey-onboarding/assets/setup-resources5.png)

1. Um die Ihrem Benutzer zugewiesenen Rollen anzuzeigen, wählen Sie **Benutzerrollen**.

   ![Benutzerrollen](/help/journey-onboarding/assets/setup-resources6.png)

1. Im Dialogfeld sollte bestätigt werden, dass die jeweilige Person über die Rolle **Geschäftsinhaber** verfügt.

   ![Liste der Benutzerrollen](/help/journey-onboarding/assets/setup-resources7.png)

Sie haben sich erfolgreich als Geschäftsinhaber bei Cloud Manager angemeldet! Wenn Ihnen die Rolle des **Geschäftsinhabers** nicht zugewiesen wurde, wenden Sie sich an Ihren Systemadministrator.

## Wie geht es weiter {#whats-next}

Jetzt, da Sie als System-Admin auf Cloud Manager zugreifen können, können Sie Ihr erstes Programm erstellen.

Fahren Sie mit dem Onboarding-Journey fort, indem Sie das Dokument zum nächsten Mal lesen. [Programm erstellen](create-program.md) wo Sie erfahren, wie Sie dies tun.

## Zusätzliche Ressourcen {#additional-resources}

Im Folgenden finden Sie zusätzliche optionale Ressourcen, wenn Sie über den Inhalt des Onboarding-Journey hinausgehen möchten.

* [Einführung in Cloud Manager](/help/onboarding/cloud-manager-introduction.md) – 
Erfahren Sie mehr über Cloud Manager sowie Cloud Manager-Programme und -Umgebungen.
* [Team- und Produktprofile in AEM as a Cloud Service](/help/onboarding/aem-cs-team-product-profiles.md) – Erfahren Sie, wie Sie mit Team- und Produktprofilen in AEM as a Cloud Service den Zugriff auf Ihre lizenzierten Adobe-Lösungen gewähren und einschränken können. 
<!-- ERROR: Not Found (HTTP error 404) * [AEM Champion Tips and Tricks - Cloud Manager UI](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/expert-resources/aem-champions/cloud-manager-ui.md) - Watch this video for an overview of Cloud Manager's UI from an AEM champion. -->
