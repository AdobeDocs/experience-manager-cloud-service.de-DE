---
title: Wiederverwenden von Inhaltsfragmenten mit MSM und Live Copies
description: Erfahren Sie, wie Sie mit der Live Copy-Funktion von MSM dieselben oder ähnliche Inhaltsfragmentinhalte an mehreren Stellen verwenden können, während sie mit dem Quellinhalt synchronisiert werden.
badgeSaas: label="AEM Sites" type="Positive" tooltip="Gilt für AEM Sites)."
feature: Content Fragments
role: User
solution: Experience Manager Sites
hide: true
index: false
exl-id: 5039cf92-21ff-4d6c-a684-72eab13b519d
source-git-commit: 77f7d21eed1322de768ee07e3518638f60e3ae40
workflow-type: tm+mt
source-wordcount: '950'
ht-degree: 29%

---

# Wiederverwenden von Inhaltsfragmenten mit MSM {#reuse-content-fragments-using-msm}

Mit Multi Site Manager (MSM) und dessen Live Copy-Funktionen können Sie dieselben Inhalte an mehreren Orten verwenden und gleichzeitig mit den Quellinhalten synchronisieren.

<!-- CQDOC-23473 - feature is currently beta so page is hidden, see metadata -->
<!-- CQDOC-23473 - screenshots -->
<!-- CQDOC-23473 - only mentioned once in ToC, add entries -->
<!-- CQDOC-23473 - will work on folders -->

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

>[!CAUTION]
>
>MSM aus der Inhaltsfragmentkonsole ist derzeit mit Beta-Funktionen ausgestattet und steht nur bestimmten Kunden zur Verfügung.
>
>MSM für Inhaltsfragmente ist auch bei der Verwendung von Inhaltsfragmenten über die **Assets**-Konsole verfügbar.

* Mit MSM Live Copies können Sie:
   * Einmaliges Erstellen von Inhalten
   * Inhalte in anderen Bereichen derselben Site, auf anderen Sites oder in Programmen wiederverwenden.
* MSM behält dann die Live-Beziehungen zwischen Ihren Quellinhalten und deren Live Copies bei, sodass:
   * die Quelle und die Live Copies synchronisiert werden, wenn den Quellinhalt ändern.
   * Sie können nur am Inhalt der Live Copies Anpassungen vornehmen, indem Sie die Live-Beziehung für einzelne Unterfragmente und/oder Komponenten trennen.

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

Einen detaillierten Überblick über MSM-Konzepte finden Sie unter Wiederverwenden von Inhalten: Multi-Site-Manager und Live Copy.

<!--
For a detailed overview of MSM concepts see [Reusing Content: Multi Site Manager and Live Copy](/help/sites-cloud/administering/msm/overview.md).
-->

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

>[!NOTE]
>
>Mit der Funktion „Multi Site Manager“ (MSM) in Adobe Experience Manager können Benutzer einmal erstellte Inhalte über mehrere Web-Speicherorte hinweg wiederverwenden.

<!--
>[!NOTE]
>
>[Multi Site Manager (MSM)](/help/sites-cloud/administering/msm/overview.md) functionality in Adobe Experience Manager enables users to reuse content that is authored once and then reused across multiple web-locations. 
-->

Mit MSM für Inhaltsfragmente können Sie:

* Einmal Inhaltsfragmente anlegen und dann (verknüpfte) Kopien dieser Fragmente erstellen, um sie in anderen Bereichen der Site oder Anwendung wiederzuverwenden.
* Mehrere Kopien synchron halten, indem Sie die Quellkopie einmal aktualisieren und die Änderungen dann an die Kopien bzw. Live Copies übertragen.
* Lokale Änderungen vornehmen, indem Sie vorübergehend oder dauerhaft die Verknüpfung zwischen übergeordneten und untergeordneten Fragmenten vollständig oder für deren Varianten oder Felder unterbrechen.

Mit MSM für Inhaltsfragmente in Verbindung mit Funktionen im Inhaltsfragmenteditor können Sie die Vererbung auf Feldebene unterbrechen und reaktivieren.

<!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

