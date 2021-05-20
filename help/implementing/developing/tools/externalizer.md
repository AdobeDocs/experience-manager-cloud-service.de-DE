---
title: Externalisieren von URLs
description: Der Externalizer ist ein OSGi-Dienst, mit dem Sie einen Ressourcenpfad programmgesteuert in eine externe und absolute URL umwandeln können.
exl-id: 06efb40f-6344-4831-8ed9-9fc49f2c7a3f
source-git-commit: 84a97f09402602df33c8f0494feed57fdb510add
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 15%

---

# Externalisieren von URLs {#externalizing-urls}

In AEM ist der **Externalizer** ein OSGi-Dienst, mit dem Sie einen Ressourcenpfad (z. B. `/path/to/my/page`) in eine externe und absolute URL (z. B. `https://www.mycompany.com/path/to/my/page`) hinein, indem dem Pfad ein vorkonfiguriertes DNS vorangestellt wird.

Da eine AEM als Cloud Service-Instanz ihre extern sichtbare URL nicht kennen kann und manchmal ein Link außerhalb des Anforderungsbereichs erstellt werden muss, bietet dieser Dienst eine zentrale Stelle, an der diese externen URLs konfiguriert und erstellt werden können.

In diesem Artikel wird beschrieben, wie Sie den Externalizer-Dienst konfigurieren und verwenden. Technische Details zu diesem Dienst finden Sie im Abschnitt [Javadocs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html).

## Standardverhalten des Externalizers und Überschreiben von {#default-behavior}

Standardmäßig sind für den Externalizer-Dienst Werte wie `author-p12345-e6789.adobeaemcloud.com` und `publish-p12345-e6789.adobeaemcloud.com` bereits festgelegt, sodass Ihre AEM als Cloud Service-Installation ohne Eingriff Ihre benutzerdefinierte Domäne verwendet.

Um diese Werte zu überschreiben, verwenden Sie Cloud Manager-Umgebungsvariablen, wie im Artikel [Konfigurieren von OSGi für AEM als Cloud Service](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) beschrieben, und legen Sie die vordefinierten Variablen `AEM_CDN_DOMAIN_AUTHOR` und `AEM_CDN_DOMAIN_PUBLISH` fest.

## Konfigurieren des Externalizer-Dienstes {#configuring-the-externalizer-service}

Mit dem Externalizer-Dienst können Sie zentral die Domäne definieren, die zum programmatischen Präfix von Ressourcenpfaden verwendet werden kann. Der Externalizer-Dienst sollte nur für Anwendungen mit nur einer Domäne verwendet werden.

>[!NOTE]
>
>Wie beim Anwenden von [OSGi-Konfigurationen für AEM als Cloud Service,](/help/implementing/deploying/overview.md#osgi-configuration) sollten die folgenden Schritte auf einer lokalen Entwicklerinstanz ausgeführt und dann für die Bereitstellung in Ihren Projektcode übertragen werden.

Definieren Sie eine Domänenzuordnung für den Externalizer-Service wie folgt:

1. Navigieren Sie zum Configuration Manager über:

   `https://<host>:<port>/system/console/configMgr`

1. Klicken Sie auf **Day CQ Link Externalizer** , um das Konfigurationsdialogfeld zu öffnen.

   ![Die OSGi-Konfiguration des Externalizer](./assets/externalizer-osgi.png)

   >[!NOTE]
   >
   >Der direkte Link zur Konfiguration ist `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

1. Definieren Sie ein **Domänen**-Mapping. Eine Zuordnung besteht aus einem eindeutigen Namen, der im Code verwendet werden kann, um auf die Domäne, ein Leerzeichen und die Domäne zu verweisen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   wobei:

   * **`scheme`** ist normalerweise http oder https, kann aber ein anderes Protokoll sein.

      * Es wird empfohlen, HTTPS zu verwenden, um HTTPS-Links zu erzwingen.
      * Sie wird verwendet, wenn der Client-Code das Schema nicht überschreibt, wenn er die Externalisierung einer URL anfordert.
   * **`server`** ist der Hostname (entweder ein Domänenname oder eine IP-Adresse).
   * **`port`** (optional) ist die Anschlussnummer.
   * **`contextpath`** (optional) wird nur festgelegt, wenn AEM als Web-App unter einem anderen Kontextpfad installiert ist.

   Beispiel: `production https://my.production.instance`

   Die folgenden Zuordnungsnamen sind vordefiniert und müssen immer festgelegt werden, da sie von AEM abhängen:

   * `local` - die lokale Instanz
   * `author` - DNS des Authoring-Systems
   * `publish` - das DNS der öffentlichen Website

   >[!NOTE]
   >
   >Mit einer benutzerdefinierten Konfiguration können Sie eine neue Kategorie hinzufügen, z. B. `production`, `staging` oder sogar externe Nicht-AEM-Systeme wie `my-internal-webservice`. Es ist nützlich, die Hartkodierung solcher URLs an verschiedenen Stellen in der Codebasis eines Projekts zu vermeiden.

1. Klicken Sie auf **Speichern**, um Ihre Änderungen zu speichern.

### Verwenden des Externalizer-Dienstes {#using-the-externalizer-service}

Dieser Abschnitt zeigt einige Beispiele dafür, wie der Externalizer-Dienst verwendet werden kann.

>[!NOTE]
>
>Im Kontext von HTML sollten keine absoluten Links erstellt werden. Daher sollte dieses Dienstprogramm in solchen Fällen nicht verwendet werden.

* **Einen Pfad mit der publish-Domäne externalisieren Sie wie folgt:**

   ```java
   String myExternalizedUrl = externalizer.publishLink(resolver, "/my/page") + ".html";
   ```

   Angenommen, die Domänenzuordnung:

   * `publish https://www.website.com`

   * `myExternalizedUrl` endet mit dem Wert:

   * `https://www.website.com/contextpath/my/page.html`

* **Einen Pfad mit der author-Domäne externalisieren Sie wie folgt:**

   ```java
   String myExternalizedUrl = externalizer.authorLink(resolver, "/my/page") + ".html";
   ```

   Angenommen, die Domänenzuordnung:

   * `author https://author.website.com`

   * `myExternalizedUrl` endet mit dem Wert:

   * `https://author.website.com/contextpath/my/page.html`

* **Einen Pfad mit der local-Domäne externalisieren Sie wie folgt:**

   ```java
   String myExternalizedUrl = externalizer.externalLink(resolver, Externalizer.LOCAL, "/my/page") + ".html";
   ```

   Angenommen, die Domänenzuordnung:

   * `local https://publish-3.internal`

   * `myExternalizedUrl` endet mit dem Wert:

   * `https://publish-3.internal/contextpath/my/page.html`

>[!TIP]
>
>Weitere Beispiele finden Sie in den [Javadocs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html).
