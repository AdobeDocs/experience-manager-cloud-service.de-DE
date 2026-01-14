---
title: Versionshinweise für Version 2021.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 2c72973b-5a51-4744-bf88-50da0013ba31
feature: Release Information
role: Admin
source-git-commit: 281a8efcd18920dd926d92db9c757c0513d599fd
workflow-type: tm+mt
source-wordcount: '1432'
ht-degree: 97%

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

Die Version 2021.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service wiurde am 28. Juni 2021 veröffentlicht.
Die folgende Version (2021.7.0) wurde am 29. Juli 2021 veröffentlicht.

## Video zur Version {#release-video}

Sehen Sie sich das Video [Versionsübersicht Juni 2021](https://video.tv.adobe.com/v/334296) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## XML-Dokumentation zu AEM as a Cloud Service {#xml-documentation}

### Neue Funktionen {#what-is-new-xml-documentation}

* Die XML-Dokumentation zu AEM as a Cloud Service ist jetzt allgemein verfügbar.
* Dadurch können Bestandskunden von AEM Cloud Services XML-Dokumentations-Add-ons zum Importieren, Erstellen, Verwalten und Bereitstellen von technischen Inhalten über mehrere Kanäle hinweg, einschließlich AEM Sites, erwerben.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.6.0 und 2021.5.0.

### Veröffentlichungsdatum {#release-date-june-cm}

Die Version 2021.6.0 von Cloud Manager in AEM as a Cloud Service wurde am 10. Juni 2021 veröffentlicht.
Die nächste Version ist für den 15. Juli 2021 geplant.

### Neue Funktionen {#what-is-new-junecm}

* Der Vorschau-Service wird fortlaufend für alle Programme bereitgestellt. Kundinnen und Kunden werden im Produkt benachrichtigt, wenn ihr Programm für den Vorschau-Service aktiviert ist. Weitere Informationen finden Sie unter [Zugriff auf den Vorschau-Service](/help/implementing/cloud-manager/manage-environments.md#access-preview-service).

* Maven-Abhängigkeiten, die während des Build-Schritts heruntergeladen wurden, werden jetzt zwischen Pipeline-Ausführungen zwischengespeichert. Diese Funktion wird in den nächsten Wochen für Kunden aktiviert.

* Der Name des Programms kann jetzt im Dialogfeld „Programm bearbeiten“ bearbeitet werden.

* Der standardmäßige Name der Verzweigung, der sowohl bei der Projekterstellung als auch im Standard-Push-Befehl über „Git-Workflows verwalten“ verwendet wird, wurde zu `main` geändert.

* Die Bearbeitung des Programmerlebnisses in der Benutzeroberfläche wurde aktualisiert.

* Die Qualitätsregel `ImmutableMutableMixCheck` wurde aktualisiert, um `/oak:index`-Knoten als unveränderlich zu klassifizieren.

* Die Qualitätsregeln `CQBP-84` und `CQBP-84--dependencies` wurden in einer einzigen Regel zusammengefasst. Im Rahmen dieser Konsolidierung werden beim Scannen von Abhängigkeiten Probleme in Abhängigkeiten von Drittanbietern, die in der AEM-Laufzeit bereitgestellt werden, genauer identifiziert.

* Um Verwirrung zu vermeiden, wurden die Segmentzeilen „AEM veröffentlichen“ und „Dispatcher veröffentlichen“ auf der Seite „Umgebungsdetails“ konsolidiert.

  ![Dispatcher-Umgebungen](/help/implementing/cloud-manager/release-notes/assets/aem-dispatcher.png)

* Es wurde eine neue Code-Qualitätsregel hinzugefügt, um die Struktur von `damAssetLucene`-Indizes zu überprüfen. Weitere Informationen finden Sie unter [Benutzerdefinierte DAM-Asset Lucene-Oak-Indizes](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check).

* Auf der Seite „Umgebungsdetails“ werden jetzt mehrere Domain-Namen für Publishing- und Vorschau-Services angezeigt (sofern zutreffend). Weitere Informationen finden Sie unter [Umgebungsdetails](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).

### Fehlerbehebungen {#bug-fixes-junecm}

* JCR-Knoten-Definitionen, die einen Zeilenumbruch nach dem Namen des Stammelements enthielten, werden jetzt korrekt geparst.

* Die List-Repositorys-API filtert jetzt auch gelöschte Repositorys.

* Wenn für den Zeitplanschritt ein ungültiger Wert angegeben wurde, wird jetzt die richtige Fehlermeldung angezeigt.

* Dem Benutzer wird neben einer IP-Zulassungsliste kein grüner *aktiver* Status mehr angezeigt, wenn diese Konfiguration nicht bereitgestellt wurde.

* Die Produktions-Pipeline wird nicht mehr durch Programmbearbeitungssequenzen an der Erstellung oder Bearbeitung gehindert.

* Einige Programmbearbeitungssequenzen konnten dazu führen, dass auf der Seite **Überblick** eine irreführende Meldung angezeigt wurde, die besagt, dass die Programmeinrichtung erneut auszuführen ist.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#ga-features-assets}

* Mit der Funktion zur Inhaltsautomatisierung können [!DNL Experience Manager Assets] die [!DNL Adobe Creative Cloud]-APIs verwenden, um die Asset-Produktion skaliert zu automatisieren. Die Inhaltsgeschwindigkeit wird verbessert, indem die zum Erstellen von Varianten desselben Assets erforderliche Zeit erheblich verkürzt und Iterationen reduziert werden. Die Funktion erfordert keinen Code und funktioniert innerhalb des DAM.
* [!DNL Adobe Asset Link] v3.0 für [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] und [!DNL Adobe InDesign] und [!DNL Adobe Asset Link] v2.0 für [!DNL Adobe XD] wurde veröffentlicht. Es bietet:

   * Unterstützung für [!DNL Assets Essentials].
   * Die Möglichkeit, automatisch eine Verbindung zu [!DNL Experience Manager] as a [!DNL Cloud Service] oder [!DNL Assets Essentials] herzustellen.

<!-- TBD: Checking with PMs if AAE release should be mentioned here.
-->

### Neue Funktionen im Kanal der Vorabversion von [!DNL Assets] {#beta-features-assets}

* Die Anzeigeeinstellungen wurden verbessert, sodass Benutzer eine Standardansicht und einen standardmäßigen Sortierparameter wählen können.
* Die Funktion für den Linkshare-Download verwendet asynchrone Downloads, die die Download-Geschwindigkeit erhöhen.
* Benutzer können die Ordner anhand von Eigenschaftsprädikaten suchen und filtern.
* [!DNL Experience Manager Assets] bettet den von [!DNL Adobe Document Cloud] unterstützten PDF-Viewer ein, um die unterstützten Dokumente in der Vorschau anzuzeigen. Mit dieser Funktion können Benutzer eine Vorschau von PDF- und anderen mehrseitigen Dateien ohne komplexe Verarbeitung anzeigen. Dadurch wird die Funktionsparität mit [!DNL Experience Manager] 6.5 verbessert.

### Fehlerbehebungen in [!DNL Assets] {#bugs-fixed-assets}

* Wenn Sie einen Eigentümer zu einem Unterordner hinzufügen, fügt [!DNL Assets] nicht mehr denselben Benutzer als Eigentümer des übergeordneten Ordners hinzu. (CQ-4323737)
* Wenn ein Benutzer beim Hinzufügen von Assets zu Sammlungen einen Filter auf die Sammlungssuche anwendet, kann der Benutzer die Sammlungen jetzt in der Listenansicht anzeigen. (CQ-4323181)
* Wenn der Benutzer bei der Suche nach Dateien und Ordnern einen Filter anwendet und [!UICONTROL Dateien und Ordner] auswählt, wird jetzt neben den Dateien auch der Ordner angezeigt. (CQ-4319543)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#ga-features-sites}

* „In der Vorschau-Ebene veröffentlichen“ wird jetzt in der Admin-Benutzeroberfläche von Sites als Seitenstatus angezeigt.
* „In der Vorschau-Ebene veröffentlichen“ zeigt jetzt die Vorschau-URL am Ende der Aktion an und speichert die URL in den Seiteneigenschaften für eine spätere Referenz.

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* Benutzerdefinierte Spalten im AEM-Posteingang können jetzt gefiltert werden.
* Es wurde die Möglichkeit hinzugefügt, den Design-Editor und die Stilebene des Editors für adaptive Formulare zu verwenden, um die Captcha-Komponente zu gestalten.
* Verbesserte Geschwindigkeit und Genauigkeit bei der automatischen Erkennung logischer Abschnitte in den Quell-PDF-Formularen und Konvertieren dieser Abschnitte in entsprechende Bedienfelder adaptiver Formulare.
* Eine Aktion zum Verschieben von PDF- oder XDP-Dateien von einem Ordner in einen anderen wurde hinzugefügt.

### Beta-Funktion von [!DNL Forms]  {#what-is-new-forms-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: Mithilfe von Kommunikations-APIs können Sie XDP-Vorlagen und XML-Daten kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Anwendungen mit folgenden Funktionen erstellen:
   * Erzeugen fertiger Formulardokumente durch Füllen von Vorlagendateien mit XML-Daten
   * Erzeugen Sie Ausgabeformulare in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckdatenströme.
   * Erzeugen von druckbaren PDFs aus einem XFA-Formular-PDF und Adobe Acrobat-Formular (AcroForm).

* **Variablendaten-Externalizer**: Sie können Daten von AEM-Workflow-Variablen in einem externen Speichersystem speichern, das von Ihrer Organisation verwaltet wird.

Sie können an [!DNL formscsbeta@adobe.com] schreiben, um sich für das Beta-Programm anzumelden.

### Fehlerbehebungen in [!DNL Forms] {#forms-bugs-fixed}

* Wenn ein Feld vor dem Senden von Daten an den Backend-Service über das Formulardatenmodell (FDM) validiert wird, sind die Validierungen erfolgreich, und der Formulardatenmodell-Service kann die Nachvalidierung jetzt auch aufrufen.
* Wenn Sie ein Formular mit einem standardmäßigen HTML-Upload-Feld von einem Apple iOS-Gerät senden, wird der Inhalt der Datei jetzt zuverlässig gesendet. Dies ist ein bekanntes Problem in Apple iOS. [FB9117687](https://feedbackassistant.apple.com/feedback/9117687)

## [!DNL Experience Manager Screens] as a [!DNL Cloud Service] {#screens}

In diesem Abschnitt finden Sie die Versionshinweise für AEM Screens as a Cloud Service.

### Veröffentlichungsdatum {#release-date-june-screens}

Das Veröffentlichungsdatum für AEM Screens as a Cloud Service war 24. Juni 2021.

### Neue Funktionen {#what-is-new-screens-june}

>[!NOTE]
>Unter [Handbuch für AEM Screens as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/screens-as-cloud-service/home.html?lang=de) finden Sie Grundlagenkenntnisse, die für die erfolgreiche Installation, Konfiguration und Ausführung von Screens as a Cloud Service erforderlich sind, sowie Links zu die ausführlichen technischen Dokumentationen zu Konzepten.

* Die Verwaltung der Massenregistrierung von Geräten bedeutet, dass die Bereitstellung sehr großer Mengen von Player-Geräten schneller und effizienter ist.

* Verbesserte Such- und Filteroptionen für die Bestandsansichten „Gerät“, „Display“ und „Kanal“.

* Die Momentaufnahme des Gerätezustands spart Zeit, da sie kritische Status auf einen Blick zeigt.

* Die Seite „Objektdetails“ bietet eine Zusammenfassung der relevantesten Informationen für jedes Objekt in Ihrem Projekt.

## CIF-Add-on {#cloud-services-cif}

### Neue Funktionen {#what-is-new-cif}

* Neue CIF-Produkt- und Kategoriereferenzdatentypen für Inhaltsfragmente (inkl. Benutzeroberflächenunterstützung für Produkt-/Kategorieauswahl)
* Neue Commerce-Inhaltsfragment-Kernkomponente
* Im AEM-Backend unterstützte E-Commerce-Volltext-Suche
* Commerce-Kernkomponenten unterstützen die Datenerfassung in Adobe Commerce AI Recs .
* Verbesserte SEO-freundliche URLs für Kategorieseiten
* Unterstützung benutzerdefinierter HTTP-Header pro Website/Konfiguration

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Das Content Transfer Tool 1.5.4 wurde am 28. Juni 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-latest}

* Unterstützung für einen optionalen Schritt [Vorab-Kopie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/handling-large-content-repositories.html?lang=de) zur Verwendung mit CTT wurde hinzugefügt. Der Schritt „Vorab-Kopie“ kann verwendet werden, um die Extraktions- und Aufnahmephasen der Inhaltstransferaktivität erheblich zu beschleunigen, wenn die Quell-AEM-Instanz für die Verwendung eines Amazon S3- oder Azure Blob Storage-Datenspeichers konfiguriert ist.

* Eine Schutzmaßnahme wurde zu CTT hinzugefügt, um zu verhindern, dass Benutzer die Aufnahme stoppen und möglicherweise Daten beschädigen, sobald sie während der Aufnahmephase den kritischen Punkt erreicht hat.

* Extraktionsprotokolle wurden beschreibender gestaltet, um die Fehlerbehebung zu unterstützen.

* In der Benutzeroberfläche wurden besser beschreibende Statusmeldungen zur Aufnahme hinzugefügt.

### Fehlerbehebungen {#bug-fixes-ctt-latest}

* Beim Stoppen einer Aufnahme in der Autoreninstanz hatte die Benutzeroberfläche eine zuvor abgeschlossene Aufnahme in der Veröffentlichungsinstanz für `STOPPED` von `FINISHED` aus überschrieben. Dieses Problem wurde behoben.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer 2.1.16 wurde am 30. Juni 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-bpa-latest}

* Die Möglichkeit, fehlende untergeordnete Knoten in Ordnern unter `/content/dam` zu erkennen und darüber zu berichten.

* Die Möglichkeit, die verwendete Version von Best Practices Analyzer zu erkennen und darüber zu berichten.

### Fehlerbehebungen {#bug-fixes-bpa-latest}

* die Protokollierung in Zusammenhang mit nicht unterstützten Repository Structure (URS) funktioniert jetzt fehlerfrei.
