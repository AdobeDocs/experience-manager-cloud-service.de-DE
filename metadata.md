---
product: adobe experience manager
git-repo: https://github.com/AdobeDocs/experience-manager-cloud-service.en
index: y
solution-title: Adobe Experience Manager als Cloud-Dienst
solution-hub-url: https://docs.adobe.com/content/help/en/experience-manager-cloud-service/landing/home.html
getting-started-title: Erste Schritte
getting-started-url: https://docs.adobe.com/content/help/en/experience-manager-cloud-service/overview/home.html
tutorials-title: Tutorials
tutorials-url: https://docs.adobe.com/content/help/en/experience-manager-learn/cloud-service/overview.html
translation-type: tm+mt
source-git-commit: 99dce041a6d7554785fd43eb82c671643e903f23

---


# Metadaten für die interne Verwendung

Die Metadaten im GitHub-Authoring-System sind hierarchisch aufgebaut und werden in den folgenden, sich verstärkenden Ebenen definiert.

1. metadata.md
1. ToC
1. Artikel

Die in der Datei &quot;metadata.md&quot;definierten Metadaten gelten für den gesamten Bericht, können jedoch auf den Ebenen &quot;ToC&quot;und &quot;article&quot;überschrieben werden. Das Überschreiben der Metadaten sollte auf der niedrigstmöglichen Ebene erfolgen.

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

ToCs

* `sub-product`
* `user-guide-title`

Artikel

* `title`
* `description`
* `contentOwner` (nur auf Core Asset-Inhalt unter `/help/assets`)

Weitere Informationen zu den Metadaten finden Sie im [internen Authoring-Handbuch.](https://docs.adobe.com/help/en/collaborative-doc-instructions/collaboration-guide/markdown/metadata.html#solution-metadata)