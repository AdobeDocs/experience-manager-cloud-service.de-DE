---
title: Versionshinweise für die Version 2020.7.0 [!DNL Adobe Experience Manager] von als Cloud Service.
description: '[!DNL-Adobe Experience Manager] als Cloud Service-Versionshinweise für 2020.7.0.'
translation-type: tm+mt
source-git-commit: a454bcce2d4db89c0ac8dc27fd187a822bacf7e6
workflow-type: tm+mt
source-wordcount: '968'
ht-degree: 38%

---


# Release Notes for [!DNL Adobe Experience Manager] as a Cloud Service 2020.7.0 {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für Experience Manager as a Cloud Service 2020.7.0 beschrieben.

## Veröffentlichungsdatum {#release-date}

The release date for [!DNL Experience Manager] as a Cloud Service 2020.7.0 is July 30, 2020.

## Adobe Experience Manager Sites als Cloud Service {#cloud-services-sites}

### Neuerungen {#what-is-new-sites}

[!DNL Experience Manager] als Cloud Service-Connectors für [!DNL Adobe Target] und [!DNL Adobe Analytics] werden wie folgt verbessert:

* Eine neue Benutzeroberflächenimplementierung ersetzt die Implementierung auf der Grundlage der klassischen Benutzeroberfläche.

