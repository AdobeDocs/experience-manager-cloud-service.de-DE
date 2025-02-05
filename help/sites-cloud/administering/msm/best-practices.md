---
title: Best Practices für MSM
description: Hier finden Sie Best Practices für die Einrichtung und Verwendung von AEM Multi Site Manager (MSM), die von Technik- und Beratungsteams von Adobe zusammengestellt wurden.
feature: Multi Site Manager
role: Admin
exl-id: 61b8ded8-3b9e-423f-85a9-7280e1a721cc
solution: Experience Manager Sites
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1414'
ht-degree: 98%

---

# Best Practices für MSM {#msm-best-practices}

## Allgemein {#general}

MSM ist ein konfigurierbares Framework zur Automatisierung der Inhaltsbereitstellung. Implementierungen umfassen häufig große Teile einer Website und umspannen Organisationen und geografische Regionen. Es wird daher dringend empfohlen, MSM-Implementierungen mit der gleichen Sorgfalt zu planen wie Ihre Website:

* **Planen Sie zunächst sorgfältig die Struktur und den Inhaltsfluss**, bevor Sie mit der Implementierung beginnen.
* **Beschränken Sie Anpassungen auf das Nötigste.** MSM unterstützt zwar ein hohes Maß an Anpassungen (beispielsweise Rollout-Konfigurationen). Es empfiehlt sich jedoch, möglichst wenige Anpassungen vorzunehmen, um die Leistung und Zuverlässigkeit Ihrer Website nicht zu beeinträchtigen und Website-Upgrades durchführen zu können.
* Etablieren Sie frühzeitig ein **Governance-Modell** und schulen Sie die Benutzer entsprechend. Bei der Governance empfiehlt es sich, die **Autorität zu minimieren, über die lokale Inhaltsersteller verfügen**, um Inhalt anderen lokalen Benutzern oder ihren jeweiligen Live Copies zuzuordnen oder mit ihnen zu verknüpfen. Das liegt daran, dass nicht regulierte verkettete Vererbungen die Komplexität einer MSM-Struktur erheblich erhöhen und ihre Leistung und Zuverlässigkeit beeinträchtigen.
* Wenn Sie über einen Plan für Ihre Struktur, Ihren Inhaltsfluss, Ihre Automatisierung und die Governance verfügen, **erstellen Sie einen Prototyp und testen Sie Ihr System sorgfältig**, bevor Sie mit der Live-Implementierung beginnen.
* **Adobe Consulting und führende Systemintegratoren** sind bestens mit der Planung und Implementierung der Inhaltsautomatisierung mit MSM vertraut und können Sie sowohl bei den ersten Schritten mit Ihrem MSM-Projekt als auch im weiteren Verlauf der Implementierung unterstützen.

## Live Copy-Quellen und Blueprint-Konfigurationen {#live-copy-sources-and-blueprint-configurations}

