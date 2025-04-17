---
title: Benutzerdefinierte Berechtigungen
description: Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzende zu beschränken.
exl-id: 167da985-7f19-45b3-90a3-884817907da2
solution: Experience Manager
feature: Security, Developing
role: Admin, Architect, Developer
source-git-commit: 0712ba8918696f4300089be24cad3e4125416c02
workflow-type: tm+mt
source-wordcount: '1492'
ht-degree: 73%

---


# Benutzerdefinierte Berechtigungen {#custom-permissions}

Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzende zu beschränken.

## Einführung {#introduction}

Cloud Manager verfügt über eine Reihe vordefinierter Rollen, die den Zugriff auf verschiedene Cloud Manager-Funktionen steuern:

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwicklerin oder Entwickler

Mit benutzerdefinierten Berechtigungen können Benutzende neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um den Zugriff auf Programme, Pipelines und Umgebungen für Benutzerinnen und Benutzer von Cloud Manager zu beschränken.

>[!TIP]
>
>Weitere Informationen zu vordefinierten Rollen finden Sie unter [AEM as a Cloud Service – Team- und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md).

## Verwenden benutzerdefinierter Berechtigungen {#using}

Um eigene, benutzerdefinierte Berechtigungen zu erstellen und zu verwenden, sind drei Schritte erforderlich:

