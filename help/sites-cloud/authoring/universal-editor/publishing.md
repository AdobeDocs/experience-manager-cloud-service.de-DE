---
title: Veröffentlichen von Inhalten mit dem universellen Editor
description: Erfahren Sie, wie Inhalte mit dem universellen Editor veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: c0714a7b74cd223ad4a405934c89a3146fb8b5c4
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 96%

---


# Veröffentlichen von Inhalten mit dem universellen Editor {#publishing}

Erfahren Sie, wie Inhalte mit dem universellen Editor veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.

>[!TIP]
>
>Der hier beschriebene Veröffentlichungsprozess ist die standardmäßige vordefinierte Funktion des universellen Editors.
>
>Der universelle Editor unterstützt auch [Erweiterungen und die Erweiterbarkeit der Benutzeroberfläche](/help/implementing/universal-editor/extending.md), damit Workflows Ihren Veröffentlichungsprozess unterstützen können, sodass Ihr Veröffentlichungsablauf variieren kann.

## Veröffentlichen von Inhalten aus dem universellen Editor {#publishing-content}

Wenn Sie nach dem Erstellen von Inhalten bereit sind, Ihre Inhalte zu veröffentlichen, brauchen Sie einfach nur auf das Symbol **Veröffentlichen** auf der Symbolleiste des universellen Editors zu tippen oder klicken.

![Veröffentlichen von Seiten](assets/publish-menu.png)

1. Tippen oder klicken Sie im universellen Editor auf das [Symbol **Veröffentlichen** auf der Symbolleiste des universellen Editors](/help/sites-cloud/authoring/universal-editor/navigation.md#publish).
1. Wenn ein [Vorschau-Service](/help/sites-cloud/authoring/sites-console/previewing-content.md) verfügbar ist, können Sie auswählen, wo Sie Ihre Inhalte veröffentlichen möchten, entweder als **[Vorschau](/help/sites-cloud/authoring/sites-console/previewing-content.md)** (falls verfügbar) oder zum **Veröffentlichen**.
1. Im Abschnitt **Elemente** werden die in der Veröffentlichung enthaltenen Inhalte aufgelistet. Tippen oder klicken Sie auf **Anzeigen**, um die Details anzuzeigen, darunter:
   * **Neue** Elemente, die noch nicht veröffentlicht wurden.
   * **Geänderte** Inhalte, die veröffentlicht, aber seit der letzten Veröffentlichung geändert wurden.
   * **Veröffentlichte** Inhalte, die veröffentlicht und seit dieser Veröffentlichung nicht geändert wurden.

   Tippen oder klicken Sie auf die Kontrollkästchen neben den Elementen, um sie nach Bedarf in die Veröffentlichung ein- bzw. von ihr auszuschließen. Tippen oder klicken Sie auf **Erweitern**, um die einzelnen Elemente anzuzeigen, die in den Elementen dieser drei Kategorien enthalten sind, und um sie einzeln ein- oder ausschließen zu können.

   ![Veröffentlichen von Elementen](assets/publish-items.png)

   Tippen oder klicken Sie auf den Pfeil nach links neben der Überschrift **Elemente**, um zur Übersicht zurückzukehren.

1. Tippen oder klicken Sie auf **Veröffentlichen**, um zu veröffentlichen, oder auf **Abbrechen**, um den Vorgang abzubrechen.

>[!NOTE]
>
>Die Option zum Veröffentlichen in der Vorschau [kann deaktiviert sein](/help/implementing/universal-editor/customizing.md#publish-preview) und wird daher möglicherweise nicht im Editor angezeigt.

## Aufheben der Veröffentlichung von Inhalten mit dem universellen Editor {#unpublishing-content}

Das Aufheben der Veröffentlichung von Inhalten funktioniert ähnlich wie das Veröffentlichen von Inhalten. Wenn Sie bereit sind, Inhalte aus der Veröffentlichung zu entfernen, tippen oder klicken Sie auf das Symbol mit den Auslassungspunkten auf der Symbolleiste des universellen Editors und dann auf **Veröffentlichung aufheben**.

Dann haben Sie dieselben Optionen zum Aufheben der Veröffentlichung von Inhalten wie beim [Veröffentlichen von Inhalten.](#publishing-content) Dazu gehört auch das Aufheben der Veröffentlichung über eine Vorschauinstanz, falls verfügbar, und das Festlegen der Elemente, die in das Aufheben der Veröffentlichung eingeschlossen werden sollen.

## Veröffentlichen und Aufheben der Veröffentlichung über die Sites-Konsole {#publishing-sites-console}

Sie können Inhalte auch [über die Sites-Konsole](/help/sites-cloud/authoring/sites-console/publishing-pages.md) veröffentlichen. Dies kann nützlich sein, wenn Sie mehrere Inhaltsseiten veröffentlichen oder die Veröffentlichung bzw. das Aufheben der Veröffentlichung planen möchten.

## Zusätzliche Ressourcen {#additional-resources}

Informationen zum Erstellen von Inhalten mit dem universellen Editor finden Sie in diesem Dokument.

* [Inhaltserstellung mit dem universellen Editor](authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.

Weitere Informationen zu den technischen Details zum universellen Editor finden Sie in diesen Entwicklerdokumenten.

* [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Erste Schritte mit dem universellen Editor in AEM](/help/implementing/universal-editor/getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](/help/implementing/universal-editor/architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](/help/implementing/universal-editor/attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](/help/implementing/universal-editor/authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
