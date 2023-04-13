---
title: Inhaltsfragmente
description: Inhaltsfragmente in Adobe Experience Manager as a Cloud Service ermöglichen Ihnen das Entwerfen, Erstellen, Kuratieren und Verwenden von seitenunabhängigen Inhalten
exl-id: 7a44fc4e-3793-4aa3-8c21-db0567c93244
source-git-commit: 7ce05d282d553c5552cd828d08aaf6b7b5fb4e05
workflow-type: tm+mt
source-wordcount: '1227'
ht-degree: 66%

---

# Inhaltsfragmente {#content-fragments}

Inhaltsfragmente in Adobe Experience Manager (AEM) as a Cloud Service werden als [seitenunabhängige Assets erstellt und verwaltet](/help/sites-cloud/administering/content-fragments/content-fragments.md).

Sie ermöglichen es Ihnen, kanalneutrale Inhalte zusammen mit (möglicherweise kanalspezifischen) Varianten zu erstellen. Sie können diese Fragmente und ihre Varianten bei der Erstellung Ihrer Inhaltsseiten verwenden.

In Verbindung mit dem aktualisierten JSON Exporter können strukturierte Inhaltsfragmente auch verwendet werden, um AEM-Inhalte über Content Services anderen Kanälen als AEM-Seiten bereitzustellen.

