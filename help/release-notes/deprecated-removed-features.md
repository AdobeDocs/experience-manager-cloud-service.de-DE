---
title: Veraltete und entfernte Funktionen
description: Versionshinweise, die spezifisch für veraltete und entfernte Funktionen in [!DNL Adobe Experience Manager] als a [!DNL Cloud Service] sind.
translation-type: tm+mt
source-git-commit: e6ad571b7428f6fb7a11907e752ba670a722057c
workflow-type: tm+mt
source-wordcount: '457'
ht-degree: 46%

---


# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird. Da [!DNL Adobe Experience Manager] als [!DNL Cloud Service] ein Cloud-natives Bereitstellungsmodell bereitstellt, wurden bestimmte Funktionen und Funktionen durch Cloud-native Gegenstücke ersetzt.

Für die Mitteilung der bevorstehenden Entfernung/Ersetzung von [!DNL Experience Manager]-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Veraltete Funktionen stehen weiterhin zur Verfügung, werden aber nicht weiter verbessert.
1. Funktionen, für die eine künftige Aufhebung der Unterstützung angekündigt wurde, werden frühestens in der nächsten Hauptversion entfernt. Der tatsächliche Termin für das Entfernen wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen Liste, die in [!DNL Experience Manager] als [!DNL Cloud Service] als nicht mehr unterstützt markiert wurden. In der Regel werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zuerst auf &quot;Veraltet&quot;eingestellt, wobei eine Alternative bereitgestellt wird.

Kunden wird empfohlen, zu prüfen, ob sie die Funktion/Funktion in ihrer aktuellen Bereitstellung verwenden, und Pläne zur Änderung ihrer Implementierung zu erstellen, um die verfügbare Alternative zu nutzen.

| Funktionen | Veraltete Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| [!DNL Assets] | `DAM Asset Update`-Workflow zur Verarbeitung erfasster Bilder. | Für die Asset-Erfassung werden jetzt [Asset-Microservices](/help/assets/asset-microservices-overview.md) verwendet. |
| [!DNL Assets] | Hochladen von Assets direkt auf [!DNL Experience Manager]. Siehe [APIs zum Hochladen von veralteten Assets](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Verwenden Sie den [direkten binären Upload](/help/assets/add-assets.md). Weitere technische Daten finden Sie im Abschnitt zu den [APIs für den direkten Upload](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Bestimmte Workflow-Schritte ](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) im `DAM Asset Update`-Workflow werden nicht unterstützt, darunter der Aufruf von Befehlszeilen-Tools wie ImageMagick. | [Asset-Microservices](/help/assets/asset-microservices-overview.md) bieten Ersatz für viele Workflows. Verwenden Sie für die benutzerdefinierte Verarbeitung [Nachbearbeitungs-Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | FFmpeg-Transcodierung von Videos. | Verwenden Sie für die Generierung von FFmpeg-Miniaturansichten [Asset-Microservices](/help/assets/asset-microservices-overview.md). Verwenden Sie für die von FFmpeg-Transcodierung [Dynamic Media](/help/assets/manage-video-assets.md). |

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen Liste, die von [!DNL Experience Manager] mit [!DNL Experience Manager] als [!DNL Cloud Service] entfernt wurden.

| Bereich | Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| Benutzeroberfläche | Die klassische Benutzeroberfläche wird aus der Benutzeroberfläche des Produkts entfernt. Für einige ausgewählte Funktionen wie Link-Prüfer, Versionsbereinigung und einige Cloud Service-Konfigurationen stehen einige Dialogfelder der klassischen Benutzeroberfläche zur Verfügung. Kommende [Produktupdates](/help/release-notes/home.md) können die Verfügbarkeit der klassischen Benutzeroberfläche weiter entfernen. | Standard-Benutzeroberfläche |
| [!DNL Dynamic Media] | Frühere Integrationen mit [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=de#integration) und [Dynamic Media Hybrid-Modus](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=de#dynamic) sind in [!DNL Experience Manager] nicht als [!DNL Cloud Service] verfügbar. | Verwenden Sie [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md), das mit [!DNL Experience Manager] bereitgestellt wird, als [!DNL Cloud Service]. |
| [!DNL Sites] | Komponenten „Portal Director“ und „Portlet“ | Diese Funktionen wurden in [!DNL Experience Manager] 6.4 nicht mehr unterstützt und jetzt aus [!DNL Experience Manager] entfernt. |
| [!DNL Sites] | Design-Import-Tool | Diese Funktion wurde entfernt, da unveränderliche Abschnitte des [!DNL Experience Manager]-Repositorys zur Laufzeit nicht verfügbar sind. |
| [!DNL Assets] | [[!DNL Assets] Die Freigabe mit Marketing Cloud Assets Core Service und Creative Cloud Service ](https://docs.adobe.com/content/help/de-DE/experience-manager-65/administering/integration/configure-assets-cc-integration.html) ist nicht verfügbar. | Für die Integration mit [!DNL Adobe Creative Cloud] verwenden Sie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html). |
