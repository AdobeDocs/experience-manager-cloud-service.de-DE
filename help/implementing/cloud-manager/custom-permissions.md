---
title: Benutzerdefinierte Berechtigungen
description: Erfahren Sie, wie Sie in Cloud Manager benutzerdefinierte Berechtigungsprofile erstellen, um den Benutzerzugriff auf bestimmte Programme, Pipelines und Umgebungen zu steuern.
exl-id: 167da985-7f19-45b3-90a3-884817907da2
solution: Experience Manager
feature: Security, Developing
role: Admin, Developer
source-git-commit: ff567c4f328bf0ab10ee9e93ad850a597536cdbf
workflow-type: tm+mt
source-wordcount: '1258'
ht-degree: 54%

---


# Benutzerdefinierte Berechtigungen {#custom-permissions}

Erfahren Sie, wie Sie in Cloud Manager maßgeschneiderte Berechtigungsprofile einrichten. Sie können spezifische Zugriffssteuerungen für Programme, Pipelines und Umgebungen konfigurieren, sodass Sie eine granulare Kontrolle darüber erhalten, was jeder Benutzer tun kann.

## Einführung {#introduction}

Cloud Manager bietet eine Reihe vordefinierter Rollen, die den Zugriff auf verschiedene Cloud Manager-Funktionen steuern:

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwicklerin oder Entwickler

Mit benutzerdefinierten Berechtigungen können Benutzende benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um den Zugriff für Cloud Manager-Benutzende auf Programme, Pipelines und Umgebungen zu beschränken.

>[!TIP]
>Weitere Informationen zu vordefinierten Rollen finden Sie unter [AEM as a Cloud Service – Team- und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md).

## Verwenden benutzerdefinierter Berechtigungen {#using}

Für das Erstellen und Verwenden eigener, benutzerdefinierter Berechtigungen sind drei Schritte erforderlich:

