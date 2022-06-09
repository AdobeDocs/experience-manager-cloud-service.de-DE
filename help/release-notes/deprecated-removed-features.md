---
title: Veraltete und entfernte Funktionen
description: Spezifische Versionshinweise zu veralteten und entfernten Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service].
exl-id: ef082184-4eb7-49c7-8887-03d925e3da6f
source-git-commit: c4809bcbeae5339427b1da588021606d18b482a5
workflow-type: tm+mt
source-wordcount: '666'
ht-degree: 91%

---

# Veraltete und entfernte Funktionen {#deprecated-and-removed-features}

>[!CONTEXTUALHELP]
>id="aem_cloud_deprecated_features"
>title="Veraltete und entfernte Funktionen in AEM as a Cloud Service"
>abstract="AEM as a Cloud Service verfügt über ein Cloud-natives Implementierungsmodell. Bestimmte Funktionen wurden von Cloud-nativen Gegenstücken ersetzt. Diese Registerkarte zeigt diese Funktionen."


Adobe evaluiert fortlaufend Produktfunktionen, um ältere Features zu überarbeiten oder durch modernere Alternativen zu ersetzen und so den Nutzen für die Kunden insgesamt zu verbessern, wobei stets auf Abwärtskompatibilität geachtet wird. Da [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] ein Cloud-natives Implementierungsmodell bietet, wurden bestimmte Funktionen und Features durch Cloud-native Entsprechungen ersetzt.

