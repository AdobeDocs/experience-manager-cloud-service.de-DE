---
title: Änderungen zwischen AEM 6.5 Forms und AEM Cloud Services
description: 'Verwenden Sie Experience Manager Forms und möchten auf Adobe Experience Manager Forms as a Cloud Service aktualisieren? In diesem Abschnitt erfahren Sie mehr über die wichtigsten Änderungen, bevor Sie auf Cloud Service aktualisieren oder migrieren.  '
contentOwner: khsingh
exl-id: 46fcc1b4-8fd5-40e1-b0fc-d2bc9df3802e
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '1214'
ht-degree: 100%

---

# Wesentliche Änderungen für bestehende Adobe Experience Manager Forms-Benutzer  {#notable-changes-for-existing-AEM-Forms-users}

Adobe Experience Manager Forms as a Cloud Service enthält einige wichtige Änderungen an bestehenden Funktionen im Vergleich zu Adobe Experience Manager Forms On-Premise- und [!DNL Adobe-Managed Service]-Umgebungen. Die wichtigsten Unterschiede sind im Folgenden aufgeführt:

* Der Service bietet eine lokale und eine Cloud-native Entwicklungsumgebung. Sie können eine [lokale Entwicklungsumgebung](setup-local-development-environment.md) verwenden, um benutzerdefinierten Code, Komponenten, Vorlagen, Designs, adaptive Formulare und andere Assets zu entwickeln und zu testen, bevor Sie diese Assets in einer Cloud-Umgebung bereitstellen. Auf diese Weise wird der Entwicklungsprozess beschleunigt.
* [!DNL AEM] as Cloud Service wird mit einem integrierten CDN ausgeliefert. Der Hauptzweck besteht darin, die Latenz zu verringern, indem zwischengespeicherte Inhalte von den CDN-Knoten in der Nähe des Browsers bereitgestellt werden. Es ist vollständig verwaltet und für eine optimale Leistung von AEM-Programmen konfiguriert.
* Eine Cloud-native Umgebung verfügt nicht über Web Console (Konfigurations-Manager). Sie können das [[!DNL AEM Forms]  as a Cloud Service SDK verwenden, um Konfigurationen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#generating-osgi-configurations-using-the-aem-sdk-quickstart) und eine CI/CD-Pipeline zur [Bereitstellung der Konfiguration](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/using-cloud-manager/deploy-code.html?lang=de#deployment-process) für Ihre Cloud Service-Instanz zu generieren.

* Die URL-Konvention von lokalisierten adaptiven Formularen unterstützt nun die Angabe eines Gebietsschemas in der URL. Die neue URL-Konvention ermöglicht das Caching lokalisierter Formulare in einem Dispatcher oder CDN. Verwenden Sie in der Cloud Service-Umgebung, um die lokalisierte Version eines adaptiven Formulars anzufordern, das URL-Format `http://host:port/content/forms/af/<afName>.<locale>.html` statt `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`. Adobe empfiehlt die Verwendung von Dispatcher- oder CDN-Caching. Auf diese Weise wird das Rendern vorausgefüllter Formulare beschleunigt.
* Bei der Formularvorbefüllung werden Daten mit einem adaptiven Formular auf einem Client zusammengeführt. Der Zeitaufwand für das Vorbefüllen eines adaptiven Formulars wird dadurch verringert. Sie können jederzeit konfigurieren, dass die Zusammenführung auf dem Adobe Experience Manager Forms-Server ausgeführt wird.
* E-Mail unterstützt standardmäßig nur HTTP- und HTTPS-Protokolle. [Kontaktieren Sie das Support-Team](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/developing/development-guidelines.html?lang=de#sending-email), um Ports für den Versand von E-Mails und das SMTP-Protokoll für Ihre Umgebung zu aktivieren.
* Adobe Experience Manager Forms as a Cloud Service bietet eine Vielzahl neuer Funktionen und Möglichkeiten für Ihre AEM-Projekte. Es sind jedoch einige Änderungen erforderlich, damit Adobe Experience Manager-Maven-Projekte mit AEM Cloud Service kompatibel sind. Im Allgemeinen erfordert AEM eine Trennung von Inhalt und Code in separate Unterpakete, um die Aufteilung zwischen veränderlichem und unveränderlichem Inhalt zu berücksichtigen. Verwenden Sie das Tool [Repository Modernizer](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/refactoring-tools/repo-modernizer.html?lang=de), um bestehende Projektpakete neu zu strukturieren, indem Inhalt und Code in separate Pakete aufgeteilt werden. So gewährleisten Sie die Kompatibilität der Pakete mit der Projektstruktur, die für Adobe Experience Manager as a Cloud Service definiert wurde.

<!--  If your Cloud Configuration contains a secret (password), create a separate Cloud Configuration for every Author instance (Developer, Stage, and Production). If a Cloud Configuration is also required on Publish instances, publish/replicate a separate Cloud Configuration for every Publish instance (Developer, Stage, and Production). 

* When you create a Cloud Configuration that contains a secret, each Cloud Service instance (Developer, Stage, and Production) uses its own encryption key to encrypt the password before storing it. So, manually create such Cloud Configuration for every Cloud Service instance (Developer, Stage, and Production). Also, do not store secrets used in a Cloud Configuration to your Cloud Manager Git repository.

* Use [!DNL Cloud Manager] [APIs to convert and provide your passwords as secrets](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=en#setting-values-via-api). Do not store plain text password or secrets on your environments. -->

* Verwendung umgebungsspezifischer Konfigurationen für geheime OSGi-Konfigurationswerte wie Passwörter, private API-Schlüssel oder andere Werte. Diese können aus Sicherheitsgründen nicht in Git gespeichert werden. [Verwenden Sie geheime umgebungsspezifische Konfigurationen, um den Wert für Geheimnisse in allen Adobe Experience Manager as a Cloud Service-Umgebungen zu speichern, einschließlich Staging- und Produktionsumgebungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#when-to-use-secret-environment-specific-configuration-values).

Eine umfassende Liste der Änderungen in Adobe Experience Manager as a Cloud Service finden Sie unter [Neue Funktionen und Änderungen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/what-is-new-and-different.html?lang=de).

<!-- ## Feature comparison {#comparison}

[!DNL AEM Forms] as a Cloud Service and Experience Manager 6.5 Forms share a common set of features: Adaptive Forms, data integration, integration with [!DNL Adobe Sign], themes, templates, and forms management interface are identical. You can easily port your existing Adaptive Forms from an Experience Manager 6.5 Forms or an earlier version to [!DNL AEM Forms] as a Cloud Service.

### Features of AEM 6.5 Forms and [!DNL AEM Forms] as a Cloud Service {#feature-comparison}

The following table lists the major features of Experience Manager 6.5 Forms and provides information about whether the feature is partially or fully supported in [!DNL AEM Forms] as a Cloud Service, with a link to more information about the feature. The table also lists extra features available in [!DNL AEM Forms] as a Cloud Service.


| Feature/Capability | AEM 6.5 Forms | [!DNL AEM Forms] as a Cloud Service |
| - | - | - |
| Adaptive Forms | &#x2611; | &#x2611; |
| Data Integration | &#x2611; | &#x2611;(With some changes) |
| Automated Forms Conversion Service | &#x2611; | &#x2611; |
| Integration with Adobe Sign | &#x2611; | &#x2611;(With some changes) |
| Themes and Templates | &#x2611; | &#x2611; ([With some changes](themes.md#difference-in-themes))|
| Rule editor | &#x2611; | &#x2611; (With some changes) |
| Forms Portal | &#x2611; | --- |
| Integration with Adobe Analytics | &#x2611; | &#x2612; |
| Document Security | &#x2611; | &#x2612; | -->

<!-- ## New features {#comparison} -->



## Wichtige Verbesserungen {#whats-new}

<!-- [!DNL AEM Forms] as a Cloud Service offers benefits like auto-scaling, cost-effectiveness, zero downtime for upgrades, and cloud-native development environment and more. The list does not stop here. The following features are are start and are available only for [!DNL AEM Forms] as a Cloud Service: -->

Folgende Funktionen und Erweiterungen sind nur in [!DNL AEM Forms] as a Cloud Service verfügbar:

**Erweiterter Visual Rule Editor**
Der Service bietet einen gehärteten [Visual Rule Editor](rule-editor.md#visual-rule-editor). Folgende im Service ergänzte Funktionen im Visual Rule Editor helfen Ihnen beim Erstellen effektiver Regeln:

* [Neue Übermittlungsereignisse](working-with-adobe-sign.md#available-operator-types-and-events-in-rule-editor): `Navigation`, `Step Completion`, `Successful Submission` und `Error`

* [Neuer Datentyp `scope`](rule-editor.md#custom-functions). Sie können den Datentyp `scope` in einer benutzerdefinierten Funktion verwenden, um den gesamten Umfang eines Formulars zu übergeben.

* Verwenden von [@this zur Angabe eines JSDoc innerhalb einer benutzerdefinierten Funktion](rule-editor.md#custom-functions). Durch die Verwendung von @this in einer aktiven Komponente kann eine benutzerdefinierte Funktion aufgerufen werden.

* Hinzufügen von Bedingungen für eigenschaftsbasierte Regeln.

**Kernkomponenten**
Die [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) sind eine Reihe standardisierter Web Content Management (WCM)-Komponenten für AEM, die die Entwicklungszeit verkürzen und die Wartungskosten senken. [!DNL AEM Forms] as a Cloud Service unterstützt die **[!UICONTROL Container-Kernkomponente von AEM Forms]**. Sie können die Komponente dazu verwenden, ein adaptives Formular in eine AEM Sites-Seite einzubetten.

**AEM-Archetyp für Forms as a Cloud Service**
[Der AEM-Archetyp](https://github.com/adobe/aem-project-archetype/releases/tag/aem-project-archetype-27) hilft Ihnen beim Einstieg in die Entwicklung für [!DNL AEM Forms] as a Cloud Service. Verwenden Sie Archteyp-Version 27 oder höher, um eine mit [!DNL AEM Forms] as a Cloud Service kompatible Vorlage zu erstellen. Der Archteyp beinhaltet einige Beispielthemen und -vorlagen, die Ihnen beim schnellen Einstieg helfen.

**Sicherer und verbesserter Informationsfluss zwischen Formularen und Sign**
Die Integration von [adaptiven Formularen und Adobe Sign](working-with-adobe-sign.md) auf Cloud Service ermöglicht das gleichzeitige Senden von Daten und Unterzeichnungsvorgängen. Dadurch ist die Formularübermittlung vom Unterzeichnungsstatus unabhängig, wodurch das Senden schneller wird. Zudem speichert der Service keine Daten in Cloud Service und gewährleistet so maximale Sicherheit für den Unterzeichnungsvorgang.

**Best Practices Analyzer und Migration-Tools**
Best Practices Analyzer erstellt eine Bewertung Ihrer aktuellen AEM-Implementierung. Führen Sie das Tool vor der [Migration zu Forms as a Cloud Service](migrate-to-forms-as-a-cloud-service.md) aus. Es bewertet die Bereitschaft, von einer bestehenden Implementierung von Adobe Experience Manager (AEM) zu AEM as a Cloud Service zu migrieren.

Der Service bietet zudem ein [verbessertes Migrationserlebnis](migrate-to-forms-as-a-cloud-service.md), damit Sie nahtlos von [!DNL AEM 6.4 Forms] und [!DNL AEM 6.5 Forms] zu [!DNL AEM Forms] as a Cloud Service wechseln können.

**Schnellere Formulardarstellung und schnellere Server-seitige Validierung**
Der Service verwendet CDN- und Dispatcher-Caching, um schnellere Darstellungen und Server-seitige Validierungen für adaptive Formulare zu ermöglichen.

**Verbessertes CAPTCHA**
Sie können jetzt [CAPTCHA-Überprüfungen](captcha-adaptive-forms.md) beim Senden adaptiver Formulare oder bei einer Business-Logik nutzen. Indem Sie Bedingungen hinzufügen, können Sie CAPTCHA-Eingaben bei einer Benutzeraktion überprüfen und die CAPTCHA-Komponente in einem adaptiven Formular auf der Basis von Regeln ein- oder ausblenden.

Die CAPTCHA-Komponente bietet eine vorkonfigurierte Integration mit Google reCAPTCHA. Bei Bedarf können Sie auch weitere CAPTCHA-Services für die Komponente konfigurieren.

**Mehrere Musterseiten für Datensatzdokumente**
Jetzt können Sie für jede Seite eines Datensatzdokuments eine eigene Musterseite verwenden und die Platzierung von Bereichen in adaptiven Formularen mit Paginierungsoptionen steuern.

**Spalten zu Tabellen ohne Kopfzeile hinzufügen**
Sie können Spalten in Tabellen ohne Kopfzeile hinzufügen und löschen. Solchen Tabellen werden ausgeblendete Kopfzeilen hinzugefügt, was das Hinzufügen und Löschen von Spalten ermöglicht. Diese Kopfzeilen sind im Authoring-Modus sichtbar, bleiben aber im veröffentlichten Formular unsichtbar. Tabellen ohne Kopfzeile sind vor allem in adaptiven Formularen vorzufinden, die mithilfe der automatischen Formularumwandlung erstellt wurden.

**Verbesserte Aktionen zur Formularübermittlung**
Sie können die Aktion [E-Mail senden](configuring-submit-actions.md#send-email#send-email) verwenden, um ein Datensatzdokument (Document of Record, DoR) als Anhang im PDF-Format zu senden.

**Gruppen-E-Mail für Workflow**
Sie können aus dem Schritt „Aufgabe zuweisen“ heraus wahlweise an eine einzelne Person oder an eine Gruppe [Benachrichtigungs-E-Mails senden](aem-forms-workflow-step-reference.md#assign-task-step).

**Erweiterter Schritt zum Aufrufen des Formulardatenmodells**
Sie können jetzt den Ordnerpfad für die Option „Relativ zur Payload“ der Eingabeargumente in einem Schritt zum Aufrufen des Formulardatenmodells angeben. Dadurch wird es möglich, dem Eingabeargument eine Datei im angegebenen Ordner zuzuordnen, ohne den genauen Dateinamen anzugeben.

**Verbesserte Lesbarkeit von Übersetzungsdateien**
Bei Forms as a Cloud Service weisen die Leserichtung von Feldern und Bereichen eines adaptiven Formulars und die Nachrichtenschlüssel der zugehörigen Übersetzungsdateien (.XLIFF-Dateien) eine ähnliche Struktur auf. Dadurch werden manuelle Übersetzungen beschleunigt.

<!-- ## Feature comparison {#feature-comparison}

[!DNL AEM Forms] as a Cloud Service and [!DNL AEM 6.5 Forms] share some features like Adaptive Forms, Data Integration, and Forms Portal. You can easily port your existing Adaptive Forms from an [!DNL AEM 6.5 Forms] or an earlier version to [!DNL AEM Forms] as a Cloud Service.

### Features of [!DNL AEM 6.5 Forms] and [!DNL AEM Forms] as a Cloud Service {#aem-6.5-vs-aem-forms-as-a-cloud-service}

The following table lists the major features of [!DNL AEM 6.5 Forms] and provides information about the features coming soon to [!DNL AEM Forms] as a Cloud Service:

| Feature/Capability | AEM 6.5 Forms  | [!DNL AEM Forms] as a Cloud Service |
|---|---|---|
| Cloud-native architecture | &#x2612; | &#x2611;  |
| Auto-scaling based on load | &#x2612; | &#x2611;  |
| Zero downtime for upgrades | &#x2612; | &#x2611;  |
| Feature roll-out frequency | Quarterly | Agile*  |
| CDN (content delivery network) included | &#x2612; | &#x2611;  |
| Topologies optimized for maximum resilience and efficiency | &#x2612; | &#x2611;  |
| Cloud-native development environment | &#x2612; | &#x2611;  |
| Self-Service via Cloud Manager | &#x2612; | &#x2611;  |
| Automated upgrades with Continuous Integration and Continuous Delivery (CI/CD)| &#x2611; | &#x2611;  |
| Adaptive Forms | &#x2611; | &#x2611; |
| Data Integration | &#x2611; | &#x2611; |
| Automated Forms Conversion Service | &#x2611; | &#x2611; |
| Integration with [!DNL Adobe Sign] | &#x2611; | &#x2611; |
| Integration with [!DNL AEM Sites] | &#x2611; | &#x2611; |
| Enhanced Visual Rule editor | &#x2612; | &#x2611; |
| Forms Portal | &#x2611; | Coming Soon |
| Integration with [!DNL Adobe Analytics] | &#x2611; | Coming Soon |
| Integration with [!DNL Adobe Target] | &#x2611; | Coming Soon |
| Document Security | &#x2611; | &#x2612; |

`*` New features every month and bug fix updates on daily basis.

For a comprehensive list of changes in AEM as a Cloud Service, See [What is New and What is Different](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/overview/what-is-new-and-different.html) and [Notable changes in [!DNL AEM Forms] as a Cloud Service](notable-changes.md) -->
