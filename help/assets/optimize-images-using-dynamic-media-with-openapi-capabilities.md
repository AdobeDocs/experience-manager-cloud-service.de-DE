---
title: Optimieren von Bildern mit Dynamic Media mit OpenAPI-Funktionen
description: Erfahren Sie, wie Sie Bilder vor der öffentlichen Bereitstellung mithilfe der Bildoptimierungsfunktionen von Dynamic Media mit OpenAPI-Funktionen spontan optimieren können
role: Admin
feature: Asset Management, Publishing, Collaboration, Asset Processing
source-git-commit: 5a01aff1d6c10d86e2faef22da2dbe724e24e673
workflow-type: tm+mt
source-wordcount: '1265'
ht-degree: 0%

---


# Optimieren von Bildern mit Dynamic Media mit OpenAPI-Funktionen{#Optimize-images-using-Dynamic-Media-with-OpenAPI-Capabilities}

[!DNL Dynamic Media with OpenAPI capabilities] bietet Bildoptimierungsfunktionen wie [!DNL Smart Crop], [!DNL Image Presets] und [!DNL Smart Imaging]. Mit diesen Funktionen können Sie hochqualitative, responsive Bilder bereitstellen, die auf verschiedenen Geräten und Netzwerken schnell geladen werden.

## Intelligenter Zuschnitt{#smart-crop-using-dynamic-media-with-openapi-capabilities}

[Smartes Zuschneiden](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=smartcrop&t=request) ist eine dynamische Größenänderungsfunktion von [!DNL Dynamic Media with OpenAPI capabilities]. [!DNL Smart Crop] ist eine fortschrittliche Bildverarbeitungstechnik, die KI-gestütztes inhaltsorientiertes Zuschneiden verwendet, um Bilder für verschiedene Bildschirmgrößen intelligent zuzuschneiden, während der visuelle Kontext in zugeschnittenen Versionen erhalten bleibt. Die KI analysiert das Bild, um den Fokus oder den Zielpunkt zu identifizieren, und schneidet dann das Bild automatisch zu, um den Fokus in allen zugeschnittenen Versionen beizubehalten. [!DNL Smart Crop], ein Schlüsselelement des responsiven Designs, bietet eine kostengünstige und zeiteffiziente Möglichkeit, Bilder zuzuschneiden.

