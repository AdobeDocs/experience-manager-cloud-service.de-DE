---
title: AEM-Versionsaktualisierungen
description: Erfahren Sie, wie Adobe Experience Manager (AEM) as a Cloud Service fortlaufende Integration und Bereitstellung (CI/CD) verwendet, um Ihre Projekte auf dem neuesten Stand zu halten.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
source-git-commit: 9bfea65c07da5da044df8f698e409eab5c4320fb
workflow-type: tm+mt
source-wordcount: '827'
ht-degree: 16%

---


# AEM-Versionsaktualisierungen {#aem-version-updates}

Erfahren Sie, wie Adobe Experience Manager (AEM) as a Cloud Service fortlaufende Integration und Bereitstellung (CI/CD) verwendet, um Ihre Projekte auf dem neuesten Stand zu halten.

## CI/CD {#ci-cd}

AEM as a Cloud Service verwendet die kontinuierliche Integration und Bereitstellung (Continuous Integration und Continuous Delivery, CI/CD), um sicherzustellen, dass Ihre Projekte auf der aktuellen AEM-Version basieren. Dieser Prozess aktualisiert Ihre Produktions-, Staging- und Entwicklungsinstanzen nahtlos, ohne dass Ihre Benutzer beeinträchtigt werden.

Bevor Ihre Instanzen automatisch aktualisiert werden, wird 3-5 Tage im Voraus ein neues AEM Maintenance Release veröffentlicht. Während dieses Zeitraums können Sie optional [Manuelle Aktualisierungen von Trigger für Ihre Entwicklungsinstanzen](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment). Nach diesem Zeitpunkt werden zuerst automatisch Versionsupdates auf Ihre Entwicklungsumgebungen angewendet. Wenn die Aktualisierung erfolgreich ist, wird der Aktualisierungsprozess zu Ihren Staging- und Produktionsinstanzen fortgesetzt. Die Entwicklungs- und Staging-Instanzen fungieren als automatisiertes Qualitäts-Gate, bei dem Ihre benutzerdefinierten Tests ausgeführt werden, bevor die Aktualisierung auf Ihre Produktionsumgebung angewendet wird.

>[!NOTE]
>
> Hinweis: Die automatischen Aktualisierungen für Entwicklungsumgebungen werden 2023 schrittweise für alle Kunden aktiviert. Wenn Ihre Entwicklungsumgebungen nicht automatisch aktualisiert werden, können Sie manuelle Aktualisierungen verwenden, um sie mit Ihren Staging- und Produktionsumgebungen synchron zu halten.


## Aktualisierungstypen {#update-types}

Es gibt zwei Arten von AEM-Versionsaktualisierungen:

* [**AEM-Wartungsaktualisierungen**](/help/release-notes/maintenance/latest.md)

   * Sie dienen hauptsächlich Wartungszwecken, einschließlich der neuesten Fehlerbehebungen und Sicherheitsupdates.
   * Dies hat nur geringe Auswirkungen, da Änderungen regelmäßig angewendet werden.

* [**Neue Funktionsaktualisierungen**](/help/release-notes/release-notes-cloud/release-notes-current.md)

   * Sie werden nach einem vorhersehbaren monatlichen Zeitplan veröffentlicht.

