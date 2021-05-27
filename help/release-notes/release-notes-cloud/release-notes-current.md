---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 740b710cf21ef967f140ef1984268d9e82ea4059
workflow-type: tm+mt
source-wordcount: '947'
ht-degree: 13%

---


# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen navigieren. z. B. für die 2020, 2021 usw.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Die Version 2021.5.0 von [!DNL Adobe Experience Manager] wurde am 27. Mai 2021 veröffentlicht.
Die folgende Version (2021.6.0) wird am 24. Juni 2021 veröffentlicht.

## AEM as a Cloud Service Foundation {#foundation}

### Neue Funktionen in AEM as a Cloud Service Foundation {#what-is-new-foundation}

* [Vorabversionskanal](/help/release-notes/prerelease.md): Vorschau bevorstehender Funktionen für einen ganzen Monat, bevor sie in Produktion sind!

* [API-Einstellung](/help/release-notes/deprecated-apis.md): Eine Liste der neuesten veralteten APIs für AEM as a Cloud Service ist verfügbar.

* [Build Analyzer-Maven-Plug-in AEM as a Cloud Service SDK](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/build-analyzer-maven-plugin.html): Aktualisieren Sie Ihre Maven-Projekte auf die neueste Version, die eine veraltete Java-API-Prüfung und andere Verbesserungen enthält.

## [!DNL Adobe Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* Sie werden in Kürze in der Lage sein, Inhalte auf einer neuen [Vorschaustufe](/help/sites-cloud/authoring/fundamentals/previewing-content.md) zu überprüfen, um das endgültige Erscheinungsbild des Erlebnisses so zu simulieren, wie Sie es auf der Veröffentlichungsstufe tun würden. Dies wird vom AEM Sites-Assistenten für verwaltete Veröffentlichungen aktiviert, der jetzt die Auswahl eines Veröffentlichungsziels zwischen Veröffentlichen oder Vorschau ermöglicht. Auf Erlebnisse in der Vorschau kann dann über eine dedizierte URL zugegriffen werden. Nach der Validierung der Vorschau können Inhalte wie gewohnt vom Autor zur Veröffentlichung veröffentlicht werden. Die Aktivierung des Vorschaudienstes in AEM als Cloud Service-Umgebungen wird in den nächsten Wochen schrittweise eingeführt.

## [!DNL Adobe Experience Manager Assets] as a  [!DNL Cloud Service] {#assets}

### Neue Funktionen im Vorabversionskanal {#what-is-new-assets-prerelease}

* Metadatenschemata können direkt auf die Ordnereigenschaften angewendet werden.

   ![Hinzufügen von Metadatenschemata aus Ordnereigenschaften](/help/assets/assets/metadata-schema-folder-properties.png)

* Mit dem Asset-Massenaufnahme-Tool können Sie während einer Massenaufnahme Metadaten hinzufügen.

* Eine Erweiterung des Benutzererlebnisses zeigt die Anzahl der in einem Ordner vorhandenen Assets an. Für mehr als 1000 Assets in einem Ordner zeigt [!DNL Assets] 1000+ an.

   ![Anzahl der Assets in einem Ordner wird auf der Benutzeroberfläche angezeigt](/help/assets/assets/browse-folder-number-of-assets.png)

### Fehlerbehebungen in [!DNL Assets] {#assets-bugs-fixed}

* Das Hochladen sehr großer Dateien stürzt die [!DNL Experience Manager desktop app] ab. (CQ-4320942)
* Die Symbolleistenoptionen unterscheiden sich, wenn dieselbe Sammlung aus einem Ordner ausgewählt und in einem Suchergebnis ausgewählt wird. (CQ-4321406)

#### Neue Funktionen in Dynamic Media {#what-is-new-dm}

