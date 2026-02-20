---
title: Verwalten von Zugriffs-Token externer Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie Zugriffs-Token anzeigen, bearbeiten und löschen können, die für „Bring Your Own Git“ in AEM Cloud Manager verwendet werden.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: bc9f392c-61f5-4d39-972b-4c6c8f9bab4a
source-git-commit: 2ea076c42a6406548bf48cd246227fc8ddb3a080
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 94%

---

# Verwalten von Zugriffs-Token für externe Repositorys {#manage-access-tokens}

<!-- badge: label="Private beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#manage-access-tokens" -->

Cloud Manager verwendet Zugriffs-Token, um auf externen Git-Plattformen gehostete Repositorys zu verwalten. Wenn ein Token abgelaufen war, musste das zugehörige Repository zuvor neu integriert werden, um funktionsfähig zu bleiben.

Mit der Funktion &quot;**`Manage Access Tokens`**&quot; können Sie Token jetzt effizienter verwalten. Sie können Token anzeigen, umbenennen oder entfernen, die mit unterstützten externen Git-Anbietern wie GitHub Enterprise, GitLab, Bitbucket und Azure DevOps verbunden sind.

Siehe auch [Hinzufügen von externen Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/external-repositories.md).

## Anzeigen von Zugriffs-Token {#view-access-tokens}

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus, dessen Zugriffs-Token für „Bring Your Own Git“ Sie verwalten möchten.
1. Klicken Sie im Seitenmenü unter **Programm** auf ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_FolderOutline_18_N.svg) **Repositorys**.
1. Klicken Sie oben rechts auf der Seite auf **Zugriffs-Token verwalten**.

   Die Schaltfläche **Zugriffs-Token verwalten** ist nur sichtbar, wenn Ihr Programm die Funktion „Bring Your Own Git“ verwendet.

   ![Dialogfeld „Zugriffs-Token verwalten“ mit einem aktiven und einem inaktiven Token](/help/implementing/cloud-manager/managing-code/assets/access-tokens-manage.png)

1. Im Dialogfeld **Zugriffs-Token verwalten**:
   * Alle Zugriffs-Token werden aufgelistet.
   * Sie können jedes Zugriffs-Token **bearbeiten**.
   * Sie können nur diejenigen Zugriffs-Token **löschen**, die *derzeit nicht verwendet werden*. Wenn ein Token verwendet wird, ist die Schaltfläche ![Gliederungssymbol löschen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg) deaktiviert.

## Bearbeiten eines Zugriffs-Tokens {#edit-access-tokens}

1. Klicken Sie im Dialogfeld **Zugriffs-Token verwalten** rechts neben einem Token-Namen auf ![Bearbeiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg).
1. Aktualisieren Sie im Dialogfeld **Zugriffs-Token bearbeiten** den Wert **Token-Name** oder **Zugriffs-Token** oder beide.

   ![Dialogfeld „Zugriffstoken bearbeiten“](/help/implementing/cloud-manager/managing-code/assets/access-tokens-edit.png)

1. Wenn das **Zugriffs-Token** derzeit verwendet wird, werden Sie in einer Benachrichtigung darauf hingewiesen, dass alle zugehörigen Repositorys nach der Aktualisierung automatisch erneut validiert werden.

1. Klicken Sie auf **Aktualisieren**, um die Änderungen zu speichern.

## Löschen eines Zugriffs-Tokens {#delete-access-token}

1. Klicken Sie im Dialogfeld **Zugriffs-Token verwalten** rechts neben einem Token-Namen auf ![Löschsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg)

   Das Symbol ist für Token, die derzeit verwendet werden, deaktiviert (![Konturlöschsymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_DeleteOutline_18_N.svg)).

1. Klicken Sie im Dialogfeld &quot;**`Delete Access Token`**&quot; auf **Löschen**, um das Token dauerhaft zu entfernen.
