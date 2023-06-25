---
title: Erste Schritte mit AEM Commerce as a Cloud Service
description: Erfahren Sie, wie Sie ein für Commerce aktiviertes AEM-Projekt in einer laufenden AEM as a Cloud Service -Umgebung bereitstellen. Verwenden Sie Funktionen von Adobe Cloud Manager und eine CI/CD-Pipeline, damit Sie die Venia-Referenz-Storefront in einer laufenden Umgebung erstellen können.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: Cloud Service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
source-git-commit: f0e9fe0bdf35cc001860974be1fa2a7d90f7a3a9
workflow-type: tm+mt
source-wordcount: '1113'
ht-degree: 43%

---

# Erste Schritte mit AEM Commerce as a Cloud Service {#start}

Um mit AEM Commerce as a Cloud Service zu beginnen, muss Ihr Experience Manager Cloud Service über das Commerce Integration Framework (CIF)-Add-on verfügen. Das CIF-Add-on ist ein zusätzliches Modul zusätzlich zu [AEM Sites as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/home.html).

## Einstieg {#onboarding}

Das Onboarding für AEM Commerce as a Cloud Service erfolgt in zwei Schritten:

1. AEM Commerce as a Cloud Service aktivieren und das CIF-Add-on bereitstellen
2. AEM Commerce as a Cloud Service mit Ihrer Lösung für den Handel verbinden

Der erste Onboarding-Schritt wird von Adobe ausgeführt. Weitere Informationen zu Preisen und Bereitstellung erhalten Sie von Ihrem Vertriebsmitarbeiter.

Nachdem Sie das CIF-Add-on bereitgestellt haben, wird es auf alle vorhandenen Cloud Manager-Programme angewendet. Wenn Sie kein Cloud Manager-Programm haben, müssen Sie eines erstellen. Weitere Informationen finden Sie unter [Einrichten des Programms](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/program-setup.html).

Der zweite Schritt erfolgt per Self-Service für die einzelnen AEM as a Cloud Service-Umgebungen. Es gibt einige zusätzliche Konfigurationen, die Sie nach der ersten Bereitstellung des CIF-Add-ons vornehmen müssen.

## AEM mit einer Lösung für den Handel verbinden {#solution}

