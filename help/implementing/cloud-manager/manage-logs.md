---
title: Protokolle verwalten - Cloud-Dienst
description: Protokolle verwalten - Cloud-Dienst
translation-type: tm+mt
source-git-commit: 26833f59f21efa4de33969b7ae2e782fe5db8a14

---


# Zugriff auf und Verwalten von Protokollen {#manage-logs}

Die Benutzer können über die Umgebung Card auf eine Liste verfügbarer Protokolldateien für die ausgewählte Umgebung zugreifen.  Die Benutzer können auf eine Liste verfügbarer Protokolldateien für die ausgewählte Umgebung zugreifen.

Diese Dateien können über die Benutzeroberfläche heruntergeladen werden, entweder von der Seite &quot; **Übersicht** &quot;.

![](assets/manage-logs1.png)

Oder die Seite **Umgebung** :

![](assets/manage-logs2.png)

>[!NHinweis]
>Unabhängig davon, wo es geöffnet wird, wird dasselbe Dialogfeld angezeigt, in dem eine einzelne Protokolldatei heruntergeladen werden kann.

![](assets/manage-logs3.png)


## Protokolle über API {#logs-thorugh-api}

Zusätzlich zum Herunterladen von Protokollen über die Benutzeroberfläche stehen Protokolle über die API und die Befehlszeilenschnittstelle zur Verfügung.

Wenn Sie beispielsweise die Protokolldateien für eine bestimmte Umgebung herunterladen möchten, würde der Befehl nur die Zeilen

```java
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

Mit dem folgenden Befehl können Protokolle gezählt werden:

```java
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Um die Umgebung-ID (in diesem Fall 1884) und die verfügbaren Dienst- oder Protokollnamenoptionen abzurufen, können Sie Folgendes verwenden:

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

>[!NHinweis]
>Während **Protokolldownloads** sowohl über die Benutzeroberfläche als auch über die API verfügbar sind, ist **Log-Tailing** nur für API/CLI verfügbar.

### Zusätzliche Ressourcen {#resources}

Weitere Informationen zur Cloud Manager-API und zur Adobe I/O-CLI finden Sie in den folgenden zusätzlichen Ressourcen:

* [Dokumentation zur Cloud Manager-API](https://www.adobe.io/apis/experiencecloud/cloud-manager/docs.html)
* [Adobe I/O CLI](https://github.com/adobe/aio-cli-plugin-cloudmanager)