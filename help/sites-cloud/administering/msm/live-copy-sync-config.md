---
title: Konfigurieren der Synchronisierung von Live Copies
description: Erfahren Sie mehr über die leistungsstarken Live Copy-Synchronisierungsoptionen und wie Sie diese für Ihre Projekt-Anforderungen konfigurieren und anpassen können.
feature: Multi-Site-Manager
role: 'Administrator  '
translation-type: tm+mt
source-git-commit: 0f2b7176b44bb79bdcd1cecf6debf05bd652a1a1
workflow-type: tm+mt
source-wordcount: '2358'
ht-degree: 33%

---


# Konfigurieren der Synchronisierung von Live Copies {#configuring-live-copy-synchronization}

Adobe Experience Manager bietet eine Reihe von Synchronisierungskonfigurationen sofort zur Verfügung. Vor der Verwendung von Live Copies sollten Sie Folgendes berücksichtigen, um zu definieren, wie und wann Live Copies mit ihrem Quellinhalt synchronisiert werden.

1. Entscheiden Sie, ob bestehende Rollout-Konfigurationen Ihren Anforderungen entsprechen.
1. Wenn vorhandene Rollout-Konfigurationen dies nicht tun, entscheiden Sie, ob Sie Ihre eigenen erstellen müssen.
1. Geben Sie die für Ihre Live Copies zu verwendenden Rollout-Konfigurationen an.

## Installierte und benutzerdefinierte Rollout-Konfigurationen {#installed-and-custom-rollout-configurations}

In diesem Abschnitt finden Sie Informationen zu den installierten Rollout-Konfigurationen und den von ihnen verwendeten Synchronisierungsaktionen. Außerdem erfahren Sie, wie Sie bei Bedarf benutzerdefinierte Konfigurationen erstellen.

>[!CAUTION]
>
>Das Aktualisieren oder Ändern einer vordefinierten Rollout-Konfiguration wird **nicht** empfohlen. Wenn eine benutzerdefinierte Live-Aktion erforderlich ist, sollte sie in einer benutzerdefinierten Rollout-Konfiguration hinzugefügt werden.

### Rollout-Auslöser {#rollout-triggers}

Jede Rollout-Konfiguration nutzt einen Rollout-Auslöser, der den Rollout auslöst. Rollout-Konfigurationen können einen der folgenden Auslöser verwenden:

* **Bei Rollout**: Der  **** Befehl &quot;Rolloutu&quot;wird auf der blauen Druckseite oder auf der Seite &quot;Live Copy&quot;der Befehl &quot; **** Synchronisieren&quot;verwendet.
* **Bei Modifizierung**: Die Quellseite wird bearbeitet.
* **Bei Aktivierung**: Die Quellseite wird aktiviert.
* **Bei Deaktivierung**: Die Quellseite wird deaktiviert.

