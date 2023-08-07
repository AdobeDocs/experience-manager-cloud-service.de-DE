---
title: AEM-Versionsaktualisierungen
description: Erfahren Sie, wie AEM as a Cloud Service fortlaufende Integration und Bereitstellung (CI/CD) verwendet, um Ihre Projekte auf dem neuesten Stand zu halten.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: 635b4adeab8d93b7c7335453b04d8b78ef3a0496
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 29%

---


# AEM-Versionsaktualisierungen {#aem-version-updates}

Erfahren Sie, wie AEM as a Cloud Service fortlaufende Integration und Bereitstellung (CI/CD) verwendet, um Ihre Projekte auf dem neuesten Stand zu halten.

## CI/CD {#ci-cd}

AEM as a Cloud Service verwendet die kontinuierliche Integration und Bereitstellung (Continuous Integration und Continuous Delivery, CI/CD), um sicherzustellen, dass Ihre Projekte auf der aktuellen AEM-Version basieren. Dieser Prozess aktualisiert Ihre Produktions-, Staging- und Entwicklungsinstanzen nahtlos, ohne dass Ihre Benutzer beeinträchtigt werden.

Bevor Ihre Instanzen automatisch aktualisiert werden, werden 3-5 Tage im Voraus neue AEM veröffentlicht. Während dieses Zeitraums haben Sie die Möglichkeit,
[Manuelle Aktualisierungen von Trigger für Ihre Entwicklungsinstanzen](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment).
Nach diesem Zeitpunkt werden Versionsaktualisierungen automatisch zuerst auf Ihre Entwicklungsumgebungen angewendet. Wenn die Aktualisierung erfolgreich ist, wird der Aktualisierungsprozess zu Ihren Staging- und Produktionsinstanzen fortgesetzt. Die Entwicklungs- und Staging-Instanzen fungieren als automatisiertes Qualitäts-Gate, bei dem Ihre benutzerdefinierten Tests ausgeführt werden, bevor die Aktualisierung auf Ihre Produktionsumgebung angewendet wird.

>[!NOTE]
>
> Hinweis: Die automatischen Aktualisierungen für Entwicklungsumgebungen werden 2023 schrittweise für alle Kunden aktiviert. Wenn Ihre Entwicklungsumgebungen nicht automatisch aktualisiert werden, können Sie manuelle Aktualisierungen verwenden, um sie mit Ihren Staging- und Produktionsumgebungen synchron zu halten.


## Aktualisierungstypen {#update-types}

Es gibt zwei Arten von AEM-Versionsaktualisierungen:

* **AEM-Wartungsaktualisierungen**

   * Können täglich veröffentlicht werden.
   * Sie dienen hauptsächlich Wartungszwecken, einschließlich aktueller Fehlerbehebungen und Sicherheitsupdates.
   * Sie haben nur geringe Auswirkungen, da Änderungen regelmäßig angewendet werden.

* **Neue Funktionsaktualisierungen**

   * Werden über einen [vorhersehbaren, monatlichen Zeitplan veröffentlicht.](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de)

## Aktualisierungsfehler {#update-failure}

AEM-Aktualisierungen durchlaufen eine intensive und vollautomatisierte Produktvalidierungs-Pipeline, die mehrere Schritte umfasst, um sicherzustellen, dass keine Unterbrechung des Services für in Produktion befindliche Systeme auftritt.
Konsistenzprüfungen erlauben eine Überwachung des Zustands der Anwendung.
Wenn diese Prüfungen bei einer AEM as a Cloud Service Aktualisierung fehlschlagen, wird die Veröffentlichung nicht fortgesetzt und die Adobe untersucht, warum die Aktualisierung dieses unerwartete Verhalten verursacht hat.