1. [Erstellen Sie ein Produktprofil](#create).
1. [Weisen Sie dem Produktprofil benutzerdefinierte Berechtigungen zu](#assign-permissions).
1. [Weisen Sie dem Produktprofil Benutzende zu](#assign-users).

In diesem Abschnitt werden diese Schritte beschrieben. Möglicherweise helfen Ihnen die Informationen in den Abschnitten [Begriffe](#terms) und [Konfigurierbare Berechtigungen](#configurable-permissions) bei der Erstellung Ihrer eigenen benutzerdefinierten Berechtigungen.

>[!NOTE]
>
>Sie müssen in der Admin Console für Adobe Experience Manager as a Cloud Service über Produktadministratorrechte verfügen, um Profile zu erstellen und Berechtigungen für Cloud Manager zu verwalten.

### Erstellen eines neuen Produktprofils {#create}

Erstellen Sie zunächst ein Produktprofil, dem Sie benutzerdefinierte Berechtigungen zuweisen können.

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an.

1. Wählen Sie auf der Landingpage von Cloud Manager die Schaltfläche **Zugriff verwalten** aus.

![Schaltfläche „Zugriff verwalten“](assets/manage-access.png)

1. Sie werden zur Registerkarte **Produkte** der Admin Console geleitet, auf der Sie Benutzende und Berechtigungen für Cloud Manager verwalten können. Wählen Sie in der Admin Console die Schaltfläche **Neues Profil** aus.

![Schaltfläche „Neues Profil“](assets/admin-console-new-profile.png)

1. Geben Sie die allgemeinen Details zum Profil an.

   * **Name des Produktprofils** – Ein aussagekräftiger Name des Profils
   * **Anzeigename**: Ein abgekürzter Name, der auf der Benutzeroberfläche angezeigt wird (optional)
   * **Beschreibung**: Eine informative Beschreibung des Profils, das seinen Zweck erklärt (optional)
   * **Benutzer per E-Mail benachrichtigen** - Benutzer erhalten eine E-Mail-Benachrichtigung, wenn sie zu diesem Profil hinzugefügt oder daraus entfernt werden.

1. Wählen Sie **Speichern** aus, wenn Sie fertig sind.

Das neue Produktprofil wird gespeichert und ist in der Liste der Produktprofile in der Admin Console sichtbar.

### Zuweisen benutzerdefinierter Berechtigungen zum Profil {#assign-permissions}

Nachdem Sie ein neues Produktprofil erstellt haben, können Sie ihm benutzerdefinierte Berechtigungen zuweisen.

1. Wählen Sie in der Admin Console den Namen des [neuen Produktprofils aus, das Sie erstellt haben](#create).

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Berechtigungen**, um eine Liste bearbeitbarer Berechtigungen anzuzeigen.

   ![Bearbeitbare Berechtigungen](assets/permissions-tab.png)

1. Wählen Sie den Link **Bearbeiten** einer Berechtigung aus, damit Sie sie bearbeiten können.

1. Das Fenster **Berechtigung bearbeiten** wird geöffnet.
   * Die Berechtigung, die Sie im vorherigen Schritt ausgewählt haben, ist in der linken Spalte ausgewählt.
   * Die für die Zuweisung der Berechtigung verfügbaren Berechtigungselemente befinden sich in der mittleren Spalte **Verfügbare Berechtigungselemente**.
   * Die zugewiesenen Berechtigungselemente befinden sich in der rechten Spalte mit der Bezeichnung **Eingeschlossene Berechtigungselemente**.

   ![Berechtigungselemente bearbeiten](assets/edit-permission-items.png)

1. Wählen Sie das Pluszeichen (`+`) neben dem Berechtigungselement, um dieses zur Spalte **Eingeschlossene Berechtigungselemente** hinzuzufügen.

   * Wählen Sie das Symbol `i` neben einem Berechtigungselement aus, wenn Sie mehr darüber erfahren möchten.

1. Wählen Sie die Schaltfläche **Alle hinzufügen** oben in der Spalte **Verfügbare Berechtigungen** aus, damit Sie alle Berechtigungen hinzufügen können.

1. Wählen Sie **Speichern** aus, wenn Sie die Berechtigungselemente für Ihr neues Produktprofil definiert haben.

Ihr neues Produktprofil wird jetzt mit den benutzerdefinierten Berechtigungen gespeichert.

### Zuweisen von Benutzenden zu den benutzerdefinierten Berechtigungen {#assign-users}

Sie können dem neuen Produktprofil, das Sie mit benutzerdefinierten Berechtigungen erstellt haben, jetzt Benutzende zuweisen.

1. Wählen Sie in der Admin Console den Namen des [neuen Produktprofils aus, dem benutzerdefinierte Berechtigungen zugewiesen wurden](#assign-permissions).

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Benutzer**.

1. Wählen Sie die Schaltfläche **Benutzer hinzufügen** aus und weisen Sie Ihrem neuen Produktprofil Benutzende mit benutzerdefinierten Berechtigungen zu.

Weitere Informationen zum Arbeiten mit der Admin Console finden Sie im Abschnitt **Hinzufügen von Benutzenden und Benutzergruppen zu einem Produktprofil** des Dokuments [Verwalten von Produktprofilen für Unternehmensbenutzende](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html).

## Konfigurierbare Berechtigungen {#configurable-permissions}

Zum Erstellen benutzerdefinierter Profile stehen folgende Berechtigungen zur Verfügung.

| Berechtigung | Beschreibung |
| --- | --- |
| Programm erstellen | Benutzern die Erstellung eines Programms ermöglichen. |
| Programmzugriff | Benutzern den Zugriff auf Programme ermöglichen. |
| Programmbearbeitung | Benutzer können Programme bearbeiten. |
| Umgebung erstellen | Benutzern die Erstellung einer Umgebung ermöglichen. |
| Umgebung bearbeiten | Benutzern die Aktualisierung und Bearbeitung von Umgebungen ermöglichen. |
| Umgebungsprotokolle lesen | Benutzern das Lesen der Umgebungsprotokolle ermöglichen. |
| Umgebungsvariablen verwalten | Ermöglicht Benutzenden das Erstellen/Bearbeiten/Löschen von Umgebungskonfigurationen. |
| Umgebungswiederherstellung erstellen | Ermöglicht Benutzenden das Erstellen einer Wiederherstellungsumgebung. |
| Schnelles Zurücksetzen der Entwicklungsumgebung | Zurücksetzen der schnellen Entwicklungsumgebung (RDE) durch Benutzende. |
| Inhaltskopie verwalten | Benutzern die Verwaltung von Inhaltskopievorgängen ermöglichen. |
| Pipeline erstellen | Benutzer können Pipelines erstellen. |
| Pipeline löschen | Benutzer können Pipelines löschen. |
| Pipeline-Bearbeitung | Benutzer können Pipelines bearbeiten. |
| Genehmigung/Ablehnung von Produktionsbereitstellungen | Benutzerinnen und Benutzer können einen Produktionsbereitstellungsschritt genehmigen oder ablehnen. |
| Pipeline-Ausführungen abbrechen | Pipeline-Ausführungen durch Benutzer abbrechen lassen. |
| Pipeline-Ausführungen starten | Benutzer können eine neue Pipeline-Ausführung starten. |
| Wichtige Metrikfehler überschreiben/ablehnen | Benutzern die Möglichkeit geben, wichtige Metrikfehler zu überschreiben/abzulehnen. |
| Produktionsbereitstellungs-Zeitplan | Ermöglicht Benutzenden, einen Produktionsbereitstellungsschritt zu planen. |
| Zugriff auf Repository-Informationen | Ermöglicht Benutzenden den Zugriff auf Repository-Informationen und die Erstellung eines Zugriffspassworts. |
| Repository erstellen | Ermöglichen Sie Benutzern das Erstellen von Git-Repositorys. |
| Repository löschen | Benutzer können Git-Repositorys löschen. |
| Repository bearbeiten | Benutzer können Git-Repositorys bearbeiten. |
| Repository-Code-Generierung | Benutzerinnen und Benutzern die Erstellung eines Projekts aus dem Archetyp ermöglichen. |
| Domain-Namen verwalten | Ermöglicht Benutzern das Erstellen/Bearbeiten/Löschen von Domain-Namen. |
| IP-Zulassungslisten verwalten | Benutzerinnen und Benutzer können IP-Zulassungsliste auf die Zulassungsliste setzten und IP-Dateibindungen erstellen/bearbeiten/löschen. |
| Netzwerkinfrastruktur verwalten | Ermöglicht Benutzern das Erstellen/Bearbeiten/Löschen der Netzwerkinfrastruktur. |
| SSL-Zertifikat verwalten | Benutzer können SSL-Zertifikate erstellen/bearbeiten/löschen. |
| Benutzende von New Relic-Unterkonten verwalten | Benutzerinnen und Benutzern das Lesen/Bearbeiten von New Relic-Unterkontenbenutzenden ermöglichen. |

### Berechtigungen auf Unternehmensebene {#organization-level}

Berechtigungen auf Unternehmensebene beziehen sich auf Berechtigungen, die immer für alle Programme in einem Unternehmen gewährt werden.

Folgende Berechtigungen sind Berechtigungen auf Unternehmensebene:

* **Programm erstellen** – Mit dieser Berechtigung können Benutzende ein Programm im Unternehmen erstellen.
* **Zugriff auf Repository** Mit dieser Berechtigung auf Mandanten-/Organisationsebene können Benutzer einen Benutzernamen, ein Kennwort und eine Repository-URL generieren, um auf ein Kundenprojekt zuzugreifen und dazu beizutragen.
   * Benutzername und Kennwort für den Repository-Zugriff sind in allen Repositorys im Unternehmen gleich. Die Repository-URL ist jedoch für jedes Programm eindeutig.
   * Weitere Informationen finden Sie unter [Zugreifen auf Repositorys](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

## Begriffe {#terms}

Folgende Begriffe werden beim Erstellen und Verwalten benutzerdefinierter Berechtigungen und vordefinierter Rollen verwendet.

| Begriff | Beschreibung |
| --- | --- |
| Vordefinierte Berechtigungen | Vordefinierte Rollen wie **Geschäftsinhaber** und **Bereitstellungs-Manager**, um verschiedene Funktionen von Cloud Manager zu steuern. Weitere Informationen zu vordefinierten Rollen finden Sie unter [AEM as a Cloud Service – Team- und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md). |
| Benutzerdefinierte Berechtigungen | Mit Cloud Manager-Funktionen können Benutzende Berechtigungsprofile erstellen, um Rollen zu definieren, die die unterstützten Funktionen von Cloud Manager steuern. |
| Produktprofil | Wird in der Admin Console erstellt, um konfigurierbare Berechtigungen zu verwalten, die für Benutzende gelten, die Teil des Berechtigungsprofils sind. |
| Konfigurierbare Berechtigung | Cloud Manager-Berechtigungen, die Sie im Berechtigungsprofil konfigurieren können. |
| Berechtigungselement | Ein Programm, eine Umgebung oder eine Pipeline-Ressource, auf die eine Berechtigung angewendet werden kann. |

Berechtigungselemente beziehen sich auf den Anwendungsumfang der Berechtigung. In der Regel handelt es sich um Folgendes.

| Berechtigungselementtyp | Beispiel | Beschreibung |
| --- | --- | --- |
| Unternehmen | Unternehmen:FirmaA | Alle anwendbaren Ressourcen eines Unternehmens. Eine Ressource kann ein Programm, eine Umgebung oder eine Pipeline sein. Wenn Benutzende ein Unternehmen für eine Berechtigung hinzufügen, erhalten auch alle neuen Ressourcen in diesem Unternehmen diese Berechtigung. |
| Programm | Programm A | Alle anwendbaren Ressourcen eines Programms. |
| Umgebung | Programm A : Umgebung | Gilt für eine bestimmte Umgebung. |
| Pipeline | Programm A : Pipeline | Gilt für eine bestimmte Pipeline. |

## Nutzungshinweise {#usage-notes}

* Ein benutzerdefiniertes Berechtigungsprofil listet auch AMS-Programme, Umgebungen und Pipelines beim Konfigurieren von Berechtigungen auf.
* Es kann bis zu zwei Minuten dauern, bis in der Admin Console für die Berechtigungskonfiguration Ressourcen wie Programm, Umgebung und Pipeline angezeigt werden, die in Cloud Manager erstellt wurden.
* In seltenen Fällen, in denen ein benutzerdefinierter Berechtigungsdienst nicht reagiert, sind vordefinierte Profile weiterhin verfügbar und Benutzende in vordefinierten Profilen haben weiterhin darauf Zugriff.

## Häufig gestellte Fragen {#faq}

### Welche Berechtigungsprofile sind vordefinierte Berechtigungsprofile?

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwicklerin oder Entwickler

Weitere Informationen zu vordefinierten Rollen finden Sie unter [AEM as a Cloud Service – Team- und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md).

### Was passiert mit vordefinierten Berechtigungsprofilen bei der Einführung in benutzerdefinierte Profile?

Die standardmäßigen Produktprofile und Cloud Manager-Rollen funktionieren weiterhin wie zuvor.

### Kann ich vordefinierte Berechtigungsprofile bearbeiten?

Nein, Standardprofile können nicht bearbeitet werden. Sie können keine Berechtigungen zum standardmäßigen Berechtigungsprofil hinzufügen oder welche daraus entfernen. Sie können nur Benutzende zu vordefinierten Profilen hinzufügen oder daraus entfernen.

### Sollte ich vordefinierte Berechtigungsprofile löschen, wenn benutzerdefinierte Profile verfügbar sind?

Löschen Sie keine vordefinierten Berechtigungsprofile aus der Admin Console.

### Kann ich Benutzende zu mehreren Berechtigungsprofilen hinzufügen?

Ja, eine Person kann Teil mehrerer Profile sein, einschließlich vordefinierter und benutzerdefinierter Berechtigungsprofile. Wenn eine Person mehreren Profilen zugewiesen wird, stehen ihr die kombinierten Berechtigungen aus allen zugewiesenen Berechtigungsprofilen zur Verfügung.

### Was passiert, wenn eine Person berechtigt ist, eine Umgebung/Pipeline zu bearbeiten, aber keinen Zugriff auf ein Programm hat, das die Umgebung/Pipeline enthält?

In diesem Fall kann die Person nicht auf die Umgebung oder Pipeline zugreifen, wenn sie nicht über die Berechtigungen für den **Programmzugriff** auf die Umgebung oder Pipeline verfügt.
