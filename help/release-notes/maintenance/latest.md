---
title: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
description: Aktuelle Wartungsversionshinweise zu [!DNL Adobe Experience Manager] as a Cloud Service.
exl-id: eee42b4d-9206-4ebf-b88d-d8df14c46094
source-git-commit: dbdc63db9a9ac954ce6359d3643231d6e195fd53
workflow-type: tm+mt
source-wordcount: '302'
ht-degree: 65%

---

# Wartungsversionshinweise {#maintenance-release-notes}

Der folgende Abschnitt enthält die technischen Versionshinweise für die aktuelle Wartungsversion von Experience Manager as a Cloud Service.

## Version 15575 {#release-15575}

Im Folgenden finden Sie die kontinuierlichen Verbesserungen für die Wartungsversion 15575, die am  Mittwoch, 19. März 2024 veröffentlicht wurde. Das vorherige Wartungsversion war Version 15262.

2024.3.0: Die Funktionsaktivierung bietet den vollen Funktionsumfang für diese Wartungsversion. Weitere Informationen finden Sie in der [Experience Manager-Versions-Roadmap](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-releases-roadmap.html?lang=de).

### Verbesserungen {#enhancements-15575}

Keine

### Behobene Probleme {#fixed-issues-15575}

* ASSETS-36358: Bericht zum Hochladen kann nicht gerendert werden.
* GRANITE-50774: GraniteContent sollte die deterministische Reihenfolge der Eigenschaftswerte zum Zeitpunkt der Init-Zeit verwenden.

### Bekannte Probleme {#known-issues-15575}

Keine

### Änderungshinweis {#change-notice-15575}

**Erforderliche Aktionen**

#### Setzen Sie die Java-Version von CM auf 11 {#set-java-version-11}

Die neue Version von aem-sdk-api enthält Klassen, die mit einem Java 11-Ziel kompiliert wurden und nicht mit dem standardmäßigen JDK Version 1.8 der Cloud Manager-Build-Umgebung kompatibel sind. Diese Aktualisierung erfordert, dass Maven mit JDK 11 ausgeführt wird.

Kunden wird empfohlen, eine `.cloudmanager/java-version` -Datei im Stammverzeichnis ihres Git-Repo mit den folgenden Inhalten: `11`. Siehe [Build-Umgebung/Festlegen der Maven-JDK-Version](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/build-environment-details.md#alternate-maven-jdk-version).

#### Aktualisieren von aem-cloud-testing-clients auf 1.2.1 {#update-aem-cloud-testing-clients}

Bevorstehende Änderungen erfordern, dass die in Ihren benutzerdefinierten Funktionstests verwendete Bibliothek [aem-cloud-testing-clients](https://github.com/adobe/aem-testing-clients) mindestens auf Version **1.2.1** aktualisiert wird.

Stellen Sie sicher, dass Ihre Abhängigkeit in `it.tests/pom.xml` aktualisiert wurde.

```xml
<dependency>
   <groupId>com.adobe.cq</groupId>
   <artifactId>aem-cloud-testing-clients</artifactId>
   <version>1.2.1</version>
</dependency>
```

Diese Änderung muss vor dem 6. April 2024 vorgenommen werden.

Wenn die Abhängigkeitsbibliothek nicht aktualisiert wird, treten Pipeline-Fehler beim Schritt „Benutzerdefinierte Funktionstests“ auf.

### Eingebettete Technologien {#embedded-tech-15575}

| Technologie | Version | Link |
|---|---|---|
| AEM OAK | 1.60-T20240131102219-0cde853 | [Oak API 1.60.0-API](https://www.javadoc.io/doc/org.apache.jackrabbit/oak-api/1.60.0/index.html) |
| AEM SLING-API | Version: 2.27.2 | [Apache Sling-API 2.27.2 API](https://www.javadoc.io/doc/org.apache.sling/org.apache.sling.api/latest/index.html) |
| AEM HTL | Version: 1.4.20-1.4.0 | [Spezifikation von HTML-Vorlagensprachen](https://github.com/adobe/htl-spec) |
| AEM-Kernkomponenten | Version: 2.23.4 | [AEM WCM-Kernkomponenten](https://github.com/adobe/aem-core-wcm-components) |
