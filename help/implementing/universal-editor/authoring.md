---
title: Inhaltserstellung mit dem universellen Editor
description: Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.
exl-id: 15fbf5bc-2e30-4ae7-9e7f-5891442228dd
source-git-commit: 05554f397a843ede5a723b206b6e0748e2d6ba96
workflow-type: tm+mt
source-wordcount: '1682'
ht-degree: 44%

---

# Inhaltserstellung mit dem universellen Editor {#authoring}

Erfahren Sie, wie einfach und intuitiv es für Inhaltsautorinnen und -autoren ist, Inhalte mit dem universellen Editor zu erstellen.

## Einführung {#introduction}

Der universelle Editor ermöglicht die Bearbeitung beliebiger Inhalte in jeder Implementierung, sodass Sie außergewöhnliche Erlebnisse bereitstellen, die Inhaltsgeschwindigkeit erhöhen und ein modernes Entwicklererlebnis bieten können.

Dazu bietet der universelle Editor Autoren von Inhalten eine intuitive Benutzeroberfläche, für die eine minimale Schulung erforderlich ist, um einfach in die Lage zu wechseln und mit der Bearbeitung von Inhalten zu beginnen. In diesem Dokument wird das Authoring-Erlebnis des universellen Editors beschrieben.

>[!TIP]
>
>Eine detailliertere Einführung in den universellen Editor finden Sie im Dokument [Einführung in den universellen Editor](introduction.md).

>[!NOTE]
>
>Der universelle Editor befindet sich noch in der Entwicklung. Es kann derzeit nicht alle Inhaltstypen bearbeitet werden.

## Vorbereiten der App {#prepare-app}

Um Inhalte für eine App mit dem universellen Editor zu erstellen, muss die App von einem Entwickler instrumentiert werden, um den Editor zu unterstützen.

>[!TIP]
>
>Siehe [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) ein Beispiel für die Konfiguration einer AEM App für die Verwendung mit dem universellen Editor.

## Anmelden {#sign-in}

