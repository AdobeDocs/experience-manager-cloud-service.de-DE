---
title: Was ist der Cache für adaptive Formulare? und wie ein AEM adaptives Formular zwischengespeichert werden kann?
description: Der Adaptive Forms-Cache wurde für adaptive Forms und Dokumente entwickelt, um die zum Rendern eines adaptiven Formulars oder Dokuments erforderliche Zeit zu verkürzen.
uuid: ba8f79fd-d8dc-4863-bc0d-7c642c45505c
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: 9fa6f761-58ca-4cd0-8992-b9337dc1a279
source-git-commit: d33c7278d16a8cce76c87b606ca09aa91f1c3563
workflow-type: tm+mt
source-wordcount: '974'
ht-degree: 54%

---


# Konfigurieren des Cache für adaptive Formulare {#configure-adaptive-forms-cache}

Cachen ist ein Mechanismus zum Verkürzen von Datenzugriffszeiten, zur Reduktion von Wartezeiten und zur Steigerung der Geschwindigkeit der Eingabe/Ausgabe (I/O). Der Adaptive Forms-Cache speichert nur den HTML-Inhalt und die JSON-Struktur eines adaptiven Formulars, ohne dass vorausgefüllte Daten gespeichert werden. Die Zeit, die benötigt wird, um ein adaptives Formular auf dem Client zu rendern, wird dadurch reduziert. Er wurde speziell für adaptive Formular konzipiert.

## Konfigurieren des Cache für adaptive Formulare bei Autoren- und Veröffentlichungsinstanzen {#configure-adaptive-forms-caching-at-author-and-publish-instances}

1. Wechseln Sie zum Konfigurations-Manager der AEM-Web-Konsole unter `https://[server]:[port]/system/console/configMgr`.
1. Klicken Sie auf **[!UICONTROL Konfiguration für adaptive Formulare und interaktiven Kommunikations-Web-Kanal]**, um die Konfigurationswerte zu bearbeiten.
1. Im [!UICONTROL Konfigurationswerte bearbeiten] Dialogfeld angeben, die maximale Anzahl von Formularen angeben oder eine Instanz des AEM dokumentieren [!DNL Forms Server] kann im **[!UICONTROL Anzahl der adaptiven Forms]** -Feld. Der Standardwert ist 100.

   >[!NOTE]
   >
   >Um den Cache zu deaktivieren, setzen Sie den Wert im Feld Anzahl adaptiver Forms auf **0**. Der Cache wird zurückgesetzt, und alle Formulare und Dokumente werden aus dem Cache entfernt, wenn Sie die Cachekonfiguration deaktivieren oder ändern.

   ![Dialogfeld zum Konfigurieren des HTML-Cache für adaptive Formulare](assets/cache-configuration-edit.png)

1. Klicken Sie auf **[!UICONTROL Speichern]**, um die Konfiguration zu speichern.

Ihre Umgebung ist für die Nutzung des Cache für adaptive Formulare und zugehörige Assets konfiguriert.


## (Optional) Konfigurieren des Cache für adaptive Formulare im Dispatcher {#configure-the-cache}

Sie können auch die Zwischenspeicherung adaptiver Formulare im Dispatcher konfigurieren, um die Leistung zusätzlich zu verbessern.

### Voraussetzungen {#pre-requisites}

