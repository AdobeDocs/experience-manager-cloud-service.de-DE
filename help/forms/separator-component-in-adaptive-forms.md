---
title: Was ist eine Trennzeichenkomponente in Adaptive Forms?
description: Die Trennzeichenkomponente in Adaptive Forms hilft, Abschnitte eines Formulars visuell zu trennen.
uuid: f8d2aed3-52aa-437f-bfe3-0c8779e7986c
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 34%

---


# Trennzeichenkomponente in adaptiven Formularen {#separator-component-in-adaptive-forms}

Sie können die Trennzeichenkomponente verwenden, um Bereiche eines Formulars visuell zu trennen. Sie können die Gesamtdarstellung und den Stil einer Trennzeichenkomponente definieren, indem Sie die folgenden Eigenschaften der Trennzeichenkomponente angeben:

* **Elementname:** Gibt den Namen der Komponente an. Die SOM-Ausdrücke adressieren die Komponente mit einem Wert, der im Feld &quot;Elementname&quot;angegeben ist.
* **Stärke:** Gibt die Stärke der Trennzeichenkomponente in Pixel an.

* **CSS-Klasse:** Gibt die benutzerdefinierte CSS-Klasse für die Trennzeichenkomponente an.

* **Inline-Stile:** Mit [!DNL AEM Forms] können Sie jetzt CSS-Inline-Stile auf individuelle adaptive Formularkomponenten anwenden und eine Vorschau der Änderungen in Echtzeit anzeigen.

Im Layout-Modus können Sie die Anzahl der Spalten festlegen, die die Trennzeichenkomponente umfasst. Weitere Informationen finden Sie unter [Verwenden des Layout-Modus, um die Größe von Komponenten anzupassen](resize-using-layout-mode.md).

So legen Sie die Eigenschaften einer Trennzeichenkomponente fest:

1. Wählen Sie eine Trennzeichenkomponente aus und wählen Sie ![cmppr](assets/cmppr.png). Die Eigenschaften werden in der Seitenleiste geöffnet.
1. Klicken Sie auf eine Registerkarte im Abschnitt Inline-CSS-Eigenschaften , damit Sie CSS-Eigenschaften angeben können. Beispiel: a. Klicken Sie auf der Registerkarte Feld auf **Element hinzufügen**. Eine Zeile mit zwei Feldern wird hinzugefügt.
1. Geben Sie im ersten Feld links eine CSS3-Eigenschaft an, die Sie anwenden möchten. Beispiel: **border**. Sie können auch eine Eigenschaft auswählen, indem Sie auf die Nach-unten-Taste klicken. Die Dropdown-Liste ist nicht vollständig und Sie können einen beliebigen unterstützten CSS3-Eigenschaftennamen in dieses Feld eingeben.
1. Geben Sie im angrenzenden Feld einen gültigen Wert für die angegebene CSS3-Eigenschaft an. Beispiel: **3 Pixel Schwarz**.
1. Klicken Sie auf **Element hinzufügen**, um eine andere Eigenschaft und deren Wert anzugeben.
1. Klicks **Vorschau** sodass Sie die Änderungen im Formular sehen können.
1. Führen Sie einen der folgenden Schritte aus:
   * Bestätigen Sie die Änderungen durch Klicken auf **OK**
   * Beenden Sie das Dialogfeld ohne Änderungen, indem Sie auf **Abbrechen**.

