---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 6e834244f3de7e615df12b137f2ae90a11e64ad0
workflow-type: tm+mt
source-wordcount: '951'
ht-degree: 26%

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

Das Veröffentlichungsdatum [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version der Funktion (2023.10.0) ist der 26. Oktober 2023. Die nächste Version der Funktion (2023.11.0) ist für den 30. November 2023 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video „Versionsübersicht Oktober 2023“ an, das eine Zusammenfassung der Funktionen bietet, die mit der Version 2023.10.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3425186/?quality=12)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen {#assets-features}

**AEM Assets-Add-on für Adobe Expreß**: Experience Manager Assets bietet jetzt eine [Add-on für Adobe Expreß](/help/assets/addon-adobe-express.md). Mit dem Add-on können Sie über die Adobe Expreß-Benutzeroberfläche direkt auf die in Experience Manager Assets gespeicherten Assets zugreifen. Sie können in AEM Assets verwaltete Inhalte auf der Express-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern. Das Add-on bietet die folgenden Hauptvorteile:

* Verbesserte Wiederverwendung von Inhalten durch Bearbeiten und Speichern neuer Assets in AEM

* Verringerter Zeit- und Arbeitsaufwand beim Erstellen neuer Assets oder Erstellen neuer Versionen vorhandener Assets

  ![Einschließen von Assets aus dem Assets-Add-on](/help/assets/assets/aem-assets-add-on-include-assets.png)

### Neue Funktionen in der Assets-Ansicht {#assets-view-features}

* **Massenimport von Assets aus der OneDrive-Datenquelle**: Administratoren haben jetzt die Möglichkeit, [Import einer großen Anzahl von Assets von OneDrive in AEM Assets](/help/assets/bulk-import-assets-view.md#onedrive-developer-application). Die aktualisierte Liste der unterstützten Datenquellen für den Massenimport umfasst Azure, AWS, Google Cloud, Dropbox und OneDrive.

  ![Zuweisen eines Metadatenformulars zu einem Ordner](/help/assets/assets/bulk-import-source-details-onedrive.png)

* **Unterstützung von Cross-Org-Berechtigungen für Bibliotheken**: Mit Experience Manager Assets können Sie jetzt den Zugriff auf Creative Cloud-Bibliotheken in einer anderen IMS-Organisation konfigurieren. Dies ermöglicht einen einfacheren Zugriff auf die neuesten produktübergreifenden Workflows zwischen Creative Cloud und Experience Manager und reduziert Zeit und Aufwand für kreative Inhalte.

### Funktionen zur Vorabversion sind verfügbar in [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media**: [Unterstützung für mehrere Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma)—Sie können jetzt einfach mehrere Untertitel und mehrere Audiospuren zu einem Hauptvideo hinzufügen. Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

  ![Registerkarte &quot;Untertitel und Audiospuren&quot;auf der Seite &quot;Eigenschaften&quot;eines ausgewählten Video-Assets.](/help/release-notes/assets/msma-aem-cs.png)*Registerkarte &quot;Untertitel und Audiospuren&quot;auf der Seite &quot;Eigenschaften&quot;eines ausgewählten Video-Assets.*

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Experience Manager Forms] {#forms-features}

* **Benutzerdefinierte Eigenschaften für adaptive Forms**: Sie können benutzerdefinierte Attribute (Schlüssel-Wert-Paare) mit einer Formularvorlage oder adaptiven Formularkomponente verknüpfen, damit Formularentwickler dynamisches Formularverhalten bereitstellen können, das sich basierend auf den Werten dieser benutzerdefinierten Attribute anpasst. Beispielsweise können Entwickler basierend auf den Werten benutzerdefinierter Attribute verschiedene Ausgabeformate einer Headless-Forms-Komponente auf mobilen, Desktop- oder Webplattformen erstellen und so das Benutzererlebnis auf einer Vielzahl von Geräten erheblich verbessern.

* **Designs und Vorlagen**: Starten Sie Ihren Formularerstellungsprozess mit unseren neuen Designs und Vorlagen, die auf erfahrene Profis und neue Formularautoren zugeschnitten sind. Nahtlos mit den Kernkomponenten von Adaptive Forms erstellt, ermöglichen Ihnen diese sorgfältig kuratierten Designs und Vorlagen die rasche Erstellung von Formularen für gängige Anwendungsfälle.

  ![Vordefinierte Vorlagen](/help/forms/assets/form-templates-ootb.png)

### Funktionen zur Vorabversion sind verfügbar in [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* **Übermitteln von Forms an die Microsoft SharePoint-Liste**: AEM Forms bietet eine OOTB-Integration, um Formulardaten direkt an die SharePoint-Liste zu senden, sodass Sie die Funktionen der SharePoint-Listen nutzen können.

  >[!VIDEO](https://video.tv.adobe.com/v/3424820/connect-aem-adaptive-form-to-sharepointlist/?quality=12&learn=on)

### Programm für frühe Anwender {#forms-early-adopter}

* **[Protect Ihrer Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzer Zugriff erhalten. Diese befestigte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Augen, sondern bietet auch Seelenfrieden. Mit den Signature-APIs kann Ihr Unternehmen die Sicherheit und den Datenschutz von Adobe PDF-Dokumenten schützen, die es verteilt und empfängt. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfänger, für die dies vorgesehen ist, die Dokumente ändern können.

  Sie können schreiben an `aem-forms-early-adopter-program@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Traffic-Filterregeln, einschließlich WAF {#traffic-filter-rules-waf}

[Filtern des Traffics auf dem von Adobe verwalteten CDN](/help/security/traffic-filter-rules-including-waf.md) durch Deklarierung von Regeln, die dem Website-Traffic nach Eigenschaften wie URL, IP-Adresse und Benutzeragent entsprechen, oder Festlegung benutzerdefinierter Traffic-Ratenbeschränkungen, um DoS-Angriffe zu verhindern. Kunden können auch eine Reihe erweiterter WAF-Regeln (Web Application Firewall) für zusätzlichen Schutz vor komplexen Website-Bedrohungen lizenzieren.

Wir empfehlen Ihnen, sich mit Traffic-Filterregeln vertraut zu machen, indem Sie [Tutorial ausprobieren](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/security/traffic-filter-and-waf-rules/overview.html)! Er führt Sie durch die Einrichtung einer neuen Cloud Manager-Konfigurationspipelines, das Deklarieren von Regeln in einer Konfigurationsdatei und das Analysieren von CDN-Protokollen auf schädlichen Traffic.

Traffic-Filterregeln sind jetzt in Entwicklungsumgebungen verfügbar, mit einem schrittweisen Rollout zu Staging- und Produktionsumgebungen im November. Sie können einen früheren Zugriff auf Staging und Produktion per E-Mail anfordern **aemcs-waf-adopter@adobe.com**.

Die erweiterten WAF-Traffic-Filterregeln können noch in diesem Jahr über die Enhanced Security- oder WAF-DDoS-Schutzangebote lizenziert werden.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
