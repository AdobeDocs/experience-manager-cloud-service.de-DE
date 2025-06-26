---
title: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service.
mini-toc-levels: 1
exl-id: a2d56721-502c-4f4e-9b72-5ca790df75c5
feature: Release Information
role: Admin
source-git-commit: 75816f35a8bca8356e17b13341c2ddbd850f8eff
workflow-type: tm+mt
source-wordcount: '2077'
ht-degree: 95%

---

# Aktuelle Versionshinweise für [!DNL Adobe Experience Manager] as a Cloud Service {#release-notes}

Im folgenden Abschnitt werden die allgemeinen Versionshinweise für die aktuelle (neueste) Version von [!DNL Experience Manager] as a Cloud Service beschrieben.

>[!NOTE]
>
>Von hier aus können Sie zu den Versionshinweisen früherer Versionen wie 2023 oder 2024 navigieren.
>
>Sehen Sie sich die [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap) an, um mehr über die bevorstehenden Funktionsaktivierungen für [!DNL Experience Manager] as a Cloud Service zu erfahren.

>[!NOTE]
>
>Abonnieren Sie [Adobe Priority Product Update](https://www.adobe.com/subscription/priority-product-update.html), wenn Sie monatliche E-Mail-Benachrichtigungen über Aktualisierungen der Experience Cloud-Versionshinweise erhalten möchten.

## Veröffentlichungsdatum {#release-date}


Das Veröffentlichungsdatum der aktuellen Version von [!DNL Adobe Experience Manager] as a [!DNL Cloud Service] (2025.5.0) war der 5. Juni 2025. Die nächste Version (2025.6.0) ist für 26. Juni 2025 geplant.

## Wartungsversionshinweise {#maintenance}

Die neuesten Wartungsversionshinweise finden Sie [hier](/help/release-notes/maintenance/latest.md).

<!-- 

## Release Video {#release-video}

Have a look at the February 2025 Release Overview video for a summary of the features added in the 2025.2.0 release:

>[!VIDEO](https://video.tv.adobe.com/v/3440929?quality=12&captions=ger)

-->

## [!DNL Experience Manager Assets] as a [!DNL Cloud Service] {#assets}

**KI-generierte Metadaten**

AEM Assets verwendet jetzt [KI zum automatischen Generieren von Metadaten, einschließlich Titel, Beschreibung und Keywords](/help/assets/metadata-assets-view.md#ai-smart-tags). Diese KI-generierten Felder verbessern die Genauigkeit von Metadaten und erleichtern die Suche, Kategorisierung und Empfehlung von Assets. Dieser Ansatz verbessert nicht nur die Effizienz durch die Eliminierung des manuellen Taggings, sondern stellt auch Konsistenz und Skalierbarkeit über große Mengen digitaler Inhalte hinweg sicher.

![KI-generierte Metadaten](/help/assets/assets/enhanced-smart-tags.png)

**Integration mit Figma**

Dank der nativen Integration von AEM Assets mit Figma können Sie über die Figma-Benutzeroberfläche direkt auf die in AEM Assets gespeicherten Assets zugreifen. Sie können in AEM Assets verwaltete Inhalte in der Figma-Arbeitsfläche platzieren und dann neue oder bearbeitete Inhalte im AEM Assets-Repository speichern. Um auf den AEM Assets Connector zuzugreifen, der auf der Figma Community-Seite verfügbar ist, klicken Sie [hier](https://www.figma.com/community/plugin/1512561378275712210/adobe-experience-manager-aem-assets-connector).

>[!VIDEO](https://video.tv.adobe.com/v/3463828)


### Neue Funktionen in Content Hub {#new-features-content-hub}

**Attributbasierte Zugriffssteuerung (Attribute-based Access Control, ABAC)**

[Mit Content Hub können Sie jetzt regelbasierte Einschränkungen für den Zugriff auf Assets anwenden](/help/assets/attribute-based-access-control.md). Asset-Berechtigungen gewährleisten die Governance und stellen außerdem sicher, dass nur die relevanten Assets für Benutzende zugänglich sind.

Die Regeln für die Asset-Einschränkung basieren auf Metadaten. Wenn die Asset-Metadaten den in der Regel definierten Bedingungen entsprechen, wird das Asset den Benutzergruppen angezeigt.

Zu den wichtigsten Vorteilen der attributbasierten Zugriffssteuerung gehören:

* Beseitigt die Abhängigkeit von der Ordnerstruktur für Berechtigungen

* Ermöglicht es Admins, Assets hochzuladen und Berechtigungsstrukturen rückwirkend zu bestimmen

* Reduziert die Anzahl der Duplikate – verbessert die Integrität der Assets. Duplikate sind in ordnerbasierten Berechtigungen erforderlich, wenn dieselben Assets für verschiedene Gruppen freigegeben werden.

**UI-Branding**

Content Hub ermöglicht es Admins jetzt, [die Benutzeroberfläche mit markenspezifischen Elementen anzupassen](/help/assets/configure-content-hub-ui-options.md##configure-branding-content-hub), einschließlich Bannerbildern, Bannertiteln und des Textkörpers sowie Primär- und Sekundärfarben. Diese Verbesserungen tragen dazu bei, Markenkonsistenz zu gewährleisten, das Onboarding von Benutzenden zu vereinfachen und Vertrauen aufzubauen.

![UI-Branding](/help/assets/assets/content-hub-ui-branding.png)

**Öffentliche Link-Freigabe**

Content Hub unterstützt jetzt das [Generieren von freigabefähigen Links, damit externe Benutzende](/help/assets/share-assets-content-hub.md##share-assets) ohne Programmzugriff Asset-Metadaten anzeigen oder Assets herunterladen können.

![UI-Branding](/help/assets/assets/public-and-private-link.png)

**Governance von Sammlungen**

Mit Content Hub können Sie jetzt [den Zugriff auf Sammlungen während der Erstellung steuern, sodass sichergestellt wird, dass nur autorisierte Benutzende gruppierte Assets anzeigen oder verwalten können](/help/assets/collections-content-hub.md##create-collections). Dies sorgt für verbesserte Sicherheit, eine bessere Zusammenarbeit, ein organisiertes Asset-Management und eine vereinfachte Governance.

>[!VIDEO](https://video.tv.adobe.com/v/3463336)

>[!NOTE]
>
>Die Governance von Sammlungen ist eine Funktion mit begrenzter Verfügbarkeit. Sie können sie aktivieren lassen, indem Sie ein Support-Ticket erstellen.

**Mehrere Assets als ZIP-Datei herunterladen**

Mit Content Hub können Sie jetzt auch [die ausgewählten Assets und ihre Ausgabedarstellungen in einer ZIP-Datei herunterladen](/help/assets/download-assets-content-hub.md#download-asset-renditions) und nicht als separate Dateien, was die Dateiverwaltung für Sie vereinfacht.

**Dynamic Media-Ausgabedarstellungen in Content Hub**

Greifen Sie [direkt über die Benutzeroberfläche von Content Hub auf alle voreingestellten Dynamic Media-Ausgabedarstellungen und smarten Zuschnitte zum Herunterladen zu](/help/assets/download-assets-content-hub.md#download-asset-renditions).

![Dynamic Media-Ausgabedarstellungen](/help/assets/assets/dm-renditions-content-hub.png)

### Neue Funktionen in Dynamic Media {#new-features-dynamic-media}

**Native Dynamic Media-Integration mit AJO B2C**

[Native Integration von Experience Manager (AEM) Dynamic Media mit Journey Optimizer (AJO) B2C](https://experienceleague.adobe.com/de/docs/journey-optimizer/using/content-management/combine/aem-dynamic), sodass Marketing-Fachleute AEM Dynamic Media-Assets (Ausgabedarstellung und DM-Vorlage) einfach in AJO-Inhalte einbetten und kanalübergreifend Echtzeit-Updates sowie extrem personalisierte Erlebnisse bereitstellen können.

>[!VIDEO](https://video.tv.adobe.com/v/3463791/?learn=on&enablevpops=&autoplay=true&captions=ger)

## [!DNL Experience Manager Forms] as a [!DNL Cloud Service] {#forms}

### Funktionen der Vorabversion

* [Universeller Editor – Formularfragmente](/help/edge/docs/forms/universal-editor/creating-form-fragments.md): Mit dem universellen Editor können Sie jetzt Formularfragmente für adaptive Formulare erstellen und wiederverwenden. Bei diesen Fragmenten handelt es sich um wiederverwendbare Formularabschnitte (z. B. Kontaktdaten, Einverständnisfelder), die einmal erstellt und auf mehrere Formulare angewendet werden können. Diese Funktion optimiert die Formularerstellung, stellt Konsistenz sicher und verbessert die Effizienz bei der Bearbeitung.

* [SharePoint-Dokumentbibliothek – Anhänge mit Originaldateinamen speichern](/help/forms/connect-forms-to-sharepoint-document-library.md#connect-an-adaptive-form-to-microsoft-sharepoint-document-library): Sie haben jetzt die Möglichkeit, Formularanhänge unter Verwendung ihrer Originaldateinamen zu speichern, wenn Sie sie in einer SharePoint-Dokumentbibliothek speichern. Diese Verbesserung vereinfacht die Identifizierung und Verwaltung hochgeladener Dateien.

* **Regeleditor**:
   * [Binäre Bedingung mit Klickereignis in der Wenn-Klausel](/help/forms/rule-editor-core-components-events-operators.md#available-operator-types-and-events-in-rule-editor): Der Regeleditor ermöglicht jetzt die Kombination eines Schaltflächen-Klickereignisses (_Wird angeklickt_) mit anderen Bedingungen innerhalb der Wenn-Klausel. Dies ermöglicht eine präzisere Kontrolle der Regelausführung basierend auf der Benutzerinteraktion und anderen Faktoren. Hinweis: Bei Verwendung mehrerer Bedingungen muss das Klickereignis die erste aufgeführte Bedingung sein.
   * [Validierungsbedingungen für Felder und Bereiche](/help/forms/rule-editor-core-components-usecases.md): Der Regeleditor enthält jetzt die Bedingungen _IsValid_ und _IsNotValid_. Damit können Sie den Validierungsstatus bestimmter Felder oder ganzer Bedienfelder (einschließlich Layouts wie horizontale Registerkarten, vertikale Registerkarten, Akkordeons und Assistenten) überprüfen und die Formularnavigation und das Benutzererlebnis auf der Grundlage der Validierungsergebnisse verbessern.
* [Verbesserte Verwaltung des SharePoint-Listenumfangs](/help/forms/connect-forms-to-sharepoint-list.md): SharePoint-Sites unterstützen jetzt alle verwalteten Pfade, z. B. /sites und /teams. Diese Verbesserung ermöglicht eine breitere Integration über verschiedene Site-Strukturen von SharePoint hinweg und bietet mehr Flexibilität bei der Verbindung mit organisatorischen Inhalten.
* [Unterstützung für das Speichern des Datensatzdokuments in der SharePoint-Liste](/help/forms/generate-document-of-record-core-components.md#bind-adaptive-form-components-with-template-fields): Formulare, die mit einem auf SharePoint-Listen basierenden Formulardatenmodell (FDM) erstellt wurden, können jetzt den Nachweis (DoR) in SharePoint-Listen speichern, indem die Feldeigenschaft „Bindungsverweis für Nachweis“ konfiguriert wird. Diese Verbesserung ermöglicht die nahtlose Integration unterstützter Formulardaten und Dokumente mit dem SharePoint-Speicher.

### Early-Access-Funktionen in AEM Forms {#forms-new-early-access-features}

Das Early-Access-Programm von AEM Forms bietet Ihnen die einmalige Möglichkeit, einen exklusiven Zugang zu den aktuellen Innovationen zu erhalten und ihre Entwicklung mitzugestalten.

In diesen Versionshinweisen werden die in der aktuellen Version bereitgestellten Innovationen aufgeführt. Eine vollständige Liste der im Rahmen des Early-Access-Programms verfügbaren Innovationen finden Sie in der [Dokumentation zum AEM Forms-Early-Access-Programm](/help/forms/early-access-ea-features.md).

#### Integration von Adobe Experience Platform (AEP) mit Forms

Integrationsfunktionen zwischen Forms und AEP sind jetzt für Early Adopters verfügbar.

## [!DNL Experience Manager] as a [!DNL Cloud Service] als Fundament {#foundation}

### Aktualisierter Prozess zur Abschaffung {#updated-deprecation-process}

Adobe überprüft regelmäßig Funktionen, Bibliotheken, APIs und Konfigurationen, um sicherzustellen, dass sie den Leistungs-, Sicherheits- und Wertstandards entsprechen. Wenn Funktionen diese Standards nicht mehr erfüllen, werden sie als veraltet gekennzeichnet, und ihre Verwendung muss bis zu einem bestimmten Entfernungsdatum eingestellt werden. Bis zu diesem Datum erinnert Adobe die Kundinnen und Kunden mit E-Mail-Benachrichtigungen und Aktionen, die in Cloud Manager durchgeführt werden müssen, bevor sie mit neuen Builds fortfahren oder welche bereitstellen. Wenn die erforderlichen Maßnahmen nicht ergriffen werden, kann es passieren, dass ein Upgrade auf neue Versionen von AEM nicht möglich ist, was sich auf Sicherheit, Leistung, Zuverlässigkeit und Verfügbarkeit auswirken kann.

Weitere Informationen finden Sie im Artikel zur [Abschaffung](/help/release-notes/deprecated-removed-features.md).

#### Veraltete Java-APIs und OSGi-Konfigurationen, deren Entfernungsdatum sich nähert {#deprecated-near-removals}

Erweitern Sie die unten stehende Liste, um die veralteten APIs und OSGi-Konfigurationen anzuzeigen, die nicht mehr verwendet werden dürfen. Ausführliche Informationen, einschließlich der Zeitpläne für die Entfernung, finden Sie im Artikel zur Abschaffung.

<details>
  <summary>Erweitern Sie die Liste, um die veralteten Versionen anzuzeigen</summary>

Jav-APIs:
* `org.apache.sling.commons.auth`
* `org.apache.felix.webconsole`
* `org.eclipse.jetty`
* `com.mongodb`
* `org.apache.abdera`
* `org.apache.felix.http.whiteboard`
* `org.apache.cocoon.xml`
* `ch.qos.logback`
* `org.slf4j.spi`
* `org.slf4j.event`
* `org.apache.log4j`
* `com.google.common`
* `com.drew`
* `org.bson`
* `org.apache.jackrabbit.oak.plugins.blob`
* `org.apache.jackrabbit.oak.plugins.memory`

OSGi-Eigenschaften:

* `org.apache.sling.commons.log.LogManager` (alle Eigenschaften)
* `org.apache.sling.commons.log.LogManager.factory.config` (`org.apache.sling.commons.log.file`, `org.apache.sling.commons.log.pattern`)

</details>

### Abschaffung der Java 11-Laufzeit {#java11-runtime-deprecation}

Die **Java 11-Laufzeitumgebung** ist jetzt veraltet, und die meisten Umgebungen wurden bereits auf die leistungsfähigere **Java 21-Laufzeitumgebung** aktualisiert.

Wenn Ihre Umgebung aufgrund nicht unterstützter Abhängigkeiten nicht aktualisiert werden konnte (siehe [Java 21-Laufzeitanforderungen](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#runtime-requirements)), sollten Sie eine E-Mail von Adobe mit bestimmten nächsten Schritten erhalten haben. Bitte stellen Sie sicher, dass alle erforderlichen Aktualisierungen bis zum **28. August 2025** abgeschlossen sind, damit Ihre Umgebung unterbrechungsfrei aktualisiert werden kann.

Hinweis: Die Laufzeitversion ist von der Build-Version Ihres Codes getrennt. Es wird zwar empfohlen, Builds mit Java 21 durchzuführen, aber Java 11-Builds werden derzeit noch unterstützt. Ein separater Hinweis zur Abschaffung von Java 11 für Builds wird in Zukunft freigegeben.

### Durchsetzung der Konfigurationsrichtlinie für AEM-Java-Protokolle {#logconfig-policy}

Wie in den Versionshinweisen vom April erwähnt, müssen AEM-Java-Protokolle einem Standardformat entsprechen, um eine zuverlässige Überwachung in allen Kundenumgebungen sicherzustellen. Benutzerdefinierte Protokollkonfigurationen – wie etwa Änderungen an der Protokollformatierung, Ausgabedateien oder Standardprotokollebenen – werden nicht mehr unterstützt. Protokolle müssen an die Standarddateien weitergeleitet werden, und die standardmäßigen Protokollebenen für AEM-Produkt-Code müssen beibehalten werden. Ausführliche Informationen finden Sie im [Artikel zur Protokollierung](/help/implementing/developing/introduction/logging.md#configuration-loggers).

Ab **Ende August** werden alle nicht unterstützten benutzerdefinierten Protokollierungsüberschreibungen ignoriert. Nach unserer Analyse ist der Großteil der Kundschaft nicht betroffen, und Adobe wird sich direkt mit allen Kundinnen und Kunden in Verbindung setzen, deren aktuelle Konfiguration möglicherweise betroffen ist.

Bitte überprüfen und aktualisieren Sie alle nachgelagerten Prozesse, die auf einem benutzerdefinierten Protokollierungsverhalten basieren. Zum Beispiel:

* Wenn Ihr Protokollweiterleitungssystem ein benutzerdefiniertes Protokollformat erwartet, müssen Sie möglicherweise Ihre Aufnahmeregeln anpassen.
* Wenn Sie zuvor die Ausführlichkeit des Protokolls durch Ändern der Protokollebenen reduziert haben, beachten Sie, dass eine Rückkehr zu den Standardebenen das Protokollvolumen erhöhen kann.

### Standardmäßige Bereinigung älterer Versionen und Auditprotokolle {#mt-defaults}

Derzeit sind die zugehörigen *Bereinigungs-Wartungsaufgaben“ für Inhaltsversionen* Auditprotokolle standardmäßig deaktiviert, sodass keine Daten entfernt werden, es sei denn, diese sind explizit konfiguriert.

Um jedoch die Repository-Leistung zu optimieren, wird die Bereinigung ab **Ende Juni 2025** standardmäßig aktiviert, wobei die folgenden Richtlinien befolgt werden:

#### Inhaltsversionen {#mt-content}

* **Neue Umgebungen** (erstellt nach einem bevorstehenden Datum, das später mitgeteilt wird)
   * Versionen, die älter als **30 Tage** sind, werden regelmäßig gelöscht.
   * Die letzten fünf Versionen der letzten 30 Tage werden zusammen mit der neuesten Version und der aktuellen Version unabhängig von deren Alter beibehalten.

* **Vorhandene Umgebungen** (vor diesem bevorstehenden Datum erstellt):
   * Versionen, die älter als **7 Jahre** sind, werden regelmäßig gelöscht.
   * Alle Versionen der letzten 7 Jahre werden beibehalten.
   * Dieser hohe Standardschwellenwert verhindert ein unbeabsichtigtes Entfernen aktueller Daten. Es wird jedoch empfohlen, niedrigere Werte zu konfigurieren, um die Repository-Leistung zu optimieren.

* Sie können diese Standardwerte über die YAML-Konfiguration ändern, die mithilfe der Konfigurations-Pipeline bereitgestellt wird.

#### Auditprotokoll {#mt-auditlogs}

* **Neue Umgebungen** (erstellt nach einem bevorstehenden Datum, das separat kommuniziert wird):
   * Replikations-, DAM-und Seiten-Auditprotokolle, die älter als **7 Tage** sind, werden regelmäßig gelöscht.
   * Alle Ereignisse werden standardmäßig protokolliert.

* **Vorhandene Umgebungen** (vor diesem bevorstehenden Datum erstellt):
   * Replikations-, DAM-und Seiten-Auditprotokolle, die älter als **7 Jahre** sind, werden regelmäßig gelöscht.
   * Alle Ereignisse werden standardmäßig protokolliert.
   * Dieser hohe Standardschwellenwert verhindert ein unbeabsichtigtes Entfernen aktueller Daten. Es wird jedoch empfohlen, niedrigere Werte zu konfigurieren, um die Repository-Leistung zu optimieren.

* Sie können diese Standardwerte über die YAML-Konfiguration ändern, die mithilfe der Konfigurations-Pipeline bereitgestellt wird.

Weitere Details finden Sie im [Artikel zu Wartungsaufgaben](/help/operations/maintenance.md#defaults).

### Edge-Datenverarbeitung (Alpha-Programm) {#edge-computing}

Mit der Edge-Datenverarbeitung können Sie JavaScript auf CDN-Ebene ausführen, wodurch die Datenverarbeitung näher an die Endbenutzenden heranrückt. Dies reduziert die Latenz und ermöglicht responsive, dynamische Erlebnisse am Edge.

Häufige Anwendungsszenarien umfassen:

* Authentifizieren von Benutzenden bei einem Identitätsanbieter, bevor Zugriff auf Inhalte gewährt wird
* Personalisieren von Inhalten basierend auf Geolokalisierung, Gerätetyp oder Benutzerattributen
* Fungieren als Middleware zwischen dem CDN und Ihrer Herkunft
* Umformatieren von Antworten aus APIs von Drittanbietern (und möglicherweise Aggregieren mehrerer APIs als Antworten), bevor sie an den Browser gesendet werden
* Erstellen und Bereitstellen von Server-gerenderter HTML am Edge mithilfe von Inhalten, die aus verschiedenen Backends zusammengefügt wurden

Wir haben nur eine begrenzte Anzahl von Möglichkeiten für die AEM-Veröffentlichungsbereitstellung oder Edge Delivery Services-Projekte für Live-Produktions-Sites. Wenn Sie an einer Teilnahme interessiert sind oder mehr erfahren möchten, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com) mit einer kurzen Beschreibung Ihres Anwendungsfalls.

### CDN-Konfiguration für Edge Delivery Services (Beta-Programm) {#cdn-eds-beta}

Das von Adobe verwaltete CDN bietet flexible Konfigurationsoptionen, wie im Artikel zu [Konfigurations-Pipelines](/help/operations/config-pipeline.md#configurations) beschrieben.

Stellen Sie jetzt in der Beta-Phase eine Konfigurations-Pipeline für Funktionen bereit, einschließlich CDN-Ursprungs-Selektoren, Antwort- und Anfragetransformationen und mehr. Wenden Sie sich mit den Details Ihres Anwendungsfalls an [aemcs-cdn-config-adopter@adobe.com](mailto:aemcs-cdn-config-adopter@adobe.com).

### AEM-Protokollweiterleitung an weitere Ziele (Beta-Programm) {#log-forwarding-beta}

Die Protokolle können zwar von Cloud Manager heruntergeladen werden, aber viele Unternehmen ziehen es vor, diese Protokolle an ein bevorzugtes Protokollierungsziel weiterzuleiten. AEM unterstützt bereits die AEM- und CDN-Protokollweiterleitung an Azure Blob Storage, Datadog, HTTPS, Elasticsearch (und OpenSearch) und Splunk. Diese Funktion wird eigenständig konfiguriert und mithilfe der Konfigurations-Pipeline bereitgestellt.

Jetzt in der Beta-Phase können Sie AEM-Protokolle an Amazon S3, Sumo Logic und Ihr eigenes New Relic-Konto (nicht das von Adobe bereitgestellte Konto) weiterleiten. Beachten Sie, dass zwar AEM-Protokolle (einschließlich Apache/Dispatcher) für diese Protokollierungsziele unterstützt werden, jedoch keine CDN-Protokolle. Schreiben Sie eine E-Mail an [aemcs-logforwarding-beta@adobe.com](mailto:aemcs-logforwarding-beta@adobe.com), um Zugriff zu erhalten.

Weitere Informationen finden Sie in der [Dokumentation zur Protokollweiterleitung](/help/implementing/developing/introduction/log-forwarding.md).

## [!DNL Experience Manager] Guides {#guides}

Eine vollständige Liste der neuen und verbesserten Funktionen der neuesten Version der Adobe Experience Manager Guides finden Sie [hier](https://experienceleague.adobe.com/de/docs/experience-manager-guides/using/release-info/aem-guides-releases-roadmap).

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
