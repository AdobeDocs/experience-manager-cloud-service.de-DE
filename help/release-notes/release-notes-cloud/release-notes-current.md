---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: d4d44f452406e452372e409c6594ef4a256b9682
workflow-type: tm+mt
source-wordcount: '1095'
ht-degree: 31%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version der Funktion (2023.4.0) ist der 7. Juni 2023. Die nächste Version der Funktion (2023.6.0) ist für den 29. Juni 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht April 2023 an, das eine Zusammenfassung der Funktionen bietet, die der Version 2023.4.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3418681/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

* Exportieren Sie Inhaltsfragmente aus AEM as a Cloud-Service in Adobe Target als JSON-Angebote.
* Die Unterstützung für Paginierung und Sortierung in GraphQL sowie interne Caching-Verbesserungen verbessern jetzt die Leistung von entkoppelten Client-Anwendungen beim Abrufen großer Inhaltssets aus AEM mithilfe komplexer GraphQL-Abfragen und -Filter.

### Neue Funktionen in [!DNL Experience Manager Sites] Vorabversion {#prerelease-sites}

* Inhaltsfragmente und ihre Referenzen können jetzt in der [AEM-Vorschaudienst](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=en#access-preview-service) mithilfe der [Inhaltsfragmentkonsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=en), sodass Benutzer eine Vorschau des finalen Erlebnisses in einer entkoppelten Vorschau-App anzeigen können, bevor sie live gehen.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Unterstützung für WebP-Bilder hinzugefügt, um Metadaten automatisch zu extrahieren, Miniaturansichten und benutzerdefinierte Ausgabeformate zu generieren. Die Funktion Smart-Tags wird jetzt auch für diese Dateien unterstützt. Dynamic Media-Funktionen werden für WebP als Eingabeformat nicht unterstützt.

* [Verbesserungen bei der Suche](/help/assets/search-assets.md#aftersearch) - Sie können jetzt schnell die folgenden Vorgänge für die Assets ausführen, die in den Suchergebnissen angezeigt werden:

   * Workflow erstellen
   * Version erstellen
   * Zuordnen oder Aufheben der Zuordnung von Assets

     Sie müssen nicht zum Asset-Speicherort navigieren und seine Eigenschaften anzeigen, um diese Vorgänge durchzuführen.

* Verbesserungen der Benutzerfreundlichkeit der Farbsuche - Eingabefeld für Farbwerte kann jetzt bearbeitet werden und Suchergebnisse werden nur aktualisiert, wenn Sie die Farbauswahl verlassen.

* Neue Protokollunterstützung (DASH - Dynamic Adaptive Streaming über HTTP) für adaptives Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF) gestartet:
   * Adaptives Streaming (DASH/HLS) sorgt für ein besseres Zuschauererlebnis bei der Videoanzeige
   * DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weithin verwendet
   * In allen Regionen verfügbar, für die über ein Support-Ticket aktiviert werden soll

* Dynamic Media _Momentaufnahme_ - Experimentieren Sie mit Testbildern oder Dynamic Media-URLs, um die Ausgabe verschiedener Bildmodifikatoren anzuzeigen und Optimierungen für die intelligente Bildbearbeitung für Dateigröße (mit WebP- und AVIF-Bereitstellung), Netzwerkbandbreite und Gerätepixelverhältnis zu bewerten. Siehe [Dynamic Media-Schnappschuss](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html).

### Funktion in [!DNL Assets] Vorabversion {#prerelease-feature-assets}

* Dynamic Media - Die Benutzeroberfläche für einige Felder mit Bezug auf smartes Zuschneiden in einem Bildprofil wird jetzt aktualisiert und spiegelt die aktuellen Richtlinien zum Definieren eines smarten Zuschnitts wider. Siehe [Optionen für das Zuschneiden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=en#crop-options).

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-channel}

* **[Senden Sie Adaptive Forms an Microsoft® SharePoint und Microsoft® OneDrive](/help/forms/configuring-submit-actions.md)**: Verbessern Sie die Agilität der Geschäftsbenutzer, damit Sie schnell neue Formulare starten und gesendete Daten in täglichen Tools speichern können, die sie verwenden, wie z. B. die Microsoft® SharePoint-Site oder den OneDrive-Ordner.

### Funktionen der [!DNL Forms]-Vorabversion {#prerelease-features-forms}

* [Adaptives Forms im AEM Seiteneditor](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): Sie können jetzt AEM Seiteneditor verwenden, um schnell mehrere Formulare zu Ihren Siteseiten hinzuzufügen. Diese Funktion ermöglicht es Inhaltsautoren, nahtlose Datenerfassungserlebnisse innerhalb von Sites-Seiten zu erstellen, indem sie die Leistung adaptiver Formularkomponenten nutzen, einschließlich dynamischem Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Sie haben folgende Möglichkeiten:

   * Erstellen Sie ein adaptives Formular, indem Sie Formularkomponenten per Drag-and-Drop in die Adaptive Forms Container-Komponente im AEM Sites-Editor oder in Experience Fragments ziehen.
   * Verwenden Sie den Assistenten für adaptive Forms im AEM Sites-Editor, damit Sie unabhängig von einer beliebigen Sites-Seite Formulare erstellen können, damit Sie diese Formulare auf mehreren Seiten wiederverwenden können.
   * Fügen Sie mehrere Formulare zu einer Sites-Seite hinzu, optimieren Sie das Benutzererlebnis und bieten Sie mehr Flexibilität.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [Verbesserte Integration und Einhaltung von Adobe Acrobat Sign](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms ist jetzt in Adobe Acrobat Sign für Regierungsbehörden integriert. Diese Integration bietet eine erweiterte Kompatibilität und Sicherheit für e-Signaturen mit adaptiven Formularen für staatlich verbundene Konten (Regierungsabteilungen und Behörden).

  Durch die Integration mit Adobe Acrobat Sign for Government können Partner und Regierungskunden der Adobe elektronische Signaturen in Adaptive Forms für einige der wichtigsten und sensibelsten Geschäftsbereiche verwenden. Diese zusätzliche Sicherheitsschicht stellt sicher, dass alle E-Signaturen vollständig mit der Einhaltung der FedRAMP Moderate-Richtlinien konform sind, was den Regierungskunden der Adobe einen gesunden Menschenverstand verschafft.

* Verbesserte Fehlerbehebung mit benutzerdefinierten Fehler-Handlern im Regeleditor. Sie können jetzt eine benutzerdefinierte Funktion (mithilfe der Client-Bibliothek) aufrufen, wenn ein von einem externen Dienst zurückgegebener Fehler auftritt, und eine maßgeschneiderte Antwort für Endbenutzer bereitstellen. Sie können auch bestimmte Aktionen für Fehler ausführen, die von einem Dienst zurückgegeben werden. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehlercodes aufrufen oder den Kunden darüber informieren, dass der Dienst ausgefallen ist.

  Diese Funktion hilft bei der Verbesserung Ihrer gesamten Fehlerbearbeitungsfunktion, indem standardbasierte Fehlerantworten eingeführt werden, die abwärtskompatibel mit OOTB-Fehler-Handlern sind, und bietet mehr Flexibilität und Kontrolle.

### Early-Adopter-Programm für adaptive Headless-Formulare {#forms-early-adopter}

Die Benutzung von adaptiven Headless-Formularen ermöglicht es Entwicklerinnen und Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

* Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
* Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können eine E-Mail an senden `aem-forms-headless@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Zusätzliche Veröffentlichungsregionen: Sites Kunden können neben der primären Region bis zu drei Veröffentlichungsregionen lizenzieren. Der Traffic wird an zusätzliche Veröffentlichungsfarmen weitergeleitet, was zu einer geringeren Latenz bei bestimmten Anforderungen und erhöhter Widerstandsfähigkeit gegen regionale Ausfälle führt. Informationen zur Lizenzierung erhalten Sie von Ihrem Adobe-Kundenbetreuer [Zusätzliche Veröffentlichungsregionen](/help/operations/additional-publish-regions.md) für Ihre Programme.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier.](/help/implementing/cloud-manager/release-notes/current.md)

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