Für die Bekanntgabe des bevorstehenden Entfernens/Ersetzens von [!DNL Experience Manager]-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Veraltete Funktionen bleiben weiterhin verfügbar, werden aber nicht weiter verbessert.
1. Funktionen, für die eine künftige Aufhebung der Unterstützung angekündigt wurde, werden frühestens in der nächsten Hauptversion entfernt. Der tatsächliche Termin für das Entfernen wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Veraltete Funktionen {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgeführt, die in [!DNL Experience Manager] as a [!DNL Cloud Service] als veraltet gekennzeichnet wurden. In der Regel werden Funktionen, die in einer künftigen Version entfernt werden sollen, zuerst als veraltet gekennzeichnet, wobei eine Alternative bereitgestellt wird.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Implementierung nutzen, und die Änderung ihrer Implementierung zu planen, um die bereitgestellte Alternative nutzen zu können.

| Funktionen | Veraltete Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| [!DNL Sites] | Experience Fragments-Eigenschaften für **Social-Media-Status**. | Die Funktion wird bald entfernt. |
| [!DNL Sites] | Vorlagenbasierte einfache Inhaltsfragmente. | Jetzt [Modellbasierte strukturierte Inhaltsfragmente](/help/assets/content-fragments/content-fragments-models.md). |
| [!DNL Assets] | `DAM Asset Update`-Workflow zur Verarbeitung erfasster Bilder. | Für die Asset-Erfassung werden jetzt [Asset-Microservices](/help/assets/asset-microservices-overview.md) verwendet. |
| [!DNL Assets] | Assets können direkt in [!DNL Experience Manager] hochgeladen werden. Weitere Informationen dazu finden Sie im Abschnitt zu [veralteten Upload-APIs für Assets](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api). | Verwenden Sie den [direkten binären Upload](/help/assets/add-assets.md). Weitere technische Daten finden Sie im Abschnitt zu den [APIs für den direkten Upload](/help/assets/developer-reference-material-apis.md#upload-binary). |
| [!DNL Assets] | [Bestimmte Workflow-Schritte ](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) im `DAM Asset Update`-Workflow werden nicht unterstützt, darunter der Aufruf von Befehlszeilen-Tools wie [!DNL ImageMagick]. | [Asset-Microservices](/help/assets/asset-microservices-overview.md) bieten Ersatz für viele Workflows. Verwenden Sie für die benutzerdefinierte Verarbeitung [Nachbearbeitungs-Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |
| [!DNL Assets] | FFmpeg-Transcodierung von Videos. | Verwenden Sie für die Generierung von FFmpeg-Miniaturen [Asset-Microservices](/help/assets/asset-microservices-overview.md). Verwenden Sie für die von FFmpeg-Transcodierung [Dynamic Media](/help/assets/manage-video-assets.md). |
| [!DNL Foundation] | Benutzeroberfläche für die Strukturreplikation auf der Registerkarte „Verteilung“ des Replikationsagenten (wird nach dem 30. September 2021 entfernt) | Ansätze für [Veröffentlichungen verwalten](/help/operations/replication.md#manage-publication) oder [Workflows zur Veröffentlichung von Inhaltsbäumen](/help/operations/replication.md#publish-content-tree-workflow) |
| [!DNL Foundation] | Weder die Registerkarte &quot;Verteilung&quot;des Administrationsbildschirms des Replikationsagenten noch die Replikations-API können verwendet werden, um Inhaltspakete über 10 MB zu replizieren (Durchsetzung nach dem 12. September 2022). | Ansätze für [Veröffentlichungen verwalten](/help/operations/replication.md#manage-publication) oder [Workflows zur Veröffentlichung von Inhaltsbäumen](/help/operations/replication.md#publish-content-tree-workflow) |


| [!DNL Foundation]       | Weder die Registerkarte &quot;Verteilen&quot;des Administrationsbildschirms des Replikationsagenten noch die Replikations-API können verwendet werden, um Inhaltspakete über 10 MB zu replizieren. Verwenden Sie stattdessen entweder [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder [Arbeitsablauf für Veröffentlichungsinhalte](/help/operations/replication.md#publish-content-tree-workflow) |

## Entfernte Funktionen {#removed-features}

In diesem Abschnitt werden Funktionen aufgeführt, die aus [!DNL Experience Manager] mit [!DNL Experience Manager] as a [!DNL Cloud Service] entfernt wurden.

| Bereich | Funktion | Ersatz | Zieltermin für die Entfernung |
| ------------ | ------------------ | ----------- | ------------------- |
| Benutzeroberfläche | Die Classic-Benutzeroberfläche wurde aus der Produkt-Benutzeroberfläche entfernt. Für einige ausgewählte Funktionen wie Link Checker, Versionsbereinigung und einige Cloud Service-Konfigurationen sind einige Dialogfelder der Classic-Benutzeroberfläche verfügbar. Künftige [Produkt-Updates](/help/release-notes/home.md) können weitere verfügbare Elemente der Classic-Benutzeroberfläche entfernen. | Standard-Benutzeroberfläche | Entfernt |
| [!DNL Dynamic Media] | Frühere Integrationen mit [Dynamic Media Classic](https://experienceleague.adobe.com/docs/experience-manager-65/administering/integration/scene7.html?lang=de#integration) und dem [Dynamic Media-Hybridmodus](https://experienceleague.adobe.com/docs/experience-manager-65/assets/dynamic/config-dynamic.html?lang=de#dynamic) sind in [!DNL Experience Manager] as a [!DNL Cloud Service] nicht verfügbar. | Verwenden Sie [Dynamic Media](/help/assets/dynamic-media/dynamic-media.md), das mit [!DNL Experience Manager] as a [!DNL Cloud Service]bereitgestellt wird. | Entfernt |
| [!DNL Sites] | Komponenten „Portal Director“ und „Portlet“ | Diese Funktionen gelten seit [!DNL Experience Manager] 6.4 als veraltet und wurden nun aus [!DNL Experience Manager] entfernt. | Entfernt |
| [!DNL Sites] | Design-Import-Tool | Diese Funktion wurde entfernt, da auf unveränderliche Abschnitte des [!DNL Experience Manager]-Repositorys nicht zur Laufzeit zugegriffen werden kann. | Entfernt |
| [!DNL Assets] | [!DNL Assets]-Freigabe für Marketing Cloud Assets Core Service und Creative Cloud-Services ist nicht verfügbar. | Zur Integration mit [!DNL Adobe Creative Cloud] verwenden Sie [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html). | Entfernt |
| [!DNL Foundation] | Unterstützung für Apache Sling-Datenquellen (OSGi-Bundle org.apache.sling.datasource) | Nicht zutreffend | Entfernt |
| [!DNL Foundation] | Unterstützung für JST-Skriptvorlagen (OSGi-Bundle org.apache.sling.scripting.jst) | Nicht zutreffend | Entfernt |
| [!DNL Foundation] | Unterstützung für das Apache Felix Http Whiteboard | OSGi Http Whiteboard | März 2022 |

## Java-API {#java-api}

Auf [dieser Seite](/help/release-notes/deprecated-apis.md) finden Sie weitere Informationen zu allen veralteten oder entfernten Java-APIs, die gelegentlich eingeführt werden.

## OSGi-Konfiguration {#osgi-configuration}

In [diesem Artikel](/help/implementing/deploying/osgi-configuration-api.md) finden Sie alle Einschränkungen bezüglich der Konfiguration von OSGi-Eigenschaften, von denen einige im Laufe der Zeit eingeführt werden können.
