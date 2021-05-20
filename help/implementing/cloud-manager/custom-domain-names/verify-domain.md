---
title: Überprüfen der Domain
description: Überprüfen der Domain
source-git-commit: d2a98cf340dc755407250a9a9649addb75ad87d2
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 100%

---


# Überprüfen der Domain {#verify-domain-name}

Ein DNS-TXT-Datensatz autorisiert das Hosting einer Domain durch einen CDN-Service. Der Kunde muss einen DNS-TXT-Datensatz in der Zone erstellen, die Cloud Manager autorisiert, um den CDN-Service mit der benutzerdefinierten Domain bereitzustellen, und ihn dem Backend-Service zuordnen. Diese Zuordnung steht vollständig unter der Kontrolle des Kunden und autorisiert Cloud Manager ausdrücklich, Inhalte aus dem Service für eine Domain bereitzustellen. Diese Autorisierung kann erteilt und entzogen werden. Der TXT-Datensatz ist spezifisch für die Domain und die Cloud Manager-Umgebung.

1. Melden Sie sich bei Ihrem Domain-Host an und wechseln Sie zum Abschnitt mit den DNS-Datensätzen.
1. Kopieren Sie den TXT-Eintrag und fügen Sie ihn so, wie er angezeigt wird, in die DNS-Zone ein. Wenn Sie einen Namen für Ihren Eintrag benötigen, verwenden Sie `@`.

>[!NOTE]
>Verschiedene [DNS-Lookup-Tools](https://www.ultratools.com/tools/dnsLookup) wie Google DoH können verwendet werden, um TXT-Datensatzeinträge zu suchen und zu erkennen, ob der TXT-Datensatz fehlt oder fehlerhaft ist.
