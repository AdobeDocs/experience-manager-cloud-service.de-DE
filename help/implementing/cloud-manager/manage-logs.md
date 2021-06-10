---
title: Verwalten von Protokollen – Cloud Service
description: Verwalten von Protokollen – Cloud Service
exl-id: f17274ce-acf5-4e7d-b875-75d4938806cd
source-git-commit: 8a70a343be8a6843436f1df26adae5b1935ad4c3
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 69%

---

# Zugreifen auf und Verwalten von Protokollen {#manage-logs}

Benutzer können über die Umgebungskarte auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen. Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

## Herunterladen von Protokollen {#download-logs}

Diese Dateien können über die Benutzeroberfläche heruntergeladen werden, entweder von der Karte **Umgebungen** auf der Seite **Übersicht**:

![](assets/download-logs1.png)

Oder über die Seite &quot;Umgebungsdetails&quot;:

![](assets/download-logs.png)

>[!NOTE]
>Unabhängig davon, wo es geöffnet wird, erscheint dasselbe Dialogfeld und ermöglicht das Herunterladen einer jeweiligen Protokolldatei.

![](assets/download-logs2.png)

## Herunterladen von Protokollen für den Vorschaudienst {#download-preview-service}

Gehen Sie wie folgt vor, um Protokolle für den Vorschaudienst herunterzuladen

1. Navigieren Sie zur Karte **Umgebungen** auf der Seite **Übersicht** von Cloud Manager.

1. Wählen Sie **Protokolle herunterladen** aus dem **...** Menü.

1. Wählen Sie aus dem Dropdown-Menü **Service** die Option **Vorschau** oder **Vorschau des Dispatchers** aus, gefolgt von einem Klick auf das Download-Symbol.

   >[!NOTE]
   >Diese Aktion kann auch über die Seite &quot;Umgebungsdetails&quot;durchgeführt werden.

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
