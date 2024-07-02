---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: 3a4dd9f1d769a9c9da12fdd8febfef481112d18c
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 79%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 16799 {#release-16799}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 16799, die am 18. Juni 2024 veröffentlicht wurde. Die vorherige Wartungsversion war Version 16544.

Die Funktionsaktivierung in 2024.6.0 bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/de/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap).

### Verbesserungen {#enhancements-16799}

* ASSETS-31977: Erweiterte Vorgänge zum Verschieben, Kopieren und Löschen von Assets.
* ASSETS-33618: Automatische Transkriptions- und Übersetzungsfunktion für Videos in Dynamic Media.
* ASSETS-35185: Genehmigungsaktion für ContentHub und DM und Hinzufügen von Eigenschaften zu damAssetLucene-Eigenschaften.
* ASSETS-35533: Hinzufügen von DRM- und CAI-Eigenschaften zum damAssetLucene-Index.
* ASSETS-37280: Sequenzielle Auftragsverarbeitung für die Übersetzung, wenn der Quelluntertitel (vtt) noch verarbeitet wird.
* ASSETS-37559: Verbessertes Ereignis des Löschens von Assets.
* ASSETS-37723: Implementieren des Ereignisses „Asset veröffentlicht“.
* ASSETS-37724: Implementieren des Ereignisses „Asset nicht veröffentlicht“.
* ASSETS-38614: Verbesserungen der Benutzeroberfläche zum Freigeben von Links.
* ASSETS-39601: Automatisches Anwenden der Validierungs-Regex auf den Asset-Livecopy-Namen.
* ASSETS-39454: Aktualisierung auf Viewer 2024.5.0 in Quickstart.
* CNTBF-184: Unterstützungspfade unter `/conf` im Inhaltsrückfluss.

### Behobene Probleme {#fixed-issues-16799}

* ASSETS-37335: Beim Bearbeiten des Bedienfelds „Suchen“ im Filter werden alle Felder deaktiviert.
* ASSETS-38069: Problem mit der AEM DAM-PDF-Vorschau bei der Auswahl des Zeitleistenfilters.
* ASSETS-38215: Die Schaltfläche „Adobe Stock-Lizenz“ wurde in AEM as a Cloud Service für Unternehmensabonnements ausgegraut.
* ASSETS-38578: Falsche Hyperlinks im Bericht zur Link-Freigabe für Assets.
* ASSETS-38678: Anzeigeeinstellungen in den Details zur Sammlung beschädigt.
* ASSETS-39071: Eine Web-optimierte Bereitstellung kann eine Ausnahme auslösen, wenn der MIME-Typ der ursprünglichen Ausgabedarstellung null ist.
* ASSETS-39316: Sortieren nach Namen funktioniert nicht in Sammlungen.
* ASSETS-39377: Massenimport von OneDrive schlägt möglicherweise fehl, wenn der Gegendruck von einer Remote-API empfangen wird.
* ASSETS-39428: Render-Probleme in der Benutzeroberfläche von Copyright-Management.
* CQ-4357150: Guava im cq-content-sync-Bundle.
* GRANITE-52573: Anfragen mit einem doppelten Schrägstrich `//` werden mit dem Status-Code 400 abgelehnt. 
* SCRNS-4194: Entfernen der Abhängigkeit von Google Guava-APIs.
* SCRNS-4360: Fehlende Schaltfläche „Veröffentlichung verwalten und Quick Publish“ für Benutzende ohne Administratorrechte im Inhaltsanbieter für Kanäle.
* SCRNS-4323: Ausblenden/Deaktivieren von Launches aus screens.html.

#### Forms

* FORMS-14844: Adaptive Forms ermöglicht die Übermittlung von Formularen trotz fehlerhafter reCAPTCHA-Überprüfung.
* FORMS-14984: Forms mit CAPTCHA überspringt die Validierung, wenn &quot;submitMetaData&quot;in den gesendeten Daten fehlt.
* FORMS-14477: Die Optionen &quot;Is After&quot;und &quot;Is Before&quot;im Regeleditor funktionieren bei der Datumsauswahl-Validierung nicht mehr.
* FORMS-14019: Die Funktion &quot;Dienst aufrufen&quot;des Regeleditors funktioniert nicht im universellen Editor.
* FORMS-14336: Wenn kein Formularfeld ausgewählt ist, sollte der Editor geöffnet werden und den Fokus auf das gesamte Formularelement legen.
* FORMS-15061: Der Kreis &quot;Lader&quot;bleibt bei Verwendung der Option &quot;Dienst aufrufen&quot;im Regeleditor auf unbestimmte Zeit bestehen.

### Bekannte Probleme {#known-issues-16799}

>[!NOTE]
> AEM Engineering hat eine Regression für die Funktionen von Launches identifiziert, die sich auf aktuelle AEM-Versionen ab 16461 auswirkt. Aufgrund dieser Regression werden neue Launches (die nach der Anwendung neuer Versionen erstellt wurden), die nicht-tiefe Seiten enthalten, aufgrund fehlender Konfigurationen nicht ordnungsgemäß weitergeleitet.
> Falls Ihre Umgebungen betroffen sind, ist über den Kunden-Support ein Shell-Skript erhältlich, mit dem fehlende Konfigurationen identifiziert und aktualisiert werden können (interne Referenz SITES-22457).
> Es wird eine längerfristige Korrektur bereitgestellt, die sicherstellt, dass neue Launches mit allen richtigen Konfigurationen erstellt werden. Bis dahin ist auf Anfrage auch eine interne Patch-Version verfügbar.

#### Forms

* Wenn Sie das AEM SDK installieren und hinzufügen `AEM Forms add-on v2024.05.04.00-240400`, kann der Docker-Dienst nicht gestartet werden. Der Docker-Dienst ist erforderlich, um das Datensatzdokument in einer lokalen Entwicklungsumgebung zu generieren. Beheben des Problems:
   1. Laden Sie die [Hotfix](/help/forms/assets/sdk_hotfix.zip). Wenn Sie den Hotfix herunterladen, wird ein `.zip` heruntergeladen werden.
   1. Extrahieren Sie den heruntergeladenen Hotfix in einen Ordner.
   1. Ältere ersetzen `sdk.sh` und `sdk.bat` Dateien mit neueren Dateien im Ordner, der in Schritt 2 extrahiert wurde.

### Änderungshinweis {#change-notice-16799}

* Diese Version enthält die folgenden neuen Produktindex-Versionen:
   * **damAssetLucene-11**
   * **fragments-11**

  Benutzerdefinierte Versionen der vorherigen Indexversionen werden automatisch mit der neuen Produktindex-Version zusammengeführt. Wenden Sie weitere benutzerdefinierte Aktualisierungen auf die zusammengeführte Version an.

* AEM as a Cloud Service deaktiviert ab September 2024 die Serialisierung von Ressourcen-Konfliktlösern über das Sling Model Exporter-Framework. Weitere Informationen finden Sie in der [Dokumentation](/help/implementing/developing/hybrid/disallow-the-serialization-of-resourceresolvers-via-sling-model-exporter.md).

### Eingestellte Funktionen und APIs {#deprecated-16799}

Informationen zu veralteten oder entfernten Elementen in AEM as a Cloud Service finden Sie unter [Eingestellte und entfernte Funktionen und APIs](/help/release-notes/deprecated-removed-features.md).

### Eingebettete Technologien {#embedded-tech-16799}

| Technologie | Version | Link |
|---|---|---|
| AEM Oak | 1.64.0 | [Oak-API 1.64.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.64.0/index.html) |
| AEM SLING-API | 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | 1.4.22–1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | 2.25.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
