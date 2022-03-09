---
title: Zugriff auf Repositorys
description: Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihr Git-Repository zugreifen und es verwalten können.
exl-id: 0c0671a3-e400-46f3-ad86-166a6cfdd44b
source-git-commit: 4729574eb31e01077f0d2a35efcef6d134f6aa5c
workflow-type: tm+mt
source-wordcount: '229'
ht-degree: 8%

---

# Zugriff auf Repositorys {#accessing-repos}

Erfahren Sie, wie Sie mithilfe der Self-Service-Git-Kontoverwaltung über Cloud Manager auf Ihr Git-Repository zugreifen und es verwalten können.

## Verwenden der Self-Service-Repository-Kontoverwaltung {#self-service-repos}

Cloud Manager erleichtert das Abrufen Ihrer Repository-Informationen mithilfe der **Zugriff auf Repo Info** auf der Pipeline-Karte verfügbar.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Navigieren Sie zu **Pipelines** Karte aus **Programmübersicht** und suchen Sie nach **Zugriff auf Repo Info** -Schaltfläche, um auf Ihr Git-Repository zuzugreifen und es zu verwalten.

   ![Schaltfläche &quot;Repo Info&quot;auf der Karte &quot;Umgebungen&quot;aufrufen](/help/implementing/cloud-manager/assets/repos/access-repo1.png)

1. Klicken Sie auf **Repo Info anzeigen** Schaltfläche zum Öffnen eines Dialogfelds zur Ansicht:

   * Die URL zum Git-Repository von Cloud Manager.
   * Der Git-Benutzername.
   * Das Git-Kennwort, dessen Wert beim **Kennwort generieren** auf klicken.

   ![](/help/implementing/cloud-manager/assets/repos/access-repo-create.png)

Mithilfe dieser Anmeldeinformationen kann der Benutzer eine lokale Kopie des Repositorys klonen und Änderungen an diesem lokalen Repository vornehmen. Sobald dies möglich ist, kann er alle Code-Änderungen wieder in das Remote-Code-Repository in Cloud Manager übertragen.

Die **Zugriff auf Repo Info** ist auch auf der **Nicht Produktion** Pipeline-Registerkarte der **Pipelines** Karte.

![Schaltfläche &quot;Repo Info&quot;auf Nicht-Produktions-Registerkarte aufrufen](/help/implementing/cloud-manager/assets/repos/access-repo-nonprod.png)

>[!NOTE]
>
>Die **Zugriff auf Repo Info** -Option für Benutzer mit **Entwickler** oder **Bereitstellungsmanager** Rollen.
