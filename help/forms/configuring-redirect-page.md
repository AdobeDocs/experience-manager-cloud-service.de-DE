---
title: Wie wird eine Umleitungsseite konfiguriert?
description: Erfahren Sie, wie Benutzer zu einer Webseite umgeleitet werden können, die Formularersteller beim Erstellen des Formulars konfigurieren können.
feature: Adaptive Forms
role: User
level: Intermediate
exl-id: e4dc01d2-7c89-4bd8-af0a-1d2df4676a9a
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '186'
ht-degree: 100%

---

# Konfigurieren einer Umleitungsseite {#configuring-redirect-page}

Formularersteller können für jedes Formular eine Seite konfigurieren, zu der die Formularbenutzer nach dem Absenden eines Formulars umgeleitet werden.

1. Wählen Sie im Bearbeitungsmodus eine Komponente aus, klicken Sie dann auf ![field-level](assets/select_parent_icon.svg) > **[!UICONTROL Container für ein adaptives Formular]** und anschließend auf ![cmppr](assets/configure-icon.svg).

1. Klicken Sie in der Seitenleiste auf **[!UICONTROL Übermittlung]**.

1. Geben Sie die URL der Umleitungsseite unter **[!UICONTROL Umleitungs-URL/Pfad]** im Abschnitt **[!UICONTROL Übermittlung]** an.
1. Optional können Sie unter „Übermittlungsaktion“ für die Aktion „An REST-Endpunkt übermitteln“ den Parameter konfigurieren, der zur Umleitungsseite weitergeleitet wird.

   ![Konfigurieren der Umleitungsseite](assets/redirect-url.png)

   Konfigurieren der Umleitungsseite

Formularersteller können folgende Parameter verwenden, die zur Dankeseite weitergeleitet werden. Bei allen verfügbaren Übermittlungsaktionen werden `status`- und `owner`-Parameter übergeben. Neben diesen beiden Parametern werden für die folgenden Übermittlungsaktionen einige weitere Parameter übergeben:

* **[!UICONTROL An REST-Endpunkt übermitteln]**: Parameter, die für die Zuordnung feldinterner Werte zu Parametern hinzugefügt wurden, werden weitergeleitet. Die Parameter `status` und `owner` werden bei dieser Übermittlungsaktion nicht übergeben. Weitere Informationen finden Sie unter [Konfigurieren der Übermittlungsaktion „An REST-Endpunkt übermitteln“](configuring-submit-actions.md).
