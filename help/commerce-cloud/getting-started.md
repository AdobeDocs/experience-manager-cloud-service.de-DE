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
source-git-commit: 84a97f09402602df33c8f0494feed57fdb510add
workflow-type: tm+mt
source-wordcount: '1071'
ht-degree: 35%

---

# Erste Schritte mit AEM Commerce as a Cloud Service {#start}

Damit Sie mit AEM Commerce as a Cloud Service loslegen können, muss Ihr Experience Manager Cloud Service über das Add-on Commerce Integration Framework (CIF) verfügen. Das CIF-Add-on ist ein Zusatzmodul für [AEM Sites as a Cloud Service](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/sites/home.translate.html).

## Einstieg {#onboarding}

Das Onboarding für AEM Commerce as a Cloud Service erfolgt in zwei Schritten:

1. AEM Commerce as a Cloud Service aktivieren und das CIF-Add-on bereitstellen
2. Verbinden AEM Commerce as a Cloud Service mit Ihrer Commerce-Lösung

Der erste Onboarding-Schritt wird von Adobe ausgeführt. Weitere Informationen zu Preisen und Bereitstellung erhalten Sie von Ihrem Vertriebsmitarbeiter.

Nachdem Sie das CIF-Add-on bereitgestellt haben, wird es auf alle vorhandenen Cloud Manager-Programme angewendet. Wenn Sie kein Cloud Manager-Programm haben, müssen Sie ein neues erstellen. Weitere Informationen finden Sie unter [Ihr Programm einrichten](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/getting-started/setting-up-program.html).

Der zweite Schritt erfolgt per Self-Service für die einzelnen AEM as a Cloud Service-Umgebungen. Es gibt einige zusätzliche Konfigurationen, die Sie nach der anfänglichen Bereitstellung des CIF-Add-ons vornehmen müssen.

## AEM mit einer Commerce-Lösung verbinden {#magento}

Um das CIF-Add-on und die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) mit einer Commerce-Lösung zu verbinden, müssen Sie die GraphQL-Endpunkt-URL über eine Cloud Manager-Umgebungsvariable angeben. Der Variablenname lautet `COMMERCE_ENDPOINT`. Es muss eine sichere Verbindung über HTTPS konfiguriert werden.

Diese Umgebungsvariable wird an zwei Stellen verwendet:

- GraphQL-Aufrufe vom AEM zum Commerce-Backend über einen gemeinsamen GraphQl-Client, der von den AEM CIF-Kernkomponenten und Kundenprojektkomponenten verwendet wird.
- Richten Sie eine GraphQL-Proxy-URL für jede AEM Umgebung ein, für die die Variable unter `/api/graphql` verfügbar ist. Dies wird von den AEM Commerce-Authoring-Tools (CIF-Add-on) und den clientseitigen CIF-Komponenten verwendet.

Für jede AEM als Cloud Service-Umgebung kann eine andere GraphQL-Endpunkt-URL verwendet werden. So können Projekte AEM Staging-Umgebungen mit Commerce-Staging-Systemen und AEM Produktionsumgebung mit einem Commerce-Produktionssystem verbinden. Dieser GraphQL-Endpunkt muss öffentlich verfügbar sein, private VPN- oder lokale Verbindungen werden nicht unterstützt. Optional kann ein Authentifizierungs-Header bereitgestellt werden, um zusätzliche CIF-Funktionen zu verwenden, für die eine Authentifizierung erforderlich ist.

Optional und nur für Adobe Commerce Enterprise/Cloud unterstützt das CIF-Add-on die Verwendung von gestaffelten Katalogdaten für AEM Autoren. Dies erfordert die Konfiguration eines Autorisierungstokens. Das konfigurierte Autorisierungstoken ist aus Sicherheitsgründen nur auf AEM Autoreninstanzen verfügbar und wird verwendet. AEM Veröffentlichungsinstanzen können keine gestaffelten Daten anzeigen.

Es gibt zwei Optionen zum Konfigurieren des Endpunkts:

### Über die Cloud Manager-Benutzeroberfläche (Standard) {#cm-ui}

Dies kann über ein Dialogfeld auf der Seite &quot;Umgebungsdetails&quot;erfolgen. Wenn Sie diese Seite für ein Commerce-aktiviertes Programm anzeigen, wird eine Schaltfläche angezeigt, wenn der Endpunkt derzeit nicht konfiguriert ist:

![CM-Umgebungsinformationen](/help/commerce-cloud/assets/commerce-cmui.png)

Durch Klicken auf diese Schaltfläche wird ein Dialogfeld geöffnet:

