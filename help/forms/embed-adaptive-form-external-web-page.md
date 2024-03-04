---
title: Wie bettet man ein adaptives Formular in eine externe Web-Seite ein?
description: Erfahren Sie, wie Sie ein adaptives Formular in eine Website einbetten.
topic-tags: author
role: Admin, Developer, User
feature: Adaptive Forms
exl-id: 00b8cd79-bf2d-4001-b2d6-1b020c868008
source-git-commit: 527c9944929c28a0ef7f3e617ef6185bfed0d536
workflow-type: ht
source-wordcount: '1003'
ht-degree: 100%

---

# Einbetten eines adaptiven Formulars in eine externe Web-Seite{#embed-adaptive-form-in-external-web-page}

| Version | Artikel-Link |
| -------- | ---------------------------- |
| AEM 6.5 | [Hier klicken](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-basic-authoring/embed-adaptive-form-external-web-page.html?lang=de) |
| AEM as a Cloud Service | Dieser Artikel |

Sie können [adaptive Formulare in eine AEM Sites-Seite](/help/forms/embed-adaptive-form-aem-sites.md) oder eine außerhalb von AEM gehostete Webseite einbetten. Das eingebettete adaptive Formular ist voll funktionsfähig, und Benutzende können es ausfüllen und senden, ohne die Seite zu verlassen. Es hilft Benutzenden, im Kontext anderer Elemente auf der Web-Seite zu bleiben und gleichzeitig mit dem Formular zu interagieren.

## Voraussetzungen {#prerequisites}

Führen Sie folgende Schritte aus, bevor Sie ein adaptives Formular in eine externe Website einbetten:

