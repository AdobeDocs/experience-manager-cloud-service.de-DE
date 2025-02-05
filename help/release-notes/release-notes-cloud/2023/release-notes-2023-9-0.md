---
title: Versionshinweise für Version 2023.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: d747f58b-8d6c-418d-9d2b-ec3ae4b6dc03
feature: Release Information
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 84%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.9.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.9.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.9.0) ist der Freitag, 28. September 2023. Die nächste Version mit neuen Funktionen (2023.10.0) ist für den Freitag, 26. Oktober 2023 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2023.9.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version von September 2023:

>[!VIDEO](https://video.tv.adobe.com/v/3424826/?quality=12)

## AEM-Edge Delivery Services {#edge-delivery}

Edge Delivery ist ein neues Paket zusammenstellbarer Services, die darauf ausgerichtet sind, die Wirkung von Inhalten zu maximieren, um messbare Geschäftsergebnisse am Punkt der Kundeninteraktion zu erzielen.

Weitere Informationen zu Edge Delivery Services finden Sie im Artikel [hier](/help/edge/overview.md).

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#assets-view-features}

**Metadatenformular einem Ordner zuweisen**

Sie können jetzt einem bestimmten Ordner in Ihrer -Bereitstellung Metadatenformulare zuweisen. Alle Assets im Ordner, einschließlich Assets in den Unterordnern, zeigen dann die im zugewiesenen Metadatenformular definierten Eigenschaften an.

![Metadatenformular einem Ordner zuweisen](/help/release-notes/assets/assign-to-folder.png)

### Neue Funktionen in der Admin-Ansicht {#admin-view-features}

* **Integrieren von AEM Assets as a Cloud Service mit der dokumentbasierten Inhaltserstellung für Edge Delivery Services**: Integrieren Sie AEM Assets mit der dokumentbasierten Inhaltserstellung für Edge Delivery Services, damit Website-Autoren ([ in AEM Assets-Repositorys verfügbare Bilder beim Erstellen von Dokumenten in Microsoft Word oder Google Docs) ](/help/edge/using.md#integrate-assets-edge) können.

* **ZIP-Archive extrahieren**: Möglichkeit, ZIP-Archive auszuwählen, die im Experience Manager verwaltet werden, und [die Dateien direkt in den Experience Manager zu ](/help/assets/manage-digital-assets.md#extract-zip-archives), ohne sie herunterzuladen.

  ![Anheften von Elementen für Gruppen](/help/release-notes/assets/extract-archive.png)

### Vorab veröffentlichte Funktionen, die in [!DNL Experience Manager Assets] verfügbar sind {#prerelease-features-assets}

* **Dynamic Media**: [Unterstützung für mehrfache Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma) – Sie können jetzt ganz einfach mehrfache Untertitel und mehrere Audiospuren zu einem primären Video hinzufügen.  Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

  ![Registerkarte „Untertitel und Audiospuren“ auf der Seite „Eigenschaften“ eines ausgewählten Video-Assets.](/help/release-notes/assets/msma-aem-cs.png)*Registerkarte „Untertitel und Audiospuren“ auf der Seite „Eigenschaften“ eines ausgewählten Video-Assets.*

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Experience Manager Forms] {#forms-features}

* [**Unterstützung für Google reCAPTCHA Enterprise**](/help/forms/captcha-adaptive-forms-core-components.md): Verwenden Sie Google reCAPTCHA Enterprise in einem adaptiven Formular, um einen besseren Schutz vor betrügerischen Aktivitäten und Spam zu bieten und so ein sichereres Anwendererlebnis zu ermöglichen. Dank erweiterter Risikoanalyse und nahtloser Integration können echte Benutzende problemlos Formulare absenden, während Bots effektiv blockiert werden.

* [**Adobe Analytics mit Experience Cloud-Setup-Automatisierung für Formulare**](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md): Sie können nun Adobe Analytics dank Experience Cloud-Setup-Automatisierung mit wenigen Klicks aktivieren. So können Sie AEM Forms as a Cloud Service mit Experience Platform-Tags und Adobe Analytics verbinden, um Leistungsmetriken für Ihre veröffentlichten Formulare zu erfassen und nachzuverfolgen.

  >[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)

* [**Adobe Analytics-Berichtsvorlage für adaptive Formulare**](/help/forms/view-understand-aem-forms-analytics-reports.md): Forms as a Cloud Service bietet nun einen vorkonfigurierten Adobe Analytics-Bericht. Dies hilft Ihnen, die Leistung Ihrer Formulare einfach zu verstehen. Die Metriken auf Formularebene bieten Ihnen einen Einblick in die Leistung des Formulars in Bezug auf mehrere wichtige Leistungsindikatoren (KPIs) wie Ausgabedarstellungen, Besuchende, Übermittlungen, durchschnittliche Ausfüllzeit. Durch Nachverfolgung von Benutzerverhalten und -Feedback können Sie Formularbereiche identifizieren, die Verwirrung verursachen, und so Verbesserungen am Formular-Design und an der Formularfunktionalität erwirken.

  ![Adobe Analytics-Bericht zur Benutzerinteraktion im adaptiven Formular](/help/forms/assets/forms-analytics-report.png)

* **[Formularfragment in adaptiven Formularen auf Basis auf Kernkomponenten](/help/forms/adaptive-form-fragments-core-components.md)**: Keine Duplizierung mehr! Außerdem können Sie Ihre digitalen Bestände und die Zusammenarbeit optimieren, während Sie das Anwendererlebnis bei der Formularerstellung mit Formularfragmenten verbessern. Diese wiederverwendbaren Komponenten lassen sich nahtlos in mehrere Formulare integrieren, was die Erstellung konsistenter und professionell aussehender Formulare optimiert. Formularfragmente sorgen für Wiederverwendbarkeit, Standardisierung und Markenkonsistenz durch die Funktion „Einmal ändern und überall widerspiegeln“. Erleben Sie mehr Wartbarkeit und Effizienz, da Aktualisierungen an einem Ort automatisch über alle Formulare hinweg übernommen werden, die diese Fragmente verwenden.

* **[Verbesserter Workflow-Schritt in Adobe Sign](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: Der Workflow-Schritt in Adobe Sign enthält die folgenden Verbesserungen:
   * **Authentifizierung mit amtlichem Lichtbildausweis für Adobe Sign**: Die Authentifizierung mit amtlichem Lichtbildausweis von Adobe Acrobat Sign bietet eine zusätzliche Verifizierungsebene, indem Benutzenden ermöglicht wird, ihre Identität anhand von amtlichen Lichtbildausweisen (Führerschein, Personalausweis, Reisepass) zu authentifizieren. Durch die Nutzung von vertrauenswürdigen Identifikationsdokumenten verleiht diese Erweiterung dem Unterzeichnungsprozess ein zusätzliches Maß an Vertrauen und ist somit ideal für Szenarien, die erhöhte Sicherheit, Compliance und Benutzervalidierung erfordern.

   * **Audit-Protokoll für Adobe Sign-Dokumente**: Verwenden Sie die Audit-Protokoll-Funktion, um ausführliche Erkenntnisse zum Lebenszyklus Ihrer Adobe Sign-Dokumente zu erhalten. Mit dem Audit-Protokoll können Sie jetzt eine umfassende Aufzeichnung aller Aktionen und Interaktionen führen, die mit Ihren Dokumenten verbunden sind. Dazu gehören Details wie etwa die Personen, die das Dokument angesehen, bearbeitet oder unterschrieben haben, sowie Zeitstempel für jedes Ereignis. Diese Verbesserung ist entscheidend für die Einhaltung von Vorschriften, die Beilegung von Streitigkeiten und die Gewährleistung der Integrität Ihrer digitalen Vereinbarungen.

   * **Neue Rollen für Empfängerinnen und Empfänger von Vereinbarungen über die Unterzeichnerinnen bzw. Unterzeichner hinaus**: Adobe Acrobat Sign bietet die Möglichkeit, die Rollen für Empfängerinnen und Empfänger von Vereinbarungen über die Personen hinaus zu erweitern, die unterzeichnet haben, um Workflow-Anforderungen besser zu erfüllen. Wenn diese Option aktiviert ist, kann die Rolle jeder Empfängerin und jedes Empfängers in einem Vertrag einzeln konfiguriert werden, wobei die Person, die unterzeichnet hat, die Standardeinstellung ist.

* **Unterstützung der Seitenzahl in Kommunikations-APIs**: Sie können nun neben dem Abruf Ihres Dokuments über die Kommunikations-APIs auch wertvolle Informationen über die Anzahl der im Dokument enthaltenen Seiten beziehen.

* **[Fehlerhandhabung mit benutzerdefinierten Fehler-Handlern im Regeleditor](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: Sie können nun eine benutzerdefinierte Funktion aufrufen, wenn ein von einem externen Dienst zurückgegebener Fehler auftritt, und eine maßgeschneiderte Antwort für Endbenutzerinnen und -benutzer bereitstellen. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehler-Codes aufrufen oder die Kundin bzw. den Kunden darüber informieren, dass der Dienst nicht verfügbar ist.

* **[64-Bit-Version von AEM Forms Designer](/help/forms/installing-configuring-designer.md)**: Die 64-Bit-Version von AEM Forms Designer bietet verbesserte Leistung, Skalierbarkeit und Speicherverwaltung, um die Formularerstellung zu verbessern. Mit der 64-Bit-Architektur können Sie noch größere und komplexere Projekte einfach angehen, um nahtlose Design-Workflows und eine optimierte Effizienz zu gewährleisten. Verbessern Sie Ihre Formularentwurfsfähigkeiten und nutzen Sie die Zukunft von AEM Forms Designer mit dieser innovativen Version.

### Early-Adopter-Programm {#forms-early-adopter}

* **[Schützen Sie Ihre Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sondern sorgt auch für Seelenfrieden. Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies auch vorgesehen ist, die Dokumente ändern können.

  Sie können von Ihrer offiziellen E-Mail-ID aus an `aem-forms-ea@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

* **[Headless Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de)**: Verwenden Sie Headless Adaptive Forms, um Entwicklerinnen und Entwicklern die Erstellung, Veröffentlichung und Verwaltung interaktiver Formulare zu ermöglichen, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

   * Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
   * Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
   * Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
   * Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

  Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an `aem-forms-headless@adobe.com` senden, um am Early-Adopter-Programm teilzunehmen.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Neues CDN-Caching-Verhalten für kampagnenbezogene URL-Parameter {#cache-url-params}

In neuen Umgebungen entfernt das CDN standardmäßig Marketing-bezogene Abfrageparameter, um die Leistung der Marketing-Kampagne und die Cache-Trefferraten zu erhöhen. Bestehende Umgebungen sind davon nicht betroffen. [Weitere Informationen](/help/implementing/dispatcher/caching.md#marketing-parameters).

### Early-Adopter-Programm für Traffic-Filterregeln (einschließlich WAF-Regeln) {#waf-early-adopter}

Filtern Sie den Traffic im CDN anhand von:

* Anfragekopfzeilen und -eigenschaften (z. B. IP-Adresse)
* Traffic-Muster, die bekanntermaßen mit bösartigem Traffic verknüpft sind

Möchten Sie die Funktion ausprobieren und Feedback geben? Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an **aemcs-waf-adopter@adobe.com** senden, um am Early-Adopter-Programm teilzunehmen. Die Plätze sind begrenzt.

Weitere Informationen zur Funktion finden Sie im Artikel [hier](/help/security/traffic-filter-rules-including-waf.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
