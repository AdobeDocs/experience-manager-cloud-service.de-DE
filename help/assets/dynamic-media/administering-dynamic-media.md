---
title: Einrichten von Dynamic Media
description: Zum Einrichten von Dynamic Media müssen Sie Dynamic Media konfigurieren und Bild- sowie Viewer-Vorgaben verwalten.
contentOwner: Rick Brough
feature: Configuration,Viewer Presets,Image Presets,Dynamic Media
role: Admin,User
exl-id: 83b70b17-7ee3-41cb-be90-c92ca161660e
source-git-commit: 8a8f3d7b17d79791a3ebf6b583ffcccfcf214470
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 60%

---

# Einrichten von Dynamic Media {#setting-up-dynamic-media}

{{work-with-dynamic-media}}

Mithilfe von [Dynamic Media](https://business.adobe.com/de/products/experience-manager/assets/dynamic-media.html) können Sie Assets verwalten, indem Sie umfassende visuelle Merchandising- und Marketing-Assets bei Bedarf übermitteln, und zwar automatisch skaliert für die Verwendung im Web, auf Mobilgeräten und in Social Media. Anhand eines Sets von Assets aus Primärquellen können Sie mit Dynamic Media mehrere Varianten ansprechender Inhalte in Echtzeit über das globale, skalierbare und leistungsoptimierte Netzwerk generieren und bereitstellen.

<!-- OBSOLETE UNTIL THE INTEGRATING SCENE7 TOPIC GETS A MAJOR UPDATE

>[!NOTE]
>
>This documentation describes Dynamic Media capabilites, which are integrated directly into [!DNL Experience Manager]. If you are using Dynamic Media Classic (previously called Scene7) integrated into [!DNL Experience Manager], see [Dynamic Media Classic integration documentation](/help/sites-cloud/administering/integrating-scene7.md).
>
>See [Dual Use Scenario](/help/sites-cloud/administering/integrating-scene7.md#dual-use-scenario) for times when you may want to use [!DNL Experience Manager] integrated with Dynamic Media Classic along with Dynamic Media.

-->

Wenn Sie Dynamic Media verwalten, sind für Sie die folgenden Themen interessant:

* [Konfigurieren von Dynamic Media](config-dm.md)
* [Verwalten von Bildvorgaben](managing-image-presets.md)
* [Verwalten von Viewer-Vorgaben](managing-viewer-presets.md)
* [Fehlerbehebung bei Dynamic Media](troubleshoot-dm.md)

Weitere Informationen finden Sie in den folgenden Themen:

* [Videokodierung und Videoprofile](video-profiles.md)
* [Bildprofile](image-profiles.md)

>[!NOTE]
>
>**Beachten Sie Folgendes, wenn Sie ein Upgrade durchführen:**
>
>* Sobald Sie Adobe [!DNL Experience Manager] eingerichtet haben und verwenden, ist Dynamic Media für jedes Asset, das Sie hochladen, automatisch aktiviert (sofern nicht ausdrücklich vom Systemadministrator deaktiviert). Wenn Sie sich in einer aktualisierten Instanz von [!DNL Experience Manager] befinden und Dynamic Media noch nicht verwendet haben, müssen Sie die Assets wahrscheinlich erneut verarbeiten, um Dynamic Media für sie verwenden zu können. Siehe [Neuverarbeitung von Assets in einem Ordner](/help/assets/dynamic-media/about-image-video-profiles.md#reprocessing-assets).


## Einmalige DNS-Aktualisierung erforderlich für die Erneuerung von Dynamic Media-Zertifikaten {#dns-update-dynamic-media-certificate-renewals}

Wenn Ihre Domain einen CAA-DNS-Eintrag (Certification Authority Authorization) verwendet, müssen Sie DigiCert autorisieren, die kontinuierliche Erneuerung von TLS/SSL-Zertifikaten zuzulassen, die von Dynamic Media-Hostnamen verwendet werden.

Fügen Sie den folgenden CAA-Eintrag am Stamm (apex) Ihrer Domain hinzu:

```
<yourdomain> CAA 0 issue "digicert.com"
```

Dies ist eine einmalige Veränderung.

Sie können mithilfe Ihrer DNS-Provider-Tools oder eines „CAA Lookup Utility“ überprüfen[ ob ein CAA-Eintrag vorhanden ](https://caatest.co.uk/).

Wenn ein CAA-Eintrag vorhanden und DigiCert nicht autorisiert ist, schlägt die Zertifikatsverlängerung fehl, wenn das aktuelle Zertifikat abläuft, was zu Ausfallzeiten bei der Bild- und Videobereitstellung führen kann. Wenn für Ihre Domain kein CAA-Eintrag vorhanden ist, ist keine Aktion erforderlich.
