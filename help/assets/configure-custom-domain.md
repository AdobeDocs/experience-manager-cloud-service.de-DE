---
title: Konfigurieren einer benutzerdefinierten Domain für die Bereitstellungsebene
description: Erfahren Sie, wie Sie in Adobe Cloud Manager eine benutzerdefinierte Domain für die Bereitstellungsebene konfigurieren.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: 80a32672ec018274b0410abfa14fdd761fdb5aba
workflow-type: tm+mt
source-wordcount: '362'
ht-degree: 49%

---


# Konfigurieren einer benutzerdefinierten Domain für die Bereitstellungsebene{#configure-custom-domain}

In Adobe Cloud Manager können Sie Ihre Website durch das Hinzufügen einer benutzerdefinierten Domain hervorheben. AEM as a Cloud Service verfügt zwar über eine Standard-Domain, Sie können sie aber nach Bedarf anpassen.

>[!NOTE]
>
>Kunden mit Dynamic Media Prime- oder Dynamic Media Ultimate-Lizenzen müssen die in Cloud Manager verfügbare benutzerdefinierte Self-Service-Domain-Konfiguration verwenden.Weitere Informationen finden [ in der Dokumentation zu Dynamic Media Prime ](/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md#configure-custom-domain-in-delivery-tier) Ultimate .
>
>Kunden, die ältere Dynamic Media-Setups verwenden, bei denen Dynamic Media mit OpenAPI manuell aktiviert ist, sollten diese Dokumentation befolgen. Für diese Setups wird die benutzerdefinierte Domain-Zuordnung über eine Adobe-Support-Anfrage abgeschlossen.

## Vorbereiten auf die ersten Schritte

Stellen Sie sicher, dass Sie die folgenden Anforderungen erfüllen, bevor Sie den Konfigurationsprozess starten:

* Zugriff auf Cloud Manager
* Dynamic Media wurde bereits mit OpenAPI in Ihrer Umgebung über ein Support-Ticket aktiviert
* EV- oder OV-SSL-Zertifikat für die in der Bereitstellungsebene verwendete Domain. Weitere [ finden Sie unter „Einführung ](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/introduction-to-ssl-certificates) SSL-Zertifikate“

## Konfigurieren einer benutzerdefinierten Domain in der Bereitstellungsebene mithilfe von Cloud Manager

Führen Sie die folgenden Schritte in Cloud Manager aus:

1. [Hinzufügen eines vom Kunden verwalteten SSL-Zertifikats](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-ssl-certificates/add-ssl-certificate#add-customer-managed-ssl-cert)

2. [Hinzufügen eines benutzerdefinierten Domain-Namens](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/custom-domain-names/add-custom-domain-name#adding-cdn-settings)

Erstellen Sie nach Abschluss der oben genannten Schritte ein Adobe-Support-Ticket für die benutzerdefinierte Domain-Zuordnung. Adobe führt die Domain-Zuordnung im Rahmen des Support-Prozesses durch.

**Siehe auch**

* [Assets übersetzen](/help/assets/translate-assets.md)
* [Assets-HTTP-API](/help/assets/mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](/help/assets/file-format-support.md)
* [Suchen von Assets](/help/assets/search-assets.md)
* [Connected Assets](/help/assets/use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](/help/assets/asset-reports.md)
* [Metadatenschemata](/help/assets/metadata-schemas.md)
* [Herunterladen von Assets](/help/assets/download-assets-from-aem.md)
* [Verwalten von Metadaten](/help/assets/manage-metadata.md)
* [Verwalten von Dynamic Media-Vorlagen](/help/assets/dynamic-media/manage-dynamic-media-templates.md)
* [Verwalten von Berichten](/help/assets/manage-reports-assets-view.md)
* [Suchfacetten](/help/assets/search-facets.md)
* [Verwalten von Sammlungen](/help/assets/manage-collections.md)
* [Massenimport von Metadaten](/help/assets/metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

