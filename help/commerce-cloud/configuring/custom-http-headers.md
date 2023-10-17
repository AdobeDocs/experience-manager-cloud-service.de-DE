---
title: Anwenderdefinierte HTTP-Kopfzeilen
description: Erfahren Sie, wie Sie benutzerdefinierte HTTP-Header konfigurieren, die zusammen mit den bereits von CIF gesendeten an die Commerce-Engine gesendet werden.
exl-id: 2cef5d4b-45f6-4d72-a24b-67ca53d9057d
source-git-commit: ba0c1e13f311f48ac138f2c3ca582835a4a83bf6
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 91%

---

# Anwenderdefinierte HTTP-Kopfzeilen {#custom-http-headers}

## Übersicht {#overview}

Um mehr Kontrolle über ihr Backend zu erhalten, können Autoren anwenderdefinierte HTTP-Kopfzeilen konfigurieren, die zusammen mit den bereits von CIF gesendeten Kopfzeilen an die Commerce-Engine gesendet werden. Häufige Anwendungsfälle sind Multi-Store-Setups, in denen Sie HTTP-Kopfzeilen verwenden können, um die Antwort des Commerce-Backends zu steuern.

>[!NOTE]
>
>Entwickler können anwenderdefinierte HTTP-Kopfzeilen jederzeit mithilfe der GraphQL-Client-Konfiguration konfigurieren.
>

## Konfiguration {#configuration}

Um die benutzerdefinierten HTTP-Kopfzeilen zu konfigurieren, müssen Sie sie zuerst definieren. Die anwenderdefinierten HTTP-Kopfzeilen müssen zuerst definiert werden, indem sie mithilfe einer OSGi-Konfiguration zur Service-Konfiguration `com.adobe.cq.cif.http.internal.HttpHeadersConfigProviderImpl` hinzugefügt werden.

Sie können die Werte der HTTP-Kopfzeilen auf der Seite „Cloud Service-Konfiguration“ für Ihr Projekt konfigurieren:

1. Navigieren Sie zur Seite „Cloud Service-Konfiguration“ unter „Tools“ > „Cloud Services“ > „CIF-Konfiguration“.
1. Öffnen Sie eine vorhandene Konfiguration oder erstellen Sie eine neue.
1. Wechseln Sie zur Registerkarte „Erweitert“ und suchen Sie das Multi-Feld „Anwenderdefinierte HTTP-Kopfzeilen“. Sie können die zuvor definierten Kopfzeilen auswählen und ihnen Werte zuweisen.

Die Komponenten, die die obige Cloud Service-Konfiguration verwenden, senden diese HTTP-Kopfzeilen mit jeder GraphQL-Anfrage.

## Einschränkungen {#restrictions}

Der Service ermöglicht zwar die Definition von Kopfzeilennamen, einschließlich der standardmäßigen Namen, aber sie stehen nicht zur Konfiguration zur Verfügung. Mit anderen Worten: Sie können die standardmäßigen HTTP-Kopfzeilen nicht mit dieser Funktion überschreiben. Eine Liste mit eingeschränkten Kopfzeilennamen finden Sie [hier](https://developer.mozilla.org/de-DE/docs/Web/HTTP/Headers). Darüber hinaus gibt es zwei weitere Kopfzeilen, die nicht verwendet werden können:

* „Store“ – wird von CIF verwendet, um den Adobe Commerce-Store zu identifizieren.
* „Preview-Version“ – wird von CIF zum Abrufen von Staging-Produkten verwendet.
