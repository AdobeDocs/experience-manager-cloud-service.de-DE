---
title: Versionshinweise für Version 2023.11.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.11.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 19cff082-80aa-445c-9462-5e319b7fe0e9
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1286'
ht-degree: 56%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.11.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.11.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.11.0) ist der Freitag, 30. November 2023. Die nächste Version (2023.12.0) ist für den Freitag, 14. Dezember 2023 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht November 2023 an, das eine Zusammenfassung der Funktionen bietet, die der Version 2023.11.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Early-Adopter-Programm {#sites-early-adopter}

**[Zeichenfolgen in Inhaltsfragmenten suchen und ersetzen](/help/sites-cloud/administering/content-fragments/managing.md#find-and-replace-find-and-replace)**: Die Inhaltsfragmentkonsole bietet Benutzenden eine einfache und intuitive Möglichkeit, eine Zeichenfolge in mehreren Inhaltsfragmenten gleichzeitig zu ersetzen, um die Geschwindigkeit der Inhaltsbearbeitung zu erhöhen.

![Suchen und Ersetzen](/help/sites-cloud/administering/content-fragments/assets/cf-managing-find-replace.png)

Möchten Sie die Funktion ausprobieren und Feedback geben? Senden Sie von Ihrer offiziellen E-Mail-ID aus eine E-**an** aemcs-headless-adopter@adobe.com, um mehr über das Early-Adopter-Programm zu erfahren.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#assets-view-features}

* **Eingebetteter Adobe Expreß-Editor in AEM Assets**: Benutzende mit Zugriff auf Express verfügen jetzt über integrierte Bildbearbeitungs- und Erstellungs-Tools von Adobe Expreß und Adobe Firefly, die direkt in AEM Assets verfügbar sind, um die Wiederverwendung von Inhalten zu verbessern und die Geschwindigkeit der Inhaltserstellung zu beschleunigen.

  ![Zuweisen eines Metadatenformulars zu einem Ordner](/help/assets/assets/adobe-express-aem-assets.png)

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)

-->


* **Berichte zur Speichernutzung in Insights**: Administratoren haben jetzt die Möglichkeit, die Berichte zur Speichernutzung als Teil von Insights anzuzeigen.

  ![Erkenntnisse zur Speichernutzung](/help/assets/assets/storage-usage-insights.png)

* **Konfiguration der ersten Homepage durchsuchen**: Mit Experience Manager Assets können Sie jetzt das Homepage-Erlebnis für Ihr Unternehmen konfigurieren. Wenn Sie die Startseite als erste Suche festlegen, können Sie die Ausrichtung des Suchbalkens, das Hintergrundbild und das Logo Ihres Unternehmens konfigurieren.

  ![Erste Konfiguration durchsuchen](/help/assets/assets/search-first-configuration.png)

### Neue Funktionen in der Vorabversion für die Administratoransicht {#admin-view-features-prerelease}

**Videovorschau**: AEM Assets generiert jetzt standardmäßig Vorschauausgabedarstellungen aller unterstützten Videoformate, ohne dass ein Verarbeitungsprofil konfiguriert werden muss.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Experience Manager Forms] {#forms-features}

* **[Kontrollkästchen-Komponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html?lang=de)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt eine Kontrollkästchen-Komponente enthalten. Sie ermöglicht Benutzenden, binäre Entscheidungen zu treffen, indem sie eine bestimmte Option auswählen oder eine Auswahl aufheben. Sie wird normalerweise als kleines Feld angezeigt, auf das geklickt oder getippt werden kann, um zwischen zwei Status zu wechseln: „aktiviert“ und „deaktiviert“. Das Kontrollkästchen ist ein gängiges Formularelement, das verwendet wird, um eine Ja/Nein- oder „true/false“-Auswahl zu treffen.

* **[Komponente „Geschäftsbedingungen“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html?lang=de)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt eine Komponente für Geschäftsbedingungen enthalten. Sie ermöglicht es Formularautorinnen und -autoren, einen bestimmten Abschnitt innerhalb des Formulars einzuführen, in dem den Benutzenden die Nutzungsbedingungen im Zusammenhang mit der Verwendung eines Dienstes, Produkts oder einer Plattform präsentiert werden. Diese Komponente hat das Ziel, Benutzende über die Regeln, Vorschriften und Verpflichtungen zu informieren, denen sie zustimmen, wenn sie das Formular übermitteln.

  ![Kontrollkästchen, Nutzungsbedingungen und vertikale Registerkartenkomponenten](/help/forms/assets/forms-components.png)

* **[Komponente „Vertikale Registerkarten“](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html?lang=de)**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt Formularinhalte in einer vertikalen Liste von Registerkarten organisieren und so ein strukturiertes und navigierbares Layout bieten. Die Verwendung von vertikalen Registerkarten in einem Formular kann das gesamte Benutzererlebnis verbessern, indem die Navigation vereinfacht und die Organisation des Formularinhalts verbessert wird, insbesondere in Situationen, in denen ein Formular mehrere Abschnitte oder komplexe Informationen enthält.



### Neue Funktionen in [!DNL Forms] Vorabversion {#prerelease-features-forms}

* **[Verbinden eines adaptiven Forms mit der Microsoft® SharePoint-Liste](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)**: AEM Forms bietet eine vorkonfigurierte Integration zum direkten Senden von Formulardaten an die SharePoint-Liste, sodass Sie die Funktionen von SharePoint-Listen nutzen können. Sie können die Microsoft SharePoint-Liste als Datenquelle für ein Formulardatenmodell konfigurieren und die Übermittlungsaktion **Senden mit Formulardatenmodell** verwenden, um ein adaptives Formular mit der SharePoint-Liste zu verbinden.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Early-Adopter-Programm {#forms-early-adopter}

* **Senden eines adaptiven Formulars an das Adobe Workfront Fusion-Szenario**: Forms as a Cloud Service bietet vordefinierte Optionen, um ein adaptives Formular einfach mit Adobe Workfront zu verbinden. Dadurch wird der Prozess zum Senden eines adaptiven Formulars an ein Adobe Workfront-Szenario vereinfacht, indem Sie bei der Übermittlung eines adaptiven Formulars ein Workfront Fusion-Szenario auslösen können.

* **Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung**: Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt in einer RTL-Sprache (Right-to-Left) wie Arabisch, Persisch und Urdu angezeigt werden. RTL-Sprachen werden von über 2 Milliarden Menschen weltweit gesprochen. Durch die Verwendung eines Formulars in RTL-Sprache können Sie die Reichweite Ihrer adaptiven Formulare erweitern, um diese verschiedenen Zielgruppen anzusprechen und RTL-Märkte zu erschließen. In bestimmten Regionen ist es außerdem gesetzlich vorgeschrieben, Formulare in der jeweiligen Regionalsprache bereitzustellen. Durch die Anpassung an lokale Sprachen öffnen Sie nicht nur den Zugang zu einem breiteren Publikum, sondern sorgen auch für die Einhaltung der einschlägigen Gesetze und Vorschriften.

  ![Unterstützung von Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/assets/right-to-left-language-support.png)

* **[Schützen Sie Ihre Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sondern sorgt auch für Seelenfrieden. Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies auch vorgesehen ist, die Dokumente ändern können.

  Sie können von Ihrer offiziellen E-Mail-ID aus an `aem-forms-ea@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### WAF-Traffic-Filterregeln können jetzt lizenziert werden {#cdn-waf-license}

Traffic-Filterregeln wurden im Oktober veröffentlicht und enthielten den Hinweis, dass die speziellen Regeln der Web Application Firewall (WAF) noch in diesem Jahr verfügbar sein würden, um die Regeln zu ergänzen, die bereits für Sites- und Forms-Kunden verfügbar sind. Als Update kann das WAF-DDoS-Schutzangebot jetzt lizenziert werden.

Nach der Lizenzierung können diese erweiterten WAF-Regeln mithilfe der Cloud Manager-Konfigurations-Pipeline im CDN bereitgestellt werden, um eine zusätzliche Ebene zum Schutz vor Web-Angriffen hinzuzufügen.

Erfahren Sie mehr [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md) einschließlich WAF. Wenden Sie sich an Ihr AEM-Account-Team, um Informationen zur Lizenzierung von WAF-DDoS Protection bzw. Enhanced Security zu erhalten.

### Early-Adopter-Programm für die CDN-Konfiguration {#cdn-config-early-adopter}

Zusätzlich zu den kürzlich veröffentlichten [Traffic-Filterregeln (einschließlich WAF)](/help/security/traffic-filter-rules-including-waf.md) gibt es eine Möglichkeit, die Konfigurations-Pipeline zu verwenden, um andere Arten von CDN-Konfigurationen zu deklarieren und bereitzustellen. Wir würden uns über Ihre Anwendungsfälle freuen, einschließlich:
* 301/302 Client-seitige Umleitungen
* Weiterleitungs-Anfragen am Edge zu beliebigen Ursprüngen
* URL-Transformationen
* Festlegen oder Ändern von Anfragen- oder Antwortkopfzeilen
* benutzerdefinierte Fehlerseiten, wenn das CDN AEM nicht erreichen kann
* Authentifizierung mit Benutzername/Kennwort
* alle anderen nützlichen CDN-Konfigurationen

Senden Sie von Ihrer offiziellen E-Mail-ID mit **Feedback eine E-Mail an** aemcs-cdn-config-adopter@adobe.com.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Bekannte Probleme {#known-issues}

* Adaptive Forms kann nicht basierend auf Kernkomponenten gesendet werden. Das Problem tritt bei adaptiven Forms auf, die mit den Kernkomponenten der Versionen 2.0.38 bis 2.0.60 erstellt wurden.

  Um das Problem zu beheben. Sie können zu Kernkomponenten für adaptive Formulare Version 2.0.62 oder höher wechseln. Um eine Version der Kernkomponenten von Adaptive Forms für Ihre Umgebung festzulegen, [legen Sie Versionen der Kernkomponenten „core.forms.components.version“, &quot;core.forms.components.af.version“ und „core.wcm.components.version“ ](/help/forms/enable-adaptive-forms-core-components.md#2-add-adaptive-forms-core-components-dependencies-to-your-git-repository) Abhängigkeiten in Ihrem auf dem Forms as a Cloud Service-Repository oder AEM-Archetyp basierenden Projekt fest und [stellen Sie die Änderungen in Ihrer Forms as a Cloud Service-Umgebung bereit](/help/forms/enable-adaptive-forms-core-components.md#build-and-deploy-updated-code-on-an-aem-forms-as-a-cloud-service-environment). Die neueste Version der Abhängigkeiten von adaptiven Forms-Kernkomponenten finden Sie im [Git-Repository für adaptive Forms-Kernkomponenten](https://github.com/adobe/aem-core-forms-components#system-requirements).
