---
title: Benutzerdefinierte Berechtigungen
description: Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzer zu beschränken.
exl-id: 167da985-7f19-45b3-90a3-884817907da2
source-git-commit: e2505c0fec1da8395930f131bfc55e1e2ce05881
workflow-type: tm+mt
source-wordcount: '1501'
ht-degree: 2%

---

# Benutzerdefinierte Berechtigungen {#custom-permissions}

Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzer zu beschränken.

>[!NOTE]
>
>Diese Funktion steht nur für [das Programm für den frühen Anwender.](/help/implementing/cloud-manager/release-notes/current.md#early-adoption)

## Einführung {#introduction}

Cloud Manager verfügt über eine Reihe vordefinierter Rollen, die den Zugriff auf verschiedene Funktionen von Cloud Manager steuern:

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwickler

Mit benutzerdefinierten Berechtigungen können Benutzer neue benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um den Zugriff für Cloud Manager-Benutzer auf Programme, Pipelines und Umgebungen zu beschränken.

>[!TIP]
>
>Weitere Informationen zu vordefinierten Rollen finden Sie im Dokument [AEM as a Cloud Service Team und Produktprofile.](/help/onboarding/aem-cs-team-product-profiles.md)

## Verwenden benutzerdefinierter Berechtigungen {#using}

Um eigene benutzerdefinierte Berechtigungen zu erstellen und zu verwenden, sind drei Schritte erforderlich:

1. [Erstellen Sie ein neues Produktprofil.](#create)
1. [Weisen Sie dem neuen Produktprofil benutzerdefinierte Berechtigungen zu.](#assign-permissions)
1. [Weisen Sie dem neuen Produktprofil Benutzer zu.](#assign-users)

In diesem Abschnitt werden diese Schritte beschrieben. Sie können es für nützlich halten, die Informationen unter [Begriffe](#terms) und [Konfigurierbare Berechtigungen](#configurable-permissions) -Abschnitte, während Sie Ihre eigenen benutzerdefinierten Berechtigungen erstellen.

>[!NOTE]
>
>Sie müssen über Produktadministratorrechte in Admin Console für Adobe Experience Manager as a Cloud Service verfügen, um neue Profile zu erstellen und Berechtigungen für Cloud Manager zu verwalten.

### Neues Produktprofil erstellen {#create}

Sie müssen zunächst ein Produktprofil erstellen, bevor Sie benutzerdefinierte Berechtigungen zuweisen können.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/)

1. Tippen oder klicken Sie auf der Landingpage von Cloud Manager auf die **Zugriff verwalten** button

![Schaltfläche Zugriff verwalten](assets/manage-access.png)

1. Sie werden zum **Produkte** -Registerkarte der Admin Console, auf der Sie Benutzer und Berechtigungen für Cloud Manager verwalten können. Tippen oder klicken Sie in der Admin Console auf die **Neues Profil** Schaltfläche.

![Schaltfläche &quot;Neues Profil&quot;](assets/admin-console-new-profile.png)

1. Geben Sie die allgemeinen Details zum Profil an.

   * **Name des Produktprofils** - Ein beschreibender Name für das Profil
   * **Anzeigename** - Ein abgekürzter Name, der in der Benutzeroberfläche angezeigt wird (Optionen)
   * **Beschreibung** - Eine informative Beschreibung des Profils, das seinen Zweck erklärt (optional)
   * **Benutzer per E-Mail benachrichtigen** - Wenn diese Option aktiviert ist, werden Benutzer per E-Mail benachrichtigt, wenn sie diesem Profil hinzugefügt oder daraus entfernt werden.

1. Tippen oder klicken **Speichern** wenn abgeschlossen.

Das neue Produktprofil wird gespeichert und ist in der Liste der Produktprofile in der Admin Console sichtbar.

### Zuweisen benutzerdefinierter Berechtigungen zum Profil {#assign-permissions}

Nachdem Sie ein neues Produktprofil erstellt haben, können Sie ihm benutzerdefinierte Berechtigungen zuweisen.

1. Tippen oder klicken Sie in der Admin Console auf den Namen der [neues Produktprofil, das Sie soeben erstellt haben.](#create)

1. Wählen Sie im sich öffnenden Fenster die **Berechtigungen** um eine Liste bearbeitbarer Berechtigungen anzuzeigen.

   ![Bearbeitbare Berechtigungen](assets/permissions-tab.png)

1. Tippen oder klicken Sie auf **Bearbeiten** Link einer Berechtigung zur Bearbeitung.

1. Die **Berechtigungen bearbeiten** öffnet sich.
   * Die Berechtigung, die Sie im vorherigen Schritt ausgewählt haben, wird in der linken Spalte ausgewählt.
   * Die für die Zuweisung der Berechtigung verfügbaren Berechtigungselemente befinden sich in der mittleren Spalte **Verfügbare Berechtigung** Elemente.
   * Die zugewiesenen Berechtigungselemente befinden sich in der rechten Spalte mit der Bezeichnung **Eingeschlossene Berechtigungselemente**.

   ![Berechtigungselemente bearbeiten](assets/edit-permission-items.png)

1. Tippen oder klicken Sie auf das Pluszeichen (`+`) neben dem Berechtigungselement, um es der Spalte hinzuzufügen. **Eingeschlossene Berechtigungselemente**.

   * Tippen oder klicken Sie auf `i` neben einem Berechtigungselement klicken, um mehr darüber zu erfahren.

1. Tippen oder klicken Sie auf **Alle hinzufügen** -Schaltfläche oben im **Verfügbare Berechtigungen** um alle Berechtigungen hinzuzufügen.

1. Wenn das Profil immer über alle Berechtigungselemente verfügen soll, sollten Sie die **Automatisch einschließen** -Option.

   * **on** - Alle aktuellen Berechtigungselemente und zukünftigen Berechtigungselemente werden nach Einbezogene Berechtigungselemente verschoben und beim Speichern gelten entsprechend.
   * **Aus** - Alle Berechtigungselemente werden zurück zu den verfügbaren Berechtigungselementen verschoben und beim Speichern gelten entsprechend.

1. Tippen oder klicken **Speichern** wenn Sie mit der Definition der Berechtigungselemente für Ihr neues Produktprofil fertig sind.

Ihr neues Produktprofil wird jetzt mit den benutzerdefinierten Berechtigungen gespeichert.

### Benutzer benutzerdefinierten Berechtigungen zuweisen {#assign-users}

Sie können jetzt Benutzer dem neuen Produktprofil zuweisen, das Sie mit benutzerdefinierten Berechtigungen erstellt haben.

1. Tippen oder klicken Sie in der Admin Console auf den Namen der [neues Produktprofil, dem Sie soeben benutzerdefinierte Berechtigungen zugewiesen haben.](#assign-permissions)

1. Wählen Sie im sich öffnenden Fenster die **Benutzer** Registerkarte.

1. Tippen oder klicken Sie auf **Benutzer hinzufügen** und weisen Sie Ihrem neuen Produktprofil Benutzer mit benutzerdefinierten Berechtigungen zu.

Siehe Abschnitt . **Hinzufügen von Benutzern und Benutzergruppen zu einem Produktprofil** des Dokuments [Verwalten von Produktprofilen für Unternehmensbenutzer](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html) für weitere Informationen zur Verwendung der Admin Console.

## Konfigurierbare Berechtigungen {#configurable-permissions}

Die folgenden Berechtigungen sind für das Erstellen benutzerdefinierter Profile verfügbar.

| Berechtigung | Beschreibung |
|---|---|
| Programm erstellen | Benutzern das Erstellen eines Programms erlauben |
| Programmzugriff | Ermöglichen des Zugriffs auf Programme |
| Programmbearbeitung | Benutzer können Programme bearbeiten |
| Umgebung erstellen | Benutzern erlauben, eine Umgebung zu erstellen |
| Umgebungsbearbeitung | Benutzer können Umgebungen aktualisieren und bearbeiten |
| Umgebungsprotokolle lesen | Lesen von Umgebungsprotokollen durch Benutzer zulassen |
| Pipeline erstellen | Benutzer können neue Pipelines erstellen |
| Pipeline löschen | Löschen von Pipelines durch Benutzer zulassen |
| Pipeline bearbeiten | Bearbeiten von Pipelines durch Benutzer zulassen |
| Produktionsbereitstellungen Genehmigen/Ablehnen | Erlauben Sie Benutzern, einen Produktionsbereitstellungsschritt zu genehmigen oder abzulehnen |
| Pipeline-Ausführungen abbrechen | Abbrechen von Pipeline-Ausführungen durch Benutzer zulassen |
| Pipeline-Ausführungen starten | Benutzer können neue Pipeline-Ausführungen starten |
| Wichtige Metrikfehler überschreiben/ablehnen | Benutzer können wichtige Metrikfehler überschreiben/ablehnen |
| Zeitplan für Produktionsbereitstellungen | Benutzern erlauben, einen Produktionsbereitstellungsschritt zu planen |
| Zugriff auf Repository-Informationen | Ermöglichen Sie Benutzern den Zugriff auf Repository-Informationen und das Generieren des Zugriffs-Kennworts |

### Berechtigungen auf Organisationsebene {#organization-level}

Berechtigungen auf Organisationsebene beziehen sich auf Berechtigungen, die immer für alle Programme in einer Organisation gewährt werden.

Die folgenden Berechtigungen sind Berechtigungen auf Unternehmensebene:

* **Programm erstellen** - Mit dieser Berechtigung können Benutzer ein Programm in der Organisation erstellen.
* **Zugriff auf Repository-Informationen** Mit dieser Berechtigung auf Mandanten-/Organisationsebene können Benutzer Benutzernamen, Kennwort und Repository-URL generieren, um auf das Kundenprojekt zuzugreifen und zu diesem beizutragen.
   * Benutzername und Kennwort für den Repository-Zugriff sind in allen Repositorys in der Organisation gleich, die Repository-URL ist jedoch für jedes Programm eindeutig.
   * Lesen Sie das Dokument . [Zugreifen auf Repositorys](/help/implementing/cloud-manager/managing-code/accessing-repos.md) für weitere Informationen.

## Begriffe {#terms}

Die folgenden Begriffe werden beim Erstellen und Verwalten von benutzerdefinierten Berechtigungen und vordefinierten Rollen verwendet.

| Begriff | Beschreibung |
|---|---|
| Vordefinierte Berechtigungen | Vordefinierte Rollen wie **Business Owner**, **Bereitstellungsmanager**, usw. , um verschiedene Funktionen von Cloud Manager zu steuern. Weitere Informationen zu vordefinierten Rollen finden Sie im Dokument [AEM as a Cloud Service Team und Produktprofile.](/help/onboarding/aem-cs-team-product-profiles.md) |
| Benutzerdefinierte Berechtigungen | Cloud Manager-Funktionen, mit denen Benutzer Berechtigungsprofile erstellen können, um Rollen für unterstützte Cloud Manager-Funktionen zu definieren |
| Produktprofil | In der Admin Console erstellt, um konfigurierbare Berechtigungen zu verwalten, die für Benutzer gelten, die Teil des Berechtigungsprofils sind |
| Konfigurierbare Berechtigung | Cloud Manager-Berechtigungen, die im Berechtigungsprofil konfiguriert werden können |
| Berechtigungselement | Eine Programm-, Umgebungs- oder Pipeline-Ressource, auf die eine Berechtigung angewendet werden kann |

Berechtigungselemente beziehen sich auf den Umfang, in dem die Berechtigung angewendet wird. In der Regel ist dies einer der folgenden Schritte.

| Berechtigungselementtyp | Beispiel | Beschreibung |
|---|---|---|
| Organisation | Organisation:companyA | Alle anwendbaren Ressourcen einer Organisation. Eine Ressource kann ein Programm, eine Umgebung oder eine Pipeline sein. Wenn der Benutzer eine Organisation für eine Berechtigung hinzufügt, erhalten auch alle neuen Ressourcen in dieser Organisation diese Berechtigung. |
| Programm | Programm A | Alle anwendbaren Ressourcen eines Programms |
| Umgebung | Programm A : Umwelt | Anwendbar in einer bestimmten Umgebung |
| Pipeline | Programm A : Pipeline | Anwendbar auf einer bestimmten Pipeline |

## Einschränkungen {#limitations}

Beachten Sie bei der Verwendung benutzerdefinierter Berechtigungen die folgenden Einschränkungen.

* Das Profil für benutzerdefinierte Berechtigungen listet beim Konfigurieren von Berechtigungen auch AMS-Programme, -Umgebungen und -Pipelines auf.
* Ressourcen wie Programm, Umgebung, Pipeline usw. die in Cloud Manager erstellt wurden, kann es zwei Minuten dauern, bis die Admin Console zur Berechtigungskonfiguration angezeigt wird.
* In seltenen Fällen, in denen der benutzerdefinierte Berechtigungsdienst nicht reagiert, sind vordefinierte Profile weiterhin verfügbar und Benutzer in vordefinierten Profilen haben weiterhin angemessenen Zugriff.

## Häufig gestellte Fragen {#faq}

### Welche Berechtigungsprofile sind vordefinierte Berechtigungsprofile?

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwickler

Weitere Informationen zu vordefinierten Rollen finden Sie im Dokument [AEM as a Cloud Service Team und Produktprofile.](/help/onboarding/aem-cs-team-product-profiles.md)

### Was passiert mit vordefinierten Berechtigungsprofilen mit der Einführung in benutzerdefinierte Profile?

Die standardmäßigen Produktprofile und Cloud Manager-Rollen funktionieren weiterhin wie zuvor.

### Kann ich vordefinierte Berechtigungsprofile bearbeiten?

Nein, Standardprofile können nicht bearbeitet werden. Sie können dem standardmäßigen Berechtigungsprofil keine Berechtigungen hinzufügen oder entfernen. Sie können nur Benutzer aus vordefinierten Profilen hinzufügen oder entfernen.

### Sollte ich vordefinierte Berechtigungsprofile löschen, da jetzt benutzerdefinierte Profile verfügbar sind?

Vordefinierte Berechtigungsprofile dürfen nicht aus der Admin Console gelöscht werden.

### Kann ich Benutzer zu mehreren Berechtigungsprofilen hinzufügen?

Ja, ein Benutzer kann Teil mehrerer Profile sein, einschließlich vordefinierter und benutzerdefinierter Berechtigungsprofile. Wenn ein Benutzer mehreren Profilen zugewiesen wird, stehen ihm die kombinierten Berechtigungen aus allen zugewiesenen Berechtigungsprofilen zur Verfügung.

### Was passiert, wenn ein Benutzer berechtigt ist, eine Umgebung/Pipeline zu bearbeiten, aber keinen Zugriff auf ein Programm hat, das die Umgebung/Pipeline enthält?

In diesem Fall kann der Benutzer nicht auf die Umgebung oder Pipeline zugreifen, wenn er nicht über die **Programmzugriff** Berechtigungen, die die Umgebung oder Pipeline enthalten.
