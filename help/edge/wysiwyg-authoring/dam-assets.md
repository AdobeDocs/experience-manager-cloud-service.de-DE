---
title: Veröffentlichen von Seiten mit DAM-Assets über Edge Delivery Services
description: Erfahren Sie, welche Einstellungen erforderlich sind, um sicherzustellen, dass DAM-Assets für Ihre Seiten nahtlos in Edge Delivery Services veröffentlicht werden.
feature: Edge Delivery Services
role: Admin, Architect, Developer
exl-id: 160f0474-a72d-4183-a2b2-2f8ba177605d
index: false
hide: true
hidefromtoc: true
source-git-commit: 17c14a78c2cfa262e25c6196fa73c6c4b17e200a
workflow-type: ht
source-wordcount: '433'
ht-degree: 100%

---

# Veröffentlichen von Seiten mit DAM-Assets über Edge Delivery Services {#dam-assets}

Erfahren Sie, welche Einstellungen erforderlich sind, um sicherzustellen, dass DAM-Assets für Ihre Seiten nahtlos in Edge Delivery Services veröffentlicht werden.

## Universeller Editor, DAM-Assets und Edge Delivery {#overview}

Beim Bearbeiten von Inhalten für den universellen Editor können Sie selbstverständlich Assets aus DAM auswählen. Wenn Sie Ihre Inhalte in Edge Delivery Services veröffentlichen, werden auch die zugehörigen DAM-Inhalte veröffentlicht.

Um dieses nahtlose Verhalten sicherzustellen, müssen AEM und Edge Delivery Services entsprechenden DAM-Zugriff für die Veröffentlichung haben. Hierzu gehört Folgendes:

* [Sicherstellen, dass Asset-Ordner zugänglich sind](#accessible)
* [Sicherstellen, dass dem Asset-Ordner die richtige Konfiguration zugewiesen wurde (nach Bedarf)](#configuration)

## Sicherstellen, dass auf Assets-Ordner zugegriffen werden kann {#accessible}

Beim Veröffentlichen von Seiten aus AEM in Edge Delivery Services wird [ein technisches Konto](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) verwendet. Dieses Konto mit einem Namen im Format `<hash>@techacct.adobe.com` wird von Cloud Manager automatisch als Benutzer in AEM erstellt, wenn Sie eine mit dem universellen Editor erstellte Seite zum ersten Mal veröffentlichen.

![Technisches Konto](/help/edge/wysiwyg-authoring/assets/dam-assets/technical-account.png)

Dieses technische Konto muss über Zugriffsrechte für alle DAM-Ordner verfügen, um seinen Inhalt veröffentlichen zu können. Sie können entweder:

* Private DAM-Ordner nicht verwenden.
* Der bzw. dem Benutzenden des technischen Kontos Zugriff auf die DAM-Ordner gewähren.

## Sicherstellen, dass dem Asset-Ordner die richtige Konfiguration zugewiesen wurde {#configuration}

Im Allgemeinen reicht es aus, sicherzustellen, dass Ihr technisches Konto Zugriff auf Ihre Assets in DAM hat, um Ihre Assets zusammen mit Ihren Seiten in Edge Delivery Services zu veröffentlichen.

In zwei weiteren Fällen ist jedoch eine zusätzliche Konfiguration erforderlich:

* wenn Sie Seiten mit Nicht-Bild-Assets wie PDFs oder Videos in Edge Delivery Services veröffentlichen möchten
* wenn Sie Bild-Assets unabhängig von Seiten in Edge Delivery Services veröffentlichen möchten

Um beide Anwendungsfälle zu unterstützen, muss dem DAM-Ordner eine [Konfiguration](/help/implementing/developing/introduction/configurations.md) zugewiesen werden.

1. Melden Sie sich bei Ihrer AEM-Authoring-Umgebung an.
1. Wählen Sie unter **Sites** die Site aus, auf der Sie Ihre Assets veröffentlichen möchten, oder die Site, mit der die Assets verknüpft werden sollen.
1. Tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften**.
1. Notieren Sie sich auf der Registerkarte **Erweitert** des Fensters „Eigenschaften“ die Konfiguration im Feld **Cloud-Konfiguration**.
   * Diese wird automatisch erstellt, wenn Sie Ihre Site im Format `/conf/<site-name>` erstellen.
1. Tippen oder klicken Sie im Fenster „Eigenschaften“ auf **Abbrechen**, navigieren Sie zu **Assets** -> **Dateien** und wählen Sie Ihren DAM-Ordner aus.
1. Tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften**.
1. Wählen Sie auf der Registerkarte **Cloud-Services** des Fensters „Eigenschaften“ im Feld **Cloud-Konfiguration** dieselbe Konfiguration aus, die Sie sich zuvor notiert haben.
1. Tippen oder klicken Sie auf **Speichern und schließen**.
