---
title: Integrieren der Remote-Version von AEM Assets mit AEM Sites
description: Erfahren Sie, wie Sie AEM Sites mit genehmigtem AEM Assets konfigurieren und verbinden.
exl-id: 382e6166-3ad9-4d8f-be5c-55a7694508fa
source-git-commit: ed7331647ea2227e6047e42e21444b743ee5ce6d
workflow-type: tm+mt
source-wordcount: '1029'
ht-degree: 15%

---

# Integrieren der Remote-Version von AEM Assets mit AEM Sites  {#integrate-approved-assets}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

>[!AVAILABILITY]
>
>Handbuch zu Dynamic Media mit OpenAPI-Funktionen ist jetzt im PDF-Format verfügbar. Laden Sie das gesamte Handbuch herunter und verwenden Sie den Adobe Acrobat AI-Assistenten, um Ihre Fragen zu beantworten.
>
>[!BADGE Handbuch für Dynamic Media mit OpenAPI-Funktionen PDF]{type=Informative url="https://helpx.adobe.com/content/dam/help/en/experience-manager/aem-assets/dynamic-media-with-openapi-capabilities.pdf"}

Die effektive Verwaltung digitaler Assets ist für die Bereitstellung ansprechender und konsistenter Markenerlebnisse auf verschiedenen Online-Plattformen von entscheidender Bedeutung. Dynamic Media mit OpenAPI-Funktionen verbessern die Verwaltung digitaler Assets, indem eine nahtlose Integration zwischen AEM Sites und AEM Assets as a Cloud Service ermöglicht wird. Mit dieser innovativen Funktion können Sie verschiedene Arten genehmigter digitaler Assets in mehreren AEM-Umgebungen freigeben und verwalten und so Workflows für Sites-Autoren und Inhaltseditoren optimieren.

Dynamic Media mit OpenAPI-Funktionen ermöglichen es Sites-Autoren, Assets aus Remote-DAM direkt im AEM Seiteneditor und im [Inhaltsfragment](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments.html?lang=de) zu verwenden, was die Inhaltserstellung und -verwaltung vereinfacht.

Benutzer können mehrere AEM Sites-Instanzen ohne Einschränkung der Höchstanzahl mit einer Remote-DAM-Bereitstellung verbinden. Dies ist ein wichtiger Vorteil gegenüber der Funktion [Connected Assets](use-assets-across-connected-assets-instances.md) .

![Bild](/help/assets/assets/connected-assets-rdam.png)

Nach der ersten Einrichtung können Benutzer Seiten in der AEM Sites-Instanz erstellen und nach Bedarf Assets hinzufügen. Beim Hinzufügen von Assets können sie entweder in ihrem lokalen DAM gespeicherte Assets auswählen oder die im Remote-DAM verfügbaren Assets durchsuchen und verwenden.

Dynamic Media mit OpenAPI-Funktionen bieten verschiedene weitere Vorteile, z. B. den Zugriff auf und die Verwendung von Remote-Assets im Inhaltsfragment, das Abrufen von Metadaten der Remote-Assets und vieles mehr. Erfahren Sie mehr über die anderen [Vorteile von Dynamic Media mit OpenAPI-Funktionen im Vergleich zu Connected Assets](/help/assets/dynamic-media-open-apis-faqs.md).

## Vorbereitung {#pre-requisites-sites-integration}

Für die Unterstützung von Remote-Assets mit Dynamic Media mit OpenAPI-Funktionen ist Folgendes erforderlich:

* AEM 6.5 SP 18+ oder AEM as a Cloud Service

* Kernkomponenten, Version 2.23.2 oder höher

