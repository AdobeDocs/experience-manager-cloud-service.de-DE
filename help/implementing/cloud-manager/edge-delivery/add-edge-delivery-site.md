---
title: Hinzufügen einer Edge Delivery-Site zu Cloud Manager
description: Erfahren Sie, wie Sie Ihrem Produktionsprogramm oder Sandbox-Programm eine Edge Delivery-Site hinzufügen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: c952e69aa637b30abec4deba0e643b4287d84330
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 3%

---


# Hinzufügen einer Edge Delivery-Site zu Cloud Manager {#adding}

Sie können Ihrem Produktionsprogramm oder Sandbox-Programm eine Edge Delivery-Site hinzufügen.

Das Hinzufügen einer Edge Delivery-Site zu Cloud Manager ist erforderlich, um [ein Support-Ticket für Ihr Edge Delivery-Projekt zu registrieren](/help/edge/overview.md##support-ticket).

Siehe auch [Einführung in Edge Delivery Services in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

**Hinzufügen einer Edge Delivery-Site zu Cloud Manager:**

1. Melden Sie sich bei Cloud Manager unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) an und wählen Sie das entsprechende Programm aus.
1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery** . Klicken Sie dann unten rechts auf der Seite auf **Edge Delivery-Site hinzufügen**.

     ![Fügen Sie die Edge Delivery-Site von der Registerkarte &quot;Edge Delivery&quot;hinzu](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * Klicken Sie oben links auf der Seite auf das Hamburger-Symbol, um das linke Navigationsmenü anzuzeigen. Klicken Sie unter der Überschrift **Dienste** auf **Edge Delivery Sites**. Klicken Sie in der rechten oberen Ecke der Seite auf **Site hinzufügen**.

     ![Fügen Sie die Edge Delivery-Site über die Schaltfläche &quot;Edge Delivery Sites&quot;hinzu](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Geben Sie im Dialogfeld **Edge Delivery-Site hinzufügen** die folgenden Informationen in die erforderlichen Felder ein:

   | Textfeld | Zu liefernde Daten |
   | --- | --- |
   | Site-Name | Geben Sie den Namen der Edge Delivery-Site ein, die Sie hinzufügen. Der Name dient als eindeutige Kennung für die Site in Cloud Manager. |
   | Repository-URL | Dieses Feld bezieht sich auf das Git-Repository, in dem der Code Ihrer Website gespeichert ist. Mit diesem Feld kann Cloud Manager den Code während des Bereitstellungsprozesses aus diesem Repository abrufen. |
   | Site-Beschreibung (optional) | Geben Sie eine kurze Beschreibung der Edge Delivery-Site ein, die Sie hinzufügen. Diese Beschreibung hilft, die Site zu identifizieren und zu unterscheiden, wodurch es einfacher wird, unter anderen von Ihnen hinzugefügten Sites zu verwalten und zu erkennen. |

1. Klicken Sie in der rechten unteren Ecke des Dialogfelds auf **Hinzufügen**.

1. Das Dialogfeld **Repository-Eigentümer überprüfen** wird geöffnet. Führen Sie bei geöffneter Komponente die folgenden Schritte aus:

   1. Fügen Sie eine Datei mit dem Pfad und dem Namen `well-known/adobe/cloudmanager-challenge.txt` zur Verzweigung `main` des Git-Repositorys hinzu, die im Feld **Repository-URL** aufgeführt ist.
      * Klicken Sie bei Bedarf auf das Symbol **Kopieren** , um den Pfad in die Zwischenablage zu kopieren.
      * Fügen Sie am Anfang des Speicherortpfads *nicht* einen Punkt hinzu.
   1. Fügen Sie den Code aus dem Feld **Schritt &amp;num; 1** der Datei hinzu, die Sie im vorherigen Schritt erstellt haben.
      * Klicken Sie bei Bedarf auf das Symbol **Kopieren** , um den Code in die Zwischenablage zu kopieren.
   1. Erstellen Sie im Git-Repository eine Pull-Anforderung für die soeben erstellten Änderungen und führen Sie sie dann mit `main` zusammen.

1. Klicken Sie auf **Verify**.

Nachdem das Repository verifiziert wurde, ändert sich sein Status in der Tabelle Edge Deliver Sites in einen grünen Kreis mit einem weißen Häkchen darin.
