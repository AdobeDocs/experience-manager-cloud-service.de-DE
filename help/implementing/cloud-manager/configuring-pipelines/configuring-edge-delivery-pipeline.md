---
title: Hinzufügen einer Pipeline von Edge Delivery
description: Erfahren Sie, wie Sie eine Pipeline von Edge Delivery hinzufügen, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Private Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket"
hide: false
index: false
hidefromtoc: false
source-git-commit: 62134c5b67d610f801c407e696e761ed05e02c87
workflow-type: tm+mt
source-wordcount: '489'
ht-degree: 26%

---


# Hinzufügen einer Pipeline von Edge Delivery {#configure-production-pipeline}

Erfahren Sie, wie Sie Edge Delivery-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen. Eine Produktions-Pipeline stellt Code zuerst in der Staging-Umgebung bereit. Nach der Genehmigung wird derselbe Code in der Produktionsumgebung bereitgestellt.

Benutzende müssen über die Rolle **[Bereitstellungs-Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** verfügen, um Produktions-Pipelines konfigurieren zu können.

>[!NOTE]
>
>Eine Edge Delivery-Pipeline kann erst konfiguriert werden, wenn Folgendes passiert ist:
>
>* Ein Programm wird erstellt, das eine Edge Delivery Services-Site und eine zugeordnete Domain enthält. Andernfalls wird die Option **Edge Delivery-Pipeline hinzufügen** in der Benutzeroberfläche deaktiviert angezeigt und in einer QuickInfo werden fehlende Anforderungen erläutert.
>* Das Git-Repository hat mindestens eine Verzweigung.
>* Die Produktions- und Staging-Umgebungen sind erstellt.

<!-- CMGR‑69680 -->


Konfigurieren Sie Ihre Pipeline-Einstellungen über [!UICONTROL Cloud Manager], bevor Sie Code bereitstellen.

>[!NOTE]
>
>Sie können [Pipeline-Einstellungen bearbeiten](managing-pipelines.md) nach der ersten Konfiguration.

**So fügen Sie eine Edge Delivery-Pipeline hinzu:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die gewünschte Organisation aus.

1. Wählen Sie auf **Seite** Meine Programme“ das gewünschte Programm aus.

   ![Meine Programmseite in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/assets/my-programs.png)

1. Führen Sie einen der folgenden Schritte aus:

   * **Fügen Sie eine Edge Delivery-Pipeline über die Karte „Pipelines“ hinzu**

      1. Klicken Sie in der linken Leiste unter **Programm** auf **![Übersichtssymbol](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) [Übersicht](/help/implementing/cloud-manager/navigation.md#my-programs)**.
      1. Klicken Sie auf der **Programmübersicht** auf der Karte **Pipelines** auf **![Pluszeichen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)Hinzufügen** und wählen Sie dann **Edge Delivery-Pipeline hinzufügen**.

         ![Die Karte Pipelines auf der Seite Programmübersicht](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinescard-add-ed-pipeline.png)

   * **Fügen Sie eine Edge Delivery-Pipeline über die Seite Pipelines hinzu**

      1. Klicken Sie in der linken Leiste unter **Programm** auf **![Workflow-Symbol oder Pipelines-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) Pipelines**.
      1. Klicken Sie auf der Seite „Pipelines“ oben rechts auf **Pipeline hinzufügen** > **Edge Delivery-Pipeline hinzufügen**.

         ![Die Seite „Pipelines“ mit der Schaltfläche „Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinespage-add-ed-pipeline.png)

1. Geben **im Dialogfeld &quot;Edge Delivery** Pipeline hinzufügen“ im Textfeld **Pipeline-Name** eine beschreibende Pipeline-Beschriftung ein.

   ![Dialogfeld &quot;Edge Delivery-Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-configuration.png)

1. Wählen Sie die **Pipeline (Bereitstellungs-Trigger** gewünschte Option aus.

   * **Manuell** Sie starten die Bereitstellung.
   * **Bei Git-**: Git-Commits starten die Bereitstellung automatisch. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

1. Klicken Sie auf **Weiter**.

1. Legen Sie unter **Source** Code) die folgenden Optionen fest:

   * **Bereitstellungsumgebung**: Zeigt das Feld Zielumgebung an; bleibt schreibgeschützt.

   * **Repository**: Verwenden Sie die Dropdown-Liste, um die Pipeline auf das exakte Git-Repository zu verweisen, in dem die Edge Delivery-Konfiguration gespeichert ist.

     Siehe auch [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md), um zu erfahren, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten.

   * **Git-Verzweigung** - Wählen Sie in der Dropdown-Liste eine bestimmte Verzweigung im ausgewählten Repository aus. Klicken Sie bei Bedarf auf ![Symbol „Recyceln“ oder ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg)-Symbol aktualisieren, um die Dropdown-Liste der Git-Verzweigungen nach den letzten Push-Benachrichtigungen neu zu laden
   * **Code-Speicherort** - Definiert den Ordnerpfad innerhalb des Repositorys, in dem Pipeline-fähiger Code beginnt (`/` entspricht dem Repository-Stamm).

   ![Konfigurations-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-sourcecode.png)

1. Klicken Sie auf **Speichern**.

Sie können [Ihre Pipeline verwalten](managing-pipelines.md) auf der Karte **Pipelines** auf der Seite **Programmübersicht** oder auf der Seite **Pipelines**.
