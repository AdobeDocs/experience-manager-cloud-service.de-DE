---
title: Veröffentlichen von Inhalten mit dem universellen Editor
description: Erfahren Sie, wie Inhalte mit dem universellen Editor veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
exl-id: aee34469-37c2-4571-806b-06c439a7524a
solution: Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 64c257adc7e1f22531c0fe45b44b27ab4e0badb8
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 56%

---


# Veröffentlichen von Inhalten mit dem universellen Editor {#publishing}

Erfahren Sie, wie Inhalte mit dem universellen Editor veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.

>[!TIP]
>
>Der hier beschriebene Veröffentlichungsprozess ist die standardmäßige vordefinierte Funktion des universellen Editors.
>
>Der universelle Editor unterstützt auch [Erweiterungen und UI-Erweiterbarkeit](/help/implementing/universal-editor/extending.md), damit Workflows Ihren Veröffentlichungsprozess unterstützen können, sodass Ihr Veröffentlichungsablauf variieren kann.

## Veröffentlichen von Inhalten über den universellen Editor {#publishing-content}

Wenn Sie als Inhaltsautor bereit sind, Ihre Inhalte zu veröffentlichen, müssen Sie einfach auf das Symbol **Veröffentlichen** in der Symbolleiste des universellen Editors tippen oder klicken.

![Veröffentlichen von Seiten](assets/publish-menu.png)

