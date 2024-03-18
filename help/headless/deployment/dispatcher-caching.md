---
title: Persistierte GraphQL-Abfragen – Aktivieren der Caching-Funktion im Dispatcher
description: Der Dispatcher ist eine Caching- und Sicherheitsebene vor den Adobe Experience Manager-Veröffentlichungsumgebungen. Sie können das Caching für persistierte Abfragen in AEM Headless aktivieren.
feature: Dispatcher, GraphQL API
exl-id: 30a97e56-6699-41c4-a4eb-fc6236667f8f
source-git-commit: 859ea382cce6822da1da7d11213c3f44a25edef3
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 89%

---

# Persistierte GraphQL-Abfragen – Aktivieren der Caching-Funktion im Dispatcher {#graphql-persisted-queries-enabling-caching-dispatcher}

>[!CAUTION]
>
>Wenn die Caching-Funktion im Dispatcher aktiviert ist, wird der [CORS-Filter](/help/headless/deployment/cross-origin-resource-sharing.md) nicht benötigt, sodass dieser Abschnitt ignoriert werden kann.

Das Caching persistierter Abfragen ist im Dispatcher standardmäßig nicht aktiviert. Eine Standardaktivierung ist nicht möglich, da Kundinnen und Kunden, die CORS (Cross-Origin Resource Sharing) mit mehreren Ursprüngen verwenden, ihre Dispatcher-Konfiguration überprüfen und möglicherweise aktualisieren müssen.

>[!NOTE]
>
>Der Dispatcher speichert den `Vary`-Header nicht zwischen.
>
>Das Caching anderer CORS-bezogener Header kann im Dispatcher aktiviert werden, reicht jedoch möglicherweise nicht aus, wenn mehrere CORS-Quellen vorhanden sind.

>[!NOTE]
>
>Eine ausführliche Dokumentation zum Dispatcher finden Sie im [Handbuch zum Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=de).

## Aktivieren des Cachings persistierter Abfragen {#enable-caching-persisted-queries}

Um das Caching persistierter Abfragen zu aktivieren, definieren Sie die Dispatcher-Variable `CACHE_GRAPHQL_PERSISTED_QUERIES`:

1. Fügen Sie die Variable zur Dispatcher-Datei `global.vars` hinzu:

   ```xml
   Define CACHE_GRAPHQL_PERSISTED_QUERIES
   ```

>[!NOTE]
>
>Individuelle Ergebnisse `ETag` Header-Berechnung für die zwischengespeicherten persistenten Abfragen (für *each* -Antwort, die eindeutig ist) die `FileETag Digest` muss in der Konfiguration des virtuellen Hosts für die Dispatcher-Konfiguration verwendet werden (falls noch nicht vorhanden):
>
>```xml
><Directory />    
>   ...    
>   FileETag Digest
></Directory> 
>```

>[!NOTE]
>
>Um den [Anforderungen des Dispatchers für zwischenspeicherbare Dokumente](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/troubleshooting/dispatcher-faq.html?lang=de#how-does-the-dispatcher-return-documents%3F) zu entsprechen, fügt der Dispatcher allen persistierten Abfrage-URLs das Suffix `.json` hinzu, damit das Ergebnis zwischengespeichert werden kann.
>
>Dieses Suffix wird durch eine Neuschreibungsregel hinzugefügt, sobald die Caching-Funktion für persistierte Abfragen aktiviert ist.

## CORS-Konfiguration im Dispatcher {#cors-configuration-in-dispatcher}

Kundinnen und Kunden, die CORS-Anfragen verwenden, müssen möglicherweise ihre CORS-Konfiguration im Dispatcher überprüfen und aktualisieren.

* Die `Origin`-Kopfzeile darf nicht über den Dispatcher an AEM Publish weitergeben werden:
   * Überprüfen Sie die `clientheaders.any`-Datei.
* Stattdessen müssen CORS-Anfragen auf Dispatcher-Ebene im Hinblick auf zulässige Ursprünge ausgewertet werden. Dieser Ansatz stellt außerdem sicher, dass CORS-bezogene Kopfzeilen in allen Fällen korrekt an einem Ort festgelegt werden.
   * Eine solche Konfiguration sollte der `vhost`-Datei hinzugefügt werden. Nachfolgend finden Sie eine Beispielkonfiguration. Zur Vereinfachung ist nur der CORS-bezogene Teil angegeben. Sie können sie an Ihre spezifischen Anwendungsfälle anpassen.

  ```xml
  <VirtualHost *:80>
     ServerName "publish"
  
     # ...
  
     <IfModule mod_headers.c>
         Header add X-Vhost "publish"
  
          ################## Start of the CORS specific configuration ##################
  
          SetEnvIfExpr "req_novary('Origin') == ''"  CORSType=none CORSProcessing=false
          SetEnvIfExpr "req_novary('Origin') != ''"  CORSType=cors CORSProcessing=true CORSTrusted=false
  
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') == '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=invalidpreflight CORSProcessing=false
          SetEnvIfExpr "req_novary('Access-Control-Request-Method') != '' && %{REQUEST_METHOD} == 'OPTIONS' && req_novary('Origin') != ''  " CORSType=preflight CORSProcessing=true CORSTrusted=false
          SetEnvIfExpr "req_novary('Origin') -strcmatch 'https://%{HTTP_HOST}*'"  CORSType=samedomain CORSProcessing=false
  
          # For requests that require CORS processing, check if the Origin can be trusted
          SetEnvIfExpr "%{HTTP_HOST} =~ /(.*)/ " ParsedHost=$1
  
          ################## Adapt the regex to match CORS origin for your environment
          SetEnvIfExpr "env('CORSProcessing') == 'true' && req_novary('Origin') =~ m#(https://.*.your-domain.tld(:\d+)?$)#" CORSTrusted=true
  
          # Extract the Origin header 
          SetEnvIfNoCase ^Origin$ ^https://(.*)$ CORSTrustedOrigin=https://$1
  
          # Flush If already set
          Header unset Access-Control-Allow-Origin
          Header unset Access-Control-Allow-Credentials
  
          # Trusted
          Header always set Access-Control-Allow-Credentials "true" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Origin "%{CORSTrustedOrigin}e" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Methods "GET" "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Max-Age 1800 "expr=reqenv('CORSTrusted') == 'true'"
          Header always set Access-Control-Allow-Headers "Origin, Accept, X-Requested-With, Content-Type, Access-Control-Request-Method, Access-Control-Request-Headers" "expr=reqenv('CORSTrusted') == 'true'"
  
          # Non-CORS or Not Trusted
          Header unset Access-Control-Allow-Credentials "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Origin "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Allow-Methods "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
          Header unset Access-Control-Max-Age "expr=reqenv('CORSProcessing') == 'false' || reqenv('CORSTrusted') == 'false'"
  
          # Always vary on origin, even if its not there.
          Header merge Vary Origin
  
          # CORS - send 204 for CORS requests which are not trusted
          RewriteCond expr "reqenv('CORSProcessing') == 'true' && reqenv('CORSTrusted') == 'false'"
          RewriteRule "^(.*)" - [R=204,L]
  
          ################## End of the CORS specific configuration ##################
  
     </IfModule>
  
     <Directory />
  
         # ...
  
     </Directory>
  
     # ...
  
  </VirtualHost>
  ```
