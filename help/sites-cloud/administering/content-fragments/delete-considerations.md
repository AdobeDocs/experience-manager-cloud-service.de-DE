---
title: Inhaltsfragmente – Überlegungen zum Löschen
description: Lesen Sie diese wichtigen Überlegungen, bevor Sie Ihre Richtlinien zum Löschen von Inhaltsfragmenten in AEM definieren. Inhaltsfragmente sind ein leistungsstarkes Tool für die Bereitstellung von Headless-Inhalten. Die Auswirkungen des Löschens müssen sorgfältig berücksichtigt werden.
feature: Content Fragments
role: User, Developer
exl-id: d1726bff-3aa8-4758-bee7-0cacea1f660a
solution: Experience Manager Sites
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '450'
ht-degree: 100%

---

# Überlegungen zum Löschen von Inhaltsfragmenten {#delete-considerations-content-fragments}

Lesen Sie diese wichtigen Überlegungen, bevor Sie Ihre Löschrichtlinien für Inhaltsfragmente in AEM definieren. Inhaltsfragmente sind ein leistungsstarkes Tool für die Bereitstellung von Headless-Inhalten. Die Auswirkungen des Löschens müssen sorgfältig berücksichtigt werden.

## Berechtigungen – Löschen oder nicht löschen {#permissions-delete-or-not-delete}

Die Möglichkeit, Inhalt zu löschen, ist wirkungsvoll, muss aber mit Bedacht verwendet werden, da viele Branchen die Erteilung dieser Berechtigungen einschränken und kontrollieren müssen.

In Bezug auf die Berechtigung zum Löschen müssen Inhaltsfragmente aus zwei Perspektiven betrachtet werden:

1. **Das Inhaltsfragment als einzelne Entität.**

   * **Nutzungsszenario:** Benutzende, die ein Inhaltsfragment bearbeiten oder aktualisieren müssen **und ein ganzes Fragment löschen müssen**.
   * **Berechtigungen**: Die Berechtigung zum Löschen kann über die Benutzer- und/oder Gruppenverwaltung zugewiesen werden.

2. **Die verschiedenen Unterentitäten, die ein Inhaltsfragment bilden, z. B. Varianten, Unterknoten.**

   Die grundlegende Funktionsweise des Inhaltsfragmenteditors erfordert, dass solche temporären Unterelemente gelöscht werden können. Beispielsweise, wenn Varianten bearbeitet oder Metadaten oder verknüpfte Inhalte verwaltet werden.

   * **Nutzungsszenario**: Benutzende, die ein Inhaltsfragment bearbeiten oder aktualisieren müssen, **aber kein ganzes Fragment löschen können**.
   * **Berechtigungen**: Siehe [Nur für Editor-Funktionen erforderliche Berechtigungen](#permissions-required-for-editor-functionality-only).

>[!NOTE]
>
>Siehe auch „Prüfen von Benutzerverwaltungsvorgängen in AEM“. 

## Nur für Editor-Funktionen erforderliche Berechtigungen {#permissions-required-for-editor-functionality-only}

Benutzenden, die ein Inhaltsfragment bearbeiten/aktualisieren müssen, **ohne dass sie ein ganzes Fragment löschen können**, müssen spezifische Berechtigungen zugewiesen werden, da für den grundlegenden Vorgang des Inhaltsfragmenteditors das Löschen von Übergangsunterelementen erforderlich ist.

Beispielsweise, wenn Varianten bearbeitet oder Metadaten oder verknüpfte Inhalte verwaltet werden.

>[!NOTE]
>
>Die zum Bearbeiten oder Aktualisieren eines Inhaltsfragments benötigten Rechte zum Löschen sind Teil der Löschberechtigung, die über die Benutzer- und/oder Gruppenverwaltung zugewiesen wird.

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

   * `jcr:addChildNodes`, `jcr:modifyProperties`, und `jcr:removeChildNodes`

* Für alle Knoten unter `jcr:content` aller Inhaltsfragmente:

   * `jcr:addChildNodes`, `jcr:modifyProperties`, `jcr:removeChildNodes` und `jcr:removeNode`
