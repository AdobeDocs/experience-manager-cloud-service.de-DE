---
title: Externalisieren von URLs
description: Der Externalizer ist ein OSGi-Service, der es Ihnen ermöglicht, Ressourcenpfade programmgesteuert in externe, absolute URLs umzuwandeln.
exl-id: 06efb40f-6344-4831-8ed9-9fc49f2c7a3f
source-git-commit: c08e442e58a4ff36e89a213aa7b297b538ae3bab
workflow-type: tm+mt
source-wordcount: '569'
ht-degree: 96%

---

# Externalisieren von URLs {#externalizing-urls}

In AEM ist der **Externalizer** ein OSGi-Service, der es Ihnen ermöglicht, einen Ressourcenpfad (z. B. `/path/to/my/page`) in eine externe und absolute URL umzuwandeln (z. B. `https://www.mycompany.com/path/to/my/page`), indem der Pfad mit einer vorangestellten vorkonfigurieren DNS versehen wird.

Da eine AEM as a Cloud Service-Instanz ihre extern sichtbare URL nicht kennen kann und manchmal ein Link außerhalb des Anfragebereichs erstellt werden muss, bietet dieser Service eine zentrale Stelle, an der diese externen URLs konfiguriert und erstellt werden können.

Auf dieser Seite wird beschrieben, wie Sie den Externalizer-Service konfigurieren und verwenden. Technische Details zu diesem Service finden Sie im Abschnitt [Javadocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html).

## Standardverhalten des Externalizers und Überschreiben {#default-behavior}

Standardmäßig verfügt der Externalizer-Service über Werte wie `author-p12345-e6789.adobeaemcloud.com` und `publish-p12345-e6789.adobeaemcloud.com`.

Um diese Werte zu überschreiben, verwenden Sie Cloud Manager-Umgebungsvariablen, wie im Artikel [Konfigurieren von OSGi für AEM as a Cloud Service](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) beschrieben, und legen Sie die vordefinierten Variablen `AEM_CDN_DOMAIN_AUTHOR` und `AEM_CDN_DOMAIN_PUBLISH` fest.

## Konfigurieren des Externalizer-Service {#configuring-the-externalizer-service}

Der Externalizer-Service ermöglicht es Ihnen, zentral mehrere Domains zu definieren, die für das programmgesteuerte Voranstellen in Ressourcenpfaden verwendet werden können. Der Externalizer-Service sollte nur für Programme mit einer einzelnen Domain verwendet werden.

>[!NOTE]
>
>Wie beim Anwenden von [OSGi-Konfigurationen für AEM as a Cloud Service](/help/implementing/deploying/overview.md#osgi-configuration) sollten die folgenden Schritte auf einer lokalen Entwicklerinstanz ausgeführt und dann für die Implementierung in Ihren Projekt-Code übertragen werden.

Definieren Sie eine Domain-Zuordnung für den Externalizer-Service wie folgt:

1. Gehen Sie zum Configuration Manager über:

   `https://<host>:<port>/system/console/configMgr`

1. Klicken Sie auf **Day CQ Link Externalizer**, um das Konfigurationsdialogfeld zu öffnen.

   ![Die OSGi-Konfiguration des Externalizers](./assets/externalizer-osgi.png)

   >[!NOTE]
   >
   >Der Direkt-Link zur Konfiguration lautet `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

1. Definieren Sie eine **Domain**-Zuordnung. Eine Zuordnung besteht aus einem eindeutigen Namen, der im Code verwendet werden kann, um auf die Domain, ein Leerzeichen und die Domain zu verweisen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   Dabei gilt:

   * **`scheme`** ist normalerweise HTTP oder HTTPS, kann aber ein anderes Protokoll sein.

      * Es wird empfohlen, HTTPS zu verwenden, um HTTPS-Links zu erzwingen.
      * Es wird verwendet, wenn der Client-Code das Schema nicht überschreibt, wenn er die Externalisierung einer URL anfordert.
   * **`server`** ist der Host-Name (kann ein Domain-Name oder eine IP-Adresse sein).
   * **`port`** (optional) ist die Port-Nummer.
   * **`contextpath`** (optional) wird nur festgelegt, wenn AEM als Web-App unter einem anderen Kontextpfad installiert wird.

   Beispiel: `production https://my.production.instance`

   Die folgenden Zuordnungsnamen sind vordefiniert und müssen immer festgelegt werden, da AEM auf sie angewiesen ist:

   * `local` – die lokale Instanz
   * `author` – das DNS des Bearbeitungssystems
   * `publish` – das DNS der öffentlichen Website

   >[!NOTE]
   >
   >Mit einer benutzerdefinierten Konfiguration können Sie eine neue Kategorie hinzufügen, z. B. `production`, `staging` oder sogar externe Nicht-AEM-Systeme wie `my-internal-webservice`. Es ist nützlich, die Hartkodierung solcher URLs an verschiedenen Stellen in der Code-Basis eines Projekts zu vermeiden.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### Verwenden des Externalizer-Service {#using-the-externalizer-service}

Dieser Abschnitt zeigt einige Beispiele dafür, wie der Externalizer-Service verwendet werden kann.

>[!NOTE]
>
>Im Kontext von HTML sollten keine absoluten Links erstellt werden. Daher sollte dieses Dienstprogramm in solchen Fällen nicht verwendet werden.

* **Einen Pfad mit der publish-Domain externalisieren Sie wie folgt:**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   Angenommen, die Domain-Zuordnung:

   * `publish https://www.website.com`

   * `myExternalizedUrl` endet mit dem Wert:

   * `https://www.website.com/contextpath/my/page.html`

* **So externalisieren Sie einen Pfad mit der Domain „author“:**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   Angenommen, die Domain-Zuordnung:

   * `author https://author.website.com`

   * `myExternalizedUrl` endet mit dem Wert:

   * `https://author.website.com/contextpath/my/page.html`

* **So externalisieren Sie einen Pfad mit der Domain „local“:**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   Angenommen, die Domain-Zuordnung:

   * `local https://publish-3.internal`

   * `myExternalizedUrl` endet mit dem Wert:

   * `https://publish-3.internal/contextpath/my/page.html`

>[!TIP]
>
>Weitere Beispiele finden Sie in den [Javadocs](https://www.adobe.io/experience-manager/reference-materials/cloud-service/javadoc/com/day/cq/commons/Externalizer.html).
