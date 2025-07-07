---
title: Entwickeln von AEM Commerce für AEM as a Cloud Service
description: Erfahren Sie, wie Sie ein Commerce-fähiges AEM-Projekt mithilfe des AEM-Projektarchetyps generieren. Erfahren Sie, wie Sie das Projekt mithilfe des AEM as a Cloud Service-SDK in einer lokalen Entwicklungsumgebung erstellen und bereitstellen.
topics: Commerce, Development
feature: Commerce Integration Framework
version: Experience Manager as a Cloud Service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
exl-id: 6f28a52b-52f8-4b30-95cd-0f9cb521de62
role: Admin
index: false
source-git-commit: 173b70aa6f9ad848d0f80923407bf07540987071
workflow-type: ht
source-wordcount: '908'
ht-degree: 100%

---

# Entwickeln von AEM Commerce für AEM as a Cloud Service {#develop}

Die Entwicklung von AEM Commerce-Projekten basierend auf dem Commerce Integration Framework (CIF) für AEM as a Cloud Service folgt denselben Regeln und Best Practices wie andere AEM-Projekte für AEM as a Cloud Service. Überprüfen Sie zunächst die folgenden Punkte:

- [Struktur von AEM-Projekten](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-project-content-package-structure.html?lang=de)
- [AEM as a Cloud Service-SDK](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/aem-as-a-cloud-service-sdk.html?lang=de)
- [Entwicklungsrichtlinien für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/development-guidelines.html?lang=de)

## Lokale Entwicklung mit dem AEM as a Cloud Service-SDK {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

Für die Arbeit mit CIF-Projekten wird eine lokale Entwicklungsumgebung empfohlen. Das für AEM as a Cloud Service bereitgestellte CIF-Add-on ist auch für die lokale Entwicklung verfügbar. Es kann vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) heruntergeladen werden.

Das CIF-Add-on wird als Sling Feature-Archiv bereitgestellt. Die im Software Distribution-Portal verfügbare Zip-Datei enthält zwei Sling Feature-Archivdateien, eine für AEM-Autoren- und eine für AEM-Veröffentlichungsinstanzen.

**Neu bei AEM as a Cloud Service?** Sehen Sie sich [eine detaillierte Anleitung zum Einrichten einer lokalen Entwicklungsumgebung mit dem AEM as a Cloud Service-SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html?lang=de) an.

### Erforderliche Software

Folgendes sollte lokal installiert werden:

