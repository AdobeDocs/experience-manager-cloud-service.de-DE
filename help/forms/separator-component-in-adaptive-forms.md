---
title: Was ist eine Trennzeichenkomponente in adaptiven Formularen?
description: Die Trennzeichenkomponente in adaptiven Formularen hilft, Abschnitte eines Formulars visuell zu trennen.
feature: Adaptive Forms, Foundation Components
role: User
exl-id: 1b7857f9-b201-43ca-870d-42a09c441d9a
source-git-commit: a9adbb1886dcfedfc3fccb6f56939c46ba1365ee
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 100%

---

# Trennzeichenkomponente in adaptiven Formularen {#separator-component-in-adaptive-forms}

Sie können die Trennzeichenkomponente verwenden, um Bereiche eines Formulars visuell zu trennen. Sie können die Gesamtdarstellung und den Stil einer Trennzeichenkomponente definieren, indem Sie die folgenden Eigenschaften einer Trennzeichenkomponente angeben:

* **Elementname:** Gibt den Namen der Komponente an. Die SOM-Ausdrücke richten sich an die Komponente mit einem Wert, der im Feld „Elementname“ angegeben ist.
* **Stärke:** Gibt die Stärke der Trennzeichenkomponente in Pixel an.

* **CSS-Klasse:** Gibt die benutzerdefinierte CSS-Klasse für die Trennzeichenkomponente an.

* **Inline-Stile:** Mit [!DNL AEM Forms] können Sie jetzt CSS-Inline-Stile auf individuelle adaptive Formularkomponenten anwenden und eine Vorschau der Änderungen in Echtzeit anzeigen.

Im Layout-Modus können Sie die Anzahl der Spalten festlegen, die die Trennzeichenkomponente umfasst. Weitere Informationen finden Sie unter [Verwenden des Layout-Modus, um die Größe von Komponenten anzupassen](resize-using-layout-mode.md).

Angeben der Eigenschaften einer Trennzeichenkomponente:

1. Wählen Sie eine Trennzeichenkomponente und dann ![cmppr](assets/cmppr.png) aus. Die Eigenschaften werden in der Seitenleiste angezeigt.
1. Klicken Sie auf eine Registerkarte im Abschnitt „Inline-CSS-Eigenschaften“, um CSS-Eigenschaften festzulegen. Beispiel: Klicken Sie auf der Registerkarte „Feld“ auf **Element hinzufügen**. Es wird eine Zeile mit zwei Feldern hinzugefügt.
1. Geben Sie im ersten Feld von links eine CSS3-Eigenschaft an, die Sie anwenden möchten. Beispielsweise **Rahmen**. Sie können eine Eigenschaft auch auswählen, indem Sie auf den Pfeil nach unten klicken. Die Dropdown-Liste ist nicht vollständig und Sie können einen beliebigen unterstützten CSS3-Eigenschaftennamen in dieses Feld eingeben.
1. Geben Sie im angrenzenden Feld einen gültigen Wert für die angegebene CSS3-Eigenschaft an. Beispielsweise **3 pixels solid black**.
1. Klicken Sie auf **Element hinzufügen**, um eine andere Eigenschaft und deren Wert anzugeben.
1. Klicken Sie auf **Vorschau**, damit Sie die Änderungen im Formular sehen können.
1. Führen Sie einen der folgenden Schritte aus:
   * Bestätigen Sie die Änderungen, indem Sie auf **OK** klicken.
   * Verlassen Sie das Dialogfeld ohne Änderungen, indem Sie auf **Abbrechen** klicken.
