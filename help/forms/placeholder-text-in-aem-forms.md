---
title: 'Platzhaltertext in  [!DNL AEM Forms] '
description: Platzhaltertext unterstützt den Benutzer bei der Dateneingabe, wenn das Steuerelement keinen Wert hat. Das könnte ein Beispielwert oder eine kurze Beschreibung des erwarteten Formats sein.
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '206'
ht-degree: 100%

---


# Platzhaltertext in [!DNL AEM Forms] {#placeholder-text-in-aem-forms}

Der Platzhaltertext stellt ein Wort oder einen kurzen Satz dar. Er unterstützt den Benutzer bei der Dateneingabe, wenn das Steuerelement keinen Wert hat. Ein Platzhaltertext könnte ein Beispielwert oder eine kurze Beschreibung des erwarteten Formats sein. Der Platzhaltertext wird gezeigt, bevor der Benutzer einen Text eingibt, und entfernt, wenn der Benutzer einen Wert eingibt oder auswählt.

>[!NOTE]
>
>Der Platzhaltertext muss, falls angegeben, einen Wert enthalten, der keine neuen Zeilenzeichen enthält.

![Datumskomponente mit und ohne Platzhaltertext](assets/dat-picker-place-holder-text.png)

**A.** Datumskomponente mit Platzhaltertext **B.** Datumskomponente ohne Platzhaltertext

[!DNL AEM Forms] unterstützt Platzhaltertext für die Felder vom Typ „Kennwort“, „Datumsauswahl“, „Numerisches Feld“ und „Textfeld“.\
Platzhaltertexte werden für das native HTML5-Datum-Widget nicht unterstützt. Angeben eines Platzhaltertexts:

1. Kicken Sie mit der rechten Maustaste auf eine Komponente, die Platzhaltertext unterstützt, und klicken Sie auf **Bearbeiten**. Das Dialogfeld „Komponente bearbeiten“ wird angezeigt.

1. Öffnen Sie die Registerkarte **Titel und Text**.
1. Geben Sie ein Wort oder einen kurzen Satz im Feld **Platzhaltertext** ein. Klicken Sie auf **OK**.

>[!NOTE]
>
>Platzhaltertext wird in [!DNL Microsoft Internet Explorer 9] nicht unterstützt.

