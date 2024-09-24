---
title: Verwalten von CDN-Konfigurationen
description: Erfahren Sie, wie Sie mit Cloud Manager CDN-Konfigurationen für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung bearbeiten, aktualisieren oder löschen können.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 2d1382c84d872719332986baa5829d1623d9d9a6
workflow-type: tm+mt
source-wordcount: '468'
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
1. Klicken Sie im Seitenbereich unter **Dienste** auf **CDN-Konfigurationen**.
1. Klicken Sie in der Tabelle **CDN-Konfigurationen** auf das Auslassungszeichen am Ende einer Zeile, deren CDN-Konfiguration Sie bearbeiten möchten.

   ![Bearbeiten einer CDN-Konfiguration](/help/implementing/cloud-manager/assets/cdn-config-edit.png)

1. Klicken Sie auf **Bearbeiten**.
1. Legen Sie im Dialogfeld **CDN-Konfiguration bearbeiten** eine oder mehrere der Optionen in der entsprechenden Dropdownliste fest.

   Die Optionen, die im Dialogfeld angezeigt werden, variieren je nachdem, ob Sie ein von Adobe verwaltetes CDN oder ein kundenverwaltetes CDN verwenden.

1. Klicken Sie auf **Aktualisieren**.

   Der Status des bearbeiteten CDN wird in der Tabelle **CDN-Konfigurationen** aktualisiert, um die vorgenommenen Änderungen widerzuspiegeln.

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


