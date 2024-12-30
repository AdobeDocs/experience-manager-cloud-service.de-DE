---
title: Versionshinweise für Version 2023.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 81a6cbd2-7101-429b-8572-2650c5bea963
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '918'
ht-degree: 98%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.10.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.10.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.10.0) ist der 26. Oktober 2023. Die nächste Version (2023.11.0) ist für den 30. November 2023 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video „Versionsübersicht Oktober 2023“ an, das eine Zusammenfassung der Funktionen bietet, die mit der Version 2023.10.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3425186/?quality=12)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen {#assets-features}

**AEM Assets-Add-on für Adobe Express**: Experience Manager Assets bietet jetzt ein Add-on für Adobe Express. Mit dem Add-on können Sie über die Adobe Express-Benutzeroberfläche direkt auf die in Experience Manager Assets gespeicherten Assets zugreifen. Sie können in AEM Assets verwaltete Inhalte auf der Express-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern. Das Add-on bietet die folgenden Hauptvorteile:

* Verbesserte Wiederverwendung von Inhalten durch Bearbeiten und Speichern neuer Assets in AEM

* Verringerter Zeit- und Arbeitsaufwand beim Erstellen neuer Assets oder beim Erstellen neuer Versionen von vorhandenen Assets

  ![Einschließen von Assets aus dem Assets-Add-on](/help/assets/assets/aem-assets-add-on-include-assets.png)

### Neue Funktionen in der Assets-Ansicht {#assets-view-features}

* **Massenimport von Assets aus der OneDrive-Datenquelle**: Admins haben jetzt die Möglichkeit, [eine große Anzahl von Assets aus OneDrive in AEM Assets zu importieren](/help/assets/bulk-import-assets-view.md#onedrive-developer-application). Die aktualisierte Liste der unterstützten Datenquellen für den Massenimport umfasst Azure, AWS, Google Cloud, Dropbox und OneDrive.

  ![Zuweisen eines Metadatenformulars zu einem Ordner](/help/assets/assets/bulk-import-source-details-onedrive.png)

* **Unterstützung von organisationsübergreifenden Berechtigungen für Bibliotheken**: Mit Experience Manager Assets können Sie jetzt den Zugriff auf Creative Cloud-Bibliotheken in einer anderen IMS-Organisation konfigurieren. Dies ermöglicht einen einfacheren Zugriff auf die neuesten, produktübergreifenden Workflows zwischen Creative Cloud und Experience Manager und reduziert Zeit und Aufwand für kreative Inhalte.

### Vorab veröffentlichte Funktionen, die in [!DNL Experience Manager Assets] verfügbar sind {#prerelease-features-assets}

* **Dynamic Media**: [Unterstützung für mehrfache Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma) – Sie können jetzt ganz einfach mehrfache Untertitel und mehrere Audiospuren zu einem primären Video hinzufügen.  Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

  ![Registerkarte „Untertitel und Audiospuren“ auf der Seite „Eigenschaften“ eines ausgewählten Video-Assets.](/help/release-notes/assets/msma-aem-cs.png)*Registerkarte „Untertitel und Audiospuren“ auf der Seite „Eigenschaften“ eines ausgewählten Video-Assets.*

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Experience Manager Forms] {#forms-features}

* **[Benutzerdefinierte Eigenschaften für adaptive Formulare](/help/forms/template-editor-core-components.md#add-a-custom-group-name-in-the-policy-of-template-editor)**: Sie können benutzerdefinierte Attribute (Schlüssel-Wert-Paare) mit einer Formularvorlage oder einer Komponente für ein adaptives Formular verknüpfen, damit Formularentwicklerinnen und -entwickler dynamisches Formularverhalten bereitstellen können, das sich basierend auf den Werten dieser benutzerdefinierten Attribute anpasst. Beispielsweise können Entwicklerinnen und Entwickler basierend auf den Werten benutzerdefinierter Attribute verschiedene Ausgabeformate einer Headless-Forms-Komponente auf mobilen, Desktop- oder Web-Plattformen erstellen und so das Benutzererlebnis auf einer Vielzahl von Geräten erheblich verbessern.

* **Designs und Vorlagen**: Starten Sie Ihren Formularerstellungsprozess mit unseren neuen Designs und Vorlagen, die sowohl auf erfahrene Profis als auch auf neue Formularautorinnen und -autoren zugeschnitten sind. Diese sorgfältig kuratierten Designs und Vorlagen wurden mit den Kernkomponenten von adaptiven Formularen nahtlos erstellt und ermöglichen Ihnen die rasche Erstellung von Formularen für gängige Anwendungsfälle.

  ![Vordefinierte Vorlagen](/help/forms/assets/form-templates-ootb.png)


### Early-Adopter-Programm {#forms-early-adopter}

* **[Schützen Sie Ihre Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sondern sorgt auch für Seelenfrieden. Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies auch vorgesehen ist, die Dokumente ändern können.

  Sie können von Ihrer offiziellen E-Mail-ID aus an `aem-forms-ea@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Traffic-Filterregeln, einschließlich WAF {#traffic-filter-rules-waf}

[Filtern Sie Traffic auf dem von Adobe verwalteten CDN](/help/security/traffic-filter-rules-including-waf.md) durch das Deklarieren von Regeln, die dem Website-Traffic nach Eigenschaften wie URL, IP-Adresse und Benutzeragent entsprechen, oder durch das Festlegen benutzerdefinierter Traffic-Ratenbeschränkungen, um DoS-Angriffe zu verhindern. Kundinnen und Kunden können auch eine Reihe erweiterter WAF-Regeln (Web Application Firewall) für zusätzlichen Schutz vor komplexen Website-Bedrohungen lizenzieren.

Wir empfehlen Ihnen, sich mit Traffic-Filterregeln vertraut zu machen, indem Sie [ein Tutorial ausprobieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html?lang=de)! Es führt Sie durch die Einrichtung einer neuen Cloud Manager-Konfigurations-Pipeline, das Deklarieren von Regeln in einer Konfigurationsdatei und das Analysieren von CDN-Protokollen auf schädlichen Traffic.

Traffic-Filterregeln sind jetzt in Entwicklungsumgebungen verfügbar. Die Einführung für Staging- und Produktionsumgebungen findet schrittweise im November statt. Sie können einen früheren Zugriff auf Staging und Produktion per E-Mail anfordern, indem Sie eine E-Mail an **aemcs-waf-adopter@adobe.com** senden.

Die erweiterten WAF-Traffic-Filterregeln können noch in diesem Jahr über die Enhanced Security- oder WAF-DDoS-Schutzangebote lizenziert werden.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
