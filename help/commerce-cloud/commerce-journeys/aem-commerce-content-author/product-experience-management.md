---
title: Erstellen von Produkterlebnissen
description: Erfahren Sie, wie Sie Produkterlebnisse erstellen.
source-git-commit: 2d981424d22e2c8d16505eb0cc77c67d5df2bc64
workflow-type: tm+mt
source-wordcount: '1153'
ht-degree: 1%

---

# Erstellen von Produkterlebnissen {#building-experiences}

Erfahren Sie, wie Sie Produkterlebnisse verwalten.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der Journey für AEM Content and Commerce [Erlebnisse im gestaffelten Produktkatalog verwalten](staged-catalog.md), haben Sie gelernt, wie Sie gestaffelte Produktkatalog-Erlebnisse verwalten.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie Produktinhalte und Erlebnisse erstellen.

## Produkt-Experience-Management {#management}

Product Experience Management ist die Disziplin, Produktdaten (die einer PIM- oder Commerce-Lösung gehören) mit Marketinginhalten in AEM zu dekorieren. Diese angereicherten Produktdaten mit Inhalten können dann in verschiedenen Kanälen verwendet werden, um ein interaktives Einkaufserlebnis zu schaffen.

In AEM können Sie verschiedene Inhaltstypen erstellen und mit dem Produktkatalog verknüpfen. Zugehörige Inhalte können leicht erkannt und verwendet werden, was zu einer hohen Produktivität führt.

### Assets {#assets}

Auf hoher Ebene gibt es zwei Arten von Assets, die sich auf Produkte beziehen: Produkt und Marketing. Produkt-Assets werden in der Regel von Händlern verwaltet und konzentrieren sich auf die Anzeige des Produkts (meist vor neutralem Hintergrund). Die Assets werden entweder in der Commerce-Lösung oder in AEM Assets verwaltet (mit einer Assets-Integration in die Commerce-/Pim-Lösung).

Marketing-Assets beziehen sich auf die Promotion und Verwendung des Produkts, das normalerweise im Besitz des Marketing ist. Beispiele sind die Anzeige mehrerer Produkte (&quot;Shop the look&quot;), in einem bestimmten Kontext (&quot;Fallout-Sammlung im Freien&quot;) oder Anleitungen zu PDF-Dateien. CIF bietet eine einfache Möglichkeit, AEM Asset mit dem Produktkatalogobjekt zu verknüpfen.

Öffnen Sie die Asset-Eigenschaften und wechseln Sie zur **Handel** Registerkarte. Auf diesem Tab können Sie die Verknüpfung mit Produkten verwalten. Die Tabelle unter der Auswahl enthält zusätzliche Informationen für die verknüpften Objekte (nur bei einer Auswahl sichtbar). Klicken Sie auf das Detailsymbol, um eine vollständige Ansicht im Produkt-Cockpit zu erhalten. Um ein neues Objekt zuzuordnen, klicken Sie auf das Produktauswahlsymbol (Ordnersymbol), wählen Sie ein Objekt aus und schließen Sie die Auswahl.

![pem assets](assets/pem-assets.png)

### Experience Fragments {#experience-fragments}

Experience Fragments eignen sich hervorragend, um wiederverwendbare oder individuelle Produktinhalte in großem Maßstab zu erstellen. Die Zuordnung funktioniert ähnlich wie ein Asset. Öffnen Sie Eigenschaften und wechseln Sie zu **Handel** Registerkarte. Auf diesem Tab können Sie die Verknüpfung mit Produkten und Kategorien verwalten. Die Tabellen unter den Auswahl-Elementen enthalten zusätzliche Informationen zu den verknüpften Objekten (nur sichtbar bei Auswahl). Klicken Sie auf das Detailsymbol, um eine vollständige Ansicht im Produkt-Cockpit zu erhalten. Um ein neues Objekt zuzuordnen, klicken Sie auf das Produktauswahlsymbol (Ordnersymbol), wählen Sie ein Objekt aus und schließen Sie die Auswahl.

![pem xf](assets/pem-xf.png)

### Inhaltsfragmente {#content-fragments}

Inhaltsfragmente sind der beste Inhaltstyp für strukturierte Inhalte. Dies kann verwendet werden, um externe Produktdaten mit zusätzlichen Marketing-Daten zu ergänzen oder um Inhalte Headless zu erstellen. Die Zuordnung eines Inhaltsfragments zu einem Produktkatalogobjekt erfolgt über die Referenztypen für Produkte oder Kategorien im Inhaltsfragmentmodell-Editor. Ziehen Sie einfach den richtigen Referenztyp auf das Modell und konfigurieren Sie das Feld. Diese Typen unterstützen eine einzelne Auswahl oder eine Mehrfachauswahl.

![pem cf-Modell](assets/pem-cf-model.png)

Wenn Sie ein neues Inhaltsfragment erstellen, das auf diesem Modell basiert, bieten diese Referenztypen eine einfache Möglichkeit, das richtige Objekt mithilfe der entsprechenden Auswahl auszuwählen.

![pem cf](assets/pem-cf.png)

### Produkt-Cockpit {#product-cockpit}

Wir haben das Produkt-Cockpit (oder die Konsole) in einem der vorherigen Module eingeführt. Das Cockpit ist eine einfache Möglichkeit, nicht nur den Produktkatalog zu durchsuchen, sondern auch alle damit verbundenen AEM an einem Ort zu sehen. Wechseln Sie zur Produktkonsole und öffnen Sie die Eigenschaften eines Produkts, das über verknüpften Inhalt verfügt. Wechseln Sie zur entsprechenden Registerkarte, um den zugehörigen Inhalt anzuzeigen.

![pem cockpit](assets/pem-cockpit.png)

