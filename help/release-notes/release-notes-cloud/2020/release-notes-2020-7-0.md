---
title: Versionshinweise für Version 2020.7.0 von [!DNL Adobe Experience Manager] as a Cloud Service.
description: Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service für 2020.7.0.
exl-id: 75d354a3-6987-4de0-aec8-24043461c516
feature: Release Information
role: Admin
source-git-commit: 90f7f6209df5f837583a7225940a5984551f6622
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 93%

---

# Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service 2020.7.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.7.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

Die Version 2020.7.0 von [!DNL Experience Manager] as a Cloud Service wurde am 30. Juli 2020 veröffentlicht.

## Adobe Experience Manager Sites as a Cloud Service {#cloud-services-sites}

### Neue Funktionen {#what-is-new-sites}

[!DNL Experience Manager] as a Cloud Service-Connectoren für [!DNL Adobe Target] und [!DNL Adobe Analytics] wurden wie folgt verbessert:

* Eine neue Benutzeroberflächen-Implementierung ersetzt die auf der klassischen Benutzeroberfläche basierende Implementierung.

* Die Benutzeroberfläche weist vereinfachte Dialogfelder auf, sodass die Framework-Erstellung für Variablenzuordnung und andere Konfigurationen [!DNL Adobe Launch] überlassen wird. Siehe [Integrieren mit Adobe Analytics](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-analytics.html?lang=de) und [Integrieren mit Adobe Target](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/sites/integrations/integrating-adobe-target.html?lang=de).

* Konfigurationen werden jetzt in `/conf` statt in `/etc/cloudsettings` im Adobe Experience Manager-Repository gespeichert.

## [!DNL Adobe Experience Manager Assets] as a Cloud Service {#assets}

### Neue Funktionen in [!DNL Assets] {#what-is-new-assets}

* [!DNL Asset Compute Service] ist ein skalierbarer und erweiterbarer Service zur Verarbeitung von Assets. Administratoren können [!DNL Experience Manager] konfigurieren, um anwenderdefinierte Programme aufzurufen, die mit dem [!DNL Asset Compute Service] erstellt wurden. Entwickler können den Service verwenden, um spezielle anwenderdefinierte Programme zu erstellen, die sich für komplexe Anwendungsfälle eignen. Dieser Webservice kann Miniaturen für verschiedene Dateitypen und hochwertige Bilddarstellungen aus Adobe-Dateiformaten erstellen, Videos kodieren (künftig verfügbare Funktion), Metadaten und Volltext zur vorläufigen Indizierung extrahieren und Assets alle verfügbaren [!DNL Sensei]-Services durchlaufen lassen. Siehe [Verwenden von Asset-Microservices und Verarbeitungsprofilen](/help/assets/asset-microservices-configure-and-use.md).

* Die ursprüngliche Konfiguration von [!DNL Dynamic Media] in [!DNL Experience Manager] as a Cloud Service wurde verbessert, um sie stabiler zu machen. Sie informiert den Administratoren nun über den Fortschritt der Prozesse.

* Das Veröffentlichen von Assets in [!DNL Dynamic Media] wurde vereinfacht und stabiler gestaltet, indem es zu einem integralen Bestandteil der gesamten Asset-Verarbeitungs-Pipeline unter Verwendung von Asset-Microservices wird und das Backend bei der Batch-Veröffentlichung verbessert wird.

* Workflow-Schritte, die nicht mit einer Cloud Service-Bereitstellung kompatibel sind, werden jetzt im [!UICONTROL Workflow-Modell]-Editor mit einem Warnhinweis versehen. Außerdem werden beim Ausführen der vorhandenen Workflows in der Cloud Service-Umgebung die inkompatiblen Workflow-Schritte übersprungen.

* Von Kunden erstellte Workflow-Modelle, die in `/conf/global` im Git-Projekt bereitgestellten wurden, das der Umgebung in [!DNL Cloud Manager] zugeordnet ist, werden automatisch unter `/var` bereitgestellt und sind daher in [!DNL Experience Manager] verfügbar. Die Produkt-Workflow-Modelle unter `/libs`, an denen Kunden Änderungen vorgenommen haben, werden nicht automatisch in `/var` bereitgestellt.

### Fehlerbehebungen {#assets-bugs-fixed}

* Der Assistent zum Verschieben von Assets wird für die in Sammlungen enthaltenen Assets nicht wie erwartet geladen. (CQ-4296756)
* Die Werte von `dam:size` und `dam:sha1` sind von XMP Writeback ausgeschlossen. (CQ-4237355)
* Beim Aufheben der Veröffentlichung von Assets in Batches gibt [!DNL Brand Portal] einen Fehler aus, der darauf hindeutet, dass der Anfrage-URI zu lang ist. (CQ-4299474)

## Adobe Experience Manager Commerce as a Cloud Service {#cloud-services-commerce}

### Neue Funktionen {#what-is-new-commerce}

AEM Commerce ist jetzt in Cloud Service verfügbar.

Weitere [ finden Sie unter „Erste Schritte mit AEM Commerce as a Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/commerce/getting-started.html?lang=de)&quot;.

## Kernkomponenten {#core-components}

### Neue Funktionen {#what-is-new-core-components}

Version 2.11.0 der [AEM-Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de) ist jetzt als Teil von AEM Sites verfügbar, einschließlich folgenden Optionen:

