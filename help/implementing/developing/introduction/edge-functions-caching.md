---
title: Caching in AEM Edge-Funktionen
description: Erfahren Sie, wie der CDN-Cache und der Edge-Funktionsabruf-Cache interagieren, wie Sie das Caching-Verhalten konfigurieren und zwischengespeicherte Inhalte über beide Ebenen hinweg bereinigen können.
feature: Developing, Edge Delivery Services
role: Developer
source-git-commit: b33a565d9623ed44309e1d34377345dae86757cd
workflow-type: tm+mt
source-wordcount: '1224'
ht-degree: 1%

---

# Caching in AEM Edge-Funktionen {#edge-functions-caching}

>[!IMPORTANT]
>
>AEM Edge Functions ist eine **Beta**-Funktion. Funktionen und Dokumentation können sich ohne Vorankündigung ändern. Um am Early-Access-Programm teilzunehmen und Feedback zu geben, senden Sie eine E-Mail an [aemcs-edgecompute-feedback@adobe.com](mailto:aemcs-edgecompute-feedback@adobe.com).

Auf dieser Seite finden Sie detaillierte technische Anleitungen dazu, wie das Caching in AEM Edge funktioniert, einschließlich der Zwei-Cache-Architektur, der Steuerung des Caching-Verhaltens in Ihrem Code und der Bereinigung von Cache-Einträgen bei Inhaltsänderungen.

