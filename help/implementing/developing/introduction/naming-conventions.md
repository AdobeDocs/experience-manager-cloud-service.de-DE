---
title: Benennungskonventionen
description: Knoten im Repository unterliegen Benennungskonventionen des Java Content Repository
exl-id: 3c5c39dd-b209-488b-a93e-e840786fe224
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '223'
ht-degree: 94%

---

# Benennungskonventionen{#naming-conventions}

Knoten im Repository unterliegen Benennungskonventionen des Java Content Repository. AEM erfordert jedoch weitere Konventionen für die Namen von Seitenknoten.

## Benennungskonventionen für Seiten {#naming-conventions-for-pages}

Diese Benennungskonventionen werden auf verschiedenen Ebenen implementiert:

* JcrUtil: die AEM-Implementierung der [JCR-Service-Programme](#jcr-utilities).
* PageManager: der [Seitenmanager](#page-manager) stellt Methoden für Operationen auf Seitenebene bereit.
* Innerhalb der AEM-Benutzeroberfläche {#ui-behavior}

### JCR-Service-Programme {#jcr-utilities}

[JcrUtil](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/commons/jcr/JcrUtil.html) ist die AEM-Implementierung der JCR-Service-Programme. Bei der Namensvalidierung sind die Zeichenzuordnungen, die diese Implementierung steuert, und die folgenden Validierungen von besonderem Interesse:

* `isValidName`
   * Stellt sicher, dass der Name nicht leer ist und nur gültige Zeichen enthält.
   * Kann verwendet werden, um zu prüfen, ob ein vorgeschlagener Name gültig ist.
* `createValidName`
   * Erstellt eine gültige Beschriftung aus einer beliebigen Zeichenfolge.
   * Diese Funktion kann verwendet werden, um einen Namen aus einem Titel zu erstellen.

### Seiten-Manager {#page-manager}

[PageManager](https://docs.adobe.com/content/help/en/experience-manager-cloud-service-javadoc/com/day/cq/wcm/api/PageManager.html) stellt basierend auf [JCRUtil](#jcr-utilities) Methoden für Vorgänge auf Seitenebene bereit.

### Verhalten der AEM-Benutzeroberfläche {#ui-behavior}

Beim Verwalten von Inhalten wird die AEM-Benutzeroberfläche wie folgt verwendet:

* Validiert den Namen entsprechend der Einschränkungen, die PageManager vorgibt, wenn entweder:
   * ein Seitentitel zum Konvertieren in den Knotennamen angegeben ist
   * ein expliziter Knotenname angegeben ist
