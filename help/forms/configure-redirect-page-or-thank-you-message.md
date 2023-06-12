---
title: Wie konfiguriere ich eine Umleitungsseite oder Dankesnachricht?
description: Erfahren Sie, wie Benutzern eine Dankesnachricht angezeigt oder zu einer Webseite umgeleitet werden kann, die Formularverfasser beim Erstellen des Formulars konfigurieren können.
feature: Adaptive Forms
role: User
level: Intermediate
source-git-commit: b104c7ddd102b3600384bf7472b166131e334c35
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Konfigurieren einer Umleitungsseite {#configuring-redirect-page}

Bei Vorlage einer [Auf Kernkomponenten basierendes adaptives Formular](creating-adaptive-form-core-components.md)können Sie den Benutzer zu einer anderen Webseite umleiten oder eine Nachricht anzeigen. So konfigurieren Sie die Umleitungsseite oder die Dankesnachricht:

1. Öffnen Sie das adaptive Formular zum Bearbeiten.
1. Öffnen Sie die Inhaltsstruktur und wählen Sie die **[!UICONTROL Guide Container]**.
1. Klicken Sie auf die Eigenschaften des Containers für adaptive Formulare ![Eigenschaften des Containers für adaptive Formulare](/help/forms/assets/configure-icon.svg) Symbol. Das Dialogfeld Container für adaptive Formulare zum Konfigurieren von Datenmodellen wird geöffnet.
1. Öffnen Sie die **[!UICONTROL Einsendung]** Registerkarte. Es werden Optionen zum Konfigurieren einer Umleitungsseite oder einer Nachricht angezeigt:

   ![Dialogfeld &quot;Übermittlung&quot;von Guide Container zum Konfigurieren einer Umleitungsseite oder einer Nachricht](/help/forms/assets/adaptive-forms-core-components-redirect-page-or-thank-you-message.png)

   * Um eine Umleitungs-URL zu konfigurieren, wählen Sie für die Option &quot;Beim Senden&quot;die Option **[!UICONTROL Option &quot;Zur URL umleiten&quot;]** und geben Sie eine absolute Adresse oder eine Umleitungs-URL oder einen relativen Pfad zu einer AEM Sites-Seite an.

   * Um eine benutzerspezifische oder Dankesnachricht zu konfigurieren, wählen Sie die **[!UICONTROL Nachricht anzeigen]** und geben Sie im Feld Nachrichteninhalt eine Nachricht ein. Es handelt sich um ein Rich-Text-Feld. Sie können die Vollbildoption verwenden, um alle verfügbaren Rich-Text-Elemente anzuzeigen.

Formularersteller können für jedes Formular eine Seite konfigurieren, zu der die Formularbenutzer nach dem Absenden eines Formulars umgeleitet werden.

**Verwandt**

* [Konfigurieren der Umleitungsseite (Foundation Forms)](configuring-redirect-page.md)
