---
title: Visuelle Inhaltsfragmente - Versand über die Veröffentlichungs-URL
description: Verwenden Sie die Veröffentlichungs-URL, um visuelle Inhaltsfragmente bereitzustellen.
feature: Developing, Content Fragments
role: Admin, Developer
source-git-commit: 733e7a8c497fcffdfadd22c2abd3323d35d54e3e
workflow-type: tm+mt
source-wordcount: '1435'
ht-degree: 0%

---


# Visuelle Inhaltsfragmente - Versand über die Veröffentlichungs-URL {#visual-content-fragments-deliver-with-the-publish-url}

Beim Veröffentlichen eines Inhaltsfragments, das auf einem Modell mit angehängten HTML-Vorlagen basiert, wird die gerenderte HTML dieses Fragments über die as a Cloud Service-Veröffentlichungsebene von Adobe Experience Manager (AEM) unter einer URL dieser Struktur verfügbar gemacht:

```html
https://publish-p<programId>-e<envId>.adobeaemcloud.com/adobe/stable/previewtemplates/contentFragments/<templateId>/<fragmentId>/<variation>.html
```

Diese URL gibt ein *eigenständiges HTML-Dokument* (einschließlich Inline-CSS und -Struktur) zurück, das in jeden Web-Kontext eingebettet werden kann.

## Einbettungstechniken - Übersicht {#embedding-techniques-overview}

Es gibt drei verschiedene Ansätze, um HTML aus einem visuellen Inhaltsfragment auf einer Hostseite zu verwenden. Jede Version weist unterschiedliche Merkmale in Bezug auf Stilistische Isolation, Layout-Verhalten, Barrierefreiheit und Komplexität auf.

| | Inline-Element | iframe | Benutzerdefiniertes Element + Shadow-DOM |
|--- |--- |--- |--- |
| Mechanismus | `fetch()` Sie die URL und fügen Sie die Antwort-HTML über `innerHTML` in eine `<div>` ein | `<iframe src="publishURL">` | Definieren eines benutzerdefinierten Elements `fetch()` der HTML, das in einen angehängten Shadow-DOM-Stamm eingefügt wird |
| Stilistische Isolierung | Keine - Fragment-CSS sickert in die Host-Seite und Host-CSS wirkt sich auf das Fragment aus | Vollständig - separater Browserkontext, vollständige CSS-Isolierung | Stark - Schatten-DOM-Grenzblöcke hosten CSS-kaskadierend; Fragmentstile bleiben verkapselt |
| Layout-Beteiligung | Vollständig - Der Inhalt ist Teil des normalen Dokumentflusses und reagiert auf die Größe von Flexbox/Raster/Container | Keine - iframe hat feste Abmessungen; erfordert explizites `width`/`height` oder JS-basierte automatische Größenanpassung | Vollständig - Das benutzerdefinierte Element ist wie jedes andere DOM-Element am normalen Fluss des Host-Dokuments beteiligt |
| Barrierefreiheit (a11y) | Best - Inhalte befinden sich im Haupt-DOM-Baum und können von Sprachausgaben und Hilfstechnologien vollständig durchlaufen werden. | Mittelmäßig - Separater Browserkontext kann die Navigation der Bildschirmlesehilfe verwirren; erfordert `title` Attribut | Gut - Inhalte befinden sich im selben Dokument; das Schatten-DOM kann von modernen Hilfstechnologien durchlaufen werden |
| SEO | Schlecht - über JS `fetch()` geladene Inhalte werden von den meisten Crawler nicht indiziert | Schlecht - iFrame-Inhalte werden normalerweise nicht im übergeordneten Seitenkontext indiziert | Schlecht - identisch mit Inline; von JS abgerufene Inhalte sind nicht durchsuchbar |
| JavaScript-Laufzeit | Gemeinsam - Derselbe Fenster-/Dokumentkontext; Risiko von Skriptkollisionen, wenn das Fragment `<script>` Tags enthält | Isoliert — separater Fensterkontext; keine Kollisionsgefahr | Shared - Derselbe Fensterkontext, aber DOM-Bereich; Skripte innerhalb des Schattenstamms werden im Hostkontext ausgeführt |
| Ursprungsübergreifende Unterstützung | CORS-Header für die Veröffentlichungs-URL erforderlich (der Service konfiguriert diese) | Funktioniert nativ - iFrames laden ursprungsübergreifende Inhalte ohne CORS | CORS-Header für die Veröffentlichungs-URL erforderlich (identisch mit Inline-Headern) |
| Komplexität der Implementierung | Minimal - einige Zeilen JS | Trivial - Null JS erforderlich; reine HTML | Niedrig - ca. 20 Zeilen JS für die Definition benutzerdefinierter Elemente, wiederverwendbar über die Seite hinweg |
| Am besten geeignet für | Prototypen, vertrauenswürdige Inhalte derselben Herkunft, Kontexte, in denen die Layout-Integration wichtig ist und CSS-Konflikte bewältigt werden können | Schnelle Einbettung, Sandbox-Inhalte, ursprungsübergreifende Szenarien, in denen CORS nicht verfügbar ist, Inhalte, die vollständig isoliert werden müssen | Produktionsverwendung - Schränkt Isolation, Layout-Beteiligung und Barrierefreiheit ein (empfohlen für AEM-Kernkomponenten und externe Sites) |

