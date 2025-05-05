---
title: AEM as a Cloud Service Sicherheitsüberlegungen
description: Erfahren Sie mehr über wichtige Sicherheitsüberlegungen bei der Verwendung von AEM as a Cloud Service.
hidefromtoc: true
hide: true
exl-id: d2dfde05-ce02-478e-8697-b939fb8740c3
feature: Security
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 100%

---

# AEM as a Cloud Service Sicherheitsüberlegungen {#security-considerations}

## AEM Trust Store {#aem-trust-store}

Um asymmetrische, kryptografische Vorgänge zu unterstützen, speichert AEM Zertifikate innerhalb des Inhalts-Repositorys in einem globalen Trust Store. Die Inhalte sind öffentlich und stehen standardmäßig allen Publisher-Instanzen anonym zur Verfügung.

### Eigenschaften des Trust Store {#truststore-characteristics}

* Der Trust Store befindet sich unter `/etc/truststore` und besteht aus einer Java™-Keystore-Datei, dem Keystore-Passwort und den Repository-Metadaten. Sowohl das Passwort als auch der Keystore sind aus technischen Gründen verschlüsselt, auch wenn die enthaltenen Zertifikate standardmäßig über die API für alle zugänglich sind
* Standardmäßig werden die Zertifikate nur für HTTPS- und SAML-Unterstützung verwendet und der Speicher muss zuerst manuell erstellt werden
* Kunden oder Kundinnen können sie in ihrem eigenen Code über die [Keystore-API](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/keystore/KeyStoreService.html#getTrustStore-org.apache.sling.api.resource.ResourceResolver-) verwenden
* Der Trust-Store kann über die Benutzeroberfläche unter **Tools** – **Sicherheit** – **Trust Store** oder durch Zugriff auf *`https://serveraddress:serverport/libs/granite/security/content/truststore.html`* verwaltet werden, wie unten dargestellt:

  ![Trust Store-Verwaltung](/help/security/assets/global-trust-store-modified.png)

* Der Zugriff auf den Trust Store kann je nach Anwendungsfall durch die Zugriffskontrolle auf das Repository weiter eingeschränkt werden.

>[!NOTE]
>
>Adobe empfiehlt, die standardmäßigen Zugriffssteuerungen für den Trust Store zu verwenden, was bedeutet, dass er öffentlich zugänglich bleibt. Die sicherste Konfiguration ist die Verwendung einer Richtlinie, die `jcr:all` für alle verweigert.

<!--
Commenting out section for now as requested by Lars

## Anonymous Permission Hardening Package {#anonymous-permission-hardening-package}

For more information on the Anonymous Hardening Package, see [Security Checklist](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/security-checklist.html?lang=de#anonymous-permission-hardening-package).
-->
