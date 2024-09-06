---
title: Hinzufügen eines TXT-Eintrags
description: Erfahren Sie, wie Sie einen TXT-Eintrag hinzufügen, um zu überprüfen, ob eine benutzerdefinierte Domain für die Verwendung mit Cloud Manager Ihr Eigentum ist.
exl-id: d441de29-af41-4d3e-9155-531af9702841
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 5d6d3374f2dd95728b2d3ed0cf6fab4092f73568
workflow-type: tm+mt
source-wordcount: '635'
ht-degree: 93%

---


# Hinzufügen eines TXT-Eintrags {#adding-txt}

Erfahren Sie, wie Sie einen TXT-Eintrag hinzufügen, um zu überprüfen, ob eine benutzerdefinierte Domain für die Verwendung mit Cloud Manager Ihr Eigentum ist.

## Was ist ein TXT-Eintrag? {#what-is}

Ein Texteintrag (auch als TXT-Eintrag bezeichnet) ist ein Typ von Ressourceneintrag im DNS (Domain Name System). Er bietet die Möglichkeit, beliebigen Text mit einem Host-Namen zu verknüpfen. Dazu zählen u. a. für Menschen lesbare Informationen zu einem Host-Namen wie Server- oder Netzwerkinformationen.

Cloud Manager nutzt einen spezifischen TXT-Eintrag, um das Hosting einer Domain in einem CDN-Service zu autorisieren. Sie müssen einen DNS-TXT-Eintrag in der Zone erstellen, die Cloud Manager dazu autorisiert, den CDN-Service mit der benutzerdefinierten Domain bereitzustellen, und Sie müssen ihn dem Backend-Service zuordnen. Diese Zuordnung steht vollständig unter Ihrer Kontrolle und autorisiert Cloud Manager ausdrücklich, Inhalte aus dem Service für eine Domain bereitzustellen. Diese Genehmigung kann erteilt und entzogen werden. Der TXT-Eintrag ist spezifisch für die Domain und die Cloud Manager-Umgebung.

## Voraussetzungen {#requirements}

Sie müssen diese Anforderungen erfüllen, bevor Sie einen TXT-Eintrag hinzufügen.

* Sie müssen Ihren Domain-Host oder Ihre Registrierungsstelle ermitteln, falls Sie sie noch nicht kennen.
* Sie müssen in der Lage sein, die DNS-Einträge für die Domain Ihres Unternehmens zu ändern, oder sich andernfalls an eine entsprechende Person wenden, die dies kann.
* Sie müssen zunächst einen benutzerdefinierten Domänennamen hinzufügen, wie im Dokument [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) beschrieben.

## Hinzufügen eines TXT-Eintrags zur Überprüfung {#verification}

Im Rahmen der Überprüfung eines benutzerdefinierten Domain-Namens, der mit Cloud Manager verwendet werden soll, wird ein TXT-Eintrag hinzugefügt.

1. Sie müssen zunächst einen benutzerdefinierten Domänennamen hinzufügen, wie im Dokument [Hinzufügen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/add-custom-domain-name.md) beschrieben.

1. In Cloud Manager werden im Dialogfeld **Domain-Namen hinzufügen** auf der Registerkarte **Überprüfung** der Name und der TXT-Wert angezeigt, die zur Überprüfung verwendet werden sollen. Kopieren Sie diesen Wert.

   ![Verifizierung des Domain-Namens](/help/implementing/cloud-manager/assets/cdn/cdn-create6.png)

1. Melden Sie sich bei Ihrem Domain-Host an und wechseln Sie zum Abschnitt mit den DNS-Einträgen.

1. Fügen Sie `_aemverification.[yourdomainname]` als den **Namen** des Werts hinzu und fügen Sie den TXT-Wert genau so hinzu, wie er im Dialogfeld **Domain-Namen hinzufügen** angezeigt wird.

   * Weitere Informationen finden Sie in den [Beispielen im folgenden Abschnitt](#examples).

1. Speichern Sie den TXT-Eintrag auf Ihrem Domain-Host.

## Beispiele für TXT-Einträge {#examples}

| Domain | Name | TXT-Wert |
|--- |--- |---|
| `example.com` | `_aemverification.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=example.com/[program]/[env]/..*` |
| `www.example.com` | `_aemverification.www.example.com` | Kopieren Sie den vollständigen in der Benutzeroberfläche von Cloud Manager angezeigten Wert. Dieser ist spezifisch für die Domain und die Umgebung. Beispiel:<br>`adobe-aem-verification=www.example.com/[program]/[env]/..*` |

## Überprüfen des TXT-Eintrags {#verify}

Wenn Sie fertig sind, können Sie das Ergebnis überprüfen, indem Sie den folgenden Befehl ausführen.

```shell
dig _aemverification.[yourdomainname] -t txt
```

Das erwartete Ergebnis sollte den TXT-Wert anzeigen, der in der Cloud Manager-Benutzeroberfläche im Dialogfeld **Domain-Namen hinzufügen** auf der Registerkarte **Überprüfung** angegeben ist.

Wenn Ihre Domain beispielsweise `example.com` lautet, führen Sie Folgendes aus:

```shell
dig TXT _aemverification.example.com -t txt
```

>[!TIP]
>
>Es sind mehrere [DNS-Suchwerkzeuge](https://www.ultratools.com/tools/dnsLookup) verfügbar. Google DoH kann verwendet werden, um TXT-Einträge zu suchen und zu erkennen, ob der TXT-Eintrag fehlt oder fehlerhaft ist.

>[!NOTE]
>
>Die Verarbeitung der DNS-Verifizierung kann aufgrund von Verzögerungen bei der DNS-Weitergabe einige Stunden dauern.
>
>Cloud Manager überprüft die Eigentümerschaft und aktualisiert den Status, der in der Tabelle der Domain-Einstellungen zu sehen ist. Siehe [Überprüfen des Status eines benutzerdefinierten Domain-Namens](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) für weitere Details.

## Nächste Schritte {#next-steps}

Nachdem Sie Ihren TXT-Eintrag erstellt haben, können Sie den Status Ihres Domain-Namens überprüfen. Fahren Sie mit dem Dokument [Überprüfen des Domain-Namenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) fort, um mit der Einrichtung Ihres benutzerdefinierten Domain-Namens fortzufahren.

>[!TIP]
>
>Der TXT-Eintrag und der CNAME- oder A-Eintrag können zeitsparend gleichzeitig auf dem entsprechenden DNS-Server eingerichtet werden.
>
>Wenn gewünscht, überprüfen Sie zunächst den gesamten Prozess der Einrichtung eines benutzerdefinierten Domain-Namens, wie im Dokument [Einführung in benutzerdefinierte Domain-Namen](/help/implementing/cloud-manager/custom-domain-names/introduction.md) beschrieben, wobei Sie besonders das Dokument [help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md) berücksichtigen und Ihre DNS-Einstellungen entsprechend aktualisieren sollten.