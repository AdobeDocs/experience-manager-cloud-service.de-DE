---
title: Erstellen der Inhaltsstruktur für Ihre App
description: Erfahren Sie, wie Sie AEM Inhaltsfragmentmodelle verwenden können, um Ihre Inhaltsstruktur zu erstellen, die als Grundlage für Ihren Headless Content dient.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
feature: Headless
role: Admin, User, Developer
source-git-commit: c9cddf9f0e344a2a24ee1a608b3ea920e258f34a
workflow-type: tm+mt
source-wordcount: '1013'
ht-degree: 100%

---


# Erstellen der Inhaltsstruktur für Ihre App {#content-structure}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview"
>title="Erstellen der Inhaltsstruktur für Ihre App"
>abstract="Im Zuge dieser Serie von interaktiven Handbüchern erfahren Sie, wie Sie eine Struktur (das sogenannte Inhaltsfragmentmodell) erstellen, die als Grundlage für Ihre Headless-Inhalte dienen kann."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide"
>title="Modellkonsole starten"
>abstract="Sehen wir uns an, wie Sie ein wiederverwendbares Schema, ein sogenanntes Inhaltsfragmentmodell, für Ihre Inhalte in Adobe Experience Manager as a Cloud Service erstellen. Sehen Sie sich das Video an, um zu verstehen, warum dieser Schritt wichtig ist. <br><br>In diesem Lernmodul wird eine Reise-Website als Beispiel verwendet und Schritt für Schritt die Erstellung eines Modells für eine Reise erläutert.<br><br>Starten Sie dieses Modul auf einer neuen Registerkarte, indem Sie auf die Schaltfläche unten klicken und dieser Anleitung folgen."
>additional-url="https://video.tv.adobe.com/v/3413261?captions=ger" text="Einführungsvideo zu Inhaltsstrukturen"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="Herzlichen Glückwunsch! Sie haben gelernt, wie Sie ein Inhaltsfragmentmodell erstellen, in dem die Struktur Ihrer Headless-Daten dargestellt wird, und haben den ersten Schritt unternommen, um Omni-Channel-Inhalte skaliert und standardmäßig bereitzustellen."
>abstract=""

## Erstellen eines Modells {#create-model}

Die Inhaltsfragmentmodell-Konsole wird auf einer neuen Registerkarte geöffnet. Stellen Sie sich die Inhaltsfragmentmodell-Konsole als eine Modellbibliothek vor, in der Sie neue Modelle erstellen und vorhandene verwalten können.

Für das Beispiel erstellen Sie ein Modell, das die Datenstruktur einer Reise darstellt, die auf einer Reise-Website angeboten wird. Eine Reise mit diesem Modell wird als **Abenteuer** bezeichnet.

1. Klicken Sie in der rechten oberen Ecke des Bildschirms auf **Erstellen**, um mit der Erstellung eines Inhaltsfragmentmodells zu beginnen.

1. Der Assistent „Modell erstellen“ führt Sie durch die Erstellung Ihres Modells. Geben Sie die erforderlichen Informationen an.

   * **Modell-Titel** – Dies ist eine kurze Bezeichnung des Modells und enthält normalerweise den Zweck des Modells. Sie können das neue Modell `Adventure` nennen.
   * **Modell aktivieren**: Diese Option ist standardmäßig aktiviert. Sie muss aktiviert sein, damit auf diesem Modell basierende Inhaltsfragmente erstellt werden können.

1. Nachdem die Pflichtfelder ausgefüllt wurden, klicken Sie oben rechts auf **Erstellen**, um das Modell zu erstellen.

1. Das Dialogfeld **Erfolg** bestätigt, dass das Modell erstellt wurde. Klicken Sie im Dialogfeld auf **Öffnen**, damit Sie Ihr neues Inhaltsfragmentmodell im Editor auf einer neuen Registerkarte öffnen können. Fahren Sie dann mit dem nächsten Schritt fort, um Ihrem Modell Datenfelder hinzuzufügen.

![Schritte 2 und 3 zum Erstellen eines Inhaltsfragmentmodells](assets/do-not-localize/create-model.png)

## Verwenden des Modell-Editors {#configure-model}

Wir haben jetzt ein Modell namens **Abenteuer**, aber es hat keine Details wie Dauer, Ziel und Aktivitäten. Bevor Sie das Modell verwenden können, müssen Sie die Datenstruktur definieren.

Im Editor für Inhaltsfragmentmodelle konfigurieren Sie die Datentypen und Eigenschaften, die den Inhalt des Modells definieren.

>[!TIP]
>
>Es ist wichtig, die Namensschemata in den folgenden Anweisungen zu befolgen, da diese spezifischen Namen in späteren Modulen referenziert werden.

1. Ziehen Sie ein **einzeiliges Textfeld** aus dem Bedienfeld **Datentypen** auf der rechten Seite des Editors und legen Sie es auf Ihrem Inhaltsfragmentmodell ab.

