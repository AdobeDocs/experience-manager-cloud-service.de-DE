---
title: as a Cloud Service FAQs zu Screens
description: Auf dieser Seite werden as a Cloud Service häufig gestellte Fragen zu Screens beschrieben.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: cf091056bdb96917a6d22bf1197d9b34ebbf9610
workflow-type: tm+mt
source-wordcount: '275'
ht-degree: 0%

---

# as a Cloud Service FAQs zu Screens {#screens-cloud-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen (FAQs) zum as a Cloud Service Screens-Projekt.

## Was sollte ich tun, wenn der AEM Screens-Player, der auf Screens as a Cloud Service verweist, die benutzerdefinierten Client-Bibliotheken mit dem Format /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css nicht auswählt?

AEM as a Cloud Service ändert die langen Cache-Schlüssel bei jeder Bereitstellung. AEM Screens generiert Offline-Caches, wenn der Inhalt geändert wird, und nicht, wenn Cloud Manager die Bereitstellung ausführt. Diese langen Cache-Schlüssel in den Manifesten sind ungültig, sodass der Player diese *clientlibs* nicht herunterladen kann.

Durch Verwendung von `longCacheKey="none"` im Ordner `clientlib` werden die langen Cache-Schlüssel für diese *clientlibs* vollständig entfernt.


## Was sollten wir tun, wenn das Offline-Manifest nicht alle Ressourcen wie gewünscht enthält? {#offline-manifest}

Offline-Caches werden mithilfe des Dienstbenutzers **bulk-offline-update-screens-service** generiert. Bestimmte Pfade, auf die nicht über `bulk-offline-update-screens-service` zugegriffen werden kann, führen zu fehlenden Inhalten in Offline-Manifesten.

Erstellen Sie in Ihrem Code, d. h. `ui.config or ui.apps`, eine OSGi-Konfiguration im Konfigurationsordner mit folgendem Inhalt und geben Sie den Dateinamen als `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config` an

```
scripts=[
        "
        set principal ACL for bulk-offline-update-screens-service
                allow jcr:read on /content/mysite
                allow jcr:read on /apps/my-resources
        end
        "] 
```

## Welche Bildformate werden für die nahtlose Wiedergabe von Bildern in as a Cloud Service Kanälen von AEM Screens empfohlen?{#screens-cloud-image-format}

Es wird empfohlen, Bilder im Format `.png` und `.jpeg` in einem as a Cloud Service AEM Screens-Kanal zu verwenden, um eine optimale digitale Beschilderung zu erzielen.
Bilder im Format `*.tif` (Tag-Bilddateiformat) werden in AEM Screens as a Cloud Service nicht unterstützt. Wenn ein Kanal dieses Bildformat hat, wird das Bild auf der Player-Seite nicht gerendert.