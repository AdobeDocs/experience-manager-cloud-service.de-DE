---
title: Veröffentlichen von Inhalten mit dem Seiteneditor
description: Erfahren Sie, wie der Seiteneditor Inhalte veröffentlicht.
solution: Experience Manager Sites
feature: Authoring
role: User
exl-id: dc11ac02-2a8d-4d82-ae10-e0fb97025063
source-git-commit: 0fcdea7803110156d589ab6bbf960373f212747d
workflow-type: ht
source-wordcount: '345'
ht-degree: 100%

---

# Veröffentlichen von Inhalten mit dem Sites-Editor {#publishing}

Erfahren Sie, wie der Seiteneditor Inhalte veröffentlicht.

## Veröffentlichen vom Seiteneditor aus {#publishing-from-the-page-editor}

Wenn Sie eine Seite im [Seiteneditor](/help/sites-cloud/authoring/page-editor/introduction.md) bearbeiten, kann sie direkt im Editor veröffentlicht werden.

1. Wählen Sie das Symbol **Seiteninformationen** aus, um das Menü zu öffnen, und danach die Option **Seite veröffentlichen**.

   ![Veröffentlichen einer Seite über Seitenoptionen](/help/sites-cloud/authoring/assets/publishing-page-options.png)

1. Je nachdem, ob die Seite Verweise enthält, die veröffentlicht werden müssen, geschieht Folgendes:

   * Die Seite wird direkt veröffentlicht, wenn keine Verweise veröffentlicht werden müssen.
   * Wenn die Seite dagegen Verweise enthält, die veröffentlicht werden müssen, werden diese im **Veröffentlichungsassistenten** aufgeführt, und Sie können eine der folgenden Aktionen ausführen:
      * Geben Sie an, welche Assets, Tags usw. Sie mit der Seite veröffentlichen möchten, und wählen Sie **Veröffentlichen**, um den Vorgang abzuschließen.
      * Mit **Abbrechen** können Sie den Vorgang abbrechen.

   ![Veröffentlichen von Verweisen mit der Seite](/help/sites-cloud/authoring/assets/publishing-references.png)

1. Mit **Veröffentlichen** wird die Seite in der Veröffentlichungsumgebung repliziert. Im Seiteneditor wird ein Banner mit einem Hinweis angezeigt, in dem die Veröffentlichung bestätigt wird.

   ![Statusinfo-Banner veröffentlichen](/help/sites-cloud/authoring/assets/publishing-info.png)

   Wird diese Seite in der Konsole dargestellt, ist der aktualisierte Veröffentlichungsstatus sichtbar.

   ![Status der Seitenveröffentlichung in der Spaltenansicht in der Site-Konsole](/help/sites-cloud/authoring/assets/publishing-status-console-column.png)

>[!NOTE]
>
>Mit dem Seiteneditor kann nur eine teilweise Veröffentlichung vorgenommen werden, d. h. nur die ausgewählten Seiten werden veröffentlicht, aber keine untergeordneten Seiten.

>[!NOTE]
>
>Seiten, auf die im Editor über [Aliasnamen](/help/sites-cloud/authoring/sites-console/page-properties.md#advanced) zugegriffen wird, können nicht veröffentlicht werden. Veröffentlichungsoptionen im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.

## Rückgängigmachen von Veröffentlichungen im Seiteneditor {#unpublishing}

Wenn Sie bei der Bearbeitung einer Seite im Seiteneditor die Veröffentlichung dieser Seite rückgängig machen möchten, wählen Sie analog zur [Veröffentlichung einer Seite](#publishing-from-the-editor) im Menü **Seiteninformationen** die Option **Veröffentlichung der Seite rückgängig machen** aus.

>[!NOTE]
>
>Die Veröffentlichung von Seiten, auf die im Editor über [Aliasnamen](/help/sites-cloud/authoring/sites-console/page-properties.md#advanced) zugegriffen wird, kann nicht rückgängig gemacht werden. Veröffentlichungsoptionen im Editor sind nur für Seiten verfügbar, auf die über ihre tatsächlichen Pfade zugegriffen wird.

## Veröffentlichen und Aufheben der Veröffentlichung über die Sites-Konsole {#publishing-sites-console}

Sie können Inhalte auch [über die Sites-Konsole](/help/sites-cloud/authoring/sites-console/publishing-pages.md) veröffentlichen. Dies kann nützlich sein, wenn Sie mehrere Inhaltsseiten veröffentlichen oder die Veröffentlichung bzw. das Aufheben der Veröffentlichung planen möchten.