>[!NOTE]
>
>**Inhaltsfragmente** und **[Experience Fragments](/help/sites-cloud/authoring/fundamentals/experience-fragments.md)** sind unterschiedliche Funktionen in AEM:
>* **Inhaltsfragmente** sind redaktionelle Inhalte mit Definition und Struktur, aber ohne zusätzliches visuelles Design und/oder Layout. Sie können unter anderem für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.
>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.
>
>Weitere Details finden Sie in den [Informationen zu Inhaltsfragmenten und Experience Fragments in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=de#content-fragments).

>[!CAUTION]
>
>Lesen Sie diese Seite gemeinsam mit [Arbeiten mit Inhaltsfragmenten](/help/sites-cloud/administering/content-fragments/content-fragments.md) (und den zugehörigen Seiten), da dort grundlegende Termini und Konzepte sowie die Erstellung und Verwaltung von Fragmenten erklärt werden.

Die Inhaltsfragmente ermöglichen Folgendes:

* **Marketing- und Kampagnenstrategie**
   * Überprüfen Sie Inhalte über zentral verwaltete Inhaltsfragmente.
* **Creative Pro**
   * Tracking von kreativen Assets über Sammlungen, die mit Inhaltsfragmenten verknüpft sind.
* **Writer kopieren**
   * Schreiben Sie im Inhaltsfragment-Editor AEM.
   * Kann Inhaltsvarianten erstellen.
   * Kann relevante Inhalte mit dem Inhaltsfragment verknüpfen.
   * Kann Versionierung/Workflow verwenden.
   * Kann Inhaltsfragmente freigeben.
   * Kann Übersetzungen zentral verwalten.
* **Produzenten und Journey-Manager**
   * Wählen Sie aus vordefinierten Fragmenten und Varianten mit Authoring in AEM aus.
   * Kann sich darauf verlassen, dass Fragmente und verknüpfte Inhalte immer aktuell sind, da Autoren und Kreative ihre Aktualisierungen in zentral verwalteten Fragmenten und Assets vornehmen.
   * Kann sich darauf verlassen, dass verknüpfte Medieninhalte für Relevanz kuratiert werden.
   * Kann spontan Ad-hoc-Inhaltsvarianten erstellen und gleichzeitig sicherstellen, dass diese Varianten zentral im Fragment verwaltet werden.

## Hinzufügen eines Inhaltsfragments zu Ihrer Seite {#adding-a-content-fragment-to-your-page}

1. Öffnen Sie Ihre Seite zum Bearbeiten.
2. Fügen Sie die **Inhaltsfragmentkomponente** hinzu; entweder aus dem **Komponenten-Browser** oder mit **Neue Komponente einfügen**.
3. Wählen Sie eine der folgenden Möglichkeiten:
   * Öffnen Sie den **Assets**-Browser und filtern Sie nach der Option **Inhaltsfragmente** (die Standardeinstellung ist „Bilder“). Ziehen Sie dann das gewünschte Fragment auf die Komponenteninstanz.
   * Wählen Sie die Inhaltsfragmentkomponente und dann **Konfigurieren** aus der Symbolleiste. Im daraufhin angezeigten Dialogfeld können Sie das Auswahldialogfeld zum Durchsuchen und Auswählen des gewünschten **Inhaltsfragments** öffnen.

   >[!NOTE]
   >
   >Eine alternative Methode besteht darin, ein bestimmtes Inhaltsfragment direkt auf die Seite zu ziehen. Dabei wird automatisch die zugehörige Komponente (Inhaltsfragment) erstellt.

4. Anfangs wird der Inhalt aus den Elementen **Allgemein** und **Primär** (Variante) angezeigt. Sie können nach Bedarf aber [auch andere Elemente und/oder Varianten auswählen](#selecting-the-element-or-variation).

   ![Inhaltsfragmente im Assets-Browser](/help/sites-cloud/authoring/assets/content-fragments.png)

   >[!NOTE]
   >
   >Weitere Informationen zur Bearbeitungsfunktion finden Sie unter:
   >
   >* [Responsives Layout](/help/sites-cloud/authoring/features/responsive-layout.md)
   >* [Bearbeiten des Seiteninhalts](/help/sites-cloud/authoring/fundamentals/editing-content.md)


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
   * Die Standardversion **Primär** ist immer verfügbar.
   * Eine Auswahl ist verfügbar, wenn Varianten für das Fragment erstellt wurden.

* **ID**

   * **HTML-ID**-Attribut, das auf die Komponente angewandt wird.

### Schnelle Verbindung zum Fragmenteditor {#quick-connection-to-fragment-editor}

Sie können die Fragmentquelle zur Bearbeitung (das Asset) mithilfe des Symbols **Bearbeiten** in der Komponenten-Symbolleiste öffnen. Auf diese Weise können Sie [das Inhaltsfragment bearbeiten und verwalten](/help/sites-cloud/administering/content-fragments/content-fragments.md).

>[!CAUTION]
>
>Wie immer hat die Bearbeitung der Fragmentquelle Auswirkungen auf alle Seiten, auf die diese Inhaltsfragmente verweisen.

### Hinzufügen von Zwischeninhalten {#adding-in-between-content}

Wenn ein bestimmtes Inhaltsfragment zur Seite hinzugefügt wird, gibt es eine **Komponenten hierher ziehen** Platzhalter zwischen jedem HTML-Absatz (und am oberen/unteren Rand) des Fragments.

Auf diese Weise können Sie zusätzliche Inhalte hinzufügen [Zwischeninhalt (d. h. Zwischeninhalt)](/help/sites-cloud/administering/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) den Fragmentinhalt (an einem der verfügbaren Punkte), ohne das Stammfragment ändern zu müssen.

Für Übergangsinhalte haben Sie folgende Möglichkeiten:

* Komponenten aus der [Komponenten-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).
* Hinzufügen von Assets aus der [Asset-Browser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#assets-browser).
* [Zugehörige Inhalte](#using-associated-content) als Quelle für Zwischeninhalte verwenden.

>[!CAUTION]
>
>Bei Zwischeninhalten handelt es sich um Seiteninhalte. Sie werden nicht im Inhaltsfragment gespeichert.

![Komponente einfügen](/help/sites-cloud/authoring/assets/content-fragments-insert.png)

>[!NOTE]
>
>Sie können auch [Einfügen visueller Assets (Bilder) in das Fragment selbst](/help/sites-cloud/administering/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>In das Fragment selbst eingefügte visuelle Assets werden an den vorangehenden Absatz im Fragment angehängt. Deshalb können Zwischeninhalte nicht zwischen einem visuellen Asset und dem vorangehenden Absatz platziert werden. Wenn Sie diese Verbindungsebene benötigen, können Sie das Bild dem Fragment hinzufügen (als ein [Fragment mit gemischten Medien](/help/sites-cloud/administering/content-fragments/content-fragments.md#fragments-with-visual-assets)).

>[!CAUTION]
>
>Wenn Sie Zwischeninhalte zu einem Inhaltsfragment auf Ihrer Seite hinzugefügt haben, kann das Ändern der Struktur des zugrunde liegenden Inhaltsfragments (im Fragment-Editor) zu fehlerhaften/unerwarteten Ergebnissen führen.
>
>Wenn dies eintritt, wird der Zwischeninhalt unverändert beibehalten:
>
>* Übergangskomponenten haben eine absolute Position innerhalb der Komponentensequenz im Fragmentfluss. Diese Position ändert sich nicht, auch wenn sich der Inhalt der Absätze im Fragment ändert.
>
>  Dies kann den Eindruck erwecken, als hätte sich die relative Position geändert, da Zwischenabsätze keinen kontextuellen Bezug zu den Absätzen (des Fragments) haben, neben denen sie sich befinden.
>* Wenn zwischen zwei Absatzstrukturen ein Konflikt besteht, wird der Zwischeninhalt nicht angezeigt (obwohl er intern noch vorhanden ist).


### Verwenden von zugehörigen Inhalten {#using-associated-content}

Wenn Sie [verknüpften Inhalt](/help/sites-cloud/administering/content-fragments/content-fragments-assoc-content.md) für das [Inhaltsfragment](/help/sites-cloud/administering/content-fragments/content-fragments.md) haben, stehen diese Elemente im Seitenbedienfeld zur Verfügung (nachdem Sie das Fragment auf der Inhaltsseite platziert haben). Verknüpfte Inhalte sind im Grunde eine besondere Inhaltsquelle für [Zwischeninhalte](/help/sites-cloud/administering/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments).

>[!NOTE]
>
>Es gibt verschiedene Methoden zum Hinzufügen von [visuellen Assets (z. B. Bildern)](/help/sites-cloud/administering/content-fragments/content-fragments.md#fragments-with-visual-assets) zu einem Fragment und/oder zu einer Seite.

>[!NOTE]
>
>Wenn sich auf einer Seite mehrere Inhaltsfragmente befinden, wird die **Zugehörige Inhalte** -Registerkarte zeigt Assets an, die für alle Fragmente geeignet sind.

Nachdem Sie ein Fragment mit verknüpftem Inhalt zu Ihrer Seite hinzugefügt haben, wird eine neue Registerkarte (**Zugehörige Inhalte**) im Seitenbereich geöffnet.

Von hier aus können Sie die Assets an die gewünschte Position ziehen (entweder zu einer vorhandenen Komponente oder an die gewünschte Position, an der die entsprechende Komponente erstellt wird):

![Einfügen eines Bildes](/help/sites-cloud/authoring/assets/content-fragments-image.png)

### In das Fragment eingefügte Assets {#assets-inserted-into-the-fragment}

Wenn Assets (z. B. Bilder) in das Fragment selbst eingefügt wurden (als [Fragmente mit gemischten Medien](/help/sites-cloud/administering/content-fragments/content-fragments.md#fragments-with-visual-assets)), sind die Optionen zur Bearbeitung dieser Assets im Seiten-Editor eingeschränkt.

Beispielsweise haben Sie zur Bearbeitung eines Bildes folgende Möglichkeiten:

* Beschneiden, Drehen oder Spiegeln des Bildes.
* Fügen Sie einen Titel oder alternativen Text hinzu.
* Geben Sie eine Größe an.
* Sie können auch das Layout konfigurieren.

Andere Änderungen wie Verschieben, Kopieren und Löschen müssen im Fragment-Editor vorgenommen werden.

### Veröffentlichung {#publishing}

Fragmente müssen zuerst veröffentlicht werden, damit sie auf Ihren veröffentlichten Web-Seiten verwendet werden können:

* Ein Fragment kann veröffentlicht werden, nachdem [es in der Inhaltsfragmentkonsole erstellt wurde](/help/sites-cloud/administering/content-fragments/content-fragments-managing.md#publishing-and-referencing-a-fragment).
* Wenn ein *unveröffentlichtes Fragment* auf einer Seite verwendet wird, die veröffentlicht wird, kann das Fragment gleichzeitig mit der Seite veröffentlicht werden.

## Exportieren von Inhaltsfragmenten {#exporting-content-fragments}

Für den Export in Adobe Target kann JSON verwendet werden, um das Fragment bereitzustellen. Siehe:

* [Integrieren mit Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Exportieren von Inhaltsfragmenten in Adobe Target](/help/sites-cloud/integrating/content-fragments-target.md)
