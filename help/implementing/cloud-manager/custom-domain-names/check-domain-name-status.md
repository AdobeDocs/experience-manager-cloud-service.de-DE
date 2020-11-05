---
title: Überprüfen des Domänennamenstatus
description: Überprüfen des Domänennamenstatus
translation-type: tm+mt
source-git-commit: 91b06bcd96fe8a37c3fb20ef90e1684f6d19183f
workflow-type: tm+mt
source-wordcount: '519'
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
