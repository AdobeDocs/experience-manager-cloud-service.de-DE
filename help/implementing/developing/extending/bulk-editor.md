---
title: Konfigurieren der Massenbearbeitung von Seiteneigenschaften
description: Erfahren Sie, wie Sie die Massenbearbeitung konfigurieren, damit Sie die Eigenschaften mehrerer Seiten gleichzeitig bearbeiten können.
exl-id: 0d10c6b9-8643-479d-adc1-4066d227e83d
source-git-commit: bc3c054e781789aa2a2b94f77b0616caec15e2ff
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 19%

---

# Konfigurieren der Massenbearbeitung von Seiteneigenschaften {#configuring-bulk-editing-of-page-properties}

[Massenbearbeitung von Seiteneigenschaften](/help/sites-cloud/authoring/fundamentals/page-properties.md#from-the-sites-console-multiple-pages) können Sie die Eigenschaften mehrerer Seiten gleichzeitig bearbeiten.

## Überlegungen {#considerations}

Seiteneigenschaften sind nicht standardmäßig für die Massenbearbeitung aktiviert. Sie müssen explizit aktiviert sein. Beim Definieren der Seiteneigenschaften, die für die Massenbearbeitung verfügbar sein sollen, müssen Sie bestimmte Auswirkungen berücksichtigen, z. B.:

* Bestimmte Felder sind in der Regel eindeutig. Sie müssen entscheiden, ob es sinnvoll ist, diese Felder für die Massenbearbeitung zu aktivieren, wenn ein Wert angewendet wird.
   * Beispielsweise sind Seitentitel fast immer eindeutig.
* Bestimmte Felder können mehrere Werte aufweisen, die beim Rendern eine aussagekräftige Darstellung erfordern.
   * Beispielsweise eine Dropdown-Liste für den Status mit der Bezeichnung **Bereit für Veröffentlichung**. Dies kann mehrere Werte vor der Massenbearbeitung aufweisen, z. B. **ready**, **In-Review**, **in Bearbeitung** usw.

Aufgrund der Möglichkeit mehrerer Werte wird empfohlen, nur die folgenden Feldtypen für die Massenbearbeitung zu aktivieren.

* `/libs/granite/ui/components/foundation/form/textfield`
* `/libs/granite/ui/components/foundation/form/textarea`
* `/libs/granite/ui/components/foundation/form/tagspicker`
* `/libs/granite/ui/components/foundation/form/datepicker`
* `/libs/granite/ui/components/foundation/form/pathbrowser`
* `/libs/granite/ui/components/foundation/form/checkbox`

## Aktivieren eines Felds {#enabling-a-field}

Diese Schritte verwenden die `/apps/core/wcm/components/page/v1/page` aus dem [WKND-Beispielinhalt](/help/implementing/developing/introduction/develop-wknd-tutorial.md) als Beispiel für die Massenbearbeitung eines Felds in einer Entwicklungsumgebung.

1. Öffnen Sie Ihre Seitenkomponente mit CRXDE.
1. Navigieren Sie zum erforderlichen Feld innerhalb der `cq:dialog`-Definition.
1. Definieren Sie die folgende Eigenschaft auf dem Feldknoten:

   * **Name**: `allowBulkEdit`
   * **Typ**: `Boolean`
   * **Wert**: `true`

1. Wählen Sie **Alle speichern**, um ihre Aktualisierungen beizubehalten.

## Einschränkungen {#limitations}

Massenbearbeitung von Seiteneigenschaften:

* Nicht verfügbar für Seiten in einer Live Copy.
* Nur für Seiten mit demselben Ressourcentyp verfügbar.
