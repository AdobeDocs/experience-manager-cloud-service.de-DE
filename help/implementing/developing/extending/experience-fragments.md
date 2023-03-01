---
title: Experience Fragments  Übersicht
description: Erweitern Sie Experience Fragments in Adobe Experience Manager as a Cloud Service.
exl-id: bd4ea763-d17c-40a6-9a86-a24d7600229e
source-git-commit: 5968554ec221b1fe9969b131ccf0b08ffb7f6494
workflow-type: ht
source-wordcount: '1651'
ht-degree: 100%

---

# Experience Fragments{#experience-fragments}

## Grundlagen {#the-basics}

Ein [Experience Fragment](/help/sites-cloud/authoring/fundamentals/experience-fragments.md) ist eine Gruppe aus einer oder mehreren Komponenten (einschließlich Inhalt und Layout), die innerhalb von Seiten referenziert werden können.

Ein primäres Experience Fragment und/oder eine Experience Fragment-Variante verwendet:

* `sling:resourceType`: `/libs/cq/experience-fragments/components/xfpage`

Da es kein `/libs/cq/experience-fragments/components/xfpage/xfpage.html` gibt, wird auf Folgendes zurückgegriffen:

* `sling:resourceSuperType` : `wcm/foundation/components/page`

## Einfache HTML-Ausgabedarstellung {#the-plain-html-rendition}

Mit dem `.plain.`-Selektor in der URL können Sie auf die einfache HTML-Ausgabe zugreifen.

Diese ist über den Browser verfügbar, aber ihr Hauptzweck ist es, anderen Applikationen (beispielsweise Web-Applikationen von Drittanbietern oder benutzerdefinierten mobilen Implementierungen) den direkten Zugriff auf den Inhalt des Experience Fragment zu ermöglichen, und zwar allein über die URL.

Die Plain-HTML-Wiedergabe fügt den Protokoll-, Host- und Kontextpfad zu Pfaden hinzu, welche:

* den folgenden Typ aufweisen: `src`, `href` oder `action`

* oder folgendermaßen enden: `-src` oder `-href`

Beispiel:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Links verweisen immer auf die Veröffentlichungsinstanz. Sie sind für die Nutzung durch Dritte bestimmt, sodass der Link immer von der Veröffentlichungsinstanz und nicht von der Autoreninstanz aufgerufen wird.

![Einfache HTML-Ausgabe](assets/xf-14.png)

Der Selektor für die einfache Ausgabe verwendet einen Transformator im Gegensatz zu zusätzlichen Skripten. Der [Sling Rewriter](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) wird als Transformator verwendet. Dies wird hier konfiguriert

* `/libs/experience-fragments/config/rewriter/experiencefragments`

### Konfigurieren der Generierung der HTML-Ausgabedarstellung {#configuring-html-rendition-generation}

Die HTML-Ausgabedarstellung wird mithilfe der Sling Rewriter Pipelines generiert. Die Pipeline wird in `/libs/experience-fragments/config/rewriter/experiencefragments` definiert. HTML Transformer unterstützt die folgenden Optionen:

* `allowedCssClasses`
   * Ein RegEx-Ausdruck, der den CSS-Klassen entspricht, die in der endgültigen Ausgabe beibehalten werden sollen.
   * Dies ist nützlich, wenn der Kunde bestimmte CSS-Klassen entfernen möchte
* `allowedTags`
   * Eine Liste der HTML-Tags, die in der endgültigen Ausgabe zulässig sein sollen.
   * Standardmäßig sind die folgenden Tags zulässig (keine Konfiguration erforderlich): html, head, title, body, img, p, span, ul, li, a, b, i, em, strong, h1, h2, h3, h4, h5, h6, br, noscript, div, link und script

Es wird empfohlen, den Rewriter mithilfe einer Überlagerung zu konfigurieren. Weitere Informationen finden Sie unter [Überlagerungen in AEM as a Cloud Service](/help/implementing/developing/introduction/overlays.md)

