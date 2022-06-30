---
title: Bekannte Probleme
description: Bekannte Probleme mit Adobe Experience Manager as a Cloud Service
exl-id: 897b944a-d320-4d21-91f4-2cd3da6179b1
source-git-commit: 755c0072148ad73486df2ccfed69248b9d73ec2a
workflow-type: tm+mt
source-wordcount: '177'
ht-degree: 66%

---

# Bekannte Probleme {#known-issues}

In diesem Artikel werden die bekannten Probleme von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aufgeführt. Die Liste wird mit jeder weiteren Version von [!DNL Experience Manager] überarbeitet und aktualisiert.

[Wenden Sie sich an den Support](https://experienceleague.adobe.com/?lang=de&amp;support-solution=Experience+Manager#support), um weitere Informationen zu den bekannten Problemen zu erhalten.

<!-- 
## Platform {#platform}
-->

## Sites {#sites}

Zu den bekannten Probleme in [!DNL Sites] zählen:

* In der GraphQL-IDE können Sie [den Cache für die gespeicherten Abfragen verwalten](/help/headless/graphql-api/graphiql-ide.md##managing-cache).
   * Beim ersten Speichern werden die für die Header gespeicherten Werte auf `0` (anstelle der Standardwerte) - wenn der Benutzer diese Werte im Dialogfeld nicht geändert hat.
   * Bei nachfolgenden Speichervorgängen werden die Werte korrekt gespeichert.
   * Daher muss der Benutzer die Header zweimal speichern.

## [!DNL Assets] {#assets}

<!-- Jira label: assets-cloud-known-issues -->

Zu den bekannten Probleme in [!DNL Assets] zählen:

* **Download**: Wenn Sie einen leeren Ordner herunterladen, sendet [!DNL Experience Manager] eine Erfolgsmeldung über das Erstellen eines ZIP-Archivs, das Archiv wird jedoch nicht erstellt.

* **Metadatenschema**: Das Widget zur Asset-Bewertung, das verwendet wird, um JSP-Kompilierungsfehler zu verursachen. Es wurde aus dem Metadatenschema entfernt. <!-- CQ-4282865, CQ-4284633 -->

Siehe auch [Wesentliche Änderungen in [!DNL Experience Manager Assets]](/help/assets/assets-cloud-changes.md).

<!-- This content was added at GA. Not sure if we should continue to have this commitment about upcoming features/enh. in the docs. Commenting it for now.

### Upcoming Assets capabilities {#upcoming-assets-capabilities}

A few capabilities of Adobe Experience Manager Assets that depend on foundation capabilities, which are not yet available in the Experience Manager as a Cloud Service deployment architecture, are expected to be enabled at a later stage:

* Capabilities not enabled at this stage due to dependency on Commerce Integration Framework APIs:
  * Photoshoot workflow models.
  * Product information tab in the asset properties user interface is not populated.

* Capabilities not enabled at this stage due to dependency on InDesign Server integration:
  * Asset Templates and Asset Catalogs.
  * Multi-page preview of Adobe InDesign files.
-->

>[!MORELIKETHIS]
>
>* [Die wichtigsten Änderungen in [!DNL Experience Manager]](aem-cloud-changes.md)
>* [Veraltete und entfernte Funktionen](deprecated-removed-features.md)
>* [Versionshinweise](home.md)

