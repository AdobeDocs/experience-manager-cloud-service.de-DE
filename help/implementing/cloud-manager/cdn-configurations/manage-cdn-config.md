---
title: Verwalten von CDN-Konfigurationen
description: Erfahren Sie, wie Sie mit Cloud Manager CDN-Konfigurationen für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung bearbeiten, aktualisieren oder löschen können.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 70f99cfb2cd00278d9ebbb7972ef455af7a87a1b
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 8%

---


# Verwalten von CDN-Konfigurationen {#manage-cdn-configurations}

Erfahren Sie, wie Sie mit Cloud Manager CDN-Konfigurationen für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung bearbeiten, aktualisieren oder löschen können.

## Bearbeiten einer CDN-Konfiguration {#edit-cdn}

Beim Bearbeiten einer CDN-Konfiguration können Sie Einstellungen wie die Umgebungsebene (Publish oder Vorschau) oder SSL-Zertifikate anpassen, ohne die vorhandene Konfiguration vollständig zu entfernen. Änderungen gelten für die ausgewählte Umgebung, z. B. für Staging oder Produktion, und können sich auf die Bereitstellung und Sicherung von Inhalten auswirken.

Ein Benutzer muss Mitglied der Rolle **Business Owner** oder **Deployment Manager** sein, um diese Aufgabe abzuschließen.

**So bearbeiten Sie eine CDN-Konfiguration:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie im linken Navigationsbereich unter **Dienste** auf **CDN-Konfigurationen**.

1. Klicken Sie in der Tabelle **CDN-Konfigurationen** auf die Auslassungszeichen am Ende einer Zeile, deren CDN Sie aktualisieren möchten.

   ![Bearbeiten einer CDN-Konfiguration](/help/implementing/cloud-manager/assets/cdn-config-edit.png)

1. Klicken Sie auf **Bearbeiten**.

1. Legen Sie im Dialogfeld **CDN bearbeiten** eine oder mehrere der Optionen in der entsprechenden Dropdownliste fest.

   Die Optionen, die Sie im Dialogfeld sehen, können variieren, je nachdem, ob Sie ein von Adobe verwaltetes CDN oder ein kundenverwaltetes CDN verwenden.

1. Klicken Sie auf **Aktualisieren**.

   Der Status des bearbeiteten CDN wird in der Tabelle **CDN-Konfigurationen** aktualisiert, um die vorgenommenen Änderungen widerzuspiegeln.


## Löschen einer CDN-Konfiguration {#delete-cdn}

Wenn Sie eine von Adobe verwaltete oder kundenverwaltete CDN-Konfiguration in Adobe Cloud Manager löschen, werden die Routing- und SSL-Zertifikateinstellungen der zugehörigen Domäne entfernt. Die Domäne verwendet das CDN nicht mehr für die Traffic-Bereitstellung und alle vom CDN bereitgestellten Sicherheits- oder Leistungsverbesserungen gehen verloren. Sie können Dienstunterbrechungen feststellen, bis eine neue Konfiguration eingerichtet ist, unabhängig davon, ob Sie das gelöschte CDN erneut hinzufügen oder eine neue hinzufügen.

Ein Benutzer muss Mitglied der Rolle **Business Owner** oder **Deployment Manager** sein, um diese Aufgabe abzuschließen.

**So löschen Sie eine CDN-Konfiguration:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie im linken Navigationsbereich unter **Dienste** auf **CDN-Konfigurationen**.

1. Klicken Sie in der Tabelle CDN-Konfigurationen am Ende einer Zeile, deren CDN Sie entfernen möchten, auf das Auslassungszeichen.

   ![Löschen einer CDN-Konfiguration](/help/implementing/cloud-manager/assets/cdn-config-delete.png)

1. Klicken Sie auf **Löschen**.
1. Klicken Sie erneut auf **Löschen** , um das Entfernen des CDN der Site zu bestätigen.


