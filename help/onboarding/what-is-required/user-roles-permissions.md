---
title: Benutzerrollen und Berechtigungen
description: Auf dieser Seite werden Benutzerrollen und Berechtigungen beschrieben. Auf dieser Seite erfahren Sie, wie Sie Benutzer hinzufügen und sie Cloud Manager-Rollen zuweisen.
translation-type: tm+mt
source-git-commit: 4b9476b094438acd08c945f0102b029b6792cb88
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 28%

---


# Benutzerrollen und Berechtigungen {#user-roles-permissions}

## Anwenderrollen {#user-roles}

Viele Funktionen in Cloud Manager erfordern spezifische Berechtigungen zum Betrieb und schränken die Aktionen ein, die Sie in der Benutzeroberfläche je nach zugewiesenen Rollen und Berechtigungen durchführen. Wenn Sie nicht berechtigt sind, eine Aktion durchzuführen, ist in einigen Fällen das Steuerelement der Benutzeroberfläche zwar vorhanden, aber deaktiviert.

Wenn Sie eine Aktion ausführen möchten, die Sie jedoch nicht ausführen können, prüfen Sie den folgenden Abschnitt: [Benutzerrollen und -berechtigungen](#permissions). Je nach Ziel können Sie sich an den Systemadministrator wenden und die gewünschte Rolle anfordern.

In Cloud Manager sind derzeit vier Rollen für Anwender definiert, die die Verfügbarkeit bestimmter Funktionen steuern:

* Business Owner
* Bereitstellungsmanager
* Programmmanager
* Entwickler

>[!NOTE]
>Die Entwicklerrolle in Admin Console ist nicht mit der Entwicklerrolle in [!UICONTROL Cloud Manager] verbunden.

## Anzeigen Ihrer Rollen {#view-roles}

Melden Sie sich zur Ansicht Ihrer Rolle in Cloud Manager bei der Benutzeroberfläche von Cloud Manager an, wählen Sie oben rechts das Profil-Symbol und dann **Benutzerrollen** aus, wie in der folgenden Abbildung dargestellt.

>[!NOTE]
>Weitere Informationen zur Anmeldung bei Cloud Manager finden Sie unter [Navigieren Sie zu Cloud Manager](/help/onboarding/what-is-required/navigate-to-cloud-manager.md).

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

### Das Profil für das Integrationsprodukt {#integration-product-profile}

Zusätzlich zu den oben genannten Funktionen erstellt Cloud Manager automatisch ein Profil mit dem Namen &quot;Integrationen - Cloud Service&quot;. Dieses Profil wird für die Integration zwischen Adobe Experience Manager und anderen Produkten der Adobe verwendet. Dieses Profil **darf** nicht gelöscht werden. Wenn Sie dieses Profil versehentlich löschen, muss es manuell neu erstellt werden. Der Anzeigename für dieses Profil **muss** `CM_CS_DEFAULT` sein.


## Benutzerrollen und Berechtigungen {#permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das **Git-Repository** zu übertragen. Alternativ dazu verfügt ein Geschäftsinhaber über andere Berechtigungen, mit denen er Programm hinzufügen und bearbeiten, Umgebung hinzufügen und Bereitstellungen genehmigen kann.

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