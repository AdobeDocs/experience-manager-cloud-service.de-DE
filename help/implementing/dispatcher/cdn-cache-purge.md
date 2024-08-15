---
title: Bereinigen des CDN-Caches
description: Erfahren Sie, wie Sie zwischengespeicherte Objekte aus dem Adobe-CDN-Cache entfernen können, indem Sie das Bereinigungs-API-Token konfigurieren, das dann in API-Aufrufen verwendet werden kann.
feature: CDN Cache
exl-id: 4d091677-b817-4aeb-b131-7a5407ace3e0
role: Admin
source-git-commit: 85cef99dc7a8d762d12fd6e1c9bc2aeb3f8c1312
workflow-type: tm+mt
source-wordcount: '433'
ht-degree: 90%

---

# Bereinigen des CDN-Caches {#cdn-purge-cache}

Durch die Bereinigung wird ein Objekt aus dem Adobe-CDN-Cache entfernt, was dazu führt, dass zukünftige Anfragen als Cache-Fehler an die Quelle weitergeleitet werden, anstatt aus dem Cache bereitgestellt zu werden.
Mit AEM as a Cloud Service können Sie ein Bereinigungs-API-Token konfigurieren, das dann in Aufrufen der Bereinigungs-API verwendet werden kann. Lesen Sie [Konfigurieren von CDN-Anmeldeinformationen und Authentifizierung](/help/implementing/dispatcher/cdn-credentials-authentication.md#purge-API-token) , um zu erfahren, wie Sie dieses Token mithilfe der Cloud Manager Config Pipeline Authentication-Direktiven konfigurieren.

Es werden drei Bereinigungsvarianten unterstützt:

* [Einzelne URL-Bereinigung](#single-purge): Es wird jeweils nur eine Ressource bereinigt.
* [Bereinigung durch Ersatzschlüssel](#surrogate-key-purge): Es werden mehrere Ressourcen gleichzeitig bereinigt.
* [Vollständige Bereinigung](#full-purge): Es werden alle Ressourcen bereinigt.

Alle Bereinigungsvarianten vereint Folgendes:

* Als HTTP-Methode muss `PURGE` festgelegt sein.
* Die URL kann eine beliebige Domain sein, die mit dem AEM-Dienst verknüpft ist, für den die Bereinigungsanfrage bestimmt ist.
* Der `X-AEM-Purge-Key` muss in einem HTTP-Header angegeben werden.

>[!CAUTION]
>Die Bereinigung des CDN-Caches, insbesondere mit Hardflag, erhöht den Traffic an der Quelle und kann zu einem Ausfall führen, sofern die Ausführung nicht ordnungsgemäß erfolgt.

## Einzelne URL-Bereinigung {#single-purge}

Sie können jeweils eine einzelne Ressource wie folgt bereinigen:

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com/resource-path" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H 'X-AEM-Purge: soft'
```

Wie im obigen Beispiel gezeigt, können Sie **optional** festlegen, ob das CDN die standardmäßige **endgültige** (harte) Bereinigung oder eine **vorläufige** (weiche) Bereinigung der zwischengespeicherten Objekte durchführen soll.

Bei der standardmäßigen endgültigen Bereinigung wird der Inhalt sofort für neue Anfragen unzugänglich; er muss dann von der Quelle abgerufen werden. Bei der weichen Bereinigung werden Inhalte als veraltet markiert, sie werden jedoch trotzdem Clients bereitgestellt, sodass sie nicht warten müssen, bis der Inhalt von der Quelle abgerufen wird.

## Bereinigung durch Ersatzschlüssel {#surrogate-key-purge}

Ersatzschlüssel sind eindeutige Kennungen, mit denen Sie einen Satz von Inhalten bereinigen können. Sie werden auf Inhalte angewendet, indem der Antwort ein `Surrogate-Key`-Header hinzugefügt wird. Ein oder mehrere Ersatzschlüssel können in einem Bereinigungs-API-Aufruf referenziert werden.

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "Surrogate-Key: my-surrogate-key"
-H "X-AEM-Purge: soft" #optional
```

Die `Surrogate-Key`(s) werden durch Leerzeichen voneinander getrennt. Ähnlich wie bei der einzelnen URL-Bereinigung können Sie entweder eine endgültige oder vorläufige Bereinigung konfigurieren.

## Vollständige Bereinigung {#full-purge}

Sie können alle zwischengespeicherten Ressourcen wie folgt vollständig bereinigen:

```
curl
-X PURGE "https://publish-p1234-e5467.adobeaemcloud.com" \
-H 'X-AEM-Purge-Key: <my_purge_key>' \
-H "X-AEM-Purge: all"
```

Beachten Sie, dass der `X-AEM-Purge`-Header den Wert „all“ enthalten muss.

## Interaktionen mit der Apache-/Dispatcher-Ebene {#apache-layer}

Wie unter [Inhaltsbereitstellungsfluss](/help/implementing/dispatcher/overview.md) beschrieben, ruft das CDN Inhalte aus der Apache-/Dispatcher-Ebene ab, wenn der Cache abgelaufen ist. Dies bedeutet, dass Sie vor dem Bereinigen einer Ressource im CDN sicherstellen sollten, dass auch eine neue Version des Inhalts beim Dispatcher verfügbar ist. Weitere Informationen finden Sie unter [Dispatcher-Cache-Invalidierung](/help/implementing/dispatcher/caching.md#disp).
