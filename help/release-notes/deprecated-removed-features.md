---
title: Veraltete und entfernte Funktionen
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von Adobe Experience Manager as a Cloud Service
translation-type: tm+mt
source-git-commit: e31ac0c2d28f60d7b98036c16f154a09da51d6bf
workflow-type: tm+mt
source-wordcount: '506'
ht-degree: 100%

---


# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird. Da Adobe Experience Manager as a Cloud Service ein Cloud-natives Implementierungsmodell bietet, wurden bestimmte Funktionen und Features durch Cloud-native Entsprechungen ersetzt.

Für die Bekanntgabe des bevorstehenden Entfernens/Ersetzens von AEM-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Veraltete Funktionen bleiben weiterhin verfügbar, werden aber nicht weiter verbessert.
1. Funktionen, für die eine künftige Aufhebung der Unterstützung angekündigt wurde, werden frühestens in der nächsten Hauptversion entfernt. Der tatsächliche Termin für das Entfernen wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die in Adobe Experience Manager as a Cloud Service als veraltet gekennzeichnet wurden. In der Regel werden Funktionen, die in einer künftigen Version entfernt werden sollen, zuerst als veraltet gekennzeichnet, wobei eine Alternative bereitgestellt wird.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und Pläne zur Änderung ihrer Implementierung zu erstellen, um die bereitgestellte Alternative nutzen zu können.

| Funktionen | Veraltete Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| Assets | `DAM Asset Update`-Workflow zur Verarbeitung erfasster Bilder. | Für die Asset-Erfassung werden jetzt [Asset-Microservices](/help/assets/asset-microservices-overview.md) verwendet. |
| Assets | Assets können direkt in AEM hochgeladen werden. Weitere Informationen dazu finden Sie im Abschnitt zu [veralteten Upload-APIs für Assets](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Verwenden Sie den [direkten binären Upload](/help/assets/add-assets.md). Weitere technische Daten finden Sie im Abschnitt zu den [APIs für den direkten Upload](/help/assets/developer-reference-material-apis.md#upload-binary). |
| Assets | [Bestimmte Workflow-Schritte ](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) im `DAM Asset Update`-Workflow werden nicht unterstützt, darunter der Aufruf von Befehlszeilen-Tools wie ImageMagick. | [Asset-Microservices](/help/assets/asset-microservices-overview.md) bieten Ersatz für viele Workflows. Verwenden Sie für die benutzerdefinierte Verarbeitung [Nachbearbeitungs-Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| Assets | FFmpeg-Transcodierung von Videos. | Verwenden Sie für die Generierung von FFmpeg-Miniaturansichten [Asset-Microservices](/help/assets/asset-microservices-overview.md). Verwenden Sie für die von FFmpeg-Transcodierung [Dynamic Media](/help/assets/manage-video-assets.md). |

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen aufgeführt, die aus Adobe Experience Manager as a Cloud Service entfernt wurden.

| Bereich | Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| Benutzeroberfläche | Während einige Dialogfelder der klassischen Benutzeroberfläche für ausgewählte Funktionen wie Prüfer für externe Links, Versionsbereinigung und einige Cloud Service-Konfigurationen vorerst weiterhin verfügbar sind, kann generell nicht mehr auf die klassische Benutzeroberfläche in der AEM-Produkt-Benutzeroberfläche zugegriffen werden. | Standard-Benutzeroberfläche |
| Dynamic Media | Frühere Integrationen mit [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=de#integration) und dem [Dynamic Media-Hybridmodus](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=de#dynamic) sind nicht in AEM as a Cloud Service verfügbar. | Verwenden Sie die mit Adobe Experience Manager as a Cloud Service bereitgestellte [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md)-Funktion. |
| Sites | Komponenten „Portal Director“ und „Portlet“ | Diese Funktionen gelten seit AEM 6.4 als veraltet und wurden nun aus AEM entfernt. |
| Sites | Design-Import-Tool | Diese Funktion wurde entfernt, da auf unveränderliche Abschnitte des AEM-Repositorys nicht zur Laufzeit zugegriffen werden kann. |
| Assets | [AEM Assets-Freigabe für Experience Cloud Assets Core Service und Creative Cloud-Services](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/integration/configure-assets-cc-integration.html) ist nicht verfügbar. | Verwenden Sie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html) zur Integration mit Creative Cloud. |
