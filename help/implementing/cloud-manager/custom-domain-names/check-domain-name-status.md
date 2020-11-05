---
title: Überprüfen des Domänennamenstatus
description: Überprüfen des Domänennamenstatus
translation-type: tm+mt
source-git-commit: 5cd22d8af20bb947e4cdab448cf8f20c6596bb2e
workflow-type: tm+mt
source-wordcount: '810'
ht-degree: 0%

---


# Überprüfen des Domänennamenstatus {#check-status}

Sie können feststellen, ob Ihr Domänenname erfolgreich überprüft wurde, indem Sie auf der Seite &quot;Domäneneinstellungen&quot;auf der Umgebung in der Tabelle auf das Statussymbol für den Domänennamen klicken.

>[!NOTE]
>Cloud Manager löst automatisch eine TXT-Überprüfung aus, wenn Sie im Überprüfungsschritt des Assistenten für Hinzufügen benutzerdefinierte Domäne &quot;Speichern&quot;wählen. Für spätere Überprüfungen müssen Sie aktiv das Symbol &quot;Erneut überprüfen&quot;neben dem Status auswählen. BILD EINFÜGEN

Cloud Manager überprüft den Domänenbesitz über den TXT-Wert und zeigt eine der folgenden Statusmeldungen an:

* **Der TXT-Wert für die Domänenüberprüfung fehlgeschlagen** fehlt oder wird mit Fehlern erkannt. Befolgen Sie die Anweisungen und versuchen Sie es erneut. Wenn Sie bereit sind, müssen Sie das Symbol &quot;Erneut überprüfen&quot;neben dem Status auswählen.

* **Domänenüberprüfung wird ausgeführt**. Dieser Status wird in der Regel angezeigt, nachdem Sie das Symbol &quot;Erneut überprüfen&quot;neben dem Status ausgewählt haben.

* **Die TXT-Überprüfung bei Bereitstellung fehlgeschlagen** wurde erfolgreich durchgeführt. Die CDN-Bereitstellung ist jedoch fehlgeschlagen. Ein Vertreter der Adobe wird automatisch benachrichtigt.

* **Domäne überprüft und bereitgestellt** Dieser Status gibt an, dass Ihr benutzerdefinierter Domänenname einsatzbereit ist. Hinweis: An dieser Stelle steht Ihr benutzerdefinierter Domänenname zum Testen bereit und wird auf den Domänennamen von Cloud Manager verwiesen. Gehen Sie zu Konfigurieren von DNS-Einstellungen INSERT LINK, um zu erfahren, wie dies zu tun.

* **Das Löschen** des Namens der benutzerdefinierten Domäne wird derzeit ausgeführt.

* **Löschen fehlgeschlagen** Löschen des benutzerdefinierten Domänennamens. Du musst es erneut versuchen. Wechseln Sie zu &quot;Benutzerdefinierten Domänennamen löschen&quot;, um weitere Informationen zum Thema zu erhalten.


## DNS-Einstellungen konfigurieren {#configure-dns}

Nachdem der benutzerdefinierte Domänenname erfolgreich überprüft und bereitgestellt wurde, können Sie die DNS-Datensätze für Ihren benutzerdefinierten Domänennamen mit Ihrem DNS-Anbieter aktualisieren. Dadurch kann Ihre Site Besuchern dienen. Diese Aktivität wird daher in der Regel vor Go-Live durchgeführt.

>[!NOTE]
>Sie oder die entsprechende Person in Ihrer Organisation müssen sich bei Ihrem DNS-Provider (der Firma, von der Sie die Domäne gekauft haben) anmelden oder sich mit ihm in Verbindung setzen können und die DNS-Einstellungen aktualisieren können.

Dazu müssen Sie festlegen, ob Sie Ihre DNS-Einstellungen auf einen `CNAME` oder einen Apex-Datensatz konfigurieren müssen, der Ihren benutzerdefinierten Domänennamen auf den Domänennamen von Cloud Manager verweist. Ein `CNAME` oder ein Datensatz, sobald er bereitgestellt ist, leitet den gesamten Internetverkehr für die Domäne an den Punkt, an den er verweist. Wenn dieser Ort nicht für den Verkehr vorgesehen ist, wird es zu einem Ausfall kommen. Wenn der Inhalt nicht getestet wurde, kann es zu Fehlern im Inhalt kommen. Deshalb erfolgt dieser Schritt immer nach Abschluss des Tests und der Kunde ist bereit für Go-Live.

