---
title: AEM-Versionsaktualisierungen
description: AEM-Versionsaktualisierungen
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: becc07c0042cdfb5de86dc8895801c00c882f8a1
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 20%

---


# AEM-Versionsaktualisierungen {#aem-version-updates}

## Einführung    {#introduction}

AEM as a Cloud Service verwendet jetzt kontinuierliche Integration und kontinuierliche Bereitstellung (CI/CD), um sicherzustellen, dass Ihre Projekte auf der aktuellsten AEM Version basieren. Das bedeutet, dass Produktions- und Staging-Instanzen auf die neueste AEM Version aktualisiert werden, ohne dass der Service für Benutzer unterbrochen wird.

>[!NOTE]
>
>Wenn die Aktualisierung der Produktionsumgebung fehlschlägt, setzt Cloud Manager die Staging-Umgebung automatisch zurück. Dies geschieht automatisch, um sicherzustellen, dass nach Abschluss der Aktualisierung die Staging- und Produktionsumgebungen dieselbe AEM Version aufweisen.

Es gibt zwei Arten von AEM-Versionsaktualisierungen:

* **AEM Wartungsaktualisierungen**

   * Können täglich veröffentlicht werden.
   * Sie dienen hauptsächlich Wartungszwecken, einschließlich der neuesten Fehlerbehebungen und Sicherheitsupdates.
   * Sie haben nur geringe Auswirkungen, da Änderungen regelmäßig angewendet werden.

* **Neue Funktionsaktualisierungen**

   * werden über einen vorhersehbaren monatlichen Zeitplan veröffentlicht.

AEM Aktualisierungen durchlaufen eine intensive und vollautomatisierte Produktvalidierungs-Pipeline, die mehrere Schritte umfasst, um sicherzustellen, dass keine Unterbrechung des Service für Produktionssysteme eintritt. Konsistenzprüfungen erlauben eine Überwachung des Zustands der Anwendung. Wenn diese Prüfungen bei einer AEM as a Cloud Service-Aktualisierung fehlschlagen, wird die Freigabe nicht fortgesetzt. Adobe untersucht dann, warum die Aktualisierung dieses unerwartete Verhalten verursacht hat.

[Produkttests und Kundenfunktionstests,](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) die verhindern, dass Produktaktualisierungen und Kunden-Code-Push-Benachrichtigungen die Produktionssysteme beschädigen, werden auch bei einer AEM Aktualisierung der Version validiert.

>[!NOTE]
>
>Wenn benutzerdefinierter Code in die Staging- und nicht in die Produktion verschoben wurde, werden diese Änderungen beim nächsten AEM entfernt, um das Git-Tag der letzten erfolgreichen Kundenversion in der Produktion widerzuspiegeln. Daher muss der benutzerspezifische Code, der nur für das Staging verfügbar war, erneut bereitgestellt werden.

## Composite Node Store {#composite-node-store}

Aktualisierungen verursachen in den meisten Fällen keine Ausfallzeiten, auch nicht für die Autoreninstanz, bei der es sich um einen Cluster von Knoten handelt. Dank der Funktion Composite Node Store in Oak sind rollierende Aktualisierungen möglich.

Mithilfe dieser Funktion kann AEM auf mehrere Repositorys gleichzeitig verweisen. In einer rollierenden Bereitstellung enthält die neue grüne AEM eigene `/libs` (das auf TarMK basierende, unveränderliche Repository), unterscheidet sich von der älteren blauen AEM, obwohl beide auf ein gemeinsames, auf DocumentMK basierendes veränderliches Repository verweisen, das Bereiche wie `/content` , `/conf` , `/etc` und andere. Da sowohl Blau als auch Grün über eigene Versionen von verfügen `/libs`können sie beide während der rollierenden Aktualisierung aktiv sein, beide nehmen Traffic auf, bis Blau vollständig durch Grün ersetzt wird.
