---
title: Erstellen von Komponenten
description: AEM-Komponenten werden verwendet, um den Inhalt, den Sie auf Ihren Web-Seiten bereitstellen, zu speichern, zu formatieren und zu rendern. Folgen Sie dieser Seite, um mehr über das Authoring von Kanälen und das Rendern von Komponenten zu erfahren.
source-git-commit: 34a072bd8e936a7cdf6c37ad7b3eea704d644fd9
workflow-type: tm+mt
source-wordcount: '289'
ht-degree: 100%

---


# Erstellen von Komponenten {#creating-components}

AEM-Komponenten werden verwendet, um den Inhalt, den Sie auf Ihren Web-Seiten bereitstellen, zu speichern, zu formatieren und zu rendern.

## Authoring von Kanälen {#authoring-channels}

Der Kanal ist das zentrale Objekt für Inhalte, die für eine Reihe von Displays bereitgestellt werden. Daher muss ein Inhaltsautor normalerweise einen Kanal im Editor öffnen, um Inhalt hinzuzufügen oder zu ändern. Da der Kanal eine ***cq:Page*** ist, folgt er demselben herkömmlichen UX-Muster zum Hinzufügen und Bearbeiten von Komponenten des Kanals.

Da jedoch Komponenten innerhalb eines Kanals normalerweise im Vollbildmodus gerendert werden, ist das Authoring bei der Bearbeitung von einzelnen Komponenten und dem Erstellen eines neuen Auftrags beeinträchtigt. Deshalb nutzt der Kanal Selektoren, um verschiedene Ansichten der Komponenten zu rendern. In der Authoring-Umgebung wird der Bearbeitungs-Selektor genutzt, um die benutzerdefinierte Kanalwiedergabe zu aktivieren.

Beispiel: `http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html](http://localhost:4502/editor.html/content/screens/we-retail/channels/idle.edit.html`

Der Benutzer muss sich während des Bearbeitens nicht um das Hinzufügen des Selektors zur URL kümmern. Eine Client-seitige Logik wartet auf das Ebenen-Wechselereignis und fügt den Selektor hinzu, wenn der Kanal den dedizierten Ressourcentyp *screens/core/components/channel* aufweist.

## Rendern von Komponenten {#rendering-components}

Um eine korrekte Inhaltserstellung zu ermöglichen, müssen die Komponenten die folgenden beiden Wiedergaben bereitstellen:

| **Komponente** | **Wiedergaben** |
|---|---|
| *my-component/my-component.html* | Produktionswiedergabe |
| *my-component/edit.html* | Bearbeiten der Wiedergabe in einer kleineren Ansicht |

Die integrierten Komponenten nutzen die folgenden Client-Bibliothekskategorien:

| **Komponente** | **Client-Bibliothek** |
|---|---|
| *cq.screens.components.edit* | CSS und JS, die bei der Inhaltserstellung geladen werden müssen |
| *cq.screens.components.production* | CSS und JS, die geladen werden müssen, wenn der Kanal ausgeführt wird |
| *cq.screens.components* | freigegebene CSS und JS |

>[!NOTE]
>
>Um eigene Komponenten zu entwickeln, verwenden Sie die ***[Beispielvorlage für AEM Screens-Komponenten](https://github.com/Adobe-Marketing-Cloud/aem-screens-component-template)***.
