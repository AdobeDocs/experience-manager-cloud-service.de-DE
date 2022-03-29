---
title: Häufig gestellte Fragen zu Screens as a Cloud Service
description: Auf dieser Seite werden häufig gestellte Fragen zu Screens as a Cloud Service beschrieben.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: 02c9cbff56399ea2ca1baad7d2289d5d4c17c1c5
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 100%

---

# Häufig gestellte Fragen zu Screens as a Cloud Service {#screens-cloud-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen (FAQs) zum Screens as a Cloud Service-Projekt.

## Was sollte ich tun, wenn ein AEM Screens-Player, der auf Screens as a Cloud Service verweist, die benutzerdefinierten Client-Bibliotheken mit dem Format /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css nicht auswählt?

AEM as a Cloud Service ändert die langen Cache-Schlüssel bei jeder Bereitstellung. AEM Screens generiert die Offline-Caches, wenn der Inhalt geändert wird, und nicht, wenn Cloud Manager die Bereitstellung ausführt. Diese langen Cache-Schlüssel in den Manifesten sind ungültig, sodass der Player diese *Client-Bibliotheken* nicht herunterladen kann.

Durch die Verwendung von `longCacheKey="none"` in Ihrem `clientlib`-Ordner werden die langen Cache-Schlüssel für diese *Client-Bibliotheken* vollständig entfernt.


## Was sollten wir tun, wenn das Offline-Manifest nicht alle gewünschten Ressourcen enthält? {#offline-manifest}

Offline-Caches werden mithilfe des Servives **bulk-offline-update-screens-service** erzeugt. Bestimmte Pfade, auf die von `bulk-offline-update-screens-service` nicht zugegriffen werden kann, führen zu fehlenden Inhalten in Offline-Manifesten.

Erstellen Sie in Ihrem Code, d. h. in `ui.config or ui.apps`, eine OSGi-Konfiguration im Konfigurationsordner mit folgendem Inhalt, und geben Sie der Datei den Namen `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`.

```
scripts=[
        "
        set principal ACL for bulk-offline-update-screens-service
                allow jcr:read on /content/mysite
                allow jcr:read on /apps/my-resources
        end
        "] 
```

## Welche Bildformate werden für das nahtlose Rendern von Bildern in einem Kanal von AEM Screens as a Cloud Service empfohlen? {#screens-cloud-image-format}

Es wird empfohlen, in einem AEM Screens as a Cloud Service-Kanal Bilder im Format `.png` und `.jpeg` zu verwenden, um ein optimales Digital Signage-Erlebnis zu erzielen.
Bilder im Format `*.tif` (Tag-Image-Dateiformat) werden in AEM Screens as a Cloud Service nicht unterstützt. Wenn ein Kanal dieses Bildformat hat, wird das Bild auf der Player-Seite nicht gerendert.

## Was sollte ich tun, wenn ein Kanal im Entwicklermodus (online) nicht auf dem AEM Screens-Player gerendert wird? {#screens-cloud-online-channel-blank-iframe}

Es wird empfohlen, die Caching-Funktionen von AEM Screens zu nutzen. Wenn Sie jedoch Ihren Kanal im Entwicklermodus ausführen müssen und der AEM Screens-Player einen leeren Bildschirm anzeigt, überprüfen Sie die Entwickler-Tools Ihres Players und suchen Sie nach `X-Frame-Options`- oder `frame-ancestors`-Fehlern. Die Lösung besteht darin, den Dispatcher so zu konfigurieren, dass Inhalte in iFrames ausgeführt werden können. Normalerweise funktioniert die folgende Konfiguration:

```
Header set Content-Security-Policy "frame-ancestors ‘self’ file: localhost:*;"
```

## Was bedeutet die Verwendung der Registrierungs-Code-Grenze?

Als Best Practice können Sie die Verwendung des Registrierungs-Codes einschränken. Wenn ein Registrierungs-Code kompromittiert ist, aber eine Grenze von 100 Registrierungen hat, kann sich der Angreifer nur bis zu dieser Zahl registrieren, aber nicht häufiger. Sie können die Nutzungsbeschränkung jederzeit aktualisieren, nachdem der Registrierungs-Code erstellt und einige der Player des Kunden bereits registriert wurden. Wenn der Kunde eine ungewöhnliche Registrierungsaktivität für einen bestimmten Registrierungs-Code beobachtet, kann er den Grenzwert in Echtzeit senken, während er dies untersucht. Die Zahl kann wieder erhöht werden, wenn es sich um einen falschen Alarm handelt, ohne dass sich dies auf die bereits registrierten Player auswirkt.
