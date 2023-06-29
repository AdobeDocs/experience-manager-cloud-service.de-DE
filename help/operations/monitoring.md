---
title: Infrastruktur- und Service-Überwachung in AEM as a Cloud Service
description: Infrastruktur- und Service-Überwachung in AEM as a Cloud Service
exl-id: 82432c11-37ec-48ac-a52b-487abdc859fa
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '588'
ht-degree: 46%

---

# Infrastruktur- und Service-Überwachung in AEM as a Cloud Service {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service bietet Beobachtbarkeit und Überwachung von: Infrastruktur, Dienste und Benutzererfahrung. Da verschiedene Lösungen verwendet werden und es mehrere Überwachungsebenen gibt, ist diese Seite in drei Abschnitte unterteilt:

* [Externe Verfügbarkeit](#external-availability)
* [Interne Modulüberwachung](#module-monitoring)
* [Kundenbeobachtung](#customer-observability)

AEM as a Cloud Service verwendet Hunderte Cloud-native Monitore, um den Status jeder Umgebung (rund um die Uhr) kontinuierlich 365 Tage im Jahr zu melden. Die Monitordefinitionen sind nicht statisch, sie werden kontinuierlich überprüft, um die Früherkennungsfunktion zu verbessern. Darüber hinaus gibt es in der Adobe Verfahren für die Reaktion auf Warnhinweise.

Wenn Sie Informationen zu anderen Arten der Überwachung benötigen, wie z. B. Protokollierung oder Überwachung über Cloud Manager, finden Sie unter [Zusätzliche Ressourcen](#resources).

## Externe Verfügbarkeit {#external-availability}

Die externe Verfügbarkeit besteht aus zwei Teilen: Service Edge und benutzerdefinierte Überwachung.

### Service Edge {#service-edge}

Alle Umgebungen AEM as a Cloud Service werden auf Verfügbarkeit überwacht. Service Edge Monitoring ist jedoch nur für Produktionsumgebungen eingerichtet und die Metriken werden zur Berechnung des SLA des Kunden verwendet. Dabei werden die Umgebungslaufzeit und das AEM as a Cloud Service CDN berücksichtigt. Service Edge Monitoring nutzt fünf verschiedene Standorte in der Nähe Ihrer ausgewählten Region und überprüft regelmäßig die Verfügbarkeit. Die Nichtverfügbarkeit einer Site Trigger einen Warnhinweis und interagiert die On-Call-Support-Teams und -Prozesse der Adobe.

### Benutzerdefinierte Überwachung {#custom-monitoring}

Mit der benutzerdefinierten Überwachung können Kunden optional bis zu fünf verschiedene Webeigenschafts-URLs bereitstellen, bevor [live](/help/journey-migration/go-live.md). Diese URLs sollten gültig sein und den HTTP-Antwort-Code 200 zurückgeben. Diese Monitore unterstützen Kunden, die [eigene CDN](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) vor dem CDN der Adobe und vor AEM as a Cloud Service, nicht unter der Kontrolle der Adobe stehenden externen Verkehrsträgern. Warnhinweise, die aus benutzerdefinierten Überwachungsprüfungen resultieren, interagieren mit den Supportteams und Prozessen der Adobe.

>[!NOTE]
>
> Diese Funktion steht nur Kunden mit [Erweiterte Cloud-Unterstützung.](https://experienceleague.adobe.com/docs/support-resources/data-sheets/overview.html#support-add-ons) Wenden Sie sich bei Fragen an das Kundenbetreuungsteam Ihrer Adobe.

## Interne Modulüberwachung {#module-monitoring}

Während sich die externe Verfügbarkeit auf die Überwachung der Endbenutzer konzentriert, wird bei der internen Modulüberwachung beobachtet, ob die architektonischen Untersysteme normal funktionieren, ohne dass Funktionen oder Leistungsbeeinträchtigungen auftreten. Wenn ein Problem auftritt, werden Warnhinweise ausgelöst, damit Reparaturen entweder automatisch oder unter Beteiligung des Betriebsteams durchgeführt werden können, um eine kompromittierte Verfügbarkeit zu verhindern. Es gibt verschiedene Kategorien von Monitoren. Nachfolgend finden Sie einige Beispiele für Überprüfungen:

* Der Iowait-Prozentsatz der CPU überschreitet einen bestimmten Schwellenwert nicht.
* Die Neubereitstellung von Instanzen überschreitet eine bestimmte Häufigkeit nicht.
* Die Festplattenauslastung liegt unter einem bestimmten Schwellenwert.
* Die Größe des Autoren-Repositorys liegt innerhalb bestimmter Grenzen.
* Backup-Vorgänge wurden erfolgreich abgeschlossen.
* Der Zustand und die Leistung der Datenbank werden überwacht.
* AEM Cloud-Services verhalten sich erwartungsgemäß, einschließlich blockierter Replikations-Warteschlangen, konsistenter Daten und leistungsfähiger Abfragen.

Zusätzliche Prüfungen werden den für Forms bereitgestellten Umgebungen hinzugefügt. Überprüfungsdefinitionen sind nicht statisch und unterliegen Änderungen und Aktualisierungen.

## Kundenbeobachtung {#customer-observability}

Kunden können [Leistungsüberwachung von New Relic-Anwendungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html?lang=de) Suite, die Echtzeit-Leistungsdaten bereitstellt, die für die Analyse und Fehlerbehebung erfasst und kartiert werden. Mithilfe der Monitoring-Suite können Kunden verschiedene Metriken direkt beobachten, z. B.: JVM-Leistungsmetriken, Transaktionszeit für Java™, externe Hintergrundaufrufe und Datenbankaufrufe.

## Zusätzliche Ressourcen {#resources}

* [New Relic-Anwendungsleistungsüberwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html?lang=de)
* [Protokollierung für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html?lang=de)
* [Überwachen von Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html?lang=de)
