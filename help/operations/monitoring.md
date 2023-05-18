---
title: Infrastruktur- und Service-Überwachung in AEM as a Cloud Service
description: Infrastruktur- und Service-Überwachung in AEM as a Cloud Service
exl-id: 82432c11-37ec-48ac-a52b-487abdc859fa
source-git-commit: 34fed4e64b49ab32e7025c9654d930e3fa362a52
workflow-type: tm+mt
source-wordcount: '600'
ht-degree: 95%

---

# Infrastruktur- und Service-Überwachung in AEM as a Cloud Service {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service ermöglicht die Beobachtung und Überwachung von: Infrastruktur, Services und Anwendererlebnis. Da verschiedene Lösungen verwendet werden und es mehrere Überwachungsebenen gibt, ist diese Seite in drei Abschnitte unterteilt:

* [Externe Verfügbarkeit](#external-availability)
* [Interne Modulüberwachung](#module-monitoring)
* [Kundenbeobachtung](#customer-observability)

AEM as a Cloud Service verwendet Hunderte Cloud-native Monitore, um den Status jeder Umgebung (rund um die Uhr) kontinuierlich 365 Tage im Jahr zu melden. Die Monitordefinitionen sind nicht statisch, sie werden kontinuierlich überprüft, um die Früherkennungsfunktion zu verbessern. Darüber hinaus gibt es in Adobe abrufbereite Verfahren für die Reaktion auf Warnhinweise.

Informationen zu anderen Arten der Überwachung, wie z. B. Protokollierung oder Überwachung mithilfe von Cloud Manager, finden Sie im Abschnitt [Zusätzliche Ressourcen](#resources).

## Externe Verfügbarkeit {#external-availability}

Die externe Verfügbarkeit besteht aus zwei Teilen: Service Edge und benutzerdefinierte Überwachung.

### Service Edge {#service-edge}

Alle Ihre Umgebungen in AEM as a Cloud Service werden auf Verfügbarkeit überwacht. Service Edge Monitoring ist jedoch nur für Produktionsumgebungen eingerichtet und die Metriken werden zur Berechnung des SLA des Kunden verwendet. Dabei werden die Umgebungslaufzeit und das AEM as a Cloud Service CDN berücksichtigt. Service Edge Monitoring nutzt fünf verschiedene Standorte in der Nähe Ihrer ausgewählten Region und überprüft regelmäßig die Verfügbarkeit. Wenn eine Site nicht verfügbar ist, wird ein Warnhinweis ausgelöst und die einsatzbereiten Support-Teams und -prozesse von Adobe werden aktiviert.

### Benutzerdefinierte Überwachung {#custom-monitoring}

Bei der benutzerdefinierten Überwachung haben Kunden die Möglichkeit, bis zu fünf verschiedene Web-Property-URLs anzugeben, bevor sie [aktiviert werden](/help/journey-migration/go-live.md). Diese URLs sollten gültig sein und den HTTP-Antwort-Code 200 zurückgeben. Diese Monitore unterstützen Kunden, die [ihre eigenes CDN vor das Adobe CDN schalten](/help/implementing/dispatcher/cdn.md#point-to-point-CDN), sowie ein externes Traffic-Routing, das vor AEM as a Cloud Service stattfindet und nicht unter der Kontrolle von Adobe ist. Warnhinweise, die sich aus benutzerdefinierten Überwachungsaktivitäten ergeben, werden an die Support-Teams und -Prozesse von Adobe weitergeleitet.

>[!NOTE]
>
> Diese Funktion steht nur Kunden mit erweiterter Cloud-Unterstützung zur Verfügung. Wenn Sie Fragen haben, stellen Sie bitte über die Admin Console einen Support-Fall auf.

## Interne Modulüberwachung {#module-monitoring}

Während sich die externe Verfügbarkeit auf die Überwachung der Endanwender konzentriert, wird bei der internen Modulüberwachung beobachtet, ob die architektonischen Untersysteme normal funktionieren, ohne dass Funktionen oder die Leistung beeinträchtigt wird. Wenn ein Problem auftritt, werden Warnhinweise ausgelöst, damit Reparaturen entweder automatisch oder unter Beteiligung des Betriebs-Teams durchgeführt werden können, um eine eingeschränkte Verfügbarkeit zu verhindern. Es gibt verschiedene Kategorien von Monitoren. Nachfolgend finden Sie einige Beispiele für Überprüfungen:

* Der Iowait-Prozentsatz der CPU überschreitet einen bestimmten Schwellenwert nicht.
* Die Neubereitstellung von Instanzen überschreitet eine bestimmte Häufigkeit nicht.
* Die Festplattenauslastung liegt unter einem bestimmten Schwellenwert.
* Die Größe des Autoren-Repositorys liegt innerhalb bestimmter Grenzen.
* Backup-Vorgänge wurden erfolgreich abgeschlossen.
* Status und Leistung der Datenbank werden überwacht.
* AEM Cloud-Services verhalten sich erwartungsgemäß und weisen keine blockierten Replikations-Warteschlangen, inkonsistenten Daten und fehlgeschlagene Abfragen auf.

Zusätzliche Prüfungen werden den für Forms bereitgestellten Umgebungen hinzugefügt. Beachten Sie, dass die Definitionen der Prüfung nicht statisch sind und Änderungen und Aktualisierungen unterliegen.

## Kundenbeobachtung {#customer-observability}

Kunden können die Suite [New Relic-Anwendungsleistungsüberwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html?lang=de) verwenden, die Echtzeit-Leistungsdaten bereitstellt, die für die Analyse und Fehlerbehebung erfasst und grafisch dargestellt werden. Mithilfe der Monitoring-Suite können Kunden verschiedene Metriken direkt beobachten, z. B.: JVM-Leistungsmetriken, Transaktionszeit für Java, externe Aufrufe und Datenbankaufrufe im Hintergrund.

## Zusätzliche Ressourcen {#resources}

* [New Relic-Anwendungsleistungsüberwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html?lang=de)
* [Protokollierung für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html?lang=de)
* [Überwachen von Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html?lang=de)
