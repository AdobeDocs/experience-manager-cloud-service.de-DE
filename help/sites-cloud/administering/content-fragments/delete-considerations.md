---
title: Inhaltsfragmente – Überlegungen zum Löschen
description: Lesen Sie diese wichtigen Überlegungen, bevor Sie Ihre Richtlinien zum Löschen von Inhaltsfragmenten in AEM definieren. Inhaltsfragmente sind ein leistungsstarkes Tool für die Bereitstellung von Headless-Inhalten. Die Auswirkungen des Löschens müssen sorgfältig berücksichtigt werden.
feature: Content Fragments
role: User, Developer, Architect
source-git-commit: 3d20f4bca566edcdb5f13eab581c33b7f3cf286d
workflow-type: tm+mt
source-wordcount: '452'
ht-degree: 47%

---


# Überlegungen zu Inhaltsfragmenten löschen {#delete-considerations-content-fragments}

Lesen Sie diese wichtigen Überlegungen, bevor Sie Ihre Löschrichtlinien für Inhaltsfragmente in AEM definieren. Inhaltsfragmente sind ein leistungsstarkes Tool für die Bereitstellung von Headless-Inhalten. Die Auswirkungen des Löschens müssen sorgfältig berücksichtigt werden.

## Berechtigungen – Löschen oder nicht löschen {#permissions-delete-or-not-delete}

Die Möglichkeit, Inhalt zu löschen, ist wirkungsvoll, muss aber mit Bedacht verwendet werden, da viele Branchen die Erteilung dieser Berechtigungen einschränken und kontrollieren müssen.

In Bezug auf die Berechtigung zum Löschen müssen Inhaltsfragmente aus zwei Perspektiven betrachtet werden:

1. **Das Inhaltsfragment als einzelne Entität.**

   * **Anwendungsfall**: Ein Benutzer, der ein Inhaltsfragment bearbeiten/aktualisieren muss - **und Löschen eines ganzen Fragments**.
   * **Berechtigungen**: Die Berechtigung zum Löschen kann über die Benutzer- und/oder Gruppenverwaltung zugewiesen werden.

2. **Die mehreren Unterentitäten, aus denen ein Inhaltsfragment besteht, z. B. Varianten, Unterknoten.**

   Für den grundlegenden Vorgang des Inhaltsfragmente-Editors müssen diese temporären Unterelemente gelöscht werden können. Beispielsweise wenn Varianten bearbeitet oder Metadaten oder verknüpfte Inhalte verwaltet werden.

   * **Anwendungsfall**: Ein Benutzer, der ein Inhaltsfragment bearbeiten/aktualisieren muss - **ohne Berechtigung zum Löschen eines ganzen Fragments**.
   * **Berechtigungen:** Siehe [Nur für Editor-Funktionen erforderliche Berechtigungen](#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Siehe auch „Prüfen von Benutzerverwaltungsvorgängen in AEM“. 

## Nur für Editor-Funktionen erforderliche Berechtigungen {#permissions-required-for-editor-functionality-only}

Für Benutzer, die ein Inhaltsfragment bearbeiten/aktualisieren müssen, gilt Folgendes: **ohne dass sie ein ganzes Fragment löschen können** müssen spezifische Berechtigungen zugewiesen werden, da für die grundlegende Funktionsweise des Inhaltsfragment-Editors das Löschen von temporären Unterelementen erforderlich ist.

Beispielsweise wenn Varianten bearbeitet oder Metadaten oder verknüpfte Inhalte verwaltet werden.

>[!NOTE]
>
>Die zum Bearbeiten oder Aktualisieren eines Inhaltsfragments benötigten Rechte zum Löschen erhalten sie mit der Löschberechtigung, die über die Benutzer- und/oder Gruppenverwaltung zugewiesen wird.

Die zum Bearbeiten/Aktualisieren eines Fragments erforderlichen Berechtigungen müssen entweder auf den Knoten, der das Inhaltsfragment enthält, oder auf einen entsprechenden übergeordneten Knoten angewendet werden (auf jeder Ebene unter `/content/dam`). Wenn sie einem übergeordneten Knoten zugewiesen sind, werden die Berechtigungen auf alle Knoten in diesem Zweig angewendet.

Beispiel: ein Ordner, in dem alle Inhaltsfragmente gespeichert werden, z. B.:

* `/content/dam/contentfragments`

>[!CAUTION]
>
>Festlegen von Berechtigungen für `/content/dam` ist auch möglich, da hier alle Inhaltsfragmente gespeichert sind.
>
>Diese Aktion wendet jedoch dieselben Löschberechtigungen auf *all* auch andere Asset-Typen.

Die Berechtigungsvoraussetzung, die es einem bestimmten Benutzer und/oder einer bestimmten Gruppe gestattet, ein Inhaltsfragment zu bearbeiten/zu aktualisieren, ist:

>[!NOTE]
>
>Diese Liste zeigt alle erforderlichen Berechtigungen, nicht nur die Berechtigungen zum Löschen.

* Für die Inhaltsfragmentknoten oder -ordner:

   * `jcr:addChildNodes`, `jcr:modifyProperties`

* Für den `jcr:content`-Knoten aller Inhaltsfragmente:

   * `jcr:addChildNodes`, `jcr:modifyProperties`, und `jcr:removeChildNodes`

* Für alle Knoten unter `jcr:content` aller Inhaltsfragmente:

   * `jcr:addChildNodes`, `jcr:modifyProperties`, und `jcr:removeChildNodes`, `jcr:removeNode`