* Vereinfachte Dialogfelder der Benutzeroberfläche, sodass die Framework-Erstellung für Variablenzuordnung und andere Konfigurationen [!DNL Adobe Launch]bleibt. Siehe [Integration von Adobe Analytics](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/integrations/integrating-adobe-analytics.html) und [Integration von Adobe Target](https://docs.adobe.com/content/help/en/experience-manager-cloud-service/sites/integrations/integrating-adobe-target.html).

* Konfigurationen werden jetzt im Experience Manager-Repository gespeichert `/conf` und nicht `/etc/cloudsettings` im Repository.

## Adobe Experience Manager Assets as a Cloud Service {#assets}

>[!NOTE]
>AEM Assets als Cloud Service-Funktionen werden in den nächsten Tagen eingeführt.

### Neuerungen {#what-is-new-assets}

* [!DNL Asset Compute Service] ist ein skalierbarer und erweiterbarer Dienst zur Verarbeitung von Assets. Administratoren können Experience Manager so konfigurieren, dass benutzerdefinierter Worker aufgerufen wird, der mit dem [!DNL Asset Compute Service]erstellt wurde. Entwickler können den Dienst zum Erstellen spezieller, benutzerdefinierter Arbeiter verwenden, die komplexen Anwendungsfällen Rechnung tragen. Dieser Webdienst kann Miniaturansichten für verschiedene Dateitypen erstellen, hochwertige Bildwiedergaben aus Dateiformaten erstellen, Adoben kodieren (zukünftig), Metadaten extrahieren, Volltext als Vorläufer für die Indexierung extrahieren und ein Asset über alle verfügbaren Sensei-Dienste ausführen. Siehe [Verwenden von Asset-Mikrodiensten und Verarbeitungs-Profilen](/help/assets/asset-microservices-configure-and-use.md).

* Die anfängliche Konfiguration von [!DNL Dynamic Media] in [!DNL Experience Manager] als Cloud Service wurde verbessert, um robuster zu sein. Es stellt den Administratoren nun den Fortschritt der Prozesse zur Verfügung.

* Das Veröffentlichen von Assets zu [!DNL Dynamic Media] vereinfachen und robuster zu gestalten, indem es zu einem integralen Bestandteil der gesamten Asset-Verarbeitungspipeline unter Verwendung von Asset-Mikrodiensten wird und das Back-End bei der Veröffentlichung von Stapeln verbessert wird.

* Arbeitsablaufschritte, die nicht mit einer Cloud Service-Bereitstellung kompatibel sind, werden jetzt im [!UICONTROL Workflow-Modell] -Editor mit einer Warnmeldung versehen. Außerdem werden beim Ausführen der vorhandenen Workflows auf der Cloud Service-Umgebung die nicht kompatiblen Workflow-Schritte übersprungen.

* Arbeitsablaufmodelle, die von Kunden erstellt wurden, die im Git-Projekt bereitgestellt werden, das mit der Umgebung in Cloud Manager verknüpft ist, werden automatisch in Experience Manager bereitgestellt `/conf/global` `/var` und damit verfügbar gemacht. Die Produktarbeitsablaufmodelle, unter `/libs` denen der Kunde Änderungen vorgenommen hat, werden nicht automatisch bereitgestellt `/var`.

## Kernkomponenten {#core-components}

### Neuerungen {#what-is-new-core-components}

Release 2.11.0 of the [AEM Core Components](https://docs.adobe.com/content/help/de-DE/experience-manager-core-components/using/introduction.html) is now available as part of AEM Sites including:

* Einführung einer neuen [PDF Viewer-Komponente](https://aemcomponents.dev/content/core-components-examples/library/page-authoring/pdf-viewer.html).

* Die Accelerated Mobile Pages (AMP)-Unterstützung von Core-Komponenten ist jetzt verfügbar. Es hilft, schnellere Kundenerlebnisse zu erzielen, indem die Transition der Seite sofort erfolgt, wenn die Site von einem Google Mobile-Suchergebnis aus aufgerufen wird, was die Benutzerinteraktion und die SEO verbessert.
Weitere Informationen finden Sie unter [AMP-Unterstützung für die Kernkomponenten](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/amp.html) .

* Kompatibilität mit Version 1.0.2 der [Adobe Client Data Layer](https://docs.adobe.com/content/help/en/experience-manager-core-components/using/developing/data-layer/overview.html).

* Fehlerbehebungen und Verbesserungen der Codequalität.

## Cloud Manager {#cloud-manager}

### Veröffentlichungsdatum {#release-date-cm}

Die Version 2020.7.0 von [!UICONTROL Cloud Manager] wurde am 09. Juli 2020 veröffentlicht.

### Neuerungen {#what-is-new-cloud-manager}

* Die Seite „Umgebungen“ wurde neu gestaltet.

* Im Ruhezustand befindliche Umgebungen verfügen jetzt über einen separaten Status.

* Die Anzahl der Umgebungsvariablen pro Umgebung wurde auf 200 erhöht.

* Cloud Manager-Pipelines unterstützen jetzt benutzerspezifische Variablen und Geheimnisse.

   Weitere Informationen finden Sie unter [Pipeline-Variablen](/help/onboarding/getting-access-to-aem-in-cloud/creating-aem-application-project.md#pipeline-variables).

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

* Aufgrund einer Änderung bei der Berechnung der Code-Abdeckung ist die erforderliche *Mindestversion* des Jacoco-Plugins jetzt 0.7.5.201505241946 (veröffentlicht im Mai 2015). Kunden, die explizit auf eine ältere Version verweisen, erhalten eine Fehlermeldung im Code-Qualitätsprozess.


## Adobe Experience Manager as a Cloud Service Foundation {#cloud-foundation}

### Neuerungen {#what-is-new-foundations}

* [Protokolle können an Splunk-Konten](/help/implementing/developing/introduction/logging.md#splunk-logs)weitergeleitet werden, wodurch Organisationen ihre Splunk-Investitionen nutzen können.

* [Eine statische, dedizierte IP-Adresse](/help/implementing/developing/introduction/development-guidelines.md#dedicated-egress-ip-address) kann für ausgehenden Traffic zugewiesen werden, der in Java-Code programmiert ist, was bei einigen Integrationen nützlich sein kann.

* Die Benutzeroberfläche AEM Analytics Cloud-Dienstes wurde von der klassischen Benutzeroberfläche in die neue AEM Benutzeroberfläche hochgeladen. Außerdem wurde der Speicherort des Analytics Cloud-Dienstes in AEM Repository von `/etc` zu `/conf`verschieben, um ihn an andere AEM cloud services auszurichten.

* Die Benutzeroberfläche des AEM Cloud-Dienstes wurde von der klassischen Benutzeroberfläche in die neue AEM Benutzeroberfläche hochgeladen. Außerdem wurde der Speicherort des Zielgruppe Cloud-Dienstes in AEM Repository von `/etc` zu `/conf`verschieben, um ihn an andere AEM cloud services auszurichten.

## Cloud Readiness Analyzer {#cloud-readiness-analyzer}

In diesem Abschnitt erfahren Sie mehr über die neuen Funktionen und die Updates für Cloud Readiness Analyzer Version 1.0.2.

### Fehlerbehebungen {#cra-bug-fixes}

* Frühere Versionen des CRA konnten nicht unter Adobe Experience Manager (AEM) 6.1 ausgeführt werden. Es wurde expliziter Support hinzugefügt, um Benutzer für die Administratorgruppe zuzulassen.

   Weitere Informationen finden Sie unter [Installieren von CRA unter AEM 6.1](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/moving/cloud-migration/cloud-readiness-analyzer/using-cloud-readiness-analyzer.html#installing-on-aem61) .

* Der im Zusammenfassungsbericht angezeigte Ablaufzeitstempel war nicht korrekt.

* CRA erkannte doppelt vorhandene benutzerdefinierte Komponenten.

* Bei AEM 6.1 wurde die Inhaltsüberprüfung beendet, bevor die vollständige Überprüfung abgeschlossen wurde. Die Ausnahmebehandlung wurde hinzugefügt, damit der Inspektor die Prüfung überspringen und fortsetzen kann, bis die vollständige Überprüfung abgeschlossen ist.
