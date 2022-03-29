---
title: Versionshinweise für Version 2021.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 8c12ff09-fbc8-42dd-87c0-46e509604f36
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '1572'
ht-degree: 100%

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

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2021.9.0) war der 6. Oktober 2021.
Die folgende Version (2021.10.0) wurde am 4. November 2021 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht September 2021](https://video.tv.adobe.com/v/337381) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion im Kanal für die Vorabversion von [!DNL Sites] {#sites-prerelease-features}

* Inhaltsfragmentmodelle werden jetzt, sobald sie veröffentlicht werden, automatisch in den schreibgeschützten Zustand versetzt, um zu verhindern, dass Live-API-Abfragen nach der erneuten Veröffentlichung eines bearbeiteten Modells ungewollt beeinträchtigt werden. Benutzern wird beim Versuch, ein veröffentlichtes Modell zu bearbeiten, eine Warnung angezeigt. Die Bearbeitung ist möglich, sobald die Warnung akzeptiert wurde.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Benutzer können jetzt die in den Suchergebnissen angezeigten Assets in Spalten- und Kartenansichten sortieren. Die Sortierung funktioniert bei den Spalten „Name“, „Erstellt“, „Geändert“ oder „Keine“.

   ![Sortieren der Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten](/help/assets/assets/sort-searched-assets.png)
   *Abbildung: Sortieren Sie die Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten.*

* Um die Verarbeitung mithilfe von Asset-Microservices programmgesteuert aufzurufen, wird eine neue API eingeführt. Entwickler können jetzt ein vorhandenes Verarbeitungsprofil auf Ordnerebene auf ein oder mehrere bestimmte Assets in einem Ordner anwenden. Das Verarbeitungsprofil wird basierend auf Aktualisierungen der benutzerdefinierten Metadateneigenschaften angewendet. Siehe `AssetProcessor` in der [[!DNL Experience Manager] API-Referenz](https://www.adobe.io/experience-manager/reference-materials/). Wie zuvor ist es möglich, [Asset-Microservices über die Benutzeroberfläche zu verwenden](/help/assets/asset-microservices-configure-and-use.md).

<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep beta channel.
A/V transcription feature via CQ-4303854 has moved to Oct beta now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms-sep-2021}

* **Verwenden von Adobe Sign-Rollen in einem adaptiven Formular**: Die Service-Levels von Adobe Sign für Unternehmen bieten die Möglichkeit, die Rollen von Empfängern von Vereinbarungen über die unterschreibende Person hinaus zu erweitern und so ihren Workflow-Anforderungen besser zu entsprechen. Sie können jetzt [jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular zu konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html?lang=de#addsignerstoanadaptiveform), wobei „Unterschreibende Person“ die Standardrolle ist.

* **Analytics für adaptive Formulare**: Sie können jetzt das Endbenutzerverhalten über Adobe Analytics für adaptive Formulare erfassen und verfolgen, um Erkenntnisse über Endbenutzer zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Erlebnis der Endbenutzer zu verbessern.

* **Einfaches Verbinden von AEM Forms mit Microsoft Dynamics und Salesforce**: Der Service stellt vorkonfigurierte Datenquellenkonfigurationen und Datenmodelle für Microsoft Dynamics und Salesforce bereit, sodass [Entwickler Microsoft Dynamics und Salesforce schneller und einfacher als Datenquellen für adaptive Formulare konfigurieren können](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html?lang=de).

* **E-Signieren eines adaptiven Formulars mit DocuSign:** Sie können DocuSign verwenden, um ein adaptives Formular elektronisch zu unterzeichnen. Der Service bietet eine benutzerdefinierte Übermittlungsaktion zur Verwendung von DocuSign bei einem adaptiven Formular. Sie können das im Bereich Software-Verteilung verfügbare Package installieren, um die Übermittlungsaktion zu importieren.

### Beta-Funktionen von [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Unified Storage Connector:** Verwenden Sie Unified Storage Connector, um prozessinterne Daten in vom Kunden verwalteten Repositorys zu externalisieren. Sie können beispielsweise
   * die Speicher- und Wiederaufnahmefunktion des Formularportals aktivieren und adaptive Formularentwürfe in einem vom Kunden verwalteten Daten-Repository speichern.
   * prozessinterne AEM-Workflow-Daten (AEM-Workflow-Variablendaten), die sensible personenbezogene Daten (SPD) beinhalten, in einem vom Kunden verwalteten Repository speichern.

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=de) helfen Ihnen, XDP-Vorlagen und XML-Daten zu kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:
   * Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   * Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckströme.
   * Erzeugen von PDF-Druckdateien aus einem XFA-Formular-PDF und aus einem Adobe Acrobat-Formular.

Sie können sich an [!DNL formscsbeta@adobe.com] wenden, um sich für das Beta-Programm anzumelden.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Die neue Registerkarte „Zugehörige Commerce-Inhalte“ im Sites-Editor erhöht die Autoreneffizienz, indem schnell auf relevante AEM-Produktinhalte für den aktuellen Kontext zugegriffen werden kann.

   ![Zugehörige Commerce-Inhalte](/help/assets/CIF/associated-commerce-content.png)

* Verbesserte Benutzeroberfläche für die Produktauswahl für ein besseres Benutzererlebnis, höhere Effizienz und Unterstützung für einen komplexen Produktkatalog

   ![Neue Produktauswahl](/help/assets/CIF/product-picker.png)

* Berücksichtigung der Eigenschaft „include_in_menu“ in der Navigationskomponente

### Fehlerbehebungen {#bug-fixes-cif}

* Das Leeren des Menücache funktioniert jetzt erwartungsgemäß

* JS-Fehler während AEM CS-Bereitstellungsschritts und bei Nichtverwendung Client-seitiger Komponenten tritt nicht mehr auf

* CIF-Cloud-Konfiguration kann jetzt auch in Ordnern erstellt werden, die einen sling:configs-Knoten haben

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### Neue Funktionen {#what-is-new-screens}

* Screens as a Cloud Service unterstützt jetzt eine einfache Wiedergabe-Überwachung. Der Player meldet jetzt bei jedem Ping (standardmäßig alle 30 Sekunden) verschiedene Wiedergabemetriken. Basierend auf den Metriken bietet dies die Möglichkeit, verschiedene Grenzfälle zu erkennen (z. B. steckengebliebenes Erlebnis, leerer Bildschirm, Zeitplanprobleme usw.). Diese Funktion ermöglicht es dem Team, aus der Ferne zu überwachen, ob ein Player die Inhalte ordnungsgemäß abspielt. Sie verbessert die Reaktionsfähigkeit auf leere Bildschirme oder fehlerhafte Erlebnisse im Feld und verringert das Risiko, dem Endbenutzer ein fehlerhaftes Erlebnis zu zeigen.
Weitere Informationen finden Sie unter [Einfache Wiedergabe-Überwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=de#playback-monitoring).

* Unterstützung von Miniaturansichten für Videos in wird in Screens as a Cloud Service jetzt unterstützt. Ein Inhaltsautor kann eine Miniaturansicht für Videos definieren, sodass das Bild als Platzhalter verwendet und die Inhaltswiedergabe und das Targeting ordnungsgemäß getestet werden können, während das eigentliche Video vom entsprechenden Team fertiggestellt wird. Das Bild kann auch verwendet werden, wenn die Wiedergabe des Videos fehlschlägt.
Weitere Informationen finden Sie unter [Unterstützung von Miniaturansichten für Videos](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html?lang=de).

### Fehlerbehebungen {#bug-fixes-screens}

* Der Player konnte keine Inhalte von der eingebetteten Seite anzeigen. Dieses Problem wurde behoben.

* Nach einer erfolgreichen Anmeldung führte die Navigation zur Standardseite (Channels) zu einer Internal Server Error-Seite.

* Zugehörige Tag-Einträge wurden beim Entfernen der Wiedergabeliste(n) nicht entfernt.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Neue Funktionen in [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Erweiterte Netzwerke**

>[!INFO]
>
>Die Funktion für erweiterte Netzwerke ist Teil der Version 2021.9.0 und wird Mitte Oktober für Kunden aktiviert.

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] bietet jetzt mehrere Arten erweiterter Netzwerkfunktionen, darunter:

* Flexibler Port-Ausgang, um Traffic von nicht standardisierten Ports aus zu senden. Dies ist jetzt möglich, ohne sich an den Adobe-Support zu wenden.
* Dedizierte Ausgangs-IP-Adresse, um den Traffic aus AEM as a Cloud Service von einer eindeutigen IP-Adresse aus zu senden, die jetzt alle Ports unterstützt.
* VPN, um den Datenverkehr zwischen Ihrer Infrastruktur und AEM as a Cloud Service zu sichern.

Lesen Sie die [Dokumentation](/help/security/configuring-advanced-networking.md), um weitere Informationen zu erhalten, u. a. wie Sie mithilfe von Cloud Manager-APIs erweiterte Netzwerke selbst bereitstellen können.

**Indexoptimierungen**

Um die Leistung von Suchabfragen und Indizierungen zu verbessern, wird der Volltext-Index lucene-2 ab dieser Version nicht mehr vorkonfiguriert in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] verwendet. Um diesen Volltextindex auf AEM-Umgebungen in Absprache mit den AEM-Kunden zu entfernen, arbeitet Adobe Engineering individuell und proaktiv mit den Kunden an einer schonenden und nachhaltigen Entfernung des Lucene-Volltextindexes. Besuchen Sie die [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] [-Dokumentation](/help/operations/indexing.md#index-optimizations), wenn Sie weitere Informationen wünschen, und wenden Sie sich direkt an unseren Support, wenn Sie Fragen haben.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.9.0 und 2021.8.0.

## Veröffentlichungsdatum {#release-date-cm-sept}

Die Version 2021.9.0 von Cloud Manager in AEM as a Cloud Service wurde am 9. September 2021 veröffentlicht.
Die nächste Version wird am 7. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cm-sept}

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 30 aktualisiert.

* Die Programmkarten auf der Landingpage von Cloud Manager und das zugehörige Erlebnis wurden aktualisiert.

* Das „Code Quality Step“-Protokoll enthält jetzt ausführliche Protokollierungsinformationen zum OakPal-Scan-Prozess.

* Die Menüoptionen der Aktivitätsseite enthalten jetzt eine Option zum **Herunterladen von Protokollen** für abgeschlossene Code-Generator-Durchläufe. Wenn Sie diese Option auswählen, wird das Protokoll des Build-Schritts heruntergeladen.

* Wenn Sie direkt auf die Programmkarte klicken, navigieren Sie jetzt zur Übersichtsseite von Cloud Manager.

### Fehlerbehebungen {#bug-fixes-sept}

* Der Benutzer sieht jetzt eine verständlichere Meldung, wenn er versucht, eine neue IP-Zulassungsliste in ein Programm einzufügen, das die maximal zulässige Anzahl von IP-Zulassungslisten erreicht hat, die konfiguriert werden können.

* Eine falsche URL wurde kopiert, wenn die Menüoption „URL kopieren“ auf dem Bildschirm „Repositorys“ ausgewählt wurde.

## Cloud Acceleration Manager {#cam}

### Veröffentlichungsdatum {#release-date-october-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 4. Oktober 2021.

### Neue Funktionen {#what-is-new-cam}

* Cloud Acceleration Manager bietet den Nutzern jetzt die Möglichkeit, die BPA-Berichte in einer Druckvorschau zu betrachten, so dass sie einfach ausgedruckt oder als PDF gedruckt werden können, um sie leicht weitergeben zu können. Siehe Schritt 6 und 7 in [Verwenden der Best-Practices-Analyse-Karte](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=de#best-practices-analysis).

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.6.0 von Content Transfer Tool wurde am 4. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Verbesserte Benutzerzuordnung mit einem vereinfachten Benutzererlebnis, einschließlich der folgenden unten aufgeführten Funktionen. Weitere Informationen finden Sie unter [Verwenden des Tools für die Benutzerzuordnung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/using-user-mapping-tool.html?lang=de#using-user-mapping-tool).
   * Testen der Verbindung zur User Management-API, bevor die Benutzerzuordnung ausgeführt wird
   * Fehler elegant überspringen und mit der Aktivität Benutzerzuordnung fortfahren
   * Die Benutzerzuordnung schlägt nicht mehr fehl, wenn das Zugriffs-Token abläuft (nach 24 Stunden). Die Benutzerzuordnung kann an der Stelle erneut ausgeführt werden, an der sie zuletzt angehalten wurde.

* Um die Stabilität des Content Transfer Tool zu erhöhen, können Inhalte nicht gleichzeitig in die Autoren- oder Veröffentlichungsinstanz aufgenommen werden.

* Wenn Versionen enthalten sind, wird der Pfad `/var/audit` automatisch einbezogen, um Prüfereignisse zu migrieren.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa-latest}

Best Practices Analyzer 2.1.18 wurde am 2. September 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Möglichkeit, die Gesamtknotenanzahl zu erkennen und Berichte dazu zu erstellen.

* Möglichkeit, den Knotenspeichertyp und die Knotenspeichergröße zu erkennen und Berichte dazu zu erstellen.

### Fehlerbehebungen {#bug-fixes-bpa}

* BPA hat fälschlicherweise Commerce Integration Framework als vorhanden erkannt.
