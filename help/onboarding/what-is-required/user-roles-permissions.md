---
title: Cloud Manager-Rollen
description: Auf dieser Seite werden Benutzerrollen und -berechtigungen beschrieben. Auf dieser Seite erfahren Sie, wie Sie Benutzer hinzufügen und sie Cloud Manager-Rollen zuweisen.
exl-id: d1689134-044a-4d96-97a2-cd09f735a680
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 19%

---

# Cloud Manager-Rollen {#user-roles-permissions}

## Anwenderrollen {#user-roles}

Für viele Funktionen in Cloud Manager sind spezifische Berechtigungen erforderlich, um die Aktionen, die Sie in der Benutzeroberfläche ausführen, basierend auf den zugewiesenen Rollen und Berechtigungen zu ermöglichen. Wenn Sie nicht über die Berechtigung zum Ausführen einer Aktion verfügen, ist in einigen Fällen das Benutzeroberflächensteuerelement zwar vorhanden, aber deaktiviert.

Wenn Sie eine Aktion durchführen möchten, die Sie aber nicht ausführen können, überprüfen Sie den folgenden Abschnitt: [Benutzerrollen und Berechtigungen](#permissions). Je nach Ziel können Sie sich an den Systemadministrator wenden und die gewünschte Rolle anfordern.

In Cloud Manager sind derzeit vier Rollen für Anwender definiert, die die Verfügbarkeit bestimmter Funktionen steuern:

* Business Owner
* Bereitstellungsmanager
* Programmmanager
* Entwickler

>[!NOTE]
>Die Entwicklerrolle in Admin Console ist nicht mit der Entwicklerrolle in [!UICONTROL Cloud Manager] verbunden.

## Anzeigen Ihrer Rollen {#view-roles}

Um Ihre Rollen in Cloud Manager anzuzeigen, melden Sie sich bei der Benutzeroberfläche von Cloud Manager an, wählen Sie Ihr Profilsymbol oben rechts und klicken Sie auf **Benutzerrollen**, wie in der folgenden Abbildung dargestellt.

>[!NOTE]
>Weitere Informationen zur Anmeldung bei Cloud Manager finden Sie unter [Navigieren Sie zu Cloud Manager](/help/onboarding/what-is-required/navigate-to-cloud-manager.md) .

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

### Das Integrationsproduktprofil {#integration-product-profile}

Zusätzlich zu den oben stehenden Elementen erstellt Cloud Manager automatisch ein Produktprofil mit dem Namen &quot;Integrationen - Cloud Service&quot;. Dieses Produktprofil wird für Integrationen zwischen Adobe Experience Manager und anderen Adobe-Produkten verwendet. Dieses Produktprofil **darf** nicht gelöscht werden. Wenn Sie dieses Profil versehentlich löschen, muss es manuell neu erstellt werden. Der Anzeigename für dieses Profil **muss** `CM_CS_DEFAULT` sein.


## Benutzerrollen und -berechtigungen {#permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise entwickelt ein Entwickler Code und ist berechtigt, den Code an das Git-Repository zu pushen. Alternativ kann ein Business Owner über verschiedene Berechtigungen verfügen, mit denen er Programme hinzufügen und bearbeiten, Umgebungen hinzufügen und Bereitstellungen genehmigen kann.

Jeder der Rollen sind spezifische Berechtigungen zugeordnet. Wenn Sie beispielsweise die Rolle eines Benutzers haben:

* ***Business Owner***: Sie sind berechtigt, ein neues Programm hinzuzufügen oder ein Programm zu bearbeiten, eine Umgebung hinzuzufügen oder zu aktualisieren, die Pipeline hinzuzufügen, zu bearbeiten/löschen und jede Pipeline auszuführen sowie Code für AEM Umgebung oder Codequalität bereitzustellen.

* ***Deployment Manager*** verfügen Sie über die Berechtigung zum Hinzufügen oder Aktualisieren einer Umgebung, zum Ausführen einer beliebigen Pipeline und zum Bereitstellen von Code für AEM Umgebung oder Codequalität.

* ***Entwickler*** haben Sie die Berechtigung, ein persönliches Zugriffstoken für den Zugriff auf Git zu generieren.

   >[!NOTE]
   > Ein Benutzer kann mehreren Rollen zugewiesen werden. Wenn Sie beispielsweise einem Benutzer die Rollen Business Owner und Deployment Manager zuweisen, erhalten diese die Kombination oder Summe dieser Berechtigungen.


Die folgende Tabelle fasst die Rollen zusammen mit den zugehörigen Berechtigungen in Cloud Manager zusammen.

| Berechtigung | Beschreibung | Business Owner | Bereitstellungsmanager | Programmmanager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| Programm hinzufügen<br>Programm bearbeiten | Neues Programm hinzufügen.<br>Programm bearbeiten - Lösungen oder Add-ons hinzufügen oder entfernen | x |  |  |  |
| Umgebung erstellen | Erstellen Sie Prod+Stage, Entwicklung, Umgebungen. | x | x |  |  |
| Umgebung aktualisieren | Aktualisieren Sie Prod+Stage, Entwicklung, Umgebungen. | x | x |  |  |
| Entwicklungsumgebung löschen | Löschen von Entwicklungsumgebungen. | x | x |  |  |
| Pipeline-Einrichtung | Einrichten oder Bearbeiten der Pipeline. |  | x |  |  |
| Pipeline-Ausführung | Starten Sie die Pipeline. | x | x |  |  |
| Pipeline-Ausführung | Ablehnen/Genehmigen Sie wichtige 3-Tier-Fehler. | x | x | x |  |
| Pipeline-Ausführung | Bereitstellen der GoLive-Genehmigung. | x | x | x |  |
| Pipeline-Ausführung | Planen der Bereitstellung für die Produktion. | x | x | x |  |
| Pipeline löschen | Ermöglicht das Löschen einer Pipeline. |  | x |  |  |
| Ausführung abbrechen | Aktuelle Ausführung abbrechen. |  | x |  |  |
| Persönliches Zugriffs-Token erstellen | Zugriff auf Git. |  | x |  | x |
