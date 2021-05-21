---
title: 'Einführung in die Produktionsprogramme '
description: Einführung in die Produktionsprogramme
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 100%

---

# Einführung in die Produktionsprogramme {#production-programs}

Ein *Produktionsprogramm* ist für einen Benutzer gedacht, der mit AEM und Cloud Manager vertraut ist und Code für die Produktion schreiben, erstellen und bereitstellen möchte.

>[!NOTE]
>Sie können ein Produktionsprogramm nicht löschen.

Ein Assistent für die Programmerstellung leitet den Benutzer bei der Auswahl an, je nachdem, welches Ziel der Benutzer mit der Erstellung des Programms verfolgt. Basierend auf den ungenutzten Lösungsberechtigungen, die dem spezifischen Kunden oder der Organisation zur Verfügung stehen, hat der Benutzer die Kontrolle darüber, wie die verfügbaren (ungenutzten) Lösungsberechtigungen den Cloud Manager-Programmen zugeordnet werden.

## Überlegungen zur Erstellung von Programmen {#program-creation-considerations}

In der folgenden Tabelle werden gängige Szenarien beschrieben, die bei der Erstellung von Programmen in Cloud Manager berücksichtigt werden müssen:

| Ungenutzte, in der Organisation verfügbare Lösungsberechtigungen | Optionen zum Erstellen von Programmen | Inhalt | Verwendungszweck und andere Überlegungen |
|--- |--- |--- |--- |
| 1 Sites-Lösung | Nur 1 Sites-Programm erstellen | 1 Produktion + 1 Staging, 1 Entwicklung | nicht vorhanden |
| 1 Assets-Lösung | Nur 1 Assets-Programm erstellen | 1 Produktion + 1 Staging, 1 Entwicklung | nicht vorhanden |
| 1 Sites + 1 Assets | Ein Programm erstellen: 1 Sites- und Assets-Programm | 1 Produktion + 1 Staging, 2 Entwicklung | Die meisten digitalen Assets werden zur Unterstützung der Sites-Implementierung verwendet. Die meisten digitalen Assets befinden sich in einem fertigen Zustand und können über Sites für kanalübergreifende Erlebnisse verwendet werden. Typischerweise ist ein einziges Team für die Verwaltung von Inhalten sowohl für Sites als auch für Assets zuständig. **Häufige Beispiele**: Bilder, die primär für eine Website verwendet werden. PDFs, die über ein in AEM Sites erstelltes internes Portal verteilt werden. |
| 1 Sites + 1 Assets | Separate Programme erstellen: Nur 1 Sites-Programm und 1 Assets-Programm | 1 Produktion + 1 Staging, 1 Entwicklung<br> 1 Produktion + 1 Staging, 1 Entwicklung | Viele digitale Assets unterstützen die Sites-Implementierung nicht direkt. Verwaltete Assets befinden sich in verschiedenen Status, einschließlich der Rohdateitypen, sich in Bearbeitung befindende Assets. Ein dediziertes Kreativ=Team verwaltet die digitalen Assets über den Lebenszyklus und verfügt über separate Workflows und Freigabezyklen als das Sites-Content-Management-Team. *Häufige Beispiele*: Rohbilder eines Fotoshootings werden im Assets-Programm gespeichert und nur einige wenige davon werden für die Sites-Implementierung verwendet. Eine große Anzahl von Creative Cloud-Dateitypen, wie Photoshop und Illustrator, werden in AEM Assets verwaltet und durchlaufen ihren eigenen Genehmigungs-Workflow, bevor ein fertiges Asset generiert wird. Zu nutzende Funktionen: [Connected Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html?lang=de#overview-of-connected-assets) |
| 1 Sites + 1 Sites | Separate Programme erstellen: Nur 1 Sites-Programm und 1 Sites-Programm | 1 Produktion + 1 Staging, 1 Entwicklung<br> 1 Produktion + 1 Staging, 1 Entwicklung | Sites-Implementierungen mit mehreren Mandanten. Mehrere Sites mit einem eigenen Veröffentlichungsplan und dedizierten Entwicklungs- und Inhalts-Teams. *Häufige Beispiele*: Zwei Handelsmarken mit eigenen Websites und separaten Entwicklungsteams |
