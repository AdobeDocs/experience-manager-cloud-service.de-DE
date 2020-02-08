---
title: Veraltete und entfernte Funktionen
description: Versionshinweise zu nicht mehr unterstützten und entfernten Funktionen in Adobe Experience Manager als Cloud-Dienst.
translation-type: tm+mt
source-git-commit: b31ae32285080075d2531edd2c4976cf801d1c89

---


# Deprecated and removed features {#deprecated-and-removed-features}

Adobe bewertet die Produktfunktionen ständig, um ältere Funktionen mit der Zeit neu zu erfinden oder durch modernere Alternativen zu ersetzen, um den Gesamtwert der Kunden zu verbessern, wobei stets die Abwärtskompatibilität zu berücksichtigen ist. Da Adobe Experience Manager als Cloud-Dienst ein Cloud-natives Bereitstellungsmodell bereitstellt, wurden bestimmte Funktionen und Funktionen durch Cloud-native Gegenstücke ersetzt.

Für die Bekanntgabe des bevorstehenden Entfernens/Ersetzens von AEM-Funktionen gelten die folgenden Regeln:

1. Zunächst wird angekündigt, dass die betreffende Funktion veraltet ist. Veraltete Funktionen bleiben weiterhin verfügbar, werden aber nicht weiter verbessert.
1. Funktionen, die als veraltet angekündigt werden, werden in der folgenden Hauptversion frühestens entfernt. Der tatsächliche Termin für die Entfernung wird bekannt gegeben.

Dieser Prozess räumt Kunden mindestens einen Veröffentlichungszyklus ein, um ihre Implementierung an eine neue Version oder die Nachfolgeversion einer veralteten Funktion anzupassen, bevor die Funktion tatsächlich entfernt wird.

## Deprecated features {#deprecated-features}

In diesem Abschnitt werden Funktionen aufgelistet, die in Experience Manager als nicht mehr unterstützt markiert wurden. In der Regel werden Funktionen, die in einer zukünftigen Version entfernt werden sollen, zuerst auf &quot;Veraltet&quot;eingestellt, es wird eine Alternative bereitgestellt.

Kunden wird empfohlen zu überprüfen, ob sie die Funktion in ihrer aktuellen Bereitstellung nutzen, und Pläne zur Änderungen ihrer Implementierung zu erstellen, um die bereitgestellte Alternative nutzen zu können.

| Bereich | Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| Assets | Asset-Erfassung und -Verarbeitung verwenden keinen `DAM Asset Update` Workflow mehr | Asset-Erfassung verwendet jetzt [Asset-Mikrodienste](/help/assets/asset-microservices-overview.md) . |
| Assets | Hochladen von Assets direkt in AEM - siehe APIs zum Hochladen [veralteter Assets](/help/assets/developer-reference-material-apis.md#deprecated-asset-upload-api) | [Das direkte binäre Hochladen](/help/assets/add-assets.md) wird in Experience Manager als Cloud-Dienst verwendet. Technische Informationen finden Sie unter APIs [für das direkte Hochladen](/help/assets/developer-reference-material-apis.md#overview-binary-upload). |
| Assets | [Bestimmte Workflow-Schritte](/help/assets/developer-reference-material-apis.md#post-processing-workflows-steps) im `DAM Asset Update` Workflow werden nicht unterstützt, einschließlich des Aufrufs von Befehlszeilenwerkzeugen wie ImageMagick | [Asset-Mikrodienste](/help/assets/asset-microservices-overview.md) stellen einen Ersatz für viele Arbeitsabläufe dar. Verwenden Sie für die benutzerdefinierte Verarbeitung die Arbeitsabläufe [nach der Verarbeitung](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows). |

## Removed features {#removed-features}

Dieser Abschnitt listet Funktionen auf, die aus AEM mit Experience Manager als Cloud-Dienst entfernt wurden.

| Bereich | Funktion | Ersatz |
| ------------ | ------------------ | ----------- |
| Benutzeroberfläche | Während einige Classic-UI-Dialogfelder für einige ausgewählte Funktionen wie Link Checker, Version Purge und einige Cloud-Dienstkonfigurationen noch bestehen, wurde der Zugriff auf die klassische Benutzeroberfläche in der AEM-Produkt-Benutzeroberfläche generell entfernt. | Standard-UI |
| Dynamic Media | Frühere Integrationen mit [Dynamic Media Classic (Scene7)](https://helpx.adobe.com/experience-manager/6-5/sites/administering/using/scene7.html) und dem [dynamischen Media Hybrid-Modus](https://helpx.adobe.com/experience-manager/6-5/assets/using/config-dynamic.html) sind in AEM nicht als Cloud-Dienst verfügbar. | Verwenden Sie die mit Experience Manager bereitgestellten [dynamischen Medien](/help/assets/dynamic-media/dynamic-media.md) als Cloud-Dienst. |
| Sites | Portaldirektor und Portlet-Komponente | Diese Funktionen wurden in AEM 6.4 nicht mehr unterstützt und wurden jetzt aus AEM entfernt. |
| Sites | Design-Importtool | Diese Funktion wurde entfernt, da unveränderliche Abschnitte des AEM-Repositorys zur Laufzeit nicht verfügbar sind. |
| Assets | [Die Freigabe von AEM Assets mit dem Hauptdienst Marketing Cloud Assets und den Creative Cloud-Diensten](https://docs.adobe.com/content/help/en/experience-manager-65/administering/integration/configure-assets-cc-integration.html) ist nicht verfügbar. | Für die Integration in die Creative Cloud verwenden Sie [Adobe Asset Link](https://helpx.adobe.com/enterprise/using/adobe-asset-link.html). |
