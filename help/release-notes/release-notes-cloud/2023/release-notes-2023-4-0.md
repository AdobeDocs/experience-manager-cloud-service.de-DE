---
title: Versionshinweise für Version 2023.4.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.4.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: c34aedee-e45a-4e2a-ae7f-930bc0cc026f
feature: Release Information
role: Admin
source-git-commit: b4ffcddddfcd990c359380071f19b5442dee9eb2
workflow-type: tm+mt
source-wordcount: '1112'
ht-degree: 100%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.4.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.4.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.4.0) war der 7. Juni 2023. Die nächste Version (2023.6.0) ist für den 29. Juni 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Übersichtsvideo zur Version April 2023 an, das eine Zusammenfassung der Funktionen bietet, die in Version 2023.4.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3418681/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

* Exportieren Sie Inhaltsfragmente aus AEM as a Cloud Service in Adobe Target im JSON-Format und erstellen Sie entsprechende JSON-Angebote in Target.
* Die Unterstützung für Paginierung und Sortierung in GraphQL sowie interne Caching-Verbesserungen verbessern jetzt die Leistung von entkoppelten Client-Anwendungen beim Abrufen großer Inhaltssätze aus AEM mithilfe komplexer GraphQL-Abfragen und -Filter.

### Neue Funktionen in der Vorabversion von [!DNL Experience Manager Sites] {#prerelease-sites}

