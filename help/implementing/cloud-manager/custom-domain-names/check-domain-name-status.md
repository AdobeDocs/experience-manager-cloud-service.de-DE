---
title: Überprüfen des Domänennamenstatus
description: Überprüfen des Domänennamenstatus
translation-type: tm+mt
source-git-commit: 1c51560886515e092680c23db3e128758dcd7d99
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---


# Überprüfen des Domänennamenstatus {#check-status}

Sie können feststellen, ob Ihr Domänenname erfolgreich überprüft wurde, indem Sie auf der Seite &quot;Domäneneinstellungen&quot;auf der Umgebung in der Tabelle auf das Statussymbol für den Domänennamen klicken.

>[!NOTE]
>Cloud Manager löst automatisch eine TXT-Überprüfung aus, wenn Sie im Überprüfungsschritt des Assistenten für Hinzufügen benutzerdefinierte Domäne &quot;Speichern&quot;wählen. Für spätere Überprüfungen müssen Sie das Symbol **verify wiederum** neben dem Status aktiv auswählen.

Cloud Manager überprüft den Domänenbesitz über den TXT-Wert und zeigt eine der folgenden Statusmeldungen an:

* **Der Wert für**
die Domänenüberprüfung &quot;FehlgeschlagenTXT&quot;fehlt oder wird mit Fehlern erkannt. Befolgen Sie die Anweisungen und versuchen Sie es erneut. Wenn Sie bereit sind, müssen Sie das Symbol &quot;Erneut überprüfen&quot;neben dem Status auswählen.

* **Domänenüberprüfung**
läuftÜberprüfung läuft. Dieser Status wird in der Regel angezeigt, nachdem Sie das Symbol &quot;Erneut überprüfen&quot;neben dem Status ausgewählt haben.

* **Geprüft,**
fehlgeschlagene Bereitstellung TXT-Überprüfung erfolgreich. Die CDN-Bereitstellung ist jedoch fehlgeschlagen. Ein Vertreter der Adobe wird automatisch benachrichtigt.

* **Domäne überprüft und**
bereitgestelltDieser Status gibt an, dass Ihr benutzerdefinierter Domänenname einsatzbereit ist. Hinweis: An dieser Stelle steht Ihr benutzerdefinierter Domänenname zum Testen bereit und wird auf den Domänennamen von Cloud Manager verwiesen. Informationen dazu finden Sie unter Konfigurieren von DNS-Einstellungen.

* **Das**
Löschen des Namens der benutzerdefinierten Domäne wird ausgeführt.

* **Löschen**
fehlgeschlagenLöschen des Namens der benutzerdefinierten Domäne fehlgeschlagen. Du musst es erneut versuchen. Wechseln Sie zu &quot;Benutzerdefinierten Domänennamen löschen&quot;, um weitere Informationen zum Thema zu erhalten.

