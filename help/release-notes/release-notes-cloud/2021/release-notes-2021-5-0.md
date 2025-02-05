---
title: Versionshinweise für Version 2021.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 3f9d7339-7e37-4702-821e-f2b03cd7e224
feature: Release Information
role: Admin
source-git-commit: 10580c1b045c86d76ab2b871ca3c0b7de6683044
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 92%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am 27. Mai 2021 veröffentlicht.
Die folgende Version (2021.6.0) wird am 28. Juni 2021 veröffentlicht.

## AEM as a Cloud Service Foundation {#foundation}

### Neue Funktionen in Adobe Experience Manager as a Cloud Service Foundation {#what-is-new-foundation}

* [Vorabveröffentlichungskanal](/help/release-notes/prerelease.md): Sehen Sie sich kommende Funktionen einen ganzen Monat vor deren Veröffentlichung in der Vorschau an.

* [Veraltete APIs](/help/release-notes/deprecated-removed-features.md): Die neueste Liste der veralteten APIs für Adobe Experience Manager as a Cloud Service ist verfügbar.

* [Build Analyzer-Maven-Plug-in des AEM as a Cloud Service-SDK](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html?lang=de): Aktualisieren Sie Ihre Maven-Projekte auf die neueste Version, die eine Prüfung auf veraltete Java-APIs sowie weitere Verbesserungen umfasst.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* In Kürze können Sie Inhalte in einer neuen [Vorschaustufe](/help/sites-cloud/authoring/sites-console/previewing-content.md) zu überprüfen, um die endgültige Gestaltung von Erlebnissen so zu simulieren, wie Sie es in der Veröffentlichungsstufe tun würden. Dies wird vom Assistent zum Verwalten von Veröffentlichungen von AEM Sites aktiviert. Dieser ermöglicht es nun, bei Auswahl eines Veröffentlichungsziels zwischen Veröffentlichen oder Vorschau zu wählen. Auf Erlebnisse in der Vorschau kann dann über eine dedizierte URL zugegriffen werden. Nach der Validierung in der Vorschau können Inhalte wie gewohnt von der Autoreninstanz auf die Veröffentlichungsinstanz übertragen werden. Die Aktivierung des Vorschau-Service in Adobe Experience Manager as a Cloud Service-Umgebungen erfolgt in den nächsten Wochen schrittweise.

## [!DNL Adobe Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* Sie können die freigegebenen Assets mithilfe der Funktion „Linkfreigabe“ herunterladen. Dieser Download verwendet jetzt einen asynchronen Service, der schnellere und unterbrechungsfreie Downloads ermöglicht, selbst bei sehr großen Downloads. Siehe [Herunterladen von Assets](/help/assets/download-assets-from-aem.md#link-share-download).

  ![Posteingang herunterladen](/help/assets/assets/download-inbox.png)

### Neue Funktionen im Vorabveröffentlichungskanal {#what-is-new-assets-prerelease}

* Metadatenschemata können direkt auf die Ordnereigenschaften angewendet werden.

  ![Hinzufügen von Metadatenschemata aus Ordnereigenschaften](/help/assets/assets/metadata-schema-folder-properties.png)

* Mit dem Tool zur Asset-Massenaufnahme können Sie während einer Massenaufnahme Metadaten hinzufügen.

* Zur Verbesserung des Anwendererlebnisses wird nun die Anzahl der in einem Ordner vorhandenen Assets angezeigt. Für mehr als 1.000 Assets in einem Ordner zeigt [!DNL Assets] „1000+“ an.

  ![Anzahl der Assets in einem Ordner in Benutzeroberfläche angezeigt](/help/assets/assets/browse-folder-number-of-assets.png)

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

* Beim Hochladen sehr großer Dateien stürzt das [!DNL Experience Manager desktop app] ab. (CQ-4320942)
* Die Optionen der Symbolleiste variieren, je nachdem ob eine Sammlung innerhalb eines Ordners von einem Suchergebnis aus ausgewählt wird. (CQ-4321406)

#### Neue Funktionen in Dynamic Media {#what-is-new-dm}

