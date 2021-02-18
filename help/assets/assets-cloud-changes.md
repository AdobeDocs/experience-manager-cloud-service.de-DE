---
title: Wichtige Änderungen in  [!DNL Adobe Experience Manager Assets] als a [!DNL Cloud Service]
description: Bemerkenswerte Änderungen zu [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] im Vergleich zu [!DNL Adobe Experience Manager 6.5.
translation-type: tm+mt
source-git-commit: 6dc6445e4019664525629fe2204d255cfee37a81
workflow-type: tm+mt
source-wordcount: '743'
ht-degree: 24%

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
* Der Standardarbeitsablauf **[!UICONTROL DAM Asset Update]** in früheren Versionen von [!DNL Experience Manager] ist nicht mehr verfügbar. Stattdessen bieten Asset-Mikrodienste einen skalierbaren, leicht verfügbaren Dienst, der den Großteil der standardmäßigen Asset-Verarbeitung abdeckt (Darstellungen, Metadaten-Extraktion und Text-Extraktion für die Indexierung).
   * Siehe [Asset-Mikrodienste konfigurieren und verwenden](/help/assets/asset-microservices-configure-and-use.md)
   * Um benutzerdefinierte Workflow-Schritte in der Verarbeitung zu haben, können [Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) verwendet werden.
* Die Metadaten-Schreibablage wird nicht unterstützt. Siehe [Metadaten-Schreibback in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/xmp-writeback.html).
* Für Assets, die mit Package Manager hochgeladen werden, ist eine manuelle Neuverarbeitung mithilfe der Aktion **[!UICONTROL Asset]** in der [!DNL Assets]-Benutzeroberfläche erforderlich.
* [!DNL Assets] erkennt nicht automatisch den MIME-Typ der hochgeladenen Assets. Ein digitales Asset ohne Erweiterung oder mit einer falschen Erweiterung wird nicht wie gewünscht verarbeitet. Beim Hochladen solcher Assets passiert beispielsweise nichts oder es kann ein falsches Profil für die Verarbeitung auf das Asset angewendet werden. Benutzer können die Binärdateien weiterhin ohne Erweiterung im DAM speichern. Siehe [MIME-Typerkennung in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/detect-asset-mime-type-with-tika.html).
* [!DNL Experience Manager] als  [!DNL Cloud Service] keine Teilassets für zusammengesetzte Assets generiert. Siehe [Erstellen von Unterelementen in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-linked-subassets.html#generate-subassets).
* [!DNL Assets] Startseite ist nicht verfügbar. Siehe [[!DNL Assets] Home Page experience in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-home-page.html).
* Die Erkennung von Duplikat-Assets funktioniert anders als [wie sie unter  [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/duplicate-detection.html) funktioniert hat.
* Nur für Platzierung (FPO) werden Darstellungen anders generiert als frühere [!DNL Experience Manager] Versionen. Siehe [FPO-Darstellung für [!DNL Experience Manager] als a [!DNL Cloud Service]](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/configure-aem-assets-for-asset-link.ug.html).
* Wenn ein ZIP-Archiv hochgeladen wird, extrahiert [!DNL Experience Manager] als [!DNL Cloud Service] nicht die im Archiv gebündelten Elemente. Siehe [ZIP-Extraktion in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.htmln#extractzip).

Mit Asset-Mikrodiensten generierte Standarddarstellungen werden auf abwärtskompatible Weise in den Asset-Repository-Knoten unter Verwendung derselben Benennungskonventionen gespeichert.

## Entwickeln und Testen von Asset-Microservices {#asset-microservices}

Asset-Microservices bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud Services. Adobe verwaltet die Cloud Services für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen. Asset-Microservices helfen dabei, die Notwendigkeit von Rendering-Tools und -Methoden von Drittanbietern (wie ImageMagick) zu vermeiden, die Konfiguration des Systems zu vereinfachen und sofort einsatzbereite Funktionen für gängige Dateitypen bereitzustellen. Sie können jetzt eine [breite Palette von Dateitypen](/help/assets/file-format-support.md) verarbeiten, die mehr Formate standardmäßig abdecken, als dies mit früheren Versionen von Experience Manager möglich war. Beispielsweise ist jetzt das Extrahieren von Miniaturansichten von PSD- und PSB-Formaten möglich, für die zuvor Lösungen von Drittanbietern wie ImageMagick erforderlich waren. Sie können die komplexen Konfigurationen von ImageMagick nicht für die Konfiguration von [!UICONTROL Verarbeitungsprofilen] verwenden. Verwenden Sie [!DNL Dynamic Media] für die erweiterte FFmpeg-Transkodierung von Videos und verwenden Sie Verarbeitungsvideos für die [einfache Transkodierung von MP4-Profile](/help/assets/manage-video-assets.md#transcode-video).

Asset Microservices ist ein Cloud-nativer Dienst, der in Programmen und Umgebung, die in Cloud Manager verwaltet werden, automatisch bereitgestellt und an [!DNL Experience Manager] verkabelt wird. Um [!DNL Experience Manager] zu erweitern oder anzupassen, können die Entwickler den vorhandenen Inhalt oder die vorhandenen Assets mit in einer Cloud-Umgebung generierten Darstellungen verwenden, um den Code zu testen und zu validieren, indem sie Assets anzeigen, herunterladen.

Implementieren Sie für eine umfassende Validierung des Codes und des Prozesses, einschließlich der Erfassung und Verarbeitung von Assets, die Code-Änderungen in einer Cloud-Entwicklungsumgebung unter Verwendung der [Pipeline](/help/implementing/cloud-manager/configure-pipeline.md) und testen Sie mit vollständiger Ausführung der Asset-Microservice-Verarbeitung.

## Entfernung der klassischen Benutzeroberfläche {#classic-ui}

Die klassische Benutzeroberfläche ist in [!DNL Experience Manager] nicht mehr als [!DNL Cloud Service] verfügbar. Es ist nur die Touch-aktivierte Benutzeroberfläche verfügbar.

>[!MORELIKETHIS]
>
>Die folgenden Ressourcen stehen für [!DNL Experience Manager] als [!DNL Cloud Service] zur Verfügung:
>
>* [Einführung](/help/overview/introduction.md)
>* [Neue Funktionen und Unterschiede](/help/overview/what-is-new-and-different.md)
>* [Die Architektur](/help/core-concepts/architecture.md)
>* [Wesentliche Änderungen](/help/release-notes/aem-cloud-changes.md)
>* [Wesentliche Änderungen [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
>* [Videoschulungen](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html?lang=de)

