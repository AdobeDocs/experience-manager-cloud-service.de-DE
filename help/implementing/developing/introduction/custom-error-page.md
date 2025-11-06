---
title: benutzerdefinierte Fehlerseiten
description: AEM enthält einen Standard-Fehler-Handler für die Verarbeitung von HTTP-Fehlern, der angepasst werden kann.
exl-id: b74c65d1-8ef5-4ad4-8255-8187f3b1d84c
feature: Developing
role: Admin, Developer
source-git-commit: ff06dbd86c11ff5ab56b3db85d70016ad6e9b981
workflow-type: tm+mt
source-wordcount: '583'
ht-degree: 100%

---

# Anpassen von Fehlerseiten {#customizing-error-pages}

AEM enthält einen Standard-Fehler-Handler für die Verarbeitung von HTTP-Fehlern. Beispielsweise wird Folgendes gezeigt:

![Standardfehlermeldung](assets/error-message-standard.png)

Um auf Fehler zu reagieren, stellt AEM unter `/libs/sling/servlet/errorhandler` ein `404.jsp`-Skript bereit.

>[!TIP]
>
>Da AEM auf Apache Sling basiert, sind weitere Informationen [in der Apache-Dokumentation zur Fehlerbehandlung](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html) verfügbar.

>[!NOTE]
>
>Auf einer Autoreninstanz ist der [CQ WCM Debug Filter](/help/implementing/deploying/configuring-osgi.md) standardmäßig aktiviert. Das Ergebnis ist immer der Antwort-Code 200. Der standardmäßige Fehler-Handler antwortet, indem er den vollständigen Stacktrace in die Antwort schreibt.
>
>In Veröffentlichungsinstanzen ist CQ WCM Debug Filter **immer** deaktiviert (selbst wenn er als aktiviert konfiguriert ist).

>[!NOTE]
>
>Weitere Informationen zur Fehlerbehandlung mit dem Dispatcher finden Sie unter [Konfigurieren von CDN-Fehlerseiten](/help/implementing/dispatcher/cdn-error-pages.md).

## Anpassen der vom Fehler-Handler angezeigten Seiten {#how-to-customize-pages-shown-by-the-error-handler}

Sie können Ihre eigenen Skripte erstellen, um die Seiten anzupassen, die der Fehler-Handler anzeigen soll, wenn ein Fehler auftritt. Dazu verwenden Sie den [standardmäßigen Überlagerungsmechanismus von AEM](/help/implementing/developing/introduction/overlays.md), damit Ihre benutzerdefinierten Seiten unter `/apps` erstellt werden und die Standardseiten unter `/libs` überlagert werden.

1. Kopieren Sie im Repository das/die Standardskript(e):

   * von `/libs/sling/servlet/errorhandler/`
   * nach `/apps/sling/servlet/errorhandler/`

   Da der Zielpfad standardmäßig nicht vorhanden ist, müssen Sie ihn erstellen, wenn Sie diesen Vorgang zum ersten Mal durchführen.

1. Navigieren Sie zu `/apps/sling/servlet/errorhandler`. Hier können Sie entweder:

   * das entsprechende vorhandene Skript bearbeiten, um die benötigten Informationen anzugeben. Oder
   * ein neues Skript für den erforderlichen Code erstellen und bearbeiten.

1. Speichern Sie die Änderungen und testen Sie sie.

>[!CAUTION]
>
>Das `404.jsp`-Skript wurde speziell für die AEM-Authentifizierung entwickelt, insbesondere um die Systemanmeldung bei Auftreten dieser Fehler zu ermöglichen.
>
>Daher sollten Sie dieses Skript nur mit größter Vorsicht ersetzen.

### Anpassung der Reaktion auf HTTP 500-Fehler {#customizing-the-response-to-http-errors}

[HTTP 500 – interner Server-Fehler](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html) zeigt einen Server-seitigen Fehler an, z. B. wenn der Server auf eine unerwartete Bedingung gestoßen ist, die ihn daran gehindert hat, die Anfrage zu erfüllen.

Wenn die Bearbeitung einer Anfrage zu einem Ausnahmefehler führt, führt das Apache Sling-Framework (auf dem AEM basiert) folgende Schritte durch:

* Protokolliert den Ausnahmefehler
* Gibt Folgendes im Antworttext zurück:
   * den HTTP-Antwort-Code 500
   * den Stacktrace des Ausnahmefehlers

Indem Sie [die Seiten anpassen, die der Fehler-Handler zeigt](#how-to-customize-pages-shown-by-the-error-handler), können Sie ein `500.jsp`-Skript erstellen. Es wird jedoch nur verwendet, wenn `HttpServletResponse.sendError(500)` explizit ausgeführt wird, d. h. von einem Abfangalgorithmus für Ausnahmen.

Andernfalls wird der Antwort-Code auf „500“ gesetzt, aber das `500.jsp`-Skript wird nicht ausgeführt.

Um 500-Fehler zu verarbeiten, muss der Dateiname des Fehler-Handler-Skripts identisch mit der Ausnahmeklasse (oder der übergeordneten Klasse) sein. Um alle derartigen Ausnahmen zu bearbeiten, können Sie ein `/apps/sling/servlet/errorhandler/Throwable.jsp`- oder `/apps/sling/servlet/errorhandler/Exception.jsp`-Skript erstellen.

>[!NOTE]
>
>In AEM as a Cloud Service gibt das CDN eine allgemeine Fehlerseite aus, wenn vom Backend ein 5XX-Fehler empfangen wird. Damit die tatsächliche Antwort des Backends weitergeleitet werden kann, müssen Sie die folgende Kopfzeile zur Antwort hinzufügen: `x-aem-error-pass: true`.
>Dies funktioniert nur bei Antworten aus AEM oder der Apache-/Dispatcher-Ebene. Bei anderen unerwarteten Fehlern, die von Zwischeninfrastruktur-Ebenen kommen, wird weiterhin die allgemeine Fehlerseite angezeigt.

>[!CAUTION]
>
>Auf einer Autoreninstanz ist der [CQ WCM Debug Filter](/help/implementing/deploying/configuring-osgi.md) standardmäßig aktiviert. Das Ergebnis ist immer der Antwort-Code 200. Der standardmäßige Fehler-Handler schreibt daraufhin den vollständigen Stacktrace in die Antwort.
>
>Für eine individuelle Fehlerverarbeitung sind Antworten mit Code 500 erforderlich. Der [CQ WCM Debug-Filter muss also deaktiviert sein](/help/implementing/deploying/configuring-osgi.md). Dadurch wird sichergestellt, dass der Antwort-Code 500 zurückgegeben wird, was wiederum den richtigen Sling-Fehler-Handler auslöst.
>
>In Veröffentlichungsinstanzen ist CQ WCM Debug Filter **immer** deaktiviert (selbst wenn er als aktiviert konfiguriert ist).
