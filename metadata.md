---
product: adobe experience manager
description: Dokumentation zu Adobe Experience Manager as a Cloud Service.
git-repo: https://github.com/AdobeDocs/experience-manager-cloud-service.en
index: true
type: Documentation
solution: Experience Manager, Experience Manager as a Cloud Service
feature-set: Experience Manager Assets, Experience Manager Sites, Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager, Experience Manager Screens
product_v2: id: fd1f54a9-f50c-467d-8956-cebbaf4f3eb8
usetq: true
landing-page-name: experience-manager
landing-page-breadcrumb-title: AEM
version: Experience Manager as a Cloud Service
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: 41d72ba991b6aa5a4b2c2f6d16f37d2f5c498889
workflow-type: tm+mt
source-wordcount: 95
ht-degree: 2%

---


# Metadaten für die interne Verwendung

Metadaten im GitHub-Authoring-System sind hierarchisch und werden in den folgenden zunehmenden Präzedenzfällen definiert.

1. metadata.md
1. toC
1. Artikel

Metadaten, die in der Datei „metadata.md“ definiert sind, gelten für das gesamte Repository, können jedoch auf der Inhaltsverzeichnis- und Artikelebene überschrieben werden. Jede Überschreibung der Metadaten sollte auf der niedrigstmöglichen Ebene erfolgen.

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

toCS

* `sub-product`
* `user-guide-title`

Artikel

* `title`
* `description`
* `contentOwner` (nur auf Asset-Kerninhalte unter `/help/assets`)
