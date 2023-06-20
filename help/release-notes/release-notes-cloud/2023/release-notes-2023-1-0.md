---
title: Versionshinweise für Version 2023.1.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.1.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: f134fdbc-224b-404c-b20f-44cae8bad681
source-git-commit: bceec9ea6858b1c4c042ecd96f13ae5cac1bbee5
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 97%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.1.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.1.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2021, 2022 usw.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] 2023.1.0 mit seinen neuen Funktionen ist der 9. Februar 2023. Die nächste Version mit neuen Funktionen (2023.2.0) ist für den 12. April 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht Januar 2023 an, das eine Zusammenfassung der Funktionen bietet, die der Version 2023.1.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3413479/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in der Vorabversion von [!DNL Sites] {#prerelease-features-sites}

* Die Content-Delivery-API von AEM GraphQL unterstützt jetzt [Paging](/help/headless/graphql-api/content-fragments.md#paging) und [Sortierung](/help/headless/graphql-api/content-fragments.md#sorting) durch GraphQL, um das Abrufen und Rendern großer Inhaltssätze effizienter zu gestalten. Mit der GraphQL-Paginierung können Sie die Antwortzeit der Abfrage verbessern, indem Ergebnisse in Teilmengen zurückgegeben werden, im Gegensatz zu allem auf einmal. Die GraphQL-Sortierung ermöglicht die Platzierung von Inhaltssätzen in einer gewünschten Reihenfolge, was die Verarbeitung der Inhalte durch eine Client-Anwendung erleichtert.  Die Reaktionszeit von Abfragen wird durch Hybrid-Filter in der AEM GraphQL-Engine weiter verbessert. Inhalte werden jetzt aus JCR in kleineren Sets gelesen, die mit Abfragefiltern übereinstimmen.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Asset-Berichte bieten Administrierenden jetzt die Möglichkeit der [Erstellung von Asset-Download-Berichten](/help/assets/asset-reports.md) aus der Experience Manager Assets as a Cloud Service-Bereitstellung. Diese Daten ermöglichen es Administratoren außerdem, Einblicke aus wichtigen Erfolgsmetriken zu gewinnen, um die Akzeptanz von Assets innerhalb Ihres Unternehmens und durch Kunden zu messen.

  ![PDF-Ausgabe für andere Formate](/help/release-notes/assets/choose_report.png)

* Experience Manager Assets unterstützt jetzt zusätzlich zum Zugriffsschlüssel [SAS-Token](/help/assets/add-assets.md#asset-bulk-ingestor) für die Authentifizierung beim Herstellen einer Verbindung zur Azure Blob Storage-Datenquelle für die Aufnahme von Assets mit dem Bulk-Import-Tool.

* Die verbesserte Verwaltung von CMYK-Bildern im Asset Compute erlaubt es Ihnen, Smarte Zuschnitte und Smart-Tags für CMYK-Bilder zu generieren.

### Neue Funktionen in der Vorabversion von [!DNL Assets] {#prerelease-features-assets}

* Experience Manager Assets unterstützt jetzt die [groß angelegte Erfassung von Assets aus Google Cloud Platform](/help/assets/add-assets.md#asset-bulk-ingestor) durch das Tool für den Massenimport.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-channel}

* **[Workflow-Schritte zum Generieren nicht interaktiver PDF-Dokumente und druckbarer Ausgaben](/help/forms/aem-forms-workflow-step-reference.md)**: Automatisieren Sie die Erstellung nicht interaktiver PDF-Dokumente und druckbarer Ausgaben für Ihre Geschäftsprozesse mit AEM Workflow-Schritten, indem Sie den Prozess der Dokumenterstellung optimieren und Zeit sparen.
* **[Verwenden von Fußnoten, um Zitate oder zusätzliche Informationen in adaptiven Formularen bereitzustellen](/help/forms/footnotes-richtextsupport.md)**: Verwenden Sie Fußnoten in einem adaptiven Formular, um Informationen zum Ausfüllen oder Verwenden eines Formulars anzuzeigen. Sie können damit auch Informationen in Klammern, Copyright-Berechtigungen und andere hilfreiche Informationen bereitstellen.

### Neue Funktionen in der Vorabversion von [!DNL Forms] {#prerelease-features-forms}

* **[Verwenden der Datenerfassungskernkomponenten zum Erstellen adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de)**: [Verwenden Sie den Editor für adaptive Formulare](/help/forms/creating-adaptive-form-core-components.md), um Formulare zu erstellen, die auf standardisierten Datenerfassungskomponenten (Kernkomponenten) basieren. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung.
* **[Frontend-Pipeline-Unterstützung für die Gestaltung von Adaptive Forms auf Basis von Kernkomponenten](/help/forms/using-themes-in-core-components.md)**:Nutzen Sie leicht anpassbare AEM-basierte Designs für Kernkomponenten-basierte Adaptive Forms, indem Sie sie mit der Frontend-Implementierungs-Pipeline bereitstellen, um das Erscheinungsbild Ihrer Formulare zu verbessern.
* **[Generieren eines Datensatzdokuments für auf Kernkomponenten basierende adaptive Formulare](/help/forms/generate-document-of-record-core-components.md)**: Erstellen Sie einen Datensatz für ein auf Kernkomponenten basierendes adaptives Formular bei der Übermittlung für die langfristige Archivierung, im Druck oder im Dokumentformat.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Senden adaptiver Formulare an Microsoft SharePoint und Microsoft OneDrive](/help/forms/configuring-submit-actions.md)**: Optimieren Sie die Datenübermittlung mit der Möglichkeit, adaptive Formulardaten direkt sowohl an Microsoft SharePoint als auch an Microsoft OneDrive zu senden. Sie können sowohl schemabasierte als auch schemalose Daten senden. Diese Sendeaktionen sind zusätzlich zu den bereits verfügbaren Sendeaktionen verfügbar.
* **[Effiziente Formularerstellung mit der Funktion „Adaptives Formular als Vorlage speichern“](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: Optimieren Sie den Prozess der Formularerstellung, indem Sie ein adaptives Formular als Vorlage speichern und die Vorlagen für Ihr nächstes adaptives Formular wiederverwenden.
* **[Verbinden von AEM Forms mit JDBC-unterstützten Datenbanken](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Verbinden Sie Ihr AEM Forms-Datenmodell einfach mit Datenbanken, die JDBC unterstützen. So können Sie Daten nahtlos lesen und schreiben.
* **[Integrieren mit REST-Endpunkten beim Verwenden von OpenAPI 3.0](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Verbinden Sie Formulardatenmodelle von AEM Forms as a Cloud Service mit REST-Endpunkten, die die OpenAPI-Spezifikation in der Version 3.0 unterstützen. So können Sie mühelos Daten senden und empfangen.
* **[Freigeben eines adaptiven Formulars zur Überprüfung](/help/forms/create-reviews-forms.md)**: Verwenden Sie den Überprüfungsmechanismus adaptiver Formulare, damit eine oder mehrere Personen das Formular überprüfen können.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* [Schnelle Entwicklungsumgebungen](/help/implementing/developing/introduction/rapid-development-environments.md) – RDEs ermöglichen es Entwickelnden, Probleme schnell zu beheben und neue Funktionen auf AEM as a Cloud Service bereitzustellen.

  Schnelle Entwicklungsumgebungen sind eine neue Art von Cloud-Umgebung, die als schnelle, konsistente und erweiterbare Methode zur Prüfung dienen, ob lokal funktionierender Code auch wie erwartet in der Cloud funktioniert. Mithilfe der Befehlszeilenwerkzeuge können Sie Inhaltspakete, Pakete, Inhaltsdateien, OSGi-Konfigurationen oder Dispatcher-Konfigurationen schnell mit der RDE „synchronisieren“. Siehe dies in Aktion im Video unten:

  >[!VIDEO](https://video.tv.adobe.com/v/3413508/?quality=12&learn=on)

  Nach der erfolgreichen Validierung des Codes in der RDE wird empfohlen, ihn in einer Cloud-Entwicklungsumgebung bereitzustellen, um die Cloud Manager Quality Gates durchzuführen, bevor er über die Produktions-Pipeline in Staging- und Produktionsumgebungen bereitgestellt wird.

  Jedes Programm enthält eine RDE und weitere können optional lizenziert werden.

  >[!NOTE]
  >
  >In den nächsten Wochen werden RDEs schrittweise eingeführt. Sie können eine E-Mail an aemcs-rde-support@adobe.com senden, um an die Spitze der Warteschlange zu gelangen.

* [Erweiterte Unterstützung für Server-seitige API-Zugriffstoken](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) – Sie können jetzt mehrere Anmeldeinformationen generieren, was für Szenarien nützlich ist, in denen APIs unterschiedliche Merkmale aufweisen. Es ist jetzt auch möglich, Anmeldeinformationen in Form von Self-Service zu widerrufen.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier.](/help/implementing/cloud-manager/release-notes/current.md)

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
