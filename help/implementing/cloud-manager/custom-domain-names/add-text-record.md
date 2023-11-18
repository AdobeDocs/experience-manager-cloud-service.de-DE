---
title: Hinzufügen eines TXT-Eintrags
description: Erfahren Sie, wie Sie einen TXT-Eintrag hinzufügen, um einen benutzerdefinierten Domain-Namen in Cloud Manager hinzuzufügen.
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: 6bb7b2d056d501d83cf227adb239f7f40f87d0ce
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 91%

---

# Hinzufügen eines TXT-Eintrags {#adding-txt}

Ein DNS-TXT-Eintrag autorisiert das Hosting einer Domain durch einen CDN-Service. Der Kunde muss einen DNS-TXT-Eintrag in der Zone erstellen, die Cloud Manager autorisiert, den CDN-Service mit der benutzerdefinierten Domain bereitzustellen, und ihn dem Backend-Service zuzuordnen. Diese Zuordnung steht vollständig unter der Kontrolle des Kunden und autorisiert Cloud Manager ausdrücklich, Inhalte aus dem Service für eine Domain bereitzustellen. Diese Genehmigung kann erteilt und entzogen werden. Der TXT-Eintrag ist spezifisch für die Domain und die Cloud Manager-Umgebung.

Sie müssen diese Anforderungen erfüllen, bevor Sie einen TXT-Eintrag hinzufügen.

* Sie müssen in der Lage sein, die DNS-Einträge für die Domäne Ihres Unternehmens zu bearbeiten, oder sich an die entsprechende Person wenden können.
* Sie müssen Ihren Domain-Host oder Ihre Registrierungsstelle ermitteln, falls Sie sie noch nicht kennen.

Wenn Sie die Domain-Überprüfung starten, erhalten Sie von Cloud Manager den Namen und den TXT-Wert, die zur Überprüfung verwendet werden sollen. Fügen Sie dem DNS-Server Ihrer Domain einen TXT-Eintrag mit dem angegebenen Namen und Wert hinzu.

1. Melden Sie sich bei Ihrem Domain-Host an und wechseln Sie zum Abschnitt mit den DNS-Einträgen.
1. Fügen Sie `_aemverification.[yourdomainname]` als **Namen** hinzu und fügen Sie den TXT-Wert genau so hinzu, wie er angezeigt wird.

Siehe die Beispiele in dieser Tabelle.

| Domain | Name | TXT-Wert |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

Abschließend können Sie das Ergebnis überprüfen, indem Sie den folgenden Befehl ausführen.

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
>Es gibt mehrere [DNS-Suchwerkzeuge](https://www.ultratools.com/tools/dnsLookup) verfügbar. Google DoH kann verwendet werden, um TXT-Einträge zu suchen und zu erkennen, ob der TXT-Eintrag fehlt oder fehlerhaft ist.
