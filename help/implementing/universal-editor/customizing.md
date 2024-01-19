---
title: Anpassen der Benutzeroberfläche
description: Erfahren Sie mehr über die verschiedenen Erweiterungspunkte, mit denen Sie die Benutzeroberfläche des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.
exl-id: 8d6523c8-b266-4341-b301-316d5ec224d7
source-git-commit: 7ef3efa6e074778b7b3e3a8159056200b2663b30
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---


# Anpassen der Benutzeroberfläche {#customizing-ui}

Erfahren Sie mehr über die verschiedenen Erweiterungspunkte, mit denen Sie die Benutzeroberfläche des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.

## Publishing deaktivieren {#disable-publish}

Bestimmte Authoring-Workflows erfordern, dass Inhalte vor der Veröffentlichung überprüft werden. In solchen Fällen sollte die Option zur Veröffentlichung für Autoren nicht verfügbar sein.

Die **Veröffentlichen** -Schaltfläche kann daher in einer App vollständig unterdrückt werden, indem die folgenden Metadaten hinzugefügt werden.

```html
<meta name="urn:adobe:aue:config:disable" content="publish"/>
```
