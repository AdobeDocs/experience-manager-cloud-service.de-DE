---
title: Tour zu AEM Quick Site Creation
description: Beginnen Sie hier mit einer geführten Tour durch das benutzerfreundliche Tool AEM Quick Site Creation, um die Frontend-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site schnell ohne AEM-Backend-Kenntnisse anzupassen.
exl-id: b8218232-0298-4b16-9dab-fa59be592a24
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 100%

---

# Tour zu AEM Quick Site Creation {#quick-site-creation-journey}

Beginnen Sie hier mit einer geführten Tour durch das benutzerfreundliche Tool AEM Quick Site Creation, um die Frontend-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site schnell ohne AEM-Backend-Kenntnisse anzupassen.

## Einführung {#introduction}

AEM Sites ist ein leistungsstarkes Toolset zum Erstellen und Verwalten digitaler Erlebnisse. Inhaltsautoren können mit dem Sites-Editor einfach digitale Erlebnisse erstellen und die Inhalte mithilfe der Sites-Konsole organisieren. Gleichzeitig können sie die Inhalte live sehen, so wie sie kanalübergreifend von AEM an Zielgruppen bereitgestellt werden.

Mit dem Tool AEM Quick Site Creation können Nicht-Entwickler mithilfe von Site-Vorlagen schnell eine neue Site von Grund auf erstellen. Nach der Erstellung ermöglicht das Tool Quick Site Creation auch eine schnelle Anpassung des Designs und des Stils der AEM-Site (JavaScript, CSS und statische Ressourcen). Dadurch kann der Frontend-Entwickler, der keine Kenntnisse über AEM benötigt, getrennt und parallel zu den Erstellern von Inhalten arbeiten. Der AEM-Administrator lädt ganz einfach das Site-Design herunter und stellt es dem Frontend-Entwickler bereit, der es mithilfe seiner bevorzugten Tools anpasst und dann die Änderungen an das AEM Code-Repository übergibt, das dann bereitgestellt wird.

Indem es Entwicklerwissen für die Site-Erstellung unnötig macht, keine Anforderungen an spezielles AEM-Wissens für die Frontend-Entwicklung stellt und ermöglicht, dass die Design-Entwicklung parallel zur Inhaltserstellung fortgesetzt wird, beschleunigt das Tool AEM Quick Site Creation die Time-to-Value Ihrer Site erheblich und erhöht die Flexibilität beim Anpassen und Implementieren der Site.

## Videoüberblick {#video-overview}

