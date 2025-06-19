---
title: Komponenten- und GraphQL-Cache löschen
description: Erfahren Sie, wie Sie die Funktion „Clear-Cache“ in AEM CIF aktivieren und überprüfen.
feature: Commerce Integration Framework
role: Admin
exl-id: f89c07c7-631f-41a4-b5b9-0f629ffc36f0
source-git-commit: fb8b2645c0401d1358c7751db03a138dc2de2664
workflow-type: tm+mt
source-wordcount: '883'
ht-degree: 2%

---

# Komponenten- und GraphQL-Cache löschen {#clear-cache}

Dieses Dokument enthält eine umfassende Anleitung zum Aktivieren und Überprüfen der Funktion „Cache löschen“ in AEM CIF.

>[!NOTE]
>
> Diese Funktion ist experimentell.

## Aktivieren der Funktion „Cache löschen“ in der CIF-Konfiguration {#enable-clear-cache}

Standardmäßig ist die Funktion „Cache löschen“ in der CIF-Konfiguration deaktiviert. Um ihn zu aktivieren, müssen Sie den entsprechenden Projekten Folgendes hinzufügen:

* Aktivieren Sie das Servlet-`/bin/cif/invalidate-cache`, mit dem Sie die Clear-Cache-API mit den entsprechenden Anfragen auslösen können, indem Sie die `com.adobe.cq.cif.cacheinvalidation.internal.InvalidateCacheNotificationImpl.cfg.json`-Konfiguration in Ihrem Projekt hinzufügen, wie [hier](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config.author/com.adobe.cq.cif.cacheinvalidation.internal.InvalidateCacheNotificationImpl.cfg.json) dargestellt.
  >[!NOTE]
  >
  > Die Konfiguration muss nur für die Autoreninstanzen aktiviert werden.

* Aktivieren Sie den Listener, um den Cache jeder Instanz von AEM (Veröffentlichungs- und Autoreninstanz) zu löschen, indem Sie die `com.adobe.cq.commerce.core.cacheinvalidation.internal.InvalidateCacheSupport.cfg.json` Konfiguration in Ihrem Projekt hinzufügen, wie [hier](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.core.cacheinvalidation.internal.InvalidateCacheSupport.cfg.json) dargestellt.
   * Die Konfiguration sollte sowohl für die Autoren- als auch für die Veröffentlichungsinstanz aktiviert sein.
   * Aktivieren des Dispatcher-Caches (optional): Sie können die Einstellung „Dispatcher-Cache löschen“ aktivieren, indem Sie in der obigen Konfiguration die `enableDispatcherCacheInvalidation`-Eigenschaft auf „true“ festlegen. Dies bietet die Möglichkeit, den Cache vom Dispatcher zu löschen.
     >[!NOTE]
     >
     > Dies funktioniert nur mit Veröffentlichungsinstanzen.

   * Stellen Sie außerdem sicher, dass Sie das entsprechende Muster angeben, das Ihrem Produkt, Ihrer Kategorie und Ihrer CMS-Seite entspricht. Es muss der obigen Konfigurationsdatei hinzugefügt werden, um es aus dem Dispatcher-Cache zu entfernen.

* Um die Leistung von SQL-Abfragen beim Suchen der entsprechenden Seite für Produkt und Kategorie zu verbessern, fügen Sie den entsprechenden Index in Ihrem Projekt hinzu (empfohlen). Weitere Informationen finden Sie unter [cifCacheInvalidationSupport](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.apps/src/main/content/jcr_root/_oak_index/cifCacheInvalidationSupport/.content.xml).

## Überprüfen der Funktion „Cache löschen“ {#verify-clear-cache}

So überprüfen Sie, ob alles ordnungsgemäß eingerichtet ist:

