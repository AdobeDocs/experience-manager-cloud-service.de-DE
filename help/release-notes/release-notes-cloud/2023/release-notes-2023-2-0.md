---
title: Versionshinweise für Version 2023.2.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.2.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 671056e6-84cc-4c2c-bca3-fde68d5cc835
feature: Release Information
role: Admin
source-git-commit: b4ffcddddfcd990c359380071f19b5442dee9eb2
workflow-type: tm+mt
source-wordcount: '716'
ht-degree: 100%

---

# Versionshinweise für Version 2023.2.0 von [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.2.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2021, 2022 usw.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.2.0) ist der 12. April 2023. Die nächste Versionsveröffentlichung (2023.4.0) ist für den 7. Juni 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video zur Versionsübersicht Februar 2023 an, das eine Zusammenfassung der Funktionen bietet, die der Version 2023.2.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3416885/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in der Vorabversion von [!DNL Experience Manager Sites] {#prerelease-sites}

* Exportieren Sie Inhaltsfragmente aus AEM as a Cloud-Service in Adobe Target als JSON-Angebote.
* Die Unterstützung für Paginierung und Sortierung in GraphQL sowie interne Caching-Verbesserungen verbessern jetzt die Leistung von entkoppelten Client-Anwendungen beim Abrufen großer Inhaltssets aus AEM mithilfe komplexer GraphQL-Abfragen und -Filter.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Neue Protokollunterstützung (DASH – Dynamic Adaptive Streaming über HTTP) für adaptives Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF):
   * Adaptives Streaming (DASH/HLS) sorgt für ein besseres Zuschauererlebnis bei der Videoanzeige
   * DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weithin verwendet

* Unterstützung für WebP-Bilder hinzugefügt, um Metadaten automatisch zu extrahieren, Miniaturansichten und benutzerdefinierte Ausgabeformate zu generieren. Die Funktionen „Smartes Markieren“ und „Smartes Zuschneiden“ werden jetzt auch für diese Dateien unterstützt.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-channel}

* **[Verwenden der Datenerfassungskernkomponenten zum Erstellen adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de)**: [Verwenden Sie den Editor für adaptive Formulare](/help/forms/creating-adaptive-form-core-components.md), um Formulare zu erstellen, die auf standardisierten Datenerfassungskomponenten (Kernkomponenten) basieren. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung.

* **[Frontend-Pipeline-Unterstützung für die Gestaltung von adaptiven Formularen auf Basis von Kernkomponenten](/help/forms/using-themes-in-core-components.md)**: Nutzen Sie leicht anpassbare AEM-basierte Designs für Kernkomponenten-basierte adaptive Formulare, indem Sie sie mit der Frontend-Implementierungs-Pipeline implementieren, um das Look-and-Feel Ihrer Formulare zu verbessern.

* **[Generieren des Datensatzdokuments für die auf Kernkomponenten basierenden adaptiven Formulare](/help/forms/generate-document-of-record-core-components.md)**: Erstellen Sie ein Datensatzdokument mit den gesendeten Daten für adaptive Formulare, das mithilfe von Kernkomponenten für die Archivierung oder als Referenz für Endbenutzerinnen und -benutzer erstellt wurde, in gedruckter Form oder im Dokumentformat.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Effiziente Formularerstellung mit der Funktion „Adaptives Formular als Vorlage speichern“](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: Beschleunigen und standardisieren Sie die Formularentwicklung, indem Sie vorhandene, von der Marke genehmigte Formulare zur schnellen Wiederverwendung speichern.

* **[Verbinden von AEM Forms mit JDBC-unterstützten Datenbanken](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Stellen Sie mithilfe des JDBC-Protokolls eine Verbindung zu Unternehmensdatenbanken direkt über den AEM Cloud Service her, ohne dass Sie diese über die REST-API verfügbar machen müssen.

* **[Integration mit REST-Endpunkten unter Verwendung von Open API 3.0](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Nahtlose Integration in Datensatzsysteme, die Open API 3.0 zum Speichern und Abrufen von Daten mithilfe von Formulardatenmodellen unterstützen.

* **[Freigeben eines adaptiven Formulars zur Überprüfung](/help/forms/create-reviews-forms.md)**: Verwenden Sie den Überprüfungsmechanismus adaptiver Formulare, damit eine oder mehrere Personen das Formular überprüfen können.


### Funktionen der [!DNL Forms]-Vorabversion {#prerelease-features-forms}

* **[Senden von adaptiven Formularen an Microsoft SharePoint und Microsoft OneDrive](/help/forms/configuring-submit-actions.md)**: Verbessern Sie die Agilität von Business-Anwenderinnen und -Anwendern, neue Formulare schnell zu starten und gesendete Daten in alltäglichen Tools zu speichern, die sie verwenden, wie z. B. die Microsoft SharePoint-Site oder den OneDrive-Ordner.

![Senden von adaptiven Formularen an Microsoft SharePoint und Microsoft OneDrive](/help/forms/assets/onedrive-and-sharepoint.jpg)


## Early-Adopter-Programm für adaptive Headless-Formulare {#forms-early-adopter}

Die Benutzung von adaptiven Headless-Formularen ermöglicht es Entwicklerinnen und Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

* Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
* Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an aem-forms-headless@adobe.com senden, um am Early-Adopter-Programm teilzunehmen.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