* DPR-Optimierung (Device Pixel Ratio, Gerätepixelverhältnis) für die intelligente Bildbearbeitung und die Optimierung der Netzwerkbandbreite ermöglichen es Ihnen, auf Geräten mit hoher Auflösung und eingeschränkter Netzwerkbandbreite effizient Bilder der besten Qualität bereitzustellen. Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur intelligenten Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md) und [Bildoptimierung mit den Bildformaten der nächsten Generation, WebP und AVIF](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4).
* Unterstützung für AVIF, das Bildformat der nächsten Generation, bei der Bereitstellung von Dynamic Media (fmt-URL-Modifikator) wurde eingeführt.

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **Kontextuelle Hilfe**: Es wurde eine kontextuelle Hilfe für den Editor für adaptive Formulare, den Vorlageneditor und den Design-Editor hinzugefügt, um Autoren dabei zu helfen, verschiedene Funktionen von Editoren besser zu verstehen.
* **Fehlermeldungen im Eigenschaften-Browser**: Es wurden Fehlermeldungen für jede Eigenschaft im Eigenschaften-Browser für adaptive Formulare hinzugefügt. Diese Meldungen helfen beim Verständnis der zulässigen Werte für ein Feld.

### Kommende Beta-Funktion von [!DNL Forms] {#what-is-new-forms-prerelease}

Output as a Cloud Service: Dieser Ausgabe-Service unterstützt Sie beim Kombinieren von XDP-Vorlagen und XML-Daten, um Druckdokumente in verschiedenen Formaten zu generieren. Mit dem Service können Sie Dokumente im synchronen und asynchronen Stapelmodus generieren. Dabei können Sie mit dem Output-Service Programme mit folgenden Funktionen erstellen:

* Erzeugen fertiger Formulardokumente durch Füllen von Vorlagendateien mit XML-Daten
* Erzeugen Sie Ausgabeformulare in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckdatenströme.
* Generieren von druckbaren PDFs aus XFA-Formular-PDFs

Sie können an formscsbeta@adobe.com schreiben, um sich für das Beta-Programm zu registrieren.

### Fehlerbehebungen in [!DNL Forms] {#forms-bugs-fixed}

* Wenn Sie in AEM Forms-Workflows in einem Schritt „Aufgabe zuweisen“ das Standardsymbol der Aktionsschaltflächen durch ein Coral-Symbol ersetzen, funktioniert die Workflows nicht mehr und protokollieren eine Ausnahme. Wenn Standardsymbole verwendet werden, funktioniert der Workflow wie erwartet.
* Wenn Sie auf der Layout-Ebene die Anzahl der Spalten ändern, die Bearbeitungsebene öffnen und einige Komponenten in ein Bedienfeld ziehen, werden im Inhaltsbereich des adaptiven Formular-Editors blaue Quadrate angezeigt und der Editor reagiert nicht mehr.
* Die Fehlermeldung einer Option des Regel-Editors in Bezug auf die Angabe der URL eines adaptiven oder externen Assets ist zu lang und nicht anwenderfreundlich.


## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0.

### Veröffentlichungsdatum {#release-date-cm-may}

Die Version 2021.5.0 von Cloud Manager in AEM as a Cloud Service wurde am 6. Mai 2021 veröffentlicht.
Die nächste Version ist für den 3. Juni 2021 geplant.

### Neue Funktionen {#what-is-new-may}

* Die PackageOverlaps-Qualitätsregel erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, im selben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Bereitstellungsprotokoll, das von einem Cloud Manager-Benutzer heruntergeladen wurde, ist aufschlussreicher und enthält Details zu Fehlern und Erfolgsszenarien.

* Beim Pushen von Code an Adobe Git wurden treten jetzt keine Fehler mehr auf.

* Das Commerce-Add-on kann jetzt während des Workflows „Programm bearbeiten“ auf Sandbox-Programme angewendet werden.

* Das Erlebnis „Programm bearbeiten“ wurde aktualisiert.

* In der Tabelle „Domain-Names“ auf der Seite mit den Umgebungsdetails werden bis zu 250 Domain-Namen mit Seitenumbruch angezeigt.

