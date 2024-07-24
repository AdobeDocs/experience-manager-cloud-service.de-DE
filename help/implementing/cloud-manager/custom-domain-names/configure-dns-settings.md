---
title: Konfigurieren von DNS-Einstellungen
description: Erfahren Sie, wie Sie mit der Konfiguration von DNS-Einstellungen für Ihre benutzerdefinierten Domänennamen Besucher auf Ihrer Site bedienen können.
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
solution: Experience Manager
feature: Cloud Manager, Developing
role: Admin, Architect, Developer
source-git-commit: 06e961febd7cb2ea1d8fca00cb3dee7f7ca893c9
workflow-type: tm+mt
source-wordcount: '416'
ht-degree: 57%

---


# Konfigurieren von DNS-Einstellungen {#configure-dns}

Nachdem Ihr benutzerdefinierter Domänenname erfolgreich [verifiziert und bereitgestellt wurde,](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) können Sie die DNS-Einträge für Ihren benutzerdefinierten Domänennamen mit Ihrem DNS-Provider aktualisieren. Dies ermöglicht es Ihrer Site, Besuchern Inhalte bereitzustellen. Diese Aktivität wird daher in der Regel vor einer Live-Schaltung durchgeführt.

## Was sind DNS-Einstellungen? {#dns-settings}

Ein `CNAME` oder ein Datensatz leitet nach der Bereitstellung den gesamten Internet-Traffic für die Domäne an den Ort weiter, an den er verweist. Wenn dieser Speicherort nicht für den Traffic vorgesehen ist, kommt es zu einem Ausfall. Wenn er nicht getestet wurde, kann es zu Fehlern in den Inhalten kommen. Aus diesem Grund wird dieser Schritt immer durchgeführt, nachdem der Test abgeschlossen ist und Sie bereit sind, live zu gehen.

Um diese Einstellungen zu konfigurieren, müssen Sie festlegen, ob ein `CNAME`- oder ein Apex-Eintrag so konfiguriert werden muss, dass Ihr benutzerdefinierter Domänenname auf den Cloud Manager-Domänennamen verweist. Die folgenden Abschnitte dieses Dokuments helfen Ihnen bei der Bestimmung des für Ihre DNS-Konfiguration geeigneten Datensatztyps.

## Voraussetzungen {#requirements}

Sie müssen diese Anforderungen erfüllen, bevor Sie Ihre DNS-Einträge konfigurieren.

* Sie müssen Ihren Domain-Host oder Ihre Registrierungsstelle ermitteln, falls Sie sie noch nicht kennen.
* Sie müssen in der Lage sein, die DNS-Einträge für die Domain Ihres Unternehmens zu ändern oder sich ansonsten an eine entsprechende Person zu wenden, die dies kann.
* Sie müssen Ihren konfigurierten benutzerdefinierten Domänennamen bereits überprüft haben, wie im Dokument [Überprüfen des Domänennamenstatus](/help/implementing/cloud-manager/custom-domain-names/check-domain-name-status.md) beschrieben.

## CNAME-Datensatz {#cname-record}

Ein kanonischer Name oder CNAME-Eintrag ist eine Art von DNS-Eintrag, der einen Aliasnamen einem wahren oder kanonischen Domain-Namen zuordnet. CNAME-Datensätze werden normalerweise dazu verwendet, eine Unter-Domain wie `www.example.com` der Domain zuzuordnen, in der der Inhalt dieser Unter-Domain gehostet wird.

Melden Sie sich bei Ihrer Domain-Registrierungsstelle an und erstellen Sie einen `CNAME`-Eintrag, um Ihren benutzerdefinierten Domain-Nnamen auf das Ziel zu verweisen, wie in der folgenden Tabelle dargestellt.

| CNAME | benutzerdefinierter Domain-Name, der auf das Ziel verweist |
|--- |--- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

## APEX-Datensatz {#apex-record}

Eine Apex-Domain ist eine benutzerdefinierte Domain, die keine Unter-Domain enthält, z. B. `example.com`. Eine Apex-Domain wird mit einem `A`-, `ALIAS`- oder `ANAME`-Datensatz über Ihren DNS-Anbieter konfiguriert. Die Apex-Domains müssen auf bestimmte IP-Adressen verweisen.

Fügen Sie die folgenden `A`-Einträge über Ihren Domain-Provider in den DNS-Einstellungen Ihrer Domain hinzu.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

## Nächste Schritte {#next-steps}

Nachdem Sie Ihre DNS-Einträge für Ihren benutzerdefinierten Domänennamen konfiguriert haben, müssen Sie diese Einstellungen in Cloud Manager überprüfen. Fahren Sie mit dem Dokument [Überprüfen des DNS-Datensatzstatus](/help/implementing/cloud-manager/custom-domain-names/check-dns-record-status.md) fort, um Ihren benutzerdefinierten Domänennamen abzuschließen.
