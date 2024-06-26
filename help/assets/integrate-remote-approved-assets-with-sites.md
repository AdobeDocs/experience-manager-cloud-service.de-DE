---
title: Integrieren von Remote AEM Assets mit AEM Sites
description: Erfahren Sie im Creative Cloud, wie Sie AEM Sites mit der genehmigten AEM Assets konfigurieren und verbinden.
source-git-commit: f6c0e8e5c1d7391011ccad5aa2bad4a6ab7d10c3
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 1%

---


# Integrieren von Remote AEM Assets mit AEM Sites  {#integrate-approved-assets}

Die effektive Verwaltung digitaler Assets ist für die Bereitstellung ansprechender und konsistenter Markenerlebnisse auf verschiedenen Online-Plattformen von entscheidender Bedeutung. Dynamic Media mit OpenAPI-Funktionen verbessern die Verwaltung digitaler Assets, indem eine nahtlose Integration zwischen AEM Sites und AEM Assets as a Cloud Service ermöglicht wird. Mit dieser innovativen Funktion können Sie verschiedene Arten genehmigter digitaler Assets in mehreren AEM-Umgebungen freigeben und verwalten und so Workflows für Sites-Autoren und Inhaltseditoren optimieren.

Mit Dynamic Media mit OpenAPI-Funktionen können Sites-Autoren Assets aus Remote-DAM direkt im AEM Seiteneditor verwenden und [Inhaltsfragment](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments.html?lang=de), die die Inhaltserstellung und -verwaltung vereinfacht.

Benutzer können mehrere AEM Sites-Instanzen ohne Einschränkung der Höchstanzahl mit einer Remote-DAM-Bereitstellung verbinden, was einen erheblichen Vorteil gegenüber der [Connected Assets](use-assets-across-connected-assets-instances.md) Funktion.

![Bild](/help/assets/assets/connected-assets-rdam.png)

Nach der ersten Einrichtung können Benutzer Seiten in der AEM Sites-Instanz erstellen und nach Bedarf Assets hinzufügen. Beim Hinzufügen von Assets können sie entweder in ihrem lokalen DAM gespeicherte Assets auswählen oder die im Remote-DAM verfügbaren Assets durchsuchen und verwenden.

Dynamic Media mit OpenAPI-Funktionen bieten verschiedene weitere Vorteile, z. B. den Zugriff auf und die Verwendung von Remote-Assets im Inhaltsfragment, das Abrufen von Metadaten der Remote-Assets und vieles mehr. Weitere Informationen zur anderen [Vorteile von Dynamic Media mit OpenAPI-Funktionen gegenüber Connected Assets](/help/assets/dynamic-media-open-apis-faqs.md).

## Vorbereitung {#pre-requisits-sites-integration}

