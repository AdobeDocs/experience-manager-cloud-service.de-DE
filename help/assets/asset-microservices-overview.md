---
title: Verarbeiten von Assets mit Asset-Microservices
description: Verarbeiten Sie Ihre digitalen Assets mit Cloud-nativen und skalierbaren Microservices für die Asset-Verarbeitung.
contentOwner: AG
feature: Asset Compute Microservices, Asset Ingestion, Asset Processing
role: Architect, Admin
exl-id: 1e069b95-a018-40ec-be01-9a74ed883b77
source-git-commit: 9c1104f449dc2ec625926925ef8c95976f1faf3d
workflow-type: tm+mt
source-wordcount: '837'
ht-degree: 100%

---

# Übersicht über die Erfassung und Verarbeitung von Assets mit Asset-Microservices {#asset-microservices-overview}

Adobe Experience Manager as a [!DNL Cloud Service] bietet eine Cloud-native Möglichkeit, Experience Manager-Programme und -Funktionen zu nutzen. Eines der Schlüsselelemente dieser neuen Architektur ist die auf Asset-Microservices basierende Erfassung und Verarbeitung von Assets. Asset-Microservices bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud Services. Adobe verwaltet die Cloud Services für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen. Die wichtigsten Vorteile von Cloud-nativen Asset-Microservices sind:

* Skalierbare Architektur, die eine nahtlose Verarbeitung für ressourcenintensive Vorgänge ermöglicht.
* Effiziente Indizierung und Textextraktion, die die Leistung Ihrer Experience Manager-Umgebungen nicht beeinträchtigen.
* Minimieren des Bedarfs an Workflows zur Verarbeitung von Assets in der Experience Manager-Umgebung. Dadurch werden Ressourcen freigesetzt, die Belastung von Experience Manager minimiert und Skalierbarkeit gewährleistet.
* Verbesserte Ausfallsicherheit bei der Verarbeitung von Assets. Potenzielle Probleme beim Umgang mit atypischen Dateien, wie beschädigten oder extrem großen Dateien, wirken sich nicht mehr auf die Leistung der Bereitstellung aus.
* Vereinfachte Konfiguration der Asset-Verarbeitung für Administratoren.
* Die Einrichtung der Asset-Verarbeitung wird von Adobe verwaltet und gewartet, um eine optimale Konfiguration für die Handhabung von Ausgabedarstellungen, Metadaten und Textextraktion für verschiedene Dateitypen bereitzustellen.
* Gegebenenfalls werden native Adobe-Dateiverarbeitungs-Services verwendet, um eine Ausgabe mit hoher Wiedergabetreue und einen [effizienten Umgang mit proprietären Adobe-Formaten](file-format-support.md) zu ermöglichen.
* Möglichkeit, den Nachbearbeitungs-Workflow so zu konfigurieren, dass benutzerspezifische Aktionen und Integrationen hinzugefügt werden können.

Asset-Microservices helfen dabei, die Notwendigkeit von Rendering-Tools und -Methoden von Drittanbietern (wie [!DNL ImageMagick] und FFmpeg-Transkodierung) zu vermeiden, die Konfiguration des Systems zu vereinfachen und standardmäßig einfache Funktionen für gängige Dateitypen bereitzustellen.

## Umfangreiche Architektur {#asset-microservices-architecture}

Ein Architekturdiagramm zeigt die Schlüsselelemente für die Erfassung und Verarbeitung von Assets sowie den Fluss von Assets im gesamten System.

<!-- Proposed DRAFT diagram for asset microservices overview - see section "Asset processing - high-level diagram" in the PPTX deck

https://adobe-my.sharepoint.com/personal/gklebus_adobe_com/_layouts/15/guestaccess.aspx?guestaccesstoken=jexDC5ZnepXSt6dTPciH66TzckS1BPEfdaZuSgHugL8%3D&docid=2_1ec37f0bd4cc74354b4f481cd420e07fc&rev=1&e=CdgElS
-->

![Erfassung und Verarbeitung von Assets mit Asset-Microservices](assets/asset-microservices-overview.png "Erfassung und Verarbeitung von Assets mit Asset-Microservices")

Die wichtigsten Schritte der Erfassung und Verarbeitung mithilfe von Asset-Microservices sind:

* Clients wie Webbrowser oder Adobe Asset Link senden eine Upload-Anfrage an [!DNL Experience Manager] und beginnen mit dem Hochladen der Binärdatei direkt in den binären Cloud-Speicher.
* Nach Abschluss des direkten binären Uploads benachrichtigt der Client [!DNL Experience Manager].
* [!DNL Experience Manager] sendet eine Verarbeitungsanfrage an die Asset-Microservices. Der Inhalt der Anfrage hängt von der Konfiguration der Verarbeitungsprofile in [!DNL Experience Manager] ab, die angeben, welche Ausgabedarstellungen generiert werden sollen.
* Das Backend der Assets-Microservices empfängt die Anfrage und sendet sie je nach Anfrage an einen oder mehrere Microservices. Jeder Microservice greift direkt auf die ursprüngliche Binärdatei im binären Cloud-Speicher zu.
* Die Ergebnisse der Verarbeitung, z. B. Ausgabedarstellungen, werden im binären Cloud-Speicher gespeichert.
* Experience Manager wird benachrichtigt, dass die Verarbeitung abgeschlossen ist und direkte Verweise auf die generierten Binärdateien (Ausgabedarstellungen) vorhanden sind. Die generierten Ausgabedarstellungen sind in [!DNL Experience Manager] für das hochgeladene Asset verfügbar.

