---
title: Versionshinweise für Version 2021.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: ab584923-5f06-4b54-941b-e00bc1158b81
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1439'
ht-degree: 69%

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

### Neue Funktion im [!DNL Assets]-Vorabversionskanal {#assets-prerelease-features}

* [!DNL Dynamic Media] Image Smart Crop and Swatch basiert jetzt auf den neuesten Sensei-Diensten, die verbesserte Zuschnitte und Farb-/Bildmuster generieren. Außerdem wurde eine Erweiterung gestartet, um unterschiedliche Zuschnittinhalte zu generieren, für das gleiche Seitenverhältnis aber über verschiedene Auflösungen hinweg. Darüber hinaus bleiben manuelle Bearbeitungen bei der Neuverarbeitung erhalten, wenn sich die Breite und Höhe des Bildprofils nicht ändern.

* Smart-Tags werden automatisch über Asset-Microservices auf die Assets angewendet, anstatt über Smart Content Services. Das zugrunde liegende Modell wird aktualisiert, um die Tagging-Ergebnisse zu verbessern und Verzerrungen zu reduzieren. <!-- As it uses asset microservices, it is now possible to develop custom workers using Stock10-based Smart Tags. -->

<!-- Leave this commented.
### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Oct release. Details in CQDOC-18404.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms-oct-2021}

* **Analytics für adaptive Formulare**: Sie können jetzt das Verhalten sowohl angemeldeter als auch nicht angemeldeter (anonymer) Benutzer über Adobe Analytics für adaptive Formulare erfassen und verfolgen, um Erkenntnisse über Endbenutzern zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Erlebnis der Endbenutzer zu verbessern.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#prerelease-features-forms-oct-2021}

* **Externalisieren von AEM-Workflow-Daten für eine sichere Verarbeitung**: Sie können prozessinterne AEM-Workflow-Daten (AEM-Workflow-Variablendaten), die sensible personenbezogene Daten (SPD) beinhalten, zur sicheren Verarbeitung in einem vom Kunden verwalteten Repository speichern. Die Datenelemente und Workflow-Variablen werden nicht im AEM-Repository gespeichert, sondern bei der Verarbeitung des Workflows bei Bedarf aus dem vom Kunden verwalteten Repository abgerufen.

### Beta-Funktionen von [!DNL Forms] {#what-is-new-forms-oct2021-beta}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/using-communications/aem-forms-cloud-service-communications.html) helfen Ihnen, eine Vorlage und XML-Daten zu kombinieren, um Print-Dokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus und im Batch-Modus generieren. Dabei können Sie mit den APIs Programme mit folgenden Funktionen erstellen:

   * Erzeugen von Dokumenten durch Ausfüllen von Vorlagendateien (PDF und XDP) mit XML-Daten.
   * Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Print-Datenströme.

Sie können sich an [!DNL formscsbeta@adobe.com] wenden, um sich für das Beta-Programm anzumelden.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Das CIF-Add-on unterstützt die neueste Commerce-Version 2.4.3 mit neuen GraphQL-APIs und -Schemata

* Autoren können mithilfe des Rich-Text-Editors (RTE) Links zu Produkt- und Katalogseiten in Textfeldern hinzufügen. Der RTE-Symbolleiste wurde ein CIF-Symbol hinzugefügt, über das die Auswahl geöffnet wird, um das Produkt oder die Kategorie schnell zu suchen und auszuwählen, ohne den Kontext zu verlassen.

* Bestehende Popup-Warenkorb- und Kassenvorgänge wurden durch spezielle AEM Warenkorb- und Checkout-Seiten ersetzt. Die Komponenten auf diesen Seiten werden mithilfe der erweiterbaren Peregrenzen-Komponenten von Adobe Commerce erstellt

* Händler können bestimmte Produktkatalogkategorien in der Navigation mithilfe des Commerce-Backend ausblenden. Die CIF-Navigations-Kernkomponente respektiert die Commerce-Backend-Konfiguration &quot;Einbeziehen in Menü&quot;, um Kategorien in der Navigation ein-/auszublenden

* AEM Storefront Venia gibt den HTTP 404-Fehler zurück, wenn keine Kategorie- oder Produktseite gefunden wird

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0.

### Veröffentlichungsdatum {#release-date-cm-nov}

Die Version 2021.11.0 von Cloud Manager in AEM as a Cloud Service wurde am 04. November 2021 veröffentlicht.
Die nächste Version soll am 09. Dezember 2021 veröffentlicht werden.

### Neue Funktionen {#what-is-new-cm-nov}

