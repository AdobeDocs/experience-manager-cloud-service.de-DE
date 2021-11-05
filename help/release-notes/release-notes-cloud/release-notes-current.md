---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: e911abd75cf44d2188e936e9143a48cb88236865
workflow-type: tm+mt
source-wordcount: '1436'
ht-degree: 14%

---


# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] Die aktuelle Version (2021.10.0) ist der 4. November 2021.
Die folgende Version (2021.11.0) wurde am 2. Dezember 2021 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich die [Übersicht über die Version Oktober 2021](https://video.tv.adobe.com/v/338253) Video mit einer Zusammenfassung der hinzugefügten Funktionen.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in [!DNL Sites] {#sites-features}

* Inhaltsfragmentmodelle werden jetzt nach ihrer Veröffentlichung automatisch im schreibgeschützten Status festgelegt, um unbeabsichtigte Umbrüche von Live-API-Abfragen nach der erneuten Veröffentlichung eines bearbeiteten Modells zu vermeiden. Benutzern wird beim Versuch, ein veröffentlichtes Modell zu bearbeiten, eine Warnung angezeigt. Die Bearbeitung ist möglich, sobald die Warnung akzeptiert wurde.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* [!DNL Experience Manager] unterstützt jetzt die automatische Generierung von Texttranskripten aus den unterstützten Audio- und Video-Assets mithilfe eines integrierten Connectors zu [!DNL Azure Media Services]. Die [unterstützte Dateitypen](/help/assets/file-format-support.md#audio-video-transcription-formats) werden automatisch transkribiert und der Text wird im WebVTT-Format gespeichert. Die WebVTT-Untertitel werden für eine effektivere Suche, Untertitelung oder Übersetzung verwendet. Außerdem verbessert die Funktion die Barrierefreiheit, Erkennung und Lokalisierung der Assets.

### Neue Funktion im [!DNL Assets] Vorabversionskanal {#assets-prerelease-features}

* [!DNL Dynamic Media] Image Smart Crop and Swatch basiert jetzt auf den neuesten Sensei-Diensten, die verbesserte Zuschnitte und Farb-/Bildmuster generieren. Außerdem wurde eine Erweiterung gestartet, um unterschiedliche Zuschnittinhalte zu generieren, für das gleiche Seitenverhältnis aber über verschiedene Auflösungen hinweg. Darüber hinaus bleiben manuelle Bearbeitungen bei der Neuverarbeitung erhalten, wenn sich die Breite und Höhe des Bildprofils nicht ändern.

* Smart-Tags werden automatisch über Asset-Microservices auf die Assets angewendet, anstatt über Smart Content Services. Das zugrunde liegende Modell wird aktualisiert, um die Tagging-Ergebnisse zu verbessern und Verzerrungen zu reduzieren. <!-- As it uses asset microservices, it is now possible to develop custom workers using Stock10-based Smart Tags. -->

<!-- Leave this commented.
### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Oct release. Details in CQDOC-18404.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms-oct-2021}

* **Analytics für adaptive Forms**: Sie können jetzt das Verhalten sowohl der angemeldeten als auch der nicht angemeldeten (anonymen) Benutzer über Adobe Analytics für Adaptive Forms erfassen und verfolgen, um Einblicke von Endbenutzern zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Erlebnis der Endbenutzer zu verbessern.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#prerelease-features-forms-oct-2021}

* **Externalisieren AEM Workflow-Daten für eine sichere Verarbeitung**: Sie können in einem kundenverwalteten Repository AEM Daten von Workflows (AEM Workflow-Variablen-Daten) speichern, die sensible personenbezogene Daten (EPPD) enthalten, um sie sicher zu verarbeiten. Die Datenelemente und Workflow-Variablen werden nicht im AEM Repository gespeichert und bei der Verarbeitung des Workflows bei Bedarf aus einem kundenverwalteten Repository abgerufen.

### Beta-Funktionen von [!DNL Forms] {#what-is-new-forms-oct2021-beta}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) hilft Ihnen, eine Vorlage und XML-Daten zu kombinieren, um Druckdokumente in verschiedenen Formaten zu generieren. Mit dem Dienst können Sie Dokumente im synchronen Modus und im Batch-Modus generieren. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:

   * Generieren Sie Dokumente, indem Sie Vorlagendateien (PDF und XDP) mit XML-Daten ausfüllen.
   * Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckströme.

Sie können an [!DNL formscsbeta@adobe.com] schreiben, um sich für das Betaprogramm anzumelden.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Das CIF-Add-on unterstützt die neueste Commerce-Version 2.4.3 mit neuen GraphQL-APIs und -Schemata

* Autoren können mithilfe des Rich-Text-Editors (RTE) Links zu Produkt- und Katalogseiten in Textfeldern hinzufügen. Der RTE-Symbolleiste wurde ein CIF-Symbol hinzugefügt, über das die Auswahl geöffnet wird, um das Produkt oder die Kategorie schnell zu suchen und auszuwählen, ohne den Kontext zu verlassen.

* Bestehende Popup-Warenkorb- und Kassenvorgänge wurden durch spezielle AEM Warenkorb- und Checkout-Seiten ersetzt. Die Komponenten auf diesen Seiten werden mithilfe der erweiterbaren Peregrine-Komponenten von Magento erstellt

* Händler können bestimmte Produktkatalogkategorien in der Navigation mithilfe des Commerce-Backend ausblenden. Die CIF-Navigations-Kernkomponente respektiert die Commerce-Backend-Konfiguration &quot;Einbeziehen in Menü&quot;, um Kategorien in der Navigation ein-/auszublenden

* AEM Storefront Venia gibt den HTTP 404-Fehler zurück, wenn keine Kategorie- oder Produktseite gefunden wird

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0.

### Veröffentlichungsdatum {#release-date-cm-nov}

Die Version 2021.11.0 von Cloud Manager in AEM as a Cloud Service wurde am 04. November 2021 veröffentlicht.
Die nächste Version ist für den 9. Dezember 2021 geplant.

### Neue Funktionen {#what-is-new-cm-nov}

* Benutzer können jetzt neue Front-End-Pipelines nutzen, um Frontend-Code exklusiv schneller bereitzustellen. Siehe [Cloud Manager-Frontend-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) , um mehr zu erfahren.

   >[!IMPORTANT]
   >Sie müssen AEM Version verwenden `2021.10.5933.20211012T154732Z` , um neue Front-End-Pipelines zu nutzen.

* Die Dauer der Code-Qualitäts-Pipeline wird erheblich reduziert, indem die Codeanalyse effizienter durchgeführt wird, ohne dass ein ganzes AEM Bild erstellt werden muss. Diese Änderung wird in den Wochen nach der Veröffentlichung schrittweise eingeführt.

* Die Git-Zusage-ID wird jetzt in den Details zur Pipeline-Ausführung angezeigt, was die Verfolgung des erstellten Codes erleichtert.

* Die Erstellung von Programmen ist jetzt über öffentlich zugängliche APIs verfügbar.

* Die Erstellung von Umgebungen ist jetzt über öffentlich zugängliche APIs verfügbar.

* Die `x-request-id` Die Antwort-Kopfzeile ist jetzt in der API-Wiedergabe auf [www.adobe.io](https://www.adobe.io/). Diese Kopfzeile ist beim Senden von Problemen bei der Kundenunterstützung zur Fehlerbehebung nützlich.

* Als Benutzer sehe ich die Pipeline-Karte mit Null-Pipelines, die mir eine entsprechende Anleitung bietet.

* Eine neue Aktivitätsseite ist jetzt verfügbar, auf der Aktivitäten wie Pipeline- und Codeausführungen zusammen mit den zugehörigen Details angezeigt werden können. Im Laufe der Zeit werden die auf dieser Seite aufgelisteten Aktivitäten zusammen mit den angegebenen Details erweitert.

* Eine neue Pipelines-Seite mit einem On-Hover-Status-Popup für einen einfachen Überblick über die Zusammenfassung der Details ist jetzt verfügbar. Pipeline-Ausführungen können zusammen mit den zugehörigen Details angezeigt werden.

* Die API &quot;Pipeline bearbeiten&quot;unterstützt jetzt das Ändern der in den Bereitstellungsphasen verwendeten Umgebung.

* Für große Packages wurde eine Optimierung des OakPal-Scanprozesses eingeführt.

* Die CSV-Datei mit dem Qualitätsproblem enthält jetzt den Zeitstempel für jedes Qualitätsproblem.

### Fehlerbehebungen {#bug-fixes-nov}

* Bestimmte unorthodoxe Build-Konfigurationen führten dazu, dass unnötige Dateien im Maven-Artefakt-Cache der Pipeline gespeichert wurden, was beim Starten und Beenden des Build-Containers zu irrelevanten Netzwerk-I/O führte.

* Die Pipeline-PATCH-API schlägt fehl, wenn die Bereitstellungsphase nicht vorhanden ist.

* Die `ClientlibProxyResourceCheck` Qualitätsregel verursachte falsch positive Probleme, wenn es Client-Bibliotheken mit gemeinsamen Basispfaden gab.

* Die Fehlermeldung, wenn die maximale Anzahl von Repositorys erreicht wurde, hat den Grund für den Fehler nicht angegeben.

* In seltenen Fällen schlugen Pipelines aufgrund einer unangemessenen Wiederholungsverarbeitung bestimmter Antwort-Codes fehl.


## Veröffentlichungsdatum {#release-date-cm-oct}

Die Cloud Manager-Version AEM as a Cloud Service Version 2021.10.0 wurde am 14. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cm-oct}

* In Vorbereitung auf einige bevorstehende Änderungen werden bestehende Implementierungs-Pipelines nun in der Benutzeroberfläche als **Voller Stapel** Pipelines.

* Die Pipeline-Karte wurde aktualisiert und zeigt jetzt ein einziges, integriertes Gesicht, das sowohl Produktions- als auch Nicht-Produktions-Pipelines anzeigt, und der Benutzer kann Ausführen/Aussetzen/Fortsetzen direkt aus dem Aktionsmenü auswählen, das mit jeder Pipeline verknüpft ist.

* Ein Benutzer mit der Rolle &quot;Bereitstellungsmanager&quot;kann nun die Produktions-Pipeline über die Benutzeroberfläche auf Self-Service-Weise löschen.

* Das Hinzufügen und Bearbeiten von Pipeline-Erlebnissen wurde aktualisiert und verwendet jetzt vertraute, moderne Modale.

* Benutzer von Cloud Manager können jetzt Feedback direkt über die Benutzeroberfläche über die **Feedback** rechts oben auf der Landingpage.

* Jährliche SLA-Diagramme können jetzt von der Benutzeroberfläche von Cloud Manager heruntergeladen werden.

* Code-Qualitäts- und Nicht-Produktions-Pipeline-Ausführungen verwenden jetzt während des Build-Schritts einen effizienteren Prozess zum Klonen von flachen Elementen, was zu einer schnelleren Build-Zeit für Kunden mit besonders großen Git-Repositorys führt.

* Der Assistent IP-Zulassungsliste hinzufügen informiert den Benutzer jetzt darüber, ob die maximal zulässige Anzahl von IP-Zulassungslisten erreicht wurde.

* Die Dokumentation zur Cloud Manager-API enthält jetzt einen interaktiven Spielplatz, auf dem angemeldete Benutzer über ihren Browser mit der API experimentieren können. Siehe [Cloud Manager-API-Wiedergabe](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/) für weitere Details.

* Die QuickInfo auf der Programmkarte ist beschreibender, wenn eine Auswahloption unter &quot;Navigieren zu&quot;deaktiviert ist. Jetzt wird &quot;Es gibt keine Produktionsumgebung mehr&quot; angezeigt.

### Fehlerbehebungen {#bug-fixes-cm-oct}

* In seltenen Fällen, in denen Mitarbeiter der Adobe die Umgebung eines Kunden wiederherstellen, wurde die Wiederherstellung als abgeschlossen angesehen, bevor die Umgebung voll funktionsfähig war.

* Bestimmte interne Anforderungen, die während der Erstellung der Umgebung gestellt wurden, wurden nicht erneut versucht.

* Wenn nach der Verifizierung des Domain-Namens ein Fehler bei der Bereitstellung auftritt, wurde die Fehlermeldung korrigiert, um den Kunden aufzufordern, sich an seinen Kundenbetreuer zu wenden.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa-latest}

Die Version 2.1.20 von Best Practices Analyzer wurde am 5. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Möglichkeit, die Länge von Knotennamen zu erkennen und darüber zu berichten.

* Möglichkeit, die Gesamtgröße des Index zu erkennen und darüber zu berichten.

* Möglichkeit zur Erkennung und Berichterstellung von Assets, denen die ursprüngliche Ausgabedarstellung fehlt.
