---
title: AEM-Versionsaktualisierungen
description: 'AEM-Versionsaktualisierungen '
feature: Bereitstellen
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 100%

---


# AEM-Versionsaktualisierungen {#aem-version-updates}

## Einführung {#introduction}

AEM as a Cloud Service verwendet jetzt CI/CD (Continuous Integration und Continuous Delivery), um sicherzustellen, dass Ihre Projekte auf der aktuellen AEM-Version basieren. Dies bedeutet, dass Produktions- und Staging-Instanzen ohne Unterbrechung des Service für Benutzer auf die aktuelle AEM-Version aktualisiert werden.

>[!NOTE]
>Wenn die Aktualisierung der Produktionsumgebung fehlschlägt, setzt Cloud Manager automatisch auf die Staging-Umgebung zurück. Dies erfolgt automatisch, um sicherzustellen, dass nach Abschluss der Aktualisierung die Staging- und Produktionsumgebung auf derselben AEM-Version basieren.

Es gibt zwei Arten von AEM-Versionsaktualisierungen:

* **AEM-Push-Aktualisierungen**

   * Können täglich veröffentlicht werden.

   * Vor allem zu Wartungszwecken, einschließlich der neuesten Fehlerkorrekturen und Sicherheitsaktualisierungen.

      Da die Änderungen regelmäßig durchgeführt werden, sind die Auswirkungen inkrementell, was die Auswirkungen auf Ihren Service verringert.

* **Neue Funktionsaktualisierungen**

   * Werden über einen vorhersehbaren monatlichen Zeitplan veröffentlicht.

AEM-Aktualisierungen durchlaufen eine intensive und vollautomatisierte Produktvalidierungs-Pipeline, die mehrere Schritte umfasst, um sicherzustellen, dass keine Unterbrechung des Service für in Produktion befindliche Systeme auftritt. Konsistenzprüfungen erlauben eine Überwachung des Zustands der Anwendung. Wenn diese Prüfungen bei einer AEM as a Cloud Service-Aktualisierung fehlschlagen, wird die Freigabe nicht fortgesetzt. Adobe untersucht dann, warum die Aktualisierung dieses unerwartete Verhalten verursacht hat.

[Produkttests und Kundenfunktionstests](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/understand-test-results.html#functional-testing), die verhindern, dass Produktaktualisierungen und Kunden-Codepushes die Produktion unterbrechen, werden ebenfalls während einer AEM-Versionsaktualisierung validiert.

>[!NOTE]
>
>Wenn benutzerspezifischer Code in die Staging-Umgebung gepusht und dann von Ihnen abgelehnt wurde, werden die Änderungen bei der nächsten AEM-Aktualisierung entfernt, um das git-Tag der letzten erfolgreichen Kundenfreigabe in der Produktion widerzuspiegeln.

## Composite Node Store {#composite-node-store}

Wie oben erwähnt, verursachen Aktualisierungen in den meisten Fällen keine Ausfallzeiten, auch nicht bei der Autoreninstanz, die aus einem Cluster von Knoten besteht. Dank der Funktion *Composite Node Store* in Oak sind rollierende Aktualisierungen möglich.

Mithilfe dieser Funktion kann AEM auf mehrere Repositorys gleichzeitig verweisen. Bei einer rollierenden Implementierung enthält die neue grüne AEM-Version ihr eigenes Repository `/libs` (das auf TarMK basierende, unveränderliche Repository), das sich von der älteren blauen AEM-Version unterscheidet, obwohl beide auf ein gemeinsames, auf DocumentMK basierendes veränderliches Repository verweisen, das Bereiche wie `/content`, `/conf`, `/etc` und andere umfasst. Da sowohl die Blau- als auch die Grün-Implementierung über ihre eigenen Versionen von `/libs` verfügen, können sie bei der rollierenden Aktualisierung beide aktiv bleiben, wobei beide Traffic aufnehmen, bis Blau vollständig durch Grün ersetzt wurde.

