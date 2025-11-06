---
title: Experience Fragments
description: Verwenden Sie Experience Fragments in Adobe Experience Manager as a Cloud Service, um Ihre Erlebnisse wiederverwendbar und flexibel zu gestalten.
exl-id: 9dc33677-141f-47e5-a01e-6c7488686314
solution: Experience Manager Sites
feature: Authoring, Experience Fragments
role: User
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '2142'
ht-degree: 100%

---

# Experience Fragments {#experience-fragments}

Ein Experience Fragment in Adobe Experience Manager as a Cloud Service:

* ist eine Gruppe von einer oder mehreren Komponenten
* enthält sowohl Inhalt als auch Layout
* kann auf Seiten referenziert werden
* kann jede beliebige Komponente enthalten.

Ein Experience Fragment:

* ist Teil eines Erlebnisses (Seite).
* kann auf mehreren Seiten verwendet werden (basierend auf bearbeitbaren Vorlagen).
* basiert auf einer (bearbeitbaren) Vorlage, die seine Struktur und Komponenten definiert.
* Diese Vorlage wird verwendet, um die *Stammseite* des Experience Fragments zu erstellen.
* besteht aus einer oder mehreren Komponenten mit Layout in einem Absatzsystem.
* kann andere Experience Fragments enthalten.
* kann mit anderen Komponenten (einschließlich anderen Experience Fragments) kombiniert werden, um eine vollständige Seite (Erlebnis) zu bilden.
* Je nach Stammseite können eine oder mehrere Varianten erstellt werden.
* Diese Varianten können Inhalte und/oder Komponenten gemeinsam nutzen.
* kann in Bausteine untergliedert werden, die sich übergreifend für mehrere Varianten des Fragments verwenden lassen.

Experience Fragments können in folgenden Fällen verwendet werden:

* Wenn ein Autor Teile einer Seite (die sogenannten Fragmente eines Erlebnisses) wiederverwenden möchte.
Ohne Experience Fragments müsste der Autor dieses Fragment kopieren und einfügen. Das Erstellen und Verwalten dieser zum Kopieren/Einfügen vorgesehenen Erlebnisse sind zeitaufwendige und fehleranfällige Verfahren.
Mit Experience Fragments ersparen Sie sich das Kopieren/Einfügen.
* Zur Unterstützung des Nutzungsszenarios mit Headless-Content-Management-Systemen.
Autoren sollten AEM nur zum Erstellen von Inhalten nutzen, jedoch nicht für deren Bereitstellung für Kunden. In diesem Fall würde das Erlebnis über ein System/einen Touchpoint eines Drittanbieters aufgenommen und dann an die Benutzerin bzw. den Benutzer weitergeben werden.
* Mit [Multi-Site-Management (MSM)](/help/sites-cloud/administering/msm/overview.md); denn ein Experience Fragment ist Teil einer Seite. Dies gilt sowohl für die einzelnen Fragmente als auch für die Ordner, in denen sie sich befinden.

