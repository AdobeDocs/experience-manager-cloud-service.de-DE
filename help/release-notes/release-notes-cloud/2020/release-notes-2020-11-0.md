---
title: Versionshinweise für die Version 2020.11.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.11.0
translation-type: tm+mt
source-git-commit: c0db892d58f762bd5659596371ece86950e9cdd7
workflow-type: tm+mt
source-wordcount: '1269'
ht-degree: 13%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] als Cloud Service beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!DNL Adobe Experience Manager] als Cloud Service 2020.11.0 ist der 2. Dezember 2020.
Die folgende Version (2020.12.0) wird am 17. Dezember 2020 veröffentlicht

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* **[Startet Hierarchieverwaltung](/help/sites-cloud/authoring/launches/managing-pages.md)  und  [zukünftigen Timewarp](/help/sites-cloud/authoring/launches/preview.md)**: Die neue Benutzeroberfläche zum Hinzufügen/Entfernen von Seiten während eines Starts und das Browsen der Site mit &quot;Zeitverkrümmung&quot;zeigt den Zukunftsstatus von Launches an.

* **[Erweiterte Inhaltsfragmentmodelle und Editor](/help/assets/content-fragments/content-fragments-models.md)**: Neue Optionen für die Eingabevalidierung für verschiedene Datentypen, verbesserter Datentyp für Auflistungen mit neuen Formularvisualisierungen und der Name des Inhaltsfragmentmodells wird in der Benutzeroberfläche &quot;Assets&quot;angezeigt und kann durchsucht werden.

* **Sortieren Sie die für die Aktualisierung** verfügbaren Live Copy-Seiten: Neue Option zum Sortieren der für die Aktualisierung verfügbaren Live Copy-Seiten mit den  [!UICONTROL Dateneigenschaften &quot;Name]&quot;, &quot; [!UICONTROL Zuletzt geändert&quot;] und &quot; [!UICONTROL Letzte ] Aktualisierung&quot;. Das [!UICONTROL Letzte Rollout-Datum] für eine Seite ist eine neue Eigenschaft eingeführt.

## [!DNL Adobe Experience Manager Assets] als Cloud Service  {#assets}

### Neue Funktionen in [!DNL Assets] und [!DNL Dynamic Media] {#what-is-new-assets}