## Vorlagen für Experience Fragments {#templates-for-experience-fragments}

>[!CAUTION]
>
>Für Experience Fragments werden ***nur*** bearbeitbare Vorlagen unterstützt.

<!-- >***Only*** [editable templates](/help/sites-developing/page-templates-editable.md) are supported for Experience Fragments.
-->

Beim Entwickeln einer neuen Vorlage für Experience Fragments folgen Sie den Standardverfahren für eine bearbeitbare Vorlage.

<!-- When developing a new template for Experience Fragments you can follow follow the standard practices for an [editable template](/help/sites-developing/page-templates-editable.md).
-->

Um eine Experience Fragment-Vorlage zu erstellen, die vom **Experience Fragment**-Assistenten erstellt wird, müssen Sie einen dieser Regelsätze verfolgen:

1. Beide:

   1. Der Ressourcentyp der Vorlage (der Anfangsknoten) muss erben von:
      `cq/experience-fragments/components/xfpage`

   1. Der Name der Vorlage muss beginnen mit:
      `experience-fragments`
Dadurch können Anwender Experience Fragments in „/content/experience-fragments“ erstellen, da 
die `cq:allowedTemplates`-Eigenschaft dieses Ordners alle Vorlagen umfasst, deren Namen mit `experience-fragment`beginnen. Kunden können diese Eigenschaft aktualisieren, um ihr eigenes Namensschema oder ihre eigenen Vorlagenspeicherorte einzuschließen.

