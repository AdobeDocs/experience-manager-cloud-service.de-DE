---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: ee16d3a0fe1fc93c215d31f7dea0e9c21e051350
workflow-type: tm+mt
source-wordcount: '1963'
ht-degree: 99%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.4.0) ist der 25. April 2024. Die nächste Version (2024.5.0) ist für den 30. Mai 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- ## Release Video {#release-video}

Have a look at the April 2024 Release Overview video for a summary of the features added in the 2024.4.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3428342?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzen Sie GenAI über die neue Funktion [Varianten generieren](/help/generative-ai/generate-variations.md) von AEM, die jetzt in Cloud Service verfügbar ist. „Varianten generieren“ hilft Ihnen bei der Erstellung und Skalierung von Inhalten durch den Einsatz generativer KI. Wenden Sie sich an Ihr Adobe-Accountteam, um sich für das Programm zu erkundigen.

**Durchsuchen von Assets in der Inhaltsfragmentkonsole**

Inhaltsautorinnen und -autoren können jetzt Bilder und andere Assets durchsuchen, anzeigen und bearbeiten, ohne die Inhaltsfragmentkonsole verlassen zu müssen.

![Durchsuchen von Assets](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Möchten Sie die Funktion ausprobieren und Feedback geben? Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an aemcs-headless-adopter@adobe.com senden, um am Early-Adopter-Programm teilzunehmen.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Assets-Ansicht {#assets-view-new-features}


**Kontextsuche**

Sie können jetzt auch [im Repository verfügbare Assets durchsuchen, indem Sie Text-Prompts definieren](/help/assets/search-assets-view.md#contextual-search). Experience Manager Assets wandelt diese Text-Prompts automatisch in Suchfilter um und zeigt die Suchergebnisse an. Im Bereich „Filter“ können Sie automatische Filter anzeigen und ändern, um die Suchergebnisse weiter einzugrenzen.

![Kontextsuche](/help/assets/assets/contextual-search-text-prompt1.png)

**Express-Schnellaktionen für Videos**

Experience Manager Assets enthält jetzt [einfache und intuitive Tools zur Videobearbeitung, unterstützt von Adobe Express](/help/assets/edit-videos-assets-view.md), um die Wiederverwendung von Inhalten zu verbessern und deren Geschwindigkeit zu erhöhen. Zu den Bearbeitungsoptionen gehören das Zuschneiden, das Beschneiden, das Ändern der Größe eines Videos und das Konvertieren einer MP4-Datei in eine GIF-Datei.

![Beschneiden von Videos mit Adobe Express](/help/assets/assets/adobe-express-crop-video.png)

**Dynamische Ausgabedarstellungen**

Sie können jetzt [ dynamische Ausgabedarstellungen (einschließlich smartes Zuschneiden)](/help/assets/renditions.md) in Experience Manager Assets ansehen und herunterladen. Dynamische Ausgabeformate sind benutzerdefinierte Versionen von Bild-Assets, die in Echtzeit erstellt werden, um bestimmten Anforderungen zu entsprechen, z. B. die Größenanpassung von Bildern an die Auflösung des Geräts oder das Zuschneiden auf verschiedene Seitenverhältnisse. Mit diesen Ausgabedarstellungen können Unternehmen personalisierte und optimierte Erlebnisse für unterschiedliche Zielgruppenanforderungen bereitstellen.

![Dynamische Ausgabedarstellungen](/help/assets/assets/preset_smart_crop.png)

**Umbenennung im Kontext für Assets und Ordner**

Experience Manager Assets bietet jetzt ein vereinfachtes Benutzererlebnis, indem die [Möglichkeit geboten wird, ein Asset oder einen Ordner per Klick umzubenennen](/help/assets/manage-organize-assets-view.md).

**Zuweisen oder Entfernen von Metadatenformularen zu/aus mehreren Ordnern**

Sie können jetzt [Metadatenformulare mehreren Ordnern zuweisen oder daraus entfernen](/help/assets/metadata-assets-view.md#assign-metadata-form-to-a-folder).



## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Neue Funktionen in AEM Forms {#forms-new-features}

* **Verbesserter visueller Regeleditor für auf Kernkomponenten basierende adaptive Formulare**: Diese Version umfasst ein bedeutendes Upgrade des visuellen Regeleditors für adaptive Formulare, die auf Kernkomponenten basieren. Diese Version umfasst ein bedeutendes Upgrade des visuellen Regeleditors für adaptive Formulare, die auf Kernkomponenten basieren. Diese Aktualisierung konzentriert sich auf die Optimierung der Interaktionen mit benutzerdefinierten Funktionen und ermöglicht Ihnen so, robustere und effizientere Formulare zu erstellen.

  Sie können jetzt Interaktionen mit benutzerdefinierten Funktionen optimieren, indem Sie:

   * [neue Anmerkungen nutzen, um klarere Funktionsdefinitionen bereitzustellen](/help/forms/create-and-use-custom-functions.md#supported-javascript-annotations-for-custom-function).
   * [Caching-Mechanismen für benutzerdefinierte Funktionen verwenden, was zu einer schnelleren Formular-Performance führt](/help/forms/create-and-use-custom-functions.md#caching-support-for-custom-function).
   * [nahtlos mit globalen Objekten in benutzerdefinierten Funktionen arbeiten](/help/forms/create-and-use-custom-functions.md#field-and-global-scope-objects-in-custom-functions).
   * [optionale Parameter in benutzerdefinierten Funktionen definieren und verwenden](/help/forms/create-and-use-custom-functions.md#parameter).

  Diese Aktualisierung umfasst außerdem die folgenden Verbesserungen an der Funktionalität des Regeleditors. Sie haben folgende Möglichkeiten:

   * Implementieren Sie eine leistungsstarke [„Wenn-Dann-Sonst“-Logik](/help/forms/rule-editor-core-components.md#when) für die bedingte Ausführung.
   * Nutzen Sie moderne JavaScript-Funktionen wie Let- und Pfeilfunktionen (ES10-Unterstützung).
   * Validieren oder setzen Sie nicht nur Felder zurück, sondern auch ganze Bedienfelder und Formulare, um die Kontrolle über Benutzerinteraktionen zu erweitern.

  Diese Verbesserungen bieten ein intuitiveres und leistungsfähigeres Erlebnis für das Erstellen von Regeln und benutzerdefinierten Funktionen im visuellen Regeleditor.

* **[Erstellen mehrerer Versionen eines adaptiven Formulars](/help/forms/add-comments-annotations-versioning-adaptive-form-core-components.md)**: Sie können jetzt problemlos Varianten vorhandener Formulare verwalten. Dies vereinfacht die Versionskontrolle und erleichtert den Vergleich für die Formularoptimierung – alles innerhalb eines einzigen, optimierten Workflows.

* **[Vergleichen adaptiver Formulare](/help/forms/compare-forms.md)**: Sie können jetzt ganz einfach zwei Formulare vergleichen, um Unterschiede zwischen ihnen zu identifizieren. Dies erleichtert die reibungslose Zusammenarbeit, da Team-Mitglieder nun Revisionen vergleichen und Änderungen effizient diskutieren können.

* **Verbesserungen der Barrierefreiheit für die Freihandsignatur-Komponente**: In dieser Aktualisierung wird die Barrierefreiheit der Freihandsignatur-Komponente erheblich verbessert:

  **Verbesserte Tastaturnavigation:**
   * Durch Drücken der Tabulatortaste können Benutzende innerhalb des Signatur-Dialogfelds durch alle interaktiven Elemente navigieren.
   * Durch Signieren mit einem Pinsel oder der Tastatur und Drücken der Eingabetaste wird das Dialogfeld geschlossen.
   * Nach dem Signieren und Klicken auf „OK“ bleibt der Fokus auf der Signatur-Steuerung.

  **Funktion zum Löschen der Signatur:**

   * Über die Tabulatortaste kann auf ein Kreuzsymbol zum Löschen der Signatur zugegriffen werden.
   * Auf das Dialogfeld „Bestätigung des Löschens der Signatur“ kann auch über die Registerkartennavigation zugegriffen werden.

  **Erweiterte Beschriftungen und Steuerelemente:**
   * Die Beschriftung der Schaltfläche für die Tastatursignatur ist jetzt klarer und verwendet „aria-label“, um die Funktionalität anzukündigen (z. B. „aria-label=Mit Tastatur signieren“).
   * Der verbesserte Kontrast stellt sicher, dass alle Steuerelemente innerhalb der Freihandsignatur leicht zu unterscheiden sind.
   * Die Schaltfläche „OK“ bzw. das Häkchen-Symbol zeigt Inaktivität jetzt visuell an.

  **Signatur-Feedback für Bildschirmlesehilfen:**
   * Wenn eine Signatur eingegeben wird, können Benutzende der Bildschirmlesehilfen den Text hören, der zum Erstellen der Signatur verwendet wird.

Diese Aktualisierung sorgt dank Verbesserungen bei der Navigation, der Klarheit und dem Feedback für die Freihandsignatur-Komponente für ein inklusiveres Erlebnis für Benutzende mit körperlichen Einschränkungen.

### Early-Adopter-Programm {#forms-early-adopter}

* **[Senden eines adaptiven Formulars an das Adobe Workfront Fusion-Szenario](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service bietet vordefinierte Optionen, um ein adaptives Formular einfach mit Adobe Workfront zu verbinden. Dadurch wird der Prozess zum Senden eines adaptiven Formulars an ein Adobe Workfront-Szenario vereinfacht, indem Sie bei der Übermittlung eines adaptiven Formulars ein Workfront Fusion-Szenario auslösen können.

  <br/> ![Adobe Workfront](/help/forms/assets/adobe-workfront.png) <br/> Mit dem Adobe Workfront Fusion Connector können Sie Workflows entwickeln, die automatisch bei der Übermittlung eines adaptiven Formulars ausgelöst werden. Stellen Sie sich beispielsweise ein Szenario vor, bei dem ein Workflow initiiert wird, um einer bestimmten Person die Aufgabe zuzuweisen, die übermittelten Daten zu überprüfen, sodass ein Antrag auf Grundlage der im adaptiven Formular erfassten Informationen genehmigt oder abgelehnt werden kann. Diese optimierte Integration verbessert die Effizienz und führt die Automatisierung Ihrer Workflow-Prozesse auf eine neue Stufe.|

* **[Reader Extension-Dienst](/help/forms/aem-forms-cloud-service-communications-introduction.md#reader-extension-service)**: AEM Forms Communication APIs hat den Reader Extension-Dienst eingeführt, der es Ihnen ermöglicht, Funktionen wie das Ausfüllen von Formularen und das Kommentieren in normalen PDFs hinzuzufügen und diese für Benutzende mit dem kostenlosen Adobe Reader interaktiv zu machen.

* [Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/supporting-new-language-localization-core-components.md): Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt in einer RTL-Sprache (Right-to-Left) wie Arabisch, Persisch und Urdu angezeigt werden. RTL-Sprachen werden von über 2 Milliarden Menschen weltweit gesprochen. Durch die Verwendung eines Formulars in RTL-Sprache können Sie die Reichweite Ihrer adaptiven Formulare erweitern, um diese unterschiedlichen Zielgruppen zu bedienen und in RTL-Märkte einzutreten. In bestimmten Regionen ist es außerdem gesetzlich vorgeschrieben, Formulare in der jeweiligen Regionalsprache bereitzustellen. Durch die Anpassung an lokale Sprachen öffnen Sie nicht nur den Zugang zu einem breiteren Publikum, sondern sorgen auch für die Einhaltung der einschlägigen Gesetze und Vorschriften.

* **[Schützen Sie Ihre Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sondern sorgt auch für Seelenfrieden. Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies auch vorgesehen ist, die Dokumente ändern können.

  Sie können von Ihrer offiziellen E-Mail-ID aus an `aem-forms-ea@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

* **[Sie können den Datendienst Real User Monitoring (RUM) nutzen](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)**, um die Client-seitige Sammlung für AEM as a Cloud Service zu aktivieren.
Der Datendienst Real User Monitoring (RUM) bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktionen sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist nützlich für Kundinnen und Kunden, die entweder ein von Adobe verwaltetes CDN oder ein nicht von Adobe verwaltetes CDN verwenden. Für diejenigen, die ein nicht von Adobe verwaltetes CDN verwenden, kann jetzt außerdem die automatisierte Traffic-Berichterstellung aktiviert werden, sodass keine Traffic-Berichte mehr für Adobe freigegeben werden müssen.

  Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-rum-adopter@adobe.com`. Geben Sie in der E-Mail den Domain-Namen für jede Umgebung an, für die Sie RUM aktivieren möchten. Das Produkt-Team von Adobe aktiviert dann den Datendienst Real User Monitoring (RUM) für Sie.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### CDN-Konfiguration {#cdn-config}

Konfigurieren Sie den Traffic auf dem Adobe-CDN wie folgt:

* [Anforderungsumwandlungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#request-transformations): Ändern Sie Aspekte eingehender Anfragen, einschließlich Pfaden, Abfrageparametern und HTTP-Headern, bevor sie an AEM weitergeleitet werden.
* [Antwortumwandlungen](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations): Ändern Sie die HTTP-Header der ausgehenden Antworten, bevor sie an den Browser weitergeleitet werden.
* [Ursprungs-Auswahlen](/help/implementing/dispatcher/cdn-configuring-traffic.md#response-transformations#origin-selectors): Leiten Sie den Traffic durch das CDN zu Websites und Anwendungen außerhalb von AEM.

Sobald diese Regeln in der Quell-Code-Verwaltung (Git) deklariert sind, können Sie sie mithilfe der Cloud Manager-Konfigurations-Pipeline für das CDN bereitstellen. Weitere Informationen über die Client-seitigen Umleitungen finden Sie im Abschnitt „Early Adopter“ weiter unten.

### Benutzerdefinierte CDN-Fehlerseiten {#cdn-error-pages}

Für den unwahrscheinlichen Fall, dass das CDN nicht in der Lage ist, den Traffic an den AEM-Ursprung weiterzuleiten, kann eine benutzerdefinierte Fehlerseite deklariert werden, die die generische Version ersetzt. [Weitere Informationen](/help/implementing/dispatcher/cdn-error-pages.md) zur Bereitstellung von Fehlerseiten mit Branding.

### Early-Adopter-Programm {#foundation-early-adopter}

#### Client-seitige Weiterleitungen (Early Adopter-Programm) {#client-side-redirects-early-adopter}

Konfigurieren Sie Client-seitige Weiterleitungen vom Typ 301/302 in der Quell-Code-Verwaltung und stellen Sie sie im CDN bereit. [Weitere Informationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors) und Teilnahme am Early-Adopter-Programm unter **<aemcs-cdn-config-adopter@adobe.com>**.

#### Warnhinweise zu Traffic-Filterregeln (Early-Adopter-Programm) {#traffic-filter-rules-alerts-early-adopter}

Die kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), die die optional lizenzierbaren WAF-Regeln (Web Application Firewall) enthalten, ermöglichen es Ihnen zu konfigurieren, welcher Traffic erlaubt oder verweigert werden soll.

Sie können jetzt eine E-Mail an **<aemcs-cdn-config-adopter@adobe.com>** senden, um dem Early-Adopter-Programm beizutreten, damit Sie benachrichtigt werden, sobald Ihre Traffic-Filterregeln ausgelöst werden. Aktionszentrum-E-Mail-Benachrichtigungen informieren Sie darüber, wann bestimmte Traffic-Bedingungen eintreten, damit Sie geeignete Maßnahmen treffen können.

#### Apache/Dispatcher-Laufzeiterfassung von Rewrite-Zuordnungen (Early-Adopter-Programm) {#apache-rewritemaps-early-adopter}

Ähnlich wie bei AEM 6.5 erfassen Apache/Dispatcher Rewrite-Zuordnungen, die an einem bestimmten Speicherort im Veröffentlichungs-Repository platziert werden, und laden sie, ohne dass eine Pipeline auf der Web-Ebene ausgeführt werden muss. Dies eröffnet Business-Anwenderinnen und -Anwendern die Möglichkeit, Umleitungen über eine Benutzeroberfläche zu deklarieren, z. B. durch ACS Commons Redirect Map Manager. Bitte wenden Sie sich an **<aemcs-cdn-config-adopter@adobe.com>** für weitere Informationen.

#### Edge Side Includes (ESI) für das Laden dynamischer Inhalte (Early-Adopter-Programm) {#esi-early-adopter}

Das von Adobe verwaltete CDN unterstützt jetzt Edge Side Includes (ESI), eine Markup-Sprache für die dynamische Zusammenführung von Web-Inhalten auf Edge-Ebene. Durch die Einbeziehung von ESI-Snippets können Sie die gesamte HTML-Seite im CDN mit höheren TTLs zwischenspeichern und gleichzeitig diejenigen kleineren Abschnitte, die höhere Intervall-Updates (niedrigere TTLs) erfordern, öfter aus der Quelle abrufen. Bitte wenden Sie sich an **<aemcs-cdn-config-adopter@adobe.com>** für weitere Informationen.

#### RDE-Unterstützung für Frontend-Code mithilfe von Site-Designs und Site-Vorlagen (Early-Adopter-Programm) {#rde-frontend-early-adopter}

[Schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs)](/help/implementing/developing/introduction/rapid-development-environments.md) unterstützen jetzt Frontend-Code basierend auf [Site-Designs](/help/sites-cloud/administering/site-creation/site-themes.md) und [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md) für Early Adopters. Bei RDEs erfolgt dies über eine Befehlszeilenanweisung und nicht über eine [Frontend-Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Bitte wenden Sie sich an **<aemcs-rde-support@adobe.com>**, um dies auszuprobieren und Feedback zu hinterlassen.

#### Verbesserte Protokollierung für RDEs (Early-Adopter-Programm) {#rde-logging-early-adopter}

Beim Debugging von Code in einer [schnellen Entwicklungsumgebung (Rapid Development Environment, RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)können Entwicklerinnen und Entwickler Protokolle jetzt effizienter konfigurieren und streamen, indem sie die Befehlszeile verwenden und ohne die OSGi-Eigenschaften in der Versionskontrolle zu ändern. Zu den Funktionen gehören:

* Deklarieren von Protokollebenen auf Paket- oder Klassenebene
* Anpassen des Protokollausgabeformats
* Mehrere Protokolle parallel streamen

Bitte wenden Sie sich an **<aemcs-rde-support@adobe.com>**, um dies auszuprobieren und Feedback zu hinterlassen.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
