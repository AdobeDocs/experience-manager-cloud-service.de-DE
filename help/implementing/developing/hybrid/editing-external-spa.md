---
title: Bearbeiten einer externen SPA in AEM
description: In diesem Dokument werden die empfohlenen Schritte zum Hochladen einer eigenständigen SPA in eine AEM-Instanz, zum Hinzufügen bearbeitbarer Inhaltsabschnitte und zum Aktivieren des Authoring beschrieben.
exl-id: 7978208d-4a6e-4b3a-9f51-56d159ead385
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '2421'
ht-degree: 48%

---

# Bearbeiten einer externen SPA in AEM {#editing-external-spa-within-aem}

Bei der Entscheidung [Integrationsstufe](/help/implementing/developing/headful-headless.md) Wenn Sie zwischen Ihren externen SPA und AEM haben möchten, beachten Sie, dass Sie die SPA in AEM häufig bearbeiten und anzeigen können müssen.

## Übersicht {#overview}

In diesem Dokument werden die empfohlenen Schritte zum Hochladen einer eigenständigen SPA in eine AEM-Instanz, zum Hinzufügen bearbeitbarer Inhaltsabschnitte und zum Aktivieren des Authoring beschrieben.

## Voraussetzungen {#prerequisites}

Die Voraussetzungen sind einfach.

