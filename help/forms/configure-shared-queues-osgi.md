---
title: Konfigurieren freigegebener Warteschlangen
description: Erfahren Sie, wie Sie freigegebene Warteschlangen für Forms-zentrierte Workflows für [!DNL AEM Forms] unter OSGi verwenden.
topic-tags: process
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
source-git-commit: 2d4ffd5518d671a55e45a1ab6f1fc41ac021fd80
workflow-type: tm+mt
source-wordcount: '839'
ht-degree: 76%

---


# Freigeben und Anfordern des Zugriffs auf Posteingangselemente eines Benutzers {#share-and-request-access}

Eine Warteschlange ist eine Liste von Elementen im AEM-Posteingang eines Benutzers. Dabei kann es sich um Elemente handeln, die einem Benutzer zugewiesen sind, oder um Elemente, die für die Gruppe freigegeben sind, der ein Benutzer angehört. Sie können auf Ihren Posteingang zugreifen, um das Posteingangselement anzuzeigen und eine Aktion dafür auszuführen. Geben Sie beispielsweise ein Element für einen anderen Benutzer frei.

Sie können Ihre Posteingangselemente auch für einen anderen Benutzer freigeben. Sobald ein anderer Benutzer Zugriff auf Ihre Posteingangselemente hat, kann er sie beanspruchen und entsprechende Aktionen durchführen. Ebenso können Sie von anderen Benutzern Zugriff auf Posteingangselemente anfordern.

## Voraussetzungen {#pre-requisites}

Der angemeldete Benutzer muss Mitglied der Gruppe [!DNL `workflow-users`] sein. Der Benutzer kann Elemente freigeben oder Zugriff auf Elemente nur von Benutzern anfordern, für die der angemeldete Benutzer über Leserechte verfügt, oder nur von Benutzern, die ein öffentliches Profil aktiviert haben.

## Teilen eines einzelnen oder aller Elemente Ihres Posteingangs mit einem anderen Benutzer

Beim AEM-Posteingang können Sie einzelne oder alle Elemente in Ihrem Posteingang für andere Benutzende freigeben.

### Alle Posteingangselemente freigeben

Führen Sie folgende Schritte aus, um alle Elemente in einem Posteingang für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Wählen Sie die ![Posteingang](assets/bell.svg) Symbol und wählen Sie **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie die ![Ansichtauswahl](assets/viewlist.svg) oder ![Ansichtauswahl](assets/calendar.svg) Symbol neben **[!UICONTROL Erstellen]** Schaltfläche und wählen Sie **[!UICONTROL Einstellungen]**. Das Dialogfeld „Einstellungen“ wird angezeigt.
1. Öffnen Sie im Dialogfeld „Einstellungen“ die Registerkarte **[!UICONTROL Freigeben]**.
1. Geben Sie den Namen eines Benutzers im **[!UICONTROL Zugriff auf Ihre Posteingangselemente gewähren]** Textfeld und wählen Sie **[!UICONTROL Zuschuss]**. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **Benutzername** angezeigt.
1. Wählen Sie **[!UICONTROL Speichern]** aus.

>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Zulassen, dass Verantwortlicher per Freigabe des Posteingangs freigibt](aem-forms-workflow-step-reference.md)** im Schritt **Aufgabe zuweisen**. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

### Freigeben einzelner Elemente

Führen Sie folgende Schritte aus, um ein Posteingangselement für einen anderen Benutzer freizugeben:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Wählen Sie die ![Posteingang](assets/bell.svg) Symbol und wählen Sie **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Element auswählen und **[!UICONTROL Freigeben]**. Ein Dialogfeld wird angezeigt.
1. Geben Sie den Namen eines Benutzers in das Textfeld Benutzer hinzufügen, um dieses Element freizugeben ein und wählen Sie **[!UICONTROL Hinzufügen]**. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen. Alle Benutzer mit Zugriff auf Ihre Elemente werden im Abschnitt **[!UICONTROL Benutzername]** angezeigt.
1. Wählen Sie **[!UICONTROL Speichern]** aus.


