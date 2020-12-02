---
title: Domäne überprüfen
description: Domäne überprüfen
translation-type: tm+mt
source-git-commit: d2a98cf340dc755407250a9a9649addb75ad87d2
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---


# Domäne {#verify-domain-name} überprüfen

Ein DNS-TXT-Datensatz autorisiert die Hosting einer Domäne in einem CDN-Dienst. Der Kunde muss einen DNS-TXT-Datensatz in der Zone erstellen, die Cloud Manager autorisiert, den CDN-Dienst mit der benutzerdefinierten Domäne bereitzustellen und ihn mit dem Backend-Dienst zu verknüpfen. Diese Verbindung steht vollständig unter der Kontrolle des Kunden und autorisiert Cloud Manager ausdrücklich, Inhalte aus dem Dienst für eine Domäne bereitzustellen. Diese Genehmigung kann erteilt und entzogen werden. Der TXT-Datensatz ist spezifisch für die Domäne und die Cloud Manager-Umgebung.

1. Melden Sie sich bei Ihrem Domänenhost an und besuchen Sie den Abschnitt DNS-Datensätze.
1. Kopieren Sie den TXT-Eintrag in Ihre DNS-Zone, wo sich Ihre benutzerdefinierte Domäne befindet, genau wie er angezeigt wird. Wenn Sie einen &quot;Namen&quot; für Ihren Eintrag benötigen, geben Sie ihn `@`.

>[!NOTE]
>Verschiedene DNS-Nachschlagewerkzeuge wie [DNS-Nachschlagewerkzeug](https://www.ultratools.com/tools/dnsLookup), Google DoH können verwendet werden, um TXT-Datensatzeinträge nachzuschlagen und herauszufinden, ob der TXT-Datensatz fehlt oder fehlerhaft ist.
