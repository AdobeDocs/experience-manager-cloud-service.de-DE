---
title: hinzufügen Benutzer und Rollen - Erforderliche Elemente
description: hinzufügen Benutzer und Rollen - Erforderliche Elemente
translation-type: tm+mt
source-git-commit: 2c21414edd6c3178d05c818d2bf57aa152b5956b
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 63%

---


# Hinzufügen von Anwendern und Rollen {#add-users-roles}


Für viele Funktionen in [!UICONTROL Cloud Manager] sind spezielle Berechtigungen erforderlich.

In [!UICONTROL Cloud Manager] sind derzeit vier Rollen für Anwender definiert, die die Verfügbarkeit bestimmter Funktionen steuern:

* Business Owner
* Programmmanager
* Bereitstellungsmanager
* Entwickler

>[!CAUTION]
>
>Um [!UICONTROL Cloud Manager] verwenden zu können, müssen Sie über ein Adobe ID und das Adobe Experience Manager als Cloud Service-Produktkontext verfügen.

## Rollendefinitionen {#role-definitions}

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

## Das Profil für das Integrationsprodukt {#integration-product-profile}

Zusätzlich zu den oben genannten Funktionen erstellt Cloud Manager automatisch ein Profil mit dem Namen &quot;Integrationen - Cloud Service&quot;. Dieses Profil wird für die Integration zwischen Adobe Experience Manager und anderen Produkten der Adobe verwendet. Dieses Profil **darf** nicht gelöscht werden. Wenn Sie dieses Profil versehentlich löschen, muss es manuell neu erstellt werden. Der Anzeigename für dieses Profil **muss** `CM_CS_DEFAULT` sein.
