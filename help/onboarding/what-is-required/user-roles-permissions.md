---
title: Cloud Manager-Rollen
description: Auf dieser Seite werden Benutzerrollen und Berechtigungen beschrieben. Auf dieser Seite erfahren Sie, wie Sie Benutzer hinzufügen und sie Cloud Manager-Rollen zuweisen.
translation-type: tm+mt
source-git-commit: f518cab23b1dadceee5800b3454f74d341e941c4
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 19%

---


# Cloud Manager-Rollen {#user-roles-permissions}

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

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Ein Entwickler entwickelt beispielsweise Code und hat die Berechtigung, den Code an das Git-Repository zu senden. Alternativ dazu verfügt ein Geschäftsinhaber über andere Berechtigungen, mit denen er Programm hinzufügen und bearbeiten, Umgebung hinzufügen und Bereitstellungen genehmigen kann.

Jeder der Rollen sind spezifische Berechtigungen zugeordnet. Wenn Sie z. B. die Rolle eines

* ***Geschäftsinhaber*** haben Sie die Berechtigung, ein neues Programm zu Hinzufügen oder ein Programm zu bearbeiten, eine Umgebung hinzuzufügen oder zu aktualisieren, die Pipeline hinzuzufügen/zu bearbeiten/zu löschen, Pipeline auszuführen und Code für AEM Umgebung oder Codequalität bereitzustellen.

* ***Deployment Manager*** verfügen Sie über die Berechtigung zum Hinzufügen oder Aktualisieren einer Umgebung, zum Ausführen einer beliebigen Pipeline und zum Bereitstellen von Code für AEM Umgebung oder Codequalität.

* ***Entwickler*** haben Sie die Berechtigung, Personal Zugriffstoken zu generieren, um auf Git zuzugreifen.

   >[!NOTE]
   > Ein Benutzer kann mehreren Rollen zugewiesen werden. Wenn einem Benutzer beispielsweise die Rollen &quot;Geschäftsinhaber&quot;und &quot;Deployment Manager&quot;zugewiesen werden, erhalten diese Benutzer die Kombination oder Summe dieser Berechtigungen.


Die folgende Tabelle fasst die Rollen zusammen mit den zugehörigen Berechtigungen in Cloud Manager zusammen.

| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungsmanager | Programmmanager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| hinzufügen Programm<br>Programm bearbeiten | hinzufügen ein neues Programm.<br>Bearbeiten eines Programms - Hinzufügen oder Entfernen von Lösungen oder Add-ons | x |  |  |  |
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

