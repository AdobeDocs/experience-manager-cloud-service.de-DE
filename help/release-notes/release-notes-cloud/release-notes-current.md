---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
source-git-commit: b47901d749712384506cf4eb03c099027933e95f
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 23%

---


# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise für die Funktion für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2021, 2022 usw.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) , um mehr über die bevorstehenden Funktionsaktivierungen zu erfahren. [!DNL Experience Manager] as a Cloud Service.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version der Funktion (2023.1.0) ist der 9. Februar 2023. Die nächste Version der Funktion (2023.2.0) ist für den 6. April 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht Januar 2023 an, das eine Zusammenfassung der Funktionen bietet, die der Version 2023.1.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3413479/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in der Vorabversion von [!DNL Sites] {#prerelease-features-sites}

* Die AEM GraphQL Content Delivery API unterstützt jetzt GraphQL [Paging](/help/headless/graphql-api/content-fragments.md#paging) und [Sortierung](/help/headless/graphql-api/content-fragments.md#sorting), um das Abrufen und Rendern großer Inhaltssätze effizienter zu gestalten. Mit der GraphQL-Paginierung können Sie die Antwortzeit der Abfrage verbessern, indem Ergebnisse in Teilmengen zurückgegeben werden (im Gegensatz zu allen auf einmal). Die GraphQL-Sortierung ermöglicht die Platzierung von Inhaltssätzen in einer gewünschten Reihenfolge, was die Verarbeitung der Inhalte durch eine Client-Anwendung erleichtert.  Die Reaktionszeit von Abfragen wird durch Hybrid-Filter in der AEM GraphQL-Engine weiter verbessert. Inhalte werden jetzt aus JCR in kleineren Sets gelesen, die mit Abfragefiltern übereinstimmen.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Asset-Berichte bieten Administratoren jetzt die Möglichkeit, [Asset-Download-Berichte erstellen](/help/assets/asset-reports.md) aus der as a Cloud Service Experience Manager Assets-Implementierung. Diese Daten ermöglichen es Administratoren außerdem, Einblicke aus wichtigen Erfolgsmetriken zu gewinnen, um die Akzeptanz von Assets in Ihrem Unternehmen und durch Kunden zu messen.

   ![PDF-Ausgabe für andere Formate](/help/release-notes/assets/choose_report.png)

* Experience Manager Assets unterstützt jetzt zusätzlich zum Zugriffsschlüssel [SAS-Token](/help/assets/add-assets.md#asset-bulk-ingestor) für die Authentifizierung beim Herstellen einer Verbindung zur Azure Blob Storage-Datenquelle für die Aufnahme von Assets mit dem Bulk-Import-Tool.

* Verbesserte Verwaltung von CMYK-Bildern im Asset compute, sodass Sie Smart Crop und Smart Tags für CMYK-Bilder generieren können.

### Neue Funktionen in der Vorabversion von [!DNL Assets] {#prerelease-features-assets}

* Experience Manager Assets unterstützt jetzt [groß angelegte Erfassung von Assets aus Google Cloud Platform](/help/assets/add-assets.md#asset-bulk-ingestor) mit dem Tool für den Massenimport .

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-channel}

* **[Workflow-Schritte zum Generieren nicht interaktiver PDF-Dokumente und druckbarer Ausgaben](/help/forms/aem-forms-workflow-step-reference.md)**: Automatisieren Sie die Erstellung nicht interaktiver PDF-Dokumente und druckbarer Ausgaben für Ihre Geschäftsprozesse mit AEM Workflow-Schritten, optimieren Sie den Prozess der Dokumenterstellung und sparen Sie Zeit.
* **[Verwenden Sie Fußnoten, um Zitate oder zusätzliche Informationen in Adaptive Forms bereitzustellen.](/help/forms/footnotes-richtextsupport.md)**: Verwenden Sie Fußnoten in einem adaptiven Formular, um Informationen zum Ausfüllen oder Verwenden eines Formulars anzuzeigen. Sie können damit auch Klammerinformationen, Copyright-Berechtigungen und andere hilfreiche Informationen bereitstellen.

### Neue Funktionen in der Vorabversion von [!DNL Forms] {#prerelease-features-forms}

* **[Verwenden der Datenerfassungskernkomponenten zum Erstellen von Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=en)**: [Adaptiven Forms-Editor verwenden](/help/forms/creating-adaptive-form-core-components.md) , um Formulare zu erstellen, die auf standardisierten Datenerfassungskomponenten (Kernkomponenten) basieren. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre digitalen Registrierungserlebnisse.
* **[Unterstützung der Frontend-Pipeline für die Formatierung von Kernkomponenten mit adaptivem Forms](/help/forms/using-themes-in-core-components.md)**: Nutzen Sie einfach anpassbare BEM-basierte Designs für die auf Kernkomponenten basierende adaptive Forms, indem Sie sie mit der Frontend-Bereitstellungs-Pipeline bereitstellen, um das Erscheinungsbild Ihrer Formulare zu verbessern.
* **[Generieren des Datensatzdokuments für die auf Kernkomponenten basierende adaptive Forms](/help/forms/generate-document-of-record-core-components.md)**: Erstellen Sie einen Datensatz für ein auf Kernkomponenten basierendes adaptives Formular bei der Übermittlung für die langfristige Archivierung, im Druck oder im Dokumentformat.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Senden von Adaptive Forms an Microsoft SharePoint und Microsoft OneDrive](/help/forms/configuring-submit-actions.md)**: Optimieren Sie die Datenübermittlung mit der Möglichkeit, adaptive Formulardaten direkt an Microsoft SharePoint und Microsoft OneDrive zu senden. Sie können sowohl schemabasierte als auch schemabasierte Daten senden. Diese Übermittlungsaktionen sind zusätzlich zu den bereits verfügbaren Übermittlungsaktionen verfügbar.
* **[Effiziente Formularerstellung mit der Funktion &quot;Adaptives Formular als Vorlage speichern&quot;](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: Optimieren Sie den Prozess der Formularerstellung, indem Sie ein adaptives Formular als Vorlage speichern und die Vorlagen für Ihr nächstes adaptives Formular wiederverwenden.
* **[Verbinden von AEM Forms mit JDBC-unterstützten Datenbanken](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Verbinden Sie Ihr AEM Forms-Datenmodell einfach mit Datenbanken, die JDBC unterstützen. So können Sie Daten nahtlos lesen und schreiben.
* **[Integration mit REST-Endpunkten mit Open API 3.0](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Verbinden Sie as a Cloud Service AEM Forms-Formulardatenmodelle mit REST-Endpunkten, die die Open API-Spezifikation Version 3.0 unterstützen. So können Sie mühelos Daten senden und empfangen.
* **[Freigeben eines adaptiven Formulars zur Überprüfung](/help/forms/create-reviews-forms.md)**: Verwenden Sie den Adaptive Forms-Überprüfungsmechanismus, damit ein oder mehrere Überprüfer das Formular überprüfen können.


## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Autoren können Produktlisten dynamisch mit Experience Fragments anreichern (Beispiel: Banner zwischen Produktlisten platzieren).
* Die Listenkomponente unterstützt jetzt zugehörige Produkt-/Kategorieseiten, um diese dynamisch anzuzeigen.
* Es wurde Unterstützung für Peregrine-12.5-Komponenten hinzugefügt.
* Es wurde Unterstützung für das Client-seitige Laden von Preisen in Produkt-Teasern und im Karussell hinzugefügt.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* [Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md) - RDEs ermöglichen es Entwicklern, Probleme schnell zu beheben und neue Funktionen auf AEM as a Cloud Service bereitzustellen.

   Rapid Development Environments sind eine neue Art von Cloud-Umgebung, die als schnelle, konsistente und erweiterbare Methode zur Validierung dieses Codes dient, der lokal funktioniert, und auch wie erwartet in der Cloud funktioniert. Mithilfe der Befehlszeilenwerkzeuge können Sie Inhaltspakete, Pakete, Inhaltsdateien, OSGi-Konfigurationen oder Dispatcher-Konfigurationen schnell mit dem RDE &quot;synchronisieren&quot;. Siehe dies in Aktion im Video unten:

   >[!VIDEO](https://video.tv.adobe.com/v/3413508/?quality=12&learn=on)

   Nach der erfolgreichen Validierung des Codes in der RDE wird empfohlen, in einer Cloud-Entwicklungsumgebung bereitzustellen, um die Cloud Manager-Qualitätstests durchzuführen, bevor über die Produktions-Pipeline in Staging- und Produktionsumgebungen bereitgestellt wird.

   Jedes Programm enthält eine RDE und optional weitere können lizenziert werden.

   >[!NOTE]
   >
   >In den nächsten Wochen werden RDE schrittweise eingeführt. Sie können eine E-Mail an aemcs-rde-support@adobe.com senden, um zu der Zeile vorn zu springen.

* [Erweiterte Unterstützung für serverseitige API-Zugriffstoken](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) - Sie können jetzt mehrere Anmeldeinformationen generieren, was für Szenarien nützlich ist, in denen APIs unterschiedliche Merkmale aufweisen. Es ist jetzt auch möglich, Anmeldeinformationen auf Self-Service-Art zu widerrufen.

## Versionshinweise zur Wartungsversion {#maintenance}

Die neuesten Versionshinweise zur Wartungsversion finden Sie [here](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier.](/help/implementing/cloud-manager/release-notes/current.md)

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
