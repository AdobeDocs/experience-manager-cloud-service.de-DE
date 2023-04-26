---
title: Erstellen der Inhaltsstruktur für Ihre App
description: Erfahren Sie, wie Sie AEM Inhaltsfragmentmodelle verwenden können, um Ihre Inhaltsstruktur zu erstellen, die als Grundlage für Ihren Headless Content dient.
hidefromtoc: true
index: false
exl-id: ace9b9f3-8bc6-4a36-a51c-ff60cdd339ce
source-git-commit: 7134951a588eae3ee0c7c11abea17a34eac21474
workflow-type: tm+mt
source-wordcount: '1062'
ht-degree: 37%

---


# Erstellen der Inhaltsstruktur für Ihre App {#content-structure}

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview"
>title="Erstellen der Inhaltsstruktur für Ihre App"
>abstract="Wenn Sie dieser Reihe interaktiver Handbücher folgen, lernen Sie, eine Struktur (das so genannte Inhaltsfragmentmodell) zu erstellen, die als grundlegende Struktur für Headless-Inhalte dient."

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide"
>title="Starten der Modellkonsole"
>abstract="Nun sehen wir uns an, wie Sie ein wiederverwendbares Schema, ein sogenanntes Inhaltsfragmentmodell, für Ihre Inhalte in Adobe Experience Manager as a Cloud Service erstellen. In diesem Video erfahren Sie, warum dies ein wichtiger Schritt ist. <br><br>In diesem Lernmodul verwenden wir eine Reisesite als Beispiel und gehen durch die Erstellung eines Modells, das eine Reise darstellt. Wir werden dieses Modell in späteren Modulen referenzieren. Befolgen Sie daher das Namensschema wie angegeben.<br><br>Starten Sie dieses Modul auf einer neuen Registerkarte, indem Sie auf die Schaltfläche unten klicken und dieser Anleitung folgen."
>additional-url="https://video.tv.adobe.com/v/3413261?captions=ger" text="Einführungsvideo zu Inhaltsstrukturen"

>[!CONTEXTUALHELP]
>id="aemcloud_sites_trial_admin_content_fragments_overview_guide_footer"
>title="Herzlichen Glückwunsch! Sie haben gelernt, wie Sie ein Inhaltsfragmentmodell erstellen, in dem die Struktur Ihrer Headless-Daten dargestellt wird, und haben den ersten Schritt unternommen, um Omni-Channel-Inhalte skaliert und standardmäßig bereitzustellen."
>abstract=""

## Erstellen eines Modells {#create-model}

Die Inhaltsfragmentmodell-Konsole wird auf einer neuen Registerkarte geöffnet. Stellen Sie sich die Inhaltsfragmentmodell-Konsole als eine Modellbibliothek vor, in der Sie neue Modelle erstellen und vorhandene verwalten.

Für unser Beispiel erstellen wir ein Modell, das die Datenstruktur einer Reise darstellt, die auf einer Reisewebsite dargestellt wird. Wir werden eine Reise in diesem Modell als **Abenteuer.**

1. Klicken Sie oben rechts im Bildschirm auf **Erstellen**, um mit der Erstellung eines Inhaltsfragmentmodells zu beginnen.

1. Der Assistent Modell erstellen wird gestartet, der Sie durch die Erstellung Ihres Modells führt. Geben Sie die folgenden Informationen an.

   * **Modelltitel**: Dies ist eine kurze Beschreibung des Modells und enthält normalerweise den Zweck des Modells. Wir nennen unser neues Modell `Adventure`.
   * **Modell aktivieren**: Diese Option ist standardmäßig aktiviert. Es muss aktiviert sein, damit auf diesem Modell basierende Inhaltsfragmente erstellt werden können.

1. Nachdem die Pflichtfelder ausgefüllt wurden, klicken Sie oben links auf **Erstellen**, um das Modell zu erstellen.

1. Das Dialogfeld **Erfolg** bestätigt, dass das Modell erstellt wurde. Klicken Sie im Dialogfeld auf **Öffnen**, um Ihr neues Inhaltsfragmentmodell auf einer neuen Registerkarte im Editor zu öffnen. Fahren Sie dann mit dem nächsten Schritt fort, um Ihrem Modell Datenfelder hinzuzufügen.

![Schritte 2 und 3 zum Erstellen eines Inhaltsfragmentmodells](assets/do-not-localize/create-model.png)

## Verwenden des Modell-Editors {#configure-model}

Wir haben jetzt ein Modell namens **Abenteuer** , um Reisen auf einer Reise-Website zu repräsentieren, aber keine Details wie Dauer, Ziel, Aktivitäten usw. Bevor Sie das Modell verwenden können, müssen Sie die Datenstruktur definieren.

Im Editor für Inhaltsfragmentmodelle konfigurieren Sie die Datentypen und Eigenschaften, die den Inhalt des Modells definieren.

