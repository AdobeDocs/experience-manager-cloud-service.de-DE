---
title: Dispatcher-Konfigurationen in Screens as a Cloud Service
description: Auf dieser Seite werden Dispatcher-Konfigurationen in Screens als Cloud Service beschrieben.
source-git-commit: b00fd1e3826a7d0b0a4bf80b002fffda8f3983d0
workflow-type: tm+mt
source-wordcount: '140'
ht-degree: 1%

---


# Dispatcher-Konfigurationen in Screens as a Cloud Service {#dispatcher-configurations-screens-cloud}

In diesem Abschnitt werden die Dispatcher-Konfigurationen für Screens als Cloud Service beschrieben.

## Hinzufügen von Filtern und Cache-Regeln in Dispatcher für Screens as a Cloud Service-Bereitstellung {#deployment}

Lassen Sie die folgenden Filter und Cache-Regeln in Dispatchern für die Veröffentlichungsinstanzen in Screens as a Cloud Service zu.

### AEM Screens Filters {#filters}

```
## # Content Configurations
/0200 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
#/0201 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you're using experience-fragments
## add any other formats required for your project here
/0202 { /type "allow" /extension '(css|eot|gif|ico|jpeg|jpg|js|gif|pdf|png|svg|swf|ttf|woff|woff2|html|mp4|mov|m4v)' /path "/content/dam/*" }
/0203 { /type "allow" /method 'GET' /url "/screens/channels.json" }
## # Enable clientlibs proxy servlet
/0210 { /type "allow" /method "GET" /url "/etc.clientlibs/*" }
```

### Cache-Regeln {#cache-rules}

* Fügen Sie `/statfileslevel "10"` zum Abschnitt `/cache` in `publish_farm.any`/ hinzu.

   >[!NOTE]
   >Diese Cache-Regel unterstützt die Zwischenspeicherung von bis zu 10 Ebenen vom Cache-Basisverzeichnis und macht die Veröffentlichung von Inhalten ungültig, anstatt alles zu invalidieren. Sie können diese Ebene ändern, je nachdem, wie tief Ihre Inhaltsstruktur eingerichtet ist.

* Fügen Sie Folgendes zum Abschnitt `/invalidate` in `publish_farm.any` hinzu.

   ```
   /0003 {
       /glob "*.json"
       /type "allow"
   }
   ```

* Fügen Sie die folgenden Regeln zum Abschnitt `/rules` in `/cache` in publish_farm.any oder in einer Datei hinzu, die aus `publish_farm.any` enthalten ist.

   ```
   ## Allow Dispatcher Cache for Screens channels
    /0002
        {
        /glob "/content/screens/*.html"
        /type "allow"
        }
   
   ## Allow Dispatcher Cache for Screens offline manifests
   
   /0003
       {
       /glob "/content/screens/*.manifest.json"
       /type "allow"
       }
   
   ## Allow Dispatcher Cache for Assets
   /0004
       {
       /glob "/content/dam/*"
       /type "allow"
       }
   
   ## Deny Screens Channels json
   /0005
       {
       /glob "/screens/channels.json"
       /type "deny"
       }
   ```
