---
title: Universelle Editor-Authentifizierung
description: Erfahren Sie, wie der universelle Editor authentifiziert wird.
source-git-commit: 0e66c379e10d275610d85a699da272dc0c32a9a8
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 0%

---


# Universelle Editor-Authentifizierung {#authentication}

Erfahren Sie, wie der universelle Editor authentifiziert wird.

## Optionen {#options}

Der Universal Editor verwendet die IMS-Authentifizierung (Identity Management System) der Adobe, die über die Unified Shell bereitgestellt wird.

Alle Anwendungen/Remote-Seiten sind für die Authentifizierung für erforderliche Backend-Systeme verantwortlich. Der Universal Editor-Dienst benötigt diese Authentifizierung, um Backend-Systeme für CRUD-Vorgänge durchzuführen, da es sich um einen eigenständigen Dienst handelt.

## Standardfluss {#standard-flow}

Dies ist die Lösung für AEM as a Cloud Service und AMS, die IMS verwenden, um den universellen Editor zu verwenden.

Um den universellen Editor zu verwenden, muss der Benutzer bei der Unified Shell angemeldet sein, die sich für IMS authentifiziert. Das bereitgestellte IMS-Token wird im Sitzungsspeicher der Benutzer gespeichert.

Wenn ein Benutzer einen CRUD-Vorgang ausführt, wird ein Aufruf an den Universal Editor-Dienst mit dem IMS-Trägertoken im HTTP-Header gesendet. Der Universal Editor-Dienst verwendet dann das Trägertoken, um die Anfrage gegen das AEM Backend-System zu authentifizieren, um Vorgänge im Benutzernamen auszuführen.

![Standardauthentifizierungsfluss](assets/standard-flow.png)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) - Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Inhaltserstellung mit dem universellen Editor](authoring.md) - Erfahren Sie, wie einfach und intuitiv es für Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.
* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) - Erfahren Sie, wie der universelle Visual Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) - Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](architecture.md) - Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](attributes-types.md) - Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