* Veröffentlichen Sie das einzubettende adaptive Formular in der Veröffentlichungsinstanz des AEM Forms-Servers.
* Erstellen Sie auf Ihrer Website eine Web-Seite oder legen Sie sie fest, um dort das adaptive Formular zu hosten. Stellen Sie sicher, dass die Web-Seite [jQuery-Dateien von einem CDN lesen](https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js) kann oder eine lokale jQuery-Kopie eingebettet hat. jQuery ist erforderlich, um ein adaptives Formular zu rendern.
* Wenn der AEM-Server und die Web-Seite sich in verschiedenen Domains befinden, führen Sie die im Abschnitt [Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site durch AEM Forms](#cross-site) beschriebenen Schritte aus.

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
    var options = {path:"/content/forms/af/locbasic.html", dataRef:"", themepath:"", CSS_Selector:".customafsection"};
    alert(options.path);
    var loadAdaptiveForm = function(options){
    //alert(options.path);
       if(options.path) {
           // options.path refers to the path of the adaptive form
           // For Example: /content/forms/af/ABC, where ABC is the adaptive form
           // Note: If AEM server is running on a context path, the adaptive form URL must contain the context path
           var path = options.path;
           path += "/jcr:content/guideContainer.html";
           $.ajax({
               url  : path ,
               type : "GET",
               data : {
                   // Set the wcmmode to be disabled
                   wcmmode : "disabled"
                   // Set the data reference, if any
                  // "dataRef": options.dataRef
                   // Specify a different theme for the form object
                 //  "themeOverride" : options.themepath
               },
               async: false,
               success: function (data) {
                   // If jquery is loaded, set the inner html of the container
                   // If jquery is not loaded, use APIs provided by document to set the inner HTML but these APIs would not evaluate the script tag in HTML as per the HTML5 spec
                   // For example: document.getElementById().innerHTML
                   if(window.$ && options.CSS_Selector){
                       // HTML API of jquery extracts the tags, updates the DOM, and evaluates the code embedded in the script tag.
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

   * Ersetzen Sie den Wert der Variablen *options.path* durch den Pfad der Veröffentlichungs-URL des adaptiven Formulars. Wenn der AEM-Server in einem Kontextpfad ausgeführt wird, stellen Sie sicher, dass die URL diesen Pfad enthält. Geben Sie immer den vollständigen Namen des adaptiven Formulars einschließlich der Erweiterung an. Beispielsweise befinden sich der Code und das adaptive Formular im Beispiel oben auf demselben AEM Forms-Server. Daher wird im Kontextpfad dieses Beispiels der Pfad „`/content/forms/af/locbasic.html`“ für das adaptive Formular verwendet.
   * Ersetzen Sie *options.dataRef* durch Attribute, die mit der URL übertragen werden sollen. Sie können die Variable dataref zum [Vorausfüllen eines adaptiven Formulars](/help/forms/prepopulate-adaptive-form-fields.md) verwenden.
   * Ersetzen Sie *options.themePath* durch den Pfad zu einem anderen Design als dem im adaptiven Formular konfigurierten Design. Alternativ können Sie den Design-Pfad mit dem Anfrageattribut angeben.
   * CSS_Selector ist der CSS-Selektor des Formularcontainers, in den das adaptive Formular eingebettet ist. Im obigen Beispiel ist die CSS-Klasse „.customafsection“ der CSS-Selektor.

Das adaptive Formular wird in die Web-Seite eingebettet. Beobachten Sie Folgendes im eingebetteten adaptiven Formular:

* Die Kopf- und Fußzeile im adaptiven Originalformular werden nicht vom eingebetteten Formular übernommen.
* Entwürfe und übermittelte Formulare sind auf der entsprechenden Registerkarte im Forms Portal verfügbar.
* Die im adaptiven Originalformular konfigurierte Übermittlungsaktion wird im eingebetteten Formular beibehalten.
* Regeln für adaptive Formulare bleiben erhalten und sind im eingebetteten Formular voll funktionsfähig.
* Die Experience Targeting- und A/B-Test-Konfigurationen im Originalformular funktionieren nicht im eingebetteten adaptiven Formular.
* Wenn Adobe Analytics im ursprünglichen Formular konfiguriert ist, werden die Analysedaten vom Adobe Analytics-Server erfasst. Sie sind jedoch nicht im Formularanalysebericht verfügbar.

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
>Wenn Sie eine andere Topologie einrichten, stellen Sie sicher, dass Sie die URLs für Übermitteln, Vorausfüllen und andere Funktionen auf der Dispatcher-Ebene in die Zulassungsliste eintragen.

## Best Practices {#best-practices}

Berücksichtigen Sie beim Einbetten eines adaptiven Formulars in eine Web-Seite die folgenden Best Practices:

* Stellen Sie sicher, dass die Formatierungsregeln im Web-Seiten-CSS nicht mit dem Formularobjekt-CSS in Konflikt stehen. Um Konflikte zu vermeiden, können Sie das Web-Seiten-CSS im Design für das adaptive Formular mithilfe der AEM-Client-Bibliothek wiederverwenden. Weitere Informationen zur Verwendung der Client-Bibliothek in den Designs für adaptive Formulare finden Sie unter [Designs in AEM Forms](/help/forms/themes.md).
* Verwenden Sie für den Formular-Container auf der Web-Seite die gesamte Fensterbreite. So wird sichergestellt, dass die für mobile Geräte konfigurierten CSS-Regeln ohne Änderungen funktionieren. Wenn der Formular-Container nicht die gesamte Fensterbreite einnimmt, müssen Sie ein benutzerdefiniertes CSS schreiben, damit sich das Formular an verschiedene mobile Geräte anpasst.
* Verwenden Sie die API `[getData](https://helpx.adobe.com/experience-manager/6-5/forms/javascript-api/GuideBridge.html)`, um die XML- oder JSON-Darstellung der Formulardaten im Client abzurufen.
* Verwenden Sie die API `[unloadAdaptiveForm](https://helpx.adobe.com/experience-manager/6-5/forms/javascript-api/GuideBridge.html)`, um das adaptive Formular aus HTML DOM zu entfernen.
* Richten Sie den Header „access-control-origin“ ein, wenn Sie eine Antwort von einem AEM-Server senden.

## Bereitstellung adaptiver Formulare auf einer Domain-übergreifenden Site durch AEM Forms {#cross-site}

1. Gehen Sie in der AEM-Veröffentlichungsinstanz zum Konfigurations-Manager der AEM-Web-Konsole unter `https://'[server]:[port]'/system/console/configMgr`.
1. Suchen Sie die Konfiguration **Apache Sling Referrer Filter** und öffnen Sie sie.
1. Geben Sie im Feld Zulässige Hosts die Domain an, in der sich die Webseite befindet. Dadurch kann der Host POST-Anforderungen an den AEM-Server senden. Sie können auch einen regulären Ausdruck verwenden, um eine Reihe von externen Anwendungs-Domains anzugeben.

>[!MORELIKETHIS]
>
>* [Einbetten eines adaptiven Formulars basierend auf Kernkomponenten in eine externe Web-Seite](/help/forms/embed-adaptive-form-core-components-external-web-page.md)
