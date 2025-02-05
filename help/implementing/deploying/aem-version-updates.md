---
title: AEM-Versionsaktualisierungen
description: Erfahren Sie, wie Adobe Experience Manager (AEM) as a Cloud Service durch Integration und Bereitstellung (CI/CD) Ihre Projekte auf dem aktuellen Versionsstand hält.
feature: Deploying
exl-id: 36989913-69db-4f4d-8302-57c60f387d3d
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '997'
ht-degree: 98%

---


# AEM-Versionsaktualisierungen {#aem-version-updates}

Erfahren Sie, wie Adobe Experience Manager (AEM) as a Cloud Service durch Integration und Bereitstellung (CI/CD) Ihre Projekte auf dem aktuellen Versionsstand hält.

## CI/CD {#ci-cd}

AEM as a Cloud Service verwendet die kontinuierliche Integration und Bereitstellung (Continuous Integration und Continuous Delivery, CI/CD), um sicherzustellen, dass Ihre Projekte auf der aktuellen AEM-Version basieren. Dieser Prozess ermöglicht eine nahtlose Aktualisierung Ihrer Produktions-, Staging- und Entwicklungsinstanzen, ohne Ihre Benutzenden zu stören.

>[!NOTE]
> Da Entwicklungsinstanzen bereits automatisch aktualisiert werden, stehen die manuellen Aktualisierungen für Entwicklungsinstanzen für _einige_ Ihrer Programme möglicherweise nicht zur Verfügung. Diese Funktion wird derzeit auf automatische Aktualisierungen umgestellt.

