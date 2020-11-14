---
title: Current Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service.
description: Current Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service.
translation-type: tm+mt
source-git-commit: 4bce4fceab08a95fc2c1c8334f84fd54204228ba
workflow-type: tm+mt
source-wordcount: '886'
ht-degree: 4%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

The following section outlines the general Release Notes for [!DNL Experience Manager] as a Cloud Service.

## Veröffentlichungsdatum {#release-date}

The Release Date for [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 is October 28, 2020.
Die folgende Version (2020.11.0) wird am 1. Dezember 2020 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### What is new in [!DNL Sites] {#what-is-new-sites}

<!-- add when release done: * **Core Components 2.12.0**: With Core Components being on auto-update, benefit from the latest improvements contributed by the community. See list of changes since 2.11.1: Release Notes -->

* **Projekttyp 24**: Die empfohlene Grundlage für den Beginn eines neuen AEM-Projekts wurde verbessert, jetzt einschließlich der neuen Adobe Client Data Layer, Option zur Bereitstellung der Site in AMP und neue Erweiterungspunkte zum Hinzufügen von Projekt CSS/JS.

* **ContextHub-Ordner**: Möglichkeit zum Erstellen von Audiencen-Ordnern zur einfachen Organisation, Suche und Auswahl von Audiencen-Segmenten, die für ContextHub-Angebot-Targeting-Funktionen verwendet werden.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### What is new in [!DNL Assets] {#what-is-new-assets}

* **[!DNL Adobe Sensei]Powered Video Smart Tagging**: Durch die Nutzung von AI-Modellen zur Analyse von Videoinhalten für objektspezifische und aktionsspezifische Tags können DAM-Benutzer weniger Zeit damit verbringen, Tags hinzuzufügen, und mehr Zeit damit verbringen, die umfangreichen Informationen zu nutzen, um Kunden das richtige Erlebnis zu bieten. Siehe [Smart-Tag-Video-Assets](/help/assets/smart-tags-video-assets.md).

* **Markenportal-Verbesserungen**: Die folgenden neuen Funktionen und mehr sind in verfügbar [!DNL Brand Portal]. Weitere Details finden Sie in den [[!DNL Brand Portal] Versionshinweisen](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [Verbesserte Download-Erfahrung](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) für vereinfachte und schnelle Downloads. Zusätzliche Download-Konfigurationen können von Administratoren konfiguriert werden, um ein Erlebnis Angebot, das den Anforderungen der Benutzer und Unternehmen entspricht.
   * Die Navigation zu Dateien, [Sammlungen](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/share/brand-portal-share-collection.html)und freigegebenen Links mit einem Klick ist jetzt von jeder Seite aus möglich.
   * Benutzer können jetzt bestimmte Darstellungen [auswählen und herunterladen](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page) . Die neue Option zum Herunterladen der Darstellung ist im Bedienfeld &quot;Darstellungen&quot;auf der Seite &quot;Asset-Details&quot;verfügbar.
   * Eine Zeitüberschreitung von 15 Minuten für Benutzersitzungen gewährleistet eine bessere Benutzererfahrung für alle gleichzeitigen Benutzer.

* **[!DNL Adobe Asset Link]Version 2.1**: Eine neue Version der [Adobe Asset Link](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) -Erweiterung für [!DNL Adobe Photoshop], [!DNL Adobe Illustrator]und [!DNL Adobe InDesign] ist verfügbar. Es fügt Kompatibilität mit den neuesten [!DNL Adobe Creative Cloud] Anwendungen mit Version 2021, veröffentlicht im Oktober 2020.

* **[!DNL Assets]WebP-Dateiunterstützung**: [!DNL Assets] als Cloud Service unterstützt jetzt das WebP-Bildformat. WebP ist ein aufstrebendes Bildformat, das von Google erstellt wurde. Bilder im WebP-Dateiformat sind visuell nicht von JPG- oder PNG-Dateien zu unterscheiden und die Dateien sind viel kleiner. Die geringere Dateigröße von Assets verbessert die Seitenladezeit und hilft Inhaltserstellern, eine schnellere Web-Erfahrung zu erzielen. Siehe [Erstellen eines Standard-Profils](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile).

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* CIF-Referenzseite Venia - 2020.10.2, die die aktuellste CIF-Kernkomponenten Version v1.4.0 enthält. Weitere Informationen finden Sie auf der [CIF Venia-Referenzseite](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2) .

* Version 1.4.0 der CIF-Kernkomponenten Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0) .

### Fehlerbehebungen {#bug-fixes-commerce}

* GraphQL-Anfragen in der Produktkonsole und Picker wurden über HTTP-POST durchgeführt. Dieser Fehler wurde behoben, um sicherzustellen, dass der Apollo GraphQL-Client die Einstellung in der GraphQL Client OSGi-Konfiguration respektiert, um GET-Anfragen zu unterstützen, falls konfiguriert.

* In der Benutzeroberfläche der CIF Cloud-Konfiguration wurden Schaltflächen zum Speichern und Schließen für Konfigurationen in /lib und /apps/ angezeigt. Diese sind jedoch schreibgeschützt und daher wurde die Benutzeroberfläche so eingestellt, dass nur die Schaltfläche &quot;Schließen&quot;angezeigt wird.


## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.11.0 ist der 12. November 2020.

### What is new in [!DNL Cloud Manager] {#what-is-new-cm}

* Eine neue Menüoption **Lokale Anmeldung** steht nun den Benutzern über die Menüoptionen auf den Zusammenfassungsseiten für die **Umgebung** und **Umgebung** zur Verfügung.
Refer to [Managing Environments](/help/implementing/cloud-manager/manage-environments.md##login-locally) for more details.

* Die Registerkarte &quot; **Lernen** &quot;in Cloud Manager wurde mit neuen Bildern in der Benutzeroberfläche aktualisiert.

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Das Laden von Abhängigkeiten vor der Ausführung des Builds erforderte den Download eines Maven-Plugins.
* Über den Link in der Fußzeile von Cloud Manager zur Auswahl einer Sprache navigieren Sie jetzt zum richtigen Speicherort.
* Während der Codeprüfung wird der SonarQube-Vorgang manchmal nicht Beginn. Dies wird nun automatisch erkannt und ein Neustart wird versucht.
* Alle vorhandenen Produktionslinien werden automatisch mit dem Experience Audit-Schritt aktiviert.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Es wurde Unterstützung für die Suche von Workflow-Instanzen auf Grundlage von Workflow-Titel, Workflow-Modell, Status, Initiator, Nutzlastpfad und Beginn-Datum hinzugefügt. Siehe [Instanzen](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html)des Sucharbeitsablaufs.

## Content Transfer-Tool {#content-transfer-tool}

Follow this section to learn about what is new and the updates for [Content Transfer Tool](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12.

### Neue Funktionen {#what-is-new-ctt}

* Benutzerfreundlichkeit für Protokolle verbessert. Zeitstempel zu Extraktionen- und Ingestion-Protokollen hinzugefügt. Meldung hinzugefügt, die angibt, ob die Protokolle leer sind.

### Fehlerbehebungen {#ctt-bug-fixes}

* Content Transfer Tool übersprungen Inhaltsdateien, wenn der Migrationssatz Pfade mit teilweise ähnlichen Dateinamen enthielt. Das wurde behoben.

## Best Practices-Analyzer {#best-practices-analyzer}

### Veröffentlichungsdatum {#release-date-bpa}

Das Veröffentlichungsdatum für Best Practices Analyzer ist der 13. November 2020.

### What is new in [!DNL Best Practices Analyzer] {#what-is-new-bpa}

* Cloud Readiness Analyzer ist jetzt Best Practices Analyzer (BPA). BPA bietet eine Best Practices-Bewertung Ihrer aktuellen AEM-Implementierung und hilft bei der Beurteilung der Bereitschaft, von einer vorhandenen AEM zu AEM als Cloud Service zu wechseln.

* Es wurde ein neuer Detektor hinzugefügt, um die Verwendung von zu erkennen, `java.io.InputStream`die Probleme verursachen kann, wenn sie in AEM als Cloud Service verwendet werden.

### Fehlerbehebungen {#bpa-bug-fixes}

* Der Fehler, der die positiven Eigenschaften der *textfield-Foundation* -Komponente verursachte, wurde behoben.