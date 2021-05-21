---
title: Vorbereiten von Inhalten für die Übersetzung
description: Erfahren Sie, wie Sie Inhalte für die Übersetzung vorbereiten.
feature: Sprachkopie
role: Administrator
exl-id: afc577a2-2791-481a-ac77-468011e4302e
source-git-commit: 90de3cf9bf1c949667f4de109d0b517c6be22184
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 100%

---

# Vorbereiten von Inhalten für die Übersetzung  {#preparing-content-for-translation}

Bei mehrsprachigen Websites wird in der Regel ein Teil der Inhalte in mehreren Sprachen bereitgestellt. Die Website wird in einer Sprache verfasst und anschließend in weitere Sprachen übersetzt. Im Allgemeinen bestehen mehrsprachige Websites aus Zweigen von Seiten, wobei jeder Zweig die Seiten der Website in einer anderen Sprache enthält.

Die [WKND-Tutorial-Website](/help/implementing/developing/introduction/develop-wknd-tutorial.md) umfasst mehrere Sprachzweige und weist die folgende Struktur auf:

```text
/content
    |- wknd
        |- language-masters
            |- en
            |- de
            |- es
            |- fr
            |- it
        |- us
            |- en
            |- es
        |- ca
            |- en
            |- fr
        |- ch
            |- de
            |- fr
            |- it
        |- de
            |- de
        |- fr
            |- fr
        |- es
            |- es
        |- it
            |- it
```

Die Sprachkopie, für die Sie ursprünglich Inhalte verfassen, ist der Sprach-Master. Die Sprach-Master-Vorlage ist die Quelle, die in andere Sprachen übersetzt wird.