1. Nachdem ein Datentyp abgelegt wurde, wird automatisch statt der Spalte **Datentypen** die Registerkarte **Eigenschaften** angezeigt, auf der Sie die Details des von Ihnen platzierten Datentyps definieren können. Für dieses erste Feld sollten Sie den Titel der Reise oder des Abenteuers speichern. Tragen Sie die folgenden Eigenschaften ein.

   * **Rendern als:** **Textfeld** – Wenn Sie ein Abenteuer erstellen, wird in diesem Feld der Titel des Abenteuers gespeichert.
   * **Feldbezeichnung:** `Title`: Die Bezeichnung, die für dieses Feld angezeigt wird, wenn ein Abenteuer erstellt wird.

1. Sobald Sie die Eigenschaften des Feldes definiert haben, können Sie zurück zur Registerkarte **Datentypen** im rechten Bereich wechseln und durch Ziehen und Ablegen weitere Felder hinzufügen.

Auf diese Weise können Sie Ihrem Modell so viele Felder wie nötig hinzufügen, um die Datenstruktur zu unterstützen, die Sie benötigen. Die Datenfeld-Typen variieren, aber der Prozess, sie zu Ihrem Modell hinzuzufügen, bleibt gleich.

Fahren Sie mit dem nächsten Abschnitt fort, um die zum Ausfüllen und Speichern des Modells **Abenteuer** erforderlichen Felder hinzuzufügen

![Schritte 1, 2 und 3 zum Hinzufügen von Feldern zum Modell](assets/do-not-localize/define-model-fields.png)

## Hinzufügen von Feldern zum Modell {#additional-fields}

Sie haben bereits ein Feld für den Titel des Abenteuers. Jetzt müssen Sie Felder hinzufügen, um die Beschreibung, den Preis und ein repräsentatives Bild des Abenteuers zu erfassen.

>[!TIP]
>
>Das Modell **Abenteuer** basiert auf der WKND-Beispiel-Site für AEM. Sie können die WKND-Site [hier](https://wknd.site/us/en/adventures/yosemite-backpacking.html) besuchen, um Inhalte zu sehen, die das Modell **Abenteuer** verwenden.

Gehen Sie wie oben beschrieben vor, um diese zusätzlichen Felder hinzuzufügen. Der einzige Unterschied besteht in den Eigenschaften, die Sie festlegen müssen.

1. Fügen Sie ein Feld hinzu, um die Beschreibung des Abenteuers zu speichern, indem Sie ein **mehrzeiliges Textfeld** per Drag-and-Drop hinzufügen und die folgenden Eigenschaften eingeben:

   * **Rendern als:** **Textbereich**: Wenn Sie ein Abenteuer erstellen, wird in diesem Feld eine kurze Beschreibung der Reise gespeichert.
   * **Feldbezeichnung:** `Description`: Die Bezeichnung, die für dieses Feld angezeigt wird, wenn ein Abenteuer erstellt wird.
   * **Standardtyp**: **Nur Text**: Das für dieses Beispiel erforderliche Format.

1. Fügen Sie ein Feld hinzu, um den Preis des Abenteuers zu speichern, indem Sie ein **einzeiliges Textfeld** per Drag-and-Drop hinzufügen und die folgenden Eigenschaften eingeben:

   * **Rendern als:** **Textfeld**: Wenn Sie ein Abenteuer erstellen, wird in diesem Feld der Preis der Reise gespeichert.
   * **Feldbezeichnung:** `Price`: Die Bezeichnung, die für dieses Feld angezeigt wird, wenn ein Abenteuer erstellt wird.

1. Fügen Sie ein Feld hinzu, um ein Bild zu speichern, das die Reise darstellt. Bilder in AEM werden als ein weiterer Inhaltstyp namens **Assets** gespeichert. Um ein Feld für sie zu erstellen, erstellen Sie per Drag-and-Drop ein Feld **Inhaltsreferenz**, das auf das Asset des Bildes verweist.

   * **Rendern als:** **Inhaltsreferenz**: Wenn Sie ein Abenteuer erstellen, verweist dieses Feld auf das Bild-Asset, das diese Reise darstellt.
   * **Feldbezeichnung:** `Image`: Die Bezeichnung, die für dieses Feld angezeigt wird, wenn ein Abenteuer erstellt wird.
   * **Stammpfad:** `/content/dam/aem-demo-assets/en`: Gibt einen Startpunktpfad beim Suchen nach Assets mit dem Asset-Selektor an.

1. Nachdem Sie die erforderlichen Felder für das Inhaltsfragmentmodell hinzugefügt haben, klicken Sie oben rechts im Fenster auf **Speichern**.

1. Das Modell wird gespeichert, und Sie kehren zur Inhaltsfragmentmodell-Konsole zurück.
