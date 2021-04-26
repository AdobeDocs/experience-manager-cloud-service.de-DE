---
title: Externalisieren von URLs
description: Der Externalizer ist ein OSGi-Dienst, mit dem Sie einen Ressourcenpfad programmgesteuert in eine externe und absolute URL umwandeln können.
translation-type: tm+mt
source-git-commit: 4c584ceadaa358120d1d4b4cabd7e21ced814b31
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 15%

---


# Externalisieren von URLs {#externalizing-urls}

In AEM ist der **Externalizer** ein OSGi-Dienst, mit dem Sie einen Ressourcenpfad programmgesteuert transformieren können (z. `/path/to/my/page`) in eine externe und absolute URL (z. B. `https://www.mycompany.com/path/to/my/page`) hinein, indem dem Pfad ein vorkonfiguriertes DNS vorangestellt wird.

Da eine AEM als Cloud Service-Instanz ihre extern sichtbare URL nicht erkennen kann und manchmal ein Link außerhalb des Anforderungsbereichs erstellt werden muss, stellt dieser Dienst eine zentrale Stelle zum Konfigurieren dieser externen URLs und zum Erstellen dieser URLs bereit.

In diesem Artikel wird beschrieben, wie Sie den Externalizer-Dienst konfigurieren und wie er verwendet wird. Technische Details zum Dienst finden Sie unter [Javadocs](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/Externalizer.html).

## Standardverhalten des Externalisierers und Überschreiben von {#default-behavior}

Standardmäßig sind für den Externalizer-Dienst bereits Werte wie `author-p12345-e6789.adobeaemcloud.com` und `publish-p12345-e6789.adobeaemcloud.com` festgelegt, sodass Ihre AEM als Cloud Service-Installation ohne Eingreifen Ihre benutzerdefinierte Domäne verwendet.

Um diese Werte zu überschreiben, verwenden Sie die Cloud Manager-Umgebung-Variablen, wie im Artikel [OSGi für AEM als Cloud Service](/help/implementing/deploying/configuring-osgi.md#cloud-manager-api-format-for-setting-properties) konfigurieren und die vordefinierten Variablen `AEM_CDN_DOMAIN_AUTHOR` und `AEM_CDN_DOMAIN_PUBLISH` festlegen beschrieben.

## Konfigurieren des Externalizer-Dienstes {#configuring-the-externalizer-service}

Mit dem Externalizer-Dienst können Sie die Domäne zentral definieren, die zum programmatischen Präfix von Ressourcenpfaden verwendet werden kann. Der Externalizer-Dienst sollte nur für Anwendungen mit einer einzigen Domäne verwendet werden.

>[!NOTE]
>
>Wie beim Anwenden von [OSGi-Konfigurationen für AEM als Cloud Service sollten die folgenden Schritte für eine lokale Entwicklerinstanz ausgeführt und dann für die Bereitstellung an den Projektcode gebunden werden.](/help/implementing/deploying/overview.md#osgi-configuration)

Definieren Sie eine Domänenzuordnung für den Externalizer-Service wie folgt:

1. Navigieren Sie zum Configuration Manager über:

   `https://<host>:<port>/system/console/configMgr`

1. Klicken Sie auf **Day CQ Link Externalizer**, um das Konfigurationsdialogfeld zu öffnen.

   ![Externalizer OSGi-Konfiguration](./assets/externalizer-osgi.png)

   >[!NOTE]
   >
   >Der direkte Link zur Konfiguration ist `https://<host>:<port>/system/console/configMgr/com.day.cq.commons.impl.ExternalizerImpl`

1. Definieren Sie eine **Domänenzuordnung**. Eine Zuordnung besteht aus einem eindeutigen Namen, der im Code verwendet werden kann, um auf die Domäne, ein Leerzeichen und die Domäne zu verweisen:

   `<unique-name> [scheme://]server[:port][/contextpath]`

   wobei:

   * **`scheme`** ist normalerweise http oder https, kann aber ein anderes Protokoll sein.

      * Es wird empfohlen, HTTPS zum Erzwingen von HTTPS-Links zu verwenden.
      * Es wird verwendet, wenn der Client-Code das Schema nicht außer Kraft setzt, wenn eine externe URL angefordert wird.
   * **`server`** ist der Hostname (entweder ein Domänenname oder eine IP-Adresse).
   * **`port`** (optional) ist die Anschlussnummer.
   * **`contextpath`** (optional) wird nur festgelegt, wenn AEM als Webanwendung unter einem anderen Kontextpfad installiert wird.

   Beispiel: `production https://my.production.instance`

   Die folgenden Zuordnungsnamen sind vordefiniert und müssen immer so eingestellt werden, wie AEM davon abhängt:

   * `local` - die örtliche Instanz
   * `author` - das Authoring-System DNS
   * `publish` - die öffentlich zugängliche Website DNS

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
