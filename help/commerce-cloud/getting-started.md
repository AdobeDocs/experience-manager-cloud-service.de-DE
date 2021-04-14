---
title: Erste Schritte mit AEM Commerce as a Cloud Service
description: Erfahren Sie, wie Sie ein für Commerce aktiviertes AEM-Projekt in einer laufenden AEM as a Cloud Service -Umgebung bereitstellen. Verwenden Sie Funktionen von Adobe Cloud Manager und eine CI/CD-Pipeline, um die Venia-Referenz-Storefront in einer laufenden Umgebung zu erstellen.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: cloud-service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
translation-type: tm+mt
source-git-commit: e34592d24c8f6c17e6959db1d5c513feaf6381c8
workflow-type: tm+mt
source-wordcount: '766'
ht-degree: 64%

---

# Erste Schritte mit AEM Commerce as a Cloud Service {#start}

Damit Sie mit AEM Commerce as a Cloud Service loslegen können, muss Ihr Experience Manager Cloud Service über das Add-on Commerce Integration Framework (CIF) verfügen. Das CIF-Add-on ist ein Zusatzmodul für [AEM Sites as a Cloud Service](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/sites/home.translate.html).

## Einstieg {#onboarding}

Das Onboarding für AEM Commerce as a Cloud Service erfolgt in zwei Schritten:

1. AEM Commerce as a Cloud Service aktivieren und das CIF-Add-on bereitstellen
2. Verbinden AEM Commerce als Cloud Service mit Ihrer Commerce-Lösung

Der erste Einstieg erfolgt durch Adobe. Weitere Informationen zu Preisen und Bereitstellung erhalten Sie von Ihrem Vertriebsmitarbeiter.

Nachdem Sie das CIF-Add-on bereitgestellt haben, wird es auf alle vorhandenen Cloud Manager-Programme angewendet. Wenn Sie kein Cloud Manager-Programm haben, müssen Sie ein neues erstellen. Weitere Informationen finden Sie unter [Ihr Programm einrichten](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

Der zweite Schritt erfolgt per Self-Service für die einzelnen AEM as a Cloud Service-Umgebungen. Es gibt einige zusätzliche Konfigurationen, die Sie nach der anfänglichen Bereitstellung des CIF-Add-ons vornehmen müssen.

## AEM mit einer Commerce-Lösung {#magento} verbinden

Um das CIF-Add-on und die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) mit einer Commerce-Lösung zu verbinden, müssen Sie die GraphQL-Endpunkt-URL über eine Cloud Manager-Umgebung-Variable angeben. Der Variablenname lautet `COMMERCE_ENDPOINT`. Es muss eine sichere Verbindung über HTTPS konfiguriert werden.
Für jede AEM kann eine andere GraphQL-Endpunkt-URL als Cloud Service-Umgebung verwendet werden. Auf diese Weise können Projekte AEM Staging-Umgebung mit kommerziellen Staging-Systemen und AEM Produktions-Umgebung mit einem kommerziellen Produktionssystem verbinden. Dieser GraphQL-Endpunkt muss öffentlich verfügbar sein, private VPN- oder lokale Verbindungen werden nicht unterstützt. Optional kann ein Authentifizierungsheader bereitgestellt werden, um zusätzliche CIF-Funktionen zu verwenden, für die eine Authentifizierung erforderlich ist.

Es gibt zwei Optionen zum Konfigurieren des Endpunkts:

### 1) Über die Benutzeroberfläche von Cloud Manager (Standard)

Dies kann über ein Dialogfeld auf der Seite &quot;Umgebung-Details&quot;erfolgen. Wenn Sie diese Seite für ein Commerce-aktiviertes Programm anzeigen, wird eine Schaltfläche angezeigt, wenn der Endpunkt derzeit nicht konfiguriert ist:

![Abzeichen für „Umweltfreundlich“ – endgültige Implementierung](/help/commerce-cloud/assets/commerce-cmui.png)

Durch Klicken auf diese Schaltfläche wird ein Dialogfeld geöffnet:

![Abzeichen für „Umweltfreundlich“ – endgültige Implementierung](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Nachdem der Endpunkt (und optional das Token) festgelegt wurde, wird der Endpunkt auf der Detailseite angezeigt. Durch Klicken auf das Symbol Bearbeiten wird dasselbe Dialogfeld geöffnet, in dem der Endpunkt bei Bedarf geändert werden kann.

![Abzeichen für „Umweltfreundlich“ – endgültige Implementierung](/help/commerce-cloud/assets/commerce-cmui-done.png)

### 2) Über Adobe I/O CLI

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Gehen Sie wie folgt vor, um AEM über die Adobe I/O-CLI mit einer Commerce-Lösung zu verbinden:

1. Adobe I/O-CLI mit dem Cloud Manager-Plug-in abrufen

   Konsultieren Sie die [Adobe Cloud Manager-Dokumentation](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html), um Informationen zum Herunterladen, Einrichten und Verwenden der [Adobe I/O-CLI](https://github.com/adobe/aio-cli) mit dem [Cloud Manager-CLI-Plug-in](https://github.com/adobe/aio-cli-plugin-cloudmanager) zu erhalten.

2. Authentifizieren Sie die Adobe I/O-CLI mit dem AEM als Cloud Service-Programm

3. `COMMERCE_ENDPOINT`-Variable in Cloud Manager festlegen

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Weitere Informationen finden Sie in den [CLI-Dokumentationen](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   Die Commerce GraphQL-Endpunkt-URL muss auf den GraphQl-Dienst des Commerce verweisen und eine sichere HTTPS-Verbindung verwenden. Beispiel: `https://demo.magentosite.cloud/graphql`.

>[!TIP]
>
>Sie können alle Cloud Manager-Variablen mithilfe des folgenden Befehls zur Überprüfung auflisten: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

Danach können Sie AEM Commerce as a Cloud Service verwenden und Ihr Projekt über Cloud Manager bereitstellen.

## Aktivieren Sie Funktionen, für die eine Authentifizierung erforderlich ist (Optional) {#staging}

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
