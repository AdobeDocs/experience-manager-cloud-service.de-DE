---
title: Hinzufügen eines TXT-Datensatzes
description: Hinzufügen eines benutzerdefinierten Domain-Namens
exl-id: d441de29-af41-4d3e-9155-531af9702841
source-git-commit: f7688559a791281d0e157dd1d48a5f63568914f5
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 84%

---

# Hinzufügen eines TXT-Datensatzes {#adding-txt}

Ein DNS-TXT-Datensatz autorisiert das Hosting einer Domain durch einen CDN-Service. Der Kunde muss einen DNS-TXT-Datensatz in der Zone erstellen, die Cloud Manager autorisiert, um den CDN-Service mit der benutzerdefinierten Domain bereitzustellen, und ihn dem Backend-Service zuordnen. Diese Zuordnung steht vollständig unter der Kontrolle des Kunden und autorisiert Cloud Manager ausdrücklich, Inhalte aus dem Service für eine Domain bereitzustellen. Diese Autorisierung kann erteilt und entzogen werden.

Führen Sie die folgenden Schritte aus, bevor Sie einen TXT-Datensatz erstellen:

* Sie haben die Möglichkeit, die DNS-Datensätze für die Domain Ihres Unternehmens zu ändern oder sich an eine entsprechende Person zu wenden, die dies kann.
* Identifizieren Sie Ihren Domain-Host oder Ihre Registrierungsstelle, falls Sie sie noch nicht kennen.

Wenn Sie die Domain-Überprüfung starten, erhalten Sie von Cloud Manager den Namen und den TXT-Wert, die zur Überprüfung verwendet werden sollen. Fügen Sie dem DNS-Server Ihrer Domain einen TXT-Datensatz mit dem angegebenen Namen und Wert hinzu.

1. Melden Sie sich bei Ihrem Domain-Host an und wechseln Sie zum Abschnitt mit den DNS-Datensätzen.
1. Fügen Sie `_aemverification.[yourdomainname]` als Namen und den TXT-Wert genau so hinzu, wie er angezeigt wird.
Beispiele finden Sie in der nachfolgenden Tabelle.

| Domain | Name | TXT-Wert |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Kopieren Sie den gesamten in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dies ist spezifisch für die Domäne und die Umgebung. Beispiel:<br>*adobe-aem-validation=<br>example.com/[program]/[env]/.* |
| `www.example.com` | `_aemverification.www.example.com` | Kopieren Sie den gesamten in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dies ist spezifisch für die Domäne und die Umgebung. Beispiel:<br>*adobe-aem-validation=<br>www.example.com/[program]/[env]/.* |

Abschließend können Sie das Ergebnis überprüfen, indem Sie Folgendes ausführen: `dig _aemverification.[yourdomainname] -t txt`.
Das erwartete Ergebnis sollte den in der Benutzeroberfläche von Cloud Manager bereitgestellten TXT-Wert anzeigen.

Wenn Ihre Domain beispielsweise `example.com` lautet, führen Sie Folgendes aus: `dig TXT _aemverification.example.com -t txt`.

>[!NOTE]
>Es gibt auch verschiedene [DNS-Lookup-Tools](https://www.ultratools.com/tools/dnsLookup). Google DoH kann verwendet werden, um TXT-Datensätze zu suchen und zu erkennen, ob der TXT-Datensatz fehlt oder fehlerhaft ist.
