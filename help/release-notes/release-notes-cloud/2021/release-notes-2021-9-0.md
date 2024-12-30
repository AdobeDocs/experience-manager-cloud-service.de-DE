---
title: Versionshinweise für Version 2021.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 8c12ff09-fbc8-42dd-87c0-46e509604f36
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 63%

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

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2021.9.0) war der 6. Oktober 2021.
Die folgende Version (2021.10.0) wurde am 4. November 2021 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht September 2021](https://video.tv.adobe.com/v/337381) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion im Kanal für die Vorabversion von [!DNL Sites] {#sites-prerelease-features}

* Inhaltsfragmentmodelle werden jetzt, sobald sie veröffentlicht werden, automatisch in einen schreibgeschützten Status versetzt, um zu vermeiden, dass Live-API-Abfragen nach der erneuten Veröffentlichung eines bearbeiteten Modells unbeabsichtigt beschädigt werden. Benutzern wird beim Versuch, ein veröffentlichtes Modell zu bearbeiten, eine Warnung angezeigt. Die Bearbeitung ist möglich, sobald die Warnung akzeptiert wurde.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Benutzer können jetzt die in den Suchergebnissen angezeigten Assets in Spalten- und Kartenansichten sortieren. Die Sortierung funktioniert bei den Spalten „Name“, „Erstellt“, „Geändert“ oder „Keine“.

  ![Sortieren der Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten](/help/assets/assets/sort-searched-assets.png)
  *Abbildung: Sortieren Sie die Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten.*

* Um die Verarbeitung mithilfe von Asset-Microservices programmgesteuert aufzurufen, wird eine neue API eingeführt. Entwickler können jetzt ein vorhandenes Verarbeitungsprofil auf Ordnerebene auf ein oder mehrere bestimmte Assets in einem Ordner anwenden. Das Verarbeitungsprofil wird basierend auf Aktualisierungen der benutzerdefinierten Metadateneigenschaften angewendet. Siehe `AssetProcessor` in der [[!DNL Experience Manager] API-Referenz](https://developer.adobe.com/experience-manager/reference-materials/). Wie zuvor ist es möglich, [Asset-Microservices über die Benutzeroberfläche zu verwenden](/help/assets/asset-microservices-configure-and-use.md).

<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep beta channel.
A/V transcription feature by way of CQ-4303854 has moved to Oct beta now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms-sep-2021}

* **Verwenden von Adobe Sign-Rollen in einem adaptiven Formular** - Mit Adobe Sign für Business- und Enterprise Service-Levels können Sie optional die Rollen für Empfangende von Vereinbarungen über den Unterzeichnenden hinaus erweitern, um deren Workflow-Anforderungen besser zu erfüllen. Sie können jetzt [jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular zu konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform) wobei Signer die Standardrolle ist.

* **Analytics für Adaptive Forms** - Sie können jetzt das Endbenutzerverhalten mit Adobe Analytics for Adaptive Forms erfassen und verfolgen, um Erkenntnisse über Endbenutzern zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Endbenutzererlebnis zu verbessern.

* **Einfaches Verbinden von Adobe Experience Manager (AEM) Forms mit Microsoft® Dynamics und Salesforce** - Der Service bietet eine sofort einsatzbereite Datenquellenkonfiguration und Datenmodelle für Microsoft® Dynamics und Salesforce. Dadurch können [schneller und einfacher Microsoft® Dynamics und Salesforce als Datenquellen für adaptive Formulare konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics-salesforce.html).

* **E-Signieren eines adaptiven Formulars mit DocuSign** - Sie können DocuSign verwenden, um ein adaptives Formular elektronisch zu unterzeichnen. Der Service bietet eine benutzerdefinierte Übermittlungsaktion zur Verwendung von DocuSign bei einem adaptiven Formular. Sie können das im Bereich Software-Verteilung verfügbare Package installieren, um die Übermittlungsaktion zu importieren.

### Beta-Funktionen von [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Unified Storage Connector** - Verwenden Sie Unified Storage Connector, um prozessinterne Daten in vom Kunden verwalteten Repositorys zu externalisieren. Sie können beispielsweise 
   * die Speicher- und Wiederaufnahmefunktion des Formularportals aktivieren und adaptive Formularentwürfe in einem kundenverwalteten Daten-Repository speichern.
   * prozessinterne AEM-Workflow-Daten (AEM-Workflow-Variablendaten), die sensible personenbezogene Daten (SPD) beinhalten, in einem vom Kunden verwalteten Repository speichern.

* **[!DNL AEM Forms as a Cloud Service - Communications]** - [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) helfen Ihnen, XDP-Vorlagen und XML-Daten zu kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:
   * Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   * Erzeugen Sie Ausgabeformulare in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckdatenströme.
   * Erzeugen von PDF-Druckdateien aus einem XFA-Formular-PDF und aus einem Adobe Acrobat-Formular.

Sie können sich an [!DNL formscsbeta@adobe.com] wenden, um sich für das Beta-Programm anzumelden.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Die neue Registerkarte „Zugehörige Commerce-Inhalte“ im AEM Sites-Editor erhöht die Autoreneffizienz, indem schnell auf relevante AEM-Produktinhalte für den aktuellen Kontext zugegriffen werden kann

  ![Zugehörige Commerce-Inhalte](/help/assets/CIF/associated-commerce-content.png)

* Verbesserte Benutzeroberfläche zur Produktauswahl für ein besseres Benutzererlebnis, höhere Effizienz und Unterstützung bei einem komplexen Produktkatalog

  ![Neue Produktauswahl](/help/assets/CIF/product-picker.png)

* Berücksichtigung der Eigenschaft „include_in_menu“ in der Navigationskomponente

### Fehlerbehebungen {#bug-fixes-cif}

* Das Leeren des Menücache funktioniert jetzt erwartungsgemäß

* JS-Fehler während des AEM CS-Bereitstellungsschritts und bei Nichtverwendung Client-seitiger Komponenten

* CIF-Cloud-Konfiguration kann jetzt auch in Ordnern erstellt werden, die einen sling:configs-Knoten haben

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### Neue Funktionen {#what-is-new-screens}

* Screens as a Cloud Service unterstützt jetzt eine einfache Wiedergabe-Überwachung. Der Player meldet jetzt bei jedem Ping (standardmäßig alle 30 Sekunden) verschiedene Wiedergabemetriken. Basierend auf den Metriken können verschiedene Randfälle erkannt werden (steckengebliebenes Erlebnis, leerer Bildschirm, Zeitplanprobleme usw.). Mit dieser Funktion kann das Team aus der Ferne überwachen, ob ein Player die Inhalte ordnungsgemäß wiedergibt. Dadurch wird die Reaktionsfähigkeit auf leere Bildschirme oder fehlerhafte Erlebnisse im Feld verbessert und das Risiko verringert, dem Benutzer ein fehlerhaftes Erlebnis anzuzeigen.
Weitere Informationen finden Sie unter [Einfache Wiedergabe-Überwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html#playback-monitoring).

* Unterstützung von Miniaturansichten für Videos in wird in Screens as a Cloud Service jetzt unterstützt. Inhaltsautorinnen und -autoren können eine Miniaturansicht für Videos definieren, sodass das Bild als Platzhalter verwendet und die Inhaltswiedergabe und das Targeting ordnungsgemäß getestet werden können, während das eigentliche Video vom entsprechenden Team fertiggestellt wird. Das Bild kann auch verwendet werden, wenn die Wiedergabe des Videos fehlschlägt.
Weitere Informationen finden Sie unter [Unterstützung von Miniaturansichten für Videos](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html).

### Fehlerbehebungen {#bug-fixes-screens}

* Der Player konnte keine Inhalte von der eingebetteten Seite anzeigen. Dieses Problem wurde nun behoben.

* Nach erfolgreicher Anmeldung führte die Navigation zur Standardseite (Kanäle) zu einer internen Server-Fehlerseite.

* Zugehörige Tag-Einträge wurden beim Entfernen von Wiedergabelisten nicht entfernt.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Neue Funktionen in [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Erweiterte Netzwerke**

>[!INFO]
>
>Die Funktion für erweiterte Netzwerke ist Teil der Version 2021.9.0 und wurde Mitte Oktober 2021 für Kunden aktiviert.

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] bietet jetzt mehrere Arten erweiterter Netzwerkfunktionen, darunter:

* Flexibler Port-Ausgang, um Traffic von nicht standardisierten Ports aus zu senden. Dies ist jetzt möglich, ohne sich an den Adobe-Support zu wenden.
* Dedizierte Ausgangs-IP-Adresse, um den Traffic aus AEM as a Cloud Service von einer eindeutigen IP-Adresse aus zu senden, die jetzt alle Ports unterstützt.
* VPN, um den Datenverkehr zwischen Ihrer Infrastruktur und AEM as a Cloud Service zu sichern.

Lesen Sie die [Dokumentation](/help/security/configuring-advanced-networking.md), um weitere Informationen zu erhalten, u. a. wie Sie mithilfe von Cloud Manager-APIs erweiterte Netzwerke selbst bereitstellen können.

**Indexoptimierungen**

Um die Leistung von Suchabfragen und Indizierungen zu verbessern, wird der Volltext-Index lucene-2 ab dieser Version nicht mehr vorkonfiguriert in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] verwendet. Um diesen Volltextindex auf AEM-Umgebungen in Absprache mit AEM-Kunden zu entfernen, arbeitet Adobe Engineering individuell und proaktiv mit Kunden zusammen, um eine schonende und nachhaltige Entfernung des Lucene-Volltextindexes zu erreichen. Besuchen Sie die [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] [Dokumentation](/help/operations/indexing.md#index-optimizations), um weitere Informationen zu erhalten, und wenden Sie sich direkt an den Adobe-Support, wenn Sie Fragen haben.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.9.0 und 2021.8.0.

## Veröffentlichungsdatum {#release-date-cm-sept}

Die Version 2021.9.0 von Cloud Manager in AEM as a Cloud Service wurde am 9. September 2021 veröffentlicht.
Die nächste Version wird am 7. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cm-sept}

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 30 aktualisiert.

* Die Programmkarten auf der Landingpage vom Cloud Manager und das zugehörige Erlebnis wurden aktualisiert.

* Das Protokoll des Schritts „Code-Qualität“ enthält jetzt ausführliche Protokollierungsinformationen zum OakPal-Scan-Prozess.

* Die Menüoptionen der Aktivitätsseite enthalten jetzt eine Option zum **Herunterladen von Protokollen** für abgeschlossene Code-Generator-Durchläufe. Wenn Sie diese auswählen, wird das Protokoll des Build-Schritts heruntergeladen.

* Wenn Sie direkt auf die Programmkarte klicken, navigieren Sie jetzt zur Cloud Manager-Übersichtsseite.

### Fehlerbehebungen {#bug-fixes-sept}

* Benutzern wird jetzt eine verständlichere Meldung angezeigt, wenn sie versuchen, eine IP-Zulassungsliste in ein Programm einzufügen, die die maximal zulässige Anzahl von IP-Zulassungslisten erreicht hat, die konfiguriert werden können.

* Es wurde die falsche URL kopiert, wenn die Menüoption „URL kopieren“ auf dem Bildschirm „Repositorys“ ausgewählt wurde.

## Cloud Acceleration Manager {#cam}

### Veröffentlichungsdatum {#release-date-october-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 4. Oktober 2021.

### Neue Funktionen {#what-is-new-cam}

* Cloud Acceleration Manager bietet den Nutzern jetzt die Möglichkeit, die BPA-Berichte in einer Druckvorschau zu betrachten, so dass sie einfach ausgedruckt oder als PDF gedruckt werden können, um sie leicht weitergeben zu können. Siehe Schritt 6 und 7 in [Verwenden der Karte „Best-Practices-Analyse](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=de#best-practices-analysis).

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.6.0 von Content Transfer Tool wurde am 4. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Verbesserte Benutzerzuordnung mit einem vereinfachten Benutzererlebnis, einschließlich der folgenden unten aufgeführten Funktionen. Weitere Informationen finden Sie unter [Verwenden des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/legacy-user-mapping-tool/using-user-mapping-tool-legacy.html#using-user-mapping-tool).
   * Testen der Verbindung zur User Management-API, bevor die Benutzerzuordnung ausgeführt wird
   * Fehler elegant überspringen und mit der Aktivität Benutzerzuordnung fortfahren
   * Die Benutzerzuordnung schlägt nicht mehr fehl, wenn das Zugriffstoken abläuft (nach 24 Stunden). Die Benutzerzuordnung kann an der Stelle erneut ausgeführt werden, an der sie zuletzt angehalten wurde.

* Um die Stabilität des Content Transfer Tool zu erhöhen, können Inhalte nicht gleichzeitig in die Autoren- oder Veröffentlichungsinstanz aufgenommen werden.

* Wenn Versionen enthalten sind, wird der Pfad `/var/audit` automatisch einbezogen, um Prüfereignisse zu migrieren.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa-latest}

Best Practices Analyzer 2.1.18 wurde am 2. September 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Möglichkeit, die Gesamtknotenanzahl zu erkennen und Berichte dazu zu erstellen.

* Möglichkeit, den Knotenspeichertyp und die Knotenspeichergröße zu erkennen und Berichte dazu zu erstellen.

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA hat fälschlicherweise Commerce integration framework nachgewiesen.
