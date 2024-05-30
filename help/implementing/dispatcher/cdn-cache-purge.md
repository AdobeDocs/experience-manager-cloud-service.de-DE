---
title: Löschen des CDN-Cache
description: Erfahren Sie, wie Sie zwischengespeicherte Objekte aus dem Adobe CDN-Cache entfernen können, indem Sie das Bereinigungs-API-Token konfigurieren, das dann in API-Aufrufen verwendet werden kann.
feature: CDN Cache
source-git-commit: a10faaecf8f6dcaf53e7c72504b927125b32c0d4
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 1%

---

# Löschen des CDN-Cache {#cdn-purge-cache}

>[!NOTE]
>Diese Funktion ist noch nicht allgemein verfügbar.  Um dem Programm für frühe Anwender beizutreten, senden Sie eine E-Mail `aemcs-cdn-config-adopter@adobe.com`.

Durch die Bereinigung wird ein Objekt aus dem Adobe-CDN-Cache entfernt, was dazu führt, dass zukünftige Anforderungen als Cache-Versäumnis an die Quelle weitergeleitet werden, anstatt aus dem Cache bereitgestellt zu werden.
AEM as a Cloud Service können Sie ein Bereinigungs-API-Token konfigurieren, das dann in API-Aufrufen verwendet werden kann. Lesen Sie die [Artikel &quot;Konfigurieren von CDN-Anmeldeinformationen und Authentifizierung&quot;](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) , um zu erfahren, wie Sie dieses Token mithilfe der Authentifizierungsrichtlinien der Cloud Manager-Konfigurationspipelineauthentifizierung konfigurieren.

Es werden drei Bereinigungsvarianten unterstützt:

* [Einzelne URL-Bereinigung](#single-purge) - jeweils nur eine Ressource bereinigen.
* [Bereinigen durch Ersatzschlüssel](#surrogate-key-purge) - mehrere Ressourcen gleichzeitig bereinigen.
* [Vollständige Bereinigung](#full-purge) - Bereinigen Sie alle Ressourcen.

Alle Bereinigungsvarianten weisen Folgendes auf:

* Die HTTP-Methode muss auf `PURGE`.
* Die URL kann eine beliebige Domäne sein, die mit dem AEM-Dienst verknüpft ist, für den die Bereinigungsanforderung bestimmt ist.
* Die `X-AEM-Purge-Key` muss in einem HTTP-Header angegeben werden.

>[!CAUTION]
>Das Löschen des CDN-Cache, insbesondere mit der Hard Flag, erhöht den Traffic an der Quelle und kann zu einem Ausfall führen, wenn er nicht ordnungsgemäß ausgeführt wird.

## Einzelne URL-Bereinigung {#single-purge}

Sie können eine Ressource gleichzeitig wie folgt bereinigen:

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com/resource-path" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H 'X-AEM-Purge: soft'
```

Wie im obigen Beispiel gezeigt, können Sie **optional** angeben, ob das CDN eine **hard** Bereinigung (Standard) oder **soft** Bereinigen Sie die zwischengespeicherten Objekte.

Die standardmäßige Hard-Bereinigung macht den Inhalt für neue Anforderungen sofort unzugänglich, bis der Inhalt aus der Quelle abgerufen wird. Bei der Soft-Bereinigung werden Inhalte als veraltet markiert, sie werden jedoch trotzdem Clients bereitgestellt, sodass sie nicht warten müssen, bis der Inhalt von der Quelle abgerufen wird.

## Bereinigung der Ersatzschlüssel {#surrogate-key-purge}

Ersatzschlüssel sind eindeutige Kennungen, mit denen Sie einen Satz von Inhalten bereinigen. Sie werden auf Inhalte angewendet, indem eine `Surrogate-Key` -Kopfzeile zur Antwort. Ein oder mehrere Ersatzschlüssel können in einem Bereinigungs-API-Aufruf referenziert werden.

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "Surrogate-Key: my-surrogate-key"
-H "X-AEM-Purge: soft" #optional
```

Die `Surrogate-Key`(s) durch Leerzeichen getrennt sind. Ähnlich wie bei der einzelnen URL-Bereinigung können Sie entweder eine Hard- oder eine Soft-Bereinigung konfigurieren.

## Vollständige Bereinigung {#full-purge}

Sie können alle zwischengespeicherten Ressourcen wie folgt vollständig bereinigen:

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "X-AEM-Purge: all"
```

Beachten Sie, dass `X-AEM-Purge` -Kopfzeile muss den Wert &quot;all&quot;enthalten.

## Interaktionen mit der Apache-/Dispatcher-Ebene {#apache-layer}

Wie im Abschnitt [Artikel zum Ablauf der Inhaltsbereitstellung](/help/implementing/dispatcher/overview.md), ruft das CDN Inhalte aus der Apache-/Dispatcher-Ebene ab, wenn der Cache abgelaufen ist. Dies bedeutet, dass Sie vor dem Bereinigen einer Ressource im CDN sicherstellen sollten, dass auch eine neue Version des Inhalts beim Dispatcher verfügbar ist. Weitere Informationen finden Sie unter [Dispatcher-Cache-Invalidierung](/help/implementing/dispatcher/caching.md#disp).
