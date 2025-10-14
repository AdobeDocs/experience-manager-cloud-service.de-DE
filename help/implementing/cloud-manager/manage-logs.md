---
title: Zugreifen auf und Verwalten von Protokollen
description: Erfahren Sie, wie Sie auf Protokolle zugreifen und diese verwalten können, um Ihren Entwicklungsprozess in AEM as a Cloud Service zu unterstützen.
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
solution: Experience Manager
feature: Log Files, Developing
role: Admin, Architect, Developer
source-git-commit: 498a58c89910f41e6b86c5429629ec9282028987
workflow-type: tm+mt
source-wordcount: '349'
ht-degree: 92%

---


# Zugreifen auf und Verwalten von Protokollen {#manage-logs}

Erfahren Sie, wie Sie auf Protokolle zugreifen und diese verwalten können, um Ihren Entwicklungsprozess in AEM as a Cloud Service zu unterstützen.

Sie können über die Karte **Umgebungen** auf der Seite **Überblick** oder der Seite „Umgebungsdetails“ auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Protokolle werden sieben Tage lang aufbewahrt.

## Herunterladen von Protokollen {#download-logs}

Gehen Sie wie folgt vor, um Protokolle herunterzuladen:

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation aus.

1. Wählen Sie in der Konsole **[Meine Programme](/help/implementing/cloud-manager/navigation.md#my-programs)** das Programm aus.

1. Navigieren Sie von der Seite **Überblick** zur Karte **Umgebungen**.

1. Wählen Sie **Protokolle herunterladen** aus dem Menü mit den Auslassungspunkten.

   ![Menüelement „Protokolle herunterladen“](assets/download-logs1.png)

1. Wählen Sie im Dialog **Protokolle herunterladen** den entsprechenden **Service** aus dem Dropdown-Menü aus

   ![Dialog „Protokolle herunterladen“](assets/download-preview.png)

   Falls [Zusätzliche Veröffentlichungsregionen](/help/operations/additional-publish-regions.md) für Ihre Umgebung aktiviert sind, können Sie jede Region auswählen und ihre Protokolle separat herunterladen, wie unten dargestellt:

   ![Herunterladen von Protokollen für zusätzliche Veröffentlichungsregionen](assets/download-publish-region-logs.png)

1. Nachdem Sie Ihren Service ausgewählt haben, klicken Sie auf das Download-Symbol neben dem Protokoll, das Sie abrufen möchten.

Sie können Ihre Protokolle auch über die Seite **Umgebungen** aufrufen.

![Protokolle aus dem Bildschirm „Umgebungen“](assets/download-logs.png)

## Protokolle über API {#logs-through-api}

Abgesehen vom Herunterladen von Protokollen über die Benutzeroberfläche sind die Protokolle auch über die API und die Befehlszeilenschnittstelle verfügbar.

Um die Protokolldateien für eine bestimmte Umgebung herunterzuladen, ähnelt der Befehl dem folgenden.

```shell
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

Außerdem können Sie Protokolle über die Befehlszeilenschnittstelle verfolgen.

```shell
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Um die Umgebungs-ID (in diesem Fall „1884“) und die verfügbaren Service- oder Protokollnamenoptionen abzurufen, können Sie die folgenden Befehle verwenden.

```shell
$ aio cloudmanager:list-environments
Environment Id Name                     Type  Description                          
1884           FoundationInternal_dev   dev   Foundation Internal Dev environment  
1884           FoundationInternal_stage stage Foundation Internal STAGE environment
1884           FoundationInternal_prod  prod  Foundation Internal Prod environment
 
 
$ aio cloudmanager:list-available-log-options 1884
Environment Id Service    Name         
1884           author     aemerror     
1884           author     aemrequest   
1884           author     aemaccess    
1884           publish    aemerror     
1884           publish    aemrequest   
1884           publish    aemaccess    
1884           dispatcher httpderror   
1884           dispatcher aemdispatcher
1884           dispatcher httpdaccess
```

### Zusätzliche Ressourcen {#resources}

>[!TIP]
>
>Sehen Sie sich [dieses Video](https://app.frame.io/reviews/28cdf463-b7fc-443b-a54a-93cb7da6567e/dbf158f1-568b-4efc-8fbc-3b241561cbab) an, um mehr über das Debugging von AEM as a Cloud Service zu erfahren.

Weitere Informationen zur Cloud Manager-API und zur Adobe I/O-CLI finden Sie in den folgenden zusätzlichen Ressourcen:

* [Dokumentation für Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/)
* [Adobe I/O-CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)

Weitere Informationen zu Protokolldateien in AEM as a Cloud Service finden Sie in den folgenden zusätzlichen Ressourcen:

* [Cloud 5-AEM-Protokolldateien](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/expert-resources/cloud-5/cloud5-aem-log-files#)
* [Debugging von AEM as a Cloud Service mithilfe von Protokollen](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-as-a-cloud-service/logs#)