Allgemeine Informationen zur Funktionsweise der AEM as a Cloud Service-Zwischenspeicherung finden Sie unter [Caching in AEM as a Cloud Service](/help/implementing/dispatcher/caching.md) und [Das CDN in AEM as a Cloud Service](/help/implementing/dispatcher/cdn.md). Code-Beispiele finden Sie im [AEM Edge Functions Boilerplate - Caching](https://github.com/adobe/aem-edge-functions-boilerplate/blob/main/README.md#caching).

## Caching-Architektur {#architecture}

AEM Edge-Funktionen befinden sich zwischen dem CDN und den Backend-Services, von denen die Funktion abgerufen wird. Bei diesen Backends kann es sich um AEM-Veröffentlichungsinstanzen, Drittanbieter-APIs, externe Datenbanken oder einen beliebigen HTTP-Endpunkt handeln, den Ihr Code aufruft. Es gibt **zwei verschiedene Caches** im Anfragefluss, von denen jeder unabhängig arbeitet:

```
Browser → AEM CDN (CDN Cache) → AEM Edge Functions (Fetch Cache) → Backend (AEM, APIs, etc.)
```

| Cache | Was zwischengespeichert wird | Beeinflusst durch | Bereinigen |
|---|---|---|---|
| **CDN-Cache** | Die Antwort der Edge-Funktion auf den Browser | Von der Edge-Funktion festgelegte Antwort-Header (`Cache-Control`, `Surrogate-Control`, `Surrogate-Key`) | [CDN Cache Purge API](/help/implementing/dispatcher/cdn-cache-purge.md) |
| **Cache für Edge-Funktionsabruf** | Backend-Antworten auf `fetch()`-Aufrufe innerhalb der Edge-Funktion und über die Core-Cache-API gespeicherte Daten | Backend-Antwort-Header, `CacheOverride` bei Abrufaufrufen oder programmgesteuerte Ersatzschlüssel über die Core Cache API | `aio aem edge-functions purge-cache` CLI-Befehl oder `purgeSurrogateKey()` |

Das Verständnis dieser zweischichtigen Architektur ist wichtig, da jeder Cache einen anderen Umfang, andere Steuerelemente und einen anderen Bereinigungsmechanismus hat. Eine effektive Zwischenspeicherung erfordert eine gezielte Konfiguration auf beiden Ebenen.

## CDN-Cache (außen) {#cdn-cache}

Der CDN-Cache befindet sich zwischen dem Browser und der Edge-Funktion. Es wird die (Antwort **der Edge-Funktion**. Sie steuern sein Verhalten, indem Sie standardmäßige HTTP-Cache-Header für Ihre Edge-Funktionsantworten festlegen:

```js
return new Response(body, {
  headers: {
    'Surrogate-Key': 'page-home product-123',
    'Cache-Control': 'public, max-age=3600'
  }
});
```

Mehrere Ersatzschlüssel werden durch Leerzeichen getrennt. Diese Ersatzschlüssel können verwendet werden, um den CDN-Cache mithilfe der [CDN Cache Purge API) zu &#x200B;](/help/implementing/dispatcher/cdn-cache-purge.md). Das Konzept der Löschung von Ersatzschlüsseln ist dasselbe wie unter [Bereinigen des Caches für eine Gruppe von Ressourcen](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/caching/how-to/purge-cache#purge-the-cache-for-a-group-of-resources) beschrieben. Der wesentliche Unterschied besteht darin, dass die CDN-Ersatzschlüssel hier durch Ihren Edge-Funktions-Code festgelegt werden und nicht durch das Backend.

## Edge, Funktion Zwischenspeicher abrufen (innere) {#fetch-cache}

Der Cache zum Abrufen von Edge-Funktionen befindet sich zwischen der Edge-Funktion und den von ihr aufgerufenen Backends. Er speichert die **Antwort des Backends** in `fetch()` Aufrufe, die innerhalb Ihres Edge-Funktions-Codes getätigt werden. Es enthält auch alle Daten, die Ihr Code über die [**Core Cache API**](https://js-compute-reference-docs.edgecompute.app/docs/fastly:cache/CoreCache) oder [**Simple Cache API**](https://js-compute-reference-docs.edgecompute.app/docs/fastly:cache/SimpleCache) speichert - programmgesteuerte Caching-Schnittstellen, die Ihnen eine genaue Kontrolle darüber geben, was wie lange und unter welchen Ersatzschlüsseln zwischengespeichert wird.

Sie wird **nicht** durch Kopfzeilen beeinflusst, die Sie in der ausgehenden Antwort der Edge-Funktion festlegen - nur durch die Antwort-Kopfzeilen des Backends, durch [`CacheOverride`](https://js-compute-reference-docs.edgecompute.app/docs/fastly:cache-override/CacheOverride/) von Optionen in Ihren Abrufaufrufen oder durch Ersatzschlüssel, die Sie beim Schreiben in die Core-Cache-API programmgesteuert zuweisen.

>[!NOTE]
>
>Der `Surrogate-Key`-Header, den Sie in der (ausgehenden *Antwort) Ihrer Edge* Funktion an den Browser festlegen, steuert den **äußeren CDN-Cache**, nicht diesen inneren Cache. Ersatzschlüssel für den inneren Cache stammen aus dem `Surrogate-Key`-Antwort-Header des Backends oder aus Schlüsseln, die Sie beim Schreiben in die Core-Cache-API zuweisen.

### Caching von Backend-Antworten {#cache-override}

So speichern Sie Backend-Antworten für eine bestimmte Dauer zwischen:

```js
import { CacheOverride } from "fastly:cache-override";

const response = await fetch(request, {
  backend: "my-origin",
  cacheOverride: new CacheOverride({ ttl: 300 })
});
```

### Umgehen des Cache {#cache-pass}

Um den Abrufcache vollständig zu umgehen und immer aus dem Backend abzurufen, verwenden Sie `pass`:

```js
import { CacheOverride } from "fastly:cache-override";

const response = await fetch(request, {
  backend: "my-origin",
  cacheOverride: new CacheOverride({ mode: "pass" })
});
```

## Cache-Bereinigung {#cache-purging}

Wenn zwischengespeicherte Inhalte veraltet sind, müssen Sie sie explizit bereinigen. Da die beiden Caches unabhängig voneinander arbeiten, ist es wichtig zu verstehen, welche Ebene Sie invalidieren und wie sie interagieren.

### Koordinieren von Bereinigungen über beide Ebenen hinweg {#coordinating-purges}

Da die Edge-Funktion sich als Backend hinter dem CDN befindet (erreichbar über [Origin-Selektoren](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors)), kann das Bereinigen einer Cache-Ebene ohne die andere zu unerwarteten Ergebnissen führen:

1. **Nur den CDN-Cache bereinigen** ruft die nächste Anfrage die Edge-Funktion auf. Wenn der Abruf-Cache der Edge-Funktion weiterhin veraltete Daten enthält, gibt er alte Inhalte zurück, die dann vom CDN erneut zwischengespeichert werden.
2. **Nur den Edge-Funktions-Cache bereinigen** löscht den internen Status, aber das CDN stellt seine zuvor zwischengespeicherte Kopie weiter bereit, bis sie abläuft oder separat bereinigt wird.

**Best Practice:** Bei zugrunde liegenden Datenänderungen, Bereinigen **beide** Caches - Verwenden Sie die CDN Cache Purge API für die äußere Ebene und `purge-cache` (oder `purgeSurrogateKey()`) für die innere Edge-Funktionsebene. Die Verwendung konsistenter Ersatzschlüssel auf beiden Ebenen vereinfacht die koordinierte Invalidierung. Ein vollständiges Beispiel für dieses Muster finden Sie unter [AEM Edge Functions Boilerplate - Purging](https://github.com/adobe/aem-edge-functions-boilerplate/blob/main/README.md#purging-the-edge-function-fetch-cache).

### Bereinigen des CDN-Cache {#purge-cdn-cache}

Um den äußeren CDN-Cache zu bereinigen (die auf CDN-Ebene zwischengespeicherte Antwort der Edge-Funktion), verwenden Sie die [CDN Cache Purge API](/help/implementing/dispatcher/cdn-cache-purge.md). Dies ist derselbe Bereinigungsmechanismus, der für alle im CDN zwischengespeicherten AEM as a Cloud Service-Inhalte verwendet wird - siehe [Bereinigen des CDN-Cache](https://experienceleague.adobe.com/de/docs/experience-manager-learn/cloud-service/caching/how-to/purge-cache) für eine schrittweise Anleitung.

In der AEM as a Cloud Service-Architektur empfangen Edge-Funktionen Traffic vom CDN über [Ursprungsselektoren](/help/implementing/dispatcher/cdn-configuring-traffic.md#origin-selectors) (siehe auch [CDN-Routing](/help/implementing/developing/introduction/edge-functions.md#cdn-routing)). Der vollständige Anfragefluss ist:

```
Client → AEM CDN (VCL) → Origin Selector → Edge Function → Backend
```

Das CDN speichert die endgültige Antwort zwischen, die von der Edge-Funktion zurückgegeben wird. Eine CDN-Bereinigung löscht **nur** diese äußere zwischengespeicherte Antwort - sie hat keine Auswirkungen auf die internen Caches der Edge-Funktion.

### Löschen des Cache für Edge-Funktionsabrufe {#purge-fetch-cache}

Der `purge-cache` CLI-Befehl löscht den **Cache für den Abruf der Edge-Funktion** (die Backend-Antworten, die innerhalb der Edge-Funktion zwischengespeichert wurden). Der äußere CDN **Cache wird** gelöscht. Vollständige CLI-Optionen und -Flags finden Sie in der [`purge-cache`-Befehlsreferenz](https://github.com/adobe/aio-cli-plugin-aem-edge-functions/blob/main/README.md#purge-cache).

#### Woher die Ersatzschlüssel kommen {#surrogate-key-origin}

Ersatzschlüssel, die in Bereinigungsbefehlen verwendet werden, müssen mit den Schlüsseln übereinstimmen, die **im zwischengespeicherten Inhalt zum Zeitpunkt seiner Speicherung getaggt waren**. Dies entspricht dem Konzept der [schlüsselbasierten Ersatzbereinigung](/help/implementing/dispatcher/cdn-cache-purge.md#surrogate-key-purge), das im AEM CDN verwendet wird, wird aber auf den internen Cache der Edge-Funktion angewendet. Diese Schlüssel stammen aus:

- Der `Surrogate-Key` Antwort-Header, den das Backend zurückgibt, wenn die Edge-Funktion daraus abruft.
- Schlüssel, die Sie beim Schreiben in die [Core Cache API](https://js-compute-reference-docs.edgecompute.app/docs/fastly:cache/CoreCache) programmgesteuert zuweisen (z. B. über die Option `surrogateKeys` beim Einfügen eines Cache-Eintrags).

Wenn Ihr Backend beispielsweise mit antwortet:

```
HTTP/1.1 200 OK
Content-Type: text/html
Surrogate-Key: page-about product-456 category-shoes
Cache-Control: public, max-age=3600
```

Anschließend wird die zwischengespeicherte Antwort mit drei Ersatzschlüsseln getaggt: `page-about`, `product-456` und `category-shoes`. Sie können sie später mit einem dieser Schlüssel bereinigen:

```bash
# Purge all cached content tagged with "product-456"
aio aem edge-functions purge-cache <function-name> --surrogateKey product-456

# Purge multiple keys at once
aio aem edge-functions purge-cache <function-name> -k page-about -k category-shoes
```

>[!TIP]
>
>Wählen Sie Namenskonventionen für Ersatzschlüssel aus, die Ihrem Inhaltsmodell zugeordnet sind, z. B. nach Seitenpfad (`page-about`), Inhalts-ID (`product-456`) oder Inhaltstyp (`category-shoes`). Dadurch wird die gezielte Cache-Invalidierung bei Inhaltsänderungen intuitiv.

#### Alle bereinigen {#purge-all}

```bash
# Purge all cached content (use with caution)
aio aem edge-functions purge-cache <function-name> --all
```

#### Soft Purge {#soft-purge}

Verwenden Sie das `--soft`-Flag, um eine Soft Purge durchzuführen, bei der veraltete Einträge im Cache beibehalten werden und die Backend-Last reduziert wird, während eine veraltete erneute Überprüfung aktiviert wird:

```bash
aio aem edge-functions purge-cache <function-name> --surrogateKey product-456 --soft
```

#### Bereinigung {#programmatic-purge}

Sie können Ersatzschlüssel auch programmgesteuert aus Ihrem Edge-Funktions-Code löschen, indem Sie [`purgeSurrogateKey`](https://js-compute-reference-docs.edgecompute.app/docs/fastly:compute/purgeSurrogateKey) verwenden:

```js
import { purgeSurrogateKey } from "fastly:compute";

// Hard purge (immediate removal)
purgeSurrogateKey("product-456");

// Soft purge (retain stale entries for revalidation)
purgeSurrogateKey("product-456", true);
```

>[!CAUTION]
>
>Das Löschen aller zwischengespeicherten Inhalte erhöht den Traffic an Backends. Verwenden Sie das `--all`-Flag sorgfältig und bevorzugen Sie nach Möglichkeit gezielte Löschungen von Ersatzschlüsseln.