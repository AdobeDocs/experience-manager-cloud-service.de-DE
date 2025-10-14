---
title: Versionshinweise für Version 2022.5.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2022.5.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 1b867582-e34c-435b-b8f8-fc71dddcaccb
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '800'
ht-degree: 67%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2022.5.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den Funktionen der Version 2022.5.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version (2022.5.0) von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] war der 9. Juni 2022.
Die Veröffentlichung der nächsten Version (2022.6.0) ist für den 30. Juni 2022 geplant.

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2022.5.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version vom Mai 2022:

>[!VIDEO](https://video.tv.adobe.com/v/343321/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Sites] verfügbar {#prerelease-features-sites}

* Verschiedene GraphQL-Funktionen
* Eine [neue Konsole](/help/sites-cloud/administering/content-fragments/managing.md#content-fragments-console), die für die Headless-Nutzung von Inhaltsfragmenten optimiert wurde

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* [Dynamic Media Smart Imaging](https://medium.com/adobetech/one-solution-fits-all-smart-imaging-with-aem-dynamic-media-be690b62df9f) unterstützt jetzt das AVIF-Dateiformat und bietet eine weitere Verbesserung von Google Core Web Vital (Largest Contentful Paint), wobei AVIF gegenüber WebP eine zusätzliche Größenreduktion um 20 % ermöglicht. Insgesamt ermöglicht AVIF eine durchschnittliche Größenreduktion um bis zu 41 % im Vergleich zu JPEG (bei einigen Bildern sogar bis zu 76 %).

* [!UICONTROL Experience Manager Assets Brand Portal] führt jetzt alle 12 Stunden automatische Vorgänge aus, um alle in AEM veröffentlichten Brand Portal-Assets zu löschen. Daher müssen Sie die Assets im Beitragsordner nicht manuell löschen, um die Ordnergröße unter dem Schwellenwert zu halten. Siehe [Neue Funktionen in Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=de).

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Assets] verfügbar {#prerelease-features-assets}

Experience Manager Assets verwendet jetzt die KI-Funktionen von Adobe Sensei, um [zwischen Farben in einem Bild zu unterscheiden und diese bei der Aufnahme automatisch als Tags anzuwenden](/help/assets/color-tag-images.md). Diese Tags ermöglichen eine einfachere Suche, die auf der Farbkomposition des Bildes basiert. Sie können die Anzahl der Farben zwischen 1 und 40 konfigurieren, mit denen ein Bild getaggt werden kann, sodass Sie später nach Bildern suchen können, die auf diesen Farben basieren.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **Integrieren von adaptiven Formularen mit Microsoft® Power Automate**: Sie können jetzt ein adaptives Formular konfigurieren, um bei der Übermittlung einen Microsoft® Power Automate Cloud-Fluss auszuführen. Das konfigurierte adaptive Formular sendet erfasste Daten, Anhänge und das Datensatzdokument zur Verarbeitung an den Cloud-Fluss von Power Automate. Dies hilft Ihnen beim Erstellen benutzerdefinierter Datenerfassungserlebnisse und nutzt gleichzeitig die Leistungsfähigkeit von Microsoft® Power Automate, um Geschäftslogiken zu erfassten Daten zu erstellen und Kunden-Workflows zu automatisieren.

* **Assistent zum Erstellen eines adaptiven Formulars**: Sie können den benutzerfreundlichen Assistenten für Unternehmen verwenden, um schnell adaptive Forms zu erstellen. Der Assistent bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

  ![Assistent zum Erstellen eines adaptiven Formulars](/help/release-notes/assets/wizard.png)

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Schnellzugriff auf das Produkt-Cockpit: Einfacher Zugriff auf detaillierte Produktinformationen mit einem Klick im Sites-Editor

<!-- Image was not found during PR validation despite correct path   ![Enable wantlist](/help/assets/CIF/enable-wishlist.png) -->

* Unterstützung für zusätzliche Marketing-Commerce-Komponenten: Komponenten können so konfiguriert werden, dass sie einen Aufruf zum Hinzufügen zum Warenkorb und zum Hinzufügen zur Wunschliste anzeigen

  ![Verknüpfung mit dem Produkt-Cockpit im Sites-Editor](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Die Option „Struktur hinzufügen“ auf der Registerkarte „Verteilen **im Administrator-Bildschirm des Replikationsagenten,** zuvor als veraltet angekündigt wurde, wurde am 20. Juni 2022 oder kurz danach entfernt. Pakete mit einer Baumstruktur mit Inhalten sollten stattdessen mithilfe von [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder mit dem Workflow [Inhaltsstruktur veröffentlichen](/help/operations/replication.md#publish-content-tree-workflow) repliziert werden.

* Die Verwendung des Administrationsbildschirms des Replikationsagenten oder der Replikations-API für die Verteilung von Inhaltspaketen, die größer als 10 MB sind (Knoten mit Eigenschaften, ohne Binärdateien), wird nicht mehr unterstützt und wird am 12. September 2022 oder bald danach erzwungen. Stattdessen muss [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder der Workflow [Inhaltsstruktur veröffentlichen](/help/operations/replication.md#publish-content-tree-workflow) verwendet werden, um derart große Inhaltspakete zu replizieren. Wenn versucht wird, derart große Inhaltspakete zu replizieren, wird ab Juli auf der Registerkarte **Verteilen** des Replikationsagenten eine Warnmeldung angezeigt. Ebenso erscheint eine Warnmeldung im AEM-Fehlerprotokoll, wenn die Replikations-API verwendet wird, um solche großen Inhaltspakete zu replizieren. Im September wurden die Warnungen durch Fehler ersetzt. Anpassen der Prozesse entsprechend.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Experience Manager] verfügbar {#prerelease-features-foundation}

* AEM as a Cloud Service ist jetzt in Unified Shell integriert, um das Benutzererlebnis zu verbessern und es mit allen anderen Experience Cloud-Programmen zu vereinheitlichen. Weitere Informationen finden Sie unter [AEM as a Cloud Service &#x200B;](/help/overview/aem-cloud-service-on-unified-shell.md) Unified Shell.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation – Sicherheit {#foundation-security}

### TLS 1.0, 1.1 veraltet

Ab dem 30. Juni 2022 erfordert Experience Manager as a Cloud Service eine sicherere Netzwerkkommunikation und einen sichereren Datenaustausch mit Benutzersystemen. AEM verwendet ausschließlich das TLS 1.2-Protokoll (Transport Layer Security). Ältere TLS-Versionen 1.0 und 1.1 werden jetzt nicht mehr unterstützt.

Wenn Sie weiterhin ältere Versionen von TLS als 1.0 und 1.1 verwenden, können Sie möglicherweise nicht mehr auf Experience Manager as a Cloud Service zugreifen.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
