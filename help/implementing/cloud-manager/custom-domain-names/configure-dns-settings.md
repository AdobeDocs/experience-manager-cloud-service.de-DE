---
title: Konfigurieren von DNS-Einstellungen
description: Erfahren Sie, wie Sie DNS-Einstellungen für Ihre benutzerdefinierten Domänennamen konfigurieren.
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
source-git-commit: 9fd7c17fce8c11809eabcc6387cbace0ebdc64a2
workflow-type: tm+mt
source-wordcount: '338'
ht-degree: 96%

---

# Konfigurieren von DNS-Einstellungen {#configure-dns}

Nachdem der benutzerdefinierte Domain-Name erfolgreich überprüft und bereitgestellt wurde, können Sie die DNS-Einträge für Ihren benutzerdefinierten Domain-Namen mit Ihrem DNS-Anbieter aktualisieren. Dies ermöglicht es Ihrer Site, Besuchern Inhalte bereitzustellen. Diese Aktivität wird daher in der Regel vor einer Live-Schaltung durchgeführt.

## Was sind DNS-Einstellungen? {#dns-settings}

Ein `CNAME`- oder Apex-Eintrag leitet, sobald er bereitgestellt ist, den gesamten Internet-Traffic für die Domain zu dem Punkt, auf den er verweist. Wenn dieser Speicherort nicht für den Traffic vorgesehen ist, kommt es zu einem Ausfall. Wenn er nicht getestet wurde, kann es zu Fehlern in den Inhalten kommen. Aus diesem Grund wird dieser Schritt immer durchgeführt, nachdem der Test abgeschlossen ist und Sie bereit sind, live zu gehen.

Um diese Einstellungen zu konfigurieren, müssen Sie festlegen, ob ein `CNAME`- oder ein Apex-Eintrag so konfiguriert sein muss, dass Ihr benutzerdefinierter Domain-Name auf den Cloud Manager-Domain-Namen verweist. Die folgenden Abschnitte helfen Ihnen dabei, zu ermitteln, welche Art von Eintrag für Ihre DNS-Konfiguration geeignet ist.

>[!NOTE]
>
>Sie bzw. entsprechende Personen in Ihrem Unternehmen müssen sich bei Ihrem DNS-Anbieter (der Firma, von der Sie die Domain erworben haben) anmelden oder sich mit ihm in Verbindung setzen und die DNS-Einstellungen aktualisieren können.

## CNAME-Datensatz {#cname-record}

Ein kanonischer Name oder CNAME-Eintrag ist eine Art von DNS-Eintrag, der einen Aliasnamen einem wahren oder kanonischen Domain-Namen zuordnet. CNAME-Datensätze werden normalerweise dazu verwendet, eine Unter-Domain wie `www.example.com` der Domain zuzuordnen, in der der Inhalt dieser Unter-Domain gehostet wird.

Melden Sie sich bei Ihrer Domain-Registrierungsstelle an und erstellen Sie einen `CNAME`-Eintrag, um Ihren benutzerdefinierten Domain-Nnamen auf das Ziel zu verweisen, wie in der folgenden Tabelle dargestellt.

| CNAME | benutzerdefinierter Domain-Name, der auf das Ziel verweist |
|--- |--- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

## APEX-Datensatz {#apex-record}

Eine Apex-Domain ist eine benutzerdefinierte Domain, die keine Unter-Domain enthält, z. B. `example.com`. Eine Apex-Domain wird mit einem `A`-, `ALIAS`- oder `ANAME`-Datensatz über Ihren DNS-Anbieter konfiguriert. Die Apex-Domains müssen auf bestimmte IP-Adressen verweisen.

Fügen Sie alle der folgenden `A`-Einträge über Ihren Domain-Anbieter zu den DNS-Einstellungen Ihrer Domain hinzu.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
