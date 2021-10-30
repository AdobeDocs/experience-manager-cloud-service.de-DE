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
source-git-commit: 35137687e51d54454d3a4b7aed247a28d98dc291
workflow-type: ht
source-wordcount: '1104'
ht-degree: 100%

---

# Erste Schritte mit AEM Commerce as a Cloud Service {#start}

Damit Sie mit AEM Commerce as a Cloud Service loslegen können, muss Ihr Experience Manager Cloud Service über das Add-on Commerce Integration Framework (CIF) verfügen. Das CIF-Add-on ist ein Zusatzmodul für [AEM Sites as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/home.html?lang=de).

## Einstieg {#onboarding}

Das Onboarding für AEM Commerce as a Cloud Service erfolgt in zwei Schritten:

1. AEM Commerce as a Cloud Service aktivieren und das CIF-Add-on bereitstellen
2. AEM Commerce as a Cloud Service mit Ihrer Lösung für den Handel verbinden

Der erste Onboarding-Schritt wird von Adobe ausgeführt. Weitere Informationen zu Preisen und Bereitstellung erhalten Sie von Ihrem Vertriebsmitarbeiter.

Nachdem Sie das CIF-Add-on bereitgestellt haben, wird es auf alle vorhandenen Cloud Manager-Programme angewendet. Wenn Sie kein Cloud Manager-Programm haben, müssen Sie ein neues erstellen. Weitere Informationen finden Sie unter [Ihr Programm einrichten](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/getting-started/setting-up-program.html?lang=de).

Der zweite Schritt erfolgt per Self-Service für die einzelnen AEM as a Cloud Service-Umgebungen. Es gibt einige zusätzliche Konfigurationen, die Sie nach der anfänglichen Bereitstellung des CIF-Add-ons vornehmen müssen.

## AEM mit einer Lösung für den Handel verbinden {#magento}

Um das CIF-Add-on und die [AEM CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) mit Ihrer Lösung für den Handel zu verbinden, müssen Sie über eine Cloud Manager-Umgebungsvariable die GraphQL-Endpunkt-URL angeben. Der Variablenname lautet `COMMERCE_ENDPOINT`. Es muss eine sichere Verbindung über HTTPS konfiguriert werden.

Diese Umgebungsvariable wird an zwei Stellen verwendet:

- GraphQL-Aufrufe vom AEM zum Commerce-Backend über einen gemeinsamen GraphQL-Client, die von den AEM CIF-Kernkomponenten und Projektkomponenten des Kunden verwendet werden.
- Richten Sie eine GraphQL-Proxy-URL für jede AEM-Umgebung ein, für die die Variable unter `/api/graphql` verfügbar ist. Diese wird von den AEM Commerce-Authoring-Tools (CIF-Add-on) und den Client-seitigen CIF-Komponenten verwendet.

Für jede AEM as a Cloud Service-Umgebung kann eine andere GraphQL-Endpunkt-URL verwendet werden. Auf diese Weise können Projekte AEM-Staging-Umgebungen, die über Commerce-Staging-Systeme und eine AEM-Produktionsumgebung verfügen, mit einem Commerce-Produktionssystem verbinden. Der entsprechende-GraphQL-Endpunkt muss öffentlich verfügbar sein; private VPN- oder lokale Verbindungen werden nicht unterstützt. Optional kann ein Authentifizierungs-Header bereitgestellt werden, um zusätzliche CIF-Funktionen zu verwenden, für die eine Authentifizierung erforderlich ist.

Optional und nur für Adobe Commerce Enterprise/Cloud unterstützt das CIF-Add-on die Verwendung von gestaffelten Katalogdaten für AEM-Autoren. Dies erfordert die Konfiguration eines Autorisierungstokens. Das konfigurierte Autorisierungstoken ist aus Sicherheitsgründen nur auf AEM-Autoreninstanzen verfügbar und wird nur dort verwendet. AEM-Veröffentlichungsinstanzen können keine gestaffelten Daten anzeigen.

Es gibt zwei Optionen zum Konfigurieren des Endpunkts:

### Über die Cloud Manager-Benutzeroberfläche (Standard) {#cm-ui}

Dies kann über ein Dialogfeld auf der Seite „Umgebungsdetails“ erfolgen. Wenn Sie diese Seite für ein Commerce-fähiges Programm anzeigen, wird eine Schaltfläche angezeigt, wenn der Endpunkt derzeit nicht konfiguriert ist:

![CM-Umgebungsinformationen](/help/commerce-cloud/assets/commerce-cmui.png)

Durch Klicken auf diese Schaltfläche wird ein Dialogfeld geöffnet:

![CM-Commerce-Endpunkt](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Nachdem der Endpunkt (optional ein Authentifizierungstoken für die Unterstützung gestaffelter Katalogdaten) festgelegt wurde, wird der Endpunkt auf der Detailseite angezeigt. Durch Klicken auf das Symbol „Bearbeiten“ wird dasselbe Dialogfeld geöffnet, in dem der Endpunkt bei Bedarf geändert werden kann.

![CM-Umgebungsinformationen](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Über Adobe I/O CLI  {#adobe-cli}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Gehen Sie wie folgt vor, um AEM über Adobe I/O CLI mit einer Lösung für den Handel zu verbinden:

1. Adobe I/O CLI mit dem Cloud Manager-Plug-in abrufen

   Lesen Sie die [Adobe Cloud Manager-Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/using/introduction-to-cloud-manager.html?lang=de), um Informationen zum Herunterladen, Einrichten und Verwenden der [Adobe I/O CLI](https://github.com/adobe/aio-cli) mit dem [Cloud Manager-CLI-Plug-in](https://github.com/adobe/aio-cli-plugin-cloudmanager) zu erhalten.

2. Adobe I/O CLI mit dem AEM as a Cloud Service-Programm authentifizieren

3. `COMMERCE_ENDPOINT`-Variable in Cloud Manager festlegen

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Weitere Informationen finden Sie in den [CLI-Dokumentationen](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   Die Commerce-GraphQL-Endpunkt-URL muss auf den GraphQL-Service von Magento verweisen und eine sichere HTTPS-Verbindung nutzen. Beispiel: `https://<yourmagentosystem>/graphql`.

4. Aktivieren von Funktionen für gestaffelte Katalogdaten, für die eine Authentifizierung erforderlich ist (optional)

   >[!NOTE]
   >
   >Diese Funktion ist nur mit Adobe Commerce Enterprise oder Cloud Edition verfügbar. Weitere Informationen finden Sie unter [Token-basierte Authentifizierung.](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens)

   Legen Sie die `COMMERCE_AUTH_HEADER`-Geheimnis-Variable in Cloud Manager fest:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>Sie können alle Cloud Manager-Variablen mithilfe des folgenden Befehls zur Überprüfung auflisten: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

Danach können Sie AEM Commerce as a Cloud Service verwenden und Ihr Projekt über Cloud Manager bereitstellen.

## Shops und Kataloge konfigurieren {#catalog}

Das CIF-Add-on und die [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) können auf mehreren AEM-Website-Strukturen verwendet werden, die mit verschiedenen Commerce-Shops (oder Shop-Ansichten usw.) verbunden sind. Standardmäßig wird das CIF-Add-on mit einer vordefinierten Konfiguration bereitgestellt, die mit dem Standard-Shop und -Katalog von Adobe Commerce verbunden ist (Magento).

Diese Konfiguration kann mithilfe der CIF-Cloud Service-Konfiguration wie folgt für das Projekt angepasst werden:

1. Gehen Sie in AEM zu „Tools“ > „Cloud Services“ > „CIF-Konfiguration“

2. Wählen Sie die Commerce-Konfiguration aus, die Sie ändern möchten

3. Öffnen Sie die Konfigurationseigenschaften über die Symbolleiste

![CIF-Cloud Services-Konfiguration](/help/commerce-cloud/assets/cif-cloud-service-config.png)

Die folgenden Eigenschaften können konfiguriert werden:

- GraphQL-Client – Wählen Sie den konfigurierten GraphQL-Client für die Commerce-Backend-Kommunikation aus. Dies sollte normalerweise auf der Standardeinstellung bleiben.
- Shop-Ansicht – die Kennung der (Magento-)Shop-Ansicht. Wenn leer, wird die standardmäßige Shop-Ansicht verwendet.
- GraphQL-Proxy-Pfad – der URL-Pfad des GraphQL-Proxy in AEM, der als Proxy für Anfragen an den Commerce-Backend-GraphQL-Endpunkt verwendet wird.
   >[!NOTE]
   >
   > In den meisten Setups darf der Standardwert `/api/graphql` nicht geändert werden. Nur komplexere Setups, die nicht den bereitgestellten GraphQL-Proxy verwenden, sollten diese Einstellung ändern.
- Unterstützung der Catalog-UID aktivieren – aktiviert die Unterstützung für UID anstelle von ID in den Commerce-Backend-GraphQL-Aufrufen.
   >[!NOTE]
   >
   > Die Unterstützung für UIDs wurde in Adobe Commerce (Magento) 2.4.2 eingeführt. Aktivieren Sie dies nur, wenn Ihr Commerce-Backend ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.
- Kennung der Stammkategorie des Katalogs – die Kennung (UID oder ID) des Stammverzeichnisses des Shops
   >[!CAUTION]
   >
   > Ab Version 2.0.0 der CIF-Kernkomponenten wurde die Unterstützung für `id` entfernt und durch `uid` ersetzt. Wenn Ihr Projekt Version 2.0.0 der CIF-Kernkomponenten verwendet, müssen Sie die Unterstützung der Catalog-UID aktivieren und eine gültige Kategorie-UID als „Katalogstamm-Kategorienkennung“ verwenden.

Die oben dargestellte Konfiguration dient als Referenz. Projekte sollten ihre eigenen Konfigurationen bereitstellen.

Komplexere Setups mit mehreren AEM-Website-Strukturen in Kombination mit verschiedenen Commerce-Katalogen finden Sie im Tutorial [Einrichten von mehreren Commerce-Shops](configuring/multi-store-setup.md).

## Zusätzliche Ressourcen {#additional-resources}

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Multi-Store-Einrichtung in Commerce](configuring/multi-store-setup.md)
