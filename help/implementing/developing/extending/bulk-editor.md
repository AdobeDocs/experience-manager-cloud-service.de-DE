---
title: Konfigurieren der Massenbearbeitung von Seiteneigenschaften
description: Erfahren Sie, wie Sie die Massenbearbeitung konfigurieren, damit Sie die Eigenschaften mehrerer Seiten gleichzeitig bearbeiten können.
exl-id: 0d10c6b9-8643-479d-adc1-4066d227e83d
feature: Developing
role: Admin, Architect, Developer
source-git-commit: 3238b11cdd891cf18048199d4103397e3af75edf
workflow-type: ht
source-wordcount: '250'
ht-degree: 100%

---

# Konfigurieren der Massenbearbeitung von Seiteneigenschaften {#configuring-bulk-editing-of-page-properties}

Die [Massenbearbeitung von Seiteneigenschaften](/help/sites-cloud/authoring/sites-console/edit-page-properties.md#from-the-sites-console-multiple-pages) ermöglicht es Ihnen, die Eigenschaften mehrerer Seiten gleichzeitig zu bearbeiten.

## Überlegungen {#considerations}

Seiteneigenschaften sind nicht standardmäßig für die Massenbearbeitung aktiviert. Sie müssen explizit aktiviert sein. Wenn Sie die Seiteneigenschaften definieren, die für die Massenbearbeitung verfügbar sein sollen, müssen Sie bestimmte Auswirkungen berücksichtigen, wie zum Beispiel:

* Bestimmte Felder sind in der Regel eindeutig. Sie müssen entscheiden, ob es sinnvoll ist, diese Felder für die Massenbearbeitung zu aktivieren, wenn ein Wert angewendet wird.
   * Beispielsweise sind Seitentitel fast immer eindeutig.
* Bestimmte Felder können mehrere Werte haben – dies erfordert eine sinnvolle Darstellung beim Rendern.
   * Eine Status-Dropdown-Liste mit der Bezeichnung **Bereit zur Veröffentlichung** kann etwa. mehrere Werte vor der Massenbearbeitung aufweisen, z. B. **bereit**, **in Überarbeitung**, **in Bearbeitung** usw.

Aufgrund der Möglichkeit mehrerer Werte wird empfohlen, nur die folgenden Feldtypen für die Massenbearbeitung zu aktivieren.

* `/libs/granite/ui/components/foundation/form/textfield`
* `/libs/granite/ui/components/foundation/form/textarea`
* `/libs/granite/ui/components/foundation/form/tagspicker`
* `/libs/granite/ui/components/foundation/form/datepicker`
* `/libs/granite/ui/components/foundation/form/pathbrowser`
* `/libs/granite/ui/components/foundation/form/checkbox`

## Aktivieren eines Felds {#enabling-a-field}

Für diese Schritte wird `/apps/core/wcm/components/page/v1/page` aus dem [WKND-Beispielinhalt](/help/implementing/developing/introduction/develop-wknd-tutorial.md) als Beispiel für die Massenbearbeitung eines Felds in einer Entwicklungsumgebung verwendet.

1. Öffnen Sie Ihre Seitenkomponente mit CRXDE.
1. Navigieren Sie zum erforderlichen Feld innerhalb der `cq:dialog`-Definition.
1. Definieren Sie die folgende Eigenschaft auf dem Feldknoten:

   * **Name**: `allowBulkEdit`
   * **Typ**: `Boolean`
   * **Wert**: `true`

1. Wählen Sie **Alle speichern**, um ihre Aktualisierungen beizubehalten.

## Einschränkungen {#limitations}

Die Massenbearbeitung von Seiteneigenschaften ist:

* für Seiten in einer Live Copy nicht verfügbar.
* nur für Seiten mit demselben Ressourcentyp verfügbar.
