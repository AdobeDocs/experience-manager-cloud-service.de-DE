---
title: Verwenden zielgerichteter Inhalte in Multisites
description: Möchten Sie zielgerichtete Inhalte wie beispielsweise Aktivitäten, Erlebnisse und Angebote auf Ihren Sites verwalten, können Sie hierzu die in AEM integrierte Multisite-Unterstützung für zielgerichtete Inhalte verwenden
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
exl-id: 03d2d640-8de8-4c4c-8a1d-756bb2dc8457
solution: Experience Manager Sites
feature: Authoring, Personalization
role: User
source-git-commit: 98c0c9b6adbc3d7997bc68311575b1bb766872a6
workflow-type: tm+mt
source-wordcount: '2850'
ht-degree: 99%

---

# Verwenden zielgerichteter Inhalte in Multisites {#working-with-targeted-content-in-multisites}

Möchten Sie zielgerichtete Inhalte wie beispielsweise Aktivitäten, Erlebnisse und Angebote auf Ihren Sites verwalten, können Sie hierzu die in AEM integrierte Multisite-Unterstützung für zielgerichtete Inhalte verwenden.

>[!NOTE]
>
>Bei der Multisite-Unterstützung für zielgerichtete Inhalte handelt es sich um eine erweiterte Funktion. Damit Sie diese Funktion verwenden können, sollten Sie sich mit [Site-Manager](/help/sites-cloud/administering/msm/overview.md) und der [Adobe Target-Integration](/help/sites-cloud/integrating/integrating-adobe-target.md) in AEM vertraut machen.

Dieses Dokument beschäftigt sich mit den folgenden Themen:

* Kurzüberblick über die Multisite-Unterstützung für zielgerichtete Inhalte von AEM.
* Beschreibung möglicher Nutzungsszenarien dazu, wie Sie Sites (in einer Marke) verknüpfen können.
* Schrittweise Führung durch ein Beispiel dafür, wie Marketing-Experten diese Funktion nutzen können.
* Detaillierte Anweisungen zur Implementierung der Multisite-Unterstützung für zielgerichtete Inhalte.

Zur Festlegung der Art, auf die Ihre Sites personalisierte Inhalte freigeben, müssen Sie die folgenden Schritte ausführen:

1. [Erstellen Sie ein neues Gebiet](#creating-new-areas) oder [erstellen Sie ein Gebiet als Live Copy](#creating-new-areas). Ein Gebiet umfasst alle Aktivitäten, die für ein *Gebiet* der Seite zur Verfügung stehen; das heißt, die Stelle auf der Seite, auf die die Komponente abzielt. Beim Erstellen eines neuen Gebiets ist dieses zunächst leer, wobei Sie jedoch Inhalte Site-Struktur-übergreifend übernehmen können, wenn Sie das Gebiet als Live Copy erstellen.

1. [Verknüpfen Sie Ihre Site oder Seite](#linking-sites-to-an-area) mit einem Gebiet.

Sie können die Vererbung jederzeit aussetzen oder wiederherstellen.  Wenn Sie die Vererbung nicht aussetzen möchten, können Sie auch lokale Erlebnisse erstellen. Standardmäßig verweisen alle Seiten auf das primäre Gebiet, außer es wurde eigens ein anderes Gebiet festgelegt.

## Einführung in die Multisite-Unterstützung für zielgerichtete Inhalte {#introduction-to-multisite-support-for-targeted-content}

Die Multisite-Unterstützung für zielgerichtete Inhalte ist als einsatzbereite Standardfunktion erhältlich und ermöglicht das Pushen von zielgerichteten Inhalten von der mit MSM verwalteten primären Seite an eine lokale Live Copy sowie die lokale und globale Bearbeitung solcher Inhalte.

Diese Funktion wird in einem **Gebiet** verwaltet. Bereiche trennen zielgerichteten Content (Aktivitäten, Erlebnisse und Angebote), der auf verschiedenen Sites eingesetzt wird, und ermöglichen durch einen MSM-basierten Mechanismus das Erstellen und Verwalten der Vererbung zielgerichteter Inhalte sowie der Site-Vererbung. Dadurch wird verhindert, dass Sie zielgerichteten Content in vererbten Sites neu erstellen müssen.

Innerhalb eines Gebiets können nur Aktivitäten, die mit diesem Gebiet verknüpft sind, an Live Copies gepusht werden. Standardmäßig ist das primäre Gebiet ausgewählt. Nach der Erstellung weiterer Gebiete können Sie diese mit Ihren Sites oder Seiten verknüpfen, um anzugeben, welche zielgerichteten Inhalte gepusht werden.

Eine Site oder Live Copy verweist auf ein Gebiet, das die Aktivitäten enthält, die auf dieser Site oder Live Copy zur Verfügung gestellt werden müssen. Standardmäßig ist die Site oder Live Copy mit dem primären Gebiet verknüpft, es können jedoch auch andere Gebiete zugewiesen werden.

>[!NOTE]
>
>Beachten Sie Folgendes bei der Verwendung der Multisite-Unterstützung für zielgerichtete Inhalte:
>
>* Wenn Sie Rollouts oder Live Copies verwenden, ist eine MSM-Lizenz erforderlich.
>* Wenn Sie die Synchronisierung mit Adobe Target verwenden, ist eine Adobe Target-Lizenz erforderlich.
>

## Anwendungsfälle {#use-cases}

Für zielgerichtete Inhalte können Sie je nach Anwendungsfall auf verschiedene Weisen die Multi-Site-Unterstützung einrichten. In diesem Abschnitt wird beschrieben, wie diese Einrichtung theoretisch für eine Marke funktioniert. Zudem finden Sie in unserem [Beispiel: Inhalts-Targeting basierend auf geografischen Angaben](#example-targeting-content-based-on-geography) eine Darstellung zur praktischen Anwendung von Inhalts-Targeting auf mehreren Sites.

Zielgerichtete Inhalte werden in sogenannte Gebiete eingeschlossen, die den Umfang für Sites oder Seiten definieren. Diese Gebiete werden auf Markenebene definiert. Eine Marke kann mehrere Gebiete enthalten. Gebiete können sich von Marke zu Marke unterscheiden. So kann beispielsweise eine Marke nur das primäre Gebiet enthalten, das für alle Marken gilt, während eine andere Marke hingegen zeitgleich mehrere Gebiete enthält (beispielsweise mit Unterschieden je nach Region). Marken müssen somit nicht zwingend die gleichen Gebiete aufweisen.

Mit der Multisite-Unterstützung für zielgerichtete Inhalte können Sie beispielsweise über zwei (oder mehr) Sites mit **einer** Marke verfügen, die eines der folgenden Merkmale aufweisen:

* Vollständig *unterschiedliche* zielgerichtete Inhalte: Die Bearbeitung der Inhalte auf einer Site beeinflusst die Inhalte der anderen Site nicht. Sites, die mit verschiedenen Gebieten verknüpft sind, führen Lese- und Schreibaufgaben für getrennt konfigurierte Gebiete aus. Beispiel:
   * Site A verknüpft mit Bereich X
   * Site B verknüpft mit Bereich Y
* Ein *freigegebener* Satz von zielgerichteten Inhalten; die Bearbeitung in einer Site wirkt sich direkt auf beide Sites aus. Sie können dies einrichten, indem Sie beide Sites auf dasselbe Gebiet verweisen. Sites, die sich auf dasselbe Gebiet beziehen, teilen die zielgerichteten Inhalte dieses Gebiets. Beispiel:
   * Site A verknüpft mit Bereich X
   * Site B verknüpft mit Bereich X
* Bestimmte zielgerichtete Inhalte werden über MSM von einer anderen Site *übernommen*: Die Inhalte können unidirektional von der Quelle an die Live Copy übermittelt werden. Beispiel:
   * Site A verknüpft mit Bereich X
   * Site B verknüpft mit Bereich Y (eine Live Copy von Bereich X)

Sie können auch **mehrere** Marken auf einer Site einsetzen, dieses Verfahren ist jedoch komplexer als die hier dargestellten Sachverhalte.

![Multisite-Beispiel](/help/sites-cloud/authoring/assets/multisite-example.png)

>[!NOTE]
>
>Technischere Ausführungen zu dieser Funktion finden Sie unter [Strukturierung des Multisite-Managements für zielgerichtete Inhalte](/help/sites-cloud/authoring/personalization/multisite-structure.md).

## Beispiel: Inhalts-Targeting basierend auf geografischen Angaben {#example-targeting-content-based-on-geography}

Durch die Verwendung von Multisite für zielgerichtete Inhalte können Sie Personalisierungsinhalte freigeben, einführen oder isolieren. Um besser zu veranschaulichen, wie diese Funktion verwendet wird, sollten Sie ein Szenario festlegen, das regelt, wie zielgerichtete Inhalte anhand geografischer Daten bereitgestellt werden:

Es gibt vier Geografie-basierte Versionen derselben Site:

* Die Site für die **Vereinigten Staaten** befindet sich oben links und dient als primäre Site. In diesem Beispiel ist sie im Targeting-Modus geöffnet.
* Die drei übrigen Versionen sind diejenigen für **Kanada**, **Großbritannien** und **Australien**, wobei es sich bei diesen um Live Copies handelt. Diese Sites sind im Vorschaumodus geöffnet.

![Multisite-Versionen](/help/sites-cloud/authoring/assets/multisite-versions.png)

Alle Sites haben die personalisierten Inhalte der geografischen Regionen gemeinsam:

* Für Kanada wird das gleiche primäre Gebiet wie für die Vereinigten Staaten verwendet.
* Die Site für Großbritannien wurde mit Europa verknüpft und übernimmt die Inhalte des europäischen primären Gebiets.
* Australien verfügt über eigene personalisierte Inhalte, da es sich auf der Südhalbkugel befindet und saisonal bedingte Produkte nicht mit Produkten für die anderen Länder übereinstimmen.

![Multisite-Diagramm](/help/sites-cloud/authoring/assets/multisite-diagram.png)

Für die Nordhalbkugel wurde eine Winteraktivität erstellt, doch der nordamerikanische Marketing-Experte wünscht sich für den Winter ein anderes Bild, das also für die US-Site geändert wird.

![US-Version](/help/sites-cloud/authoring/assets/multisite-us.png)

Nach Aktualisierung der Registerkarte ändert sich die kanadische Site in das neue Bild, ohne dass wir etwas unternehmen müssen. Diese Änderung geschieht, da die Site von Kanada sich auf das gleiche primäre Gebiet wie die Site der Vereinigten Staaten bezieht. Die Bilder auf den Sites für Großbritannien und Australien ändern sich hingegen nicht.

![Ändern von Versionen](/help/sites-cloud/authoring/assets/multisite-us-change.png)

Die Marketing-Fachkraft möchte diese Änderungen auf das europäische Gebiet übertragen und [aktiviert die Live Copy](/help/sites-cloud/administering/msm/creating-live-copies.md), indem sie auf **Seiten-Rollout** tippt oder klickt. Nach Aktualisierung der Registerkarte erscheint auf der Site für Großbritannien das neue Bild, da das europäische Gebiet dieses (nach dem Rollout) vom primären Gebiet bezieht.

![Rollout einer Live Copy](/help/sites-cloud/authoring/assets/multisite-roll-out.png)

Das Bild auf der australischen Site bleibt unverändert, was das gewünschte Verhalten ist, da es in Australien Sommer ist und die Marketing-Fachkraft diesen Inhalt nicht ändern möchte. Die australische Site ändert sich nicht, da sie weder ein Gebiet mit einer anderen Region teilt noch eine Live Copy einer anderen Region ist. Die Marketing-Fachkraft muss sich nie Sorgen machen, dass die zielgerichteten Inhalte der australischen Site überschrieben werden.

Zudem kann für die Site für Großbritannien, deren Gebiet eine Live Copy des primären Gebiets darstellt, der Vererbungsstatus anhand des grünen Indikators neben dem Aktivitätennamen erkannt werden. Vererbte Aktivitäten können Sie nur ändern, wenn Sie die Live Copy aussetzen oder trennen.

Sie können die Vererbung jederzeit aussetzen oder vollständig trennen. Sie können auch immer lokale Erlebnisse hinzufügen, die nur für dieses Erlebnis verfügbar sind, ohne die Vererbung auszusetzen.

>[!NOTE]
>
>Technischere Ausführungen zu dieser Funktion finden Sie unter [Strukturierung des Multisite-Managements für zielgerichtete Inhalte](/help/sites-cloud/authoring/personalization/multisite-structure.md).

### Erstellen eines neuen Gebiets bzw. eines neuen Gebiets als Live Copy {#creating-a-new-area-versus-creating-a-new-area-as-livecopy}

In AEM haben Sie die Möglichkeit, einen neuen Bereich zu erstellen oder neue Bereiche als Live Copy zu erstellen. Beim Erstellen eines neuen Bereichs werden Aktivitäten und alles, was dazu gehört, z. B. Angebote, Erlebnisse usw. gruppiert. Sie erstellen ein Gebiet, wenn Sie entweder einen völlig eigenen Satz von zielgerichteten Inhalten erstellen oder einen Satz von zielgerichteten Inhalten freigeben möchten.

Wenn Sie jedoch bereits über MSM eine Vererbung zwischen den beiden Sites eingerichtet haben, möchten Sie vielleicht die Aktivitäten übernehmen. In diesem Fall sollten Sie ein Gebiet als Live Copy erstellen, bei der Y eine Live Copy von X ist und somit auch alle Aktivitäten übernimmt.

>[!NOTE]
>
>Handelt es sich bei einer Seite um eine Live Copy, verknüpft mit einem Gebiet, das selbst wiederum eine mit dem Gebiet der Seitenvorlage verknüpfte Live Copy ist, werden durch den Standard-Rollout alle folgenden Rollouts der zielgerichteten Inhalte ausgelöst.

In der folgenden Darstellung finden Sie beispielsweise vier Sites, von denen sich zwei ein primäres Gebiet (sowie alle Aktivitäten dieses Gebiets) teilen, eine weitere Site über ein Gebiet verfügt, das eine Live Copy des primären Gebiets ist, sodass die Aktivitäten bei einem Rollout geteilt werden, und die letzte Site völlig eigenständig ist (und somit ein eigenes Aktivitätsgebiet benötigt).

![Diagrammdetail](/help/sites-cloud/authoring/assets/multisite-diagram-detail.png)

Um dies in AEM umzusetzen, gehen Sie folgendermaßen vor:

* Site A ist mit dem primären Gebiet verknüpft – es muss kein eigenes Gebiet erstellt werden. Das primäre Gebiet ist in AEM standardmäßig ausgewählt. Sites A und B nutzen Aktivitäten gemeinsam usw.
* Site B ist mit dem primären Gebiet verknüpft – es muss kein eigenes Gebiet erstellt werden. Das primäre Gebiet ist in AEM standardmäßig ausgewählt. Sites A und B nutzen Aktivitäten gemeinsam usw.
* Site C ist mit dem vererbten Gebiet verknüpft, das wiederum eine Live Copy des primären Gebiets ist – erstellen Sie ein neues Gebiet als Live Copy, wenn eine Live Copy erstellt werden soll, die auf dem primären Gebiet beruht. Im Rahmen des Rollouts übernimmt das erbende Gebiet Aktivitäten aus dem primären Gebiet.
* Site D wird mit ihrem eigenen isolierten Gebiet verknüpft. So erstellen Sie ein völlig neues Gebiet, für das noch keine Aktivitäten definiert wurden. Dieses isolierte Gebiet übernimmt keine Aktivitäten der anderen Sites.

## Erstellen neuer Gebiete {#creating-new-areas}

Gebiete können aktivitäten- und angebotsübergreifend gelten. Nach der Erstellung eines Gebiets in einer der Kategorien (beispielsweise in den Aktivitäten) kann dieses Gebiet auch in der anderen (beispielsweise in den Angeboten) verfügbar gemacht werden.

>[!NOTE]
>
>Das Standardgebiet wird als Primärgebiet bezeichnet und bleibt standardmäßig ausgeblendet, wenn Sie den Namen einer Marke auswählen, **bis** Sie ein weiteres Gebiet erstellen. Wenn Sie dann entweder in der **Aktivitäts-** oder der **Angebotskonsole** eine Marke auswählen, wird Ihnen die **Gebietskonsole** angezeigt.

So erstellen Sie ein Gebiet:

1. Navigieren Sie zu **Personalisierung** > **Aktivitäten** oder **Angebote** und dann zu Ihrer Marke.
1. Wählen Sie **Gebiet erstellen** aus.

   ![Gebiet erstellen](/help/sites-cloud/authoring/assets/multisite-create-area.png)

1. Klicken Sie auf das Symbol **Gebiet** und dann auf **Weiter**.
1. Geben Sie im Feld **Titel** einen Namen für das neue Gebiet ein. Wählen Sie optional Tags aus.
1. Wählen Sie **Erstellen** aus.

   AEM leitet Sie zum Markenfenster um, in dem alle erstellten Gebiete aufgelistet werden. Sollten neben dem primären Gebiet noch andere Gebiete angezeigt werden, können Sie Gebiete direkt in der Markenkonsole erstellen.

   ![Erstellen](/help/sites-cloud/authoring/assets/multisite-create.png)

## Erstellen neuer Gebiete als Live Copys {#creating-areas-as-live-copies}

Gebiete werden als Live Copies erstellt, damit diese über Site-Strukturen hinweg zielgerichtete Inhalte übernehmen können.

So erstellen Sie ein Gebiet als Live Copy:

1. Navigieren Sie zu **Personalisierung** > **Aktivitäten** oder **Angebote** und dann zu Ihrer Marke.
1. Wählen Sie **Gebiet als Live Copy erstellen** aus.

   ![Gebiet als Live Copy erstellen](/help/sites-cloud/authoring/assets/multisite-area-as-livecopy.png)

1. Wählen Sie das Gebiet aus, von dem Sie eine Live Copy erstellen möchten, und klicken Sie auf **Weiter**.

   ![Live Copy erstellen](/help/sites-cloud/authoring/assets/multisite-livecopy.png)

1. Geben Sie im Feld **Name** einen Namen für die Live Copy ein. Standardmäßig werden Unterseiten einbezogen. schließen Sie sie aus, indem Sie das Kontrollkästchen **Unterseiten ausschließen** aktivieren.

   ![Live Copy erstellen](/help/sites-cloud/authoring/assets/multisite-create-livecopy.png)

1. Wählen Sie im Dropdown-Menü **Rollout-Konfigurationen** die entsprechende Konfiguration aus.

   Beschreibungen der verschiedenen Optionen finden Sie unter [Installierte Rollout-Konfigurationen](/help/sites-cloud/administering/msm/live-copy-sync-config.md#installed-and-custom-rollout-configurations).

   Weitere Informationen zu Live Copies finden Sie unter [Erstellen und Synchronisieren von Live Copies](/help/sites-cloud/administering/msm/creating-live-copies.md).

   >[!NOTE]
   >
   >Wird der Rollout einer Site für eine Live Copy durchgeführt und ist das für die Blueprint-Seite konfigurierte Gebiet auch Blueprint des Gebiets, das für die Live Copy der Seite konfiguriert wurde, löst die LiveAction **personalizationContentRollout** einen synchronen subRollout aus, der Teil der **Standard-Rollout-Konfigurationen** ist.

1. Wählen Sie **Erstellen** aus.

   AEM leitet Sie zum Markenfenster um, in dem alle erstellten Gebiete aufgelistet werden. Sollten neben dem primären Gebiet noch andere Gebiete angezeigt werden, können Sie Gebiete direkt im Markenfenster erstellen.

   ![Gebiet erstellen](/help/sites-cloud/authoring/assets/multisite-create-2.png)

## Verknüpfen von Sites mit Gebieten {#linking-sites-to-an-area}

Gebiete können entweder mit Seiten oder einer Site verknüpft werden. Gebiete werden von allen Unterseiten übernommen, falls diese auf der Unterseite nicht durch eine Zuordnung überschrieben werden. Im Allgemeinen erfolgen Verknüpfungen jedoch auf Site-Ebene.

Beim Verknüpfen sind nur die Aktivitäten, Erlebnisse und Angebote aus dem ausgewählten Gebiet verfügbar. Dies verhindert eine versehentliche Mischung von unabhängig verwalteten Inhalten. Wird kein weiteres Gebiet konfiguriert, gilt das primäre Gebiet der jeweiligen Marke.

>[!NOTE]
>
>Seiten oder Sites, die auf dasselbe Gebiet verweisen, verwenden *denselben* freigegebenen Satz an Aktivitäten, Erlebnissen und Angeboten. Die Bearbeitung einer Aktivität, eines Erlebnisses oder eines Angebots, die bzw. das von mehreren Sites gemeinsam genutzt werden, wirkt sich auf alle Sites aus.

Verknüpfen einer Site mit einem Gebiet:

1. Navigieren Sie zur Site (oder Seite), die Sie mit einem Gebiet verknüpfen möchten.
1. Wählen Sie die Site oder Seite und dann die Option **Eigenschaften anzeigen** aus.
1. Wählen Sie die Registerkarte **Personalisierung** aus.
1. Wählen Sie im Menü **Marke** die Marke, mit der Sie Ihr Gebiet verknüpfen möchten. Nachdem Sie die Marke ausgewählt haben, sind die verfügbaren Gebiete im Menü **Gebietsverweis** verfügbar.

   ![Verknüpfen von Sites](/help/sites-cloud/authoring/assets/multisite-english.png)

1. Wählen Sie das Gebiet im Dropdown-Menü **Gebiets-Verweis** und dann die Option **Speichern** aus.

   ![Gebiets-Verweis](/help/sites-cloud/authoring/assets/multisite-area-reference.png)

## Trennen von Live Copy oder Aussetzen der Vererbung zielgerichteter Inhalte {#detaching-live-copy-or-suspending-inheritance-of-targeted-content}

Sie können die Vererbung zielgerichteter Inhalte aussetzen oder deaktivieren. Das Aussetzen oder Trennen der Live Copy erfolgt pro Aktivität. Zum Beispiel: Sie möchten Erlebnisse in Ihrer Aktivität ändern, aber wenn diese Aktivität noch mit einer vererbten Kopie verknüpft ist, können Sie weder das Erlebnis noch eine der Eigenschaften der Aktivität ändern.

Beim Aussetzen der Live Copy wird die Vererbung vorübergehend unterbrochen, sie kann jedoch zu einem späteren Zeitpunkt wiederhergestellt werden. Beim Trennen der Live Copy wird die Vererbung dauerhaft unterbrochen.

Die Vererbung zielgerichteter Inhalte lässt sich aussetzen oder deaktivieren, indem der Inhalt in einer Aktivität wiederhergestellt wird. Sollte eine Site oder Seite sich auf ein Gebiet beziehen, das eine Live Copy ist, können Sie den Vererbungsstatus der Aktivität anzeigen.

Eine Aktivität, die Daten von einer anderen Site erbt, weist neben ihrem Namen eine grüne Markierung auf. Ausgesetzte Vererbungen werden rot gekennzeichnet, lokal erstellte Aktivitäten verfügen über keine eigene Kennzeichnung.

>[!NOTE]
>
>* Sie können Live Copies nur in einer Aktivität aussetzen oder deaktivieren.
>* Live Copies müssen nicht ausgesetzt oder getrennt werden, um eine geerbte Aktivität zu erweitern. Sie können jederzeit **neue** lokale Erlebnisse und Angebote für die Aktivität erstellen. Möchten Sie eine bestehende Aktivität bearbeiten, müssen Sie die Vererbung aussetzen.
>

### Aussetzen der Vererbung {#suspending-inheritance}

Aussetzen bzw. Trennen der Vererbung von zielgerichteten Inhalten in einer Aktivität:

1. Navigieren Sie zu der Seite, auf der Sie die Vererbung aussetzen oder trennen möchten, und wählen Sie im Modus-Dropdown-Menü die Option **Targeting** aus.
1. Ist Ihre Seite mit einem Gebiet verknüpft, das eine Live Copy darstellt, wird der Vererbungsstatus angezeigt. Wählen Sie **Targeting starten**.
1. Gehen Sie wie folgt vor, um die Vererbung einer Aktivität auszusetzen:

   1. Wählen Sie ein Element der Aktivität aus, z. B. die Zielgruppe. AEM zeigt automatisch das Bestätigungsdialogfeld „Live Copy aussetzen“ an. (Sie können die Live Copy aussetzen, indem Sie während des Targeting-Prozesses auf ein beliebiges Element tippen oder klicken.)
   1. Wählen Sie **Live Copy unterbrechen** aus dem Dropdown-Menü in der Symbolleiste.

   ![Live Copy aussetzen](/help/sites-cloud/authoring/assets/multisite-suspend-livecopy.png)

1. Wählen Sie **Aussetzen** aus, um die Aktivität auszusetzen. Ausgesetzte Aktivitäten werden rot markiert.

   ![Ausgesetzte Live Copy](/help/sites-cloud/authoring/assets/multisite-suspended.png)

### Deaktivieren der Vererbung {#breaking-inheritance}

Deaktivieren der Vererbung zielgerichteter Inhalte einer Aktivität:

1. Navigieren Sie zu der Seite, auf der die Live Copy von der Primärversion getrennt werden soll, und wählen Sie im Modus-Dropdown-Menü die Option **Targeting** aus.
1. Ist Ihre Seite mit einem Gebiet verknüpft, das eine Live Copy darstellt, wird der Vererbungsstatus angezeigt. Wählen Sie **Targeting starten**.
1. Wählen Sie aus dem Dropdown-Menü in der Symbolleiste die Option **Live Copy trennen**. AEM bestätigt, dass Sie die Live Copy trennen möchten.
1. Wählen Sie die Option **Trennen** aus, um die Live Copy von der Aktivität zu trennen. Nach dem Trennen wird das Dropdown-Menü zur Vererbung nicht mehr angezeigt. Die Aktivität ist jetzt eine lokale Aktivität.

   ![Lokale Aktivität](/help/sites-cloud/authoring/assets/multisite-winter.png)

## Wiederherstellen der Vererbung von zielgerichtetem Content {#restoring-inheritance-of-targeted-content}

Wenn Sie die Vererbung zielgerichteter Inhalte in einer Aktivität ausgesetzt haben, können Sie diese jederzeit wiederherstellen. Wenn Sie die Live Copy jedoch getrennt haben, können Sie die Vererbung nicht wiederherstellen.

So stellen Sie die Vererbung zielgerichteter Inhalte in einer Aktivität wieder her:

1. Navigieren Sie zu der Seite, auf der die Vererbung wiederhergestellt werden soll, und wählen Sie im Modus-Dropdown-Menü die Option **Targeting** aus.
1. Wählen Sie **Targeting starten**.
1. Wählen Sie im Dropdownmenü in der Symbolleiste die Option **Live Copy fortsetzen**.

   ![Live Copy wird fortgesetzt](/help/sites-cloud/authoring/assets/multisite-resume.png)

1. Wählen Sie **Fortsetzen** aus, um zu bestätigen, dass die Vererbung für die Live Copy wiederhergestellt werden soll. Alle Änderungen, die an der aktuellen Aktivität vorgenommen wurden, gehen beim Wiederherstellen der Vererbung verloren.

## Löschen von Gebieten {#deleting-areas}

Wenn Sie ein Gebiet löschen, werden alle Aktivitäten in diesem Gebiet ebenfalls gelöscht. AEM warnt Sie, bevor Sie ein Gebiet löschen können. Sollten Sie ein Gebiet löschen, das mit einer Site verknüpft ist, wird die Marke stattdessen automatisch mit dem primären Gebiet verknüpft.

So löschen Sie Gebiete:

1. Navigieren Sie zu **Personalisierung** > **Aktivitäten** oder **Angebote** und dann zu Ihrer Marke.
1. Wählen Sie das Symbol neben dem zu löschenden Gebiet aus.
1. Wählen Sie **Löschen** aus und bestätigen Sie, dass das Gebiet gelöscht werden soll.
