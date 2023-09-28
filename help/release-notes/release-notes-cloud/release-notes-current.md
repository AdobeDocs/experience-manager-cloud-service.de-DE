---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 39284210e6639c4ed2a80cf86dbf0ea32d889986
workflow-type: tm+mt
source-wordcount: '1421'
ht-degree: 27%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version der Funktion (2023.9.0) ist der 28. September 2023. Die nächste Version der Funktion (2023.10.0) ist für den 26. Oktober 2023 geplant.

<!-- 

## Release Video {#release-video}

Have a look at the September 2023 Release Overview video for a summary of the features added in the 2023.9.0 release:

>[!VIDEO](put new link here)

-->

## Edge-Bereitstellungsdienste {#edge-delivery}

Edge Delivery ist ein neuer Satz zusammenstellbarer Services, die darauf ausgerichtet sind, die Wirkung von Inhalten zu maximieren, um messbare Geschäftsergebnisse zum Zeitpunkt der Kundeninteraktion zu erzielen.

Weitere Informationen zu Edge Delivery Services finden Sie im Artikel [here](/help/edge/overview.md).

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Asset-Ansicht {#assets-view-features}

**Zuweisen eines Metadatenformulars zu einem Ordner**

Sie können jetzt ein Metadatenformular einem bestimmten Ordner in Ihrer Assets Essentials-Bereitstellung zuweisen. Alle Assets im Ordner, einschließlich Assets in den Unterordnern, zeigen dann Eigenschaften an, die im zugewiesenen Metadatenformular definiert sind.

![Zuweisen eines Metadatenformulars zu einem Ordner](/help/release-notes/assets/assign-to-folder.png)

### Neue Funktionen in der Administratoransicht {#admin-view-features}

* **Integrieren von AEM Assets as a Cloud Service mit dokumentbasiertem Authoring für Edge Delivery Services**: Integrieren Sie AEM Assets in dokumentbasiertes Authoring für Edge Delivery Services, damit Website-Autoren [Bilder verwenden, die in AEM Assets-Repositorys beim Erstellen von Dokumenten in Microsoft Word- oder Google-Dokumenten verfügbar sind](/help/edge/using.md#integrate-assets-edge).

* **ZIP-Archive extrahieren**: Möglichkeit zur Auswahl von ZIP-Archiven, die in Experience Manager verwaltet werden, und [Extrahieren der Dateien direkt in Experience Manager](/help/assets/manage-digital-assets.md#extract-zip-archives) , ohne sie herunterzuladen.

  ![Elemente für Gruppen fixieren](/help/release-notes/assets/extract-archive.png)

### Funktionen zur Vorabversion sind verfügbar in [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media**: [Unterstützung für mehrere Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma)—Sie können jetzt einfach mehrere Untertitel und mehrere Audiospuren zu einem Hauptvideo hinzufügen. Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

  ![Registerkarte &quot;Untertitel und Audiospuren&quot;auf der Seite &quot;Eigenschaften&quot;eines ausgewählten Video-Assets.](/help/release-notes/assets/msma-aem-cs.png)*Registerkarte &quot;Untertitel und Audiospuren&quot;auf der Seite &quot;Eigenschaften&quot;eines ausgewählten Video-Assets.*

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Experience Manager Forms] {#forms-features}

* [**Enterprise-Unterstützung für Google reCAPTCHA**](/help/forms/captcha-adaptive-forms-core-components.md): Verwenden Sie Google reCAPTCHA Enterprise in einem adaptiven Formular, um einen verbesserten Schutz vor betrügerischer Aktivität und Spam zu bieten und so eine sicherere Benutzererfahrung zu bieten. Dank der erweiterten Risikoanalyse und nahtloser Integration können echte Benutzer problemlos Formulare senden, während Bots effektiv blockiert werden.

* [**Adobe Analytics mit Experience Cloud-Setup-Automatisierung für Forms**](/help/forms/enable-adobe-analytics-adaptive-form-using-experience-cloud-setup-automation.md): Sie können Adobe Analytics jetzt mit Experience Cloud Setup Automation mit mehreren Schaltflächen aktivieren. Dadurch können Sie AEM Forms as a Cloud Service mit Experience Platform-Tags und Adobe Analytics verbinden, um Leistungsmetriken für Ihre veröffentlichten Formulare zu erfassen und zu verfolgen.

  >[!VIDEO](https://video.tv.adobe.com/v/3424577/enable-adobe-analytics/?quality=12&learn=on)

* [**Adobe Analytics-Berichtsvorlage für Adaptive Forms**](/help/forms/view-understand-aem-forms-analytics-reports.md): Forms as a Cloud Service bietet jetzt einen Adobe Analytics-Bericht OOTB. Dies hilft Ihnen, die Leistung Ihrer Formulare einfach zu verstehen. Die Metriken auf Formularebene bieten Ihnen einen Einblick in die Leistung des Formulars in Bezug auf mehrere wichtige Leistungsindikatoren (KPIs) wie Ausgabedarstellungen, Besuchende, Übermittlungen, durchschnittliche Ausfüllzeit. Durch die Verfolgung des Benutzerverhaltens und des Feedbacks können Sie Bereiche des Formulars identifizieren, die Verwirrung verursachen, und Orientierungsverbesserungen am Formularentwurf und der Funktionalität vornehmen.

  ![Adobe Analytics-Bericht zur Benutzerinteraktion im adaptiven Formular](/help/forms/assets/forms-analytics-report.png)

* **[Formularfragment in Adaptive Forms basierend auf Kernkomponenten](/help/forms/adaptive-form-fragments-core-components.md)**: Verabschieden Sie sich von Duplizierung, optimieren Sie Ihren digitalen Bestand und verbessern Sie die Zusammenarbeit bei der Steigerung Ihrer Formularerstellungserfahrung mit Formularfragmenten. Diese wiederverwendbaren Komponenten lassen sich nahtlos in mehrere Formulare integrieren, wodurch die Erstellung konsistenter und professionell aussehender Formulare optimiert wird. Formularfragmente sorgen für Wiederverwendbarkeit, Standardisierung und Markenkonsistenz durch die Funktion &quot;Einmal ändern und überall widerspiegeln&quot;. Erleben Sie mehr Wartbarkeit und Effizienz, da Aktualisierungen an einem Ort automatisch über alle Formulare hinweg übernommen werden, die diese Fragmente verwenden.

* **[Verbesserter Workflow-Schritt in Adobe Sign](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: Der Schritt &quot;Adobe Sign-Workflow&quot;wurde um Folgendes erweitert:
   * **ID-basierte Authentifizierung für Adobe Sign**: Die Adobe Acrobat Sign-Authentifizierung mit ID-basierter Regierungsauthentifizierung bietet eine zusätzliche Überprüfungsebene, indem sie es Benutzern ermöglicht, ihre Identität mit staatlich ausgestellten Kennungen (Führerschein, nationale Kennung, Pass) zu authentifizieren. Durch die Nutzung von vertrauenswürdigen Identifikationsdokumenten verleiht diese Erweiterung dem Unterzeichnungsprozess ein zusätzliches Maß an Vertrauen und ist somit ideal für Szenarien, die erhöhte Sicherheit, Compliance und Benutzervalidierung erfordern.

   * **Audit-Protokoll für Adobe Sign-Dokumente**: Verwenden Sie die Funktion &quot;Audit-Protokoll&quot;, um detaillierte Einblicke in den Lebenszyklus Ihrer Adobe Sign-Dokumente zu erhalten. Mit dem Audit-Protokoll können Sie jetzt eine umfassende Aufzeichnung aller Aktionen und Interaktionen führen, die mit Ihren Dokumenten verbunden sind. Dazu gehören Details wie etwa die Personen, die das Dokument angesehen, bearbeitet oder unterschrieben haben, sowie Zeitstempel für jedes Ereignis. Diese Verbesserung ist entscheidend für die Einhaltung von Vorschriften, die Beilegung von Streitigkeiten und die Gewährleistung der Integrität Ihrer digitalen Vereinbarungen.

   * **Neue Rollen für Empfänger von Vereinbarungen, die über den Unterzeichner hinausgehen**: Adobe Acrobat Sign hat die Möglichkeit, die Rollen für Vertragsempfänger über den Unterzeichner hinaus zu erweitern, um die Anforderungen an den Workflow besser zu erfüllen. Wenn diese Option aktiviert ist, kann die Rolle jeder Empfängerin und jedes Empfängers in einem Vertrag einzeln konfiguriert werden, wobei die Unterzeichnerin bzw. der Unterzeichner die Standardeinstellung ist.

* **Unterstützung der Seitenzahl in Kommunikations-APIs**: Jetzt können Sie neben dem Abrufen Ihres Dokuments über die Kommunikations-APIs auch die wertvollen Informationen über die Anzahl der im Dokument enthaltenen Seiten erhalten.

* **[Umgang mit Fehlern mit benutzerdefinierten Fehler-Handlern im Regeleditor](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: Sie können jetzt eine benutzerdefinierte Funktion aufrufen, wenn ein von einem externen Dienst zurückgegebener Fehler auftritt, und eine angepasste Antwort für Endbenutzer bereitstellen. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehlercodes aufrufen oder den Kunden darüber informieren, dass der Dienst ausgefallen ist.

* **[64-Bit-Version von AEM Forms Designer](/help/forms/installing-configuring-designer.md)**: Die 64-Bit-Version von AEM Forms Designer bietet verbesserte Leistung, Skalierbarkeit und Speicherverwaltung, um die Erstellung von Formularen zu optimieren. Mit der 64-Bit-Architektur können Sie noch größere und komplexere Projekte einfach angehen, um nahtlose Design-Workflows und eine optimierte Effizienz zu gewährleisten. Verbessern Sie Ihre Formularentwurfskompetenzen und nutzen Sie die Zukunft von AEM Forms Designer mit dieser innovativen Version.

### Programm für frühe Anwender {#forms-early-adopter}

* **[Protect Ihrer Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzer Zugriff erhalten. Diese befestigte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Augen, sondern bietet auch Seelenfrieden. Mit den Signature-APIs kann Ihr Unternehmen die Sicherheit und den Datenschutz von Adobe PDF-Dokumenten schützen, die es verteilt und empfängt. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfänger, für die dies vorgesehen ist, die Dokumente ändern können.

  Sie können schreiben an `aem-forms-early-adopter-program@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

* **[Headless Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de)**: Verwenden Sie Headless Adaptive Forms, um Ihren Entwicklern die Möglichkeit zu geben, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

   * Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
   * Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
   * Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
   * Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

  Sie können eine E-Mail an senden `aem-forms-headless@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten.

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neues CDN-Caching-Verhalten für kampagnenbezogene URL-Parameter {#cache-url-params}

Bei neuen Umgebungen entfernt das CDN standardmäßig Marketing-bezogene Abfrageparameter, um die Leistung von Marketing-Kampagnen und die Cache-Trefferquoten zu erhöhen. Bestehende Umgebungen sind nicht betroffen. [Weitere Informationen](/help/implementing/dispatcher/caching.md#marketing-parameters)

### Regeln für Traffic-Filter (einschließlich WAF-Regeln) für frühe Anwender {#waf-early-adopter}

Filtern Sie den Traffic im CDN anhand von:
* Anfragekopfzeilen und -eigenschaften (z. B. IP-Adresse)
* Traffic-Muster, die bekanntermaßen mit bösartigem Traffic verknüpft sind

Möchten Sie die Funktion ausprobieren und Feedback teilen? E-Mail an senden **aemcs-waf-adopter@adobe.com** von Ihrer offiziellen E-Mail-ID, um mehr über das Programm für frühe Anwender zu erfahren. Der Platz ist begrenzt.

Weitere Informationen zur Funktion finden Sie im Artikel . [here](/help/security/cdn-and-waf-rules.md).

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
