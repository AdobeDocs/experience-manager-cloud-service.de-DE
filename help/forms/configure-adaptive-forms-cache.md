---
title: Konfigurieren des Cache für adaptive Formulare
seo-title: Configure Adaptive Forms cache
description: Der Cache für adaptive Formulare wurde speziell für adaptive Formulare und Dokumente konzipiert. Adaptive Formulare und adaptive Dokumente werden zwischengespeichert, um die Zeit zu minimieren, die zum Rendern eines adaptiven Formulars oder Dokuments auf dem Client notwendig ist.
seo-description: The Adaptive Forms cache is designed specifically for Adaptive Forms and documents. It caches Adaptive Forms and adaptive documents with the objective of reducing the time required to render an Adaptive Form or document on the client.
uuid: ba8f79fd-d8dc-4863-bc0d-7c642c45505c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 9fa6f761-58ca-4cd0-8992-b9337dc1a279
docset: aem65
source-git-commit: 7163eb2551f5e644f6d42287a523a7dfc626c1c4
workflow-type: tm+mt
source-wordcount: '979'
ht-degree: 98%

---


# Konfigurieren des Cache für adaptive Formulare {#configure-adaptive-forms-cache}

Cachen ist ein Mechanismus zum Verkürzen von Datenzugriffszeiten, zur Reduktion von Wartezeiten und zur Steigerung der Geschwindigkeit der Eingabe/Ausgabe (I/A). Der Cache für adaptive Formulare speichert nur HTML-Inhalte und JSON-Strukturen eines adaptiven Formulars, ohne die vorausgefüllten Daten zu speichern. Die Zeit, die benötigt wird, um ein adaptives Formular auf dem Client zu rendern, wird dadurch reduziert. Er wurde speziell für adaptive Formular konzipiert.

