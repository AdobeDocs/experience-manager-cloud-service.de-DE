---
title: Fehlerbehebung bei persistierten GraphQL-Abfragen
description: Erfahren Sie, wie Sie Probleme bei persistierten GraphQL-Abfragen in Adobe Experience Manager as a Cloud Service beheben können.
feature: Content Fragments,GraphQL API
exl-id: 71bd1f68-ca96-4c78-a936-abed250ecec1
source-git-commit: 05548d56d791584781606b02839c5602b4469f7b
workflow-type: ht
source-wordcount: '353'
ht-degree: 100%

---

# Fehlerbehebung bei persistierten GraphQL-Abfragen {#troubleshoot-persisted-graphql-queries}

Das [Aktionszentrum](/help/operations/actions-center.md) enthält den Warnhinweis **Fehler bei persistierter GraphQL-Abfrage**. Dies bedeutet, dass Sie immer dann informiert werden, wenn eine der persistierten GraphQL-Abfragen einen Fehler ausgibt.

Um Ihnen bei der Fehlerbehebung und Lösung solcher Probleme zu helfen, erläutern wir die *häufigsten* Ursachen von Fehlern und die Schritte zu deren Behebung.

## Änderungen am Inhaltsfragmentmodell {#changes-to-content-fragment-model}

Eine persistierte GraphQL-Abfrage kann fehlschlagen, wenn sie auf veralteten GraphQL-Typen basiert. Dies ist häufig auf eine Änderung der zugrunde liegenden Inhaltsfragmentmodelle zurückzuführen.

Dies kann aus verschiedenen Gründen geschehen. Zum Beispiel, wenn ein Inhaltsmodellautor oder eine -autorin:

* ein Feld entfernt oder umbenennt
* die für einen Fragmentverweis definierten zulässigen Modelle aktualisiert
* die Veröffentlichung eines Modells aufhebt, auf das andere Modelle verweisen
* sonstige Aktionen und Gründe

Gehen Sie zur Fehlerbehebung wie folgt vor:

* Die persistierte Abfrage, die fehlschlägt, sollte aktualisiert werden, um die Änderung am Inhaltsfragmentmodell zu berücksichtigen,
* oder die Änderung des Modells, durch die das Problem verursacht wurde, sollte zurückgesetzt werden

## GraphQL-Endpunkt nicht konfiguriert {#graphql-endpoint-not-configured}

Wenn persistierte Abfragen den Fehler-Code `400` oder `500` zusammen mit der Information `No suitable endpoint found` zurückgeben, bedeutet dies, dass in der AEM-Umgebung kein GraphQL-Endpunkt konfiguriert ist.

Um dies zu korrigieren, führen Sie die Schritte zum Aktivieren und Veröffentlichen Ihres Endpunkts gemäß [Verwalten von GraphQL-Endpunkten in AEM](/help/headless/graphql-api/graphql-endpoint.md) aus.

## Fehlender Pfad in der von GraphQL persistierten Abfrage-URL {#missing-path-query-url}

Wenn persistierte Abfragen den Fehler-Code `400` oder `500` mit der Information `Suffix: '/' does not contain a path` zurückgeben, wird das GraphQL-Servlet ohne Pfadsuffix aufgerufen.

Das Muster sollte `/graphql/execute.json/thePath` sein.

## Blockierung aufgrund der IP-Zulassungsliste {#blocked-due-to-ip-allow-list}

In diesem Fall gibt die Abfrage den Fehler-Code `405` zurück.

Dies gilt nicht spezifisch für GraphQL. Siehe KB-Artikel [405-Fehler Nicht zulässig](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-20824.html?lang=de).

## Von Dispatcher blockiert {#blocked-dispatcher}

Wenn der GraphQL-Endpunkt beim Veröffentlichen für `POST`-Anfragen den Fehler `404` zurückgibt, bedeutet dies, dass die GraphQL-Abfragen auf Dispatcher-Ebene blockiert werden und der Endpunkt manuell aktiviert werden muss.

Dies sollte standardmäßig nicht der Fall sein, aber eine benutzerdefinierte Dispatcher-Konfiguration kann dieses Problem verursachen. Weitere Informationen finden Sie unter [Dispatcher – Endpunktkonfiguration mit AEM Headless](/help/headless/deployment/dispatcher.md).
