---
title: Integrieren des Asset-Wählers mithilfe von Vanilla JS
description: Integrieren Sie den Asset-Wähler in verschiedene Adobe-, Adobe-fremde- und Drittanbieter-Anwendungen.
role: Admin, User
exl-id: 1c0051a3-549c-4783-9fc1-594f424a70c3
source-git-commit: 08fc43bc8edeea91bfeb01f053d435e136658e7f
workflow-type: ht
source-wordcount: '225'
ht-degree: 100%

---

# Integrieren des Asset-Wählers mithilfe von Vanilla JS {#integration-using-vanilla-js}

<table>
    <tr>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/dm-prime-ultimate.md"><b>Dynamic Media Prime und Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/assets-ultimate-overview.md"><b>AEM Assets Ultimate</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/integrate-aem-assets-edge-delivery-services.md"><b>AEM Assets-Integration mit Edge Delivery Services</b></a>
        </td>
        <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/aem-assets-view-ui-extensibility.md"><b>Erweiterbarkeit der Benutzeroberfläche</b></a>
        </td>
          <td>
            <sup style= "background-color:#008000; color:#FFFFFF; font-weight:bold"><i>Neu</i></sup> <a href="/help/assets/dynamic-media/enable-dynamic-media-prime-and-ultimate.md"><b>Aktivieren von Dynamic Media Prime und Ultimate</b></a>
        </td>
    </tr>
    <tr>
        <td>
            <a href="/help/assets/search-best-practices.md"><b>Best Practices für die Suche</b></a>
        </td>
        <td>
            <a href="/help/assets/metadata-best-practices.md"><b>Best Practices für Metadaten</b></a>
        </td>
        <td>
            <a href="/help/assets/product-overview.md"><b>Content Hub</b></a>
        </td>
        <td>
            <a href="/help/assets/dynamic-media-open-apis-overview.md"><b>Dynamic Media mit OpenAPI-Funktionen</b></a>
        </td>
        <td>
            <a href="https://developer.adobe.com/experience-cloud/experience-manager-apis/"><b>Entwicklerdokumentation zu AEM Assets</b></a>
        </td>
    </tr>
</table>

Sie können jede [!DNL Adobe]- oder Nicht-Adobe-Anwendung mit dem [!DNL Experience Manager Assets]-Repository integrieren und Assets aus der Anwendung heraus auswählen. Siehe [Integration des Asset-Wählers mit verschiedenen Anwendungen](#asset-selector-integration-with-apps).

Die Integration erfolgt durch den Import des Asset-Selektor-Pakets und die Verbindung zu Assets as a Cloud Service unter Verwendung der Vanilla JavaScript-Bibliothek. Bearbeiten Sie eine Datei `index.html` oder eine andere geeignete Datei innerhalb Ihrer Anwendung, um:

* Authentifizierungsdetails zu definieren
* Zugriff auf das Assets as a Cloud Service-Repository zu erhalten
* Anzeigeeigenschaften des Asset-Selektors zu konfigurieren

Sie können eine Authentifizierung durchführen, ohne einige der IMS-Eigenschaften zu definieren, wenn:

* Sie eine [!DNL Adobe]-Applikation auf [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=de) integrieren.
* Für die Authentifizierung wurde bereits ein IMS-Token generiert.

## Integrieren des Asset-Wählers mit verschiedenen Anwendungen {#asset-selector-integration-with-apps}

Sie können den Asset-Wähler mit verschiedenen Anwendungen integrieren, z. B.:

* [Integrieren des Asset-Wählers mit einer [!DNL Adobe] -Anwendung](/help/assets/integrate-asset-selector-adobe-app.md)
* [Integrieren des Asset-Wählers mit einer Nicht-Adobe-Anwendung](/help/assets/integrate-asset-selector-non-adobe-app.md)
* [Integrieren in Dynamic Media mit OpenAPI-Funktionen](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)


>[!MORELIKETHIS]
>
>* [Anpassungen des Asset-Wählers](/help/assets/asset-selector-customization.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
>* [Integrieren des Asset-Wählers in Dynamic Media mit OpenAPI-Funktionen](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
