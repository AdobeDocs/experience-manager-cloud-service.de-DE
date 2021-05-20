---
title: Entwickeln von AEM Commerce für AEM as a Cloud Service
description: Erfahren Sie, wie Sie ein Commerce-fähiges AEM-Projekt mithilfe des AEM-Projektarchetyps generieren. Erfahren Sie, wie Sie das Projekt mithilfe des AEM as a Cloud Service-SDK in einer lokalen Entwicklungsumgebung erstellen und bereitstellen.
topics: Commerce, Development
feature: Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 6f28a52b-52f8-4b30-95cd-0f9cb521de62
source-git-commit: 84a97f09402602df33c8f0494feed57fdb510add
workflow-type: tm+mt
source-wordcount: '1011'
ht-degree: 85%

---

# Entwickeln von AEM Commerce für AEM as a Cloud Service {#develop}

Die Entwicklung von AEM Commerce-Projekten basierend auf Commerce Integration Framework (CIF) für AEM as a Cloud Service folgt denselben Regeln und Best Practices wie andere AEM-Projekte für AEM as a Cloud Service. Sehen Sie sich zuerst die folgenden Artikel an:

- [Struktur von AEM-Projekten](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service-SDK](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [Entwicklungsrichtlinien für AEM as a Cloud Service](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## Lokale Entwicklung mit dem AEM as a Cloud Service-SDK {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

Für die Arbeit mit CIF-Projekten wird eine lokale Entwicklungsumgebung empfohlen. Das CIF-Add-on für AEM als Cloud Service steht auch für die lokale Entwicklung zur Verfügung. Es kann vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) heruntergeladen werden.

Das CIF-Add-on wird als Sling Feature-Archiv bereitgestellt. Die im Software Distribution-Portal verfügbare Zip-Datei enthält zwei Sling Feature-Archivdateien, eine für AEM-Autoren- und eine für AEM-Veröffentlichungsinstanzen.

**Neu bei AEM as a Cloud Service?** Sehen Sie sich [eine detaillierte Anleitung zum Einrichten einer lokalen Entwicklungsumgebung mit dem AEM as a Cloud Service-SDK](https://docs.adobe.com/content/help/de/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html) an.

### Erforderliche Software

Folgendes sollte lokal installiert werden:

- [AEM as a Cloud Service-SDK](https://docs.adobe.com/content/help/de/*experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 oder höher)
- [Node.js v10+](https://nodejs.org/en/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Zugriff auf das CIF-Add-on

Das CIF-Add-on kann als ZIP-Datei vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) heruntergeladen werden. Die ZIP-Datei enthält das CIF-Add-on als **Sling Feature-Archiv**. Es ist kein AEM-Paket. Beachten Sie, dass der Zugriff auf die SDK-Listen auf Benutzer mit AEM as a Cloud Service-Lizenz beschränkt ist.

>[!TIP]
>
>Stellen Sie sicher, dass Sie immer die neueste Version des CIF-Add-ons verwenden.

### Lokale Einrichtung

Gehen Sie für die lokale CIF-Add-on-Entwicklung mit dem AEM as a Cloud Service-SDK wie folgt vor:

1. Laden Sie das aktuelle AEM as a Cloud Service-SDK.
1. Entpacken Sie die AEM.jar, um den `crx-quickstart`-Ordner zu erstellen, und führen Sie Folgendes aus:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Erstellen Sie einen `crx-quickstart/install`-Ordner.
1. Kopieren Sie die richtige Sling Feature-Archivdatei des CIF-Add-ons in den `crx-quickstart/install`-Ordner.

   Die CIF-Add-on-ZIP-Datei enthält zwei Sling Feature-Archivdateien (`.far`). Stellen Sie sicher, dass Sie die richtige Version für die AEM-Autoren- oder AEM-Veröffentlichungsumgebung verwenden, je nachdem, wie Sie das lokale AEM as a Cloud Service-SDK ausführen möchten.

1. Erstellen Sie eine lokale BS-Umgebungsvariable mit dem Namen `COMMERCE_ENDPOINT`, die den Magento GraphQL-Endpunkt beinhaltet.

   Beispiel für Mac OSX:

   ```bash
   export COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Beispiel für Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Diese Variable wird von AEM verwendet, um eine Verbindung zu Ihrem E-Commerce-System herzustellen. Außerdem enthält das CIF-Add-on einen lokalen Reverse-Proxy, um den Commerce GraphQL-Endpunkt lokal verfügbar zu machen. Dies wird von den CIF-Authoring-Werkzeugen (Produktkonsole und Picker) und für die Client-seitigen CIF-Komponenten verwendet, die direkte GraphQL-Aufrufe durchführen.

   Diese Variable muss auch für die AEM as a Cloud Service-Umgebung eingerichtet werden. Weitere Informationen zu Variablen finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html?lang=de#local-development).

1. (Optional) Um gestaffelte Katalogfunktionen zu aktivieren, müssen Sie ein Integrations-Token für Ihre Magento-Instanz erstellen. Führen Sie die Schritte unter [Erste Schritte](./getting-started.md#staging) aus, um das Token zu erstellen.

   Setzen Sie ein OSGi-Geheimnis mit dem Namen `COMMERCE_AUTH_HEADER` auf den folgenden Wert:

   ```xml
   Authorization: Bearer <Access Token>
   ```

   Weitere Informationen zu Geheimnissen finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development).

1. Starten Sie das AEM as a Cloud Service-SDK.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie AEM als Cloud Service-SDK im selben Terminal-Fenster starten, in dem die Umgebungsvariable in Schritt 5 festgelegt wurde. Wenn Sie es in einem separaten Terminalfenster starten oder durch Doppelklicken auf die JAR-Datei, stellen Sie sicher, dass die Umgebungsvariable sichtbar ist.

Überprüfen Sie das Setup über die OSGi-Konsole: `http://localhost:4502/system/console/osgi-installer`. Die Liste sollte die mit dem CIF-Add-on zusammenhängenden Pakete, Content-Pakete und OSGi-Konfigurationen enthalten, wie sie in der Feature-Modelldatei definiert sind.

## Projekt-Setup {#project}

Es gibt zwei Möglichkeiten für das Bootstrapping Ihres CIF-Projekts für AEM as a Cloud Service.

### Verwenden des AEM-Projektarchetyps

Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) ist das wichtigste Tool für das Bootstrapping eines vorkonfigurierten Projekts, um mit CIF zu beginnen. Die CIF-Kernkomponenten und alle erforderlichen Konfigurationen können mit einer zusätzlichen Option in ein generiertes Projekt aufgenommen werden.

>[!TIP]
>
>Verwenden Sie [AEM-Projektarchetyp 24 oder höher](https://github.com/adobe/aem-project-archetype/releases), um das Projekt zu erstellen.

Weitere Informationen zum Generieren eines AEM-Projekts finden Sie in den [Anweisungen zur Verwendung](https://github.com/adobe/aem-project-archetype#usage) des AEM-Projektarchetyps. Verwenden Sie die Option `includeCommerce`, um CIF in das Projekt aufzunehmen.

Beispiel:

```bash
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.granite.archetypes \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=24 \
 -D aemVersion=cloud \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D frontendModule=general \
 -D includeExamples=n \
 -D includeCommerce=y
```

CIF-Kernkomponenten können in jedem Projekt verwendet werden, indem entweder das bereitgestellte `all`-Paket oder einzeln mithilfe des CIF-Inhaltspakets und der zugehörigen OSGI-Bundles eingefügt werden. Verwenden Sie die folgenden Abhängigkeiten, um einem Projekt manuell CIF-Kernkomponenten hinzuzufügen:

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-config</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-core</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>graphql-client</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>magento-graphql</artifactId>
    <version>x.y.z</version>
</dependency>
```

### Verwenden des AEM Venia Reference Store

Eine zweite Möglichkeit, ein CIF-Projekt zu starten, besteht darin, den [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) zu klonen und zu verwenden. Der AEM Venia Reference Store ist ein Beispiel-Referenz-Storefront-Programm, das die Verwendung von CIF-Kernkomponenten für AEM demonstriert. Es ist als Best-Practice-Satz von Beispielen und als möglicher Ausgangspunkt für die Entwicklung Ihrer eigenen Funktionalität gedacht.

Um mit dem Venia Reference Store zu beginnen, klonen Sie einfach das Git-Repository und passen Sie das Projekt an Ihre Bedürfnisse an.

>[!NOTE]
>
>Das Venia Reference Store-Projekt enthält zwei Build-Profile für AEM as a Cloud Service und AEM 6.5. Schauen Sie sich die Datei [readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) des Projekts an, um zu sehen, wie sie verwendet werden.

## Zusätzliche Ressourcen

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
