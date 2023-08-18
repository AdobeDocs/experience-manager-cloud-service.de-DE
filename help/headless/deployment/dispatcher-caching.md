---
title: Persistente GraphQL-Abfragen - Aktivierung der Zwischenspeicherung im Dispatcher
description: Der Dispatcher ist eine Caching- und Sicherheitsebene vor den Adobe Experience Manager-Veröffentlichungsumgebungen. Sie können die Zwischenspeicherung für persistente Abfragen in AEM Headless aktivieren.
feature: Dispatcher, GraphQL API
source-git-commit: 6f07089812e587834784aeda7e62d3e4614f45a1
workflow-type: tm+mt
source-wordcount: '301'
ht-degree: 5%

---


# Persistente GraphQL-Abfragen - Aktivierung der Zwischenspeicherung im Dispatcher {#graphql-persisted-queries-enabling-caching-dispatcher}

>[!CAUTION]
>
>Wenn die Zwischenspeicherung im Dispatcher aktiviert ist, wird die [CORS-Filter](/help/headless/deployment/cross-origin-resource-sharing.md) ist nicht erforderlich, sodass dieser Abschnitt ignoriert werden kann.

Die Zwischenspeicherung persistenter Abfragen ist im Dispatcher standardmäßig nicht aktiviert. Die Standardumaktivierung ist nicht möglich, da Kunden, die CORS (Cross-Origin Resource Sharing) mit mehreren Ursprüngen verwenden, ihre Dispatcher-Konfiguration überprüfen und möglicherweise aktualisieren müssen.

>[!NOTE]
>
>Der Dispatcher speichert die `Vary` -Kopfzeile.
>
>Das Caching anderer CORS-bezogener Header kann im Dispatcher aktiviert werden, reicht jedoch möglicherweise nicht aus, wenn mehrere CORS-Quellen vorhanden sind.

## Zwischenspeichern persistenter Abfragen aktivieren {#enable-caching-persisted-queries}

Um das Zwischenspeichern persistenter Abfragen zu aktivieren, definieren Sie die Dispatcher-Variable `CACHE_GRAPHQL_PERSISTED_QUERIES`:

1. Variable zur Dispatcher-Datei hinzufügen `global.vars`:

   ```xml
   Define CACHE_GRAPHQL_PERSISTED_QUERIES
   ```

>[!NOTE]
>
>Übereinstimmung mit dem [Anforderungen des Dispatchers für Dokumente, die zwischengespeichert werden können](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/troubleshooting/dispatcher-faq.html#how-does-the-dispatcher-return-documents%3F), fügt der Dispatcher das Suffix hinzu. `.json` an alle gespeicherten Abfrage-URLs, damit das Ergebnis zwischengespeichert werden kann.
>
>Dieses Suffix wird durch eine Neuschreibungsregel hinzugefügt, sobald die beibehaltene Abfrage-Zwischenspeicherung aktiviert ist.

## CORS-Konfiguration im Dispatcher {#cors-configuration-in-dispatcher}

Kunden, die CORS-Anforderungen verwenden, müssen möglicherweise ihre CORS-Konfiguration im Dispatcher überprüfen und aktualisieren.

* Die `Origin` -Kopfzeile darf nicht an AEM Veröffentlichungsinstanz über den Dispatcher übergeben werden:
   * Überprüfen Sie die `clientheaders.any` -Datei.
* Stattdessen müssen CORS-Anforderungen auf Dispatcher-Ebene auf zulässige Ursprünge hin bewertet werden. Dieser Ansatz stellt außerdem sicher, dass CORS-bezogene Kopfzeilen in allen Fällen korrekt an einem Ort festgelegt werden.
   * Eine solche Konfiguration sollte der `vhost` -Datei. Nachfolgend finden Sie eine Beispielkonfiguration. Zur Vereinfachung wurde nur der CORS-bezogene Teil bereitgestellt. Sie können sie für Ihre spezifischen Anwendungsfälle anpassen.

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
