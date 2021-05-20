---
title: Konfigurieren der Synchronisierung von Live Copies
description: Erfahren Sie mehr über die leistungsstarken Synchronisierungsoptionen für Live Copy und wie Sie sie entsprechend den Anforderungen Ihres Projekts konfigurieren und anpassen können.
feature: Multi-Site-Manager
role: Administrator
exl-id: 0c97652c-edac-436e-9b5b-58000bccf534
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '2339'
ht-degree: 33%

---

# Konfigurieren der Synchronisierung von Live Copies {#configuring-live-copy-synchronization}

Adobe Experience Manager bietet eine Reihe vordefinierter Synchronisierungskonfigurationen. Bevor Sie Live Copies verwenden, sollten Sie Folgendes berücksichtigen, um zu definieren, wie und wann Live Copies mit ihrem Quellinhalt synchronisiert werden.

1. Entscheiden Sie, ob vorhandene Rollout-Konfigurationen Ihren Anforderungen entsprechen.
1. Wenn vorhandene Rollout-Konfigurationen dies nicht tun, entscheiden Sie, ob Sie eine eigene erstellen müssen.
1. Geben Sie die Rollout-Konfigurationen an, die für Ihre Live Copies verwendet werden sollen.

## Installierte und benutzerdefinierte Rollout-Konfigurationen {#installed-and-custom-rollout-configurations}

In diesem Abschnitt finden Sie Informationen zu den installierten Rollout-Konfigurationen und den von ihnen verwendeten Synchronisierungsaktionen. Außerdem erfahren Sie, wie Sie bei Bedarf benutzerdefinierte Konfigurationen erstellen.

>[!CAUTION]
>
>Das Aktualisieren oder Ändern einer vordefinierten Rollout-Konfiguration wird **nicht** empfohlen. Wenn eine benutzerdefinierte Live-Aktion erforderlich ist, sollte sie in einer benutzerdefinierten Rollout-Konfiguration hinzugefügt werden.

### Rollout-Auslöser {#rollout-triggers}

Jede Rollout-Konfiguration nutzt einen Rollout-Auslöser, der den Rollout auslöst. Rollout-Konfigurationen können einen der folgenden Auslöser verwenden:

* **Bei Rollout**: Der  **** Befehl &quot;Rollout&quot;wird auf der blauen Druckseite verwendet oder der Befehl &quot; **** Synchronisieren&quot;wird auf der Seite &quot;Live Copy&quot;verwendet.
* **Bei Modifizierung**: Die Quellseite wird bearbeitet.
* **Bei Aktivierung**: Die Quellseite wird aktiviert.
* **Bei Deaktivierung**: Die Quellseite wird deaktiviert.

