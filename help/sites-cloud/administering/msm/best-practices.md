---
title: Best Practices für MSM
description: Lernen Sie die Best Practices kennen, die von Adobe Engineering- und Consulting-Teams zusammengestellt wurden, um sich mit dem AEM Multi-Site-Manager vertraut zu machen.
translation-type: tm+mt
source-git-commit: 66b2fb19cbc4c8aa480f1ace31a7f973dc7fb0f7
workflow-type: tm+mt
source-wordcount: '1409'
ht-degree: 34%

---


# Best Practices für MSM {#msm-best-practices}

## Allgemein {#general}

MSM ist ein konfigurierbares Framework für die Automatisierung der Inhaltsbereitstellung. Implementierungen umfassen häufig große Teile einer Website und erstrecken sich über Organisationen und geografische Regionen. Es wird daher dringend empfohlen, MSM-Implementierungen mit der gleichen Sorgfalt zu planen wie Ihre Website:

* Sorgfältig **Planen Sie Struktur und Inhaltsflüsse**, bevor Sie die Implementierung starten.
* **Beschränken Sie Anpassungen auf das Nötigste.** MSM unterstützt zwar einen hohen Grad an Anpassung (z.B. Rollout-Konfigurationen), aber die beste Methode für die Leistung, Zuverlässigkeit und Upgradefähigkeit Ihrer Website besteht in der Minimierung der Anpassung.
* Richten Sie frühzeitig ein **Governance**-Modell ein und trainieren Sie die Benutzer entsprechend, um den Erfolg sicherzustellen. Eine Best Practice von einem Governance-Punkt der Ansicht ist **die Minimierung der Autorität, die lokale Content-Produzenten haben, um Inhalte anderen lokalen Benutzern und ihren jeweiligen Live Copies zuzuordnen/zu verbinden.** Das liegt daran, dass ungesteuerte, verkettete Erbschaften die Komplexität einer MSM-Struktur deutlich erhöhen und ihre Leistung und Zuverlässigkeit beeinträchtigen können.
* Sobald ein Plan für Ihre Struktur, Inhaltsflüsse, Automatisierung und Governance vorhanden ist, **Prototyp und testen Sie Ihr System gründlich**, bevor Sie eine Live-Implementierung starten.
* Denken Sie daran, dass **Adobe Consulting und führende Systemintegratoren** über umfassende Erfahrung bei der Planung und Implementierung von Inhaltsautomatisierung mit MSM verfügen, sodass sie Ihnen sowohl beim Einstieg in Ihr MSM-Projekt als auch bei der gesamten Implementierung helfen können.

## Live Copy-Quellen und Blueprint-Konfigurationen {#live-copy-sources-and-blueprint-configurations}