>[!NOTE]
>
>Die Verwendung des Triggers **Bei Änderung** kann sich auf die Leistung auswirken. Weitere Informationen finden Sie in den [Best Practices für MSM](best-practices.md#onmodify).

### Rollout-Konfigurationen {#rollout-configurations}

In der folgenden Tabelle werden die Rollout-Konfigurationen Liste, die standardmäßig mit AEM bereitgestellt werden. Auslöser und Synchronisierungsaktionen jeder Rollout-Konfigurationen werden ebenfalls angegeben. Wenn die Aktionen der installierten Rollout-Konfigurationen Ihre Anforderungen nicht erfüllen, können Sie [eine neue Rollout-Konfiguration erstellen](#creating-a-rollout-configuration).

| Name | Beschreibung | Auslöser | [Synchronisierungsaktionen](#synchronization-actions) |
|---|---|---|---|
| Standard-Rollout-Konfiguration | Standard-Rollout-Konfiguration, die den Start des Rollout-Prozesses bei Rollout-Auslösern ermöglicht und Aktionen ausführt: Erstellen, Aktualisieren, Löschen von Inhalten und Sortierung untergeordneter Knoten | Bei Rollout | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`referencesUpdate`<br>`productUpdate`<br>`orderChildren` |
| Bei Blueprint-Aktivierung aktivieren | Veröffentlicht die Live Copy, wenn die Quelle veröffentlicht wird | Bei Aktivierung | `targetActivate` |
| Bei Blueprint-Deaktivierung deaktivieren | Deaktiviert die Live Copy, wenn die Quelle deaktiviert wird | Bei Deaktivierung | `targetDeactivate` |
| Push bei Bearbeitung | Verschiebt den Inhalt auf die Live Copy, wenn die Quelle geändert wird. Verwenden Sie diese Rollout-Konfiguration sparsam, da der Trigger &quot;Bei Änderung&quot;verwendet wird.<br> | Bei Modifizierung | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`referencesUpdate`<br>`orderChildren` |
| Push bei Bearbeitung (leicht) | Verschiebt Inhalte beim Ändern der Blueprint-Seite in die Live Copy, ohne Referenzen zu aktualisieren (z. B. für flache Kopien)<br>Verwenden Sie diese Rollout-Konfiguration sparsam, da sie den On-Modification-Trigger verwendet. | Bei Modifizierung | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`orderChildren` |
| Launch bewerben | Standard-Rollout-Konfigurationen zur Veröffentlichung von Startseiten. | Bei Rollout | `contentUpdate`<br>`contentCopy`<br>`contentDelete`<br>`referencesUpdate`<br>`orderChildren`<br>`markLiveRelationship` |

### Synchronisierungsaktionen {#synchronization-actions}

In der folgenden Tabelle werden die Synchronisierungsaktionen Liste, die standardmäßig mit AEM bereitgestellt werden.

<!--If the installed actions do not meet your requirements, you can [Create a New Synchronization Action](/help/sites-developing/extending-msm.md#creating-a-new-synchronization-action).-->

| Aktionsname | Beschreibung | Eigenschaften |
|---|---|---|
| `contentCopy` | Wenn auf der Live Copy keine Knoten der Quelle vorhanden sind, kopiert diese Aktion die Knoten in die Live Copy. [Konfigurieren Sie den  **CQ MSM Content Copy** ](#excluding-properties-and-node-types-from-synchronization) ActionService, um die auszuschließenden Node-Typen, Absätze und Seiteneigenschaften anzugeben. |  |
| `contentDelete` | Diese Aktion löscht Knoten der Live Copy, die nicht in der Quelle vorhanden sind. [Konfigurieren Sie den  **CQ MSM Content Delete** ](#excluding-properties-and-node-types-from-synchronization) ActionService, um die auszuschließenden Node-Typen, Absatz-Elemente und Seiteneigenschaften anzugeben. |  |
| `contentUpdate` | Diese Aktion aktualisiert den Live Copy-Inhalt mit den Änderungen aus der Quelle. [Konfigurieren Sie den  **CQ MSM Content Update** ](#excluding-properties-and-node-types-from-synchronization) ActionService, um die auszuschließenden Node-, Absatz- und Seiteneigenschaften anzugeben. |  |
| `editProperties` | Diese Aktion bearbeitet Eigenschaften der Live Copy. Die `editMap`-Eigenschaft bestimmt, welche Eigenschaften und deren Wert bearbeitet werden. Der Wert der Eigenschaft `editMap` muss das folgende Format verwenden:<br>`[property_name_n]#[current_value]#[new_value]`<br>`current_value` und `new_value` sind reguläre Ausdruck und `n` ist eine inkrementierte Ganzzahl.<br>Betrachten Sie zum Beispiel den folgenden Wert für  `editMap`:<br>`sling:resourceType#/(contentpage` ‖ `homepage)#/mobilecontentpage,cq:template#/contentpage#/mobilecontentpage`<br>Dieser Wert bearbeitet die Eigenschaften der Live Copy-Knoten wie folgt:<br>Die  `sling:resourceType` Eigenschaften, die entweder auf  `contentpage` oder auf  `homepage` festgelegt  `mobilecontentpage`sind.<br>Die  `cq:template` Eigenschaften, auf die festgelegt  `contentpage` sind, sind auf  `mobilecontentpage`. | `editMap: (String)` identifiziert die Eigenschaft, den aktuellen Wert und den neuen Wert. Weitere Informationen finden Sie in der Beschreibung. |
| `notify` | Diese Aktion sendet ein Ereignis der Seite, bei dem das Rollout der Seite erfolgt ist. Um Benachrichtigungen zu erhalten, müssen Benutzer zunächst Rollout-Ereignisse abonnieren. |  |
| `orderChildren` | Diese Aktion ordnet die untergeordneten Knoten basierend auf der Reihenfolge auf dem Entwurf an. |  |
| `referencesUpdate` | Durch diese Synchronisierungsaktion werden Verweise auf die Live Copy aktualisiert.<br>Es sucht nach Pfaden auf den Live Copy-Seiten, die auf eine Ressource im Entwurf verweisen. Bei der Suche wird der Pfad aktualisiert, um auf die zugehörige Ressource in der Live Copy zu verweisen. Verweise, die Ziele außerhalb des Blueprints aufweisen, werden nicht geändert. <br>[Konfigurieren Sie den  **CQ MSM References Update** ](#excluding-properties-and-node-types-from-synchronization) ActionService, um die auszuschließenden Node-Typen, Absatz-Elemente und Seiteneigenschaften anzugeben. |  |
| `targetVersion` | Diese Aktion erstellt eine Version der Live Copy.<br>Diese Aktion muss die einzige Synchronisierungsaktion in einer Rollout-Konfiguration sein. |  |
| `targetActivate` | Diese Aktion aktiviert die Live Copy.<br>Diese Aktion muss die einzige Synchronisierungsaktion in einer Rollout-Konfiguration sein. |  |
| `targetDeactivate` | Diese Aktion deaktiviert die Live Copy.<br>Diese Aktion muss die einzige Synchronisierungsaktion in einer Rollout-Konfiguration sein. |  |
| `workflow` | Diese Aktion Beginn den Workflow, der von der Seiteneigenschaft definiert wird (nur für Seiten), und nimmt die Live Copy als Payload auf.<br>Der Pfad der Zielgruppe ist der Pfad des Modellknotens. | `target: (String)` ist der Pfad zum Workflow-Modell. |
| `mandatory` | Durch diese Aktion wird die Berechtigung mehrerer ACLs auf der Seite &quot;Live Copy&quot;auf schreibgeschützt für eine bestimmte Benutzergruppe eingestellt. Die folgenden ACLs sind konfiguriert:<br>`ActionSet.ACTION_NAME_REMOVE`<br>`ActionSet.ACTION_NAME_SET_PROPERTY`<br>`ActionSet.ACTION_NAME_ACL_MODIFY`<br>Verwenden Sie diese Aktion nur für Seiten. | `target: (String)` ist die ID der Gruppe, für die Sie Berechtigungen festlegen. |
| `mandatoryContent` | Durch diese Aktion wird die Berechtigung mehrerer ACLs auf der Seite &quot;Live Copy&quot;auf schreibgeschützt für eine bestimmte Benutzergruppe eingestellt. Die folgenden ACLs sind konfiguriert:<br>`ActionSet.ACTION_NAME_SET_PROPERTY`<br>`ActionSet.ACTION_NAME_ACL_MODIFY`<br>Verwenden Sie diese Aktion nur für Seiten. | `target: (String)` ist die ID der Gruppe, für die Sie Berechtigungen festlegen. |
| `mandatoryStructure` | Durch diese Aktion wird die Berechtigung von `ActionSet.ACTION_NAME_REMOVE` ACL auf der Seite &quot;Live Copy&quot;auf schreibgeschützt für eine bestimmte Benutzergruppe eingestellt.<br>Nutzen Sie diese Aktion nur für Seiten. | `target: (String)` ist die ID der Gruppe, für die Sie Berechtigungen festlegen. |
| `VersionCopyAction` | Wenn die Entwurfs-/Quellseite mindestens einmal veröffentlicht wurde, wird mit dieser Aktion eine Live Copy-Seite mit der veröffentlichten Version erstellt. Hinweis: Diese Aktion ist nur zum Erstellen einer Live Copy-Seite auf der Grundlage einer veröffentlichten Quellseite verfügbar, nicht zum Aktualisieren einer vorhandenen Live Copy-Seite. |  |
| `PageMoveAction` | Das `PageMoveAction`-Zeichen wird angewendet, wenn eine Seite in den Blueprint verschoben wurde.<br>Die Aktion kopiert statt die (zugehörige) Live Copy-Seite vom Speicherort zu verschieben, bevor der Wechsel zum Speicherort nach dem Vorgang erfolgt.<br>Die Seite &quot;Live Copy&quot; `PageMoveAction` ändert sich nicht am Speicherort vor dem Verschieben. Bei aufeinander folgenden Rollout-Konfigurationen hat es daher den Status einer Live-Beziehung ohne Vorlage.<br>[**** Konfigurieren Sie den Dienst „CQ MSM Page Move Action“](#excluding-properties-and-node-types-from-synchronization), um die Knotentypen, Absatzelemente und Seiteneigenschaften festzulegen, die ausgeschlossen werden sollen.<br>Diese Aktion muss die einzige Synchronisierungsaktion in einer Rollout-Konfiguration sein. | Setzen Sie `prop_referenceUpdate: (Boolean)` auf true (Standard), um Verweise zu aktualisieren. |
| `markLiveRelationship` | Diese Aktion gibt an, dass eine Live-Beziehung für neu erstellte Inhalte vorhanden ist. |  |

<!--
### Creating a Rollout Configuration {#creating-a-rollout-configuration}

You can [create a rollout configuration](/help/sites-developing/extending-msm.md#creating-a-new-rollout-configuration) when the installed rollout configurations do not meet your application requirements by performing the following steps.

1. [Create the rollout configuration](/help/sites-developing/extending-msm.md#create-the-rollout-configuration).
1. [Add synchronization actions to the rollout configuration](/help/sites-developing/extending-msm.md#add-synchronization-actions-to-the-rollout-configuration).

The new rollout configuration is then available to you when configuring rollout configurations on a blueprint or Live Copy page.
-->

### Ausschließen von Eigenschaften und Knotentypen von der Synchronisierung {#excluding-properties-and-node-types-from-synchronization}

Sie können mehrere OSGi-Dienste konfigurieren, die die entsprechenden Synchronisierungsaktionen unterstützen, sodass sie sich nicht auf bestimmte Knotentypen und Eigenschaften auswirken. Beispielsweise sollten viele Eigenschaften und Unterknoten im Zusammenhang mit der internen Funktionsweise von AEM nicht in eine Live Copy einbezogen werden. Es sollten nur die Inhalte kopiert werden, die für den Benutzer der Seite relevant sind.

Bei der Arbeit mit AEM gibt es verschiedene Methoden, die Konfigurationseinstellungen für solche Dienste zu verwalten. Weitere Informationen und empfohlene Vorgehensweisen finden Sie unter [Konfigurieren von OSGi](/help/implementing/deploying/configuring-osgi.md).

In der folgenden Tabelle sind die Synchronisierungsaktionen aufgeführt, von denen Sie Knoten ausschließen können. Die Tabelle führt die Namen der Services an, die mit der Web-Konsole und der PID mit Repository-Knoten konfiguriert werden.

| Synchronisierungsaktion | Dienstname in der Web-Konsole | Dienst-PID |
|---|---|---|
| `contentCopy` | CQ MSM Content Copy Action | `com.day.cq.wcm.msm.impl.actions.ContentCopyActionFactory` |
| `contentDelete` | CQ MSM Content Delete Action | `com.day.cq.wcm.msm.impl.actions.ContentDeleteActionFactory` |
| `contentUpdate` | CQ MSM Content Update Action | `com.day.cq.wcm.msm.impl.actions.ContentUpdateActionFactory` |
| `PageMoveAction` | CQ MSM Page Move Action | `com.day.cq.wcm.msm.impl.actions.PageMoveActionFactory` |
| `referencesUpdate` | Aktualisierungsaktion für CQ MSM-Referenzen | `com.day.cq.wcm.msm.impl.actions.ReferencesUpdateActionFactory` |

In der folgenden Tabelle werden die Eigenschaften beschrieben, die Sie konfigurieren können:

| Webkonsole-Eigenschaft | OSGi-Eigenschaft | Beschreibung |
|---|---|---|
| Ausgeschlossene Knotentypen | `cq.wcm.msm.action.excludednodetypes` | Ein regulärer Ausdruck, der mit den Node-Typen übereinstimmt, die von der Synchronisierungsaktion ausgeschlossen werden sollen |
| Ausgeschlossene Absatzelemente | `cq.wcm.msm.action.excludedparagraphitems` | Ein regulärer Ausdruck, der mit den von der Synchronisierungsaktion auszuschließenden Absatzelementen übereinstimmt |
| Ausgeschlossene Seiteneigenschaften | `cq.wcm.msm.action.excludedprops` | Ein regulärer Ausdruck, der mit den Seiteneigenschaften übereinstimmt, die von der Synchronisierungsaktion ausgeschlossen werden sollen |
| Ignorierte Mixin-NodeTypes | `cq.wcm.msm.action.ignoredMixin` | Ein regulärer Ausdruck, der mit den Namen der Mixin-Node-Typen übereinstimmt, die von der Synchronisierungsaktion ausgeschlossen werden (nur für `contentUpdate` verfügbar) |

#### CQ MSM Content Update Action – Ausschlüsse {#cq-msm-content-update-action-exclusions}

Einige Eigenschaften und Knotentypen sind standardmäßig ausgeschlossen. Sie sind in der OSGi-Konfiguration der Aktion **CQ MSM Content Update Action** unter **Ausgeschlossene Seiteneigenschaften** definiert.

Standardmäßig werden Eigenschaften, die mit den folgenden regulären Ausdrücken übereinstimmen, beim Rollout ausgeschlossen (d. h. nicht aktualisiert):

![Live Copy-Ausschlussregexen](../assets/live-copy-exclude.png)

Sie können die Ausdrücke, die die Ausschlussliste definieren, bei Bedarf ändern.

Wenn Sie beispielsweise möchten, dass die Seite **Title** bei den Änderungen enthalten sein soll, die beim Rollout berücksichtigt werden, entfernen Sie `jcr:title` von den Ausschlüssen, z. B. mit dem regulären Ausdruck:

`jcr:(?!(title)$).*`

### Konfigurieren der Synchronisierung für die Aktualisierung von Verweisen {#configuring-synchronization-for-updating-references}

Sie können mehrere OSGi-Dienste konfigurieren, die die entsprechenden Synchronisierungsaktionen im Zusammenhang mit der Aktualisierung von Verweisen unterstützen.

Bei der Arbeit mit AEM gibt es verschiedene Methoden, die Konfigurationseinstellungen für solche Dienste zu verwalten. Weitere Informationen und empfohlene Vorgehensweisen finden Sie unter [Konfigurieren von OSGi](/help/implementing/deploying/configuring-osgi.md).

In der folgenden Tabelle sind die Synchronisierungsaktionen aufgeführt, für die Sie die Verweisaktualisierung festlegen können. Die Tabelle führt die Namen der Services an, die mit der Web-Konsole und der PID mit Repository-Knoten konfiguriert werden.

| Webkonsole-Eigenschaft | OSGi-Eigenschaft | Beschreibung |
|---|---|---|
| Referenz über verschachtelte LiveCopies aktualisieren | `cq.wcm.msm.impl.action.referencesupdate.prop_updateNested` | Wählen Sie diese Option in der Webkonsole aus oder setzen Sie diese boolesche Eigenschaft mithilfe der Repository-Konfiguration auf `true`, um Verweise auf diese Zielgruppe zu ersetzen, die sich in der Verzweigung der obersten Live Copy befinden. Nur für `referencesUpdate`-Aktion verfügbar. |
| Verweisende Seiten aktualisieren | `cq.wcm.msm.impl.actions.pagemove.prop_referenceUpdate` | Wählen Sie diese Option in der Webkonsole aus oder setzen Sie diese boolesche Eigenschaft mithilfe der Repository-Konfiguration auf `true`, um Verweise zu aktualisieren, damit die Originalseite stattdessen auf die Live Copy-Seite verweist. Nur verfügbar für `PageMoveAction`. |

## Festlegen der zu verwendenden Rollout-Konfigurationen {#specifying-the-rollout-configurations-to-use}

Mit MSM können Sie einen Satz von Rollout-Konfigurationen angeben, die im Allgemeinen verwendet werden. Bei Bedarf können Sie diese bei bestimmten Live Copies überschreiben. MSM bietet mehrere Orte, an denen Sie die zu verwendenden Rollout-Konfigurationen festlegen können. Der Speicherort bestimmt, ob die Konfiguration für eine bestimmte Live Copy gilt.

Die folgende Liste der Stellen, an denen Sie die zu verwendenden Rollout-Konfigurationen angeben können, beschreibt, wie MSM bestimmt, welche Rollout-Konfigurationen für eine Live Copy verwendet werden sollen:

* **[Eigenschaften](live-copy-sync-config.md#setting-the-rollout-configurations-for-a-live-copy-page) der Live Copy-Seite:** Wenn eine Live Copy-Seite für die Verwendung einer oder mehrerer Rollout-Konfigurationen konfiguriert ist, verwendet MSM diese Rollout-Konfigurationen.
* **[Eigenschaften](live-copy-sync-config.md#setting-the-rollout-configuration-for-a-blueprint-page) der Blueprint-Seite:** Wenn eine Live Copy auf einem Entwurf basiert und die Live Copy-Seite nicht mit einer Rollout-Konfiguration konfiguriert ist, wird die mit der Blueprint-Quellseite verknüpfte Rollout-Konfiguration verwendet.
* **Eigenschaften übergeordneter Live Copy-Seiten:** Wenn weder die Live Copy-Seite noch die Blueprint-Quellseite mit einer Rollout-Konfiguration konfiguriert sind, wird die Rollout-Konfiguration verwendet, die für die übergeordnete Seite der Live Copy-Seite gilt.
* **[Systemstandard](live-copy-sync-config.md#setting-the-system-default-rollout-configuration):** Wenn die Rollout-Konfiguration der übergeordneten Seite von Live Copy nicht bestimmt werden kann, wird die standardmäßige Rollout-Konfiguration des Systems verwendet.

Beispielsweise verwendet ein Entwurf die Website [WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) als Quellinhalt. Aus dem Blueprint wird eine Website erstellt. Jedes Element der folgenden Liste beschreibt ein anderes Szenario hinsichtlich der Nutzung von Rollout-Konfigurationen:

* Keine der Musterseiten oder die Live Copy-Seiten sind für die Verwendung einer Rollout-Konfiguration konfiguriert. MSM verwendet die standardmäßige Rollout-Konfiguration des Systems für alle Live Copy-Seiten.
* Die Stammseite der WKND-Site ist mit verschiedenen Rollout-Konfigurationen konfiguriert. MSM verwendet diese Rollout-Konfigurationen für alle Live Copy-Seiten.
* Die Stammseite der WKND-Site wird mit mehreren Rollout-Konfigurationen konfiguriert, und die Stammseite der Live Copy-Site wird mit einem anderen Satz von Rollout-Konfigurationen konfiguriert. MSM verwendet die Rollout-Konfigurationen, die auf der Stammseite der Live Copy-Site konfiguriert sind.

### Festlegen der Rollout-Konfigurationen für eine Live Copy-Seite {#setting-the-rollout-configurations-for-a-live-copy-page}

Konfigurieren Sie eine Live Copy-Seite mit den Rollout-Konfigurationen, die beim Rollout der Quellseite verwendet werden sollen. Untergeordnete Seiten erben diese Konfiguration standardmäßig. Wenn Sie die Rollout-Konfiguration für die Verwendung konfigurieren, überschreiben Sie die Konfiguration, die die Live Copy-Seite von der übergeordneten Seite erbt.

Sie können die Rollout-Konfigurationen für eine Live Copy-Seite auch konfigurieren, wenn Sie [die Live Copy](creating-live-copies.md#creating-a-live-copy-of-a-page) erstellen.

1. Verwenden Sie die Konsole **Sites**, um die Seite &quot;Live Copy&quot;auszuwählen.
1. Wählen Sie in der Symbolleiste **Eigenschaften** aus.
1. Öffnen Sie die Registerkarte **Live Copy**.

   Im Bereich **Konfigurationen** werden die Rollout-Konfigurationen angezeigt, die die Seite erbt.

   ![Live Copy-Vererbung von übergeordneter Seite](../assets/live-copy-inherit.png)

1. Passen Sie bei Bedarf die Markierung **Live Copy-Vererbung** an. Wenn diese Option aktiviert ist, ist die Live Copy-Konfiguration für alle untergeordneten Elemente gültig.

1. Löschen Sie die Eigenschaft **Rollout-Konfiguration aus übergeordnetem Element übernehmen** und wählen Sie dann mindestens eine Rollout-Konfiguration aus der Liste aus.

   Die ausgewählten Rollout-Konfigurationen werden unter der Dropdown-Liste angezeigt.

   ![Live Copy-Konfigurationsvererbung überschreiben](../assets/live-copy-inherit-override.png)

1. Klicken Sie auf oder tippen Sie auf **Speichern &amp; Schließen**.

### Festlegen der Rollout-Konfiguration für eine Blueprint-Seite {#setting-the-rollout-configuration-for-a-blueprint-page}

Konfigurieren Sie eine Blueprint-Seite mit den Rollout-Konfigurationen, die beim Rollout der Blueprint-Seite genutzt werden sollen. 

Beachten Sie, dass die untergeordneten Seiten der Blueprint-Seite die Konfiguration erben. Wenn Sie die zu verwendende Rollout-Konfiguration konfigurieren, überschreiben Sie die Konfiguration, die die Seite von der übergeordneten Seite erbt.

1. Wählen Sie über die **Sites-Konsole** die Stammseite des Blueprints aus.
1. Wählen Sie in der Symbolleiste **Eigenschaften** aus.
1. Öffnen Sie die Registerkarte **Blueprint**.
1. Wählen Sie mit dem Dropdown-Selektor mindestens eine **Rollout-Konfigurationen** aus.
1. Übernehmen Sie die Aktualisierungen mit **Speichern**.

### Festlegen der standardmäßigen Rollout-Konfiguration {#setting-the-system-default-rollout-configuration}

Um eine Rollout-Konfiguration als Systemstandard festzulegen, konfigurieren Sie den folgenden OSGi-Dienst.

* **Day CQ WCM Live Relationship** Manager mit der Dienst-PID  `com.day.cq.wcm.msm.impl.LiveRelationshipManagerImpl`

Konfigurieren Sie den Dienst entweder mit der [Webkonsole](/help/implementing/deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) oder einem [Repository-Knoten](/help/implementing/deploying/configuring-osgi.md#osgi-configuration-in-the-repository).

* In der Webkonsole lautet der Name der zu konfigurierenden Eigenschaft **Standardmäßige Rollout-Konfiguration**.
* Bei Verwendung eines Repository-Knotens lautet der Name der zu konfigurierenden Eigenschaft `liverelationshipmgr.relationsconfig.default`.

Legen Sie diesen Eigenschaftswert auf den Pfad der Rollout-Konfiguration fest, die als Systemstandard genutzt werden soll. Der Standardwert ist `/libs/msm/wcm/rolloutconfigs/default`, d. h. die **Standard-Rollout-Konfiguration**.
