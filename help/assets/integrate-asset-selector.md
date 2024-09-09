---
title: Asset-Selektor für [!DNL Adobe Experience Manager] als ein [!DNL Cloud Service]
description: Integrieren Sie die Asset-Auswahl in verschiedene Adobe-, Nicht-Adobe- und Drittanbieter-Anwendungen.
role: Admin, User
exl-id: 1c0051a3-549c-4783-9fc1-594f424a70c3
source-git-commit: 575980320c1dbd32f799bf9c2fddf3d6773c838a
workflow-type: tm+mt
source-wordcount: '178'
ht-degree: 85%

---

# Integrieren des Asset-Wählers mithilfe von Vanilla JS {#integration-using-vanilla-js}

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
>* [Asset-Selektor-Anpassungen](/help/assets/asset-selector-customization.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
>* [Integrieren der Asset-Auswahl in Dynamic Media mit OpenAPI-Funktionen](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
