---
title: Experience Fragments
description: Verwenden Sie Adobe Experience Manager als Cloud-Service-Erlebnisfragmente, um Ihre Erlebnisse wiederverwendbar und flexibel zu gestalten.
translation-type: tm+mt
source-git-commit: b7a2e86de27dbfcdecaf3a2bc1984678b7b69375

---


# Experience Fragments {#experience-fragments}

In Adobe Experience Manager als Cloud-Dienst ein Erlebnisfragment:
* ist eine Gruppe von einer oder mehreren Komponenten
* enthält sowohl Inhalt als auch Layout
* kann auf Seiten verwiesen werden
* kann beliebige Komponenten enthalten

Ein Experience Fragment:

* ist Teil eines Erlebnisses (Seite).
* kann übergreifend für mehrere Seiten verwendet werden.
* basiert auf einer (bearbeitbaren) Vorlage, die seine Struktur und Komponenten definiert.
* besteht aus einer oder mehreren Komponenten mit Layout innerhalb eines Absatzsystems.
* kann Experience Fragments enthalten.
* kann mit anderen Komponenten (einschließlich anderen Experience Fragments) zu einer vollständigen Seite (Erlebnis) kombiniert werden.
* kann verschiedene Varianten aufweisen, die Inhalte und/oder Komponenten gemeinsam nutzen.
* kann in Bausteine untergliedert werden, die sich übergreifend für mehrere Varianten des Fragments verwenden lassen.

Experience Fragments können in folgenden Fällen verwendet werden:

* Wenn ein Autor Teile (ein Fragment eines Erlebnisses) einer Seite wiederverwenden möchte.
Ohne Erlebnisfragmente müsste der Autor dieses Fragment kopieren und einfügen. Das Erstellen und Verwalten dieser zum Kopieren/Einfügen vorgesehenen Erlebnisse sind zeitaufwendige und fehleranfällige Verfahren.
Mit Experience Fragments ersparen Sie sich das Kopieren/Einfügen.
* Zur Unterstützung des nutzungsfreien CMS.
Autoren möchten AEM nur zum Authoring, nicht aber zum Senden an den Kunden verwenden. In diesem Fall würde das Erlebnis über ein System/einen Touchpoint eines Drittanbieters für den Endnutzer bereitgestellt.

>[!NOTE]
>
>Für den Schreibzugriff auf Experience Fragments muss das betreffende Benutzerkonto der folgenden Gruppe angehören:
>
>* `experience-fragments-editors`
>
>
Wenden Sie sich an Ihren Systemadministrator, falls Probleme auftreten.

## Wann ist die Verwendung von Experience Fragments sinnvoll? {#when-should-you-use-experience-fragments}

Experience Fragments sollten in folgenden Fällen verwendet werden:

* Immer wenn Sie Erlebnisse wiederverwenden möchten.
   * Erlebnisse, die in Verbindung mit demselben oder ähnlichem Inhalt wiederverwendet werden.
* Wenn Sie AEM als Inhaltsbereitstellungs-Plattform für Dritte nutzen möchten.
   * Nutzung durch beliebige Lösungen, bei denen AEM als Inhaltsbereitstellungs-Plattform fungieren soll.
   * Einbetten von Inhalten in Touchpoints von Dritten.
* Wenn ein Erlebnis verschiedene Varianten oder Ausgabeformate aufweist.
   * Kanal- oder kontextspezifische Varianten.
   * Erlebnisse, die für eine Gruppierung sinnvoll sind; zum Beispiel eine Kampagne mit unterschiedlichen Erlebnissen über verschiedene Kanäle hinweg.