>[!NOTE]
>
> Wichtige Daten für monatliche Versionen auf der Seite [Roadmap für Experience Manager veröffentlicht](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de#aem-as-cloud-service) und markieren Sie Ihre Kalender, um sich auf die wichtigsten Aktivitäten vorzubereiten und sich auf die Veröffentlichung vorzubereiten.

## Aktualisierungsfehler {#update-failure}

AEM-Aktualisierungen durchlaufen eine intensive und vollautomatisierte Produktvalidierungs-Pipeline, die mehrere Schritte umfasst, um sicherzustellen, dass keine Unterbrechung des Services für in Produktion befindliche Systeme auftritt. Konsistenzprüfungen erlauben eine Überwachung des Zustands der Anwendung. Wenn diese Prüfungen bei einer AEM as a Cloud Service Aktualisierung fehlschlagen, wird die Veröffentlichung nicht fortgesetzt und Adobe untersucht, warum die Aktualisierung dieses unerwartete Verhalten verursacht hat.

Wenn Sie eine neue Version von benutzerdefiniertem Code in Ihrer Umgebung bereitstellen, [Produkt- und benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) eine entscheidende Rolle spielen. Sie gewährleisten, dass die Produktionssysteme auch nach einer Änderung stabil und funktionsfähig bleiben. Diese Tests werden auch im Aktualisierungsprozess AEM Version angewendet.

Wenn die Aktualisierung der Produktionsumgebung fehlschlägt, setzt Cloud Manager die Staging-Umgebung automatisch zurück. Dies geschieht automatisch, um sicherzustellen, dass nach Abschluss der Aktualisierung die Staging- und Produktionsumgebungen dieselbe AEM Version aufweisen.
Wenn eine automatische Aktualisierung einer Entwicklungsumgebung fehlschlägt, werden Staging- und Produktionsumgebungen ebenfalls nicht aktualisiert.

>[!NOTE]
>
>Wenn benutzerdefinierter Code in die Staging- und nicht in die Produktion verschoben wurde, werden diese Änderungen beim nächsten AEM-Update entfernt, um das Git-Tag der letzten erfolgreichen Kundenversion in der Produktion widerzuspiegeln. Daher muss der benutzerspezifische Code, der nur für das Staging verfügbar war, erneut bereitgestellt werden.

## Best Practices {#best-practices}

* **Nutzung der Staging-Umgebung**
   * Verwenden Sie für lange QA-/UAT-Zyklen eine andere Umgebung (nicht Staging).
   * Nachdem die Integritätstests auf der Bühne abgeschlossen sind, fahren Sie zur Überprüfung in der Produktion fort.

* **Produktions-Pipeline**
   * Vor Implementierung in Produktion pausieren.
   * Wird die Pipeline nach einer Staging-Bereitstellung abgebrochen, deutet dies darauf hin, dass der Code ein &quot;Durchlauf&quot;und kein gültiger Kandidat für die Produktion ist. Siehe [Konfigurieren einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

* **Produktionsfremde Pipeline**
   * Konfigurieren Sie eine [Produktionsfremde Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).
   * Beschleunigen Sie die Geschwindigkeit und Häufigkeit der Bereitstellung bei Fehlern in der Produktions-Pipeline. Identifizieren Sie Probleme in Pipelines ohne Produktanzeigen, indem Sie Funktionstests für das Produkt, benutzerdefinierte Funktionstests und benutzerdefinierte UI-Tests aktivieren.

* **Inhaltskopie**
   * Verwendung [Inhaltskopie](/help/implementing/developing/tools/content-copy.md) , um ähnliche Inhaltssätze in eine Umgebung ohne Produktionsumgebung zu verschieben.

* **Automatisierte Funktionstests**
   * Schließen Sie automatisierte Tests in Ihre Pipeline ein, damit Sie kritische Funktionen testen können.
   * [Kundenfunktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) und [Testen der benutzerdefinierten Benutzeroberfläche](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) blockieren, wenn sie fehlschlagen, wird die AEM nicht bereitgestellt.

## Regression {#regression}

Wenn ein Regressionsfehler auftritt, senden Sie über die Admin Console einen Support-Fall. Wenn es sich bei dem Problem um einen Blocker handelt und sich auf die Produktion auswirkt, sollte ein P1-Fehler gemeldet werden. Geben Sie alle Details an, die zum Reproduzieren des Regressionsproblems erforderlich sind.

## Zusammengesetzter Knotenspeicher {#composite-node-store}

Aktualisierungen verursachen normalerweise keine Ausfallzeiten, auch nicht für die Autoreninstanz, bei der es sich um einen Cluster von Knoten handelt. Rollierende Aktualisierungen sind aufgrund [der Composite Node Store-Funktion in Oak möglich. ](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html)

Mithilfe dieser Funktion kann AEM auf mehrere Repositorys gleichzeitig verweisen. In [rollierende Implementierung](/help/implementing/deploying/overview.md#how-rolling-deployments-work), enthält die neue AEM eine eigene `/libs` (das auf TarMK basierende, unveränderliche Repository). Sie unterscheidet sich von der älteren AEM, obwohl beide auf ein gemeinsames, auf DocumentMK basierendes veränderliches Repository verweisen, das Bereiche wie `/content` , `/conf` , `/etc` und andere.

Da sowohl die alte als auch die neue Version über eigene Versionen von verfügen, `/libs`, können sie beide während der rollierenden Aktualisierung aktiv sein. Und beide können Traffic aufnehmen, bis das alte vollständig durch das neue ersetzt wird.
