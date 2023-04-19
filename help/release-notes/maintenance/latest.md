---
title: Aktuelle Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Versionshinweise zur Wartung [!DNL Adobe Experience Manager] as a Cloud Service.
source-git-commit: 4aa4954f214545dcd768fdf955f1fc2f776da939
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 17%

---


# Wartungsversionshinweise {#maintenance-release-notes}

Im folgenden Abschnitt finden Sie die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 11835 {#release-11835}

Nachfolgend sind die kontinuierlichen Verbesserungen für die Wartungsversion 11835 zusammengefasst, die am 19. April 2023 veröffentlicht wurde. Dieses Maintenance Release ist eine Aktualisierung von dem vorherigen Maintenance Release 11382.

Mit der Aktivierung der Funktionen für diese Wartungsversion steht Ihnen der volle Funktionsumfang zur Verfügung. Detaillierte Informationen finden Sie in den [aktuellen Versionshinweisen](/help/release-notes/release-notes-cloud/release-notes-current.md).

### Behobene Probleme {#fixed-issues-11835}

- SITES-12573 - GraphQL-Abfragen, die Variablen innerhalb eines Filters verwenden, schlagen fehl, wenn keine Variable angegeben ist. Bitte aktualisieren Sie nicht auf diese Version, sollten Sie GraphQL mit AEM as a Cloud Service verwenden.
- SKYOPS-51970 - Identifizierte Regression der im Schritt &quot;buildImage&quot;verwendeten FACT-Version, die zu einer nicht übereinstimmenden Benutzerzuordnung führte.
- GRANITE-44542 - Es wurden Probleme für Kunden gemeldet, die keinen Paketnotentyp (durch Bereitstellung einer .content.xml mit jcr:primaryType) für Ordner im Paketfilter angegeben haben. Dies führte dazu, dass diese Ordner als nt:folder behandelt wurden, was in verschiedenen Fällen zu Problemen führte.
- SKYOPS-56928 - Eine Apache HTTPD-Regression kann 404-Fehler verursachen. Wenn diese Probleme auftreten, wird aus Sicherheitsgründen empfohlen, zur vorherigen Version zurückzukehren und Pipeline zu vermeiden, die während dieses Zeitraums ausgeführt wird.

### Eingebettete Technologien {#embedded-tech-11835}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.44-T20221206170501-6d59064 | [Oak API 1.44.0 API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.44.0/index.html) |
| AEM SLING-API | Version: 2.27.0 | [Apache Sling API 2.27.0 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version 1.4.20-1.4.0 | [Sprachspezifikation für HTML-Vorlagen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.21.2 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
