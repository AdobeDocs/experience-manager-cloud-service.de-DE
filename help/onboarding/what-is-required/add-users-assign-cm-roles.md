---
title: 'Systemadministrator-Aufgaben '
description: Auf dieser Seite erfahren Sie, wie Sie Benutzer hinzufügen und sie als Systemadministrator Cloud Manager-Rollen zuweisen
translation-type: tm+mt
source-git-commit: fdf8416b281b14e3dd49d1e28c3c241ddfd2d342
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 0%

---


# Systemadministrator-Aufgaben {#add-users-assign}

## Hinzufügen von Benutzern {#add-users}

>[!NOTE]
>Zum Hinzufügen eines Benutzers müssen Sie über die Administratorrechte verfügen.

1. Als Systemadministrator navigieren Sie zur Admin Console [a1/>. ](https://adminconsole.adobe.com) Alternativ können Sie auch zu Cloud Manager navigieren, wo die Schaltfläche **Zugriff verwalten** angezeigt wird, wie nachfolgend beschrieben.

1. Klicken Sie auf die Schaltfläche **Zugriff verwalten** oben rechts in der Cloud Manager-Landingpage, um die Admin Console in einer neuen Registerkarte zu öffnen.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin5.png)

   Unter **Admin Console** können Sie Benutzer zu Cloud Manager hinzufügen und sie Rollen zuweisen, die in der Admin Console als Product Profils bezeichnet werden.

1. Wählen Sie **Adobe Experience Manager als Cloud Service** aus der Karte **Produkte und Dienste** wie unten dargestellt.

   ![](/help/onboarding/what-is-required/assets/admin-console-1.png)

1. Wählen Sie in der Aktionsleiste die Registerkarte **Benutzer** und dann **Hinzufügen Benutzer**.

   ![](/help/onboarding/what-is-required/assets/admin-console-2.png)

1. Wählen Sie den Benutzer aus und weisen Sie ihm die entsprechende(n) Cloud Manager-Rolle(en) oder Produkt-Profil(e) zu, wie unten dargestellt.

   ![](/help/onboarding/what-is-required/assets/admin-console-3.png)

   >[!NOTE]
   >Lesen Sie die Abschnitte [Benutzerrollen und -berechtigungen](#user-roles) und [Berechtigungen, die mit Rollendefinitionen](#permissions) verknüpft sind, um sicherzustellen, dass den richtigen Benutzern die richtige(n) Rolle(en) in der **Admin Console** zugewiesen wird.

   Jetzt haben Sie Benutzer zu Adobe Experience Manager als Cloud Service-Produktkontext hinzugefügt und sind mit den richtigen Rollen oder Profilen eingerichtet.

   Wenn Sie z. B. die Rolle eines

   * ***Geschäftsinhaber*** haben Sie die Berechtigung, ein neues Programm zu Hinzufügen oder ein Programm zu bearbeiten, eine Umgebung hinzuzufügen oder zu aktualisieren, die Pipeline hinzuzufügen/zu bearbeiten/zu löschen, Pipeline auszuführen und Code für AEM Umgebung oder Codequalität bereitzustellen.

   * ***Deployment Manager*** verfügen Sie über die Berechtigung zum Hinzufügen oder Aktualisieren einer Umgebung, zum Ausführen einer beliebigen Pipeline und zum Bereitstellen von Code für AEM Umgebung oder Codequalität.

   * ***Entwickler*** haben Sie die Berechtigung, Personal Zugriffstoken zu generieren, um auf Git zuzugreifen.

      >[!NOTE]
      > Ein Benutzer kann mehreren Rollen zugewiesen werden. Wenn einem Benutzer beispielsweise die Rollen &quot;Geschäftsinhaber&quot;und &quot;Deployment Manager&quot;zugewiesen werden, erhalten diese Benutzer die Kombination oder Summe dieser Berechtigungen.
