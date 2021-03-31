---
title: Erste Schritte mit AEM Commerce as a Cloud Service
description: Erfahren Sie, wie Sie ein für Commerce aktiviertes AEM-Projekt in einer laufenden AEM as a Cloud Service -Umgebung bereitstellen. Verwenden Sie Funktionen von Adobe Cloud Manager und eine CI/CD-Pipeline, um die Venia-Referenz-Storefront in einer laufenden Umgebung zu erstellen.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
translation-type: tm+mt
source-git-commit: d1727601bb5d70bea9920aa1d680284fb3d25bf0
workflow-type: tm+mt
source-wordcount: '657'
ht-degree: 98%

---


# Erste Schritte mit AEM Commerce as a Cloud Service {#start}

Damit Sie mit AEM Commerce as a Cloud Service loslegen können, muss Ihr Experience Manager Cloud Service über das Add-on Commerce Integration Framework (CIF) verfügen. Das CIF-Add-on ist ein Zusatzmodul für [AEM Sites as a Cloud Service](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/sites/home.translate.html).

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

## Einstieg {#onboarding}

Das Onboarding für AEM Commerce as a Cloud Service erfolgt in zwei Schritten:

1. AEM Commerce as a Cloud Service aktivieren und das CIF-Add-on bereitstellen
2. AEM Commerce as a Cloud Service mit Ihrer Magento-Umgebung verbinden

Der erste Einstieg erfolgt durch Adobe. Weitere Informationen zu Preisen und Bereitstellung erhalten Sie von Ihrem Vertriebsmitarbeiter.

Nachdem Sie das CIF-Add-on bereitgestellt haben, wird es auf alle vorhandenen Cloud Manager-Programme angewendet. Wenn Sie kein Cloud Manager-Programm haben, müssen Sie ein neues erstellen. Weitere Informationen finden Sie unter [Ihr Programm einrichten](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

Der zweite Schritt erfolgt per Self-Service für die einzelnen AEM as a Cloud Service-Umgebungen. Es gibt einige zusätzliche Konfigurationen, die Sie nach der anfänglichen Bereitstellung des CIF-Add-ons vornehmen müssen.

## Verbinden von AEM Commerce mit Magento {#magento}

Um das CIF-Add-on und die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) mit Ihrer Magento-Umgebung zu verbinden, müssen Sie über eine Cloud Manager-Umgebungsvariable die Magento-GraphQL-Endpunkt-URL angeben. Der Variablenname lautet `COMMERCE_ENDPOINT`. Es muss eine sichere Verbindung über HTTPS konfiguriert werden.
Für jede AEM as a Cloud Service-Umgebung kann eine andere Magento-GraphQL-Endpunkt-URL verwendet werden. Auf diese Weise können Projekte AEM-Staging-Umgebungen die über Magento-Staging-Systeme und eine AEM-Produktionsumgebung verfügen, mit einem Magento-Produktionssystem verbinden. Der entsprechende Magento-GraphQL-Endpunkt muss öffentlich verfügbar sein; private VPN- oder lokale Verbindungen werden nicht unterstützt.

Gehen Sie wie folgt vor, um AEM Commerce mit Magento zu verbinden:

1. Adobe I/O-CLI mit dem Cloud Manager-Plug-in abrufen

   Konsultieren Sie die [Adobe Cloud Manager-Dokumentation](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html), um Informationen zum Herunterladen, Einrichten und Verwenden der [Adobe I/O-CLI](https://github.com/adobe/aio-cli) mit dem [Cloud Manager-CLI-Plug-in](https://github.com/adobe/aio-cli-plugin-cloudmanager) zu erhalten.

2. CLI mit AEM as a Cloud Service authentifizieren

3. `COMMERCE_ENDPOINT`-Variable in Cloud Manager festlegen

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Weitere Informationen finden Sie in den [CLI-Dokumentationen](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   Die Magento-GraphQL-Endpunkt-URL muss auf den GraphQl-Service von Magento verweisen und eine sichere HTTPS-Verbindung nutzen. Beispiel: `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>Sie können alle Cloud Manager-Variablen mithilfe des folgenden Befehls zur Überprüfung auflisten: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

>[!NOTE]
>
>Alternativ können Sie auch die [Cloud Manager-API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html) zum Konfigurieren der Cloud Manager-Variablen verwenden.

Danach können Sie AEM Commerce as a Cloud Service verwenden und Ihr Projekt über Cloud Manager bereitstellen.

## Aktivieren stufenweiser Katalogfunktionen (optional) {#staging}

>[!NOTE]
>
>Diese Funktion ist nur in Magento Enterprise Edition oder Magento Cloud verfügbar.

1. Melden Sie sich bei Magento an und erstellen Sie ein Integrations-Token. Weitere Informationen finden Sie unter [Token-basierte Authentifizierung](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens). Stellen Sie sicher, dass das Integrations-Token *nur* auf `Content -> Staging`-Ressourcen zugreifen kann. Kopieren Sie den Wert `Access Token`.

1. Legen Sie die `COMMERCE_AUTH_HEADER`-Variable in Cloud Manager fest:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

   Informationen zum Konfigurieren der Adobe I/O-CLI für Cloud Manager finden Sie unter [Verbinden von AEM Commerce mit Magento](#magento).

## Integrationen mit Commerce-Systemen von Drittanbietern {#integrations}

Bei Integrationen mit Commerce-Systemen von Drittanbietern ist eine [API-Zuordnungsebene](architecture/third-party.md) erforderlich, um AEM Commerce as a Cloud Service und CIF-Kernkomponenten mit Ihrem Commerce-System zu verbinden. Diese API-Zuordnungsebene wird normalerweise in Adobe I/O Runtime bereitgestellt. Wenden Sie sich an Ihren Vertriebsmitarbeiter, um Informationen zu verfügbaren Integrationen und Zugriff auf Adobe I/O Runtime zu erhalten.