![CM Commerce Endpoint](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Nachdem der Endpunkt (optional ein Authentifizierungstoken für die Unterstützung staging-Katalogs) festgelegt wurde, wird der Endpunkt auf der Detailseite angezeigt. Durch Klicken auf das Symbol Bearbeiten wird dasselbe Dialogfeld geöffnet, in dem der Endpunkt bei Bedarf geändert werden kann.

![CM-Umgebungsinformationen](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Über Adobe I/O CLI {#adobe-cli}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Gehen Sie wie folgt vor, um AEM über die Adobe I/O-CLI mit einer Commerce-Lösung zu verbinden:

1. Adobe I/O CLI mit dem Cloud Manager-Plug-in abrufen

   Lesen Sie die [Adobe Cloud Manager-Dokumentation](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html), um zu erfahren, wie Sie die [Adobe I/O-CLI](https://github.com/adobe/aio-cli) mit dem [Cloud Manager-CLI-Plugin](https://github.com/adobe/aio-cli-plugin-cloudmanager) herunterladen, einrichten und verwenden.

2. Adobe I/O-CLI mit dem AEM as a Cloud Service-Programm authentifizieren

3. `COMMERCE_ENDPOINT`-Variable in Cloud Manager festlegen

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Weitere Informationen finden Sie in den [CLI-Dokumentationen](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   Die Commerce-GraphQL-Endpunkt-URL muss auf den GraphQl-Dienst des Commerce verweisen und eine sichere HTTPS-Verbindung verwenden. Beispiel: `https://demo.magentosite.cloud/graphql`.

4. Aktivieren von Stage-Katalog-Funktionen, für die eine Authentifizierung erforderlich ist (optional)

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

## Stores und Kataloge konfigurieren {#catalog}

Das CIF-Add-on und die [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) können auf mehreren AEM Site-Strukturen verwendet werden, die mit verschiedenen Commerce-Stores (oder Store-Ansichten usw.) verbunden sind. Standardmäßig wird das CIF-Add-on mit einer Standardkonfiguration bereitgestellt, die mit dem Standardspeicher und -katalog von Adobe Commerce verbunden ist (Magento).

Diese Konfiguration kann mithilfe der CIF-Cloud Service-Konfiguration wie folgt für das Projekt angepasst werden:

1. Navigieren Sie AEM zu Tools > Cloud Services > CIF-Konfiguration .

2. Wählen Sie die Commerce-Konfiguration aus, die Sie ändern möchten

3. Öffnen Sie die Konfigurationseigenschaften über die Symbolleiste.

![CIF-Cloud Services-Konfiguration](/help/commerce-cloud/assets/cif-cloud-service-config.png)

Die folgenden Eigenschaften können konfiguriert werden:

- GraphQL-Client : Wählen Sie den konfigurierten GraphQL-Client für die Commerce-Backend-Kommunikation aus. Dies sollte in der Regel standardmäßig beibehalten werden.
- Store View - die Kennung der (Magento-)Store-Ansicht. Wenn leer, wird die standardmäßige Store-Ansicht verwendet.
- GraphQL-Proxy-Pfad - der URL-Pfad GraphQL-Proxy in AEM zum Proxy von Anforderungen an den Commerce-Backend-GraphQL-Endpunkt verwendet wird.
   >[!NOTE]
   >
   > In den meisten Setups darf der Standardwert `/api/graphql` nicht geändert werden. Nur erweiterte Einstellungen, die nicht den bereitgestellten GraphQL-Proxy verwenden, sollten diese Einstellung ändern.
- Unterstützung der Catalog-UID aktivieren - Aktivieren Sie die Unterstützung für UID anstelle der ID in den Commerce-Backend-GraphQL-Aufrufen.
   >[!NOTE]
   >
   > Die Unterstützung für UIDs wurde in Adobe Commerce (Magento) 2.4.2 eingeführt. Aktivieren Sie dies nur, wenn Ihr Commerce-Backend ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.
- Kennung der Stammkategorie des Katalogs - die Kennung (UID oder ID) des Stammverzeichnisses des Stores

Die oben dargestellte Konfiguration dient als Referenz. Die Projekte sollten ihre eigenen Konfigurationen bereitstellen.

Komplexere Setups mit mehreren AEM Site-Strukturen in Kombination mit verschiedenen Commerce-Katalogen finden Sie im Tutorial [Commerce Multi-Store Setup](configuring/multi-store-setup.md) .

## Zusätzliche Ressourcen {#additional-resources}

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Commerce-Multi-Store-Einrichtung](configuring/multi-store-setup.md)
