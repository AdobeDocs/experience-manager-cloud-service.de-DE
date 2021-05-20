---
title: Planungsphase
description: Planungsphase
exl-id: 987cb929-7871-4fec-8ef5-4d2f5f2f2186
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 100%

---

# Planung {#planning-phase}

>[!CONTEXTUALHELP]
>id="aemcloud_cam_planning"
>title="Planen Ihrer Umstellung"
>abstract="Bevor Sie mit der Umstellung auf Cloud Service beginnen, sollten Sie sich mit AEM as a Cloud Service vertraut machen und die wichtigen Änderungen und Funktionen einsehen, die ersetzt oder eingestellt wurden."
>additional-url="https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/best-practices-analyzer/overview-best-practices-analyzer.html?lang=de" text="Best Practices Analyzer"

Bevor Sie mit der Umstellung auf Cloud Service beginnen, sollten Sie sich mit AEM as a Cloud Service vertraut machen und die wichtigen Änderungen und Funktionen einsehen, die ersetzt oder eingestellt wurden.

## Wesentliche Änderungen {#notable-changes}

AEM as a Cloud Service bietet viele neue Funktionen und Möglichkeiten zur Verwaltung Ihrer AEM-Projekte.

Es gibt jedoch eine Reihe von Unterschieden zwischen AEM On-Premise oder in Adobe Managed Services im Vergleich zu AEM as a Cloud Service.

Die wichtigen Unterschiede finden Sie unter [Wichtige Änderungen in AEM Cloud Service](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/release-notes/aem-cloud-changes.html).

## Veraltete Funktionen {#deprecated-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird.

Weitere Informationen zu Funktionen, die in Experience Manager as a Cloud Service als veraltet markiert wurden, finden Sie unter [Veraltete Funktionen](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/release-notes/deprecated-removed-features.html#deprecated-features).

## Grundlegendes zur Planungsphase {#introduction}

Die folgende Abbildung zeigt die wichtigsten Schritte der Planungsphase:

![image](/help/move-to-cloud-service/assets/planning-phaseimg1.png)

### Bewerten der Cloud Service-Bereitschaft {#access-cloud-readiness}

Der erste Schritt in der Planungsphase besteht darin, Ihre Bereitschaft für den Umstieg von Ihrer bestehenden AEM-Version auf Cloud Service zu bewerten und Bereiche zu ermitteln, die eine Umgestaltung erfordern, um mit AEM as a Cloud Service kompatibel zu sein.

Sie müssen eine umfassende Bewertung Ihres aktuellen AEM-Quell-Codes anhand der wichtigen Änderungen und veralteten Funktionen vornehmen, um den für die Umstellung erwarteten Aufwand zu bestimmen.

Sie können den Bewertungsschritt beschleunigen, indem Sie Best Practices Analyzer für Ihre aktuelle AEM-Version ausführen. Weitere Informationen finden Sie unter [Best Practices Analyzer](/help/move-to-cloud-service/best-practices-analyzer/overview-best-practices-analyzer.md).

>[!NOTE]
>Wenn Sie bereits Zugriff auf Cloud Manager und eine Cloud Service-Umgebung haben, wird empfohlen, Ihren aktuellen Code in einer Cloud Manager-Pipeline für die Code-Qualität auszuführen, um die erforderlichen Code-Änderungen für die Kompatibilität mit Cloud Service zu bewerten.

### Überprüfen der Ressourcenplanung {#review-resource-planning}

Nachdem Sie den für die Umstellung auf Cloud Service erforderlichen Arbeitsaufwand geschätzt haben, sollten Sie Ressourcen identifizieren, ein Team erstellen und Rollen und Verantwortlichkeiten für die Umstellung zuordnen.

### Festlegen von KPIs {#establish-kpis}

Wenn Sie zuvor noch keine Bewertungsparameter (Key Performance Indicators, KPIs) festgelegt haben, wird empfohlen, KPIs für Ihre Adobe Experience Manager (AEM)-Implementierung festzulegen, damit sich Ihr Team auf das Wesentliche konzentrieren kann.

Unter [Entwickeln von KPIs](https://guided.adobe.com/welcome/aem/part6.html) erfahren Sie, wie Sie die richtigen KPIs für Ihre Geschäftsziele auswählen.
