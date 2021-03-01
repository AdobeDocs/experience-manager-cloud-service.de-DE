---
product: adobe experience manager
description: dies sind die für die AEMaaCS-Dokumentationsseiten erforderlichen Metadaten
git-repo: https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.de-DE
index: y
type: Dokumentation
solution-title: Adobe Experience Manager as a Cloud Service
solution-hub-url: https://experienceleague.adobe.com/docs/experience-manager-cloud-service/landing/home.html?lang=de
getting-started-title: Erste Schritte
getting-started-url: https://experienceleague.adobe.com/docs/experience-manager-cloud-service/overview/home.html
tutorials-title: Tutorials
tutorials-url: https://experienceleague.adobe.com/docs/experience-manager-learn/cloud-service/overview.html?lang=de
translation-type: tm+mt
source-git-commit: 28de20620a7cc8a3df231abacde4b3daa98cbcdb
workflow-type: tm+mt
source-wordcount: '120'
ht-degree: 70%

---


# Metadaten für die interne Verwendung

Die Metadaten im GitHub-Authoring-System sind hierarchisch aufgebaut und werden in den folgenden aufsteigend sortierten Präzedenzebenen definiert.

1. metadata.md
1. IHV
1. Artikel

Die in der Datei „metadata.md“ definierten Metadaten gelten für den gesamten Bericht, können jedoch auf der IHV- (ToC) und der Artikelebene überschrieben werden. Das Überschreiben der Metadaten sollte auf der niedrigstmöglichen Ebene erfolgen.

Die Metadaten im Bericht &quot;experience-manager-cloud-service.de&quot;sind das erforderliche Minimum.

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
* `contentOwner` (nur auf Core Asset-Inhalt unter  `/help/assets`)