* Aktivieren Sie die [Zusammenführen oder Vorausfüllen von Daten auf dem Client](prepopulate-adaptive-form-fields.md#prefill-at-client) -Option. Dadurch können eindeutige Daten für jede Instanz eines vorbefüllten Formulars zusammengeführt werden.
* [Aktivieren eines Flush-Agenten für jede Veröffentlichungsinstanz](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/page-invalidate.html?lang=de#invalidating-dispatcher-cache-from-a-publishing-instance). Durch diesen Schritt wird die Cache-Performance für adaptive Formulare verbessert. Die Standard-URL von Flush-Agents ist `http://[server]:[port]]/etc/replication/agents.publish/flush.html`.

### Überlegungen zum Zwischenspeichern des adaptiven Forms auf einem Dispatcher {#considerations}

* Wenn Sie den Cache für adaptive Formulare verwenden, nutzen Sie den AEM-[!DNL Dispatcher], um Client-Bibliotheken (CSS und JavaScript) eines adaptiven Formulars zwischenzuspeichern.
* Beim Entwickeln der benutzerdefinierten Komponenten muss auf dem für die Entwicklung verwendeten Server der Cache für adaptive Formulare deaktiviert bleiben.
* URLs ohne Erweiterung werden nicht zwischengespeichert. Beispiel: URL mit Muster `/content/forms/[folder-structure]/[form-name].html` zwischengespeichert werden und beim Zwischenspeichern werden URLs mit Mustern ignoriert `/content/dam/formsanddocument/[folder-name]/<form-name>/jcr:content`. Verwenden Sie daher URLs mit Erweiterungen, um die Vorteile des Caching zu nutzen.
* Überlegungen zu lokalisierten adaptiven Formularen:
   * Verwenden Sie das URL-Format `http://host:port/content/forms/af/<afName>.<locale>.html` anstelle von `http://host:port/content/forms/af/afName.html?afAcceptLang=<locale>`, um die lokalisierte Version eines adaptiven Formulars aufzurufen.
   * Deaktivieren Sie die Verwendung des Browser-Gebietsschemas <!-- [Disable using browser locale](supporting-new-language-localization.md#how-localization-of-adaptive-form-works) -->für URLs mit dem Format `http://host:port/content/forms/af/<adaptivefName>.html`.
   * Wenn Sie das URL-Format `http://host:port/content/forms/af/<adaptivefName>.html` verwenden und **[!UICONTROL Browser-Gebietsschema verwenden]** im Konfigurations-Manager deaktiviert ist, wird die nicht lokalisierte Version des adaptiven Formulars bereitgestellt. Die nicht lokalisierte Sprache ist die Sprache, die bei der Entwicklung des adaptiven Formulars verwendet wurde. Das für Ihren Browser konfigurierte Gebietsschema (Browser-Gebietsschema) wird nicht berücksichtigt und es wird eine nicht lokalisierte Version des adaptiven Formulars bereitgestellt.
   * Wenn Sie das URL-Format `http://host:port/content/forms/af/<adaptivefName>.html` verwenden und **[!UICONTROL Browser-Gebietsschema verwenden]** im Konfigurations-Manager aktiviert ist, wird, sofern verfügbar, eine lokalisierte Version des adaptiven Formulars bereitgestellt. Die Sprache des lokalisierten adaptiven Formulars basiert auf dem für Ihren Browser konfigurierten Gebietsschema (Browser-Gebietsschema). Dies kann zu [Zwischenspeicherung nur der ersten Instanz eines adaptiven Formulars]. Um zu erfahren, wie Sie diesem Problem vorbeugen können, lesen Sie unter [Fehlerbehebung](#only-first-insatnce-of-adptive-forms-is-cached) nach.

### Zwischenspeicherung im Dispatcher aktivieren

Führen Sie die folgenden Schritte aus, damit Sie die Zwischenspeicherung von Adaptive Forms in Dispatcher aktivieren und konfigurieren können:

1. Öffnen Sie die folgende URL für jede Veröffentlichungsinstanz Ihrer Umgebung und konfigurieren Sie den Replikationsagenten:
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

   * Wenn eine neuere Version einer Ressource veröffentlicht wird, auf die in einem adaptiven Formular verwiesen wird, wird das betroffene adaptive Formular automatisch invalidiert. Beim automatischen Verfall referenzierter Ressourcen bestehen jedoch einige Ausnahmen. Eine Problemumgehung für Ausnahmen finden Sie unter [Fehlerbehebung](#troubleshooting) Abschnitt.
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

Ihre AEM-Umgebung ist so konfiguriert, dass adaptive Formulare im Cache abgelegt werden. Es werden alle Arten von adaptiven Formularen zwischengespeichert. Wenn Sie die Benutzerzugriffsberechtigungen für eine Seite überprüfen müssen, bevor Sie die zwischengespeicherte Seite bereitstellen, lesen Sie [Zwischenspeichern gesicherter Inhalte](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/permissions-cache.html?lang=de).

## Fehlerbehebung {#troubleshooting}

### Einige adaptive Forms, die Bilder oder Videos enthalten, werden nicht automatisch aus dem Dispatcher-Cache invalidiert {#videos-or-images-not-auto-invalidated}

#### Problem {#issue1}

Wenn Sie Bilder oder Videos über den Asset-Browser auswählen und in einem adaptiven Formular hinzufügen und sie im Assets-Editor bearbeitet werden, werden diese Assets nicht automatisch aus dem Dispatcher-Cache invalidiert.

#### Lösung {#Solution1}

Nach dem Veröffentlichen der Bilder und Videos müssen Sie die Veröffentlichung des adaptiven Formulars, das auf diese Assets verweist, rückgängig machen und das Formular erneut veröffentlichen.

### Einige adaptive Forms, die Inhaltsfragmente oder Experience Fragments enthalten, werden nicht automatisch aus dem Dispatcher-Cache invalidiert {#content-or-experience-fragment-not-auto-invalidated}

#### Problem {#issue2}

Wenn Sie ein Inhaltsfragment oder ein Experience Fragment zu einem adaptiven Formular hinzufügen und diese Assets unabhängig bearbeitet und veröffentlicht werden, wird Adaptive Forms mit solchen Assets, die nicht automatisch aus dem Dispatcher-Cache ungültig gemacht werden, automatisch veröffentlicht.

#### Lösung {#Solution2}

Nachdem Sie ein aktualisiertes Inhaltsfragment oder Experience Fragment veröffentlicht haben, machen Sie die Veröffentlichung des adaptiven Forms, der diese Assets verwendet, explizit rückgängig und veröffentlichen Sie es.

### Nur die erste Instanz eines adaptiven Formulars wird zwischengespeichert{#only-first-insatnce-of-adptive-forms-is-cached}

#### Problem {#issue3}

Wenn die URL des adaptiven Formulars keine Lokalisierungsinformationen enthält und **[!UICONTROL Gebietsschema des Browsers verwenden]** im Konfigurationsmanager aktiviert ist. Es wird eine lokalisierte Version des adaptiven Formulars bereitgestellt und nur die erste Instanz des adaptiven Formulars wird zwischengespeichert und an jeden nachfolgenden Benutzer gesendet.

#### Lösung {#Solution3}

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
        # The Rewrite Cond(ition) is looking for the Accept-Lanague header and if found takes the first two characters which most likely is the desired language selector.
        RewriteCond %{HTTP:Accept-Language} ^(..).*$ [NC]
        RewriteRule "^/content/forms/af/(.*).html$" "/content/forms/af/$1.%1.html" [R]
   </VirtualHost>
```
