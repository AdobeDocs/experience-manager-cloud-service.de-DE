---
title: Hinzufügen einer Edge Delivery-Site zu Cloud Manager
description: Erfahren Sie, wie Sie Ihrem Produktionsprogramm oder Sandbox-Programm eine Edge Delivery-Site hinzufügen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2b384a4233672d69de09b922fcdef6d0f84ff7df
workflow-type: tm+mt
source-wordcount: '505'
ht-degree: 3%

---


# Hinzufügen einer Edge Delivery-Site zu Cloud Manager {#adding}

Nachdem Sie Ihrem Produktionsprogramm eine Edge Delivery-Site hinzugefügt haben, wird Ihre Edge Delivery Services-Lizenz darauf angewendet.

Das Hinzufügen einer Edge Delivery-Site zu Cloud Manager ist erforderlich, um [ein Support-Ticket für Ihr Edge Delivery-Projekt zu registrieren](/help/edge/overview.md##support-ticket).

Siehe auch [Einführung in Edge Delivery Services in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

**Hinzufügen einer Edge Delivery-Site zu Cloud Manager:**

1. Melden Sie sich bei Cloud Manager unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/) an und wählen Sie das entsprechende Programm aus.
1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery** . Klicken Sie dann unten rechts auf der Seite auf **Edge Delivery-Site hinzufügen**.

     ![Fügen Sie die Edge Delivery-Site von der Registerkarte &quot;Edge Delivery&quot;hinzu](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * Klicken Sie oben links auf der Seite auf ![Seitennavigation ein- oder ausblenden](https://spectrum.corp.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) , um das Seitennavigationsmenü einzublenden.
Klicken Sie unter der Überschrift **Dienste** auf ![Webseite für Edge Delivery-Sites](https://spectrum.corp.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
Klicken Sie in der rechten oberen Ecke der Seite auf **Site hinzufügen**.

     ![Fügen Sie die Edge Delivery-Site über die Schaltfläche &quot;Edge Delivery Sites&quot;hinzu](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Geben Sie im Dialogfeld **Edge Delivery-Site hinzufügen** die folgenden Informationen in die erforderlichen Felder ein:

   | Textfeld | Beschreibung |
   | - | --- |
   | Site-Name | Geben Sie den Namen der Edge Delivery-Site ein, die Sie hinzufügen.<br>Der Name dient als eindeutige Kennung für die Site in Cloud Manager. |
   | Repository-URL | Geben Sie das Git-Repository ein, in dem der Code Ihrer Website gespeichert ist.<br>Mit diesem Feld kann Cloud Manager den Code während des Bereitstellungsprozesses aus diesem Repository abrufen. |
   | Site-Beschreibung (optional) | Geben Sie eine kurze Beschreibung der Edge Delivery-Site ein, die Sie hinzufügen.<br>Eine Beschreibung hilft, die Site zu identifizieren und zu unterscheiden, wodurch die Verwaltung und Erkennung von anderen von Ihnen hinzugefügten Sites erleichtert wird. |

1. Klicken Sie in der rechten unteren Ecke des Dialogfelds auf **Hinzufügen**.

1. Überprüfen Sie im Dialogfeld **Repository-Eigentümer überprüfen** den Besitz Ihres Repositorys, indem Sie die folgenden Schritte ausführen:

   | Schrittnummer | Beschreibung |
   | - | - |
   | **1** | Fügen Sie eine Datei mit dem Pfad und dem Namen `well-known/adobe/cloudmanager-challenge.txt` zur Verzweigung `main` des Git-Repositorys hinzu, die im Feld **Repository-URL** aufgeführt ist. Fügen Sie am Anfang des Speicherortpfads *nicht* einen Punkt hinzu.<br>Klicken Sie bei Bedarf auf ![Kopieren](https://spectrum.corp.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) , um den Pfad in die Zwischenablage zu kopieren. |
   | **2** | Fügen Sie den im Textfeld in Schritt 2 angezeigten Code der Datei hinzu, die Sie gerade in Schritt 1 erstellt haben.<br>Klicken Sie bei Bedarf auf ![Kopieren](https://spectrum.corp.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg) , um den Code in die Zwischenablage zu kopieren. |
   | **3** | Erstellen Sie eine Pull-Anforderung für die soeben erstellten Änderungen im Git-Repository und führen Sie sie dann mit `main` zusammen, um den Code zu übertragen. |

1. Klicken Sie auf **Verify**.

Nachdem das Repository verifiziert wurde, ändert sich sein Status in der Tabelle der Edge Delivery-Sites in einen grünen Kreis mit einem weißen Häkchen darin.

In derselben Tabelle können Sie auf ![Informationen zur Edge Delivery-Site klicken.](https://spectrum.corp.adobe.com/static/icons/workflow_18/Smock_InfoOutline_18_N.svg) , um Details zu Ihrer Site anzuzeigen, z. B. die verifizierte URL des Repositorys und die URL der Vorschau- und Produktionswebsite.


