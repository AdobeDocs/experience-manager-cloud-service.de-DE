---
title: Versionshinweise für Version 2022.3.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2022.3.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 761f1605-c421-4f3a-8f90-af23f4f047b1
source-git-commit: b71cd1394260c8ec14b661934199632987a034f6
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 56%

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
Die nächste Version (2022.4.0) ist für den 5. Mai 2022 geplant.

## Video zur Version {#release-video}

Sehen Sie sich die [März 2022 - Versionsübersicht](https://video.tv.adobe.com/v/341465) Video mit einer Zusammenfassung der Funktionen, die in der Version 2022.3.0 hinzugefügt wurden.

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Sites] verfügbar {#prerelease-features-sites}

* Die Datentypen des Inhaltsmodells können jetzt mithilfe eines einfachen Kontrollkästchens im Inhaltsmodell-Editor als übersetzbar definiert werden. Darüber hinaus werden AEM Übersetzungsregeln und -konfigurationen automatisch aktualisiert.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#assets-features}

* [!DNL AEM Dynamic Media] bietet jetzt die Flexibilität, in der Benutzeroberfläche [ein Alias-Konto zu konfigurieren](/help/assets/dynamic-media/dm-alias-account.md), um sicherzustellen, dass vorkonfigurierte Dynamic Media-URLs und der Viewer-Einbettungs-Code aktualisiert werden. Dies wirkt sich positiv auf die SEO aus, die nun Aktualisierungen an Ihrem Geschäftskontext, wie z. B. Rebranding, widerspiegelt.

* Sie können die Benutzeroberfläche von [!DNL Experience Manager Assets] für folgende Vorgänge verwenden:

   * Konfigurieren Sie die [Erkennung doppelter Assets](/help/assets/manage-digital-assets.md#detect-duplicate-assets) in einem Repository.

   * Konfigurieren [Hinzufügen digitaler Wasserzeichen](/help/assets/watermark-assets.md) Bilder.

* Administratoren können jetzt den E-Mail-Service für große Downloads konfigurieren. Dadurch können Benutzer von der [!DNL Experience Manager Assets]-Benutzeroberfläche aus [E-Mail-Benachrichtigungen für große Downloads aktivieren](/help/assets/download-assets-from-aem.md#enable-email-notifications-for-large-downloads). Nach Abschluss des Download-Prozesses erhält der Benutzer eine E-Mail-Benachrichtigung mit dem Download-Link des archivierten ZIP-Ordners.

* Die Funktion [Veröffentlichung verwalten](/help/assets/manage-publication.md) wurde um eine verbesserte Benutzeroberfläche erweitert. Die Benutzer können Inhalte in dem ausgewählten Ziel veröffentlichen oder dessen Veröffentlichung rückgängig machen. [Inhalt hinzufügen](/help/assets/manage-publication.md#add-content) zur Veröffentlichungsliste aus dem gesamten DAM-Repository [Ordnereinstellungen einschließen](/help/assets/manage-publication.md#include-folder-settings) zum Veröffentlichen des Inhalts der ausgewählten Ordner und zum Anwenden von Filtern und [Veröffentlichung planen](/help/assets/manage-publication.md#publish-assets-later) zu einem späteren Zeitpunkt.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Assets] verfügbar {#prerelease-features-assets}

* Sie können jetzt [sort Tags](/help/assets/organize-assets.md#use-tags-to-organize-assets) im Tag-Auswahl-Fenster in auf- oder absteigender Reihenfolge, basierend auf dem Tag-Namen, dem Erstellungsdatum oder dem Änderungsdatum.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **[!DNL Communications - Document Generation APIs]**: [APIs zur Dokumenterstellung](/help/forms/aem-forms-cloud-service-communications.md) hilft beim Kombinieren, Neuanordnen und Validieren von PDF-Dokumenten. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:

   * Zusammenführen von PDF-Dokumenten.
   * Aufteilen von PDF-Dokumenten.
   * Konvertieren in PDF/A-konforme Dokumente und Validieren.

* **Automatische Konvertierung von PDF forms mit mehr als 15 Seiten in adaptive Formulare**: Sie können jetzt den automated forms conversion-Dienst verwenden, um PDF forms mit bis zu 40 Seiten in adaptive Formulare zu konvertieren. Der Dienst bietet jetzt eine Option zum Konvertieren von Abschnitten von Formularen, die größer als 15 Seiten sind, in adaptive Formularfragmente. Dies trägt zur Beschleunigung der Darstellungsgeschwindigkeit konvertierter Formulare bei und erleichtert das Laden großer Formulare im Editor für adaptive Formulare.

### Neue Funktionen im Kanal für die Vorabversion von [!DNL Forms] verfügbar {#prerelease-features-forms}

* **Verwenden benutzerdefinierter XCI zum Generieren eines Datensatzdokuments**: Sie können jetzt eine benutzerdefinierte XCI-Datei verwenden, um verschiedene Eigenschaften eines Datensatzdokuments festzulegen. Sie überschreibt das Übergeordnete XCI mit den benutzerdefinierten Änderungen.

* **Unsichtbares CAPTCHA in einem adaptiven Formular verwenden**: Sie können das unsichtbare CAPTCHA verwenden, um die CAPTCHA-Herausforderung nur im Falle einer verdächtigen Aktivität anzuzeigen. Wenn keine verdächtige Aktivität gefunden wird, wird die CAPTCHA-Herausforderung nicht angezeigt.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Verbessertes SEO für Multi-Store-Szenarien: URL-Formate für PDP/PLP können jetzt auf Store-Ebene über die CIF Cloud-Konfigurationseigenschaften konfiguriert werden
* Die Produktauswahl unterstützt gestaffelte Produkte über die neue Filteroption in der Benutzeroberfläche.  Dadurch können Content-Experten das Content-Management für bevorstehende Produktstarts vorbereiten.
* Vereinfachte CIF-Konfigurationsverwaltung und Fehlerbehandlung durch Verwendung des CIF-Cloud-Konfigurationsnamens anstelle der config-Proxy-URL
* Manuelle Kategorieauswahl für Produktliste und Karussellkomponenten. Dadurch können Content-Experten diese Komponenten auf Inhaltsseiten außerhalb des Katalogerlebnisses verwenden

### Neue Funktionen im CIF-Vorversionskanal {#prerelease-features-cif}

* AEM CIF-Such-Kernkomponente unterstützt Commerce LiveSearch

## [!DNL Experience Manager] as a [!DNL Cloud Service] Foundation {#foundation}

### Neue Funktionen {#what-is-new-foundation}

* Für eine effizientere und effektivere Fehlerbehebung bei benutzerdefinierten Funktionen in Cloud-Umgebungen haben wir ein neues Entwickler-Tool veröffentlicht - [Repository-Browser](/help/implementing/developing/tools/repository-browser.md). Es handelt sich um einen einfachen, schreibgeschützten HTML-Browser, den Sie über die Developer Console starten können. Erhalten Sie Einblicke in das Inhalts-Repository auf den Ebenen &quot;Publisher&quot;, &quot;Autor&quot;und &quot;Vorschau&quot;- und in allen Umgebungen, einschließlich Produktion, Staging und Entwicklung. Durchsuchen Sie die Inhaltsstruktur, zeigen Sie die Eigenschaften an, zeigen Sie die Binärdateien in der Vorschau an und laden Sie sie herunter.

   ![repobrowserrelnotes](/help/release-notes/assets/repobrowserrelnotes.png)

* Die Anmeldeinformationen, die zum Authentifizieren von Server-zu-Server-API-Aufrufen verwendet werden (z. B. für GraphQL-API-Anfragen), können jetzt vor Ablauf von der Developer Console aus aktualisiert werden. Siehe [Dokumentation](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md#refresh-credentials) für weitere Informationen.

* Wartungsaufgaben für Versionsbereinigung und Auditprotokolllöschung, die zuvor nicht aktiviert waren, werden für neue Umgebungen aktiviert. Die zugehörigen Werte finden Sie in der [Wartungsaufgabe](/help/operations/maintenance.md) Artikel.

* AEM as a Cloud Service SDK Dispatcher Tools unterstützen jetzt Mac-Computer mit M1-Chip

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der monatlichen Cloud Manager-Versionen finden Sie [here](/help/implementing/cloud-manager/release-notes-cloud-manager/release-notes-cm-current.md).

## Content Transfer Tool {#ctt-release}

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.9.0 wurde am 28. Februar 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt}

* Schutzmaßnahme Größenüberprüfung: Die Funktion „Größenüberprüfung“ des Content Transfer Tools hilft bei der Reduzierung fehlgeschlagener Inhaltsübertragungen. Mit der Funktion „Größenüberprüfung“ können Benutzer 1) vor der Extraktion feststellen, ob sie über ausreichend Festplattenspeicher im `crx-quickstart`-Unterverzeichnis und 2) die Größe des Migrationssatzes schätzen und überprüfen, ob er unterstützt wird. Wenn eine oder beide dieser Prüfungen nicht bestanden werden, erhalten die Benutzer Warnungen auf der CTT-Benutzeroberfläche. Mit dieser Schutzmaßnahme können Sie Fehler bei der Inhaltsübertragung vermeiden und Migrationsoptionen proaktiv mit der Adobe-Kundenunterstützung besprechen. Weitere Informationen finden Sie unter [Bestimmen der Größe des Migrationssets und des Speicherplatzes](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/migration-journey/cloud-migration/content-transfer-tool/getting-started-content-transfer-tool.html?lang=de#migration-set-size).

## Best Practices Analyzer {#bpa-release}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.26 wurde am 16. März 2022 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa}

* Möglichkeit, nicht verarbeitete Assets zu erkennen. Wenn nicht verarbeitete Assets erkannt werden, müssen diese Assets entweder auf „Verarbeitet“ gesetzt oder während der Inhaltsübertragung aus dem Migrationssatz entfernt werden, um Probleme bei der Inhaltsaufnahme zu vermeiden.
* Möglichkeit, festzustellen, ob Inhalte über mehr als 1000 Vanity-URLs verfügen. Die Verwendung einer hohen Anzahl von Vanity-URLs empfiehlt sich nicht, da dies die Dispatcher- und Veröffentlichungs-Server belastet.
* Möglichkeit, Probleme im Zusammenhang mit Oak-Index-Definitionen zu identifizieren und Inkompatibilitäten mit AEM as a Cloud Service zu erkennen.
* Möglichkeit, die Verwendung von Externalizer-Konfigurationen zu erkennen und darüber zu berichten. In AEM as a Cloud Service werden Externalizer-Konfigurationen von Cloud Manager festgelegt. Daher müssen vorhandene Externalizer-Konfigurationen überarbeitet werden, um die Kompatibilität zu gewährleisten.

### Fehlerbehebungen {#bug-fixes-bpa}

* In einigen Szenarien konnte BPA nicht ausgeführt werden, da FormsSelectiveFeaturesAnalysis einen Assertionsfehler ausgab. Dieses Problem wurde behoben.
* BPA meldete Befunde im Zusammenhang mit dem WRK-Muster als SCHWERWIEGEND anstelle von KRITISCH. Dieses Problem wurde behoben.
* BPA meldete fälschlicherweise Befunde im Zusammenhang mit OAK-Index-Definitionen in ui.apps als KRITISCH. Dieses Problem wurde behoben
