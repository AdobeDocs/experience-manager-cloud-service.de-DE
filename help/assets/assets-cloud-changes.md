---
title: Wesentliche Änderungen in [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service]
description: Wesentliche Änderungen an  [!DNL Adobe Experience Manager Assets] in [!DNL Experience Manager] as a [!DNL Cloud Service] as compared to [!DNL Adobe Experience Manager] 6.5.
feature: Release Information
role: User,Leader,Architect,Admin
exl-id: 93e7dbcd-016e-4ef2-a1cd-c554efb5ad34
source-git-commit: 9235dd41a77242655bf944666bdd5c14db8a83d6
workflow-type: tm+mt
source-wordcount: '995'
ht-degree: 68%

---

# Wesentliche Änderungen in[!DNL Experience Manager Assets]as a [!DNL Cloud Service] {#notable-changes}

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] bietet eine Vielzahl neuer Funktionen und Möglichkeiten für die Verwaltung Ihrer Experience Manager-Projekte. Es gibt viele Unterschiede zwischen [!DNL Experience Manager Assets] On-Premise oder als Adobe Managed Service (gehostet) im Vergleich zu [!DNL Experience Manager] as a [!DNL Cloud Service]. In diesem Artikel werden wichtige Unterschiede bei den Funktionalitäten von [!DNL Assets] verdeutlicht.

Die Hauptunterschiede gegenüber Adobe [!DNL Experience Manager] 6.5 bestehen in den folgenden Bereichen:

