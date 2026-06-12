---
title: Konfigurieren einer benutzerdefinierten Domain für die Bereitstellungsebene
description: Erfahren Sie, wie Sie in Adobe Cloud Manager eine benutzerdefinierte Domain für die Bereitstellungsebene konfigurieren.
exl-id: cc71c8c5-cf42-4092-b0e0-646a2ed0ee54
source-git-commit: b24faf23435948a8f122223bf38227a0936bbeb5
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 46%

---


# Konfigurieren einer benutzerdefinierten Domain für die Bereitstellungsebene{#configure-custom-domain}

In Adobe Cloud Manager können Sie Ihre Website durch das Hinzufügen einer benutzerdefinierten Domain hervorheben. AEM as a Cloud Service verfügt zwar über eine Standard-Domain, Sie können sie aber nach Bedarf anpassen.

>[!NOTE]
>
>Kunden mit Dynamic Media Prime- oder Dynamic Media Ultimate-Lizenzen müssen die in Cloud Manager verfügbare benutzerdefinierte Self-Service-Domain-Konfiguration verwenden.
> Informationen finden [ in der Dokumentation zu Dynamic Prime und Ultimate ](/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md#configure-custom-domain-in-delivery-tier).
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