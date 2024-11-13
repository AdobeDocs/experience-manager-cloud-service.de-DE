---
title: Verwalten von CDN-Konfigurationen
description: Erfahren Sie, wie Sie mit Cloud Manager CDN-Konfigurationen für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung bearbeiten, aktualisieren oder löschen können.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 2ec16c91-0195-4732-a26d-ac223e10afb9
source-git-commit: ea478d73307c3b57b0a12e35b247bb1c46b33595
workflow-type: tm+mt
source-wordcount: '773'
ht-degree: 14%

---

# Verwalten von CDN-Konfigurationen {#manage-cdn-configurations}

Erfahren Sie, wie Sie mit Cloud Manager CDN-Konfigurationen für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung bearbeiten oder löschen können.

## Bearbeiten einer CDN-Konfiguration über die Seite &quot;CDN-Konfigurationen&quot; {#edit-cdn}

Unter Adobe Cloud Manager können Sie aus verschiedenen Gründen eine CDN-Konfiguration (Content Delivery Network) bearbeiten, einschließlich der Umgebungsebene (Publish oder Vorschau) und des SSL-Zertifikats.

* **Umgebungsänderungen**: Das Anpassen der Ebene hilft, die CDN-Einstellungen mit der richtigen Umgebung abzustimmen, sei es für die Live-Produktion (Publish) oder für Tests (Vorschau).
* **Sicherheitsverbesserungen**: Bei der Aktualisierung von Zertifikaten oder der Erfüllung von Compliance- und Sicherheitsanforderungen kann die Auswahl eines anderen SSL-Zertifikats erforderlich sein.
* **Leistungsoptimierung**: Durch die Bearbeitung der Konfiguration werden die richtigen CDN-Einstellungen für die Bereitstellung von Inhalten auf der Grundlage sich ändernder betrieblicher Anforderungen sichergestellt.

Sie können eine Konfiguration bearbeiten, ohne die vorhandene Konfiguration vollständig zu entfernen. Änderungen gelten für die ausgewählte Umgebung, z. B. für Staging oder Produktion, und können sich auf die Bereitstellung und Sicherung von Inhalten auswirken.

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**So bearbeiten Sie eine CDN-Konfiguration über die Seite &quot;CDN-Konfigurationen&quot;:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Klicken Sie im Menü auf der linken Seite unter **Dienste** auf das Symbol für das soziale Netzwerk ![3} **CDN-Konfigurationen**.](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg)
1. Klicken Sie in der Tabelle **CDN-Konfigurationen** am Ende einer Zeile, deren CDN-Konfiguration Sie aktualisieren möchten, auf das Symbol &quot;![Mehr&quot;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) .

1. Klicken Sie im Dropdown-Menü auf **Bearbeiten**.

1. Legen Sie im Dialogfeld **CDN-Konfiguration bearbeiten** eine oder mehrere der Optionen in der entsprechenden Dropdownliste fest.

   Die im Dialogfeld angezeigten Optionen hängen davon ab, ob Sie ein **vom Adobe verwaltetes CDN** oder einen **anderen CDN-Anbieter** (kundenverwaltetes CDN) verwenden.

1. Klicken Sie auf **Aktualisieren**.

   Der Status des bearbeiteten CDN wird in der Tabelle **CDN-Konfigurationen** aktualisiert, um die vorgenommenen Änderungen widerzuspiegeln.


## Bearbeiten einer CDN-Konfiguration auf der Seite Umgebungen

Die Schritte zum Bearbeiten einer CDN-Konfiguration auf der Seite **Umgebungen** sind fast dieselben wie beim Bearbeiten einer CDN-Konfiguration auf der Seite &quot;CDN-Konfigurationen&quot;](#edit-cdn), doch der Einstiegspunkt unterscheidet sich.[

**So bearbeiten Sie eine CDN-Konfiguration auf der Seite &quot;Umgebungen&quot;:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie im Menü auf der linken Seite auf **Umgebungen**.

1. Wählen Sie auf der Seite **Umgebungen** eine Umgebung von Interesse aus.

1. Klicken Sie auf der Seite mit den Umgebungsdetails in der Gruppierung der CDN-Konfigurationen auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) , das der zu bearbeitenden CDN-Konfiguration entspricht.

1. Klicken Sie im Popup-Menü auf **Bearbeiten**.

1. Legen Sie im Dialogfeld **CDN-Konfiguration bearbeiten** eine oder mehrere der Optionen in der entsprechenden Dropdownliste fest.

   Die im Dialogfeld angezeigten Optionen hängen davon ab, ob Sie ein **vom Adobe verwaltetes CDN** oder einen **anderen CDN-Anbieter** (kundenverwaltetes CDN) verwenden.

1. Klicken Sie auf **Aktualisieren**.


<!-- ## Go live readiness {#go-live-readiness} 

1. ADD STEPS -->


## Löschen einer CDN-Konfiguration {#delete-cdn}

Wenn Sie eine von Adobe verwaltete oder kundenverwaltete CDN-Konfiguration in Cloud Manager löschen, werden die Routing- und SSL-Zertifikateinstellungen der zugehörigen Domäne entfernt. Die Domäne verwendet das CDN nicht mehr für die Traffic-Bereitstellung und alle vom CDN bereitgestellten Sicherheits- oder Leistungsverbesserungen gehen verloren. Sie können Dienstunterbrechungen feststellen, bis eine neue Konfiguration eingerichtet ist, unabhängig davon, ob Sie das gelöschte CDN erneut hinzufügen oder eine neue hinzufügen.

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**So löschen Sie eine CDN-Konfiguration:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie im Menü auf der linken Seite unter **Dienste** auf **CDN-Konfigurationen**.

1. Klicken Sie in der Tabelle &quot;CDN-Konfigurationen&quot;am Ende einer Zeile, die einem CDN entspricht, das Sie entfernen möchten, auf das Symbol ![Mehr](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und klicken Sie dann auf **Löschen**.

1. Klicken Sie im Dialogfeld **CDN-Konfiguration löschen** auf **Löschen**.

1. Klicken Sie erneut auf **Löschen** , um das Entfernen des CDN der Site zu bestätigen.


## Löschen einer CDN-Konfiguration von der Seite &quot;Umgebungen&quot;

Die Schritte zum Löschen einer CDN-Konfiguration von der Seite **Umgebungen** sind fast identisch mit dem Löschen einer CDN-Konfiguration von der Seite &quot;CDN-Konfigurationen&quot;](#edit-cdn), doch der Einstiegspunkt unterscheidet sich.[

**So löschen Sie eine CDN-Konfiguration von der Seite &quot;Umgebungen&quot;:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie im Menü auf der linken Seite auf **Umgebungen**.

1. Wählen Sie auf der Seite **Umgebungen** eine Umgebung von Interesse aus.

1. Klicken Sie auf der Seite mit den Umgebungsdetails in der Gruppe **CDN-Konfigurationen** auf das Symbol ![Mehr ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) , das der zu entfernenden CDN-Konfiguration entspricht, und klicken Sie dann auf **Löschen**.

1. Klicken Sie im Dialogfeld **CDN-Konfiguration löschen** auf **Löschen**.

1. Klicken Sie erneut auf **Löschen** , um das Entfernen des CDN der Site zu bestätigen.
