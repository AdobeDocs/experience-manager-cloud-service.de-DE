---
title: Versionshinweise für Version 2024.3.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2024.3.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: b3816929-2c0a-4d6a-b583-c928d2182ecd
feature: Release Information
role: Admin
source-git-commit: 7f63f66cb1753fc32996e4672214eccc33ca8d92
workflow-type: tm+mt
source-wordcount: '2293'
ht-degree: 95%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2024.3.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2024.3.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2021 oder 2022 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.3.0) ist der 11. April 2024. Die nächste Version mit neuen Funktionen (2024.4.0) ist für den 25. April 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Werfen Sie einen Blick auf das Video „Versionsübersicht März 2024“ für eine Zusammenfassung der neuen Funktionen in der Version 2024.3.0:

>[!VIDEO](https://video.tv.adobe.com/v/3428342?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in [!DNL Experience Manager Sites] {#sites-features}

**AEM-Authoring für Edge Delivery Services**

AEM Sites kann jetzt als Inhaltsquelle für Edge Delivery Services verwendet werden. Autorinnen und Autoren verwalten ihre Websites in AEM mit dem neuen universellen Editor mit kontextbezogenem WYSIWYG-Authoring. Dies ermöglicht es Unternehmen, mit Edge Delivery Services schnelle und leistungsstarke Websites zu erstellen und gleichzeitig die leistungsstarken Funktionen von AEM für das Content-Management zu nutzen.

![AEM-Authoring](/help/edge/assets/universal_editor_edge_delivery_services.png)

Weitere Informationen finden Sie in der [Dokumentation](/help/edge/overview.md) und durch Ansehen von [AEM Gems – Erste Schritte mit AEM-Authoring und Edge Delivery Services](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/aem-gems-getting-started-with-aem-authoring-and-edge-delivery/m-p/652694?profile.language=de#M43905?lang=de)

**Universeller Editor für Headless-Implementierungen**

Der universelle Editor ermöglicht es auch entkoppelten Web-Anwendungen, das gleiche intuitive, kontextbezogene WYSIWYG-Authoring zu nutzen, das bisher nur für herkömmliche Sites verfügbar war. Erstellerinnen und Ersteller von Inhalten können nun Layouts mithilfe von Inhaltsfragmenten genauso einfach visuell zusammenstellen wie Komponenten innerhalb von Seiten.

Der universelle Editor zeichnet sich durch seine Anpassungsfähigkeit an verschiedene Web-Architekturen aus, indem er sowohl Server- als auch Client-seitiges Rendering unterstützt, Framework-agnostisch bleibt und die Notwendigkeit für ein AEM-Hosting eliminiert. Die Integration vorhandener Web-Anwendungen mit dem universellen Editor für die Inhaltsbearbeitung ist unkompliziert. In erster Linie müssen Entwickelnde bestimmte Datenattribute in ihr Markup integrieren.

Dadurch gewährleistet der universelle Editor ein konsistentes Bearbeitungserlebnis, unabhängig von der Inhaltsstruktur oder dem zugrunde liegenden Technologie-Stack. Weitere Informationen dazu finden Sie in der [Einführung zum universellen Editor](/help/implementing/universal-editor/introduction.md).

**Content-Management-OpenAPIs für Inhaltsfragmente und -modelle**

Entwickelnde können jetzt programmatisch mit Inhaltsfragmenten und Inhaltsfragmentmodellen interagieren und mithilfe von Content-Management-OpenAPIs CruD-Vorgänge für sie durchführen. Weitere Informationen finden Sie in der [API-Dokumentation](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/).

**Unterstützung für Multisite-Management für Experience Fragments**

Die Unterstützung von Multisite-Management wurde für Ordnerstrukturen erweitert, die Experience Fragments speichern, was Benutzenden den Rollout einer kompletten Inhaltsstruktur mit Experience Fragments ermöglicht.

**Vergleichen von Inhaltsfragmentversionen**

Mit dem neuen Inhaltsfragmenteditor können Inhaltsautorinnen und -autoren jetzt Unterschiede zwischen der aktuellen Version eines Inhaltsfragments und einer früheren Version vergleichen und anzeigen.

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzen Sie GenAI über die neue Funktion [Varianten generieren](/help/generative-ai/generate-variations.md) von AEM, die jetzt in Cloud Service verfügbar ist. „Varianten generieren“ hilft Ihnen bei der Erstellung und Skalierung von Inhalten durch den Einsatz generativer KI. Wenden Sie sich an Ihr Adobe-Accountteam, um sich für das Programm zu erkundigen.

**Durchsuchen von Assets in der Inhaltsfragmentkonsole**

Inhaltsautorinnen und -autoren können jetzt Bilder und andere Assets durchsuchen, anzeigen und bearbeiten, ohne die Inhaltsfragmentkonsole verlassen zu müssen.

![Durchsuchen von Assets](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Möchten Sie die Funktion ausprobieren und Feedback geben? Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an aemcs-headless-adopter@adobe.com senden, um am Early-Adopter-Programm teilzunehmen.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Admin-Ansicht {#admin-view}

**Native Integration mit Adobe Express**

Dank der nativen Integration von AEM Assets mit Adobe Express können Sie über die Adobe Express-Benutzeroberfläche direkt auf die in AEM Assets gespeicherten Assets zugreifen. Sie können in AEM Assets verwaltete Inhalte auf der Express-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte in einem AEM Assets-Repository speichern.

![Einschließen von Assets aus dem Assets-Add-on](/help/assets/assets/adobe-express-native-integration.png)

**Vorschau der Ausgabedarstellungen für alle unterstützten Videotypen**

Experience Manager Assets generiert jetzt standardmäßig Vorschaudarstellungen aller unterstützten Videotypen, ohne dass eine Verarbeitungsprofilkonfiguration erforderlich ist.

### Neue Funktionen in der Assets-Ansicht {#assets-view}

**Verwaltung von Zugriffsberechtigungen für Sammlungen**

Mit Assets Essentials können Admins die Zugriffsebenen für private Sammlungen verwalten, die im Repository verfügbar sind. Als Admin können Sie Benutzergruppen erstellen und diesen Gruppen Berechtigungen zum Verwalten von Zugriffsebenen zuweisen. Außerdem können Sie die Berechtigung zur Zugriffsberechtigungsverwaltung an Benutzergruppen delegieren.


## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Neue Funktionen für AEM Forms {#forms-new-features}

* **[Adobe Experience Manager Forms Edge Delivery Services](/help/edge/docs/forms/overview.md)**: Edge Delivery Services für AEM Forms ist ein zusammengesetzter Service, der eine schnelle Entwicklungsumgebung ermöglicht, in der Autoren neue Formulare schnell aktualisieren, veröffentlichen und starten können. Diese Dienste bieten außergewöhnliche und sehr wirkungsvolle Formularerlebnisse, die Interaktionen und Konversionen fördern. Diese Formularerlebnisse sind einfach zu erstellen und zu entwickeln.

  ![EDS Forms-Funktionen](/help/edge/assets/eds-forms-features.png)

Diese Dienste ermöglichen Ihnen Folgendes:

* Arbeiten Sie mit mehreren Inhaltsquellen auf derselben Formular-Site und verwenden Sie Ihre bevorzugten Authoring-Tools wie Microsoft Excel, Google Tabellen oder den Editor für adaptive Formulare.
* Bereitstellen digitaler Registrierungserlebnisse, die schnell geladen und gerendert werden können, und kontinuierliche Überwachung der Formularleistung durch Real-Use-Monitoring (RUM).
* Verwenden Sie einfaches HTML, modernes CSS und Vanilla JavaScript, um außergewöhnliche Erlebnisse zu erstellen und so die steile Lernkurve eines bestimmten Frameworks zu vermeiden.


### Neue Funktionen in der Vorabversion für AEM Forms {#forms-pre-release}

* **Verbesserter visueller Regeleditor für auf Kernkomponenten basierende adaptive Formulare**: Diese Version umfasst ein bedeutendes Upgrade des visuellen Regeleditors für adaptive Formulare, die auf Kernkomponenten basieren. Diese Version umfasst ein bedeutendes Upgrade des visuellen Regeleditors für adaptive Formulare, die auf Kernkomponenten basieren. Diese Aktualisierung konzentriert sich auf die Optimierung der Interaktionen mit benutzerdefinierten Funktionen und ermöglicht Ihnen so, robustere und effizientere Formulare zu erstellen.

  Sie können jetzt Interaktionen mit benutzerdefinierten Funktionen optimieren, indem Sie:

   * neue Anmerkungen nutzen, um klarere Funktionsdefinitionen bereitzustellen,
   * Caching-Mechanismen für benutzerdefinierte Funktionen verwenden, was zu einer schnelleren Formularleistung führt,
   * nahtlos mit globalen Objekten in benutzerdefinierten Funktionen arbeiten,
   * optionale Parameter in benutzerdefinierten Funktionen definieren und verwenden.

  Diese Aktualisierung umfasst außerdem die folgenden Verbesserungen an der Funktionalität des Regeleditors. Sie haben folgende Möglichkeiten:

   * Implementieren Sie eine leistungsstarke „Wenn-Dann-Sonst“-Logik für die bedingte Ausführung.
   * Nutzen Sie moderne JavaScript-Funktionen wie Let- und Pfeilfunktionen (ES10-Unterstützung).
   * Validieren oder setzen Sie nicht nur Felder zurück, sondern auch ganze Bedienfelder und Formulare, um die Kontrolle über Benutzerinteraktionen zu erweitern.

  Diese Verbesserungen bieten ein intuitiveres und leistungsfähigeres Erlebnis für das Erstellen von Regeln und benutzerdefinierten Funktionen im visuellen Regeleditor.

* **Erstellen mehrerer Versionen eines adaptiven Formulars**: Sie können jetzt problemlos Varianten vorhandener Formulare verwalten. Dies vereinfacht die Versionskontrolle und erleichtert den Vergleich für die Formularoptimierung – alles innerhalb eines einzigen, optimierten Workflows.

* **Vergleichen adaptiver Formulare**: Sie können jetzt ganz einfach zwei Formulare vergleichen, um Unterschiede zwischen ihnen zu identifizieren. Dies erleichtert die reibungslose Zusammenarbeit, da Team-Mitglieder nun Revisionen vergleichen und Änderungen effizient diskutieren können.

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

* **Reader Extension-Dienst**: AEM Forms Communication APIs hat den Reader Extension-Dienst eingeführt, der es Ihnen ermöglicht, Funktionen wie das Ausfüllen von Formularen und das Kommentieren in normalen PDFs hinzuzufügen und diese für Benutzende mit dem kostenlosen Adobe Reader interaktiv zu machen.

* [Unterstützung für Sprachen mit Rechts-nach-links-Schreibrichtung](/help/forms/supporting-new-language-localization-core-components.md): Adaptive Formulare, die auf Kernkomponenten basieren, können jetzt in einer RTL-Sprache (Right-to-Left) wie Arabisch, Persisch und Urdu angezeigt werden. RTL-Sprachen werden von über 2 Milliarden Menschen weltweit gesprochen. Durch die Verwendung eines Formulars in RTL-Sprache können Sie die Reichweite Ihrer adaptiven Formulare erweitern, um diese unterschiedlichen Zielgruppen zu bedienen und in RTL-Märkte einzutreten. In bestimmten Regionen ist es außerdem gesetzlich vorgeschrieben, Formulare in der jeweiligen Regionalsprache bereitzustellen. Durch die Anpassung an lokale Sprachen öffnen Sie nicht nur den Zugang zu einem breiteren Publikum, sondern sorgen auch für die Einhaltung der einschlägigen Gesetze und Vorschriften.

* **[Schützen Sie Ihre Dokumente mit DocAssurance-APIs (Teil der Kommunikations-APIs)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance-doc-assurance)**: Mit den DocAssurance-APIs können Sie vertrauliche Informationen schützen, indem Sie die Dokumente signieren und verschlüsseln. Durch Verschlüsselung werden die Inhalte eines Dokuments in ein unlesbares Format umgewandelt, sodass nur autorisierte Benutzende Zugriff erhalten. Diese verstärkte Schutzschicht schützt nicht nur wertvolle Daten vor unbefugten Blicken, sondern sorgt auch für Seelenfrieden. Der Signature-Service ermöglicht Ihrem Unternehmen, die Sicherheit und Vertraulichkeit verteilter und empfangener Adobe PDF-Dokumente zu gewährleisten. Dieser Service verwendet digitale Signaturen und Zertifizierung, um sicherzustellen, dass nur die Empfängerinnen und Empfänger, für die dies auch vorgesehen ist, die Dokumente ändern können.

  Sie können von Ihrer offiziellen E-Mail-ID aus an `aem-forms-ea@adobe.com` schreiben, um dem Early-Adopter-Programm beizutreten und Zugriff auf die Funktion anzufordern.

* **[Sie können den Real Use Monitoring (RUM)-Datendienst nutzen](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** um die Client-seitige Erfassung für AEM as a Cloud Service zu aktivieren.
Der Real Use Monitoring-Datendienst (RUM) bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktionen sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist nützlich für Kundinnen und Kunden, die entweder ein von Adobe verwaltetes CDN oder ein nicht von Adobe verwaltetes CDN verwenden. Für diejenigen, die ein nicht von Adobe verwaltetes CDN verwenden, kann jetzt außerdem die automatisierte Traffic-Berichterstellung aktiviert werden, sodass keine Traffic-Berichte mehr für Adobe freigegeben werden müssen.

  Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-rum-adopter@adobe.com`. Geben Sie in der E-Mail den Domain-Namen für jede Umgebung an, für die Sie RUM aktivieren möchten. Das Produkt-Team von Adobe wird dann den Real Use Monitoring (RUM)-Datendienst für Sie aktivieren.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Early-Adopter-Programm {#foundation-early-adopter}

#### Warnhinweise zu Traffic-Filterregeln (Early-Adopter-Programm) {#traffic-filter-rules-alerts-early-adopter}

Die kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), die die optional lizenzierbaren WAF-Regeln (Web Application Firewall) enthalten, ermöglichen es Ihnen zu konfigurieren, welcher Traffic erlaubt oder verweigert werden soll.

Sie können jetzt eine E-Mail an **<aemcs-cdn-config-adopter@adobe.com>** senden, um dem Early-Adopter-Programm beizutreten, damit Sie benachrichtigt werden, sobald Ihre Traffic-Filterregeln ausgelöst werden. Aktionszentrum-E-Mail-Benachrichtigungen informieren Sie darüber, wann bestimmte Traffic-Bedingungen eintreten, damit Sie geeignete Maßnahmen treffen können.

#### CDN-Konfiguration (Early-Adopter-Programm) {#cdn-config-early-adopter}

Zusätzlich zu den kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), welche die optional lizenzierbaren WAF-Regeln (Web Application Firewall) enthalten, gibt es eine Möglichkeit, die Konfigurations-Pipeline zum Deklarieren und Bereitstellen anderer Typen von CDN-Konfigurationen zu verwenden. [Weitere Informationen dazu finden Sie hier](/help/implementing/dispatcher/cdn-configuring-traffic.md). Sie haben außerdem die Möglichkeit, dem Early-Adopter-Programm beitreten. Schreiben Sie einfach eine E-Mail an **<aemcs-cdn-config-adopter@adobe.com>**, um Zugriff zu den folgenden Ressourcen zu erhalten:

* 301/302 Server-seitige Weiterleitungen
* Weiterleitungs-Anfragen am Edge zu beliebigen Ursprüngen (z. B. nicht-AEM-Anwendungen)
* URL-Transformationen
* Festlegen oder Ändern von Anfragen- oder Antwortkopfzeilen
* benutzerdefinierte Fehlerseiten, wenn das CDN AEM nicht erreichen kann

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
