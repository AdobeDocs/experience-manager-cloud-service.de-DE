---
title: Versionshinweise für Version 2022.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2022.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 1b867582-e34c-435b-b8f8-fc71dddcaccb
source-git-commit: 097c17b37cc308dc906cd4af7dc7c5d51862bdfa
workflow-type: tm+mt
source-wordcount: '805'
ht-degree: 21%

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

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2022.5.0) ist der 9. Juni 2022.
Die nächste Version (2022.6.0) ist für den 30. Juni 2022 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht vom Mai 2022 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2022.5.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/343321/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Sites] verfügbar {#prerelease-features-sites}

* Verschiedene GraphQL-Funktionen
* A [neue Konsole](/help/sites-cloud/administering/content-fragments/content-fragments-console.md) optimiert für Headless-Nutzung von Inhaltsfragmenten

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* [Dynamic Media Smart Imaging](https://medium.com/adobetech/one-solution-fits-all-smart-imaging-with-aem-dynamic-media-be690b62df9f) unterstützt jetzt das AVIF-Dateiformat - weitere Verbesserung des Google Core Web Vital (Größter Inhaltsbereiter Paint), wobei AVIF im Vergleich zu WebP eine 20%ige Reduzierung der zusätzlichen Größe ermöglicht. Insgesamt ermöglicht AVIF eine Reduzierung der durchschnittlichen Größe um bis zu 41 % im Vergleich zu JPEG (in einigen Bildern sogar bis zu 76 %).

* [!UICONTROL Experience Manager Assets Brand Portal] führt nun alle zwölf Stunden automatische Aufträge aus, um alle in AEM veröffentlichten Brand Portal-Assets zu löschen. Daher müssen Sie die Assets im Beitragsordner nicht manuell löschen, um die Ordnergröße unter dem Schwellenwert zu halten. Siehe [Neue Funktionen in Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=de).

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Assets] verfügbar {#prerelease-features-assets}

Experience Manager Assets verwendet jetzt Adobe Sensei AI-Funktionen [zwischen Farben in einem Bild unterscheiden und diese bei der Aufnahme automatisch als Tags anwenden](/help/assets/color-tag-images.md). Diese Tags ermöglichen ein verbessertes Sucherlebnis, das auf der Farbkomposition des Bildes basiert. Sie können die Anzahl der Farben zwischen 1 und 40 konfigurieren, die mit einem Bild getaggt sind, sodass Sie später nach Bildern suchen können, die auf diesen Farben basieren.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **Integrieren von Adaptive Forms mit Microsoft® Power Automate**: Sie können jetzt ein adaptives Formular konfigurieren, um einen Microsoft® Power Automate Cloud-Fluss bei der Übermittlung auszuführen. Das konfigurierte adaptive Formular sendet erfasste Daten, Anhänge und Datensatzdokument zur Verarbeitung an Power Automate Cloud Flow zur Verarbeitung. Dies hilft Ihnen beim Erstellen benutzerdefinierter Datenerfassungserlebnisse und nutzt gleichzeitig die Leistungsfähigkeit von Microsoft® Power Automate, um Geschäftslogiken zu erfassten Daten zu erstellen und Kundenworkflows zu automatisieren.

* **Assistent zum Erstellen eines adaptiven Formulars**: Sie können den benutzerfreundlichen Assistenten für Unternehmen verwenden, um schnell Adaptive Forms zu erstellen. Der Assistent bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

   ![Assistent zum Erstellen eines adaptiven Formulars](/help/release-notes/assets/wizard.png)

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Schnellzugriff auf das Produkt-Cockpit: Einfacher Zugriff auf detaillierte Produktinformationen mit einem Klick im Sites Editor

   ![Wunschliste aktivieren](/help/assets/CIF/enable-wishlist.png)

* Unterstützung für zusätzliche Marketing-Commerce-Komponenten: Komponenten können so konfiguriert werden, dass sie einen Aufruf zum Hinzufügen zum Warenkorb und zum Hinzufügen zur Wunschliste anzeigen

   ![Verknüpfung zum Produkt-Cockpit im Sites-Editor](/help/assets/CIF/sites-editor-shortcut-to-cockpit.png)


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Die Option &quot;Struktur hinzufügen&quot;im Admin-Bildschirm des Replikationsagenten **Registerkarte &quot;Verteilen&quot;**, die zuvor als veraltet angekündigt wurde, wird am 20. Juni 2022 oder bald danach entfernt. Pakete mit einer Baumstruktur von Inhalten sollten stattdessen mit repliziert werden. [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder [Workflow &quot;Inhaltsstruktur veröffentlichen&quot;](/help/operations/replication.md#publish-content-tree-workflow).

* Die Verwendung des Administrationsbildschirms des Replikationsagenten oder der Replikations-API für die Verteilung von Inhaltspaketen, die größer als 10 MB sind (Knoten mit Eigenschaften, einschließlich Binärdateien), wird nicht mehr unterstützt und ab dem 12. September 2022 oder bald danach durchgesetzt. Stattdessen [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder [Workflow &quot;Inhaltsstruktur veröffentlichen&quot;](/help/operations/replication.md#publish-content-tree-workflow) muss verwendet werden, um diese großen Inhaltspakete zu replizieren. Im Juli wird eine Warnmeldung im Bildschirm des Replikationsagenten-Administrators angezeigt. **Registerkarte &quot;Verteilen&quot;** wenn versucht wird, diese großen Inhaltspakete zu replizieren, und auch im AEM Fehlerprotokoll, wenn die Replikations-API zur Replikation dieser großen Inhaltspakete verwendet wird. Im September werden die Warnungen durch Fehler ersetzt. Bitte passen Sie Ihre Prozesse entsprechend an.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Experience Manager] verfügbar {#prerelease-features-foundation}

* AEM as a Cloud Service ist jetzt in Unified Shell integriert, um das Benutzererlebnis zu verbessern und es mit allen anderen Experience Cloud-Anwendungen zu vereinheitlichen. Siehe [Auf Unified Shell as a Cloud Service AEM](/help/overview/aem-cloud-service-on-unified-shell.md) für weitere Details.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation-Sicherheit {#foundation-security}

### TLS 1.0, 1.1 veraltet

Ab dem 30. Juni 2022 erfordert Experience Manager as a Cloud Service eine sicherere Netzwerkkommunikation und einen sichereren Datenaustausch mit den Benutzersystemen. AEM verwendet ausschließlich Transport Layer Security (TLS), 1.2-Protokoll. Ältere TLS-Versionen 1.0 und 1.1 werden nicht mehr unterstützt.

Wenn Sie weiterhin ältere Versionen von TLS als 1.0 und 1.1 verwenden, können Sie möglicherweise den Zugriff auf Experience Manager as a Cloud Service verlieren.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der monatlichen Cloud Manager-Versionen finden Sie [here](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Migrationstools {#migration-tools}

Eine vollständige Liste der Versionen der Migrationswerkzeuge finden Sie [here](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
