---
title: AEM-Versionsaktualisierungen
description: AEM-Versionsaktualisierungen
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: c3e1559923699d300d78a71195bd5658c3323331
workflow-type: tm+mt
source-wordcount: '399'
ht-degree: 94%

---


# AEM-Versionsaktualisierungen {#aem-version-updates}

## Einführung {#introduction}

AEM as a Cloud Service verwendet jetzt die kontinuierliche Integration und Bereitstellung (Continuous Integration und Continuous Delivery, CI/CD), um sicherzustellen, dass Ihre Projekte auf der aktuellen AEM-Version basieren. Das bedeutet, dass Produktions- und Staging-Instanzen auf die neueste AEM Version aktualisiert werden, ohne dass der Service für Benutzer unterbrochen wird.

>[!NOTE]
>
>Wenn die Aktualisierung der Produktionsumgebung fehlschlägt, setzt Cloud Manager sie automatisch auf die Staging-Umgebung zurück. Dies erfolgt automatisch, um sicherzustellen, dass nach Abschluss einer Aktualisierung die Staging- und Produktionsumgebung beide auf derselben AEM-Version basieren.

Es gibt zwei Arten von AEM-Versionsaktualisierungen:

* **AEM-Wartungsaktualisierungen**

   * Können täglich veröffentlicht werden.
   * Sie dienen hauptsächlich Wartungszwecken, einschließlich aktueller Fehlerbehebungen und Sicherheitsupdates.
   * Sie haben nur geringe Auswirkungen, da Änderungen regelmäßig angewendet werden.

* **Neue Funktionsaktualisierungen**

   * Werden über einen vorhersehbaren monatlichen Zeitplan veröffentlicht.

AEM-Aktualisierungen durchlaufen eine intensive und vollautomatisierte Produktvalidierungs-Pipeline, die mehrere Schritte umfasst, um sicherzustellen, dass keine Unterbrechung des Services für in Produktion befindliche Systeme auftritt. Konsistenzprüfungen erlauben eine Überwachung des Zustands der Anwendung. Wenn diese Prüfungen bei einer AEM as a Cloud Service-Aktualisierung fehlschlagen, wird die Freigabe nicht fortgesetzt. Adobe untersucht dann, warum die Aktualisierung dieses unerwartete Verhalten verursacht hat.

[Produkttests und Kundenfunktionstests](/help/implementing/cloud-manager/overview-test-results.md#functional-testing), die verhindern, dass Produktaktualisierungen und Kunden-Codepushes die Produktion unterbrechen, werden ebenfalls während einer AEM-Versionsaktualisierung validiert.

>[!NOTE]
>
>Wenn benutzerdefinierter Code in die Staging-Umgebung gepusht und nicht in die Produktionsumgebung übernommen wurde, werden die Änderungen bei der nächsten AEM-Aktualisierung entfernt, um das git-Tag der letzten erfolgreichen Kundenfreigabe in die Produktion widerzuspiegeln. Daher muss der benutzerdefinierte Code, der nur in der Staging-Umgebung verfügbar war, erneut bereitgestellt werden.

## Zusammengesetzter Knotenspeicher {#composite-node-store}

In den meisten Fällen verursachen Aktualisierungen keine Ausfallzeiten, auch nicht bei der Autoreninstanz, die aus einem Cluster von Knoten besteht. Dank der Funktion „Composite Node Store“ (Zusammengesetzter Knotenspeicher) in Oak sind rollierende Aktualisierungen möglich.

Mithilfe dieser Funktion kann AEM auf mehrere Repositorys gleichzeitig verweisen. Bei einer rollierenden Implementierung enthält die neue grüne AEM-Version ihr eigenes `/libs`-Repository (das auf TarMK basierende, unveränderliche Repository), das sich von der älteren blauen AEM-Version unterscheidet, obwohl beide auf ein gemeinsames, auf DocumentMK basierendes veränderliches Repository verweisen, das unter anderem Bereiche wie `/content` , `/conf` und `/etc` umfasst. Da sowohl die Blau- als auch die Grün-Implementierung über ihre eigenen Versionen von `/libs` verfügen, können sie bei der rollierenden Aktualisierung beide aktiv bleiben, wobei beide Traffic aufnehmen, bis Blau vollständig durch Grün ersetzt wurde.