1. Tippen oder klicken Sie im universellen Editor auf [ Symbol **Veröffentlichen** in der Symbolleiste des universellen Editors.](/help/sites-cloud/authoring/universal-editor/navigation.md#publish)
1. Wenn ein [Vorschau-Service](/help/sites-cloud/authoring/sites-console/previewing-content.md) verfügbar ist, können Sie auswählen, wo Sie Ihre Inhalte veröffentlichen möchten, entweder **Vorschau** oder **Veröffentlichen**.
1. Im Abschnitt **Elemente** werden die Inhalte aufgelistet, die in der Veröffentlichung enthalten sind, einschließlich:
   * **Neu** Elemente, die noch nicht veröffentlicht wurden.
   * **Geändert** Inhalt, der veröffentlicht, aber seit der letzten Veröffentlichung geändert wurde.
   * **Veröffentlicht** Inhalte, die seit dieser Veröffentlichung veröffentlicht und nicht geändert wurden.

   Tippen oder klicken Sie auf die Kontrollkästchen neben den Elementen, um sie nach Bedarf in die Veröffentlichung einzubeziehen bzw. von ihr auszuschließen. Tippen oder klicken Sie auf **Erweitern**, um einzelne Elemente anzuzeigen, die in den Gesamtwerten für die drei Kategorien enthalten sind, und um sie einzeln ein- oder ausschließen zu können.

   ![Elemente veröffentlichen](assets/publish-items.png)

   Tippen oder klicken Sie auf den Pfeil nach hinten neben der Überschrift **Elemente**, um zur Übersicht zurückzukehren.

1. Tippen oder klicken Sie auf **Veröffentlichen**, um zu veröffentlichen, oder auf **Abbrechen**, um den Vorgang abzubrechen.

## Rückgängigmachen der Veröffentlichung von Inhalten im universellen Editor {#unpublishing-content}

Das Rückgängigmachen der Veröffentlichung von Inhalten funktioniert ähnlich wie das Veröffentlichen von Inhalten. Wenn Sie als Inhaltsautor bereit sind, Inhalte aus der Veröffentlichung zu entfernen, tippen oder klicken Sie auf das Symbol mit den Auslassungspunkten in der Symbolleiste des universellen Editors und dann **Veröffentlichung rückgängig machen**.

In diesem Fall haben Sie dieselben Optionen zum Rückgängigmachen der Veröffentlichung von Inhalten wie beim [Veröffentlichen von Inhalten“.](#publishing-content) einschließlich Rückgängigmachen der Veröffentlichung über eine Vorschauinstanz, falls verfügbar, und welche Elemente in die Rückgängigmachung der Veröffentlichung einbezogen werden sollen.

## Veröffentlichen und Rückgängigmachen der Veröffentlichung über die Sites-Konsole {#publishing-sites-console}

Sie können auch [über die Sites-Konsole) veröffentlichen](/help/sites-cloud/authoring/sites-console/publishing-pages.md) was nützlich sein kann, wenn Sie mehrere Inhaltsseiten veröffentlichen oder die Veröffentlichung oder das Rückgängigmachen der Veröffentlichung planen möchten.

## Ähnlichkeiten mit dem Seiteneditor {#similarities}

Für Benutzende des [AEM-Seiteneditors ](/help/sites-cloud/authoring/page-editor/introduction.md) der Prozess zum Veröffentlichen von Inhalten mit dem universellen Editor wie gewohnt: Bei der Veröffentlichung in AEM wird der Inhalt von der Autorenebene in die Veröffentlichungsebene repliziert.

## Unterschiede {#differences}

Was die Veröffentlichung mit dem universellen Editor geringfügig unterscheidet, ist nicht so sehr der Editor selbst, sondern vielmehr das externe Hosten der App, was durch den universellen Editor möglich gemacht wird.

Wenn die Web-App extern gehostet wird, muss sichergestellt werden, dass Inhalte von der Autorenebene geladen werden, wenn die App von Autorinnen oder Autoren im Editor geöffnet wird, und dass sie von der Veröffentlichungsebene geladen werden, wenn Besuchende auf die App zugreifen.

## Erkennen der Ebene in der App {#detecting}

Um zu bestimmen, ob auf die Autoren- oder Veröffentlichungsebene zugegriffen werden soll, können Sie durch eine einfache bedingte Anweisung in der App festlegen, dass der entsprechende Autoren- oder Veröffentlichungsendpunkt ausgewählt wird, wenn festgestellt wird, dass der Endpunkt im Editor geöffnet wird.

Eine andere Möglichkeit besteht darin, die App in zwei verschiedenen Umgebungen bereitzustellen, die unterschiedlich konfiguriert sind, sodass eine Umgebung ihren Inhalt von der Autorenebene und die andere Umgebung ihn von der Veröffentlichungsebene abruft. Damit Autorinnen und Autoren die veröffentlichte URL im universellen Editor öffnen können, kann ein kleines Skript erstellt werden, um die URL auf der Veröffentlichungsseite in die entsprechende URL in der Autorenumgebung zu „konvertieren“ (z. B. durch Voranstellen einer `author`-Sub-Domain), sodass die Autorinnen und Autoren automatisch umgeleitet werden.

## Zusammenfassung {#summary}

Ziel des universellen Editors ist es, kein bestimmtes Muster vorzuschreiben, damit die Implementierung ihre Ziele am besten vollständig entkoppelt erreichen kann und dabei alles für die Implementierung einfach und unkompliziert bleibt.

Gleichermaßen stellt der universelle Editor keine Anforderungen daran, wie ein bestimmtes Projekt die Bestimmung der Ebene durchführt, von der der Inhalt bereitgestellt werden soll. Stattdessen bietet er verschiedene Möglichkeiten und ermöglicht es dem Projekt, zu bestimmen, welche Lösung für seine eigenen Anforderungen am besten geeignet ist.

## Zusätzliche Ressourcen {#additional-resources}

Informationen zum Erstellen von Inhalten mit dem universellen Editor finden Sie in diesem Dokument.

* [Inhaltserstellung mit dem universellen Editor](authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.

Weitere Informationen zu den technischen Details zum universellen Editor finden Sie in diesen Entwicklerdokumenten.

* [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Erste Schritte mit dem universellen Editor in AEM](/help/implementing/universal-editor/getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](/help/implementing/universal-editor/architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](/help/implementing/universal-editor/attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](/help/implementing/universal-editor/authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
