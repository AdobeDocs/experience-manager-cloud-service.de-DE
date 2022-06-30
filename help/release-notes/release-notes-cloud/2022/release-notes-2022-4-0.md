---
title: Versionshinweise für Version 2022.4.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2022.4.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 6c86838a-cabf-4770-b1ae-618af70193a2
source-git-commit: f42cf1b82f7cf42be2afd30d69d71354fe0afeb3
workflow-type: tm+mt
source-wordcount: '573'
ht-degree: 29%

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

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2022.4.0) ist der 5. Mai 2022.
Die nächste Version (2022.5.0) ist für den 9. Juni 2022 geplant.

## Video zur Version {#release-video}

Sehen Sie sich die [Versionsübersicht April 2022](https://video.tv.adobe.com/v/342612?quality=12) Video mit einer Zusammenfassung der Funktionen, die in der Version 2022.4.0 hinzugefügt wurden.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#sites-features}

* Die Datentypen des Inhaltsmodells können jetzt als [übersetzbar](/help/assets/content-fragments/content-fragments-models.md#properties) mit einem einfachen Kontrollkästchen im Inhaltsmodell-Editor. Darüber hinaus werden AEM Übersetzungsregeln und -konfigurationen automatisch aktualisiert.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Sie können jetzt [sort Tags](/help/assets/organize-assets.md#use-tags-to-organize-assets) im Tag-Auswahl-Fenster in auf- oder absteigender Reihenfolge, basierend auf dem Tag-Namen, dem Erstellungsdatum oder dem Änderungsdatum.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **Kommunikation - Unterstützung von Document Manipulation APIs im as a Cloud Service SDK von Forms**: [Dokumentverarbeitungs-APIs](/help/forms/aem-forms-cloud-service-communications.md) hilft beim Kombinieren, Neuanordnen und Validieren von PDF-Dokumenten. Sie können jetzt mithilfe des as a Cloud Service SDK von AEM Forms Kommunikations - Document Generation APIs in einer lokalen Entwicklungsumgebung verwenden.

* **Verwenden benutzerdefinierter XCI zum Generieren eines Datensatzdokuments**: Sie können jetzt [Verwenden einer benutzerdefinierten XCI-Datei, um verschiedene Eigenschaften eines Datensatzdokuments festzulegen](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). Sie überschreibt das Übergeordnete XCI mit den benutzerdefinierten Änderungen. Es bietet mehr Kontrolle über die Generierung von Datensatzdokumenten, mehr Personalisierung und Anpassungsmöglichkeiten.

* **Unsichtbares CAPTCHA in einem adaptiven Formular verwenden**: Sie können die [unsichtbares CAPTCHA, um die CAPTCHA-Herausforderung nur im Falle einer verdächtigen Aktivität anzuzeigen](/help/forms/captcha-adaptive-forms.md). Wenn keine verdächtige Aktivität gefunden wird, wird die CAPTCHA-Herausforderung nicht angezeigt. Sie hilft bei der Bewertung der Fertigstellung menschlicher Formulare ohne Checkbox-Anforderungen, reduziert Anpassungsbemühungen und verbessert das Benutzererlebnis für Endbenutzer.

* **Formulardatenmodellkonfigurationen**: Sie können jetzt [Formulardatenmodellkonfigurationen in Umgebungen wiederverwenden](/help/forms/create-form-data-models.md#runmode-specific-context-aware-config), die Datenintegration zu vereinfachen und IT-Kosten zu senken.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### SDK Build Analyzer {#sdk-build-analyzers}

Das Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK erkennt Probleme in einem Maven-Projekt, einschließlich fehlender Abhängigkeiten. Es gibt Entwicklern die Möglichkeit, Probleme während der lokalen Entwicklung zu entdecken, lange bevor sie mit Cloud Manager in Cloud-Umgebungen bereitgestellt werden.

Vor kurzem wurde ein neuer Analyzer hinzugefügt:

* `content-packages-validation` - validiert für eine gut formulierte Inhaltssyntax und -struktur für Pakete, die während der Bereitstellung installiert werden

Es wird dringend empfohlen, Ihr Maven-Projekt mit der neuesten Version des Analyzers zu aktualisieren oder den Analyzer einzuschließen, falls Sie dies noch nicht getan haben. Weitere Informationen finden Sie in der Dokumentation [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de).

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation-Sicherheit {#foundation-security}

### TLS 1.0, 1.1 veraltet

Ab dem 30. Juni 2022 erfordert Experience Manager as a Cloud Service eine sicherere Netzwerkkommunikation und einen sichereren Datenaustausch mit den Benutzersystemen. AEM verwendet ausschließlich Transport Layer Security (TLS), 1.2-Protokoll. Ältere TLS-Versionen 1.0 und 1.1 werden nicht mehr unterstützt.

Wenn Sie weiterhin ältere Versionen von TLS als 1.0 und 1.1 verwenden, können Sie möglicherweise den Zugriff auf Experience Manager as a Cloud Service verlieren.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der monatlichen Cloud Manager-Versionen finden Sie [here](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Migrationstools {#migration-tools}

Eine vollständige Liste der Versionen der Migrationswerkzeuge finden Sie [here](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
