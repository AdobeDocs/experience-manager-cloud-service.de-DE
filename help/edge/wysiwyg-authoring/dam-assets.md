---
title: Veröffentlichen von Seiten mit DAM Assets mithilfe von Edge Delivery Services
description: Erfahren Sie, welche Einstellungen erforderlich sind, um sicherzustellen, dass Ihre DAM-Assets für Ihre Seiten nahtlos in Edge Delivery Services veröffentlicht werden.
feature: Edge Delivery Services
role: Admin, Architect, Developer
source-git-commit: 65a3b4d923a91702e7ea9b13356802836fa4ce0b
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 2%

---


# Veröffentlichen von Seiten mit DAM Assets mithilfe von Edge Delivery Services {#dam-assets}

Erfahren Sie, welche Einstellungen erforderlich sind, um sicherzustellen, dass Ihre DAM-Assets für Ihre Seiten nahtlos in Edge Delivery Services veröffentlicht werden.

## Universal Editor, DAM Assets und Edge Delivery {#overview}

Beim Bearbeiten von Inhalten für den universellen Editor können Sie natürlich Assets aus dem DAM auswählen. Wenn Sie Ihre Inhalte in Edge Delivery Services veröffentlichen, wird auch der zugehörige DAM-Inhalt veröffentlicht.

Um dieses nahtlose Verhalten sicherzustellen, müssen AEM und Edge Delivery Services einen angemessenen Zugriff auf das DAM haben, damit sie es veröffentlichen können. Hierzu gehört Folgendes:

* [Sicherstellen, dass Assets-Ordner zugänglich sind.](#accessible)
* [Sicherstellen, dass dem Ordner &quot;Assets&quot;die richtige Konfiguration zugewiesen wird (nach Bedarf).](#configuration)

## Sicherstellen, dass Assets-Ordner verfügbar sind {#accessible}

Beim Veröffentlichen von Seiten von AEM in Edge Delivery Services wird [ein technisches Konto](/help/implementing/developing/introduction/generating-access-tokens-for-server-side-apis.md) verwendet. Dieses Konto mit einem Namen im Format &quot;`<hash>@techacct.adobe.com`&quot; wird in Cloud Manager automatisch als Benutzer AEM, sobald Sie eine mit dem universellen Editor erstellte Seite zum ersten Mal veröffentlichen.

![Technisches Konto](/help/edge/wysiwyg-authoring/assets/dam-assets/technical-account.png)

Dieses technische Konto muss über Zugriffsrechte für alle DAM-Ordner verfügen, um seinen Inhalt veröffentlichen zu können. Wählen Sie eine der folgenden Möglichkeiten aus:

* Verwenden Sie keine privaten DAM-Ordner.
* Gewähren Sie dem Benutzer des technischen Kontos Zugriff auf die DAM-Ordner.

## Sicherstellen, dass der Assets-Ordner ordnungsgemäß konfiguriert ist {#configuration}

Generell ist es ausreichend sicherzustellen, dass Ihr technisches Konto Zugriff auf Ihre Assets in DAM hat, um Ihre Assets zusammen mit Ihren Seiten für Edge Delivery Services zu veröffentlichen.

In zwei zusätzlichen Fällen ist jedoch eine zusätzliche Konfiguration erforderlich:

* Wenn Sie Seiten mit Nicht-Bild-Assets wie PDF oder Videos für Edge Delivery Services veröffentlichen möchten.
* Wenn Sie Bild-Assets unabhängig von Seiten in Edge Delivery Services veröffentlichen möchten.

Um beide Anwendungsfälle zu unterstützen, muss dem DAM-Ordner eine [Konfiguration](/help/implementing/developing/introduction/configurations.md) zugewiesen werden.

1. Melden Sie sich in Ihrer AEM Authoring-Umgebung an.
1. Wählen Sie unter **Sites** die Site aus, auf der Sie Ihre Assets veröffentlichen, oder die Site, mit der die Assets verknüpft werden sollen.
1. Tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften** .
1. Notieren Sie sich auf der Registerkarte **Erweitert** im Eigenschaftenfenster die Konfiguration im Feld **Cloud-Konfiguration** .
   * Diese wird automatisch erstellt, wenn Sie Ihre Site im Format `/conf/<site-name>` erstellen.
1. Tippen oder klicken Sie im Eigenschaftenfenster auf **Abbrechen** , navigieren Sie zu **Assets** -> **Dateien** und wählen Sie Ihren DAM-Ordner aus.
1. Tippen oder klicken Sie in der Symbolleiste auf **Eigenschaften** .
1. Wählen Sie auf der Registerkarte **Cloud Service** des Eigenschaftenfensters im Feld **Cloud-Konfiguration** dieselbe Konfiguration aus wie zuvor.
1. Tippen oder klicken Sie auf **Speichern und schließen**.