>[!TIP]
>
>Wir werden einige wichtige Felder für die **Abenteuer**. In späteren Modulen werden wir verwenden und zum Modell hinzufügen. Befolgen Sie daher das Namensschema wie angegeben.

1. Ziehen Sie eine **Einzelzeilentext** aus dem **Datentypen** rechts neben dem Editor und legen Sie es auf Ihrem Inhaltsfragmentmodell ab.

1. Nachdem ein Datentyp abgelegt wurde, wird automatisch statt der Spalte **Datentypen** die Registerkarte **Eigenschaften** angezeigt, auf der Sie die Details des gerade platzierten Datentyps definieren können. Für dieses erste Feld möchten wir den Titel der Reise oder des Abenteuers speichern. Tragen Sie die folgenden Eigenschaften ein.

   * **Render As:** **Textfeld** - Wenn Sie ein Abenteuer erstellen, wird dieses Feld den Titel des Abenteuers speichern.
   * **Feldbezeichnung:** `Title` - Dies ist der Titel, der für dieses Feld angezeigt wird, wenn ein neues Abenteuer erstellt wird.

1. Sobald Sie die Eigenschaften des Felds definiert haben, können Sie zum **Datentypen** im rechten Bereich ein und fügen Sie durch Ziehen und Ablegen zusätzliche Felder hinzu.

Auf diese Weise können Sie Ihrem Modell so viele Felder wie nötig hinzufügen, um die Datenstruktur zu unterstützen, die Sie benötigen. Die Typen von Datenfeldern variieren, aber der Prozess, sie zu Ihrem Modell hinzuzufügen, bleibt gleich.

Fahren Sie mit dem nächsten Abschnitt fort, um die zum Ausfüllen und Speichern der **Abenteuer** model

![Schritte 1, 2 und 3 zum Hinzufügen von Feldern zum Modell](assets/do-not-localize/define-model-fields.png)

## Hinzufügen von Feldern zum Modell {#additional-fields}

Sie haben bereits ein Feld für den Titel des Abenteuers. Jetzt müssen Sie Felder hinzufügen, um die Beschreibung, den Preis und ein repräsentatives Bild der Reise zu erfassen.

>[!TIP]
>
>Die **Abenteuer** basiert auf der WKND-Beispiel-Site für AEM. Sie können [Besuchen Sie die Website hier](https://wknd.site/us/en/adventures/yosemite-backpacking.html) um mehr darüber zu erfahren, wenn Sie es wünschen, aber Kenntnisse darüber sind für diese Lernmodule nicht erforderlich.

Gehen Sie wie oben beschrieben vor, um diese zusätzlichen Felder hinzuzufügen. Der einzige Unterschied sind die Eigenschaften, die Sie festlegen müssen.

1. Fügen Sie ein Feld hinzu, um die Beschreibung des Abenteuers durch Ziehen und Ablegen einer **Mehrzeiliger Text** und geben Sie die folgenden Eigenschaften ein:

   * **Render As:** **Textbereich** - Wenn Sie ein Abenteuer erstellen, wird dieses Feld eine kurze Beschreibung der Reise speichern.
   * **Feldbezeichnung:** `Description` - Dies ist der Titel, der für dieses Feld angezeigt wird, wenn ein neues Abenteuer erstellt wird.

1. Fügen Sie ein Feld hinzu, um den Preis des Abenteuers durch Ziehen und Ablegen eines **Einzelzeilentext** und geben Sie die folgenden Eigenschaften ein:

   * **Render As:** **Textfeld** - Wenn Sie ein Abenteuer erstellen, wird dieses Feld den Preis der Reise speichern.
   * **Feldbezeichnung:** `Price` - Dies ist der Titel, der für dieses Feld angezeigt wird, wenn ein neues Abenteuer erstellt wird.

1. Fügen Sie ein Feld hinzu, um ein Bild zu speichern, das die Reise darstellt. Bilder in AEM werden als anderer Inhaltstyp gespeichert, der **Assets**. Um ein Feld für sie zu erstellen, müssen Sie eine **Inhaltsreferenz** -Feld, das auf das Asset des Bildes verweist.

   * **Render As:** **Inhaltsreferenz** - Wenn Sie ein Abenteuer erstellen, verweist dieses Feld auf das Bild-Asset, das diese Reise darstellt.
   * **Feldbezeichnung:** `Image` - Dies ist der Titel, der für dieses Feld angezeigt wird, wenn ein neues Abenteuer erstellt wird.

1. Nachdem Sie alle für das Inhaltsfragmentmodell erforderlichen Felder hinzugefügt haben, klicken Sie oben rechts im Fenster auf **Speichern**.

1. Das Modell wird gespeichert und Sie kehren zur Inhaltsfragmentmodell-Konsole zurück.
