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
source-git-commit: 08e258d4e9cd67de3da2aa57c058036bd104472d
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 34%

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

Die Variable &quot;Umgebung&quot;wird an zwei Stellen verwendet:

- GraphQL-Aufrufe von AEM zum Commerce-Backend, über einen gemeinsamen, freigegebenen GraphQl-Client, verwendet von den AEM CIF Core Components und Kundenprojektkomponenten.
- Richten Sie auf jeder AEM Umgebung, auf der die Variable eingestellt ist, eine GraphQL-Proxy-URL ein. `/api/graphql` Dies wird von den AEM Commerce-Authoring-Werkzeugen (CIF-Add-on) und CIF clientseitigen Komponenten verwendet.

Für jede AEM kann eine andere GraphQL-Endpunkt-URL als Cloud Service-Umgebung verwendet werden. Auf diese Weise können Projekte AEM Staging-Umgebung mit kommerziellen Staging-Systemen und AEM Produktions-Umgebung mit einem kommerziellen Produktionssystem verbinden. Dieser GraphQL-Endpunkt muss öffentlich verfügbar sein, private VPN- oder lokale Verbindungen werden nicht unterstützt. Optional kann ein Authentifizierungsheader bereitgestellt werden, um zusätzliche CIF-Funktionen zu verwenden, für die eine Authentifizierung erforderlich ist.

Optional und nur für Adobe Commerce Enterprise/Cloud unterstützt das CIF-Add-on die Verwendung von Stage-Katalogdaten für AEM Autoren. Hierfür muss ein Autorisierungstoken konfiguriert werden. Das konfigurierte Autorisierungstoken ist aus Sicherheitsgründen nur in AEM Autoreninstanzen verfügbar und wird verwendet. AEM Veröffentlichungsinstanzen können keine gestaffelten Daten anzeigen.

Es gibt zwei Optionen zum Konfigurieren des Endpunkts:

### Über die Benutzeroberfläche von Cloud Manager (Standard) {#cm-ui}

Dies kann über ein Dialogfeld auf der Seite &quot;Umgebung-Details&quot;erfolgen. Wenn Sie diese Seite für ein Commerce-aktiviertes Programm anzeigen, wird eine Schaltfläche angezeigt, wenn der Endpunkt derzeit nicht konfiguriert ist:

![CM-Umweltinformationen](/help/commerce-cloud/assets/commerce-cmui.png)

Durch Klicken auf diese Schaltfläche wird ein Dialogfeld geöffnet:

![CM Commerce-Endpunkt](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Nachdem der Endpunkt (optional ein Authentifizierungstoken für die Unterstützung von gestaffelten Katalogen) festgelegt wurde, wird der Endpunkt auf der Detailseite angezeigt. Durch Klicken auf das Symbol Bearbeiten wird dasselbe Dialogfeld geöffnet, in dem der Endpunkt bei Bedarf geändert werden kann.

![CM-Umweltinformationen](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Über Adobe I/O CLI {#adobe-cli}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Gehen Sie wie folgt vor, um AEM über die Adobe I/O-CLI mit einer Commerce-Lösung zu verbinden:

1. Adobe I/O-CLI mit dem Cloud Manager-Plug-in abrufen

   Überprüfen Sie in der [Adobe Cloud Manager-Dokumentation](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html), wie Sie die [Adobe I/O-CLI](https://github.com/adobe/aio-cli) mit dem [Cloud Manager-CLI-Plugin](https://github.com/adobe/aio-cli-plugin-cloudmanager) herunterladen, einrichten und verwenden.

2. Authentifizieren Sie die Adobe I/O-CLI mit dem AEM als Cloud Service-Programm

3. `COMMERCE_ENDPOINT`-Variable in Cloud Manager festlegen

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Weitere Informationen finden Sie in den [CLI-Dokumentationen](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   Die Commerce GraphQL-Endpunkt-URL muss auf den GraphQl-Dienst des Commerce verweisen und eine sichere HTTPS-Verbindung verwenden. Beispiel: `https://demo.magentosite.cloud/graphql`.

4. Gestufte Katalogfunktionen aktivieren, für die eine Authentifizierung erforderlich ist (Optional)

   >[!NOTE]
   >
   >Diese Funktion ist nur mit Adobe Commerce Enterprise oder Cloud Edition verfügbar. Weitere Informationen finden Sie unter [Token-basierte Authentifizierung.](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens)

   Legen Sie die `COMMERCE_AUTH_HEADER`-Variable in Cloud Manager fest:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>Sie können alle Cloud Manager-Variablen mithilfe des folgenden Befehls zur Überprüfung auflisten: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

Danach können Sie AEM Commerce as a Cloud Service verwenden und Ihr Projekt über Cloud Manager bereitstellen.

## Konfigurieren von Stores und Katalogen {#catalog}

Das CIF-Add-on und die [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) können auf mehreren AEM Sitestrukturen verwendet werden, die mit verschiedenen Commerce Stores (oder Store-Ansichten usw.) verbunden sind. Standardmäßig wird das CIF-Add-on mit einer Standardkonfiguration bereitgestellt, die mit dem Standardspeicher und -katalog von Adobe Commerce (Magento) verbunden ist.

Diese Konfiguration kann mithilfe der CIF-Cloud Service-Konfiguration wie folgt für das Projekt angepasst werden:

1. Gehen Sie AEM zu Tools -> Cloud Services -> CIF-Konfiguration

2. Wählen Sie die Commerce-Konfiguration aus, die Sie ändern möchten

3. Öffnen Sie die Konfigurationseigenschaften über die Aktionsleiste

![CIF-Cloud Services-Konfiguration](/help/commerce-cloud/assets/cif-cloud-service-config.png)

Die folgenden Eigenschaften können konfiguriert werden:

- GraphQL Client - Wählen Sie den konfigurierten GraphQL Client für Commerce Backend Kommunikation. Dies sollte in der Regel standardmäßig beibehalten werden.
- Store-Ansicht - die Kennung der (Magento-)Store-Ansicht. Wenn leer, wird die standardmäßige Store-Ansicht verwendet.
- GraphQL Proxy Path - der URL-Pfad GraphQL Proxy in AEM Verwendung, um Anforderungen an den Commerce Backend GraphQL Endpunkt zu projizieren.
   >[!NOTE]
   >
   > In den meisten Setups darf der Standardwert `/api/graphql` nicht geändert werden. Diese Einstellung sollte nur durch erweiterte Einstellungen geändert werden, die nicht den bereitgestellten GraphQL-Proxy verwenden.
- Unterstützung für Katalog-UID aktivieren: Aktivieren Sie die Unterstützung für UID anstelle von ID in den Commerce-Backend-GraphQL-Aufrufen.
   >[!NOTE]
   >
   > Die Unterstützung für UIDs wurde in Adobe Commerce (Magento) 2.4.2 eingeführt. Aktivieren Sie dies nur, wenn Ihr Commerce-Backend ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.
- Katalogstamm-Kategorien-ID - die Kennung (UID oder ID) des Stammkatalogs

Die oben dargestellte Konfiguration dient als Referenz. Die Projekte sollten ihre eigenen Konfigurationen bereitstellen.

Für komplexere Setups mit mehreren AEM Site-Strukturen kombiniert mit verschiedenen Commerce-Katalogen lesen Sie das Lernprogramm [Commerce Multi-Store Setup](configuring/multi-store-setup.md).

## Zusätzliche Ressourcen {#additional-resources}

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Commerce-Multi-Store-Einrichtung](configuring/multi-store-setup.md)
