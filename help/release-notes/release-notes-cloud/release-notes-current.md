---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
mini-toc-levels: 1
source-git-commit: 372e40eb90d87d9ed366e08a3c0117068542680b
workflow-type: tm+mt
source-wordcount: '1427'
ht-degree: 23%

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

Das Veröffentlichungsdatum von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] aktuelle Version (2022.3.0) ist der 31. März 2022.
Die folgende Version (2022.4.0) wurde am 28. April 2022 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich die [März 2022 - Versionsübersicht](https://video.tv.adobe.com/v/341465) Video mit einer Zusammenfassung der Funktionen, die in der Version 2022.3.0 hinzugefügt wurden.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* [!DNL AEM Dynamic Media] bietet jetzt die Flexibilität, [ein Alias-Konto konfigurieren](/help/assets/dynamic-media/dm-alias-account.md) in der Benutzeroberfläche, um sicherzustellen, dass native Dynamic Media-URLs und der Viewer-Einbettungscode aktualisiert werden. Dies wirkt sich positiv auf SEO aus, um Aktualisierungen an Ihrem Geschäftskontext widerzuspiegeln, wie z. B. Rebranding.

* Sie können jetzt die [!DNL Experience Manager Assets] Benutzeroberfläche für:

   * Konfigurieren Sie die [Erkennung doppelter Assets](/help/assets/manage-digital-assets.md#detect-duplicate-assets) in einem Repository.

   * Konfigurieren [Hinzufügen digitaler Wasserzeichen](/help/assets/watermark-assets.md) Bilder.

* Administratoren können jetzt den E-Mail-Dienst für große Downloads konfigurieren. Dadurch können Benutzer [E-Mail-Benachrichtigungen für große Downloads aktivieren](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads) von [!DNL Experience Manager Assets] -Schnittstelle. Nach Abschluss des Download-Prozesses erhält der Benutzer eine E-Mail-Benachrichtigung mit dem Download-Link des archivierten ZIP-Ordners.

* Die [Veröffentlichung verwalten](/help/assets/manage-publication.md) wurde um eine verbesserte Benutzeroberfläche erweitert. Die Benutzer können Inhalte in dem ausgewählten Ziel veröffentlichen oder dessen Veröffentlichung rückgängig machen. [Inhalt hinzufügen](/help/assets/manage-publication.md#add-content) zur Veröffentlichungsliste aus dem gesamten DAM-Repository [Ordnereinstellungen einschließen](/help/assets/manage-publication.md#include-folder-settings) zum Veröffentlichen des Inhalts der ausgewählten Ordner und zum Anwenden von Filtern und [Veröffentlichung planen](/help/assets/manage-publication.md#publish-assets-later) zu einem späteren Zeitpunkt.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Assets] verfügbar {#prerelease-features-assets}

* Sie können [sort Tags](/help/assets/organize-assets.md#use-tags-to-organize-assets) beim Erstellen von Smart-Tags sowie beim Anwenden von Suchfiltern mithilfe des Tag-Prädikats.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **[!DNL Communications - Document Generation APIs]**: [APIs zur Dokumenterstellung](/help/forms/aem-forms-cloud-service-communications.md) hilft beim Kombinieren, Neuanordnen und Validieren von PDF-Dokumenten. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:

   * Zusammenführen von PDF-Dokumenten.
   * Aufteilen von PDF-Dokumenten.
   * Konvertieren Sie in PDF/A-konforme Dokumente und überprüfen Sie sie.

* **Automatische Konvertierung von PDF forms mit mehr als 15 Seiten in adaptive Formulare**: Sie können jetzt den automated forms conversion-Dienst verwenden, um PDF forms mit bis zu 40 Seiten in adaptive Formulare zu konvertieren. Der Dienst bietet jetzt eine Option zum Konvertieren von Abschnitten von Formularen, die größer als 15 Seiten sind, in adaptive Formularfragmente. Dies trägt zur Beschleunigung der Darstellungsgeschwindigkeit konvertierter Formulare bei und erleichtert das Laden großer Formulare im Editor für adaptive Formulare.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **Verwenden benutzerdefinierter XCI zum Generieren eines Datensatzdokuments**: Sie können jetzt eine benutzerdefinierte XCI-Datei verwenden, um verschiedene Eigenschaften eines Datensatzdokuments festzulegen. Sie überschreibt das Übergeordnete XCI mit den benutzerdefinierten Änderungen.

* **Unsichtbares CAPTCHA in einem adaptiven Formular verwenden**: Sie können das unsichtbare CAPTCHA verwenden, um die CAPTCHA-Herausforderung nur im Falle einer verdächtigen Aktivität anzuzeigen. Wenn keine verdächtige Aktivität gefunden wird, wird die CAPTCHA-Herausforderung nicht angezeigt.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Beta: AEM CIF-Such-Kernkomponente unterstützt Commerce LiveSearch
* Verbessertes SEO für Multi-Store-Szenarien: URL-Formate für PDP/PLP können jetzt auf Store-Ebene über die CIF Cloud-Konfigurationseigenschaften konfiguriert werden
* Die Produktauswahl unterstützt gestaffelte Produkte über die neue Filteroption in der Benutzeroberfläche.  Dadurch können Content-Experten das Content-Management für bevorstehende Produktstarts vorbereiten.
* Vereinfachte CIF-Konfigurationsverwaltung und Fehlerbehandlung durch Verwendung des CIF-Cloud-Konfigurationsnamens anstelle der config-Proxy-URL
* Manuelle Kategorieauswahl für Produktliste und Karussellkomponenten. Dadurch können Content-Experten diese Komponenten auf Inhaltsseiten außerhalb des Katalogerlebnisses verwenden

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Für eine effizientere und effektivere Fehlerbehebung bei benutzerdefinierten Funktionen in Cloud-Umgebungen haben wir ein neues Entwickler-Tool veröffentlicht - [Repository-Browser](/help/implementing/developing/tools/repository-browser.md). Es handelt sich um einen einfachen, schreibgeschützten HTML-Browser, den Sie über die Developer Console starten können. Erhalten Sie Einblicke in das Inhalts-Repository auf den Ebenen &quot;Publisher&quot;, &quot;Autor&quot;und &quot;Vorschau&quot;- und in allen Umgebungen, einschließlich Produktion, Staging und Entwicklung. Durchsuchen Sie die Inhaltsstruktur, zeigen Sie die Eigenschaften an, zeigen Sie die Binärdateien in der Vorschau an und laden Sie sie herunter.

   ![repobrowserrelnotes](/help/release-notes/assets/repobrowserrelnotes.png)

* Die Anmeldeinformationen, die zum Authentifizieren von Server-zu-Server-API-Aufrufen verwendet werden (z. B. für GraphQL-API-Anfragen), können jetzt vor Ablauf von der Developer Console aus aktualisiert werden. Siehe [Dokumentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) für weitere Informationen.

* Wartungsaufgaben für Versionsbereinigung und Auditprotokolllöschung, die zuvor nicht aktiviert waren, werden für neue Umgebungen aktiviert. Die zugehörigen Werte finden Sie in der [Wartungsaufgabe](/help/operations/maintenance.md) Artikel.

* AEM as a Cloud Service SDK Dispatcher Tools unterstützen jetzt Mac-Computer mit M1-Chip

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum Februar {#release-date-cm-feb}

Die Cloud Manager-Version AEM as a Cloud Service Version 2022.02.0 wurde am 10. Februar 2022 veröffentlicht. Die nächste Version soll am 10. März 2022 veröffentlicht werden.

### Neue Funktionen {#what-is-new-cm-feb}

* Neu beschleunigt [Web-Ebenen-Konfigurations-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) wurden eingeführt, um ausschließlich die HTTPD/Dispatcher-Konfiguration bereitzustellen.
   * Sie müssen AEM Version verwenden `2021.12.6151.20211217T120950Z` oder neuer und [Aktivieren des flexiblen Modus der Dispatcher-Tools](/help/implementing/dispatcher/disp-overview.md#validation-debug) , um diese Funktion zu verwenden.
   * Diese Funktion wird in den zwei Wochen nach der Version 2022.02.0 schrittweise eingeführt.
* Das Landingpage-Erlebnis von Cloud Manager wurde aktualisiert, um eine verbesserte Navigation, einen einfachen Wechsel zwischen Raster-/Kachelansichten und Pop-ups für eine schnelle Programmzusammenfassung zu ermöglichen.
* Ein neuer ausfallender Schwellenwert (`< D`) wurde zum [Zuverlässigkeitsbewertungsmetrik.](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules)
   * Kunden mit schwerwiegenden Qualitätsproblemen, die sich auf die Systemstabilität auswirken und in erster Linie auf ungültige Indizes und Workflow-Prozesse zurückzuführen sind, können die Bereitstellung erst nach Behebung dieser Probleme durchführen.
* Die Schwere der `BannedPath` [Qualitätsregel](/help/implementing/cloud-manager/code-quality-testing.md#understanding-code-quality-rules) wurde von Blocker zu kritisch geändert.
* Der Pipeline-Assistent informiert den Benutzer, wenn vor dem Konfigurieren einer AEM möglicherweise eine Aktualisierung der Umgebung erforderlich ist. [Web-Ebenen-Konfigurations-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md#web-tier-config-pipelines) zugeordnet.

### Fehlerbehebungen {#bug-fixes-cm-feb}

* Alte Git-Repository-Kennwörter werden jetzt immer invalidiert, wenn ein neues Kennwort generiert wird.
* Die Aktualisierung von Umgebungsvariablen über die API beeinträchtigt in seltenen Fällen nicht mehr die Pipelineausführung.

### Veröffentlichungsdatum März {#release-date-cm-march}

Die Cloud Manager -Version 2022.3.0 wurde AEM as a Cloud Service 10. März 2022 veröffentlicht. Die nächste Version ist für den 7. April 2022 geplant.

### Neue Funktionen {#what-is-new-cm-march}

* Der Zugriff auf AEM Umgebungsprotokoll kann über die Entwicklerrolle erfolgen.

### Fehlerbehebungen {#bug-fixes-cm-march}

* Eine Untergruppe von manuell erstellten Git-Repositorys hatte einen falschen Namenswert, was verhindert hat, dass die Funktion zur Wiederverwendung von Build-Artefakten effektiv war. Die Namen dieser Repositorys wurden geändert, und die Benutzer sehen den berichtigten Namen in der Cloud Manager-API/-Benutzeroberfläche.
* Build-Artefakte aus produktionsfremden Pipelines wurden in Vollstapel-Pipelines der Produktion unangemessen wiederverwendet.
* Beim Hinzufügen oder Bearbeiten einer Code-Qualitäts-Pipeline werden die Optionen zum Verarbeiten von Metrikfehlern nicht mehr angezeigt.
* Im Build-Schritt konnten einige unerwartete Konfigurationen von Pipeline-Variablen auftreten.

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.9.0 wurde am 28. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Schutzmechanismen für die Größe überprüfen - Die Funktion &quot;Prüfgröße für Content Transfer Tool&quot;hilft bei der Reduzierung fehlgeschlagener Inhaltstransfers.  Mit der Funktion &quot;Größe überprüfen&quot;können Benutzer 1) feststellen, ob sie über ausreichend Festplattenspeicher im `crx-quickstart` -Unterverzeichnis vor der Extraktion und 2) schätzen die Größe des Migrationssatzes und überprüfen Sie, ob es unterstützt wird. Wenn eine oder beide Prüfungen verletzt werden, werden Benutzern Warnungen in der CTT-Benutzeroberfläche angezeigt. Mit dieser Limits können Sie Fehler bei der Inhaltstransfer vermeiden und Migrationsoptionen proaktiv mit der Adobe-Kundenunterstützung besprechen. Siehe [Bestimmen der Größe des Migrationssatzes und des Festplattenspeichers](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=en#migration-set-size) für weitere Details.

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.26 wurde am 16. März 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, nicht verarbeitete Assets zu erkennen. Wenn nicht verarbeitete Assets erkannt werden, müssen diese Assets entweder auf &quot;Verarbeitet&quot;gesetzt oder aus dem Migrationssatz während der Inhaltstransfer entfernt werden, um Probleme bei der Inhaltsaufnahme zu vermeiden.
* Möglichkeit, festzustellen, ob Inhalt über mehr als 1000 Vanity-URLs verfügt. Die Verwendung einer hohen Anzahl von Vanity-URLs empfiehlt sich nicht, da Dispatcher- und Publish-Server geladen werden.
* Möglichkeit, Probleme im Zusammenhang mit Oak-Indexdefinitionen zu identifizieren und Inkompatibilitäten mit AEM as a Cloud Service zu erkennen.
* Möglichkeit, die Verwendung von Externalizer-Konfigurationen zu erkennen und darüber zu berichten. In AEM werden as a Cloud Service Externalizer-Konfigurationen von Cloud Manager festgelegt. Daher müssen vorhandene Externalizer-Konfigurationen überarbeitet werden, um die Kompatibilität zu gewährleisten.

### Fehlerbehebungen {#bug-fixes-bpa}

* In einigen Szenarien konnte BPA nicht ausgeführt werden, da FormsSelectiveFeaturesAnalysis einen Assertionsfehler ausgab. Dieses Problem wurde behoben.
* BPA meldete Ergebnisse im Zusammenhang mit dem WRK-Muster als MAJOR anstelle von CRITICAL. Dieses Problem wurde behoben.
* BPA meldete fälschlicherweise Ergebnisse im Zusammenhang mit OAK-Indexdefinitionen in ui.apps als CRITICAL an. Dieses Problem wurde behoben
