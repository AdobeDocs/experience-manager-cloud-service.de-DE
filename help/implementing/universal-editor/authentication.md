---
title: Authentifizierung beim universellen Editor
description: Erfahren Sie, wie der universelle Editor die Authentifizierung mit Adobe Identity Management System (IMS) durchführt.
exl-id: fb86c510-3c41-4511-81b7-1bdf2f5e7dd3
source-git-commit: 9d88d9b6d3315f34ca6819820b4b4306ba901390
workflow-type: tm+mt
source-wordcount: '332'
ht-degree: 100%

---


# Authentifizierung beim universellen Editor {#authentication}

Erfahren Sie, wie beim universellen Editor authentifiziert wird.

{{universal-editor-status}}

## Optionen {#options}

Der universelle Editor verwendet die IMS-Authentifizierung (Identity Management System) von Adobe, die über Unified Shell bereitgestellt wird.

Alle Anwendungen/Remote-Seiten sind für die Authentifizierung für erforderliche Backend-Systeme verantwortlich. Der universelle Editor-Dienst benötigt diese Authentifizierung, um Backend-Systeme für CRUD-Vorgänge durchzuführen, da es sich um einen eigenständigen Dienst handelt.

## Standardfluss {#standard-flow}

Dies ist die Lösung für AEM as a Cloud Service und AMS, die IMS verwenden, um den universellen Editor zu verwenden.

Um den universellen Editor zu verwenden, müssen Benutzende bei Unified Shell angemeldet sein, die sich gegenüber IMS authentifiziert. Das bereitgestellte IMS-Token wird im Sitzungsspeicher der Benutzenden gespeichert.

Wenn Benutzende einen CRUD-Vorgang ausführen, wird ein Aufruf an den universellen Editor-Dienst mit dem IMS-Bearer-Token im HTTP-Header gesendet. Der universelle Editor-Dienst verwendet dann das Bearer-Token, um die Anfrage gegenüber dem AEM Backend-System zu authentifizieren, um Vorgänge im Namen der Person auszuführen.

![Standard-Authentifizierungablauf](assets/standard-flow.png)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Inhaltserstellung mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/authoring.md) – Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](/help/sites-cloud/authoring/universal-editor/publishing.md) – Erfahren Sie, wie mit dem universellen Editor Inhalte veröffentlicht werden und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
