---
title: Versionshinweise für Version 2023.8.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.8.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a0ffa6cf-64ae-468c-93f4-ac6805ef907e
feature: Release Information
role: Admin
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '1691'
ht-degree: 100%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.8.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.8.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version mit neuen Funktionen von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2023.8.0) ist der 31. August 2023. Die nächste Version mit neuen Funktionen (2023.9.0) ist für den 28. September 2023 geplant.

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2023.8.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version vom August 2023:

>[!VIDEO](https://video.tv.adobe.com/v/3423535/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

* Über die [Inhaltsfragmentkonsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=de) können Benutzende nun Tags anzeigen und nach Tags suchen, die als Metadaten auf Inhaltsfragmente angewendet werden. Benutzende müssen nicht mehr zur Assets-Benutzeroberfläche wechseln, um diese Funktion zu nutzen. Dadurch werden Kontextwechsel reduziert und die Effizienz verbessert.

  ![Tagging in der Inhaltsfragmentkonsole](/help/assets/content-fragments-console-tags.png)
* Der neue Inhaltsfragmenteditor ist jetzt in AEM as a Cloud Service verfügbar. Er ermöglicht es Autorinnen und Autoren von Inhalten, produktiver zu sein, indem deren Authoring-Aufgaben optimiert und nötige Wechsel zwischen verschiedenen Apps bei der Bearbeitung von Inhalten reduziert werden.
  ![Neuer Inhaltsfragmenteditor](/help/release-notes/assets/newCFEditor.png)

Der neue Inhaltsfragmenteditor hat gegenüber dem ursprünglichen Editor folgende Vorteile:

* automatisches Speichern für eine höhere Authoring-Effizienz und zur Vermeidung versehentlicher Bearbeitungsverluste.
* hierarchische Ansicht eines Inhaltsfragments und seiner Verweise mithilfe der Baumstruktur zur schnellen Navigation innerhalb eines tief strukturierten Fragments.
  ![Baumstruktur im Inhaltsfragmenteditor](/help/release-notes/assets/newCFEditor_StructureTree.png)

* Inline-Upload von Assets als Inhaltsverweise, ohne sie zuerst in das Asset-DAM-System hochladen zu müssen
* Ad-hoc-Vorschau des gerenderten Erlebnisses, das vom Inhaltsfragment bereitgestellt wird, um Autorinnen und Autoren bei der Look-and-Feel-Visualisierung der Inhalte in der Frontend-App zu unterstützen
* Veröffentlichen und Aufheben der Veröffentlichung des Inhaltsfragments im Editor mit einem Klick
* Anzeigen von und Navigieren zu Sprachkopien beim Bearbeiten eines Inhaltsfragments
  ![Sprachkopien im Inhaltsfragmenteditor](/help/release-notes/assets/newCFEditor_LanguageCopies.PNG)

* Anzeigen von Versionen, um die Timeline eines Inhaltsfragments nachzuverfolgen

  ![Versionen im Inhaltsfragmenteditor](/help/release-notes/assets/newCFEditor_Versionhistory.PNG)

* Anzeigen übergeordneter Verweise, um Autorinnen und Autoren dabei zu unterstützen, die Wirkung ihrer Änderungen zu verstehen

  ![Übergeordnete Verweise im Inhaltsfragmenteditor](/help/release-notes/assets/newCFEditor_Parentreferences.PNG)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

* **Massenimport von Assets aus Datenquellen**: Admins [können nun eine große Anzahl von Assets aus einer Datenquelle in AEM Assets importieren](/help/assets/bulk-import-assets-view.md). Die Admins müssen keine einzelnen Assets oder Ordner mehr in AEM Assets hochladen. Zu den unterstützten Datenquellen für den Massenimport gehören Azure, AWS, Google Cloud und Dropbox.

  ![Massenimport von Assets aus einer Datenquelle](/help/release-notes/assets/bulk-import.png)

* **Bildbearbeitungswerkzeuge von Adobe Express**: Einfache und intuitive [Bildbearbeitungswerkzeuge von Adobe Express](/help/assets/edit-images-assets-view.md), die direkt in AEM Assets zur Verfügung stehen, um die Wiederverwendung von Inhalten zu verbessern und die Inhaltsgeschwindigkeit zu erhöhen.

  ![Bildbearbeitung mit Adobe Express](/help/release-notes/assets/edit-adobe-express.png)

* **Flexibilität beim Anheften von Elementen für den Schnellzugriff in „Mein Arbeitsbereich“**: Sie können Objekte für sich selbst, für Ihr gesamtes Unternehmen oder für eine Liste von Gruppen auswählen und anheften, sodass sie im [Schnellzugriffsbereich von „Mein Arbeitsbereich“](/help/assets/my-workspace-assets-view.md) entsprechend Ihrer Auswahl angezeigt werden.

  ![Anheften von Elementen für Gruppen](/help/release-notes/assets/pin-items-for-groups.png)

### Neue Funktionen in der Admin-Ansicht {#admin-view-features}

**Verbesserungen bei der Suche**

* Admins können nun die [Batch-Größe von Assets konfigurieren](/help/assets/search-assets.md#configure-asset-batch-size), die bei einer Suche angezeigt werden. Die Asset-Suchergebnisse zeigen ein Vielfaches der konfigurierten Batch-Größenanzahl an, wenn Sie weiter nach unten scrollen, um die Ergebnisse zu laden. Sie können aus den verfügbaren Batch-Größen von 200, 500 oder 1000 Assets auswählen. Wenn Sie eine niedrigere Batch-Größenanzahl festlegen, werden die Antwortzeiten der Suche beschleunigt.

  ![Konfiguration der Batch-Größe von Assets](/help/release-notes/assets/assets-batch-size-configuration.png)

* Experience Manager Assets enthält nun die neue Version 9 des `damAssetLucene`-Index. `damAssetLucene-9`[ ändert das Verhalten der Facettenzählung der Oak-Abfrage, damit die Zugriffskontrolle nicht mehr entsprechend der Facettenzahlen ausgewertet wird, die vom zugrunde liegenden Suchindex zurückgegeben werden, was zu schnelleren Antwortzeiten bei der Suche führt.](/help/assets/search-assets.md)

### Vorabversionsfunktionen, die in [!DNL Experience Manager Assets] verfügbar sind {#prerelease-features-assets}

* **Dynamic Media**: [Unterstützung für mehrfache Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma) – Sie können jetzt ganz einfach mehrfache Untertitel und mehrere Audiospuren zu einem primären Video hinzufügen.  Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

  ![Registerkarte „Untertitel und Audiospuren“ auf der Seite „Eigenschaften“ eines ausgewählten Video-Assets.](/help/release-notes/assets/msma-aem-cs.png)*Registerkarte „Untertitel und Audiospuren“ auf der Seite „Eigenschaften“ eines ausgewählten Video-Assets.*

* **Assets**: Sie können in Experience Manager verwaltete ZIP-Archive auswählen und [die Dateien direkt in Experience Manager extrahieren](/help/assets/manage-digital-assets.md#extract-zip-archives), ohne sie herunterzuladen.

  ![Anheften von Elementen für Gruppen](/help/release-notes/assets/extract-archive.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Unterstützung für Google reCAPTCHA Enterprise**](/help/forms/captcha-adaptive-forms.md): Verwenden Sie Google reCAPTCHA Enterprise in einem adaptiven Formular, um einen besseren Schutz vor betrügerischen Aktivitäten und Spam zu bieten und so ein sichereres Anwendererlebnis zu ermöglichen. Dank erweiterter Risikoanalyse und nahtloser Integration können echte Benutzende problemlos Formulare absenden, während Bots effektiv blockiert werden.


### Vorabversionsfunktionen, die in [!DNL Forms] verfügbar sind {#pre-release-features-available-in-forms-channel}

* **Adobe Analytics mit Experience Cloud-Setup-Automatisierung für Formulare**: Sie können nun Adobe Analytics dank Experience Cloud-Setup-Automatisierung mit wenigen Klicks aktivieren. So können Sie AEM Forms as a Cloud Service mit Experience Platform-Tags und Adobe Analytics verbinden, um Leistungsmetriken für Ihre veröffentlichten Formulare zu erfassen und nachzuverfolgen.

* **Adobe Analytics-Berichtsvorlage für adaptive Formulare**: Forms as a Cloud Service bietet nun einen vorkonfigurierten Adobe Analytics-Bericht. Dies hilft Ihnen, die Leistung Ihrer Formulare einfach zu verstehen. Die Metriken auf Formularebene bieten Ihnen einen Einblick in die Leistung des Formulars in Bezug auf mehrere wichtige Leistungsindikatoren (KPIs) wie Ausgabedarstellungen, Besuchende, Übermittlungen, durchschnittliche Ausfüllzeit. Durch Nachverfolgung von Benutzerverhalten und -Feedback können Sie Formularbereiche identifizieren, die Verwirrung verursachen, und so Verbesserungen am Formular-Design und an der Formularfunktionalität erwirken.

  ![Adobe Analytics-Bericht zur Benutzerinteraktion im adaptiven Formular](/help/forms/assets/forms-analytics-report.png)

* **[Formularfragment in adaptiven Formularen auf Basis auf Kernkomponenten](/help/forms/adaptive-form-fragments-core-components.md)**: Keine Duplizierung mehr! Außerdem können Sie Ihre digitalen Bestände und die Zusammenarbeit optimieren, während Sie das Anwendererlebnis bei der Formularerstellung mit Formularfragmenten verbessern. Diese wiederverwendbaren Komponenten lassen sich nahtlos in mehrere Formulare integrieren, was die Erstellung konsistenter und professionell aussehender Formulare optimiert. Formularfragmente sorgen für Wiederverwendbarkeit, Standardisierung und Markenkonsistenz durch die Funktion „Einmal ändern und überall widerspiegeln“. Erleben Sie mehr Wartbarkeit und Effizienz, da Aktualisierungen an einem Ort automatisch über alle Formulare hinweg übernommen werden, die diese Fragmente verwenden.

* **[Verbesserter Workflow-Schritt in Adobe Sign](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: Der Workflow-Schritt in Adobe Sign enthält die folgenden Verbesserungen:
   * **Authentifizierung mit amtlichem Lichtbildausweis für Adobe Sign**: Die Authentifizierung mit amtlichem Lichtbildausweis von Adobe Acrobat Sign bietet eine zusätzliche Verifizierungsebene, indem Benutzenden ermöglicht wird, ihre Identität anhand von amtlichen Lichtbildausweisen (Führerschein, Personalausweis, Reisepass) zu authentifizieren. Durch die Nutzung von vertrauenswürdigen Identifikationsdokumenten verleiht diese Erweiterung dem Unterzeichnungsprozess ein zusätzliches Maß an Vertrauen und ist somit ideal für Szenarien, die erhöhte Sicherheit, Compliance und Benutzervalidierung erfordern.

   * **Audit-Protokoll für Adobe Sign-Dokumente**: Verwenden Sie die Audit-Protokoll-Funktion, um ausführliche Erkenntnisse zum Lebenszyklus Ihrer Adobe Sign-Dokumente zu erhalten. Mit dem Audit-Protokoll können Sie jetzt eine umfassende Aufzeichnung aller Aktionen und Interaktionen führen, die mit Ihren Dokumenten verbunden sind. Dazu gehören Details wie etwa die Personen, die das Dokument angesehen, bearbeitet oder unterschrieben haben, sowie Zeitstempel für jedes Ereignis. Diese Verbesserung ist entscheidend für die Einhaltung von Vorschriften, die Beilegung von Streitigkeiten und die Gewährleistung der Integrität Ihrer digitalen Vereinbarungen.

   * **Neue Rollen für Empfängerinnen und Empfänger von Vereinbarungen über die Unterzeichnerinnen bzw. Unterzeichner hinaus**: Adobe Acrobat Sign bietet die Möglichkeit, die Rollen für Empfängerinnen und Empfänger von Vereinbarungen über die Personen hinaus zu erweitern, die unterzeichnet haben, um Workflow-Anforderungen besser zu erfüllen. Wenn diese Option aktiviert ist, kann die Rolle jeder Empfängerin und jedes Empfängers in einem Vertrag einzeln konfiguriert werden, wobei die Person, die unterzeichnet hat, die Standardeinstellung ist.

* **[Schutz Ihrer Dokumente mit Document Assurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den Document Assurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch die Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sondern sorgt auch für Seelenfrieden. Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies vorgesehen ist, die Dokumente ändern können.

* **Unterstützung der Seitenzahl in Kommunikations-APIs**: Sie können nun neben dem Abruf Ihres Dokuments über die Kommunikations-APIs auch wertvolle Informationen über die Anzahl der im Dokument enthaltenen Seiten beziehen.

* **[Fehlerhandhabung mit benutzerdefinierten Fehler-Handlern im Regeleditor](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: Sie können nun eine benutzerdefinierte Funktion aufrufen, wenn ein von einem externen Dienst zurückgegebener Fehler auftritt, und eine maßgeschneiderte Antwort für Endbenutzerinnen und -benutzer bereitstellen. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehler-Codes aufrufen oder die Kundin bzw. den Kunden darüber informieren, dass der Dienst nicht verfügbar ist.


### Early-Adopter-Programm für adaptive Headless-Formulare {#forms-early-adopter}

Die Benutzung von [adaptiven Headless-Formularen](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de) ermöglicht es Entwicklerinnen und Entwicklern, interaktive Formulare zu erstellen, zu veröffentlichen und zu verwalten, für die der Zugriff und die Interaktion über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche möglich ist. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

* Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
* Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an `aem-forms-headless@adobe.com` senden, um am Early-Adopter-Programm teilzunehmen.


## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### CDN-Protokolle {#cdn-logs}

Laden Sie CDN-Protokolle aus Cloud Manager herunter. Dies ist nützlich für die Optimierung des Cache-Treffer-Verhältnisses und eine bessere Sichtbarkeit des Inhaltsbereitstellungsflusses. [Erfahren Sie mehr](/help/implementing/developing/introduction/logging.md#cdn-log) über das CDN-Protokollformat. Diese Funktion wird Anfang September schrittweise für Kundinnen und Kunden eingeführt.

### CDN und WAF-Regeln – Early-Adopter-Programm {#waf-early-adopter}

Filtern Sie den Traffic im CDN anhand von:

* Anfragekopfzeilen und -eigenschaften (z. B. IP-Adresse)
* Traffic-Muster, die bekanntermaßen mit bösartigem Traffic verknüpft sind

Möchten Sie die Funktion ausprobieren und Feedback geben? Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an **aemcs-waf-adopter@adobe.com** senden, um am Early-Adopter-Programm teilzunehmen. Die Plätze sind begrenzt.

Weitere Informationen zur Funktion finden Sie im Artikel [hier](/help/security/traffic-filter-rules-including-waf.md).


## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
