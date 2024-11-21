---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 5d2c09a3e1c67e6c2435d84112546107d284259f
workflow-type: tm+mt
source-wordcount: '1778'
ht-degree: 41%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2022 oder 2023 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.11.0) ist der Freitag, 21. November 2024. Die nächste Version (2024.12.0) ist für den Freitag, 12. Dezember 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- ## Release Video {#release-video}

Have a look at the November 2024 Release Overview video for a summary of the features added in the 2024.11.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3434847?quality=12)

-->

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**[!DNL Edge Delivery Services]Seitenvorlagen mit Universal Editor Authoring**

Verwandeln Sie schnell eine beliebige Edge Delivery-Seite in eine Seitenvorlage. Auf diese Weise können Sie eine neue Seite mit einer vordefinierten Struktur und einem vordefinierten Inhalt anstelle einer leeren Seite beginnen. [Weitere Informationen](/help/sites-cloud/authoring/universal-editor/templates.md).

**[!DNL Edge Delivery Services]CSV-Importtool für die Veröffentlichung über eine AEM-Instanz**

Verwalten Sie Ihre Edge Delivery-Tabellenkalkulationsdaten (z. B. Umleitungen) effizient in Ihrem bevorzugten Tabellenkalkulationstool und laden Sie sie über das neue CSV-Importtool in AEM hoch. [Weitere Informationen](/help/edge/wysiwyg-authoring/tabular-data.md#importing).

### Vorabversionsfunktionen in AEM Sites

Verbesserte Referenzierung von Inhaltsfragmenten mit eindeutigen ID-basierten Referenzen, wodurch stabile Links sichergestellt werden, die auch dann gültig bleiben, wenn Assets oder Fragmente verschoben werden. Dadurch müssen keine Aktualisierungen mehr vorgenommen oder erneut veröffentlicht werden. Aktuelle Einschränkung: Seitenverweise werden noch nicht mit eindeutigen IDs unterstützt. Wenn in Inhaltsfragmenten auf Seiten verwiesen wird, sollte diese Funktion nicht verwendet werden.

### Early-Adopter-Programm {#sites-early-adopter}

**AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten**

Die [AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten](/help/headless/aem-rest-openapi-content-fragment-delivery.md) ist jetzt für AEM as a Cloud Service verfügbar.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Funktionen für frühzeitigen Zugriff in Dynamic Media {#dm-early-access}

**KI-generierte Videountertitel**

Bei KI-generierten Videountertiteln in Adobe Dynamic Media wird künstliche Intelligenz eingesetzt, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion soll die Barrierefreiheit und das Benutzererlebnis verbessern, indem akkurate Untertitel in Echtzeit bereitgestellt werden. Die KI analysiert die Audiospur des Videos, um Sprache zu transkribieren und Untertitel zu erstellen, die zwecks Korrektheit oder Anpassung bearbeitet werden können. Diese Untertitel dienen der Barrierefreiheit und machen Videos für Zielgruppen attraktiver, die textbasierte Videounterstützung nutzen bzw. bevorzugen.

Um frühzeitig Zugang zur Unterstützung für KI-generierte Untertitel in Ihrem Dynamic Media-Konto zu erhalten, [erstellen und senden Sie eine Anfrage an den Adobe-Kunden-Support.](/help/assets/dynamic-media/video.md##enable-dash)

**Dynamic Media-Bereitstellungsbericht**

Hier erhalten Sie Einblicke in die Bereitstellung von Assets, die mit Dynamic Media bereitgestellt werden, mit der Anzahl der Bereitstellungen auf Asset-Ebene, Referrer-Informationen, dem Asset-Pfad in AEM Assets und der eindeutigen Asset-ID. Berichte können für alle Assets generiert werden, die über Dynamic Media für das AEM Assets-Repository bereitgestellt werden, oder für eine bestimmte Ordnerhierarchie in AEM Assets. Mithilfe von Insights können Sie den ROI der bereitgestellten Assets messen, die Kanalleistung messen und fundierte Asset-Management-Aufgaben für Assets durchführen.

Um frühzeitigen Zugriff auf den Dynamic Media-Bereitstellungsbericht für Ihr Dynamic Media-Konto zu erhalten, erstellen und senden Sie eine Adobe-Support-Anfrage](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).[

### Neue Funktionen in der Assets-Ansicht {#assets-view-new-features}

**Dynamic Media-Bedienfeld**

Die Assets-Ansicht ermöglicht Ihnen jetzt den Zugriff auf Dynamic Media und Dynamic Media mit OpenAPI-Ausgabedarstellungen über ein separates Bedienfeld, das Ihnen zur Verfügung gestellt wird. Sie können die Bereitstellungs-URL kopieren oder die Ausgabedarstellungen entsprechend dem Asset- und Ausgabetyp herunterladen. Weitere Informationen finden Sie unter [Dynamic Media-Ausgabedarstellungen](/help/assets/renditions.md#dynamic-media-renditions) und [Dynamic Media mit OpenAPI-Leistungsausgabeformaten](/help/assets/renditions.md#dm-with-openapi-renditions).

![Dynamische Ausgabedarstellungen](/help/assets/assets/dm-scene7-renditions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in AEM Forms {#forms-new-features}

* **[Adobe Sign-Bereiche einfach aktualisieren](/help/forms/adobe-sign-integration-adaptive-forms.md)**: Sie können die Bereiche einer Adobe Sign-Konfiguration direkt auf der Seite „AEM Cloud-Konfigurationen“ ändern, um bestehende Konfigurationen schneller und leichter zu aktualisieren.

* **[Unterstützung von asynchronen Funktionen für adaptive Formulare](/help/forms/using-async-funct-in-rule-editor.md)**: Wenn für Ihr adaptives Formular asynchrone Vorgänge erforderlich sind, z. B. das Warten auf externe Prozesse oder das Abrufen von Daten, können Sie diese Vorgänge mit benutzerdefinierten Funktionen implementieren und im Regel-Editor konfigurieren.

### Vorab-Funktionen in AEM Forms {#forms-new-prerelease-features}

* **Veröffentlichung verwalten**: Sie können den Workflow Veröffentlichung verwalten verwenden, um Formulare in verschiedenen Umgebungen zu veröffentlichen oder deren Veröffentlichung rückgängig zu machen, normalerweise von der Autoreninstanz zur Veröffentlichungs- und Vorschauinstanz(en). Sie ermöglicht es Benutzern, Inhalte zu veröffentlichen, ihre Veröffentlichung rückgängig zu machen oder ihre Veröffentlichung zu planen.

* **[Automatisches Speichern eines Entwurfs für auf Kernkomponenten basierende adaptive Formulare](/help/forms/save-core-component-based-form-as-draft.md)**: Benutzende können jetzt von einer automatischen Speicherfunktion profitieren, mit der ein teilweise ausgefülltes Formular automatisch als Entwurf gespeichert wird. Sie können später zurückkehren, um das Ausfüllen des Formulars auf demselben oder einem anderen Gerät abzuschließen. Diese Funktion verbessert die Konversionsraten für Unternehmen, indem Formularabbrüche reduziert werden, da Benutzende nicht mit dem Ausfüllen von Formularen von Anfang an beginnen müssen.

* **[Verbesserungen des Regeleditors](/help/forms/invoke-service-enhancements-rule-editor.md)**: Für adaptive Forms, die auf Kernkomponenten basieren, können Sie jetzt Dropdown-Optionen mit der Ausgabe des Invoke-Dienstes füllen, wiederholbare Bedienfelder mithilfe der Ausgabe des Invoke-Dienstes festlegen, einzelne Bedienfelder mithilfe der Ausgabe des Invoke-Dienstes festlegen und den Ausgabeparameter von Invoke Service verwenden, um andere Felder zu validieren.

* **[Verbessern des Anwendererlebnisses mit Navigations-Schaltflächen in Bedienfeld-Layouts](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)**: Sie können Ihren Bedienfeld-Layouts jetzt Navigations-Schaltflächen hinzufügen, z. B. horizontale Registerkarten, vertikale Registerkarten, Akkordeons oder Assistent. Diese Schaltflächen verbessern das Anwendererlebnis, indem sie die Übergänge zwischen Bedienfeldern vereinfachen und sich auf das ausgewählte Bedienfeld konzentrieren.


### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### Integrationen

* **[Integrieren Sie Adaptive Forms in Adobe Marketo Engage](/help/forms/integrate-form-to-marketo-engage.md)**: AEM Forms as a Cloud Service bietet jetzt eine benutzerfreundliche Option, um Adaptive Forms mit Adobe Marketo Engage zu verbinden. Mit dieser Integration können Sie Adaptive Forms direkt mit Marketo Engage-Lead-Erfassung und zugehörigen benutzerdefinierten Objekten erstellen. Sie können jetzt Formularfelder mit Daten aus der Marketo Engage vorab ausfüllen und Daten zurücksenden, um Workflows wie Smart-Kampagnen und E-Mail-Automatisierung zu automatisieren. Sie können auch ein adaptives Formular mit der Munchkin-Bibliothek verbinden, um die Anzahl der Besuche, Klicks und Formularübermittlungen zu verfolgen.

#### Adaptive Forms und HTML5 Forms

* **[Adaptive Forms basierend auf vorhandener XFA-Vorlage erstellen](/help/forms/create-adaptive-form-using-xfa-templates.md)**: Sie können jetzt eine auf Kernkomponenten basierende adaptive Forms mit XFA-Formularvorlagen (*.XDP-Dateien) erstellen. Diese Funktion ermöglicht es AEM Forms On-Premise-Kunden mit bereits getätigten Investitionen in XFA-Technologien, AEM Forms as a Cloud Service zu übernehmen.

* **HTML5 Forms (XFA-basierte Webformulare)**: AEM Forms On-Premise-Kunden, die XFA-Technologie verwenden, können jetzt mühelos auf AEM Forms as a Cloud Service umsteigen und gleichzeitig ihr bestehendes Benutzererlebnis mit HTML5 Forms (XFA-basierte Webformulare) beibehalten. Diese Funktion ermöglicht die Wiedergabe von XFA-Formularvorlagen im HTML5-Format, sodass Formulare auf Geräten verfügbar sind, die XFA-basierte PDF forms nicht unterstützen.

  ![HTML Forms (XFA-basierte Webformulare)](/help/forms/assets/html-forms-xfa-based-web-forms.png)


* **[Base64-kodierte Zeichenfolgenunterstützung für Dateianlagen](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab)**: Die Dateianlagenkomponente im adaptiven Forms basierend auf Kernkomponenten enthält jetzt eine Option zum Senden angehängter Dateien als Base64-kodierte Zeichenfolgen.

#### APIs für interaktive Kommunikation und Kommunikation

* **Editor für interaktive Kommunikation**: Der Editor für interaktive Kommunikation ist ein benutzerfreundliches, grafisches Kommunikationsdesign-Tool, das die Erstellung personalisierter, datengesteuerter Schriftstücke vereinfacht und in jedem modernen Browser ausgeführt wird. Es unterstützt die nahtlose Datenintegration, die komplexe Logikdefinition und die Rich-Media-Integration, um eine professionelle und konforme Dokument-, Kommunikations- und Vorlagenerstellung für verschiedene geschäftliche Anforderungen zu gewährleisten.

  ![Editor für interaktive Kommunikation](/help/forms/assets/ic-editor.png)


* **[PDF/A Compliance Enhancements](/help/forms/aem-forms-cloud-service-communications-introduction.md#convert-to-and-validate-pdfa-compliant-documents)**: Sie können jetzt Kommunikations-APIs verwenden, um PDF-Dokumente für Archivierungszwecke in PDF/A-Formate (1a, 2a, 3a) zu konvertieren, während gleichzeitig die Barrierefreiheit gewährleistet und die Einhaltung dieser Standards überprüft wird.


* **[Signature API (Document Assurance)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance)**: Eine neue RESTful-API in Kommunikations-APIs ermöglicht die einfache Verwaltung von PDF-Signaturen. Es unterstützt Vorgänge wie:
   * Signatur löschen: Entfernt eine Signatur aus einem angegebenen Feld.
   * Signaturfeld entfernen: Löscht ein angegebenes Signaturfeld.


<!-- 
* **Hamburger Menu Layout in Adaptive Forms**: Adaptive Forms now offers a responsive hamburger menu layout for mobile devices. This collapsible menu organizes form sections, making navigation more 
intuitive and improving the mobile form-filling experience.

* **Masked Field with Eye Icon (Password Box Component)**: The Password Box is a text input field that masks the characters typed into it by displaying placeholder symbols. It allows users to securely input sensitive information, such as passwords and enables them to toggle visibility on demand using the eye icon.

-->

## Service zur automatisierten Formularkonvertierung

* **[PDF forms in Kernkomponenten-basierte adaptive Forms konvertieren](https://experienceleague.adobe.com/en/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms)**: Sie können jetzt den Automated forms conversion-Dienst verwenden, um PDF forms-, AcroForms- oder XFA-basierte Formulare in Kernkomponenten-basierte adaptive Forms umzuwandeln.


>[!IMPORTANT]
>
> Möchten Sie am Early-Access-Programm für Forms-Innovationen teilnehmen? Senden Sie von Ihrer offiziellen E-Mail-Adresse eine Nachricht an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) mit der Liste der Funktionen, an denen Sie interessiert sind.## CIF Add-on {#cloud-services-cif}

## CIF-Add-on {#cif}

### Fehlerbehebungen {#bug-fixes-cif}

* Die Benutzeroberflächentests funktionieren jetzt ordnungsgemäß mit den CIF-Kernkomponenten.
* Es wurde ein Problem behoben, durch das das URL-Format „Kategorie“ in der Cloud-Instanz nicht wie erwartet funktionierte.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Verbesserte Leistung bei der Baumreplikation (und veraltete Verwendung des Publish Content Tree-Workflows) {#tree-replication-performance}

Der Schritt [Tree Activation Workflow Schritt](/help/operations/replication.md#tree-activation) ist ein neuer Workflow-Modellschritt, der zum Replizieren von tiefen Inhaltshierarchien empfohlen wird. Beachten Sie, dass unabhängige Replikationen (z. B. durch schnelle Veröffentlichung oder Verwaltung der Veröffentlichung) parallel zum laufenden Workflow für die Strukturreplikation fortgesetzt werden können. Dies ist besonders nützlich, wenn Sie zeitkritische Inhalte veröffentlichen müssen, während eine Massenreplikation noch läuft. Der Schritt &quot;Tree Replication Step&quot;ersetzt den Publish Content Tree-Workflow und den zugehörigen Workflow-Schritt, der jetzt nicht mehr unterstützt wird.

### OpenAPI-basierte APIs - Frühkindliche Betreuung {#open-apis-earlyadopter}

Entwickler können AEM als Cloud Service-Funktionen in ihre eigenen Anwendungen und Tools integrieren. Neue AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation, um konsistent, gut dokumentiert und benutzerfreundlich zu sein. Anmeldeinformationen für Endpunkte, für die eine Authentifizierung erforderlich ist, werden durch Erstellen von Adobe Developer Console-Projekten generiert.

Erfahren Sie mehr über [OpenAPI-basierte AEM-APIs](/help/implementing/developing/open-api-based-apis.md) und probieren Sie ein [End-to-End-Tutorial](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) aus, in dem Konfiguration und Verwendung veranschaulicht werden.

Konkret sind die unten aufgeführten API-Endpunkte als Teil eines Programms für frühe Anwender verfügbar. Wenn Sie daran interessiert sind, senden Sie eine E-Mail an [aem-apis@adobe.com](mailto:aem-apis@adobe.com) , in der Sie beschreiben, wie Sie diese verwenden möchten.
* [Sites-Inhaltsfragmente-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de)
* [Assets-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [Sites- und Assets-Ordner-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [Forms Communications-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Edge Computing - Feedback anfordern! {#edge-computing-feedback}

Edge-Computing bringt die Datenverarbeitung näher an den Browser heran, was Vorteile bietet, einschließlich reduzierter Latenz. Als Beitrag zur Roadmap würden wir gerne hören, ob diese Technologie für AEM Publish-Bereitstellungs- und -Edge Delivery Services-Projekte nützlich ist und wofür Sie sie verwenden möchten. E-Mail [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit Fragen und Kommentaren!

### Neue AEM Developer Console (öffentliche Beta-Version) {#aem-developer-console-beta}

Probieren Sie die neu gestaltete [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) aus, die ein interaktiveres Erlebnis für das Debugging von Code in Cloud-Umgebungen bietet.

Jeder kann auf die öffentliche Beta-Version zugreifen, indem in der aktuellen AEM Developer Console auf die Schaltfläche *Neue Konsole verfügbar* geklickt wird. Adobe begrüßt Feedback, das Sie per E-Mail an [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com) senden können

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/release-notes/cloud-release-notes/2024-releases/2410-release/2410-0-release/whats-new-2024-10-0).

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
