---
title: Wie können SOM-Ausdrücke in adaptiven Formularen verwendet werden?
description: Erfahren Sie, wie Sie SOM-Ausdrücke eines Bereichs in adaptiven Formularen extrahieren.
feature: Adaptive Forms, Foundation Components
role: User
exl-id: 5c30d5ca-12b8-4cc6-aa95-bde562419827
source-git-commit: a9adbb1886dcfedfc3fccb6f56939c46ba1365ee
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 100%

---

# Verwenden von SOM-Ausdrücken in adaptiven Formularen {#using-som-expressions-in-adaptive-forms}

Adaptive Formulare werden als AEM-Seite modelliert, die im AEM-Repository als JCR-Inhaltstruktur repräsentiert wird. Das Schlüsselelement der Inhaltsstruktur ist der Knoten „guideContainer“. Unter „guideContainer“ befindet sich der Knoten „rootPanel“, der verschachtelte Bedienfelder und Felder enthalten kann.

Sie können ein Skripting-Objektmodell (SOM) verwenden, um Werte, Eigenschaften und Methoden innerhalb eines bestimmten Dokumentobjektmodells (DOM) zu referenzieren. Ein DOM organisiert die Speicherobjekte und Eigenschaften in einer hierarchischen Baumstruktur. Ein SOM-Ausdruck verweist auf Felder/Zeichenelemente und Bedienfelder.

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
