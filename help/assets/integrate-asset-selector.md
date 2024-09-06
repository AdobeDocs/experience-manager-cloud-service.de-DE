---
title: Asset-Selektor für [!DNL Adobe Experience Manager] als ein [!DNL Cloud Service]
description: Integrieren Sie die Asset-Auswahl in verschiedene Adobe-, Nicht-Adobe- und Drittanbieter-Anwendungen.
role: Admin, User
source-git-commit: fb1350c91468f9c448e34b66dc938fa3b5a3e9a9
workflow-type: tm+mt
source-wordcount: '176'
ht-degree: 86%

---


# Integrieren des Asset-Wählers mithilfe von Vanilla JS {#integration-using-vanilla-js}

Sie können jede [!DNL Adobe]- oder Nicht-Adobe-Anwendung mit dem [!DNL Experience Manager Assets]-Repository integrieren und Assets aus der Anwendung heraus auswählen. Siehe [Integration des Asset-Wählers mit verschiedenen Anwendungen](#integrate-asset-selector.md).

Die Integration erfolgt durch den Import des Asset-Selektor-Pakets und die Verbindung zu Assets as a Cloud Service unter Verwendung der Vanilla JavaScript-Bibliothek. Bearbeiten Sie eine Datei `index.html` oder eine andere geeignete Datei innerhalb Ihrer Anwendung, um:

* Authentifizierungsdetails zu definieren
* Zugriff auf das Assets as a Cloud Service-Repository zu erhalten
* Anzeigeeigenschaften des Asset-Selektors zu konfigurieren

Sie können eine Authentifizierung durchführen, ohne einige der IMS-Eigenschaften zu definieren, wenn:

* Sie eine [!DNL Adobe]-Applikation auf [Unified Shell](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/overview/aem-cloud-service-on-unified-shell.html?lang=de) integrieren.
* Für die Authentifizierung wurde bereits ein IMS-Token generiert.

## Integrieren des Asset-Wählers mit verschiedenen Anwendungen {#asset-selector-integration-with-apps}

Sie können den Asset-Wähler mit verschiedenen Anwendungen integrieren, z. B.:

* [Integrieren des Asset-Wählers mit einer [!DNL Adobe] -Anwendung](#integrate-asset-selector.md)
* [Integrieren des Asset-Wählers mit einer Nicht-Adobe-Anwendung](#integrate-asset-selector-non-adobe.md)
* [Integrieren in Dynamic Media mit OpenAPI-Funktionen](#integrate-asset-selector-dynamic-media-open-api.md)


>[!MORELIKETHIS]
>
>* [Anpassung der Asset-Auswahl](/help/assets/asset-selector-customization.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
>* [Integrieren der APIs zum Öffnen dynamischer Medien in der Asset-Auswahl](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)

