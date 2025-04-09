---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: c8d7f23ef89de97ed656157ba628fd33206b4588
workflow-type: tm+mt
source-wordcount: '1576'
ht-degree: 94%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 20133 {#20133}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 20133, die am 1. April 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 19823.

Die Funktionsaktivierung von 2025.4.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-20133}

* ASSETS-47850: Das Hinzufügen von Scene7-Konfigurationen wird beschränkt, wenn ES für AEM CS aktiviert ist.
* CQ-4359547: Vollständiges Entfernen von Guava aus dem Git-Repository.
* FORMS-17551: Es wurde Unterstützung für Nachweise (DoR) für SharePoint-Listenintegrationen hinzugefügt.
* FORMS-18432: Es wurde eine formularspezifische (Regex-basierte) Client-seitige Vorbefüllungskonfiguration implementiert, um eine selektive Vorbefüllungsfunktion ohne Änderungen auf OSGi-Ebene zu ermöglichen.
* FORMS-18513: Es wurde Unterstützung für die Umwandlung von Datenbäumen in AEP Connector implementiert, um die Assistentenfunktionalität und die Möglichkeiten der Datenverarbeitung zu erweitern.
* FORMS-19068: Es wurde Unterstützung für Übermittlungsaktionen von AEP Connector in Forms Manager-APIs hinzugefügt, um die Funktionen zur Formulardatenintegration zu verbessern.
* GRANITE-57717: Aktualisierung des Client-Bundles in AEM.
* SITES-10469: AdapterFactory sollte immer dieselbe PageManager-Instanz zurückgeben.
* SITES-25130: Veröffentlichen der Kernkomponenten der Version 2.28.0.
* SITES-25433: Unterstützung für das Rendering der gesamten Seite beim Vergleichen mit alten Versionen.
* SITES-25923: LinkInfoStorageImpl kann blockieren, wenn keine URLs mehr gespeichert werden.
* Beim Löschen eines Inhaltsfragments über einen Workflow gibt es jetzt die Option, referenzierende Ressourcen zu aktualisieren, indem das neu gelöschte Fragment entfernt wird.
* SITES-26500: Hinzufügen der Option zum Verschieben von Inhaltsfragmenten über den Workflow – `move-fragments`.
* SITES-26711: Rollout-Trigger – Links werden nicht aktualisiert.
* SITES-27583: Experience Fragments verlieren den Versionsverlauf nach dem Verschieben.
* SITES-27618: Bei der Suche nach Verweisen eines Fragments auf Seiten werden nicht alle Ergebnisse zurückgegeben.
* SITES-27781: Es wurde eine Validierung auf Modellebene für Inhaltsfragmentverweise implementiert, was die Validierung referenzierter Fragmente anhand ihrer Modelleinschränkungen und erforderlichen Tags ermöglicht.
* SITES-27784: Aktualisieren der SQL-Abfragegenerierung, um die PATH-Funktion anstelle von `jcr:path` zu verwenden.
* SITES-28040: Adobe Target ExperienceFragmentsReplicationListener ist fehlerhaft.
* SITES-28051: Abrufen der Berechtigungen des aktuellen Benutzers für ein Inhaltsfragment: GET /cf/fragments/{fragmentId}/permissions.
* SITES-28190: Einrichtung für den Vorschau-Integrationstest.
* SITES-28227: Beim Hinzufügen von Assets als Referenzen zu einem Fragment überprüfen wir, ob das Asset vorhanden ist.
* SITES-28248: Umschalten von Sites-Ereignissen basierend auf der OSGi-Konfiguration.
* SITES-28255: Vollständiger Name fehlt in allen 3 Audit-Eigenschaften: erstellt, geändert, veröffentlicht.
* SITES-28390: PageImpl: hasContent() optimieren.
* SITES-28404: Durch das Löschen von Seiten in der Autoreninstanz sollte ihre Veröffentlichung im Vorschau-Service aufgehoben werden.
* SITES-28446: Es wurden zwei neue Felder hinzugefügt, die in der Antwort nicht sichtbar waren: der Platzhalter in NumberModelField und zulässige Modelle aus LongTextModelField.
* SITES-28536: Erstellen des `RENAME`-Endpunkts für Inhaltsfragmente.
* SITES-28537: Hinzufügen der Option zum Umbenennen von Inhaltsfragmenten über den Workflow – `rename-fragments`.
* SITES-28538: Verweise müssen erneut veröffentlicht werden, um gültige Inhalte in der Autoren- und Veröffentlichungsinstanz beizubehalten.
* SITES-28549: Erstellen von `/cf/domains`, um die Domain-ID basierend auf der AEM-Ebene zurückzugeben.
* SITES-29026: Es wurde ein optionaler Parameter hinzugefügt, der das Gebietsschema des Inhaltsfragments angibt, wobei ein Sprach- und ein Länder-Code verwendet werden.
* SITES-29031: Verbesserte Logik für das PATCH-en von Fragmenten und damit eine bessere Leistung.
* SITES-29169: Ressourcen mit dem Status VERÖFFENTLICHT werden erneut veröffentlicht, wenn sie auf eine Ressource verweisen, die verschoben, umbenannt oder gelöscht wurde.
* SITES-29376: Umschalter „Code hinzufügen“ zur Validierung des Löschens einer veröffentlichten Ressource.
* SITES-29417: Aktualisieren von `/libs/cq/Page/proxy.jsp`, um die Anfrage an den Knoten „jcr:content“ weiterzuleiten, anstatt sie einzuschließen.
* SITES-2947: Erstellen/Ändern der Kibana-Visualisierung, um Rasp beim Veröffentlichen zu vergleichen.
* SITES-29733: Erhöhte Leistung der Modellsuche durch Tags von Inhaltsfragmenten.
* SITES-8316: Inhaltsrichtlinien: Zwischenspeichern des ContentPolicyManager.
* SITES-24906: Edge Delivery mit universellem Editor: Unterstützen von durch Autorinnen und Autoren erstellten Tabellen ohne Zuordnung (frühzeitiger Zugriff).
* SITES-24907: Edge Delivery mit universellem Editor: Unterstützen der Veröffentlichung von Assets auf mehreren Sites für MSM-Anwendungsfälle (frühzeitiger Zugriff).
* SITES-26087: Edge Delivery mit universellem Editor: Verbessern des Veröffentlichungsdurchsatzes (frühzeitiger Zugriff).
* SITES-27956: Edge Delivery mit universellem Editor: Verbessern der Fehlerverarbeitung für die Veröffentlichung in Edge Delivery Services (frühzeitiger Zugriff).
* SITES-29602: CIF: Entfernung der Guava-Nutzung im core-cif-components-core.
* SITES-25785: CIF: Hinzufügen der Auswahl von Produktvarianten für den CIF-Produktverweis-Datentyp.
* SITES-26392: CIF[Experimental]: JSON+LD in CIF-Kernkomponenten in PDPs.
* SITES-21278: CIF[Experimental]: Möglichkeit von CIF, den Cache zu löschen.

