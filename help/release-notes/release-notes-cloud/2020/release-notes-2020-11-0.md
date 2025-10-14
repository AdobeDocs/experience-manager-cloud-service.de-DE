---
title: Versionshinweise für Version 2020.11.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.11.0
exl-id: 8066c0fb-c2f5-4625-9448-b0c74ff4e192
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1223'
ht-degree: 91%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.11.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am 2. Dezember 2020 veröffentlicht.
Die folgende Version (2020.12.0) wird am 17. Dezember 2020 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* **[Hierarchieverwaltung für Launches](/help/sites-cloud/authoring/launches/managing-pages.md) und [Timewarp für Zeitpunkte in der Zukunft](/help/sites-cloud/authoring/launches/preview.md)**: Neue Benutzeroberfläche zum Hinzufügen/Entfernen von Sites innerhalb eines Launches und das Durchsuchen der Site mit Timewarp zeigt den zukünftigen Status von Launches an.

* **[Erweiterte Inhaltsfragmentmodelle und Editor](/help/assets/content-fragments/content-fragments-models.md)**: Neue Optionen für die Eingabevalidierung bei verschiedenen Datentypen, verbesserter Datentyp für Aufzählungen mit neuen Formularvisualisierungen und der Name des Inhaltsfragmentmodells wird in der Assets-Benutzeroberfläche angezeigt und ist durchsuchbar.

