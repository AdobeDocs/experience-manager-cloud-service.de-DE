---
title: Journey zur AEM SchnellSite-Erstellung
description: Beginnen Sie hier mit einer geführten Journey durch das benutzerfreundliche AEM Schnellerstellungs-Tool, um die Front-End-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site ohne AEM Backend-Wissen schnell anzupassen.
source-git-commit: efeb97d4bd7e7c11ec2c0ba1244a32b8b9affdab
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 2%

---


# Journey zur AEM SchnellSite-Erstellung {#quick-site-creation-journey}

Beginnen Sie hier mit einer geführten Journey durch das benutzerfreundliche AEM Schnellerstellungs-Tool, um die Front-End-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site ohne AEM Backend-Wissen schnell anzupassen.

>[!CAUTION]
>
>Das Tool für die schnelle Site-Erstellung ist derzeit eine technische Vorschau. Sie wird zu Test- und Evaluierungszwecken bereitgestellt und ist nicht zur Verwendung in der Produktion bestimmt, es sei denn, sie wurde mit der Adobe Support vereinbart.

## Einführung {#introduction}

AEM Sites ist ein leistungsstarkes Tool-Set zum Erstellen und Verwalten digitaler Erlebnisse. Autoren von Inhalten können mit dem Sites-Editor einfach digitale Erlebnisse erstellen und die Inhalte mithilfe der Sites-Konsole organisieren. Gleichzeitig können sie die Inhalte live sehen, wie sie von AEM an Ihre Zielgruppen kanalübergreifend bereitgestellt werden.

Mit dem Tool AEM schnelle Site-Erstellung können Nicht-Entwickler mithilfe von Site-Vorlagen schnell eine neue Site von Grund auf neu erstellen. Nach der Erstellung ermöglicht das Tool für die schnelle Site-Erstellung auch eine schnelle Anpassung des Designs und des Stils der AEM Site (JavaScript, CSS und statische Ressourcen). Dadurch kann der Frontend-Entwickler, der keine Kenntnisse über AEM benötigt, getrennt und parallel zu den Erstellern von Inhalten arbeiten. Der AEM Administrator lädt das Site-Design einfach herunter und stellt es dem Frontend-Entwickler bereit, der es mithilfe seiner bevorzugten Tools anpasst, und übergibt dann die Änderungen an das AEM Code-Repository, das dann bereitgestellt wird.

Indem Sie Entwicklerwissen für die Site-Erstellung eliminieren, AEM Wissensanforderungen für die Front-End-Entwicklung eliminieren und die Designentwicklung parallel zur Inhaltserstellung fortsetzen können, beschleunigt das Tool AEM SchnellSite-Erstellung die Time-to-Value Ihrer Site erheblich und erhöht die Flexibilität Ihrer Site-Anpassung und -Bereitstellung.

## Journey AEM Dokumentation {#documentation-journeys}

[Eine Journey der Dokumentation](/help/journey-documentation/home.md) verbindet viele verschiedene und vielleicht komplizierte Themen und Funktionen, indem eine Erzählung bereitgestellt wird, die dem Leser hilft, der neu zu AEM sein kann, ein Geschäftsproblem von Anfang bis Ende zu verstehen und zu lösen, während er von Anfang bis Ende nur ein minimales vorheriges Thema oder AEM Wissen angeht.

Die Journey der Dokumentation basieren auf Best-Practice-Prinzipien, die durch aktuelle Forschungsarbeiten der Adobe, bewährte Implementierungserfahrungen von Adobe-Beratern und Rückmeldungen von Kundenprojekten informiert werden.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Sites-Geschäftsfälle mit AEM zu lösen, sollten AEM Sites-Journey beginnen.

## Zielgruppe {#audience}

In dieser Journey werden die Anforderungen, Schritte und Ansätze zur Anpassung von AEM Sites-Designs beschrieben. Seine primäre Zielgruppe ist der Frontend-Entwickler, der keine Kenntnisse über AEM benötigt. Zur Veranschaulichung des gesamten Prozesses umfasst die Journey jedoch Administratoren, von denen angenommen wird, dass sie über grundlegende Kenntnisse in AEM Sites und Cloud Manager verfügen. In der Praxis können mehrere Benutzer mehrere Rollen bedienen. Diese Journey unterstützt Perspektiven sowohl von Administratoren als auch von Frontend-Entwicklern.