Im Artikel [Dynamic Media-Bildprofile](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles) erfahren Sie, wie Sie [Ausgabedarstellungen für smartes Zuschneiden erstellen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#creating-image-profiles) in [!DNL Admin View], [sie auf Ordner anwenden](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#applying-an-image-profile-to-folders) oder [Ausgabedarstellungen bearbeiten](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles#editing-the-smart-crop-or-smart-swatch-of-a-single-image) die bereits auf ein Bild oder einen Ordner angewendet wurden. In diesem Video erfahren Sie, wie Sie Schritt für Schritt einen [!DNL Smart Crop] [ erstellen](https://experienceleague.adobe.com/de/docs/experience-manager-learn/assets/dynamic-media/images/smart-crop-feature-video-use).

Der [!DNL Smart Crop] Parameter erwartet, dass „named-smartcut-profiles“ vorhanden sind und auf das Asset angewendet wurden. Weitere Informationen [ Parameter &quot;](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=smartcrop&t=request)&quot; und [!DNL Smart Crop] Anwendung von Profilen mit [!DNL Smart Crop] Namen finden Sie unter „Smartes Zuschneiden“.

>[!IMPORTANT]
>
> Sie können [!DNL Smart Crop] Ausgabedarstellungen nur in der Administratoransicht erstellen.

## Bildvorgaben{#image-presets-using-dynamic-media-with-openapi-capabilities}

So wandeln Sie Bilder mithilfe der [Bildvorgaben](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=preset&t=request) in [!DNL Dynamic Media with OpenAPI capabilities] um. Ein [!DNL image preset] ist ein vordefinierter Satz von Größenangaben und Formatierungsregeln für ein Ausgabebild.

[!DNL Dynamic Media with OpenAPI capabilities] verwendet Vorgabennamen, um ein Bild dynamisch zu transformieren und sofort seine Ausgabedarstellung zu generieren. Wenn Sie ein Bild über eine [!DNL Dynamic Media with OpenAPI] Versand-URL anfordern, die einen vordefinierten Parameter enthält, wendet [!DNL DM with OpenAPI] die Transformationen der Vorgabe an, erstellt die Ausgabedarstellung bei Bedarf und stellt sie dem Benutzer bereit.

Sie können eine einzelne Vorgabe über die [!DNL Dynamic Media with OpenAPI] Versand-URLs auf mehrere Bilder anwenden. Dadurch wird eine konsistente Formatierung aller Assets sichergestellt, ohne dass jedes Asset manuell bearbeitet werden muss.

Weitere Informationen [Erstellen von Bildvorgaben in der Admin-](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets)) und „Erstellen [ responsiven Bildvorgaben“, ](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets#creating-image-presets) Assets automatisch an unterschiedliche Bildschirmgrößen [, finden Sie unter „Verwalten ](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/managing-image-presets#creating-a-responsive-image-preset) Bildvorgaben .

### Vorteile der Verwendung von Bildvorgaben{#benefits-of-image-presets}

[!DNL Image Presets] bieten mehrere Vorteile für die Verwaltung und Bereitstellung von Bildern in [!DNL Dynamic Media with OpenAPI]. Zu den wichtigsten Vorteilen gehören die folgenden:

* Voreinstellungen verkürzen URLs zur Bildbereitstellung. Verwenden Sie eine einzige Vorgabe, anstatt mehrere Bildmodifikatoren hinzuzufügen, die die Versand-URL verlängern. Kürzere URLs sind einfacher zu verwalten und stellen eine konsistente Bildbereitstellung über Websites, Mobile Apps, E-Mails und andere Kanäle hinweg sicher.
* Bildvorgaben erstellen Just-in-time-Ausgabedarstellungen aus einer Quellbilddatei. Durch diese Funktion zur Erzeugung von Ausgabedarstellungen auf Anfrage entfällt die Notwendigkeit, mehrere statische Ausgabedarstellungen derselben Datei zu erstellen und zu speichern, was Zeit und Speicher spart.
* Gleichzeitiges Anwenden einer einzelnen Vorgabe auf eine große Anzahl von Assets, Vermeidung manueller Bearbeitungen an jedem Asset einzeln, Sicherstellung einer konsistenten Formatierung und Ermöglichung von Skalierbarkeit.
* Wenn Sie die Parameter einer Vorgabe aktualisieren, werden alle Bilder, die diese Vorgabe verwenden, automatisch neu formatiert. Dadurch wird die Bearbeitung durch Zentralisierung von Formatierungsaktualisierungen optimiert, sodass einzelne Assets oder Web-Code nicht mehr neu bearbeitet werden müssen.
* Verbessert Effizienz und Leistung mit dynamischen Ausgabedarstellungen, die vom CDN zwischengespeichert werden, was zu schnellerem Laden und optimierter Leistung auf allen Geräten und Netzwerken führt.

### Verwenden von Bildvorgaben{#use-image-presets-using-dynamic-media-with-openapi-capabilities}

Nachdem Sie die [!DNL Image Presets] erstellt haben, können Sie sie für die folgenden Workflows verwenden:

* [Verwenden Sie Voreinstellungen in der Bildbereitstellungs-URL, um die Ausgabedarstellungen direkt zu erstellen, bevor Sie sie an den Endbenutzer versenden](#use-presets-in-delivery-urls)
* [Verwenden von Vorgaben beim Authoring in AEM Sites](#use-presets-during-authoring-in-aem-sites)

#### Verwenden von Vorgaben in Bildbereitstellungs-URLs{#use-presets-in-delivery-urls}

Voreinstellungen machen Ihre Versand-URLs kürzer und benutzerfreundlicher.  Jeder Vorgabenname dient als eindeutige Kennung in der Versand-URL. Anstatt der Bereitstellungs-URL eines Assets mehrere Modifikatoren hinzuzufügen, verweisen Sie auf den Vorgabennamen, um die Ausgabedarstellung sofort zu generieren. [Erfahren Sie, wie Sie Dynamic Media-Bildvorgaben auf Ihr Bild anwenden](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-presets).
Im folgenden Beispiel wird eine URL mit einer Voreinstellung mit einer URL ohne Voreinstellung verglichen.

**URL ohne Voreinstellung (lange URL)**:

```
https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:393d5579-5be2-49a5-ac5f-8fed72bfb614/as/AdobeStock_63266433.avif?width=400&height=300&fit=crop&qualit=85&sharpen=true
```

**URL mit einer Voreinstellung (kurze URL)**:

```
https://delivery-p30902-e145436-cmstg.adobeaemcloud.com/adobe/assets/urn:aaid:aem:393d5579-5be2-49a5-ac5f-8fed72bfb614/as/AdobeStock_63266433.avif?preset=thumbnail
```

Die vordefinierte Miniaturansicht enthält die gleichen Bildmodifikatoreinstellungen.

#### Verwenden von Vorgaben beim Authoring in AEM Sites{#use-presets-during-authoring-in-aem-sites}

Autoren können während der Seitenbearbeitung auf [!DNL Image Presets] Authoring-Seite [!DNL AEM Sites] auswählen, wenn [!DNL Dynamic Media] Unterstützung aktiviert ist.

Führen Sie die folgenden Schritte aus, um Bildvorgaben auf Ihrer Authoring-Seite zu verwenden:

1. Navigieren Sie zu Ihrer Sites-Authoring-Seite.
1. Führen Sie die Schritte im Abschnitt [Zugriff auf Remote-Assets im AEM](/help/assets/integrate-remote-approved-assets-with-sites.md#access-remote-assets-in-aem-page-editor)Seiteneditor aus, um das [!DNL Asset Selector]-Bedienfeld zur Auswahl eines Assets zu verwenden.
1. Scrollen Sie im [!DNL asset selector] nach unten zu **[!UICONTROL Vorgabetyp]** geben Sie `Preset=Preset Name` im Feld **[!UICONTROL Bildmodifikatoren]** an.

   ![Voreinstellung](/help/assets/assets/preset-in-asset-selector-panel.png)

## Intelligente Bildbearbeitung{#use-smart-imaging-using-dynamic-media-with-openapi-capabilities}

Wenn Sie [!DNL Dynamic Media with OpenAPI capabilities] für die Bildbereitstellung verwenden, werden Bilder automatisch durch [intelligente Bildbearbeitung](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/) optimiert. Die optimierte Bereitstellung stellt sicher, dass Bilder schneller geladen werden, eine maximale visuelle Qualität aufweisen und eine minimale Dateigröße aufweisen. Dies führt zu schnellsten Seitenladevorgängen und einer konsistent hohen visuellen Qualität auf allen Geräten und in allen Netzwerken. Gleichzeitig wird nur minimale Bandbreite beansprucht, was Ihre Website schneller und reaktionsfähiger macht.

[!DNL Smart Imaging] umfasst die folgenden Funktionen:

* [Automatische Formatkonvertierung](#auto-format-conversion)
* [Optimierung der Netzwerkbandbreite](#network-bandwidth-optimisation)

### Automatische Formatkonvertierung{#auto-format-conversion}

[!DNL Dynamic Media with OpenAPI] [konvertiert Bilder automatisch in moderne, Web-optimierte Formate wie AVIF oder WEBP](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=auto-format&t=request). Die Konvertierung hängt von den Browserfunktionen und [Lizenzberechtigungen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-prime-ultimate) ab, unabhängig vom angeforderten Format.

AVIF- und WEBP-Formate bieten eine bessere Komprimierung, sodass Bilder kleiner und schneller bereitgestellt und geladen werden können. AVIF wird als Standardformat verwendet, da es alle Browser-Funktionen verarbeitet.

[!DNL Dynamic Media with OpenAPI] verwendet den `auto-format` Abfrageparameter, um das Verhalten des Browsers zur Konvertierung eines Bildes in verschiedene Formate für eine optimierte Bereitstellung zu steuern. Die automatische Formatkonvertierung umfasst **automatische Promotion** und **automatische**. Wenn das System ein Web-optimiertes Format (AVIF oder WEBP) über JPEG oder PNG für die Bereitstellung fördert, wird dies als automatische Promotion bezeichnet.

Standardmäßig ist der `auto-format` Abfrageparameter auf `true` festgelegt. Wenn `auto-format` aktiviert ist (true), ignoriert das System das angeforderte Format und wählt automatisch ein Web-optimiertes Format (AVIF oder WEBP) basierend auf Bildeigenschaften, Browser-Funktionen und [Lizenzberechtigungen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/assets/dynamicmedia/dm-prime-ultimate) aus.

Wenn `auto-format` „true“ ist, liefert das System das Bildformat in der folgenden Reihenfolge:

* ***AVIF***: AVIF wird bereitgestellt, wenn der Browser dies unterstützt und die Lizenz dies zulässt. Dies wird als automatische Promotion bezeichnet.
* ***WEBP***: WEBP wird bereitgestellt, wenn AVIF nicht unterstützt oder lizenziert wird. Dies ist auch eine automatische Promotion.
* ***JPEG***: JPEG wird nur bereitgestellt, wenn AVIF und WEBP nicht unterstützt werden und das Bild keinen Alphakanal aufweist (Transparenz). Dies wird als automatische Herabstufung bezeichnet.
* ***PNG***: PNG wird bereitgestellt, wenn der Browser moderne Formate nicht unterstützt und das Bild einen Alphakanal (Transparenz) aufweist. Dies wird auch als automatische Herabstufung bezeichnet.

Deaktivieren Sie `auto-format`, indem Sie den Abfrageparameter auf `false` setzen, und geben Sie dann das erforderliche Format an, um das Bild in diesem Format bereitzustellen.

### Optimierung der Netzwerkbandbreite{#network-bandwidth-optimisation}

Bilder werden automatisch auf Basis der Netzwerkbedingungen des Kunden optimiert, um eine schnellere Bereitstellung und ein reibungsloses Laden zu gewährleisten. Die Parameter [Qualität](#quality-parameter) und [Max-Qualität](#max-quality-parameter) passen die Qualität automatisch an, indem sie die Bildkomprimierungsstufen mit Werten zwischen 1 und 100 steuern.

Siehe die folgenden Schlüsselverhaltensweisen von `quality` und `max-quality `Parametern:

* Wenn sowohl [!DNL quality] als auch [!DNL max-quality] angegeben sind, hat [!DNL quality] Vorrang.
* Wenn nur [!DNL quality] angegeben ist, wird die Qualität unabhängig von der Ladezeit basierend auf der Netzwerkgeschwindigkeit bereitgestellt.
* Wenn nur [!DNL max-quality] angegeben wird, passt sich die Bildqualität automatisch an die Netzwerkbedingungen an und liefert die bestmögliche Qualität bis zum angegebenen [!DNL max-quality].
* Wenn keines von beiden angegeben ist, wendet das System die dynamische Optimierung mit dem `max-quality` `85` an.

#### Qualitätsparameter{#quality-parameter}

Der Qualitätsparameter priorisiert die Bildqualität vor der Ladegeschwindigkeit. Die Qualität des ausgegebenen Bildes wird auf den angeforderten Wert (zwischen 1 und 100) festgelegt und die Netzwerkbedingungen werden ignoriert. Erfahren Sie mehr über den [Qualitätsparameter](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=quality&t=request).

#### Parameter für maximale Qualität{#max-quality-parameter}

Die maximale Qualität gleicht die Bildqualität und die Ladezeit basierend auf der Netzwerkgeschwindigkeit des Clients aus. Es priorisiert schnellere Ladezeiten, indem es die Bildqualität in langsameren Netzwerken senkt, während es dennoch die höchstmögliche Qualität (1-100) für die gegebenen Netzwerkbedingungen liefert. Weitere Informationen zum Parameter [max-quality](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/assets/delivery/#operation/getAssetSeoFormat!in=query&path=quality&t=request).
