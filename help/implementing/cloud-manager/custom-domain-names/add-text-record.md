---
title: Hinzufügen eines TXT-Datensatzes
description: Hinzufügen eines benutzerdefinierten Domänennamens
translation-type: tm+mt
source-git-commit: 8d97bedc8c473c13e3378849741104b2c85492e2
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---


# Hinzufügen eines TXT-Eintrags {#adding-txt}

Ein DNS-TXT-Datensatz autorisiert die Hosting einer Domäne in einem CDN-Dienst. Der Kunde muss einen DNS-TXT-Datensatz in der Zone erstellen, die Cloud Manager autorisiert, den CDN-Dienst mit der benutzerdefinierten Domäne bereitzustellen und ihn mit dem Backend-Dienst zu verknüpfen. Diese Verbindung steht vollständig unter der Kontrolle des Kunden und autorisiert Cloud Manager ausdrücklich, Inhalte aus dem Dienst für eine Domäne bereitzustellen. Diese Genehmigung kann erteilt und entzogen werden.

Führen Sie die folgenden Schritte aus, bevor Sie einen TXT-Datensatz erstellen:

* Sie haben die Möglichkeit, die DNS-Einträge für die Domäne Ihres Unternehmens zu ändern, oder wenden Sie sich an die entsprechende Person, die dies kann.
* Identifizieren Sie Ihren Domänenhost oder Ihre Registrierungsstelle, wenn Sie ihn noch nicht kennen.

Wenn Sie die Domänenüberprüfung starten, gibt Ihnen Cloud Manager den Namen und den TXT-Wert, der zur Überprüfung verwendet werden soll. hinzufügen einen TXT-Datensatz mit dem angegebenen Namen und Wert an den DNS-Server Ihrer Domäne.

1. Melden Sie sich bei Ihrem Domänenhost an und besuchen Sie den Abschnitt DNS-Datensätze.
1. hinzufügen `_aemverification.[yourdomainname]` als Name und fügen Sie den TXT-Wert genau so hinzu, wie er angezeigt wird.
Siehe Beispiele in der unten stehenden Tabelle.

| Domäne | Name | TXT-Wert |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Wird in der Benutzeroberfläche von Cloud Manager angezeigt und ist spezifisch für die Domäne und die Cloud Manager-Umgebung |
| `test.example.com` | `_aemverification.test.example.com` | Wird in der Benutzeroberfläche von Cloud Manager angezeigt und ist spezifisch für die Domäne und die Cloud Manager-Umgebung |

Nach Abschluss können Sie das Ergebnis überprüfen, indem Sie Folgendes ausführen: `dig _aemverification.[yourdomainname] -t txt`.
Das erwartete Ergebnis sollte den in der Benutzeroberfläche von Cloud Manager bereitgestellten TXT-Wert anzeigen.

Wenn Ihre Domäne beispielsweise `example.com` lautet, führen Sie Folgendes aus: `dig TXT _aemverification.example.com -t txt`.

>[!NOTE]
>Es gibt auch verschiedene [DNS Lookup Tools](https://www.ultratools.com/tools/dnsLookup), Google DoH kann verwendet werden, um TXT-Einträge nachzuschlagen und zu erkennen, ob der TXT-Datensatz fehlt oder fehlerhaft ist.

