---
title: Versionshinweise für Version 2021.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: dcc598b565dfeeb7c5f62671edc8b256b60d9ec4
workflow-type: tm+mt
source-wordcount: '1440'
ht-degree: 25%

---


# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.6.0 von [!DNL Adobe Experience Manager] wurde am 28. Juni 2021 veröffentlicht.
Die folgende Version (2021.7.0) wird am 29. Juli 2021 veröffentlicht.

## Release Video {#release-video}

Sehen Sie sich das Video [Versionsübersicht vom Juni 2021](https://video.tv.adobe.com/v/334296) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## XML-Dokumentation für AEM as a Cloud Service {#xml-documentation}

### Neue Funktionen {#what-is-new-xml-documentation}

* Die XML-Dokumentation für AEM als Cloud Service ist jetzt allgemein verfügbar.
* Dadurch können Bestandskunden von AEM Cloud Services XML-Dokumentations-Add-ons zum Importieren, Erstellen, Verwalten und Bereitstellen von technischen Inhalten über mehrere Kanäle hinweg abrufen, einschließlich AEM Sites

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.6.0 und 2021.5.0.

### Veröffentlichungsdatum {#release-date-june-cm}

Die Version 2021.6.0 von Cloud Manager in AEM wurde am 10. Juni 2021 veröffentlicht.
Die nächste Version ist für den 15. Juli 2021 geplant.

### Neue Funktionen {#what-is-new-junecm}

* Der Vorschaudienst wird fortlaufend für alle Programme bereitgestellt. Kunden werden im Produkt benachrichtigt, wenn ihr Programm für den Vorschaudienst aktiviert ist. Weitere Informationen finden Sie unter [Zugriff auf den Vorschaudienst](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) .

* Maven-Abhängigkeiten, die während des Build-Schritts heruntergeladen wurden, werden jetzt zwischen Pipeline-Ausführungen zwischengespeichert. Diese Funktion wird in den nächsten Wochen für Kunden aktiviert.

* Der Name des Programms kann jetzt im Dialogfeld Programm bearbeiten bearbeitet werden.

* Der standardmäßige Name der Verzweigung, der sowohl bei der Projekterstellung als auch im Standard-Push-Befehl über „Git-Workflows verwalten“ verwendet wird, wurde zu `main` geändert.

* Die Bearbeitung des Programmerlebnisses in der Benutzeroberfläche wurde aktualisiert.

* Die Qualitätsregel `ImmutableMutableMixCheck` wurde aktualisiert, um `/oak:index`-Knoten als unveränderlich zu klassifizieren.

* Die Qualitätsregeln `CQBP-84` und `CQBP-84--dependencies` wurden in einer einzigen Regel zusammengefasst. Im Rahmen dieser Konsolidierung werden beim Überprüfen von Abhängigkeiten Probleme in Abhängigkeiten von Drittanbietern genauer identifiziert, die zur AEM-Laufzeit bereitgestellt werden.

* Um Verwirrung zu vermeiden, wurden die Segmentzeilen Veröffentlichen AEM und Veröffentlichen des Dispatchers auf der Seite Umgebungsdetails konsolidiert.

   ![](/help/onboarding/release-notes-cloud-manager/assets/aem-dispatcher.png)

* Es wurde eine neue Code-Qualitätsregel hinzugefügt, um die Struktur von `damAssetLucene` -Indizes zu überprüfen. Weitere Informationen finden Sie unter [Benutzerdefinierte DAM-Asset Lucene Oak-Indizes](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) .

* Auf der Seite &quot;Umgebungsdetails&quot;werden jetzt mehrere Domänennamen für Veröffentlichungs- und Vorschaudienste angezeigt (sofern zutreffend). Weitere Informationen finden Sie unter [Umgebungsdetails](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) .

### Fehlerbehebungen {#bug-fixes-junecm}

* JCR-Knoten-Definitionen, die einen Zeilenumbruch nach dem Namen des Stammelements enthielten, werden jetzt korrekt geparst.

* Die List-Repositorys-API filtert jetzt auch gelöschte Repositorys.

* Wenn für den Zeitplanschritt ein ungültiger Wert angegeben wurde, wird jetzt die richtige Fehlermeldung angezeigt.

* Gelegentlich kann der Benutzer neben einer IP-Zulassungsliste den grünen Status *active* sehen, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Einige Programmbearbeitungssequenzen können dazu führen, dass die Produktions-Pipeline nicht erstellt oder bearbeitet werden kann.

* Einige Programmbearbeitungssequenzen können dazu führen, dass auf der Seite **Übersicht** eine irreführende Meldung angezeigt wird, um die Programmeinrichtung erneut auszuführen.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#ga-features-assets}

* Mit der Funktion zur Inhaltsautomatisierung kann [!DNL Experience Manager Assets] die [!DNL Adobe Creative Cloud]-APIs nutzen, um die Asset-Produktion skaliert zu automatisieren. Die Geschwindigkeit von Inhalten wird verbessert, indem die zum Erstellen von Varianten desselben Assets erforderliche Zeit und Iterationen erheblich verkürzt werden. Die Funktion erfordert keinen Code und funktioniert innerhalb des DAM.
* [!DNL Adobe Asset Link] v3.0 für  [!DNL Adobe Photoshop],  [!DNL Adobe Illustrator]und  [!DNL Adobe InDesign] und  [!DNL Adobe Asset Link] v2.0 für  [!DNL Adobe XD] wird veröffentlicht. Er bietet:

   * Unterstützung für [!DNL Assets Essentials].
   * Möglichkeit, automatisch eine Verbindung zu [!DNL Experience Manager] als [!DNL Cloud Service] oder [!DNL Assets Essentials] herzustellen.

<!-- TBD: Checking with PMs if AAE release should be mentioned here.
-->

### Neue Funktionen im Kanal [!DNL Assets] der Vorabversion {#beta-features-assets}

* Die Anzeigeeinstellungen wurden verbessert, sodass Benutzer eine Standardansicht und einen standardmäßigen Sortierparameter wählen können.
* Die Funktion für den Linkshare-Download verwendet asynchrone Downloads, die die Download-Geschwindigkeit erhöhen.
* Benutzer können die Ordner anhand von Eigenschaftsprädikaten suchen und filtern.
* [!DNL Experience Manager Assets] bettet den PDF-Viewer, der von bereitgestellt wird,  [!DNL Adobe Document Cloud] ein, um die unterstützten Dokumente in der Vorschau anzuzeigen. Mit dieser Funktion können Benutzer eine Vorschau von PDF- und anderen mehrseitigen Dateien ohne komplexe Verarbeitung anzeigen. Dadurch wird die Funktionsparität mit [!DNL Experience Manager] 6.5 verbessert.

### Fehlerbehebungen in [!DNL Assets] {#bugs-fixed-assets}

* Wenn Sie einen Eigentümer zu einem Unterordner hinzufügen, fügt [!DNL Assets] auch denselben Benutzer als Eigentümer des übergeordneten Ordners hinzu. (CQ-4323737)
* Wenn ein Benutzer beim Hinzufügen von Assets zu Sammlungen einen Filter auf die Sammlungssuche anwendet, kann der Benutzer die Sammlungen nicht in der Listenansicht anzeigen. (CQ-4323181)
* Wenn der Benutzer bei der Suche nach Dateien und Ordnern einen Filter anwendet und [!UICONTROL Dateien und Ordner] auswählt, werden nur die Dateien angezeigt, nicht jedoch der Ordner. (CQ-4319543)

## [!DNL Experience Manager Sites] as a  [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#ga-features-sites}

* In der Vorschau-Ebene veröffentlichen wird jetzt in der Sites Admin-Benutzeroberfläche als Seitenstatus angezeigt
* In der Vorschau veröffentlichen : Statusvorschau-URL wird nun am Ende der Aktion angezeigt und die URL wird in den Seiteneigenschaften beibehalten, um später darauf zu verweisen

## [!DNL Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* Benutzerdefinierte Spalten können jetzt im Posteingang AEM gefiltert werden.
* Es wurde die Möglichkeit hinzugefügt, den Design-Editor und die Stilschicht des adaptiven Formular-Editors zu verwenden, um die Captcha-Komponente zu gestalten.
* Verbesserte Geschwindigkeit und Genauigkeit für die automatische Erkennung logischer PDF forms und deren Konvertierung in entsprechende adaptive Formularbereiche.
* Aktion zum Verschieben von PDF- oder XDP-Dateien von einem Ordner in einen anderen hinzugefügt.

### Beta-Funktion von [!DNL Forms] {#what-is-new-forms-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: Mithilfe von Kommunikations-APIs können Sie XDP-Vorlagen und XML-Daten kombinieren, um Druckdokumente in verschiedenen Formaten zu generieren. Mit dem Dienst können Sie Dokumente im synchronen Modus generieren. Mit den APIs können Sie Anwendungen erstellen, mit denen Sie:
   * Generieren fertiger Formulardokumente durch Füllen von Vorlagendateien mit XML-Daten
   * Generieren Sie Ausgabeformulare in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckströme.
   * Generieren Sie druckbare PDFs aus einem XFA-Formular-PDF und Adobe Acrobat-Formular (AcroForm).

* **Variablendaten-Externalizer**: Sie können Daten vom AEM-Workflow-Variablen in einem externen Speichersystem speichern, das von Ihrem Unternehmen verwaltet wird.

Sie können [!DNL formscsbeta@adobe.com] schreiben, um sich für das Betaprogramm anzumelden.

### Fehlerbehebungen in [!DNL Forms] {#forms-bugs-fixed}

* Wenn ein Feld vor dem Senden von Daten an den Backend-Dienst über das Formulardatenmodell (FDM) validiert wird, sind die Validierungen erfolgreich, aber der Formulardatenmodelldienst kann die Nachvalidierung nicht aufrufen.
* Wenn Sie ein Formular mit einem standardmäßigen HTML-Upload-Feld von einem Apple iOS-Gerät senden, wird manchmal der Inhalt der Datei nicht gesendet und am anderen Ende wird eine 0-Byte-Datei empfangen. Dies ist ein bekanntes Problem in Apple iOS. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

## [!DNL Experience Manager Screens] as a  [!DNL Cloud Service] {#screens}

In diesem Abschnitt werden die Versionshinweise für AEM Screens as a Cloud Service beschrieben.

### Veröffentlichungsdatum {#release-date-june-screens}

Die Version von AEM Screens as a Cloud Service wurde am 24. Juni 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-screens-june}

