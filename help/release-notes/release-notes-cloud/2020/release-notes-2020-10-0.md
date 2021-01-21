---
title: Versionshinweise für die Version 2020.10.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0
translation-type: tm+mt
source-git-commit: 13774cc8684166c98f85bf4096d2c7de8d257746
workflow-type: tm+mt
source-wordcount: '1044'
ht-degree: 24%

---


# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.10.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für [!DNL Experience Manager] as a Cloud Service 2020.10.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Das Veröffentlichungsdatum für [!DNL Adobe Experience Manager] als Cloud Service 2020.10.0 ist der 28. Oktober 2020.
Die folgende Version (2020.11.0) wird am 1. Dezember 2020 veröffentlicht.

## [!DNL Adobe Experience Manager Sites] as a Cloud Service {#sites}

### Neue Funktionen in [!DNL Sites] {#what-is-new-sites}

* **[Hauptkomponenten 2.12.0](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)**: AEM als Cloud Service profitieren von automatischen Aktualisierungen der neuesten Version der Kernkomponenten. Version 2.12.0 enthält die neuesten, von der Community hinzugefügten Verbesserungen, wie [ein neuer POST-Formularhandler;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/forms/form-container.html#post-data) die Möglichkeit, benutzerdefinierte CSS-, JavaScript- und Metadaten [Tags über eine kontextabhängige Konfiguration einzuschließen;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading) und ein [`DataLayerBuilder`-Dienstprogramm zur Vereinfachung der Integration von Adobe Data Layer in benutzerdefinierte Komponenten. ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/integrations.html#enabling-custom-components) Siehe [Liste der Änderungen](https://github.com/adobe/aem-core-wcm-components/releases/tag/core.wcm.components.reactor-2.12.0) in 2.12.0.

* **[Projekttyp 24](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html)**: Die empfohlene Grundlage für den Beginn eines neuen AEM-Projekts wurde verbessert, jetzt einschließlich der neuen  [Adobe Client Data Layer](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html), der Option zur  [Bereitstellung der Site in AMP ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html) und neuer  [Erweiterungspunkte zum Hinzufügen von Projekt-CSS/JS.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/including-clientlibs.html#context-aware-loading)

* **[ContextHub-Ordner](/help/sites-cloud/authoring/personalization/contexthub-segmentation.md#organizing-segments)**: Möglichkeit zum Erstellen von Audiencen-Ordnern zur einfachen Organisation, Suche und Auswahl von Audiencen-Segmenten, die für ContextHub-Angebot-Targeting-Funktionen verwendet werden.

## [!DNL Adobe Experience Manager Assets] als Cloud Service  {#assets}

* **[!DNL Adobe Sensei]Powered Video Smart Tagging**: Durch die Nutzung von AI-Modellen zur Analyse von Videoinhalten für objektspezifische und aktionsspezifische Tags können DAM-Benutzer weniger Zeit damit verbringen, Tags hinzuzufügen, und mehr Zeit damit verbringen, die umfangreichen Informationen zu nutzen, um Kunden das richtige Erlebnis zu bieten. Siehe [Smart-Tag-Video-Assets](/help/assets/smart-tags-video-assets.md).

* **Markenportal-Verbesserungen**: Die folgenden neuen Funktionen und mehr sind in verfügbar  [!DNL Brand Portal]. Weitere Details finden Sie in den [[!DNL Brand Portal] Versionshinweisen](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/introduction/brand-portal-release-notes.html).

   * [Verbesserte Download-](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html) Erfahrung für vereinfachte und schnelle Downloads. Zusätzliche Download-Konfigurationen können von Administratoren konfiguriert werden, um ein Erlebnis Angebot, das den Anforderungen der Benutzer und Unternehmen entspricht.
   * Die Navigation zu Dateien, Sammlungen](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/share/brand-portal-share-collection.html) und Freigegebene Links ist jetzt von jeder Seite aus möglich.[
   * Benutzer können jetzt bestimmte Darstellungen [auswählen und herunterladen. ](https://docs.adobe.com/content/help/en/experience-manager-brand-portal/using/download/brand-portal-download-assets.html#download-assets-from-asset-details-page) Die neue Option zum Herunterladen der Darstellung ist im Bedienfeld &quot;Darstellungen&quot;auf der Seite &quot;Asset-Details&quot;verfügbar.
   * Eine Zeitüberschreitung von 15 Minuten für Benutzersitzungen gewährleistet eine bessere Benutzererfahrung für alle gleichzeitigen Benutzer.

* **[!DNL Adobe Asset Link]Version 2.1**: Eine neue Version der Asset- [Erweiterung der ](https://helpx.adobe.com/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) Adobe für  [!DNL Adobe Photoshop],  [!DNL Adobe Illustrator]und  [!DNL Adobe InDesign] ist verfügbar. Es fügt Kompatibilität mit den neuesten [!DNL Adobe Creative Cloud] Anwendungen mit Version 2021, veröffentlicht im Oktober 2020.

* **[!DNL Assets]WebP-Dateiunterstützung**:  [!DNL Assets] als Cloud Service unterstützt jetzt das WebP-Bildformat. WebP ist ein aufstrebendes Bildformat, das von Google erstellt wurde. Bilder im WebP-Dateiformat sind visuell nicht von JPG- oder PNG-Dateien zu unterscheiden und die Dateien sind viel kleiner. Die geringere Dateigröße von Assets verbessert die Seitenladezeit und hilft Inhaltserstellern, eine schnellere Web-Erfahrung zu erzielen. Erfahren Sie, wie Sie WebP in [Verarbeitungs-Profil](/help/assets/asset-microservices-configure-and-use.md#create-standard-profile) erstellen.

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

* CIF-Referenzseite Venia - 2020.10.2, die die aktuellste CIF-Kernkomponenten Version v1.4.0 enthält. Weitere Informationen finden Sie unter [CIF Venia Reference Site](https://github.com/adobe/aem-cif-guides-venia/releases/tag/venia-2020.10.2).

* Version 1.4.0 von CIF-Kernkomponenten veröffentlicht. Weitere Informationen finden Sie unter [CIF-Kernkomponenten](https://github.com/adobe/aem-core-cif-components/releases/tag/core-cif-components-reactor-1.4.0).

### Fehlerbehebungen {#bug-fixes-commerce}

* GraphQL-Anfragen in der Produktkonsole und Picker wurden über HTTP-POST durchgeführt. Dieser Fehler wurde behoben, um sicherzustellen, dass der Apollo GraphQL-Client die Einstellung in der GraphQL Client OSGi-Konfiguration respektiert, um GET-Anfragen zu unterstützen, falls konfiguriert.

* In der Benutzeroberfläche der CIF Cloud-Konfiguration wurden Schaltflächen zum Speichern und Schließen für Konfigurationen in /lib und /apps/ angezeigt. Diese sind jedoch schreibgeschützt und daher wurde die Benutzeroberfläche so eingestellt, dass nur die Schaltfläche &quot;Schließen&quot;angezeigt wird.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Das Veröffentlichungsdatum für Cloud Manager in AEM als Cloud Service 2020.10.0 ist der 02. Oktober 2020.

### Neue Funktionen in [!DNL Cloud Manager] {#what-is-new-cm}

* Die Seite &quot;Umgebung&quot;wurde neu gestaltet.

* Im Ruhezustand befindliche Umgebungen verfügen jetzt über einen separaten Status.

* Der Cloud Manager Build Container unterstützt jetzt das Kompilieren von Projekten mit Java 8 oder Java 11. Java 11 wird vom Maven Toolchain-System unterstützt.

* Die Anzahl der Umgebungsvariablen pro Umgebung wurde auf 200 erhöht.

* Die Umgebung auf der Übersichtsseite wird jetzt bis zu drei Umgebung Liste. Die Benutzer können die Schaltfläche **Alle anzeigen** auswählen, um zur Zusammenfassungsseite der Umgebung zu navigieren und eine Tabelle mit einer vollständigen Liste von Umgebung Ansicht.
Weitere Informationen finden Sie unter [Umgebung anzeigen](/help/implementing/cloud-manager/manage-environments.md#viewing-environment).

### Fehlerbehebungen {#bug-fixes-cloud-manager}

* Die Verknüpfung von Cloud Manager mit der Developer Console war vor der vollständigen Erstellung der Umgebung nicht korrekt aktiviert.

* Die Verknüpfung zur Developer Console direkt aus Cloud Manager zeigte die Option zum Versetzen der Umgebung eines Sandbox-Programms in den Ruhezustand und zum Aufheben des Ruhezustands nicht an.

* Die Schaltflächen &quot;Abbrechen&quot;und &quot;Speichern&quot;auf der Seite &quot;Bearbeiten in der Nicht-Produktionsumgebung&quot;waren nicht immer sichtbar.

* Bestimmte Fehler im Code-Qualitätsprozess konnten dazu führen, dass die Protokolldatei nicht korrekt erzeugt wurde.

* Beim Erstellen eines neuen Programms gab der vorgeschlagene Name manchmal ein Duplikat eines vorhandenen Programmnamens zurück.

* Protokolle für bestimmte größere Pipeline-Schritte konnten nicht über die gesamte Benutzeroberfläche konsistent heruntergeladen werden.

* Bei der Validierung von Umgebungsnamen trat ein Fehler mit einer Verschiebung um den Wert eins auf.

* Auf der Seite „Umgebungen“ wurden manchmal Veröffentlichungs- und Dispatcher-Segmente angezeigt, wenn keine vorhanden waren.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-service-foundation}

### Workflows {#workflows}

* Es wurde Unterstützung für die Suche von Workflow-Instanzen auf Grundlage von Workflow-Titel, Workflow-Modell, Status, Initiator, Nutzlastpfad und Beginn-Datum hinzugefügt. Siehe [Instanzen des Sucharbeitsablaufs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/administering/workflows-administering.html).

## Content Transfer-Tool {#content-transfer-tool}

Folgen Sie diesem Abschnitt, um mehr über die neuen Funktionen und die Aktualisierungen für [Content Transfer Tool](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/moving/cloud-migration/content-transfer-tool/overview-content-transfer-tool.html) Release v1.1.12 zu erfahren.

### Neue Funktionen {#what-is-new-ctt}

* Benutzerfreundlichkeit für Protokolle verbessert. Zeitstempel zu Extraktionen- und Ingestion-Protokollen hinzugefügt. Meldung hinzugefügt, die angibt, ob die Protokolle leer sind.

### Fehlerbehebungen {#ctt-bug-fixes}

* Content Transfer Tool übersprungen Inhaltsdateien, wenn der Migrationssatz Pfade mit teilweise ähnlichen Dateinamen enthielt. Das wurde behoben.
