---
title: Fehlerbehebung bei persistierten GraphQL-Abfragen
description: Erfahren Sie, wie Sie Probleme bei persistierten GraphQL-Abfragen in Adobe Experience Manager as a Cloud Service beheben können.
feature: Headless, Content Fragments,GraphQL API
exl-id: 71bd1f68-ca96-4c78-a936-abed250ecec1
role: Admin, Developer
source-git-commit: bdf3e0896eee1b3aa6edfc481011f50407835014
workflow-type: tm+mt
source-wordcount: '363'
ht-degree: 61%

---

# Fehlerbehebung bei persistierten GraphQL-Abfragen {#troubleshoot-persisted-graphql-queries}

Das [Aktionszentrum](/help/operations/actions-center.md) enthält den Warnhinweis **Fehler bei persistierter GraphQL-Abfrage**. Dies bedeutet, dass Sie immer dann informiert werden, wenn eine der persistierten GraphQL-Abfragen einen Fehler ausgibt.

Um Ihnen bei der Fehlerbehebung und Lösung solcher Probleme zu helfen, wird auf dieser Seite der Abschnitt *am häufigsten* Ursachen von Fehlern und Schritte zu deren Behebung.

## Änderungen am Inhaltsfragmentmodell {#changes-to-content-fragment-model}

Eine von GraphQL beibehaltene Abfrage kann fehlschlagen, wenn sie auf veralteten GraphQL-Typen basiert. Dies ist häufig auf eine Änderung der zugrunde liegenden Inhaltsfragmentmodelle zurückzuführen.

Solche Fehler können aus verschiedenen Gründen auftreten. Beispiele sind (die Liste ist nicht vollständig), wenn der Autor eines Inhaltsfragmentmodells:

* ein Feld entfernt oder umbenennt
* aktualisiert die **Modelltyp** definiert die für den Fragmentverweis zulässigen Modelle
* Veröffentlichung eines Modells rückgängig machen, auf das andere Modelle verweisen

Um solche Fehler zu beheben, sollten Sie entweder:

* Aktualisieren Sie die beibehaltene Abfrage, die die am Inhaltsfragmentmodell vorgenommenen Änderungen nicht berücksichtigt
* die Änderung des Modells zurücksetzen, durch das das Problem verursacht wurde

## GraphQL-Endpunkt nicht konfiguriert {#graphql-endpoint-not-configured}

Wenn persistierte Abfragen den Fehler-Code `404` zusammen mit der Information `No suitable endpoint found` zurückgeben, bedeutet dies, dass in der AEM-Umgebung kein GraphQL-Endpunkt konfiguriert ist.

Um dies zu korrigieren, führen Sie die Schritte zum Aktivieren und Veröffentlichen Ihres Endpunkts gemäß [Verwalten von GraphQL-Endpunkten in AEM](/help/headless/graphql-api/graphql-endpoint.md) aus.

## Fehlender Pfad in der von GraphQL persistierten Abfrage-URL {#missing-path-query-url}

Wenn persistierte Abfragen den Fehler-Code `400` mit der Information `Suffix: '/' does not contain a path` zurückgeben, wird das GraphQL-Servlet ohne Pfadsuffix aufgerufen.

Das Muster sollte `/graphql/execute.json/thePath` sein.

## Blockierung aufgrund der IP-Zulassungsliste {#blocked-due-to-ip-allow-list}

In diesem Fall gibt die Abfrage den Fehler-Code `405` zurück.

Ein solcher Fehler ist nicht speziell für GraphQL. Siehe KB-Artikel [405-Fehler Nicht zulässig](https://experienceleague.adobe.com/en/docs/experience-cloud-kcs/kbarticles/ka-20824).

## Von Dispatcher blockiert {#blocked-dispatcher}

Wenn der GraphQL-Endpunkt beim Veröffentlichen für `POST`-Anfragen den Fehler `404` zurückgibt, bedeutet dies, dass die GraphQL-Abfragen auf Dispatcher-Ebene blockiert werden und der Endpunkt manuell aktiviert werden muss.

Dies sollte standardmäßig nicht der Fall sein, aber eine benutzerdefinierte Dispatcher-Konfiguration kann dieses Problem verursachen. Weitere Informationen finden Sie unter [Dispatcher – Endpunktkonfiguration mit AEM Headless](/help/headless/deployment/dispatcher.md).
