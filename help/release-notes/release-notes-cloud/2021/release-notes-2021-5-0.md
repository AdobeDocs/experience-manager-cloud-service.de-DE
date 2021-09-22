---
title: Versionshinweise für Version 2021.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2021.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: 3f9d7339-7e37-4702-821e-f2b03cd7e224
source-git-commit: af5eb5aeb34e2f0ead98e0a0acb412b19bcfe517
workflow-type: tm+mt
source-wordcount: '1355'
ht-degree: 61%

---

# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>Von hier aus können Sie zu Versionshinweisen früherer Versionen navigieren. z. B. für die Jahre 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service wiurde am 27. Mai 2021 veröffentlicht.
Die folgende Version (2021.6.0) wird am 28. Juni 2021 veröffentlicht.

## AEM as a Cloud Service Foundation {#foundation}

### Neue Funktionen in AEM as a Cloud Service Foundation {#what-is-new-foundation}

* [Vorabversionskanal](/help/release-notes/prerelease.md): Vorschau bevorstehender Funktionen für einen ganzen Monat, bevor sie in Produktion sind!

* [API-Einstellung](/help/release-notes/deprecated-apis.md): Eine Liste der neuesten veralteten APIs für AEM as a Cloud Service ist verfügbar.

* [Build Analyzer-Maven-Plug-in AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html): Aktualisieren Sie Ihre Maven-Projekte auf die neueste Version, die eine veraltete Java-API-Prüfung und andere Verbesserungen enthält.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* Sie werden in Kürze in der Lage sein, Inhalte auf einer neuen [Vorschaustufe](/help/sites-cloud/authoring/fundamentals/previewing-content.md) zu überprüfen, um das endgültige Erscheinungsbild des Erlebnisses so zu simulieren, wie Sie es auf der Veröffentlichungsstufe tun würden. Dies wird vom AEM Sites-Assistenten für verwaltete Veröffentlichungen aktiviert, der jetzt die Auswahl eines Veröffentlichungsziels zwischen Veröffentlichen oder Vorschau ermöglicht. Auf Erlebnisse in der Vorschau kann dann über eine dedizierte URL zugegriffen werden. Nach der Validierung der Vorschau können Inhalte wie gewohnt vom Autor zur Veröffentlichung veröffentlicht werden. Die Aktivierung des Vorschaudienstes in AEM als Cloud Service-Umgebungen wird in den nächsten Wochen schrittweise eingeführt.

## [!DNL Adobe Experience Manager Assets] as a  [!DNL Cloud Service] {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* Sie können die freigegebenen Assets mit der Funktion Linkfreigabe herunterladen. Dieser Download verwendet jetzt einen asynchronen Dienst, der schnellere und unterbrechungsfreie Downloads bietet, selbst bei sehr großen Downloads. Siehe [Herunterladen von Assets](/help/assets/download-assets-from-aem.md#link-share-download).

   ![Posteingang herunterladen](/help/assets/assets/download-inbox.png)

### Neue Funktionen im Kanal für die Vorabversion {#what-is-new-assets-prerelease}

* Metadatenschemata können direkt auf die Ordnereigenschaften angewendet werden.

   ![Hinzufügen von Metadatenschemata aus Ordnereigenschaften](/help/assets/assets/metadata-schema-folder-properties.png)

* Mit dem Asset-Massenaufnahme-Tool können Sie während einer Massenaufnahme Metadaten hinzufügen.

* Eine Erweiterung des Benutzererlebnisses zeigt die Anzahl der in einem Ordner vorhandenen Assets an. Für mehr als 1000 Assets in einem Ordner zeigt [!DNL Assets] 1000+ an.

   ![Anzahl der Assets in einem Ordner wird auf der Benutzeroberfläche angezeigt](/help/assets/assets/browse-folder-number-of-assets.png)

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

* Das Hochladen sehr großer Dateien stürzt die [!DNL Experience Manager desktop app] ab. (CQ-4320942)
* Die Symbolleistenoptionen unterscheiden sich, wenn dieselbe Sammlung aus einem Ordner ausgewählt und in einem Suchergebnis ausgewählt wird. (CQ-4321406)

#### Neue Funktionen in Dynamic Media {#what-is-new-dm}

