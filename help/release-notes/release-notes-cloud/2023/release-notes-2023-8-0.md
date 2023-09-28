---
title: Versionshinweise für Version 2023.8.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2023.8.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 2b242cb10fb5d1da725c1396633d2db779a78639
workflow-type: tm+mt
source-wordcount: '1686'
ht-degree: 21%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2023.8.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2023.8.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version der Funktion (2023.8.0) ist der 31. August 2023. Die nächste Version der Funktion (2023.9.0) ist für den 28. September 2023 geplant.

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht vom August 2023 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2023.8.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3423535/?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

* Die [Inhaltsfragmentkonsole](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/sites/administering/content-fragments/content-fragments-console.html?lang=en) ermöglicht es Benutzern nun, Tags anzuzeigen und nach Tags zu suchen, die als Metadaten auf Inhaltsfragmente angewendet werden. Benutzer müssen nicht mehr zur Assets-Benutzeroberfläche wechseln, um diese Funktion zu nutzen, wodurch der Kontextwechsel reduziert und die Effizienz verbessert wird.

  ![Tagging in der Inhaltsfragmentkonsole](/help/assets/content-fragments-console-tags.png)
* Der neue Inhaltsfragment-Editor ist jetzt auf AEM as a Cloud Service verfügbar. Sie ermöglicht es Autoren von Inhalten, produktiver zu sein, indem sie ihre Authoring-Aufgaben optimieren und das Wechseln zwischen verschiedenen Apps bei der Bearbeitung von Inhalten reduzieren.
  ![Neuer Inhaltsfragment-Editor](/help/release-notes/assets/newCFEditor.png)

Der neue Inhaltsfragment-Editor bietet die folgenden Vorteile, die im ursprünglichen Editor nicht verfügbar sind:
* Automatisches Speichern zur Verbesserung der Authoring-Effizienz und zur Vermeidung des versehentlichen Verlusts von Bearbeitungen.
* Hierarchische Ansicht eines Inhaltsfragments und seiner Verweise mithilfe der Struktur für die schnelle Navigation innerhalb eines tief strukturierten Fragments.
  ![Strukturstruktur im Inhaltsfragment-Editor](/help/release-notes/assets/newCFEditor_StructureTree.png)

* Online-Upload von Assets als Inhaltsverweise, ohne sie zuerst in Asset DAM hochladen zu müssen
* Ad-hoc-Vorschau des gerenderten Erlebnisses, das vom Inhaltsfragment bereitgestellt wird, um Autoren bei der Visualisierung des Erscheinungsbilds des Inhalts in der Frontend-App zu unterstützen
* 1-Klick-Veröffentlichung und Rückgängigmachen der Veröffentlichung des Inhaltsfragments im Editor
* Anzeigen von und Navigieren zu Sprachkopien während der Bearbeitung eines Inhaltsfragments
  ![Sprachkopien im Inhaltsfragment-Editor](/help/release-notes/assets/newCFEditor_LanguageCopies.PNG)

* Anzeigen von Versionen, um die Zeitleiste eines Inhaltsfragments zu verfolgen

  ![Versionen im Inhaltsfragment-Editor](/help/release-notes/assets/newCFEditor_Versionhistory.PNG)