Einen kurzen Überblick über diese Funktion in Aktion [sehen Sie in dieser 5-minütigen Einführung](https://www.youtube.com/watch?v=NQeQ1jZ7ZBw).

Diese Dokumentations-Tour führt Sie schrittweise und detailliert durch alle Funktionen des Videos, sodass Sie den Workflow verstehen und den Prozess in Ihrer eigenen Umgebung reproduzieren können.

## AEM-Dokumentations-Touren {#documentation-journeys}

[Eine Dokumentations-Tour](/help/journey-documentation/documentation-journeys.md) verbindet viele verschiedene und möglicherweise komplizierte Themen und Funktionen durch eine Erzählung, die dem nicht mit AEM vertrauten Leser hilft, ein geschäftliches Problem von Anfang bis Ende zu verstehen und zu lösen, wobei nur minimale Vorkenntnisse zum Thema oder zu AEM vorausgesetzt werden.

Dokumentations-Touren werden auf der Grundlage von Best-Practice-Prinzipien entwickelt, die auf Informationen aus den neuesten Forschungsergebnissen von Adobe, bewährten Implementierungserfahrungen der Adobe-Berater und dem Feedback aus Kundenprojekten basieren.

Wenn Sie wissen möchten, wie Adobe empfiehlt, Geschäftsfälle für Websites mit AEM zu lösen, sollten Sie mit den AEM Sites-Touren beginnen.

## Zielgruppe {#audience}

In dieser Tour werden die Anforderungen, Schritte und Ansätze zur Anpassung von AEM Sites-Designs beschrieben. Ihre primäre Zielgruppe ist der Frontend-Entwickler, der keine Kenntnisse über AEM benötigt. Zur Veranschaulichung des gesamten Prozesses bezieht die Tour jedoch auch Administratoren ein, von denen angenommen wird, dass sie über grundlegende Kenntnisse in AEM Sites und Cloud Manager verfügen. In der Praxis können mehrere Benutzer mehrere Rollen einnehmen. Diese Tour unterstützt Perspektiven sowohl von Administratoren als auch von Frontend-Entwicklern.

| Rolle | Beschreibung | Rolle in der Tour |
|---|---|---|
| Frontend-Entwickler | Passt das Design von Sites an | Nimmt das vom AEM-Administrator bereitgestellte Design und passt es an, sodass es auf der AEM-Site bereitgestellt werden kann. |
| Inhaltsautor | Erstellt und verwaltet Inhalte, die als Sites bereitgestellt werden | Inhaltsautoren erstellen Inhalte in AEM, die mit dem vom Frontend-Entwickler angepassten Design gerendert werden. |
| AEM-Administrator | Erstellt eine neue AEM-Site | Der AEM-Administrator erstellt auf der Grundlage einer Vorlage eine neue Site und stellt dem Frontend-Entwickler dann ein Design zur Anpassung zur Verfügung. |
| Cloud Manager-Administrator | Erstellt Pipelines und gewährt Zugriffsrechte | Der Cloud Manager-Administrator erstellt die Frontend-Pipeline und gewährt dem Frontend-Entwickler Zugriffsrechte, damit er Anpassungen am AEM-Git-Repository vornehmen kann. |

## Die Tour zu AEM Quick Site Creation {#the-journey}

Im Rahmen dieser Tour werden Sie sich mit zahlreichen Themen befassen. Die folgenden Artikel vermitteln Ihnen grundlegende Kenntnisse zum Erstellen und Anpassen von AEM-Sites mithilfe des Tools Quick Site Creation. Außerdem verweisen sie auf eine detaillierte technische Dokumentation.

|#|Artikel|Beschreibung|Verantwortliche Rolle|
|---|---|---|--| |
|0|Tour zu AEM Quick Site Creation|Dieses Dokument|AEM- und Cloud Manager-Administratoren| |
|1|[Grundlegendes zu Cloud Manager und dem Workflow von Quick Site Creation](cloud-manager.md)|Erfahren Sie mehr über Cloud Manager und die Verbindung mit dem neuen Quick Site Creation-Prozess.|AEM-Administrator| |
|2||[Erstellen einer Site aus einer Vorlage](create-site.md)|Erfahren Sie, wie Sie mithilfe einer Site-Vorlage schnell eine neue AEM-Site erstellen.|AEM-Administrator| |
|3|[Einrichten der Pipeline](pipeline-setup.md)|Erstellen Sie eine Frontend-Pipeline, um die Anpassung des Designs Ihrer Site zu verwalten.|Cloud Manager-Administrator| |
|4|[Gewähren des Zugriffs für den Frontend-Entwickler](grant-access.md)|Integrieren Sie die Frontend-Entwickler in Cloud Manager, damit sie Zugriff auf das Git-Repository Ihrer AEM-Site und auf Ihre AEM-Pipeline haben.|Cloud Manager-Administrator| |
|5|[Git-Repository-Zugriffsinformationen abrufen](retrieve-access.md)|Erfahren Sie, wie der Frontend-Entwickler Cloud Manager verwendet, um auf Git-Repository-Informationen zuzugreifen.|Frontend-Entwickler| |
|6|[Anpassen des Site-Designs](customize-theme.md)|Erfahren Sie, wie ein Site-Design erstellt wird, wie es angepasst wird und wie es mithilfe von AEM-Live-Inhalten getestet wird.|Frontend-Entwickler| |
|7|[Bereitstellen eines benutzerdefinierten Designs](deploy-theme.md)|Erfahren Sie, wie Sie das Site-Design mithilfe der Pipeline bereitstellen.|Frontend-Entwickler|

## Wie geht es weiter {#what-is-next}

Jetzt sind Sie bereit, mit Ihrer Tour zu AEM Quick Site Creation zu beginnen.

* Wenn Sie ein AEM- oder Cloud Manager-Administrator sind oder sowohl Frontend-Entwickler- als auch -Administratorrollen verwenden oder einfach den durchgängigen Prozess in AEM verstehen möchten, beginnen Sie am Anfang der Tour mit [Grundlegendes zu Cloud Manager](cloud-manager.md), wie unten beschrieben.
* Wenn Sie nur für die Frontend-Entwicklung verantwortlich sind und mit den AEM- und Cloud Manager-Administratoren interagieren, können Sie direkt zu [Git-Repository-Zugriffsinformationen abrufen](retrieve-access.md) springen, um Zugriff auf das AEM-Git-Repository zu erhalten und mit der Anpassung zu beginnen.
* Wenn Sie bereits wissen, dass AEM Sites und Cloud Manager zusammenarbeiten, und direkt mit der Konfiguration beginnen möchten, können Sie [direkt zum Erstellen einer neuen Site aus einer Vorlage springen](create-site.md).

## Zusätzliche Ressourcen {#additional-resources}

In diesen zusätzlichen Ressourcen finden Sie weitere Informationen darüber, wie die leistungsstarken Funktionen von AEM zusammenarbeiten.

* [Technische Dokumentation zu AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=de) – Wenn Sie bereits über ein solides Verständnis von AEM verfügen, sehen Sie sich die ausführlichen technischen Dokumente an.
* [Dokumentation zur Verwaltung von Sites](/help/sites-cloud/administering/site-creation/create-site.md) – Weitere Informationen zu den Funktionen des Tools Quick Site Creation finden Sie in den technischen Dokumenten zur Site-Erstellung.
