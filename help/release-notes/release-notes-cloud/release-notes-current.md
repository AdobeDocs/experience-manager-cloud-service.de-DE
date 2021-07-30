---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: d977ff765accb650daff4c35f2668489454305cd
workflow-type: tm+mt
source-wordcount: '1313'
ht-degree: 10%

---


# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen navigieren. z. B. für die 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] als [!DNL Cloud Service] aktuelle Version (2021.7.0) ist der 29. Juli 2021.
Die folgende Version (2021.8.0) wurde am 26. August 2021 veröffentlicht.

## Release Video {#release-video}

Sehen Sie sich das Video [Versionsübersicht Juli 2021](https://video.tv.adobe.com/v/335580) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## Experience Manager Foundation als Cloud Service {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Flexiblere Dispatcher-Konfiguration: Projekte können leichter organisiert werden. Beispielsweise können Sie jetzt mehrere Rewrite-Regeldateien einbeziehen, die Ihre Site-Struktur widerspiegeln. [Erfahren Sie ](/help/implementing/dispatcher/disp-overview.md#validation-debug) mehr über diesen flexiblen Modus, einschließlich der Strukturierung Ihrer Dispatcher-Konfiguration, um diese nutzen zu können.
* Die Benutzeroberfläche für die Strukturreplikation auf der Registerkarte &quot;Verteilen&quot;des Replikationsagenten sollte als veraltet betrachtet werden und soll nach dem 30. September entfernt werden. [Erfahren Sie ](/help/operations/replication.md#tree-activation) mehr über alternative Replikationsstrategien.
* Das Paket `org.apache.sling.datasource-1.0.4.jar` für die Unterstützung der Sling-Datenquelle wurde entfernt, da es veraltete Funktionen aufweist und von Kunden nicht verwendet wird.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Mit der Funktion zur Inhaltsautomatisierung kann [!DNL Experience Manager Assets] die [!DNL Adobe Creative Cloud]-APIs nutzen, um die Asset-Produktion skaliert zu automatisieren. Die Geschwindigkeit von Inhalten wird verbessert, indem die zum Erstellen von Varianten desselben Assets erforderliche Zeit und Iterationen erheblich verkürzt werden. Die Funktion erfordert keine Programmierung und funktioniert innerhalb des DAM. Siehe [Generieren von Varianten von Assets mithilfe der Creative Cloud-Integration](/help/assets/cc-api-integration.md).

* [!DNL Experience Manager Assets] enthält den  [!DNL Document Cloud] PDF-Viewer zur nativen Vorschau von PDF-Dokumenten. Mit dieser Funktion können Benutzer mehrseitige PDF-Dateien ohne Dateiverarbeitung oder Konvertierung in der Vorschau anzeigen. Diese Funktion verbessert die Parität mit [!DNL Experience Manager] 6.5. Die im Viewer verfügbaren Steuerelemente umfassen Zoom, Navigieren zu Seiten, Entfernen von Steuerelementen und Anzeigen im Vollbildmodus. Benutzer können die Groß-/Kleinschreibung auch in der Vorschau anzeigen und zu Seiten und Lesezeichen springen. Kommentare zur Datei selbst werden unterstützt und Kommentare und Anmerkungen zum Inhalt in der PDF-Datei werden in einer zukünftigen Version hinzugefügt.

   ![PDF-Dateien in  [!DNL Experience Manager] der Vorschau mit dem PDF-Viewer anzeigen](/help/assets/assets/preview-pdf-file-viewer.png)

* Die Funktion für den Linkshare-Download verwendet asynchrone Downloads, die die Download-Geschwindigkeit erhöhen. Siehe [Herunterladen von freigegebenen Assets mithilfe der Linkfreigabe](/help/assets/download-assets-from-aem.md#link-share-download).

   ![Posteingang herunterladen](/help/assets/assets/download-inbox.png)

* Die Anzeigeeinstellungen wurden verbessert, sodass Benutzer eine Standardansicht und einen standardmäßigen Sortierparameter wählen können.

   ![Festlegen der Standardansicht in den  [!UICONTROL Anzeigeeinstellungen]](/help/assets/assets/view-settings-for-defaults.png)

* Benutzer können die Ordner anhand von Eigenschaftsprädikaten suchen und filtern.

   ![Filtern von Suchordnern mithilfe von Sucheigenschaften](/help/assets/assets/search-folders-via-predicates.png)

### Neue Funktionen im Kanal [!DNL Assets] der Vorabversion {#assets-prerelease-features}

<!-- TBD: Not sure about GA of these enh. Shall check with the team.

* A user experience enhancements displays the number of assets present in a folder. For more than 1000 assets in a folder, [!DNL Assets] displays 1000+.

  ![Number of assets in a folder are displayed on the interface](/help/assets/assets/browse-folder-number-of-assets.png)

* You can directly apply a metadata schemas to a folder in its [!UICONTROL Properties].

  ![Add metadata schema from folder properties](/help/assets/assets/metadata-schema-folder-properties.png)
-->

* Wenn Sie digitale Assets als Link freigeben, können Benutzer die URL in die Zwischenablage kopieren. Dank der Verbesserung können Sie Assets schneller und bequemer freigeben.

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

Die API `com.day.cq.dam.api.collection.SmartCollection` ist in [!DNL Experience Manager] nicht als [!DNL Cloud Service] verfügbar. (CQ-4326322)

## [!DNL Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* Sie können jetzt den Automated forms conversion-Dienst verwenden, um [PDF forms in französischer, deutscher und spanischer Sprache](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) in adaptive Formulare zu konvertieren.
* Es wurde ein separates Bedienfeld zum Vorlagen-Editor hinzugefügt, um Fehler im Zusammenhang mit adaptiven Formularkomponenten anzuzeigen. Dies hilft, alle Fehler in adaptiven Formularen an einem Ort zu konsolidieren und die Auflösungszeit zu verkürzen.

### Neue Funktionen im Kanal für die Vorabversion [!DNL Forms] {#beta-features-forms}

* **[!DNL AEM Forms as a Cloud Service - Communications]**:  [Communication ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html) APIshelp: Kombinieren Sie XDP-Vorlagen und XML-Daten, um Druckdokumente in verschiedenen Formaten zu generieren. Mit dem Dienst können Sie Dokumente im synchronen Modus generieren. Mit den APIs können Sie Anwendungen erstellen, mit denen Sie:
   * Generieren Sie Dokumente, indem Sie Vorlagendateien mit XML-Daten füllen.
   * Generieren Sie Ausgabeformulare in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckströme.
   * Generieren Sie PDF-Druckdateien aus einem XFA-Formular als PDF und Adobe Acrobat-Formular.

* **Variablendaten-Externalizer**: Sie können Daten vom AEM-Workflow-Variablen in einem externen Speichersystem speichern, das von Ihrem Unternehmen verwaltet wird.

* **Acroform-based Document of Record**: Sie können auch Adobe Acrobat Form PDF (Acroform PDF) [ ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html)  als Vorlage für Datensatzdokument neben XFA-basierten Formularvorlagen verwenden.

* **Microsoft Azure-Datenspeicher-Connector**: Sie können jetzt das Formulardatenmodell mit dem Microsoft Azure-Speicher  [verbinden](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html). Dadurch können Sie adaptive Formulardaten abrufen und in Microsoft Azure Storage als BLOB speichern.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* CIF-Kernkomponenten v2
   * Vereinfachte und verbesserte Konfigurationen für PDP/PLP-URL und SEO
   * Visueller Indikator für gestaffelte Produktdaten im Authoring-Modus für bessere Sichtbarkeit bevorstehender Änderungen
   * Neue Sitemap-Komponente für Inhalte und Commerce-Seiten

* Unterstützung für [Adobe Commerce Sensei Product Recommendation, powered by Adobe Sensei](https://business.adobe.com/products/magento/product-recommendations.html) in AEM Storefront mit vordefinierten oder direkt erstellten Empfehlungen

## [!DNL Experience Manager Screens] as a  [!DNL Cloud Service] {#screens}

### Fehlerbehebungen {#bug-fixes-screens}

* Die Einstellungen des Content Providers werden jetzt bei der Erstellung oder Aktualisierung validiert.

* Alle Ansichten verfügen über eine Ordnerspalte.

* Sie können die Screens-Inhaltsstruktur erweitern.

* `bulk-offline-update-service` fehlte bei einigen Umgebungen alle Berechtigungen.

* Der Hilfe-Link wurde entsprechend der neuen Screens-Cloud-Dokumentation aktualisiert.

* Die Zuweisung von Wiedergabelisten aufheben und das Entfernen von Wiedergabelisten mit zugewiesenen Playern deaktivieren, funktioniert jetzt.

* Der Player lädt Assets jetzt erneut herunter, wenn der Cache &quot;ALL&quot;gelöscht wird.

* Die Wiederholungszeitplanung funktioniert jetzt, wenn die *Endzeit* für den folgenden Tag festgelegt ist.

* `Back&Forward` funktioniert jetzt in Screens als Cloud Service-Benutzeroberfläche.

* Tags mit demselben Namen, aber unterschiedlichen Namespaces konnten nicht früher erstellt werden.

## XML-Dokumentation für Experience Manager as a Cloud Service {#xml-documentation}

### Neue Funktionen {#what-is-new-xml-documentation}

Die XML-Dokumentation für Experience Manager as a Cloud Service ist allgemein verfügbar. Dadurch können Experience Manager als Cloud Service XML-Dokumentationsdaten abrufen, um technische Inhalte über verschiedene Kanäle, einschließlich Experience Manager-Sites, zu importieren, zu erstellen, zu verwalten und bereitzustellen.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.7.0.

### Veröffentlichungsdatum {#release-cm-july}

Die Version 2021.7.0 von Cloud Manager in AEM as a Cloud Service wurde am 15. Juli 2021 veröffentlicht.
Die nächste Version ist für den 12. August 2021 geplant.

### Neue Funktionen {#what-is-new-cm-july}

* Kunden können jetzt Azul 8- und 11-JDKs für ihre Cloud Manager-Build-Prozesse verwenden und entweder festlegen, eines dieser JDKs für toolchain-kompatible Maven-Plug-ins *oder* für die gesamte Maven-Prozessausführung zu verwenden.

* Die ausgehende Ausgangs-IP wird jetzt in der Protokolldatei des Buildschritts protokolliert.

* Staging- und Produktionsumgebungen, die alte Versionen von AEM ausführen, melden jetzt den Status **Update Verfügbar**.

* Die maximal unterstützten SSL-Zertifikate wurden auf 20 pro Programm erhöht.

* Die maximale Anzahl der Domänen, die konfiguriert werden können, wurde auf 500 pro Umgebung erhöht.

* Die Schaltflächen **Git** verwalten wurden in **Git Info** öffnen umbenannt und das Dialogfeld wurde visuell aktualisiert.

* Die Version des AEM Projektarchetyps, der von Cloud Manager verwendet wird, wurde auf Version 28 aktualisiert.

### Fehlerbehebungen {#bug-fixes-cm-july}

* In einigen Fällen war die Vorschau beim Binden einer IP-Zulassungsliste an eine Umgebung keine verfügbare Option.

* Beim manuellen Navigieren zur Seite mit den Ausführungsdetails für eine nicht vorhandene Ausführung wurde kein Fehler angezeigt, sondern nur ein Bildschirm mit endlosen Ladevorgängen.

* Die Fehlermeldung, die angezeigt wird, wenn die maximale Anzahl von SSL-Zertifikaten erreicht wurde, war nicht hilfreich.

* Unter bestimmten Umständen kann es zu einer Diskrepanz in der Release-Version kommen, die auf der Pipeline-Karte auf der Seite **Übersicht** angezeigt wird.

* Der Assistent Programm hinzufügen hat fälschlicherweise angegeben, dass der Name nach der Erstellung nicht mehr geändert werden kann.

### Bekannte Probleme {#known-issues-cm-july}

Kunden, die zur Verwendung der Azul JDKs wechseln, sollten beachten, dass nicht alle vorhandenen Anwendungen ohne Fehler auf Azul JDK kompiliert werden. Es wird dringend empfohlen, vor dem Wechsel lokal zu testen.

## Cloud Acceleration Manager {#cam}

### Veröffentlichungsdatum {#release-date-july-cam}

Die Cloud Acceleration Manager-Version wurde am 15. Juli 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cam}

Cloud Acceleration Manager ist eine Cloud-basierte Anwendung, die IT-Teams während des gesamten Journey-Übergangszeitraums von der Planung bis hin zur Live-Schaltung auf dem Cloud Service begleitet. Richten Sie Ihre Teams für eine erfolgreiche Migration ein, indem Sie von der Adobe empfohlene Best Practices, Tipps, Dokumentationen und Tools einsetzen, um in jeder Phase des Journey zu helfen, als Cloud Service AEM zu werden. Weitere Informationen zu [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/getting-started-cam.html?lang=en).

>[!NOTE]
>
> Sehen Sie sich dieses [Demovideo zum Cloud Acceleration Manager](https://video.tv.adobe.com/v/335547) an.
