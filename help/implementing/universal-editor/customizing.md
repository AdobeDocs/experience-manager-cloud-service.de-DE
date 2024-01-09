---
title: Anpassen der Benutzeroberfläche
description: Erfahren Sie mehr über die verschiedenen Erweiterungspunkte, mit denen Sie die Benutzeroberfläche des universellen Editors anpassen können, um die Anforderungen Ihrer Inhaltsautoren zu unterstützen.
source-git-commit: 65893c0c0dee37bed8ecfbb06a12e7c093c4397c
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