Dies ist der grundlegende Fluss der Asset-Erfassung und -Verarbeitung. Falls konfiguriert, kann Experience Manager auch ein benutzerdefiniertes Workflow-Modell starten, um die Nachbearbeitung des Assets durchzuführen. Führen Sie beispielsweise benutzerdefinierte Schritte aus, die spezifisch für Ihre Umgebung sind, wie z. B. das Abrufen von Informationen aus einem Unternehmenssystem und das Hinzufügen von Asset-Eigenschaften.

Der Aufnahme- und Verarbeitungsfluss sind Schlüsselkonzepte der Asset-Microservices-Architektur für Experience Manager.

* **Direkter Binärzugriff**: Assets werden nach der Konfiguration für Experience Manager-Umgebungen in den binären Cloud-Speicher übertragen (und hochgeladen). Anschließend erhalten [!DNL Experience Manager], Asset-Microservices und schließlich Clients direkten Zugriff auf sie, um ihre Arbeit auszuführen. Dadurch wird die Belastung der Netzwerke und die Duplizierung der gespeicherten Binärdateien minimiert.
* **Ausgelagerte Verarbeitung**: Die Verarbeitung von Assets erfolgt außerhalb der [!DNL Experience Manager]-Umgebung und hält deren Ressourcen (CPU, Speicher) für die Bereitstellung der wichtigsten Digital Asset Management (DAM)-Funktionen und die Unterstützung der interaktiven Arbeit mit dem System für Endanwender frei.

## Asset-Upload mit direktem Binärzugriff {#asset-upload-with-direct-binary-access}

Experience Manager-Clients, die Teil des Produktangebots sind, unterstützen standardmäßig alle Uploads mit direktem Binärzugriff. Dazu gehören das Hochladen über die Web-Oberfläche, Adobe Asset Link und das [!DNL Experience Manager]-Desktop-Programm.

Sie können benutzerdefinierte Upload-Tools verwenden, die direkt mit [!DNL Experience Manager]-HTTP-APIs funktionieren. Sie können diese APIs direkt verwenden oder die folgenden Open-Source-Projekte verwenden und erweitern, die das Upload-Protokoll implementieren:

* [Open-Source-Upload-Bibliothek](https://github.com/adobe/aem-upload)
* [Open-Source-Befehlszeilen-Tool](https://github.com/adobe/aio-cli-plugin-aem)

Weitere Informationen hierzu finden Sie unter [Hochladen von Assets](add-assets.md).

## Hinzufügen einer benutzerdefinierten Asset-Nachbearbeitung {#add-custom-asset-post-processing}

Während die Anforderungen an die Asset-Verarbeitung der meisten Kunden von den konfigurierbaren Asset-Microservices erfüllt werden, benötigen einige Kunden möglicherweise zusätzliche Asset-Verarbeitungsschritte. Dies gilt insbesondere dann, wenn Assets auf der Grundlage von Informationen aus anderen Systemen über Integrationen verarbeitet werden müssen. In solchen Fällen können benutzerdefinierte Workflows für die Nachbearbeitung verwendet werden.

Nachbearbeitungs-Workflows sind reguläre [!DNL Experience Manager]-Workflow-Modelle, die im [!DNL Experience Manager]-Workflow-Editor erstellt und verwaltet werden. Kunden können die Workflows so konfigurieren, dass zusätzliche Verarbeitungsschritte für ein Asset ausgeführt werden, einschließlich der verfügbaren vordefinierten Workflow-Schritte und benutzerdefinierter Workflows.

Adobe Experience Manager kann so konfiguriert werden, dass die Workflows nach Abschluss der Asset-Verarbeitung automatisch ausgelöst werden.

<!-- TBD asgupta, Engg: Create some asset-microservices-data-flow-diagram.
-->

**Siehe auch**

* [Assets übersetzen](translate-assets.md)
* [Assets-HTTP-API](mac-api-assets.md)
* [Von AEM Assets unterstützte Dateiformate](file-format-support.md)
* [Suchen von Assets](search-assets.md)
* [Connected Assets](use-assets-across-connected-assets-instances.md)
* [Asset-Berichte](asset-reports.md)
* [Metadatenschemata](metadata-schemas.md)
* [Herunterladen von Assets](download-assets-from-aem.md)
* [Verwalten von Metadaten](manage-metadata.md)
* [Suchfacetten](search-facets.md)
* [Verwalten von Sammlungen](manage-collections.md)
* [Massenimport von Metadaten](metadata-import-export.md)
* [Veröffentlichen von Assets in AEM und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md)

>[!MORELIKETHIS]
>
>* [Erste Schritte mit Asset-Microservices](asset-microservices-configure-and-use.md)
>* [Unterstützte Dateiformate](file-format-support.md)
>* [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/adobe-asset-link.html)
>* [[!DNL Experience Manager] -Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=de)
>* [Apache Oak-Dokumentation zum direkten Binärzugriff](https://jackrabbit.apache.org/oak/docs/features/direct-binary-access.html)
