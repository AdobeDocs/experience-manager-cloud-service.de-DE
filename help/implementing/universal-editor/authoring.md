---
title: Inhaltserstellung mit dem universellen Editor
description: Erfahren Sie, wie einfach und intuitiv es für Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: 9cff6e94b38016f008fd8177be2e071a530d80b6
workflow-type: tm+mt
source-wordcount: '1152'
ht-degree: 2%

---

# Inhaltserstellung mit dem universellen Editor {#authoring}

Erfahren Sie, wie einfach und intuitiv es für Inhaltsautoren ist, Inhalte mit dem universellen Editor zu erstellen.

## Einführung {#introduction}

Der universelle Editor ermöglicht die Bearbeitung beliebiger Inhalte in jeder Implementierung, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.

Zu diesem Zweck bietet es Autoren von Inhalten eine intuitive Benutzeroberfläche, die eine minimale Schulung erfordert, damit sie einfach einspringen und mit der Bearbeitung von Inhalten beginnen können.

>[!TIP]
>
>Eine detailliertere Einführung in den universellen Editor finden Sie im Dokument [Einführung in den universellen Editor.](introduction.md)

>[!NOTE]
>
>Der Universal Editor befindet sich noch in der Entwicklung und kann derzeit nicht alle Inhaltstypen bearbeiten.

## Vorbereiten der App {#prepare-app}

Um Inhalte für eine App mit dem universellen Editor erstellen zu können, muss die App von einem Entwickler instrumentiert werden, um den Editor zu unterstützen.

>[!TIP]
>
>Lesen Sie das Dokument [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) ein Beispiel für die Konfiguration einer AEM App für die Verwendung mit dem universellen Editor.

## Anmelden {#sign-in}