* Auf der Registerkarte „Lösungen“ in den Workflows „Programm hinzufügen“ und „Programm bearbeiten“ wird die Lösung angezeigt, auch wenn für das Programm nur eine Lösung verfügbar ist.

* Die Fehlermeldung, die im Build-Schritt-Protokoll aufgeführt wurde, wenn der Build keine bereitgestellten Inhaltspakete generiert hat, war unklar.

### Fehlerbehebungen {#bug-fixes-cm-may}

* Dem Benutzer wird neben einer IP-Zulassungsliste kein grüner „aktiver“ Status mehr angezeigt, wenn diese Konfiguration nicht bereitgestellt wurde.

* Anstatt „gelöschte“ Variablen zu entfernen, markiert die Pipeline-Variablen-API sie nur mit dem Status **GELÖSCHT**.

* Einige Code-Smell-Qualitätsprobleme haben sich fälschlicherweise auf die Zuverlässigkeitsbewertung ausgewirkt.

* Da Platzhalter-Domains nicht unterstützt werden, verhindert die Benutzeroberfläche das Senden von Platzhalter-Domains durch Anwender.

* Wenn die Pipeline-Ausführung zwischen Mitternacht und 1:00 Uhr UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als die am Vortag erstellte Version.

* Während des Setups des Sandbox-Programms wird nach erfolgreicher Erstellung des Projekts mit Beispielcode auf der Übersichtsseite „Git verwalten“ als Link von der Hero-Karte angezeigt.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Das Content Transfer Tool 1.4.6 wurde am 27. Mai 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-latest}

* Dem Schnellstart-Fehlerprotokoll wurde eine neue Protokollierungsanweisung hinzugefügt, wenn der Benutzer keine Ausführungsberechtigung für die ausführbare Java-Datei hat.

* Wenn ein Benutzer einen Migrationssatz aus der CTT-Benutzeroberfläche löscht, über die eine Extraktion durchgeführt wurde, wird der mit diesem Migrationssatz verknüpfte `tmp` gelöscht, um Speicherplatz zu sparen.

### Fehlerbehebungen {#bug-fixes-ctt-latest}

* Beim Löschen eines Migrationssatzes wurde in der CTT-Benutzeroberfläche gelegentlich eine nicht hilfreiche Fehlermeldung angezeigt. Dieses Problem wurde behoben.

* Wenn bei der Ausführung des User Mapping Tools die Anwender auf dem Ziel und dem Host dieselbe E-Mail-Adresse, aber unterschiedliche Anwendernamen hatten, schlug die gesamte Aufnahme fehl. Dieses Problem wurde behoben. In einem solchen Konfliktszenario wird der Anwender/die Gruppe übersprungen und in der Protokolldatei als Konflikt protokolliert.

### Veröffentlichungsdatum {#release-date-ctt}

Das Content Transfer Tool 1.4.0 wurde am 11. Mai 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-may}

* Diese Version des Content Transfer Tool erstellt Textausgabedarstellungen für Assets, die zu Cloud Service migriert werden. Textausgabedarstellungen sind erforderlich, um die Volltextsuche für aufgenommene Assets zu unterstützen.
* Die maximale Anzahl der Migrationssätze für das Content Transfer Tool, die ein Benutzer erstellen kann, wurde von 4 auf 10 erhöht.

### Fehlerbehebungen {#bug-fixes-ctt-may}

* Mehrere Fehlerbehebungen im Zusammenhang mit der Funktion zur automatischen Aktualisierung in der Benutzeroberfläche des Content Transfer Tool.
* Content Transfer Tool mit `wipe=true` führt nicht mehr zu einem falschen Zählerindex auf dem Ziel. Dieses Problem wurde behoben.

## Commerce-Add-on {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Unterstützung der Seitenumbrüche für zugehörige Inhalte in den Eigenschaften der Produktkonsole

### Fehlerbehebungen {#bug-fixes-commerce}

* Asset-Miniaturen werden nicht auf der Registerkarte „Asset“ der Produkteigenschaften angezeigt.

* Breadcrumb setzt Vorschaudaten in der Produktkonsole zurück.
