---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: af9e30ffb585619d1581db94d3961f561e12df2b
workflow-type: tm+mt
source-wordcount: '2261'
ht-degree: 34%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.3.0) ist der Freitag, 11. April 2024. Die nächste Version mit neuen Funktionen (2024.4.0) ist für den Freitag, 25. April 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- ## Release Video {#release-video}

Have a look at the March 2024 Release Overview video for a summary of the features added in the 2024.3.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3425864?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

**AEM Authoring für Edge Delivery Services**

AEM Sites kann jetzt als Inhaltsquelle für Edge Delivery Services verwendet werden. Autoren verwalten ihre Websites in AEM mit dem neuen universellen Editor mit kontextbezogenem Wysiwyg Authoring. Dies ermöglicht es Unternehmen, mit Edge Delivery Services schnell und leistungsstarke Webseiten zu erstellen und gleichzeitig AEM leistungsstarke Funktionen für Content Management zu nutzen.

![AEM-Authoring](/help/edge/assets/universal_editor_edge_delivery_services.png)

Weitere Informationen finden Sie unter [Dokumentation](/help/edge/overview.md) und beobachten Sie die [AEM Gems - Erste Schritte mit AEM Authoring und Edge Delivery Services](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-gems-getting-started-with-aem-authoring-and-edge-delivery/m-p/652694#M43905)

**Universal Editor für Headless-Implementierungen**

Der universelle Editor ermöglicht auch entkoppelte Webanwendungen, um die gleiche intuitive kontextbezogene WYSIWYG-Bearbeitung zu nutzen, die zuvor ausschließlich für herkömmliche Websites verwendet wurde. Autoren von Inhalten können Layouts jetzt visuell mithilfe von Inhaltsfragmenten erstellen, und zwar auf die gleiche Weise wie Komponenten auf Seiten.

Der universelle Editor zeichnet sich durch seine Anpassungsfähigkeit an verschiedene Webarchitekturen aus, die sowohl Server- als auch Client-seitiges Rendering ermöglichen, Framework-agnostisch bleiben und die Notwendigkeit AEM Hosting eliminieren. Die Integration vorhandener Webanwendungen mit dem universellen Editor für die Inhaltsbearbeitung ist unkompliziert. In erster Linie müssen Entwickler bestimmte Datenattribute in ihr Markup integrieren.

Dadurch gewährleistet der universelle Editor ein konsistentes Bearbeitungserlebnis, unabhängig von der Inhaltsstruktur oder dem zugrunde liegenden Technologie-Stack. Weitere Informationen finden Sie unter [Einführung in den universellen Editor](/help/implementing/universal-editor/introduction.md).

**Content Management - OpenAPIs für Inhaltsfragmente und -modelle**

Entwickler können jetzt programmatisch mit Inhaltsfragmenten und Inhaltsfragmentmodellen interagieren und mithilfe von Content Management OpenAPIs CruD-Vorgänge für sie durchführen. Weitere Informationen finden Sie unter [API-Dokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/)

**Unterstützung für Multisite-Management für Experience Fragments**

Die Unterstützung von Multisite-Management wurde für Ordnerstrukturen erweitert, die Experience Fragments speichern, sodass Benutzer eine vollständige Inhaltsstruktur mit Experience Fragments erstellen können.

**Inhaltsfragmentversionen vergleichen**

Mit dem neuen Inhaltsfragment-Editor können Inhaltsautoren jetzt Unterschiede zwischen der aktuellen Version eines Inhaltsfragments und einer früheren Version vergleichen und anzeigen.

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzung von GenAI durch AEM neue Funktion, [Varianten generieren](/help/generative-ai/generate-variations.md), jetzt im Cloud Service verfügbar. Mithilfe von generativen KI können Sie Varianten generieren und die Inhaltserstellung skalieren. Wenden Sie sich an Ihr Adobe-Account-Team, um sich für das Programm zu erkundigen.

**Asset-Navigation in der Inhaltsfragmentkonsole**

Inhaltsautoren können jetzt Bilder und andere Assets durchsuchen, anzeigen und bearbeiten, ohne die Inhaltsfragmentkonsole verlassen zu müssen.

![Asset-Navigation](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Möchten Sie die Funktion ausprobieren und Feedback geben? Senden Sie von Ihrer offiziellen E-Mail-ID eine E-Mail an aemcs-headless-adopter@adobe.com , um mehr über das Programm für frühe Anwender zu erfahren.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Admin-Ansicht {#admin-view}

**Native Integration mit Adobe Expreß**

AEM Assets lässt sich nativ in Adobe Expreß integrieren, sodass Sie direkt über die Adobe Expreß-Benutzeroberfläche auf die in AEM Assets gespeicherten Assets zugreifen können. Sie können in AEM Assets verwaltete Inhalte auf der Express-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern.

![Einschließen von Assets aus dem Assets-Add-on](/help/assets/assets/adobe-express-native-integration.png)

**Vorschau der Ausgabedarstellungen für alle unterstützten Videotypen**

Experience Manager Assets generiert jetzt standardmäßig Vorschaudarstellungen aller unterstützten Videotypen, ohne dass eine Verarbeitungsprofilkonfiguration erforderlich ist.

### Neue Funktionen in der Assets-Ansicht {#assets-view}

**Berechtigungen für Sammlungen verwalten**

Mit Assets Essentials können Administratoren die Zugriffsebenen für private Sammlungen verwalten, die im Repository verfügbar sind. Als Administrator können Sie Benutzergruppen erstellen und diesen Gruppen Berechtigungen zum Verwalten von Zugriffsebenen zuweisen. Sie können die Berechtigungsverwaltungsberechtigungen auch Benutzergruppen zuweisen.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Neue Funktionen für AEM Forms {#forms-new-features}

* **[Adobe Experience Manager Forms Edge Delivery Services](/help/edge/docs/forms/overview.md)**: AEM Forms Edge Delivery Services ist ein zusammenstellbarer Satz von Diensten, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autoren neue Formulare schnell aktualisieren, veröffentlichen und starten können. Diese Dienste bieten außergewöhnliche und sehr wirkungsvolle Formularerlebnisse, die Interaktionen und Konversionen fördern. Diese Formularerlebnisse sind einfach zu erstellen und zu entwickeln.

  ![EDS Forms-Funktionen](/help/edge/assets/eds-forms-features.png)

Diese Dienste ermöglichen Ihnen Folgendes:

* Arbeiten Sie mit mehreren Inhaltsquellen auf derselben Formularsite und verwenden Sie Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen oder Adaptive Forms Editor.
* Stellen Sie digitale Registrierungserlebnisse bereit, die schnell und kontinuierlich geladen und gerendert werden und Ihre Formularleistung durch echte Benutzerüberwachung (RUM) überwachen.
* Verwenden Sie HTML, modernes CSS und Vanilla JavaScript, um außergewöhnliche Erlebnisse zu erstellen und so die steile Lernkurve eines bestimmten Frameworks zu vermeiden.


### Neue Funktionen in der Vorabversion für AEM Forms {#forms-pre-release}

* **Verbesserter visueller Regeleditor für auf Kernkomponenten basierende adaptive Forms**: Mit dieser Version wird der visuelle Regeleditor für adaptive Formulare, die auf Kernkomponenten basieren, erheblich aktualisiert. Mit dieser Version wird der visuelle Regeleditor für adaptive Formulare, die auf Kernkomponenten basieren, erheblich aktualisiert. Diese Aktualisierung konzentriert sich auf die Optimierung der Interaktionen mit benutzerdefinierten Funktionen und ermöglicht Ihnen so, robustere und effizientere Formulare zu erstellen.

  Sie können jetzt benutzerdefinierte Funktionsinteraktionen optimieren, indem Sie:

   * Nutzen neuer Anmerkungen, um klarere Funktionsdefinitionen bereitzustellen.
   * Verwendung von Caching-Mechanismen für benutzerdefinierte Funktionen, was zu einer schnelleren Formularleistung führt.
   * Nahtloses Arbeiten mit globalen Objekten in benutzerdefinierten Funktionen.
   * Definieren und Verwenden optionaler Parameter in benutzerdefinierten Funktionen.

  Diese Aktualisierung bringt außerdem die folgenden Verbesserungen an der Funktionalität des Regeleditors. Sie haben folgende Möglichkeiten:

   * Implementieren Sie eine leistungsstarke &quot;when-then-else&quot;-Logik für die bedingte Ausführung.
   * Nutzen Sie moderne JavaScript-Funktionen wie Links- und Pfeilfunktionen (ES10-Unterstützung).
   * Validieren oder Zurücksetzen nicht nur von Feldern, sondern auch von ganzen Bedienfeldern und Formularen, wodurch die Kontrolle über Benutzerinteraktionen erweitert wird.

  Diese Verbesserungen bieten ein intuitiveres und leistungsfähigeres Erlebnis für das Erstellen von Regeln und benutzerdefinierten Funktionen im visuellen Regeleditor.

* **Erstellen mehrerer Versionen eines adaptiven Formulars**: Sie können jetzt problemlos Varianten vorhandener Formulare verwalten. Dies vereinfacht die Versionskontrolle und erleichtert den Vergleich für die Formularoptimierung - alles innerhalb eines einzigen, optimierten Workflows.

* **Adaptives Formular vergleichen**: Sie können jetzt zwei Formulare einfach vergleichen, um Unterschiede zwischen zwei Formularen zu identifizieren. Dies erleichtert die reibungslose Zusammenarbeit, da Teammitglieder Revisionen vergleichen und Änderungen effizient diskutieren können.

* **Verbesserungen der Barrierefreiheit für die Scribble-Signatur-Komponente**: Diese Aktualisierung verbessert die Barrierefreiheit der Scribble-Signatur-Komponente erheblich:

  **Verbesserte Tastaturnavigation:**
   * Durch Drücken der Tabulatortaste können Benutzer innerhalb des Signaturdialogfelds durch alle interaktiven Elemente navigieren.
   * Durch Unterschreiben mit einer Pinsel oder Tastatur und Drücken der Eingabetaste wird das Dialogfeld geschlossen.
   * Nach dem Signieren und Klicken auf &quot;OK&quot;bleibt der Fokus auf das Signatursteuerelement.

  **Signaturfunktion löschen:**

   * Über die Tabulatortaste kann auf ein klares Kreuzsymbol zum Löschen der Signatur zugegriffen werden.
   * Auf das Dialogfeld &quot;Signaturbestätigung löschen&quot;kann auch über die Registerkartennavigation zugegriffen werden.

  **Erweiterte Beschriftungen und Steuerelemente:**
   * Der Titel der Signaturschaltfläche für die Tastatur ist jetzt klarer und verwendet &quot;aria-label&quot;, um Funktionen anzukündigen (z. B. &quot;aria-label=&#39;Sign using Keyboard&#39;&quot;).
   * Der verbesserte Kontrast stellt sicher, dass alle Steuerelemente innerhalb der Freihandsignatur leicht zu unterscheiden sind.
   * Die Schaltfläche OK/Häkchen zeigt jetzt visuell an, wann sie inaktiv ist.

  **Signature Feedback für Screens-Reader:**
   * Wenn eine Signatur eingegeben wird, können Benutzer der Sprachausgabe den Text hören, der zum Erstellen der Signatur verwendet wird.

Diese Aktualisierung ermöglicht ein integrativeres Erlebnis für Benutzer mit Behinderungen, indem die Navigation, Klarheit und das Feedback für die Scribble-Signatur-Komponente verbessert werden.

### Early-Adopter-Programm {#forms-early-adopter}

* **[Senden eines adaptiven Formulars an das Adobe Workfront Fusion-Szenario](/help/forms/submit-adaptive-form-to-workfront-fusion.md)**: Forms as a Cloud Service bietet eine vordefinierte Option, um ein adaptives Formular mühelos mit Adobe Workfront zu verbinden. Dadurch wird der Prozess zum Senden eines adaptiven Formulars an ein Adobe Workfront-Szenario vereinfacht, indem Sie bei der Übermittlung eines adaptiven Formulars ein Workfront Fusion-Szenario auslösen können.

  <br/> ![Adobe Workfront](/help/forms/assets/adobe-workfront.png) <br/> Mit dem Adobe Workfront Fusion Connector können Sie Workflows entwickeln, die automatisch bei der Übermittlung eines adaptiven Formulars ausgelöst werden. Stellen Sie sich beispielsweise ein Szenario vor, bei dem ein Workflow initiiert wird, um einer bestimmten Person die Aufgabe zuzuweisen, die übermittelten Daten zu überprüfen, sodass ein Antrag auf Grundlage der im adaptiven Formular erfassten Informationen genehmigt oder abgelehnt werden kann. Diese optimierte Integration verbessert die Effizienz und bringt eine neue Automatisierungsstufe in Ihre Workflow-Prozesse.|

* **Reader Extension-Dienst**: AEM Forms Communication APIs bieten Reader Extension Service, mit dem Sie Funktionen wie das Ausfüllen von Formularen und das Kommentieren regulärer PDF hinzufügen können. So lassen sich diese interaktiv für Benutzer mit dem kostenlosen Adobe Reader gestalten.

* [Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/supporting-new-language-localization-core-components.md): Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt in einer RTL-Sprache (Right-to-Left) wie Arabisch, Persisch und Urdu angezeigt werden. RTL-Sprachen werden von über 2 Milliarden Menschen weltweit gesprochen. Durch die Verwendung eines Formulars in RTL-Sprache können Sie die Reichweite Ihrer adaptiven Formulare erweitern, um diese unterschiedlichen Zielgruppen zu bedienen und in RTL-Märkte einzutreten. In bestimmten Regionen ist es außerdem gesetzlich vorgeschrieben, Formulare in der jeweiligen Regionalsprache bereitzustellen. Durch die Anpassung an lokale Sprachen öffnen Sie nicht nur den Zugang zu einem breiteren Publikum, sondern sorgen auch für die Einhaltung der einschlägigen Gesetze und Vorschriften.

* **[Schützen Sie Ihre Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sondern sorgt auch für Seelenfrieden. Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies auch vorgesehen ist, die Dokumente ändern können.

  Sie können von Ihrer offiziellen E-Mail-ID aus an `aem-forms-ea@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

* **[Sie können den Datendienst Real User Monitoring (RUM) nutzen](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)**, um die Client-seitige Sammlung für AEM as a Cloud Service zu aktivieren.
Der Datendienst Real User Monitoring (RUM) bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktionen sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist nützlich für Kundinnen und Kunden, die entweder ein von Adobe verwaltetes CDN oder ein nicht von Adobe verwaltetes CDN verwenden. Für diejenigen, die ein nicht von Adobe verwaltetes CDN verwenden, kann jetzt außerdem die automatisierte Traffic-Berichterstellung aktiviert werden, sodass keine Traffic-Berichte mehr für Adobe freigegeben werden müssen.

  Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-rum-adopter@adobe.com`. Geben Sie in der E-Mail den Domain-Namen für jede Umgebung an, für die Sie RUM aktivieren möchten. Das Produkt-Team von Adobe aktiviert dann den Datendienst Real User Monitoring (RUM) für Sie.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Frühkindliche Betreuung {#foundation-early-adopter}

#### Warnhinweise zu Traffic-Filter-Regeln (früheres Adopter-Programm) {#traffic-filter-rules-alerts-early-adopter}

Die kürzlich veröffentlichte [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), die die optional lizenzierbaren Web Application Firewall (WAF)-Regeln enthalten, können Sie konfigurieren, welcher Traffic erlaubt oder verweigert werden soll.

Jetzt können Sie eine E-Mail senden **<aemcs-cdn-config-adopter@adobe.com>** , um dem Programm für frühe Benutzer beizutreten, damit Sie benachrichtigt werden können, sobald Ihre Traffic-Filterregeln ausgelöst werden. Aktionen Center-E-Mail-Benachrichtigungen informieren Sie darüber, wann bestimmte Traffic-Bedingungen eintreten, damit Sie geeignete Maßnahmen treffen können.

#### CDN-Konfiguration (Early Adopter Program) {#cdn-config-early-adopter}

Zusätzlich zu den kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), die die optional lizenzierbaren Web Application Firewall (WAF)-Regeln enthalten, gibt es eine Möglichkeit, die Configuration Pipeline zu verwenden, um andere Typen der CDN-Konfiguration zu deklarieren und bereitzustellen. [Weitere Infos](/help/implementing/dispatcher/cdn-configuring-traffic.md) und dem frühen Adoptionsprogramm durch E-Mail beitreten **<aemcs-cdn-config-adopter@adobe.com>** Zugriff auf:

* 301/302 Client-seitige Umleitungen
* Proxying-Anfragen am Rande zu beliebigen Ursprüngen (z. B. Nicht-AEM-Anwendungen)
* URL-Transformationen
* Festlegen oder Ändern von Anfragen- oder Antwortkopfzeilen
* benutzerdefinierte Fehlerseiten, wenn das CDN AEM nicht erreichen kann

#### Apache/Dispatcher Runtime-Erfassung von Rewrite-Maps (früheres Adopter-Programm) {#apache-rewritemaps-early-adopter}

Ähnlich wie bei AEM 6.5 erfassen Apache/Dispatcher Umschreibungen, die an einem bestimmten Speicherort im Publishing-Repository platziert werden, und laden sie, ohne dass eine Pipeline auf der Web-Ebene ausgeführt werden muss. Dies eröffnet Geschäftsbenutzern die Möglichkeit, Umleitungen über eine Benutzeroberfläche zu deklarieren, z. B. durch ACS Commons Redirect Map Manager. Bitte wenden Sie sich an **<aemcs-cdn-config-adopter@adobe.com>** für weitere Informationen.

#### Edge Side Includes (ESI) für das Laden dynamischer Inhalte (Early Adopter Program) {#esi-early-adopter}

Das Adobe Managed CDN unterstützt jetzt Edge Side Includes (ESI), eine Markup-Sprache für die dynamische Webinhaltassembly auf Edge-Ebene. Durch die Einbeziehung von ESI-Snippets können Sie die gesamte HTML-Seite im CDN mit höheren TTLs zwischenspeichern und gleichzeitig diejenigen kleineren-Abschnitte, die höhere Cadence-Updates erfordern (niedrigere TTLs), öfter aus der Quelle abrufen. Bitte wenden Sie sich an **<aemcs-cdn-config-adopter@adobe.com>** für weitere Informationen.

#### RDE-Unterstützung für Frontend-Code mithilfe von Site-Designs und Site-Vorlagen (Early Adopter-Programm) {#rde-frontend-early-adopter}

[Schnelle Entwicklungsumgebungen (Rapid Development Environments, RDEs)](/help/implementing/developing/introduction/rapid-development-environments.md) unterstützen jetzt Frontend-Code basierend auf [Site-Designs](/help/sites-cloud/administering/site-creation/site-themes.md) und [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md) für Early Adopters. Bei RDEs erfolgt dies über eine Befehlszeilenanweisung und nicht über eine [Frontend-Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md). Bitte wenden Sie sich an **<aemcs-rde-support@adobe.com>** , um es auszuprobieren und Feedback zu geben.

#### Verbesserte Protokollierung für RDEs (Early Adopter Program) {#rde-logging-early-adopter}

Beim Debugging von Code in einem [Rapid Development Environment (RDE)](/help/implementing/developing/introduction/rapid-development-environments.md)können Entwickler Protokolle jetzt effizienter konfigurieren und streamen, indem sie die Befehlszeile verwenden und ohne die OSGi-Eigenschaften in der Versionskontrolle zu ändern. Zu den Funktionen gehören:

* Deklarieren von Protokollebenen pro Paket- oder Klassenebene
* Anpassen des Protokollausgabeformats
* Mehrere Protokolle parallel streamen

Bitte wenden Sie sich an **<aemcs-rde-support@adobe.com>** , um es auszuprobieren und Feedback zu geben.

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