* Wenn Sie Omnichannel-Commerce betreiben.
   * Skaliertes Teilen von Commerce-bezogenem Inhalt auf [Social-Media-Kanälen.](/help/implementing/developing/extending/experience-fragments.md#social-variations)
   * Ermöglichen von Transaktionen an Touchpoints.

## Organisieren von Erlebnisfragmenten {#organizing-your-experience-fragments}

Es wird empfohlen,
* Ordner zum Organisieren der Erlebnisfragmente verwenden,

* [konfigurieren Sie die zulässigen Vorlagen für diese Ordner](#configure-allowed-templates-folder).

Mit dem Erstellen von Ordnern können Sie:

* eine aussagekräftige Struktur für Ihre Erlebnisfragmente erstellen; zum Beispiel nach Klassifizierung

   >[!NOTE]
   >
   >Es ist nicht erforderlich, die Struktur Ihrer Erlebnisfragmente an der Seitenstruktur Ihrer Site auszurichten.

* [Zuweisen der zulässigen Vorlagen auf Ordnerebene](#configure-allowed-templates-folder)

   >[!NOTE]
   >
   >Verwenden Sie den [Vorlagen-Editor](/help/sites-cloud/authoring/features/templates.md), wenn Sie eine eigene Vorlage erstellen möchten.

Das WKND-Projekt strukturiert einige Erlebnisfragmente entsprechend `Contributors`. Die verwendete Struktur zeigt auch, wie andere Funktionen, wie Multi-Site-Management (einschließlich Sprachkopien), verwendet werden können.

Siehe:

`http://localhost:4502/aem/experience-fragments.html/content/experience-fragments/wknd/language-masters/en/contributors/kumar-selveraj/master`

![Ordner für Erlebnisfragmente](/help/sites-cloud/authoring/assets/xf-folders.png)

## Erstellen und Konfigurieren eines Ordners für Ihre Erlebnisfragmente {#creating-and-configuring-a-folder-for-your-experience-fragments}

Um einen Ordner für Ihre Erlebnisfragmente zu erstellen und zu konfigurieren, wird empfohlen,

1. [Erstellen von Ordnern](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#creating-a-new-folder).

1. [Konfigurieren Sie die zulässigen Erlebnisfragment-Vorlagen für diesen Ordner](#configure-allowed-templates-folder).

>[!NOTE]
>
>Es ist auch möglich, die [zulässigen Vorlagen für Ihre Instanz](#configure-allowed-templates-instance)zu konfigurieren. Diese Methode wird jedoch **nicht** empfohlen, da die Werte bei der Aktualisierung überschrieben werden können.

### Zulässige Vorlagen für Ihren Ordner konfigurieren {#configure-allowed-templates-folder}

>[!NOTE]
>
>Dies ist die empfohlene Methode zur Angabe der **zulässigen Vorlagen**, da die Werte bei der Aktualisierung nicht überschrieben werden.

1. Navigieren Sie zum gewünschten Ordner **Experience Fragments**.

1. Wählen Sie den Ordner und dann **Eigenschaften** aus.

1. Geben Sie den regulären Ausdruck zum Abrufen der erforderlichen Vorlagen im Feld **Zulässige Vorlagen** an.

   Beispiel:
   `/conf/(.*)/settings/wcm/templates/experience-fragment(.*)?`

   Siehe:
   `http://localhost:4502/mnt/overlay/cq/experience-fragments/content/experience-fragments/folderproperties.html/content/experience-fragments/wknd`

   ![Erlebnisfragment-Eigenschaften - Zulässige Vorlagen](/help/sites-cloud/authoring/assets/xf-folders-templates.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Vorlagen für Experience Fragments](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments).

1. Select **Save and Close**.

### Zulässige Vorlagen für Ihre Instanz konfigurieren {#configure-allowed-templates-instance}

>[!CAUTION]
>
>Es wird nicht empfohlen, die **zulässigen Vorlagen** mit dieser Methode zu ändern, da die angegebenen Vorlagen bei der Aktualisierung überschrieben werden können.
>
>Bitte benutzen Sie diesen Dialog nur zu Informationszwecken.

1. Navigate to the required **Experience Fragments** console.

1. Wählen Sie **Konfigurationsoptionen**:

   ![Konfigurationsschaltfläche](/help/sites-cloud/authoring/assets/xf-18.png)

1. Geben Sie im Dialogfeld **Experience Fragments konfigurieren** die erforderlichen Vorlagen an: 

   ![Experience Fragments konfigurieren](/help/sites-cloud/authoring/assets/xf-19.png)

   >[!NOTE]
   >
   >Weitere Informationen finden Sie unter [Vorlagen für Experience Fragments](/help/implementing/developing/extending/experience-fragments.md#templates-for-experience-fragments).

1. Wählen Sie **Speichern**.


## Erstellen eines Experience Fragments {#creating-an-experience-fragment}

Gehen Sie für die Erstellung eines Experience Fragment folgendermaßen vor:

1. Select **Experience Fragments** from the Global Navigation.

   ![Erlebnisfragmente im Navigationsbereich](/help/sites-cloud/authoring/assets/xf-01.png)

1. Navigieren Sie zum gewünschten Ordner und wählen Sie **Erstellen**:

   ![Erstellen eines Ordners für Erlebnisfragmente](/help/sites-cloud/authoring/assets/xf-02.png)

1. Wählen Sie **Erlebnisfragment** , um den Assistenten zum **Erstellen von Erlebnisfragmenten** zu öffnen.

   Wählen Sie die gewünschte Vorlage **** und klicken Sie auf **Weiter**:

   ![Auswählen einer Erlebnisfragment-Vorlage](/help/sites-cloud/authoring/assets/xf-03.png)


1. Geben Sie die **Eigenschaften** für das **Experience Fragment** ein.

   Sie müssen einen **Titel** angeben. Wenn Sie das Feld **Name** leer lassen, wird der Name vom **Titel** abgeleitet.

   ![Erlebnisfragment-Eigenschaften](/help/sites-cloud/authoring/assets/xf-04.png)

1. Klicken Sie auf **Erstellen**.

   Daraufhin wird eine Meldung angezeigt. Wählen Sie nun eine der folgenden Optionen aus:

   * **Fertig**, um zur Konsole zurückzukehren
   * **Öffnen**, um den Editor für Fragmente zu öffnen

## Bearbeiten eines Experience Fragment {#editing-your-experience-fragment}

Der Experience Fragment Editor bietet Ihnen ähnliche Funktionen wie der normale Seiteneditor.

>[!NOTE]
>
>Weiterführende Informationen zu dessen Verwendung finden Sie unter [Bearbeiten des Seiteninhalts](/help/sites-cloud/authoring/fundamentals/editing-content.md).

Die folgende Beispielvorgehensweise veranschaulicht, wie Sie Teaser für Produkte erstellen:

1. Ziehen Sie die gewünschte Komponente per Drag &amp; Drop aus dem [Komponentenbrowser](/help/sites-cloud/authoring/fundamentals/environment-tools.md#components-browser).

1. Abhängig von der Komponente:
   * Fügen Sie nach Bedarf Inhalte und/oder Assets hinzu.
   * Konfigurieren Sie die Eigenschaften nach Bedarf.

1. Fügen Sie bei Bedarf weitere Komponenten hinzu.

Beispiel: `http://<host>:<port>/editor.html/content/experience-fragments/wknd/language-masters/en/contributors/stacey-roswells/master.html`

![Erlebnisfragment auf Seite](/help/sites-cloud/authoring/assets/xf-05.png)

## Erstellen einer Experience-Fragment-Variante {#creating-an-experience-fragment-variation}

Je nach Ihren Anforderungen können Sie Varianten eines Experience Fragment erstellen:

1. Öffnen Sie ein Fragment zur [Bearbeitung](#editing-your-experience-fragment).
1. Öffnen Sie die Registerkarte **Varianten**.

   ![Erstellen einer Erlebnisfragment-Variante](/help/sites-cloud/authoring/assets/xf-06.png)

1. Die Option **Erstellen** ermöglicht es Ihnen, Folgendes zu erstellen:

   * **Variante**
   * **Variante als Live Copy**

1. Definieren Sie die gewünschten Eigenschaften:

   * **Vorlage**
   * **Titel**
   * **Name** - Wenn das Feld leer gelassen wird, wird es aus dem Titel abgeleitet
   * **Beschreibung**
   * **Varianten-Tags**
   Beispiel:

   ![Variationseigenschaften](/help/sites-cloud/authoring/assets/xf-07.png)

1. Confirm with **Done**, the new variation will be shown in the panel.

## Verwenden eines Experience Fragment {#using-your-experience-fragment}

Jetzt können Sie das Experience Fragment auf Ihren Seiten verwenden:

1. Öffnen Sie eine beliebige Seite, um sie zu bearbeiten.

1. Erstellen Sie eine Instanz der Komponente Erlebnisfragment innerhalb des Seitenabsatzsystems:

1. Fügen Sie das eigentliche Experience Fragment zur Komponenteninstanz hinzu, indem Sie einen der folgenden Schritte ausführen:

   * Ziehen Sie das gewünschte Fragment aus dem Assets-Browser und legen Sie es auf die Komponente.
   * Select **Configure** from the component toolbar and specify the fragment to use, confirm with **Done**.
   >[!NOTE]
   >
   >In der Komponenten-Symbolleiste dient die Option „Bearbeiten“ als Kurzbefehl zum Öffnen eines Fragments im Editor für Fragmente.

Beispiel: `http://<host>:<port>/editor.html/content/wknd/language-masters/en/about-us.html`

![Erlebnisfragment im Seiten-Editor](/help/sites-cloud/authoring/assets/xf-08.png)

## Bausteine {#building-blocks}

Sie können eine oder mehrere Komponenten auswählen, um einen Baustein zur Wiederverwendung in Ihrem Fragment zu erstellen:

### Erstellen eines Bausteins {#creating-a-building-block}

So erstellen Sie einen neuen Baustein:

1. Wählen Sie im Editor für Experience Fragments die Komponenten, die wiederverwendet werden sollen:

   ![Komponente für Baustein auswählen](/help/sites-cloud/authoring/assets/xf-09.png)

1. Wählen Sie in der Komponenten-Symbolleiste die Option **In Baustein umwandeln**:

   ![Schaltfläche &quot;Baustein&quot;](/help/sites-cloud/authoring/assets/xf-10.png)

1. Geben Sie den Namen des Bausteins **** ein und bestätigen Sie ihn mit der Option **Konvertieren**:

   ![Baustein &quot;Name&quot;](/help/sites-cloud/authoring/assets/xf-11.png)

1. Der **Baustein** wird auf der linken Registerkarte (**Lokal**) angezeigt und kann für weitere Aktionen ausgewählt werden:

   ![Baustein in der Leiste](/help/sites-cloud/authoring/assets/xf-12.png)

#### Verwalten eines Bausteins {#managing-a-building-block}

Der Baustein wird auf der Registerkarte **Bausteine** angezeigt. Für jeden Baustein sind die folgenden Aktionen verfügbar:

* **** Zum Master wechseln: zum Öffnen der Mastervariante in einer neuen Registerkarte
* **Umbenennen**
* **Löschen**

![Verwalten von Bausteinen](/help/sites-cloud/authoring/assets/xf-13.png)

#### Verwenden eines Bausteins {#using-a-building-block}

Sie können den Baustein wie bei jeder anderen Komponente auch in das Absatzsystem eines beliebigen Fragments ziehen.

Beim Bearbeiten eines Erlebnisfragments werden verfügbare Bausteine auf der Registerkarte links angezeigt. Sie können nach folgenden Kriterien filtern:

* **Lokal** - Erstellen von Blöcken aus dem aktuellen Erlebnisfragment
* **Alle** - Blöcke aus allen Fragmenten erstellen

![Auswählen von Bausteinen](/help/sites-cloud/authoring/assets/xf-14.png)

## Details Ihres Experience Fragments {#details-of-your-experience-fragment}

Details zu Ihrem Fragment können wie folgt angezeigt werden:

1. Navigieren Sie zum Speicherort Ihrer Erlebnisfragmente (navigieren Sie nicht weiter nach unten zu den Varianten im Fragment).
Details are shown in all views of the **Experience Fragments** console, with the **List View** including details of an export to Target: <!--Details are shown in all views of the **Experience Fragments** console, with the **List View** including details of an [export to Target](/help/sites-administering/experience-fragments-target.md):-->

   ![Details zum Erlebnisfragment](/help/sites-cloud/authoring/assets/xf-15.png)

1. Beim Öffnen der **Eigenschaften** des Experience Fragments gilt Folgendes:

   ![Schaltfläche &quot;Eigenschaften&quot;](/help/sites-cloud/authoring/assets/xf-16.png)

   Die Eigenschaften werden auf verschiedenen Registerkarten angezeigt:

   >[!CAUTION]
   >
   >Diese Registerkarten werden angezeigt, wenn Sie **Eigenschaften** aus der Konsole &quot;Erlebnisfragmente&quot;öffnen.
   >
   >Wenn Sie beim Bearbeiten eines Erlebnisfragments Eigenschaften **öffnen** , werden die entsprechenden [Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md) angezeigt.

   ![Erlebnisfragment-Eigenschaften](/help/sites-cloud/authoring/assets/xf-17.png)

   * **Einfach**
      * **Titel** - erforderlich
      * **Beschreibung**
      * **Tags**
      * **Gesamtanzahl der Varianten** - nur zur Information
      * **Anzahl der Webvarianten** – nur zur Information
      * **Anzahl der Nicht-Webvarianten** - nur Informationen
      * **Anzahl der Seiten, auf denen dieses Fragment verwendet wird** – nur zur Information
   * **Cloud-Services**
      * **Cloud-Konfiguration**
      * **Cloud-Service-Konfigurationen**
      * **Facebook-Seiten-ID**
      * **Pinterest-Pinnwand**
   * **Verweise**
      * Eine Liste mit Verweisen
   * **Status in sozialen Netzwerken**
      * Details zu Social-Media-Varianten

## Die Plain-HTML-Wiedergabe {#the-plain-html-rendition}

Using the `.plain.` selector in the URL, you can access the plain HTML rendition from the browser.

>[!NOTE]
>
>Diese ist zwar direkt über den Browser verfügbar, [aber ihr Hauptzweck ist es, anderen Applikationen (beispielsweise Web-Applikationen von Drittanbietern oder benutzerdefinierten mobilen Implementierungen) den direkten Zugriff auf den Inhalt des Experience Fragment zu ermöglichen, und zwar allein über die URL](/help/implementing/developing/extending/experience-fragments.md#the-plain-html-rendition).

## Exportieren von Experience Fragments {#exporting-experience-fragments}

Standardmäßig werden Experience Fragments im HTML-Format bereitgestellt. Dies kann von AEM und Drittkanalanbietern gleichermaßen verwendet werden.

Für den Export nach Adobe Target kann JSON ebenfalls verwendet werden. Vollständige Informationen finden Sie unter Target-Integration mit Experience Fragments. <!--For export to Adobe Target, JSON can also be used. See [Target Integration with Experience Fragments](/help/sites-administering/experience-fragments-target.md) for full information.-->
