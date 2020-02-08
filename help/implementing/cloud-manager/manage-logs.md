---
title: Protokolle verwalten - Cloud-Dienst
description: Protokolle verwalten - Cloud-Dienst
translation-type: tm+mt
source-git-commit: 81f993325b80c0de17d6032a45ebd61c22169d39

---


# Zugriff und Verwaltung von Protokollen {#manage-logs}

Benutzer können über die Umgebungskarte auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.  Benutzer können auf eine Liste der verfügbaren Protokolldateien für die ausgewählte Umgebung zugreifen.

Diese Dateien können über die Benutzeroberfläche heruntergeladen werden, entweder von der Seite **Übersicht** .

![](assets/manage-logs1.png)

Oder die Seite **Umgebungen** :

![](assets/manage-logs2.png)

>[!Note]
>Unabhängig davon, wo es geöffnet wird, wird dasselbe Dialogfeld angezeigt, in dem eine einzelne Protokolldatei heruntergeladen werden kann.

![](assets/manage-logs3.png)


## Protokolle über API {#logs-thorugh-api}

Zusätzlich zum Herunterladen von Protokollen über die Benutzeroberfläche stehen Protokolle über die API und die Befehlszeilenschnittstelle zur Verfügung.

Wenn Sie beispielsweise die Protokolldateien für eine bestimmte Umgebung herunterladen möchten, wäre der Befehl etwas Anderes, als

```java
$ aio cloudmanager:download-logs --programId 5 1884 author aemerror
```

Mit dem folgenden Befehl können Protokolle gezählt werden:

```java
$ aio cloudmanager:tail-log --programId 5 1884 author aemerror
```

Um die Umgebungs-ID (in diesem Fall 1884) und die verfügbaren Dienst- oder Protokollnamenoptionen abzurufen, können Sie Folgendes verwenden:

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

>[!Note]
>Während **Protokolldownloads** sowohl über die Benutzeroberfläche als auch über die API verfügbar sein werden, ist **Log Tailing** nur für API/CLI verfügbar.
