---
title: Verwalten von Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Ihre Git-Repositorys in Cloud Manager hinzufügen, anzeigen und löschen.
exl-id: 6e1cf636-78f5-4270-9a21-38b4d5e5a0b0
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b35b25bcd62c28f7894171b7b2269fa46d612686
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 20%

---


# Repositorys in Cloud Manager verwalten {#managing-repos}

Erfahren Sie, wie Sie Ihre Git-Repositorys in Cloud Manager anzeigen, hinzufügen und löschen.

## Über Repositorys in Cloud Manager {#overview}

Repositorys in Cloud Manager werden zum Speichern und Verwalten des Projektcodes mithilfe von Git verwendet. Für jedes von Ihnen hinzugefügte *Programm* wird automatisch ein von Adobe verwaltetes Repository erstellt.

Darüber hinaus haben Sie die Möglichkeit, weitere von Adobe verwaltete Repositorys zu erstellen oder eigene private Repositorys hinzuzufügen. Alle mit Ihrem Programm verknüpften Repositorys können auf der Seite **Repositorys** angezeigt werden.

In Cloud Manager erstellte Repositorys können auch beim Hinzufügen oder Bearbeiten von Pipelines ausgewählt werden. Weitere Informationen zum Konfigurieren von Pipelines finden Sie unter [CI/CD Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

Jede Pipeline ist mit einem primären Repository oder einer Verzweigung verknüpft. Mit der Unterstützung von [Git-Untermodulen](git-submodules.md) können jedoch während des Build-Prozesses mehrere sekundäre Zweige einbezogen werden.

## Anzeigen der Seite &quot;Repositorys&quot; {#repositories-window}

Auf der Seite **Repositorys** können Sie Details zum ausgewählten Repository anzeigen. Diese Informationen enthalten den Typ des verwendeten Repositorys. Wenn das Repository als **Adobe** markiert ist, bedeutet dies, dass es sich um ein von Adobe verwaltetes Repository handelt. Wenn es als **GitHub** bezeichnet wird, bezieht es sich auf ein privates GitHub-Repository, das Sie verwalten. Darüber hinaus enthält die Seite Details wie den Zeitpunkt der Erstellung des Repositorys und die damit verbundenen Pipelines.

Um Aktionen für ein ausgewähltes Repository auszuführen, können Sie auf das Repository klicken und das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) verwenden, um ein Dropdown-Menü zu öffnen. Für von Adobe verwaltete Repositorys können Sie **[Verzweigungen überprüfen/Projekt erstellen](#check-branches)**.

![Repository-Aktionen](assets/repository-actions.png)
*Dropdown-Menü auf der Seite &quot;Repositorys&quot;.*

Weitere verfügbare Aktionen im Dropdown-Menü sind **[Repository-URL kopieren](#copy-url)**, **[Anzeigen und Aktualisieren](#view-update)** und **[Löschen](#delete)** des Repositorys.

**Anzeigen der Seite &quot;Repositorys&quot;:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie auf der Seite **Programmübersicht** im Seitenmenü auf das Symbol ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositorys**.

1. Auf der Seite **Repositorys** werden alle Repositorys angezeigt, die mit Ihrem ausgewählten Programm verknüpft sind.

   ![Seite &quot;Repositorys&quot;](assets/repositories.png)
   *Die Seite &quot;Repositorys&quot;in Cloud Manager.*

## Repository hinzufügen {#adding-repositories}

Ein Benutzer muss über die Rolle **Bereitstellungsmanager** oder **Business Owner** verfügen, um ein Repository hinzuzufügen.

Klicken Sie auf der Seite **Repositorys** in der rechten oberen Ecke auf **Repository hinzufügen** .

![Dialogfeld &quot;Repository hinzufügen&quot;.](assets/repository-add.png)
*Dialogfeld &quot;Repository hinzufügen&quot;.*

Cloud Manager unterstützt zwei Typen von Repositorys: Adobe-verwaltete Repositorys (**Adobe-Repository**) und selbstverwaltete Repositorys (**Privates Repository**). Die für die Einrichtung erforderlichen Felder variieren je nach dem Typ des Repositorys, das Sie hinzufügen möchten. Weitere Informationen finden Sie in den folgenden Themen:

* [Hinzufügen von Adobe-Repositorys in Cloud Manager](adobe-repositories.md)
* [Hinzufügen von privaten Repositorys in Cloud Manager](private-repositories.md)

Für jedes Unternehmen oder IMS-Organisation gibt es eine Grenze von 300 Repositorys über alle Programme hinweg.

## Auf Repository-Informationen zugreifen {#repo-info}

Wenn Sie sich Ihre Repositorys im Fenster **Repositorys** ansehen, können Sie die Details zum programmgesteuerten Zugriff auf die von Adobe verwalteten Repositorys anzeigen, indem Sie in der Symbolleiste auf die Schaltfläche **Auf Repository-Informationen zugreifen** klicken.

![Repository-Informationen](assets/repository-access-repo-info2.png)

Das Fenster **Repository-Informationen** mit den Details wird geöffnet. Weitere Informationen zum Zugreifen auf Repository-Informationen finden Sie unter [Zugriff auf Repository-Informationen](/help/implementing/cloud-manager/managing-code/accessing-repos.md).

## Verzweigungen überprüfen/Projekt erstellen {#check-branches}

In **AEM Cloud Manager** dient die Aktion **Verzweigungen überprüfen/Projekt erstellen** je nach dem aktuellen Status des Repositorys zwei Zwecken.

* Wenn das Repository neu erstellt wurde, generiert diese Aktion ein Beispielprojekt mit [dem AEM Projektarchetyp](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/developing/archetype/overview).
* Wenn das Beispielprojekt bereits im Repository erstellt wurde, prüft die Aktion den Status des Repositorys und seiner Verzweigungen und gibt Feedback dazu, ob das Beispielprojekt bereits vorhanden ist.

  ![Aktion „Verzweigungen überprüfen“](assets/check-branches.png)

## Repository-URL kopieren {#copy-url}

Mit der Aktion &quot;**Repository-URL kopieren**&quot;wird die URL des auf der Seite &quot;**Repositorys**&quot;ausgewählten Repositorys in die Zwischenablage kopiert, damit sie an anderer Stelle verwendet werden kann.

## Repository anzeigen und aktualisieren {#view-update}

Mit der Aktion **Anzeigen und Aktualisieren** wird das Dialogfeld **Repository aktualisieren** geöffnet, in dem Sie die Vorschau der Repository-URL **Name** und **Repository-URL-Vorschau** anzeigen können. Außerdem können Sie damit die **Beschreibung** des Repositorys aktualisieren.

![Anzeigen und Aktualisieren von Repository-Informationen](assets/repository-view-update.png)

## Repository löschen {#delete}

Die Aktion **Löschen** entfernt das Repository aus Ihrem Projekt. Ein Repository kann nicht gelöscht werden, wenn es mit einer Pipeline verknüpft ist.

![Löschen](assets/repository-delete.png)

Durch das Löschen eines Repositorys wird sein Name für alle zukünftigen Repositorys unbrauchbar. Wenn Sie versuchen, ein Repository mit demselben Namen wie ein gelöschtes Repository hinzuzufügen, wird die folgende Fehlermeldung angezeigt:

`Repository name should be unique within organization.`

Darüber hinaus ist das gelöschte Repository nicht mehr in Cloud Manager verfügbar und kann nicht mit Pipelines verknüpft werden.

