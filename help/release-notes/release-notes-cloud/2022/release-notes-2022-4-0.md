---
title: Versionshinweise für Version 2022.4.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2022.4.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 6c86838a-cabf-4770-b1ae-618af70193a2
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '580'
ht-degree: 85%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2022.4.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den Funktionen der Version 2022.4.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2022.4.0) war der 5. Mai 2022.
Die nächste Version (2022.5.0) ist für den 9. Juni 2022 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht April 2022](https://video.tv.adobe.com/v/342612?quality=12) an, das eine Zusammenfassung der Funktionen bietet, die der Version 2022.4.0 hinzugefügt wurden.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#sites-features}

* Die Datentypen des Inhaltsmodells können jetzt mit einem einfachen Kontrollkästchen im Inhaltsmodell-Editor als [übersetzbar](/help/assets/content-fragments/content-fragments-models.md#properties) definiert werden. Außerdem werden AEM-Übersetzungsregeln und -konfigurationen automatisch aktualisiert.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Sie können jetzt Tags im Tag-Auswahlfenster in auf- oder absteigender Reihenfolge basierend auf dem Tag-Namen, dem Erstellungsdatum oder dem Änderungsdatum [sortieren](/help/assets/organize-assets.md#use-tags-to-organize-assets).


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **Kommunikation – Unterstützung von APIs zur Dokumentbearbeitung im Forms as a Cloud Service SDK**: [APIs zur Dokumentbearbeitung](/help/forms/aem-forms-cloud-service-communications.md) helfen beim Kombinieren, Neuanordnen und Validieren von PDF-Dokumenten. Sie können jetzt mithilfe des AEM Forms as a Cloud Service SDK Kommunikations-APIs für die Dokumentengenerierung in einer lokalen Entwicklungsumgebung verwenden.

* **Verwenden einer benutzerdefinierten XCI-Datei zum Generieren eines Datensatzdokuments**: Sie können jetzt [eine benutzerdefinierten XCI-Datei verwenden, um verschiedene Eigenschaften eines Datensatzdokuments festzulegen](/help/forms/generate-document-of-record-for-non-xfa-based-adaptive-forms.md#use-a-custom-xci-file). Sie überschreibt die primäre XCI-Datei mit den benutzerdefinierten Änderungen. Sie bietet mehr Kontrolle über die Generierung von Datensatzdokumenten, mehr Personalisierung und Anpassungsmöglichkeiten.

* **Verwenden eines unsichtbaren Captcha in einem adaptiven Formular**: Sie können das [unsichtbare Captcha verwenden, um den Captcha-Test nur bei einer verdächtigen Aktivität anzuzeigen](/help/forms/captcha-adaptive-forms.md). Wenn keine verdächtige Aktivität gefunden wird, wird die Captcha-Aufforderung nicht angezeigt. Sie hilft bei der Bewertung des Ausfüllens von Formularen durch Menschen ohne Kontrollkästchenanforderungen, reduziert den Anpassungsaufwand und verbessert das Erlebnis für Endbenutzerinnen und -benutzer.

* **Konfigurationen von Formulardatenmodellen**: Sie können jetzt [Konfigurationen von Formulardatenmodellen in Umgebungen wiederverwenden](/help/forms/create-form-data-models.md#runmode-specific-context-aware-config), um die Datenintegration zu vereinfachen und IT-Kosten zu senken.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### SDK Build Analyzer {#sdk-build-analyzers}

Das Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK erkennt Probleme in einem Maven-Projekt, einschließlich fehlender Abhängigkeiten. Es gibt Entwicklern die Möglichkeit, Probleme während der lokalen Entwicklung zu entdecken, lange bevor sie mit Cloud Manager in Cloud-Umgebungen bereitgestellt werden.

Vor Kurzem wurde ein neuer Analyzer hinzugefügt:

* `content-packages-validation`: Validiert eine gut formulierte Inhaltssyntax und -struktur für Pakete, die während der Bereitstellung installiert werden.

Es wird dringend empfohlen, Ihr Maven-Projekt mit der neuesten Version des Analyzers zu aktualisieren oder den Analyzer einzubinden, falls Sie dies noch nicht getan haben. Weitere Informationen finden Sie in der Dokumentation [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de).

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation – Sicherheit {#foundation-security}

### TLS 1.0, 1.1 veraltet

Ab dem 30. Juni 2022 erfordert Experience Manager as a Cloud Service eine sicherere Netzwerkkommunikation und einen sichereren Datenaustausch mit Benutzersystemen. AEM beabsichtigt, ausschließlich das Protokoll Transport Layer Security (TLS) 1.2 zu verwenden. Ältere TLS-Versionen 1.0 und 1.1 werden jetzt nicht mehr unterstützt.

Wenn Sie weiterhin ältere Versionen von TLS als 1.0 und 1.1 verwenden, können Sie möglicherweise nicht mehr auf Experience Manager as a Cloud Service zugreifen.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
