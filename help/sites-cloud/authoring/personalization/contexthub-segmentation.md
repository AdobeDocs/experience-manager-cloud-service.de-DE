---
title: Konfigurieren der Segmentierung mit ContextHub
description: Erfahren Sie, wie Sie die Segmentierung mit ContextHub konfigurieren.
translation-type: tm+mt
source-git-commit: 82ad2cda70dd664ac9456a04f34e2d5831687fc1
workflow-type: tm+mt
source-wordcount: '1372'
ht-degree: 60%

---


# Konfigurieren der Segmentierung mit ContextHub{#configuring-segmentation-with-contexthub}

Die Segmentierung ist bei der Erstellung einer Kampagne eine grundlegende Überlegung. See [Understanding Segmentation](segmentation.md) for information on how segmentation works and key terms.

Je nach den von Ihnen bereits zu den Besuchern Ihrer Site erfassten Informationen sowie je nach Ihren angepeilten Zielen müssen Sie die erforderlichen Segmente und Strategien für Ihre zielgerichteten Inhalte festlegen.

Diese Segmente werden dann verwendet, um einem Besucher gezielt bestimmte Inhalte bereitzustellen. Hier festgelegte [Aktivitäten](activities.md) können auf jeder Seite einbezogen werden – und sie können bestimmen, auf welches Besuchersegment die spezialisierten Inhalte angewendet werden sollen.

AEM ermöglicht Ihnen die einfache Personalisierung der Benutzererfahrungen. Außerdem können Sie damit die Ergebnisse Ihrer Segmentdefinitionen überprüfen.

## Zugriff auf Segmente {#accessing-segments}

The [Audiences](audiences.md) console is used to manage segments for ContextHub as well as audiences for your Adobe Target account. Diese Dokumentation befasst sich mit der Verwaltung von Segmenten für ContextHub.

Zum Zugriff auf Ihre Segmente wählen Sie in der globalen Navigation die Optionen **Navigation > Personalisierung > Zielgruppen** aus.

![Verwalten von Audiencen](/help/sites-cloud/authoring/assets/contexthub-segmentation-audiences.png)

## Segment-Editor {#segment-editor}

