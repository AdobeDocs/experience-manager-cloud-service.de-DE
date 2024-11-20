---
title: Hinzufügen einer Edge Delivery-Site zu Cloud Manager
description: Erfahren Sie, wie Sie Ihrem Produktions- oder Sandbox-Programm eine Edge Delivery-Site hinzufügen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 17e842c9-599a-4877-9834-1e7220f508a8
source-git-commit: db661281831dcb07491dca16e73e835b487814a6
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 96%

---

# Hinzufügen einer Edge Delivery-Site zu Cloud Manager {#adding}

Nachdem Sie Ihrem Produktionsprogramm eine Edge Delivery-Site hinzugefügt haben, wird Ihre Edge Delivery Services-Lizenz darauf angewendet.

Das Hinzufügen einer Edge Delivery-Site zu Cloud Manager ist erforderlich, um [ein Support-Ticket für Ihr Edge Delivery-Projekt zu öffnen](/help/edge/overview.md##support-ticket).

Siehe auch [Einführung in Edge Delivery Services in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md).

**So fügen Sie eine Edge Delivery-Site zu Cloud Manager hinzu:**

1. Melden Sie sich unter [`https://my.cloudmanager.adobe.com`](https://my.cloudmanager.adobe.com/ ) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**. Klicken Sie dann unten rechts auf der Seite auf **Edge Delivery-Site hinzufügen**.

     ![Hinzufügen einer Edge Delivery-Site auf der Registerkarte „Edge Delivery“](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen.
Klicken Sie unter der Überschrift **Services** auf ![Web-Seiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery-Sites**.
Klicken Sie oben rechts auf der Seite auf **Site hinzufügen**.

     ![Hinzufügen einer Edge Delivery-Site über die Schaltfläche „Edge Delivery-Sites“](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Geben Sie im Dialogfeld **Edge Delivery-Site hinzufügen** die folgenden Informationen in die Pflichtfelder ein:

   | Textfeld | Beschreibung |
   | - | --- |
   | Site-Name | Geben Sie den Namen der Edge Delivery-Site ein, die Sie hinzufügen.<br>Der Name dient als eindeutige Kennung für die Site in Cloud Manager. |
   | Repository-URL | Geben Sie das Git-Repository ein, in dem der Code Ihrer Website gespeichert ist.<br>Mit diesem Feld kann Cloud Manager den Code während des Bereitstellungsprozesses aus diesem Repository abrufen. |
   | Site-Beschreibung (optional) | Geben Sie eine kurze Beschreibung der Edge Delivery-Site ein, die Sie hinzufügen.<br>Eine Beschreibung hilft, die Site zu identifizieren und zu unterscheiden und so die Verwaltung und Erkennung von anderen von Ihnen hinzugefügten Sites zu vereinfachen. |

1. Klicken Sie unten rechts im Dialogfeld auf **Speichern**.

1. Verifizieren Sie im Dialogfeld **Repository-Eigentümerschaft verifizieren** die Eigentümerschaft Ihres Repositorys, indem Sie die folgenden Schritte ausführen:

   | Schritt | Beschreibung |
   | - | - |
   | **1** | Fügen Sie eine Datei mit dem Pfad und dem Namen `well-known/adobe/cloudmanager-challenge.txt` zur Verzweigung `main` des Git-Repositorys hinzu, das im Feld **Repository-URL** aufgeführt ist. Fügen Sie am Anfang des Speicherortpfads *keinen* Punkt hinzu.<br>Klicken Sie bei Bedarf auf ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg), um den Pfad in die Zwischenablage zu kopieren. |
   | **2** | Fügen Sie den im Textfeld in Schritt 2 angezeigten Code der Datei hinzu, die Sie gerade in Schritt 1 erstellt haben.<br>Klicken Sie bei Bedarf auf ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg), um den Code in die Zwischenablage zu kopieren. |
   | **3** | Erstellen Sie eine Pull-Anfrage für die soeben erstellten Änderungen im Git-Repository und führen Sie sie dann mit `main` zusammen, um den Code zu übertragen. |

1. Klicken Sie auf **Überprüfen**.

Wenn das Repository überprüft wird, wird sein Status in der Edge Delivery Sites-Tabelle aktualisiert. Der Status wird durch einen grünen Kreis mit weißem Häkchen angegeben.

Klicken Sie in derselben Tabelle auf ![Informationen zur Edge Delivery-Site](https://spectrum.adobe.com/static/icons/workflow_18/Smock_InfoOutline_18_N.svg), um die Site-Details anzuzeigen. Zu diesen Informationen gehören die verifizierte Repository-URL sowie die Vorschau- und Produktions-Website-URLs.
