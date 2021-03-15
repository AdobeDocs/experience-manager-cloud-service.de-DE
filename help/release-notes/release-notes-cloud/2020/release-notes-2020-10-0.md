---
title: Versionshinweise für die Version 2020.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0
translation-type: tm+mt
source-git-commit: 13774cc8684166c98f85bf4096d2c7de8d257746
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 100%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service 2020.10.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service wurde am 28. Oktober 2020 veröffentlicht.
Die folgende Version (2020.11.0) wird am 1. Dezember 2020 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* **[Version 2.12.0 der Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de)**: AEM as a Cloud Service profitiert von automatischen Aktualisierungen der neuesten Version der Kernkomponenten. Version 2.12.0 enthält die neuesten, von der Community beigetragenen Verbesserungen. Dazu zählen [ein neuer POST-Formular-Handler](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html?lang=de#post-data), die Möglichkeit, benutzerdefinierte CSS-, JavaScript- und [Metadaten-Tags über eine kontextbezogene Konfiguration einzubinden](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html?lang=de#context-aware-loading) und ein [`DataLayerBuilder`](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html?lang=de#enabling-custom-components)-Service-Programm zur Vereinfachung der Adobe Datenschicht-Integration in benutzerdefinierte Komponenten. Siehe die [Liste der Änderungen](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) in 2.12.0.

* **[Projektarchetyp 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)**: Das empfohlene Fundament für ein neues AEM-Projekts wurde verbessert, jetzt einschließlich der neuen [Adobe-Client-Datenschicht](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=de), der Option zur [Bereitstellung der Site in AMP](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html?lang=de) und neuer [Erweiterungspunkte zum Hinzufügen von Projekt-CSS/JS.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[ContextHub-Ordner](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)**: Möglichkeit zum Erstellen von Zielgruppenordnern zur einfachen Organisation, Suche und Auswahl von Zielgruppensegmenten, die für Funktionen zum Targeting von ContextHub-Angeboten verwendet werden.

## [!DNL Adobe Experience Manager Assets] als Cloud Service  {#assets}

* **[!DNL Adobe Sensei]-basierte Funktion für das Tagging von Videos**: Durch die Nutzung von KI-Modellen zur Analyse von Videoinhalten für objekt- und aktionsspezifische Tags verbringen DAM-Anwender weniger Zeit mit dem Hinzufügen von Tags und haben mehr Zeit, die umfangreichen Informationen zu verwerten, um dem Kunden das passende Erlebnis zu bieten. Siehe [Tagging von Video-Assets mit Smart-Tags](/help/assets/smart-tags-video-assets.md).

* **Brand Portal-Verbesserungen**: In [!DNL Brand Portal] sind u. a die nachfolgend aufgeführten neuen Funktionen verfügbar. Weitere Details finden Sie in den [[!DNL Brand Portal] Versionshinweisen](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [Verbessertes Download-Erlebnis](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) mit einfacheren, schnellen Downloads. Administratoren können zusätzliche Download-Konfigurationen vornehmen, um ein Erlebnis zu bieten, das den Anforderungen der Anwender und Unternehmen entspricht.
   * Die Navigation zu Dateien, [Sammlungen](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/share/brand-portal-share-collection.html) und geteilten Links ist jetzt von jeder Seite aus möglich.
   * Anwender können jetzt [bestimmte Ausgabedarstellungen auswählen und herunterladen](https://docs.adobe.com/content/help/de-DE/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page). Die neue Option zum Herunterladen der Ausgabedarstellung ist auf der Seite mit den Asset-Details im Bedienfeld „Ausgabedarstellung“ verfügbar.
   * Eine Zeitüberschreitung von 15 Minuten für Anwendersitzungen gewährleistet ein besseres Anwendererlebnis für alle gleichzeitigen Anwender.

* **[!DNL Adobe Asset Link]Version 2.1**: Es ist eine neue Version der [Adobe Asset Link](https://helpx.adobe.com/de/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html)-Erweiterung für [!DNL Adobe Photoshop], [!DNL Adobe Illustrator] und [!DNL Adobe InDesign] verfügbar. Sie sorgt für Kompatibilität der neuesten [!DNL Adobe Creative Cloud]-Programme mit Version 2021, die im Oktober 2020 veröffentlicht wurde.

* **[!DNL Assets]WebP-Dateiunterstützung**: [!DNL Assets] as a Cloud Service unterstützt jetzt das WebP-Bildformat. WebP ist ein neues Bildformat, das von Google entwickelt wurde. Bilder im WebP-Dateiformat sind visuell nicht von JPG- oder PNG-Dateien zu unterscheiden und die Dateien sind viel kleiner. Die geringere Dateigröße von Assets verbessert die Seitenladezeit und hilft Inhaltserstellern, ein schnelleres Web-Erlebnis zu erzielen. Erfahren Sie, wie Sie WebP beim [Erstellen von Verarbeitungsprofilen](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile) verwenden.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* Version 2020.10.2 der CIF-Venia-Referenz-Website veröffentlicht, die die neueste Version (1.4.0.) der CIF-Kernkomponenten umfasst. Weitere Informationen finden Sie unter [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2).

* Version 1.4.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0).

### Fehlerbehebungen {#bug-fixes-commerce}

* GraphQL-Anfragen in der Produkt-Konsole und in Auswahlen wurden über HTTP-POST durchgeführt. Dieser Fehler wurde behoben, um sicherzustellen, dass der Apollo GraphQL-Client die Einstellung in der GraphQL-Client-OSGi-Konfiguration berücksichtigt, um GET-Anfragen zu unterstützen, falls konfiguriert.

* In der Benutzeroberfläche der CIF-Cloud-Konfiguration wurden Schaltflächen zum Speichern und Schließen für Konfigurationen in „/lib“ und „/apps/“ angezeigt. Diese sind jedoch schreibgeschützt und daher wurde die Benutzeroberfläche nun so eingestellt, dass nur die Schaltfläche „Schließen“ angezeigt wird.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Das Veröffentlichungsdatum von Cloud Manager in AEM as a Cloud Service Version 2020.10.0 ist der 2. Oktober 2020.

### Neue Funktionen in [!DNL Cloud Manager] {#what-is-new-cm}

* Die Seite „Umgebungen“ wurde neu gestaltet.

* Im Ruhezustand befindliche Umgebungen verfügen jetzt über einen separaten Status.

* Der Cloud Manager-Build-Container unterstützt jetzt die Kompilierung von Projekten mit Java 8 und Java 11. Die Unterstützung für Java 11 wird durch das Maven Toolchains-System bereitgestellt.

* Die Anzahl der Umgebungsvariablen pro Umgebung wurde auf 200 erhöht.

* Die Umgebungskarte auf der Übersichtsseite listet jetzt bis zu drei Umgebungen auf. Die Benutzer können die Schaltfläche **Alle anzeigen** auswählen, um zur Zusammenfassungsseite „Umgebung“ zu navigieren und eine Tabelle mit einer vollständigen Liste der Umgebungen anzeigen.
Weitere Informationen finden Sie unter [Anzeigen von Umgebungen](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Verknüpfung von Cloud Manager mit der Developer Console war vor der vollständigen Erstellung der Umgebung nicht korrekt aktiviert.

* Die Verknüpfung zur Developer Console direkt aus Cloud Manager zeigte die Option zum Versetzen der Umgebung eines Sandbox-Programms in den Ruhezustand und zum Aufheben des Ruhezustands nicht an.

* Die Schaltflächen „Abbrechen“ und „Speichern“ auf der Seite „Bearbeiten“ für produktionsfremde Pipelines waren nicht immer sichtbar.

* Bestimmte Fehler im Code-Qualitätsprozess konnten dazu führen, dass die Protokolldatei nicht korrekt erzeugt wurde.

* Beim Erstellen eines neuen Programms gab der vorgeschlagene Name manchmal ein Duplikat eines vorhandenen Programmnamens zurück.

* Protokolle für bestimmte größere Pipeline-Schritte konnten nicht über die gesamte Benutzeroberfläche konsistent heruntergeladen werden.

* Bei der Validierung von Umgebungsnamen trat ein Fehler mit einer Verschiebung um den Wert eins auf.

* Auf der Seite „Umgebungen“ wurden manchmal Veröffentlichungs- und Dispatcher-Segmente angezeigt, wenn keine vorhanden waren.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Es wurde Unterstützung für die Suche nach Workflow-Instanzen basierend auf Workflow-Titel, Workflow-Modell, Status, Initiator, Payload-Pfad und Startdatum hinzugefügt. Siehe [Suchen nach Workflow-Instanzen](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/sites/administering/workflows-administering.html).

## Content Transfer Tool {#content-transfer-tool}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und Updates für [Content Transfer Tool](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Version 1.1.12.

### Neue Funktionen {#what-is-new-ctt}

* Anwendererlebnis für Protokolle verbessert. Zeitstempel zu Extraktions- und Aufnahmeprotokollen hinzugefügt. Meldung hinzugefügt, die angibt, ob Protokolle leer sind.

### Fehlerbehebungen {#ctt-bug-fixes}

* Das Content Transfer Tool übersprang Inhaltsdateien, wenn der Migrationssatz Pfade enthielt, die teilweise ähnliche Dateinamen hatten. Dieses Problem wurde behoben.
