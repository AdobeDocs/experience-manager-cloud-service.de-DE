---
title: 'Einführung in die Produktionsprogramme '
description: Erfahren Sie, was Produktionsprogramme sind und wie Sie Ihre einrichten können.
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
source-git-commit: a6152a1529b5c70bcf056857204e7ff97fc614e4
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 21%

---


# Einführung in die Produktionsprogramme {#production-programs}

Ein Produktionsprogramm ist für ein Team gedacht, das bereit ist, Code zu schreiben, zu erstellen und zu testen, um ihn für das Hosten von Live-Traffic bereitzustellen.

Nach [Erstellen Ihres Produktionsprogramms,](creating-production-programs.md) a [Assistent zur Programmerstellung](using-the-wizard.md) führt den Benutzer durch die Auswahl, abhängig vom Ziel des Benutzers bei der Erstellung des Programms.

## Optionen zur Programmerstellung {#program-creation-options}

Ihr Vertrag mit Adobe definiert die Anzahl und die Arten von Lösungen, die Ihrem Unternehmen bei der Erstellung von Produktionsprogrammen zur Verfügung stehen. Sie haben die Kontrolle darüber, wie Sie die verfügbaren Lösungen Cloud Manager-Programmen zuordnen.

In der folgenden Tabelle werden gängige Szenarien der verfügbaren Lösungen und die darauf basierenden typischen Produktionsprogramme beschrieben.

| Verfügbare Lösungen | Programmoptionen | Inhalt | Verwendungsbereiche | Beispiele |
|--- |--- |--- |--- |---|
| 1 Sites-Lösung | Programm &quot;Nur 1 Sites erstellen&quot; | 1 Produktion + 1 Staging, 1 Entwicklung | Nicht zutreffend | Nicht zutreffend |
| 1 Assets-Lösung | Programm &quot;Nur 1 Assets erstellen&quot; | 1 Produktion + 1 Staging, 1 Entwicklung | Nicht zutreffend | Nicht zutreffend |
| 1 Sites + 1 Assets | Erstellen Sie ein Programm: <br>1 Sites &amp; Assets-Programm | 1 Produktion + 1 Staging, 2 Entwicklung | Wenn ein Großteil der digitalen Assets zur Unterstützung der Sites-Implementierung verwendet wird.<br>In solchen Fällen befinden sich die meisten digitalen Assets in einem fertigen Zustand, der für kanalübergreifende Erlebnisse über Sites verwendet werden kann.<br>In der Regel ist ein einzelnes Team für die Verwaltung von Inhalten sowohl für Sites als auch für Assets verantwortlich. | Bilder, die hauptsächlich für eine Website verwendet werden.<br>PDFs, die über ein in AEM Sites erstelltes internes Portal verteilt werden. |
| 1 Sites + 1 Assets | Erstellen Sie separate Programme:<br>Nur 1 Sites Programm &amp; 1 Nur Assets Programm | 1 Produktion + 1 Staging, 1 Entwicklung<br> 1 Produktion + 1 Staging, 1 Entwicklung | Wenn viele digitale Assets die Sites-Implementierung nicht direkt unterstützen.<br> In solchen Fällen befinden sich Assets in verschiedenen Status, einschließlich der Rohdateitypen und der laufenden Arbeiten.<br>Ein dediziertes Kreativ-Team verwaltet digitale Assets über seinen eigenen Lebenszyklus und verfügt über separate Workflows und Veröffentlichungszyklen als das Sites Content Management-Team. | Rohbilder aus einem Foto-Shooting werden im Assets-Programm gespeichert und in der Sites-Implementierung werden nur ausgewählte Bilder verwendet.<br>Eine große Anzahl von Creative Cloud-Dateitypen, wie Photoshop und Illustrator, werden in AEM Assets verwaltet und durchlaufen ihren eigenen Genehmigungs-Workflow, bevor ein fertiges Asset generiert wird.<br>Erwägen Sie die Verwendung von [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md#overview-of-connected-assets) in solchen Fällen. |
| 1 Sites + 1 Sites | Erstellen Sie separate Programme:<br>Nur 1 Sites Programm &amp; 1 Sites Programm | 1 Produktion + 1 Staging, 1 Entwicklung<br> 1 Produktion + 1 Staging, 1 Entwicklung | Für Sites mit mehreren Mandanten.<br>In solchen Fällen müssen mehrere Sites mit einem eigenen Veröffentlichungszeitplan und dedizierten Entwicklungs- und Inhaltsteams verwaltet werden. | Zwei Einzelhandelsmarken mit eigenen Websites und separaten Entwicklungsteams |

>[!NOTE]
>
>Produktionsprogramme [kann bearbeitet werden, nicht gelöscht werden.](editing-programs.md)