* Fügen Sie den Trigger des entsprechenden Servlets zur AEM der Autoreninstanz hinzu, z. B. [http://localhost:4502/bin/cif/invalidate-cache](http://localhost:4502/bin/cif/invalidate-cache). Sie sollten daraufhin eine HTTP-Antwort von 200 erhalten.
* Stellen Sie sicher, dass in Autoreninstanzen unter dem folgenden Pfad ein Knoten erstellt wurde: `/var/cif/cacheinvalidation`. Der Knotenname folgt diesem Muster: `cmd_{{timestamp}}`.
* Stellen Sie sicher, dass in jeder Veröffentlichungsinstanz derselbe Knoten erstellt wurde.

So überprüfen Sie nun, ob die Caches ordnungsgemäß geleert werden:
1. Navigieren Sie zu den entsprechenden PLP- und PDP-Seiten.
2. Aktualisieren eines Produkt- oder Kategorienamens in der Commerce-Engine. Die Änderungen werden basierend auf Cache-Konfigurationen nicht sofort in AEM übernommen.
3. Trigger der Servlet-API, wie hier gezeigt:

   ```
   curl --location '{Author AEM Instance Url}/bin/cif/invalidate-cache' \
   --header 'Content-Type: application/json' \
   --header 'Authorization: ••••••' \ // Mandatory
   --header 'Cookie: private_content_version=0299c5e4368a1577a6f454a61370317b' \
   --data '{
       "productSkus": ["Sku1", "Sku2"], // Optional: Pass the corresponding sku which got updated.
       "categoryUids":["CategoryUid"], // Optional : Pass the corresponding category-uid which got updated.
       "storePath": "/content/venia/us/en", // Mandatory : Needs to be given to know for which site we are removing the clear cache.
   }'
   ```
Wenn alles gut geht, werden die neuen Änderungen in jedem Fall widergespiegelt. Wenn die Änderungen in der Veröffentlichungsinstanz nicht sichtbar sind, versuchen Sie, die relevanten PLP- und PDP-Seiten in einem privaten/Inkognito-Browser-Fenster aufzurufen.

>[!NOTE]
>
> Veröffentlichungsinstanzen können über mehrere Cache-Ebenen verfügen. Die Funktion ist nur für das Löschen des Cache aus dem internen Speicher und Dispatcher von AEM verantwortlich.

## Cache-Invalidierungs-API löschen {#clear-cache-api}

Dies ist die API, die Sie zum Löschen des Triggers von Commerce-bezogenen Daten aus AEM verwenden müssen.

Anfragetyp: `POST`

### Kopfzeilen

| Parameter | Wert  | Erforderlich/Obligatorisch | Kommentar |
|------------------------------|-------------------|---|---|
| `Content-Type` | `application/json` | Erforderlich |  |
| `Authorization` | Entsprechende Benutzeranmeldeinformationen des Autors (Authentifizierungstyp: Standardauthentifizierung) | Erforderlich | Fügen Sie den entsprechenden Benutzernamen und das Passwort hinzu. |


### Payload

Die folgende Tabelle zeigt die vorhandenen Attribute, die die Funktion standardmäßig bereitstellt. Diese `InvalidateType` Eigenschaften müssen in Kombination mit einem obligatorischen Attribut angegeben werden (z. B. `storePath`).

| `invalidateType` | Wert | Typ (Array/String/Boolean) | Löscht dies den Dispatcher-Cache? | Kommentar |
|------------------------------|-------------------|---|---|---|
| `productSkus` | Produkt-SKU - , die im Cache ungültig gemacht werden muss. | Array | Ja | Löschen Sie den Cache aus dem internen Speicher nach dem folgenden Muster: <br>```"\"sku\":\\s*\""```<br>Dispatcher<br><ul><li>Löschen Sie den PDP-Seiten-Cache der entsprechenden SKUs</li><li>Cache der entsprechenden Kategorieseite löschen, in der sie vorhanden sind (basierend auf der GraphQL-Antwort von Commerce)</li><li>Löschen Sie den Cache basierend auf der folgenden Abfrage:</li></ul><br>```SELECT content.[jcr:path] FROM [nt:unstructured] AS content<br>WHERE ISDESCENDANTNODE(content, '{storePath}')<br>AND ( (content.[product] IN ('sku1','sku2') AND content.[productType] = 'combinedSku')<br> OR (content.[selection] IN ('sku1','sku2') AND content.[selectionType] IN ('combinedSku', 'sku')))``` |
| `categoryUids` | Die UID der Kategorie - die im Cache ungültig gemacht werden muss. | Array | Ja | Löschen Sie den Cache aus dem internen Speicher nach dem folgenden Muster: <br>```"\"uid\"\\s*:\\s*\\{\"id\"\\s*:\\s*\""```<br>Dispatcher<br><ul><li>Löschen des Kategorieseiten-Cache für entsprechende Daten (einschließlich der untergeordneten Kategorieseite)</li><li>Löschen Sie alle PDP-Seiten mit den entsprechenden Kategorien</li><li>Löschen Sie den Cache basierend auf der folgenden Abfrage:</li></ul><br>```SELECT content.[jcr:path] FROM [nt:unstructured] AS content<br>WHERE ISDESCENDANTNODE(content,'{storePath}')<br>AND ((content.[categoryId] in ('category1','category2')<br>AND content.[categoryIdType] in ('uid'))<br>OR (content.[category] in ('category1','category2') AND content.[categoryType] in ('uid')))``` |
| `regexPatterns` | Wenn Sie die GraphQL-Antwortdaten basierend auf dem Regex-Muster löschen müssen, verwenden Sie dies. | Array | Nein | |
| `cacheNames` | Diese Werte werden unter der entsprechenden CIF GraphQL Client Configuration Factory > Entsprechende StorePath-GraphQL-Konfiguration > GraphQL-Cache-Konfigurationen definiert | Array | Nein | |
| `invalidateAll` | Wahr oder falsch | Boolesch | Ja | |

In dieser Tabelle wird die obligatorische Eigenschaft angezeigt, die bei jedem API-Aufruf übergeben werden muss:

| Eigenschaft | Wert | Typ (Array/String/Boolean) | Löscht dies den Dispatcher-Cache? | Kommentar |
|------------------------------|-------------------|---|---|---|
| `storePath` | Entsprechender Wert des Site-Pfads, aus dem der Cache entfernt werden muss (Beispiel: `/content/venia/us/en` als Referenz mit dem Venia-Projekt). | Zeichenfolge | Ja | Dies muss zusammen mit der Kombination aus `invalidateType.` angewendet werden |

### Beispiel einer API-Anfrage

```
curl --location 'https://author-p10603-e145552-cmstg.adobeaemcloud.com/bin/cif/invalidate-cache' \
--header 'Content-Type: application/json' \
--header 'Authorization: ••••••' \
--header 'Cookie: private_content_version=0299c5e4368a1577a6f454a61370317b' \
--data '{
"productSkus": ["VP01", "VT10"], // This will clear cache for the corresponding pages related with mentioned skus.
"categoryUids":["Mjk="], // This will clear cache for the corresponding pages related with mentioned categories.
"regexPatterns":["\"uid\"\\s*:\\s*\\{\"id\"\\s*:\\s*\"(Mjk=)\"", "\"sku\":\\s*\"(VP02|VP03)\""],
"cacheNames": ["venia/components/commerce/product"], // If this been added then it will clear respective caches for the corresponding storepath
"storePath": "/content/venia/us/en"
}'
```

## Erweiterbarkeit {#clear-cache-extensibility}

Diese Funktion bietet nicht nur ihre Kernfunktionen, sondern auch Erweiterbarkeit, sodass Entwickler sie nach Bedarf weiter nutzen und anpassen können.

### Erweitern des vorhandenen Attributs {#existing-attribute}

Wenn der Cache gelöscht werden muss, die derzeit nicht von den vorhandenen attributbasierten Funktionen abgedeckt sind (z. B. `categoryUids`), können Sie [diese Referenzdatei) ](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/ExtendedCategoryUidInvalidation.java), um neue Muster hinzuzufügen und zusätzliche `invalidatePaths` zu definieren, die über die aktuellen Implementierungen hinaus aus dem Cache gelöscht werden sollen.

### Hinzufügen eines neuen benutzerdefinierten Attributs {#new-custom-attribute}

Wenn Sie beispielsweise das vorhandene Attribut nicht zum Löschen des Cache verwenden möchten, haben Sie die Flexibilität, Ihr eigenes Attribut zu erstellen und die entsprechende Funktionalität zu definieren.

* Wenn Sie nur den Cache aus dem internen Speicher von AEM löschen müssen (die GraphQL-Antwort), müssen Sie [diese Referenz](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/CustomInvalidation.java) folgen.
* Wenn Sie den Cache aus dem internen Speicher und dem Dispatcher-Cache löschen müssen, müssen Sie [diese Referenz](https://github.com/adobe/aem-cif-guides-venia/blob/main/core/src/main/java/com/venia/core/models/commerce/services/cacheinvalidation/CustomDispatcherInvalidation.java) folgen.
  >[!NOTE]
  >
  > Sie können den internen Cache zum Löschen ignorieren, indem Sie `null` für die `getPatterns()` Methode zurückgeben.
