---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 7d93af706d8b0556e9e26282d339794447eb0a41
workflow-type: tm+mt
source-wordcount: '1514'
ht-degree: 21%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 20133 {#20133}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 20133, die am Mittwoch, 1. April 2025 veröffentlicht wurde. Die vorherige Wartungsversion war Version 19823.

Die Funktionsaktivierung von 2025.4.0 wird den vollen Funktionsumfang für diese Wartungsversion bieten. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-20133}

* ASSETS-47850: Hinzufügen von Scene7-Konfigurationen beschränken, wenn AEM CS ES aktiviert ist.
* CQ-4359547: Vollständige Entfernung von Guava aus dem Repository https://git.corp.adobe.com/target-sdk/tsdk-core.
* FORMS-17551: Es wurde Unterstützung für Datensatzdokumente (DoR) für SharePoint-Listenintegrationen hinzugefügt.
* FORMS-18432: Es wurde eine formularspezifische (Regex-basierte) Client-seitige Vorbefüllungskonfiguration implementiert, um eine selektive Vorbefüllungsfunktion ohne Änderungen auf OSGi-Ebene zu ermöglichen.
* FORMS-18513: Es wurde Unterstützung für die Umwandlung von Datenbäumen in AEP Connector implementiert, um die Assistentenfunktionen und Datenverarbeitungsfunktionen zu erweitern.
* FORMS-19068: Übermittlungsaktionen für den AEP-Connector in Forms Manager-APIs werden nun unterstützt, um die Funktionen zur Formulardatenintegration zu verbessern.
* GRANITE-57717: Aktualisieren des Client-Bundles in AEM.
* SITES-10469: AdapterFactory sollte immer dieselbe PageManager-Instanz zurückgeben.
* SITES-25130: Version der Kernkomponenten 2.28.0.
* SITES-25433: Unterstützt das vollständige Seiten-Rendering beim Vergleich alter Versionen.
* SITES-25923: LinkInfoStorageImpl kann blockieren, wenn keine URLs mehr gespeichert werden.
* SITES-26208: Wenn Sie ein Inhaltsfragment per Workflow löschen, können Sie jetzt die verweisenden Ressourcen aktualisieren, indem Sie das neu gelöschte Fragment entfernen.
* SITES-26500: Hinzufügen der Option zum Verschieben von Inhaltsfragmenten über den Workflow - `move-fragments`.
* SITES-26711: Rollout-Trigger - Links werden nicht aktualisiert.
* SITES-27583: Experience Fragments verlieren den Versionsverlauf nach dem Verschieben.
* SITES-27618: Die Suche nach Verweisen eines Fragments auf Seiten liefert nicht alle Ergebnisse.
* SITES-27781: Es wurde eine Validierung auf Modellebene für Inhaltsfragmentverweise implementiert, die die Validierung referenzierter Fragmente anhand ihrer Modelleinschränkungen und erforderlichen Tags ermöglicht.
* SITES-27784: SQL-Abfragegenerierung aktualisieren, um die Funktion PATH anstelle von `jcr:path` zu verwenden.
* SITES-28040: Adobe Target ExperienceFragmentsReplicationListener ist fehlerhaft.
* SITES-28051: Abrufen der Berechtigungen des aktuellen Benutzers für ein Inhaltsfragment: GET /cf/fragments/{fragmentId}/permissions.
* SITES-28190: Setup für den Vorschau-Integrationstest.
* SITES-28227: Beim Hinzufügen von Assets als Referenzen zu einem Fragment überprüfen wir, ob das Asset vorhanden ist.
* SITES-28248: Umschalten von Sites-Ereignissen basierend auf der OSGi-Konfiguration.
* SITES-28255: Vollständiger Name fehlt in allen 3 Audit-Eigenschaften: erstellt, geändert, veröffentlicht.
* SITES-28390: PageImpl: Optimize hasContent().
* SITES-28404: Beim Löschen von Seiten in der Autoreninstanz sollte die Veröffentlichung im Vorschau-Service aufgehoben werden.
* SITES-28446: Es wurden zwei neue Felder hinzugefügt, die in der Antwort nicht sichtbar waren - der Platzhalter in NumberModelField und zulässige Modelle aus LongTextModelField.
* SITES-28536: Erstellen Sie `RENAME` Endpunkt für Inhaltsfragmente.
* SITES-28537: Hinzufügen der Option zum Umbenennen von Inhaltsfragmenten über den Workflow - `rename-fragments`.
* SITES-28538: Verweise müssen erneut veröffentlicht werden, um gültige Inhalte in der Autoren- und Veröffentlichungsinstanz beizubehalten.
* SITES-28549: Erstellen Sie `/cf/domains`, um die Domain-ID basierend auf der AEM-Ebene zurückzugeben.
* SITES-29026: Es wurde ein optionaler Parameter hinzugefügt, der das Gebietsschema des Inhaltsfragments angibt, wobei eine Sprache und ein Länder-Code verwendet werden.
* SITES-29031: Verbesserte Logik für PATCH-ING-Fragmente und damit höhere Leistung.
* SITES-29169: Alle veröffentlichten Ressourcen (unabhängig davon, ob sie sich im Status VERÖFFENTLICHT oder GEÄNDERT befinden) werden erneut veröffentlicht, wenn sie auf eine Ressource verweisen, die verschoben, umbenannt oder gelöscht wurde.
* SITES-29376: Umschalter „Code hinzufügen“ zur Validierung des Löschens veröffentlichter Ressourcen.
* SITES-29417: Aktualisieren Sie /libs/cq/Page/proxy.jsp , um die Anfrage an den jcr:content-Knoten weiterzuleiten, anstatt Folgendes einzuschließen.
* SITES-2947: Erstellen/ändern Sie die Kibana-Visualisierung, um Veröffentlichungsraps zu vergleichen.
* SITES-29733: Erhöhte Leistung der Modellsuche durch Tags von Inhaltsfragmenten.
* SITES-8316: Inhaltsrichtlinien: Speichern Sie den ContentPolicyManager zwischen.
* SITES-24906: Edge Delivery mit universellem Editor: Unterstützen von durch Autoren erstellten Tabellen ohne Zuordnung (früher Zugriff)
* SITES-24907: Edge Delivery mit universellem Editor: Unterstützung der Veröffentlichung von Assets auf mehreren Sites für MSM-Anwendungsfälle (früher Zugriff)
* SITES-27956: Edge Delivery mit universellem Editor: Verbesserung des Veröffentlichungsdurchsatzes (frühzeitiger Zugriff)
* SITES-27956: Edge Delivery mit universellem Editor: Verbessern der Fehlerbehandlung bei der Veröffentlichung in Edge Delivery Services (frühzeitiger Zugriff)