* [Asset-Aufnahme, -Upload und -Verarbeitung](#asset-ingestion).
* [Asset-Microservices für Cloud-native Verarbeitung](#asset-microservices).
* [Entfernung der klassischen Benutzeroberfläche](#classic-ui).

## Asset-Erfassung, -Verarbeitung und -Verteilung {#asset-ingestion-distribution}

Der Asset-Upload wurde auf Effizienz optimiert, indem eine bessere Skalierung der Aufnahme, schnellere Uploads, eine schnellere Verarbeitung mithilfe von Microservices und eine Massenaufnahme ermöglicht wurden. Produktfunktionen (Web-Benutzeroberflächen, Desktop-Clients) wurden aktualisiert. Dies kann sich auch auf einige bestehende Anpassungen auswirken.

* [!DNL Experience Manager] verwendet das Prinzip des direkten Binärzugriffs zum Hoch- und Herunterladen von Assets und verwendet Asset-Microservices zur Verarbeitung von Assets. Weitere Informationen finden Sie unter [Überblick über Microservices](/help/assets/asset-microservices-overview.md).
   * Asset-Upload [mit direktem Binärzugriff](/help/assets/asset-microservices-overview.md#asset-upload-with-direct-binary-access).
   * Weitere technische Daten finden Sie im Abschnitt [Protokoll und APIs für den direkten Binär-Upload](/help/assets/developer-reference-material-apis.md#upload-binary).
   * Einen Vergleich der verfügbaren API-Methoden für grundlegende CRUD-Vorgänge finden Sie unter [APIs und Asset-Vorgänge](/help/assets/developer-reference-material-apis.md#use-cases-and-apis).
* Der standardmäßige Workflow **[!UICONTROL DAM-Asset-Update]** in früheren Versionen von [!DNL Experience Manager] ist nicht mehr verfügbar. Stattdessen bieten Asset-Microservices einen skalierbaren, jederzeit nutzbaren Service, der den Großteil der standardmäßigen Asset-Verarbeitung (Ausgabedarstellungen, Metadatenextraktion, Textextraktion für die Indizierung) abdeckt.
   * Weitere Informationen finden Sie unter [Konfigurieren und Verwenden von Asset-Microservices](/help/assets/asset-microservices-configure-and-use.md).
   * Um bei der Verarbeitung benutzerdefinierte Workflow-Schritte durchzuführen, können Sie [Nachbearbeitungs-Workflows](/help/assets/asset-microservices-configure-and-use.md#post-processing-workflows) verwenden.

* Die Website-Komponenten, die eine Binärdatei ohne Umwandlung bereitstellen, können den direkten Download verwenden. Das Sling-GET-Servlet wird aktualisiert, damit Entwickler dies standardmäßig tun können. Die Website-Komponenten, die eine Binärdatei mit einer Umwandlung bereitstellen (z. B. Größenanpassung über ein Servlet), können weiterhin wie bisher funktionieren.

Mit Asset-Microservices generierte Standardausgabedarstellungen werden in abwärtskompatibler Form im Asset-Repository-Knoten gespeichert, wobei dieselben Benennungskonventionen verwendet werden.

## Entwickeln und Testen von Asset-Microservices {#asset-microservices}

Asset-Microservices bieten eine skalierbare und widerstandsfähige Verarbeitung von Assets mithilfe von Cloud Services. Adobe verwaltet die Cloud Services für eine optimale Handhabung verschiedener Asset-Typen und Verarbeitungsoptionen. Asset-Microservices helfen dabei, die Notwendigkeit von Rendering-Tools und -Methoden von Drittanbietern (wie [!DNL ImageMagick]) zu vermeiden, Konfigurationen zu vereinfachen und sofort einsatzbereite Funktionen für gängige Dateitypen bereitzustellen. Sie können jetzt eine [breite Palette von Dateitypen](/help/assets/file-format-support.md) verarbeiten, die mehr Formate standardmäßig abdecken, als dies mit früheren Versionen von Experience Manager möglich war. Beispielsweise ist jetzt die Extraktion von Miniaturansichten aus PSD- und PSB-Formaten möglich, die zuvor Drittanbieterlösungen wie [!DNL ImageMagick] erforderten. Sie können die komplexen Konfigurationen von [!DNL ImageMagick] nicht für die Konfiguration [!UICONTROL Verarbeitungsprofile] verwenden. Verwenden Sie [!DNL Dynamic Media] für die erweiterte FFmpeg-Transkodierung von Videos und Verarbeitungsprofile für die [einfache Transkodierung von MP4-Videos](/help/assets/manage-video-assets.md#transcode-video).

Asset-Microservices sind ein Cloud-nativer Service, der in Kundenprogrammen und -umgebungen, die in Cloud Manager verwaltet werden, automatisch bereitgestellt und mit [!DNL Experience Manager] vernetzt wird. Um [!DNL Experience Manager] zu erweitern oder anzupassen, können Entwickler den vorhandenen Inhalt (oder Assets mit in einer Cloud-Umgebung generierten Ausgabedarstellungen) verwenden, um ihren Code zu testen und zu validieren, indem sie Assets verwenden, anzeigen und herunterladen.

Implementieren Sie für eine umfassende Validierung des Codes und des Prozesses, einschließlich der Erfassung und Verarbeitung von Assets, die Code-Änderungen in einer Cloud-Entwicklungsumgebung unter Verwendung der [Pipeline](/help/implementing/cloud-manager/configure-pipeline.md) und testen Sie mit vollständiger Ausführung der Asset-Microservice-Verarbeitung.

## Parität der Funktionen mit [!DNL Experience Manager] 6.5 {#cloud-service-feature-status}

[!DNL Experience Manager] as a [!DNL Cloud Service] führt viele neue Funktionen und effektive Methoden ein, um die Leistung vorhandener Funktionen zu optimieren. Beim Wechsel von [!DNL Experience Manager] 6.5 zu [!DNL Experience Manager] as a [!DNL Cloud Service] werden Sie möglicherweise feststellen, dass einige Funktionen entweder anders arbeiten, nicht verfügbar sind oder nur teilweise verfügbar sind. Im Folgenden finden Sie eine Liste solcher Funktionen. Weitere Informationen finden Sie unter [veraltete und entfernte Funktionen](/help/release-notes/deprecated-removed-features.md).

| Funktion oder Nutzungsszenario | Status in [!DNL Experience Manager] as a [!DNL Cloud Service] | Kommentare |
|-----|-----|-----|
| [Ermittlung doppelter Assets](/help/assets/manage-digital-assets.md#detect-duplicate-assets) | Funktioniert anders. | Hier erfahren Sie mehr zur [Funktionsweise in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/duplicate-detection.html?lang=de). |
| [FPO-Ausgabedarstellungen](/help/assets/configure-fpo-renditions.md) | Funktioniert anders. | Verarbeitungsprofile verwenden Asset-Microservices zum Generieren von FPO-Ausgabedarstellungen. In Experience Manager 6.5 war eine Drittanbieterlösung wie [!DNL ImageMagick] verfügbar, um die Ausgabedarstellungen zu generieren. |
| Metadaten-Writeback | Funktioniert anders. | Standardmäßig deaktiviert. Aktivieren Sie bei Bedarf den entsprechenden Workflow-Starter. Writeback wird von Asset-Microservices verarbeitet. |
| Verarbeitung der mit Package Manager hochgeladenen Assets | Erfordert manuelles Eingreifen. | Veranlassen Sie die Neuverarbeitung manuell mit der Aktion **[!UICONTROL Assets erneut verarbeiten]**. |
| MIME-Typerkennung | Nicht unterstützt. | Wenn Sie ein digitales Asset ohne Erweiterung oder mit einer falschen Erweiterung hochladen, wird es möglicherweise nicht wie gewünscht verarbeitet. Benutzer können die Binärdateien weiterhin ohne Erweiterung im DAM speichern. Weitere Informationen finden Sie unter [MIME-Typerkennung in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/detect-asset-mime-type-with-tika.html?lang=de). |
| Erstellung von Unter-Assets für zusammengesetzte Assets | Nicht unterstützt. | Abhängige Anwendungsfälle wie Anmerkungen sind möglicherweise nicht erfüllt. Weitere Informationen finden Sie unter [Erstellen von Teil-Assets in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/managing-linked-subassets.html?lang=de#generate-subassets). Die PDF-Vorschau einiger Dateitypen ist ab [Version 2021.7.0](/help/release-notes/release-notes-cloud/release-notes-current.md) verfügbar. |
| Startseite | Nicht unterstützt. | Weitere Informationen finden Sie unter [[!DNL Assets] Home Page experience in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-home-page.html?lang=de) |
| Extrahieren von Assets aus dem ZIP-Archiv | Nicht unterstützt. | Weitere Informationen finden Sie unter [ZIP-Extraktion in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/managing/manage-assets.html?lang=de#extractzip). |
| Asset-Bewertungen | Nicht unterstützt. | Das Bewertungs-Widget im Metadatenschema-Editor wird nicht unterstützt. |
| Inhaltsdispositionsfilter | Nicht unterstützt. | Ein beliebtes Nutzungsszenario von `ContentDispositionFilter` besteht darin, Administratoren zu ermöglichen, [!DNL Experience Manager] so zu konfigurieren, dass HTML-Dateien bereitgestellt und PDF-Dateien inline geöffnet werden, anstatt sie herunterzuladen. Auf den Veröffentlichungsinstanzen können Sie die Dispatcher-Konfiguration verwenden. In den Autoreninstanzen empfiehlt Adobe keine Änderung am Content Disposition-Header. Siehe [Filter für Inhaltsdisposition in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/administering/security/content-disposition-filter.html). |
| [Bericht herunterladen](/help/assets/asset-reports.md) | Nicht unterstützt. | Vorerst ist der Download-Bericht mit Informationen zur Asset-Nutzung nicht verfügbar. Siehe [Bericht herunterladen in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/asset-reports.html). |
| Vorlage für Produktfotos | Nicht unterstützt. | Siehe [Produkt-Fotoshooting-Vorlage in [!DNL Experience Manager] 6.5](https://experienceleague.adobe.com/docs/experience-manager-65/authoring/projects/managing-product-information.html). |
| Intelligente Übersetzung | Nicht unterstützt. | [Intelligente ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/translation/smart-translation-search-feature-video-use.html) Übersetzungen werden in  [!DNL Experience Manager] as a  [!DNL Cloud Service]nicht unterstützt. |
| WebDAV | Nicht unterstützt. | Alternativen finden Sie unter [[!DNL Creative Cloud] integration](/help/assets/aem-cc-integration-best-practices.md) oder [Entwicklerreferenzmaterial](/help/assets/developer-reference-material-apis.md). |
| Klassische Benutzeroberfläche | Nicht unterstützt. | Es ist nur die Touch-optimierte Benutzeroberfläche verfügbar. |

>[!MORELIKETHIS]
>
>Die folgenden Ressourcen stehen für [!DNL Experience Manager] as a [!DNL Cloud Service] zur Verfügung:
>
>* [Liste veralteter und entfernter Funktionen](/help/release-notes/deprecated-removed-features.md)
>* [Einführung](/help/overview/introduction.md)
>* [Neue Funktionen und Unterschiede](/help/overview/what-is-new-and-different.md)
>* [Die Architektur](/help/overview/architecture.md)
>* [Wesentliche Änderungen](/help/release-notes/aem-cloud-changes.md)
>* [Wesentliche Änderungen [!DNL Sites]](/help/sites-cloud/sites-cloud-changes.md)
>* [Video-Tutorials](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html?lang=de)

