---
title: Überlegungen zur as a Cloud Service Sicherheit AEM
description: Wichtige Sicherheitsüberlegungen bei der Verwendung von AEM as a Cloud Service
hidefromtoc: true
hide: true
exl-id: d2dfde05-ce02-478e-8697-b939fb8740c3
source-git-commit: f7525b6b37e486a53791c2331dc6000e5248f8af
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 0%

---

# Überlegungen zur as a Cloud Service Sicherheit AEM {#security-considerations}

## AEM Trust Store {#aem-trust-store}

Um asymmetrische kryptografische Vorgänge zu unterstützen, speichert AEM Zertifikate im Inhalts-Repository in einem globalen Trust Store. Die Inhalte sind öffentlich und stehen standardmäßig allen Publisherinstanzen anonym zur Verfügung.

### Eigenschaften des Trust Store {#truststore-characteristics}

* Der Trust Store befindet sich unten. `/etc/truststore` und besteht aus einer Java-Keystore-Datei, dem Keystore-Kennwort und den Repository-Metadaten. Beachten Sie, dass sowohl das Kennwort als auch der Keystore selbst aus technischen Gründen verschlüsselt sind, auch wenn die enthaltenen Zertifikate standardmäßig über die API für alle zugänglich sind.
* Standardmäßig werden die Zertifikate nur für HTTPS- und SAML-Unterstützung verwendet und der Speicher muss zuerst manuell erstellt werden
* Kunden können sie in ihrem eigenen Code über [Keystore-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/keystore/KeyStoreService.html#getTrustStore-org.apache.sling.api.resource.ResourceResolver-)
* Der TrustStore kann über die Benutzeroberfläche unter **Instrumente** - **Sicherheit** - **Trust Store** oder durch Zugriff auf *`https://serveraddress:serverport/libs/granite/security/content/truststore.html`*, wie unten dargestellt:

  ![Trust Store-Verwaltung](/help/security/assets/global-trust-store-modified.png)

* Der Zugriff auf den Trust Store kann je nach Anwendungsfall durch die Zugriffskontrolle auf das Repository weiter eingeschränkt werden.

>[!NOTE]
>
>Adobe empfiehlt, die standardmäßigen Zugriffssteuerungen für den Trust Store zu verwenden, was bedeutet, dass er öffentlich zugänglich bleibt. Für die sicherste Konfiguration können Sie die Richtlinie &quot;jcr:all verweigern&quot;für alle verwenden.

<!--
Commenting out section for now as requested by Lars

## Anonymous Permission Hardening Package {#anonymous-permission-hardening-package}

For more information on the Anonymous Hardening Package, please see the [Security Checklist](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html#anonymous-permission-hardening-package).
-->
