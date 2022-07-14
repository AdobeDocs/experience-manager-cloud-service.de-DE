---
title: Zugreifen auf Cloud Manager
description: Erfahren Sie, wie Sie auf Cloud Manager zugreifen können, damit Sie Ihre Projektressourcen einrichten können.
role: Admin, User, Developer
source-git-commit: 709a80683357b0d56280ff14aa5f4ba6bf2c6b23
workflow-type: tm+mt
source-wordcount: '1025'
ht-degree: 41%

---


# Zugreifen auf Cloud Manager {#cloud-resources}

In diesem Teil des [Onboarding-Journey,](overview.md) Hier erfahren Sie, wie Sie auf Cloud Manager zugreifen können, um Ihre Projektressourcen einzurichten.

## Ziel {#objective}

Im vorherigen Artikel in dieser Onboarding-Journey, [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen,](assign-profiles-cloud-manager.md) Sie Ihrem AEMaaCS-Team die richtigen Rollen zugewiesen haben. Erfahren Sie jetzt, wie Sie auf Cloud Manager zugreifen können, damit Sie Ihre Projektressourcen einrichten können, die Ihr Team verwenden wird.

Da Sie den vorherigen Schritt in dieser Journey abgeschlossen haben, kann Ihr Team auf Cloud Manager zugreifen. Cloud Manager wird zum Erstellen und Verwalten von Projektressourcen wie Programmen und Umgebungen verwendet.

Nach dem Lesen dieses Dokuments sollten Sie Folgendes verstehen:

* Dieser Systemadministrator hat der **Business Owner** Die Rolle muss die erste Rolle in Ihrem Unternehmen sein, die sich anmeldet und auf Cloud Manager zugreift.
* Anmeldung bei Cloud Manager.

## Cloud Manager {#cloud-manager}

Cloud Manager ist eine wesentliche Komponente von AEM as a Cloud Service und dient als zentraler Einstiegspunkt für Ihr Team. Es unterstützt Kunden mit Enterprise-Entwicklungs-Setups mit den speziell dafür vorgesehenen CI/CD-Pipelines, die für gründliche Tests und höchste Code-Qualität ausgelegt sind, um außergewöhnliche Erlebnisse bereitzustellen. Cloud Manager bietet alles, was für die ersten Schritte auf Self-Service-Weise erforderlich ist, einschließlich der Möglichkeit, Cloud-Ressourcen und -Umgebungen zu erstellen.

Normalerweise ist ein Team-Mitglied, das dem **Business Owner** Das Produktprofil ist für das Hinzufügen Ihrer Cloud-Ressourcen, wie Programme und Umgebungen, verantwortlich. Diese Person versteht die Geschäftsanforderungen und die Ersteinrichtung von Cloud Manager.

Im Rahmen dieser Onboarding-Journey haben Sie sich als Systemadministrator bereits dem **Business Owner** Produktprofil erstellen und die Cloud-Ressourcen einrichten. Abhängig von den tatsächlichen Projektanforderungen können die Geschäftsinhaber mit dem Systemadministrator identisch sein.

## Zugriff auf Cloud Manager als Systemadministrator und Geschäftsinhaber {#access-sysadmin-bo}

Vor den Teammitgliedern, die Sie der **Business Owner** Rolle kann auf Cloud Manager zugreifen und mit der Erstellung von Cloud-Ressourcen beginnen. Dem Systemadministrator muss die **Business Owner** Rolle und melden Sie sich bei Cloud Manager an, wie Sie es im vorherigen Schritt in dieser Onboarding-Journey getan haben.

1. Stellen Sie sicher, dass Sie als Systemadministrator über die **Business Owner** zugewiesene Rolle.

   * Kehren Sie zum vorherigen Schritt in dieser Journey zurück, [Zuweisen von Team-Mitgliedern zu Cloud Manager-Produktprofilen,](assign-profiles-cloud-manager.md) Weitere Informationen zur Zuweisung der **Business Owner** Rolle für den Systemadministrator hinzufügen, falls Sie dies noch nicht getan haben.

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und lassen Sie sich die normale Landingpage anzeigen.

Durch erfolgreiche Anmeldung als Systemadministrator bei der **Business Owner** Rolle, initialisieren Sie Cloud Manager zur Verwendung durch die anderen Benutzer mit der **Business Owner** Rolle. Sie erhalten keine Bestätigung mit dieser oder irgendeiner Nachricht. Die Anmeldung genügt einfach.

Bis Sie sich bei Cloud Manager als Systemadministrator bei der **Business Owner** Rolle, anderen Benutzern mit dem **Business Owner** -Rolle kann keine Programme in Cloud Manager erstellen, selbst wenn ihnen die richtigen Rollen zugewiesen sind.

## Navigieren zu Cloud Manager {#navigate-cloud-manager}

Benutzer mit **Business Owner** -Rolle erhält eine Begrüßungs-E-Mail mit einem Link zu den ersten Schritten. Gehen Sie wie folgt vor, um mithilfe dieser Begrüßungs-E-Mail zu Cloud Manager zu gelangen.

