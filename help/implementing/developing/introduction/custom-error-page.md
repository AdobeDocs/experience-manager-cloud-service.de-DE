---
title: Benutzerdefinierte Fehlerseiten
description: AEM enthält einen standardmäßigen Fehlerhandler für die Verarbeitung von HTTP-Fehlern, der angepasst werden kann.
translation-type: tm+mt
source-git-commit: d7e9bdee83f1b85436185ca57420ee178268cb33
workflow-type: tm+mt
source-wordcount: '503'
ht-degree: 50%

---


# Anpassen von Fehlerseiten {#customizing-error-pages}

AEM enthält einen Standard-Fehlerhandler für die Verarbeitung von HTTP-Fehlern. Beispiel:

![Standardfehlermeldung](assets/error-message-standard.png)

Um auf Fehler zu reagieren, stellt AEM unter `/libs/sling/servlet/errorhandler` ein `404.jsp`-Skript bereit.

>[!TIP]
>
>Da AEM auf Apache Sling basiert, sind weitere Informationen [in der Apache-Dokumentation zur Fehlerverarbeitung verfügbar.](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html)

>[!NOTE]
>
>In Autoreninstanzen ist [CQ WCM Debug Filter](/help/implementing/deploying/configuring-osgi.md) standardmäßig aktiviert. Das Ergebnis ist immer der Antwortcode 200. Der standardmäßige Fehler-Handler schreibt als Reaktion die vollständige Stacktrace in die Antwort.
>
>In Veröffentlichungsinstanzen ist CQ WCM Debug Filter **immer** deaktiviert (selbst wenn er als aktiviert konfiguriert ist).

## Anpassen der vom Fehler-Handler {#how-to-customize-pages-shown-by-the-error-handler} angezeigten Seiten

Sie können Ihre eigenen Skripte erstellen, um die Seiten anzupassen, die der Fehler-Handler anzeigt, wenn ein Fehler auftritt. Dazu verwenden Sie den standardmäßigen Überlagerungsmechanismus [AEM](/help/implementing/developing/introduction/overlays.md), damit Ihre benutzerdefinierten Seiten unter `/apps` erstellt werden und die Standardseiten unter `/libs` überlagert werden.

1. Kopieren Sie im Repository das/die Standardskript(e):

   * von `/libs/sling/servlet/errorhandler/`
   * in `/apps/sling/servlet/errorhandler/`

   Der Zielpfad ist nicht standardmäßig vorhanden. Daher müssen Sie ihn zum ersten Mal erstellen.

1. Navigieren Sie zu `/apps/sling/servlet/errorhandler`. Hier können Sie entweder:

   * das entsprechende vorhandene Skript bearbeiten, um die benötigten Informationen anzugeben. Oder
   * ein neues Skript für den erforderlichen Code erstellen und bearbeiten.

1. Speichern Sie die Änderungen und testen Sie sie.

>[!CAUTION]
>
>Das Skript `404.jsp` wurde speziell für AEM Authentifizierung entwickelt. insbesondere die Möglichkeit der Systemanmeldung im Fall dieser Fehler.
>
>Daher sollte der Austausch dieses Skripts mit großer Sorgfalt erfolgen.

### Anpassung der Reaktion auf HTTP 500-Fehler {#customizing-the-response-to-http-errors}

Der HTTP [500 Interner Serverfehler](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) gibt einen serverseitigen Fehler an, z. B. wenn der Server auf eine unerwartete Bedingung stößt, die die Erfüllung der Anforderung verhinderte.

Wenn die Verarbeitung von Anforderungen eine Ausnahme ergibt, wird das Apache Sling-Framework (auf dem AEM basiert) wie folgt ausgeführt:

* Protokolliert die Ausnahme
* Und gibt im Hauptteil der Antwort zurück:
   * HTTP-Antwortcode 500
   * Ausnahme-Stapelablaufverfolgung

Indem Sie [die Seiten anpassen, die der Fehler-Handler zeigt](#how-to-customize-pages-shown-by-the-error-handler), können Sie ein `500.jsp`-Skript erstellen. Sie wird jedoch nur verwendet, wenn `HttpServletResponse.sendError(500)` explizit ausgeführt wird. d. h. von einem Ausnahmenfänger.

Andernfalls wird der Antwortcode auf gesetzt, aber das Skript `500.jsp`500.  wird nicht ausgeführt.

Um 500-Fehler zu verarbeiten, muss der Dateiname des Fehler-Handler-Skripts identisch mit der Ausnahmeklasse (oder der übergeordneten Klasse) sein. Um alle derartigen Ausnahmen zu bearbeiten, können Sie ein Skript `/apps/sling/servlet/errorhandler/Throwable.jsp` oder `/apps/sling/servlet/errorhandler/Exception.jsp` erstellen.

>[!CAUTION]
>
>In Autoreninstanzen ist [CQ WCM Debug Filter](/help/implementing/deploying/configuring-osgi.md) standardmäßig aktiviert. Das Ergebnis ist immer der Antwortcode 200. Der standardmäßige Fehler-Handler schreibt als Reaktion die vollständige Stacktrace in die Antwort.
>
>Für eine individuelle Fehlerverarbeitung sind Antworten mit Code 500 erforderlich. Der [CQ WCM Debug-Filter muss also deaktiviert sein.](/help/implementing/deploying/configuring-osgi.md) Dadurch wird sichergestellt, dass der Antwortcode 500 zurückgegeben wird, was wiederum den richtigen Sling-Fehler-Handler auslöst.
>
>In Veröffentlichungsinstanzen ist CQ WCM Debug Filter **immer** deaktiviert (selbst wenn er als aktiviert konfiguriert ist).