| Rolle | Beschreibung | Rolle beim Journey |
|---|---|---|
| Frontend-Entwickler | Passt das Site-Design an | Nimmt das vom AEM-Administrator bereitgestellte Design und passt es an, sodass es auf der AEM-Site bereitgestellt werden kann. |
| Inhaltsautor | Erstellt und verwaltet Inhalte, die als Sites bereitgestellt werden | Inhaltsautoren erstellen Inhalte auf AEM, die mit dem vom Frontend-Entwickler angepassten Design gerendert werden. |
| AEM-Administrator | Erstellt eine neue AEM Site | Der AEM Administrator erstellt eine neue Site auf der Grundlage einer Vorlage und stellt dem Frontend-Entwickler dann ein Design zur Anpassung bereit. |
| Cloud Manager-Administrator | Erstellt Pipelines und gewährt Zugriff | Der Cloud Manager-Administrator erstellt die Frontend-Pipeline und gewährt dem Frontend-Entwickler Zugriff auf die Möglichkeit, Anpassungen an das AEM Git-Repository zu übertragen. |

## Die Journey zur AEM schnellen Site-Erstellung {#the-journey}

Im Rahmen dieser Tour werden Sie sich mit zahlreichen Themen befassen. Die folgenden Artikel geben Ihnen grundlegende Kenntnisse zum Erstellen und Anpassen AEM Sites mithilfe des Tools für die schnelle Site-Erstellung und verweisen auf eine detaillierte technische Dokumentation.

|#|Article|Description|Responsible role |
|---|---|---|---|
|0|AEM Journey zur schnellen Site-Erstellung|Dieses Dokument|AEM- und Cloud Manager-Administratoren|
|1|[Grundlegendes zu Cloud Manager und dem Arbeitsablauf für die schnelle Site-Erstellung](cloud-manager.md)|Erfahren Sie mehr über Cloud Manager und wie dieser den neuen Prozess zur schnellen Site-Erstellung verbindet.|AEM Administrator|
|2|[Erstellen einer Site aus einer Vorlage](create-site.md)|Erfahren Sie, wie Sie mithilfe einer Site-Vorlage schnell eine neue AEM erstellen.|AEM Administrator|
|3|[Einrichten der Pipeline](pipeline-setup.md)|Erstellen Sie eine Front-End-Pipeline, um die Anpassung des Designs Ihrer Site zu verwalten.|Cloud Manager-Administrator|
|4|[Gewähren des Zugriffs für den Frontend-Entwickler](grant-access.md)|Integrieren Sie die Frontend-Entwickler in Cloud Manager, damit sie Zugriff auf Ihr Git-Repository und Ihre AEM-Pipeline haben.|Cloud Manager-Administrator|
|5|[Git-Repository-Zugriffsinformationen abrufen](retrieve-access.md)|Erfahren Sie, wie der Frontend-Entwickler Cloud Manager verwendet, um auf Git-Repository-Informationen zuzugreifen.|Frontend-Entwickler|
|6|[Anpassen des Site-Designs](customize-theme.md)|Erfahren Sie, wie ein Site-Design erstellt wird, wie es angepasst wird und wie es mithilfe von Live-AEM-Inhalten getestet wird.|Frontend-Entwickler|
|7|[Bereitstellen Ihres benutzerdefinierten Designs](deploy-theme.md)|Erfahren Sie, wie Sie das Site-Design mithilfe der Pipeline bereitstellen.|Frontend-Entwickler|

## Wie geht es weiter {#what-is-next}

Sie können jetzt mit der Adobe Quick Site Creation Journey beginnen.

* Wenn Sie ein AEM- oder Cloud Manager-Administrator sind oder sowohl Frontend-Entwickler- als auch -Administratorrollen verwenden oder einfach den End-to-End-Prozess in AEM verstehen möchten, beginnen Sie bitte am Anfang des Journey mit [Grundlegendes zu Cloud Manager](cloud-manager.md) wie unten beschrieben.
* Wenn Sie nur für die Front-End-Entwicklung verantwortlich sind und mit den AEM- und Cloud Manager-Administratoren interagieren, können Sie direkt zu [Git-Repository-Zugriffsinformationen abrufen](retrieve-access.md) , um Zugriff auf das AEM Git-Repository zu erhalten und mit der Anpassung zu beginnen.
* Wenn Sie bereits wissen, dass AEM Sites und Cloud Manager zusammenarbeiten und direkt mit der Konfiguration beginnen möchten, können Sie [direkt zum Erstellen einer neuen Site aus einer Vorlage springen.](create-site.md)

## Zusätzliche Ressourcen {#additional-resources}

Sehen Sie sich diese zusätzlichen Ressourcen an, um mehr darüber zu erfahren, wie AEM leistungsstarken Funktionen zusammenarbeiten.

* [AEM as a Cloud Service technische Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) - Wenn Sie bereits über ein festes Verständnis der AEM verfügen, können Sie die ausführlichen technischen Dokumente direkt konsultieren.
* [Dokumentation zur Site-Verwaltung](/help/sites-cloud/administering/site-creation/create-site.md) - Weitere Informationen zu den Funktionen des Tools für die schnelle Site-Erstellung finden Sie in den technischen Dokumenten zur Site-Erstellung .
