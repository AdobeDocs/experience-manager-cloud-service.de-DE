---
title: Inhaltsfragmente
description: Mit Inhaltsfragmenten in Adobe Experience Manager as a Cloud Service können Sie kanalunabhängige Inhalte entwerfen, erstellen, kuratieren und verwenden, die auch bei der Seitenerstellung verwendet werden können.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 7a44fc4e-3793-4aa3-8c21-db0567c93244
solution: Experience Manager Sites
feature: Authoring, Content Fragments
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '1278'
ht-degree: 99%

---

# Inhaltsfragmente {#content-fragments}

Inhaltsfragmente in Adobe Experience Manager (AEM) as a Cloud Service werden [als seitenunabhängige Assets erstellt und verwaltet](/help/sites-cloud/administering/content-fragments/overview.md), sodass Sie kanalneutrale Inhalte zusammen mit (möglicherweise kanalspezifischen) Varianten erstellen können. Sie können diese Fragmente und ihre Varianten bei der Erstellung Ihrer Inhaltsseiten verwenden.

>[!CAUTION]
>
>Lesen Sie diese Seite gemeinsam mit [Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/overview.md) (und den zugehörigen Seiten), da dort grundlegende Termini und Konzepte sowie Informationen zum Erstellen und Verwalten von Fragmenten und zum Bereitstellen von strukturierten Inhaltsfragmenten für andere Kanäle als AEM-Seiten vorgestellt werden.

