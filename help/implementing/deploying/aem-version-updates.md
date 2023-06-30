---
title: AEM-Versionsaktualisierungen
description: Erfahren Sie, wie AEM as a Cloud Service fortlaufende Integration und Bereitstellung (CI/CD) verwendet, um Ihre Projekte auf dem neuesten Stand zu halten.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 71%

---


# AEM-Versionsaktualisierungen {#aem-version-updates}

Erfahren Sie, wie AEM as a Cloud Service fortlaufende Integration und Bereitstellung (CI/CD) verwendet, um Ihre Projekte auf dem neuesten Stand zu halten.

## CI/CD {#ci-cd}

AEM as a Cloud Service verwendet die kontinuierliche Integration und Bereitstellung (Continuous Integration und Continuous Delivery, CI/CD), um sicherzustellen, dass Ihre Projekte auf der aktuellen AEM-Version basieren. Dies bedeutet, dass Produktions- und Staging-Instanzen ohne Unterbrechung des Services für Benutzende auf die aktuelle AEM-Version aktualisiert werden.

Versionsaktualisierungen werden nur automatisch auf Produktions- und Staging-Instanzen angewendet. [AEM Aktualisierungen müssen manuell auf alle anderen Instanzen angewendet werden](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment).

## Aktualisierungstypen {#update-types}

Es gibt zwei Arten von AEM-Versionsaktualisierungen:

* **AEM-Wartungsaktualisierungen**

   * Können täglich veröffentlicht werden.
   * Sie dienen hauptsächlich Wartungszwecken, einschließlich aktueller Fehlerbehebungen und Sicherheitsupdates.
   * Sie haben nur geringe Auswirkungen, da Änderungen regelmäßig angewendet werden.

* **Neue Funktionsaktualisierungen**

   * Werden über einen [vorhersehbaren, monatlichen Zeitplan veröffentlicht.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de)

## Aktualisierungsfehler {#update-failure}

AEM-Aktualisierungen durchlaufen eine intensive und vollautomatisierte Produktvalidierungs-Pipeline, die mehrere Schritte umfasst, um sicherzustellen, dass keine Unterbrechung des Services für in Produktion befindliche Systeme auftritt. Konsistenzprüfungen erlauben eine Überwachung des Zustands der Anwendung. Wenn diese Prüfungen bei einer AEM as a Cloud Service-Aktualisierung fehlschlagen, wird die Freigabe nicht fortgesetzt. Adobe untersucht dann, warum die Aktualisierung dieses unerwartete Verhalten verursacht hat.

[Produkttests und Kundenfunktionstests](/help/implementing/cloud-manager/overview-test-results.md#functional-testing), die verhindern, dass Produktaktualisierungen und Kunden-Codepushes die Produktion unterbrechen, werden ebenfalls während einer AEM-Versionsaktualisierung validiert.

Wenn die Aktualisierung der Produktionsumgebung fehlschlägt, setzt Cloud Manager sie automatisch auf die Staging-Umgebung zurück. Dies erfolgt automatisch, um sicherzustellen, dass nach Abschluss einer Aktualisierung die Staging- und Produktionsumgebung beide auf derselben AEM-Version basieren.

>[!NOTE]
>
>Wenn benutzerdefinierter Code in die Staging-Umgebung gepusht und nicht in die Produktionsumgebung übernommen wurde, werden die Änderungen bei der nächsten AEM-Aktualisierung entfernt, um das git-Tag der letzten erfolgreichen Kundenfreigabe in die Produktion widerzuspiegeln. Daher muss der benutzerdefinierte Code, der nur in der Staging-Umgebung verfügbar war, erneut bereitgestellt werden.

## Zusammengesetzter Knotenspeicher {#composite-node-store}

In den meisten Fällen verursachen Aktualisierungen keine Ausfallzeiten, auch nicht für die Autoreninstanz, bei der es sich um einen Cluster von Knoten handelt. Rollierende Aktualisierungen sind aufgrund [der Composite Node Store-Funktion in Oak möglich. ](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

Mithilfe dieser Funktion kann AEM auf mehrere Repositorys gleichzeitig verweisen. In [rollierende Bereitstellung,](/help/implementing/deploying/overview.md#how-rolling-deployments-work) Die neue AEM enthält eine eigene `/libs` (das auf TarMK basierende, unveränderliche Repository), unterscheidet sich von der älteren AEM, obwohl beide auf ein freigegebenes, auf DocumentMK basierendes veränderliches Repository verweisen, das Bereiche wie `/content` , `/conf` , `/etc` und andere.

Da sowohl die alte als auch die neue Version über eigene Versionen von verfügen, `/libs`können sie beide während der rollierenden Aktualisierung aktiv sein und beide können Traffic aufnehmen, bis das alte vollständig durch das neue ersetzt wurde.
