---
product: adobe experience manager
git-repo: https://git.corp.adobe.com/AdobeDocs/experience-manager-cloud-service.de-DE
index: y
solution-title: Adobe Experience Manager as a Cloud Service
solution-hub-url: https://docs.adobe.com/content/help/de-DE/experience-manager-cloud-service/landing/home.translate.html
getting-started-title: Erste Schritte
getting-started-url: https://docs.adobe.com/content/help/en/experience-manager-cloud-service/overview/home.html
tutorials-title: Tutorials
tutorials-url: https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html
translation-type: tm+mt
source-git-commit: 967d0993ba2114d0dd081724cf5e7754899b5c8e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

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
* `contentOwner` (nur auf Core Asset-Inhalt unter `/help/assets`)

Weitere Informationen zu den Metadaten finden Sie im [internen Authoring-Handbuch.](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/markdown/metadata.html#solution-metadata)
