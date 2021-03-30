---
title: 'Hinzufügen von Benutzern und Zuweisen von Cloud Manager-Rollen '
description: Auf dieser Seite erfahren Sie, wie Sie Benutzer hinzufügen und sie Cloud Manager-Rollen zuweisen.
translation-type: tm+mt
source-git-commit: 6e8cf08ec3f85437a8472a45895f3818e473e98c
workflow-type: tm+mt
source-wordcount: '818'
ht-degree: 33%

---


# Hinzufügen von Benutzern und Zuweisen von Cloud Manager-Rollen {#add-users-assign}

Adobe erstellt im Adobe Identity Management System (IMS) eine **Organisationskennung** für Ihre Firma, in der alle Ihre Benutzer und ihre Berechtigungen verwaltet werden können. Jeder Benutzer, der Mitglied dieser Organisation sein muss und Zugriff auf einen der [!UICONTROL Experience Cloud]-Dienste erhält, muss über ein eigenes **Adobe ID** verfügen.

## Benutzerrollen {#user-roles}

Für viele Funktionen in Cloud Manager sind spezielle Berechtigungen erforderlich.

In Cloud Manager sind derzeit vier Rollen für Anwender definiert, die die Verfügbarkeit bestimmter Funktionen steuern:

* Business Owner
* Bereitstellungsmanager
* Programmmanager
* Entwickler

>[!NOTE]
>Die Entwicklerrolle in Admin Console ist nicht mit der Entwicklerrolle in [!UICONTROL Cloud Manager] verbunden.

In der folgenden Tabelle finden Sie eine Zusammenfassung der Rollen:

| [!UICONTROL Cloud Manager]-Rollen | Beschreibung |
|--- |--- |
| Geschäftsinhaber | Verantwortlich für die Definition von KPIs, Genehmigung von Produktionsbereitstellungen und Außerkraftsetzung bedeutender 3-Tier-Fehler. |
| Programmmanager | Verwendet [!UICONTROL Cloud Manager], um Teams einzurichten, den Status zu überprüfen und KPIs anzuzeigen. Kann bedeutende 3-Tier-Fehler genehmigen. |
| Bereitstellungsmanager | Verwaltet Bereitstellungsvorgänge. Kann mit [!UICONTROL Cloud Manager] Staging-/Produktionsbereitstellungen ausführen. Kann CI/CD Pipelines bearbeiten. Kann bedeutende 3-Tier-Fehler genehmigen. Kann Zugriff auf das Git-Repository erhalten. |
| Entwickler | Entwickelt und testet anwenderspezifischen Anwendungscode. Nutzt [!UICONTROL Cloud Manager] hauptsächlich, um den Status anzuzeigen. Kann Zugriff auf das Git-Repository für Codecommits erhalten. |
| Inhaltsautor | Interagiert im Allgemeinen nicht mit [!UICONTROL Cloud Manager]. Kann über den [!UICONTROL Cloud Manager]-Programmumschalter (nach Navigation über [!UICONTROL Experience Cloud]) auf AEM zugreifen. |

### Das Profil für das Integrationsprodukt {#integration-product-profile}

Zusätzlich zu den oben genannten Funktionen erstellt Cloud Manager automatisch ein Profil mit dem Namen &quot;Integrationen - Cloud Service&quot;. Dieses Profil wird für die Integration zwischen Adobe Experience Manager und anderen Produkten der Adobe verwendet. Dieses Profil **darf** nicht gelöscht werden. Wenn Sie dieses Profil versehentlich löschen, muss es manuell neu erstellt werden. Der Anzeigename für dieses Profil **muss** `CM_CS_DEFAULT` sein.


## Berechtigungen in Verbindung mit Rollendefinitionen {#permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das **Git-Repository** zu übertragen. Ein Business Owner verfügt wiederum über verschiedene Berechtigungen, um KPIs (Key Performance Indicators) zu definieren und Bereitstellungen zu genehmigen.

Jede der Rollen hat spezifische Berechtigungen für jede Rolle. In der folgenden Tabelle sind die Rollen, die verfügbaren Funktionen und die Rollen, die die Funktion ausführen können, zusammengefasst.

| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungsmanager | Programmmanager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| Programm hinzufügen | hinzufügen ein neues Programm. | x |  |  |  |
| Umgebung erstellen | Erstellen Sie Prod+Stage, Dev, Umgebung. | x | x |  |  |
| Umgebung aktualisieren | Aktualisieren Sie Prod+Stage, Dev, Umgebung. | x | x |  |  |
| Umgebung löschen | Löschen Sie Umgebung ohne Prod, Dev und Dev. | x | x |  |  |
| Pipeline-Einrichtung | Einrichten oder Bearbeiten der Pipeline. |  | x |  |  |
| Pipeline-Ausführung | Beginn der Pipeline. | x | x |  |  |
| Pipeline-Ausführung | Ablehnen/Genehmigen Sie wichtige 3-Stufen-Fehler. | x | x | x |  |
| Pipeline-Ausführung | Bereitstellen der GoLive-Genehmigung. | x | x | x |  |
| Pipeline-Ausführung | Planen der Bereitstellung für die Produktion. | x | x | x |  |
| Pipeline löschen | Ermöglicht das Löschen einer Pipeline. |  | x |  |  |
| Ausführung abbrechen | Aktuelle Ausführung abbrechen. |  | x |  |  |
| Persönliches Zugriffs-Token erstellen | Zugriff auf Git. |  | x |  | x |

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
