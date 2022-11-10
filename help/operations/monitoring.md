---
title: Infrastruktur- und Dienstleistungsüberwachung in AEM as a Cloud Service
description: Infrastruktur- und Dienstleistungsüberwachung in AEM as a Cloud Service
source-git-commit: 8121d2e9cd98b4cc6e848f6cd6c3fa4359988053
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---


# Infrastruktur- und Dienstleistungsüberwachung in AEM as a Cloud Service {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service bietet Beobachtbarkeit und Überwachung von: Infrastruktur, Dienste und Benutzererfahrung. Da verschiedene Lösungen verwendet werden und es mehrere Überwachungsebenen gibt, ist diese Seite in drei Abschnitte unterteilt:

* [Externe Verfügbarkeit](#external-availability)
* [Interne Modulüberwachung](#module-monitoring)
* [Kundenbeobachtung](#customer-observability)

AEM as a Cloud Service verwendet Hunderte Cloud-native Monitore, um den Status jeder Umgebung (rund um die Uhr) kontinuierlich 365 Tage im Jahr zu melden. Die Monitordefinitionen sind nicht statisch, sie werden kontinuierlich überprüft, um die Früherkennungsfunktion zu verbessern. Darüber hinaus gibt es in Adobe Verfahren für die Reaktion auf Warnhinweise.

Wenn Sie Informationen zu anderen Arten der Überwachung benötigen, wie z. B. Protokollierung oder Überwachung über Cloud Manager, finden Sie im Abschnitt [Zusätzliche Ressourcen](#resources) Abschnitt.

## Externe Verfügbarkeit {#external-availability}

Die externe Verfügbarkeit besteht aus zwei Teilen: Service Edge und benutzerdefinierte Überwachung.

### Service Edge {#service-edge}

Alle Ihre AEM as a Cloud Service Umgebungen werden auf Verfügbarkeit überwacht. Service Edge Monitoring ist jedoch nur für Produktionsumgebungen eingerichtet und die Metriken werden zur Berechnung der SLA des Kunden verwendet. Dabei werden die Umgebungslaufzeit und das AEM as a Cloud Service CDN berücksichtigt. Service Edge Monitoring nutzt fünf verschiedene Standorte in der Nähe Ihrer ausgewählten Region und überprüft regelmäßig die Verfügbarkeit. Wenn eine Site nicht verfügbar ist, wird ein Warnhinweis Trigger und die Bereitstellungsteams und -prozesse der Adobe werden einbezogen.

### Benutzerdefinierte Überwachung {#custom-monitoring}

Bei der benutzerdefinierten Überwachung haben Kunden die Möglichkeit, bis zu fünf verschiedene Webeigenschafts-URLs vor [live](/help/journey-migration/go-live.md). Diese URLs sollten gültig sein und einen HTTP 200-Antwortcode zurückgeben. Diese Monitore unterstützen Kunden, die [eigene CDN](/help/implementing/dispatcher/cdn.md#point-to-point-CDN) vor dem CDN der Adobe und vor AEM as a Cloud Service, nicht unter der Kontrolle der Adobe stehenden externen Verkehrsträgern. Warnhinweise, die aus benutzerdefinierten Überwachungsprüfungen resultieren, binden die Supportteams und Prozesse der Adobe ein.

## Interne Modulüberwachung {#module-monitoring}

Während sich die externe Verfügbarkeit auf die Überwachung der Endbenutzer konzentriert, wird bei der internen Modulüberwachung beobachtet, ob die architektonischen Untersysteme normal funktionieren, ohne dass Funktionen oder Leistungsbeeinträchtigungen auftreten. Im Fall eines Problems werden Warnhinweise ausgelöst, damit Reparaturen entweder automatisch oder unter Beteiligung des Einsatzteams durchgeführt werden können, um eine kompromittierte Verfügbarkeit zu verhindern. Es gibt verschiedene Kategorien von Monitoren. Nachfolgend finden Sie einige Beispielprüfungen:

* Der Prozentsatz der CPU-Iowait überschreitet einen bestimmten Schwellenwert nicht.
* Die Neubereitstellung von Instanzen überschreitet eine bestimmte Häufigkeit nicht.
* Die Festplattenauslastung liegt unter einem bestimmten Schwellenwert.
* Die Größe des Autoren-Repositorys liegt innerhalb bestimmter Grenzen.
* Sicherungsvorgänge wurden erfolgreich abgeschlossen.
* Der Zustand und die Leistung der Datenbank werden überwacht.
* AEM Cloud-Services verhalten sich erwartungsgemäß, einschließlich blockierter Replikations-Warteschlangen, konsistenter Daten und leistungsfähiger Abfragen.

Zusätzliche Prüfungen werden den für Forms bereitgestellten Umgebungen hinzugefügt. Beachten Sie, dass die Definitionen der Prüfung nicht statisch sind und Änderungen und Aktualisierungen unterliegen.

## Kundenbeobachtung {#customer-observability}

Kunden können [Neue Überwachung der relativen Anwendungsleistung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html) Suite, die Echtzeit-Leistungsdaten bereitstellt, die für die Analyse und Fehlerbehebung erfasst und kartiert werden. Mithilfe der Monitoring-Suite können Kunden verschiedene Metriken direkt beobachten, z. B.: JVM-Leistungsmetriken, Transaktionszeit für Java, externe Hintergrundaufrufe und Datenbankaufrufe.

## Zusätzliche Ressourcen {#resources}

* [Neue Überwachung der relativen Anwendungsleistung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html)
* [Protokollierung für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html)
* [Überwachen von Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html)
