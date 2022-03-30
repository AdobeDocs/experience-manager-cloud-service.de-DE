---
title: Hinzufügen eines TXT-Datensatzes
description: Erfahren Sie, wie Sie einen TXT-Eintrag hinzufügen, um einen benutzerdefinierten Domänennamen in Cloud Manager hinzuzufügen.
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: c80b7288b86ac62da17d5a83ec96cb882e36f687
workflow-type: tm+mt
source-wordcount: '319'
ht-degree: 29%

---

# Hinzufügen eines TXT-Datensatzes {#adding-txt}

Ein DNS-TXT-Eintrag autorisiert eine Domäne, in einem CDN-Dienst gehostet zu werden. Sie müssen einen DNS-TXT-Eintrag in der Zone erstellen, die Cloud Manager berechtigt, den CDN-Dienst mit der benutzerdefinierten Domäne bereitzustellen und ihn mit dem Backend-Service zu verknüpfen. Diese Zuordnung unterliegt vollständig Ihrer Kontrolle und autorisiert Cloud Manager, Inhalte vom Dienst für eine Domäne bereitzustellen. Diese Genehmigung kann erteilt und entzogen werden.

Sie müssen diese Anforderungen erfüllen, bevor Sie einen TXT-Eintrag hinzufügen.

* Sie müssen die Möglichkeit haben, die DNS-Einträge für die Domäne Ihres Unternehmens zu ändern, oder sich an die entsprechende Person wenden, die dies kann.
* Sie müssen Ihren Domänenhost oder Ihre Registrierungsstelle identifizieren, wenn Sie ihn nicht bereits kennen.

Wenn Sie die Domain-Überprüfung starten, erhalten Sie von Cloud Manager den Namen und den TXT-Wert, die zur Überprüfung verwendet werden sollen. Fügen Sie dem DNS-Server Ihrer Domäne einen TXT-Eintrag mit dem angegebenen Namen und Wert hinzu.

1. Melden Sie sich bei Ihrem Domain-Host an und suchen Sie den Abschnitt DNS-Einträge .
1. Hinzufügen `_aemverification.[yourdomainname]` als **Name** und fügen Sie den TXT-Wert genau so hinzu, wie er angezeigt wird.

Siehe Beispiele in dieser Tabelle.

| Domain | Name | TXT-Wert |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

Wenn Sie fertig sind, können Sie das Ergebnis überprüfen, indem Sie den folgenden Befehl ausführen

```shell
dig _aemverification.[yourdomainname] -t txt
```

Das erwartete Ergebnis sollte den in der Benutzeroberfläche von Cloud Manager bereitgestellten TXT-Wert anzeigen.

Wenn Ihre Domain beispielsweise `example.com` lautet, führen Sie Folgendes aus:

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Es gibt eine Reihe von [DNS-Suchwerkzeuge](https://www.ultratools.com/tools/dnsLookup) verfügbar. Google DoH kann verwendet werden, um TXT-Eintragungen zu suchen und zu erkennen, ob der TXT-Eintrag fehlt oder fehlerhaft ist.
