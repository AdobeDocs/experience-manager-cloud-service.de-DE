---
title: '[!DNL AEM Forms] as a Cloud Service – Versionshinweise'
description: '[!DNL AEM Forms] as a Cloud Service – Versionshinweise'
exl-id: 35950b81-6e45-4a75-bd27-8c28fd68e42e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '2024'
ht-degree: 100%

---


# [!DNL Experience Manager Forms] as a Cloud Service – Versionshinweise {#overview}

Adobe Experience Manager [!DNL AEM Forms] as a Cloud Service wird ständig verbessert. Besuchen Sie diese Seite regelmäßig, um über die neuesten Entwicklungen auf dem Laufenden zu bleiben. Diese Seite bietet Ihnen Informationen über:

- Neue Funktionen
- Verbesserungen
- Funktionen der Vorabversion
- Beta-Funktionen
- Fehlerbehebungen
- Veraltete Funktionalität
- Spezielle Anweisungen
- Zukünftige Pläne für Änderungen

>[!NOTE]
>
>Versionshinweise zu allen anderen AEM as a Cloud Service-Versionskomponenten finden Sie unter [Aktuelle Versionshinweise](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/release-notes/release-notes/release-notes-current.html?lang=de).

## 2021.10.0 {#sep-2021-10-0}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms-oct-2021}

- **Analytics für adaptive Formulare**: Sie können jetzt das Verhalten sowohl angemeldeter als auch nicht angemeldeter (anonymer) Benutzer über Adobe Analytics für adaptive Formulare erfassen und verfolgen, um Erkenntnisse über Endbenutzern zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Erlebnis der Endbenutzer zu verbessern.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#prerelease-features-forms-oct-2021}

- **Externalisieren von AEM-Workflow-Daten für eine sichere Verarbeitung**: Sie können prozessinterne AEM-Workflow-Daten (AEM-Workflow-Variablendaten), die sensible personenbezogene Daten (SPD) beinhalten, zur sicheren Verarbeitung in einem vom Kunden verwalteten Repository speichern. Die Datenelemente und Workflow-Variablen werden nicht im AEM-Repository gespeichert, sondern bei der Verarbeitung des Workflows bei Bedarf aus dem vom Kunden verwalteten Repository abgerufen.

### Beta-Funktionen von [!DNL Forms] {#sep-what-is-new-forms-oct-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](aem-forms-cloud-service-communications.md) helfen Ihnen, eine Vorlage und XML-Daten zu kombinieren, um Print-Dokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus und im Batch-Modus generieren. Dabei können Sie mit den APIs Programme mit folgenden Funktionen erstellen:

   - Erzeugen von Dokumenten durch Ausfüllen von Vorlagendateien (PDF und XDP) mit XML-Daten.
   - Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Print-Datenströme.

Sie können an [!DNL formscsbeta@adobe.com] schreiben, um sich für das Beta-Programm anzumelden.

## 2021.9.0 {#sep-2021-09-0}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms-sep-2021}

- **Verwenden von Adobe Sign-Rollen in einem adaptiven Formular**: Die Service-Levels von Adobe Sign für Unternehmen bieten die Möglichkeit, die Rollen von Empfängern von Vereinbarungen über die unterschreibende Person hinaus zu erweitern und so ihren Workflow-Anforderungen besser zu entsprechen. Sie können jetzt [jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular zu konfigurieren](working-with-adobe-sign.md#addsignerstoanadaptiveform), wobei „Unterschreibende Person“ die Standardrolle ist.

- **Analytics für adaptive Formulare**: [Sie können jetzt das Endbenutzerverhalten über Adobe Analytics](integrate-aem-forms-with-adobe-analytics.md) für adaptive Formulare erfassen und verfolgen, um Erkenntnisse über Endbenutzer zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Erlebnis der Endbenutzer zu verbessern.

- **Einfaches Verbinden von AEM Forms mit Microsoft Dynamics und Salesforce**: Der Service stellt vorkonfigurierte Datenquellenkonfigurationen und Datenmodelle für Microsoft Dynamics und Salesforce bereit, sodass [Entwickler Microsoft Dynamics und Salesforce schneller und einfacher als Datenquellen für adaptive Formulare konfigurieren können](configure-msdynamics-salesforce.md).

- **E-Signieren eines adaptiven Formulars mit DocuSign:** [Sie können DocuSign verwenden, um ein adaptives Formular elektronisch zu unterzeichnen](integrate-docusign-adaptive-forms.md). Der Service bietet eine benutzerdefinierte Übermittlungsaktion zur Verwendung von DocuSign bei einem adaptiven Formular.

### Beta-Funktionen von [!DNL Forms] {#sep-what-is-new-forms-prerelease}

- **Unified Storage Connector:** Verwenden Sie Unified Storage Connector, um prozessinterne Daten in vom Kunden verwalteten Repositorys zu externalisieren. Sie können beispielsweise prozessinterne AEM-Workflow-Daten (AEM-Workflow-Variablendaten), die sensible personenbezogene (SPD) beinhalten, in einem vom Kunden verwalteten Repository speichern.

   <!--* Enable Forms Portal’s save and resume functionality and store adaptive forms drafts in a customer-managed data repository.-->

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](aem-forms-cloud-service-communications.md) helfen Ihnen, XDP-Vorlagen und XML-Daten zu kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Programme mit folgenden Funktionen erstellen:
   - Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   - Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Print-Datenströme.
   - Erzeugen von PDF-Druckdateien aus einem XFA-Formular-PDF und aus einem Adobe Acrobat-Formular.

