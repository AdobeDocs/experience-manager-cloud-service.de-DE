---
title: Wesentliche Änderungen an Adobe Experience Manager Assets as a Cloud Service
description: Die Änderungen an Adobe Experience Manager-Assets im AEM Cloud-Dienst im Vergleich zu Adobe Experience Manager 6.5 sind erheblich.
translation-type: tm+mt
source-git-commit: 0686acbc61b3902c6c926eaa6424828db0a6421a

---


# Wesentliche Änderungen an Adobe Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für die Verwaltung Ihrer AEM-Projekte. Es gibt jedoch viele Unterschiede zwischen Experience Manager Assets vor Ort oder in Adobe Managed Service im Vergleich zu Experience Manager als Cloud-Dienst. In diesem Dokument werden die wichtigen Unterschiede bei den Asset-Funktionen hervorgehoben. For other changes, see the generic [changes to Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Die Hauptunterschiede gegenüber Adobe Experience Manager 6.5 bestehen in den folgenden Bereichen:

* [Asset-Erfassung und -Upload](#asset-ingestion).
* [Asset-Mikrodienste für die Cloud-Verarbeitung](#asset-microservices).
* [Entfernung der klassischen Benutzeroberfläche](#classic-ui).

## Asset-Erfassung und -Upload {#asset-ingestion}

Das Hochladen von Assets wurde für Effizienz optimiert, da die Asset-Erfassung besser skaliert und die Uploads beschleunigt werden konnten. Produktfunktionen (Web-Benutzeroberflächen, Desktopclients) wurden aktualisiert. Dies kann sich jedoch auf einige bestehende Anpassungen auswirken.

* Adobe Experience Manager wendet das Prinzip des direkten binären Zugriffs für den Upload und Download sowie für Asset-Microservices zur Asset-Verarbeitung an. Siehe [Übersicht über die Asset-Erfassung](/help/assets/asset-microservices-overview.md)..
   * Asset-Upload [mit direktem binären Zugriff](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * For technical details, see  of [direct binary upload protocol and APIs](/help/assets/developer-reference-material-apis.md#overview-binary-upload).
* Der Standard-Workflow **[!UICONTROL DAM-Update-Asset]** vorheriger AEM-Versionen ist nicht mehr verfügbar. Stattdessen bieten Asset-Microservices einen skalierbaren, jederzeit nutzbaren Service, der den Großteil der standardmäßigen Asset-Verarbeitung (Ausgabeformate, Metadatenextraktion, Textextraktion für die Indizierung) abdeckt..
   * Siehe [Konfigurieren und Verwenden von Asset Microservices](/help/assets/asset-microservices-configure-and-use.md).
   * Um bei der Verarbeitung benutzerdefinierte Workflow-Schritte durchzuführen, können Sie [Nachbearbeitungsarbeitsabläufe](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) verwenden..
* Assets that come in via Package Manager require manual reprocessing using the **[!UICONTROL Reprocess Asset]** action in the Assets interface.

Mit Asset-Microservices generierte Standardausgabeformate werden in abwärtskompatibler Form im Asset-Repository-Knoten gespeichert (gleiche Benennungskonventionen).

## Entwickeln und Testen von Asset-Microservices {#asset-microservices}

Asset Microservices bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud-Diensten. Adobe verwaltet die Cloud-Dienste für eine optimale Verarbeitung verschiedener Asset-Typen und Verarbeitungsoptionen. Mithilfe von Asset-Mikrodiensten können Sie die Notwendigkeit von Rendering-Werkzeugen und -Methoden von Drittanbietern (z. B. ImageMagick- und FFmpeg-Transkodierung) vermeiden und Konfigurationen vereinfachen. Gleichzeitig stehen Ihnen die standardmäßigen Funktionen für gängige Dateitypen zur Verfügung. Derzeit sind die ImageMagick-Integration und die FFMmpeg-Transkodierung in Cloud Service nicht verfügbar.

Asset Microservices ist ein Cloud-nativer Dienst, der automatisch für Experience Manager bereitgestellt wird und in Programmen und Umgebung, die in Cloud Manager verwaltet werden, verkabelt wird. Um Experience Manager zu erweitern oder anzupassen, können die Entwickler die vorhandenen Inhalte oder Assets mit in einer Cloud-Umgebung generierten Darstellungen verwenden, um ihren Code zu testen und zu validieren, indem sie Assets anzeigen, herunterladen.

To do an end-to-end validation of the code and process including asset ingestion and processing, deploy the code changes to a cloud-dev environment using [the pipeline](/help/implementing/cloud-manager/configure-pipeline.md) and test with full execution of asset microservices processing.

## Entfernung der klassischen Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche ist in Adobe Experience Manager as a Cloud Service nicht mehr verfügbar. Die Standardschnittstelle ist die Touch-aktivierte Benutzeroberfläche.
