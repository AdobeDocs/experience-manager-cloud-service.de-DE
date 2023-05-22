---
title: Inhaltserstellung mit dem universellen Editor
description: Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: ht
source-wordcount: '1152'
ht-degree: 100%

---

# Inhaltserstellung mit dem universellen Editor {#authoring}

Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.

## Einführung {#introduction}

Der universelle Editor ermöglicht die Bearbeitung beliebiger Inhalte in jeder Implementierung, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.

Zu diesem Zweck bietet es Inhaltsautorinnen und -autoren eine intuitive Benutzeroberfläche, die eine minimale Schulung erfordert, damit sie einfach loslegen und mit der Bearbeitung von Inhalten beginnen können.

>[!TIP]
>
>Eine detailliertere Einführung in den universellen Editor finden Sie im Dokument [Einführung in den universellen Editor](introduction.md).

>[!NOTE]
>
>Der universelle Editor befindet sich noch in der Entwicklung und kann derzeit nicht alle Inhaltstypen bearbeiten.

## Vorbereiten der App {#prepare-app}

Um Inhalte für eine App mit dem universellen Editor erstellen zu können, muss die App von einer Entwicklerperson instrumentiert werden, um den Editor zu unterstützen.

>[!TIP]
>
>Im Dokument [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) finden Sie ein Beispiel dafür, wie Sie eine AEM-App für die Arbeit mit dem universellen Editor konfigurieren.

## Anmelden {#sign-in}