Jeder Sprachzweig einer Website wird als Sprachkopie bezeichnet. Die Stammseite einer Sprachkopie, auch als Sprachstamm bezeichnet, identifiziert die Sprache des Inhalts in der Sprachkopie. Beispielsweise stellt `/content/wknd/fr` den Sprachstamm der französischen Sprachkopie dar. Sprachkopien müssen einen [korrekt konfigurierten Sprachstamm](preparation.md#creating-a-language-root) verwenden, damit die korrekte Sprache angesprochen wird, wenn Übersetzungen von einer Quell-Website durchgeführt werden.

Führen Sie die folgenden Schritte aus, um Ihre Website für die Übersetzung vorzubereiten:

1. Erstellen Sie den Sprachstamm für Ihren Sprach-Master. Der Sprachstamm der englischen Beispiel-WKND-Website ist z. B. `/content/wknd/language-masters/en`. Stellen Sie sicher, dass der Sprachstamm entsprechend den Informationen unter [Erstellen eines Sprachstamms](preparation.md#creating-a-language-root) konfiguriert ist.
1. Verfassen Sie den Inhalt des Sprach-Masters.
1. Erstellen Sie den Sprachstamm jeder Sprachkopie für die Website. Der Sprachstamm der französischen Beispiel-WKND-Website ist z. B. /`/content/wknd/language-masters/fr`

Wenn Sie die Inhalte für die Übersetzung vorbereitet haben, können Sie automatisch fehlende Seiten in den Sprachkopien und zugehörigen Übersetzungsprojekten erstellen. (Siehe [Erstellen eines Übersetzungsprojekts](managing-projects.md).) Einen Überblick über den Prozess der Inhaltsübersetzung in AEM finden Sie unter [Übersetzen von Inhalten für mehrsprachige Websites](overview.md).

## Erstellen eines Sprachstamms {#creating-a-language-root}

Erstellen Sie einen Sprachstamm als Stammseite einer Sprachkopie, die die Sprache der Inhalte identifiziert. Nachdem Sie den Sprachstamm erstellt haben, können Sie Übersetzungsprojekte erstellen, die die Sprachkopie umfassen.

Um den Sprachstamm zu erstellen, erstellen Sie eine Seite und verwenden Sie einen ISO-Sprachcode als Wert für die Eigenschaft **Name**. Der Sprachcode muss eines der folgenden Formate aufweisen:

* `<language-code>` - Der unterstützte Sprachcode ist ein Code mit zwei Buchstaben gemäß ISO-639-1, zum Beispiel `en`.
* `<language-code>_<country-code>` oder `<language-code>-<country-code>` – Der unterstützte Ländercode ist ein Code mit zwei Groß- oder zwei Kleinbuchstaben gemäß ISO 3166, zum Beispiel `en_US`, `en_us`, `en_GB`, `en-gb`.

Sie können jedes dieser Formate verwenden, passend zur Struktur Ihrer globalen Website.  Beispielsweise verfügt die Stammseite der französischen Sprachkopie der WKND-Website über `fr` als die Eigenschaft **Name**. Beachten Sie, dass die Eigenschaft **Name** als Name des Seitenknotens im Repository verwendet wird und daher den Pfad der Seite bestimmt (`http://<host>:<4502>/content/wknd/language-masters/fr.html`).

1. Navigieren Sie zu „Sites“.
1. Klicken oder tippen Sie auf die Website, für die Sie eine Sprachkopie erstellen möchten.
1. Klicken oder tippen Sie auf **Erstellen** und anschließend auf **Seite**.

   ![Seite erstellen](../assets/create-page.png)

1. Wählen Sie die Seitenvorlage aus und klicken oder tippen Sie auf **Weiter**.
1. Geben Sie in den Feldtyp **Name** den Ländercode im Format `<language-code>` oder `<language-code>_<country-code>` ein, z. B. `en`, `en_US`, `en_us`, `en_GB`, `en_gb`. Geben Sie einen Titel für die Seite ein.

   ![Sprachstammseite erstellen](../assets/create-language-root.png)

1. Klicken oder tippen Sie auf **Erstellen**. Klicken oder tippen Sie im Bestätigungsdialogfeld auf **Fertig**, um zur Sites-Konsole zurückzukehren, oder auf **Öffnen**, um die Sprachkopie zu öffnen.

## Anzeigen des Status der Sprachstämme  {#seeing-the-status-of-language-roots}

AEM hat eine Leiste **Verweise**, die eine Liste der erstellten Sprachstämme anzeigt.

![Sprachstämme](../assets/language-roots.png)

Verwenden Sie die folgende Ansicht, um die Sprachkopien für eine Seite mithilfe der [Leistenauswahl](/help/sites-cloud/authoring/getting-started/basic-handling.md#rail-selector) anzuzeigen.

1. Wählen Sie in der Sites-Konsole eine Seite der Website aus und klicken oder tippen Sie auf **Verweise**.

   ![Offene Verweise-Leiste](../assets/opening-references-rail.png)

1. Klicken oder tippen Sie in der Verweise-Leiste auf **Sprachkopien**. In der Leiste werden die Sprachkopien der Website angezeigt.

## Sprachkopien auf mehreren Ebenen {#multiple-levels}

Sie können Sprachstämme jetzt unter Knoten gruppieren, z. B. nach Region. Diese werden weiterhin als Stämme von Sprachkopien erkannt.

```text
/content
    |- wknd
        |- language-masters
            |- europe
                |- de
                |- fr
                |- it
                |- es
                ]- pt
            |- americas
                |- en
                |- es
                |- fr
                |- pt
            |- asia
                |- ...
            |- africa
                |- ...
            |- oceania
                |- ...
        |- europe
        |- americas
        |- asia
        |- africa
        |- oceania            
```

>[!NOTE]
>
>Hierbei ist nur eine Ebene zulässig. Im folgenden Beispiel ist nicht zulässig, dass die `es`-Seite in eine Sprachkopie aufgelöst wird:
>
>* `/content/wknd/language-masters/en`
>* `/content/wknd/language-masters/americas/central-america/es`

>
> 
Die Sprachkopie `es` wird nicht erkannt, da sie zwei Ebenen (`americas/central-america`) vom Knoten `en` entfernt ist.

>[!TIP]
>
>Bei einer solchen Einrichtung können Sprachstämme einen beliebigen Seitennamen haben. Es muss nicht immer nur der ISO-Code der Sprache sein. AEM prüft stets zuerst den Pfad und den Namen, aber wenn der Seitenname keinen Hinweis auf eine Sprache enthält, überprüft AEM die Eigenschaft `cq:language` der Seite, um die Sprache zu identifizieren.
