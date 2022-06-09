---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: a2cdc7c4e9d3dfd52ca76afcf951fa67b279918a
workflow-type: tm+mt
source-wordcount: '776'
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
* Eine neue Konsole, die für die Headless-Verwendung von Inhaltsfragmenten optimiert ist

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* [Dynamic Media Smart Imaging](https://medium.com/adobetech/one-solution-fits-all-smart-imaging-with-aem-dynamic-media-be690b62df9f) unterstützt jetzt das AVIF-Dateiformat - weitere Verbesserung des Google Core Web Vital (Größter Inhaltsbereiter Paint), wobei AVIF im Vergleich zu WebP eine 20%ige Reduzierung der zusätzlichen Größe ermöglicht. Insgesamt ermöglicht AVIF eine Reduzierung der durchschnittlichen Größe um bis zu 41 % im Vergleich zu JPEG (in einigen Bildern sogar bis zu 76 %).

* [!UICONTROL Experience Manager Assets Brand Portal] führt nun alle zwölf Stunden automatische Aufträge aus, um alle in AEM veröffentlichten Brand Portal-Assets zu löschen. Daher müssen Sie die Assets im Beitragsordner nicht manuell löschen, um die Ordnergröße unter dem Schwellenwert zu halten. Siehe [Neue Funktionen in Experience Manager Assets Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/whats-new.html?lang=de).

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Assets] verfügbar {#prerelease-features-assets}

Experience Manager Assets verwendet jetzt Adobe Sensei AI-Funktionen [zwischen Farben in einem Bild unterscheiden und diese bei der Aufnahme automatisch als Tags anwenden](../../assets/color-tag-images.md). Diese Tags ermöglichen ein verbessertes Sucherlebnis, das auf der Farbkomposition des Bildes basiert. Sie können die Anzahl der Farben zwischen 1 und 40 konfigurieren, die mit einem Bild getaggt sind, sodass Sie später nach Bildern suchen können, die auf diesen Farben basieren.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **Integrieren von Adaptive Forms mit Microsoft® Power Automate**: Sie können jetzt ein adaptives Formular konfigurieren, um einen Microsoft® Power Automate Cloud-Fluss bei der Übermittlung auszuführen. Das konfigurierte adaptive Formular sendet erfasste Daten, Anhänge und Datensatzdokument zur Verarbeitung an Power Automate Cloud Flow zur Verarbeitung. Dies hilft Ihnen beim Erstellen benutzerdefinierter Datenerfassungserlebnisse und nutzt gleichzeitig die Leistungsfähigkeit von Microsoft® Power Automate, um Geschäftslogiken zu erfassten Daten zu erstellen und Kundenworkflows zu automatisieren.

* **Assistent zum Erstellen eines adaptiven Formulars**: Sie können den benutzerfreundlichen Assistenten für Unternehmen verwenden, um schnell Adaptive Forms zu erstellen. Der Assistent bietet eine schnelle Registerkartennavigation, mit der Sie einfach vorkonfigurierte Vorlagen, Stile, Felder und Übermittlungsoptionen auswählen können, um ein adaptives Formular zu erstellen.

   ![Assistent zum Erstellen eines adaptiven Formulars](/help/release-notes/assets/wizard.png)

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue Seite mit Eigenschaften für das Produkt-Cockpit für eine bessere und vereinfachte Übersicht

![Übersicht über die Eigenschaften des Produkt-Cockpits](/help/assets/CIF/product_cockpit_properties_overview.png)

* Verbesserte Kompatibilität und Stabilität für Connectoren von Drittanbietern in I/O Runtime

* Verbesserte Unterstützung für Überschreibungen der GQL-Client-Konfiguration (z. B. Festlegen des benutzerdefinierten Caching-Verhaltens)

### Fehlerbehebungen {#bug-fixes-cif}

* Das Feld für die Produktauswahl mit mehreren Werten zeigt das zweite und zusätzliche Produkte als ungültig an.

* Die Produktauswahl wird gelegentlich hinter Komponenten verborgen.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Die Option &quot;Struktur hinzufügen&quot;im Admin-Bildschirm des Replikationsagenten **Registerkarte &quot;Verteilen&quot;**, die zuvor als veraltet angekündigt wurde, wird am 20. Juni 2022 oder bald danach entfernt. Pakete mit einer Baumstruktur von Inhalten sollten stattdessen mit repliziert werden. [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder [Workflow &quot;Inhaltsstruktur veröffentlichen&quot;](/help/operations/replication.md#publish-content-tree-workflow).

* Die Verwendung des Administrationsbildschirms des Replikationsagenten oder der Replikations-API für die Verteilung von Inhaltspaketen, die größer als 10 MB sind (Knoten mit Eigenschaften, einschließlich Binärdateien), wird nicht mehr unterstützt und ab dem 12. September 2022 oder bald danach durchgesetzt. Stattdessen [Veröffentlichung verwalten](/help/operations/replication.md#manage-publication) oder [Workflow &quot;Inhaltsstruktur veröffentlichen&quot;](/help/operations/replication.md#publish-content-tree-workflow) muss verwendet werden, um diese großen Inhaltspakete zu replizieren. Im Juli wird eine Warnmeldung im Bildschirm des Replikationsagenten-Administrators angezeigt. **Registerkarte &quot;Verteilen&quot;** wenn versucht wird, diese großen Inhaltspakete zu replizieren, und auch im AEM Fehlerprotokoll, wenn die Replikations-API zur Replikation dieser großen Inhaltspakete verwendet wird. Im September werden die Warnungen durch Fehler ersetzt. Bitte passen Sie Ihre Prozesse entsprechend an.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation-Sicherheit {#foundation-security}

### TLS 1.0, 1.1 veraltet

Ab dem 30. Juni 2022 erfordert Experience Manager as a Cloud Service eine sicherere Netzwerkkommunikation und einen sichereren Datenaustausch mit den Benutzersystemen. AEM verwendet ausschließlich Transport Layer Security (TLS), 1.2-Protokoll. Ältere TLS-Versionen 1.0 und 1.1 werden nicht mehr unterstützt.

Wenn Sie weiterhin ältere Versionen von TLS als 1.0 und 1.1 verwenden, können Sie möglicherweise den Zugriff auf Experience Manager as a Cloud Service verlieren.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der monatlichen Cloud Manager-Versionen finden Sie [here](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Migrationstools {#migration-tools}

Eine vollständige Liste der Versionen der Migrationswerkzeuge finden Sie [here](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