So verbinden Sie das CIF-Add-on und das [CIF-Kernkomponenten AEM](https://github.com/adobe/aem-core-cif-components) mit einer Commerce-Lösung verwenden, müssen Sie die GraphQL-Endpunkt-URL über eine Cloud Manager-Umgebungsvariable bereitstellen. Der Variablenname lautet `COMMERCE_ENDPOINT`. Eine sichere Verbindung über HTTPS muss konfiguriert werden.

Diese Umgebungsvariable wird an zwei Stellen verwendet:

- GraphQL-Aufrufe vom AEM zum Commerce-Backend über einen gemeinsamen GraphQl-Client, der von den AEM CIF-Kernkomponenten und Kundenprojektkomponenten verwendet wird.
- Richten Sie in jeder AEM Umgebung, in der die Variable festgelegt ist, eine GraphQL-Proxy-URL ein unter `/api/graphql`. Diese URL wird von den AEM Commerce-Authoring-Tools (CIF-Add-on) und den clientseitigen CIF-Komponenten verwendet.

Für jede AEM as a Cloud Service-Umgebung kann eine andere GraphQL-Endpunkt-URL verwendet werden. Auf diese Weise können Projekte AEM-Staging-Umgebungen, die über Commerce-Staging-Systeme und eine AEM-Produktionsumgebung verfügen, mit einem Commerce-Produktionssystem verbinden. Der entsprechende-GraphQL-Endpunkt muss öffentlich verfügbar sein; private VPN- oder lokale Verbindungen werden nicht unterstützt. Optional kann ein Authentifizierungs-Header bereitgestellt werden, um zusätzliche CIF-Funktionen zu verwenden, für die eine Authentifizierung erforderlich ist.

Optional und nur für Adobe Commerce Enterprise/Cloud unterstützt das CIF-Add-on die Verwendung von gestaffelten Katalogdaten für AEM Autoren. Für diese Daten müssen Sie einen Autorisierungs-Header konfigurieren. Dieser konfigurierte Autorisierungs-Header ist aus Sicherheitsgründen nur auf AEM-Autoreninstanzen verfügbar und wird nur dort verwendet. AEM-Veröffentlichungsinstanzen können keine gestaffelten Daten anzeigen.

Es gibt zwei Optionen zum Konfigurieren des Endpunkts:

### Über die Benutzeroberfläche von Cloud Manager (Standard) {#cm-ui}

>[!VIDEO](https://video.tv.adobe.com/v/37843?quality=12&learn=on)

Diese Konfiguration kann über ein Dialogfeld auf der Seite &quot;Umgebungsdetails&quot;durchgeführt werden. Wenn Sie diese Seite für ein Commerce-aktiviertes Programm anzeigen, wird eine Schaltfläche angezeigt, wenn der Endpunkt derzeit nicht konfiguriert ist:

![CM-Umgebungsinformationen](/help/commerce-cloud/assets/commerce-cmui.png)

Durch Klicken auf diese Schaltfläche wird ein Dialogfeld geöffnet:

![CM-Commerce-Endpunkt](/help/commerce-cloud/assets/commerce-cm-endpoint.png)

Nachdem der Endpunkt und optional ein Autorisierungsheader für die staging-Katalogunterstützung festgelegt wurden, wird der Endpunkt auf der Detailseite angezeigt. Klicken Sie auf das Symbol Bearbeiten , um dasselbe Dialogfeld zu öffnen, in dem Sie den Endpunkt bei Bedarf bearbeiten können.

![CM-Umgebungsinformationen](/help/commerce-cloud/assets/commerce-cmui-done.png)

### Über Adobe Developer CLI  {#adobe-cli}

Gehen Sie wie folgt vor, um über Adobe Developer CLI AEM mit einer Commerce-Lösung zu verbinden:

1. Adobe Developer-CLI mit dem Cloud Manager-Plugin abrufen

   Überprüfen Sie die [Dokumentation zu Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=de) Informationen zum Herunterladen, Einrichten und Verwenden des [Adobe Developer CLI](https://github.com/adobe/aio-cli) mit dem [Cloud Manager-CLI-Plug-in](https://github.com/adobe/aio-cli-plugin-cloudmanager).

2. Adobe Developer-CLI mit dem as a Cloud Service AEM-Programm authentifizieren

3. `COMMERCE_ENDPOINT`-Variable in Cloud Manager festlegen

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   Weitere Informationen finden Sie in den [CLI-Dokumentationen](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   Die Commerce-GraphQL-Endpunkt-URL muss auf den GraphQL-Service von Magento verweisen und eine sichere HTTPS-Verbindung nutzen. Beispiel: `https://<yourcommercesystem>/graphql`.

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

Sie können AEM Commerce as a Cloud Service verwenden und Ihr Projekt über Cloud Manager bereitstellen.

## Konfigurieren von Stores und Katalogen {#catalog}

Das CIF-Add-on und das [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) kann auf mehreren AEM Site-Strukturen verwendet werden, die mit verschiedenen Commerce-Stores (oder Store-Ansichten usw.) verbunden sind. Standardmäßig wird das CIF-Add-on mit einer Standardkonfiguration bereitgestellt, die mit dem Standardspeicher und -katalog von Adobe Commerce verbunden ist.

Diese Konfiguration kann mithilfe der CIF-Cloud Service-Konfiguration wie folgt für das Projekt angepasst werden:

1. Gehen Sie AEM zu Tools > Cloud Services > CIF-Konfiguration .

2. Wählen Sie die Commerce-Konfiguration aus, die Sie ändern möchten.

3. Öffnen Sie die Konfigurationseigenschaften über die Aktionsleiste.

![CIF-Cloud Services-Konfiguration](/help/commerce-cloud/assets/cif-cloud-service-config.png)

Die folgenden Eigenschaften können konfiguriert werden:

- GraphQL-Client – Wählen Sie den konfigurierten GraphQL-Client für die Commerce-Backend-Kommunikation aus. Dieser Client sollte in der Regel standardmäßig beibehalten werden.
- Shop-Ansicht – die Kennung der Shop-Ansicht. Wenn leer, wird die standardmäßige Store-Ansicht verwendet.
- GraphQL-Proxy-Pfad – der URL-Pfad des GraphQL-Proxy in AEM, der als Proxy für Anfragen an den Commerce-Backend-GraphQL-Endpunkt verwendet wird.
  >[!NOTE]
  >
  > In den meisten Setups wird der Standardwert `/api/graphql` darf nicht geändert werden. Nur komplexere Setups, die nicht den bereitgestellten GraphQL-Proxy verwenden, sollten diese Einstellung ändern.
- Unterstützung der Catalog-UID aktivieren – aktiviert die Unterstützung für UID anstelle von ID in den Commerce-Backend-GraphQL-Aufrufen.
  >[!NOTE]
  >
  > Unterstützung für UIDs wurde in Adobe Commerce 2.4.2 eingeführt. Aktivieren Sie UIDs nur dann, wenn Ihr Commerce-Backend ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.
- Kennung der Stammkategorie des Katalogs – die Kennung (UID oder ID) des Stammverzeichnisses des Shops
  >[!CAUTION]
  >
  > Ab Version 2.0.0 der CIF-Kernkomponenten wurde die Unterstützung für `id` entfernt und durch `uid` ersetzt. Wenn Ihr Projekt Version 2.0.0 der CIF-Kernkomponenten verwendet, müssen Sie die Unterstützung der Catalog-UID aktivieren und eine gültige Kategorie-UID als „Katalogstamm-Kategorienkennung“ verwenden.

Die oben dargestellte Konfiguration dient als Referenz. Projekte sollten ihre eigenen Konfigurationen bereitstellen.

Für komplexere Setups finden Sie unter Verwendung mehrerer AEM Site-Strukturen in Kombination mit verschiedenen Commerce-Katalogen die [Commerce-Multi-Store-Einrichtung](configuring/multi-store-setup.md) Tutorial.

## Zusätzliche Ressourcen {#additional-resources}

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Multi-Store-Einrichtung in Commerce](configuring/multi-store-setup.md)
- [Mehrere Commerce-Systemkonfigurationen](configuring/multiple-commerce-systems-setup.md)

