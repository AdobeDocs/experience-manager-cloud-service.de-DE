---
title: Anzeigen und Verwalten von Protokollen
description: Erfahren Sie, wie Sie auf Protokolle zugreifen und diese verwalten können, um Ihren Entwicklungsprozess in AEM as a Cloud Service zu unterstützen.
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
source-git-commit: 1994b90e3876f03efa571a9ce65b9fb8b3c90ec4
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 19%

---


# Anzeigen und Verwalten von Protokollen {#manage-logs}

Erfahren Sie, wie Sie auf Protokolle zugreifen und diese verwalten können, um Ihren Entwicklungsprozess in AEM as a Cloud Service zu unterstützen.

Sie können mithilfe der **Umgebungen** der Karte **Übersicht** Seite oder Umgebungsdetails .

## Herunterladen von Protokollen {#download-logs}

Gehen Sie wie folgt vor, um Protokolle herunterzuladen.

1. Melden Sie sich unter [my.cloudmanager.adobe.com](https://my.cloudmanager.adobe.com/) bei Cloud Manager an und wählen Sie die entsprechende Organisation und das entsprechende Programm aus.

1. Gehen Sie von der Seite **Überblick** zur Karte **Umgebungen**.

1. Auswählen **Protokolle herunterladen** aus dem Menü mit den Auslassungspunkten.

   ![Menüelement &quot;Protokolle herunterladen&quot;](assets/download-logs1.png)

1. Im **Protokolle herunterladen** wählen Sie das entsprechende **Diensleistung** aus dem Dropdown-Menü

   ![Dialogfeld &quot;Protokolle herunterladen&quot;](assets/download-preview.png)

1. Nachdem Sie Ihren Dienst ausgewählt haben, klicken Sie auf das Download-Symbol neben dem Protokoll, das Sie abrufen möchten.

Sie können Ihre Protokolle auch über **Umgebungen** Seite.

![Protokolle über den Bildschirm &quot;Umgebungen&quot;](assets/download-logs.png)

## Protokolle über API {#logs-through-api}

Protokolle können nicht nur über die Benutzeroberfläche heruntergeladen werden, sondern auch über die API und die Befehlszeilenschnittstelle.

Um die Protokolldateien für eine bestimmte Umgebung herunterzuladen, ähnelt der Befehl dem folgenden.

```shell
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

Außerdem können Sie Protokolle über die Befehlszeilenschnittstelle verfolgen.

```shell
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Um die Umgebungs-ID (in diesem Beispiel 1884) und die verfügbaren Dienst- oder Protokollnamenoptionen abzurufen, können Sie die folgenden Befehle verwenden.

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

Weitere Informationen zur Cloud Manager-API und zur Adobe I/O-CLI finden Sie in den folgenden zusätzlichen Ressourcen:

* [Dokumentation für Cloud Manager-API](https://developer.adobe.com/experience-cloud/cloud-manager/)
* [Adobe I/O-CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)