* Einrichten der folgenden [Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md#add-variables) für AEM as a Cloud Service:

   * ASSET_DELIVERY_REPOSITORY_ID= &quot;delivery-pxxxxx-eyyyy.adobeaemcloud.com&quot; <br>
     `pXXXX` bezieht sich auf die Programm-ID <br>
     `eYYYY` bezieht sich auf die Umgebungs-ID

   * ASSET_DELIVERY_IMS_CLIENT= [IMSClientId]

  oder konfigurieren Sie [OSGi-Einstellungen](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi.html) für AEM 6.5 in der AEM Sites-Instanz verwenden, indem Sie die folgenden Schritte ausführen:

   1. Melden Sie sich bei der Konsole an und klicken Sie auf **[!UICONTROL OSGi] >** oder die direkte URL verwenden, z. B.: `http://localhost:4502/system/console/configMgr`

   1. Fügen Sie die **[!UICONTROL repositoryID]**= &quot;delivery-pxxx-eyyyyy.adobeaemcloud.com&quot; und **[!UICONTROL imsClient]**= [IMSClientId]
Weitere Informationen [IMS-Authentifizierung](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/ims-config-and-admin-console.html).

* IMS-Zugriff zur Anmeldung bei der Remote-DAM-AEM as a Cloud Service-Instanz.

* Schalten Sie die Dynamic Media mit OpenAPI-Funktionen ein, um im Remote-DAM zu wechseln.

* Konfigurieren Sie die Bildv3-Komponente in der AEM Sites-Instanz. Wenn die Komponente nicht vorhanden ist, laden Sie die [Inhaltspaket](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.23.0).

## Zugreifen auf Assets über Remote DAM {#fetch-assets}

Mit Dynamic Media mit OpenAPI-Funktionen können Sie auf Assets zugreifen, die in Ihrer Remote-DAM-Instanz im lokalen AEM Sites-Seiteneditor und AEM Inhaltsfragment verfügbar sind.

![Bild](/help/assets/assets/open-APIs.png)

### Zugreifen auf Remote-Assets im AEM Seiteneditor {#access-assets-page-editor}

Führen Sie die folgenden Schritte aus, um Remote-Assets im Seiteneditor AEM AEM Sites-Instanz zu verwenden. Sie können diese Integration in AEM as a Cloud Service und AEM 6.5 durchführen.

1. Navigieren Sie zu **[!UICONTROL Sites]** > _Ihre Website_ wobei die AEM **[!UICONTROL Seite]** vorhanden ist, in dem Sie das Remote-Asset hinzufügen müssen.
1. Navigieren Sie zur jeweiligen AEM **[!UICONTROL Seite]** auf Ihrer Website unter **[!UICONTROL Sites]** -Abschnitt, in dem Sie das Remote-Asset hinzufügen möchten.
1. Wählen Sie die Seite aus und klicken Sie auf **[!UICONTROL Bearbeiten (_e_)]**. Die AEM **[!UICONTROL Seiten-Editor]** geöffnet.
1. Klicken Sie auf den Layout-Container und fügen Sie eine **[!UICONTROL Bild]** -Komponente.
1. Klicken Sie auf **[!UICONTROL Bild]** Komponente und klicken Sie ![Einstellungssymbol](/help/assets/assets/do-not-localize/settings-icon.svg) Symbol.
1. Deaktivieren Sie die **[!UICONTROL Eigenes Bild von Seite übernehmen]** -Option.
1. Klicks **[!UICONTROL Auswahl]** und wählen **[!UICONTROL Remote]**.
   ![Bild](/help/assets/assets/uncheck-inherit-option.jpg)

   Sie werden aufgefordert, sich anzumelden.
1. Wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Auswählen]**.
1. Alternativtext hinzufügen und klicken Sie auf **[!UICONTROL Fertig]**.
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
   >Wenn Sie nicht über AEM Inhaltsfragmentmodell verfügen, müssen Sie möglicherweise [Erstellen einer](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments-models.html?lang=en).

1. Klicken Sie auf ![Häkchen-Symbol](/help/assets/assets/do-not-localize/checkmark-icon.svg) neben der Textkomponente.
1. Auswählen **[!UICONTROL Remote]** , um das Asset aus dem Remote-DAM abzurufen. <br>
Sie können entweder **[!UICONTROL Lokal]** oder **[!UICONTROL Remote]** DAM-Repository basierend auf Ihren Anforderungen.

   ![image](/help/assets/assets/cf-pick.jpg)
Sie werden aufgefordert, sich anzumelden.
1. Wählen Sie das Asset aus und klicken Sie auf **[!UICONTROL Auswählen]**.
   <br> Die Remote-Asset-URL wird in der Textkomponente angezeigt.

#### Video: Zugriff auf Remote-Assets in AEM Inhaltsfragment

>[!VIDEO](https://video.tv.adobe.com/v/3427667)

### Zugreifen auf Remote-Assets in Edge Delivery Services {#access-assets-eds}

Sie können auch auf Remote-Assets in Edge Delivery Services zugreifen. Weitere Informationen finden Sie unter [Verwenden von Assets aus Assets as a Cloud Service, die mit Dynamic Media mit OpenAPI-Funktionen bereitgestellt werden](https://www.aem.live/docs/aem-assets-sidekick-plugin#utilizing-assets-from-assets-cloud-services-delivered-via-dynamic-media-with-openapi).
