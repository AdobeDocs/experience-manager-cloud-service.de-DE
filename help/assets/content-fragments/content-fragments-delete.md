---
title: Inhaltsfragmente – Überlegungen zum Löschen (Assets – Inhaltsfragmente)
description: Lesen Sie diese wichtigen Überlegungen, bevor Sie Ihre Richtlinien zum Löschen von Inhaltsfragmenten in AEM definieren. Inhaltsfragmente sind ein leistungsstarkes Tool für die Bereitstellung von Headless-Inhalten. Die Auswirkungen des Löschens müssen sorgfältig berücksichtigt werden.
exl-id: 69c08f2f-4d51-4aea-957e-ee81c4604377
source-git-commit: 5c59189abf809293a319d6bce4ef7389c2451f92
workflow-type: ht
source-wordcount: '472'
ht-degree: 100%

---

# Inhaltsfragmente – Überlegungen zum Löschen {#content-fragments-delete-considerations}

Lesen Sie diese wichtigen Überlegungen, bevor Sie Ihre Richtlinien zum Löschen von Inhaltsfragmenten in AEM definieren. Inhaltsfragmente sind ein leistungsstarkes Tool für die Bereitstellung von Headless-Inhalten. Die Auswirkungen des Löschens müssen sorgfältig berücksichtigt werden.

## Berechtigungen – Löschen oder nicht löschen {#permissions-delete-or-not-delete}

Die Möglichkeit, Inhalt zu löschen, ist wirkungsvoll, muss aber mit Bedacht verwendet werden, da viele Branchen die Erteilung dieser Berechtigungen einschränken und kontrollieren müssen.

In Bezug auf die Berechtigung zum Löschen müssen Inhaltsfragmente aus zwei Perspektiven betrachtet werden:

1. **Das Inhaltsfragment als einzelne Entität.**

   * **Nutzungsszenario:** Ein Benutzer, der ein Inhaltsfragment bearbeiten oder aktualisieren und **ein ganzes Fragment löschen muss**.
   * **Berechtigungen:** Die Berechtigung zum Löschen kann über die Benutzer- und/oder Gruppenverwaltung zugewiesen werden. <!-- The [Delete](/help/sites-administering/security.md#actions) permission can be [assigned through User and/or Group Management](/help/sites-administering/security.md#managing-permissions). -->

2. **Die verschiedenen Unterentitäten, die ein Inhaltsfragment bilden. Z. B. Varianten, Unterknoten.**

   Die grundlegende Funktionsweise des Inhaltsfragment-Editors erfordert, dass solche temporären Unterelemente gelöscht werden können. Beispielsweise wenn Varianten bearbeitet oder Metadaten oder verknüpfte Inhalte verwaltet werden.

   * **Nutzungsszenario:** Ein Benutzer, der ein Inhaltsfragment bearbeiten oder aktualisieren muss, **aber kein ganzes Fragment löschen darf**.
   * **Berechtigungen:** Siehe [Nur für Editor-Funktionen erforderliche Berechtigungen](#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Wenn ein Benutzer keine Berechtigungen zum Löschen besitzt, wird der Inhaltsfragmente-Editor im *schreibgeschützten* Modus geöffnet. <!-- When a user does not have any [Delete](/help/sites-administering/security.md#actions) permissions, the Content Fragment editor operates in *read-only* mode. -->

>[!NOTE]
>
>Siehe auch „Prüfen von Benutzerverwaltungsvorgängen in AEM“. <!-- See also [How to Audit User Management Operations in AEM](/help/sites-administering/audit-user-management-operations.md). -->

## Nur für Editor-Funktionen erforderliche Berechtigungen {#permissions-required-for-editor-functionality-only}

Benutzer, die ein Fragment bearbeiten oder aktualisieren müssen, **aber keine kompletten Fragmente löschen dürfen**, benötigen bestimmte Berechtigungen, da die grundlegende Funktionsweise des Inhaltsfragmente-Editors erfordert, dass diese temporären Unterelemente gelöscht werden können.

Beispielsweise wenn Varianten bearbeitet oder Metadaten oder verknüpfte Inhalte verwaltet werden.

>[!NOTE]
>
>Die zum Bearbeiten oder Aktualisieren eines Inhaltsfragments benötigten Rechte zum Löschen erhalten sie mit der Löschberechtigung, die über die Benutzer- und/oder Gruppenverwaltung zugewiesen wird. <!-- The delete permissions, required to edit/update a Content Fragment, are included in the Delete permission [assigned through User and/or Group Management](/help/sites-administering/security.md#managing-permissions). -->

Die zum Bearbeiten oder Aktualisieren eines Fragments benötigten Rechte müssen auf den Knoten, der das Fragment enthält, oder einen entsprechenden übergeordneten Knoten angewendet werden (auf allen Ebenen unter `/content/dam`). Wenn sie einem übergeordneten Knoten zugewiesen sind, werden die Berechtigungen auf alle Knoten in diesem Zweig angewendet.

Beispiel: Ein Ordner, der alle Inhaltsfragmente enthält, z. B.:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Die Berechtigungen können auch auf `/content/dam` festgelegt werden, weil hier alle Inhaltsfragmente gespeichert werden.
>
>Allerdings wird die Löschberechtigung dadurch auch für *alle* anderen Asset-Typen gewährt.

Die Berechtigungsvoraussetzungen, die es bestimmten Benutzenden und/oder einer bestimmten Gruppe gestattet, ein Inhaltsfragment zu bearbeiten/zu aktualisieren, sind:

>[!NOTE]
>
>Diese Liste zeigt alle erforderlichen Berechtigungen, nicht nur die Berechtigungen zum Löschen.

* Für die Inhaltsfragmentknoten oder -ordner:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Für den `jcr:content`-Knoten aller Inhaltsfragmente:

   * `jcr:addChildNodes`, `jcr:modifyProperties` und `jcr:removeChildNodes`

* Für alle Knoten unter `jcr:content` aller Inhaltsfragmente:

   * `jcr:addChildNodes`, `jcr:modifyProperties` und `jcr:removeChildNodes`, `jcr:removeNode`

<!-- There is no CRXDE Lite -->

<!--
These `remove` privileges must be [administered using Access Control Lists, within CRXDE Lite](/help/sites-administering/user-group-ac-admin.md#access-right-management). 

The `add` and `modify` privileges can also be administered in CRXDE Lite, or using the User Management console.

For example, the definition of the `remove` privileges for a group `content-authors-no-delete`:

![Remove privileges](assets/cf-delete-03.png)
-->