* **Erfassung** von Massenelementen: Bieten Sie Kunden einen skalierbaren, Cloud-nativen Erfassungsdienst an, der  [!DNL Experience Manager] als Cloud Service-Architektur einschließlich Asset-Mikrodiensten genutzt wird. Zu den wichtigsten Anwendungsfällen zählen die Erfassung im Maßstab mit Überwachung, Berichte und Planung, während gleichzeitig die erstmalige Übertragung von Assets an Cloud-Datenspeicher mithilfe der üblichen Cloud-Upload-Werkzeuge ermöglicht wird. Siehe [Asset Bulk Ingestor Tool](/help/assets/add-assets.md#asset-bulk-ingestor).

   Dieses Tool richtet sich an Systemadministratoren, Berater oder Implementierungspartner. Diese Funktion ermöglicht eine großflächige Aufnahme und wird ideal bei der anfänglichen Aufnahme oder gelegentlichen großen Aufnahme verwendet. Für kleinere Erfassungsaufträge verwenden Sie die [[!DNL Experience Manager] Desktop-App](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/introduction.html?lang=de) oder [Hochladen mit der Assets-Benutzeroberfläche](/help/assets/add-assets.md#upload-assets).

   ![Konfiguration des Massen-Importeurs](/help/assets/assets/bulk-import-config-low-res.png)

* Die Benutzer können die digitalen Assets jetzt in den Ansichten &quot;Karte&quot;und &quot;Spalte&quot;sortieren.

   ![Assets sortieren](/help/assets/assets/asset-sort-options.png)

* Die folgenden Erweiterungen werden für Barrierefreiheit in [!DNL Experience Manager Assets] in dieser Version vorgenommen. Weitere Informationen finden Sie unter [Barrierefreiheitsfunktionen in [!DNL Assets]](/help/assets/accessibility.md).

   * Beim Navigieren in der Zeitleiste mit einer Tastatur kann die Esc-Taste die Option &quot;Alle anzeigen&quot;ausblenden, ohne den Fokus zu verlieren.
   * Beim Navigieren mit der Tabulatortaste für die Tastatur bleibt der Fokus beim Entfernen des letzten Tags aus den hinzugefügten Tags erhalten.
   * [!DNL Experience Manager] Komponenten enthalten nun die entsprechenden Informationen für Namen, Rollen und Werte, die von Bildschirmlesehilfen verwendet werden sollen.
   * Nachdem Sie das Kombinationsfeld &quot;Typ/Größe&quot;, das Kombinationsfeld &quot;Verknüpfen&quot;, das Sprachkombinationsfeld oder das Textfeld zum Bearbeiten von Text gelöscht haben, kehrt der Tastaturfokus zu den nächsten oder vorherigen Elementen der Benutzeroberfläche oder zu einem relevanteren Element der Benutzeroberfläche zurück.
   * Wenn Sie den Mauszeiger über Optionen bewegen, werden Tipps wie &quot;Auswählen&quot;und &quot;Herunterladen&quot;angezeigt. Benutzer, die eine Vergrößerung verwenden, sehen aufgrund dieser Tipps möglicherweise keine Dateiminiaturen. Jetzt ist es möglich, den Fokus beizubehalten, nachdem die Option mit der `Escape`-Taste entfernt wurde.
   * Wenn Sie eine Rasterzelle aus dem Raster auf der Seite auswählen, wird der Fokus auf die Aktionsleiste verschoben, die auf dem Bildschirm angezeigt wird.
   * Visuelle Benutzer können zwischen normalem Text und einem Link unterscheiden, da visuelle Hinweise (Unterstreichung und Chevron-Symbol) für Links zu allen Lösungen in der [!DNL Experience Manager]-Startseite angezeigt werden.

* **Stapelsatzvorgaben in Dynamic Media**: Jetzt können Sie die Erstellung und Organisation mehrerer Assets in einem Bildsatz oder Rotationsset automatisieren, wenn Sie Asset-Dateien einzeln oder mit Massenaufnahmen in einen Ordner hochladen.

   Siehe [Stapelsatzvorgaben](/help/assets/dynamic-media/batch-set-presets-dm.md).

* Die folgenden Barrierefreiheitsverbesserungen sind jetzt in [!DNL Dynamic Media] verfügbar:

   * Bildschirmlesehilfen (JAWS, Erzähler) beschreiben den Namen, die Rolle und den Status der Menüelemente in der Menüoption &quot;Größe einbetten&quot;.
   * Benutzer können mit der `Tab`-Taste durch das Dialogfeld &quot;E-Mail-Link&quot;navigieren.
   * Der Arbeitsablauf zum Erstellen von Videokodierungs-Profilen ist benutzerfreundlicher, da die Bildschirmlesehilfe verbessert wurde.
   * Beim Navigieren mit der `Tab`-Taste wird der Fokus auf die entsprechenden Elemente der Benutzeroberfläche im Workflow verschoben, um ein interaktives Video zu erstellen.
   * Die Seiten &quot;Veröffentlichen&quot;, &quot;Asset bearbeiten&quot;, &quot;Smart Crops bearbeiten&quot;und &quot;Bildsatz-Editor&quot;wurden verbessert, um Webstandards zu entsprechen. Hilfstechnologie (AT)-Benutzer können nun einfach durch diese Seiten navigieren und Aktionen wie das Beschneiden von Bildern ausführen.
   * Die Viewer wurden verbessert, sodass Benutzer mit der Tastatur navigieren können.
   * Die Benutzer der Tastatur und der Bildschirmlesehilfe können die Funktion zum Beschneiden verwenden.
   * Die Tastaturbenutzer können die Hotspots besser verwalten.

   Siehe [Barrierefreiheit in [!DNL Dynamic Media]](/help/assets/dynamic-media/accessibility-dm.md).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* CIF Venia-Referenzseite - 2020.11.05, die die aktuellste CIF-Core-Komponenten Version v1.5.0 enthält. Weitere Informationen finden Sie unter [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.27).

* Version 1.5.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.5.0).

### Fehlerbehebungen {#bug-fixes-commerce}

* Die Konfiguration des GraphQL-Clients wurde nicht korrekt gelesen, wenn die Konfiguration nicht direkt in der Sling CA-Konfiguration, sondern in einer der übergeordneten Konfigurationen angegeben wurde. Das wurde behoben.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.11.0 ist der 12. November 2020.

### Neue Funktionen in [!DNL Cloud Manager] {#what-is-new-cm}

* Eine neue Menüoption **Lokale Anmeldung** steht nun Benutzern über die Menüoptionen &quot;Umgebung&quot;auf den Zusammenfassungsseiten **Umgebung** und **Umgebung** zur Verfügung.
Weitere Informationen finden Sie unter [Verwalten von Umgebungen](/help/implementing/cloud-manager/manage-environments.md##login-locally).

* Die Registerkarte **Lernen** in Cloud Manager wurde mit neuen Bildern in der Benutzeroberfläche aktualisiert.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plug-ins.
* Über den Link in der Fußzeile von Cloud Manager zur Sprachauswahl wird jetzt an die richtige Stelle navigiert.
* Manchmal startete der SonarQube-Prozess während des Code-Scannens nicht. Dies wird nun automatisch erkannt und ein Neustart wird versucht.
* Alle vorhandenen Produktionslinien werden automatisch mit dem Experience Audit-Schritt aktiviert.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Es wurde Unterstützung für die Suche von Workflow-Instanzen auf Grundlage von Workflow-Titel, Workflow-Modell, Status, Initiator, Nutzlastpfad und Beginn-Datum hinzugefügt. Siehe [Instanzen des Sucharbeitsablaufs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html).

### Synchronisierung von Benutzerdaten auf Veröffentlichungsebene {#user-sync}

* Benutzerdaten, einschließlich Profil- und Gruppenattributen, können auf der Veröffentlichungsebene beibehalten werden. Weitere Informationen zu dieser Funktion finden Sie in der [Profil-, Anmelde- und Benutzerdokumentation](/help/sites-cloud/authoring/personalization/user-and-group-sync-for-publish-tier.md).

### SDK Build Analyzers {#analyzers}

Das AEM als Cloud Service SDK Build Analyzer Maven Plugin erkennt Probleme in einem Maven-Projekt, einschließlich fehlender Abhängigkeiten. Es bietet Entwicklern die Möglichkeit, Probleme während der lokalen Entwicklung zu erkennen, lange vor der Bereitstellung in Cloud-Umgebung mit Cloud Manager. Weitere Informationen finden Sie in der Dokumentation [hier](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=en#developing) und [hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=en#building-for-the-sdk).

### Andere {#others-foundation}

Neue Syntax [&quot;httpd -t&quot;](/help/implementing/dispatcher/disp-overview.md#local-validation) sucht nach Apache- und Dispatcher-Konfiguration, die während der Cloud Manager-Erstellung ausgeführt wird. Diese kann auch mit AEM als Cloud Service-SDKs Dispatcher Tools ausgeführt werden.

## Content Transfer-Tool {#content-transfer-tool}

Folgen Sie diesem Abschnitt, um mehr über die neuen Funktionen und die Aktualisierungen für [Content Transfer Tool](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12 zu erfahren.

### Neue Funktionen {#what-is-new-ctt}

* Benutzerfreundlichkeit für Protokolle verbessert. Zeitstempel zu Extraktionen- und Ingestion-Protokollen hinzugefügt. Meldung hinzugefügt, die angibt, ob die Protokolle leer sind.

### Fehlerbehebungen {#ctt-bug-fixes}

* Content Transfer Tool übersprungen Inhaltsdateien, wenn der Migrationssatz Pfade mit teilweise ähnlichen Dateinamen enthielt. Das wurde behoben.

## Best Practices-Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Das Veröffentlichungsdatum für Best Practices Analyzer ist der 13. November 2020.

### Neue Funktionen in [!DNL Best Practices Analyzer] {#what-is-new-bpa}

* Cloud Readiness Analyzer ist jetzt Best Practices Analyzer (BPA). BPA bietet eine Best Practices-Bewertung Ihrer aktuellen AEM-Implementierung und hilft bei der Beurteilung der Bereitschaft, von einer vorhandenen AEM zu AEM als Cloud Service zu wechseln.

* Ein neuer Detektor wurde hinzugefügt, um die Verwendung von `java.io.InputStream` zu erkennen, was Probleme verursachen kann, wenn AEM als Cloud Service verwendet wird.

### Fehlerbehebungen {#bpa-bug-fixes}

* Es wurde ein Fehler behoben, der dazu führte, dass die Positivwerte für die Komponente *textfield foundation* behoben wurden.
