---
title: Wie kann Platzhaltertext zu Formularfeldern hinzugefügt werden?
description: Platzhaltertext soll Benutzern bei der Dateneingabe helfen, wenn das Steuerelement keinen Wert hat. Es kann sich um einen Beispielwert oder eine kurze Beschreibung des erwarteten Formats handeln.
source-git-commit: d33c7278d16a8cce76c87b606ca09aa91f1c3563
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 57%

---


# Platzhaltertext in [!DNL AEM Forms] {#placeholder-text-in-aem-forms}

Der Platzhaltertext stellt ein Wort oder einen kurzen Satz dar. Sie soll den Benutzer bei der Dateneingabe unterstützen, wenn das Steuerelement keinen Wert hat. Ein Platzhaltertext kann ein Beispielwert oder eine kurze Beschreibung des erwarteten Formats sein. Der Platzhaltertext wird gezeigt, bevor der Benutzer einen Text eingibt, und entfernt, wenn der Benutzer einen Wert eingibt oder auswählt.

>[!NOTE]
>
>Der Platzhaltertext muss, falls angegeben, einen Wert enthalten, der keine neuen Zeilenzeichen enthält.

![Datumskomponente mit und ohne Platzhaltertext](assets/dat-picker-place-holder-text.png)

**A.** Datumskomponente mit Platzhaltertext **B.** Datumskomponente ohne Platzhaltertext

[!DNL AEM Forms] unterstützt Platzhaltertext für die Felder vom Typ „Kennwort“, „Datumsauswahl“, „Numerisches Feld“ und „Textfeld“.\
Platzhaltertexte werden für das native HTML5-Datum-Widget nicht unterstützt. Angeben eines Platzhaltertexts:

1. Klicken Sie mit der rechten Maustaste auf eine Komponente, die Platzhaltertext unterstützt, und klicken Sie auf **Bearbeiten**. Das Dialogfeld „Komponente bearbeiten“ wird angezeigt.

1. Öffnen Sie die Registerkarte **Titel und Text**.
1. Geben Sie ein Wort oder einen kurzen Satz im Feld **Platzhaltertext** ein. Klicken Sie auf **OK**.

>[!NOTE]
>
>Platzhaltertext wird in [!DNL Microsoft Internet Explorer 9] nicht unterstützt.