## Konfigurieren des Cache für adaptive Formulare bei Autoren- und Veröffentlichungsinstanzen {#configure-adaptive-forms-caching-at-author-and-publish-instances}

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter `https://[server]:[port]/system/console/configMgr`.
1. Klicken Sie auf **[!UICONTROL Konfiguration für adaptive Formulare und interaktiven Kommunikations-Web-Kanal]**, um die Konfigurationswerte zu bearbeiten.
1. Geben Sie im Dialogfeld [!UICONTROL Bearbeiten der Konfigurationswerte] die maximale Anzahl von Formularen oder Dokumenten an, die eine Instanz des AEM [!DNL Forms]-Servers im Feld **[!UICONTROL Anzahl adaptiver Formulare]** zwischenspeichern kann. Der Standardwert ist 100.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, setzen Sie den Wert im Feld Anzahl adaptiver Forms auf **0**. Der Cache wird zurückgesetzt, und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

   ![Dialogfeld zum Konfigurieren des HTML-Cache für adaptive Formulare](assets/cache-configuration-edit.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

Ihre Umgebung ist für die Nutzung des Cache für adaptive Formulare und zugehörige Assets konfiguriert.


## (Optional) Konfigurieren des Dispatcher-Cache für adaptive Formulare {#configure-the-cache}

Um die Performance zu verbessern, können Sie die Dispatcher-Caching-Funktion für adaptive Formulare konfigurieren.

### Voraussetzungen {#pre-requisites}

* Aktivieren Sie die Option [Zusammenführen oder Vorbefüllen von Daten auf Client](prepopulate-adaptive-form-fields.md#prefill-at-client). Dadurch können eindeutige Daten für jede Instanz eines vorbefüllten Formulars zusammengeführt werden.
* [Aktivieren Sie „Flush-Agent“ für jede Veröffentlichungsinstanz](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=de#invalidating-dispatcher-cache-from-a-publishing-instance). Durch diesen Schritt wird die Cache-Performance für adaptive Formulare verbessert. Die Standard-URL von Flush-Agents ist `http://[server]:[port]]/etc/replication/agents.publish/flush.html`.

### Überlegungen zum Caching von adaptiven Formularen auf einem Dispatcher {#considerations}

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den AEM-[!DNL Dispatcher], um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars zwischenzuspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.
* URLs ohne Erweiterung werden nicht zwischengespeichert. Beispiel: URLs mit dem Muster `/content/forms/[folder-structure]/[form-name].html` werden im Cache abgelegt, während URLs mit dem Muster `/content/dam/formsanddocument/[folder-name]/<form-name>/jcr:content` von der Caching-Funktion ignoriert werden. Verwenden Sie daher URLs mit Erweiterungen, um die Caching-Vorteile zu nutzen.
* Überlegungen zu lokalisierten adaptiven Formularen:
   * Verwenden Sie das URL-Format `http://host:port/content/forms/af/<afName>.<locale>.html` anstelle von `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`, um die lokalisierte Version eines adaptiven Formulars aufzurufen.
   * Deaktivieren Sie die Verwendung des Browser-Gebietsschemas <!-- [Disable using browser locale](supporting-new-language-localization.md#how-localization-of-adaptive-form-works) -->für URLs mit dem Format `http://host:port/content/forms/af/<adaptivefName>.html`.
   * Wenn Sie das URL-Format `http://host:port/content/forms/af/<adaptivefName>.html` verwenden und **[!UICONTROL Browser-Gebietsschema verwenden]** im Konfigurations-Manager deaktiviert ist, wird die nicht lokalisierte Version des adaptiven Formulars bereitgestellt. Die nicht lokalisierte Sprache ist die Sprache, die bei der Entwicklung des adaptiven Formulars verwendet wurde. Das für Ihren Browser konfigurierte Gebietsschema (Browser-Gebietsschema) wird ignoriert und eine nicht lokalisierte Version des adaptiven Formulars wird bereitgestellt.
   * Wenn Sie das URL-Format `http://host:port/content/forms/af/<adaptivefName>.html` verwenden und **[!UICONTROL Browser-Gebietsschema verwenden]** im Konfigurations-Manager aktiviert ist, wird, sofern verfügbar, eine lokalisierte Version des adaptiven Formulars bereitgestellt. Die Sprache des lokalisierten adaptiven Formulars basiert auf dem für Ihren Browser konfigurierten Gebietsschema (Browser-Gebietsschema). Dies kann dazu führen, dass nur [die erste Instanz eines adaptiven Formulars zwischengespeichert abgelegt wird]. Um zu erfahren, wie Sie diesem Problem vorbeugen können, lesen Sie unter [Fehlerbehebung](#only-first-insatnce-of-adptive-forms-is-cached) nach.

### Aktivieren des Dispatcher-Cache

Führen Sie die folgenden Schritte aus, um den Dispatcher-Cache für adaptive Formulare zu aktivieren und zu konfigurieren:

1. Öffnen Sie die folgende URL für jede Veröffentlichungsinstanz Ihrer Umgebung und konfigurieren Sie den Replikationsagenten.
   `http://[server]:[port]]/etc/replication/agents.publish/flush.html`

1. [Fügen Sie folgende Zeilen in Ihre Datei dispatcher.any ein](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#automatically-invalidating-cached-files):

   ```JSON
      /invalidate
      {
      /0000
      {
      /glob "*"
      /type "deny"
      }
      /0001
      {
      # Consider all HTML files stale after an activation.
      /glob "*.html"
      /type "allow"
      }
      /0002
      {
      # Exclude htmls present in AF directories
      /glob "/content/forms/**/*.html"
      /type "deny"
      }
   ```

   Das Hinzufügen des Obenstehenden bewirkt Folgendes:

   * Ein adaptives Formular bleibt im Cache, bis eine aktualisierte Version des Formulars veröffentlicht wird.

   * Bei Veröffentlichung einer neueren Version der Ressource, auf die in einem adaptiven Formular verwiesen wird, wird das betroffene adaptive Formular automatisch ungültig. Beim automatischen Verfall referenzierter Ressourcen bestehen jedoch einige Ausnahmen. Um zu erfahren, wie Sie diese Ausnahmen vermeiden können, lesen Sie den Abschnitt [Fehlerbehebung](#troubleshooting).
1. [Fügen Sie die folgenden Regeln dispatcher.any oder einer benutzerdefinierten Regeldatei hinzu](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#specifying-the-documents-to-cache). Die URLs ohne Cache-Unterstützung werden ausgeschlossen. So zum Beispiel URLs für interaktive Kommunikation.

   ```JSON
      /0000 {
            /glob "*"
            /type "allow"
      }
      ## Don't cache csrf login tokens
      /0001 {
            /glob "/libs/granite/csrf/token.json"
            /type "deny"
      }
      ## Don't cache IC - print channel
      /0002 {
            /glob "/content/forms/**/channels/print.html"
            /type "deny"
      }
      ## Don't cache IC - web channel
      /0003 {
            /glob "/content/forms/**/channels/web.html"
            /type "deny"
      }
   ```

1. [Fügen Sie folgende Parameter der Liste „URL-Parameter ignorieren“ hinzu](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=de#ignoring-url-parameters):

   ```JSON
      /ignoreUrlParams {
      /0001 { /glob "*" /type "deny" }
      # added for AEM forms specific use cases.
      /0003 { /glob "dataRef" /type "allow" }
      }
   ```

Ihre AEM-Umgebung ist so konfiguriert, dass adaptive Formulare im Cache abgelegt werden. Es werden alle Arten von adaptiven Formularen zwischengespeichert. Falls Sie vor Bereitstellung einer zwischengespeicherten Seite die Zugriffsberechtigungen für diese Seite überprüfen müssen, lesen Sie [Caching von geschütztem Inhalt](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=de).

## Fehlerbehebung {#troubleshooting}

### Einige adaptive Formulare, die Bilder oder Videos enthalten, werden nicht automatisch im Dispatcher-Cache ungültig {#videos-or-images-not-auto-invalidated}

#### Problem {#issue1}

Wenn Sie Bilder oder Videos über den Asset-Browser auswählen und zu einem adaptiven Formular hinzufügen und diese Bilder und Videos im Assets-Editor bearbeitet werden, wird das adaptive Formular im Dispatcher-Cache, das diese Bilder enthält, nicht automatisch ungültig.

#### Lösung {#Solution1}

Nach dem Veröffentlichen der Bilder und Videos müssen Sie die Veröffentlichung des adaptiven Formulars, das auf diese Assets verweist, rückgängig machen und das Formular erneut veröffentlichen.

### Einige adaptive Formulare, die Inhaltsfragmente oder Experience Fragments enthalten, werden nicht automatisch im Dispatcher-Cache ungültig {#content-or-experience-fragment-not-auto-invalidated}

#### Problem {#issue2}

Wenn Sie ein Inhaltsfragment oder ein Erlebnisfragment zu einem adaptiven Formular hinzufügen und diese Assets unabhängig bearbeitet und veröffentlicht werden, wird das adaptive Formular im Dispatcher-Cache, das diese Assets enthält, nicht automatisch ungültig.

#### Lösung {#Solution2}

Nach dem Veröffentlichen des aktualisierten Inhalts- oder Erlebnisfragments machen Sie die Veröffentlichung des adaptiven Formulars, das diese Assets enthält, rückgängig und veröffentlichen es erneut.

### Nur die erste Instanz eines adaptiven Formulars wird zwischengespeichert {#only-first-insatnce-of-adptive-forms-is-cached}

#### Problem {#issue3}

Wenn die URL des adaptiven Formulars keine Lokalisierungsinformationen enthält und die Option **[!UICONTROL Browser-Gebietsschema verwenden]** im Konfigurations-Manager aktiviert ist, wird eine lokalisierte Version des adaptiven Formulars bereitgestellt und nur die erste Instanz des Formulars wird zwischengespeichert und jedem nachfolgenden Benutzer bereitgestellt.

#### Lösung {#Solution3}

Führen Sie zur Behebung dieses Problems folgende Schritte durch:

1. Öffnen Sie die Datei conf.d/httpd-dispatcher.conf oder eine andere Konfigurationsdatei, die für das Laden zur Laufzeit konfiguriert ist.

1. Fügen Sie Ihrer Datei folgenden Code hinzu und speichern Sie die Änderung. Es handelt sich dabei um Beispiel-Code, den Sie an Ihre Umgebung anpassen können.

```XML
   <VirtualHost *:80>
        # Set log level high during development / debugging and then turn it down to whatever is appropriate
    LogLevel rewrite:trace6
        # Start Rewrite Engine
    RewriteEngine On
        # Handle actual URL convention (just pass through)
        RewriteRule "^/content/forms/af/(.*)[.](.*).html$" "/content/forms/af/$1.$2.html" [PT]
 
        # Handle selector based redirection basded on browser language
        # The Rewrite Cond(ition) is looking for the Accept-Lanague header and if found takes the first two character which most likely will be the desired language selector.
        RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
        RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
   </VirtualHost>
```