Bevor Ihre Instanzen automatisch aktualisiert werden, wird 3 bis 5 Tage vorher eine neue AEM-Wartungsversion veröffentlicht. Während dieses Zeitraums wird Ihre Entwicklungsinstanz möglicherweise automatisch aktualisiert, oder Sie können, falls verfügbar, optional [die Aktualisierung für Ihre Entwicklungsinstanzen auslösen](/help/implementing/cloud-manager/manage-environments.md#updating-dev-environment). Versionsaktualisierungen werden automatisch zuerst auf Ihre Entwicklungsumgebungen angewendet. Bei erfolgreicher Aktualisierung wird der Aktualisierungsprozess in Ihren Staging- und Produktionsinstanzen fortgesetzt. Die Entwicklungs- und Staging-Instanzen fungieren als automatisiertes Quality Gate (Qualitätsprüfpunkt), bei dem Ihre benutzerdefinierten Tests ausgeführt werden, bevor das Update auf Ihre Produktionsumgebung angewendet wird.

### Nicht-intrusive Wartungsupdates (NIMU, Non-Intrusive Maintenance Updates) {#nimu}

Nicht-intrusive Wartungsupdates sind automatische Aktualisierungen, die ohne Einbeziehung der Kunden-Pipelines angewendet werden.
Über NIMU kann die Kundin bzw. der Kunde die Pipeline jederzeit verwenden, auch wenn eine AEM-Versionsaktualisierung geplant oder im Gange ist, und Wartungs-Updates werden nicht mehr im Ausführungsverlauf der Kunden-Pipeline angezeigt, wodurch es einfacher wird, den Verlauf von Code-Bereitstellungen zu verfolgen.

#### Aktualisieren von Aktivitäten

Die aktuelle AEM-Version kann wie bisher für jede Umgebung mithilfe des Bedienfelds „Umgebungen der Cloud Manager-Benutzeroberfläche“ überprüft werden. Dieselben Qualitäts-Gates, die in der Pipeline verwendet werden, werden von nicht-intrusiven Wartungs-Updates verwendet, einschließlich der von Kundinnen und Kunden geschriebenen Tests.
Es wird eine [Benachrichtigung über die Cloud Manager-Benutzeroberfläche](/help/implementing/cloud-manager/notifications.md) gesendet, sobald ein nicht-intrusives Wartungs-Update auf die Umgebungen Ihres Programms angewendet wird. Sie können dies so konfigurieren, dass sie auch an Ihre E-Mail-Adresse gesendet wird.

>[!NOTE]
>
> Hinweis: Nicht-intrusive Wartungs-Updates werden im Jahr 2024 schrittweise für alle Kundinnen und Kunden aktiviert.


## Aktualisierungstypen {#update-types}

Es gibt zwei Arten von AEM-Versionsaktualisierungen:

* [**AEM-Wartungsaktualisierungen**](/help/release-notes/maintenance/latest.md)

   * Sie dienen hauptsächlich Wartungszwecken, einschließlich aktueller Fehlerbehebungen und Sicherheits-Updates.
   * Sie haben nur geringe Auswirkungen, da Änderungen regelmäßig angewendet werden.

* [**AEM-Funktionsaktivierung**](/help/release-notes/release-notes-cloud/release-notes-current.md)

   * Sie werden nach einem vorhersehbaren, monatlichen Zeitplan veröffentlicht.

>[!NOTE]
>
> Ermitteln Sie die Stichtage für die monatlichen Versionen in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de#aem-as-cloud-service) und merken Sie sich diese in Ihrem Kalender vor, um sich auf die wichtigsten Aktivitäten für die Versionsveröffentlichung vorzubereiten.

## Aktualisierungsfehler {#update-failure}

AEM-Aktualisierungen durchlaufen eine intensive und vollautomatisierte Produktvalidierungs-Pipeline, die mehrere Schritte umfasst, um sicherzustellen, dass keine Unterbrechung des Services für in Produktion befindliche Systeme auftritt. Konsistenzprüfungen erlauben eine Überwachung des Zustands der Anwendung. Wenn diese Prüfungen bei einem AEM as a Cloud Service-Update fehlschlagen, wird die Versionsfreigabe nicht fortgesetzt. Adobe untersucht dann, warum das Update zu diesem unerwarteten Verhalten geführt hat.

Wenn Sie eine neue Version von benutzerdefiniertem Code in Ihrer Umgebung bereitstellen, spielen [produktbezogene und benutzerdefinierte Funktionstests](/help/implementing/cloud-manager/overview-test-results.md#functional-testing) eine entscheidende Rolle. Sie stellen sicher, dass die Produktionssysteme auch nach einer Änderung stabil und funktionsfähig bleiben. Diese Tests werden auch im Aktualisierungsprozess für die AEM-Version angewendet.

Wenn die Aktualisierung der Produktionsumgebung fehlschlägt, setzt Cloud Manager sie automatisch auf die Staging-Umgebung zurück. Dies erfolgt automatisch, um sicherzustellen, dass nach Abschluss einer Aktualisierung die Staging- und Produktionsumgebung auf derselben AEM-Version basieren.
Wenn die automatische Aktualisierung einer Entwicklungsumgebung fehlschlägt, werden Staging- und Produktionsumgebungen ebenfalls nicht aktualisiert.

>[!NOTE]
>
>Wenn benutzerdefinierter Code per Push in die Staging-Umgebung und nicht in die Produktionsumgebung übertragen wurde, werden die Änderungen mit dem nächsten AEM-Update entfernt, um das git-Tag der letzten erfolgreichen Kundenfreigabe in die Produktion widerzuspiegeln. Daher muss der benutzerdefinierte Code, der nur in der Staging-Umgebung verfügbar war, erneut bereitgestellt werden.

## Best Practices {#best-practices}

* **Nutzung der Staging-Umgebung**
   * Verwenden Sie für lange Qualitätssicherungs-/Benutzerakzeptanztest-Zyklen eine andere Umgebung als die Staging-Umgebung.
   * Nachdem die Integritätstests in der Staging-Umgebung abgeschlossen sind, fahren Sie mit einer Überprüfung in der Produktionsumgebung fort.

* **Produktions-Pipeline**
   * Pausieren Sie vor der Implementierung in der Produktion.
   * Wird die Pipeline nach einer Staging-Bereitstellung abgebrochen, deutet dies darauf hin, dass der Code „für die Tonne“ ist und nicht als zulässiger Kandidat für die Produktion infrage kommt. Siehe [Konfigurieren einer Produktions-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-production-pipelines.md).

* **Produktionsfremde Pipeline**
   * Konfigurieren Sie eine [produktionsfremde Pipeline](/help/implementing/cloud-manager/configuring-pipelines/configuring-non-production-pipelines.md#full-stack-code).
   * Beschleunigen Sie die Geschwindigkeit/Häufigkeit der Bereitstellung bei Fehlern in der Produktions-Pipeline. Identifizieren Sie Probleme in produktionsfremden Pipelines, indem Sie produktbezogene Funktionstests, benutzerdefinierte Funktionstests und benutzerdefinierte UI-Tests aktivieren.

* **Inhaltskopie**
   * Verwenden Sie eine [Inhaltskopie](/help/implementing/developing/tools/content-copy.md), um ähnliche Content-Sets in eine produktionsfremde Umgebung zu verschieben.

* **Automatisierte Funktionstests**
   * Schließen Sie automatisierte Tests in Ihre Pipeline ein, damit Sie kritische Funktionen testen können.
   * [Kundenfunktionstests](/help/implementing/cloud-manager/functional-testing.md#custom-functional-testing) und [Testen der benutzerdefinierten UI](/help/implementing/cloud-manager/functional-testing.md#custom-ui-testing) blockieren. Wenn sie fehlschlagen, wird die AEM-Freigabe nicht bereitgestellt.

## Regression {#regression}

Wenn ein Regressionsfehler auftritt, reichen Sie einen Support-Fall über die Admin Console ein. Wenn es sich bei dem Problem um einen Blocker handelt und es sich auf die Produktion auswirkt, sollte ein P1 gemeldet werden. Geben Sie alle Details an, die zum Reproduzieren des Regressionsproblems erforderlich sind.

## Zusammengesetzter Knotenspeicher {#composite-node-store}

Normalerweise verursachen Aktualisierungen keine Ausfallzeiten, auch nicht bei der Autoreninstanz, die aus einem Cluster von Knoten besteht. Rollierende Aktualisierungen sind aufgrund der [Composite Node Store-Funktion in Oak](https://jackrabbit.apache.org/oak/docs/nodestore/compositens.html) möglich.

Mithilfe dieser Funktion kann AEM auf mehrere Repositorys gleichzeitig verweisen. In einer [rollierenden Implementierung](/help/implementing/deploying/overview.md#how-rolling-deployments-work) enthält die neue AEM-Version ein eigenes `/libs` (das auf TarMK basierende, unveränderliche Repository). Es unterscheidet sich von der älteren AEM-Version, obwohl beide auf ein gemeinsames, auf DocumentMK basierendes veränderliches Repository verweisen, das Bereiche wie `/content`, `/conf` und `/etc` enthält.

Da sowohl die alte als auch die neue Version über ihre eigenen Versionen von `/libs` verfügen, können sie bei der rollierenden Aktualisierung beide aktiv bleiben, wobei beide Traffic aufnehmen, bis die alte vollständig durch die neue ersetzt wurde. 

## Weiterführende Informationen {#further-information}

Weitere Informationen zu verwandten Themen:

* [CI/CD-Pipelines in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md)
* [Benachrichtigung über die Cloud Manager-Benutzeroberfläche](/help/implementing/cloud-manager/notifications.md)
* [Die Architektur von Adobe Experience Manager as a Cloud Service](/help/overview/architecture.md)