1. Klicken Sie in Ihrer Begrüßungs-E-Mail auf **Erste Schritte**, wie in der folgenden Abbildung dargestellt.
   ![E-Mail-Beispiel](/help/journey-onboarding/assets/get-started-email.png)

1. Gehen Sie zur Seite **Programme und Produkte** von Cloud Manager.

   >[!TIP]
   >
   >Alternativ können Sie auch direkt von `[my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)` zur Anmeldeseite von Cloud Manager gelangen. Bitte setzen Sie für diese Seite für künftige Referenzzwecke ein Lesezeichen.

1. Sie werden zur Landingpage von Cloud Manager weitergeleitet.

Alternativ können Sie auch zum **Programme und Produkte** von der Adobe Experience Cloud-Startseite aus, indem Sie die folgenden Schritte ausführen

1. Gehen Sie direkt zu [Adobe Experience Cloud](https://experience.adobe.com) und melden Sie sich mit Ihrer Adobe ID an.

1. Wählen Sie auf der Adobe Experience Cloud-Startseite **Experience Manager** aus.

   ![Experience Cloud-Startseite](/help/journey-onboarding/assets/setup-resources2.png)

1. Dadurch gelangen Sie zur AEM-Startseite. Klicken Sie hier auf der Kachel **Cloud Manager** auf **Starten**.

   ![AEM-Startseite](/help/journey-onboarding/assets/setup-resources3.png)

1. Nach erfolgreicher Anmeldung werden Sie zur Landingpage von Cloud Manager weitergeleitet. Weitere Informationen finden Sie im Abschnitt [Anzeigen der Cloud Manager-Programme](#viewing-programs).

Der Zugriff auf Ihre Programme und Produkte über Cloud Manager liegt bei Ihnen und hat keine Auswirkungen auf die Verwendung von Cloud Manager oder die Verwaltung Ihrer Programme.

>[!NOTE]
>
>Je nach den in Cloud Manager zugewiesenen Rollen und dem Status der Anwendung werden bei der Verwendung der Cloud Manager-Benutzeroberfläche unterschiedliche Bildschirme angezeigt.

## Anzeigen von Programmen {#viewing-programs}

Sobald Sie erfolgreich auf den Cloud Manager zugreifen, hängt das, was Sie sehen, vom Status Ihrer Programme ab, wie in den folgenden Abschnitten beschrieben.

### Wenn es keine Programme gibt {#no-programs}

Wenn in Ihrer Organisation keine Programme vorhanden sind, werden Sie von Ihrer Landingpage angewiesen, Ihr erstes Programm zu erstellen.

![Keine Programme](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin0.png)

### Wenn es bereits Programme gibt {#programs-exist}

Wenn in Ihrer Organisation bereits Programme vorhanden sind, zeigt Ihre Landingpage Ihre vorhandenen Programme an und bietet außerdem eine Schaltfläche zum Hinzufügen zusätzlicher Programme.

![Programme sind vorhanden](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/first_timelogin1.png)

### Wenn ein Programm vorhanden ist und Sie ein Systemadministrator sind {#programs-exist-sysadmin}

Wenn in Ihrer Organisation bereits Programme vorhanden sind und Sie Systemadministrator sind, wird Ihre Landingpage angezeigt **Zugriff verwalten** -Schaltfläche zusammen mit **Programm hinzufügen** -Option.

![Systemadministratoransicht](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/assets/admin-console-4.png)

## Überprüfen der Benutzerrollen {#verify-user-roles}

Nachdem Sie sich erfolgreich bei Cloud Manager angemeldet haben, können Sie verifizieren, dass Ihnen das Produktprofil **Geschäftsinhaber** zugewiesen wurde.

1. Wählen Sie Ihr Profil oben rechts im Fenster aus.

   ![Benutzerprofil](/help/journey-onboarding/assets/setup-resources5.png)

1. Wählen Sie **Benutzerrollen** aus, um die Ihrem Benutzer zugewiesenen Rollen anzuzeigen.

   ![Benutzerrollen](/help/journey-onboarding/assets/setup-resources6.png)

1. Im Dialogfeld sollte bestätigt werden, dass Ihr Benutzer über die **Business Owner** Rolle.

   ![Liste der Benutzerrollen](/help/journey-onboarding/assets/setup-resources7.png)

Sie haben sich erfolgreich als Geschäftsinhaber bei Cloud Manager angemeldet! Wenn Ihnen die Rolle des **Geschäftsinhabers** nicht zugewiesen wurde, wenden Sie sich an Ihren Systemadministrator.

## Wie geht es weiter? {#whats-next}

Jetzt, da Sie als Systemadministrator auf Cloud Manager zugreifen können, können Sie Ihr erstes Programm erstellen.

Sie sollten Ihre Onboarding-Journey fortsetzen, indem Sie das Dokument zum nächsten Mal lesen. [Programm erstellen](create-program.md) wo Sie erfahren, wie Sie das machen.

## Zusätzliche Ressourcen {#additional-resources}

Folgen Sie den zusätzlichen Ressourcen, um mehr über Folgendes zu erfahren:

* [Einführung in Cloud Manager](/help/onboarding/cloud-manager-introduction.md) - Erfahren Sie mehr über Cloud Manager-, Cloud Manager-Programme und -Umgebungen.
