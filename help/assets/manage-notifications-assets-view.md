---
title: Verwalten von Benachrichtigungen
description: Überwachen Sie die Vorgänge, die mit den im Repository verfügbaren Assets oder Ordnern durchgeführt werden, mithilfe der Assets-Ansichtsbenachrichtigungen.
exl-id: 1fe6a845-37d5-43c2-bb96-c5b149c238ab
feature: Assets Essentials
role: User, Leader
source-git-commit: e3fd0fe2ee5bad2863812ede2a294dd63864f3e2
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 100%

---

# Überwachen von Assets, Ordnern und Sammlungen {#watch-assets-folders}

| [Best Practices für die Suche](/help/assets/search-best-practices.md) | [Best Practices für Metadaten](/help/assets/metadata-best-practices.md) | [Content Hub](/help/assets/product-overview.md) | [Dynamic Media mit OpenAPI-Funktionen](/help/assets/dynamic-media-open-apis-overview.md) | [Entwicklerdokumentation zu AEM Assets](https://developer.adobe.com/experience-cloud/experience-manager-apis/) |
| ------------- | --------------------------- |---------|----|-----|

Assets-Ansichtsbenachrichtigungen ermöglichen es Ihnen, die Vorgänge zu überwachen, die mit den im Repository verfügbaren Assets, Ordnern oder Sammlungen durchgeführt werden. Sie müssen den Inhalt auswählen und abonnieren, für den die Benachrichtigungen an Sie gesendet werden sollen. Sie können auch die Kategorien konfigurieren, für die die Benachrichtigungen an Sie gesendet werden.

## Abonnieren von Benachrichtigungskategorien {#subscribe-to-notification-categories}

Sie können aus einer Liste von Kategorien auswählen und diese abonnieren, um Benachrichtigungen zu erhalten. Die Assets-Ansicht sendet Ihnen die Benachrichtigungen nur für die Kategorien, die Sie aus den verfügbaren Optionen ausgewählt haben:

<table>
    <tbody>
     <tr>
      <th><strong>Benachrichtigungskategorie</strong></th>
      <th><strong>Beschreibung</strong></th>
     </tr>
     <tr>
      <td>Anfragen</td>
      <td>Wenn Sie einem Benutzer eine Aufgabe zuweisen, erhalten Sie Benachrichtigungen, wenn von diesem Benutzer Aktionen zu dieser Aufgabe durchgeführt werden.</td>
     </tr>
     <tr>
      <td>Mir zugewiesen</td>
      <td>Sie erhalten eine Benachrichtigung, wenn Ihnen eine Aufgabe von einem anderen Benutzer zugewiesen wurde.</td>
     </tr>
     <tr>
      <td>Kommentar zu abonnierten Inhalten</td>
      <td>Sie erhalten eine Benachrichtigung, wenn ein Nutzer einen Kommentar zu Ihrem abonnierten Asset abgibt.</td>
     </tr>
     <tr>
      <td>Löschung abonnierter Inhalte</td>
      <td>Sie erhalten eine Benachrichtigung, wenn Benutzende Ihr abonniertes Asset, Ihren abonnierten Ordner oder Ihre abonnierte Sammlung löschen.</td>
     </tr>
     <tr>
      <td>Externe Freigabe abonnierter Inhalte</td>
      <td>Sie erhalten eine Benachrichtigung, wenn Benutzende einen öffentlichen Link für Ihr abonniertes Asset, Ihren abonnierten Ordner oder Ihre abonnierte Sammlung erstellen.</td>
     </tr>
     <tr>
      <td>Änderung von abonnierten Inhalten</td>
      <td>Sie erhalten eine Benachrichtigung, wenn ein Benutzer eine neue Version für Ihr abonniertes Asset erstellt.</td>
     </tr>
     <tr>
      <td>Verschieben/Umbenennen abonnierter Inhalte</td>
      <td>Sie erhalten eine Benachrichtigung, wenn ein Benutzer Ihr abonniertes Asset oder Ihren Ordner verschiebt oder umbenennt.</td>
     </tr>
     <tr>
      <td>Aktualisierungen von abonnierten Ordnern und Sammlungen</td>
      <td>Sie erhalten eine Benachrichtigung, wenn Benutzende ein Asset zu einem abonnierten Ordner oder einer abonnierten Sammlung hinzufügt oder daraus entfernen.</td>
     </tr>    
    </tbody>
   </table>

So abonnieren Sie die Benachrichtigungskategorien:

1. Klicken Sie in der Benutzeroberfläche der Assets-Ansicht auf das ![Glockensymbol](assets/bell-icon.svg) am rechten Ende der Menüleiste.

1. Klicken Sie auf das Symbol ![Einstellungen](assets/settings-icon.svg), um die Seite [!UICONTROL Experience Cloud-Einstellungen] anzuzeigen.

1. Klicken Sie auf die Option **[!UICONTROL Benachrichtigungen]** im linken Fensterbereich.

1. Navigieren Sie im Abschnitt **[!UICONTROL Benachrichtigungen]** zum Abschnitt [!UICONTROL Assets-Ansicht] und vergewissern Sie sich, dass die Umschaltoption auf EIN geschaltet ist.

   ![Benachrichtigungen in der Assets-Ansicht](assets/enable-notifications.png)

1. Klicken Sie auf **[!UICONTROL Anpassen]**, um die Benachrichtigungskategorien anzuzeigen.
   ![Benachrichtigungen in der Assets-Ansicht](assets/enable-notification-categories.png)

1. Wählen Sie die Benachrichtigungskategorien aus, für die Sie benachrichtigt werden möchten.

## Beobachten oder Nicht-Beobachten von Ordnern, Assets oder Sammlungen {#watch-unwatch-assets}

Nachdem Sie [die Benachrichtigungskategorien abonniert haben](#subscribe-to-notification-categories), müssen Sie den Inhalt abonnieren, damit Sie Benachrichtigungen erhalten.

>[!NOTE]
>
>* Für die Benachrichtigungskategorien **[!UICONTROL Anfragen]** und **[!UICONTROL Mir zugewiesen]** müssen Sie den Inhalt nicht abonnieren, nachdem Sie die Benachrichtigungskategorien abonniert haben. Sie werden automatisch benachrichtigt, wenn Sie eine Anfrage erstellen oder wenn Ihnen eine Aufgabe zugewiesen wird.
>* Die Assets-Ansicht sendet nur Benachrichtigungen, wenn andere Menschen Aktionen für abonnierte Inhalte ausführen. Sie erhalten keine Benachrichtigungen über die Aktionen, die Sie für den abonnierte Inhalte ausführen.

Um den Inhalt zu abonnieren, wählen Sie den zu abonnierenden Ordner, das zu abonnierende Asset oder die zu abonnierende Kollektion und klicken Sie auf **[!UICONTROL Ansehen]**.

Die Assets-Ansicht zeigt eine Erfolgsmeldung an. Sie können auf **[!UICONTROL Zu den Benachrichtigungseinstellungen gehen]** klicken, was in der Erfolgsmeldung verfügbar ist, um Ihr [Abonnement für Benachrichtigungskategorien](#subscribe-to-notification-categories) zu bearbeiten.

![Benachrichtigungen in der Assets-Ansicht](assets/watch-assets.png)

Die Assets-Ansicht sendet jetzt Benachrichtigungen für die abonnierten Kategorien. Sie können auch mehrere Assets, Ordner oder Kollektionen auswählen und auf **[!UICONTROL Ansehen]** klicken, um Zeit zu sparen. Wenn Sie jedoch mehrere Entitäten auswählen, von denen einige bereits abonniert wurden, wird die Option **[!UICONTROL Ansehen]** nicht angezeigt.

Um ein Abonnement zu kündigen, wählen Sie das abonnierte Asset, den abonnierten Ordner oder die abonnierte Kollektion aus und klicken Sie auf **[!UICONTROL Nicht mehr beobachten]**.

## Anzeigen von Benachrichtigungen {#view-notifications}

Die Benachrichtigungen werden in der Benutzeroberfläche der Assets-Ansicht am rechten Ende der Menüleiste angezeigt.

![Benachrichtigungen in der Assets-Ansicht](assets/notifications-assets-essentials.png)

Wenn Sie auf eine Benachrichtigung klicken, gelangen Sie in der Assets-Ansicht zum entsprechenden Asset oder Ordner, worauf sich die Benachrichtigung bezieht.