>[!NOTE]
>
>**[Inhaltsfragmente](/help/sites-cloud/authoring/fragments/content-fragments.md)** und **Experience Fragments** sind unterschiedliche Funktionen in AEM:
>
>* **Inhaltsfragmente** sind redaktionelle Inhalte mit Definition und Struktur, aber ohne zusätzliches visuelles Design und/oder Layout. Sie können unter anderem für den Zugriff auf strukturierte Daten wie Texte, Zahlen und Daten verwendet werden.
>* **Experience Fragments** sind vollständig gestaltete Inhalte und stellen Teile von Web-Seiten dar.
>
>Experience Fragments können Inhalte in Form von Inhaltsfragmenten enthalten, aber nicht umgekehrt.
>
>Weitere Details finden Sie in den [Informationen zu Inhaltsfragmenten und Experience Fragments in AEM](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/content-fragments/understand-content-fragments-and-experience-fragments.html?lang=de#content-fragments).

>[!NOTE]
>
>Damit für Experience Fragments Schreibzugriff besteht, muss das betreffende Benutzerkonto in der folgenden Gruppe registriert sein:
>
>* `experience-fragments-editors`
>
>Falls Probleme auftreten, wenden Sie sich an Ihre Systemadmins.

## Wann ist die Verwendung von Experience Fragments sinnvoll? {#when-should-you-use-experience-fragments}

Experience Fragments sollten in folgenden Fällen verwendet werden:

* Wann immer Sie Erlebnisse wiederverwenden möchten.
   * Bei Erlebnissen, die mit demselben oder ähnlichen Inhalten wiederverwendet werden.
* Wenn Sie AEM als Plattform zur Inhaltsbereitstellung für Dritte nutzen möchten.
   * Zur Nutzung durch beliebige Lösungen, bei denen AEM als Plattform zur Inhaltsbereitstellung fungieren soll.
   * Beim Einbetten von Inhalten in Touchpoints von Drittanbietern.
* Wenn Sie über ein Erlebnis mit unterschiedlichen Varianten oder Ausgabedarstellungen verfügen.
   * Kanal- oder kontextspezifische Varianten.
   * Erlebnisse, die für Gruppen sinnvoll sind, z. B. eine Kampagne mit unterschiedlichen Erlebnissen über verschiedene Kanäle.
* Wenn Sie Omni-Channel-Commerce betreiben.
   * Ermöglichen von Transaktionen an Touchpoints.

## Organisieren von Experience Fragments {#organizing-your-experience-fragments}

Folgendes wird empfohlen:

* verwenden von Ordnern zum Organisieren der Experience Fragments,
* [Konfigurieren der zulässigen Vorlagen für diese Ordner](#configure-allowed-templates-folder).

Beim Erstellen von Ordnern können Sie:

* eine aussagekräftige Struktur für Ihre Experience Fragments erstellen; zum Beispiel nach Klassifizierung

  >[!NOTE]
  >
  >Es ist nicht erforderlich, die Struktur Ihrer Experience Fragments an der Seitenstruktur Ihrer Site auszurichten.

* [Zuweisen der zulässigen Vorlagen auf Ordnerebene](#configure-allowed-templates-folder)

  >[!NOTE]
  >
  >Verwenden Sie den [Vorlagen-Editor](/help/sites-cloud/authoring/page-editor/templates.md), wenn Sie eine eigene Vorlage erstellen möchten.

Das WKND-Projekt strukturiert einige Experience Fragments nach `Contributors`. Die verwendete Struktur zeigt auch, wie andere Funktionen, wie Multi-Site-Management (einschließlich Sprachkopien), verwendet werden können.

Siehe:

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![Ordner für Experience Fragments](/help/sites-cloud/authoring/assets/xf-folders.png)

## Erstellen und Konfigurieren eines Ordners für Ihre Experience Fragments {#creating-and-configuring-a-folder-for-your-experience-fragments}

Um einen Ordner für Ihre Experience Fragments zu erstellen und zu konfigurieren, wird Folgendes empfohlen:

1. [Erstellen eines Ordners](/help/sites-cloud/authoring/sites-console/managing-pages.md#creating-a-new-folder).

1. [Konfigurieren der zulässigen Experience Fragment-Vorlagen für diesen Ordner](#configure-allowed-templates-folder).

>[!NOTE]
>
>Es ist auch möglich, die [zulässigen Vorlagen für Ihre Instanz](#configure-allowed-templates-instance) zu konfigurieren. Diese Methode wird jedoch **nicht** empfohlen, da die Werte bei der Aktualisierung überschrieben werden können.

### Konfigurieren zulässiger Vorlagen für Ihren Ordner {#configure-allowed-templates-folder}

>[!NOTE]
>
>Dies ist die empfohlene Methode zur Angabe der **zulässigen Vorlagen**, da die Werte bei der Aktualisierung nicht überschrieben werden.

1. Navigieren Sie zum gewünschten Ordner mit **Experience Fragments**.

1. Wählen Sie den Ordner und dann **Eigenschaften** aus.

1. Geben Sie den regulären Ausdruck zum Abrufen der erforderlichen Vorlagen im Feld **Zulässige Vorlagen** an.

   Zum Beispiel:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   Siehe:
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![Experience Fragment-Eigenschaften – Zulässige Vorlagen](/help/sites-cloud/authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Vorlagen für Experience Fragments](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments).

1. Klicken Sie auf **Speichern und schließen**.

### Konfigurieren zulässiger Vorlagen für Ihre Instanz {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Es wird nicht empfohlen, die **zulässigen Vorlagen** mit dieser Methode zu ändern, da die angegebenen Vorlagen bei einer Aktualisierung überschrieben werden können.
>
>Verwenden Sie dieses Dialogfeld nur zu Informationszwecken.

1. Navigieren Sie zur gewünschten Konsole **Experience Fragments**.

1. Wählen Sie **Konfigurationsoptionen** aus:

   ![Schaltfläche „Konfiguration“](/help/sites-cloud/authoring/assets/xf-18.png)

1. Geben Sie im Dialogfeld **Experience Fragments konfigurieren** die erforderlichen Vorlagen an:

   ![Experience Fragments konfigurieren](/help/sites-cloud/authoring/assets/xf-19.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Vorlagen für Experience Fragments](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments).

1. Klicken Sie auf **Speichern**.

## Erstellen eines Experience Fragment {#creating-an-experience-fragment}

Gehen Sie zum Erstellen eines Experience Fragment folgendermaßen vor:

1. Wählen Sie in der globalen Navigation die Option **Experience Fragments** aus.

   ![Experience Fragments im Navigationsbereich](/help/sites-cloud/authoring/assets/xf-01.png)

1. Navigieren Sie zum gewünschten Ordner und wählen Sie **Erstellen** aus:

   ![Erstellen eines Ordners für Experience Fragments](/help/sites-cloud/authoring/assets/xf-02.png)

1. Wählen Sie **Experience Fragment** aus, um den Assistenten zum **Erstellen von Experience Fragments** zu öffnen.

   Wählen Sie die gewünschte **Vorlage** aus und klicken Sie auf **Weiter**:

   ![Auswählen einer Experience Fragment-Vorlage](/help/sites-cloud/authoring/assets/xf-03.png)


1. Geben Sie die **Eigenschaften** für das **Experience Fragment** ein.

   Ein **Titel** ist zwingend erforderlich. Wenn der **Name** leer gelassen wird, wird er aus dem **Titel** abgeleitet.

   ![Experience Fragment-Eigenschaften](/help/sites-cloud/authoring/assets/xf-04.png)

   >[!NOTE]
   >
   >Tags aus der Experience Fragment-Vorlage werden nicht mit Tags auf dieser Experience Fragment-Stammseite zusammengeführt.
   >
   >Diese sind völlig voneinander getrennt.

1. Klicken Sie auf **Erstellen**.

   Eine Meldung wird angezeigt. Klicken Sie auf:

   * **Fertig**, um zur Konsole zurückzukehren
   * **Öffnen**, um den Editor für Fragmente zu öffnen

## Bearbeiten eines Experience Fragment {#editing-your-experience-fragment}

Der Experience Fragment Editor bietet Ihnen ähnliche Funktionen wie der normale Seiten-Editor.

>[!NOTE]
>
>Weitere Informationen zur Verwendung des Seiteneditors finden Sie unter [Bearbeiten des Seiteninhalts](/help/sites-cloud/authoring/page-editor/edit-content.md).

Das folgende Beispielverfahren zeigt, wie Sie einen Teaser für ein Produkt erstellen:

1. Ziehen Sie die gewünschte Komponente per Drag-and-Drop aus dem [Komponenten-Browser](/help/sites-cloud/authoring/page-editor/editor-side-panel.md#components-browser).

1. Abhängig von der Komponente:
   * Fügen Sie bei Bedarf Inhalte und/oder Assets hinzu.
   * Konfigurieren Sie bei Bedarf die Eigenschaften.

1. Fügen Sie bei Bedarf weitere Komponenten hinzu.

Beispiel: `http://<host>:<port>/editor.html/content/experience-fragments/wknd/language-masters/en/contributors/stacey-roswells/master.html`

![Experience Fragment auf Seite](/help/sites-cloud/authoring/assets/xf-05.png)

## Erstellen einer Experience Fragment-Variante {#creating-an-experience-fragment-variation}

Je nach Ihren Anforderungen können Sie Varianten eines Experience Fragments erstellen:

1. Öffnen Sie ein Fragment zur [Bearbeitung](#editing-your-experience-fragment).
1. Öffnen Sie die Registerkarte **Varianten**.

   ![Erstellen einer Experience Fragment-Variante](/help/sites-cloud/authoring/assets/xf-06.png)

1. Mit **Erstellen** können Sie Folgendes erstellen:

   * **Variante**
   * **Variante als Live Copy**

     >[!NOTE]
     >
     >Wenn Sie eine erste Variante als Live Copy erstellen, wird der Titel durch die Verwendung der Live Copy-Quelle als primäre Variante übernommen.

1. Definieren Sie die erforderlichen Eigenschaften:

   * **Vorlage**
   * **Titel**
   * **Name** (Wenn Sie das Feld leer lassen, wird der Name vom Titel abgeleitet)
   * **Beschreibung**
   * **Varianten-Tags**

   Zum Beispiel:

   ![Varianteneigenschaften](/help/sites-cloud/authoring/assets/xf-07.png)


1. Bestätigen Sie Ihre Auswahl mit **Fertig**. Daraufhin wird die neue Variante im Bedienfeld angezeigt.

## Verwenden eines Experience Fragment {#using-your-experience-fragment}

Sie können Ihr Experience Fragment jetzt beim Erstellen Ihrer Seiten verwenden:

1. Öffnen Sie eine beliebige Seite, um sie zu bearbeiten.

   >[!NOTE]
   >
   >Die Seite muss auf einer bearbeitbaren Vorlage basieren.

1. Erstellen Sie eine Instanz der Experience Fragment-Komponente innerhalb des Seitenabsatzsystems:

1. Fügen Sie das eigentliche Experience Fragment zur Komponenteninstanz hinzu, indem Sie einen der folgenden Schritte ausführen:

   * Ziehen Sie das gewünschte Fragment vom Asset-Browser auf die Komponente.
   * Wählen Sie in der Komponenten-Symbolleiste die Option **Konfigurieren** aus und geben Sie das zu verwendende Fragment an. Bestätigen Sie Ihre Auswahl mit **Fertig**.

   >[!NOTE]
   >
   >In der Komponenten-Symbolleiste dient die Option „Bearbeiten“ als Kurzbefehl zum Öffnen eines Fragments im Editor für Fragmente.

Beispiel: `http://<host>:<port>/editor.html/content/wknd/language-masters/en/about-us.html`

![Experience Fragment im Seiten-Editor](/help/sites-cloud/authoring/assets/xf-08.png)

## Bausteine {#building-blocks}

Sie können eine oder mehrere Komponenten auswählen, um einen Baustein zur Wiederverwendung in Ihrem Fragment zu erstellen:

### Erstellen eines Bausteins {#creating-a-building-block}

So erstellen Sie einen neuen Baustein:

1. Wählen Sie im Experience Fragment-Editor die Komponenten aus, die Sie wiederverwenden möchten:

   ![Komponente für Baustein auswählen](/help/sites-cloud/authoring/assets/xf-09.png)

1. Wählen Sie in der Komponenten-Symbolleiste die Option **In Baustein umwandeln** aus:

   ![Schaltfläche „Baustein“](/help/sites-cloud/authoring/assets/xf-10.png)

1. Geben Sie den **Namen des Bausteins** ein und bestätigen Sie ihn mit der Option **Konvertieren**:

   ![Baustein „Name“](/help/sites-cloud/authoring/assets/xf-11.png)

1. Der **Baustein** wird auf der linken Registerkarte (**Lokal**) angezeigt und kann für weitere Aktionen ausgewählt werden:

   ![Baustein in der Leiste](/help/sites-cloud/authoring/assets/xf-12.png)

#### Verwalten eines Bausteins {#managing-a-building-block}

Der Baustein wird auf der Registerkarte **Bausteine** angezeigt. Für jeden Baustein sind die folgenden Aktionen verfügbar:

* **Zur Hauptvariante wechseln**: zum Öffnen der Stammseiten-Variante in einer neuen Registerkarte
* **Umbenennen**
* **Löschen**

![Verwalten von Bausteinen](/help/sites-cloud/authoring/assets/xf-13.png)

#### Verwenden eines Bausteins {#using-a-building-block}

Sie können den Baustein wie bei jeder anderen Komponente auch in das Absatzsystem eines beliebigen Fragments ziehen.

Beim Bearbeiten eines Experience Fragment werden verfügbare Bausteine auf der Registerkarte links angezeigt. Sie können nach folgenden Kriterien filtern:

* **Lokal** - Erstellen von Bausteinen aus dem aktuellen Experience Fragment
* **Alle** - Erstellen von Bausteinen aus allen Experience Fragments

![Auswählen von Bausteinen](/help/sites-cloud/authoring/assets/xf-14.png)

## Personalisierung für Ihr Experience Fragment {#personalization-experience-fragment}

Mit der Personalisierung in Ihrem Experience Fragment können Sie als Marketing-Experte Zielgruppen für das Experience Fragment einmal definieren und das Fragment dann auf jeder beliebigen Seite wiederverwenden. Dies:

* vermeidet die Notwendigkeit, bei jeder Verwendung des Fragments die erforderlichen Varianten für jede Zielgruppe anzugeben
* behält Stile für alle Angebote bei

Sie können ein Experience Fragment mit mehreren Komponenten erstellen, die innerhalb dieses Fragments gruppiert sind. Sie können auch Varianten des Fragments für jedes spezifische Zielgruppensegment erstellen und diese Experience Fragments dann über die erforderlichen Kanäle hinweg wiederverwenden.

Die Personalisierung wird durch Definition der **Personalisierungseigenschaften** für das Experience Fragment bzw. die Variante oder den Ordner, der die Fragmente enthält, erreicht. Dies bedeutet, dass die Vererbung die Personalisierungseigenschaften überschreiben kann.

Durch die Konfiguration dieser Eigenschaften wird auch der Modus **Targeting** im Experience Fragment-Editor aktiviert.

### Definieren der Personalisierung für Ihr Experience Fragment {#defining-personalization-experience-fragment}

So personalisieren Sie Ihr Fragment:

1. Navigieren Sie zum gewünschten Speicherort in der **Experience Fragments**-Konsole.

1. Wählen Sie entweder einen Ordner oder Ihr Fragment aus und klicken Sie dann in der Symbolleiste auf **Eigenschaften**.

   >[!NOTE]
   >
   >Für einen Ordner definierte Personalisierungseigenschaften werden von allen untergeordneten Ordnern über die Unterstruktur sowie die Experience Fragments (und Varianten) in dieser Unterstruktur geerbt. Sie können überschrieben werden, indem die Vererbung unterbrochen wird.

1. Öffnen Sie die Registerkarte **Personalisierung**, um Ihre Einstellungen zu definieren und zu speichern. Zum Beispiel für einen Ordner:

   ![Experience Fragment – Personalisierungseigenschaften](/help/sites-cloud/authoring/assets/xf-personalization-properties.png)

   >[!CAUTION]
   >
   >Wenn ein Fragment in eine Sites-Seite eingebettet wird und die **Personalisierung** konfiguriert wurde, wird beim Rendern der Seite nur die Personalisierungsversion der Seite verwendet.
   >
   >Damit das Targeting für die Komponenten in einem Fragment beim Rendern der Seite funktioniert, müssen die folgenden Bedingungen erfüllt sein:
   >
   >Der ausgewählte **ContextHub-Pfad** auf der Registerkarte **Personalisierung** muss wie folgt sein:
   >
   >* der gleiche Pfad wie der Pfad, der für die Seite konfiguriert wurde, auf der das Fragment gerendert wird
   >
   >  Oder:
   >
   >* ein Pfad, der eine Teilmenge der Stores enthält, die im für die Seite konfigurierten ContextHub definiert sind
   >
   >Der ausgewählte **Segmentpfad** in der Registerkarte **Personalisierung** muss entweder:
   >
   >* der gleiche Pfad sein wie der Pfad, der für die Seite konfiguriert wurde, auf der das Fragment gerendert wird
   >
   >  oder
   >
   >* ein Pfad sein, der eine Teilmenge der für die Seite konfigurierten Segmente enthält

### Definieren des Targetings für Ihr Experience Fragment {#defining-targeting-experience-fragment}

Nachdem die Personalisierungseigenschaften konfiguriert wurden, ist der Targeting-Modus verfügbar, wenn das Fragment zur Bearbeitung geöffnet wird.

![Experience Fragment Editor – Targeting-Modus](/help/sites-cloud/authoring/assets/xf-targeting-mode.png)

Dieser Modus funktioniert auf die gleiche Weise wie die Seitenbearbeitung. Siehe [Targeting-Modus für den Seiten-Editor](/help/sites-cloud/authoring/personalization/targeted-content.md) für weitere Details.

## Details Ihres Experience Fragment {#details-of-your-experience-fragment}

Details zu Ihrem Fragment können wie folgt angezeigt werden:

1. Navigieren Sie zum Speicherort Ihrer Experience Fragments (navigieren Sie nicht weiter nach unten zu den Varianten innerhalb des Fragments).
Details werden in allen Ansichten der Konsole **Experience Fragments** angezeigt. Dabei enthält die **Listenansicht** Details eines [Exports nach Target](/help/sites-cloud/integrating/integrating-adobe-target.md):

   ![Experience Fragment-Details](/help/sites-cloud/authoring/assets/xf-15.png)

1. Beim Öffnen der **Eigenschaften** des Experience Fragment gilt Folgendes:

   ![Schaltfläche „Eigenschaften“](/help/sites-cloud/authoring/assets/xf-16.png)

   Die Eigenschaften werden auf verschiedenen Registerkarten angezeigt:

   >[!CAUTION]
   >
   >Diese Registerkarten werden angezeigt, wenn Sie **Eigenschaften** in der Konsole „Experience Fragments“ öffnen.
   >
   >Wenn Sie beim Bearbeiten eines Experience Fragment **Eigenschaften** öffnen, werden die entsprechenden [Seiteneigenschaften](/help/sites-cloud/authoring/sites-console/page-properties.md) angezeigt.

   ![Experience Fragment-Eigenschaften](/help/sites-cloud/authoring/assets/xf-17.png)

   * **Allgemein**
      * **Titel** – erforderlich
      * **Beschreibung**
      * **Tags**
      * **Gesamtanzahl der Varianten** – nur zur Information
      * **Anzahl der Web-Varianten** – nur zur Information
      * **Anzahl der Nicht-Web-Varianten** – nur zur Information
      * **Anzahl der Seiten, die dieses Fragment verwenden** – nur zur Information
   * **Cloud Services**
      * **Cloud-Konfiguration**
      * **Cloud Service-Konfigurationen**
      * **Facebook-Seiten-ID**
      * **Pinterest-Pinnwand**
   * **Verweise**
      * Eine Liste mit Verweisen
   * **Personalisierung**
      * **ContextHub-Pfad**
      * **Segmentpfad**
      * **Marke**

## Einfache HTML-Ausgabedarstellung {#the-plain-html-rendition}

Mit dem `.plain.`-Selektor in der URL können Sie auf die einfache HTML-Ausgabe des Browsers zugreifen.

>[!NOTE]
>
>Diese ist zwar direkt über den Browser verfügbar, [aber ihr Hauptzweck ist es, anderen Anwendungen (beispielsweise Web-Anwendungen von Drittanbietern oder benutzerdefinierten Mobile- Implementierungen) den direkten Zugriff auf den Inhalt des Experience Fragments zu ermöglichen, und zwar allein über die URL](/help/implementing/developing/extending/experience-fragments.md#the-plain-html-rendition).

## Veröffentlichen von Experience Fragments {#publishing-experience-fragments}

Das Veröffentlichen Ihres Experience Fragments ist im Wesentlichen dasselbe wie das Szenario [Veröffentlichen einer Seite](/help/sites-cloud/authoring/sites-console/publishing-pages.md) (allerdings über die Experience Fragments-Konsole oder den Editor) 

Alternativ können Sie auch [In der Vorschau veröffentlichen](/help/sites-cloud/authoring/sites-console/previewing-content.md) (ebenfalls über die Experience Fragments-Konsole oder den Editor).

>[!CAUTION]
>
>Standardmäßig geschieht bei der Veröffentlichung des Stammordners von Experience Fragments (direkt unter `/content/experience-fragments`) Folgendes:
>
>* nur der Container-Ordner selbst wird veröffentlicht
>* keine untergeordneten Elemente werden veröffentlicht
>* die Veröffentlichung bereits veröffentlichter untergeordneter Elemente wird aufgehoben
>
>Um alle Experience Fragments im Ordner zu veröffentlichen, muss jedes separat veröffentlicht werden.

## Exportieren von Experience Fragments {#exporting-experience-fragments}

Standardmäßig werden Experience Fragments im HTML-Format bereitgestellt. Dies kann sowohl von AEM als auch von Drittanbieterkanälen verwendet werden.

Für den Export nach Adobe Target kann auch JSON verwendet werden. Siehe:

* [Integrieren mit Adobe Target](/help/sites-cloud/integrating/integrating-adobe-target.md)
* [Exportieren von Experience Fragments nach Adobe Target](/help/sites-cloud/integrating/experience-fragments-target.md)
