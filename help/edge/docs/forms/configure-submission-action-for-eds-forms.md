---
title: Konfigurieren von Übermittlungsaktionen für AEM Forms mit Edge Delivery Services
description: Erfahren Sie, wie Sie mithilfe von Edge Delivery Services Übermittlungsaktionen in AEM Forms konfigurieren können. Wählen Sie zwischen dem Formularübermittlungsdienst und der Übermittlungsaktion in AEM Publish, um Formulardaten sicher und effizient zu verarbeiten.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 8f490054-f7b6-40e6-baa3-3de59d0ad290
source-git-commit: 75d8ea4f0913e690e3374d62c6e7dcc44ea74205
workflow-type: ht
source-wordcount: '2166'
ht-degree: 100%

---

# Konfigurieren von Formularübermittlungen: Übermittlung und Zielort ihrer Daten

Wenn eine Person in Ihrem Formular auf **Senden** geklickt hat, müssen Sie Edge Delivery Services mitteilen, was mit diesen Daten geschehen soll. Es gibt zwei Möglichkeiten:

## Methode 1: Verwenden des AEM-Formularübermittlungsdiensts (Vereinfacht)

Dieser Dienst ist ideal für häufige, unkomplizierte Aktionen wie das Senden von Daten an eine Tabelle oder eine E-Mail.

**Was ist dieser Dienst und wie kann er Ihnen helfen?**

Der [Formularübermittlungsdienst](/help/forms/forms-submission-service.md) ist ein von Adobe gehosteter Endpunkt. Wenn Ihr Formular Daten an ihn sendet, übernimmt dieser Dienst die Verantwortung und führt eine vorkonfigurierte Aktion durch. Er ist für eine einfache Einrichtung konzipiert. Sie können Folgendes konfigurieren: Senden an Tabellen oder E-Mails:

* **Senden an Tabelle:** Fügen Sie die gesendeten Formulardaten einer Google-Tabelle oder einer (auf OneDrive oder SharePoint gespeicherten) Microsoft Excel-Datei automatisch als neue Zeile hinzu.
* **Senden einer E-Mail:** Senden Sie eine E-Mail mit den Formulardaten an eine oder mehrere von Ihnen angegebene E-Mail-Adressen.

#### Wichtig: Setup-Anforderungen

* **Zugriff auf Tabellen:** Um Daten an eine Google-Tabelle oder eine Excel-Datei auf OneDrive/SharePoint zu senden, benötigt das Adobe-Dienstkonto (häufig `forms@adobe.com`) in der Regel eine **Bearbeitungsberechtigung** für diese spezifische Tabelle.
* **Early-Access-Programm** Einige Funktionen dieses Dienstes, insbesondere für Tabellen, können Teil eines Early-Access-Programms sein. Möglicherweise müssen Sie den Zugriff anfordern, indem Sie eine E-Mail an `aem-forms-ea@adobe.com` senden oder ein bestimmtes Adobe-Formular mit Ihren Projektdetails ausfüllen. Überprüfen Sie immer die neueste Adobe-Dokumentation.

**Flussdiagramm des Formularübermittlungsdiensts**
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
![Formularübermittlung](/help/forms/assets/eds-fss.png)

Dieses Flussdiagramm zeigt, wie der Formularübermittlungsdienst gesendete Daten übernimmt und an eine konfigurierte Tabelle oder E-Mail sendet.

## Methode 2: Senden an Ihre AEM-Veröffentlichungsinstanz (Erweitert)

Bei komplexeren Anforderungen können [Formulare (insbesondere wenn sie mit dem universellen Editor erstellt wurden) Daten direkt an Ihre AEM as a Cloud Service-Veröffentlichungsinstanz senden](/help/forms/configure-submit-actions-core-components.md). Dadurch wird die volle Backend-Leistung von AEM freigegeben.

**Daten sollten aus folgenden Gründen an AEM Publish gesendet werden**

