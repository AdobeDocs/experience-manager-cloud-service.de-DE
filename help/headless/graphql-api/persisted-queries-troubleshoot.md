---
title: Fehlerbehebung bei persistenten GraphQL-Abfragen
description: Erfahren Sie, wie Sie Probleme mit persistenten GraphQL-Abfragen in Adobe Experience Manager as a Cloud Service beheben können.
feature: Content Fragments,GraphQL API
source-git-commit: c8ea9846600d1773e6f269973635f5338f31906f
workflow-type: tm+mt
source-wordcount: '353'
ht-degree: 0%

---


# Fehlerbehebung bei persistenten GraphQL-Abfragen {#troubleshoot-persisted-graphql-queries}

Die [Aktionszentrum](/help/operations/actions-center.md) enthält die **Persistenter Abfragefehler von GraphQL** Warnhinweis. Dies bedeutet, dass Sie immer dann informiert werden, wenn eine der von GraphQL gespeicherten Abfragen einen Fehler ausgibt.

Um Ihnen bei der Fehlerbehebung und Lösung solcher Probleme zu helfen, erläutern wir die *am häufigsten* Ursachen von Fehlern und Schritte zu deren Behebung.

## Änderungen am Inhaltsfragmentmodell {#changes-to-content-fragment-model}

Eine von GraphQL beibehaltene Abfrage kann fehlschlagen, wenn sie auf veralteten GraphQL-Typen basiert. Dies ist häufig auf eine Änderung der zugrunde liegenden Inhaltsfragmentmodelle zurückzuführen.

Dies kann aus verschiedenen Gründen geschehen. Beispiel: wenn ein Inhaltsmodellautor:

* entfernt oder benennt ein Feld um
* aktualisiert die für einen Fragmentverweis definierten zulässigen Modelle
* Veröffentlichung eines Modells aufheben, auf das andere Modelle verweisen
* sonstige Maßnahmen und Gründe

Gehen Sie dazu wie folgt vor:

* Die beibehaltene Abfrage, die fehlschlägt, sollte aktualisiert werden, um die Änderung am Inhaltsfragmentmodell zu berücksichtigen.
* oder die Änderung des Modells, durch das das Problem verursacht wurde, zurückgesetzt werden sollte

## GraphQL-Endpunkt nicht konfiguriert {#graphql-endpoint-not-configured}

Wenn persistente Abfragen die `400` oder `500` Fehler-Code zusammen mit den Informationen `No suitable endpoint found`bedeutet dies, dass in der AEM Umgebung kein GraphQL-Endpunkt konfiguriert ist.

Um dies zu korrigieren, führen Sie die Schritte zum Aktivieren und Veröffentlichen Ihres Endpunkts aus [Verwalten von GraphQL-Endpunkten in AEM](/help/headless/graphql-api/graphql-endpoint.md).

## Fehlender Pfad in der von GraphQL gespeicherten Abfrage-URL {#missing-path-query-url}

Wenn persistente Abfragen die `400` oder `500` Fehlercode mit den Informationen `Suffix: '/' does not contain a path`, wird das GraphQL-Servlet ohne Pfadsuffix aufgerufen.

Das Muster sollte `/graphql/execute.json/thePath`.

## Blockierung aufgrund IP-Zulassungsliste {#blocked-due-to-ip-allow-list}

In diesem Fall gibt die Abfrage die `405` Fehlercode.

Dies ist nichts Besonderes für GraphQL. Siehe KB-Artikel [405 Fehler nicht zulässig](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-20824.html).

## Von Dispatcher blockiert {#blocked-dispatcher}

Wenn der GraphQL-Endpunkt die `404` Fehler beim Veröffentlichen für `POST` -Anfragen bedeutet, dass die GraphQL-Abfragen auf Dispatcher-Ebene blockiert werden und der -Endpunkt manuell aktiviert werden muss.

Dies sollte nicht standardmäßig der Fall sein, aber eine benutzerdefinierte Dispatcher-Konfiguration kann dieses Problem verursachen. Weitere Informationen finden Sie unter [Dispatcher - Endpunktkonfiguration mit AEM Headless](/help/headless/deployment/dispatcher.md).
