---
product: adobe experience manager
description: Dokumentation zu Adobe Experience Manager as a Cloud Service.
git-repo: https://github.com/AdobeDocs/experience-manager-cloud-service.de-DE
index: true
type: Documentation
solution: Experience Manager, Experience Manager as a Cloud Service
feature-set: Experience Manager Assets, Experience Manager Sites, Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager, Experience Manager Screens
landing-page-name: experience-manager
landing-page-breadcrumb-title: AEM
version: Experience Manager as a Cloud Service
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: 81f85045212ca6fd92f2b665aeceaa0d4b92318c
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 51%

---


# Metadaten für die interne Verwendung

Metadaten im GitHub-Authoring-System sind hierarchisch und werden in den folgenden zunehmenden Präzedenzfällen definiert.

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
* `contentOwner` (nur auf Asset-Kerninhalte unter `/help/assets`)
