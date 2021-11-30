---
title: as a Cloud Service FAQs zu Screens
description: Auf dieser Seite werden as a Cloud Service häufig gestellte Fragen zu Screens beschrieben.
exl-id: 93f2144c-0e64-4012-88c6-86972d8cad9f
source-git-commit: fb82970154fa37e3b3d1591a2e25989853ec6b90
workflow-type: tm+mt
source-wordcount: '459'
ht-degree: 0%

---

# as a Cloud Service FAQs zu Screens {#screens-cloud-faqs}

Im folgenden Abschnitt finden Sie Antworten auf häufig gestellte Fragen (FAQs) zum as a Cloud Service Screens-Projekt.

## Was sollte ich tun, wenn der AEM Screens-Player, der auf Screens as a Cloud Service verweist, die benutzerdefinierten Client-Bibliotheken mit dem Format /etc.clientlibs/xxx/clientlibs/clientlib-site.lc-813643788974b0f89d686d9591526d63-lc.min.css nicht auswählt?

AEM as a Cloud Service ändert die langen Cache-Schlüssel bei jeder Bereitstellung. AEM Screens generiert Offline-Caches, wenn der Inhalt geändert wird, und nicht, wenn Cloud Manager die Bereitstellung ausführt. Diese langen Cache-Schlüssel in den Manifesten sind ungültig, sodass der Player diese nicht herunterladen kann *clientlibs*.

Verwenden `longCacheKey="none"` in `clientlib` Ordner entfernt die langen Cache-Schlüssel für diese *clientlibs*.


## Was sollten wir tun, wenn das Offline-Manifest nicht alle Ressourcen wie gewünscht enthält? {#offline-manifest}

Offline-Caches werden mithilfe von **bulk-offline-update-screens-service** Dienstbenutzer. Bestimmte Pfade, auf die nicht zugegriffen werden kann `bulk-offline-update-screens-service`führen zu fehlenden Inhalten in Offline-Manifesten.

In Ihrem Code bedeutet dies: `ui.config or ui.apps`erstellen Sie eine OSGi-Konfiguration im Konfigurationsordner mit folgendem Inhalt und geben Sie den Dateinamen als `org.apache.sling.jcr.repoinit.RepositoryInitializer-serviceusersandacls-content.config`

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

Es wird empfohlen, Bilder im folgenden Format zu verwenden: `.png` und `.jpeg` in einem as a Cloud Service AEM Screens-Kanal für das beste Digital Signage-Erlebnis.
Die Bilder im Format `*.tif` (Tag-Image-Dateiformat) werden in AEM Screens as a Cloud Service nicht unterstützt. Wenn ein Kanal dieses Bildformat hat, wird das Bild auf der Player-Seite nicht gerendert.

## Was sollte ich tun, wenn ein Kanal im Entwicklermodus (online) nicht auf dem AEM Screens-Player gerendert wird?{#screens-cloud-online-channel-blank-iframe}

Es wird empfohlen, die Zwischenspeicherungsfunktionen von AEM Screens zu nutzen. Wenn Sie jedoch Ihren Kanal im Entwicklermodus ausführen müssen und der AEM Screens-Player einen leeren Bildschirm anzeigt, überprüfen Sie die Entwicklertools Ihres Players und suchen Sie nach `X-Frame-Options` oder `frame-ancestors` Fehler. Die Lösung besteht darin, den Dispatcher so zu konfigurieren, dass Inhalte in iFrames ausgeführt werden können. Normalerweise funktioniert die folgende Konfiguration:

```
Header set Content-Security-Policy "frame-ancestors ‘self’ file: localhost:*;"
```

## Was ist die Verwendung der Registrierungs-Code-Grenze?

Als Best Practice können Sie die Verwendung des Registrierungs-Codes einschränken. Wenn ein Registrierungs-Code kompromittiert ist, aber eine Grenze von 100 Registrierungen hat, kann sich der Angreifer nur bis zu dieser Zahl registrieren, aber nicht mehr. Sie können die Nutzungsbeschränkung jederzeit aktualisieren, nachdem der Registrierungs-Code erstellt und einige der Player des Kunden bereits registriert wurden. Wenn der Kunde eine ungewöhnliche Registrierungsaktivität für einen bestimmten Registrierungs-Code beobachtet, kann er den Grenzwert in Echtzeit senken, während er untersucht, und die Zahl kann erhöht werden, wenn es sich um einen falschen Alarm handelt, ohne dass sich dies auf die bereits registrierten Player auswirkt.