---
title: Benutzerdefinierte Berechtigungen
description: Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzer zu beschränken.
exl-id: 167da985-7f19-45b3-90a3-884817907da2
source-git-commit: be38ca5bf79d401fc12c1422c270a2ee84bbbad2
workflow-type: tm+mt
source-wordcount: '1532'
ht-degree: 38%

---

# Benutzerdefinierte Berechtigungen {#custom-permissions}

Erfahren Sie, wie Sie mit benutzerdefinierten Berechtigungen benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen können, um den Zugriff auf Programme, Pipelines und Umgebungen für Cloud Manager-Benutzer zu beschränken.

>[!NOTE]
>
>Diese Funktion ist nur für das [Early-Adopter-Programm](/help/implementing/cloud-manager/release-notes/current.md#early-adoption) verfügbar.

## Einführung {#introduction}

Cloud Manager verfügt über eine Reihe vordefinierter Rollen, die den Zugriff auf verschiedene Funktionen von Cloud Manager steuern:

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwickler

Mit benutzerdefinierten Berechtigungen können Benutzer benutzerdefinierte Berechtigungsprofile mit konfigurierbaren Berechtigungen erstellen, um den Zugriff für Cloud Manager-Benutzer auf Programme, Pipelines und Umgebungen zu beschränken.

>[!TIP]
>
>Weitere Informationen zu vordefinierten Rollen finden Sie unter [AEM as a Cloud Service Team und Produktprofile](/help/onboarding/aem-cs-team-product-profiles.md).

## Verwenden benutzerdefinierter Berechtigungen {#using}

Um eigene benutzerdefinierte Berechtigungen zu erstellen und zu verwenden, sind drei Schritte erforderlich:

1. [Erstellen Sie ein Produktprofil.](#create)
1. [Weisen Sie dem Produktprofil benutzerdefinierte Berechtigungen zu.](#assign-permissions)
1. [Weisen Sie dem Produktprofil Benutzer zu.](#assign-users)

In diesem Abschnitt werden diese Schritte beschrieben. Möglicherweise helfen Ihnen die Informationen unter [Begriffe](#terms) und [Konfigurierbare Berechtigungen](#configurable-permissions) bei der Erstellung Ihrer eigenen benutzerdefinierten Berechtigungen.

>[!NOTE]
>
>Sie müssen über Produktadministratorrechte in Admin Console verfügen, damit Adobe Experience Manager as a Cloud Service Profile erstellen und Berechtigungen für Cloud Manager verwalten kann.

### Erstellen eines neuen Produktprofils {#create}

Erstellen Sie zunächst ein Produktprofil, bevor Sie benutzerdefinierte Berechtigungen zuweisen können.

1. Melden Sie sich bei Cloud Manager an unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/).

1. Wählen Sie auf der Landingpage von Cloud Manager die **Zugriff verwalten** Schaltfläche.

![Schaltfläche Zugriff verwalten](assets/manage-access.png)

1. Sie werden zur Registerkarte **Produkte** der Admin Console geleitet, auf der Sie Cloud Manager-Benutzende und Berechtigungen verwalten können. Wählen Sie in der Admin Console die **Neues Profil** Schaltfläche.

![Schaltfläche „Neues Profil“](assets/admin-console-new-profile.png)

1. Geben Sie die allgemeinen Details zum Profil an.

   * **Name des Produktprofils** – Ein aussagekräftiger Name des Profils
   * **Anzeigename** - Ein abgekürzter Name, der in der Benutzeroberfläche angezeigt wird (Optionen)
   * **Beschreibung** – Eine informative Beschreibung des Profils, das seinen Zweck erklärt (optional)
   * **Benutzer per E-Mail benachrichtigen** - Wenn diese Option aktiviert ist, werden Benutzer per E-Mail benachrichtigt, wenn sie diesem Profil hinzugefügt oder daraus entfernt werden.

1. Auswählen **Speichern** wenn abgeschlossen.

Das neue Produktprofil wird gespeichert und ist in der Liste der Produktprofile in der Admin Console sichtbar.

### Zuweisen benutzerdefinierter Berechtigungen zum Profil {#assign-permissions}

Nachdem Sie ein neues Produktprofil erstellt haben, können Sie ihm benutzerdefinierte Berechtigungen zuweisen.

1. Wählen Sie in der Admin Console den Namen der [Neues Produktprofil, das Sie erstellt haben](#create).

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Berechtigungen**, um eine Liste bearbeitbarer Berechtigungen anzuzeigen.

   ![Bearbeitbare Berechtigungen](assets/permissions-tab.png)

1. Wählen Sie die **Bearbeiten** einer Berechtigung, damit Sie sie bearbeiten können.

1. Die **Berechtigung bearbeiten** öffnet sich.
   * Die Berechtigung, die Sie im vorherigen Schritt ausgewählt haben, ist in der linken Spalte ausgewählt.
   * Die für die Zuweisung der Berechtigung verfügbaren Berechtigungselemente befinden sich in der mittleren Spalte **Verfügbare Berechtigungselemente**.
   * Die zugewiesenen Berechtigungselemente befinden sich in der rechten Spalte mit der Bezeichnung **Eingeschlossene Berechtigungselemente**.

   ![Berechtigungselemente bearbeiten](assets/edit-permission-items.png)

1. Wählen Sie das Pluszeichen (`+`) neben dem Berechtigungselement, damit Sie es zur Spalte hinzufügen können. **Eingeschlossene Berechtigungselemente**.

   * Wählen Sie die `i` neben einem Berechtigungselement klicken, wenn Sie mehr darüber erfahren möchten.

1. Wählen Sie die **Alle hinzufügen** -Schaltfläche oben im **Verfügbare Berechtigungen** -Spalte, damit Sie alle Berechtigungen hinzufügen können.

1. Auswählen **Speichern** wenn Sie mit der Definition der Berechtigungselemente für Ihr neues Produktprofil fertig sind.

Ihr neues Produktprofil wird jetzt mit den benutzerdefinierten Berechtigungen gespeichert.

### Zuweisen von Benutzenden zu den benutzerdefinierten Berechtigungen {#assign-users}

Sie können dem neuen Produktprofil, das Sie mit benutzerdefinierten Berechtigungen erstellt haben, jetzt Benutzende zuweisen.

1. Wählen Sie in der Admin Console den Namen der [neues Produktprofil, dem Sie benutzerdefinierte Berechtigungen zugewiesen haben.](#assign-permissions)

1. Öffnen Sie in dem Fenster, das daraufhin erscheint, die Registerkarte **Benutzer**.

1. Wählen Sie die **Benutzer hinzufügen** und weisen Sie Ihrem neuen Produktprofil Benutzer mit benutzerdefinierten Berechtigungen zu.

Siehe Abschnitt . **Hinzufügen von Benutzern und Benutzergruppen zu einem Produktprofil** des Dokuments [Verwalten von Produktprofilen für Unternehmensbenutzer](https://helpx.adobe.com/de/enterprise/using/manage-product-profiles.html) für weitere Informationen zur Verwendung der Admin Console.

## Konfigurierbare Berechtigungen {#configurable-permissions}

Zum Erstellen benutzerdefinierter Profile stehen folgende Berechtigungen zur Verfügung.

| Berechtigung | Beschreibung |
|---|---|
| Programm erstellen | Benutzern das Erstellen eines Programms erlauben |
| Programmzugriff | Benutzenden den Zugriff auf Programme gewähren |
| Programmbearbeitung | Benutzenden erlauben, Programme zu bearbeiten |
| Umgebung erstellen | Benutzern erlauben, eine Umgebung zu erstellen |
| Umgebungsbearbeitung | Benutzer können Umgebungen aktualisieren und bearbeiten |
| Umgebungsprotokolle lesen | Lesen von Umgebungsprotokollen durch Benutzer zulassen |
| Verwalten von Umgebungsvariablen | Benutzer können Umgebungskonfigurationen erstellen/bearbeiten/löschen |
| Umgebungswiederherstellung erstellen | Benutzer können Umgebung wiederherstellen |
| Schnelles Zurücksetzen der Entwicklungsumgebung | Benutzer können die schnelle Entwicklungsumgebung zurücksetzen |
| Inhaltskopie verwalten | Benutzern erlauben, Vorgänge zum Kopieren von Inhalten zu verwalten |
| Pipeline erstellen | Erstellen von Pipelines durch Benutzer zulassen |
| Pipeline löschen | Benutzenden erlauben, Pipelines zu löschen |
| Pipeline-Bearbeitung | Benutzenden erlauben, Pipelines zu bearbeiten |
| Genehmigung/Ablehnung von Produktionsbereitstellungen | Benutzenden erlauben, einen Produktionsbereitstellungsschritt zu genehmigen oder abzulehnen |
| Pipeline-Ausführungen abbrechen | Benutzenden erlauben, Pipeline-Ausführungen abzubrechen |
| Pipeline-Ausführungen starten | Benutzer können eine neue Pipeline-Ausführung starten |
| Wichtige Metrikfehler überschreiben/ablehnen | Benutzenden erlauben, wichtige Metrikfehler zu überschreiben/abzulehnen |
| Produktionsbereitstellungs-Zeitplan | Benutzenden erlauben, einen Produktionsbereitstellungsschritt zu planen |
| Zugriff auf Repository-Informationen | Benutzenden erlauben, auf Repository-Informationen zuzugreifen und ein Passwort für den Zugriff zu erstellen |
| Repository erstellen | Benutzern erlauben, Git-Repositorys zu erstellen |
| Repository löschen | Löschen von Git-Repositorys durch Benutzer zulassen |
| Repository bearbeiten | Benutzern erlauben, Git-Repositorys zu bearbeiten |
| Repository-Codegenerierung | Benutzer können Projekte aus dem Archetyp generieren |
| Domänenname verwalten | Benutzern das Erstellen/Bearbeiten/Löschen von Domänennamen ermöglichen |
| Verwalten von IP-Zulassungslisten | Benutzern das Erstellen/Bearbeiten/Löschen von IP-Zulassungslisten- und IP-Zulassungslisten-Bindungen ermöglichen |
| Netzwerkinfrastruktur-Management | Benutzer können Netzwerkinfrastruktur erstellen/bearbeiten/löschen |
| SSL-Zertifikatverwaltung | Ermöglichen Sie Benutzern das Erstellen/Bearbeiten/Löschen eines SSL-Zertifikats |
| New Relic Sub Account User Verwalten | Benutzern das Lesen/Bearbeiten von New Relic-Unterkontobenutzern ermöglichen |

### Berechtigungen auf Unternehmensebene {#organization-level}

Berechtigungen auf Organisationsebene beziehen sich auf Berechtigungen, die immer für alle Programme in einer Organisation gewährt werden.

Folgende Berechtigungen sind Berechtigungen auf Unternehmensebene:

* **Programm erstellen** - Mit dieser Berechtigung können Benutzer ein Programm in der Organisation erstellen.
* **Zugriff auf Repository-Informationen** Mit dieser Berechtigung auf Mandanten-/Organisationsebene können Benutzer Benutzernamen, Kennwort und Repository-URL generieren, um auf das Kundenprojekt zuzugreifen und zu diesem beizutragen.
   * Benutzername und Kennwort für den Repository-Zugriff sind in allen Repositorys in der Organisation üblich, die Repository-URL ist jedoch für jedes Programm eindeutig.
   * Siehe [Zugreifen auf Repositorys](/help/implementing/cloud-manager/managing-code/accessing-repos.md) für weitere Informationen.

## Begriffe {#terms}

Folgende Begriffe werden beim Erstellen und Verwalten benutzerdefinierter Berechtigungen und vordefinierter Rollen verwendet.

| Begriff | Beschreibung |
|---|---|
| Vordefinierte Berechtigungen | Vordefinierte Rollen wie **Business Owner** und **Bereitstellungsmanager** , um verschiedene Funktionen von Cloud Manager zu steuern. Weitere Informationen zu vordefinierten Rollen finden Sie unter [AEM as a Cloud Service Team und Produktprofile.](/help/onboarding/aem-cs-team-product-profiles.md) |
| Benutzerdefinierte Berechtigungen | Mit Cloud Manager-Funktionen können Benutzer Berechtigungsprofile erstellen, um Rollen für unterstützte Cloud Manager-Funktionen zu definieren. |
| Produktprofil | Erstellt in der Admin Console zum Verwalten konfigurierbarer Berechtigungen, die für Benutzer gelten, die zum Berechtigungsprofil gehören |
| Konfigurierbare Berechtigung | Cloud Manager-Berechtigungen, die im Berechtigungsprofil konfiguriert werden können |
| Berechtigungselement | Eine Programm-, Umgebungs- oder Pipeline-Ressource, auf die eine Berechtigung angewendet werden kann |

Berechtigungselemente beziehen sich auf den Umfang, in dem die Berechtigung angewendet wird. In der Regel handelt es sich um eine der folgenden Aktionen.

| Berechtigungselementtyp | Beispiel | Beschreibung |
|---|---|---|
| Unternehmen | Unternehmen:FirmaA | Alle anwendbaren Ressourcen eines Unternehmens. Eine Ressource kann ein Programm, eine Umgebung oder eine Pipeline sein. Wenn der Benutzer eine Organisation für eine Berechtigung hinzufügt, haben auch alle neuen Ressourcen in dieser Organisation diese Berechtigung. |
| Programm | Programm A | Alle anwendbaren Ressourcen eines Programms |
| Umgebung | Programm A : Umgebung | Anwendbar für eine bestimmte Umgebung |
| Pipeline | Programm A : Pipeline | Anwendbar für eine bestimmte Pipeline |

## Einschränkungen {#limitations}

Beachten Sie bei der Verwendung benutzerdefinierter Berechtigungen die folgenden Einschränkungen.

* Benutzerdefinierte Berechtigungsprofile listen beim Konfigurieren von Berechtigungen auch AMS-Programme, -Umgebungen und -Pipelines auf.
* Es kann zwei Minuten dauern, bis in Admin Console für die Berechtigungskonfiguration Ressourcen wie Programm, Umgebung und Pipeline angezeigt werden, die in Cloud Manager erstellt wurden.
* In seltenen Fällen, in denen der benutzerdefinierte Berechtigungsdienst nicht reagiert, sind vordefinierte Profile weiterhin verfügbar und Benutzende in vordefinierten Profilen haben weiterhin darauf Zugriff.

## Häufig gestellte Fragen {#faq}

### Welche Berechtigungsprofile sind vordefinierte Berechtigungsprofile?

* Geschäftsinhaber
* Programm-Manager
* Bereitstellungs-Manager
* Entwickler

Weitere Informationen zu vordefinierten Rollen finden Sie unter [AEM as a Cloud Service Team und Produktprofile.](/help/onboarding/aem-cs-team-product-profiles.md)

### Was passiert mit vordefinierten Berechtigungsprofilen bei der Einführung in benutzerdefinierte Profile?

Die standardmäßigen Produktprofile und Cloud Manager-Rollen funktionieren weiterhin wie zuvor.

### Kann ich vordefinierte Berechtigungsprofile bearbeiten?

Nein, Standardprofile können nicht bearbeitet werden. Sie können keine Berechtigungen zum standardmäßigen Berechtigungsprofil hinzufügen oder entfernen. Sie können nur Benutzende zu vordefinierten Profilen hinzufügen oder daraus entfernen.

### Sollte ich vordefinierte Berechtigungsprofile löschen, wenn benutzerdefinierte Profile verfügbar sind?

Löschen Sie keine vordefinierten Berechtigungsprofile aus der Admin Console.

### Kann ich Benutzende zu mehreren Berechtigungsprofilen hinzufügen?

Ja, eine Person kann Teil mehrerer Profile sein, einschließlich vordefinierter und benutzerdefinierter Berechtigungsprofile. Wenn ein Benutzer mehreren Profilen zugewiesen ist, stehen ihm die kombinierten Berechtigungen aus allen zugewiesenen Berechtigungsprofilen zur Verfügung.

### Was passiert, wenn eine Person berechtigt ist, eine Umgebung/Pipeline zu bearbeiten, aber keinen Zugriff auf ein Programm hat, das die Umgebung/Pipeline enthält?

In diesem Fall kann der Benutzer nicht auf die Umgebung oder Pipeline zugreifen, wenn er nicht über die **Programmzugriff** Berechtigungen, die die Umgebung oder Pipeline enthalten.
