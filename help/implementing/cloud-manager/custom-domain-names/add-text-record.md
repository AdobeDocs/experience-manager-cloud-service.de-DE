---
title: Hinzufügen eines TXT-Eintrags
description: Erfahren Sie, wie Sie TXT-Eintrag hinzufügen, um zu überprüfen, ob Sie Eigentümer einer benutzerdefinierten Domäne für die Verwendung mit Cloud Manager sind.
exl-id: d441de29-af41-4d3e-9155-531af9702841
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 06e961febd7cb2ea1d8fca00cb3dee7f7ca893c9
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 32%

---


# Hinzufügen eines TXT-Eintrags {#adding-txt}

Erfahren Sie, wie Sie TXT-Eintrag hinzufügen, um zu überprüfen, ob Sie Eigentümer einer benutzerdefinierten Domäne für die Verwendung mit Cloud Manager sind.

## Was ist ein TXT-Eintrag? {#what-is}

Ein Textdatensatz (auch als TXT-Eintrag bezeichnet) ist ein Ressourcentyp im Domain Name System (DNS). Es bietet die Möglichkeit, beliebigen Text mit einem Hostnamen zu verknüpfen, z. B. für Menschen lesbare Informationen über einen Hostnamen wie Server- oder Netzwerkinformationen.

Cloud Manager verwendet einen bestimmten TXT-Eintrag, um zu autorisieren, dass eine Domäne in einem CDN-Dienst gehostet wird. Sie müssen einen DNS-TXT-Eintrag in der Zone erstellen, die Cloud Manager berechtigt, den CDN-Dienst mit der benutzerdefinierten Domäne bereitzustellen und ihn mit dem Backend-Dienst zu verknüpfen. Diese Zuordnung steht vollständig unter der Kontrolle des Kunden und autorisiert Cloud Manager ausdrücklich, Inhalte aus dem Service für eine Domain bereitzustellen. Diese Genehmigung kann erteilt und entzogen werden. Der TXT-Eintrag ist spezifisch für die Domäne und die Cloud Manager-Umgebung.

## Voraussetzungen {#requirements}

Sie müssen diese Anforderungen erfüllen, bevor Sie einen TXT-Eintrag hinzufügen.

* Sie müssen Ihren Domain-Host oder Ihre Registrierungsstelle ermitteln, falls Sie sie noch nicht kennen.
* Sie müssen in der Lage sein, die DNS-Einträge für die Domain Ihres Unternehmens zu ändern oder sich ansonsten an eine entsprechende Person zu wenden, die dies kann.
* Sie müssen zunächst einen benutzerdefinierten Domänennamen hinzufügen, wie im Dokument [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) beschrieben.

## Hinzufügen eines TXT-Eintrags zur Überprüfung {#verification}

Im Rahmen der Verifizierung eines benutzerdefinierten Domain-Namens, der mit Cloud Manager verwendet werden soll, wird ein TXT-Eintrag hinzugefügt.

1. Sie müssen zunächst einen benutzerdefinierten Domänennamen hinzufügen, wie im Dokument [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) beschrieben.

1. Auf der Registerkarte **Verifizierung** im Dialogfeld **Domänennamen hinzufügen** zeigt Cloud Manager den Namen und den TXT-Wert an, die zur Überprüfung verwendet werden sollen. Kopieren Sie diesen Wert.

   ![Verifizierung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

1. Melden Sie sich bei Ihrem Domain-Host an und suchen Sie den Abschnitt DNS-Einträge .

1. Fügen Sie `_aemverification.[yourdomainname]` als **Name** des Werts hinzu und fügen Sie den TXT-Wert genau so hinzu, wie er im Dialogfeld **Domänennamen hinzufügen** angezeigt wird.

   * Siehe die [Beispiele im folgenden Abschnitt.](#examples)

1. Speichern Sie den TXT-Eintrag auf Ihrem Domain-Host.

## Beispiele für TXT-Einträge {#examples}

| Domain | Name | TXT-Wert |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

## TXT-Eintrag überprüfen {#verify}

Wenn Sie fertig sind, können Sie das Ergebnis überprüfen, indem Sie den folgenden Befehl ausführen.

```shell
dig _aemverification.[yourdomainname] -t txt
```

Das erwartete Ergebnis sollte den TXT-Wert anzeigen, der auf der Registerkarte **Verifizierung** im Dialogfeld **Domänennamen hinzufügen** der Cloud Manager-Benutzeroberfläche bereitgestellt wird.

Wenn Ihre Domain beispielsweise `example.com` lautet, führen Sie Folgendes aus:

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Es sind mehrere [DNS-Suchwerkzeuge](https://www.ultratools.com/tools/dnsLookup) verfügbar. Google DoH kann verwendet werden, um TXT-Einträge zu suchen und zu erkennen, ob der TXT-Eintrag fehlt oder fehlerhaft ist.

>[!NOTE]
>
>Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Verbreitung einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Siehe [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) für weitere Details.

## Nächste Schritte {#next-steps}

Nachdem Sie Ihren TXT-Eintrag erstellt haben, können Sie den Status Ihres Domain-Namens überprüfen. Fahren Sie mit dem Dokument [Überprüfen des Domänennamenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) fort, um mit der Einrichtung Ihres benutzerdefinierten Domänennamens fortzufahren.

>[!TIP]
>
>Der TXT-Eintrag und der CNAME oder A Record können gleichzeitig auf dem herrschenden DNS-Server gesetzt werden, wodurch Zeit gespart wird.
>
>Wenn Sie dies wünschen, überprüfen Sie zunächst den gesamten Prozess der Einrichtung eines benutzerdefinierten Domänennamens, wie im Dokument [Einführung in benutzerdefinierte Domänennamen](/help/implementing/cloud-manager/custom-domain-names/introduction.md) beschrieben, wobei Sie besonders auf das Dokument [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) achten und Ihre DNS-Einstellungen entsprechend aktualisieren.