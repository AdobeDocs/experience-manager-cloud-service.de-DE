---
title: Konfigurieren von Übermittlungsaktionen für AEM Forms mit Edge Delivery Services
description: Erfahren Sie, wie Sie mithilfe von Edge Delivery Services Übermittlungsaktionen in AEM Forms konfigurieren. Wählen Sie zwischen Forms Submission Service und AEM Publish Submit Action , um Formulardaten sicher und effizient zu verarbeiten.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: bca160763fdd1e96f1350ac74eb76ff7c26ac00b
workflow-type: tm+mt
source-wordcount: '2166'
ht-degree: 1%

---


# Konfigurieren von Formularübermittlungen: Wohin gehen Ihre Daten?

Nachdem ein Benutzer in **Formular auf** Senden“ geklickt hat, müssen Sie Edge Delivery Services mitteilen, was mit diesen Daten geschehen soll. Es gibt zwei Hauptoptionen:

## Methode 1: Verwenden des AEM Forms-Übermittlungsdienstes (vereinfacht)

Dieser Service eignet sich ideal für gängige, unkomplizierte Aktionen wie das Senden von Daten an eine Tabelle oder eine E-Mail.

**Was ist es und wie kann es Ihnen helfen?**

Der [Forms-Übermittlungsdienst](/help/forms/forms-submission-service.md) ist ein von Adobe gehosteter Endpunkt. Wenn Ihr Formular Daten an dieses sendet, übernimmt dieser Service und führt eine vorkonfigurierte Aktion durch. Es ist so konzipiert, dass es einfach einzurichten ist. Sie können Folgendes konfigurieren: Senden an Tabellen oder E-Mails:

* **An Arbeitsblatt übermitteln:** Fügen Sie die übermittelten Formulardaten automatisch als neue Zeile in einem Google-Arbeitsblatt oder einer Microsoft Excel-Datei (gespeichert auf OneDrive oder SharePoint) hinzu.
* **E-Mail senden** Senden Sie eine E-Mail mit den Formulardaten an eine oder mehrere von Ihnen angegebene E-Mail-Adressen.

#### WICHTIG: Setup-Anforderungen

* **Zugriff auf Kalkulationstabellen:** Um Daten an ein Google-Blatt oder eine Excel-Datei auf OneDrive/SharePoint zu senden, benötigt das Adobe-Service-Konto (häufig `forms@adobe.com`) in der Regel **Bearbeitungsberechtigung** für diese spezifische Kalkulationstabelle.
* **Early-Access-Programm** Einige Funktionen dieses Services, insbesondere für Tabellen, können Teil eines Early-Access-Programms sein. Möglicherweise müssen Sie den Zugriff anfordern, indem Sie eine E-Mail an `aem-forms-ea@adobe.com` senden oder ein bestimmtes Adobe-Formular mit Ihren Projektdetails ausfüllen. Lesen Sie immer die neueste Adobe-Dokumentation.

**Flussdiagramm des Forms Submission Service**
<!--
```mermaid
    graph TD
    UserForm[User Submits Form on Your EDS Site] >|Data Sent| FormSubmissionService[AEM Forms Submission Service]
    FormSubmissionService -- "If configured for Google Sheets" > GoogleSheet[Data written to Google Sheet]
    FormSubmissionService -- "If configured for Excel (OneDrive or SharePoint)" > ExcelSheet[Data written to Excel]
    FormSubmissionService -- "If configured for Email" > Email[Email with data is sent]

    style UserForm fill:#ccf,stroke:#333
    style FormSubmissionService fill:#fca,stroke:#333
    style GoogleSheet fill:#90ee90,stroke:#333
    style ExcelSheet fill:#90ee90,stroke:#333
    style Email fill:#add8e6,stroke:#333
```-->
![Forms-Übermittlung](/help/forms/assets/eds-fss.png)

Dieses Diagramm zeigt, wie der Forms Submission Service gesendete Daten an eine konfigurierte Tabelle oder E-Mail sendet.

## Methode 2: Senden an Ihre AEM-Veröffentlichungsinstanz (erweitert)