Sie können an [!DNL formscsbeta@adobe.com] schreiben, um sich für das Beta-Programm anzumelden.

### Beschränkungen {#limitations}

- Adobe Analytics kann Formularmetriken nur für authentifizierte Benutzer verfolgen.

<!--

### New features available in [!DNL Forms] prerelease channel {#prerelease-features-forms-sep-2021}

* **Forms Portal:**  In a typical forms-centric portal deployment scenario, forms development and portal development are two disjoint activities. While Form Designers design and store forms in a repository, Web Developers create a web application to list forms and handle submission of forms. Forms are copied over to the web tier as there is no communication between the forms repository and the web application.

  Such scenarios often result in management issues and production delays. For example, if there is a newer version of a form available in the repository, you need to replace the form on the web tier, modify the web application, and redeploy the form on the public site. Redeploying the web application might cause some server downtime. Typically, the server downtime is a planned activity and therefore the changes cannot be pushed to the public site instantaneously.

  AEM Forms provides portal components that reduce management overheads and production delays. The components equip Web Developers to create and customize a forms portal on websites authored using Adobe Experience Manager (AEM). The form portal components allow you to add the following functionality:

  * List forms in customized layouts. Out of the box, List view and Card view are provided.

  * List published adaptive forms on an AEM Sites page.

  * Enable searching of forms based on a various criteria, such as form properties, metadata, and tags.

  * Lists drafts and submissions related to Adaptive Form created by end user.

  -->

## 2021.8.0 {#aug-2021-08-0}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms-aug-2021}

<!-- * Automated Forms Conversion service can [convert PDF Forms in Italian and Portuguese language](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?#language-specific-meta-model) to Adaptive Forms. -->

- Ein AEM-Archetyp-Projekt für Forms as a Cloud Service enthält jetzt [Formulardatenmodelle für Microsoft Dynamics und Salesforce](setup-local-development-environment.md).

- **AcroForm-basiertes Datensatzdokument**: AEM Forms as a Cloud Service unterstützt neben XFA-basierten Formularvorlagen die Verwendung von [Adobe Acrobat Form PDF (AcroForm PDF)](generate-document-of-record-for-non-xfa-based-adaptive-forms.md) als Vorlage für Datensatzdokumente (DoR, Documents of Record).

- **Microsoft Azure-Datenspeicherungs-Connector**: Sie können jetzt das [Formulardatenmodell mit der Microsoft Azure-Datenspeicherung verbinden](configure-azure-storage.md). Dadurch können Sie Daten aus adaptiven Formularen abrufen und in der Microsoft Azure-Datenspeicherung als BLOB speichern.

### Beta-Funktion von [!DNL Forms] {#aug-what-is-new-forms-prerelease}

- **Unified Storage Connector:** Verwenden Sie Unified Storage Connector, um prozessinterne Daten in vom Kunden verwalteten Repositorys zu externalisieren. Sie können beispielsweise

   - die Speicher- und Wiederaufnahmefunktion des Formularportals aktivieren und adaptive Formularentwürfe in einem vom Kunden verwalteten Daten-Repository speichern.
   - prozessinterne AEM-Workflow-Daten (AEM-Workflow-Variablendaten), die sensible personenbezogene Daten (SPD) beinhalten, in einem vom Kunden verwalteten Repository speichern.

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](aem-forms-cloud-service-communications.md) helfen Ihnen, XDP-Vorlagen und XML-Daten zu kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Programme mit folgenden Funktionen erstellen:
   - Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   - Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Print-Datenströme.
   - Erzeugen von PDF-Druckdateien aus einem XFA-Formular-PDF und aus einem Adobe Acrobat-Formular.

