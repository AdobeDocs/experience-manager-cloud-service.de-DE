---
title: Konfigurieren einer Umleitungsseite oder Dankesnachricht
description: Erfahren Sie, wie Benutzenden eine Dankesnachricht angezeigt oder sie auf eine Webseite weitergeleitet werden können, die Formularautorinnen bzw. -autoren bei der Erstellung des Formulars konfigurieren können.
feature: Adaptive Forms, Edge Delivery Services
role: User
level: Intermediate
source-git-commit: 1be7bafc1d93a65a81eeb2f7e86cac33cde7aa35
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 50%

---

# Konfigurieren der Weiterleitung oder Dankesnachricht

In Formularen, die mit dem universellen Editor erstellt wurden, können Formularautoren konfigurieren, was geschieht, nachdem ein Benutzer ein Formular sendet. Sie können entweder eine Dankesnachricht anzeigen oder den Benutzer auf eine bestimmte Web-Seite umleiten, indem Sie die Registerkarte Übermittlung in der Erweiterung Formulareigenschaften bearbeiten verwenden.

Sie können die Dankesnachricht oder Umleitungs-URLs für Formulare konfigurieren, die im universellen Editor erstellt wurden, indem Sie die Registerkarte **Übermittlung** der Erweiterung **AEM Form Properties** verwenden.

## Voraussetzungen

Sie können die Übermittlungsaktion für Formulare, die im universellen Editor erstellt wurden, über die Registerkarte **Übermittlung** der Erweiterung **Formulareigenschaften bearbeiten** konfigurieren.

![Symbol für Formulareigenschaften](/help/forms/assets/ue-form-properties-icon.png)

![Formulareigenschaften des universellen Editors](/help/forms/assets/ue-form-properties.png)

>[!NOTE]
>
>* Wenn das Symbol **Formulareigenschaften** in der Benutzeroberfläche des universellen Editors nicht angezeigt wird, aktivieren Sie die Erweiterung **Formulareigenschaften bearbeiten** in der Extension Manager.
>* Informationen zum Aktivieren oder Deaktivieren von Erweiterungen im universellen Editor finden [ im Artikel ](https://developer.adobe.com/uix/docs/extension-manager/feature-highlights/#enablingdisabling-extensions)Extension Manager-Feature-Highlights&rbrace;.

## Konfigurieren der Umleitung oder Dankesnachricht

Bei der Übermittlung eines Formulars können Sie den Benutzer auf eine andere Web-Seite weiterleiten oder eine Nachricht anzeigen.

So konfigurieren Sie die Umleitungsseite oder die Dankesnachricht:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie den **[!UICONTROL Guide-Container]**.
1. Klicken Sie auf das Symbol für die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg). Das Dialogfeld der Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
1. Öffnen Sie die Registerkarte **[!UICONTROL Übermittlung]**. Es werden Optionen zum Konfigurieren einer Umleitungsseite oder einer Nachricht angezeigt:

   ![Übermittlungsdialog des Guide-Containers zur Konfiguration einer Weiterleitungsseite oder einer Nachricht](/help/forms/assets/adaptive-forms-core-components-redirect-page-or-thank-you-message.png)

**Konfigurieren von Umleitungs-URLs**

* Um eine Umleitungs-URL zu konfigurieren, wählen Sie für die Senden-Option die Option **[!UICONTROL Zu URL umleiten]** aus und geben Sie eine absolute Adresse, eine Umleitungs-URL oder einen relativen Pfad einer AEM Sites-Seite an.

![redirect](/help/edge/docs/forms/universal-editor/assets/redirect-ue.png)

**Dankesnachricht konfigurieren**

* Um eine benutzerdefinierte Nachricht oder eine Dankesnachricht zu konfigurieren, wählen Sie die Option **[!UICONTROL Nachricht anzeigen]**, und geben Sie eine Nachricht in das Feld „Nachrichteninhalt“ ein. Es handelt sich um ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.

![Danke](/help/edge/docs/forms/universal-editor/assets/thankyou-ue.png)

Menschen, die ein Formular verfassen, können für jedes Formular eine Seite konfigurieren, zu der die Benutzenden nach dem Absenden eines Formulars weitergeleitet werden.
