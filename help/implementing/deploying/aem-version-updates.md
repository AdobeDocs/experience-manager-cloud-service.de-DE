---
title: Aktualisierungen der AEM-Version
description: 'Aktualisierungen der AEM-Version '
translation-type: tm+mt
source-git-commit: 78c0802a0703e81941013347a3f4b57cb106c927
workflow-type: tm+mt
source-wordcount: '396'
ht-degree: 40%

---


# Aktualisierungen der AEM-Version {#aem-version-updates}

## Einführung {#introduction}

AEM als Cloud Service verwendet jetzt Continuous Integration und Continuous Versand (CI/CD), um sicherzustellen, dass Ihre Projekte die aktuellste AEM Version aufweisen. Das bedeutet, dass Produktions- und Stage-Instanzen auf die neueste AEM aktualisiert werden, ohne dass der Dienst für Benutzer unterbrochen wird.

>[!NOTE]
>Wenn die Aktualisierung der Produktions-Umgebung fehlschlägt, führt Cloud Manager automatisch eine Rollback-Umgebung durch. Dies erfolgt automatisch, um sicherzustellen, dass nach Abschluss des Updates die Umgebung für die Phase und Produktion AEM gleichen Version sind.

AEM Updates der Version umfassen zwei Typen:

* **AEM Push-Updates**

   * Kann täglich freigegeben werden.

   * Meistens Wartung, einschließlich der neuesten Fehlerbehebungen und Sicherheitsaktualisierungen.

      Da Änderungen regelmäßig vorgenommen werden, ist der Einfluss inkrementell, was die Auswirkungen auf Ihren Dienst verringert.

* **Neue Funktionen**

   * Veröffentlicht über einen vorhersehbaren Monatszeitplan.

AEM Updates durchlaufen eine intensive und vollautomatisierte Produktvalidierungspipeline, die mehrere Schritte umfasst, um eine Unterbrechung des Service für alle in der Produktion befindlichen Systeme zu vermeiden. Konsistenzprüfungen erlauben eine Überwachung des Zustands der Anwendung. Wenn diese Prüfungen während eines AEM als Cloud Service-Update fehlschlagen, wird die Veröffentlichung nicht fortgesetzt und die Adobe wird prüfen, warum das Update zu diesem unerwarteten Verhalten geführt hat.

[Produkttests und Funktionstests](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/implementing/developing/understand-test-results.html#functional-testing) des Kunden, die verhindern, dass Produktaktualisierungen und Kundencode-Push die Produktion unterbrechen, werden auch während einer AEM Aktualisierung der Version überprüft.

>[!NOTE]
>
>Wenn benutzerspezifischer Code in die Staging-Umgebung gepusht und dann von Ihnen abgelehnt wurde, werden die Änderungen bei der nächsten AEM-Aktualisierung entfernt, um das git-Tag der letzten erfolgreichen Kundenfreigabe in der Produktion widerzuspiegeln.

## Composite Node Store {#composite-node-store}

Wie oben erwähnt, verursachen Aktualisierungen in den meisten Fällen keine Ausfallzeiten, auch nicht bei der Autoreninstanz, die aus einem Cluster von Knoten besteht. Rolling updates are possible due to the *composite node store* feature in Oak.

Mithilfe dieser Funktion kann AEM auf mehrere Repositorys gleichzeitig verweisen. Bei einer rollierenden Implementierung enthält die neue Green AEM-Version ihr eigenes Repository `/libs` (das auf TarMK basierende, unveränderliche Repository), das sich von der älteren Blue AEM-Version unterscheidet, obwohl beide auf ein gemeinsames, auf DocumentMK basierendes veränderliches Repository verweisen, das Bereiche wie `/content`, `/conf`, `/etc` und andere umfasst. Da sowohl die Blue- als auch die Green-Implementierung über ihre eigenen Versionen von `/libs` verfügen, können sie bei der rollierenden Aktualisierung beide aktiv bleiben, wobei beide Traffic aufnehmen, bis Blau vollständig durch Grün ersetzt wurde. 

