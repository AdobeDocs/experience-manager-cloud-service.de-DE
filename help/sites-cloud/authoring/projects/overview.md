---
title: Projekte
description: Projekte ermöglichen es Ihnen, Ressourcen zu einer Einheit gruppieren, deren gemeinsame Umgebung die Projektverwaltung erleichtert.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: c5f3331e-637f-4816-be83-faf2df59bd5f
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '1259'
ht-degree: 99%

---

# Projekte {#projects}

Mithilfe von Projekten können Sie Ressourcen zu einer Einheit gruppieren. Eine gemeinsam genutzte Umgebung erleichtert die Projektverwaltung. Die Ressourcentypen, die Sie mit einem Projekt verknüpfen können, werden in AEM als Kacheln bezeichnet. Kacheln können Projekt- und Team-Informationen, Assets, Workflows und andere Arten von Informationen sein. Ausführliche Informationen finden Sie unter [Projektkacheln](#project-tiles).

>[!CAUTION]
>
>Damit Benutzer in Projekten andere Benutzer/Gruppen sehen können, während sie mit Projektfunktionen wie Erstellen von Projekten, Erstellen von Aufgaben/Workflows, Anzeigen und Verwalten des Teams arbeiten, benötigen sie Lesezugriff auf `/home/users` und `/home/groups`. Um dies umzusetzen, erteilen Sie am besten der Gruppe **projects-users** Lesezugriff auf `/home/users` und `/home/groups`.

Als Benutzer haben Sie folgende Möglichkeiten:

* Erstellen von Projekten
* Zuordnen von Inhalten und Asset-Ordnern zu einem Projekt
* Löschen von Projekten
* Entfernen von Inhaltsverknüpfungen aus einem Projekt

Weitere Informationen finden Sie in folgenden Themen:

* [Verwalten von Projekten](/help/sites-cloud/authoring/projects/managing.md)
* [Arbeiten mit Aufgaben](/help/sites-cloud/authoring/projects/tasks.md)
* [Arbeiten mit Projekt-Workflows](/help/sites-cloud/authoring/projects/workflows.md)

## Projektekonsole {#projects-console}

In der Projektekonsole können Sie innerhalb von AEM auf Ihre Projekte zugreifen und diese verwalten.

![Die Projektekonsole](/help/sites-cloud/authoring/assets/projects-console.png)

* Wählen Sie **Timeline** und dann ein Projekt, um seine Timeline anzuzeigen.
* Wählen Sie **Auswählen** aus, um in den Auswahlmodus zu wechseln.
* Klicken Sie auf **Erstellen**, um Projekte hinzuzufügen.
* Mit **Aktive Projekte ein/aus** können Sie zwischen allen Projekten und nur den aktiven wechseln.
* Mit **Statistikansicht anzeigen** können Sie die Projektstatistiken zu Aufgabenabschlüssen anzeigen.

## Projektkacheln {#project-tiles}

Sie können verschiedene Arten von Informationen mit Ihren Projekten verknüpfen. Diese werden als **Kacheln** bezeichnet. In diesem Abschnitt werden die einzelnen Kacheln und die enthaltenen Informationen beschrieben.

Sie können die folgenden Kacheln mit Ihrem Projekt verknüpfen. Sie werden in den folgenden Abschnitten beschrieben:

* Assets und Asset-Sammlungen
* Erlebnisse
* Links
* Projektinformationen
* Team
* Landingpages
* E-Mails
* Workflows
* Launches
* Aufgaben

### Assets {#assets}

In der Kachel **Assets** können Sie alle Assets zusammenstellen, die Sie für ein bestimmtes Projekt verwenden.

![Assets-Kachel](/help/sites-cloud/authoring/assets/projects-assets-tile.png)

Laden Sie Assets direkt in die Kachel hoch. Darüber hinaus können Sie Bild-Sets, Rotations-Sets oder gemischte Mediensets erstellen, wenn Sie über das Zusatzmodul für Dynamic Media verfügen.

![Bild-Set](/help/sites-cloud/authoring/assets/projects-image-sets.png)

### Asset-Sammlungen {#asset-collections}

[Asset-Sammlungen](/help/assets/manage-collections.md) können Ihrem Projekt ähnlich wie Assets direkt hinzugefügt werden. Sie definieren die Sammlungen unter „Assets“.

![Asset-Sammlung](/help/sites-cloud/authoring/assets/projects-asset-collections.png)

Fügen Sie eine Sammlung hinzu, indem Sie auf **Sammlung hinzufügen** klicken und die entsprechende Sammlung in der Liste auswählen.

### Erlebnisse {#experiences}

Über die Kachel **Erlebnisse** können Sie eine Mobile App, eine Website oder eine Veröffentlichung zum Projekt hinzufügen.

![Erlebnisse](/help/sites-cloud/authoring/assets/project-experiences.png)

Die Symbole geben an, welche Art von Erlebnis dargestellt wird: Website, Mobile App oder eine Veröffentlichung. Fügen Sie Erlebnisse hinzu, indem Sie auf den nach unten zeigenden Pfeil tippen oder klicken, dann auf **Erlebnis hinzufügen** tippen und die Art des Erlebnisses auswählen.

![Erlebnis hinzufügen](/help/sites-cloud/authoring/assets/projects-add-experience.png)

Wählen Sie den Pfad für die Miniaturen aus und, falls zutreffend, ändern Sie die Miniatur für das Erlebnis. Erlebnisse werden in der Kachel **Erlebnisse** gruppiert.

### Links {#links}

Über die Kachel „Links“ können Sie externe Links mit Ihrem Projekt verknüpfen.

![Links](/help/sites-cloud/authoring/assets/project-links.png)

Sie können dem Link einen aussagekräftigen Namen geben und das Miniaturbild ändern.

![Link hinzufügen](/help/sites-cloud/authoring/assets/projects-add-link.png)

### Projektinformationen {#project-info}

Die Kachel „Projektinformationen“ enthält allgemeine Informationen zum Projekt, einschließlich einer Beschreibung, des Projektstatus (inaktiv oder aktiv), eines Fälligkeitsdatums und der Mitglieder. Darüber hinaus können Sie eine ProjektMiniatur hinzufügen, die auf der Hauptprojektseite angezeigt wird.

![Projektinformationen](/help/sites-cloud/authoring/assets/project-info.png)

Team-Mitglieder können über diese Kachel und die Team-Kachel zugewiesen und gelöscht (oder ihre Rollen geändert) werden.

![Team-Mitglieder zum Projekt hinzufügen](/help/sites-cloud/authoring/assets/projects-add-team.png)

### Übersetzungsauftrag {#translation-job}

In der Kachel „Übersetzungsauftrag“ können Sie eine Übersetzung starten und sehen den jeweiligen Status Ihrer Übersetzungen. Informationen zum Einrichten Ihrer Übersetzung finden Sie unter [Erstellen von Übersetzungsprojekten](/help/assets/translate-assets.md).

![Übersetzungsauftrag](/help/sites-cloud/authoring/assets/projects-translation-job.png)

Klicken Sie auf die Auslassungszeichen unten auf der Karte **Übersetzungsauftrag**, um die Assets im Übersetzungs-Workflow anzuzeigen. In der Übersetzungsauftragsliste werden auch Einträge für Asset-Metadaten und -Tags aufgeführt. Diese Einträge geben an, dass die Metadaten und Tags für die Assets ebenfalls übersetzt werden.

![Detail des Übersetzungsauftrags](/help/sites-cloud/authoring/assets/projects-translation-job-detail.png)

### Team {#team}

In dieser Kachel können Sie die Mitglieder des Projekt-Teams angeben. Geben Sie die Namen der Team-Mitglieder ein und weisen Sie Benutzerrollen zu.

![Kachel „Team“](/help/sites-cloud/authoring/assets/projects-team-tile.png)

Sie können Team-Mitglieder zum Team hinzufügen und aus ihm löschen. Darüber hinaus können Sie die [Benutzerrolle](#user-roles-in-a-project) bearbeiten, die dem jeweiligen Team-Mitglied zugewiesen ist.

![Team aus Liste hinzufügen](/help/sites-cloud/authoring/assets/projects-add-team-list.png)

### Workflows {#workflows}

Sie können Ihr Projekt bestimmten Workflows zuweisen. Wenn Workflows ausgeführt werden, wird ihr Status in „Projekte“ in der Kachel **Workflows** angezeigt.

![Workflows](/help/sites-cloud/authoring/assets/project-workflows.png)

Sie können Ihr Projekt bestimmten Workflows zuweisen. Je nach Projekt stehen verschiedene Workflows zur Verfügung.

Diese werden unter [Arbeiten mit Projekt-Workflows](/help/sites-cloud/authoring/projects/workflows.md) beschrieben.

### Launches {#launches}

Die Kachel „Launches“ enthält alle Launches, die mit einem [Workflow für die Launch-Anforderung](/help/sites-cloud/authoring/projects/workflows.md) angefordert wurden.

![Launches](/help/sites-cloud/authoring/assets/project-launches.png)

### Aufgaben {#tasks}

Mithilfe von Aufgaben können Sie den Status aller projektbezogenen Aufgaben überwachen, einschließlich Workflows. Aufgaben werden im Detail unter [Arbeiten mit Aufgaben](/help/sites-cloud/authoring/projects/tasks.md) beschrieben.

![Aufgaben](/help/sites-cloud/authoring/assets/projects-tasks.png)

## Projektvorlagen {#project-templates}

Im Lieferumfang von AEM sind drei verschiedene Vorlagen enthalten:

* Ein einfaches Projekt: ein Referenzbeispiel für alle Projekte, die nicht in andere Kategorien passen (ein Allrounder). Es umfasst drei grundlegende Rollen (Inhaber, Bearbeiter und Beobachter) und vier Workflows (Projektbestätigung, Launch anfordern, Landingpage anfordern und E-Mail anfordern).
* Ein Medienprojekt: ein beispielhaftes Referenzprojekt für medienbezogene Aktivitäten. Es umfasst eine Reihe von medienbezogenen Projektrollen (Fotografen, Bearbeiter, Werbetexter, Designer, Inhaber und Beobachter). Es enthält auch den Workflow „Kopie anfordern“, um Text anzufordern und zu überprüfen.
* [Ein Übersetzungsprojekt](/help/sites-cloud/administering/translation/overview.md): ein beispielhaftes Referenzprojekt für die Verwaltung von übersetzungsbezogenen Aktivitäten. Es umfasst drei grundlegende Rollen (Inhaber, Bearbeiter und Beobachter). Es enthält zwei Workflows, auf die in der Workflow-Benutzeroberfläche zugegriffen werden kann.

Je nach ausgewählter Vorlage stehen Ihnen verschiedene Optionen für Benutzerrollen und Workflows zur Verfügung.

## Benutzerrollen in einem Projekt {#user-roles-in-a-project}

Die verschiedenen Benutzerrollen werden in einer Projektvorlage festgelegt und sind vor allem für die folgenden beiden Bereiche wichtig:

1. Berechtigungen. Die Benutzerrollen fallen in eine der drei genannten Kategorien: Beobachter, Bearbeiter, Inhaber. Ein Fotograf oder Werbetexter hat z. B. dieselben Berechtigungen wie ein Bearbeiter. Über die Berechtigungen wird festgelegt, inwiefern ein Benutzer Inhalte in einem Projekt ändern kann.
1. Workflows. Mit Workflows wird festgelegt, wem welche Aufgaben in einem Projekt zugewiesen sind. Die Aufgaben können einer Projektrolle zugeordnet werden. Beispielsweise kann der Rolle „Fotografen“ eine Aufgabe zugewiesen werden, sodass alle Team-Mitglieder mit dieser Rolle die Aufgabe erhalten.

Alle Projekte unterstützen die folgenden Standardrollen, mit denen Sie Sicherheits- und Kontrollberechtigungen verwalten können:

| Rolle | Beschreibung | Berechtigungen | Gruppenzugehörigkeit |
|---|---|---|---|
| Beobachter | Ein Benutzer mit dieser Rolle kann Projektdetails, einschließlich des Projektstatus, anzeigen. | Nur-Lese-Zugriff auf ein Projekt | `workflow-users`-Gruppe |
| Bearbeiter | Ein Benutzer mit dieser Rolle kann Inhalt in ein Projekt hochladen und Projektinhalte bearbeiten. | Lese- und Schreibzugriff auf ein Projekt, die zugehörigen Metadaten und Assets; Berechtigungen zum Hochladen einer Aufnahmenliste sowie zum Überprüfen und Genehmigen von Assets; Schreibberechtigung für „/etc/commerce“; Berechtigung zum Ändern für ein bestimmtes Projekt | Gruppe „workflow-users“ |
| Inhaber | Ein Benutzer mit dieser Rolle kann ein Projekt starten. Ein Inhaber kann ein Projekt erstellen, Arbeitsschritte in einem Projekt initiieren und genehmigte Assets in den Produktionsordner verschieben. Aber auch alle anderen Aufgaben im Projekt können vom Inhaber angezeigt und ausgeführt werden. | Schreibberechtigung für `/etc/commerce` | `dam-users`-Gruppe (um ein Projekt erstellen zu können) mit Projektadministratorengruppe (um ein Projekt erstellen und Assets verschieben zu können) |

>[!NOTE]
>
>Wenn Sie das Projekt erstellen und den verschiedenen Rollen Benutzer hinzufügen, werden mit dem Projekt verknüpfte Gruppen automatisch erstellt, um die zugehörigen Berechtigungen zu verwalten. Ein Projekt mit dem Namen Myproject könnte z. B. drei Gruppen **Myproject-Eigentümer**, **MyProject-Editor**, **MyProject-Beobachter** haben. Wird das Projekt jedoch gelöscht, werden diese Gruppen nicht automatisch gelöscht. Admins müssen die Gruppen unter **Tools** > **Sicherheit** > **Gruppen** manuell löschen.
