---
title: Datenschutz- und Datenschutzvorschriften - Adobe Experience Manager als Cloud Service-Sites - Bereitschaft
description: 'Erfahren Sie mehr über Adobe Experience Manager als Unterstützung für Cloud-Service-Sites für die verschiedenen Datenschutzbestimmungen und Datenschutzbestimmungen. einschließlich der EU-Datenschutzverordnung (GDPR), des kalifornischen Datenschutzgesetzes für Verbraucher und wie bei der Implementierung eines neuen AEM als Cloud-Service-Projekt einzuhalten ist. '
translation-type: tm+mt
source-git-commit: 1130e8a07bc3826380483a7560ebda7e8a17e238

---


# Adobe Experience Manager als Cloud-Service-Sites - Eignung für Datenschutz und Datenschutzbestimmungen {#aem-sites-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Bitte konsultieren Sie die Rechtsabteilung Ihres Unternehmens, um sich über die Datenschutzbestimmungen zu informieren.

>[!NOTE]
>
>Weitere Informationen über die Reaktion von Adobe auf Datenschutzprobleme und was dies für Sie als Adobe-Kunde bedeutet, finden Sie im Datenschutzzentrum von [Adobe](https://www.adobe.com/privacy.html).

Adobe Experience Manager als Cloud-Service-Sites ist bereit, Kunden bei ihren Datenschutzverpflichtungen und der Einhaltung von Datenschutzbestimmungen zu unterstützen. Diese Seite führt Kunden durch die Verfahren zur Bearbeitung solcher Anfragen in AEM-Sites. Sie beschreibt den Speicherort der privaten Daten und wie diese manuell oder per Code entfernt werden können.

Weitere Informationen finden Sie im [Adobe Privacy Center](https://www.adobe.com/privacy.html).

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Adobe Experience Manager als Cloud Service Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md) .

## AEM-Autorenebene {#aem-author-tier}

User accounts and UGC content on the author server are covered in the [AEM Foundation documentation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md).

## Veröffentlichungsstufe in AEM {#aem-publish-tier}

User accounts used to authenticate visitors on the site, and UGC content on the publish server are covered in the [AEM Foundation documentation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md).

Standardmäßig speichern AEM-Sites-Komponenten keine Formulardaten, die von Besuchern auf dem Veröffentlichungsserver eingegeben wurden. Es wird empfohlen, diese Daten zur weiteren Verarbeitung an ein Drittanbietersystem oder an Adobe Campaign zu übermitteln.

## Opt-in/Opt-out {#opt-in-opt-out}

<!--
AEM has a [cookie opt-out service](/help/sites-developing/cookie-optout.md ) that can be used for managing the opt-in/opt-out for users.
-->

Adobe Experience Manager unterliegt einem Ausschluss-Service für Cookies, der für die Verwaltung der Ausschluss-/Abmeldeoption für Benutzer verwendet wird.

So wählen Sie aus:

1. Navigieren Sie zu:
   [Adobe Privacy Center - Ausschluss](https://www.adobe.com/privacy/opt-out.html)

1. Blättern Sie nach unten zu **Dienste** - **Experience Cloud-Nutzungsdaten**.

1. Wählen Sie den referenzierten Link aus. derzeit **hier** benannt.

1. Sie erhalten die folgenden Details sowie die Optionen zum Ausschluss oder zur Teilnahme:

   * Um die Aggregation und Analyse von Daten über Ihren Besuch auf dieser Site abzuwählen, müssen Sie ein Cookie in Ihrem Browser installieren. Dieses Cookie identifiziert, dass Sie sich abgemeldet haben.

      Wenn Sie das Ausschluss-Cookie löschen oder Computer oder Webbrowser wechseln, müssen Sie die Abmeldung erneut vornehmen.

      Ausschluss - Ausschluss von der Aggregation und Analyse der Besuchersitzung ( `amcglobal.sc.omtrdc.net` Ausschluss-Cookie installieren) - Klicken Sie hier.

      Teilnahme - Schließen Sie mich in die Aggregation und Analyse der Besuchersitzung ein (installieren Sie nicht das `amcglobal.sc.omtrdc.net` Ausschluss-Cookie) - Klicken Sie hier.
   Gehen Sie wie oben beschrieben vor, um auf die eigentlichen Links zuzugreifen.

   >[!NOTE]
   >
   > Eine weitere Beschreibung finden Sie im Abschnitt **Datenschutzrichtlinien** der [Nutzungsbedingungen](https://marketing.adobe.com/resources/help/en_US/terms.html).

## Analytics Foundation {#analytics-foundation}

AEM-Sites enthalten eine optionale Integration mit Analytics Foundation, die Funktionen des Adobe Analytics On-Demand-Dienstes verwendet.

For further information on managing data subject requests related to Adobe Analytics see [Adobe Analytics and Data Privacy](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-view-settings.html).

## Personalisierungsstiftung nach Target {#personalization-foundation-by-target}

AEM-Sites enthalten eine optionale Integration mit Personalization Foundation von Target, die Funktionen des Adobe Target-On-Demand-Dienstes verwendet.

For further information on managing data subject requests related to Adobe Target see [Adobe Target - Privacy and General Data Protection Regulation](https://marketing.adobe.com/resources/help/en_US/target/target/privacy-and-general-data-protection-regulation.html).

## ContextHub {#contexthub}

<!--
AEM provides an optional data layer with [ContextHub](/help/sites-developing/contexthub.md).
-->

AEM bietet eine optionale Datenschicht mit ContextHub. Dadurch verbleiben besucherspezifische Daten im Browser, die dort für eine regelbasierte Personalisierung verwendet werden.

Standardmäßig werden diese Besucherdaten nicht in AEM gespeichert. AEM übermittelt Regeln an die Datenebene, sodass personalisierungsbezogene Entscheidungen direkt im Browser getroffen werden.

### Implementieren von Opt-in-/Opt-out-Komponenten {#implementing-opt-in-opt-out}

Der Website-Inhaber muss eine Opt-out-Komponente gemäß den folgenden Richtlinien implementieren.

Diese Richtlinien sehen eine standardmäßige Opt-in-Implementierung vor. Daher muss ein Besucher der Website eindeutig zustimmen, bevor personenbezogene Daten in der (clientseitigen) Persistenz des Browsers gespeichert werden.

* Die Opt-out-Komponente sollte immer dann integriert werden, wenn die ContextHub-Komponente vorhanden ist.
* Die Geschäftsbedingungen, die sich auf den Datenschutz und die Privatsphäre der Website beziehen, müssen dem Website-Besucher angezeigt werden, damit er:

   * Akzeptieren der Bedingungen
   * Ablehnen der Bedingungen
   * Ändern der vorherigen Auswahl

* Wenn ein Besucher der Website die zugehörigen Nutzungsbedingungen akzeptiert, sollte das ContextHub-Opt-out-Cookie entfernt werden:

   ```
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   ```

* Wenn ein Besucher der Website die zugehörigen Nutzungsbedingungen nicht akzeptiert, sollte das ContextHub-Opt-out-Cookie gesetzt werden:

   ```
   ContextHub.Utils.Cookie.setItem('cq-opt-out', 1);
   ```

* Um zu überprüfen, ob ContextHub im Opt-out-Modus ausgeführt wird, sollte folgender Aufruf in der Browserkonsole erfolgen:

   ```
   var isOptedOut = ContextHub.isOptedOut(true) === true;
   // if isOptedOut is true, ContextHub is running in opt-out mode
   ```

### Vorschau der ContextHub-Persistenz {#previewing-persistence-of-contexthub}

Zum Anzeigen der von ContextHub verwendeten Persistenz bestehen folgende Möglichkeiten:

* Verwenden der Browserkonsole, z. B.:

   * Chrome:

      * Öffnen Sie „Entwicklertools“ > „Anwendung“ > „Speicher“:

         * „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
         * „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
         * „Cookies“ > „(Website)“ > „SessionPersistence“
   * Firefox:

      * Öffnen Sie „Entwicklertools“ > „Speicher“:

         * „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
         * „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
         * „Cookies“ > „(Website)“ > „SessionPersistence“
   * Safari:

      * Öffnen Sie „Voreinstellungen“ > „Erweitert“ > „Menü ‚Entwickeln‘ in der Menüleiste anzeigen“.
      * Öffnen Sie „Entwickeln“ > „JavaScript-Konsole anzeigen“:

         * „Konsole“ > „Speicher“ > „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
         * „Konsole“ > „Speicher“ > „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
         * „Konsole“ > „Speicher“ > „Cookies“ > „(Website)“ > „ContextHubPersistence“
   * Internet Explorer:

      * Öffnen Sie „Entwicklertools“ > „Konsole“:

         * `localStorage.getItem('ContextHubPersistence')`
         * `sessionStorage.getItem('ContextHubPersistence')`
         * `document.cookie`




* Verwenden der ContextHub-API in der Browserkonsole:

   * ContextHub bietet folgende Datenpersistenzschichten:

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (default)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`
      Der ContextHub-Speicher definiert, welche Persistenzschicht verwendet wird. Um den aktuellen Status der Persistenz anzuzeigen, sollten daher alle Schichten überprüft werden.


So können beispielsweise in localStorage gespeicherte Daten angezeigt werden:

Zum Anzeigen der von ContextHub verwendeten Persistenz bestehen folgende Möglichkeiten:

* Verwenden der Browserkonsole:

   * Öffnen Sie in Chrome „Entwicklertools“ > „Anwendung“ > „Speicher“:

      * „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
      * „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
      * „Cookies“ > „(Website)“ > „SessionPersistence“
   * Öffnen Sie in Firefox „Entwicklertools“ > „Speicher“:

      * „Lokaler Speicher“ > „(Website)“ > „ContextHubPersistence“
      * „Sitzungsspeicher“ > „(Website)“ > „ContextHubPersistence“
      * „Cookies“ > „(Website)“ > „SessionPersistence“


* Verwenden der ContextHub-API in der Browserkonsole:

   * ContextHub bietet folgende Datenpersistenzschichten:

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (default)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`
      Der ContextHub-Speicher definiert, welche Persistenzschicht verwendet wird. Um den aktuellen Status der Persistenz anzuzeigen, sollten daher alle Schichten überprüft werden.


So können beispielsweise in localStorage gespeicherte Daten angezeigt werden:

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### Löschen der ContextHub-Persistenz {#clearing-persistence-of-contexthub}

So löschen Sie die ContextHub-Persistenz:

* So löschen Sie die Persistenz von aktuell geladenen Speichern:

   ```
   // in order to be able to fully access persistence layer, Opt-Out must be turned off
   ContextHub.Utils.Cookie.removeItem('cq-opt-out');
   
   // following call asks all currently loaded stores to clear their data
   ContextHub.cleanAllStores();
   
   // following call asks all currently loaded stores to set back default values (provided in their configs)
   ContextHub.resetAllStores();
   ```

* So löschen Sie eine bestimmte Persistenzschicht, z. B. „sessionStorage“:

   ```
   var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.SESSION });
   storage.setItem('/store', null);
   storage.setItem('/_', null);
   
   // to confirm that nothing is stored:
   console.log(storage.getTree());
   ```

* Um alle ContextHub-Persistenzschichten zu löschen, muss der entsprechende Code für alle Ebenen aufgerufen werden:

   * `ContextHub.Utils.Persistence.Modes.LOCAL` (default)
   * `ContextHub.Utils.Persistence.Modes.SESSION`
   * `ContextHub.Utils.Persistence.Modes.COOKIE`
   * `ContextHub.Utils.Persistence.Modes.WINDOW`
