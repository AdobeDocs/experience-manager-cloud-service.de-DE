---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: f89fbf4e693fb1b17e8923dfcc6c9b4de92b536d
workflow-type: tm+mt
source-wordcount: '1928'
ht-degree: 34%

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

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2021.9.0) ist der 6. Oktober 2021.
Die folgende Version (2021.10.0) wurde am 4. November 2021 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich die [September 2021 - Versionsübersicht](https://video.tv.adobe.com/v/337381) Video mit einer Zusammenfassung der hinzugefügten Funktionen.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion im [!DNL Sites] Vorabversionskanal {#sites-prerelease-features}

* Inhaltsfragmentmodelle werden jetzt nach ihrer Veröffentlichung automatisch im schreibgeschützten Status festgelegt, um unbeabsichtigte Umbrüche von Live-API-Abfragen nach der erneuten Veröffentlichung eines bearbeiteten Modells zu vermeiden. Benutzern wird beim Versuch, ein veröffentlichtes Modell zu bearbeiten, eine Warnung angezeigt. Die Bearbeitung ist möglich, sobald die Warnung akzeptiert wurde.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* Die Anmerkung von PDF-Dateien wird jetzt mit nativen Kommentar- und Anmerkungs-Tools von Adobe Document Cloud unterstützt. Kommentieren Sie PDF-Inhalte, indem Sie Text, Highlights, Notizen und Zeichnungen direkt im Dokumentvorschaufenster hinzufügen. Benutzer können auch zu Seiten springen, die für die PDF von Interesse sind, indem sie auf bestimmte Kommentare klicken

* Benutzer können nun die in den Suchergebnissen in den Spalten- und Kartenansichten angezeigten Assets sortieren. Die Sortierung funktioniert mit den Spalten &quot;Name&quot;, &quot;Erstellt&quot;, &quot;Geändert&quot;oder &quot;Keine&quot;.

   ![Sortieren Sie die Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten](/help/assets/assets/sort-searched-assets.png)
   *Abbildung: Sortieren Sie die Suchergebnisse in [!DNL Assets] in Spalten- und Kartenansichten.*

### Neue Funktion im [!DNL Assets] Vorabversionskanal {#assets-prerelease-features}

* [!DNL Assets] umfasst jetzt einen integrierten Connector zu [!DNL Azure Media Services] für Audio- und Videotranskriptionen. Nach der Konfiguration werden die unterstützten Dateien automatisch transkribiert und WebVTT-Dateien generiert. Die WebVTT-Untertitel werden für eine effektivere Suche, Untertitelung oder Übersetzung als Untertitel verwendet.

<!-- TBD: 'Unpublishing' this feature as suggested by engineering.

* To programmatically invoke processing using asset microservices, a new API is introduced. Developers can now apply an existing folder-level processing profile on one or more specific assets in a folder. The processing profile gets applied based on custom metadata properties updates. See `AssetProcessor` in the [[!DNL Experience Manager] API reference](https://www.adobe.io/experience-manager/reference-materials/). As before, it is possible to [use asset microservices from the user interface](/help/assets/asset-microservices-configure-and-use.md).

-->
<!-- Leave this commented.

### New feature in the [!DNL Assets] prerelease channel {#assets-prerelease-features}

Apparently, no new Assets features in Sep prerelease channel.
A/V transcription feature via CQ-4303854 has moved to Oct prerelease now.

### Bugs fixed in [!DNL Assets] {#assets-bugs-fixed}

No customer-reported bugs fixed in Sep release.
CQ-4328183 was not reported on CS so not documented here.
-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms-sep-2021}

* **Verwenden von Adobe Sign-Rollen in einem adaptiven Formular**: Die Service-Levels von Adobe Sign für Unternehmen bieten die Möglichkeit, die Rollen von Empfängern von Vereinbarungen über die unterschreibende Person hinaus zu erweitern und so ihren Workflow-Anforderungen besser zu entsprechen. Sie können jetzt [jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular zu konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/use-adobe-sign/working-with-adobe-sign.html#addsignerstoanadaptiveform), wobei „Unterschreibende Person“ die Standardrolle ist.

* **Analytics für adaptive Formulare**[: Sie können jetzt das Endbenutzerverhalten über Adobe Analytics für adaptive Formulare erfassen und verfolgen, um Erkenntnisse über Endbenutzer zu sammeln. ](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/integrate-aem-forms-with-adobe-analytics.html) Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Erlebnis der Endbenutzer zu verbessern.

* **Einfaches Verbinden von AEM Forms mit Microsoft Dynamics und Salesforce**: Der Service stellt vorkonfigurierte Datenquellenkonfigurationen und Datenmodelle für Microsoft Dynamics und Salesforce bereit, sodass [Entwickler Microsoft Dynamics und Salesforce schneller und einfacher als Datenquellen für adaptive Formulare konfigurieren können](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-msdynamics-salesforce.html?lang=en).

* **E-Signieren eines adaptiven Formulars mit DocuSign:**[ Sie können DocuSign verwenden, um ein adaptives Formular elektronisch zu unterzeichnen](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/integrate-docusign-adaptive-forms.html). Der Service bietet eine benutzerdefinierte Übermittlungsaktion zur Verwendung von DocuSign bei einem adaptiven Formular.

### Beta-Funktionen von [!DNL Forms] {#sep-what-is-new-forms-prerelease}

* **Unified Storage Connector:** Verwenden Sie Unified Storage Connector, um prozessinterne Daten in vom Kunden verwalteten Repositorys zu externalisieren. Sie können beispielsweise Speichern Sie AEM Workflow-Daten (AEM Workflow-Variablen-Daten), die vertrauliche personenbezogene Daten (EPPD) enthalten, in einem kundenverwalteten Repository.

   <!--* Enable Forms Portal’s save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=en) helfen Ihnen, XDP-Vorlagen und XML-Daten zu kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:
   * Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   * Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckströme.
   * Erzeugen von PDF-Druckdateien aus einem XFA-Formular-PDF und aus einem Adobe Acrobat-Formular.

Sie können sich an [!DNL formscsbeta@adobe.com] wenden, um sich für das Beta-Programm anzumelden.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Die neue Registerkarte &quot;Zugehörige Commerce-Inhalte&quot;im Sites-Editor erhöht die Autoreneffizienz, indem schnell auf relevante AEM Produktinhalte für den aktuellen Kontext zugegriffen wird.

   ![Zugehörige Commerce-Inhalte](/help/assets/CIF/associated-commerce-content.png)

* Verbesserte Benutzeroberfläche für die Produktauswahl für bessere Benutzererfahrung, höhere Effizienz und Unterstützung für komplexen Produktkatalog

   ![Neue Produktauswahl](/help/assets/CIF/product-picker.png)

* Die Eigenschaft &quot;include_in_menu&quot;in der Navigationskomponente respektieren

### Fehlerbehebungen {#bug-fixes-cif}

* Das Leeren des Menücache funktioniert nicht erwartungsgemäß

* JS-Fehler während AEM CS-Bereitstellungsschritts und bei Nichtverwendung clientseitiger Komponenten

* CIF-Cloud-Konfiguration kann nicht in Ordnern erstellt werden, die einen sling:configs -Knoten haben

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

### Neue Funktionen {#what-is-new-screens}

* Screens as a Cloud Service unterstützt jetzt die grundlegende Wiedergabe-Überwachung. Der Player meldet jetzt bei jedem Ping (standardmäßig alle 30 Sekunden) verschiedene Wiedergabemetriken. Basierend auf den Metriken bietet dies die Möglichkeit, verschiedene Grenzfälle zu erkennen (z. B. steckengebliebenes Erlebnis, leerer Bildschirm, Zeitplanprobleme usw.). Diese Funktion ermöglicht es dem Team, aus der Ferne zu überwachen, ob ein Player die Inhalte ordnungsgemäß abspielt. Sie verbessert die Reaktionsfähigkeit auf leere Bildschirme oder fehlerhafte Erlebnisse im Feld und verringert das Risiko, dem Endbenutzer ein fehlerhaftes Erlebnis zu zeigen.
Weitere Informationen finden Sie unter [Einfache Wiedergabe-Überwachung](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/manage-player-registration/installing-screens-cloud-player.html?lang=en#playback-monitoring).

* Unterstützung von Miniaturbildern für Videos in wird jetzt in Screens as a Cloud Service unterstützt. Ein Inhaltsautor kann eine Miniaturansicht für Videos definieren, sodass das Bild als Platzhalter verwendet und die Inhaltswiedergabe und das Targeting ordnungsgemäß getestet werden können, während das eigentliche Video vom entsprechenden Team fertiggestellt wird. Das Bild kann auch verwendet werden, wenn die Wiedergabe des Videos fehlschlägt.
Weitere Informationen finden Sie unter [Unterstützung von Miniaturansichten für Videos](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/core-product-features/thumbnail-support-videos.html).

### Fehlerbehebungen {#bug-fixes-screens}

* Der Player konnte keine Inhalte von der eingebetteten Seite anzeigen. Dieses Problem wurde behoben.

* Nach erfolgreicher Anmeldung wurde die Seite &quot;Interner Server-Fehler&quot;angezeigt, auf der die Standardseite (Kanäle) aufgerufen wurde.

* Zugehörige Tag-Einträge wurden beim Entfernen der Wiedergabeliste(n) nicht entfernt.

## [!DNL Experience Manager as a Cloud Service] Foundation {#foundation}

### Neue Funktionen in [!DNL Experience Manager as a Cloud Service] {#foundation-features}

**Erweiterte Netzwerke**

>[!INFO]
>
>Die Funktion für erweiterte Netzwerke ist Teil der Version 2021.9.0 und wird Mitte Oktober für Kunden aktiviert.

[!DNL Adobe Experience Manager] as a [!DNL Cloud Service] bietet jetzt mehrere Arten erweiterter Netzwerkfunktionen, darunter:

* Flexibler Hafenausstieg zur Auslagerung von Traffic aus nicht standardmäßigen Ports. Jetzt möglich, ohne sich an den Adobe Support zu wenden.
* Dedizierte Ausgangs-IP-Adresse, um Traffic aus AEM as a Cloud Service von einer eindeutigen IP zu entfernen, und unterstützt jetzt alle Ports.
* VPN, um den Datenverkehr zwischen Ihrer Infrastruktur und AEM as a Cloud Service zu sichern.

Lesen Sie die [Dokumentation](/help/security/configuring-advanced-networking.md) für weitere Informationen, einschließlich der Bereitstellung erweiterter Netzwerke mithilfe von Cloud Manager-APIs durch Self-Service.

**Indexoptimierungen**

Um die Leistung von Suchabfragen und Indizierungen zu verbessern, wird der Volltext-Index lucene-2 nicht mehr standardmäßig in [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aus dieser Version. Um diesen Volltext-Index in AEM Umgebungen gemäß AEM Kunden zu entfernen, arbeitet Adobe Engineering individuell und proaktiv mit den Kunden zusammen, um eine schonende und nachhaltige Entfernung des Lucene-Volltextindex zu erreichen. Besuchen Sie die [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] [Dokumentation](/help/operations/indexing.md#index-optimizations) für weitere Informationen und wenden Sie sich direkt an unseren Support, wenn Sie Fragen haben.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.10.0 und 2021.9.0.

## Veröffentlichungsdatum {#release-date-cm-oct}

Die Cloud Manager-Version AEM as a Cloud Service Version 2021.10.0 wurde am 14. Oktober 2021 veröffentlicht.
Die nächste Version ist für den 4. November 2021 geplant.

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

## Veröffentlichungsdatum {#release-date-cm-sept}

Die Cloud Manager -Version AEM as a Cloud Service Version 2021.9.0 wurde am 9. September 2021 veröffentlicht.

### Fehlerbehebungen {#bug-fixes-cm-oct}

* In seltenen Fällen, in denen Mitarbeiter der Adobe die Umgebung eines Kunden wiederherstellen, wurde die Wiederherstellung als abgeschlossen angesehen, bevor die Umgebung voll funktionsfähig war.

* Bestimmte interne Anforderungen, die während der Erstellung der Umgebung gestellt wurden, wurden nicht erneut versucht.

* Wenn nach der Verifizierung des Domain-Namens ein Fehler bei der Bereitstellung auftritt, wurde die Fehlermeldung korrigiert, um den Kunden aufzufordern, sich an seinen Kundenbetreuer zu wenden.


### Neue Funktionen {#what-is-new-cm-sept}

* Der von Cloud Manager verwendete AEM-Projektarchetyp wurde auf Version 30 aktualisiert.

* Die Programmkarten auf der Landingpage von Cloud Manager und das zugehörige Erlebnis wurden aktualisiert.

* Das „Code Quality Step“-Protokoll enthält jetzt ausführliche Protokollierungsinformationen zum OakPal-Scan-Prozess.

* Die Menüoptionen auf der Seite &quot;Aktivität&quot;enthalten jetzt eine Option zum **Download-Protokoll** für abgeschlossene Code-Generator-Ausführungen. Wenn Sie diese Option auswählen, wird das Protokoll des Build-Schritts heruntergeladen.

* Wenn Sie direkt auf die Programmkarte klicken, navigieren Sie jetzt zur Übersichtsseite von Cloud Manager.

### Fehlerbehebungen {#bug-fixes-sept}

* Der Benutzer wird jetzt eine verständlichere Meldung sehen, wenn er versucht, eine neue IP-Zulassungsliste in ein Programm einzufügen, das die maximal zulässige Anzahl von IP-Zulassungslisten erreicht hat, die konfiguriert werden können.

* Eine falsche URL wurde kopiert, wenn die Menüoption „URL kopieren“ auf dem Bildschirm „Repositorys“ ausgewählt wurde.

## Cloud Acceleration Manager {#cam}

### Veröffentlichungsdatum {#release-date-october-cam}

Die Cloud Acceleration Manager-Version wurde am 4. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-cam}

* Cloud Acceleration Manager bietet Benutzern jetzt die Möglichkeit, die BPA-Berichte in einer druckbaren Vorschau anzuzeigen, sodass sie zur einfachen Freigabe einfach drucken oder auf PDF drucken können. Siehe Schritt 6 und 7 unter [Verwenden der Analyse-Karte mit Best Practices](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-acceleration-manager/using-cam/cam-readiness-phase.html?lang=en#best-practices-analysis).

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.6.0 des Content Transfer Tool wurde am 4. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Verbessertes Tool für die Benutzerzuordnung mit einem vereinfachten Benutzererlebnis, einschließlich der folgenden unten aufgeführten Funktionen. Weitere Informationen finden Sie unter [Verwenden des Benutzerzuordnungs-Tools](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/user-mapping-tool/using-user-mapping-tool.html).
   * Testen Sie die Verbindung zur User Management-API, bevor Sie die Benutzerzuordnung ausführen.
   * Fehler lassen und mit der Aktivität Benutzerzuordnung fortfahren
   * Die Benutzerzuordnung schlägt nicht mehr fehl, wenn **Zugriffstoken** läuft nach 24 Stunden ab. Die Benutzerzuordnung kann an der Stelle erneut ausgeführt werden, an der sie zuletzt angehalten wurde.

* Um die Stabilität des Content Transfer Tool zu erhöhen, können Inhalte gleichzeitig in die Autoren- oder Veröffentlichungsinstanz aufgenommen werden. Siehe [Erste Schritte mit dem Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en) für weitere Details.

* Wenn Versionen enthalten sind, wird der Pfad `/var/audit` wird automatisch einbezogen, um Prüfereignisse zu migrieren.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa-latest}

Die Version 2.1.20 von Best Practices Analyzer wurde am 5. Oktober 2021 veröffentlicht.

### Neue Funktionen {#what-is-new}

* Möglichkeit, die Länge von Knotennamen zu erkennen und darüber zu berichten.

* Möglichkeit, die Gesamtgröße des Index zu erkennen und darüber zu berichten.

* Möglichkeit zur Erkennung und Berichterstellung von Assets, denen die ursprüngliche Ausgabedarstellung fehlt.

