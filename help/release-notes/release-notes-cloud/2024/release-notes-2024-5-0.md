---
title: Versionshinweise für Version 2024.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2024.5.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 7b7a27f9-ba57-4eb2-9fcb-653b5213af04
source-git-commit: 8be0a9894bb5b3a138c0ec40a437d6c8e4bc7e25
workflow-type: tm+mt
source-wordcount: '1943'
ht-degree: 98%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2024.5.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2024.5.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2022 oder 2023 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Weitere Informationen zu Aktualisierungen der Dokumentation, die nicht direkt mit einer Version zusammenhängen, finden Sie unter [Aktuelle Aktualisierungen der Dokumentation](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/doc-updates/documentation-updates.html?lang=de).

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.5.0) ist der 30. Mai 2024. Die nächste Version (2024.6.0) ist für den 27. Juni 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2024.5.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version vom Mai 2024:

>[!VIDEO](https://video.tv.adobe.com/v/3448071?quality=12&captions=ger)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in Sites {#sites-new-features}

#### AEM-Übersetzungsintegration {#translation-integration}

Aktionen zur Übersetzung von Inhalten und Workflows lösen jetzt Ereignisse aus, damit Sie relevante Prozessschritte und Status aus externen Anwendungen verfolgen können. Die folgenden Ereignisse werden generiert. Benutzende können Ereignisse über die Adobe Developer Console abonnieren.

* `TRANSLATION_JOB_CREATED`
* `TRANSLATION_JOB_CONTENT_ADDITION_STARTED`
* `TRANSLATION_JOB_CONTENT_ADDITION_COMPLETED`
* `TRANSLATION_JOB_CONTENT_DELETION_STARTED`
* `TRANSLATION_JOB_CONTENT_DELETION_COMPLETED`
* `TRANSLATION_JOB_COMMITTED_FOR_TRANSLATION`
* `TRANSLATION_JOB_READY_FOR_REVIEW`
* `TRANSLATION_JOB_APPROVED`
* `TRANSLATION_JOB_COMPLETED`
* `TRANSLATION_JOB_CANCELLED`
* `TRANSLATION_JOB_ERROR`

#### Telemetrieservice {#real-use-monitoring}

* **[Operational Telemetry Service ist jetzt allgemein verfügbar](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)** was Client-seitige Datenerfassung für AEM as a Cloud Service ermöglicht.
Der Real User Monitoring-Dienst, die Client-seitige Erfassung, bietet eine präzisere Darstellung der Interaktionen und stellt eine zuverlässige Messung der Website-Interaktionen sicher. Dadurch erhält die Kundschaft erweiterte Einblicke in ihren Seiten-Traffic und die Performance. Es ist eine großartige Möglichkeit, mehr über Ihre Seiten-Performance zu erfahren und Einblicke zu gewinnen, um sie zu verbessern.

#### AEM-Authoring für Edge Delivery Services {#edge-enhancements}

Verbesserte Stabilität und verschiedene Verbesserungen für ein besseres Authoring-Erlebnis.

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzen Sie GenAI über die neue Funktion [Varianten generieren](/help/generative-ai/generate-variations.md) von AEM, die jetzt in Cloud Service verfügbar ist. „Varianten generieren“ hilft Ihnen bei der Erstellung und Skalierung von Inhalten durch den Einsatz generativer KI. Wenden Sie sich an Ihr Adobe-Accountteam, um sich für das Programm zu erkundigen.

**Durchsuchen von Assets in der Inhaltsfragmentkonsole**

Inhaltsautorinnen und -autoren können jetzt Bilder und andere Assets durchsuchen, anzeigen und bearbeiten, ohne die Inhaltsfragmentkonsole verlassen zu müssen.

![Durchsuchen von Assets](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Möchten Sie die Funktion ausprobieren und Feedback geben? Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an aemcs-headless-adopter@adobe.com senden, um am Early-Adopter-Programm teilzunehmen.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in der Admin-Ansicht {#admin-view-new-features}

* WebM ist jetzt eine unterstützte Ausgabedatei im Verarbeitungsprofil für Videos.
* MP4 wird jetzt in der nativen Integration von AEM in Express (Import und Export) unterstützt.

### Neue Funktionen in der Assets-Ansicht {#assets-view-new-features}

**Veröffentlichen von Assets in AEM und Dynamic Media**

Mit Experience Manager Assets können Sie jetzt über die Asset-Ansicht schnell [Assets in Experience Manager und Dynamic Media veröffentlichen](/help/assets/publish-assets-to-aem-and-dm.md), ohne zur Admin-Ansicht wechseln zu müssen. Sie können Assets beim Hochladen, Durchsuchen und Suchen von Assets veröffentlichen.

![Prüfen des Veröffentlichungsstatus1](/help/assets/assets/check-publish-status1.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Neue, vorab veröffentlichte Funktionen in AEM Forms {#forms-new-prerelease-features}

#### Verbesserter visueller Regeleditor für auf Kernkomponenten basierende adaptive Formulare

Diese Version umfasst ein bedeutendes Upgrade des visuellen Regeleditors für adaptive Formulare, die auf Kernkomponenten basieren. Sie haben nun die folgenden Möglichkeiten:

* Erstellen Sie Regeln im visuellen Regeleditor, um [Standard-Nachrichten zur erfolgreichen/fehlerhaften Formularübermittlung zu überschreiben](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* Im Regeleditor für adaptive Formulare wurde die Möglichkeit hinzugefügt, [verschiedene Feldtypen für den WHEN-Vorgang auszuwählen](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when).

* Autorinnen und Autoren von Formularen können jetzt benutzerdefinierte Funktionen anwenden, um [Daten vor der Übermittlung vorab zu verarbeiten](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server).

* Verwenden Sie die Funktion [**Als Entwurf speichern**](/help/forms/save-core-component-based-form-as-draft.md) zum Speichern teilweise ausgefüllter Formulare für eine spätere Übermittlung. Dies ist in Szenarien nützlich, in denen Benutzende das Ausfüllen eines Formulars unterbrechen und später fortsetzen müssen.



### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen eine einmalige Möglichkeit, vor allen anderen einen exklusiven Zugang zu bahnbrechenden Neuerungen zu erhalten und ihre weitere Entwicklung mitzugestalten. Das Programm bietet Zugriff auf verschiedene Innovationen.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### Verbesserte Bot-Schutzmethoden

In AEM Forms wurden die Sicherheitsfunktionen verbessert, indem jetzt zwei gängige CAPTCHA-Lösungen unterstützt werden: Cloudflare Turnstile und hCaptcha. Dies ergänzt das bereits verfügbare Google reCAPTCHA und bietet Benutzenden mehr Auswahl und Flexibilität beim Schutz ihrer Formulare vor Bots und Spam-Übermittlungen.

* **Cloudflare Turnstile**: Dieses reibungslose CAPTCHA überprüft Benutzende anhand einer einfachen Aufgabe, die keine explizite Interaktion erfordert. Es lässt sich nahtlos in Ihre Formulare integrieren und verbessert so das Benutzererlebnis.
* **hCaptcha**: Dieses datenschutzorientierte CAPTCHA bietet eine benutzerfreundliche Alternative mit dem Schwerpunkt auf Datenschutz. Ziel ist es, ein Gleichgewicht zwischen Sicherheit und Benutzererlebnis herzustellen.
* **Google reCAPTCHA**: AEM Forms unterstützt weiterhin sowohl reCAPTCHA v2 als auch reCAPTCHA Enterprise und bietet damit eine zuverlässige und bewährte Lösung.

Durch die Bereitstellung mehrerer CAPTCHA-Optionen haben Sie in AEM Forms die Möglichkeit, die Lösung auszuwählen, die Ihren spezifischen Anforderungen am besten entspricht.

Sind Sie bereit, eine dieser CAPTCHA-Lösungen in Ihre adaptiven Formulare zu integrieren? In unserer Dokumentation finden Sie detaillierte Anweisungen zu jedem Thema: [Cloudflare Turnstile](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [hCaptcha](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components) und [Google reCAPTCHA](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Forms-Dienst

Der Forms-Dienst generiert interaktive PDF-Formulare für die Datenerfassung. Er kann auch verwendet werden, um Daten in ein vorhandenes interaktives PDF-Formular zu importieren oder daraus zu exportieren und um gesendete Daten zu validieren. Im Folgenden finden Sie eine Aufschlüsselung der Funktionen:

* **Rendern von Formularen**: Generieren Sie ein interaktives PDF-Formular aus einer Vorlage, die mit AEM Forms Designer und (optional) mit XML-Daten erstellt wurde. Dadurch wird im Wesentlichen ein ausfüllbares PDF-Formular erzeugt, das optional mit Daten vorausgefüllt ist.
* **Datenextraktion und -import**: Importieren Sie Daten in ein vorhandenes PDF-Formular und extrahieren Sie Daten aus einem ausgefüllten PDF-Formular. Es wird sowohl das XDP- als auch das XML-Datenformat unterstützt, und der Import in PDF-Formulare, die nicht im XFA-Format sind (auch AcroForms genannt), unterstützt zusätzlich FDF- und XFDF-Daten.
* **Datenvalidierung**: Validieren Sie die gesendeten Daten im XDP- oder XML-Format anhand einer mit AEM Forms Designer erstellten Vorlage.

>[!IMPORTANT]
>
> Wenn Sie Interesse haben, an unserem Early-Access-Programm für Early-Access-Innovationen teilzunehmen, senden Sie einfach eine E-Mail von Ihrer offiziellen Adresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com), um Zugriff anzufordern. Sie können Zugriff auf alle oder auf spezifische Innovationen anfordern.


## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Unterstützung für OAuth-Server-zu-Server-Anmeldedaten für AEM-Integrationen mit anderen Adobe-Lösungen {#S2S-OAuth-credentials}

Die Adobe Developer Console wird verwendet, um Anmeldedaten für den Zugriff auf verschiedene APIs zu generieren. Einer dieser Typen von Anmeldedaten, die Anmeldedaten für Dienstkonten (JWT), wurde zugunsten von OAuth-Server-zu-Server-Anmeldedaten eingestellt, die von AEM Cloud Service jetzt für Integrationen mit anderen Adobe-Lösungen wie Adobe Analytics und Adobe Target unterstützt werden.

[Lesen Sie die Informationen zur Einstellung](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md) und [erfahren Sie, wie Sie die AEM Author-Benutzeroberfläche verwenden](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md), um Integrationen mit anderen Adobe-Lösungen zu konfigurieren.

### Warnungen zu Traffic-Spitze am Ursprung {#traffic-spike-origin}

[Empfangen Sie proaktive Benachrichtigungen](/help/security/traffic-filter-rules-including-waf.md#traffic-spike-at-origin-alert) über das Aktionszentrum, wenn Traffic-Muster am Ursprung auf einen DDoS-Angriff hindeuten, sodass Sie Traffic-Filterregeln untersuchen und konfigurieren können.

### Neue Funktionen für RDEs {#RDE-new-features}

Mit [schnellen Entwicklungsumgebungen (Rapid Development Environments, RDEs)](/help/implementing/developing/introduction/rapid-development-environments.md) können Entwicklerinnen und Entwickler Änderungen schnell in der Cloud bereitstellen, überprüfen und testen. Im Juni werden mehrere neue Funktionen eingeführt. Wir laden Sie auch ein, sich direkt mit Adobe Engineering im [RDE Discord-Kanal](https://discord.com/channels/1131492224371277874/1245304281184079872) in Verbindung zu setzen.


#### RDE-Unterstützung für Frontend-Code mithilfe von Site-Designs und Site-Vorlagen {#rde-frontend}

[RDEs unterstützen jetzt Frontend-Code](/help/implementing/developing/introduction/rapid-development-environments.md#deploying-themes-to-rde) basierend auf [Site-Designs](/help/sites-cloud/administering/site-creation/site-themes.md) und [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md) für Early Adopters. Bei RDEs erfolgt dies über eine Befehlszeilenanweisung und nicht über eine [Frontend-Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).

#### Verbesserte Protokollierung für RDEs {#rde-logging}

Beim Debugging von Code in einer RDE können Entwicklerinnen und Entwickler Protokolle jetzt [produktiver konfigurieren und streamen](/help/implementing/developing/introduction/rapid-development-environments.md#rde-logging), indem sie die Befehlszeile verwenden, und das, ohne die OSGi-Eigenschaften in der Versionskontrolle zu ändern. Zu den Funktionen gehören:

* Deklarieren von Protokollebenen auf Paket- oder Klassenebene
* Anpassen des Protokollausgabeformats
* Mehrere Protokolle parallel streamen

#### RDE-CLI-Verbesserungen {#rde-cli-enhancements}

Die RDE-Befehlszeilenschnittstelle weist einige neue Funktionen auf, die das Entwicklererlebnis verbessern:

* [Der Setup-Befehl ist interaktiv](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools-interactive), was die Auswahl von Organisationen, Programmen und Umgebungen erleichtert. Es ist jetzt auch möglich, diese Werte an der Befehlszeile zu überschreiben.
* [Stiller Modus](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) für eine weniger ausführliche Ausgabe.
* [JSON-Modus](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) für nützliche Ausgaben, wenn sie programmgesteuert aufgerufen werden.

### Neue Benachrichtigungen im Aktionszentrum {#actions-center-notifications}

Das [Aktionszentrum](/help/operations/actions-center.md) sendet E-Mail-Benachrichtigungen, wenn wichtige Vorfälle auftreten oder wenn etwas in Ihrem Code oder in Ihrer Konfiguration festgestellt wird, das proaktive Maßnahmen erfordert. Es gibt drei neue Arten von Benachrichtigungen:

* Zu viele ausgehende Verbindungen über die erweiterte Netzwerkinfrastruktur
* Verwendung eines veralteten Formats für die Dienstbenutzerzuordnung
* Es findet ein potenzieller DDoS-Angriff statt

### Early-Adopter-Programm {#foundation-early-adopter}

Senden Sie eine E-Mail an **<aemcs-cdn-config-adopter@adobe.com>**, die angibt, für welche der unten aufgeführten Programme Sie sich interessieren.

#### Bereinigen von Inhalten im CDN mit einem Self-Service-API-Schlüssel (Early-Adopter-Programm) {#purge-cdn}

Registrieren Sie per Self-Service einen CDN-Bereinigungs-API-Schlüssel und verwenden Sie ihn zum Invalidieren von Inhalten im CDN, entweder global oder für eine oder mehrere Ressourcen. [Weitere Informationen](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Self-Service-Erstellung von X-AEM-Edge-Key für kundenseitig verwaltetes CDN (BYOCDN) (Early-Adopter-Programm) {#byocdn-keys}

Zuvor war ein Support-Ticket erforderlich, um den X-AEM-Edge-Key zu generieren, der für die Konfiguration eines kundenseitig verwalteten CDN erforderlich war. Dies kann jetzt durch eine Konfigurationsdatei selbst durchgeführt werden, die mithilfe der Konfigurations-Pipeline bereitgestellt wird. Dadurch werden alle Verzögerungen beim Onboarding in eine neue Umgebung beseitigt. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Server-seitige Weiterleitungen (Early-Adopter-Programm) {#server-side-redirects-early-adopter}

Konfigurieren Sie Server-seitige 301/302-Weiterleitungen in der Quell-Code-Verwaltung und stellen Sie sie im CDN bereit. [Weitere Informationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#server-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Beachten Sie, dass im Zusammenhang mit der [CDN-Konfiguration](/help/implementing/dispatcher/cdn-configuring-traffic.md) mehrere weitere Funktionen bereits verfügbar sind, einschließlich Anfrage- und Antworttransformationen und Routing des Traffics zu Nicht-AEM-Sites.

#### Warnhinweise zu Traffic-Filterregeln (Early-Adopter-Programm) {#traffic-filter-rules-alerts-early-adopter}

Die kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), die die optional lizenzierbaren WAF-Regeln (Web Application Firewall) enthalten, ermöglichen es Ihnen zu konfigurieren, welcher Traffic erlaubt oder verweigert werden soll.

Nehmen Sie am Early-Adopter-Programm teil, damit Sie benachrichtigt werden, sobald Ihre Traffic-Filterregeln ausgelöst werden. E-Mail-Benachrichtigungen durch das Aktionszentrum informieren Sie darüber, wann bestimmte Traffic-Bedingungen eintreten, damit Sie geeignete Maßnahmen treffen können.

#### Business-Anwenderinnen und -Anwender können Umleitungen außerhalb von Git deklarieren (Early-Adopter-Programm). {#apache-rewritemaps-early-adopter}

Ähnlich wie bei AEM 6.5 erfassen Apache/Dispatcher Rewrite-Zuordnungen, die an einem bestimmten Speicherort im Veröffentlichungs-Repository platziert werden, und laden sie, ohne dass eine Pipeline auf der Web-Ebene ausgeführt werden muss. Dies eröffnet Business-Anwenderinnen und -Anwendern die Möglichkeit, Umleitungen entweder mithilfe einer Tabelle oder einer Benutzeroberfläche zu deklarieren, z. B. wie durch den ACS Commons Redirect Map Manager bereitgestellt oder im Rahmen einer Kundenanwendung erstellt. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) für das Laden dynamischer Inhalte (Early-Adopter-Programm) {#esi-early-adopter}

Das von Adobe verwaltete CDN unterstützt jetzt [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), eine Markup-Sprache für die dynamische Zusammenführung von Web-Inhalten auf Edge-Ebene. Durch die Einbeziehung von ESI-Snippets können Sie die gesamte HTML-Seite im CDN mit höheren TTLs zwischenspeichern und gleichzeitig diejenigen kleineren Abschnitte, die höhere Intervall-Updates (niedrigere TTLs) erfordern, öfter aus der Quelle abrufen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] Guides {#guides}

* **Veröffentlichen eines Themas oder seiner Elemente in einem Experience Fragment**
Sie können jetzt mit Experience Manager Guides ein Thema oder dessen Elemente in einem Experience Fragment veröffentlichen. Ein Experience Fragment ist eine modulare Inhaltseinheit, die sowohl Inhalt als auch Layout integriert. Experience Fragments können Ihnen insbesondere beim Erstellen konsistenter und ansprechender Erlebnisse helfen.
* **Möglichkeit, die Themen-Asset-Metadaten an die native PDF-Ausgabe zu übergeben**
Sie können die Themen-Asset-Metadaten beim Generieren der nativen PDF-Ausgabe hinzufügen. Mit dieser Funktion können Sie bestimmte Metadaten für verschiedene Themen wie Thementitel und Autorin bzw. Autor zu den Kopf- und Fußzeilen der Themenseite hinzufügen.

Weitere Informationen zu den neuen und verbesserten Funktionen sowie zu den Problemen, die in der Version behoben wurden, finden Sie in der [Roadmap für Experience Manager Guides-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Versionshinweise zu Experience Cloud {#experience-cloud}

Informationen zu Versionen anderer Experience Cloud-Anwendungen finden Sie [hier](https://experienceleague.adobe.com/de/docs/release-notes/experience-cloud/current).
Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.