* Um nach der Übermittlung benutzerdefinierte AEM-Workflows auszulösen.
* Um das AEM-Formulardatenmodell (FDM) mit Datenbanken oder anderen Unternehmenssystemen zu integrieren.
* Um eine Verbindung zu Diensten von Drittanbietern wie Marketo, Microsoft Power Automate oder Adobe Workfront Fusion herzustellen.
* Um Daten an bestimmten Orten wie Azure Blob Storage oder SharePoint-Listen/-Dokumentbibliotheken zu speichern (nicht nur einfache Tabellen).
* Bei einer komplexen Server-seitigen Validierungs- oder Datenverarbeitungslogik in AEM.

**Verfügbare Übermittlungsaktionen (AEM Publish-Übermittlungen)**

* [An einen REST-Endpunkt übermitteln](/help/forms/configure-submit-action-restpoint.md)
* [E-Mail senden (mithilfe der E-Mail-Dienste von AEM)](/help/forms/configure-submit-action-send-email.md)
* [Senden mit Formulardatenmodell (FDM)](/help/forms/configure-data-sources.md)
* [Aufrufen eines AEM-Workflows](/help/forms/aem-forms-workflow-step-reference.md)
* [An SharePoint senden (als Listenelemente oder Dokumente)](/help/forms/configure-submit-action-sharepoint.md)
* [An OneDrive senden (als Dokumente)](/help/forms/configure-submit-action-onedrive.md)
* [An Azure Blob Storage senden](/help/forms/configure-submit-action-azure-blob-storage.md)
* [An Microsoft Power Automate senden](/help/forms/forms-microsoft-power-automate-integration.md)
* [An Adobe Workfront Fusion Senden](/help/forms/submit-adaptive-form-to-workfront-fusion.md)
* [An Adobe Marketo Engage senden](/help/forms/submit-adaptive-form-to-marketo-engage.md)

>[!NOTE]
>
> Selbst wenn von AEM Publish eine Google-Tabelle/Excel-Datei als Ziel ausgewählt wird, umfasst dies andere Konfigurationsschritte als der direkte Formularübermittlungsdienst.

**Flussdiagramm für AEM Publish-Übermittlung**

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

![Flussdiagramm für AEM Publish-Übermittlung](/help/forms/assets/eds-aem-publish.png)
Dieses Flussdiagramm zeigt ein Formular, das an AEM Publish übermittelt wird, welches dann komplexe Backend-Aufgaben verarbeitet.

### Formularübermittlungsdienst im Vergleich zu AEM Publish-Übermittlungen

| Funktion | Formularübermittlungsdienst | AEM Publish-Übermittlungen |
| :- | :- | :-- |
| **Am besten geeignet für** | Einfache Datenerfassung in Tabellen, E-Mail-Benachrichtigungen | Komplexe Workflows, Unternehmensintegrationen, benutzerdefinierte Logik |
| **Formularerstellung** | Geeignet für dokumentenbasiertes Authoring; geeignet für einfache UE-Formulare | Am besten geeignet für vom universellen Editor erstellte Formulare |
| **Setup-Aufwand** | Niedrig (oft einfache Konfiguration) | Höher (erfordert AEM Publish, Dispatcher, OSGi, CDN-Setup) |
| **Backend-System** | Von Adobe gehosteter Dienst | Ihre AEM as a Cloud Service-Veröffentlichungsinstanz |
| **Flexibilität** | Auf Tabelle/E-Mail beschränkt | Sehr flexibel, vollständiges Spektrum an AEM Forms-Aktionen |
| **Beispiel** | Kontaktformulardaten an eine Google-Tabelle | Darlehensantrag, der einen AEM-Genehmigungs-Workflow auslöst |

## Einbetten von Formularen in verschiedene Sites oder Seiten

Manchmal möchten Sie ein Formular, das an einem Ort erstellt und verwaltet wird (z. B. einer zentralen „Formular-Site“), auf einer anderen Web-Seite oder Site anzeigen.

### Gründe für die Einbettung von Formularen

* Sie haben ein „Kontakt“-Standardformular mit dem universellen Editor erstellt, das auf mehreren Landingpages angezeigt werden muss, die mit dokumentenbasiertem Authoring erstellt wurden.
* Die Hauptinhalte Ihrer Website befinden sich in der Dokumentenerstellung und Sie müssen ein spezialisiertes Formular beifügen.
* Sie möchten ein einzelnes, gut verwaltetes Formular für mehrere verschiedene EDS-Projekte wiederverwenden.

