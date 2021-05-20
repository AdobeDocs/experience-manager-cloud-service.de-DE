---
title: Datenschutzbestimmungen - Adobe Experience Manager as a Cloud Service Sites - Einhaltung von Datenschutzbestimmungen
description: Erfahren Sie mehr über die Unterstützung von Adobe Experience Manager as a Cloud Service Sites für die verschiedenen Datenschutzbestimmungen. darunter die EU-Datenschutz-Grundverordnung (DSGVO), das kalifornische Verbraucherdatenschutzgesetz und die Einhaltung der Vorschriften bei der Implementierung eines neuen AEM als Cloud Service.
exl-id: fdcad111-0cdd-46cc-964c-3f8669ca2030
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '1036'
ht-degree: 43%

---

# Adobe Experience Manager as a Cloud Service Sites - Einhaltung von Datenschutzbestimmungen {#aem-sites-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>Der Inhalt dieses Dokuments stellt keine Rechtsberatung dar und ist nicht als Ersatz für Rechtsberatung gedacht.
>
>Wenden Sie sich an die Rechtsabteilung Ihres Unternehmens, um Ratschläge zu Datenschutzbestimmungen zu erhalten.

>[!NOTE]
>
>Weitere Informationen über die Reaktion der Adobe auf Datenschutzprobleme und was dies für Sie als Adobe bedeutet, finden Sie im [Datenschutzzentrum der Adobe](https://www.adobe.com/privacy.html).

Adobe Experience Manager as a Cloud Service Sites ist bereit, Kunden bei der Erfüllung ihrer Datenschutzverpflichtungen und der Einhaltung von Datenschutzbestimmungen zu unterstützen. Diese Seite führt Kunden durch die Verfahren zur Verarbeitung solcher Anfragen in AEM Sites. Sie beschreibt den Speicherort der privaten Daten und wie diese manuell oder per Code entfernt werden können.

Weitere Informationen finden Sie im [Adobe Privacy Center](https://www.adobe.com/privacy.html).

>[!NOTE]
>
>Weitere Informationen finden Sie unter [Adobe Experience Manager as a Cloud Service Readiness for Data Protection and Data Privacy Regulations](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md) .

## AEM-Autorenebene {#aem-author-tier}

Benutzerkonten und UGC-Inhalte auf dem Autorenserver werden in der [AEM Foundation-Dokumentation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md) behandelt.

## AEM-Veröffentlichungsebene {#aem-publish-tier}

Benutzerkonten, die zur Authentifizierung von Besuchern auf der Site verwendet werden, und benutzergenerierte Inhalte auf dem Veröffentlichungsserver werden in der [AEM Foundation-Dokumentation](/help/onboarding/data-privacy-and-protection-readiness/aem-readiness.md) behandelt.

Standardmäßig speichern AEM Sites-Komponenten keine Formulardaten, die von Besuchern auf dem Veröffentlichungsserver eingegeben wurden. Es wird empfohlen, diese Daten zur weiteren Verarbeitung an ein Drittanbietersystem oder an Adobe Campaign zu übermitteln.

## Opt-in/Opt-out {#opt-in-opt-out}

<!--
AEM has a [cookie opt-out service](/help/sites-developing/cookie-optout.md ) that can be used for managing the opt-in/opt-out for users.
-->

Adobe Experience Manager unterliegt einem Cookie-Opt-out-Dienst, der zur Verwaltung des Opt-in-/Opt-outs für Benutzer verwendet wird.

Opt-out:

1. Navigieren Sie zu:
   [Adobe Privacy Center - Opt-out](https://www.adobe.com/privacy/opt-out.html)

1. Scrollen Sie nach unten zu **Services** - **Experience Cloud Service-Nutzungsdaten**.

1. Wählen Sie den referenzierten Link aus. Aktuell mit dem Titel **hier**.

1. Ihnen werden die folgenden Details sowie die Optionen zum Opt-out oder An angezeigt:

   * Um die Aggregation und Analyse von Daten zu Ihrem Besuch auf dieser Website abzuwählen, müssen Sie ein Cookie in Ihrem Browser installieren. Dieses Cookie identifiziert, dass Sie sich abgemeldet haben.

      Wenn Sie das Opt-out-Cookie löschen oder Computer oder Webbrowser wechseln, müssen Sie sich erneut abmelden.

      Opt-out - Schließen Sie mich aus der Aggregation und Analyse der Besuchersitzung aus (installieren Sie das Opt-out-Cookie `amcglobal.sc.omtrdc.net`) - Klicken Sie hier.

      Opt-in - Schließen Sie mich in die Aggregation und Analyse der Besuchersitzung ein (installieren Sie nicht das Opt-out-Cookie `amcglobal.sc.omtrdc.net`) - Klicken Sie hier.
   Führen Sie die oben genannten Schritte aus, um auf die tatsächlichen Links zuzugreifen.

   >[!NOTE]
   >
   > Eine weitere Beschreibung finden Sie in **2. Datenschutz.** Abschnitt der allgemeinen Nutzungsbedingungen der  [Adobe](https://www.adobe.com/de/legal/terms.html).

## Analytics Foundation {#analytics-foundation}

AEM Sites bietet eine optionale Integration in Analytics Foundation, die Funktionen des On-Demand-Dienstes von Adobe Analytics verwendet.

Weitere Informationen zum Verwalten von Anfragen von Datensubjekten im Zusammenhang mit Adobe Analytics finden Sie unter [Adobe Analytics und Datenschutz](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-view-settings.html).

## Personalization Foundation by Target {#personalization-foundation-by-target}

AEM Sites bietet eine optionale Integration in Personalization Foundation by Target, die Funktionen innerhalb des On-Demand-Dienstes von Adobe Target verwendet.

Weitere Informationen zur Verwaltung von Anfragen von Datensubjekten im Zusammenhang mit Adobe Target finden Sie unter [Adobe Target - Privatsphäre und Datenschutz-Grundverordnung](https://docs.adobe.com/content/help/en/target/using/implement-target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation.html).

## ContextHub {#contexthub}

<!--
AEM provides an optional data layer with [ContextHub](/help/sites-developing/contexthub.md).
-->

AEM bietet eine optionale Datenschicht mit ContextHub. Dadurch verbleiben besucherspezifische Daten im Browser, die dort für eine regelbasierte Personalisierung verwendet werden.

Standardmäßig werden diese Besucherdaten nicht in AEM gespeichert. AEM übermittelt Regeln an die Datenebene, sodass personalisierungsbezogene Entscheidungen direkt im Browser getroffen werden.

### Implementieren von Opt-in-/Opt-out-Komponenten {#implementing-opt-in-opt-out}

Der Website-Inhaber muss eine Opt-out-Komponente gemäß den folgenden Richtlinien implementieren.

Diese Richtlinien sehen eine standardmäßige Opt-in-Implementierung vor. Daher muss ein Besucher einer Website eindeutig zustimmen, bevor personenbezogene Daten in der (clientseitigen) Persistenz des Browsers gespeichert werden.

* Die Opt-out-Komponente sollte immer dann integriert werden, wenn die ContextHub-Komponente vorhanden ist.
* Die Geschäftsbedingungen, die sich auf den Datenschutz und die Privatsphäre der Website beziehen, müssen dem Besucher der Website angezeigt werden, damit er:

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

      * `ContextHub.Utils.Persistence.Modes.LOCAL` (Standard)
      * `ContextHub.Utils.Persistence.Modes.SESSION`
      * `ContextHub.Utils.Persistence.Modes.COOKIE`
      * `ContextHub.Utils.Persistence.Modes.WINDOW`

      Der ContextHub-Speicher definiert, welche Persistenzschicht verwendet wird. Um den aktuellen Status der Persistenz anzuzeigen, sollten daher alle Schichten überprüft werden.


So können beispielsweise in localStorage gespeicherte Daten angezeigt werden:

```
var storage = new ContextHub.Utils.Persistence({ mode: ContextHub.Utils.Persistence.Modes.LOCAL });
console.log(storage.getTree());
```

### Löschen der ContextHub-Persistenz  {#clearing-persistence-of-contexthub}

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

   * `ContextHub.Utils.Persistence.Modes.LOCAL` (Standard)
   * `ContextHub.Utils.Persistence.Modes.SESSION`
   * `ContextHub.Utils.Persistence.Modes.COOKIE`
   * `ContextHub.Utils.Persistence.Modes.WINDOW`
