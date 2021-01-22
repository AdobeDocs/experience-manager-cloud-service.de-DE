---
title: 'DNS-Einstellungen konfigurieren '
description: DNS-Einstellungen konfigurieren
translation-type: tm+mt
source-git-commit: 1c51560886515e092680c23db3e128758dcd7d99
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 6%

---


# Konfigurieren von DNS-Einstellungen {#configure-dns}

Nachdem der benutzerdefinierte Domänenname erfolgreich überprüft und bereitgestellt wurde, können Sie die DNS-Datensätze für Ihren benutzerdefinierten Domänennamen mit Ihrem DNS-Anbieter aktualisieren. Dadurch kann Ihre Site Besuchern dienen. Diese Aktivität wird daher in der Regel vor Go-Live durchgeführt.

>[!NOTE]
>Sie oder die entsprechende Person in Ihrer Organisation müssen sich bei Ihrem DNS-Provider (der Firma, von der Sie die Domäne gekauft haben) anmelden oder sich mit ihm in Verbindung setzen können und die DNS-Einstellungen aktualisieren können.

Dazu müssen Sie festlegen, ob Sie Ihre DNS-Einstellungen auf einen `CNAME`- oder Apex-Datensatz konfigurieren müssen, der Ihren benutzerdefinierten Domänennamen auf den Domänennamen von Cloud Manager verweist. Ein `CNAME`- oder ein Datensatz, sobald er bereitgestellt ist, leitet den gesamten Internetverkehr für die Domäne an den Punkt, an den er verweist. Wenn dieser Ort nicht für den Verkehr vorgesehen ist, wird es zu einem Ausfall kommen. Wenn der Inhalt nicht getestet wurde, kann es zu Fehlern im Inhalt kommen. Deshalb erfolgt dieser Schritt immer nach Abschluss des Tests und der Kunde ist bereit für Go-Live.

## CNAME-Eintrag {#cname-record}

Die folgenden Abschnitte helfen Ihnen bei der Bestimmung, welcher Datensatz für Ihre DNS-Konfiguration geeignet ist.

Ein kanonischer Name oder `CNAME`-Datensatz ist ein DNS-Datensatz, der einen Aliasnamen einem wahren oder kanonischen Domänennamen zuordnet. CNAME-Einträge werden normalerweise dazu verwendet, eine Subdomäne wie `www.example.com` der Domäne zuzuordnen, in der der Inhalt dieser Subdomäne gehostet wird.

Melden Sie sich bei Ihrer Domain-Registrierungsstelle an und erstellen Sie einen CNAME-Eintrag, um Ihren benutzerdefinierten Domain-Namen wie unten gezeigt auf das Ziel zu verweisen:

| CNAME | Benutzerdefinierter Domänenname verweist auf die Zielgruppe |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

## APEX Record {#apex-record}

Eine ex-Domäne ist eine benutzerdefinierte Domäne, die keine Subdomäne enthält, z. B. example.com. Eine ex-Domäne wird mit einem `A`-, `ALIAS`- oder `ANAME`-Datensatz über Ihren DNS-Provider konfiguriert. Die Apex-Domänen müssen auf bestimmte IP-Adressen verweisen.

hinzufügen alle folgenden A-Datensätze über Ihren Domänenanbieter an die DNS-Einstellungen Ihrer Domäne:

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
