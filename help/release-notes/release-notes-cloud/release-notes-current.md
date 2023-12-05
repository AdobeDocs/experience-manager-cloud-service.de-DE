---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 16%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.11.0) war der Freitag, 30. November 2023. Die nächste Version (2023.12.0) ist für den Freitag, 14. Dezember 2023 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht von November 2023 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2023.11.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Programm für frühe Anwender {#sites-early-adopter}

**[Strings in Inhaltsfragmenten suchen und ersetzen](/help/sites-cloud/administering/content-fragments/managing.md#find-and-replace-find-and-replace)**: Die Inhaltsfragmentkonsole bietet Benutzern eine einfache und intuitive Möglichkeit, eine Zeichenfolge zu ersetzen, die in mehreren Inhaltsfragmenten gleichzeitig angezeigt wird, um die Content Velocity zu beschleunigen.

![Suchen und Ersetzen](/help/sites-cloud/administering/content-fragments/assets/cf-managing-find-replace.png)

Möchten Sie die Funktion ausprobieren und Feedback teilen? E-Mail an senden **aemcs-headless-adopter@adobe.com** von Ihrer offiziellen E-Mail-ID, um mehr über das Programm für frühe Anwender zu erfahren.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#assets-view-features}

* **Eingebetteter Adobe Expreß-Editor in AEM Assets**: Benutzer mit Zugriff auf Express verfügen jetzt über integrierte Bildbearbeitungs- und -erstellungs-Tools von Adobe Expreß und Adobe Firefly direkt in AEM Assets, um die Wiederverwendung von Inhalten zu verbessern und die Geschwindigkeit der Inhaltswiedergabe zu beschleunigen.

  ![Zuweisen eines Metadatenformulars zu einem Ordner](/help/assets/assets/adobe-express-aem-assets.png)

<!--

* **Smart tags blocklist**: Experience Manager Assets now enables you to define a list of blocked tags. These tags are automatically removed from the auto-generated smart tags when you upload assets to the repository. This capability performs tags governance and saves a lot of time as you can add a tag to the block list and AEM Assets automatically excludes it from the list of tags for any of the assets that are added to the repository.

  ![storage usage insights](/help/assets/assets/block-tags.png)

-->


* **Verwendungsberichte in Insights**: Administratoren können jetzt die im Rahmen von Insights verfügbaren Speicherverwendungsberichte anzeigen.

  ![Einblicke zur Speicherverwendung](/help/assets/assets/storage-usage-insights.png)

* **Erste Homepage-Konfiguration durchsuchen**: Mit Experience Manager Assets können Sie jetzt das Starterlebnis für Ihre Organisation konfigurieren. Wenn Sie zuerst als Startseite die Suche auswählen, können Sie die Ausrichtung der Suchleiste, das Hintergrundbild und das Logo für Ihre Organisation konfigurieren.

  ![Erste Konfiguration durchsuchen](/help/assets/assets/search-first-configuration.png)

### Neue Funktionen in der Vorabversion für die Administratoransicht {#admin-view-features-prerelease}

**Videovorschau**: AEM Assets generiert jetzt standardmäßig Vorschaudarstellungen aller unterstützten Videoformate, ohne dass ein Verarbeitungsprofil konfiguriert werden muss.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Experience Manager Forms] {#forms-features}

* **[Kontrollkästchenkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html)**: Adaptive Forms, die auf Kernkomponenten basiert, kann jetzt eine Kontrollkästchenkomponente enthalten. Sie ermöglicht Benutzern, binäre Entscheidungen zu treffen, eine bestimmte Option auszuwählen oder zu deaktivieren. Es wird normalerweise als kleines Feld angezeigt, auf das geklickt oder getippt werden kann, um zwischen zwei Status zu wechseln: &quot;aktiviert&quot;und &quot;deaktiviert&quot;. Das Kontrollkästchen ist ein gängiges Formularelement, das verwendet wird, um eine Ja/Nein- oder true/false-Auswahl zu geben.

* **[Komponente &quot;Allgemeine Geschäftsbedingungen&quot;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html)**: Adaptive Forms, die auf Kernkomponenten basiert, kann jetzt eine Komponente für Geschäftsbedingungen enthalten. Sie ermöglicht es Formularautoren, einen bestimmten Abschnitt innerhalb des Formulars einzuführen, in dem den Benutzern die Bedingungen oder rechtlichen Vereinbarungen im Zusammenhang mit der Verwendung eines Dienstes, Produkts oder einer Plattform präsentiert werden. Diese Komponente soll Benutzer über die Regeln, Vorschriften und Verpflichtungen informieren, denen sie zustimmen, indem sie das Formular übermitteln.

  ![Registerkartenkomponenten &quot;Kontrollkästchen&quot;, &quot;Geschäftsbedingungen&quot;und &quot;Vertikal&quot;](/help/forms/assets/forms-components.png)

* **[Komponente mit vertikalen Registerkarten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html)**: Der auf Kernkomponenten basierende adaptive Forms kann jetzt Formularinhalte in einer vertikalen Liste von Registerkarten organisieren und so ein strukturiertes und navigierbares Layout bereitstellen. Die Verwendung von vertikalen Registerkarten in einem Formular kann das gesamte Benutzererlebnis verbessern, indem die Navigation vereinfacht und die Organisation des Formularinhalts verbessert wird, insbesondere in Situationen, in denen ein Formular mehrere Abschnitte oder komplexe Informationen enthält.



### Neue Funktionen in der Vorabversion von [!DNL Forms] {#prerelease-features-forms}

* **[Verbinden einer adaptiven Forms-Liste mit Microsoft® SharePoint-Liste](/help/forms/configure-submit-actions-core-components.md#submit-to-sharepoint)**: AEM Forms bietet eine OOTB-Integration zum Senden von Formulardaten direkt an die SharePoint-Liste, sodass Sie die SharePoint-Funktionen &quot;Listen&quot;verwenden können. Sie können die Microsoft SharePoint-Liste als Datenquelle für ein Formulardatenmodell konfigurieren und die **Senden mit Formulardatenmodell** Übermittlungsaktion zum Verbinden eines adaptiven Formulars mit einer SharePoint-Liste.

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Programm für frühe Anwender {#forms-early-adopter}

* **[Senden eines adaptiven Formulars an das Adobe Workfront Fusion-Szenario](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service bietet vordefinierte Optionen, um ein adaptives Formular einfach mit Adobe Workfront zu verbinden. Dadurch wird der Prozess zum Senden eines adaptiven Formulars an ein Adobe Workfront-Szenario vereinfacht, sodass Sie bei der Übermittlung eines adaptiven Formulars ein Workfront Fusion-Szenario Trigger haben.

* **[Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/supporting-new-language-localization-core-components.md)**: Adaptive Forms, die auf Kernkomponenten basiert, kann jetzt in einer RTL-Sprache (Right-to-Left) wie Arabisch, Persisch und Urdu angezeigt werden. Die RTL-Sprachen werden von über 2 Milliarden Menschen weltweit gesprochen. Durch die Verwendung eines Formulars in RTL-Sprache können Sie die Reichweite Ihrer adaptiven Formulare erweitern, um diese unterschiedlichen Zielgruppen zu bedienen und auf RTL-Märkten auszuwählen. In bestimmten Regionen ist es auch ein gesetzliches Mandat, Formulare in der Landessprache zu verfassen. Durch die Unterbringung der lokalen Sprachen öffnen Sie nicht nur den Zugang zu einem breiteren Publikum, sondern sorgen auch für die Einhaltung der einschlägigen Gesetze und Vorschriften.

  ![Unterstützung von Sprachen mit Rechts-Links](/help/forms/assets/right-to-left-language-support.png)

* **[Protect Ihrer Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzer Zugriff erhalten. Diese befestigte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Augen, sondern bietet auch Seelenfrieden. Signature-APIs ermöglichten Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Dienst verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur beabsichtigte Empfänger Dokumente ändern können.

  Sie können schreiben an `aem-forms-early-adopter-program@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### WAF-Traffic-Filterregeln können jetzt lizenziert werden {#cdn-waf-license}

Im Oktober wurden Traffic-Filter-Regeln veröffentlicht und es wurde ein Hinweis hinzugefügt, dass die spezielle Kategorie der Web Application Firewall (WAF)-Regeln später in diesem Jahr verfügbar sein würde, um die Regeln zu ergänzen, die bereits für Sites- und Forms-Kunden verfügbar sind. Als Update kann das WAF-DDoS-Schutzangebot jetzt lizenziert werden.

Nach der Lizenzierung können diese erweiterten WAF-Regeln mithilfe der Cloud Manager Configuration Pipeline in das CDN bereitgestellt werden, um eine zusätzliche Schutzschicht gegen Web-Angriffe hinzuzufügen.

Informationen [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), einschließlich WAF. Sprechen Sie mit Ihrem AEM-Account-Team über die Lizenzierung von WAF-DDoS-Schutz oder Enhanced Security.

### CDN Configuration Early Adopter Program {#cdn-config-early-adopter}

Zusätzlich zu den kürzlich veröffentlichten [Traffic-Filterregeln (einschließlich WAF)](/help/security/traffic-filter-rules-including-waf.md), gibt es eine Möglichkeit, die Configuration Pipeline zu verwenden, um andere Typen der CDN-Konfiguration zu deklarieren und bereitzustellen. Wir würden uns über Ihre Anwendungsfälle freuen, einschließlich:
* 301/302 Client-seitige Umleitungen
* Proxying-Anfragen am Edge zu beliebigen Ursprüngen
* URL-Transformationen
* Anforderungs- oder Antwortheader festlegen oder ändern
* benutzerdefinierte Fehlerseiten, wenn das CDN nicht AEM erreichen kann
* Authentifizierung durch Benutzername/Kennwort
* alle anderen nützlichen CDN-Konfigurationen

E-Mail an senden **aemcs-cdn-config-adopter@adobe.com** von Ihrer offiziellen E-Mail-ID mit Ihrem Feedback.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Bekannte Probleme {#known-issues}

* Adaptive Forms kann nicht basierend auf Kernkomponenten gesendet werden. Das Problem tritt bei Adaptive Forms auf, die mit den Kernkomponenten-Versionen 2.0.38 - 2.0.60 erstellt wurde.

  Um das Problem zu beheben. Sie können zu Kernkomponenten des adaptiven Formulars Version 2.0.62 oder höher wechseln. So legen Sie eine Version der adaptiven Forms-Kernkomponenten für Ihre Umgebung fest: [Versionen der Komponenten &quot;core.forms.components.version&quot;, &quot;core.forms.components.af.version&quot;und &quot;core.wcm.components.version&quot;festlegen](/help/forms/enable-adaptive-forms-core-components.md#2-add-adaptive-forms-core-components-dependencies-to-your-git-repository) Abhängigkeiten in Ihrem as a Cloud Service Forms-Repository oder AEM Archetyp-basierten Projekt und [die Änderungen in Ihrer as a Cloud Service Forms-Umgebung bereitstellen](/help/forms/enable-adaptive-forms-core-components.md#build-and-deploy-updated-code-on-an-aem-forms-as-a-cloud-service-environment). Die neueste Version der Abhängigkeiten von adaptiven Forms-Kernkomponenten finden Sie unter [Git-Repository für adaptive Forms-Kernkomponenten](https://github.com/adobe/aem-core-forms-components#system-requirements).