Eine Live Copy kann entweder unter Verwendung [regulärer Seiten](creating-live-copies.md#creating-a-live-copy-of-a-page) oder unter Verwendung einer [Blueprint-Konfiguration](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) erstellt werden. Beides sind gültige Anwendungsfälle.

Eine Blueprint-Konfiguration hat die folgenden zusätzlichen Vorteile:

* Die Autorin bzw. der Autor kann für einen Blueprint die Option **Rollout** verwenden und so (explizit) Änderungen an Live Copies pushen, die von diesem Blueprint erben.
* Die Autorin bzw. der Autor kann mit **Website erstellen** einfach Sprachen auswählen und die Struktur der Live Copy konfigurieren.
* Sie definiert eine standardmäßige Rollout-Konfiguration für Live Copies, die über eine Beziehung mit dem Blueprint verfügen.

Ohne Verweis auf eine Blueprint-Konfiguration können Rollouts nur von Live Copies selbst initiiert werden, wobei im Wesentlichen Inhalt aus der Quelle abgerufen wird.

Wenn Sie eine Website mit Live Copy erstellen, empfiehlt es sich, Blueprint-Konfigurationen zu erstellen, um die Verfügbarkeit sämtlicher MSM-Features sicherzustellen.

>[!NOTE]
>
>Beachten Sie, dass CUGs auf der Registerkarte „Berechtigungen“ aus Blueprints nicht zu Live Copies ausgerollt werden können. Planen Sie dies ein, wenn Sie eine Live Copy konfigurieren.

## Komponenten- und Container-Synchronisierung {#components-and-container-synchronization}

Für die Synchronisierung von Komponenten gilt in MSM im Allgemeinen folgende Rollout-Regel:

* Beim Rollout der Komponenten werden alle in der Blueprint enthaltenen Ressourcen synchronisiert.
* Container synchronisieren nur die aktuelle Ressource.

Dies bedeutet, dass Komponenten als ein Aggregat behandelt werden und die Komponente selbst und alle untergeordneten Elemente in einem Rollout durch die Komponenten in den Blueprints ersetzt werden. Wenn also eine Ressource lokal zu einer solchen Komponente hinzugefügt wird, geht sie für den Inhalt des Blueprints beim Rollout verloren.

Um die Schachtelung von Komponenten zu unterstützen, sodass lokal hinzugefügte Komponenten bei einem Rollout erhalten bleiben, muss die Komponente als Container deklariert werden.

>[!NOTE]
>
>Fügen Sie der Komponente die Eigenschaft `cq:isContainer` hinzu, um sie als Container zu kennzeichnen.

## Erstellen einer Website {#create-site}

Live Copies können mit AEM auf zwei Arten erstellt werden:

* Beim [Erstellen einer Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-page) – Hierbei handelt es sich um den allgemeineren Ansatz, mit dem Sie Live Copies von einer beliebigen Seite aus erstellen können. Die Inhaltsstruktur einer Live Copy entspricht exakt der Quelle.

* Beim [Erstellen einer Website](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) – Dies ist ein eher spezialisierter Ansatz, der hauptsächlich für die Erstellung von Websites mit einer mehrsprachigen Struktur gedacht ist.

Berücksichtigen Sie beim Erstellen einer Website folgende Punkte:

* Für die Erstellung einer Site benötigen Sie eine [Blueprint-Konfiguration](creating-live-copies.md#managing-blueprint-configurations).
* Um das Auswählen von Sprachpfaden zu ermöglichen, die für eine neue Website erstellt werden sollen, muss der Blueprint (Quelle) die entsprechenden Sprachstämme enthalten.
* Nach der [Erstellung einer neuen Website als Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-site-from-a-blueprint-configuration) (mithilfe von **Erstellen** > **Website**) sind die ersten beiden Ebenen dieser Live Copy *flach*. Untergeordnete Elemente der Seite sind nicht Teil der Live-Beziehung, werden bei einem Rollout aber trotzdem berücksichtigt, wenn eine dem Auslöser entsprechende Live-Beziehung gefunden wird.

Vermeiden Sie Folgendes:

* Manuelles Hinzufügen von Sprachen im Blueprint (unterhalb der ersten Ebene).
* Manuelles Hinzufügen von Inhalten unmittelbar unter dem Sprachstamm, da dadurch der neue Inhalt beim Rollout nicht automatisch auf die Live Copy übertragen wird.

## MSM und mehrsprachige Websites {#msm-and-multilingual-websites}

MSM kann Sie auf zwei Arten beim Erstellen mehrsprachiger Websites unterstützen:

Beachten Sie beim Erstellen von Sprachstämmen Folgendes:

* Während MSM selbst **keine Inhaltsübersetzung** anbietet, kann es mit Übersetzungs-Connectoren von Drittanbietern integriert werden, die dies tun. Beachten Sie Folgendes:
   * Mit MSM können Sie die Vererbung auf Seiten- und/oder Komponentenebene unterbinden. So verhindern Sie, dass übersetzter Inhalt aus einer Live Copy beim nächsten Rollout durch noch nicht übersetzten Inhalt aus einem Blueprint überschrieben wird.
      * Einige Übersetzungs-Connectoren von Drittanbietern bieten eine automatisierte Verwaltung der MSM-Vererbung.
      * Weitere Informationen erhalten Sie von Ihrem Übersetzungsdienstleister.
      * Eine Alternative für die Erstellung und Übersetzung von Sprachstämmen ist die Verwendung von Sprachkopien in Verbindung mit dem vorgefertigten AEM-Framework für die Übersetzungsintegration.

Weitere Informationen finden Sie unter [Übersetzen von Inhalt für mehrsprachige Websites](/help/sites-cloud/administering/translation/overview.md) und in den [Best Practices zur Übersetzung](/help/sites-cloud/administering/translation/best-practices.md).

## Strukturänderungen und Rollouts {#structure-changes-and-rollouts}

Änderungen an der Inhaltsstruktur in einem Blueprint/einer Quellstruktur werden in einer Live Copy unterschiedlich umgesetzt. Dies ist abhängig von der Art der Änderung:

* Wenn Sie neue Seiten in einem Blueprint **erstellen**, werden nach dem Rollout mit der standardmäßigen Rollout-Konfiguration entsprechende Seiten in Live Copies erstellt.
* Wenn Sie Seiten in einem Blueprint **löschen**, werden die entsprechenden Seiten nach dem Rollout mit der standardmäßigen Rollout-Konfiguration aus Live Copies gelöscht.
* Wenn Sie Seiten in einem Blueprint **verschieben**, werden die entsprechenden Seiten nach dem Rollout mit der standardmäßigen Rollout-Konfiguration in Live Copies **nicht** verschoben:
   * Der Grund hierfür ist, dass eine Seitenverschiebung implizit eine Seitenlöschung beinhaltet. Dies kann bei der Veröffentlichung zu unerwartetem Verhalten führen, da das Löschen von Seiten im Rahmen der Bearbeitung zur Folge hat, dass der entsprechende Inhalt bei der Veröffentlichung automatisch deaktiviert wird. Dies kann sich wiederum auch auf verwandte Elemente wie etwa Links und Lesezeichen auswirken.
      * Die Inhaltsvererbung der jeweiligen Live Copy-Seiten wird aktualisiert, um den neuen Speicherort ihrer Quellen im Blueprint widerzuspiegeln.
      * Im Anschluss finden Sie einige Best Practices für die vollständige Umsetzung einer Seitenverschiebung aus einem Blueprint in [ Live Copies].#page-move)

### Best Practices für die Seitenverschiebung {#page-move}

Halten Sie sich beim Verschieben von Seiten in einer Live Copy an die folgende Best Practice.

>[!NOTE]
>
>Folgendes funktioniert nur mit dem Auslöser [Bei Rollout](live-copy-sync-config.md#rollout-triggers).

1. Erstellen Sie eine benutzerdefinierte Rollout-Konfiguration.
   * Diese neue Konfiguration muss die Aktion `PageMoveAction` enthalten.
   * Fügen Sie dieser Konfiguration keine anderen Aktionen hinzu.
1. Positionieren Sie die neue Konfiguration.
   * Gehen Sie wie folgt vor, um ein vollständiges Rollout der Seitenverschiebung durchzuführen und gleichzeitig die entsprechenden Seiten an ihrem alten Ort in der Live Copy zu löschen:
      * Positionieren Sie die erstellte Konfiguration vor der standardmäßigen Rollout-Konfiguration. Die Löschung der Seiten an ihrem alten Ort wird durch die standardmäßige Rollout-Konfiguration übernommen.
      * Gehen Sie wie folgt vor, um das Rollout der Seitenverschiebung durchzuführen und dabei die entsprechenden Seiten an ihrem alten Ort beizubehalten (und somit im Grunde den Inhalt zu duplizieren):
         * Positionieren Sie die erstellte Konfiguration nach der standardmäßigen Rollout-Konfiguration. Dadurch wird sichergestellt, dass in der Live Copy kein Inhalt gelöscht oder für die Veröffentlichung deaktiviert wird.

## Anpassen von Rollouts {#customizing-rollouts}

MSM-Rollout-Konfigurationen können in hohem Maße angepasst werden. Die Automatisierung von Rollouts kann weitreichende Folgen haben. Deshalb sollte den folgenden Schritten eine sehr sorgfältige Planung vorausgehen:

* Automatisieren von Rollouts, etwa mit [onModify-Auslösern](#onmodify)
* Anpassen von [Knotentypen/-eigenschaften](#node-types-properties)
* Starten von Folgeworkflows
* Aktivieren von Inhalt im Rahmen eines Rollouts

### onModify {#onmodify}

Beachten Sie bei Verwendung des [Rollout-Auslösers](live-copy-sync-config.md#rollout-triggers) `onModify` Folgendes:

* Die Automatisierung von Rollouts mit Auslösern vom Typ `onModify` kann die Leistung bei der Bearbeitung beeinträchtigen, da nach jeder Seitenbearbeitung Rollouts ausgelöst werden.
* Das Ergebnis des Rollouts kann von dem erwarteten Ergebnis abweichen:
   * Sie können die Reihenfolge der resultierenden Änderungsereignisse nicht angeben.
   * Die ereignisbasierte Architektur kann die Reihenfolge der Ereignisse, die an den Rollout-Manager übergeben werden, nicht garantieren.
* Die Verwendung einer solchen Rollout-Konfiguration kann zu Commit-Konflikten führen, wenn gleichzeitige Updates derselben Ressource auftreten.

Auslöser vom Typ `onModify` sollten daher nur verwendet werden, wenn die Vorteile einer automatischen Rollout-Initiierung die potenziellen Leistungsprobleme überwiegen.

### Knotentypen/-eigenschaften {#node-types-properties}

Neben der Anpassung von Rollout-Aktionen ermöglicht MSM auch die Anpassung von Knoteneigenschaften, für die ein Rollout durchgeführt wird. Die [MSM-OSGi-Konfiguration ermöglicht das Ausschließen von Knotentypen](live-copy-sync-config.md#excluding-properties-and-node-types-from-synchronization), sodass diese nicht aus der Quelle in die Live Copy kopiert werden.

## Weiterführende Informationen {#further-information}

Weitere Informationen zu MSM und Live Copy finden Sie in den folgenden Artikeln.

* [Erstellen und Synchronisieren von Live Copies](creating-live-copies.md)
* [Konsole „Live Copy-Übersicht“](live-copy-overview.md)
* [Konfigurieren der Synchronisierung von Live Copies](live-copy-sync-config.md)
* [MSM-Rollout-Konflikte](rollout-conflicts.md)