* Die intelligente Bildbearbeitung (Device Pixel Ratio) und die Optimierung der Netzwerkbandbreite ermöglichen es Ihnen, auf Geräten mit hoher Auflösung und eingeschränkter Netzwerkbandbreite effizient Bilder der besten Qualität bereitzustellen. Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur intelligenten Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md) und [Bildoptimierung mit Bildformaten der nächsten Generation, WebP und AVIF.](https://medium.com/adobetech/image-optimisation-with-next-gen-image-formats-webp-and-avif-248c75afacc4)
* Neue Unterstützung für AVIF-Bildformat der nächsten Generation in der Dynamic Media-Bereitstellung (Fmt-URL-Modifikator).

## [!DNL Adobe Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **Kontextuelle Hilfe**: Es wurde eine kontextuelle Hilfe für den Editor für adaptive Formulare, den Vorlageneditor und den Design-Editor hinzugefügt, um Autoren dabei zu helfen, verschiedene Funktionen von Editoren besser zu verstehen.
* **Fehlermeldungen im Eigenschaften-Browser**: Es wurden Fehlermeldungen für jede Eigenschaft im Eigenschaften-Browser für adaptive Formulare hinzugefügt. Diese Meldungen helfen beim Verständnis der zulässigen Werte für ein Feld.

### Kommende Beta-Funktion von [!DNL Forms] {#what-is-new-forms-prerelease}

Output as a Cloud Service: Der Output-Service unterstützt Sie beim Kombinieren von XDP-Vorlagen und XML-Daten, um Druckdokumente in verschiedenen Formaten zu erstellen. Mit dem Service können Sie Dokumente im synchronen und asynchronen Batch-Modus generieren. Dabei können Sie mit dem Output-Service Programme mit folgenden Funktionen erstellen:

* Generieren fertiger Formulardokumente durch Füllen von Vorlagendateien mit XML-Daten.
* Generieren von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Printstreams.
* Generieren von druckbaren PDFs aus XFA-Formular-PDFs

Sie können sich an formscsbeta@adobe.com wenden, um sich für das Beta-Programm zu registrieren.

### Fehlerbehebungen in [!DNL Forms] {#forms-bugs-fixed}

* Fehlerkorrektur – Wenn Sie in einem Schritt „Aufgabe zuweisen“ von AEM Forms-Workflows das Standardsymbol der Aktions-Schaltflächen durch ein Coral-Symbol ersetzen, funktioniert der Workflow jetzt und protokolliert keinen Ausnahmefehler mehr. Der Workflow funktioniert wie erwartet, wenn Standardsymbole verwendet werden.
* Wenn Sie auf der Layout-Ebene die Anzahl der Spalten ändern, die Bearbeitungsebene öffnen und einige Komponenten in einen Bereich ziehen, werden im Inhaltsbereich des adaptiven Formulareditors keine quadratischen blauen Kästen mehr angezeigt und der Editor reagiert jetzt normal.
* Die Fehlermeldung einer Regeleditoroption im Zusammenhang mit der Bereitstellung der URL eines adaptiven oder externen Assets ist jetzt benutzerfreundlich und nicht mehr zu lang.


## Cloud Manager  {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0.

### Veröffentlichungsdatum {#release-date-cm-may}

Die Version 2021.5.0 von Cloud Manager in AEM as a Cloud Service wurde am 6. Mai 2021 veröffentlicht.
Die nächste Version ist für den 3. Juni 2021 geplant.

### Neue Funktionen {#what-is-new-may}

* Die PackageOverlaps-Qualitätsregel erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, im selben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Das von Cloud Manager-Anwendern heruntergeladene Bereitstellungsprotokoll ist nun aufschlussreicher und enthält Details zu Fehlern und Erfolgsszenarios.

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

* Dem Fehlerprotokoll des Schnellstarts wurde eine neue Protokollierungsanweisung hinzugefügt, wenn der Benutzer keine Ausführungsberechtigung für die ausführbare Java-Datei hat.

* Wenn ein Benutzer einen Migrationssatz aus der CTT-Benutzeroberfläche löscht, wo eine Extraktion durchgeführt wurde, wird der mit diesem Migrationssatz verknüpfte Ordner `tmp` gelöscht, um Speicherplatz zu sparen.

### Fehlerbehebungen {#bug-fixes-ctt-latest}

* Beim Löschen eines Migrationssatzes wurde in der CTT-Benutzeroberfläche gelegentlich eine nicht hilfreiche Fehlermeldung angezeigt. Dieses Problem wurde behoben.

* Wenn bei der Ausführung der Benutzerzuordnung Benutzer dieselbe E-Mail-Adresse auf dem Ziel und dem Host, aber unterschiedliche Benutzernamen hatten, schlug die gesamte Erfassung fehl. Dieses Problem wurde behoben. In einem solchen widersprüchlichen Szenario wird der Benutzer/die Gruppe übersprungen und als Konflikt in der Protokolldatei protokolliert.

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

* Paginierungsunterstützung für verknüpften Inhalt in den Eigenschaften der Produktkonsole

### Fehlerbehebungen {#bug-fixes-commerce}

* Asset-Miniaturansichten werden nicht auf der Registerkarte &quot;Asset&quot;der Produkteigenschaften angezeigt

* Breadcrumb setzt Vorschaudaten in der Produktkonsole zurück