>[!NOTE]
>
>Inhaltsfragmente sind eine **Sites**-Eigenschaft, werden jedoch als **Assets** gespeichert.
>
>Sie werden jetzt hauptsächlich mit der **[Inhaltsfragmente](/help/sites-cloud/administering/content-fragments/overview.md#content-fragments-console)**-Konsole verwaltet, können jedoch weiterhin über die **[Assets](/help/assets/content-fragments/content-fragments-managing.md)**-Konsole verwaltet werden. 
>
>Der Standardeditor für [Inhaltsfragmente – Authoring](/help/sites-cloud/administering/content-fragments/authoring.md) ist der neue Editor, auf den sowohl über die **Inhaltsfragmente-** als auch über die **Assets**-Konsole zugegriffen werden kann.
>
>Um den [ursprünglichen Editor](/help/assets/content-fragments/content-fragments-variations.md) zu verwenden, öffnen Sie zunächst den neuen Editor und deaktivieren Sie dann den Schalter **Neuer Editor**.

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-cloud/authoring/fragments/content-fragments.md)** sind unterschiedliche Funktionen in AEM:
>
>* **Inhaltsfragmente** sind redaktionelle Inhalte mit Definition und Struktur, aber ohne zusätzliches visuelles Design und/oder Layout. Sie können unter anderem für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.
>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.
>
>Weitere Details finden Sie in den [Informationen zu Inhaltsfragmenten und Experience Fragments in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=de#content-fragments).

Die Inhaltsfragmente ermöglichen Folgendes:

* **Marketing- und Kampagnenstrategie**
   * Überprüfen von Inhalten über zentral verwaltete Inhaltsfragmente.
* **Creative Pro**
   * Tracking von Kreativ-Assets über Sammlungen, die mit Inhaltsfragmenten verknüpft sind.
* **Copywriter**
   * Schreiben im Inhaltsfragment-Editor von AEM.
   * Können Inhaltsvarianten erstellen.
   * Können relevante Inhalte mit dem Inhaltsfragment verknüpfen.
   * Können Versionierung/Workflow verwenden.
   * Können Inhaltsfragmente freigeben.
   * Können Übersetzungen zentral verwalten.
* **Produzenten und Journey-Manager**
   * Auswahl aus vordefinierten Fragmenten und Varianten mit Authoring in AEM.
   * Können sich darauf verlassen, dass Fragmente und verknüpfte Inhalte immer aktuell sind, da Copywriter und Kreative ihre Aktualisierungen in zentral verwalteten Fragmenten und Assets vornehmen.
   * Können sich darauf verlassen, dass verknüpfte Medieninhalte im Hinblick auf ihre Relevanz kuratiert werden.
   * Können spontan Ad-hoc-Inhaltsvarianten erstellen und gleichzeitig sicherstellen, dass diese Varianten zentral im Fragment verwaltet werden.

## Hinzufügen eines Inhaltsfragments zu Ihrer Seite {#adding-a-content-fragment-to-your-page}

1. Öffnen Sie Ihre Seite zum Bearbeiten.
2. Fügen Sie die **Inhaltsfragmentkomponente** hinzu; entweder aus dem **Komponenten-Browser** oder mit **Neue Komponente einfügen**.
3. Wählen Sie eine der folgenden Möglichkeiten:
   * Öffnen Sie den **Assets**-Browser und filtern Sie nach der Option **Inhaltsfragmente** (die Standardeinstellung ist „Bilder“). Ziehen Sie dann das gewünschte Fragment auf die entsprechende Komponente.
   * Wählen Sie die Inhaltsfragmentkomponente und dann **Konfigurieren** aus der Symbolleiste. Im daraufhin angezeigten Dialogfeld können Sie das Auswahldialogfeld zum Durchsuchen und Auswählen des gewünschten **Inhaltsfragments** öffnen.

   >[!NOTE]
   >
   >Eine alternative Methode besteht darin, ein bestimmtes Inhaltsfragment direkt auf die Seite zu ziehen. Dabei wird automatisch die zugehörige Komponente (Inhaltsfragment) erstellt.

4. Anfangs wird der Inhalt aus den Elementen **Allgemein** und **Master** (Variante) angezeigt. Sie können nach Bedarf aber [auch andere Elemente und/oder Varianten auswählen](#selecting-the-element-or-variation).

   ![Inhaltsfragmente im Assets-Browser](/help/sites-cloud/authoring/assets/content-fragments.png)

   >[!NOTE]
   >
   >Weitere Informationen zur Bearbeitungsfunktion finden Sie unter:
   >
   >* [Responsives Layout](/help/sites-cloud/authoring/page-editor/responsive-layout.md)
   >* [Bearbeiten des Seiteninhalts](/help/sites-cloud/authoring/page-editor/edit-content.md)

### Auswählen des Elements oder der Variante {#selecting-the-element-or-variation}

Öffnen Sie das Dialogfeld **Konfiguration** des Fragments, um das Fragment für die Verwendung auf der aktuellen Seite zu konfigurieren. Das Dialogfeld kann von der verwendeten Komponente abhängen.

>[!NOTE]
>
>Siehe auch [Kernkomponenten, die Inhaltsfragment-Komponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=de)

Im entsprechenden Konfigurationsdialogfeld können Sie die verfügbaren Parameter auswählen, darunter:

* **Inhaltsfragment**
   * Geben Sie das zu verwendende Fragment an.
* **Anzeigemodus**:
   * **Einzelnes Textelement**
   * **Mehrere Elemente**
* **Element**
   * Je nach verwendetem Modell ist eine Auswahl verfügbar.

  >[!NOTE]
  >
  >Die verfügbaren Elemente hängen von dem verwendeten Modell ab.

* **Variante**
   * Die Standardeinstellung **Master** ist immer verfügbar.
   * Eine Auswahl ist verfügbar, wenn Varianten für das Fragment erstellt wurden.

* **ID**

   * **HTML-ID**-Attribut, das auf die Komponente angewandt wird.

### Schnelle Verbindung zum Fragmenteditor {#quick-connection-to-fragment-editor}

Sie können die Fragmentquelle zur Bearbeitung (das Asset) mithilfe des Symbols **Bearbeiten** in der Komponenten-Symbolleiste öffnen. Auf diese Weise können Sie [das Inhaltsfragment bearbeiten und verwalten](/help/sites-cloud/administering/content-fragments/overview.md).

>[!CAUTION]
>
>Wie immer hat die Bearbeitung der Fragmentquelle Auswirkungen auf alle Seiten, auf die diese Inhaltsfragmente verweisen.

### Hinzufügen von Zwischeninhalten {#adding-in-between-content}

Wenn ein bestimmtes Inhaltsfragment zur Seite hinzugefügt wird, gibt es einen Platzhalter **Komponenten hierher ziehen** zwischen jedem HTML-Absatz (und am oberen/unteren Rand) des Fragments.

Damit können Sie zusätzliche Inhalte [zwischen (d. h. Zwischeninhalte)](/help/assets/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) dem Fragmentinhalt (an einer der verfügbaren Stellen) hinzufügen, ohne das Stammfragment ändern zu müssen.

Für Zwischeninhalte haben Sie folgende Möglichkeiten:

* Hinzufügen von Komponenten über den [Komponenten-Browser](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser)
* Hinzufügen von Assets über den [Assets-Browser](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#assets-browser)
* [Zugehörige Inhalte](#using-associated-content) als Quelle für Zwischeninhalte verwenden.

>[!CAUTION]
>
>Bei Zwischeninhalten handelt es sich um Seiteninhalte. Sie werden nicht im Inhaltsfragment gespeichert.

![Komponente einfügen](/help/sites-cloud/authoring/assets/content-fragments-insert.png)

>[!NOTE]
>
>Sie können auch [visuelle Elemente (Bilder) in das Fragment selbst einfügen](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>Die in das Inhaltsfragment eingefügten visuellen Assets werden mit dem vorangehenden Absatz verbunden. Deshalb können Zwischeninhalte nicht zwischen einem visuellen Asset und dem vorangehenden Absatz platziert werden. Wenn Sie diese Verbindungsebene benötigen, können Sie das Bild dem Fragment hinzufügen (als ein [Fragment mit gemischten Medien](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets)).

>[!CAUTION]
>
>Wenn Sie Zwischeninhalte zu einem Inhaltsfragment auf Ihrer Seite hinzugefügt haben, kann das Ändern der Struktur des zugrunde liegenden Inhaltsfragments (d. h. im Inhaltsfragment-Editor) zu fehlerhaften/unerwarteten Ergebnissen führen.
>
>Wenn dies eintritt, wird der Zwischeninhalt unverändert beibehalten:
>
>* Zwischenkomponenten haben eine absolute Position innerhalb der Komponentensequenz im Fragmentfluss. Diese Position ändert sich nicht, auch wenn sich der Inhalt der Absätze im Fragment ändert.
>
>  Dies kann den Eindruck erwecken, als hätte sich die relative Position geändert, da Zwischenabsätze keinen kontextuellen Bezug zu den Absätzen (des Fragments) haben, neben denen sie sich befinden.
>
>* Wenn zwischen zwei Absatzstrukturen ein Konflikt besteht, wird der Zwischeninhalt nicht angezeigt (obwohl er intern noch vorhanden ist).

### Verwenden von zugehörigen Inhalten {#using-associated-content}

Wenn Sie Inhalt mit dem [Inhaltsfragment](/help/assets/content-fragments/content-fragments.md) [verknüpft](/help/assets/content-fragments/content-fragments-assoc-content.md) haben, sind diese Assets im seitlichen Panel verfügbar (nachdem Sie Ihr Fragment auf der Inhaltsseite platziert haben). Verknüpfte Inhalte sind im Grunde eine besondere Inhaltsquelle für [Zwischeninhalte](/help/assets/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments).

>[!NOTE]
>
>Es gibt verschiedene Methoden zum Hinzufügen von [visuellen Assets (z. B. Bildern)](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) zu einem Fragment und/oder zu einer Seite.

>[!NOTE]
>
>Wenn Sie mehrere Inhaltsfragmente auf einer Seite haben, werden auf der Registerkarte **Zugehörige Inhalte** die zu allen Fragmenten gehörenden Assets angezeigt.

Nachdem Sie ein Fragment mit verknüpftem Inhalt zu Ihrer Seite hinzugefügt haben, wird eine neue Registerkarte (**Verknüpfte Inhalte**) im Seitenbereich geöffnet.

Von hier aus können Sie die Assets an die gewünschte Position ziehen (entweder zu einer vorhandenen Komponente oder an die gewünschte Position, an der die entsprechende Komponente erstellt wird):

![Einfügen eines Bildes](/help/sites-cloud/authoring/assets/content-fragments-image.png)

### In das Fragment eingefügte Assets {#assets-inserted-into-the-fragment}

Wenn Assets (z. B. Bilder) in das Fragment selbst eingefügt wurden (als [Fragmente mit gemischten Medien](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets)), sind die Optionen zur Bearbeitung dieser Assets im Seiten-Editor eingeschränkt.

Beispielsweise haben Sie zur Bearbeitung eines Bildes folgende Möglichkeiten:

* Zuschneiden, Drehen oder Spiegeln des Bildes.
* Fügen Sie einen Titel oder alternativen Text hinzu.
* Geben Sie eine Größe an.
* Sie können auch das Layout konfigurieren.

Andere Änderungen wie Verschieben, Kopieren und Löschen müssen im Fragmenteditor vorgenommen werden.

### Veröffentlichung {#publishing}

Fragmente müssen zuerst veröffentlicht werden, damit sie auf Ihren veröffentlichten Web-Seiten verwendet werden können:

* Ein Fragment kann veröffentlicht werden, nachdem [es in der Inhaltsfragmentkonsole erstellt wurde](/help/sites-cloud/administering/content-fragments/managing.md#publishing-and-previewing-a-fragment).
* Wenn ein *unveröffentlichtes Fragment* auf einer Seite verwendet wird, die veröffentlicht wird, kann das Fragment gleichzeitig mit der Seite veröffentlicht werden.

## Exportieren von Inhaltsfragmenten {#exporting-content-fragments}

Für den Export in Adobe Target kann JSON verwendet werden, um das Fragment bereitzustellen. Siehe:

* [Integrieren mit Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Exportieren von Inhaltsfragmenten nach Adobe Target](/help/sites-cloud/integrating/content-fragments-target.md)
