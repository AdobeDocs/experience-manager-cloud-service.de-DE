---
title: Erste Schritte mit AEM Commerce as a Cloud Service
description: Erfahren Sie, wie Sie ein Adobe Experience Manager(AEM)-Commerce-Projekt mithilfe von Adobe Cloud Manager, einer CI/CD-Pipeline und der Venia-Referenz-Storefront bereitstellen.
topics: Commerce
feature: Commerce Integration Framework, Cloud Manager
version: Experience Manager as a Cloud Service
doc-type: tutorial
kt: 4947
thumbnail: 37843.jpg
exl-id: 73ba707e-5e2d-459a-8cc8-846d1a5f2fd7
role: Admin
source-git-commit: e707bddc17208d599491d27c5bc0134cb41233e0
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 89%

---


# Erste Schritte mit AEM Commerce as a Cloud Service {#start}

Um mit Adobe Experience Manager (AEM) Commerce as a Cloud Service beginnen zu können, muss Ihr Experience Manager Cloud Service mit dem Add-on für das Commerce Integration Framework (CIF) bereitgestellt werden. Das CIF-Add-on ist ein zusätzliches Modul zusätzlich zu [AEM Sites as a Cloud Service.](/help/sites-cloud/sites-cloud-changes.md)

>[!TIP]
>
>**Haben Sie Edge Delivery Services in Betracht gezogen?**
>
>Edge Delivery Services ist die von Adobe bevorzugte Lösung zum Erstellen einer Storefront. Weitere Informationen finden Sie [&#x200B; Dokument „Einführung &#x200B;](/help/commerce-cloud/introduction.md) Übersicht“.

## Einstieg {#onboarding}

Das Onboarding für AEM Commerce as a Cloud Service erfolgt in zwei Schritten:

1. AEM Commerce as a Cloud Service aktivieren und das CIF-Add-on bereitstellen
1. AEM Commerce as a Cloud Service mit Ihrer Lösung für den Handel verbinden

Der erste Onboarding-Schritt wird von Adobe ausgeführt. Weitere Informationen zu Preisen und Bereitstellung erhalten Sie von Ihrer Vertriebsmitarbeiterin bzw. Ihrem -mitarbeiter.

Nachdem Sie das CIF-Add-on bereitgestellt haben, wird es auf alle vorhandenen Cloud Manager-Programme angewendet. Wenn Sie kein Cloud Manager-Programm haben, müssen Sie eines erstellen. Weitere Informationen finden Sie unter [Einrichten des Programms.](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/getting-started/program-setup.html?lang=de)

Der zweite Schritt erfolgt per Self-Service für die einzelnen AEM as a Cloud Service-Umgebungen. Es gibt einige zusätzliche Konfigurationen, die Sie nach der anfänglichen Bereitstellung des CIF-Add-ons vornehmen müssen.

## Verbinden von AEM mit einer Lösung für den Handel {#solution}

Um das CIF-Add-on und die [AEM-CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) mit Ihrer Lösung für den Handel zu verbinden, müssen Sie über eine Cloud Manager-Umgebungsvariable die URL des GraphQL-Endpunkts angeben. Der Variablenname lautet `COMMERCE_ENDPOINT`. Eine sichere Verbindung über HTTPS muss konfiguriert werden.

Diese Umgebungsvariable wird an zwei Stellen verwendet:

* GraphQL-Aufrufe vom AEM zum Commerce-Backend über einen gemeinsamen GraphQI-Client, die von den AEM CIF-Kernkomponenten und kundenseitigen Projektkomponenten verwendet werden.
* Richten Sie eine GraphQL-Proxy-URL für jede AEM-Umgebung ein, für die die Variable unter `/api/graphql` verfügbar ist. Diese URL wird von den AEM Commerce-Authoring-Tools (CIF-Add-on) und den Client-seitigen CIF-Komponenten verwendet.

Für jede AEM as a Cloud Service-Umgebung kann eine andere GraphQL-Endpunkt-URL verwendet werden. Auf diese Weise können Projekte AEM-Staging-Umgebungen, die über Commerce-Staging-Systeme und eine AEM-Produktionsumgebung verfügen, mit einem Commerce-Produktionssystem verbinden. Der entsprechende-GraphQL-Endpunkt muss öffentlich verfügbar sein; private VPN- oder lokale Verbindungen werden nicht unterstützt. Optional kann ein Authentifizierungs-Header bereitgestellt werden, um zusätzliche CIF-Funktionen zu verwenden, die eine Authentifizierung erfordern.

Optional und nur für Adobe Commerce Enterprise/Cloud unterstützt das CIF-Add-on die Verwendung von gestaffelten Katalogdaten für AEM-Autorinnen bzw. -Autoren. Für diese Daten müssen Sie einen Autorisierungs-Header konfigurieren. Dieser Header ist aus Sicherheitsgründen nur auf AEM-Autoreninstanzen verfügbar und wird nur dort verwendet. AEM-Veröffentlichungsinstanzen können keine Staging-Daten anzeigen.

Es gibt zwei Optionen zum Konfigurieren des Endpunkts:

### Über die Benutzeroberfläche von Cloud Manager (Standard) {#cm-ui}

>[!VIDEO](https://video.tv.adobe.com/v/343434?captions=ger&quality=12&learn=on)

Diese Konfiguration kann über ein Dialogfeld auf der Seite „Umgebungsdetails“ erfolgen. Wenn Sie diese Seite für ein Commerce-fähiges Programm anzeigen, wird eine Schaltfläche angezeigt, wenn der Endpunkt derzeit nicht konfiguriert ist:

![CM-Umgebungsinformationen](/help/commerce-cloud/cif-storefront/assets/commerce-cmui.png)

Durch Klicken auf diese Schaltfläche wird ein Dialogfeld geöffnet:

![CM-Commerce-Endpunkt](/help/commerce-cloud/cif-storefront/assets/commerce-cm-endpoint.png)

Nachdem der Endpunkt (und optional ein Authentifizierungs-Header für die Unterstützung gestaffelter Katalogdaten) festgelegt wurde, wird der Endpunkt auf der Detailseite angezeigt. Klicken Sie auf das Symbol „Bearbeiten“, um dasselbe Dialogfeld zu öffnen, in dem Sie den Endpunkt bei Bedarf bearbeiten können.

![CM-Umgebungsinformationen](/help/commerce-cloud/cif-storefront/assets/commerce-cmui-done.png)

### Über Adobe I/O CLI  {#adobe-cli}

Gehen Sie wie folgt vor, um AEM über Adobe I/O CLI mit einer Lösung für den Handel zu verbinden:

1. Abrufen der Adobe I/O-CLI mit dem Cloud Manager-Plug-in.

   * Lesen Sie die [Dokumentation zu Adobe Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-manager/content/introduction.html?lang=de), um Informationen zum Herunterladen, Einrichten und Verwenden der [Adobe I/O CLI](https://github.com/adobe/aio-cli) mit dem [Cloud Manager CLI-Plug-in zu erhalten.](https://github.com/adobe/aio-cli-plugin-cloudmanager)

1. Authentifizieren Sie die Adobe I/O-CLI mit dem AEM as a Cloud Service-Programm.

1. Legen Sie die `COMMERCE_ENDPOINT` in Cloud Manager fest.

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --variable COMMERCE_ENDPOINT "<Magento GraphQL endpoint URL>"
   ```

   * Weitere Informationen finden Sie in den [CLI-Dokumentationen](https://github.com/adobe/aio-cli-plugin-cloudmanager#aio-cloudmanagerset-environment-variables-environmentid).

   * Die Commerce-GraphQL-Endpunkt-URL muss auf den GraphQL-Service von Magento verweisen und eine sichere HTTPS-Verbindung nutzen. Beispiel: `https://<yourcommercesystem>/graphql`.

1. Aktivieren Sie Funktionen für gestaffelte Katalogdaten, für die eine Authentifizierung erforderlich ist (optional).

   >[!NOTE]
   >
   >Diese Funktion ist nur mit Adobe Commerce Enterprise oder Cloud Edition verfügbar. Weitere Informationen finden Sie unter [Token-basierte Authentifizierung.](https://devdocs.magento.com/guides/v2.4/get-started/authentication/gs-authentication-token.html#integration-tokens)

   * Legen Sie die `COMMERCE_AUTH_HEADER`-Geheimnis-Variable in Cloud Manager fest:

   ```bash
   aio cloudmanager:set-environment-variables ENVIRONMENT_ID --secret COMMERCE_AUTH_HEADER "Authorization: Bearer <Access Token>"
   ```

>[!TIP]
>
>Sie können alle Cloud Manager-Variablen mithilfe des folgenden Befehls zur Überprüfung auflisten: `aio cloudmanager:list-environment-variables ENVIRONMENT_ID`

Sie sind bereit, AEM as a Cloud Service zu verwenden und können Ihr Projekt über Cloud Manager bereitstellen.

## Konfigurieren von Stores und Katalogen {#catalog}

Das Add-on und die [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components) können auf mehreren AEM-Website-Strukturen verwendet werden, die mit verschiedenen E-Commerce-Stores (oder Store-Ansichten usw.) verbunden sind. Standardmäßig wird das CIF-Add-On mit einer Standardkonfiguration bereitgestellt, die eine Verbindung mit dem Standard-Store und -Katalog von Adobe Commerce herstellt.

Diese Konfiguration kann mithilfe der CIF-Cloud-Service-Konfiguration wie folgt für das Projekt angepasst werden:

1. Gehen Sie in AEM zu „Tools“ > „Cloud-Services“ > „CIF-Konfiguration“.

1. Wählen Sie die Commerce-Konfiguration aus, die Sie ändern möchten.

1. Öffnen Sie die Konfigurationseigenschaften über die Aktionsleiste.

![CIF-Cloud Services-Konfiguration](/help/commerce-cloud/cif-storefront/assets/cif-cloud-service-config.png)

Die folgenden Eigenschaften können konfiguriert werden:

* GraphQL-Client – Wählen Sie den konfigurierten GraphQL-Client für die Commerce-Backend-Kommunikation aus. Dieser Client sollte normalerweise auf der Standardeinstellung bleiben.
* Store-Ansicht – die Kennung der Store-Ansicht. Wenn leer, wird die standardmäßige Store-Ansicht verwendet.
* GraphQL-Proxy-Pfad – der URL-Pfad des GraphQL-Proxy in AEM, der als Proxy für Anfragen an den GraphQL-Endpunkt für das Commerce-Backend verwendet wird.

  >[!NOTE]
  >
  > In den meisten Setups darf der Standardwert `/api/graphql` nicht geändert werden. Nur komplexere Setups, die nicht den bereitgestellten GraphQL-Proxy verwenden, sollten diese Einstellung ändern.

* Unterstützung der Catalog-UID aktivieren – aktiviert die Unterstützung für UID anstelle von ID in den Commerce-Backend-GraphQL-Aufrufen.

  >[!NOTE]
  >
  > Die Unterstützung für UIDs wurde in Adobe Commerce 2.4.2 eingeführt. Aktivieren Sie UIDs nur, wenn Ihr Commerce-Backend ein GraphQL-Schema der Version 2.4.2 oder höher unterstützt.

* Kennung der Stammkategorie des Katalogs – die Kennung (UID oder ID) des Stammverzeichnisses des Shops

  >[!CAUTION]
  >
  > Ab Version 2.0.0 der CIF-Kernkomponenten wurde die Unterstützung für `id` entfernt und durch `uid` ersetzt. Wenn Ihr Projekt Version 2.0.0 der CIF-Kernkomponenten verwendet, müssen Sie die Unterstützung der Catalog-UID aktivieren und eine gültige Kategorie-UID als „Katalogstamm-Kategorienkennung“ verwenden.

Die oben dargestellte Konfiguration dient als Referenz. Projekte sollten ihre eigenen Konfigurationen bereitstellen.

Komplexere Setups mit mehreren AEM-Website-Strukturen in Kombination mit verschiedenen Commerce-Katalogen finden Sie im Tutorial [Einrichten von mehreren Commerce-Stores](/help/commerce-cloud/cif-storefront/configuring/multi-store-setup.md).

## Zusätzliche Ressourcen {#additional-resources}

* [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
* [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
* [Multi-Store-Einrichtung in Commerce](/help/commerce-cloud/cif-storefront/configuring/multi-store-setup.md)
* [Einrichtung mehrerer Commerce-Systeme](/help/commerce-cloud/cif-storefront/configuring/multiple-commerce-systems-setup.md)
