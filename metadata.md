---
product: adobe experience manager
description: Dokumentation zu Adobe Experience Manager as a Cloud Service.
git-repo: https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.de-DE
index: y
type: Documentation
solution: Experience Manager, Experience Manager as a Cloud Service
version: Cloud Service
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
source-git-commit: c19c15c4e71c8ead1c3cb05add052a8ffae79d0a
workflow-type: tm+mt
source-wordcount: '90'
ht-degree: 68%

---


# Metadaten für die interne Verwendung

Die Metadaten im GitHub-Authoring-System sind hierarchisch aufgebaut und werden in den folgenden aufsteigend sortierten Präzedenzebenen definiert.

1. metadata.md
1. IHV
1. Artikel

Die in der Datei „metadata.md“ definierten Metadaten gelten für den gesamten Bericht, können jedoch auf der IHV- (ToC) und der Artikelebene überschrieben werden. Das Überschreiben der Metadaten sollte auf der niedrigstmöglichen Ebene erfolgen.

Die Metadaten im Repository experience-manager-cloud-service.en sind das erforderliche Minimum.

metadata.md

* `product`
* `git-repo`
* `index`
* `solution-title`
* `solution-hub-url`
* `getting-started-title`
* `getting-started-url`
* `tutorials-title`
* `tutorials-url`

IHVs

* `sub-product`
* `user-guide-title`

Artikel

* `title`
* `description`
* `contentOwner` (nur auf Asset-Kerninhalt unter  `/help/assets`)
