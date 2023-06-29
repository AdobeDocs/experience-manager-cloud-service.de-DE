---
title: Zusätzliche Veröffentlichungsregionen
description: Erfahren Sie, wie AEM as a Cloud Service zusätzliche Veröffentlichungsbereiche unterstützt, um die Verfügbarkeit zu erhöhen und die Latenz zu reduzieren.
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '542'
ht-degree: 1%

---


# Zusätzliche Veröffentlichungsregionen {#additional-publish-regions}

Zusätzliche Veröffentlichungsbereiche können für mit AEM Sites eingerichtete Programme lizenziert und aktiviert werden. Wenn dies konfiguriert ist, wird der Traffic in Staging- und Produktionsumgebungen an mehrere Veröffentlichungsfarmen weitergeleitet, was die folgenden Vorteile hat:

* Geringere Latenz - Anforderungen, die vom CDN zu den AEM Veröffentlichungsinstanzen geleitet werden, werden an den nächstgelegenen Veröffentlichungsbereich geleitet. Dies ist von Vorteil für Websites und Anwendungen, die von Benutzern in mehreren geografischen Regionen besucht werden.
* Höhere Verfügbarkeit - Wenn eine Region nicht verfügbar ist, leitet das CDN Traffic an die anderen verfügbaren Regionen weiter.

Organisationen können bis zu drei weitere Veröffentlichungsregionen lizenzieren.

>[!NOTE]
>
>Diese Funktion ist derzeit nur für AEM Sites verfügbar. Sie kann auch nicht auf Sandbox-Programme angewendet werden. Beachten Sie außerdem, dass für zusätzliche Veröffentlichungsregionen-Funktionen Ihr Programm aktualisiert werden muss, damit AEM Version 12142 oder höher veröffentlicht wird.

## Anwendungsfälle {#use-cases}

Im Folgenden finden Sie einige Anwendungsfälle, in denen Unternehmen von der Lizenzierung zusätzlicher Veröffentlichungsregionen profitieren können.

1. Für Unternehmen, die erheblichen oder geschäftskritischen Traffic von Benutzern erhalten, die weit von der primären Region entfernt sind, können zusätzliche Veröffentlichungsregionen die Latenz dieser Besucher verringern.
1. Für Organisationen, die unter erheblichen finanziellen oder Reputationsschäden leiden können, wenn eine Site nicht verfügbar ist, kann dies durch die Verwendung zusätzlicher Veröffentlichungsregionen abgefedert werden, um die AEM Veröffentlichungsstufe widerstandsfähiger gegen regionale Fehler zu machen.
1. Für Organisationen, deren Inhaltsautoren sich an einem geografischen Standort befinden, der von der Mehrheit der Besucher der Veröffentlichungsstufe entfernt ist, kann die primäre Region in der Nähe des Standorts der Inhaltsautoren ausgewählt werden, während zusätzliche Veröffentlichungsregionen in der Nähe des Traffics auf der Veröffentlichungsseite konfiguriert werden können, wobei beide Zielgruppen von einem optimierten Erlebnis profitieren.

## Aktivieren und Konfigurieren {#enabling-and-configuring}

Nach der Lizenzierung eines zusätzlichen Veröffentlichungsbereichs werden die Regionen mithilfe von Cloud Manager konfiguriert. Siehe [Dokumentation zu Cloud Manager](/help/implementing/cloud-manager/manage-environments.md#multiple-regions) für detaillierte Anweisungen.

Zusätzliche Veröffentlichungsbereiche werden auf Staging- und Produktionsumgebungen angewendet, nicht jedoch auf RDE- oder Entwicklungsumgebungen.

## Überlegungen zur erweiterten Vernetzung {#advanced-networking-considerations}

Wenn eine zusätzliche Veröffentlichungsregion in einem Programm aktiviert ist, für das bereits ein erweitertes Netzwerk konfiguriert wurde, wird der Traffic in der zusätzlichen Veröffentlichungsregion, der den erweiterten Netzwerkregeln entspricht, standardmäßig durch die primäre Region geleitet. Um von einer erhöhten Verfügbarkeit zu profitieren, wird empfohlen, eine erweiterte Vernetzung der zusätzlichen Regionen zu ermöglichen.

Siehe [Erweiterte Netzwerkkonfiguration für weitere Veröffentlichungsregionen](/help/security/configuring-advanced-networking.md#advanced-networking-configuration-for-additional-publish-regions) Einzelheiten dazu, wie Sie erweiterte Netzwerkkonfigurationen zu zusätzlichen Regionen hinzufügen können, ohne dass dadurch die Konnektivität beeinträchtigt wird, finden Sie in der Dokumentation zur erweiterten Vernetzung .

## Einschränkungen {#limitations}

Beachten Sie die folgenden Einschränkungen bei der Verwendung zusätzlicher Veröffentlichungsregionen.

* Zusätzliche Veröffentlichungsbereiche können nur zu AEM Sites hinzugefügt werden. Zusätzliche Veröffentlichungsbereiche erstrecken sich nicht auf andere AEM oder zugehörige Funktionen, die im selben Programm bereitgestellt werden (z. B. AEM Forms oder Adobe Learning Manager).
* Zusätzliche Regionen können nur hinzugefügt werden, wenn verknüpfte Berechtigungen im Mandanten verfügbar und nicht verwendet sind.
* Es können maximal drei weitere Veröffentlichungsbereiche zu jeder einzelnen Umgebung hinzugefügt werden.
* Zusätzliche Regionen sind nur für Produktionsprogramme verfügbar. Die Funktion ist nicht in Sandbox-Programmen verfügbar.
* Zusätzliche Veröffentlichungsbereiche werden nur auf Staging- und Produktionsumgebungen angewendet, nicht auf RDE- oder Entwicklungsumgebungen.
* Für weitere Veröffentlichungsregionen muss Ihr Programm aktualisiert werden, damit AEM Version 12142 oder höher veröffentlicht werden kann.
