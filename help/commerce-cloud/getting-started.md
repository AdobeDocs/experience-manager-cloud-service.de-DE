---
title: Erste Schritte mit AEM Commerce als Cloud Service
description: Erfahren Sie, wie Sie ein Commerce-aktiviertes AEM auf einem laufenden AEM als Cloud-Dienst-Umgebung bereitstellen. Verwenden Sie Funktionen von Adobe Cloud Manager und eine CI/CD-Pipeline, um den Venia-Referenzspeicher auf einer laufenden Umgebung zu erstellen.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
translation-type: tm+mt
source-git-commit: 7a26596b00f276404934e467490ff79d08b0e1d0
workflow-type: tm+mt
source-wordcount: '677'
ht-degree: 6%

---


# Erste Schritte mit AEM Commerce als Cloud Service {#start}

Um mit AEM Commerce als Cloud Service beginnen zu können, muss Ihr Experience Manager Cloud Service über das Commerce Integration Framework (CIF) Add-On verfügen. Das CIF-Add-on ist ein Zusatzmodul über [AEM Sites als Cloud Service](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/sites/home.html).

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

## Einstieg {#onboarding}

Das Einboarding für AEM Commerce als Cloud Service erfolgt in zwei Schritten:

1. AEM Commerce als Cloud Service aktivieren und das CIF-Add-on bereitstellen
2. Verbinden AEM Commerce als Cloud Service mit Ihrer Magento-Umgebung

Der erste Schritt erfolgt durch Adobe. Sie müssen Informationen wie die IMS-Organisation, die GraphQL-Endpunkt-URL Ihrer Magento-Umgebung usw. angeben. als Teil des Bereitstellungsprozesses. Weitere Informationen zu Preisen und Bereitstellung erhalten Sie von Ihrem Vertriebsmitarbeiter.

Nachdem Sie das CIF-Add-on bereitgestellt haben, wird es auf alle vorhandenen Cloud Manager-Programm angewendet. Wenn Sie kein Cloud Manager-Programm haben, müssen Sie ein neues erstellen. Weitere Informationen finden Sie unter [Programm](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/getting-started/setting-up-program.html) einrichten.

Der zweite Schritt ist die Selbstbedienung für jede AEM als Cloud Service-Umgebung. Es gibt einige zusätzliche Konfigurationen, die Sie nach der anfänglichen Bereitstellung des CIF-Add-ons vornehmen müssen.

## AEM Commerce mit Magento {#magento} verbinden

Um das CIF-Add-on und die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) mit Ihrer Magento-Umgebung zu verbinden, müssen Sie die Magento GraphQL-Endpunkt-URL über eine Cloud Manager-Umgebung-Variable angeben. Der Variablenname ist `COMMERCE_ENDPOINT`. Eine sichere Verbindung über HTTPS muss konfiguriert werden.
Für jede AEM kann eine andere Magento GraphQL-Endpunkt-URL als Cloud Service-Umgebung verwendet werden. Auf diese Weise können AEM Staging-Umgebung mit Magento-Staging-Systemen und AEM Produktions-Umgebung mit einem Magento-Produktionssystem verbunden werden. Dieser Magento GraphQL-Endpunkt muss öffentlich verfügbar sein, private VPN- oder Ortsverbindungen werden nicht unterstützt.

Gehen Sie wie folgt vor, um AEM Commerce mit Magento zu verbinden:

1. Adobe I/O CLI mit dem Cloud Manager-Plugin

   Überprüfen Sie in der [Adobe Cloud Manager-Dokumentation ](https://docs.adobe.com/content/help/en/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html), wie Sie die [Adobe I/O CLI](https://github.com/adobe/aio-cli) mit dem [Cloud Manager CLI-Plugin](https://github.com/adobe/aio-cli-plugin-cloudmanager) herunterladen, einrichten und verwenden.

2. Authentifizieren Sie die CLI mit dem AEM als Cloud Service-Programm

3. Variable `COMMERCE_ENDPOINT` in Cloud Manager festlegen

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Weitere Informationen finden Sie unter [CLI-Dokumente](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   Die Magento GraphQL-Endpunkt-URL muss auf den GraphQl-Dienst von Magento verweisen und eine sichere HTTPS-Verbindung verwenden. Beispiel: `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>Sie können alle Cloud Manager-Variablen mithilfe des folgenden Befehls zur Dublette-Prüfung Liste haben: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

>[!NOTE]
>
>Alternativ können Sie auch die [Cloud Manager-API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) verwenden, um die Cloud Manager-Variablen zu konfigurieren.

Damit können Sie AEM Commerce als Cloud Service verwenden und Ihr Projekt über Cloud Manager bereitstellen.

## Gestufte Katalogfunktionen aktivieren (optional) {#staging}

>[!NOTE]
>
>Diese Funktion ist nur in Magento Enterprise Edition oder Magento Cloud verfügbar.

1. Melden Sie sich bei Magento an und erstellen Sie ein Integrationstoken. Weitere Informationen finden Sie unter [Token-basierte Authentifizierung](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens). Stellen Sie sicher, dass das Integrationstoken nur *Zugriff auf*-Ressourcen hat. `Content -> Staging` Kopieren Sie den Wert `Access Token`.

1. Legen Sie die geheime Variable `COMMERCE_AUTH_HEADER` in Cloud Manager fest:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization Bearer: <Access Token>"
   ```

   Informationen zum Konfigurieren der Adobe I/O CLI für Cloud Manager finden Sie unter [Verbinden AEM Commerce mit Magento](#magento).

## Drittanbieter-Commerce-Integrationen {#integrations}

Bei Commerce-Integrationen von Drittanbietern ist eine [API-Zuordnungsebene](architecture/third-party.md) erforderlich, um AEM Commerce als Cloud Service und CIF-Kernkomponenten mit Ihrem Commerce-System zu verbinden. Diese API-Zuordnungsebene wird normalerweise auf Adobe I/O Runtime bereitgestellt. Wenden Sie sich an Ihren Vertriebsmitarbeiter, um verfügbare Integrationen und Zugriff auf Adobe I/O Runtime zu erhalten.
