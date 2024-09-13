---
title: Verwalten von Edge Delivery Sites in Cloud Manager
description: Erfahren Sie, wie Sie einer Edge Delivery-Site eine CDN-Konfiguration hinzufügen oder eine Edge Delivery-Site löschen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: b222b4384b1c2a21ecbb244d149ce7e51cc7990f
workflow-type: tm+mt
source-wordcount: '274'
ht-degree: 2%

---

# Verwalten der Edge Delivery-Site in Cloud Manager {#manage-edge-delivery-sites}

Erfahren Sie, wie Sie Edge Delivery-Sites in Cloud Manager verwalten, indem Sie einer vorhandenen Site eine CDN-Konfiguration hinzufügen. Oder löschen Sie eine Edge Delivery-Site.

## Hinzufügen einer CDN-Konfiguration zu einer vorhandenen Edge Delivery-Site {#add-cdn-to-edge-delivery-site}

Siehe [Hinzufügen einer CDN-Konfiguration](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).

## Löschen einer Edge Delivery-Site {#delete-edge-delivery-site}

Wenn Sie eine Edge Delivery Services-Site löschen, werden auch alle zugehörigen CDN-Konfigurationen entfernt. Diese Aktion unterbricht die Verbindung zwischen benutzerdefinierten Domänen und der Site. Weitere Informationen finden Sie unter CDN-Konfigurationen. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**So löschen Sie eine Edge Delivery-Site:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem Sie eine Edge Delivery-Site hinzufügen möchten.
1. Führen Sie eine der folgenden Aktionen aus:
   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery** . Klicken Sie in der Edge Delivery-Sitetabelle auf das Auslassungszeichen am Ende einer Zeile, deren Site Sie entfernen möchten.
Klicken Sie auf **Löschen** und dann erneut auf **Löschen** , um das Entfernen der Site zu bestätigen.

     ![Hinzufügen der Edge Delivery-Site vom Tab &quot;Edge Delivery&quot;](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Klicken Sie oben links auf der Seite auf das Hamburger-Symbol, um das linke Navigationsmenü anzuzeigen. Klicken Sie unter der Überschrift **Dienste** auf **Edge Delivery Sites**.
Klicken Sie in der Edge Delivery-Sitetabelle auf das Auslassungszeichen am Ende einer Zeile, deren Site Sie entfernen möchten. Klicken Sie auf **Löschen** und dann erneut auf **Löschen** , um das Entfernen der Site zu bestätigen.


     ![Edge Delivery-Site über die Schaltfläche &quot;Edge Delivery Sites&quot;hinzufügen](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)