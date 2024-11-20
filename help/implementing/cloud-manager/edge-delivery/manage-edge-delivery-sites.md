---
title: Verwalten von Edge Delivery-Sites in Cloud Manager
description: Erfahren Sie, wie Sie einer Edge Delivery-Site eine CDN-Konfiguration hinzufügen oder eine Edge Delivery-Site löschen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 960aa3c6-27b9-44b1-81ea-ad8c5bbc99a5
source-git-commit: 4eb0feecbc5d0f090789bd3023e366ef4eb620db
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 100%

---

# Verwalten von Edge Delivery-Sites in Cloud Manager {#manage-edge-delivery-sites}

Erfahren Sie, wie Sie Edge Delivery-Sites in Cloud Manager verwalten, indem Sie einer vorhandenen Site eine CDN-Konfiguration hinzufügen. oder eine Edge Delivery-Site löschen.

## Hinzufügen einer CDN-Konfiguration zu einer vorhandenen Edge Delivery-Site {#add-cdn-to-edge-delivery-site}

Siehe [Hinzufügen einer CDN-Konfiguration](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).

## Umbenennen einer Edge Delivery-Site (#rename-edge-delivery-site)

Es gibt verschiedene Gründe, um in Adobe Cloud Manager eine Edge Delivery-Site umzubenennen:

* **Klarheit und Organisation**: Durch eine Umbenennung lässt sich der Zweck der Site oder ihrer zugehörigen Umgebung (z. B. Produktion, Staging) besser beschreiben.
* **Vermeiden von Verwirrung**: Wenn mehrere Sites vorhanden sind, kann durch eine Umbenennung leichter zwischen ihnen unterscheiden werden. Dadurch wird die Wahrscheinlichkeit verringert, dass Konfigurationen oder Aktualisierungen auf die falsche Site angewendet werden.
* **Standardisierung**: Durch eine Umbenennung kann einer einheitlichen Namenskonvention gefolgt werden, die den Richtlinien Ihrer Organisation entspricht und so das Management und Auditing vereinfacht.

**So benennen Sie eine Edge Delivery-Site um:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/ ) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem eine Edge Delivery-Site hinzugefügt werden soll.
1. Führen Sie eine der folgenden Aktionen aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**. Klicken Sie in der Edge Delivery-Site-Tabelle auf die Auslassungspunkte am Ende einer Zeile, deren Site umbenannt werden soll.
Klicken Sie auf **Umbenennen**.
   * Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen. Klicken Sie unter der Überschrift **Services** auf ![Web-Seiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery-Sites**.
Klicken Sie in der Edge Delivery-Site-Tabelle auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren Site umbenannt werden soll. Klicken Sie auf **Umbenennen**.

1. Geben Sie im Dialogfeld **Edge Delivery-Site bearbeiten** den neuen Namen der Site in das Feld **Site-Name** ein.

1. Klicken Sie auf **Bearbeiten**.

## Löschen einer Edge Delivery-Site {#delete-edge-delivery-site}

Wenn Sie eine Edge Delivery Services-Site löschen, werden auch alle zugehörigen CDN-Konfigurationen entfernt. Diese Aktion trennt die Verbindung zwischen benutzerdefinierten Domains und der Site. Weitere Informationen finden Sie unter „CDN-Konfigurationen“. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**So löschen Sie eine Edge Delivery-Site:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/ ) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem eine Edge Delivery-Site hinzugefügt werden soll.
1. Führen Sie eine der folgenden Aktionen aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery**. Klicken Sie in der Edge Delivery-Site-Tabelle auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren Site entfernt werden soll.
Klicken Sie auf ![Edge Delivery-Site löschen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Löschen** und dann erneut auf **Löschen**, um das Entfernen der Site zu bestätigen.

     ![Hinzufügen einer Edge Delivery-Site auf der Registerkarte „Edge Delivery“](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Klicken Sie oben links auf der Seite auf ![Symbol zur Menüanzeige](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg), um das linke Seitenmenü anzuzeigen. Klicken Sie unter der Überschrift **Services** auf ![Web-Seite für Edge Delivery-Sites](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery-Sites**.
Klicken Sie in der Edge Delivery-Site-Tabelle auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren Site entfernt werden soll. Klicken Sie auf ![Edge Delivery-Site löschen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Löschen** und dann erneut auf **Löschen**, um das Entfernen der Site zu bestätigen.

     ![Hinzufügen einer Edge Delivery-Site über die Schaltfläche „Edge Delivery-Sites“](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Einreichen eines Support-Tickets {#eds-support-ticket}

{{support-ticket}}