1. [Zulässige Vorlagen](/help/sites-cloud/authoring/fundamentals/experience-fragments.md#configure-allowed-templates-folder) können in der Experience Fragments-Konsole konfiguriert werden.

<!--
1. Add the template details manually in `cq:allowedTemplates` on the `/content/experience-fragment` node.
-->

<!-- >[!NOTE]
>
>[Allowed templates](/help/sites-authoring/experience-fragments.md#configuring-allowed-templates) can be configured in the Experience Fragments console.
-->

## Komponenten für Experience Fragments {#components-for-experience-fragments}

Die Entwicklung von Komponenten für die Verwendung mit/in Experience Fragments erfolgt gemäß den üblichen Verfahren.

Die einzige zusätzliche Konfiguration besteht darin, sicherzustellen, dass die Komponenten in der Vorlage zulässig sind. Dies wird mit der Inhaltsrichtlinie erreicht.

<!--
[Developing components](/help/sites-developing/components.md) for use with/in Experience Fragments follow standard practices.

The only additional configuration is to ensure that the components are [allowed on the template, this is achieved with the Content Policy](/help/sites-developing/page-templates-editable.md#content-policies).
-->

## Der Experience Fragment Link Rewriter Provider – HTML {#the-experience-fragment-link-rewriter-provider-html}

In AEM können Sie Experience Fragments erstellen. Ein Experience Fragment:

* besteht aus einer Gruppe von Komponenten und einem Layout,
* kann unabhängig von einer AEM-Seite vorhanden sein.

Einer der Anwendungsfälle für solche Gruppen ist das Einbetten von Inhalten in Touchpoints von Drittanbietern, wie z. B. Adobe Target.

### Standardmäßige Link-Umschreibung {#default-link-rewriting}

<!--Using the [Export to Target](/help/sites-administering/experience-fragments-target.md) feature, you can:
-->

Mit der Funktion „In Target exportieren“ können Sie:

* ein Experience Fragment erstellen,
* Komponenten hinzufügen,
* und es dann als Adobe Target-Angebot entweder im HTML- oder JSON-Format exportieren.

Diese Funktion kann in einer Autoreninstanz von AEM aktiviert werden. Sie erfordert eine gültige Adobe Target-Konfiguration und Konfigurationen für den Link Externalizer.

<!--
This feature can be [enabled on an author instance of AEM](/help/sites-administering/experience-fragments-target.md#Prerequisites). It requires a valid Adobe Target Configuration, and configurations for the Link Externalizer.
-->

Der Link Externalizer wird verwendet, um die richtigen URLs zu ermitteln, die beim Erstellen der HTML-Version des Target-Angebots erforderlich sind, die anschließend an Adobe Target gesendet wird. Dies ist erforderlich, da Adobe Target erfordert, dass alle Links im Target-HTML-Angebot öffentlich zugänglich sind. Dies bedeutet, dass alle Ressourcen, auf die die Links verweisen, und das Experience Fragment selbst veröffentlicht werden müssen, bevor sie verwendet werden können.

Wenn Sie ein Target-HTML-Angebot erstellen, wird standardmäßig eine Anfrage an einen benutzerdefinierten Sling-Selektor in AEM gesendet. Dieser Selektor heißt `.nocloudconfigs.html`. Wie der Name schon sagt, erstellt er ein einfaches HTML-Rendering eines Experience Fragment, enthält jedoch keine Cloud-Konfigurationen (die überflüssige Informationen wären).

Nachdem Sie die HTML-Seite generiert haben, nimmt die Sling Rewriter-Pipeline Änderungen an der Ausgabe vor:

1. Die Elemente `html`, `head` und `body` werden durch `div`-Elemente ersetzt. Die Elemente `meta`, `noscript` und `title` werden entfernt (sie sind untergeordnete Elemente des ursprünglichen `head`-Elements und werden nicht berücksichtigt, wenn dieses durch das `div`-Element ersetzt wird).

   Dies geschieht, um sicherzustellen, dass das HTML-Target-Angebot in Target-Aktivitäten einbezogen werden kann.

2. AEM ändert alle internen Links im HTML-Code, sodass sie auf eine veröffentlichte Ressource verweisen.

   Um die zu ändernden Links zu bestimmen, folgt AEM diesem Muster für Attribute von HTML-Elementen:

   1. `src`-Attribute
   2. `href`-Attribute
   3. `*-src`-Attribute (z. B. data-src, custom-src usw.)
   4. `*-href`-Attribute (z. B. `data-href`, `custom-href`, `img-href` usw.)

   >[!NOTE]
   >
   >In den meisten Fällen handelt es sich bei den internen Links im HTML-Code um relative Links. Es kann jedoch vorkommen, dass benutzerdefinierte Komponenten vollständige URLs im HTML-Code bereitstellen. Standardmäßig ignoriert AEM diese vollständigen URLs und nimmt keine Änderungen vor.

   Die Links in diesen Attributen werden über `publishLink()` von AEM Link Externalizer ausgeführt, um die URL so neu zu erstellen, als ob sie sich auf einer veröffentlichten Instanz befände und als solche öffentlich verfügbar wäre.

Bei Verwendung einer vordefinierten Implementierung sollte der oben beschriebene Prozess ausreichen, um das Target-Angebot aus dem Experience Fragment zu generieren und es dann in Adobe Target zu exportieren. Es gibt jedoch einige Anwendungsfälle, die in diesem Prozess nicht berücksichtigt werden. Dazu gehören:

* Sling-Zuordnung nur für die Veröffentlichungsinstanz verfügbar
* Dispatcher-Umleitungen

Für diese Anwendungsfälle stellt AEM die Link Rewriter Provider-Schnittstelle bereit.

### Link Rewriter Provider-Schnittstelle {#link-rewriter-provider-interface}

Für kompliziertere Fälle, die nicht vom [Standard](#default-link-rewriting) abgedeckt werden, bietet AEM die Link Rewriter Provider-Schnittstelle. Dies ist eine `ConsumerType`-Schnittstelle, die Sie als Service in Ihren Bundles implementieren können. Sie umgeht die Änderungen, die AEM an internen Links eines HTML-Angebots vornimmt, die aus einem Experience Fragment gerendert wurden. Diese Schnittstelle ermöglicht es Ihnen, den Prozess des Umschreibens interner HTML-Links an Ihre geschäftlichen Anforderungen anzupassen.

Beispiele für Anwendungsfälle für die Implementierung dieser Schnittstelle als Service:

* Sling-Zuordnungen sind in den Veröffentlichungsinstanzen aktiviert, nicht jedoch in der Autoreninstanz
* Eine Dispatcher- oder ähnliche Technologie wird verwendet, um URLs intern umzuleiten
* Es gibt `sling:alias mechanisms` für Ressourcen

>[!NOTE]
>
>Diese Schnittstelle verarbeitet nur die internen HTML-Links aus dem generierten Target-Angebot.

Die Link Rewriter Provider-Schnittstelle (`ExperienceFragmentLinkRewriterProvider`) lautet wie folgt:

```java
public interface ExperienceFragmentLinkRewriterProvider {

    String rewriteLink(String link, String tag, String attribute);

    boolean shouldRewrite(ExperienceFragmentVariation experienceFragment);

    int getPriority();

}
```

### Verwendung der Link Rewriter Provider-Schnittstelle {#how-to-use-the-link-rewriter-provider-interface}

Um die Schnittstelle zu verwenden, müssen Sie zunächst ein Bundle anlegen, das eine neue Service-Komponente enthält, die die Link Rewriter Provider-Schnittstelle implementiert.

Dieser Service wird verwendet, um das Umschreiben beim Exportieren von Experience Fragments nach Target zu ermöglichen, um Zugriff auf die verschiedenen Links zu erhalten.

Beispiel: `ComponentService`:

```java
import com.adobe.cq.xf.ExperienceFragmentLinkRewriterProvider;
import com.adobe.cq.xf.ExperienceFragmentVariation;
import org.osgi.service.component.annotations.Service;
import org.osgi.service.component.annotations.Component;

@Component
@Service
public class GeneralLinkRewriter implements ExperienceFragmentLinkRewriterProvider {

    @Override
    public String rewriteLink(String link, String tag, String attribute) {
        return null;
    }

    @Override
    public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
        return false;
    }

    @Override
    public int getPriority() {
        return 0;
    }

}
```

Damit der Service funktioniert, müssen jetzt drei Methoden innerhalb des Service implementiert werden:

* `[shouldRewrite](#shouldrewrite)`
* `[rewriteLink](#rewritelink)`

   * `rewriteLinkExample2`

* `[getPriority](#priorities-getpriority)`

#### shouldRewrite {#shouldrewrite}

Sie müssen dem System angeben, ob die Links umgeschrieben werden müssen, wenn für eine bestimmte Experience Fragment-Variante ein Aufruf „In Target exportieren“ aufgerufen wird. Implementieren Sie dazu die folgende Methode:

`shouldRewrite(ExperienceFragmentVariation experienceFragment);`

Beispiel:

```java
@Override
public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
    return experienceFragment.getPath().equals("/content/experience-fragment/master");
}
```

Diese Methode erhält als Parameter die Experience Fragment-Variante, die das System „In Target exportieren“ derzeit umschreibt.

Im obigen Beispiel möchten wir Folgendes umschreiben:

* in `src` vorhandene Links

* nur `href`-Attribute

* für ein bestimmtes Experience Fragment:
   `/content/experience-fragment/master`

Alle anderen Experience Fragments, die das System „In Target exportieren“ durchlaufen, werden ignoriert und sind von den in diesem Service implementierten Änderungen nicht betroffen.

#### rewriteLink {#rewritelink}

Für die Experience Fragment-Variante, die vom Umschreibungsprozess betroffen ist, wird der Service dann die Links umschreiben. Bei jedem Auftreten eines Links im internen HTML-Code wird die folgende Methode aufgerufen:

`rewriteLink(String link, String tag, String attribute)`

Als Eingabe erhält die Methode die folgenden Parameter:

* `link`
Die 
`String`-Darstellung des Links, der derzeit verarbeitet wird. Dies ist normalerweise eine relative URL, die auf die Ressource in der Autoreninstanz verweist.

* `tag`
Der Name des HTML-Elements, das derzeit verarbeitet wird.

* `attribute`
Der genaue Attributname.

Wenn beispielsweise das System „Nach Target exportieren“ dieses Element derzeit verarbeitet, können Sie `CSSInclude` wie folgt definieren:

```java
<link rel="stylesheet" href="/etc.clientlibs/foundation/clientlibs/main.css" type="text/css">
```

Die `rewriteLink()`-Methode wird mithilfe der folgenden Parameter aufgerufen:

```java
rewriteLink(link="/etc.clientlibs/foundation/clientlibs/main.css", tag="link", attribute="href" )
```

Wenn Sie den Service erstellen, können Sie Entscheidungen basierend auf der angegebenen Eingabe treffen und dann den Link entsprechend umschreiben.

In unserem Beispiel möchten wir den `/etc.clientlibs`-Teil der URL entfernen und die entsprechende externe Domain hinzufügen. Um die Dinge einfach zu halten, werden wir in Betracht ziehen, dass wir Zugriff auf einen Resource Resolver für Ihren Service haben, wie in `rewriteLinkExample2`:

>[!NOTE]
>
>Weitere Informationen zum Abrufen eines Ressource Resolver über einen Service-Benutzer finden Sie unter „Service-Benutzer in AEM“.

<!--
>For more information on how to get a resource resolver through a service user see [Service Users in AEM](/help/sites-administering/security-service-users.md).
-->

```java
private ResourceResolver resolver;

private Externalizer externalizer;

@Override
public String rewriteLink(String link, String tag, String attribute) {

    // get the externalizer service
    externalizer = resolver.adaptTo(Externalizer.class);
    if(externalizer == null) {
        // if there was an error, then we do not modify the link
        return null;
    }

    // remove leading /etc.clientlibs from resource link before externalizing
    link = link.replaceAll("/etc.clientlibs", "");

    // considering that we configured our publish domain, we directly apply the publishLink() method
    link = externalizer.publishLink(resolver, link);

    return link;
}
```

>[!NOTE]
>
>Wenn die oben beschriebene Methode `null` zurückgibt, lässt das System „In Target exportieren“ den Link so, wie er ist (ein relativer Link zu einer Ressource).

#### Prioritäten – getPriority {#priorities-getpriority}

Es ist nicht ungewöhnlich, dass mehrere Service für verschiedene Arten von Experience Fragments benötigt werden oder dass sogar ein generischer Service vorhanden ist, der die Externalisierung und Zuordnung aller Experience Fragments übernimmt. In diesen Fällen kann es zu Konflikten darüber kommen, welcher Service verwendet werden soll, sodass AEM die Möglichkeit bietet, **Prioritäten** für verschiedene Services festzulegen. Die Prioritäten werden nach folgendem Verfahren festgelegt:

* `getPriority()`

Diese Methode ermöglicht die Verwendung mehrerer Services, bei denen die `shouldRewrite()`-Methode für dasselbe Experience Fragment „true“ zurückgibt. Der Service, der die höchste Zahl aus der `getPriority()`-Methode zurückgibt, ist der Service, der die Experience Fragment-Variante verarbeitet.

Beispielsweise können Sie einen `GenericLinkRewriterProvider`-Service verwenden, der die grundlegende Zuordnung für alle Experience Fragments handhabt und wenn die `shouldRewrite()` Methode für alle Experience-Fragment-Varianten `true` zurückgibt. Für mehrere spezifische Experience Fragments ist möglicherweise eine besondere Behandlung erforderlich. In diesem Fall können Sie also einen `SpecificLinkRewriterProvider`-Service bereitstellen, für den die `shouldRewrite()`-Methode nur für einige Experience Fragment-Varianten „true“ zurückgibt. Um sicherzustellen, dass `SpecificLinkRewriterProvider` für die Verarbeitung dieser Experience Fragment-Varianten ausgewählt wird, muss in der `getPriority()`-Methode eine höhere Zahl zurückgegeben werden als für `GenericLinkRewriterProvider.`
