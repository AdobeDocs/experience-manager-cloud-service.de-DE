---
title: Best Practices für MSM
description: Lernen Sie die Best Practices kennen, die von Adobe-Engineering- und Beratungsteams zusammengestellt werden, um den AEM Multi-Site-Manager einzurichten und zu nutzen.
feature: Multi-Site-Manager
role: Administrator
exl-id: 61b8ded8-3b9e-423f-85a9-7280e1a721cc
source-git-commit: 184de9c1391ade3abbf2c6d73f09a324e6fa7e3e
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 34%

---

# Best Practices für MSM {#msm-best-practices}

## Allgemein {#general}

MSM ist ein konfigurierbares Framework für die Automatisierung der Inhaltsbereitstellung. Implementierungen umfassen häufig große Teile einer Website und erstrecken sich über Organisationen und geografische Regionen. Es wird daher dringend empfohlen, MSM-Implementierungen mit der gleichen Sorgfalt zu planen wie Ihre Website:

* Sorgfältig **Planen Sie Struktur und Inhaltsflüsse**, bevor Sie mit der Implementierung beginnen.
* **Beschränken Sie Anpassungen auf das Nötigste.** MSM unterstützt zwar ein hohes Maß an Anpassung (z. B. Rollout-Konfigurationen), aber die Best Practice für die Leistung, Zuverlässigkeit und Upgrade Ihrer Website besteht normalerweise darin, die Anpassung zu minimieren.
* Richten Sie frühzeitig ein **Governance**-Modell ein und trainieren Sie Benutzer entsprechend, um Erfolg zu gewährleisten. Eine Best Practice aus Governance-Sicht besteht darin, **die Autorität zu minimieren, die lokale Inhaltsersteller haben**, um Inhalte anderen lokalen Benutzern und ihren jeweiligen Live Copies zuzuordnen/zu verbinden. Dies liegt daran, dass nicht verwaltete, verkettete Vererbungen die Komplexität einer MSM-Struktur erheblich erhöhen und ihre Leistung und Zuverlässigkeit beeinträchtigen können.
* Sobald ein Plan für Ihre Struktur, Inhaltsflüsse, Automatisierung und Governance vorhanden ist, können Sie den Prototyp **erstellen und Ihr System** gründlich testen, bevor Sie mit einer Live-Implementierung beginnen.
* Beachten Sie, dass **Adobe Consulting und führende Systemintegratoren** über umfassende Erfahrung bei der Planung und Implementierung der Inhaltsautomatisierung mit MSM verfügen, sodass sie Ihnen sowohl bei den ersten Schritten mit Ihrem MSM-Projekt als auch während der gesamten Implementierung helfen können.

## Live Copy-Quellen und Blueprint-Konfigurationen {#live-copy-sources-and-blueprint-configurations}