* Stellen Sie sicher, dass eine Instanz von AEM lokal ausgeführt wird.
* Erstellen Sie ein AEM-SPA-Projekt mit [dem AEM-Projektarchetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de#available-properties).
   * Forms bildet die Grundlage des AEM Projekts, das aktualisiert wird, um die externe SPA aufzunehmen.
   * Für die Beispiele in diesem Dokument verwendet Adobe den Ausgangspunkt von [das WKND-SPA](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=de#spa-editor).
* Halten Sie die funktionierende, externe React SPA bereit, die Sie integrieren möchten.

## Hochladen der SPA in das AEM-Projekt {#upload-spa-to-aem-project}

Zunächst müssen Sie die externe SPA in Ihr AEM-Projekt hochladen.

1. Ersetzen Sie `src` im Projektordner `/ui.frontend` durch den Ordner `src` des React-Programms.
1. Schließen Sie alle weiteren Abhängigkeiten in der Datei `package.json` der App in die Datei `/ui.frontend/package.json` ein.
   * Stellen Sie sicher, dass die SPA SDK-Abhängigkeiten [empfohlene Versionen](/help/implementing/developing/hybrid/getting-started-react.md#dependencies).
1. Fügen Sie alle Anpassungen in den Ordner `/public` ein.
1. Fügen Sie alle hinzugefügten Inline-Skripte oder Stile ein die Datei `/public/index.html` ein.

## Konfigurieren der Remote-SPA {#configure-remote-spa}

Nachdem die externe SPA Teil Ihres AEM-Projekts ist, muss sie in AEM konfiguriert werden.

### Einschließen der Adobe SPA-SDK-Pakete {#include-spa-sdk-packages}

Um die AEM SPA-Funktionen nutzen zu können, gibt es Abhängigkeiten von den folgenden drei Paketen.

* [`@adobe/aem-react-editable-components`](https://github.com/adobe/aem-react-editable-components)
* [`@adobe/aem-spa-component-mapping`](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)
* [`@adobe/aem-spa-page-model-manager`](https://www.npmjs.com/login?next=/package/@adobe/aem-spa-model-manager)

Die `@adobe/aem-spa-page-model-manager` -Paket stellt die API zum Initialisieren eines Modell-Managers und zum Abrufen des Modells aus der AEM-Instanz bereit. Dieses Modell kann dann zum Rendern von AEM-Komponenten mithilfe der APIs von `@adobe/aem-react-editable-components` und `@adobe/aem-spa-component-mapping` verwendet werden.

#### Installation {#installation}

Führen Sie Folgendes aus: `npm` -Befehl, damit Sie die erforderlichen Pakete installieren können.

```shell
npm install --save @adobe/aem-spa-component-mapping @adobe/aem-spa-page-model-manager @adobe/aem-react-editable-components
```

### ModelManager-Initialisierung {#model-manager-initialization}

Bevor die App gerendert wird, muss die [`ModelManager`](/help/implementing/developing/hybrid/blueprint.md#pagemodelmanager) muss initialisiert werden, um die Erstellung des AEM zu handhaben `ModelStore`.

Diese Initialisierung muss innerhalb der `src/index.js` -Datei Ihrer Anwendung oder wo immer der Stamm der Anwendung gerendert wird.

Für diese Initialisierung können Sie `initializationAsync` Die von der `ModelManager`.

Der folgende Screenshot zeigt, wie die Initialisierung von `ModelManager` in einem einfachen React-Programm aktiviert wird. Die einzige Einschränkung ist, dass `initializationAsync` muss vor aufgerufen werden `ReactDOM.render()`.

![ModelManager initialisieren](assets/external-spa-initialize-modelmanager.png)

In diesem Beispiel wird `ModelManager` initialisiert und ein leerer `ModelStore` erstellt.

Die `initializationAsync` kann optional eine `options` -Objekt als Parameter:

* `path` - Bei der Initialisierung wird das Modell vom definierten Pfad abgerufen und im `ModelStore` gespeichert. Dieser Pfad kann zum Abrufen der `rootModel` bei der Initialisierung, falls erforderlich.
* `modelClient` - Ermöglicht die Bereitstellung eines benutzerdefinierten Clients, der für das Abrufen des Modells verantwortlich ist.
* `model` - A `model` Objekt, das als Parameter übergeben wird, wird normalerweise ausgefüllt, wenn [Verwendung von SSR](/help/implementing/developing/hybrid/ssr.md).

### Bearbeitbare AEM-Blattkomponenten {#authorable-leaf-components}

1. Erstellen/identifizieren Sie eine AEM-Komponente, für die eine bearbeitbare React-Komponente erstellt wird. In diesem Beispiel wird die Textkomponente des WKND-Projekts verwendet.

   ![WKND-Textkomponente](assets/external-spa-text-component.png)

1. Erstellen Sie eine einfache React-Textkomponente in der SPA. In diesem Beispiel wurde eine neue Datei `Text.js` mit folgendem Inhalt erstellt.

   ![Text.js](assets/external-spa-textjs.png)

1. Erstellen Sie ein Konfigurationsobjekt, mit dem Sie die zum Aktivieren AEM Bearbeitung erforderlichen Attribute angeben können.

   ![config-Objekt erstellen](assets/external-spa-config-object.png)

   * `resourceType` ist erforderlich, um die React-Komponente der AEM-Komponente zuzuordnen und die Bearbeitung zu aktivieren, wenn sie im AEM Editor geöffnet wird.

1. Verwenden Sie die Wrapper-Funktion `withMappable`.

   ![withMappable verwenden](assets/external-spa-withmappable.png)

   Diese Wrapper-Funktion ordnet die React-Komponente dem AEM zu `resourceType` angegeben in der Konfiguration und ermöglicht Bearbeitungsfunktionen, wenn sie im AEM Editor geöffnet werden. Bei eigenständigen Komponenten ruft es auch den Modellinhalt für den jeweiligen Knoten ab.

   >[!NOTE]
   >
   >In diesem Beispiel gibt es separate Versionen der Komponente: AEM umschlossene und entpackte React-Komponenten. Die umschlossene Version muss verwendet werden, wenn die Komponente explizit verwendet wird. Wenn die Komponente Teil einer Seite ist, können Sie weiterhin die Standardkomponente verwenden (wie derzeit im SPA-Editor).

1. Rendern des Inhalts in der Komponente

   Die JCR-Eigenschaften der Textkomponente werden wie folgt in AEM angezeigt.

   ![Eigenschaften von Textkomponenten](assets/external-spa-text-properties.png)

   Diese Werte werden als Eigenschaften an die neu erstellte `AEMText` React-Komponente und kann zum Rendern des Inhalts verwendet werden.

   ```javascript
   import React from 'react';
   import { withMappable } from '@adobe/aem-react-editable-components';
   
   export const TextEditConfig = {
       // Empty component placeholder label
       emptyLabel:'Text', 
       isEmpty:function(props) {
          return !props || !props.text || props.text.trim().length < 1;
       },
       // resourcetype of the AEM counterpart component
       resourceType:'wknd-spa-react/components/text'
   };
   
   const Text = ({ text }) => (<div>{text}</div>);
   
   export default Text;
   
   export const AEMText = withMappable(Text, TextEditConfig);
   ```

   Im Folgenden sehen Sie, wie die Komponente angezeigt wird, wenn die AEM Konfigurationen abgeschlossen sind.

   ```javascript
   const Text = ({ cqPath, richText, text }) => {
      const richTextContent = () => (
         <div className="aem_text" id={cqPath.substr(cqPath.lastIndexOf('/') + 1)} data-rte-editelement dangerouslySetInnerHTML={{__html: text}}/>
      );
      return richText ? richTextContent() : (<div className="aem_text">{text}</div>);
   };
   ```

   >[!NOTE]
   >
   >In diesem Beispiel wurden weitere Anpassungen an der gerenderten Komponente vorgenommen, um sie an die vorhandene Textkomponente anzupassen. Sie ist nicht mit dem Authoring in AEM verbunden.

#### Hinzufügen von bearbeitbaren Komponenten zur Seite {#add-authorable-component-to-page}

Nachdem die bearbeitbaren React-Komponenten erstellt wurden, können Sie sie in der gesamten Anwendung verwenden.

Nehmen wir eine Beispielseite, auf der Sie einen Text aus dem WKND-SPA hinzufügen müssen. In diesem Beispiel möchten Sie den Text &quot;Hello World!&quot;anzeigen. auf `/content/wknd-spa-react/us/en/home.html` anzeigen.

1. Legen Sie den Pfad der anzuzeigenden Knoten fest.

   * `pagePath`: Die Seite, die den Knoten enthält, in diesem Beispiel `/content/wknd-spa-react/us/en/home`
   * `itemPath`: Pfad zum Knoten innerhalb der Seite, in diesem Beispiel `root/responsivegrid/text`
      * Besteht aus den Namen der enthaltenen Elemente auf der Seite.

   ![Pfad des Knotens](assets/external-spa-path.png)

1. Fügen Sie die Komponente an gewünschter Position in die Seite ein.

   ![Komponente zur Seite hinzufügen](assets/external-spa-add-component.png)

   Die `AEMText`-Komponente kann an der gewünschten Position in die Seite eingefügt werden, wobei die Werte `pagePath` und `itemPath` als Eigenschaften festgelegt sind. `pagePath` ist eine obligatorische Eigenschaft.

#### Überprüfen der Bearbeitung von Textinhalten in AEM {#verify-text-edit}

Testen Sie nun die Komponente auf der laufenden AEM-Instanz.

1. Führen Sie den folgenden Maven-Befehl aus dem `aem-guides-wknd-spa` -Verzeichnis, damit Sie das Projekt erstellen und für AEM bereitstellen können.

```shell
mvn clean install -PautoInstallSinglePackage
```

1. Navigieren Sie in Ihrer AEM-Instanz zu `http://<host>:<port>/editor.html/content/wknd-spa-react/us/en/home.html`.

![Bearbeiten der SPA in AEM](assets/external-spa-edit-aem.png)

Die `AEMText`-Komponente kann jetzt in AEM bearbeitet werden.

### In AEM bearbeitbare Seiten {#aem-authorable-pages}

1. Identifizieren Sie eine Seite, die zur Bearbeitung in der SPA hinzugefügt werden soll. In diesem Beispiel wird `/content/wknd-spa-react/us/en/home.html` verwendet.
1. Erstellen Sie eine Datei (z. B. `Page.js`) für die bearbeitbare Seitenkomponente. die Seitenkomponente verwenden, die in `@adobe/cq-react-editable-components`.
1. Wiederholen Sie Schritt 4 im Abschnitt [Bearbeitbare AEM-Blattkomponenten](#authorable-leaf-components). Verwenden Sie die Wrapper-Funktion `withMappable` für die Komponente.
1. Wenden Sie wie zuvor `MapTo` auf die AEM-Ressourcentypen für alle untergeordneten Komponenten in der Seite an.

   ```javascript
   import { Page, MapTo, withMappable } from '@adobe/aem-react-editable-components';
   import Text, { TextEditConfig } from './Text';
   
   export default withMappable(Page);
   
   MapTo('wknd-spa-react/components/text')(Text, TextEditConfig);
   ```

   >[!NOTE]
   >
   >In diesem Beispiel wird die entpackte React-Text-Komponente anstelle der umschlossenen `AEMText` erstellt. Der Grund dafür ist, dass der Container die rekursive Zuordnung der Komponente übernimmt, wenn die Komponente Teil einer Seite/eines Containers und nicht allein ist. Die Aktivierung der Authoring-Funktionen und des zusätzlichen Wrappers ist nicht für jedes untergeordnete Element erforderlich.

1. Um eine bearbeitbare Seite in der SPA hinzuzufügen, folgen Sie denselben Schritten wie im Abschnitt [Hinzufügen von bearbeitbaren Komponenten zur Seite](#add-authorable-component-to-page). Hier können Sie die `itemPath` -Eigenschaft.

#### Überprüfen des Seiteninhalts in AEM {#verify-page-content}

Um zu überprüfen, ob die Seite bearbeitet werden kann, folgen Sie denselben Schritten im Abschnitt [Überprüfen der Bearbeitung von Textinhalten in AEM](#verify-text-edit).

![Bearbeiten einer Seite in AEM](assets/external-spa-edit-page.png)

Die Seite ist nun in AEM mit einem Layout-Container und einer untergeordneten Textkomponente bearbeitbar.

### Virtuelle Blattkomponenten {#virtual-leaf-components}

In den vorherigen Beispielen haben Sie der SPA Komponenten mit vorhandenem AEM hinzugefügt. Es gibt jedoch Fälle, in denen Inhalte noch nicht in AEM erstellt wurden, sondern später vom Inhaltsautor hinzugefügt werden müssen. Um dieses Szenario zu berücksichtigen, kann der Frontend-Entwickler Komponenten an den entsprechenden Stellen innerhalb des SPA hinzufügen. Diese Komponenten zeigen Platzhalter an, wenn sie im Editor in AEM geöffnet werden. Nachdem der Inhalt in diesen Platzhaltern vom Inhaltsautor hinzugefügt wurde, werden Knoten in der JCR-Struktur erstellt und der Inhalt bleibt erhalten. Die erstellte Komponente ermöglicht denselben Satz von Vorgängen wie die eigenständigen Blattkomponenten.

In diesem Beispiel verwenden Sie die `AEMText` Komponente, die zuvor erstellt wurde. Sie möchten, dass unter der vorhandenen Textkomponente auf der WKND-Startseite neuer Text hinzugefügt wird. Das Hinzufügen von Komponenten ist dasselbe wie bei normalen Blattkomponenten. Die Variable `itemPath` kann in den Pfad aktualisiert werden, in dem die neue Komponente hinzugefügt werden muss.

Da die neue Komponente unter dem vorhandenen Text hinzugefügt werden muss unter `root/responsivegrid/text`, lautet der neue Pfad . `root/responsivegrid/{itemName}`.

```html
<AEMText
 pagePath='/content/wknd-spa-react/us/en/home'
 itemPath='root/responsivegrid/text_20' />
```

Die Komponente `TestPage` sieht nach dem Hinzufügen der virtuellen Komponente wie folgt aus.

![Testen der virtuellen Komponente](assets/external-spa-virtual-component.png)

>[!NOTE]
>
>Stellen Sie sicher, dass `AEMText` -Komponente `resourceType` in der Konfiguration festgelegt, damit Sie diese Funktion aktivieren können.

Sie können jetzt die Änderungen an AEM entsprechend den Schritten im folgenden Abschnitt bereitstellen: [Überprüfen der Bearbeitung von Textinhalten in AEM](#verify-text-edit). Für die derzeit nicht vorhandene `text_20` Knoten.

![Der text_20-Knoten in AEM](assets/external-spa-text20-aem.png)

Wenn der Inhaltsautor diese Komponente aktualisiert, wird unter `root/responsivegrid/text_20` in `/content/wknd-spa-react/us/en/home` ein neuer `text_20`-Knoten erstellt.

![Der text20-Knoten](assets/external-spa-text20-node.png)

#### Anforderungen und Einschränkungen {#limitations}

Es gibt mehrere Anforderungen zum Hinzufügen von Virtual-Leaf-Komponenten und einige Einschränkungen.

* Die `pagePath`-Eigenschaft ist zum Erstellen einer virtuellen Komponente obligatorisch.
* Der im Pfad in `pagePath` angegebene Seitenknoten muss im AEM-Projekt vorhanden sein.
* Der Name des zu erstellenden Knotens muss im `itemPath` angegeben werden.
* Die Komponente kann auf jeder Ebene erstellt werden.
   * Wenn Sie `itemPath='text_20'` im vorherigen Beispiel wird der neue Knoten direkt unter der Seite erstellt, d. h. `/content/wknd-spa-react/us/en/home/jcr:content/text_20`
* Der Pfad zum Knoten, in dem ein neuer Knoten erstellt wird, muss gültig sein, wenn er über `itemPath` bereitgestellt wird.
   * In diesem Beispiel muss `root/responsivegrid` vorhanden sein, damit der neue Knoten `text_20` dort erstellt werden kann.
* Es wird nur die Erstellung von Blattkomponenten unterstützt. Virtuelle Container und Seiten werden in zukünftigen Versionen unterstützt.

### Virtuelle Container {#virtual-containers}

Die Möglichkeit, Container hinzuzufügen, auch wenn der entsprechende Container noch nicht in AEM erstellt wurde, wird unterstützt. Konzept und Ansatz ähneln den [virtuellen Blattkomponenten](#virtual-leaf-components).

Der Frontend-Entwickler kann die Container-Komponenten an geeigneten Stellen innerhalb des SPA hinzufügen. Diese Komponenten zeigen Platzhalter an, wenn sie im Editor in AEM geöffnet werden. Der Autor kann dann Komponenten und deren Inhalt zum Container hinzufügen, der die erforderlichen Knoten in der JCR-Struktur erstellt.

Wenn beispielsweise ein Container unter `/root/responsivegrid`und der Entwickler einen untergeordneten Container hinzufügen möchte:

![Container-Speicherort](assets/container-location.png)

Die `newContainer` existiert noch nicht in der AEM.

Wenn Sie in AEM die Seite bearbeiten, die diese Komponente enthält, wird ein leerer Platzhalter für einen Container angezeigt, dem Autorinnen und Autoren Inhalte hinzufügen können.

![Container-Platzhalter](assets/container-placeholder.png)

![Container-Speicherort in JCR](assets/container-jcr-structure.png)

Sobald der Autor dem Container eine untergeordnete Komponente hinzufügt, wird der neue Container-Knoten mit dem entsprechenden Namen in der JCR-Struktur angelegt.

![Container mit Inhalten](assets/container-with-content.png)

![Container mit Inhalten in JCR](assets/container-with-content-jcr.png)

Dem Container können jetzt mehr Komponenten und Inhalte hinzugefügt werden, da der Autor dies benötigt und die Änderungen beibehalten werden.

#### Anforderungen und Einschränkungen {#container-limitations}

Es gibt verschiedene Anforderungen zum Hinzufügen virtueller Container und einige Einschränkungen.

* Die Richtlinie zum Bestimmen, welche Komponenten hinzugefügt werden können, wird vom übergeordneten Container übernommen.
* Das unmittelbare übergeordnete Element des zu erstellenden Containers muss in AEM vorhanden sein.
   * Wenn der Container `root/responsivegrid` im AEM-Container vorhanden ist, kann ein neuer Container durch Angabe des Pfads erstellt werden `root/responsivegrid/newContainer`.
   * `root/responsivegrid/newContainer/secondNewContainer` ist jedoch nicht möglich.
* Es kann jeweils nur eine neue Komponentenebene erstellt werden.

## Zusätzliche Anpassungen {#additional-customizations}

Wenn Sie den vorherigen Beispielen gefolgt sind, kann Ihre externe SPA jetzt in AEM bearbeitet werden. Es gibt jedoch zusätzliche Aspekte Ihrer externen SPA, die Sie weiter anpassen können.

### Stammknoten-ID {#root-node-id}

Standardmäßig können Sie davon ausgehen, dass die React-Anwendung in einem `div` Element-ID `spa-root`. Bei Bedarf kann diese Syntax angepasst werden.

Angenommen, Sie verfügen über eine SPA, in der die Anwendung in einem `div` Element-ID `root`. Diese Syntax muss in drei Dateien übernommen werden.

1. Im `index.js` der React-Programm (oder wo `ReactDOM.render()` aufgerufen wird)

   ![ReactDOM.render() in der index.js](assets/external-spa-root-index.png)

1. In der `index.html` des React-Programms

   ![index.html des Programms](assets/external-spa-index.png)

1. Führen Sie im Hauptteil der Seitenkomponente der AEM-App zwei Schritte aus:

   1. Erstellen Sie eine `body.html` für die Seitenkomponente.

   ![Erstellen einer Datei &quot;body.html&quot;](assets/external-spa-update-body.gif)

   1. Fügen Sie das Stammelement in der neuen `body.html` -Datei.

   ![Stammelement zu body.html hinzufügen](assets/external-spa-add-root.png)

### Bearbeiten einer React-SPA mit Routing {#editing-react-spa-with-routing}

Wenn das externe React-SPA-Programm über mehrere Seiten verfügt, kann [sie mithilfe von Routing die zu rendernde Seite/Komponente bestimmen](/help/implementing/developing/hybrid/routing.md). Der grundlegende Anwendungsfall ist der Abgleich der aktuell aktiven URL mit dem für eine Route bereitgestellten Pfad. Um die Bearbeitung in solchen Routinganwendungen zu aktivieren, muss der Pfad, mit dem abgeglichen werden soll, transformiert werden, um AEM spezifische Informationen aufzunehmen.

Im folgenden Beispiel haben Sie eine einfache React-Anwendung mit zwei Seiten. Die Seite, die gerendert werden soll, wird durch den Abgleich des an den Router übergebenen Pfads mit der aktiven URL bestimmt. Wenn Sie beispielsweise auf `mydomain.com/test`, `TestPage` wird gerendert.

![Routing in einer externen SPA](assets/external-spa-routing.png)

Um die Bearbeitung in AEM für diese Beispiel-SPA zu aktivieren, sind die folgenden Schritte erforderlich.

1. Identifizieren Sie die Ebene, die als Stamm in AEM fungieren würde.

   * Betrachten Sie für Ihr Beispiel wknd-spa-react/us/en als Wurzel des SPA. Dieser Stamm bedeutet, dass alles vor diesem Pfad nur Seiten/Inhalte AEM.

1. Erstellen Sie eine Seite auf der erforderlichen Ebene.

   * In diesem Beispiel lautet die zu bearbeitende Seite `mydomain.com/test`. `test` befindet sich im Stammpfad der App. Dieser Stammpfad muss auch beim Erstellen der Seite in AEM beibehalten werden. Daher können Sie eine Seite auf der im vorherigen Schritt definierten Stammebene erstellen.
   * Die neu erstellte Seite muss denselben Namen haben wie die zu bearbeitende Seite. In diesem Beispiel gilt Folgendes: `mydomain.com/test`, muss die neu erstellte Seite `/path/to/aem/root/test`.

1. Fügen Sie Helfer innerhalb des SPA-Routings hinzu.

   * Die neu erstellte Seite kann den erwarteten Inhalt noch nicht in AEM rendern. Der Grund dafür ist, dass der Router einen Pfad von `/test` in der Erwägung, dass AEM aktive Pfad `/wknd-spa-react/us/en/test`. Um den AEM spezifischen Teil der URL aufzunehmen, müssen Sie einige Helfer auf der SPA hinzufügen.

   ![Routing-Helfer](assets/external-spa-router-helper.png)

   * Die `toAEMPath` Helfer bereitgestellt von `@adobe/cq-spa-page-model-manager` verwendet werden. Er wandelt den für das Routing bereitgestellten Pfad so um, dass er AEM-spezifische Teile enthält, wenn das Programm auf einer AEM-Instanz geöffnet ist. Es werden drei Parameter akzeptiert:
      * Der für das Routing erforderliche Pfad
      * Die ursprüngliche URL der AEM-Instanz, in der die SPA bearbeitet wird
      * Das Projektstammverzeichnis in AEM, wie im ersten Schritt festgelegt

   * Diese Werte können für mehr Flexibilität als Umgebungsvariablen festgelegt werden.

1. Überprüfen Sie die Bearbeitung der Seite in AEM.

   * Stellen Sie das Projekt in AEM bereit und navigieren Sie zur neu erstellten `test`-Seite. Der Seiteninhalt wird jetzt gerendert und die AEM-Komponenten können bearbeitet werden.

## Framework-Einschränkungen {#framework-limitations}

Die RemotePage-Komponente erwartet, dass die Implementierung ein Asset-Manifest wie das hier [gefundene bereitstellt](https://github.com/shellscape/webpack-manifest-plugin). Die RemotePage-Komponente wurde jedoch nur für die Verwendung mit dem React-Framework getestet (und Next.js über die Komponente &quot;remote-page-next&quot;) und unterstützt daher nicht das Remote-Laden von Anwendungen aus anderen Frameworks wie Angular.

## Zusätzliche Ressourcen {#additional-resources}

Das folgende Referenzmaterial kann hilfreich sein, um SPAs im Kontext der AEM zu verstehen.

* [Headful und Headless in AEM](/help/implementing/developing/headful-headless.md)
* [AEM-Projekt-Archetyp](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=de)
* [WKND-SPA-Projekt](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/spa-editor/spa-editor-framework-feature-video-use.html?lang=de)
* [Erste Schritte mit SPAs in AEM unter Verwendung von React](/help/implementing/developing/hybrid/getting-started-react.md)
* [SPA-Referenzmaterialien (API-Referenzen)](/help/implementing/developing/hybrid/reference-materials.md)
* [SPA-Blueprint und PageModelManager](/help/implementing/developing/hybrid/blueprint.md#pagemodelmanager)
* [SPA-Modell-Routing](/help/implementing/developing/hybrid/routing.md)
* [Single Page Applications (SPAs) und Server-seitiges Rendering](/help/implementing/developing/hybrid/ssr.md)
