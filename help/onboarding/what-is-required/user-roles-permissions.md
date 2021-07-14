---
title: Cloud Manager-Rollen
description: Auf dieser Seite werden Anwenderrollen und -berechtigungen beschrieben. Auf dieser Seite erfahren Sie, wie Sie Anwender hinzufügen und sie Cloud Manager-Rollen zuweisen.
exl-id: d1689134-044a-4d96-97a2-cd09f735a680
source-git-commit: a0edbaf650fdfbc271a000ab4827a4c414321613
workflow-type: tm+mt
source-wordcount: '546'
ht-degree: 92%

---

# Cloud Manager-Rollen {#user-roles-permissions}

## Anwenderrollen {#user-roles}

Für viele Funktionen in Cloud Manager sind spezifische Berechtigungen erforderlich, um die Aktionen, die Sie in der Benutzeroberfläche ausführen, basierend auf den zugewiesenen Rollen und Berechtigungen zu ermöglichen. Wenn Sie nicht über die Berechtigung zum Ausführen einer Aktion verfügen, ist in einigen Fällen das Benutzeroberflächen-Steuerelement zwar vorhanden, aber deaktiviert.

Wenn Sie eine Aktion durchführen möchten, es aber nicht können, überprüfen Sie den folgenden Abschnitt: [Anwenderrollen und -berechtigungen](#permissions). Je nach Zielsetzung können Sie sich an den Systemadministrator wenden und die gewünschte Rolle anfordern.

In Cloud Manager sind derzeit vier Rollen für Anwender definiert, die die Verfügbarkeit bestimmter Funktionen steuern:

* Geschäftsinhaber
* Bereitstellungs-Manager
* Programm-Manager
* Entwickler

>[!NOTE]
>Die Entwicklerrolle in Admin Console ist nicht mit der Entwicklerrolle in [!UICONTROL Cloud Manager] verbunden.

## Anzeigen Ihrer Rollen {#view-roles}

Um Ihre Rollen in Cloud Manager anzuzeigen, melden Sie sich bei der Benutzeroberfläche von Cloud Manager an, wählen Sie Ihr Profilsymbol oben rechts und klicken Sie auf **Anwenderrollen**, wie in der folgenden Abbildung dargestellt.

>[!NOTE]
>Weitere Informationen zur Anmeldung bei Cloud Manager finden Sie unter [Navigieren zu Cloud Manager](/help/onboarding/what-is-required/navigate-to-cloud-manager.md) .

![](/help/onboarding/what-is-required/assets/admin-console-9.png)

### Das Integrations-Produktprofil {#integration-product-profile}

Zusätzlich zu den oben genannten Funktionen erstellt Cloud Manager automatisch ein Produktprofil mit dem Namen „Integrationen – Cloud Service“. Dieses Profil wird für die Integration zwischen Adobe Experience Manager und anderen Adobe-Produkten verwendet. Dieses Profil **darf nicht** gelöscht werden. Wenn Sie dieses Profil versehentlich löschen, muss es manuell neu erstellt werden. Der Anzeigename für dieses Profil **muss** `CM_CS_DEFAULT` sein.


## Anwenderrollen und -berechtigungen {#permissions}

[!UICONTROL Cloud Manager] verfügt über vorkonfigurierte Rollen mit entsprechenden Berechtigungen. Beispielsweise schreibt ein Entwickler Code und ist berechtigt, den Code per Push an das Git-Repository zu übertragen. Alternativ kann ein Geschäftsinhaber über verschiedene Berechtigungen verfügen, mit denen er Programme hinzufügen und bearbeiten, Umgebungen hinzufügen und Implemetierungen genehmigen kann.

Jeder der Rollen sind spezifische Berechtigungen zugeordnet. Beispiele für Rollen:

* ***Business Owner***: Sie sind berechtigt, ein neues Programm hinzuzufügen oder ein Programm zu bearbeiten, eine Umgebung hinzuzufügen oder zu aktualisieren und jede Pipeline auszuführen.

* ***Deployment Manager*** verfügen Sie über die Berechtigung zum Hinzufügen oder Aktualisieren einer Umgebung und zum Ausführen einer beliebigen Pipeline.

* ***Entwickler***: Sie haben die Berechtigung, ein persönliches Zugriffstoken für den Zugriff auf Git zu generieren.

   >[!NOTE]
   > Ein Anwender kann mehreren Rollen zugewiesen werden. Wenn Sie beispielsweise einem Anwender die Rollen „Geschäftsinhaber“ und „Implementierungs-Manager“ zuweisen, erhalten diese die Kombination oder Summe dieser Berechtigungen.


Die folgende Tabelle fasst die Rollen zusammen mit den zugehörigen Berechtigungen in Cloud Manager zusammen.

| Berechtigung | Beschreibung | Geschäftsinhaber | Bereitstellungs-Manager | Programm-Manager | Entwickler |
|--- |--- |--- |--- |--- |--- |
| Programm hinzufügen<br>Programm bearbeiten | Neues Programm hinzufügen.<br>Programm bearbeiten – Lösungen oder Add-ons hinzufügen oder entfernen | x |  |  |  |
| Umgebung einrichten | Kann Produktions-, Staging und Entwicklungs-Umgebungen erstellen. | x | x |  |  |
| Umgebung aktualisieren | Kann Produktions-, Staging und Entwicklungs-Umgebungen aktualisieren. | x | x |  |  |
| Entwicklungsumgebung löschen | Kann Entwicklungsumgebungen löschen. | x | x |  |  |
| Einrichten der Pipeline | Kann die Pipeline einrichten oder bearbeiten. |  | x |  |  |
| Pipeline-Ausführung | Kann die Pipeline starten. | x | x |  |  |
| Pipeline-Ausführung | Kann wichtige 3-Tier-Fehler ablehnen/akzeptieren. | x | x | x |  |
| Pipeline-Ausführung | Kann die GoLive-Genehmigung bereitstellen. | x | x | x |  |
| Pipeline-Ausführung | Kann die Bereitstellung für die Produktion planen. | x | x | x |  |
| Pipeline löschen | Kann eine Pipeline löschen. |  | x |  |  |
| Ausführung abbrechen | Kann die aktuelle Ausführung abbrechen. |  | x |  |  |
| Persönliches Zugriffs-Token erstellen | Kann auf Git zugreifen. |  | x |  | x |
