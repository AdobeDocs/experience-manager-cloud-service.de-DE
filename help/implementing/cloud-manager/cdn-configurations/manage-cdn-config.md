---
title: Verwalten von CDN-Konfigurationen
description: Erfahren Sie, wie Sie mit Cloud Manager CDN-Konfigurationen für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung bearbeiten, aktualisieren oder löschen können.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: ff8c7fb21b4d8bcf395d28c194a7351281eef45b
workflow-type: tm+mt
source-wordcount: '477'
ht-degree: 15%

---


# Verwalten von CDN-Konfigurationen (Content Delivery Network) {#manage-cdn-configurations}

Erfahren Sie, wie Sie mit Cloud Manager CDN-Konfigurationen für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung bearbeiten, aktualisieren oder löschen können.

## Bearbeiten einer CDN-Konfiguration {#edit-cdn}

In Adobe Cloud Manager können Sie eine CDN-Konfiguration, einschließlich der Umgebungsebene (Publish oder Vorschau) und des SSL-Zertifikats, aus verschiedenen Gründen bearbeiten.

* **Umgebungsänderungen**: Das Anpassen der Ebene hilft, die CDN-Einstellungen mit der richtigen Umgebung abzustimmen, sei es für die Live-Produktion (Publish) oder für Tests (Vorschau).
* **Sicherheitsverbesserungen**: Bei der Aktualisierung von Zertifikaten oder der Erfüllung von Compliance- und Sicherheitsanforderungen kann die Auswahl eines anderen SSL-Zertifikats erforderlich sein.
* **Leistungsoptimierung**: Durch die Bearbeitung der Konfiguration werden die richtigen CDN-Einstellungen für die Bereitstellung von Inhalten auf der Grundlage sich ändernder betrieblicher Anforderungen sichergestellt.

Sie können eine Konfiguration bearbeiten, ohne die vorhandene Konfiguration vollständig zu entfernen. Änderungen gelten für die ausgewählte Umgebung, z. B. für Staging oder Produktion, und können sich auf die Bereitstellung und Sicherung von Inhalten auswirken.

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**So bearbeiten Sie eine CDN-Konfiguration:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Klicken Sie im seitlichen Bedienfeld unter **Dienste** auf das Symbol für das soziale Netzwerk ![ ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **CDN-Konfigurationen**.
1. Klicken Sie in der Tabelle **CDN-Konfigurationen** am Ende einer Zeile, deren CDN-Konfiguration Sie aktualisieren möchten, auf das Symbol &quot;![Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) .

   ![Bearbeiten einer CDN-Konfiguration](/help/implementing/cloud-manager/assets/cdn-config-edit.png)

1. Klicken Sie im Dropdownmenü auf **Bearbeiten**.
1. Legen Sie im Dialogfeld **CDN-Konfiguration bearbeiten** eine oder mehrere der Optionen in der entsprechenden Dropdownliste fest.

   Die Optionen, die im Dialogfeld angezeigt werden, variieren je nachdem, ob Sie ein von Adobe verwaltetes CDN oder ein kundenverwaltetes CDN verwenden.

1. Klicken Sie auf **Aktualisieren**.

   Der Status des bearbeiteten CDN wird in der Tabelle **CDN-Konfigurationen** aktualisiert, um die vorgenommenen Änderungen widerzuspiegeln.

<!-- ## ALTERNATE METHOD FOR EDITING A CDN CONFIGURATION from the Environments page
    
    The steps for adding a custom domain name from the **Environments** page are the same as when [adding a custom domain name from the Domain Settings page](#adding-cdn-settings), but the entry point differs. Follow these steps to add a custom domain name from the **Environments** page.
    
    1. Log into Cloud Manager at [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) and select the appropriate organization and program.
    
    1. Navigate to the **Environments Detail** detail page for the environment of interest.
    
       ![Entering domain name on the Environment Details page](/help/implementing/cloud-manager/assets/cdn/environments-cdn-config.png)
    
    1. Use the **Domain Names** table to submit the custom domain name.
    
       1. Enter the custom domain name.
       1. Select the SSL certificate associated with this name from the drop-down list.
       1. Click ![Add icon](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg) **Add**.
    
       ![Add a custom domain name](/help/implementing/cloud-manager/assets/cdn/cdn-create3.png)
    
    1. The **Add domain name** dialog box opens to the **Domain Name** tab. Continue as you would for [adding a custom domain name from the Domain Settings page](#adding-cdn-settings). -->

## Löschen einer CDN-Konfiguration {#delete-cdn}

Wenn Sie eine von Adobe verwaltete oder kundenverwaltete CDN-Konfiguration in Adobe Cloud Manager löschen, werden die Routing- und SSL-Zertifikateinstellungen der zugehörigen Domäne entfernt. Die Domäne verwendet das CDN nicht mehr für die Traffic-Bereitstellung und alle vom CDN bereitgestellten Sicherheits- oder Leistungsverbesserungen gehen verloren. Sie können Dienstunterbrechungen feststellen, bis eine neue Konfiguration eingerichtet ist, unabhängig davon, ob Sie das gelöschte CDN erneut hinzufügen oder eine neue hinzufügen.

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**So löschen Sie eine CDN-Konfiguration:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie im linken Navigationsbereich unter **Dienste** auf **CDN-Konfigurationen**.

1. Klicken Sie in der Tabelle CDN-Konfigurationen am Ende einer Zeile, deren CDN Sie entfernen möchten, auf das Auslassungszeichen.

   ![Löschen einer CDN-Konfiguration](/help/implementing/cloud-manager/assets/cdn-config-delete.png)

1. Klicken Sie auf **Löschen**.
1. Klicken Sie erneut auf **Löschen** , um das Entfernen des CDN der Site zu bestätigen.