Durch Klicken auf das Aktionssymbol wird dieser Inhalt in einer neuen Browser-Registerkarte geöffnet.

## Anreicherung einzelner Produkt- und Kategorieseiten {#enrich}

In den vorherigen Modulen haben Sie gelernt, wie Sie mit mehreren Produktkatalogvorlagen arbeiten können. Mehrere Vorlagen eignen sich hervorragend, um verschiedene Vorlagen zu erstellen, sind aber in vielen Fällen nicht erforderlich. In vielen Fällen kann dieselbe Vorlage in Kombination mit Platzhaltern für einzelne Inhalte verwendet werden. CIF unterstützt Platzhalter für Inhaltsfragmente und Experience Fragments.

Beginnen wir mit dem Experience Fragment-Platzhalter. Öffnen Sie eine Produktvorlage im AEM-Editor. Ziehen Sie die **Commerce Experience Fragment** auf der Vorlage und öffnen Sie dann das Konfigurationsdialogfeld.

![PEM-Platzhalter](assets/pem-placeholder.png)

Öffnen Sie das Dialogfeld der Komponente und geben Sie einen Namen für diesen Platzhalter ein. Der Platzhaltername ist erforderlich und ermöglicht das Hinzufügen beliebig vieler Platzhalter.

![Dialogfeld &quot;pem XF&quot;](assets/pem-dialog-xf.png)

Öffnen Sie das Experience Fragment, das Sie im vorherigen Schritt mit einem Produkt verknüpft haben. Öffnen Sie die Eigenschaften und wechseln Sie zur Registerkarte &quot;Commerce&quot;. Geben Sie unter denselben Platzhalternamen ein **Speicherort des Katalogplatzhalters**.

![pem xf](assets/pem-xf.png)

Ziehen Sie jetzt die **Commerce-Inhaltsfragment** -Komponente in der Vorlage und öffnen Sie das Konfigurationsdialogfeld.

![pem CF-Dialogfeld](assets/pem-dialog-cf.png)

Dieses Dialogfeld verwendet das Dialogfeld Kernkomponente &quot;Inhaltsfragment&quot; erneut. Weitere Informationen finden Sie unter Zusätzliche Ressourcen. Der einzige Unterschied ist die **Link-Element** -Eigenschaft, die das Identifizierungsfeld (Produkt-SKU oder Kategorie-UID) im Inhaltsfragmentmodell konfiguriert.

Zeigen Sie jetzt eine Produktseite mit einem zugehörigen Inhaltsfragment und/oder Experience Fragment in der Vorschau an. Wenn AEM eine Seite rendert, sucht sie nach jedem Platzhalter basierend auf dem Typ (Inhalt oder Experience Fragment), der Kennung und dem Platzhalternamen für Experience Fragments. AEM verwendet einen URL-Resolver, um die Kennung abzurufen (SKU für Produkte, UID für Kategorien). Wenn ein Erlebnis oder ein Inhaltsfragment zurückgegeben wird, wird es an der Position des Platzhalters gerendert, andernfalls wird der Platzhalter ignoriert.

![pem result](assets/pem-result.png)

## Erstellen von Inhalten mit Shopping-Funktion {#making-shoppable}

Es ist auch möglich, eine reguläre AEM durch Hinzufügen von Commerce-Komponenten Shop-fähig zu machen. Erstellen Sie eine neue Inhaltsseite in AEM und öffnen Sie die leere Seite im Editor.

![leere Seite](assets/pem-page-empty.png)

Ziehen Sie zunächst eine Produktdetailkomponente auf die Seite. Wechseln Sie dann zur Seitenleiste &quot;Assets&quot;, wechseln Sie zu &quot;products&quot;und wählen Sie ein Produkt aus. Ziehen Sie das Produkt per Drag-and-Drop in die Produktkomponente. Dadurch wird eine normale Produktkomponente auf einer Inhaltsseite angezeigt.

![Produktseite von pem](assets/pem-page-product.png)

Wenn Sie verknüpften Inhalt für dieses Produkt erstellt haben, wechseln Sie in der Seitenleiste &quot;Assets&quot;zu **Zugehörige Commerce-Inhalte**. Auf dieser Registerkarte werden alle AEM Inhalte angezeigt, die mit diesem Produkt verknüpft waren. Dadurch können Sie die Seiten schnell mit allen zugehörigen Inhalten vereinfachen.

![Geberte Seite](assets/pem-page-enriched.png)

## Ende der Journey? {#end-of-journey}

Herzlichen Glückwunsch! Sie haben die AEM Content and Commerce Developer Journey abgeschlossen! Sie sollten jetzt:

* Erfahren Sie, wie Sie beliebige AEM mit Produktkatalog-Objekten verknüpfen können
* Verwenden von Platzhaltern zur individuellen Anreicherung von Produkt- und Kategorieseiten
* Erfahren Sie, wie Sie Inhalte mit Shopping-Funktion versehen und die zugehörige Registerkarte &quot;Inhalt&quot;verwenden

Sie können jetzt Produkterlebnisse mit AEM Content und Commerce verwalten. Für AEM Inhalte und Commerce stehen jedoch viele zusätzliche Optionen zur Verfügung. Sehen Sie sich einige der zusätzlichen Ressourcen an, die im Abschnitt [Abschnitt &quot;Zusätzliche Ressourcen&quot;](#additional-resources) um mehr über die Funktionen zu erfahren, die Sie auf dieser Journey gesehen haben.

## Zusätzliche Ressourcen {#additional-resources}

* [Verfassen von Commerce-Erlebnissen](/help/commerce-cloud/authoring/authoring-commerce-experiences.md)
* [Inhaltsfragment-Komponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/content-fragment-component.html?lang=en)
