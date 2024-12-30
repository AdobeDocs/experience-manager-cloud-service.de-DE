---
title: Versionshinweise für Version 2022.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2022.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: cf2133dc-56cd-4a07-ab11-72e16f015ff5
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '633'
ht-degree: 81%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2022.6.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den Funktionen der Version 2022.6.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2022.6.0) war der 30. Juni 2022.

Die nächste Version (2022.7.0) ist für den 8. August 2022 geplant.

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2022.6.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version Juni 2022:

>[!VIDEO](https://video.tv.adobe.com/v/344308/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#sites-features}

* Eine neue [Benutzeroberfläche](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console) ist jetzt für Inhaltsadministratoren und Inhaltsautoren verfügbar, um Inhaltsfragmente effizient zu verwalten (z. B. Veröffentlichen, Rückgängigmachen der Veröffentlichung, Kopieren, Verschieben usw.), zu durchsuchen/filtern und für Headless-Anwendungsfälle zu erstellen.

  ![Inhaltsfragment-Konsole](/help/release-notes/assets/cf-ui.png)

* Die neue [Inhaltsverzeichnis-Komponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/tableofcontents.html?lang=de) funktioniert nicht nur mit den Kernkomponenten, sondern mit allen Komponenten, indem auf Inhaltsseiten automatisch Inhaltsverzeichnisse gerendert werden. Da dies Server-seitig gerendert und vollständig vom Dispatcher zwischengespeichert wird, ist es auch effizient zu laden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

Experience Manager Assets verwendet jetzt KI-Funktionen von Adobe Sensei, um [zwischen Farben in einem Bild zu unterscheiden und diese bei der Aufnahme automatisch als Tags anzuwenden](/help/assets/color-tag-images.md). Diese Tags ermöglichen eine einfachere Suche, die auf der Farbkomposition des Bildes basiert. Sie können die Anzahl der Farben zwischen 1 und 40 konfigurieren, mit denen ein Bild getaggt werden kann, sodass Sie später nach Bildern suchen können, die auf diesen Farben basieren.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#forms-features}

* **[Integrieren von adaptiven Formularen mit Microsoft® Power Automate](/help/forms/forms-microsoft-power-automate-integration.md)**: Sie können jetzt ein adaptives Formular so konfigurieren, dass bei der Übermittlung ein Microsoft® Power Automate-Cloud-Fluss ausgeführt wird. Das konfigurierte adaptive Formular sendet erfasste Daten, Anhänge und das Datensatzdokument zur Verarbeitung an den Cloud-Fluss von Power Automate. Dies hilft Ihnen beim Erstellen benutzerdefinierter Datenerfassungserlebnisse und nutzt gleichzeitig die Leistungsfähigkeit von Microsoft® Power Automate, um Geschäftslogiken zu erfassten Daten zu erstellen und Kunden-Workflows zu automatisieren.

* **Assistent zum Erstellen eines adaptiven Formulars**: Sie können den benutzerfreundlichen Assistenten für Unternehmen verwenden, um schnell adaptive Formulare zu erstellen. Der Assistent bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

  ![Assistent zum Erstellen eines adaptiven Formulars](/help/release-notes/assets/wizard.png)

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue Seite mit Eigenschaften für das Produkt-Cockpit für eine bessere und vereinfachte Übersicht

![Übersicht über die Eigenschaften des Produkt-Cockpits](/help/assets/CIF/product_cockpit_properties_overview.png)

* Verbesserte Kompatibilität und Stabilität für Connectoren von Drittanbietern in I/O Runtime

* Verbesserte Unterstützung für Überschreibungen der GQL-Client-Konfiguration (z. B. Festlegen des benutzerdefinierten Caching-Verhaltens)

* Mehrere Commerce-Endpunkte werden jetzt nativ unterstützt und können über Cloud Manager konfiguriert werden. Details finden Sie im CIF-Blog [hier](https://medium.com/adobetech/use-aem-as-a-cloud-service-with-multiple-adobe-commerce-systems-9295612a9554).


### Fehlerbehebungen {#bug-fixes-cif}

* Das Feld für die Produktauswahl mit mehreren Werten zeigt das zweite und weitere Produkte als ungültig an.

* Die Produktauswahl bleibt gelegentlich hinter Komponenten verborgen

## Referenzdemo-Add-on {#cloud-services-demos}

### Neue Funktionen {#what-is-new-demos}

* Neue WKND Content- and Commerce-Vorlage, die WKND um ein E2E-Shopping-Erlebnis mit Produktkatalog, Warenkorb, Checkout und myAccount erweitert. Diese Vorlage verwendet CIF und seine CIF-Kernkomponenten, daher müssen Sie auch das CIF-Add-on installieren. Details finden Sie im CIF-Blog [hier](https://medium.com/adobetech/learn-how-to-create-a-shoppable-experience-with-the-new-wknd-reference-site-and-cif-b3b2c161f67e).

![WKND-Shop](/help/assets/CIF/wknd_shop.png)

![WKND pdp](/help/assets/CIF/wknd_pdp.png)

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Wie in den Versionshinweisen vom Mai (2022.5.0) erwähnt, wurde die Option „Struktur hinzufügen“ auf der Registerkarte „Verteilen **im Admin-Bildschirm** Replikationsagenten entfernt. Pakete mit einer Baumstruktur von Inhalten sollten stattdessen mit [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder dem Workflow [Inhaltsstruktur veröffentlichen](/help/operations/replication.md#manage-publication#publish-content-tree-workflow) repliziert werden.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