>[!NOTE]
>Grundlagenkenntnisse, die für die erfolgreiche Installation, Konfiguration und Ausführung von Screens als Cloud Service erforderlich sind, finden Sie unter [Handbuch für AEM Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/home.html?lang=de) und verlinken Sie die ausführliche technische Dokumentation zu Konzepten.

* Die Massenregistrierung von Geräten bedeutet, dass die Bereitstellung massiver Mengen von Player-Geräten schneller und effizienter ist.

* Verbesserte Such- und Filteroptionen für die Inventaransichten &quot;Gerät&quot;, &quot;Anzeige&quot;und &quot;Kanal&quot;.

* Die Momentaufnahme der Gerätegesundheit spart Zeit, da sie einen kritischen Status als Überblick bietet.

* Die Seite &quot;Objektdetails&quot;bietet eine Zusammenfassung der relevantesten Informationen für jedes Objekt in Ihrem Projekt.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue CIF-Produkt- und Kategoriereferenzdatentypen für Inhaltsfragmente (inkl. Benutzeroberflächenunterstützung für Produkt-/Kategorieauswahl
* Neue Commerce-Inhaltsfragment-Kernkomponente
* Im AEM Backend unterstützte Volltext-Commerce-Suche
* Commerce-Kernkomponenten unterstützen die Adobe Commerce Sensei Recs-Datenerfassung
* Verbesserte SEO-freundliche URLs für Kategorieseiten
* Unterstützung benutzerdefinierter HTTP-Header pro Site/Konfiguration

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.5.4 des Content Transfer Tool wurde am 28. Juni 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-latest}

