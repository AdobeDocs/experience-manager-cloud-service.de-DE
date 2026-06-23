---
title: Hinzufügen einer Edge Delivery-Site zu Cloud Manager
description: Erfahren Sie, wie Sie Ihrem Produktions- oder Sandbox-Programm eine Edge Delivery-Site hinzufügen.
feature: Cloud Manager, Developing
role: Admin, Developer
exl-id: 17e842c9-599a-4877-9834-1e7220f508a8
source-git-commit: 069e94e230b856fba15c3f465c966a5bf6b0ac46
workflow-type: tm+mt
source-wordcount: '591'
ht-degree: 58%

---

# Hinzufügen einer Edge Delivery-Site zu Cloud Manager {#adding}

>[!IMPORTANT]
>
>Erfahren Sie, warum Sie Ihre Edge Delivery Services-Site zu Cloud Manager hinzufügen müssen.
>Siehe [Vorteile der Verwendung des von Adobe empfohlenen Pfads für Edge Delivery Services](/help/implementing/cloud-manager/edge-delivery/introduction-to-edge-delivery-services.md#recommended-path-eds).

**So fügen Sie eine Edge Delivery-Site zu Cloud Manager hinzu:**

1. Vergewissern Sie sich, dass Sie Ihr Programm mit einer Edge Delivery Services-Lizenz erstellt haben, bevor Sie eine Edge Delivery-Site in Cloud Manager integrieren.
Siehe [Erstellen eines Produktionsprogramms](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md).

   >[!TIP]
   >
   >Wenn Sie eine neue Edge Delivery-Site erstellen möchten, die das AEM-Authoring mit dem universellen Editor verwendet, anstatt eine vorhandene Site zu registrieren, finden Sie weitere Informationen unter [Erstellen Ihrer ersten Edge Delivery-Site mit einem Klick](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md). Bei Programmen, die Edge Delivery für die Bereitstellung verwenden, ist möglicherweise keine Veröffentlichungsebene erforderlich. Siehe [Flexible Veröffentlichungsebene (Beta)](/help/implementing/cloud-manager/getting-access-to-aem-in-cloud/creating-production-programs.md#flexible-publish-tier).

{{sign-in-to-cloud-manager}}

1. Klicken Sie in **Konsole** Meine Programme“ auf ein Programm.
1. Führen Sie einen der folgenden Schritte aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**. Klicken Sie dann unten rechts auf der Seite auf **Edge Delivery-Site hinzufügen**.

     ![Hinzufügen einer Edge Delivery-Site auf der Registerkarte „Edge Delivery“](/help/implementing/cloud-manager/assets/cm-eds-add1.png)

   * Klicken Sie oben links auf der Seite auf ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) um das linke Menü zu öffnen.
Klicken Sie unter **Services** auf ![Web-Seitensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
Klicken Sie oben rechts auf der Seite auf ![Link-Symbol oder Hinzufügen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Link_18_N.svg) **Edge Delivery-Site hinzufügen**.

     ![Hinzufügen einer Edge Delivery-Site über die Schaltfläche „Edge Delivery-Sites“](/help/implementing/cloud-manager/assets/cm-eds-add2.png)

1. Geben Sie im Dialogfeld **Edge Delivery-Site hinzufügen** die folgenden Informationen in die Pflichtfelder ein:

   | Textfeld | Beschreibung |
   | - | --- |
   | Site-Name | Geben Sie den Namen der Edge Delivery-Site ein, die Sie hinzufügen.<br>Der Name dient als eindeutige Kennung für die Site in Cloud Manager. |
   | Edge Delivery-Herkunft | Dieser Wert gibt den URL-Pfad zur Inhaltsquelle für Ihre Site in Edge Delivery Services an. Außerdem wird dadurch Cloud Manager mit Ihrer Live-Site verknüpft.<br>Die URL umfasst normalerweise *Verzweigung*, *Projekt* und *Mandant*, wie im folgenden Beispiel (nur zu Veranschaulichungszwecken):<br>`https://main--{site}--{org}.aem.live` |
   | Site-Beschreibung (optional) | Geben Sie eine kurze Beschreibung der Edge Delivery-Site ein, die Sie hinzufügen.<br>Eine Beschreibung hilft bei der Identifizierung und Unterscheidung der Site, sodass Sie sie leichter verwalten und unter anderen hinzugefügten Sites erkennen können. |

1. Klicken Sie unten rechts im Dialogfeld auf **Speichern**.

1. Überprüfen **im Dialogfeld „Repository** Eigentümerschaft überprüfen“ die Eigentümerschaft Ihres Repositorys, indem Sie Folgendes durchführen:

   | Schritt | Beschreibung |
   | - | - |
   | **1** | Fügen Sie eine Datei mit dem Pfad und dem Namen `well-known/adobe/cloudmanager-challenge.txt` zur Verzweigung `main` des Git-Repositorys hinzu, das im Feld **Repository-URL** aufgeführt ist. Fügen Sie am Anfang des Speicherortpfads *keinen* Punkt hinzu.<br>Klicken Sie bei Bedarf auf ![Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg), um den Pfad in die Zwischenablage zu kopieren. |
   | **2** | Fügen Sie den Code aus dem Textfeld in Schritt 2 der Datei hinzu, die Sie gerade in Schritt 1 erstellt haben.<br>Klicken Sie ggf. auf ![Symbol „Kopieren](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Copy_18_N.svg), um den Code in die Zwischenablage zu kopieren. |
   | **3** | Erstellen Sie eine Pull-Anfrage für die soeben erstellten Änderungen im Git-Repository und führen Sie sie dann mit `main` zusammen, um den Code zu übertragen. |

1. Klicken Sie auf **Überprüfen**.

   >[!NOTE]
   >
   >Wenn Ihre Edge Delivery Services-Site die Helix-Authentifizierung verwendet, ist die Verifizierungsproblematik nicht zugänglich. Deaktivieren Sie die Authentifizierung vorübergehend, schließen Sie die Site-Überprüfung ab, und schalten Sie die Authentifizierung dann wieder ein.



Wenn das Repository überprüft wird, wird sein Status in der Edge Delivery Sites-Tabelle aktualisiert. Der Status wird durch einen grünen Kreis mit weißem Häkchen angegeben.

Klicken Sie in derselben Tabelle auf ![Symbol für Informationen zur Edge Delivery-Site](https://spectrum.adobe.com/static/icons/workflow_18/Smock_InfoOutline_18_N.svg), um Site-Details anzuzeigen. Zu diesen Informationen gehören die verifizierte Repository-URL sowie die Vorschau- und Produktions-Website-URLs.
