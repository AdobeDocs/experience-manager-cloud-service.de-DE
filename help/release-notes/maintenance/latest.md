---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
feature: Release Information
role: Admin
source-git-commit: fd687498a8c72bf5d47b7b97aadf22d7d1e8dd2b
workflow-type: tm+mt
source-wordcount: '649'
ht-degree: 91%

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

### Bekannte Probleme {#known-issues-16799}

>[!NOTE]
> AEM Engineering hat eine Regression für die Funktionen von Launches identifiziert, die sich auf aktuelle AEM-Versionen ab 16461 auswirkt. Aufgrund dieser Regression werden neue Launches (die nach der Anwendung neuer Versionen erstellt wurden), die nicht-tiefe Seiten enthalten, aufgrund fehlender Konfigurationen nicht ordnungsgemäß weitergeleitet.
> Falls Ihre Umgebungen betroffen sind, ist über den Kunden-Support ein Shell-Skript erhältlich, mit dem fehlende Konfigurationen identifiziert und aktualisiert werden können (interne Referenz SITES-22457).
> Es wird eine längerfristige Korrektur bereitgestellt, die sicherstellt, dass neue Launches mit allen richtigen Konfigurationen erstellt werden. Bis dahin ist auf Anfrage auch eine interne Patch-Version verfügbar.

#### Formulare

1. Wenn ein Benutzer die AEM Forms SDK-Version herunterlädt, die größer ist als `AEM Forms add-on v2024.05.04.00-240400`, kann die Batch-Datei den Docker-Dienst nicht starten. So beheben Sie dieses Problem:
   1. Laden Sie die [Ordner](/help/forms/assets/sdk_hotfix.zip).
   1. Extrahieren Sie den Inhalt aus dem heruntergeladenen Ordner und kopieren Sie den `sdk.sh` und `sdk.bat` -Dateien.
   1. Vorhandene ersetzen `sdk.sh` und `sdk.bat` -Dateien in Ihrem AEM Forms-SDK mit den neuen Dateien.

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
