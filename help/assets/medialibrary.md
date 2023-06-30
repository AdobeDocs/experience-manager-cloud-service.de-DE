---
title: Verwenden von Media Library für grundlegendes Asset-Management
description: "[!DNL Experience Manager Assets] und Media Library für das Asset-Management."
contentOwner: AG
feature: Asset Management,Publishing
role: User,Architect,Leader
exl-id: 4737d5ee-9a93-49f3-9f20-d4368e60e9fb
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '594'
ht-degree: 100%

---

<!--

Define Media Lib
Define req for it
Define use cases
Define what is not included

-->

# Verwenden von Media Library für grundlegendes Asset-Management {#manage-assets-using-media-library}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/assets/administer/medialibrary.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Die [!DNL Adobe Experience Manager]-Plattform bietet verschiedene Funktionen zum Verwalten von Assets. Mit Media Library können Benutzer eine kleine Anzahl von Assets in das Repository hochladen, diese auf den Web-Seiten suchen und verwenden und einfache Asset-Management-Aufgaben für die Assets ausführen.

Media Library ist eine einfache DAM-Lösung (Digital Asset Management), die im Lieferumfang einer [!DNL Adobe Experience Manager Sites]-Lizenz enthalten ist. [!DNL Sites] ist ein WCM-Angebot (Web Content Management). Media Library arbeitet mit allen Funktionen von Experience Manager.

Die [!DNL Adobe Experience Manager Assets]-Lizenz kann separat erworben werden. [!DNL Experience Manager Assets] ermöglicht eine robuste Handhabung von Assets über Nutzungsszenarien für Unternehmen, Anpassungen für Metadaten, Schemata, Suchen und die Benutzeroberfläche sowie viele andere Funktionen, die über die von Media Library bereitgestellten hinausgehen.

## Lizenzanforderungen {#avail-media-library-license}

Kunden, die über eine [!DNL Sites]-Lizenz verfügen, sind berechtigt, Media Library zu verwenden. Es funktioniert mit allen Komponenten von [!DNL Experience Manager].

Media Library wird als Teil von Sites installiert. Über die Sites-Lizenz und -Installation hinaus ist keine zusätzliche Lizenz und kein Package erforderlich.

## [!DNL Assets] im Vergleich mit Media Library {#assets-and-media-library}

Experience Manager Assets bietet DAM-Funktionen im Unternehmensmaßstab. Die Funktionalität vo Assets wird mit [!DNL Experience Manager] in einem einzigen Package bereitgestellt. Benutzer, die keine Assets-Lizenz erworben haben, sind nicht berechtigt, die erweiterten DAM-Funktionen zu verwenden. Ohne Assets-Lizenz sind nur [Media Library-Funktionen](#use-media-library) verfügbar.

Wenn Sie eine unbeabsichtigte Verwendung von nicht lizenzierten [!DNL Assets]-Funktionen verhindern möchten, entfernen Sie alle [!DNL Assets]-spezifischen Workflows, Komponenten, Taxonomien, Optionen und den [!DNL Assets]-Administrator aus [!DNL Experience Manager]. Hierdurch verhindern Sie, dass Benutzer versehentlich [!DNL Assets]-Funktionen nutzen, für die Sie keine Lizenz haben.

## Verwenden von Media Library {#use-media-library}

Media Library deckt im Großen und Ganzen die folgenden Anwendungsfälle ab:

* Bereitstellen von einfachen DAM-Funktionen für Web-Seiten, die mit [!DNL Adobe Experience Manager Sites] erstellt wurden.
* Adaptive Formulare und Kommunikationen, die mit [!DNL Adobe Experience Manager Forms] erstellt wurden.
* Mit [!DNL Adobe Experience Manager Screens] erstellte digitale Bildschirmerlebnisse.
* [!DNL Assets]-HTTP-REST-APIs für Headless-Vorgänge.

<!-- TBD: Remove this after confirmation. May need to merge this list with the list provided by PMs.

* Static renditions

-->

Um die Media Library-Funktionalität zu verwenden, können Sie die Standardbenutzeroberfläche von [!DNL Experience Manager] verwenden. Media Library ist Teil der [!DNL Experience Manager Sites]-Installation und es ist keine separate Oberfläche oder Add-on erforderlich. Über die vorhandene Benutzeroberfläche sind Media Library-Benutzer berechtigt, die folgenden Aufgaben auszuführen:

* Erstellen von Ordnern zum Organisieren von Assets.
* Hochladen von Assets.
* Veröffentlichen von Assets.
* Bearbeiten, Verschieben und Kopieren von Assets.
* Durchsuchen, Filtern und Suchen (einschließlich Ähnlichkeitssuche) von Assets.
* Hinzufügen von Werten zu den Metadatenfeldern und ihre Bearbeitung, mit Ausnahme von Smart-Tags, die standardmäßig auf der Registerkarte [!UICONTROL Standard] der Seite [!UICONTROL Eigenschaften] eines Assets verfügbar sind.
* Hinzufügen und Löschen von statischen Ausgabedarstellungen.
* Herunterladen von Ordnern, Assets und Asset-Ausgabedarstellungen.
* Erstellen von Asset-Versionen.
* Erstellen von Assets und Durchführen von Prüfungsaufgaben für Assets.
* Kommentieren von Assets.
* Hinzufügen von Assets zu [!DNL Sites]-Seiten über die Content-Suche.
* Verwenden von [!DNL Content Fragments].
* Verwenden von HTTP REST- und GraphQL-APIs für [!DNL Content Fragments] und referenzierte Medien-Assets unter Sites-Lizenz.
* Experience Cloud-Integration.
* Anpassen und Erweitern der Benutzeroberfläche für das Asset-Management.
* Zugriff auf Query Builder (API), um die Suchfunktion zu erweitern.
* Erstellen von statischen Tags.
* Erstellen von Projekten und Aufgaben.
* Aktivitäts-Stream (Zeitleiste).
* Kommentare und Anmerkungen.

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?

As per PM, we must avoid stating such a list, as we do not have a list that makes sense in Cloud Service.
-->

>[!IMPORTANT]
>
>Viele erweiterte DAM-Nutzungsszenarien werden von [!DNL Experience Manager Assets] erfüllt. Die Media Library-Lizenz berechtigt Sie nur dazu, die aufgelisteten Nutzungsszenarien mit Media Library zu erfüllen. Wenn ein Anwendungsfall nicht aufgeführt ist, wenden Sie ihn nicht mit der Media Library-Lizenz an. Wenn Sie Fragen haben, wenden Sie sich bitte an den Support.

Beachten Sie, dass Sie ohne [!DNL Assets]-Lizenz keine Smart Tags, [!DNL Asset]-Link, [!DNL Asset]-Auswahl, Bulk-Tagging, modifizierte Asset-Workflows oder die Standard-[!DNL Adobe Experience Manager]-Benutzeroberfläche verwenden können, um auf die Medienbibliothek zuzugreifen.

<!-- TBD: Add a CTA - how to contact Adobe for queries. -->

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

>[!MORELIKETHIS]
>
>* [DAM-Funktionen in  [!DNL Experience Manager Assets]](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/assets/home.html?lang=de)
>* [[!DNL Experience Manager] as a [!DNL Cloud Service] Produktbeschreibung](https://helpx.adobe.com/de/legal/product-descriptions/adobe-experience-manager-cloud-service.html)
