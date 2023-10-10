---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 3fbdb150a9a1c133b4910603682e37f1c5d885d2
workflow-type: tm+mt
source-wordcount: '414'
ht-degree: 32%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 13804 {#release-13804}

Nachfolgend sind die kontinuierlichen Verbesserungen für das Maintenance Release 13804 zusammengefasst, das am 10. Oktober 2023 veröffentlicht wurde. Diese Wartungsversion ist eine Aktualisierung der vorherigen Wartungsversion 13665.

2023.10.0 Die Funktionsaktivierung stellt das vollständige Funktionssatz für dieses Maintenance Release bereit. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-13804}

* GRANITE-47238: Audit Log Maintenance - Purge cronjobs zur Verwendung der Kundenkonfiguration.
* GRANITE-47123: Veröffentlichen (Sling) - Verbessern Sie die Startzeit, indem Sie den Vanity-Pfad-Cache standardmäßig asynchron initialisieren.
* GRANITE-46618: Veröffentlichen (Replikation) - Verbessern Sie die Geschwindigkeit beim Start der Veröffentlichung durch die Stapelverarbeitung von Replikationsstatus-Meldungen.
* GRANITE-47136: Indizierung (Download) - Verbessern Sie die Download-Geschwindigkeit des neuen parallelen Index-Downloaders (durch Deaktivieren der Prüfsummenvalidierung).
* GRANITE-47211: Veröffentlichen (Infra) - Verbessern Sie die Entkopplung von Veröffentlichungsstufe-Bereitstellungen (durch Speichern und Abrufen des Segmentspeicherrevisionsnamens).
* GRANITE-47267: Update auf Apache Felix Http Jetty 4.2.18 (enthält Fehlerbehebung für die Verarbeitung von Anforderungsparametern ([FELIX-6625](https://issues.apache.org/jira/browse/FELIX-6625)) mit Leistungsverbesserungen für lokale und RDE-Entwicklungen).
* GRANITE-47247: Aktualisierung auf Sling Servlets Resolver 2.9.14 mit Leistungsverbesserungen bei der Servlet-Auflösung.

### Behobene Probleme {#fixed-issues-13804}

* GRANITE-47376: Autor (Infra) - Fehlerbehebung für DiscoveryTopologyUndefinierte Fehler nach rollierendem Neustart.
* CQ-4353436: AEM Web Console (Sling) - Leere Konfigurationen in ServiceUserMapperImpl Validators (Principal/User) unterbrechen AEM Instanz ([SLING-11912](https://issues.apache.org/jira/browse/SLING-11912)).
* SKYOPS-63925: Transform Job - Vermeiden von TransformJob-Fehlern mit JDK 11 - ZipException: Ungültige CEN-Kopfzeilenfehler (mit der JVM-Markierung disableZip64ExtraFieldValidation ).
* SKYOPS-63361: Vorgang (Protokollierung) umformen Verbesserte Protokollierung mit Umwandlungsaufträgen (Unterschritt CUSTOMER_EXTRACT ).
* SKYOPS-64103: FACT-Tool (Protokollierung) - Reduzieren oder Abschneiden von Kompilierungsfehlern und Warnmeldungen der Clientlib-Datei.
* SKYOPS-65109: FACT Tool (Error Handling) - Inhaltspakete mit nicht aufgelösten Abhängigkeiten führen zu einem ordnungsgemäß gemeldeten Fehler.
* SKYOPS-65368: FACT Tool (Error Handling) - Tool läuft in einen endlosen Einschlusszyklus und endet schließlich mit einer Zeitüberschreitung bei zirkulären Einbettungen von Clientlibs.
* SKYOPS-64031: RDE - ComponentCacheImpl kann aufgrund der doppelten Registrierung von ResourceResolverFactory ([SLING-12019](https://issues.apache.org/jira/browse/SLING-12019)).
* ASSETS-29105: RDE - Restriction provider missing from SecurityProviderRegistration requiredServicePids in RDE feature model.
* GRANITE-44674: CoralUI - Die erforderliche Feldfunktionalität für Datepicker ist nicht korrekt.

### Bekannte Probleme {#known-issues-13804}

Keine

### Eingebettete Technologien {#embedded-tech-13804}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.56-T20230927085643-189caed | [Oak-API 1.56.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.56.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