### Inline-Element (fetch + innerHTML) {#inline-element-fetch-and-innerhtml}

Der einfachste Ansatz:

1. Abrufen der Veröffentlichungs-URL
1. Fügen Sie HTML in ein Container-Element ein

Beispiel für das Einbetten von Inline-Elementen:

```html
<div id="cf-container"></div>
<script>
  fetch("<publish-url>")
    .then(r => r.ok ? r.text() : Promise.reject(r.status))
    .then(html => {
      document.getElementById("cf-container").innerHTML = html;
    })
    .catch(err => console.error("Failed to load fragment", err));
</script>
```

Verwendung:

* Rapid Prototyping oder Proof-of-Concept-Seiten
* Kontexte derselben Herkunft, in denen Sie sowohl die Host-Seite als auch die Fragmentstile steuern
* Wenn maximale Layout-Flexibilität wichtiger ist als Stilkapselung

>[!CAUTION]
>
>**CSS-Kollisionsrisiko**
>
>Die Inline-Stile des Fragments (einschließlich der `<style>`, Schriftdeklarationen und Elementauswahlen) werden in die Kaskade der Host-Seite eingebunden.
>
>Dies kann zu unbeabsichtigten Stilüberschreibungen in beide Richtungen führen.
>
>Verwenden Sie diese Technik nur, wenn Sie diese Konflikte entweder tolerieren oder aktiv bewältigen können.

### iframe {#iframe}

Laden Sie die Veröffentlichungs-URL direkt als `src` einer `<iframe>`. Es ist keine JavaScript erforderlich.

Beispiel für die iFrame-Einbettung:

```iframe
<iframe
  src="<publish-url>"
  title="Content Fragment Preview"
  width="100%"
  height="600"
  frameborder="0"
  style="border: none;"
></iframe>
```

Sie können auch die Größe des iframe automatisch ändern (optional).

Verwenden Sie ein `postMessage` oder eine entsprechende Bibliothek, um die Größe des iframe dynamisch an die Inhaltshöhe anzupassen (Bildlaufleisten werden vermieden).

Ein Beispiel für einen schlanken Ansatz ist:

```iframe
<iframe id="cf-iframe" src="<publish-url>" title="Content Fragment Preview"
  width="100%" frameborder="0" style="border:none; overflow:hidden;"
  onload="this.style.height = this.contentDocument.documentElement.scrollHeight + 'px';"
></iframe>
```

>[!WARNING]
>
>Der oben beschriebene Ansatz der `onload` automatischen Größenanpassung funktioniert nur für iFrames **gleichen Ursprungs**.
>
>Für **ursprungsübergreifende** Veröffentlichungs-URLs benötigen Sie eine `postMessage` Lösung oder müssen eine feste Höhe festlegen.

Verwendung:

