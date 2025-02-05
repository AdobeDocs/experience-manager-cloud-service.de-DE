---
title: Infrastruktur- und Service-Überwachung in AEM as a Cloud Service
description: Infrastruktur- und Service-Überwachung in AEM as a Cloud Service
exl-id: 82432c11-37ec-48ac-a52b-487abdc859fa
feature: Operations
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 95%

---

# Infrastruktur- und Service-Überwachung in AEM as a Cloud Service {#monitoring-in-aem-as-a-cloud-service}

Adobe Experience Manager as a Cloud Service ermöglicht die Beobachtung und Überwachung von: Infrastruktur, Diensten und Anwendererlebnis. Da verschiedene Lösungen verwendet werden und es mehrere Überwachungsebenen gibt, ist diese Seite in drei Abschnitte unterteilt:

* [Externe Verfügbarkeit](#external-availability)
* [Interne Modulüberwachung](#module-monitoring)
* [Kundenbeobachtung](#customer-observability)

AEM as a Cloud Service verwendet Hunderte Cloud-native Monitore, um den Status jeder Umgebung (rund um die Uhr) kontinuierlich 365 Tage im Jahr zu melden. Die Monitordefinitionen sind nicht statisch, sie werden kontinuierlich überprüft, um die Früherkennungsfunktion zu verbessern. Darüber hinaus gibt es bei Adobe einen Satz abrufbereiter Verfahren für die Reaktion auf Warnhinweise.

Informationen zu anderen Arten der Überwachung, wie z. B. Protokollierung oder Überwachung mithilfe von Cloud Manager, finden Sie im Abschnitt [Zusätzliche Ressourcen](#resources).

## Externe Verfügbarkeit {#external-availability}

Die externe Verfügbarkeit besteht aus zwei Teilen: Service Edge und benutzerdefinierte Überwachung.

### Service Edge {#service-edge}

Alle Ihre Umgebungen in AEM as a Cloud Service werden auf Verfügbarkeit überwacht. Service Edge Monitoring ist jedoch nur für Produktionsumgebungen eingerichtet und die Metriken werden zur Berechnung des SLA des Kunden verwendet. Dabei werden die Umgebungslaufzeit und das AEM as a Cloud Service CDN berücksichtigt. Service Edge Monitoring nutzt fünf verschiedene Standorte in der Nähe Ihrer ausgewählten Region und überprüft regelmäßig die Verfügbarkeit. Wenn eine Site nicht verfügbar ist, wird ein Warnhinweis ausgelöst und die einsatzbereiten Support-Teams von Adobe und die entsprechenden Prozesse werden aktiviert.

### Benutzerdefinierte Überwachung {#custom-monitoring}

Mit der benutzerdefinierten Überwachung können Kundinnen und Kunden optional bis zu fünf verschiedene Web-Eigenschafts-URLs bereitstellen, bevor sie [live](/help/journey-migration/go-live.md) gehen. Diese URLs sollten gültig sein und den HTTP-Antwort-Code 200 zurückgeben. Diese Monitore unterstützen Kundinnen und Kunden, die [ihre eigenes CDN vor das Adobe CDN schalten](/help/implementing/dispatcher/cdn.md#point-to-point-CDN), sowie ein externes Traffic-Routing, das vor AEM as a Cloud Service stattfindet und nicht unter der Kontrolle von Adobe ist. Warnhinweise, die sich aus benutzerdefinierten Überwachungsaktivitäten ergeben, werden an die Support-Teams von Adobe weitergeleitet und aktivieren die entsprechenden Prozesse.

>[!NOTE]
>
> Diese Funktion steht nur Produktionsumgebungen und Kunden mit &quot;[ Cloud-Support“ ](https://experienceleague.adobe.com/docs/support-resources/data-sheets/overview.html?lang=de#support-add-ons). Bei Fragen wenden Sie sich bitte an Ihr Adobe-Account-Team.

## Interne Modulüberwachung {#module-monitoring}

Während sich die externe Verfügbarkeit auf die Überwachung der Endbenutzenden konzentriert, wird bei der internen Modulüberwachung beobachtet, ob die Untersysteme der Architektur normal funktionieren, ohne dass Funktionen oder die Leistung beeinträchtigt wird. Wenn ein Problem auftritt, werden Warnhinweise ausgelöst, damit Reparaturen entweder automatisch oder unter Beteiligung des Betriebs-Teams durchgeführt werden können, um eine Beeinträchtigung der Verfügbarkeit zu verhindern. Es gibt verschiedene Kategorien von Monitoren. Nachfolgend finden Sie einige Beispiele für Überprüfungen:

* Der Iowait-Prozentsatz der CPU überschreitet einen bestimmten Schwellenwert nicht.
* Die Neubereitstellung von Instanzen überschreitet eine bestimmte Häufigkeit nicht.
* Die Festplattenauslastung liegt unter einem bestimmten Schwellenwert.
* Die Größe des Autoren-Repositorys liegt innerhalb bestimmter Grenzen.
* Backup-Vorgänge wurden erfolgreich abgeschlossen.
* Status und Leistung der Datenbank werden überwacht.
* AEM Cloud-Services verhalten sich erwartungsgemäß und weisen keine blockierten Replikations-Warteschlangen, inkonsistenten Daten und fehlgeschlagenen Abfragen auf.

Zusätzliche Prüfungen werden für die für Forms bereitgestellten Umgebungen hinzugefügt. Überprüfungsdefinitionen sind nicht statisch und unterliegen Änderungen und Aktualisierungen.

## Kundenseitige Beobachtung {#customer-observability}

Kundinnen und Kunden können die Suite [New Relic-Anwendungsleistungsüberwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html?lang=de) verwenden, die in Echtzeit erfasste Leistungsdaten bereitstellt und sie für die Analyse und Fehlerbehebung grafisch darstellt. Mithilfe der Monitoring-Suite können Kundinnen und Kunden verschiedene Metriken direkt beobachten, z. B. JVM-Leistungsmetriken, Transaktionszeit für Java™, externe Aufrufe im Hintergrund und Datenbankaufrufe.

## Zusätzliche Ressourcen {#resources}

* [New Relic-Anwendungsleistungsüberwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/user-access-new-relic.html?lang=de)
* [Protokollierung für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/logging.html?lang=de)
* [Überwachen von Umgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/using/monitoring-environments.html?lang=de)
