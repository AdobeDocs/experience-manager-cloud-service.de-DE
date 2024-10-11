---
title: Einführung in die Produktionsprogramme
description: Erfahren Sie, was Produktionsprogramme sind und wie Sie Ihres einrichten können.
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2573eb5f8a8ff21a8e30b94287b554885cd1cd89
workflow-type: tm+mt
source-wordcount: '485'
ht-degree: 89%

---


# Einführung in Produktionsprogramme {#production-programs}

Ein Produktionsprogramm ist für ein Team gedacht, das bereit ist, Code zu schreiben, zu erstellen und zu testen, um ihn für das Hosten von Live-Traffic bereitzustellen.

Nachdem Sie [Ihr Produktionsprogramm ](creating-production-programs.md) erstellt haben, führt ein [Assistent zur Programmerstellung](using-the-wizard.md) den Benutzer durch die Auswahl, je nach Ziel des Benutzers beim Erstellen des Programms.

## Optionen zur Programmerstellung {#program-creation-options}

Ihr Vertrag mit Adobe definiert die Anzahl und die Arten von Lösungen, die Ihrem Unternehmen bei der Erstellung von Produktionsprogrammen zur Verfügung stehen. Sie haben die Kontrolle darüber, wie Sie die verfügbaren Lösungen Cloud Manager-Programmen zuordnen.

In der folgenden Tabelle werden gängige Szenarien der verfügbaren Lösungen und die darauf basierenden typischen Produktionsprogramme beschrieben.

| Verfügbare Lösungen | Programmoptionen | Inhalt | Wann ist sie einzusetzen? | Beispiele |
|---------------------|-------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| 1 Sites-Lösung | Erstellen von 1 Nur-Sites-Programm | 1 Produktion + 1 Staging, 1 Entwicklung, 1 Schnelle Entwicklung | Nicht zutreffend | Nicht zutreffend |
| 1 Assets-Lösung | Erstellen von 1 Nur-Assets-Programm | 1 Produktion + 1 Staging, 1 Entwicklung, 1 Schnelle Entwicklung | Nicht zutreffend | Nicht zutreffend |
| 1 Sites + 1 Assets | Ein Programm erstellen: <br>1 Sites-und-Assets-Programm | 1 Produktion + 1 Staging, 2 Entwicklung, 2 Schnelle Entwicklung | Wenn die meisten digitalen Assets zur Unterstützung der Sites-Implementierung verwendet werden.<br>In solchen Fällen befinden sich die meisten digitalen Assets in einem fertigen Zustand, der für Cross-Channel-Erlebnisse über Sites verwendet werden kann.<br>In der Regel ist ein einzelnes Team für die Verwaltung von Inhalten sowohl für Sites als auch für Assets verantwortlich. | Bilder, die primär für eine Website verwendet werden.<br>Ein in AEM Sites erstelltes internes Portal verteilt PDF. |
| 1 Sites + 1 Assets | Separate Programme erstellen: <br>1 Nur-Sites-Programm und 1 Nur-Assets-Programm | 1 Produktion + 1 Staging, 1 Entwicklung, 1 Schnelle Entwicklung<br>1 Produktion + 1 Staging, 1 Entwicklung, 1 Schnelle Entwicklung | Wenn viele digitale Assets die Sites-Implementierung nicht direkt unterstützen.<br> In solchen Fällen befinden sich die Assets in verschiedenen Zuständen, darunter Rohdateien und in Bearbeitung befindlich.<br>Ein dediziertes Kreativ-Team verwaltet die digitalen Assets über den Lebenszyklus und verfügt über von denen des Sites-Content-Management-Teams getrennte Workflows und Freigabezyklen. | Rohbilder eines Foto-Shootings werden im Assets-Programm gespeichert, und nur einige wenige davon werden für die Sites-Implementierung verwendet.<br>Eine große Anzahl von Creative Cloud-Dateitypen, wie Photoshop und Illustrator, werden in AEM Assets verwaltet und durchlaufen ihren eigenen Genehmigungs-Workflow, bevor ein fertiges Asset generiert wird.<br>Erwägen Sie in solchen Fällen die Verwendung von [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md#overview-of-connected-assets). |
| 1 Sites + 1 Sites | Separate Programme erstellen:<br> 1 Nur-Sites-Programm und 1 Nur-Sites-Programm | 1 Produktion + 1 Staging, 1 Entwicklung, 1 Schnelle Entwicklung<br>1 Produktion + 1 Staging, 1 Entwicklung, 1 Schnelle Entwicklung | Für Implementierungen von Sites mit mehreren Mandanten.<br>In solchen Fällen müssen mehrere Sites mit einem eigenen Veröffentlichungszeitplan und dedizierten Entwicklungs- und Inhalts-Teams verwaltet werden. | Zwei Handelsmarken mit eigenen Websites und separaten Entwicklungs-Teams |


>[!NOTE]
>
>Produktionsprogramme [ können bearbeitet, aber nicht gelöscht werden](editing-programs.md).
