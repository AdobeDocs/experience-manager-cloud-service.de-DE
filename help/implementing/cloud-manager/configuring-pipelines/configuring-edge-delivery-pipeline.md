---
title: Hinzufügen einer Pipeline von Edge Delivery
description: Erfahren Sie, wie Sie eine Pipeline von Edge Delivery hinzufügen, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen.
index: false
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
badge: label="Private Beta" type="Positive" url="/help/implementing/cloud-manager/release-notes/current.md
hide: true
hidefromtoc: true
source-git-commit: 169de7971fba829b0d43e64d50a356439b6e57ca
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 94%

---



# Hinzufügen einer Pipeline von Edge Delivery {#configure-production-pipeline}

Erfahren Sie, wie Sie Edge Delivery-Pipelines konfigurieren, um Ihren Code zu erstellen und in Produktionsumgebungen bereitzustellen. Eine Produktions-Pipeline stellt Code zuerst in der Staging-Umgebung bereit. Nach der Genehmigung wird derselbe Code in der Produktionsumgebung bereitgestellt.

Benutzende müssen über die Rolle **[Bereitstellungs-Manager](/help/onboarding/cloud-manager-introduction.md#role-based-permissions)** verfügen, um Produktions-Pipelines konfigurieren zu können.

>[!NOTE]
>
>Eine Produktions-Pipeline kann erst eingerichtet werden, wenn Folgendes gegeben ist:
>
>* Das Programm ist erstellt. 
>* Das Git-Repository hat mindestens eine Verzweigung.
>* Die Produktions- und Staging-Umgebungen sind erstellt.

Konfigurieren Sie Ihre Pipeline-Einstellungen über [!UICONTROL Cloud Manager], bevor Sie Code bereitstellen.

>[!NOTE]
>
>Nach der Ersteinrichtung können Sie die [Pipeline-Einstellungen bearbeiten](managing-pipelines.md).

## Neue Edge Delivery-Pipeline hinzufügen {#adding-production-pipeline}

Sobald Sie mit der Benutzeroberfläche von [!UICONTROL Cloud Manager] Ihr Programm eingerichtet und mindestens eine Umgebung haben, können Sie eine Produktions-Pipeline hinzufügen, indem Sie die folgenden Schritte ausführen.

>[!TIP]
>
>Bevor Sie eine Frontend-Pipeline konfigurieren, lesen Sie die [Tour zur schnellen AEM-Site-Erstellung](/help/journey-sites/quick-site/overview.md). Dort finden Sie eine vollständige Anleitung für das benutzerfreundliche Tool zur schnellen AEM-Site-Erstellung. Diese Tour hilft Ihnen, die Frontend-Entwicklung Ihrer AEM-Site zu optimieren und Ihre Site ohne AEM-Backend-Kenntnisse schnell anzupassen.

**So fügen Sie eine neue Edge Delivery-Pipeline hinzu:**

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Gehen Sie von der Seite **Programmübersicht** zur Karte **Pipelines**, klicken Sie auf **Hinzufügen** und wählen Sie dann **Produktions-Pipeline hinzufügen** aus.

   ![Die Karte „Pipelines“ im Programm-Manager – Überblick](/help/implementing/cloud-manager/assets/configure-pipeline/add-prod-1.png)

1. Das Dialogfeld **Produktions-Pipeline hinzufügen** erscheint. Geben Sie einen **Pipeline-Name** an, um Ihre Pipeline zu identifizieren, sowie die folgenden Optionen. Klicken Sie auf **Weiter**.

   **Bereitstellungsauslöser**: Beim Definieren der Bereitstellungsauslöser für den Start der Pipeline haben Sie die folgenden Optionen.

   * **Manuell**: Mit dieser Option wird die Pipeline manuell gestartet.
   * **Bei Git-Änderungen**: Mit dieser Option wird die CI/CD-Pipeline gestartet, wenn zur konfigurierten Git-Verzweigung bestätigte Änderungen hinzugefügt werden. Mit dieser Option können Sie die Pipeline bei Bedarf immer noch manuell starten.

   **Verhalten bei bedeutenden Metrikfehlern**: Bei der Einrichtung oder Bearbeitung der Pipeline kann der **Bereitstellungs-Manager** festlegen, wie sich die Pipeline verhält, wenn bei einem der Quality Gates ein wichtiger Fehler auftritt. Folgende Optionen sind verfügbar:

   * **Jedes Mal fragen**: Dies ist die Standardeinstellung, die ein manuelles Eingreifen bei jedem bedeutenden Fehler verlangt.
   * **Sofortiger Ausfall**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler abgebrochen. Damit wird im Grunde eine Person simuliert, die manuell jeden Fehler ablehnt.
   * **Sofort fortfahren**: Wenn diese Option ausgewählt ist, wird die Pipeline bei einem bedeutenden Fehler automatisch fortgesetzt. Damit wird im Grunde eine Person simuliert, die manuell jeden Fehler quittiert.

   ![Konfiguration der Produktions-Pipeline](/help/implementing/cloud-manager/assets/configure-pipeline/production-pipeline-configuration.png)

1. Legen Sie auf der Registerkarte **Quell-Code** fest, welche Art von Code von der Pipeline verarbeitet werden soll.

   * **[Konfigurieren einer Full-Stack-Pipeline](#full-stack-code)**
   * **[Konfigurieren einer zielgerichteten Bereitstellungs-Pipeline](#targeted-deployment)**

Weitere Informationen zu diesem Pipeline-Typ finden Sie unter [CI/CD-Pipelines](/help/implementing/cloud-manager/configuring-pipelines/introduction-ci-cd-pipelines.md).

Die Schritte zum Abschluss der Erstellung Ihrer Produktions-Pipeline variieren je nach dem von Ihnen gewählten Typ von Quell-Code. Folgen Sie den oben stehenden Links, um zum nächsten Abschnitt dieses Dokuments zu springen und die Konfiguration Ihrer Pipeline abzuschließen.

