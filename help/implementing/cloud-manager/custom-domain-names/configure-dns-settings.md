---
title: 'Konfigurieren von DNS-Einstellungen '
description: Konfigurieren von DNS-Einstellungen
translation-type: tm+mt
source-git-commit: 1c51560886515e092680c23db3e128758dcd7d99
workflow-type: tm+mt
source-wordcount: '328'
ht-degree: 100%

---


# Konfigurieren von DNS-Einstellungen {#configure-dns}

Nachdem der benutzerdefinierte Domain-Name erfolgreich überprüft und bereitgestellt wurde, können Sie die DNS-Datensätze für Ihren benutzerdefinierten Domain-Namen mit Ihrem DNS-Anbieter aktualisieren. Dies ermöglicht es Ihrer Site, Besuchern Inhalte bereitzustellen. Diese Aktivität wird daher in der Regel vor einem Go-Live durchgeführt.

>[!NOTE]
>Sie bzw. entsprechende Personen in Ihrem Unternehmen müssen sich bei Ihrem DNS-Anbieter (der Firma, von der Sie die Domain erworben haben) anmelden oder sich mit ihm in Verbindung setzen und die DNS-Einstellungen aktualisieren können.

Dazu müssen Sie ermitteln, ob Sie Ihre DNS-Einstellungen für einen `CNAME`- oder Apex-Datensatz konfigurieren müssen, der Ihren benutzerdefinierten Domain-Namen auf den Domain-Namen von Cloud Manager verweist. Ein `CNAME`- oder Apex-Datensatz leitet, sobald er bereitgestellt ist, den gesamten Internet-Traffic für die Domain zu dem Punkt, auf den er verweist. Wenn dieser nicht für den Traffic vorgesehen ist, kommt es zu einem Ausfall. Wenn er nicht getestet wurde, kann es zu Fehlern in den Inhalten kommen. Deshalb erfolgt dieser Schritt immer nach Abschluss der Tests. Der Kunde ist dann bereit für den Go-Live.

## CNAME-Datensatz {#cname-record}

Die folgenden Abschnitte helfen Ihnen dabei, zu ermitteln, welcher Datensatz für Ihre DNS-Konfiguration geeignet ist.

Ein kanonischer Name oder `CNAME`-Datensatz ist ein DNS-Datensatz, der einen Aliasnamen einem wahren oder kanonischen Domain-Namen zuordnet. CNAME-Datensätze werden normalerweise dazu verwendet, eine Unter-Domain wie `www.example.com` der Domain zuzuordnen, in der der Inhalt dieser Unter-Domain gehostet wird.

Melden Sie sich bei Ihrer Domain-Registrierungsstelle an und erstellen Sie einen CNAME-Datensatz, um dafür zu sorgen, dass Ihr benutzerdefinierter Domain-Namen auf das Ziel verweist, wie nachfolgend gezeigt:

| CNAME | benutzerdefinierter Domain-Name, der auf das Ziel verweist |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

## APEX-Datensatz {#apex-record}

Eine Apex-Domain ist eine benutzerdefinierte Domain, die keine Unter-Domain enthält, z. B. „example.com“. Eine Apex-Domain wird mit einem `A`-, `ALIAS`- oder `ANAME`-Datensatz über Ihren DNS-Anbieter konfiguriert. Die Apex-Domains müssen auf bestimmte IP-Adressen verweisen.

Fügen Sie alle der folgenden Apex-Datensätze über Ihren Domain-Anbieter zu Ihren DNS-Einstellungen Ihrer Domain hinzu:

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`