Sobald die App für die Verwendung mit dem universellen Editor konfiguriert wurde, müssen Sie sich beim universellen Editor anmelden. Sie benötigen eine Adobe ID, um sich anzumelden und [Zugang zum universellen Editor zu erhalten](getting-started.md#request-access).

Sobald Sie angemeldet sind, geben Sie die URL der Seite, die Sie bearbeiten möchten, in die [Adressleiste ein.](#address-bar), um mit der [Bearbeitung des Inhalts zu beginnen](#edit-content).

## Grundlegendes zur Benutzeroberfläche {#ui}

Die Benutzeroberfläche ist in vier Hauptbereiche unterteilt.

* [Die Kopfzeile von Experience Cloud](#experience-cloud-header)
* [Die Kopfzeile des universellen Editors](#universal-editor-header)
* [Die Leiste](#rail)
* [Der Editor](#editor)

![Die Benutzeroberfläche des universellen Editors](assets/ui.png)

### Die Kopfzeile von Experience Cloud {#experience-cloud-header}

Die Kopfzeile von Experience Cloud befindet sich immer oben im Bildschirm. Es handelt sich um einen Anker, der Ihnen mitteilt, wo Sie sich in Experience Cloud befinden, und Ihnen dabei hilft, zu anderen Experience Cloud-Apps zu navigieren.

![Die Kopfzeile von Experience Cloud](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

Wählen Sie links in der Kopfzeile den Adobe Experience Cloud-Link aus, um zum Stammverzeichnis Ihrer Experience Manager-Lösung zu navigieren und auf Tools wie [Cloud Manager](/help/onboarding/cloud-manager-introduction.md), [Cloud Acceleration Manager](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) und [Software-Verteilung](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de) zuzugreifen.

![Schaltfläche für „Globale Navigation“](assets/global-navigation.png)

#### Organisation {#organization}

Dadurch wird die Organisation angezeigt, bei der Sie sich derzeit angemeldet haben. Tippen oder klicken Sie, um zu einer anderen Organisation zu wechseln, wenn Ihre Adobe ID mit mehreren Organisationen verknüpft ist.

![Organisationsanzeige](assets/organization.png)

#### Lösungen {#solutions}

Durch Tippen oder Klicken auf den Lösungsumschalter können Sie schnell zu anderen Experience Cloud-Lösungen wechseln.

![Lösungsumschalter](assets/solutions.png)

#### Hilfe {#help}

Das Hilfesymbol bietet schnellen Zugriff auf Lern- und Support-Ressourcen.

![Hilfe](assets/help.png)

#### Benachrichtigungen {#notifications}

Dieses Symbol wird mit der Anzahl der aktuell zugewiesenen unvollständigen [Benachrichtigungen](/help/implementing/cloud-manager/notifications.md) gekennzeichnet.

![Benachrichtigungen](assets/notifications.png)

#### Benutzereigenschaften {#user-properties}

Tippen oder klicken Sie auf das Symbol für Ihre Benutzerin bzw. Ihren Benutzer, um auf Ihre Benutzereinstellungen zuzugreifen. Wenn Sie kein Benutzerbild konfiguriert haben, wird ein zufälliges Symbol zugewiesen.

![Benutzereigenschaften](assets/user-properties.png)

### Die Kopfzeile des universellen Editors {#universal-editor-header}

Die Kopfzeile des universellen Editors befindet sich immer oben im Bildschirm direkt unter [der Kopfzeile von Experience Cloud.](#experience-cloud-header) Dadurch erhalten Sie schnellen Zugriff auf die Navigation zu einer anderen Seite, die Sie bearbeiten können, sowie auf die Veröffentlichung der aktuellen Seite.

![Die Kopfzeile des universellen Editors](assets/universal-editor-header.png)

#### Das Hamburger-Menü {#hamburger-menu}

Das Hamburger-Menü ist noch nicht implementiert.

![Hamburger-Menü](assets/hamburger-menu.png)

#### Speicherortleiste {#Location-bar}

Die Speicherortleiste zeigt die Adresse der Seite an, die Sie bearbeiten. Tippen oder klicken Sie, um die Adresse einer anderen Seite einzugeben, die bearbeitet werden soll.

![Speicherortleiste](assets/address-bar.png)

>[!TIP]
>
>Verwenden Sie den Hotkey `L`, um die Adressleiste zu öffnen.

>[!NOTE]
>
>Jede Seite, die Sie mit dem universellen Editor bearbeiten möchten, muss [für die Unterstützung des universellen Editors instrumentiert sein](getting-started.md).

#### App-Vorschau öffnen {#open-app-preview}

Tippen oder klicken Sie auf das Symbol „App-Vorschau öffnen“, um die Seite, die Sie gerade bearbeiten, in einem eigenen Browser zu öffnen, ohne dass der Editor eine Vorschau der Änderungen anzeigen kann.

![App-Vorschau öffnen](assets/open-app-preview.png)

>[!TIP]
>
>Verwenden Sie den Hotkey `O`, um die App-Vorschau zu öffnen.

#### Veröffentlichen  {#publish}

Tippen oder klicken Sie auf die Schaltfläche „Veröffentlichen“, um die Änderungen am Inhalt für Ihre Leserinnen und Leser live zu veröffentlichen.

![Schaltfläche „Veröffentlichen“](assets/publish.png)

>[!TIP]
>
>Weitere Informationen zur Veröffentlichung mit dem universellen Editor finden Sie im Dokument [Veröffentlichen von Inhalten mit dem universellen visuellen Editor](publishing.md).

### Die Leiste {#rail}

Die Leiste befindet sich immer auf der linken Seite des Editors. Dadurch können Sie den Editor einfach zwischen Vorschaumodus und Bearbeitungsmodus wechseln.

![Die Leiste](assets/rail.png)

#### Vorschaumodus {#preview-mode}

Im Vorschaumodus wird die Seite im Editor so gerendert, wie sie in Ihrem veröffentlichten Dienst angezeigt werden würde. Dadurch können Inhaltsautorinnen und -autoren durch Klicken auf Links usw. durch den Inhalt navigieren.

![Vorschaumodus](assets/preview-mode.png)

>[!TIP]
>
>Verwenden Sie den Hotkey `P`, um in den Vorschaumodus zu wechseln.

#### Bearbeitungsmodus {#edit-mode}

Im Bearbeitungsmodus wird die Seite im Editor gerendert, aber Inhaltsautorinnen und -autoren können klicken, um Inhalte auszuwählen und zu bearbeiten. Dies ist der Standardmodus des Editors beim Laden einer Seite.

![Bearbeitungsmodus](assets/edit-mode.png)

### Der Editor {#editor}

Der Editor nimmt den größten Teil des Fensters ein und ist der Ort, an dem die in der [Adressleiste](#address-bar) angegebene Seite gerendert wird.

Je nachdem, ob sich der Editor im [Bearbeitungsmodus](#edit-mode) oder [Vorschaumodus](#edit-mode) befindet, ist der Inhalt entweder editierbar oder navigierbar.

![Bearbeiter](assets/editor.png)

## Bearbeiten von Inhalten {#editing-content}

Die Bearbeitung von Inhalten ist einfach und intuitiv. Wenn Sie im [Bearbeitungsmodus](#edit-mode) mit dem Mauszeiger über einen Inhalt im Editor fahren, werden bearbeitbare Inhalte mit einem blauen Feld hervorgehoben.

![Bearbeitbare Inhalte werden durch ein blaues Feld hervorgehoben](assets/editable-content.png)

Tippen oder klicken Sie einfach auf den Inhalt im blauen Feld, um einen Editor für die Bearbeitung im Kontext zu starten und Ihre Änderungen vorzunehmen. Drücken Sie die Eingabetaste oder kehren Sie zurück, um die Änderungen zu speichern.

![Bearbeiten von Inhalten](assets/editing-content.png)

Beachten Sie, dass im Bearbeitungsmodus durch Tippen oder Klicken auf den Inhalt versucht wird, diesen zur Bearbeitung auszuwählen. Wenn Sie durch das Folgen von Links in Ihren Inhalten navigieren möchten, wechseln Sie zum [Vorschaumodus](#preview-mode).

## Vorschau von Inhalten {#previewing-content}

Wenn Sie mit der Bearbeitung von Inhalten fertig sind, möchten Sie häufig durch diese navigieren, um zu sehen, wie sie im Inhalt anderer Seiten aussehen. Im [Vorschaumodus](#preview-mode) können Sie auf Links klicken, um genau wie eine Person, die Ihre Inhalte liest, durch diese zu navigieren. Der Inhalt wird im Editor so wiedergegeben, wie er veröffentlicht werden würde.

Beachten Sie, dass im Vorschaumodus beim Tippen oder Klicken auf den Inhalt die gleiche Reaktion erfolgt, wie es bei einer Person, die den Inhalt liest, der Fall wäre. Wenn Sie den Inhalt zum Bearbeiten auswählen möchten, wechseln Sie in den [Bearbeitungsmodus](#edit-mode).

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) – Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) – Erfahren Sie, wie der universelle visuelle Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
