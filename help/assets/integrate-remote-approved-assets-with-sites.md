---
title: Integrieren der Remote-Version von AEM Assets mit AEM Sites
description: Erfahren Sie im Creative Cloud, wie Sie AEM Sites mit der genehmigten AEM Assets konfigurieren und verbinden.
source-git-commit: f6c0e8e5c1d7391011ccad5aa2bad4a6ab7d10c3
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 2%

---


# Integrieren der Remote-Version von AEM Assets mit AEM Sites  {#integrate-approved-assets}

Die effektive Verwaltung digitaler Assets ist für die Bereitstellung ansprechender und konsistenter Markenerlebnisse auf verschiedenen Online-Plattformen von entscheidender Bedeutung. Dynamic Media mit OpenAPI-Funktionen verbessern die Verwaltung digitaler Assets, indem eine nahtlose Integration zwischen AEM Sites und AEM Assets as a Cloud Service ermöglicht wird. Mit dieser innovativen Funktion können Sie verschiedene Arten genehmigter digitaler Assets in mehreren AEM-Umgebungen freigeben und verwalten und so Workflows für Sites-Autoren und Inhaltseditoren optimieren.

Dynamic Media mit OpenAPI-Funktionen ermöglichen es Sites-Autoren, Assets aus Remote-DAM direkt im AEM Seiteneditor und im [Inhaltsfragment](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments.html?lang=de) zu verwenden, was die Inhaltserstellung und -verwaltung vereinfacht.

Benutzer können mehrere AEM Sites-Instanzen ohne Einschränkung der Höchstanzahl mit einer Remote-DAM-Bereitstellung verbinden. Dies ist ein wichtiger Vorteil gegenüber der Funktion [Connected Assets](use-assets-across-connected-assets-instances.md) .

![Bild](/help/assets/assets/connected-assets-rdam.png)

Nach der ersten Einrichtung können Benutzer Seiten in der AEM Sites-Instanz erstellen und nach Bedarf Assets hinzufügen. Beim Hinzufügen von Assets können sie entweder in ihrem lokalen DAM gespeicherte Assets auswählen oder die im Remote-DAM verfügbaren Assets durchsuchen und verwenden.

Dynamic Media mit OpenAPI-Funktionen bieten verschiedene weitere Vorteile, z. B. den Zugriff auf und die Verwendung von Remote-Assets im Inhaltsfragment, das Abrufen von Metadaten der Remote-Assets und vieles mehr. Erfahren Sie mehr über die anderen [Vorteile von Dynamic Media mit OpenAPI-Funktionen im Vergleich zu Connected Assets](/help/assets/dynamic-media-open-apis-faqs.md).

## Vorbereitung {#pre-requisits-sites-integration}

* Richten Sie die folgenden [Umgebungsvariablen](/help/implementing/cloud-manager/environment-variables.md#add-variables) für AEM as a Cloud Service ein:

   * ASSET_DELIVERY_REPOSITORY_ID= &quot;delivery-pxxxxx-eyyyy.adobeaemcloud.com&quot; <br>
     `pXXXX` bezeichnet die Programm-ID <br>
     `eYYYY` bezeichnet die Umgebungs-ID

   * ASSET_DELIVERY_IMS_CLIENT= [IMSClientId]

  oder konfigurieren Sie die [OSGi-Einstellungen](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/configuring/configuring-osgi.html) für AEM 6.5 in der AEM Sites-Instanz, indem Sie die folgenden Schritte ausführen:

   1. Melden Sie sich bei der Konsole an und klicken Sie auf **[!UICONTROL OSGi] >** oder
Verwenden Sie die direkte URL, z. B.: `http://localhost:4502/system/console/configMgr`

   1. Fügen Sie die **[!UICONTROL repositoryID]**= &quot;delivery-pxxx-eyyyyy.adobeaemcloud.com&quot; und **[!UICONTROL imsClient]**= [IMSClientId] hinzu.
Erfahren Sie mehr über die [IMS-Authentifizierung](https://experienceleague.adobe.com/docs/experience-manager-65/content/security/ims-config-and-admin-console.html).

* IMS-Zugriff zur Anmeldung bei der Remote-DAM-AEM as a Cloud Service-Instanz.

* Schalten Sie die Dynamic Media mit OpenAPI-Funktionen ein, um im Remote-DAM zu wechseln.

* Konfigurieren Sie die Bildv3-Komponente in der AEM Sites-Instanz. Wenn die Komponente nicht vorhanden ist, laden Sie das [Inhaltspaket](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.23.0) herunter und installieren Sie es.

## Zugreifen auf Assets über Remote DAM {#fetch-assets}

Mit Dynamic Media mit OpenAPI-Funktionen können Sie auf Assets zugreifen, die in Ihrer Remote-DAM-Instanz im lokalen AEM Sites-Seiteneditor und AEM Inhaltsfragment verfügbar sind.

![Bild](/help/assets/assets/open-APIs.png)

### Zugreifen auf Remote-Assets im AEM Seiteneditor {#access-assets-page-editor}

Führen Sie die folgenden Schritte aus, um Remote-Assets im Seiteneditor AEM AEM Sites-Instanz zu verwenden. Sie können diese Integration in AEM as a Cloud Service und AEM 6.5 durchführen.

1. Wechseln Sie zu **[!UICONTROL Sites]** > _Ihre Website_, auf der die AEM **[!UICONTROL Seite]** vorhanden ist, in der Sie das Remote-Asset hinzufügen müssen.
1. Navigieren Sie in Ihrer Website zur gewünschten AEM **[!UICONTROL Seite]** unter dem Abschnitt **[!UICONTROL Sites]** , wo Sie das Remote-Asset hinzufügen möchten.
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
   >Wenn Sie nicht über AEM Inhaltsfragmentmodell verfügen, müssen Sie möglicherweise [ein](https://experienceleague.adobe.com/docs/experience-manager-65/content/assets/content-fragments/content-fragments-models.html?lang=en) erstellen.

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