* Inhaltsfragmente und ihre Referenzen können jetzt mithilfe der [Inhaltsfragmentkonsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=de) im [AEM-Vorschau-Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/using-cloud-manager/manage-environments.html?lang=de#access-preview-service) veröffentlicht werden, sodass Benutzerinnen und Benutzer eine Vorschau des endgültigen Erlebnisses in einer entkoppelten Vorschau-App anzeigen können, bevor sie live gehen.
* Bilder können jetzt dynamisch für die Web-Bereitstellung in Headless-Szenarien mit AEM GraphQL optimiert werden. [Abfragevariablen](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/how-to/images.html?lang=de#query-variables) können in GraphQL-Abfragen definiert werden, um zuzulassen, dass entkoppelte Client-Anwendungen entsprechend optimierte Bilder von AEM anfordern können.
* Tags für [Inhaltsfragmentvarianten](https://experienceleague.adobe.com/docs/experience-manager-65/assets/content-fragments/content-fragments-variations.html?lang=de) können jetzt über die Inhaltsbereitstellungs-API von AEM GraphQL an JSON ausgegeben werden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Unterstützung für WebP-Bilder hinzugefügt, um Metadaten automatisch zu extrahieren sowie Miniaturansichten und benutzerdefinierte Ausgabeformate zu generieren. Die Funktion „Smart Tags“ wird jetzt auch für diese Dateien unterstützt. Dynamic Media-Funktionen werden für WebP als Eingabeformat nicht unterstützt.

* [Verbesserungen des Sucherlebnisses](/help/assets/search-assets.md#aftersearch): Sie können jetzt schnell die folgenden Vorgänge für die Assets ausführen, die in den Suchergebnissen angezeigt werden:

   * Erstellen eines Workflows
   * Version erstellen
   * Zuordnung für Assets herstellen oder aufheben

     Sie müssen nicht erst zum Asset-Speicherort navigieren und seine Eigenschaften anzeigen, um diese Vorgänge durchzuführen.

* Verbesserungen der Benutzerfreundlichkeit der Farbsuche: Das Eingabefeld für Farbwerte kann jetzt bearbeitet werden, und Suchergebnisse werden nur aktualisiert, wenn Sie die Farbauswahl verlassen.

* Neue Protokollunterstützung (DASH – Dynamic Adaptive Streaming über HTTP) für adaptives Streaming in Dynamic Media-Videobereitstellung (mit aktiviertem CMAF) eingeführt:
   * Adaptives Streaming (DASH/HLS) sorgt für ein besseres Zuschauererlebnis bei der Videoanzeige
   * DASH ist das internationale Standardprotokoll für adaptives Video-Streaming und wird in der Branche weithin verwendet

* Dynamic Media _Snapshot_: Experimentieren Sie mit Testbildern oder URLs für dynamische Medien, um die Ausgabe verschiedener Bildmodifikatoren zu sehen und die Optimierungen der intelligenten Bildbearbeitung für Dateigröße (mit WebP- und AVIF-Übertragung), Netzwerkbandbreite und Geräte-Pixel-Verhältnis zu bewerten. Siehe [Dynamic Media Snapshot](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html?lang=de).

### Funktion der [!DNL Assets]-Vorabversion {#prerelease-feature-assets}

* Dynamic Media: Die Benutzeroberfläche für einige Felder mit Bezug auf smartes Zuschneiden in einem Bildprofil wurde aktualisiert und spiegelt jetzt die aktuellen Richtlinien zum Definieren eines smarten Zuschnitts wider. Siehe [Optionen für das Zuschneiden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/dynamicmedia/image-profiles.html?lang=de#crop-options).

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-channel}

* **[Senden von adaptiven Formularen an Microsoft® SharePoint und Microsoft® OneDrive](/help/forms/configuring-submit-actions.md)**: Verbessern Sie die Agilität von Business-Anwenderinnen und -Anwendern, neue Formulare schnell zu starten und gesendete Daten in alltäglichen Tools zu speichern, die sie verwenden, wie z. B. die Microsoft® SharePoint-Site oder der OneDrive-Ordner.

### Funktionen der [!DNL Forms]-Vorabversion {#prerelease-features-forms}

* [Adaptive Formulare im AEM-Seiteneditor](/help/forms/create-or-add-an-adaptive-form-to-aem-sites-page.md): Sie können jetzt den AEM-Seiteneditor verwenden, um schnell mehrere Formulare zu erstellen und sie zu Ihren Sites-Seiten hinzuzufügen. Diese Funktion ermöglicht es Inhaltsautorinnen und -autoren, nahtlose Datenerfassungserlebnisse innerhalb von Sites-Seiten zu erstellen, indem sie die Möglichkeiten der Komponenten adaptiver Formulare nutzen, einschließlich dynamisches Verhalten, Überprüfungen, Datenintegration, Generierung von Datensatzdokumenten und Automatisierung von Geschäftsprozessen. Sie haben folgende Möglichkeiten:

   * Erstellen Sie ein adaptives Formular, indem Sie Formularkomponenten per Drag-and-Drop in die Container-Komponente für adaptive Formulare im AEM Sites-Editor oder in Experience Fragments ziehen.
   * Verwenden Sie den Assistenten für adaptive Formulare im AEM Sites-Editor, damit Sie unabhängig von einer Sites-Seite Formulare erstellen können. So können Sie solche Formulare auf mehreren Seiten wiederverwenden.
   * Fügen Sie mehrere Formulare zu einer Sites-Seite hinzu, was das Benutzererlebnis optimiert und mehr Flexibilität bietet.

     >[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

* [Adobe Acrobat Sign Solutions für Behörden](/help/forms/adobe-sign-integration-adaptive-forms.md): AEM Forms können jetzt in Adobe Acrobat Sign Solutions für Behörden integriert werden. Diese Integration bietet eine erweiterte Kompatibilität und Sicherheit für E-Signaturen bei Einreichungen von adaptiven Formularen für behördliche Konten (Regierungsstellen und -agenturen).

  Durch die Integration mit Adobe Acrobat Sign für Behörden können Partner und Regierungskunden von Adobe elektronische Signaturen in adaptiven Formularen für einige der wichtigsten und sensibelsten Geschäftsbereiche verwenden. Diese zusätzliche Sicherheitsschicht stellt sicher, dass alle E-Signaturen vollständig konform mit der Richtlinie „FedRAMP Moderate“ sind, was Regierungskunden von Adobe Gewissheit bietet.

* Verbesserte Fehlerbehebung mit benutzerdefinierten Fehler-Handlern im Regeleditor: Sie können jetzt eine benutzerdefinierte Funktion (mithilfe der Client-Bibliothek) aufrufen, wenn ein von einem externen Dienst zurückgegebener Fehler auftritt, und eine maßgeschneiderte Antwort für Endbenutzerinnen und Endbenutzer bereitstellen. Oder Sie können bestimmte Aktionen für Fehler ausführen, die von einem Dienst zurückgegeben werden. Sie können beispielsweise einen benutzerdefinierten Workflow im Back-End für bestimmte Fehler-Codes aufrufen oder die Kundin bzw. den Kunden darüber informieren, dass der Dienst nicht verfügbar ist.

  Diese Funktion hilft bei der Verbesserung Ihrer gesamten Fehlerhandhabung, indem standardbasierte Fehlerantworten eingeführt werden, die abwärtskompatibel mit OOTB-Fehler-Handlern sind, und bietet mehr Flexibilität und Kontrolle.

### Early-Adopter-Programm für adaptive Headless-Formulare {#forms-early-adopter}

Die Benutzung von adaptiven Headless-Formularen ermöglicht es Entwicklerinnen und Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

* Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
* Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an `aem-forms-headless@adobe.com` senden, um am Early-Adopter-Programm teilzunehmen.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Zusätzliche Veröffentlichungsregionen: Sites-Kundinnen und -Kunden können neben der primären Region bis zu drei Veröffentlichungsregionen zusätzlich lizenzieren. Der Traffic wird an zusätzliche Veröffentlichungsfarmen weitergeleitet, was zu einer geringeren Latenz bei bestimmten Anforderungen und erhöhter Widerstandsfähigkeit gegen regionale Ausfälle führt. Informationen über die [Lizenzierung zusätzlicher Veröffentlichungsregionen](/help/operations/additional-publish-regions.md) für Ihre Programme erhalten Sie von Ihrer Adobe-Kundenbetreuung.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
