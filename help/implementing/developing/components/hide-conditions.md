---
title: 'Verwenden von Bedingungen zum Ausblenden '
description: Bedingungen zum Ausblenden können verwendet werden, um festzustellen, ob eine Komponentenressource gerendert wird.
exl-id: 2a96f246-fb0f-4298-899e-ebbf9fc1c96f
source-git-commit: ac64ca485391d843c0ebefcf86e80b4015b72b2f
workflow-type: tm+mt
source-wordcount: '614'
ht-degree: 97%

---

# Verwenden von Bedingungen zum Ausblenden   {#using-hide-conditions}

Bedingungen zum Ausblenden können verwendet werden, um festzustellen, ob eine Komponentenressource gerendert wird. Etwa wenn ein Vorlagenautor die Kernkomponente [Listenkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/list.html) im [Vorlageneditor](/help/sites-cloud/authoring/features/templates.md) konfiguriert und beschließt, die Optionen zum Erstellen der Liste auf Basis untergeordneter Seiten zu deaktivieren. Durch das Deaktivieren dieser Option im Designdialogfeld wird eine Eigenschaft so festgelegt, dass beim Rendern der Listenkomponente die Bedingung zum Ausblenden ausgewertet und die Option zum Anzeigen untergeordneter Seiten nicht angezeigt wird.

## Überblick {#overview}

Dialogfelder können aufgrund der zahlreichen Optionen sehr komplex für die Benutzer sein, die möglicherweise nur einen kleinen Teil der ihnen zur Verfügung stehenden Optionen nutzen. Dies kann dazu führen, dass die Benutzeroberfläche unübersichtlich wird.

Durch die Verwendung von Bedingungen zum Ausblenden haben Administratoren, Entwickler und Superuser die Möglichkeit, Ressourcen anhand von Regeln auszublenden. Mit dieser Funktion können sie entscheiden, welche Ressourcen angezeigt werden sollen, wenn ein Autor Inhalte bearbeitet.

>[!NOTE]
>
>Das Ausblenden einer Ressource auf Grundlage eines Ausdrucks ersetzt nicht die ACL-Berechtigungen. Der Inhalt bleibt bearbeitbar, wird aber einfach nicht angezeigt.

## Implementierung und Nutzungsdetails   {#implementation-and-usage-details}

`com.adobe.granite.ui.components.FilteringResourceWrapper` ist verantwortlich für das Filtern der Ressourcen basierend auf dem Vorhandensein und dem Wert der Eigenschaft `granite:hide` für das zu filternde Feld. Die Implementierung `/libs/cq/gui/components/authoring/dialog/dialog.jsp` umfasst eine Instanz von `FilteringResourceWrapper.`

Die Implementierung greift auf die [ELResolver-API](https://helpx.adobe.com/de/experience-manager/6-5/sites/developing/using/reference-materials/granite-ui/api/jcr_root/libs/granite/ui/docs/server/el.html) von Granite zurück und fügt über den ExpressionCustomizer eine benutzerdefinierte `cqDesign`-Variable hinzu.

Im Folgenden sind einige Beispiele für Bedingungen zum Ausblenden für einen Design-Knoten aufgeführt, die sich entweder unter `etc/design` befinden oder als Inhaltsrichtlinie vorliegen.

```
${cqDesign.myProperty}
${!cqDesign.myProperty}
${cqDesign.myProperty == 'someText'}
${cqDesign.myProperty != 'someText'}
${cqDesign.myProperty == true}
${cqDesign.myProperty == true}
${cqDesign.property1 == 'someText' && cqDesign.property2 || cqDesign.property3 != 1 || header.myHeader}
```

Beachten Sie beim Definieren Ihrer Bedingung zum Ausblenden Folgendes:

* Damit sie gültig ist, sollte der Bereich, in dem sich die Eigenschaft befindet, ausgedrückt werden (beispielsweise `cqDesign.myProperty`).
* Werte sind schreibgeschützt.
* Funktionen (falls erforderlich) sollten auf eine bestimmte, vom Service vorgegebene Auswahl beschränkt sein.

## Beispiel {#example}

Beispiele für Bedingungen zum Ausblenden finden sich überall in AEM und insbesondere in den [Kernkomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=de). Betrachten Sie beispielsweise die [Listenkernkomponente](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/list.html), die im [WKND-Tutorial](/help/implementing/developing/introduction/develop-wknd-tutorial.md) implementiert ist.

[Mit dem Vorlageneditor](/help/sites-cloud/authoring/features/templates.md) kann der Vorlagenautor im Design-Dialogfeld festlegen, welche Optionen der Listenkomponente dem Seitenautor zur Verfügung stehen. Optionen wie die, ob die Liste eine statische Liste, eine Liste mit untergeordneten Seiten, eine Liste getaggter Seiten usw. sein darf, können aktiviert oder deaktiviert werden.

Wenn Vorlagenautoren die Option für die untergeordneten Seiten deaktivieren, wird eine Designeigenschaft festgelegt und eine Bedingung zum Ausblenden dagegen ausgewertet, was dazu führt, dass die Option für Seitenautoren nicht gerendert wird.

1. Standardmäßig können Seitenautoren die Listenkernkomponente verwenden, um eine Liste mit untergeordneten Seiten zu erstellen, indem sie die Option **Untergeordnete Seiten** auswählen.

   ![Einstellungen der Listenkomponente](assets/hide-conditions-list-settings.png)

1. Im Design-Dialogfeld der Listenkomponente können Vorlagenautoren die Option **Untergeordnete Elemente deaktivieren** auswählen, um zu verhindern, dass Seitenautoren eine Liste mit untergeordneten Seiten angezeigt wird.

   ![Design-Dialogfeld der Listenkomponente](assets/hide-conditions-list-design.png)

1. Ein Richtlinienknoten wird unter `/conf/wknd/settings/wcm/policies/wknd/components/list` erstellt, wobei die Eigenschaft `disableChildren` auf `true` festgelegt wird.

   ![Knotenstruktur der Bedingung zum Ausblenden](assets/hide-conditions-node-structure.png)

1. Die Bedingung zum Ausblenden wird als Wert der Eigenschaft `granite:hide` des Dialogfeldeigenschafts-Knotens `/libs/core/wcm/components/list/v2/list/cq:dialog/content/items/tabs/items/listSettings/items/columns/items/column/items/listFrom/items/children` definiert.

   ![Auswertung der Bedingung zum Ausblenden](assets/hide-conditions-evaluation.png)

1. Der Wert von `disableChildren` wird aus der Design-Konfiguration gezogen und der Ausdruck `${cqDesign.disableChildren}` wird als `false` ausgewertet, was bedeutet, dass die Option nicht als Teil der Komponente gerendert wird.

1. Die Option **Untergeordnete Seiten** wird für Seitenautoren bei Verwendung der Listenkomponente nicht mehr gerendert.

   ![Listenkomponente mit Option für untergeordnete Elemente deaktiviert](assets/hide-conditions-child-disabled.png)
