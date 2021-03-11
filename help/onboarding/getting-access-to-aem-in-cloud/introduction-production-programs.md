---
title: 'Einführung in die Produktions-Programme '
description: 'Einführung in die Produktions-Programme '
translation-type: tm+mt
source-git-commit: aa42ccf73a6be9050a06f9cbea0d16b80b039d89
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---


# Einführung in die Produktions-Programm {#production-programs}

Ein *Production*-Programm ist für einen Benutzer gedacht, der mit AEM und Cloud Manager vertraut ist und in der Lage ist, Beginn zum Schreiben, Erstellen und Testen von Code zu erstellen, um ihn in der Produktion bereitzustellen.

>[!NOTE]
>Sie können ein Produktions-Programm nicht löschen.

Ein Assistent zum Erstellen von Programmen hilft dem Benutzer, eine Auswahl zu treffen, je nachdem, welches Ziel der Benutzer beim Erstellen des Programms verfolgt. Basierend auf den nicht verwendeten Lösungsberechtigungen, die dem jeweiligen Kunden oder Unternehmen zur Verfügung stehen, hat der Benutzer die Kontrolle darüber, wie Sie verfügbare (nicht verwendete) Lösungsberechtigungen Cloud Manager-Programmen zuordnen.

## Überlegungen zur Erstellung von Programmen {#program-creation-considerations}

In der folgenden Tabelle werden gängige Szenarien beschrieben, die bei der Erstellung von Programmen in Cloud Manager berücksichtigt werden müssen:

| Nicht verwendete Lösungsberechtigungen im Org verfügbar | Optionen zum Erstellen von Programmen | Inhalt | Verwendungszweck und andere Aspekte |
|--- |--- |--- |--- |
| 1 Sitelösung | Programm &quot;Nur 1 Sites erstellen&quot; | 1 Produktion + 1 Stufe, 1 Entwicklung | nicht vorhanden |
| 1 Sites + 1 Sites | Erstellen Sie separate Programm: Nur 1 Sites Programm &amp; 1 Sites Programm | 1 Produktion + 1 Stufe, 1 Entwicklung 1 Produktion + 1 Stufe, 1 Entwicklung | Implementierungen von Sites mit mehreren Mandanten. Mehrere Sites mit einem eigenen Veröffentlichungsplan und dedizierten Entwicklungs- und Inhaltsteams. *Allgemeine Beispiele*: Zwei Handelsmarken mit eigenen Websites und separaten Entwicklungsteams |
| 1 Sites + 1 Assets | Ein Programm erstellen: 1 Site- und Assets-Programm | 1 Produktion + 1 Stufe, 2 Entwicklung | Die meisten digitalen Assets werden zur Unterstützung der Siteimplementierung verwendet. Die meisten digitalen Assets befinden sich in einem fertigen Zustand und können über Sites für die Nutzung über mehrere Kanal hinweg verwendet werden. Normalerweise ist ein einziges Team für die Verwaltung von Inhalten sowohl für Sites als auch für Assets zuständig. *Allgemeine Beispiele*: Bilder, die hauptsächlich für eine Website verwendet werden. PDFs, die über ein in AEM Sites erstelltes internes Portal verteilt werden. |
| 1 Sites + 1 Assets | Erstellen Sie separate Programm: Nur 1 Sites Programm &amp; 1 Assets Programm | 1 Produktion + 1 Stufe, 1 Entwicklung 1 Produktion + 1 Stufe, 1 Entwicklung | Viele digitale Assets unterstützen die Implementierung der Sites nicht direkt. Verwaltete Assets befinden sich in verschiedenen Status, einschließlich der Rohdateitypen, und funktionieren in Bearbeitung. Ein dediziertes Kreativteam verwaltet digitale Assets über seinen eigenen Lebenszyklus und verfügt über separate Workflows- und Veröffentlichungszyklen als das Sites-Content-Management-Team. *Allgemeine Beispiele*: Rohbilder aus einem Foto werden im Assets-Programm gespeichert und nur einige wenige werden in der Sites-Implementierung verwendet. Eine große Anzahl von Creative Cloud-Dateitypen, wie Photoshop und Illustrator, werden in AEM Assets verwaltet und durchlaufen ihren eigenen Genehmigungsvorgang, bevor ein fertiges Asset generiert wird. Zu nutzende Funktionen: [Verbundene Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html?lang=en#overview-of-connected-assets) |
| 1 Asset-Lösung | Programm &quot;Nur 1 Assets erstellen&quot; | 1 Produktion + 1 Stufe, 1 Entwicklung | nicht vorhanden |


