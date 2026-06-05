---
title: Einbetten anpassungsfähiger Formulare in externe Web-Seiten
description: Erfahren Sie, wie Sie ein adaptives Formular in eine externe Web-Seite einbetten
contentOwner: Khushwant Singh
docset: CloudService
role: Admin, Developer, User
feature: Adaptive Forms, Core Components
badgeSaas: label="AEM Forms" type="Positive" tooltip="Gilt für AEM Forms)."
exl-id: 198f6f76-1134-4818-89a0-6ddc84ff956c
source-git-commit: 4994babacc862977c5ff4c398027d54546c65212
workflow-type: tm+mt
source-wordcount: '1371'
ht-degree: 66%

---

# Einbetten eines adaptiven Formulars basierend auf Kernkomponenten in eine externe Web-Seite {#embed-adaptive-form-in-external-web-page}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Dieser Artikel |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/embed-adaptive-form-external-web-page.html?lang=de) |


Sie können [adaptive Formulare in eine AEM Sites-Seite](/help/forms/embed-adaptive-form-aem-sites.md) oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzende können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzenden, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

## Voraussetzungen {#prerequisites}

Führen Sie folgende Schritte aus, bevor Sie ein adaptives Formular in eine externe Website einbetten:

* Veröffentlichen Sie das einzubettende adaptive Formular in der Veröffentlichungsinstanz des AEM Forms-Servers.
* Erstellen Sie auf Ihrer Website eine Web-Seite oder legen Sie sie fest, um dort das adaptive Formular zu hosten. Stellen Sie sicher, dass die Web-Seite [jQuery-Dateien von einem CDN lesen](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) kann oder eine lokale jQuery-Kopie eingebettet hat. jQuery ist erforderlich, um ein adaptives Formular zu rendern.
* Wenn sich der AEM-Server und die Web-Seite in verschiedenen Domains befinden, führen Sie die im Abschnitt „Konfigurieren [&#x200B; absoluten Anforderungs-URLs mit GuideBridge“ und &quot;](#configure-base-url) [&#x200B; von AEM Forms, um adaptive Formulare auf einer Domain-übergreifenden Site bereitzustellen“ &#x200B;](#cross-site).

## Adaptives Formular einbetten {#embed-adaptive-form}

Sie können ein adaptives Formular einbetten, indem Sie einige Zeilen JavaScript in die Web-Seite einfügen. Die API im Code sendet eine HTTP-Anforderung an den AEM-Server für adaptive Formularressourcen und fügt das adaptive Formular in den angegebenen Formularcontainer ein.

Einbetten des adaptiven Formulars:

1. Erstellen Sie eine Web-Seite auf Ihrer Website mit dem folgenden Code:

   ```html
        <!doctype html>
        <html>
          <head>
            <title>This is the title of the webpage!</title>
            <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
          </head>
          <body>
          <div class="customafsection"/>
            <p>This section is replaced with the adaptive form.</p>
   
         <script>
         var options = {path:"/content/forms/af/myadaptiveform.html", CSS_Selector:".customafsection"};
         alert(options.path);
         var loadAdaptiveForm = function(options){
         //alert(options.path);
            if(options.path) {
                // options.path refers to the path of the adaptive form
                // For Example: /content/forms/af/ABC, where ABC is the adaptive form
                // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path
                var path = options.path;
                $.ajax({
                    url  : path ,
                    type : "GET",
                    data : {
                        // wcmmode=disabled is only required for author instance
                        // wcmmode : "disabled"
                    },
                    async: false,
                    success: function (data) {
                        // If jquery is loaded, set the inner html of the container
                        // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not        evaluate the script tag in HTML as per the HTML5 spec
                        // For example: document.getElementById().innerHTML
                        if(window.$ && options.CSS_Selector){
                            // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the        script tag.
                            $(options.CSS_Selector).html(data);
                        }
                    },
                    error: function (data) {
                        // any error handler
                    }
                });
            } else {
                if (typeof(console) !== "undefined") {
                    console.log("Path of Adaptive Form not specified to loadAdaptiveForm");
                }
            }
         }(options);
   
         </script>
          </body>
        </html>
   ```

1. Im eingebetteten Code:

   * Ersetzen Sie den Wert der Variablen *options.path* durch den Pfad der Veröffentlichungs-URL des adaptiven Formulars. Wenn der AEM-Server in einem Kontextpfad ausgeführt wird, stellen Sie sicher, dass die URL diesen Pfad enthält. Geben Sie immer den vollständigen Namen des adaptiven Formulars einschließlich der Erweiterung an. Beispielsweise befinden sich der obige Code und das adaptive Formular auf demselben AEM Forms-Server, daher wird im Beispiel der Kontextpfad des `/content/forms/af/myadaptiveform.html` für adaptive Formulare verwendet.
   * CSS_Selector ist der CSS-Selektor des Formularcontainers, in den das adaptive Formular eingebettet ist. Im obigen Beispiel ist die CSS-Klasse „.customafsection“ der CSS-Selektor.

Das adaptive Formular wird in die Web-Seite eingebettet. Beobachten Sie Folgendes im eingebetteten adaptiven Formular:

* Entwürfe und übermittelte Formulare sind auf der entsprechenden Registerkarte im Forms Portal verfügbar.
* Die im adaptiven Originalformular konfigurierte Übermittlungsaktion wird im eingebetteten Formular beibehalten.
* Regeln für adaptive Formulare bleiben erhalten und sind im eingebetteten Formular voll funktionsfähig.
* Die im Originalformular konfigurierten Experience Targeting- und A/B-Tests funktionieren im eingebetteten adaptiven Formular nicht.
* Wenn Adobe Analytics im ursprünglichen Formular konfiguriert ist, werden die Analysedaten vom Adobe Analytics-Server erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.
* In auf Kernkomponenten basierenden adaptiven Formularen werden die Client-Bibliotheken (ClientLibs) zusammen mit den Kopf- und Fußzeilenkomponenten eines Formulars eingeschlossen und geladen. Wenn Sie also ein auf Kernkomponenten basierendes adaptives Formular in eine Web-Seite einbetten, enthält diese immer die Kopf- und Fußzeile des Formulars.

## Konfigurieren absoluter Anforderungs-URLs mit GuideBridge {#configure-base-url}

Wenn sich der AEM-Server und die Web-Seite in verschiedenen Domains befinden, können Sie die GuideBridge-API verwenden, um den von den GuideRuntime-Bibliotheken generierten Anfragen einen absoluten AEM-Veröffentlichungsursprung voranzustellen. Verwenden Sie die `baseUrl`-Konfiguration, um guideRuntime anzuweisen, Anforderungen wie Formularübermittlung, Datenabruf zum Vorbefüllen, Generierung von Datensatzdokumenten, Datei-Uploads und internen Übermittlungsvorgängen den angegebenen absoluten Ursprung voranzustellen.

Fügen Sie der einbettenden Web-Seite das folgende Snippet zusammen mit der vorhandenen `guideBridge.connect`-Implementierung hinzu:

```javascript
window.guideBridge.connect(function () {
    window.guideBridge.registerConfig("baseUrl", "https://publish.example.com");
});
```

Ersetzen Sie `https://publish.example.com` durch die Veröffentlichungs-URL des AEM Forms-Servers.

Mit dieser Konfiguration wird eine Anfrage-URL ähnlich dem folgenden Beispiel angezeigt:

`/content/forms/af/my-form/jcr:content/guideContainer.af.submit.jsp`

wird wie folgt an den AEM-Server gesendet:

`https://publish.example.com/content/forms/af/my-form/jcr:content/guideContainer.af.submit.jsp`

Wenn sich der AEM-Server und die Web-Seite in verschiedenen Domains befinden, müssen Sie auch CORS in der AEM-Veröffentlichungsinstanz konfigurieren. Führen Sie die im Abschnitt &quot;AEM Forms [&#x200B; Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site aktivieren“ &#x200B;](#cross-site).

## Beispieltopologie {#sample-topology}

Die externe Web-Seite, in die das adaptive Formular eingebettet wird, sendet Anfragen an den AEM-Server, der sich in der Regel hinter der Firewall in einem privaten Netzwerk befindet. Um sicherzustellen, dass die Anfragen sicher an den AEM-Server weitergeleitet werden, wird empfohlen, einen Reverse-Proxy-Server einzurichten.

Sehen wir uns ein Beispiel an, wie Sie einen Apache 2.4-Reverse-Proxy-Server ohne Dispatcher einrichten können. In diesem Beispiel hosten Sie den AEM-Server mit dem Kontextpfad `/forms` und weisen `/forms` für den Reverse-Proxy zu. Dadurch wird sichergestellt, dass alle Anfragen für `/forms` auf dem Apache-Server an die AEM-Instanz weitergeleitet werden. Diese Topologie hilft dabei, die Anzahl der Regeln auf der Dispatcher-Ebene zu reduzieren, da alle Anfragen mit dem Präfix `/forms` an den AEM-Server weitergeleitet werden.

1. Öffnen Sie die Konfigurationsdatei `httpd.conf` und heben Sie den Kommentar für die folgenden Codezeilen auf. Alternativ können Sie die folgenden Codezeilen in die Datei einfügen.

   ```text
   LoadModule proxy_html_module modules/mod_proxy_html.so
   LoadModule proxy_http_module modules/mod_proxy_http.so
   ```

1. Richten Sie Proxy-Regeln ein, indem Sie die folgenden Codezeilen in der Konfigurationsdatei `httpd-proxy.conf` hinzufügen.

   ```text
   ProxyPass /forms https://[AEM_Instance]/forms
   ProxyPassReverse /forms https://[AEM_Instance]/forms
   ```

   Ersetzen Sie in den Regeln `[AEM_Instance]` durch die Veröffentlichungs-URL des AEM-Servers.

Wenn Sie den AEM-Server nicht in einem Kontextpfad bereitstellen, lauten die Proxy-Regeln auf Apache-Ebene wie folgt:

```text
ProxyPass /content https://<AEM_Instance>/content
ProxyPass /etc https://<AEM_Instance>/etc
ProxyPass /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# CSRF Filter
ProxyPass /libs/granite/csrf/token.json https://<AEM_Instance>/libs/granite/csrf/token.json

ProxyPassReverse /etc https://<AEM_Instance>/etc
ProxyPassReverse /etc.clientlibs https://<AEM_Instance>/etc.clientlibs
# written for thank you page and other URL present in AF during redirect
ProxyPassReverse /content https://<AEM_Instance>/content
```

>[!NOTE]
>
>Wenn Sie eine andere Topologie einrichten, stellen Sie sicher, dass Sie die URLs für Senden, Vorausfüllen und andere Funktionen auf der Dispatcher-Ebene in die Positivliste eintragen.

## Best Practices {#best-practices}

Berücksichtigen Sie beim Einbetten eines adaptiven Formulars in eine Web-Seite die folgenden Best Practices:

* Stellen Sie sicher, dass die in den CSS der Web-Seite definierten Formatierungsregeln nicht mit den CSS des Formularobjekts in Konflikt stehen. Um dies zu vermeiden, können Sie die CSS der Web-Seite im Design für das adaptive Formular mithilfe der AEM-Client-Bibliothek wiederverwenden. Weitere Informationen zur Verwendung der Client-Bibliothek in den Designs für adaptive Formulare finden Sie unter [Designs in AEM Forms](/help/forms/using-themes-in-core-components.md).
* Stellen Sie sicher, dass der Formular-Container auf der Web-Seite die gesamte Fensterbreite verwendet. So wird sichergestellt, dass die für mobile Geräte konfigurierten CSS-Regeln ohne Änderungen funktionieren. Wenn der Formular-Container nicht die gesamte Fensterbreite einnimmt, müssen Sie ein benutzerdefiniertes CSS schreiben, damit sich das Formular an verschiedene mobile Geräte anpasst.
* Verwenden Sie die API `[getData](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/javascript-api/GuideBridge.html)`, um die XML- oder JSON-Darstellung der Formulardaten im Client abzurufen.
* Verwenden Sie die API `[unloadAdaptiveForm](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/javascript-api/GuideBridge.html)`, um das adaptive Formular aus HTML DOM zu entfernen.
* Richten Sie den Header „access-control-origin“ ein, wenn Sie eine Antwort von einem AEM-Server senden.

## Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site durch AEM Forms {#cross-site}

Wenn sich der AEM-Server und die Web-Seite in verschiedenen Domains befinden, konfigurieren Sie die AEM-Veröffentlichungsinstanz mit einer der folgenden Optionen.

>[!NOTE]
>
> AEM as a Cloud Service bietet keinen Zugriff auf die OSGi-Web-Konsole in Veröffentlichungsinstanzen. Fügen Sie die folgenden Konfigurationen zu Ihrem Cloud Manager-Git-Repository unter `ui.config/src/main/content/jcr_root/apps/<application-folder>/osgiconfig/config.publish` hinzu und [&#x200B; Sie die Änderungen über Cloud Manager &#x200B;](/help/implementing/cloud-manager/deploy-code.md).

>[!BEGINTABS]

>[!TAB Verwenden der GuideBridge-baseUrl-Konfiguration]

Wenn Sie die GuideBridge-`baseUrl`-Konfiguration verwenden, konfigurieren Sie CORS auf der AEM-Veröffentlichungsinstanz so, dass der AEM-Server geeignete Kopfzeilen für die Endpunkte „Übermittlung“, „Vorbefüllen“ und „Datensatzdokument“ zurückgibt.

1. Navigieren Sie in Ihrem Cloud Manager-Git-Repository zu `ui.config/src/main/content/jcr_root/apps/<application-folder>/osgiconfig/config.publish`.
1. Erstellen Sie die OSGi-Konfigurationsdatei `com.adobe.granite.cors.impl.CORSPolicyImpl~embedded-forms.cfg.json` mit Inhalten, die dem folgenden Beispiel ähneln. Ersetzen Sie `https://www.example.com` durch den Ursprung der einbettenden Web-Seite.

   ```json
   {
     "supportscredentials": false,
     "supportedmethods": [
       "GET",
       "HEAD",
       "POST"
     ],
     "exposedheaders": [
       ""
     ],
     "alloworigin": [
       "https://www.example.com"
     ],
     "maxage:Integer": 1800,
     "alloworiginregexp": [
       ""
     ],
     "supportedheaders": [
       "Origin",
       "Accept",
       "X-Requested-With",
       "Content-Type",
       "Access-Control-Request-Method",
       "Access-Control-Request-Headers"
     ],
     "allowedpaths": [
       "/content/forms/af/.*",
       "/libs/granite/csrf/token.json"
     ]
   }
   ```

1. Übertragen, Übertragen und Bereitstellen der Konfiguration über eine Cloud Manager-Pipeline.

Weitere Informationen finden Sie unter [CORS-Konfiguration (Cross-Origin Resource Sharing)](/help/headless/deployment/cross-origin-resource-sharing.md).

>[!TAB Apache Sling Referrer Filter]

Wenn Sie einen Reverse-Proxy verwenden oder das adaptive Formular ohne die GuideBridge-`baseUrl`-Konfiguration einbetten, konfigurieren Sie den Apache Sling Referrer-Filter auf der AEM-Veröffentlichungsinstanz.

1. Navigieren Sie in Ihrem Cloud Manager-Git-Repository zu `ui.config/src/main/content/jcr_root/apps/<application-folder>/osgiconfig/config.publish`.
1. Erstellen oder aktualisieren Sie die OSGi-Konfigurationsdatei `org.apache.sling.security.impl.ReferrerFilter.cfg.json` mit Inhalten, die dem folgenden Beispiel ähneln. Ersetzen Sie `www.example.com` durch die Domain, in der sich die Webseite befindet.

   ```json
   {
     "allow.empty": false,
     "allow.hosts": [
       "www.example.com"
     ],
     "allow.hosts.regexp": [
       ""
     ],
     "filter.methods": [
       "POST",
       "PUT",
       "DELETE",
       "COPY",
       "MOVE"
     ],
     "exclude.agents.regexp": [
       ""
     ]
   }
   ```

1. Übertragen, Übertragen und Bereitstellen der Konfiguration über eine Cloud Manager-Pipeline.

>[!WARNING]
>
> Der Referrer-Filter von AEM ist keine OSGi-Konfigurations-Factory, d. h., für einen AEM-Service ist immer nur eine Konfiguration aktiv. Wenn möglich, vermeiden Sie das Hinzufügen benutzerdefinierter Referrer-Filterkonfigurationen, da dies die nativen Konfigurationen von AEM überschreibt und die Produktfunktionalität beeinträchtigen kann.

Weitere Informationen finden Sie unter [Konfiguration des Referrer-Filters](/help/headless/deployment/referrer-filter.md).

>[!ENDTABS]

<!--

>[!MORELIKETHIS]
>
>* [Embed adaptive form based on core components to AEM sites](/help/forms/embed-adaptive-form-core-components-aem-sites.md)

-->