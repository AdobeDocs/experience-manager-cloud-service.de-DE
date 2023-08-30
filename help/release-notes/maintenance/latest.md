---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: 22ed74b307b9eb4c6c2f72ac2a34e2ab6d30a85c
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 38%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 13239 {#release-13239}

Nachfolgend sind die kontinuierlichen Verbesserungen für die Wartungsversion 13239 zusammengefasst, die am 29. August 2023 veröffentlicht wurde. Dieses Maintenance Release ersetzt Version 13206.

2023.9.0 Die Funktionsaktivierung stellt den vollständigen Funktionsumfang für dieses Maintenance Release bereit. Siehe [Roadmap für Experience Manager-Versionen](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de) für weitere Informationen.

### Verbesserungen {#enhancements-13239}

- GRANITE-46784: Option hinzufügen, um BearerAuthenticationHandler zu deaktivieren
- GRANITE-36205: Aktualisieren der internen Oak-Version auf die neueste
- GRANITE-47059: Granite Jetty SSL Bundle entfernen
- ASSETS-26713: Externer Link zur Touch-optimierten Benutzeroberfläche zum Dashboard der neuen Experience UI - Unified-Shell-Integration und ui-touch-optimierte Aktualisierung
- SKYOPS-63302: Upgrade von com.adobe.granite:com.adobe.granite.auth.saml auf v1.0.54
- GRANITE-46634: Upgrade auf Eventing-Client 1.4.0
- GRANITE-46788: Aktualisieren der Apache Commons-Bibliotheken
- GRANITE-29211: Update-Tools für Sling Feature Model 2.0
- GRANITE-46705: Update auf Apache Felix HTTP Jetty 4.1.14
- GRANITE-46631: Jackrabbit-Version auf 2.20.11 aktualisieren
- SKYOPS-61895: Update auf Jackrabbit Filevault 3.7.0

### Behobene Probleme {#fixed-issues-13239}

- SKYOPS-63290: Fehlerhafte Evolution von Buckets behoben
- SKYOPS-54607: Die Berechnung des Ratelimiter-Servers für fehlgeschlagene Anfragen ist nicht korrekt
- ASSETS-27648: ContentModelIT kann Ausschlussdateien aus anderen Bundles nicht lesen
- GRANITE-43744: Sling Authenticator funktioniert nicht ordnungsgemäß, wenn eine Fehlkonfiguration mit Authentifizierungspflicht und Vanity-Pfad vorliegt
- GRANITE-46419: AEM Integrationsproblem mit Auth0 IPp
- GRANITE-46292: Okta-SAML-Konfiguration funktioniert nach AEM Cloud-Update nicht

### Bekannte Probleme {#known-issues-13239}

Keine

### Eingebettete Technologien {#embedded-tech-13239}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.54-T20230817132355-3800a65 | [Oak-API 1.54.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.54.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
