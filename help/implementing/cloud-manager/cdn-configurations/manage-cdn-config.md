---
title: Verwalten von Domain-Zuordnungen
description: Erfahren Sie, wie Sie mit Cloud Manager CDN-Konfigurationen für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung bearbeiten, aktualisieren oder löschen können.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
exl-id: 2ec16c91-0195-4732-a26d-ac223e10afb9
source-git-commit: 1683d53491e06ebe2dfcc96184ce251539ecf732
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 100%

---

# Verwalten von Domain-Zuordnungen {#manage-cdn-configurations}

Erfahren Sie, wie Sie mit Cloud Manager CDN-Konfigurationen für eine Edge Delivery-Site oder eine Cloud Manager-Umgebung bearbeiten oder löschen können.

## Bearbeiten einer CDN-Konfiguration auf der Seite „Domain-Zuordnungen“ {#edit-cdn}

In Adobe Cloud Manager kann es verschiedene Gründe geben, dass Sie eine CDN-Konfiguration (Content Delivery Network) einschließlich der Umgebungsebene (Veröffentlichung oder Vorschau) und des SSL-Zertifikats bearbeiten möchten.

* **Umgebungsänderungen**: Das Anpassen der Ebene hilft dabei, die CDN-Einstellungen mit der richtigen Umgebung abzustimmen, sei es für die Live-Produktion (Veröffentlichen) oder für Tests (Vorschau).
* **Sicherheitserweiterungen**: Bei der Aktualisierung von Zertifikaten oder der Erfüllung von Compliance- und Sicherheitsanforderungen kann die Auswahl eines anderen SSL-Zertifikats erforderlich sein.
* **Leistungsoptimierung**: Durch das Bearbeiten der Konfiguration werden die richtigen CDN-Einstellungen für das Bereitstellen von Inhalten auf der Grundlage sich ändernder betrieblicher Anforderungen sichergestellt.

Sie können eine Konfiguration bearbeiten, ohne die vorhandene Konfiguration vollständig zu entfernen. Änderungen gelten für die ausgewählte Umgebung, z. B. für die Staging- oder Produktionsumgebung, und können sich auf die Bereitstellung und Sicherung von Inhalten auswirken.

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**So bearbeiten Sie eine CDN-Konfiguration auf der Seite „Domain-Zuordnungen“:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.
1. Klicken Sie im linken Seitenmenü unter **Services** auf ![Symbol für soziale Netzwerke](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Domain-Zuordnungen**.
1. Klicken Sie in der Tabelle **Domain-Zuordnungen** auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) am Ende einer Zeile, deren CDN-Konfiguration Sie aktualisieren möchten.

1. Klicken Sie im Dropdown-Menü auf **Bearbeiten**.

1. Legen Sie im Dialogfeld **CDN-Konfiguration bearbeiten** eine oder mehrere der Optionen in der entsprechenden Dropdown-Liste fest.

   Die im Dialogfeld angezeigten Optionen hängen davon ab, ob Sie ein **von Adobe verwaltetes CDN** oder einen **anderen CDN-Anbieter** (kundenseitig verwaltetes CDN) verwenden.

1. Klicken Sie auf **Aktualisieren**.

   Der Status des bearbeiteten CDN wird in der Tabelle **Domain-Zuordnungen** aktualisiert, um die vorgenommenen Änderungen widerzuspiegeln.


## Bearbeiten einer CDN-Konfiguration auf der Seite „Umgebungen“

Die Schritte zum Bearbeiten einer CDN-Konfiguration von der Seite **Umgebungen** aus sind nahezu dieselben wie beim [Bearbeiten einer CDN-Konfiguration von der Seite „Domain-Zuordnungen“ aus](#edit-cdn), der Einstiegspunkt ist jedoch ein anderer.

**So bearbeiten Sie eine CDN-Konfiguration auf der Seite „Umgebungen“:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie im linken Seitenmenü auf ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Umgebungen**. 

1. Wählen Sie auf der Seite **Umgebungen** eine Umgebung von Interesse aus.

1. Klicken Sie auf der Seite mit den Umgebungsdetails in der Gruppierung „Domain-Zuordnungen“ auf das Symbol ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), das der CDN-Konfiguration entspricht, die Sie bearbeiten möchten.