* Die intelligente Bildbearbeitung (Device Pixel Ratio) und die Optimierung der Netzwerkbandbreite ermöglichen es Ihnen, auf Geräten mit hoher Auflösung und eingeschränkter Netzwerkbandbreite effizient Bilder der besten Qualität bereitzustellen. Weitere Informationen finden Sie unter [Häufig gestellte Fragen zur intelligenten Bildbearbeitung](/help/assets/dynamic-media/imaging-faq.md).

   >[!NOTE]
   >
   >Die Veröffentlichungszeitleiste für die oben genannten Verbesserungen der intelligenten Bildbearbeitung lautet:
   >
   >* Nordamerika 24. Mai 2021 in NA,
      >
      >
   * Europa, Naher Osten und Afrika, 25. Juni 2021,
      >
      >
   * Asien-Pazifik 19. Juli 2021.


* Neue Unterstützung für AVIF-Bildformat der nächsten Generation in der Dynamic Media-Bereitstellung (Fmt-URL-Modifikator).

   >[!NOTE]
   >
   >Die Veröffentlichungszeitleiste für die AVIF-Unterstützung lautet:
   >
   >* Nordamerika 10. Mai 2021,
      >
      >
   * Europa, Naher Osten und Afrika 24. Mai 2021,
      >
      >
   * Asien-Pazifik 24. Juni 2021.


## Cloud Manager {#cloud-manager}

In diesem Abschnitt finden Sie die Versionshinweise für Cloud Manager in AEM as a Cloud Service 2021.5.0.

### Veröffentlichungsdatum {#release-date-cm-may}

Die Version 2021.5.0 von Cloud Manager in AEM as a Cloud Service wurde am 6. Mai 2021 veröffentlicht.
Die nächste Version ist für den 3. Juni 2021 geplant.

### Neue Funktionen {#what-is-new-may}

* Die Qualitätsregel PackageOverlaps erkennt jetzt Fälle, in denen dasselbe Paket mehrmals bereitgestellt wurde, d. h. an mehreren eingebetteten Speicherorten, in demselben bereitgestellten Paketsatz.

* Der Repository-Endpunkt in der öffentlichen API enthält jetzt die Git-URL.

* Das von einem Cloud Manager-Benutzer heruntergeladene Bereitstellungsprotokoll enthält jetzt Details zu Fehlern und Erfolgsszenarios.

* Beim Pushen von Code an Adobe Git wurden zeitweise auftretende Fehler behoben.

* Das Commerce-Add-on kann jetzt während des Workflows Programm bearbeiten auf Sandbox-Programme angewendet werden.

* Das Erlebnis Bearbeiten des Programms wurde aktualisiert.

* In der Tabelle &quot;Domänennamen&quot;auf der Seite &quot;Umgebungsdetails&quot;werden bis zu 250 Domänennamen per Paginierung angezeigt.

* Auf der Registerkarte &quot;Lösungen&quot;in den Workflows Programm hinzufügen und Programm bearbeiten wird die Lösung angezeigt, selbst wenn für das Programm nur eine Lösung verfügbar ist.

* Die Fehlermeldung im Build-Schrittprotokoll, wenn der Build keine bereitgestellten Inhaltspakete generiert hat, war unklar.

### Fehlerbehebungen {#bug-fixes-cm-may}

* Gelegentlich kann der Benutzer neben einer IP-Zulassungsliste einen grünen &quot;aktiven&quot;Status sehen, selbst wenn diese Konfiguration nicht bereitgestellt wurde.

* Anstatt &quot;gelöschte&quot;Variablen zu entfernen, markiert die Pipeline-Variablen-API sie nur mit dem Status **DELETED**.

* Einige Qualitätsprobleme vom Typ Code Smell wirkten sich fälschlicherweise auf die Zuverlässigkeitsbewertung aus.

* Da Wildcard-Domänen nicht unterstützt werden, verhindert die Benutzeroberfläche das Senden einer Wildcard-Domäne durch den Benutzer.

* Wenn die Pipelineausführung zwischen Mitternacht und 1 Uhr UTC gestartet wurde, war nicht garantiert, dass die von Cloud Manager generierte Artefaktversion größer ist als die am Vortag erstellte Version.

* Während der Einrichtung des Sandbox-Programms wird nach erfolgreicher Erstellung des Projekts mit Beispielcode Git verwalten auf der Seite Überblick als Link von der Heldenkarte angezeigt.

## Content Transfer Tool {#content-transfer-tool}

### Veröffentlichungsdatum {#release-date-ctt}

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