Wenn Sie eine neue Version eines benutzerdefinierten Codes von in Ihren Umgebungen bereitstellen,
[Produkt- und benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/overview-test-results.md#functional-testing)
eine entscheidende Rolle dabei zu spielen, dass die Produktionssysteme auch nach einer Änderung stabil und funktionsfähig bleiben. Diese Tests werden auch beim Aktualisierungsprozess der AEM-Version genutzt.

Wenn die Aktualisierung der Produktionsumgebung fehlschlägt, setzt Cloud Manager sie automatisch auf die Staging-Umgebung zurück. Dies geschieht automatisch, um sicherzustellen, dass nach Abschluss der Aktualisierung die Staging- und Produktionsumgebungen dieselbe AEM Version aufweisen.
Wenn eine automatische Aktualisierung einer Entwicklungsumgebung fehlschlägt, werden Staging- und Produktionsumgebungen ebenfalls nicht aktualisiert.

>[!NOTE]
>
>Wenn benutzerdefinierter Code in die Staging-Umgebung gepusht und nicht in die Produktionsumgebung übernommen wurde, werden die Änderungen bei der nächsten AEM-Aktualisierung entfernt, um das git-Tag der letzten erfolgreichen Kundenfreigabe in die Produktion widerzuspiegeln. Daher muss der benutzerdefinierte Code, der nur in der Staging-Umgebung verfügbar war, erneut bereitgestellt werden.

## Best Practices {#best-practices}

* 
   * **Nutzung der Staging-Umgebung**
   * Verwenden Sie für lange QA-/UAT-Zyklen eine andere Umgebung (nicht Staging).
   * Nachdem die Integritätstests auf der Bühne abgeschlossen sind, fahren Sie zur Überprüfung in der Produktion fort.

* 
   * **Produktions-Pipeline**
   * Vor Implementierung in Produktion pausieren.
   * Wenn die Pipeline nach einer Staging-Bereitstellung abgebrochen wird, bedeutet dies, dass der Code ein &quot;Durchlauf&quot;und kein gültiger Kandidat für die Produktion ist, siehe [Konfigurieren einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

* 
   * **Produktionsfremde Pipeline**
* Konfigurieren [Produktionsfremde Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).
* 
   * Beschleunigen Sie die Geschwindigkeit und Häufigkeit der Bereitstellung bei Fehlern in der Produktions-Pipeline.  Ermitteln Sie Probleme in Pipelines ohne Produktanzeigen, indem Sie Funktionstests für das Produkt, benutzerdefinierte Funktionstests und benutzerdefinierte UI-Tests aktivieren.

* 
   * **Inhaltskopie**
   * Verwendung [Inhaltskopie](/help/implementing/developing/tools/content-copy.md) , um ähnliche Inhaltssätze in eine Umgebung ohne Produktionsumgebung zu verschieben.

* 
   * **Automatisierte Funktionstests**
* Schließen Sie automatisierte Tests in Ihre Pipeline ein, um wichtige Funktionen zu testen.
* [Kundenfunktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) und [Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) blockieren, wenn sie fehlschlagen, wird AEM Veröffentlichung nicht durchgeführt.

## Regression {#regression}

Wenn Sie auf ein Regressionsproblem stoßen, wenden Sie sich bitte über die Admin Console an einen Support-Fall.  Wenn das Problem ein Blocker ist und sich auf die Produktion auswirkt, sollte ein P1-Fehler angezeigt werden.  Geben Sie alle Details an, die zum Reproduzieren des Regressionsproblems erforderlich sind.

## Zusammengesetzter Knotenspeicher {#composite-node-store}

In den meisten Fällen verursachen Aktualisierungen keine Ausfallzeiten, auch nicht für die Autoreninstanz, bei der es sich um einen Cluster von Knoten handelt. Rollierende Aktualisierungen sind aufgrund [der Composite Node Store-Funktion in Oak möglich. ](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

Mithilfe dieser Funktion kann AEM auf mehrere Repositorys gleichzeitig verweisen. In [kontinuierliche Bereitstellung,](/help/implementing/deploying/overview.md#how-rolling-deployments-work) Die neue AEM enthält eine eigene `/libs` (das auf TarMK basierende, unveränderliche Repository), unterscheidet sich von der älteren AEM, obwohl beide auf ein gemeinsames, auf DocumentMK basierendes veränderliches Repository verweisen, das Bereiche wie `/content` , `/conf` , `/etc` und andere.

Da sowohl die alte als auch die neue Version über eigene Versionen von verfügen, `/libs`können sie beide während der rollierenden Aktualisierung aktiv sein und beide können Traffic aufnehmen, bis das alte vollständig durch das neue ersetzt wurde.