1. [Erstellen Sie ein Produktprofil](#create).
1. [Weisen Sie dem Produktprofil benutzerdefinierte Berechtigungen zu](#assign-permissions).
1. [Weisen Sie dem Produktprofil Benutzende zu](#assign-users).

>[!TIP]
>Lesen Sie die Abschnitte [Bedingungen](#terms) und [Konfigurierbare Berechtigungen](#configurable-permissions) , während Sie Ihre eigenen benutzerdefinierten Berechtigungen erstellen.

>[!IMPORTANT]
>Zum Erstellen von Produktprofilen und Verwalten von Berechtigungen für Cloud Manager benötigen Sie Produktadministratorrechte in der Admin Console für Adobe Experience Manager as a Cloud Service.

### Produktprofil erstellen {#create}

{{sign-in-to-cloud-manager}}

1. Klicken Sie auf der Cloud Manager-Landingpage auf **Zugriff verwalten**.

   ![Schaltfläche „Zugriff verwalten“](assets/manage-access.png)

1. Klicken Sie in der Admin Console auf **Neues Profil**.

   ![Schaltfläche „Neues Profil“](assets/admin-console-new-profile.png)

1. Geben Sie die allgemeinen Details zum Profil an.

   * **Name des Produktprofils** – Ein aussagekräftiger Name des Profils
   * **Anzeigename**: Ein abgekürzter Name, der auf der Benutzeroberfläche angezeigt wird (optional)
   * **Beschreibung**: Eine informative Beschreibung des Profils, das seinen Zweck erklärt (optional)
   * **Benutzer per E-Mail benachrichtigen**: Benutzende erhalten eine E-Mail-Benachrichtigung, wenn sie zu diesem Profil hinzugefügt oder daraus entfernt werden.

1. Klicken Sie auf **Speichern**.

Das neue Produktprofil wird gespeichert und ist in der Liste der Produktprofile in der Admin Console sichtbar.

### Zuweisen benutzerdefinierter Berechtigungen zum Produktprofil {#assign-permissions}

1. Klicken Sie in der Admin Console auf den Namen des [von Ihnen erstellten neuen Produktprofils](#create).

1. Klicken Sie auf der **Benutzerdefiniertes Profil** auf die Registerkarte **Berechtigungen**.

   ![Bearbeitbare Berechtigungen](assets/permissions-tab.png)

1. Klicken Sie in der Zeile mit dem Berechtigungsnamen auf **Bearbeiten**.

1. Führen **im Dialogfeld „Berechtigungen für benutzerdefiniertes** bearbeiten“ einen der folgenden Schritte aus:

   * Klicken Sie oben in der Spalte **Verfügbare Berechtigungselemente** auf ![Hinzufügen-Symbol oder Pluszeichen-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg) **Alle hinzufügen**, um alle Berechtigungen einzuschließen.
   * Um der Spalte **Enthaltene Berechtigungselemente“ eine einzelne Berechtigung hinzuzufügen** klicken Sie auf die zugehörige ![Symbol hinzufügen oder Pluszeichen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_AddCircle_18_N.svg).

     ![Berechtigungselemente bearbeiten](assets/edit-permission-items.png)

1. Klicken Sie auf **Speichern**.

### Zuweisen von Benutzern zum Produktprofil {#assign-users}

1. Klicken Sie in der Admin Console auf den Namen des [neuen Produktprofils, dem Sie benutzerdefinierte Berechtigungen zugewiesen haben](#assign-permissions).

1. Klicken Sie im sich öffnenden Fenster auf die Registerkarte **Benutzer**.

1. Klicken Sie **Benutzer hinzufügen** und weisen Sie dem Produktprofil Benutzer mit benutzerdefinierten Berechtigungen zu.

Unter [Verwalten von Produktprofilen für Enterprise](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html) finden Sie **Hinzufügen von Benutzern und Benutzergruppen zu einem Produktprofil** weitere Informationen zur Verwendung der Admin Console.

## Konfigurierbare Berechtigungen {#configurable-permissions}

Die folgenden Berechtigungen sind verfügbar, wenn Sie ein benutzerdefiniertes Produktprofil erstellen.

| Berechtigung | Beschreibung |
| --- | --- |
| `Program Create` | Ermöglicht es Benutzenden, ein Programm zu erstellen. |
| `Program Access` | Ermöglicht es Benutzenden, auf Programme zuzugreifen. |
| `Program Edit` | Ermöglicht es Benutzenden, Programme zu bearbeiten. |
| `Environment Create` | Ermöglicht es Benutzenden, eine Umgebung zu erstellen. |
| `Environment Edit` | Ermöglicht es Benutzenden, Umgebungen zu aktualisieren und zu bearbeiten. |
| `Environment Logs Read` | Ermöglicht es Benutzenden, Umgebungsprotokolle zu lesen. |
| `Environment Variables Manage` | Ermöglicht es Benutzenden, Umgebungskonfigurationen zu erstellen, zu bearbeiten und zu löschen. |
| `Environment Restore Create` | Ermöglicht es Benutzenden, eine Umgebungswiederherstellung zu erstellen. |
| `Rapid Development Environment Reset` | Ermöglicht es Benutzenden, die schnelle Entwicklungsumgebung (Rapid Development Environment, RDE) zurückzusetzen. |
| `Content Copy Manage` | Ermöglicht es Benutzenden, Vorgänge zum Kopieren von Inhalten zu verwalten. |
| `Pipeline Create` | Ermöglicht es Benutzenden, Pipelines zu erstellen. |
| `Pipeline Delete` | Ermöglicht es Benutzenden, Pipelines zu löschen. |
| `Pipeline Edit` | Ermöglicht es Benutzenden, Pipelines zu bearbeiten. |
| `Production Deployments Approve/Reject` | Ermöglicht es Benutzenden, einen Produktionsbereitstellungsschritt zu genehmigen oder abzulehnen. |
| `Pipeline Executions Cancel` | Ermöglicht es Benutzenden, Pipeline-Ausführungen abzubrechen. |
| `Pipeline Executions Start` | Benutzern die Möglichkeit geben, eine neue Ausführungs-Pipeline zu starten. |
| `Override/Reject Important Metric Failures` | Ermöglicht es Benutzenden, wichtige Metrikfehler zu überschreiben oder abzulehnen. |
| `Production Deployments Schedule` | Ermöglicht es Benutzenden, einen Produktionsbereitstellungsschritt zu planen. |
| `Repository Info Access` | Benutzenden erlauben, auf Repository-Informationen zuzugreifen und ein Passwort für den Zugriff zu erstellen. |
| `Repository Create` | Benutzenden erlauben, Git-Repositorys zu erstellen. |
| `Repository Delete` | Benutzenden erlauben, Git-Repositorys zu löschen. |
| `Repository Edit` | Benutzenden erlauben, Git-Repositorys zu bearbeiten. |
| `Repository Code Generate` | Benutzenden erlauben, ein Projekt aus einem Archetyp zu generieren. |
| `Domain Name Manage` | Benutzenden das Erstellen/Bearbeiten/Löschen von Domain-Namen erlauben. |
| `IP Allowlist Manage` | Benutzenden das Erstellen/Bearbeiten/Löschen von IP-Zulassungslisten und Bindungen an IP-Zulassungslisten erlauben. |
| `Network Infrastructure Manage` | Ermöglicht Benutzern das Erstellen/Löschen/Bearbeiten/Testen der Netzwerkinfrastruktur. |
| `SSL Certificate Manage` | Benutzenden das Erstellen/Bearbeiten/Löschen eines SSL-Zertifikats erlauben. |
| `New Relic Sub Account User Manage` | Benutzenden das Lesen/Bearbeiten von Benutzenden von New Relic-Unterkonten erlauben. |

### Berechtigungen auf Unternehmensebene {#organization-level}

Berechtigungen auf Organisationsebene beziehen sich auf Berechtigungen, die immer für alle Programme in einer Organisation erteilt werden.

Folgende Berechtigungen sind Berechtigungen auf Unternehmensebene:

* **`Program Create`** : Mit dieser Berechtigung können Benutzer ein Programm in der Organisation erstellen.
* **Zugriff auf Repository-**: Mit dieser Berechtigung auf Mandanten-/Organisationsebene können Benutzer einen Benutzernamen, ein Kennwort und eine Repository-URL generieren, um auf ein Kundenprojekt zuzugreifen und dazu beizutragen.
   * Benutzername und Kennwort für den Repository-Zugriff sind in allen Repositorys im Unternehmen gleich. Die Repository-URL ist jedoch für jedes Programm eindeutig.
   * Weitere Informationen finden Sie unter [Zugreifen auf Repositorys](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

## Begriffe {#terms}

Folgende Begriffe werden beim Erstellen und Verwalten benutzerdefinierter Berechtigungen und vordefinierter Rollen verwendet.

| Begriff | Beschreibung |
| --- | --- |
| Vordefinierte Berechtigungen | Vordefinierte Rollen wie **Geschäftsinhaber** und **Bereitstellungs-Manager**, um verschiedene Funktionen von Cloud Manager zu steuern. Weitere Informationen zu vordefinierten Rollen finden Sie unter [AEM as a Cloud Service – Team- und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md). |
| Benutzerdefinierte Berechtigungen | Mit Cloud Manager-Funktionen können Benutzende Berechtigungsprofile erstellen, um Rollen zur Verwaltung unterstützter Cloud Manager-Funktionen zu definieren. |
| Produktprofil | Wird in der Admin Console zur Verwaltung konfigurierbarer Berechtigungen erstellt, die für Benutzende gelten, die Teil des Berechtigungsprofils sind. |
| Konfigurierbare Berechtigung | Cloud Manager-Berechtigungen, die im Berechtigungsprofil konfiguriert werden können. |
| Berechtigungselement | Eine Programm-, Umgebungs- oder Pipeline-Ressource, auf die eine Berechtigung angewendet werden kann. |

Berechtigungselemente beziehen sich auf den Anwendungsumfang der Berechtigungen. In der Regel handelt es sich um Folgendes.

| Berechtigungselementtyp | Beispiel | Beschreibung |
| --- | --- | --- |
| Unternehmen | Unternehmen:companyA | Alle anwendbaren Ressourcen eines Unternehmens. Eine Ressource kann ein Programm, eine Umgebung oder eine Pipeline sein. Wenn Benutzende ein Unternehmen für eine Berechtigung hinzufügen, erhalten auch alle neuen Ressourcen in diesem Unternehmen diese Berechtigung. |
| Programm | Programm A | Alle anwendbaren Ressourcen eines Programms. |
| Umgebung | Programm A : Umgebung | Anwendbar für eine bestimmte Umgebung. |
| Pipeline | Programm A : Pipeline | Anwendbar für eine bestimmte Pipeline. |

## Nutzungshinweise {#usage-notes}

* Ein benutzerdefiniertes Berechtigungsprofil führt beim Konfigurieren von Berechtigungen auch AMS-Programme, -Umgebungen und -Pipelines auf.
* Für Ressourcen wie Programme, Umgebungen und Pipelines, die in Cloud Manager erstellt wurden, dauert es mehrere Minuten, bis sie in Admin Console zur Berechtigungskonfiguration angezeigt werden.
* Wenn ein benutzerdefinierter Berechtigungs-Service nicht reagiert, sind weiterhin vordefinierte Profile verfügbar und Benutzer in vordefinierten Profilen haben weiterhin angemessenen Zugriff.

## Häufig gestellte Fragen {#faq}

### Welche Berechtigungsprofile sind vordefiniert?

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwicklerin oder Entwickler

Weitere Informationen zu vordefinierten Rollen finden Sie unter [AEM as a Cloud Service – Team- und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md).

### Was passiert mit vordefinierten Berechtigungsprofilen mit der Einführung benutzerdefinierter Profile?

Standardproduktprofile und Cloud Manager-Rollen funktionieren weiterhin wie zuvor.

### Kann ich vordefinierte Berechtigungsprofile bearbeiten?

Nein. Standardprofile können nicht bearbeitet werden. Sie können keine Berechtigungen zum Standardberechtigungsprofil hinzufügen oder daraus entfernen. Sie können nur Benutzende zu vordefinierten Profilen hinzufügen oder daraus entfernen.

### Sollte ich vordefinierte Berechtigungsprofile löschen, wenn benutzerdefinierte Profile verfügbar sind?

Löschen Sie keine vordefinierten Berechtigungsprofile aus der Admin Console.

### Kann ich Benutzende zu mehreren Berechtigungsprofilen hinzufügen?

Ja. Ein Benutzer kann mehreren Profilen zugewiesen werden, einschließlich vordefinierter und benutzerdefinierter Berechtigungsprofile. Wenn eine Person mehreren Profilen zugewiesen wird, stehen ihr die kombinierten Berechtigungen aus allen zugewiesenen Berechtigungsprofilen zur Verfügung.

### Was passiert, wenn ein Benutzer berechtigt ist, eine Umgebung/Pipeline zu bearbeiten, aber keinen Zugriff auf ein Programm hat, das die Umgebung/Pipeline enthält?

Der Benutzer kann nicht auf die Umgebung oder Pipeline zugreifen, wenn er nicht über die **Programmzugriff**-Berechtigungen verfügt, die mit der Umgebung oder Pipeline verknüpft sind.