* **Sortieren der für den Rollout verfügbaren Live Copy-Seiten**: Neue Option zum Sortieren der für den Rollout verfügbaren Live Copy-Seiten mit den Eigenschaften [!UICONTROL Name], [!UICONTROL Letztes Änderungsdatum] und [!UICONTROL Letztes Rollout-Datum]. [!UICONTROL Letztes Rollout-Datum] für eine Seite ist eine neu eingeführte Eigenschaft.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Neue Funktionen in [!DNL Assets] und [!DNL Dynamic Media] {#what-is-new-assets}

* **Massenaufnahme von Assets**: Bieten Sie Kundinnen und Kunden einen skalierbaren, Cloud-nativen Aufnahme-Service, der [!DNL Experience Manager] as a Cloud Service-Architektur einschließlich Asset-Microservices verwendet. Zu den wichtigsten Anwendungsfällen gehört die skalierte Aufnahme mit Überwachung, Reporting und Planung, während die erstmalige Übertragung von Assets in Cloud-Datenspeicher mithilfe gängiger Cloud-Upload-Tools ermöglicht wird. Weitere Informationen finden Sie unter [Tool zur Massenaufnahme von Assets](/help/assets/add-assets.md#asset-bulk-ingestor).

  Dieses Tool ist für Systemadministratoren, Berater und Implementierungspartner gedacht. Diese Funktion ermöglicht die Aufnahme in großem Umfang und wird idealerweise bei der ersten Aufnahme oder gelegentlicher großer Aufnahme verwendet. Für kleinere Aufnahmeaufträge verwenden Sie das [[!DNL Experience Manager] Desktop-Programm](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=de) oder [laden Sie über die Assets-Benutzeroberfläche hoch](/help/assets/add-assets.md#upload-assets).

  ![Konfiguration des Massenimport-Tools](/help/assets/assets/bulk-import-config-low-res.png)

* Die Benutzer können die digitalen Assets jetzt in den Karten- und Spaltenansichten sortieren.

  ![Assets sortieren](/help/assets/assets/asset-sort-options.png)

* Die folgenden Erweiterungen werden für Barrierefreiheit in [!DNL Experience Manager Assets] in dieser Version vorgenommen. Weitere Informationen finden Sie unter [Funktionen für die Barrierefreiheit in [!DNL Assets]](/help/assets/accessibility.md).

   * Beim Navigieren in der Zeitleiste mit einer Tastatur können Sie mit der Esc-Taste die Option „Alle anzeigen“ ausblenden, ohne den Fokus zu verlieren.
   * Beim Navigieren mit der Tabulator-Taste der Tastatur behält das Tag-Feld nach dem Entfernen des letzten Tags aus den hinzugefügten Tags den Fokus.
   * [!DNL Experience Manager]-Komponenten enthalten jetzt entsprechende Informationen für Name, Rolle und Wert, die von Bildschirmlesehilfen verwendet werden können.
   * Nachdem Sie das Kombinationsfeld „Typ/Größe“, das Kombinationsfeld „Link“, das Kombinationsfeld „Sprache“ oder das Textbearbeitungsfeld gelöscht haben, kehrt der Tastaturfokus zum nächsten oder vorherigen Element der Benutzeroberfläche oder zu einem relevanteren Element der Benutzeroberfläche zurück.
   * Wenn Sie den Mauszeiger über Optionen bewegen, werden Tipps wie „Auswählen“ und „Herunterladen“ angezeigt. Benutzer, die eine Bildschirmlupe verwenden, können die Miniaturen der Dateien wegen dieser Tipps möglicherweise nicht sehen. Es ist jetzt möglich, den Fokus beizubehalten, nachdem die Option mit der `Escape`-Taste entfernt wurde.
   * Bei der Auswahl einer Rasterzelle aus dem auf der Seite vorhandenen Raster wird der Fokus auf die Aktionsleiste verschoben, die auf dem Bildschirm erscheint.
   * Visuelle Benutzer können zwischen normalem Text und einem Link unterscheiden, da visuelle Hinweise (Unterstrich und Pfeilsymbol) für Links zu allen Lösungen auf der [!DNL Experience Manager]-Startseite angezeigt werden.

* **Stapelsatzvorgaben in Dynamic Media**: Jetzt können Sie die Erstellung und Organisation mehrerer Assets in einem Bild- oder Rotationsset automatisieren, wenn Sie Asset-Dateien einzeln oder mit der Massenaufnahme in einen Ordner hochladen.

  Weitere Information finden Sie unter [Über Stapelsatzvorgaben](/help/assets/dynamic-media/batch-set-presets-dm.md).

* Die folgenden Erweiterungen für die Barrierefreiheit sind jetzt in [!DNL Dynamic Media] verfügbar:

   * Bildschirmlesehilfen (JAWS, Sprachausgabe) beschreiben den Namen, die Rolle und den Status der Menüelemente in der Menüoption „Einbettungsgröße“.
   * Benutzer können mit der `Tab`-Taste durch das Dialogfeld „E-Mail-Link“ navigieren.
   * Der Workflow zum Erstellen von Videokodierungsprofilen ist durch die Verbesserungen bei den Bildschirmlesehilfen benutzerfreundlicher geworden.
   * Beim Navigieren mit der `Tab`-Taste wird der Fokus auf die entsprechenden Elemente der Benutzeroberfläche im Workflow verschoben, um ein interaktives Video zu erstellen.
   * Die Seiten „Veröffentlichen“, „Asset bearbeiten“, „Smartes Zuschneiden bearbeiten“ und „Bildset-Editor“ wurden verbessert, um den Web-Standards zu entsprechen. Benutzende von Hilfstechnologien (Assistive Technology, AT) können jetzt einfach auf diesen Seiten navigieren und auf sie reagieren, z. B. Bilder zuschneiden.
   * Die Viewer wurden verbessert, sodass Benutzer mit der Tastatur navigieren können.
   * Benutzer, die Tastatur und Bildschirmlesehilfe verwenden, können die Funktion zum Zuschneiden verwenden.
   * Tastaturbenutzer können die Hotspots besser verwalten.

  Weitere Informationen finden Sie unter [Barrierefreiheit in [!DNL Dynamic Media]](/help/assets/dynamic-media/accessibility-dm.md).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Freigabe der CIF Venia-Referenz-Website 2020.11.05, die die aktuelle CIF-Kernkomponenten Version 1.5.0 enthält. Weitere Informationen finden Sie unter [CIF Venia](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.27)Referenz-Site .

* Version 1.5.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter {[&#128279;](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.5.0)}CIF-Kernkomponenten.

### Fehlerbehebungen {#bug-fixes-commerce}

* Die GraphQL-Client-Konfiguration wurde nicht korrekt gelesen, wenn die Konfiguration nicht direkt in der Sling CA-Konfiguration, sondern in einer der übergeordneten Konfigurationen angegeben wurde. Dieses Problem wurde behoben.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2020.11.0 von Cloud Manager in AEM as a Cloud Service wurde am 12. November 2020 veröffentlicht.

### Neue Funktionen in [!DNL Cloud Manager] {#what-is-new-cm}

* Eine neue Menüoption **Lokale Anmeldung** steht Benutzern jetzt über die Umgebungsmenüoptionen auf der Karte **Umgebungen** und auf den Zusammenfassungsseiten **Umgebungen** zur Verfügung.
Weitere Einzelheiten finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#login-locally).

* Die Registerkarte **Lernen** in Cloud Manager wurde mit neuen Bildern in der Benutzeroberfläche aktualisiert.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plug-ins.
* Über den Link in der Fußzeile von Cloud Manager zur Sprachauswahl wird jetzt an die richtige Stelle navigiert.
* Manchmal startete der SonarQube-Prozess während des Code-Scannens nicht. Dies wird nun automatisch erkannt und ein Neustart wird versucht.
* Alle vorhandenen Produktions-Pipelines werden automatisch mit dem Experience Audit-Schritt aktiviert.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Es wurde Unterstützung für die Suche nach Workflow-Instanzen basierend auf Workflow-Titel, Workflow-Modell, Status, Initiator, Payload-Pfad und Startdatum hinzugefügt. Weitere Informationen finden Sie unter [Nach Workflow-Instanzen suchen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html?lang=de).

### Synchronisierung von Benutzerdaten auf Veröffentlichungsebene {#user-sync}

* Benutzerdaten, einschließlich Profilattributen und Gruppenmitgliedschaften, können auf der Veröffentlichungsebene beibehalten werden. Weitere Informationen zu dieser Funktion finden Sie in der [Dokumentation zu Registrierung, Anmeldung und Benutzerprofil](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md).

### SDK Build Analyzer {#analyzers}

Das Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK erkennt Probleme in einem Maven-Projekt, einschließlich fehlender Abhängigkeiten. Es gibt Entwicklern die Möglichkeit, Probleme während der lokalen Entwicklung zu entdecken, lange bevor sie mit Cloud Manager in Cloud-Umgebungen bereitgestellt werden. Weitere Informationen finden Sie in der Dokumentation [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de#developing) und [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=de#building-for-the-sdk).

### Andere {#others-foundation}

Neue [&#x200B; „httpd-t“-Syntax](/help/implementing/dispatcher/disp-overview.md#local-validation) Überprüfen Sie, ob die Apache- und Dispatcher-Konfiguration während des Cloud Manager-Builds ausgeführt wird, der auch mit den Dispatcher-Tools von AEM as a Cloud Service SDK ausgeführt werden kann.

## Content Transfer Tool {#content-transfer-tool}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für [Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de) Version 1.1.12.

### Neue Funktionen {#what-is-new-ctt}

* Anwendererlebnis für Protokolle verbessert. Zeitstempel zu Extraktions- und Aufnahmeprotokollen hinzugefügt. Meldung hinzugefügt, die angibt, ob Protokolle leer sind.

### Fehlerbehebungen {#ctt-bug-fixes}

* Das Content Transfer Tool übersprang Inhaltsdateien, wenn der Migrationssatz Pfade enthielt, die teilweise ähnliche Dateinamen hatten. Dieses Problem wurde behoben.

## Best Practices Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Best Practices Analyzer wurde am 13. November 2020 veröffentlicht.

### Neue Funktionen in [!DNL Best Practices Analyzer] {#what-is-new-bpa}

* Cloud Readiness Analyzer ist jetzt Best Practices Analyzer (BPA). BPA bietet eine Best Practices-Bewertung Ihrer aktuellen AEM-Implementierung und hilft bei der Beurteilung, ob von einer vorhandenen AEM-Instanz zu AEM as a Cloud Service gewechselt werden kann.

* Es wurde ein neues Erkennungs-Tool hinzugefügt, um die Verwendung von `java.io.InputStream` zu erkennen, was Probleme verursachen kann, wenn AEM as a Cloud Service verwendet wird.

### Fehlerbehebungen {#bpa-bug-fixes}

* Fehlerkorrektur – Im Zusammenhang mit der Komponente *Foundation für Textfelder* werden keine Positivmeldungen mehr angezeigt.
