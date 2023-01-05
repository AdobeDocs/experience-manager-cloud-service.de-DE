---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 33bf3dbf6118a9d93e0fe021736b74079100a214
workflow-type: tm+mt
source-wordcount: '1092'
ht-degree: 17%

---


# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

>[!CAUTION]
>
>**Ausschlusszeitraum für geplante Wartungen**
>
> Während der folgenden Zeiträume, die um Mitternacht (00:00 Uhr) CET beginnen und enden, wird keine automatische AEMaaCS-Wartung ausgeführt:
>
>* Montag, 21. November bis Montag, 12. Dezember
>* Montag, 19. Dezember bis Dienstag, 3. Januar


## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle monatliche Version (2022.10.0) ist der 10. November 2022. Die nächste monatliche Version (2023.1.0) ist für den 26. Januar 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht vom Oktober 2022 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2022.10.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3409801/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}


### Neue Funktionen in [!DNL Sites] {#sites-features}

* Die [Registerkarte &quot;Personalisierung&quot;für Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#personalization-experience-fragment) ermöglicht dem Experience Fragment-Editor Funktionen zur Segmentierungsspezifikation sowie die Flexibilität, verschachtelte Experience Fragments zu erstellen, wodurch Kopf- und Fußzeilen für mehrere Segmente erstellt werden können. Vor dem Start dieser Funktion ist die von AEM angebotene Personalisierung nur für Webseiten verfügbar, nicht aber für Experience Fragments.

* Die [Inhaltsfragmentkonsole](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) ermöglicht es Benutzern, übersetzte Inhaltsfragmente effizient zu verwalten. Es wurde ein 1-Klick-Zugriff bereitgestellt, um auch alle Sprachkopien anzuzeigen. Benutzer können die Tabellenansicht auch nach dem Gebietsschema ihrer Interessen filtern.

![Inhaltsfragmentsprachen](/help/release-notes/assets/cfconsole-languages.png)

* Reduzieren Sie die Seitenladezeit für Besucher weiter, indem Sie die Bildgrößeneinstellungen in Vorlagen optimieren. Weitere Informationen zur Bildkomponente finden Sie unter [WCM-Kernkomponente](https://github.com/adobe/aem-core-wcm-components)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Mit Experience Manager Assets können Sie jetzt Dokumente in anderen unterstützten Formattypen hochladen und[ Vorschau mit dem integrierten Document Cloud-Viewer](/help/assets/manage-pdf-documents.md). Zu den unterstützten Formattypen gehören TXT, RTF, DOC, DOCX, PPT, PPTX, XLS und XLSX.

   ![PDF-Ausgabedarstellung für andere Formate](/help/release-notes/assets/multi-page-other-formats.png)


### Neue Funktionen in [!DNL Assets] Vorabversion {#prerelease-features-assets}

* Experience Manager Assets verwendet jetzt ein verbessertes Framework für künstliche Intelligenz für Smart-Tags für Bilder. Diese Content-Intelligenz führt zu einer besseren Relevanz und Genauigkeit von Smart-Tags, die für alle Bild-Assets bei der Erfassung verfügbar sind. Darüber hinaus werden Orientierungsinformationen in `cq:tags`, was mithilfe des Orientierungsfilters bessere Suchergebnisse ermöglicht.

   Wenn Sie an der Betaversion teilnehmen möchten, [Dieses Formular ausfüllen](https://forms.office.com/pages/responsepage.aspx?id=Wht7-jR7h0OUrtLBeN7O4epXZrTVKKdJkUiHeolccf9UNEwyNEpHVEFaODdBNFZQSlFDREZQOVRRTy4u) bis zum 14. November.

* Experience Manager Assets jetzt [unterstützt SAS-Token](/help/assets/add-assets.md#asset-bulk-ingestor) zusätzlich zum Zugriffsschlüssel für die Authentifizierung beim Herstellen einer Verbindung zur Azure Blob Storage-Datenquelle für die Aufnahme von Assets mit dem Bulk Import-Tool.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-channel}


* [Adaptiver Forms-Assistent](/help/forms/creating-adaptive-form.md): AEM Forms bietet einen benutzerfreundlichen Assistenten für Unternehmen, mit dem sich Adaptive Forms schnell erstellen lässt. Der Assistent verfügt über eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen. Diese Version bringt die folgenden Verbesserungen am Assistenten:

   * Auswählen oder Aufheben der Auswahl von Feldern: Mit dem Assistenten können Sie ein adaptives Formular erstellen, das auf JSON- und Formulardatenmodellschemata basiert. Sie können jetzt eine Teilmenge von Feldern innerhalb eines Schemas auswählen, um sie in ein adaptives Formular einzuschließen. Die ausgewählten Felder werden in die entsprechenden Datenerfassungskomponenten für adaptive Formulare konvertiert, um die gewünschten adaptiven Formulare schnell zu erstellen.

   * Statische Vorlagen verwenden: Kunden, die bereits in ältere statische Vorlagen investiert haben, können ihre Journey der Cloud-Akzeptanz fortsetzen, indem sie statische Vorlagen im Assistenten verwenden, um adaptive Formulare zu erstellen. Dadurch erhalten Kunden zusätzliche Zeit, alte statische Vorlagen in moderne bearbeitbare Vorlagen zu migrieren.

* [Entfernen ausgeblendeter Felder aus einem Datensatzdokument (DoR) bei der serverseitigen Verarbeitung](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md): Sie können das Datensatzdokument-PDF für Endbenutzer generieren, die nur die Felder enthalten, die für sie während der Datenerfassung sichtbar waren. Bei Formularübermittlung überprüft der Server, welche Felder dem Endbenutzer basierend auf gesendeten Daten ausgeblendet wurden, und schließt sie aus dem Datensatzdokument aus, um Konsistenz zu gewährleisten.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **Adaptiver Forms-Vorlageneditor**: Mit dem Vorlageneditor können Sie die Grundstruktur und das Erscheinungsbild von Adaptive Forms in einem Unternehmen vordefinieren. Diese Version bringt die folgenden Verbesserungen am Vorlageneditor:
   * **[Formulardatenmodell im Vorlageneditor](/help/forms/creating-adaptive-form.md#edit-form-model-properties-of-an-adaptive-form-edit-form-model)**: Sie können ein Formulardatenmodellschema mit einer Vorlage für adaptive Formulare im Vorlageneditor verknüpfen. Dadurch wird die Zeit für die Erstellung eines adaptiven Formulars reduziert. Die Option wird auch zum adaptiven Forms-Editor hinzugefügt, damit Benutzer Formulardatenmodell für vorhandene Formulare auswählen oder ändern können.
   * **[Datensatzdokument im Vorlageneditor](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#document-of-record-support-in-adaptive-form-editor-dor-support-in-adaptiveform)**: Sie können jetzt die Generierung des Datensatzdokuments für alle Formulare standardisieren, die mit einer Vorlage erstellt wurden. Dies trägt dazu bei, die Einhaltung und Standardisierung von Organisationsanforderungen zu verbessern.

* **[Starten des Assistenten für adaptive Formulare von einer AEM Sites-Seite aus](/help/forms/embed-adaptive-form-aem-sites.md)**: Die AEM Sites-Seite bietet nun erweiterte Unterstützung für Adaptive Forms. Sie können jetzt ein neues adaptives Formular erstellen oder ein vorhandenes adaptives Formular einbetten, während Sie auf der AEM Sites-Seite verbleiben.
* **[Ändern der Anzeigenausrichtung für Kontrollkästchen und Radiobutton in DoR](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#customize-the-branding-information-in-document-of-record-customize-the-branding-information-in-document-of-record)**: Sie können jetzt die gewünschte Ausrichtung (horizontal, vertikal, wie Adaptive Forms) für das Kontrollkästchen und das Optionsfeld im Datensatzdokument festlegen. Diese Option bestimmt die Positionierung von Kontrollkästchen- und Optionsschaltflächen-Optionen im Datensatzdokument.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Autoren können Produktlisten mit Experience Fragments dynamisch anreichern (Beispiel: Banner zwischen Produktlisten platzieren).
* Die Listenkomponente unterstützt jetzt zugehörige Produkt-/Kategorieseiten, um zugehörige Seiten dynamisch anzuzeigen.
* Unterstützung für Peregrine 12.5-Komponenten wurde hinzugefügt.
* Es wurde Unterstützung für das clientseitige Laden von Preisen in Produkt-Teaser und Karussell hinzugefügt.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* AEM as a Cloud Service (Autorendienst) ist jetzt in Unified Shell integriert, um das Benutzererlebnis zu verbessern und es mit allen anderen Experience Cloud-Anwendungen zu vereinheitlichen. Siehe AEM als [Cloud Service auf Unified Shell](/help/overview/aem-cloud-service-on-unified-shell.md) für weitere Details.

* Wie bereits in den Versionshinweisen erwähnt, wird die Verwendung des Administrationsbildschirms des Replikationsagenten oder der Replikations-API für die Verteilung von Inhaltspaketen, die größer als 10 MB sind (Knoten mit Eigenschaften, einschließlich Binärdateien), nicht mehr unterstützt und in den nächsten Tagen durchgesetzt. Siehe [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder [Workflow &quot;Inhaltsstruktur veröffentlichen&quot;](/help/operations/replication.md#publish-content-tree-workflow) für die vorgeschlagenen Ansätze zur Replikation dieser großen Inhaltspakete.

* Die Dispatcher-Konfiguration verweist jetzt auf eine Datei, in der gängige Abfrageparameter für Marketing-Kampagnen aufgelistet sind. Kunden können die Auskommentierung der für sie relevanten Parameter aufheben, was zu einer besseren Zwischenspeicherung führt. Siehe [Parameter der Marketing-Kampagne](/help/implementing/dispatcher/caching.md#marketing-parameters) für weitere Details.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