>[!NOTE]
>
>(Nur für Forms-zentrierte Workflow-Elemente) Aktivieren Sie die Option **[Zulassen, dass Verantwortlicher explizit im Posteingang freigibt](aem-forms-workflow-step-reference.md)** des Workflow-Schritts **Aufgabe zuweisen**. Für andere Benutzer werden nur Elemente angezeigt, für die die oben genannte Option aktiviert ist.

## Anfordern von Zugriff auf Elemente im Posteingang {#request-access}

Sie können Zugriff auf die Posteingangselemente eines anderen Benutzers anfordern. Sobald der Zugriff gewährt ist, können Sie freigegebene Elemente anzeigen, beanspruchen und entsprechende Aktionen durchführen. Führen Sie folgende Schritte aus, um den Zugriff auf Posteingangselemente eines anderen Benutzers anzufordern:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Wählen Sie die ![Ansichtauswahl](assets/bell.svg) Symbol und wählen Sie **[!UICONTROL Alle anzeigen]**.
1. Wählen Sie die ![Ansichtauswahl](assets/viewlist.svg) oder ![Ansichtauswahl](assets/calendar.svg) Symbol neben **[!UICONTROL Erstellen]** Schaltfläche und wählen Sie **[!UICONTROL Einstellungen]**. Das Dialogfeld „Einstellungen“ wird angezeigt.
1. Geben Sie den Namen eines Benutzers im **[!UICONTROL Anfordern des Zugriffs auf Inbox-Elemente des Benutzers]** Textfeld und wählen Sie **[!UICONTROL Anfrage]**. Der Benutzer erhält eine Anfrage und der Status der Anfrage wird beim Namen des Benutzers angezeigt. Wiederholen Sie den Schritt, um weitere Benutzer hinzuzufügen.
1. Wählen Sie **[!UICONTROL Speichern]** aus. Die Anfrage wird als Posteingangselement an die Benutzer gesendet. Der Benutzer kann das Element auswählen und die Option Genehmigen oder Ablehnen wählen, um den Zugriff zu gewähren oder abzulehnen.


## Anfordern von Elementen, die von anderen Benutzern freigegeben werden {#claim-items}

Sie können erst mit einem freigegebenen Element arbeiten, nachdem Sie es beansprucht haben. Dadurch wird verhindert, dass mehrere Benutzer an einem einzelnen Element arbeiten. Führen Sie folgende Schritte aus, um ein Element zu beanspruchen:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Auswählen des Posteingangs ![Posteingang](assets/bell.svg) Symbol und wählen Sie **[!UICONTROL Alle anzeigen]**.
1. Wählen Sie die ![Nur Inhalt](assets/railleft.svg) -Symbol, um die Filterauswahl zu öffnen.
1. Wählen Sie die **[!UICONTROL Bevollmächtigten auswählen]** in der Dropdown-Liste, um Benutzer anzuzeigen und auszuwählen, die ihre Inbox-Elemente für Sie freigegeben haben.
1. Element auswählen und **[!UICONTROL Anspruch]**. Das Element wird Ihrem Posteingang hinzugefügt.

## Freigeben angeforderter Elemente {#release-items}

Sie können erst mit einem freigegebenen Element arbeiten, nachdem Sie es beansprucht haben. Andere Benutzer können Elemente, die Sie beansprucht haben, nicht sehen oder bearbeiten. Wenn Sie mit der Arbeit an einem Element nicht fortfahren können, können Sie es wieder in den Pool freigeben.   Nachdem Sie das Element freigegeben haben, können andere das Element beanspruchen und bearbeiten:

Führen Sie folgende Schritte aus, um ein Element freizugeben:

1. Melden Sie sich bei Ihrer AEM-Autoreninstanz an. Auswählen des Posteingangs ![Posteingang](assets/bell.svg) Symbol und wählen Sie **[!UICONTROL Alle anzeigen]**. Eine Liste Ihrer Posteingangselemente wird angezeigt.
1. Wählen Sie das zu veröffentlichende Element aus und wählen Sie **[!UICONTROL UnClaim]**. Das Element wird wieder zum Pool hinzugefügt. Andere können das Element jetzt beanspruchen.

## Beschränkungen {#limitations}

* Die Freigabe von Elementen für eine Gruppe wird nicht unterstützt.
* Die Freigabe von Projektaufgaben wird nicht unterstützt.
