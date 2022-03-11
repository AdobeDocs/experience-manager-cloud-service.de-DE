---
title: Demosite erstellen
description: Erstellen Sie eine Demosite in AEM basierend auf einer Bibliothek vorkonfigurierter Vorlagen.
exl-id: e76fd283-12b2-4139-9e71-2e145b9620b1
source-git-commit: 940a01cd3b9e4804bfab1a5970699271f624f087
workflow-type: tm+mt
source-wordcount: '844'
ht-degree: 3%

---

# Demosite erstellen {#creating-a-site}

Erstellen Sie eine Demosite in AEM basierend auf einer Bibliothek vorkonfigurierter Vorlagen.

## Die bisherige Entwicklung {#story-so-far}

Im vorherigen Dokument der AEM-Referenz-Demos-Add-On-Journey, [Programm erstellen,](create-program.md) Sie haben den ersten Konfigurationsschritt ausgeführt, um ein Programm für Testzwecke zu erstellen, und eine Pipeline zum Bereitstellen des Add-On-Inhalts verwendet. Sie sollten jetzt:

* Erfahren Sie, wie Sie mit Cloud Manager ein neues Programm erstellen können.
* Erfahren Sie, wie Sie das Referenz-Demos-Add-On für das neue Programm aktivieren.
* Sie können eine Pipeline zum Bereitstellen des Add-On-Inhalts ausführen.

In diesem Artikel wird der nächste Schritt des Prozesses beschrieben, indem ein neues Site- oder AEM Screens-Projekt in AEM erstellt wird, das auf den Vorlagen des Referenz-Demo-Add-ons basiert.

## Ziel {#objective}

In diesem Dokument erfahren Sie, wie Sie eine neue Site basierend auf den Vorlagen des Referenz-Demo-Add-ons erstellen. Nach dem Lesen sollten Sie:

* Erfahren Sie, wie Sie auf die AEM Authoring-Umgebung zugreifen.
* Erfahren Sie, wie Sie eine Site basierend auf einer Vorlage erstellen.
* Machen Sie sich mit den Grundlagen zum Navigieren in der Site-Struktur und Bearbeiten einer Seite vertraut.

## Erstellen einer Demosite oder eines Screens-Projekts {#create-site}

Nachdem die Pipeline das Referenz-Demo-Add-On bereitgestellt hat, können Sie auf die AEM Authoring-Umgebung zugreifen, um Demosites basierend auf dem Add-On-Inhalt zu erstellen.

1. Tippen oder klicken Sie auf der Seite mit der Programmübersicht in Cloud Manager auf den Link zur AEM Authoring-Umgebung.

   ![Auf Authoring-Umgebung zugreifen](assets/access-author.png)

1. Tippen oder klicken Sie im Hauptmenü von AEM auf **Sites**.

   ![Auf Sites zugreifen](assets/access-sites.png)

1. Tippen oder klicken Sie in der Sites-Konsole auf **Erstellen** oben rechts im Bildschirm, und wählen Sie **Site aus Vorlage** in der Dropdown-Liste.

   ![Erstellen einer Site aus einer Vorlage](assets/create-site-from-template.png)

1. Der Site-Erstellungsassistent wird gestartet. In der linken Spalte sehen Sie die Demovorlagen, die die Pipeline für Ihre Authoring-Instanz bereitgestellt hat. Tippen oder klicken Sie auf einen Ordner, um ihn auszuwählen und Details in der rechten Spalte anzuzeigen. Wenn Sie AEM Screens testen oder vorführen möchten, wählen Sie die **We.Cafe-Site-Vorlage**. Tippen oder klicken Sie auf **Weiter**.

   ![Assistent zur Site-Erstellung](assets/site-creation-wizard.png)