Sobald die App für die Verwendung mit dem universellen Editor konfiguriert wurde, müssen Sie sich beim universellen Editor anmelden. Sie benötigen eine Adobe ID, um sich anzumelden und [Zugang zum universellen Editor zu erhalten](getting-started.md#request-access).

Geben Sie nach der Anmeldung die URL der Seite ein, die Sie bearbeiten möchten, im [Standortleiste.](#location-bar) damit Sie mit der Bearbeitung von Inhalten beginnen können, z. B. [Textinhalt](#text-mode) oder [Medieninhalte.](#media-mode)

## Grundlegendes zur Benutzeroberfläche {#ui}

Die Benutzeroberfläche ist in fünf Hauptbereiche unterteilt.

* [Die Kopfzeile von Experience Cloud](#experience-cloud-header)
* [Die Kopfzeile des universellen Editors](#universal-editor-header)
* [Die Modusleiste](#mode-rail)
* [Der Editor](#editor)
* [Die Komponentenleiste](#component-rail)

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

Dieses Symbol ist mit der Anzahl der aktuell zugewiesenen unvollständigen Zeichen gekennzeichnet [Benachrichtigungen.](/help/implementing/cloud-manager/notifications.md)

![Benachrichtigungen](assets/notifications.png)

#### Benutzereigenschaften {#user-properties}

Tippen oder klicken Sie auf das Symbol für Ihre Benutzerin bzw. Ihren Benutzer, um auf Ihre Benutzereinstellungen zuzugreifen. Wenn Sie kein Benutzerbild konfiguriert haben, wird ein Symbol zufällig zugewiesen.

![Benutzereigenschaften](assets/user-properties.png)

### Die Kopfzeile des universellen Editors {#universal-editor-header}

Die Kopfzeile des universellen Editors befindet sich immer oben im Bildschirm direkt unter [der Kopfzeile von Experience Cloud.](#experience-cloud-header) So erhalten Sie schnellen Zugriff auf die Navigation zu einer anderen Seite, um die aktuelle Seite zu bearbeiten und zu veröffentlichen.

![Die Kopfzeile des universellen Editors](assets/universal-editor-header.png)

#### Das Hamburger-Menü {#hamburger-menu}

Das Hamburger-Menü ist noch nicht implementiert.

![Hamburger Menü](assets/hamburger-menu.png)

#### Speicherortleiste {#location-bar}

Die Speicherortleiste zeigt die Adresse der Seite an, die Sie bearbeiten. Tippen oder klicken Sie, um die Adresse einer anderen Seite einzugeben, die bearbeitet werden soll.

![Speicherortleiste](assets/location-bar.png)

>[!TIP]
>
>Verwenden Sie den Hotkey `L`, um die Adressleiste zu öffnen.

>[!NOTE]
>
>Jede Seite, die Sie mit dem universellen Editor bearbeiten möchten, muss [für die Unterstützung des universellen Editors instrumentiert sein](getting-started.md).

#### Emulator-Einstellungen {#emulator}

Tippen oder klicken Sie auf das Emulationssymbol, um festzulegen, wie der Universal Editor die Seite rendert.

![Emulator-Symbol](assets/emulator.png)

Durch Tippen oder Klicken auf das Emulationssymbol werden die Optionen angezeigt.

![Emulierungsoptionen](assets/emulation-options.png)

Standardmäßig wird der Editor im Desktop-Layout geöffnet, wobei Höhe und Breite automatisch vom Browser definiert werden.

Sie können auch ein Mobilgerät und im universellen Editor emulieren:

* Ausrichtung definieren
* Breite und Höhe definieren
* Ausrichtung ändern

#### App-Vorschau öffnen {#open-app-preview}

Tippen oder klicken Sie auf das Symbol „App-Vorschau öffnen“, um die Seite, die Sie gerade bearbeiten, in einem eigenen Browser zu öffnen, ohne dass der Editor eine Vorschau der Änderungen anzeigen kann.

![App-Vorschau öffnen](assets/open-app-preview.png)

>[!TIP]
>
>Verwenden des Hotkeys `O` (Buchstabe O), um die App-Vorschau zu öffnen.

#### Veröffentlichen  {#publish}

Tippen oder klicken Sie auf die Schaltfläche &quot;Veröffentlichen&quot;, damit Sie die Änderungen an den Inhalten live für Ihre Leser veröffentlichen können.

![Schaltfläche „Veröffentlichen“](assets/publish.png)

>[!TIP]
>
>Weitere Informationen zur Veröffentlichung mit dem universellen Editor finden Sie im Dokument [Veröffentlichen von Inhalten mit dem universellen visuellen Editor](publishing.md).

### Die Modusleiste {#rail}

Die Modusleiste befindet sich immer auf der linken Seite des Editors. Dies ermöglicht das einfache Wechseln des Editors zwischen verschiedenen Bearbeitungsmodi.

![Die Modusleiste](assets/mode-rail.png)

#### Vorschaumodus {#preview-mode}

Im Vorschaumodus wird die Seite im Editor so gerendert, wie sie in Ihrem veröffentlichten Dienst angezeigt werden würde. Dadurch können Inhaltsautorinnen und -autoren durch Klicken auf Links usw. durch den Inhalt navigieren.

![Vorschaumodus](assets/preview-mode.png)

>[!TIP]
>
>Verwenden Sie den Hotkey `P`, um in den Vorschaumodus zu wechseln.

#### Textmodus {#text-mode}

Im Textmodus wird die Seite im Editor gerendert, aber der Inhaltsautor kann klicken, um Textinhalt auszuwählen und zu bearbeiten. Dies ist der Standardmodus des Editors beim Laden einer Seite.

![Textmodus](assets/text-mode.png)

>[!TIP]
>
>Verwenden des Hotkeys `T` , um in den Textmodus zu wechseln.

#### Medienmodus {#media-mode}

Im Medienmodus wird die Seite im Editor gerendert, aber der Inhaltsautor kann klicken, um Medieninhalte auszuwählen und zu bearbeiten.

![Medienmodus](assets/media-mode.png)

>[!TIP]
>
>Verwenden des Hotkeys `M` , um in den Medienmodus zu wechseln.

#### Komponentenmodus {#component-mode}

Im Komponentenmodus wird die Seite im Editor gerendert, aber der Inhaltsautor kann klicken, um Seitenkomponenten auszuwählen.

![Komponentenmodus](assets/component-mode.png)

Wenn Sie ein Inhaltsfragment auswählen, werden die Details in der [Komponentenleiste.](#component-rail)

>[!TIP]
>
>Verwenden des Hotkeys `C` , um in den Komponentenmodus zu wechseln.

#### Bearbeiten {#edit}

Wann [Komponentenmodus,](#component-mode) Wenn Sie ein Inhaltsfragment auswählen, wird die Bearbeitungsoption in der Modusleiste angezeigt.

![Symbol Bearbeiten](assets/edit.png)

Durch Tippen oder Klicken auf die Schaltfläche &quot;Bearbeiten&quot;wird der Inhaltsfragment-Editor in einer neuen Registerkarte geöffnet, mit der Sie referenzierte Inhalte sowie Text- und Medieninhalte im universellen Editor bearbeiten können.

>[!TIP]
>
>Verwenden des Hotkeys `E` , um eine ausgewählte Komponente zu bearbeiten.

### Der Editor {#editor}

Der Editor belegt den Großteil des Fensters und ist dort, wo die Seite angegeben ist in [die Standortleiste](#location-bar) wird gerendert.

* Wenn sich der Editor in einem Bearbeitungsmodus befindet, z. B. [Textmodus](#text-mode) oder [Medienmodus,](#media-mode) Der Inhalt kann bearbeitet werden und Sie können den Links nicht folgen.
* Wenn sich der Editor in [Vorschaumodus,](#preview-mode) Der Inhalt kann navigiert werden und Sie können Links folgen, den Inhalt kann jedoch nicht bearbeitet werden.

![Bearbeiter](assets/editor.png)

### Komponentenleiste {#component-rail}

Die Komponentenleiste befindet sich immer auf der linken Seite des Editors. Je nach Modus können Details zu einer im Inhalt ausgewählten Komponente oder die Hierarchie der Seiteninhalte angezeigt werden.

![Die Komponentenleiste](assets/component-rail.png)

#### Eigenschaftenmodus {#properties-mode}

Im Eigenschaftenmodus zeigt die Leiste die Eigenschaften der Komponente an, die derzeit im Editor ausgewählt sind. Dies ist der Standardmodus der Komponentenleiste beim Laden einer Seite.

![Eigenschaftenmodus](assets/properties-mode.png)

Details zur ausgewählten Komponente werden in der Leiste angezeigt. Wenn Sie ein Inhaltsfragment mithilfe von [Komponentenmodus,](#component-mode) Sie können die Einstellungen in der Komponentenleiste ändern. Änderungen werden automatisch vom universellen Editor gespeichert.

![Komponentendetails](assets/component-details.png)

Beachten Sie, dass nicht alle Komponenten Details aufweisen, die angezeigt werden können.

>[!TIP]
>
>Verwenden des Hotkeys `D` , um in den Eigenschaftenmodus zu wechseln.

#### Inhaltsbaum-Modus {#Content-tree-mode}

Im Inhaltsstrukturmodus zeigt die Leiste die Hierarchie des Seiteninhalts an.

![Inhaltsbaum-Modus](assets/content-tree-mode.png)

Bei der Auswahl eines Elements in der Inhaltsstruktur scrollt der Editor zu diesem Inhalt und wählt ihn aus.

![Inhaltsstruktur](assets/content-tree.png)

>[!TIP]
>
>Verwenden des Hotkeys `F` , um in den Inhaltsbaummodus zu wechseln.


## Bearbeiten von Inhalten {#editing-content}

Die Bearbeitung von Inhalten ist einfach und intuitiv. In den Bearbeitungsmodi ([Textmodus](#text-mode), [Medienmodus](#media-mode)und [Komponentenmodus](#component-mode)), während Sie den Mauszeiger über den Inhalt im Editor bewegen, wird der bearbeitbare Inhalt durch ein blaues Feld markiert.

![Bearbeitbare Inhalte werden durch ein blaues Feld hervorgehoben](assets/editable-content.png)

Tippen oder klicken Sie einfach auf den Inhalt im blauen Feld, um einen Editor für die Bearbeitung im Kontext zu starten und Ihre Änderungen vorzunehmen. Ihre Änderungen werden automatisch gespeichert.

![Bearbeiten von Inhalten](assets/editing-content.png)

Beachten Sie, dass im Bearbeitungsmodus durch Tippen oder Klicken auf den Inhalt versucht wird, diesen zur Bearbeitung auszuwählen. Wenn Sie durch das Folgen von Links in Ihren Inhalten navigieren möchten, wechseln Sie zum [Vorschaumodus](#preview-mode).

Je nach [mode](#mode-rail) Wenn Sie sich in befinden und den Inhalt, den Sie auswählen, haben Sie möglicherweise unterschiedliche Bearbeitungsoptionen für die Position.

Darüber hinaus können Sie zusätzliche Eigenschaften für den Inhalt mithilfe der [Komponentenleiste.](#component-rail) Wenn Sie beispielsweise eine Rich-Text-Komponente auswählen, können Sie Formatierungsoptionen in der Komponentenleiste bearbeiten.

![Bearbeiten einer Rich-Text-Komponente](assets/rich-text-editing.png)

## Vorschau von Inhalten {#previewing-content}

Wenn Sie mit der Bearbeitung von Inhalten fertig sind, möchten Sie häufig durch diese navigieren, um zu sehen, wie sie im Inhalt anderer Seiten aussehen. Im [Vorschaumodus](#preview-mode) können Sie auf Links klicken, um genau wie eine Person, die Ihre Inhalte liest, durch diese zu navigieren. Der Inhalt wird im Editor so wiedergegeben, wie er veröffentlicht werden würde.

Beachten Sie, dass im Vorschaumodus beim Tippen oder Klicken auf den Inhalt die gleiche Reaktion erfolgt, wie es bei einer Person, die den Inhalt liest, der Fall wäre. Wenn Sie den zu bearbeitenden Inhalt auswählen möchten, wechseln Sie in den Bearbeitungsmodus, z. B. [Textmodus](#text-mode) oder [Medienmodus.](#media-mode)

## Zusätzliche Ressourcen {#additional-resources}

Weitere Informationen zum universellen Editor finden Sie in diesen Dokumenten.

* [Einführung in den universellen Editor](introduction.md) - Erfahren Sie, wie der universelle Editor die Bearbeitung beliebiger Inhalte in jeder Implementierung ermöglicht, sodass Sie außergewöhnliche Erlebnisse bereitstellen, die Inhaltsgeschwindigkeit erhöhen und ein modernes Entwicklererlebnis bieten können.
* [Veröffentlichen von Inhalten mit dem universellen Editor](publishing.md) – Erfahren Sie, wie der universelle visuelle Editor Inhalte veröffentlicht und wie Ihre Apps mit den veröffentlichten Inhalten umgehen können.
* [Erste Schritte mit dem universellen Editor in AEM](getting-started.md) – Erfahren Sie, wie Sie Zugriff auf den universellen Editor erhalten und wie Sie mit der Instrumentierung Ihrer ersten AEM-App beginnen, um ihn zu verwenden.
* [Architektur des universellen Editors](architecture.md) – Erfahren Sie mehr über die Architektur des universellen Editors und darüber, wie Daten zwischen seinen Diensten und Ebenen fließen.
* [Attribute und Typen](attributes-types.md) – Erfahren Sie mehr über die Datenattribute und -typen, die der universelle Editor erfordert.
* [Authentifizierung beim universellen Editor](authentication.md) – Erfahren Sie, wie beim universellen Editor authentifiziert wird.