Bei komplexeren Anforderungen können [Formulare (insbesondere die mit dem universellen Editor erstellten) Daten direkt an Ihre AEM as a Cloud Service-Veröffentlichungsinstanz senden](/help/forms/configure-submit-actions-core-components.md). Dadurch wird die volle Backend-Power von AEM freigeschaltet.

**Wann müssen Sie an AEM Publish übermitteln?**

* So erstellen Sie einen Trigger für benutzerdefinierte AEM-Workflows nach der Übermittlung.
* So verwenden Sie das AEM-Formulardatenmodell (FDM) zur Integration mit Datenbanken oder anderen Unternehmenssystemen.
* So stellen Sie eine Verbindung zu Services von Drittanbietern wie Marketo, Microsoft Power Automate oder Adobe Workfront Fusion her.
* Um Daten an bestimmten Orten wie Azure Blob Storage oder SharePoint-Listen/-Dokumentbibliotheken zu speichern (nicht nur einfache Tabellen).
* Bei einer komplexen Server-seitigen Validierungs- oder Datenverarbeitungslogik in AEM.

**Verfügbare Übermittlungsaktionen (AEM-Veröffentlichungsübermittlungen)**

* [An einen REST-Endpunkt übermitteln](/help/forms/configure-submit-action-restpoint.md)
* [E-Mail senden (mithilfe der E-Mail-Services von AEM)](/help/forms/configure-submit-action-send-email.md)
* [Senden mit Formulardatenmodell (FDM)](/help/forms/configure-data-sources.md)
* [Aufrufen eines AEM-Workflows](/help/forms/aem-forms-workflow-step-reference.md)
* [An SharePoint senden (als Listenelemente oder Dokumente)](/help/forms/configure-submit-action-sharepoint.md)
* [An OneDrive senden (als Dokumente)](/help/forms/configure-submit-action-onedrive.md)
* [An Azure Blob Storage senden](/help/forms/configure-submit-action-azure-blob-storage.md)
* [An Microsoft Power Automate senden](/help/forms/forms-microsoft-power-automate-integration.md)
* [An Adobe Workfront Fusion senden](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [An Adobe Marketo Engage senden](/help/forms/submit-adaptive-form-to-marketo-engage.md)

>[!NOTE]
>
> Selbst wenn ein Google Sheet/Excel von AEM Publish aus als Ziel ausgewählt wird, umfasst dies andere Konfigurationsschritte als der direkte Forms-Übermittlungs-Service.

**Flussdiagramm für die Übermittlung von AEM-Veröffentlichungen**

<!--```mermaid
    graph TD
    UEForm[User Submits Universal Editor Form on EDS Site] >|Data sent to AEM Publish URL - example: /adobe/forms/af/submit/...| AEMPublish[AEM Publish Instance]
    AEMPublish -- Configured to run AEM Workflow > AEMWorkflow[AEM Workflow is Triggered]
    AEMPublish -- Configured to use Form Data Model > FDM[FDM updates Backend System or Database]
    AEMPublish -- Configured for Marketo > Marketo[Data sent to Marketo Engage]
    AEMPublish -- Other configured actions... > OtherIntegrations[...]

    style UEForm fill:#ccf,stroke:#333
    style AEMPublish fill:#fca,stroke:#333
    style AEMWorkflow fill:#add8e6,stroke:#333
    style FDM fill:#add8e6,stroke:#333
    style Marketo fill:#add8e6,stroke:#333
```-->

![Flussdiagramm für die Übermittlung von AEM-Veröffentlichungen](/help/forms/assets/eds-aem-publish.png)
Dieses Flussdiagramm zeigt ein Formular, das an AEM Publish übermittelt wird, welche dann komplexe Backend-Aufgaben verarbeitet.

### Forms Submission Service und AEM Publish Submissions

| Funktion | Forms Submission Service | AEM-Veröffentlichungseinreichungen |
| :- | :- | :-- |
| **Am besten geeignet für:** | Einfache Datenerfassung in Tabellen, E-Mail-Benachrichtigungen | Komplexe Workflows, Unternehmensintegrationen, benutzerdefinierte Logik |
| **Formular-Authoring** | Gut für dokumentbasierte; OK für einfache EU-Formulare | Optimiert für vom universellen Editor erstellte Formulare |
| **Setup-Aufwand** | Niedrig (oft einfache Konfiguration) | Höher (erfordert AEM Publish, Dispatcher, OSGi, CDN-Setup) |
| **Backend-** | Von Adobe gehosteter Service | Ihre AEM as a Cloud Service-Veröffentlichungsinstanz |
| **Flexibilität** | Auf Blatt/E-Mail beschränkt | Sehr flexible, vollständige Palette von AEM Forms-Aktionen |
| **Beispiel** | Kontaktformulardaten zu einem Google-Blatt | Kreditantrag, der einen AEM-Validierungs-Workflow auslöst |

## Einbetten von Forms in verschiedene Sites oder Seiten

Manchmal möchten Sie ein Formular, das an einem Ort erstellt und verwaltet wird (z. B. eine zentrale „Forms-Site„), auf einer anderen Web-Seite oder Site anzeigen.

### Warum sollten Sie ein Formular einbetten?

* Sie haben ein standardmäßiges „Kontakt“-Formular mit universellem Editor erstellt, das auf mehreren Landingpages mit dokumentbasiertem Authoring angezeigt werden muss.
* Ihre wichtigsten Inhalte auf der Website befinden sich im Bereich der Dokumenterstellung (Document Authoring, DA) und Sie müssen ein spezielles Formular einschließen.
* Sie möchten ein einzelnes, gut verwaltetes Formular für mehrere verschiedene EDS-Projekte wiederverwenden.

### Funktionsweise der Formulareinbettung in technischer Hinsicht

Die Seite, auf der das Formular angezeigt werden soll (nennen wir sie „Host-Seite„), enthält Code (normalerweise einen speziellen Block oder ein spezielles Skript). Wenn ein Benutzer die Host-Seite besucht, führt dieser Code eine Anfrage an die URL durch, unter der das eigentliche Formular gehostet wird (nennen wir es „Formular-Source„). Der Formular-Source sendet dann seine HTML zurück, die von der Host-Seite eingefügt und angezeigt wird.

**Eingebettete Formulararchitektur**

<!--```mermaid
   graph LR
    User[User] >|Visits| HostPage[Host Page - for example: your-site.com/landing-page]
    HostPage >|Contains code to embed form| FetchForm{Host Page Requests Form HTML}
    FetchForm >|HTTP GET request to the form URL| FormSource[Form Source - for example: forms-repo.hlx.page/my-form]
    FormSource >|Returns form HTML| FetchForm
    FetchForm >|Injects form HTML into page| HostPage
    HostPage >|Displays full page with embedded form| User

    subgraph Submission ["Form Submission from Host Page"]
        HostPage_Form[Embedded form on the host page] >|User submits| TargetEndpoint[Submission endpoint - FSS or AEM Publish]
    end

    style HostPage fill:#e6f3ff,stroke:#333
    style FormSource fill:#ffe6e6,stroke:#333
    style FetchForm fill:#fff2cc,stroke:#333
    style Submission fill:#f0fff0,stroke:#333
```-->
![Eingebettete Formulararchitektur](/help/forms/assets/eds-embedded-form.png)
Dieses Diagramm zeigt, wie die Host-Seite Formular-HTML aus dem Formular-Source abruft und anzeigt. Für die Übermittlung wird der konfigurierte Endpunkt des ursprünglichen Formulars verwendet.

## Einrichten von CORS für Embedded Forms

[CORS (Cross-Origin Resource Sharing](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) ist eine Browser-Sicherheitsfunktion. Wenn Ihre Host-Seite (z. B. `site-a.com`) versucht, ein Formular von einer anderen Domain abzurufen (z. B. `forms-site-b.com`), blockiert der Browser es, es sei denn, `forms-site-b.com` lässt es explizit über CORS-Kopfzeilen zu.

Ohne richtige CORS-Kopfzeilen auf dem **Formular-Source-Server** verhindert der Browser, dass die Host-Seite das Formular lädt, und das eingebettete Formular wird nicht angezeigt.

### Wie wird CORS auf der Site konfiguriert, auf der Ihr Formular bereitgestellt wird?

Sie müssen den Server konfigurieren, auf dem der **Formular-Source** gehostet wird, um bestimmte HTTP-Kopfzeilen in der Antwort zu senden. Die genaue Methode hängt von Ihrer EDS-Einrichtung ab (z. B. erfolgt dies bei Franklin-Projekten oft in einer `helix-config.yaml` oder einer ähnlichen Konfigurationsdatei in Ihrem GitHub-Repository, die das CDN-Verhalten oder die Edge-Worker-Logik steuert).
Schlüsselkopfzeilen, die den Formularantworten von Source hinzugefügt werden sollen:

* `Access-Control-Allow-Origin: <URL_of_Host_Page>` (z. B. `https://your-site.com`). Zum Testen können Sie `*` verwenden, aber geben Sie für die Produktion die exakten Domains an.
* `Access-Control-Allow-Methods: GET, OPTIONS` (Sie benötigen möglicherweise `POST`, wenn die Formularübermittlung selbst auch ursprungsübergreifend ist, aber die Übermittlungen normalerweise an einen separaten, häufig gleichen Ursprung oder spezifisch konfigurierten Endpunkt gehen).
* `Access-Control-Allow-Headers: Content-Type` (und alle anderen benutzerdefinierten Kopfzeilen, die beim Abrufen des Formulars verwendet werden könnten).

**Beispiel (konzeptionell für eine Konfigurationsdatei):**

```yaml
        # In the configuration for the site HOSTING THE FORM (Form Source)
        headers:
          # Apply to paths where your forms are served, e.g., /forms/**
          - path: /forms/**
            custom:
              Access-Control-Allow-Origin: https://host-page-domain.com
              Access-Control-Allow-Methods: GET, OPTIONS
```

## Weitere Überlegungen: CDNs und mehrere Code-Basen (Helix 4)

* **CDN-Regeln:** Ihr CDN bietet möglicherweise Möglichkeiten zum Durchführen von Proxy-Vorgängen für Anfragen. Beispielsweise könnte eine Anfrage an `host-page.com/embedded-form` intern vom CDN weitergeleitet werden, um Inhalte aus `form-source.com/actual-form` abzurufen, sodass sie dem Browser als dieselbe Herkunft erscheinen. Die Einrichtung kann kompliziert sein.
* **Mehrere Code-Basen (Helix 4):** Wenn sich Ihre Host-Seite und der Formular-Source in verschiedenen GitHub-Repositorys befinden (häufig in Helix 4-Setups), stellen Sie sicher, dass alle JavaScript-„Formularblöcke“, die zum Rendern oder Verwalten des Formulars benötigt werden, in der Code-Basis der Host-Seite verfügbar sind oder dass das Formular-HTML, das aus dem Formular-Source abgerufen wurde, mit allen erforderlichen JavaScript-Dateien eigenständig ist. In den Originaldokumenten wird angegeben, dass Sie für „helix4 mit verschiedenen Code-Basen den Formularblock zu beiden Code-Basen hinzufügen müssen“.

### Allgemeine Einrichtung und Konfiguration der Architektur

Im Folgenden finden Sie einige gängige Möglichkeiten, wie Sie Ihre Formulare einrichten können, indem Sie Authoring-Methoden mit Übermittlungsstrategien und wichtige Konfigurationspunkte kombinieren.

#### Dokumentenbasiertes Formular mit Tabellenkalkulation/E-Mail-Übermittlung

Dies ist die einfachste Einrichtung. Sie erstellen Ihr Formular in Word/Google Docs und es sendet Daten an eine Tabelle oder E-Mail über den Forms Submission Service.

1. Definieren Sie Ihr Formular in einem Word/Google-Dokument/Blatt mithilfe der angegebenen Tabellenstruktur oder des Formularblocks.
1. Geben Sie im Dokument (oder in der entsprechenden Konfiguration) die Ziel-Kalkulationstabellen-URL oder E-Mail-Adresse für den Forms Submission Service an.
1. Stellen Sie sicher, dass `forms@adobe.com` (oder das entsprechende Service-Konto) Bearbeitungszugriff auf Ihre Zieltabelle hat.
1. Veröffentlichen Sie das Dokument auf Ihrer Edge Delivery-Site.

**Dokumentbasierte + Forms Submissions Service-Architektur**
<!--
```mermaid
    graph TD
        User[<img src='https://img.icons8.com/ios-filled/50/000000/user.png' width='30' /> User] >|Fills Out| EDS_Page_DocBased[EDS Page with Document-Based Form]
        EDS_Page_DocBased >|Submits Data| FSS[AEM Forms Submission Service]
        FSS > Target[<img src='https://img.icons8.com/color/48/000000/google-sheets.png' width='30' /> Data to Spreadsheet / <img src='https://img.icons8.com/color/48/000000/filled-sent.png' width='30' /> Email Notification]

        Authoring[Form defined in Google Doc/Sheet] >|EDS Syncs & Renders| EDS_Page_DocBased

        style EDS_Page_DocBased fill:#ccf,stroke:#333
        style FSS fill:#fca,stroke:#333
        style Target fill:#90ee90,stroke:#333
        style Authoring fill:#e6ffe6,stroke:#333
```-->

![Dokumentbasierte + Forms Submissions Service-Architektur](/help/forms/assets/eds-doc-fss.png)

#### Universeller Editor für Formulare mit Tabellenkalkulation/E-Mail-Übermittlung

Sie verwenden den universellen Editor von Visual , um Ihr Formular zu erstellen, aber weiterhin den einfachen Forms-Übermittlungsdienst für die Datenerfassung.

1. Erstellen Sie Ihr Formular mit dem universellen Editor in AEM.
1. Konfigurieren Sie die Übermittlungsaktion des Formulars in der Benutzeroberfläche so, dass die Option „An Forms Submit Service übermitteln“ verwendet wird.
1. Geben Sie die URL oder E-Mail-Adresse der Zieltabelle an.
1. Wenn Sie Tabellen verwenden, stellen Sie sicher, dass `forms@adobe.com` Bearbeitungszugriff hat.
1. Veröffentlichen Sie die Seite mit dem Formular aus AEM auf Ihrer Edge Delivery-Site.

   **Architektur des universellen Editors und des Forms-Übermittlungsdienstes**

   ![Architektur des universellen Editors und des Forms-Übermittlungsdienstes](/help/forms/assets/eds-ue-fss.png)

   <!--```mermaid
    graph TD
    User[User] >|Fills Out| EDS_Page_UE[EDS Page with Universal Editor Form]
    EDS_Page_UE >|Submits Data| FSS[AEM Forms Submission Service]
    FSS > Target[Data sent to Google Sheet and Email Notification]
    AuthoringUE[Form built in Universal Editor - AEM] >|AEM Publishes to EDS| EDS_Page_UE
    style EDS_Page_UE fill:#ccf,stroke:#333
    style FSS fill:#fca,stroke:#333
    style Target fill:#90ee90,stroke:#333
    style AuthoringUE fill:#e6f3ff,stroke:#333
    ```
    -->

#### Universelles Editor-Formular mit AEM-Veröffentlichungsübermittlung (Erweitert)

Diese Einrichtung verwendet den universellen Editor für die Formularerstellung und Ihre AEM-Veröffentlichungsinstanz für eine leistungsstarke Backend-Verarbeitung (Workflows, FDM usw.). Dies erfordert mehr Konfiguration.

1. **Formular in UE erstellen** Erstellen Sie Ihr Formular im universellen Editor. Konfigurieren Sie die Übermittlungsaktion so, dass sie auf eine AEM Forms-Aktion verweist (z. B. &quot;AEM-Workflow aufrufen“ oder „Senden mit Formulardatenmodell„).
1. **AEM Dispatcher-Konfiguration (auf der AEM-Veröffentlichungsebene):**
   * **Keine Umleitungen:** Stellen Sie sicher, dass Ihre Dispatcher *Regeln keine* Umleitungsanfragen an `/adobe/forms/af/submit/...` Pfade senden.
   * **Übermittlungen zulassen** Ändern Sie Ihre Dispatcher-Filter (z. B. in `filters.any`), um POST-Anfragen an `allow` explizit von der Domain oder den IP-Adressen Ihrer Edge Delivery-Site aus zu `/adobe/forms/af/submit/...`.
1. **OSGi-Referrer-Filter in AEM (auf der AEM-Veröffentlichungsebene):**
   * Suchen und konfigurieren Sie in der AEM OSGi-Konsole (`/system/console/configMgr`) den „Apache Sling Referrer Filter“.
   * Fügen Sie die Domain(n) Ihrer Edge Delivery-Site (z. B. `https://your-eds-domain.hlx.page`, `https://your-custom-eds-domain.com`) zur Liste „Hosts zulassen“ oder „Hosts RegExp zulassen“ hinzu. Dadurch wird AEM angewiesen, Einreichungen von Ihrer EDS-Site zu akzeptieren.
1. **CDN-Umleitungsregel (in Ihrem Edge Delivery-CDN):**
   * Ihre Edge Delivery-Site (z. B. `your-eds-domain.hlx.page`) muss Übermittlungsanfragen korrekt an Ihre AEM-Veröffentlichungsinstanz weiterleiten.
   * Wenn das Formular auf Ihrer EDS-Seite gesendet wird, wird möglicherweise ein relativer Pfad wie `/adobe/forms/af/submit/...` ausgewählt. Sie benötigen eine Regel in Ihrem Edge Delivery-CDN (oder Edge-Worker), die besagt: „Wenn eine Anfrage an `your-eds-domain.hlx.page/adobe/forms/af/submit/...` kommt, leiten Sie sie an `your-aem-publish-instance.com/adobe/forms/af/submit/...` weiter (Proxy oder Umleitung).“
   * Die genaue Implementierung hängt von Ihrem CDN-Anbieter ab (z. B. Fastly VCL, Akamai Property Manager, Cloudflare Workers).
1. **(Optional) `constants.js` für Entwicklung (in der Code-Basis Ihres EDS-Projekts):**
   * Für die lokale Entwicklung oder wenn Ihre Client-seitigen Formularskripte die vollständige AEM-Veröffentlichungs-URL kennen müssen, können Sie dies in einer `constants.js` oder ähnlichen Konfigurationsdatei im GitHub-Repository Ihres Edge Delivery-Projekts konfigurieren. Zum Beispiel:

   ```javascript
       // in your-eds-project/scripts/constants.js
       export const AEM_PUBLISH_URL = 'https://publish-p123-e456.adobeaemcloud.com';
            // Your form submission script might then construct the submit URL:
           // const submitUrl = `${AEM_PUBLISH_URL}/adobe/forms/af/submit/...`;
   ```

1. **Veröffentlichen** Veröffentlichen Sie Ihre Formularseite aus AEM in EDS und stellen Sie sicher, dass alle AEM-Konfigurationen in Ihrer AEM-Veröffentlichungsinstanz aktiv sind.

   **Universeller Editor + AEM-Veröffentlichungsarchitektur**

![Universeller Editor + AEM-Veröffentlichungsarchitektur](/help/forms/assets/eds-aem-publish.png)

Hier wird der Ablauf angezeigt: Der Benutzer sendet auf der EDS-Site, CDN leitet ihn zu AEM Dispatcher weiter und wird dann von der AEM-Veröffentlichungsinstanz verarbeitet.

#### Einbetten eines Formulars in eine Dokumenterstellungsseite (Document Authoring, DA)

Ihr Hauptinhalt der Website wird in der Dokumenterstellung (Document Authoring, DA) erstellt. Sie erstellen Ihr Formular entweder mit dokumentbasierter Bearbeitung oder dem separaten universellen Editor und betten es dann in Ihre DAM-Seite ein.

1. **Formular erstellen und veröffentlichen:**
   * Verwenden Sie das dokumentbasierte Authoring ODER den universellen Editor, um Ihr Formular zu erstellen.
   * Konfigurieren Sie die Übermittlungsmethode (entweder an den Forms-Übermittlungs-Service oder die AEM-Veröffentlichung gemäß Setup 1, 2 oder 3).
   * Veröffentlichen Sie dieses Formular, damit es über eine eigene Edge Delivery-URL live ist (z. B. `.../forms/my-special-form`).
1. **Konfigurieren Sie CORS:** Stellen Sie sicher, dass auf der Edge Delivery-Site bzw. im Projekt, das bzw. das dieses eigenständige Formular hostet, CORS-Header eingerichtet sind, damit die Domain Ihrer Site für die Dokumenterstellung sie abrufen kann .
1. **Seite in DA erstellen** Erstellen oder Bearbeiten der Seite beim Erstellen von Dokumenten.
1. **Formularblock einbetten:** Verwenden Sie den entsprechenden Block in DA, um eine externe URL einzubetten. Lassen Sie diesen Block auf die URL des eigenständigen veröffentlichten Formulars verweisen.
1. **DA-Seite veröffentlichen:** Veröffentlichen Sie Ihre DA-Seite. Daraufhin wird das Formular abgerufen und angezeigt.

   **Forms in DA-Architektur eingebettet**

   ![Forms in DA-Architektur eingebettet](/help/forms/assets/eds-forms-embedd-da.png)

   Hier wird eine DAM-Seite angezeigt, die ein Formular von einem anderen EDS-Speicherort abruft. Das eingebettete Formular verarbeitet seine eigene Übermittlung.

## Fehlerbehebung

* **Meine Formularübermittlung funktioniert nicht.**
   * **Konsolenfehler überprüfen:** Öffnen Sie die Entwicklerkonsole Ihres Browsers (normalerweise F12) und suchen Sie beim Senden auf der Registerkarte „Netzwerk“ oder „Konsole“ nach Fehlern.
   * **Übermittlungs-URL überprüfen:** Versucht das Formular, eine Übermittlung an den richtigen Endpunkt (Forms Submission Service URL oder Ihr AEM-Veröffentlichungspfad) vorzunehmen?
   * **Forms-Übermittlungsdienst:** Wenn an eine Tabelle gesendet wird, `forms@adobe.com` Bearbeitungszugriff erhalten? Ist die Kalkulationstabellen-URL korrekt?
   * **AEM-Veröffentlichungseinreichungen:**
      * Erlaubt Ihr Dispatcher die `/adobe/forms/af/submit/...` von POSTs?
      * Ist der Sling Referrer-Filter in der AEM-Veröffentlichungsinstanz so konfiguriert, dass er Ihre EDS-Domain zulässt?
      * Funktionieren Ihre CDN-Umleitungsregeln für `/adobe/forms/af/submit/...` ordnungsgemäß?

* **Mein eingebettetes Formular wird nicht angezeigt.**

   * **CORS!** Dies ist der häufigste Grund. Überprüfen Sie die Browser-Konsole auf CORS-Fehler. Stellen Sie sicher *dass das* die richtigen `Access-Control-Allow-Origin` Kopfzeilen enthält.
   * **Formular-URL korrekt?** verweist der Einbettungs-Code auf der Host-Seite auf die richtige Live-URL des Formulars?
   * **JavaScript-Blöcke:** Ist der Code dieses Blocks auf der Host-Seite verfügbar, wenn das Formular zum Rendern auf einen bestimmten JavaScript-„Formularblock“ angewiesen ist?

* **Bei der Übermittlung an AEM Publish erhalte ich die Fehlermeldung „403 Forbidden“ oder „401 Unauthorized“**

   * Dies verweist häufig auf den Sling Referrer-Filter in AEM Publish, der keine Anfragen von Ihrer EDS-Domain zulässt. Überprüfen Sie die Konfiguration.
   * Es kann auch zu einem Authentifizierungs-/Autorisierungsproblem kommen, wenn Ihr AEM-Übermittlungsendpunkt dies erfordert, obwohl Standardformularübermittlungen in der Regel anonym sind.

## Nächste Schritte

Dieses Handbuch bietet einen Überblick über die Verwendung von Formularen mit AEM Edge Delivery Services. Detailliertere schrittweise Anleitungen zu bestimmten Konfigurationen finden Sie in der offiziellen Adobe Experience Manager-Dokumentation:

* [Dokumentenbasiertes Authoring mit Edge Delivery Services Forms](/help/edge/docs/forms/tutorial.md)
* [Universeller Editor mit Edge Delivery Services Forms](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Dokumenterstellung (Document Authoring, DA) und Einbetten von Inhalten](https://www.aem.live/developer/da-tutorial)
* [AEM Forms Submission Service](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)