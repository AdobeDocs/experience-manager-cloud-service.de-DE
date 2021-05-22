---
title: Veraltete und entfernte Funktionen
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: 8c26dbcc77113b86ab28ab52e0b6564fa5ed538a
workflow-type: tm+mt
source-wordcount: '448'
ht-degree: 45%

---

# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird. Da [!DNL Adobe Experience Manager] als [!DNL Cloud Service] ein Cloud-natives Bereitstellungsmodell bereitstellt, wurden bestimmte Funktionen und Funktionen durch Cloud-native Entsprechungen ersetzt.

Für die Mitteilung der bevorstehenden Entfernung/Ersetzung von [!DNL Experience Manager]-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Veraltete Funktionen sind weiterhin verfügbar, werden aber nicht weiter verbessert.
1. Funktionen, für die eine künftige Aufhebung der Unterstützung angekündigt wurde, werden frühestens in der nächsten Hauptversion entfernt. Der tatsächliche Termin für das Entfernen wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgelistet, die in [!DNL Experience Manager] als [!DNL Cloud Service] nicht mehr unterstützt wurden. In der Regel werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zuerst als veraltet gekennzeichnet, wobei eine Alternative bereitgestellt wird.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung verwenden, und Pläne zu erstellen, um ihre Implementierung zu ändern und die bereitgestellte Alternative zu nutzen.

| Funktionen | Veraltete Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| [!DNL Assets] | `DAM Asset Update`-Workflow zur Verarbeitung erfasster Bilder. | Für die Asset-Erfassung werden jetzt [Asset-Microservices](/help/assets/asset-microservices-overview.md) verwendet. |
| [!DNL Assets] | Hochladen von Assets direkt in [!DNL Experience Manager]. Siehe [veraltete APIs zum Hochladen von Assets](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Verwenden Sie den [direkten binären Upload](/help/assets/add-assets.md). Weitere technische Daten finden Sie im Abschnitt zu den [APIs für den direkten Upload](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Bestimmte Workflow-Schritte ](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) im `DAM Asset Update`-Workflow werden nicht unterstützt, darunter der Aufruf von Befehlszeilen-Tools wie ImageMagick. | [Asset-Microservices](/help/assets/asset-microservices-overview.md) bieten Ersatz für viele Workflows. Verwenden Sie für die benutzerdefinierte Verarbeitung [Nachbearbeitungs-Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | FFmpeg-Transcodierung von Videos. | Verwenden Sie für die Generierung von FFmpeg-Miniaturansichten [Asset-Microservices](/help/assets/asset-microservices-overview.md). Verwenden Sie für die von FFmpeg-Transcodierung [Dynamic Media](/help/assets/manage-video-assets.md). |

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen aufgelistet, die aus [!DNL Experience Manager] mit [!DNL Experience Manager] als [!DNL Cloud Service] entfernt wurden.

| Bereich | Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| Benutzeroberfläche | Die klassische Benutzeroberfläche wurde aus der Produktoberfläche entfernt. Für einige ausgewählte Funktionen wie Link Checker, Versionsbereinigung und einige Cloud Service-Konfigurationen sind einige Dialogfelder der klassischen Benutzeroberfläche verfügbar. Künftige [Produktupdates](/help/release-notes/home.md) können die Verfügbarkeit der klassischen Benutzeroberfläche weiter entfernen. | Standard-Benutzeroberfläche |
| [!DNL Dynamic Media] | Frühere Integrationen mit [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=de#integration) und [Dynamic Media Hybridmodus](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=de#dynamic) sind in [!DNL Experience Manager] nicht als [!DNL Cloud Service] verfügbar. | Verwenden Sie [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md), das mit [!DNL Experience Manager] als [!DNL Cloud Service] bereitgestellt wird. |
| [!DNL Sites] | Komponenten „Portal Director“ und „Portlet“ | Diese Funktionen wurden in [!DNL Experience Manager] 6.4 nicht mehr unterstützt und wurden nun aus [!DNL Experience Manager] entfernt. |
| [!DNL Sites] | Design-Import-Tool | Diese Funktion wurde entfernt, da unveränderliche Abschnitte des [!DNL Experience Manager]-Repositorys zur Laufzeit nicht verfügbar sind. |
| [!DNL Assets] | [!DNL Assets] Die Freigabe für Marketing Cloud Assets Core Service und Creative Cloud Services ist nicht verfügbar. | Verwenden Sie für die Integration mit [!DNL Adobe Creative Cloud] [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html). |
