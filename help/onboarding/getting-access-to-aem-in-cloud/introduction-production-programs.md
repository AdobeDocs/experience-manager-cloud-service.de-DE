---
title: 'Einführung in Produktionsprogramme '
description: Einführung in Produktionsprogramme
exl-id: bb8d4a5a-b26a-4718-9327-149fedb87e6a
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '422'
ht-degree: 0%

---

# Einführung in Produktionsprogramme {#production-programs}

Ein *Production*-Programm ist für Benutzer gedacht, die mit AEM und Cloud Manager vertraut sind und mit dem Schreiben, Erstellen und Testen von Code beginnen können, um ihn in der Produktion bereitzustellen.

>[!NOTE]
>Sie können ein Produktionsprogramm nicht löschen.

Ein Assistent zur Programmerstellung führt den Benutzer je nach Ziel des Benutzers bei der Programmerstellung zu einer Auswahl. Basierend auf den nicht verwendeten Lösungsberechtigungen, die dem jeweiligen Kunden oder der Organisation zur Verfügung stehen, hat der Benutzer die Kontrolle darüber, wie verfügbare (nicht verwendete) Lösungsberechtigungen Cloud Manager-Programmen zugeordnet werden.

## Überlegungen zur Programmerstellung {#program-creation-considerations}

In der folgenden Tabelle werden gängige Szenarien beschrieben, die bei der Erstellung von Programmen in Cloud Manager berücksichtigt werden müssen:

| Nicht verwendete Lösungsberechtigungen in der Organisation verfügbar | Programmoptionen erstellen | Was ist enthalten? | Verwendung und andere Aspekte |
|--- |--- |--- |--- |
| 1 Sites-Lösung | Programm &quot;Nur 1 Sites erstellen&quot; | 1 Produktion + 1 Staging, 1 Entwicklung | nicht vorhanden |
| 1 Assets-Lösung | Nur Programm &quot;1 Assets erstellen&quot; | 1 Produktion + 1 Staging, 1 Entwicklung | nicht vorhanden |
| 1 Sites +1 Assets | Erstellen eines Programms: 1 Sites &amp; Assets-Programm | 1 Produktion + 1 Staging, 2 Entwicklung | Die meisten digitalen Assets werden zur Unterstützung der Sites-Implementierung verwendet. Die meisten digitalen Assets sind fertig und können über Sites für kanalübergreifende Erlebnisse verwendet werden. In der Regel ist ein einzelnes Team für die Verwaltung von Inhalten für Sites und Assets verantwortlich. **Allgemeine Beispiele**: Bilder, die hauptsächlich für eine Website verwendet werden. PDFs, die über ein in AEM Sites erstelltes internes Portal verteilt werden. |
| 1 Sites +1 Assets | Erstellen Sie separate Programme: Nur 1 Sites Programm &amp; 1 Nur Assets Programm | 1 Produktion + 1 Staging, 1 Entwicklung<br> 1 Produktion + 1 Staging, 1 Entwicklung | Viele digitale Assets unterstützen die Sites-Implementierung nicht direkt. Die verwalteten Assets befinden sich in verschiedenen Status, einschließlich der Rohdateitypen und der laufenden Arbeiten. Ein dediziertes Kreativ-Team verwaltet digitale Assets über seinen eigenen Lebenszyklus und verfügt über separate Workflows und Veröffentlichungszyklen als das Sites Content Management-Team. *Allgemeine Beispiele*: Rohbilder aus einem Foto-Shooting werden im Assets-Programm gespeichert und in der Sites-Implementierung werden nur ausgewählte Bilder verwendet. Eine große Anzahl von Creative Cloud-Dateitypen wie Photoshop und Illustrator werden in AEM Assets verwaltet und durchlaufen ihren eigenen Genehmigungs-Workflow, bevor ein fertiges Asset generiert wird. Zu nutzende Funktionen: [Connected Assets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/admin/use-assets-across-connected-assets-instances.html?lang=en#overview-of-connected-assets) |
| 1 Sites + 1 Sites | Erstellen Sie separate Programme: Nur 1 Sites Programm &amp; 1 Sites Programm | 1 Produktion + 1 Staging, 1 Entwicklung<br>1 Produktion + 1 Staging, 1 Entwicklung | Implementierungen von Sites mit mehreren Mandanten. Mehrere Sites mit einem eigenen Veröffentlichungszeitplan und dedizierten Entwicklungs- und Inhaltsteams. *Allgemeine Beispiele*: Zwei Einzelhandelsmarken mit eigenen Websites und separaten Entwicklungsteams |