1. Geben Sie im nächsten Bildschirm einen Titel für Ihre Site oder Ihr Screens-Projekt ein. Ein Site-Name kann angegeben werden oder wird aus dem Titel generiert, wenn er weggelassen wird. Tippen oder klicken Sie auf **Erstellen**.

   * Der Titel der Site wird in der Titelleiste des Browsers angezeigt.
   * Der Site-Name wird Teil der URL.
   * Der Site-Name muss AEM Seitenbenennungskonventionen entsprechen, die im Abschnitt [Zusätzliche Ressourcen](#additional-resources) Abschnitt.

   ![Site-Details](assets/site-details.png)

1. Die Site-Erstellung wird mit einem Dialogfeld bestätigt. Tippen oder klicken Sie auf **Fertig**.

   ![Site-Erstellung abgeschlossen](assets/site-creation-complete.png)

Sie haben jetzt Ihre eigene Demosite erstellt!

## Demosite verwenden {#use-site}

Nachdem Sie Ihre Demosite erstellt haben, können Sie sie wie jede andere Website in AEM verwenden.

1. Die Site wird jetzt in der Sites-Konsole angezeigt.

   ![Neue Demosite in der Sites-Konsole](assets/new-demo-site.png)

1. Stellen Sie in der oberen rechten Ecke des Bildschirms sicher, dass die Konsolenansicht auf **Spaltenansicht**.

   ![Spaltenansicht](assets/column-view.png)

1. Tippen oder klicken Sie auf die Site, um deren Struktur und Inhalt zu untersuchen. Die Spaltenansicht wird beim Navigieren in der Inhaltsstruktur der Demosite kontinuierlich erweitert.

   ![Site-Struktur](assets/site-structure.png)

1. Tippen oder klicken Sie auf eine Seite, um sie auszuwählen, und tippen oder klicken Sie auf **Bearbeiten** in der Symbolleiste.

   ![Seite auswählen](assets/select-page.png)

1. Sie können die Seite wie jede andere AEM Inhaltsseite bearbeiten, z. B. das Hinzufügen oder Bearbeiten von Komponenten oder Assets und die Funktionalität von AEM testen.

   ![Seite bearbeiten](assets/edit-page.png)

Herzlichen Glückwunsch! Sie können nun den Inhalt Ihrer Demosite weiter untersuchen und alle Angebote AEM über den Inhalt der Best Practices des Referenz-Demo-Add-ons ermitteln.

Erstellen Sie zusätzliche Sites basierend auf anderen Vorlagen, um weitere AEM zu erkunden.

## Wie geht es weiter {#what-is-next}

Nachdem Sie diesen Teil der AEM Referenz-Demo-Add-On-Journey abgeschlossen haben, sollten Sie Folgendes tun:

* Erfahren Sie, wie Sie auf die AEM Authoring-Umgebung zugreifen.
* Erfahren Sie, wie Sie eine Site basierend auf einer Vorlage erstellen.
* Machen Sie sich mit den Grundlagen zum Navigieren in der Site-Struktur und Bearbeiten einer Seite vertraut.

Sie können jetzt die Funktionen von AEM mithilfe von Add-On-Inhalten testen. Sie haben zwei Möglichkeiten, um mit dem Journey fortzufahren:

* Wenn Sie AEM Screens-Inhalte vollständig demonstrieren und testen möchten, stellen Sie sicher, dass Sie eine Site basierend auf der **We.Cafe-Site-Vorlage** wie zuvor beschrieben und weiterhin [Aktivieren Sie AEM Screens für Ihre Demosite.](screens.md)
* Wenn Sie nur mit zum Demo von Sites-Inhalten arbeiten, fahren Sie mit [Verwalten Ihrer Demosites,](manage.md) Hier erfahren Sie mehr über die Tools, die Ihnen bei der Verwaltung Ihrer Demosites zur Verfügung stehen und wie Sie diese entfernen können.

## Zusätzliche Ressourcen {#additional-resources}

* [Dokumentation zu Cloud Manager](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/onboarding/onboarding-concepts/cloud-manager-introduction.html) - Wenn Sie weitere Details zu den Funktionen von Cloud Manager wünschen, sollten Sie sich die ausführlichen technischen Dokumente direkt ansehen.
* [Site erstellen](/help/sites-cloud/administering/site-creation/create-site.md) - Erfahren Sie, wie Sie AEM verwenden, um eine Site mithilfe von Site-Vorlagen zu erstellen, um den Stil und die Struktur Ihrer Site zu definieren.
* [Seitenbenennungskonventionen AEM.](/help/sites-cloud/authoring/fundamentals/organizing-pages.md#page-name-restrictions-and-best-practices) - Auf dieser Seite finden Sie die Konventionen zum Organisieren AEM Seiten.
* [AEM Grundlegende Handhabung](/help/sites-cloud/authoring/getting-started/basic-handling.md) - Sehen Sie sich dieses Dokument an, wenn Sie mit grundlegenden Konzepten wie Navigation und Konsolenorganisation noch nicht vertraut AEM sind.