>[!NOTE]
>
>Die Verwendung des Triggers **Bei Änderung** kann sich auf die Leistung auswirken. Weitere Informationen finden Sie in den [Best Practices für MSM](best-practices.md#onmodify).

### Rollout-Konfigurationen {#rollout-configurations}

In der folgenden Tabelle sind die Rollout-Konfigurationen aufgeführt, die standardmäßig mit AEM bereitgestellt werden. Auslöser und Synchronisierungsaktionen jeder Rollout-Konfigurationen werden ebenfalls angegeben.

<!--
If the installed rollout configuration actions do not meet your requirements, you can [create a new rollout configuration](#creating-a-rollout-configuration).
-->

| Name | Beschreibung | Auslöser | [Synchronisierungsaktionen](#synchronization-actions) |
|---|---|---|---|
| Standard-Rollout-Konfiguration | Standard-Rollout-Konfiguration, die den Start des Rollout-Prozesses bei Rollout-Auslösern ermöglicht und Aktionen ausführt: Erstellen, Aktualisieren, Löschen von Inhalten und Sortierung untergeordneter Knoten | Bei Rollout | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`referencesUpdate`<br>`productUpdate`<br>`orderChildren` |
| Bei Blueprint-Aktivierung aktivieren | Veröffentlicht die Live Copy, wenn die Quelle veröffentlicht wird | Bei Aktivierung | `targetActivate` |
| Bei Blueprint-Deaktivierung deaktivieren | Deaktiviert die Live Copy, wenn die Quelle deaktiviert wird | Bei Deaktivierung | `targetDeactivate` |
| Push bei Bearbeitung | Verschiebt den Inhalt in die Live Copy, wenn die Quelle geändert wird<br>Verwenden Sie diese Rollout-Konfiguration sparsam, da sie den Trigger Bei Änderung verwendet. | Bei Modifizierung | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`referencesUpdate`<br>`orderChildren` |
| Push bei Bearbeitung (leicht) | Gibt Inhalt bei Änderung der Blueprint-Seite in die Live Copy weiter, ohne die Verweise zu aktualisieren (z. B. für flache Kopien)<br>Verwenden Sie diese Rollout-Konfiguration sparsam, da sie den Trigger &quot;Bei Modifizierung&quot;verwendet. | Bei Modifizierung | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`orderChildren` |
| Launch bewerben | Standard-Rollout-Konfigurationen zur Veröffentlichung von Startseiten. | Bei Rollout | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`referencesUpdate`<br>`orderChildren`<br>`markLiveRelationship` |

### Synchronisierungsaktionen {#synchronization-actions}

In der folgenden Tabelle sind die Synchronisierungsaktionen aufgeführt, die standardmäßig mit AEM bereitgestellt werden.

<!--If the installed actions do not meet your requirements, you can [Create a New Synchronization Action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action).-->

| Aktionsname | Beschreibung | Eigenschaften |
|---|---|---|
| `contentCopy` | Wenn Knoten der Quelle nicht in der Live Copy vorhanden sind, kopiert diese Aktion die Knoten in die Live Copy. [Konfigurieren Sie den Dienst  **CQ MSM Content Copy** ](#excluding-properties-and-node-types-from-synchronization) Action , um die Knotentypen, Absatzelemente und Seiteneigenschaften festzulegen, die ausgeschlossen werden sollen. |  |
| `contentDelete` | Durch diese Aktion werden Knoten der Live Copy gelöscht, die nicht in der Quelle vorhanden sind. [Konfigurieren Sie den Dienst  **CQ MSM Content Delete** ](#excluding-properties-and-node-types-from-synchronization) Action , um die Knotentypen, Absatzelemente und Seiteneigenschaften festzulegen, die ausgeschlossen werden sollen. |  |
| `contentUpdate` | Diese Aktion aktualisiert den Live Copy-Inhalt mit den Änderungen aus der Quelle. [Konfigurieren Sie den Dienst  **CQ MSM Content Update** ](#excluding-properties-and-node-types-from-synchronization) Action , um die Knotentypen, Absatzelemente und Seiteneigenschaften festzulegen, die ausgeschlossen werden sollen. |  |
| `editProperties` | Diese Aktion bearbeitet die Eigenschaften der Live Copy. Die `editMap`-Eigenschaft bestimmt, welche Eigenschaften bearbeitet werden, und deren Wert. Der Wert der Eigenschaft `editMap` muss das folgende Format aufweisen:<br>`[property_name_n]#[current_value]#[new_value]`<br>`current_value` und `new_value` sind reguläre Ausdrücke und `n` ist eine inkrementierte Ganzzahl.<br>Betrachten Sie beispielsweise den folgenden Wert für  `editMap`:<br>`sling:resourceType#/(contentpage` ‖ `homepage)#/mobilecontentpage,cq:template#/contentpage#/mobilecontentpage`<br>Dieser Wert bearbeitet die Eigenschaften der Live Copy-Knoten wie folgt:<br>Die  `sling:resourceType` Eigenschaften, die entweder auf  `contentpage` oder auf gesetzt  `homepage` sind, sind auf  `mobilecontentpage`festgelegt.<br>Die  `cq:template` Eigenschaften, die auf festgelegt  `contentpage` sind, sind auf  `mobilecontentpage`festgelegt. | `editMap: (String)` gibt die Eigenschaft, den aktuellen Wert und den neuen Wert an. Weitere Informationen finden Sie in der Beschreibung . |
| `notify` | Durch diese Aktion wird ein Seitenereignis gesendet, bei dem das Rollout der Seite erfolgt ist. Um Benachrichtigungen zu erhalten, müssen Benutzer zunächst Rollout-Ereignisse abonnieren. |  |
| `orderChildren` | Diese Aktion ordnet die untergeordneten Knoten basierend auf der Reihenfolge im Blueprint an. |  |
| `referencesUpdate` | Diese Synchronisierungsaktion aktualisiert die Verweise auf die Live Copy.<br>Er sucht auf den Live Copy-Seiten nach Pfaden, die auf eine Ressource innerhalb des Blueprints verweisen. Wenn sie gefunden wird, aktualisiert sie den Pfad, um auf die zugehörige Ressource in der Live Copy zu verweisen. Verweise, die Ziele außerhalb des Blueprints aufweisen, werden nicht geändert. <br>[Konfigurieren Sie den Dienst  **CQ MSM References Update** ](#excluding-properties-and-node-types-from-synchronization) Action , um die Knotentypen, Absatzelemente und Seiteneigenschaften festzulegen, die ausgeschlossen werden sollen. |  |
| `targetVersion` | Diese Aktion erstellt eine Version der Live Copy.<br>Diese Aktion muss die einzige Synchronisierungsaktion in einer Rollout-Konfiguration sein. |  |
| `targetActivate` | Diese Aktion aktiviert die Live Copy.<br>Diese Aktion muss die einzige Synchronisierungsaktion in einer Rollout-Konfiguration sein. |  |
| `targetDeactivate` | Diese Aktion deaktiviert die Live Copy.<br>Diese Aktion muss die einzige Synchronisierungsaktion in einer Rollout-Konfiguration sein. |  |
| `workflow` | Diese Aktion startet den Workflow, der durch die Zieleigenschaft definiert wird (nur für Seiten), und übernimmt die Live Copy als Nutzlast.<br>Der Zielpfad ist der Pfad des Modellknotens. | `target: (String)` ist der Pfad zum Workflow-Modell. |
| `mandatory` | Durch diese Aktion wird die Berechtigung mehrerer ACLs auf der Live Copy-Seite für eine bestimmte Benutzergruppe auf schreibgeschützt gesetzt. Die folgenden ACLs sind konfiguriert:<br>`ActionSet.ACTION_NAME_REMOVE`<br>`ActionSet.ACTION_NAME_SET_PROPERTY`<br>`ActionSet.ACTION_NAME_ACL_MODIFY`<br>Verwenden Sie diese Aktion nur für Seiten. | `target: (String)` ist die ID der Gruppe, für die Sie Berechtigungen festlegen. |
| `mandatoryContent` | Durch diese Aktion wird die Berechtigung mehrerer ACLs auf der Live Copy-Seite für eine bestimmte Benutzergruppe auf schreibgeschützt gesetzt. Die folgenden ACLs sind konfiguriert:<br>`ActionSet.ACTION_NAME_SET_PROPERTY`<br>`ActionSet.ACTION_NAME_ACL_MODIFY`<br>Verwenden Sie diese Aktion nur für Seiten. | `target: (String)` ist die ID der Gruppe, für die Sie Berechtigungen festlegen. |
| `mandatoryStructure` | Durch diese Aktion wird die Berechtigung der ACL `ActionSet.ACTION_NAME_REMOVE` auf der Live Copy-Seite für eine bestimmte Benutzergruppe auf schreibgeschützt gesetzt.<br>Nutzen Sie diese Aktion nur für Seiten. | `target: (String)` ist die ID der Gruppe, für die Sie Berechtigungen festlegen. |
| `VersionCopyAction` | Wenn die Blueprint-/Quellseite mindestens einmal veröffentlicht wurde, erstellt diese Aktion eine Live Copy-Seite mit der veröffentlichten Version. Hinweis: Diese Aktion ist nur zum Erstellen einer Live Copy-Seite basierend auf einer veröffentlichten Quellseite verfügbar, nicht zum Aktualisieren einer vorhandenen Live Copy-Seite. |  |
| `PageMoveAction` | `PageMoveAction` gilt, wenn eine Seite in den Blueprint verschoben wurde.<br>Die Aktion kopiert statt verschiebt die (zugehörige) Live Copy-Seite von der Position vor dem Verschieben an die Position nach.<br>Die Live Copy-Seite  `PageMoveAction` wird nicht am Speicherort vor dem Verschieben geändert. Daher hat es für aufeinander folgende Rollout-Konfigurationen den Status einer Live-Beziehung ohne Blueprint.<br>[**** Konfigurieren Sie den Dienst „CQ MSM Page Move Action“](#excluding-properties-and-node-types-from-synchronization), um die Knotentypen, Absatzelemente und Seiteneigenschaften festzulegen, die ausgeschlossen werden sollen.<br>Diese Aktion muss die einzige Synchronisierungsaktion in einer Rollout-Konfiguration sein. | Setzen Sie `prop_referenceUpdate: (Boolean)` auf &quot;true&quot;(Standard), um Verweise zu aktualisieren. |
| `markLiveRelationship` | Diese Aktion Gibt an, dass eine Live-Beziehung für vom Launch erstellte Inhalte vorhanden ist. |  |

<!--
### Creating a Rollout Configuration {#creating-a-rollout-configuration}

You can [create a rollout configuration](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration) when the installed rollout configurations do not meet your application requirements by performing the following steps.

1. [Create the rollout configuration](/help/sites-developing/extending-msm.md#create-the-rollout-configuration).
1. [Add synchronization actions to the rollout configuration](/help/sites-developing/extending-msm.md#add-synchronization-actions-to-the-rollout-configuration).

The new rollout configuration is then available to you when configuring rollout configurations on a blueprint or Live Copy page.
-->

### Ausschließen von Eigenschaften und Knotentypen von der Synchronisierung {#excluding-properties-and-node-types-from-synchronization}

Sie können mehrere OSGi-Dienste konfigurieren, die die entsprechenden Synchronisierungsaktionen unterstützen, sodass sie sich nicht auf bestimmte Knotentypen und Eigenschaften auswirken. Beispielsweise sollten viele Eigenschaften und Unterknoten im Zusammenhang mit der internen Funktionsweise von AEM nicht in eine Live Copy aufgenommen werden. Nur der Inhalt, der für den Benutzer der Seite relevant ist, sollte kopiert werden.

Bei der Arbeit mit AEM gibt es verschiedene Methoden, die Konfigurationseinstellungen für solche Dienste zu verwalten. Weitere Informationen und empfohlene Vorgehensweisen finden Sie unter [Konfigurieren von OSGi](/help/implementing/deploying/configuring-osgi.md).

In der folgenden Tabelle sind die Synchronisierungsaktionen aufgeführt, von denen Sie Knoten ausschließen können. Die Tabelle führt die Namen der Services an, die mit der Web-Konsole und der PID mit Repository-Knoten konfiguriert werden.

| Synchronisierungsaktion | Dienstname in der Web-Konsole | Service PID |
|---|---|---|
| `contentCopy` | CQ MSM Content Copy Action | `com.day.cq.wcm.msm.impl.actions.ContentCopyActionFactory` |
| `contentDelete` | CQ MSM Content Delete Action | `com.day.cq.wcm.msm.impl.actions.ContentDeleteActionFactory` |
| `contentUpdate` | CQ MSM Content Update Action | `com.day.cq.wcm.msm.impl.actions.ContentUpdateActionFactory` |
| `PageMoveAction` | CQ MSM Page Move Action | `com.day.cq.wcm.msm.impl.actions.PageMoveActionFactory` |
| `referencesUpdate` | Aktualisierungsaktion für CQ MSM-Referenzen | `com.day.cq.wcm.msm.impl.actions.ReferencesUpdateActionFactory` |

In der folgenden Tabelle werden die Eigenschaften beschrieben, die Sie konfigurieren können:

| Webkonsoleneigenschaft | OSGi-Eigenschaft | Beschreibung |
|---|---|---|
| Ausgeschlossene Knotentypen | `cq.wcm.msm.action.excludednodetypes` | Ein regulärer Ausdruck, der den Knotentypen entspricht, die von der Synchronisierungsaktion ausgeschlossen werden sollen |
| Ausgeschlossene Absatzelemente | `cq.wcm.msm.action.excludedparagraphitems` | Ein regulärer Ausdruck, der mit den von der Synchronisierungsaktion auszuschließenden Absatzelementen übereinstimmt |
| Ausgeschlossene Seiteneigenschaften | `cq.wcm.msm.action.excludedprops` | Ein regulärer Ausdruck, der mit den Seiteneigenschaften übereinstimmt, die von der Synchronisierungsaktion ausgeschlossen werden sollen |
| Ignorierte Mixin-NodeTypes | `cq.wcm.msm.action.ignoredMixin` | Ein regulärer Ausdruck, der mit den Namen der Mixin-Knotentypen übereinstimmt, die von der Synchronisierungsaktion ausgeschlossen werden sollen (nur für die Aktion `contentUpdate` verfügbar) |

#### CQ MSM Content Update Action – Ausschlüsse {#cq-msm-content-update-action-exclusions}

Einige Eigenschaften und Knotentypen sind standardmäßig ausgeschlossen. Sie sind in der OSGi-Konfiguration der Aktion **CQ MSM Content Update Action** unter **Ausgeschlossene Seiteneigenschaften** definiert.

Standardmäßig werden Eigenschaften, die mit den folgenden regulären Ausdrücken übereinstimmen, beim Rollout ausgeschlossen (d. h. nicht aktualisiert):

![Live Copy-Ausschlussregex](../assets/live-copy-exclude.png)

Sie können die Ausdrücke, die die Ausschlussliste definieren, bei Bedarf ändern.

Wenn Sie beispielsweise möchten, dass die Seite **Title** bei den Änderungen enthalten sein soll, die beim Rollout berücksichtigt werden, entfernen Sie `jcr:title` von den Ausschlüssen, z. B. mit dem regulären Ausdruck:

`jcr:(?!(title)$).*`

### Konfigurieren der Synchronisierung für die Aktualisierung von Verweisen {#configuring-synchronization-for-updating-references}

Sie können mehrere OSGi-Dienste konfigurieren, die die entsprechenden Synchronisierungsaktionen im Zusammenhang mit der Aktualisierung von Verweisen unterstützen.

Bei der Arbeit mit AEM gibt es verschiedene Methoden, die Konfigurationseinstellungen für solche Dienste zu verwalten. Weitere Informationen und empfohlene Vorgehensweisen finden Sie unter [Konfigurieren von OSGi](/help/implementing/deploying/configuring-osgi.md).

In der folgenden Tabelle sind die Synchronisierungsaktionen aufgeführt, für die Sie die Verweisaktualisierung festlegen können. Die Tabelle führt die Namen der Services an, die mit der Web-Konsole und der PID mit Repository-Knoten konfiguriert werden.

| Webkonsoleneigenschaft | OSGi-Eigenschaft | Beschreibung |
|---|---|---|
| Aktualisieren der Referenz über verschachtelte Live Copies hinweg | `cq.wcm.msm.impl.action.referencesupdate.prop_updateNested` | Wählen Sie diese Option in der Web-Konsole aus oder legen Sie diese boolesche Eigenschaft mithilfe der Repository-Konfiguration auf `true` fest, um Verweise zu ersetzen, die auf eine Ressource abzielen, die sich in der Verzweigung der am weitesten oben stehenden Live Copy befindet. Nur für die Aktion `referencesUpdate` verfügbar. |
| Verweisende Seiten aktualisieren | `cq.wcm.msm.impl.actions.pagemove.prop_referenceUpdate` | Wählen Sie diese Option in der Web-Konsole aus oder legen Sie diese boolesche Eigenschaft mithilfe der Repository-Konfiguration auf `true` fest, um alle Verweise zu aktualisieren, damit die Originalseite verwendet wird, um stattdessen auf die Live Copy-Seite zu verweisen. Nur verfügbar für `PageMoveAction`. |

## Festlegen der zu verwendenden Rollout-Konfigurationen {#specifying-the-rollout-configurations-to-use}

Mit MSM können Sie Sätze von Rollout-Konfigurationen angeben, die allgemein verwendet werden, und bei Bedarf können Sie sie für bestimmte Live Copies überschreiben. MSM bietet mehrere Orte, an denen Sie die zu verwendenden Rollout-Konfigurationen festlegen können. Der Speicherort bestimmt, ob die Konfiguration für eine bestimmte Live Copy gilt.

In der folgenden Liste der Speicherorte, an denen Sie die zu verwendenden Rollout-Konfigurationen angeben können, wird beschrieben, wie MSM bestimmt, welche Rollout-Konfigurationen für eine Live Copy verwendet werden sollen:

* **[Eigenschaften der Live Copy-Seite](live-copy-sync-config.md#setting-the-rollout-configurations-for-a-live-copy-page):** Wenn eine Live Copy-Seite für die Verwendung einer oder mehrerer Rollout-Konfigurationen konfiguriert ist, verwendet MSM diese Rollout-Konfigurationen.
* **[Eigenschaften der Blueprint-Seite](live-copy-sync-config.md#setting-the-rollout-configuration-for-a-blueprint-page):** Wenn eine Live Copy auf einem Blueprint basiert und die Live Copy-Seite nicht mit einer Rollout-Konfiguration konfiguriert ist, wird die Rollout-Konfiguration verwendet, die mit der Blueprint-Quellseite verknüpft ist.
* **Eigenschaften der übergeordneten Live Copy-Seite:**  Wenn weder die Live Copy-Seite noch die Blueprint-Quellseite mit einer Rollout-Konfiguration konfiguriert sind, wird die Rollout-Konfiguration verwendet, die für die übergeordnete Seite der Live Copy-Seite gilt.
* **[Systemstandard](live-copy-sync-config.md#setting-the-system-default-rollout-configuration):** Wenn die Rollout-Konfiguration der übergeordneten Seite der Live Copy nicht ermittelt werden kann, wird die standardmäßige Rollout-Konfiguration des Systems verwendet.

Beispielsweise verwendet ein Blueprint die Website [WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) als Quellinhalt. Aus dem Blueprint wird eine Website erstellt. Jedes Element der folgenden Liste beschreibt ein anderes Szenario hinsichtlich der Nutzung von Rollout-Konfigurationen:

* Keine der Blueprint-Seiten oder die Live Copy-Seiten sind für die Verwendung einer Rollout-Konfiguration konfiguriert. MSM verwendet die standardmäßige Rollout-Konfiguration des Systems für alle Live Copy-Seiten.
* Die Stammseite der WKND-Site ist mit mehreren Rollout-Konfigurationen konfiguriert. MSM verwendet diese Rollout-Konfigurationen für alle Live Copy-Seiten.
* Die Stammseite der WKND-Site ist mit mehreren Rollout-Konfigurationen konfiguriert und die Stammseite der Live Copy-Site wird mit einem anderen Satz von Rollout-Konfigurationen konfiguriert. MSM verwendet die Rollout-Konfigurationen, die auf der Stammseite der Live Copy-Site konfiguriert sind.

### Festlegen der Rollout-Konfigurationen für eine Live Copy-Seite {#setting-the-rollout-configurations-for-a-live-copy-page}

Konfigurieren Sie eine Live Copy-Seite mit den Rollout-Konfigurationen, die beim Rollout der Quellseite verwendet werden sollen. Untergeordnete Seiten erben diese Konfiguration standardmäßig. Wenn Sie die zu verwendende Rollout-Konfiguration konfigurieren, überschreiben Sie die Konfiguration, die die Live Copy-Seite von der übergeordneten Seite übernimmt.

Sie können die Rollout-Konfigurationen für eine Live Copy-Seite auch konfigurieren, wenn Sie [die Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-page) erstellen.

1. Verwenden Sie die Konsole **Sites** , um die Seite &quot;Live Copy&quot;auszuwählen.
1. Wählen Sie in der Symbolleiste **Eigenschaften** aus.
1. Öffnen Sie die Registerkarte **Live Copy**.

   Im Bereich **Konfigurationen** werden die Rollout-Konfigurationen angezeigt, die die Seite erbt.

   ![Live Copy-Vererbung von der übergeordneten Seite](../assets/live-copy-inherit.png)

1. Passen Sie bei Bedarf die Markierung **Live Copy-Vererbung** an. Wenn diese Option aktiviert ist, ist die Live Copy-Konfiguration für alle untergeordneten Elemente wirksam.

1. Löschen Sie die Eigenschaft **Rollout-Konfiguration aus übergeordnetem Element übernehmen** und wählen Sie dann mindestens eine Rollout-Konfiguration aus der Liste aus.

   Die ausgewählten Rollout-Konfigurationen werden unter der Dropdown-Liste angezeigt.

   ![Überschreiben der Vererbung der Live Copy-Konfiguration](../assets/live-copy-inherit-override.png)

1. Klicken oder tippen Sie auf **Speichern und schließen**.

### Festlegen der Rollout-Konfiguration für eine Blueprint-Seite {#setting-the-rollout-configuration-for-a-blueprint-page}

Konfigurieren Sie eine Blueprint-Seite mit den Rollout-Konfigurationen, die beim Rollout der Blueprint-Seite genutzt werden sollen. 

Beachten Sie, dass die untergeordneten Seiten der Blueprint-Seite die Konfiguration erben. Wenn Sie die zu verwendende Rollout-Konfiguration konfigurieren, überschreiben Sie die Konfiguration, die die Seite von der übergeordneten Seite erbt.

1. Wählen Sie über die **Sites-Konsole** die Stammseite des Blueprints aus.
1. Wählen Sie in der Symbolleiste **Eigenschaften** aus.
1. Öffnen Sie die Registerkarte **Blueprint**.
1. Wählen Sie mit dem Dropdown-Selektor mindestens eine **Rollout-Konfigurationen** aus.
1. Übernehmen Sie die Aktualisierungen mit **Speichern**.

### Festlegen der standardmäßigen Rollout-Konfiguration {#setting-the-system-default-rollout-configuration}

Um eine Rollout-Konfiguration anzugeben, die als Systemstandard verwendet werden soll, konfigurieren Sie den folgenden OSGi-Dienst.

* **Day CQ WCM Live Relationship** Manager mit der Dienst-PID  `com.day.cq.wcm.msm.impl.LiveRelationshipManagerImpl`

Konfigurieren Sie den Dienst entweder mit der [Web-Konsole](/help/implementing/deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) oder einem [Repository-Knoten](/help/implementing/deploying/configuring-osgi.md#osgi-configuration-in-the-repository).

* In der Web-Konsole lautet der Name der zu konfigurierenden Eigenschaft **Standard-Rollout-Konfiguration**.
* Bei Verwendung eines Repository-Knotens lautet der Name der zu konfigurierenden Eigenschaft `liverelationshipmgr.relationsconfig.default`.

Legen Sie diesen Eigenschaftswert auf den Pfad der Rollout-Konfiguration fest, die als Systemstandard genutzt werden soll. Der Standardwert ist `/libs/msm/wcm/rolloutconfigs/default`, was der **Standard-Rollout-Konfiguration** entspricht.
