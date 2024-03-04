---
product: adobe experience manager
description: Dokumentation zu Adobe Experience Manager as a Cloud Service.
git-repo: https://github.com/AdobeDocs/experience-manager-cloud-service.de-DE
index: y
type: Documentation
solution: Experience Manager, Experience Manager as a Cloud Service
feature-set: Experience Manager Assets,Experience Manager Sites,Experience Manager, Experience Manager Forms, Experience Manager Cloud Manager
cloud: Experience Cloud
recommendations: noDisplay
source-git-commit: 2b2469382fa8adfbf8a0625a90f92e27cdf53d63
workflow-type: tm+mt
source-wordcount: '86'
ht-degree: 51%

---


# Metadaten für die interne Verwendung

Metadaten im GitHub-Authoring-System sind hierarchisch aufgebaut und werden in den folgenden zunehmenden Präzedenzebenen definiert.

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
* `contentOwner` (nur für den Kern-Asset-Inhalt unter `/help/assets`)
