---
title: Zusätzliche Veröffentlichungsregionen
description: Erfahren Sie, wie AEM as a Cloud Service zusätzliche Veröffentlichungsregionen für höhere Verfügbarkeit und geringere Latenz unterstützt.
exl-id: b9ac3c6a-eb8b-461d-8f1d-a0356046a3f9
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '640'
ht-degree: 80%

---

# Zusätzliche Veröffentlichungsregionen {#additional-publish-regions}

Zusätzliche Veröffentlichungsregionen können für mit AEM Sites eingerichtete Programme lizenziert und aktiviert werden. Wenn dies konfiguriert ist, wird der Traffic in Staging- und Produktionsumgebungen an mehrere Veröffentlichungsfarmen weitergeleitet, was die folgenden Vorteile hat:

* Geringere Latenz – Anforderungen, die vom CDN zu den AEM-Veröffentlichungsinstanzen weitergeleitet werden, werden an die nächstgelegene Veröffentlichungsregion übermittelt. Dies ist von Vorteil für Websites und Anwendungen, die von Benutzenden in mehreren geografischen Regionen besucht werden.
* Höhere Verfügbarkeit – Wenn eine Region nicht verfügbar ist, leitet das CDN Traffic an die andere(n) verfügbare(n) Region(en) weiter.

Organisationen können bis zu drei zusätzliche Veröffentlichungsregionen lizenzieren.

>[!NOTE]
>
>Diese Funktion ist derzeit nur für AEM Sites verfügbar. Sie kann auch nicht auf Sandbox-Programme angewendet werden. Beachten Sie außerdem, dass für die Funktion zum Veröffentlichen in zusätzlichen Regionen Ihr Programm auf die AEM-Version 12142 oder höher aktualisiert werden muss.

## Anwendungsfälle {#use-cases}

Im Folgenden finden Sie einige Anwendungsfälle, in denen Unternehmen von der Lizenzierung zusätzlicher Veröffentlichungsregionen profitieren können.

1. Für Unternehmen, die erheblichen oder geschäftskritischen Traffic von Benutzenden erhalten, die weit von der primären Region entfernt sind, können zusätzliche Veröffentlichungsregionen die Latenz dieser Besucherinnen und Besucher verringern.
1. Für Organisationen, die unter erheblichen finanziellen oder Reputationsschäden leiden können, wenn eine Site nicht verfügbar ist, kann dies durch die Verwendung zusätzlicher Veröffentlichungsregionen abgefedert werden, um die AEM-Veröffentlichungsebene widerstandsfähiger gegen regionale Ausfälle zu machen.
1. Für Organisationen, deren Autorenschaft sich an einem geografischen Standort befindet, der von der Mehrheit der Besucherinnen und Besucher der Veröffentlichungsebene weit entfernt ist, kann die primäre Region in der Nähe des Standorts der Autorenschaft ausgewählt werden, während zusätzliche Veröffentlichungsregionen in der Nähe des Traffics auf der Veröffentlichungsseite konfiguriert werden können, wodurch beide Zielgruppen von einem optimierten Erlebnis profitieren.

## Aktivieren und Konfigurieren {#enabling-and-configuring}

Nach der Lizenzierung einer zusätzlichen Veröffentlichungsregion werden die Regionen mithilfe von Cloud Manager konfiguriert. Detaillierte Anweisungen finden Sie in der [Dokumentation zu Cloud Manager](/help/implementing/cloud-manager/manage-environments.md#multiple-regions).

Zusätzliche Veröffentlichungsregionen werden auf Staging- und Produktionsumgebungen angewendet, nicht jedoch auf RDE- oder Entwicklungsumgebungen.

Sollte eine Region nicht verfügbar sein, müssen Kunden das Routing von Traffic zu verfügbaren Regionen nicht verwalten, da es vom Adobe CDN verwaltet wird.

Wie im Abschnitt Hinweise zu erweiterten Netzwerken unten beschrieben, wird empfohlen, dass Kunden, die erweiterte Netzwerke verwenden, diese für jede zusätzliche Veröffentlichungsregion konfigurieren, damit die Verfügbarkeit beibehalten wird, wenn eine Region nicht mehr verfügbar ist.


## Überlegungen zu erweiterten Netzwerken {#advanced-networking-considerations}

Wenn eine zusätzliche Veröffentlichungsregion in einem Programm aktiviert wird, für das bereits ein erweitertes Netzwerk konfiguriert ist, wird der Traffic in der zusätzlichen Veröffentlichungsregion, der den erweiterten Netzwerkregeln entspricht, standardmäßig durch die primäre Region geleitet. Um die Vorteile der erhöhten Verfügbarkeit zu nutzen, empfiehlt es sich, ein erweitertes Netzwerk auf den zusätzlichen Regionen zu aktivieren.

Weitere Informationen finden Sie im Abschnitt [Erweiterte Netzwerkkonfiguration für zusätzliche Veröffentlichungsregionen](/help/security/configuring-advanced-networking.md#advanced-networking-configuration-for-additional-publish-regions) in der Dokumentation zu erweiterten Netzwerken, einschließlich einer Anleitung, wie Sie erweiterte Netzwerkkonfigurationen zu zusätzlichen Regionen hinzufügen können, ohne dass es zu einem Verlust der Konnektivität kommt.

## Protokollierung {#logging}

Wenn zusätzliche Veröffentlichungsbereiche aktiviert sind, werden über Cloud Manager separate Protokolle für jede Region bereitgestellt. Weitere Informationen finden Sie unter [Zugreifen auf und Verwalten von Protokollen](/help/implementing/cloud-manager/manage-logs.md) und [Protokolle für weitere Veröffentlichungsregionen](/help/implementing/developing/introduction/logging.md#logs-for-additional-publish-regions).

## Einschränkungen {#limitations}

Beachten Sie die folgenden Einschränkungen bei der Verwendung zusätzlicher Veröffentlichungsregionen.

* Zusätzliche Veröffentlichungsregionen können nur zu AEM Sites hinzugefügt werden. Zusätzliche Veröffentlichungsbereiche erstrecken sich nicht auf andere AEM oder zugehörige Funktionen, die im selben Programm bereitgestellt werden (z. B. AEM Forms oder Adobe Learning Manager).
* Zusätzliche Regionen können nur hinzugefügt werden, wenn verknüpfte Berechtigungen im Mandanten verfügbar und nicht verwendet sind.
* Es können maximal drei zusätzliche Veröffentlichungsregionen zu jeder einzelnen Umgebung hinzugefügt werden.
* Zusätzliche Regionen sind nur für Produktionsprogramme verfügbar. Die Funktion ist nicht in Sandbox-Programmen verfügbar.
* Zusätzliche Veröffentlichungsregionen werden nur auf Staging- und Produktionsumgebungen angewendet, nicht auf RDE- oder Entwicklungsumgebungen.
* Für zusätzliche Veröffentlichungsregionen muss Ihr Programm auf die AEM-Version 12142 oder höher aktualisiert werden.
