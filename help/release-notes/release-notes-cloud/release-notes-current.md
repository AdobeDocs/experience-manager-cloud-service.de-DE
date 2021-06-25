---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 344a42f31444d30e9304b3a2198b1a4df17aa9c0
workflow-type: tm+mt
source-wordcount: '1663'
ht-degree: 23%

---


# Aktuelle Versionshinweise für[!DNL Adobe Experience Manager]as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen navigieren. z. B. für die 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.5.0 von [!DNL Adobe Experience Manager] wurde am 27. Mai 2021 veröffentlicht.
Die folgende Version (2021.6.0) wird am 24. Juni 2021 veröffentlicht.

## Release Video {#release-video}

Sehen Sie sich das Video [Versionsübersicht vom Mai 2021](https://video.tv.adobe.com/v/333602) an, um eine Zusammenfassung der hinzugefügten Funktionen zu erhalten.

## AEM as a Cloud Service Foundation {#foundation}

### Neue Funktionen in AEM as a Cloud Service Foundation {#what-is-new-foundation}

* [Vorabversionskanal](/help/release-notes/prerelease.md): Vorschau bevorstehender Funktionen für einen ganzen Monat, bevor sie in Produktion sind!

* [API-Einstellung](/help/release-notes/deprecated-apis.md): Eine Liste der neuesten veralteten APIs für AEM as a Cloud Service ist verfügbar.

* [Build Analyzer-Maven-Plug-in AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html): Aktualisieren Sie Ihre Maven-Projekte auf die neueste Version, die eine veraltete Java-API-Prüfung und andere Verbesserungen enthält.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* Sie werden in Kürze in der Lage sein, Inhalte auf einer neuen [Vorschaustufe](/help/sites-cloud/authoring/fundamentals/previewing-content.md) zu überprüfen, um das endgültige Erscheinungsbild des Erlebnisses so zu simulieren, wie Sie es auf der Veröffentlichungsstufe tun würden. Dies wird vom AEM Sites-Assistenten für verwaltete Veröffentlichungen aktiviert, der jetzt die Auswahl eines Veröffentlichungsziels zwischen Veröffentlichen oder Vorschau ermöglicht. Auf Erlebnisse in der Vorschau kann dann über eine dedizierte URL zugegriffen werden. Nach der Validierung der Vorschau können Inhalte wie gewohnt vom Autor zur Veröffentlichung veröffentlicht werden. Die Aktivierung des Vorschaudienstes in AEM als Cloud Service-Umgebungen wird in den nächsten Wochen schrittweise eingeführt.

## [!DNL Adobe Experience Manager Assets] as a  [!DNL Cloud Service] {#assets}

### Neue Funktionen im Kanal für die Vorabversion {#what-is-new-assets-prerelease}

* Metadatenschemata können direkt auf die Ordnereigenschaften angewendet werden.

   ![Hinzufügen von Metadatenschemata aus Ordnereigenschaften](/help/assets/assets/metadata-schema-folder-properties.png)

* Mit dem Asset-Massenaufnahme-Tool können Sie während einer Massenaufnahme Metadaten hinzufügen.

* Eine Erweiterung des Benutzererlebnisses zeigt die Anzahl der in einem Ordner vorhandenen Assets an. Für mehr als 1000 Assets in einem Ordner zeigt [!DNL Assets] 1000+ an.

   ![Anzahl der Assets in einem Ordner wird auf der Benutzeroberfläche angezeigt](/help/assets/assets/browse-folder-number-of-assets.png)

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

* Das Hochladen sehr großer Dateien stürzt die [!DNL Experience Manager desktop app] ab. (CQ-4320942)
* Die Symbolleistenoptionen unterscheiden sich, wenn dieselbe Sammlung aus einem Ordner ausgewählt und in einem Suchergebnis ausgewählt wird. (CQ-4321406)

#### Neue Funktionen in [!DNL Dynamic Media] {#what-is-new-dm}

* Mit der DSGVO (Smart Imaging Device Pixel Ratio) und der Optimierung der Netzwerkbandbreite können Sie effizient hochwertige Bilder auf Geräten mit hoher Auflösung und eingeschränkter Netzwerkbandbreite bereitstellen. Siehe [Häufig gestellte Fragen zur intelligenten Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md).

* Neue Unterstützung für das Bildformat AVIF der nächsten Generation in [!DNL Dynamic Media] Bereitstellung (`fmt` URL-Modifikator). Weitere Informationen und die Timeline finden Sie unter [Image Serving and Rendering API fmt](https://experienceleague.corp.adobe.com/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt.html).

## [!DNL Adobe Experience Manager Forms] as a  [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms}

* **Kontextuelle Hilfe**: Es wurde eine kontextuelle Hilfe für den Editor für adaptive Formulare, den Vorlageneditor und den Design-Editor hinzugefügt, um Autoren dabei zu helfen, verschiedene Funktionen von Editoren besser zu verstehen.
* **Fehlermeldungen im Eigenschaftenbrowser**: Es wurden Fehlermeldungen für jede Eigenschaft im Browser Adaptive Forms Properties hinzugefügt. Diese Meldungen helfen beim Verständnis der zulässigen Werte für ein Feld.

### Bevorstehende Beta-Funktion von [!DNL Forms] {#what-is-new-forms-prerelease}

Output as a Cloud Service: Der Output-Dienst unterstützt Sie beim Kombinieren von XDP-Vorlagen und XML-Daten, um Druckdokumente in verschiedenen Formaten zu generieren. Mit dem Dienst können Sie Dokumente im synchronen und asynchronen Batch-Modus generieren. Dabei können Sie mit dem Output-Dienst Anwendungen mit folgenden Funktionen erstellen:

* Generieren fertiger Formulardokumente durch Füllen von Vorlagendateien mit XML-Daten
* Generieren Sie Ausgabeformulare in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Druckströme.
* Generieren von druckbaren PDFs aus XFA-Formular-PDFs

Sie können an formscsbeta@adobe.com schreiben, um sich für das Betaprogramm zu registrieren.

### Fehlerbehebungen in [!DNL Forms] {#forms-bugs-fixed}

* Wenn Sie in einem Schritt &quot;Aufgabe zuweisen&quot;von AEM Forms-Workflows das Standardsymbol der Aktionsschaltflächen durch ein Coral-Symbol ersetzen, funktioniert der Workflow nicht mehr und protokolliert eine Ausnahme. Der Workflow funktioniert wie erwartet, wenn Standardsymbole verwendet werden.
* Wenn Sie auf der Layoutebene die Anzahl der Spalten ändern, die Bearbeitungsebene öffnen und einige Komponenten in ein Bedienfeld ziehen, werden im Inhaltsbereich des adaptiven Formulareditors quadratische blaue Felder angezeigt und der Editor reagiert nicht mehr.
* Die Fehlermeldung einer Regeleditoroption im Zusammenhang mit der Bereitstellung der URL eines adaptiven oder externen Assets ist zu lang und nicht benutzerfreundlich.

## Cloud Manager {#cloud-manager}

In diesem Abschnitt werden die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.6.0 und 2021.5.0 beschrieben.

## Veröffentlichungsdatum {#release-date-june-cm}

Die Version 2021.6.0 von Cloud Manager in AEM wurde am 10. Juni 2021 veröffentlicht.
Die nächste Version ist für den 15. Juli 2021 geplant.

### Neue Funktionen {#what-is-new-junecm}

* Der Vorschaudienst wird fortlaufend für alle Programme bereitgestellt. Kunden werden im Produkt benachrichtigt, wenn ihr Programm für den Vorschaudienst aktiviert ist. Weitere Informationen finden Sie unter [Zugriff auf den Vorschaudienst](/help/implementing/cloud-manager/manage-environments.md#access-preview-service) .

* Maven-Abhängigkeiten, die während des Build-Schritts heruntergeladen wurden, werden jetzt zwischen Pipeline-Ausführungen zwischengespeichert. Diese Funktion wird in den nächsten Wochen für Kunden aktiviert.

* Der Name des Programms kann jetzt im Dialogfeld Programm bearbeiten bearbeitet werden.

* Der standardmäßige Name der Verzweigung, der sowohl bei der Projekterstellung als auch im Standard-Push-Befehl über „Git-Workflows verwalten“ verwendet wird, wurde zu `main` geändert.

* Die Bearbeitung des Programmerlebnisses in der Benutzeroberfläche wurde aktualisiert.

* Die Qualitätsregel `ImmutableMutableMixCheck` wurde aktualisiert, um `/oak:index`-Knoten als unveränderlich zu klassifizieren.

* Die Qualitätsregeln `CQBP-84` und `CQBP-84--dependencies` wurden in einer einzigen Regel zusammengefasst. Im Rahmen dieser Konsolidierung werden beim Überprüfen von Abhängigkeiten Probleme in Abhängigkeiten von Drittanbietern, die zur AEM Laufzeit bereitgestellt werden, genauer identifiziert.

* Um Verwirrung zu vermeiden, wurden die Segmentzeilen Veröffentlichen AEM und Veröffentlichen des Dispatchers auf der Seite Umgebungsdetails konsolidiert.

   ![](/help/onboarding/release-notes-cloud-manager/assets/aem-dispatcher.png)

* Es wurde eine neue Code-Qualitätsregel hinzugefügt, um die Struktur von `damAssetLucene` -Indizes zu überprüfen. Weitere Informationen finden Sie unter [Benutzerdefinierte DAM-Asset Lucene Oak-Indizes](/help/implementing/cloud-manager/custom-code-quality-rules.md#oakpal-damAssetLucene-sanity-check) .

* Auf der Seite &quot;Umgebungsdetails&quot;werden jetzt mehrere Domänennamen für Veröffentlichungs- und Vorschaudienste angezeigt (sofern zutreffend). Weitere Informationen finden Sie unter [Umgebungsdetails](/help/implementing/cloud-manager/manage-environments.md#viewing-environment) .

### Fehlerbehebungen {#bug-fixes-junecm}

* Fehlerkorrektur – JCR-Knoten-Definitionen, die einen Zeilenumbruch nach dem Namen des Stammelements enthielten, werden jetzt korrekt geparst.

* Fehlerkorrektur – Die List-Repositorys-API filtert jetzt auch gelöschte Repositorys.

* Fehlerkorrektur – Wenn für den Zeitplanschritt ein ungültiger Wert angegeben wurde, wird jetzt die richtige Fehlermeldung angezeigt.

* Gelegentlich kann der Benutzer neben einer IP-Zulassungsliste den grünen Status *active* sehen, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Einige Programmbearbeitungssequenzen können dazu führen, dass die Produktions-Pipeline nicht erstellt oder bearbeitet werden kann.

* Einige Programmbearbeitungssequenzen können dazu führen, dass auf der Seite **Übersicht** eine irreführende Meldung angezeigt wird, um die Programmeinrichtung erneut auszuführen.


### Veröffentlichungsdatum {#release-date-cm-may}

Die Version 2021.5.0 von Cloud Manager in AEM as a Cloud Service wurde am 6. Mai 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-may}

* Die PackageOverlaps-Qualitätsregel erkennt jetzt, wenn dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, und zwar in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der Public API enthält jetzt die Git-URL.

* Das von einem Cloud Manager-Benutzer heruntergeladene Bereitstellungsprotokoll enthält jetzt Details zu Fehlern und Erfolgsszenarios.

* Beim Pushen von Code an Adobe Git wurden zeitweise auftretende Fehler behoben.

* Das Commerce-Add-on kann jetzt während des Workflows Programm bearbeiten auf Sandbox-Programme angewendet werden.

* Programmbearbeitung wurde modernisiert.

* In der Tabelle &quot;Domänennamen&quot;auf der Seite &quot;Umgebungsdetails&quot;werden bis zu 250 Domänennamen per Paginierung angezeigt.

* Auf der Registerkarte &quot;Lösungen&quot;in den Workflows Programm hinzufügen und Programm bearbeiten wird die Lösung angezeigt, selbst wenn für das Programm nur eine Lösung verfügbar ist.

* Die Fehlermeldung im Build-Schrittprotokoll, wenn der Build keine bereitgestellten Inhaltspakete generiert hat, war unklar.

### Fehlerbehebungen {#bug-fixes-cm-may}

* Gelegentlich kann der Benutzer neben einer IP-Zulassungsliste einen grünen &quot;aktiven&quot;Status sehen, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Anstatt &quot;gelöschte&quot;Variablen zu entfernen, markiert die Pipeline-Variablen-API sie nur mit dem Status **DELETED**.

* Einige Code-Smell-Qualitätsprobleme haben die Zuverlässigkeitsbewertung fälschlicherweise beeinflusst.

* Da Wildcard-Domänen nicht unterstützt werden, verhindert die Benutzeroberfläche das Senden einer Wildcard-Domäne durch den Benutzer.

* Wenn eine Pipeline-Ausführung zwischen Mitternacht und 1:00 Uhr UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer war als eine Version, die am Vortag erstellt wurde.

* Während der Einrichtung des Sandbox-Programms wird nach erfolgreicher Erstellung des Projekts mit Beispielcode Git verwalten auf der Seite Überblick als Link von der Heldenkarte angezeigt.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt-latest}

Die Version 1.4.6 des Content Transfer Tool wurde am 27. Mai 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-latest}

* Dem Fehlerprotokoll des Schnellstarts wurde eine neue Protokollierungsanweisung hinzugefügt, wenn der Benutzer keine Ausführungsberechtigung für die ausführbare Java-Datei hat.

* Wenn ein Benutzer einen Migrationssatz aus der CTT-Benutzeroberfläche löscht, wo eine Extraktion durchgeführt wurde, wird der mit diesem Migrationssatz verknüpfte Ordner `tmp` gelöscht, um Speicherplatz zu sparen.

### Fehlerbehebungen {#bug-fixes-ctt-latest}

* Beim Löschen eines Migrationssatzes wurde in der CTT-Benutzeroberfläche gelegentlich eine nicht hilfreiche Fehlermeldung angezeigt. Dieses Problem wurde behoben.

* Wenn bei der Ausführung der Benutzerzuordnung Benutzer dieselbe E-Mail-Adresse auf dem Ziel und dem Host, aber unterschiedliche Benutzernamen hatten, schlug die gesamte Erfassung fehl. Dieses Problem wurde behoben. In einem solchen widersprüchlichen Szenario wird der Benutzer/die Gruppe übersprungen und als Konflikt in der Protokolldatei protokolliert.

### Veröffentlichungsdatum {#release-date-ctt-may}

Die Version 1.4.0 des Content Transfer Tool wurde am 11. Mai 2021 veröffentlicht.

### Neue Funktionen {#what-is-new-ctt-may}

* Diese Version des Content Transfer Tool erstellt Textausgabeformate für Assets, die in Cloud Service migriert werden. Textausgabeformate sind erforderlich, um die Volltextsuche in aufgenommenen Assets zu unterstützen.
* Die maximale Anzahl der Migrationssätze für das Content Transfer Tool, die ein Benutzer erstellen kann, wurde von 4 auf 10 erhöht.

### Fehlerbehebungen {#bug-fixes-ctt-may}

* Mehrere Fehlerbehebungen im Zusammenhang mit der Funktion zur automatischen Aktualisierung in der Benutzeroberfläche des Content Transfer Tool.
* Content Transfer Tool mit `wipe=true` führte zu einem falschen Zählerindex auf dem Ziel. Dieses Problem wurde behoben.

## Commerce-Add-on {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Paginierungsunterstützung für verknüpften Inhalt in den Eigenschaften der Produktkonsole

### Fehlerbehebungen {#bug-fixes-commerce}

* Asset-Miniaturansichten werden nicht auf der Registerkarte &quot;Asset&quot;der Produkteigenschaften angezeigt

* Breadcrumb setzt Vorschaudaten in der Produktkonsole zurück
