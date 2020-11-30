---
title: Entwicklung AEM Handels für AEM als Cloud Service
description: Erfahren Sie, wie Sie mit dem AEM Projektarchiv ein kommerziell unterstütztes AEM erstellen. Erfahren Sie, wie Sie das Projekt mithilfe des AEM als Cloud Service-SDK auf einer lokalen Entwicklungs-Umgebung erstellen und bereitstellen.
topics: Commerce, Development
feature: Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
translation-type: tm+mt
source-git-commit: 72d98c21a3c02b98bd2474843b36f499e8d75a03
workflow-type: tm+mt
source-wordcount: '987'
ht-degree: 12%

---


# Entwicklung AEM Handels für AEM als Cloud Service {#develop}

Die Entwicklung AEM Handelsprojekte auf der Grundlage des Commerce Integration Framework (CIF) für AEM als Cloud Service folgt den gleichen Regeln und Best Practices wie andere AEM Projekte auf AEM als Cloud Service. Bitte überprüfen Sie diese zuerst:

- [Struktur von AEM-Projekten](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service-SDK](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [Entwicklungsrichtlinien für AEM as a Cloud Service](https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## Lokale Entwicklung mit AEM als Cloud Service-SDK {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

Eine lokale Entwicklungs-Umgebung wird empfohlen, um mit CIF-Projekten zu arbeiten. Das CIF-Hinzufügen-on, das als Cloud Service-Umgebung AEM ist, steht auch für die örtliche Entwicklung zur Verfügung. Es kann vom [Software Distribution Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)heruntergeladen werden.

Das CIF Hinzufügen-On wird als Sling Feature Archiv bereitgestellt. Die im Software Distribution Portal verfügbare ZIP-Datei enthält zwei Sling Feature-Archivdateien, eine für AEM Autor und eine für AEM Veröffentlichungsinstanzen.

**Neu AEM als Cloud Service?** Sehen Sie sich [eine detaillierte Anleitung zum Einrichten einer lokalen Entwicklungs-Umgebung mit dem AEM als Cloud Service-SDK](https://docs.adobe.com/content/help/de-DE/experience-manager-learn/cloud-service/local-development-environment-set-up/overview.html)an.

### Erforderliche Software

Folgendes sollte lokal installiert werden:

- [AEM as a Cloud Service-SDK](https://docs.adobe.com/content/help/en/*experience-manager-learn/cloud-service/local-development-environment-set-up/aem-runtime.html#download-the-aem-as-a-cloud-service-sdk)
- [Java 11](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [Apache Maven](https://maven.apache.org/) (3.3.9 oder neuer)
- [Node.js v10+](https://nodejs.org/de/)
- [npm 6+](https://www.npmjs.com/)
- [Git](https://git-scm.com/)

### Zugriff auf das CIF-Add-on

The CIF add-on can be downloaded as a zip file from the [Software Distribution portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html). Die ZIP-Datei enthält das CIF-Add-on als **Sling Feature-Archiv**, es ist kein AEM Paket. Beachten Sie, dass der Zugriff auf die SDK-Listen auf die Listen mit AEM als Cloud Service-Lizenz beschränkt ist.

>[!TIP]
>
>Stellen Sie sicher, dass Sie immer die neueste CIF Hinzufügen-On Version verwenden.

### Lokale Einrichtung

Für die lokale CIF-Hinzufügen-on-Entwicklung, bei der das AEM als Cloud Service-SDK verwendet wird, gehen Sie wie folgt vor:

1. Die neuesten AEM als Cloud Service-SDK
2. Entpacken Sie die AEM .jar, um den `crx-quickstart` Ordner zu erstellen, und führen Sie Folgendes aus:

   ```bash
   java -jar <jar name> -unpack
   ```

3. Create a `crx-quickstart/install` folder
4. Kopieren Sie die richtige Sling Feature-Archivdatei des CIF-Add-ons in den `crx-quickstart/install` Ordner.

   Die CIF-Add-on-ZIP-Datei enthält zwei Sling Feature-Archivdateien `.far` . Achten Sie darauf, je nachdem, wie Sie die lokale AEM als Cloud Service-SDK ausführen möchten, das richtige für AEM Author oder AEM Publish zu verwenden.

5. Erstellen Sie eine lokale OS-Umgebung mit dem Namen `COMMERCE_ENDPOINT` , die den Magento GraphQL-Endpunkt enthält.

   Beispiel Mac OSX:

   ```bash
   export COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Beispiel Windows:

   ```bash
   set COMMERCE_ENDPOINT=https://demo.magentosite.cloud/graphql
   ```

   Diese Variable muss auch für die AEM als Cloud Service-Umgebung eingerichtet werden.

6. Beginn des AEM als Cloud Service-SDK

7. Beginn des lokalen GraphQL-Proxyservers

   Um den Magento GraphQL-Endpunkt lokal für das CIF-Add-on und die CIF-Komponenten verfügbar zu machen, verwenden Sie den folgenden Befehl. Der GraphQL-Endpunkt steht dann unter `http://localhost:3002/graphql`.
Beispiel Mac OSX:

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial ''
   ```

   Beispiel Windows:

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial '""'
   ```
   Das Argument `--proxyPartial` muss eine leere Zeichenfolge erhalten.

   Sie können den lokalen GraphQL-Proxy testen, indem Sie mit einem GraphQL-Abfrage-Tool einige Abfragen testen `http://localhost:3002/graphql` und testen.

8. Melden Sie sich bei AEM SDK an und konfigurieren Sie CIF für die Verwendung des lokalen GraphQL-Proxyservers

   Navigieren Sie zur CIF-Cloud Service-Konfiguration (&quot;Extras&quot;> &quot;Cloud Services&quot;> &quot;CIF-Konfiguration&quot;). Öffnen Sie die Ansicht Eigenschaften der von Ihrem Projekt verwendeten Konfiguration.

   Verwenden Sie für die `GraphQL Proxy Path` Eigenschaft den lokalen Proxyserver-Endpunkt `http://localhost:3002/graphql`. Speichern Sie die Konfiguration.

>[!NOTE]
>
>Schieben Sie die Konfiguration von Schritt 8 nicht in den Projektbericht. Diese Konfiguration ist nur für eine lokale Entwicklungseinrichtung erforderlich. AEM als Cloud Service-Umgebung werden bereits während des Einsteigens mit dem GraphQL Proxy eingerichtet.

Überprüfen Sie das Setup über OSGI-Konsole:`http://localhost:4502/system/console/osgi-installer`. Die Liste sollte die CIF-Add-on-bezogenen Bundles, Inhaltspakete und OSGI-Konfigurationen enthalten, wie in der Funktionsmodelldatei definiert.

## Projekt-Setup {#project}

Es gibt zwei Möglichkeiten, Ihr CIF-Projekt als Cloud Service für AEM zu bootstrapping durchzuführen.

### AEM Projektarchetyp verwenden

Das [AEM Projekt Archetype](https://github.com/adobe/aem-project-archetype) ist das Hauptwerkzeug, um ein vorkonfiguriertes Projekt zu starten und mit CIF zu starten. CIF-Kernkomponenten und alle erforderlichen Konfigurationen können mit einer zusätzlichen Option in ein generiertes Projekt aufgenommen werden.

>[!TIP]
>
>Verwenden Sie [AEM Projektarchiv 24 oder höher](https://github.com/adobe/aem-project-archetype/releases) , um das Projekt zu erstellen.

Informationen zum Generieren eines AEM-Projekts finden Sie AEM [Gebrauchsanweisungen](https://github.com/adobe/aem-project-archetype#usage) zum Projektarchiv. Um CIF in das Projekt einzubeziehen, verwenden Sie die `includeCommerce` Option.

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

CIF-Kernkomponenten können in jedem Projekt verwendet werden, indem entweder das bereitgestellte `all` Paket oder individuell mit dem CIF-Inhaltspaket und dazugehörigen OSGI-Bundles verwendet werden. Um einem Projekt CIF-Kernkomponenten manuell hinzuzufügen, verwenden Sie die folgenden Abhängigkeiten:

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
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

### Verwenden AEM Venedig Reference Store

Eine zweite Möglichkeit zum Beginn eines CIF-Projektes ist das Klonen und Verwenden des [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia). Der AEM Venia Reference Store ist eine Beispielanwendung, die die Verwendung der CIF-Kernkomponenten für AEM demonstriert. Es ist als Best-Practice-Satz von Beispielen sowie als potenzieller Ausgangspunkt zur Entwicklung Ihrer eigenen Funktionalität gedacht.

Um mit dem Venia Reference Store zu beginnen, klonen Sie einfach das Git-Repository und Beginn, die das Projekt an Ihre Bedürfnisse anpassen.

>[!NOTE]
>
>Das Projekt Venia Reference Store umfasst zwei Profile für AEM als Cloud Service und AEM 6.5. Überprüfen Sie, ob das [Projekt readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) verwendet wird.

## Zusätzliche Ressourcen

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venedig-Referenzspeicher](https://github.com/adobe/aem-cif-guides-venia)
- [Softwareverteilungsportal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
