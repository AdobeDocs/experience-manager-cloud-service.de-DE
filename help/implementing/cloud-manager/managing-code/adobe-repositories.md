---
title: Hinzufügen eines Adobe-Repositorys in Cloud Manager
description: Erfahren Sie, wie Sie in Cloud Manager ein Adobe-verwaltetes Repository hinzufügen.
exl-id: 6c32c4ae-f48d-4440-bfc2-cdc1a3d59599
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: f2364de6237ca9f0285815b581bcf3881488188d
workflow-type: tm+mt
source-wordcount: '231'
ht-degree: 7%

---

# Adobe-Repository in Cloud Manager hinzufügen {#adobe-repositories}

Erfahren Sie, wie Sie in Cloud Manager ein Adobe-verwaltetes Repository hinzufügen.

Die Seite **Repositorys** erleichtert das Hinzufügen zusätzlicher von Adobe verwalteter Repositorys zu einem ausgewählten Programm.

**Hinzufügen eines Adobe-Repositorys in Cloud Manager:**

1. Melden Sie sich bei Cloud Manager unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) an und wählen Sie die entsprechende Organisation und das Programm aus, zu dem Sie ein von Adobe verwaltetes Repository hinzufügen möchten.

1. Klicken Sie auf der Seite **Programmübersicht** im Seitenmenü auf die Registerkarte ![Ordnersymbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Folder_18_N.svg) **Repositorys** .

1. Klicken Sie auf der Seite **Repositorys** oben rechts auf **Repository hinzufügen**.

   ![Schaltfläche „Repository hinzufügen“](assets/add-repository.png)

1. Stellen Sie im Dialogfeld **Repository hinzufügen** sicher, dass **Adobe Repository** als Repository-Typ ausgewählt ist.

1. Geben Sie in die entsprechenden Textfelder Folgendes ein:

   * **Repository name** - Ein ausdrucksstarker Name für Ihr neues Repository.
   * **Vorschau der Repository-URL** - Sie müssen keinen URL-Pfad eingeben oder den vorhandenen Pfad bearbeiten, da die Repository-Infrastruktur bereits vorhanden ist und vollständig von Adobe integriert und verwaltet wird.
   * **Beschreibung (optional)** - Eine detaillierte Beschreibung des Repositorys.

   ![Dialogfeld &quot;Repository hinzufügen&quot;](assets/add-adobe-repository.png)

1. Klicken Sie auf **Speichern**.
Ihr neues Repository wird in der Tabelle auf der Seite **Repositorys** angezeigt.

Sie können jetzt eine [CI/CD-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md) damit verknüpfen oder sie auf der Seite [**Repositorys**](managing-repositories.md) verwalten.

>[!TIP]
>
>Sie können auch GitHub-Repositorys hinzufügen, die Sie selbst als [private Repositorys](private-repositories.md) verwalten.
