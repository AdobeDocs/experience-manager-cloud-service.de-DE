---
title: Versionshinweise für Version 2022.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2022.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 8fce7c50-f322-4bcf-bd76-390faedfd5b7
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '833'
ht-degree: 78%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2022.10.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den Funktionen der Version 2022.10.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2022.10.0) war der 10. November 2022. Die nächste monatliche Version (2023.1.0) ist für den Freitag, 9. Februar 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video „Versionsübersicht Oktober 2022“ an, das eine Zusammenfassung der Funktionen bietet, die mit der Version 2022.10.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3409801/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}


### Neue Funktionen in [!DNL Sites] {#sites-features}

* Die [Personalization-Registerkarte für Experience Fragments](/help/sites-cloud/authoring/fragments/content-fragments.md#personalization-experience-fragment) bietet für den Experience Fragment-Editor Funktionen zur Segmentierungsspezifikation und die Flexibilität, verschachtelte Experience Fragments zu erstellen, wodurch Kopf- und Fußzeilen für mehrere Segmente erstellt werden können. Bis zur Einführung dieser Funktion ist die von AEM angebotene Personalisierung nur für Web-Seiten verfügbar, nicht aber für Experience Fragments.

* Die [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) ermöglicht es Benutzenden, übersetzte Inhaltsfragmente effizient zu verwalten. Über einen 1-Klick-Zugriff können auch alle Sprachkopien angezeigt werden. Benutzende können die Tabellenansicht auch nach der Region filtern, die sie interessiert.

![Sprachen von Inhaltsfragmenten](/help/release-notes/assets/cfconsole-languages.png)

* Reduzieren Sie die Seitenladezeit für Besuchende weiter, indem Sie die Bildgrößeneinstellungen in Vorlagen optimieren. Weitere Informationen zur Bildkomponente finden Sie unter [WCM-Kernkomponente](https://github.com/adobe/aem-core-wcm-components)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Mit Experience Manager Assets können Sie jetzt Dokumente in anderen unterstützten Formattypen hochladen und [&#x200B; dem integrierten Document Cloud-Viewer in der Vorschau anzeigen](/help/assets/manage-pdf-documents.md). Zu den unterstützten Formattypen gehören TXT, RTF, DOC, DOCX, PPT, PPTX, XLS und XLSX.

  ![PDF-Ausgabe für andere Formate](/help/release-notes/assets/multi-page-other-formats.png)


### Neue Funktionen in der Vorabversion von [!DNL Assets] {#prerelease-features-assets}

* Experience Manager Assets verwendet jetzt ein verbessertes Framework mit künstlicher Intelligenz für Smart-Tags für Bilder. Diese inhaltsbezogene Intelligenz führt zu einer besseren Relevanz und Genauigkeit von Smart-Tags, die für alle Bild-Assets bei der Benutzende verfügbar sind. Darüber hinaus werden Orientierungsinformationen in `cq:tags` eingebettet, was mithilfe des Orientierungsfilters bessere Suchergebnisse ermöglicht.

  Wenn Sie daran interessiert sind, an der Beta-Version mitzuwirken, [füllen Sie dieses Formular](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4epXZrTVKKdJkUiHeolccf9UNEwyNEpHVEFaODdBNFZQSlFDREZQOVRRTy4u) bis zum 14. November aus.

* Experience Manager Assets unterstützt jetzt zusätzlich zum Zugriffsschlüssel [SAS-Token](/help/assets/add-assets.md#asset-bulk-ingestor) für die Authentifizierung beim Herstellen einer Verbindung zur Azure Blob Storage-Datenquelle für die Aufnahme von Assets mit dem Bulk-Import-Tool.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **Vorlagen-Editor für adaptive Forms**: Mit dem Vorlagen-Editor können Sie die Grundstruktur und das Erscheinungsbild von adaptiven Forms eines Unternehmens vordefinieren. Diese Version enthält die folgenden Verbesserungen am Vorlagen-Editor:
   * **[Formulardatenmodell im Vorlagen-Editor](/help/forms/creating-adaptive-form.md#edit-form-model-properties-of-an-adaptive-form-edit-form-model)**: Sie können das Schema für ein Formulardatenmodell mit einer Vorlage für adaptive Formulare im Vorlagen-Editor verknüpfen. Dadurch wird die Zeit für die Erstellung eines adaptiven Formulars reduziert. Die Option wird auch zum Editor für adaptive Formulare hinzugefügt, damit Benutzende ein Formulardatenmodell für vorhandene Formulare auswählen oder ändern können.
   * **[Datensatzdokument im Vorlagen-Editor](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform)**: Sie können jetzt die Generierung des Datensatzdokuments für alle Formulare standardisieren, die mithilfe einer Vorlage erstellt wurden. Dies trägt dazu bei, die Einhaltung und Standardisierung von Organisationsanforderungen zu verbessern.

* **[Starten des Assistenten für adaptive Formulare von einer AEM Sites-Seite](/help/forms/embed-adaptive-form-aem-sites.md)**: Die AEM Sites-Seite bietet nun erweiterte Unterstützung für adaptive Formulare. Sie können jetzt ohne Verlassen der AEM Sites-Seite ein adaptives Formular erstellen oder ein vorhandenes adaptives Formular einbetten.
* **[Ändern der Anzeigenausrichtung für Kontrollkästchen und Optionsfelder im Datensatzdokument](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record-customize-the-branding-information-in-document-of-record)**: Sie können jetzt die gewünschte Ausrichtung (horizontal, vertikal, gleich wie adaptive Formulare) für das Kontrollkästchen und das Optionsfeld im Datensatzdokument festlegen. Diese Option bestimmt die Positionierung von Optionen für Kontrollkästchen und Optionsfelder im Datensatzdokument.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Autoren können Produktlisten dynamisch mit Experience Fragments anreichern (Beispiel: Banner zwischen Produktlisten platzieren).
* Die Listenkomponente unterstützt jetzt zugehörige Produkt-/Kategorieseiten, um diese dynamisch anzuzeigen.
* Es wurde Unterstützung für Peregrine-12.5-Komponenten hinzugefügt.
* Es wurde Unterstützung für das Client-seitige Laden von Preisen in Produkt-Teasern und im Karussell hinzugefügt.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* AEM as a Cloud Service (Autoren-Service) wurde mit Unified Shell integriert, um das Benutzererlebnis zu verbessern und mit allen weiteren Experience Cloud-Anwendungen zu vereinheitlichen. Weitere Informationen finden Sie unter AEM as a [Cloud Service &#x200B;](/help/overview/aem-cloud-service-on-unified-shell.md) Unified Shell.

* Wie bereits in den Versionshinweisen erwähnt, wird die Verwendung des Administrationsbildschirms des Replikationsagenten oder der Replikations-API für die Verteilung von Inhaltspaketen, die größer als 10 MB sind (Knoten mit Eigenschaften, ohne Binärdateien), jetzt nicht mehr unterstützt und durchgesetzt. Siehe [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder den Workflow [Publish-Inhaltsstruktur](/help/operations/replication.md#publish-content-tree-workflow) für empfohlene Ansätze zur Replikation dieser großen Inhaltspakete.

* Die Dispatcher-Konfiguration verweist jetzt auf eine Datei, in der gängige Abfrageparameter für Marketing-Kampagnen aufgelistet sind. Kunden können die Auskommentierung der für sie relevanten Parameter aufheben, was zu einer besseren Zwischenspeicherung führt. Siehe [Parameter von Marketing-Kampagnen](/help/implementing/dispatcher/caching.md#marketing-parameters) für weitere Details.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
