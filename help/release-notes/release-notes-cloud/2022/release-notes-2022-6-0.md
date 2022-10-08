---
title: Versionshinweise für Version 2022.6.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2022.6.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: cf2133dc-56cd-4a07-ab11-72e16f015ff5
source-git-commit: ca849bd76e5ac40bc76cf497619a82b238d898fa
workflow-type: tm+mt
source-wordcount: '642'
ht-degree: 22%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2022.6.0) ist der 30. Juni 2022.

Die nächste Version (2022.7.0) ist für den 8. August 2022 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht vom Juni 2022 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2022.6.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/344308/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#sites-features}

* Eine neue [Benutzeroberfläche](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) ist jetzt für Inhaltsadministratoren und Inhaltsautoren verfügbar, um Inhaltsfragmente effizient zu verwalten (Aktionen wie Veröffentlichung, Rückgängigmachen der Veröffentlichung, Kopieren, Verschieben usw.), zu durchsuchen/filtern und für Headless-Anwendungsfälle zu erstellen.

   ![Inhaltsfragmentkonsole](/help/release-notes/assets/cf-ui.png)

* Die neue [Inhaltskomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/tableofcontents.html) funktioniert nicht nur mit den Kernkomponenten, sondern mit allen Komponenten, indem auf Inhaltsseiten automatisch ToCs gerendert wird. Da es Server-seitig gerendert und vollständig vom Dispatcher zwischengespeichert wird, ist es auch effizient zu laden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

Experience Manager Assets verwendet jetzt Adobe Sensei AI-Funktionen [zwischen Farben in einem Bild unterscheiden und diese bei der Aufnahme automatisch als Tags anwenden](/help/assets/color-tag-images.md). Diese Tags ermöglichen ein verbessertes Sucherlebnis, das auf der Farbkomposition des Bildes basiert. Sie können die Anzahl der Farben zwischen 1 und 40 konfigurieren, die mit einem Bild getaggt sind, sodass Sie später nach Bildern suchen können, die auf diesen Farben basieren.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#forms-features}

* **[Integrieren von Adaptive Forms mit Microsoft® Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)**: Sie können jetzt ein adaptives Formular konfigurieren, um einen Microsoft® Power Automate Cloud-Fluss bei der Übermittlung auszuführen. Das konfigurierte adaptive Formular sendet erfasste Daten, Anhänge und Datensatzdokument zur Verarbeitung an Power Automate Cloud Flow zur Verarbeitung. Dies hilft Ihnen beim Erstellen benutzerdefinierter Datenerfassungserlebnisse und nutzt gleichzeitig die Leistungsfähigkeit von Microsoft® Power Automate, um Geschäftslogiken zu erfassten Daten zu erstellen und Kundenworkflows zu automatisieren.

* **Assistent zum Erstellen eines adaptiven Formulars**: Sie können den benutzerfreundlichen Assistenten für Unternehmen verwenden, um schnell Adaptive Forms zu erstellen. Der Assistent bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

   ![Assistent zum Erstellen eines adaptiven Formulars](/help/release-notes/assets/wizard.png)

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue Seite mit Eigenschaften für das Produkt-Cockpit für eine bessere und vereinfachte Übersicht

![Übersicht über die Eigenschaften des Produkt-Cockpits](/help/assets/CIF/product_cockpit_properties_overview.png)

* Verbesserte Kompatibilität und Stabilität für Connectoren von Drittanbietern in I/O Runtime

* Verbesserte Unterstützung für Überschreibungen der GQL-Client-Konfiguration (z. B. Festlegen des Verhaltens beim benutzerdefinierten Caching)

* Mehrere Commerce-Endpunkte werden jetzt nativ unterstützt und können über Cloud Manager konfiguriert werden. Details finden Sie im CIF-Blog . [here](https://medium.com/adobetech/use-aem-as-a-cloud-service-with-multiple-adobe-commerce-systems-9295612a9554).


### Fehlerbehebungen {#bug-fixes-cif}

* Das Feld für die Produktauswahl mit mehreren Werten zeigt das zweite und zusätzliche Produkte als ungültig an.

* Die Produktauswahl wird gelegentlich hinter Komponenten verborgen.

## Referenz-Demos-Add-on {#cloud-services-demos}

### Neue Funktionen {#what-is-new-demos}

* Neue WKND Content &amp; Commerce-Vorlage, die WKND mit einem E2E-Shopping-Erlebnis mit Produktkatalog, Warenkorb, Checkout und myAccount erweitert. Diese Vorlage verwendet CIF und seine CIF-Kernkomponenten, daher müssen Sie auch das CIF-Add-on installieren. Details finden Sie im CIF-Blog . [here](https://medium.com/adobetech/learn-how-to-create-a-shoppable-experience-with-the-new-wknd-reference-site-and-cif-b3b2c161f67e).

![WKND-Shop](/help/assets/CIF/wknd_shop.png)

![WKND pdp](/help/assets/CIF/wknd_pdp.png)

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Wie in den Versionshinweisen vom Mai (2022.5.0) erwähnt, enthält die Option &quot;Struktur hinzufügen&quot;im Admin-Bildschirm des Replikationsagenten **Verteilen** wurde entfernt. Pakete mit einer Baumstruktur von Inhalten sollten stattdessen mit repliziert werden. [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder [Inhaltsstruktur veröffentlichen](/help/operations/replication.md#manage-publication#publish-content-tree-workflow) Arbeitsablauf.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
