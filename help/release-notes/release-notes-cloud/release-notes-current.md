---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
source-git-commit: 32d8477f85edf7fc33a0558e886c5fbb4854f8e5
workflow-type: tm+mt
source-wordcount: '1847'
ht-degree: 33%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.5.0) ist der Freitag, 30. Mai 2024. Die nächste Version (2024.6.0) ist für den Freitag, 27. Juni 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2024.5.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version vom Mai 2024:

>[!VIDEO](https://video.tv.adobe.com/v/3429503?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktionen in Sites {#sites-new-features}

**AEM-Authoring für Edge Delivery Services**

Verbesserte Stabilität und verschiedene Verbesserungen für eine bessere Inhaltserstellung.

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

Mit Experience Manager Assets können Sie jetzt schnell [Veröffentlichen von Assets in Experience Manager und Dynamic Media](/help/assets/publish-assets-to-aem-and-dm.md) über die Asset-Ansicht, ohne zur Admin-Ansicht zu wechseln. Sie können Assets beim Hochladen, Durchsuchen und Suchen nach Assets veröffentlichen.

![Prüfung des Veröffentlichungsstatus1](/help/assets/assets/check-publish-status1.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Neue Funktionen vor der Veröffentlichung in AEM Forms {#forms-new-prerelease-features}

#### Verbesserter visueller Regeleditor für auf Kernkomponenten basierende adaptive Forms

Diese Version umfasst ein bedeutendes Upgrade des visuellen Regeleditors für adaptive Formulare, die auf Kernkomponenten basieren. Sie haben nun die folgenden Möglichkeiten:

* Erstellen Sie Regeln im Visual Rule Editor, um [Überschreiben der standardmäßigen Prozess-Übermittlungs-Erfolgs-/Fehler-Handler für Formulare](/help/forms/create-and-use-custom-functions.md#field-and-global-scope-objects-in-custom-functions).

* Im Regeleditor für adaptive Forms wurde die Möglichkeit hinzugefügt, [Auswahl verschiedener Feldtypen für den WHEN-Vorgang](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when).

* Formularautoren können jetzt benutzerdefinierte Funktionen auf [Vorverarbeitung von Daten vor der Übermittlung](/help/forms/create-and-use-custom-functions.md#field-and-global-scope-objects-in-custom-functions).

* Verwenden Sie die [**Als Entwurf speichern**](/help/forms/save-core-component-based-form-as-draft.md) Funktion zum Speichern teilweise ausgefüllter Formulare für die spätere Übermittlung. Dies ist in Szenarien nützlich, in denen Benutzer das Ausfüllen eines Formulars unterbrechen und später zu ihm zurückkehren müssen.



### Funktionen früherer Anwender in AEM Forms {#forms-new-early-adopter-features}

Das AEM Forms Early Adopter Program bietet Ihnen die einmalige Möglichkeit, vor allen anderen exklusiven Zugang zu innovativen Technologien zu erhalten und ihre Entwicklung zu gestalten.
Das Programm bietet Zugriff auf verschiedene Innovationen.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Programms für frühzeitige Teilnehmer verfügbaren Innovationen finden Sie unter [Dokumentation zum AEM Forms Early Adopter Program](/help/forms/early-adopter-ea-features.md).

#### Verbesserte Bot-Schutzmethoden

AEM Forms hat seine Sicherheitsfunktionen verbessert, indem es zwei gängige CAPTCHA-Lösungen unterstützt: Cloudflare Turnstile und hCaptcha. Dies ergänzt die bereits verfügbare Google reCAPTCHA, die Benutzern mehr Auswahl und Flexibilität beim Schutz ihrer Formulare vor Bots und Spam-Einsendungen bietet.

* **Cloudflare Turnstile**: Dieses reibungslose CAPTCHA überprüft Benutzer anhand einer einfachen Herausforderung, die keine explizite Interaktion erfordert. Es lässt sich nahtlos in Ihre Formulare integrieren und verbessert so das Benutzererlebnis.
* **Captcha**: Diese datenschutzorientierte CAPTCHA bietet eine benutzerfreundliche Alternative mit dem Schwerpunkt Datenschutz. Ziel ist es, ein Gleichgewicht zwischen Sicherheit und Anwendererlebnis herzustellen.
* **Google reCAPTCHA**: AEM Forms unterstützt weiterhin sowohl reCAPTCHA v2 als auch reCAPTCHA Enterprise und bietet eine zuverlässige und bewährte Lösung.

Durch die Bereitstellung mehrerer CAPTCHA-Optionen haben Sie in AEM Forms die Möglichkeit, die Lösung auszuwählen, die Ihren spezifischen Anforderungen am besten entspricht.

Sind Sie bereit, eine dieser CAPTCHA-Lösungen in Ihre adaptive Forms zu integrieren? In unserer Dokumentation finden Sie detaillierte Anweisungen zu jedem Thema: [Cloudflare Turnstile](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [Captcha](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components), und [Google reCAPTCHA](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Formularservice

Der Forms-Dienst generiert interaktive PDF forms für die Datenerfassung. Sie kann auch verwendet werden, um Daten in ein und aus einem vorhandenen interaktiven PDF-Formular zu importieren und gesendete Daten zu validieren. Im Folgenden finden Sie eine Aufschlüsselung der Funktionen:

* **Rendern von Forms**: Generieren Sie ein interaktives PDF-Formular aus einer Vorlage, die mit AEM Forms Designer und optional mit XML-Daten erstellt wurde. Dadurch wird im Wesentlichen ein ausfüllbares PDF-Formular erzeugt, das optional mit Daten vorausgefüllt ist.
* **Datenextraktion und -import**: Importieren Sie Daten in ein vorhandenes PDF-Formular und extrahieren Sie Daten aus einem ausgefüllten PDF-Formular. Es werden sowohl XDP- als auch XML-Datenformate unterstützt, und der Import in Nicht-XFA-PDF forms (auch AcroForms genannt) unterstützt zusätzlich FDF- und XFDF-Daten.
* **Datenvalidierung**: Validieren Sie die gesendeten Daten im XDP- oder XML-Format anhand einer mit AEM Forms Designer erstellten Vorlage.

>[!IMPORTANT]
>
> Wenn Sie Interesse haben, an unserem Early Adopter-Programm für eine frühe Adopter-Innovation teilzunehmen, senden Sie einfach eine E-Mail von Ihrer offiziellen Adresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) , um Zugriff anzufordern. Sie können Zugriff auf alle oder auf jede spezifische Innovation anfordern.


## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### OAuth Server-zu-Server-Anmeldeinformationen-Unterstützung für AEM Integrationen mit anderen Adobe-Lösungen {#S2S-OAuth-credentials}

Adobe Developer Console wird verwendet, um Anmeldeinformationen für den Zugriff auf verschiedene APIs zu generieren. Einer dieser Berechtigungstypen, die Anmeldedaten für Dienstkonten (JWT), wurde zugunsten von OAuth Server-zu-Server-Anmeldedaten eingestellt, die von AEM Cloud Service jetzt für Integrationen mit anderen Adobe-Lösungen wie Adobe Analytics und Adobe Target unterstützt werden.

[Informationen zur veralteten Version](/help/security/jwt-credentials-deprecation-in-adobe-developer-console.md) und [Erfahren Sie, wie Sie die AEM Author-Benutzeroberfläche verwenden](/help/security/setting-up-ims-integrations-for-aem-as-a-cloud-service.md) um Integrationen mit anderen Adobe-Lösungen zu konfigurieren.

### Traffic-Spitze bei Ursprungswarnungen {#traffic-spike-origin}

[Proaktive Benachrichtigungen empfangen](/help/security/traffic-filter-rules-including-waf.md#traffic-spike-at-origin-alert) über das Aktionszentrum, wenn Traffic-Muster am Ursprung auf einen DDoS-Angriff hindeuten, sodass Sie Traffic-Filterregeln untersuchen und konfigurieren können.

### Neue Funktionen für RDEs {#RDE-new-features}

[Rapid Development Environments (RDEs)](/help/implementing/developing/introduction/rapid-development-environments.md) Entwickler können Änderungen in der Cloud schnell bereitstellen, überprüfen und testen. Im Juni werden mehrere neue Funktionen eingeführt. Wir laden Sie auch ein, sich direkt mit Adobe-Engineering am [RDE Discover-Kanal](https://discord.com/channels/1131492224371277874/1245304281184079872).


#### RDE-Unterstützung für Frontend-Code mithilfe von Site-Designs und Site-Vorlagen {#rde-frontend}

[RDEs unterstützen jetzt Front-End-Code](/help/implementing/developing/introduction/rapid-development-environments.md#deploying-themes-to-rde) basierend auf [Site-Designs](/help/sites-cloud/administering/site-creation/site-themes.md) und [Site-Vorlagen](/help/sites-cloud/administering/site-creation/site-templates.md), für frühe Anwender. Bei RDEs erfolgt dies über eine Befehlszeilenanweisung und nicht über eine [Front-End-Pipeline](/help/sites-cloud/administering/site-creation/enable-front-end-pipeline.md).

#### Verbesserte Protokollierung für RDEs {#rde-logging}

Beim Debugging von Code in einer RDE können Entwickler jetzt [produktivere Konfiguration und Streaming von Protokollen](/help/implementing/developing/introduction/rapid-development-environments.md#rde-logging), unter Verwendung der Befehlszeile und ohne Ändern der OSGi-Eigenschaften in der Versionskontrolle. Zu den Funktionen gehören:

* Deklarieren der Protokollebenen auf einer Paket- oder Klassenebene
* Anpassen des Protokollausgabeformats
* Paralleles Streaming mehrerer Protokolle

#### RDE-CLI-Verbesserungen {#rde-cli-enhancements}

Die RDE-Befehlszeilenschnittstelle weist einige neue Funktionen auf, die das Entwicklererlebnis verbessern:

* [der Setup-Befehl interaktiv ist](/help/implementing/developing/introduction/rapid-development-environments.md#installing-the-rde-command-line-tools-interactive), was die Auswahl zwischen Organisationen, Programmen und Umgebungen erleichtert. Es ist jetzt auch möglich, diese Werte an der Befehlszeile zu überschreiben.
* [Stiller Modus](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) für eine weniger ausführliche Ausgabe.
* [JSON-Modus](/help/implementing/developing/introduction/rapid-development-environments.md#global-flags) für nützliche Ausgaben, wenn sie programmatisch aufgerufen werden.

### Neue Mitteilungen zu Aktionsscentern {#actions-center-notifications}

[Aktionszentrum](/help/operations/actions-center.md) sendet E-Mail-Benachrichtigungen, wenn wichtige Vorfälle auftreten oder wenn wir etwas über Ihren Code oder Ihre Konfiguration feststellen, wo Sie proaktive Maßnahmen ergreifen sollten. Es gibt drei neue Arten von Benachrichtigungen:

* zu viele ausgehende Verbindungen über erweiterte Netzwerkinfrastruktur
* Verwendung eines veralteten Dienstbenutzerzuordnungsformats
* ein potenzieller DDoS-Angriff im Gange ist

### Early-Adopter-Programm {#foundation-early-adopter}

Email **<aemcs-cdn-config-adopter@adobe.com>**, die angibt, für welche der unten aufgeführten Programme Sie sich interessieren.

#### Bereinigen von Inhalten im CDN mit einem Self-Service-API-Schlüssel (Early Adopter Program) {#purge-cdn}

Registrieren Sie einen CDN-Bereinigungs-API-Schlüssel auf Self-Service-Art und verwenden Sie ihn zum Invalidieren von Inhalten im CDN, entweder global oder für eine oder mehrere Ressourcen. [Weitere Informationen](/help/implementing/dispatcher/cdn-cache-purge.md)

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Self-Service-Erstellung von X-AEM-Edge-Key für kundenverwaltetes CDN (BYOCDN) (Early Adopter Program) {#byocdn-keys}

Zuvor war ein Support-Ticket erforderlich, um den X-AEM-Edge-Key zu generieren, der für die Konfiguration eines kundenverwalteten CDN erforderlich war. Dies lässt sich jetzt durch eine Konfigurationsdatei selbst durchführen, die mithilfe der Configuration Pipeline bereitgestellt wird. Dadurch werden alle Verzögerungen beim Einstieg in eine neue Umgebung beseitigt. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value)

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Client-seitige Weiterleitungen (Early Adopter-Programm) {#client-side-redirects-early-adopter}

Konfigurieren Sie Client-seitige Weiterleitungen vom Typ 301/302 in der Quell-Code-Verwaltung und stellen Sie sie im CDN bereit. [Weitere Informationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors)<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Beachten Sie, dass im Zusammenhang mit [CDN-Konfiguration](/help/implementing/dispatcher/cdn-configuring-traffic.md), einschließlich Anforderung- und Antworttransformationen und Routing des Traffics zu AEM Sites.

#### Warnhinweise zu Traffic-Filterregeln (Early-Adopter-Programm) {#traffic-filter-rules-alerts-early-adopter}

Die kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), die die optional lizenzierbaren WAF-Regeln (Web Application Firewall) enthalten, ermöglichen es Ihnen zu konfigurieren, welcher Traffic erlaubt oder verweigert werden soll.

Treten Sie dem Programm für frühe Benutzer bei, damit Sie benachrichtigt werden können, sobald Ihre Traffic-Filterregeln ausgelöst werden. Aktionszentrum-E-Mail-Benachrichtigungen informieren Sie darüber, wann bestimmte Traffic-Bedingungen eintreten, damit Sie geeignete Maßnahmen treffen können.

#### Geschäftsbenutzer können Umleitungen außerhalb von Git (Early Adopter Program) deklarieren. {#apache-rewritemaps-early-adopter}

Ähnlich wie bei AEM 6.5 erfassen Apache/Dispatcher Rewrite-Zuordnungen, die an einem bestimmten Speicherort im Veröffentlichungs-Repository platziert werden, und laden sie, ohne dass eine Pipeline auf der Web-Ebene ausgeführt werden muss. Dies eröffnet Geschäftsbenutzern die Möglichkeit, Umleitungen entweder mithilfe einer Tabelle oder einer Benutzeroberfläche zu deklarieren, z. B. durch den ACS Commons Redirect Map Manager oder, der im Rahmen einer Kundenanwendung erstellt wurde. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) für das Laden dynamischer Inhalte (Early-Adopter-Programm) {#esi-early-adopter}

Das von Adobe verwaltete CDN unterstützt jetzt [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), eine Markup-Sprache für die Zusammenstellung dynamischer Webinhalte auf Edge-Ebene. Durch die Einbeziehung von ESI-Snippets können Sie die gesamte HTML-Seite im CDN mit höheren TTLs zwischenspeichern und gleichzeitig diejenigen kleineren-Abschnitte, die höhere Cadence-Updates erfordern (niedrigere TTLs), öfter aus der Quelle abrufen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

#### Datendienst für die Echtzeit-Benutzerüberwachung (RUM) (Early Adopter Program)

* **[Sie können den Datendienst Real User Monitoring (RUM) nutzen](/help/implementing/cloud-manager/content-requests.md#real-user-monitoring-for-aem-as-a-cloud-service)**, um die Client-seitige Sammlung für AEM as a Cloud Service zu aktivieren.
Der Datendienst Real User Monitoring (RUM) bietet eine präzisere Darstellung der Benutzerinteraktionen und stellt so eine zuverlässige Messung der Website-Interaktionen sicher. Dies ist eine großartige Gelegenheit, erweiterte Einblicke in Ihre Seitenleistung zu erhalten. Dies ist nützlich für Kundinnen und Kunden, die entweder ein von Adobe verwaltetes CDN oder ein nicht von Adobe verwaltetes CDN verwenden. Für diejenigen, die ein nicht von Adobe verwaltetes CDN verwenden, kann jetzt außerdem die automatisierte Traffic-Berichterstellung aktiviert werden, sodass keine Traffic-Berichte mehr für Adobe freigegeben werden müssen.

  Wenn Sie diese neue Funktion testen und Ihr Feedback teilen möchten, senden Sie bitte über die mit Ihrer Adobe ID verknüpfte E-Mail-Adresse eine E-Mail an `aemcs-rum-adopter@adobe.com`. Geben Sie in der E-Mail den Domain-Namen für jede Umgebung an, für die Sie RUM aktivieren möchten. Das Produkt-Team von Adobe aktiviert dann den Datendienst Real User Monitoring (RUM) für Sie.

## [!DNL Experience Manager]-Handbücher {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager-Handbücher finden Sie [here](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2404-release/whats-new-2024-04-0).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).