* Anzeigen übergeordneter Verweise, um Autoren dabei zu unterstützen, die Auswirkungen ihrer Änderungen zu verstehen

  ![Übergeordnete Verweise im Inhaltsfragment-Editor](/help/release-notes/assets/newCFEditor_Parentreferences.PNG)

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Asset-Ansicht {#assets-view-features}

<!--

**Assign metadata form to a folder**

You can now assign metadata form to a specific folder within your Assets Essentials deployment. All assets in the folder, including assets in the sub-folders, then display properties defined in the assigned metadata form.

![assign metadata form to a folder](/help/release-notes/assets/assign-to-folder.png)

-->

* **Massenimport von Assets aus Datenquellen**: Administratoren verfügen jetzt über die [Möglichkeit zum Importieren einer großen Anzahl von Assets](/help/assets/bulk-import-assets-view.md) von einer Datenquelle zu AEM Assets. Administratoren müssen keine einzelnen Assets oder Ordner mehr in AEM Assets hochladen. Zu den unterstützten Datenquellen für den Massenimport gehören Azure, AWS, Google Cloud und Dropbox.

  ![Massenimport von Assets aus einer Datenquelle](/help/release-notes/assets/bulk-import.png)

* **Bildbearbeitungswerkzeuge auf Basis von Adobe Expreß**: Einfach und intuitiv [Bildbearbeitungswerkzeuge auf Basis von Adobe Expreß](/help/assets/edit-images-assets-view.md) direkt in AEM Assets verfügbar sind, um die Wiederverwendung von Inhalten zu steigern und die Content-Geschwindigkeit zu beschleunigen.

  ![Bildbearbeitung mit Adobe Expreß](/help/release-notes/assets/edit-adobe-express.png)

* **Flexibilität beim Einfügen von Elementen für meinen Workspace-Schnellzugriff**: Möglichkeit, Elemente für Sie, für Ihre gesamte Organisation oder für eine Liste von Gruppen auszuwählen und anzuheften, damit sie in der [Bereich &quot;Schnellzugriff&quot;in My Workspace](/help/assets/my-workspace-assets-view.md) basierend auf Ihrer Auswahl.

  ![Elemente für Gruppen fixieren](/help/release-notes/assets/pin-items-for-groups.png)

### Neue Funktionen in der Administratoransicht {#admin-view-features}

**Verbesserungen der Suche**

* Administratoren können jetzt [Konfigurieren der Stapelgröße von Assets](/help/assets/search-assets.md#configure-asset-batch-size) die bei der Durchführung einer Suche angezeigt werden. Die Asset-Suchergebnisse zeigen ein Vielfaches der konfigurierten Stapelgrößenanzahl an, wenn Sie weiter nach unten scrollen, um die Ergebnisse zu laden. Sie können aus den verfügbaren Batch-Größen 200, 500 und 1000 Assets auswählen. Wenn Sie eine niedrigere Stapelgrößenanzahl festlegen, werden die Antwortzeiten der Suche beschleunigt.

  ![Konfiguration der Batch-Größe von Assets](/help/release-notes/assets/assets-batch-size-configuration.png)

* Experience Manager Assets enthält jetzt die neue Version 9 von `damAssetLucene` Index. `damAssetLucene-9` ändert das Verhalten der Facette Oak Query in [Zugriffskontrolle auf Facettenzählungen wird nicht mehr ausgewertet](/help/assets/search-assets.md) vom zugrunde liegenden Suchindex zurückgegeben, was zu schnelleren Suchantwortzeiten führt.

### Funktionen zur Vorabversion sind verfügbar in [!DNL Experience Manager Assets] {#prerelease-features-assets}

* **Dynamic Media**: [Unterstützung für mehrere Untertitel und mehrere Audiospuren für Videos in Dynamic Media](/help/assets/dynamic-media/video.md#about-msma)—Sie können jetzt einfach mehrere Untertitel und mehrere Audiospuren zu einem Hauptvideo hinzufügen. Diese Funktion bedeutet, dass Ihre Videos für eine globale Zielgruppe zugänglich sind. Sie können ein einzelnes veröffentlichtes primäres Video für eine globale Zielgruppe in mehreren Sprachen anpassen und die Richtlinien zur Barrierefreiheit für verschiedene geografische Regionen einhalten. Autorinnen und Autoren können die Untertitel und Audiospuren auch über eine einzige Registerkarte in der Benutzeroberfläche verwalten.

  ![Registerkarte &quot;Untertitel und Audiospuren&quot;auf der Seite &quot;Eigenschaften&quot;eines ausgewählten Video-Assets.](/help/release-notes/assets/msma-aem-cs.png)*Registerkarte &quot;Untertitel und Audiospuren&quot;auf der Seite &quot;Eigenschaften&quot;eines ausgewählten Video-Assets.*

* **Assets**: Möglichkeit zur Auswahl von ZIP-Archiven, die in Experience Manager verwaltet werden, und [Extrahieren der Dateien direkt in Experience Manager](/help/assets/manage-digital-assets.md#extract-zip-archives) , ohne sie herunterzuladen.

  ![Elemente für Gruppen fixieren](/help/release-notes/assets/extract-archive.png)


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#new-features-available-in-forms-channel}

* [**Enterprise-Unterstützung für Google reCAPTCHA**](/help/forms/captcha-adaptive-forms.md): Verwenden Sie Google reCAPTCHA Enterprise in einem adaptiven Formular, um einen verbesserten Schutz vor betrügerischer Aktivität und Spam zu bieten und so eine sicherere Benutzererfahrung zu bieten. Dank der erweiterten Risikoanalyse und nahtloser Integration können echte Benutzer problemlos Formulare senden, während Bots effektiv blockiert werden.


### Funktionen zur Vorabversion sind verfügbar in [!DNL Forms] {#pre-release-features-available-in-forms-channel}

* **Adobe Analytics mit Experience Cloud-Setup-Automatisierung für Forms**: Sie können Adobe Analytics jetzt mit Experience Cloud Setup Automation mit mehreren Schaltflächen aktivieren. Dadurch können Sie AEM Forms as a Cloud Service mit Experience Platform-Tags und Adobe Analytics verbinden, um Leistungsmetriken für Ihre veröffentlichten Formulare zu erfassen und zu verfolgen.

* **Adobe Analytics-Berichtsvorlage für Adaptive Forms**: Forms as a Cloud Service bietet jetzt einen Adobe Analytics-Bericht OOTB. Dies hilft Ihnen, die Leistung Ihrer Formulare einfach zu verstehen. Die Metriken auf Formularebene bieten Ihnen einen Einblick in die Leistung des Formulars in Bezug auf mehrere wichtige Leistungsindikatoren (KPIs) wie Ausgabedarstellungen, Besuchende, Übermittlungen, durchschnittliche Ausfüllzeit. Durch die Verfolgung des Benutzerverhaltens und des Feedbacks können Sie Bereiche des Formulars identifizieren, die Verwirrung verursachen, und Orientierungsverbesserungen am Formularentwurf und der Funktionalität vornehmen.

  ![Adobe Analytics-Bericht zur Benutzerinteraktion im adaptiven Formular](/help/forms/assets/forms-analytics-report.png)

* **[Formularfragment in Adaptive Forms basierend auf Kernkomponenten](/help/forms/adaptive-form-fragments-core-components.md)**: Verabschieden Sie sich von Duplizierung, optimieren Sie Ihren digitalen Bestand und verbessern Sie die Zusammenarbeit bei der Steigerung Ihrer Formularerstellungserfahrung mit Formularfragmenten. Diese wiederverwendbaren Komponenten lassen sich nahtlos in mehrere Formulare integrieren, wodurch die Erstellung konsistenter und professionell aussehender Formulare optimiert wird. Formularfragmente sorgen für Wiederverwendbarkeit, Standardisierung und Markenkonsistenz durch die Funktion &quot;Einmal ändern und überall widerspiegeln&quot;. Erleben Sie mehr Wartbarkeit und Effizienz, da Aktualisierungen an einem Ort automatisch über alle Formulare hinweg übernommen werden, die diese Fragmente verwenden.

* **[Verbesserter Workflow-Schritt in Adobe Sign](/help/forms/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)**: Der Schritt &quot;Adobe Sign-Workflow&quot;wurde um Folgendes erweitert:
   * **ID-basierte Authentifizierung für Adobe Sign**: Die Adobe Acrobat Sign-Authentifizierung mit ID-basierter Regierungsauthentifizierung bietet eine zusätzliche Überprüfungsebene, indem sie es Benutzern ermöglicht, ihre Identität mit staatlich ausgestellten Kennungen (Führerschein, nationale Kennung, Pass) zu authentifizieren. Durch die Nutzung von vertrauenswürdigen Identifikationsdokumenten verleiht diese Erweiterung dem Unterzeichnungsprozess ein zusätzliches Maß an Vertrauen und ist somit ideal für Szenarien, die erhöhte Sicherheit, Compliance und Benutzervalidierung erfordern.

   * **Audit-Protokoll für Adobe Sign-Dokumente**: Verwenden Sie die Funktion &quot;Audit-Protokoll&quot;, um detaillierte Einblicke in den Lebenszyklus Ihrer Adobe Sign-Dokumente zu erhalten. Mit dem Audit-Protokoll können Sie jetzt eine umfassende Aufzeichnung aller Aktionen und Interaktionen führen, die mit Ihren Dokumenten verbunden sind. Dazu gehören Details wie etwa die Personen, die das Dokument angesehen, bearbeitet oder unterschrieben haben, sowie Zeitstempel für jedes Ereignis. Diese Verbesserung ist entscheidend für die Einhaltung von Vorschriften, die Beilegung von Streitigkeiten und die Gewährleistung der Integrität Ihrer digitalen Vereinbarungen.

   * **Neue Rollen für Empfänger von Vereinbarungen, die über den Unterzeichner hinausgehen**: Adobe Acrobat Sign hat die Möglichkeit, die Rollen für Vertragsempfänger über den Unterzeichner hinaus zu erweitern, um die Anforderungen an den Workflow besser zu erfüllen. Wenn diese Option aktiviert ist, kann die Rolle jeder Empfängerin und jedes Empfängers in einem Vertrag einzeln konfiguriert werden, wobei die Unterzeichnerin bzw. der Unterzeichner die Standardeinstellung ist.

* **[Protect Ihrer Dokumente mit Document Assurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den Document Assurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzer Zugriff erhalten. Diese befestigte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Augen, sondern bietet auch Seelenfrieden. Mit den Signature-APIs kann Ihr Unternehmen die Sicherheit und den Datenschutz von Adobe PDF-Dokumenten schützen, die es verteilt und empfängt. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfänger, für die dies vorgesehen ist, die Dokumente ändern können.

* **Unterstützung der Seitenzahl in Kommunikations-APIs**: Jetzt können Sie neben dem Abrufen Ihres Dokuments über die Kommunikations-APIs auch die wertvollen Informationen über die Anzahl der im Dokument enthaltenen Seiten erhalten.

* **[Umgang mit Fehlern mit benutzerdefinierten Fehler-Handlern im Regeleditor](/help/forms/add-custom-error-handler-adaptive-forms-core-components.md)**: Sie können jetzt eine benutzerdefinierte Funktion aufrufen, wenn ein von einem externen Dienst zurückgegebener Fehler auftritt, und eine angepasste Antwort für Endbenutzer bereitstellen. Sie können beispielsweise einen benutzerdefinierten Workflow im Backend für bestimmte Fehlercodes aufrufen oder den Kunden darüber informieren, dass der Dienst ausgefallen ist.


### Early-Adopter-Programm für adaptive Headless-Formulare {#forms-early-adopter}

Verwendung [Headless Adaptive Forms](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html?lang=de) , damit Ihre Entwickler interaktive Formulare erstellen, veröffentlichen und verwalten können, auf die über APIs und nicht über eine herkömmliche grafische Benutzeroberfläche zugegriffen und mit denen interagiert werden kann. Adaptive Headless-Formulare unterstützen Sie bei Folgendem:

* Erstellen hochwertiger Mehrkanal-Formulare in der gewünschten Programmiersprache
* Native Integration von Formularen in Ihre Desktop- und Mobile Apps, Websites und Chat-Anwendungen
* Wiederverwenden Ihrer proprietären UI-Komponenten mit Formularanwendungen
* Nutzung der Leistungsfähigkeit von Adobe Experience Manager Forms

Sie können eine E-Mail an senden `aem-forms-headless@adobe.com` von Ihrer offiziellen E-Mail-ID, um dem frühen Adopter-Programm beizutreten.


## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### CDN-Protokolle {#cdn-logs}

Laden Sie CDN-Protokolle aus Cloud Manager herunter. Dies ist für die Optimierung des Cache-Trefferverhältnisses und eine bessere Sichtbarkeit des Inhaltsbereitstellungsflusses nützlich. [Informationen zu](/help/implementing/developing/introduction/logging.md#cdn-log) das CDN-Protokollformat. Diese Funktion wird Anfang September schrittweise für Kunden eingeführt.

### CDN und WAF-Regeln für frühe Anwender {#waf-early-adopter}

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