>[!NOTE]
>
>Auf dieser Seite werden die MSM-Funktionen bei Verwendung der **Inhaltsfragmente**-Konsole behandelt.
>
>MSM für Inhaltsfragmente ist auch bei der Verwendung von Inhaltsfragmenten über die **Assets**-Konsole verfügbar.

<!--
>[!NOTE]
>
>This page covers MSM functionality when using the **Content Fragments** console.
>
>MSM for Content Fragments is also available when using [Content Fragments via the **Assets** console](/help/assets/content-fragments/content-fragments-msm.md). 
-->

## Erstellen einer Live Copy {#create-a-live-copy}

<!-- CQDOC-23473 - exclude children or referenced content fragments? -->

Erstellen einer Live Copy Ihres Inhaltsfragments:

1. Navigieren Sie in der Inhaltsfragmentkonsole zum Speicherort des gewünschten Fragments.
1. Wählen Sie Ihr Fragment aus.
1. Wählen **Live Copy erstellen** in der oberen Symbolleiste aus.
1. Geben Sie in dem daraufhin angezeigten Dialogfeld das Ziel an und setzen Sie den Vorgang mit **Weiter** fort.
1. Geben Sie die Eigenschaften an. Sie können den Titel, den Namen und angeben, ob die Live Copy untergeordnete Elemente (verschachtelte Fragmente) ausschließen soll.
1. Fahren Sie mit **Weiter** fort.
1. Wählen Sie aus, ob die Live Copy sofort (**Jetzt**) oder zu einem **Später** Zeitpunkt erstellt werden soll.
1. Bestätigen Sie mit **Live Copy erstellen**.

   <!-- CQDOC-23473 - feature is currently beta remove Caution for GA -->

   >[!CAUTION]
   >
   >Wenn Sie mit MSM Kopien von Inhaltsfragmenten erstellen möchten), sollten alle **Unique**-Einschränkungen aus allen Datentypen entfernt werden, die in den entsprechenden Inhaltsfragmentmodellen verwendet werden.

   <!--
   >[!CAUTION]
   >
   >If you want to use MSM to create copies of Content Fragments), then any **Unique** constraints should be removed from any Data Types used in the respective [Content Fragment Models](/help/assets/content-fragments/content-fragments-models.md).
   -->

## Eigenschaften und Status anzeigen {#view-properties-and-status}

So zeigen Sie die Eigenschaften und den Status der Quelle und Ihrer Live Copy an:

1. Navigieren Sie in der Inhaltsfragmentkonsole zum Speicherort des gewünschten Fragments.
1. Wählen Sie Ihr Fragment aus.
1. Wählen Sie das Informationssymbol (i) in der Spalte **Titel** Ihres Fragments aus.
Das rechte Informationsfenster öffnet sich.
1. Wählen Sie die Registerkarte für **Live Copy-Details**.

   ![Informationen auf einer Live Copy](/help/sites-cloud/administering/content-fragments/assets/cf-msm-information.png)

## Änderungen ausdehnen {#propagate-modifications}

So übertragen Sie Änderungen zwischen der Quelle und Ihrer Live Copy.

### Synchronisieren {#synchronize}

So führen Sie einen Trigger für eine Synchronisierung durch, bei der die Inhaltsaktualisierungen von Ihrer Live Copy an die Quelle übertragen werden:

1. Navigieren Sie in der Inhaltsfragmentkonsole zum Speicherort der Fragmentquelle.
1. Wählen Sie Ihr Fragment aus.
1. Wählen Sie in der Symbolleiste die Option **Synchronisieren** aus.
1. Bestätigen Sie **Synchronisieren** im Dialogfeld.

### Rollout {#rollout}

So erstellen Sie einen Trigger für einen Rollout, bei dem die Quellaktualisierungen an Ihre Live Copy gesendet werden:

1. Navigieren Sie in der Inhaltsfragmentkonsole zum Speicherort der Live Copy des Fragments.
1. Wählen Sie Ihr Fragment aus.
1. Wählen Sie in der Symbolleiste die Option **Rollout** aus. Der Assistent wird geöffnet, um Sie durch den Prozess zu führen.
1. Wählen Sie die Live Copies aus, die in den Rollout eingeschlossen werden sollen, und **Sie**.
1. Planen Sie den Rollout für sofort (**Jetzt**) oder **Später**.
1. **Weiter** soweit erforderlich.