- [AEM as a Cloud Service-SDK](https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html?lang=de#download-the-aem-as-a-cloud-service-sdk)
- [Java™ 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 oder höher)
- [Node.js v10+](https://nodejs.org/de)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Zugriff auf das CIF-Add-on

Das CIF-Add-on kann als ZIP-Datei vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) heruntergeladen werden. Die ZIP-Datei enthält das CIF-Add-on als **Sling Feature-Archiv**. Es ist kein AEM-Paket. Auf SDK-Listen kann über eine AEM as a Cloud Service Lizenz zugegriffen werden.

>[!TIP]
>
>Stellen Sie sicher, dass Sie immer die neueste Version des CIF-Add-ons verwenden.

### Lokales Setup

Gehen Sie für die lokale CIF-Add-on-Entwicklung mit dem AEM as a Cloud Service-SDK wie folgt vor:

1. Laden Sie das aktuelle AEM as a Cloud Service-SDK.
1. Entpacken Sie die AEM-.jar-Datei, damit Sie den Ordner `crx-quickstart` erstellen können, und führen Sie sie aus:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Erstellen Sie einen `crx-quickstart/install`-Ordner.
1. Kopieren Sie die richtige Sling Feature-Archivdatei des CIF-Add-ons in den `crx-quickstart/install`-Ordner.

   Die CIF-Add-on-ZIP-Datei enthält zwei Sling Feature-Archivdateien (`.far`). Stellen Sie sicher, dass Sie die richtige Version für die AEM-Autoren- oder AEM-Veröffentlichungsumgebung verwenden, je nachdem, wie Sie das lokale AEM as a Cloud Service-SDK ausführen möchten.

1. Erstellen Sie eine lokale Betriebssystem-Umgebungsvariable mit dem Namen `COMMERCE_ENDPOINT`, die den Adobe Commerce GraphQL-Endpunkt beinhaltet.

   Beispiel für macOS X:

   ```bash
   export COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   Beispiel für Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://<yourcommercesystem>/graphql
   ```

   Diese Variable wird von AEM verwendet, um eine Verbindung zu Ihrem E-Commerce-System herzustellen. Darüber hinaus enthält das CIF-Add-on einen lokalen Reverse-Proxy, um den Commerce-GraphQL-Endpunkt lokal verfügbar zu machen. Dieser Proxy wird von den CIF-Authoring-Tools (Produktkonsole und Auswahl) und für die Client-seitigen CIF-Komponenten verwendet, die direkte GraphQL-Aufrufe durchführen.

   Diese Variable muss auch für die AEM as a Cloud Service-Umgebung eingerichtet werden. Weitere Informationen zu Variablen finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html?lang=de#local-development).

1. (Optional) Um Funktionen für gestaffelte Katalogdaten zu aktivieren, müssen Sie ein Integrations-Token für Ihre Adobe Commerce-Instanz erstellen. Führen Sie die Schritte unter [Erste Schritte](./getting-started.md#staging) aus, um das Token zu erstellen.

   Setzen Sie ein OSGi-Geheimnis mit dem Namen `COMMERCE_AUTH_HEADER` auf den folgenden Wert:

   ```xml
   Authorization: Bearer <Access Token>
   ```

   Weitere Informationen zu Geheimnissen finden Sie unter [Konfigurieren von OSGi für AEM as a Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/deploying/configuring-osgi.html?lang=de#local-development).

1. Starten Sie das AEM as a Cloud Service-SDK.

>[!NOTE]
>
>Stellen Sie sicher, dass Sie das AEM as a Cloud Service-SDK im selben Terminal-Fenster starten, in dem die Umgebungsvariable in Schritt 5 festgelegt wurde. Wenn Sie es in einem separaten Terminal-Fenster oder durch Doppelklicken auf die JAR-Datei starten, stellen Sie sicher, dass die Umgebungsvariable sichtbar ist.

Überprüfen Sie das Setup über die OSGi-Konsole: `http://localhost:4502/system/console/osgi-installer`. Die Liste sollte die mit dem CIF-Add-on zusammenhängenden Pakete, Content-Pakete und OSGi-Konfigurationen enthalten, wie sie in der Feature-Modelldatei definiert sind.

## Projekt-Setup {#project}

Es gibt zwei Möglichkeiten für das Bootstrapping Ihres CIF-Projekts für AEM as a Cloud Service.

### Verwenden des AEM-Projektarchetyps

Der [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype) ist das wichtigste Tool für das Bootstrapping eines vorkonfigurierten Projekts, um mit CIF zu beginnen. Die CIF-Kernkomponenten und alle erforderlichen Konfigurationen können mit einer zusätzlichen Option in ein generiertes Projekt aufgenommen werden.

>[!TIP]
>
>Verwenden Sie immer die neueste Version des [AEM-Projektarchetyps](https://github.com/adobe/aem-project-archetype/releases), um das Projekt zu generieren.

Weitere Informationen zum Generieren eines AEM-Projekts finden Sie in den [Anweisungen zur Verwendung](https://github.com/adobe/aem-project-archetype#usage) des AEM-Projektarchetyps. Verwenden Sie die Option `includeCommerce`, um CIF in das Projekt aufzunehmen.

Beispiel:

```bash
mvn -B org.apache.maven.plugins:maven-archetype-plugin:3.2.1:generate \
 -D archetypeGroupId=com.adobe.aem \
 -D archetypeArtifactId=aem-project-archetype \
 -D archetypeVersion=35 \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D includeCommerce=y
```

CIF-Kernkomponenten können in jedem Projekt verwendet werden, indem entweder das bereitgestellte `all`-Paket oder sie einzeln mithilfe des CIF-Inhaltspakets und den zugehörigen OSGi-Paketen hinzugefügt werden. Verwenden Sie die folgenden Abhängigkeiten, um einem Projekt manuell CIF-Kernkomponenten hinzuzufügen:

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

Eine zweite Möglichkeit, ein CIF-Projekt zu starten, besteht darin, den [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) zu klonen und zu verwenden. Der AEM Venia Reference Store ist ein Beispiel-Referenz-Storefront-Programm, das die Verwendung von CIF-Kernkomponenten für AEM demonstriert. Sie ist sowohl als Satz von Best Practice-Beispielen als auch als möglicher Ausgangspunkt für die Entwicklung Ihrer eigenen Funktionalität gedacht.

Um mit dem Venia Referenz-Store zu beginnen, klonen Sie das Git-Repository und passen Sie das Projekt an Ihre Bedürfnisse an.

>[!NOTE]
>
>Das Venia Reference Store-Projekt enthält zwei Build-Profile für AEM as a Cloud Service und AEM 6.5. Schauen Sie sich die Datei [readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) des Projekts an, um zu sehen, wie sie verwendet werden.

## Zusätzliche Ressourcen

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
