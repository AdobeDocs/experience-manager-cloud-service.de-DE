---
title: DNS-Datensatzstatus überprüfen
description: DNS-Datensatzstatus überprüfen
translation-type: tm+mt
source-git-commit: b76a22469f248dde316dcaa514a906fe4361afd1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 0%

---


# DNS-Datensatzstatus {#check-dns-record-status} überprüfen

Sie können feststellen, ob Ihr Domänenname ordnungsgemäß auf Ihrer AEM als Cloud Service-Website aufgelöst wird, indem Sie in der Tabelle auf der Seite &quot;Domäneneinstellungen&quot;auf das Statussymbol für den DNS-Datensatz klicken.

Cloud Manager Trigger automatisch eine DNS-Suche, wenn Ihr benutzerspezifischer Domänenname zum ersten Mal erfolgreich überprüft und bereitgestellt wurde. Bei nachfolgenden Versuchen müssen Sie das Symbol **resolve** neben dem Status aktiv auswählen.

Cloud Manager führt eine DNS-Suche nach Ihrem Domänennamen durch und zeigt eine der folgenden Statusmeldungen an:

* **DNS-Status nicht**
erkanntDNS-Status wird erst erkannt, wenn der benutzerdefinierte Domänenname erfolgreich überprüft und bereitgestellt wurde. Dieser Status wird auch angezeigt, wenn der Name Ihrer benutzerdefinierten Domäne gelöscht wird.

* **DNS löst**
Unrichtig auf. Dies weist darauf hin, dass die DNS-Datensatzkonfiguration noch nicht aufgelöst/verzeichnet wurde oder fehlerhaft ist. Ein Vertreter der Adobe wird automatisch benachrichtigt.

   >[!NOTE]
   >Sie müssen entweder ein `CNAME` oder ein `A-record` konfigurieren, indem Sie die entsprechenden Anweisungen befolgen. Weitere Informationen finden Sie unter Konfigurieren von DNS-Einstellungen. Wenn Sie bereit sind, müssen Sie das Symbol **resolve** neben dem Status erneut auswählen.

* **DNS-Auflösung In**
ProgressResolution wird ausgeführt. Dieser Status wird normalerweise angezeigt, nachdem Sie das Symbol &quot;Erneut auflösen&quot;neben dem Status ausgewählt haben.

* **DNS löst**
korrekt aufIhre DNS-Einstellungen sind richtig konfiguriert. Ihre Website dient Besuchern.
