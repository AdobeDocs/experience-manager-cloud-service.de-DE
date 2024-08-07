---
title: Ressourcenzuordnung
description: Erfahren Sie, wie Sie mithilfe der Ressourcenzuordnung Umleitungen, Vanity-URLs und virtuelle Hosts für AEM definieren.
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
feature: Configuring
exl-id: 1a1bb23c-d1d1-4e2b-811b-753e6a90a01b
role: Admin
source-git-commit: f66ea281e6abc373e9704e14c97b77d82c55323b
workflow-type: tm+mt
source-wordcount: '526'
ht-degree: 100%

---

# Ressourcenzuordnung{#resource-mapping}

Die Ressourcenzuordnung wird verwendet, um Umleitungen, Vanity-URLs und virtuelle Hosts für AEM zu definieren.

Diese Zuordnungen können Sie beispielsweise verwenden, um:

* Allen Anfragen das Präfix `/content` voranzustellen, sodass die interne Struktur für Besucher Ihrer Website ausgeblendet wird.
* Eine Umleitung zu definieren, sodass alle Anfragen an die Seite `/content/en/gateway` Ihrer Website zu `https://gbiv.com/` umgeleitet werden.

Bei einer möglichen HTTP-Zuordnung wird allen Anfragen an `localhost:4503` das Präfix `/content` vorangestellt. Eine solche Zuordnung kann zum Ausblenden der internen Struktur für die Besucher der Website verwendet werden, da sie den Zugriff auf:

`localhost:4503/content/we-retail/en/products.html`

über:

`localhost:4503/we-retail/en/products.html`

erlaubt, da bei der Zuordnung automatisch das Präfix `/content` zu `/we-retail/en/products.html` hinzufügt wird.

>[!CAUTION]
>
>Vanity-URLs unterstützen keine Regex-Muster.

>[!NOTE]
>
>Weitere Informationen finden Sie in der Sling-Dokumentation sowie unter [Zuordnungen für die Ressourcenauflösung](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html) und [Ressourcen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html).

## Anzeigen von Zuordnungsdefinitionen {#viewing-mapping-definitions}

Die Zuordnungen bilden zwei Listen, die der JCR-Ressourcen-Resolver auswertet (von oben nach unten), um eine Übereinstimmung zu finden.

Diese Listen können (zusammen mit Konfigurationsinformationen) unter der Option **JCR ResourceResolver** der Felix-Konsole angezeigt werden. Beispiel: `https://<*host*>:<*port*>/system/console/jcrresolver`:

* Configuration
Zeigt die aktuelle Konfiguration (wie für den [Apache Sling-Ressourcen-Resolver](/help/overview/seo-and-url-management.md#etc-map) definiert) an.

* Konfigurationstest
Hiermit können Sie eine URL oder einen Ressourcenpfad eingeben. Klicken Sie auf **Resolve** oder **Map**, um festzulegen, wie das System den Eintrag transformiert.

* **Resolver Map Entries**
Die Liste der Einträge, die von den ResourceResolver.resolve-Methoden für die Zuordnung von URLs zu Ressourcen verwendet wird.

* **Mapping Map Entries**
Die Liste der Einträge, die von den ResourceResolver.map-Methoden für die Zuordnung von Ressourcenpfaden zu URLs verwendet wird.

Die beiden Listen enthalten verschiedene Einträge, darunter die Einträge, die von den Anwendungen als Standardwerte definiert sind. Diese Einträge zielen häufig darauf ab, URLs für Benutzende zu vereinfachen.

Das Listen paaren ein **Muster**, d. h. einen regulären Ausdruck, der mit der Anfrage übereinstimmt, mit einem **Ersatz**, der die Umleitung definiert, die durchgesetzt werden soll.

Zum Beispiel löst das

**Muster** `^[^/]+/[^/]+/welcome$`

den

**Ersatz** `/libs/cq/core/content/welcome.html` aus.

aus, zur Umleitung der Anfrage

`https://localhost:4503/welcome` ``

an:

`https://localhost:4503/libs/cq/core/content/welcome.html`

Neue Zuordnungsdefinitionen werden im Repository erstellt.

>[!NOTE]
>
>Es steht eine Vielzahl von Ressourcen zur Verfügung, die das Definieren regulärer Ausdrücke erläutern, z. B. [https://www.regular-expressions.info/](https://www.regular-expressions.info/).

### Erstellen von Zuordnungsdefinitionen in AEM {#creating-mapping-definitions-in-aem}

In einer Standardinstallation von AEM finden Sie den Ordner:

`/etc/map/http`

Dieser Ordner ist die Struktur, die beim Definieren von Zuordnungen für das HTTP-Protokoll verwendet wird. Wenn Sie Zuordnungen für weitere Protokolle erstellen möchten, können unter `/etc/map` weitere Ordner (`sling:Folder`) erstellt werden.

#### Konfigurieren einer internen Umleitung an /content {#configuring-an-internal-redirect-to-content}

So erstellen Sie eine Zuordnung, die allen Anfragen an https://localhost:4503/ das Präfix `/content` voranstellt:

1. Navigieren Sie mithilfe von CRXDE zu `/etc/map/http`.

1. Erstellen Sie einen Knoten:

   * **Typ** `sling:Mapping`
Der Knotentyp ist für diese Zuordnungen bestimmt, seine Verwendung ist jedoch nicht obligatorisch.

   * **Name** `localhost_any`

1. Klicken Sie auf **Alle speichern**.
1. **Fügen Sie diesem Knoten die folgenden Eigenschaften hinzu:**

   * **Name** `sling:match`

      * **Typ** `String`

      * **Wert** `localhost.4503/`

   * **Name** `sling:internalRedirect`

      * **Typ** `String`

      * **Wert** `/content/`

1. Klicken Sie auf **Alle speichern**.

Diese Zuordnung verarbeitet eine Anfrage wie
`localhost:4503/geometrixx/en/products.html`,
als wenn
`localhost:4503/content/geometrixx/en/products.html`
angefordert worden wäre.

>[!NOTE]
>
>Weitere Informationen zu den verfügbaren Sling-Eigenschaften und dazu, wie diese konfiguriert werden können, finden Sie in der Sling-Dokumentation unter [Ressourcen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)
>Beispielsweise ist eine [Zeichenfolgeninterpolation](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html#string-interpolation-for-etcmap) sehr nützlich, da sie es ermöglicht, eine Zuordnung zu konfigurieren, die Umgebungswerte durch Umgebungsvariablen erhält.

>[!NOTE]
>
>Die Konfigurationen für die Publishing-Umgebung können unter `/etc/map.publish` gespeichert werden. Diese Konfigurationen müssen dann repliziert werden, und der neue Speicherort (`/etc/map.publish`) muss für den **Zuordnungsspeicherort** des [Apache Sling Resource Resolver](/help/overview/seo-and-url-management.md#etc-map) der Publishing-Umgebung konfiguriert werden.