Beachten Sie, dass eine Live Copy entweder mit [normalen Seiten](creating-live-copies.md#creating-a-live-copy-of-a-page) oder mit einer [Blueprint-Konfiguration](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) erstellt werden kann. Beide Varianten sind zulässig.

Die Verwendung einer Blueprint-Konfiguration hat allerdings folgende Vorteile:

* Erlauben Sie dem Autor, die Option **Rollout** auf einem Blueprint zu verwenden, um explizit Änderungen an Live Copies zu übertragen, die von diesem Blueprint erben.
* Erlauben Sie dem Autor, **Site erstellen** zu verwenden, um Sprachen einfach auszuwählen und die Struktur der Live Copy zu konfigurieren.
* Definieren Sie eine standardmäßige Rollout-Konfiguration für Live Copies, die eine Beziehung zum Blueprint haben.

Wenn keine Blueprint-Konfiguration referenziert wird, können Rollouts nur von den Live Copies selbst initiiert werden, wodurch Inhalte im Wesentlichen aus der Quelle abgerufen werden.

Bei der Erstellung einer neuen Site mit Live Copy ist es von Vorteil, Blueprint-Konfigurationen zu erstellen, um die Verfügbarkeit des vollständigen MSM-Funktionssatzes sicherzustellen.

>[!NOTE]
>
> Beachten Sie, dass CUGs auf der Registerkarte &quot;Berechtigungen&quot;nicht für Live Copies aus Blueprints bereitgestellt werden können. Planen Sie dies ein, wenn Sie eine Live Copy konfigurieren.

## Komponenten- und Containersynchronisierung {#components-and-container-synchronization}

Für die Synchronisierung von Komponenten gilt in MSM im Allgemeinen folgende Rollout-Regel:

* Beim Rollout der Komponenten werden alle im Blueprint enthaltenen Ressourcen synchronisiert.
* Container synchronisieren nur die aktuelle Ressource.

Das bedeutet, dass Komponenten als Aggregat behandelt und bei einem Rollout die Komponente selbst und alle ihre untergeordneten Elemente durch die Elemente aus den Blueprints ersetzt werden. Wenn also eine Ressource einer solchen Komponente lokal hinzugefügt wird, geht sie beim Rollout des Blueprints verloren.

Um die Schachtelung von Komponenten zu unterstützen, sodass lokal hinzugefügte Komponenten bei einem Rollout erhalten bleiben, muss die Komponente als Container deklariert werden.

>[!NOTE]
>
>Fügen Sie der Komponente die Eigenschaft `cq:isContainer` hinzu, um sie als Container zu kennzeichnen.

## Erstellen einer Website {#create-site}

Beachten Sie, dass AEM zwei Hauptansätze zum Erstellen von Live Copies hat:

* Wenn Sie [eine Live Copy erstellen](creating-live-copies.md#creating-a-live-copy-of-a-page) - Dies kann als allgemeiner Ansatz betrachtet werden, der es Ihnen ermöglicht, Live Copies von jeder Seite aus zu erstellen. Die Inhaltsstruktur einer Live Copy stimmt genau mit der Quelle überein.

* Wenn [eine Site](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) erstellt wird - Dies ist ein speziellerer Ansatz, vor allem zum Erstellen von Websites mit einer mehrsprachigen Struktur.

Beachten Sie beim Erstellen einer Site die folgenden Punkte:

* Für die Erstellung einer neuen Website benötigen Sie eine [Blueprint-Konfiguration](creating-live-copies.md#managing-blueprint-configurations).
* Damit Sprachpfade in einer neuen Site erstellt werden können, müssen die entsprechenden Sprachstämme im Blueprint (Quelle) vorhanden sein.
* Nachdem eine [neue Site als Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) erstellt wurde (mit **Erstellen** und **Site**), sind die ersten beiden Ebenen dieser Live Copy *flach*. Untergeordnete Elemente der Seite sind nicht Teil der Live-Beziehung, werden bei einem Rollout aber trotzdem berücksichtigt, wenn eine dem Auslöser entsprechende Live-Beziehung gefunden wird.

Es ist hilfreich, Folgendes zu vermeiden:

* Manuelles Hinzufügen von Sprachen im Blueprint (unterhalb der ersten Ebene).
* Manuelles Hinzufügen von Inhalten direkt unterhalb des Sprachstamms, da dies nicht dazu führt, dass dieser neue Inhalt beim Rollout automatisch in die Live Copy übertragen wird.

## MSM und mehrsprachige Websites {#msm-and-multilingual-websites}

MSM kann Sie auf zwei Arten beim Erstellen mehrsprachiger Websites unterstützen:

Beachten Sie beim Erstellen von Sprach-Mastern Folgendes:

* MSM bietet zwar selbst **keine Inhaltsübersetzung**, kann jedoch mit entsprechenden Übersetzungs-Connectors von Dritten integriert werden. Beachten Sie Folgendes:
   * Mit MSM können Sie die Vererbung auf Seiten- und/oder Komponentenebene abbrechen. Dadurch wird verhindert, dass übersetzte Inhalte (aus einer Live Copy mit noch nicht übersetzten Inhalten aus einem Blueprint) beim nächsten Rollout überschrieben werden.
      * Einige Übersetzungs-Connectors von Dritten bieten eine automatisierte Verwaltung der MSM-Vererbung.
      * Weitere Informationen erhalten Sie von Ihrem Übersetzungsdienstleister.
      * Eine Alternative für die Erstellung und Übersetzung von Sprach-Mastern ist die Verwendung von Sprachkopien in Verbindung mit dem vorgefertigten AEM-Framework für die Übersetzungsintegration.

Weitere Informationen finden Sie unter [Übersetzen von Inhalt für mehrsprachige Websites](/help/sites-cloud/administering/translation/overview.md) und in den [Best Practices zur Übersetzung.](/help/sites-cloud/administering/translation/best-practices.md)

## Strukturänderungen und Rollouts {#structure-changes-and-rollouts}

Änderungen an der Inhaltsstruktur in einem Blueprint/einer Quellstruktur werden in einer Live Copy unterschiedlich dargestellt. Dies ist abhängig von der Art der Änderung:

* **** Das Erstellen neuer Seiten in einem Blueprint führt dazu, dass entsprechende Seiten in Live Copies nach dem Rollout mit der standardmäßigen Rollout-Konfiguration erstellt werden.
* **** Das Löschen von Seiten in einem Blueprint führt dazu, dass die entsprechenden Seiten nach dem Rollout mit der standardmäßigen Rollout-Konfiguration aus den Live Copies gelöscht werden.
* **** Das Verschieben von Seiten in einen Blueprint führt  **** nicht dazu, dass entsprechende Seiten nach dem Rollout mit der standardmäßigen Rollout-Konfiguration in Live Copies verschoben werden:
   * Der Grund: Eine Seitenverschiebung beinhaltet implizit eine Seitenlöschung. Dies kann möglicherweise zu unerwartetem Verhalten bei der Veröffentlichung führen, da beim Löschen von Seiten auf der Autoreninstanz der entsprechende Inhalt bei der Veröffentlichung automatisch deaktiviert wird. Dies kann sich auch auf verwandte Elemente wie Links, Lesezeichen und andere auswirken.
      * Die Inhaltsvererbung auf den entsprechenden Live Copy-Seiten wird aktualisiert, um den neuen Speicherort ihrer Quellen im Blueprint widerzuspiegeln.
      * Um einen Seitenwechsel von einem Blueprint zu Live Copies vollständig zu realisieren, beachten Sie die Best Practices für Seitenverschiebungen.](#page-move)[

### Best Practices für Seitenverschiebungen {#page-move}

Beachten Sie beim Verschieben von Seiten in eine Live Copy die folgende Best Practice.

>[!NOTE]
>
>Folgendes funktioniert nur mit dem Trigger [Bei Rollout](live-copy-sync-config.md#rollout-triggers).

1. Erstellen Sie eine benutzerdefinierte Rollout-Konfiguration.
   * Diese neue Konfiguration muss die Aktion `PageMoveAction` enthalten.
   * Fügen Sie dieser Konfiguration keine weiteren Aktionen hinzu.
1. Positionieren Sie die neue Konfiguration.
   * Um die Seitenverschiebung vollständig auszuführen, während Sie die entsprechenden Seiten an ihrem alten Speicherort in der Live Copy löschen:
      * Positionieren Sie die neu erstellte Konfiguration vor der standardmäßigen Rollout-Konfiguration. Die standardmäßige Rollout-Konfiguration sorgt dafür, dass die Seiten an ihren alten Speicherorten gelöscht werden.
      * So führen Sie die Seitenverschiebung durch und behalten dabei die entsprechenden Seiten an ihren alten Positionen in den Live Copies bei (im Wesentlichen Duplizieren des Inhalts):
         * Positionieren Sie die neu erstellte Konfiguration nach der standardmäßigen Rollout-Konfiguration. Dadurch wird sichergestellt, dass keine Inhalte in der Live Copy gelöscht oder aus der Veröffentlichung deaktiviert werden.

## Anpassen von Rollouts {#customizing-rollouts}

Die Rollout-Konfigurationen von MSM sind in hohem Maße anpassbar. Beachten Sie, dass die Automatisierung von Rollouts weitreichende Folgen haben kann. Als Best Practice sollten Sie eine sorgfältige Planung durchführen, bevor Sie die folgenden Aktivitäten durchführen:

* Automatisieren von Rollouts, z. B. mit [onModify-Triggern](#onmodify)
* Anpassen von [Knotentypen/-eigenschaften](#node-types-properties)
* Starten nachfolgender Workflows
* Aktivieren von Inhalten im Rahmen von Rollouts

### onModify {#onmodify}

Beachten Sie bei Verwendung des [Rollout-Auslösers](live-copy-sync-config.md#rollout-triggers) `onModify` Folgendes:

* Die Automatisierung von Rollouts mit `onModify` -Triggern kann sich negativ auf die Authoring-Leistung auswirken, da nach jeder Seitenänderung Trigger-Rollouts ausgeführt werden.
* Das Rollout-Ergebnis entspricht aus folgenden Gründen möglicherweise nicht den Erwartungen:
   * Die Reihenfolge der resultierenden Änderungsereignisse kann nicht angegeben werden.
   * Die ereignisbasierte Architektur kann die Reihenfolge der an den Rollout-Manager übergebenen Ereignisse nicht garantieren.
* Die Verwendung einer solchen Rollout-Konfiguration kann im Falle von parallelen Aktualisierungen derselben Ressource zu Bestätigungskonflikten führen.

Daher wird empfohlen, `onModify`-Trigger nur zu verwenden, wenn die Vorteile des automatischen Rollout-Starts mögliche Leistungsprobleme überwiegen.

### Knotentypen/-eigenschaften {#node-types-properties}

Neben der Anpassung von Rollout-Aktionen können Sie mit MSM auch die Knoteneigenschaften anpassen, die gerade eingeführt werden. Mit der OSGi-Konfiguration [MSM können Sie Knotentypen](live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) von der Quelle in die Live Copy ausschließen.

## Weiterführende Informationen {#further-information}

Weitere Informationen zu MSM und Live Copy finden Sie in den folgenden Artikeln .

* [Erstellen und Synchronisieren von Live Copies](creating-live-copies.md)
* [Konsole „Live Copy-Übersicht“](live-copy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](live-copy-sync-config.md)
* [MSM-Rollout-Konflikte](rollout-conflicts.md)