<!--The **Segment Editor** allows you to easily modify a segment. To edit a segment, select a segment in the [list of segments](/help/sites-administering/segmentation.md#accessing-segments) and click the **Edit** button.-->
The **Segment Editor** allows you to easily modify a segment. Wählen Sie zur Bearbeitung eines Segments ein Segment aus der Liste von Segmenten aus und klicken Sie auf die Schaltfläche **Bearbeiten**.

![Segment-Editor](/help/sites-cloud/authoring/assets/contexthub-segment-editor.png)

Using the components browser you can add **AND** and **OR** containers to define the segment logic, then add additional components to compare properties and values or reference scripts and other segments to define the selection criteria (see [Creating a New Segment](#creating-a-new-segment)) to define the exact scenario for selecting the segment.

Wenn die gesamte Anweisung mit „true“ bewertet wurde, wird das Segment aufgelöst. Falls mehrere Segmente zutreffen, wird außerdem der Faktor **Verstärken** verwendet. See [Creating a New Segment](#creating-a-new-segment) for details on the boost factor.

>[!CAUTION]
>
>Der Segment-Editor prüft nicht auf Zirkelbezüge. Beispiel: Segment A verweist auf ein anderes Segment B, das wiederum auf Segment A verweist. Sie müssen sicherstellen, dass Ihre Segmente keine kreisförmigen Verweise enthalten.

### Container {#containers}

Die folgenden Container sind standardmäßig verfügbar und ermöglichen Ihnen die Gruppierung von Vergleichen und Verweisen zum Zweck einer booleschen Bewertung. Sie können vom Komponentenbrowser in den Editor gezogen werden. See the following section [Using AND and OR Containers](#using-and-and-or-containers) for more information.

|  |  |
|---|---|
| UND-Container | Der boolesche AND-Operator |
| ODER-Container | Der boolesche OR-Operator |

### Vergleiche {#comparisons}

Die folgenden Segmentvergleiche sind standardmäßig für die Bewertung der Segmenteigenschaften verfügbar. Sie können vom Komponentenbrowser in den Editor gezogen werden.

|  |  |
|---|---|
| property-value | Vergleicht eine Eigenschaft eines Stores mit einem definierten Wert |
| property-property | Vergleicht eine Eigenschaft eines Stores mit einer anderen Eigenschaft |
| Eigenschafts-/Segmentreferenz | Vergleicht eine Eigenschaft eines Stores mit einem anderen referenzierten Segment |
| PropertyScript-Referenz | Vergleicht eine Eigenschaft eines Stores mit den Ergebnissen eines Skripts |
| Segmentreferenz - Skriptreferenz | Vergleicht ein referenziertes Segment mit den Ergebnissen eines Skripts |

>[!NOTE]
>
>Wenn beim Vergleich von Werten der Datentyp des Vergleichs nicht festgelegt ist (d. h. automatisch erkannt wird), vergleicht die ContextHub-Segmentierungsengine die Werte einfach wie JavaScript. Sie verteilt keine Werte an die erwarteten Typen, was zu irreführenden Ergebnissen führen kann. Beispiel:
>
>`null < 30 // will return true`
>
>Therefore when [creating a segment](#creating-a-new-segment), you should select a **data type** whenever the types of compared values are known. Beispiel:
>
>When comparing the property `profile/age`, you already know that the compared type will be **number**, so even if `profile/age` is not set, a comparison `profile/age` less-than 30 will return **false**, as you would expect.

### Verweise {#references}

Die folgenden Verweise sind standardmäßig für die direkte Verknüpfung eines Skripts oder eines anderen Segments verfügbar. Sie können vom Komponentenbrowser in den Editor gezogen werden.

|  |  |
|---|---|
| Segment-Verweis | Bewerten Sie das referenzierte Segment |
| Skript-Referenz | Bewerten Sie das referenzierte Skript. Weitere Informationen finden Sie im folgenden Abschnitt [Verwenden von Skriptverweisen](#using-script-references) . |

## Erstellen eines neuen Segments {#creating-a-new-segment}

So legen Sie Ihr neues Segment fest:

1. Klicken oder tippen Sie nach dem [Zugriff auf die Segmente](#accessing-segments) auf die Schaltfläche „Erstellen“ und wählen Sie **ContextHub-Segment erstellen** aus.

   ![hinzufügen](/help/sites-cloud/authoring/assets/contexthub-create-segment.png)

1. Geben Sie unter **Neues ContextHub-Segment** einen Titel für das Segment sowie bei Bedarf einen Verstärkungswert ein und tippen oder klicken Sie auf **Erstellen**.

   ![Neues Segment](/help/sites-cloud/authoring/assets/contexthub-new-segment.png)

   Jedes Segment verfügt über einen Boost-Parameter, der als Gewichtungsfaktor verwendet wird. Eine höhere Zahl zeigt an, dass das Segment in Instanzen mit mehreren gültigen Segmenten bei der Auswahl gegenüber einem Segment mit einer niedrigeren Zahl bevorzugt wird.

   * Mindestwert: `0`
   * Höchstwert: `1000000`

1. Bearbeiten Sie in der Segmentkonsole Ihr neu erstelltes Segment, um es im Segment-Editor zu öffnen.
1. Ziehen Sie einen Vergleich oder Verweis in den Segment-Editor. Der Vergleich oder Verweis wird dann im standardmäßigen UND-Container angezeigt.
1. Doppelklicken oder tippen Sie auf die Konfigurationsoption des neuen Verweises oder Segments, um die spezifischen Parameter zu bearbeiten. In diesem Beispiel testen wir Menschen in Basel.

   ![Tests für Menschen in Basel](/help/sites-cloud/authoring/assets/contexthub-comparing-property-value.png)

   Legen Sie möglichst immer einen **Datentyp** fest, um die ordnungsgemäße Bewertung Ihrer Vergleiche sicherzustellen. Weitere Informationen finden Sie unter [Vergleiche](#comparisons).

1. Click **Done** to save your definition:
1. Fügen Sie bei Bedarf weitere Komponenten hinzu. Sie können boolesche Ausdrücke anhand der Containerkomponenten für UND- und ODER-Vergleiche formulieren (siehe [Verwenden von UND- und ODER-Containern](#using-and-and-or-containers) weiter unten). Mit dem Segment-Editor können Sie nicht mehr benötigte Komponenten löschen oder diese an neue Positionen innerhalb der Anweisung ziehen.

### Verwenden von UND- und ODER-Containern {#using-and-and-or-containers}

Mithilfe von UND- und ODER-Containerkomponenten können Sie komplexe Segmente in AEM erstellen. Hierbei ist es hilfreich, sich einige grundlegende Punkte bewusst zu machen:

* Die oberste Ebene der Definition ist immer der UND-Container, der ursprünglich erstellt wurde. Dies kann nicht geändert werden, hat aber keine Auswirkungen auf den Rest Ihrer Segmentdefinition.
* Stellen Sie sicher, dass die Verschachtelung Ihrer Container Sinn ergibt. Die Container können als die Klammern Ihres booleschen Ausdrucks betrachtet werden.

Im folgenden Beispiel werden Besucher ausgewählt, die in unserer Schweizer Zielpopulation berücksichtigt werden:

```text
 People in Basel

 OR

 People in Zürich
```

Beginnen Sie damit, eine ODER-Containerkomponente innerhalb des standardmäßigen UND-Containers zu platzieren. Innerhalb des ODER-Containers können Sie die Eigenschaften- oder Referenzkomponenten hinzufügen.

![Segment mit ODER-Operator](/help/sites-cloud/authoring/assets/contexthub-or-operator.png)

Sie können bei Bedarf mehrere UND- und ODER-Operatoren verschachteln.

### Verwenden von Skript-Referenzen {#using-script-references}

Durch die Verwendung der Skript-Referenzkomponente kann die Bewertung einer Segmenteigenschaft an ein externes Skript delegiert werden. Sobald das Skript ordnungsgemäß konfiguriert ist, kann es als eine beliebige andere Komponente einer Segmentbedingung verwendet werden.

#### Definieren eines Skripts für einen Verweis {#defining-a-script-to-reference}

1. Add file to `contexthub.segment-engine.scripts` clientlib.
1. Implementieren Sie eine Funktion, durch die ein Wert ausgegeben wird. Beispiel:

   ```javascript
   ContextHub.console.log(ContextHub.Shared.timestamp(), '[loading] contexthub.segment-engine.scripts - script.profile-info.js');
   
   (function() {
       'use strict';
   
       /**
        * Sample script returning profile information. Returns user info if data is available, false otherwise.
        *
        * @returns {Boolean}
        */
       var getProfileInfo = function() {
           /* let the SegmentEngine know when script should be re-run */
           this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
           this.dependOn(ContextHub.SegmentEngine.Property('profile/givenName'));
   
           /* variables */
           var name = ContextHub.get('profile/givenName');
           var age = ContextHub.get('profile/age');
   
           return name === 'Joe' && age === 123;
       };
   
       /* register function */
       ContextHub.SegmentEngine.ScriptManager.register('getProfileInfo', getProfileInfo);
   
   })();
   ```

1. Register the script with `ContextHub.SegmentEngine.ScriptManager.register`.

Wenn das Skript von zusätzlichen Eigenschaften abhängig ist, sollte dieses `this.dependOn()` () abrufen. For example if the script depends on `profile/age`:

```javascript
this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
```

#### Verweisen auf ein Skript {#referencing-a-script}

1. Erstellen Sie ein ContextHub-Segment.
1. Fügen Sie eine **Skript-Referenz**-Komponente an der gewünschten Stelle des Segments hinzu.
1. Öffnen Sie das Dialogfeld der **Skript-Referenz**-Komponente. Ist das Skript [ordnungsgemäß konfiguriert](#defining-a-script-to-reference), sollte es im Dropdown-Menü **Skriptname** verfügbar sein.

## Testen der Anwendung eines Segments {#testing-the-application-of-a-segment}

Sobald das Segment definiert wurde, können die potenziellen Ergebnisse mithilfe von **[ContextHub](contexthub.md)getestet werden.**

1. Vorschau einer Seite
1. Klicken Sie auf das ContextHub-Symbol, damit die ContextHub-Symbolleiste angezeigt wird.
1. Wählen Sie eine Rolle aus, die mit dem von Ihnen erstellten Segment übereinstimmt.
1. Der ContextHub löst die entsprechenden Elemente für die ausgewählte Rolle auf.

Beispielsweise basiert unsere einfache Segmentdefinition zur Identifizierung von Benutzern in Basel auf dem Standort des Benutzers. Das Laden einer spezifischen Rolle, die mit diesen Kriterien übereinstimmt, zeigt, ob das Segment erfolgreich aufgelöst wurde:

![Segment, das aufgelöst wird](/help/sites-cloud/authoring/assets/contexthub-segment-resolve.png)

Oder ob es nicht aufgelöst wurde:

![Segment, das nicht aufgelöst wird](/help/sites-cloud/authoring/assets/contexthub-segment-doesnt-resolve.png)

>[!NOTE]
>
>Alle Eigenschaften werden sofort aufgelöst, obwohl die meisten sich nur beim erneuten Laden der Seite ändern.

Solche Tests können auch zu Inhaltsseiten und in Kombination mit gezieltem Inhalt und damit verbundenen **Aktivitäten** und **Erlebnissen** durchgeführt werden.

Wenn Sie eine Aktivität und ein Erlebnis eingerichtet haben, können Sie Ihr Segment einfach mit der Aktivität testen. Weitere Details zur Einrichtung einer Aktivität finden Sie in der entsprechenden [Dokumentation zur Bearbeitung gezielter Inhalte](targeted-content.md).

1. Im Bearbeitungsmodus einer Seite, auf der Sie gezielte Inhalte eingerichtet haben, können Sie anhand des Pfeilsymbols auf dem Inhalt erkennen, dass es sich um gezielten Inhalt handelt.
1. Wechseln Sie in den Vorschaumodus und anschließend mithilfe von ContextHub zu einer Rolle, die nicht mit der für das Erlebnis konfigurierten Segmentierung übereinstimmt.
1. Wechseln Sie zu einer Rolle, die nicht mit der für das Erlebnis konfigurierten Segmentierung übereinstimmt, und sehen Sie, wie sich das Erlebnis entsprechend verändert.

## Verwenden Ihres Segments {#using-your-segment}

Segmente werden verwendet, um den tatsächlichen Inhalt zu steuern, der von bestimmten Audiencen der Zielgruppe gesehen wird. See [Managing Audiences](audiences.md) for more information about audiences and segments and [Authoring Targeted Content](targeted-content.md) about using audiences and segments to target content.
