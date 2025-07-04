---
title: Integrieren des Asset-Wählers mithilfe von Vanilla JS
description: Integrieren Sie den Asset-Wähler in verschiedene Adobe-, Adobe-fremde- und Drittanbieter-Anwendungen.
role: Admin, User
exl-id: 1c0051a3-549c-4783-9fc1-594f424a70c3
source-git-commit: 32fdbf9b4151c949b307d8bd587ade163682b2e5
workflow-type: ht
source-wordcount: '179'
ht-degree: 100%

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
>* [Anpassungen des Asset-Wählers](/help/assets/asset-selector-customization.md)
>* [Eigenschaften des Asset-Wählers](/help/assets/asset-selector-properties.md)
>* [Integrieren des Asset-Wählers in Dynamic Media mit OpenAPI-Funktionen](/help/assets/integrate-asset-selector-dynamic-media-open-api.md)
