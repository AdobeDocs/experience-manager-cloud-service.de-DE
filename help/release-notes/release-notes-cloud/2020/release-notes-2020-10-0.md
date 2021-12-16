---
title: Versionshinweise für die Version 2020.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0
exl-id: ac741744-5b47-47a4-b5af-e1089e92c3f0
source-git-commit: 95ea603db207d93fa025a2ae20552f790b47f27c
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 60%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service 2020.10.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am 28. Oktober 2020 veröffentlicht.
Die folgende Version (2020.11.0) wird am 1. Dezember 2020 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* **[Kernkomponenten 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)**: Adobe Experience Manager as a Cloud Service profitiert von automatischen Aktualisierungen bis zur neuesten Version der Kernkomponenten. Version 2.12.0 enthält die neuesten Verbesserungen der Community. Zu den Verbesserungen gehören [einen neuen POST-Formular-Handler;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html?lang=de#post-data) Möglichkeit, benutzerdefinierte CSS-, JavaScript- und Metadaten einzuschließen [Tags über eine kontextbezogene Konfiguration;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html?lang=de#context-aware-loading) und [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html?lang=de#enabling-custom-components) -Dienstprogramm zur Vereinfachung der Adobe Data Layer-Integration in benutzerdefinierten Komponenten. Siehe die [Liste der Änderungen](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) in 2.12.0.

* **[Projektarchetyp 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)**: Die empfohlene Grundlage für den Start eines neuen Experience Manager-Projekts wurde besser. Er enthält jetzt die neue [Adobe Client-Datenschicht](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=de), Option [Site in AMP bereitstellen,](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html?lang=de) und neue [Erweiterungspunkte zum Hinzufügen von Projekt-CSS/JS.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[ContextHub-Ordner](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)**: Möglichkeit zur Erstellung von Zielgruppenordnern zur einfachen Organisation, Suche und Auswahl von Zielgruppensegmenten zur Verwendung für die Targeting-Funktionen von ContextHub-Angeboten.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

* **[!DNL Adobe Sensei]Powered Video Smart Tagging**: Durch Anwendung von KI-Modellen zur Analyse von Videoinhalten für objektspezifische und aktionsspezifische Tags können DAM-Benutzer weniger Zeit mit dem Hinzufügen von Tags und mehr Zeit mit den bereitgestellten, umfassenden Informationen verbringen. Sie liefern den Kunden das richtige Erlebnis. Siehe [Tagging von Video-Assets mit Smart-Tags](/help/assets/smart-tags-video-assets.md).

* **Brand Portal-Verbesserungen**: In [!DNL Brand Portal] sind u. a die nachfolgend aufgeführten neuen Funktionen verfügbar. Weitere Details finden Sie in den [[!DNL Brand Portal] Versionshinweisen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html?lang=de).

   * [Verbessertes Download-Erlebnis](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html?lang=de) mit einfacheren, schnellen Downloads. Administratoren können zusätzliche Download-Konfigurationen vornehmen, um ein Erlebnis zu bieten, das den Anforderungen der Anwender und Unternehmen entspricht.
   * Die Navigation zu Dateien, [Sammlungen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/share/brand-portal-share-collection.html?lang=de) und geteilten Links ist jetzt von jeder Seite aus möglich.
   * Anwender können jetzt [bestimmte Ausgabedarstellungen auswählen und herunterladen](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html?lang=de#download-assets-from-asset-details-page). Die neue Option zum Herunterladen der Ausgabedarstellung ist auf der Seite mit den Asset-Details im Bedienfeld „Ausgabedarstellung“ verfügbar.
   * Eine Zeitüberschreitung von 15 Minuten für Anwendersitzungen gewährleistet ein besseres Anwendererlebnis für alle gleichzeitigen Anwender.

* **[!DNL Adobe Asset Link]Version 2.1**: Es ist eine neue Version der [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/using/manage-assets-using-adobe-asset-link.html)-Erweiterung für [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] und [!DNL Adobe InDesign] verfügbar. Sie sorgt für Kompatibilität der neuesten [!DNL Adobe Creative Cloud]-Programme mit Version 2021, die im Oktober 2020 veröffentlicht wurde.

* **[!DNL Assets]WebP-Dateiunterstützung**: [!DNL Assets] as a Cloud Service unterstützt jetzt das WebP-Bildformat. WebP ist ein neues Bildformat, das von Google entwickelt wurde. Bilder im WebP-Dateiformat sind visuell nicht von JPG- oder PNG-Dateien zu unterscheiden und die Dateien sind viel kleiner. Die geringere Dateigröße von Assets verbessert die Seitenladezeit und hilft Inhaltserstellern, ein schnelleres Web-Erlebnis zu erzielen. Erfahren Sie, wie Sie WebP beim [Erstellen von Verarbeitungsprofilen](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile) verwenden.

## [!DNL Adobe Experience Manager Forms] as a Cloud Service {#forms-oct-2021}

### Neue Funktionen in [!DNL Forms] {#what-is-new-forms-oct-2021}

* **Analytics für adaptive Forms**: Sie können jetzt über Adobe Analytics für Adaptive Forms das Verhalten sowohl angemeldeter als auch nicht angemeldeter Benutzer (anonym) erfassen und verfolgen, um Einblicke von Endbenutzern zu sammeln. Dies hilft Benutzern aus Unternehmen, fundierte Entscheidungen über Inhalt, Layout und Stil adaptiver Formulare basierend auf den gesammelten Einblicken zu treffen.

### Neue Funktionen in [!DNL Forms] im Kanal für die Vorabversion {#prerelease-features-forms-oct-2021}

* **Externalisieren AEM Workflow-Daten für eine sichere Verarbeitung**: Sie können Daten von Workflow-Variablen, die vertrauliche personenbezogene Daten (EPPD) enthalten, AEM in einem kundenverwalteten Repository speichern, um sie sicher zu verarbeiten. Bei der Verarbeitung des Workflows werden die in Workflow-Variablen gespeicherten Daten nicht in AEM Repository gespeichert. Sie wird bei Bedarf aus dem kundenverwalteten Repository abgerufen.

### Beta-Funktionen von [!DNL Forms] {#sep-what-is-new-forms-oct-prerelease}

* **[!DNL AEM Forms as a Cloud Service - Communications]**: [Kommunikations-APIs](https://experienceleague.adobe.com/docs/experience-manager-forms-cloud-service/forms/aem-forms-cloud-service-communications.html?lang=de) hilft Ihnen, eine Vorlage und XML-Daten zu kombinieren, um Dokumente in verschiedenen Formaten zu generieren. Mit dem Dienst können Sie Dokumente im synchronen Modus und im Batch-Modus generieren.

Sie können an [!DNL formscsbeta@adobe.com] schreiben, um sich für das Beta-Programm anzumelden.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Freigabe der CIF Venia-Referenz-Website 2020.10.2, die die aktuelle CIF-Kernkomponenten Version 1.4.0 enthält. Weitere Informationen finden Sie unter [CIF Venia-Referenz-Website](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2).

* Version 1.4.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0).

### Fehlerbehebungen {#bug-fixes-commerce}

* GraphQL-Anfragen, die sich in der Produktkonsole und in Pickern befanden, wurden über HTTP-POST durchgeführt. Dieses Problem wurde behoben, um sicherzustellen, dass der Apollo GraphQL-Client die Einstellung in der GraphQL-Client-OSGi-Konfiguration respektiert, um GET-Anfragen zu unterstützen, sofern konfiguriert.

* In der Benutzeroberfläche der CIF-Cloud-Konfiguration wurden Schaltflächen zum Speichern und Schließen für Konfigurationen in „/lib“ und „/apps/“ angezeigt. Diese Schnittstellen sind jedoch schreibgeschützt, weshalb die Benutzeroberfläche so eingestellt ist, dass nur die Schaltfläche &quot;Schließen&quot;angezeigt wird.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Cloud Manager -Version as a Cloud Service 2020.10.0 in Experience Manager wurde am Donnerstag, 2. Oktober 2020 veröffentlicht.

### Neue Funktionen in [!DNL Cloud Manager] {#what-is-new-cm}

* Die Seite „Umgebungen“ wurde neu gestaltet.

* Im Ruhezustand befindliche Umgebungen verfügen jetzt über einen separaten Status.

* Der &quot;Build-Container&quot;von Cloud Manager unterstützt jetzt das Kompilieren von Projekten mit Java™ 8 oder Java™ 11. Unterstützung für Java™ 11 wird vom Maven-Toolchain-System bereitgestellt.

* Die Anzahl der Umgebungsvariablen pro Umgebung wurde auf 200 erhöht.

* Auf der Umgebungskarte auf der Übersichtsseite werden jetzt bis zu drei Umgebungen aufgelistet. Die Benutzer können die Schaltfläche **Alle anzeigen** auswählen, um zur Zusammenfassungsseite „Umgebung“ zu navigieren und eine Tabelle mit einer vollständigen Liste der Umgebungen anzeigen.
Weitere Informationen finden Sie unter [Anzeigen von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Verknüpfung von Cloud Manager mit der Developer Console war vor der vollständigen Erstellung der Umgebung nicht korrekt aktiviert.

* Die Verknüpfung zur Developer Console direkt aus Cloud Manager zeigte die Option zum Versetzen der Umgebung eines Sandbox-Programms in den Ruhezustand und zum Aufheben des Ruhezustands nicht an.

* Die Schaltflächen „Abbrechen“ und „Speichern“ auf der Seite „Bearbeiten“ für produktionsfremde Pipelines waren nicht immer sichtbar.

* Bestimmte Fehler im Code-Qualitätsprozess konnten dazu führen, dass die Protokolldatei nicht korrekt erzeugt wurde.

* Beim Erstellen eines Programms gibt der vorgeschlagene Name manchmal ein Duplikat eines vorhandenen Programmnamens zurück.

* Protokolle für bestimmte größere Pipeline-Schritte konnten nicht über die gesamte Benutzeroberfläche konsistent heruntergeladen werden.

* Bei der Validierung von Umgebungsnamen trat ein Fehler mit einer Verschiebung um den Wert eins auf.

* Auf der Seite Umgebungen wurden manchmal Veröffentlichungs- und Dispatcher-Segmente angezeigt, wenn keine vorhanden waren.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Es wurde Unterstützung für die Suche nach Workflow-Instanzen basierend auf Workflow-Titel, Workflow-Modell, Status, Initiator, Payload-Pfad und Startdatum hinzugefügt. Weitere Informationen finden Sie unter [Nach Workflow-Instanzen suchen](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/administering/workflows-administering.html?lang=de).

## Content Transfer Tool {#content-transfer-tool}

Erfahren Sie mehr über die neuen Funktionen und Updates für [Content Transfer Tool](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html?lang=de) Version 1.1.12.

### Neue Funktionen {#what-is-new-ctt}

* Anwendererlebnis für Protokolle verbessert. Zeitstempel zu Extraktions- und Aufnahmeprotokollen hinzugefügt. Meldung hinzugefügt, die angibt, ob Protokolle leer sind.

### Fehlerbehebungen {#ctt-bug-fixes}

* Das Content Transfer Tool hat Inhaltsdateien übersprungen, wenn der Migrationssatz Pfade mit teilweise ähnlichen Dateinamen enthielt.
