---
title: Versionshinweise für Version 2021.7.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
description: Versionshinweise für Version 2021.7.0 von  [!DNL Adobe Experience Manager]  as a Cloud Service.
exl-id: 848f6a29-2e0f-4976-8ed7-6b7f69408c1b
source-git-commit: f956b8379b5b93bc00e25f0eec641430c5565e34
workflow-type: tm+mt
source-wordcount: '1319'
ht-degree: 58%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen navigieren, z. B. für die Versionen 2020 und 2021.

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

* Flexiblere Dispatcher-Konfiguration: Projekte können leichter organisiert werden. Beispielsweise können Sie jetzt mehrere Rewrite-Regeldateien einbeziehen, die Ihre Website-Struktur widerspiegeln. [Informationen zu](/help/implementing/dispatcher/disp-overview.md#validation-debug) Dieser flexible Modus, einschließlich der Strukturierung Ihrer Dispatcher-Konfiguration, sodass Sie diese nutzen können.
* Die Benutzeroberfläche für die Strukturreplikation auf der Registerkarte &quot;Verteilen&quot;des Replikationsagenten sollte als veraltet betrachtet werden und wurde nach dem 30. September 2021 entfernt. [Erfahren Sie mehr](/help/operations/replication.md#tree-activation) über alternative Replikationsstrategien.
* Das Bundle `org.apache.sling.datasource-1.0.4.jar` für die Unterstützung der Sling-Datenquelle wurde entfernt, da es veraltete Funktionen aufweist und von Kunden nicht verwendet wird.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Funktionen zur Inhaltsautomatisierung ermöglichen [!DNL Experience Manager Assets] die [!DNL Adobe Creative Cloud] APIs zur Automatisierung der Asset-Produktion im Maßstab. Die Inhaltsgeschwindigkeit wird verbessert, indem die zum Erstellen von Varianten desselben Assets erforderliche Zeit verkürzt und die Anzahl der Iterationen erheblich verringert werden. Die Funktion erfordert keine Programmierung und funktioniert aus dem DAM heraus. Siehe [Erzeugen von Varianten von Assets mithilfe der Creative Cloud-Integration](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] enthält den [!DNL Document Cloud]-PDF-Viewer zur nativen Vorschau von PDF-Dokumenten. Mit dieser Funktion können Benutzer mehrseitige PDF-Dateien ohne Dateiverarbeitung oder Konvertierung in der Vorschau anzeigen. Diese Funktion verbessert die Parität mit [!DNL Experience Manager] 6.5. Die im Viewer verfügbaren Steuerelemente umfassen Zoom, Navigieren zu Seiten, Entfernen von Steuerelementen und Anzeigen im Vollbildmodus. Benutzer können auch eine Vorschau der Seiten und Lesezeichen anzeigen und zu ihnen springen. Kommentare zur Datei selbst werden unterstützt. Kommentare und Anmerkungen zu Inhalten in der PDF-Datei sind für eine zukünftige Version geplant.

  ![PDF-Dateien in [!DNL Experience Manager] in der Vorschau mit dem PDF-Viewer anzeigen](/help/assets/assets/preview-pdf-file-viewer.png)

* Die Downloadfunktion für die Linkfreigabe verwendet asynchrone Downloads, die die Download-Geschwindigkeit erhöhen. Weitere Informationen finden Sie unter [Herunterladen von freigegebenen Assets mithilfe der Linkfreigabe](/help/assets/download-assets-from-aem.md#link-share-download).

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

* Sie können jetzt den Automated forms conversion-Dienst für [Konvertieren von PDF forms in französischer, deutscher und spanischer Sprache](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=de?#language-specific-meta-model) in adaptive Formulare.
* Es wurde ein separates Bedienfeld zum Vorlagen-Editor hinzugefügt, um Fehler im Zusammenhang mit adaptiven Formularkomponenten anzuzeigen. Dies hilft, alle Fehler in adaptiven Formularen an einem Ort zu konsolidieren und die Auflösungszeit zu verkürzen.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) helfen Ihnen, XDP-Vorlagen und XML-Daten zu kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Dienst können Sie Dokumente im synchronen Modus generieren. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:
   * Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   * Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckströme.
   * Erzeugen von PDF-Druckdateien aus einem XFA-Formular-PDF und aus einem Adobe Acrobat-Formular.

* **Variablendaten-Externalizer**: Sie können Daten von AEM-Workflow-Variablen in einem externen Speichersystem speichern, das von Ihrer Organisation verwaltet wird.

* **Acroform-basiertes aufzuzeichnendes Dokument**: Sie können auch [Adobe Acrobat Form PDF (Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=de) als Vorlage für ein aufzuzeichnendes Dokument neben XFA-basierten Formularvorlagen verwenden.

* **Microsoft® Azure-Datenspeicher-Connector**: Sie können jetzt [Formulardatenmodell mit Microsoft® Azure Storage verbinden](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-azure-storage.html). Dadurch können Sie adaptive Formulardaten abrufen und in Microsoft® Azure Storage as a BLOB speichern.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* CIF-Kernkomponenten v2
   * Vereinfachte und verbesserte Konfigurationen für PDP/PLP-URL und SEO
   * Visueller Indikator für gestaffelte Produktdaten im Authoring-Modus für bessere Sichtbarkeit bevorstehender Änderungen
   * Neue Sitemap-Komponente für Inhalte und Commerce-Seiten

* Unterstützung für [Adobe Commerce Sensei Product Recommendation, powered by Adobe Sensei](https://business.adobe.com/de/products/magento/product-recommendations.html) in der AEM-Storefront mit vordefinierten oder direkt erstellten Empfehlungen

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### Fehlerbehebungen {#bug-fixes-screens}

* Die Einstellungen des Content Providers werden jetzt bei der Erstellung oder Aktualisierung validiert.

* Alle Anzeigeansichten verfügen über eine Ordnerspalte.

* Sie können die Screens-Inhaltsstruktur erweitern.

* `bulk-offline-update-service` fehlten für einige Umgebungen alle Berechtigungen.

* Der Hilfe-Link wurde entsprechend der neuen Screens-Cloud-Dokumentation aktualisiert.

* Die Zuweisung von Wiedergabelisten aufheben und das Entfernen von Wiedergabelisten mit zugewiesenen Playern deaktivieren, funktioniert jetzt.

* Der Player lädt Assets jetzt erneut herunter, wenn der Cache &quot;ALL&quot;gelöscht wird.

* Die wiederholte Planung funktioniert jetzt, wenn die Variable *Endzeit* wird für den folgenden Tag festgelegt.

* `Back&Forward` funktioniert jetzt in der Screens as a Cloud Service-Benutzeroberfläche.

* Tags mit demselben Namen, aber unterschiedlichen Namespaces konnten nicht zuvor erstellt werden.

## XML-Dokumentation für Experience Manager as a Cloud Service {#xml-documentation}

### Neue Funktionen {#what-is-new-xml-documentation}

Die XML-Dokumentation für Experience Manager as a Cloud Service ist allgemein verfügbar. Dadurch können Kunden von Experience Managern, die as a Cloud Service sind, ein XML Documentation-Add-on für den Import, die Erstellung, die Verwaltung und die Bereitstellung technischer Inhalte über mehrere Kanäle, einschließlich Experience Manager Sites, zu beziehen.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.7.0.

### Veröffentlichungsdatum {#release-cm-july}

Die Version 2021.7.0 von Cloud Manager in AEM as a Cloud Service wurde am 15. Juli 2021 veröffentlicht.
Die nächste Version wird am 12. August 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cm-july}

* Kunden können jetzt Azul 8- und 11-JDKs für ihre Cloud Manager-Build-Prozesse verwenden und entweder eines dieser JDKs für mit Toolketten kompatible Maven-Plug-ins verwenden *oder* die gesamte Ausführung des Maven-Prozesses.

* Die ausgehende Ausgangs-IP wird jetzt in der Protokolldatei des Buildschritts protokolliert.

* Staging- und Produktionsumgebungen, die alte Versionen von AEM ausführen, melden jetzt den Status von **Verfügbare Aktualisierung**.

* Die maximale Anzahl unterstützter SSL-Zertifikate wurde auf 20 pro Programm erhöht.

* Die maximale Anzahl der Domains, die konfiguriert werden können, wurde auf 500 pro Umgebung erhöht.

* Die **Git verwalten** Schaltfläche wurde eingestellt auf **Git-Informationen aufrufen** und das Dialogfeld visuell aktualisiert wurde.

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 28 aktualisiert.

### Fehlerbehebungen {#bug-fixes-cm-july}

* In einigen Fällen war die Vorschau keine verfügbare Option beim Binden einer IP-Zulassungsliste an eine Umgebung.

* Beim manuellen Navigieren zur Seite mit den Ausführungsdetails für eine nicht vorhandene Ausführung wird nicht mehr ein Bildschirm mit endlosen Ladevorgängen, sondern ein Fehler angezeigt.

* Die Fehlermeldung, die angezeigt wurde, wenn die maximale Anzahl von SSL-Zertifikaten erreicht wurde, war nicht hilfreich.

* Versionsnummern werden auf der Pipeline-Karte auf der Seite **Überblick** jetzt ohne Diskrepanzen angezeigt.

* Der Assistent Programm hinzufügen wurde fälschlicherweise darauf hingewiesen, dass der Name nach der Erstellung nicht mehr geändert werden kann.

### Bekannte Probleme {#known-issues-cm-july}

Kunden, die zur Verwendung der Azul-JDKs wechseln, sollten wissen, dass nicht alle vorhandenen Anwendungen ohne Fehler auf dem Azul-JDK kompiliert werden. Adobe empfiehlt, dass Sie vor dem Umschalten lokal testen.

## Cloud Acceleration Manager {#cam}

### Veröffentlichungsdatum {#release-date-july-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 15. Juli 2021.

### Neue Funktionen {#what-is-new-cam}

Cloud Acceleration Manager ist eine Cloud-basierte Anwendung, die IT-Teams während des gesamten Übergangszeitraums von der Planung bis hin zur Live-Schaltung auf dem Cloud-Service begleitet. Richten Sie Ihr Team für eine erfolgreiche Migration ein, mit Best Practices, Tipps, Dokumentationen und Tools, die von der Adobe empfohlen werden und in jeder Phase des Journey helfen, als Cloud Service AEM zu werden. Weitere Informationen finden Sie [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en).

>[!NOTE]
>
> Sehen Sie sich dies an [Demovideo zu Cloud Acceleration Manager](https://video.tv.adobe.com/v/335547).
