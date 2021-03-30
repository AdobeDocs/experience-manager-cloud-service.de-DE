---
title: Benutzerrollen und Berechtigungen
description: Auf dieser Seite werden Benutzerrollen und Berechtigungen beschrieben. Auf dieser Seite erfahren Sie, wie Sie Benutzer hinzufügen und sie Cloud Manager-Rollen zuweisen.
translation-type: tm+mt
source-git-commit: f09b688db23024d59f39b53766060b6f3b14e564
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 54%

---


# Benutzerrollen und Berechtigungen {#user-roles-permissions}

Adobe erstellt im Adobe Identity Management System (IMS) eine **Organisationskennung** für Ihre Firma, in der alle Ihre Benutzer und ihre Berechtigungen verwaltet werden können. Jeder Benutzer, der Mitglied dieser Organisation sein muss und Zugriff auf einen der [!UICONTROL Experience Cloud]-Dienste erhält, muss über ein eigenes **Adobe ID** verfügen.

## Anwenderrollen {#user-roles}

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