Sobald die App für die Verwendung mit dem universellen Editor konfiguriert wurde, müssen Sie sich beim universellen Editor anmelden. Sie benötigen eine Adobe ID, um sich anzumelden und [haben Zugriff auf den universellen Editor.](getting-started.md#request-access)

Geben Sie nach der Anmeldung die URL der Seite ein, die Sie bearbeiten möchten, im [Adressleiste.](#address-bar) um zu beginnen [den Inhalt bearbeiten.](#edit-content)

## Grundlegendes zur Benutzeroberfläche {#ui}

Die Benutzeroberfläche ist in vier Hauptbereiche unterteilt.

* [Die Kopfzeile des Experience Cloud](#experience-cloud-header)
* [Die Kopfzeile des universellen Editors](#universal-editor-header)
* [Die Leiste](#rail)
* [Der Editor](#editor)

![Die Benutzeroberfläche des universellen Editors](assets/ui.png)

### Die Experience Cloud-Kopfzeile {#experience-cloud-header}

Die Kopfzeile des Experience Cloud befindet sich immer oben im Bildschirm. Es handelt sich um einen Anker, der Ihnen mitteilt, wo Sie sich in Experience Cloud befinden, und Ihnen dabei hilft, zu anderen Experience Cloud-Apps zu navigieren.

![Die Kopfzeile des Experience Cloud](assets/experience-cloud-header.png)

#### Experience Manager {#experience-manager}

Wählen Sie links in der Kopfzeile den Link Adobe Experience Cloud aus, um zum Stammverzeichnis Ihrer Experience Manager-Lösung zu navigieren und auf Tools wie [Cloud Manager,](/help/onboarding/cloud-manager-introduction.md) [Cloud Acceleration Manager,](/help/journey-migration/cloud-acceleration-manager/introduction/overview-cam.md) und [Softwareverteilung.](https://experienceleague.adobe.com/docs/experience-cloud/software-distribution/home.html?lang=de)

![Schaltfläche &quot;Globale Navigation&quot;](assets/global-navigation.png)

#### Organisation {#organization}

Dadurch wird die Organisation angezeigt, bei der Sie sich derzeit angemeldet haben. Tippen oder klicken Sie auf , um zu einer anderen Organisation zu wechseln, wenn Ihre Adobe ID mehreren zugeordnet ist.

![Organisationskennung](assets/organization.png)

#### Lösungen {#solutions}

Durch Tippen oder Klicken auf den Lösungsschalter können Sie schnell zu anderen Experience Cloud-Lösungen wechseln.

![Lösungsschalter](assets/solutions.png)

#### Hilfe {#help}

Das Hilfesymbol bietet schnellen Zugriff auf Lern- und Support-Ressourcen.

![Hilfe](assets/help.png)

#### Benachrichtigungen {#notifications}

Dieses Symbol wird mit der Anzahl der aktuell zugewiesenen unvollständigen Zeichen gekennzeichnet [Benachrichtigungen.](/help/implementing/cloud-manager/notifications.md)

![Benachrichtigungen](assets/notifications.png)

#### Benutzereigenschaften {#user-properties}

Tippen oder klicken Sie auf das Symbol für Ihren Benutzer, um auf Ihre Benutzereinstellungen zuzugreifen. Wenn Sie kein Benutzerbild konfiguriert haben, wird ein Symbol zufällig zugewiesen.

![Benutzereigenschaften](assets/user-properties.png)

### Die Kopfzeile des universellen Editors {#universal-editor-header}

Die Kopfzeile des universellen Editors befindet sich immer oben im Bildschirm direkt unten [die Kopfzeile des Experience Cloud.](#experience-cloud-header) Dadurch erhalten Sie schnellen Zugriff auf die Navigation zu einer anderen Seite, die Sie bearbeiten können, sowie auf die Veröffentlichung der aktuellen Seite.

![Die Kopfzeile des universellen Editors](assets/universal-editor-header.png)

#### Hamburger-Menü {#hamburger-menu}

Das Hamburger-Menü ist noch nicht implementiert.

![Hambuger-Menü](assets/hamburger-menu.png)

#### Standortleiste {#Location-bar}

Die Standortleiste zeigt die Adresse der Seite an, die Sie bearbeiten. Tippen oder klicken Sie, um die Adresse einer anderen Seite einzugeben, die bearbeitet werden soll.

![Symbolleiste](assets/address-bar.png)

>[!TIP]
>
>Verwenden des Hotkeys `L` um die Adressleiste zu öffnen.

>[!NOTE]
>
>Jede Seite, die Sie mit dem universellen Editor bearbeiten möchten, muss [instrumentiert, um den universellen Editor zu unterstützen.](getting-started.md)

#### App-Vorschau öffnen {#open-app-preview}

Tippen oder klicken Sie auf das Symbol &quot;App-Vorschau öffnen&quot;, um die Seite zu öffnen, die Sie gerade bearbeiten, in einem eigenen Browser, der nicht vom Editor zur Vorschau der Änderungen verfügbar ist.

![App-Vorschau öffnen](assets/open-app-preview.png)

>[!TIP]
>
>Verwenden des Hotkeys `O` , um die App-Vorschau zu öffnen.

#### Veröffentlichen  {#publish}

Tippen oder klicken Sie auf die Schaltfläche &quot;Veröffentlichen&quot;, um die Änderungen am Inhalt für Ihre Leser live zu veröffentlichen.

![Schaltfläche &quot;Veröffentlichen&quot;](assets/publish.png)

>[!TIP]
>
>Siehe Dokument . [Veröffentlichen von Inhalten mit dem universellen Visual Editor](publishing.md) für weitere Informationen zur Veröffentlichung mit dem universellen Editor.

### Die Leiste {#rail}

Die Leiste befindet sich immer auf der linken Seite des Editors. Dadurch können Sie den Editor einfach zwischen Vorschaumodus und Bearbeitungsmodus wechseln.

![Die Leiste](assets/rail.png)

#### Vorschaumodus {#preview-mode}

Im Vorschaumodus wird die Seite im Editor so gerendert, wie sie in Ihrem veröffentlichten Dienst angezeigt wird. Dadurch kann der Inhaltsautor durch Klicken auf Links usw. durch den Inhalt navigieren.

![Vorschaumodus](assets/preview-mode.png)

>[!TIP]
>
>Verwenden des Hotkeys `P` , um in den Vorschaumodus zu wechseln.

#### Bearbeitungsmodus {#edit-mode}

Im Bearbeitungsmodus wird die Seite im Editor gerendert, aber der Inhaltsautor kann klicken, um Inhalt auszuwählen und zu bearbeiten. Dies ist der Standardmodus des Editors beim Laden einer Seite.

![Modus Bearbeiten](assets/edit-mode.png)

### Der Editor {#editor}

Der Editor belegt den Großteil des Fensters und ist dort, wo die Seite angegeben ist in [Adressleiste](#address-bar) wird gerendert.

Je nachdem, ob sich der Editor in [Bearbeitungsmodus](#edit-mode) oder [Vorschaumodus,](#edit-mode) der Inhalt kann entweder bearbeitet oder navigiert werden.

![Bearbeiter](assets/editor.png)

## Bearbeiten von Inhalten {#editing-content}

Die Bearbeitung von Inhalten ist einfach und intuitiv. In [Bearbeitungsmodus,](#edit-mode) Wenn Sie den Mauszeiger über den Inhalt im Editor bewegen, werden bearbeitbare Inhalte durch ein blaues Feld markiert.

![Bearbeitbare Inhalte werden durch ein blaues Feld markiert](assets/editable-content.png)

Tippen oder klicken Sie einfach auf den Inhalt im blauen Feld, um einen Editor für die Bearbeitung im Kontext zu starten, um Ihre Änderungen vorzunehmen. Drücken Sie die Eingabetaste oder kehren Sie zurück, um die Änderungen zu speichern.

![Inhalt bearbeiten](assets/editing-content.png)

Beachten Sie, dass im Bearbeitungsmodus durch Tippen oder Klicken auf den Inhalt versucht wird, ihn zur Bearbeitung auszuwählen. Wenn Sie durch folgende Links in Ihren Inhalt navigieren möchten, wechseln Sie zu [Vorschaumodus.](#preview-mode)

## Vorschau von Inhalten {#previewing-content}

Wenn Sie mit der Bearbeitung von Inhalten fertig sind, möchten Sie häufig durch diese navigieren, um zu sehen, wie sie im Inhalt anderer Seiten aussehen. In [Vorschaumodus](#preview-mode) Sie können auf Links klicken, um wie ein Leser durch Ihren Inhalt zu navigieren. Der Inhalt wird im Editor so wiedergegeben, wie er veröffentlicht würde.

Beachten Sie, dass im Vorschaumodus das Tippen oder Klicken auf den Inhalt so reagiert, wie es für einen Leser des Inhalts der Fall wäre. Wenn Sie den zu bearbeitenden Inhalt auswählen möchten, wechseln Sie zu [Bearbeitungsmodus.](#edit-mode)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) - Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, um außergewöhnliche Erlebnisse bereitzustellen, die Inhaltsgeschwindigkeit zu erhöhen und ein modernes Entwicklererlebnis zu bieten.
* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) - Erfahren Sie, wie der universelle Visual Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) - Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](architecture.md) - Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](attributes-types.md) - Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Universelle Editor-Authentifizierung](authentication.md) - Erfahren Sie, wie der universelle Editor authentifiziert wird.