* Einführung einer neuen [PDF-Viewer-Komponente](https://www.aemcomponents.dev/content/core-components-examples/library/core-content/pdf-viewer.html).

* Die Kernkomponenten unterstützen jetzt Accelerated Mobile Pages (AMP). Dies hilft, schnellere Kundenerlebnisse zu erzielen, indem Seitenübergänge sofort erfolgen, wenn die Site von einem Google Mobile-Suchergebnis aus aufgerufen wird, was zu Verbesserungen bei Anwenderinteraktionen und SEO führt.
Siehe [AMP-Unterstützung für die Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/amp.html?lang=de) für weitere Details.

* Kompatibilität mit Version 1.0.2 der [Adobe Client-Datenschicht](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/data-layer/overview.html?lang=de).

* Fehlerbehebungen und Qualitätsverbesserungen am Code.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die [!UICONTROL Cloud Manager]-Version 2020.7.0 wurde am 9. Juli 2020 veröffentlicht.

### Neue Funktionen {#what-is-new-cloud-manager}

* Die Seite „Umgebungen“ wurde neu gestaltet.

* Im Ruhezustand befindliche Umgebungen verfügen jetzt über einen separaten Status.

* Die Anzahl der Umgebungsvariablen pro Umgebung wurde auf 200 erhöht.

* Cloud Manager-Pipelines unterstützen jetzt anwenderspezifische Variablen und Geheimnisse.

  Weitere Details finden Sie unter „Pipeline-Variablen“.

* Authentifizierungsgebundene private Maven-Repositorys werden jetzt unterstützt.

* Der Cloud Manager-Build-Container unterstützt jetzt sowohl Java 8 als auch Java 11.
Weitere Details finden Sie unter „Verwenden von Java 11-Unterstützung“.

### Fehlerbehebungen {#bug-fixes-cm}

* Die Verknüpfung von Cloud Manager mit der Developer Console war vor der vollständigen Erstellung der Umgebung nicht korrekt aktiviert.

* Die Verknüpfung zur Developer Console direkt aus Cloud Manager zeigte die Option zum Versetzen der Umgebung eines Sandbox-Programms in den Ruhezustand und zum Aufheben des Ruhezustands nicht an.

* Die Optionen **Abbrechen** und **Speichern** auf der Seite „Bearbeiten“ für produktionsfremde Pipelines waren nicht immer sichtbar.

* Bestimmte Fehler im Code-Qualitätsprozess konnten dazu führen, dass die Protokolldatei nicht korrekt erzeugt wurde.

* Beim Erstellen eines neuen Programms gab der vorgeschlagene Name manchmal ein Duplikat eines vorhandenen Programmnamens zurück.

* Protokolle für bestimmte größere Pipeline-Schritte konnten nicht über die gesamte Benutzeroberfläche konsistent heruntergeladen werden.

* Bei der Validierung von Umgebungsnamen trat ein Fehler mit einer Verschiebung um den Wert eins auf.

* Auf der Seite „Umgebungen“ wurden manchmal Veröffentlichungs- und Dispatcher-Segmente angezeigt, wenn keine vorhanden waren.

### Bekannte Probleme {#known-issues}

* Aufgrund einer Änderung bei der Berechnung der Code-Abdeckung ist die erforderliche *Mindestversion* des Jacoco-Plugins jetzt 0.7.5.201505241946 (veröffentlicht im Mai 2015). Kunden, die eine ältere Version verwenden, erhalten eine Fehlermeldung im Code-Qualitätsprozess.

## Adobe Experience Manager as a Cloud Service Foundation {#cloud-foundation}

### Neue Funktionen {#what-is-new-foundations}

* [Protokolle können an Splunk-Konten weitergeleitet werden](/help/implementing/developing/introduction/logging.md#splunk-logs) wodurch Unternehmen ihre Splunk-Investition nutzen können.

* [Eine statische, dedizierte Ausgangs-IP-Adresse](/help/implementing/developing/introduction/development-guidelines.md#dedicated-egress-ip-address) kann für ausgehenden Traffic zugewiesen werden, der in Java-Code programmiert ist, was bei einigen Integrationen nützlich sein kann.

* Die Benutzeroberfläche von AEM Analytics Cloud Service wurde von der klassischen Benutzeroberfläche in die neue AEM-Benutzeroberfläche übertragen. Außerdem wurde der Speicherort von AEM Analytics Cloud Service im AEM-Repository von `/etc` in `/conf` in Abstimmung mit anderen AEM Cloud Services verschoben.

* Die Benutzeroberfläche von AEM Target Cloud Service wurde von der klassischen Benutzeroberfläche in die neue AEM-Benutzeroberfläche übertragen. Außerdem wurde der Speicherort des AEM Target Cloud Service im AEM-Repository von `/etc` in `/conf` in Abstimmung mit anderen AEM Cloud Services verschoben.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Readiness Analyzer Version 1.0.2.

### Fehlerbehebungen {#cra-bug-fixes}

* Frühere Versionen des CRA konnten nicht unter Adobe Experience Manager (AEM) 6.1 ausgeführt werden. Es wurde expliziter Support hinzugefügt, um Benutzer für die Administratorgruppe zuzulassen.

  Weitere [ finden Sie unter „Installieren von CRA ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html?lang=de#installing-on-aem61) AEM 6.1“.

* Der im Zusammenfassungsbericht angezeigte Ablaufzeitstempel war nicht korrekt.

* CRA erkannte doppelt vorhandene benutzerdefinierte Komponenten.

* Bei AEM 6.1 wurde die Inhaltsüberprüfung beendet, bevor die vollständige Überprüfung abgeschlossen wurde. Die Ausnahmebehandlung wurde hinzugefügt, damit der Inspektor die Prüfung überspringen und fortsetzen kann, bis die vollständige Überprüfung abgeschlossen ist.