<!-- CQDOC-23473 - feature is beta, is in authoring so remove here when GA -->

## Abbrechen und Wiederherstellen der Vererbung im Editor {#cancel-and-revert-to-inheritance-in-the-editor}

Vererbung ist der Mechanismus, bei dem Inhalte automatisch von einer Komponente in eine andere verschoben werden können. Übernommene Felder und Varianten können das Produkt des Multi-Site-Managements sein.

Sie können die Vererbung im Inhaltsfragment-Editor abbrechen (und dann wiederherstellen). Je nach Kontext kann dies für eine Variante oder ein einzelnes Feld verfügbar sein, wenn das Fragment Teil einer Live Copy ist.

Zum Beispiel:

* Abbrechen der Vererbung

  ![Symbol „Vererbung abbrechen“](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-cancel-inheritance.png)

* Auf Vererbung zurücksetzen (wenn die Vererbung bereits abgebrochen wurde)

  ![Symbol „Vererbung wiederherstellen“](/help/sites-cloud/administering/content-fragments/assets/cf-authoring-revert-to-inheritance.png)

<!-- CQDOC-23473 - feature is currently beta reinstate Note for GA -->

<!--
## Cancel, and revert to, inheritance {#cancel-and-reinstate-inheritance}

Inheritance is the mechanism where content can be automatically pushed from one fragment to another. Inherited fields, and variations, can be the product of Multi-Site Management.

You can cancel (then revert) the inheritance. Depending on the context, this can be available for a variation, or an individual field, if the fragment is part of a live copy.
-->

<!--
>[!NOTE]
>
>For more details see [Cancel, and revert to, inheritance in the editor](/help/sites-cloud/administering/content-fragments/authoring.md#cancel-and-revert-to-inheritance).
-->

## Vergleich von MSM für Inhaltsfragmente und Sites-Seiten {#compare-msm-for-content-fragments-and-sites-pages}

<!-- CQDOC-23473 - needs a detailed review -->

In den meisten Szenarien entspricht das Verhalten von MSM für Inhaltsfragmente dem von MSM für Sites für Seiten. Einige wichtige Unterschiede lauten wie folgt:

* Blueprints in MSM für Sites-Seiten werden in MSM für Inhaltsfragmente als Live Copy-Quellen bezeichnet.
* Bei Sites-Seiten können Sie Blueprints und deren Live Copies vergleichen. Inhaltsfragmente können jedoch keine Quelle mit der zugehörigen Live Copy vergleichen.
* Live Copies können nicht in der Inhaltsfragmentkonsole bearbeitet werden.
* Sites-Seiten haben in der Regel untergeordnete Elemente, Inhaltsfragmente jedoch nicht, obwohl sie möglicherweise referenzierte Fragmente enthalten. Die Option zum Ein- oder Ausschließen von untergeordneten Elementen bezieht sich auf diese referenzierten Fragmente.
* Das Entfernen des Schritts „Kapitel“ im Assistenten zum Erstellen von Sites wird in MSM für Inhaltsfragmente nicht unterstützt.
* Das Konfigurieren von MSM-Sperren in Seiteneigenschaften wird in MSM für Inhaltsfragmente nicht unterstützt.
* Verwenden Sie für MSM für Inhaltsfragmente nur die **standardmäßige Rollout-Konfiguration**. Andere Rollout-Konfigurationen sind für MSM für Inhaltsfragmente nicht verfügbar.

>[!NOTE]
>
>Beachten Sie, dass MSM für Inhaltsfragmente, auf die über die Inhaltsfragmentkonsole zugegriffen wird, auf der Assets-Funktionalität basiert. Dies liegt daran, dass sie als Assets gespeichert werden (obwohl sie als Sites-Funktion betrachtet werden).

## Einschränkungen {#limitations}

* Trigger, die sich auf Änderungen beziehen, und die zugehörige Rollout-Konfiguration sind für Inhaltsfragmente nicht vorhanden.
