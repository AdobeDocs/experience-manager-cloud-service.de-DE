---
title: Wesentliche Änderungen an Adobe Experience Manager Assets as a Cloud Service
description: Wesentliche Änderungen an Adobe Experience Manager Assets in AEM Cloud Service im Vergleich zu Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 37ff6912837ba78c90526e8f8322b9002e9a4304
workflow-type: tm+mt
source-wordcount: '541'
ht-degree: 100%

---


# Wesentliche Änderungen an Adobe Experience Manager Assets as a Cloud Service {#notable-changes}

Adobe Experience Manager as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für die Verwaltung Ihrer AEM-Projekte. Allerdings gibt es viele Unterschiede zwischen der On-Premise- und der über Adobe Managed Service bereitgestellten Version von Adobe Experience Manager Assets und Adobe Experience Manager as a Cloud Service. In diesem Dokument werden die wichtigen Unterschiede bei den Asset-Funktionen verdeutlicht. Weitere Änderungen finden Sie im Abschnitt zu den allgemeinen [Änderungen an Adobe Experience Manager as a Cloud Service](/help/release-notes/aem-cloud-changes.md).

Die Hauptunterschiede gegenüber Adobe Experience Manager 6.5 bestehen in den folgenden Bereichen:

* [Asset-Aufnahme und -Upload](#asset-ingestion).
* [Asset-Microservices für die Cloud-Verarbeitung](#asset-microservices).
* [Entfernung der klassischen Benutzeroberfläche](#classic-ui).

## Asset-Erfassung und -Upload {#asset-ingestion}

Das Hochladen von Assets wurde auf Effizienz optimiert, indem eine bessere Skalierung der Asset-Aufnahme und schnellere Uploads ermöglicht werden. Produktfunktionen (Web-Benutzeroberflächen, Desktopclients) wurden aktualisiert. Dies kann sich jedoch auf einige bestehende Anpassungen auswirken.

* Adobe Experience Manager wendet das Prinzip des direkten binären Zugriffs für den Upload und Download sowie für Asset-Microservices zur Asset-Verarbeitung an. Siehe [Übersicht über die Asset-Erfassung](/help/assets/asset-microservices-overview.md)..
   * Asset-Upload [mit direktem Binärzugriff](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Weitere technische Daten finden Sie im Abschnitt [Protokoll und APIs für den direkten Binär-Upload](/help/assets/developer-reference-material-apis.md#overview-binary-upload).
* Der Standard-Workflow **[!UICONTROL DAM-Update-Asset]** vorheriger AEM-Versionen ist nicht mehr verfügbar. Stattdessen bieten Asset-Microservices einen skalierbaren, jederzeit nutzbaren Service, der den Großteil der standardmäßigen Asset-Verarbeitung (Ausgabeformate, Metadatenextraktion, Textextraktion für die Indizierung) abdeckt..
   * Siehe [Konfigurieren und Verwenden von Asset Microservices](/help/assets/asset-microservices-configure-and-use.md).
   * Um bei der Verarbeitung benutzerdefinierte Workflow-Schritte durchzuführen, können Sie [Nachbearbeitungsarbeitsabläufe](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) verwenden..
* Für Assets, die über Package Manager eingehen, ist eine manuelle erneute Verarbeitung mithilfe der Aktion **[!UICONTROL Assets erneut verarbeiten]** über die AEM Assets-Benutzeroberfläche erforderlich.

Mit Asset-Microservices generierte Standardausgabeformate werden in abwärtskompatibler Form im Asset-Repository-Knoten gespeichert (gleiche Benennungskonventionen).

## Entwickeln und Testen von Asset-Microservices {#asset-microservices}

Asset-Microservices bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud Services. Adobe verwaltet die Cloud Services für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen. Asset-Microservices helfen dabei, die Notwendigkeit von Rendering-Tools und -Methoden von Drittanbietern (wie ImageMagick) zu vermeiden, die Konfiguration des Systems zu vereinfachen und sofort einsatzbereite Funktionen für gängige Dateitypen bereitzustellen. Sie können jetzt eine [breite Palette von Dateitypen](/help/assets/file-format-support.md) verarbeiten, die mehr Formate standardmäßig abdecken, als dies mit früheren Versionen von Experience Manager möglich war. Beispielsweise ist jetzt das Extrahieren von Miniaturansichten von PSD- und PSB-Formaten möglich, für die zuvor Lösungen von Drittanbietern wie ImageMagick erforderlich waren. Sie können die komplexen Konfigurationen von ImageMagick nicht für die Konfiguration von [!UICONTROL Verarbeitungsprofilen] verwenden. Verwenden Sie [!DNL Dynamic Media] auch für die FFmpeg-Transcodierung von Videos.

Asset-Microservices sind ein Cloud-nativer Dienst, der in Kundenprogrammen und -umgebungen, die in Cloud Manager verwaltet werden, automatisch bereitgestellt und mit Adobe Experience Manager vernetzt wird. Um Experience Manager zu erweitern oder anzupassen, können Entwickler den vorhandenen Inhalt (oder Assets mit in einer Cloud-Umgebung generierten Ausgabeformate) verwenden, um ihren Code zu testen und zu validieren, indem sie Assets verwenden, anzeigen und herunterladen.

Implementieren Sie für eine umfassende Validierung des Codes und des Prozesses, einschließlich der Erfassung und Verarbeitung von Assets, die Code-Änderungen in einer Cloud-Entwicklungsumgebung unter Verwendung der [Pipeline](/help/implementing/cloud-manager/configure-pipeline.md) und testen Sie mit vollständiger Ausführung der Asset-Microservice-Verarbeitung.

## Entfernung der klassischen Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche ist in Adobe Experience Manager as a Cloud Service nicht mehr verfügbar. Die Standardoberfläche ist die Touch-optimierte Benutzeroberfläche.
