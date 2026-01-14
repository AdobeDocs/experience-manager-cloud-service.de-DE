---
title: Versionshinweise für Version 2021.7.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2021.7.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 848f6a29-2e0f-4976-8ed7-6b7f69408c1b
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1292'
ht-degree: 67%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020 und 2021.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2021.7.0) war der 29. Juli 2021.
Die folgende Version (2021.8.0) wurde am 26. August 2021 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht Juli 2021](https://video.tv.adobe.com/v/335580) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## Experience Manager Foundation as a Cloud Service {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Flexiblere Dispatcher-Konfiguration: Projekte können leichter organisiert werden. Beispielsweise können Sie jetzt mehrere Rewrite-Regeldateien einbeziehen, die Ihre Website-Struktur widerspiegeln. [Erfahren Sie mehr &#x200B;](/help/implementing/dispatcher/disp-overview.md#validation-debug) diesen flexiblen Modus, einschließlich der Strukturierung Ihrer Dispatcher-Konfiguration, damit Sie sie nutzen können.
* Die Benutzeroberfläche für die Strukturreplikation unter der Registerkarte „Verteilen“ des Replikationsagenten sollte als veraltet betrachtet werden und wurde nach dem 30. September 2021 entfernt. [Erfahren Sie mehr](/help/operations/replication.md#tree-activation) über alternative Replikationsstrategien.
* Das Bundle `org.apache.sling.datasource-1.0.4.jar` für die Unterstützung der Sling-Datenquelle wurde entfernt, da es veraltete Funktionen aufweist und von Kunden nicht verwendet wird.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Mit der Funktion zur Inhaltsautomatisierung können [!DNL Experience Manager Assets] die [!DNL Adobe Creative Cloud]-APIs verwenden, um die Asset-Produktion skaliert zu automatisieren. Die Inhaltsgeschwindigkeit wird verbessert, indem die zum Erstellen von Varianten desselben Assets erforderliche Zeit verkürzt und die Anzahl der Iterationen erheblich verringert werden. Die Funktion erfordert keine Programmierung und funktioniert aus dem DAM heraus. Siehe [Erzeugen von Varianten von Assets mithilfe der Creative Cloud-Integration](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] enthält den [!DNL Document Cloud]-PDF-Viewer zur nativen Vorschau von PDF-Dokumenten. Mit dieser Funktion können Benutzer mehrseitige PDF-Dateien ohne Dateiverarbeitung oder Konvertierung in der Vorschau anzeigen. Diese Funktion verbessert die Parität mit [!DNL Experience Manager] 6.5. Die im Viewer verfügbaren Steuerelemente umfassen Zoom, Navigieren zu Seiten, Entfernen von Steuerelementen und Anzeigen im Vollbildmodus. Benutzer können auch eine Vorschau der Seiten und Lesezeichen anzeigen und zu ihnen springen. Kommentare zur Datei selbst werden unterstützt. Kommentare und Anmerkungen zu Inhalten in der PDF-Datei sind für eine künftige Version geplant.

  ![PDF-Dateien in [!DNL Experience Manager] in der Vorschau mit dem PDF-Viewer anzeigen](/help/assets/assets/preview-pdf-file-viewer.png)

* Die Download-Funktion Linkfreigabe verwendet asynchrone Downloads, die die Download-Geschwindigkeit erhöhen. Weitere Informationen finden Sie unter [Herunterladen von freigegebenen Assets mithilfe der Linkfreigabe](/help/assets/download-assets-from-aem.md#link-share-download).

  ![Posteingang herunterladen](/help/assets/assets/download-inbox.png)

* Die Anzeigeeinstellungen wurden verbessert, sodass Benutzer eine Standardansicht und einen standardmäßigen Sortierparameter wählen können.

  ![Festlegen der Standardansicht in den [!UICONTROL Anzeigeeinstellungen]](/help/assets/assets/view-settings-for-defaults.png)

* Benutzer können die Ordner anhand von Eigenschaftsprädikaten suchen und filtern.

  ![Filtern von Suchordnern mithilfe von Sucheigenschaften](/help/assets/assets/search-folders-via-predicates.png)

### Neue Funktionen im Kanal der Vorabversion von [!DNL Assets] {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* Wenn Sie digitale Assets als Link freigeben, können Benutzer die URL in die Zwischenablage kopieren. Dank der Verbesserung können Sie Assets schneller und bequemer freigeben.

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

Die API `com.day.cq.dam.api.collection.SmartCollection` ist in [!DNL Experience Manager] as a [!DNL Cloud Service] nicht verfügbar. (CQ-4326322)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* Sie können jetzt den Service für die automatische Formularkonvertierung verwenden, um [PDF forms in französischer, deutscher und spanischer Sprache) in &#x200B;](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=de?#language-specific-meta-model) Formulare zu konvertieren.
* Es wurde ein separates Bedienfeld zum Vorlagen-Editor hinzugefügt, um Fehler im Zusammenhang mit Komponenten von adaptiven Formularen anzuzeigen. Dies hilft, alle Fehler in adaptiven Formularen an einem Ort zu konsolidieren und die Auflösungszeit zu verkürzen.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) helfen Ihnen, XDP-Vorlagen und XML-Daten zu kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:
   * Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   * Erzeugen Sie Ausgabeformulare in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckdatenströme.
   * Erzeugen von PDF-Druckdateien aus einem XFA-Formular-PDF und aus einem Adobe Acrobat-Formular.

* **Variablendaten-Externalizer**: Sie können Daten von AEM-Workflow-Variablen in einem externen Speichersystem speichern, das von Ihrer Organisation verwaltet wird.

* **Acroform-basiertes aufzuzeichnendes Dokument**: Sie können auch [Adobe Acrobat Form PDF (Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=de) als Vorlage für ein aufzuzeichnendes Dokument neben XFA-basierten Formularvorlagen verwenden.

* **Microsoft® Azure-Datenspeicher-Connector**: Sie können jetzt [Formulardatenmodell mit Microsoft verbinden® Azure-Speicher](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html). Damit können Sie Daten adaptiver Formulare abrufen und im Microsoft® Azure-Speicher als BLOB speichern.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* CIF-Kernkomponenten v2
   * Vereinfachte und verbesserte Konfigurationen für PDP/PLP-URL und SEO
   * Visueller Indikator für gestaffelte Produktdaten im Authoring-Modus für bessere Sichtbarkeit bevorstehender Änderungen
   * Neue Sitemap-Komponente für Inhalte und Commerce-Seiten

* Unterstützung für [Adobe Commerce AI Product Recommendation, powered by Adobe AI](https://business.adobe.com/ai/adobe-genai.html) in der AEM-Storefront mit vordefinierten oder direkt erstellten Empfehlungen

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### Fehlerbehebungen {#bug-fixes-screens}

* Die Einstellungen des Content Providers werden jetzt während der Erstellung oder Aktualisierung validiert.

* Alle Anzeigeansichten verfügen über eine Ordnerspalte.

* Sie können die Screens-Inhaltsstruktur erweitern.

* `bulk-offline-update-service` fehlten für einige Umgebungen alle Berechtigungen.

* Der Hilfe-Link wurde entsprechend der neuen Screens-Cloud-Dokumentation aktualisiert.

* Die Zuweisung von Wiedergabelisten aufzuheben und das Entfernen von Wiedergabelisten mit zugewiesenen Playern zu verbieten, funktioniert jetzt.

* Der Player lädt Assets jetzt erneut herunter, wenn der Cache „ALL“ gelöscht wird.

* Die Wiederholungszeitplanung funktioniert jetzt, wenn die *Endzeit* für den folgenden Tag festgelegt ist.

* `Back&Forward` funktioniert jetzt in der Screens as a Cloud Service-Benutzeroberfläche.

* Tags mit demselben Namen, aber unterschiedlichen Namespaces konnten zuvor nicht erstellt werden.

## XML-Dokumentation für Experience Manager as a Cloud Service {#xml-documentation}

### Neue Funktionen {#what-is-new-xml-documentation}

Die XML-Dokumentation für Experience Manager as a Cloud Service ist allgemein verfügbar. Kunden von Experience Manager as a Cloud Service können damit ein XML Documentation-Add-on erwerben, um technische Inhalte zu importieren, zu erstellen, zu verwalten und über mehrere Kanäle, einschließlich Experience Manager Sites, bereitzustellen.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.7.0.

### Veröffentlichungsdatum {#release-cm-july}

Die Version 2021.7.0 von Cloud Manager in AEM as a Cloud Service wurde am 15. Juli 2021 veröffentlicht.
Die nächste Version wird am 12. August 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cm-july}

* Kundinnen und Kunden können jetzt Azul 8- und 11-JDKs für ihre Cloud Manager-Build-Prozesse verwenden und entweder festlegen, eines dieser JDKs für Toolchain-kompatible Maven-Plug-ins *oder* für die gesamte Maven-Prozessausführung zu verwenden.

* Die ausgehende Austritts-IP wird jetzt in der Protokolldatei des Build-Schritts protokolliert.

* Staging- und Produktionsumgebungen, die alte Versionen von AEM ausführen, melden jetzt den Status **Update verfügbar**.

* Die maximale Anzahl unterstützter SSL-Zertifikate wurde auf 20 pro Programm erhöht.

* Die maximale Anzahl der Domains, die konfiguriert werden können, wurde auf 500 pro Umgebung erhöht.

* Die Schaltfläche **Git verwalten** wurde in **Git-Informationen abrufen** umbenannt und das Dialogfeld wurde optisch aufgefrischt.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 28 aktualisiert.

### Fehlerbehebungen {#bug-fixes-cm-july}

* Beim Binden einer IP-Zulassungsliste an eine Umgebung ist die Vorschau jetzt immer eine verfügbare Option.

* Beim manuellen Navigieren zur Seite mit den Ausführungsdetails für eine nicht vorhandene Ausführung wird nicht mehr ein Bildschirm mit endlosen Ladevorgängen, sondern ein Fehler angezeigt.

* Die Fehlermeldung, die angezeigt wurde, wenn die maximale Anzahl von SSL-Zertifikaten erreicht wurde, war nicht hilfreich.

* Versionsnummern werden auf der Pipeline-Karte auf der Seite **Überblick** jetzt ohne Diskrepanzen angezeigt.

* Der Assistent „Programm hinzufügen“ gibt jetzt nicht mehr an, dass der Name nach der Erstellung nicht mehr geändert werden könne.

### Bekannte Probleme {#known-issues-cm-july}

Kundschaft, die zur Verwendung der Azul-JDKs wechselt, sollte beachten, dass nicht alle vorhandenen Anwendungen ohne Fehler auf Azul-JDK kompiliert werden. Adobe empfiehlt, vor dem Wechsel lokal zu testen.

## Cloud Acceleration Manager {#cam}

### Veröffentlichungsdatum {#release-date-july-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 15. Juli 2021.

### Neue Funktionen {#what-is-new-cam}

Cloud Acceleration Manager ist eine Cloud-basierte Anwendung, die IT-Teams während des gesamten Übergangszeitraums von der Planung bis hin zur Live-Schaltung auf dem Cloud-Service begleitet. Bereiten Sie Ihr Team auf eine erfolgreiche Migration vor, indem Sie von Adobe empfohlene Best Practices, Tipps, Dokumentationen und Tools bereitstellen, die Sie in jeder Phase des Journey auf AEM as a Cloud Service unterstützen. Weitere Informationen finden Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=de).

>[!NOTE]
>
> Sehen Sie sich dieses Demovideo zu [Cloud Acceleration Manager &#x200B;](https://video.tv.adobe.com/v/335547).
