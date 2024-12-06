---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: d7156a79f004a454b7689b2085a97d4c513d52b7
workflow-type: tm+mt
source-wordcount: '1802'
ht-degree: 98%

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

Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2024.11.0) ist der 21. November 2024. Die nächste Version (2025.1.0) ist für den 30. Januar 2024 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

## Video zur Version {#release-video}

Sehen Sie sich das Video Versionsübersicht von November 2024 an, um eine Zusammenfassung der Funktionen zu erhalten, die in der Version 2024.11.0 hinzugefügt wurden:

>[!VIDEO](https://video.tv.adobe.com/v/3440920?quality=12)

## [!DNL Experience Manager Sites] as a [!DNL Cloud Service] {#sites}

**[!DNL Edge Delivery Services]Seitenvorlagen mit Authoring mit dem universellen Editor**

Verwandeln Sie schnell eine beliebige Edge Delivery-Seite in eine Seitenvorlage. Auf diese Weise können Sie eine neue Seite mit einer vordefinierten Struktur und einem vordefinierten Inhalt anstelle einer leeren Seite beginnen. [Weitere Informationen](/help/sites-cloud/authoring/universal-editor/templates.md).

**[!DNL Edge Delivery Services]CSV-Importer für das Publishing über eine AEM-Instanz**

Verwalten Sie Ihre Edge Delivery-Tabellenkalkulationsdaten (z. B. Umleitungen) effizient in Ihrem bevorzugten Tabellenkalkulations-Tool und laden Sie sie über den neuen CSV-Importer in AEM hoch. [Weitere Informationen](/help/edge/wysiwyg-authoring/tabular-data.md#importing).

### Funktionen in der Vorabversion in AEM Sites

Verbesserte [Referenzierung von Inhaltsfragmenten mit eindeutigen ID-basierten Referenzen](/help/headless/graphql-api/uuid-reference-upgrade.md), wodurch stabile Links sichergestellt werden, die auch dann gültig bleiben, wenn Assets oder Fragmente verschoben werden – sodass Aktualisierungen oder erneutes Veröffentlichen nicht mehr erforderlich sind. Aktuelle Einschränkung: Seitenverweise werden noch nicht mit eindeutigen IDs unterstützt. Wenn Seiten in Inhaltsfragmenten referenziert werden, sollte diese Funktion nicht verwendet werden.

### Early-Adopter-Programm {#sites-early-adopter}

**AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten**

Die [AEM REST OpenAPI für die Bereitstellung von Inhaltsfragmenten](/help/headless/aem-rest-openapi-content-fragment-delivery.md) ist jetzt für AEM as a Cloud Service verfügbar.

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

### Early-Access-Funktionen in Dynamic Media {#dm-early-access}

**KI-generierte Videountertitel**

Bei KI-generierten Videountertiteln in Adobe Dynamic Media wird künstliche Intelligenz eingesetzt, um automatisch Untertitel für Videoinhalte zu generieren. Diese Funktion soll die Barrierefreiheit und das Benutzererlebnis verbessern, indem akkurate Untertitel in Echtzeit bereitgestellt werden. Die KI analysiert die Audiospur des Videos, um Sprache zu transkribieren und Untertitel zu erstellen, die zwecks Korrektheit oder Anpassung bearbeitet werden können. Diese Untertitel dienen der Barrierefreiheit und machen Videos für Zielgruppen attraktiver, die textbasierte Videounterstützung nutzen bzw. bevorzugen.

Um frühzeitig Zugang zur Unterstützung für KI-generierte Untertitel in Ihrem Dynamic Media-Konto zu erhalten, [erstellen und senden Sie eine Anfrage an den Adobe-Kunden-Support.](/help/assets/dynamic-media/video.md##enable-dash)

**Dynamic Media-Bereitstellungsbericht**

Hier erhalten Sie Einblicke in die Bereitstellung von Assets, die mit Dynamic Media bereitgestellt werden, mit der Anzahl der Bereitstellungen auf Asset-Ebene, Referrer-Informationen, dem Asset-Pfad in AEM Assets und der eindeutigen Asset-ID. Berichte können für alle Assets generiert werden, die über Dynamic Media für das AEM Assets-Repository bereitgestellt werden, oder für eine bestimmte Ordnerhierarchie in AEM Assets. Mithilfe von Insights können Sie den ROI der bereitgestellten Assets messen, die Kanalleistung messen und fundierte Asset-Management-Aufgaben für Assets durchführen.

Um frühzeitig Zugang zum Dynamic Media-Bereitstellungsbericht in Ihrem Dynamic Media-Konto zu erhalten, [erstellen und senden Sie eine Anfrage an den Adobe-Kunden-Support](https://helpx.adobe.com/de/enterprise/using/support-for-experience-cloud.html).

### Neue Funktionen in der Assets-Ansicht {#assets-view-new-features}

**Dynamic Media-Bedienfeld**

Die Assets-Ansicht ermöglicht Ihnen jetzt den Zugriff auf Dynamic Media und Dynamic Media mit OpenAPI-Ausgabedarstellungen über ein separates Bedienfeld, das Ihnen zur Verfügung gestellt wird. Sie können die Bereitstellungs-URL kopieren oder die Ausgabedarstellungen entsprechend dem Asset- und Ausgabetyp herunterladen. Weitere Informationen finden Sie unter [Dynamic Media-Ausgabedarstellungen](/help/assets/renditions.md#dynamic-media-renditions) und [Ausgabedarstellungen durch Dynamic Media mit OpenAPI-Funktionen](/help/assets/renditions.md#dm-with-openapi-renditions).

![Dynamische Ausgabedarstellungen](/help/assets/assets/dm-scene7-renditions.png)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in AEM Forms {#forms-new-features}

* **[Adobe Sign-Bereiche einfach aktualisieren](/help/forms/adobe-sign-integration-adaptive-forms.md)**: Sie können die Bereiche einer Adobe Sign-Konfiguration direkt auf der Seite „AEM Cloud-Konfigurationen“ ändern, um bestehende Konfigurationen schneller und leichter zu aktualisieren.

* **[Unterstützung von asynchronen Funktionen für adaptive Formulare](/help/forms/using-async-funct-in-rule-editor.md)**: Wenn für Ihr adaptives Formular asynchrone Vorgänge erforderlich sind, z. B. das Warten auf externe Prozesse oder das Abrufen von Daten, können Sie diese Vorgänge mit benutzerdefinierten Funktionen implementieren und im Regel-Editor konfigurieren.

### Vorabversionsfunktionen in AEM Forms {#forms-new-prerelease-features}

* **Veröffentlichung verwalten**: Sie können den Workflow „Veröffentlichung verwalten“ verwenden, um Formulare in verschiedenen Umgebungen zu veröffentlichen oder deren Veröffentlichung rückgängig zu machen, normalerweise von der Autoreninstanz zur Veröffentlichungs- und Vorschauinstanz(en). Er ermöglicht es Benutzenden, Inhalte zu veröffentlichen, ihre Veröffentlichung rückgängig zu machen oder ihre Veröffentlichung effizient zu planen.

* **[Automatisches Speichern eines Entwurfs für auf Kernkomponenten basierende adaptive Formulare](/help/forms/save-core-component-based-form-as-draft.md)**: Benutzende können jetzt von einer automatischen Speicherfunktion profitieren, mit der ein teilweise ausgefülltes Formular automatisch als Entwurf gespeichert wird. Sie können später zurückkehren, um das Ausfüllen des Formulars auf demselben oder einem anderen Gerät abzuschließen. Diese Funktion verbessert die Konversionsraten für Unternehmen, indem Formularabbrüche reduziert werden, da Benutzende nicht mit dem Ausfüllen von Formularen von Anfang an beginnen müssen.

* **[Verbesserungen des Regeleditors](/help/forms/invoke-service-enhancements-rule-editor.md)**: Für adaptive Formulare, die auf Kernkomponenten basieren, können Sie jetzt Dropdown-Optionen mit der Ausgabe des Aufrufdienstes füllen, wiederholbare Bedienfelder mithilfe der Ausgabe des Aufrufdienstes festlegen, einzelne Bedienfelder mithilfe der Ausgabe des Aufrufdienstes festlegen und den Ausgabeparameter des Aufrufdienstes verwenden, um andere Felder zu validieren.

* **[Verbessern des Anwendererlebnisses mit Navigations-Schaltflächen in Bedienfeld-Layouts](/help/forms/rule-editor-core-components-usecases.md#navigating-among-panels-using-button)**: Sie können Ihren Bedienfeld-Layouts jetzt Navigations-Schaltflächen hinzufügen, z. B. horizontale Registerkarten, vertikale Registerkarten, Akkordeons oder Assistent. Diese Schaltflächen verbessern das Anwendererlebnis, indem sie die Übergänge zwischen Bedienfeldern vereinfachen und sich auf das ausgewählte Bedienfeld konzentrieren.


### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### Integrationen

* **[Integration adaptiver Formulare in Adobe Marketo Engage](/help/forms/integrate-form-to-marketo-engage.md)**: AEM Forms as a Cloud Service bietet jetzt eine benutzerfreundliche Option, um adaptive Formulare mit Adobe Marketo Engage zu verbinden. Mit dieser Integration können Sie adaptive Formulare direkt mit der Marketo Engage-Lead-Erfassung und zugehörigen benutzerdefinierten Objekten erstellen. Sie können jetzt Formularfelder mit Daten aus Marketo Engage vorab ausfüllen und Daten zurücksenden, um Workflows wie intelligente Kampagnen und E-Mail-Automatisierung zu automatisieren. Sie können auch ein adaptives Formular mit der Munchkin-Bibliothek verbinden, um die Anzahl der Besuche, Klicks und Formularübermittlungen zu verfolgen.

#### Adaptive Formulare und HTML5-Formulare

* **[Erstellen adaptiver Formulare basierend auf vorhandener XFA-Vorlage](/help/forms/create-adaptive-form-using-xfa-templates.md)**: Sie können jetzt auf Kernkomponenten basierende adaptive Formulare mit XFA-Formularvorlagen (*.XDP-Dateien) erstellen. Diese Funktion ermöglicht es AEM Forms On-Premise-Kundinnen und -Kunden mit bereits getätigten Investitionen in XFA-Technologien, AEM Forms as a Cloud Service zu übernehmen.

* **HTML5 Forms (XFA-basierte Web-Formulare)**: AEM Forms On-Premise-Kundinnen und -Kunden, die XFA-Technologie verwenden, können jetzt mühelos auf AEM Forms as a Cloud Service umsteigen und gleichzeitig ihr bestehendes Anwendererlebnis mit HTML5 Forms (XFA-basierte Web-Formulare) beibehalten. Diese Funktion ermöglicht die Wiedergabe von XFA-Formularvorlagen im HTML5-Format, sodass Formulare auf Geräten verfügbar sind, die XFA-basierte PDF-Formulare nicht unterstützen.

  ![HTML Forms (XFA-basierte Web-Formulare)](/help/forms/assets/html-forms-xfa-based-web-forms.png)


* **[Base64-codierte Zeichenfolgenunterstützung für Dateianlagen](https://experienceleague.adobe.com/de/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment#basic-tab)**: Die Dateianlagenkomponente im adaptiven Formularen, die auf Kernkomponenten basiert, enthält jetzt eine Option zum Senden angehängter Dateien als Base64-codierte Zeichenfolgen.

#### Interaktive Kommunikationen und Kommunikations-APIs

* **Editor für interaktive Kommunikationen**: Der Editor für interaktive Kommunikationen ist ein benutzerfreundliches, grafisches Tool zum Design von Kommunikationen, das die Erstellung personalisierter, datengesteuerter Korrespondenz vereinfacht und in jedem modernen Browser ausgeführt werden kann. Es unterstützt die nahtlose Datenintegration, die komplexe Logikdefinition und die Rich-Media-Integration, um eine professionelle und konforme Erstellung von Dokumenten, Kommunikationen und Vorlagen für verschiedene geschäftliche Anforderungen zu gewährleisten.

  ![Editor für interaktive Kommunikationen](/help/forms/assets/ic-editor.png)


* **[Verbesserungen bei der PDF/A-Compliance](/help/forms/aem-forms-cloud-service-communications-introduction.md#convert-to-and-validate-pdfa-compliant-documents)**: Sie können jetzt Kommunikations-APIs verwenden, um PDF-Dokumente für Archivierungszwecke in PDF/A-Formate (1a, 2a, 3a) zu konvertieren und dabei die Zugänglichkeit sicherzustellen und die Einhaltung dieser Standards zu überprüfen.


* **[Signature-API (Document Assurance)](/help/forms/aem-forms-cloud-service-communications-introduction.md#document-assurance)**: Eine neue RESTful-API in Kommunikations-APIs ermöglicht die einfache Verwaltung von PDF-Signaturen. Sie unterstützt Vorgänge wie:
   * Signatur löschen: Entfernt eine Signatur aus einem angegebenen Feld.
   * Signaturfeld entfernen: Löscht ein angegebenes Signaturfeld.


<!-- 
* **Hamburger Menu Layout in Adaptive Forms**: Adaptive Forms now offers a responsive hamburger menu layout for mobile devices. This collapsible menu organizes form sections, making navigation more 
intuitive and improving the mobile form-filling experience.

* **Masked Field with Eye Icon (Password Box Component)**: The Password Box is a text input field that masks the characters typed into it by displaying placeholder symbols. It allows users to securely input sensitive information, such as passwords and enables them to toggle visibility on demand using the eye icon.

-->

## Service zur automatisierten Formularkonvertierung

* **[PDF-Formulare in Kernkomponenten-basierte adaptive Formulare konvertieren](https://experienceleague.adobe.com/de/docs/aem-forms-automated-conversion-service/using/convert-existing-forms-to-adaptive-forms)**: Sie können jetzt den Service zur automatisierten Formularkonvertierung verwenden, um PDF-Formulare, AcroForms oder XFA-basierte Formulare in Kernkomponenten-basierte adaptive Formulare umzuwandeln.


>[!IMPORTANT]
>
> Möchten Sie am Early-Access-Programm für Forms-Innovationen teilnehmen? Senden Sie von Ihrer offiziellen E-Mail-Adresse eine Nachricht an [aem-forms-ea@adobe.com](mailto:aem-forms-ea@adobe.com) mit der Liste der Funktionen, an denen Sie interessiert sind.## CIF-Add-on {#cloud-services-cif}

## CIF-Add-on {#cif}

### Fehlerbehebungen {#bug-fixes-cif}

* Die Benutzeroberflächentests funktionieren jetzt ordnungsgemäß mit den CIF-Kernkomponenten.
* Es wurde ein Problem behoben, durch das das URL-Format „Kategorie“ in der Cloud-Instanz nicht wie erwartet funktionierte.

## [!DNL Experience Manager] as a [!DNL Cloud Service]-Foundation {#foundation}

### Verbesserte Leistung bei der Strukturreplikation (und Einstellung der Verwendung des Workflows für die Veröffentlichung einer Inhaltsstruktur) {#tree-replication-performance}

Der [Workflow-Schritt für die Strukturaktivierung](/help/operations/replication.md#tree-activation) ist ein neuer Workflow-Modellschritt, der zum Replizieren von tiefen Inhaltshierarchien empfohlen wird. Beachten Sie, dass unabhängige Replikationen (z. B. durch schnelle Veröffentlichung oder Verwalten der Veröffentlichung) parallel zum laufenden Workflow für die Strukturreplikation fortgesetzt werden können. Dies ist besonders nützlich, wenn Sie zeitkritische Inhalte veröffentlichen müssen, während eine Massenreplikation noch läuft. Der Strukturreplikationsschritt ersetzt den Workflow für die Veröffentlichung der Inhaltsstruktur und den zugehörigen Workflow-Schritt, der jetzt nicht mehr unterstützt wird.

### OpenAPI-basierte APIs – Early-Adopter-Programm {#open-apis-earlyadopter}

Entwickelnde können AEM as a Cloud Service-Funktionen in ihre eigenen Anwendungen und Tools integrieren. Neue AEM as a Cloud Service-APIs folgen der OpenAPI-Spezifikation, weil sie konsistent, gut dokumentiert und benutzerfreundlich sein sollen. Anmeldeinformationen für Endpunkte, für die eine Authentifizierung erforderlich ist, werden durch Erstellen von Adobe Developer Console-Projekten generiert.

Erfahren Sie mehr über [OpenAPI-basierte AEM-APIs](/help/implementing/developing/open-api-based-apis.md) und probieren Sie ein [End-to-End-Tutorial](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/aem-apis/invoke-openapi-based-aem-apis) aus, in dem Konfiguration und Verwendung veranschaulicht werden.

Konkret sind die unten aufgeführten API-Endpunkte im Rahmen eines Early-Adopter-Programms verfügbar. Wenn Sie daran interessiert sind, senden Sie eine E-Mail an [aem-apis@adobe.com](mailto:aem-apis@adobe.com), in der Sie beschreiben, wie Sie die API-Endpunkte verwenden möchten.
* [Sites-Inhaltsfragmente-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/stable/sites/?lang=de)
* [Assets-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/assets/author/)
* [Sites- und Assets-Ordner-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/folders/)
* [Forms-Kommunikationen-APIs](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/document/)

### Edge-Computing – Einladung zum Feedback! {#edge-computing-feedback}

Edge-Computing bringt die Datenverarbeitung näher an den Browser heran, was Vorteile bietet, darunter eine reduzierte Latenz. Als Input für die Roadmap würden wir gerne von Ihnen hören, ob Sie diese Technologie als nützlich für AEM-Projekte für Veröffentlichungsbereitstellungs- und Edge-Bereitstellungsdienste erachten würden und wofür Sie sie voraussichtlich verwenden würden. Schreiben Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit Fragen und Kommentaren!

### Neue AEM Developer Console (öffentliche Beta-Version) {#aem-developer-console-beta}

Probieren Sie die neu gestaltete [AEM Developer Console](/help/implementing/developing/introduction/aem-developer-console.md) aus, die ein interaktiveres Erlebnis für das Debugging von Code in Cloud-Umgebungen bietet.

Jeder kann auf die öffentliche Beta-Version zugreifen, indem in der aktuellen AEM Developer Console auf die Schaltfläche *Neue Konsole verfügbar* geklickt wird. Adobe freut sich über Feedback, das Sie per E-Mail an [aemcs-new-devconsole-ui-beta@adobe.com](mailto:aemcs-new-devconsole-ui-beta@adobe.com) senden können.

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
