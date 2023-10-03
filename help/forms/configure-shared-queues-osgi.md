---
title: Wie werden freigegebene Warteschlangen konfiguriert?
description: Erfahren Sie, wie Sie freigegebene Warteschlangen für Forms-zentrierte Workflows für [!DNL AEM Forms] unter OSGi verwenden.
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
source-git-commit: 7e3eb3426002408a90e08bee9c2a8b7a7bfebb61
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 97%

---


# Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers {#share-and-request-access}

Eine Warteschlange ist eine Liste von Elementen im AEM-Posteingang eines Benutzers. Dabei kann es sich um Elemente handeln, die einem Benutzer zugewiesen sind, oder um Elemente, die für die Gruppe freigegeben sind, der ein Benutzer angehört. Sie können auf Ihren Posteingang zugreifen, um das Posteingangselement anzuzeigen und eine Aktion damit auszuführen. Geben Sie beispielsweise ein Element für einen anderen Benutzer frei.

Sie können Ihre Posteingangselemente auch für einen anderen Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente hat, kann er sie beanspruchen und entsprechende Aktionen durchführen. Ebenso können Sie von anderen Benutzern Zugriff auf Posteingangselemente anfordern.

## Voraussetzungen {#pre-requisites}

Der angemeldete Benutzer muss Mitglied der Gruppe [!DNL `workflow-users`] sein. Der Benutzer kann Elemente freigeben oder Zugriff auf Elemente nur von Benutzern anfordern, für die der angemeldete Benutzer über Leserechte verfügt, oder nur von Benutzern, die ein öffentliches Profil aktiviert haben.

## Teilen eines einzelnen oder aller Elemente Ihres Posteingangs mit einem anderen Benutzer

Mit AEM Posteingang können Sie ein einzelnes oder alle Elemente in Ihrem Posteingang für einen anderen Benutzer freigeben.

### Alle Posteingangselemente freigeben

Führen Sie folgende Schritte aus, um alle Elemente in einem Posteingang für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Tippen Sie auf das Symbol ![Posteingang](assets/bell.svg) und dann auf **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Tippen Sie auf das Symbol ![Listenansicht](assets/viewlist.svg) oder ![Kalender](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und dann auf **[!UICONTROL Einstellungen]**. Das Dialogfeld „Einstellungen“ wird angezeigt.
1. Öffnen Sie im Dialogfeld „Einstellungen“ die Registerkarte **[!UICONTROL Freigeben]**.
1. Geben Sie den Namen eines Benutzers in das Textfeld **[!UICONTROL Zugriff auf Ihre Posteingangselemente gewähren]** ein und tippen Sie auf **[!UICONTROL Gewähren]**. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **Benutzername** angezeigt.
1. Tippen Sie auf **[!UICONTROL Speichern]**.

>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Zulassen, dass Verantwortlicher per Freigabe des Posteingangs freigibt](aem-forms-workflow-step-reference.md)** im Schritt **Aufgabe zuweisen**. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

### Freigeben einzelner Elemente

Führen Sie folgende Schritte aus, um ein Posteingangselement für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Tippen Sie auf das Symbol ![Posteingang](assets/bell.svg) und dann auf **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie ein Element aus und tippen Sie auf **[!UICONTROL Freigeben]**. Folgendes Dialogfeld wird angezeigt.
1. Geben Sie den Namen eines Benutzers in das Textfeld „Benutzer hinzufügen, um dieses Element freizugeben“ ein und tippen Sie auf **[!UICONTROL Hinzufügen]**. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **[!UICONTROL Benutzername]** angezeigt.
1. Tippen Sie auf **[!UICONTROL Speichern]**.


>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Zulassen, dass Verantwortlicher explizit im Posteingang freigibt](aem-forms-workflow-step-reference.md)** des Workflow-Schritts **Aufgabe zuweisen**. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

## Anfordern von Zugriff auf Elemente im Posteingang {#request-access}

Sie können Zugriff auf die Posteingangselemente eines anderen Benutzers anfordern. Sobald der Zugriff gewährt ist, können Sie freigegebene Elemente anzeigen, beanspruchen und entsprechende Aktionen durchführen. Führen Sie folgende Schritte aus, um den Zugriff auf Posteingangselemente eines anderen Benutzers anzufordern:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Tippen Sie auf das Symbol ![View Selector](assets/bell.svg) und dann auf **[!UICONTROL Alle anzeigen]**.
1. Tippen Sie auf das Symbol ![View Selector](assets/viewlist.svg) oder ![View Selector](assets/calendar.svg) neben der Schaltfläche **[!UICONTROL Erstellen]** und dann auf **[!UICONTROL Einstellungen]**. Das Dialogfeld „Einstellungen“ wird angezeigt.
1. Geben Sie den Namen eines Benutzers in das Textfeld **[!UICONTROL Zugriff auf Posteingangselemente des Benutzers anfordern]** ein und tippen Sie auf **[!UICONTROL Anfordern]**. Der Benutzer erhält eine Anfrage und der Status der Anfrage wird beim Namen des Benutzers angezeigt. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen.
1. Tippen Sie auf **[!UICONTROL Speichern]**. Die Anfrage wird als Posteingangselement an die Benutzer gesendet. Der Benutzer kann das Element auswählen und auf „Genehmigen“ oder „Ablehnen“ tippen, um den Zugriff zu gewähren oder abzulehnen.


## Anfordern von Elementen, die von anderen Benutzern freigegeben werden {#claim-items}

Sie können erst mit einem freigegebenen Element arbeiten, nachdem Sie es beansprucht haben. Dadurch wird verhindert, dass mehrere Benutzer an einem einzelnen Element arbeiten. Führen Sie folgende Schritte aus, um ein Element zu beanspruchen:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Tippen Sie auf das Posteingangssymbol (![Inbox](assets/bell.svg)) und dann auf **[!UICONTROL Alle anzeigen]**.
1. Tippen Sie auf das Symbol ![Content only](assets/railleft.svg), um die Filterauswahl zu öffnen.
1. Tippen Sie auf die Dropdown-Liste **[!UICONTROL Verantwortlichen auswählen]**, um Benutzer anzuzeigen und auszuwählen, die ihre Posteingangselemente für Sie freigegeben haben.
1. Wählen Sie ein Element aus und tippen Sie auf **[!UICONTROL Beanspruchen]**. Das Element wird Ihrem Posteingang hinzugefügt.

## Freigeben angeforderter Elemente {#release-items}

Sie können erst mit einem freigegebenen Element arbeiten, nachdem Sie es beansprucht haben. Andere Benutzer können Elemente, die Sie beansprucht haben, nicht sehen oder bearbeiten. Wenn Sie mit der Arbeit an einem Element nicht fortfahren können, können Sie es wieder in den Pool freigeben.   Nachdem Sie das Element freigegeben haben, können andere das Element beanspruchen und bearbeiten:

Führen Sie folgende Schritte aus, um ein Element freizugeben:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Tippen Sie auf das Posteingangssymbol (![Inbox](assets/bell.svg)) und dann auf **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie das zu veröffentlichende Element aus und tippen Sie auf **[!UICONTROL Beanspruchung aufheben]**. Das Element wird wieder zum Pool hinzugefügt. Andere können das Element jetzt beanspruchen.

## Beschränkungen {#limitations}

* Die Freigabe von Elementen für eine Gruppe wird nicht unterstützt.
* Die Freigabe von Projektaufgaben wird nicht unterstützt.