* Edge Delivery Services-Einbettungsblock (die Standardintegration - siehe Abschnitt unten)
* Kontexte, in denen eine vollständige CSS/JS-Isolierung wichtig ist
* Cross-Origin-Einbettung, wenn CORS nicht konfiguriert ist
* Schnelle Integration ohne Code (fügen Sie einfach die URL ein)

### Benutzerdefiniertes Element + Shadow-DOM (empfohlen) {#custom-element-and-shadow-dom-recommended}

Definieren Sie ein wiederverwendbares `<cf-visualization>` benutzerdefiniertes Element, das die Veröffentlichungs-URL abruft und die HTML in einen gekapselten Shadow-DOM-Stamm einfügt.

Dieses Element bietet:

* Shadow-DOM-Isolierung
   * Das Markup und die Stile des Fragments sind in einem Schattenstamm gekapselt, wodurch Konflikte mit der CSS-Kaskade der Host-Seite verhindert werden.
* Inline-Layout-Teilnahme
   * Der gerenderte Inhalt ist Teil des normalen Flusses des Host-Dokuments und reagiert auf Container-Größe und FlexBox-/Rasterkontexte ohne manuelles Dimensionsmanagement.
* Einzelner Browserkontext
   * Es wird kein sekundärer Dokumentkontext erstellt. Der Fragmentinhalt nutzt die JavaScript-Laufzeit der Seite gemeinsam und kann von Hilfstechnologien vollständig durchlaufen werden.
* Minimaler Overhead
   * Ein einzelner `fetch` ruft die vorab gerenderte HTML von der Veröffentlichungsebene ab. Es ist kein Client-seitiges Rendering-Framework erforderlich.

>[!IMPORTANT]
>
>Dies ist der empfohlene Ansatz für die Produktionsverwendung und die von AEM-Kernkomponenten verwendete Technik.

Um das benutzerdefinierte Element zu definieren, schließen Sie das folgende Skript einmal pro Seite ein. Alle `<cf-visualization>` auf der Seite verwenden diese Definition:

```javascript
<script>
  class CfVisualization extends HTMLElement {
    connectedCallback() {
      const src = this.getAttribute("src");
      if (!src) return;

      const shadow = this.attachShadow({ mode: "open" });

      fetch(src)
        .then((r) => (r.ok ? r.text() : Promise.reject(r.status)))
        .then((html) => {
          shadow.innerHTML = html;
        })
        .catch((err) => {
          console.error("cf-visualization: failed to load", src, err);
        });
    }
  }

  if (!customElements.get("cf-visualization")) {
    customElements.define("cf-visualization", CfVisualization);
  }
</script>
```

So verwenden Sie das benutzerdefinierte Element:

```html
<cf-visualization src="<publish-url>"></cf-visualization>
```

Verwendung:

* AEM Sites-Seiten, die Kernkomponenten verwenden (dies ist das integrierte Verhalten)
* Externe Websites/Websites von Drittanbietern, die eine saubere, wiederverwendbare Integration benötigen
* Jeder Kontext, in dem sowohl Stilisolierung als auch Beteiligung am Layout-Fluss erforderlich ist

## Integration mit Edge Delivery Services (Einbettungsblock) {#integration-with-edge-services-embed-block}