* Benutzer können jetzt neue Front-End-Pipelines nutzen, um Frontend-Code exklusiv schneller bereitzustellen. Siehe [Cloud Manager-Frontend-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#front-end) , um mehr zu erfahren.

   >[!IMPORTANT]
   >Sie müssen AEM Version verwenden `2021.10.5933.20211012T154732Z` , um neue Front-End-Pipelines zu nutzen.

* Die Dauer der Code-Qualitäts-Pipeline wird erheblich reduziert, indem die Codeanalyse effizienter durchgeführt wird, ohne dass ein ganzes AEM Bild erstellt werden muss. Diese Änderung wird in den Wochen nach der Veröffentlichung schrittweise eingeführt.

* Die Git-Commit-ID wird jetzt in den Details zur Pipeline-Ausführung angezeigt, was die Verfolgung des erstellten Codes erleichtert.

* Die Erstellung von Programmen ist jetzt über öffentlich zugängliche APIs verfügbar.

* Die Erstellung von Umgebungen ist jetzt über öffentlich zugängliche APIs verfügbar.

* Der Antwort-Header `x-request-id` ist jetzt im API Playground auf [www.adobe.io](https://www.adobe.io/) sichtbar. Dieser Header ist beim Senden von Problemen an die Kundenunterstützung zur Fehlerbehebung nützlich.

* Als Benutzer sehe ich die Pipeline-Karte mit null Pipelines, die mir eine entsprechende Anleitung bieten.

* Auf einer neuen Aktivitätsseite können jetzt Aktivitäten wie Pipeline- und Code-Ausführungen zusammen mit den zugehörigen Details angezeigt werden. Im Laufe der Zeit werden auf dieser Seite immer mehr Aktivitäten und Details aufgelistet.

* Die neue Pipelines-Seite enthält ein Status-Popover, in dem eine Zusammenfassung der Details eingeblendet wird, sobald der Mauszeiger über eine Aktivität bewegt wird. Pipeline-Ausführungen können zusammen mit den zugehörigen Details angezeigt werden.

* Außerdem unterstützt sie jetzt das Ändern der in den Bereitstellungsphasen verwendeten Umgebung.

* Für große Pakete wurde eine Optimierung des OakPal-Scan-Prozesses eingeführt.

* Die CSV-Datei mit Qualitätsproblemen enthält jetzt für jedes Qualitätsproblem einen Zeitstempel.

### Fehlerbehebungen {#bug-fixes-nov}

* Bestimmte unorthodoxe Build-Konfigurationen führten dazu, dass unnötige Dateien im Maven-Artefakt-Cache der Pipeline gespeichert wurden, was beim Starten und Beenden des Build-Containers zu überflüssigem Netzwerk-I/O führte.

* Die Pipeline-PATCH-API schlägt fehl, wenn keine Bereitstellungsphase vorhanden ist.

* Die Qualitätsregel `ClientlibProxyResourceCheck` meldete falsch positive Probleme, wenn Client-Bibliotheken mit gemeinsamen Basispfaden vorhanden waren.

* In der Fehlermeldung beim Erreichen der maximalen Anzahl von Repositorys war kein Grund für den Fehler angegeben.

* In seltenen Fällen schlugen Pipelines aufgrund einer unangemessenen Wiederholungsverarbeitung bestimmter Antwort-Codes fehl.


## Veröffentlichungsdatum {#release-date-cm-oct}

Die Version 2021.10.0 von Cloud Manager in AEM as a Cloud Service wurde am 14. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cm-oct}

* In Vorbereitung auf einige bevorstehende Änderungen werden bestehende Implementierungs-Pipelines nun in der Benutzeroberfläche als **Full Stack**-Pipelines referenziert und benannt.

* Die Pipeline-Karte wurde aktualisiert und zeigt jetzt ein einziges, integriertes Gesicht, das sowohl Produktions-Pipelines als auch produktionsfremde Pipelines anzeigt, und der Benutzer kann Ausführen/Aussetzen/Fortsetzen direkt aus dem Aktionsmenü auswählen, das mit jeder Pipeline verknüpft ist.

* Ein Benutzer mit der Rolle „Implementierungs-Manager“ kann nun die Produktions-Pipeline über die Benutzeroberfläche im Self-Service löschen.

* Das Hinzufügen und Bearbeiten von Pipeline-Erlebnissen wurde aktualisiert und verwendet jetzt vertraute, moderne Modale.

* Benutzer von Cloud Manager können jetzt Feedback direkt über die Benutzeroberfläche über die Schaltfläche **Feedback** rechts oben auf der Landingpage übermitteln.

* Von der Benutzeroberfläche von Cloud Manager können jetzt jährliche SLA-Diagramme heruntergeladen werden.

* Ausführungen von Code-Qualitäts-Pipelines und produktionsfremden Pipelines verwenden jetzt während des Build-Schritts einen effizienteren Prozess zum Klonen von flachen Elementen, was zu einer schnelleren Build-Zeit für Kunden mit besonders großen Git-Repositorys führt.

* Der Assistent „IP-Zulassungsliste hinzufügen“ informiert den Benutzer jetzt darüber, ob die maximal zulässige Anzahl von IP-Zulassungslisten erreicht wurde.

* Die Dokumentation zur Cloud Manager-API enthält jetzt einen interaktiven Spielplatz, auf dem angemeldete Benutzer über ihren Browser mit der API experimentieren können. Weitere Einzelheiten finden Sie unter [Cloud Manager API Playground](https://www.adobe.io/experience-cloud/cloud-manager/reference/playground/).

* Die QuickInfo auf der Programmkarte ist aussagekräftiger, wenn eine Auswahloption unter „Navigieren zu“ deaktiviert ist. Jetzt wird „Es ist keine Produktionsumgebung vorhanden“ angezeigt.

### Fehlerbehebungen {#bug-fixes-cm-oct}

* In den seltenen Fällen, in denen Mitarbeiter von Adobe die Umgebung eines Kunden wiederherstellen, wird jetzt die Wiederherstellung nicht mehr als abgeschlossen angesehen, bevor die Umgebung voll funktionsfähig ist.

* Bestimmte interne Anfragen, die während der Erstellung der Umgebung gestellt wurden, werden jetzt erneut ausgeführt.

* Die Fehlermeldung für den Fall, dass nach der Überprüfung des Domain-Namens ein Fehler bei der Bereitstellung auftritt, wurde dahingehend korrigiert, dass der Kunde aufgefordert wird, sich an seinen Adobe-Support-Mitarbeiter zu wenden.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa-latest}

Best Practices Analyzer 2.1.20 wurde am 5. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Möglichkeit, die Länge von Knotennamen zu erkennen und darüber zu berichten.

* Möglichkeit, die Gesamtgröße des Index zu erkennen und darüber zu berichten.

* Möglichkeit, Assets zu erkennen, denen die ursprüngliche Ausgabedarstellung fehlt und darüber zu berichten.
