---
title: Bereitstellung von AEM-Inhaltsfragmenten mit OpenAPI
description: Erfahren Sie mehr über die Bereitstellung von AEM-Inhaltsfragmenten mit OpenAPI
feature: Headless, Content Fragments, Edge Delivery Services
role: Admin, Developer
exl-id: b298db37-1033-4849-bc12-7db29fb77777
source-git-commit: dd7d2b5553e4ecac7a9955e83da1cab077c74127
workflow-type: tm+mt
source-wordcount: '551'
ht-degree: 86%

---


# Bereitstellung von AEM-Inhaltsfragmenten mit OpenAPI {#aem-content-fragment-delivery-with-openapi}

In Adobe Experience Manager (AEM) as a Cloud Service umfasst die AEM OpenAPI für die Bereitstellung von Inhaltsfragmenten Folgendes:

* Sie ist ein OpenAPI, das für die Live-Bereitstellung von AEM-Inhaltsfragmenten im JSON-Format optimiert ist.
* Sie bietet eine moderne CDN-Integration, die die Invalidierung aktiver Inhalte ermöglicht.
* Sie konzentriert sich auf die Bereitstellung von Inhalten (Leistung, Skalierbarkeit, CDN-Integration, optimierte JSON-Steuerung und -Ausgabe).
* Sie umfasst die Möglichkeit, JSON für referenzierte Fragmente und Assets einzubinden.

Diese API:

* ist die Nachfolgerin der [Unterstützung für Inhaltsfragmente in der AEM-Assets-HTTP-API](/help/assets/content-fragments/assets-api-content-fragments.md).

* ergänzt die OpenAPIs mit [Inhaltsfragmenten und Inhaltsfragmentmodellen](/help/headless/content-fragment-openapis.md), mit denen Sie die Inhaltsfragmente und Inhaltsfragmentmodelle (CRUD) verwalten können.

* ist eine HTTP-REST-Alternative zur [AEM-GraphQL-API zur Verwendung mit Inhaltsfragmenten](/help/headless/graphql-api/content-fragments.md).

Die vollständige Dokumentation finden Sie unter [Bereitstellung von AEM-Inhaltsfragmenten mit OpenAPI](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/contentfragments/delivery/?lang=de).

>[!NOTE]
>
>Unter [AEM-APIs für die Bereitstellung und Verwaltung strukturierter Inhalte](/help/headless/apis-headless-and-content-fragments.md) finden Sie einen Überblick über die verschiedenen verfügbaren APIs und einen Vergleich einiger der damit verbundenen Konzepte.

>[!IMPORTANT]
>
>Um die Bereitstellung von Inhaltsfragmenten mit OpenAPI in AEM as a Cloud Service zu aktivieren, stellen Sie sicher, dass sie nicht bereits aktiviert ist. Reichen Sie dann ein Adobe-Support-Ticket mit dem Titel **Bereitstellung von Inhaltsfragmenten mit OpenAPI aktivieren** ein und geben Sie Folgendes an:
>
>* die ID(s) des Cloud Service-Programms und der Umgebung
>* Details des Anwendungsfalls, den Sie mit der OpenAPI für die Bereitstellung von Inhaltsfragmenten lösen möchten
>* Details zu allen Kontakten, auf die Adobe reagieren sollte, sowie Informationen zu Anfrage und Projekt (falls erforderlich)

## Caching {#caching}

AEM integriert sich in das AEM CDN Fastly. Das bedeutet, dass auf der Veröffentlichungsstufe bereitgestellte JSON-Antworten auf der Fastly-Ebene zwischengespeichert werden.

Antworten werden dann zwischengespeichert, basierend auf vordefinierten Zwischenspeicherkopfzeilen (können nicht konfiguriert werden):

* Antworten werden 5 Minuten lang im Browser-/Client-Cache zwischengespeichert.
   * `max-age`=`300`
* Antworten werden 1 Stunde lang im CDN-Cache zwischengespeichert.
   * `s-maxage`=`3600`
* Veraltete Inhalte können bei der erneuten Validierung neuer Anforderungen für bis zu 1 Stunde bereitgestellt werden.
   * `stale-while-revalidate`=`3600`
* Veraltete Inhalte können mit einem Fehler bis zu 1 Tag lang bereitgestellt werden.
   * `stale-on-error`=`86400`

Die Bereitstellung von Inhaltsfragmenten mit OpenAPI unterstützt die Invalidierung des aktiven CDN-Caches. Das bedeutet, dass bei jeder Aktualisierung oder Veröffentlichung von Inhalten die entsprechenden JSON OpenAPI-Antworten über eine Soft-Bereinigungsanfrage an Fastly automatisch invalidiert werden. Auf diese Weise können Sie Änderungen sehen, die sich in der JSON-Ausgabe widerspiegeln, bevor die tatsächliche CDN-Cache-Seite (`s-maxage`) erreicht wird.

## Verfügbarkeit {#availability}

Die Bereitstellung von Inhaltsfragmenten mit OpenAPI ist auf der Vorschau- und Veröffentlichungsebene verfügbar. Die OpenAPI stellt Inhaltsfragmente im JSON-Format für die Vorschau und die Live-Bereitstellung bereit.

Für die Vorschau ermöglicht die Bereitstellung von Inhaltsfragmenten mit OpenAPI Folgendes:

* Veröffentlichen in der Vorschau
* Aktivieren des Zugriffs auf die Vorschau mit einer IP-Zulassungsliste
* Abrufen der Vorschau-URL

## CORS {#cors}

[Zulässige CORS-Ursprünge](/help/headless/deployment/cross-origin-resource-sharing.md) definieren die Ursprünge, die das API aufrufen können.

Die auf der Dispatcher-Konfigurationsseite definierten zulässigen CORS-Ursprünge, speziell für GraphQL, werden von diesem API nicht berücksichtigt.

## API-Ratenbeschränkungen {#api-rate-limits}

Die -API ermöglicht neue Anfragen mit einer Rate von bis zu 200 Anfragen pro Sekunde und Umgebung.

Sobald dieses Limit überschritten wird, beginnt die API mit dem Senden von [429](https://www.rfc-editor.org/rfc/rfc6585#section-4)Fehlerantworten. Diese Fehler müssen von allen Client-Anwendungen verarbeitet werden, und fehlgeschlagene Anfragen müssen nach einem exponentiellen Backoff-Versuch erneut versucht werden. Die HTTP-Antwort enthält eine bestimmte Kopfzeile, `Retry-After`, die dem Client angibt, wie lange er warten muss, bevor er die Anfrage erneut sendet.

<!-- 
## Limitations {#limitations}
-->
