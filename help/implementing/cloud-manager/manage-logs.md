---
title: Verwalten von Protokollen – Cloud Service
description: Verwalten von Protokollen – Cloud Service
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
source-git-commit: d44a4239205b88f05ab5ae9ef3263e6549f998fc
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 68%

---

# Zugreifen auf und Verwalten von Protokollen {#manage-logs}

Benutzer können über die Karte **Umgebungen** auf der Seite **Übersicht** oder Umgebungsdetails auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

## Herunterladen von Protokollen {#download-logs}

Gehen Sie wie folgt vor, um Protokolle herunterzuladen.

1. Navigieren Sie von der Seite **Übersicht** zur Karte **Umgebungen** .

1. Wählen Sie **Protokolle herunterladen** aus dem **...** Menü.

   ![](assets/download-logs1.png)

   *Oder*

   Auf der Seite &quot;Umgebungsdetails&quot;:

   ![](assets/download-logs.png)

   >[!NOTE]
   >Unabhängig davon, wo es geöffnet wird, erscheint dasselbe Dialogfeld und ermöglicht das Herunterladen einer jeweiligen Protokolldatei.

1. Wählen Sie aus dem Dropdown-Menü **Service** Optionen wie **Vorschau** oder **Vorschau des Dispatchers** aus, gefolgt von einem Klick auf das Download-Symbol.

   ![](assets/download-preview.png)


## Protokolle über API {#logs-through-api}

Abgesehen vom Herunterladen von Protokollen über die Benutzeroberfläche sind die Protokolle auch über die API und die Befehlszeilenschnittstelle verfügbar.

Für das Herunterladen der Protokolldateien für eine bestimmte Umgebung würde der Befehl ungefähr folgendermaßen aussehen:

```java
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

Der folgende Befehl ermöglicht das Tailing von Protokollen:

```java
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Um die Umgebungs-ID (in diesem Fall „1884“) und die verfügbaren Service- oder Protokollnamenoptionen abzurufen, können Sie den folgenden Befehl verwenden:

```java
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

>[!NOTE]
>Während **Protokoll-Downloads** sowohl über die Benutzeroberfläche als auch über die API möglich sind, ist das **Protokoll-Tailing** nur über APIs/die Befehlszeilenschnittstelle möglich.

### Zusätzliche Ressourcen {#resources}

Weitere Informationen zur Cloud Manager-API und zur Adobe I/O-CLI finden Sie in den folgenden zusätzlichen Ressourcen:

* [Dokumentation für Cloud Manager-API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)
* [Adobe I/O-CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)