### Behobene Probleme {#fixed-issues-20133}

* CQ-4358378: Umgang mit Lizenzfehlern bei der Übersetzungsausführung.
* CQ-4359263: Es wird keine Meldung im Dialogfeld angezeigt, wenn der Vorgang abgeschlossen ist.
* CQ-4359386: i18n-Wörterbuch kann nicht zum Übersetzungsprojekt in AEMaaCS hinzugefügt werden.
* FORMS-18068: Probleme mit der fett gedruckten Textwiedergabe im Datensatzdokument (DoR) für Optionsfeld- und Kontrollkästchen-Gruppen unter Verwendung von Rich-Text-Feldern.
* FORMS-18189: Die Handhabung benutzerdefinierter Funktionen wurde geändert, um die Fehlerprotokollierung für leere Client-Bibliotheken zu verhindern und die Fehleranzeige in der Benutzeroberfläche zu verbessern.
* FORMS-18213: Es wurde eine Funktion zum Ausblenden/Ausschließen deaktivierter Felder aus dem Datensatzdokument (DoR) implementiert, um die Dokumentklarheit und das Benutzererlebnis zu verbessern.
* FORMS-18271: Der Forms-Design-Editor zeigt nicht lokalisierte Fehlermeldungen an, die das Benutzererlebnis bei der Konfiguration von Formularen und der Anpassung von Designs beeinträchtigen.
* FORMS-18304: PDF/A-1b-Dokumente, die die Validierung in Acrobat und LiveCycle ES4 bestehen, werden in AEM 6.5 Forms aufgrund von geräteabhängigen Farbfehlern fälschlicherweise als nicht konform gekennzeichnet.
* FORMS-18325: Die Cloud-Konfiguration für Adobe Experience Platform (AEP) wurde hinzugefügt, um die Funktionen für die Integration und Verarbeitung von Formulardaten zu verbessern.
* FORMS-18360: Verbesserte Verwaltung des SharePoint-Listenbereichs für Team-Sites in Forms Document Management zur Verbesserung der Datenorganisation und Zugriffskontrolle.
* FORMS-18375: Auf Foundation-Komponenten basierende Formulare wählen fälschlicherweise reCAPTCHA-Konfigurationen aus `conf/global` Ordner aus, wenn kein bestimmter Konfigurations-Container ausgewählt ist.
* FORMS-18426: Die SharePoint-Listensuchfunktion schlägt fehl, wenn Listennamen Sonderzeichen enthalten (z. B. &quot;-„), was sich auf die Formularintegration mit SharePoint-Listen auswirkt.
* FORMS-19028: Die Client-seitige Vorbefüllungsfunktion unterbricht die Formularereignisverarbeitung, was verhindert, dass Value Commit- und DOMContentLoaded-Ereignisse beim Laden des Formulars ordnungsgemäß ausgelöst werden.
* FORMS-6950: Es wurden erforderliche ARIA-Rollen und -Attribute zu den Strukturansichtskomponenten des Dateisystemnavigators hinzugefügt, um die Barrierefreiheit der Sprachausgabe zu verbessern und den WCAG 4.1.2-Standard für Name, Rolle und Wert (Stufe A) zu erfüllen.
* FORMS-7016: Die Reihenfolge des Tastaturfokus im Formular-Editor folgt nicht der logischen Navigation.
* SITES-1960: Verbesserte Leistung des JSON-Vorschauvorgangs des Inhaltsfragment-Editors.
* SITES-24308: Horizontale Bildlaufleiste wird angezeigt, wenn die Größe des Inhalts auf 400 % geändert wird.
* SITES-24493: Interaktives Element hat nicht die erforderliche Rolle.
* SITES-24669: Auf die Fensterunterteilung in der Verweisleiste kann nicht über die Tastatur zugegriffen werden.
* SITES-26881: Fehler bei der Barrierefreiheit von AEMaaCS - Für das Symbol „Drei Punkte“, das neben dem Feld für die Kommentareingabe steht, wird eine falsche Rolle angegeben.
* SITES-26956: Follow-up zu SITES-24920 kann Seite nicht in die Produktionsumgebung verschieben.
* SITES-27707: Die Asset-Auflistung in der Inhaltssuche schlägt aufgrund von Problemen mit Asset-Namen fehl (Regression 6.5 SP22).
* SITES-27757: Edge Delivery mit universellem Editor: Symbole gemäß der Semantik von helix-html-pipeline umschreiben.
* SITES-27780: Unerwartetes &lt;br>-Tag erscheint im RTE mit Plaintext DefaultPasteMode auf SP22.
* SITES-27958: Linkchecker gibt Fehler des Typs „Diese Sitzung wurde geschlossen“ aus.
* SITES-28149: Benutzerdefinierter ExperienceFragmentLinkRewriterProvider wird beim XF-Export in Target nicht ausgelöst.
* SITES-28449: Fehler in der Benutzeroberfläche des Workflow-Widgets - Schließt untergeordnete Elemente ein, die nicht alle untergeordneten Seiten in AEM anzeigen.
* SITES-28456: Fehlende Benachrichtigung auf der Benutzeroberfläche beim Speichern falscher persistierter Abfragen im GraphiQL-Explorer (Follow-up - SITES-28313).
* SITES-28464: Aktualisieren Sie die Fragmentabfrage, um formatierte Datumsangaben mit Millisekunden zu verwenden.
* SITES-28486: Die Bearbeitung im neuen Inhaltsfragment-Editor führt nicht zum alten Editor weiter.
* SITES-28570: Fehlende Asset-Metadaten werden von der GraphQL des Inhaltsfragments ordnungsgemäß verarbeitet.
* SITES-28580: Klassischer Bild-Asset-Finder nach SP22-Upgrade beschädigt.
* SITES-28600: Launches - Inhaltsduplikat.
* SITES-28668: Launch kann nicht mit LaunchPromotionParameters weitergeleitet werden.
* SITES-28820: Launch-Präfix wurde zweimal innerhalb der neuen Variante hinzugefügt, die bei rebase erstellt wurde.
* SITES-28877: Der UE-URL-Service löst eine Ausnahme aus, wenn kein lokaler Externalizer-Endpunkt definiert ist.
* SITES-28956: Beim Löschen von Tags wird eine Warnung angezeigt, wenn das Tag von Inhaltsfragmenten referenziert wird.
* SITES-29208: Verweise und Varianten werden in Situationen, in denen ein Referenzfeld einen ungültigen Pfad enthält, ordnungsgemäß zurückgegeben.
* SITES-29363: Die Schaltfläche „Live Copy zurücksetzen“ funktioniert nicht für verschachtelte Live Copy-Inhaltshierarchie.
* SITES-29369: Assets-Ereignisproblem in der Organisation der Luft- und Raumfahrtindustrien | Falsches Auslösen von Ereignissen des Typs „Veröffentlichung/Rückgängigmachung der Veröffentlichung“.
* SITES-29972: Löschen und Umbenennen von Aktionen führen manchmal zu unwahren Workflow-Kommentaren.

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

Weitere Informationen zu dieser Einstellung finden Sie im Dokument [SPA Editor Deprecation.](/help/implementing/developing/hybrid/spa-editor-deprecation.md)

### Sicherheitskorrekturen {#security-20133}

Mit AEM as a Cloud Service sollen Sicherheit und Leistung Ihrer Plattform optimiert werden. Diese Wartungsversion behebt 34 identifizierte Schwachstellen und sorgt somit für einen noch robusteren Systemschutz.

### Eingebettete Technologien {#embedded-tech-20133}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.76.0 | [Oak-API 1.76.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.76.0/index.html) |
| AEM SLING-API | 2.27.6 | [Apache Sling-API 2.27.6-API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.26–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2,28,0 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