* Unterstützung für einen optionalen Schritt [pre-copy](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=en) zur Verwendung mit CTT hinzugefügt. Der Schritt &quot;Vorab-Kopie&quot;kann verwendet werden, um die Extraktions- und Aufnahmephasen der Inhaltstransferaktivität erheblich zu beschleunigen, wenn die Quell-AEM-Instanz für die Verwendung eines Amazon S3- oder Azure Blob Storage-Datenspeichers konfiguriert ist.

* Eine Schutzmaßnahme wurde zu CTT hinzugefügt, um zu verhindern, dass Benutzer die Aufnahme stoppen und möglicherweise Daten beschädigen, sobald sie während der Aufnahmephase den kritischen Punkt erreicht haben.

* Extraktionsprotokolle wurden beschreibender gestaltet, um die Fehlerbehebung zu unterstützen.

* In der Benutzeroberfläche wurden beschreibende Statusmeldungen zur Aufnahme hinzugefügt.

### Fehlerbehebungen {#bug-fixes-ctt-latest}

* Beim Beenden einer Aufnahme in der Autoreninstanz hat die Benutzeroberfläche eine zuvor abgeschlossene Aufnahme in der Veröffentlichungsinstanz von `FINISHED` in `STOPPED` überschrieben. Dieses Problem wurde behoben.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Die Version 2.1.16 von Best Practices Analyzer wurde am 30. Juni 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa-latest}

* Möglichkeit, fehlende untergeordnete Knoten in Ordnern unter `/content/dam` zu erkennen und darüber zu berichten.

* Möglichkeit, die verwendete Version von Best Practices Analyzer zu erkennen und darüber zu berichten.

### Fehlerbehebungen {#bug-fixes-bpa-latest}

* Fehler bei der Protokollierung in Zusammenhang mit nicht unterstützten Repository Structure (URS) behoben.

