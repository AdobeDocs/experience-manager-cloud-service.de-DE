---
title: Entwickeln von AEM Commerce für AEM as a Cloud Service
description: Erfahren Sie, wie Sie mit dem AEM Projektarchiv ein kommerziell unterstütztes AEM erstellen. Erfahren Sie, wie Sie das Projekt mithilfe des AEM als Cloud Service-SDK auf einer lokalen Entwicklungs-Umgebung erstellen und bereitstellen.
topics: Commerce, Development
feature: Commerce Integration Framework
version: cloud-service
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
translation-type: tm+mt
source-git-commit: 6be2ed60f4e672b99a85b55f833b8ae2f1b952b0
workflow-type: tm+mt
source-wordcount: '1070'
ht-degree: 89%

---


# Entwickeln von AEM Commerce für AEM as a Cloud Service {#develop}

Die Entwicklung von AEM Commerce-Projekten basierend auf Commerce Integration Framework (CIF) für AEM as a Cloud Service folgt denselben Regeln und Best Practices wie andere AEM-Projekte für AEM as a Cloud Service. Sehen Sie sich zuerst die folgenden Artikel an:

- [Struktur von AEM-Projekten](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/aem-project-content-package-structure.html)
- [AEM as a Cloud Service-SDK](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/aem-as-a-cloud-service-sdk.html)
- [Entwicklungsrichtlinien für AEM as a Cloud Service](https://docs.adobe.com/content/help/de/experience-manager-cloud-service/implementing/developing/development-guidelines.html)

## Lokale Entwicklung mit dem AEM as a Cloud Service-SDK {#local}

>[!VIDEO](https://video.tv.adobe.com/v/39476/?quality=12&learn=on)

Für die Arbeit mit CIF-Projekten wird eine lokale Entwicklungsumgebung empfohlen. Das für AEM as a Cloud Service-Umgebungen bereitgestellte CIF-Add-on ist auch für die lokale Entwicklung verfügbar. Es kann vom [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) heruntergeladen werden.

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

### Lokales Setup

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

   Diese Variable muss auch für die AEM as a Cloud Service-Umgebung eingerichtet werden.

   Weitere Informationen zu Variablen finden Sie unter [OSGi für AEM als Cloud Service](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development) konfigurieren.

1. (Optional) Um gestaffelte Katalogfunktionen zu aktivieren, müssen Sie ein Integrationstoken für Ihre Magento-Instanz erstellen. Führen Sie die Schritte unter [Erste Schritte](./getting-started.md#staging) aus, um das Token zu erstellen.

   Setzen Sie ein OSGi-Geheimnis mit dem Namen `COMMERCE_AUTH_HEADER` auf den folgenden Wert:

   ```xml
   Authorization: Bearer <Access Token>
   ```

   Weitere Informationen zu Geheimnissen finden Sie unter [OSGi für AEM als Cloud Service konfigurieren](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/implementing/deploying/configuring-osgi.html#local-development).

1. Starten Sie das AEM as a Cloud Service-SDK.

1. Starten Sie den lokalen GraphQL-Proxy-Server.

   Um den Magento GraphQL-Endpunkt lokal für das CIF-Add-on und die CIF-Komponenten verfügbar zu machen, verwenden Sie den folgenden Befehl. Der GraphQL-Endpunkt steht dann unter `http://localhost:3002/graphql` zur Verfügung.
Beispiel für Mac OSX:

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial ''
   ```

   Beispiel für Windows:

   ```bash
   npx local-cors-proxy --proxyUrl https://demo.magentosite.cloud --port 3002 --proxyPartial '""'
   ```

   Das Argument `--proxyPartial` muss eine leere Zeichenfolge erhalten.

   Sie können den lokalen GraphQL-Proxy testen, indem Sie mit einem GraphQL-Abfrage-Tool auf `http://localhost:3002/graphql` verweisen und einige Abfragen testen.

1. Melden Sie sich beim AEM SDK an und konfigurieren Sie CIF für die Verwendung des lokalen GraphQL-Proxy-Servers..

   Navigieren Sie zur CIF-Cloud Service-Konfiguration („Tools“ > „Cloud Services“ > „CIF-Konfiguration“). Öffnen Sie die Eigenschaftsansicht der von Ihrem Projekt verwendeten Konfiguration.

   Verwenden Sie für die `GraphQL Proxy Path`-Eigenschaft den lokalen Proxy-Server-Endpunkt `http://localhost:3002/graphql`. Speichern Sie die Konfiguration.

>[!NOTE]
>
>Veröffentlichen Sie die Konfiguration von Schritt 8 nicht in das Projekt-Repository. Diese Konfiguration ist nur für ein lokales Entwicklungs-Setup erforderlich. AEM as a Cloud Service-Umgebungen werden bereits während des Einstiegs mit dem GraphQL-Proxy eingerichtet.

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

CIF-Kernkomponenten können in jedem Projekt verwendet werden, indem entweder das bereitgestellte `all`-Paket oder sie einzeln mithilfe des CIF-Inhaltspakets und den entsprechenden OSGi-Paketen hinzugefügt werden. Verwenden Sie die folgenden Abhängigkeiten, um einem Projekt manuell CIF-Kernkomponenten hinzuzufügen:

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

### Verwenden des AEM Venia Reference Store

Eine zweite Möglichkeit, ein CIF-Projekt zu starten, besteht darin, den [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia) zu klonen und zu verwenden. Der AEM Venia Reference Store ist eine Beispiel-Referenz-Storefront-Anwendung, die die Verwendung von CIF-Kernkomponenten für AEM demonstriert. Sie ist sowohl als Satz von Best Practice-Beispielen als auch als möglicher Ausgangspunkt für die Entwicklung Ihrer eigenen Funktionalität gedacht.

Um mit dem Venia Reference Store zu beginnen, klonen Sie einfach das Git-Repository und passen Sie das Projekt an Ihre Bedürfnisse an.

>[!NOTE]
>
>Das Venia Reference Store-Projekt enthält zwei Build-Profile für AEM as a Cloud Service und AEM 6.5. Schauen Sie sich die Datei [readme.md](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) des Projekts an, um zu sehen, wie sie verwendet werden.

## Zusätzliche Ressourcen

- [AEM-Projektarchetyp](https://github.com/adobe/aem-project-archetype)
- [AEM Venia Reference Store](https://github.com/adobe/aem-cif-guides-venia)
- [Software Distribution-Portal](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html)
