---
title: Wie können wir adaptive Formulare in externe Webseiten einbetten?
description: Erfahren Sie, wie Sie ein adaptives Formular in eine externe Webseite einbetten
contentOwner: Khushwant Singh
docset: CloudService
role: Developer
exl-id: 198f6f76-1134-4818-89a0-6ddc84ff956c
source-git-commit: a942e87a33775851631a1fe123fa3e8d2686bb30
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 63%

---

# Einbetten des adaptiven Formulars basierend auf Kernkomponenten in eine externe Webseite {#embed-adaptive-form-in-external-web-page}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM as a Cloud Service | Dieser Artikel |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/embed-adaptive-form-external-web-page.html?lang=de) |


Sie können [adaptive Formulare in eine AEM Sites-Seite](/help/forms/embed-adaptive-form-aem-sites.md) oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzende können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzenden, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

## Voraussetzungen {#prerequisites}

Führen Sie die folgenden Schritte aus, bevor Sie ein adaptives Formular in eine externe Website einbetten

* Veröffentlichen Sie das einzubettende adaptive Formular in der Veröffentlichungsinstanz von AEM Forms Server.
* Erstellen Sie auf Ihrer Website eine Webseite oder legen Sie sie fest, um das adaptive Formular zu hosten. Stellen Sie sicher, dass die Webseite [jQuery-Dateien von einem CDN lesen](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) kann oder eine lokale Kopie von jQuery eingebettet hat. jQuery ist erforderlich, um ein adaptives Formular zu rendern.
* Wenn AEM-Server und die Web-Seite sich in verschiedenen Domains befinden, führen Sie die im Abschnitt [Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site durch AEM Forms](#cross-site) beschriebenen Schritte aus.

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

   * Ersetzen Sie den Wert der Variablen *options.path* durch die Veröffentlichungs-URL des adaptiven Formulars. Wenn der AEM-Server in einem Kontextpfad ausgeführt wird, stellen Sie sicher, dass die URL diesen Pfad enthält. Geben Sie immer den vollständigen Namen des adaptiven Formulars einschließlich der Erweiterung an. Beispielsweise befinden sich der Code und das adaptive Formular im Beispiel oben auf demselben AEM Forms-Server, daher wird im Kontextpfad dieses Beispiels der Pfad „/content/forms/af/locbasic.html“ für das adaptive Formular verwendet.
   * CSS_Selector ist der CSS-Selektor des Formularcontainers, in den das adaptive Formular eingebettet ist. Im obigen Beispiel ist die CSS-Klasse „.customafsection“ der CSS-Selektor.

Das adaptive Formular ist in die Webseite eingebettet. Beachten Sie Folgendes im eingebetteten adaptiven Formular:

* Entwürfe und übermittelte Formulare sind auf der entsprechenden Registerkarte im Forms Portal verfügbar.
* Die im ursprünglichen adaptiven Formular konfigurierte Sendeaktion wird im eingebetteten Formular beibehalten.
* Die Regeln für adaptive Formulare werden beibehalten und im eingebetteten Formular vollständig verwendet.
* Erlebnis-Targeting und im ursprünglichen adaptiven Formular konfigurierte A/B-Tests funktionieren im eingebetteten Formular nicht.
* Wenn Adobe Analytics im Originalformular konfiguriert ist, werden die Analysedaten auf dem Adobe Analytics-Server erfasst. Sie ist jedoch nicht im Forms-Analysebericht verfügbar.
* In Adaptive Forms basierend auf Kernkomponenten werden die Client-Bibliotheken (ClientLibs) zusammen mit den Kopf- und Fußzeilenkomponenten eines Formulars eingeschlossen und geladen. Wenn Sie also eine adaptive Forms, die auf Kernkomponenten basiert, in eine Webseite einbetten, enthält sie immer Kopf- und Fußzeile des Formulars.

## Beispieltopologie {#sample-topology}

Die externe Webseite, die das adaptive Formular einbettet, sendet Anforderungen an den AEM-Server, der sich normalerweise hinter der Firewall in einem privaten Netzwerk befindet. Um sicherzustellen, dass die Anfragen sicher an den AEM-Server weitergeleitet werden, wird empfohlen, einen Reverse-Proxy-Server einzurichten.

Sehen wir uns ein Beispiel an, wie Sie einen Apache 2.4 Reverse-Proxy-Server ohne Dispatcher einrichten können. In diesem Beispiel hosten Sie den AEM-Server mit dem Kontextpfad `/forms` und weisen `/forms` für den Reverse-Proxy zu. Dadurch wird sichergestellt, dass alle Anforderungen für `/forms` auf dem Apache-Server an die AEM-Instanz geleitet werden. Diese Topologie hilft dabei, die Anzahl der Regeln auf der Dispatcher-Ebene zu reduzieren, da alle Anforderungen mit dem Präfix `/forms` an den AEM-Server weitergeleitet werden.

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

Beachten Sie beim Einbetten eines adaptiven Formulars in eine Webseite die folgenden Best Practices:

* Stellen Sie sicher, dass die Stilregeln, die in der CSS der Webseite definiert sind, nicht mit dem CSS des Formularobjekts in Konflikt stehen. Um Konflikte zu vermeiden, können Sie das CSS der Webseite im Thema für adaptive Formulare mithilfe AEM Client-Bibliothek wiederverwenden. Informationen zur Verwendung der Client-Bibliothek in Designs für adaptive Formulare finden Sie unter [Designs in AEM Forms](/help/forms/using-themes-in-core-components.md).
* Stellen Sie sicher, dass der Formularcontainer auf der Webseite die gesamte Fensterbreite verwendet. Dadurch wird sichergestellt, dass die für Mobilgeräte konfigurierten CSS-Regeln ohne Änderungen funktionieren. Wenn der Formular-Container nicht die gesamte Fensterbreite benötigt, müssen Sie benutzerdefiniertes CSS schreiben, damit das Formular an verschiedene Mobilgeräte angepasst werden kann.
* Verwenden Sie die API `[getData](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/javascript-api/GuideBridge.html)`, um die XML- oder JSON-Darstellung der Formulardaten im Client abzurufen.
* Verwenden Sie die API `[unloadAdaptiveForm](https://developer.adobe.com/experience-manager/reference-materials/6-5/forms/javascript-api/GuideBridge.html)`, um das adaptive Formular aus HTML DOM zu entfernen.
* Richten Sie den Header „access-control-origin“ ein, wenn Sie eine Antwort vom AEM-Server senden.

## Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site durch AEM Forms {#cross-site}

1. Gehen Sie in der AEM-Veröffentlichungsinstanz zum Konfigurations-Manager der AEM-Web-Konsole unter `https://'[server]:[port]'/system/console/configMgr`.
1. Suchen Sie die Konfiguration **Apache Sling Referrer Filter** und öffnen Sie sie.
1. Geben Sie im Feld Zulässige Hosts die Domain an, in der sich die Webseite befindet. Dadurch kann der Host POST-Anforderungen an den AEM-Server senden. Sie können auch einen regulären Ausdruck verwenden, um eine Reihe von externen Anwendungs-Domains anzugeben.

<!--

>[!MORELIKETHIS]
>
>* [Embed adaptive form based on core components to AEM sites](/help/forms/embed-adaptive-form-core-components-aem-sites.md)

-->