### Technische Funktionsweise der Formulareinbettung

Die Seite, auf der das Formular angezeigt werden soll (nennen wir sie „Host-Seite“), enthält Code (normalerweise einen speziellen Block oder ein spezielles Skript). Wenn Benutzende die Host-Seite besuchen, stellt dieser Code eine Anfrage an die URL, unter der das eigentliche Formular gehostet wird (die sogenannte „Formularquelle“). Die Formularquelle sendet dann ihre HTML zurück, die von der Host-Seite eingefügt und angezeigt wird.

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
Dieses Diagramm zeigt, wie die Host-Seite die Formular-HTML aus der Formularquelle abruft und anzeigt. Für die Übermittlung wird der konfigurierte Endpunkt des ursprünglichen Formulars verwendet.

## Einrichten von CORS für eingebettete Formulare

[CORS (Cross-Origin Resource Sharing)](https://experienceleague.adobe.com/de/docs/experience-manager-learn/foundation/security/understand-cross-origin-resource-sharing) ist eine Browser-Sicherheitsfunktion. Wenn Ihre Host-Seite (z. B. `site-a.com`) versucht, ein Formular von einer anderen Domain abzurufen (z. B. `forms-site-b.com`), wird dies vom Browser blockiert, wenn `forms-site-b.com` es nicht explizit über einen CORS-Header erlaubt.

Ohne korrekte CORS-Header auf dem **Formularquellen-Server** verhindert der Browser, dass die Host-Seite das Formular lädt, und das eingebettete Formular wird nicht angezeigt.

### Konfigurieren von CORS auf der Site, auf der Ihr Formular bereitgestellt wird

Sie müssen den Server, auf dem die **Formularquelle** gehostet wird, so konfigurieren, dass bestimmte HTTP-Header in der Antwort gesendet werden. Die genaue Methode hängt von Ihrem EDS-Setup ab (z. B. erfolgt dies bei Franklin-Projekten oft in `helix-config.yaml` oder einer ähnlichen Konfigurationsdatei in Ihrem GitHub-Repository, die das CDN-Verhalten oder die Edge-Worker-Logik steuert).
Empfohlene Schlüssel-Header, die den Antworten der Formularquelle hinzugefügt werden können:

* `Access-Control-Allow-Origin: <URL_of_Host_Page>` (z. B. `https://your-site.com`). Zum Testen können Sie `*` verwenden, aber für die Produktion sind die genauen Domains erforderlich.
* `Access-Control-Allow-Methods: GET, OPTIONS` (Sie benötigen möglicherweise `POST`, wenn die Formularübermittlung selbst auch ursprungsübergreifend ist, aber die Übermittlungen normalerweise an einen separaten Endpunkt gehen, der häufig gleichen Ursprungs oder spezifisch konfiguriert ist).
* `Access-Control-Allow-Headers: Content-Type` (und alle anderen benutzerdefinierten Header, die beim Abrufen des Formulars verwendet werden könnten).

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

* **CDN-Regeln:** Ihr CDN bietet möglicherweise Proxy-Anfragen an. Beispielsweise könnte eine Anfrage an `host-page.com/embedded-form` intern vom CDN weitergeleitet werden, um Inhalte aus `form-source.com/actual-form` abzurufen, sodass der Browser es für den gleichen Ursprung hält. Das Einrichten kann kompliziert sein.
* **Mehrere Code-Basen (Helix 4):** Wenn sich Ihre Host-Seite und die Formularquelle in verschiedenen GitHub-Repositorys befinden (häufig in Helix 4-Setups), stellen Sie sicher, dass alle JavaScript-„Formularblöcke“, die zum Rendern oder Verwalten des Formulars benötigt werden, in der Code-Basis der Host-Seite verfügbar sind oder dass das Formular-HTML, das aus der Formularquelle abgerufen wurde, mit allen erforderlichen JavaScript-Dateien eigenständig ist. In den Originaldokumenten wird angegeben, dass Sie für helix4 mit verschiedenen Code-Basen den Formularblock in beiden Code-Basen hinzufügen müssen.

### Allgemeines Einrichten der Architektur und Konfigurationsschritte

Im Folgenden finden Sie einige gängige Möglichkeiten, wie Sie Ihre Formulare einrichten können, indem Sie Authoring-Methoden mit Übermittlungsstrategien und wichtigen Konfigurationspunkten kombinieren.

#### Dokumentenbasiertes Formular mit Tabellen-/E-Mail-Übermittlung

Dies ist das einfachste Setup. Sie erstellen Ihr Formular in Word/Google Docs und es sendet über den Formularübermittlungsdienst Daten an eine Tabelle oder E-Mail.

1. Definieren Sie Ihr Formular in Word, einem Google-Dokument oder einer Google-Tabelle mithilfe der angegebenen Tabellenstruktur oder des Formularblocks.
1. Geben Sie im Dokument (oder in der entsprechenden Konfiguration) die Zieltabellen-URL oder die E-Mail-Adresse für den Formularübermittlungsdienst an.
1. Stellen Sie sicher, dass `forms@adobe.com` (oder das entsprechende Dienstkonto) Bearbeitungszugriff auf Ihre Zieltabelle hat.
1. Veröffentlichen Sie das Dokument auf Ihrer Edge Delivery-Site.

**Dokumentenbasierte Architektur und Architektur für den Formularübermittlungsdienst**
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

![Dokumentenbasierte Architektur und Architektur für den Formularübermittlungsdienst](/help/forms/assets/eds-doc-fss.png)

#### Formular im universellen Editor mit Tabellen-/E-Mail-Übermittlung

Sie verwenden den visuellen universellen Editor, um Ihr Formular zu erstellen, verwenden aber weiterhin den einfachen Formularübermittlungsdienst für die Datenerfassung.

1. Erstellen Sie Ihr Formular mit dem universellen Editor in AEM.
1. Konfigurieren Sie die Übermittlungsaktion des Formulars im universellen Editor so, dass die Option „An Formularübermittlungsdienst senden“ verwendet wird.
1. Geben Sie die URL der Zieltabelle oder die E-Mail-Adresse an.
1. Wenn Sie Tabellen verwenden, stellen Sie sicher, dass `forms@adobe.com` Bearbeitungszugriff hat.
1. Veröffentlichen Sie Ihre Seite mit dem Formular aus AEM auf Ihrer Edge Delivery-Site.

   **Architektur des universellen Editors und des Formularübermittlungsdiensts**

   ![Architektur des universellen Editors und des Formularübermittlungsdiensts](/help/forms/assets/eds-ue-fss.png)

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

#### Formular im universellen Editor mit AEM Publish-Übermittlung (Erweitert)

Dieses Setup verwendet den universellen Editor für die Formularerstellung und Ihre AEM-Veröffentlichungsinstanz für eine leistungsstarke Backend-Verarbeitung (Workflows, FDM usw.). Zusätzliche Konfiguration ist erforderlich.

1. **Formular im universellen Editor erstellen:** Erstellen Sie Ihr Formular im universellen Editor. Konfigurieren Sie die Übermittlungsaktion so, dass sie auf eine AEM Forms-Aktion verweist (z. B. „AEM-Workflow aufrufen“ oder „Mit Formulardatenmodell senden“).
1. **AEM Dispatcher-Konfiguration (auf der AEM Publish-Ebene):**
   * **Keine Umleitungen:** Stellen Sie sicher, dass Ihre Dispatcher-Regeln *keine* Umleitungsanfragen an `/adobe/forms/af/submit/...`-Pfade senden.
   * **Zulassen von Übermittlungen:** Ändern Sie Ihre Dispatcher-Filter (z. B. in `filters.any`), um POST-Anfragen an `/adobe/forms/af/submit/...` von der Domain oder IP-Adresse Ihrer Edge Delivery Server-Site explizit mit `allow` zu erlauben.
1. **OSGi-Referrer-Filter in AEM (auf der AEM Publish-Ebene):**
   * Suchen und konfigurieren Sie in der AEM OSGi-Konsole (`/system/console/configMgr`) „Apache Sling Referrer Filter“.
   * Fügen Sie die Domain(s) Ihrer Edge Delivery-Site (z. B. `https://your-eds-domain.hlx.page`, `https://your-custom-eds-domain.com`) zur Liste „Hosts zulassen“ oder „Hosts RegExp zulassen“ hinzu. Dadurch wird AEM angewiesen, Übermittlungen von Ihrer EDS-Site zu akzeptieren.
1. **CDN-Umleitungsregel (in Ihrem Edge Delivery-CDN):**
   * Ihre Edge Delivery-Site (z. B. `your-eds-domain.hlx.page`) muss Übermittlungsanfragen korrekt an Ihre AEM-Veröffentlichungsinstanz weiterleiten.
   * Wenn das Formular auf Ihrer EDS-Seite gesendet wird, wird möglicherweise ein relativer Pfad wie `/adobe/forms/af/submit/...` als Ziel ausgewählt. Sie benötigen eine Regel in Ihrem Edge Delivery-CDN (oder Edge-Worker), die Folgendes festlegt: „Beim Eingang einer Anfrage an `your-eds-domain.hlx.page/adobe/forms/af/submit/...` muss diese an `your-aem-publish-instance.com/adobe/forms/af/submit/...` weitergeleitet werden (Proxy oder Umleitung).“
   * Die genaue Implementierung hängt von Ihrem CDN-Anbieter ab (z. B. Fastly VCL, Akamai Property Manager, Cloudflare Workers).
1. **(Optional) `constants.js` für Entwicklung (in der Code-Basis Ihres EDS-Projekts):**
   * Für die lokale Entwicklung oder wenn Ihre Client-seitigen Formularskripte die vollständige AEM Publish-URL kennen müssen, können Sie dies in `constants.js` oder einer ähnlichen Konfigurationsdatei im GitHub-Repository Ihres Edge Delivery-Projekts konfigurieren. Zum Beispiel:

   ```javascript
       // in your-eds-project/scripts/constants.js
       export const AEM_PUBLISH_URL = 'https://publish-p123-e456.adobeaemcloud.com';
            // Your form submission script might then construct the submit URL:
           // const submitUrl = `${AEM_PUBLISH_URL}/adobe/forms/af/submit/...`;
   ```

1. **Veröffentlichen:** Veröffentlichen Sie Ihre Formularseite aus AEM in EDS und stellen Sie sicher, dass alle AEM-Konfigurationen in Ihrer AEM-Veröffentlichungsinstanz aktiv sind.

   **Architektur für universellen Editor und AEM Publish**

![Architektur für universellen Editor und AEM Publish](/help/forms/assets/eds-aem-publish.png)

Hier wird der Ablauf angezeigt: Person sendet an die EDS-Site, CDN leitet zu AEM Dispatcher weiter und AEM-Publish übernimmt die Verarbeitung.

#### Einbetten eines Formulars in eine Dokumentenerstellungsseite

Der Hauptinhalt Ihrer Website wird in der Dokumentenerstellung erstellt. Sie erstellen Ihr Formular entweder mit dokumentenbasiertem Authoring oder separat mit dem universellen Editor und betten es dann in Ihre DAM-Seite ein.

1. **Erstellen und Veröffentlichen des Formulars:**
   * Verwenden Sie das dokumentenbasierte Authoring ODER den universellen Editor, um Ihr Formular zu erstellen.
   * Konfigurieren Sie die Übermittlungsmethode (entweder an den Formularübermittlungsdienst oder an AEM Publish gemäß Setup 1, 2 oder 3).
   * Veröffentlichen Sie dieses Formular, um es über eine eigene Edge Delivery-URL live bereitzustellen (z. B. `.../forms/my-special-form`).
1. **Konfigurieren von CORS:** Stellen Sie sicher, dass auf der Edge Delivery-Site bzw. im Edge Delivery-Projekt, auf der bzw. in dem dieses eigenständige Formular gehostet wird, CORS-Header eingerichtet sind, damit die Domain der Dokumentenerstellungs-Site es abrufen kann.
1. **Erstellen einer Seite in der Dokumentenerstellung:** Erstellen oder bearbeiten Sie Ihre Seite in der Dokumentenerstellung.
1. **Einbetten eines Formularblocks:** Verwenden Sie den entsprechenden Block in der Dokumentenerstellung, um eine externe URL einzubetten. Dieser Block muss auf die URL des eigenständigen und veröffentlichten Formulars verweisen.
1. **Veröffentlichen einer Dokumentenerstellungsseite:** Veröffentlichen Sie Ihre Dokumentenerstellungsseite. Das Formular wird abgerufen und angezeigt.

   **Formulare, die in der Architektur der Dokumentenerstellung eingebettet sind**

   ![Formulare, die in der Architektur der Dokumentenerstellung eingebettet sind](/help/forms/assets/eds-forms-embedd-da.png)

   Hier wird eine DAM-Seite angezeigt, die ein Formular von einem anderen EDS-Speicherort abruft. Das eingebettete Formular übernimmt die Verarbeitung seiner Übermittlung selbst.

## Fehlerbehebung

* **Meine Formularübermittlung funktioniert nicht.**
   * **Auf Konsolenfehler prüfen:** Öffnen Sie die Entwicklungskonsole Ihres Browsers (normalerweise F12) und suchen Sie beim Senden auf der Registerkarte „Netzwerk“ oder „Konsole“ nach Fehlern.
   * **Überprüfen der Übermittlungs-URL:** Sendet das Formular an den richtigen Endpunkt (Formularübermittlungsdienst-URL oder Ihr AEM-Publish-Pfad)?
   * **Formularübermittlungsdienst:** Hat `forms@adobe.com` Bearbeitungszugriff für das Senden an eine Tabelle? Ist die Tabellen-URL korrekt?
   * **AEM Publish-Übermittlungen:**
      * Erlaubt Ihr Dispatcher POSTs an `/adobe/forms/af/submit/...`?
      * Ist der Sling Referrer-Filter in der AEM-Veröffentlichungsinstanz so konfiguriert, dass er Ihre EDS-Domain zulässt?
      * Funktionieren Ihre CDN-Umleitungsregeln für `/adobe/forms/af/submit/...` ordnungsgemäß?

* **Mein eingebettetes Formular wird nicht angezeigt.**

   * **CORS** Dies ist der häufigste Grund. Überprüfen Sie die Browser-Konsole auf CORS-Fehler. Stellen Sie sicher, dass die Site, die das Formular *hostet*, die korrekten Header `Access-Control-Allow-Origin` enthält.
   * **Ist die Formular-URL korrekt?** Verweist der Einbettungs-Code auf der Host-Seite auf die korrekte Live-URL des Formulars?
   * **JavaScript-Blöcke:** Wenn das Formular auf einem spezifischen JavaScript-„Formularblock“ für das Rendern basiert, ist der Code dieses Blocks auf der Host-Seite verfügbar?

* **Bei der Übermittlung an AEM Publish erhalte ich die Fehlermeldung „403 Forbidden“ oder „401 Unauthorized“.**

   * Dies verweist häufig auf den Sling Referrer-Filter in AEM Publish, der keine Anfragen von Ihrer EDS-Domain erlaubt. Überprüfen Sie die Konfiguration.
   * Es kann auch ein Authentifizierungs-/Autorisierungsproblem sein, wenn Ihr AEM-Endpunkt für die Übermittlung dies erfordert, obwohl Standardformularübermittlungen in der Regel anonym sind.

## Nächste Schritte

Dieses Handbuch bietet einen Überblick über die Verwendung von Formularen mit AEM Edge Delivery Services. Detailliertere schrittweise Anweisungen zu bestimmten Konfigurationen finden Sie in der offiziellen Adobe Experience Manager-Dokumentation:

* [Dokumentenbasiertes Authoring mit Edge Delivery Services-Formularen.](/help/edge/docs/forms/tutorial.md)
* [Universeller Editor mit Edge Delivery Services-Formularen.](/help/edge/docs/forms/universal-editor/overview-universal-editor-for-edge-delivery-services-for-forms.md)
* [Dokumentenerstellung und Einbetten von Inhalten](https://www.aem.live/developer/da-tutorial)
* [AEM Forms-Übermittlungsdienst](/help/edge/docs/forms/configure-submission-action-for-eds-forms.md)