* Richten Sie die folgenden [Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md#add-variables) für AEM as a Cloud Service ein:

   * ASSET_DELIVERY_REPOSITORY_ID= &quot;delivery-pxxxxx-eyyyy.adobeaemcloud.com&quot; <br>
     `pXXXX` bezeichnet die Programm-ID <br>
     `eYYYY` bezeichnet die Umgebungs-ID

  Diese Variablen werden über die Cloud Manager-Benutzeroberfläche der AEM as a Cloud Service-Umgebung festgelegt, die als Ihre lokale Sites-Instanz fungiert.

   * ASSET_DELIVERY_IMS_CLIENT= [IMSClientId]: Sie müssen ein Adobe-Supportticket senden, um die IMS-Client-ID zu erhalten.

     oder konfigurieren Sie die [OSGi-Einstellungen](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi.html) für AEM 6.5 in der AEM Sites-Instanz, indem Sie die folgenden Schritte ausführen:

   1. Melden Sie sich bei der Konsole an und klicken Sie auf **[!UICONTROL OSGi] >** oder
Verwenden Sie die direkte URL, z. B.: `https://localhost:4502/system/console/configMgr`

   1. Konfigurieren Sie die OSGi-Konfiguration **Dynamic Media-Konfiguration der nächsten Generation** (`NextGenDynamicMediaConfigImpl`) wie folgt und ersetzen Sie die Werte durch die Ihrer Remote-Asset-Umgebung.

      ```text
        imsClient="<ims-client-ID>"
        enabled=B"true"
        imsOrg="<ims-org>@AdobeOrg"
        repositoryId="<repo-id>.adobeaemcloud.com"
      ```

      `imsOrg` ist keine obligatorische Eingabe.
      `repositoryId` = &quot;delivery-pxxx-eyyyyy.adobeaemcloud.com&quot;
wobei `pXXXX` auf die Programm-ID verweist
      `eYYYY` bezeichnet die Umgebungs-ID

      ![Das OSGi-Konfigurationsfenster von Next Generation Dynamic Media](/help/assets/assets/remote-assets-osgi.png)

  Erfahren Sie mehr über die [IMS-Authentifizierung](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/ims-config-and-admin-console.html).

  Weitere Informationen zum Konfigurieren von OSGi finden Sie in den folgenden Dokumenten:

   * [Konfigurieren von OSGi für Adobe Experience Manager as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html?lang=de) für AEM as a Cloud Service
   * [Konfigurieren von OSGi](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/configuring/configuring-osgi.html?lang=de) für AEM 6.5

* IMS-Zugriff zur Anmeldung bei der Remote-DAM-AEM as a Cloud Service-Instanz. Er bezieht sich auf den Sites-Autor, der über IMS-Zugriff auf die Remote-DAM-Umgebung verfügt.

* Konfigurieren Sie die Bildv3-Komponente in der AEM Sites-Instanz. Wenn die Komponente nicht vorhanden ist, laden Sie das [Inhaltspaket](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.23.0) herunter und installieren Sie es.

## Konfigurieren von HTTPS {#https}

Es wird allgemein empfohlen, alle Ihre Produktions-AEM-Instanzen mithilfe von HTTPS auszuführen. Ihre lokalen Entwicklungsumgebungen sind jedoch möglicherweise nicht als solche eingerichtet. Damit Remote-Assets von Dynamic Media mit OpenAPI funktionieren, ist jedoch HTTPS erforderlich.

[Verwenden Sie dieses Handbuch](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/security/use-the-ssl-wizard.html?lang=de), um HTTPS zu konfigurieren, wo immer Sie Remote-Assets verwenden möchten, einschließlich Entwicklungsumgebungen.

## Zugreifen auf Assets über Remote DAM {#fetch-assets}

Mit Dynamic Media mit OpenAPI-Funktionen können Sie auf Assets zugreifen, die in Ihrer Remote-DAM-Instanz im lokalen AEM Sites-Seiteneditor und AEM Inhaltsfragment verfügbar sind.

![Bild](/help/assets/assets/open-APIs.png)

### Zugreifen auf Remote-Assets im AEM Seiteneditor {#access-assets-page-editor}

Führen Sie die folgenden Schritte aus, um Remote-Assets im Seiteneditor AEM AEM Sites-Instanz zu verwenden. Sie können diese Integration in AEM as a Cloud Service und AEM 6.5 durchführen.

1. Wechseln Sie zu **[!UICONTROL Sites]** > _Ihre Website_, auf der die AEM **[!UICONTROL Seite]** vorhanden ist, in der Sie das Remote-Asset hinzufügen müssen.
1. Wählen Sie die Seite aus und klicken Sie auf **[!UICONTROL Bearbeiten (_e_)]**. Der AEM **[!UICONTROL Seiten-Editor]** wird geöffnet.
1. Klicken Sie auf den Layout-Container und fügen Sie eine Komponente **[!UICONTROL Bild]** hinzu.
1. Klicken Sie auf die Komponente **[!UICONTROL Bild]** und dann auf das Symbol ![Einstellungen](/help/assets/assets/do-not-localize/settings-icon.svg) .
1. Deaktivieren Sie die Option **[!UICONTROL Eigenes Bild von Seite übernehmen]** .
1. Klicken Sie auf **[!UICONTROL Auswählen]** und wählen Sie **[!UICONTROL Remote]** aus.
   ![Bild](/help/assets/assets/uncheck-inherit-option.jpg)

   Sie werden aufgefordert, sich anzumelden.
1. Wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Auswählen]**.
1. Fügen Sie einen Alternativtext hinzu und klicken Sie auf **[!UICONTROL Fertig]**.
   <br> Das Remote-Asset wird in der Bildkomponente angezeigt. Sie können auch die Bereitstellungs-URL des Assets überprüfen, wenn es auf der Seite geladen wird, oder indem Sie den Tab &quot;Vorschau&quot;verwenden. Die Bereitstellungs-URL gibt an, dass auf das Asset remote zugegriffen wird.