1. Klicken Sie im Popup-Menü auf **Bearbeiten**.

1. Legen Sie im Dialogfeld **CDN-Konfiguration bearbeiten** eine oder mehrere der Optionen in der entsprechenden Dropdown-Liste fest.

   Welche Optionen im Dialogfeld angezeigt werden, hängt davon ab, ob Sie ein **von Adobe verwaltetes CDN** oder einen **anderen CDN-Anbieter** (kundenseitig verwaltetes CDN) verwenden.

1. Klicken Sie auf **Aktualisieren**.


<!-- ## Go live readiness {#go-live-readiness} 

1. ADD STEPS -->


## Löschen einer CDN-Konfiguration {#delete-cdn}

Wenn Sie eine von Adobe verwaltete oder eine kundenseitig verwaltete CDN-Konfiguration in Cloud Manager löschen, werden die Routing- und SSL-Zertifikatseinstellungen der zugehörigen Domain entfernt. Die Domain verwendet das CDN nicht mehr für die Traffic-Bereitstellung, und alle vom CDN bereitgestellten Sicherheitserweiterungen oder Leistungsverbesserungen gehen verloren. Es können Dienstunterbrechungen auftreten, bis eine neue Konfiguration eingerichtet ist. Dies ist unabhängig davon, ob Sie das gelöschte CDN erneut hinzufügen oder eine neues CDN hinzufügen.

Eine Person muss über die Rolle **Geschäftsinhaber** oder **Bereitstellungs-Manager** verfügen, um diese Aufgabe abzuschließen.

**So löschen Sie eine CDN-Konfiguration:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie im linken Seitenmenü unter **Services** auf ![Symbol für soziale Netzwerke](https://spectrum.adobe.com/static/icons/workflow_18/Smock_SocialNetwork_18_N.svg) **Domain-Zuordnungen**.

1. Klicken Sie in der Tabelle „Domain-Zuordnungen“ am Ende einer Zeile, die einem zu entfernenden CDN entspricht, auf ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg) und dann auf **Löschen**.

1. Klicken Sie im Dialogfeld **CDN-Konfiguration löschen** auf **Löschen**.

1. Klicken Sie erneut auf **Löschen**, um das Entfernen des CDN der Site zu bestätigen.


## Löschen einer CDN-Konfiguration auf der Seite „Umgebungen“

Die Schritte zum Löschen einer CDN-Konfiguration auf der Seite **Umgebungen** sind nahezu mit denen beim [Löschen einer CDN-Konfiguration auf der Seite „Domain-Zuordnungen“](#edit-cdn) identisch, der Einstiegspunkt ist jedoch ein anderer.

**So löschen Sie eine CDN-Konfiguration auf der Seite „Umgebungen“:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation sowie das entsprechende Programm aus.

1. Klicken Sie im linken Seitenmenü auf ![Datensymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Data_18_N.svg) **Umgebungen**. 

1. Wählen Sie auf der Seite **Umgebungen** eine Umgebung von Interesse aus.

1. Klicken Sie auf der Seite mit den Umgebungsdetails in der Gruppierung **Domain-Zuordnungen** auf das Symbol ![Mehr-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_More_18_N.svg), das der CDN-Konfiguration entspricht, die Sie entfernen möchten. Klicken Sie dann auf **Löschen**.

1. Klicken Sie im Dialogfeld **CDN-Konfiguration löschen** auf **Löschen**.

1. Klicken Sie erneut auf **Löschen**, um das Entfernen des CDN der Site zu bestätigen.
