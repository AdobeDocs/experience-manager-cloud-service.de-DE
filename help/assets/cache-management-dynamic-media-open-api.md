---
title: Cache-Verwaltung in Dynamic Media mit offenen APIs
description: Cache-Verwaltung in Dynamic Media mit offenen APIs
role: User
source-git-commit: 89f21f96a741acbd6458c3777227548fbc89e525
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 1%

---

# Cache-Verwaltung in Dynamic Media mit offenen APIs {#cache-management-dynamic-media-open-apis}

Eine effektive Cache-Verwaltung ist für die Bereitstellung hochleistungsfähiger, skalierbarer und aktueller digitaler Assets unerlässlich. In Dynamic Media mit offenen APIs definiert die Cache-Verwaltung, wie Inhalte über die verschiedenen Ebenen der Bereitstellungs-Pipeline gespeichert, aktualisiert und bereitgestellt werden. Die Antworten zur Asset-Bereitstellung werden auf mehreren Ebenen zwischengespeichert, um eine optimale Leistung und eine schnelle Inhaltsbereitstellung zu gewährleisten.

Längeres Caching in Dynamic Media mit offenen APIs besteht aus [CDN-Ebenen-Caching](#cdn-layer-caching) und [Externer Cache-Steuerung (BYOCDN- und Browser-Caching)](#byocdn-browser-caching).

## CDN-Ebenen-Caching {#cdn-layer-caching}

Die Antworten auf die Asset-Bereitstellung werden über einen längeren Zeitraum im [Adobe Managed CDN](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn#aem-managed-cdn) zwischengespeichert, um die Leistung zu maximieren und die Auslastung der Quelle zu minimieren. Diese Zwischenspeicherung wird vollständig von Adobe verwaltet, um Endbenutzern ein einheitlich hochwertiges Erlebnis zu gewährleisten. Die Aufbewahrungsfrist im Cache ist absichtlich leistungsoptimiert und kann von Benutzenden nicht angepasst werden, um die Zuverlässigkeit und effiziente Bereitstellung von Inhalten für alle Kundinnen und Kunden zu gewährleisten.

Alle Versand-URLs werden über einen längeren Zeitraum am Edge (Fastly) zwischengespeichert, um eine optimale Leistung zu gewährleisten. Die zwischengespeicherten Versandobjekte umfassen statische Ausgabedarstellungen, Videos, Binärdateien für Originalbilder und dynamisch umgewandelte Bilder wie skalierte oder neu formatierte Assets, die über URL-Parameter generiert wurden. <!--The CDN is designed to serve these assets directly from the cache without revalidating them, unless an explicit purge is performed.-->

## Externe Cache-Steuerung (BYOCDN- und Browser-Caching) {#byocdn-browser-caching}

Die Antworten zur Asset-Bereitstellung enthalten eine `Cache-Control`-Kopfzeile mit einer `max-age` von **10 Minuten** für nachgelagerte Caching-Ebenen. Dies gilt für benutzerdefinierte *Bring-Your-Own-CDN (BYOCDN*-Konfigurationen, *Endbenutzer-Browser* und alle *Zwischenzwischengespeicherten Caching-Proxys*, um eine konsistente Cache-Steuerung über den gesamten Versandpfad hinweg sicherzustellen.

### Anpassen von Cache-Control-Kopfzeilen {#customizing-cache-control-headers}

Wenn Sie die Cache-Zeit bis zum Erreichen der Live-Werte über die Standardkonfiguration hinaus erhöhen, erhöht sich die Wahrscheinlichkeit, veraltete Inhalte bereitzustellen, was die Sichtbarkeit von Inhaltsaktualisierungen im Endbenutzererlebnis verzögern kann. Wenn Sie das Verhalten der Cache-Steuerung für Ihren spezifischen Anwendungsfall ändern müssen, können Sie benutzerdefinierte CDN-Regeln konfigurieren, um Antwort-Header anzupassen. Auf diese Weise können Sie je nach Ihren Anforderungen unterschiedliche Aufbewahrungsfristen im Cache festlegen. Siehe [Benutzerdefinierte CDN-Regeln von AEM für Antwort-Header](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-configuring-traffic).

```
responseTransformations:
    rules:
      - name: cache-asset-delivery
        when:
          allOf:
            - reqProperty: path
              like: '/adobe/assets/urn:aaid:aem:*'
            - reqProperty: tier
              equals: delivery
        actions:
          - type: set
            respHeader: Cache-Control
            value: max-age=300
```

Wenden Sie sich bei weiteren Fragen zur Cache-Verwaltung an den [Adobe-Support](https://helpx.adobe.com/de/contact.html).

## Active Cache Invalidation {#active-cache-invalidation}

Jedes Mal, wenn ein Asset aktualisiert, gelöscht oder geändert wird (alle Metadatenänderungen), macht Dynamic Media mit Open APIs automatisch alle zugehörigen Versand-URLs im Adobe Managed CDN ungültig. Dies gilt für URLs, die Vanity-IDs oder Aliase verwenden, sowie für URLs, die Transformationsparameter wie Breite, Format oder Qualität enthalten. Diese ereignisgesteuerte Invalidierung stellt sicher, dass Ihre Benutzer immer die neueste Version Ihrer Assets erhalten, ohne manuell eingreifen zu müssen.

### Manuelle Cache-Bereinigung {#manual-cache-purging}

Wenn zwischengespeicherte Inhalte manuell gelöscht werden müssen, können Sie dies mithilfe der Cache-Invalidierungsfunktionen von AEM tun. Detaillierte Anweisungen zum Bereinigen bestimmter Cache-URLs finden Sie unter [AEM CDN Cache Invalidation](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/content-delivery/cdn-cache-purge#single-purge).

## Häufig gestellte Fragen{#faq-cache-management}

+++**Wie wirkt sich die Cache-Verwaltung auf vorhandene Integrationen aus?**

Asset-URLs bleiben unverändert, und der Cache-Control-Header, der an Browser (und andere nachgelagerte Intermediäre) vom Adobe Managed CDN gesendet wird, beträgt weiterhin 10 Minuten mit einer [`stale-while-revalidate directive`](https://web.dev/articles/stale-while-revalidate#whats_it_mean), sodass sichergestellt ist, dass nachgelagerte Systeme ihre Caches weiterhin optimal nutzen.

+++

+++**Welche Trigger gibt es bei einer Cache-Bereinigung?**

Die Cache-Bereinigung führt automatisch zu Triggern, wenn ein Asset aktualisiert, geändert, archiviert oder gelöscht wird.

<!--The cache purge triggers automatically in the following circumstances:
 
 - when an asset is updated, modified, or archived.
 - when an asset reaches `ready_for_delivery` state after approval.-->

+++

<!--
+++ **How long does it take for the cache to refresh after updating an asset?**

Any time the asset changes, the cache refreshes usually in *less than 60 seconds*.

+++

<!--
+++ **What happens if the cache purge system fails?**
The following mechanisms can be followed:
 
 - **Automatic retries:** 3 retry attempts with exponential backoff
 - **Monitoring:** Sev-2 alert fires if staleness exceeds 10 minutes
 - **Natural expiry:** Even without purge, cache expires after 10 hours maximum
 - **Manual override:** Engineers can manually purge via CLI tool

+++
-->

+++ **Welche Asset-Typen werden für das Caching mit langer Lebensdauer unterstützt?**

Die verlängerte Zwischenspeicherung mit ereignisgesteuerter aktiver Cache-Invalidierung gilt für alle Asset-Typen in Dynamic Media mit offenen APIs, unabhängig vom Asset-Typ oder -Format.

+++

+++ **Kann ich die langlebige Zwischenspeicherung für mein Repository deaktivieren?**

Sie können sich an den [Adobe-Support wenden](https://helpx.adobe.com/de/contact.html) um die Gründe zu erklären. Adobe wird sich dann zwecks Diskussion mit Ihnen in Verbindung setzen.

+++


>[!MORELIKETHIS]
>
>- [Integrieren des Asset-Wählers in verschiedene Anwendungen](/help/assets/integrate-asset-selector.md)
>- [Vanity-URL](/help/assets/vanity-urls.md)
