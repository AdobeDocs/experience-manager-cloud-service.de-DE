---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: eb42c39af65f1e10417d855e5ad476cafc97da45
workflow-type: tm+mt
source-wordcount: '733'
ht-degree: 37%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2021, 2022 usw.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren. 

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version der Funktion (2023.2.0) ist der 12. April 2023. Die nächste Version der Funktion (2023.4.0) ist für den 18. Mai 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht vom Februar 2023 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2023.2.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3416885/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] Vorabversion {#prerelease-sites}

* Exportieren Sie Inhaltsfragmente aus AEM als Cloud-Service in Adobe Target als JSON-Angebote.
* Die Unterstützung für Paginierung und Sortierung in GraphQL sowie interne Caching-Verbesserungen verbessern jetzt die Leistung von entkoppelten Clientanwendungen beim Abrufen großer Inhaltssets aus AEM mithilfe komplexer GraphQL-Abfragen und -Filter.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Neue Protokollunterstützung (DASH - Dynamic Adaptive Streaming über HTTP) für adaptives Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF):
   * Adaptives Streaming (DASH/HLS) sorgt für ein besseres Anwendererlebnis bei der Videoanzeige
   * DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weitläufig verwendet
   * Verfügbar in der NA, für die in Kürze ein Support-Ticket bei APAC, EMEA verfügbar ist

* Unterstützung für WebP-Bilder hinzugefügt, um Metadaten automatisch zu extrahieren, Miniaturansichten und benutzerdefinierte Ausgabeformate zu generieren. Die Funktionen Smart-Tag und Smartes Zuschneiden werden jetzt auch für diese Dateien unterstützt.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-channel}

* **[Verwenden der Datenerfassungskernkomponenten zum Erstellen adaptiver Formulare](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=de)**: [Verwenden Sie den Editor für adaptive Formulare](/help/forms/creating-adaptive-form-core-components.md), um Formulare zu erstellen, die auf standardisierten Datenerfassungskomponenten (Kernkomponenten) basieren. Diese Komponenten bieten Anpassungsfunktionen, kürzere Entwicklungszeiten und niedrigere Wartungskosten für Ihre Erlebnisse bei der digitalen Registrierung.

* **[Unterstützung der Frontend-Pipeline für die Formatierung von Kernkomponenten mit adaptivem Forms](/help/forms/using-themes-in-core-components.md)**: Verwenden Sie standardisierte BEM-basierte Designs für die auf Kernkomponenten basierende adaptive Forms, indem Sie sie mit der Frontend-Implementierungs-Pipeline bereitstellen, um das Erscheinungsbild Ihrer Formulare zu verbessern und die Richtlinien für das Design Ihres Unternehmens einzuhalten, die für die Marke freigegeben sind.

* **[Generieren des Datensatzdokuments für die auf Kernkomponenten basierende adaptive Forms](/help/forms/generate-document-of-record-core-components.md)**: Erstellen Sie ein Datensatzdokument mit den gesendeten Daten für Adaptive Forms, das mithilfe von Kernkomponenten für die Archivierung oder als Referenz für Endbenutzer erstellt wurde, in gedruckter Form oder im Dokumentformat.

![https://www.aemcomponents.dev/](/help/forms/assets/sample-core-components-based-adaptive-form.png)

* **[Effiziente Formularerstellung mit der Funktion &quot;Adaptives Formular als Vorlage speichern&quot;](/help/forms/template-editor.md#save-an-adaptive-form-as-template-saving-adaptive-form-as-template)**: Beschleunigen und standardisieren Sie die Formularentwicklung, indem Sie bereits als Marke genehmigte Formulare zur schnellen Wiederverwendung speichern.

* **[Verbinden von AEM Forms mit JDBC-unterstützten Datenbanken](/help/forms/configure-data-sources.md#configure-relational-database-configure-relational-database)**: Stellen Sie mithilfe des JDBC-Protokolls eine Verbindung zu Unternehmensdatenbanken direkt über AEM Cloud Service her, ohne dass Sie diese über die REST-API verfügbar machen müssen.

* **[Integration mit REST-Endpunkten mit Open API 3.0](/help/forms/configure-data-sources.md#configure-restful-services-open-api-specification-version-20-configure-restful-services-swagger-version30)**: Nahtlose Integration in Datensatzsysteme, die Open API 3.0 zum Speichern und Abrufen von Daten mithilfe von Formulardatenmodellen unterstützen.

* **[Freigeben eines adaptiven Formulars zur Überprüfung](/help/forms/create-reviews-forms.md)**: Verwenden Sie den Überprüfungsmechanismus adaptiver Formulare, damit eine oder mehrere Personen das Formular überprüfen können.


### Funktionen in [!DNL Forms] Vorabversion {#prerelease-features-forms}

* **[Senden von Adaptive Forms an Microsoft SharePoint und Microsoft OneDrive](/help/forms/configuring-submit-actions.md)**: Verbessern Sie die Agilität von Geschäftsbenutzern, neue Formulare schnell zu starten und gesendete Daten in täglichen Tools zu speichern, die sie verwenden, wie z. B. die Microsoft SharePoint-Site oder den OneDrive-Ordner.

![Senden von Adaptive Forms an Microsoft SharePoint und Microsoft OneDrive](/help/forms/assets/onedrive-and-sharepoint.jpg)


## Headless-Adaptive Forms-Programm für frühe Anwender {#forms-early-adopter}

Verwenden Sie Headless Adaptive Forms, damit Ihre Entwickler interaktive Formulare erstellen, veröffentlichen und verwalten können, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. Headless-adaptive Formulare unterstützen Sie bei Folgendem:

* Erstellen Sie hochwertige Mehrkanal-Formulare in der gewünschten Programmiersprache.
* Native Integration von Formularen in Ihre Desktop- und mobilen Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an aem-forms-headless@adobe.com senden, um dem frühen Adopter-Programm beizutreten.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier.](/help/implementing/cloud-manager/release-notes/current.md)

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
