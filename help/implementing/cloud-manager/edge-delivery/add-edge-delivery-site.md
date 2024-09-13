---
title: Hinzufügen einer Edge Delivery-Site zu Cloud Manager
description: Erfahren Sie, wie Sie Ihrem Produktionsprogramm oder Sandbox-Programm eine Edge Delivery-Site hinzufügen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '589'
ht-degree: 4%

---


## Hinzufügen einer Edge Delivery-Site zu Cloud Manager {#eds-add-site}

Nachdem Sie einem Produktionsprogramm Edge Delivery Services hinzugefügt haben, wird Ihre Edge Delivery Services-Lizenz darauf angewendet.

Auf der Übersichtsseite wird eine klickbare Registerkarte mit dem Namen **Edge Delivery** angezeigt. Durch Klicken auf die Registerkarte wird eine Tabelle mit den einzelnen Edge Delivery-Sites angezeigt, die Sie hinzugefügt haben. Beachten Sie im linken Navigationsbereich unter der Gruppierung **Dienste** die Menüoption namens **Edge Delivery Sites**.

![Übersichtsseite mit Edge Delivery Sites im linken Navigationsbereich und der Registerkarte Edge Delivery rechts neben der Registerkarte Publish-Bereitstellung](/help/implementing/cloud-manager/assets/cm-overview-eds.png)

**Hinzufügen einer Edge Delivery-Site zu Cloud Manager:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem Sie eine Edge Delivery-Site hinzufügen möchten.
1. Führen Sie eine der folgenden Aktionen aus:
   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery** . Klicken Sie dann unten rechts auf der Seite auf **Edge Delivery-Site hinzufügen**.

     ![Hinzufügen der Edge Delivery-Site vom Tab &quot;Edge Delivery&quot;](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

     Die im obigen Bild dargestellte &quot;Edge Delivery-Aufgabenliste&quot;**ist eine optionale Anleitung zur Einstieg in die Checkliste, die Ihnen bei den ersten Schritten mit Edge Delivery helfen soll.** Siehe [Info zur Edge Delivery-Aufgabenliste](#ed-todo-list).

   * Klicken Sie oben links auf der Seite auf das Hamburger-Symbol, um das linke Navigationsmenü anzuzeigen. Klicken Sie unter der Überschrift **Dienste** auf **Edge Delivery Sites**. Klicken Sie in der rechten oberen Ecke der Seite auf **Site hinzufügen**.

     ![Edge Delivery-Site über die Schaltfläche &quot;Edge Delivery Sites&quot;hinzufügen](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Gehen Sie im Dialogfeld **Edge Delivery-Site hinzufügen** wie folgt vor:

   | Textfeld | Vorgehensweise |
   | --- | --- |
   | Site-Name | Geben Sie den Namen der Edge Delivery-Site ein, die Sie hinzufügen. Der Name dient als eindeutige Kennung für die Site in Cloud Manager. |
   | Repository-URL | Dieses Feld bezieht sich auf das Git-Repository, in dem der Code Ihrer Website gespeichert ist.<br>Geben Sie die URL des Git-Repositorys ein, das die erforderlichen Dateien und Ressourcen (wie HTML, CSS, JavaScript und andere Web-Assets) für Ihre Edge Delivery-Site enthält. Auf diese Weise kann Cloud Manager den Code während des Bereitstellungsprozesses aus diesem Repository abrufen. |
   | Site-Beschreibung (optional) | Geben Sie eine kurze Beschreibung der Edge Delivery-Site ein, die Sie hinzufügen.<br>Diese Beschreibung hilft, die Site zu identifizieren und zu unterscheiden, wodurch es einfacher wird, unter anderen von Ihnen hinzugefügten Sites zu verwalten und zu erkennen. Sie können Details zum Zweck, zum Inhalt oder zu anderen relevanten Informationen der Site hinzufügen, die dazu beitragen können, deren Funktion oder Umfang zu verdeutlichen. |

1. Klicken Sie in der rechten unteren Ecke des Dialogfelds auf **Hinzufügen**.

1. Führen Sie im Dialogfeld **Repository-Eigentümer überprüfen** die folgenden Schritte aus:

   | Schritt | Beschreibung |
   | --- | --- |
   | 1 | Fügen Sie eine Datei mit dem Speicherortpfad zur Verzweigung `main` des Git-Repositorys hinzu, die im Feld **Repository-URL** aufgeführt ist. Klicken Sie bei Bedarf auf das Symbol Kopieren , um den Pfad in die Zwischenablage zu kopieren.<br> Der Speicherort ist:<br>`well-known/adobe/cloudmanager-challenge.txt`.<br><br>Fügen Sie *nicht* am Anfang des Speicherortpfads einen Punkt hinzu, der sich in:<br>`.well-known/adobe/cloudmanager-challenge.txt` befindet. |
   | 2 | Fügen Sie den generierten Code der Datei hinzu, die Sie in Schritt 1 erstellt haben. Klicken Sie bei Bedarf auf das Symbol Kopieren , um den Code in die Zwischenablage zu kopieren. |
   | 3 | Erstellen Sie im Git-Repository eine Pull-Anfrage und führen Sie sie dann zusammen, um den Code zu übertragen. |

1. Klicken Sie auf **Verify**. Nachdem das Repository verifiziert wurde, ändert sich sein Status in der Tabelle Edge Deliver Sites in einen grünen Kreis mit einem weißen Häkchen darin.
