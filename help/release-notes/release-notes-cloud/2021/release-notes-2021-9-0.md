---
title: Versionshinweise für Version 2021.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.9.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 8c12ff09-fbc8-42dd-87c0-46e509604f36
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1519'
ht-degree: 62%

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

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2021.9.0) war der 6. Oktober 2021.
Die folgende Version (2021.10.0) wurde am 4. November 2021 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht September 2021](https://video.tv.adobe.com/v/337381) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion im Kanal für die Vorabversion von [!DNL Sites] {#sites-prerelease-features}

* Inhaltsfragmentmodelle werden jetzt nach ihrer Veröffentlichung automatisch in einen schreibgeschützten Status versetzt, um unbeabsichtigte Umbrüche von Live-API-Abfragen nach der erneuten Veröffentlichung eines bearbeiteten Modells zu vermeiden. Benutzern wird beim Versuch, ein veröffentlichtes Modell zu bearbeiten, eine Warnung angezeigt. Die Bearbeitung ist möglich, sobald die Warnung akzeptiert wurde.

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

* **Verwenden Sie Adobe Sign-Rollen in einem adaptiven Formular** - Adobe Sign für Unternehmens- und Unternehmensdienstebenen ermöglichen es Ihnen, optional die Rollen für Vertragsempfänger über den Unterzeichner hinaus zu erweitern, damit sie besser den Workflow-Anforderungen entsprechen. Sie können jetzt [jedem Empfänger der Vereinbarung die Konfiguration seiner Rolle in einem adaptiven Formular ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform) ermöglichen, wobei der Unterzeichner die Standardrolle ist.

* **Analytics für adaptive Forms** - Sie können jetzt das Endbenutzerverhalten über Adobe Analytics für adaptive Forms erfassen und verfolgen, um Einblicke von Endbenutzern zu sammeln. Es hilft, informierte, datenbasierte Entscheidungen zu treffen, um das Endbenutzererlebnis zu verbessern.

* **Einfaches Verbinden von Adobe Experience Manager (AEM) Forms mit Microsoft® Dynamics und Salesforce** - Der Dienst stellt vordefinierte Datenquellenkonfigurationen und Datenmodelle für Microsoft® Dynamics und Salesforce bereit. Dies erleichtert Entwicklern die Konfiguration von Microsoft® Dynamics und Salesforce als Datenquellen für ein adaptives Formular ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/configure-msdynamics-salesforce.html).[

* **E-Signieren eines adaptiven Formulars mit DocuSign** - Sie können mithilfe von DocuSign ein adaptives Formular e-signieren. Der Service bietet eine benutzerdefinierte Übermittlungsaktion zur Verwendung von DocuSign bei einem adaptiven Formular. Sie können das im Bereich Software-Verteilung verfügbare Package installieren, um die Übermittlungsaktion zu importieren.

### Beta-Funktionen von [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Unified Storage Connector** - Verwenden Sie Unified Storage Connector, um Prozessdaten in kundenverwalteten Repositorys zu externalisieren. Sie können beispielsweise 
   * die Speicher- und Wiederaufnahmefunktion des Formularportals aktivieren und adaptive Formularentwürfe in einem kundenverwalteten Daten-Repository speichern.
   * prozessinterne AEM-Workflow-Daten (AEM-Workflow-Variablendaten), die sensible personenbezogene Daten (SPD) beinhalten, in einem vom Kunden verwalteten Repository speichern.

* **[!DNL AEM Forms as a Cloud Service - Communications]** - [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications.html) helfen Ihnen beim Kombinieren von XDP-Vorlagen und XML-Daten, um Druckdokumente in verschiedenen Formaten zu generieren. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:
   * Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   * Erzeugen Sie Ausgabeformulare in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckdatenströme.
   * Erzeugen von PDF-Druckdateien aus einem XFA-Formular-PDF und aus einem Adobe Acrobat-Formular.

Sie können sich an [!DNL formscsbeta@adobe.com] wenden, um sich für das Beta-Programm anzumelden.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Die neue Registerkarte &quot;Zugehörige Commerce-Inhalte&quot;im AEM Sites-Editor erhöht die Autoreneffizienz, indem schnell auf relevante AEM Produktinhalte für den aktuellen Kontext zugegriffen wird.

  ![Zugehörige Commerce-Inhalte](/help/assets/CIF/associated-commerce-content.png)

* Verbesserte Benutzeroberfläche zur Produktauswahl für ein besseres Benutzererlebnis, höhere Effizienz und Unterstützung bei einem komplexen Produktkatalog

  ![Neue Produktauswahl](/help/assets/CIF/product-picker.png)

* Berücksichtigung der Eigenschaft „include_in_menu“ in der Navigationskomponente

### Fehlerbehebungen {#bug-fixes-cif}

* Das Leeren des Menücache funktioniert jetzt erwartungsgemäß

* JS-Fehler während des AEM CS-Bereitstellungsschritts und bei Nichtverwendung clientseitiger Komponenten

* CIF-Cloud-Konfiguration kann jetzt auch in Ordnern erstellt werden, die einen sling:configs-Knoten haben

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### Neue Funktionen {#what-is-new-screens}

* Screens as a Cloud Service unterstützt jetzt eine einfache Wiedergabe-Überwachung. Der Player meldet jetzt bei jedem Ping (standardmäßig alle 30 Sekunden) verschiedene Wiedergabemetriken. Basierend auf den Metriken kann es verschiedene Edge-Fälle erkennen (festes Erlebnis, leerer Bildschirm, Planungsproblem usw.). Mit dieser Funktion kann das Team remote überwachen, ob ein Player Inhalte ordnungsgemäß wiedergibt. Sie verbessert die Reaktionsrate auf leere Bildschirme oder fehlerhafte Erlebnisse im Feld und verringert das Risiko, dem Benutzer ein fehlerhaftes Erlebnis anzuzeigen.
Weitere Informationen finden Sie unter [Einfache Wiedergabe-Überwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html#playback-monitoring).

* Unterstützung von Miniaturansichten für Videos in wird in Screens as a Cloud Service jetzt unterstützt. Inhaltsautorinnen und -autoren können eine Miniaturansicht für Videos definieren, sodass das Bild als Platzhalter verwendet und die Inhaltswiedergabe und das Targeting ordnungsgemäß getestet werden können, während das eigentliche Video vom entsprechenden Team fertiggestellt wird. Das Bild kann auch verwendet werden, wenn die Wiedergabe des Videos fehlschlägt.
Weitere Informationen finden Sie unter [Unterstützung von Miniaturansichten für Videos](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html).

### Fehlerbehebungen {#bug-fixes-screens}

* Der Player konnte keine Inhalte von der eingebetteten Seite anzeigen. Dieses Problem wurde behoben.

* Nach erfolgreicher Anmeldung wurde die Seite &quot;Interner Server-Fehler&quot;angezeigt, auf der die Standardseite (Kanäle) aufgerufen wurde.

* Zugehörige Tag-Einträge wurden beim Entfernen von Wiedergabelisten nicht entfernt.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Neue Funktionen in [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Erweiterte Netzwerke**

>[!INFO]
>
>Die erweiterte Netzwerkfunktion ist Teil der Version 2021.9.0 und wurde Mitte Oktober 2021 für Kunden aktiviert.

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] bietet jetzt mehrere Arten erweiterter Netzwerkfunktionen, darunter:

* Flexibler Port-Ausgang, um Traffic von nicht standardisierten Ports aus zu senden. Dies ist jetzt möglich, ohne sich an den Adobe-Support zu wenden.
* Dedizierte Ausgangs-IP-Adresse, um den Traffic aus AEM as a Cloud Service von einer eindeutigen IP-Adresse aus zu senden, die jetzt alle Ports unterstützt.
* VPN, um den Datenverkehr zwischen Ihrer Infrastruktur und AEM as a Cloud Service zu sichern.

Lesen Sie die [Dokumentation](/help/security/configuring-advanced-networking.md) , um weitere Informationen zu erhalten, einschließlich der Bereitstellung von Self-Service für erweiterte Netzwerke mit Cloud Manager-APIs.

**Indexoptimierungen**

Um die Leistung von Suchabfragen und Indizierungen zu verbessern, wird der Volltext-Index lucene-2 ab dieser Version nicht mehr vorkonfiguriert in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] verwendet. Um diesen Volltext-Index in AEM Umgebungen gemäß AEM Kunden zu entfernen, arbeitet Adobe Engineering individuell und proaktiv mit den Kunden zusammen, um eine schonende und nachhaltige Entfernung des Lucene-Volltext-Index zu erreichen. Weitere Informationen finden Sie in der Dokumentation [!DNL Adobe Experience Manager] als [!DNL Cloud Service] [Dokumentation](/help/operations/indexing.md#index-optimizations) und wenden Sie sich direkt an den Support von Adobe, wenn Sie Fragen haben.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.9.0 und 2021.8.0.

## Veröffentlichungsdatum {#release-date-cm-sept}

Die Version 2021.9.0 von Cloud Manager in AEM as a Cloud Service wurde am 9. September 2021 veröffentlicht.
Die nächste Version wird am 7. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cm-sept}

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 30 aktualisiert.

* Die Programmkarten auf der Landingpage vom Cloud Manager und das zugehörige Erlebnis wurden aktualisiert.

* Das Protokoll des Schritts „Code-Qualität“ enthält jetzt ausführliche Protokollierungsinformationen zum OakPal-Scan-Prozess.

* Die Menüoptionen der Aktivitätsseite enthalten jetzt eine Option zum **Herunterladen von Protokollen** für abgeschlossene Code-Generator-Durchläufe. Wenn Sie diese Option auswählen, wird das Protokoll des Build-Schritts heruntergeladen.

* Durch Klicken direkt auf die Programmkarte gelangen Sie jetzt zur Cloud Manager-Übersichtsseite.

### Fehlerbehebungen {#bug-fixes-sept}

* Benutzern wird jetzt eine verständlichere Meldung angezeigt, wenn sie versuchen, eine IP-Zulassungsliste in einem Programm hinzuzufügen, das die maximal zulässige Anzahl von IP-auf die Zulassungsliste setzten erreicht hat, die konfiguriert werden können.

* Die falsche URL wurde kopiert, wenn die Menüoption URL kopieren auf dem Bildschirm Repositorys ausgewählt wurde.

## Cloud Acceleration Manager {#cam}

### Veröffentlichungsdatum {#release-date-october-cam}

Das Veröffentlichungsdatum für Cloud Acceleration Manager war der 4. Oktober 2021.

### Neue Funktionen {#what-is-new-cam}

* Cloud Acceleration Manager bietet den Nutzern jetzt die Möglichkeit, die BPA-Berichte in einer Druckvorschau zu betrachten, so dass sie einfach ausgedruckt oder als PDF gedruckt werden können, um sie leicht weitergeben zu können. Siehe Schritt 6 und 7 in [Verwenden der Karte &quot;Best Practices für Analysen&quot;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=de#best-practices-analysis).

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

* BPA erkannte fälschlicherweise das Vorhandensein von Commerce integration framework.