### CNAME-Eintrag {#cname-record}

Die folgenden Abschnitte helfen Ihnen bei der Bestimmung, welcher Datensatz für Ihre DNS-Konfiguration geeignet ist.

Ein kanonischer Name oder `CNAME` Datensatz ist ein DNS-Datensatz, der einen Aliasnamen einem echten oder kanonischen Domänennamen zuordnet. CNAME-Einträge werden normalerweise dazu verwendet, eine Subdomäne zuzuordnen, z. B. `www.example.com` der Domäne, in der der Inhalt dieser Subdomäne gehostet wird.

Melden Sie sich bei Ihrem Domänenregistrierer an und erstellen Sie einen CNAME-Eintrag, um Ihren benutzerspezifischen Domänennamen auf die Zielgruppe zu verweisen, wie nachfolgend gezeigt:

| CNAME | Benutzerdefinierter Domänenname verweist auf die Zielgruppe |
|--- |--- |
| www.customdomain.com | cdn.adobeaemcloud.com |

### APEX-Datensatz {#apex-record}

Eine ex-Domäne ist eine benutzerdefinierte Domäne, die keine Subdomäne enthält, z. B. example.com. Eine ex-Domäne wird mit einem `A` , `ALIAS` oder `ANAME` Datensatz über Ihren DNS-Provider konfiguriert. Die Apex-Domänen müssen auf bestimmte IP-Adressen verweisen.

hinzufügen alle folgenden A-Datensätze über Ihren Domänenanbieter an die DNS-Einstellungen Ihrer Domäne:

* `A RECORD`

* `A record for domain @ pointing to IP 151.101.3.10`

* `A record for domain @ pointing to IP 151.101.67.10`

* `A record for domain @ pointing to IP 151.101.131.10`

* `A record for domain @ pointing to IP 151.101.195.10`

## DNS-Datensatzstatus überprüfen {#check-status-dns-record}

Sie können feststellen, ob Ihr Domänenname ordnungsgemäß auf Ihrer AEM als Cloud Service-Website aufgelöst wird, indem Sie in der Tabelle auf der Seite &quot;Domäneneinstellungen&quot;auf das Statussymbol für den DNS-Datensatz klicken. Cloud Manager führt eine DNS-Suche nach Ihrem Domänennamen durch und zeigt eine der folgenden Statusmeldungen an:

>[!NOTE]
>Cloud Manager löst automatisch eine DNS-Suche aus, wenn Ihr benutzerspezifischer Domänenname zum ersten Mal überprüft und bereitgestellt wurde. Bei nachfolgenden Versuchen müssen Sie das Symbol **Wiederholen** auflösen neben dem Status aktiv auswählen. BILD EINFÜGEN

* **Der DNS-Status, der nicht erkannt** wurde, wird erst erkannt, wenn der benutzerdefinierte Domänenname erfolgreich überprüft und bereitgestellt wurde. Dieser Status wird auch angezeigt, wenn der Name Ihrer benutzerdefinierten Domäne gelöscht wird.

* **DNS löst falsch**. Dies deutet darauf hin, dass die DNS-Datensatzkonfiguration noch nicht aufgelöst/verzeichnet wurde oder fehlerhaft ist. Ein Vertreter der Adobe wird automatisch benachrichtigt.

   >[!NOTE]
   >Sie müssen entweder eine `CNAME` oder `A-record` die entsprechenden Anweisungen befolgen. Gehen Sie zum Konfigurieren von DNS-Einstellungen INSERT LINK, um mehr über das Thema zu erfahren. Wenn Sie bereit sind, müssen Sie das Symbol &quot;Erneut auflösen&quot;neben dem Status auswählen.

* **DNS-Auflösung wird** ausgeführt. Dieser Status wird normalerweise angezeigt, nachdem Sie das Symbol &quot;Erneut auflösen&quot;neben dem Status ausgewählt haben.

* **DNS löst korrekt** Ihre DNS-Einstellungen sind richtig konfiguriert. Ihre Website dient Besuchern.
