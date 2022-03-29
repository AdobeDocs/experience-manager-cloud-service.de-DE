---
title: 'Fehlerbehebung bei der Cache-Performance  '
seo-title: Troubleshooting caching performance
description: 'Fehlerbehebung bei der Cache-Performance  '
seo-description: Troubleshooting caching performance
contentOwner: khsingh
exl-id: eae44a6f-25b4-46e9-b38b-5cec57b6772c
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '360'
ht-degree: 100%

---

# Caching-Leistung {#caching-performance}

Beim Konfigurieren oder Verwenden des Cache für adaptive Formulare in einer Cloud Service-Umgebung können Sie auf folgende Probleme stoßen:

## Einige adaptive Formulare, die Bilder oder Videos enthalten, werden nicht automatisch im Dispatcher-Cache ungültig {#images-videos-not-invalidated}

Sie können Bilder oder Videos aus dem Asset-Browser auswählen und zu einem adaptiven Formular hinzufügen. Wenn diese Bilder im Assets-Editor bearbeitet werden, wird die zwischengespeicherte Version eines adaptiven Formulars, das diese Bilder enthält, nicht ungültig. Das adaptive Formular zeigt weiterhin ältere Bilder an.

Um das Problem zu beseitigen, heben Sie nach dem Veröffentlichen der Bilder und Videos die Veröffentlichung des adaptiven Formulars, das auf diese Assets verweist, explizit auf und veröffentlichen Sie es erneut.

## Einige adaptive Formulare, die Inhaltsfragmente oder Experience Fragments enthalten, werden nicht automatisch im Dispatcher-Cache ungültig {#content-fragments-experience-fragments-not-invalidated}

Sie können einem adaptiven Formular ein Content- oder Erlebnisfragment hinzufügen. Wenn diese Fragmente unabhängig bearbeitet und veröffentlicht werden, wird die zwischengespeicherte Version eines adaptiven Formulars, das diese Fragmente enthält, nicht automatisch ungültig. Das adaptive Formular zeigt weiterhin ältere Fragmente an.

Um das Problem zu beseitigen, heben Sie nach dem Veröffentlichen der aktualisierten Content- oder Experience-Fragmente die Veröffentlichung des adaptiven Formulars, das diese Assets verwendet, explizit auf und veröffentlichen Sie es erneut.

## Es wird nur die erste Instanz von adaptiven Formularen zwischengespeichert {#only-first-instance-cached}

Wenn die URL des adaptiven Formulars keine Lokalisierungsinformationen enthält und die Option „Browser-Locale verwenden“ im Configuration Manager aktiviert ist, wird eine lokalisierte Version des adaptiven Formulars bereitgestellt und auf der Basis der ersten Anforderung (angefordertes Browser-Gebietsschema) eine Instanz des adaptiven Formulars zwischengespeichert und an jeden nachfolgenden Benutzer gesendet.

Führen Sie zur Behebung dieses Problems folgende Schritte durch:

1. Öffnen Sie Ihr Experience Manager-Projekt.
1. Öffnen Sie `dispatcher/scr/conf.d/rewrites/rewrite.rules` zur Bearbeitung.
1. Öffnen Sie `conf.d/httpd-dispatcher.conf` oder eine andere Konfigurationsdatei, die zur Laufzeit geladen wird.
1. Fügen Sie Ihrer Datei folgenden Code hinzu und speichern Sie die Änderung. Es handelt sich dabei um Beispiel-Code, den Sie an Ihre Umgebung anpassen können.

```shellscript
    # Handle actual URL convention (just pass through)
    RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]
    
    # Handle selector-based redirection based on browser language
    <VirtualHost *:80>
            # Handle actual URL convention (just pass through)
    RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]

    # Handle selector based redirection basded on browser language
    # The Rewrite Condition is looking for the Accept-Language header and if found takes the first two character which most likely will be the desired language selector.
    RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
    RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
    RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
```

## CDN-Caching stoppt nach 300 Sekunden {#cdn-caching-stops-working-after-300-seconds}

Das CDN-Caching funktioniert nach 300 Sekunden nicht mehr, und alle Anforderungen, die im CDN zwischengespeichert werden sollen, werden an Dispatcher weitergeleitet.

Um das Problem zu beheben, setzen Sie die Age-Kopfzeile auf 0:

1. Erstellen Sie eine Datei unter `src\conf.d\available_vhosts`.

1. Fügen Sie der Datei folgende Zeilen hinzu, um die Age-Kopfzeile zu definieren:

   ```shellscript
       <IfModule mod_headers.c>
               Header add X-Vhost "publish"
               Header set age 0
       </IfModule>
   ```

1. Speichern und schließen Sie die Datei.
1. Ändern Sie den weichen Link für `src\conf.d\enabled_vhosts\default.vhost` so, dass er auf eine neue Datei verweist.
