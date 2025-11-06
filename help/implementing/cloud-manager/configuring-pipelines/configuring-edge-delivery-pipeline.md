---
title: Hinzufügen einer Pipeline von Edge Delivery
description: Erfahren Sie, wie Sie eine Pipeline von Edge Delivery hinzufügen, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Developer
hide: false
index: false
hidefromtoc: false
exl-id: 5ad342fa-dd71-4105-a9cb-2d999d402780
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 71%

---

# Hinzufügen einer Pipeline von Edge Delivery {#configure-production-pipeline}

<!--badge: label="Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md#gitlab-bitbucket" -->

Erfahren Sie, wie Sie Edge Delivery-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen. Mit Edge Delivery-Pipelines können Sie Funktionen wie die Protokollweiterleitung und das von Adobe verwaltete CDN konfigurieren.

Eine Liste der unterstützten Konfigurationen finden Sie unter [Verwenden von Konfigurations-Pipelines - Unterstützte Konfigurationen](/help/operations/config-pipeline.md#configurations).

Benutzende müssen über die Rolle **[Bereitstellungs-Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** verfügen, um Produktions-Pipelines konfigurieren zu können.

>[!IMPORTANT]
>
>Eine Edge Delivery-Pipeline lässt sich erst konfigurieren, nachdem folgende Aufgaben erledigt wurden:
>
>* Es wurde ein Programm erstellt, das eine Edge Delivery Services-Site und eine zugeordnete Domain enthält. Andernfalls wird die Option **Edge Delivery-Pipeline hinzufügen** in der Benutzeroberfläche deaktiviert angezeigt und in einer QuickInfo werden fehlende Anforderungen erläutert. Siehe [Erstellen einer Edge Delivery-Site in Cloud Manager](/help/implementing/cloud-manager/edge-delivery/create-edge-delivery-site.md)
>* Das Git-Repository hat mindestens eine Verzweigung. Siehe [Verwalten von Repositorys in Cloud Manager](/help/implementing/cloud-manager/managing-code/managing-repositories.md).
>* Die Produktions- und Staging-Umgebungen sind erstellt. Siehe [Einführung in CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

<!-- CMGR‑69680 -->

Konfigurieren Sie Ihre Pipeline-Einstellungen über [!UICONTROL Cloud Manager], bevor Sie Code bereitstellen.

>[!NOTE]
>
>Nach der Ersteinrichtung können Sie die [Pipeline-Einstellungen bearbeiten](managing-pipelines.md).

**Hinzufügen einer Pipeline von Edge Delivery:**

1. Melden Sie sich bei Cloud Manager unter [experience.adobe.com](https://experience.adobe.com) an.
1. Klicken Sie **Abschnitt „Schnellzugriff** auf **Experience Manager**.
1. Klicken Sie im linken Panel auf **Cloud Manager**.
1. Wählen Sie die gewünschte Organisation aus.
1. Klicken Sie in **Konsole** Meine Programme“ auf ein Programm.

   ![Die Seite „Meine Programme“ in Cloud Manager](/help/implementing/cloud-manager/configuring-pipelines/assets/my-programs.png)

1. Führen Sie einen der folgenden Schritte aus:

   * **Hinzufügen einer Edge Delivery-Pipeline über die Karte „Pipelines“**

      1. Klicken Sie in der linken Leiste unter **Programm** auf **![Überblickssymbol](/help/implementing/cloud-manager/configuring-pipelines/assets/overview.svg) [Überblick](/help/implementing/cloud-manager/navigation.md#my-programs)**.
      1. Klicken Sie auf der Seite **Programmüberblick** unter der Karte **Pipelines** auf **![Pluszeichen](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Add_18_N.svg)Hinzufügen** und wählen Sie dann **Edge Delivery-Pipeline hinzufügen**.

         ![Die Karte „Pipelines“ auf der Seite „Programmüberblick“](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinescard-add-ed-pipeline.png)

         >[!TIP]
         >
         >Neben der Verwendung der Karte **Pipeline** wie im obigen Screenshot gezeigt, können Sie Ihre Pipeline auch über die Seite **Pipelines** verwalten.
         >
         >![Edge Delivery-Pipeline-Widget, das Pipeline-Namen, -Status, -Repository und -Verzweigung anzeigt](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)

   * **Hinzufügen einer Edge Delivery-Pipeline über die Seite „Pipelines“**

      1. Klicken Sie in der linken Leiste unter **Programm** auf das **![Workflow-Symbol oder Pipelines-Symbol](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Workflow_18_N.svg) Pipelines**.
      1. Klicken Sie auf der Seite „Pipelines“ oben rechts auf **Pipeline hinzufügen** > **Edge Delivery-Pipeline hinzufügen**.

         ![Die Seite „Pipelines“ mit der Schaltfläche „Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/pipelinespage-add-ed-pipeline.png)

         >[!TIP]
         >
         >Klicken Sie links oben auf **Filter** und aktivieren Sie dann im Abschnitt **Versandtyp** das Kontrollkästchen **Edge-**, um die Liste nur nach Edge Delivery-Pipelines (d. h. Pipelines, die Edge Delivery Services verwenden) zu filtern. <!-- (CMGR-69682) -->
         >
         >![Filterbedienfeld, das den neuen Bereitstellungstyp der Edge-Bereitstellung und der Veröffentlichungsbereitstellung anzeigt](/help/implementing/cloud-manager/release-notes/assets/filter-delivery-type.png)

1. Geben Sie im Dialogfeld **Edge Delivery-Pipeline hinzufügen** im Textfeld **Pipeline-Name** einen beschreibenden Pipeline-Titel ein.

   ![Dialogfeld „Edge Delivery-Pipeline hinzufügen“](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-configuration.png)

1. Wählen Sie die **Pipeline-Option** Bereitstellungs-Trigger) aus.

   * **Manuell**: Sie starten die Bereitstellung.
   * **Bei Git-Änderungen**: Git-Commits starten die Bereitstellung automatisch. Auch bei dieser Option können Sie die Pipeline bei Bedarf manuell starten.

1. Klicken Sie auf **Weiter**.

1. Definieren Sie unter **Quell-Code** die folgenden Optionen:

   * **Bereitstellungsumgebung**: Zeigt das Zielumgebungsfeld an; bleibt schreibgeschützt.

   * **Repository**: Verwenden Sie die Dropdown-Liste, um die Pipeline auf das exakte Git-Repository zu verweisen, in dem die Edge Delivery-Konfiguration gespeichert ist.

     Weitere Informationen dazu, wie Sie Repositorys in Cloud Manager hinzufügen und verwalten, finden Sie unter [Hinzufügen und Verwalten von Repositorys](/help/implementing/cloud-manager/managing-code/managing-repositories.md).

   * **Git-Verzweigung**: Wählen Sie in der Dropdown-Liste eine bestimmte Verzweigung im ausgewählten Repository aus. Klicken Sie bei Bedarf auf ![Symbol „Recyceln“ oder &#x200B;](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Refresh_18_N.svg) „Aktualisieren“, um die Dropdown-Liste „Git-Verzweigung“ nach den letzten Push-Benachrichtigungen neu zu laden.
   * **Code-Speicherort**: Definiert den Ordnerpfad innerhalb des Repositorys, in dem Pipeline-fähiger Code beginnt (`/` entspricht dem Repository-Stamm).

   ![Konfigurations-Pipeline](/help/implementing/cloud-manager/configuring-pipelines/assets/add-edge-delivery-pipeline-sourcecode.png)

1. Klicken Sie auf **Speichern**.

Sie können [Ihre Pipeline verwalten](managing-pipelines.md) über die Karte **Pipelines** auf der Seite **Programmübersicht** oder über die Seite **Pipelines**.


![Edge Delivery-Pipeline-Widget, das Pipeline-Namen, -Status, -Repository und -Verzweigung anzeigt](/help/implementing/cloud-manager/release-notes/assets/edge-delivery-pipeline-widget.png)



