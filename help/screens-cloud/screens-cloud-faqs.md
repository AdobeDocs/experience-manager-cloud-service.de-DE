---
title: Häufig gestellte Fragen zu Screens as a Cloud Service
description: Auf dieser Seite werden häufig gestellte Fragen zu Screens as a Cloud Service beschrieben.
source-git-commit: 7a26bb50a8b95a2358912249e21daeb9c5e9c1a3
workflow-type: tm+mt
source-wordcount: '191'
ht-degree: 0%

---


# Häufig gestellte Fragen zu Screens as a Cloud Service {#screens-cloud-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen zu Screens as a Cloud Service.

## Was sollte ich tun, wenn der AEM Screens-Player, der auf Screens als Cloud Service verweist, die benutzerdefinierten Client-Bibliotheken mit dem Format /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css nicht auswählt?

AEM als Cloud Service ändert die langen Cache-Schlüssel bei jeder Bereitstellung. AEM Screens generiert Offline-Caches, wenn der Inhalt geändert wird, und nicht, wenn Cloud Manager die Bereitstellung ausführt. Diese langen Cache-Schlüssel in den Manifesten sind ungültig, sodass der Player diese *clientlibs* nicht herunterladen kann.

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
