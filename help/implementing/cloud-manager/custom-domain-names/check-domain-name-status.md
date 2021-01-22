---
title: Überprüfen des Domänennamenstatus
description: Überprüfen des Domänennamenstatus
translation-type: tm+mt
source-git-commit: f11cb3b56f51046779300626d1deb037dd687309
workflow-type: tm+mt
source-wordcount: '244'
ht-degree: 0%

---


# Überprüfen des Domänennamenstatus {#check-status}

Sie können feststellen, ob Ihr Domänenname erfolgreich überprüft wurde, indem Sie auf der Seite &quot;Domäneneinstellungen&quot;auf der Umgebung in der Tabelle auf das Statussymbol für den Domänennamen klicken.

>[!NOTE]
>Cloud Manager wird automatisch eine TXT-Überprüfung Trigger, wenn Sie im Überprüfungsschritt des Assistenten für benutzerdefinierte Domänen die Option Speichern auswählen. Für spätere Überprüfungen müssen Sie das Symbol **verify wiederum** neben dem Status aktiv auswählen.

Cloud Manager überprüft den Domänenbesitz über den TXT-Wert und zeigt eine der folgenden Statusmeldungen an:

* **Der Wert für**
die Domänenüberprüfung &quot;FehlgeschlagenTXT&quot;fehlt oder wird mit Fehlern erkannt. Befolgen Sie die Anweisungen und versuchen Sie es erneut. Wenn Sie bereit sind, müssen Sie die 
*überprüfen Sie* das Symbol neben dem Status.

* **Domänenüberprüfung**
läuftÜberprüfung läuft. Dieser Status wird normalerweise angezeigt, nachdem Sie die Variable 
*überprüfen Sie* das Symbol neben dem Status.

* **Geprüft,**
fehlgeschlagene Bereitstellung TXT-Überprüfung erfolgreich. Die CDN-Bereitstellung ist jedoch fehlgeschlagen. Ein Vertreter der Adobe wird automatisch benachrichtigt.

* **Domäne überprüft und**
bereitgestelltDieser Status gibt an, dass Ihr benutzerdefinierter Domänenname einsatzbereit ist.
   >[!NOTE]
   >An dieser Stelle steht Ihr benutzerdefinierter Domänenname zum Testen bereit und wird auf den Domänennamen von Cloud Manager verwiesen. Weitere Informationen finden Sie unter [Konfigurieren von DNS-Einstellungen](/help/implementing/cloud-manager/custom-domain-names/configure-dns-settings.md).

* **Das**
Löschen des Namens der benutzerdefinierten Domäne wird ausgeführt.

* **Löschen**
fehlgeschlagenLöschen des Namens der benutzerdefinierten Domäne fehlgeschlagen. Du musst es erneut versuchen. Weitere Informationen finden Sie unter [Löschen eines benutzerdefinierten Domänennamens](/help/implementing/cloud-manager/custom-domain-names/delete-custom-domain-name.md).