Denken Sie daran, dass eine Live Copy entweder mit [normalen Seiten](creating-live-copies.md#creating-a-live-copy-of-a-page) oder mit einer [Blueprint-Konfiguration](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) erstellt werden kann. Beide Varianten sind zulässig.

Die Verwendung einer Blueprint-Konfiguration hat allerdings folgende Vorteile:

* Erlauben Sie dem Autor, die Option **Rollout** auf einem Blueprint zu verwenden, um explizit Änderungen an Live Copies zu übertragen, die von diesem Entwurf erben.
* Erlauben Sie dem Autor, **Site** erstellen zu verwenden, um Sprachen einfach auszuwählen und die Struktur der Live Copy zu konfigurieren.
* Definieren Sie eine standardmäßige Rollout-Konfiguration für Live Copies, die mit dem Entwurf in Beziehung stehen.

Wenn keine Blueprint-Konfiguration referenziert wird, können Rollouts nur von den Live Copies selbst initiiert werden, wobei Inhalte aus der Quelle abgerufen werden.

Beim Erstellen einer neuen Site mit Live Copy ist es von Vorteil, dass Sie Musterkonfigurationen erstellen, um die Verfügbarkeit des vollständigen MSM-Funktionssatzes sicherzustellen.

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

* Wenn [eine Live Copy ](creating-live-copies.md#creating-a-live-copy-of-a-page) erstellen - Dies kann als der generischere Ansatz betrachtet werden, mit dem Sie Live-Kopien von jeder Seite erstellen können. Die Inhaltsstruktur einer Live Copy stimmt exakt mit der Quelle überein.

* Wenn [eine Site](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) - Dies ist ein speziellerer Ansatz, vor allem zum Erstellen von Websites mit einer mehrsprachigen Struktur.

Bei der Erstellung einer Site sind folgende Punkte zu beachten:

* Für die Erstellung einer neuen Website benötigen Sie eine [Blueprint-Konfiguration](creating-live-copies.md#managing-blueprint-configurations).
* Damit die Auswahl von Sprachpfaden in einer neuen Site möglich ist, müssen die entsprechenden Sprachwurzeln im Entwurf (Quelle) vorhanden sein.
* Nachdem eine [neue Site als Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (mit **Create** und **Site**) erstellt wurde, sind die ersten beiden Ebenen dieser Live Copy *flach*. Untergeordnete Elemente der Seite sind nicht Teil der Live-Beziehung, werden bei einem Rollout aber trotzdem berücksichtigt, wenn eine dem Auslöser entsprechende Live-Beziehung gefunden wird.

Es ist hilfreich, Folgendes zu vermeiden:

* Manuelles Hinzufügen von Sprachen in der Vorlage (unterhalb der ersten Ebene).
* Manuelles Hinzufügen von Inhalten direkt unter dem Sprachstamm, da dies nicht dazu führt, dass dieser neue Inhalt bei der Einführung automatisch in die Live Copy übernommen wird.

## MSM und mehrsprachige Websites {#msm-and-multilingual-websites}

MSM kann Sie auf zwei Arten beim Erstellen mehrsprachiger Websites unterstützen:

Beachten Sie beim Erstellen von Sprachmastern Folgendes:

* MSM bietet zwar selbst **keine Inhaltsübersetzung**, kann jedoch mit entsprechenden Übersetzungs-Connectors von Dritten integriert werden. Beachten Sie Folgendes:
   * Mit MSM können Sie die Vererbung auf Seiten- und/oder Komponentenebene abbrechen. Dadurch wird verhindert, dass übersetzte Inhalte (aus einer Live Copy mit noch nicht übersetzten Inhalten aus einem Entwurf) bei der nächsten Einführung überschrieben werden.
      * Einige Übersetzungs-Connectors von Dritten bieten eine automatisierte Verwaltung der MSM-Vererbung.
      * Weitere Informationen erhalten Sie von Ihrem Übersetzungsdienstleister.
      * Eine Alternative für die Erstellung und Übersetzung von Sprach-Mastern ist die Verwendung von Sprachkopien in Verbindung mit dem vorgefertigten AEM-Framework für die Übersetzungsintegration.

Weitere Informationen finden Sie unter [Übersetzen von Inhalt für mehrsprachige Websites](/help/sites-cloud/administering/translation/overview.md) und in den [Best Practices zur Übersetzung.](/help/sites-cloud/administering/translation/best-practices.md)

## Strukturänderungen und Rollouts {#structure-changes-and-rollouts}

Änderungen an der Inhaltsstruktur in einer Entwurfs-/Quellstruktur werden in einer Live Copy unterschiedlich dargestellt. Dies ist abhängig von der Art der Änderung:

* **Das** Erstellen neuer Seiten in einem Entwurf führt dazu, dass entsprechende Seiten in Live Copies nach der Aktualisierung mit der standardmäßigen Rollout-Konfiguration erstellt werden.
* **Das** Löschen von Seiten in einem Entwurf führt dazu, dass die entsprechenden Seiten nach der Einführung mit der standardmäßigen Rollout-Konfiguration aus Live Copies gelöscht werden.
* **Das** Verschieben von Seiten in eine Vorlage führt  **** nicht dazu, dass entsprechende Seiten nach der Einführung mit der standardmäßigen Rollout-Konfiguration in Live Copies verschoben werden:
   * Der Grund: Eine Seitenverschiebung beinhaltet implizit eine Seitenlöschung. Dies kann möglicherweise zu unerwartetem Verhalten bei der Veröffentlichung führen, da beim Löschen von Seiten beim Autor der entsprechende Inhalt automatisch deaktiviert wird. Dies kann sich auch auf verwandte Elemente wie Links, Lesezeichen usw. auswirken.
      * Die Inhaltsvererbung auf den entsprechenden Live Copy-Seiten wird aktualisiert, um den neuen Speicherort ihrer Quellen im Entwurf widerzuspiegeln.
      * Um einen Seitenumbruch von einem Blueprint auf Live Copies vollständig zu realisieren, sollten Sie die Best Practices für das Verschieben der [Seite beachten.](#page-move)

### Best Practices zum Verschieben von Seiten {#page-move}

Berücksichtigen Sie beim Verschieben von Seiten in einer Live Copy die folgende Best Practice.

>[!NOTE]
>
>Folgendes funktioniert nur mit dem Trigger [Bei Rollout](live-copy-sync-config.md#rollout-triggers).

1. Erstellen Sie eine benutzerdefinierte Rollout-Konfiguration.
   * Diese neue Konfiguration muss die Aktion `PageMoveAction` enthalten.
   * Fügen Sie dieser Konfiguration keine weiteren Aktionen hinzu.
1. Positionieren Sie die neue Konfiguration.
   * So rollen Sie die Seite vollständig aus, während Sie die entsprechenden Seiten an ihrer alten Position in der Live Copy löschen:
      * Positionieren Sie die neu erstellte Konfiguration vor der standardmäßigen Rollout-Konfiguration. Die standardmäßige Rollout-Konfiguration sorgt dafür, dass die Seiten an ihren alten Positionen gelöscht werden.
      * So rollen Sie die Seitenverschiebung unter Beibehaltung der entsprechenden Seiten an ihren alten Positionen in den Live Copies (im Wesentlichen Duplizieren des Inhalts) aus:
         * Positionieren Sie die neu erstellte Konfiguration nach der standardmäßigen Rollout-Konfiguration. Dadurch wird sichergestellt, dass keine Inhalte in der Live Copy gelöscht oder aus der Veröffentlichung deaktiviert werden.

## Anpassen von Rollouts {#customizing-rollouts}

Die Rollout-Konfigurationen von MSM sind in hohem Maße anpassbar. Beachten Sie, dass die Automatisierung von Rollouts weitreichende Folgen haben kann. Als Best Practice sollten Sie vor der Teilnahme an den folgenden Aktivitäten sehr sorgfältig planen:

* Automatisieren von Rollouts, z. B. mit [onModifizieren von Triggern](#onmodify)
* Anpassen von [Knotentypen/Eigenschaften](#node-types-properties)
* Starten der folgenden Workflows
* Aktivieren von Inhalten im Rahmen von Rollouts

### onModify {#onmodify}

Beachten Sie bei Verwendung des [Rollout-Auslösers](live-copy-sync-config.md#rollout-triggers) `onModify` Folgendes:

* Die Automatisierung von Rollouts mit `onModify`-Triggern kann sich negativ auf die Authoring-Leistung auswirken, da Trigger nach jeder Seitenänderung Rollouts ausführen.
* Das Rollout-Ergebnis entspricht aus folgenden Gründen möglicherweise nicht den Erwartungen:
   * Die Reihenfolge der resultierenden Änderungsereignisse kann nicht angegeben werden.
   * Die ereignisbasierte Architektur kann die Reihenfolge der an den Rollout-Manager übergebenen Ereignisse nicht garantieren.
* Die Verwendung einer solchen Rollout-Konfiguration kann im Falle von parallelen Aktualisierungen derselben Ressource zu Bestätigungskonflikten führen.

Daher wird empfohlen, die Trigger `onModify` nur dann zu verwenden, wenn die Vorteile des automatischen Rollout-Starts etwaige Leistungsaspekte überwiegen.

### Knotentypen/-eigenschaften {#node-types-properties}

Neben der Anpassung der Rollout-Aktionen können Sie mit MSM auch die Knoteneigenschaften anpassen, für die ein Rollout ausgeführt wird. Die [MSM OSGi-Konfiguration ermöglicht es Ihnen, Node-Typen](live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization) von der Quelle in die Live Copy auszuschließen.

## Weiterführende Informationen {#further-information}

Weitere Informationen zu MSM und Live Copy finden Sie in den folgenden Artikeln.

* [Erstellen und Synchronisieren von Live Copies](creating-live-copies.md)
* [Konsole „Live Copy-Übersicht“](live-copy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](live-copy-sync-config.md)
* [MSM-Rollout-Konflikte](rollout-conflicts.md)