Sie können an [!DNL formscsbeta@adobe.com] schreiben, um sich für das Beta-Programm anzumelden.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#prerelease-features-forms-aug-2021}

- **Verwenden von Adobe Sign-Rollen in einem adaptiven Formular**: Die Service-Levels von Adobe Sign für Unternehmen bieten die Möglichkeit, die Rollen von Empfängern von Vereinbarungen über die unterschreibende Person hinaus zu erweitern und so ihren Workflow-Anforderungen besser zu entsprechen. Sie können jetzt [jedem Empfänger der Vereinbarung die Möglichkeit geben, seine Rolle in einem adaptiven Formular zu konfigurieren](working-with-adobe-sign.md#addsignerstoanadaptiveform), wobei „Unterschreibende Person“ die Standardrolle ist.

- **Analytics für adaptive Formulare**: Sie können jetzt das Endbenutzerverhalten über Adobe Analytics für adaptive Formulare erfassen und verfolgen, um Erkenntnisse über Endbenutzer zu sammeln. Es hilft dabei, fundierte Entscheidungen auf der Grundlage von Daten zu treffen, um das Erlebnis der Endbenutzer zu verbessern.

- **Einfaches Verbinden von AEM Forms mit Microsoft Dynamics und Salesforce**: Der Service stellt vorkonfigurierte Datenquellenkonfigurationen und Datenmodelle für Microsoft Dynamics und Salesforce bereit, sodass [Entwickler Microsoft Dynamics und Salesforce schneller und einfacher als Datenquellen für adaptive Formulare konfigurieren können](configure-msdynamics-salesforce.md).

## 2021.7.0 {#july-2021-07-0}

### Neue Funktionen in [!DNL Forms] {#july-what-is-new-forms}

- Sie können jetzt den Automated Forms Conversion-Service verwenden, um [PDF-Formulare in französischer, deutscher und spanischer Sprache](https://experienceleague.adobe.com/docs/aem-forms-automated-conversion-service/using/extending-the-default-meta-model.html?lang=de#language-specific-meta-model) in adaptive Formulare zu konvertieren.
- Es wurde ein separates Bedienfeld zum Vorlagen-Editor hinzugefügt, um Fehler im Zusammenhang mit Komponenten von adaptiven Formularen anzuzeigen. Dies hilft, alle Fehler in adaptiven Formularen an einem Ort zu konsolidieren und die Auflösungszeit zu verkürzen.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#july-prerelease-features-forms}

- **Acroform-basiertes aufzuzeichnendes Dokument**: Sie können auch [Adobe Acrobat Form PDF (Acroform PDF)](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/create-an-adaptive-form/generate-document-of-record-for-non-xfa-based-adaptive-forms.html?lang=de) als Vorlage für ein aufzuzeichnendes Dokument neben XFA-basierten Formularvorlagen verwenden.

- **Microsoft Azure-Datenspeicherungs-Connector**: Sie können jetzt das [Formulardatenmodell mit der Microsoft Azure-Datenspeicherung verbinden](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/use-form-data-model/configure-azure-storage.html?lang=de). Dadurch können Sie Daten aus adaptiven Formularen abrufen und in der Microsoft Azure-Datenspeicherung als BLOB speichern.

- **Variablendaten-Externalizer**: Sie können Daten von AEM-Workflow-Variablen in einem externen Speichersystem speichern, das von Ihrem Unternehmen verwaltet wird.

### Beta-Funktion von [!DNL Forms] {#july-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](aem-forms-cloud-service-communications.md) helfen Ihnen, XDP-Vorlagen und XML-Daten zu kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Programme mit folgenden Funktionen erstellen:
   - Erzeugen von Dokumenten durch Füllen von Vorlagendateien mit XML-Daten
   - Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Print-Datenströme.
   - Erzeugen von PDF-Druckdateien aus einem XFA-Formular-PDF und aus einem Adobe Acrobat-Formular.

## 2021.6.0 {#july-2021-06-0}

### Neue Funktionen in [!DNL Forms] {#june-what-is-new-forms}

- Benutzerdefinierte Spalten im AEM-Posteingang können jetzt gefiltert werden.
- Es wurde die Möglichkeit hinzugefügt, den Design-Editor und die Stilebene des Editors für adaptive Formulare zu verwenden, um die Captcha-Komponente zu gestalten.
- Verbesserte Geschwindigkeit und Genauigkeit bei der automatischen Erkennung logischer Abschnitte in den Quell-PDF-Formularen und Konvertieren dieser Abschnitte in entsprechende Bedienfelder adaptiver Formulare.
- Eine Aktion zum Verschieben von PDF- oder XDP-Dateien von einem Ordner in einen anderen wurde hinzugefügt.

### Beta-Funktion von [!DNL Forms] {#june-what-is-new-forms-prerelease}

- **[!DNL AEM Forms as a Cloud Service - Communications]**: Mithilfe von Kommunikations-APIs können Sie XDP-Vorlagen und XML-Daten kombinieren, um Druckdokumente in verschiedenen Formaten zu erzeugen. Mit dem Service können Sie Dokumente im synchronen Modus erzeugen. Dabei können Sie mit den APIs Programme mit folgenden Funktionen erstellen:

   - Erzeugen fertiger Formulardokumente durch Füllen von Vorlagendateien mit XML-Daten
   - Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Print-Datenströme.
   - Erzeugen von druckbaren PDFs aus einem XFA-Formular-PDF und Adobe Acrobat-Formular (AcroForm).

- **Variablendaten-Externalizer**: Sie können Daten von AEM-Workflow-Variablen in einem externen Speichersystem speichern, das von Ihrer Organisation verwaltet wird.

Sie können an [!DNL formscsbeta@adobe.com] schreiben, um sich für das Beta-Programm anzumelden.

### Fehlerbehebungen in [!DNL Forms] {#june-forms-bugs-fixed}

- Fehlerkorrektur – Wenn ein Feld vor dem Senden von Daten an den Backend-Service über das Formulardatenmodell (FDM) validiert wird, sind die Validierungen erfolgreich, und der Formulardatenmodell-Service kann die Nachvalidierung jetzt auch aufrufen.
- Fehlerkorrektur – Wenn Sie ein Formular mit einem standardmäßigen HTML-Upload-Feld von einem Apple iOS-Gerät senden, wird der Inhalt der Datei jetzt zuverlässig gesendet. Apple iOS 15.1 bietet eine Korrektur für das Problem.

## 2021.5.0 {#may-2021-05-0}

## [!DNL Adobe Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Neue Funktionen in [!DNL Forms] {#may-what-is-new-forms}

- **Kontextuelle Hilfe**: Es wurde eine kontextuelle Hilfe für den Editor für adaptive Formulare, den Vorlageneditor und den Design-Editor hinzugefügt, um Autoren dabei zu helfen, verschiedene Funktionen von Editoren besser zu verstehen.
- **Fehlermeldungen im Eigenschaften-Browser**: Es wurden Fehlermeldungen für jede Eigenschaft im Eigenschaften-Browser für adaptive Formulare hinzugefügt. Diese Meldungen helfen beim Verständnis der zulässigen Werte für ein Feld.

### Kommende Beta-Funktion von [!DNL Forms] {#may-what-is-new-forms-prerelease}

Output as a Cloud Service: Dieser Ausgabe-Service unterstützt Sie beim Kombinieren von XDP-Vorlagen und XML-Daten, um Druckdokumente in verschiedenen Formaten zu generieren. Mit dem Service können Sie Dokumente im synchronen und asynchronen Stapelmodus generieren. Dabei können Sie mit dem Output-Service Programme mit folgenden Funktionen erstellen:

- Generieren fertiger Formulardokumente durch Füllen von Vorlagendateien mit XML-Daten.
- Erzeugen von Ausgabeformularen in verschiedenen Formaten, einschließlich nicht interaktiver PDF-Print-Datenströme.
- Generieren von druckbaren PDFs aus XFA-Formular-PDFs

Sie können an formscsbeta@adobe.com schreiben, um sich für das Beta-Programm zu registrieren.

### Fehlerbehebungen in [!DNL Forms] {#may-forms-bugs-fixed}

- Wenn Sie in AEM Forms-Workflows in einem Schritt „Aufgabe zuweisen“ das Standardsymbol der Aktionsschaltflächen durch ein Coral-Symbol ersetzen, funktioniert die Workflows nicht mehr und protokollieren eine Ausnahme. Wenn Standardsymbole verwendet werden, funktioniert der Workflow wie erwartet.
- Wenn Sie auf der Layout-Ebene die Anzahl der Spalten ändern, die Bearbeitungsebene öffnen und einige Komponenten in ein Bedienfeld ziehen, werden im Inhaltsbereich des adaptiven Formular-Editors blaue Quadrate angezeigt und der Editor reagiert nicht mehr.
- Die Fehlermeldung einer Regeleditoroption im Zusammenhang mit der Bereitstellung der URL eines adaptiven oder externen Assets ist jetzt benutzerfreundlich und nicht mehr zu lang.

## 2021.4.0 {#april-2021-04-0}

### Neue Funktionen in [!DNL Forms] {#april-what-is-new-forms}

- **Identitätsauthentifizierungs-Methode Amtlicher Lichtbildausweis in Adobe Sign-fähigen adaptiven Formularen verwenden**

   Mit dem auf fortschrittlichen Algorithmen des maschinellen Lernens basierenden Verfahrens für amtliche Lichtbildausweise in Adobe Sign können Unternehmen auf der ganzen Welt eine hochwertige Authentifizierung der Identität ihrer Empfänger sicherstellen. Jetzt können Sie die Methode der Identitätsauthentifizierung über amtliche Lichtbildausweise in Adobe Sign-fähigen adaptiven Formularen verwenden.

   Amtlicher Lichtbildausweis ist eine erstklassige Identitätsauthentifizierungsmethode, die den Empfänger anweist, [das Bild eines staatlich ausgestellten Identitätsdokuments (Führerschein, Personalausweis, Pass) hochzuladen](https://helpx.adobe.com/de/sign/using/adobesign-authentication-government-id.html) und dieses Dokument dann bewertet, um seine Authentizität sicherzustellen.

- **Unterstützung für die Verwendung von Formularsignierlebnissen für asynchrone Übermittlungen adaptiver Formulare**

   Sie können jetzt das Formularsigniererlebnis für asynchrone Übermittlungen adaptiver Formulare verwenden. Sie können ein adaptives Formular auch in eine [!DNL Experience Manager Sites]-Seite einbetten und das Formularsigniererlebnis für Übermittlungen adaptiver Formulare verwenden.

- **Unterstützung für die Verwendung einer Variablen zum Angeben eines Anhang beim Vorausfüllen eines adaptiven Formulars für einen Schritt „Aufgabe zuweisen“**

   Beim Vorausfüllen eines adaptiven Formulars für einen Schritt „Aufgabe zuweisen“ können Sie jetzt eine Variable vom Typ „document“ verwenden, um einen Anhang als Eingabe für das adaptive Formular auszuwählen.

- **Unterstützung für die Verwendung der Option „Literal“ zum Festlegen eines Werts für eine JSON-Typvariable**

   Sie können die Option „Literal“ verwenden, um Werte für eine JSON-Typvariable im Schritt „set variable“ eines AEM-Workflows festzulegen. Mit der Option „Literal“ können Sie eine JSON in Form einer Zeichenfolge angeben.

- **Verwenden der lokalen Entwicklungsumgebung zum Erstellen des aufzuzeichnenden Dokuments (DoR)**

   in Cloud Service-Instanzen und im AEM Forms as a Cloud Service-SDK (Lokale Entwicklungsumgebung) können Sie einen XDP als Vorlage für das aufzuzeichnende Dokument verwenden. Zuvor war die Unterstützung auf Cloud Service-Instanzen beschränkt.

### Fehlerbehebungen in [!DNL Forms] {#april-bug-fixes-forms}

- Wenn ein adaptives Formular, das so konfiguriert wurde, dass es kein Datensatzdokument (DoR) generiert, an einen AEM-Workflow gesendet wird, der zum Generieren des DoR konfiguriert ist, wird jetzt eine Fehlermeldung angezeigt und die Aufgabe wird nicht übermittelt.
