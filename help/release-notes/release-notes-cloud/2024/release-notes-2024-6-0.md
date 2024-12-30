---
title: Versionshinweise für Version 2024.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für Version 2024.6.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
feature: Release Information
role: Admin
exl-id: 4033abf4-7094-4ce4-ba93-c936062667e3
source-git-commit: a9adbb1886dcfedfc3fccb6f56939c46ba1365ee
workflow-type: tm+mt
source-wordcount: '1972'
ht-degree: 100%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2024.6.0 {#release-notes}

Im folgenden Abschnitt werden die Versionshinweise zu den neuen Funktionen der Version 2024.6.0 von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2022 oder 2023 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.6.0) war der 27. Juni 2024. Die nächste Version (2024.7.0) ist für den 25. Juli 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Eine Zusammenfassung der in der Version 2024.6.0 hinzugefügten Funktionen finden Sie im Übersichtsvideo zur Version Juni 2024:

>[!VIDEO](https://video.tv.adobe.com/v/3430779?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

### Neue Funktion in Experience Manager Sites {#new-feature-sites}

**Real Use Monitoring-Datendienst (RUM)** {#real-use-monitoring}

Der [Real Use Monitoring-Datendienst (RUM)](/help/sites-cloud/administering/real-use-monitoring-for-aem-as-a-cloud-service.md) ist jetzt allgemein verfügbar und ermöglicht die Client-seitige Datenerfassung für AEM as a Cloud Service. Dieser Dienst gibt Benutzerinteraktionen genauer wieder und stellt so eine zuverlässige Messung der Website-Interaktionen sicher. Er liefert Kundinnen und Kunden erweiterte Einblicke in den Traffic und die Performance ihrer Seite. Damit bietet er eine wertvolle Möglichkeit, die Seiten-Performance zu verstehen und zu optimieren.

### Early-Adopter-Programm {#sites-early-adopter}

**Generieren von Varianten**

Nutzen Sie GenAI über die neue Funktion [Varianten generieren](/help/generative-ai/generate-variations.md) von AEM, die jetzt in Cloud Service verfügbar ist. „Varianten generieren“ hilft Ihnen bei der Erstellung und Skalierung von Inhalten durch den Einsatz generativer KI. Wenden Sie sich an Ihr Adobe-Accountteam, um sich für das Programm zu erkundigen.

**Durchsuchen von Assets in der Inhaltsfragmentkonsole**

Inhaltsautorinnen und -autoren können jetzt Bilder und andere Assets durchsuchen, anzeigen und bearbeiten, ohne die Inhaltsfragmentkonsole verlassen zu müssen.

![Durchsuchen von Assets](/help/sites-cloud/administering/content-fragments/assets/cf-console-assets-browse.png)

Möchten Sie die Funktion ausprobieren und Feedback geben? Sie können von Ihrer offiziellen E-Mail-ID eine E-Mail an aemcs-headless-adopter@adobe.com senden, um am Early-Adopter-Programm teilzunehmen.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Neue Funktionen in Experience Manager Assets {#new-features-assets}



**Content Hub**

Content Hub ist als Teil von Experience Manager Assets as a Cloud Service für die Demokratisierung des Zugriffs auf Markeninhalte für Unternehmen und ihre Geschäftspartner verfügbar. Mit Content Hub können Sie Assets einfach finden und verteilen, Markenvarianten wiederverwenden sowie neue erstellen und die Aktivierung skaliert beschleunigen.

![Content Hub-Benutzeroberfläche](/help/release-notes/assets/content-hub-ui.png)

**Dynamic Media mit OpenAPI-Funktionen**

Dynamic Media mit OpenAPI-Funktionen erweitert das DAM über Adobe- und Drittanbieteranwendungen hinweg und ermöglicht den Zugriff auf markenbestätigte digitale Assets in jedem Kanal über den Asset-Wähler oder OpenAPI-Stapel. Wichtigste Grundsätze: keine Binärkopien, Assets werden für schnelle Performance optimiert und umgewandelt, Assets werden öffentlich bzw. sicher bereitgestellt.

![Neues Dynamic Media-Datenflussdiagramm](/help/assets/assets/dm-openapi-dfd.png)


### Neue Funktionen in der Assets-Ansicht {#assets-view-new-features}

**Weitere Optionen sind im Assets Insights-Dashboard verfügbar**

Die Asset-Anzahl nach Asset-Typ und -Größe ist jetzt im Assets Insights-Dashboard verfügbar. Diese Optionen liefern Echtzeitdaten in Ihrer Assets-Ansichtsumgebung. Sie geben die Anzahlen und Prozentsätze der Assets nach Größenbereich und Asset-Typ an.

**Aktualisierungen des eingebetteten Adobe Express-Editors**

* Optimiertes Benutzererlebnis beim Speichern als neues Asset im Vergleich zum Speichern als neue Version.

* Exportieren mehrseitiger Express-Dokumente (bisher wurden nur einzelne Seiten unterstützt) sowohl in mehrseitige PDF-Dateien als auch in Bildformate. Bei der Auswahl von Bildformaten wird jede Seite als separates Asset im DAM für die nachgelagerte Verteilung gespeichert.

* Unterstützung für das Hinzufügen von Metadaten im Dialogfeld „Speichern“ beim Speichern eines Assets.

<!--


**Content Credentials**

Content Credentials feature in Assets view now provides detailed asset provenance data adhered to an asset. This helps to trace the enroute edits along the asset's lifecycle to prevent users from deception through deliberately tempered assets. This ensures content authenticity among users and fosters trust through transparency.

When looking at the asset details, any image with content credentials added, such as those created with GenAI, displays the manifest details in a dedicated panel. If the asset is downloaded, published, or shared, the credentials remain intact with the asset.

![check publish status1](/help/release-notes/assets/content-credentials.png)

-->

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

<!-- 

* **Configure a shard for Adobe Sign for AEM Forms**: Adobe distributes Acrobat Sign API around the globe in many deployment units called "shards." Each shard serves a customer's account, such as NA1, NA2, NA3, EU1, JP1, AU1, IN1, and others. The shard names correspond to geographic locations. You can now use more than one shard while using Adobe Sign integration with AEM Forms. 

-->

### Neue Funktionen in AEM Forms {#forms-new-prerelease-features}

#### Verbesserter visueller Regeleditor für auf Kernkomponenten basierende adaptive Formulare

Diese Version umfasst ein bedeutendes Upgrade des visuellen Regeleditors für adaptive Formulare, die auf Kernkomponenten basieren. Sie haben nun die folgenden Möglichkeiten:

* Erstellen Sie Regeln im visuellen Regeleditor, um die [Standard-Nachrichten zur erfolgreichen/fehlerhaften Formularübermittlung zu überschreiben](/help/forms/create-and-use-custom-functions.md#use-case-override-form-submission-success-and-error-handlers).

* Im Regeleditor für adaptive Formulare wurde die Möglichkeit hinzugefügt, [verschiedene Feldtypen für den WHEN-Vorgang auszuwählen](/help/forms/rule-editor-core-components.md#allowed-multiple-fields-in-when).

* Autorinnen und Autoren von Formularen können jetzt benutzerdefinierte Funktionen anwenden, um [Daten vor der Übermittlung vorab zu verarbeiten](/help/forms/create-and-use-custom-functions.md#use-case-submit-altered-data-to-the-server).

* Verwenden Sie die Funktion [**Als Entwurf speichern**](/help/forms/save-core-component-based-form-as-draft.md) zum Speichern teilweise ausgefüllter Formulare für eine spätere Übermittlung. Diese Funktion ist in Szenarien nützlich, in denen Benutzende das Ausfüllen eines Formulars unterbrechen und später fortsetzen müssen.

### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen eine einmalige Möglichkeit, vor allen anderen einen exklusiven Zugang zu bahnbrechenden Neuerungen zu erhalten und ihre weitere Entwicklung mitzugestalten. Das Programm bietet Zugriff auf verschiedene Innovationen.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### Verbesserte Bot-Schutzmethoden

In AEM Forms wurden die Sicherheitsfunktionen verbessert, indem jetzt zwei gängige CAPTCHA-Lösungen unterstützt werden: Cloudflare Turnstile und hCaptcha. Diese Funktion ergänzt das vorhandene Google reCAPTCHA und bietet Benutzenden zusätzliche Optionen. Sie erhöht die Flexibilität beim Schutz von Formularen vor Bots und Spam-Übermittlungen.

* **Cloudflare Turnstile**: Dieses reibungslose CAPTCHA überprüft Benutzende anhand einer einfachen Aufgabe, die keine explizite Interaktion erfordert. Es lässt sich nahtlos in Ihre Formulare integrieren und verbessert so das Benutzererlebnis.
* **hCaptcha**: Dieses datenschutzorientierte CAPTCHA bietet eine benutzerfreundliche Alternative mit dem Schwerpunkt auf Datenschutz. Ziel ist es, ein Gleichgewicht zwischen Sicherheit und Benutzererlebnis herzustellen.
* **Google reCAPTCHA**: AEM Forms unterstützt weiterhin sowohl reCAPTCHA v2 als auch reCAPTCHA Enterprise und bietet damit eine zuverlässige und bewährte Lösung.

Durch die Bereitstellung mehrerer CAPTCHA-Optionen haben Sie in AEM Forms die Möglichkeit, die Lösung auszuwählen, die Ihren spezifischen Anforderungen am besten entspricht.

Sind Sie bereit, eine dieser CAPTCHA-Lösungen in Ihre adaptiven Formulare zu integrieren? In der Dokumentation von Adobe finden Sie detaillierte Anweisungen zu jedem Thema: [Cloudflare Turnstile](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-turnstile-core-components), [hCaptcha](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/integrate-adaptive-forms-hcaptcha-core-components) und [Google reCAPTCHA](https://experienceleague.adobe.com/de/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/captcha-adaptive-forms-core-components).


### Forms-Dienst

Der Forms-Dienst generiert interaktive PDF-Formulare für die Datenerfassung. Er kann auch verwendet werden, um Daten in ein vorhandenes interaktives PDF-Formular zu importieren oder daraus zu exportieren und um gesendete Daten zu validieren. Im Folgenden finden Sie eine Aufschlüsselung der Funktionen:

* **Rendern von Formularen**: Generieren Sie ein interaktives PDF-Formular aus einer Vorlage, die mit AEM Forms Designer und (optional) mit XML-Daten erstellt wurde. Mit dieser Funktion wird ein ausfüllbares PDF-Formular erzeugt, das optional mit Daten vorausgefüllt ist.
* **Datenextraktion und -import**: Importieren Sie Daten in ein vorhandenes PDF-Formular und extrahieren Sie Daten aus einem ausgefüllten PDF-Formular. Es wird sowohl das XDP- als auch das XML-Datenformat unterstützt, und der Import in PDF-Formulare, die nicht im XFA-Format sind (auch AcroForms genannt), unterstützt zusätzlich FDF- und XFDF-Daten.
* **Datenvalidierung**: Validieren Sie die gesendeten Daten im XDP- oder XML-Format anhand einer mit AEM Forms Designer erstellten Vorlage.

>[!IMPORTANT]
>
> Wenn Sie Interesse haben, am Early-Access-Programm von Adobe für Early-Access-Innovationen teilzunehmen, senden Sie einfach eine E-Mail von Ihrer offiziellen Adresse an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) und bitten Sie um Zugriff. Sie können Zugriff auf alle oder auf spezifische Innovationen anfordern.


## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Aktionszentrum – Benachrichtigungen zum Inhaltsstatus – Early-Adopter-Programm {#actions-center-notifications}

Das [Aktionszentrum](/help/operations/actions-center.md) sendet E-Mail-Benachrichtigungen, wenn wichtige Vorfälle auftreten oder wenn etwas in Ihrem Code oder in Ihrer Konfiguration festgestellt wird, das proaktive Maßnahmen erfordert. Adobe hat jetzt mehrere neue Arten von Benachrichtigungen im Zusammenhang mit dem Status Ihrer Inhalte eingeführt. Diese Funktion ist über ein Early-Adopter-Programm verfügbar. Wenden Sie sich an die Adobe-Kundenunterstützung, wenn Sie teilnehmen möchten.

#### Seiten enthalten eine große Anzahl von Knoten {#page-nodes}

Eine große Anzahl von Knoten kann die Performance beim Rendern beeinträchtigen und die Seitenladezeiten verkürzen. Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn eine große Anzahl von Knoten auf einer Seite festgestellt wird. So können Sie die erforderlichen Schritte unternehmen, um die Gesamtzahl der Knoten auf einer Seite zu reduzieren.

#### Große Anzahl an ausgeführten Workflow-Instanzen {#running-workflows}

Die Performance der Workflow-Engine wird beeinträchtigt, wenn in der Autorenumgebung eine große Anzahl von ausgeführten Workflows vorliegt. Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn eine große Anzahl an ausgeführten Workflow-Instanzen erkannt wird. So können Sie einen Bereinigungsauftrag konfigurieren, um unnötige laufende Workflows zu beenden.

#### Benutzende, die direkt zu benutzerdefinierten Gruppen hinzugefügt wurden {#users-customgroups}

Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn Benutzende direkt benutzerdefinierten Gruppen hinzugefügt werden. So können Sie die Best Practices von IMS befolgen, indem Sie Benutzende zu relevanten IMS-Gruppen hinzufügen und diese IMS-Gruppen dann als Mitglieder in AEM-Gruppen aufnehmen.

#### Fehlende JCR-Inhalte {#jcr-content}

Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn festgestellt wird, dass JCR-Inhalte fehlen. So können Sie die fehlenden Inhalte hinzufügen und damit den Ausfall bestimmter AEM Assets-Funktionen verhindern.

#### Abgeschlossene Workflows die nicht bereinigt wurden {#workflows}

Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn abgeschlossene Workflows, die älter als 90 Tage sind, nicht bereinigt wurden. Dieser Ansatz optimiert die Leistung Ihrer Workflow-Engine, da die Anzahl der Workflow-Instanzen reduziert wird.

#### Fehlende Sling-Ressource {#sling-resource}

Sie erhalten über das Aktionszentrum eine proaktive Benachrichtigung, wenn festgestellt wird, dass eine Sling-Ressource fehlt. So können Sie die fehlende Ressource hinzufügen und damit den Ausfall bestimmter AEM Assets-Funktionen verhindern.

### Early-Adopter-Programme im Zusammenhang mit der Inhaltsbereitstellung {#foundation-early-adopter}

Senden Sie eine E-Mail an **<aemcs-cdn-config-adopter@adobe.com>**, die angibt, für welche der unten aufgeführten Programme Sie sich interessieren.

#### Standardauthentifizierung beim CDN (Early-Adopter-Programm) {#basicauth-cdn}

Schützen Sie bestimmte Inhaltsressourcen mithilfe eines einfachen Authentifizierungsdialogfelds als Popup, das einen Benutzernamen und ein Passwort erforderlich macht. Diese Funktion ist in erster Linie für leichte Authentifizierungsfälle wie die Überprüfung von Inhalten durch geschäftliche Stakeholder und nicht als umfassende Lösung für Zugriffsrechte von Endbenutzenden gedacht. Die Liste der Benutzernamen und Passwörter wird über eine Konfigurationsdatei in Git verwaltet, die über die Konfigurations-Pipeline bereitgestellt wird – mit Verweis auf die geheimen Cloud Manager-Umgebungsvariablen. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md#basic-auth).

#### Bereinigen von Inhalten im CDN mit einem API-Schlüssel per Self-Service (Early-Adopter-Programm) {#purge-cdn}

Registrieren Sie per Self-Service einen CDN-Bereinigungs-API-Schlüssel und verwenden Sie ihn zum Invalidieren von Inhalten im CDN, entweder global oder für eine oder mehrere Ressourcen. [Weitere Informationen](/help/implementing/dispatcher/cdn-cache-purge.md).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Erstellung von X-AEM-Edge-Key per Self-Service für kundenseitig verwaltetes CDN (BYOCDN) (Early-Adopter-Programm) {#byocdn-keys}

Zuvor war ein Support-Ticket erforderlich, um den X-AEM-Edge-Key zu generieren, der für die Konfiguration eines kundenseitig verwalteten CDN erforderlich war. Dies kann jetzt durch eine Konfigurationsdatei selbst durchgeführt werden, die mithilfe der Konfigurations-Pipeline bereitgestellt wird. Dadurch werden Verzögerungen beim Onboarding in eine neue Umgebung beseitigt. [Weitere Informationen](/help/implementing/dispatcher/cdn-credentials-authentication.md#CDN-HTTP-value).

<!-- Email **<aemcs-cdn-config-adopter@adobe.com>** with a request to be an early adopter. -->

#### Client-seitige Weiterleitungen (Early-Adopter-Programm) {#client-side-redirects-early-adopter}

Konfigurieren Sie Client-seitige Weiterleitungen vom Typ 301/302 in der Verwaltung des Quell-Codes und stellen Sie sie im CDN bereit. [Weitere Informationen](/help/implementing/dispatcher/cdn-configuring-traffic.md#client-side-redirectors).<!-- and join the early adopter program by emailing **<aemcs-cdn-config-adopter@adobe.com>**. --> Beachten Sie, dass im Zusammenhang mit der [CDN-Konfiguration](/help/implementing/dispatcher/cdn-configuring-traffic.md) mehrere weitere Funktionen bereits verfügbar sind, einschließlich Anfrage- und Antworttransformationen und Routing des Traffics zu Nicht-AEM-Sites.

#### Warnhinweise zu Traffic-Filterregeln (Early-Adopter-Programm) {#traffic-filter-rules-alerts-early-adopter}

Die kürzlich veröffentlichten [Traffic-Filterregeln](/help/security/traffic-filter-rules-including-waf.md), die die optional lizenzierbaren WAF-Regeln (Web Application Firewall) enthalten, ermöglichen es Ihnen zu konfigurieren, welcher Traffic erlaubt oder verweigert werden soll.

Nehmen Sie am Early-Adopter-Programm teil, damit Sie benachrichtigt werden, sobald Ihre Traffic-Filterregeln ausgelöst werden. E-Mail-Benachrichtigungen durch das Aktionszentrum informieren Sie darüber, wenn bestimmte Traffic-Bedingungen eintreten, damit Sie geeignete Maßnahmen treffen können.

#### Business-Anwenderinnen und -Anwender können Umleitungen außerhalb von Git deklarieren (Early-Adopter-Programm) {#apache-rewritemaps-early-adopter}

Ähnlich wie bei AEM 6.5 erfassen Apache/Dispatcher Rewrite-Zuordnungen, die an einem bestimmten Speicherort im Veröffentlichungs-Repository abgelegt werden, und laden sie, ohne dass eine Pipeline auf Web-Ebene ausgeführt werden muss. So können geschäftliche Anwenderinnen und Anwender Umleitungen mithilfe einer Tabelle oder einer Benutzeroberfläche deklarieren, z. B. mit ACS Commons Redirect Map Manager oder einer benutzerdefinierten Anwendung. <!-- Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information. -->

#### Edge Side Includes (ESI) für das Laden dynamischer Inhalte (Early-Adopter-Programm) {#esi-early-adopter}

Das von Adobe verwaltete CDN unterstützt jetzt [Edge Side Includes (ESI)](/help/implementing/dispatcher/edge-side-includes.md), eine Markup-Sprache für die dynamische Zusammenführung von Web-Inhalten auf Edge-Ebene. Durch die Einbeziehung von ESI-Snippets können Sie die gesamte HTML-Seite im CDN mit höheren TTLs zwischenspeichern und gleichzeitig diejenigen kleineren Abschnitte, die höhere Intervall-Updates (niedrigere TTLs) erfordern, öfter aus der Quelle abrufen. <!--Please reach out to **<aemcs-cdn-config-adopter@adobe.com>** for more information.-->

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2406-release/whats-new-2024-06-0).

## Cloud Manager {#cloud-manager}

Eine vollständige Liste der Cloud Manager-Veröffentlichungen nach Monaten finden Sie [hier](/help/implementing/cloud-manager/release-notes/current.md).

## Migrations-Tools {#migration-tools}

Eine vollständige Liste der Versionen von Migrations-Tools finden Sie [hier](/help/journey-migration/release-notes/release-notes-migration-tools-current.md).

## Universeller Editor {#universal-editor}

Eine vollständige Liste der Versionen des universellen Editors finden Sie [hier](/help/release-notes/universal-editor/current.md).

## Generieren von Varianten {#generate-variations}

Eine vollständige Liste der Versionen für das Generieren von Varianten finden Sie [hier](/help/generative-ai/release-notes-generate-variations.md).

## Versionshinweise zu Experience Cloud {#experience-cloud}

Informationen zu Versionen anderer Experience Cloud-Anwendungen finden Sie [hier](https://experienceleague.adobe.com/de/docs/release-notes/experience-cloud/current).
