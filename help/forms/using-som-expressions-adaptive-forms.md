---
title: Verwendung von SOM-Ausdrücken in Adaptive Forms
description: Erfahren Sie, wie Sie SOM-Ausdrücke eines Bedienfelds in Adaptive Forms extrahieren.
uuid: c5d55aff-fb69-4a1c-96ea-fb3f9322cbb0
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 13f00bb2-561f-4d64-8829-292c663abeab
docset: aem65
source-git-commit: 92f89243b79c6c2377db3ca2b8ea244957416626
workflow-type: tm+mt
source-wordcount: '347'
ht-degree: 75%

---


# Verwenden von SOM-Ausdrücken in adaptiven Formularen {#using-som-expressions-in-adaptive-forms}

Adaptive Formulare werden als AEM-Seite modelliert, die im AEM-Repository als JCR-Inhaltstruktur repräsentiert wird. Das Schlüsselelement der Inhaltsstruktur ist der Knoten guideContainer . Unter &quot;guideContainer&quot;befindet sich &quot;rootPanel&quot;, das verschachtelte Bedienfelder und Felder enthalten kann.

Sie können ein Skriptobjektmodell (SOM) verwenden, um Werte, Eigenschaften und Methoden innerhalb eines bestimmten Dokumentobjektmodells (DOM) zu referenzieren. Ein DOM organisiert die Speicherobjekte und -eigenschaften in einer Baumstruktur. Ein SOM-Ausdruck verweist auf Felder/Zeichenelemente und Bereiche.

Im folgenden Bild ist eine Knotenstruktur abgebildet, in das ein adaptives Formular übertragen wird, wenn Sie einem Formular Komponenten hinzufügen. Sie können beispielsweise dem Stammbereich einen Bereich und diesem dann ein Optionsfeld hinzufügen. Der Bereich wird dann zur Laufzeit in ein DOM transformiert. Der SOM-Ausdruck für das Optionsfeld im adaptiven Formular ist als `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]` angegeben.

![DOM-Baumstruktur](assets/hierarchy.png)

DOM-Baumstruktur

Einem SOM-Ausdruck für ein beliebiges Element in einem adaptiven Formular wird das Präfix `guide[0].guide1[0]` vorangestellt. Die Position einer Komponente in der hierarchischen Knotenstruktur wird zum Ableiten des entsprechenden SOM-Ausdrucks verwendet.

![DOM-Baumstruktur mit zwei Optionsfeldern](assets/hierarchy_radio_button.png)

DOM-Baumstruktur mit zwei Optionsfeldern

Der SOM-Ausdruck ändert sich, wenn Sie die Position der Optionsfelder im adaptiven Formular ändern. Im Autorenmodus können Sie den SOM-Ausdruck eines Felds oder Elements in [!DNL AEM Forms] mithilfe der Option „SOM-Ausdruck anzeigen“ anzeigen. Die Option wird auf dem Bereich angezeigt und wenn Sie mit der rechten Maustaste auf das Feld oder Element klicken.

![Extrahieren von SOM-Ausdrücken in einem adaptiven Formular](assets/som-expressions.png)

Extrahieren von SOM-Ausdrücken in einem adaptiven Formular

Innerhalb von Bereichen können Sie von der Bereichssymbolleiste aus auf die Funktion zugreifen. Die Funktion vereinfacht die Skripterstellung für Autoren adaptiver Formulare.

![Extrahieren von SOM-Ausdrücken mithilfe der Bereichssymbolleiste](assets/som-expression.png)

Extrahieren von SOM-Ausdrücken mithilfe der Bereichssymbolleiste

Einige in [GuideBridge](https://helpx.adobe.com/de/aem-forms/6/javascript-api/GuideBridge.html) aufgeführte APIs verwenden den SOM-Ausdruck eines Elements. Um beispielsweise den Fokus auf ein bestimmtes Feld in einem adaptiven Formular zu legen, muss der entsprechende SOM-Ausdruck an die `getFocus`-API in `guideBridge` übergeben werden.
