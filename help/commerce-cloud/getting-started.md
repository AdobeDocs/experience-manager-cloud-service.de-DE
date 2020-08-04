---
title: Erste Schritte mit AEM Commerce als Cloud Service
description: Erste Schritte mit AEM Commerce als Cloud Service
translation-type: tm+mt
source-git-commit: 1fcdfa60c134491c781906e4a757a3a10399bde1
workflow-type: tm+mt
source-wordcount: '572'
ht-degree: 6%

---


# Erste Schritte mit AEM Commerce als Cloud Service {#start}

Um mit AEM Commerce als Cloud Service beginnen zu können, muss Ihr Experience Manager Cloud Service über das Commerce Integration Framework (CIF) Add-On verfügen. Das CIF-Add-on ist ein Zusatzmodul, das als Cloud Service über den [AEM Sites](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/sites/home.translate.html)steht.

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

## Einstieg {#onboarding}

Das Einboarding für AEM Commerce als Cloud Service erfolgt in zwei Schritten:

1. AEM Commerce als Cloud Service aktivieren und das CIF-Add-on bereitstellen
2. Verbinden AEM Commerce als Cloud Service mit Ihrer Magento-Umgebung

Der erste Schritt erfolgt durch Adobe. Sie müssen Informationen wie die IMS-Organisation, die GraphQL-Endpunkt-URL Ihrer Magento-Umgebung usw. angeben. als Teil des Bereitstellungsprozesses. Weitere Informationen zu Preisen und Bereitstellung erhalten Sie von Ihrem Vertriebsmitarbeiter.

Nachdem Sie das CIF-Add-on bereitgestellt haben, wird es auf alle vorhandenen Cloud Manager-Programm angewendet. Wenn Sie kein Cloud Manager-Programm haben, müssen Sie ein neues erstellen. Weitere Informationen finden Sie unter [Einrichten des Programms](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

Der zweite Schritt ist die Selbstbedienung für jede AEM als Cloud Service-Umgebung. Es gibt einige zusätzliche Konfigurationen, die Sie nach der anfänglichen Bereitstellung des CIF-Add-ons vornehmen müssen.

## AEM Handel mit Magento verbinden {#magento}

Um das CIF-Add-on und die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) mit Ihrer Magento-Umgebung zu verbinden, müssen Sie die Magento GraphQL-Endpunkt-URL über eine Cloud Manager-Umgebung-Variable angeben. Der Variablenname lautet `COMMERCE_ENDPOINT`. Eine sichere Verbindung über HTTPS muss konfiguriert werden.
Für jede AEM kann eine andere Magento GraphQL-Endpunkt-URL als Cloud Service-Umgebung verwendet werden. Auf diese Weise können AEM Staging-Umgebung mit Magento-Staging-Systemen und AEM Produktions-Umgebung mit einem Magento-Produktionssystem verbunden werden. Dieser Magento GraphQL-Endpunkt muss öffentlich verfügbar sein, private VPN- oder Ortsverbindungen werden nicht unterstützt.

Gehen Sie wie folgt vor, um AEM Commerce mit Magento zu verbinden:

1. Adobe-I/O-CLI mit dem Cloud Manager-Plugin abrufen

   Informationen zum Herunterladen, Einrichten und Verwenden der [Adobe-E/A-CLI](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html) - [mit dem CLI-Plug-In](https://github.com/adobe/aio-cli) für [Cloud Manager finden Sie in der Dokumentation](https://github.com/adobe/aio-cli-plugin-cloudmanager)zu Adobe Cloud Manager.

2. Authentifizieren Sie die CLI mit dem AEM als Cloud Service-Programm

3. Festlegen der `COMMERCE_ENDPOINT` Variablen in Cloud Manager

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Weitere Informationen finden Sie in den [CLI-Dokumenten](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid) .

   Die Magento GraphQL-Endpunkt-URL muss auf den GraphQl-Dienst von Magento verweisen und eine sichere HTTPS-Verbindung verwenden. Beispiel: `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>Sie können alle Cloud Manager-Variablen mithilfe des folgenden Befehls zur Dublette-Prüfung Liste haben: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

>[!NHinweis]
>
>Alternativ können Sie auch die [Cloud Manager-API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) verwenden, um die Cloud Manager-Variablen zu konfigurieren.

Damit können Sie AEM Commerce als Cloud Service verwenden und Ihr Projekt über Cloud Manager bereitstellen.

## 3rd party commerce integrations {#integrations}

Bei Commerce-Integrationen von Drittanbietern ist eine [API-Zuordnungsebene](architecture/third-party.md) erforderlich, um AEM Commerce als Cloud Service und CIF-Kernkomponenten mit Ihrem Commerce-System zu verbinden. Diese API-Zuordnungsebene wird normalerweise auf Adobe I/O Runtime bereitgestellt. Wenden Sie sich an Ihren Vertriebsmitarbeiter, um verfügbare Integrationen und Zugriff auf Adobe I/O Runtime zu erhalten.
