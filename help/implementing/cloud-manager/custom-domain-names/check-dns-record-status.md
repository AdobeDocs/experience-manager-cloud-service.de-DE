---
title: Überprüfen des Status von DNS-Einträgen
description: Überprüfen des Status von DNS-Einträgen
translation-type: tm+mt
source-git-commit: b76a22469f248dde316dcaa514a906fe4361afd1
workflow-type: tm+mt
source-wordcount: '235'
ht-degree: 100%

---


# Überprüfen des Status von DNS-Einträgen {#check-dns-record-status}

Sie können feststellen, ob Ihr Domain-Name ordnungsgemäß in Ihre AEM as a Cloud Service-Website aufgelöst wird, indem Sie auf das Statussymbol für den DNS-Eintrag in der Tabelle der Umgebungen auf der Seite „Domain-Einstellungen“ klicken.

Cloud Manager löst automatisch eine DNS-Suche aus, wenn Ihr benutzerdefinierter Domain-Name zum ersten Mal überprüft und bereitgestellt wird. Bei nachfolgenden Versuchen müssen Sie das Symbol zum **erneuten Auflösen** neben dem Status aktiv auswählen.

Cloud Manager führt eine DNS-Suche nach Ihrem Domain-Namen durch und zeigt eine der folgenden Statusmeldungen an:

* **DNS-Status nicht erkannt**
Der DNS-Status wird erst dann erkannt, wenn Ihr benutzerdefinierter Domain-Name erfolgreich überprüft und bereitgestellt wurde. Dieser Status wird auch angezeigt, wenn der Name Ihrer benutzerdefinierten Domain gerade gelöscht wird.

* **DNS wird falsch aufgelöst**
Dies zeigt an, dass entweder die Konfiguration der DNS-Einträge noch nicht aufgelöst/übertragen wurde oder fehlerhaft ist. Ein Adobe-Support-Mitarbeiter wird automatisch benachrichtigt.

   >[!NOTE]
   >Sie müssen entweder einen `CNAME` oder einen `A-record` konfigurieren, indem Sie die entsprechenden Anweisungen befolgen. Weitere Informationen finden Sie unter „Konfigurieren von DNS-Einstellungen“. Wenn Sie bereit sind, müssen Sie das Symbol zum **erneuten Auflösen** neben dem Status auswählen.

* **DNS-Auflösung in Bearbeitung**
Die Auflösung ist im Gange. Dieser Status wird normalerweise angezeigt, nachdem Sie neben dem Status das Symbol zum erneuten Auflösen ausgewählt haben.

* **DNS wird korrekt aufgelöst**
Ihre DNS-Einstellungen sind ordnungsgemäß konfiguriert. Ihre Website bedient Besucher.