### Behobene Probleme {#fixed-issues-20133}

* CQ-4358378: Verarbeitung von Lizenzfehlern bei der Übersetzungsausführung.
* CQ-4359263: Beim Abschluss des Auftrags wird keine Meldung im Dialogfeld angezeigt.
* CQ-4359386: Das i18n-Wörterbuch kann nicht zum Übersetzungsprojekt in AEMaaCS hinzugefügt werden.
* FORMS-18068: Probleme beim Rendern von fett gedrucktem Text in Nachweisen (DoR) für Optionsfeld- und Kontrollkästchengruppen, die Rich-Text-Felder verwenden.
* FORMS-18189: Die Handhabung benutzerdefinierter Funktionen wurde geändert, um die Protokollierung von Fehlern für leere Client-Bibliotheken zu verhindern und die Fehleranzeige in der Benutzeroberfläche zu verbessern.
* FORMS-18213: Es wurde eine Funktion zum Ausblenden/Ausschließen deaktivierter Felder aus dem Nachweis (DoR) implementiert, um die Dokumentenklarheit und das Anwendererlebnis zu verbessern.
* FORMS-18271: Der Forms Design-Editor zeigt nicht lokalisierte Fehlermeldungen an, was das Anwendererlebnis bei der Konfiguration von Formularen und der Anpassung von Designs beeinträchtigt.
* FORMS-18304: PDF/A-1b-Dokumente, die die Validierung in Acrobat und LiveCycle ES4 bestehen, werden in AEM 6.5 Forms aufgrund von geräteabhängigen Farbfehlern fälschlicherweise als nicht konform gekennzeichnet.
* FORMS-18325: Die Cloud-Konfiguration für Adobe Experience Platform (AEP) wurde hinzugefügt, um die Möglichkeiten der Integration und Verarbeitung von Formulardaten zu verbessern.
* FORMS-18360: Die Verwaltung des SharePoint-Listenumfangs für Team-Sites in der Forms-Dokumentenverwaltung wurde verbessert, um die Datenorganisation und Zugriffskontrolle zu optimieren.
* FORMS-18375: Auf Foundation-Komponenten basierende Formulare wählen fälschlicherweise reCAPTCHA-Konfigurationen aus dem Ordner `conf/global` aus, wenn kein bestimmter Konfigurations-Container ausgewählt ist.
* FORMS-18426: Die Suchfunktion der SharePoint-Liste schlägt fehl, wenn Listennamen Sonderzeichen enthalten (z. B. „-“), was sich auf die Formularintegration mit SharePoint-Listen auswirkt.
* FORMS-19028: Die Client-seitige Vorbefüllungsfunktion unterbricht die Formularereignisverarbeitung und verhindert dadurch, dass Wertübergabe- und DOMContentLoaded-Ereignisse beim Laden des Formulars ordnungsgemäß ausgelöst werden.
* FORMS-6950: Erforderliche ARIA-Rollen und -Attribute wurden zu den Baumansichtskomponenten des Dateisystemnavigators hinzugefügt, um die Barrierefreiheit für Bildschirmlesehilfen zu verbessern und den WCAG 4.1.2-Standard für Name, Rolle und Wert (Stufe A) zu erfüllen.
* FORMS-7016: Die Reihenfolge des Tastaturfokus im Formular-Editor folgt nicht der logischen Navigation.
* SITES-1960: Verbesserte Leistung des JSON-Vorschauvorgangs des Inhaltsfragmenteditors.
* SITES-24308: Die horizontale Bildlaufleiste wird angezeigt, wenn die Größe des Inhalts auf 400 % geändert wird.
* SITES-24493: Das interaktive Element hat nicht die erforderliche Rolle.
* SITES-24669: Auf den Fenster-Aufteiler in der Referenzleiste kann nicht über die Tastatur zugegriffen werden.
* SITES-26881: Fehler bei der Barrierefreiheit von AEMaaCS – Für das Symbol „Drei Punkte“ neben dem Feld für die Kommentareingabe wird eine falsche Rolle angegeben.
* SITES-26956: Follow-up zu SITES-24920 Die Seite lässt sich nicht in die Produktionsumgebung verschieben.
* SITES-27707: Die Auflistung von Assets in der Inhaltssuche schlägt aufgrund von Problemen mit Asset-Namen fehl (Regression 6.5 SP22).
* SITES-27757: Edge Delivery mit universellem Editor: Neuschreiben von Symbolen gemäß der Semantik von helix-html-pipeline.
* SITES-27780: Unerwartetes &lt;br>-Tag erscheint im RTE mit Plaintext DefaultPasteMode auf SP22.
* SITES-27958: Der Link-Prüfer gibt Fehler des Typs „Diese Sitzung wurde geschlossen“ aus.
* SITES-28149: Benutzerdefinierter ExperienceFragmentLinkRewriterProvider wird beim XF-Export an das Ziel nicht ausgelöst.
* SITES-28449: Fehler in der Benutzeroberfläche des Workflow-Widgets – Schließt untergeordnete Elemente ein, die nicht alle untergeordneten Seiten in AEM anzeigen.
* SITES-28456: Fehlende Benachrichtigung auf der Benutzeroberfläche beim Speichern falscher persistierter Abfragen im GraphiQL-Explorer (Follow-up zu SITES-28313).
* SITES-28464: Aktualisierung der Fragmentabfrage, um formatierte Daten mit Millisekunden zu verwenden.
* SITES-28486: Durch die Bearbeitung im Kontext im neuen Inhaltsfragmenteditor erfolgt keine Umleitung zum alten Editor.
* SITES-28570: Fehlende Asset-Metadaten werden von der GraphQL des Inhaltsfragments ordnungsgemäß verarbeitet.
* SITES-28580: Klassische Bild-Asset-Suche nach SP22-Upgrade beschädigt.
* SITES-28600: Launches – Inhaltsduplikat.
* SITES-28668: Launch kann nicht mit LaunchPromotionParameters beworben werden.
* SITES-28820: Launch-Präfix wurde zweimal innerhalb der neuen Variation hinzugefügt, die beim Zurücksetzen erstellt wurde.
* SITES-28877: Der UE-URL-Service wirft eine Ausnahme aus, wenn kein lokaler Externalizer-Endpunkt definiert ist.
* SITES-28956: Beim Löschen von Tags wird eine Warnung angezeigt, wenn das Tag von Inhaltsfragmenten referenziert wird.
* SITES-29208: Verweise und Variationen werden in Situationen, in denen ein Referenzfeld einen ungültigen Pfad enthält, ordnungsgemäß zurückgegeben.
* SITES-29363: Die Schaltfläche „Live Copy zurücksetzen“ funktioniert nicht für eine verschachtelte Live Copy-Inhaltshierarchie.
* SITES-29369: Assets-Ereignisproblem in AIO | Falsches Auslösen von Ereignissen des Typs „Seite veröffentlicht/Seite nicht veröffentlicht“.
* SITES-29972: Die Aktionen „Löschen“ und „Umbenennen“ erzeugen manchmal einen falschen Workflow-Kommentar.
* SITES-24631: CIF: Problem im Produktfeld suchen.
* SITES-24902: CIF: Produkt-URL-Format funktioniert für #variant_sku nicht wie erwartet.
* SITES-29191: CIF: Es können nicht mehr als 20 SKUs zur Produktlistenkomponente hinzugefügt werden.

