---
title: Dispatcher-Konfigurationen in Screens as a Cloud Service
description: Auf dieser Seite werden Dispatcher-Konfigurationen in Screens as a Cloud Service beschrieben.
exl-id: cc04b480-9310-4975-a7c2-20682c567fa4
feature: Administering Screens
role: Admin, Developer, User
source-git-commit: f9ba9fefc61876a60567a40000ed6303740032e1
workflow-type: ht
source-wordcount: '140'
ht-degree: 100%

---

# Dispatcher-Konfigurationen in Screens as a Cloud Service {#dispatcher-configurations-screens-cloud}

In diesem Abschnitt werden die Dispatcher-Konfigurationen für Screens as a Cloud Service beschrieben.

## Hinzufügen von Filtern und Cache-Regeln im Dispatcher für die Bereitstellung von Screens as a Cloud Service {#deployment}

Lassen Sie die folgenden Filter und Cache-Regeln in Dispatchern für die Veröffentlichungsinstanzen in Screens as a Cloud Service zu.

### AEM Screens-Filter {#filters}

```
## # Content Configurations
/0200 { /type "allow" /method '(GET|HEAD)' /url "/content/screens/*" }
#/0201 { /type "allow" /method '(GET|HEAD)' /url "/content/experience-fragments/*" } ## uncomment this, if you are using experience-fragments
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

* Fügen Sie dem Abschnitt `/invalidate` in `publish_farm.any` Folgendes hinzu.

  ```
  /0003 {
      /glob "*.json"
      /type "allow"
  }
  ```

* Fügen Sie die folgenden Regeln zum Abschnitt `/rules` in `/cache` in publish_farm.any oder in einer Datei hinzu, die in `publish_farm.any` enthalten ist:

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
