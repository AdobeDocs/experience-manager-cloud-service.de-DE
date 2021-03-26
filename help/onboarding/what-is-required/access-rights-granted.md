---
title: Zuerkannte Zugriffsrechte - Erforderlich
description: Zuerkannte Zugriffsrechte - Erforderlich
translation-type: tm+mt
source-git-commit: 8259bf4e7f2004d76fd985ec7ad7c416b6f8d491
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 50%

---


# Gewährte Zugriffsrechte {#access-rights-granted}

Adobe erstellt im Adobe Identity Management System (IMS) eine **Organisationskennung** für Ihre Firma, in der alle Ihre Benutzer und ihre Berechtigungen verwaltet werden können. Jeder Benutzer, der Mitglied dieser Organisation sein muss und Zugriff auf einen der [!UICONTROL Experience Cloud]-Dienste erhält, muss über ein eigenes **Adobe ID** verfügen.

## Anwenderidentitätstypen {#user-identity-types}

Zur Verwendung der Adobe ID rufen Sie zunächst den Artikel [Verwalten von Identitätstypen](https://helpx.adobe.com/de/enterprise/using/identity.html) auf. Dort finden Sie ausführliche Informationen zum Bezug einer Adobe ID mit einem der verfügbaren Identitätstypen.

## Anwender und Rollen {#users-and-roles}

Sobald Adobe eine Organisation für Ihr Unternehmen erstellt hat, wird Ihr Administrator als erstes Mitglied dieser Organisation hinzugefügt. Dem Administrator werden standardmäßig die Administratorberechtigungen erteilt und das [!UICONTROL AEM Managed Services]-**Produkt** sowie mindestens ein [!UICONTROL Cloud Manager] **Produktprofil** zugewiesen.

1. Sobald Ihr Systemadministrator Ihnen Zugriff auf Cloud Manager gewährt hat, erhalten Sie eine E-Mail, mit der Sie zur Anmeldeseite von Cloud Manager gelangen, auf die Sie auch über [Adobe Experience Cloud](https://my.cloudmanager.adobe.com/) zugreifen können.

1. Klicken Sie in der Landingpage des Cloud-Managers auf **Zugriff verwalten**.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin5.png)

1. Wenn Sie auf **Zugriff verwalten** klicken, navigieren Sie zu **Admin Console**, von wo Sie die Benutzerrollen oder Berechtigungen für Cloud Manager verwalten können.

   ![](/help/onboarding/getting-access-to-aem-in-cloud/assets/sys-admin1.png)

   Von der Admin Console aus können Sie SysAdmin-Aufgaben wie folgende ausführen:
   * [Rollen verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#manage-roles)
   * [Zugriff auf Autorinstanz verwalten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/getting-access/navigation.html?lang=en#manage-access-aem)

      >[!NOTE]
      >Weitere Informationen zu Benutzern und Rollendefinitionen in Cloud Manager finden Sie im Abschnitt [Benutzer und Rollen](#users-roles).

Mit diesen Rechten kann Ihr Administrator nun per Single Sign-on (mit der Adobe ID) auf [!UICONTROL Experience Cloud]-Dienste zugreifen, sich bei Ihren AEM-Cloud-Umgebungen anmelden und [!UICONTROL Cloud Manager] verwenden.

Für viele Funktionen in [!UICONTROL Cloud Manager] sind spezielle Berechtigungen erforderlich.

In [!UICONTROL Cloud Manager] sind derzeit vier Rollen für Anwender definiert, die die Verfügbarkeit bestimmter Funktionen steuern:

* Business Owner
* Programmmanager
* Bereitstellungsmanager
* Entwickler

>[!CAUTION]
>Um [!UICONTROL Cloud Manager] verwenden zu können, müssen Sie über ein Adobe ID und das Adobe Experience Manager als Cloud Service-Produktkontext verfügen.

### Rollendefinitionen {#role-definitions}

>[!NOTE]
>
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

