---
title: Wichtige Änderungen in  [!DNL Adobe Experience Manager Assets] als a [!DNL Cloud Service]
description: Bemerkenswerte Änderungen zu [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] im Vergleich zu [!DNL Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: ed449eea146ec18bdc4d25ae4938f9a36180037d
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 44%

---


# Notable Änderungen zu [!DNL Experience Manager Assets] als [!DNL Cloud Service] {#notable-changes}

[!DNL Adobe Experience Manager] als  [!DNL Cloud Service] bringt viele neue Funktionen und Möglichkeiten zur Verwaltung Ihrer Experience Manager-Projekte. Es gibt viele Unterschiede zwischen [!DNL Experience Manager Assets] lokal oder als Adobe Managed Service gehostet im Vergleich zu [!DNL Experience Manager] als [!DNL Cloud Service]. In diesem Artikel werden die wichtigen Unterschiede bei den Funktionen von [!DNL Assets] hervorgehoben.

Die Hauptunterschiede zu [Experience Manager] 6.5 bestehen in den folgenden Bereichen:

* [Asset-Erfassung, -Upload und -Verarbeitung](#asset-ingestion).
* [Asset-Microservices für Cloud-native Verarbeitung](#asset-microservices).
* [Entfernung der klassischen Benutzeroberfläche](#classic-ui).

## Asset-Erfassung und -Verarbeitung {#asset-ingestion}

Das Hochladen von Assets wurde für die Effizienz optimiert, indem die Erfassung besser skaliert, Uploads beschleunigt, die Verarbeitung mithilfe von Mikrodiensten beschleunigt und Massenaufnahmen erfasst werden. Produktfunktionen (Webbenutzerschnittstellen, Desktop-Clients) werden aktualisiert. Dies kann sich auch auf einige bestehende Anpassungen auswirken.

* [!DNL Experience Manager] verwendet das Prinzip des direkten binären Zugriffs, um Assets hochzuladen und herunterzuladen, und verwendet Asset-Mikrodienste zur Verarbeitung von Assets. Siehe [Übersicht über Microservices](/help/assets/asset-microservices-overview.md).
   * Asset-Upload [mit direktem Binärzugriff](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Technische Details finden Sie unter [Direct Binary Upload-Protokoll und APIs](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Einen Vergleich der verfügbaren API-Methoden für grundlegende CRUD-Vorgänge finden Sie unter [APIs und Asset-Vorgänge](/help/assets/developer-reference-material-apis.md#use-cases-and-apis).
* Der Standardarbeitsablauf **[!UICONTROL DAM Asset Update]** in früheren Versionen von [!DNL Experience Manager] ist nicht mehr verfügbar. Stattdessen bieten Asset-Mikrodienste einen skalierbaren, leicht verfügbaren Dienst, der den Großteil der standardmäßigen Asset-Verarbeitung abdeckt (Darstellungen, Metadaten-Extraktion und Text-Extraktion für die Indizierung).
   * Siehe [Asset-Mikrodienste konfigurieren und verwenden](/help/assets/asset-microservices-configure-and-use.md)
   * Um benutzerdefinierte Workflow-Schritte in der Verarbeitung zu haben, können [Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) verwendet werden.
* Für Assets, die mit Package Manager hochgeladen werden, ist eine manuelle Neuverarbeitung mithilfe der Aktion **[!UICONTROL Asset]** in der [!DNL Assets]-Schnittstelle erforderlich.
* Ein digitales Asset ohne Erweiterung oder mit einer falschen Erweiterung wird nicht wie gewünscht verarbeitet. Beim Hochladen solcher Assets passiert beispielsweise nichts oder es kann ein falsches Profil für die Verarbeitung auf das Asset angewendet werden. Benutzer können die Binärdateien weiterhin im DAM speichern.

Mit Asset-Microservices generierte Standardausgabedarstellungen werden in abwärtskompatibler Form im Asset-Repository-Knoten gespeichert (gleiche Benennungskonventionen).

## Entwickeln und Testen von Asset-Microservices {#asset-microservices}

Asset-Microservices bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud Services. Adobe verwaltet die Cloud Services für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen. Asset-Microservices helfen dabei, die Notwendigkeit von Rendering-Tools und -Methoden von Drittanbietern (wie ImageMagick) zu vermeiden, die Konfiguration des Systems zu vereinfachen und sofort einsatzbereite Funktionen für gängige Dateitypen bereitzustellen. Sie können jetzt eine [breite Palette von Dateitypen](/help/assets/file-format-support.md) verarbeiten, die mehr Formate standardmäßig abdecken, als dies mit früheren Versionen von Experience Manager möglich war. Beispielsweise ist jetzt das Extrahieren von Miniaturansichten von PSD- und PSB-Formaten möglich, für die zuvor Lösungen von Drittanbietern wie ImageMagick erforderlich waren. Sie können die komplexen Konfigurationen von ImageMagick nicht für die Konfiguration von [!UICONTROL Verarbeitungsprofilen] verwenden. Verwenden Sie [!DNL Dynamic Media] für die erweiterte FFmpeg-Transkodierung von Videos und verwenden Sie Verarbeitungsvideos für die [einfache Transkodierung von MP4-Profile](/help/assets/manage-video-assets.md#transcode-video).

Asset-Microservices sind ein Cloud-nativer Service, der in Kundenprogrammen und -umgebungen, die in Cloud Manager verwaltet werden, automatisch bereitgestellt und mit Adobe Experience Manager vernetzt wird. Um Experience Manager zu erweitern oder anzupassen, können Entwickler den vorhandenen Inhalt (oder Assets mit in einer Cloud-Umgebung generierten Ausgabedarstellungen) verwenden, um ihren Code zu testen und zu validieren, indem sie Assets verwenden, anzeigen und herunterladen.

Implementieren Sie für eine umfassende Validierung des Codes und des Prozesses, einschließlich der Erfassung und Verarbeitung von Assets, die Code-Änderungen in einer Cloud-Entwicklungsumgebung unter Verwendung der [Pipeline](/help/implementing/cloud-manager/configure-pipeline.md) und testen Sie mit vollständiger Ausführung der Asset-Microservice-Verarbeitung.

## Entfernung der klassischen Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche ist in Adobe Experience Manager as a [!DNL Cloud Service] nicht mehr verfügbar. Die Standardoberfläche ist die Touch-optimierte Benutzeroberfläche.

>[!MORELIKETHIS]
>
>* [Eine Einführung  [!DNL Adobe Experience Manager] als [!DNL Cloud Service]](/help/overview/introduction.md)
>* Eine [Übersicht von [!DNL Experience Manager] as a [!DNL Cloud Service] - Was ist neu und Was ist anders](/help/overview/what-is-new-and-different.md)
>* Die [Architektur](/help/core-concepts/architecture.md) von [!DNL Experience Manager] als [!DNL Cloud Service]
>* [Bemerkenswerte Änderungen  [!DNL Experience Manager] zu [!DNL Cloud Service]](/help/release-notes/aem-cloud-changes.md)
>* [Bemerkenswerte Änderungen  [!DNL Experience Manager Sites] zu [!DNL Cloud Service]](/help/sites-cloud/sites-cloud-changes.md)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html?lang=de)