Sie können im Seiteneditor standardmäßig nur auf Remote-Assets zugreifen, die für die Bild-Kernkomponente v3 und die Teaser-Kernkomponente v2 AEM sind. Für andere Komponenten, einschließlich benutzerdefinierter Komponenten, sind Anpassungen erforderlich, um die Asset-Auswahl mit diesen Komponenten zu integrieren.

#### Video: Zugriff auf Remote-Assets im AEM Seiteneditor

>[!VIDEO](https://video.tv.adobe.com/v/3427666)

### Zugreifen auf Remote-Assets in AEM Inhaltsfragment {#access-assets-content-fragment}

Führen Sie die folgenden Schritte aus, um Remote-Assets in AEM Inhaltsfragment in Ihrer AEM Sites-Instanz zu verwenden. Sie können diese Integration in AEM 6.5 und nicht in AEM as a Cloud Service durchführen.

1. Navigieren Sie zu **[!UICONTROL Assets]** > **[!UICONTROL Dateien]**.
1. Wählen Sie den Asset-Ordner aus, in dem das Inhaltsfragment vorhanden ist.
1. Wählen Sie das Inhaltsfragment aus und klicken Sie auf **[!UICONTROL Bearbeiten (_e_)]**.

   >[!NOTE]
   >
   Wenn Sie nicht über AEM Inhaltsfragmentmodell verfügen, müssen Sie möglicherweise [ein](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments-models.html?lang=en) erstellen.

1. Klicken Sie auf das Symbol ![Häkchen](/help/assets/assets/do-not-localize/checkmark-icon.svg) neben der Textkomponente.
1. Wählen Sie **[!UICONTROL Remote]** aus, um das Asset aus dem Remote-DAM abzurufen. <br>
Sie können je nach Bedarf entweder das DAM-Repository **[!UICONTROL Lokal]** oder das DAM-Repository **[!UICONTROL Remote]** auswählen.

   ![image](/help/assets/assets/cf-pick.jpg)
Sie werden aufgefordert, sich anzumelden.
1. Wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Auswählen]**.
   <br> Die Remote-Asset-URL wird in der Textkomponente angezeigt.

#### Video: Zugriff auf Remote-Assets in AEM Inhaltsfragment

>[!VIDEO](https://video.tv.adobe.com/v/3427667)

### Zugreifen auf Remote-Assets in Edge Delivery Services {#access-assets-eds}

Sie können auch auf Remote-Assets in Edge Delivery Services zugreifen. Weitere Informationen finden Sie unter [Verwenden von Assets aus Assets as a Cloud Service, die mit Dynamic Media mit OpenAPI-Funktionen bereitgestellt werden](https://www.aem.live/docs/aem-assets-sidekick-plugin#utilizing-assets-from-assets-cloud-services-delivered-via-dynamic-media-with-openapi).
