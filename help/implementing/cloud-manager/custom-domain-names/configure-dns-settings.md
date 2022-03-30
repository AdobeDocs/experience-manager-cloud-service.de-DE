---
title: 'Konfigurieren von DNS-Einstellungen '
description: Konfigurieren von DNS-Einstellungen
exl-id: 6e294f0b-52cb-40dd-bc42-ddbcffdf5600
source-git-commit: 60b496024b3d012033309632999851c08f43c5d7
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 45%

---

# Konfigurieren von DNS-Einstellungen {#configure-dns}

Nachdem der benutzerdefinierte Domain-Name erfolgreich überprüft und bereitgestellt wurde, können Sie die DNS-Datensätze für Ihren benutzerdefinierten Domain-Namen mit Ihrem DNS-Anbieter aktualisieren. Dies ermöglicht es Ihrer Site, Besuchern Inhalte bereitzustellen. Diese Aktivität wird daher in der Regel vor der Live-Schaltung durchgeführt.

## Was sind DNS-Einstellungen? {#dns-settings}

Ein `CNAME`- oder Apex-Datensatz leitet, sobald er bereitgestellt ist, den gesamten Internet-Traffic für die Domain zu dem Punkt, auf den er verweist. Wenn dieser nicht für den Traffic vorgesehen ist, kommt es zu einem Ausfall. Wenn er nicht getestet wurde, kann es zu Fehlern in den Inhalten kommen. Aus diesem Grund wird dieser Schritt immer durchgeführt, nachdem der Test abgeschlossen ist und Sie bereit sind, live zu gehen.

Um diese Einstellungen zu konfigurieren, müssen Sie festlegen, ob ein `CNAME` oder ein Apex-Eintrag so konfiguriert sein, dass Ihr benutzerdefinierter Domänenname auf den Cloud Manager-Domänennamen verweist. Die folgenden Abschnitte helfen Ihnen dabei, zu ermitteln, welcher Datensatz für Ihre DNS-Konfiguration geeignet ist.

>[!NOTE]
>
>Sie oder die entsprechende Person in Ihrer Organisation müssen sich bei Ihrem DNS-Provider (dem Unternehmen, von dem Sie die Domäne gekauft haben) anmelden oder sich mit ihm in Verbindung setzen können und Ihre DNS-Einstellungen aktualisieren können.

## CNAME-Datensatz {#cname-record}

Ein kanonischer Name oder CNAME-Eintrag ist ein Typ von DNS-Eintrag, der einen Aliasnamen einem wahren oder kanonischen Domänennamen zuordnet. CNAME-Datensätze werden normalerweise dazu verwendet, eine Unter-Domain wie `www.example.com` der Domain zuzuordnen, in der der Inhalt dieser Unter-Domain gehostet wird.

Melden Sie sich bei Ihrer Domänenregistrierungsstelle an und erstellen Sie eine `CNAME` -Eintrag, um Ihren benutzerdefinierten Domänennamen auf das Ziel zu verweisen, z. B. in der folgenden Tabelle.

| CNAME | benutzerdefinierter Domain-Name, der auf das Ziel verweist |
|--- |--- |
| `www.customdomain.com` | `cdn.adobeaemcloud.com` |

## APEX-Datensatz {#apex-record}

Eine API-Domäne ist eine benutzerdefinierte Domäne, die keine Subdomäne enthält, z. B. `example.com`. Eine Apex-Domain wird mit einem `A`-, `ALIAS`- oder `ANAME`-Datensatz über Ihren DNS-Anbieter konfiguriert. Apex-Domänen müssen auf bestimmte IP-Adressen verweisen.

Fügen Sie Folgendes hinzu: `A` -Einträge in die DNS-Einstellungen Ihrer Domäne über Ihren Domänenanbieter speichern.

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