In Edge Delivery Services wird die Veröffentlichungs-URL über einen **[Einbettungsblock](https://sidekick-library--aem-block-collection--adobe.aem.page/tools/sidekick/library.html?plugin=blocks&path=/block-collection/embed&index=0)** genutzt, der sie als `<iframe>` rendert.

1. Stellen Sie sicher, dass der Einbettungsblock in Ihrem Projekt vorhanden ist.

   Wenn Ihr EDS-Projekt den Einbettungsblock noch nicht enthält, kopieren Sie ihn aus dem Repository aem-block-collection :

   ```cmdline
   # From the aem-block-collection repo, copy blocks/embed/ into your project's blocks/ directory
   cp -r aem-block-collection/blocks/embed/ your-eds-project/blocks/embed/
   ```

1. Erstellen Sie die Einbettung im Editor für die Dokumenterstellung (in Edge Delivery Services)

   Beim Erstellen von Dokumenten werden Blöcke als Tabellen dargestellt. So fügen Sie eine visuelle Inhaltsfragmenteinbettung hinzu:

   | Einbetten |
   |--- |
   | (Veröffentlichungs-URL als Hyperlink einfügen) |

   Falls Ihr Projekt oder Sidekick mit dem Einbettungsblock in der Blockbibliothek konfiguriert ist, können Sie ihn alternativ über das Schrägstrichmenü einfügen und die Veröffentlichungs-URL in den Blockinhalt einfügen.

1. Ergebnis

   Der Einbettungsblock rendert die Veröffentlichungs-URL innerhalb eines `<iframe>`. Der Fragmentinhalt wird im EDS-Seitenlayout vollständig CSS-isoliert geladen.

## Integration - AEM Sites mit Kernkomponenten {#integration-aem-sites-with-core-components}

Die Inhaltsfragment-Kernkomponente (`core/wcm/components/contentfragment/v1/contentfragment`) verfügt über integrierte Unterstützung für die Wiedergabe visueller Inhaltsfragmente mithilfe der [Kundenelement + Schatten-DOM](#custom-element-and-shadow-dom-recommended)-Technik.

Funktionsweise:

* Autorenmodus:

  Wenn die `displayMode` der Komponente auf `vcf` festgelegt ist, ruft die Authoring-Client-Bibliothek (`vcfRenderer.js`) das HTML-Fragment von der Vorschau-API ab und rendert es in der Authoring-Arbeitsfläche inline.

  Ein Beispiel für einen Authoring-Vorschau-Endpunkt ist:

  ```html
  GET /adobe/sites/cf/fragments/{fragmentId}/preview?templateId={templateId}&variation={variation}
  ```

* Veröffentlichungsmodus:

  Auf der veröffentlichten Seite (`wcmmode.disabled`) rendert die HTL-Vorlage ein Inline-Skript, das von der Veröffentlichungs-URL abruft und die HTML in einen Shadow-DOM-Stamm einfügt.

  Eine Beispiel-Kernkomponente für visuelle Inhaltsfragmente (templates.html):

  ```html
  <div class="cmp-contentfragment cmp-contentfragment--vcf"
     data-cmp-contentfragment-id="{fragmentId}"
     data-cmp-contentfragment-vcf-template="{templateId}"
     data-cmp-contentfragment-variation="{variation}">
    <!-- Only rendered when wcmmode.disabled (publish) -->
    <div data-vcf-url="{vcfPublishUrl}" class="cmp-contentfragment__vcf-loader" style="display:none"></div>
    <script>
        (function() {
            var script = document.currentScript;
            var loader = script.previousElementSibling;
            var el = script.parentElement;
            if (!el || !loader) return;
            var url = loader.dataset.vcfUrl;
            if (!url) return;
            loader.remove();
            var shadow = el.attachShadow({ mode: "open" });
            var body = document.createElement("body");
            body.style.display = "none";
            shadow.appendChild(body);
            fetch(url)
                .then(function(r) { return r.ok ? r.text() : Promise.reject(r.status); })
                .then(function(html) {
                    body.innerHTML = html;
                    body.style.display = "";
                });
        })();
    </script>
  </div>
  ```

  Veröffentlichungs-URL-Format:

  Das Sling-Modell (`ContentFragmentImpl`) erstellt die Veröffentlichungs-URL nach dem folgenden Muster:

  ```html
  /adobe/experimental/previewtemplates-expires-20260301/contentFragments/{templateId}/{fragmentId}/{variation}.html
  ```

  Diese relative URL wird zur Laufzeit für den Veröffentlichungs-Host aufgelöst.

## Integration mit externen Sites {#integration-with-external-sites}

Verwenden Sie für Nicht-AEM-Websites die Technik [Kundenelement + Shadow-DOM](#custom-element-and-shadow-dom-recommended). Dadurch erhalten Sie eine saubere, deklarative Integration ohne Framework-Abhängigkeiten.

Ein Beispiel:

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <title>Product Page</title>
</head>
<body>
  <h1>Product Details</h1>
  <p>Some host-page content here...</p>

  <!-- Embed the Content Fragment visualization -->
  <cf-visualization
    src="https://publish-p12345-e67890.adobeaemcloud.com/adobe/experimental/previewtemplates-expires-20260301/contentFragments/product_template/abc-123/master.html"
  ></cf-visualization>

  <p>More host-page content below the fragment...</p>

  <!-- Custom Element definition (include once) -->
  <script>
    class CfVisualization extends HTMLElement {
      connectedCallback() {
        const src = this.getAttribute("src");
        if (!src) return;
        const shadow = this.attachShadow({ mode: "open" });
        fetch(src)
          .then(r => r.ok ? r.text() : Promise.reject(r.status))
          .then(html => { shadow.innerHTML = html; })
          .catch(err => console.error("cf-visualization: failed to load", src, err));
      }
    }
    if (!customElements.get("cf-visualization")) {
      customElements.define("cf-visualization", CfVisualization);
    }
  </script>
</body>
</html>
```

>[!NOTE]
>
>Sie können mehrere `<cf-visualization>`-Elemente mit unterschiedlichen `src`-URLs auf derselben Seite platzieren. Die Definition des benutzerdefinierten Elements muss nur einmal eingefügt werden.

## CORS und Sicherheitsüberlegungen {#cors-and-security-considerations}

| Sorge | Details |
|--- |--- |
| CORS | Der Visualisierungs-Service für Inhaltsfragmente konfiguriert CORS auf dem `/adobe/**` Pfad mit konfigurierbaren zulässigen Ursprüngen.<br>Die [Inline-Element (fetch + innerHTML)](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#inline-element-fetch-and-innerhtml) 1- und [Customer-Element + Shadow-DOM](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#custom-element-and-shadow-dom-recommended)-Techniken (die `fetch()` verwenden) erfordern, dass der Ursprung der Host-Seite in der Zulassungsliste liegt. <br>Die [iFrame](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#iframe)-Technik erfordert keine CORS. |
| csp/x-frame-options | Der Service legt keine `Content-Security-Policy` oder `X-Frame-Options` Kopfzeilen für die veröffentlichte HTML fest. Wenn Ihr CDN oder Dispatcher diese Kopfzeilen hinzufügt, stellen Sie sicher, dass sie Framing (für [iFrame](/help/implementing/developing/extending/content-fragments-visualization-publish-url.md#iframe)) oder `fetch()` Zugriff (für Inline-/Shadow-DOM) von Ihren Host-Ursprüngen aus zulassen. |
| Vertrauen in Inhalte | Die veröffentlichte HTML wird vorab aus den erstellten Inhaltsfragmentdaten mithilfe der vom Service verwalteten [Handlebars](/help/implementing/developing/extending/content-fragments-visualization-templates.md)Vorlagen) gerendert. Es enthält keine benutzergenerierten Skripte. Stellen Sie jedoch wie bei jeder InnerHTML-Injektion sicher, dass Sie der Quelle vertrauen. |

### Wählen Sie die entsprechende Technik aus {#choose-the-appropriate-technique}

Verwenden Sie Folgendes als Entscheidungshandbuch, um die geeignete Methode auszuwählen:

| Szenario | Lösung |
|--- |--- |
| Benötigen Sie keinen JavaScript und eine vollständige Isolation? | iframe |
| Benötigen Sie Layout-Flow-Beteiligung mit Stil-Isolierung? | Benutzerdefiniertes Element + Shadow-DOM (empfohlen) |
| Benötigen Sie die schnellsten Konflikte mit Prototypen, identischen Quellen und CSS? | Inline-Element |
| Einbetten in Edge Delivery Services? | Block einbetten (iframe unter der Haube) |
| Einbetten in AEM Sites-Seiten? | Kernkomponente (Shadow DOM, integriert) |


## Zusätzliche Ressourcen {#additional-resources}

Zusätzliche Ressourcen sind verfügbar:

* [Dokumentation zu AEM-Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md)

<!-- CQDOC-23650 - add link when docs are stable; not experimental -->

<!--
* [Content Fragment Visualization Templates APIs (experimental)](https://developer.adobe.com/experience-cloud/experience-manager-apis/api/experimental/sites/cvt/#)
-->
