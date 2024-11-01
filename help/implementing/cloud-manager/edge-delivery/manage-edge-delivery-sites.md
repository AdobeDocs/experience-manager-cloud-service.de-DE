---
title: Verwalten von Edge Delivery-Sites in Cloud Manager
description: Erfahren Sie, wie Sie einer Edge Delivery-Site eine CDN-Konfiguration hinzufügen oder eine Edge Delivery-Site löschen.
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f64a551bc18b53d0026736ece2a44e48cd0cfb4c
workflow-type: tm+mt
source-wordcount: '538'
ht-degree: 10%

---

# Verwalten der Edge Delivery-Site in Cloud Manager {#manage-edge-delivery-sites}

Erfahren Sie, wie Sie Edge Delivery-Sites in Cloud Manager verwalten, indem Sie einer vorhandenen Site eine CDN-Konfiguration hinzufügen. Oder löschen Sie eine Edge Delivery-Site.

## Hinzufügen einer CDN-Konfiguration zu einer vorhandenen Edge Delivery-Site {#add-cdn-to-edge-delivery-site}

Siehe [Hinzufügen einer CDN-Konfiguration](/help/implementing/cloud-manager/cdn-configurations/add-cdn-config.md).

## Umbenennen einer Edge Delivery-Site (#rename-edge-delivery-site)

Unter Adobe Cloud Manager können Sie eine Edge Delivery-Site aus verschiedenen Gründen umbenennen:

* **Klarheit und Organisation**: Zum Beschreiben des Zwecks der Site oder ihrer zugehörigen Umgebung (z. B. Produktion, Staging).
* **Vermeidung von Verwirrung**: Wenn mehrere Sites verwendet werden, kann das Umbenennen dazu beitragen, leicht zwischen ihnen zu unterscheiden, wodurch die Wahrscheinlichkeit verringert wird, Konfigurationen oder Aktualisierungen auf die falsche Site anzuwenden.
* **Standardisierung**: Befolgen Sie eine konsistente Benennungskonvention, die den Richtlinien Ihres Unternehmens zur einfacheren Verwaltung und Prüfung entspricht.

**So benennen Sie eine Edge Delivery-Site um:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem Sie eine Edge Delivery-Site hinzufügen möchten.
1. Führen Sie eine der folgenden Aktionen aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery** . Klicken Sie in der Edge Delivery-Sitetabelle auf das Auslassungszeichen am Ende einer Zeile, deren Site Sie umbenennen möchten.
Klicken Sie auf **Umbenennen**.
   * Klicken Sie oben links auf der Seite auf das Symbol ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) , um das Menü links einzublenden. Klicken Sie unter der Überschrift **Dienste** auf das Symbol ![Webseiten-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
Klicken Sie in der Edge Delivery-Sitetabelle am Ende einer Zeile, deren Site Sie umbenennen möchten, auf das Symbol &quot;![Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)&quot;. Klicken Sie auf **Umbenennen**.

1. Geben Sie im Dialogfeld **Edge Delivery-Site bearbeiten** im Textfeld **Site-Name** den neuen Namen der Site ein.

1. Klicken Sie auf **Bearbeiten**.

## Löschen einer Edge Delivery-Site {#delete-edge-delivery-site}

Wenn Sie eine Edge Delivery Services-Site löschen, werden auch alle zugehörigen CDN-Konfigurationen entfernt. Diese Aktion unterbricht die Verbindung zwischen benutzerdefinierten Domänen und der Site. Weitere Informationen finden Sie unter CDN-Konfigurationen. <!-- https://wiki.corp.adobe.com/display/DMSArchitecture/%5BKT%5D+Cloud+Manager+2024.9.0+Release -->

**So löschen Sie eine Edge Delivery-Site:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie das entsprechende Programm aus.
1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm mit konfigurierten Edge Delivery Services aus, in dem Sie eine Edge Delivery-Site hinzufügen möchten.
1. Führen Sie eine der folgenden Aktionen aus:

   * Klicken Sie auf der Seite **Programmübersicht** auf die Registerkarte **Edge Delivery** . Klicken Sie in der Edge Delivery-Sitetabelle am Ende einer Zeile, deren Site Sie entfernen möchten, auf das Symbol &quot;![Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)&quot;.
Klicken Sie auf ![Edge Delivery-Site löschen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Löschen** und dann erneut auf **Löschen** , um das Entfernen der Site zu bestätigen.

     ![Hinzufügen der Edge Delivery-Site vom Tab &quot;Edge Delivery&quot;](/help/implementing/cloud-manager/assets/cm-eds-delete1.png)

   * Klicken Sie oben links auf der Seite auf das Symbol ![Menüsymbol anzeigen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_ShowMenu_18_N.svg) , um das Menü links einzublenden. Klicken Sie unter der Überschrift **Dienste** auf ![Webseite für Edge Delivery-Sites](https://spectrum.adobe.com/static/icons/workflow_18/Smock_WebPages_18_N.svg) **Edge Delivery Sites**.
Klicken Sie in der Edge Delivery-Sitetabelle am Ende einer Zeile, deren Site Sie entfernen möchten, auf das Symbol &quot;![Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg)&quot;. Klicken Sie auf ![Edge Delivery-Site löschen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Delete_18_N.svg) **Löschen** und dann erneut auf **Löschen** , um das Entfernen der Site zu bestätigen.

     ![Edge Delivery-Site über die Schaltfläche &quot;Edge Delivery Sites&quot;hinzufügen](/help/implementing/cloud-manager/assets/cm-eds-delete2.png)

## Einreichen eines Support-Tickets {#eds-support-ticket}

{{support-ticket}}