### Bekannte Probleme {#known-issues-20133}

Keine.

### Eingestellte Funktionen und APIs {#deprecated-20133}

Veraltete und entfernte Funktionen und APIs in AEM as a Cloud Service werden im Dokument [Veraltete und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md) beschrieben.

#### Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen {#changes-user-groups}

Bei Verwendung der Adobe Admin Console für die Berechtigungsverwaltung dürfen die folgenden Gruppen NICHT verwendet werden, da sie nicht mehr mit AEM synchronisiert werden:
* AEM-Gruppen, die mit _GROUP_NAME_SUFFIX enden.
* Produktprofile aus anderen Umgebungen, Programmen oder Produkten.

Weitere Informationen finden Sie unter [Änderungen bei der Synchronisierung von Benutzergruppen und Produktprofilen](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/security/changes-in-user-group-and-product-profile-synchronization).

#### Einstellung des SPA-Editors {#deprecate-spa-editor}

Der [SPA-Editor](/help/implementing/developing/hybrid/introduction.md) wird ab Version 2025.4.0 für neue Projekte nicht mehr unterstützt. Für bestehende Projekte wird er weiterhin unterstützt, sollte allerdings nicht mehr für neue Projekte verwendet werden.

Die bevorzugten Editoren für die Verwaltung von Headless-Inhalten in AEM sind:

* der [universelle Editor](/help/edge/wysiwyg-authoring/authoring.md) zur visuellen Bearbeitung
* der [Inhaltsfragment-Editor](/help/assets/content-fragments/content-fragments-managing.md) zur formularbasierten Bearbeitung

Weitere Details zu dieser Einstellung finden Sie im Dokument [Einstellung des SPA-Editors](/help/implementing/developing/hybrid/spa-editor-deprecation.md).

### Sicherheitskorrekturen {#security-20133}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 34 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-20133}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.76.0 | [Oak-API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.28.0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
